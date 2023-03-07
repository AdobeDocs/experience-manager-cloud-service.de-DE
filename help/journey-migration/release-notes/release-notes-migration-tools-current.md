---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2023.03.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.03.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: 5815dacd2806cc7886aa0c7c5c9fd329306b3e1b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 49%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2023.03.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.03.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.40 wurde am 03. März 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* BPA kann jetzt Knoten, die in Konflikt zueinander stehen, erkennen und darüber berichten - Knoten mit denselben `jcr:uuid`. Solche Ergebnisse werden als kritisch markiert, da sie zu Fehlern bei der Inhaltsaufnahme führen können, wenn Inhalte auf AEM as a Cloud Service verschoben werden.
* BPA kann jetzt die Verwendung von Event-Listenern erkennen und darüber berichten. Es wird empfohlen, diesen Ereignistyp bei der Umstellung auf AEM as a Cloud Service in Sling-Aufträge umzuwandeln.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA meldete falsch-positive Ergebnisse über `grouprendercondition`. Dieses Problem wurde behoben.