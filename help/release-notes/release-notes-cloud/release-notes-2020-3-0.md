---
title: Versionshinweise für Version 2020.3.0
description: Versionshinweise für Version 2020.3.0
translation-type: tm+mt
source-git-commit: 27225bf4b918f39892ac9ab6f46deb97479f08e8

---


# Release Notes for AEM as a Cloud Service 2020.3.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager als Cloud Service 2020.3.0 beschrieben.


## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Experience Manager als Cloud-Dienst 2020.3.0 ist der 05. März 2020.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Manager in AEM als Cloud-Service-Version 2020.3.0.

### Neuerungen {#what-is-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipelineausführung wurden für bessere Übersichtlichkeit geändert.

### Fehlerbehebungen  {#bug-fixes}

* Protokolldateien für die benutzerdefinierten und produktspezifischen Testschritte konnten nicht über die Benutzeroberfläche heruntergeladen werden.
* Wenn das Git-Repository für ein Cloud-Dienst-Programm nicht erstellt werden konnte, konnten Benutzer in der Rolle &quot;Deployment Manager&quot;manchmal nicht von diesem Fehler wiederherstellen.
* Bestimmte Benutzereinstellungen während der Erstellung eines Sandbox-Programms können dazu führen, dass die Erstellung des Programms fehlschlägt, bevor die Nicht-Produktionspipeline erstellt wurde.
* Die im Build-Schritt verwendete temporäre SonarQube-Instanz konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* Bei der gleichzeitigen Erstellung von dev-Umgebung im selben Cloud-Dienst-Programm kann es zu einer Bedingung kommen, bei der nur eine erfolgreich erstellt werden konnte.
* Experience Cloud-Benachrichtigungen für Cloud-Programm wurden nicht konsistent empfangen.
* In bestimmten Projekten erzeugte die Option *ResourceResolver-Objekte sollten immer geschlossen werden* eine Null Pointer-Ausnahme. Dies hatte jedoch keine Auswirkungen auf die Ausführung der Pipeline.

