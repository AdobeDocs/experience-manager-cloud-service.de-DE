---
title: Versionshinweise für Version 2020.3.0
description: Versionshinweise für Version 2020.3.0
translation-type: tm+mt
source-git-commit: bcbb50f467a0e3b3047e2bb872a8fe39a9f02a1a

---


# Release Notes for AEM as a Cloud Service 2020.3.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager als Cloud Service 2020.3.0 beschrieben.

## Cloud Manager {#cloud-manager}

Das Releasedatum für Cloud Manager Version 2020.3.0 ist der 05. März 2020.

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Manager Release 2020.3.0.

### Neuerungen {#what-is-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipelineausführung wurden aus Gründen der Klarheit bearbeitet.

### Fehlerbehebungen  {#bug-fixes}

* Protokolldateien für die benutzerdefinierten und produktspezifischen Testschritte konnten nicht über die Benutzeroberfläche heruntergeladen werden.
* Wenn das Git-Repository für ein Cloud-Serviceprogramm nicht erstellt werden konnte, konnten Benutzer in der Rolle &quot;Deployment Manager&quot;manchmal nicht von diesem Fehler wiederherstellen.
* Bestimmte Benutzeraktivitäten während der Erstellung eines Sandbox-Programms könnten dazu führen, dass die Programmierung fehlschlägt, bevor die Nicht-Produktion-Pipeline erstellt wurde.
* Die im Buildschritt verwendete Kurzzeitinstanz SonarQube konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* Bei der gleichzeitigen Erstellung von Entwicklungsumgebungen im selben Cloud-Serviceprogramm könnte eine Bedingung auftreten, bei der nur eine erfolgreich erstellt werden konnte.
* Experience Cloud-Benachrichtigungen für Cloud-Serviceprogramme wurden nicht konsistent empfangen.
* In bestimmten Projekten sollte das *ResourceResolver-Objekt immer geschlossen* sein, wodurch eine Null-Zeiger-Ausnahme entsteht. Dies hatte jedoch keine Auswirkungen auf die Durchführung der Pipeline.

