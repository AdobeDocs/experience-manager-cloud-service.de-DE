---
title: '[!DNL Adobe Experience Manager] as a Cloud Service Prerelease Channel'
description: '[!DNL Adobe Experience Manager] as a Cloud Service Prerelease Channel'
source-git-commit: 4ee9a5744cdcec00dd497a00b0d8dbf288a5adcb
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 3%

---


# [!DNL Adobe Experience Manager] as a Cloud Service Prerelease Channel  {#prerelease-channel}


## Einführung {#introduction}

[!DNL Adobe Experience Manager] as a Cloud Service bietet monatlich neue Funktionen, entsprechend der Roadmap für  [Experience Manager-Releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=en#aem-as-cloud-service). Um sich mit den für den folgenden Monat geplanten Funktionen vertraut zu machen, können Kunden den Kanal für die Vorabversion abonnieren, auf den über eine entsprechende Konfiguration in standardmäßigen Programmentwicklungsumgebungen oder in beliebigen Sandbox-Programmumgebungen zugegriffen werden kann. Kunden können eine Vorschau von Änderungen an der Sites-Konsole anzeigen sowie Code für alle neuen Vorabversions-APIs erstellen.

Die Liste der Funktionen der Vorabversion für einen bestimmten Monat wird in den [monatlichen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md) veröffentlicht.

>[!VIDEO](/help/release-notes/assets/prerelease-overview.mp4)

## Aktivieren der Vorabversion {#enable-prerelease}

Die Funktionen der Vorabversion können auf unterschiedliche Weise genutzt werden:

* Cloud-Umgebungen (Standard-Programmentwicklungsumgebungen oder beliebige Sandbox-Programmumgebungstypen)
* Lokales SDK

### Cloud-Umgebungen {#cloud-environments}

So zeigen Sie neue Funktionen in der Sites-Konsole in Cloud-Entwicklungsumgebungen sowie das Ergebnis von Projektanpassungen an:

* Setzen Sie mithilfe des Umgebungsvariablen-Endpunkts [Cloud Manager-APIs ](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchEnvironmentVariables) die Umgebungsvariable **AEM_RELEASE_CHANNEL** auf den Wert **prerelease**.

```
PATCH /program/{programId}/environment/{environmentId}/variables
[
        {
                "name" : "AEM_RELEASE_CHANNEL",
                "value" : "prerelease",
                "type" : "string"
        }
]
```

Die Cloud Manager-CLI kann auch gemäß den Anweisungen unter [https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) verwendet werden.
```aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL “prerelease”```


Die Variable kann gelöscht oder auf einen anderen Wert zurückgesetzt werden, wenn Sie möchten, dass die Umgebung zum Verhalten des normalen Kanals (Nicht-Vorabversion) wiederhergestellt wird.

### Lokales SDK {#local-sdk}

Neue Funktionen werden in der Sites-Konsole im lokalen Schnellstart-SDK angezeigt und in der Vorabversion können Sie Code gegen neue APIs verarbeiten, indem Sie Ihr Maven-Projekt auf die Vorabversion `API Jar` in Maven Central verweisen. Sie können diese Vorabversionsfunktionen auch auf Ihrem lokalen Computer sehen, indem Sie das reguläre Schnellstart-SDK im Vorabversionsmodus starten:

* Laden Sie das SDK aus dem Software Distribution-Portal herunter und installieren Sie es wie unter [Zugriff auf das AEM als Cloud Service-SDK](/help/implementing/developing/aem-as-a-cloud-service-sdk.md#accessing-the-aem-as-a-cloud-service-sdk.) beschrieben.
* Fügen Sie beim Starten des SDK-Schnellstarts das Argument `-r prerelease` hinzu.
* Der Wert ist *sticky*, sodass er nur beim ersten Start ausgewählt werden kann. Installieren Sie das SDK neu, um die Befehlszeilenoption zu ändern.

Da es zwischen den monatlichen Funktionsveröffentlichungen mehrere AEM Wartungsversionen geben kann, können Sie diese neuen SDKs herunterladen und in Maven-Projekten auf die neuen SDK-API-JAR-Versionen verweisen. Die Wartungsversionen fügen keine zusätzlichen Vorabversionsfunktionen hinzu, könnten aber andere kleinere Änderungen wie Fehlerbehebungen, Sicherheitskorrekturen und Leistungsverbesserungen umfassen.
Javadocs werden in Maven Central veröffentlicht.

So erstellen Sie mit dem Vorabversions-SDK:

1. ändern Sie die pom.xml Ihres Maven-Projekts, um auf eine bestimmte Vorabversion-SDK-API-JAR zu verweisen, die in der Maven-Zentrale veröffentlicht wird. Es enthält jede neue Java-API für die Funktionen der Vorabversion und ist von der SDK-API-JAR-Datei abhängig. Es verwendet dieselbe Version.

   Hier finden Sie beispielsweise einen Ausschnitt aus dem Abschnitt zur Abhängigkeitsverwaltung des übergeordneten Poms, der auf das reguläre API-JAR verweist:

   ```
   <dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-sdk-api</artifactId>
            <version>${aem.sdk.api}</version>
            <scope>provided</scope>
        </dependency>
   ```

   Und dann die Verwendung in einem Modul:

   ```
    <dependencies>
     <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-sdk-api</artifactId>
     </dependency>
   ```

   Um zum Vorabversions-SDK zu wechseln, ändern Sie einfach die Abhängigkeit von `com.adobe.aem:aem-sdk-api` zu `com.adobe.aem:aem-prerelease-sdk-api` wie unten beschrieben:

   ```
   <dependencyManagement>
    <dependencies>
      <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-prerelease-sdk-api</artifactId>
            <version>${aem.sdk.api}</version>
            <scope>provided</scope>
      </dependency>
   <dependencies>
      <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-prerelease-sdk-api</artifactId>
      </dependency>
   ```

   Wie üblich können einzelne Projekte die Abhängigkeit verwenden.

1. Bereitstellen auf Ihrem lokalen Server
1. Wenn Sie sich davon überzeugt haben, dass sie lokal wie erwartet funktioniert, übertragen Sie den Code auf eine Entwicklungsverzweigung und verwenden Sie eine Nicht-Produktions-Pipeline von Cloud Manager, um sie in einer Umgebung bereitzustellen, die den Vorabversionskanal abonniert

>[!CAUTION]
Die `aem-prerelease-sdk-api` artifactId darf bei der Bereitstellung in der Staging- oder Produktionsumgebung nie verwendet werden. Verwenden Sie immer aem-sdk-api bei der Bereitstellung über die Produktions-Pipeline. Ebenso sollten Code, der auf Vorabversions-APIs verweist, nicht über die Produktions-Pipeline bereitgestellt werden.

Das [AEM CS SDK-Build Analyzer-Maven-Plug-in v1.0 und höher](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de#developing) erkennt, ob die Vorabversion-API in einem Projekt verwendet wird, indem die Abhängigkeiten überprüft werden. Wenn der Analyzer es findet, verwendet er die Vorabversion-SDK-API, um das Projekt zu analysieren.

## Besonderheiten {#considerations}

Beim Kanal für die Vorabversion sind einige Punkte zu beachten:

* Einige Funktionen, die in der Version für den nächsten Monat eingeführt werden, sind möglicherweise nicht im Kanal für die Vorabversion enthalten.
* Die Funktionen in der Vorabversion werden durch eine strenge Qualitätssicherung umgesetzt und sollen anstelle der Beta-Qualität als Funktionsbeendigung dienen. Wenn Sie Probleme bemerken, melden Sie diese, genau wie Sie es tun würden, wenn Sie Fehler in Funktionen in einer regulären AEM-Version vermuten würden.
* Um festzustellen, ob eine Umgebung für den Kanal der Vorabversion konfiguriert ist, gehen Sie zur Seite **Info** der AEM-Konsole und überprüfen Sie, ob die AEM Versionsnummer ein *Vorabversion*-Suffix wie ```Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE``` enthält.

![über](/help/release-notes/assets/about.png)
