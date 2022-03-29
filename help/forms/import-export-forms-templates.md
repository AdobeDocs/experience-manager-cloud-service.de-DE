---
title: Importieren, Exportieren und Organisieren von adaptiven Formularen, PDF-Formularen und anderen Assets
seo-title: Learn to import, export, and organize Adaptive Forms, PDF forms, and other assets on an[!DNL AEM Forms] instance
description: 'Sie möchten adaptive Formulare und Assets in und von einer AEM-Instanz migrieren? Hier erfahren Sie, wie Sie adaptive Formulare, PDF-Formulare, Designs und andere unterstützende Assets aus einer  [!DNL AEM Forms] -Instanz importieren und exportieren. '
seo-description: Looking to migrate Adaptive Forms and assets to and from an AEM instances? Learn here how to import and export Adaptive Forms, PDF forms, themes, and other supporting assets from an [!DNL AEM Forms] instance.
topic-tags: forms-manager
exl-id: f5105fb7-b8c0-4656-8095-b21d392746c0
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 100%

---

# Importieren, Exportieren und Organisieren von adaptiven Formularen, PDF-Formularen und anderen Assets{#importing-and-exporting-assets-to-aem-forms}

Sie können adaptive Formulare und zugehörige Assets wie Designs für adaptive Formulare, Formulardatenmodelle, Vorlagen für adaptive Formulare, Dokumentfragmente und PDF-Formulare zwischen einzelnen [!DNL AEM Forms]-Instanzen verschieben. Sie können Assets in CRX-Paket- oder binäre Dateiformate importieren und exportieren.

Wenn Sie ein adaptives Formular exportieren, werden die Content-Richtlinien und Vorlagen nicht exportiert. Verwenden Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de#how-rolling-deployments-work), um diese Assets zu exportieren.

## Herunterladen von adaptiven Formularen, PDF-Formularen oder zugehörigen Assets {#download-forms-amp-documents-assets}

So laden Sie Formulare oder zugehörige Assets herunter:

1. Melden Sie sich bei der [!DNL AEM Forms]-Instanz an.
1. Tippen Sie auf das Symbol **[!UICONTROL Adobe Experience Manager]** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol **[!UICONTROL Navigation]** ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie die Assets und klicken Sie auf das Symbol **[!UICONTROL Herunterladen]**.
1. Wählen Sie unter „Asset(s) herunterladen“ eine der folgenden Optionen und tippen Sie auf **[!UICONTROL Herunterladen]**.

   * **Als CRX-Paket herunterladen:** Verwenden Sie die Option zum Herunterladen und Verschieben aller ausgewählten Assets und der zugehörigen Abhängigkeiten von einer [!DNL AEM Forms]-Instanz in eine andere. Es werden alle Assets und Ordner als CRX-Paket heruntergeladen, einschließlich der in AEM erstellten Formulare (adaptive Formulare und adaptive Formularfragmente), Formularsätze, Formulardatenmodelle, Formularvorlagen, PDF-Dokumente und referenzierten Ressourcen (XSDs und Bilder).
Der Vorteil des Herunterladens von Assets als Paket besteht darin, dass auch referenzierte Assets mit heruntergeladen werden. Beispiel: Sie haben ein adaptives Formular, das eine Formularvorlage, XSD und ein Bild verwendet. Wenn Sie dieses adaptive Formular auswählen und es als Paket herunterladen, enthält das heruntergeladene Paket auch die Formularvorlage, XSD und das Bild. Alle mit dem Asset verknüpften Metadateneigenschaften (einschließlich benutzerdefinierter Eigenschaften) werden ebenfalls heruntergeladen.

   * **Asset(s) als Binärdateien herunterladen:** Verwenden Sie die Option nur zum Herunterladen von Formularvorlagen (XDP), PDF-Formularen (PDF), Dokumenten (PDF) und Ressourcen (Bilder, Schemas, Stylesheets). Sie können diese Assets mit externen Anwendungen bearbeiten. Assets, die Binärdateien wie Bilder, PDFs und andere unterstützte Formate enthalten, werden als .zip-Datei heruntergeladen.
Sie können keine adaptiven Formulare, adaptiven Formularfragmente, Designs und Formularsätze mit der Option **[!UICONTROL Asset(s) als Binärdateien herunterladen]** herunterladen. Um diese Assets herunterzuladen, müssen Sie die Option **[!UICONTROL Als CRX-Paket herunterladen]** verwenden.

   Die ausgewählten Assets werden als ein Archiv (.zip-Datei) heruntergeladen.

   >[!NOTE]
   >
   >Das AEM-Paket und die Binärdateien werden als ein Archiv (.zip-Datei) heruntergeladen. Die Vorlagen für die Assets werden nicht zusammen mit den Assets heruntergeladen. Sie müssen die Asset-Vorlagen separat exportieren.

