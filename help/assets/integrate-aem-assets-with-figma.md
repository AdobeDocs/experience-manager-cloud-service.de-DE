---
title: Integrieren Sie [!DNL AEM Assets] mit [!DNL Figma].
description: Erfahren Sie, wie Sie [!DNL AEM Assets] mit [!DNL Figma] integrieren, um auf die Assets Ihres Unternehmens in Ihrem  [!DNL Figma] -Design-Workflow zuzugreifen und sie zu verwenden.
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: d37ebf94f617e8424799757c18037a73e97820b4
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 28%

---


# Integration von [!DNL AEM Assets] mit [!DNL Figma]{#integrate-aem-assets-with-figma}

Dank der nativen Integration von [!DNL AEM Assets] mit [!DNL Figma] können Entwickelnde über die [!DNL Figma]-Benutzeroberfläche direkt auf die in [!DNL AEM Assets] gespeicherten Assets zugreifen. Sie können in [!DNL AEM Assets] verwaltete Inhalte auf der [!DNL Figma]-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem [!DNL AEM Assets]-Repository speichern.

## Voraussetzungen{#prerequisites-for-aem-assets-and-figma-integration}

* Die mindestens erforderliche AEM-Version ist `19149`.

* Sie müssen über gültige [!DNL AEM Assets]- und [!DNL Figma]-Lizenzen verfügen, um [!DNL AEM Assets] mit [!DNL Figma] integrieren zu können.

## Unterstützte Dateiformate {#supported-file-formats-integration-figma}


* Für den Import von [!DNL AEM]-Assets in Figma werden folgende Formate unterstützt: Bild-Assets (JPEG, PNG), Videodateien (MP4, MOV, WebM), Animationsdateien (GIF) und Vektordateien (SVG).
* Beim Export von Designs von [!DNL Figma] nach [!DNL AEM Assets] werden die Formate **PNG**, **PDF**, **JPG** und **SVG** unterstützt.

## Zugriff auf den [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]{#access-aem-assets-connector}

Führen Sie die folgenden Schritte aus, um auf den [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] zuzugreifen:

