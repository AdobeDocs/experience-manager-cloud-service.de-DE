---
title: Reporting in Dynamic Media
description: Erfahren Sie, wie Sie einen Fehlerbericht für Dynamic Media-Bereitstellungs-URLs anfordern, die fehlschlagen.
contentOwner: Rick Brough
feature: Asset Management
role: User
hide: true
hidefromtoc: true
exl-id: 2488f813-df15-4dbb-8747-f827ee5925e1
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 90%

---

# Anfordern eines Fehlerberichts für fehlgeschlagene Dynamic Media-Bereitstellungs-URLs

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

Sie können einen Fehlerbericht anfordern, der Dynamic Media-URLs aufführt, die bei der Bereitstellung fehlgeschlagen sind. Der Bericht ist eine Aggregation von Daten aus bis zu fünf Tagen und im CSV-Format verfügbar. Der Fehlerbericht enthält die folgenden Informationen:

* Fehlgeschlagene Dynamic Media-Bereitstellungs-URL – Eine fehlerhafte URL ist eine von Dynamic Media generierte URL, die bei der Bereitstellung keinen Inhalt erstellen kann.
* Referrer-URL – Die Referrer-URL, von der aus die fehlgeschlagene Bereitstellungs-URL aufgerufen wird.
* Fehleranzahl – Die Anzahl der Ladevorgänge der Versand-URL, die zu einem Fehler führten.

Wenn Sie den Fehlerbericht anfordern, sendet das Adobe Dynamic Media-Team den Bericht im CSV-Format per E-Mail an Sie. Dies umfasst einen Zeitraum von fünf Tagen ab dem Tag, an dem Ihre Anfrage gestellt wurde.

Sie können einen Fehlerbericht einmal monatlich für ein bestimmtes Unternehmen anfordern.

**Anfordern eines Fehlerberichts für fehlgeschlagene Dynamic Media-Bereitstellungs-URLs**

1. Senden Sie eine [E-Mail an reports-dynamic-media@adobe.com senden](mailto:reports-dynamic-media@adobe.com) mit dem Unternehmensnamen, der mit Ihrem Dynamic Media-Konto verknüpft ist.

   Wenn Sie den Unternehmensnamen nicht kennen, lesen Sie die Seite [Dynamic Media-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html?lang=de#configuring-dynamic-media-cloud-services) in **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media-Konfiguration]**. Klicken Sie auf der Seite „Dynamic Media-Konfigurations-Browser“ auf **[!UICONTROL global]**, aktivieren Sie das Kontrollkästchen *[Dynamic_Media_folder_icon]* und wählen Sie dann **[!UICONTROL Bearbeiten]** aus. Sie müssen über Administratorrechte in AEM verfügen, um auf die Seite „Dynamic Media-Konfiguration“ zugreifen zu können.

   ![Zugreifen auf die Seite „Dynamic Media-Konfiguration“](/help/assets/dynamic-media/assets/reporting-accessdmconfig.png)
