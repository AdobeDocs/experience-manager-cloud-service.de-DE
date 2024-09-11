---
title: Benutzerdefinierte Domäne für die Publish-Ebene konfigurieren
description: Erfahren Sie, wie Sie eine benutzerdefinierte Domäne für die Veröffentlichungsstufe in Adobe Cloud Manager konfigurieren.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 8a10634e413ea5c66845dfffa7396a4554a5b3ca
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 6%

---

# Benutzerdefinierte Domäne für die Veröffentlichungsstufe konfigurieren{#configure-custom-domain}

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
Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.

1. Protokollieren Sie einen Support-Fall, um die Konfiguration der benutzerdefinierten Domäne zu erleichtern und sicherzustellen, dass sie zur Bereitstellungsebene weitergeleitet wird.

>[!NOTE]
>
>Fügen Sie die benutzerdefinierte Domäne zur Liste der zulässigen Umleitungs-URLs hinzu. Die Liste befindet sich im IMS-Client für die Asset-Auswahl.<br>Koordinieren Sie diese Aufgabe mit dem entsprechenden Adobe-Team, indem Sie die benutzerdefinierte Domain-Zeichenfolge angeben.
