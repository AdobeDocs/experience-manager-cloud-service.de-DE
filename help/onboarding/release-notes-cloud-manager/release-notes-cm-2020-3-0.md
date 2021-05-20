---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.3.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.3.0
feature: Versionshinweise
exl-id: 2ff62ba5-a657-4739-b646-1e948332bf79
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.3.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.3.0.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von Cloud Manager in AEM as a Cloud Service Version 2020.3.0 ist der 5. März 2020.

### Neue Funktionen {#what-is-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipeline-Ausführung wurden für bessere Übersichtlichkeit geändert.

### Fehlerbehebungen {#bug-fixes}

* Protokolldateien für die benutzerdefinierten und produktspezifischen Testschritte konnten nicht über die Benutzeroberfläche heruntergeladen werden.
* Wenn das git-Repository für ein Cloud Service-Programm nicht erstellt werden konnte, war bei Benutzern mit der Rolle „Implementierungs-Manager“ manchmal keine Wiederherstellung möglich.
* Bestimmte Benutzeraktivitäten während der Erstellung eines Sandbox-Programms konnten dazu führen, dass die Programmerstellung fehlschlug, bevor die produktionsfremde Pipeline erstellt wurde.
* Die im Build-Schritt verwendete temporäre SonarQube-Instanz konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* Bei der gleichzeitigen Erstellung von Entwicklungsumgebungen im selben Cloud Service-Programm konnte es zu einer Bedingung kommen, bei der nur eine erfolgreich erstellt werden konnte.
* Experience Cloud-Benachrichtigungen für Cloud Service-Programme wurden nicht konsistent empfangen.
* In bestimmten Projekten erzeugte die Option *ResourceResolver-Objekte sollten immer geschlossen werden* eine Nullzeiger-Ausnahme. Dies hatte jedoch keine Auswirkungen auf die Ausführung der Pipeline.
