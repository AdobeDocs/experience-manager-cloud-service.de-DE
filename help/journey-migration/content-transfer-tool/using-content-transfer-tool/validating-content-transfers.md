---
title: Validieren von Inhaltsübertragungen
description: Validieren von Inhaltsübertragungen mithilfe des Content Transfer Tool
source-git-commit: c542b631a94b9fcbda4790ca9ca5a461d104c790
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 2%

---


# Validieren von Inhaltsübertragungen {#validating-content-transfers}

## Erste Schritte {#getting-started}

Benutzer können zuverlässig ermitteln, ob der gesamte vom Content Transfer Tool extrahierte Inhalt erfolgreich in die Zielinstanz aufgenommen wurde. Diese Validierungsfunktion vergleicht eine Zusammenfassung der während der Extraktion beteiligten Knoten mit einer Zusammenfassung der während der Aufnahme beteiligten Knoten. Wenn im ExtraktionsDigest Knotenpfade enthalten sind, die in der Aufnahme-Digest fehlen, gilt die Validierung als fehlgeschlagen und es kann eine zusätzliche manuelle Validierung erforderlich sein.

>[!INFO]
>
>Diese Funktion ist ab Version 1.8.x des Content Transfer Tool (CTT) verfügbar. Die AEM Cloud Service-Zielumgebung muss mindestens Version 6158 oder höher ausführen. Außerdem muss die Quellumgebung für die Ausführung eingerichtet werden [pre-copy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step). Die Validierungsfunktion sucht in der Quelle nach der Datei azcopy.config . Wenn die Datei nicht gefunden werden kann, wird die Validierung nicht ausgeführt. Weitere Informationen zum Konfigurieren einer Datei &quot;azcopy.config&quot;finden Sie unter [diese Seite](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

Die Validierung eines Inhaltstransfers ist eine optionale Funktion. Durch die Aktivierung dieser Funktion wird sowohl die Zeit für die Durchführung einer Extraktion als auch für eine Aufnahme verlängert. Um die Funktion zu verwenden, aktivieren Sie sie in der Systemkonsole der AEM-Quellumgebung, indem Sie die folgenden Schritte ausführen:

1. Navigieren Sie zur Adobe Experience Manager Web Console in Ihrer Quellinstanz, indem Sie zu **Tools - Vorgänge - Web-Konsole** oder direkt auf die URL unter *https://serveraddress:serverport/system/console/configMgr*
1. Suchen Sie nach **Konfiguration des Inhaltstransfer-Tool-Extrahierungsdienstes**
1. Über die Schaltfläche mit dem Stiftsymbol können Sie die Konfigurationswerte bearbeiten
1. Aktivieren Sie die **Aktivieren der Migrationsvalidierung während der Extraktion** Einstellung festlegen, und drücken Sie dann **Speichern**:

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

Wenn diese Einstellung aktiviert ist und die AEM Cloud Service-Zielumgebung eine kompatible Version ausführt, wird die Migrationsprüfung bei allen folgenden Extraktionen und Aufnahmen durchgeführt.

Weitere Informationen zum Installieren des Content Transfer Tool finden Sie unter [Erste Schritte mit dem Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## Validieren eines Inhaltstransfers {#how-to-validate-a-content-transfer}

Wenn die Migrationsprüfung für die Quell-AEM-Umgebung aktiviert ist, starten Sie eine Extraktion.

Wenn **Überschreiben des Staging-Containers während der Extraktion** aktiviert ist, werden alle Knoten, die an der Extraktion beteiligt sind, beim Digest des Extraktionspfads protokolliert. Wenn diese Einstellung verwendet wird, muss die **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** während der Aufnahme festgelegt wurde, da andernfalls Knoten in der Aufnahme-Digest fehlen können. Hierbei handelt es sich um die Knoten, die bereits von früheren Aufnahmen auf der Zielgruppe vorhanden sind.

Eine grafische Darstellung dieses Problems finden Sie in den folgenden Beispielen:

### Beispiel 1 {#example-1}

* **Extraktion (überschreiben)**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTextractionoverwrite.png)

* **Aufnahme (Bereinigen)**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTingestionwipe.png)

* **Anmerkungen**

   Diese Kombination aus &quot;Überschreiben&quot;und &quot;Bereinigen&quot;führt zu konsistenten Validierungsergebnissen, auch für wiederholte Aufnahmen.

### Beispiel 2 {#example-2}

* **Extraktion**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTextraction.png)

* **Aufnahme**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTingestion.png)

* **Anmerkungen**

   Diese Kombination aus &quot;Überschreiben&quot;und &quot;Bereinigen&quot;führt zu konsistenten Validierungsergebnissen für die erste Aufnahme.

   Wenn die Aufnahme wiederholt wird, ist der Aufnahmedigest leer, und die Validierung scheint fehlgeschlagen zu sein. Der Aufnahme-Digest ist leer, da alle Knoten dieser Extraktion bereits in der Zielgruppe vorhanden sind.

Sobald die Extraktion abgeschlossen ist, beginnen Sie mit der Aufnahme.

Am Anfang des Aufnahmeprotokolls befindet sich ein Eintrag, der dem `aem-ethos/tools:1.2.438`. Stellen Sie sicher, dass diese Versionsnummer **1,2 438** oder höher, andernfalls wird die Validierung von der Veröffentlichung AEM as a Cloud Service, die Sie verwenden, nicht unterstützt.

