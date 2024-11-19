---
title: Hochladen der von Ihrer Marke genehmigten Assets in  [!DNL Content Hub]
description: Erfahren Sie, wie Sie Ihre markengenehmigten Assets in Content Hub hochladen.
role: User
exl-id: f1be7cfc-1803-4c17-bb58-947104aa883c
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 7%

---

# Hochladen von markenkonformen Assets in Content Hub {#upload-brand-approved-assets-content-hub}

>[!CONTEXTUALHELP]
>id="upload_assets_content_hub"
>title="Hochladen von markenkonformen Assets in Content Hub"
>abstract="Fügen Sie genehmigte Assets entweder aus dem lokalen Dateisystem zu Content Hub hinzu oder importieren Sie Assets aus OneDrive- oder Dropbox-Datenquellen. Alle Assets werden unabhängig von der Ordnerstruktur auf der obersten Ebene in Content Hub angezeigt, um die Suchfunktionen zu verbessern."

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub Guide PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

[Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) können Assets zur Content Hub entweder aus dem lokalen Dateisystem hinzufügen oder Assets aus OneDrive- oder Dropbox-Datenquellen importieren. Alle Assets werden unabhängig von der Ordnerstruktur in Ihrem lokalen Dateisystem oder den OneDrive- und Dropbox-Datenquellen auf der obersten Ebene in Content Hub angezeigt, um die Suchfunktionen zu verbessern.

Die Assets, die in Assets as a Cloud Service als `Approved` markiert sind, sind automatisch in Content Hub verfügbar. Weitere Informationen finden Sie unter [Genehmigen von Assets für Content Hub](/help/assets/approve-assets-content-hub.md).

Zur weiteren Verbesserung der Asset-Suche bietet Content Hub folgende Möglichkeiten:

* Definieren Sie wichtige Details, die für den Asset-Upload relevant sind, wie Kampagnenname, Suchbegriffe, Kanäle usw.

* Beim erfolgreichen Upload automatisch weitere Eigenschaften für jedes Asset generieren, z. B. Dateigröße, Format, Auflösung und einige andere Eigenschaften.

