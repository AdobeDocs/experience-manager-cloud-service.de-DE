---
title: Adobe Experience Manager as a Cloud Service-Vorabversionskanal
description: Erfahren Sie, wie Sie mit dem Vorabversionskanal eine Vorschau bevorstehender Funktionen AEM as a Cloud Service erhalten.
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
source-git-commit: 5b38e7d0ad97cdf8b7d0d5da79cf3d6721fa618a
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 21%

---


# Adobe Experience Manager as a Cloud Service-Vorabversionskanal {#prerelease-channel}

Erfahren Sie, wie Sie mit dem Vorabversionskanal eine Vorschau bevorstehender Funktionen AEM as a Cloud Service erhalten.

## Einführung {#introduction}

Adobe Experience Manager as a Cloud Service stellt laut der Variablen [Experience Manager veröffentlicht Roadmap.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de#aem-as-cloud-service)

Um sich mit den für den folgenden Monat geplanten Funktionen vertraut zu machen, können Sie den Kanal für die Vorabversion abonnieren, auf den Sie durch die Konfiguration Ihrer Entwicklungsumgebungen oder beliebiger Sandbox-Umgebungen zugreifen können. Sie können eine Vorschau der über die AEM-Benutzeroberfläche zugänglichen Änderungen sowie den Build-Code für alle neuen Vorabversions-APIs anzeigen.

Die Liste der Vorabversionsfunktionen für einen bestimmten Monat wird im [monatliche Versionshinweise.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## AEM as a Cloud Service Versionen {#releases}

AEM as a Cloud Service hat zwei Arten von Versionen.

* **Monatliche Versionen** Hinzufügen von Funktionen und Funktionen zu AEM as a Cloud Service
* **Kritische Aktualisierungen** Sicherheitsaktualisierungen, Leistungsverbesserungen und Fehlerbehebungen hinzufügen und täglich angewendet werden.

Dadurch werden kontinuierliche Versionen ohne Unterbrechung des Service sichergestellt.

Der Kanal für die Vorabversion ermöglicht es Ihnen, eine Vorschau der für die bevorstehende monatliche Version geplanten Funktionen anzuzeigen, um die bevorstehende Funktion zu bewerten und die mögliche Implementierung für Ihre eigenen Projekte zu planen. Damit können Sie die nächste monatliche Version planen.

Wenn es beispielsweise Mai ist und Sie den Kanal für die Vorabversion abonniert haben, können Sie die Funktionen in der kommenden Version vom Juni bewerten.

![Grafik der Vorabversion](assets/prerelease-cadence.png)

Mit der Vorabversion erhalten Sie ein rollierendes einmonatiges Fenster zu den bevorstehenden AEMaaCS-Funktionen, in dem Sie die Auswirkungen neuer Funktionen auf Ihre Projekte und Anpassungen sowie geplante Rollouts für diese Funktionen, Tests und Benutzerschulungen einschätzen können.

Die effektive Nutzung des Vorversionskanals erfordert vier Schritte.

1. [Kalender markieren](#mark-calendars)
1. [Versionshinweise überprüfen](#release-notes)
1. [Neue Funktionen aufrufen und ausprobieren](#new-features)
1. [Trainieren von Benutzern](#train-users)

## Kalender markieren {#mark-calendars}

Die monatlichen Versionen sind weit im Voraus geplant und die Veröffentlichungstermine werden am [Adobe Experience League.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html#aem-as-cloud-service)

Notieren Sie sich die Veröffentlichungsdaten, damit Sie planen können, die bevorstehenden Funktionen zu überprüfen und zu testen.

## Versionshinweise überprüfen {#release-notes}

Sobald Sie die Veröffentlichungsdaten in Ihrem Kalender markiert haben, überprüfen Sie die [Adobe Experience League](/help/release-notes/release-notes-cloud/release-notes-current.md) Website am Tag der Veröffentlichung mit den neuesten Versionshinweisen.

Jede Version wird von Versionshinweisen begleitet, die nicht nur die neuen Funktionen in dieser Version dokumentieren, sondern auch die Funktionen, die für die Vorabauswertung verfügbar sind. Machen Sie sich mit den neuesten Funktionen von AEMaaCS vertraut und planen Sie, die neuesten Funktionen zu nutzen!

Sie können auch [bekannte Probleme überprüfen](/help/release-notes/known-issues.md) die zusammen mit jeder Version veröffentlicht werden, damit Sie auch über alle technischen Probleme informiert sein können, die eine Herausforderung für Ihre Bewertung oder die Übernahme neuer Funktionen darstellen können.

## Aktivieren Sie den Kanal &quot;Vorabversion&quot;, um auf neue Funktionen zuzugreifen und sie auszuprobieren. {#new-features}

Der Kanal für die Vorabversion kann in jeder Entwicklungs- oder Sandbox-Umgebung aktiviert werden. Die Vorabversion kann in Staging- oder Produktionsumgebungen nicht aktiviert werden.

Die Vorabversionsfunktionen können in unterschiedlichen Bereichen genutzt werden:

* [Cloud-Umgebungen](#cloud-environments)
* [Lokales SDK](#local-sdk)

### Cloud-Umgebungen {#cloud-environments}

Um eine Cloud-Umgebung zu aktualisieren und die Vorabversion zu verwenden, müssen Sie eine neue Umgebungsvariable hinzufügen. Dies ist entweder über die Cloud Manager-Benutzeroberfläche oder über die CLI möglich.

#### Umgebungsvariable mithilfe der Benutzeroberfläche hinzufügen {#add-with-ui}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Navigieren Sie zu dem Programm, für das Sie die Vorabversion aktivieren möchten.

1. Wählen Sie die Umgebung aus, in der Sie die Vorabversion aktivieren möchten, und greifen Sie über auf ihre Konfiguration zu **Programm** > **Umgebung** > **Umgebungskonfiguration**.

1. Hinzufügen neuer [Umgebungsvariable:](../implementing/cloud-manager/environment-variables.md)

   | Name | Wert | Service angewendet | Typ |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | Alle | Variable |

1. Speichern Sie die Änderungen und die Umgebung wird aktualisiert, wenn die Umschalter für die Vorabversion aktiviert sind.

   ![Neue Umgebungsvariable](assets/env-configuration-prerelease.png)

#### Umgebungsvariable mithilfe der CLI hinzufügen {#add-with-cli}

Sie können auch die Cloud Manager-API und die CLI verwenden, um die Umgebungsvariablen zu aktualisieren.

* Verwenden [Umgebungsvariablen-Endpunkt der Cloud Manager-API,](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables) legen Sie die `AEM_RELEASE_CHANNEL` Umgebungsvariable zum Wert `prerelease`.

   ```text
   PATCH /program/{programId}/environment/{environmentId}/variables
   [
           {
                   "name" : "AEM_RELEASE_CHANNEL",
                   "value" : "prerelease",
                   "type" : "string"
           }
   ]
   ```

* [Die Cloud Manager-CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) kann auch verwendet werden

   ```shell
   aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL “prerelease
   ```

Die Variable kann gelöscht oder auf einen anderen Wert zurückgesetzt werden, wenn Sie möchten, dass das Verhalten des regulären Kanals (nicht des Kanals für Vorabversionen) wiederhergestellt wird.

### Lokales SDK {#local-sdk}

Sie können neue Funktionen in der Sites-Konsole im lokalen Schnellstart-SDK sehen und in der Vorabversion Code gegen neue APIs anzeigen, indem Sie Ihr Maven-Projekt so konfigurieren, dass es auf die Vorabversion verweist `API Jar` befindet sich in Maven Central. Sie können diese Vorabversionsfunktionen auch in Ihrer lokalen Entwicklungsumgebung sehen, indem Sie das reguläre Schnellstart-SDK im Vorabversionsmodus starten.

#### Starten des Schnellstart-SDK im Vorversionsmodus {#prerelease-mode}

1. Laden Sie das SDK aus dem Software Distribution-Portal herunter und installieren Sie es wie unter [Zugriff auf das AEM as a Cloud Service SDK.](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
1. Fügen Sie beim Starten des QuickStart-SDK das Argument `-r prerelease` hinzu.

Der Wert ist sticky, sodass er nur beim ersten Starten ausgewählt werden kann. Installieren Sie das SDK neu, um die Befehlszeilenoption zu ändern.

Da es zwischen den monatlichen Funktionsveröffentlichungen mehrere AEM-Wartungsversionen geben kann, können Sie diese neuen SDKs herunterladen und in Maven-Projekten auf die neuen SDK-API-JAR-Versionen verweisen. Mit den Wartungsversionen werden keine zusätzlichen Vorabversionsfunktionen hinzugefügt. Sie könnten jedoch andere kleinere Änderungen wie Fehlerbehebungen, Sicherheitskorrekturen und Leistungsverbesserungen umfassen.
Javadocs werden in Maven Central veröffentlicht.

#### Build anhand des Vorabversions-SDK {#build-sdk}

1. Ändern der `pom.xml` , um auf eine eigene Vorabversion-SDK-API-JAR zu verweisen, die in Maven Central veröffentlicht wird. Es enthält jede neue Java-API für die Vorabversionsfunktionen und ist von der SDK-API-JAR-Datei abhängig. Sie verwendet dieselbe Version.

   Hier finden Sie beispielsweise einen Ausschnitt aus dem Abschnitt zur Abhängigkeitsverwaltung des übergeordneten Poms, der auf die reguläre API-JAR verweist:

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

1. Bereitstellen auf Ihrem lokalen Server.

1. Wenn Sie sich vergewissert haben, dass sie lokal wie erwartet funktioniert, übertragen Sie den Code in eine Entwicklungsverzweigung und verwenden Sie eine Cloud Manager-Nicht-Produktions-Pipeline, um sie in einer Umgebung bereitzustellen, die den Vorabversionskanal abonniert.

>[!CAUTION]
> 
> Die `aem-prerelease-sdk-api` artifactId darf nie bei der Bereitstellung in der Staging- oder Produktionsumgebung verwendet werden. Verwenden Sie immer `aem-sdk-api` bei der Bereitstellung über die Produktions-Pipeline. Ebenso sollte Code, der auf Vorabversions-APIs verweist, nicht über die Produktions-Pipeline bereitgestellt werden.

Die [AEM CS SDK Build Analyzer-Maven-Plug-in Version 1.0 und höher](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html#developing) erkennt, ob die Vorabversion-API in einem Projekt verwendet wird, indem die Abhängigkeiten überprüft werden. Wenn der Analyzer es findet, verwendet er die Vorabversion-SDK-API, um das Projekt zu analysieren.

## Trainieren Ihrer Benutzer {#train-users}

Nachdem Sie die neuen Funktionen im Vorversionskanal getestet und entschieden haben, sie in Ihren Projekten zu nutzen, müssen Sie Ihre Benutzer trainieren.

Adobe Experience League bietet viele Ressourcen zum Kennenlernen von AEMaaCS.

* [Die AEMaaCS-Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de)
* [Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-tutorials/overview.html)
* [Video zur monatlichen Versionsübersicht](/help/release-notes/release-notes-cloud/release-notes-current.md#release-video) in den Versionshinweisen

## Zu beachten {#considerations}

Beim Verwenden des Vorabversionskanals sind einige Elemente zu beachten.

* Der Kanal für die Vorabversion enthält nicht unbedingt alle neuen Funktionen, die in der folgenden Version eingeführt werden sollen.
* Die Vorabversionsfunktionen durchlaufen eine strenge Kontrolle zur Qualitätssicherung und sind eher als vollständige Funktionen denn als Betaversionen konzipiert. Wenn Sie Probleme bemerken, melden Sie diese, genau wie Sie es tun würden, wenn Sie Fehler bei Funktionen in regulären AEM-Versionen vermuten.
* Um festzustellen, ob eine Umgebung für den Kanal der Vorabversion konfiguriert ist, gehen Sie zur AEM **Info** und überprüfen Sie, ob die AEM Versionsnummer eine *Vorabversion* Suffix wie ```Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE```.

![Info](/help/release-notes/assets/about.png)