Sobald die Aufnahme abgeschlossen ist und die Validierung beginnt, wird der folgende Protokolleintrag im Aufnahmeprotokoll vermerkt:

```
Gathering artifacts for migration validation...  
```

Die Details der Validierung folgen diesem Eintrag. Suchen Sie unten ein Beispiel aus einer großen Migration:

```
Beginning publish migration validation. Migration job id=[3aba1f96-84b6-4bd0-8642-c61c0d528387]
Extraction path digest is being processed...
Extraction path digest processing took 982 seconds
Ingestion path digest is being processed...
Ingestion path digest processing took 999 seconds
Comparing the Extraction and Ingestion path digests...
----------------------------------------------------------
EXTRACTION: Number of nodes extracted: 51674784
INGESTION: Number of nodes ingested: 51674784
----------------------------------------------------------
Validation succeeded! No entries were detected to be missing from the ingestion digest.
----------------------------------------------------------
Comparing the path digests took 29 seconds
Migration validation took 33 minutes
```

Dies ist ein Beispiel für eine erfolgreich durchgeführte Validierung, da in der Aufnahmedigest keine Einträge fehlten, die in der ExtraktionsDigest vorhanden waren.

So würde ein Validierungsbericht aussehen, wenn die Validierung fehlgeschlagen wäre:

```
Beginning publish migration validation. Migration job id=[ac217e5a-a08d-4e81-cbd6-f39f88b174ce]
Extraction path digest is being processed...
Extraction path digest processing took 0 seconds
Ingestion path digest is being processed...
Ingestion path digest processing took 0 seconds
Comparing the Extraction and Ingestion path digests...
----------------------------------------------------------
EXTRACTION: Number of nodes extracted: 4635
INGESTION: Number of nodes ingested: 0
----------------------------------------------------------
Validation failed. However, the following nodes may already be present in the target environment.
Please refer to our Migration Validation FAQ (https://www.adobe.com/go/aem_cloud_ctt_validation_en) or open a ticket with Customer Care.
There are 4635 entries present in the extraction digest that are missing from the ingestion digest.
/content/dam/bruce
/content/dam/bruce-assets
... more paths listed (up to 10k) ...
----------------------------------------------------------
Comparing the path digests took 0 seconds
Migration validation took 0 minutes
```

Das obige Fehlerbeispiel wurde durch Ausführen einer Aufnahme und anschließendes erneutes Ausführen derselben Aufnahme mit deaktiviertem Bereinigen erreicht, sodass während der Aufnahme keine Knoten beteiligt waren - alles war bereits auf dem Ziel vorhanden.

Der Validierungsbericht ist nicht nur im Aufnahmeprotokoll enthalten, sondern kann auch über die Benutzeroberfläche des Content Transfer Tool aufgerufen werden. Wählen Sie dazu einen Migrationssatz aus und klicken Sie auf das **Bestätigen** in der Aktionsleiste:


![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidatebutton.png)

Das Dialogfeld &quot;Validierungsprotokolle&quot;wird geöffnet:

![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidationlogs.png)

Verwenden Sie die **Validieren des Veröffentlichungs-/Autorenberichts** -Schaltfläche, um den Validierungsbericht für die neueste Aufnahme in die jeweilige Ebene Ihrer Zielumgebung anzuzeigen. Unten finden Sie ein Beispiel aus einer kleinen Veröffentlichungsaufnahme:

![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidationreport.png)

>[!NOTE]
>
>Die **Validieren des Veröffentlichungs-/Autorenberichts** wird angezeigt, sobald die Aufnahme abgeschlossen ist. Darüber hinaus werden die Validierungsberichte beibehalten, sodass sie nach Abschluss der Aufnahme nicht ablaufen, wie dies in den Aufnahmeprotokollen der Fall ist.

## Fehlerbehebung {#troubleshooting}

### Validierung fehlgeschlagen. Was jetzt? {#validation-fail}

Der erste Schritt besteht darin festzustellen, ob die Aufnahme wirklich fehlschlug oder ob der extrahierte Inhalt bereits in der Zielumgebung vorhanden ist. Dies kann vorkommen, wenn eine Aufnahme mit der **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** Option deaktiviert.

Wählen Sie zur Überprüfung einen Pfad aus dem Validierungsbericht aus und überprüfen Sie, ob er in der Zielumgebung vorhanden ist. Wenn es sich um eine Veröffentlichungsumgebung handelt, können Sie sich darauf beschränken, Seiten und Assets direkt zu überprüfen. Wenn Sie Hilfe zu diesem Schritt benötigen, öffnen Sie ein Ticket bei der Kundenunterstützung.

### Die Knotenanzahl ist geringer als erwartet. Warum ist das so? {#node-count-lower-than-expected}

Einige Pfade von den Extraktions- und Aufnahmedigesten werden vorsätzlich ausgeschlossen, damit die Größe dieser Dateien überschaubar bleibt, sodass das Ergebnis der Migrationsvalidierung innerhalb von zwei Stunden nach Abschluss der Aufnahme berechnet werden kann.

Zu den Pfaden, die wir derzeit aus den Digests ausschließen, gehören: `cqdam.text.txt` Ausgabedarstellungen, Knoten in `/home`und Knoten in `/jcr:system`.




