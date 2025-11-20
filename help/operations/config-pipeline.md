---
title: Verwenden von Konfigurations-Pipelines
description: Erfahren Sie, wie Sie Konfigurations-Pipelines verwenden können, um in AEM as a Cloud Service verschiedene Konfigurationen wie Einstellungen für die Protokollweiterleitung, Bereinigungsaufgaben und verschiedene CDN-Konfigurationen bereitzustellen.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: 5e0626c57f233ac3814355d7efe7db010897d72b
workflow-type: tm+mt
source-wordcount: '1378'
ht-degree: 50%

---

# Konfigurieren von Pipelines {#config-pipelines}

Erfahren Sie, wie Sie Konfigurations-Pipelines verwenden können, um in AEM as a Cloud Service verschiedene Konfigurationen wie Einstellungen für die Protokollweiterleitung, Bereinigungsaufgaben und verschiedene CDN-Konfigurationen bereitzustellen.

## Überblick {#overview}

Eine Cloud Manager-Konfigurations-Pipeline stellt Konfigurationsdateien (die im YAML-Format erstellt wurden) in einer Zielumgebung bereit. Auf diese Weise kann eine Reihe von Funktionen in AEM as a Cloud Service konfiguriert werden, darunter die Protokollweiterleitung, Bereinigungsaufgaben sowie verschiedene CDN-Funktionen.

Bei **Veröffentlichungsbereitstellung**-Projekten können Konfigurations-Pipelines über Cloud Manager für Entwicklungs-, Staging- und Produktionsumgebungstypen bereitgestellt werden. Die Konfigurationsdateien können mit dem [Befehlszeilen-Tool](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline) in schnellen Entwicklungsumgebungen (Rapid Development Environments, RDEs) bereitgestellt werden.

Konfigurations-Pipelines können auch über Cloud Manager für **Edge Delivery-Projekte** werden.

In den folgenden Abschnitten dieses Dokuments erhalten Sie einen Überblick über wichtige Informationen dazu, wie Konfigurations-Pipelines verwendet werden können und wie Konfigurationen für diese strukturiert sein sollten. Es werden allgemeine Konzepte beschrieben, die für alle oder eine Teilmenge der von Konfigurations-Pipelines unterstützten Funktionen freigegeben werden.

