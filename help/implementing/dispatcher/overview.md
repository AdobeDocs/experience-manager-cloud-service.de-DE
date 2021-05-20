---
title: Übersicht über den Ablauf der Inhaltsbereitstellung
description: Übersicht über den Ablauf der Inhaltsbereitstellung
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 100%

---

# Ablauf der Inhaltsbereitstellung {#content-delivery}

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

Der HTML-/Text-Inhaltstyp läuft standardmäßig nach 300 Sekunden (5 Minuten) auf der Dispatcher-Ebene ab. Dieser Schwellenwert wird sowohl vom Dispatcher-Cache als auch vom CDN eingehalten. Bei der erneuten Bereitstellung des Publish-Dienst wird der Dispatcher-Cache geleert und anschließend aufgewärmt, bevor die neuen Veröffentlichungsknoten Traffic akzeptieren.

In den folgenden Abschnitten finden Sie ausführlichere Informationen zur Bereitstellung von Inhalten, einschließlich CDN-Konfiguration und Caching.

Informationen zur Replikation vom Autorendienst zum Veröffentlichungsdienst finden Sie [hier](/help/operations/replication.md).
