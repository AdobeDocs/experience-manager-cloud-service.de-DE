---
title: Verwenden von MCP mit AEM as a Cloud Service
description: Erfahren Sie, wie Sie das Model Context Protocol mit AEM as a Cloud Service verwenden.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: ddb7fc8c-affc-4374-8e08-d45d96017109
source-git-commit: b3704dad066b66b103fdec849879f889e895c09d
workflow-type: tm+mt
source-wordcount: '1761'
ht-degree: 1%

---

# Verwenden von MCP mit AEM as a Cloud Service {#using-mcp-with-aem-as-a-cloud-service}

## Einführung {#introduction}

Viele Adobe Experience Manager (AEM)-Teams arbeiten jetzt in integrierten Entwicklungsumgebungen (IDEs) und Chat-basierten Anwendungen wie Cursor, OpenAI ChatGPT, Anthropic Claude und Microsoft Copilot Studio. Diese Anwendungen unterstützen das Model Context Protocol (MCP), das es Anwendungen ermöglicht, Backend-Tools standardisiert für große Sprachmodelle (LLMs) verfügbar zu machen.

Mit der MCP-Integration von AEM können verschiedene Personas um denselben Inhalt herum zusammenarbeiten:

* **Entwickler** können Inhaltsvorgänge und Workflows über ihre IDE- oder Chat-Anwendung orchestrieren
* **Anwender** und Inhaltsarchitekten können Sites, Inhaltsfragmente und Assets mithilfe von KI verwalten und dabei das bestehende Berechtigungsmodell von AEM beibehalten.

>[!IMPORTANT]
>
> Bei Szenarien, in denen Inhalte geändert oder gelöscht werden, sollten Anwender die Benutzeroberfläche des KI-Assistenten verwenden, anstatt MCP-Tools direkt aufzurufen. Die von AI Assistant ausgeführten AEM-Agenten enthalten integrierte Sicherheitsfunktionen.
>

In diesem Artikel wird erläutert, was die MCP-Funktionen von AEM bieten, welche MCP-Anwendungen unterstützt werden, wie sie konfiguriert werden und wie sie in der Praxis verwendet werden.

## Warum MCP für AEM-Kunden nützlich ist {#why-mcp-is-useful-for-aem-customers}

Moderne IDE- und Chat-Anwendungen verwenden MCP als eine Möglichkeit für ein LLM, Tools aufzurufen, die hinter MCP-Servern bereitgestellt werden. Kunden können ihre Absichten in natürlicher Sprache beschreiben, anstatt Code anhand von API-Spezifikationen auf niedriger Ebene zu schreiben. Beispielsweise ermöglicht eine Eingabeaufforderung wie *„Aktualisieren des Hero-Banners für diese Kampagne auf allen Seiten“* dem LLM den Aufruf der entsprechenden MCP-Tools, die dann mit den APIs von AEM interagieren.

Die wichtigsten Vorteile sind:

* **Interaktion in natürlicher Sprache statt API-Programmierung**
MCP-Tools beschreiben, welche Vorgänge verfügbar sind und wie diese aufgerufen werden können. Das LLM verwendet diese Schemata, um zu entscheiden, welche Tools aufgerufen werden sollen und mit welchen Parametern.
* **Einheitliches Erlebnis über Anwendungen hinweg**
Dieselben AEM MCP-Tools können von mehreren MCP-kompatiblen Programmen aus verwendet werden, sodass Teams dort arbeiten können, wo sie am produktivsten sind, während sie dieselben zugrunde liegenden AEM-Funktionen aufrufen.
* **Sicherheit und Governance erhalten**
Anfragen an AEM MCP-Tools werden unter der Identität des authentifizierten Benutzers ausgeführt, und jedes Tool erzwingt die bestehenden AEM-Berechtigungen des Benutzers. KI-gestützte Vorgänge folgen denselben Zugriffsregeln wie manuelle Arbeit in AEM.

## Von AEM bereitgestellte MCP-Server {#mcp-servers-provided-by-aem}

AEM stellt MCP-Server als HTTP-Endpunkte bereit. Die unten aufgeführten Endpunkte beziehen sich auf:

