---
title: 'Importieren und Exportieren von Assets '
seo-title: Import and export assets to [!DNL AEM Forms]
description: Sie können adaptive Formulare und zugehörige Assets in eine AEM-Instanz importieren und exportieren. Dies erleichtert das Integrieren von Formularen oder das Verschieben von Formularen zwischen Systemen.
seo-description: You can import and export Adaptive Forms and templates from and in to AEM instances. This helps in migrating forms or moving them across systems.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1325'
ht-degree: 100%

---


# Importieren und Exportieren von Assets {#importing-and-exporting-assets-to-aem-forms}

Sie können Formulare, Designs, Vorlagen, Dokumentfragmente und andere Assets zwischen verschiedenen [!DNL AEM Forms]-Instanzen verschieben. Ein solches Verschieben ist bei der Migration von Systemen oder beim Verschieben von Formularen von einem Entwicklungs- oder Staging-Server auf einen Produktions-Server erforderlich.

Für die Assets, für die das Hochladen und Importieren über die [!DNL AEM Forms]-Benutzeroberfläche unterstützt wird, ist die Verwendung der Forms-Benutzeroberfläche der empfohlene Weg für den Export oder Import. Die Verwendung von AEM Package Manager zum Exportieren oder Importieren solcher Assets wird nicht empfohlen.

## Download und Upload von Assets für Formulare und Dokumente {#download-or-upload-forms-amp-documents-assets}

Mithilfe der [!DNL AEM Forms]-Benutzeroberfläche können Sie Assets aus einer AEM-Instanz exportieren, indem Sie sie als CRX-Paket oder Binärdateien herunterladen. Sie können dann das heruntergeladene AEM CRX-Paket oder die Binärdatei in eine andere AEM-Instanz importieren.

Der Export und Import über die Benutzeroberfläche von [!DNL AEM Forms] wird für alle Assets mit Ausnahme von adaptiven Formularvorlagen und adaptiven Formularinhaltsrichtlinien unterstützt. Deshalb werden beim Exportieren eines adaptiven Formulars von der [!DNL AEM Forms]-Benutzeroberfläche die verknüpfte adaptive Formularvorlage und die Inhaltsrichtlinien nicht wie andere verknüpfte Assets automatisch exportiert.

Sie müssen AEM Package Manager verwenden, um ein CRX-Paket dieser Elemente auf dem AEM-Quell-Server zu erstellen und das Paket auf dem Ziel-Server zu installieren. Informationen zum Erstellen und Installieren von Paketen finden Sie unter [Bereitstellen in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de).

### Download von Assets für Formulare und Dokumente {#download-forms-amp-documents-assets}

Download von Assets für Formulare und Dokumente

1. Melden Sie sich bei der [!DNL AEM Forms]-Instanz an.
1. Tippen Sie auf das Symbol „Experience Manager“ ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol „Navigation“ ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie die AEM Forms-Assets und klicken Sie auf das Symbol **[!UICONTROL Herunterladen]**.
1. Wählen Sie unter „Asset(s) herunterladen“ eine der folgenden Optionen und tippen Sie auf **[!UICONTROL Herunterladen]**.

   * **Als CRX-Paket herunterladen:** Verwenden Sie die Option zum Herunterladen und Verschieben aller ausgewählten Elemente und der zugehörigen Abhängigkeiten von einer [!DNL AEM Forms]-Instanz in eine andere. Dadurch werden alle Assets und Ordner als CRX-Paket heruntergeladen. Formular-Assets, einschließlich in AEM erstellter Formulare (adaptive Formulare und adaptive Formularfragmente), PDF-Dokumente und Ressourcen (XSDs, XFS, Bilder), können über die [!DNL AEM Forms]-Benutzeroberfläche als Paket heruntergeladen werden.
