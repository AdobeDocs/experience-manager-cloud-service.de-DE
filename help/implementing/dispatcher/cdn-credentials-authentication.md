---
title: Konfigurieren von CDN-Anmeldeinformationen und einer Authentifizierung
description: Erfahren Sie, wie Sie CDN-Anmeldeinformationen und eine Authentifizierung konfigurieren, indem Sie Regeln in einer Konfigurationsdatei deklarieren und diese mithilfe der Cloud Manager-Konfigurations-Pipeline bereitstellen.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
role: Admin
source-git-commit: 73d0a4a73a3e97a91b2276c86d3ed1324de8c361
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 73%

---

# Konfigurieren von CDN-Anmeldeinformationen und einer Authentifizierung {#cdn-credentials-authentication}

>[!NOTE]
>Diese Funktion ist noch nicht allgemein verfügbar.  Wenn Sie am Early-Adopter-Programm teilnehmen möchten, senden Sie eine E-Mail an `aemcs-cdn-config-adopter@adobe.com`.

Das von Adobe bereitgestellte CDN verfügt über mehrere Funktionen und Dienste, von denen einige auf Anmeldeinformationen und eine Authentifizierung angewiesen sind, um ein angemessenes Maß an Unternehmenssicherheit zu gewährleisten. Durch Deklarieren von Regeln in einer Konfigurationsdatei, die mithilfe der [Cloud Manager-Konfigurations-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline) bereitgestellt wird, können Kundinnen und Kunden per Self-Service Folgendes konfigurieren:

* Der HTTP-Header-Wert, der vom Adobe-CDN verwendet wird, um Anforderungen zu überprüfen, die von einem kundenseitig verwalteten CDN stammen.
* Das API-Token, mit dem Ressourcen im CDN-Cache gelöscht werden.
* Eine Liste mit Benutzername-/Kennwortkombinationen, die durch Senden eines einfachen Authentifizierungsformulars auf eingeschränkten Inhalt zugreifen können.


