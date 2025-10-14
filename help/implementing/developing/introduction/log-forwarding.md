---
title: Protokollweiterleitung für AEM as a Cloud Service
description: Erfahren Sie mehr über die Weiterleitung von Protokollen an Protokollierungsanbieter in AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: afa88d89b24ac425ba1b69ee9062e589d49ebee9
workflow-type: tm+mt
source-wordcount: '2478'
ht-degree: 95%

---

# Protokollweiterleitung {#log-forwarding}

>[!NOTE]
>
>Die Protokollweiterleitung wird jetzt als Self-Service konfiguriert, was sich von der veralteten Methode unterscheidet, für die ein Adobe-Support-Ticket gesendet werden musste. Wenn Ihre Protokollweiterleitung von Adobe eingerichtet wurde, lesen Sie den Abschnitt [Migrieren](#legacy-migration).

Kundinnen und Kunden, die eine Lizenz bei einem Protokollierungsanbieter besitzen oder ein Protokollierungsprodukt hosten, können AEM-Protokolle (einschließlich Apache/Dispatcher) und CDN-Protokolle an das zugehörige Protokollierungsziel weiterleiten lassen. AEM as a Cloud Service unterstützt die folgenden Protokollierungsziele:

<table>
  <tbody>
    <tr>
      <th>Protokolltechnologie</th>
      <th>AEM</th>
      <th>Dispatcher</th>
      <th>CDN</th>
    </tr>
    <tr>
      <td>Amazon S3</td>
      <td>Ja</td>
      <td>Ja</td>
      <td style="background-color: #ffb3b3;">Future</td>
    </tr>
    <tr>
      <td>Azure Blob Storage</td>
      <td>Ja</td>
      <td>Ja</td>
      <td>Ja</td>
    </tr>
    <tr>
      <td>DataDog</td>
      <td>Ja</td>
      <td>Ja</td>
      <td>Ja</td>
    </tr>
    <tr>
      <td>Dynatrace</td>
      <td>Ja</td>
      <td>Ja</td>
      <td style="background-color: #ffb3b3;">Future</td>
    </tr>
    <tr>
      <td>ElasticSearch<br>OpenSearch</td>
      <td>Ja</td>
      <td>Ja</td>
      <td>Ja</td>
    </tr>
    <tr>
      <td>HTTPS</td>
      <td>Ja</td>
      <td>Ja</td>
      <td>Ja</td>
    </tr>
    <tr>
      <td>New Relic</td>
      <td>Ja</td>
      <td>Ja</td>
      <td style="background-color: #ffb3b3;">Future</td>
    </tr>
    <tr>
      <td>Splunk</td>
      <td>Ja</td>
      <td>Ja</td>
      <td>Ja</td>
    </tr>
    <tr>
      <td>Sumo Logic</td>
      <td>Ja</td>
      <td>Ja</td>
      <td style="background-color: #ffb3b3;">Future</td>
    </tr>
  </tbody>
</table>

>[!NOTE]
>
> Für geplante künftige CDN-Protokolltechnologien senden Sie eine E-Mail an [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com), um Interesse zu bekunden.

Die Protokollweiterleitung wird im Self-Service-Modus konfiguriert, indem eine Konfiguration in Git deklariert wird, und kann über Cloud Manager-Konfigurations-Pipelines für Entwicklungs-, Staging- und Produktionsumgebungstypen bereitgestellt werden. Die Konfigurationsdatei kann mithilfe von Befehlszeilenprogrammen in schnellen Entwicklungsumgebungen (Rapid Development Environments, RDEs) bereitgestellt werden.

Es gibt eine Option für die Weiterleitung der AEM- und Apache/Dispatcher-Protokolle über die erweiterte Netzwerkinfrastruktur von AEM, z. B. eine dedizierte Egress-IP.

Die Netzwerkbandbreite, die mit an Splunk gesendeten Protokollen verknüpft ist, wird als Teil der kundenseitigen Netzwerk-E/A-Nutzung betrachtet.

## Wie dieser Artikel organisiert ist {#how-organized}

Dieser Artikel ist wie folgt aufgebaut:

* Setup – für alle Protokollierungsziele gleich
* Transport und erweiterte Netzwerkfunktionen – Vor der Erstellung der Protokollierungskonfiguration muss das Netzwerk-Setup berücksichtigt werden.
* Konfigurationen von Protokollierungszielen – Jedes Ziel hat ein leicht unterschiedliches Format
* Protokolleintragsformate – Informationen zu den Protokolleintragsformaten
* Migrieren von der alten Protokollweiterleitung – So wechseln Sie von der zuvor von Adobe eingerichteten Protokollweiterleitung zum Self-Service-Ansatz

## Setup {#setup}

1. Erstellen Sie eine Datei mit dem Namen `logForwarding.yaml`. Sie sollte Metadaten enthalten, wie im Artikel [Konfigurations-Pipeline](/help/operations/config-pipeline.md#common-syntax) beschrieben (**kind** sollte auf `LogForwarding` und „version“ auf „1“ gesetzt werden). Die Konfiguration sollte dann ähnlich wie die folgende aussehen (wir verwenden Splunk als Beispiel).

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

1. Platzieren Sie die Datei unter einem Ordner der obersten Ebene mit dem Namen *config* oder ähnlich, wie in [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) beschrieben.

1. Erstellen Sie für andere Umgebungstypen als RDE (der Befehlszeilen-Tools verwendet) eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager, wie in [diesem Abschnitt](/help/operations/config-pipeline.md#creating-and-managing) beschrieben. Beachten Sie, dass Full-Stack-Pipelines und Web-Stufen-Pipelines die Konfigurationsdatei nicht implementieren.

1. Implementieren Sie die Konfiguration.

Token in der Konfiguration (z. B. `${{SPLUNK_TOKEN}}`) stellen geheime Daten dar, die nicht in Git gespeichert werden sollten. Deklarieren Sie sie stattdessen als [Geheime Umgebungsvariablen](/help/operations/config-pipeline.md#secret-env-vars) von Cloud Manager. Wählen Sie **Alle** als Dropdown-Wert für das Feld „Angewendeter Service“ aus, damit Protokolle an die Autoren-, Veröffentlichungs- und Vorschauebenen weitergeleitet werden können.

Es ist möglich, für CDN-Protokolle und AEM-Protokolle (einschließlich Apache/Dispatcher) unterschiedliche Werte festzulegen, indem nach dem Block **default** ein zusätzlicher Block **cdn** und/oder **aem** eingefügt wird. Dabei können Eigenschaften die im Block **default** definierten Werte überschreiben. Nur die Eigenschaft „enabled“ ist erforderlich. Ein möglicher Anwendungsfall könnte die Verwendung eines abweichenden Splunk-Index für CDN-Protokolle sein, wie im folgenden Beispiel veranschaulicht.

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
       cdn:
         enabled: true
         token: "${{SPLUNK_TOKEN_CDN}}"
         index: "AEMaaCS_CDN"   
```

Ein weiteres Szenario besteht darin, die Weiterleitung der CDN-Protokolle oder AEM-Protokolle (einschließlich Apache/Dispatcher) zu deaktivieren. Um beispielsweise nur die CDN-Protokolle weiterzuleiten, können Sie Folgendes konfigurieren:

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
       aem:
         enabled: false
```

## Transport und erweiterte Netzwerkfunktionen {#transport-advancednetworking}

Einige Organisationen möchten einschränken, welcher Traffic von den Protokollierungszielen empfangen werden kann. Andere benötigen möglicherweise andere Ports als HTTPS (443).  In diesem Fall  müssen vor der Implementierung der Protokollweiterleitungskonfiguration [Erweiterte Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) konfiguriert werden.

In der folgenden Tabelle sehen Sie, welche Anforderungen an die erweiterte Netzwerk- und Protokollierungskonfiguration gestellt werden, je nachdem, ob Sie Port 443 verwenden oder nicht und ob Ihre Protokolle über eine feste IP-Adresse angezeigt werden müssen oder nicht.

<table>
  <tbody>
    <tr>
      <th>Ziel-Port</th>
      <th>Sollen Protokolle über eine feste IP-Adresse angezeigt werden?</th>
      <th>Überlegungen zu erweiterten Netzwerkfunktionen</th>
      <th>Port-Definition für logForwarding.yaml erforderlich</th>
    </tr>
    <tr>
      <td rowspan="2" ro>HTTPS (443)</td>
      <td>Nein</td>
      <td>Nein</td>
      <td>Nein</td>
    </tr>
    <tr>
      <td>Ja</td>
      <td>Ja, <a href="/help/security/configuring-advanced-networking.md#dedicated-egress-ip-address-dedicated-egress-ip-address">dedizierter Egress</a></td>
      <td>Nein</td>
    <tr>
    <tr>
      <td rowspan="2">Nicht standardmäßiger Port (z. B. 8088)</td>
      <td>Nein</td>
      <td>Ja, <a href="/help/security/configuring-advanced-networking.md#flexible-port-egress-flexible-port-egress">flexibler Egress</a></td>
      <td>Ja</td>
    </tr>
    <tr>
      <td>Ja</td>
      <td>Ja, <a href="/help/security/configuring-advanced-networking.md#dedicated-egress-ip-address-dedicated-egress-ip-address">dedizierter Egress</a></td>
      <td>Ja</td>
  </tbody>
</table>

>[!NOTE]
>Ob Ihre Protokolle von einer einzelnen IP-Adresse aus angezeigt werden, hängt von der gewählten erweiterten Netzwerkkonfiguration ab.  Um dies zu erleichtern, muss ein dedizierter Egress verwendet werden.
>
> Die erweiterte Netzwerkkonfiguration ist ein [zweistufiger Prozess](/help/security/configuring-advanced-networking.md#configuring-and-enabling-advanced-networking-configuring-enabling), der eine Aktivierung auf Programm- und Umgebungsebene erfordert.

Wenn Sie [Erweiterte Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) konfiguriert haben, können Sie für AEM-Protokolle (einschließlich Apache/Dispatcher) die `aem.advancedNetworking`-Eigenschaft verwenden, um sie von einer dedizierten Egress-IP-Adresse oder über ein VPN weiterzuleiten.

Das folgende Beispiel zeigt, wie die Protokollierung an einem Standard-HTTPS-Port mit erweiterten Netzwerkfunktionen konfiguriert wird.

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
      port: 443
      token: "${{SPLUNK_TOKEN}}"
      index: "aemaacs"
    aem:
      advancedNetworking: true
```

Für CDN-Protokolle können Sie die IP-Adressen auf die Zulassungsliste setzen, wie unter [Fastly-Dokumentation – Öffentliche IP-Liste](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/) beschrieben. Wenn diese Liste der freigegebenen IP-Adressen zu groß ist, sollten Sie Traffic an einen HTTPS-Server oder Azure Blob Store (außer Adobe) senden, in den Logik erstellt werden kann, mit der die Protokolle von einer bekannten IP an ihr endgültiges Ziel gesendet werden.

>[!NOTE]
>
>Es ist nicht möglich, dass CDN-Protokolle von derselben IP-Adresse aus angezeigt werden, von der Ihre AEM-Protokolle stammen, da Protokolle direkt von Fastly und nicht von AEM Cloud Service gesendet werden.
>
>Aus diesem Grund ist es nicht möglich, die Protokollweiterleitung mit erweiterten Netzwerk-VPN-Konfigurationen zu verwenden.

## Konfiguration des Protokollierungsziels {#logging-destinations}

Im Folgenden sind die Konfigurationen sowie ggf. spezifische Überlegungen für die unterstützten Protokollierungsziele aufgeführt.

### Amazon S3 {#amazons3}

Die Protokollweiterleitung an Amazon S3 unterstützt AEM- und Dispatcher-Protokolle. CDN-Protokolle werden noch nicht unterstützt.

>[!NOTE]
>
>In S3 werden regelmäßig alle 10 Minuten für jeden Protokolldateityp Protokolle geschrieben.  Dies kann zu einer anfänglichen Verzögerung für das Schreiben von Protokollen in S3 führen, sobald die Funktion aktiviert/deaktiviert wird.  [Weitere Informationen zu diesem Verhalten](https://docs.fluentbit.io/manual/pipeline/outputs/s3#differences-between-s3-and-other-fluent-bit-outputs).

```yaml
kind: "LogForwarding"
version: "1.0"
metadata:
  envTypes: ["dev"]
data:
  awsS3:
    default:
      enabled: true
      region: "your-bucket-region"
      bucket: "your_bucket_name"
      accessKey: "${{AWS_S3_ACCESS_KEY}}"
      secretAccessKey: "${{AWS_S3_SECRET_ACCESS_KEY}}"
```

Um die S3-Protokollweiterleitung zu verwenden, müssen Sie einen AWS IAM-Benutzenden mit der entsprechenden Richtlinie für den Zugriff auf Ihren S3-Bucket vorkonfigurieren.  Wie Sie IAM-Benutzeranmeldeinformationen erstellen, erfahren Sie in der [AWS IAM-Benutzerdokumentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html).

Die IAM-Richtlinie sollte dem Benutzenden die Verwendung von `s3:putObject` ermöglichen.  Beispiel:

```json
 {
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": [
            "s3:PutObject"
        ],
        "Resource": "arn:aws:s3:::your_bucket_name/*"
    }]
}
```

Weitere Informationen zur Implementierung finden Sie in der [Dokumentation zur AWS-Bucket-Richtlinie](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html).

>[!NOTE]
>CDN-Protokollunterstützung für AWS S3 ist für die Zukunft geplant. Bitte senden Sie eine E-Mail an {0[aemcs-logforwarding-beta@adobe.com), um Interesse zu registrieren.](mailto:aemcs-logforwarding-beta@adobe.com)

### Azure Blob Storage {#azureblob}

```yaml
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

Zur Authentifizierung sollte ein SAS-Token verwendet werden. Erstellen Sie das Token auf der Seite „Shared Access Signature“ und nicht auf der Seite „Shared Access Token“. Verwenden Sie die folgenden Einstellungen für die Konfiguration:

* Zugelassene Dienste: „Blob“ muss ausgewählt sein.
* Zugelassene Ressourcen: „Objekt“ muss ausgewählt sein.
* Zugelassene Berechtigungen: „Schreiben“, „Hinzufügen“, „Erstellen“ müssen ausgewählt sein.
* Gültiges Start- und Ablaufdatum mit Uhrzeit.

Im Folgenden finden Sie einen Screenshot einer Beispiel-SAS-Token-Konfiguration:

![Azure Blob SAS-Token-Konfiguration](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)

Wenn Protokolle nicht mehr bereitgestellt werden, nachdem sie zuvor korrekt funktioniert haben, überprüfen Sie, ob das von Ihnen konfigurierte SAS-Token weiterhin gültig ist, da es möglicherweise abgelaufen ist.

#### Azure Blob Storage-CDN-Protokolle {#azureblob-cdn}

Jeder der global verteilten Protokollierungs-Server erzeugt alle paar Sekunden eine neue Datei im Ordner `aemcdn`. Nach der Erstellung wird nichts mehr an die Datei angehängt. Das Dateinamenformat ist JJJJ-MM-DDThh:mm:ss.sss-uniqueid.log. Beispielsweise 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

Beispielsweise zu einem bestimmten Zeitpunkt:

```text
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

Und dann 30 Sekunden später:

```text
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

Jede Datei enthält mehrere JSON-Protokolleinträge, die sich jeweils in einer separaten Zeile befinden. Die Protokolleintragsformate werden unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) beschrieben. Jeder Protokolleintrag enthält auch die zusätzlichen Eigenschaften, die im Abschnitt [Protokolleintragsformate](#log-formats) unten erwähnt werden.

#### Azure Blob Storage-AEM-Protokolle {#azureblob-aem}

AEM-Protokolle (einschließlich Apache/Dispatcher) werden unter einem Ordner mit der folgenden Namenskonvention angezeigt:

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

Unter jedem Ordner wird eine einzelne Datei erstellt, an die angehängt wird. Kundinnen und Kunden sind für die Verarbeitung und Verwaltung dieser Datei verantwortlich, damit sie nicht zu groß wird.

Weitere Informationen finden Sie in den Protokolleintragsformaten unter [Protolkollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md). Die Protokolleinträge enthalten auch die zusätzlichen Eigenschaften, die im Abschnitt [Protokolleintragsformate](#log-formats) unten erwähnt werden.

### Datadog {#datadog}

```yaml
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

#### Überlegungen

* Erstellen Sie einen API-Schlüssel ohne Integration mit einem bestimmten Cloud-Anbieter.
* Die Eigenschaft „tags“ ist optional
* Bei AEM-Protokollen wird das Datadog-Quell-Tag auf eines der folgenden festgelegt: `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` oder `aemhttpderror`
* Bei CDN-Protokollen wird das Datadog-Quell-Tag auf `aemcdn` gesetzt
* Das Datadog-Service-Tag ist auf `adobeaemcloud` festgelegt, kann jedoch im Tags-Abschnitt überschrieben werden
* Wenn Ihre Aufnahme-Pipeline Datadog-Tags verwendet, um den entsprechenden Index für Weiterleitungsprotokolle zu ermitteln, stellen Sie sicher, dass diese Tags in der YAML-Datei für die Protokollweiterleitung korrekt konfiguriert sind. Fehlende Tags können eine erfolgreiche Protokollaufnahme verhindern, wenn die Pipeline von ihnen abhängig ist.

### Elasticsearch und OpenSearch {#elastic}

```yaml
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

#### Überlegungen

* Der standardmäßige Port ist 443. Optional kann er mit einer Eigenschaft namens `port` überschrieben werden.
* Verwenden Sie als Anmeldeinformationen Implementierungs-Anmeldeinformationen und keine Konto-Anmeldeinformationen. Dies sind die Anmeldeinformationen, die auf einem Bildschirm ähnlich dem folgenden generiert werden:

![Implementierungs-Anmeldeinformationen für Elastic](/help/implementing/developing/introduction/assets/ec-creds.png)

* Für AEM-Protokolle ist `index` auf einen der Werte `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` oder `aemhttpderror` festgelegt.
* Die optionale Pipeline-Eigenschaft sollte auf den Namen der Elasticsearch- oder OpenSearch-Aufnahme-Pipeline festgelegt werden, die so konfiguriert werden kann, dass der Protokolleintrag an den entsprechenden Index weitergeleitet wird. Der Prozessortyp der Pipeline muss auf *script* und die Skriptsprache auf *painless* eingestellt werden. Hier finden Sie ein Beispielskript-Snippet zur Weiterleitung von Protokolleinträgen in einen Index wie aemaccess_dev_26_06_2024:

```text
def envType = ctx.aem_env_type != null ? ctx.aem_env_type : 'unknown';
def sourceType = ctx._index;
def date = new SimpleDateFormat('dd_MM_yyyy').format(new Date());
ctx._index = sourceType + "_" + envType + "_" + date;
```

### HTTPS {#https}

```yaml
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

#### Überlegungen

* Die URL-Zeichenfolge muss **https://** enthalten. Andernfalls schlägt die Validierung fehl.
* Die URL kann einen Port enthalten. Beispiel: `https://example.com:8443/aem_logs/aem`. Wenn in der URL-Zeichenfolge kein Port enthalten ist, wird Port 443 (der standardmäßige HTTPS-Port) angenommen.

#### HTTPS-CDN-Protokolle {#https-cdn}

Web-Anfragen (POSTs) werden kontinuierlich mit einer JSON-Payload gesendet, die ein Array von Protokolleinträgen ist, wobei das unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md#cdn-log) beschriebene Protokolleintragsformat verwendet wird. Weitere Eigenschaften werden im Abschnitt [Protokolleintragsformate](#log-formats) unten beschrieben.

Es gibt auch eine Eigenschaft mit dem Namen `sourcetype`, für die der Wert `aemcdn` festgelegt ist.

>[!NOTE]
>
> Bevor der erste CDN-Protokolleintrag gesendet wird, muss Ihr HTTP-Server eine einmalige Anfrage erfolgreich abschließen: Eine Anfrage, die an den Pfad gesendet wird, muss ``/.well-known/fastly/logging/challenge`` mit einem Sternchen ``*`` im Hauptteil und dem Status-Code 200 antworten.

#### HTTPS-AEM-Protokolle {#https-aem}

Bei AEM-Protokollen (einschließlich Apache/Dispatcher) werden Web-Anfragen (POSTs) kontinuierlich mit einer JSON-Payload gesendet, die ein Array von Protokolleinträgen mit den verschiedenen Protokolleintragsformaten ist, wie unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) beschrieben. Weitere Eigenschaften werden im Abschnitt [Protokolleintragsformate](#log-formats) unten beschrieben.

Es gibt auch eine Eigenschaft mit dem Namen `Source-Type`, die auf einen der folgenden Werte eingestellt ist:

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

### New Relic-Protokoll-API {#newrelic-https}

Die Protokollweiterleitung an New Relic nutzt die New Relic-HTTPS-API für die Aufnahme.  Derzeit werden nur Protokolle von AEM und Dispatcher unterstützt. CDN-Protokolle werden noch nicht unterstützt.

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
  data:
    newRelic:
      default:
        enabled: true
        uri: "https://log-api.newrelic.com/log/v1"
        apiKey: "${{NR_API_KEY}}"
```

>[!NOTE]
>
>Die Protokollweiterleitung an New Relic ist nur für kundeneigene New Relic-Konten verfügbar.
>
>Die Unterstützung des CDN-Protokolls für die New Relic-Protokoll-API ist für die Zukunft geplant. Bitte senden Sie eine E-Mail an {0[aemcs-logforwarding-beta@adobe.com), um Interesse zu registrieren.](mailto:aemcs-logforwarding-beta@adobe.com)
>
>New Relic bietet regionsspezifische Endpunkte, je nachdem, wo Ihr New Relic-Konto bereitgestellt wird.  Weitere Informationen finden Sie in der [New Relic-Dokumentation](https://docs.newrelic.com/docs/logs/log-api/introduction-log-api/#endpoint).

### Dynatrace-Protokoll-API {#dynatrace-https}

Die Protokollweiterleitung an Dynatrace nutzt die Dynatrace-HTTPS-API für die Aufnahme.  Derzeit werden nur Protokolle von AEM und Dispatcher unterstützt. CDN-Protokolle werden noch nicht unterstützt.

Das Umfangsattribut „Ingest Logs“ ist für das Token erforderlich.

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
  data:
    dynatrace:
      default:
        enabled: true
        environmentId: "${{DYNATRACE_ENVID}}"
        token: "${{DYNATRACE_TOKEN}}"  
```

>[!NOTE]
>Die Unterstützung des CDN-Protokolls für die Dynatrace-Protokoll-API ist für die Zukunft geplant. Bitte senden Sie eine E-Mail an {0[aemcs-logforwarding-beta@adobe.com), um Interesse zu registrieren.](mailto:aemcs-logforwarding-beta@adobe.com)

### Splunk {#splunk}

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
      index: "aemaacs"
```

#### Überlegungen

* Der standardmäßige Port ist 443. Optional kann er mit einer Eigenschaft namens `port` überschrieben werden.
* Das Feld „sourceType“ hat abhängig vom spezifischen Protokoll einen der folgenden Werte: *aemaccess*, *aemerror*,
  *aemrequest*, *aemdispatcher*, *aemhttpdaccess*, *aemhttpderror*, *aemcdn*.
* Wenn die erforderlichen IPs auf die Zulassungsliste gesetzt wurden und die Protokolle immer noch nicht bereitgestellt werden, stellen Sie sicher, dass keine Firewall-Regeln aktiv sind, die die Splunk-Token-Validierung erzwingen. Fastly führt einen anfänglichen Validierungsschritt durch, bei dem absichtlich ein ungültiges Splunk-Token gesendet wird. Wenn Ihre Firewall so eingestellt ist, dass Verbindungen mit ungültigen Splunk-Token beendet werden, schlägt der Validierungsprozess fehl, was Fastly daran hindert, Protokolle an Ihre Splunk-Instanz zu senden.

>[!NOTE]
>
> [Bei der Migration](#legacy-migration) von der alten Protokollweiterleitung zu diesem Self-Service-Modell haben sich die Werte des Felds `sourcetype`, die an Ihren Splunk-Index gesendet werden, möglicherweise geändert. Passen Sie sie daher entsprechend an.

### Sumo Logic {#sumologic}

Die Protokollweiterleitung an Sumo Logic unterstützt AEM- und Dispatcher-Protokolle; CDN-Protokolle werden noch nicht unterstützt.

Bei der Konfiguration der Sumo-Logik für die Datenaufnahme erhalten Sie eine „HTTP Source Address“, die den Host, den Receiver-URI und den privaten Schlüssel in einer einzigen Zeichenfolge bereitstellt.  Beispiel:

`https://collectors.de.sumologic.com/receiver/v1/http/ZaVnC...`

Sie müssen den letzten Abschnitt der URL (ohne den vorhergehenden `/`) kopieren und als [Cloud Manager-Geheimnis-Umgebungsvariable](/help/operations/config-pipeline.md#secret-env-vars) hinzufügen, wie oben im Abschnitt [Setup](#setup) beschrieben, und dann in Ihrer Konfiguration auf diese Variable verweisen.  Ein Beispiel wird unten angezeigt.

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  sumoLogic:
    default:
      enabled: true
      collectorURL: "https://collectors.de.sumologic.com/receiver/v1/http"
      privateKey: "${{SUMOLOGIC_PRIVATE_KEY}}"
      index: "aem-logs"
```

>[!NOTE]
>CDN Log-Unterstützung für SumoLogic ist für die Zukunft geplant. Bitte senden Sie eine E-Mail an {0[aemcs-logforwarding-beta@adobe.com), um Interesse zu registrieren.](mailto:aemcs-logforwarding-beta@adobe.com)
>
> Sie benötigen ein Sumo Logic Enterprise-Abonnement, um die Indexfeldfunktion nutzen zu können.  Bei Nicht-Enterprise-Abonnements werden die Protokolle standardmäßig an die `sumologic_default`-Partition weitergeleitet.  Weitere Informationen finden Sie in der [Dokumentation zur Sumo Logic-Partitionierung](https://help.sumologic.com/docs/search/optimize-search-partitions/).

## Protokolleintragsformate {#log-formats}

Unter [Protokollierung für AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) finden Sie das Format der jeweiligen Protokolltypen (CDN-Protokolle und AEM-Protokolle, einschließlich Apache/Dispatcher).

Da Protokolle aus mehreren Programmen und Umgebungen an dasselbe Protokollierungsziel weitergeleitet werden können, sind zusätzlich zum im Protokollierungsartikel beschriebenen Output die folgenden Eigenschaften in jedem Protokolleintrag enthalten:

* aem_env_id
* aem_env_type
* aem_program_id
* aem_tier

Beispielsweise könnten die Eigenschaften die folgenden Werte aufweisen:

```text
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
```

## Migration von der alten Protokollweiterleitung {#legacy-migration}

Bevor die Konfiguration der Protokollweiterleitung über ein Self-Service-Modell erfolgte, wurden Kundinnen und Kunden aufgefordert, Support-Tickets zu öffnen, damit Adobe die Integration initiierte.

Kundinnen und Kunden, deren Setup von Adobe auf diese Weise erstellt wurde, können jederzeit zum Self-Service-Modell wechseln. Es gibt mehrere Gründe für diesen Umstieg:

* Eine neue Umgebung (z. B. eine neue Entwicklungsumgebung oder RDE) wurde bereitgestellt.
* Änderungen an Ihrem vorhandenen Splunk-Endpunkt oder Ihren Anmeldedaten.
* Adobe hatte die Protokollweiterleitung eingerichtet, bevor CDN-Protokolle verfügbar waren, und Sie möchten CDN-Protokolle erhalten.
* Eine bewusste Entscheidung, proaktiv das Self-Service-Modell zu übernehmen, damit Ihr Unternehmen über das Wissen verfügt, noch bevor eine zeitkritische Änderung erforderlich ist.

Wenn Sie zur Migration bereit sind, konfigurieren Sie einfach die YAML-Datei wie in den vorherigen Abschnitten beschrieben. Verwenden Sie die Cloud Manager-Konfigurations-Pipeline, um sie in jeder Umgebung zu implementieren, in der die Konfiguration angewendet werden soll.

Es wird empfohlen, ist aber nicht erforderlich, dass eine Konfiguration in allen Umgebungen implementiert wird, damit sie alle per Self-Service gesteuert werden. Anderenfalls könnten Sie vielleicht vergessen, welche Umgebungen von Adobe und welche Umgebungen eigenständig konfiguriert wurden.

>[!NOTE]
>
>Die Werte des Felds `sourcetype`, die an Ihren Splunk-Index gesendet werden, haben sich möglicherweise geändert. Passen Sie sie daher entsprechend an.
>
>Wenn die Protokollweiterleitung in einer Umgebung implementiert wird, die zuvor vom Adobe-Support konfiguriert wurde, erhalten Sie möglicherweise einige Stunden lang doppelte Protokolle. Dies wird jedoch nach kurzer Zeit automatisch aufhören.
