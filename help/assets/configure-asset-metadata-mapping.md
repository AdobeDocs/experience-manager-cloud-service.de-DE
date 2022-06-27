---
title: Konfigurieren der Asset-Metadatenzuordnung zwischen Workfront und Experience Manager Assets
description: Ordnen Sie die Asset-Metadatenfelder zwischen Adobe Workfront und Experience Manager as a Cloud Service Anwendungen zu. Durch die Zuordnung von Metadatenfeldern können Sie beim Senden eines Assets von Workfront an Experience Manager Assets die zugeordneten Asset-Metadaten in Experience Manager Assets anzeigen.
source-git-commit: 212ecb5330de739b2e479d36462953ce33697c1c
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 10%

---

# Konfigurieren der Asset-Metadatenzuordnung zwischen Adobe Workfront und Experience Manager Assets {#asset-metadata-mapping-workfront-aem-assets}

Sie können die Asset-Metadatenfelder zwischen Adobe Workfront und Experience Manager as a Cloud Service Anwendungen zuordnen. Durch die Zuordnung von Metadatenfeldern können Sie beim Senden eines Assets von Workfront an Experience Manager Assets die zugeordneten Asset-Metadaten in Experience Manager Assets anzeigen.

Wenn Sie beispielsweise die Metadatenfelder für ein Bild wie Namen, Beschreibung und das Projekt, zu dem es gehört, beim Senden des Bildes an Experience Manager Assets, beibehalten müssen, konfigurieren und ordnen Sie diese Felder den Experience Manager Assets-Eigenschaften zu.

**Nutzungsszenario**

Ein Bild `add-users-workfront.png` ist in der `Metadata Syncs` Projekt in der Adobe Workfront-Anwendung. Sie müssen dieses Bild mit den folgenden Metadaten as a Cloud Service an Experience Manager Assets senden:

* Projektname

* Dokumentname

* Dokumentbeschreibung

## Voraussetzungen {#prerequisites}

* Administratorzugriff auf as a Cloud Service Workfront- und Experience Manager Assets-Anwendungen.

* Eine Integration zwischen [as a Cloud Service Anwendungen für Workfront und Experience Manager Assets](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FDocuments%2FAdobe_Workfront_for_Experience_Manager_Assets_Essentials%2Fsetup-asset-essentials.htm&amp;_LANG=enus).

## Einrichten der Metadatenzuordnung in Workfront {#set-up-metadata-mapping}

So legen Sie die Metadatenzuordnung für die Felder &quot;Projektname&quot;, &quot;Dokumentname&quot;und &quot;Dokumentbeschreibung&quot;in Workfront fest:

1. Klicken Sie auf das Symbol Hauptmenü . ![Menü anzeigen](assets/show-menu.svg) in der oberen rechten Ecke der Adobe Workfront-Anwendung verfügbar sind, klicken Sie auf **[!UICONTROL Einrichtung]**.

1. Auswählen **[!UICONTROL Dokumente]** Wählen Sie im linken Bereich die Option **[!UICONTROL Experience Manager Assets]**.

1. Wählen Sie die Experience Manager Assets-Integration aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Klicken **[!UICONTROL Metadaten]**. Im **[!UICONTROL Assets]** Registerkarte, ordnen Sie die [!UICONTROL Projekt] > [!UICONTROL Name] Workfront-Feld zum `wm:projectName` Experience Manager Assets-Feld. Wenn Sie die exakte Übereinstimmung nicht finden, empfiehlt Adobe, nach der besten Übereinstimmung zu suchen, um das Workfront- und Experience Manager Assets-Feld zuzuordnen. Sie können die Zuordnung von Feldern unterschiedlicher Datentypen vermeiden. Sie können beispielsweise ein Datumsfeld in Workfront einem Beschreibungsfeld in Assets zuordnen.
1. Ordnen Sie die [!UICONTROL Dokument] > [!UICONTROL Name] Workfront-Feld zum `wm:documentName` Experience Manager Assets-Feld.

   ![Zuordnung in Workfront](assets/workfront-metadata-mapping.png)

