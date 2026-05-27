---
title: KI-gestützte Code-Migration zu AEM as a Cloud Service
description: Überblick über die AEM Cloud Migration Skills und MCP, eine KI-Agent-Lösung, die BPA-Ergebnisse liest und AEM 6.x-Code nach Muster zu AEM as a Cloud Service migriert.
feature: Migration
role: Developer
source-git-commit: 85b630684db9de7e16e3a52203f55bca5846f66e
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 1%

---


# KI-gestützte Code-Migration zu AEM as a Cloud Service {#cloud-migration-skill-overview}

Die **AEM Cloud Migration**-Lösung ist ein agentenbasiertes Toolset, das Entwicklerinnen und Entwickler durch die Migration von AEM 6.x, AMS oder On-Premise-Java-Code und OSGi-Konfigurationen zu **AEM as a Cloud Service (AEMaaCS)**. Es funktioniert in jeder KI-aktivierten IDE, die Agentenfähigkeiten unterstützt, und im Model Context Protocol (MCP).

Das folgende Demovideo bietet eine kurze Beschreibung der AEM Cloud-Migrationslösung und ist als Referenz enthalten.

>[!VIDEO](https://publish.tv.adobe.com/bucket/7642/category/12553/video/3491438/)

Die Lösung besteht aus zwei Komponenten:

| Komponente | Rolle |
|-----------|------|
| **Migrationsfertigkeit** | Orchestriert den Migrations-Workflow, ruft Best Practices Analyzer (BPA)-Ergebnisse ab, identifiziert betroffene Dateien in Ihrem Projekt und wendet Code-Umwandlungen musterweise an. Funktioniert mit einem lokalen BPA-CSV-Export oder mit dem Cloud Migration MCP (empfohlen). |
| **Cloud-Migration - MCP** | Verbindet Ihren IDE-Agenten mit Cloud Acceleration Manager (CAM), sodass er BPA-Ergebnisse direkt ohne CSV-Export abrufen kann. Wird anstelle einer lokalen CSV-Datei für die aktuellsten Ergebnisse empfohlen. |

## Voraussetzungen {#prerequisites}

- Ein AEM-Projekt (Maven oder Gradle), das in Ihrer IDE geöffnet ist
- Eine der folgenden BPA-Suchquellen (wird dringend empfohlen, ist für manuelle Flüsse nicht erforderlich):
   - Ein **BPA-CSV-** aus Ihrer AEM-Instanz
   - Ein **Cloud Acceleration Manager-Projekt** mit hochgeladenem BPA-Bericht und konfiguriertem MCP für die Cloud-Migration

## Die Migrationsfertigkeit {#migration-skill}

Die Migrationsfertigkeit ist eine Agentenfertigkeit für KI-aktivierte IDEs. Er orchestriert einen **ein-Muster-pro-Sitzung**-Workflow: Sie benennen das zu behebende Muster, verweisen den Agenten auf Ihre BPA-Ergebnisse, und der Agent liest die relevanten Umwandlungsregeln, findet die betroffenen Dateien in Ihrem Projekt und wendet die Änderungen in Batches von jeweils fünf an und hält Sie nach jedem Batch zur Überprüfung an.

### Unterstützte Muster {#supported-patterns}

| Muster | Fehlerbehebungen |
|---------|--------------|
| `scheduler` | `sling.commons.scheduler` Aufträge sind mit der statuslosen -Laufzeit von AEMaaCS nicht kompatibel |
| `resourceChangeListener` | `ResourceChangeListener` Implementierungen, die Cloud Service-Updates erfordern |
| `replication` | Alte `Replicator` API-Aufrufe wurden durch `ContentDistribution` Äquivalente ersetzt |
| `eventListener` | Aktualisierte OSGi-`EventListener` für die AEMaaCS-Ereignissemantik |
| `eventHandler` | Für Cloud Service angepasste synchrone OSGi-`EventHandler` |
| `assetApi` | Veraltete `AssetManager`- und DAM-API-Aufrufe wurden durch unterstützte Entsprechungen ersetzt |
| `htlLint` | `data-sly-test` von redundanten, konstanten Vergleichswarnungen in HTL-Vorlagen |
| OSGi-Konfigurationen | `.cfg.json`, Berechnung des Ausführungsmodus und Extraktion von Cloud Manager-Geheimnissen/env-var |

Die Qualifikation delegiert alle Code-Umwandlungsschritte an die Companion-`best-practices`-Qualifikation. Beide werden zusammen als das Paket für `aem-cloud-service` Kenntnisse verteilt. Installieren Sie das Paket einmal, um beide zu erhalten.

### Erste Schritte {#getting-started-skill}

1. Installieren Sie das `aem-cloud-service` Skill-Paket aus dem [Adobe Skills Repository](https://github.com/adobe/skills).
2. Öffnen Sie Ihr AEM-Projekt als Workspace-Stamm in Ihrer IDE.
3. Abrufen von BPA-Ergebnissen: Exportieren Sie eine CSV-Datei aus BPA oder konfigurieren Sie die MCP für die Cloud-Migration (siehe unten).
4. Starten Sie eine Sitzung mit Ihrem Agenten über eine der folgenden Eingabeaufforderungen:

   **BPA CSV:**

   ```
   Use the migration skill: scheduler only, BPA CSV at ./reports/bpa.csv
   ```

   **CAM über MCP:**

   ```
   Fix replictaion findings from project <projectname>/<projectId>.
   ```

   **Manuell (kein BPA):**

   ```
   Migrate event listener in core/src/main/java/com/example/Listener.java
   ```

   **OSGi-Konfigurationen:**

   ```
   Scan my config files and create Cloud Manager environment secrets or variables.
   ```

   **HTL-Link:**

   ```
   Fix htlLint in ui.apps - scan for data-sly-test redundant constant warnings.
   ```

>[!NOTE]
>Die Qualifikation verarbeitet ein Muster pro Sitzung. Wenn Ihr BPA-Bericht mehrere Muster enthält, werden Sie vom Agenten aufgefordert, eines auszuwählen, bevor Sie beginnen.

Eine vollständige Anleitung zum Pattern-Referenzhandbuch und zur Sitzungsverwaltung finden Sie unter [Verwenden der Cloud-Migrationsfertigkeit](/help/journey-migration/cloud-migration-skill/using-cloud-migration-skill.md).

## MCP der Cloud-Migration {#cloud-migration-mcp}

Der **AEM Cloud Migration MCP** ist ein [Model Context Protocol](https://modelcontextprotocol.io)-Server, der Ihren IDE-Agenten mit Cloud Acceleration Manager verbindet. Wenn konfiguriert, kann die Migrationskompetenz BPA-Ergebnisse direkt aus Ihrem CAM-Projekt abrufen, ohne dass ein CSV-Download erforderlich ist.

### Was der MCP bietet {#mcp-tools}

| Tool | Beschreibung |
|------|-------------|
| `fetch-cam-bpa-findings-by-pattern` | Gibt BPA-Ergebnisse für ein bestimmtes Code-Migrationsmuster aus dem neuesten BPA-Bericht in einem CAM-Projekt zurück. |
| `fetch-cam-bpa-findings-by-importance` | Gibt alle BPA-Ergebnisse mit einem bestimmten Schweregrad (`CRITICAL`, `MAJOR`, `ADVISORY`, `INFO`) zurück, sortiert nach Anzahl. Nützlich für die Priorisierung, welche Muster zuerst bearbeitet werden sollen. |

Diese Tools werden automatisch von der Migrationsfertigkeit aufgerufen. Sie rufen sie nicht direkt auf.

### Erste Schritte {#getting-started-mcp}

1. Fügen Sie in der MCP-Konfiguration Ihrer IDE die MCP-Server-URL der Cloud-Migration hinzu: `https://mcp.adobeaemcloud.com/adobe/mcp/cloud-migration`
2. Melden Sie sich bei Aufforderung mit Ihrer Adobe ID an, um sich bei Cloud Acceleration Manager zu authentifizieren.
3. Die Migrationsfertigkeit kann jetzt BPA-Ergebnisse direkt aus Ihren CAM-Projekten abrufen.

Detaillierte Informationen zu Setup und Fehlerbehebung finden Sie unter [Verwenden des Cloud Migration MCP](/help/journey-migration/cloud-migration-skill/using-cloud-migration-mcp.md).

## So passen sie in die Migrations-Journey {#migration-journey}

Die Kenntnisse und das MCP ergänzen die anderen Tools in der **Implementierungsphase**:

- **Best Practices Analyzer**: Erzeugt die Ergebnisse, die zu den neuen Fähigkeiten beitragen. Siehe [Verwenden von Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md).
- **Cloud Acceleration Manager**: hostet BPA-Berichte und verfolgt den gesamten Migrationsfortschritt. Siehe [ Schritte mit CAM](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md).
- **Refaktorierungs-Tools**: Übernimmt die Modernisierung der Repository-Struktur und Dispatcher-Konfiguration. Siehe [Übersicht über die Umgestaltungs-Tools](/help/journey-migration/refactoring-tools/overview-refactoring-tools.md).
- **Content Transfer Tool**: Migriert Repository-Inhalte von AEM 6.x auf AEMaaCS.

Umfassende Informationen finden Sie [ „Übersicht ](/help/journey-migration/implementation.md) Implementierungsphase“.
