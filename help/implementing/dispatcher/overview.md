---
title: Übersicht über den Inhaltsfluss Versand
description: Übersicht über den Inhaltsfluss Versand
translation-type: tm+mt
source-git-commit: 0080ace746f4a7212180d2404b356176d5f2d72c
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 81%

---


# Content Versand Flow {#content-delivery}

Auf dieser Seite wird der Veröffentlichungsdienst für die Inhaltsbereitstellung in AEM as a Cloud Service beschrieben. Der Veröffentlichungsdienst für die Inhaltsbereitstellung umfasst:

* CDN
* AEM Dispatcher
* AEM Publish

Der Datenfluss sieht wie folgt aus:

1. Die URL wird im Browser hinzugefügt
1. Anfrage an CDN, das in DNS dieser Domäne zugeordnet ist
1. Wenn der Inhalt im CDN vollständig zwischengespeichert ist, stellt CDN ihn für den Browser bereit
1. Wenn der Inhalt nicht vollständig zwischengespeichert ist, ruft CDN den Dispatcher auf (Reverse-Proxy)
1. Wenn der Inhalt in Dispatcher vollständig zwischengespeichert ist, stellt Dispatcher ihn dem CDN bereit
1. Wenn der Inhalt nicht vollständig zwischengespeichert ist, ruft Dispatcher die AEM-Veröffentlichungsinstanz auf (Reverse-Proxy)
1. Der Inhalt wird vom Browser gerendert, der ihn je nach Header auch zwischenspeichern kann

Standardmäßig läuft der Content-Typ HTML/Text auf der Dispatcher-Ebene nach 300 s (5 Minuten) ab. Dies ist ein Schwellenwert, den sowohl der Dispatcher-Cache als auch CDN berücksichtigen. Bei der erneuten Bereitstellung des Publish-Dienst wird der Dispatcher-Cache geleert und anschließend aufgewärmt, bevor die neuen Veröffentlichungsknoten Traffic akzeptieren.

In den folgenden Abschnitten finden Sie ausführlichere Informationen zur Bereitstellung von Inhalten, einschließlich CDN-Konfiguration und Caching.

Informationen zur Replikation vom Autorendienst zum Veröffentlichungsdienst finden Sie [hier](/help/operations/replication.md).
