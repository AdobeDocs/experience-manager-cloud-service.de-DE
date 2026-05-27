---
title: Verwenden der AEM Cloud-Migrationsfertigkeit
description: Referenz für jedes Migrationsmuster, das von AEM Cloud Migration unterstützt wird, einschließlich OSGi-Konfigurationskonvertierung, BPA-Quelloptionen und Sitzungsverwaltungsanleitungen.
feature: Migration
role: Developer
source-git-commit: 5cda629090d9a9d020deca5192b8a89659ec4749
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---


# Verwenden der AEM Cloud-Migrationsfertigkeit {#using-cloud-migration-skill}

Diese Referenz behandelt alle unterstützten Migrationsmuster, die Bereitstellung von BPA-Ergebnissen und die Verwaltung von Sitzungen in einem großen Projekt. Eine Einführung und Einrichtungsanweisungen finden Sie in der [Übersicht](/help/journey-migration/cloud-migration-skill/overview-cloud-migration-skill.md).

## Funktionsweise von Sitzungen {#workflow-overview}

Jede Migrationssitzung folgt dieser Reihenfolge:

1. **Benennen des Musters**: Geben Sie ein Muster an (z. B. `scheduler`)
2. **Ergebnisse bereitstellen**: aus einer BPA-CSV-Datei, CAM über MCP oder bestimmten Dateipfaden
3. **Agent liest Umwandlungsregeln**: Die Kenntnis liest das relevante Best-Practices-Modul, bevor sie Code-Änderungen vornimmt
4. **Erster Batch von fünf**: Der Agent wandelt bis zu fünf Funde um und meldet, was er geändert hat
5. **Sie überprüfen und fortfahren**: Nachdem Sie jeden Batch überprüft haben, `continue` Sie, um mit dem nächsten fortzufahren

Der Agent verarbeitet jeweils ein Muster und einen Batch. Er wird nicht automatisch fortgesetzt. Für jeden Batch ist eine Bestätigung erforderlich.

## Migrationsmuster {#patterns}

### Planung {#scheduler}

Targeting von Java-Klassen mit `sling.commons.scheduler`- oder `Scheduler`, die mit der statuslosen, containerisierten Laufzeit von AEMaaCS nicht kompatibel sind.

**BPA-Muster-ID:** `scheduler`

Der Agent konvertiert `Scheduler`-injizierte Aufträge mithilfe von `@Designate` in `@Component` Implementierungen von `Runnable` und ersetzt die konstruktorbasierte Scheduler-Registrierung durch `@Activate`-/`@Deactivate`-Lebenszyklusmethoden.

### ResourceChangeListener {#resource-change-listener}

Targeting `ResourceChangeListener` oder `ResourceChange` Listener-Implementierungen, die Aktualisierungen für AEMaaCS erfordern.

**BPA-Muster-ID:** `resourceChangeListener`

### Replikation {#replication}

Targeting-Klassen, die `com.day.cq.replication.Replicator` oder zugehörige Replikations-APIs importieren, die in AEMaaCS nicht unterstützt werden. Der Agent ersetzt sie durch `ContentDistribution` Äquivalente und aktualisiert die entsprechenden OSGi-Service-Verweise.

**BPA-Muster-ID:** `replication`

### Ereignis-Listener {#event-listener}

Targeting von OSGi-`EventListener` oder `EventHandler`, die für die Semantik der AEMaaCS-Ereignisverarbeitung aktualisiert werden müssen.

**BPA-Muster-ID:** `eventListener`

### Ereignishandler {#event-handler}

Targeting von synchronen OSGi-`EventHandler`, die für AEMaaCS angepasst werden müssen.

**BPA-Muster-ID:** `eventHandler`

### Asset-API {#asset-api}

Targeting von Klassen mit veralteten `AssetManager`, `DAMEvent` oder nicht unterstützten DAM-APIs. Der Agent ersetzt sie durch die unterstützten AEM Assets-API-Entsprechungen.

**BPA-Muster-ID:** `assetApi`

### HTL-Link (data-sly-test) {#htl-lint}

Targeting von HTL-Vorlagen unter `ui.apps`, die `data-sly-test: redundant constant value comparison` Lint-Warnungen erzeugen. Der Agent erkennt betroffene Vorlagen, indem er das Inhaltspaket direkt scannt. Für dieses Muster ist keine BPA-CSV- oder CAM-Verbindung erforderlich.

**BPA-Muster-ID:** `htlLint`

>[!NOTE]
>`htlLint` Ergebnisse werden nicht in BPA-CSV-Exporten angezeigt. Der Agent erkennt sie durch direkte Dateiüberprüfung, wenn Sie eine Sitzung mit diesem Muster starten.

### OSGi-Konfigurationen in Cloud Manager {#osgi-cloud-manager}

Konvertiert OSGi-Konfigurationen in `ui.config` in das Cloud Manager-kompatible `.cfg.json`-Format mit vollständiger umgebungsspezifischer Handhabung. Dies umfasst zwei miteinander verknüpfte Aufgaben:

**Formatkonvertierung konfigurieren**

