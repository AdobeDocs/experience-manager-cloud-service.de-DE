---
title: Aktualisieren Ihrer Inhaltsfragmente für UUID-Referenzen
description: Erfahren Sie, wie Sie Ihre Inhaltsfragmente für optimierte UUID-Referenzen in Adobe Experience Manager as a Cloud Service zur Bereitstellung von Headless-Inhalten aktualisieren.
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
exl-id: 004d1340-8e3a-4e9a-82dc-fa013cea45a7
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 99%

---

# Aktualisieren Ihrer Inhaltsfragmente für UUID-Referenzen {#upgrade-content-fragments-for-UUID-references}

Um die Stabilität Ihrer GraphQL-Filter zu optimieren, können Sie die Inhalts- und Fragmentreferenzen in Ihren Inhaltsfragmenten so aktualisieren, dass sie Universally Unique Identifiers (UUIDs) verwenden.

Ursprünglich wurden bei Inhaltsfragmentmodellen die Datentypen **Inhaltsreferenz** und **Fragmentreferenz** bereitgestellt. Beide Referenzen verweisen mithilfe eines Pfads auf die referenzierte Ressource. Dieser Pfad kann veraltet sein, wenn die Ressource verschoben wurde. Obwohl solche Referenzen in den meisten Fällen mehr als ausreichend sind, wurden die Inhaltsfragmentmodelle erweitert, um auch Referenzen auf Grundlage einer UUID bereitzustellen:

* **Inhaltsreferenz (UUID)**
* **Fragmentreferenz (UUID)**.

Diese neuen Referenztypen können sowohl in neuen Inhaltsfragmentmodellen und Inhaltsfragmenten als auch zur Erweiterung vorhandener Instanzen verwendet werden.

Um vorhandene Inhaltsfragmente und Inhaltsfragmentmodelle zu aktualisieren, können Sie das hier beschriebene Verfahren durchführen.

