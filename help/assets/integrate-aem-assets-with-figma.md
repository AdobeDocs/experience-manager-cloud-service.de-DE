---
title: Integrieren Sie [!DNL AEM Assets] mit [!DNL Figma].
description: Erfahren Sie, wie Sie [!DNL AEM Assets] mit [!DNL Figma] integrieren, um auf die Assets Ihres Unternehmens in Ihrem  [!DNL Figma] -Design-Workflow zuzugreifen und sie zu verwenden.
hide: false
role: User
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: 3603a98dfee62db49f3201c8d75aa8eee4909cc1
workflow-type: ht
source-wordcount: '450'
ht-degree: 100%

---


# Integration von [!DNL AEM Assets] mit [!DNL Figma]{#integrate-aem-assets-with-figma}

Dank der nativen Integration von [!DNL AEM Assets] mit [!DNL Figma] können Entwickelnde über die [!DNL Figma]-Benutzeroberfläche direkt auf die in [!DNL AEM Assets] gespeicherten Assets zugreifen. Sie können in [!DNL AEM Assets] verwaltete Inhalte auf der [!DNL Figma]-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem [!DNL AEM Assets]-Repository speichern.

## Voraussetzungen{#prerequisites-for-aem-assets-and-figma-integration}

* Die mindestens erforderliche AEM-Version ist `19149`.

* Sie müssen über gültige [!DNL AEM Assets]- und [!DNL Figma]-Lizenzen verfügen, um [!DNL AEM Assets] mit [!DNL Figma] integrieren zu können.

## Zugriff auf den [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]{#access-aem-assets-connector}

Führen Sie die folgenden Schritte aus, um auf den [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] zuzugreifen:

1. Klicken Sie auf Ihrer [!DNL Figma]-Startseite in der Symbolleiste unten auf der Arbeitsfläche auf **[!UICONTROL Aktionen]** und suchen Sie in der Suchleiste im Dialogfeld nach [!DNL Adobe Experience Manager (AEM) Assets Connector].
1. Wählen Sie [!DNL Adobe Experience Manager (AEM) Assets Connector] aus, um das Panel [!DNL Adobe Experience Manager (AEM) Assets Connector] anzuzeigen. [Importieren Sie [!DNL AEM] Assets über dieses Panel in Ihre [!DNL Figma] Arbeitsfläche](#import-aem-assets-into-figma-workflow).
   ![Aktionen](/help/assets/assets/actions-on-figma.png)
Alternativ können Sie über die [!DNL Figma]-Community auf [[!DNL Adobe Experience Manager (AEM) Assets Connector]](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector) zugreifen, indem Sie auf **[!UICONTROL In … öffnen]** klicken, eine kürzlich erstellte Datei auswählen oder eine neue Datei erstellen und auf **[!UICONTROL Ausführen]** klicken, um das Panel [!DNL Adobe Experience Manager (AEM) Assets Connector] aufzurufen.
   ![plugin-page-on-figma-community](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [Wenden Sie sich an den Adobe-Support](https://helpx.adobe.com/de/contact.html), wenn Ihnen nach der Anmeldung bei Ihrer [!DNL AEM]-Umgebung eine Meldung zu einem **[!UICONTROL Netzwerkfehler]** angezeigt wird.

## Importieren von [!DNL AEM]-Assets in die [!DNL Figma]-Arbeitsfläche{#import-aem-assets-into-figma-workflow}

[Greifen Sie auf das Panel [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]](#access-aem-assets-connector) in Ihrer [!DNL Figma]-Design-Benutzeroberfläche zu und führen Sie die folgenden Schritte aus:

1. Suchen Sie im Panel [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] nach Assets. Weitere Informationen finden Sie unter [Verwenden des Asset-Wählers](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector).

1. Ziehen Sie das Asset per Drag-and-Drop auf die Arbeitsfläche oder wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Auswählen]**, damit das Asset auf der Arbeitsfläche angezeigt wird.

1. Klicken Sie auf ![drei Punkte](/help/assets/assets/three-dots.svg) im Ordnerpfad, um alle übergeordneten und untergeordneten Ordner in der aktuellen Hierarchie anzuzeigen. Wählen Sie einen Ordner aus, um zu diesem Speicherort zu navigieren.
   ![drei Punkte](/help/assets/assets/assets-folder-structure.png)

Sobald Ihr Figma-Design fertig ist, können Sie [das Asset in das AEM Assets-Repository exportieren](#export-figma-design-to-aem-assets-folder).

## Exportieren von Assets in das [!DNL AEM Assets]-Repository{#export-figma-design-to-aem-assets-folder}

[Greifen Sie auf das Panel [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]](#access-aem-assets-connector) in Ihrer [!DNL Figma]-Design-Benutzeroberfläche zu und führen Sie die folgenden Schritte aus, um Ihr Design in das [!DNL AEM Assets]-Repository zu exportieren:

1. Navigieren Sie zum Zielordner, in dem Sie Ihr [!DNL Figma]-Design speichern möchten. Wenn Sie sich bereits in einem Ordner befinden, klicken Sie auf „Weitere Optionen“ (![drei Punkte](/help/assets/assets/three-dots.svg)) im Ordnerpfad, um einen anderen Zielordner auszuwählen.
1. Optional: Gruppieren Sie Assets auf der Arbeitsfläche, um sie als eine Einheit zum Hochladen in Ihren Ordner auszuwählen.
1. Klicken Sie auf ![Datei-Upload](/help/assets/assets/upload-icon.svg) **[!UICONTROL Hochladen]**, um das Dialogfeld **[!UICONTROL Asset hochladen]** anzuzeigen.
1. Geben Sie im Dialogfeld einen Dateinamen an, wählen Sie ein Dateiformat sowie entweder **[!UICONTROL Ausgewähltes Element]** oder **[!UICONTROL Seite]** aus und klicken Sie auf **[!UICONTROL Hochladen]**, um das ausgewählte Asset oder das gesamte Design in den Zielordner hochzuladen.
   ![Hochladen des Figma-Designs](/help/assets/assets/upload-figma-design.png)

## Wichtige Hinweise{#Limitations-of-using-aem-assets-into-figma}

Für diese Integration gelten folgende Einschränkungen:

* Beim Import von [!DNL AEM]-Assets in Figma werden die Formate **JPEG** und **PNG** unterstützt.
* Beim Export von Designs von [!DNL Figma] nach [!DNL AEM Assets] werden die Formate **PNG**, **PDF**, **JPG** und **SVG** unterstützt.