`https://mcp.adobeaemcloud.com/adobe/mcp/`

### MCP-Server {#mcp-servers}

| **MCP-Server** | **Endpunkt** | **Beschreibung** |
|---|---|----------------------------------------------------------------------------------------------------------------------|
| **Inhalt** | `/content` | Alle Inhaltsvorgänge auf niedriger Ebene, einschließlich Erstellen, Lesen, Aktualisieren und Löschen (CRUD) für Seiten, Fragmente und Assets. |
| **Inhalt (schreibgeschützt)** | `/content-readonly` | Schreibgeschützte Inhaltsvorgänge (Abrufen, Auflisten/Suchen) für Seiten, Fragmente und Assets. |
| **Cloud Manager** | `/cloudmanager` | Verwalten Sie Cloud Manager-Entitäten, einschließlich Programmen, Umgebungen, Repositorys und Pipelines, die ebenfalls ausgelöst werden können. <br><br>*Dieser MCP-Server befindet sich jetzt in der **Betaversion**. Um den Zugriff anzufordern, senden Sie eine E-Mail an [&#128279;](mailto:aemcs-mcp-feedback@adobe.com)aemcs-mcp-feedback@adobe.com) mit einer Beschreibung Ihres Anwendungsfalls.* |

Die spezifischen Tools, die von den einzelnen MCP-Servern bereitgestellt werden, können sich im Laufe der Zeit weiterentwickeln. In der Praxis können Sie Ihre MCP-fähige Anwendung bitten, Tools über eine Eingabeaufforderung zu ermitteln, z. B.:

```
"List all AEM MCP tools available from this server and describe what they do."
```

Der MCP-Client verwendet das MCP-Protokoll, um die Toolliste und die Schemata abzurufen, die der LLM dann verwenden kann.

## Unterstützte MCP-Anwendungen {#supported-mcp-applications}

Die MCP-Server von AEM sind für die Verwendung mit einer Reihe von MCP-kompatiblen Anwendungen konzipiert. Jede Anwendung bietet ein eigenes Konfigurationserlebnis, aber die allgemeinen Schritte sind ähnlich.

### Chat-Anwendungen (Web und Desktop) {#chat-applications}

* Claude Anthropica
* OpenAI ChatGPT

### Entwickler-Tools (IDE-Erweiterungen, Desktop-Programme, CLIs) {#developer-tools}

* Anthropischer Claude-Code (CLI, JetBrains, VS-Code, Cursor)
* Erweiterungs-Code (CLI, JetBrains, VS-Code, Cursor)
* Erweitern der Einrückung für Desktop-Programm
* Cline (JetBrains, VS Code, Cursor)
* Mauszeiger
* GitHub-Copilot (VS-Code)
* Kiro (Desktop-Programm, CLI)
* OpenAI-Codex (Desktop-Programm)
* OpenAI Codex CLI
* Windsurfen

### Unternehmensplattformen {#enterprise-platforms}

* Microsoft Copilot Studio

## Setup-Übersicht {#setup-overview}

Die Konfiguration von MCP für AEM umfasst zwei Hauptbestandteile:

1. **Konfiguration in jeder MCP-Client-Anwendung** sodass die Anwendung weiß, wie eine Verbindung zu den AEM-MCP-Servern hergestellt und eine OAuth-Anmeldung durchgeführt werden soll
1. **Wählen Sie den MCP-Server aus** bevor Sie mit der Eingabeaufforderung beginnen, damit der MCP-Client ihn verwenden kann.

### AEM-Konfiguration {#aem-configuration}

Standardmäßig steuern die Berechtigungen, die einzelne Benutzende in AEM haben, den Zugriff auf AEM MCP-Server. Wenn sich ein Benutzer über eine MCP-Client-Anwendung authentifiziert, erzwingen die MCP-Tools dieselben Zugriffsregeln wie manuelle Vorgänge in AEM. Ein Benutzer kann nur Aktionen ausführen, zu deren Durchführung er bereits berechtigt ist.

#### Zulässige MCP-Client-Anwendungen {#permitted-mcp-client-applications}

Die folgenden MCP-Client-Anwendungen sind standardmäßig zulässig:

* Claude Anthropica
* Anthropischer Claude-Code
* Ergänzungscode
* Erweiterter Einzug
* Cline
* Mauszeiger
* GitHub-Copilot
* Kiro
* Microsoft Copilot Studio
* OpenAI ChatGPT
* OpenAI-Code
* OpenAI Codex CLI
* Windsurfen

#### Einschränken von MCP-Servern {#restricting-mcp-servers}

Auf die Zulassungsliste setzen Alle MCP-Server sind standardmäßig aktiviert. Als Administrator haben Sie die Möglichkeit, den Zugriff auf bestimmte MCP-Server auf Organisations-, Programm- oder Umgebungsebene einzuschränken. Durch diese Einschränkung erhalten Sie eine granulare Kontrolle darüber, welche MCP-Funktionen Benutzern in Ihrer Organisation zur Verfügung stehen.

#### Verwalten des MCP-Client-Zugriffs {#managing-mcp-client-access}

Administratoren können auch den Zugriff für bestimmte MCP-Client-Anwendungen deaktivieren, wenn die Richtlinien Ihrer Organisation dies erfordern. Wenn Sie möchten, dass Adobe die Unterstützung für weitere MCP-Client-Produkte aktiviert, senden Sie einen Link zur -Produkt-Website. Auf die Zulassungsliste setzen Wenn Sie einen benutzerdefinierten MCP-Client ändern müssen, wenden Sie sich auch an .

Für alle Anfragen zum MCP-Server wenden Sie sich bitte an uns unter **aemcs-mcp-feedback@adobe.com**

### Konfiguration der MCP Client-Anwendung {#mcp-client-application-configuration}

Jeder Benutzer führt diesen Schritt aus oder ein Administrator der MCP-Client-Anwendung kann ihn ausführen, wo er unterstützt wird. Konfigurationsdetails variieren geringfügig zwischen den Programmen. MCP-Clients entwickeln sich schnell weiter, und die Unterstützung für Remote-MCP-Server wird aktiv entwickelt. Möglicherweise müssen Sie den Entwicklermodus aktivieren, um auf die Funktionalität zum Hinzufügen von Remote-Servern zuzugreifen. Der allgemeine Prozess ist jedoch:

1. Eine oder mehrere AEM MCP-Server-URLs hinzufügen
   * Konfigurieren Sie einen oder mehrere MCP-Endpunkte aus der obigen Tabelle. Beispiel:`https://mcp.adobeaemcloud.com/adobe/mcp/content-readonly`
1. Trigger der Verbindung
   * Speichern oder aktivieren Sie die Konfiguration, damit die MCP-Client-Anwendung versucht, eine Verbindung zum AEM MCP-Server herzustellen
1. Mit Adobe ID anmelden
   * Wenn Sie dazu aufgefordert werden, schließen Sie den Anmeldevorgang für Adobe ab, damit die Anwendung OAuth-Token abrufen kann, die mit Ihrer Adobe ID verknüpft sind
1. Überprüfen der erkannten Tools
   * Nach der Authentifizierung erkennt die Anwendung die MCP-Tools vom Server. Anschließend können Sie den LLM auffordern, AEM-Vorgänge auszuführen.

Im Folgenden finden Sie die unterstützten Programme, von denen einige auf schrittweise Anleitungen verweisen:

#### Chat-Anwendungen (Web und Desktop) {#setup-chat-applications}

* [Claude Anthropica](/help/ai-in-aem/mcp-support/setup-claude.md)
* [OpenAI ChatGPT](/help/ai-in-aem/mcp-support/setup-chatgpt.md)

#### Entwickler-Tools (IDE-Erweiterungen, Desktop-Programme, CLIs) {#setup-developer-tools}

* Anthropischer Claude-Code (CLI, JetBrains, VS-Code, Cursor)
* Erweiterungs-Code (CLI, JetBrains, VS-Code, Cursor)
* Erweitern der Einrückung für Desktop-Programm
* Cline (JetBrains, VS Code, Cursor)
* [Mauszeiger](/help/ai-in-aem/mcp-support/setup-cursor.md)
* GitHub-Copilot (VS-Code)
* Kiro (Desktop-Programm, CLI)
* OpenAI-Codex (Desktop-Programm)
* OpenAI Codex CLI
* Windsurfen

#### Unternehmensplattformen {#setup-enterprise-platforms}

* [Microsoft Copilot Studio](/help/ai-in-aem/mcp-support/setup-microsoft-copilot-studio.md)

## Authentifizierung {#authentication}

Die von Adobe gehosteten MCP-Server implementieren OAuth und sind in das Identitätssystem von Adobe integriert.

* Wenn eine MCP-Client-Anwendung eine Verbindung zu einem AEM-MCP-Server herstellt, sehen die Benutzer ein Adobe-Anmeldedialogfeld und authentifizieren sich bei ihrer **Adobe ID**
* Nach erfolgreicher Anmeldung überprüft das System, ob die MCP-Client-Anwendung in Ihrer Organisation zulässig ist und ob der angeforderte MCP-Server zulässig ist. Wenn eine der Prüfungen fehlschlägt, wird eine Fehlermeldung angezeigt.

![Fehler „MCP-Client nicht erlaubt“](assets/MCP-Client-not-permitted.png)

* Nach der Überprüfung gibt der MCP-Server Token aus, die die Anwendung für nachfolgende Tool-Aufrufe verwendet
* MCP-Tools berücksichtigen die AEM-Berechtigungen des Benutzers. Nur Benutzer, die berechtigt sind, ein Inhaltsfragment in AEM zu ändern, können es über MCP ändern.

Dieser Ansatz stellt sicher, dass KI-unterstützte Vorgänge mit Ihrem bestehenden AEM-Sicherheits- und Governance-Modell übereinstimmen.

## Verwenden von MCP mit AEM {#using-mcp-with-aem}

Sobald AEM und Ihre MCP-Client-Anwendungen konfiguriert sind, können Sie in der gewünschten Anwendung arbeiten und den LLM auffordern, AEM-Vorgänge auszuführen. Das LLM liest die MCP-Tool-Schemata, wählt die aufzurufenden Tools aus und sequenziert sie nach Bedarf, um Ihre Anfrage zu erfüllen.

>[!IMPORTANT]
>
>Eingabeaufforderungen, die mehrere Schritte enthalten oder auf verschiedene Inhaltstypen wie Bilder und Text abzielen, funktionieren am besten mit einem denkenden Modell. Aktivieren Sie ein Denkmodell oder wählen Sie die Option Denken in Ihrem MCP-Client aus, anstatt sich auf den Auto-Modus zu verlassen.

### Anwendungsbeispiele {#example-usecases}

Zu den repräsentativen Szenarien gehören:

* **Umgebungserkennung**
   * Listen Sie Umgebungen und Lizenzen auf, um zu entscheiden, wo ein Workflow ausgeführt werden soll.

* **Sites-Management**
   * Auflisten von Sites
   * Erstellen, Lesen, Aktualisieren und Löschen von Seiten und Seiteninhalten.

* **Inhaltsfragmentverwaltung**
   * Nach Inhaltsfragmenten suchen
   * Erstellen neuer Fragmente
   * Vorhandene Fragmente aktualisieren, wenn sich Campaign-Messaging ändert

* **Assets-Verwaltung**
   * Assets importieren
   * Vorhandene Assets suchen
   * Veröffentlichen von Assets.

### Beispiel-Workflows {#example-workflows}

Die folgenden Beispiele veranschaulichen, wie ein LLM MCP-Tools miteinander verketten könnte.

1. **Arbeiten mit einem Inhaltsfragment, auf das von einer Seite verwiesen wird**
   * **Seiteninhalt abrufen** - Rufen Sie ein Tool wie `get-aem-page-content` auf, um die Seite abzurufen und die `fragmentPath`-Eigenschaft zu suchen.
   * **Auflösen des Fragmentpfads** - Verwenden Sie `resolve_fragment_path`, um den Pfad in eine UUID zu konvertieren.
   * **Fragmentdaten abrufen** - `get_fragment` zum Abrufen der aktuellen Felder aufrufen.
   * **Fragment aktualisieren** - `patch_fragment` aufrufen, um Änderungen auf den Fragmentinhalt anzuwenden.
1. **Erstellen neuer Inhalte basierend auf einem Modell**
   * **Entdecken Sie Modelle** - Verwenden Sie `list_models`, um zu sehen, welche Inhaltsfragmentmodelle verfügbar sind.
   * **Modell überprüfen** - Verwenden Sie `get_model`, um das Feldschema des Modells zu verstehen.
   * **Inhalt erstellen** - Verwenden Sie `create_fragment`, um ein neues Fragment mit Werten zu erstellen, die von Ihrer Eingabeaufforderung abgeleitet wurden.
1. **Sicheres Aktualisieren vorhandener Inhalte**
   * **Aktuelle Daten lesen** - Verwenden Sie `get_fragment`, um die vorhandenen Daten und ein E-Tag abzurufen.
   * **JSON-Patch anwenden** - Verwenden Sie `patch_fragment` mit dem E-Tag und einem JSON-Patch-Dokument, um das Fragment zu aktualisieren und so eine optimistische Parallelität zu unterstützen.

Aus Benutzersicht können diese Workflows mit Eingabeaufforderungen wie den folgenden gestartet werden:

```
"Create a new content fragment for the spring campaign based on our hero banner model and fill in its fields from this brief."
```

Das LLM wählt und koordiniert die notwendigen MCP-Tools automatisch.

## Erwartungsmanagement {#expectation-management}

Beachten Sie bei der Arbeit mit LLMs über MCP Folgendes:

* **Hochleistungsfähig, aber nicht unfehlbar**
LLMs können komplexe Aufgaben ausführen, sind aber anfällig für gelegentliche Fehler. Die gleiche Eingabeaufforderung kann ohne offensichtlichen Grund leicht unterschiedliche Ergebnisse oder Darstellungen liefern. Überprüfen Sie Ausgaben immer, bevor Sie Änderungen auf Produktionsinhalte anwenden.

* **Weiterentwicklung der Funktionen**
Die LLM-Modelle werden kontinuierlich verbessert. Im Laufe der Zeit werden sie klüger darin, neue Möglichkeiten zu entdecken, MCP-Tools zu kombinieren, um Ihre Ziele zu erreichen. Eine Aufgabe, für die heute mehrere Eingabeaufforderungen erforderlich sind, kann morgen nahtlos mit einer einzigen Eingabeaufforderung funktionieren.

* **Menschliche Aufsicht ist unerlässlich:**
Stellen Sie sich den LLM als einen kompetenten Assistenten vor, der Supervision braucht. Sie verfügt über breites Wissen und kann kreative Lösungen entwickeln, profitiert jedoch von Ihrer Beratung und Überprüfung. Überprüfen Sie die Ergebnisse, insbesondere bei kritischen Vorgängen, und geben Sie Feedback, wenn die Ausgabe nicht Ihren Erwartungen entspricht.

* **Seien Sie vorsichtig mit der automatischen Quittierung von Tool-Ausführungen**
Einige MCP-Client-Anwendungen, wie Claude, bieten die Möglichkeit, die vom LLM angeforderten Tool-Ausführungen automatisch zu bestätigen. Diese Option kann für schreibgeschützte Vorgänge wie das Suchen oder Abrufen von Inhalten praktisch sein. Gehen Sie jedoch mit Tools, die Inhalte aktualisieren oder löschen, vorsichtig vor. Überprüfen Sie jede Anfrage zur Ausführung des Tools, bevor Sie Aktionen bestätigen, die Ihre AEM-Umgebung ändern.

## Einschränkungen {#limitations}

AEM unterstützt derzeit die Konfiguration von MCP-Servern in den Anwendungen, die unter [Unterstützte MCP-Anwendungen](#supported-mcp-applications) aufgeführt sind.

Wenn Sie eine andere MCP-Client-Anwendung verwenden möchten, wenden Sie sich unter **aemcs-mcp-feedback@adobe.com** an uns, um Unterstützung für weitere Clients anzufordern oder einen benutzerdefinierten Client auf die Zulassungsliste setzen.
