---
title: Stilsystem
description: Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.
translation-type: tm+mt
source-git-commit: 130b372a9450c5c632715b098fd5c5ebf61bdf0d
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 93%

---


# Stilsystem{#style-system}

Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um die Komponente flexibler zu gestalten.

So muss nicht eigens für jeden Stil eine benutzerdefinierte Komponente entwickelt oder der Komponentendialog angepasst werden, um eine derartige Stilfunktionalität zu ermöglichen. Das Resultat sind mehr wiederverwendbare Komponenten, die schnell und einfach an die Bedürfnisse von Inhaltsautoren angepasst werden können, ohne dass eine AEM-Back-End-Entwicklung erforderlich ist.

## Nutzungsszenario     {#use-case}

Vorlagenautoren müssen nicht nur die Funktionsweise der Komponenten für die Inhaltsautoren konfigurieren können, sondern auch eine Reihe alternativer visueller Varianten einer Komponente.

Genauso müssen Inhaltsautoren ihre Inhalte nicht nur strukturieren und anordnen können. Sie müssen auch auswählen können, wie der Inhalt visuell präsentiert wird.

Das Stilsystem bietet eine einheitliche Lösung für die Anforderungen des Vorlagenautors und des Inhaltsautors:

* Vorlagenautoren können in den Inhaltsrichtlinien für Komponenten Stilklassen festlegen.
* Inhaltsautoren können diese Klassen später aus einem Dropdown-Menü auswählen, wenn sie die Komponente auf einer Seite bearbeiten, um die jeweiligen Stile darauf anzuwenden.

Die Stilklasse wird daraufhin in das Decoration-Wrapper-Element der Komponente eingefügt, sodass sich der Komponentenentwickler nicht mit der Handhabung der Stile über die Bereitstellung der CSS-Regeln hinaus befassen muss.

## Übersicht {#overview}

Die allgemeine Verwendung des Stilsystems sieht wie folgt aus.

1. Der Webdesigner erstellt unterschiedliche visuelle Varianten einer Komponente.

1. Dem HTML-Entwickler werden die HTML-Ausgabe der Komponenten sowie die zu implementierenden visuellen Varianten zur Verfügung übermittelt.

1. Der HTML-Entwickler definiert die CSS-Klassen, die der jeweiligen visuellen Variante entsprechen und die in das Wrapper-Element der Komponenten eingefügt werden sollen.

1. Der HTML-Entwickler implementiert den entsprechenden CSS-Code (und optional JS-Code) für die einzelnen visuellen Varianten, damit diese wie definiert angezeigt werden.

1. Der AEM-Entwickler legt den bereitgestellten CSS-Code (und optional JS-Code) in einer Client-Bibliothek ab und stellt ihn bereit. <!--The AEM developer places the provided CSS (and optional JS) in a [Client Library](/help/sites-developing/clientlibs.md) and deploys it.-->

1. Der AEM-Entwickler oder der Vorlagenautor konfiguriert die Seitenvorlagen und bearbeitet die Richtlinien für die formatierten Komponenten mit den definierten CSS-Klassen. Dabei legt er benutzerfreundliche Namen für die einzelnen Stile fest und definiert, welche Stile kombiniert werden können.

1. Der AEM-Seitenautor kann die entworfenen Stile daraufhin über das Stilmenü in der Symbolleiste einer Komponente im Seiten-Editor auswählen.

Beachten Sie, dass nur die letzten drei Schritte direkt in AEM ausgeführt werden. Das bedeutet, dass die gesamte erforderliche CSS- und JavaScript-Entwicklung ohne AEM durchgeführt werden kann.

Für die eigentliche Implementierung der Stile ist nur die Bereitstellung in AEM sowie die Auswahl innerhalb der Komponenten der gewünschten Vorlagen erforderlich.

Das folgende Diagramm veranschaulicht die Architektur des Stilsystems.

![aem-style-system](/help/sites-cloud/authoring/assets/style-system-architecture.png)

## Verwenden {#use}

