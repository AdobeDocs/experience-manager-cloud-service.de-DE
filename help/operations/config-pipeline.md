---
title: Verwenden von Config Pipelines
description: Erfahren Sie, wie Sie Konfigurationspipelines verwenden können, um verschiedene Konfigurationen wie Einstellungen für die Protokollweiterleitung, Bereinigungsaufgaben und verschiedene CDN-Konfigurationen bereitzustellen.
feature: Operations
role: Admin
source-git-commit: 3a10a0b8c89581d97af1a3c69f1236382aa85db0
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 1%

---


# Verwenden von Config Pipelines {#config-pipelines}

Erfahren Sie, wie Sie Konfigurationspipelines verwenden können, um verschiedene Konfigurationen wie Einstellungen für die Protokollweiterleitung, Bereinigungsaufgaben und verschiedene CDN-Konfigurationen bereitzustellen.

## Überblick {#overview}

Eine Cloud Manager-Konfigurationspipeline stellt Konfigurationsdateien (die im YAML-Format erstellt wurden) in einer Zielumgebung bereit. Eine Reihe von Funktionen in AEM as a Cloud Service können auf diese Weise konfiguriert werden, darunter die Protokollweiterleitung, Bereinigungsaufgaben sowie verschiedene CDN-Funktionen.

Config Pipelines können über Cloud Manager für Entwicklungs-, Staging- und Produktionsumgebungstypen in Produktionsprogrammen (ohne Sandbox) bereitgestellt werden. RDE werden nicht unterstützt.

In den folgenden Abschnitten dieses Dokuments erhalten Sie einen Überblick über wichtige Informationen dazu, wie Config Pipelines verwendet werden können und wie Konfigurationen für sie strukturiert sein sollten. Es werden allgemeine Konzepte beschrieben, die für alle oder eine Untergruppe der von Konfigurations-Pipelines unterstützten Funktionen freigegeben werden.

