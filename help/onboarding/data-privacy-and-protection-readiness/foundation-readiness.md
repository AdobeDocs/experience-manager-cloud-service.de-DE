---
title: Datenschutz- und Datenschutzvorschriften - Adobe Experience Manager als Cloud Service Foundation Readiness
description: 'Erfahren Sie mehr über Adobe Experience Manager als Unterstützung der Cloud Service Foundation für die verschiedenen Datenschutzbestimmungen und Datenschutzbestimmungen. einschließlich der EU-Datenschutzverordnung (GDPR), des kalifornischen Datenschutzgesetzes für Verbraucher und wie bei der Implementierung eines neuen AEM als Cloud-Service-Projekt einzuhalten ist. '
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 32%

---


# Adobe Experience Manager als Cloud Service Foundation Readiness for Data Protection and Data Privacy Regulations {#aem-foundation-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Für Informationen zu Datenschutzbestimmungen und Datenschutzbestimmungen wenden Sie sich bitte an die Rechtsabteilung Ihrer Firma.

>[!NOTE]
>
>Weitere Informationen über die Reaktion von Adobe auf Datenschutzprobleme und was dies für Sie als Adobe-Kunde bedeutet, finden Sie im Datenschutzzentrum von [Adobe](https://www.adobe.com/privacy.html).

## Unterstützung von AEM Foundation für Datenschutz und Datenschutz {#aem-foundation-data-privacy-and-protection-support}

Auf AEM Foundation-Ebene werden die gespeicherten personenbezogenen Daten im User Profil gespeichert. Die Informationen in diesem Artikel behandeln daher in erster Linie das Zugreifen auf und Löschen von Profilen, das Ansprechen von Zugänglichkeits- bzw. Löschanforderungen.

## Zugreifen auf Benutzerprofile {#accessing-a-user-profile}

### Manuelle Schritte {#manual-steps}

1. Open the User Administration console, by browsing to **[!UICONTROL Tools - Security - Users]** or by browsing directly to `https://<serveraddress>:<serverport>/security/users.html`

<!--
   ![useradmin2](assets/useradmin2.png)
-->

1. Suchen Sie dann den jeweiligen Benutzer, indem Sie dessen Name in der Suchleiste oben auf der Seite eingeben:

   ![Konto suchen](assets/dpp-foundation-01.png)

1. Klicken Sie nun auf das Benutzerprofil, um es zu öffnen, und rufen Sie die Registerkarte **[!UICONTROL Details]** auf.

   ![user Profil](assets/dpp-foundation-02.png)

### HTTP-API {#http-api}

Wie bereits ausgeführt, bietet Adobe APIs, mit denen der Zugriff auf Benutzerdaten automatisiert werden kann. Es stehen verschiedene Arten von APIs zur Verfügung:

**UserProperties API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**Sling API**

**Ermitteln der Benutzerstartseite:**

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**Abrufen von Benutzerdaten:**

Verwenden des Knotenpfads aus der Eigenschaft home der JSON-Payload, der vom oben genannten Befehl zurückgegeben wird:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## Deaktivieren von Benutzern und Löschen der zugehörigen Profile {#disabling-a-user-and-deleting-the-associated-profiles}

### Benutzer deaktivieren {#disable-user}

1. Öffnen Sie die Konsole für die Benutzerverwaltung und suchen Sie nach dem entsprechenden Benutzer, wie oben beschrieben.
2. Bewegen Sie den Mauszeiger über den Benutzer und klicken Sie auf das Auswahlsymbol. Das ausgewählte Profil wird nun in grau angezeigt.

3. Press the **Disable** button in the upper menu to disable the user:

   ![Konto deaktivieren](assets/dpp-foundation-03.png)

4. Bestätigen Sie abschließend die Aktion.

   Die Benutzeroberfläche weist dann darauf hin, dass das Benutzerkonto deaktiviert wurde, indem die Profil-Karte abgegraut und eine Sperre hinzugefügt wurde:

   ![Konto deaktiviert](assets/dpp-foundation-04.png)

### Benutzerprofilinformationen löschen {#delete-user-profile-information}

>[!NOTE]
>
> Für AEM als Cloud-Dienst ist in der Benutzeroberfläche kein manuelles Verfahren zum Löschen eines Profils verfügbar, da auf CRXDE nicht zugegriffen werden kann.

### HTTP-API {#http-api-1}

Die folgenden Verfahren verwenden das `curl` Befehlszeilenwerkzeug, um zu veranschaulichen, wie Benutzer mit der **[!UICONTROL Aufnahme]** deaktiviert und die entsprechenden Profile am Standardspeicherort gelöscht werden können `userId`.

**Ermitteln der Benutzerstartseite:**

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**Deaktivieren des Benutzers:**

Verwenden des Knotenpfads aus der Eigenschaft home der JSON-Payload, der vom oben genannten Befehl zurückgegeben wird:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (Data Privacy in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

**Löschen von Benutzerprofilen**

Verwenden des Knotenpfads aus der Eigenschaft home der JSON-Payload, der vom Befehl zur Kontosuche zurückgegeben wird, und der bekannten Out-of-the-Box-Profil-Knotenpunkte:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
