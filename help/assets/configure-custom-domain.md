---
title: Benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren
description: Erfahren Sie, wie Sie in Adobe Cloud Manager eine benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren.
role: null
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 1%

---


# Benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren{#configure-custom-domain}

In Adobe Cloud Manager können Sie Ihre Website durch Hinzufügen einer benutzerdefinierten Domäne hervorheben. Während AEM as a Cloud Service mit einer Standarddomäne geliefert wird, können Sie sie entsprechend Ihren Anforderungen anpassen.
<!-- For example, AEM sites can use `sites.custom_domain.com`, and the AEM publish domain can be accessed via `assets.custom_domain.com`. Additionally, getting an SSL certificate for assets.pmi.com with a SAN entry for `delivery.custom_domain.com` improves security and trustworthiness. -->

## Vorbereitung

* Sie müssen über ein TLS- oder SSL-Zertifikat mit mehreren SAN (Subject Alternative Name) verfügen.
* Das SSL-Zertifikat sollte über separate SANs für das Zertifikat verfügen, das für die Veröffentlichungsstufe in derselben Domäne zugeordnet ist.
* Die Zertifikatrichtlinie muss entweder der Extended Validation (EV) oder der Organisationsvalidierung (OV) und nicht der Richtlinie Domain Validation (DV) entsprechen.


## Benutzerdefinierte Domäne hinzufügen

Gehen Sie wie folgt vor, um eine benutzerdefinierte Domäne für die Veröffentlichungsstufe zu konfigurieren:

1. Navigieren Sie zu **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Programmübersicht]** > **[!UICONTROL SSL-Zertifikate]**und fügen Sie Ihr SSL-Zertifikat hinzu.
   ![image](/help/assets/assets/ssl-certificate.png)
Erfahren Sie, wie Sie [SSL-Zertifikat](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate.html?lang=en) in Adobe Cloud Manager.

1. Fügen Sie nach dem Hinzufügen des SSL-Zertifikats eine benutzerdefinierte Domäne hinzu. Klicks **[!UICONTROL Domäneneinstellungen]** und geben Sie die benutzerdefinierte Domäne für die **[!UICONTROL Veröffentlichungsdienst]** -Option.
   <br> Weitere Informationen [Benutzerdefinierte Domäne](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name.html?lang=en).

1. Fügen Sie Ihrem DNS-Eintrag 2 CNAME-Einträge hinzu, die den Veröffentlichungsdomänen entsprechen.
   <br> Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.

1. Protokollieren Sie einen Support-Fall, um die Konfiguration der benutzerdefinierten Domäne zu erleichtern und sicherzustellen, dass sie zur Bereitstellungsebene weitergeleitet wird.

>[!NOTE]
>
> Stellen Sie sicher, dass Sie die benutzerdefinierte Domäne zur Liste der zulässigen Umleitungs-URLs im IMS-Client für die Asset-Auswahl hinzufügen.<br>Koordinieren Sie diese Aufgabe mit dem entsprechenden Adobe-Team, indem Sie die benutzerdefinierte Domain-Zeichenfolge angeben.
