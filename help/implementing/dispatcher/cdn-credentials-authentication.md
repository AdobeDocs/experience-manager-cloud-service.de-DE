---
title: Konfigurieren von CDN-Anmeldeinformationen und Authentifizierung
description: Erfahren Sie, wie Sie CDN-Anmeldeinformationen und die Authentifizierung konfigurieren, indem Sie Regeln in einer Konfigurationsdatei deklarieren, die dann mithilfe der Cloud Manager-Konfigurationspipeline bereitgestellt wird.
feature: Dispatcher
source-git-commit: ee993798739232da794dbf7ff0a643ca93effa7d
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 3%

---

# Konfigurieren von CDN-Anmeldeinformationen und Authentifizierung {#cdn-credentials-authentication}

>[!NOTE]
>Diese Funktion ist noch nicht allgemein verfügbar.  Um dem Programm für frühe Anwender beizutreten, senden Sie eine E-Mail `aemcs-cdn-config-adopter@adobe.com`.

Das von Adobe bereitgestellte CDN verfügt über mehrere Funktionen und Dienste, von denen einige auf Anmeldeinformationen und Authentifizierung angewiesen sind, um ein angemessenes Maß an Unternehmenssicherheit zu gewährleisten. Durch Deklarieren von Regeln in einer Konfigurationsdatei, die mithilfe der Variablen [Cloud Manager-Konfigurations-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline), können Kunden Folgendes auf Self-Service-Weise konfigurieren:

* Der HTTP-Header-Wert, der vom Adobe CDN verwendet wird, um Anforderungen zu überprüfen, die von einem kundenverwalteten CDN stammen.
* Das API-Token, mit dem Ressourcen im CDN-Cache gelöscht werden.