AEMaaCS erfordert, dass OSGi-Konfigurationen als `.cfg.json`-Dateien gespeichert werden, mit umgebungsspezifischen Konfigurationen in Ordnern, die den Ausführungsmodus betreffen (`config.author/`, `config.publish/`, `config.dev/` usw.). Der Agent:

* Konvertiert vorhandene OSGi-Konfigurationen im `.config`-, `.cfg`- und XML-Format in `.cfg.json`
* Teilt Konfigurationen, die sowohl autoren- als auch veröffentlichungsspezifische Werte enthalten, in separate Dateien mit Ausführungsmodus-Bereich auf.
* Validiert Eigenschaftstypen anhand der OSGi-Metatypspezifikation (Zeichenfolgen, Ganzzahlen, boolesche Werte, Arrays)
* Kennzeichnet Adobe-eigene PIDs für die manuelle Überprüfung, anstatt sie automatisch zu konvertieren

**Geheimnisse und Umgebungsvariablen**

Verschiebt Nur-Text-Geheimnisse und umgebungsspezifische Werte aus den bestätigten Konfigurationsdateien und ersetzt sie durch Cloud Manager-Platzhalter:

* `$[secret:NAME]`: für Kennwörter, Token und andere vertrauliche Werte
* `$[env:NAME]`: für nicht vertrauliche Werte, die sich je nach Umgebung unterscheiden (z. B. Service-URLs)

Die entsprechenden Variablen und Geheimnisse werden in Cloud Manager angewendet und zur Laufzeit eingefügt. In der Quell-Code-Verwaltung werden keine Werte gespeichert.

>[!IMPORTANT]
>Der Agent gibt in der Konversation nie geheime Werte aus. Alle sensiblen Daten werden in eine ignorierte Übergabedatei geschrieben, damit Sie sie über die Cloud Manager-API oder die Benutzeroberfläche anwenden können.

**Dieses Muster verwendet weder BPA CSV noch CAM.** Sitzung starten mit:

```
Scan my config files and create Cloud Manager environment secrets or variables.
```

## BPA-Source-Optionen {#bpa-source}

| Quelle | Wann ist sie einzusetzen? |
|--------|------------|
| **BPA-CSV-Datei** | Sie haben eine CSV aus Ihrer AEM-Instanz oder Cloud Acceleration Manager exportiert. Geben Sie den Dateipfad an, wenn Sie die Sitzung starten. |
| **CAM über MCP** | Sie haben die AEM Cloud Migration MCP konfiguriert. Der Agent listet Ihre CAM-Projekte auf, Sie bestätigen, welches verwendet werden soll, und die Ergebnisse werden direkt abgerufen. Siehe [Verwenden des Cloud Migration MCP](/help/journey-migration/cloud-migration-skill/using-cloud-migration-mcp.md). |
| **Manuelle Dateipfade** | Sie möchten bestimmte Dateien ohne BPA-Bericht migrieren. Geben Sie die Pfade direkt in Ihrer Eingabeaufforderung an. |

### MCP-Fehlerbehandlung {#mcp-errors}

Wenn die MCP-Verbindung einen Fehler zurückgibt (einschließlich „Projekt nicht gefunden“ oder Authentifizierungsfehler), stoppt der Agent und zeigt den Fehler an. Es wechselt nicht automatisch zu einer anderen Quelle. Vom Status Angehalten aus haben Sie folgende Möglichkeiten:

* Bestätigen Sie das richtige Projekt aus der Liste, die der Agent angezeigt hat
* Geben Sie alternativ einen BPA-CSV-Pfad an.
* Spezifische Java-Dateipfade für eine manuelle Migration angeben

## Verwalten von Sitzungen in großen Berichten {#large-reports}

Bei BPA-Berichten mit vielen Ergebnissen ermöglicht der Batch-für-Batch-Ansatz eine inkrementelle Validierung:

1. Überprüfen Sie die Unterschiede für jeden Batch
2. Übergeben Sie den Batch mit einer Commit-Nachricht im Musterbereich
3. Zum Starten des nächsten Batches `continue` antworten
4. Wiederholen Sie den Vorgang, bis der Agent meldet, dass alle Ergebnisse für das Muster abgeschlossen sind

**Ein Muster pro Commit** sorgt dafür, dass der Git-Verlauf lesbar bleibt, und erleichtert die Wiederherstellung einzelner Mustertransformationen.

>[!NOTE]
>Wenn Sie eine Sitzung beenden, bevor alle Ergebnisse verarbeitet werden, starten Sie mit demselben Muster und derselben BPA-Quelle in einer neuen Sitzung neu. Der Agent wird von dort fortgesetzt, wo er aufgehört hat.

## Workspace-Umfang {#workspace-scope}

Der Agent sucht und bearbeitet Dateien nur in den geöffneten IDE-Arbeitsbereichordnern. Übergeordnete Verzeichnisse, gleichrangige Ordner oder andere Speicherorte auf der Festplatte werden nicht überprüft.

Wenn eine BPA-Suche auf einen Dateipfad verweist, der nicht im Arbeitsbereich vorhanden ist, stoppt der Agent und teilt Ihnen mit, welche Pfade fehlen. Öffnen Sie den richtigen Projektordner oder geben Sie die Pfade explizit an, um fortzufahren.

