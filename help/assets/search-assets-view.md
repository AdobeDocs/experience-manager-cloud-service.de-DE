---
title: Erfahren Sie, wie man in der  [!DNL Assets view] Assets sucht und findet.
description: Erfahren Sie, wie man in der AEM Assets-Ansicht Assets sucht und findet. Mit der leistungsstarken Suchfunktion können Sie schnell das passende Asset ermitteln und die Geschwindigkeit Ihrer Inhaltserstellung steigern.
role: User
exl-id: abfe6a91-1699-436f-8bf4-0d0bf2369f46
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 100%

---

# Suchen nach Assets in [!DNL Assets view] {#search-assets}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!CONTEXTUALHELP]
>id="assets_search"
>title="Suchen nach Assets"
>abstract="Sie können nach Assets suchen, indem Sie ein Keyword in der Suchleiste eingeben oder Assets nach ihrem Status, Dateityp, MIME-Typ, Erstellungs-, Änderungs- und Ablaufdatum oder ihrer Größe filtern. Zusätzlich zu den Standardfiltern können Sie auch benutzerdefinierte Filter anwenden. Sie können die gefilterten Ergebnisse als gespeicherte Suche oder Smart-Sammlung speichern."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-collections.html?lang=de#manage-smart-collection" text="Erstellung von Smart-Sammlungen"

[!DNL Assets view] bietet eine effektive Suche, die einfach standardmäßig funktioniert. Die Suche ist umfassend, da es sich um eine Volltextsuche handelt. Mit der leistungsstarken Suchfunktion können Sie schnell das passende Asset ermitteln und die Geschwindigkeit Ihrer Inhaltserstellung steigern. [!DNL Assets view] bietet Volltextsuche und Suchvorgänge durch die Metadaten wie Smart-Tags, Titel, Erstellungsdatum und Copyright.

Um nach Assets zu suchen,

* klicken Sie oben auf der Seite in das Suchfeld. Standardmäßig wird innerhalb des Ordners gesucht, den Sie gerade durchsuchen. Führen Sie einen der folgenden Schritte aus:

  ![Suchfeld](assets/search-box.png)

   * Suchen Sie mithilfe eines Keywords und ändern Sie optional den Ordner. Drücken Sie die Eingabetaste.

   * Beginnen Sie die Arbeit mit einem kürzlich angezeigten Asset, indem Sie direkt danach suchen. Klicken Sie in das Suchfeld und wählen Sie aus den Vorschlägen ein kürzlich angezeigtes Asset aus.

## Filtern von Suchergebnissen {#refine-search-results}

Sie können die Suchergebnisse anhand der folgenden Parameter filtern.

![Suchfilter](assets/filters1.png)

*Abbildung: Filtern gesuchter Assets basierend auf verschiedenen Parametern.*

* Asset-Status: Filtern Sie die Suchergebnisse mithilfe eines der Asset-Status `Approved`, `Rejected` oder `No Status`.

* Dateityp: Filtern von Suchergebnissen nach den unterstützten Dateitypen: `Images`, `Documents` und `Videos`.
* MIME-Typ: Filtern nach einem oder mehreren der unterstützten Dateiformate. <!-- TBD:  [supported file formats](/help/using/supported-file-formats.md). -->
* Bildgrösse: Geben Sie eine oder mehrere der minimalen und maximalen Abmessungen zum Filtern von Bildern an. Die Größe wird in Pixeln angegeben und ist nicht die Dateigröße der Bilder.
* Erstellungsdatum: Das Erstellungsdatum des Assets, wie es in den Metadaten angegeben ist. Das verwendete Standarddatumsformat ist `yyyy-mm-dd`.
* Änderungsdatum: Das Datum der letzten Änderung der Assets. Das verwendete Standarddatumsformat ist `yyyy-mm-dd`.

* Ablaufdatum: Filtern Sie die Suchergebnisse anhand des Asset-Status `Expired`. Darüber hinaus können Sie einen Zeitraum für das Ablaufdatum für Assets angeben, um Ihre Suchergebnisse weiter zu filtern.

