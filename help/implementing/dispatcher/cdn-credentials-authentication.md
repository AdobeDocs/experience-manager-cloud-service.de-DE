---
title: Konfigurieren der CDN-Anmeldeinformationen und der Authentifizierung
description: Erfahren Sie, wie Sie CDN-Anmeldeinformationen und die Authentifizierung konfigurieren, indem Sie Regeln in einer Konfigurationsdatei deklarieren und diese mithilfe der Cloud Manager-Konfigurations-Pipeline bereitstellen.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
role: Admin
source-git-commit: ab855192e4b60b25284b19cc0e3a8e9da5a7409c
workflow-type: ht
source-wordcount: '1712'
ht-degree: 100%

---


# Konfigurieren der CDN-Anmeldeinformationen und der Authentifizierung {#cdn-credentials-authentication}

Das von Adobe bereitgestellte CDN verfügt über mehrere Funktionen und Dienste, von denen einige auf Anmeldeinformationen und eine Authentifizierung angewiesen sind, um ein angemessenes Maß an Unternehmenssicherheit zu gewährleisten. Durch die Deklaration von Regeln in einer Konfigurationsdatei, die über die [Konfigurationspipeline](/help/operations/config-pipeline.md) des Cloud Managers bereitgestellt wird, können Kundinnen und Kunden Folgendes selbst konfigurieren:

* Den HTTP-Header-Wert des X-AEM-Edge-Key, der vom Adobe-CDN verwendet wird, um Anforderungen zu überprüfen, die von einem kundenseitig verwalteten CDN stammen.
* Das API-Token, mit dem Ressourcen im CDN-Cache gelöscht werden.
* Liste mit Benutzernamen-/Passwortkombinationen, mit denen durch Übermitteln eines einfachen Authentifizierungsformulars auf beschränkte Inhalte zugegriffen werden kann.

Jede dieser Optionen, einschließlich der Konfigurationssyntax, wird in einem eigenen Abschnitt unten beschrieben. 

