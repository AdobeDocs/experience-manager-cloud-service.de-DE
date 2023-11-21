---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.09.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.09.0
feature: Release Information
exl-id: 484a60d4-a439-43d6-a23e-4a3b45ef4160
source-git-commit: be38ca5bf79d401fc12c1422c270a2ee84bbbad2
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 39%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.09.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.09.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 3.0.0 des Content Transfer Tool wurde am 7. September 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

Das Content Transfer Tool wurde verbessert und bietet nun folgende Vorteile:

* Die Übertragungszeit beim Migrieren einer Teilmenge eines Inhalts-Repositorys wurde verkürzt, indem AzCopy verwendet wurde, um nur die erforderlichen Blob-IDs zu kopieren, anstatt alle Blob-IDs zu kopieren.
* Schnellere differenzielle Auffüllungen von Inhalten mit Oak-Upgrade.
* Die Stabilität wurde verbessert, indem der Indizierungsprozess vom Inhaltserfassungsprozess getrennt wurde. Wenn die Indizierung fehlgeschlagen ist, muss der Inhalt nicht erneut erfasst werden. Nur die Indizierung wird automatisch neu gestartet, wodurch viel Zeit und Mühe eingespart wird.
