---
title: Struktur der AEM Benutzeroberfläche
description: Die Benutzeroberfläche der AEM umfasst mehrere grundlegende Prinzipien und besteht aus mehreren Schlüsselelementen
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 51%

---


# Structure of the AEM UI {#structure-of-the-aem-ui}

Die Benutzeroberfläche der AEM umfasst mehrere grundlegende Prinzipien und setzt sich aus mehreren Schlüsselelementen zusammen:

## Konsolen {#consoles}

### Grundlegendes Layout und Größenanpassung {#basic-layout-and-resizing}

Die Benutzeroberfläche eignet sich sowohl für Mobilgeräte als auch für Desktop-Geräte. Anstatt zwei Stile zu erstellen, verwendet AEM einen Stil, der für alle Bildschirme und Geräte funktioniert.

Alle Module verwenden dasselbe Basislayout. In AEM sieht es wie folgt aus:

![AEM Sites Console](assets/ui-sites-console.png)

Das Layout entspricht einem reaktionsfähigen Designstil und passt sich an die Größe des verwendeten Geräts/Fensters an.

Wenn beispielsweise die Auflösung unter 1024 px liegt (z. B. auf einem Mobilgerät), wird die Anzeige entsprechend angepasst:

![Sites, Konsolen, mobile Ansicht](assets/ui-sites-mobile.png)

### Kopfzeilenleiste {#header-bar}

![AEM](assets/ui-header-bar.png)

Die Kopfzeilenleiste zeigt globale Elemente, z. B.:

* das Logo und das spezifische Produkt/die spezifische Lösung, das/die Sie derzeit verwenden; aem bildet dies auch einen Link zur globalen Navigation
* Suchen
* Symbol für den Zugriff auf die Hilferessourcen
* Symbol für den Zugriff auf andere Lösungen
* Ein Indikator (und der Zugriff auf) alle Warnungen oder Posteingangselemente, die auf Sie warten
* Das Benutzersymbol sowie eine Verknüpfung zu Ihrer Profil-Verwaltung

### Symbolleiste {#toolbar}

Die Symbolleiste steht im Zusammenhang mit Ihren Positionierungs- und Oberflächenwerkzeugen, die für die Steuerung der Ansicht oder der Assets auf der folgenden Seite relevant sind. Die Symbolleiste ist produktspezifisch, es gibt jedoch einige gemeinsame Elemente.

Sie zeigt stets die aktuell möglichen Aktionen an:

![AEM Sites-Symbolleiste](assets/ui-sites-toolbar.png)

Die möglichen Aktionen hängen auch davon ab, ob eine Ressource ausgewählt ist:

![AEM Sites-Symbolleiste ausgewählt](assets/ui-sites-toolbar-selected.png)

### Linke Leiste {#left-rail}

Die linke Leiste kann nach Bedarf geöffnet oder ausgeblendet werden. Sie zeigt Folgendes an:

* **Nur Inhalt**
* **Inhaltsstruktur**
* **Timeline**
* **Verweise**
* **Filter**

Die Standardeinstellung ist **nur Inhalt** (Leiste ausgeblendet).

![Linke Leiste](assets/ui-left-rail.png)

## Bearbeiten von Seiten {#page-authoring}

Beim Bearbeiten von Seiten gibt es folgende strukturelle Bereiche.

### Inhalts-Frame {#content-frame}

Der Seiteninhalt wird im Inhalts-Frame gerendert. Der Inhalts-Frame ist komplett unabhängig vom Editor, sodass Konflikte durch CSS- oder JavaScript-Code vermieden werden.

Der Inhalts-Frame wird im rechten Bereich des Fensters unter der Symbolleiste angezeigt.

![Inhaltsrahmen](assets/ui-content-frame.png)

### Editor-Frame {#editor-frame}

Der Editorrahmen aktiviert die Bearbeitungsfunktionen.

Der Editor-Frame ist ein Container (Abstraktion) für alle Seitenbearbeitungselemente. Er wird über dem Inhalts-Frame angezeigt und enthält:

* Die obere Symbolleiste
* Das Seitenbedienfeld
* Alle Überlagerungen
* jedes andere Seitenerstellungselement; zum Beispiel die Komponenten-Symbolleiste

![Editor-Frame](assets/ui-editor-frame.png)

### Seitenbereich {#side-panel}

Diese enthält drei Standardregisterkarten. Auf den Registerkarten &quot; **Assets** &quot;und &quot; **Komponenten** &quot;können Sie diese Elemente auswählen, aus dem Bedienfeld ziehen und auf der Seite ablegen. Auf der Registerkarte &quot; **Inhaltsstruktur** &quot;können Sie die Hierarchie der Inhalte auf der Seite überprüfen.

