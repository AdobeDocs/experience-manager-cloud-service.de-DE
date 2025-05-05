---
title: Konfigurieren einer benutzerdefinierten Domain für die Veröffentlichungsebene
description: Erfahren Sie, wie Sie eine benutzerdefinierte Domain für die Veröffentlichungsebene in Adobe Cloud Manager konfigurieren.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 91%

---

# Konfigurieren einer benutzerdefinierten Domain für die Veröffentlichungsebene{#configure-custom-domain}

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
>Das Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch zu Dynamic Media mit OpenAPI-Funktionen als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

In Adobe Cloud Manager können Sie Ihre Website durch das Hinzufügen einer benutzerdefinierten Domain hervorheben. AEM as a Cloud Service verfügt zwar über eine Standard-Domain, Sie können sie aber nach Bedarf anpassen.

## Voraussetzungen

* Sie müssen über ein TLS- oder SSL-Zertifikat mit mehreren Subject Alternative Names (SANs) verfügen.
* Das SSL-Zertifikat sollte über separate SANs für das Zertifikat verfügen, das der Veröffentlichungsebene in derselben Domain zugeordnet ist.
* Die Zertifikatsrichtlinie muss entweder der Richtlinie „Extended Validation“ (EV) oder „Organization Validation“ (OV), aber nicht der Richtlinie „Domain Validation“ (DV) entsprechen.


## Konfigurieren einer benutzerdefinierten Domain für die Veröffentlichungsebene

1. Navigieren Sie zu **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Programmübersicht]** > **[!UICONTROL SSL-Zertifikate]** und fügen Sie Ihr SSL-Zertifikat hinzu.
   ![Bild](/help/assets/assets/ssl-certificate.png)
Erfahren Sie, wie Sie in Adobe Cloud Manager ein [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) hinzufügen.

1. Fügen Sie nach dem Hinzufügen des SSL-Zertifikats eine benutzerdefinierte Domain hinzu. Klicken Sie auf **[!UICONTROL Domain-Einstellungen]** und geben Sie die benutzerdefinierte Domain für die Option **[!UICONTROL Veröffentlichungs-Service]** an.
Erfahren Sie mehr über [benutzerdefinierte Domains](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Fügen Sie zwei [CNAME-Einträge](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) in Ihrem DNS-Eintrag hinzu, die den Veröffentlichungs-Domains entsprechen.
Die DNS-Überprüfung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.

1. Reichen Sie einen Support-Fall ein, um die Konfiguration der benutzerdefinierten Domain zu erleichtern und sicherzustellen, dass sie zur Bereitstellungsebene führt.

>[!NOTE]
>
>Fügen Sie die benutzerdefinierte Domain zur Liste der zulässigen Umleitungs-URLs hinzu. Die Liste befindet sich im IMS-Client für den Asset-Wähler.<br>Stimmen Sie sich zur Durchführung dieser Aufgabe mit dem entsprechenden Adobe-Team ab, indem Sie die Zeichenfolge der benutzerdefinierten Domain bereitstellen.
