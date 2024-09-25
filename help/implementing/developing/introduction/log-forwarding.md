---
title: Protokollweiterleitung für AEM as a Cloud Service
description: Erfahren Sie mehr über die Weiterleitung von Protokollen an Splunk und andere Protokollierungsanbieter in AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 17d195f18055ebd3a1c4a8dfe1f9f6bc35ebaf37
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 3%

---

# Protokollweiterleitung {#log-forwarding}

>[!NOTE]
>
>Diese Funktion wurde noch nicht veröffentlicht und einige Protokollierungsziele sind möglicherweise zum Zeitpunkt der Veröffentlichung nicht verfügbar. In der Zwischenzeit können Sie ein Support-Ticket öffnen, um Protokolle an **Splunk** weiterzuleiten, wie unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) beschrieben.

Kunden, die über eine Lizenz für einen Protokollierungsanbieter verfügen oder ein Protokollierungsprodukt hosten, können AEM Protokolle (einschließlich Apache/Dispatcher) und CDN-Protokolle an die zugehörigen Protokollierungsziele weiterleiten lassen. AEM as a Cloud Service unterstützt die folgenden Protokollierungsziele:

* Azure Blob Storage
* DataDog
* Elasticsearch oder OpenSearch
* HTTPS
* Splunk

Die Protokollweiterleitung wird auf Self-Service-Weise konfiguriert, indem eine Konfiguration in Git deklariert und über die Cloud Manager-Konfigurationspipeline für Entwicklungs-, Staging- und Produktionsumgebungstypen in Produktionsprogrammen (ohne Sandbox) bereitgestellt wird.

Es gibt eine Option, mit der die AEM- und Apache/Dispatcher-Protokolle über AEM erweiterte Netzwerkinfrastruktur, wie z. B. dedizierte Egress-IP, weitergeleitet werden können.

Beachten Sie, dass die Netzwerkbandbreite, die mit an das Protokollierungsziel gesendeten Protokollen verknüpft ist, als Teil der Netzwerk-I/O-Nutzung Ihres Unternehmens betrachtet wird.


## Wie dieser Artikel organisiert ist {#how-organized}

Dieser Artikel ist wie folgt organisiert:

* Einrichtung - für alle Protokollierungsziele gemeinsam
* Protokollieren von Zielkonfigurationen - jedes Ziel hat ein etwas anderes Format
* Protokolleintragsformate - Informationen zu den Protokolleintragsformaten
* Erweiterte Netzwerke - Senden von AEM- und Apache/Dispatcher-Logs über eine dedizierte Ausfahrt oder über eine VPN-Verbindung


## Einrichtung {#setup}

