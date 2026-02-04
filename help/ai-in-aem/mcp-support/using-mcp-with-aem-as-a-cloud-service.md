---
title: Verwenden von MCP mit AEM as a Cloud Service
description: Erfahren Sie, wie Sie das Model Context Protocol mit AEM as a Cloud Service verwenden.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 243fbd007235949fc03852658f606d483ef9ce4d
workflow-type: tm+mt
source-wordcount: '2064'
ht-degree: 0%

---


# Verwenden von MCP mit AEM as a Cloud Service {#using-mcp-with-aem-as-a-cloud-service}

## Einführung {#introduction}

Viele Adobe Experience Manager (AEM)-Teams arbeiten jetzt in integrierten Entwicklungsumgebungen (IDEs) und Chat-basierten Anwendungen wie Cursor, ChatGPT, Anthropic Claude und Microsoft Copilot Studio. Diese Anwendungen unterstützen das Model Context Protocol (MCP), das es Anwendungen ermöglicht, Backend-Tools standardisiert für große Sprachmodelle (LLMs) verfügbar zu machen.

Mit der MCP-Integration von AEM können verschiedene Personas um denselben Inhalt herum zusammenarbeiten:

* **Entwickler** können Inhaltsvorgänge und Workflows über ihre IDE- oder Chat-Anwendung orchestrieren
* **Anwender** und Inhaltsarchitekten können Sites, Inhaltsfragmente und Assets mithilfe von KI verwalten und dabei das bestehende Berechtigungsmodell von AEM beibehalten.

>[!IMPORTANT]
>
> Bei Szenarien, in denen Inhalte geändert oder gelöscht werden, sollten Anwender die Benutzeroberfläche des KI-Assistenten verwenden, anstatt MCP-Tools direkt aufzurufen, da die vom KI-Assistenten ausgeführten AEM-Agenten integrierte Sicherheitsmaßnahmen enthalten.
>

In diesem Artikel wird erläutert, was die MCP-Funktionen von AEM bieten, welche MCP-Anwendungen unterstützt werden, wie sie konfiguriert werden und wie sie in der Praxis verwendet werden.

## Warum MCP für AEM-Kunden nützlich ist {#why-mcp-is-useful-for-aem-customers}

Moderne IDE- und Chat-Anwendungen verwenden MCP als eine Möglichkeit für ein LLM, Tools aufzurufen, die hinter MCP-Servern bereitgestellt werden. Anstatt Code anhand von API-Spezifikationen auf niedriger Ebene zu schreiben, können Kunden ihre Absicht in natürlicher Sprache beschreiben (*„Aktualisieren Sie das Hero-Banner für diese Kampagne auf allen Seiten“*) und das LLM die entsprechenden MCP-Tools aufrufen lassen, die wiederum mit den APIs von AEM interagieren.

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

Die spezifischen Tools, die von den einzelnen MCP-Servern bereitgestellt werden, können sich im Laufe der Zeit weiterentwickeln. In der Praxis können Sie Ihre MCP-fähige Anwendung bitten, Tools über eine Eingabeaufforderung zu ermitteln, z. B.:

*„Listen Sie alle auf diesem Server verfügbaren AEM-MCP-Tools auf und beschreiben Sie deren Funktionsweise.*

Der MCP-Client verwendet das MCP-Protokoll, um die Toolliste und die Schemata abzurufen, die der LLM dann verwenden kann.

## Unterstützte MCP-Anwendungen {#supported-mcp-applications}

Die MCP-Server von AEM sind für die Verwendung mit einer Reihe von MCP-kompatiblen Anwendungen konzipiert. Die folgenden Anwendungen werden unterstützt:

* Claude Anthropica
* Mauszeiger
* OpenAI ChatGPT
* Microsoft Copilot Studio

Jede Anwendung bietet ein eigenes Konfigurationserlebnis, aber die allgemeinen Schritte sind ähnlich.

## Setup-Übersicht {#setup-overview}

Die Konfiguration von MCP für AEM umfasst zwei Hauptbestandteile:

1. **Konfiguration in jeder MCP-Client-Anwendung** sodass die Anwendung weiß, wie eine Verbindung zu den AEM-MCP-Servern hergestellt und eine OAuth-Anmeldung durchgeführt werden soll
1. **Wählen Sie den MCP-Server aus** bevor Sie mit der Eingabeaufforderung beginnen, damit der MCP-Client ihn verwenden kann.

### AEM-Konfiguration {#aem-configuration}

Standardmäßig wird der Zugriff auf AEM MCP-Server durch die Berechtigungen gesteuert, die einzelne Benutzende in AEM haben. Wenn sich ein Benutzer über eine MCP-Client-Anwendung authentifiziert, erzwingen die MCP-Tools dieselben Zugriffsregeln wie manuelle Vorgänge in AEM. Ein Benutzer kann nur Aktionen ausführen, zu deren Durchführung er bereits berechtigt ist.

