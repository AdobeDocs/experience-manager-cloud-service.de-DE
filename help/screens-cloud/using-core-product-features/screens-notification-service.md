---
title: Screens-Benachrichtigungsdienst in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie den Benachrichtigungsdienst in Screens as a Cloud Service konfigurieren.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

---

# Screens-Benachrichtigungsdienst {#notification-service}

## Einführung {#introduction}

### Überblick

Der AEM Screens-Benachrichtigungsdienst bietet Admins die Möglichkeit, einen Bericht mit einer Liste aller AEM Screens-Player zu erhalten, die in einem konfigurierbaren Zeitraum nicht für eine E-Mail gepingt haben.

### Vorgehensweise bei der Konfiguration

In der AEM Screens-Cloud können Kundinnen und Kunden einen Bericht zum Status der Geräteinaktivität anfordern, indem sie ein Support-Ticket mit folgenden Informationen erstellen:

* Kundenname
* IMS-Organisations-ID
* Häufigkeit: Geben Sie eine Zeit oder eine Häufigkeit in Stunden (z. B. 1) an, zu der der Service E-Mails senden soll.
* Ping-Timeout: Gibt das Intervall in Minuten an, nach dem ein Gerät als nicht erreichbar betrachtet werden soll.
* E-Mail-ID(s) : E-Mail-ID(s), an die der Bericht gesendet wird

>[!NOTE]
>Bei E-Mails wird der Player nur dann gemeldet, wenn das Gerät zum Zeitpunkt der Generierung der E-Mail keinen Ping für die angegebene Ping-Zeitüberschreitung durchgeführt hat.

### Anwendungsbeispiel

Wenn Sie die Berichtszeit auf 5:00 Uhr und das Ping-Timeout auf 1 Stunde setzen, erhalten Sie, falls Ihr Screens-Gerät zwischen 4:00 Uhr und 5:00 Uhr nicht pingt, eine E-Mail-Benachrichtigung, mit der die Inaktivität des Geräts bestätigt wird.
