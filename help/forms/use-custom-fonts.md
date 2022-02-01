---
title: 'Verwenden benutzerdefinierter Schriftarten '
description: 'Verwenden benutzerdefinierter Schriftarten '
source-git-commit: 94fe397d6ce08380ef08b65b47fe2c1aeb015ca3
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# Verwenden benutzerdefinierter Schriftarten

**Cloud Service Communications-Dokumentation ist in der Beta-Phase**

Sie können Forms as a Cloud Service Communications verwenden, um eine XDP-Vorlage, ein XDP-basiertes PDF-Dokument oder Acrobat Form (AcroForm) mit XML-Daten zu kombinieren, um PDF-Dokumente zu generieren. Sie können auch Communications verwenden, um PDF- und XDP-Dokumente zu kombinieren, neu anzuordnen und zu erweitern und Informationen über PDF-Dokumente zu erhalten.

Neben den bereits erwähnten Vorgängen können Sie Schriftarten, die in Cloud Service enthalten sind, oder benutzerdefinierte Schriftarten (vom Unternehmen genehmigte Schriftarten) verwenden, um die generierten PDF-Dokumente zu rendern. Sie können das Cloud Service-Entwicklungsprojekt verwenden, um benutzerdefinierte Schriftarten zu Ihrer Cloud Service-Umgebung hinzuzufügen.

## Verhalten von PDF-Dokumenten

Sie können [Schrift einbetten](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) zu einem PDF-Dokument. Wenn eine Schriftart eingebettet wird, wird das PDF-Dokument auf allen Plattformen identisch angezeigt (aussieht). Es verwendet eingebettete Schriftarten, um ein einheitliches Erscheinungsbild zu gewährleisten. Wenn eine Schriftart nicht eingebettet ist, hängt das Rendering der Schriftart von den Rendering-Einstellungen von PDF-Viewer-Clients wie Acrobat oder Acrobat Reader ab. Wenn die Schriftart auf dem Clientcomputer verfügbar ist, verwendet das PDF die angegebene Schriftart, andernfalls wird das PDF mit einer standardmäßigen Fallback-Schriftart gerendert.

## Hinzufügen benutzerdefinierter Schriftarten zu Ihrer as a Cloud Service Forms-Umgebung {#custom-fonts-cloud-service}

So fügen Sie benutzerdefinierte Schriftarten zu Ihrer Cloud Service-Umgebung hinzu:

1. Einrichten und Öffnen der [lokales Entwicklungsprojekt](setup-local-development-environment.md). Sie können eine beliebige IDE Ihrer Wahl verwenden.
1. Erstellen Sie auf der obersten Ebene der Ordnerstruktur des Projekts einen Ordner (Modul), um benutzerdefinierte Schriftarten zu speichern und benutzerdefinierte Schriftarten zum Ordner hinzuzufügen. Beispiel: fonts/src/main/resources
   ![Ordner &quot;Schriftarten&quot;](assets/fonts.png)

1. Öffnen Sie die Datei &quot;pom.xml&quot;des Schriftartenmoduls des Entwicklungsprojekts.
1. Fügen Sie der POM-Datei das JAR-Plug-in hinzu:

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   <addDefaultEntries/>
                   <addDefaultImplementationEntries/>
               </manifest>
           </archive>
       </configuration>
   </plugin>
   ```


1. Fügen Sie die `<Font-Archive-Version>` manifest geben Sie die .pom-Datei ein und legen Sie den Wert von Version auf 1 fest:

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   <addDefaultEntries/>
                   <addDefaultImplementationEntries/>
               </manifest>
               <manifestEntries>
                   <Font-Archive-Version>1</Font-Archive-Version>
                   <Font-Archive-Contents>/</Font-Archive-Contents>
               </manifestEntries> 
           </archive>
       </configuration>
   </plugin>
   ```

1. Ordner &quot;Schriftarten&quot;zu `<modules>` in der Pom-Datei aufgeführt. Beispiel:

   ```xml
   <modules>
       <module>all</module>
       <module>core</module>
       <module>ui.frontend</module>
       <module>ui.apps</module>
       <module>ui.apps.structure</module>
       <module>ui.config</module>
       <module>ui.content</module>
       <module>it.tests</module>
       <module>dispatcher</module>
       <module>dispatcher.ams</module>
       <module>dispatcher.cloud</module>
       <module>ui.tests</module>
       <module>fonts</module>
   </modules>
   ```

   Der Ordner &quot;Schriftarten&quot;enthält alle benutzerdefinierten Schriftarten.

1. Checken Sie den aktualisierten Code ein und [Pipeline ausführen](/help/implementing/cloud-manager/deploy-code.md) , um die Schriftarten in Ihrer Cloud Service-Umgebung bereitzustellen.

1. (Optional) Öffnen Sie die Eingabeaufforderung, navigieren Sie zum lokalen Projektordner und führen Sie den folgenden Befehl aus. Der Befehl packt die Schriftarten zusammen mit relevanten Informationen in eine JAR-Datei. Sie können die JAR-Datei verwenden, um benutzerdefinierte Schriftarten zu einer lokalen Entwicklungsumgebung für Forms-Cloud Service hinzuzufügen.

   ```shell
   mvn clean install
   ```

## Fügen Sie benutzerdefinierte Schriftarten zu Ihrer lokalen Forms Cloud Service-Entwicklungsumgebung hinzu. {#custom-fonts-cloud-service-sdk}

1. Starten Sie Ihre lokale Entwicklungsumgebung.
1. Navigieren Sie zu `<aem install directory>/crx-quickstart/install` Ordner.
1. Platzieren Sie die `<jar file contaning custom fonts and relevant deployment code>.jar` in den Installationsordner. Wenn Sie nicht über die JAR-Datei verfügen, führen Sie die Schritte aus, die unter [Hinzufügen benutzerdefinierter Schriftarten zu Ihrer as a Cloud Service Forms-Umgebung](#custom-fonts-cloud-service) -Abschnitt, um die Datei zu generieren.
1. Führen Sie die [docker-basierte SDK-Umgebung](setup-local-development-environment.md#docker-microservices)


   >[!NOTE]
   >
   >Wenn Sie eine aktualisierte Datei mit benutzerdefinierten Schriftarten .jar in einer lokalen Entwicklungsumgebung bereitstellen, starten Sie die docker-basierte SDK-Umgebung neu.