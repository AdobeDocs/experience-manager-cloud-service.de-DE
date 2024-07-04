---
title: Importieren, Exportieren und Organisieren von adaptiven Formularen oder PDF-Formularen auf einer AEM Forms-Instanz?
description: Erfahren Sie, wie Sie adaptive Formulare, PDF-Formulare, Designs und andere unterstützende Assets in und von AEM-Instanzen migrieren können.
topic-tags: forms-manager
role: Admin, User
feature: Adaptive Forms
exl-id: f5105fb7-b8c0-4656-8095-b21d392746c0
source-git-commit: 6f547bd743932d45e45e0a3c47ff5eb2129cb664
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 53%

---



| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/manage-administer-aem-forms/import-export-forms-templates) |
| AEM as a Cloud Service | Dieser Artikel |

# Importieren und Exportieren von adaptiven Formularen und AEM Forms-Assets {#importing-and-exporting-assets-to-aem-forms}

Sie können Adaptive Forms und zugehörige Assets wie Themen für adaptive Formulare, Formulardatenmodell (FDM), Vorlagen für adaptive Formulare, Fragmente und PDF forms zwischen [!DNL AEM Forms] Instanzen.

## Herunterladen adaptiver Forms-, PDF forms- oder zugehöriger Assets {#download-forms-amp-documents-assets}

So laden Sie Formulare oder zugehörige Assets herunter:

1. Melden Sie sich bei der [!DNL Experience Manager Forms]-Instanz an.
1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

   ![Forms auswählen](/help/forms/assets/select-forms.png)

1. Wählen Sie die Assets aus und klicken Sie auf die **[!UICONTROL Herunterladen]** in der oberen Leiste angezeigt.

   ![Forms herunterladen](/help/forms/assets/download-form.png)

   Wenn Sie das Formular herunterladen, wird die **[!UICONTROL Asset(s) herunterladen]** angezeigt.

   ![Herunterladen von Formular-Assets](/help/forms/assets/download-form-assets.png)

1. Klicken Sie auf **[!UICONTROL Herunterladen]**.

Die ausgewählten Assets werden als Archiv (.zip-Datei) heruntergeladen.

## Hochladen von adaptiven Forms-, PDF forms- oder zugehörigen Assets {#upload-forms-amp-documents-assets}

Sie können die unterstützten Assettypen einzeln oder als ZIP-Archiv hochladen. Bei einer ZIP-Datei werden die relativen Pfade aller unterstützten Assets angezeigt. Nicht unterstützte Assets in der ZIP-Datei werden ignoriert und nicht aufgelistet. Wenn das ZIP-Archiv jedoch nur die nicht unterstützten Assets enthält, wird anstelle des Popup-Dialogfensters eine Fehlermeldung angezeigt.
So laden Sie ein Formular oder ein referenziertes Asset hoch:

1. Melden Sie sich bei der [!DNL Experience Manager Forms]-Instanz an.
1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

   ![Forms auswählen](/help/forms/assets/select-forms.png)

1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]**. Ein Dialogfeld wird angezeigt.

   ![Forms hochladen](/help/forms/assets/form-upload.png)

1. Navigieren Sie im Dialogfeld zum Paket oder Archiv, das importiert werden soll, und wählen Sie es aus. Sie können auch andere unterstützte Dateitypen auswählen. Wählen Sie **[!UICONTROL Öffnen]**. Der ausgewählte Ordner- oder Dateiname darf keine Sonderzeichen enthalten.

   Überprüfen Sie im Dialogfeld die Details der Assets, die hochgeladen werden, und wählen Sie **[!UICONTROL Hochladen]** aus.

   Wenn Sie ein vorhandenes Formular-Asset hochladen, wird das Asset aktualisiert.

   >[!NOTE]
   >
   > Bei Namenskonflikten mit unterschiedlichen Ressourcentypen wird beim Hochladen eines Pakets die vorhandene Ordnerhierarchie nicht ersetzt. Wenn Sie beispielsweise ein adaptives Formular mit dem Namen &quot;Training&quot;am Speicherort haben `/content/dam/formsanddocuments` auf einem Server. Sie können das adaptive Formular herunterladen und das Formular auf einen anderen Server hochladen. Der zweite Server hat auch einen Ordner mit dem Namen &quot;Training&quot;am selben Speicherort. `/content/dam/formsanddocuments`. Der Hochladevorgang schlägt fehl.

