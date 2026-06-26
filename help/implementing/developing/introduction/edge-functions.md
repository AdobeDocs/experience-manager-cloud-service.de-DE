---
title: AEM Edge-Funktionen
description: Erfahren Sie, wie Sie JavaScript auf CDN-Ebene mit AEM Edge-Funktionen ausführen können, um Endbenutzerinnen und Endbenutzern Personalisierung, Sicherheit und dynamische Erlebnisse zu ermöglichen.
feature: Developing, Edge Delivery Services
role: Developer
exl-id: 9cebe65c-6aea-4096-9c58-f88295a80639
source-git-commit: 1bb231d04e0b418a3b56de34c70424d06f94a4e1
workflow-type: tm+mt
source-wordcount: '2023'
ht-degree: 2%

---

# AEM Edge-Funktionen {#aem-edge-functions}

>[!IMPORTANT]
>
>AEM Edge Functions ist eine **öffentliche Beta**-Funktion, mit der Sie sie im Selbstbedienungsmodus ausprobieren können, ohne sich zur Aktivierung an Adobe zu wenden. Adobe empfiehlt Ihnen, eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) zu senden, um Ihren Anwendungsfall zu beschreiben, damit Adobe sicherstellen kann, dass er unterstützt wird, und eine Anleitung bereitstellen kann. Es ist besonders wichtig, Adobe zu kontaktieren, bevor Sie die Funktion für den Produktions-Traffic bereitstellen.
>
>Durch die Verwendung von AEM Edge Functions Beta erkennen Sie an, dass es sich noch in der Entwicklung befindet und Sie sich nicht auf die ordnungsgemäße Funktionsweise der Technologie oder die Verfügbarkeit der Daten verlassen sollten. Diese Funktion wird unverändert bereitgestellt, kann sich ohne Vorankündigung ändern und wird nicht von der Produktion abgedeckt.

Mit den AEM Edge-Funktionen können Sie JavaScript auf CDN-Ebene ausführen, wodurch die Datenverarbeitung näher an den Endbenutzer heranrückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse ohne einen Roundtrip zu Ihrem Ursprung.

Häufige Anwendungsfälle umfassen:

- Personalisieren von Inhalten basierend auf Informationen wie Geolokalisierung, Gerätetyp oder Benutzerattributen
- Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
- Umformatieren oder Aggregieren von Antworten von Drittanbieter-APIs, bevor sie den Browser erreichen
- Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus mehreren Backends zusammengefügt wurden

AEM Edge-Funktionen sind sowohl mit Edge Delivery Services als auch mit dem AEM as a Cloud Service Java-Stack für AEM Sites-Kunden kompatibel.

In [diesem Tutorial](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/edge-functions/overview) finden Sie eine Anleitung für Edge Delivery Services und AEM as a Cloud Service Java-Stack-Varianten.

## Wichtigste Vorteile {#key-benefits}

| Vorteil | Beschreibung |
|---|---|
| **Leistung** | Schnelles TTFB über Edge SSR, das vollständig gerenderte HTML zurückgibt. API-Aufrufe mit geringer Latenz über parallele Abrufe und optimierte Netzwerk-Hops. |
| **SEO/GEO** | KI-Crawler können Inhalte indizieren, die Server-seitig zusammengefügt werden. |
| **Sicherheit** | API-Anmeldeinformationen Server-seitig aufbewahren und vor Client-JavaScript verbergen. Authentifizierung bei einem Identitätsanbieter und Einschränkung des Inhaltszugriffs. |
| **Personalisierung** | Personalisieren Sie Inhalte vor dem Laden der Seite anhand von Geo- und Gerätesignalen. Führen Sie Zielgruppen-Lookups am Edge für einen zielgerichteten Versand aus. |

## Voraussetzungen {#prerequisites}

- Ein Cloud Manager-Programm, das entweder AEM Java-Stack-Umgebungen oder Edge Delivery Services Sites enthält. Erfahren Sie, wie Sie [EDS Sites in Cloud Manager integrieren](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).
- Eine Cloud Manager-Konfigurations-Pipeline (genannt Edge Delivery Services-Pipeline für EDS Sites).
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

## Registrieren der AEM Edge-Funktion {#register-your-function}

AEM Edge-Funktionen werden in einer YAML-Konfigurationsdatei deklariert und über die Cloud Manager-Konfigurations-Pipeline bereitgestellt.

### &#x200B;1. Einrichten einer Konfigurations-Pipeline {#configuration-pipeline}

