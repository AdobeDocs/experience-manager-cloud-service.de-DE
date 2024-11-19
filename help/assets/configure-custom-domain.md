---
title: Benutzerdefinierte Domäne für die Publish-Ebene konfigurieren
description: Erfahren Sie, wie Sie eine benutzerdefinierte Domäne für die Veröffentlichungsstufe in Adobe Cloud Manager konfigurieren.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 11%

---

# Benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren{#configure-custom-domain}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch für Dynamic Media mit OpenAPI-Funktionen PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

In Adobe Cloud Manager können Sie Ihre Website durch Hinzufügen einer benutzerdefinierten Domäne auffallen lassen. AEM as a Cloud Service verfügt zwar über eine Standarddomäne, Sie können sie jedoch nach Bedarf anpassen.

## Vorbereitung

* Sie müssen über ein TLS- oder SSL-Zertifikat mit mehreren SAN (Subject Alternative Name) verfügen.
* Das SSL-Zertifikat sollte über separate SANs für das Zertifikat verfügen, das für die Veröffentlichungsstufe in derselben Domäne zugeordnet ist.
* Die Zertifikatrichtlinie muss entweder der Extended Validation (EV) oder der Organisationsvalidierung (OV) und nicht der Richtlinie Domain Validation (DV) entsprechen.


## Benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren

1. Wechseln Sie zu **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Programmübersicht]** > **[!UICONTROL SSL-Zertifikate]** und fügen Sie Ihr SSL-Zertifikat hinzu.
   ![image](/help/assets/assets/ssl-certificate.png)
Erfahren Sie, wie Sie in Adobe Cloud Manager das [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) hinzufügen.

1. Fügen Sie nach dem Hinzufügen des SSL-Zertifikats eine benutzerdefinierte Domäne hinzu. Klicken Sie auf **[!UICONTROL Domäneneinstellungen]** und geben Sie die benutzerdefinierte Domäne für die Option **[!UICONTROL Publish-Dienst]** an.
Erfahren Sie mehr über [benutzerdefinierte Domäne](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Fügen Sie zwei [CNAME-Einträge](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) in Ihrem DNS-Eintrag hinzu, die den Veröffentlichungsdomänen entsprechen.
Die DNS-Überprüfung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.

1. Protokollieren Sie einen Support-Fall, um die Konfiguration der benutzerdefinierten Domäne zu erleichtern und sicherzustellen, dass sie zur Bereitstellungsebene weitergeleitet wird.

>[!NOTE]
>
Fügen Sie die benutzerdefinierte Domäne zur Liste der zulässigen Umleitungs-URLs hinzu. Die Liste befindet sich im IMS-Client für die Asset-Auswahl.<br>Koordinieren Sie diese Aufgabe mit dem entsprechenden Adobe-Team, indem Sie die benutzerdefinierte Domain-Zeichenfolge angeben.
