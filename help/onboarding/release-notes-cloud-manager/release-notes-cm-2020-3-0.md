---
title: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.3.0
description: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.3.0
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 73%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager als Cloud Service 2020.3.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2020.3.0 erläutert.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.3.0 ist der 05. März 2020.

### Neuerungen {#what-is-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipelineausführung wurden für bessere Übersichtlichkeit geändert.

### Fehlerbehebungen {#bug-fixes}

* Protokolldateien für die benutzerdefinierten und produktspezifischen Testschritte konnten nicht über die Benutzeroberfläche heruntergeladen werden.
* Wenn das git-Repository für ein Cloud-Service-Programm nicht erstellt werden konnte, war bei Benutzern mit der Rolle „Bereitstellungs-Manager“ manchmal keine Wiederherstellung möglich.
* Bestimmte Benutzeraktivitäten während der Erstellung eines Sandbox-Programms konnten dazu führen, dass die Programmerstellung fehlschlug, bevor die produktionsfremde Pipeline erstellt wurde.
* Die im Build-Schritt verwendete temporäre SonarQube-Instanz konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* Bei der gleichzeitigen Erstellung von Entwicklungsumgebungen im selben Cloud Service-Programm konnte es zu einer Bedingung kommen, bei der nur eine erfolgreich erstellt werden konnte.
* Experience Cloud-Benachrichtigungen für Cloud Service-Programme wurden nicht konsistent empfangen.
* In bestimmten Projekten erzeugte die Option *ResourceResolver-Objekte sollten immer geschlossen werden* eine Nullzeiger-Ausnahme. Dies hatte jedoch keine Auswirkungen auf die Ausführung der Pipeline.