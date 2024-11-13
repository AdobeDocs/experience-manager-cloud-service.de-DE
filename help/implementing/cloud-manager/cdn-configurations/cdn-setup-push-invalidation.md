---
title: Einrichten der Push-Invalidierung
description: Erfahren Sie, wie Sie die Push-Invalidierung für die Erstellung Ihres eigenen Produktions-CDN konfigurieren.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 7cded93c-325c-4a4b-8644-e6a2379d5179
source-git-commit: 0ac6856e8f3e664fcc7e3c08faac4c4f5c16af18
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 2%

---

# Push-Invalidierung einrichten

Die Push-Invalidierung stellt sicher, dass Inhaltsaktualisierungen von Autoren automatisch aus dem verwalteten Content Delivery Network (CDN) entfernt werden, wenn sie veröffentlicht werden. Dadurch wird sichergestellt, dass nur der neueste Inhalt bereitgestellt wird.

Das System löscht den Inhalt basierend auf bestimmten URLs und Cache-Tags oder -Schlüsseln und stellt dabei sicher, dass veraltete Versionen gelöscht werden.

Um die Push-Invalidierung zu aktivieren, müssen der Konfigurationsdatei des Projekts spezifische Eigenschaften hinzugefügt werden. Beispiel: eine Microsoft Excel-Arbeitsmappe mit dem Namen `.helix/config.xlsx` in SharePoint oder ein Google-Tabellenblatt mit dem Namen `.helix/config` in Google Drive.

Die folgenden Konfigurationseigenschaften definieren den Namen des Produktions-Hosts und den Typ der CDN-Verwaltung:

| key | value | Kommentar |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Hostname der Produktions-Site. Zum Beispiel: `www.example.com`. |
| `cdn.prod.type` | verwaltet |   |

Nachdem Änderungen am Konfigurationsblatt vorgenommen wurden, müssen Benutzer sie mit dem [Sidekick-Tool](/help/edge/docs/sidekick.md) in der Vorschau anzeigen und aktivieren, um die Aktualisierungen anzuwenden.

Siehe auch [Über die Aufgabenliste von Edge Delivery in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list).
