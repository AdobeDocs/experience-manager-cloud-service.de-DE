---
title: Generieren von Zugriffs-Token für Server-seitige APIs
description: Erfahren Sie, wie Sie durch Generieren eines sicheren JWT-Tokens die Kommunikation zwischen einem Drittanbieter-Server und AEM as a Cloud Service ermöglichen.
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 22216d2c045b79b7da13f09ecbe1d56a91f604df
workflow-type: tm+mt
source-wordcount: '2112'
ht-degree: 97%

---

# Generieren von Zugriffs-Token für Server-seitige APIs {#generating-access-tokens-for-server-side-apis}

Einige Architekturen müssen AEM as a Cloud Service von einer Programm aufrufen, das auf einem Server außerhalb der AEM-Infrastruktur gehostet wird. Dies könnte eine Mobile App sein, die einen Server aufruft, welcher anschließend API-Anfragen an AEM as a Cloud Service sendet.

Der Server-zu-Server-Fluss wird unten beschrieben, zusammen mit einem vereinfachten Fluss für die Entwicklung. Die [Entwicklerkonsole](development-guidelines.md#crxde-lite-and-developer-console) von AEM as a Cloud Service dient dazu, Token zu generieren, die für den Authentifizierungsprozess benötigt werden.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Der Server-zu-Server-Fluss {#the-server-to-server-flow}

Benutzende mit der Rolle „IMS-Organisationsadministrator“, die Mitglieder des AEM-Benutzerprofils oder AEM-Produktprofils „Administratoren“ in der AEM-Autoreninstanz sind, können eine Reihe von Anmeldeinformationen aus AEM as a Cloud Service generieren. Jeder Berechtigungsnachweis ist eine JSON-Payload, die ein Zertifikat (den öffentlichen Schlüssel), einen privaten Schlüssel und ein technisches Konto, bestehend aus `clientId` und `clientSecret`, enthält. Diese Anmeldeinformationen können später von Benutzenden mit einer Admin-Rolle für die AEM as a Cloud Service-Umgebung abgerufen werden und sollten auf einem Nicht-AEM-Server installiert sein. Sie müssen zudem sorgfältig als geheimer Schlüssel behandelt werden. Diese Datei im JSON-Format enthält alle Daten, die zur Integration mit einer AEM as a Cloud Service-API erforderlich sind. Die Daten werden zum Erstellen eines signierten JWT-Tokens verwendet, das mit Adobe Identity Management Services (IMS) gegen ein IMS-Zugriffs-Token eingetauscht wird. Dieses Zugriffs-Token kann dann als Inhaberauthentifizierungs-Token für Anfragen an AEM as a Cloud Service verwendet werden. Das Zertifikat in den Anmeldeinformationen läuft standardmäßig nach einem Jahr ab, sie können jedoch bei Bedarf aktualisiert werden, wie unter [Anmeldeinformationen aktualisieren](#refresh-credentials) beschrieben.

Der Server-zu-Server-Fluss umfasst die folgenden Schritte:

* Abrufen der Anmeldeinformationen für AEM as a Cloud Service von der Developer Console
* Installieren der Anmeldeinformationen für AEM as a Cloud Service auf einem Nicht-AEM-Server, der Aufrufe an AEM sendet
* Generieren eines JWT-Tokens und Eintauschen dieses Tokens gegen ein Zugriffs-Token über die IMS-APIs von Adobe
* Aufrufen der AEM-API mit dem Zugriffs-Token als Inhaberauthentifizierungs-Token
* Festlegen der entsprechenden Berechtigungen für technische Kontobenutzer in der AEM-Umgebung

### Abrufen der Anmeldeinformationenn für AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Für Benutzende mit Zugriff auf die Developer Console von AEM as a Cloud Service werden in der Developer Console die Registerkarte mit Integrationen für eine bestimmte Umgebung angezeigt. Benutzende mit der Rolle eines AEM as a Cloud Service-Umgebungs-Admins können Anmeldeinformationen erstellen, anzeigen oder verwalten.

Wenn Sie auf **Neues technisches Konto erstellen** klicken, wird ein neuer Satz von Anmeldeinformationen erstellt, der die Client-ID, das Client-Geheimnis, den privaten Schlüssel, das Zertifikat und die Konfiguration für die Autoren- und Veröffentlichungsebenen der Umgebung enthält, unabhängig von der Pod-Auswahl.

![Erstellen eines neuen technischen Kontos](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Daraufhin wird eine neue Browser-Registerkarte mit den Anmeldeinformationen geöffnet. Sie können diese Ansicht verwenden, um die Anmeldeinformationen herunterzuladen, indem Sie auf das Download-Symbol neben dem Statustitel klicken:

![Herunterladen von Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Nachdem die Anmeldeinformationen erstellt wurden, erscheinen sie unter der Registerkarte **Technische Konten** im Abschnitt **Integrationen**:

![Anzeigen der Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Benutzende können die Anmeldeinformationen später mit der Aktion „Anzeigen“ einsehen. Darüber hinaus können Benutzende die Anmeldeinformationen für dasselbe technische Konto bearbeiten, wie weiter unten im Artikel beschrieben. Sie führen diese Bearbeitung durch Erstellen eines privaten Schlüssels oder Zertifikats durch, falls das Zertifikat erneuert oder widerrufen werden muss.

Benutzende mit der Rolle eines AEM as a Cloud Service Umgebungs-Admins können später neue Anmeldeinformationen für zusätzliche technische Konten erstellen. Diese Fähigkeit ist nützlich, wenn verschiedene APIs unterschiedliche Zugriffsanforderungen haben. Zum Beispiel Lesezugriff versus Lese- und Schreibzugriff.

>[!NOTE]
>
>Kundinnen und Kunden können bis zu zehn technische Konten anlegen, einschließlich der Konten, die bereits gelöscht wurden.

>[!IMPORTANT]
>
>Ein Mitglied aus der Gruppe der IMS-Organisationsadmins (in der Regel die Person, die die Umgebung über Cloud Manager bereitgestellt hat), das auch Mitglied des AEM-Benutzerprofils oder AEM-Administrator-Produktprofils in AEM Author sein sollte, muss zuerst auf die Developer Console zugreifen. Klicken Sie anschließend auf **Neues technisches Konto erstellen**, damit die Anmeldeinformationen von einer Person mit Administratorberechtigungen für die AEM as a Cloud Service-Umgebung generiert und später abgerufen werden können. Wenn IMS-Organisationsadmins das technische Konto noch nicht erstellt haben, werden sie in einer Nachricht darüber informiert, dass sie die IMS-Organisationsadmin-Rolle benötigen.

### Installieren der AEM-Service-Anmeldeinformationen auf einem Nicht-AEM-Server {#install-the-aem-service-credentials-on-a-non-aem-server}

Die Anwendung, die Aufrufe an AEM sendet, sollte in der Lage sein, auf die Anmeldeinformationen für AEM as a Cloud Service zuzugreifen, und diese als geheim behandeln.

### Generieren und Eintauschen eines JWT-Tokens gegen ein Zugriffs-Token {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Verwenden Sie die Anmeldeinformationen, um ein JWT-Token in einem Aufruf an den IMS-Service von Adobe zu erstellen und ein Zugriffs-Token abzurufen, das 24 Stunden gültig ist.

Die AEM CS-Service-Anmeldeinformationen können mithilfe von hierfür entwickelten Code-Beispielen gegen ein Zugriffstoken eingetauscht werden. Beispielcode ist im öffentlichen GitHub-Repository[ von ](https://github.com/adobe/aemcs-api-client-lib)Adobe verfügbar, das Code-Beispiele enthält, die Sie kopieren und für Ihre eigenen Projekte anpassen können. Beachten Sie, dass dieses Repository Beispiel-Code für Referenzzwecke enthält und nicht als produktionsbereite Bibliotheksabhängigkeit gepflegt wird.

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

>[!NOTE]
>Wenn mehrere Anmeldeinformationen vorhanden sind, verweisen Sie auf die entsprechende JSON-Datei für den API-Aufruf an AEM, der später aufgerufen wird.

### Aufrufen der AEM-API {#calling-the-aem-api}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`. Beispiel mit `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Festlegen der entsprechenden Berechtigungen für den technischen Kontobenutzer in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Zunächst muss in der Adobe Admin Console ein neues Produktprofil erstellt werden.

1. Navigieren Sie zur Adobe Admin Console unter [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/).
1. Klicken Sie auf den Link **Verwalten** unter der Spalte **Produkte und Dienste** auf der linken Seite.
1. Wählen Sie **AEM as a Cloud Service**.
1. Klicken Sie auf die Schaltfläche **Neues Profil.**

   ![Neues Profil](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Benennen Sie das Profil und drücken Sie **Speichern**.

   ![Profil speichern](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Wählen Sie das soeben erstellte Profil aus der Profilliste aus.
1. Wählen Sie **Benutzende hinzufügen** aus.

   ![Benutzende hinzufügen](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. Fügen Sie das soeben erstellte technische Konto hinzu (in diesem Fall `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) und klicken Sie auf **Speichern**.

   ![Tech-Konto hinzufügen](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. Warten Sie 10 Minuten, bis die Änderungen wirksam werden, und führen Sie einen API-Aufruf an AEM mit einem aus den neuen Anmeldeinformationen generierten Zugriffstoken durch. Als cURL-Befehl würde er ähnlich wie in diesem Beispiel dargestellt werden:

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Nachdem Sie den API-Aufruf durchgeführt haben, wird das Produktprofil als Benutzergruppe in der AEM as a Cloud Service-Autoreninstanz angezeigt, wobei das entsprechende technische Konto Mitglied dieser Gruppe ist.

Gehen Sie wie folgt vor, um diese Informationen zu überprüfen:

1. Melden Sie sich bei der Autoreninstanz an.
1. Navigieren Sie zu **Tools** > **Sicherheit** und klicken Sie auf die Karte **Gruppen**.
1. Suchen Sie den Namen des erstellten Profils in der Gruppenliste und klicken Sie darauf:

   ![Gruppenprofil](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. Wechseln Sie im folgenden Fenster zu **Mitglieder** und überprüfen Sie, ob das technische Konto dort korrekt aufgeführt ist:

   ![Mitglieder-Registerkarte](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


Alternativ können Sie auch überprüfen, ob das technische Konto in der Benutzerliste angezeigt wird, indem Sie die folgenden Schritte in der Autoreninstanz ausführen:

1. Navigieren Sie zu **Tools** > **Sicherheit** > **Benutzer**.
1. Überprüfen Sie, ob Ihr technisches Konto in der Benutzerliste aufgeführt ist, und klicken Sie darauf.
1. Klicken Sie auf die Registerkarte **Gruppen**, um zu überprüfen, ob die Benutzerin bzw. der Benutzer Teil der Gruppe ist, die Ihrem Produktprofil entspricht. Diese Person ist auch Mitglied einer Handvoll anderer Gruppen, einschließlich Mitwirkende:

   ![Gruppenzugehörigkeit](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Vor Mitte 2023, bevor mehrere Anmeldeinformationen erstellt werden konnten, wurden Kundinnen und Kunden nicht angeleitet, ein Produktprofil in der Adobe Admin Console zu erstellen. Daher war das technische Konto in der AEM as a Cloud Service-Instanz nicht mit einer anderen Gruppe außer „Mitwirkende“ verknüpft. Aus Gründen der Konsistenz wird empfohlen, für dieses technische Konto in der Adobe Admin Console wie oben beschrieben ein neues Produktprofil zu erstellen und das vorhandene technische Konto zu dieser Gruppe hinzuzufügen.

<u>**Einrichten der entsprechenden Gruppenberechtigungen**</u>

Konfigurieren Sie abschließend für die Gruppe die entsprechenden Berechtigungen, damit Sie Ihre APIs ordnungsgemäß aufrufen oder sperren können.

1. Melden Sie sich bei der entsprechenden Autoreninstanz an und navigieren Sie zu **Einstellungen** > **Sicherheit** > **Berechtigungen**
1. Suchen Sie im linken Bereich (in diesem Fall „Schreibgeschützte APIs“) nach dem Namen der dem Produktprofil entsprechenden Gruppe und wählen Sie sie aus:

   ![Nach Gruppe suchen](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Klicken Sie im folgenden Fenster auf die Bearbeiten-Schaltfläche:

   ![Bearbeiten von Berechtigungen](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Ändern Sie die Berechtigungen entsprechend und klicken Sie auf **Speichern**.

   ![Bestätigen der Bearbeitung von Berechtigungen](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>Weitere Informationen zum Adobe Identity Management System (IMS) und AEM-Benutzenden und -Gruppen. Siehe die [Dokumentation](/help/security/ims-support.md).

## Entwicklungsablauf {#developer-flow}

Entwicklerinnen und Entwickler möchten wahrscheinlich Tests mit einer Entwicklungsinstanz ihrer Nicht-AEM-Anwendung durchführen (entweder auf ihrem Laptop oder gehostet), die Anfragen an eine Entwicklungsumgebung von AEM as a Cloud Service sendet. Da Entwicklerinnen und Entwickler jedoch nicht unbedingt über IMS-Admin-Berechtigungen verfügen, kann Adobe nicht davon ausgehen, dass sie das im normalen Server-zu-Server-Fluss beschriebene JWT-Bearer-Token generieren können. Deshalb bieten wir Entwicklungspersonen einen Mechanismus, um direkt ein Zugriffs-Token zu generieren, das in Anfragen an AEM as a Cloud Service-Umgebungen verwendet werden kann, auf die sie Zugriff haben.

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

1. Navigieren Sie zum **Lokalen Token** unter **Integrationen**.
1. Klicken Sie auf **Lokales Entwicklungs-Token abrufen** in der Entwicklerkonsole, damit Sie ein Zugriffs-Token generieren können.

### Aufrufen der AEM-Anwendung mit einem Zugriffs-Token {#call-the-aem-application-with-an-access-token}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe vom Nicht-AEM-Programm an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`.

## Verlängern der Gültigkeit von Anmeldeinformationen {#refresh-credentials}

Standardmäßig laufen die Anmeldeinformationen für AEM as a Cloud Service nach einem Jahr ab. Um die Kontinuität des Service sicherzustellen, haben Entwicklerinnen und Entwickler die Möglichkeit, die Gültigkeit der Anmeldeinformationen zu verlängern, sodass sie für ein weiteres Jahr gültig bleiben.

Gehen Sie wie folgt vor, um diese Aktualisierungserweiterung zu erreichen:

* Verwenden Sie wie unten dargestellt in der Entwicklerkonsole die Schaltfläche **Zertifikat hinzufügen** unter **Integrationen** – **Technische Konten**.

  ![Aktualisieren von Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Nach dem Drücken der Schaltfläche wird ein Satz von Anmeldeinformationen generiert, der ein neues Zertifikat enthält. Installieren Sie die neuen Anmeldeinformationen auf Ihrem Nicht-AEM-Server und stellen Sie sicher, dass die Verbindung wie erwartet funktioniert, ohne die alten Anmeldeinformationen zu entfernen.
* Achten Sie darauf, dass beim Generieren des Zugriffs-Tokens die neuen Anmeldeinformationen anstelle der alten verwendet werden.
* Optional können Sie das vorherige Zertifikat widerrufen (und dann löschen), damit es nicht mehr zur Authentifizierung bei AEM as a Cloud Service verwendet werden kann.

## Widerrufen der Anmeldeinformationen {#credentials-revocation}

Wenn der private Schlüssel kompromittiert ist, müssen Sie Anmeldeinformationen mit einem neuen Zertifikat und einem neuen privaten Schlüssel erstellen. Nachdem Ihre Anwendung die neuen Anmeldeinformationen verwendet hat, um Zugriffs-Token zu generieren, können Sie die alten Zertifikate widerrufen und löschen, indem Sie Folgendes durchführen:

1. Fügen Sie zunächst den neuen Schlüssel hinzu. Dadurch werden Anmeldeinformationen mit einem neuen privaten Schlüssel und einem neuen Zertifikat generiert. Der neue private Schlüssel wird in der Benutzeroberfläche als **aktuell** markiert und wird somit für alle neuen Anmeldeinformationen für dieses technische Konto verwendet. Die mit den älteren privaten Schlüsseln verknüpften Anmeldeinformationen sind weiterhin gültig, bis sie widerrufen werden. Um sie zu widerrufen, wählen Sie das Symbol mit den drei Punkten (**…**) unter Ihrem aktuellen technischen Konto aus und danach die Option **Neuen privaten Schlüssel hinzufügen**:

   ![Neuen privaten Schlüssel hinzufügen](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. Wählen Sie bei der darauffolgenden Eingabeaufforderung **Hinzufügen** aus:

   ![Hinzufügen eines neuen privaten Schlüssels bestätigen](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Eine neue Registerkarte mit den neuen Anmeldeinformationen wird geöffnet und die Benutzeroberfläche wird aktualisiert, um beide privaten Schlüssel anzuzeigen, wobei der neue Schlüssel als **aktuell** markiert ist:

   ![Private Schlüssel in der Benutzeroberfläche](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installieren Sie die neuen Anmeldeinformationen auf dem Nicht-AEM-Server und stellen Sie sicher, dass die Verbindung erwartungsgemäß funktioniert. Siehe den [Abschnitt „Server-zu-Server-Fluss“](#the-server-to-server-flow), um Details zu erfahren.
1. Widerrufen Sie das alte Zertifikat, indem Sie die drei Punkte (**…**) rechts neben dem Zertifikat und dann **Widerrufen** auswählen:

   ![Zertifikat widerrufen](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Bestätigen Sie dann den Widerruf in der folgenden Aufforderung durch Auswahl der Schaltfläche **Widerrufen**:

   ![Widerrufen der Zertifikatsbestätigung](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Löschen Sie abschließend das kompromittierte Zertifikat.
