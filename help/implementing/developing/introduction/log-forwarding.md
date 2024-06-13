---
title: Protokollweiterleitung für AEM as a Cloud Service
description: Erfahren Sie mehr über die Weiterleitung von Protokollen an Splunk und andere Protokollierungsanbieter in AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: e007f2e3713d334787446305872020367169e6a2
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 2%

---

# Protokollweiterleitung {#log-forwarding}

>[!NOTE]
>
>Diese Funktion wurde noch nicht veröffentlicht und einige Protokollierungsziele sind möglicherweise zum Zeitpunkt der Veröffentlichung nicht verfügbar. In der Zwischenzeit können Sie ein Support-Ticket öffnen, um Logs an weiterzuleiten. **Splunk**, wie im Abschnitt [Protokollierungsartikel](/help/implementing/developing/introduction/logging.md).

Kunden, die über eine Lizenz für einen Protokollierungsanbieter verfügen oder ein Protokollierungsprodukt hosten, können AEM Protokolle (einschließlich Apache/Dispatcher) und CDN-Protokolle an die zugehörigen Protokollierungsziele weiterleiten lassen. AEM as a Cloud Service unterstützt die folgenden Protokollierungsziele:

* Azure Blob Storage
* DataDog
* Elasticsearch oder OpenSearch
* HTTPS
* Splunk

Die Protokollweiterleitung wird auf Self-Service-Weise konfiguriert, indem eine Konfiguration in Git deklariert und über die Cloud Manager-Konfigurationspipeline für Entwicklungs-, Staging- und Produktionsumgebungstypen in Produktionsprogrammen (ohne Sandbox) bereitgestellt wird.

Es gibt eine Option, dass die AEM- und Apache-/Dispatcher-Protokolle über AEM erweiterte Netzwerkinfrastruktur, wie z. B. dedizierte Egress-IP, weitergeleitet werden.

Beachten Sie, dass die Netzwerkbandbreite, die mit an das Protokollierungsziel gesendeten Protokollen verknüpft ist, als Teil der Netzwerk-I/O-Nutzung Ihres Unternehmens betrachtet wird.


## Wie dieser Artikel organisiert ist {#how-organized}

Dieser Artikel ist wie folgt organisiert:

* Einrichtung - für alle Protokollierungsziele gemeinsam
* Protokollieren von Zielkonfigurationen - jedes Ziel hat ein etwas anderes Format
* Protokolleintragsformate - Informationen zu den Protokolleintragsformaten
* Erweiterte Netzwerke - Senden von AEM- und Apache-/Dispatcher-Logs über eine dedizierte Ausfahrt oder über eine VPN-Verbindung


## Einrichtung {#setup}

1. Erstellen Sie die folgende Ordner- und Dateistruktur im Ordner der obersten Ebene in Ihrem Projekt in Git:

   ```
   config/
        logForwarding.yaml
   ```

1. `logForwarding.yaml` sollte Metadaten und eine Konfiguration ähnlich dem folgenden Format enthalten (wir verwenden Splunk als Beispiel).

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

   Die **kind** -Parameter auf `LogForwarding` sollte die Version auf die Schemaversion (1) eingestellt werden.

   Token in der Konfiguration (z. B. `${{SPLUNK_TOKEN}}`) stellen Geheimnisse dar, die nicht in Git gespeichert werden sollten. Deklarieren Sie sie stattdessen als Cloud Manager  [Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md) des Typs **secret**. Wählen Sie **Alle** als Dropdown-Wert für das Feld Dienst angewendet , sodass Protokolle an die Ebenen Autor, Veröffentlichung und Vorschau weitergeleitet werden können.

   Es ist möglich, verschiedene Werte zwischen CDN-Protokollen und AEM-Protokollen (einschließlich Apache/Dispatcher) festzulegen, indem eine zusätzliche **cdn** und/oder **aem** -Block nach **default** -Block, in dem Eigenschaften die im **default** -Block; nur die aktivierte Eigenschaft ist erforderlich. Ein möglicher Anwendungsfall könnte die Verwendung eines anderen Splunk-Index für CDN-Protokolle sein, wie im folgenden Beispiel gezeigt wird.

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
          cdn:
            enabled: true
            token: "${{SPLUNK_TOKEN_CDN}}"
            index: "AEMaaCS_CDN"   
   ```

   Ein weiteres Szenario besteht darin, die Weiterleitung der CDN-Protokolle oder AEM-Protokolle (einschließlich Apache/Dispatcher) zu deaktivieren. Um beispielsweise nur die CDN-Protokolle weiterzuleiten, können Sie Folgendes konfigurieren:

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
          aem:
            enabled: false
   ```

