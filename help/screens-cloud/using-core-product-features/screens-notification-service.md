---
title: Screens-Benachrichtigungsdienst in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie den Benachrichtigungsdienst in Screens as a Cloud Service konfigurieren.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
source-git-commit: 69798b1ac3758d37c4e2f480ccc23bae24d6a814
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 42%

---

# Screens-Benachrichtigungsdienst {#notification-service}

## Einführung {#introduction}

### Übersicht

Mit dem AEM Screens-Benachrichtigungsdienst können Administratoren einen Bericht mit einer Liste aller AEM Screens-Player erhalten, die während eines konfigurierbaren Zeitraums nicht per Ping an eine E-Mail gesendet wurden.

### Vorgehensweise bei der Konfiguration

In AEM Screens Cloud können Kunden einen Bericht zum Status der Geräteinaktivität anfordern, indem sie ein Support-Ticket mit folgenden Informationen erstellen:

* Kundenname
* IMS-Organisations-ID
* Häufigkeit: Geben Sie eine Zeit oder eine Häufigkeit in Stunden (z. B. 1) an, zu der der Service E-Mails senden soll.
* Ping-Timeout: Gibt das Intervall in Minuten an, nach dem ein Gerät als nicht erreichbar betrachtet werden soll.
* E-Mail-ID(s) : E-Mail-ID(s), an die der Bericht gesendet wird

>[!NOTE]
>Bei E-Mails wird der Player nur dann gemeldet, wenn das Gerät, das zum Zeitpunkt der Generierung der E-Mail keinen Ping für die angegebene Ping-Zeitüberschreitung durchgeführt hat.

### Anwendungsbeispiel

Wenn Sie die Berichtszeit auf 5 Uhr und das Ping-Timeout auf 1 Stunde festlegen, erhalten Sie, wenn Ihr Screens-Gerät nicht zwischen 4:00 Uhr und 5:00 Uhr pingt, eine E-Mail-Benachrichtigung, in der die Inaktivität des Geräts bestätigt wird.
