---
title: Erstellen von Zugriffs-Token für Server-seitige APIs (Legacy)
description: Erfahren Sie, wie Sie durch Generieren eines sicheren JWT-Tokens die Kommunikation zwischen einem Drittanbieter-Server und AEM as a Cloud Service ermöglichen.
hidefromtoc: true
exl-id: 6561870c-cbfe-40ef-9efc-ea75c88c4ed7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 22216d2c045b79b7da13f09ecbe1d56a91f604df
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 95%

---

# Erstellen von Zugriffs-Token für Server-seitige APIs (Legacy) {#generating-access-tokens-for-server-side-apis-legacy}

Einige Architekturen müssen AEM as a Cloud Service von einer Programm aufrufen, das auf einem Server außerhalb der AEM-Infrastruktur gehostet wird. Dies könnte eine Mobile App sein, die einen Server aufruft, welcher anschließend API-Anfragen an AEM as a Cloud Service sendet.

Der Server-zu-Server-Fluss wird unten beschrieben, zusammen mit einem vereinfachten Fluss für die Entwicklung. Die [Entwicklerkonsole](development-guidelines.md#crxde-lite-and-developer-console) von AEM as a Cloud Service dient dazu, Token zu generieren, die für den Authentifizierungsprozess benötigt werden.

<!-- ERROR: Not Found (HTTP error 404)
>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=de#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Der Server-zu-Server-Fluss {#the-server-to-server-flow}

Ein Benutzer mit der Rolle „IMS-Organisationsadministrator“, der auch Mitglied des AEM-Benutzerprofils oder AEM-Administrator-Produktprofils in der AEM-Autoreninstanz ist, kann Anmeldeinformationen für AEM as a Cloud Service erzeugen. Diese Anmeldeinformationen können später von einer Benutzerin oder einem Benutzer mit einer Admin-Rolle für die AEM as a Cloud Service-Umgebung abgerufen werden und sollten auf dem Server installiert sein. Sie müssen zudem sorgfältig als geheimer Schlüssel behandelt werden. Diese Datei im JSON-Format enthält alle Daten, die zur Integration mit einer AEM as a Cloud Service-API erforderlich sind. Die Daten werden zum Erstellen eines signierten JWT-Tokens verwendet, das mit IMS gegen ein IMS-Zugriffs-Token eingetauscht wird. Dieses Zugriffs-Token kann dann als Inhaberauthentifizierungs-Token für Anfragen an AEM as a Cloud Service verwendet werden. Die Anmeldeinformationen laufen standardmäßig nach einem Jahr ab, können jedoch bei Bedarf aktualisiert werden, wie unter [Aktualisieren der Anmeldeinformationen](#refresh-credentials) beschrieben.

Der Server-zu-Server-Fluss umfasst die folgenden Schritte:

* Rufen Sie die Anmeldeinformationen für AEM as a Cloud Service aus Developer Console ab.
* Installieren der Anmeldeinformationen für AEM as a Cloud Service auf einem Nicht-AEM-Server, der Aufrufe an AEM sendet
* Generieren eines JWT-Tokens und Eintauschen dieses Tokens gegen ein Zugriffs-Token über die IMS-APIs von Adobe
* Aufrufen der AEM-API mit dem Zugriffs-Token als Inhaberauthentifizierungs-Token
* Festlegen der entsprechenden Berechtigungen für technische Kontobenutzer in der AEM-Umgebung

### Abrufen der Anmeldeinformationenn für AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Benutzenden mit Zugriff auf die Developer Console von AEM as a Cloud Service werden in der Developer Console die Registerkarte mit Integrationen für eine bestimmte Umgebung sowie zwei Schaltflächen angezeigt. Benutzende mit einer Admin-Rolle für die AEM as a Cloud Service-Umgebung können auf die Schaltfläche **Service-Anmeldeinformationen generieren** klicken, um die JSON-Datei mit den Service-Anmeldeinformationen zu generieren und anzuzeigen. Die JSON-Datei enthält alle für den Nicht-AEM-Server erforderlichen Informationen, darunter Client-ID, Client-Geheimnis, privater Schlüssel, Zertifikat und Konfiguration für die Authoring- und Publishing-Ebene der Umgebung, unabhängig von der Pod-Auswahl.

![JWT-Generierung](assets/JWTtoken3.png)

Die Ausgabe sieht ähnlich wie die folgende aus:

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

Nach der Generierung können die Anmeldeinformationen später abgerufen werden, indem Sie an derselben Stelle auf die Schaltfläche **Service-Anmeldeinformationen abrufen** klicken.

>[!IMPORTANT]
>
>Ein Mitglied aus der Gruppe der IMS-Organisationsadmins (in der Regel die Person, die die Umgebung über Cloud Manager bereitgestellt hat), das auch Mitglied des AEM-Benutzerprofils oder AEM-Administrator-Produktprofils in der AEM-Authoring-Instanz sein sollte, greift auf die Developer Console zu. Anschließend muss diese Person auf die Schaltfläche **Service-Anmeldeinformationen generieren** klicken, damit die Anmeldeinformationen von Benutzenden mit Administratorberechtigungen für die AEM as a Cloud Service-Umgebung generiert und später abgerufen werden können. Wenn die oder der IMS-Organisationsadmin diese Aufgabe nicht durchgeführt hat, wird in einer Meldung darauf hingewiesen, dass die IMS-Organisationsadmin-Rolle erforderlich ist.

### Installieren der AEM-Service-Anmeldeinformationen auf einem Nicht-AEM-Server {#install-the-aem-service-credentials-on-a-non-aem-server}

Die Nicht-AEM-Anwendung, die Aufrufe an AEM sendet, sollte in der Lage sein, auf die Anmeldeinformationen für AEM as a Cloud Service zuzugreifen, und diese geheim behandeln.

### Generieren und Eintauschen eines JWT-Tokens gegen ein Zugriffs-Token {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Verwenden Sie die Anmeldeinformationen, um ein JWT-Token in einem Aufruf an den IMS-Service von Adobe zu erstellen und ein Zugriffs-Token abzurufen, das 24 Stunden gültig ist.

Die AEM CS-Service-Anmeldeinformationen können mithilfe von hierfür entwickelten Code-Beispielen gegen ein Zugriffstoken eingetauscht werden. Beispielcode ist im öffentlichen GitHub-Repository[&#x200B; von &#x200B;](https://github.com/adobe/aemcs-api-client-lib)Adobe verfügbar, das Code-Beispiele enthält, die Sie kopieren und für Ihre eigenen Projekte anpassen können. Beachten Sie, dass dieses Repository Beispiel-Code für Referenzzwecke enthält und nicht als produktionsbereite Bibliotheksabhängigkeit gepflegt wird.

```
/*jshint node:true */
"use strict";

const fs = require('fs');
// Sample code adapted from Adobe's GitHub repository
const exchange = require("./your-local-aemcs-client"); // Copy and adapt the code from the GitHub repository

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

Das Zugriffs-Token bestimmt, wann es abläuft – in der Regel nach 24 Stunden. Im Git-Repository steht Beispiel-Code für das Verwalten und Aktualisieren eines Zugriffs-Tokens vor dem Ablauf zur Verfügung.

### Aufrufen der AEM-API {#calling-the-aem-api}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`. Beispiel mit `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Festlegen der entsprechenden Berechtigungen für den technischen Kontobenutzer in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Sobald technische Kontobenutzende in AEM erstellt wurden (dies erfolgt nach der ersten Anfrage mit dem entsprechenden Zugriffs-Token), müssen diese **in** AEM die entsprechenden Berechtigungen erhalten.

Technische Kontobenutzende werden im AEM Author-Service standardmäßig der Benutzergruppe „Mitwirkende“ hinzugefügt und verfügen damit über Leserechte für AEM.

Dieser Benutzer eines technischen Kontos in AEM kann mit den üblichen Methoden weitere Berechtigungen erhalten.

## Entwicklungsablauf {#developer-flow}

Entwicklerinnen und Entwickler sollten Tests mit einer Entwicklungsinstanz ihrer Nicht-AEM-Anwendung durchführen (entweder auf ihrem Laptop oder gehostet), die Anfragen an eine Entwicklungsumgebung von AEM as a Cloud Service sendet. Da Entwicklerinnen und Entwickler jedoch nicht unbedingt über IMS-Admin-Berechtigungen verfügen, kann Adobe nicht davon ausgehen, dass sie das im normalen Server-zu-Server-Fluss beschriebene JWT-Bearer-Token generieren können. Deshalb bietet Adobe Entwicklerinnen und Entwicklern einen Mechanismus, um direkt ein Zugriffs-Token zu generieren, das in Anfragen an AEM as a Cloud Service-Umgebungen verwendet werden kann, auf die sie Zugriff haben.

Informationen zu den erforderlichen Berechtigungen zur Verwendung der Entwicklerkonsole von AEM as a Cloud Service finden Sie in der Dokumentation zu [Entwicklerrichtlinien](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
>
>Das lokale Zugriffs-Token für Entwickler ist maximal 24 Stunden lang gültig. Danach muss es mit derselben Methode neu generiert werden.

Entwicklerinnen und Entwickler können dieses Token verwenden, um Aufrufe von ihrem Nicht-AEM-Testprogramm an eine AEM as a Cloud Service-Umgebung zu senden. Normalerweise verwenden sie dieses Token mit der Nicht-AEM-Anwendung auf dem eigenen Laptop. Außerdem ist AEM as a Cloud Service normalerweise keine Produktionsumgebung.

Der Entwicklungsablauf umfasst die folgenden Schritte:

* Erstellen eines Zugriffs-Tokens über die Entwicklerkonsole
* Aufrufen des AEM-Programms mit dem Zugriffs-Token

Entwickler können auch API-Aufrufe an ein AEM-Projekt auf ihrem lokalen Computer durchführen. In diesem Fall ist kein Zugriffs-Token erforderlich.

### Generieren des Zugriffs-Tokens {#generating-the-access-token}

Um ein Zugriffs-Token zu generieren, klicken Sie in der Developer Console auf **Lokales Entwicklungs-Token abrufen**.

### Aufrufen des AEM-Programms mit einem Zugriffs-Token {#call-the-aem-application-with-an-access-token}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe vom Nicht-AEM-Programm an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`.

## Verlängern der Gültigkeit von Anmeldeinformationen {#refresh-credentials}

Standardmäßig laufen die Anmeldeinformationen in AEM as a Cloud Service nach einem Jahr ab. Um die Kontinuität des Service sicherzustellen, haben Entwicklerinnen und Entwickler die Möglichkeit, die Gültigkeit der Anmeldeinformationen zu verlängern, sodass sie für ein weiteres Jahr gültig bleiben. Verwenden Sie dazu in der Developer Console auf der Registerkarte **Integrationen** die Option **Service-Anmeldeinformationen aktualisieren**, wie unten gezeigt.

![Aktualisieren von Anmeldeinformationen](assets/credential-refresh.png)

Nach dem Klicken auf die Schaltfläche wird ein neuer Satz von Anmeldeinformationen generiert. Sie können Ihren geheimen Speicher mit den neuen Anmeldedaten aktualisieren und überprüfen, ob sie wie gewünscht funktionieren.

>[!NOTE]
>
> Nachdem Sie auf die Schaltfläche **Service-Anmeldeinformationen aktualisieren** geklickt haben, bleiben die alten Anmeldeinformationen bis zu ihrem Ablauf registriert. Es steht jedoch immer nur der neueste Satz zur Anzeige in der Entwicklerkonsole zur Verfügung.

## Widerruf der Service-Anmeldeinformationen {#service-credentials-revocation}

Wenn die Anmeldeinformationen widerrufen werden müssen, müssen Sie eine Anfrage an den Kunden-Support senden, indem Sie folgende Schritte durchführen:

1. Deaktivieren Sie den technischen Kontobenutzer für die Adobe Admin Console in der Benutzeroberfläche:
   * Klicken Sie in Cloud Manager auf die Schaltfläche **...** neben Ihrer Umgebung. Dadurch wird die Seite mit den Produktprofilen geöffnet.
   * Klicken Sie nun auf das Profil für die **AEM-Benutzenden**, um eine Liste der Benutzenden anzuzeigen.
   * Klicken Sie auf die Registerkarte **API-Anmeldeinformationen**, suchen Sie den entsprechenden Benutzer des technischen Kontos und löschen Sie ihn.
2. Wenden Sie sich an den Kunden-Support und fordern Sie an, dass die Service-Anmeldeinformationen für diese bestimmte Umgebung gelöscht werden.
3. Schließlich können Sie die Anmeldeinformationen erneut generieren, wie in dieser Dokumentation beschrieben. Stellen Sie außerdem sicher, dass der neu erstellte Benutzer des technischen Kontos über die entsprechenden Berechtigungen verfügt.