Der Seitenbereich ist standardmäßig ausgeblendet. Wenn sie ausgewählt ist, wird sie entweder auf der linken Seite angezeigt oder sie wird über das gesamte Fenster verschoben, wenn die Fenstergröße unter einer Breite von 1024 px liegt. wie z. B. auf einem Mobilgerät.

![Seitenbedienfeld](assets/ui-side-panel.png)

### Seitenbereich – Assets {#side-panel-assets}

Auf der Registerkarte „Assets“ können Sie aus einer Reihe von Assets auswählen. Sie können auch nach einem bestimmten Begriff filtern oder eine Gruppe auswählen.

![Registerkarte &quot;Assets&quot;](assets/ui-side-panel-assets.png)

### Seitenbereich – Asset-Gruppen {#side-panel-asset-groups}

Auf der Registerkarte &quot;Assets&quot;finden Sie eine Dropdown-Liste, in der Sie die jeweiligen Asset-Gruppen auswählen können.

![Asset-Gruppen](assets/ui-side-panel-asset-groups.png)

### Seitenbereich – Komponenten {#side-panel-components}

Auf der Registerkarte „Komponenten“ können Sie aus verschiedenen Komponenten auswählen. Sie können auch nach einem bestimmten Begriff filtern oder eine Gruppe auswählen.

![Registerkarte &quot;Komponenten&quot;](assets/ui-side-panel-components.png)

### Seitenbedienfeld - Inhaltsstruktur {#side-panel-content-tree}

Auf der Registerkarte &quot;Inhaltsstruktur&quot;können Sie die Inhaltshierarchie auf der Seite Ansicht haben. Wenn Sie auf einen Eintrag in der Registerkarte klicken, wird das Element auf der Seite im Editor geöffnet und ausgewählt.

![Inhaltsstruktur](assets/ui-side-panel-content-tree.png)

### Überlagerungen {#overlays}

Diese überlagern den Inhalts-Frame und werden von [Ebenen](#layer) genutzt, um die (vollständig transparente) Interaktion mit Komponenten und ihrem Inhalt zu ermöglichen.

Die Überlagerungen befinden sich im Editor-Frame (neben allen anderen Seitenbearbeitungselementen); sie überlagern jedoch die entsprechenden Elemente im Inhalts-Frame.

![Überlagerungen](assets/ui-overlays.png)

### Ebene {#layer}

Eine Ebene ist eine unabhängige Funktionsgruppe, die Sie aktivieren können, um Folgendes auszuführen:

* Eine andere Ansicht der Seite bereitstellen
* Ermöglicht Ihnen die Manipulation und/oder Interaktion mit einer Seite

Anders als spezifische Aktionen zu einzelnen Komponenten bieten die Ebenen komplexe Funktionen für die gesamte Seite.

AEM enthält mehrere Ebenen, die bereits für das Erstellen von Seiten implementiert sind. darunter beispielsweise Ebenen zum Bearbeiten, Vorschau und Anmerkungen.

>[!NOTE]
>
>Ebenen sind ein Konzept mit hohem Potenzial; sie beeinflussen die Ansicht und die Interaktion des Nutzers mit dem Seiteninhalt. Wenn Sie Ihre eigenen Ebenen entwickeln, stellen Sie sicher, dass die Ebene beim Verlassen eine Bereinigung durchführt.

### Ebenenschalter {#layer-switcher}

Mit dem Ebenenschalter können Sie die Ebene auswählen, die Sie verwenden möchten. Wenn er geschlossen ist, zeigt er die aktuell verwendete Ebene an.

Der Ebenenschalter ist ein Dropdown-Menü in der Symbolleiste (am oberen Rand des Fensters im Editor-Frame).

![Ebenenumschalter](assets/ui-layer-switcher.png)

### Komponentensymbolleiste {#component-toolbar}

Jede Instanz einer Komponente zeigt ihre Symbolleiste an, wenn Sie darauf klicken (entweder einmal oder mit einem langsamen Doppelklick). Die Symbolleiste enthält die spezifischen Aktionen (z. B. Kopieren, Einfügen, Öffnen-Editor), die für die Komponenteninstanz auf der Seite verfügbar sind.

Je nach verfügbarem Platz werden die Komponentensymbolleisten in der oberen oder unteren rechten Ecke der entsprechenden Komponente platziert.

![Komponenten-Symbolleiste](assets/ui-component-toolbar.png)

## Weiterführende Informationen {#further-information}

<!--For more details about the concepts around the touch-enabled UI, continue to the article [Concepts of the AEM Touch-Enabled UI](/help/sites-developing/touch-ui-concepts.md).-->

Weitere technische Informationen finden Sie im [JS-Dokumentationssatz](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/jsdoc/ui-touch/editor-core/index.html) für den Seiteneditor.
