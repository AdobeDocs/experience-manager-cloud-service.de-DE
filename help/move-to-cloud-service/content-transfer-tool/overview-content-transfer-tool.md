---
title: Übersicht über das Content Transfer-Tool
description: Übersicht über das Content Transfer-Tool
translation-type: tm+mt
source-git-commit: f2a6b67e3673bf6dfeb63d445074f6d1e05971cf
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 100%

---


# Übersicht {#overview-content-transfer-tool}

Das Content Transfer-Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können.

Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch.

Beim Inhaltstransfer gibt es zwei Phasen:

1. **Extraktion**: Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als *Migrationssatz* bezeichnet wird. Ein *Migrationssatz* ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern.

   Weitere Informationen finden Sie unter [Extraktionsvorgang beim Inhaltstransfer](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process).

2. **Aufnahme**: Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem *Migrationssatz* in die Cloud Service-Zielinstanz.

   Weitere Informationen finden Sie unter [Aufnahmevorgang beim Inhaltstransfer](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process).

Ein *Migrationssatz* hat die folgenden Attribute:

* Während der Aktivität zum Inhaltstransfer können maximal vier Migrationssätze erstellt und gepflegt werden.
* Jeder Migrationssatz sollte einen eindeutigen Namen haben.
* Wenn ein Migrationssatz länger als 30 Tage inaktiv war, wird er automatisch gelöscht.
* Wenn Sie einen Migrationssatz erstellen, wird er einer bestimmten Umgebung zugeordnet. Sie können nur in eine Autoren- oder Veröffentlichungsinstanz derselben Umgebung aufnehmen.

Das Content Transfer-Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
> Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

In der Extraktionsphase muss die Option ***Überschreiben*** deaktiviert werden, um einen vorhandenen Migrationssatz *aufzufüllen*. Weitere Informationen finden Sie unter [Auffüllextraktion](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process).

In der Aufnahmephase muss die *Löschoption* deaktiviert werden, damit der Delta-Inhalt zusätzlich zum aktuellen Inhalt angewendet wird. Weitere Informationen finden Sie unter [Auffüllaufnahme](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process).


## Richtlinien und Best Practices {#best-practices}

Im folgenden Abschnitt erfahren Sie mehr über die Richtlinien und Best Practices für die Verwendung des Content Transfer-Tools:

* Es ist ratsam, die Überprüfungen zu Komprimierung und Konsistenz der Datenspeicher in den Repositorys vorab durchzuführen, um potenzielle Probleme zu erkennen und den im Repository vorhandenen Datenmüll zu reduzieren.

* Wenn das Content Delivery Network (CDN) von AEM Cloud Author so konfiguriert ist, dass eine Whitelist von IPs vorliegt, sollte sichergestellt werden, dass die IPs der Quellumgebung auch der Whitelist hinzugefügt werden, damit die Quellumgebung und die AEM Cloud-Umgebung miteinander kommunizieren können.

* In der Aufnahmephase wird empfohlen, die Aufnahme mit aktiviertem *Wischmodus* auszuführen, wobei das vorhandene Repository (Autor oder Veröffentlichung) in der Zielumgebung des AEM Cloud-Dienstes vollständig gelöscht und dann mit den Migrationssatzdaten aktualisiert wird. Dieser Modus ist viel schneller als der Nicht-Löschmodus, bei dem der Migrationssatz zusätzlich zum aktuellen Inhalt angewendet wird.

* Nach Abschluss der Aktivität zum Inhaltstransfer ist in der Cloud Service-Umgebung die korrekte Projektstruktur erforderlich, um sicherzustellen, dass der Inhalt in der Cloud Service-Umgebung erfolgreich gerendert wird.
