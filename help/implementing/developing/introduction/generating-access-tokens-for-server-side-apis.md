---
title: Erstellen von Zugriffs-Tokens für Server-seitige APIs
description: Erfahren Sie, wie Sie durch Generieren eines sicheren JWT-Tokens die Kommunikation zwischen einem Drittanbieter-Server und AEM as a Cloud Service ermöglichen.
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: dd869397feca593f93ee8ed5030828e01cc45c4d
workflow-type: tm+mt
source-wordcount: '2132'
ht-degree: 100%

---

# Erstellen von Zugriffs-Token für Server-seitige APIs {#generating-access-tokens-for-server-side-apis}

Einige Architekturen müssen AEM as a Cloud Service von einer Programm aufrufen, das auf einem Server außerhalb der AEM-Infrastruktur gehostet wird. Dies könnte eine Mobile App sein, die einen Server aufruft, welcher anschließend API-Anfragen an AEM as a Cloud Service sendet.

Der Server-zu-Server-Fluss wird unten beschrieben, zusammen mit einem vereinfachten Fluss für die Entwicklung. Die [Entwicklerkonsole](development-guidelines.md#crxde-lite-and-developer-console) von AEM as a Cloud Service dient dazu, Token zu generieren, die für den Authentifizierungsprozess benötigt werden.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Der Server-zu-Server-Fluss {#the-server-to-server-flow}

Eine Person mit der Rolle eines IMS-Org-Administrierenden, die auch Mitglied des AEM-Benutzerprofils oder AEM Administrator-Produktprofils in der AEM-Autoreninstanz ist, kann einen Satz von AEM as a Cloud Service-Anmeldeinformationen generieren, bei denen es sich jeweils um einen JSON-Payload handelt, der ein Zertifikat (den öffentlichen Schlüssel), einen privaten Schlüssel und ein technisches Konto bestehend aus `clientId` und `clientSecret` enthält. Diese Anmeldeinformationen können anschließend von einem Benutzenden mit der Rolle eines „AEM as a Cloud-Service-Umgebung-Administrierenden“ abgerufen werden und sollten auf einem Nicht-AEM-Server installiert und sorgfältig wie ein geheimer Schlüssel behandelt werden. Diese Datei im JSON-Format enthält alle Daten, die zur Integration mit einer AEM as a Cloud Service-API erforderlich sind. Die Daten werden zum Erstellen eines signierten JWT-Tokens verwendet, das mit Adobe Identity Management Services (IMS) gegen ein IMS-Zugriffs-Token eingetauscht wird. Dieses Zugriffs-Token kann dann als Inhaberauthentifizierungs-Token für Anfragen an AEM as a Cloud Service verwendet werden. Die Anmeldeinformationen laufen standardmäßig nach einem Jahr ab, können jedoch bei Bedarf aktualisiert werden, wie [hier](#refresh-credentials) beschrieben.

Der Server-zu-Server-Fluss umfasst die folgenden Schritte:

* Abrufen der Anmeldeinformationen für AEM as a Cloud Service von der Entwicklerkonsole
* Installieren der Anmeldeinformationen für AEM as a Cloud Service auf einem Nicht-AEM-Server, der Aufrufe an AEM sendet
* Generieren eines JWT-Tokens und Eintauschen dieses Tokens gegen ein Zugriffs-Token über die IMS-APIs von Adobe
* Aufrufen der AEM-API mit dem Zugriffs-Token als Inhaberauthentifizierungs-Token
* Festlegen der entsprechenden Berechtigungen für technische Kontobenutzer in der AEM-Umgebung

### Abrufen der Anmeldeinformationenn für AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Für Benutzende mit Zugriff auf die Developer Console von AEM as a Cloud Service werden in der Developer Console die Registerkarte mit Integrationen für eine bestimmte Umgebung sowie zwei Schaltflächen angezeigt. Benutzende mit der Rolle eines Administrierenden von AEM as a Cloud Service-Umgebungen können Anmeldeinformationen erstellen, anzeigen oder verwalten.

Wenn Sie auf die Schaltfläche **Neues technisches Konto erstellen** klicken, wird ein neuer Satz von Anmeldeinformationen erstellt, der die Client-ID, das Client-Geheimnis, den privaten Schlüssel, das Zertifikat und die Konfiguration für die Autoren- und Veröffentlichungsebenen der Umgebung enthält, unabhängig von der Pod-Auswahl.

![Erstellen eines neuen technischen Kontos](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Daraufhin wird eine neue Browser-Registerkarte mit den Anmeldeinformationen geöffnet. Sie können diese Ansicht verwenden, um die Anmeldeinformationen herunterzuladen, indem Sie auf das Download-Symbol neben dem Statustitel klicken:

![Herunterladen von Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Nachdem die Anmeldeinformationen erstellt wurden, erscheinen sie unter der Registerkarte **Technische Konten** im Abschnitt **Integrationen**:

![Anzeigen der Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Benutzende können die Anmeldeinformationen später mit der Aktion „Anzeigen“ einsehen. Darüber hinaus können Benutzende, wie weiter unten im Artikel beschrieben, die Anmeldeinformationen für dasselbe technische Konto ändern, indem sie einen neuen privaten Schlüssel oder ein neues Zertifikat erstellen. Dies gilt für Fälle, in denen das Zertifikat erneuert oder widerrufen werden muss.

Benutzende mit der Rolle eines AEM as a Cloud Service Umgebungs-Administrierenden können später neue Anmeldeinformationen für zusätzliche technische Konten erstellen. Dies ist nützlich, wenn verschiedene APIs unterschiedliche Zugriffsanforderungen haben. Zum Beispiel Lese- vs. Lese- und Schreibzugriffe.

>[!NOTE]
>
>Kunden können bis zu 10 technische Konten erstellen, darunter auch solche, die bereits gelöscht wurden.

>[!IMPORTANT]
>
>Eine IMS-Org-Administrationsperson (in der Regel dieselbe Person, die die Umgebung über Cloud Manager bereitgestellt hat), die auch Mitglied des Produktprofils „AEM-Benutzende“ oder „AEM-Administrierende“ auf AEM Author sein sollte, muss zunächst auf die Developer Console zugreifen und auf die Schaltfläche **Neues technisches Konto erstellen** klicken, damit die Anmeldeinformationen generiert und später von einer Person mit Administratorberechtigungen für die AEM as a Cloud Service-Umgebung abgerufen werden können. Wenn der IMS-Organisationsadministrator dies nicht getan hat, wird in einer Meldung darauf hingewiesen, dass die Rolle eines IMS-Organisationsadministrators erforderlich ist.

### Installieren der AEM-Service-Anmeldeinformationen auf einem Nicht-AEM-Server {#install-the-aem-service-credentials-on-a-non-aem-server}

Die Applikation, die AEM aufruft, sollte in der Lage sein, auf die AEM as a Cloud Service-Anmeldeinformationen zuzugreifen und sie als Geheimnis zu behandeln.

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

>[!NOTE]
>Wenn mehrere Anmeldeinformationen vorhanden sind, verweisen Sie auf die entsprechende JSON-Datei für den API-Aufruf an AEM, der später aufgerufen wird.

### Aufrufen der AEM-API {#calling-the-aem-api}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`. Beispiel mit `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Festlegen der entsprechenden Berechtigungen für den technischen Kontobenutzer in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Zunächst muss in der Adobe Admin Console ein neues Produktprofil erstellt werden. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zur Adobe Admin Console unter [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/)
1. Klicken Sie auf den Link **Verwalten** unter der Spalte **Produkte und Dienste** auf der linken Seite.
1. Wählen Sie **AEM as a Cloud Service**
1. Drücken Sie auf die Schaltfläche **Neues Profil**

   ![Neues Profil](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Benennen Sie das Profil und drücken Sie **Speichern**

   ![Profil speichern](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Wählen Sie das soeben erstellte Profil aus der Profilliste aus
1. Drücken Sie auf die Schaltfläche **Benutzende hinzufügen**

   ![Benutzende hinzufügen](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. Fügen Sie das soeben erstellte technische Konto hinzu (in diesem Fall `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) und drücken Sie auf **Speichern**

   ![Tech-Konto hinzufügen](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. Warten Sie 10 Minuten, bis die Änderungen wirksam werden, und führen Sie einen API-Aufruf an AEM mit einem aus den neuen Anmeldeinformationen generierten Zugriffstoken durch. Als cURL-Befehl würde er ähnlich wie in diesem Beispiel dargestellt werden:

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Nachdem Sie den API-Aufruf durchgeführt haben, wird das Produktprofil als Benutzergruppe in der AEM as a Cloud Service Autoreninstanz angezeigt, wobei das entsprechende technische Konto Mitglied dieser Gruppe ist.

Um dies zu überprüfen, müssen Sie Folgendes tun:

1. Melden Sie sich bei der Autoreninstanz an
1. Navigieren Sie zu **Tools** – **Sicherheit** und klicken Sie auf die Karte **Gruppen**
1. Suchen Sie den Namen des erstellten Profils in der Gruppenliste und klicken Sie darauf:

   ![Gruppenprofil](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. Wechseln Sie im folgenden Fenster zu **Mitglieder** und überprüfen Sie, ob das technische Konto dort korrekt aufgeführt ist:

   ![Mitglieder-Registerkarte](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


Alternativ können Sie auch überprüfen, ob das technische Konto in der Benutzerliste angezeigt wird, indem Sie die folgenden Schritte in der Autoreninstanz ausführen:

1. Gehen Sie zu **Tools** > **Sicherheit** > **Benutzer**
1. Überprüfen Sie, ob Ihr technisches Konto in der Benutzerliste aufgeführt ist, und klicken Sie darauf.
1. Klicken Sie auf die Registerkarte **Gruppen**, um zu überprüfen, ob der bzw. die Benutzende Teil der Gruppe ist, die Ihrem Produktprofil entspricht. Diese Person ist auch Mitglied einer Handvoll anderer Gruppen, einschließlich Mitwirkende:

   ![Gruppenmitgliedschaft](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Vor Juli 2023, bevor es möglich war, mehrere Anmeldeinformationen zu erstellen, wurden Kunden und Kundinnen nicht aufgefordert, ein Produktprofil in der Adobe Admin Console zu erstellen. Folglich wurde das technische Konto mit keiner anderen Gruppe außer mit „Mitwirkende“ in der AEM as a Cloud Service-Instanz verknüpft. Aus Gründen der Konsistenz wird empfohlen, für dieses technische Konto in der Adobe Admin Console wie oben beschrieben ein neues Produktprofil zu erstellen und das vorhandene technische Konto zu dieser Gruppe hinzuzufügen.

<u>**Einrichten der entsprechenden Gruppenberechtigungen**</u>

Konfigurieren Sie abschließend für die Gruppe die entsprechenden Berechtigungen, um Ihre APIs ordnungsgemäß aufzurufen oder zu sperren.Gehen Sie dazu wie folgt vor:

1. Melden Sie sich bei der entsprechenden Autoreninstanz an und gehen Sie zu **Einstellungen** – **Sicherheit** - **Berechtigungen**.
1. Suchen Sie im linken Bereich (in diesem Fall „Schreibgeschützte APIs“) nach dem Namen der dem Produktprofil entsprechenden Gruppe und klicken Sie darauf:

   ![Nach Gruppe suchen](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Klicken Sie im folgenden Fenster auf die Bearbeiten-Schaltfläche:

   ![Bearbeiten von Berechtigungen](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Ändern Sie die Berechtigungen entsprechend und klicken Sie auf **Speichern**.

   ![Bestätigen der Bearbeitung von Berechtigungen](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>Weitere Informationen zu Adobe Identity Management System (IMS) und AEM-Benutzer und -Gruppen finden Sie in der [Dokumentation](/help/security/ims-support.md).

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

1. Navigieren Sie zum **Lokalen Token** unter **Integrationen**.
1. Klicken Sie in der Entwicklerkonsole auf die Schaltfläche zum **Abrufen eines lokalen Entwicklungs-Tokens**, um ein Zugriffs-Token zu generieren.

### Aufrufen der AEM-Anwendung mit einem Zugriffs-Token {#call-the-aem-application-with-an-access-token}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe vom Nicht-AEM-Programm an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`.

## Verlängern der Gültigkeit von Anmeldeinformationen {#refresh-credentials}

Standardmäßig laufen die AEM as a Cloud Service-Anmeldedaten nach einem Jahr ab. Um die Kontinuität des Service sicherzustellen, haben Entwickler die Möglichkeit, die Gültigkeit der Anmeldeinformationen zu verlängern, sodass sie für ein weiteres Jahr gültig bleiben.

Dazu haben Sie folgende Möglichkeiten:

* Verwenden Sie wie unten dargestellt in der Entwicklerkonsole die Schaltfläche **Zertifikat hinzufügen** unter **Integrationen** – **Technische Konten**.

   ![Aktualisieren von Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Nach dem Drücken der Schaltfläche wird ein Satz von Anmeldeinformationen generiert, der ein neues Zertifikat enthält. Installieren Sie die neuen Anmeldeinformationen auf Ihrem off-AEM-Server und stellen Sie sicher, dass die Verbindung wie erwartet funktioniert, ohne die alten Anmeldeinformationen zu entfernen. 
* Achten Sie darauf, dass beim Generieren des Zugriffs-Tokens die neuen Anmeldeinformationen anstelle der alten verwendet werden.
* Optional können Sie das vorherige Zertifikat widerrufen (und dann löschen), damit es nicht mehr zur Authentifizierung bei AEM as a Cloud Service verwendet werden kann.

## Widerrufen der Anmeldeinformationen {#credentials-revocation}

Wenn der private Schlüssel kompromittiert ist, müssen Sie Anmeldeinformationen mit einem neuen Zertifikat und einem neuen privaten Schlüssel erstellen. Nachdem Ihre Anwendung die neuen Anmeldeinformationen zum Generieren von Zugriffs-Token verwendet hat, können Sie die alten Zertifikate widerrufen und löschen.

Gehen Sie dazu wie folgt vor:

1. Fügen Sie zunächst den neuen Schlüssel hinzu. Dadurch werden Anmeldeinformationen mit einem neuen privaten Schlüssel und einem neuen Zertifikat generiert. Der neue private Schlüssel wird in der Benutzeroberfläche als **aktuell** markiert und wird somit für alle neuen Anmeldeinformationen für dieses technische Konto verwendet. Beachten Sie, dass die mit den älteren privaten Schlüsseln verknüpften Anmeldeinformationen weiterhin gültig sind, bis sie widerrufen werden.Wählen Sie dazu das Symbol mit den drei Punkten (**...**) unter Ihrem aktuellen technischen Konto und danach die Option **Neuen privaten Schlüssel hinzufügen**:

   ![Neuen privaten Schlüssel hinzufügen](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. Wählen Sie bei der darauffolgenden Eingabeaufforderung **Hinzufügen**:

   ![Hinzufügen eines neuen privaten Schlüssels bestätigen](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Eine neue Registerkarte mit den neuen Anmeldeinformationen wird geöffnet und die Benutzeroberfläche wird aktualisiert, um beide privaten Schlüssel anzuzeigen, wobei der neue Schlüssel als **aktuell** markiert ist:

   ![Private Schlüssel in der Benutzeroberfläche](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installieren Sie die neuen Anmeldeinformationen auf dem Nicht-AEM-Server und stellen Sie sicher, dass die Verbindung erwartungsgemäß funktioniert. Informationen dazu finden Sie im [Abschnitt „Server-zu-Server-Fluss“](#the-server-to-server-flow).
1. Widerrufen Sie das alte Zertifikat. Wählen Sie dazu die drei Punkte (**...**) rechts neben dem Zertifikat aus und danach die Option **Widerrufen**:

   ![Zertifikat widerrufen](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Bestätigen Sie dann den Widerruf in der folgenden Aufforderung durch Auswahl der Schaltfläche **Widerrufen**:

   ![Widerrufen der Zertifikatsbestätigung](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Löschen Sie abschließend das kompromittierte Zertifikat.
