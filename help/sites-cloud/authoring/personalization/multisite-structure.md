---
title: Strukturierung von Multisite-Management für zielgerichtete Inhalte
description: Ein Diagramm zeigt, wie die Multisite-Unterstützung für zielgerichtete Inhalte strukturiert ist
exl-id: c6b05c2a-0897-4514-8937-e23bfcf757d5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 78%

---

# Strukturierung von Multisite-Management für zielgerichtete Inhalte {#how-multisite-management-for-targeted-content-is-structured}

Im folgenden Diagramm ist der Aufbau der Multisite-Unterstützung für Targeting-Inhalte dargestellt.

Gebiete werden unter **/content/campaigns/&lt;Marke>** eingeordnet und jede Marke verfügt standardmäßig über ein automatisch erstelltes Hauptgebiet. In jedem Gebiet ist ein eigener Satz Aktivitäten, Erlebnisse und Angebote enthalten.

![Multisite-Struktur](/help/sites-cloud/authoring/assets/multisite-structure.png)

Zum Nachschlagen zielgerichteter Inhalte können die Seiten oder Sites einem Gebiet zugeordnet werden. Sollte kein Gebiet konfiguriert sein, bezieht sich AEM für diese Marke auf das primäre Gebiet.

Im folgenden Diagramm finden Sie ein Beispiel dafür, wie die Logik im Falle der drei Sites Site1, Site2 und Site3 funktioniert.

![Site-übergreifende Multisite-Struktur](/help/sites-cloud/authoring/assets/multisite-structure-2.png)

* site1 sucht basierend auf der Bereichszuordnung nach myarea1 für brand1 und other area2 für brand2.
* Site2 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf das primäre Gebiet, da nur für Marke1 Gebiete zugewiesen wurden.
* Site3 bezieht sich für Marke1 und für Marke2 auf das primäre Gebiet, weil für diese Site keine Gebietszuordnung vorgenommen wurde.