## Herunterladen eines Designs

Sie können Designs in [!DNL AEM Forms] exportieren und in anderen Projekten oder Instanzen verwenden. AEM ermöglicht Ihnen, Designs als ZIP-Datei herunterzuladen, die Sie in die Instanz hochladen können.
Herunterladen von Designs

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms] Autoreninstanz.
1. Auswählen **[!UICONTROL Forms]** > **[!UICONTROL Designs]**.

   ![Design auswählen](/help/forms/assets/select-theme.png)

1. Wählen Sie auf der Seite Designs das Design aus und klicken Sie auf das **[!UICONTROL Herunterladen]** in der oberen Leiste angezeigt.

   ![Download-Design](/help/forms/assets/download-theme.png)

   Wenn Sie das Design herunterladen, wird die **[!UICONTROL Asset(s) herunterladen]** angezeigt.

   ![Herunterladen von Designassets](/help/forms/assets/download-theme-asset.png)

1. Klicken Sie auf **[!UICONTROL Herunterladen]**.

Die ausgewählten Assets werden als Archiv (.zip-Datei) heruntergeladen.

## Hochladen eines Designs {#uploading-a-theme}

Sie können Designs hochladen und verwenden, die andere in Ihren Formularen erstellen.
Hochladen von Designs

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Instanz an.
1. In Experience Manager navigieren Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Designs]**.

   ![Design auswählen](/help/forms/assets/select-theme.png)

1. Auf der Seite „Designs“ klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Datei hochladen]**.

   ![Design hochladen](/help/forms/assets/theme-upload.png)

1. Suchen Sie ein Designpaket auf Ihrem Computer, wählen Sie es aus und klicken Sie auf **[!UICONTROL Hochladen]**. Das hochgeladene Design wird auf der Seite Designs verfügbar.

## Organisieren von adaptiven Formularen, PDF-Formularen und zugehörigen Assets mithilfe von Ordnern   {#folders-and-organizing-assets}

Sie können Ordner verwenden, um Assets zu gruppieren und zu organisieren. Wenn Sie Dokumente und Assets in einem Ordner organisieren, können Sie die Dateien gruppieren und somit die Verwaltung vereinfachen. Sie können einen Ordner auswählen und ihn herunterladen oder löschen.

### Erstellen eines Ordners {#create-a-folder}

So erstellen Sie einen Ordner:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Instanz an.
1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

   ![Formular auswählen](/help/forms/assets/select-forms.png)

1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Ordner]**.

   ![Ordner erstellen](/help/forms/assets/create-folder.png)

   Die **[!UICONTROL Ordner hinzufügen]** angezeigt.
1. Geben Sie die **[!UICONTROL Titel]**. Die **[!UICONTROL Name]** automatisch ausgefüllt wird, während Sie die **[!UICONTROL Titel]**.

   ![Ordner hinzufügen](/help/forms/assets/add-folder.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des Namensfelds automatisch mit dem Titel ausgefüllt. Der Name darf nur alphanumerische Zeichen oder die Sonderzeichen Bindestrich (-) und Unterstrich (_) enthalten. Alle anderen Sonderzeichen, die im Titel eingegeben werden, werden automatisch durch einen Bindestrich ersetzt und Sie werden aufgefordert, den neuen Namen zu bestätigen. Sie können den vorgeschlagenen Namen verwenden oder ihn weiter bearbeiten.

Ein neuer Ordner mit dem definierten Titel wird an der aktuellen Position in der Asset-Liste angezeigt.

Wenn ein Ordner mit dem angegebenen Namen vorhanden ist, schlägt das Senden mit einem Fehler fehl. Sie können die Fehlermeldung anzeigen, indem Sie die Maus über das Fehlersymbol ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) bewegen, das neben dem Namensfeld angezeigt wird.

Sie können den erstellten Ordner auswählen, um in den Ordner zu wechseln und Assets oder Ordner innerhalb des Ordners zu erstellen. Außerdem können Sie einen Ordner auswählen und ihn zum Herunterladen in die Warteschlange stellen, ihn löschen oder seinen Namen bearbeiten.

### Erstellen von Kopien eines oder mehrerer Assets {#create-copies-of-one-or-more-assets-or-letters}