Der Vorteil des Herunterladens von Assets als Paket besteht darin, dass dabei auch Assets enthalten sind, die von den ausgewählten Assets verwendet wurden. Beispiel: Sie haben ein adaptives Formular, das eine Formularvorlage, XSD und ein Bild verwendet. Wenn Sie dieses adaptive Formular auswählen und es als Paket herunterladen, enthält das heruntergeladene Paket ebenfalls die Formularvorlage, XSD und das Bild. Alle mit dem Asset verknüpften Metadateneigenschaften (einschließlich benutzerdefinierter Eigenschaften) werden ebenfalls heruntergeladen.

   * **Asset(s) als Binärdateien herunterladen:** Verwenden Sie die Option nur zum Herunterladen von Formularvorlagen (XDP), PDF-Formularen (PDF), Dokumenten (PDF) und Ressourcen (Bilder, Schemas, Stylesheets). Sie können diese Assets mit externen Anwendungen bearbeiten. Es werden die Forms-Assets, die Binärdaten enthalten, wie XSDs, XDPs, Bilder, PDFs, und XDPs, als .zip-Datei heruntergeladen.
Das Herunterladen von adaptiven Formulare, adaptiven Formularfragmenten und Designs ist mit der Option **[!UICONTROL Asset(s) als binäre Dateien herunterladen]** nicht möglich. Um diese Assets herunterzuladen, müssen Sie die Option **[!UICONTROL Als CRX-Paket herunterladen]** verwenden.

   Die ausgewählten Assets werden als ein Archiv (.zip-Datei) heruntergeladen.

   >[!NOTE]
   >
   >Das AEM-Paket und die Binärdateien werden als ein Archiv (.zip-Datei) heruntergeladen. Die Vorlagen für die Assets werden nicht zusammen mit den Assets heruntergeladen. Sie müssen die Asset-Vorlagen separat exportieren.

### Upload von Assets {#upload-forms-amp-documents-assets}

Upload von Assets für Formulare und Dokumente

1. Melden Sie sich bei der [!DNL AEM Forms]-Instanz an.
1. Tippen Sie auf das Symbol „Experience Manager“ ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol „Navigation“ ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Tippen Sie auf **Erstellen** > **Datei hochladen**. Ein Dialogfeld zum Hochladen von Formularen oder Paketen wird angezeigt.
1. Navigieren Sie im Dialogfeld zum Paket oder Archiv, das importiert werden soll, und wählen Sie es aus. Sie können außerdem PDF-Dokumente, XSDs, Bilder, Stylesheets und XDP-Formulare auswählen. Tippen Sie auf **[!UICONTROL Öffnen]**. Der ausgewählte Ordner- oder Dateiname darf keine Sonderzeichen enthalten.

   Überprüfen Sie im Dialogfeld die Details der Assets, die hochgeladen werden, und tippen Sie auf **[!UICONTROL Hochladen]**.

   Wenn Sie ein vorhandenes Formular-Asset hochladen, wird das Asset aktualisiert.

   >[!NOTE]
   >
   >Beim Hochladen eines Pakets wird eine vorhandene Ordnerhierarchie nicht ersetzt. Beispiel: Angenommen, Sie haben ein adaptives Formular mit dem Namen „Training“ am Speicherort /content/dam/formsanddocuments auf einem Server gespeichert. Sie laden das adaptive Formular herunter und laden es auf einen anderen Server hoch. Der zweite Server hat ebenfalls einen Ordner „Training“ am selben Standort „/content/dam/formsanddocuments“. Der Hochladevorgang schlägt fehl.

## Download oder Upload eines Designs {#downloading-or-uploading-a-theme}

Mit [!DNL AEM Forms] können Sie Designs erstellen, herunterladen und hochladen. Ein Design wird wie andere Assets erstellt, z. B. Formulare, Dokumente und Briefe. Sie können ein Design erstellen, herunterladen und auf einer anderen Instanz hochladen, um es erneut zu verwenden. Weitere Informationen zu Designs finden Sie unter [Designs](themes.md) in [!DNL AEM Forms].

