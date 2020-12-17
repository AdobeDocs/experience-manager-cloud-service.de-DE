---
title: Erstellen von Zugriffstoken für serverseitige APIs
description: Erfahren Sie, wie Sie die Kommunikation zwischen einem Drittanbieter-Server und AEM als Cloud Service durch Generieren eines sicheren JWT-Tokens erleichtern.
translation-type: tm+mt
source-git-commit: 9a4cb6d981fdf5eea4d1b9c7ae9e3c99947d9745
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---


# Einführung {#introduction}

>[!IMPORTANT]
>
>Diese Funktion ist noch nicht verfügbar. Eine aktuelle Liste der Funktionen finden Sie in den [Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

Einige Architekturen sind darauf angewiesen, AEM als Cloud Service von einer Anwendung aufzurufen, die auf einem Server außerhalb AEM Infrastruktur gehostet wird. Beispielsweise eine Mobilanwendung, die einen Server aufruft und dann API-Anfragen als Cloud Service AEM.

Der Server-zu-Server-Fluss wird unten beschrieben, zusammen mit einem vereinfachten Fluss für die Entwicklung. Der AEM als Cloud Service [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) wird verwendet, um Token zu generieren, die für den Authentifizierungsprozess benötigt werden.

## Der Server-zu-Server-Fluss {#the-server-to-server-flow}

Ein Benutzer mit der Rolle &quot;admin&quot;kann ein JWT-TrägerToken generieren, das auf dem Server installiert werden sollte und sorgfältig als geheimer Schlüssel behandelt werden sollte. Das JWT-Inhabertoken sollte mit IMS gegen ein Zugriffstoken getauscht werden, das in der Bitte um AEM als Cloud Service enthalten sein sollte.

Der Server-zu-Server-Fluss umfasst die folgenden Schritte:

* Generieren des JWT-Inhabertokens über die Developer Console
* Installieren Sie das Token auf einem Nicht-AEM-Server, der Aufrufe an AEM
* Austausch des JWT-Inhabertokens für ein Zugriffstoken mithilfe der IMS-APIs der Adobe
* Aufruf der AEM-API

### Generieren des JWT-Bearer-Tokens {#generating-the-jwt-bearer-token}

Benutzer mit der Administratorrolle für ein Unternehmen sehen die Registerkarte &quot;Integrationen&quot;in der Entwicklerkonsole für eine bestimmte Umgebung sowie zwei Schaltflächen. Durch Klicken auf die Schaltfläche **Dienstberechtigungen abrufen** wird der private Schlüssel, das Zertifikat und die Konfiguration generiert.

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

### Token auf einem nicht AEM Server {#install-the-token-on-a-non-aem-server} installieren

Die AEM Anwendung, die Aufrufe an AEM sendet, sollte das JWT-Inhabertoken installieren und als geheim behandeln.

### JWT-Token für ein Zugriffstoken {#exchange-the-jwt-token-for-an-access-token} tauschen

Schließen Sie das JWT-Token in einen Aufruf des IMS-Dienstes der Adobe ein, um ein Zugriffstoken abzurufen, das 24 Stunden gültig ist.

### Aufrufen der AEM-API {#calling-the-aem-api}

Nehmen Sie die entsprechenden Server-zu-Server-API-Aufrufe an eine AEM als Cloud Service-Umgebung vor, einschließlich des Zugriffstokens im Header. Verwenden Sie daher für den Header &quot;Autorisierung&quot;den Wert `"Bearer <access_token>"`.

<!-- ### Code Samples {#code-samples}

https://git.corp.adobe.com/boston/skyline-api-client-lib (internal note: URL will change to public git repo before we publish) contains client libraries written in node.js that will exchange the JSON outputted by the developer console for an access token. -->

## Entwicklerfluss {#developer-flow}

Entwickler möchten wahrscheinlich eine Entwicklungsinstanz ihrer Nicht-AEM-Anwendung testen (entweder auf ihrem Laptop ausgeführt oder gehostet), die Anforderungen an eine Entwicklungs-AEM als Cloud Service-dev-Umgebung stellt. Da Entwickler jedoch nicht unbedingt als Cloud Service-Dev-Umgebung Zugriff auf die AEM haben, können wir nicht davon ausgehen, dass sie den im normalen Server-zu-Server-Fluss beschriebenen JWT-Träger generieren können. So bieten wir einem Entwickler einen Mechanismus, um ein Zugriffstoken direkt zu generieren, das in Anforderungen zur AEM als Cloud Service-Umgebung verwendet werden kann, auf die er Zugriff hat. Informationen zu den erforderlichen Berechtigungen zur Verwendung des AEM als Cloud Service-Entwicklerkonsole finden Sie in der Dokumentation zu [Entwicklerrichtlinien](/help/implementing/developing/introduction/development-guidelines.md).

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

## JWT-Träger-Token-Widerruf {#jwt-bearer-token-revocation}

Bitte senden Sie eine Anfrage an den Kundensupport, wenn das JWT-Inhabertoken widerrufen werden muss.