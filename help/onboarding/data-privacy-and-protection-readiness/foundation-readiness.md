---
title: Datenschutzbestimmungen - Adobe Experience Manager as a Cloud Service Foundation - Einhaltung von Datenschutzbestimmungen
description: Erfahren Sie mehr über die Unterstützung von Adobe Experience Manager as a Cloud Service Foundation für die verschiedenen Datenschutzbestimmungen. darunter die EU-Datenschutz-Grundverordnung (DSGVO), das kalifornische Verbraucherdatenschutzgesetz und die Einhaltung der Vorschriften bei der Implementierung eines neuen AEM als Cloud Service.
exl-id: 3a4b9d00-297d-4b1d-ae57-e75fbd5c490c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 32%

---

# Adobe Experience Manager as a Cloud Service Foundation - Einhaltung von Datenschutzbestimmungen {#aem-foundation-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion der Adobe auf Datenschutzprobleme und was dies für Sie als Adobe bedeutet, finden Sie im [Datenschutzzentrum der Adobe](https://www.adobe.com/privacy.html).

## AEM Foundation-Unterstützung für Datenschutz und Schutz {#aem-foundation-data-privacy-and-protection-support}

Auf AEM Foundation-Ebene werden die gespeicherten personenbezogenen Daten im Benutzerprofil gespeichert. Daher wird in diesem Artikel hauptsächlich beschrieben, wie Sie auf Benutzerprofile zugreifen und diese löschen, um Zugriffs- bzw. Löschanfragen zu beantworten.

## Zugreifen auf Benutzerprofile {#accessing-a-user-profile}

### Manuelle Schritte {#manual-steps}

1. Öffnen Sie die Konsole Benutzerverwaltung , indem Sie zu **[!UICONTROL Tools - Sicherheit - Benutzer]** navigieren oder direkt zu `https://<serveraddress>:<serverport>/security/users.html` navigieren.

<!--
   ![useradmin2](assets/useradmin2.png)
-->

1. Suchen Sie dann den jeweiligen Benutzer, indem Sie dessen Name in der Suchleiste oben auf der Seite eingeben:

   ![Konto suchen](assets/dpp-foundation-01.png)

1. Klicken Sie nun auf das Benutzerprofil, um es zu öffnen, und rufen Sie die Registerkarte **[!UICONTROL Details]** auf.

   ![Benutzerprofil](assets/dpp-foundation-02.png)

### HTTP-API {#http-api}

Wie bereits ausgeführt, bietet Adobe APIs, mit denen der Zugriff auf Benutzerdaten automatisiert werden kann. Es stehen verschiedene Arten von APIs zur Verfügung:

**UserProperties API**

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

Verwenden des Knotenpfads aus der Starteigenschaft der JSON-Payload, der vom obigen Befehl zurückgegeben wird:

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

3. Drücken Sie die Schaltfläche **Deaktivieren** im oberen Menü, um den Benutzer zu deaktivieren:

   ![Konto deaktivieren](assets/dpp-foundation-03.png)

4. Bestätigen Sie abschließend die Aktion.

   Die Benutzeroberfläche weist dann darauf hin, dass das Benutzerkonto deaktiviert wurde, indem es ausgegraut wurde und der Profilkarte eine Sperre hinzufügt:

   ![Konto deaktiviert](assets/dpp-foundation-04.png)

### Benutzerprofilinformationen löschen {#delete-user-profile-information}

>[!NOTE]
>
>Für AEM als Cloud Service ist kein manuelles Verfahren über die Benutzeroberfläche zum Löschen eines Benutzerprofils verfügbar, da auf CRXDE nicht zugegriffen werden kann.

### HTTP-API {#http-api-1}

Die folgenden Verfahren verwenden das `curl` Befehlszeilenwerkzeug, um zu veranschaulichen, wie Benutzer mit der **[!UICONTROL Aufnahme]** deaktiviert und die entsprechenden Profile am Standardspeicherort gelöscht werden können `userId`.

**Ermitteln der Benutzerstartseite:**

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**Deaktivieren des Benutzers:**

Verwenden des Knotenpfads aus der Starteigenschaft der JSON-Payload, der vom obigen Befehl zurückgegeben wird:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (Data Privacy in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

**Löschen von Benutzerprofilen**

Verwenden Sie den Knotenpfad der Starteigenschaft der JSON-Payload, der vom Konto-Erkennungsbefehl zurückgegeben wird, und die bekannten Out-of-the-box-Knoten-Speicherorte:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
