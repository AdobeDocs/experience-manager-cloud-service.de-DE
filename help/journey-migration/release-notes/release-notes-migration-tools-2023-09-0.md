---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.09.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.09.0
feature: Release Information
exl-id: 484a60d4-a439-43d6-a23e-4a3b45ef4160
source-git-commit: 95871cb435499b941cf9648fa2e8930049c8171c
workflow-type: ht
source-wordcount: '147'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.09.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.09.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool in Version 3.0.0 wurde am 07. September 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

Das Content Transfer Tool wurde verbessert und bietet nun folgende Vorteile:

* Die Übertragungszeit beim Migrieren einer Teilmenge eines Inhalts-Repositorys wurde verkürzt, indem AzCopy verwendet wird, um statt aller nur die erforderlichen Blob-IDs zu kopieren.
* Schnellere differenzielle Auffüllungen von Inhalten mit Oak-Aktualisierung.
* Die Stabilität wurde verbessert, indem der Indizierungsprozess vom Inhaltserfassungsprozess getrennt wurde. Wenn die Indizierung fehlschlägt, muss der Inhalt nicht erneut erfasst werden. Nur die Indizierung wird automatisch neu gestartet, wodurch viel Zeit und Mühe eingespart wird.
