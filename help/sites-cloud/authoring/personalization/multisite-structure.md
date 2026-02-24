---
title: Strukturierung von Multisite-Management für zielgerichtete Inhalte
description: Im Diagramm ist der Aufbau der Multisite-Unterstützung für zielgerichtete Inhalte dargestellt.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: c6b05c2a-0897-4514-8937-e23bfcf757d5
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 97%

---

# Strukturierung von Multisite-Management für zielgerichtete Inhalte {#how-multisite-management-for-targeted-content-is-structured}

Im folgenden Diagramm ist der Aufbau der Multisite-Unterstützung für Targeting-Inhalte dargestellt.

Gebiete werden unter **/content/campaigns/&lt;Marke>** eingeordnet und jede Marke verfügt standardmäßig über ein automatisch erstelltes Hauptgebiet. In jedem Gebiet ist ein eigener Satz Aktivitäten, Erlebnisse und Angebote enthalten.

![Multisite-Struktur](/help/sites-cloud/authoring/assets/multisite-structure.png)

Seiten oder Sites können Gebieten zugeordnet werden, sodass sich Targeting-Inhalte nachschlagen lassen. Sollte kein Gebiet konfiguriert sein, bezieht sich AEM für diese Marke auf das primäre Gebiet.

Im folgenden Diagramm finden Sie ein Beispiel dafür, wie die Logik im Falle der drei Sites Site1, Site2 und Site3 funktioniert.

![Site-übergreifende Multisite-Struktur](/help/sites-cloud/authoring/assets/multisite-structure-2.png)

* site1 schlägt myarea1 für brand1 und otherarea2 für brand2 basierend auf der Bereichszuordnung nach.
* Site2 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf das primäre Gebiet, da nur für Marke1 Gebiete zugewiesen wurden.
* Site3 bezieht sich für Marke1 und für Marke2 auf das primäre Gebiet, weil für diese Site keine Gebietszuordnung vorgenommen wurde.