Es gibt einen Abschnitt über das [Rotieren von Schlüsseln](#rotating-secrets), welches eine gute Sicherheitspraxis ist.

>[!NOTE]
> Geheimnisse, die als Umgebungsvariablen definiert sind, sollten als unveränderlich betrachtet werden. Anstatt den Wert zu ändern, sollten Sie ein neues Geheimnis mit einem neuen Namen erstellen und in der Konfiguration auf dieses Geheimnis verweisen. Andernfalls erfolgt eine unzuverlässige Aktualisierung der Geheimnisse.

>[!WARNING]
>Entfernen Sie nicht die Umgebungsvariablen, auf die in Ihrer CDN-Konfiguration verwiesen wird. Dies kann zu Fehlern beim Aktualisieren Ihrer CDN-Konfiguration führen (z. B. beim Aktualisieren von Regeln oder benutzerdefinierten Domains und Zertifikaten).

## HTTP-Header-Wert des kundenseitig verwalteten CDN {#CDN-HTTP-value}

Wie auf der Seite [CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) beschrieben, können Kundinnen und Kunden Traffic über ihr eigenes CDN weiterleiten, das als Kunden-CDN (manchmal auch als BYOCDN) bezeichnet wird.

Im Rahmen der Einrichtung müssen sich das Adobe-CDN und das Kunden-CDN auf einen Wert des HTTP-Headers `X-AEM-Edge-Key` einigen. Dieser Wert wird bei jeder Anfrage im Kunden-CDN festgelegt, bevor er an das Adobe-CDN weitergeleitet wird. Dieses überprüft dann, ob der Wert erwartungsgemäß ist, damit anderen HTTP-Headern vertraut werden kann, einschließlich derer, die dazu beitragen, die Anfrage an den entsprechenden AEM-Ursprung weiterzuleiten.

Der Wert *X-AEM-Edge-Key* wird durch die Eigenschaften `edgeKey1` und `edgeKey2` in einer Datei mit dem Namen `cdn.yaml` oder ähnlich referenziert, die sich unter einem `config`-Ordner der obersten Ebene befindet. Under [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) finden Sie weitere Informationen zur Ordnerstruktur und Bereitstellung der Konfiguration.  Die Syntax ist im folgenden Beispiel beschrieben.

Weitere Informationen zur Fehlerbehebung und häufige Fehler finden Sie unter [Häufige Fehler](/help/implementing/dispatcher/cdn.md#common-errors).

>[!WARNING]
>Direkter Zugriff ohne korrekten X-AEM-Edge-Schlüssel wird für alle Anfragen verweigert, die der Bedingung entsprechen (im Beispiel unten bedeutet dies alle Anfragen an die Veröffentlichungsebene). Wenn Sie die Authentifizierung schrittweise einführen müssen, lesen Sie den Abschnitt [Sichere Migration zur Verringerung des Risikos von blockiertem Traffic](#migrating-safely).

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
    authenticators:
      - name: edge-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_052824}}
        edgeKey2: ${{CDN_EDGEKEY_041425}}
    rules:
      - name: edge-auth-rule
        when: { reqProperty: tier, equals: "publish" }
        action:
          type: authenticate
          authenticator: edge-auth
```

Eine Beschreibung der Eigenschaften oberhalb des Knotens `data` finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Wert der Eigenschaft `kind` sollte *CDN* sein, und die Eigenschaft `version` sollte auf `1` festgelegt werden.

Weitere Informationen finden Sie im Tutorial-Schritt [Konfigurieren und Bereitstellen der CDN-Regel für die HTTP-Header-Validierung](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/content-delivery/custom-domain-names-with-customer-managed-cdn#configure-and-deploy-http-header-validation-cdn-rule).

Weitere Eigenschaften sind:

* `Data`-Knoten, der einen untergeordneten `authentication`-Knoten enthält.
* Unter `authentication` ist ein `authenticators`-Knoten und ein `rules`-Knoten vorhanden, bei denen es sich jeweils um Arrays handelt.
* Authentifizierer: Hiermit können Sie einen Typ von Token oder Anmeldeinformationen deklarieren. In diesem Fall handelt es sich dabei um einen Edge-Schlüssel.  Dieser umfasst die folgenden Eigenschaften:
   * name – eine beschreibende Zeichenfolge.
   * type – muss `edge` sein.
   * edgeKey1 – der Wert von *X-AEM-Edge-Key*, der auf eine [Cloud Manager-Umgebungsvariable vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) verweisen muss. Wählen Sie für das Feld „Angewendeter Service“ die Option „Alle“ aus. Es wird empfohlen, dass der Wert (z. B.`${{CDN_EDGEKEY_052824}}`) den Tag widerspiegelt, an dem er hinzugefügt wurde.
   * edgeKey2 – wird für die Rotation von Geheimnissen verwendet, die unten im Abschnitt [Rotieren von Geheimnissen](#rotating-secrets) beschrieben ist. Definieren Sie den Wert ähnlich wie „edgeKey1“. Von `edgeKey1` und `edgeKey2` muss mindestens einer deklariert werden.
<!--   * OnFailure - defines the action, either `log` or `block`, when a request doesn't match either `edgeKey1` or `edgeKey2`. For `log`, request processing will continue, while `block` will serve a 403 error. The `log` value is useful when testing a new token on a live site since you can first confirm that the CDN is correctly accepting the new token before changing to `block` mode; it also reduces the chance of lost connectivity between the customer CDN and the Adobe CDN, as a result of an incorrect configuration. -->
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet werden sollen, und ob es sich um die Veröffentlichungs- und/oder die Vorschaustufe handelt.   Folgendes ist enthalten:
   * name – eine beschreibende Zeichenfolge.
   * when – eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax im Artikel [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) beurteilt werden soll. Typischerweise umfasst dies einen Vergleich der aktuellen Stufe (z. B. die Veröffentlichungsstufe), sodass der gesamte Live-Traffic beim Routing über das Kunden-CDN validiert wird.
   * action – muss „authenticate“ angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird.

>[!NOTE]
>Der Edge-Schlüssel muss als [Cloud Manager-Umgebungsvariable vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) konfiguriert werden, bevor die Konfiguration, die auf ihn verweist, bereitgestellt wird. Es wird empfohlen, einen eindeutigen zufälligen Schlüssel mit einer Mindestlänge von 32 Byte zu verwenden. Beispielsweise kann die kryptografische Open SSL-Bibliothek einen zufälligen Schlüssel generieren, indem der Befehl `openssl rand -hex 32` ausgeführt wird.

### Sichere Migration zur Verringerung des Risikos von blockiertem Traffic {#migrating-safely}

Wenn Ihre Site bereits live ist, sollten Sie bei der Migration zu einem kundenseitig verwaltetem CDN Vorsicht walten lassen, da eine Fehlkonfiguration öffentlichen Traffic blockieren kann. Dies liegt daran, dass nur Anforderungen mit dem erwarteten Header-Wert X-AEM-Edge-Key vom Adobe CDN akzeptiert werden. Es wird ein Ansatz empfohlen, bei dem vorübergehend eine zusätzliche Bedingung in die Authentifizierungsregel aufgenommen wird, wodurch die Anfrage nur dann blockiert wird, wenn ein Test-Header enthalten ist oder ein Pfad übereinstimmt:

```
    - name: edge-auth-rule
        when:
          allOf:  
            - { reqProperty: tier, equals: "publish" }
            - { reqHeader: x-edge-test, equals: "test" }
        action:
          type: authenticate
          authenticator: edge-auth
```

```
    - name: edge-auth-rule
        when:
          allOf:
            - { reqProperty: tier, equals: "publish" }
            - { reqProperty: path, like: "/test*" }
        action:
          type: authenticate
          authenticator: edge-auth
```

Das folgende `curl`-Anfragemuster kann verwendet werden:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <CONFIGURED_EDGE_KEY>" -H "x-edge-test: test"
```

Nach erfolgreichem Testen kann die zusätzliche Bedingung entfernt und die Konfiguration neu bereitgestellt werden.

## API-Bereinigungs-Token {#purge-API-token}

Kundinnen und Kunden können [den CDN-Cache mithilfe eines deklarierten API-Bereinigungs-Tokens bereinigen](/help/implementing/dispatcher/cdn-cache-purge.md). Das Token wird in einer Datei mit dem Namen `cdn.yaml` oder ähnlich unter einem `config`-Ordner der obersten Ebene deklariert. Unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) finden Sie weitere Informationen zur Ordnerstruktur und Bereitstellung der Konfiguration.

