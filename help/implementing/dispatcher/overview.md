---
title: Übersicht über den Ablauf der Inhaltsbereitstellung
description: Übersicht über den Ablauf der Inhaltsbereitstellung
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 49%

---

# Ablauf der Inhaltsbereitstellung {#content-delivery}

Auf dieser Seite wird der Veröffentlichungsdienst für die Inhaltsbereitstellung in AEM as a Cloud Service beschrieben. Der Veröffentlichungsdienst für die Inhaltsbereitstellung umfasst:

* CDN
* AEM Dispatcher
* AEM Publisher

Der Datenfluss sieht wie folgt aus:

1. Die URL wird im Browser hinzugefügt
1. Anfrage an CDN, das in DNS dieser Domain zugeordnet ist
1. Wenn der Inhalt im CDN vollständig zwischengespeichert ist, stellt CDN ihn für den Browser bereit
1. Wenn der Inhalt nicht vollständig zwischengespeichert ist, ruft das CDN den Dispatcher (Reverse-Proxy) auf
1. Wenn der Inhalt vollständig im Dispatcher zwischengespeichert ist, stellt der Dispatcher ihn dem CDN bereit
1. Wenn der Inhalt nicht vollständig zwischengespeichert ist, ruft der Dispatcher die AEM zur Veröffentlichung auf (Reverse-Proxy)
1. Der Inhalt wird vom Browser gerendert, der ihn je nach Header auch zwischenspeichern kann

Standardmäßig läuft der Content-Typ HTML/Text nach 300 Sekunden (5 Minuten) auf der Dispatcher-Ebene ab, ein Schwellenwert, den sowohl der Dispatcher-Cache als auch das CDN berücksichtigen. Bei der erneuten Bereitstellung des Veröffentlichungsdienstes wird der Dispatcher-Cache gelöscht und dann aufgewärmt, bevor die neuen Veröffentlichungsknoten Traffic akzeptieren.

Die folgenden Abschnitte enthalten detailliertere Informationen zur Inhaltsbereitstellung:
* [CDN-Konfiguration](/help/implementing/dispatcher/cdn.md)
* [Caching](/help/implementing/dispatcher/caching.md)


Informationen zur Replikation vom Autoren-Service zum Veröffentlichungs-Service finden Sie [hier](/help/operations/replication.md).