Zur Veranschaulichung der Funktion werden wir die [WKND](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)-Implementierung der Komponente [Titel](https://www.adobe.com/go/aem_cmp_title_v2_de) der Kernkomponente als Beispiel verwenden.

In den folgenden Abschnitten [Als Inhaltsautor](#as-a-content-author) und [Als Vorlagenautor](#as-a-template-author) wird beschrieben, wie Sie die Funktionalität des Stilsystems mit dem WKND-Stilsystem testen können.

Wenn Sie das Stilsystem für Ihre eigenen Komponenten verwenden möchten, gehen Sie wie folgt vor:

1. Installieren Sie den CSS-Code als Client-Bibliotheken, wie im Abschnitt [Überblick](#overview) erklärt.
1. Konfigurieren Sie die CSS-Klassen, die Sie Ihren Inhaltsautoren zur Verfügung stellen möchten, wie im Abschnitt [Als Vorlagenautor](#as-a-template-author) beschrieben.
1. Inhaltsautoren können die Stile daraufhin wie im Abschnitt [Als Inhaltsautor](#as-a-content-author) beschrieben verwenden.

### Als Inhaltsautor   {#as-a-content-author}

1. Gehen Sie nach der Installation des WKND-Projekts zur englischsprachigen Master-Homepage von WKND unter `http://<host>:<port>/sites.html/content/wknd/language-masters/en` und bearbeiten Sie die Seite.
1. Wählen Sie weiter unten auf der Seite eine Komponente **Titel** aus

   ![Stilsystem für den Autor](/help/sites-cloud/authoring/assets/style-system-author1.png)

1. Tippen oder klicken Sie auf die Schaltfläche **Stile** in der Symbolleiste der Komponente **Liste**, um das Stilmenü zu öffnen und das Erscheinungsbild der Komponente zu bearbeiten.

   ![Auswählen von Stilen](/help/sites-cloud/authoring/assets/style-system-author2.png)

   >[!NOTE]
   >
   >In diesem Beispiel schließen sich die **Farbstile** (**Schwarz**, **Weiß** und **Grau**) gegenseitig aus, während die **Stiloptionen** (**Unterstrichen**, **Rechtsbündig ausrichten** und **Mini-Abstand**) kombiniert werden können. Dies kann [vom Vorlagenautor in der Vorlage konfiguriert werden](#as-a-template-author).

### Als Vorlagenautor     {#as-a-template-author}

1. Bei der Bearbeitung der englischsprachigen Master-Homepage von WKND unter `http://<host>:<port>/sites.html/content/wknd/language-masters/en` können Sie die Vorlage der Seite über **Seiteninformationen > Vorlage bearbeiten** anpassen.

   ![Vorlage bearbeiten](/help/sites-cloud/authoring/assets/style-system-edit-template.png)

1. Bearbeiten Sie die Richtlinien für die Komponente **Titel**, indem Sie auf die Schaltfläche **Richtlinie** der Komponente klicken.

   ![Richtlinie bearbeiten](/help/sites-cloud/authoring/assets/style-system-edit-policy.png)

1. Auf der Registerkarte „Stile“ in den Eigenschaften können Sie sehen, wie die Stile konfiguriert wurden.

   ![Eigenschaften bearbeiten](/help/sites-cloud/authoring/assets/style-system-properties.png)

   * **Gruppenname:** Stile können im Stilmenü gruppiert werden, das dem Inhaltsautor angezeigt wird, während er den Stil einer Komponente konfiguriert.
   * **Stile können kombiniert werden:** Legt fest, dass mehrere Stile innerhalb einer Gruppe gleichzeitig ausgewählt werden können.
   * **Stilname:** Die Beschreibung des Stils, der dem Inhaltsautor bei der Konfiguration des Stils der Komponente angezeigt wird.
   * **CSS-Klassen:** Der tatsächliche Name der dem Stil zugeordneten CSS-Klasse.
   Ordnen Sie die Gruppen und die Stile innerhalb der Gruppen mit den Ziehpunkten. Nutzen Sie die Symbole „Hinzufügen“ oder „Löschen“, um Gruppen bzw. Stile innerhalb der Gruppen hinzuzufügen oder zu entfernen.

>[!CAUTION]
>
>Die als Stil-Eigenschaften einer Komponentenrichtlinie konfigurierten CSS-Klassen (sowie der JavaScript-Code, soweit erforderlich) müssen als Client-Bibliotheken bereitgestellt werden, damit sie funktionieren.

<!--The CSS classes (as well as any necessary Javascript) configured as style properties of a component's policy must be deployed as [Client Libraries](/help/sites-developing/clientlibs.md) in order to work.-->

## Einrichtung {#setup}

Die Kernkomponenten ab Version 2 können die Vorteile des Stilsystems voll nutzen und erfordern keine zusätzliche Konfiguration.

Die folgenden Schritte sind nur erforderlich, um das Stilsystem für Ihre eigenen benutzerdefinierten Komponenten zu aktivieren oder um die [optionale Registerkarte „Stile“ im Dialogfeld „Bearbeiten“ zu aktivieren](#enable-styles-tab-edit).

### Aktivieren der Registerkarte „Stil“ im Dialogfeld „Design“ {#enable-styles-tab-design}

Damit eine Komponente mit dem AEM-Stilsystem funktioniert und die Stilregisterkarte im Designdialogfeld angezeigt wird, muss der Komponentenentwickler die Stilregisterkarte mit den folgenden Einstellungen für die Komponente einschließen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>Dabei werden [Überlagerungen](/help/implementing/developing/introduction/overlays.md)über den [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md)verwendet.

Ist die Komponente entsprechend konfiguriert, fügt AEM die von den Seitenautoren festgelegten Stile automatisch in den Decoration-Element-Wrapper ein, der automatisch auf alle bearbeitbaren Komponenten angewendet wird. Dafür ist keine weitere Aktion der Komponente erforderlich.

### Aktivieren der Registerkarte „Stile“ im Dialogfeld „Bearbeiten“ {#enable-styles-tab-edit}

Im Dialogfeld „Bearbeiten“ steht auch eine optionale Registerkarte „Stile“ zur Verfügung. Anders als bei der Registerkarte &quot;Designdialog&quot;ist die Registerkarte im Dialogfeld &quot;Bearbeiten&quot;nicht unbedingt erforderlich, damit das Stilsystem funktioniert. Es ist jedoch eine optionale alternative Schnittstelle, über die ein Inhaltsersteller Stile festlegen kann.

Die Registerkarte für das Bearbeitungsdialogfeld kann auf ähnliche Weise wie die Registerkarte für das Dialogfeld „Design“ eingebunden werden:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_edit/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>Dabei werden [Überlagerungen](/help/implementing/developing/introduction/overlays.md)über den [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md)verwendet.

>[!NOTE]
>
>Die Registerkarte „Stile“ im Dialogfeld „Bearbeiten“ ist standardmäßig nicht aktiviert.

### Stile mit Elementnamen     {#styles-with-element-names}

Mit der String-Array-Eigenschaft `cq:styleElements` können Entwickler auch eine Liste der zulässigen Elementnamen für Stile in der Komponente konfigurieren. In der Registerkarte „Stile“ für die Richtlinie im Dialogfeld „Design“ kann der Vorlagenautor außerdem Elementnamen auswählen, die für die einzelnen Stile festgelegt werden sollen. Dadurch wird der Elementname des Wrapper-Elements definiert.

Diese Eigenschaft wird auf dem Knoten `cq:Component` festgelegt. Beispiel:

* `/apps/<yoursite>/components/content/list@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Definieren Sie keine Elementnamen für Stile, die kombiniert werden können. Wenn mehrere Elementnamen definiert werden, gilt die folgende Prioritätsreihenfolge:
>
>1. HTL hat stets den Vorrang: `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Danach wird unter mehreren aktiven Stilen der erste Stil in der Liste der in der Komponentenrichtlinie konfigurierten Stile ausgewählt.
>1. Die Werte `cq:htmlTag`/ `cq:tagName` der Komponente werden schließlich als Ausweichwert verwendet.
>



Die Fähigkeit, Stilnamen zu definieren, ist bei sehr generischen Komponenten wie dem Layout-Container oder der Inhaltsfragmentkomponente hilfreich, um diesen eine zusätzliche Bedeutung zu verleihen.

Zum Beispiel können einem Layout-Container so Semantik-Elemente wie `<main>`, `<aside>`, `<nav>` usw. zugewiesen werden.