Die Syntax ist unten beschrieben:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
    authenticators:
       - name: purge-auth
         type: purge
         purgeKey1: ${{CDN_PURGEKEY_031224}}
         purgeKey2: ${{CDN_PURGEKEY_021225}}
    rules:
       - name: purge-auth-rule
         when: { reqProperty: tier, equals: "publish" }
         action:
           type: authenticate
           authenticator: purge-auth
```

Eine Beschreibung der Eigenschaften oberhalb des Knotens `data` finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Wert der Eigenschaft `kind` sollte *CDN* sein, und die Eigenschaft `version` sollte auf `1` festgelegt werden.

Weitere Eigenschaften sind:

* `data`-Knoten, der einen untergeordneten `authentication`-Knoten enthält.
* Unter `authentication` ist ein `authenticators`-Knoten und ein `rules`-Knoten vorhanden, bei denen es sich jeweils um Arrays handelt.
* Authentifizierer: Hiermit können Sie einen Token-Typ oder Anmeldeinformationen deklarieren. In diesem Fall handelt es sich hierbei um einen Bereinigungsschlüssel. Dieser umfasst die folgenden Eigenschaften:
   * name – eine beschreibende Zeichenfolge.
   * type – muss „purge“ sein.
   * purgeKey1 – sein Wert muss auf eine [Cloud Manager-Umgebungsvariable vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) verweisen. Wählen Sie für das Feld „Angewendeter Service“ die Option „Alle“ aus. Es wird empfohlen, dass der Wert (z. B.`${{CDN_PURGEKEY_031224}}`) den Tag widerspiegelt, an dem er hinzugefügt wurde.
   * purgeKey2 – wird für die Rotation von Geheimnissen verwendet, wie unten im Abschnitt [Rotieren von Geheimnissen](#rotating-secrets) beschrieben. Von `purgeKey1` und `purgeKey2` muss mindestens einer deklariert werden.
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet werden sollen, und ob es sich um die Veröffentlichungs- und/oder die Vorschaustufe handelt.   Folgendes ist enthalten:
   * name – eine beschreibende Zeichenfolge
   * when – eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax im Artikel [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) beurteilt werden soll. Typischerweise umfasst dies einen Vergleich der aktuellen Stufe (z. B. die Veröffentlichungsstufe).
   * action – muss „authenticate“ angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird.

>[!NOTE]
>Der Purge Key muss als [Cloud Manager-Umgebungsvariable vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) konfiguriert werden, bevor die Konfiguration, die auf ihn verweist, bereitgestellt wird. Es wird empfohlen, einen eindeutigen zufälligen Schlüssel mit einer Mindestlänge von 32 Byte zu verwenden. Beispielsweise kann die kryptografische Open SSL-Bibliothek einen zufälligen Schlüssel generieren, indem der Befehl „openssl rand -hex 32“ ausgeführt wird.

Sie können [ein Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache) durchlaufen, das sich auf die Konfiguration von Bereinigungsschlüsseln und die Durchführung der CDN-Cache-Bereinigung konzentriert.

## Standardauthentifizierung {#basic-auth}

Schützen Sie bestimmte Inhaltsressourcen mithilfe eines einfachen Authentifizierungsdialogfelds als Popup, das einen Benutzernamen und ein Passwort erforderlich macht. Diese Funktion ist in erster Linie für leichte Authentifizierungsfälle wie die Überprüfung von Inhalten durch geschäftliche Stakeholder und nicht als vollständige Lösung für Zugriffsrechte von Endbenutzenden gedacht.

Endbenutzenden wird ein einfaches Authentifizierungsdialogfeld wie das folgende angezeigt:

![basicauth-dialog](/help/implementing/dispatcher/assets/basic-auth-dialog.png)


Es gilt folgende Syntax:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
    authenticators:
       - name: my-basic-authenticator
         type: basic
         credentials:
           - user: johndoe
             password: ${{JOHN_DOE_PASSWORD}}
           - user: janedoe
             password: ${{JANE_DOE_PASSWORD}}
    rules:
       - name: basic-auth-rule
         when: { reqProperty: path, like: "/summercampaign" }
         action:
           type: authenticate
           authenticator: my-basic-authenticator
```