>[!CAUTION]
>
>Vor der Aktualisierung sollten Sie immer [einen Probelauf ausführen](#execute-a-dry-run), um etwaige Probleme im Zusammenhang mit Ihrem Inhalt zu ermitteln.

## Was aktualisiert wird {#what-is-upgraded}

Die folgenden Aktualisierungen werden durchgeführt:

* Felder der Datentypen:
   * **Inhaltsreferenz** wird in **Inhaltsreferenz (UUID)** umgewandelt.
   * **Fragmentreferenz** wird in **Fragmentreferenz (UUID)** umgewandelt.
* Die Werte der pfadbasierten Referenzen in diesen Feldern werden durch die entsprechenden UUIDs ersetzt.

>[!NOTE]
>
>Nach der Aktualisierung sind beide Datentypen weiterhin im Inhaltsfragmentmodelleditor verfügbar. Sie können neue Felder basierend auf beiden Typen erstellen (es wird jedoch die Verwendung der UUID-basierten Typen erwartet) und die Aktualisierung bei Bedarf erneut durchführen.

## Was NICHT aktualisiert wird {#what-is-not-upgraded}

Die folgenden Verweise (Referenzen) werden nicht aktualisiert:

* Seitenverweise – UUIDs werden noch nicht unterstützt.
* Alle ungültigen Referenzen, z. B. wenn das Ziel des Inhaltsfragment- oder Asset-Pfads nicht vorhanden ist.

   * Ungültige Referenzen werden nicht aktualisiert, wenn der Inhaltsfragmentpfad oder der Asset-Pfad ungültig ist und so keine entsprechende UUID zugewiesen werden kann. Die ursprüngliche Referenz bleibt hiervon unberührt.

   * Führen Sie einen [Probelauf](#execute-a-dry-run) durch, um ungültige Referenzen zu erkennen.

  >[!NOTE]
  >
  >Wenn sie ungültig sind, können sie unabhängig von der Aktualisierung nicht verwendet werden.

## Wann nicht aktualisiert werden sollte {#when-you-should-not-upgrade}

Es sollte nicht aktualisiert werden:

* wenn eines Ihrer Inhaltsfragmente Seitenverweise verwendet, da UUIDs für Seitenverweise noch nicht unterstützt werden.

## Einschränkungen bei UUID-Referenzen {#limitations-of-uuid-references}

Derzeit gelten die folgenden Einschränkungen beim Verwenden von Referenzen, die auf einer UUID basieren:

* Modelle

   * Neue Inhaltsfragmentmodelle mit Inhaltsfragment-UUID- oder Inhaltsreferenz-UUID-Feldern können nicht über die OpenAPI erstellt werden.
   * Das Feld `id` für Modelle wurde nicht dahingehend geändert, dass es UUID-basiert ist. Es verwendet den dekodierten base64-Pfad des Modells. Modelle können nicht verschoben werden. Daher ist dieser Wert weiterhin stabil.

* Assets

   * Beim Erstellen eines Inhaltsfragments über die OpenAPI müssen die Feldtypen `fragment-reference` oder `content-reference` verwendet werden, um Verweise auf ein Fragment bzw. ein Asset anzugeben. Dies gilt selbst dann, wenn der Wert eines UUID-basierten Referenzfelds festgelegt wird.

## Aktualisierungsplanung {#upgrade-planning}

Es gibt einige vorbereitende Schritte, bevor Sie Ihre Aktualisierung ausführen.

### Ausführen eines Probelaufs {#execute-a-dry-run}

Es wird empfohlen, bei *jeder* Aktualisierung Ihres Inhalts zunächst einen Probelauf durchzuführen. Dadurch werden Protokolldateien mit Einträgen erstellt, die auf potenzielle Probleme hinweisen:

* Ungültige Verweise
* Seitenverweise

Führen Sie die Inhaltsaktualisierung im Modus `dryRun` aus, um:

* ungültige Referenzen zu identifizieren, indem Sie sie in den Protokolldateien auflisten.
Sie können diese Referenzen dann vor der eigentlichen Inhaltsaktualisierung korrigieren.
* alle Seitenverweise zu identifizieren, indem sie sie in den Protokolldateien auflisten.
Wenn Seitenverweise erkannt werden, sollten Sie [die Inhaltsaktualisierung nicht ausführen](#when-you-should-not-upgrade).


### Erzwingen des Einfrierens von Inhalten {#enforce-a-content-freeze}

Inhalte sollten aktualisiert werden, wenn sie eingefroren sind.

Wie lange Inhalte eingefroren sind, hängt von der Menge der Inhaltsfragmente ab, die aktualisiert werden. Dementsprechend kann die Aktualisierung zwischen einigen Minuten und einigen Stunden dauern und richtet sich auch nach den Parametern, die beim Starten der Inhaltsaktualisierung verwendet werden.

## Ausführen der Inhaltsaktualisierung {#running-the-content-upgrade}

Die Inhaltsaktualisierung kann mithilfe des Endpunkts `/libs/dam/cfm/maintenance.json` gesteuert werden.

>[!NOTE]
>
>Für den Zugriff auf den Endpunkt benötigt Ihr Konto die Rolle `Administrator`.

### Starten der Inhaltsaktualisierung {#start-a-content-upgrade}

| Endpunkt | HTTP-Anfragetyp | Kommentar |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **Anfrageparameter** | **Wert** | |
| action | `start` | |
| serviceTypeId | `uuidUpgradeService` | Die Diensttyp-ID (vordefinierter, fester Wert). |
|  segmentSize | `1000` | Die Anzahl der Inhaltsfragmente oder Modelle, die in einem Segment (Batch) aktualisiert werden. |
| basePath | `/conf` | Geben Sie Folgendes an:<ul><li>den Stamm `/conf`, um alle AEM-Konfigurationen zu aktualisieren, ODER</li><li>einen ausgewählten AEM-Konfigurationspfad, für den die Inhaltsaktualisierung ausgeführt wird.<br>Beispiel: `/conf/wknd-shared` aktualisiert nur den einzelnen Mandanten `wknd-shared`.</li></ul> |
| interval | `10` | Das Intervall in Sekunden, nach dem das nächste Segment von Inhaltsfragmenten oder Modellen aktualisiert wird. |
| mode | `replicate`, `noReplicate` | <ul><li>`replicate`: Repliziert den gleichen Auftrag in allen AEM-Veröffentlichungsinstanzen.</li><li>`noReplicate`: Führt den Auftrag nur in AEM-Autoreninstanzen aus.</li></ul> |
| dryRun |  `true`, `false` | <ul><li>`false`: Simuliert die Inhaltsaktualisierung, ohne Inhaltsänderungen zu speichern.</li><li>`true`: Führt die Inhaltsaktualisierung durch und speichert Inhaltsänderungen.</li></ul> |
| **Antwortdetails** | **Wert** | |
| jobId | `UUID` |  Die ID des Auftrags, der die Inhaltsaktualisierung ausführt.<ul><li>Diese ID wird bei allen nachfolgenden Aufrufen im Zusammenhang mit dieser Ausführung benötigt.</li><li>Wenn der Wert `mode` auf `replicate` gesetzt ist, muss die Ausführung in AEM-Veröffentlichungsinstanzen ebenfalls unter derselben `jobId` erfolgen.</li></ul> |
| Parameter | Die Parameter für die Inhaltsaktualisierung | Dazu gehören die anfänglichen Parameter, die zum Starten der Inhaltsaktualisierung bereitgestellt werden, sowie einige interne Standardeinstellungen. |


### Beispielhafte Anfrage zur Inhaltsaktualisierung {#example-content-upgrade-request}

+++Anfrage

```http
POST http://localhost:4502/libs/dam/cfm/maintenance.json
Content-Type: application/json
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
 
{
    "action": "start",
    "serviceTypeId": "uuidUpgradeService",
    "segmentSize": 1000,
    "basePath": "/conf/wknd-shared",
    "interval": 10,
    "mode": "replicate",
    "dryRun": true
}
```

+++

+++Antwort

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:34:37 GMT
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: application/json
Content-Length: 386
 
{
  "jobId": "91af43a6-63ff-45e5-ac7b-06ccf565bdfa",
  "jcr:created": 1729089277309,
  "parameters": {
    "mode": "replicate",
    "dryRun": true,
    "segmentSize": 1000,
    "serviceTypeId": "uuidUpgradeService",
    "action": "start",
    "basePath": "/conf/wknd-shared",
    "topic": "cfm/maintenance",
    "interval": 10,
    "cronSchedule": "*/10 * * * * ?"
  }
}
```

+++

### Abrufen des Status einer Inhaltsaktualisierung {#get-the-status-of-a-content-upgrade}

| Endpunkt | HTTP-Anfragetyp | Kommentar |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `GET` | |
| **Anfrageparameter** | **Wert** | |
| action | status | |
| jobId | `<UUID>` | Die `jobId`, die beim Aufruf zum Starten der Inhaltsaktualisierung zurückgegeben wurde. |
| **Antwortdetails** | **Wert** | |
| status | JSON-Werte | Enthält den detaillierten Status der Inhaltsaktualisierung:<ul><li>Wird nach jedem Intervall (Sekunden) aktualisiert.</li><li>Die Ausführung von `uuidUpgradeService` umfasst zwei Phasen:<ol><li>Phase 0 zum Aktualisieren von Inhaltsfragmentmodellen</li><li>Phase 1 zum Aktualisieren von Inhaltsfragmenten</li></ol></li><li>In jeder Phase werden Statistiken nach jedem Intervall aktualisiert.</li><li>„jobStatus“: „COMPLETED“ kennzeichnet die Aktualisierung als erfolgreich abgeschlossen.</li><li>Die anderen Statuswerte sind selbsterklärend.</li></ul> |

### Beispiel einer Anfrage zum Status der Inhaltsaktualisierung {#example-content-upgrade-status-request}

+++Anfrage

```http
GET http://localhost:4502/libs/dam/cfm/maintenance.json?action=status&jobId=91af43a6-63ff-45e5-ac7b-06ccf565bdfa
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
```

+++

+++Antwort

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:35:51 GMT
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: application/json
Content-Length: 1116
 
{
  "jobId": "91af43a6-63ff-45e5-ac7b-06ccf565bdfa",
  "jcr:created": 1729089277309,
  "eventProcessed": 1,
  "parameters": {
    "mode": "replicate",
    "dryRun": true,
    "segmentSize": 1000,
    "serviceTypeId": "uuidUpgradeService",
    "action": "start",
    "confPath": "/conf/wknd-shared",
    "topic": "cfm/uuid-migration",
    "interval": 10,
    "cronSchedule": "*/10 * * * * ?"
  },
  "status": {
    "jobStatus": "COMPLETED",
    "lastModified": 1729089310301,
    "currentPhaseIndex": 1,
    "phases": {
      "phase-0": {
        "bookmark": 1727183332520,
        "stats": {
          "successCount": 2,
          "skippedCount": 1,
          "errorCount": 0
        },
        "name": "modelUpgrade",
        "lastModified": 1729089290040,
        "isCompleted": true
      },
      "phase-1": {
        "bookmark": 1727183347990,
        "stats": {
          "successCount": 29,
          "skippedCount": 0,
          "errorCount": 1
        },
        "name": "cfUpgrade",
        "lastModified": 1729089310298,
        "isCompleted": true
      }
    }
  }
}
```

+++

+++Beispiele für Protokolldateien

Zusätzlich zum Status einer laufenden Inhaltsaktualisierung, die vom HTTP-Endpunkt abgerufen wurde, liefern AEM-Protokolle detaillierte Informationen zum Fortschritt auf Inhaltsebene. Zum Beispiel:

```xml
#Successful model upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-0: resource: /conf/wknd-shared/settings/dam/cfm/models/article , status: SUCCESS, skips: [], errors: []
 
#Successful content fragment upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-1: resource: /content/dam/wknd-shared/en/magazine/san-diego-surf-spots/san-diego-surfspots , status: SUCCESS, skips: [], errors: []
 
#Unsuccessful/Skipped model upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-0: resource: /conf/wknd-shared/settings/dam/cfm/models/adventure , status: SKIPPED, skips: [Model: '/conf/wknd-shared/settings/dam/cfm/models/adventure', no upgradeable fields found], errors: []
 
#Unsuccessful content fragment upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-1: resource: /content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van , status: FAILED, skips: [], errors: [Path '/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van', Variation: 'master' Field 'featuredImage', Value '/content/dam/wknd-shared/en/magazine/western-australia/adobestock_156407519.jpeg' is invalid; will not upgrade this field.] 
```

Außerdem wird nach der Verarbeitung jedes Segments (Batches) von Inhaltsfragmenten und Modellen ein kumulierter Status protokolliert, der den bisher erzielten Fortschritt zusammenfasst. Zum Beispiel:

```xml
com.adobe.cq.dam.cfm.impl.servicing.PhaseChainProcessor Phase phase-x, processed a segment, stats: {successCount=29, skippedCount=0, errorCount=1}
```

+++

### Abbrechen einer Inhaltsaktualisierung {#abort-a-content-upgrade}

>[!CAUTION]
>
>Durch den Abbruch einer Inhaltsaktualisierung (kein Probelauf):
>
>* werden bereits vorgenommene Änderungen nicht rückgängig gemacht,
>* werden Ihre Inhalte möglicherweise in einem gemischten Status belassen.
>
>Seien Sie vorsichtig, wenn Sie sich hierfür entscheiden.

| Endpunkt | HTTP-Anfragetyp | Kommentar |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **Anfrageparameter** | **Wert** | |
| action | abort | |
| jobId | `<UUID>` | Die `jobId`, die beim Aufruf zum Starten der Inhaltsaktualisierung zurückgegeben wurde. |
| **Antwortdetails** | **Wert** | |
| status | JSON-Werte | Enthält den detaillierten Status der Inhaltsaktualisierung:<ul><li>Der Status, auf den Sie achten sollten, lautet „jobStatus“: „ABORTED“.<br>Nach einer Abbruchaktion werden ausstehende Datensegmente nicht verarbeitet.</li><li>Wenn „jobStatus“ vor einem Abbruch als „COMPLETED“ angegeben wird, hat der Aufruf keine Auswirkungen.</li></ul> |

### Beispielhafte Anfrage zum Abbruch einer Inhaltsaktualisierung {#example-abort-content-upgrade-request}

+++Anfrage

```http
POST http://localhost:4502/libs/dam/cfm/maintenance.json
Content-Type: application/json
Authorization: Basic YWRtaW46YWRtaW4=
Accept: application/json
 
{
    "action": "abort",
    "jobId": "b1dbf6f9-5f59-4007-b631-01b63cd17807"
    "mode": "replicate",
}
```

+++

+++Antwort

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:39:03 GMT
 
{
  "jobId": "b1dbf6f9-5f59-4007-b631-01b63cd17807",
   ...
  "eventProcessed": 2,
  "parameters": {
    ...
    "abort": true,
    ...
  },
  "status": {
     "jobStatus": "ABORTED",
    ...
  }
}
```

+++