#### Zulässige MCP-Client-Anwendungen {#permitted-mcp-client-applications}

Die folgenden MCP-Client-Anwendungen sind standardmäßig zulässig:

* ChatGPT
* Claude
* MS Copilot Studio
* Mauszeiger

#### Einschränken von MCP-Servern {#restricting-mcp-servers}

Auf die Zulassungsliste setzen Alle MCP-Server sind standardmäßig aktiviert. Als Administrator haben Sie die Möglichkeit, den Zugriff auf bestimmte MCP-Server auf Organisations-, Programm- oder Umgebungsebene einzuschränken. Dadurch erhalten Sie eine granulare Kontrolle darüber, welche MCP-Funktionen Benutzern in Ihrer Organisation zur Verfügung stehen.

#### Verwalten des MCP-Client-Zugriffs {#managing-mcp-client-access}

Administratoren können auch den Zugriff für bestimmte MCP-Client-Anwendungen deaktivieren, wenn die Richtlinien Ihrer Organisation dies erfordern. Wenn Sie möchten, dass Adobe die Unterstützung für weitere MCP-Client-Produkte aktiviert, senden Sie einen Link zur -Produkt-Website. Auf die Zulassungsliste setzen Wenn Sie einen benutzerdefinierten MCP-Client ändern müssen, wenden Sie sich auch an .

Für alle Anfragen zum MCP-Server wenden Sie sich bitte an uns unter **aemcs-mcp-feedback@adobe.com**

### Konfiguration der MCP Client-Anwendung {#mcp-client-application-configuration}

Dieser Schritt wird von jedem Benutzer (oder, sofern unterstützt, von einem Administrator der MCP-Client-Anwendung) ausgeführt. Konfigurationsdetails variieren geringfügig zwischen den Programmen. MCP-Clients entwickeln sich schnell weiter, und die Unterstützung für Remote-MCP-Server wird aktiv entwickelt. Möglicherweise müssen Sie den Entwicklermodus aktivieren, um auf die Funktionalität zum Hinzufügen von Remote-Servern zuzugreifen. Der allgemeine Prozess ist jedoch:

1. AEM MCP-Server-URL(s) hinzufügen
   * Konfigurieren Sie den/die MCP-Endpunkt(e) aus der obigen Tabelle. Beispiel:`https://mcp.adobeaemcloud.com/adobe/mcp/content-readonly`
1. Trigger der Verbindung
   * Speichern oder aktivieren Sie die Konfiguration, damit die MCP-Client-Anwendung versucht, eine Verbindung zum AEM MCP-Server herzustellen
1. Mit Adobe ID anmelden
   * Wenn Sie dazu aufgefordert werden, schließen Sie den Anmeldevorgang für Adobe ab, damit die Anwendung OAuth-Token abrufen kann, die mit Ihrer Adobe ID verknüpft sind
1. Überprüfen der erkannten Tools
   * Nach der Authentifizierung erkennt die Anwendung die MCP-Tools vom Server. Anschließend können Sie den LLM auffordern, AEM-Vorgänge auszuführen.

Im Folgenden finden Sie Beispiele dafür, wie dies in jeder unterstützten Anwendung auf einer allgemeinen Ebene aussieht.

**ChatGPT**

![Konfigurieren von ChatGPT - Einstellungen](assets/chatgpt-1.png)

![Konfigurieren von ChatGPT - Apps und Connectoren - Erweiterte Einstellungen](assets/chatgpt-2.png)

![Konfigurieren von ChatGPT - Apps und Connectoren - Entwicklermodus](assets/chatgpt-3.png)

![Konfigurieren von ChatGPT - Apps und Connectoren - Erstellen einer App](assets/chatgpt-4.png)

![Konfigurieren von ChatGPT - Apps und Connectoren - Neue App](assets/chatgpt-5.png)

![Konfigurieren von ChatGPT - Apps und Connectoren - AEM Content MCP Service](assets/chatgpt-6.png)

![Konfigurieren von ChatGPT - Fragen Sie den AEM Content MCP Service](assets/chatgpt-7.png)

* Fügen Sie die AEM MCP-Server-URL(s) in dem Bereich hinzu, in dem MCP-Verbindungen oder -Tools konfiguriert sind
* Erstellen Sie einen Trigger für die Verbindung und melden Sie sich bei der Weiterleitung mit Ihrer Adobe ID an
* Verweisen Sie in einem Chat auf die konfigurierten AEM-Tools in Ihren Eingabeaufforderungen, zum Beispiel:

  *„Listen Sie mithilfe der konfigurierten AEM-MCP-Tools alle Websites in Ihrer Autorenumgebung auf.“*

**Claude**

![Claude konfigurieren - Einstellungen](assets/claude-1.png)

