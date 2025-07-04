---
title: Konfigurieren einer benutzerdefinierten Domain für die Veröffentlichungsebene
description: Erfahren Sie, wie Sie eine benutzerdefinierte Domain für die Veröffentlichungsebene in Adobe Cloud Manager konfigurieren.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---

# Konfigurieren einer benutzerdefinierten Domain für die Veröffentlichungsebene{#configure-custom-domain}

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