## Hochladen von adaptiven Formularen, PDF-Formularen oder zugehörigen Assets {#upload-forms-amp-documents-assets}

Sie können die unterstützten Assettypen einzeln oder als ZIP-Archiv hochladen. Bei einer ZIP-Datei werden die relativen Pfade aller unterstützten Assets angezeigt. Nicht unterstützte Assets in der ZIP-Datei werden ignoriert und nicht aufgelistet. Wenn das ZIP-Archiv jedoch nur die nicht unterstützten Assets enthält, wird anstelle des Popup-Dialogfensters eine Fehlermeldung angezeigt.
So laden Sie ein Formular oder ein referenziertes Asset hoch:

1. Melden Sie sich bei der [!DNL AEM Forms]-Instanz an.
1. Tippen Sie auf das Symbol **[!UICONTROL Adobe Experience Manager]** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol **[!UICONTROL Navigation]** ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]**. Das folgende Dialogfeld wird angezeigt.
1. Navigieren Sie im Dialogfeld zum Paket oder Archiv, das importiert werden soll, und wählen Sie es aus. Sie können auch andere unterstützte Dateitypen auswählen. Tippen Sie auf **[!UICONTROL Öffnen]**. Der ausgewählte Ordner- oder Dateiname darf keine Sonderzeichen enthalten.

   Überprüfen Sie im Dialogfeld die Details der Assets, die hochgeladen werden, und tippen Sie auf **[!UICONTROL Hochladen]**.

   Wenn Sie ein vorhandenes Formular-Asset hochladen, wird das Asset aktualisiert.

   >[!NOTE]
   >
   > * Bei Namenskonflikten mit unterschiedlichen Ressourcentypen wird beim Hochladen eines Pakets die vorhandene Ordnerhierarchie nicht ersetzt. Beispiel: Angenommen, Sie haben ein adaptives Formular mit dem Namen „Training“ am Speicherort /content/dam/formsanddocuments auf einem Server gespeichert. Sie laden das adaptive Formular herunter und laden es auf einen anderen Server hoch. Der zweite Server hat ebenfalls einen Ordner „Training“ am selben Speicherort /content/dam/formsanddocuments. Der Hochladevorgang schlägt fehl.
   > * Nur ein Mitglied der Gruppe `form-power-user` kann XDP-Dateien hochladen.



## Herunterladen eines Designs {#downloading-a-theme}

Sie können Designs in [!DNL AEM Forms] exportieren und in anderen Projekten oder Instanzen verwenden. Mit AEM können Sie Designs als ZIP-Datei herunterladen, um diese in die Instanz hochzuladen.

Herunterladen von Designs

1. Melden Sie sich bei der [!DNL AEM Forms]-Instanz an.
1. Tippen Sie auf das Symbol **[!UICONTROL Adobe Experience Manager]** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol **[!UICONTROL Navigation]** ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulare]** > **[!UICONTROL Designs]**.
1. Wählen Sie das Design und tippen Sie auf **[!UICONTROL Herunterladen]**. Das Design wird als ein Archiv (.zip-Datei) heruntergeladen.

## Hochladen eines Designs {#uploading-a-theme}

Sie können Designs hochladen und verwenden, die andere in Ihren Formularen erstellen. Hochladen von Designs

1. In Experience Manager navigieren Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Designs]**.
1. Auf der Seite „Designs“ klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]**.
1. In der Eingabeaufforderung zur Dateiaktualisierung suchen Sie ein Designpaket auf Ihrem Computer, wählen es aus und klicken auf **[!UICONTROL Hochladen]**. Das hochgeladene Thema ist nun auf der Seite „Designs“ verfügbar.

<!-- ## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

To share assets, such as data dictionaries, letters, and document fragments, between two different implementations of Correspondence Management, you can create and share .cmp files. A .cmp file can include one or more data dictionaries, letters, document fragments, and forms.

### Export Document Fragments, Letters, and/or Data Dictionaries {#export-document-fragments-letters-and-or-data-dictionaries}