![Claude konfigurieren - Connectoren](assets/claude-2.png)

![Claude konfigurieren - Connectoren - Benutzerdefinierten Connector hinzufügen](assets/claude-3.png)

![Claude konfigurieren - Connectoren - Benutzerdefinierten Connector verbinden](assets/claude-4.png)

![Claude konfigurieren - Connectoren - Benutzerdefinierten Connector konfigurieren](assets/claude-5.png)

![Claude konfigurieren - Connectoren - Benutzerdefinierte Connector-Tool-Berechtigungen](assets/claude-6.png)

![Claude konfigurieren - AEM Content MCP Service fragen](assets/claude-7.png)

* Registrieren Sie in Claudes MCP-Konfiguration die AEM MCP-Server-URL(s)
* Adobe-Anmeldeablauf abschließen
* Aktivieren Sie optional die automatische Bestätigung für bestimmte Tools im Konfigurationsbereich. Dies wird für Suchvorgänge oder schreibgeschützte Vorgänge empfohlen.
* Stellen Sie sicher, dass der MCP-Server ausgewählt ist, bevor Sie mit der Konversation beginnen
* Bitten Sie Claude, AEM-bezogene Aufgaben auszuführen. Claude wählt die vom MCP-Server bereitgestellten AEM-Tools nach Ihrer Aufforderung aus.

**Cursor**

![Konfigurieren des Cursors - Einstellungen](assets/cursor-1.png)

![Konfigurieren des Cursors - Tools und MCP - Hinzufügen benutzerdefinierter MCP](assets/cursor-2.png)

![Konfigurieren des Cursors - Hinzufügen benutzerdefinierter MCP-Einstellungen](assets/cursor-3.png)

![Konfigurieren des Cursors - Verbinden](assets/cursor-4.png)

![Konfigurieren des Cursors - Neuen Service fragen](assets/cursor-5.png)

* Erstellen Sie in den MCP-Einstellungen des Cursors einen neuen MCP-Server-Eintrag mit den AEM MCP-URLs
* Bei Aufforderung mit Ihrer Adobe ID authentifizieren
* Optional können Sie einzelne Werkzeuge aktivieren oder deaktivieren, indem Sie auf die Werkzeugnamen klicken. Alle Tools sind standardmäßig aktiviert.
* Verwenden Sie den Editor oder Chat des Cursors, um AEM-Tools als Teil von Entwicklungs- oder Inhalts-Workflows aufzurufen.

**Microsoft Copilot Studio**

![Konfigurieren von CoPilot - Agenten](assets/copilot-1.png)

![Konfigurieren von Copilot - Tool hinzufügen](assets/copilot-2.png)

![Konfigurieren des Kopiloten - Tool hinzufügen - Modellkontextprotokoll](assets/copilot-3.png)

![Konfigurieren des Kopiloten - Hinzufügen eines Modell-Kontext-Protokoll-Servers (Vorschau)](assets/copilot-4.png)

![Konfigurieren von Copilot - Tool hinzufügen - Neue Verbindung erstellen](assets/copilot-5.png)

![Konfigurieren von Copilot - Tool hinzufügen - Hinzufügen und Konfigurieren](assets/copilot-6.png)

![Konfigurieren des Kopiloten - Tool hinzufügen - Konfigurieren](assets/copilot-7.png)

![Konfigurieren von Copilot - Verbindung testen](assets/copilot-8.png)

![Konfigurieren von CoPilot - Verbindungen verwalten](assets/copilot-9.png)

![Konfigurieren von CoPilot - Test Agent](assets/copilot-10.png)

* Erstellen eines neuen Agenten
* Navigieren Sie zum Abschnitt „Tool“ und klicken Sie auf **Tool hinzufügen**
* Vorhandenes Tool auswählen oder ein neues erstellen
* Konfigurieren eines neuen MCP-Tools, das auf die AEM MCP-Server-URL(s) verweist
* Erstellen einer Verbindung, die zwischen Agenten geteilt oder dediziert werden kann
* Mit Adobe ID bei Weiterleitung anmelden
* Optional können Sie den automatischen Bestätigungsmodus aktivieren oder eine Bestätigung durch den Endbenutzer für alle Tool-Interaktionen verlangen
* Öffnen Sie beim Testen Ihres Agenten zunächst den Verbindungs-Manager, um Ihrer Sitzung eine Verbindung zuzuweisen, und drücken Sie dann **Wiederholen**.

## Authentifizierung {#authentication}

Die von Adobe gehosteten MCP-Server implementieren OAuth und sind in das Identitätssystem von Adobe integriert.

