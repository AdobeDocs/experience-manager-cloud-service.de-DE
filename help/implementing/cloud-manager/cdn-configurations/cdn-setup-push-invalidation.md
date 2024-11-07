---
title: Einrichten der Push-Invalidierung
description: Erfahren Sie, wie Sie die Push-Invalidierung für die Erstellung Ihres eigenen Produktions-CDN konfigurieren.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
source-git-commit: 3941b7f97d434946a3cb796633f306b89e68c0a4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 2%

---

# Push-Invalidierung einrichten

Die Push-Invalidierung stellt sicher, dass Inhaltsaktualisierungen von Autoren automatisch aus dem verwalteten Content Delivery Network (CDN) entfernt werden, wenn sie veröffentlicht werden, sodass nur der neueste Inhalt bereitgestellt wird.

Das System löscht den Inhalt basierend auf bestimmten URLs und Cache-Tags oder -Schlüsseln und stellt dabei sicher, dass veraltete Versionen gelöscht werden.

Um die Push-Invalidierung zu aktivieren, müssen der Konfigurationsdatei des Projekts spezifische Eigenschaften hinzugefügt werden. Beispiel: eine Microsoft Excel-Arbeitsmappe mit dem Namen `.helix/config.xlsx` in SharePoint oder ein Google-Tabellenblatt mit dem Namen `.helix/config` in Google Drive.

Die folgenden Konfigurationseigenschaften definieren den Namen des Produktions-Hosts und den Typ der CDN-Verwaltung:

| key | value | Kommentar |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Hostname der Produktions-Site. Zum Beispiel: `www.example.com`. |
| `cdn.prod.type` | verwaltet |   |

Nachdem Änderungen am Konfigurationsblatt vorgenommen wurden, müssen Benutzer sie mit dem [Sidekick-Tool](/help/edge/docs/sidekick.md) in der Vorschau anzeigen und aktivieren, um die Aktualisierungen anzuwenden.