1. In the letters, document fragments, or data dictionary pages, tap and select the assets you want to export to a single package, and then tap Queue For Download. The assets are lined-up for export.
1. As required, repeat the above step to add letters, document fragments, and data dictionaries.
1. Tap **Download**.
1. Correspondence Management displays Download Asset(s) dialog with a list of assets in the export list.

   ![export](assets/export.png)

1. To view the dependencies that are exported, Tap Resolve. Or skip to the next step. Even if you do not tap resolve, the dependencies are still exported.
1. To download the .cmp file, tap **OK**.
1. Correspondence Management downloads a .cmp file to your computer.

   The .cmp file includes the exported assets. You can share the .cmp file with others. Other users can import the .cmp file in a different server to get all the assets in the new server.

### Export all the Correspondence Management assets as a package {#export-all-the-correspondence-management-assets-as-a-package}

Use this option to download all the Correspondence Management assets and related dependencies as a package from an [!DNL AEM Forms] instance.

For example, if Correspondence Management has a letter that uses an image and text, the downloaded package also contains the image and the text related to the letter. All the metadata properties (including custom properties) associated with the asset are also downloaded. Once you have downloaded the package (.cmp), you can [import the package to a different [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

To download all the Correspondence Management assets and related dependencies as a package, complete the following steps:

1. Log in to [!DNL AEM Forms] server as a forms user.
1. Tap **Adobe Experience Manager** in the Global Navigation bar.
1. Tap tools ( ![tools](assets/tools.png)) and then tap **Forms**.
1. Tap **Export Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``The Export All Correspondence Management Assets page appears and displays the information about the last time the Export process was attempted and a link to download the last successfully exported package.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Tap **Export** and, in the confirm message, tap **OK**.

   After a batch process is complete, the last run details and the link to download the package are updated. This includes information such as the Administrator login and if the batch run successfully or failed. The assets are exported to a package and the Download Exported Package link appears.

   >[!NOTE]
   >
   >The Export All Assets process cannot be canceled once initiated. Also, while the export all operation is in process, do not create, delete, modify, or publish any assets or initiate Publish All Assets process.a

1. Tap the **Download Exported Package** link to download the package file.

   To add the assets in the package to another instance of Correspondence Management, [import the package to an [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

<!-- ### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

You can import assets that are exported into a .cmp file. A .cmp file can have one or more letters, data dictionaries, document fragments, and dependent assets.

>[!NOTE]
>
>While importing old Correspondence Management assets for migration, log in using an Admin account. For more information on Migrating old Correspondence Management assets, see [Migrate Correspondence Management assets to AEM 6.1 forms](migration-utility.md).

1. On the data dictionary, letters, or document fragments page, tap **Create &gt; File Upload** and select the .cmp file.
1. Correspondence Management displays the Import Assets dialog with the list of assets that are imported. Tap **Import**.

   After importing the assets, the following properties of the assets are updated while the other properties remain the same:

    * Author: Displays the ID of the user that imported the asset to the server
    * Modified: The time when the asset was imported to the server

   >[!NOTE]
   >
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator. -->

## Exportieren eines Workflow-Programms {#export-a-workflow-application}

Sie können AEM Package Manager verwenden, um Workflow-Programme zu exportieren. Das Verfahren wird unten aufgeführt:

1. Öffnen Sie den [!DNL AEM Forms]-Paket-Manager. Die URL des Package Manager lautet `https://[server]:[port]/crx/packmgr`.
1. Klicken Sie auf **[!UICONTROL Paket erstellen]**. Das Dialogfeld **[!UICONTROL Neues Paket]** wird angezeigt.
1. Geben Sie Name, Version und Gruppe für das Paket an. Klicken Sie auf **[!UICONTROL OK]**.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]** und öffnen Sie die Registerkarte **[!UICONTROL Filter]**. Klicken Sie auf **[!UICONTROL Filter hinzufügen]**. Geben Sie den Pfad der Workflow-Anwendung ein. Beispiel: /etc/fd/dashboard/startpoints/homemortgage. Klicken Sie auf **[!UICONTROL Regel hinzufügen]**.

1. Öffnen Sie die Registerkarte **[!UICONTROL Erweitert]**. Wählen Sie **[!UICONTROL Zusammenführen]** oder **[!UICONTROL Überschreiben]** im Feld „ACL-Bearbeitung“. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um das Paket zu erstellen.

   Nachdem das Paket erstellt wurde, können Sie es herunterladen und auf den anderen Server importieren. Der Arbeitsablauf wird auf dem Server, auf dem das Paket hochgeladen wird, angezeigt.

   >[!NOTE]
   >
   >Damit das Workflow-Programm korrekt funktioniert, exportieren Sie auch das entsprechende adaptive Formular und Workflow-Modell mit dem Arbeitsablaufprogramm.

## Organisieren von adaptiven Formularen, PDF-Formularen und zugehörigen Assets mithilfe von Ordnern   {#folders-and-organizing-assets}

Sie können Ordner verwenden, um Assets zu gruppieren und zu organisieren. Wenn Sie Dokumente und Assets in einem Ordner organisieren, können Sie die Dateien gruppieren und somit die Verwaltung vereinfachen. Sie können einen Ordner auswählen und ihn herunterladen oder löschen. Um einen Ordner zu erstellen, führen Sie die folgenden Schritte aus:

### Erstellen von Ordnern {#create-a-folder}

1. Melden Sie sich bei der [!DNL AEM Forms]-Instanz an.
1. Tippen Sie auf das Symbol „Experience Manager“ ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol „Navigation“ ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Ordner]**.
1. Geben Sie die folgenden Details ein:

   * **[!UICONTROL Titel]**: Der Anzeigename für den Ordner
   * **[!UICONTROL Name]**: *(obligatorisch)* Der Knotenname, unter dem Sie den Ordner im Repository speichern möchten

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des Namensfelds automatisch mit dem Titel ausgefüllt. Der Name darf nur alphanumerische Zeichen oder die Sonderzeichen Bindestrich (-) und Unterstrich (_) enthalten. Andere Sonderzeichen, die in den Titel eingegeben wurden, werden automatisch durch einen Bindestrich ersetzt und Sie werden aufgefordert, den neuen Namen zu bestätigen. Sie können den vorgeschlagenen Namen verwenden oder ihn weiter bearbeiten.

1. Ein neuer Ordner mit dem definierten Titel wird an der aktuellen Position in der Asset-Liste angezeigt.

   Wenn ein Ordner mit dem angegebenen Namen vorhanden ist, schlägt das Senden mit einem Fehler fehl. Sie können die Fehlermeldung anzeigen, indem Sie die Maus über das Fehlersymbol ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) bewegen, das neben dem Namensfeld angezeigt wird.

   Sie können auf den neu erstellten Ordner tippen, um innerhalb des Ordners zu navigieren und Assets oder Ordner innerhalb des Ordners zu erstellen. Außerdem können Sie einen Ordner auswählen und ihn für den Download in die Warteschlange stellen, ihn löschen oder seinen Namen bearbeiten.


<!-- ### Create copies of one or more assets or letters {#create-copies-of-one-or-more-assets-or-letters}

You can use an existing assets to quickly create an asset with similar properties, content, and inherited assets.

Complete the following steps to create copies of assets and letters:

1. On the relevant assets page, select one or more assets. The UI displays the Copy icon.
1. Tap **[!UICONTROL Copy]**. The UI displays the **[!UICONTROL Paste]** icon. You can also choose to go/navigate inside a folder before you paste. Different folders can contain assets with same names. For more information on folders, see [Folders and organizing assets](#folders-and-organizing-assets).
1. Tap **[!UICONTROL Paste]**. The **[!UICONTROL Paste]** dialog appears. The system auto generates names and titles to the new copies of assets/letters, but you can edit the titles and names of the assets/letters.

   If you are copying and pasting the assets/letters at the same place, a suffix "-CopyXX" gets added to the existing name of the asset/letter. If no title existed for the copied asset/letter, the auto generated title field remains blank.

1. If required, edit the Title and Name with which you want to save the copy of the asset/letter.
1. Tap **[!UICONTROL Paste]**. New copies of the copied assets are created.

## Search {#search-forms}

You ca use the top bar **[A]** to search your content. When you search for assets, a side panel is displayed. You can also tap ![assets-browser-content-only](assets/assets-browser-content-only.png) &gt; Filter **[B]** to invoke the side panel. Using the various filters in the side panel, you can narrow down your search. The side panel also allows you to save your searches.

![search_topbar](assets/search_topbar.png)

**A.** Search **B.** Filter

![Side panel - Filters](assets/search_sidepanel.png)

Side panel - Filters

On the side panel, you can use the following to narrow down your search results:

* Search Directory
* Tags
* Search Criteria; for example, Modified Dates, Publish Status, LiveCopy Status.

The side panel also allows you to save your search settings with names of your choice.

For more information and instructions on using search, filters, saved search, and side panel, see [Search](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html). -->
