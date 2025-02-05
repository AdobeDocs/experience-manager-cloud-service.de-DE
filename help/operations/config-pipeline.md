---
title: Verwenden von Konfigurations-Pipelines
description: Erfahren Sie, wie Sie Konfigurations-Pipelines verwenden können, um in AEM as a Cloud Service verschiedene Konfigurationen wie Einstellungen für die Protokollweiterleitung, Bereinigungsaufgaben und verschiedene CDN-Konfigurationen bereitzustellen.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 96%

---

# Verwenden von Konfigurations-Pipelines {#config-pipelines}

Erfahren Sie, wie Sie Konfigurations-Pipelines verwenden können, um in AEM as a Cloud Service verschiedene Konfigurationen wie Einstellungen für die Protokollweiterleitung, Bereinigungsaufgaben und verschiedene CDN-Konfigurationen bereitzustellen.

## Überblick {#overview}

Eine Cloud Manager-Konfigurations-Pipeline stellt Konfigurationsdateien (die im YAML-Format erstellt wurden) in einer Zielumgebung bereit. Auf diese Weise kann eine Reihe von Funktionen in AEM as a Cloud Service konfiguriert werden, darunter die Protokollweiterleitung, Bereinigungsaufgaben sowie verschiedene CDN-Funktionen.

Konfigurations-Pipelines können über Cloud Manager für Entwicklungs-, Staging- und Produktionsumgebungstypen bereitgestellt werden. Die Konfigurationsdateien können mit dem [Befehlszeilen-Tool](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline) in schnellen Entwicklungsumgebungen (Rapid Development Environments, RDEs) bereitgestellt werden.

In den folgenden Abschnitten dieses Dokuments erhalten Sie einen Überblick über wichtige Informationen dazu, wie Konfigurations-Pipelines verwendet werden können und wie Konfigurationen für diese strukturiert sein sollten. Es werden allgemeine Konzepte beschrieben, die für alle oder eine Teilmenge der von Konfigurations-Pipelines unterstützten Funktionen freigegeben werden.