* Wenn eine MCP-Client-Anwendung eine Verbindung zu einem AEM-MCP-Server herstellt, sehen die Benutzer ein Adobe-Anmeldedialogfeld und authentifizieren sich bei ihrer **Adobe ID**
* Nach erfolgreicher Anmeldung überprüft das System, ob die MCP-Client-Anwendung in Ihrer Organisation zulässig ist und ob der angeforderte MCP-Server zulässig ist. Wenn eine der Prüfungen fehlschlägt, wird eine Fehlermeldung angezeigt.

![Fehler „MCP-Client nicht erlaubt“](assets/MCP-Client-not-permitted.png)

* Nach der Überprüfung gibt der MCP-Server Token aus, die die Anwendung für nachfolgende Tool-Aufrufe verwendet
* MCP-Tools berücksichtigen die AEM-Berechtigungen des Benutzers. Benutzende ohne Berechtigung zum Ändern eines Inhaltsfragments in AEM können dieses ebenfalls nicht über MCP ändern.

Dadurch wird sichergestellt, dass KI-unterstützte Vorgänge mit Ihrem bestehenden AEM-Sicherheits- und Governance-Modell übereinstimmen.

## Verwenden von MCP mit AEM {#using-mcp-with-aem}

Sobald AEM und Ihre MCP-Client-Anwendungen konfiguriert sind, können Sie in der gewünschten Anwendung arbeiten und den LLM auffordern, AEM-Vorgänge auszuführen. Das LLM liest die MCP-Tool-Schemata, wählt die aufzurufenden Tools aus und sequenziert sie nach Bedarf, um Ihre Anfrage zu erfüllen.

>[!IMPORTANT]
>
>Um optimale Ergebnisse zu erzielen, insbesondere bei Eingabeaufforderungen, die mehrere Schritte enthalten oder auf verschiedene Inhaltstypen wie Bilder und Text abzielen, aktivieren Sie ein Denking-Modell oder wählen Sie die Option Denken in Ihrem MCP-Client aus, anstatt sich auf den Auto-Modus zu verlassen.

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

*„Erstellen Sie ein neues Inhaltsfragment für die Frühlingskampagne, das auf unserem Hero-Banner-Modell basiert, und füllen Sie die zugehörigen Felder aus dieser Zusammenfassung aus.*

Das LLM wählt und koordiniert die notwendigen MCP-Tools automatisch.

## Erwartungsmanagement {#expectation-management}

Beachten Sie bei der Arbeit mit LLMs über MCP Folgendes:

* **Hochleistungsfähig, aber nicht unfehlbar**
LLMs können komplexe Aufgaben ausführen, sind aber anfällig für gelegentliche Fehler. Die gleiche Eingabeaufforderung kann ohne offensichtlichen Grund leicht unterschiedliche Ergebnisse oder Darstellungen liefern. Überprüfen Sie Ausgaben immer, bevor Sie Änderungen auf Produktionsinhalte anwenden.

* **Weiterentwicklung der Funktionen**
Die LLM-Modelle werden kontinuierlich verbessert. Im Laufe der Zeit werden sie klüger darin, neue Möglichkeiten zu entdecken, MCP-Tools zu kombinieren, um Ihre Ziele zu erreichen. Eine Aufgabe, für die heute mehrere Eingabeaufforderungen erforderlich sind, kann morgen nahtlos mit einer einzigen Eingabeaufforderung funktionieren.

* **Menschliche Aufsicht ist unverzichtbar**
Stellen Sie sich den LLM als einen kompetenten Assistenten vor, der Supervision braucht. Sie verfügt über breites Wissen und kann kreative Lösungen entwickeln, profitiert jedoch von Ihrer Beratung und Überprüfung. Überprüfen Sie die Ergebnisse, insbesondere bei kritischen Vorgängen, und geben Sie Feedback, wenn die Ausgabe nicht Ihren Erwartungen entspricht.

* **Seien Sie vorsichtig mit der automatischen Quittierung von Tool-Ausführungen**
Einige MCP-Client-Anwendungen, wie Claude, bieten die Möglichkeit, die vom LLM angeforderten Tool-Ausführungen automatisch zu bestätigen. Dies kann für schreibgeschützte Vorgänge wie das Suchen oder Abrufen von Inhalten praktisch sein. Gehen Sie jedoch mit Tools, die Inhalte aktualisieren oder löschen, vorsichtig vor. Überprüfen Sie jede Anfrage zur Ausführung des Tools, bevor Sie Aktionen bestätigen, die Ihre AEM-Umgebung ändern.

## Einschränkungen {#limitations}

Die MCP-Server von AEM sollen derzeit in ChatGPT, Claude, Cursor und Microsoft Copilot Studio konfiguriert werden.

Wenn Sie eine andere MCP-Client-Anwendung verwenden möchten, wenden Sie sich unter **aemcs-mcp-feedback@adobe.com** an uns, um Unterstützung für weitere Clients anzufordern oder einen benutzerdefinierten Client auf die Zulassungsliste setzen.
