---
title: Einrichten der Push-Invalidierung für eine Edge Delivery-Site
description: Erfahren Sie, wie Sie die Push-Invalidierung für eine Edge Delivery-Site konfigurieren, um effiziente Inhaltsaktualisierungen und die Caching-Kontrolle sicherzustellen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 7cded93c-325c-4a4b-8644-e6a2379d5179
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 100%

---

# Einrichten der Push-Invalidierung

Die Push-Invalidierung stellt sicher, dass Inhaltsaktualisierungen von Autorinnen und Autoren automatisch aus dem verwalteten Content Delivery Network (CDN) entfernt werden, wenn sie veröffentlicht werden. Dadurch wird sichergestellt, dass nur der neueste Inhalt bereitgestellt wird.

Das System löscht den Inhalt basierend auf bestimmten URLs und Cache-Tags oder -Schlüsseln. So wird sichergestellt, dass veraltete Versionen entfernt werden.

Um die Push-Invalidierung zu aktivieren, müssen der Konfigurationsdatei des Projekts bestimmte Eigenschaften hinzugefügt werden. Zum Beispiel eine Microsoft Excel-Arbeitsmappe mit dem Namen `.helix/config.xlsx` in SharePoint oder ein Google-Tabellenblatt mit dem Namen `.helix/config` in Google Drive.

Die folgenden Konfigurationseigenschaften definieren den Namen des Produktions-Hosts und den Typ der CDN-Verwaltung:

| Schlüssel | Wert | Kommentar |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Host-Name der Produktions-Site. Zum Beispiel: `www.example.com`. |
| `cdn.prod.type` | verwaltet |   |

Nachdem Änderungen am Konfigurationsblatt vorgenommen wurden, müssen die Benutzenden sie mit dem [Sidekick-Tool](https://www.aem.live/docs/sidekick) in der Vorschau anzeigen und aktivieren, um die Aktualisierungen anzuwenden.

Siehe auch [Über die Aufgabenliste von Edge Delivery in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list).
