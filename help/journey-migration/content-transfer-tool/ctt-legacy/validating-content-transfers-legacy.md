---
title: Validieren von Inhaltsübertragungen (veraltet)
description: Validieren von Inhaltsübertragungen mithilfe des Content Transfer Tool
hide: true
hidefromtoc: true
exl-id: 304b7aee-1d84-4d90-a89b-0c532d5d9c92
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 100%

---

# Validieren von Inhaltsübertragungen   (Frühere Version) {#validating-content-transfers}

## Erste Schritte {#getting-started}

Benutzer können zuverlässig ermitteln, ob der gesamte vom Content Transfer Tool extrahierte Inhalt erfolgreich in die Zielinstanz aufgenommen wurde. Diese Validierungsfunktion vergleicht einen Auszug der während der Extraktion beteiligten Knoten mit einem Auszug der während der Aufnahme beteiligten Knoten. Wenn im Extraktions-Auszug Knotenpfade enthalten sind, die im Aufnahme-Auszug fehlen, gilt die Validierung als fehlgeschlagen, und es kann eine zusätzliche manuelle Validierung erforderlich sein.

>[!INFO]
>
>Diese Funktion ist ab Version 1.8.x des Content Transfer Tool (CTT) verfügbar. Die AEM as a Cloud Service-Zielumgebung muss mindestens Version 6158 oder höher ausführen. Außerdem muss die Quellumgebung für die Ausführung der [Vorabkopie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step) eingerichtet sein. Die Validierungsfunktion sucht in der Quelle nach der Datei azcopy.config. Wenn die Datei nicht gefunden werden kann, wird die Validierung nicht ausgeführt. Weitere Informationen zum Konfigurieren einer azcopy.config-Datei finden Sie auf [dieser Seite](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

Die Validierung eines Inhaltstransfers ist eine optionale Funktion. Durch die Aktivierung dieser Funktion wird sowohl die Zeit für die Durchführung einer Extraktion als auch für eine Aufnahme verlängert. Um die Funktion zu verwenden, aktivieren Sie sie in der Systemkonsole der AEM-Quellumgebung, indem Sie die folgenden Schritte ausführen:

1. Sie gelangen zur Adobe Experience Manager Web-Konsole in Ihrer Quellinstanz, indem Sie zu **Tools – Vorgänge – Web-Konsole** gehen oder direkt zur URL unter *https://serveraddress:serverport/system/console/configMgr*
1. Suchen Sie nach **Konfiguration des Content Transfer Tool-Extrahierungs-Service**
1. Über die Schaltfläche mit dem Stiftsymbol können Sie die Konfigurationswerte bearbeiten
1. Aktivieren Sie die Einstallung **Aktivieren der Migrationsvalidierung während der Extraktion**, und klicken Sie dann auf **Speichern**:

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

Wenn diese Einstellung aktiviert ist und die AEM as a Cloud Service-Zielumgebung eine kompatible Version ausführt, wird die Migrationsvalidierung bei allen folgenden Extraktionen und Aufnahmen durchgeführt.

Weitere Informationen zum Installieren des Content Transfer Tools finden Sie unter [Erste Schritte mit dem Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## Validieren eines Inhaltstransfers {#how-to-validate-a-content-transfer}

Wenn die Migrationsvalidierung in der Quell-AEM-Umgebung aktiviert ist, starten Sie eine Extraktion.

Wenn **Überschreiben des Staging-Containers während der Extraktion** aktiviert ist, werden alle Knoten, die an der Extraktion beteiligt sind, im Auszug des Extraktionspfads protokolliert. Wenn diese Einstellung verwendet wird, muss die Einstellung **Vorhandene Inhalte in der Cloud-Instanz vor der Aufnahme löschen** während der Aufnahme aktiviert sein, da andernfalls Knoten im Aufnahme-Auszug fehlen können. Hierbei handelt es sich um die Knoten, die bereits aus früheren Aufnahmen im Ziel vorhanden sind.

Eine grafische Darstellung dazu finden Sie in den folgenden Beispielen:

### Beispiel 1 {#example-1}

* **Extraktion (Überschreiben)**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTextractionoverwrite.png)

* **Aufnahme (Löschen)**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTingestionwipe.png)

* **Anmerkungen**

   Diese Kombination aus „Überschreiben“ und „Löschen“ führt zu konsistenten Validierungsergebnissen, auch für wiederholte Aufnahmen.

### Beispiel 2 {#example-2}

* **Extraktion**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTextraction.png)

* **Aufnahme**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTingestion.png)

