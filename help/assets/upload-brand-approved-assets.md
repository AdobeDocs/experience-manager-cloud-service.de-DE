---
title: Hochladen Ihrer markengenehmigten Assets in [!DNL Content Hub]
description: Erfahren Sie, wie Sie Ihre markengenehmigten Assets in Content Hub hochladen.
role: User
source-git-commit: 92c4cd64503653c5d9248c2c3f6952100b03ff86
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 0%

---


# Hochladen von markengenehmigten Assets in Content Hub {#upload-brand-approved-assets-content-hub}

Administratoren können Assets zur Content Hub entweder aus dem lokalen Dateisystem hinzufügen oder Assets aus OneDrive- oder Dropbox-Datenquellen importieren. Alle Assets werden unabhängig von der Ordnerstruktur in Ihrem lokalen Dateisystem oder den OneDrive- und Dropbox-Datenquellen auf der obersten Ebene in Content Hub angezeigt, um die Suchfunktionen zu verbessern.

Zur weiteren Verbesserung der Asset-Suche bietet Content Hub folgende Möglichkeiten:

* Definieren Sie wichtige Details, die für den Asset-Upload relevant sind, wie Kampagnenname, Suchbegriffe, Kanäle usw.

* Beim erfolgreichen Upload automatisch weitere Eigenschaften für jedes Asset generieren, z. B. Dateigröße, Format, Auflösung und einige andere Eigenschaften.

* Verwenden Sie die künstliche Intelligenz, die durch [Adobe Sensei](https://www.adobe.com/de/sensei.html) , um automatisch relevante Tags auf alle hochgeladenen Assets anzuwenden. Diese Tags, auch Smart-Tags genannt, erhöhen die Content-Geschwindigkeit Ihrer Projekte, indem Sie schnell relevante Assets finden.

Stellen Sie sicher, dass Sie nur Ihre [Markieren genehmigter Assets in Content Hub](/help/assets/approve-assets.md).

![Hochladen von markengenehmigten Assets](assets/upload-brand-approved-assets.png)

## Voraussetzungen {#prerequisites-add-assets}

[Content Hub Asset-Verbraucherbenutzer mit Berechtigungen zum Übermitteln](/help/assets/deploy-content-hub.md#onboard-content-hub-consumer-users-submission-rights) Assets können in Content Hub hochgeladen werden.

## Hinzufügen von Assets zu Content Hub aus dem lokalen Dateisystem {#add-assets-local-file-system}

So fügen Sie Assets zu Content Hub hinzu:

1. Klicks **[!UICONTROL Assets hinzufügen]** , um die **[!UICONTROL Hinzufügen genehmigter Assets]** -Dialogfeld, in dem Sie einen Upload erstellen können.

1. Im **[!UICONTROL Dateien oder Ordner hierher ziehen]** können Sie die Assets aus dem lokalen Dateisystem ziehen oder auf **[!UICONTROL Durchsuchen]** , um manuell Dateien oder Ordner auszuwählen, die im lokalen Dateisystem verfügbar sind. Diese Liste der Dateien, die Teil Ihres Uploads sind, ist als Liste verfügbar.


   Sie können auch mithilfe der Miniaturansichten eine Vorschau ausgewählter Bilder anzeigen und auf das X-Symbol klicken, um ein bestimmtes Bild aus der Liste zu entfernen. Das X-Symbol wird nur angezeigt, wenn Sie den Mauszeiger über den Bildnamen oder die Bildgröße bewegen. Sie können auch auf **[!UICONTROL Alle entfernen]** , um alle Elemente aus Ihrer Upload-Liste zu löschen.

   So schließen Sie den Upload-Prozess ab und aktivieren die **[!UICONTROL Schaltfläche &quot;Hochladen&quot;]** müssen Sie Ihre Assets unter einem Kampagnennamen gruppieren.

   ![Hochladen von Assets in Content Hub](assets/upload-assets-content-hub.png)

1. Definieren Sie den Namen für Ihren Upload mithilfe des **[!UICONTROL Kampagnenname]** -Feld. Sie können einen vorhandenen Namen verwenden oder einen neuen erstellen. Die Content Hub bietet weitere Optionen, während Sie den Namen eingeben. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   Als Best Practice empfiehlt Adobe, Werte im Rest der Felder anzugeben und eine erweiterte Sucherfahrung für Ihre hochgeladenen Assets zu erstellen.

1. Definieren Sie auf ähnliche Weise Werte für die **[!UICONTROL Schlüsselwörter]**, **[!UICONTROL Kanäle]**, **[!UICONTROL Zeitrahmen]**, und **[!UICONTROL Region]** -Felder. Durch das Tagging und Gruppieren von Assets nach Keywords, Kanälen und Standorten können alle Benutzer, die Ihre genehmigten Unternehmensinhalte verwenden, diese Assets suchen und organisieren.

1. Klicks **[!UICONTROL Hochladen]** , um Assets in die Content Hub hochzuladen. [!UICONTROL Details überprüfen] Bestätigungsfeld angezeigt. Klicken Sie auf [!UICONTROL Weiter].

1. Assets beginnt mit dem Hochladen. Klicks [!UICONTROL Neuer Upload] , um den Upload-Vorgang neu zu starten. Klicks [!UICONTROL Fertig] , um den Upload abzuschließen.

Administratoren können auch die obligatorischen und optionalen Felder konfigurieren, die beim Hochladen von Assets angezeigt werden, z. B. Kampagnenname, Keywords, Kanäle usw. Weitere Informationen finden Sie unter [Konfigurieren der Content Hub-Benutzeroberfläche](configure-content-hub-ui-options.md#configure-upload-options-content-hub).


## Hinzufügen von Assets zu Content Hub aus OneDrive- oder Dropbox-Datenquellen {#add-assets-onedrive-dropbox}

So fügen Sie Assets aus OneDrive- oder Dropbox-Datenquellen zu Content Hub hinzu:

1. Klicks **[!UICONTROL Assets hinzufügen]** , um die **[!UICONTROL Hinzufügen genehmigter Assets]** -Dialogfeld, über das Sie Assets von OneDrive oder Dropbox importieren können.

1. Klicks **[!UICONTROL OneDrive]** oder **[!UICONTROL Dropbox]** um den Importvorgang zu starten. Content Hub fordert Sie auf, sich bei Ihrem OneDrive- oder Dropbox-Konto anzumelden und zeigt dann Ihre OneDrive- oder Dropbox-Ordnerstruktur im linken Bereich an.

1. Klicken Sie auf das Symbol + neben der Datei oder dem Ordnernamen, um das Element in der Liste der ausgewählten Elemente anzuzeigen. Nachdem Sie alle Dateien ausgewählt haben, die Sie zum Content Hub-Portal hinzufügen müssen, wiederholen Sie die Schritte 3 bis 6 von [Hinzufügen von Assets zu Content Hub aus dem lokalen Dateisystem](#add-assets-local-file-system) , um den Upload-Prozess abzuschließen.

   ![Hochladen von Assets von OneDrive oder Dropbox in Content Hub](assets/add-assets-onedrive-dropbox.png)

Administratoren können auch die obligatorischen und optionalen Felder konfigurieren, die beim Hochladen von Assets angezeigt werden, z. B. Kampagnenname, Keywords, Kanäle usw. Weitere Informationen finden Sie unter [Konfigurieren der Content Hub-Benutzeroberfläche](configure-content-hub-ui-options.md#configure-upload-options-content-hub).

