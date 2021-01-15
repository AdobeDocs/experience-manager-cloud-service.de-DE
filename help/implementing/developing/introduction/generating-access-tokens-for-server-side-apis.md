---
title: Erstellen von Zugriffstoken für serverseitige APIs
description: Erfahren Sie, wie Sie die Kommunikation zwischen einem Drittanbieter-Server und AEM als Cloud Service durch Generieren eines sicheren JWT-Tokens erleichtern.
translation-type: tm+mt
source-git-commit: a8cb0c1bf2cdc741173e83ad00b6453931a8df18
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---


# Einführung {#introduction}

>[!IMPORTANT]
>
>Diese Funktion ist noch nicht verfügbar. Eine aktuelle Liste der Funktionen finden Sie in den [Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

Einige Architekturen sind darauf angewiesen, AEM als Cloud Service von einer Anwendung aufzurufen, die auf einem Server außerhalb AEM Infrastruktur gehostet wird. Beispielsweise eine Mobilanwendung, die einen Server aufruft und dann API-Anfragen als Cloud Service AEM.

Der Server-zu-Server-Fluss wird unten beschrieben, zusammen mit einem vereinfachten Fluss für die Entwicklung. Der AEM als Cloud Service [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) wird verwendet, um Token zu generieren, die für den Authentifizierungsprozess benötigt werden.

## Der Server-zu-Server-Fluss {#the-server-to-server-flow}

Ein Benutzer mit der Administratorrolle kann eine AEM als Berechtigung für Cloud Service generieren, die auf dem Server installiert werden sollte und sorgfältig als geheimer Schlüssel behandelt werden sollte. Diese JSON-Formatdatei enthält alle Daten, die zur Integration mit einer AEM als Cloud Service-API erforderlich sind. Die Daten werden zum Erstellen eines signierten JWT-Tokens verwendet, das mit IMS für ein IMS-Zugriffstoken ausgetauscht wird. Dieses Zugriffstoken kann dann als Interaktionskennzeichen verwendet werden, um Anforderungen an AEM als Cloud Service zu stellen.

Der Server-zu-Server-Fluss umfasst die folgenden Schritte:

* Rufen Sie den AEM als Cloud Service-Anmeldeinformationen von der Developer Console ab.
* Installieren Sie das AEM als Cloud Service-Anmeldeinformationen auf einem Nicht-AEM-Server, der Aufrufe an AEM
* Erstellen Sie ein JWT-Token und tauschen Sie dieses Token mit den IMS-APIs der Adobe für ein Zugriffstoken aus
* Aufrufen der AEM-API mit dem Zugriffstoken als Interaktionsauthentifizierungstoken

### Abrufen des AEM als Cloud Service-Anmeldeinformationen {#fetch-the-aem-as-a-cloud-service-credentials}

Benutzer mit der Administratorrolle für ein IMS-Unternehmen sehen die Registerkarte Integrationen in der Developer Console für eine bestimmte Umgebung sowie zwei Schaltflächen. Wenn Sie auf die Schaltfläche **Dienstberechtigungen abrufen** klicken, werden die Dienstberechtigungen generiert. Diese enthalten alle für den Nicht-AEM-Server erforderlichen Informationen, einschließlich Client-ID, Clientgeheimnis, privater Schlüssel, Zertifikat und Konfiguration für Autoren- und Veröffentlichungsstufen der Umgebung, unabhängig von der Pod-Auswahl.

![JWT-Erzeugung](assets/JWTtoken3.png)

Die Ausgabe ähnelt der folgenden:

```
{
  "ok": true,
  "integration": {
    "imsEndpoint": "ims-na1.adobelogin.com",
    "metascopes": "ent_aem_cloud_sdk,ent_cloudmgr_sdk",
    "technicalAccount": {
      "clientId": "cm-p123-e1234",
      "clientSecret": "4AREDACTED17"
    },
    "email": "abcd@techacct.adobe.com",
    "id": "ABCDAE10A495E8C@techacct.adobe.com",
    "org": "1234@AdobeOrg",
    "privateKey": "-----BEGIN RSA PRIVATE KEY-----\r\REDACTED\r\n==\r\n-----END RSA PRIVATE KEY-----\r\n",
    "publicKey": "-----BEGIN CERTIFICATE-----\r\nREDACTED\r\n-----END CERTIFICATE-----\r\n"
  },
  "statusCode": 200
}
```

### Installieren Sie die AEM Dienstberechtigungen auf einem Nicht-AEM-Server {#install-the-aem-service-credentials-on-a-non-aem-server}

Die AEM, die AEM aufrufen, sollten in der Lage sein, auf die AEM als Anmeldedaten des Cloud Service zuzugreifen, und sie als geheim behandeln.

### Erstellen Sie ein JWT-Token und tauschen Sie es für ein Zugriffstoken{#generate-a-jwt-token-and-exchange-it-for-an-access-token} aus.

Verwenden Sie die Anmeldeinformationen, um ein JWT-Token in einem Aufruf des IMS-Dienstes der Adobe zu erstellen, um ein Zugriffstoken abzurufen, das 24 Stunden gültig ist.

Die AEM-CS-Dienstberechtigungen können mithilfe von zu diesem Zweck eingerichteten Client-Bibliotheken für ein Zugriffstoken ausgetauscht werden. Die Client-Bibliotheken sind im öffentlichen GitHub-Repository der Adobe [verfügbar, das detailliertere Anleitungen und aktuelle Informationen enthält.](https://github.com/adobe/aemcs-api-client-lib)

```
/*jshint node:true */
"use strict";

const fs = require('fs');
const exchange = require("@adobe/aemcs-api-client-lib");

const jsonfile = "aemcs-service-credentials.json";

var config = JSON.parse(fs.readFileSync(jsonfile, 'utf8'));
exchange(config).then(accessToken => {
    // output the access token in json form including when it will expire.
    console.log(JSON.stringify(accessToken,null,2));
}).catch(e => {
    console.log("Failed to exchange for access token ",e);
});
```

Derselbe Austausch kann in jeder Sprache durchgeführt werden, die ein signiertes JWT-Token mit dem richtigen Format generieren und die IMS Token Exchange-APIs aufrufen kann.

Das Zugriffstoken legt fest, wann es abläuft, was in der Regel 12 Stunden beträgt. Es gibt Beispielcode im Git-Repository, um ein Zugriffstoken zu verwalten und zu aktualisieren, bevor es abläuft.

### Aufrufen der AEM-API {#calling-the-aem-api}

Nehmen Sie die entsprechenden Server-zu-Server-API-Aufrufe an eine AEM als Cloud Service-Umgebung vor, einschließlich des Zugriffstokens im Header. Verwenden Sie daher für den Header &quot;Autorisierung&quot;den Wert `"Bearer <access_token>"`. Beispiel:`curl`

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

## Entwicklerfluss {#developer-flow}

Entwickler möchten wahrscheinlich eine Entwicklungsinstanz ihrer Nicht-AEM-Anwendung testen (entweder auf ihrem Laptop ausgeführt oder gehostet), die Anforderungen an eine Entwicklungs-AEM als Cloud Service-dev-Umgebung stellt. Da Entwickler jedoch nicht unbedingt als Cloud Service-Dev-Umgebung Zugriff auf die AEM haben, können wir nicht davon ausgehen, dass sie den im normalen Server-zu-Server-Fluss beschriebenen JWT-Träger generieren können. So bieten wir einem Entwickler einen Mechanismus, um ein Zugriffstoken direkt zu generieren, das in Anforderungen zur AEM als Cloud Service-Umgebung verwendet werden kann, auf die er Zugriff hat.

Informationen zu den erforderlichen Berechtigungen zur Verwendung des AEM als Cloud Service-Entwicklerkonsole finden Sie in der Dokumentation zu [Entwicklerrichtlinien](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
>
>Das Token ist 24 Stunden gültig, danach muss es mit derselben Methode neu generiert werden.

Entwickler können dieses Token verwenden, um Aufrufe von ihrer Nicht-AEM-Testanwendung an eine AEM als Cloud Service-Umgebung durchzuführen. Normalerweise verwendet der Entwickler dieses Token mit der Nicht-AEM-Anwendung auf seinem eigenen Laptop. Außerdem ist die AEM als Cloud normalerweise eine Nicht-Produktions-Umgebung.

Der Entwicklerfluss umfasst die folgenden Schritte:

* Erstellen eines Zugriffstokens über die Developer Console
* Rufen Sie die AEM Anwendung mit dem Zugriffstoken auf.

Entwickler können auch API-Aufrufe an ein AEM Projekt auf ihrem lokalen Computer durchführen. In diesem Fall ist kein Zugriffstoken erforderlich.

### Generieren des Zugriffstokens {#generating-the-access-token}

Klicken Sie in der Developer Console auf die Schaltfläche **Lokales Entwicklungstoken abrufen**, um ein Zugriffstoken zu generieren.

### Rufen Sie dann AEM Anwendung mit einem Zugriffstoken {#call-the-aem-application-with-an-access-token} auf

Führen Sie die entsprechenden Server-zu-Server-API-Aufrufe von der Nicht-AEM-Anwendung zu einer AEM als Cloud Service-Umgebung durch, einschließlich des Zugriffstokens im Header. Verwenden Sie daher für den Header &quot;Autorisierung&quot;den Wert `"Bearer <access_token>"`.

## Dienstanmeldeinformationen - Widerruf {#service-credentials-revocation}

Bitte senden Sie eine Anfrage an den Kundensupport, wenn das JWT-Inhabertoken widerrufen werden muss.