---
title: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.4.0
description: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.4.0
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 77%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager als Cloud Service 2020.4.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2020.4.0 erläutert.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.4.0 ist der 09. April 2020.

## Neuerungen {#whats-new-cloud-manager}

* Herausgeber-URLs sind jetzt auf der Seite „Umgebung“ in der Benutzeroberfläche von Cloud Manager verfügbar.
* Änderungen an der Navigation, die es dem Benutzer ermöglichen, ein Programm von der Cloud Manager-Übersichtsseite aus zu bearbeiten, zu wechseln oder hinzuzufügen.
* Änderungen, die es Benutzern erlauben, das Programm über die Programmkarte auf der Startseite von Cloud Manager zu bearbeiten.
* Neuer Pipeline-Status: **Pipeline wird ausgeführt** wird in der Umgebung angezeigt, der sie zugewiesen ist.
* Bessere Verständlichkeit der Pipeline-Ausführungsseite. Dazu gehören die Anzeige des Pipeline-Namens (nur produktionsfremde Pipelines) und des Typs sowie ein Abzeichen mit dem Pipeline-Status (In Bearbeitung/Abgebrochen/Fehlgeschlagen).
* QuickInfos zur Verbesserung des Kundenerlebnisses und der Verständlichkeit, warum die Schaltfläche „Programm/Umgebung hinzufügen“ deaktiviert ist.
* Fehlgeschlagene Umgebungen können jetzt über die Benutzeroberfläche und die API gelöscht werden.
* Der zur Erstellung von Git-Kennwörtern Prozess ist jetzt weniger anfällig für Probleme in der zugrunde liegenden Service-Ebene.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Links zur Staging-Umgebung auf der Seite mit Details zur Pipeline-Ausführung führten nicht konsistent zum richtigen Speicherort.
* Einzelne Schritte innerhalb des Prozesses der Umgebungserstellung setzten früher als nötig aus und brachten den Prozess zum Scheitern.
* Die Maven-Konfiguration, die im Build-Container verwendet wird, wurde aktualisiert, um Deadlocks beim Download von Artefaktmetadaten zu vermeiden.
* In einigen Fällen konnte der Schritt zur Bilderstellung die Kundenpakete nicht erfolgreich herunterladen.
* Bestimmte selten auftretende Bedingungen verhinderten, dass Umgebungen gelöscht wurden.
* Experience Cloud-Benachrichtigungen wurden nicht konsistent empfangen.