Sie können vorhandene Assets verwenden, um schnell ein Asset mit ähnlichen Eigenschaften, Inhalten und vererbten Assets zu erstellen.

So erstellen Sie Kopien von Assets:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Instanz an.
1. Wählen Sie auf der entsprechenden Asset-Seite mindestens ein Asset aus. Die Benutzeroberfläche zeigt die **[!UICONTROL Kopieren]** Symbol.
1. Auswählen **[!UICONTROL Kopieren]**. Die Benutzeroberfläche zeigt die ![Symbol &quot;Einfügen&quot;](/help/forms/assets/Smock_Paste_18_N.svg) Symbol.

   ![Asset kopieren](/help/forms/assets/copy-asset.png)

   Sie können vor dem Einfügen auch in einen Ordner wechseln bzw. darin navigieren. Verschiedene Ordner können Assets mit denselben Namen enthalten. Weitere Informationen zu Ordnern finden Sie unter [Ordner und Organisieren von Assets](#folders-and-organizing-assets).
1. Auswählen **[!UICONTROL Einfügen]**.

   ![Asset einfügen](/help/forms/assets/paste-asset.png)

1. Die **[!UICONTROL Einfügen]** angezeigt. Das System generiert automatisch Namen und Titel für die neuen Kopien von Assets, aber Sie können die Titel und Namen der Assets bearbeiten.

   Wenn Sie die Assets kopieren und an derselben Stelle einfügen, wird dem vorhandenen Namen des `asset`. Wenn für das kopierte Asset kein Titel vorhanden war, bleibt das automatisch generierte Titelfeld leer.

   ![Einfügen von Assets an einem neuen Speicherort](/help/forms/assets/paste-click-asset.png)

   Bearbeiten Sie bei Bedarf die **[!UICONTROL Titel]** mit dem Sie die Kopie des Assets speichern möchten. Die **[!UICONTROL Name]** automatisch ausgefüllt wird, während Sie die **[!UICONTROL Titel]**.
1. Auswählen **[!UICONTROL Einfügen]**. Es werden neue Kopien der kopierten Assets erstellt.

## Suchen {#search-forms}

Wenn Sie eine große Anzahl von Assets haben, ist die Suche nach dem richtigen Asset zeitaufwendig. Sie können eine textbasierte Suche nach einem bestimmten Asset auf der Asset-Seite durchführen.

So suchen Sie das Asset:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Instanz an.
1. Klicken Sie auf ![Suchsymbol](assets/folder-search-icon.svg) Suchsymbol.

   ![Suchformular](/help/forms/assets/search-form.png)

1. Geben Sie in der Suchleiste den Namen des Assets ein, nach dem Sie suchen möchten.

1. Eine Liste verwandter Assets wird angezeigt. Wählen Sie das gewünschte Asset aus der angezeigten Asset-Liste aus.

   ![Suchen von Assets](/help/forms/assets/search-bar.png)

Weitere Informationen und Anweisungen zur Verwendung der Suche finden Sie unter [Suche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=de).

<!--
## Export or create a package {#export-a-workflow-application}

You can use packages to install new content, install new functionality, transfer content between instances, and back up content.
To export or create a package:

1. Log in to your [!DNL Experience Manager Forms] instance.
1. Navigate to **[!UICONTROL Tools]** ![hammer](assets/hammer.png) &gt; **[!UICONTROL Deployment]** &gt; **[!UICONTROL Packages]**.

   ![Package Manager](/help/forms/assets/package-manager.png)

1. Click **[!UICONTROL Create Package]**.

   ![Create package](/help/forms/assets/create-package.png)   
   
   When **[!UICONTROL Create Package]** is clicked, the **[!UICONTROL New Package]** dialog box appears.
1. Specify the package name, version, and group for the package. 
   
   ![New package](/help/forms/assets/new-package.png)  

   * **Package Name** - Select a descriptive name to help you identify the contents of the package.

   * **Version** - It is a textual field to indicate a version. This is appended to the package name to form the name of the zip file.

   * **Group** - This is the target group (or folder) name. Groups help you organize your packages. A folder is created for the group if it does not already exist. If you leave the group name blank, it creates the package in the main package list.

1. Click **[!UICONTROL OK]**.

   Once the package is created, it appears at the top of the list of packages.

1. Click **[!UICONTROL Edit]**.
   
   ![Edit Package](/help/forms/assets/edit-package.png)
    
1. Open the **[!UICONTROL Filters]** tab.
   
   ![Open filter tab](/help/forms/assets/add-filter-package.png)
   
1.  Click **[!UICONTROL Add Filter]**. 
   
      ![Add filter](/help/forms/assets/add-filter.png)

      You can specify the path of the package. You can also add rules and other validations for the package.

      ![Add path](/help/forms/assets/add-path.png)

1. Click **[!UICONTROL Save]** after you are finished editing the settings.
1. Click **[!UICONTROL Build]** to create the package.
    
     ![Build path](/help/forms/assets/build-package.png)

   After the package is built, you can download the package and import it to the other server. The workflow application appears on the server where the package is uploaded.

   >[!NOTE]
   >
   >For the workflow application to work properly, also export the corresponding Adaptive Form and workflow model with the work application.

   Once a package is uploaded to AEM, you can modify its settings. You can also download or delete the package.

## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

To share assets, such as data dictionaries, letters, and document fragments, between two different implementations of Correspondence Management, you can create and share .cmp files. A .cmp file can include one or more data dictionaries, letters, document fragments, and forms.

### Export Document Fragments, Letters, and/or Data Dictionaries {#export-document-fragments-letters-and-or-data-dictionaries}

1. In the letters, document fragments, or data dictionary pages, select and select the assets you want to export to a single package, and then select Queue For Download. The assets are lined-up for export.
1. As required, repeat the above step to add letters, document fragments, and data dictionaries.
1. Select **Download**.
1. Correspondence Management displays Download Asset(s) dialog with a list of assets in the export list.

   ![export](assets/export.png)

1. To view the dependencies that are exported, Select Resolve. Or skip to the next step. Even if you do not select resolve, the dependencies are still exported.
1. To download the .cmp file, select **OK**.
1. Correspondence Management downloads a .cmp file to your computer.

   The .cmp file includes the exported assets. You can share the .cmp file with others. Other users can import the .cmp file in a different server to get all the assets in the new server.

### Export all the Correspondence Management assets as a package {#export-all-the-correspondence-management-assets-as-a-package}

Use this option to download all the Correspondence Management assets and related dependencies as a package from an [!DNL AEM Forms] instance.

For example, if Correspondence Management has a letter that uses an image and text, the downloaded package also contains the image and the text related to the letter. All the metadata properties (including custom properties) associated with the asset are also downloaded. Once you have downloaded the package (.cmp), you can [import the package to a different [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

To download all the Correspondence Management assets and related dependencies as a package, complete the following steps:

1. Log in to [!DNL AEM Forms] server as a forms user.
1. Select **Adobe Experience Manager** in the Global Navigation bar.
1. Select tools ( ![tools](assets/tools.png)) and then select **Forms**.
1. Select **Export Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``The Export All Correspondence Management Assets page appears and displays the information about the last time the Export process was attempted and a link to download the last successfully exported package.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Select **Export** and, in the confirm message, select **OK**.

   After a batch process is complete, the last run details and the link to download the package are updated. This includes information such as the Administrator login and if the batch run successfully or failed. The assets are exported to a package and the Download Exported Package link appears.

   >[!NOTE]
   >
   >The Export All Assets process cannot be canceled once initiated. Also, while the export all operation is in process, do not create, delete, modify, or publish any assets or initiate Publish All Assets process.a

1. Select the **Download Exported Package** link to download the package file.

   To add the assets in the package to another instance of Correspondence Management, [import the package to an [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

<!-- ### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

You can import assets that are exported into a .cmp file. A .cmp file can have one or more letters, data dictionaries, document fragments, and dependent assets.

>[!NOTE]
>
>While importing old Correspondence Management assets for migration, log in using an Admin account. For more information on Migrating old Correspondence Management assets, see [Migrate Correspondence Management assets to AEM 6.1 forms](migration-utility.md).

1. On the data dictionary, letters, or document fragments page, select **Create &gt; File Upload** and select the .cmp file.
1. Correspondence Management displays the Import Assets dialog with the list of assets that are imported. Select **Import**.

   After importing the assets, the following properties of the assets are updated while the other properties remain the same:

    * Author: Displays the ID of the user that imported the asset to the server
    * Modified: The time when the asset was imported to the server

   >[!NOTE]
   >
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator. -->

## Siehe auch {#see-also}

{{see-also}}
