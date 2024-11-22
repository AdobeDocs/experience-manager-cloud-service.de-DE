---
title: Aktualisieren Ihrer Inhaltsfragmente für UUID-Referenzen
description: Erfahren Sie, wie Sie Ihre Inhaltsfragmente für optimierte UUID-Referenzen in Adobe Experience Manager as a Cloud Service für die Bereitstellung Headless Content aktualisieren.
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 5aa04f3b042f8e9f9af97148ceab0288ff210238
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 2%

---

# Aktualisieren Ihrer Inhaltsfragmente für UUID-Referenzen {#upgrade-content-fragments-for-UUID-references}

>[!IMPORTANT]
>
>Verschiedene Funktionen der GraphQL-API für die Verwendung mit Inhaltsfragmenten sind über das Early Adopter-Programm verfügbar.
>
>Informationen zum Status und zur Anwendung bei Interesse finden Sie in den [Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

Um die Stabilität Ihrer GraphQL-Filter zu optimieren, können Sie die Inhalts- und Fragmentverweise in Ihren Inhaltsfragmenten so aktualisieren, dass sie universell eindeutige IDs (UUID) verwenden.

Ursprünglich stellten Inhaltsfragmentmodelle die Datentypen **Inhaltsreferenz** und **Fragmentreferenz** bereit. Beide Verweise verwenden einen Pfad, um auf die referenzierte Ressource zu verweisen. Dieser Pfad kann veraltet sein, wenn die Ressource verschoben wird. Obwohl solche Verweise in den meisten Szenarien mehr als ausreichen, wurden Inhaltsfragmentmodelle erweitert, um auch Verweise auf Grundlage einer UUID bereitzustellen:

* **Inhaltsreferenz (UUID)**
* **Fragmentverweis (UUID)**.

Diese neuen Referenztypen können sowohl in neuen Inhaltsfragmentmodellen und -fragmenten als auch zur Erweiterung vorhandener Instanzen verwendet werden.

Um vorhandene Inhaltsfragmente und -modelle zu aktualisieren, können Sie das hier beschriebene Verfahren ausführen.

>[!CAUTION]
>
>Vor dem Ausführen des Aktualisierungsvorgangs sollten Sie immer [einen Probelauf ausführen](#execute-a-dry-run) , um potenzielle Probleme mit Ihrem Inhalt hervorzuheben.

## Was wird aktualisiert? {#what-is-upgraded}

Die folgenden Aktualisierungen werden vorgenommen:

* Felder der Datentypen:
   * **Inhaltsreferenz** wird in **Inhaltsreferenz (UUID)** konvertiert.
   * **Fragmentverweis** wird in **Fragmentverweis (UUID)** konvertiert.
* Die Werte der pfadbasierten Verweise in diesen Feldern werden durch die entsprechenden UUIDs ersetzt

>[!NOTE]
>
>Nach der Aktualisierung sind beide Datentypen weiterhin im Inhaltsfragmentmodell-Editor verfügbar. Sie können neue Felder basierend auf beiden Typen erstellen (es wird jedoch erwartet, dass Sie die UUID-basierten Typen verwenden) und die Aktualisierung bei Bedarf erneut durchführen.

## Inhalt NICHT aktualisiert {#what-is-not-upgraded}

Die folgenden Referenzen werden nicht aktualisiert:

* Seitenverweise - UUIDs werden noch nicht unterstützt
* Alle ungültigen Verweise, z. B. wenn das Ziel des Inhaltsfragmentpfads oder des Asset-Pfads nicht vorhanden ist

   * Ungültige Referenzen werden nicht aktualisiert, da der Inhaltsfragmentpfad oder der Asset-Pfad ungültig ist und keine entsprechende UUID zugewiesen werden kann. Die ursprüngliche Referenz bleibt unberührt.

   * Verwenden Sie einen [Trockenlauf](#execute-a-dry-run), um ungültige Verweise zu erkennen.

  >[!NOTE]
  >
  >Da sie ungültig sind, können sie unabhängig von der Aktualisierung nicht verwendet werden.

## Wann sollten Sie nicht aktualisieren? {#when-you-should-not-upgrade}

Aktualisieren Sie nicht:

* Wenn eines Ihrer Inhaltsfragmente Seitenverweise verwendet; da UUIDs für Seitenverweise noch nicht unterstützt werden

## Einschränkungen von UUID-Verweisen {#limitations-of-uuid-references}

Derzeit gelten die folgenden Einschränkungen bei der Verwendung von Verweisen, die auf einer UUID basieren:

* Modelle

   * Neue Inhaltsfragmentmodelle mit den Feldern &quot;Inhaltsfragment-UUID&quot;oder &quot;Content Reference UUID&quot;können nicht über OpenAPI erstellt werden.
   * Das Feld `id` für Modelle wurde nicht in UUID-basiert geändert. Es verwendet den dekodierten base64-Pfad des Modells. Modelle können nicht verschoben werden. Daher ist dieser Wert weiterhin stabil.

* Assets

   * Beim Erstellen eines Inhaltsfragments über OpenAPI müssen die Feldtypen `fragment-reference` oder `content-reference` verwendet werden, um Verweise auf ein Fragment bzw. ein Asset anzugeben - selbst wenn der Wert eines UUID-basierten Referenzfelds festgelegt wird.

## Upgrade-Planung {#upgrade-planning}

Es gibt einige vorbereitende Schritte, bevor Sie Ihr Upgrade ausführen.

### Ausführen eines Trockenlaufs {#execute-a-dry-run}

Es wird empfohlen, bei jedem *Upgrade Ihres Inhalts zunächst einen Probelauf durchzuführen.* Dadurch werden Protokolldateien mit Einträgen erstellt, die potenzielle Probleme hervorheben:

* Ungültige Verweise
* Seitenverweise

Führen Sie das Inhaltsupdate im Modus `dryRun` aus, um:

* Identifizieren Sie ungültige Verweise, indem Sie sie in den Protokolldateien auflisten.
Sie können diese Verweise dann beheben, bevor Sie die eigentliche Inhaltsaktualisierung ausführen.
* alle Seitenverweise identifizieren, indem sie sie in den Protokolldateien auflisten
Wenn Seitenverweise erkannt werden, sollten Sie [nicht die Inhaltsaktualisierung ausführen](#when-you-should-not-upgrade).


### Erzwingen des Einfrierens von Inhalt {#enforce-a-content-freeze}

Die Durchführung der Aktualisierung des Inhalts sollte während des Einfrierzeitraums des Inhalts geplant werden.

Die Dauer des Einfrierens des Inhalts hängt vom Volumen der Inhaltsfragmente ab, die aktualisiert werden. Dementsprechend kann die Aktualisierung zwischen einigen Minuten und einigen Stunden dauern und hängt auch von den Parametern ab, die beim Starten der Inhaltsaktualisierung verwendet werden.

## Ausführen der Inhaltsaktualisierung {#running-the-content-upgrade}

Die Inhaltsaktualisierung kann mithilfe des -Endpunkts verwaltet werden: `/libs/dam/cfm/maintenance.json`

>[!NOTE]
>
>Für den Zugriff auf den Endpunkt benötigt Ihr Konto die Rolle `Administrator` .

### Inhaltsaktualisierung starten {#start-a-content-upgrade}

| Endpunkt | HTTP-Anfragetyp | Kommentar |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **Anforderungsparameter** | **Wert** | |
| Aktion | `start` | |
| serviceTypeId | `uuidUpgradeService` | Die Diensttyp-ID (vordefinierter, fester Wert). |
|  segmentSize | `1000` | Die Anzahl der Inhaltsfragmente oder Modelle, die in einem Segment (Batch) aktualisiert werden. |
| basePath | `/conf` | Geben Sie Folgendes an:<ul><li>den Stamm `/conf` , um alle AEM Konfigurationen zu aktualisieren</li><li>einen ausgewählten AEM Konfigurationspfad. für die das Content-Upgrade ausgeführt wird<br>Beispiel: `/conf/wknd-shared` aktualisiert nur den einzelnen Mandanten `wknd-shared`</li></ul> |
| Intervall | `10` | Intervall in Sekunden, nach dem das nächste Segment von Inhaltsfragmenten oder Modellen aktualisiert wird. |
| mode | `replicate`, `noReplicate` | <ul><li>`replicate`: repliziert denselben Auftrag auf allen AEM Publish-Instanzen.</li><li>`noReplicate`: Führt den Auftrag nur auf AEM Autoreninstanzen aus</li></ul> |
| dryRun |  `true`, `false` | <ul><li>`false`: Simulieren Sie die Inhaltsaktualisierung, ohne Inhaltsänderungen zu speichern.</li><li>`true`: Führen Sie die Inhaltsaktualisierung durch und speichern Sie Inhaltsänderungen</li></ul> |
| **Antwortdetails** | **Wert** | |
| jobId | `UUID` |  Die ID des Auftrags, der die Inhaltsaktualisierung ausführt.<ul><li>Diese ID ist bei allen nachfolgenden Aufrufen im Zusammenhang mit dieser Ausführung erforderlich.</li><li>Wenn der Wert `mode` auf `replicate` gesetzt ist, muss die Ausführung auf AEM Publish-Instanzen ebenfalls unter demselben `jobId` erfolgen.</li></ul> |
| Parameter | Die Parameter für die Inhaltsaktualisierung | Dazu gehören die anfänglichen Parameter, die zum Starten der Inhaltsaktualisierung bereitgestellt werden, sowie einige interne Standardeinstellungen. |


### Beispiel für eine Anfrage zur Inhaltsaktualisierung {#example-content-upgrade-request}

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

++ + Antwort

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

### Abrufen des Status eines Content-Upgrades {#get-the-status-of-a-content-upgrade}

| Endpunkt | HTTP-Anfragetyp | Kommentar |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `GET` | |
| **Anforderungsparameter** | **Wert** | |
| Aktion | status | |
| jobId | `<UUID>` | Die `jobId` , die vom Aufruf zum Starten der Inhaltsaktualisierung zurückgegeben wurde. |
| **Antwortdetails** | **Wert** | |
| status | JSON-Werte | Enthält den detaillierten Status der Inhaltsaktualisierung:<ul><li>Aktualisiert nach jedem Intervall (Sekunden).</li><li>Die Ausführung von `uuidUpgradeService` umfasst zwei Phasen:<ol><li>Phase 0 zum Aktualisieren von Inhaltsfragmentmodellen</li><li>Phase 1 zum Aktualisieren von Inhaltsfragmenten</li></ol></li><li>In jeder Phase werden Statistiken nach jedem Intervall aktualisiert.</li><li>&quot;jobStatus&quot;: &quot;COMPLETED&quot;kennzeichnet die Aktualisierung als erfolgreich abgeschlossen.</li><li>Andere Statuswerte sind selbsterklärend.</li></ul> |

### Beispiel für eine Statusanforderung für die Inhaltsaktualisierung {#example-content-upgrade-status-request}

+++Anfrage

```http
GET http://localhost:4502/libs/dam/cfm/maintenance.json?action=status&jobId=91af43a6-63ff-45e5-ac7b-06ccf565bdfa
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
```

+++

++ + Antwort

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

+++Beispielprotokolldateien

Zusätzlich zum Status einer laufenden Inhaltsaktualisierung, die vom HTTP-Endpunkt abgerufen wurde, liefern AEM Protokolle detaillierte Informationen zum Fortschritt auf der Inhaltsebene. Zum Beispiel:

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
>Abbrechen einer Inhaltsaktualisierung (dies ist kein Trockenlauf):
>
>* keine bereits vorgenommenen Änderungen rückgängig machen
>* Ihren Inhalt möglicherweise in einem gemischten Status belassen
>
>Verwenden Sie diese Aktion mit Vorsicht.

| Endpunkt | HTTP-Anfragetyp | Kommentar |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **Anforderungsparameter** | **Wert** | |
| Aktion | abort | |
| jobId | `<UUID>` | Die `jobId` , die vom Aufruf zum Starten der Inhaltsaktualisierung zurückgegeben wurde. |
| **Antwortdetails** | **Wert** | |
| status | JSON-Werte | Enthält den detaillierten Status der Inhaltsaktualisierung:<ul><li>Der zu beachtende Status lautet &quot;jobStatus&quot;: &quot;ABORTED&quot;.<br>Nach einer Abbruchaktion werden ausstehende Segmente von Daten nicht verarbeitet.</li><li>Wenn der jobStatus vor einem Abbruch &quot;COMPLETED&quot;lautet, hat der Aufruf keine Auswirkungen.</li></ul> |

### Beispiel für Abbruch einer Anfrage zur Inhaltsaktualisierung {#example-abort-content-upgrade-request}

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

++ + Antwort

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