1. Erstellen Sie eine Datei mit dem Namen `logForwarding.yaml`. Sie sollte Metadaten enthalten, wie im [Konfigurations-Pipeline-Artikel](/help/operations/config-pipeline.md#common-syntax) beschrieben (**kind** sollte auf `LogForwarding` und Version auf &quot;1&quot; gesetzt werden), mit einer Konfiguration ähnlich der folgenden (wir verwenden Splunk als Beispiel).

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

1. Platzieren Sie die Datei unter einem Ordner der obersten Ebene mit dem Namen *config* oder ähnlich, wie in [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) beschrieben.

1. Erstellen Sie für andere Umgebungstypen als RDE (die derzeit nicht unterstützt wird) eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager, auf die in [diesem Abschnitt](/help/operations/config-pipeline.md#creating-and-managing) verwiesen wird. Beachten Sie, dass die Konfigurationsdatei nicht über Vollstack-Pipelines und Web-Tier-Pipelines bereitgestellt wird.

1. Stellen Sie die Konfiguration bereit.

Token in der Konfiguration (z. B. `${{SPLUNK_TOKEN}}`) stellen Geheimnisse dar, die nicht in Git gespeichert werden sollten. Deklarieren Sie sie stattdessen als Cloud Manager [Secret Environment Variables](/help/operations/config-pipeline.md#secret-env-vars). Stellen Sie sicher, dass Sie &quot;**Alle**&quot;als Dropdown-Wert für das Feld &quot;Dienst angewendet&quot;auswählen, damit Protokolle an die Ebenen &quot;Autor&quot;, &quot;Veröffentlichen&quot;und &quot;Vorschau&quot;weitergeleitet werden können.

Es ist möglich, verschiedene Werte zwischen CDN-Protokollen und AEM-Protokollen (einschließlich Apache/Dispatcher) festzulegen, indem ein zusätzlicher Block **cdn** und/oder **aem** nach dem Block **default** eingefügt wird, in dem Eigenschaften die im Block **default** definierten überschreiben können. Es ist nur die aktivierte Eigenschaft erforderlich. Ein möglicher Anwendungsfall könnte die Verwendung eines anderen Splunk-Index für CDN-Protokolle sein, wie im folgenden Beispiel gezeigt wird.

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

Jeder der global verteilten Protokollierungsserver erzeugt alle paar Sekunden eine neue Datei im Ordner &quot;`aemcdn`&quot;. Nach der Erstellung wird die Datei nicht mehr an angehängt. Das Format des Dateinamens ist YYY-MM-DDThh:mm:s.sss-uniqueid.log. Beispiel: 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

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

Jede Datei enthält mehrere JSON-Protokolleinträge, die jeweils in einer separaten Zeile stehen. Die Protokolleintragsformate werden unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) beschrieben und jeder Protokolleintrag enthält auch die zusätzlichen Eigenschaften, die im Abschnitt [Protokolleintragsformate](#log-format) unten erwähnt werden.

#### Azure Blob Storage-AEM {#azureblob-aem}

AEM Protokolle (einschließlich Apache/Dispatcher) werden unter einem Ordner mit der folgenden Namenskonvention angezeigt:

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

Unter jedem Ordner wird eine einzelne Datei erstellt und an diese angehängt. Kunden sind für die Verarbeitung und Verwaltung dieser Datei verantwortlich, sodass sie nicht zu groß wird.

Siehe Protokolleintragsformate unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md). Die Protokolleinträge enthalten auch die zusätzlichen Eigenschaften, die im Abschnitt [Protokolleintragsformate](#log-formats) unten erwähnt werden.


### Datadog {#datadog}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  datadog:
    default:
      enabled: true       
      host: "http-intake.logs.datadoghq.eu"
      token: "${{DATADOG_API_KEY}}"
      tags:
         tag1: value1
         tag2: value2
      
```

Zu beachten:

* Erstellen Sie einen API-Schlüssel ohne Integration mit einem bestimmten Cloud-Anbieter.
* Die Eigenschaft &quot;tags&quot;ist optional.
* Für AEM Protokolle wird das Quell-Tag des Datadog auf einen der Werte `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` oder `aemhttpderror` festgelegt
* Für CDN-Protokolle ist das Quell-Tag &quot;Datadog&quot;auf `aemcdn` gesetzt.
* Das Tag des Datadog-Dienstes ist auf `adobeaemcloud` gesetzt, Sie können es jedoch im Abschnitt &quot;Tags&quot;überschreiben.


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
      pipeline: "ingest pipeline name"
```

Zu beachten:

* Standardmäßig ist der Port 443. Optional kann sie mit einer Eigenschaft mit dem Namen `port` überschrieben werden.
* Verwenden Sie für Anmeldeinformationen nicht die Kontoanmeldeinformationen, sondern die Bereitstellungsberechtigungen. Dies sind die Anmeldeinformationen, die auf einem Bildschirm generiert werden, der diesem Bild ähneln kann:

![Elastic deployment credentials](/help/implementing/developing/introduction/assets/ec-creds.png)

* Für AEM Protokolle ist `index` auf einen der Werte `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` oder `aemhttpderror` festgelegt.
* Die optionale Pipeline-Eigenschaft sollte auf den Namen der Elasticsearch- oder OpenSearch-Erfassungspipeline festgelegt werden, die so konfiguriert werden kann, dass der Protokolleintrag an den entsprechenden Index weitergeleitet wird. Der Prozessortyp der Pipeline muss auf *script* und die Skriptsprache auf *schmerless* eingestellt sein. Im Folgenden finden Sie ein Beispielskript-Snippet zum Weiterleiten von Protokolleinträgen in einen Index wie aemaccess_dev_26_06_2024:

```
def envType = ctx.aem_env_type != null ? ctx.aem_env_type : 'unknown';
def sourceType = ctx._index;
def date = new SimpleDateFormat('dd_MM_yyyy').format(new Date());
ctx._index = sourceType + "_" + envType + "_" + date;
```

### HTTPS {#https}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  https:
    default:
      enabled: true
      url: "https://example.com/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

Zu beachten:

* Die URL-Zeichenfolge muss **https://** enthalten. Andernfalls schlägt die Überprüfung fehl.
* Die URL kann einen Port enthalten. Beispiel: `https://example.com:8443/aem_logs/aem`. Wenn in der URL-Zeichenfolge kein Port enthalten ist, wird Port 443 (der standardmäßige HTTPS-Port) angenommen.

#### HTTPS-CDN-Protokolle {#https-cdn}

Webanfragen (POSTs) werden kontinuierlich gesendet, mit einer JSON-Payload, die ein Array von Protokolleinträgen ist, wobei das Protokolleintragsformat unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md#cdn-log) beschrieben wird. Weitere Eigenschaften werden im Abschnitt [Protokolleintragsformate](#log-formats) unten erwähnt.

Es gibt auch eine Eigenschaft mit dem Namen `sourcetype`, die auf den Wert `aemcdn` festgelegt ist.

>[!NOTE]
>
> Bevor der erste CDN-Protokolleintrag gesendet wird, muss Ihr HTTP-Server eine einmalige Aufgabe erfolgreich durchführen: Eine an den Pfad ``/.well-known/fastly/logging/challenge`` gesendete Anfrage muss mit einem Sternchen ``*`` im Hauptteil und 200 Statuscode antworten.

#### HTTPS-AEM {#https-aem}

Für AEM Protokolle (einschließlich Apache/Dispatcher) werden Webanfragen (POSTs) kontinuierlich gesendet, mit einer JSON-Payload, die ein Array von Protokolleinträgen ist, mit den verschiedenen Protokolleintragsformaten, wie unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) beschrieben. Weitere Eigenschaften werden im Abschnitt [Protokolleintragsformate](#log-format) unten erwähnt.

Es gibt auch eine Eigenschaft mit dem Namen `Source-Type`, die auf einen der folgenden Werte festgelegt ist:

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

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
      index: "aemaacs"
```

Zu beachten:

* Standardmäßig ist der Port 443. Optional kann sie mit einer Eigenschaft mit dem Namen `port` überschrieben werden.


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

Unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) finden Sie das Format der einzelnen Protokolltypen (CDN-Protokolle und AEM-Protokolle einschließlich Apache/Dispatcher).

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

Einige Unternehmen beschränken, welcher Traffic von den Protokollierungszielen empfangen werden kann.

Für das CDN-Protokoll können Sie die IP-Adressen auf die Zulassungsliste setzen, wie in der [Schnelldokumentation - Öffentliche IP-Liste](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/) beschrieben. Wenn die Liste der freigegebenen IP-Adressen zu groß ist, sollten Sie Traffic an einen HTTPS-Server oder (Nicht-Adobe) Azure Blob Store senden, wo Logik geschrieben werden kann, um die Protokolle von einer bekannten IP an ihr ultimatives Ziel zu senden.

Für AEM Protokolle (einschließlich Apache/Dispatcher) können Sie, wenn Sie [erweiterte Netzwerke](/help/security/configuring-advanced-networking.md) konfiguriert haben, die Eigenschaft advancedNetworking verwenden, um sie von einer dedizierten Ausgangs-IP-Adresse oder über einen VPN weiterzuleiten.

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
      port: 443
      token: "${{SPLUNK_TOKEN}}"
      index: "aemaacs"
    aem:
      advancedNetworking: true
```

