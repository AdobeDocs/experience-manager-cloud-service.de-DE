---
title: Generieren von Zugriffstoken für serverseitige APIs (alt)
description: Erfahren Sie, wie Sie die Kommunikation zwischen einem Drittanbieterserver und AEM as a Cloud Service erleichtern können, indem Sie ein sicheres JWT-Token generieren.
hidefromtoc: true
exl-id: 6561870c-cbfe-40ef-9efc-ea75c88c4ed7
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1359'
ht-degree: 54%

---

# Generieren von Zugriffstoken für serverseitige APIs (alt) {#generating-access-tokens-for-server-side-apis-legacy}

Einige Architekturen müssen AEM as a Cloud Service von einer Programm aufrufen, das auf einem Server außerhalb der AEM-Infrastruktur gehostet wird. Dies könnte eine Mobile App sein, die einen Server aufruft, welcher anschließend API-Anfragen an AEM as a Cloud Service sendet.

Der Server-zu-Server-Fluss wird unten beschrieben, zusammen mit einem vereinfachten Fluss für die Entwicklung. Die [Entwicklerkonsole](development-guidelines.md#crxde-lite-and-developer-console) von AEM as a Cloud Service dient dazu, Token zu generieren, die für den Authentifizierungsprozess benötigt werden.

<!-- ERROR: Not Found (HTTP error 404)
>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Der Server-zu-Server-Fluss {#the-server-to-server-flow}

Ein Benutzer mit der Rolle „IMS-Organisationsadministrator“, der auch Mitglied des AEM-Benutzerprofils oder AEM-Administrator-Produktprofils in der AEM-Autoreninstanz ist, kann Anmeldeinformationen für AEM as a Cloud Service erzeugen. Diese Berechtigung kann später von einem Benutzer mit der AEM as a Cloud Service Umgebungsadministratorrolle abgerufen werden und sollte auf dem Server installiert sein und muss sorgfältig als geheimer Schlüssel behandelt werden. Diese Datei im JSON-Format enthält alle Daten, die zur Integration mit einer AEM as a Cloud Service-API erforderlich sind. Die Daten werden zum Erstellen eines signierten JWT-Tokens verwendet, das mit IMS gegen ein IMS-Zugriffs-Token eingetauscht wird. Dieses Zugriffs-Token kann dann als Inhaberauthentifizierungs-Token für Anfragen an AEM as a Cloud Service verwendet werden. Die Anmeldeinformationen laufen standardmäßig nach einem Jahr ab, können jedoch bei Bedarf aktualisiert werden, wie [hier](#refresh-credentials) beschrieben.

Der Server-zu-Server-Fluss umfasst die folgenden Schritte:

* Rufen Sie die Anmeldeinformationen für AEM as a Cloud Service aus der Developer Console ab.
* Installieren Sie die Anmeldeinformationen für AEM as a Cloud Service auf einem Nicht-AEM-Server, der Aufrufe an AEM sendet.
* Generieren eines JWT-Tokens und Eintauschen dieses Tokens gegen ein Zugriffs-Token über die IMS-APIs von Adobe
* Aufrufen der AEM-API mit dem Zugriffs-Token als Inhaberauthentifizierungs-Token
* Festlegen der entsprechenden Berechtigungen für technische Kontobenutzer in der AEM-Umgebung

### Abrufen der Anmeldeinformationenn für AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Benutzer mit Zugriff auf die AEM as a Cloud Service Entwicklerkonsole finden die Registerkarte Integrationen in der Entwicklerkonsole für eine bestimmte Umgebung sowie zwei Schaltflächen. Ein Benutzer mit der AEM as a Cloud Service Umgebungsadministratorrolle kann auf die **Dienstanmeldeinformationen generieren** -Schaltfläche, um die Dienstanmeldeinformationen zu generieren und anzuzeigen. Die JSON-Datei enthält alle für den Nicht-AEM-Server erforderlichen Informationen, einschließlich Client-ID, Client-Geheimnis, privater Schlüssel, Zertifikat und Konfiguration für die Autoren- und Veröffentlichungsschicht der Umgebung, unabhängig von der Pod-Auswahl.

![JWT-Generierung](assets/JWTtoken3.png)

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

Nach der Generierung können die Anmeldeinformationen später abgerufen werden, indem Sie die **Get Service-Anmeldedaten** -Schaltfläche an derselben Stelle.

>[!IMPORTANT]
>
>Ein IMS-Organisationsadministrator - in der Regel der Benutzer, der die Umgebung über Cloud Manager bereitgestellt hat -, der auch Mitglied des AEM-Benutzerprofils oder AEM Administrator-Produktprofils in der AEM-Autoreninstanz sein sollte - greift auf die Developer Console zu. Anschließend müssen sie auf die **Dienstanmeldeinformationen generieren** -Schaltfläche, damit die Anmeldeinformationen von einem Benutzer mit Administratorberechtigungen für die AEM as a Cloud Service Umgebung generiert und später abgerufen werden. Wenn der IMS-Organisationsadministrator diese Aufgabe nicht ausgeführt hat, wird er in einer Meldung darüber informiert, dass er die Rolle &quot;IMS-Organisationsadministrator&quot;benötigt.

### Installieren Sie die AEM-Dienstanmeldeinformationen auf einem Nicht-AEM-Server {#install-the-aem-service-credentials-on-a-non-aem-server}

Die nicht AEM Anwendung, die AEM aufruft, sollte auf die Anmeldeinformationen von AEM as a Cloud Service zugreifen und sie als geheim behandeln können.

### Generieren und Eintauschen eines JWT-Tokens gegen ein Zugriffs-Token {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Verwenden Sie die Anmeldeinformationen, um ein JWT-Token in einem Aufruf des IMS-Dienstes der Adobe zu erstellen und ein Zugriffstoken abzurufen, das 24 Stunden lang gültig ist.

Die Anmeldeinformationen für den AEM CS-Service können mithilfe von zu diesem Zweck eingerichteten Client-Bibliotheken gegen ein Zugriffs-Token eingetauscht werden. Die Client-Bibliotheken sind im [öffentlichen GitHub-Repository von Adobe](https://github.com/adobe/aemcs-api-client-lib) verfügbar, das detailliertere Anleitungen und aktuelle Informationen enthält.

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

Derselbe Austausch kann in jeder Sprache durchgeführt werden, die in der Lage ist, ein signiertes JWT-Token im richtigen Format zu generieren und die IMS Token Exchange-APIs aufzurufen.

Das Zugriffstoken definiert, wann es abläuft, was normalerweise 24 Stunden dauert. Im Git-Repository steht Beispiel-Code für das Verwalten und Aktualisieren eines Zugriffs-Tokens vor dem Ablauf zur Verfügung.

### Aufrufen der AEM-API {#calling-the-aem-api}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`. Beispiel mit `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Festlegen der entsprechenden Berechtigungen für den technischen Kontobenutzer in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Nachdem der Benutzer des technischen Kontos in AEM erstellt wurde (tritt nach der ersten Anfrage mit dem entsprechenden Zugriffstoken auf), muss der Benutzer des technischen Kontos über die entsprechenden Berechtigungen verfügen **in** AEM.

Standardmäßig wird im AEM-Autorendienst der Benutzer für das technische Konto der Benutzergruppe Mitarbeiter hinzugefügt, die Lesezugriff AEM.

Dieser Benutzer eines technischen Kontos in AEM kann mit den üblichen Methoden weitere Berechtigungen erhalten.

## Entwicklungsablauf {#developer-flow}

Entwickler sollten Tests mit einer Entwicklungsinstanz ihrer AEM (entweder auf ihrem Laptop ausgeführt oder gehostet) durchführen, die Anforderungen an eine Entwicklungsumgebung AEM as a Cloud Service Entwicklungsumgebung sendet. Da Entwickler jedoch nicht unbedingt über IMS-Administratorrollenberechtigungen verfügen, kann Adobe nicht davon ausgehen, dass sie den im regulären Server-zu-Server-Fluss beschriebenen JWT-Träger generieren können. Daher bietet Adobe einen Mechanismus, mit dem Entwickler direkt ein Zugriffstoken generieren können, das in Anforderungen an eine AEM as a Cloud Service Umgebung verwendet werden kann, auf die sie Zugriff haben.

Informationen zu den erforderlichen Berechtigungen zur Verwendung der Entwicklerkonsole von AEM as a Cloud Service finden Sie in der Dokumentation zu [Entwicklerrichtlinien](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
>
Das lokale Zugriffs-Token für Entwickler ist maximal 24 Stunden lang gültig. Danach muss es mit derselben Methode neu generiert werden.

Entwickler können dieses Token verwenden, um Aufrufe von ihrem Nicht-AEM-Testprogramm an eine AEM as a Cloud Service-Umgebung zu senden. In der Regel verwendet der Entwickler dieses Token mit der AEM Anwendung auf seinem eigenen Laptop. Außerdem ist AEM as a Cloud Service normalerweise keine Produktionsumgebung.

Der Entwicklungsablauf umfasst die folgenden Schritte:

* Erstellen eines Zugriffs-Tokens über die Entwicklerkonsole
* Aufrufen des AEM-Programms mit dem Zugriffs-Token

Entwickler können auch API-Aufrufe an ein AEM-Projekt auf ihrem lokalen Computer durchführen. In diesem Fall ist kein Zugriffs-Token erforderlich.

### Generieren des Zugriffs-Tokens {#generating-the-access-token}

Um ein Zugriffstoken zu generieren, klicken Sie in der Developer Console auf **Abrufen des lokalen Entwicklungstokens**.

### Aufrufen des AEM-Programms mit einem Zugriffs-Token {#call-the-aem-application-with-an-access-token}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe vom Nicht-AEM-Programm an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`.

## Verlängern der Gültigkeit von Anmeldeinformationen {#refresh-credentials}

Standardmäßig laufen AEM as a Cloud Service Anmeldedaten nach einem Jahr ab. Um die Kontinuität des Service sicherzustellen, haben Entwickler die Möglichkeit, die Gültigkeit der Anmeldeinformationen zu verlängern, sodass sie für ein weiteres Jahr gültig bleiben. Verwendung **Dienstanmeldeinformationen aktualisieren** von **Integrationen** in der Developer Console, wie unten dargestellt.

![Aktualisieren von Anmeldeinformationen](assets/credential-refresh.png)

Nach dem Drücken der Schaltfläche wird ein neuer Satz von Anmeldeinformationen generiert. Sie können Ihren geheimen Speicher mit den neuen Anmeldedaten aktualisieren und überprüfen, ob sie wie gewünscht funktionieren.

>[!NOTE]
>
Nachdem Sie auf die Schaltfläche **Service-Anmeldeinformationen aktualisieren** geklickt haben, bleiben die alten Anmeldeinformationen bis zu ihrem Ablauf registriert. Es steht jedoch immer nur der neueste Satz zur Anzeige in der Entwicklerkonsole zur Verfügung.

## Widerruf der Service-Anmeldeinformationen {#service-credentials-revocation}

Wenn die Anmeldeinformationen widerrufen werden müssen, müssen Sie mithilfe der folgenden Schritte eine Anfrage an den Support senden:

1. Deaktivieren Sie den technischen Kontobenutzer für die Adobe Admin Console in der Benutzeroberfläche:
   * Klicken Sie in Cloud Manager auf die Schaltfläche **...** neben Ihrer Umgebung. Durch diese Aktion wird die Seite mit den Produktprofilen geöffnet.
   * Klicken Sie nun auf die **AEM** Profil, um eine Liste der Benutzer anzuzeigen
   * Klicken Sie auf die Registerkarte **API-Anmeldeinformationen**, suchen Sie den entsprechenden Benutzer des technischen Kontos und löschen Sie ihn.
2. Wenden Sie sich an den Kunden-Support und fordern Sie an, dass die Service-Anmeldeinformationen für diese bestimmte Umgebung gelöscht werden.
3. Schließlich können Sie die Anmeldeinformationen erneut generieren, wie in dieser Dokumentation beschrieben. Stellen Sie außerdem sicher, dass der neu erstellte Benutzer des technischen Kontos über die entsprechenden Berechtigungen verfügt.
