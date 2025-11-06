---
title: Entwickeln von SPAs für AEM
description: Dieser Artikel enthält wichtige Fragen, die zu beachten sind, wenn Frontend-Entwicklerinnen bzw. -Entwickler damit beauftragt werden, eine SPA für AEM zu entwickeln. Er gibt auch einen Überblick über die Architektur der AEM bezüglich SPAs, die bei der Bereitstellung einer entwickelten SPA auf AEM zu beachten sind.
exl-id: f6c6f31a-69ad-48f6-b995-e6d0930074df
feature: Developing
role: Admin, Developer
index: false
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2028'
ht-degree: 100%

---


# Entwickeln von SPAs für AEM {#developing-spas-for-aem}

Single Page Applications (SPAs) können Nutzerinnen und Nutzern von Websites ein überzeugendes Erlebnis bieten. Entwicklungspersonen möchten Sites mit SPA-Frameworks erstellen und Autorinnen bzw. Autoren möchten Inhalte in AEM nahtlos für eine Site bearbeiten, die mit diesen Frameworks erstellt wurde.

Dieser Artikel stellt wichtige Fragen vor, die bei der Beauftragung von Frontend-Entwicklungspersonen mit der Entwicklung einer SPA für AEM zu beachten sind, und gibt einen Überblick über die Architektur von AEM im Hinblick auf die Bereitstellung von SPAs auf AEM.

{{ue-over-spa}}

## SPA-Entwicklungsgrundsätze für AEM {#spa-development-principles-for-aem}

