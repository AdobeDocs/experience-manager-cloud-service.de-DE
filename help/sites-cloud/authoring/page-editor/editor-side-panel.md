---
title: Seitenbereich des Seiteneditors
description: Erfahren Sie, wie Sie mit dem Seitenbereich im Seiteneditor AEM Sites-Editor Komponenten und Assets zu Ihrer Seite hinzufügen.
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 48%

---


# Seitenbereich des Seiteneditors {#side-panel}

Erfahren Sie, wie Sie mit dem Seitenbereich im Seiteneditor AEM Sites-Editor Komponenten und Assets zu Ihrer Seite hinzufügen.

## Seitenbereichsmodi {#modes}

Der Seitenbereich kann immer im Seiteneditor durch Tippen oder Klicken auf die **Seitliches Bedienfeld ein/aus** in der Symbolleiste des Seiteneditors.

![Seitliches Bedienfeld ein/aus](assets/editor-side-panel-side-panel-toggle.png)

Wenn Sie den Seitenbereich öffnen, wird er von der linken Seite aus eingeblendet und Sie können dann aus drei wichtigen Registerkarten auswählen:

* [Komponenten-Browser](#components-browser) , um neue Inhalte zu Ihrer Seite hinzuzufügen
* [Der Asset-Browser](#assets-browser) , um neue Assets zu Ihrer Seite hinzuzufügen
* [Inhaltsstruktur](#content-tree) , um die Struktur Ihrer Seite zu durchsuchen

## Komponenten-Browser {#components-browser}

[Komponenten](/help/implementing/developing/components/overview.md) sind die Bausteine, die zum Erstellen von Inhalten mit dem AEM Seiteneditor verwendet werden. Sie platzieren mehrere Komponenten auf einer Seite und konfigurieren deren Optionen zum Erstellen Ihrer Inhaltsseite.

Der Komponenten-Browser enthält alle Komponenten, die zur Verwendung auf der aktuellen Seite verfügbar sind. Sie können diese an die gewünschte Position ziehen und dann bearbeiten, um Inhalte hinzuzufügen.

Tippen oder klicken Sie auf **Komponenten** Registerkarte im Seitenbereich, um auf die **Komponenten** Browser.

![Symbol des Komponenten-Browsers im Seitenbereich](assets/editor-side-panel-components-browser.png)

Das tatsächliche Erscheinungsbild und die Handhabung hängen vom verwendeten Gerätetyp ab.

### Mobilgerät {#mobile-device-components-browser}

Beim Öffnen des Komponenten-Browsers auf einem Mobilgerät wird die zu bearbeitende Seite vollständig abgedeckt.

Um Ihrer Seite eine Komponente hinzuzufügen, wählen Sie die Komponente aus, ziehen Sie sie und verschieben Sie sie nach rechts. Der Komponenten-Browser wird geschlossen und die Seite wird erneut angezeigt, wo Sie die Komponente platzieren können.

![Komponenten-Browser auf einem Mobilgerät](assets/editor-side-panel-mobile-device.png)

>[!NOTE]
>
>Ein Mobilgerät wird erkannt, wenn die Breite weniger als 1024 Pixel beträgt.

### Desktop-Gerät {#desktop-device-components-browser}

Wenn Sie den Komponenten-Browser auf einem Desktop-Gerät öffnen, wird er links im Fenster angezeigt.

Um der Seite eine Komponente hinzuzufügen, klicken Sie auf die gewünschte Komponente und ziehen Sie sie an die gewünschte Position.

![Komponenten-Browser auf einem Desktop-Gerät](/help/sites-cloud/authoring/assets/component-browser-desktop.png)

### Komponenten-Browser verwenden {#using-component-browser}

Komponenten im **Komponenten** -Browser durch:

* Komponentenname
* Komponentengruppe (in grau)
* Symbol oder Abkürzung
   * Die Symbole für die Standardkomponenten sind monochrom dargestellt.
   * Für die Abkürzungen werden immer die ersten zwei Buchstaben des Komponentennamens verwendet.

In der oberen Symbolleiste des **Komponenten-Browsers** haben Sie folgende Möglichkeiten:

* Komponenten nach Namen filtern
* Mittels Dropdown-Auswahl die Anzeige auf eine bestimmte Gruppe begrenzen

Für eine detailliertere Beschreibung der Komponente können Sie (falls verfügbar) im **Komponenten-Browser** das Informationssymbol neben der Komponente auswählen. Zum Beispiel für das **Inhaltsfragment**:

![Komponenten-Browser-Informationen](assets/editor-side-panel-component-description.png)

Detaillierte Informationen zu den verfügbaren Komponenten finden Sie unter [Komponentenkonsole.](/help/sites-cloud/authoring/components-console.md)

## Asset-Browser {#assets-browser}

Die **Assets** alle [Assets](/help/assets/overview.md) die zur Verwendung auf Ihrer aktuellen Seite verfügbar sind.

Tippen oder klicken Sie auf **Assets** im Seitenbereich, um durch die Assets zu navigieren.

![Schaltfläche „Asset-Browser“](assets/editor-side-panel-assets-browser-tab.png)

Der unendliche Bildlauf wird verwendet, um die Liste der Assets nach Bedarf zu erweitern, wenn Sie einen Bildlauf durchführen.

![Asset-Browser](assets/editor-side-panel-assets-browser.png)

Das tatsächliche Aussehen und die Nutzung hängen vom verwendeten Gerätetyp ab:

### Mobilgerät {#mobile-device-assets-browser}

Beim Öffnen des Asset-Browsers auf einem Mobilgerät wird die zu bearbeitende Seite vollständig abgedeckt.

Um ein Asset zu Ihrer Seite hinzuzufügen, wählen Sie das gewünschte Asset aus, ziehen Sie es und verschieben Sie es dann nach rechts. Der Asset-Browser wird geschlossen und die Seite wird erneut angezeigt. Dort können Sie das Asset zur erforderlichen Komponente hinzufügen.

![Asset-Browser auf Mobilgerät](assets/editor-side-panel-assets-browser-mobile.png)

>[!NOTE]
>
>Ein Mobilgerät wird erkannt, wenn die Breite weniger als 1024 Pixel beträgt.

### Desktop-Gerät {#desktop-device-assets-browser}

Wenn Sie den Asset-Browser auf einem Desktop-Gerät öffnen, wird er auf der linken Seite des Fensters geöffnet.

Um ein Asset zu Ihrer Seite hinzuzufügen, wählen Sie das gewünschte Asset aus und ziehen Sie es auf die gewünschte Komponente oder Position.

![Asset-Browser auf Desktop-Gerät](assets/editor-side-panel-assets-browser-desktop.png)

### Verwenden des Asset-Browsers {#using-assets-browser}

Um ein Asset zu der Seite hinzuzufügen, wählen Sie es aus und ziehen Sie es an die gewünschte Position. Dabei kann es sich um Folgendes handeln:

* Eine vorhandene Komponente des entsprechenden Typs.
   * Sie können beispielsweise ein Asset des Typs „Bild“ auf eine Bildkomponente ziehen.
* Ein [Platzhalter](/help/sites-cloud/authoring/page-editor/edit-content.md#component-placeholder) im Absatzsystem zum Erstellen einer Komponente des entsprechenden Typs.
   * Sie können beispielsweise ein Asset des Typs „Bild“ in das Absatzsystem ziehen, um eine Bildkomponente zu erstellen.

>[!NOTE]
>
>Das Ziehen und Ablegen von Assets ist für bestimmte Assets und Komponententypen verfügbar. Weitere Einzelheiten finden Sie unter [Einfügen einer Komponente mit dem Asset-Browser](/help/sites-cloud/authoring/page-editor/edit-content.md#adding-a-component-from).

In der Symbolleiste des Asset-Browsers können Sie Assets nach folgenden Kriterien filtern:

* Name
* Pfad
* Asset-Typ wie Bilder, Videos, Dokumente, Absätze, Inhaltsfragmente und Experience Fragments
* Asset-Eigenschaften wie Ausrichtung und Stil
   * Nur für bestimmte Asset-Typen verfügbar

Wenn Sie eine Änderung an einem der Assets vornehmen möchten, können Sie den [Asset-Editor](/help/assets/manage-digital-assets.md) auch direkt über den Browser starten. Klicken Sie dazu einfach auf das Bearbeitungssymbol neben dem Asset-Namen.

![Schaltfläche „Asset bearbeiten“](assets/editor-side-panel-asset-edit-button.png)

## Inhaltsstruktur {#content-tree}

Die **Inhaltsstruktur** bietet einen Überblick über alle auf der Seite verwendeten Komponenten in einer hierarchischen Darstellung, sodass Sie direkt feststellen können, wie die Seite aufgebaut ist.

>[!NOTE]
>
>Beim Bearbeiten einer Seite auf einem Mobilgerät ist die Inhaltsstruktur nicht verfügbar (wenn die Browser-Breite weniger als 1.024 Pixel beträgt).

Tippen oder klicken Sie auf **Inhaltsstruktur** -Tab, um auf die Inhaltsstruktur zuzugreifen.

![Schaltfläche „Inhaltsstruktur“](assets/editor-side-panel-content-tree-tab.png)

Mit dieser Strukturansicht Ihrer Seite oder Vorlage können Sie leicht nachvollziehen, wie die darauf verwendeten Komponenten hierarchisch strukturiert sind. Auf einer komplexeren Seite können Sie so zudem einfacher zwischen Komponenten auf der Seite wechseln.

![Inhaltsstruktur](assets/editor-side-panel-content-tree.png)

Eine Seite kann problemlos aus vielen Komponenten desselben Typs bestehen. Daher wird in der Inhaltsstruktur nach dem Namen des Komponententyps (in Schwarz) beschreibender Text (grau) angezeigt. Der Text für diese Beschreibung wird aus den allgemeinen Eigenschaften der Komponente (z. B. Titel oder Text) entnommen.

Die Komponententypen werden in der für die Benutzeroberfläche ausgewählten Sprache angezeigt, die Beschreibung dagegen in der Sprache, die für die Seite verwendet wird.

Durch Klicken auf den Richtungspfeil neben einer Komponente wird die entsprechende Ebene ein- bzw. ausgeblendet.

![Pfeilerweiterung für Inhaltsstruktur](assets/editor-side-panel-content-tree-chevron.png)

Durch Klicken auf die Komponente wird diese im Seiteneditor markiert. Die verfügbaren Aktionen hängen vom Seitenstatus ab. Zum Beispiel:

## Eine einfache Seite {#basic-page}

Die Komponenten einer Basisseite weisen die üblichen Optionen auf.

![Inhaltsstruktur hervorgehoben](assets/editor-side-panel-content-tree-highlighted.png)

Wenn Sie in der Struktur auf eine Komponente klicken, die bearbeitbar ist, wird rechts neben ihrem Namen ein Schraubenschlüssel-Symbol angezeigt. Durch Klicken auf dieses Symbol wird das Dialogfeld „Bearbeiten“ für die Komponente geöffnet.

![Schaltfläche zum Bearbeiten einer Inhaltsstruktur](assets/editor-side-panel-content-tree-edit.png)

### Eine Live Copy {#live-copy}

Eine Seite, die Teil eines [Livecopy](/help/sites-cloud/administering/msm/overview.md), wo Komponenten von einer anderen Seite übernommen werden, haben unterschiedliche Optionen.

## Browser für zugehörige Inhalte {#associated-content-browser}

Wenn Ihre Seite Inhaltsfragmente enthält, können Sie auch auf die [Browser für zugehörige Inhalte.](/help/sites-cloud/authoring/fragments/content-fragments.md#using-associated-content)
