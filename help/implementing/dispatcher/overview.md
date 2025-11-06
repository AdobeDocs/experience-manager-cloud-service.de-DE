---
title: Übersicht über den Ablauf der Inhaltsbereitstellung
description: Erfahren Sie mehr über den Datenfluss bei der Inhaltsbereitstellung und darüber, wie Sie Inhalte veröffentlichen.
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
feature: Dispatcher
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 100%

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
1. Wenn der Inhalt nicht vollständig zwischengespeichert ist, ruft CDN den Dispatcher auf (Reverse-Proxy)
1. Wenn der Inhalt in Dispatcher vollständig zwischengespeichert ist, stellt Dispatcher ihn dem CDN bereit
1. Wenn der Inhalt nicht vollständig zwischengespeichert ist, ruft Dispatcher die AEM Publishing-Instanz auf (Reverse-Proxy)
1. Der Inhalt wird vom Browser gerendert, der ihn je nach Header auch zwischenspeichern kann

Der HTML-/Text-Inhaltstyp läuft standardmäßig nach 300 Sekunden (5 Minuten) auf der Dispatcher-Ebene ab. Dieser Schwellenwert wird sowohl vom Dispatcher-Cache als auch vom CDN eingehalten. Bei der erneuten Bereitstellung des Publishing-Service wird der Dispatcher-Cache geleert und anschließend aufgewärmt, damit die neuen Veröffentlichungsknoten Traffic akzeptieren.

In den folgenden Abschnitten finden Sie genauere Informationen zur Inhaltsbereitstellung:

* [CDN-Konfiguration](/help/implementing/dispatcher/cdn.md)
* [Caching](/help/implementing/dispatcher/caching.md)

Informationen zur Replikation vom Autoren-Service zum Veröffentlichungs-Service finden Sie unter [Replikation](/help/operations/replication.md).
