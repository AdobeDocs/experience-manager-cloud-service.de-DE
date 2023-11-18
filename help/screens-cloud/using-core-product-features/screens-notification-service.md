---
title: Screens-Benachrichtigungsdienst in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie den Benachrichtigungsdienst in Screens as a Cloud Service konfigurieren.
index: true
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 4%

---


# Screens-Benachrichtigungsdienst {#notification-service}

## Einführung {#introduction}

### Übersicht

Mit dem AEM Screens-Benachrichtigungsdienst können Administratoren eine E-Mail erhalten, wenn ein AEM Screens-Player während eines konfigurierbaren Zeitraums nicht pingt.

### Vorgehensweise bei der Konfiguration

In AEM Screens Cloud können Kunden Warnhinweise zum Status der Geräteinaktivität anfordern, indem sie ein Support-Ticket mit folgenden Informationen erstellen:

* Kundenname
* IMS-Organisations-ID
* Häufigkeit planen: Geben Sie eine Uhrzeit oder Häufigkeit in Stunden an (z. B. 1), zu der dieser Monitor E-Mails senden soll.
* Ping-Timeout: Gibt das Intervall in Minuten an, nach dem ein Gerät als nicht erreichbar betrachtet werden soll.
* E-Mail-ID(s) : E-Mail-ID(s), an die der Bericht gesendet wird