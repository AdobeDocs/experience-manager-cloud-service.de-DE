---
title: Überprüfen des Status eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
description: Überprüfen des Status eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
exl-id: 59d81356-2fa9-43db-bfa5-c2896c530eaa
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 75%

---

# Überprüfen des Status eines SSL-Zertifikats {#checking-status-an-ssl-certificate}

Der Status Ihrer SSL-Zertifikate ist auf der SSL-Zertifikatsseite auf einen Blick ersichtlich.

Sie können den Status eines SSL-Zertifikats anhand der folgenden Farbschemata erkennen:

* **Grün**
Zeigt an, dass Ihr Zertifikat mindestens 60 Tage in der Zukunft gültig ist.

* **Orange**
Zeigt an, dass Ihr Zertifikat in weniger als 60 Tagen abläuft. Sie sollten sicherzustellen und planen, Ihr Zertifikat zu erneuern und über die Cloud Manager-Benutzeroberfläche zu ersetzen, um mögliche Website-Zugriffe oder Ausfälle zu vermeiden. Cloud Manager sendet in der Benutzeroberfläche regelmäßige Benachrichtigungen, um Sie über einen bevorstehenden Zertifikatablauf zu informieren.

* **Rot**
Zeigt an, dass Ihr SSL-Zertifikat trotz mehrfacher Benachrichtigungen abgelaufen ist.

## Vorbestehende CDN-Konfigurationen für IP-Zulassungslisten {#pre-existing-cdn}

Kunden mit Umgebungen, die bereits vorhandene CDN-Konfigurationen für IP-Zulassungslisten, SSL-Zertifikate oder benutzerdefinierte Domänennamen enthalten, sehen die folgende Meldung auf der Detailseite **IP-Zulassungsliste** und **Umgebung** . Die auf der Benutzeroberfläche angezeigte Meldung wird ausgeblendet, sobald der Kunde alle bereits vorhandenen Konfigurationen der Umgebung über die Benutzeroberfläche vollständig migriert hat. Es kann ein bis zwei Werktage dauern, bis die Meldung ausgeblendet wird.

>[!NOTE]
>Um die bereits vorhandenen Konfigurationen anzuzeigen und zu verwalten, müssen sie über die Benutzeroberfläche hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) .

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
