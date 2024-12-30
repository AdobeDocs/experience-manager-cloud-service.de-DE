---
title: Versionshinweise für Version 2020.3.0
description: '[!DNL Adobe Experience Manager] as a Cloud Service-Versionshinweise für 2020.3.0.'
exl-id: 0393c789-3999-4e51-be83-269d6eabd3f3
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 96%

---

# Versionshinweise für AEM as a Cloud Service 2020.3.0 {#release-notes}

Auf dieser Seite finden Sie die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.3.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.3.0 von Experience Manager as a Cloud Service wurde am 5. März 2020 veröffentlicht.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in Version 2020.3.0 von AEM as a Cloud Service.

### Neue Funktionen {#what-is-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipeline-Ausführung wurden für bessere Übersichtlichkeit geändert.

### Fehlerbehebungen  {#bug-fixes}

* Protokolldateien für die benutzerdefinierten und produktspezifischen Testschritte konnten nicht über die Benutzeroberfläche heruntergeladen werden.
* Wenn das git-Repository für ein Cloud Service-Programm nicht erstellt werden konnte, war bei Benutzern mit der Rolle „Bereitstellungs-Manager“ manchmal keine Wiederherstellung möglich.
* Bestimmte Benutzeraktivitäten während der Erstellung eines Sandbox-Programms konnten dazu führen, dass die Programmerstellung fehlschlug, bevor die produktionsfremde Pipeline erstellt wurde.
* Die im Build-Schritt verwendete temporäre SonarQube-Instanz konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* Bei der gleichzeitigen Erstellung von Entwicklungsumgebungen im selben Cloud Service-Programm konnte es zu einer Bedingung kommen, bei der nur eine erfolgreich erstellt werden konnte.
* Experience Cloud-Benachrichtigungen für Cloud Service-Programme wurden nicht konsistent empfangen.
* In bestimmten Projekten erzeugte die Option *ResourceResolver-Objekte sollten immer geschlossen werden* eine Nullzeiger-Ausnahme. Dies hatte jedoch keine Auswirkungen auf die Ausführung der Pipeline.
