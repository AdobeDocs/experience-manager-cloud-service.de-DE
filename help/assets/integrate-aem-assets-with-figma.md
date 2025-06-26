---
title: Integration  [!DNL AEM Assets] mit [!DNL Figma].
description: Erfahren Sie, wie  [!DNL AEM Assets]  mit  [!DNL Figma]  können, um auf die Assets Ihres Unternehmens in Ihrem Design [!DNL Figma] Workflow zuzugreifen und sie zu verwenden.
hide: false
role: User
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: 2644c849df32af14c70e686a803b690996812046
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 11%

---

# Integration von [!DNL AEM Assets] mit [!DNL Figma]{#integrate-aem-assets-with-figma}

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

[!DNL AEM Assets] lässt sich nativ mit [!DNL Figma] integrieren, wodurch Designer direkt über die [!DNL Figma]-Benutzeroberfläche auf die in [!DNL AEM Assets] gespeicherten Assets zugreifen können. Sie können verwaltete Inhalte in [!DNL AEM Assets] in der [!DNL Figma] Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte im [!DNL AEM Assets]-Repository speichern.

## Bevor Sie beginnen{#prerequisites-for-aem-assets-and-figma-integration}

* Die mindestens erforderliche AEM-Release-Version ist `19149`.

* Sie müssen über gültige [!DNL AEM Assets]- und [!DNL Figma] verfügen, um [!DNL AEM Assets] mit [!DNL Figma] integrieren zu können.

## Zugriff auf den [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]{#access-aem-assets-connector}

Führen Sie die folgenden Schritte aus, um auf den [!UICONTROL Adobe Experience Manager (AEM) Assets Connector zuzugreifen]:

1. Klicken Sie auf Ihrer [!DNL Figma] **[!UICONTROL -Startseite in der]** unten auf der Arbeitsfläche auf „Aktionen“ und suchen Sie in der Suchleiste im Dialogfeld nach [!DNL Adobe Experience Manager (AEM) Assets Connector].
1. Wählen Sie [!DNL Adobe Experience Manager (AEM) Assets Connector] aus, um das [!DNL Adobe Experience Manager (AEM) Assets Connector] anzuzeigen. [Assets  [!DNL AEM]  diesem Bedienfeld in  [!DNL Figma] /](#import-aem-assets-into-figma-workflow) importieren.
   ![Aktionen](/help/assets/assets/actions-on-figma.png)
Alternativ können Sie auf die in [!DNL Figma] Community verfügbaren [[!DNL Adobe Experience Manager (AEM) Assets Connector]](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector) zugreifen, auf **[!UICONTROL Öffnen in…]** klicken, eine aktuelle Datei auswählen oder eine neue Datei erstellen und auf **[!UICONTROL Ausführen]** klicken, um auf das [!DNL Adobe Experience Manager (AEM) Assets Connector] zuzugreifen.
   ![plugin-page-on-figma-community](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [Kontaktieren Sie den Adobe](https://helpx.adobe.com/de/contact.html)**[!UICONTROL Support, wenn nach der Anmeldung in Ihrer [!DNL AEM]-Umgebung]** Meldung „Netzwerkfehler“ angezeigt wird.

## [!DNL AEM] Assets in [!DNL Figma] Arbeitsfläche importieren{#import-aem-assets-into-figma-workflow}

[Greifen Sie auf das Bedienfeld [!UICONTROL Adobe Experience Manager (AEM] Assets Connector](#access-aem-assets-connector) in Ihrer [!DNL Figma]-Design-Oberfläche zu und führen Sie die folgenden Schritte aus:

1. Suchen nach Assets im Bedienfeld [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]. Weitere Informationen finden Sie unter [Verwenden des Asset-Wählers](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector).

1. Ziehen Sie das Asset auf die Arbeitsfläche oder wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Auswählen]**, um das Asset auf die Arbeitsfläche zu bringen.

1. Klicken Sie ![drei Punkte](/help/assets/assets/three-dots.svg) im Ordnerpfad, um alle übergeordneten und untergeordneten Ordner in der aktuellen Hierarchie anzuzeigen. Wählen Sie einen Ordner aus, um zu diesem Speicherort zu navigieren.
   ![drei Punkte](/help/assets/assets/assets-folder-structure.png)

Sobald Ihr Figma-Design fertig ist, können Sie [das Asset in das AEM Assets-Repository exportieren](#export-figma-design-to-aem-assets-folder).

## Exportieren von Assets in [!DNL AEM Assets] Repository{#export-figma-design-to-aem-assets-folder}

[Greifen Sie auf das Bedienfeld [!UICONTROL Adobe Experience Manager (AEM] Assets Connector](#access-aem-assets-connector) in Ihrer [!DNL Figma] Design-Benutzeroberfläche zu und führen Sie die folgenden Schritte aus, um Ihr Design in das [!DNL AEM Assets]-Repository zu exportieren:

1. Navigieren Sie zum Zielordner, in dem Sie Ihr [!DNL Figma] speichern möchten. Wenn Sie sich bereits in einem Ordner befinden, klicken Sie auf Weitere Optionen (![drei Punkte](/help/assets/assets/three-dots.svg)) im Ordnerpfad, um einen anderen Zielordner auszuwählen.
1. Optional: Gruppieren Sie Assets auf der Arbeitsfläche, um sie als eine Einheit zum Hochladen in Ihren Ordner auszuwählen.
1. Klicken Sie auf ![Datei-](/help/assets/assets/upload-icon.svg)**[!UICONTROL Hochladen]**, um das Dialogfeld **[!UICONTROL Asset hochladen]** anzuzeigen.
1. Geben Sie im Dialogfeld einen Dateinamen an, wählen Sie ein Dateiformat aus, wählen Sie entweder **[!UICONTROL Ausgewähltes Element]** oder **[!UICONTROL Seite]** und klicken Sie auf **[!UICONTROL Hochladen]**, um das ausgewählte Asset oder das gesamte Design in den Zielordner hochzuladen.
   ![Figma-Design hochladen](/help/assets/assets/upload-figma-design.png)

## Wichtige Hinweise{#Limitations-of-using-aem-assets-into-figma}

Diese Integration weist derzeit die folgenden Einschränkungen auf:

* Für den Import von [!DNL AEM]-Assets in Figma werden die Formate **JPEG**, **PNG** unterstützt.
* Für den Export von Designs von [!DNL Figma] nach [!DNL AEM Assets] werden folgende Formate **PNG**, **PDF**, **JPG**, **SVG**.
