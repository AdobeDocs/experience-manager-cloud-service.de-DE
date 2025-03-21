---
title: Aktivieren des Hotlink-Schutzes in Dynamic Media
description: Erfahren sie, wie Sie den Hotlink-Schutz in Dynamic Media aktivieren.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 0198b3a3-173e-46ca-a845-3f58f8eab769
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 88%

---

# Aktivieren des Hotlink-Schutzes in Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

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

Von Hotlinking spricht man, wenn eine Drittanbieter-Website HTML-Code verwendet, um ein Bild von Ihrer Website anzuzeigen. Sie beanspruchen bei jedem Aufruf des Bildes Ihre Bandbreite, da der Browser des Besuchers direkt über Ihren Server darauf zugreift. Der Hotlink-*Schutz* ist eine Methode, um das direkte Verknüpfen anderer Websites mit Bildern, CSS oder JavaScript auf Ihren Web-Seiten zu verhindern. Dadurch können Sie unnötige Bandbreitennutzung in Ihrem Dynamic Media-Konto reduzieren.

[Der Adobe-Support](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=de#home) kann einen Referrer-Filter auf CDN-Ebene konfigurieren. Dadurch wird sichergestellt, dass Dynamic Media-Inhalte nur Websites zur Verfügung gestellt werden, die auf Ihrer Liste der zulässigen Websites für die Domain stehen.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt. Um den Hotlink-Schutz zu aktivieren, muss ein Administrator ein Support-Ticket erstellen, um die Konfigurationsänderung an Ihrem Dynamic Media-Konto anzufordern. Mit der Aktivierung des Hotlink-Schutzes sind keine zusätzlichen Kosten verbunden.
