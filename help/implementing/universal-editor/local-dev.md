---
title: Ausführen eines eigenen universellen Editordienstes
description: Erfahren Sie, wie Sie Ihren eigenen Universal Editor-Dienst entweder für die lokale Entwicklung oder als Teil Ihrer eigenen Infrastruktur ausführen können.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 4fedb7a812b53fd9ebd9c82e86fa8f05394d464f
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 77%

---


# Ausführen eines eigenen universellen Editordienstes {#local-ue-service}

Erfahren Sie, wie Sie Ihren eigenen Universal Editor-Dienst entweder für die lokale Entwicklung oder als Teil Ihrer eigenen Infrastruktur ausführen können.

## Übersicht {#overview}

Der Dienst „Universeller Editor“ bindet den universellen Editor und das Backend-System zusammen. Um eine lokale Entwicklung für den universellen Editor durchführen zu können, müssen Sie eine lokale Kopie des Dienstes „Universeller Editor“ ausführen. Der Grund hierfür ist Folgender:

* Der offizielle Dienst „Universeller Editor“ von Adobe wird global gehostet, und Ihre lokale AEM-Instanz würde so dem Internet ausgesetzt werden.
* Bei der Entwicklung mit einem lokalen AEM SDK ist der Zugriff auf den Dienst „Universeller Editor“ von Adobe über das Internet nicht möglich.
* Wenn Ihre AEM-Instanz IP-Beschränkungen aufweist und sich der Dienst „Universeller Editor“ von Adobe nicht in einem definierten IP-Bereich befindet, können Sie ihn selbst hosten.

## Anwendungsfälle {#use-cases}

Ihre eigene Kopie des Universal Editor-Dienstes ist nützlich, wenn Sie:

* Lokales Entwickeln auf AEM für die Verwendung mit dem universellen Editor.
* Führen Sie Ihren eigenen Universal Editor-Dienst als Teil der eigenen Infrastruktur aus, unabhängig von Adobe Universal Editor Service.

Beide Anwendungsfälle werden unterstützt. In diesem Dokument wird beschrieben, wie Sie AEM in HTTPS zusammen mit einer lokalen Kopie des Universal Editor-Dienstes ausführen.

Wenn Sie Ihren eigenen Universal Editor-Dienst als Teil Ihrer eigenen Infrastruktur ausführen möchten, gehen Sie analog zum lokalen Entwicklungsbeispiel vor.

## Einrichten von AEM für die Ausführung auf HTTPS {#aem-https}

Innerhalb eines mit HTTPS gesicherten äußeren Rahmens kann kein unsicherer HTTP-Frame geladen werden. Der Dienst „Universeller Editor“ wird auf HTTPS ausgeführt, weshalb AEM oder jede andere Remote-Seite auch auf HTTPS ausgeführt werden muss.

Dazu müssen Sie AEM für die Ausführung auf HTTPS einrichten. Zu Entwicklungszwecken können Sie ein selbstsigniertes Zertifikat verwenden.

[In diesem Dokument](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html?lang=de) erfahren Sie, wie Sie AEM einrichten, das auf HTTPS ausgeführt wird, einschließlich eines selbstsignierten Zertifikats, das Sie verwenden können.

## Installieren des Dienstes „Universeller Editor“ {#install-ue-service}

Der Dienst „Universeller Editor“ ist keine vollständige Kopie des universellen Editors, sondern nur eine Teilmenge seiner Funktionen, um sicherzustellen, dass Aufrufe aus Ihrer lokalen AEM-Umgebung nicht über das Internet weitergeleitet werden, sondern von einem definierten Endpunkt, den Sie steuern.