* **Anmerkungen**

   Diese Kombination aus „Überschreiben“ und „Löschen“ führt zu konsistenten Validierungsergebnissen für die erste Aufnahme.

   Wenn die Aufnahme wiederholt wird, ist der Aufnahmeauszug leer, und die Validierung scheint fehlgeschlagen zu sein. Der Aufnahmeauszug ist leer, da alle Knoten dieser Extraktion bereits im Ziel vorhanden sind.

Sobald die Extraktion abgeschlossen ist, beginnen Sie mit der Aufnahme.

Am Anfang des Aufnahmeprotokolls befindet sich ein Eintrag, ähnlich `aem-ethos/tools:1.2.438`. Stellen Sie sicher, dass diese Versionsnummer **1.2.438** oder höher ist, andernfalls wird die Validierung von der AEM as a Cloud Service-Version, die Sie verwenden, nicht unterstützt.

Sobald die Aufnahme abgeschlossen ist und die Validierung beginnt, wird der folgende Protokolleintrag im Aufnahmeprotokoll vermerkt:

```
Gathering artifacts for migration validation...  
```

Die Details der Validierung folgen diesem Eintrag. Nachstehend finden Sie ein Beispiel für eine große Migration:

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

Dies ist ein Beispiel für eine erfolgreich durchgeführte Validierung, da im Aufnahmeauszug keine Einträge fehlten, die im Extraktionsauszug vorhanden waren.

So würde vergleichsweise ein Validierungsbericht aussehen, wenn die Validierung fehlgeschlagen wäre:

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

Das obige Fehlerbeispiel wurde durch Ausführen einer Aufnahme und anschließendes erneutes Ausführen derselben Aufnahme mit deaktiviertem Löschen erreicht, sodass während der Aufnahme keine Knoten beteiligt waren – alles war bereits auf dem Ziel vorhanden.

Der Validierungsbericht ist nicht nur im Aufnahmeprotokoll enthalten, sondern kann auch über die Benutzeroberfläche des Content Transfer Tool aufgerufen werden. Wählen Sie dazu einen Migrationssatz aus und klicken Sie in der Aktionsleiste auf die Schaltfläche **Validieren**:


![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidatebutton.png)

Das Dialogfeld „Validierungsprotokolle“ wird geöffnet:

![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidationlogs.png)

Verwenden Sie die Schaltfläche **Validieren des Veröffentlichungs-/Autorenberichts**, um den Validierungsbericht für die neueste Aufnahme in die jeweilige Ebene Ihrer Zielumgebung anzuzeigen. Unten finden Sie ein Beispiel aus einer kleinen Veröffentlichungsaufnahme:

![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidationreport.png)

>[!NOTE]
>
>Der Link **Validieren des Veröffentlichungs-/Autorenberichts** wird angezeigt, sobald die Aufnahme abgeschlossen ist. Darüber hinaus werden die Validierungsberichte beibehalten, sodass sie nach Abschluss der Aufnahme nicht ablaufen, wie dies bei den Aufnahmeprotokollen der Fall ist.

## Fehlerbehebung {#troubleshooting}

### Validierung fehlgeschlagen. Was jetzt? {#validation-fail}

Der erste Schritt besteht darin festzustellen, ob die Aufnahme wirklich fehlschlug oder ob die extrahierten Inhalte bereits in der Zielumgebung vorhanden sind. Dies kann vorkommen, wenn eine Aufnahme wiederholt wird, während die Option **Vorhandene Inhalte in der Cloud-Instanz vor der Aufnahme löschen** deaktiviert ist.

Wählen Sie zur Überprüfung einen Pfad aus dem Validierungsbericht aus und überprüfen Sie, ob er in der Zielumgebung vorhanden ist. Wenn es sich um eine Veröffentlichungsumgebung handelt, können Sie Seiten und Assets nur direkt überprüfen. Wenn Sie Hilfe zu diesem Schritt benötigen, eröffnen Sie ein Ticket bei der Kundenunterstützung.

### Die Knotenanzahl ist geringer als erwartet. Warum ist das so? {#node-count-lower-than-expected}

Einige Pfade von den Extraktions- und Aufnahmeauszügen werden vorsätzlich ausgeschlossen, damit die Größe dieser Dateien überschaubar bleibt, sodass das Ergebnis der Migrationsvalidierung innerhalb von zwei Stunden nach Abschluss der Aufnahme berechnet werden kann.

Zu den Pfaden, die wir derzeit aus den Auszügen ausschließen, gehören: `cqdam.text.txt`-Ausgabedarstellungen, Knoten in `/home` und Knoten in `/jcr:system`.
