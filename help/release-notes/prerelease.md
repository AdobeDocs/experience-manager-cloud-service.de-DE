---
title: Vorabversionskanal für Adobe Experience Manager as a Cloud Service
description: Erfahren Sie, wie Sie über den Vorabversionskanal eine Vorschau bevorstehender Funktionen von AEM as a Cloud Service erhalten.
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
feature: Release Information
role: Admin
source-git-commit: 36da09746f02daad82875329b0aa53ee4eb7c074
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 58%

---


# Vorabversionskanal für Adobe Experience Manager as a Cloud Service {#prerelease-channel}

Erfahren Sie, wie Sie über den Vorabversionskanal eine Vorschau bevorstehender Funktionen von AEM as a Cloud Service erhalten.

## Einführung {#introduction}

Adobe Experience Manager as a Cloud Service bietet regelmäßig neue Funktionen. Die Liste neuer und bevorstehender Funktionen für eine bestimmte Funktionsversion wird in den [Versionshinweisen.](/help/release-notes/release-notes-cloud/release-notes-current.md)

Künftige Funktionen werden in der Regel auf eine von zwei Arten verfügbar gemacht:

* Im Rahmen eines Early-Adopter-Programms
* Im Rahmen des Vorabversionskanals

In diesem Dokument wird beschrieben, wie Sie den Vorabversionskanal aktivieren. Der Vorabversionskanal bietet Zugriff auf frühe Funktionen, die in einer zukünftigen Funktionsversion von AEM eingeführt werden. Dadurch haben Sie die Möglichkeit, neue Funktionen zu validieren und deren Einführung vor der zukünftigen Version zu planen. Weitere Informationen [ AEM-Veröffentlichungszeitplan finden Sie im Dokument ](/help/release-notes/home.md)Versionshinweise für Adobe Experience Manager (AEM) as a Cloud Service.

## Aktivieren des Vorabversionskanals für den Zugriff auf bevorstehende Funktionen {#enable-prerelease}

Der Vorabversionskanals kann in jeder beliebigen Entwicklungs- oder Sandbox-Umgebung aktiviert werden. Der Vorabversionskanal kann in Staging- oder Produktionsumgebungen nicht aktiviert werden.

Der Vorabversionskanal kann auf zwei verschiedene Arten aufgerufen werden:

* [Cloud-Umgebungen](#cloud-environments)
* [Lokales SDK](#local-sdk)

### Cloud-Umgebungen {#cloud-environments}

Um eine Cloud-Umgebung für die Verwendung des Vorabversionskanals zu aktualisieren, müssen Sie eine neue Umgebungsvariable hinzufügen. Dies ist entweder über die Cloud Manager-Benutzeroberfläche oder über die CLI möglich.

#### Hinzufügen der Umgebungsvariable über die Benutzeroberfläche {#add-with-ui}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Navigieren Sie zu dem Programm, in dem Sie den Vorabversionskanal aktivieren möchten.

1. Wählen Sie die Umgebung aus, in der Sie den Vorabversionskanal aktivieren möchten, und greifen Sie über **Programm** > **Umgebung** > **Umgebungskonfiguration** auf seine Konfiguration zu.

1. Fügen Sie eine neue [Umgebungsvariable](/help/implementing/cloud-manager/environment-variables.md) hinzu:

   | Name | Wert | Service angewendet | Typ |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | Alle | Variable |

1. Speichern Sie die Änderungen, und die Umgebung wird mit aktiviertem Vorabversionskanal aktualisiert.

   ![Neue Umgebungsvariable](assets/env-configuration-prerelease.png)

#### Hinzufügen der Umgebungsvariable mithilfe der CLI {#add-with-cli}

Sie können auch die Cloud Manager-API und -CLI verwenden, um die Umgebungsvariablen zu aktualisieren.

* Legen Sie mithilfe des [Umgebungsvariablen-Endpunkts der Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables) die Umgebungsvariable `AEM_RELEASE_CHANNEL` auf den Wert `prerelease` fest.

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

* [Die Cloud Manager-CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) kann auch verwendet werden.

  ```shell
  aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL "prerelease
  ```

Die Variable kann gelöscht werden, wenn Sie die Umgebung auf das Standardverhalten (nicht den Vorabversionskanal) zurücksetzen möchten.

### Lokales SDK {#local-sdk}

Sie können auf bevorstehende Funktionen im Vorabversionskanal in Ihrer lokalen Schnellstart-SDK zugreifen und Code für neue APIs erstellen, indem Sie Ihr Maven-Projekt so konfigurieren, dass es auf die Vorabversionskanal-`API Jar` in Maven Central verweist. Sie können auch auf den Vorabversionskanal in Ihrer lokalen Entwicklungsumgebung zugreifen, indem Sie die reguläre Schnellstart-SDK im Vorabversionsmodus starten.

#### Starten des Schnellstart-SDK im Vorabversionsmodus {#prerelease-mode}

1. Laden Sie die SDK von Software Distribution herunter und installieren Sie sie wie unter [Zugriff auf die AEM as a Cloud Service SDK&quot; beschrieben](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
1. Fügen Sie beim Starten des QuickStart-SDK das Argument `-r prerelease` hinzu.

Der Wert bleibt erhalten und kann deshalb nur beim ersten Starten ausgewählt werden. Installieren Sie das SDK neu, um die Befehlszeilenoption zu ändern.

Da es zwischen den monatlichen Funktionsveröffentlichungen mehrere AEM-Wartungsversionen geben kann, können Sie diese neuen SDKs herunterladen und in Maven-Projekten auf die neuen SDK-API-JAR-Versionen verweisen. Mit den Wartungsversionen werden keine zusätzlichen Vorabversionsfunktionen hinzugefügt. Sie könnten jedoch andere kleinere Änderungen wie Fehlerbehebungen, Sicherheitskorrekturen und Leistungsverbesserungen umfassen.
Javadocs werden in Maven Central veröffentlicht.

#### Erstellen von Code für das Vorabversions-SDK {#build-sdk}

1. Ändern Sie das `pom.xml` Ihres Maven-Projekts, um auf ein bestimmtes Vorabversions-SDK-API-JAR zu verweisen, das in Maven Central veröffentlicht wird. Es enthält alle neuen Java-APIs für die Vorabversionsfunktionen und ist von der SDK-API-JAR-Datei abhängig. Es verwendet dieselbe Version.

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

1. Die Bereitstellung erfolgt auf Ihrem lokalen Server.

1. Wenn Sie sich vergewissert haben, dass die Bereitstellung lokal wie erwartet erfolgt, übertragen Sie den Code auf einen Entwicklungszweig und verwenden Sie eine produktionsfremde Cloud Manager-Pipeline, um die Bereitstellung in einer [Umgebung mit aktiviertem Vorabversionskanal“ durchzuführen](#cloud-environments)

>[!CAUTION]
> 
> Die `aem-prerelease-sdk-api` artifactId darf nie bei der Bereitstellung in einer Staging- oder Produktionsumgebung verwendet werden. Verwenden Sie bei der Bereitstellung über die Produktions-Pipeline immer die `aem-sdk-api`. Ebenso sollte Code, der auf Vorabversions-APIs verweist, nicht über die Produktions-Pipeline bereitgestellt werden.

Das [Build Analyzer Maven-Plug-in der AEM CS-SDK der Version 1.0 und höher](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de#developing) erkennt, ob die Vorabversions-API in einem Projekt verwendet wird, indem es die Abhängigkeiten überprüft. Wenn der Analyzer sie findet, verwendet er die Vorabversions-SDK-API, um das Projekt zu analysieren.

## Zu beachten {#considerations}

Beim Verwenden des Vorabversionskanals sind einige Aspekte zu beachten.

* Der Vorabversionskanal enthält nicht unbedingt alle neuen Funktionen, die in der folgenden Version eingeführt werden sollen.
* Die Vorabversionsfunktionen durchlaufen eine strenge Kontrolle zur Qualitätssicherung und sind eher als vollständige Funktionen denn als Betaversionen konzipiert. Wenn Sie Probleme bemerken, melden Sie diese, genau wie Sie es tun würden, wenn Sie Fehler bei Funktionen in regulären AEM-Versionen vermuten.
* Um festzustellen, ob eine Umgebung für den Vorabversionskanal konfiguriert ist, wechseln Sie zur Seite &quot;**&quot; der AEM-Konsole** überprüfen Sie, ob die AEM-Versionsnummer ein `PRERELEASE` Suffix wie `Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE` enthält.

![Info](/help/release-notes/assets/about.png)
