---
title: Datenschutzbestimmungen – Adobe Experience Manager as a Cloud Service Foundation – Einhaltung von Datenschutzbestimmungen
description: Erfahren Sie mehr über die Foundation-Unterstützung von Adobe Experience Manager as a Cloud Service für die verschiedenen Datenschutzbestimmungen. Dieser Artikel enthält die Datenschutz-Grundverordnung (DSGVO) der EU, den California Consumer Privacy Act und eine Beschreibung, wie die Konformität mit diesen Vorschriften bei der Implementierung eines neuen AEM as a Cloud Service-Projekts gewährleistet wird.
exl-id: 3a4b9d00-297d-4b1d-ae57-e75fbd5c490c
feature: Compliance
role: Admin, Developer, Leader
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service Foundation – Einhaltung von Datenschutzbestimmungen {#aem-foundation-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Antwort von Adobe auf Datenschutzprobleme und was dies für Sie als Adobe-Kundin bzw. -Kunden bedeutet, finden Sie im [Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy.html).

## AEM Foundation – Unterstützung für Datenschutz {#aem-foundation-data-privacy-and-protection-support}

Auf AEM Foundation-Ebene werden personenbezogene Daten im Benutzerprofil gespeichert. Dementsprechend wird in diesem Artikel in erster Linie erläutert, wie der Zugriff auf und das Löschen von Benutzerprofilen erfolgt, um Zugriffs- bzw. Löschanfragen bearbeiten zu können.

## Zugreifen auf Benutzerprofile {#accessing-a-user-profile}

### Manuelle Schritte {#manual-steps}

1. Öffnen Sie die Konsole für die Benutzerverwaltung, indem Sie zu **[!UICONTROL Tools > Sicherheit > Benutzer]** gehen oder die Seite `https://<serveraddress>:<serverport>/security/users.html` direkt aufrufen.

<!--
   ![useradmin2](assets/useradmin2.png)
-->

1. Suchen Sie dann den jeweiligen Benutzer, indem Sie dessen Name in der Suchleiste oben auf der Seite eingeben:

   ![Konto suchen](assets/dpp-foundation-01.png)

1. Klicken Sie nun auf das Benutzerprofil, um es zu öffnen, und rufen Sie die Registerkarte **[!UICONTROL Details]** auf.

   ![Benutzerprofil](assets/dpp-foundation-02.png)

### -HTTP-API {#http-api}

Wie bereits ausgeführt, bietet Adobe APIs, mit denen der Zugriff auf Benutzerdaten automatisiert werden kann. Es stehen verschiedene Arten von APIs zur Verfügung:

**UserProperties-API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**Sling-API**

**Ermitteln der Benutzerstartseite:**

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**Abrufen von Benutzerdaten:**

Verwenden Sie dazu den Knotenpfad der über den vorangegangenen Befehl ausgegebenen Home-Eigenschaft der JSON-Payload:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## Deaktivieren von Benutzern und Löschen der zugehörigen Profile {#disabling-a-user-and-deleting-the-associated-profiles}

### Deaktivieren von Benutzern {#disable-user}

1. Öffnen Sie die Konsole für die Benutzerverwaltung und suchen Sie nach dem entsprechenden Benutzer, wie oben beschrieben.
2. Bewegen Sie den Mauszeiger über den Benutzer und klicken Sie auf das Auswahlsymbol. Das Profil wird grau, was anzeigt, dass es ausgewählt wurde.

3. Klicken Sie im oberen Menü auf **Deaktivieren**, um die Benutzerin bzw. den Benutzer zu deaktivieren (auszuschalten):

   ![Konto deaktivieren](assets/dpp-foundation-03.png)

4. Bestätigen Sie abschließend die Aktion.

   Die Benutzeroberfläche zeigt an, dass das Benutzerkonto deaktiviert wurde, indem es ausgegraut und mit einem Schlosssymbol auf der Profilkarte angezeigt wird.

   ![Konto deaktiviert](assets/dpp-foundation-04.png)

### Löschen von Benutzerprofilinformationen {#delete-user-profile-information}

>[!NOTE]
>
>Für AEM as a Cloud Service ist zum Löschen eines Benutzerprofils über die Benutzeroberfläche kein manuelles Verfahren verfügbar, da nicht auf CRXDE zugegriffen werden kann.

### HTTP-API {#http-api-1}

Die folgenden Verfahren verwenden das Befehlszeilen-Tool `curl`, um zu veranschaulichen, wie die Person mit der `userId` **[!UICONTROL cavery]** deaktiviert und ihre Profile am Standardspeicherort gelöscht werden können.

**Ermitteln der Benutzerstartseite:**

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**Deaktivieren des Benutzers:**

Verwenden Sie dazu den Knotenpfad der über den vorangegangenen Befehl ausgegebenen home-Eigenschaft der JSON-Payload:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (Data Privacy in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

**Löschen von Benutzerprofilen**

Verwenden Sie dazu den Knotenpfad der Home-Eigenschaft der JSON-Payload, der über den Befehl zur Ermittlung der Benutzerstartseite ausgegeben wurde, sowie die bekannten vorkonfigurierten Speicherorte des Profilknotens:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
