---
title: Verwalten von ebenenübergreifenden Assets
description: Erfahren Sie, wie Sie in InDesign-, Illustrator- und Photoshop-Dateien Verweise auf AEM-Assets erstellen. Darüber hinaus erfahren Sie, wie Sie mit der Funktion „Seitenanzeige“ einzelne Seiten mehrseitiger Dateien, darunter PDF, INDD, PPT, PPTX und Ai-Dateien, anzeigen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Verwalten von ebenenübergreifenden Assets {#managing-compound-assets}

Adobe Experience Manager (AEM) Assets kann erkennen, ob eine hochgeladene Datei Referenzen zu Assets enthält, die bereits im Repository vorhanden sind. Diese Funktion ist nur für unterstützte Dateiformate verfügbar. Wenn das hochgeladene Asset Referenzen zu AEM-Assets enthält, wird eine bidirektionale Verknüpfung zwischen dem hochgeladenen Asset und den referenzierten Assets erstellt.

Durch die Referenzierung von AEM-Assets in Adobe Creative Cloud-Anwendungen wird Redundanz beseitigt und die Zusammenarbeit verbessert. Außerdem werden die Effizienz und Produktivität der Benutzer gesteigert.

AEM Assets supports **bidirectional referencing**. Referenzierte Assets finden Sie auf der Asset-Detailseite der hochgeladenen Datei. Darüber hinaus finden Sie die referenzierenden Dateien für AEM-Assets auf der Asset-Detailseite des referenzierten Assets.

Referenzen werden auf der Grundlage von Pfad, Dokument-ID und Instanz-ID der referenzierten Assets aufgelöst.

## Hinzufügen von AEM-Assets als Referenzen in Adobe Illustrator {#refai}

Sie können vorhandene AEM-Assets aus einer Adobe Illustrator-Datei referenzieren.

1. Using [AEM desktop app](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html), mount AEM Assets repository as a drive on your local machine. Navigieren Sie im bereitgestellten Laufwerk zum Speicherort des Assets, das Sie referenzieren möchten.
1. Ziehen Sie das Asset vom bereitgestellten Laufwerk auf die Illustrator-Datei.
1. Save the Illustrator file to the mounted drive, or [upload](/help/assets/manage-digital-assets.md#uploading-assets) to the AEM repository.
1. Nach Abschluss des Workflows navigieren Sie zur Seite mit den Asset-Details für das Asset. Die Referenzen zu vorhandenen AEM-Assets werden unter **Abhängigkeiten** in der Spalte **Verweise** aufgeführt.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. The referenced assets that appear under **Dependencies** can also be referenced by files other than the current one. Um eine Liste der referenzierenden Dateien für ein Asset anzuzeigen, klicken Sie unter **Abhängigkeiten** auf das Asset.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Click the **View Properties** icon from the toolbar. Auf der Seite „Eigenschaften“ wird die Liste der Dateien, die das aktuelle Asset referenzieren, auf der Registerkarte **Allgemein** unter der Spalte **Verweise** angezeigt.

   ![chlimage_1-86](assets/chlimage_1-86.png)

## Hinzufügen von AEM-Assets als Referenzen in Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}

Um auf AEM-Assets aus einer InDesign-Datei zu verweisen, ziehen Sie entweder AEM-Assets in die InDesign-Datei oder exportieren Sie die InDesign-Datei als ZIP-Datei.

Referenzierte Assets sind bereits in AEM Assets enthalten. <!-- You can extract subassets by [configuring InDesign server](/help/assets/indesign.md). Embedded assets in an InDesign file are extracted as subassets. -->

>[!NOTE]
>
>Wenn der InDesign-Server als Proxyserver dient, wird die Vorschau der InDesign-Dateien innerhalb der XMP-Metadaten eingebettet. In diesem Fall ist die Extraktion von Miniaturen nicht explizit erforderlich. Wenn der InDesign-Server nicht als Proxyserver fungiert, müssen Miniaturen für InDesign-Dateien explizit extrahiert werden.

### Erstellen von Referenzen durch Ziehen von AEM-Assets {#create-references-by-dragging-aem-assets}

Dieses Verfahren weist Ähnlichkeiten zur in [Hinzufügen von AEM-Assets als Referenzen in Adobe Illustrator](#refai) beschriebenen Prozedur auf.

### Erstellen von Referenzen zu AEM-Assets durch Exportieren einer ZIP-Datei {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Erstellen Sie ein neues Workflow-Modell.
1. Exportieren Sie das Dokument mit der Paketfunktion von Adobe InDesign. 
Adobe InDesign kann ein Dokument und die verknüpften Assets als Paket exportieren. In diesem Fall enthält der exportierte Ordner einen Links-Ordner, der Unter-Assets in der InDesign-Datei enthält.
1. Erstellen Sie eine ZIP-Datei und laden Sie sie in das AEM-Repository hoch.
1. Starten Sie den Unarchiver-Workflow.
1. When the workflow completes, the references in the Links folder are automatically referenced as subassets. To view a list of referred assets, navigate to the asset details page of the InDesign asset and close the [Rail](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector).

## Hinzufügen von AEM-Assets als Referenzen in Adobe Photoshop {#refps}

1. Mit einem WebDAV-Client installieren Sie AEM Assets als Laufwerk.
1. Um Referenzen zu AEM-Assets in einer Photoshop-Datei zu erstellen, navigieren Sie im bereitgestellten Laufwerk zu den entsprechenden Assets mit der Funktion „Verknüpftes Smartobjekt platzieren“ in Photoshop.

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Save in Photoshop file to the mounted drive or or [upload](/help/assets/manage-digital-assets.md#uploading-assets) to the AEM repository.
1. Nach Abschluss des Workflows werden die Referenzen zu vorhandenen AEM-Assets auf der Asset-Detailseite aufgeführt.

   To view the referenced assets, close the [Rail](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) in the asset details page.

1. The referenced assets also contain the list of assets they are referenced from. To view a list of referenced assets, navigate to the asset details page and close the [Rail](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector).

>[!NOTE]
>
>Auf die Assets in zusammengesetzten Assets kann auch anhand ihrer Dokument-ID und Instanz-ID verwiesen werden. Diese Funktion ist nur in Adobe Illustrator und Adobe Photoshop verfügbar. Bei anderen Versionen erfolgt die Referenzierung basierend auf dem relativen Pfad von verknüpften Assets im ebenenübergreifenden Haupt-Asset, wie das auch bei früheren Versionen von AEM der Fall ist.

## Anzeigen von Seiten einer mehrseitigen Datei {#view-pages-of-a-multi-page-file}

Über die Viewer-Funktion von AEM Assets können Sie einzelne Seiten in mehrseitigen Dateien anzeigen, einschließlich PDF-, INDD-, PPT-, PPTX- und AI-Dateien. In InDesign können Sie Seiten mithilfe des InDesign-Servers extrahieren. Wenn die Vorschau von Seiten bei der Erstellung einer InDesign-Datei gespeichert wird, ist der InDesign-Server nicht für die Seitenextraktion erforderlich.

Sie können die einzelnen Seiten einer Datei auf der Asset-Seite durchblättern. Sie können Optionen in der Symbolleiste verwenden, um einzelne Seiten der Datei zu kommentieren. You can also use the **Page Overview** option to view all the pages simultaneously.

1. Navigieren Sie in AEM Assets zu dem Ordner, der die mehrseitige Datei enthält.
1. Klicken Sie auf ein Asset, um die entsprechende Asset-Seite anzuzeigen.

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Klicken Sie auf das globale Navigationssymbol und wählen Sie dann im Menü die Option **Seiten** aus.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Klicken Sie unterhalb des Bildes auf den Pfeil nach links bzw. nach rechts, um zu einzelnen Seiten in der Datei zu navigieren.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. To annotate a page, click the **Annotate** icon from the toolbar and add a comment.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. To download the file, click the **Download** icon.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. To view all pages of the file simultaneously, click the **Page Overview** icon.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. To view the activity stream for the file, including annotations and downloads, click the Global Nav ico and then choose **Timeline** from the menu.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. To view and edit the metadata properties of the page, click the **View Properties** icon from the toolbar.

   ![chlimage_1-95](assets/chlimage_1-95.png)