### Download eines Designs {#downloading-a-theme}

Sie können Designs in [!DNL AEM Forms] exportieren und in anderen Projekten oder Instanzen verwenden. Mit AEM können Sie ein Design als ZIP-Datei herunterladen, die Sie in die Instanz hochladen können.

Herunterladen von Designs

1. Melden Sie sich bei der [!DNL AEM Forms]-Instanz an.
1. Tippen Sie auf das Symbol „Experience Manager“ ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol „Navigation“ ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulare]** > **[!UICONTROL Designs]**.
1. Wählen Sie das Design und tippen Sie auf **[!UICONTROL Herunterladen]**. Das Design wird als ein Archiv (.zip-Datei) heruntergeladen.

### Upload eines Designs {#uploading-a-theme}

Sie können erstellte Designs mit Formatierungsvorgaben für Ihr Projekt verwenden. Sie können von Anderen erstellte Design-Pakete importieren, indem Sie diese in Ihr Projekt hochladen.

Hochladen von Designs

1. In Experience Manager navigieren Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulardesigns]**.
1. Auf der Seite „Designs“ klicken Sie auf **[!UICONTROL Formulare erstellen]** > **[!UICONTROL Formulardatei hochladen]**.
1. In der Eingabeaufforderung zur Dateiaktualisierung suchen Sie ein Designpaket auf Ihrem Computer, wählen es aus und klicken auf **[!UICONTROL Formulare hochladen]**. Das Design wird hochgeladen.

<!--

## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

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

### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

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
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator.
-->

## Exportieren eines Workflow-Programms {#export-a-workflow-application}

Sie können den AEM-Paket-Manager verwenden, um Workflow-Programme zu exportieren. Das Verfahren wird im Folgenden erläutert:

1. Öffnen Sie den [!DNL AEM Forms]-Paket-Manager.
1. Klicken Sie auf **[!UICONTROL Paket erstellen]**. Das Dialogfeld **[!UICONTROL Neues Paket]** wird angezeigt.
1. Geben Sie Name, Version und Gruppe für das Paket an. Klicken Sie auf **[!UICONTROL OK]**.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]** und öffnen Sie die Registerkarte **[!UICONTROL Filter]**. Klicken Sie auf **[!UICONTROL Filter hinzufügen]**. Geben Sie den Pfad der Workflow-Anwendung ein. Beispiel: /etc/fd/dashboard/startpoints/homemortgage. Klicken Sie auf **[!UICONTROL Regel hinzufügen]**.

1. Öffnen Sie die Registerkarte **[!UICONTROL Erweitert]**. Wählen Sie **[!UICONTROL Zusammenführen]** oder **[!UICONTROL Überschreiben]** im Feld „ACL-Bearbeitung“. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um das Paket zu erstellen.

   Nachdem das Paket erstellt wurde, können Sie es herunterladen und auf den anderen Server importieren. Der Arbeitsablauf wird auf dem Server, auf dem das Paket hochgeladen wird, angezeigt.

   >[!NOTE]
   >
   >Damit die Workflow-Anwendung ordnungsgemäß funktioniert, exportieren Sie auch das entsprechende adaptive Formular und Workflow-Muster mit der Arbeitsanwendung.

## Ordner und Organisieren von Assets {#folders-and-organizing-assets}

Die Benutzeroberfläche von [!DNL AEM Forms] verwendet Ordner zum Anordnen von Assets. Diese Ordner werden für Elemente verwendet, die in der Benutzeroberfläche von [!DNL AEM Forms] erstellt werden. In diesen Ordnern können Sie Dateien umbenennen, Unterordner erstellen und Assets und Dokumente ablegen. Wenn Sie Dokumente und Assets in einem Ordner organisieren, können Sie die Dateien für einfache Verwaltung gruppieren. Sie können einen Ordner auswählen und ihn herunterladen oder löschen.

Um einen Ordner zu erstellen, führen Sie die folgenden Schritte aus:

