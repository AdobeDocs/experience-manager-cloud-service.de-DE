---
title: Protokollweiterleitung für AEM as a Cloud Service
description: Erfahren Sie mehr über die Weiterleitung von Protokollen an Protokollierungsanbieter in AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: f6de6b6636d171b6ab08fdf432249b52c2318c45
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 2%

---

# Protokollweiterleitung {#log-forwarding}

>[!NOTE]
>
>Die Protokollweiterleitung wird jetzt im Self-Service-Modus konfiguriert, der sich von der veralteten Methode unterscheidet, die die Übermittlung eines Adobe-Support-Tickets erforderte. Siehe den Abschnitt [Migration](#legacy-migration), wenn Ihre Protokollweiterleitung per Adobe eingerichtet wurde.

Kunden mit einer -Lizenz bei einem Protokollierungsanbieter oder die ein Protokollierungsprodukt hosten, können AEM-Protokolle (einschließlich Apache/Dispatcher) und CDN-Protokolle an das zugehörige Protokollierungsziel weitergeleitet bekommen. AEM as a Cloud Service unterstützt die folgenden Protokollierungsziele:

* Azure Blob Storage
* Datadog
* Elasticsearch oder OpenSearch
* HTTPS
* Splunk

Die Protokollweiterleitung wird im Self-Service-Modus konfiguriert, indem eine Konfiguration in Git deklariert und über die Cloud Manager-Konfigurations-Pipeline für RDE-, Entwicklungs-, Staging- und Produktionsumgebungstypen in Produktionsprogrammen (ohne Sandbox) bereitgestellt wird.

Es gibt eine Option für das Routing der AEM- und Apache-/Dispatcher-Protokolle über die erweiterte AEM-Netzwerkinfrastruktur, z. B. die dedizierte Ausgangs-IP.

Beachten Sie, dass die Netzwerkbandbreite, die mit den an das Protokollierungsziel gesendeten Protokollen verbunden ist, als Teil der Netzwerk-E/A-Nutzung Ihres Unternehmens betrachtet wird.


## Wie dieser Artikel organisiert ist {#how-organized}

Dieser Artikel ist wie folgt aufgebaut:

* Setup - für alle Protokollierungsziele gleich
* Protokollieren von Zielkonfigurationen - Jedes Ziel hat ein leicht unterschiedliches Format
* Protokolleintragsformate : Informationen zu den Protokolleintragsformaten
* Erweiterte Netzwerke - Senden von AEM- und Apache/Dispatcher-Protokollen über einen dedizierten Ausgang oder ein VPN
* Migration von der alten Protokollweiterleitung - Wie wechselt man von der zuvor per Adobe eingerichteten Protokollweiterleitung zum Self-Service-Ansatz?


## Einrichtung {#setup}

1. Erstellen Sie eine Datei mit dem Namen `logForwarding.yaml`. Sie sollte Metadaten enthalten, wie im Artikel [Pipeline konfigurieren](/help/operations/config-pipeline.md#common-syntax) beschrieben (**kind** sollte auf `LogForwarding` und Version auf „1“ festgelegt sein), mit einer Konfiguration, die der folgenden ähnelt (wir verwenden Splunk als Beispiel).

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

1. Erstellen Sie für andere Umgebungstypen als RDE (die Befehlszeilen-Tools verwendet) eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager, wie in [diesem Abschnitt) ](/help/operations/config-pipeline.md#creating-and-managing). Beachten Sie, dass Full-Stack-Pipelines und Web-Stufen-Pipelines die Konfigurationsdatei nicht bereitstellen.

1. Stellen Sie die Konfiguration bereit.

Token in der Konfiguration (z. B. `${{SPLUNK_TOKEN}}`) stellen geheime Daten dar, die nicht in Git gespeichert werden sollten. Deklarieren Sie sie stattdessen als Cloud Manager [Geheime Umgebungsvariablen](/help/operations/config-pipeline.md#secret-env-vars). Wählen Sie **Alle** als Dropdown-Wert für das Feld Angewendeter Service aus, damit Protokolle an die Autoren-, Veröffentlichungs- und Vorschauebenen weitergeleitet werden können.

Es ist möglich, zwischen CDN-Protokollen und AEM-Protokollen (einschließlich Apache/Dispatcher) unterschiedliche Werte festzulegen, indem nach dem Block **default** ein zusätzlicher **cdn**- und/oder **aem**-Block eingefügt wird. Dabei können Eigenschaften die im Block **default** definierten Werte überschreiben. Nur die Eigenschaft „enabled“ ist erforderlich. Ein möglicher Anwendungsfall könnte die Verwendung eines anderen Splunk-Index für CDN-Protokolle sein, wie im folgenden Beispiel veranschaulicht.

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

Ein weiteres Szenario besteht darin, entweder die Weiterleitung der CDN-Protokolle oder der AEM-Protokolle (einschließlich Apache/Dispatcher) zu deaktivieren. Um beispielsweise nur die CDN-Protokolle weiterzuleiten, können Sie Folgendes konfigurieren:

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

## Protokollierungszielkonfiguration {#logging-destinations}

Konfigurationen für die unterstützten Protokollierungsziele sind unten aufgeführt, zusammen mit etwaigen spezifischen Überlegungen.

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

Zur Authentifizierung sollte ein SAS-Token verwendet werden. Sie sollte auf der Seite mit der Signatur für freigegebenen Zugriff und nicht auf der Seite mit dem freigegebenen Zugriffstoken erstellt und mit den folgenden Einstellungen konfiguriert werden:

* Zulässige Dienste: Blob muss ausgewählt sein.
* Zugelassene Ressourcen: Das Objekt muss ausgewählt werden.
* Zulässige Berechtigungen: Schreiben, Hinzufügen, Erstellen muss ausgewählt sein.
* Ein gültiges Start- und Ablaufdatum/-uhrzeit.

Im Folgenden finden Sie einen Screenshot einer Beispiel-SAS-Token-Konfiguration:

![Azure Blob SAS-Token-Konfiguration](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)

Wenn Protokolle nicht mehr bereitgestellt werden, nachdem sie zuvor korrekt funktioniert haben, überprüfen Sie, ob das von Ihnen konfigurierte SAS-Token weiterhin gültig ist, da es möglicherweise abgelaufen ist.

#### Azure Blob Storage-CDN-Protokolle {#azureblob-cdn}

Jeder der global verteilten Logging-Server erzeugt alle paar Sekunden eine neue Datei im `aemcdn`. Nach der Erstellung wird die Datei nicht mehr an angehängt. Das Dateinamenformat ist JJJJ-MM-DDThh:mm:ss.sss-uniqueid.log. Beispielsweise 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

Beispielsweise zu einem bestimmten Zeitpunkt:

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

Und dann 30 Sekunden später:

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

Jede Datei enthält mehrere JSON-Protokolleinträge, die sich jeweils in einer separaten Zeile befinden. Die Protokolleintragsformate werden unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) beschrieben. Jeder Protokolleintrag enthält auch die zusätzlichen Eigenschaften, die im Abschnitt [Protokolleintragsformate](#log-format) unten erwähnt werden.

#### Azure Blob Storage-AEM-Protokolle {#azureblob-aem}

AEM-Protokolle (einschließlich Apache/Dispatcher) werden unter einem Ordner mit der folgenden Namenskonvention angezeigt:

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

Unter jedem Ordner wird eine einzelne Datei erstellt und an sie angehängt. Kunden sind für die Verarbeitung und Verwaltung dieser Datei verantwortlich, damit sie nicht zu groß wird.

Weitere Informationen finden Sie in den Protokolleintragsformaten unter &quot;[ für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md). Die Protokolleinträge enthalten auch die zusätzlichen Eigenschaften, die im Abschnitt [Protokolleintragsformate](#log-formats) unten erwähnt werden.


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

Überlegungen:

* Erstellen Sie einen API-Schlüssel ohne Integration mit einem bestimmten Cloud-Anbieter.
* Die Tag-Eigenschaft ist optional
* Bei AEM-Protokollen wird das Datadog-Quell-Tag auf eines der folgenden festgelegt: `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` oder `aemhttpderror`
* Bei CDN-Protokollen wird das Datadog-Quell-Tag auf `aemcdn` gesetzt
* Das Datadog-Service-Tag ist auf `adobeaemcloud` festgelegt, kann jedoch im Tags-Abschnitt überschrieben werden
* Wenn Ihre Aufnahme-Pipeline Datadog-Tags verwendet, um den entsprechenden Index für Weiterleitungsprotokolle zu ermitteln, stellen Sie sicher, dass diese Tags in der YAML-Datei für die Protokollweiterleitung korrekt konfiguriert sind. Fehlende Tags können eine erfolgreiche Protokollaufnahme verhindern, wenn die Pipeline von ihnen abhängig ist.



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

Überlegungen:

* Standardmäßig ist der Port 443. Optional kann sie mit einer Eigenschaft namens `port` überschrieben werden
* Verwenden Sie für die Anmeldeinformationen Bereitstellungs-Anmeldeinformationen und keine Konto-Anmeldeinformationen. Dies sind die Anmeldeinformationen, die auf einem Bildschirm generiert werden, der diesem Bild ähneln kann:

![Elastic-Bereitstellungsanmeldeinformationen](/help/implementing/developing/introduction/assets/ec-creds.png)

* Für AEM-Protokolle ist `index` auf eines der folgenden festgelegt: `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` oder `aemhttpderror`
* Die optionale Pipeline-Eigenschaft sollte auf den Namen der Elasticsearch- oder OpenSearch-Aufnahme-Pipeline festgelegt werden, die so konfiguriert werden kann, dass der Protokolleintrag an den entsprechenden Index weitergeleitet wird. Der Prozessortyp der Pipeline muss auf &quot;*&quot;* und die Skriptsprache sollte auf &quot;*&quot;*. Hier finden Sie ein Beispielskript-Snippet zum Routen von Protokolleinträgen in einen Index wie aemaccess_dev_26_06_2024:

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

Überlegungen:

* Die URL-Zeichenfolge muss **https://** enthalten. Andernfalls schlägt die Validierung fehl.
* Die URL kann einen Port enthalten. Beispiel: `https://example.com:8443/aem_logs/aem`. Wenn in der URL-Zeichenfolge kein Port enthalten ist, wird Port 443 (der standardmäßige HTTPS-Port) angenommen.

#### HTTPS-CDN-Protokolle {#https-cdn}

Web-Anfragen (POSTs) werden kontinuierlich mit einer JSON-Payload gesendet, die ein Array von Protokolleinträgen ist, wobei das unter „Protokollierung für AEM as a Cloud Service[ beschriebene Protokolleintragsformat verwendet ](/help/implementing/developing/introduction/logging.md#cdn-log). Weitere Eigenschaften werden im Abschnitt [Protokolleintragsformate](#log-formats) unten beschrieben.

Es gibt auch eine Eigenschaft mit dem Namen `sourcetype`, für die der Wert `aemcdn` festgelegt ist.

>[!NOTE]
>
> Bevor der erste CDN-Protokolleintrag gesendet wird, muss Ihr HTTP-Server eine einmalige Anfrage erfolgreich abschließen: Eine Anfrage, die an den Pfad gesendet wird, muss ``/.well-known/fastly/logging/challenge`` mit einem Sternchen ``*`` im Hauptteil und 200-Status-Code antworten.

#### HTTPS-AEM-Protokolle {#https-aem}

Bei AEM-Protokollen (einschließlich Apache/Dispatcher) werden Web-Anfragen (POSTs) kontinuierlich mit einer JSON-Payload gesendet, die ein Array von Protokolleinträgen mit den verschiedenen Protokolleintragsformaten ist, wie unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) beschrieben. Weitere Eigenschaften werden im Abschnitt [Protokolleintragsformate](#log-format) unten beschrieben.

Es gibt auch eine Eigenschaft mit dem Namen `Source-Type`, die auf einen der folgenden Werte eingestellt ist:

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

Überlegungen:

* Standardmäßig ist der Port 443. Optional kann sie mit einer Eigenschaft namens `port` überschrieben werden.
* Das Feld „sourceType“ hat abhängig vom spezifischen Protokoll einen der folgenden Werte: *aemaccess*, *aemerror*,
  *aemrequest*, *aemdispatcher*, *aemhttpdaccess*, *aemhttpderror*, *aemcdn*
* Wenn die erforderlichen IPs auf die Zulassungsliste gesetzt wurden und die Protokolle immer noch nicht bereitgestellt werden, stellen Sie sicher, dass es keine Firewall-Regeln gibt, die die Splunk-Token-Validierung erzwingen. Fastly führt einen anfänglichen Validierungsschritt durch, bei dem absichtlich ein ungültiges Splunk-Token gesendet wird. Wenn Ihre Firewall so eingestellt ist, dass Verbindungen mit ungültigen Splunk-Token beendet werden, schlägt der Validierungsprozess fehl, was Fastly daran hindert, Protokolle an Ihre Splunk-Instanz zu senden.


>[!NOTE]
>
> [Bei der Migration](#legacy-migration) von der alten Protokollweiterleitung zu diesem Self-Service-Modell haben sich die Werte des `sourcetype`-Felds, die an Ihren Splunk-Index gesendet werden, möglicherweise geändert. Passen Sie sie daher entsprechend an.


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

Unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) finden Sie das Format der jeweiligen Protokolltypen (CDN-Protokolle und AEM-Protokolle einschließlich Apache/Dispatcher).

Da Protokolle aus mehreren Programmen und Umgebungen an dasselbe Protokollierungsziel weitergeleitet werden können, werden zusätzlich zu der im Protokollierungsartikel beschriebenen Ausgabe die folgenden Eigenschaften in jedem Protokolleintrag enthalten:

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

Einige Organisationen entscheiden sich dafür, den Traffic einzuschränken, der von den Protokollierungszielen empfangen werden kann.

Für das CDN-Protokoll können Sie die IP-Adressen auf die Zulassungsliste setzen, wie unter [Fastly-Dokumentation - Öffentliche IP-Liste](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/) beschrieben. Wenn diese Liste freigegebener IP-Adressen zu groß ist, sollten Sie Traffic an einen HTTPS-Server oder (Nicht-Adobe) Azure Blob Store senden, wo Logiken geschrieben werden können, um die Protokolle von einer bekannten IP an ihr endgültiges Ziel zu senden.

Für AEM-Protokolle (einschließlich Apache/Dispatcher) können Sie, wenn Sie [erweiterte Vernetzung](/help/security/configuring-advanced-networking.md) konfiguriert haben, die Eigenschaft „advancedNetworking“ verwenden, um sie von einer dedizierten Ausgangs-IP-Adresse oder über ein VPN weiterzuleiten.

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

## Migration von der alten Protokollweiterleitung {#legacy-migration}

Bevor die Konfiguration der Protokollweiterleitung über ein Self-Service-Modell durchgeführt wurde, wurden Kunden aufgefordert, Support-Tickets zu öffnen, bei denen Adobe die Integration initiieren würde.

Kunden, die auf diese Weise durch Adobe eingerichtet wurden, sind willkommen, sich nach Belieben an das Self-Service-Modell anzupassen. Es gibt mehrere Gründe für diesen Übergang:

* Eine neue Umgebung (z. B. eine neue Entwicklungsumgebung oder RDE) wurde bereitgestellt.
* Änderungen an Ihrem vorhandenen Splunk-Endpunkt oder Ihren Anmeldedaten.
* Adobe hatte die Protokollweiterleitung eingerichtet, bevor CDN-Protokolle verfügbar waren, und Sie möchten CDN-Protokolle erhalten.
* Eine bewusste Entscheidung, sich proaktiv an das Self-Service-Modell anzupassen, damit Ihr Unternehmen über das Wissen verfügt, noch bevor eine zeitkritische Änderung erforderlich ist.

Wenn Sie zur Migration bereit sind, konfigurieren Sie einfach die YAML-Datei wie in den vorherigen Abschnitten beschrieben. Verwenden Sie die Cloud Manager-Konfigurations-Pipeline, um sie in jeder Umgebung bereitzustellen, in der die Konfiguration angewendet werden soll.

Es wird empfohlen, aber nicht erforderlich, dass eine Konfiguration in allen Umgebungen bereitgestellt wird, sodass sie alle unter Selbstbedienungssteuerung stehen. Andernfalls können Sie vergessen, welche Umgebungen per Adobe konfiguriert wurden, anstatt diejenigen, die eigenständig konfiguriert wurden.

>[!NOTE]
>
>Die Werte des `sourcetype`, die an Ihren Splunk-Index gesendet werden, haben sich möglicherweise geändert. Passen Sie sie daher entsprechend an.

>[!NOTE]
>
>Wenn die Protokollweiterleitung in einer Umgebung bereitgestellt wird, die zuvor vom Adobe-Support konfiguriert wurde, erhalten Sie möglicherweise doppelte Protokolle für bis zu einige Stunden. Dies wird sich schließlich automatisch auflösen.

