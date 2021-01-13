---
title: Komponenten-Referenzhandbuch
description: Ein Referenzhandbuch für Entwickler zu den Details der Komponenten und ihrer Struktur
translation-type: tm+mt
source-git-commit: d843182585a269b5ebb24cc31679b77fb6b6d697
workflow-type: tm+mt
source-wordcount: '3720'
ht-degree: 31%

---


# Komponenten-Referenzhandbuch {#components-reference-guide}

Komponenten sind das Herzstück des Erlebnisses in AEM. Die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) und das [AEM Projektarchiv](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) machen es einfach, mit einem Werkzeugsatz vorgefertigter, robuster Komponenten zu beginnen. Das [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) erläutert dem Entwickler, wie diese Tools verwendet werden und wie benutzerdefinierte Komponenten erstellt werden, um eine neue AEM zu erstellen.

>[!TIP]
>
>Bevor Sie auf dieses Dokument verweisen, stellen Sie sicher, dass Sie das [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) abgeschlossen haben und daher mit den [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) und dem [AEM Projektarchiv vertraut sind.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)

Da das WKND-Tutorial die meisten Anwendungsfälle abdeckt, ist dieses Dokument nur als Ergänzung zu diesen Ressourcen gedacht. Es enthält detaillierte technische Details darüber, wie Komponenten in AEM strukturiert und konfiguriert sind und nicht als Anleitung zum Einstieg gedacht sind.

## Überblick {#overview}

In diesem Abschnitt werden zentrale Konzepte und Schwierigkeiten erläutert. Er bietet so einen guten Einstieg in die Entwicklung eigener Komponenten.

### Planung {#planning}

Bevor Sie mit der Konfiguration oder dem Code Ihrer Komponente beginnen, sollten Sie sich fragen:

* Was genau soll die neue Komponente tun?
* Müssen Sie die Komponente komplett neu entwickeln oder können Sie die Grundlagen von einer vorhandenen Komponente übernehmen?
* Benötigt die Komponente eine Logik zur Auswahl/Bearbeitung des Inhalts?
   * Die Logik sollte getrennt von der Ebene der Benutzeroberfläche aufbewahrt werden. HTL dient dazu, dies sicherzustellen.
* Benötigt Ihre Komponente eine CSS-Formatierung?
   * Eine CSS-Formatierung sollte getrennt von den Komponentendefinitionen aufbewahrt werden. Legen Sie Konventionen für die Benennung der HTML-Elemente fest, damit Sie sie über externe CSS-Dateien modifizieren können.
* Welche Sicherheitsauswirkungen kann Ihre neue Komponente haben?

### Wiederverwenden vorhandener Komponenten {#reusing-components}

Bevor Sie Zeit in die Erstellung einer völlig neuen Komponente investieren, sollten Sie die Anpassung oder Erweiterung vorhandener Komponenten in Erwägung ziehen. [Die Core ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) Component bietet eine Reihe flexibler, robuster und bewährter produktionsfähiger Komponenten.

#### Erweitern der Kernkomponenten {#extending-core-components}

Die Kernkomponenten werden auch mit dem Angebot [clear customization patterns](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html) versehen, das Sie verwenden können, um sie an die Anforderungen Ihres eigenen Projekts anzupassen.

#### Komponenten überlagern {#overlying-components}

Komponenten können auch mit einer [Überlagerung](/help/implementing/developing/introduction/overlays.md) neu definiert werden, basierend auf der Suchpfadlogik. In diesem Fall wird jedoch der [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) nicht ausgelöst und `/apps` muss die gesamte Überlagerung definieren.

#### Erweitern von Komponentendialogen {#extending-component-dialogs}

Es ist auch möglich, ein Komponentendialogfeld mithilfe des Sling Resource Mergers zu überschreiben und die Eigenschaft `sling:resourceSuperType` zu definieren.

Das bedeutet, dass Sie nur die erforderlichen Unterschiede neu definieren müssen, anstatt den gesamten Dialog neu zu definieren.

### Inhaltslogik und Rendering-Markup  {#content-logic-and-rendering-markup}

