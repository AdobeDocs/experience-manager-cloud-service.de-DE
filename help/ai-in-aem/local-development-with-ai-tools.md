---
title: Lokale Entwicklung mit KI-Tools
description: Erfahren Sie, wie Sie KI-Kodierungstools mit Projektkontext, Agentenkenntnissen und MCP-Servern konfigurieren, um die Entwicklung von AEM as a Cloud Service zu beschleunigen.
feature: Developing
role: Developer
exl-id: 09d6257d-36ad-49e5-831f-c44b356f1800
source-git-commit: 89b0405ff170b17d8d6e26d035ebeed3ab361f4c
workflow-type: tm+mt
source-wordcount: '2156'
ht-degree: 0%

---


# Lokale Entwicklung mit KI-Tools {#local-development-with-ai-tools}

>[!NOTE]
>
>Dieser Artikel konzentriert sich auf die lokale Entwicklung mit KI-Tools für die **AEM Java Stack-Entwicklung**. Informationen zu Edge Delivery Services finden Sie [Entwickeln mit KI-Tools](https://www.aem.live/developer/ai-coding-agents).

KI-Codierungs-Agenten (Claude Code, Cursor, GitHub, Copilot und ähnliche Tools) verfügen über umfassende Kenntnisse der zugrunde liegenden Technologien von AEM (Java, OSGi, Sling, JCR, HTL), kennen jedoch nicht unbedingt die Best Practices für die Code- und Konfigurationserstellung oder die Fehlerbehebung bei häufigen AEM-Entwicklungsproblemen.

Vier einander ergänzende Komponenten befassen sich damit:

| Komponente | Zweck |
|---|---|
| **AGENTS.md** | Eine projektspezifische Kontextdatei, die für jede Sitzung die KI in Ihrem AEM as a Cloud Service-Projekt bestimmt |
| **Agentenkenntnisse** | Wiederverwendbare Befehlssätze für wiederkehrende Entwicklungsaufgaben wie Komponentenerstellung und Dispatcher-Konfiguration |
| **AEM-Schnellstart für lokalen MCP-Server** | Zeigt Live-Laufzeitdaten aus einer lokalen AEM SDK-Instanz zur Fehlerbehebung an |
| **Lokaler Dispatcher-MCP-Server** | Ermöglicht die Laufzeitvalidierung und -überprüfung einer lokalen Dispatcher-Instanz |

In den [KI-unterstützten Entwicklungs](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/ai/ai-assisted-development/overview)Tutorials finden Sie zusätzliche praktische Anweisungen.

Senden Sie eine E-Mail an [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com) mit Feedback, um die Produktentwicklung mitzugestalten.


>[!TIP]
>
>Die Remote-MCP-Server von AEM Cloud Service sind auch für die lokale Entwicklung nützlich. Weitere Informationen dazu finden Sie im Artikel [Verwenden von MCP mit Cloud Service](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md)

## AGENTS.md {#agentsmd}

`AGENTS.md` ist eine Markdown-Datei im Stammverzeichnis Ihres AEM-Projekts. KI-Kodierungs-Tools laden diese Datei automatisch zu Beginn jeder Sitzung, um sich auf das erforderliche Java-Stack-Domain-Know-how von AEM Cloud Service (und nicht auf andere AEM-Lösungen wie AEM 6.5 oder Edge Delivery Services) zu stützen.

`AGENTS.md` ist keine statische Datei, die Sie kopieren. Es wird durch die `ensure-agents-md` Kenntnisse generiert, die im nächsten Abschnitt dieses Dokuments beschrieben werden. Die Kenntnis liest Ihre `pom.xml`, um den Projektnamen aufzulösen, Module zu entdecken und installierte Add-ons zu erkennen, wodurch eine auf Ihr spezifisches Projekt zugeschnittene Datei erstellt wird.

>[!NOTE]
>
>Sobald `AGENTS.md` im Projektstamm vorhanden ist, wird die `ensure-agents-md` nicht mehr ausgeführt. Bearbeiten Sie die Datei direkt, wenn sich die Projektstruktur ändert.

## Agent-Kenntnisse {#agent-skills}

Kenntnisse sind Befehlssätze, die mehrstufige Entwicklungs-Workflows kodieren. Wenn die KI aufgerufen wird, folgt sie dem Verfahren der Qualifikation, anstatt sich ausschließlich auf allgemeine Kenntnisse zu verlassen, was konsistente, konforme Ergebnisse liefert.

Adobe veröffentlicht AEM as a Cloud Service-Kenntnisse im **[Adobe/Skills](https://github.com/adobe/skills/tree/main/plugins/aem/cloud-service)**-Repository:

| SKILL | Zweck |
|---|---|
| `ensure-agents-md` | Bootstrapping `AGENTS.md` und `CLAUDE.md` auf die eigentliche Modulstruktur des Projekts zugeschnitten |
| `create-component` | Strukturvorlagen ermöglichen eine vollständige AEM-Komponente: Komponentendefinition, XML-Dialogfeld, HTL-Vorlage, Sling-Modell, Komponententests und Client-Bibliotheken |
| `dispatcher` | KI-gestützter Dispatcher- und Apache HTTPD-Konfigurationsassistent, der die Konfigurationserstellung, technische Beratung, die Reaktion auf Vorfälle, Leistungsoptimierung und die Sicherheitsabsicherung behandelt. |
| `migration` | Migriert AEM 6.x-, AMS- oder On-Premise-Java-Code- und OSGi-Konfigurationen nach AEM as a Cloud Service, gesteuert durch [Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md)-Ergebnisse aus einem CSV-Export oder [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) |
| `workflow` | Dies ist der zentrale Einstiegspunkt für alle AEM as a Cloud Service Workflow-Fähigkeiten. Es behandelt das Design von Workflow-Modellen, die Entwicklung benutzerdefinierter Prozessschritte und Teilnehmerauswahlen, die Starterkonfiguration, das Auslösen von Workflows und die Produktionsunterstützung, einschließlich des Debuggens blockierter/fehlgeschlagener Workflows, des Auslösens von Vorfällen mit Cloud Manager-Protokollen, der Thread-Pool-Analyse und der Sling-Auftragsdiagnose für die Granite Workflow-Engine. |
| `code-assessment` | **(Beta)** Erkennt und behebt Probleme mit Best Practices für AEM, der Code-Qualität und der Korrektheit in Ihrem lokalen Projekt, meldet Ergebnisse und führt chirurgische Korrekturen durch |

### Kenntnisse installieren {#install-skills}

Wählen Sie die Methode aus, die Ihrem KI-Kodierungstool entspricht. Durch das Installieren von Kenntnissen werden diese für alle Projekte auf diesem Computer verfügbar. Eine [&#x200B; Anleitung finden Sie &#x200B;](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/ai/ai-assisted-development/setup/agent-skills) Tutorial zum Einrichten von AEM Agent-.

#### Claude Code {#claude-code}

```bash
# Add the Adobe Skills marketplace (one-time setup)
/plugin marketplace add adobe/skills

# Install all available skills
/plugin install aem-cloud-service@adobe-skills
```

#### NPX-Kenntnisse {#npx-skills}

```bash
# Install all available skills
npx skills add https://github.com/adobe/skills/tree/main/skills/aem/cloud-service --all
```

#### Kenntnisse erweitern (GitHub-CLI-Erweiterung) {#upskill-github-cli-extension}

```bash
# Install the gh-upskill extension (one-time setup)
gh extension install ai-ecoverse/gh-upskill

# Install all available skills
gh upskill adobe/skills --path plugins/aem/cloud-service --all
```

### Use the Ensure-agents-md SKILL {#use-the-ensure-agents-md-skill}

Öffnen Sie nach der Installation der Kenntnisse Ihren KI-Assistenten in jedem AEM as a Cloud Service-Projekt, das noch keine `AGENTS.md` hat. Die Kenntnisse werden automatisch vor der Verarbeitung Ihrer ersten Anfrage ausgeführt, sodass beide Dateien im Projektstamm erstellt werden, ohne dass ein expliziter Aufruf erforderlich ist.

### Verwenden der Create-component SKILL {#use-the-create-component-skill}

Bei der ersten Verwendung erkennt die Kenntnis automatisch `project`, `package` und `group` aus `pom.xml` und vorhandenen Komponenten und fordert Sie auf, die erkannten Werte zu bestätigen. Anschließend wird `.aem-skills-config.yaml` im Projektstamm erstellt. Vor der ersten Verwendung ist keine manuelle Konfiguration erforderlich.

Wenn Sie die Datei lieber vorab erstellen möchten, platzieren Sie `.aem-skills-config.yaml` im Projektstamm mit der folgenden Struktur:

```yaml
configured: true

project: "wknd"                                    # Check /apps/{project}/ or pom.xml
package: "com.adobe.aem.guides.wknd.core"          # Check core/pom.xml
group: "WKND Components"                           # Check existing component .content.xml files
```

Die Datei befindet sich außerhalb des Kenntnisverzeichnisses und wird nie überschrieben, wenn die Kenntnis aktualisiert wird.

Beschreiben Sie die Komponente in Ihrem KI-Chat:

```
Create an AEM component called "Hero Banner"

Dialog specification:
Title (title) - Textfield, mandatory
Subtitle (subtitle) - Textfield
Background Image (backgroundImage) - Fileupload
CTA Text (ctaText) - Textfield
CTA Link (ctaLink) - Pathfield
```

Der Agent wiederholt die Feldspezifikation zur Bestätigung und generiert dann alle Komponentendateien. Zu den unterstützten Mustern gehören Mehrfachfeld- mit zusammengesetzten verschachtelten Elementen, bedingte Einblenden-/Ausblenden-Logik, Kernkomponenten-Erweiterung über Sling Resource Merger und JUnit 5-Tests mit AEM Mocks. Das Design kann aus verschiedenen Quellen stammen, darunter eine Textbeschreibung, ein Bild oder eine Figma Design URL unter Verwendung des MCP-Servers von Figma.

Weitere Informationen erhalten Sie im Tutorial [Komponentenentwicklung mit AEM Agent-Kenntnissen“](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/ai/ai-assisted-development/use-cases/component-development)

### Verwenden der Migrationsfertigkeit {#use-the-migration-skill}

Die `migration` Kenntnisse leiten den Agenten durch die Migration von AEM Java-Code und OSGi-Konfigurationen zu AEM as a Cloud Service. Es funktioniert ein Muster nach dem anderen: Sie benennen das Muster (z. B. `scheduler` oder `replication`), lassen den Agenten auf Ihre Best Practices Analyzer-Ergebnisse verweisen, suchen die betroffenen Dateien in Ihrem Projekt und wenden die richtigen Transformationen in Batches an, wobei Sie nach jeder Überprüfung anhalten.

Zu den unterstützten Mustern gehören Sling Scheduler, ResourceChangeListener, Replication API, OSGi EventListener und EventHandler, Assets API, HTL-Link-Fehlerbehebungen und OSGi-Konfigurationskonvertierung mit Cloud Manager Secrets und Extraktion von Umgebungsvariablen.

Die Kenntnisse sind mit dem [Cloud Migration MCP](/help/journey-migration/cloud-migration-skill/using-cloud-migration-mcp.md) verknüpft, um Ergebnisse direkt aus [Cloud Acceleration Manager abzurufen](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md). Ohne konfiguriertes MCP wird die Qualifikation auf einen lokalen [BPA](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) CSV-Export zurückgesetzt oder Sie können sie auf bestimmte Dateien manuell verweisen.

Vollständige Setupanweisungen und Musterverweise finden Sie unter [KI-unterstützte Code-Migration zu AEM as a Cloud Service](/help/journey-migration/cloud-migration-skill/overview-cloud-migration-skill.md).

### Dispatcher-Kenntnisse verwenden {#use-the-dispatcher-skill}

Rufen Sie die Dispatcher-Kenntnisse für alle Dispatcher- oder Apache HTTPD-Konfigurationsaufgaben auf. Die Qualifikation leitet Anfragen je nach Art der Anfrage an eine von sechs spezialisierten Unterqualifikationen weiter:

| Sub-SKILL | Zweck |
|---|---|
| `workflow-orchestrator` | End-to-End-Arbeit, die Design, Konfigurationsänderungen, Validierung und Follow-up umfasst |
| `config-authoring` | Konkrete Konfigurationsänderungen: Filter, Cache-Regeln, Umschreibungen, vhosts, Header und Farms |
| `technical-advisory` | Konzeptorientierung, politische Erläuterung und zitierungsgestützte Empfehlungen |
| `incident-response` | Laufzeitfehler, Cache-Anomalien und Regressionen |
| `performance-tuning` | Cache-Effizienz, Latenz und Durchsatzoptimierung |
| `security-hardening` | Überprüfung der Exposition und Härtung der Produktion |

Bei allgemeinen oder erstmaligen Anfragen beginnen Sie mit der `workflow-orchestrator` Unterqualifikation. Beschreiben Sie für zielgerichtete Arbeiten das spezifische Anliegen und die Qualifikationswege zum entsprechenden Spezialisten.

Die Dispatcher-Kenntnisse umfassen die Orchestrierung und Beratung. Der Dispatcher MCP-Server, der im folgenden Abschnitt beschrieben wird, stellt die sieben Validierungs- und Laufzeittools bereit, die die Qualifikation verwendet, wenn sie lokale Beweise benötigt.

### Kenntnisse zur Code-Bewertung verwenden (Beta) {#use-the-code-assessment-skill}

>Diese Funktion ist **Beta**. Adobe empfiehlt Ihnen, Feedback zu geben, indem Sie [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com) per E-Mail versenden, um die Produktentwicklung zu gestalten.
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

Die `code-assessment` kann Probleme mit der Code-Qualität und -Korrektheit in einem AEM as a Cloud Service-Projekt vollständig innerhalb Ihres lokalen Arbeitsbereichs erkennen, überprüfen und beheben. Beschreiben Sie das Problem, und die Qualifikation leitet die Anfrage an den entsprechenden Workflow zur Behebung weiter.

Zu den unterstützten Prüfungen gehören die Modernisierung der Sling-Modell-Abhängigkeitseinschleusung, die Aktualisierung veralteter Maven-Abhängigkeiten, das Hinzufügen fehlender Timeouts zu ausgehenden HTTP-Aufrufen, das Binden ungebundener Abfragen, Sling-Scheduler, Ressourcenänderungs-Listener, die Replikations- und Assets-APIs sowie JCR- oder OSGi-Ereignisverarbeitung sowie das Scannen und Beheben der Verwendung von [veralteten und entfernten AEM-APIs](/help/release-notes/deprecated-removed-features.md) mit mehr Hinzugefügten im Laufe der Zeit. Je nach Problem wendet die Kenntnis entweder direkt eine mechanische Korrektur an oder führt Sie durch eine, die einen Beurteilungsaufruf erfordert.

Für eine umfassende oder Erstüberprüfung bitten Sie die SKILL, das gesamte Projekt zu bewerten: Es wird jeder Detektor ausgeführt, alle Ergebnisse werden gemeldet und der Code behebt ein Muster nach dem anderen.

Öffnen Sie zunächst einen neuen Agent-Chat in Ihrem AEM as a Cloud Service-Projekt.

**1. Überprüfen Sie Ihr Projekt.** Einen Bericht anfordern. Die SKILL führt ihren Analyzer aus und gibt die Ergebnisse inline zurück, gruppiert nach Muster und Schweregrad, mit einem vorgeschlagenen Plan zur Mängelbehebung. Zu diesem Zeitpunkt wird kein Code geändert.

```
scan my AEM project and report any code-quality issues
```

Für einen expliziteren Aufruf benennen Sie die Qualifikation direkt:

```
/code-assessment review my code for AEM as a Cloud Service issues
```

Um den Fokus auf ein einzelnes Muster zu legen, benennen Sie es in der Eingabeaufforderung:

```
scan my project for unbounded queries
```

**2. Fehlerbehebungen einzeln anwenden.** Bitten Sie die Kenntnis, ein bestimmtes Muster zu korrigieren. Es nimmt chirurgische Bearbeitungen vor und überprüft, ob sie kompiliert wurden. Mechanische Korrekturen gelten direkt; geführte Korrekturen führen Sie durch jede Entscheidung.

```
apply unbounded-query
```

Es übergibt niemals einen Commit oder einen Push - man überprüft den Diff und übernimmt. Große Fehlerbehebungen werden in wiederverwendbaren Batches ausgeführt. Antworten Sie `apply <pattern>`, um fortzufahren.

## AEM QuickStart MCP-Server {#aem-quickstart-mcp-server}

Das Model Context Protocol (MCP) ist ein offener Standard, der es KI-Kodierungstools ermöglicht, eine Verbindung zu externen Datenquellen und Services herzustellen. Der AEM QuickStart MCP-Server ist ein Inhaltspaket, das Laufzeitdaten direkt über verbundene KI-Tools verfügbar macht, sobald es in einer lokalen AEM SDK-Instanz installiert ist. Dadurch können Agenten Protokolle abrufen, OSGi-Fehler diagnostizieren und die Anforderungsverarbeitung überprüfen, ohne die IDE verlassen zu müssen.

### Installieren des Inhaltspakets {#install-the-content-package}

Laden Sie das Inhaltspaket vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=mcp*&1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&1_group.propertyvalues.operation=equals&1_group.propertyvalues.0_values=software-type%3Atooling&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=3) herunter und installieren Sie `com.adobe.aem:com.adobe.aem.mcp-server-contribs-content` mithilfe von Package Manager unter `/crx/packmgr` in Ihren lokalen Schnellstart.

**Kompatibilität:** mit AEM SDK `2026.2.24678.20260226T154829Z-260200` und höher validiert.

### Verfügbare Tools {#available-tools}

| Tool | Beschreibung |
|---|---|
| `aem-logs` | Ruft AEM- und OSGi-Protokolleinträge ab, filterbar nach Regex-Muster, Protokollebene und Eintragsanzahl |
| `diagnose-osgi-bundle` | Diagnostiziert, warum eine Bundle- oder DS-Komponente nicht gestartet wird, meldet fehlende Pakete, nicht erfüllte Verweise und Konfigurationsprobleme |
| `recent-requests` | Gibt aktuelle HTTP-Anfragen mit der vollständigen internen Verarbeitungsablaufverfolgung von Sling zurück (Ressourcenauflösung, Skriptauflösung, Filterkette), filterbar nach Pfadregex |

### Konfigurieren der IDE {#configure-your-ide}

#### Mauszeiger {#cursor}

Fügen Sie in den Cursoreinstellungen einen neuen benutzerdefinierten MCP-Server hinzu:

```json
"aem-cs-sdk": {
  "type": "streamable-http",
  "url": "http://localhost:4502/bin/mcp",
  "headers": {
    "Authorization": "Basic YWRtaW46YWRtaW4="
  }
}
```

#### GitHub Copilot mit IntelliJ IDEA {#github-copilot-with-ihtellij-idea}

Navigieren Sie zu **Tools > GitHub-Kopilot > Model Context Protocol (MCP)** und klicken Sie auf **Konfigurieren**. Hinzufügen:

```json
"aem-cs-sdk": {
  "url": "http://localhost:4502/bin/mcp",
  "requestInit": {
    "headers": {
      "Authorization": "Basic YWRtaW46YWRtaW4="
    }
  }
}
```

#### Andere IDEs {#other-ides}

Jeder MCP-Client kann eine Verbindung herstellen, indem er mit einem `Authorization: Basic YWRtaW46YWRtaW4=` auf `http://localhost:4502/bin/mcp` verweist. Konfigurieren Sie benutzerdefinierte Header mithilfe der MCP-Einstellungen Ihrer IDE.

>[!NOTE]
>
>Der Wert `Basic YWRtaW46YWRtaW4=` ist die Base64-Codierung von `admin:admin`, der Standardberechtigung für einen lokalen Schnellstart. Verwenden Sie dies nicht in nicht-lokalen Umgebungen.

## Dispatcher MCP-Server {#dispatcher-mcp-server}

Der Dispatcher MCP-Server ist im Paket mit dem AEM Dispatcher SDK enthalten. Dadurch können KI-Tools die Dispatcher- und Apache-HTTPD-Konfiguration überprüfen, die Verarbeitung von Trace-Anfragen verfolgen und das Cacheverhalten mit einer Dispatcher-Instanz überprüfen, die lokal in Docker ausgeführt wird.

Anders als die Dispatcher-Kenntnisse stellt der Dispatcher MCP-Server nur Tools bereit: sieben MCP-Tools und keine Eingabeaufforderungen oder Ressourcen.

>[!VIDEO](https://video.tv.adobe.com/v/3491968?captions=ger&quality=12&learn=on)

### Voraussetzungen {#prerequisites}

- Docker Desktop 4.x oder höher, installiert und ausgeführt
- AEM Dispatcher SDK vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=mcp*&1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&1_group.propertyvalues.operation=equals&1_group.propertyvalues.0_values=software-type%3Atooling&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=3)

>[!NOTE]
>
>Wenn Sie `client version 1.43 is too new` sehen, legen Sie `DOCKER_API_VERSION=1.41` in Ihrer Shell oder in `mcp.json` fest.

### Installieren von Dispatcher SDK {#install-the-dispatcher-sdk}

**macOS und Linux:**

```bash
chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
./aem-sdk-dispatcher-tools-<version>-unix.sh
cd dispatcher-sdk-<version>
chmod +x ./bin/docker_run_mcp.sh
./bin/docker_run_mcp.sh test
```

**Windows:**

```powershell
Expand-Archive aem-sdk-dispatcher-tools-<version>-windows.zip
```

Führen Sie `./bin/docker_run_mcp.sh help` aus, um die IDE-Konfiguration zum Kopieren und Einfügen abzurufen und die gebündelte MCP- und SDK-Version zu `./bin/docker_run_mcp.sh version`. Verwenden Sie `./bin/docker_run_mcp.sh diagnose`, um Konnektivitätsprobleme zu untersuchen.

### Cursor konfigurieren {#configure-cursor}

Fügen Sie einen `aem-dispatcher-mcp` Eintrag zu `~/.cursor/mcp.json` hinzu:

```json
{
  "mcpServers": {
    "aem-dispatcher-mcp": {
      "command": "<path_to_dispatcher_sdk>/bin/docker_run_mcp.sh",
      "env": {
        "DOCKER_API_VERSION": "1.43",
        "AEM_DEPLOYMENT_MODE": "cloud",
        "MCP_LOG_LEVEL": "trace",
        "MCP_LOG_FILE": "/tmp/dispatcher-mcp.log",
        "DISPATCHER_CONFIG_PATH": "<path_to_dispatcher_src>"
      }
    }
  }
}
```

Ersetzen Sie `<path_to_dispatcher_sdk>` durch den extrahierten Speicherort für Dispatcher SDK und `<path_to_dispatcher_src>` Sie mit dem Dispatcher-`src` des Projekts. Legen Sie `DISPATCHER_CONFIG_PATH` auf den Konfigurationsstamm fest, der die Dateien enthält, in denen `/docroot` definiert ist. `MCP_LOG_LEVEL` und `MCP_LOG_FILE` sind optionale Debugging-Einstellungen. Wenn Sie `client version 1.43 is too new` sehen, setzen Sie `DOCKER_API_VERSION` auf `1.41`. Wenn bereits andere MCP-Server konfiguriert sind, fügen Sie den `aem-dispatcher-mcp` hinzu, ohne sie zu ersetzen. Cursor nach dem Speichern neu starten.

Andere IDEs können auf ähnliche Weise konfiguriert werden. Die `docs/DispatcherMCP.md` von SDK enthält vollständige Beispiele für Claude Desktop und VS Code.

### Verfügbare Tools {#available-tools-dispatcher}

| Tool | Beschreibung |
|---|---|
| `validate` | Validiert Dispatcher- und Apache-HTTPD-Konfigurationen |
| `lint` | Führt modusabhängige statische Prüfungen und Best-Practice-Analysen durch |
| `sdk` | Führt Dispatcher SDK-Workflows aus: `validate`, `validate-full`, `three-phase-validate`, `docker-test`, `check-files`, `diff-baseline` |
| `trace_request` | Verfolgt das Anforderungsverhalten mit Laufzeitbeweisen |
| `inspect_cache` | Überprüft das Cache- und Stammverhalten für eine Ziel-URL |
| `monitor_metrics` | Liest Laufzeitmetriken aus Dispatcher- und HTTPD-Protokollen |
| `tail_logs` | Verweist relevante Dispatcher- und HTTPD-Laufzeitprotokolle |

Die MCP-Oberfläche legt absichtlich nur diese sieben Tools offen. Eingabeaufforderungen und Ressourcen verbleiben in der Kompetenzschicht. Die vollständige Referenzdokumentation finden Sie in der `docs/DispatcherMCP.md` im extrahierten Dispatcher SDK.
