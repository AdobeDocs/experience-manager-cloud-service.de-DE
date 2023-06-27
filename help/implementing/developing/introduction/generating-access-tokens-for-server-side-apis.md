---
title: Generieren von Zugriffstoken für serverseitige APIs
description: Erfahren Sie, wie Sie die Kommunikation zwischen einem Drittanbieterserver und AEM as a Cloud Service erleichtern können, indem Sie ein sicheres JWT-Token generieren.
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '2090'
ht-degree: 40%

---

# Generieren von Zugriffstoken für serverseitige APIs {#generating-access-tokens-for-server-side-apis}

Einige Architekturen müssen AEM as a Cloud Service von einer Programm aufrufen, das auf einem Server außerhalb der AEM-Infrastruktur gehostet wird. Dies könnte eine Mobile App sein, die einen Server aufruft, welcher anschließend API-Anfragen an AEM as a Cloud Service sendet.

Der Server-zu-Server-Fluss wird unten beschrieben, zusammen mit einem vereinfachten Fluss für die Entwicklung. Die [Entwicklerkonsole](development-guidelines.md#crxde-lite-and-developer-console) von AEM as a Cloud Service dient dazu, Token zu generieren, die für den Authentifizierungsprozess benötigt werden.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Der Server-zu-Server-Fluss {#the-server-to-server-flow}

Benutzer mit der Rolle &quot;IMS-Organisationsadministrator&quot;und die Mitglied des AEM-Benutzerprofils oder AEM Produktprofils &quot;Administratoren&quot;in der AEM-Autoreninstanz sind, können eine Reihe von Anmeldeinformationen aus AEM as a Cloud Service generieren. Jede Berechtigung ist eine JSON-Payload, die ein Zertifikat (den öffentlichen Schlüssel), einen privaten Schlüssel und ein technisches Konto enthält, das aus einem `clientId` und `clientSecret`. Diese Anmeldeinformationen können später von einem Benutzer mit der Rolle &quot;Administrator für die AEM as a Cloud Service Umgebung&quot;abgerufen werden. Sie sollten auf einem Nicht-AEM-Server installiert und sorgfältig wie ein geheimer Schlüssel behandelt werden. Diese Datei im JSON-Format enthält alle Daten, die zur Integration mit einer AEM as a Cloud Service-API erforderlich sind. Die Daten werden zum Erstellen eines signierten JWT-Tokens verwendet, das mit Adobe Identity Management Services (IMS) gegen ein IMS-Zugriffs-Token eingetauscht wird. Dieses Zugriffs-Token kann dann als Inhaberauthentifizierungs-Token für Anfragen an AEM as a Cloud Service verwendet werden. Das Zertifikat in den Anmeldedaten läuft standardmäßig nach einem Jahr ab, kann jedoch bei Bedarf aktualisiert werden, wie beschrieben [here](#refresh-credentials).

Der Server-zu-Server-Fluss umfasst die folgenden Schritte:

* Rufen Sie die Anmeldeinformationen auf AEM as a Cloud Service aus der Developer Console ab.
* Installieren Sie die Anmeldeinformationen für AEM as a Cloud Service auf einem Nicht-AEM-Server, der Aufrufe an AEM sendet.
* Generieren eines JWT-Tokens und Eintauschen dieses Tokens gegen ein Zugriffs-Token über die IMS-APIs von Adobe
* Aufrufen der AEM-API mit dem Zugriffs-Token als Inhaberauthentifizierungs-Token
* Festlegen der entsprechenden Berechtigungen für technische Kontobenutzer in der AEM-Umgebung

### Abrufen der Anmeldeinformationenn für AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Benutzer mit Zugriff auf die AEM as a Cloud Service Entwicklerkonsole finden die Registerkarte Integrationen in der Entwicklerkonsole für eine bestimmte Umgebung. Benutzer mit der Rolle &quot;Administrator für die AEM as a Cloud Service Umgebung&quot;können Anmeldeinformationen erstellen, anzeigen oder verwalten.

Klicken **Neues technisches Konto erstellen**, wird ein Satz von Anmeldeinformationen erstellt, der Client-ID, Client-Geheimnis, privaten Schlüssel, Zertifikat und Konfiguration für die Autoren- und Veröffentlichungsschicht der Umgebung enthält, unabhängig von der Pod-Auswahl.

![Erstellen eines neuen technischen Kontos](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Eine neue Registerkarte im Browser wird mit den Anmeldedaten geöffnet. Sie können diese Ansicht verwenden, um die Anmeldeinformationen herunterzuladen, indem Sie auf das Download-Symbol neben dem Statustitel klicken:

![Herunterladen von Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Nachdem die Anmeldeinformationen erstellt wurden, erscheinen sie unter der Registerkarte **Technische Konten** im Abschnitt **Integrationen**:

![Anzeigen der Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Benutzende können die Anmeldeinformationen später mit der Aktion „Anzeigen“ einsehen. Darüber hinaus können Benutzer, wie weiter unten im Artikel beschrieben, die Anmeldeinformationen für dasselbe technische Konto bearbeiten. Sie führen diese Bearbeitung durch Erstellen eines neuen privaten Schlüssels oder Zertifikats durch, falls das Zertifikat erneuert oder widerrufen werden muss.

Benutzer mit der AEM as a Cloud Service Umgebungsadministratorrolle können später Anmeldeinformationen für zusätzliche technische Konten erstellen. Diese Funktion ist nützlich, wenn verschiedene APIs unterschiedliche Zugriffsanforderungen haben. Zum Beispiel Lese- oder Lese-Schreib.

>[!NOTE]
>
>Kunden können bis zu zehn technische Konten erstellen, einschließlich der Konten, die bereits gelöscht wurden.

>[!IMPORTANT]
>
>Ein IMS-Organisationsadministrator (normalerweise derselbe Benutzer, der die Umgebung über Cloud Manager bereitgestellt hat), der auch Mitglied des AEM-Benutzerprofils oder AEM Administrator-Produktprofils in der AEM-Autoreninstanz ist, muss zuerst auf die Developer Console zugreifen. Klicken Sie anschließend auf **Neues technisches Konto erstellen** , damit die Anmeldeinformationen von einem Benutzer mit Administratorberechtigungen für die AEM as a Cloud Service Umgebung generiert und später abgerufen werden. Wenn der IMS-Organisationsadministrator das technische Konto noch nicht erstellt hat, wird er in einer Meldung darüber informiert, dass er die Rolle &quot;IMS-Organisationsadministrator&quot;benötigt.

### Installieren Sie die AEM-Dienstanmeldeinformationen auf einem Nicht-AEM-Server {#install-the-aem-service-credentials-on-a-non-aem-server}

Die Anwendung, die AEM aufruft, sollte auf die Anmeldeinformationen für AEM as a Cloud Service zugreifen und sie als geheim behandeln können.

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

>[!NOTE]
>Wenn mehrere Anmeldeinformationen vorhanden sind, verweisen Sie auf die entsprechende JSON-Datei für den API-Aufruf an AEM , der später aufgerufen wird.

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
1. Drücken Sie auf die Schaltfläche **Neues Profil.**

   ![Neues Profil](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Benennen Sie das Profil und drücken Sie **Speichern**.

   ![Profil speichern](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Wählen Sie das von Ihnen erstellte Profil aus der Profilliste aus.
1. Auswählen **Benutzer hinzufügen**.

   ![Benutzende hinzufügen](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. Fügen Sie das von Ihnen erstellte technische Konto hinzu (in diesem Fall `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) und klicken Sie auf **Speichern**.

   ![Tech-Konto hinzufügen](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. Warten Sie 10 Minuten, bis die Änderungen wirksam werden, und führen Sie einen API-Aufruf an AEM mit einem aus den neuen Anmeldeinformationen generierten Zugriffstoken durch. Als cURL-Befehl würde er ähnlich wie in diesem Beispiel dargestellt werden:

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Nachdem Sie den API-Aufruf durchgeführt haben, wird das Produktprofil als Benutzergruppe in der AEM as a Cloud Service Autoreninstanz angezeigt, wobei das entsprechende technische Konto Mitglied dieser Gruppe ist.

Gehen Sie wie folgt vor, um diese Informationen zu überprüfen:

1. Melden Sie sich bei der Autoreninstanz an.
1. Navigieren Sie zu **Instrumente** > **Sicherheit** und klicken Sie dann auf **Gruppen** Karte.
1. Suchen Sie den Namen des von Ihnen erstellten Profils in der Gruppenliste und klicken Sie darauf:

   ![Gruppenprofil](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. Wechseln Sie im folgenden Fenster zu **Mitglieder** und überprüfen Sie, ob das technische Konto dort korrekt aufgeführt ist:

   ![Mitglieder-Registerkarte](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


Alternativ können Sie auch überprüfen, ob das technische Konto in der Liste des Benutzers angezeigt wird, indem Sie die folgenden Schritte in der Autoreninstanz ausführen:

1. Navigieren Sie zu **Tools** > **Sicherheit** > **Benutzer**.
1. Überprüfen Sie, ob Ihr technisches Konto die Benutzerliste ist, und wählen Sie es aus.
1. Klicken Sie auf **Gruppen** -Tab, damit Sie überprüfen können, ob der Benutzer Teil der Gruppe ist, die Ihrem Produktprofil entspricht. Dieser Benutzer ist auch Mitglied einer Handvoll anderer Gruppen, einschließlich Mitwirkender:

   ![Gruppenmitgliedschaft](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Vor Mitte 2023, bevor mehrere Anmeldeinformationen erstellt werden konnten, wurden Kunden nicht dazu geführt, ein Produktprofil in der Adobe Admin Console zu erstellen. Daher war das technische Konto in der AEM as a Cloud Service Instanz nicht mit einer anderen Gruppe als &quot;Mitwirkende&quot;verknüpft. Aus Gründen der Konsistenz wird empfohlen, für dieses technische Konto ein Produktprofil in der Adobe Admin Console zu erstellen, wie oben beschrieben, und das vorhandene technische Konto dieser Gruppe hinzuzufügen.

<u>**Festlegen der entsprechenden Gruppenberechtigungen**</u>

Konfigurieren Sie abschließend die Gruppe mit den erforderlichen Berechtigungen, damit Sie Ihre APIs entsprechend aufrufen oder sperren können.

1. Melden Sie sich bei der entsprechenden Autoreninstanz an und navigieren Sie zu **Einstellungen** > **Sicherheit** > **Berechtigungen**
1. Suchen Sie im linken Bereich (in diesem Fall &quot;Schreibgeschützte APIs&quot;) nach dem Namen der Gruppe, die dem Produktprofil entspricht (in diesem Fall &quot;Schreibgeschützte APIs&quot;), und wählen Sie sie aus:

   ![Nach Gruppe suchen](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Klicken Sie im folgenden Fenster auf die Bearbeiten-Schaltfläche:

   ![Bearbeiten von Berechtigungen](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Ändern Sie die Berechtigungen entsprechend und klicken Sie auf **Speichern**.

   ![Bestätigen der Bearbeitung von Berechtigungen](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>Erfahren Sie mehr über die Adobe Identity Management System (IMS) und AEM Benutzer und Gruppen. Siehe [Dokumentation](/help/security/ims-support.md).

## Entwicklungsablauf {#developer-flow}

Entwickler möchten wahrscheinlich mit einer Entwicklungsinstanz ihrer AEM (entweder auf ihrem Laptop ausgeführt oder gehostet) testen, die Anforderungen an eine Entwicklungsumgebung AEM as a Cloud Service Entwicklungsumgebung sendet. Da Entwickler jedoch nicht unbedingt über IMS-Administratorrollenberechtigungen verfügen, kann Adobe nicht davon ausgehen, dass sie den im regulären Server-zu-Server-Fluss beschriebenen JWT-Träger generieren können. Daher bietet Adobe einen Mechanismus, mit dem Entwickler direkt ein Zugriffstoken generieren können, das in Anfragen an Umgebungen auf AEM as a Cloud Service, auf die sie Zugriff haben, verwendet werden kann.

Informationen zu den erforderlichen Berechtigungen zur Verwendung der Entwicklerkonsole von AEM as a Cloud Service finden Sie in der Dokumentation zu [Entwicklerrichtlinien](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
>
>Das lokale Zugriffs-Token für Entwickler ist maximal 24 Stunden lang gültig. Danach muss es mit derselben Methode neu generiert werden.

Entwickler können dieses Token verwenden, um Aufrufe von ihrem Nicht-AEM-Testprogramm an eine AEM as a Cloud Service-Umgebung zu senden. In der Regel verwendet der Entwickler dieses Token mit der AEM Anwendung auf seinem eigenen Laptop. Außerdem ist AEM as a Cloud Service normalerweise keine Produktionsumgebung.

Der Entwicklungsablauf umfasst die folgenden Schritte:

* Erstellen eines Zugriffs-Tokens über die Entwicklerkonsole
* Aufrufen des AEM-Programms mit dem Zugriffs-Token

Entwickler können auch API-Aufrufe an ein AEM-Projekt auf ihrem lokalen Computer durchführen. In diesem Fall ist kein Zugriffs-Token erforderlich.

### Generieren des Zugriffs-Tokens {#generating-the-access-token}

1. Navigieren Sie zum **Lokalen Token** unter **Integrationen**.
1. Klicken **Abrufen des lokalen Entwicklungstokens** in der Entwicklerkonsole , damit Sie ein Zugriffstoken generieren können.

### Aufrufen der AEM-Anwendung mit einem Zugriffs-Token {#call-the-aem-application-with-an-access-token}

Senden Sie die entsprechenden Server-zu-Server-API-Aufrufe vom Nicht-AEM-Programm an eine AEM as a Cloud Service-Umgebung, einschließlich des Zugriffs-Tokens im Header. Verwenden Sie daher für den „Authorization“-Header den Wert `"Bearer <access_token>"`.

## Verlängern der Gültigkeit von Anmeldeinformationen {#refresh-credentials}

Standardmäßig laufen die Anmeldedaten AEM as a Cloud Service nach einem Jahr ab. Um die Kontinuität des Service sicherzustellen, haben Entwickler die Möglichkeit, die Gültigkeit der Anmeldeinformationen zu verlängern, sodass sie für ein weiteres Jahr gültig bleiben.

Gehen Sie wie folgt vor, um diese Aktualisierungserweiterung zu erreichen:

* Verwenden Sie wie unten dargestellt in der Entwicklerkonsole die Schaltfläche **Zertifikat hinzufügen** unter **Integrationen** – **Technische Konten**.

  ![Aktualisieren von Anmeldeinformationen](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Nachdem Sie auf die Schaltfläche geklickt haben, wird eine Reihe von Anmeldeinformationen generiert, die ein neues Zertifikat enthalten. Installieren Sie die neuen Anmeldedaten auf Ihrem AEM-Server und stellen Sie sicher, dass die Verbindung wie erwartet funktioniert, ohne dass die alten Anmeldedaten entfernt werden.
* Stellen Sie sicher, dass beim Generieren des Zugriffstokens die neuen Anmeldeinformationen anstelle der alten verwendet werden.
* Optional können Sie das vorherige Zertifikat widerrufen (und dann löschen), damit es nicht mehr zur Authentifizierung bei AEM as a Cloud Service verwendet werden kann.

## Widerrufen der Anmeldeinformationen {#credentials-revocation}

Wenn der private Schlüssel kompromittiert ist, müssen Sie Anmeldeinformationen mit einem neuen Zertifikat und einem neuen privaten Schlüssel erstellen. Nachdem Ihre Anwendung die neuen Anmeldeinformationen verwendet hat, um Zugriffstoken zu generieren, können Sie die alten Zertifikate widerrufen und löschen, indem Sie Folgendes durchführen:

1. Fügen Sie zunächst den neuen Schlüssel hinzu. Dieser Schlüssel generiert Anmeldeinformationen mit einem neuen privaten Schlüssel und einem neuen Zertifikat. Der neue private Schlüssel wird in der Benutzeroberfläche als **current** und wird daher für alle neuen Anmeldedaten für dieses technische Konto verwendet. Die mit den älteren privaten Schlüsseln verknüpften Anmeldeinformationen sind weiterhin gültig, bis sie widerrufen werden. Wählen Sie die drei Punkte (**...**) unter Ihrem aktuellen technischen Konto und wählen Sie dann **Neuen privaten Schlüssel hinzufügen**:

   ![Neuen privaten Schlüssel hinzufügen](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. Auswählen **Hinzufügen** an der folgenden Eingabeaufforderung:

   ![Hinzufügen eines neuen privaten Schlüssels bestätigen](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Eine neue Registerkarte &quot;Durchsuchen&quot;mit den neuen Anmeldedaten wird geöffnet und die Benutzeroberfläche wird aktualisiert, um beide privaten Schlüssel anzuzeigen, wobei der neue als **current**:

   ![Private Schlüssel in der Benutzeroberfläche](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installieren Sie die neuen Anmeldeinformationen auf dem Nicht-AEM-Server und stellen Sie sicher, dass die Verbindung erwartungsgemäß funktioniert. Siehe [Abschnitt &quot;Server-zu-Server-Fluss&quot;](#the-server-to-server-flow) für Details.
1. Rufen Sie das alte Zertifikat auf, indem Sie die drei Punkte (**...**) rechts neben dem Zertifikat und wählen Sie **Sperren**:

   ![Zertifikat widerrufen](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Bestätigen Sie dann den Widerruf in der folgenden Aufforderung durch Auswahl der Schaltfläche **Widerrufen**:

   ![Widerrufen der Zertifikatsbestätigung](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Löschen Sie abschließend das kompromittierte Zertifikat.
