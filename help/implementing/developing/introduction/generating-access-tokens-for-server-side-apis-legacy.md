---
title: Erstellen von Zugriffs-Tokens für Server-seitige APIs (Frühere Version)
description: Erfahren Sie, wie Sie durch Generieren eines sicheren JWT-Tokens die Kommunikation zwischen einem Drittanbieter-Server und AEM as a Cloud Service ermöglichen.
hidefromtoc: true
source-git-commit: aad1033828e400aaf4d9418f8e57afb61f05eecc
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 99%

---

# Generieren von Zugriffstoken für serverseitige APIs (alt) {#generating-access-tokens-for-server-side-apis-legacy}

Einige Architekturen müssen AEM as a Cloud Service von einer Programm aufrufen, das auf einem Server außerhalb der AEM-Infrastruktur gehostet wird. Dies könnte eine Mobile App sein, die einen Server aufruft, welcher anschließend API-Anfragen an AEM as a Cloud Service sendet.

Der Server-zu-Server-Fluss wird unten beschrieben, zusammen mit einem vereinfachten Fluss für die Entwicklung. Die [Entwicklerkonsole](development-guidelines.md#crxde-lite-and-developer-console) von AEM as a Cloud Service dient dazu, Token zu generieren, die für den Authentifizierungsprozess benötigt werden.

>[!NOTE]
>
>Zusätzlich zu dieser Dokumentation können Sie auch die Tutorials [Token-basierte Authentifizierung für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=de#authentication) und [Abrufen eines Anmelde-Tokens für Integrationen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html?lang=de) zu Rate ziehen.

## Der Server-zu-Server-Fluss {#the-server-to-server-flow}

Ein Benutzer mit der Rolle „IMS-Organisationsadministrator“, der auch Mitglied des AEM-Benutzerprofils oder AEM-Administrator-Produktprofils in der AEM-Autoreninstanz ist, kann Anmeldeinformationen für AEM as a Cloud Service erzeugen. Diese Anmeldeinformationen können anschließend von einem Benutzer mit der Rolle Administrator der AEM as a Cloud Service-Umgebung abgerufen werden und sollten auf dem Server installiert sein und müssen sorgfältig als geheimer Schlüssel behandelt werden. Diese Datei im JSON-Format enthält alle Daten, die zur Integration mit einer AEM as a Cloud Service-API erforderlich sind. Die Daten werden zum Erstellen eines signierten JWT-Tokens verwendet, das mit IMS gegen ein IMS-Zugriffs-Token eingetauscht wird. Dieses Zugriffs-Token kann dann als Inhaberauthentifizierungs-Token für Anfragen an AEM as a Cloud Service verwendet werden. Die Anmeldeinformationen laufen standardmäßig nach einem Jahr ab, können jedoch bei Bedarf aktualisiert werden, wie [hier](#refresh-credentials) beschrieben.

Der Server-zu-Server-Fluss umfasst die folgenden Schritte:

* Abrufen der Anmeldeinformationen für AEM as a Cloud Service von der Entwicklerkonsole
* Installieren der Anmeldeinformationen für AEM as a Cloud Service auf einem Nicht-AEM-Server, der Aufrufe an AEM sendet
* Generieren eines JWT-Tokens und Eintauschen dieses Tokens gegen ein Zugriffs-Token über die IMS-APIs von Adobe
* Aufrufen der AEM-API mit dem Zugriffs-Token als Inhaberauthentifizierungs-Token
* Festlegen der entsprechenden Berechtigungen für technische Kontobenutzer in der AEM-Umgebung

### Abrufen der Anmeldeinformationenn für AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Für Benutzer mit Zugriff auf die Entwicklerkonsole von AEM as a Cloud Service werden in der Entwicklerkonsole die Registerkarte mit Integrationen für eine bestimmte Umgebung sowie zwei Schaltflächen angezeigt. Benutzer mit der Rolle eines Umgebungsadministrators für AEM as a Cloud Service können auf die Schaltfläche **Service-Anmeldeinformationen erzeugen** klicken, um die Service-Anmeldeinformationen im JSON-Format zu erzeugen. Diese enthalten alle für den Nicht-AEM-Server erforderlichen Informationen, einschließlich Client-ID, Client-Geheimnis, privatem Schlüssel, Zertifikat und Konfiguration für die Autoren- und Veröffentlichungsebenen der Umgebung, unabhängig vom ausgewählten Pod.

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

Nach der Generierung können die Anmeldeinformationen zu einem späteren Zeitpunkt abgerufen werden, indem Sie an derselben Stelle auf die Schaltfläche **Service-Anmeldeinformation abrufen** klicken.

>[!IMPORTANT]
>
>Ein IMS-Organisationsadministrator (in der Regel derselbe Benutzer, der die Umgebung über Cloud Manager bereitgestellt hat), der auch Mitglied des AEM-Benutzerprofils oder AEM-Administrator-Produktprofils in der AEM-Autoreninstanz sein sollte, muss zuerst auf die Entwicklerkonsole zugreifen und auf die Schaltfläche **Service-Anmeldeinformationen abrufen** klicken, damit die Anmeldeinformationen erzeugt und später von einem Benutzer mit Administratorrechten für die AEM as a Cloud Service-Umgebung abgerufen werden können. Wenn der IMS-Organisationsadministrator dies nicht getan hat, wird in einer Meldung darauf hingewiesen, dass die Rolle eines IMS-Organisationsadministrators erforderlich ist.

### Installieren der AEM-Service-Anmeldeinformationen auf einem Nicht-AEM-Server {#install-the-aem-service-credentials-on-a-non-aem-server}

Das Nicht-AEM-Programm, das Aufrufe an AEM sendet, sollte in der Lage sein, auf AEM as a Cloud Service-Anmeldeinformationen zuzugreifen, und sie geheim behandeln.

### Generieren und Eintauschen eines JWT-Tokens gegen ein Zugriffs-Token {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Verwenden Sie die Anmeldeinformationen, um ein JWT-Token in einem Aufruf an den IMS-Service von Adobe zu erstellen und ein Zugriffs-Token abzurufen, das 24 Stunden gültig ist.

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

Das Zugriffs-Token bestimmt, wann es abläuft – in der Regel nach 24 Stunden. Im Git-Repository steht Beispiel-Code für das Verwalten und Aktualisieren eines Zugriffs-Tokens vor dem Ablauf zur Verfügung.

### Aufrufen der AEM-API {#calling-the-aem-api}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`. Beispiel mit `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Festlegen der entsprechenden Berechtigungen für den technischen Kontobenutzer in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Sobald der technische Kontobenutzer in AEM erstellt wurde (dies erfolgt nach der ersten Anfrage mit dem entsprechenden Zugriffs-Token), muss der technische Kontobenutzer **in** AEM die entsprechenden Berechtigungen erhalten.

Beachten Sie, dass der technische Kontobenutzer im AEM Author-Service standardmäßig der Benutzergruppe „Mitwirkende“ hinzugefügt wird und damit über Leserechte für AEM verfügt.

Dieser Benutzer eines technischen Kontos in AEM kann mit den üblichen Methoden weitere Berechtigungen erhalten.

## Entwicklungsablauf {#developer-flow}

Entwickler möchten wahrscheinlich Tests mit einer Entwicklungsinstanz ihres Nicht-AEM-Programms durchführen (entweder auf ihrem Laptop oder gehostet), das Anfragen an eine Entwicklungsumgebung von AEM as a Cloud Service sendet. Da Entwickler jedoch nicht unbedingt über Berechtigungen als IMS-Administrator verfügen, können wir nicht davon ausgehen, dass sie den im normalen Server-zu-Server-Fluss beschriebenen JWT-Inhaber generieren können. Deshalb bieten wir Entwicklern einen Mechanismus, um direkt ein Zugriffs-Token zu generieren, das in Anfragen an AEM as a Cloud Service-Umgebungen verwendet werden kann, auf die sie Zugriff haben.

Informationen zu den erforderlichen Berechtigungen zur Verwendung der Entwicklerkonsole von AEM as a Cloud Service finden Sie in der Dokumentation zu [Entwicklerrichtlinien](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
>
>Das lokale Zugriffs-Token für Entwickler ist maximal 24 Stunden lang gültig. Danach muss es mit derselben Methode neu generiert werden.

Entwickler können dieses Token verwenden, um Aufrufe von ihrem Nicht-AEM-Testprogramm an eine AEM as a Cloud Service-Umgebung zu senden. Normalerweise verwenden Entwickler dieses Token mit dem Nicht-AEM-Programm auf dem eigenen Laptop. Außerdem ist AEM as a Cloud Service normalerweise keine Produktionsumgebung.

Der Entwicklungsablauf umfasst die folgenden Schritte:

* Erstellen eines Zugriffs-Tokens über die Entwicklerkonsole
* Aufrufen des AEM-Programms mit dem Zugriffs-Token

Entwickler können auch API-Aufrufe an ein AEM-Projekt auf ihrem lokalen Computer durchführen. In diesem Fall ist kein Zugriffs-Token erforderlich.

### Generieren des Zugriffs-Tokens {#generating-the-access-token}

Klicken Sie in der Entwicklerkonsole auf die Schaltfläche zum **Abrufen eines lokalen Entwicklungs-Tokens**, um ein Zugriffs-Token zu generieren.

### Aufrufen des AEM-Programms mit einem Zugriffs-Token {#call-the-aem-application-with-an-access-token}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe vom Nicht-AEM-Programm an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`.

## Verlängern der Gültigkeit von Anmeldeinformationen {#refresh-credentials}

Standardmäßig laufen die AEM as a Cloud Service-Anmeldedaten nach einem Jahr ab. Um die Kontinuität des Service sicherzustellen, haben Entwickler die Möglichkeit, die Gültigkeit der Anmeldeinformationen zu verlängern, sodass sie für ein weiteres Jahr gültig bleiben.

Zu diesem Zweck können Sie die Schaltfläche **Service-Anmeldeinformationen verlängern** auf der Registerkarte **Integrationen** in der Entwicklerkonsole verwenden, wie unten dargestellt.

![Verlängern von Anmeldeinformationen](assets/credential-refresh.png)

Nach dem Klicken auf die Schaltfläche wird ein neuer Satz von Anmeldeinformationen erzeugt. Sie können Ihren geheimen Speicher mit den neuen Anmeldedaten aktualisieren und überprüfen, ob sie wie gewünscht funktionieren.

>[!NOTE]
>
> Nachdem Sie auf die Schaltfläche **Service-Anmeldeinformationen aktualisieren** geklickt haben, bleiben die alten Anmeldeinformationen bis zu ihrem Ablauf registriert. Es steht jedoch immer nur der neueste Satz zur Anzeige in der Entwicklerkonsole zur Verfügung.

## Widerruf der Service-Anmeldeinformationen {#service-credentials-revocation}

Wenn die Anmeldeinformationen widerrufen werden müssen, müssen Sie eine Anfrage an den Kunden-Support senden, indem Sie folgende Schritte durchführen:

1. Deaktivieren Sie den technischen Kontobenutzer für die Adobe Admin Console in der Benutzeroberfläche:
   * Klicken Sie in Cloud Manager auf die Schaltfläche **...** neben Ihrer Umgebung. Dadurch wird die Seite mit den Produktprofilen geöffnet.
   * Klicken Sie jetzt auf das Profil **AEM-Benutzer**, um eine Liste der Benutzer anzuzeigen.
   * Klicken Sie auf die Registerkarte **API-Anmeldeinformationen**, suchen Sie den entsprechenden Benutzer des technischen Kontos und löschen Sie ihn.
2. Wenden Sie sich an den Kunden-Support und fordern Sie an, dass die Service-Anmeldeinformationen für diese bestimmte Umgebung gelöscht werden.
3. Schließlich können Sie die Anmeldeinformationen erneut generieren, wie in dieser Dokumentation beschrieben. Stellen Sie außerdem sicher, dass der neu erstellte Benutzer des technischen Kontos über die entsprechenden Berechtigungen verfügt.