* [Unterstützte Konfigurationen](#configurations): Eine Liste von Konfigurationen, die mit Konfigurations-Pipelines bereitgestellt werden können
* [Erstellen und Verwalten von Konfigurations-Pipelines](#creating-and-managing): Erstellen einer Konfigurations-Pipeline.
* [Allgemeine Syntax](#common-syntax): Syntax, die über verschiedene Konfigurationen hinweg verwendet wird
* [Ordnerstruktur](#folder-structure): Beschreibt die für die Konfigurationen erwarteten Strukturkonfigurations-Pipelines
* [Geheime Umgebungsvariablen](#secret-env-vars): Beispiele für die Verwendung von Umgebungsvariablen, um Geheimnisse in Ihren Konfigurationen nicht offenzulegen

## Unterstützte Konfigurationen {#configurations}

Die folgende Tabelle enthält eine umfassende Liste solcher Konfigurationen mit Links zur entsprechenden Dokumentation, wo die jeweilige Konfigurationssyntax und andere Informationen beschrieben werden.

| Typ | YAML `kind`-Wert | Beschreibung |
|---|---|---|
| [Traffic-Filterregeln, einschließlich WAF](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | Deklarieren von Regeln zur Verhinderung von schädlichem Traffic |
| [Anfrageumwandlungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | Deklarieren von Regeln zur Umwandlung der Form der Traffic-Anforderung |
| [Reaktionsumwandlungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | Deklarieren von Regeln zur Umwandlung der Form für die Antwort für eine gegebene Anfrage |
| [Client-seitige Umleitungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) | `CDN` | Deklarieren von Client-seitigen Umleitungen im Stil 301/302 |
| [Ursprungs-Auswahlen](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Deklarieren von Regeln, um Traffic an verschiedene Backends zu leiten, einschließlich Adobe-fremder Anwendungen |
| [CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Überschreiben der standardmäßigen Fehlerseite, wenn der AEM-Ursprung nicht erreicht werden kann, und Referenzieren des Speicherorts des selbst-gehosteten statischen Inhalts in der Konfigurationsdatei |
| [CDN-Bereinigung](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Deklarieren der API-Bereinigungsschlüssel für die Bereinigung des CDN |
| [Kundenseitig verwaltetes CDN-HTTP-Token](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Deklarieren des Werts des X-AEM-Edge-Schlüssels, der zum Aufrufen des Adobe CDN von einem Kunden-CDN erforderlich ist |
| [Standardauthentifizierung](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Deklarieren Sie die Benutzernamen und Kennwörter für einen einfachen Authentifizierungsdialog, der bestimmte URLs schützt. |
| [Wartungsaufgabe zur Versionsbereinigung](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimieren des AEM-Repositorys durch Deklarieren von Regeln für den Zeitpunkt der Bereinigung von Inhaltsversionen |
| [Wartungsaufgabe zur Bereinigung des Auditprotokolls](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimieren des AEM-Auditprotokolls für eine verbesserte Leistung durch Deklarieren von Regeln für den Zeitpunkt der Bereinigung von Protokollen |
| [Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Konfigurieren Sie die Endpunkte und Anmeldedaten für die Weiterleitung von Protokollen an verschiedene Ziele, einschließlich Azure Blob Storage, Datadog, HTTPS, Elasticsearch, Splunk). |

## Erstellen und Verwalten von Konfigurations-Pipelines {#creating-and-managing}

Informationen zum Erstellen und Konfigurieren von Pipelines finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline).

Achten Sie beim Erstellen einer Konfigurations-Pipeline in Cloud Manager darauf, dass Sie beim Konfigurieren der Pipeline eine **zielgerichtete Bereitstellung** anstelle eines **Full-Stack-Codes** auswählen.

Wie bereits erwähnt, wird die Konfiguration für RDEs mit dem [Befehlszeilen-Tool](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline) und nicht mit einer Pipeline bereitgestellt.


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
| `kind` | Eine Zeichenfolge, die die Art der Konfiguration bestimmt, z. B. Protokollweiterleitung, Traffic-Filterregeln oder Anfrageumwandlungen. | Erforderlich, kein Standard |
| `version` | Eine Zeichenfolge, die die Schemaversion darstellt | Erforderlich, kein Standard |
| `envTypes` | Dieses Zeichenfolgen-Array ist eine untergeordnete Eigenschaft des `metadata`-Knotens. Mögliche Werte sind „Entwicklung“, „Staging“, „Produktion“ oder eine beliebige Kombination, und sie bestimmen, für welche Umgebungstypen die Konfiguration verarbeitet wird. Wenn das Array beispielsweise nur `dev` enthält, wird die Konfiguration nicht in Staging- oder Produktionsumgebungen geladen, selbst wenn die Konfiguration dort bereitgestellt wird. | Alle Umgebungstypen (Entwicklung, Staging, Produktion) |

Sie können das Dienstprogramm `yq` verwenden, um die YAML-Formatierung Ihrer Konfigurationsdatei lokal zu überprüfen (z. B. `yq cdn.yaml`).

## Ordnerstruktur {#folder-structure}

Ein Ordner mit dem Namen `/config` oder einem ähnlichen Namen sollte sich ganz oben in der Struktur befinden, wobei sich eine weitere YAML-Datei in einer Struktur darunter befindet.

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

Die Ordner- und Dateinamen unter `/config` sind beliebig. Die YAML-Datei muss jedoch einen gültigen Wert für die [`kind` enthalten](#configurations).

In der Regel werden Konfigurationen für alle Umgebungen bereitgestellt. Wenn alle Eigenschaftswerte für jede Umgebung identisch sind, reicht eine einzelne YAML-Datei aus. Es ist jedoch üblich, dass sich Eigenschaftswerte zwischen Umgebungen unterscheiden, z. B. beim Testen einer niedrigeren Umgebung.

Die folgenden Abschnitte zeigen einige Strategien zur Strukturierung Ihrer Dateien.

### Eine einzelne Konfigurationsdatei für alle Umgebungen {#single-file}

Die Dateistruktur ähnelt dem Folgenden:

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Verwenden Sie diese Struktur, wenn dieselbe Konfiguration für alle Umgebungen und für alle Konfigurationstypen (CDN, Protokollweiterleitung usw.) ausreicht. In diesem Szenario würde die `envTypes`-Array-Eigenschaft alle Umgebungstypen enthalten.

```yaml
   kind: "cdn"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

Mithilfe von Umgebungsvariablen mit geheimen Typen können die [geheimen Eigenschaften](#secret-env-vars) pro Umgebung variieren, wie durch die `${{SPLUNK_TOKEN}}`-Referenz veranschaulicht wird

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

Die Dateistruktur ähnelt dem Folgenden:

```text
/config
  cdn-dev.yaml
  cdn-stage.yaml
  cdn-prod.yaml
  logForwarding-dev.yaml
  logForwarding-stage.yaml
  logForwarding-prod.yaml
```

Verwenden Sie diese Struktur, wenn es Unterschiede bei Eigenschaftswerten geben kann. Es wäre zu erwarten, dass der `envTypes`-Array-Wert in den Dateien dem Suffix entspricht, beispielsweise
`cdn-dev.yaml` und `logForwarding-dev.yaml` mit dem Wert `["dev"]`, `cdn-stage.yaml` und `logForwarding-stage.yaml` mit dem Wert `["stage"]` usw.

### Ein Ordner pro Umgebung {#folder-per-env}

Bei dieser Strategie gibt es einen separaten `config`-Ordner pro Umgebung, wobei für jede Umgebung eine separate Pipeline in Cloud Manager deklariert wird.

Dieser Ansatz ist besonders dann nützlich, wenn Sie über mehrere Entwicklungsumgebungen mit jeweils eindeutigen Eigenschaftswerten verfügen.

Die Dateistruktur ähnelt dem Folgenden:

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

## Geheime Umgebungsvariablen {#secret-env-vars}

Damit vertrauliche Informationen nicht in der Verwaltung der Quelle gespeichert werden müssen, unterstützen Konfigurationsdateien Cloud Manager-Umgebungsvariablen vom Typ **secret**. Bei einigen Konfigurationen, einschließlich der Protokollweiterleitung, sind geheime Umgebungsvariablen für bestimmte Eigenschaften obligatorisch.

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

Bitte lesen Sie das Dokument [Cloud Manager-Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md), um zu erfahren, wie Sie Umgebungsvariablen verwenden können.