Eine Beschreibung der Eigenschaften oberhalb des Knotens `data` finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Wert der Eigenschaft `kind` sollte *CDN* sein, und die Eigenschaft `version` sollte auf `1` festgelegt werden.

Darüber hinaus enthält die Syntax Folgendes:

* ein `data`-Knoten, der einen `authentication`-Knoten enthält.
* Unter `authentication`, einen Knoten `authenticators` und einen Knoten`rules`, die beide Arrays sind.
* Authentifizierer: Deklarieren Sie in diesem Szenario einen einfachen Authentifizierer mit der folgenden Struktur:
   * name – eine beschreibende Zeichenfolge
   * type – muss `basic` sein.
   * ein Array von bis zu 10 Anmeldeinformationen, die jeweils die folgenden Name/Wert-Paare enthalten, die Endbenutzende im Dialogfeld der einfachen Authentifizierung eingeben können:
      * user – der Name der Benutzerin bzw. des Benutzers.
      * password – Der Wert muss auf eine [Cloud Manager-Umgebungsvariable vom Typ „secret“ ](/help/operations/config-pipeline.md#secret-env-vars) verweisen, wobei **Alle** als Dienstfeld ausgewählt ist.
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet und welche Ressourcen geschützt werden sollen. Jede Regel umfasst:
   * name – eine beschreibende Zeichenfolge
   * when – eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax im Artikel [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) beurteilt werden soll. Typischerweise umfasst dies einen Vergleich der Veröffentlichungsstufe oder bestimmter Pfade.
   * action – muss „authenticate“ angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird. In diesem Fall ist dies der einfache Authentifizierer.

>[!NOTE]
>Die Kennwörter müssen als [Cloud Manager-Umgebungsvariablen vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) konfiguriert werden, bevor die Konfiguration, die auf sie verweist, bereitgestellt wird.

## Wechseln von Geheimnissen {#rotating-secrets}

Es empfiehlt sich als gute Sicherheitspraxis, die Anmeldeinformationen regelmäßig zu ändern. Denken Sie daran, dass Umgebungsvariablen nicht direkt geändert werden sollten, sondern erstellen Sie stattdessen einen neuen geheimen Schlüssel und verweisen Sie in der Konfiguration auf den neuen Namen.

Dies kann wie unten dargestellt mithilfe des Beispiels eines Edge-Schlüssels erreicht werden, wobei dieselbe Strategie auch für Bereinigungsschlüssel verwendet wird.

1. Zunächst wurde nur `edgeKey1` definiert, der in diesem Fall als `${{CDN_EDGEKEY_052824}}` referenziert wird, was als empfohlene Konvention das Erstellungsdatum widerspiegelt.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
   ```
1. Wenn Sie den Schlüssel rotieren müssen, erstellen Sie ein neues Cloud Manager-Geheimnis, z. B. `${{CDN_EDGEKEY_041425}}`.
1. Verweisen Sie in der Konfiguration von `edgeKey2` darauf und stellen Sie es bereit.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```

1. Sobald Sie sicher sind, dass der alte Edge Key nicht mehr verwendet wird, entfernen Sie ihn, indem Sie `edgeKey1` aus der Konfiguration entfernen.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```
1. Löschen Sie die Referenz des alten Geheimnisses (`${{CDN_EDGEKEY_052824}}`) aus Cloud Manager aus und nehmen Sie die Bereitstellung vor.

1. Wenn Sie für die nächste Rotation bereit sind, gehen Sie analog vor. Diesmal fügen Sie jedoch `edgeKey1` zu der Konfiguration hinzu, indem Sie auf ein neues Cloud Manager-Umgebungsgeheimnis verweisen, das beispielsweise den Namen `${{CDN_EDGEKEY_031426}}` hat.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
         edgeKey1: ${{CDN_EDGEKEY_031426}}
   ```

Beim Rotieren von geheimen Daten, die in Anfrage-Headern festgelegt sind, z. B. zur Authentifizierung gegen ein Backend, wird empfohlen, die Rotation in zwei Schritten durchzuführen, um sicherzustellen, dass der Header-Wert ohne temporäre Lücken gewechselt wird.

1. Erstkonfiguration vor der Rotation. In diesem Zustand wird der alte Schlüssel an das Backend gesendet.

   ```
   requestTransformations:
     rules:
       - name: set-api-key-header
         actions:
           - type: set
             reqHeader: x-api-key
             value ${{API_KEY_1}}
   ```

1. Führen Sie den neuen Schlüssel `API_KEY_2` ein, indem Sie dieselbe Kopfzeile zweimal festlegen (der neue Schlüssel sollte dabei nach dem alten Schlüssel festgelegt werden). Nach der Bereitstellung wird der neue Schlüssel im Backend angezeigt.

   ```
   requestTransformations:
     rules:
       - name: set-api-key-header
         actions:
           - type: set
             reqHeader: x-api-key
             value ${{API_KEY_1}}
           - type: set
             reqHeader: x-api-key
             value ${{API_KEY_2}}
   ```

1. Entfernen Sie den alten Schlüssel `API_KEY_1` aus der Konfiguration. Nach der Bereitstellung wird der neue Schlüssel im Backend angezeigt und die Umgebungsvariable des alten Schlüssels kann sicher entfernt werden.


   ```
   requestTransformations:
     rules:
       - name: set-api-key-header
         actions:
           - type: set
             reqHeader: x-api-key
             value ${{API_KEY_2}}
   ```


