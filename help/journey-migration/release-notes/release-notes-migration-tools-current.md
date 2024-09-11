---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.09
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.09.0
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
role: Admin
source-git-commit: 0c16f264826a46907afc33c91a021e7696f5b7a8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 33%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.09.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2024.09.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 3.0.20 des Content Transfer Tool wurde am 28. August 2024 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Benutzer werden in dieser Version nicht mehr erfasst und daher wurde die optionale Funktion Benutzerzuordnung entfernt.
* Es wurde eine OSGi-Konfigurationsoption hinzugefügt, um die Migration von Prinzipalen während der Extraktion und Aufnahme zu deaktivieren oder zu aktivieren (die Standardeinstellung ist, sie zu aktivieren).

### Fehlerbehebungen {#bug-fixes-ctt}

* CTT wurde verbessert, um Fehler beim Aufheben des Schutzes eines geheimen Schlüssels in der azcopy-Konfiguration zu vermeiden.
* Beim Kopieren von AzCopy-Logs in der Validierungsphase übernimmt CTT nun die ordnungsgemäße Verarbeitung aller Fehler
* Ändern des beim Extraktionsvorgang erstellten azcopy log directory

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Die Version 2.1.52 von Best Practices Analyzer wurde am 4. September 2024 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Ein neues Muster wurde eingeführt, um JCR-basiertes Eventing in AEM zu erkennen

### Fehlerbehebungen {#bug-fixes-bpa}

* Falsch-Positiv-Werte korrigiert
* Verbesserte Stabilität bei der Verarbeitung umgeleiteter Antworten vom Dispatcher
* Korrektur der Nicht-Meldung von NCC-Suchen für alle Sprachen unter /apps/wcm/core/resources/languages/
* Es wurde eine Prüfung hinzugefügt, um festzustellen, ob eine Mehrfacheigenschaft eines Knotens über keine Werte verfügt.

