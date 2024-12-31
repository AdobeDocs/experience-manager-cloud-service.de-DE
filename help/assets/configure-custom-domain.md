---
title: Konfigurieren einer benutzerdefinierten Domain für die Veröffentlichungsebene
description: Erfahren Sie, wie Sie eine benutzerdefinierte Domain für die Veröffentlichungsebene in Adobe Cloud Manager konfigurieren.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 100%

---

# Konfigurieren einer benutzerdefinierten Domain für die Veröffentlichungsebene{#configure-custom-domain}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

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
