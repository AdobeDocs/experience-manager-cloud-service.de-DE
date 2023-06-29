---
title: Entwickeln von SPAs für AEM
description: Dieser Artikel enthält wichtige Fragen, die zu beachten sind, wenn ein Frontend-Entwickler damit beauftragt wird, eine SPA für AEM zu entwickeln. Es gibt auch einen Überblick über die Architektur der AEM bezüglich SPA, die bei der Bereitstellung einer entwickelten SPA auf AEM zu beachten sind.
exl-id: f6c6f31a-69ad-48f6-b995-e6d0930074df
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2035'
ht-degree: 48%

---

# Entwickeln von SPAs für AEM {#developing-spas-for-aem}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten Sites mit SPA Frameworks erstellen können und Autoren möchten Inhalte in AEM für eine Site, die mit solchen Frameworks erstellt wurde, nahtlos bearbeiten.

Dieser Artikel enthält wichtige Fragen, die zu beachten sind, wenn ein Frontend-Entwickler damit beauftragt wird, eine SPA für AEM zu entwickeln, und gibt einen Überblick über die Architektur von AEM bezüglich der Bereitstellung von SPA auf AEM.

## SPA-Entwicklungsgrundsätze für AEM {#spa-development-principles-for-aem}

Bei der Entwicklung von Single Page Applications in AEM wird davon ausgegangen, dass sich der Frontend-Entwickler beim Erstellen einer SPA an die üblichen Best Practices hält. Wenn Sie als Frontend-Entwickler diese allgemeinen Best Practices und einige AEM-spezifische Prinzipien befolgen, kann Ihr SPA mit [AEM und die Inhaltsbearbeitungsfunktionen](introduction.md#content-editing-experience-with-spa).

* **[Portabilität](#portability)**: Wie alle anderen Komponenten auch sollten die Komponenten so portabel wie möglich gestaltet werden. Die SPA sollte aus portablen und wiederverwendbaren Komponenten bestehen.
* **[AEM verwaltet die Site-Struktur](#aem-drives-site-structure)** - Der Frontend-Entwickler erstellt Komponenten und ist für ihre interne Struktur verantwortlich, verlässt sich jedoch bei der Definition der Inhaltsstruktur der Site auf AEM.
* **[Dynamisches Rendering](#dynamic-rendering)**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **[Dynamisches Routing](#dynamic-routing)**: Die SPA ist für das Routing verantwortlich; AEM lauscht darauf und ruft Inhalte auf dieser Basis ab. Jegliches Routing sollte ebenfalls dynamisch sein.

Wenn Sie diese Prinzipien bei der Entwicklung Ihrer SPA beachten, wird diese so flexibel und zukunftssicher wie möglich gestaltet und gleichzeitig alle unterstützten AEM-Authoring-Funktionen aktiviert.

Wenn Sie AEM Authoring-Funktionen nicht unterstützen müssen, sollten Sie eine andere [SPA-Designmodell](#spa-design-models).

### Portabilität {#portability}

Wie bei der Entwicklung von Komponenten sollten Ihre Komponenten so gestaltet sein, dass sie maximale Portabilität aufweisen. Alle Muster, die der Portabilität oder Wiederverwendbarkeit der Komponenten zuwiderlaufen, sollten vermieden werden, um Kompatibilität, Flexibilität und Wartbarkeit in Zukunft zu garantieren.

Die resultierende SPA sollte mit hochgradig portablen und wiederverwendbaren Komponenten erstellt werden.

### AEM verwaltet die Site-Struktur {#aem-drives-site-structure}

Der Frontend-Entwickler muss sich selbst als verantwortlich für die Erstellung einer Bibliothek mit SPA Komponenten betrachten, die zum Erstellen der App verwendet werden. Der Frontend-Entwickler hat die volle Kontrolle über die interne Struktur der Komponenten. [Die Struktur der Site ist jedoch immer AEM](editor-overview.md).

Dieses Steuerelement bedeutet, dass der Frontend-Entwickler Kundeninhalte vor oder nach dem Einstiegspunkt der Komponenten hinzufügen und innerhalb der Komponente auch einen Drittanbieter-Aufruf durchführen kann. Der Frontend-Entwickler hat jedoch nicht die volle Kontrolle darüber, wie die Komponenten verschachtelt sind.

### Dynamisches Rendering {#dynamic-rendering}

Die SPA sollte sich nur auf dynamisches Rendering von Inhalten stützen. Diese Erwartung ist die Standardeinstellung, bei der AEM alle untergeordneten Elemente der Inhaltsstruktur abruft und rendert.

Jedes explizite Rendering, das auf bestimmte Inhalte verweist, gilt als statisches Rendering und wird zwar unterstützt, ist jedoch mit AEM Inhaltsbearbeitungsfunktionen kompatibel. Außerdem widerspricht es dem Grundsatz [Portabilität](#portability).

### Dynamisches Routing {#dynamic-routing}

Wie beim Rendering auch sollte das gesamte Routing dynamisch sein. In AEM sollte [die SPA stets für das Routing verantwortlich sein](routing.md); AEM lauscht darauf und ruft Inhalte auf dieser Basis ab.

Jedes statische Routing verstößt gegen den [Grundsatz der Portabilität](#portability) und schränkt den Autor ein, da es nicht mit den Inhaltserstellungsfunktionen von AEM kompatibel ist. Wenn beispielsweise der Inhaltsautor bei statischem Routing eine Route ändern oder eine Seite ändern möchte, muss er den Frontend-Entwickler bitten, dies zu tun.

## AEM-Projektarchetyp {#aem-project-archetype}

Jedes AEM Projekt sollte [AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de), SPA Projekte mit React oder Angular unterstützt und das SPA SDK verwendet.

## SPA-Design-Modelle {#spa-design-models}

Wenn die Variable [Grundsätze für die Entwicklung von SPA in AEM](#spa-development-principles-for-aem) folgen, wird Ihre SPA mit allen unterstützten AEM Inhaltsbearbeitungsfunktionen unterstützt.

Es kann jedoch vorkommen, dass diese Funktion nicht vollständig erforderlich ist. Die folgende Tabelle bietet einen Überblick über die verschiedenen Design-Modelle sowie ihre Vor- und Nachteile.

<table>
 <tbody>
  <tr>
   <th><strong>Design-Modell<br /> </strong></th>
   <th><strong>Vorteile</strong></th>
   <th><strong>Nachteile</strong></th>
  </tr>
  <tr>
   <td>AEM wird als Headless-CMS ohne das <a href="/help/implementing/developing/hybrid/reference-materials.md">SPA Editor SDK-Framework</a> verwendet.</td>
   <td>Der Frontend-Entwickler hat die volle Kontrolle über die App.</td>
   <td><p>Inhaltsautoren können AEM Inhaltserstellungserlebnis nicht verwenden.</p> <p>Der Code ist nicht portabel oder wiederverwendbar, wenn er statische Referenzen oder statisches Routing enthält.</p> <p>Die Verwendung des Vorlageneditors ist nicht zulässig, daher muss der Frontend-Entwickler bearbeitbare Vorlagen über JCR verwalten.</p> </td>
  </tr>
  <tr>
   <td>Der Frontend-Entwickler verwendet das SPA Editor SDK-Framework, öffnet jedoch nur einige Bereiche für den Inhaltsautor.</td>
   <td>Der Entwickler behält die Kontrolle über die App, indem er Authoring nur in eingeschränkten Bereichen der App aktiviert.</td>
   <td><p>Autoren von Inhalten sind auf eine begrenzte Anzahl von AEM-Inhaltserstellungsfunktionen beschränkt.</p> <p>Der Code kann nicht portabel oder wiederverwendbar sein, wenn er statische Referenzen oder statisches Routing enthält.</p> <p>Die Verwendung des Vorlageneditors ist nicht zulässig, daher muss der Frontend-Entwickler bearbeitbare Vorlagen über JCR verwalten.</p> </td>
  </tr>
  <tr>
   <td>Das Projekt verwendet vollständig das SPA Editor SDK und die Frontend-Komponenten werden als Bibliothek entwickelt und die Inhaltsstruktur der App wird an AEM delegiert.</td>
   <td><p>Die App ist wiederverwendbar und portabel.</p> <p>Der Inhaltsautor kann die App mit den Inhaltserstellungsfunktionen von AEM bearbeiten.<br /> </p> <p>Die SPA ist mit dem Vorlageneditor kompatibel.</p> </td>
   <td><p>Der Entwickler hat keine Kontrolle über die Struktur der App und den Teil des Inhalts, der an AEM delegiert wurde.</p> <p>Der Entwickler kann aber Bereiche der App für Inhalte reservieren, die nicht mit AEM erstellt werden sollen.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Zwar werden alle Modelle in AEM unterstützt, jedoch nur durch Implementierung des dritten Modells (und Befolgen der empfohlenen [SPA Entwicklungsgrundsätze](#spa-development-principles-for-aem)) sind die Inhaltsautoren, die mit dem Inhalt der SPA in AEM interagieren und ihn bearbeiten können.

## Migrieren vorhandener SPAs zu AEM {#migrating-existing-spas-to-aem}

Im Allgemeinen, wenn Ihre SPA dem [SPA Entwicklungsgrundsätze für AEM](#spa-development-principles-for-aem), funktioniert Ihr SPA in AEM und kann mit dem AEM SPA Editor bearbeitet werden.

Führen Sie diese Schritte aus, damit Sie Ihre vorhandene SPA für die Arbeit mit AEM bereit machen können.

1. **Gestalten Sie Ihre JS-Komponenten modular.** - Gestalten Sie sie so, dass sie in beliebiger Reihenfolge, Position und Größe gerendert werden können.
1. **Verwenden Sie die vom SDK bereitgestellten Container, um Ihre Komponenten auf dem Bildschirm zu platzieren.** – AEM bietet eine Seiten- und Absatzsystemkomponente, die Sie verwenden können.
1. **Erstellen Sie für jede JS-Komponente eine AEM-Komponente.** - Die AEM Komponenten definieren das Dialogfeld und die JSON-Ausgabe.

## Anweisungen für Frontend-Entwickler {#instructions-for-front-end-developers}

Wenn ein Frontend-Entwickler damit beauftragt wird, eine SPA für AEM zu erstellen, besteht die wichtigste Aufgabe darin, sich auf die Komponenten und ihre JSON-Modelle zu einigen.

Im Folgenden werden die Schritte beschrieben, die ein Frontend-Entwickler ausführen muss, wenn er eine SPA für AEM entwickelt.

1. **Einigen Sie sich hinsichtlich der Komponenten und ihrer JSON-Modelle**

   Frontend-Entwickler und Back-End-AEM-Entwickler müssen sich darauf einigen, welche Komponenten erforderlich sind, und ein Modell erstellen, damit eine Eins-zu-Eins-Übereinstimmung zwischen SPA Komponenten und den Backend-Komponenten besteht.

   AEM-Komponenten sind weiterhin erforderlich, insbesondere um Bearbeitungsdialogfelder bereitzustellen und das Komponentenmodell zu exportieren.

1. **In React-Komponenten greifen Sie auf das Modell zu über`this.props.cqModel`**

   Sobald Komponenten vereinbart sind und das JSON-Modell vorhanden ist, kann der Frontend-Entwickler die SPA entwickeln und über `this.props.cqModel` bequem auf das JSON-Modell zugreifen.

1. **Implementieren der `render()` method**

   Der Frontend-Entwickler implementiert die `render()`-Methode nach Belieben und kann die Felder der `cqModel`-Eigenschaft verwenden. Diese Methode gibt die DOM- und HTML-Fragmente aus, die in die Seite eingefügt werden. Diese Methode ist auch die Standardmethode zum Erstellen einer App in React.

1. **Ordnen Sie die Komponente dem AEM-Ressourcentyp zu via`MapTo()`**

   Die Zuordnung speichert Komponentenklassen und wird von der bereitgestellten `Container`-Komponente intern zum Abrufen und dynamischen Instanziieren von Komponenten basierend auf dem angegebenen Ressourcentyp genutzt.

   Diese Karte dient als &quot;Kleber&quot;zwischen Frontend und Backend, sodass der Editor weiß, welchen Komponenten die React-Komponenten entsprechen.

   `Page` und `ResponsiveGrid` sind gute Beispiele für Klassen, die den grundlegenden `Container` erweitern.

1. **Definieren Sie die `EditConfig` als Parameter zu`MapTo()`**

   Dieser Parameter teilt dem Editor mit, wie die Komponente benannt werden soll, solange sie noch nicht gerendert ist oder über keinen zu rendernden Inhalt verfügt.

1. **Erweitern Sie die bereitgestellte `Container`-Klasse für Seiten und Container**

   Seiten und Absatzsysteme sollten diese Klasse erweitern, damit die Übertragung an innere Komponenten erwartungsgemäß funktioniert.

1. **Implementieren Sie eine Routing-Lösung, die die HTML5-`History`-API verwendet.**

   Wenn die `ModelRouter` aktiviert ist, wird die `pushState` und `replaceState` Funktionen Trigger einer Anforderung an die `PageModelManager` , um ein fehlendes Fragment des Modells abzurufen.

   Die aktuelle Version von `ModelRouter` unterstützt nur die Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad der Einstiegspunkte des Sling-Modells verweisen. Die Verwendung von Vanity-URLs oder Aliasen wird nicht unterstützt.

   Der `ModelRouter` kann deaktiviert oder so konfiguriert werden, dass eine Liste von regulären Ausdrücken ignoriert wird.

## AEM-Agnostik {#aem-agnostic}

Diese Code-Blöcke veranschaulichen, dass Ihre React- und Angular-Komponenten nichts Spezifisches für Adobe oder AEM benötigen.

* Alles, was sich in der JavaScript-Komponente befindet, ist AEM-agnostisch.
* Was jedoch AEM ist, ist, dass die JS-Komponente mit dem MapTo-Helfer einer AEM Komponente zugeordnet werden muss.

![AEM-agnostischer Ansatz](assets/aem-agnostic.png)

Das `MapTo`-Hilfsprogramm ist die Verbindung, die eine Abstimmung zwischen Backend- und Frontend-Komponenten ermöglicht:

* Es teilt dem JS-Container (oder dem JS-Absatzsystem) mit, welche JS-Komponente für das Rendern der einzelnen Komponenten, die in der JSON vorhanden sind, verantwortlich ist.
* Es wird ein HTML-Datenattribut zum HTML-Code hinzugefügt, das die JS-Komponente rendert, damit der SPA-Editor weiß, welches Dialogfeld dem Autor beim Bearbeiten der Komponente angezeigt werden soll.

Weitere Informationen zum Verwenden von `MapTo` und Erstellen von SPAs für AEM im Allgemeinen finden Sie im Handbuch „Erste Schritte“ für Ihr ausgewähltes Framework.

* [Erste Schritte mit SPAs in AEM unter Verwendung von React](getting-started-react.md)
* [Erste Schritte mit SPAs in AEM unter Verwendung von Angular](getting-started-angular.md)

## AEM-Architektur und SPAs {#aem-architecture-and-spas}

Die allgemeine Architektur von AEM einschließlich Umgebungen für Entwicklung, Authoring und Veröffentlichung ändert sich bei Verwendung von SPAs nicht. Es ist jedoch hilfreich zu verstehen, wie die SPA-Entwicklung mit dieser Architektur verbunden ist.

![AEM-Architektur und SPAs](assets/aem-architecture.png)

* **Build-Umgebung**

  In dieser Umgebung wird die Quelle für die SPA Anwendung und die Komponentenquelle ausgecheckt.

   * Der NPM-clientlib-Generator erstellt aus dem SPA-Projekt eine Client-Bibliothek.
   * Diese Bibliothek wird von Maven übernommen und vom Maven Build-Plug-in zusammen mit der Komponente für die AEM-Autoreninstanz bereitgestellt.

* **AEM Author**

  Inhalte werden im AEM Author erstellt, einschließlich der Authoring-SPAs.

  Wenn eine SPA in der Authoring-Umgebung mit dem SPA-Editor bearbeitet wird:

   1. Die SPA fordert den äußeren HTML-Code an.
   1. Das CSS wird geladen.
   1. Das JavaScript der SPA wird geladen.
   1. Sobald die SPA-Anwendung ausgeführt wird, wird die JSON angefordert, damit die App das DOM der Seite einschließlich der `cq-data`-Attribute erstellen kann.
   1. Die `cq-data` -Attribute ermöglichen es dem Editor, zusätzliche Seiteninformationen zu laden, damit er weiß, welche Bearbeitungskonfigurationen für die Komponenten verfügbar sind.

* **AEM Publish**

  Wo die erstellten Inhalte und kompilierten Bibliotheken einschließlich SPA Anwendungsartefakten, Client-Bibliotheken und Komponenten für die öffentliche Nutzung veröffentlicht werden.

* **Dispatcher/CDN**

  Der Dispatcher dient als Zwischenspeicherebene von AEM für Besucher der Site.
   * Anforderungen werden ähnlich wie in der AEM-Autoreninstanz verarbeitet. Die Seiteninformationen werden jedoch nicht angefordert, da sie nur vom Editor benötigt werden.
   * JavaScript, CSS, JSON und HTML werden zwischengespeichert, wodurch die Seite für eine schnelle Bereitstellung optimiert wird.

>[!NOTE]
>
>Innerhalb AEM gibt es keine Notwendigkeit, JavaScript-Build-Mechanismen auszuführen oder das JavaScript selbst auszuführen. AEM hostet lediglich die kompilierten Artefakte aus der SPA-Anwendung.

## Nächste Schritte {#next-steps}

* [Erste Schritte mit SPAs in AEM unter Verwendung von React](getting-started-react.md) zeigt, wie unter Verwendung von React eine einfache SPA für die Zusammenarbeit mit dem SPA-Editor in AEM erstellt wird.
* [Erste Schritte mit SPAs in AEM unter Verwendung von Angular](getting-started-angular.md) zeigt, wie unter Verwendung von Angular eine einfache SPA für die Zusammenarbeit mit dem SPA-Editor in AEM erstellt wird.
* [SPA-Editor – Überblick](editor-overview.md) vertieft das Kommunikationsmodell zwischen AEM und der SPA.
* [WKND-SPA-Projekt](wknd-tutorial.md) ist ein Schritt-für-Schritt-Tutorial zur Implementierung eines einfachen SPA-Projekts in AEM.
* [Dynamisches Modell zur Komponentenzuordnung für SPAs](model-to-component-mapping.md) erläutert das dynamische Modell für die Komponentenzuordnung und dessen Funktionsweise innerhalb von SPAs in AEM.
* [SPA Blueprint](blueprint.md) bietet einen tiefen Einblick in die Funktionsweise des SPA SDK für AEM, falls Sie SPA in AEM für ein anderes Framework als React oder Angular implementieren möchten. Oder Sie möchten einfach ein tieferes Verständnis.