Bei der Entwicklung von Single Page Applications in AEM wird davon ausgegangen, dass sich die Frontend-Entwicklungspersonen beim Erstellen einer SPA an die üblichen Best Practices halten. Wenn Sie als Frontend-Entwicklerin bzw. -Entwickler diese allgemeinen Best Practices sowie einige AEM-spezifische Prinzipien befolgen, wird Ihre SPA mit [AEM und seinen Inhaltsverfassungsfunktionen](introduction.md#content-editing-experience-with-spa) zusammenarbeiten.

* **[Portabilität](#portability)**: Wie alle anderen Komponenten auch sollten die Komponenten so portabel wie möglich gestaltet werden. Die SPA sollte aus portablen und wiederverwendbaren Komponenten bestehen.
* **[AEM verwaltet die Site-Struktur](#aem-drives-site-structure)**: Die Frontend-Entwicklungsperson erstellt Komponenten und ist für deren interne Struktur verantwortlich, verlässt sich für die Definition der Inhaltsstruktur der Site jedoch auf AEM.
* **[Dynamisches Rendering](#dynamic-rendering)**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **[Dynamisches Routing](#dynamic-routing)**: Die SPA ist für das Routing verantwortlich; AEM lauscht darauf und ruft Inhalte auf dieser Basis ab. Jegliches Routing sollte ebenfalls dynamisch sein.

Wenn Sie sich bei der Entwicklung Ihrer SPA an diese Grundsätze halten, wird diese so flexibel und zukunftssicher wie möglich sein sowie die Nutzung aller unterstützten AEM-Authoring-Funktionen ermöglichen.

Wenn Sie keine Unterstützung für AEM-Authoring-Funktionen benötigen, sollten Sie ein anderes [SPA-Design-Modell](#spa-design-models) in Betracht ziehen.

### Portabilität {#portability}

Wie bei der Entwicklung von Komponenten sollten Ihre Komponenten so gestaltet sein, dass sie maximale Portabilität aufweisen. Alle Muster, die der Portabilität oder Wiederverwendbarkeit der Komponenten zuwiderlaufen, sollten vermieden werden, um Kompatibilität, Flexibilität und Wartbarkeit in Zukunft zu garantieren.

Die resultierende SPA sollte mit hochgradig portablen und wiederverwendbaren Komponenten erstellt werden.

### AEM verwaltet die Site-Struktur {#aem-drives-site-structure}

Die Frontend-Entwicklungsperson muss sich als verantwortlich für die Einrichtung einer Bibliothek mit SPA-Komponenten betrachten, die zum Erstellen der App verwendet werden. Die Frontend-Entwicklungsperson hat die vollständige Kontrolle über die interne Struktur der Komponenten. [Die Struktur der Site gehört jedoch immer AEM](editor-overview.md).

Diese Kontrolle bedeutet, dass die Frontend-Entwicklungsperson Kundeninhalte vor oder nach dem Einstiegspunkt der Komponenten hinzufügen und innerhalb der Komponente auch Drittanbieter-Aufrufe durchführen kann. Die Frontend-Entwicklungsperson hat jedoch zum Beispiel nicht die volle Kontrolle darüber, wie Komponenten verschachtelt werden.

### Dynamisches Rendering {#dynamic-rendering}

Die SPA sollte sich nur auf dynamisches Rendering von Inhalten stützen. Diese Erwartung ist der Standard, bei dem AEM alle untergeordneten Elemente der Inhaltsstruktur abruft und rendert.

Jedes explizite Rendering, das auf bestimmte Inhalte verweist, gilt als statisches Rendering und wird zwar unterstützt, ist jedoch nicht mit den Inhaltserstellungsfunktionen von AEM kompatibel. Es widerspricht auch dem Grundsatz der [Portabilität](#portability).

### Dynamisches Routing {#dynamic-routing}

Wie beim Rendering auch sollte das gesamte Routing dynamisch sein. In AEM sollte [die SPA stets für das Routing verantwortlich sein](routing.md); AEM lauscht darauf und ruft Inhalte auf dieser Basis ab.

Jedes statische Routing verstößt gegen den [Grundsatz der Portabilität](#portability) und schränkt den Autor ein, da es nicht mit den Inhaltserstellungsfunktionen von AEM kompatibel ist. Wenn beispielsweise Inhaltsautorinnen oder -autoren bei statischem Routing eine Route ändern oder eine Seite ändern möchten, müssen sie die Frontend-Entwicklungsperson bitten, dies zu tun.

## AEM-Projektarchetyp {#aem-project-archetype}

Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA-SDK verwendet.

## SPA-Design-Modelle {#spa-design-models}

Wenn die [Prinzipien der Entwicklung von SPAs in AEM](#spa-development-principles-for-aem) befolgt werden, wird Ihre SPA mit allen unterstützten Inhaltserstellungsfunktionen von AEM zusammenarbeiten.

Es kann jedoch Fälle geben, in denen diese Funktionalität nicht unbedingt erforderlich ist. Die folgende Tabelle bietet einen Überblick über die verschiedenen Design-Modelle sowie ihre Vor- und Nachteile.

<table>
 <tbody>
  <tr>
   <th><strong>Design-Modell<br /> </strong></th>
   <th><strong>Vorteile</strong></th>
   <th><strong>Nachteile</strong></th>
  </tr>
  <tr>
   <td>AEM wird als Headless-CMS ohne das <a href="/help/implementing/developing/hybrid/reference-materials.md">SPA Editor SDK-Framework</a> verwendet.</td>
   <td>Die Frontend-Entwicklungsperson hat die vollständige Kontrolle über die App.</td>
   <td><p>Inhaltsautorinnen bzw. -autoren können das Inhaltserstellungserlebnis von AEM nicht nutzen.</p> <p>Der Code ist weder portabel noch wiederverwendbar, wenn er statische Referenzen oder Routing enthält.</p> <p>Eine Verwendung des Vorlageneditors ist nicht zulässig. Daher muss die Frontend-Entwicklungsperson bearbeitbare Vorlagen über das JCR verwalten.</p> </td>
  </tr>
  <tr>
   <td>Die Frontend-Entwicklungsperson verwendet das SPA-Editor-SDK-Framework, gibt jedoch für die Inhaltsautorinnen und -autoren nur ausgewählte Bereiche frei.</td>
   <td>Der Entwickler behält die Kontrolle über die App, indem er Authoring nur in eingeschränkten Bereichen der App aktiviert.</td>
   <td><p>Autoren von Inhalten sind auf eine begrenzte Anzahl von AEM-Inhaltserstellungsfunktionen beschränkt.</p> <p>Es besteht die Gefahr, dass der Code nicht portabel oder wiederverwendbar ist, wenn er statische Referenzen oder Routing enthält.</p> <p>Eine Verwendung des Vorlageneditors ist nicht zulässig. Daher muss die Frontend-Entwicklungsperson bearbeitbare Vorlagen über das JCR verwalten.</p> </td>
  </tr>
  <tr>
   <td>Das Projekt nutzt komplett das SPA-Editor-SDK, die Frontend-Komponenten werden als Bibliothek entwickelt und die Verwaltung der Inhaltsstruktur der App wird an AEM übertragen.</td>
   <td><p>Die App ist wiederverwendbar und portabel.</p> <p>Der Inhaltsautor kann die App mit den Inhaltserstellungsfunktionen von AEM bearbeiten.<br /> </p> <p>Die SPA ist mit dem Vorlageneditor kompatibel.</p> </td>
   <td><p>Der Entwickler hat keine Kontrolle über die Struktur der App und den Teil des Inhalts, der an AEM delegiert wurde.</p> <p>Der Entwickler kann aber Bereiche der App für Inhalte reservieren, die nicht mit AEM erstellt werden sollen.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Obwohl alle Modelle in AEM unterstützt werden, können die Inhaltsautorinnen und -autoren nur dann mit dem Inhalt der SPA in AEM interagieren und ihn bearbeiten, wenn sie das dritte Modell implementieren (und die empfohlenen [SPA-Entwicklungsprinzipien](#spa-development-principles-for-aem) befolgen).

## Migrieren vorhandener SPAs zu AEM {#migrating-existing-spas-to-aem}

Wenn Ihre SPA den [SPA-Entwicklungsprinzipien für AEM](#spa-development-principles-for-aem) entspricht, funktioniert Ihre SPA in AEM und kann mit dem AEM-SPA-Editor bearbeitet werden.

Führen Sie die folgenden Schritte aus, um Ihre bestehende SPA für die Zusammenarbeit mit AEM bereitzumachen.

1. **Gestalten Sie Ihre JS-Komponenten modular.** – Gestalten Sie sie so, dass sie in beliebiger Reihenfolge, Position und Größe gerendert werden können.
1. **Verwenden Sie die vom SDK bereitgestellten Container, um Ihre Komponenten auf dem Bildschirm zu platzieren.** – AEM bietet eine Seiten- und Absatzsystemkomponente, die Sie verwenden können.
1. **Erstellen Sie für jede JS-Komponente eine AEM-Komponente.** – Die AEM-Komponenten definieren das Dialogfeld und die JSON-Ausgabe.

## Anweisungen für Frontend-Entwickler {#instructions-for-front-end-developers}

Wenn eine Frontend-Entwicklungsperson damit beauftragt wird, eine SPA für AEM zu erstellen, besteht die wichtigste Aufgabe darin, sich mit ihr auf die Komponenten und ihre JSON-Modelle zu einigen.

Im Folgenden werden die Schritte erläutert, die eine Frontend-Entwicklungsperson bei der Entwicklung einer SPA für AEM befolgen muss.

1. **Einigen Sie sich hinsichtlich der Komponenten und ihrer JSON-Modelle**

   AEM-Frontend/Backend-Entwicklungspersonen müssen sich auf die erforderlichen Komponenten und ein Modell einigen, damit eine Eins-zu-Eins-Übereinstimmung der SPA-Komponenten mit den Backend-Komponenten besteht.

   AEM-Komponenten sind weiterhin erforderlich, insbesondere um Bearbeitungsdialogfelder bereitzustellen und das Komponentenmodell zu exportieren.

1. **In React-Komponenten greifen Sie auf das Modell zu über`this.props.cqModel`**

   Sobald Komponenten vereinbart sind und das JSON-Modell vorhanden ist, kann der Frontend-Entwickler die SPA entwickeln und über `this.props.cqModel` bequem auf das JSON-Modell zugreifen.

1. **Implementieren der `render()`-Methode der Komponente**

   Der Frontend-Entwickler implementiert die `render()`-Methode nach Belieben und kann die Felder der `cqModel`-Eigenschaft verwenden. Diese Methode gibt das DOM und die HTML-Fragmente aus, die in die Seite eingefügt werden. Diese Methode ist auch die Standardmethode zur Erstellung einer App in React.

1. **Ordnen Sie die Komponente dem AEM-Ressourcentyp zu via`MapTo()`**

   Die Zuordnung speichert Komponentenklassen und wird von der bereitgestellten `Container`-Komponente intern zum Abrufen und dynamischen Instanziieren von Komponenten basierend auf dem angegebenen Ressourcentyp genutzt.

   Diese Zuordnung dient als „Kleber“ zwischen Front- und Backend, sodass der Editor weiß, welchen Komponenten die React-Komponenten entsprechen.

   `Page` und `ResponsiveGrid` sind gute Beispiele für Klassen, die den grundlegenden `Container` erweitern.

1. **Definieren Sie `EditConfig` der Komponente als Parameter für`MapTo()`**

   Dieser Parameter teilt dem Editor mit, wie die Komponente benannt werden soll, solange sie noch nicht gerendert ist oder über keinen zu rendernden Inhalt verfügt.

1. **Erweitern Sie die bereitgestellte `Container`-Klasse für Seiten und Container**

   Seiten und Absatzsysteme sollten diese Klasse erweitern, damit die Übertragung an innere Komponenten erwartungsgemäß funktioniert.

1. **Implementieren Sie eine Routing-Lösung, die die HTML5-`History`-API verwendet.**

   Wenn `ModelRouter` aktiviert ist, löst der Aufruf der Funktionen `pushState` und `replaceState` eine Anfrage an `PageModelManager` aus, um ein fehlendes Fragment des Modells abzurufen.

   Die aktuelle Version von `ModelRouter` unterstützt nur die Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad von Sling-Modell-Einstiegspunkten verweisen. Der Einsatz von Vanity-URLs oder -Aliassen wird nicht unterstützt.

   Der `ModelRouter` kann deaktiviert oder so konfiguriert werden, dass eine Liste von regulären Ausdrücken ignoriert wird.

## AEM-Agnostik {#aem-agnostic}

Diese Code-Blöcke veranschaulichen, dass Ihre React- und Angular-Komponenten nichts Spezifisches für Adobe oder AEM benötigen.

* Alles, was sich in der JavaScript-Komponente befindet, ist AEM-agnostisch.
* AEM-spezifisch ist jedoch, dass die JS-Komponente mit dem MapTo-Hilfsprogramm einer AEM-Komponente zugeordnet werden muss.

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

  In dieser Umgebung wird die Quelle für die SPA-Anwendung und die Komponentenquelle ausgecheckt.

   * Der NPM-clientlib-Generator erstellt aus dem SPA-Projekt eine Client-Bibliothek.
   * Diese Bibliothek wird von Maven verwendet und vom Maven Build-Plugin zusammen mit der Komponente für AEM Author bereitgestellt.

* **AEM Author**

  Inhalte werden im AEM Author erstellt, einschließlich der Authoring-SPAs.

  Wenn eine SPA in der Authoring-Umgebung mit dem SPA-Editor bearbeitet wird:

   1. Die SPA fordert den äußeren HTML-Code an.
   1. Das CSS wird geladen.
   1. Das JavaScript der SPA-Anwendung wird geladen.
   1. Sobald die SPA-Anwendung ausgeführt wird, wird die JSON angefordert, damit die App das DOM der Seite einschließlich der `cq-data`-Attribute erstellen kann.
   1. Diese `cq-data`-Attribute ermöglichen es dem Editor, zusätzliche Seiteninformationen zu laden, sodass er weiß, welche Bearbeitungskonfigurationen für die Komponenten verfügbar sind.

* **AEM Publish**

  Hier werden die erstellten Inhalte und kompilierten Bibliotheken, einschließlich SPA-Anwendungsartefakte, Client-Bibliotheken und Komponenten, zur öffentlichen Nutzung veröffentlicht.

* **Dispatcher/CDN**

  Der Dispatcher dient für Besucherinnen und Besucher der Site als Zwischenspeicherebene von AEM.
   * Anforderungen werden ähnlich wie in der AEM-Authoring-nstanz verarbeitet. Die Seiteninformationen werden jedoch nicht angefordert, da sie nur vom Editor benötigt werden.
   * JavaScript, CSS, JSON und HTML werden zwischengespeichert, wodurch die Seite für eine schnelle Bereitstellung optimiert wird.

>[!NOTE]
>
>In AEM gibt es keine Notwendigkeit, JavaScript-Build-Mechanismen oder das JavaScript selbst auszuführen. AEM hostet lediglich die kompilierten Artefakte aus der SPA-Anwendung.

## Nächste Schritte {#next-steps}

* [Erste Schritte mit SPAs in AEM unter Verwendung von React](getting-started-react.md) zeigt, wie unter Verwendung von React eine einfache SPA für die Zusammenarbeit mit dem SPA-Editor in AEM erstellt wird.
* [Erste Schritte mit SPAs in AEM unter Verwendung von Angular](getting-started-angular.md) zeigt, wie unter Verwendung von Angular eine einfache SPA für die Zusammenarbeit mit dem SPA-Editor in AEM erstellt wird.
* [SPA-Editor – Überblick](editor-overview.md) vertieft das Kommunikationsmodell zwischen AEM und der SPA.
* [WKND-SPA-Projekt](wknd-tutorial.md) ist ein Schritt-für-Schritt-Tutorial zur Implementierung eines einfachen SPA-Projekts in AEM.
* [Dynamisches Modell zur Komponentenzuordnung für SPAs](model-to-component-mapping.md) erläutert das dynamische Modell für die Komponentenzuordnung und dessen Funktionsweise innerhalb von SPAs in AEM.
* [SPA-Blueprint](blueprint.md) liefert gründlichere Informationen zur Funktionsweise des SPA-SDK für AEM, falls Sie SPAs für ein anderes Framework als React oder Angular implementieren möchten. Oder Sie möchten einfach ein tieferes Verständnis erlangen.
