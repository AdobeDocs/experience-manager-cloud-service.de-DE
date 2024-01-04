---
title: Lokale AEM mit dem universellen Editor
description: Erfahren Sie, wie der universelle Editor die Bearbeitung lokaler AEM-Instanzen zu Entwicklungszwecken unterstützt.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
source-git-commit: 16f2922a3745f9eb72f7070c30134e5149eb78ce
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---


# Lokale AEM mit dem universellen Editor {#local-dev-ue}

Erfahren Sie, wie der universelle Editor die Bearbeitung lokaler AEM-Instanzen zu Entwicklungszwecken unterstützt.

{{universal-editor-status}}

## Übersicht {#overview}

In diesem Dokument wird beschrieben, wie Sie AEM in HTTPS zusammen mit einer lokalen Kopie des Universal Editor-Dienstes ausführen, damit Sie mit dem universellen Editor lokal AEM entwickeln können.

## Einrichten von AEM für die Ausführung auf HTTPS {#aem-https}

Innerhalb eines äußeren Rahmens, der mit HTTPS gesichert ist, kann kein unsicherer HTTP-Frame geladen werden. Der Universal Editor-Dienst wird unter HTTPS ausgeführt, weshalb AEM oder jede andere Remote-Seite auch unter HTTPS ausgeführt werden muss.

Dazu müssen Sie AEM für die Ausführung auf HTTPS einrichten. Zu Entwicklungszwecken können Sie ein selbstsigniertes Zertifikat verwenden.

In diesem Dokument erfahren Sie, wie Sie AEM, die auf HTTPS ausgeführt werden, einrichten, einschließlich eines selbstsignierten Zertifikats, das Sie verwenden können.

## Installieren des Universal Editor-Dienstes {#install-ue-service}

Der universelle Editor-Dienst bindet den universellen Editor und das Backend-System. Da der offizielle universelle Editor-Dienst global gehostet wird, muss Ihre lokale AEM-Instanz dem Internet zugänglich gemacht werden. Um dies zu vermeiden, können Sie eine lokale Kopie des Universal Editor-Dienstes ausführen.

[NodeJS, Version 16](https://nodejs.org/en/download/releases) ist erforderlich, um eine lokale Kopie des Universal Editor Service auszuführen.

Der Universal Editor Service wird direkt von AEM Engineering vertrieben. Kontaktieren Sie Ihren Ingenieur im VIP Programm für eine lokale Kopie.

Das Engineering bietet Ihnen eine `universal-editor-service.cjs` -Datei. Speichern Sie diese in Ihrer lokalen Entwicklungsumgebung.

## Erstellen eines Zertifikats zum Ausführen des Universal Editor-Dienstes mit HTTPS {#ue-https}

Für den universellen Editor-Dienst ist auch ein Zertifikat erforderlich, das in Ihrer Entwicklungsumgebung unter HTTPS ausgeführt werden kann.

Führen Sie den folgenden Befehl aus.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

Der Befehl generiert eine `key.pem` und `certificate.pem` -Datei. Speichern Sie diese Dateien in demselben Pfad wie Ihre `universal-editor-service.cjs` -Datei.

## Einrichten der Konfiguration des Universal Editor Service {#setting-up-service}

In NodeJS müssen eine Reihe von Umgebungsvariablen festgelegt sein, damit der Universal Editor Service lokal ausgeführt werden kann.

Auf demselben Pfad wie Ihre `universal-editor-service.cjs`, `key.pem` und `certificate.pem` -Dateien, erstellen Sie eine `.env` -Datei mit dem folgenden Inhalt.

```text
EXPRESS_PORT=8000
EXPRESS_PRIVATE_KEY=./key.pem
EXPRESS_CERT=./certificate.pem
NODE_TLS_REJECT_UNAUTHORIZED=0
```

Die -Variable hat die folgende Bedeutung:

* `EXPRESS_PORT`: Definiert, welchen Anschluss der Universal Editor-Dienst abruft.
* `EXPRESS_PRIVATE`: Verweist auf Ihre [zuvor erstellter privater Schlüssel,](#ue-https) `key.pem`
* `EXPRESS_CERT`: Verweist auf Ihre [zuvor erstelltes Zertifikat,](#ue-https) `certificate.pem`
* `NODE_TLS_REJECT_UNAUTHORIZED=0`: Akzeptiert selbstsignierte Zertifikate

## Ausführen des Universal Editor-Dienstes {#running-ue}

Führen Sie den folgenden Befehl aus, um den Universal Editor-Dienst zu starten:

```text
$ node ./universal-editor-service.cjs
```

Es sollte Folgendes an Ihr Terminal ausgeben:

```text
Universal Editor Service listening on port 8000 as HTTPS Server
```

Stellen Sie sicher, dass der Dienst den HTTPS-Server und nicht den HTTP-Server startet.

## Verwenden des lokalen Universal Editor-Dienstes anstelle des globalen Dienstes {#using-local-ue}

Der universelle Editor weiß, welchen universellen Editor-Dienst zum Bearbeiten einer Seite verwendet werden soll, basierend darauf, wie die Seite instrumentiert wird. Dies erfolgt über Meta-Tags auf der Seite, die im universellen Editor geladen wird.

Damit eine Seite mit Ihrem lokalen Universal Editor-Dienst bearbeitet werden kann, muss das folgende Meta-Tag festgelegt sein:

```html
<meta name="urn:adobe:aue:config:service" content="https://localhost:8000">
```

Nach der Festlegung sollte jeder Inhaltsaktualisierungsaufruf an `https://localhost:8000` anstelle des standardmäßigen Universal Editor-Dienstes.

>[!TIP]
>
>Weitere Informationen dazu, wie Seiten für die Verwendung des Global Universal Editor Service instrumentiert werden, finden Sie im Dokument [Erste Schritte mit dem Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md#instrument-page)

## Bearbeiten einer Seite mit dem lokalen universellen Editor-Dienst {#editing}

Mit dem [Lokaler Editor-Dienst](#running-ue) und [Inhaltsseite, die für die Verwendung des lokalen Dienstes instrumentiert wurde,](#using-loca-ue) können Sie jetzt den Editor starten.

1. Öffnen Sie den Browser in `https://localhost:8000/`.
1. Wenden Sie Ihren Browser an, um zu akzeptieren [Ihr selbstsigniertes Zertifikat.](#ue-https)
1. Sobald das selbst signierte Zertifikat als vertrauenswürdig eingestuft wurde, können Sie die Seite mit Ihrem lokalen Universal Editor-Dienst bearbeiten.