Stellen Sie vor dem Erstellen einer Edge-Funktion sicher, dass in Cloud Manager eine Konfigurations-Pipeline für Ihre Umgebung vorhanden ist (wenn Sie den AEM Java-Stack verwenden) oder dass eine Edge Delivery Services-Pipeline vorhanden ist, wenn Ihr Projekt mit Edge Delivery Services implementiert ist. Informationen [&#x200B; Konfigurieren der Pipelines finden &#x200B;](/help/operations/config-pipeline.md) unter „Verwenden von-Pipelines“.

>[!NOTE]
>
>Wenn Sie eine schnelle Entwicklungsumgebung (RDE) verwenden, können Sie die Konfiguration direkt mit `aio aem rde:install -t env-config ./config` bereitstellen, anstatt eine Konfigurations-Pipeline zu verwenden.

### &#x200B;2. Edge-Funktion deklarieren {#declare-functions}

Erstellen Sie eine Datei mit dem Namen `edgeFunctions.yaml` im Konfigurationsverzeichnis:

```yaml
kind: "EdgeFunctions"
version: "1"
data:
  functions:
    - name: my-edge-function
    # add advanced configuration under here
```

Java-Stack-Umgebungen verfügen über 1 Edge-Funktion und Edge Delivery Services-Implementierungen über 3 Edge-Funktionen. Die optionalen Schlüssel der obersten Ebene sind:

| Schlüssel | Beschreibung |
|---|---|
| `functions` | Liste der Kantenfunktionen, jeweils gekennzeichnet durch eine `name`. Aus Gründen der Abwärtskompatibilität wird `services` ebenfalls akzeptiert, aber `functions` ist der bevorzugte Schlüssel. Die Verwendung von beiden in derselben Datei ist nicht zulässig. |
| `configs` | Schlüssel/Wert-Paare, die den Edge-Funktionen einer Umgebung als Umgebungsvariablen bereitgestellt werden. |
| `secrets` | Schlüssel/Wert-Paare, die auf Cloud Manager-Geheimnisse verweisen, in Bezug auf die Edge-Funktionen einer Umgebung |
| `kvs` | Boolescher Umschalter zur Bereitstellung eines KV-Speichers für Schlüsselwertdaten mit Lese-/Schreibzugriff zur Laufzeit, die über alle Edge-Funktionen in einer Umgebung hinweg gemeinsam genutzt werden. |

Weitere Informationen zur erweiterten Konfiguration wie `configs`, `secrets` und `kvs` finden Sie [&#x200B; Abschnitt „Erweiterte Konfiguration](#advanced-function-configuration) weiter unten.

### &#x200B;3. Bereitstellen der Edge-Funktion über Cloud Manager {#deploy-functions-via-cm}

Stellen Sie mithilfe von Cloud Manager die Pipeline bereit, damit die Edge-Funktion im CDN registriert wird.

## AEM Edge-Funktions-Code erstellen, erstellen und bereitstellen {#build-deploy}

### Author {#author}

Schreiben Sie Ihre Geschäftslogik für den Edge-Funktions[Code mithilfe des `src` Ordners &#x200B;](https://github.com/adobe/aem-edge-functions-boilerplate/tree/main/src)Textbausteinvorlage“ als Ausgangspunkt.

### Aufbauen {#build}

Verpacken Sie Ihren Edge-Funktions-Code für die Bereitstellung:

```bash
aio aem edge-functions build
```

### Bereitstellen {#deploy}

Stellen Sie den gepackten Code der Edge-Funktion für die benannte Edge-Funktion bereit. Das `function-name`-Argument muss mit dem `name` in `edgeFunctions.yaml` übereinstimmen:

```bash
aio aem edge-functions deploy <function-name>
```

### Testen {#test}

Stellen Sie sicher, dass die Kantenfunktion erwartungsgemäß funktioniert. Sie können es unter folgender Adresse testen:

`edgefunction-pXXXXX-eYYYYY-<function name>.adobeaemcloud.com/<path>`

Beispielsweise für den AEM Java-Stack: <br/>
`edgefunction-pXXXXX-eYYYYY-my-edge-function.adobeaemcloud.com/weather`

oder für Edge Delivery Services:<br/>
`edgefunction-pXXXXX-dYYYYY-my-edge-function.adobeaemcloud.com/weather`

Diese Domain mit dem Präfix *EDGEFUNCTION* dient nur zur Fehlerbehebung, darf *für Live-Traffic nicht referenziert werden* da kein stabiler Name garantiert ist. Informationen zum Bestimmen des Werts für JJJJ finden Sie in der Ausgabe des Bereitstellungsbefehls.


## In den Inhaltsbereitstellungs-Fluss integrieren {#wiring}

Funktions-Traffic von Edge sollte an die Domain der Website gesendet werden, die normalerweise eine benutzerdefinierte Domain für den AEM Java-Stack ist, und *muss* eine benutzerdefinierte Domain für Edge Delivery Services Sites sein.

### &#x200B;1. Herkunft-Selektoren definieren {#origin-selectors}

Edge-Funktionen werden aufgerufen, indem CDN-Traffic über Regeln der Ursprungsauswahl an sie weitergeleitet wird. Fügen Sie der `cdn.yaml`-Konfigurationsdatei Folgendes hinzu (oder erstellen Sie eine, falls sie nicht vorhanden ist):

```yaml
kind: 'CDN'
version: '1'
data:
  originSelectors:
    rules:
      - name: route-weather-to-edge-function
        when: { reqProperty: path, equals: "/weather" }
        action:
          type: selectAemOrigin
          originName: edgefunction-my-edge-function
      - name: route-hello-world-to-edge-function
        when: { reqProperty: path, equals: "/hello-world" }
        action:
          type: selectAemOrigin
          originName: edgefunction-my-edge-function
```

Mit den Regeln der Ursprungsauswahl können Sie Traffic basierend auf einer in der CDN-Regel-Engine verfügbaren Bedingung, z. B. einem bestimmten Pfad, einer bestimmten Domain oder einem Anfrageheader, an Ihre Edge-Funktionen weiterleiten. Mehrere Regeln können verschiedene Pfade zu derselben Edge-Funktion routen. Siehe [Ursprungs-Selektoren](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) für die vollständige Regelsyntax.

### &#x200B;2. Bereitstellen der Konfiguration {#deploy-to-cdn}

Übertragen Sie `cdn.yaml` in Ihr Cloud Manager-Git-Repository und Trigger in die Konfigurations-Pipeline. Sobald die Pipeline erfolgreich abgeschlossen wurde, sind Ihre Edge-Funktionsendpunkte unter verfügbar:

- `example.com/weather`
- `example.com/hello-world`

Zum Debuggen können Sie die Edge-Funktion auf der Domain-`publish-pXXXXX-eYYYYY.adobeaemcloud.com` (für den AEM Java-Stack) oder `publish-pXXXXX-dYYYYY.adobeaemcloud.com` (für Edge Delivery Services Sites) referenzieren. Verwenden Sie diese Domain nicht für die Verwendung in der Produktion, da sie nicht garantiert ein stabiler Name ist. Informationen zum Bestimmen des Werts für JJJJ finden Sie in der Ausgabe des Bereitstellungsbefehls.

## Lokale Entwicklung {#local-development}

### Lokal ausführen {#local-run}

Starten Sie einen lokalen Entwicklungs-Server unter `http://127.0.0.1:7676`:

```bash
aio aem edge-functions serve
```

In dieser [Compute JavaScript-Dokumentation](https://www.fastly.com/documentation/guides/compute/javascript/) finden Sie Details dazu, was die lokale Laufzeit unterstützt.

### Testen {#test-localdev}

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

- Jeder Edge-Funktionsaufruf wird innerhalb einer Sandbox mit Ressourcenbeschränkungen ausgeführt, die von der zugrunde liegenden Rechenplattform erzwungen werden.

- Die maximale Größe des erstellten Web-Assembly-Artefakts (wasm) beträgt 100 MB

- Maximaler Speicherverbrauch beträgt 1 MB Byte-Stack, 128 MB Heap

- Wichtige Informationen zur Ausführung der Edge-Funktion:
   - Eine Ausführung wird nach 120s Wandzeit beendet
   - Ausführungen werden mit 1 s Berechnung beendet (nicht Wandzeit)
   - Die durchschnittliche Ausführungszeit der Edge-Funktion muss unter 100 ms liegen.

- Siehe Einschränkungen in Bezug auf [Edge-Funktionskonfigurationsvariablen](#function-configuration), [Edge-](#function-secrets) und [Edge-Funktions-KV-Speicher](#function-kv-store).

### Maximal ausgehende Abrufaufrufe pro Aufruf {#max-fetch-calls}

AEM Edge-Funktionen erzwingen eine feste Grenze von **32 Backend-Anfragen pro Ausführung** (d. h. pro eingehender Anfrage, die von Ihrer Funktion verarbeitet wird). Sobald diese Grenze erreicht ist, schlagen alle weiteren `fetch()`-Aufrufe mit dem folgenden Fehler fehl:

```
Requested backend named '…' does not exist
```

Wenn dieser Fehler angezeigt wird und Ihre ursprüngliche Konfiguration korrekt ist, besteht die wahrscheinlichste Ursache darin, dass das Kontingent für die Backend-Anfrage pro Aufruf ausgeschöpft wurde. Siehe [Fastly Compute Resource Limits](https://docs.fastly.com/products/compute-resource-limits#default-limits) für die vollständige Liste der Platform Limits.

## Erweiterte Edge-Funktionskonfiguration {#advanced-function-configuration}

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

>[!NOTE]
>
>Konfigurationen, Geheimnisse und KVs sind in [Sandbox-Programmen) &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Edge-Funktionen selbst werden in Sandbox-Umgebungen normal ausgeführt - nur diese Entitäten werden nicht bereitgestellt.

### Edge-Funktionskonfigurationsvariablen {#function-configuration}

Offenlegung von Umgebungsvariablen für Ihre Funktionen mithilfe der `configs` in `edgeFunctions.yaml`. Die Werte werden in einem Konfigurationsspeicher mit dem Namen `config_default` gespeichert:

```yaml
kind: "EdgeFunctions"
version: "1"
data:
  functions:
    - name: my-edge-function
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
>- Der Konfigurationsspeicher wird für alle Edge-Funktionen in derselben Umgebung freigegeben.
>- Der Konfigurationsspeicher wird über das globale Netzwerk des von Adobe verwalteten CDN repliziert
>- Max. 500 Einträge
>- Max. Größe für Name/Wert: 255 und 8.000 Zeichen


### Edge-Funktionsgeheimnis-Variablen {#function-secrets}

Geheimnisse werden in `edgeFunctions.yaml` referenziert, nicht gespeichert. Das `value` muss mithilfe der `${{SECRET_REFERENCE}}` auf geheime Daten vom Typ Cloud Manager verweisen. Definieren Sie zunächst das zugrunde liegende Geheimnis in Cloud Manager - siehe [Cloud Manager-Geheimnisvariablen](/help/implementing/cloud-manager/environment-variables.md).


```yaml
kind: "EdgeFunctions"
version: "1"
data:
  functions:
    - name: my-edge-function
  secrets:
    - key: API_TOKEN
      value: ${{API_TOKEN_SECRET}}
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
>- Der geheime Speicher wird für alle Edge-Funktionen in derselben Umgebung freigegeben.
>- Der geheime Speicher wird über das globale Netzwerk des von Adobe verwalteten CDN repliziert
>- Maximale Größe aller geheimen Daten: 64 KB

### Edge-Funktions-KV-Speicher {#function-kv-store}

Edge-Funktionen können beliebige Schlüssel-Wert-Daten zur Laufzeit über einen KV-Speicher lesen und schreiben. Um sie zu aktivieren, legen Sie `kvs: true` in `edgeFunctions.yaml` fest:


```yaml
kind: "EdgeFunctions"
version: "1"
data:
  functions:
    - name: my-edge-function
  kvs: true
```

Dadurch wird ein leerer KV-Speicher mit dem Namen `kv_default` bereitgestellt. Füllen Sie es zur Laufzeit aus Ihrem Edge-Funktions-Code mithilfe der [Fastly KV Store-API](https://js-compute-reference-docs.edgecompute.app/docs/fastly:kv-store/KVStore):

```js
import { KVStore } from "fastly:kv-store";

const kv = new KVStore('kv_default');

// Read a value
const entry = await kv.get('visit-count');
const count = entry ? Number(await entry.text()) : 0;

// Write a value
await kv.put('visit-count', String(count + 1));
```

>[!NOTE]
>
>- Der KV-Speicher heißt immer `kv_default`.
>- Der KV-Speicher ist zur Bereitstellungszeit leer; füllen Sie ihn zur Laufzeit über die [Fastly KV-Speicher-API](https://js-compute-reference-docs.edgecompute.app/docs/fastly:kv-store/KVStore). Deklarative Schlüssel/Wert-Einträge in `edgeFunctions.yaml` werden nicht unterstützt.
>- Der KV-Speicher ist über alle Edge-Funktionen in derselben Umgebung verteilt.
>- Der KV-Speicher wird über das globale Netzwerk des von Adobe verwalteten CDN repliziert
>- KV-Speicher sorgen letztendlich für Konsistenz, was bedeutet, dass das Lesen eines Schlüssels unmittelbar nach dem Schreiben nicht unbedingt den aktualisierten Wert zurückgibt.
>- KV-Schlüsselnamen sind maximal 1024 Byte UTF-8-Dateien
>- KV-Eingangsgröße ist max. 25M
>- KV-Speicher-Elemente haben eine Ratenbegrenzung von 1 Schreib pro Sekunde pro Element.
>- Für KV-Speicherartikel-Batch-Anforderungen gilt eine Beschränkung von 100.000 Elementen pro Anforderung.


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
>CDN-Protokolle, die AEM Edge-Funktionsprotokolleinträge enthalten, können für Java-Stack-Umgebungen von Cloud Manager heruntergeladen werden, nicht aber für Edge Delivery Sites.
>

