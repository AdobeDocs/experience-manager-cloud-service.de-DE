---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.07
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.07.0
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
role: Admin
source-git-commit: 4f01ca0076248442fe93161bbc8b98bffb64551b
workflow-type: ht
source-wordcount: '171'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.07.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.07.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 3.0.16 wurde am 16. Juli 2024 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Automatisches Hochladen von CTT-Extraktionsprotokollen bei Fehlern.
* Benutzende können nun die Aufnahme nach Erneuerung des Extraktionsschlüssels erfolgreich durchführen.
* Es wurde Unterstützung für die Durchführung von CTT-Extraktionen mit einem Azure-Zugriffsschlüssel und geheimen Schlüssel mit AzureDataStore hinzugefügt.
* Benutzende erhalten jetzt die richtige Fehlermeldung, wenn zum Erstellen eines Migrationssatzes ein ungültiger Schlüssel verwendet wird.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer v2.1.50 wurde im Mai 2024 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-bpa}

* Der Best Practices Analyzer erkennt jetzt alle Knoten, die größer sind als 16 MB.
* Eine Wettlaufsituation, die zu sporadischen Vorkommnissen von NCC-Befunden führte, wurde korrigiert.
