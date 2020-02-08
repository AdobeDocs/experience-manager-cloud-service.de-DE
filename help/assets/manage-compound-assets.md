---
title: Verwalten von zusammengesetzten Assets
description: Erfahren Sie, wie Sie Verweise auf AEM-Assets aus Adobe InDesign-, Adobe Illustrator- und Adobe Fotoshop-Dateien erstellen. Erfahren Sie außerdem, wie Sie mit der Funktion "Seiten-Viewer"einzelne Seiten mehrseitiger Dateien anzeigen können, einschließlich PDF-, INDD-, PPT-, PPTX- und AI-Dateien.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Verwalten von ebenenübergreifenden Assets {#managing-compound-assets}

Adobe Experience Manager (AEM) Assets kann erkennen, ob eine hochgeladene Datei Referenzen zu Assets enthält, die bereits im Repository vorhanden sind. Diese Funktion ist nur für unterstützte Dateiformate verfügbar. Wenn das hochgeladene Asset Referenzen zu AEM-Assets enthält, wird eine bidirektionale Verknüpfung zwischen dem hochgeladenen Asset und den referenzierten Assets erstellt.

Durch die Referenzierung von AEM-Assets in Adobe Creative Cloud-Anwendungen wird Redundanz beseitigt und die Zusammenarbeit verbessert. Außerdem werden die Effizienz und Produktivität der Benutzer gesteigert.

AEM Assets supports **bidirectional referencing**. Referenzierte Assets finden Sie auf der Asset-Detailseite der hochgeladenen Datei. Darüber hinaus finden Sie die referenzierenden Dateien für AEM-Assets auf der Asset-Detailseite des referenzierten Assets.

Referenzen werden auf der Grundlage von Pfad, Dokument-ID und Instanz-ID der referenzierten Assets aufgelöst.

## Hinzufügen von AEM-Assets als Referenzen in Adobe Illustrator {#refai}

Sie können vorhandene AEM-Assets aus einer Adobe Illustrator-Datei referenzieren.

Um digitale Assets hinzuzufügen, verwenden Sie entweder die [AEM-Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem) oder [laden Sie sie über die AEM](/help/assets/manage-digital-assets.md#uploading-assets) -Benutzeroberfläche hoch.

Nach Abschluss des Workflows navigieren Sie zur Seite mit den Asset-Details für das Asset. Die Referenzen zu vorhandenen AEM-Assets werden unter **Abhängigkeiten** in der Spalte **Verweise** aufgeführt. The referenced assets that appear under **Dependencies** can also be referenced by files other than the current one.

Um eine Liste der referenzierenden Dateien für ein Asset anzuzeigen, klicken Sie unter **Abhängigkeiten** auf das Asset. Click the **View Properties** icon from the toolbar. Auf der Seite „Eigenschaften“ wird die Liste der Dateien, die das aktuelle Asset referenzieren, auf der Registerkarte **Allgemein** unter der Spalte **Verweise** angezeigt.

## Hinzufügen von AEM-Assets als Referenzen in Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}

Um auf AEM-Assets aus einer InDesign-Datei zu verweisen, ziehen Sie entweder AEM-Assets in die InDesign-Datei oder exportieren Sie die InDesign-Datei als ZIP-Datei.

Referenzierte Assets sind bereits in AEM Assets enthalten. Sie können Teilassets extrahieren, indem Sie den Adobe InDesign-Server konfigurieren. Eingebettete Assets in einer InDesign-Datei werden als Teilassets extrahiert.

>[!NOTE]
>
>Wenn der InDesign-Server als Proxyserver dient, wird die Vorschau der InDesign-Dateien innerhalb der XMP-Metadaten eingebettet. In diesem Fall ist die Extraktion von Miniaturen nicht explizit erforderlich. Wenn der InDesign-Server nicht als Proxyserver fungiert, müssen Miniaturen für InDesign-Dateien explizit extrahiert werden.

### Create references by dragging AEM assets {#create-references-by-dragging-aem-assets}

The procedure is similar to [Adding AEM assets as references in Adobe Illustrator](#refai).

### Create references to assets by exporting a ZIP file {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Neuen Arbeitsablauf erstellen.
1. Exportieren Sie das Dokument mit der Paketfunktion von Adobe InDesign. 
Adobe InDesign kann ein Dokument und die verknüpften Assets als Paket exportieren. In diesem Fall enthält der exportierte Ordner einen Links-Ordner, der Unter-Assets in der InDesign-Datei enthält.
1. Erstellen Sie eine ZIP-Datei und laden Sie sie in das AEM-Repository hoch.
1. Starten Sie den Unarchiver-Workflow.
1. Nach Abschluss des Workflows werden die Verweise im Ordner &quot;Links&quot;automatisch als Teilassets referenziert. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Seite mit den Asset-Details.

## Hinzufügen von AEM-Assets als Referenzen in Adobe Photoshop {#refps}

Um digitale Assets hinzuzufügen, verwenden Sie entweder die [AEM-Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem) oder [laden Sie sie über die AEM](/help/assets/manage-digital-assets.md#uploading-assets) -Benutzeroberfläche hoch.

Nach Abschluss des Workflows werden die Verweise auf vorhandene AEM-Assets auf der Seite mit den Asset-Details aufgeführt. Die referenzierten Assets enthalten auch die Liste der Assets, auf die sie verwiesen werden. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Seite mit den Asset-Details.

>[!NOTE]
>
>Auf die Assets in zusammengesetzten Assets kann auch anhand ihrer Dokument-ID und Instanz-ID verwiesen werden. Diese Funktion ist nur in Adobe Illustrator und Adobe Photoshop verfügbar. Bei anderen Versionen erfolgt die Referenzierung basierend auf dem relativen Pfad von verknüpften Assets im ebenenübergreifenden Haupt-Asset, wie das auch bei früheren Versionen von AEM der Fall ist.

## Anzeigen von Seiten einer mehrseitigen Datei {#view-pages-of-a-multi-page-file}

Über die Viewer-Funktion von AEM Assets können Sie einzelne Seiten in mehrseitigen Dateien anzeigen, einschließlich PDF-, INDD-, PPT-, PPTX- und AI-Dateien. In InDesign können Sie Seiten mithilfe des InDesign-Servers extrahieren. Wenn die Vorschau von Seiten bei der Erstellung einer InDesign-Datei gespeichert wird, ist der InDesign-Server nicht für die Seitenextraktion erforderlich.

Sie können die einzelnen Seiten einer Datei auf der Asset-Seite durchblättern. Sie können Optionen in der Symbolleiste verwenden, um einzelne Seiten der Datei zu kommentieren. You can also use the **Page Overview** option to view all the pages simultaneously.

1. Navigieren Sie in AEM Assets zu dem Ordner, der die mehrseitige Datei enthält.
1. Klicken Sie auf ein Asset, um die entsprechende Asset-Seite anzuzeigen.
1. Klicken Sie auf das globale Navigationssymbol und wählen Sie dann im Menü die Option **Seiten** aus.
1. Klicken Sie unterhalb des Bildes auf den Pfeil nach links bzw. nach rechts, um zu einzelnen Seiten in der Datei zu navigieren.
1. To annotate a page, click the **Annotate** icon from the toolbar and add a comment.
1. To download the file, click the **Download** icon.
1. To view all pages of the file simultaneously, click the **Page Overview** icon.
1. To view the activity stream for the file, including annotations and downloads, click the AEM icon and then choose **Timeline** from the menu.
1. To view and edit the metadata properties of the page, click the **View Properties** icon from the toolbar.
