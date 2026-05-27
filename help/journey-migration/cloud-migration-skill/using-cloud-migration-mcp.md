---
title: Verwenden des AEM Cloud Migration MCP
description: Erfahren Sie, wie Sie den AEM Cloud Migration MCP-Server zu Ihrer KI-aktivierten IDE hinzufügen und ihn verwenden, um während einer Migrationssitzung Best Practices Analyzer-Ergebnisse aus Cloud Acceleration Manager abzurufen.
feature: Migration
role: Developer
source-git-commit: 5cda629090d9a9d020deca5192b8a89659ec4749
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 1%

---


# Verwenden des AEM Cloud Migration MCP {#using-cloud-migration-mcp}

Der **AEM Cloud Migration MCP** ist ein gehosteter [Model Context Protocol (MCP)](https://modelcontextprotocol.io)-Server, der Ihren IDE-Agenten mit **Cloud Acceleration Manager (CAM)**. Nach der Konfiguration kann der [AEM Cloud Migration Skill](/help/journey-migration/cloud-migration-skill/overview-cloud-migration-skill.md) Best Practices Analyzer-Ergebnisse direkt aus Ihrem CAM-Projekt abrufen, ohne dass ein CSV-Export erforderlich ist.

## MCP Server URL {#server-url}

```
https://mcp.adobeaemcloud.com/adobe/mcp/cloud-migration
```

Fügen Sie diese URL zur MCP-Konfiguration Ihrer IDE hinzu, um eine Verbindung herzustellen.

## Was sie bietet {#what-it-provides}

Der MCP-Server stellt zwei Tools bereit, die durch die Migrationsfertigkeit während einer Sitzung automatisch aufgerufen werden:

| Tool | Beschreibung |
|------|-------------|
| `fetch-cam-bpa-findings-by-pattern` | Gibt BPA-Ergebnisse für ein bestimmtes Migrationsmuster (`scheduler`, `assetApi`, `eventListener`, `resourceChangeListener`, `eventHandler` oder `all`) aus dem letzten BPA-Bericht in einem CAM-Projekt zurück. |
| `fetch-cam-bpa-findings-by-importance` | Gibt alle BPA-Ergebnisse mit einem bestimmten Schweregrad (`CRITICAL`, `MAJOR`, `ADVISORY`, `INFO`) aus dem letzten BPA-Bericht zurück, sortiert nach absteigender Anzahl. Nützlich für die Priorisierung, welche Muster zuerst behandelt werden sollen. |

## Voraussetzungen {#prerequisites}

* Ein **Cloud Acceleration Manager**-Projekt mit einem hochgeladenen BPA-Bericht. Siehe [CAM-Bereitschaftsphase](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md).
* Eine **Adobe ID** mit Zugriff auf dieses CAM-Projekt.
* Eine KI-fähige IDE, die Remote-MCP-Server unterstützt.

## Setup {#setup}

1. Fügen Sie in der MCP-Konfiguration Ihrer IDE einen neuen MCP-Server-Eintrag mit der URL `https://mcp.adobeaemcloud.com/adobe/mcp/cloud-migration` hinzu.
2. Speichern oder aktivieren Sie die Konfiguration, damit Ihre IDE eine Verbindung zum Server herstellt.
3. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrer **Adobe ID** an, um die Authentifizierung abzuschließen.
4. Nach der Authentifizierung erkennt Ihre IDE die verfügbaren Migrations-Tools und die Migrationsfertigkeit kann sie in Sitzungen verwenden.

Informationen zu IDE-spezifischen Konfigurationsschritten finden Sie in den Handbüchern unter [Einrichten von MCP mit AEM](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md).

>[!NOTE]
>Sie müssen sich mit dem Adobe ID anmelden, der Zugriff auf Ihre CAM-Projekte hat. Wenn ein Autorisierungsfehler angezeigt wird, stellen Sie sicher, dass Ihr Konto über die entsprechenden Berechtigungen in Cloud Acceleration Manager verfügt.

## Verwenden des MCP in einer Migrationssitzung {#using-in-session}

Wenn der MCP-Server angeschlossen ist, starten Sie eine Migrationssitzung in Ihrer IDE mit einer Eingabeaufforderung wie:

```
Fetch scheduler findings for project <name>/<id>.
```

Der Agent:

1. Ruft die BPA-Ergebnisse für dieses Projekt ab
2. Fahren Sie mit dem Workflow für die Batch-weise Migration fort

>[!IMPORTANT]
>Bestätigen Sie das Projekt immer aus der Liste, bevor der Agent fortfährt. Ergebnisse werden erst abgerufen, wenn Sie explizit ein Projekt ausgewählt haben.

### Priorisierung nach Schweregrad {#by-severity}

So zeigen Sie vor dem Start der Mustermigration eine nach Zählern sortierte Zusammenfassung Ihrer BPA-Berichtsergebnisse an:

```
Show me CRITICAL findings from CAM for project <name>/<id>.
```

Verwenden Sie dies, um zu entscheiden, welche Muster in Ihren Sitzungen priorisiert werden sollen.

## Fehlerbehebung {#troubleshooting}

**IDE kann keine Verbindung zum MCP-Server herstellen**

* Überprüfen Sie, ob die URL genau wie oben gezeigt eingegeben wurde, ohne Schrägstrich
* Starten Sie Ihre IDE neu, nachdem Sie die MCP-Konfiguration gespeichert haben

**Authentifizierung schlägt fehl**

* Stellen Sie sicher, dass Sie sich mit der Adobe ID anmelden, die Zugriff auf Ihre CAM-Projekte hat

**Kein BPA-Bericht gefunden**

* Überprüfen Sie, ob ein BPA-Bericht in das ausgewählte CAM-Projekt hochgeladen wurde. Siehe [Verwenden von Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md).

## So geht es weiter {#whats-next}

Wenn der MCP konfiguriert ist, finden [ unter „Verwenden der Cloud-](/help/journey-migration/cloud-migration-skill/using-cloud-migration-skill.md)&quot; eine vollständige Referenz zu Migrationsmustern und zur Sitzungsverwaltung.

