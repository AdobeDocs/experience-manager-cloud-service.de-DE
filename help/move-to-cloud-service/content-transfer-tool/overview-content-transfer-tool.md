---
title: Übersicht über das Inhaltsübermittlungstool
description: Übersicht über das Inhaltsübermittlungstool
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Überblick {#overview-content-transfer-tool}

Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (lokal oder AMS) in die AEM Cloud-Dienstinstanz der Zielgruppe verschieben können.

Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch.

Der Inhaltsübertragung sind zwei Phasen zugeordnet:

1. **Extraktion**:  Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als *Migrationsset* bezeichnet wird. Ein *Migrationsset* ist ein Cloud-Datenspeicherung-Bereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der AEM-Instanz des Cloud-Dienstes zu speichern.

   Weitere Informationen finden Sie unter [Extraktion Process in Content Transfer](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process) .

2. **Ingestion**: &quot;Einbettung&quot;bezieht sich auf die Inhaltsaufnahme aus dem *Migrationsset* in der Zielgruppe Cloud-Dienstinstanz.

   Weitere Informationen finden Sie unter [Ingestion Process in Content Transfer](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process) .

Ein *Migrationssatz* hat die folgenden Attribute:

* Während der Aktivität zur Inhaltsübertragung können maximal vier Migrationssets erstellt und gepflegt werden.
* Jeder Migrationssatz sollte einen eindeutigen Namen haben.
* Wenn ein Migrationsset länger als 30 Tage inaktiv war, wird er automatisch gelöscht.
* Wenn Sie einen Migrationssatz erstellen, wird er einer bestimmten Umgebung zugeordnet. Sie können nur eine Instanz im Autorenmodus oder in eine Instanz im Veröffentlichungsmodus derselben Umgebung aufnehmen.

Das Inhaltsübermittlungstool verfügt über eine Funktion, mit der das Aufstocken von differenziellen Inhalten unterstützt wird, wenn nur Änderungen übertragen werden können, die seit der vorherigen Aktivität der Inhaltsübertragung vorgenommen wurden.

>[!NOTE]
> Nach der ersten Inhaltsübertragung wird empfohlen, häufig differenzielle Inhaltsaufstockungen durchzuführen, um die Einfrierzeit für die endgültige Übertragung von differenziellen Inhalten zu verkürzen, bevor Sie mit Cloud Service live gehen.

In der Extraktion muss die Option &quot; ***Überschreiben*** &quot;deaktiviert werden, um einen vorhandenen Migrationssatz zu *ergänzen* . Weitere Informationen finden Sie in der [Top-Up-Extraktion](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process) .

Wenn Sie während der Erfassung den Delta-Inhalt auf den aktuellen Inhalt anwenden möchten, muss die Option &quot; *Wischen* &quot;deaktiviert sein. Weitere Informationen finden Sie unter [Top-Up-Einbindung](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process) .


## Leitlinien und bewährte Verfahren {#best-practices}

Befolgen Sie den unten stehenden Abschnitt, um die Richtlinien und Best Practices für die Verwendung des Content Transfer Tool zu verstehen:

* Es ist ratsam, vor der Hand Vergleichs- und Datenspeicherkonsistenzprüfungen in den Repositorys durchzuführen, um potenzielle Probleme zu erkennen und auch den im Repository vorhandenen Müll zu reduzieren.

* Wenn die AEM Cloud Author Content Versand Network (CDN)-Konfiguration so konfiguriert ist, dass eine Whitelist von IPs vorliegt, sollte sichergestellt werden, dass die Quell-Umgebung-IPs auch der Whitelist hinzugefügt werden, damit die Quell-Umgebung und die AEM Cloud-Umgebung miteinander kommunizieren können.

* In der Erfassungsphase wird empfohlen, die Erfassung mit dem aktivierten *Wischmodus* auszuführen, wobei das vorhandene Repository (Autor oder Veröffentlichung) in der Zielgruppe-AEM Cloud-Dienst-Umgebung vollständig gelöscht und dann mit den Migrationssatzdaten aktualisiert wird. Dieser Modus ist viel schneller als der Nicht-Wischen-Modus, bei dem der Migrationssatz auf den aktuellen Inhalt angewendet wird.

* Nach Abschluss der Aktivität zur Inhaltsübertragung ist die richtige Projektstruktur in der Cloud-Dienst-Umgebung erforderlich, um sicherzustellen, dass die Inhalte in der Cloud-Dienst-Umgebung erfolgreich wiedergegeben werden.