1. Ordnen Sie die [!UICONTROL Dokument] > [!UICONTROL Beschreibung] Workfront-Feld zum `dc:description` Experience Manager Assets-Feld.

   >[!VIDEO](https://video.tv.adobe.com/v/344255)

## Senden des Bildes von Workfront an Experience Manager Assets {#send-image-workfront-assets}

So senden Sie das Bild von Workfront an Experience Manager Assets:

1. Klicken Sie auf das Symbol Hauptmenü . ![Menü anzeigen](assets/show-menu.svg) in der oberen rechten Ecke der Adobe Workfront-Anwendung verfügbar sind, klicken Sie auf **[!UICONTROL Projekte]**.

1. Klicken **[!UICONTROL Neues Projekt]** , um ein neues Projekt zu erstellen.

1. Klicken **[!UICONTROL Dokumente]** im linken Bereich verfügbar sind, ziehen Sie das Bild, das Sie an Experience Manager Assets senden möchten, und wählen Sie es aus.

1. Klicken **[!UICONTROL Senden an]** und wählen Sie dann den Integrationsnamen Experience Manager Assets Essentials aus.

   ![Senden an AEM](assets/send-to-aem.png)

1. Wählen Sie den Zielordner für das Asset aus und klicken Sie auf **[!UICONTROL Ordner auswählen]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Konfigurieren der Asset-Metadatenzuordnung in Experience Manager as a Cloud Service {#metadata-mapping-aem}

Nachher [Konfigurieren der Asset-Metadatenzuordnung in Adobe Workfront](#set-up-metadata-mapping)müssen Sie dieselbe Zuordnung in der as a Cloud Service Experience Manager Assets-Anwendung verwenden, um die entsprechenden Metadaten-Ergebnisse für das Bild anzuzeigen.

Die Metadaten-Zuordnung wird mithilfe von Metadatenschemata in Experience Manager Assets durchgeführt. Sie können ein neu hinzugefügtes oder vorhandenes Metadatenschema-Formular bearbeiten. Das Metadatenschema-Formular enthält Registerkarten und Formularelemente auf Registerkarten. Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren. Sie können dem Metadatenschema-Formular Registerkarten oder Formularelemente hinzufügen. Weitere Informationen finden Sie unter [Metadatenschemata](metadata-schemas.md).

So konfigurieren Sie die Metadatenzuordnung mit einem neuen Metadatenformular in Experience Manager Assets as a Cloud Service:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**. Geben Sie im Dialog den Titel des Schemaformulars ein und klicken Sie auf **[!UICONTROL Erstellen]**, um den Prozess zur Formularerstellung abzuschließen.

1. Wählen Sie das Schemaformular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. (Optional) Klicken Sie im Metadatenschema-Formular-Editor auf `+` , um eine neue Registerkarte für die Workfront-Felder zu erstellen.

1. Klicken Sie auf **[!UICONTROL Formular erstellen]** und ziehen Sie die **[!UICONTROL Einzelzeilentext]** -Komponente in das Formular ein. Klicken Sie auf die Komponente im Formular. Im **[!UICONTROL Formular erstellen]** tab:

   1. Angeben `Project Name` im **[!UICONTROL Feldbezeichnung]** -Feld.

   1. Angeben `./jcr:content/metadata/wm:projectName` im **[!UICONTROL Zu Eigenschaft zuordnen]** -Feld. Verwenden Sie als Richtlinie die folgende Vorlage, um die Feldzuordnungen in Experience Manager Assets zu definieren:
      `./jcr:content/metadata/<mapping defined for the field in workfront>`.

      Beim Konfigurieren von Zuordnungen in Workfront haben Sie `wm:projectName` Experience Manager Assets-Feld zu Projekt > Workfront-Feld benennen .

      `wm` auf den Namespace-Namen verweist und `projectName` verweist auf den Eigenschaftstitel. Verwenden Sie die `namespace:propertyTitle` -Format, um Metadatenfeld-Zuordnungen zu definieren.

      ![Senden an AEM](assets/metadata-schema-mapping.png)

1. Klicken Sie auf **[!UICONTROL Formular erstellen]** und ziehen Sie die **[!UICONTROL Einzelzeilentext]** -Komponente in das Formular ein. Klicken Sie auf die Komponente im Formular. Im **[!UICONTROL Formular erstellen]** tab:

   1. Angeben `Document Name` im **[!UICONTROL Feldbezeichnung]** -Feld.

   1. Angeben `./jcr:content/metadata/wm:documentName` im **[!UICONTROL Zu Eigenschaft zuordnen]** -Feld.
Beim Konfigurieren von Zuordnungen in Workfront haben Sie `wm:documentName` Experience Manager Assets-Feld zu Dokument > Workfront-Feld benennen .

1. Klicken Sie auf **[!UICONTROL Formular erstellen]** und ziehen Sie die **[!UICONTROL Mehrzeiliger Text]** -Komponente in das Formular ein. Klicken Sie auf die Komponente im Formular. Im **[!UICONTROL Formular erstellen]** tab:

   1. Angeben `Document Description` im **[!UICONTROL Feldbezeichnung]** -Feld.

   1. Angeben `./jcr:content/metadata/dc:description` im **[!UICONTROL Zu Eigenschaft zuordnen]** -Feld.
Beim Konfigurieren von Zuordnungen in Workfront haben Sie `dc:description` Experience Manager Assets-Feld in das Feld &quot;Dokument&quot;> &quot;Beschreibung Workfront&quot;.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

   >[!VIDEO](https://video.tv.adobe.com/v/344314)

## Anwenden von Metadateneinstellungen auf Bildordner {#apply-metadata-settings-image-folder}

Wenden Sie diese Einstellungen nach dem Konfigurieren der Metadateneinstellungen in der as a Cloud Service Experience Manager-Anwendung auf die [Ordner mit dem Bild, das von der Workfront-Anwendung gesendet wird](#send-image-workfront-assets).

So wenden Sie Metadateneinstellungen auf den Bildordner an:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.

1. Wählen Sie das Metadatenschema aus der verfügbaren Liste aus und klicken Sie auf **[!UICONTROL Auf Ordner anwenden]**.

1. Wählen Sie den Zielordner aus, in den [das Bild von der Adobe Workfront-Anwendung gesendet wird](#send-image-workfront-assets) und klicken Sie auf **[!UICONTROL Anwenden]**.

Sie können zum Bild in Experience Manager Assets navigieren und die mit dem Bild verknüpften Metadaten anzeigen. Wählen Sie das Bild aus und klicken Sie auf **[!UICONTROL Eigenschaften]** , um die Bildmetadaten anzuzeigen.



