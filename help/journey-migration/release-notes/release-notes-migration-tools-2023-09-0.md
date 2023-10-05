---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.09.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.09.0
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
source-git-commit: c89ca7320d8f31d2545cadf98f39e577337b8918
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 38%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.09.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.09.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 3.0.0 des Content Transfer Tool wurde am 7. September 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

Das Content Transfer Tool wurde erheblich verbessert und bietet nun folgende Vorteile:
* Verringerte Übertragungszeit bei der Migration einer Teilmenge eines Inhalts-Repositorys durch Nutzung von AzCopy, um nur die erforderlichen Blob-IDs zu kopieren, anstatt alle Blob-IDs zu kopieren
* Schnellere differenzielle Auffüllungen von Inhalten mit Oak-Upgrade
* Die Stabilität wurde verbessert, indem der Indizierungsprozess vom Inhaltserfassungsprozess getrennt wurde. Im Falle einer fehlgeschlagenen Indizierung müssen Inhalte nicht erneut erfasst werden. Nur die Indizierung startet automatisch neu, wodurch viel Zeit und Aufwand eingespart wird.