Jede dieser Optionen, einschließlich der Konfigurationssyntax, wird in einem eigenen Abschnitt unten beschrieben. Im Abschnitt [Allgemeine Einrichtung](#common-setup) werden die beiden allgemeinen Einrichtungen sowie die Bereitstellung erläutert. Schließlich gibt es einen Abschnitt über das [Rotieren von Schlüsseln](#rotating-secrets), welches als gute Sicherheitspraxis betrachtet wird.

## HTTP-Header-Wert des kundenseitig verwalteten CDN {#CDN-HTTP-value}

Wie auf der Seite [CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) beschrieben, können Kundinnen und Kunden Traffic über ihr eigenes CDN weiterleiten, das als Kunden-CDN (manchmal auch als BYOCDN) bezeichnet wird.

Im Rahmen der Einrichtung müssen sich das Adobe-CDN und das Kunden-CDN auf einen Wert des HTTP-Headers `X-AEM-Edge-Key` einigen. Dieser Wert wird bei jeder Anfrage im Kunden-CDN festgelegt, bevor er an das Adobe-CDN weitergeleitet wird. Dieses überprüft dann, ob der Wert erwartungsgemäß ist, damit anderen HTTP-Headern vertraut werden kann, einschließlich derer, die dazu beitragen, die Anfrage an den entsprechenden AEM-Ursprung weiterzuleiten.

Die `X-AEM-Edge-Key` -Wert wird mit der unten stehenden Syntax deklariert, wobei die tatsächlichen Werte durch die Eigenschaften edgeKey1 und edgeKey2 referenziert werden. Siehe [Allgemeine Einrichtung](#common-setup) -Abschnitt, um zu erfahren, wie Sie die Konfiguration bereitstellen.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
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

Die Syntax für den Wert `X-AEM-Edge-Key` enthält:

* Art, Version und Metadaten.
* Datenknoten, der einen untergeordneten Knoten `experimental_authentication` enthält (das experimentelle Präfix wird entfernt, wenn die Funktion veröffentlicht wird).
* under `experimental_authentication`, einer `authenticators` Knoten und einen `rules` -Knoten, bei denen es sich jeweils um Arrays handelt.
* Authentifizierer: Hiermit können Sie einen Typ von Token oder Anmeldeinformationen deklarieren. In diesem Fall handelt es sich dabei um einen Edge-Schlüssel.  Dieser umfasst die folgenden Eigenschaften:
   * name – eine beschreibende Zeichenfolge.
   * type - must be `edge`.
   * edgeKey1 - der Wert der *X-AEM-Edge-Key*, das auf ein geheimes Token verweisen muss, das nicht in Git gespeichert, sondern als [Cloud Manager-Umgebungsvariable](/help/implementing/cloud-manager/environment-variables.md) des Typs &quot;secret&quot;. Wählen Sie für das Feld „Angewendeter Service“ die Option „Alle“ aus. Es wird empfohlen, dass der Wert (z. B.`${{CDN_EDGEKEY_052824}}`) den Tag widerspiegelt, an dem er hinzugefügt wurde.
   * edgeKey2 – wird für die Rotation von Geheimnissen verwendet, die unten im Abschnitt [Rotieren von Geheimnissen](#rotating-secrets) beschrieben ist. Definieren Sie es ähnlich wie edgeKey1. Von `edgeKey1` und `edgeKey2` muss mindestens einer deklariert werden.
<!--   * OnFailure - defines the action, either `log` or `block`, when a request doesn't match either `edgeKey1` or `edgeKey2`. For `log`, request processing will continue, while `block` will serve a 403 error. The `log` value is useful when testing a new token on a live site since you can first confirm that the CDN is correctly accepting the new token before changing to `block` mode; it also reduces the chance of lost connectivity between the customer CDN and the Adobe CDN, as a result of an incorrect configuration. -->
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet werden sollen, und ob es sich um die Veröffentlichungs- und/oder die Vorschaustufe handelt.   Folgendes ist enthalten:
   * name – eine beschreibende Zeichenfolge.
   * when – eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax im Artikel [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) beurteilt werden soll. Typischerweise umfasst dies einen Vergleich der aktuellen Stufe (z. B. die Veröffentlichungsstufe), sodass der gesamte Live-Traffic beim Routing über das Kunden-CDN validiert wird.
   * action – muss „authenticate“ angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird.

>[!NOTE]
>Der Edge-Schlüssel muss als [Cloud Manager-Umgebungsvariable](/help/implementing/cloud-manager/environment-variables.md) Typvariable `secret` (mit *Alle* ausgewählt für Dienst angewendet), bevor die Konfiguration, auf die sie verweist, bereitgestellt wird.

## API-Bereinigungs-Token {#purge-API-token}

Kundinnen und Kunden können [den CDN-Cache mithilfe eines deklarierten API-Bereinigungs-Tokens bereinigen](/help/implementing/dispatcher/cdn-cache-purge.md). Das Token wird mit der unten stehenden Syntax deklariert.   Im Abschnitt [Allgemeine Einrichtung](#common-setup) erfahren Sie, wie Sie es bereitstellen.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
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

Die Syntax enthält:

* Art, Version und Metadaten.
* Datenknoten, der einen untergeordneten Knoten `experimental_authentication` enthält (das experimentelle Präfix wird entfernt, wenn die Funktion veröffentlicht wird).
* under `experimental_authentication`, einer `authenticators` Knoten und einen `rules` -Knoten, bei denen es sich jeweils um Arrays handelt.
* Authentifizierer: Hiermit können Sie einen Token-Typ oder Anmeldeinformationen deklarieren. In diesem Fall handelt es sich hierbei um einen Bereinigungsschlüssel. Dieser umfasst die folgenden Eigenschaften:
   * name – eine beschreibende Zeichenfolge.
   * type – muss „purge“ sein.
   * edgeKey1 – sein Wert muss auf ein geheimes Token verweisen, das nicht in Git gespeichert, sondern als [Cloud Manager-Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md) des Typs `secret` deklariert werden sollte. 
   * Wählen Sie für das Feld „Angewendeter Service“ die Option „Alle“ aus. Es wird empfohlen, dass der Wert (z. B.`${{CDN_PURGEKEY_031224}}`) den Tag widerspiegelt, an dem er hinzugefügt wurde.
   * purgeKey2 – wird für die Rotation von Geheimnissen verwendet, die unten im Abschnitt [Rotieren von Geheimnissen](#rotating-secrets) beschrieben wird. Von `purgeKey1` und `purgeKey2` muss mindestens einer deklariert werden.
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet werden sollen, und ob es sich um die Veröffentlichungs- und/oder die Vorschaustufe handelt.   Folgendes ist enthalten:
   * name – eine beschreibende Zeichenfolge
   * when – eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax im Artikel [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) beurteilt werden soll. Typischerweise umfasst dies einen Vergleich der aktuellen Stufe (z. B. die Veröffentlichungsstufe).
   * action – muss „authenticate“ angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird.

>[!NOTE]
>Der Edge Key muss als [Cloud Manager-Umgebungsvariable](/help/implementing/cloud-manager/environment-variables.md) des Typs `secret` konfiguriert werden, bevor die Konfiguration, die auf ihn verweist, bereitgestellt wird.

## Standardauthentifizierung {#basic-auth}

Protect bestimmte Inhaltsressourcen durch Aufrufen eines einfachen Authentifizierungsdialogfelds, das einen Benutzernamen und ein Kennwort erfordert. Diese Funktion ist in erster Linie für leichte Authentifizierungsfälle wie die Überprüfung von Inhalten durch Interessengruppen in Unternehmen und nicht als vollständige Lösung für Zugriffsrechte von Endbenutzern gedacht.

Dem Endbenutzer wird ein grundlegendes Authentifizierungsdialogfeld angezeigt, wie das folgende:

![basicauth-dialog](/help/implementing/dispatcher/assets/basic-auth-dialog.png)


Die Syntax wird wie unten beschrieben deklariert. Siehe [Allgemeine Einrichtung](#common-setup) unten finden Sie Informationen zur Bereitstellung.

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

Die Syntax enthält:

* Art, Version und Metadaten.
* einen Daten-Knoten, der eine `experimental_authentication` Knoten (das experimentelle Präfix wird entfernt, wenn die Funktion veröffentlicht wird).
* under `experimental_authentication`, einer `authenticators` Knoten und einen `rules` -Knoten, bei denen es sich jeweils um Arrays handelt.
* Authentifizierer: Deklarieren Sie in diesem Szenario einen einfachen Authentifizierer mit der folgenden Struktur:
   * name – eine beschreibende Zeichenfolge
   * type - must be `basic`
   * ein Array von Anmeldeinformationen, die jeweils die folgenden Name/Wert-Paare enthalten, die Endbenutzer im Dialogfeld für die einfache Authentifizierung eingeben können:
      * user - der Name des Benutzers
      * password - Der Wert muss auf ein geheimes Token verweisen, das nicht in Git gespeichert, sondern als Cloud Manager-Umgebungsvariablen des Typs &quot;secret&quot;deklariert werden sollte (mit **Alle** ausgewählt als Dienstfeld)
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet werden soll und welche Ressourcen geschützt werden sollen. Jede Regel umfasst:
   * name – eine beschreibende Zeichenfolge
   * when – eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax im Artikel [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) beurteilt werden soll. Normalerweise enthält es einen Vergleich der Veröffentlichungsstufe oder bestimmter Pfade.
   * action - muss &quot;authenticate&quot;angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird, der für dieses Szenario eine einfache Authentifizierung ist.

>[!NOTE]
>Der Edge Key muss als [Cloud Manager-Umgebungsvariable](/help/implementing/cloud-manager/environment-variables.md) des Typs `secret` konfiguriert werden, bevor die Konfiguration, die auf ihn verweist, bereitgestellt wird.

## Allgemeine Einrichtung {#common-setup}

Alle Authentifizierer werden wie folgt eingerichtet:

* Erstellen Sie zunächst den folgenden Ordner und die Dateistruktur im obersten Ordner Ihres Git-Projekts:

```
config/
     cdn.yaml
```

* Zweitens sollte die Konfigurationsdatei `cdn.yaml` die Knoten enthalten, die in den folgenden Beispielen beschrieben sind. Die Eigenschaft `kind` sollte auf `CDN` gesetzt sein und die Version auf die Schemaversion eingestellt sein, die derzeit `1` ist. Der Metadatenknoten verfügt über die Eigenschaft „envTypes“, die angibt, für welche Umgebungstypen (dev, stage, prod) diese Konfiguration ausgewertet wird.

* Erstellen Sie abschließend eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager. Siehe [Konfigurieren von Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

Beachten Sie Folgendes:

* RDEs unterstützen derzeit nicht die Konfigurations-Pipeline.
* Sie können `yq` verwenden, um die YAML-Formatierung Ihrer Konfigurationsdatei lokal zu überprüfen (z. B. `yq cdn.yaml`).

## Rotieren von Geheimnissen {#rotating-secrets}

Es gilt als gute Sicherheitspraxis, die Anmeldeinformationen gelegentlich zu ändern. Dies kann wie unten dargestellt mithilfe des Beispiels eines Edge Keys erreicht werden, wobei dieselbe Strategie auch für Bereinigungsschlüssel verwendet wird.

* Zunächst wurde nur `edgeKey1` definiert, der in diesem Fall als `${{CDN_EDGEKEY_052824}}` referenziert wird, was als empfohlene Konvention das Erstellungsdatum widerspiegelt.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
```

* Wenn Sie den Schlüssel rotieren müssen, erstellen Sie ein neues Cloud Manager-Geheimnis, z. B. `${{CDN_EDGEKEY_041425}}`.
* Verweisen Sie in der Konfiguration von `edgeKey2` darauf und stellen Sie es bereit.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Sobald Sie sicher sind, dass der alte Edge Key nicht mehr verwendet wird, entfernen Sie ihn, indem Sie `edgeKey1` aus der Konfiguration entfernen.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Löschen Sie die Referenz des alten Geheimnisses (`${{CDN_EDGEKEY_052824}}`) aus Cloud Manager aus und nehmen Sie die Bereitstellung vor.
* Wenn Sie für die nächste Rotation bereit sind, gehen Sie analog vor. Diesmal fügen Sie jedoch `edgeKey1` zu der Konfiguration hinzu, indem Sie auf ein neues Cloud Manager-Umgebungsgeheimnis verweisen, das beispielsweise den Namen `${{CDN_EDGEKEY_031426}}` hat.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
      edgeKey1: ${{CDN_EDGEKEY_031426}}
```
