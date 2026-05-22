---
title: AEM Edge-Funktionen
description: Erfahren Sie, wie Sie JavaScript auf CDN-Ebene mit AEM Edge-Funktionen ausführen können, um Endbenutzerinnen und Endbenutzern Personalisierung, Sicherheit und dynamische Erlebnisse zu ermöglichen.
feature: Developing, Edge Delivery Services
role: Developer
exl-id: 9cebe65c-6aea-4096-9c58-f88295a80639
source-git-commit: b33a565d9623ed44309e1d34377345dae86757cd
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 3%

---

# AEM Edge-Funktionen {#aem-edge-functions}

>[!IMPORTANT]
>
>AEM Edge Functions ist eine **Beta**-Funktion. Funktionen und Dokumentation können sich ohne Vorankündigung ändern. Um am Early-Access-Programm teilzunehmen und Feedback zu geben, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com).

Mit den AEM Edge-Funktionen können Sie JavaScript auf CDN-Ebene ausführen, wodurch die Datenverarbeitung näher an den Endbenutzer heranrückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse ohne einen Roundtrip zu Ihrem Ursprung.

Häufige Anwendungsfälle umfassen:

- Personalisieren von Inhalten basierend auf Informationen wie Geolokalisierung, Gerätetyp oder Benutzerattributen
- Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
- Umformatieren oder Aggregieren von Antworten von Drittanbieter-APIs, bevor sie den Browser erreichen
- Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus mehreren Backends zusammengefügt wurden

AEM Edge-Funktionen sind sowohl mit Edge Delivery Services als auch mit dem AEM as a Cloud Service Java-Stack kompatibel.

## Wichtigste Vorteile {#key-benefits}

| Vorteil | Beschreibung |
|---|---|
| **Leistung** | Schnelles TTFB über Edge SSR, das vollständig gerenderte HTML zurückgibt. API-Aufrufe mit geringer Latenz über parallele Abrufe und optimierte Netzwerk-Hops. |
| **SEO/GEO** | Server-HTML wird beim ersten crawlen indiziert. Vollständig gerenderte Inhalte sind für KI-Crawler bereit. |
| **Sicherheit** | API-Anmeldeinformationen Server-seitig aufbewahren und vor Client-JavaScript verbergen. Authentifizierung bei einem Identitätsanbieter und Einschränkung des Inhaltszugriffs. |
| **Personalisierung** | Personalisieren Sie Inhalte vor dem Laden der Seite anhand von Geo- und Gerätesignalen. Führen Sie Zielgruppen-Lookups am Edge für einen zielgerichteten Versand aus. |

## Voraussetzungen {#prerequisites}

