---
title: Bearbeiten von Bildern in Content Hub mit Adobe Express
description: Bearbeiten von Bildern in Content Hub mit Adobe Express
exl-id: c9777862-226c-4d39-87da-9c4a30437dc5
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 93%

---

# Bearbeiten von Bildern in Content Hub {#edit-images-content-hub}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

![Bearbeiten von Bildern in Content Hub mit Adobe Express](assets/edit-images-content-hub.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub-Handbuch als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Mit Content Hub können Sie neue Inhalte mit Adobe Express erstellen. Sie können vorhandene Inhalte mit anwenderfreundlichen Tools bearbeiten, Markenvarianten mit Vorlagen und Markenelementen erstellen und neue Inhalte mit den neuesten GenAI-Funktionen von Adobe Firefly erstellen.

## Voraussetzungen {#prereqs-edit-image-content-hub}

Es sind Berechtigungen für den Zugriff auf Adobe Express vorhanden und [Content Hub-Benutzende mit Berechtigungen zum Remixen von Assets in neue Varianten](/help/assets/deploy-content-hub.md#onboard-content-hub-users-remix-assets) können Bilder mit Content Hub bearbeiten.

>[!NOTE]
>
>Sie können mit [!DNL Adobe Express] Bilder vom Dateityp PNG und JPG/JPEG bearbeiten.

## Bearbeiten von Bildern mit [!DNL Adobe Express] {#edit-images-using-content-hub}

So bearbeiten Sie Bilder mit Content Hub:

1. Klicken Sie auf der Asset-Karte des Bildes, das bearbeitet werden soll, auf **[!DNL Open in Adobe Express]**. Alternativ können Sie erst auf das Bild klicken, um dessen Details zu öffnen, und dann auf das [!DNL Adobe Express]-Logo. Der eingebettete Editor für Adobe Express wird anschließend geladen, ohne Content Hub verlassen zu müssen.

   Sie können die Funktionen von [!DNL Adobe Express] zum Ausführen aller Bildbearbeitungsaktionen nutzen, wie z. B. [Bildgröße ändern](https://helpx.adobe.com/de/express/using/resize-image.html), [Hintergrundfarbe entfernen oder ändern](https://helpx.adobe.com/de/express/using/remove-background.html), [Bild zuschneiden](https://helpx.adobe.com/de/express/using/crop-image.html), das Bild mit einem KI-generierten Bild oder Text kombinieren und vieles mehr.

1. Führen Sie Ihre Änderungen durch und klicken Sie auf **[!UICONTROL Speichern]**, um das bearbeitete Asset in einem der folgenden Formattypen zu speichern:

   * **[!UICONTROL PNG]** (als Bildformat guter Qualität)
   * **[!UICONTROL JPG]** (geeignet für kleine Dateien)
   * **[!UICONTROL PDF]** (geeignet für Dokumente)

   ![Speichern des Bildes mit Adobe Express](assets/adobe-express-save-as.png)

1. Geben Sie einen Namen für das Asset im Feld **[!UICONTROL Speichern unter]** an.

1. Geben Sie den Kampagnennamen für Ihr Asset im Feld **[!UICONTROL Kampagnenname]** an. Sie können einen vorhandenen Namen verwenden oder einen neuen erstellen. Content Hub bietet weitere Optionen, wenn Sie den Namen eingeben. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   Adobe empfiehlt als Best Practice, in den restlichen Feldern ebenfalls Werte anzugeben, da hierdurch ein verbessertes Sucherlebnis für Ihre hochgeladenen Assets geschaffen wird.

1. [Optional] Definieren Sie Werte für die Felder **[!UICONTROL Keywords]**, **[!UICONTROL Kanäle]**, **[!UICONTROL Zeitraum]** und **[!UICONTROL Region]**. Durch das Tagging und Gruppieren von Assets nach Keywords, Kanälen und Speicherorten kann jede Person, die Ihre genehmigten Unternehmensinhalte verwendet, nach diesen Assets suchen und sie organisieren.

1. Klicken Sie auf **[!UICONTROL Als neues Asset speichern]**, um das Asset zu speichern.

Admins können auch die obligatorischen und optionalen Felder konfigurieren, die beim Hinzufügen von Assets zu Content Hub angezeigt werden, z. B. Kampagnenname, Keywords, Kanäle usw. Weitere Informationen finden Sie unter [Konfigurieren der Benutzeroberfläche von Content Hub](configure-content-hub-ui-options.md#configure-upload-options-content-hub).
