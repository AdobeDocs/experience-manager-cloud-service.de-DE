---
title: Verwalten lizenzierter Assets in Content Hub
description: Erfahren Sie, wie Sie ein Lizenzfeld zum Metadatenformular für Assets hinzufügen, die Metadateneigenschaft „Lizenz“ auf Asset-Ordner anwenden und Assets mit Lizenzen zur Nutzung genehmigen.
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 91%

---

# Verwalten lizenzierter Assets in Content Hub {#manage-licensed-assets-on-content-hub}

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

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub-Handbuch als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Als Admin bearbeiten Sie das Metadatenformular, um das Feld für die Asset-Lizenz einzuschließen, damit es in den Asset-Eigenschaften in der AEM-Autorenumgebung angezeigt wird. Anschließend können Sie das Asset sowie seine Lizenz genehmigen, um das Asset in Content Hub zu lizenzieren und verfügbar zu machen.

Führen Sie die folgenden Schritte aus:

1. Bearbeiten Sie das Metadatenformular, um ein neues Textfeld für die Lizenzdetails hinzuzufügen. Ordnen Sie das Textfeld der Eigenschaft `dc:license` zu. Weitere Informationen zum Hinzufügen von Feldern zu einem Metadatenformular und zum Definieren von Eigenschaften finden Sie unter [Einrichten von Metadatenformularen](/help/assets/metadata-assets-view.md#metadata-forms).
   ![ZIP-Extraktion](/help/assets/assets/metadata-form-edit.png)
1. Wenden Sie das Metadatenformular auf den Asset-Ordner an, um die Einstellungen aus Schritt 1 anzuwenden. Informationen zum Zuweisen von Metadatenformularen zum Asset-Ordner finden Sie unter [Zuweisen von Metadatenformularen zu einem Ordner](/help/assets/metadata-assets-view.md#metadata-forms).
1. [Genehmigen Sie die lizenzierte PDF](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. Wählen Sie das Asset aus und klicken Sie auf **Details**, um seine Eigenschaften anzuzeigen. Definieren Sie im in Schritt 1 hinzugefügten Lizenzfeld den absoluten Pfad für die Asset-Lizenz, die in Schritt 3 oder bereits zuvor genehmigt wurde. Der absolute Pfad zu Content Hub folgt diesem Standardmuster: `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. Zum Beispiel: /content/dam/teamA/projects/documents/file1.pdf
   ![Absoluter Pfad](/help/assets/assets/absolute-path.png)
1. Genehmigen Sie das Asset, um es in Content Hub verfügbar zu machen, und klicken Sie auf **Speichern**. Informationen zum Genehmigen eines Assets finden Sie unter [Festlegen des Asset-Status](/help/assets/manage-organize-assets-view.md#set-asset-status).