* [Unterstützte Konfigurationen](#configurations) - Eine Liste der Konfigurationen, die mit Konfigurations-Pipelines bereitgestellt werden können.
* [Erstellen und Verwalten von Konfigurations-](#creating-and-managing): So erstellen Sie eine Konfigurations-Pipeline
* [Allgemeine Syntax](#common-syntax) - Syntax, die in allen Konfigurationen verwendet wird.
* [Ordnerstruktur](#folder-structure): Beschreibt die Konfigurationsstruktur, die Pipelines für die Konfigurationen erwarten.
* [Geheime Umgebungsvariablen](#secret-env-vars) - Beispiele für die Verwendung von Umgebungsvariablen, um Geheimnisse in Ihren Konfigurationen nicht offenzulegen.
* [Geheime Pipeline-Variablen](#secret-pipeline-vars) - Beispiele für die Verwendung von Umgebungsvariablen, um geheime Daten nicht in Ihren Konfigurationen für Edge Delivery Services-Projekte offenzulegen.

## Unterstützte Konfigurationen {#configurations}

Die folgende Tabelle enthält eine umfassende Liste solcher Konfigurationen mit Links zur entsprechenden Dokumentation, wo die jeweilige Konfigurationssyntax und andere Informationen beschrieben werden.

| Typ | YAML `kind`-Wert | Beschreibung | Veröffentlichungsbereitstellung | Edge-Bereitstellung |
|---|---|---|---|---|
| [Traffic-Filterregeln, einschließlich WAF](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | Deklarieren von Regeln zur Verhinderung von schädlichem Traffic | X | X |
| [Anfrageumwandlungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | Deklarieren von Regeln zur Umwandlung der Form der Traffic-Anforderung | X | X |
| [Reaktionsumwandlungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | Deklarieren von Regeln zur Umwandlung der Form für die Antwort für eine gegebene Anfrage | X | X |
| [Server-seitige Umleitungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) | `CDN` | Deklarieren von Server-seitigen Umleitungen im Stil 301/302 | X | X |
| [Ursprungs-Auswahlen](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Deklarieren von Regeln, um Traffic an verschiedene Backends zu leiten, einschließlich Adobe-fremder Anwendungen | X | X |
| [CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Überschreiben der standardmäßigen Fehlerseite, wenn der AEM-Ursprung nicht erreicht werden kann, und Referenzieren des Speicherorts des selbst-gehosteten statischen Inhalts in der Konfigurationsdatei | X |  |
| [CDN-Bereinigung](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Deklarieren der API-Bereinigungsschlüssel für die Bereinigung des CDN | X |  |
| [Kundenseitig verwaltetes CDN-HTTP-Token](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Deklarieren des Werts des X-AEM-Edge-Schlüssels, der zum Aufrufen des Adobe CDN von einem Kunden-CDN erforderlich ist | X |  |
| [Standardauthentifizierung](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Deklarieren Sie die Benutzernamen und Kennwörter für einen einfachen Authentifizierungsdialog, der bestimmte URLs schützt. | X | X |
| [Wartungsaufgabe zur Versionsbereinigung](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimieren des AEM-Repositorys durch Deklarieren von Regeln für den Zeitpunkt der Bereinigung von Inhaltsversionen | X |  |
| [Wartungsaufgabe zur Bereinigung des Auditprotokolls](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimieren des AEM-Auditprotokolls für eine verbesserte Leistung durch Deklarieren von Regeln für den Zeitpunkt der Bereinigung von Protokollen | X |  |
| [Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Konfigurieren Sie die Endpunkte und Anmeldedaten für die Weiterleitung von Protokollen an verschiedene Ziele, einschließlich Azure Blob Storage, Datadog, HTTPS, Elasticsearch, Splunk. | X | X |
| [Registrieren einer Client-ID](/help/implementing/developing/open-api-based-apis.md) | `API` | Richten Sie Adobe Developer Console-API-Projekte durch Registrierung der Client-ID auf eine bestimmte AEM-Umgebung ein. Wird für die Verwendung von OpenAPI-basierten APIs benötigt, die eine Authentifizierung erfordern | X |  |

## Konfigurieren von Pipelines {#creating-and-managing}

Informationen zum Erstellen und Konfigurieren von **Veröffentlichungs-Bereitstellung** Konfigurations-Pipelines finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline). Achten Sie beim Erstellen einer Konfigurations-Pipeline in Cloud Manager darauf, beim Konfigurieren **Pipeline „Zielgerichtete Bereitstellung** und nicht **Full-Stack-**&quot; auszuwählen. Wie bereits erwähnt, wird die Konfiguration für RDEs mit dem [Befehlszeilen-Tool](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline) und nicht mit einer Pipeline bereitgestellt.

Informationen zum Erstellen und Konfigurieren von **Edge Delivery**-Konfigurations-Pipelines finden Sie im Artikel [Hinzufügen einer Edge Delivery-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md) .

## Allgemeine Syntax {#common-syntax}

Jede Konfigurationsdatei beginnt mit Eigenschaften, die dem folgenden Beispielausschnitt ähneln:

```yaml
   kind: "CDN"
   version: "1"
   metadata: ...
   data: ...
```

| Eigenschaft | Beschreibung | Standard |
|---|---|---|
| `kind` | Eine Zeichenfolge, die die Art der Konfiguration bestimmt, z. B. Protokollweiterleitung, Traffic-Filterregeln oder Anfrageumwandlungen. | Erforderlich, kein Standard |
| `version` | Eine Zeichenfolge, die die Schemaversion darstellt | Erforderlich, kein Standard |
| `metadata` | (Optional) Dieses enthält ein Array von `envTypes`, das bestimmt, für welche Umgebungstypen die Konfiguration verarbeitet wird. Für **Bereitstellung veröffentlichen** sind mögliche Werte `dev`, `stage` und `prod`. Für **Edge Delivery** sollte nur der Wert `prod` verwendet werden. Wenn das Array beispielsweise nur `dev` enthält, wird die Konfiguration nicht in Staging- oder Produktionsumgebungen geladen, auch wenn die Konfiguration dort bereitgestellt wird. | Alle Umgebungstypen, d. h. (dev, stage, prod) für die Veröffentlichungsbereitstellung oder nur prod für Edge Delivery. |

Sie können das Dienstprogramm `yq` verwenden, um die YAML-Formatierung Ihrer Konfigurationsdatei lokal zu überprüfen (z. B. `yq cdn.yaml`).

## Veröffentlichungsbereitstellung {#yamls-for-aem}

**Veröffentlichungsbereitstellung** Konfigurationen werden in einer Zielumgebung bereitgestellt. Wenn mehrere Umgebungen als Ziel dienen, können die verschiedenen Dateien auf unterschiedliche Weise organisiert werden. Wenn das Array beispielsweise nur `dev` enthält, wird die Konfiguration nicht in Staging- oder Produktionsumgebungen geladen, auch wenn die Konfiguration dort bereitgestellt wird.

```yaml
   kind: "CDN"
   version: "1"
   metadata:
    envType: ["dev"]
```

### Ordnerstruktur {#folder-structure}

Ein Ordner mit dem Namen `/config` oder einem ähnlichen Namen sollte sich ganz oben in der Struktur befinden, wobei sich eine weitere YAML-Datei in einer Struktur darunter befindet.

Zum Beispiel:

```text
/config
  cdn.yaml
```

Oder

```text
/config
  /dev
    cdn.yaml
```

Die Ordner- und Dateinamen unter `/config` sind beliebig. Die YAML-Datei muss jedoch einen gültigen [`kind`-Eigenschaftswert enthalten](#configurations).

In der Regel werden Konfigurationen für alle Umgebungen bereitgestellt. Wenn alle Eigenschaftswerte für jede Umgebung identisch sind, reicht eine einzelne YAML-Datei aus. Es ist jedoch üblich, dass sich Eigenschaftswerte zwischen Umgebungen unterscheiden, z. B. beim Testen einer niedrigeren Umgebung.

Die folgenden Abschnitte zeigen einige Strategien zur Strukturierung Ihrer Dateien.

### Eine einzige Konfigurationsdatei für alle Umgebungen {#single-file}

Die Dateistruktur sieht ähnlich der folgenden aus:

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Verwenden Sie diese Struktur, wenn dieselbe Konfiguration für alle Umgebungen und für alle Konfigurationstypen (CDN, Protokollweiterleitung usw.) ausreicht. In diesem Szenario würde die `envTypes`-Array-Eigenschaft alle Umgebungstypen enthalten.

```yaml
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

Bei Verwendung von Umgebungsvariablen vom Typ „Geheime Daten“ (oder Pipeline[&#x200B; können die &quot;](#secret-env-vars)&quot; je nach Umgebung variieren, wie in der folgenden `${{SPLUNK_TOKEN}}`-Referenz veranschaulicht.

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

### Eine separate Datei pro Umgebungstyp {#file-per-env}

Die Dateistruktur sieht ähnlich der folgenden aus:

```text
/config
  cdn-dev.yaml
  cdn-stage.yaml
  cdn-prod.yaml
  logForwarding-dev.yaml
  logForwarding-stage.yaml
  logForwarding-prod.yaml
```

Verwenden Sie diese Struktur, wenn es Unterschiede bei Eigenschaftswerten geben kann. In den Dateien würde man erwarten, dass der `envTypes` Array-Wert mit dem Suffix übereinstimmt. Beispiel: `cdn-dev.yaml` und `logForwarding-dev.yaml` mit dem Wert `["dev"]`, `cdn-stage.yaml` und `logForwarding-stage.yaml` mit dem Wert `["stage"]` usw.

### Ein Ordner pro Umgebung {#folder-per-env}

Bei dieser Strategie gibt es einen separaten `config`-Ordner pro Umgebung, wobei für jede Umgebung eine separate Pipeline in Cloud Manager deklariert wird.

Dieser Ansatz ist besonders dann nützlich, wenn Sie über mehrere Entwicklungsumgebungen mit jeweils eindeutigen Eigenschaftswerten verfügen.

Die Dateistruktur sieht ähnlich der folgenden aus:

```text
/config/dev1
  cdn.yaml
  logForwarding.yaml
/config/dev2
  cdn.yaml
  logForwarding.yaml
/config/prod  
  cdn.yaml
  logForwarding.yaml
```

Eine Variante dieses Ansatzes besteht darin, für jede Umgebung eine separate Verzweigung zu führen.

## Edge Delivery Services {#yamls-for-eds}

Edge Delivery-Konfigurations-Pipelines verfügen über keine separaten Entwicklungs-, Staging- und Produktionsumgebungen. In Veröffentlichungs-Bereitstellungsumgebungen schreiten Änderungen durch die Entwicklungs-, Staging- und Produktebenen voran. Eine Edge Delivery-Konfigurations-Pipeline wendet die Konfiguration dagegen direkt auf alle Domain-Zuordnungen an, die in Cloud Manager für eine Edge Delivery-Site registriert sind.


Stellen Sie daher eine einfache Dateistruktur wie die folgende bereit:

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Wenn eine Regel pro Edge Delivery-Site unterschiedlich sein muss, verwenden Sie die Syntax *wenn*, um die Regeln voneinander zu unterscheiden. Beachten Sie beispielsweise, dass die Domain im folgenden Ausschnitt mit dev.example.com übereinstimmt, was vom Domain-`www.example.com` unterschieden werden kann.

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
    # Block simple path
    - name: block-path
      when:
        allOf:
          - reqProperty: domain
            equals: "dev.example.com"
          - reqProperty: path
            equals: '/block/me'
      action: block
```

Wenn Sie das Metadatenfeld *envTypes* einschließen, sollte nur der Wert **prod** verwendet werden (das Auslassen des Metadatenfelds envTypes ist ebenfalls in Ordnung). Für die *tier* reqProperty sollte nur der Wert **publish** verwendet werden.

## Geheime Umgebungsvariablen {#secret-env-vars}

Damit vertrauliche Informationen nicht in der Verwaltung der Quelle gespeichert werden müssen, unterstützen Konfigurationsdateien Cloud Manager-Umgebungsvariablen vom Typ **secret**. Bei einigen Konfigurationen, einschließlich der Protokollweiterleitung, sind geheime Umgebungsvariablen für bestimmte Eigenschaften obligatorisch.

Beachten Sie, dass geheime Umgebungsvariablen für Veröffentlichungs-Bereitstellungsprojekte verwendet werden. Weitere Informationen finden Sie im Abschnitt Geheime Pipeline-Variablen für Edge Delivery Services-Projekte.

Das folgende Snippet ist ein Beispiel dafür, wie die geheime Umgebungsvariable `${{SPLUNK_TOKEN}}` in der Konfiguration verwendet wird.

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

Weitere Informationen zur Verwendung von Umgebungsvariablen finden Sie unter [Cloud Manager-Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md).

## Geheime Pipeline-Variablen {#secret-pipeline-vars}

Verwenden Sie für Edge Delivery Services-Projekte Cloud Manager-Pipeline-Variablen vom Typ **secret** sodass vertrauliche Informationen nicht in der Quell-Code-Verwaltung gespeichert werden müssen. Das Auswahlfeld *Schritt angewendet* sollte die Option **Bereitstellen** verwenden.

Die Syntax ist identisch mit dem im vorherigen Abschnitt gezeigten Snippet.

Weitere Informationen zur Verwendung von Pipeline-Variablen finden Sie unter [Pipeline-Variablen in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).
