---
title: Benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren
description: Erfahren Sie, wie Sie in Adobe Cloud Manager eine benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren.
source-git-commit: f6c0e8e5c1d7391011ccad5aa2bad4a6ab7d10c3
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 6%

---


# Benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren{#configure-custom-domain}

In Adobe Cloud Manager können Sie Ihre Website durch Hinzufügen einer benutzerdefinierten Domäne auffallen lassen. AEM as a Cloud Service verfügt zwar über eine Standarddomäne, Sie können sie jedoch nach Bedarf anpassen.

## Vorbereitung

* Sie müssen über ein TLS- oder SSL-Zertifikat mit mehreren SAN (Subject Alternative Name) verfügen.
* Das SSL-Zertifikat sollte über separate SANs für das Zertifikat verfügen, das für die Veröffentlichungsstufe in derselben Domäne zugeordnet ist.
* Die Zertifikatrichtlinie muss entweder der Extended Validation (EV) oder der Organisationsvalidierung (OV) und nicht der Richtlinie Domain Validation (DV) entsprechen.


## Benutzerdefinierte Domäne hinzufügen

Gehen Sie wie folgt vor, um eine benutzerdefinierte Domäne für die Veröffentlichungsstufe zu konfigurieren:

1. Wechseln Sie zu **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Programmübersicht]** > **[!UICONTROL SSL-Zertifikate]** und fügen Sie Ihr SSL-Zertifikat hinzu.
   ![image](/help/assets/assets/ssl-certificate.png)
Erfahren Sie, wie Sie in Adobe Cloud Manager das [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) hinzufügen.

1. Fügen Sie nach dem Hinzufügen des SSL-Zertifikats eine benutzerdefinierte Domäne hinzu. Klicken Sie auf **[!UICONTROL Domäneneinstellungen]** und geben Sie die benutzerdefinierte Domäne für die Option **[!UICONTROL Publish-Dienst]** an.
Erfahren Sie mehr über [benutzerdefinierte Domäne](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Fügen Sie 2 [CNAME-Einträge](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) in Ihren DNS-Eintrag hinzu, die den Veröffentlichungsdomänen entsprechen.
Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.

1. Protokollieren Sie einen Support-Fall, um die Konfiguration der benutzerdefinierten Domäne zu erleichtern und sicherzustellen, dass sie zur Bereitstellungsebene weitergeleitet wird.

>[!NOTE]
>
> Stellen Sie sicher, dass Sie die benutzerdefinierte Domäne zur Liste der zulässigen Umleitungs-URLs im IMS-Client für die Asset-Auswahl hinzufügen.<br>Koordinieren Sie diese Aufgabe mit dem entsprechenden Adobe-Team, indem Sie die benutzerdefinierte Domain-Zeichenfolge angeben.
