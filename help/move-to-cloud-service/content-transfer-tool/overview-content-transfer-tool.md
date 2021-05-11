---
title: Übersicht über das Content Transfer Tool
description: Übersicht über das Content Transfer Tool
exl-id: 4715937e-4c4c-4680-af15-016db4fe7db9
translation-type: tm+mt
source-git-commit: 1fb9814f10ef8eae87a7eef9f390700f2f2127d8
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 77%

---

# Übersicht {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Überblick"
>abstract="Content Transfer Tool ist ein von der Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer Quellinstanz (lokal oder AMS) in die Zielgruppe AEM Cloud Service-Instanz verschieben können. Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#extraction-process" text="Extraktion"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#ingestion-process" text="Einstiegsprozess"

Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können.

Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch.

Beim Inhaltstransfer gibt es zwei Phasen:

1. **Extraktion**: Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als *Migrationssatz* bezeichnet wird. Ein *Migrationssatz* ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern.

   Weitere Informationen finden Sie unter [Extraktionsvorgang beim Inhaltstransfer](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process).

>[!NOTE]
>
> Es wird empfohlen, das User Mapping Tool als Teil der Extraktion auszuführen. Weitere Informationen finden Sie unter [Verwenden des User Mapping Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#cloud-migration).

1. **Aufnahme**: Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem *Migrationssatz* in die Cloud Service-Zielinstanz.

   Weitere Informationen finden Sie unter [Aufnahmevorgang beim Inhaltstransfer](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process).

Ein *Migrationssatz* hat die folgenden Attribute:

* Während der Aktivität zur Inhaltsübertragung können maximal zehn Migrationssets erstellt und gepflegt werden.
* Jeder Migrationssatz sollte einen eindeutigen Namen haben.
* Wenn ein Migrationssatz länger als 30 Tage inaktiv war, wird er automatisch gelöscht.
* Wenn Sie einen Migrationssatz erstellen, wird er einer bestimmten Umgebung zugeordnet. Sie können nur in eine Autoren- oder Veröffentlichungsinstanz derselben Umgebung aufnehmen.


Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

In der Extraktionsphase muss die Option ***Überschreiben*** deaktiviert werden, um einen vorhandenen Migrationssatz *aufzufüllen*. Weitere Informationen finden Sie unter [Auffüllextraktion](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process).

In der Aufnahmephase muss die *Löschoption* deaktiviert werden, damit der Delta-Inhalt zusätzlich zum aktuellen Inhalt angewendet wird. Weitere Informationen finden Sie unter [Auffüllaufnahme](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process).


## Richtlinien und Best Practices {#best-practices}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Richtlinien und Best Practices"
>abstract="Lesen Sie die Richtlinien und Best Practices für die Verwendung des Content Transfer-Tools, einschließlich Aufgaben zur Bereinigung von Revisionen, Überlegungen zum Festplattenspeicherplatz und mehr."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs" text="Wichtige Überlegungen zur Verwendung des Content Transfer Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Wichtige Überlegungen zur Verwendung des Tools für die Benutzerzuordnung"

Im folgenden Abschnitt erfahren Sie mehr über die Richtlinien und Best Practices für die Verwendung des Content Transfer Tools:

* Es wird empfohlen, ein [Revision Cleanup](https://docs.adobe.com/content/help/de-DE/experience-manager-65/deploying/deploying/revision-cleanup.html) und [Datenspeicher-Konsistenzprüfungen](https://helpx.adobe.com/de/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) im **Quell**-Repository durchzuführen, um potenzielle Probleme zu identifizieren und die Größe des Repositorys zu reduzieren.

* Wenn das Content Delivery Network (CDN) von AEM Cloud Author so konfiguriert ist, dass eine Whitelist von IPs vorliegt, sollte sichergestellt werden, dass die IPs der Quellumgebung auch der Zulassungsliste hinzugefügt werden, damit die Quellumgebung und die AEM Cloud-Umgebung miteinander kommunizieren können.

* In der Aufnahmephase wird empfohlen, die Aufnahme mit aktiviertem *Wischmodus* auszuführen, wobei das vorhandene Repository (Autor oder Veröffentlichung) in der Zielumgebung von AEM Cloud Service vollständig gelöscht und dann mit den Migrationssatzdaten aktualisiert wird. Dieser Modus ist viel schneller als der Nicht-Löschmodus, bei dem der Migrationssatz zusätzlich zum aktuellen Inhalt angewendet wird.

* Nach Abschluss der Aktivität zum Inhaltstransfer ist in der Cloud Service-Umgebung die korrekte Projektstruktur erforderlich, um sicherzustellen, dass der Inhalt in der Cloud Service-Umgebung erfolgreich gerendert wird.

* Stellen Sie sicher, dass im Unterverzeichnis `crx-quickstart` der AEM-Quellinstanz genügend Speicherplatz vorhanden ist, bevor Sie das Content Transfer Tool ausführen. Dies ist notwendig, da das Content Transfer Tool eine lokale Kopie des Repositorys erstellt, die später in den Migrationssatz hochgeladen wird.
Die allgemeine Formel zur Berechnung des erforderlichen freien Festplattenspeicherplatzes lautet wie folgt:
   `data store size + node store size * 1.5`

   * *Datenspeichergröße*: Das Content Transfer Tool verwendet 64 GB, auch wenn der eigentliche Datenspeicher größer ist.
   * *Knotenspeichergröße*: Größe des Segmentspeicherverzeichnisses oder der MongoDB-Datenbank.
Bei einer Segmentspeichergröße von 20 GB wären daher 94 GB freier Speicherplatz erforderlich.

* Ein Migrationssatz muss während der gesamten Aktivität der Inhaltsübertragung beibehalten werden, um Inhaltsaktualisierungen zu unterstützen. Da während der Aktivität der Inhaltsübertragung maximal zehn Migrationssätze erstellt und gepflegt werden können, wird empfohlen, das Inhalts-Repository entsprechend zu unterteilen, um sicherzustellen, dass Ihnen die Migrationssätze nicht ausgehen.  während/Struktur der Migration entsprechend festgelegt.
