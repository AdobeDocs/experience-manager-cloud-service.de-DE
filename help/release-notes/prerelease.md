---
title: '"[!DNL Adobe Experience Manager] as a Cloud Service-Kanal für Vorabversionen"'
description: '"[!DNL Adobe Experience Manager] as a Cloud Service-Kanal für Vorabversionen"'
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
source-git-commit: c2f0b9c904374b5e59ce2b2f268fdd73dfdbfd21
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 88%

---

# [!DNL Adobe Experience Manager] as a Cloud Service-Kanal für Vorabversionen {#prerelease-channel}


## Einführung {#introduction}

[!DNL Adobe Experience Manager] as a Cloud Service bietet monatlich neue Funktionen, entsprechend der [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de#aem-as-cloud-service). Um sich mit den Funktionen vertraut zu machen, deren Veröffentlichung für den folgenden Monat geplant ist, können Kunden den Kanal für Vorabversionen abonnieren, auf den über eine entsprechende Konfiguration in standardmäßigen Programmentwicklungsumgebungen oder in beliebigen Sandbox-Programmumgebungen zugegriffen werden kann. Kunden können eine Vorschau von Änderungen an der Sites-Konsole anzeigen sowie Code für alle neuen Vorabversions-APIs erstellen.

Die Liste der Vorabversionsfunktionen für einen bestimmten Monat wird in den [monatlichen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md) veröffentlicht.

>[!VIDEO](/help/release-notes/assets/prerelease-overview.mp4)

## Aktivieren von Vorabversionen {#enable-prerelease}

Die Vorabversionsfunktionen können in unterschiedlichen Bereichen genutzt werden:

* Cloud-Umgebungen (Standardmäßige Programmentwicklungsumgebungen oder jegliche Sandbox-Programmumgebungen)
* Lokales SDK

### Cloud-Umgebungen {#cloud-environments}

Um eine Cloud-Umgebung für die Verwendung der Vorabversion zu aktualisieren, fügen Sie eine neue [Umgebungsvariable](../implementing/cloud-manager/environment-variables.md) Verwenden der Umgebungskonfigurationsbenutzeroberfläche in Cloud Manager:

1. Navigieren Sie zum **Programm** > **Umgebung** > **Umgebungskonfiguration** Sie aktualisieren möchten.
1. Hinzufügen neuer [Umgebungsvariable](../implementing/cloud-manager/environment-variables.md):

   | Name | Wert | Service angewendet | Typ |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | Alle | Variable |

1. Speichern Sie die Änderungen und die Umgebung wird aktualisiert, sobald die Umschalter für die Vorabversion aktiviert sind.

   ![Neue Umgebungsvariable](assets/env-configuration-prerelease.png)


**Alternativ** Sie können die Cloud Manager-API und die CLI verwenden, um die Umgebungsvariablen zu aktualisieren:

* Verwendung [Umgebungsvariablen-Endpunkt der Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables), legen Sie die **AEM_RELEASE_CHANNEL** Umgebungsvariable zum Wert **Vorabversion**.

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

* Auch die Cloud Manager-CLI kann gemäß den Anweisungen unter [https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) verwendet werden.


   ```aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL “prerelease”```


Die Variable kann gelöscht oder auf einen anderen Wert zurückgesetzt werden, wenn Sie möchten, dass das Verhalten des regulären Kanals (nicht des Kanals für Vorabversionen) wiederhergestellt wird.

### Lokales SDK {#local-sdk}

Neue Funktionen werden in der Sites-Konsole im lokalen QuickStart-SDK angezeigt und in der Vorabversion können Sie Code für neue APIs verarbeiten, indem Sie Ihr Maven-Projekt auf das Vorabversions-`API Jar` in Maven Central verweisen. Sie können diese Vorabversionsfunktionen auch auf Ihrem lokalen Computer sehen, indem Sie das reguläre QuickStart-SDK im Vorabversionsmodus starten:

* Laden Sie das SDK vom Software Distribution-Portal herunter und installieren Sie es wie unter [Zugriff auf das AEM as a Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) beschrieben.
* Fügen Sie beim Starten des QuickStart-SDK das Argument `-r prerelease` hinzu.
* Der Wert ist *sticky*, sodass er nur beim ersten Starten ausgewählt werden kann. Installieren Sie das SDK neu, um die Befehlszeilenoption zu ändern.

Da es zwischen den monatlichen Funktionsveröffentlichungen mehrere AEM-Wartungsversionen geben kann, können Sie diese neuen SDKs herunterladen und in Maven-Projekten auf die neuen SDK-API-JAR-Versionen verweisen. Mit den Wartungsversionen werden keine zusätzlichen Vorabversionsfunktionen hinzugefügt. Sie könnten jedoch andere kleinere Änderungen wie Fehlerbehebungen, Sicherheitskorrekturen und Leistungsverbesserungen umfassen.
Javadocs werden in Maven Central veröffentlicht.

So erstellen Sie Code für das Vorabversions-SDK:

1. Ändern Sie die Datei „pom.xml“ Ihres Maven-Projekts, um auf ein bestimmtes Vorabversions-SDK-API-JAR zu verweisen, das in Maven Central veröffentlicht wird. Sie enthält jede neue Java-API für die Funktionen der Vorabversion und ist von der SDK-API-JAR-Datei abhängig. Sie verwendet dieselbe Version.

   Hier finden Sie beispielsweise ein Snippet aus dem Abschnitt zur Abhängigkeitsverwaltung des übergeordneten POM, das auf das reguläre API-JAR verweist:

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
1. Wenn Sie sich vergewissert haben, dass die Bereitstellung lokal wie erwartet erfolgt, übertragen Sie den Code in einen Entwicklungsverzweigung und verwenden Sie eine produktionsfremde Pipeline von Cloud Manager, um die Bereitstellung in einer Umgebung durchzuführen, die den Kanal für Vorabversionen abonniert hat.

>[!CAUTION]
> 
> Die artifactId `aem-prerelease-sdk-api` darf bei der Bereitstellung in der Staging- oder Produktionsumgebung nicht verwendet werden. Verwenden Sie bei der Bereitstellung über die Produktions-Pipeline immer die artifactId „aem-sdk-api“. Ebenso sollten Code, der auf Vorabversions-APIs verweist, nicht über die Produktions-Pipeline bereitgestellt werden.

Das [Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK der Version 1.0 und höher](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de#developing) erkennt, ob die Vorabversions-API in einem Projekt verwendet wird, indem es die Abhängigkeiten überprüft. Wenn Build Analyzer sie findet, verwendet er die Vorabversions-SDK-API, um das Projekt zu analysieren.

## Überlegungen {#considerations}

Bei Verwendung des Kanals für Vorabversionen sollten Sie einige Punkte beachten:

* Einige Funktionen, die mit der Version für den nächsten Monat eingeführt werden, sind möglicherweise nicht über den Kanal für Vorabversionen erhältlich.
* Die Vorabversionsfunktionen durchlaufen eine strenge Kontrolle zur Qualitätssicherung und sind eher als vollständige Funktionen denn als Betaversionen konzipiert. Wenn Sie Probleme bemerken, melden Sie diese, genau wie Sie es tun würden, wenn Sie Fehler bei Funktionen in regulären AEM-Versionen vermuten.
* Um festzustellen, ob eine Umgebung für den Kanal für Vorabversionen konfiguriert ist, wechseln Sie zur Seite **Info** der AEM-Konsole und überprüfen Sie, ob die AEM-Versionsnummer ein *prerelease*-Suffix wie ```Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE``` aufweist.

![Info](/help/release-notes/assets/about.png)