1. Erstellen Sie für andere Umgebungstypen als RDE (derzeit nicht unterstützt) eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager.

   * [Siehe: Konfigurieren von Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).
   * [Siehe: Konfigurieren von produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

## Konfiguration des Protokollierungsziels {#logging-destinations}

Die Konfigurationen für die unterstützten Protokollierungsziele sind unten aufgeführt, zusammen mit allen spezifischen Überlegungen.

### Azure Blob Storage {#azureblob}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  azureBlob:
    default:
      enabled: true       
      storageAccountName: "example_acc"
      container: "aem_logs"
      sasToken: "${{AZURE_BLOB_SAS_TOKEN}}
      
```

Für die Authentifizierung sollte ein SAS-Token verwendet werden. Sie sollte nicht auf der Seite Freigegebener Zugriffstoken, sondern auf der Signaturseite Freigegebener Zugriff erstellt und mit den folgenden Einstellungen konfiguriert werden:

* Zulässige Dienste: Blob muss ausgewählt sein.
* Zulässige Ressourcen: Objekt muss ausgewählt sein.
* Zulässige Berechtigungen: Schreiben, Hinzufügen, Erstellen muss ausgewählt sein.
* Ein gültiges Start- und Ablaufdatum/-zeit.

Im Folgenden finden Sie einen Screenshot einer Beispiel-SAS-Token-Konfiguration:

![Azure Blob SAS-Token-Konfiguration](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)

#### Azure Blob Storage-CDN-Protokolle {#azureblob-cdn}

Jeder der global verteilten Protokollierungsserver erzeugt alle paar Sekunden eine neue Datei unter der `aemcdn` Ordner. Nach der Erstellung wird die Datei nicht mehr an angehängt. Das Format des Dateinamens ist JJJ-MM-DDThh:mm:ss.sss-uniqueid.log. z. B. 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

Beispiel:

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

Und 30 Sekunden später:

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

Jede Datei enthält mehrere JSON-Protokolleinträge, die jeweils in einer separaten Zeile stehen. Die Protokolleintragsformate werden im Abschnitt [Protokollierungsartikel](/help/implementing/developing/introduction/logging.md)und jeder Protokolleintrag enthält auch die zusätzlichen Eigenschaften, die in der Variablen [Protokolleintragsformate](#log-format) unten.

#### Azure Blob Storage-AEM {#azureblob-aem}

AEM Protokolle (einschließlich Apache/Dispatcher) werden unter einem Ordner mit der folgenden Namenskonvention angezeigt:

* aemaccess
* aemerror
* aemdispatcher
* httpdaccess
* httpderror

Unter jedem Ordner wird eine einzelne Datei erstellt und an diese angehängt. Kunden sind für die Verarbeitung und Verwaltung dieser Datei verantwortlich, sodass sie nicht zu groß wird.

Siehe Protokolleintragsformate im Abschnitt [Protokollierungsartikel](/help/implementing/developing/introduction/logging.md). Die Protokolleinträge enthalten auch die zusätzlichen Eigenschaften, die in der [Protokolleintragsformate](#log-formats) unten.


### Datadog {#datadog}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  dataDog:
    default:
      enabled: true       
      host: "http-intake.logs.datadoghq.eu"
      token: "${{DATADOG_API_KEY}}"
      
```

Zu beachten:

* Erstellen Sie einen API-Schlüssel ohne Integration mit einem bestimmten Cloud-Anbieter.


### Elasticsearch und OpenSearch {#elastic}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  elasticsearch:
    default:
      enabled: true
      host: "example.com"
      user: "${{ELASTICSEARCH_USER}}"
      password: "${{ELASTICSEARCH_PASSWORD}}"
```

Zu beachten:

* Verwenden Sie für Anmeldeinformationen nicht die Kontoanmeldeinformationen, sondern die Bereitstellungsberechtigungen. Dies sind die Anmeldeinformationen, die auf einem Bildschirm generiert werden, der diesem Bild ähneln kann:

![Elastische Bereitstellungsberechtigungen](/help/implementing/developing/introduction/assets/ec-creds.png)

### HTTPS {#https}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  https:
    default:
      url: "https://example.com/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

#### HTTPS-CDN-Protokolle {#https-cdn}

Webanfragen (POSTs) werden kontinuierlich gesendet, mit einer JSON-Payload, die ein Array von Protokolleinträgen ist, wobei das Protokolleintragsformat im Abschnitt [Protokollierungsartikel](/help/implementing/developing/introduction/logging.md#cdn-log). Weitere Eigenschaften werden im Abschnitt [Protokolleintragsformate](#log-formats) unten.

Es gibt auch eine Eigenschaft mit dem Namen `sourcetype`, der auf den Wert `aemcdn`.

>[!NOTE]
>
> Bevor der erste CDN-Protokolleintrag gesendet wird, muss Ihr HTTP-Server erfolgreich eine einmalige Anfrage ausführen: eine an den Pfad gesendete Anfrage. ``wellknownpath`` muss antworten mit ``*``.


#### HTTPS-AEM {#https-aem}

Für AEM Protokolle (einschließlich Apache/Dispatcher) werden Webanfragen (POSTs) kontinuierlich gesendet, mit einer JSON-Payload, die ein Array von Protokolleinträgen mit den verschiedenen Protokolleintragsformaten ist, wie im Abschnitt [Protokollierungsartikel](/help/implementing/developing/introduction/logging.md). Weitere Eigenschaften werden im Abschnitt [Protokolleintragsformate](#log-format) unten.

Es gibt auch eine Eigenschaft mit dem Namen `sourcetype`, der auf einen der folgenden Werte festgelegt ist:

* aemaccess
* aemerror
* aemdispatcher
* httpdaccess
* httpderror

### Splunk {#splunk}

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

<!--
### Sumo Logic {#sumologic}

   ```
   kind: "LogForwarding"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     splunk:
       default:
         enabled: true
         host: "https://collectors.de.sumologic.com"
         uri: "/receiver/v1/http"
         privateKey: "${{SomeOtherToken}}"
   
   ```   
-->

## Protokolleintragsformate {#log-formats}

Siehe Allgemein . [Protokollierungsartikel](/help/implementing/developing/introduction/logging.md) für das Format der jeweiligen Protokolltypen (CDN-Protokolle und AEM-Protokolle, einschließlich Apache/Dispatcher).

Da Protokolle aus mehreren Programmen und Umgebungen an dasselbe Protokollierungsziel weitergeleitet werden können, werden zusätzlich zur im Protokollartikel beschriebenen Ausgabe die folgenden Eigenschaften in jeden Protokolleintrag aufgenommen:

* aem_env_id
* aem_env_type
* aem_program_id
* aem_tier

Beispielsweise könnten die Eigenschaften die folgenden Werte aufweisen:

```
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
```

## Erweiterte Netzwerkfunktionen {#advanced-networking}

>[!NOTE]
>
>Diese Funktion steht noch nicht für frühe Anwender bereit.


Einige Unternehmen beschränken, welcher Traffic von den Protokollierungszielen empfangen werden kann.

Für das CDN-Protokoll können Sie die IP-Adressen auf die Zulassungsliste setzen, wie unter [diesem Artikel](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). Wenn die Liste der freigegebenen IP-Adressen zu groß ist, sollten Sie Traffic an einen (Nicht-Adobe-)Azure Blob Store senden, in den Logik geschrieben werden kann, um die Protokolle von einer dedizierten IP-Adresse an ihr endgültiges Ziel zu senden.

Für AEM Protokolle (einschließlich Apache/Dispatcher) können Sie die Protokollweiterleitung so konfigurieren, dass sie ausgeführt wird [erweiterte Vernetzung](/help/security/configuring-advanced-networking.md). Sehen Sie sich die Muster für die drei folgenden erweiterten Netzwerktypen an, die eine optionale `port` -Parameter zusammen mit dem `host` -Parameter.

### Flexibler Port-Ausgang {#flex-port}

Wenn der Protokolltraffic an einen anderen Port als 443 geleitet wird (z. B. 8443 unten), konfigurieren Sie erweiterte Netzwerke wie folgt:

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 8443, # something other than 443
            "portOrig": 30443
        }    
    ]
}
```

und konfigurieren Sie die YAML-Datei wie folgt:

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      host: "${{AEM_PROXY_HOST}}"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```

### Dedizierte Ausgangs-IP {#dedicated-egress}


Wenn der Log-Traffic aus einer dedizierten Egress-IP stammen muss, konfigurieren Sie erweiterte Netzwerke wie folgt:

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 443, 
            "portOrig": 30443
        }    
    ]
}
```

und konfigurieren Sie die YAML-Datei wie folgt:

```
      
kind: "LogForwarding"
version: "1"
   metadata:
     envTypes: ["dev"]
data:
  splunk:
     default:
       enabled: true
       index: "index_name" 
       token: "${{SPLUNK_TOKEN}}"  
     aem:
       enabled: true
       host: "${{AEM_PROXY_HOST}}"
       port: 30443       
     cdn:
       enabled: true
       host: "splunk-host.example.com"
       port: 443    
```

### VPN {#vpn}

Wenn der Protokolltraffic einen VPN durchlaufen muss, konfigurieren Sie erweiterte Netzwerke wie folgt:

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 443,
            "portOrig": 30443
        }    
    ]
}

kind: "LogForwarding"
version: "1"
   metadata:
     envTypes: ["dev"]
data:
  splunk:
     default:
       enabled: true
       index: "index_name" 
       token: "${{SPLUNK_TOKEN}}"  
     aem:
       enabled: true
       host: "${{AEM_PROXY_HOST}}"
       port: 30443       
     cdn:
       enabled: true
       host: "splunk-host.example.com"
       port: 443     
```
