---
title: Strukturierung von Multisite-Management für zielgerichtete Inhalte
description: Im Diagramm ist der Aufbau der Multisite-Unterstützung für zielgerichtete Inhalte dargestellt.
exl-id: c6b05c2a-0897-4514-8937-e23bfcf757d5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# Strukturierung von Multisite-Management für zielgerichtete Inhalte {#how-multisite-management-for-targeted-content-is-structured}

Im folgenden Diagramm ist der Aufbau der Multisite-Unterstützung für Targeting-Inhalte dargestellt.

Gebiete werden unter **/content/campaigns/&lt;Marke>** eingeordnet und jede Marke verfügt standardmäßig über ein automatisch erstelltes Master-Gebiet. In jedem Gebiet ist ein eigener Satz Aktivitäten, Erlebnisse und Angebote enthalten.

![Multisite-Struktur](/help/sites-cloud/authoring/assets/multisite-structure.png)

Seiten oder Sites können Gebieten zugeordnet werden, sodass sich Targeting-Inhalte nachschlagen lassen. Sollte kein Gebiet konfiguriert sein, bezieht sich AEM für diese Marke auf das Mastergebiet.

Im folgenden Diagramm finden Sie ein Beispiel dafür, wie die Logik im Falle der drei Sites Site1, Site2 und Site3 funktioniert.

![Site-übergreifende Multisite-Struktur](/help/sites-cloud/authoring/assets/multisite-structure-2.png)

* Site1 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf AnderesGebiet2, basierend auf der Gebietszuordnung.
* Site2 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf das Mastergebiet, da nur für Marke1 Gebiete zugewiesen wurden.
* Site3 bezieht sich für Marke1 und für Marke2 auf das Mastergebiet, weil für diese Site keine Gebietszuordnung vorgenommen wurde.