- Eine AEM as a Cloud Service-Umgebung
- Das AEM-Administratorproduktprofil in der Autoreninstanz Ihrer Cloud Service-Umgebung **oder** Rolle &quot;Cloud Manager-Bereitstellungs-Manager“ in Admin Console für Edge Delivery Services Sites
- [Node.js und npm](https://nodejs.org/)

## Einrichtung {#setup}

### Installieren des Adobe-CLI {#install-adobe-cli}

Installieren des Adobe Developer-CLI (`aio`):

```bash
npm install -g @adobe/aio-cli
```

Installieren des AEM Edge-Funktions-Plug-ins:

```bash
aio plugins install @adobe/aio-cli-plugin-aem-edge-functions
```

Authentifizieren und Konfigurieren des Plug-ins für Ihre Umgebung:

```bash
aio login
aio aem edge-functions setup
```

Der Setup-Befehl fordert Sie zur Anmeldung auf und wählt dann die AEM-Umgebung aus, in der Sie AEM Edge-Funktionen verwenden möchten.

### Textbaustein klonen {#boilerplate}

Kopieren Sie [aem-edge-features-boilerplate](https://github.com/adobe/aem-edge-functions-boilerplate) in Ihr eigenes Repository und installieren Sie dann die Abhängigkeiten:

```bash
npm install
```

## Erstellen der ersten Funktion {#create-your-function}

AEM Edge-Funktions-Services werden in einer YAML-Konfigurationsdatei deklariert und über die Cloud Manager-Konfigurations-Pipeline bereitgestellt.

### &#x200B;1. Einrichten einer Konfigurations-Pipeline {#configuration-pipeline}

Stellen Sie vor dem Erstellen einer Edge-Funktion sicher, dass in Cloud Manager eine Konfigurations-Pipeline für Ihre Umgebung vorhanden ist. Wenn nicht, erstellen [ zuerst eine Konfigurations](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)Pipeline.

>[!NOTE]
>
>Wenn Sie eine schnelle Entwicklungsumgebung (RDE) verwenden, können Sie die Konfiguration direkt mit `aio aem rde:install -t env-config ./config` bereitstellen, anstatt eine Konfigurations-Pipeline zu verwenden.

### &#x200B;2. Edge Function Services deklarieren {#declare-services}

Erstellen Sie eine Datei mit dem Namen `edgeFunctions.yaml` im Konfigurationsverzeichnis:

```yaml
kind: "EdgeFunctions"
version: "1"
data:
  services:
    - name: first-function
    - name: second-function
    # Uncomment to enable secrets
    # secrets:
    #   - key: API_TOKEN
    #     value: ${{ API_TOKEN_SECRET }}
```

Die Konfiguration unterstützt bis zu drei Services. Die Schlüssel der obersten Ebene sind:

| Schlüssel | Beschreibung |
|---|---|
| `services` | Liste der Edge-Funktions-Services, die jeweils durch eine `name` gekennzeichnet sind. |
| `configs` | Schlüssel/Wert-Paare, die allen Edge-Funktions-Services als Umgebungsvariablen bereitgestellt werden. |
| `secrets` | Schlüssel/Wert-Paare, die auf Cloud Manager-Geheimnisse verweisen und für alle Edge-Funktions-Services verfügbar gemacht werden. |

### &#x200B;3. Hinzufügen von CDN-Ursprungsauswahlregeln {#cdn-routing}

Edge-Funktionen werden aufgerufen, indem CDN-Traffic über Regeln der Ursprungsauswahl an sie weitergeleitet wird. Fügen Sie der `cdn.yaml`-Konfigurationsdatei Folgendes hinzu (oder erstellen Sie eine, falls sie nicht vorhanden ist):

```yaml
kind: 'CDN'
version: '1'
data:
  originSelectors:
    rules:
      - name: route-to-first-function
        when: { reqProperty: path, equals: "/weather" }
        action:
          type: selectAemOrigin
          originName: edgefunction-first-function
      - name: route-to-second-function
        when: { reqProperty: path, equals: "/hello-world" }
        action:
          type: selectAemOrigin
          originName: edgefunction-second-function
```

Mit den Regeln der Ursprungsauswahl können Sie Traffic basierend auf einer in der CDN-Regel-Engine verfügbaren Bedingung, z. B. einem bestimmten Pfad, einer bestimmten Domain oder einem Anfrageheader, an Ihre Edge-Funktionen weiterleiten. Siehe [Ursprungs-Selektoren](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) für die vollständige Regelsyntax.

### &#x200B;4. Bereitstellen der Konfiguration {#deploy-configuration}

Übertragen Sie sowohl `edgeFunctions.yaml` als auch `cdn.yaml` in das Cloud Manager-Git-Repository und erstellen Sie einen Trigger für die Konfigurations-Pipeline. Sobald die Pipeline erfolgreich abgeschlossen wurde, sind Ihre Edge-Funktionsendpunkte unter verfügbar:

- `publish-pXXXXX-eYYYYY.adobeaemcloud.com/weather`
- `publish-pXXXXX-eYYYYY.adobeaemcloud.com/hello-world`

Wo `pXXXXX-eYYYYY` Ihre Umgebungskoordinaten sind. Wenn eine benutzerdefinierte Domain konfiguriert ist, sind die Funktionen auch über diese Domain-Pfade erreichbar (z. B. `example.com/weather`).

## Erstellen und Bereitstellen des Funktionscodes für AEM Edge {#build-deploy}

### Aufbauen {#build}

Verpacken Sie Ihren Edge-Funktions-Code für die Bereitstellung:

```bash
aio aem edge-functions build
```

### Bereitstellen {#deploy}

Stellen Sie das erstellte Paket in einem benannten Edge-Funktions-Service bereit. Das `function-name`-Argument muss mit dem `name` in `edgeFunctions.yaml` übereinstimmen:

```bash
aio aem edge-functions deploy <function-name>
```

## Lokale Entwicklung {#local-development}

### Lokal ausführen {#local-run}

Starten Sie einen lokalen Entwicklungs-Server unter `http://127.0.0.1:7676`:

```bash
aio aem edge-functions serve
```

In dieser [Compute JavaScript-Dokumentation](https://www.fastly.com/documentation/guides/compute/javascript/) finden Sie Details dazu, was die lokale Laufzeit unterstützt.

### Testen {#test}

Ausführen der Test-Suite mit [Mokka](https://mochajs.org/):

```bash
npm run test
```

### Remote-Debugging {#remote-debugging}

Das von Adobe verwaltete CDN stellt keinen Remote-Debugger bereit, stellt jedoch Protokoll-Streaming bereit. Verfolgen Sie die Protokolle für eine bereitgestellte Funktion, um `console.log` Ausgabe direkt in Ihrem Terminal zu erhalten:

```bash
aio aem edge-functions tail-logs <function-name>
```

## Caching und Cache-Bereinigung {#caching}

Edge-Funktionen können die Ursprungslast erheblich reduzieren und die Antwortzeiten verbessern, indem Daten am Edge zwischengespeichert werden. Für das Caching ist jedoch ein absichtliches Design erforderlich - insbesondere in Edge-Funktionen **bei denen (zwei unabhängige Cache** Ebenen) involviert sind:

```
Browser → AEM CDN (CDN Cache) → AEM Edge Functions (Fetch Cache) → Backend (AEM, APIs, etc.)
```

Bevor Sie das Caching konfigurieren, überlegen Sie, wie sich Ihr Inhalt verhält:

- **Wirklich eindeutige Inhalte pro Anfrage** (Sitzungs-Token, Echtzeit-Preise für einen bestimmten Benutzer) sollten die Zwischenspeicherung umgehen, um zu vermeiden, dass falsche Ergebnisse bereitgestellt werden.
- **Kohortenbasierte Personalisierung** (Inhalte, die nach Region, Gerätetyp oder Zielgruppensegment zugeschnitten sind) kann oft mit kürzeren TTLs oder `Vary`-Headern zwischengespeichert werden, da viele Benutzende dieselbe Variante nutzen.
- **Stabiler, freigegebener Inhalt** (Produktkataloge, CMS-Seiten, API-Antworten, die sich nach einem bekannten Zeitplan ändern) profitiert von aggressivem Caching mit expliziter Invalidierung über Ersatzschlüssel.
- **Wenn wir das in beide Richtungen falsch machen, hat das Konsequenzen.** Das Übercaching verursacht veraltete Inhaltsfehler, die auf zwei Cache-Ebenen schwer zu diagnostizieren sind. Die unzureichende Zwischenspeicherung vereitelt den Zweck der Leistungs- und Ursprungs-Abladung bei der Verwendung von Edge-Funktionen überhaupt.

Da das CDN und der interne Abrufcache der Edge-Funktion unabhängig voneinander arbeiten, erfordert eine Änderung der zugrunde liegenden Daten die bewusste Invalidierung **beider** Ebenen. Das Verständnis dieser Architektur ist für eine zuverlässige Cache-Verwaltung unerlässlich.

Detaillierte technische Anleitungen zum Konfigurieren des Caching-Verhaltens, zum Steuern der Cache-Lebensdauer, zum Verwenden von Ersatzschlüsseln und zum Bereinigen von zwischengespeicherten Inhalten finden Sie unter [Caching in AEM Edge Functions](/help/implementing/developing/introduction/edge-functions-caching.md).

## Einschränkungen {#limitations}

Jeder Edge-Funktionsaufruf wird innerhalb einer Sandbox mit Ressourcenbeschränkungen ausgeführt, die von der zugrunde liegenden Rechenplattform erzwungen werden.

### Maximal ausgehende Abrufaufrufe pro Aufruf {#max-fetch-calls}

AEM Edge-Funktionen erzwingen eine feste Grenze von **32 Backend-Anfragen pro Ausführung** (d. h. pro eingehender Anfrage, die von Ihrer Funktion verarbeitet wird). Sobald diese Grenze erreicht ist, schlagen alle weiteren `fetch()`-Aufrufe mit dem folgenden Fehler fehl:

```
Requested backend named '…' does not exist
```

Wenn dieser Fehler angezeigt wird und Ihre ursprüngliche Konfiguration korrekt ist, besteht die wahrscheinlichste Ursache darin, dass das Kontingent für die Backend-Anfrage pro Aufruf ausgeschöpft wurde. Siehe [Fastly Compute Resource Limits](https://docs.fastly.com/products/compute-resource-limits#default-limits) für die vollständige Liste der Platform Limits.

## Konfigurationsreferenz {#configuration-reference}

### Ursprünge {#origins}

Standardmäßig können Edge-Funktionen aus jedem beliebigen Ursprung abgerufen werden. Um eine Funktion auf einen definierten Satz von Ursprüngen zu beschränken, deklarieren Sie sie unter `origins` in `edgeFunctions.yaml`:

```yaml
origins:
  - name: my-origin-name
    domain: example.com
```

Referenzieren Sie die benannte Herkunft in Ihrem Funktionscode mithilfe der `backend`-Fetch-Option:

```js
const request = new Request("https://example.com/test");
const response = await fetch(request, { backend: "my-origin-name" });
```

### Service-Konfiguration {#service-configuration}

Offenlegung von Umgebungsvariablen für Ihre Funktionen mithilfe der `configs` in `edgeFunctions.yaml`. Die Werte werden in einem Konfigurationsspeicher mit dem Namen `config_default` gespeichert:

```yaml
configs:
  - key: LOG_LEVEL
    value: DEBUG
```

Lesen Sie die Konfigurationswerte im Funktionscode:

```js
import { ConfigStore } from "fastly:config-store";

const config = new ConfigStore('config_default');
const logLevel = config.get('LOG_LEVEL') || 'info';
```

>[!NOTE]
>
>- Der Konfigurationsspeicher hat immer den Namen `config_default`.
>- Bei Schlüsselnamen wird zwischen Groß- und Kleinschreibung unterschieden.
>- Der Konfigurationsspeicher wird für alle Edge-Funktions-Services in derselben Umgebung freigegeben.

### Dienstgeheimnisse {#service-secrets}

Geheimnisse werden in `edgeFunctions.yaml` referenziert, nicht gespeichert. Das `value` muss mithilfe der `${{SECRET_REFERENCE}}` auf geheime Daten vom Typ Cloud Manager verweisen. Definieren Sie zunächst das zugrunde liegende Geheimnis in Cloud Manager - siehe [Cloud Manager-Geheimnisvariablen](/help/implementing/cloud-manager/environment-variables.md).

```yaml
secrets:
  - key: API_TOKEN
    value: ${{ API_TOKEN_SECRET }}
```

Abrufen von geheimen Daten im Funktionscode mithilfe des `SecretStoreManager` Helpers aus dem Textbaustein:

```js
import { SecretStoreManager } from "./lib/config";

const apiToken = await SecretStoreManager.getSecret('API_TOKEN');
```

>[!NOTE]
>
>- Der geheime Speicher heißt immer `secret_default`.
>- Bei Schlüsselnamen wird zwischen Groß- und Kleinschreibung unterschieden.
>- Geheime Daten sind unveränderlich, sobald sie erstellt wurden.
>- Der geheime Speicher wird für alle Edge-Funktions-Services in derselben Umgebung freigegeben.

### Protokollierung {#logging}

AEM Edge-Funktionen sind mit der Funktion [AEM-](/help/implementing/developing/introduction/log-forwarding.md) integriert. Erstellen Sie eine `logForwarding.yaml` Datei zusammen mit Ihrem `edgeFunctions.yaml`:

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["rde", "dev", "stage", "prod"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

Verwenden Sie den Logger in Ihrem Funktionscode, um strukturierte Protokolleinträge zu schreiben:

```js
import { Logger } from "fastly:logger";

const logger = new Logger("customerSplunk");
logger.log(JSON.stringify({
  method: event.request.method,
  url: event.request.url
}));
```

>[!NOTE]
>
>CDN-Protokolle, die AEM Edge-Funktionsprotokolleinträge enthalten, können für Java-Stack-Umgebungen von Cloud Manager heruntergeladen werden, nicht aber für Edge Delivery Services Sites.
>