[NodeJS Version 20](https://nodejs.org/en/download/releases) ist erforderlich, um eine lokale Kopie des Dienstes „Universeller Editor“ auszuführen.

Der Dienst „Universeller Editor“ ist über die Software-Verteilung verfügbar. In der [Dokumentation zur Software-Verteilung](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de) finden Sie weitere Informationen zum Zugriff darauf.

Speichern Sie die Datei `universal-editor-service.cjs` von der Software-Verteilung in Ihrer lokalen Entwicklungsumgebung.

## Erstellen eines Zertifikats zum Ausführen des Dienstes „Universeller Editor“ mit HTTPS {#ue-https}

Für den Dienst „Universeller Editor“ ist auch ein Zertifikat erforderlich, das in Ihrer Entwicklungsumgebung auf HTTPS ausgeführt werden kann.

Führen Sie den folgenden Befehl aus.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

Der Befehl generiert eine Datei `key.pem` und eine Datei `certificate.pem`. Speichern Sie diese Dateien unter demselben Pfad wie Ihre Datei `universal-editor-service.cjs`.

## Einrichten der Konfiguration des Dienstes „Universeller Editor“ {#setting-up-service}

In NodeJS müssen eine Reihe von Umgebungsvariablen festgelegt sein, damit der Dienst „Universeller Editor“ lokal ausgeführt werden kann.

Erstellen Sie unter demselben Pfad wie die Dateien `universal-editor-service.cjs`, `key.pem` und `certificate.pem` eine Datei `.env` mit dem folgenden Inhalt.

```text
UES_PORT=8000
UES_PRIVATE_KEY=./key.pem
UES_CERT=./certificate.pem
UES_TLS_REJECT_UNAUTHORIZED=false
UES_CORS_PRIVATE_NETWORK=true
```

Dies sind die Mindestwerte, die für die lokale Entwicklung in unserem Beispiel erforderlich sind.

>[!NOTE]
>
>Wenn Sie Chrome-Version 130+ ausführen, müssen Sie das Senden von CORS-Kopfzeilen für den privaten Netzwerkzugriff [1} mithilfe der Option `UES_CORS_PRIVATE_NETWORK` aktivieren.](https://wicg.github.io/private-network-access/#private-network-request)


In der folgenden Tabelle sind diese und zusätzliche Werte aufgeführt.

| Wert | Optional | Standard | Beschreibung |
|---|---|---|---|
| `UES_PORT` | Ja | `8080` | Der Anschluss, an dem der Server ausgeführt wird. |
| `UES_PRIVATE_KEY` | Ja | Kein | Pfad zum privaten Schlüssel für HTTPS-Server |
| `UES_CERT` | Ja | Kein | Pfad zur Zertifizierungsdatei für den HTTPS-Server |
| `UES_TLS_REJECT_UNAUTHORIZED` | Ja | `true` | Ablehnen nicht autorisierter TLS-Verbindungen |
| `UES_DISABLE_IMS_VALIDATION` | Ja | `false` | Deaktivieren der IMS-Validierung |
| `UES_ENDPOINT_MAPPING` | Ja | Leer | Zuordnung der Endpunkte für interne Umschreibungen<br>Beispiel: `UES_ENDPOINT_MAPPING='[{"https://your-public-facing-author-domain.net": "http://10.0.0.1:4502"}]'`<br>Ergebnis: Der Dienst „Universeller Editor“ stellt eine Verbindung zu `http://10.0.0.1:4502` anstelle der bereitgestellten Verbindung `https://your-public-facing-author-domain.net` her. |
| `UES_LOG_LEVEL` | Ja | `info` | Protokollebene für den Server, mögliche Werte sind `silly`, `trace`, `debug`, `verbose`, `info`, `log`, `warn`, `error` und `fatal` |
| `UES_SPLUNK_HEC_URL` | Ja | Kein | HEC-URL für Splunk-Endpunkt |
| `UES_SPLUNK_TOKEN` | Ja | Kein | Splunk-Token |
| `UES_SPLUNK_INDEX` | Ja | Kein | Index zum Schreiben von Protokollen |
| `UES_SPLUNK_SOURCE` | Ja | `universal-editor-service` | Name der Quelle in den Splunk-Protokollen |
| `UES_CORS_PRIVATE_NETWORK` | Ja | `false` | Aktivieren Sie das Senden von CORS-Headern, um das private Netzwerk [zuzulassen.](https://wicg.github.io/private-network-access/#private-network-request) Erforderlich für Benutzer von Chrome Version 130+ |

>[!NOTE]
>
>Vor der [Version 2024.08.13](/help/release-notes/universal-editor/current.md) des universellen Editors waren die folgenden Variablen in der Datei `.env` erforderlich. Diese Werte werden aus Gründen der Abwärtskompatibilität noch bis zum 1. Oktober 2024 unterstützt.
>
>`EXPRESS_PORT=8000`
>`EXPRESS_PRIVATE_KEY=./key.pem`
>`EXPRESS_CERT=./certificate.pem`
>`NODE_TLS_REJECT_UNAUTHORIZED=0`

## Ausführen des Dienstes „Universeller Editor“ {#running-ue}

Führen Sie den folgenden Befehl aus, um den Dienst „Universeller Editor“ zu starten:

```text
$ node ./universal-editor-service.cjs
```

Er sollte Folgendes an Ihr Terminal ausgeben:

```text
Universal Editor Service listening on port 8000 as HTTPS Server
```

Stellen Sie sicher, dass der Dienst den HTTPS-Server und nicht den HTTP-Server startet.

## Verwenden des lokalen Dienstes „Universeller Editor“ anstatt des globalen Dienstes {#using-local-ue}

Der universelle Editor weiß, welcher Dienst „Universeller Editor“ zum Bearbeiten einer Seite verwendet werden soll, basierend darauf, wie die Seite instrumentiert ist. Dies erfolgt über Meta-Tags auf der Seite, die im universellen Editor geladen wird.

Damit eine Seite mit Ihrem lokalen Dienst „Universeller Editor“ bearbeitet werden kann, muss das folgende Meta-Tag festgelegt sein:

```html
<meta name="urn:adobe:aue:config:service" content="https://localhost:8000">
```

Nach der Festlegung sollte jeder Inhaltsaktualisierungsaufruf an `https://localhost:8000` anstelle des standardmäßigen Dienstes „Universeller Editor“ erfolgen.

>[!NOTE]
>
>Der Versuch, direkt auf Ergebnisse von `https://localhost:8000` zuzugreifen, führt zu einem `404`-Fehler. Dies ist das erwartete Verhalten.
>
>Verwenden Sie `https://localhost:8000/corslib/LATEST` zum Testen des Zugriffs auf Ihren lokalen Dienst „Universeller Editor“. Weitere Informationen finden Sie im [nächsten Abschnitt](#editing).

>[!TIP]
>
>Weitere Informationen dazu, wie Seiten für die Verwendung des globalen Dienstes „Universeller Editor“ instrumentiert werden, finden Sie im Dokument [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md#instrument-page)

## Bearbeiten einer Seite mit dem lokalen Dienst „Universeller Editor“ {#editing}

Mit dem [lokal ausgeführten Dienst „Universeller Editor“](#running-ue) und Ihrer [Inhaltsseite, die für die Verwendung des lokalen Dienstes instrumentiert wurde, ](#using-loca-ue)können Sie jetzt den Editor starten.

1. Öffnen Sie in Ihrem Browser `https://localhost:8000/corslib/LATEST`.
1. Weisen Sie Ihren Browser an, um [Ihr selbstsigniertes Zertifikat](#ue-https) zu akzeptieren.
1. Sobald das selbstsignierte Zertifikat als vertrauenswürdig eingestuft wurde, können Sie die Seite mit Ihrem lokalen Dienst „Universeller Editor“ bearbeiten.

