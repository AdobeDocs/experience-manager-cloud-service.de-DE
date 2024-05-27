---
title: Protokollweiterleitung für AEM as a Cloud Service
description: Erfahren Sie mehr über die Weiterleitung von Protokollen an Splunk und andere Protokollierungsanbieter in AEM as a Cloud Service
source-git-commit: 13696ffde99114e5265e5c2818cb3257dd09ee8c
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 3%

---


# Protokollweiterleitung {#log-forwarding}

>[!NOTE]
>
>Diese Funktion wurde noch nicht veröffentlicht und einige Protokollierungsziele sind möglicherweise zum Zeitpunkt der Veröffentlichung nicht verfügbar. In der Zwischenzeit können Sie ein Support-Ticket öffnen, um Logs an weiterzuleiten. **Splunk**, wie im Abschnitt [Protokollierungsartikel](/help/implementing/developing/introduction/logging.md).

Kunden, die über eine Lizenz für einen Protokollierungsanbieter verfügen oder ein Protokollierungsprodukt hosten, können AEM-, Apache-/Dispatcher- und CDN-Protokolle an die zugehörigen Protokollierungsziele weiterleiten lassen. AEM as a Cloud Service unterstützt die folgenden Protokollierungsziele:

* Azure Blob Storage
* DataDog
* Elasticsearch oder OpenSearch
* HTTPS
* Splunk

Die Protokollweiterleitung wird auf Self-Service-Weise konfiguriert, indem eine Konfiguration in Git deklariert und über die Cloud Manager-Konfigurationspipeline für Entwicklungs-, Staging- und Produktionsumgebungstypen in Produktionsprogrammen (ohne Sandbox) bereitgestellt wird.

Beachten Sie, dass die Netzwerkbandbreite, die mit an das Protokollierungsziel gesendeten Protokollen verknüpft ist, als Teil der Netzwerk-I/O-Nutzung Ihres Unternehmens betrachtet wird.


## Wie dieser Artikel organisiert ist {#how-organized}

Dieser Artikel ist wie folgt organisiert:

* Einrichtung - für alle Protokollierungsziele gemeinsam
* Protokollieren von Zielkonfigurationen - jedes Ziel hat ein etwas anderes Format
* Erweiterte Netzwerke - Senden von AEM- und Apache-/Dispatcher-Logs über eine dedizierte Ausfahrt oder über eine VPN-Verbindung


## Einrichtung {#setup}

1. Erstellen Sie die folgende Ordner- und Dateistruktur im Ordner der obersten Ebene in Ihrem Projekt in Git:

   ```
   config/
        logForwarding.yaml
   ```

1. logForwarding.yaml sollte Metadaten und eine Konfiguration ähnlich dem folgenden Format enthalten (wir verwenden Splunk als Beispiel).

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

   Die **kind** auf LogForwarding festgelegt sein, sollte die Version auf die Schemaversion (1) eingestellt werden.

   Token in der Konfiguration (z. B. `${{SPLUNK_TOKEN}}`) stellen Geheimnisse dar, die nicht in Git gespeichert werden sollten. Deklarieren Sie sie stattdessen als Cloud Manager  [Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md) des Typs **secret**. Wählen Sie **Alle** als Dropdown-Wert für das Feld Dienst angewendet , sodass Protokolle an die Ebenen Autor, Veröffentlichung und Vorschau weitergeleitet werden können.

   Es ist möglich, verschiedene Werte zwischen CDN-Protokollen und allem anderen (AEM- und Apache-Logs) festzulegen, indem eine zusätzliche **cdn** und/oder **aem** -Block nach **default** -Block, in dem Eigenschaften die im **default** -Block; nur die aktivierte Eigenschaft ist erforderlich. Ein möglicher Anwendungsfall könnte die Verwendung eines anderen Splunk-Index für CDN-Protokolle sein, wie im folgenden Beispiel gezeigt wird.

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

   Ein weiteres Szenario besteht darin, die Weiterleitung der CDN-Protokolle oder alles andere (AEM- und Apache-Protokolle) zu deaktivieren. Um beispielsweise nur die CDN-Protokolle weiterzuleiten, können Sie Folgendes konfigurieren:

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

* Zulässige Dienste: Blob muss ausgewählt werden
* Zulässige Ressourcen: Objekt muss ausgewählt sein
* Zulässige Berechtigungen: Schreiben, Hinzufügen, Erstellen muss ausgewählt sein.
* Ein gültiges Start- und Ablaufdatum/-zeit.

Im Folgenden finden Sie einen Screenshot einer Beispiel-SAS-Token-Konfiguration:

![Azure Blob SAS-Token-Konfiguration](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)


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

## Erweiterte Netzwerkfunktionen {#advanced-networking}

Wenn Sie organisatorische Anforderungen haben, um den Traffic zu Ihrem Protokollierungsziel zu sperren, können Sie die Protokollweiterleitung so konfigurieren, dass [erweiterte Vernetzung](/help/security/configuring-advanced-networking.md). Sehen Sie sich die Muster für die drei folgenden erweiterten Netzwerktypen an, die eine optionale `port` -Parameter zusammen mit dem `host` -Parameter.

### Flexibler Port-Ausgang {#flex-port}

Wenn der Protokolltraffic an einen anderen Port als 443 geleitet wird (z. B. 8443 unten), konfigurieren Sie erweiterte Netzwerke wie folgt:

```
{
    "portForwards": [
        {
            "name": "mylogging.service.logger.com",
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
      host: "proxy.tunnel"
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
            "name": "mylogging.service.com",
            "portDest": 443, # something other than 443
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
      host: "proxy.tunnel"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```

### VPN {#vpn}

Wenn der Protokolltraffic einen VPN durchlaufen muss, konfigurieren Sie erweiterte Netzwerke wie folgt:

```
{
    "portForwards": [
        {
            "name": "mylogging.service.com",
            "portDest": 443, # something other than 443
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
      host: "mylogging.service.com"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```