* [Unterstützte Konfigurationen](#configurations) - Eine Liste von Konfigurationen, die mit Konfigurationspipelines bereitgestellt werden können
* [Erstellen und Verwalten von Konfigurations-Pipelines](#creating-and-managing) - Erstellen einer Konfigurations-Pipeline.
* [Allgemeine Syntax](#common-syntax) - Syntax, die über verschiedene Konfigurationen hinweg freigegeben wurde
* [Ordnerstruktur](#folder-structure) - Beschreibt die für die Konfigurationen erwarteten Strukturkonfigurations-Pipelines
* [Geheime Umgebungsvariablen](#secret-env-vars) - Beispiele für die Verwendung von Umgebungsvariablen, um Geheimnisse in Ihren Konfigurationen nicht anzuzeigen

## Unterstützte Konfigurationen {#configurations}

Die folgende Tabelle enthält eine umfassende Liste solcher Konfigurationen mit Links zur entsprechenden Dokumentation, die die jeweilige Konfigurationssyntax und andere Informationen beschreibt.

| Typ | YAML `kind`-Wert | Beschreibung |
|---|---|---|
| [Traffic-Filterregeln, einschließlich WAF](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | Regeln deklarieren, um schädlichen Traffic zu verhindern |
| [Anforderungsumwandlungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | Regeln deklarieren , um die Form der Traffic-Anforderung umzuwandeln |
| [Antwortumwandlungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | Regeln deklarieren , um die Form der Antwort für eine bestimmte Anforderung zu transformieren |
| [Client-seitige Umleitungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) | `CDN` | Clientseitige Umleitungen im Stil 301/302 deklarieren [ (nur für frühe Benutzer verfügbar)](/help/release-notes/release-notes-cloud/release-notes-current.md#foundation-early-adopter) |
| [Origin Selectors](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Regeln deklarieren, um Traffic an verschiedene Backends zu leiten, einschließlich Nicht-Adobe-Anwendungen |
| [CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Überschreiben Sie die standardmäßige Fehlerseite, wenn AEM Ursprung nicht erreicht werden kann. Referenzieren Sie den Speicherort des selbstgehosteten statischen Inhalts in der Konfigurationsdatei. |
| [CDN-Bereinigung](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Deklarieren Sie die API-Schlüssel für die Bereinigung des CDN |
| [Vom Kunden verwaltetes CDN-HTTP-Token](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Deklarieren Sie den Wert des X-AEM-Edge-Schlüssels, der erforderlich ist, um das Adobe CDN von einem Kunden-CDN aufzurufen |
| [Standardauthentifizierung](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Deklarieren Sie die Benutzernamen und Kennwörter für ein einfaches Authentifizierungsdialogfeld, das bestimmte URLs schützt [ (nur für frühe Benutzer verfügbar)](/help/release-notes/release-notes-cloud/release-notes-current.md#foundation-early-adopter) |
| [Wartungsaufgabe zur Versionsbereinigung](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimieren Sie das AEM-Repository, indem Sie Regeln dafür deklarieren, wann Inhaltsversionen gelöscht werden sollen. |
| [Wartungsaufgabe zur Bereinigung des Auditprotokolls](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimieren Sie das AEM Auditprotokoll für eine höhere Leistung, indem Sie Regeln dafür deklarieren, wann Protokolle bereinigt werden sollen. |
| [Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Noch nicht verfügbar - Konfigurieren Sie die Endpunkte und Anmeldedaten für die Weiterleitung von Protokollen an verschiedene Ziele (z. B. Splunk, Datadog, HTTPS). |

## Erstellen und Verwalten von Config Pipelines {#creating-and-managing}

Informationen zum Erstellen und Konfigurieren von Pipelines finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline) .

Stellen Sie beim Erstellen einer Config Pipeline in Cloud Manager sicher, dass Sie beim Konfigurieren der Pipeline eine &quot;**Targeted Deployment**&quot; anstelle von &quot;**Full Stack Code**&quot;auswählen.

## Allgemeine Syntax {#common-syntax}

Jede Konfigurationsdatei beginnt mit Eigenschaften, die dem folgenden Beispielausschnitt ähneln:

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
```

| Eigenschaft | Beschreibung | Standard |
|---|---|---|
| `kind` | Eine Zeichenfolge, die bestimmt, welche Art von Konfiguration, z. B. Protokollweiterleitung, Traffic-Filterregeln oder Anforderungstransformationen, | Erforderlich, kein Standardwert |
| `version` | Eine Zeichenfolge, die die Schemaversion darstellt | Erforderlich, kein Standardwert |
| `envTypes` | Dieses Zeichenfolgen-Array ist eine untergeordnete Eigenschaft des Knotens `metadata` . Mögliche Werte sind &quot;dev&quot;, &quot;stage&quot;, &quot;prod&quot;oder eine beliebige Kombination, und sie bestimmen, für welche Umgebungstypen die Konfiguration verarbeitet wird. Wenn das Array beispielsweise nur `dev` enthält, wird die Konfiguration nicht in Staging- oder Produktionsumgebungen geladen, selbst wenn die Konfiguration dort bereitgestellt wird. | Alle Umgebungstypen (dev, stage, prod) |

Sie können das Dienstprogramm `yq` verwenden, um die YAML-Formatierung Ihrer Konfigurationsdatei lokal zu überprüfen (z. B. `yq cdn.yaml`).

## Ordnerstruktur {#folder-structure}

Ein Ordner mit dem Namen `/config` oder ein ähnliches sollte sich oben im Baum befinden, wobei sich eine weitere YAML-Datei in einem Baum darunter befindet.

Zum Beispiel:

```text
/config
  cdn.yaml
```

oder

```text
/config
  /dev
    cdn.yaml
```

Die Ordnernamen und Dateinamen unter `/config` sind beliebig. Die YAML-Datei muss jedoch einen gültigen [`kind` -Eigenschaftswert enthalten.](#configurations)

In der Regel werden Konfigurationen für alle Umgebungen bereitgestellt. Wenn alle Eigenschaftswerte für jede Umgebung identisch sind, reicht eine einzelne YAML-Datei aus. Es ist jedoch üblich, dass sich Eigenschaftswerte zwischen Umgebungen unterscheiden, z. B. beim Testen einer niedrigeren Umgebung.

Die folgenden Abschnitte zeigen einige Strategien zur Strukturierung Ihrer Dateien.

### Eine einzelne Konfigurationsdatei für alle Umgebungen {#single-file}

Die Dateistruktur sieht wie folgt aus:

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Verwenden Sie diese Struktur, wenn dieselbe Konfiguration für alle Umgebungen und für alle Konfigurationstypen (CDN, Protokollweiterleitung usw.) ausreicht. In diesem Szenario würde die `envTypes` -Array-Eigenschaft alle Umgebungstypen enthalten.

```yaml
   kind: "cdn"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

Mithilfe von Umgebungsvariablen mit geheimen Typen können die [geheimen Eigenschaften](#secret-env-vars) pro Umgebung variieren, wie durch die `${{SPLUNK_TOKEN}}` -Referenz veranschaulicht wird.

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

### Separate Datei pro Umgebungstyp {#file-per-env}

Die Dateistruktur sieht wie folgt aus:

```text
/config
  cdn-dev.yaml
  cdn-stage.yaml
  cdn-prod.yaml
  logForwarding-dev.yaml
  logForwarding-stage.yaml
  logForwarding-prod.yaml
```

Verwenden Sie diese Struktur, wenn es Unterschiede bei Eigenschaftswerten geben kann. In den Dateien würde erwartet, dass der `envTypes` -Array-Wert dem Suffix entspricht, beispielsweise
`cdn-dev.yaml` und `logForwarding-dev.yaml` mit dem Wert `["dev"]`, `cdn-stage.yaml` und `logForwarding-stage.yaml` mit dem Wert `["stage"]` usw.

### Ordner pro Umgebung {#folder-per-env}

Bei dieser Strategie gibt es einen separaten Ordner `config` pro Umgebung, wobei für jede Umgebung eine separate Pipeline in Cloud Manager deklariert wird.

Dieser Ansatz ist besonders nützlich, wenn Sie über mehrere Entwicklungsumgebungen verfügen, in denen jede über eindeutige Eigenschaftswerte verfügt.

Die Dateistruktur sieht wie folgt aus:

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

Eine Variante dieses Ansatzes besteht darin, für jede Umgebung einen separaten Zweig zu verwalten.

## Geheime Umgebungsvariablen {#secret-env-vars}

Damit vertrauliche Informationen nicht in der Quell-Code-Verwaltung gespeichert werden müssen, unterstützen Konfigurationsdateien Cloud Manager-Umgebungsvariablen vom Typ **secret**. Bei einigen Konfigurationen, einschließlich der Protokollweiterleitung, sind geheime Umgebungsvariablen für bestimmte Eigenschaften obligatorisch.

Der folgende Ausschnitt zeigt, wie die geheime Umgebungsvariable `${{SPLUNK_TOKEN}}` in der Konfiguration verwendet wird.

```
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

Weitere Informationen zur Verwendung von Umgebungsvariablen finden Sie im Dokument [Cloud Manager-Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md) .
