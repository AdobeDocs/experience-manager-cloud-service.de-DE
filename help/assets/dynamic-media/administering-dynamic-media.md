---
title: Einrichten von Dynamic Media
description: Zum Einrichten von Dynamic Media müssen Sie Dynamic Media konfigurieren und Bild- sowie Viewer-Vorgaben verwalten.
contentOwner: Rick Brough
feature: Configuration,Viewer Presets,Image Presets,Dynamic Media
role: Admin,User
exl-id: 83b70b17-7ee3-41cb-be90-c92ca161660e
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 87%

---

# Einrichten von Dynamic Media {#setting-up-dynamic-media}

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

{{work-with-dynamic-media}}

Mithilfe von [Dynamic Media](https://business.adobe.com/de/products/experience-manager/assets/dynamic-media.html) können Sie Assets verwalten, indem Sie umfassende visuelle Merchandising- und Marketing-Assets bei Bedarf übermitteln, und zwar automatisch skaliert für die Verwendung im Web, auf Mobilgeräten und in Social Media. Anhand eines Sets von Assets aus Primärquellen können Sie mit Dynamic Media mehrere Varianten ansprechender Inhalte in Echtzeit über das globale, skalierbare und leistungsoptimierte Netzwerk generieren und bereitstellen.

<!-- OBSOLETE UNTIL THE INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE

>[!NOTE]
>
>This documentation describes Dynamic Media capabilites, which are integrated directly into [!DNL Experience Manager]. If you are using Dynamic Media Classic (previously called Scene7) integrated into [!DNL Experience Manager], see [Dynamic Media Classic integration documentation](/help/sites-cloud/administering/integrating-scene7.md).
>
>See [Dual Use Scenario](/help/sites-cloud/administering/integrating-scene7.md#dual-use-scenario) for times when you may want to use [!DNL Experience Manager] integrated with Dynamic Media Classic along with Dynamic Media.

-->

Wenn Sie Dynamic Media verwalten, sind für Sie die folgenden Themen interessant:

* [Konfigurieren von Dynamic Media](config-dm.md)
* [Verwalten von Bildvorgaben](managing-image-presets.md)
* [Verwalten von Viewer-Vorgaben](managing-viewer-presets.md)
* [Fehlerbehebung bei Dynamic Media](troubleshoot-dm.md)

Weitere Informationen finden Sie in den folgenden Themen:

* [Videokodierung und Videoprofile](video-profiles.md)
* [Bildprofile](image-profiles.md)

>[!NOTE]
>
>**Beachten Sie Folgendes, wenn Sie ein Upgrade durchführen:**
>
>* Sobald Sie Adobe [!DNL Experience Manager] eingerichtet haben und verwenden, ist Dynamic Media für jedes Asset, das Sie hochladen, automatisch aktiviert (sofern nicht ausdrücklich vom Systemadministrator deaktiviert). Wenn Sie sich in einer aktualisierten Instanz von [!DNL Experience Manager] befinden und Dynamic Media noch nicht verwendet haben, müssen Sie die Assets wahrscheinlich erneut verarbeiten, um Dynamic Media für sie verwenden zu können. Siehe [Neuverarbeitung von Assets in einem Ordner](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).