1. Klicken Sie auf Ihrer [!DNL Figma]-Startseite in der Symbolleiste unten auf der Arbeitsfläche auf **[!UICONTROL Aktionen]** und suchen Sie in der Suchleiste im Dialogfeld nach [!DNL Adobe Experience Manager (AEM) Assets Connector].
1. Wählen Sie [!DNL Adobe Experience Manager (AEM) Assets Connector] aus, um das Panel [!DNL Adobe Experience Manager (AEM) Assets Connector] anzuzeigen. [Importieren Sie [!DNL AEM] Assets über dieses Panel in Ihre [!DNL Figma] Arbeitsfläche](#import-aem-assets-into-figma-workflow).   ![Aktionen](/help/assets/assets/actions-on-figma.png)
Alternativ können Sie auf die in [!DNL Figma] Community verfügbaren [[!DNL Adobe Experience Manager (AEM) Assets Connector]](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector) zugreifen, auf **[!UICONTROL Öffnen in…]** klicken, eine aktuelle Datei auswählen oder eine neue Datei erstellen und auf **[!UICONTROL Ausführen]** klicken, um auf das [!DNL Adobe Experience Manager (AEM) Assets Connector] zuzugreifen.   ![plugin-page-on-figma-community](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [Wenden Sie sich an den Adobe-Support](https://helpx.adobe.com/de/contact.html), wenn Ihnen nach der Anmeldung bei Ihrer [!DNL AEM]-Umgebung eine Meldung zu einem **[!UICONTROL Netzwerkfehler]** angezeigt wird.

## Importieren von [!DNL AEM]-Assets in die [!DNL Figma]-Arbeitsfläche{#import-aem-assets-into-figma-workflow}

[Greifen Sie auf das Panel [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]](#access-aem-assets-connector) in Ihrer [!DNL Figma]-Design-Benutzeroberfläche zu und führen Sie die folgenden Schritte aus:

1. Suchen Sie im Panel [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] nach Assets. Weitere Informationen finden Sie unter [Verwenden von Content Advisor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector).

1. Ziehen Sie das Asset per Drag-and-Drop auf die Arbeitsfläche oder wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Auswählen]**, damit das Asset auf der Arbeitsfläche angezeigt wird.

1. Klicken Sie auf ![drei Punkte](/help/assets/assets/three-dots.svg) im Ordnerpfad, um alle übergeordneten und untergeordneten Ordner in der aktuellen Hierarchie anzuzeigen. Wählen Sie einen Ordner aus, um zu diesem Speicherort zu navigieren.   ![drei Punkte](/help/assets/assets/figma-v2-plugin.png)

1. [Optional] Klicken Sie auf **[!UICONTROL Nach Updates suchen]**. Die im aktuellen Figma-Dokument verwendeten Assets werden mit den in AEM vorhandenen Assets verglichen. Alle Aktualisierungen werden in einem separaten Fenster aufgelistet. Klicken Sie **[!UICONTROL Aktualisieren]**, um das aktualisierte Asset von AEM in Ihr Figma-Dokument zu übernehmen.

Sobald Ihr Figma-Design fertig ist, können Sie [das Asset in das AEM Assets-Repository exportieren](#export-figma-design-to-aem-assets-folder).

## Exportieren von Assets in das [!DNL AEM Assets]-Repository{#export-figma-design-to-aem-assets-folder}

[Greifen Sie auf das Panel [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]](#access-aem-assets-connector) in Ihrer [!DNL Figma]-Design-Benutzeroberfläche zu und führen Sie die folgenden Schritte aus, um Ihr Design in das [!DNL AEM Assets]-Repository zu exportieren:

1. Navigieren Sie zum Zielordner, in dem Sie Ihr [!DNL Figma]-Design speichern möchten. Wenn Sie sich bereits in einem Ordner befinden, klicken Sie auf „Weitere Optionen“ (![drei Punkte](/help/assets/assets/three-dots.svg)) im Ordnerpfad, um einen anderen Zielordner auszuwählen.
1. Optional: Gruppieren Sie Assets auf der Arbeitsfläche, um sie als eine Einheit zum Hochladen in Ihren Ordner auszuwählen.
1. Klicken Sie auf ![Datei-Upload](/help/assets/assets/upload-icon.svg) **[!UICONTROL Hochladen]**, um das Dialogfeld **[!UICONTROL Asset hochladen]** anzuzeigen.
1. Wählen Sie im Dialogfeld entweder **[!UICONTROL Ausgewähltes Element]** oder **[!UICONTROL Seite]** aus, geben Sie einen Datei- oder Seitennamen an, definieren Sie eine Exportkonfiguration und klicken Sie auf **[!UICONTROL Hochladen]**, um das ausgewählte Asset oder das gesamte Design in den Zielordner hochzuladen.

   Die Exportkonfiguration umfasst das Dateiformat, die Skalierung und die Qualität. Wenn Sie beispielsweise JPG als Dateiformat auswählen, können Sie auch die Bildgröße und -qualität definieren. Wenn Sie PNG als Dateiformat auswählen, können Sie auch die Bildgröße definieren.   ![Hochladen des Figma-Designs](/help/assets/assets/upload-figma-design.png)


## Häufig gestellte Fragen {#frequently-asked-questions-aem-assets-figma-integration}

### Was ermöglicht die Integration von AEM Assets mit Figma Designern? {#aem-assets-figma-integration-overview}

Die Integration von AEM Assets mit Figma ermöglicht es Designern, direkt von der Figma-Benutzeroberfläche aus auf in Adobe Experience Manager gespeicherte Assets zuzugreifen, ohne zwischen Tools wechseln zu müssen. Designer können Bilder, Videos, animierte Dateien und Vektoren aus AEM Assets suchen und in die Figma-Arbeitsfläche importieren und fertige oder bearbeitete Designs in unterstützten Formaten zurück in das AEM Assets-Repository exportieren. Die Integration ist nativ und erfordert keine Connectoren von Drittanbietern, die über den in der Figma-Community verfügbaren Adobe Experience Manager AEM Assets-Connector hinausgehen.

### Was sind die Voraussetzungen für die Integration von AEM Assets mit Figma? {#aem-assets-figma-prerequisites}

Die Integration von AEM Assets mit Figma erfordert zwei Voraussetzungen: eine AEM-Mindestversion von 19149 und gültige Lizenzen für AEM Assets und Figma. Beide Bedingungen müssen erfüllt sein, bevor der Zugriff auf den Adobe Experience Manager AEM Assets-Connector und dessen Verwendung in Figma möglich sind. Wenn nach der Anmeldung bei der AEM-Umgebung während des Setups eine Netzwerkfehlermeldung angezeigt wird, wenden Sie sich an den Adobe-Support, um Hilfe zu erhalten.

### Wie greife ich in Figma auf den Adobe Experience Manager AEM Assets Connector zu? {#access-aem-assets-connector-figma}

Der Adobe Experience Manager AEM Assets Connector ist auf zwei Arten von Figma aus zugänglich. Klicken Sie auf der Figma **Startseite in der Symbolleiste am unteren Rand der Arbeitsfläche auf „Aktionen**, suchen Sie im Dialogfeld nach Adobe Experience Manager AEM Assets Connector und wählen Sie diesen aus, um das Connector-Bedienfeld zu öffnen. Alternativ können Sie den Connector direkt über die Figma Community-Seite aufrufen, auf **Öffnen Sie in** klicken, eine aktuelle Datei auswählen oder eine neue Datei erstellen und auf **Ausführen** klicken, um das Connector-Panel zu starten.

### Welche Dateiformate können aus AEM Assets in Figma importiert werden? {#aem-assets-figma-import-formats}

Folgende Dateiformate werden für den Import von AEM Assets in Figma unterstützt: Bild-Assets im JPEG- und PNG-Format, Videodateien im MP4-, MOV- und WebM-Format, animierte Dateien im GIF-Format und Vektordateien im SVG-Format. Assets in diesen Formaten kann im Adobe Experience Manager AEM Assets Connector-Bedienfeld durchsucht und direkt auf die Figma-Arbeitsfläche platziert werden, indem Sie das Asset ziehen und ablegen oder indem Sie das Asset auswählen und auf Auswählen klicken.

### Wie importiere ich ein Asset aus AEM Assets in meine Figma-Arbeitsfläche? {#import-aem-assets-figma-canvas}

Um ein Asset aus AEM Assets in Figma zu importieren, öffnen Sie das Adobe Experience Manager AEM Assets-Anschlussfeld in der Figma-Design-Oberfläche. Suchen Sie mithilfe von Content Advisor im Connector-Bedienfeld nach dem Asset. Sobald Sie das Asset gefunden haben, ziehen Sie es auf die Arbeitsfläche oder wählen Sie das Asset aus und klicken Sie auf **Auswählen**, um es auf der Arbeitsfläche zu platzieren. Um zu Ordnern innerhalb des Repositorys zu navigieren, klicken Sie auf das Drei-Punkte-Symbol im Ordnerpfad, um übergeordnete und untergeordnete Ordner in der aktuellen Hierarchie anzuzeigen und darin zu navigieren.

### Wie kann ich überprüfen, ob die in meinem Figma-Dokument verwendeten AEM Assets aktualisiert wurden? {#check-aem-assets-updates-figma}

Der Adobe Experience Manager AEM Assets-Connector in Figma enthält eine Option **Nach Updates suchen** mit der Assets, die derzeit im geöffneten Figma-Dokument verwendet werden, mit ihren Versionen in AEM Assets verglichen werden. Öffnen Sie dazu das Connector-Panel und klicken Sie auf **Nach Updates suchen**. Alle Assets, die in AEM aktualisiert wurden, werden in einem separaten Fenster aufgeführt. Klicken Sie **Aktualisieren**, um die neueste Version jedes aktualisierten Assets aus AEM in das Figma-Dokument zu ziehen.

### Welche Dateiformate werden beim Exportieren eines Figma-Designs nach AEM Assets unterstützt? {#figma-export-aem-assets-formats}

Beim Exportieren eines Figma-Designs in das AEM Assets-Repository werden vier Dateiformate unterstützt: PNG, PDF, JPG und SVG. Die Exportkonfiguration ermöglicht auch die Definition zusätzlicher Einstellungen je nach ausgewähltem Format. Für JPG-Exporte können Bildgröße und -qualität angegeben werden. Für PNG-Exporte kann Bildgröße definiert werden. Diese Einstellungen werden während des Exportvorgangs im Dialogfeld Asset hochladen konfiguriert.

### Wie exportiere ich einen Figma-Entwurf in das AEM Assets-Repository? {#export-figma-design-aem-assets}

Um ein Figma-Design in AEM Assets zu exportieren, öffnen Sie das Adobe Experience Manager AEM Assets-Connector-Bedienfeld in Figma und navigieren Sie zum Zielordner im AEM Assets-Repository. Klicken Sie auf das Symbol Hochladen , um das Dialogfeld Asset hochladen zu öffnen. Wählen Sie im Dialogfeld entweder Ausgewähltes Element zum Hochladen eines bestimmten Assets oder Seite aus, um die gesamte Design-Seite hochzuladen, geben Sie einen Datei- oder Seitennamen an, definieren Sie die Exportkonfiguration (einschließlich Format, Skalierung und Qualität) und klicken Sie auf Hochladen . Der Entwurf wird im ausgewählten AEM Assets-Zielordner gespeichert.

### Kann ich Assets in Figma gruppieren, bevor ich sie nach AEM Assets exportiere? {#group-assets-figma-export-aem}

Figma-Designs können auf der Arbeitsfläche gruppiert werden, bevor sie in das AEM Assets-Repository exportiert werden. Durch das Gruppieren von Assets können sie als einzelne Einheit ausgewählt und in einem Vorgang zusammen in den Zielordner hochgeladen werden. Öffnen Sie nach der Gruppierung das Bedienfeld Adobe Experience Manager AEM Assets-Connector , navigieren Sie zum Zielordner, klicken Sie auf Hochladen , wählen Sie die gruppierten Elemente als das ausgewählte Element im Dialogfeld Asset hochladen aus, konfigurieren Sie die Exporteinstellungen und klicken Sie auf Hochladen .

### Wie kann ich in Figma durch Ordner im AEM Assets-Repository navigieren? {#navigate-aem-folders-figma}

Die Ordnernavigation innerhalb des AEM Assets-Repositorys ist direkt im Adobe Experience Manager AEM Assets-Connector-Bedienfeld in Figma verfügbar. Klicken Sie auf das Dreipunkt-Symbol im Ordnerpfad, um alle übergeordneten und untergeordneten Ordner in der aktuellen Hierarchie anzuzeigen. Wählen Sie einen beliebigen Ordner aus der Liste aus, um zu diesem Speicherort zu navigieren. Klicken Sie beim Exportieren eines Designs in einen anderen Zielordner auf Weitere Optionen im Ordnerpfad, um einen alternativen Ordner im AEM Assets-Repository auszuwählen.


**Siehe auch**

* [Assets übersetzen](/help/assets/translate-assets.md)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](/help/assets/file-format-support.md)
* [Suchen von Assets](/help/assets/search-assets.md)
* [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](/help/assets/asset-reports.md)
* [Metadatenschemata](/help/assets/metadata-schemas.md)
* [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)
* [Verwalten von Metadaten](/help/assets/manage-metadata.md)
* [Verwalten von Dynamic Media-Vorlagen](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Verwalten von Berichten](/help/assets/manage-reports-assets-view.md)
* [Suchfacetten](/help/assets/search-facets.md)
* [Verwalten von Sammlungen](/help/assets/manage-collections.md)
* [Massenimport von Metadaten](/help/assets/metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

