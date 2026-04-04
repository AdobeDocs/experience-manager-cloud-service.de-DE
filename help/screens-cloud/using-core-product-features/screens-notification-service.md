---
title: Screens-Benachrichtigungsdienst in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie den Benachrichtigungsdienst in Screens as a Cloud Service konfigurieren.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: 81f85045212ca6fd92f2b665aeceaa0d4b92318c
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 81%

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

Wenn Sie die Berichtszeit auf 5 Uhr und die Ping-Zeitüberschreitung auf 1 Stunde festlegen und Ihr Screens-Gerät nicht zwischen 4 :00 und 5 :00 pingt, erhalten Sie eine E-Mail-Benachrichtigung, die die Geräteinaktivität bestätigt.