### Erstellen von Ordnern {#create-a-folder}

1. Melden Sie sich bei der [!DNL AEM Forms]-Benutzeroberfläche unter `https://<server>:<port>/aem/forms.html` an.
1. Navigieren Sie zu dem Speicherort, unter dem Sie einen Ordner erstellen möchten.
1. Tippen Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Ordner]**.
1. Geben Sie die folgenden Details ein:

   * **Titel**: Anzeigename für den Ordner
   * **Name**: *(obligatorisch)* Der Knotenname, unter dem Sie den Ordner im Repository speichern möchten

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des Namensfelds automatisch mit dem Titel ausgefüllt. Der Name darf nur alphanumerische Zeichen oder die Sonderzeichen Bindestrich (-) und Unterstrich (_) enthalten. Andere Sonderzeichen, die in den Titel eingegeben wurden, werden automatisch durch einen Bindestrich ersetzt und Sie werden aufgefordert, den neuen Namen zu bestätigen. Sie können mit dem vorgeschlagenen Namen fortfahren oder diesen weiter bearbeiten.

1. Ein neuer Ordner mit dem definierten Titel wird an der aktuellen Position in der Asset-Liste angezeigt.

   Wenn ein Ordner mit dem angegebenen Namen vorhanden ist, schlägt das Senden mit einem Fehler fehl. Sie können die Fehlermeldung anzeigen, indem Sie die Maus über das Fehlersymbol ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) bewegen, das neben dem Namensfeld angezeigt wird.

   Sie können auf den neu erstellten Ordner tippen, um innerhalb des Ordners zu navigieren und Assets oder Ordner innerhalb des Ordners zu erstellen. Außerdem können Sie einen Ordner auswählen und ihn für den Download in die Warteschlange stellen, ihn löschen oder seinen Namen bearbeiten.

<!-- ### Create copies of one or more assets or letters {#create-copies-of-one-or-more-assets-or-letters}

You can use an existing assets and letters to quickly create a assets and letters with similar properties, content, and inherited assets. You can copy and paste data dictionaries, document fragments, and letters.

Complete the following steps to create copies of assets and letters:

1. In the relevant Assets or Letters page, select one or more assets/letters. The UI displays the Copy icon.
1. Tap Copy. The UI displays the Paste icon. You can also choose to go/navigate inside a folder before you paste. Different folders can contain assets with same names. For more information on folders, see [Folders and organizing assets](#folders-and-organizing-assets).
1. Tap Paste. The Paste dialog appears. The system auto generates names and titles to the new copies of assets/letters, but you can edit the titles and names of the assets/letters.

   If you are copying and pasting the assets/letters at the same place, a suffix "-CopyXX" gets added to the existing name of the asset/letter. If no title existed for the copied asset/letter, the auto generated title field remains blank.

1. If required, edit the Title and Name with which you want to save the copy of the asset/letter.
1. Tap Paste. New copies of the copied assets are created.

## Search {#search-forms}

[!DNL AEM Forms] UI allows you to search your content. Using the top bar, you can tap Search **[A]** to search your content for resources such as assets and documents.

When you search for assets, [!DNL AEM Forms] displays the side panel. You can also tap ![assets-browser-content-only](assets/assets-browser-content-only.png) &gt; Filter **[B]** to invoke the side panel. Using the various filters in the side panel, you can narrow down your search. The side panel also allows you to save your searches.

![search_topbar](assets/search_topbar.png)

**A.** Search **B.** Filter

![Side panel - Filters](assets/search_sidepanel.png)

Side panel - Filters

On the side panel, you can use the following to narrow down your search results:

* Search Directory
* Tags
* Search Criteria; for example, Modified Dates, Publish Status, LiveCopy Status.

The side panel also allows you to save your search settings with names of your choice.

For more information and instructions on using search, filters, saved search, and side panel, see [Search](/help/sites-authoring/search.md).

-->
