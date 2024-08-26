---
title: Konfigurieren der CDN-Anmeldeinformationen und der Authentifizierung
description: Erfahren Sie, wie Sie CDN-Anmeldeinformationen und die Authentifizierung konfigurieren, indem Sie Regeln in einer Konfigurationsdatei deklarieren und diese mithilfe der Cloud Manager-Konfigurations-Pipeline bereitstellen.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
role: Admin
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: ht
source-wordcount: '1266'
ht-degree: 100%

---


# Konfigurieren der CDN-Anmeldeinformationen und der Authentifizierung {#cdn-credentials-authentication}

Das von Adobe bereitgestellte CDN verfügt über mehrere Funktionen und Dienste, von denen einige auf Anmeldeinformationen und eine Authentifizierung angewiesen sind, um ein angemessenes Maß an Unternehmenssicherheit zu gewährleisten. Durch Deklarieren von Regeln in einer Konfigurationsdatei, die mithilfe der Cloud Manager-[Konfigurations-Pipeline](/help/operations/config-pipeline.md) bereitgestellt wird, können Kundinnen und Kunden per Self-Service Folgendes konfigurieren:

* Den HTTP-Header-Wert des X-AEM-Edge-Key, der vom Adobe-CDN verwendet wird, um Anforderungen zu überprüfen, die von einem kundenseitig verwalteten CDN stammen.
* Das API-Token, mit dem Ressourcen im CDN-Cache gelöscht werden.
* Eine Liste mit Benutzernamen-/Kennwortkombinationen, mit denen durch Übermitteln eines einfachen Authentifizierungsformulars auf beschränkte Inhalte zugegriffen werden kann. [Diese Funktion steht Early-Adoptern zur Verfügung.](/help/release-notes/release-notes-cloud/release-notes-current.md#foundation-early-adopter)

Jede dieser Optionen, einschließlich der Konfigurationssyntax, wird in einem eigenen Abschnitt unten beschrieben. 

Es gibt einen Abschnitt über das [Rotieren von Schlüsseln](#rotating-secrets), welches eine gute Sicherheitspraxis ist.

## HTTP-Header-Wert des kundenseitig verwalteten CDN {#CDN-HTTP-value}

Wie auf der Seite [CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) beschrieben, können Kundinnen und Kunden Traffic über ihr eigenes CDN weiterleiten, das als Kunden-CDN (manchmal auch als BYOCDN) bezeichnet wird.

Im Rahmen der Einrichtung müssen sich das Adobe-CDN und das Kunden-CDN auf einen Wert des HTTP-Headers `X-AEM-Edge-Key` einigen. Dieser Wert wird bei jeder Anfrage im Kunden-CDN festgelegt, bevor er an das Adobe-CDN weitergeleitet wird. Dieses überprüft dann, ob der Wert erwartungsgemäß ist, damit anderen HTTP-Headern vertraut werden kann, einschließlich derer, die dazu beitragen, die Anfrage an den entsprechenden AEM-Ursprung weiterzuleiten.

Der Wert *X-AEM-Edge-Key* wird durch die Eigenschaften `edgeKey1` und `edgeKey2` in einer Datei mit dem Namen `cdn.yaml` oder ähnlich referenziert, die sich unter einem `config`-Ordner der obersten Ebene befindet. Unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) finden Sie weitere Informationen zur Ordnerstruktur und Bereitstellung der Konfiguration.

Die Syntax ist unten beschrieben:

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

Eine Beschreibung der Eigenschaften oberhalb des Knotens `data` finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Eigenschaftswert `kind` sollte *CDN* sein, und die Eigenschaft `version` sollte auf `1` festgelegt werden.

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
>Der Edge-Schlüssel muss als [Cloud Manager-Umgebungsvariable vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) konfiguriert werden, bevor die Konfiguration, die auf ihn verweist, bereitgestellt wird.

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

Eine Beschreibung der Eigenschaften oberhalb des Knotens `data` finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Eigenschaftswert `kind` sollte *CDN* sein, und die Eigenschaft `version` sollte auf `1` festgelegt werden.

Weitere Eigenschaften sind:

* `data`-Knoten, der einen untergeordneten `authentication`-Knoten enthält.
* Unter `authentication` ist ein `authenticators`-Knoten und ein `rules`-Knoten vorhanden, bei denen es sich jeweils um Arrays handelt.
* Authentifizierer: Hiermit können Sie einen Token-Typ oder Anmeldeinformationen deklarieren. In diesem Fall handelt es sich hierbei um einen Bereinigungsschlüssel. Dieser umfasst die folgenden Eigenschaften:
   * name – eine beschreibende Zeichenfolge.
   * type – muss „purge“ sein.
   * purgeKey1 – sein Wert muss auf eine [Cloud Manager-Umgebungsvariable vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) verweisen. Wählen Sie für das Feld „Angewendeter Service“ die Option „Alle“ aus. Es wird empfohlen, dass der Wert (z. B.`${{CDN_PURGEKEY_031224}}`) den Tag widerspiegelt, an dem er hinzugefügt wurde.
   * purgeKey2 – wird für die Rotation von Geheimnissen verwendet, die unten im Abschnitt [Rotieren von Geheimnissen](#rotating-secrets) beschrieben wird. Von `purgeKey1` und `purgeKey2` muss mindestens einer deklariert werden.
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet werden sollen, und ob es sich um die Veröffentlichungs- und/oder die Vorschaustufe handelt.   Folgendes ist enthalten:
   * name – eine beschreibende Zeichenfolge
   * when – eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax im Artikel [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) beurteilt werden soll. Typischerweise umfasst dies einen Vergleich der aktuellen Stufe (z. B. die Veröffentlichungsstufe).
   * action – muss „authenticate“ angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird.

>[!NOTE]
>Der Purge Key muss als [Cloud Manager-Umgebungsvariable vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) konfiguriert werden, bevor die Konfiguration, die auf ihn verweist, bereitgestellt wird.

## Standardauthentifizierung {#basic-auth}

>[!NOTE]
>Diese Funktion ist noch nicht allgemein verfügbar.  Wenn Sie am Early-Adopter-Programm teilnehmen möchten, senden Sie eine E-Mail an `aemcs-cdn-config-adopter@adobe.com`.

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
  experimental_authentication:
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

Eine Beschreibung der Eigenschaften oberhalb des Knotens `data` finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Eigenschaftswert `kind` sollte *CDN* sein, und die Eigenschaft `version` sollte auf `1` festgelegt werden.

Darüber hinaus enthält die Syntax Folgendes:

* einen `data`-Knoten, der einen `experimental_authentication`-Knoten enthält (das experimentelle Präfix wird entfernt, wenn die Funktion veröffentlicht wird).
* Unter `experimental_authentication`, einen Knoten `authenticators` und einen Knoten`rules`, die beide Arrays sind.
* Authentifizierer: Deklarieren Sie in diesem Szenario einen einfachen Authentifizierer mit der folgenden Struktur:
   * name – eine beschreibende Zeichenfolge
   * type – muss `basic` sein.
   * ein Array von Anmeldeinformationen, das jeweils die folgenden Name/Wert-Paare enthält, die Endbenutzende im einfachen Authentifizierungsdialogfeld eingeben können:
      * user – der Name der Benutzerin oder des Benutzers
      * password – Der Wert muss auf eine [Cloud Manager-Umgebungsvariable vom Typ „secret“ ](/help/operations/config-pipeline.md#secret-env-vars) verweisen, wobei **Alle** als Dienstfeld ausgewählt ist.
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet und welche Ressourcen geschützt werden sollen. Jede Regel umfasst:
   * name – eine beschreibende Zeichenfolge
   * when – eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax im Artikel [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) beurteilt werden soll. Typischerweise umfasst dies einen Vergleich der Veröffentlichungsstufe oder bestimmter Pfade.
   * action – muss „authenticate“ angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird. In diesem Fall ist dies der einfache Authentifizierer.

>[!NOTE]
>Die Kennwörter müssen als [Cloud Manager-Umgebungsvariablen vom Typ „secret“](/help/operations/config-pipeline.md#secret-env-vars) konfiguriert werden, bevor die Konfiguration, die auf sie verweist, bereitgestellt wird.

## Rotieren von Geheimnissen {#rotating-secrets}

1. Es gilt als gute Sicherheitspraxis, die Anmeldeinformationen gelegentlich zu ändern. Dies kann wie unten dargestellt mithilfe des Beispiels eines Edge Keys erreicht werden, wobei dieselbe Strategie auch für Bereinigungsschlüssel verwendet wird.

1. Zunächst wurde nur `edgeKey1` definiert, der in diesem Fall als `${{CDN_EDGEKEY_052824}}` referenziert wird, was als empfohlene Konvention das Erstellungsdatum widerspiegelt.

   ```
   experimental_authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
   ```
1. Wenn Sie den Schlüssel rotieren müssen, erstellen Sie ein neues Cloud Manager-Geheimnis, z. B. `${{CDN_EDGEKEY_041425}}`.
1. Verweisen Sie in der Konfiguration von `edgeKey2` darauf und stellen Sie es bereit.

   ```
   experimental_authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```

1. Sobald Sie sicher sind, dass der alte Edge Key nicht mehr verwendet wird, entfernen Sie ihn, indem Sie `edgeKey1` aus der Konfiguration entfernen.

   ```
   experimental_authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```
1. Löschen Sie die Referenz des alten Geheimnisses (`${{CDN_EDGEKEY_052824}}`) aus Cloud Manager aus und nehmen Sie die Bereitstellung vor.

1. Wenn Sie für die nächste Rotation bereit sind, gehen Sie analog vor. Diesmal fügen Sie jedoch `edgeKey1` zu der Konfiguration hinzu, indem Sie auf ein neues Cloud Manager-Umgebungsgeheimnis verweisen, das beispielsweise den Namen `${{CDN_EDGEKEY_031426}}` hat.

   ```
   experimental_authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
         edgeKey1: ${{CDN_EDGEKEY_031426}}
   ```