* Verwenden Sie die künstliche Intelligenz von [Adobe Sensei](https://www.adobe.com/de/sensei.html), um automatisch relevante Tags auf alle hochgeladenen Assets anzuwenden. Diese Tags, auch Smart-Tags genannt, erhöhen die Content-Geschwindigkeit Ihrer Projekte, indem Sie schnell relevante Assets finden.

Stellen Sie sicher, dass Sie nur die von Ihrer Marke [genehmigten Assets in die Content Hub](/help/assets/approve-assets.md) hochladen.

![Hochladen von markengenehmigten Assets](assets/upload-brand-approved-assets.png)

## Voraussetzungen {#prerequisites-add-assets}

[Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) können Assets in Content Hub hochladen.

## Hinzufügen von Assets zu Content Hub aus dem lokalen Dateisystem {#add-assets-local-file-system}

So fügen Sie Assets zu Content Hub hinzu:

1. Klicken Sie auf **[!UICONTROL Assets hinzufügen]** , um das Dialogfeld **[!UICONTROL Genehmigte Assets hinzufügen]** anzuzeigen, mit dem Sie einen Upload erstellen können.

1. Im Abschnitt &quot;**[!UICONTROL Dateien oder Ordner hierher ziehen&quot;]** im rechten Bereich können Sie die Assets entweder aus dem lokalen Dateisystem ziehen oder auf &quot;**[!UICONTROL Durchsuchen]**&quot; klicken, um die im lokalen Dateisystem verfügbaren Dateien oder Ordner manuell auszuwählen. Diese Liste der Dateien, die Teil Ihres Uploads sind, ist als Liste verfügbar.


   Sie können auch mithilfe der Miniaturansichten eine Vorschau ausgewählter Bilder anzeigen und auf das X-Symbol klicken, um ein bestimmtes Bild aus der Liste zu entfernen. Das X-Symbol wird nur angezeigt, wenn Sie den Mauszeiger über den Bildnamen oder die Bildgröße bewegen. Sie können auch auf **[!UICONTROL Alle entfernen]** klicken, um alle Elemente aus Ihrer Upload-Liste zu löschen.

   Um den Upload-Prozess abzuschließen und die Schaltfläche **[!UICONTROL Hochladen]** zu aktivieren, müssen Sie Ihre Assets unter einem Kampagnennamen gruppieren.

   ![Hochladen von Assets in Content Hub](assets/upload-assets-content-hub.png)

1. Definieren Sie den Namen für Ihren Upload mithilfe des Felds **[!UICONTROL Kampagnenname]** . Sie können einen vorhandenen Namen verwenden oder einen neuen erstellen. Die Content Hub bietet weitere Optionen, während Sie den Namen eingeben. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   Als Best Practice empfiehlt Adobe, Werte im Rest der Felder anzugeben und eine erweiterte Sucherfahrung für Ihre hochgeladenen Assets zu erstellen.

1. Definieren Sie auf ähnliche Weise Werte für die Felder **[!UICONTROL Keywords]**, **[!UICONTROL Kanäle]**, **[!UICONTROL Timeframe]** und **[!UICONTROL Region]** . Durch das Tagging und Gruppieren von Assets nach Keywords, Kanälen und Standorten können alle Benutzer, die Ihre genehmigten Unternehmensinhalte verwenden, diese Assets suchen und organisieren.

1. Klicken Sie auf **[!UICONTROL Hochladen]** , um Assets in die Content Hub hochzuladen. [!UICONTROL Überprüfungsdetails] wird das Bestätigungsfeld angezeigt. Klicken Sie auf [!UICONTROL Weiter].

1. Assets beginnt mit dem Hochladen. Klicken Sie auf [!UICONTROL Neu hochladen] , um den Upload-Vorgang neu zu starten. Klicken Sie auf [!UICONTROL Fertig] , um den Upload abzuschließen.

Administratoren können auch die obligatorischen und optionalen Felder konfigurieren, die beim Hochladen von Assets angezeigt werden, z. B. Kampagnenname, Keywords, Kanäle usw. Weitere Informationen finden Sie unter [Konfigurieren der Content Hub-Benutzeroberfläche](configure-content-hub-ui-options.md#configure-upload-options-content-hub).


## Hinzufügen von Assets zu Content Hub aus OneDrive- oder Dropbox-Datenquellen {#add-assets-onedrive-dropbox}

So fügen Sie Assets aus OneDrive- oder Dropbox-Datenquellen zu Content Hub hinzu:

1. Klicken Sie auf **[!UICONTROL Assets hinzufügen]** , um das Dialogfeld **[!UICONTROL Genehmigte Assets hinzufügen]** anzuzeigen, in dem Sie Assets von OneDrive oder Dropbox importieren können.

1. Klicken Sie auf **[!UICONTROL OneDrive]** oder **[!UICONTROL Dropbox]** , um den Importprozess zu starten. Content Hub fordert Sie auf, sich bei Ihrem OneDrive- oder Dropbox-Konto anzumelden und zeigt dann Ihre OneDrive- oder Dropbox-Ordnerstruktur im linken Bereich an.

1. Klicken Sie auf das Symbol + neben der Datei oder dem Ordnernamen, um das Element in der Liste der ausgewählten Elemente anzuzeigen. Nachdem Sie alle Dateien ausgewählt haben, die Sie zum Content Hub-Portal hinzufügen müssen, wiederholen Sie die Schritte 3 bis 6 von [Assets aus dem lokalen Dateisystem zu Content Hub hinzufügen](#add-assets-local-file-system) , um den Upload-Vorgang abzuschließen.

   ![Hochladen von Assets von OneDrive oder Dropbox](assets/add-assets-onedrive-dropbox.png) in Content Hub

Administratoren können auch die obligatorischen und optionalen Felder konfigurieren, die beim Hochladen von Assets angezeigt werden, z. B. Kampagnenname, Keywords, Kanäle usw. Weitere Informationen finden Sie unter [Konfigurieren der Content Hub-Benutzeroberfläche](configure-content-hub-ui-options.md#configure-upload-options-content-hub).

## Verwalten von mit Content Hub hochgeladenen Assets {#manage-assets-uploaded-using-content-hub}

[Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) können [Assets zur Content Hub](/help/assets/upload-brand-approved-assets.md) hinzufügen, entweder aus dem lokalen Dateisystem oder Assets aus OneDrive- oder Dropbox-Datenquellen importieren. Alle Assets werden unabhängig von der Ordnerstruktur in Ihrem lokalen Dateisystem oder den OneDrive- und Dropbox-Datenquellen auf der obersten Ebene in Content Hub angezeigt, um die Suchfunktionen zu verbessern.

Die Anzeige von Assets, die mit Content Hub hochgeladen wurden, hängt davon ab, ob Sie [den Umschalter für die automatische Genehmigung aktiviert haben](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub):

* Wenn der Umschalter **[!UICONTROL Automatische Genehmigung]** aktiviert ist, sind die Assets, die Sie mit Content Hub hochladen, automatisch verfügbar.

* Wenn der Umschalter **[!UICONTROL Automatische Genehmigung]** deaktiviert ist, werden die Assets, die Sie mit Content Hub hochladen, nicht automatisch angezeigt. Die Assets sind im Ordner &quot;`hydrated-assets`&quot;Ihrer Assets as a Cloud Service-Umgebung verfügbar. Navigieren Sie zum Ordner und bearbeiten Sie [stapelweise](#bulk-approve-assets-content-hub) den Status dieser Assets in `Approved` , damit diese Assets in Content Hub angezeigt werden.

![Content Hub-Genehmigungsprozess](/help/assets/assets/content-hub-approval.png)
