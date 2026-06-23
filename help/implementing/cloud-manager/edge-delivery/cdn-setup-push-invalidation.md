---
title: Einrichten der Push-Invalidierung für eine Edge Delivery-Site
description: Erfahren Sie, wie Sie die Push-Invalidierung für eine Edge Delivery-Site konfigurieren, um effiziente Inhaltsaktualisierungen und die Caching-Kontrolle sicherzustellen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 7cded93c-325c-4a4b-8644-e6a2379d5179
source-git-commit: 069e94e230b856fba15c3f465c966a5bf6b0ac46
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 84%

---

# Einrichten der Push-Invalidierung für eine Edge Delivery-Site

Die Push-Invalidierung stellt sicher, dass von Autoren vorgenommene Inhaltsaktualisierungen bei der Veröffentlichung automatisch aus dem verwalteten Content Delivery Network (CDN) gelöscht werden. Dadurch wird sichergestellt, dass nur der neueste Inhalt bereitgestellt wird.

Das System löscht den Inhalt basierend auf bestimmten URLs und Cache-Tags oder -Schlüsseln. So wird sichergestellt, dass veraltete Versionen entfernt werden.

Um die Push-Invalidierung zu aktivieren, müssen der Konfigurationsdatei des Projekts bestimmte Eigenschaften hinzugefügt werden. Zum Beispiel eine Microsoft Excel-Arbeitsmappe mit dem Namen `.helix/config.xlsx` in SharePoint oder ein Google-Tabellenblatt mit dem Namen `.helix/config` in Google Drive.

Die folgenden Konfigurationseigenschaften definieren den Namen des Produktions-Hosts und den Typ der CDN-Verwaltung:

| Schlüssel | Wert | Kommentar |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Host-Name der Produktions-Site. Zum Beispiel: `www.example.com`. |
| `cdn.prod.type` | verwaltet |   |

Nachdem Änderungen am Konfigurationsblatt vorgenommen wurden, müssen die Benutzenden sie mit dem [Sidekick-Tool](https://www.aem.live/docs/sidekick) in der Vorschau anzeigen und aktivieren, um die Aktualisierungen anzuwenden.

Siehe auch [Über die Aufgabenliste von Edge Delivery in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list).
