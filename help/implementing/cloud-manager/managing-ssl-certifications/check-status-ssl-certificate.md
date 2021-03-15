---
title: Überprüfen des Status eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
description: Überprüfen des Status eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: ddee11fdfa8cadfcd63472fd3c94cd8af555c856
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 69%

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

Kunden mit Umgebung, die bereits vorhandene CDN-Konfigurationen für IP-Zulassungslisten, SSL-Zertifikate oder benutzerdefinierte Domänennamen enthalten, sehen die folgende Meldung auf der Detailseite **IP-Zulassungsliste** und **Umgebung**.

![](/help/implementing/cloud-manager/assets/ip-allow-list-1.png)

>[!NOTE]
>Um die bereits vorhandenen Konfigurationen anzuzeigen und zu verwalten, müssen sie über die Benutzeroberfläche hinzugefügt werden, wie in der folgenden Abbildung dargestellt.

![](/help/implementing/cloud-manager/assets/ip-allow-list-2.png)