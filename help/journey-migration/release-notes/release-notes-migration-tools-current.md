---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.09
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service, Version 2024.09.0
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
role: Admin
source-git-commit: 0c16f264826a46907afc33c91a021e7696f5b7a8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service, Version 2024.09.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.09.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool Version 3.0.20 wurde am 28. August 2024 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Benutzende werden in dieser Version nicht mehr aufgenommen und daher wurde die optionale Funktion zur Benutzerzuordnung entfernt.
* Es wurde eine OSGi-Konfigurationsoption hinzugefügt, um die Migration von Prinzipalen während der Extraktion und Aufnahme zu deaktivieren oder zu aktivieren (die Standardeinstellung ist, sie zu aktivieren).

### Fehlerbehebungen {#bug-fixes-ctt}

* CTT wurde verbessert, um einen Fehler beim Aufheben des Schutzes eines geheimen Schlüssels in der AzCopy-Konfiguration zu vermeiden.
* Beim Kopieren von AzCopy-Protokollen in der Überprüfungsphase übernimmt CTT nun die ordnungsgemäße Verarbeitung aller Fehler.
* Ändern des beim Extraktionsvorgang erstellten AzCopy-Protokollverzeichnisses

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer v2.1.52 wurde am 4. September 2024 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Es wurde ein neues Muster eingeführt, um JCR-basiertes Eventing in AEM zu erkennen.

### Fehlerbehebungen {#bug-fixes-bpa}

* Falsch positive Treffer wurden korrigiert.
* Die Stabilität bei der Verarbeitung umgeleiteter Antworten vom Dispatcher wurde verbessert.
* Das Ausbleiben von Meldungen von NCC-Suchen für alle Sprachen unter /apps/wcm/core/resources/languages/ wurde korrigiert.
* Es wurde eine Prüfung hinzugefügt, um festzustellen, ob eine Mehrfacheigenschaft eines Knotens über keine Werte verfügt.