* Benutzerdefinierte Filter: [Hinzufügen benutzerdefinierter Filter](#custom-filters) zur Benutzeroberfläche der Assets-Ansicht. Sie können diese benutzerdefinierten Filter zusätzlich zu den Standardfiltern anwenden, um Ihre Suchergebnisse zu verfeinern.

Sie können die gesuchten Assets in aufsteigender oder absteigender Reihenfolge nach `Name`, `Relevance`, `Size`, `Modified` und `Created` sortieren. Die gesuchten Assets werden standardmäßig nach `Relevance` sortiert.

## Verwalten von benutzerdefinierten Filtern {#custom-filters}

**Erforderliche Berechtigungen:**  `Can Edit`, `Owner` oder Administrator.

Mit der Assets-Ansicht können Sie auch benutzerdefinierte Filter zur Benutzeroberfläche hinzufügen. Sie können diese benutzerdefinierten Filter dann zusätzlich zu den [Standardfiltern](#refine-search-results) anwenden, um Ihre Suchergebnisse zu verfeinern.

Die Assets-Ansicht bietet die folgenden benutzerdefinierten Filter:

<table>
    <tbody>
     <tr>
      <th><strong>Benutzerspezifischer Filtername</strong></th>
      <th><strong>Beschreibung</strong></th>
     </tr>
     <tr>
      <td>Titel</td>
      <td>Filtern Sie Assets unter Verwendung des Asset-Titels. Der Titel, den Sie in den Suchkriterien, die die Groß- und Kleinschreibung berücksichtigen, angeben, muss genau mit dem Titel des Assets übereinstimmen, damit es in den Ergebnissen angezeigt wird.</td>
     </tr>
     <tr>
      <td>Name</td>
      <td>Filtern Sie Assets unter Verwendung des Asset-Dateinamens. Der Name, den Sie in den Suchkriterien, die die Groß- und Kleinschreibung berücksichtigen, angeben, muss genau mit dem Namen des Assets übereinstimmen, damit es in den Ergebnissen angezeigt wird.</td>
     </tr>
     <tr>
      <td>Asset-Größe</td>
      <td>Filtern Sie Assets, indem Sie in den Suchkriterien für ein Asset, das in den Ergebnissen angezeigt werden soll, einen Größenbereich in Byte festlegen.</td>
     </tr>
     <tr>
      <td>Prognostizierte Tags</td>
      <td>Filtern Sie Assets unter Verwendung des Asset-Smart-Tags. Der Smart-Tag-Name, den Sie in den Suchkriterien, die die Groß- und Kleinschreibung berücksichtigen, angeben, muss genau mit dem Smart-Tag-Namen des Assets übereinstimmen, damit es in den Ergebnissen angezeigt wird. Sie können nicht mehrere Smart-Tags in den Suchkriterien angeben.</td>
     </tr>    
    </tbody>
   </table>

<!--
   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. For example, if you define <b>ma*</b> as the search criteria, Assets view displays assets with title, such as, market, marketing, man, manchester, and so on in the results.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. You can specify multiple smart tags separated by a comma in the search criteria.

   -->

### Hinzufügen benutzerdefinierter Filter {#add-custom-filters}

Hinzufügen benutzerdefinierter Filter

1. Klicken Sie auf **[!UICONTROL Filter]**.

1. Klicken Sie im Abschnitt **[!UICONTROL Benutzerdefinierte Filter]** auf **[!UICONTROL Bearbeiten]** oder auf **[!UICONTROL Filter hinzufügen]**.

   ![Hinzufügen benutzerdefinierter Filter](assets/add-custom-filters.png)

1. Wählen Sie im Dialogfeld **[!UICONTROL Verwaltung benutzerdefinierter Filter]** die Filter aus, die Sie der vorhandenen Filterliste hinzufügen möchten. Wählen Sie **[!UICONTROL Benutzerdefinierte Filter]** aus, um alle Filter auszuwählen.

1. Klicken Sie auf **[!UICONTROL Bestätigen]**, um die Filter zur Benutzeroberfläche hinzuzufügen.

### Entfernen benutzerdefinierter Filter {#remove-custom-filters}

Entfernen benutzerdefinierter Filter

1. Klicken Sie auf **[!UICONTROL Filter]**.

1. Klicken Sie im Abschnitt **[!UICONTROL Benutzerdefinierte Filter]** auf **[!UICONTROL Bearbeiten]**.

1. Heben Sie im Dialogfeld **[!UICONTROL Verwaltung benutzerdefinierter Filter]** die Auswahl der Filter auf, die Sie aus der Liste der vorhandenen Filter entfernen möchten.

1. Klicken Sie auf **[!UICONTROL Bestätigen]**, um die Filter aus der Benutzeroberfläche zu entfernen.

## Suchen von Assets mithilfe von [!DNL Adobe Firefly] {#search-firefly}

Sie können nach einem Asset suchen, das in keinem der Asset-Ordner verfügbar ist, indem Sie die [!DNL Adobe Firefly] Asset-Suchfunktion in [!DNL Experience Manager Assets] verwenden. So können Sie effizient und in Echtzeit Assets generieren, die nicht in den Asset-Ordnern gespeichert sind.

### Vorbereitung {#search-assets-firefly-prereqs}

Sie müssen ein aktives Abonnement von [!DNL Adobe Express] haben.

### Generieren von Assets {#generate-assets-firefly}

So generieren Sie neue Assets mit [!DNL Adobe Firefly]:

1. Navigieren Sie zum [!DNL AEM Assets]-Workspace.

1. Geben Sie den Asset-Namen in die Suchleiste ein. Sie können beispielsweise ein Asset mit dem Keyword `Bugatti Type 57` suchen. Bei der Suche nach dem Asset werden keine Ergebnisse gefunden, da das Asset in keinem der Asset-Ordner vorhanden ist. Um Assets mit KI zu generieren, klicken Sie auf **[!UICONTROL Mit Firefly generieren]**. Der [!DNL Adobe Firefly]-Bildschirm wird angezeigt.

   ![Integration mit Firefly](assets/firefly-integration.png)

   Die neuen Assets wurden erfolgreich generiert. Darüber hinaus können Sie die Bildbeschreibung ändern, indem Sie den neuen Text-Prompt in das Beschreibungsfeld eingeben. [Erfahren Sie, wie Sie einen guten KI-Prompt schreiben, um außergewöhnliche und relevante Inhalte zu generieren.](https://helpx.adobe.com/de/firefly/using/tips-and-tricks.html) Alternativ können Sie [Bilder mit verschiedenen anderen Funktionen bearbeiten, wie dem Ändern von Stil, Bildabmessungen und mehr.](https://helpx.adobe.com/de/firefly/using/text-to-image.html)

   ![Integration mit Firefly](assets/bugatti-type-57.png)

1. Wählen Sie ein Bild aus, das Sie speichern möchten. Klicken Sie auf **[!UICONTROL Speichern]**, um die Assets in Ihrem bevorzugten Ordner zu speichern und so einfach darauf zuzugreifen.

1. Ein Formular zum Speichern des Assets wird angezeigt. Geben Sie die folgenden Felder an:

   * Geben Sie einen Namen für die Datei in das Feld **Speichern unter** ein.
   * Wählen Sie einen Zielordner aus.
   * Geben Sie Details wie den Projekt- oder Kampagnennamen, Keywords, Kanäle, den Zeitrahmen und die Region an.

   ![Integration mit Firefly](assets/save-generated-asset.png)

1. Klicken Sie auf **Als neues Asset speichern**, um das Asset bzw. die Assets zu speichern.

### Hochladen von Assets {#upload-assets-firefly}

So laden Sie das generierte Asset in das Asset-Repository hoch:

1. Klicken Sie auf **[!UICONTROL Hochladen]**.
1. Wählen Sie den Asset-Ordner aus, in den Sie das Asset hochladen müssen, und klicken Sie auf **[!UICONTROL Ordner auswählen]**.
   ![Hochladen eines Assets](assets/upload-asset-firefly.jpg)

## Gespeicherte Suchvorgänge {#saved-search}

In [!DNL Assets view] ist die Suchfunktion recht einfach zu verwenden. Sie können nicht nur ein Keyword ins Suchfeld eingeben und die Eingabetaste drücken, um die Ergebnisse aufzurufen, sondern auch schnell mit einem einzigen Klick erneut nach Ihren kürzlich gesuchten Keywords suchen.

Sie können die Suchergebnisse auch nach bestimmten Kriterien rund um Metadaten und Art der Assets filtern. Mit [!DNL Assets view] können Sie bei häufig verwendeten Filtern die Suchparameter speichern, um das Sucherlebnis zu verbessern. Um zu suchen und den Filter mit nur einem Klick anzuwenden, können Sie auch die gespeicherte Suche auswählen.

Um eine gespeicherte Suche zu erstellen, suchen Sie nach einem Asset, wenden Sie einen oder mehrere Filter an und klicken Sie im Bedienfeld [!UICONTROL Filter] auf **[!UICONTROL Speichern unter]** > **[!UICONTROL Gespeicherte Suche]**. Sie können auch auf **[!UICONTROL Speichern unter]** klicken und **[!UICONTROL Smart-Sammlung]** wählen, um die Ergebnisse als Smart-Sammlung zu speichern. Siehe [Erstellen einer Smart-Sammlung](manage-collections.md#create-a-smart-collection) für weitere Details.

![Erstellen einer Smart-Sammlung](assets/create-smart-collection.png)

<!-- TBD: Search behavior. Full-text search. Ranking and rank boosts. Hidden assets.
Report poor UX that users can only save a filtered search and not a simple search.
.
Are other supported files fully indexed and support full-text search? Eg. audio/videos files can at best have metadata indexed.
Anything about ranking of assets displayed in search results?

What about temporarily hiding an asset (suspending search on it) from the search results? If an asset is undergoing review collaboration, should it be used by others? Should it be hidden in search?

When userA is searching and userB add an asset that matches search results, will the asset display in search as soon as userA refreshes the page? Assuming indexing is near real-time. May not be so for bulk uploads.
-->

## Arbeiten mit Suchergebnissen {#work-with-search-results}

Sie können die Assets auswählen, die in den Suchergebnissen angezeigt werden, und die folgenden Aktionen ausführen:

* **Nach ähnlichem Bild suchen**: Suchen Sie anhand der Metadaten und Smart-Tags nach ähnlichen Bild-Assets in der Assets-Benutzeroberfläche.

* **Details**: Zeigen Sie Asset-Eigenschaften an und bearbeiten Sie diese.

* **Herunterladen**: Laden Sie ein Asset herunter.

* **Zur Sammlung hinzufügen**: Fügen Sie das ausgewählte Asset zu einer Sammlung hinzu.

* **An Schnellzugriff anheften**: [Heften Sie ein Asset an](my-workspace-assets-view.md), um später im Bedarfsfall schneller darauf zugreifen zu können. Alle angehefteten Elemente werden im Dashboard „Mein Arbeitsbereich“ im Abschnitt **Schnellzugriff** angezeigt.

* **In Adobe Express öffnen**: Bearbeiten Sie ein Bild in der integrierten Adobe Express-Anwendung auf dem Experience Manager Assets-Bildschirm.

* **Bearbeiten**: Bearbeiten Sie das Bild mit Adobe Express.

* **Link freigeben**: [Teilen Sie Links](share-links-for-assets-view.md) für ein Asset mit anderen Benutzenden, damit sie darauf zugreifen und es herunterladen können.

* **Löschen**: Löschen Sie ein Asset.

* **Kopieren**: Kopieren Sie ein Asset in einen anderen Ordner.

* **Verschieben**: Verschieben Sie ein Asset in einen anderen Ordner.

* **Umbenennen**: Benennen Sie ein Asset um.

* **In Bibliotheken kopieren**: Fügen Sie ein Asset zur Bibliothek hinzu.

* **Aufgaben zuweisen**: Weisen Sie Benutzenden Aufgaben für ein Asset zu.

* **Beobachten**: [Überwachen Sie Vorgänge](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/search-assets), die für ein Asset durchgeführt werden.

## Konfigurieren der Startseite für die erste Suche {#configuring-search-first-homepage}

Mit der Assets-Ansicht können Sie die Standard-Landingpage Ihrer Organisation auswählen. Bei der Verwendung der ersten Suche als Startseite haben Sie auch die Möglichkeit, das Branding der Seite anzupassen, indem Sie den Hintergrund und die Logo-Bilder so konfigurieren, dass sie Ihrer Marke entsprechen.

Gehen Sie wie folgt vor, um die Startseite für die erste Suche zu konfigurieren:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.
1. Wählen Sie **[!UICONTROL Erste Suche]**. Es öffnet sich die Konfiguration der ersten Suche. Sie können für Ihre Startseite die [Ausrichtung](#setting-alignment-search-bar) oder [Hintergrund- und Logo-Bilder](#setting-background-image-and-logo) festlegen.

### Festlegen der Ausrichtung der Suchleiste {#setting-alignment-search-bar}

[!DNL Assets view] ermöglicht es Ihnen, die Ausrichtung der Suchleiste zu ändern. Sie können die Suchleiste entweder in der Mitte oder oben anzeigen lassen. Wählen Sie die gewünschte Ausrichtung und klicken Sie auf **[!UICONTROL Speichern]**.

![Ausrichtung der Startseite für die erste Suche](assets/search-first-alignment.png)

### Festlegen der Hintergrund- und Logo-Bilder für die Startseite {#setting-background-image-and-logo}

Sie können zu Ihrer Startseite für die erste Suche ein Markenlogo und ein Hintergrundbild hinzufügen. Führen Sie die folgenden Schritte aus:

1. Navigieren Sie zum Abschnitt **[!UICONTROL Hintergrund- und Logo-Bild]** unter **[!UICONTROL Startseite]**.
1. Klicken Sie auf **[!UICONTROL Ersetzen]**, um die Bilder in einem vorhandenen Asset-Repository zu durchsuchen.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Öffnen Sie die [Vorschau](#preview-configured-homepage) der Änderungen, um die Änderungen zu überprüfen.

### Vorschau der konfigurierten Startseite {#preview-configured-homepage}

Sie können eine Vorschau anzeigen, um das Layout und die Formatierung der Startseite für die erste Suche zu überprüfen. Mithilfe der **[!UICONTROL Vorschau]** können Sie das Layout korrigieren oder Änderungen entsprechend Ihres Bedarfs vornehmen. Gehen Sie wie folgt vor, um eine Vorschau der konfigurierten Startseite anzuzeigen:

1. Klicken Sie auf **[!UICONTROL Allgemeine Einstellungen]** und wähle Sie **[!UICONTROL Erste Suche]**.
1. Navigieren Sie zu **[!UICONTROL Startseite für erste Suche anpassen]** und klicken Sie auf **[!UICONTROL Vorschau]**. Schalten Sie mit der Schaltfläche **[!UICONTROL Dunkles Thema]** um, um die Startseite mit dunklem oder hellem Thema als Vorschau anzuzeigen.
1. Klicken Sie auf **[!UICONTROL Schließen]**, um den Vorschau-Bildschirm zu schließen. 

   ![Vorschau der Startseite für die erste Suche](/help/assets/assets/search-first-preview.gif)

## Kontextsuche {#contextual-search}

Sie können auch im Repository verfügbare Assets durchsuchen, indem Sie Text-Prompts definieren. Experience Manager Assets wandelt diese Text-Prompts automatisch in Suchfilter um und zeigt die Suchergebnisse an. Im Bereich „Filter“ können Sie automatische Filter anzeigen und ändern, um die Suchergebnisse weiter einzugrenzen.

### Zugriff auf die Kontextsuche {#access-contextual-search}

So greifen Sie auf die Kontextsuche in Experience Manager Assets zu:

1. Klicken Sie im linken Bereich auf **[!UICONTROL Suchen]**.

   ![Kontextsuche](assets/access-contextual-search.png)

1. Definieren Sie im Textfeld „Suchen“ das Text-Prompt und klicken Sie auf **[!UICONTROL Kontextsuche]**.

   ![Text-Prompt für die Kontextsuche](/help/assets/assets/wknd-contextual-search.png)

   [!DNL Experience Manager Assets] zeigt die Suchergebnisse an.

### Unterstützte Filter {#supported-filters}

Die Kontextsuche unterstützt standardmäßig die folgenden Filter. Stützen Sie Ihr Text-Prompt auf diese Filter, um entsprechende Suchergebnisse anzuzeigen.

* Bildhöhe

* Bildbreite

* Dateityp: Bild, Dokument, Video oder Ordner.

* MIME-Typ: JPG, PNG, TIFF, GIF, MP4, PDF, PPTX, DOCX oder XLSX

* Erstellungsdatum

* Änderungsdatum

* Ablaufdatum

* Asset-Status: „Genehmigt“, „Abgelehnt“ oder alle

* Abgelaufene Assets

### Beispiele für die Text-Prompts {#text-prompts-examples}

**Beispiel 1**

**Text-Prompt**: In diesem Monat erstellte Bilder.

[!DNL Experience Manager Assets] wendet die folgenden Filter automatisch an und zeigt die Suchergebnisse an:

![Beispiel 1 für eine Kontextsuche](assets/contextual-search-example1.png)

**Beispiel 2**

**Text-Prompt**: Bilder, die mindestens 200 px hoch und 100 px breit sind und Strand und klaren Himmel zeigen.

[!DNL Experience Manager Assets] wendet die folgenden Filter automatisch an und zeigt die Suchergebnisse an:

![Beispiel 2 für eine Kontextsuche](assets/contextual-search-example2.png)

**Beispiel 3**

**Text-Prompt**: Ich benötige Bilder von blauem Himmel mit einer Höhe von 1500 und 2500 Pixel, die im letzten Monat erstellt wurden und genehmigt und noch nicht abgelaufen sind.

[!DNL Experience Manager Assets] wendet die folgenden Filter automatisch an und zeigt die Suchergebnisse an:

![Beispiel 3 für eine Kontextsuche](assets/contextual-search-example3.png)

Das folgende Video zeigt den gesamten Vorgang vom Zugriff auf die Benutzeroberfläche für die Kontextsuche über das Definieren des Text-Prompts bis zum Anzeigen der Suchergebnisse.

>[!VIDEO](https://video.tv.adobe.com/v/3428407)

### Deaktivieren der Kontextsuche {#disable-contextual-search}

Admins haben auch die Möglichkeit, die Kontextsuche für Benutzende in ihrer Organisation zu deaktivieren. Führen Sie dazu die folgenden Schritte aus:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.

1. Deaktivieren Sie im Bereich [!UICONTROL Kontextsuche] den Umschalter für **[!UICONTROL Kontextsuche für Ihre Organisation aktivieren]**, um die Kontextsuche für alle Benutzenden in Ihrer Organisation zu deaktivieren.

### Feedback zur Kontextsuche {#contextual-search-feedback}

Um Feedback zur Kontextsuche zu geben, klicken Sie auf das Symbol für die ![Kontextsuche](assets/do-not-localize/Smock_Help_18_N.svg) und anschließend auf das Feedback-Symbol. Wählen Sie den Feedback-Typ aus, geben Sie den Betreff und die Beschreibung ein und klicken Sie auf **[!UICONTROL Absenden]**.

![Feedback zur Kontextsuche](assets/contextual-search-feedback.png)

## Nächste Schritte {#next-steps}

* [Sehen Sie sich ein Video zum Suchen von Assets in Assets-Ansicht an](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/using.html?lang=de)

* Geben Sie Produkt-Feedback über die Option [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht

* Geben Sie Feedback zur Dokumentation mithilfe der Option zum [!UICONTROL Bearbeiten der Seite] ![Seite bearbeiten](assets/do-not-localize/edit-page.png) oder zum [!UICONTROL Melden eines Problems] ![GitHub-Ticket erstellen](assets/do-not-localize/github-issue.png) in der rechten Seitenleiste.

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de#support)