Jede dieser Optionen, einschließlich der Konfigurationssyntax, wird im eigenen Abschnitt unten beschrieben. Die [Allgemeine Einrichtung](#common-setup) -Abschnitt erläutert die beiden allgemeinen Einstellungen sowie die Implementierung. Schließlich gibt es einen Abschnitt darüber, wie [rotate keys](#rotating-secrets), die als gute Sicherheitspraxis betrachtet wird.

## Vom Kunden verwalteter CDN-HTTP-Header-Wert {#CDN-HTTP-value}

Wie im Abschnitt [CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) -Seite können Kunden festlegen, dass Traffic über ihr eigenes CDN weitergeleitet wird, das als Kunden-CDN (auch manchmal als BYOCDN bezeichnet) bezeichnet wird.

Im Rahmen des Setups müssen sich das Adobe CDN und das Kunden-CDN auf einen Wert der `X-AEM-Edge-Key` HTTP-Kopfzeile. Dieser Wert wird bei jeder Anfrage im Kunden-CDN festgelegt, bevor er an das Adobe-CDN weitergeleitet wird. Dadurch wird überprüft, ob der Wert erwartungsgemäß ist. Dadurch kann er anderen HTTP-Headern vertrauen, einschließlich jenen, die dazu beitragen, die Anfrage an den entsprechenden AEM weiterzuleiten.

Die `X-AEM-Edge-Key` -Wert mit der unten stehenden Syntax deklariert. Siehe [Allgemeine Einrichtung](#common-setup) -Abschnitt, um zu erfahren, wie Sie ihn bereitstellen.

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
        onFailure: log # optional, default: log, enum: log/block
    rules:
      - name: edge-auth-rule
        when: { reqProperty: tier, equals: "publish" }
        action:
          type: authenticate
          authenticator: edge-auth
```

Die Syntax für die `X-AEM-Edge-Key` enthält:

* Art, Version und Metadaten.
* Daten-Node, die ein untergeordnetes Element enthält `experimental_authentication` Knoten (das experimentelle Präfix wird entfernt, wenn die Funktion veröffentlicht wird).
* Unter experimental_authentication mit einem Authentifizierungsknoten und einem Regelknoten, die beide Arrays sind.
* Authentifizierer: Hiermit können Sie einen Token- oder Berechtigungstyp deklarieren, bei dem es sich in diesem Fall um einen Edge-Schlüssel handelt. Es enthält die folgenden Eigenschaften:
   * name - eine beschreibende Zeichenfolge.
   * type - muss edge sein.
   * edgeKey1 - sein Wert muss auf ein geheimes Token verweisen, das nicht in Git gespeichert, sondern als [Cloud Manager-Umgebungsvariable](/help/implementing/cloud-manager/environment-variables.md) des Typs &quot;secret&quot;. Wählen Sie für das Feld Dienst angewendet die Option Alle aus. Es wird empfohlen, dass der Wert (z. B.`${{CDN_EDGEKEY_052824}}`) spiegelt den Tag wider, an dem es hinzugefügt wurde.
   * edgeKey2 - wird für die Drehung von Geheimnissen verwendet, die im Abschnitt [Rotationsseitenabschnitt](#rotating-secrets) unten. Mindestens eines von `edgeKey1` und `edgeKey2` müssen deklariert werden.
   * OnFailure - definiert die Aktion, entweder `log` oder `block`, wenn eine Anforderung `edgeKey1` oder `edgeKey2`. Für `log`, wird die Anforderungsverarbeitung fortgesetzt, während `block` wird einen 403-Fehler bedienen. Die `log` -Wert ist beim Testen eines neuen Tokens auf einer Live-Site nützlich, da Sie zunächst bestätigen können, dass das CDN das neue Token korrekt akzeptiert, bevor Sie zu `block` -Modus; es verringert auch die Wahrscheinlichkeit, dass die Verbindung zwischen dem Kunden-CDN und dem Adobe-CDN aufgrund einer fehlerhaften Konfiguration unterbrochen wird.
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet werden soll und ob es sich um die Veröffentlichungs- und/oder die Vorschaustufe handelt.  Er umfasst:
   * name - eine beschreibende Zeichenfolge.
   * when - eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax in der [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) Artikel. In der Regel enthält es einen Vergleich der aktuellen Ebene (z. B. &quot;publish&quot;), sodass der gesamte Live-Traffic als Routing über das Kunden-CDN validiert wird.
   * action - muss &quot;authenticate&quot;angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird.

>[!NOTE]
>Der Edge-Schlüssel muss als [Cloud Manager-Umgebungsvariable](/help/implementing/cloud-manager/environment-variables.md) Typvariable `secret`, bevor die Konfiguration, auf die sie verweist, bereitgestellt wird.

## API-Token bereinigen {#purge-API-token}

Kunden können den CDN-Cache mithilfe eines deklarierten Bereinigungs-API-Tokens bereinigen. Das Token wird mit der unten stehenden Syntax deklariert.  Siehe [Allgemeine Einrichtung](#common-setup) -Abschnitt, um zu erfahren, wie Sie ihn bereitstellen.

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
* Datenknoten, der ein untergeordnetes Element enthält `experimental_authentication` Knoten (das experimentelle Präfix wird entfernt, wenn die Funktion veröffentlicht wird).
* under `experimental_authentication`, mit einem einzigen Authentifizierungsknoten.
* Authentifizierer: Hiermit können Sie einen Token- oder Berechtigungstyp deklarieren, bei dem es sich in diesem Fall um einen Bereinigungsschlüssel handelt. Es enthält die folgenden Eigenschaften:
   * name - eine beschreibende Zeichenfolge.
   * type - must be purge.
   * purgeKey1 - sein Wert muss auf ein geheimes Token verweisen, das nicht in Git gespeichert, sondern als [Cloud Manager-Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md) des Typs `secret`.
   * Wählen Sie für das Feld Dienst angewendet die Option Alle aus. Es wird empfohlen, dass der Wert (z. B. `${{CDN_PURGEKEY_031224}}`) spiegelt den Tag wider, an dem es hinzugefügt wurde.
   * purgeKey2 - wird für die Rotation von Geheimnissen verwendet, die im Abschnitt [Rotationsseitenabschnitt](#rotating-secrets) unten. Mindestens eines von `purgeKey1` und `purgeKey2` müssen deklariert werden.
* Regeln: Hier können Sie angeben, welche der Authentifizierer verwendet werden soll und ob es sich um die Veröffentlichungs- und/oder die Vorschaustufe handelt.  Er umfasst:
   * name - eine beschreibende Zeichenfolge
   * when - eine Bedingung, die bestimmt, wann die Regel gemäß der Syntax in der [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) Artikel. Normalerweise enthält es einen Vergleich der aktuellen Ebene (z. B. Veröffentlichen).
   * action - muss &quot;authenticate&quot;angeben, wobei auf den vorgesehenen Authentifizierer verwiesen wird.

>[!NOTE]
>Der Edge-Schlüssel muss als [Cloud Manager-Umgebungsvariable](/help/implementing/cloud-manager/environment-variables.md) Typvariable `secret`, bevor die Konfiguration, auf die sie verweist, bereitgestellt wird.

## Allgemeine Einrichtung {#common-setup}

Alle Authentifizierer werden wie folgt eingerichtet:

* Erstellen Sie zunächst den folgenden Ordner und die Dateistruktur im Ordner der obersten Ebene Ihres Git-Projekts:

```
config/
     cdn.yaml
```

* Zweitens, die `cdn.yaml` Die Konfigurationsdatei sollte die Knoten enthalten, die in den Beispielen unten beschrieben sind. Die `kind` -Eigenschaft auf `CDN` und die Version auf die Schemaversion eingestellt werden sollte, die derzeit `1`. Der Metadatenknoten verfügt über die Eigenschaft &quot;envTypes&quot;, die angibt, für welche Umgebungstypen (dev, stage, prod) diese Konfiguration ausgewertet wird.

* Erstellen Sie abschließend eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager. Siehe [Konfigurieren von Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

Beachten Sie Folgendes:

* RDEs unterstützen derzeit nicht die Konfigurations-Pipeline.
* Sie können `yq` verwenden, um die YAML-Formatierung Ihrer Konfigurationsdatei lokal zu überprüfen (z. B. `yq cdn.yaml`).

## Geheimnisse drehen {#rotating-secrets}

Es empfiehlt sich, die Anmeldeinformationen gelegentlich zu ändern. Dies kann wie unten dargestellt mithilfe des Beispiels eines Edge-Schlüssels erreicht werden, obwohl dieselbe Strategie für Bereinigungsschlüssel verwendet wird.

* Zunächst nur `edgeKey1` wurde definiert, in diesem Fall wurde als `${{CDN_EDGEKEY_052824}}`, die als empfohlene Konvention das Erstellungsdatum widerspiegelt.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
```

* Wenn Sie den Schlüssel drehen müssen, erstellen Sie ein neues Cloud Manager-Geheimnis, z. B. `${{CDN_EDGEKEY_041425}}`.
* Verweisen Sie in der Konfiguration auf `edgeKey2` und bereitstellen.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Sobald Sie sicher sind, dass der alte Kantenschlüssel nicht mehr verwendet wird, entfernen Sie ihn, indem Sie ihn entfernen `edgeKey1` aus der Konfiguration.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Löschen Sie die alte geheime Referenz (`${{CDN_EDGEKEY_052824}}`) von Cloud Manager aus und stellen Sie sie bereit.
* Wenn Sie für die nächste Rotation bereit sind, gehen Sie analog vor. Diesmal fügen Sie jedoch `edgeKey1` auf die Konfiguration zu verweisen, indem beispielsweise ein neuer Cloud Manager-Umgebungs-Geheimnis mit dem Namen `${{CDN_EDGEKEY_031426}}`.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
      edgeKey1: ${{CDN_EDGEKEY_031426}}
```
