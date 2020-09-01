---
title: Entwicklung von SPAs für AEM
description: Dieser Artikel enthält wichtige Fragen, die zu berücksichtigen sind, wenn ein Front-End-Entwickler aufgefordert wird, ein SPA für AEM zu entwickeln, sowie einen Überblick über die Architektur von AEM in Bezug auf SPAs, die bei der Bereitstellung eines entwickelten SPA auf AEM zu beachten sind.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '2078'
ht-degree: 2%

---


# Entwicklung von SPAs für AEM {#developing-spas-for-aem}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten Sites mit SPA-Frameworks erstellen und Autoren möchten Inhalte in AEM nahtlos für eine Site bearbeiten, die mit diesen Frameworks erstellt wurde.

Dieser Artikel enthält wichtige Fragen, die zu berücksichtigen sind, wenn ein Front-End-Entwickler aufgefordert wird, ein SPA für AEM zu entwickeln, und gibt einen Überblick über die Architektur von AEM im Hinblick auf die Bereitstellung von SPAs auf AEM.

## SPA-Entwicklungsgrundsätze für AEM {#spa-development-principles-for-aem}

Beim Entwickeln von Einzelseitenanwendungen auf AEM wird davon ausgegangen, dass der Front-End-Entwickler beim Erstellen einer SPA die üblichen Best Practices beachtet. Wenn Sie als Front-End-Entwickler diese allgemeinen Best Practices sowie nur wenige AEM-spezifische Prinzipien befolgen, ist Ihr SPA mit [AEM und seinen Funktionen](introduction.md#content-editing-experience-with-spa)zur Inhaltserstellung funktionsfähig.

* **[Portabilität](#portability)** - Wie bei allen Komponenten sollten die Komponenten so gebaut sein, dass sie möglichst tragbar sind. Die SPA sollte mit tragbaren und wiederverwendbaren Komponenten erstellt werden.
* **[AEM treibt die Site-Struktur](#aem-drives-site-structure)** vorn - Der Front-End-Entwickler erstellt Komponenten und besitzt deren interne Struktur, setzt aber bei der Definition der Inhaltsstruktur der Site auf AEM.
* **[Dynamisches Rendering](#dynamic-rendering)** : Alle Rendering-Vorgänge sollten dynamisch sein.
* **[Dynamisches Routing](#dynamic-routing)** - Die SPA ist für das Routing verantwortlich und AEM darauf zuhört und ruft es ab. Jedes Routing sollte ebenfalls dynamisch sein.

Wenn Sie diese Prinzipien bei der Entwicklung Ihrer SPA beachten, wird diese so flexibel und so schnell wie möglich sein und gleichzeitig alle unterstützten AEM-Authoring-Funktionen ermöglichen.

Wenn Sie AEM Authoring-Funktionen nicht unterstützen müssen, müssen Sie möglicherweise ein anderes [SPA-Designmodell](#spa-design-models)in Betracht ziehen.

### Portabilität {#portability}

Wie bei der Entwicklung von Komponenten sollten Ihre Komponenten so gestaltet sein, dass ihre Portabilität maximiert wird. Alle Muster, die gegen die Übertragbarkeit oder Wiederverwendbarkeit der Komponenten funktionieren, sollten vermieden werden, um Kompatibilität, Flexibilität und Wartbarkeit in Zukunft sicherzustellen.

Die resultierende SPA sollte mit hochtragbaren und wiederverwendbaren Komponenten gebaut werden.

### AEM treibt die Site-Struktur {#aem-drives-site-structure}

Der Front-End-Entwickler muss sich selbst als verantwortlich für die Erstellung einer Bibliothek mit SPA-Komponenten betrachten, die zum Erstellen der App verwendet werden. Der Front-End-Entwickler hat die vollständige Kontrolle über die interne Struktur der Komponenten. [AEM besitzt jedoch jederzeit die Struktur der Site.](editor-overview.md)

Das bedeutet, dass der Front-End-Entwickler Kundeninhalte vor oder nach dem Einstiegspunkt der Komponenten hinzufügen und auch Drittanbieter-Aufrufe innerhalb der Komponente durchführen kann. Der Front-End-Entwickler hat jedoch nicht die volle Kontrolle darüber, wie die Komponenten verschachteln.

### Dynamisches Rendering {#dynamic-rendering}

Die SPA sollte nur auf der dynamischen Wiedergabe von Inhalten basieren. Dies ist die Standarderwartungen, bei denen AEM alle untergeordneten Elemente der Inhaltsstruktur abruft und rendert.

Jedes explizite Rendering, das auf bestimmte Inhalte verweist, gilt als statisches Rendering und wird zwar unterstützt, ist jedoch nicht mit AEM Inhaltserstellungsfunktionen kompatibel. Dies widerspricht auch dem Grundsatz der [Übertragbarkeit](#portability).

### Dynamisches Routing {#dynamic-routing}

Wie beim Rendering sollte auch das gesamte Routing dynamisch sein. In AEM sollte [die SPA stets Eigentümer des Routings](routing.md) sein und AEM darauf hören und Inhalte abrufen, die darauf basieren.

Jedes statische Routing verstößt gegen das [Prinzip der Portabilität](#portability) und schränkt den Autor ein, indem es nicht mit Inhaltserstellungsfunktionen von AEM kompatibel ist. Bei statischem Routing muss der Autor beispielsweise den Front-End-Entwickler bitten, eine Route zu ändern oder eine Seite zu ändern.

## AEM-Projektarchetyp {#aem-project-archetype}

Jedes AEM Projekt sollte den [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)nutzen, der SPA-Projekte mit React oder Angular unterstützt und das SPA-SDK nutzt.

## SPA-Designmodelle {#spa-design-models}

Wenn die [Prinzipien der Entwicklung von SPAs in AEM](#spa-development-principles-for-aem) befolgt werden, funktioniert Ihre SPA mit allen unterstützten AEM Inhaltserstellungsfunktionen.

Es kann jedoch Fälle geben, in denen dies nicht ganz notwendig ist. Die folgende Tabelle gibt einen Überblick über die verschiedenen Designmodelle, ihre Vor- und Nachteile.

<table>
 <tbody>
  <tr>
   <th><strong>Designmodell<br /> </strong></th>
   <th><strong>Vorteile</strong></th>
   <th><strong>Nachteile</strong></th>
  </tr>
  <tr>
   <td>AEM wird als kopfloses CMS ohne Verwendung des <a href="/help/implementing/developing/spa/reference-materials.md">SPA Editor SDK Frameworks verwendet.</a></td>
   <td>Der Frontend-Entwickler hat die vollständige Kontrolle über die App.</td>
   <td><p>Inhaltsersteller können AEM Inhaltserstellungserfahrung nicht nutzen.</p> <p>Der Code ist weder portabel noch wiederverwendbar, wenn er statische Referenzen oder Routing enthält.</p> <p>Die Verwendung des Vorlageneditors ist nicht zulässig. Daher muss der Front-End-Entwickler bearbeitbare Vorlagen über JCR verwalten.</p> </td>
  </tr>
  <tr>
   <td>Der Front-End-Entwickler verwendet das SPA Editor SDK Framework, öffnet jedoch nur einige Bereiche für den Inhaltsersteller.</td>
   <td>Der Entwickler behält die Kontrolle über die App, indem er nur das Authoring in eingeschränkten Bereichen der App aktiviert.</td>
   <td><p>Autoren von Inhalten sind auf eine begrenzte Anzahl von AEM Inhaltserstellungsprogrammen beschränkt.</p> <p>Der Code kann weder portabel noch wiederverwendbar sein, wenn er statische Referenzen oder Routing enthält.</p> <p>Die Verwendung des Vorlageneditors ist nicht zulässig. Daher muss der Front-End-Entwickler bearbeitbare Vorlagen über JCR verwalten.</p> </td>
  </tr>
  <tr>
   <td>Das Projekt nutzt das SPA Editor SDK vollständig, und die Frontend-Komponenten werden als Bibliothek entwickelt und die Inhaltsstruktur der App wird an AEM übertragen.</td>
   <td><p>Die App ist wiederverwendbar und portabel.</p> <p>Der Autor des Inhalts kann die App mit AEM Inhaltserstellung bearbeiten.<br /> </p> <p>Die SPA ist mit dem Vorlageneditor kompatibel.</p> </td>
   <td><p>Der Entwickler hat keine Kontrolle über die Struktur der App und den Teil des Inhalts, der an AEM delegiert wird.</p> <p>Der Entwickler kann weiterhin Bereiche der App für Inhalte reservieren, die nicht mit AEM erstellt werden sollen.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Obwohl alle Modelle in AEM unterstützt werden, können die Inhaltsersteller nur durch die Implementierung des dritten (und damit gemäß den empfohlenen [SPA-Entwicklungsprinzipien in AEM](#spa-development-principles-for-aem)) mit dem Inhalt des SPA interagieren und ihn in AEM gewohnten Form bearbeiten.

## Migrieren vorhandener SPAs zu AEM {#migrating-existing-spas-to-aem}

Wenn Ihr SPA die [SPA-Entwicklungsprinzipien für AEM](#spa-development-principles-for-aem)befolgt, funktioniert Ihr SPA in AEM und kann mit dem AEM SPA Editor bearbeitet werden.

Führen Sie die folgenden Schritte aus, um Ihre bestehende Einzelseitenanwendung für die Arbeit mit AEM bereitzustellen.

1. **Machen Sie Ihre JS-Komponenten modular.** - Machen Sie sie in beliebiger Reihenfolge, Position und Größe gerendert.
1. **Verwenden Sie die von unserem SDK bereitgestellten Container, um Ihre Komponenten auf dem Bildschirm zu platzieren.** - AEM bietet eine Seite und eine Absatz-Systemkomponente, die Sie verwenden können.
1. **Erstellen Sie für jede JS-Komponente eine AEM.** - Die AEM Komponenten definieren den Dialog und die JSON-Ausgabe.

## Anweisungen für Front-End-Entwickler {#instructions-for-front-end-developers}

Die wichtigste Aufgabe, einen Frontend-Entwickler dazu zu bewegen, eine SPA für AEM zu erstellen, besteht darin, sich auf die Komponenten und ihre JSON-Modelle zu einigen.

Im Folgenden werden die Schritte erläutert, die ein Front-End-Entwickler bei der Entwicklung einer SPA für AEM ausführen muss.

1. **Einigung über Komponenten und ihr JSON-Modell**

   Front-End-Entwickler und Back-End-AEM-Entwickler müssen sich darauf einigen, welche Komponenten erforderlich sind, und ein Modell erstellen, damit eine Eins-zu-Eins-Übereinstimmung von SPA-Komponenten zu den Back-End-Komponenten besteht.

   AEM Komponenten sind immer noch erforderlich, um Bearbeitungsdialogfelder bereitzustellen und das Komponentenmodell zu exportieren.

1. **In React-Komponenten greifen Sie über`this.props.cqModel`**

   Sobald Komponenten vereinbart und das JSON-Modell installiert ist, kann der Front-End-Entwickler die SPA entwickeln und einfach über `this.props.cqModel`das JSON-Modell zugreifen.

1. **Implementieren der`render()`Methode der Komponente**

   Der Front-End-Entwickler implementiert die `render()` Methode nach Belieben und kann die Felder der `cqModel` Eigenschaft verwenden. Dadurch werden das DOM und die HTML-Fragmente ausgegeben, die in die Seite eingefügt werden. Dies ist die Standardmethode zum Erstellen einer App in React.

1. **Ordnen Sie die Komponente dem AEM Ressourcentyp zu`MapTo()`**

   Die Zuordnung speichert Komponentenklassen und wird intern von der bereitgestellten `Container` Komponente zum Abrufen und dynamischen Instanziieren von Komponenten basierend auf dem angegebenen Ressourcentyp verwendet.

   Dies dient als &quot;Kleber&quot;zwischen Front- und Back-End, sodass Editor weiß, zu welchen Komponenten die Reaktionskomponenten passen.

   Die `Page` und `ResponsiveGrid` sind gute Beispiele für Klassen, die die Basis erweitern `Container`.

1. **Definieren Sie den`EditConfig`Parameter der Komponente als`MapTo()`**

   Dieser Parameter ist erforderlich, um dem Editor mitzuteilen, wie die Komponente benannt werden soll, solange at noch nicht gerendert ist oder über keinen zu rendernden Inhalt verfügt.

1. **Erweitern der bereitgestellten`Container`Klasse für Seiten und Container**

   Seiten und Absatzsysteme sollten diese Klasse erweitern, damit die Übertragung auf innere Komponenten erwartungsgemäß funktioniert.

1. **Implementieren Sie eine Routing-Lösung, die die HTML5`History`-API verwendet.**

   Wenn die Funktion `ModelRouter` aktiviert ist, löst der Aufruf der Funktionen `pushState` und `replaceState` eine Anforderung aus, ein fehlendes Fragment des Modells abzurufen `PageModelManager` .

   Die aktuelle Version der `ModelRouter` einzigen Version unterstützt die Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad von Sling Model-Einstiegspunkten zeigen. Die Verwendung von Vanity-URLs oder Aliasnamen wird nicht unterstützt.

   Das `ModelRouter` kann deaktiviert oder so konfiguriert werden, dass eine Liste von regulären Ausdrücken ignoriert wird.

## AEM-Agnostik {#aem-agnostic}

Diese Codeblöcke veranschaulichen, wie Ihre React- und Angular-Komponenten nichts Spezifisches für Adobe oder AEM benötigen.

* Alles, was sich in der JavaScript-Komponente befindet, ist AEM-agnostisch.
* Was jedoch spezifisch AEM ist, ist, dass die JS-Komponente mit dem MapTo-Helfer einer AEM Komponente zugeordnet werden muss.

![AEM Agnostischen Ansatz](assets/aem-agnostic.png)

Der `MapTo` Helfer ist der &quot;Kleber&quot;, der eine Übereinstimmung zwischen Back-End- und Front-End-Komponenten ermöglicht:

* Er teilt dem JS-Container (oder dem JS-Absatzsystem) mit, welche JS-Komponente für die Wiedergabe der einzelnen Komponenten, die im JSON vorhanden sind, verantwortlich ist.
* Es wird ein HTML-Datenattribut zu dem HTML-Code hinzugefügt, den die JS-Komponente wiedergibt, damit der SPA-Editor weiß, welches Dialogfeld dem Autor beim Bearbeiten der Komponente angezeigt werden soll.

Weitere Informationen zum Verwenden `MapTo` und Erstellen von SPAs für AEM im Allgemeinen finden Sie im Handbuch &quot;Erste Schritte&quot;für Ihr ausgewähltes Framework.

* [Erste Schritte mit SPAs in AEM mithilfe von React](getting-started-react.md)
* [Erste Schritte mit SPAs in AEM Verwenden von Angular](getting-started-angular.md)

## AEM Architektur und besondere Schutzgebiete {#aem-architecture-and-spas}

Die allgemeine Architektur von AEM einschließlich Umgebung für Entwicklung, Authoring und Veröffentlichung ändert sich nicht, wenn SPAs verwendet werden. Es ist jedoch hilfreich zu verstehen, wie die SPA-Entwicklung in diese Architektur passt.

![AEM und besondere Schutzgebiete](assets/aem-architecture.png)

* **Umgebung erstellen**

   Hier werden die Quelle für die SPA-Anwendungsquelle und die Komponentenquelle ausgecheckt.

   * Der NPM clientlib Generator erstellt eine Client-Bibliothek aus dem SPA-Projekt.
   * Diese Bibliothek wird von Maven entnommen und vom Maven Build-Plugin zusammen mit der Komponente für den AEM Author bereitgestellt.

* **AEM Author**

   Inhalte werden auf dem AEM Autor erstellt, einschließlich der Authoring-SPAs.

   Wenn eine SPA mit dem SPA-Editor auf der Authoring-Umgebung bearbeitet wird:

   1. Die SPA fordert den äußeren HTML-Code an.
   1. Das CSS wird geladen.
   1. Das Javascript der SPA-Anwendung wird geladen.
   1. Wenn die SPA-Anwendung ausgeführt wird, wird die JSON angefordert, sodass die App das DOM der Seite einschließlich der `cq-data` Attribute erstellen kann.
   1. Diese `cq-data` Attribute ermöglichen es dem Editor, zusätzliche Seiteninformationen zu laden, damit er weiß, welche Bearbeitungskonfigurationen für die Komponenten verfügbar sind.

* **AEM Publish**

   Hier werden die erstellten Inhalte und kompilierten Bibliotheken einschließlich SPA-Anwendungsartefakten, clientlibs und Komponenten für den öffentlichen Gebrauch veröffentlicht.

* **Dispatcher/CDN**

   Der Dispatcher dient als Zwischenspeicherebene AEM für Besucher der Site.
   * Anforderungen werden ähnlich wie im AEM-Autor verarbeitet, es gibt jedoch keine Anforderung der Seiteninformationen, da dies nur vom Editor benötigt wird.
   * JavaScript, CSS, JSON und HTML werden zwischengespeichert, wodurch die Seite für einen schnellen Versand optimiert wird.

>[!NOTE]
>
>Innerhalb AEM gibt es keine Notwendigkeit, Javascript-Buildmechanismen auszuführen oder das Javascript selbst auszuführen. AEM hostet nur die kompilierten Artefakte aus der SPA-Anwendung.

## Nächste Schritte {#next-steps}

* [Die ersten Schritte mit SPAs in AEM mithilfe von React](getting-started-react.md) zeigen, wie ein grundlegendes SPA für die Arbeit mit dem SPA-Editor in AEM mithilfe von React erstellt wurde.
* [Erste Schritte mit SPAs in AEM Verwendung von Angular](getting-started-angular.md) zeigen, wie ein grundlegendes SPA für die Arbeit mit dem SPA-Editor in AEM Verwendung von Angular erstellt wurde.
* [Der SPA Editor-Überblick](editor-overview.md) vertieft das Kommunikationsmodell zwischen AEM und SPA.
* [WKND SPA Project](wknd-tutorial.md) ist ein Schritt-für-Schritt-Tutorial zur Implementierung eines einfachen SPA-Projekts in AEM.
* [Die Zuordnung dynamischer Modelle zu Komponenten für SPAs](model-to-component-mapping.md) erläutert das dynamische Modell zur Komponentenzuordnung und seine Funktionsweise in SPAs in AEM.
* [SPA Blueprint](blueprint.md) Angebots bietet einen tiefen Einblick in die Funktionsweise des SPA SDK for AEM, falls Sie SPAs in AEM für ein anderes Framework als React oder Angular implementieren möchten oder einfach ein tieferes Verständnis wünschen.