Ihre Komponente wird mit [HTML gerendert.](https://www.w3schools.com/htmL/html_intro.asp) Ihre Komponente muss den HTML-Code definieren, der erforderlich ist, um den erforderlichen Inhalt zu übernehmen und anschließend in der Autoren- und Veröffentlichungsumgebung nach Bedarf zu rendern.

Es empfiehlt sich, den für Markup und Rendering zuständigen Code getrennt von dem Code zu halten, der die Logik zur Auswahl des Komponenteninhalts enthält.

Dieser Ansatz wird durch [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html) unterstützt, eine Vorlagensprache, die dazu dient sicherzustellen, dass eine echte Programmiersprache für die Definition der zugrunde liegenden Geschäftslogik genutzt wird. Dieser Mechanismus kennzeichnet den Code, der für eine bestimmte Ansicht aufgerufen wird, und lässt bei Bedarf eine spezifische Logik für unterschiedliche Ansichten derselben Komponente zu.

Diese (optionale) Logik kann auf unterschiedliche Weise implementiert werden und wird von HTML mit bestimmten Befehlen aufgerufen:

* Mit Java - [Die HTML Java Use-API](https://helpx.adobe.com/experience-manager/htl/using/use-api-java.html) ermöglicht einer HTML-Datei den Zugriff auf Hilfsmethoden in einer benutzerdefinierten Java-Klasse. Dies ermöglicht es Ihnen, Java-Code zu verwenden, um die Logik zum Auswählen und Konfigurieren des Komponenteninhalts zu implementieren.
* Verwenden von JavaScript - [Die HTML-JavaScript-Use-API](https://experienceleague.adobe.com/docs/experience-manager-htl/using/htl/use-api-javascript.html) aktiviert eine HTML-Datei, um auf in JavaScript geschriebenen Helfercode zuzugreifen. Dies ermöglicht es Ihnen, JavaScript-Code zu verwenden, um die Logik zum Auswählen und Konfigurieren des Komponenteninhalts zu implementieren.
* Verwendung clientseitiger Bibliotheken - Moderne Websites basieren in hohem Maße auf clientseitiger Verarbeitung, die durch komplexen JavaScript- und CSS-Code gesteuert wird. Weitere Informationen finden Sie im Dokument [Verwenden clientseitiger Bibliotheken auf AEM als Cloud Service](/help/implementing/developing/introduction/clientlibs.md).

## Komponentenstruktur {#structure}

Die Struktur einer AEM Komponente ist leistungsstark und flexibel. Die wichtigsten Bestandteile sind:

* [Ressourcentyp](#resource-type)
* [Komponentendefinition](#component-definition)
* [Eigenschaften und untergeordnete Knoten einer Komponente](#properties-and-child-nodes-of-a-component)
* [Dialogfelder](#dialogs)
* [Designdialogfelder](#design-dialogs)

### Ressourcentyp {#resource-type}

Ein zentrales Element der Struktur ist der Ressourcentyp.

* Die Inhaltsstruktur erklärt Absichten.
* Der Ressourcentyp implementiert sie.

Dies ist eine Abstraktion, die hilft sicherzustellen, dass selbst wenn sich das Aussehen und Gefühl im Laufe der Zeit ändert, dass die Absicht bleibt die Zeit.

### Komponentendefinition {#component-definition}

Die Definition einer Komponente lässt sich wie folgt aufschlüsseln:

* AEM-Komponenten basieren auf [Sling.](https://sling.apache.org/documentation.html)
* AEM Komponenten befinden sich unter `/libs/core/wcm/components`.
* Projekt-/Site-spezifische Komponenten befinden sich unter `/apps/<myApp>/components`.
* AEM-Standardkomponenten sind als `cq:Component` definiert und haben die folgenden zentralen Elemente:
   * jcr-Eigenschaften - Eine Liste von jcr-Eigenschaften. Diese sind variabel und einige können optional sein, wenn die Basisstruktur eines Komponentenknotens, seine Eigenschaften und Unterknoten durch die Definition von `cq:Component` definiert werden.
   * Ressourcen: Diese definieren Statische Element, die von der Komponente verwendet werden.
   * Skripten - Diese werden verwendet, um das Verhalten der resultierenden Instanz der Komponente zu implementieren.

#### Wichtige Eigenschaften {#vital-properties}

* **Stammknoten**:
   * `<mycomponent> (cq:Component)` - Hierarchie-Knoten der Komponente.
* **Wichtige Eigenschaften**:
   * `jcr:title` - Titel der Komponente; wird beispielsweise als Bezeichnung verwendet, wenn die Komponente in der  [Komponenten-](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) Browser- und  [Komponentenkonsole aufgeführt wird](/help/sites-cloud/authoring/features/components-console.md)
   * `jcr:description` - Beschreibung der Komponente; als Mauszeiger im Komponentenbrowser und in der Komponentenkonsole verwendet
   * Weitere Informationen finden Sie im Abschnitt [Komponentensymbol](#component-icon)
* **Wichtige untergeordnete Knoten**:
   * `cq:editConfig (cq:EditConfig)` - Definiert die Bearbeitungseigenschaften der Komponente und ermöglicht die Anzeige der Komponente im Komponentenbrowser
      * Wenn die Komponente über ein Dialogfeld verfügt, wird sie automatisch im Komponenten-Browser oder im Sidekick angezeigt, auch wenn cq:editConfig nicht vorhanden ist.
   * `cq:childEditConfig (cq:EditConfig)` - Steuert die Aspekte der Autorenbenutzeroberfläche für untergeordnete Komponenten, die keine eigenen definieren  `cq:editConfig`.
   * `cq:dialog (nt:unstructured)` - Dialog für diese Komponente. Definiert die Oberfläche, über die Benutzer die Komponente konfigurieren und/oder Inhalte bearbeiten können.
   * `cq:design_dialog (nt:unstructured)` - Designbearbeitung für diese Komponente

#### Komponentensymbol {#component-icon}

Das Symbol oder die Abkürzung für die Komponente wird über die JCR-Eigenschaften der Komponente definiert, wenn die Komponente vom Entwickler erstellt wird. Diese Eigenschaften werden in der folgenden Reihenfolge ausgewertet und die erste erkannte gültige Eigenschaft wird verwendet.

1. `cq:icon` - String-Eigenschaft, die auf ein Standardsymbol in der  [Coral UI-Bibliothek verweist und im Komponenten-Browser angezeigt ](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html) wird
   * Verwenden Sie den Wert des HTML-Attributs des Coral-Symbols.
1. `abbreviation` - String-Eigenschaft zum Anpassen der Abkürzung des Komponentennamens im Komponenten-Browser
   * Die Abkürzung sollte auf zwei Zeichen beschränkt sein.
   * Bei einem leeren String wird die Abkürzung aus den ersten beiden Buchstaben der Eigenschaft `jcr:title` gebildet.
      * Beispiel: „Gr“ für „Grafik“.
      * Zum Erstellen der Abkürzung wird der lokalisierte Titel verwendet.
   * Die Abkürzung wird nur übersetzt, wenn die Komponente die Eigenschaft `abbreviation_commentI18n` aufweist, die dann als Anweisung für eine Übersetzung genutzt wird.
1. `cq:icon.png` oder  `cq:icon.svg` - Symbol für diese Komponente, das im Komponenten-Browser angezeigt wird
   * Symbole von Standardkomponenten haben eine Größe von 20 x 20 Pixeln.
      * Größere Symbole werden verkleinert (clientseitig).
   * Die empfohlene Farbe ist rgb(112, 112, 112) > #707070
   * Der Hintergrund von Symbolen von Standardkomponenten ist transparent.
   * Es werden nur die Dateien `.png` und `.svg` unterstützt.
   * Beim Import aus dem Dateisystem über das Eclipse-Plugin müssen Dateinamen beispielsweise mit `_cq_icon.png` oder `_cq_icon.svg` gekennzeichnet werden.
   * `.png` hat Vorrang,  `.svg` wenn beide vorhanden sind.

Wenn keine der oben genannten Eigenschaften (`cq:icon`, `abbreviation`, `cq:icon.png` oder `cq:icon.svg`) für die Komponente gefunden wird:

* Das System sucht nach denselben Eigenschaften bei den übergeordneten Komponenten, die der Eigenschaft `sling:resourceSuperType` folgen.
* Wenn auf der Superkomponentenebene nichts oder eine leere Abkürzung gefunden wird, erstellt das System die Abkürzung aus den ersten Buchstaben der `jcr:title`-Eigenschaft der aktuellen Komponente.

Um die Vererbung von Symbolen von übergeordneten Komponenten zu deaktivieren, legen Sie eine leere Eigenschaft `abbreviation` für die Komponente fest. Das Standardverhalten wird daraufhin erneut aktiviert.

Die [Komponentenkonsole](/help/sites-cloud/authoring/features/components-console.md#component-details) zeigt an, wie das Symbol für eine bestimmte Komponente definiert wird.

#### Beispiel: SVG-Symbol {#svg-icon-example}

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "https://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" id="Layer_1" xmlns="https://www.w3.org/2000/svg" xmlns:xlink="https://www.w3.org/1999/xlink" x="0px" y="0px"
     width="20px" height="20px" viewBox="0 0 20 20" enable-background="new 0 0 20 20" xml:space="preserve">
    <ellipse cx="5" cy="5" rx="3" ry="3" fill="#707070"/>
    <ellipse cx="15" cy="5" rx="4" ry="4" fill="#707070"/>
    <ellipse cx="5" cy="15" rx="5" ry="5" fill="#707070"/>
    <ellipse cx="15" cy="15" rx="4" ry="4" fill="#707070"/>
</svg>
```

### Eigenschaften und untergeordnete Knoten einer Komponente {#properties-and-child-nodes-of-a-component}

Viele der Knoten/Eigenschaften, die für die Definition einer Komponente erforderlich sind, sind in beiden Benutzeroberflächen zu finden. Die Unterschiede bleiben unabhängig, sodass Ihre Komponente in beiden Umgebungen funktioniert.

Eine Komponente ist ein Knoten des Typs `cq:Component` mit den folgenden Eigenschaften und untergeordneten Knoten:

| Name | Typ | Beschreibung |
|---|---|---|
| `.` | `cq:Component` | Dies stellt die aktuelle Komponente dar. Eine Komponente ist vom Knotentyp `cq:Component`. |
| `componentGroup` | `String` | Dies stellt die Gruppe dar, unter der die Komponente im [Komponenten-Browser ausgewählt werden kann.](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) Ein Wert, der mit beginnt,  `.` wird für Komponenten verwendet, die nicht in der Benutzeroberfläche ausgewählt werden können, wie zum Beispiel Basiskomponenten, von denen andere Komponenten erben. |
| `cq:isContainer` | `Boolean` | Dies gibt an, ob es sich bei der Komponente um eine Container-Komponente handelt, die daher andere Komponenten wie ein Absatzsystem enthalten kann. |
| `cq:dialog` | `nt:unstructured` | Dies ist die Definition des Dialogfelds zum Bearbeiten der Komponente. |
| `cq:design_dialog` | `nt:unstructured` | Dies ist die Definition des Designdialogs für die Komponente. |
| `cq:editConfig` | `cq:EditConfig` | Dadurch wird die [Bearbeitungskonfiguration der Komponente definiert.](#edit-behavior) |
| `cq:htmlTag` | `nt:unstructured` | Dadurch werden zusätzliche Tag-Attribute zurückgegeben, die dem umgebenden HTML-Tag hinzugefügt werden. Ermöglicht das Hinzufügen von Attributen zu den automatisch generierten div-Tags. |
| `cq:noDecoration` | `Boolean` | Bei „true“ wird die Komponente nicht mit automatisch erstellten div- und CSS-Klassen gerendert. |
| `cq:template` | `nt:unstructured` | Wenn dieser Knoten gefunden wird, wird er als Inhaltsvorlage verwendet, wenn die Komponente aus dem Komponentenbrowser hinzugefügt wird. |
| `jcr:created` | `Date` | Dies ist das Erstellungsdatum der Komponente. |
| `jcr:description` | `String` | Dies ist die Beschreibung der Komponente. |
| `jcr:title` | `String` | Dies ist der Titel der Komponente. |
| `sling:resourceSuperType` | `String` | Wenn dieser Wert festgelegt ist, erbt die Komponente von dieser Komponente. |
| `component.html` | `nt:file` | Dies ist die HTML-Skriptdatei der Komponente. |
| `cq:icon` | `String` | Dieser Wert verweist auf das [Symbol der Komponente](#component-icon) und wird im Komponentenbrowser angezeigt. |

Wenn wir die Komponente **Text** betrachten, sehen wir eine Reihe dieser Elemente:

![Textkomponentenstruktur](assets/components-text.png)

Zu den wichtigen Eigenschaften gehören:

* `jcr:title` - Dies ist der Titel der Komponente, die zur Identifizierung der Komponente im Komponenten-Browser verwendet wird.
* `jcr:description` - Dies ist die Beschreibung der Komponente.
* `sling:resourceSuperType` - Dies zeigt den Pfad der Vererbung an, wenn eine Komponente erweitert wird (durch Überschreiben einer Definition).

Zu den wichtigen untergeordneten Knoten gehören:

* `cq:editConfig` - Hiermit werden visuelle Aspekte der Komponente bei der Bearbeitung gesteuert.
* `cq:dialog` - Hiermit wird der Dialog zum Bearbeiten des Inhalts dieser Komponente definiert.
* `cq:design_dialog` - Hiermit werden die Designbearbeitungsoptionen für diese Komponente festgelegt.

### Dialogfelder {#dialogs}

Dialoge sind ein Schlüsselelement Ihrer Komponente, da sie eine Schnittstelle für Autoren zur Konfiguration der Komponente auf einer Inhaltsseite und zur Eingabe für diese Komponente bieten. Weitere Informationen zur Interaktion von Inhaltserstellern mit Komponenten finden Sie in der [Authoring-Dokumentation](/help/sites-cloud/authoring/fundamentals/editing-content.md).

Je nach Komplexität der Komponente benötigen Sie eventuell eine oder mehrere Registerkarten.

Dialoge für AEM Komponenten:

* Sind `cq:dialog` Knoten des Typs `nt:unstructured`.
* befinden sich unter ihren `cq:Component`-Knoten und neben ihren Komponentendefinitionen.
* Definieren Sie das Dialogfeld zum Bearbeiten des Inhalts dieser Komponente.
* werden mit Granite-UI-Komponenten definiert.
* werden serverseitig (als Sling-Komponenten) basierend auf ihrer Inhaltsstruktur und der `sling:resourceType`-Eigenschaft gerendert.
* Enthält eine Knotenstruktur, die die Felder im Dialogfeld beschreibt
   * Diese Knoten sind `nt:unstructured` mit der erforderlichen `sling:resourceType`-Eigenschaft.

![Dialogfelddefinition der Titelkomponente](assets/components-title-dialog.png)

In diesem Dialogfeld werden einzelne Felder definiert:

![Felder der Dialogdefinition der Titel-Komponente](assets/components-title-dialog-items.png)

### Designdialogfelder {#design-dialogs}

Designdialogfelder ähneln den Dialogfeldern, die zum Bearbeiten und Konfigurieren von Inhalten verwendet werden. Sie bieten jedoch die Oberfläche, über die Vorlagenautoren Designdetails für diese Komponente in einer Seitenvorlage konfigurieren und bereitstellen können. Seitenvorlagen werden dann von den Inhaltserstellern zum Erstellen von Inhaltsseiten verwendet. Weitere Informationen zum Erstellen von Vorlagen finden Sie in der [Vorlagendokumentation](/help/sites-cloud/authoring/features/templates.md).

[Beim Bearbeiten einer Seitenvorlage](/help/sites-cloud/authoring/features/templates.md) werden Designdialogfelder verwendet, die jedoch nicht für alle Komponenten benötigt werden. Beispielsweise verfügen die Komponenten **title** und **Image Components** über Designdialogfelder, die Komponente **Social Media Sharing** nicht.

### Coral- und Granite-Benutzeroberfläche {#coral-and-granite}

Die Benutzeroberfläche von Korallen und Granite definieren das Aussehen und Erscheinungsbild von AEM.

* [Die Coral-](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) Benutzeroberfläche bietet eine einheitliche Benutzeroberfläche für alle Cloud-Lösungen.
* [Granite ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html) UIstellt Coral UI-Markup bereit, das in Sling-Komponenten eingeschlossen ist, um UI-Konsolen und -Dialoge zu erstellen.

Die Granite-Benutzeroberfläche bietet eine große Auswahl an grundlegenden Widgets, die zum Erstellen Ihres Dialoges auf der Authoring-Umgebung benötigt werden. Falls erforderlich, können Sie diese Auswahl erweitern und Ihr eigenes Widget erstellen.

Weitere Informationen finden Sie in den folgenden Ressourcen:

* [Coral-Benutzeroberfläche - Handbuch](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html)
* [Dokumentattion zur Granite-Benutzeroberfläche](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
* [Struktur der AEM-UI](/help/implementing/developing/introduction/ui-structure.md)

### Anpassen von Dialogfeldern {#customizing-dialog-fields}

>[!TIP]
>
>Informationen zum Anpassen von Dialogfeldern finden Sie unter [AEM Gems session](https://docs.adobe.com/content/ddc/en/gems/customizing-dialog-fields-in-touch-ui.html).

Zum Erstellen eines neuen Widgets zur Verwendung in einem Komponentendialogfeld müssen Sie eine neue Granite-UI-Feldkomponente erstellen.

Wenn Sie das Dialogfeld für einen einfachen Container für ein Formularelement halten, können Sie den Primärinhalt Ihres Dialogfeldinhalts als auch Formularfelder sehen. Um ein neues Formularfeld zu erstellen, müssen Sie einen Ressourcentyp erstellen. Dies entspricht dem Erstellen einer neuen Komponente. Um Ihnen bei dieser Aufgabe zu helfen, bietet die Granite-Benutzeroberfläche eine generische Feldkomponente, von der eine Vererbung möglich ist (mithilfe von `sling:resourceSuperType`):

`/libs/granite/ui/components/coral/foundation/form/field`

Die Granite-Benutzeroberfläche bietet eine Reihe von Feldkomponenten, die für die Verwendung in Dialogen oder allgemein in [Formularen geeignet sind.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)

Sobald Sie Ihren Ressourcentyp erstellt haben, können Sie Ihr Feld instanziieren, indem Sie in Ihrem Dialogfeld einen neuen Knoten hinzufügen, wobei die Eigenschaft `sling:resourceType` auf den Ressourcentyp verweist, den Sie gerade eingeführt haben.

#### Zugriff auf Dialogfelder {#access-to-dialog-fields}

Sie können auch Render-Bedingungen (`rendercondition`) verwenden, um festzulegen, wer Zugriff auf bestimmte Registerkarten/Felder in Ihrem Dialogfeld hat. beispielsweise:

```text
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

## Verwenden von Komponenten {#using-components}

Nachdem Sie eine Komponente erstellt haben, müssen Sie sie aktivieren, um sie verwenden zu können. Es zeigt, wie die Struktur der Komponente mit der Struktur des resultierenden Inhalts im Repository zusammenhängt.

### Hinzufügen der Komponente zur Vorlage {#adding-your-component-to-the-template}

Nachdem eine Komponente definiert wurde, muss sie zur Verwendung bereitgestellt werden. Damit eine Komponente in einer Vorlage verwendet werden kann, müssen Sie sie in der Richtlinie des Layout-Containers der Vorlage aktivieren.

Weitere Informationen zum Erstellen von Vorlagen finden Sie in der [Vorlagendokumentation](/help/sites-cloud/authoring/features/templates.md).

### Komponenten und die von ihnen erstellten Inhalte {#components-and-the-content-they-create}

Wenn Sie eine Instanz der Komponente **Title** auf der Seite erstellen und konfigurieren: `/content/wknd/language-masters/en/adventures/extreme-ironing.html`

![Titel bearbeiten, Dialogfeld](assets/components-title-dialog.png)

Dann sehen wir die Struktur des Inhalts, der innerhalb des Repositorys erstellt wurde:

![Knotenstruktur der Titelkomponente](assets/components-title-content-nodes.png)

Insbesondere wenn Sie sich den tatsächlichen Text einer **Title-Komponente** ansehen:

* Der Inhalt enthält eine `jcr:title`-Eigenschaft mit dem tatsächlichen Text des Titels, den der Autor eingegeben hat.
* Es enthält auch einen `sling:resourceType` Verweis auf die Komponentendefinition.

Die definierten Eigenschaften sind von den einzelnen Definitionen abhängig. Zwar können sie komplexer als oben dargestellt sein, folgen aber dennoch denselben grundlegenden Prinzipien.

## Komponentenhierarchie und Vererbung {#component-hierarchy-and-inheritance}

Komponenten in AEM unterliegen der **Ressourcentyp-Hierarchie**. Dies wird zum Erweitern von Komponenten mithilfe der Eigenschaft `sling:resourceSuperType` verwendet. Dadurch kann die Komponente von einer anderen Komponente geerbt werden.

Weitere Informationen finden Sie im Abschnitt [Komponenten wiederverwenden](#reusing-components).

## Bearbeitungsverhalten {#edit-behavior}

In diesem Abschnitt wird beschrieben, wie Sie das Bearbeitungsverhalten einer Komponente konfigurieren. Dazu gehören Attribute wie für die Komponente verfügbare Aktionen, Eigenschaften des In.place-Editors und Listener für Ereignis in der Komponente.

Um das Bearbeitungsverhalten einer Komponente zu konfigurieren, fügen Sie einen `cq:editConfig`-Knoten des Typs `cq:EditConfig` unter dem Komponentenknoten (des Typs `cq:Component`) hinzu sowie spezifische Eigenschaften und untergeordnete Knoten. Die folgenden Funktionen und untergeordneten Knoten sind verfügbar:

* `cq:editConfig` Knoteneigenschaften
* [`cq:editConfig` untergeordnete Knoten](#configuring-with-cq-editconfig-child-nodes):
   * `cq:dropTargets` (Knotentyp  `nt:unstructured`): definiert eine Liste von Dropdown-Zielgruppen, die das Ablegen eines Assets der Inhaltssuche akzeptieren können (eine einzelne Dropdown-Zielgruppe ist zulässig).
   * `cq:inplaceEditing` (Knotentyp  `cq:InplaceEditingConfig`): definiert eine ersetzende Bearbeitungskonfiguration für die Komponente
   * `cq:listeners` (Knotentyp  `cq:EditListenersConfig`): definiert, was vor oder nach einer Aktion für die Komponente geschieht

Es gibt viele bestehende Konfigurationen in AEM. Mit dem Tool Abfrage in **CRXDE Lite** können Sie ganz einfach nach bestimmten Eigenschaften oder untergeordneten Knoten suchen.

### Komponentenplatzhalter {#component-placeholders}

Komponenten müssen immer HTML-Inhalte wiedergeben, die für den Autor sichtbar sind, auch wenn die Komponente keinen Inhalt hat. Andernfalls könnte es visuell aus der Benutzeroberfläche des Editors verschwinden, sodass es technisch vorhanden, aber auf der Seite und im Editor unsichtbar ist. In einem solchen Fall sind die Autoren nicht in der Lage, die leere Komponente auszuwählen und mit ihr zu interagieren.

Aus diesem Grund sollten Komponenten einen Platzhalter wiedergeben, solange sie keine sichtbare Ausgabe wiedergeben, wenn die Seite im Seiteneditor wiedergegeben wird (wenn der WCM-Modus `edit` oder `preview` ist).
Das typische HTML-Markup für einen Platzhalter ist Folgendes:

```HTML
<div class="cq-placeholder" data-emptytext="Component Name"></div>
```

Das typische HTML-Skript, das den obigen Platzhalter-HTML-Code wiedergibt, lautet wie folgt:

```HTML
<div class="cq-placeholder" data-emptytext="${component.properties.jcr:title}"
     data-sly-test="${(wcmmode.edit || wcmmode.preview) && isEmpty}"></div>
```

Im vorherigen Beispiel ist `isEmpty` eine Variable, die nur dann wahr ist, wenn die Komponente keinen Inhalt hat und für den Autor unsichtbar ist.

Um Wiederholungen zu vermeiden, empfiehlt Adobe, dass Komponentenimplementierer für diese Platzhalter eine HTML-Vorlage verwenden, [wie die von den Hauptkomponenten bereitgestellten.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/commons/v1/templates.html)

Die Verwendung der Vorlage im vorherigen Link erfolgt dann mit der folgenden HTML-Zeile:

```HTML
<sly data-sly-use.template="core/wcm/components/commons/v1/templates.html"
     data-sly-call="${template.placeholder @ isEmpty=!model.text}"></sly>
```

Im vorherigen Beispiel ist `model.text` die Variable, die nur dann wahr ist, wenn der Inhalt Inhalte enthält und sichtbar ist.

Ein Beispiel für die Verwendung dieser Vorlage ist in den Hauptkomponenten, [wie in der Titelkomponente zu finden.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/title/v2/title/title.html#L27)

### Konfigurieren mit untergeordneten cq:EditConfig-Knoten {#configuring-with-cq-editconfig-child-nodes}

#### Löschen von Assets in einem Dialogfeld - cq:dropTargets {#cq-droptargets}

Der Knoten `cq:dropTargets` (Knotentyp `nt:unstructured`) definiert die Dropdown-Zielgruppe, die ein Ablegen eines aus der Inhaltssuche gezogenen Assets akzeptieren kann. Es ist ein Knoten des Typs `cq:DropTargetConfig`.

Die untergeordnete Node des Typs `cq:DropTargetConfig` definiert eine Drop-Zielgruppe in der Komponente.

### In-Place-Bearbeitung - cq:inplaceEditing {#cq-inplaceediting}

Mit einem ersetzenden Editor können Benutzer Inhalte direkt im Inhaltsfluss bearbeiten, ohne dass ein Dialogfeld geöffnet werden muss. Beispielsweise verfügen die Standardkomponenten **Text** und **Titel** über einen Inp-Lace-Editor.

Ein ersetzender Editor ist nicht für jeden Komponententyp erforderlich/sinnvoll.

Der Knoten `cq:inplaceEditing` (Knotentyp `cq:InplaceEditingConfig`) definiert eine ersetzende Bearbeitungskonfiguration für die Komponente. Er kann die folgenden Eigenschaften aufweisen:

| Eigenschaftsname | Eigenschaftstyp | Eigenschaftswert |
|---|---|---|
| `active` | `Boolean` | `true` , um die ersetzende Bearbeitung der Komponente zu aktivieren. |
| `configPath` | `String` | Pfad der Editorkonfiguration, der von einem Konfigurationsknoten angegeben werden kann |
| `editorType` | `String` | Die verfügbaren Typen sind: `plaintext` für Nicht-HTML-Inhalte konvertiert `title` grafische Titel vor Beginn der Bearbeitung in einen Klartext und `text` verwendet den Rich-Text-Editor |

Die folgende Konfiguration ermöglicht die Bearbeitung der Komponente im Inp-Space und definiert `plaintext` als Editortyp:

```text
    <cq:inplaceEditing
        jcr:primaryType="cq:InplaceEditingConfig"
        active="{Boolean}true"
        editorType="plaintext"/>
```

### Verarbeiten von Field-Ereignissen - cq:listeners {#cq-listeners}

Die Methode zum Umgang mit Ereignissen in Dialogfeldern erfolgt mit Listenern in einer benutzerdefinierten [Client-Bibliothek.](/help/implementing/developing/introduction/clientlibs.md)

Um Logik in Ihr Feld zu injizieren, sollten Sie Folgendes beachten:

* Lassen Sie Ihr Feld mit einer bestimmten CSS-Klasse (dem Hook) markieren.
* Definieren Sie in Ihrer Client-Bibliothek einen JS-Listener, der auf diesem CSS-Klassennamen basiert (dies stellt sicher, dass Ihre benutzerdefinierte Logik nur auf Ihr Feld angewendet wird und keine Auswirkungen auf andere Felder desselben Typs hat).

Um dies zu erreichen, müssen Sie die zugrunde liegende Widget-Bibliothek kennen, mit der Sie interagieren möchten. [Informationen darüber, auf welches Ereignis Sie reagieren möchten, finden Sie in der Dokumentation zur Coral-Benutzeroberfläche](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html).

Der Knoten `cq:listeners` (Knotentyp `cq:EditListenersConfig`) definiert, was vor oder nach einer Aktion für die Komponente geschieht. In der folgenden Tabelle sind die möglichen Eigenschaften aufgeführt.

| Eigenschaftsname | Eigenschaftswert |
|---|---|
| `beforedelete` | Der Handler wird ausgelöst, bevor die Komponente entfernt wird. |
| `beforeedit` | Der Handler wird ausgelöst, bevor die Komponente bearbeitet wird. |
| `beforecopy` | Der Handler wird ausgelöst, bevor die Komponente kopiert wird. |
| `beforeremove` | Der Handler wird ausgelöst, bevor die Komponente verschoben wird. |
| `beforeinsert` | Der Handler wird ausgelöst, bevor die Komponente eingefügt wird. |
| `beforechildinsert` | Der Handler wird ausgelöst, bevor die Komponente in eine andere Komponente eingefügt wird (nur Container). |
| `afterdelete` | Der Handler wird ausgelöst, nachdem die Komponente entfernt wurde. |
| `afteredit` | Der Handler wird ausgelöst, nachdem die Komponente bearbeitet wurde. |
| `aftercopy` | Der Handler wird ausgelöst, nachdem die Komponente kopiert wurde. |
| `afterinsert` | Der Handler wird ausgelöst, nachdem die Komponente eingefügt wurde. |
| `aftermove` | Der Handler wird ausgelöst, nachdem die Komponente verschoben wurde. |
| `afterchildinsert` | Der Handler wird ausgelöst, nachdem die Komponente in eine andere Komponente eingefügt wurde (nur Container). |

>[!NOTE]
>
>Bei verschachtelten Komponenten gibt es bestimmte Einschränkungen bezüglich der Aktionen, die als Eigenschaften auf dem Knoten `cq:listeners` definiert werden. Bei verschachtelten Komponenten **müssen** die Werte der folgenden Eigenschaften `REFRESH_PAGE` sein:
>
>* `aftermove`
>* `aftercopy`


Der Ereignis-Handler kann mit einer angepassten Implementierung implementiert werden. Beispiel (hier ist `project.customerAction` eine statische Methode):

`afteredit = "project.customerAction"`

Das folgende Beispiel entspricht der `REFRESH_INSERTED`-Konfiguration:

`afterinsert="function(path, definition) { this.refreshCreated(path, definition); }"`

Mit der folgenden Konfiguration wird die Seite aktualisiert, nachdem die Komponente gelöscht, bearbeitet, eingefügt oder verschoben wurde:

```text
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afterdelete="REFRESH_PAGE"
        afteredit="REFRESH_PAGE"
        afterinsert="REFRESH_PAGE"
        afterMove="REFRESH_PAGE"/>
```

### Feldüberprüfung {#field-validation}

Die Feldüberprüfung in der Granite-Benutzeroberfläche und den Granite-UI-Widgets erfolgt mit der API `foundation-validation`. Weitere Informationen finden Sie in der Granite-Dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html).[`foundation-valdiation`

### Erkennen der Verfügbarkeit des Dialogfelds {#dialog-ready}

Wenn Sie über ein benutzerdefiniertes JavaScript verfügen, das nur ausgeführt werden muss, wenn das Dialogfeld verfügbar und bereit ist, sollten Sie auf das `dialog-ready`-Ereignis achten.

Dieses Ereignis wird ausgelöst, wenn das Dialogfeld geladen (oder erneut geladen) wird und einsatzbereit ist, d. h. wenn eine Änderung (Erstellen/Aktualisieren) im DOM des Dialogfelds erfolgt.

`dialog-ready` kann verwendet werden, um in JavaScript benutzerspezifischen Code einzubinden, der Anpassungen an den Feldern in einem Dialogfeld oder ähnlichen Aufgaben durchführt.

## Verhalten der Vorschau {#preview-behavior}

Der [WCM-Modus](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html)-Cookie wird beim Wechsel in den Vorschaumodus gesetzt, auch wenn die Seite nicht aktualisiert wird.

Komponenten mit einem Rendering, die für den WCM-Modus empfindlich sind, müssen so definiert werden, dass sie sich selbst aktualisieren und sich dann auf den Wert des Cookies verlassen.

## Dokumentationskomponenten {#documenting-components}

Als Entwickler benötigen Sie einen einfachen Zugriff auf die Komponentendokumentation, damit Sie die Komponenten schnell verstehen können:

* Beschreibung
* Beabsichtigter Verwendungszweck
* Inhaltstruktur und Eigenschaften
* Ausgesetzte APIs und Erweiterungspunkte
* usw.

Aus diesem Grund ist es sehr einfach, einen vorhandenen Dokumentations-Markdown innerhalb der Komponente selbst vorzunehmen.

Sie müssen lediglich eine `README.md`-Datei in der Komponentenstruktur platzieren.

![README.md in der Komponentenstruktur](assets/components-documentation.png)

Diese Markierung wird dann in der [Komponentenkonsole angezeigt.](/help/sites-cloud/authoring/features/components-console.md)

![README.md in der Komponentenkonsole sichtbar](assets/components-documentation-console.png)

Das unterstützte Markdown ist dasselbe wie bei [Inhaltsfragmenten.](/help/assets/content-fragments/content-fragments.md)