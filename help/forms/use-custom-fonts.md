---
title: Verwenden benutzerdefinierter Schriftarten
description: Verwenden benutzerdefinierter Schriftarten
exl-id: 88214d36-fb97-4d46-a9fe-71dbc7826eb1
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: ht
source-wordcount: '456'
ht-degree: 100%

---

# Verwenden benutzerdefinierter Schriftarten

**Cloud Service Communications-Dokumentation befindet sich in der Beta-Phase**

Sie können Forms as a Cloud Service Communications verwenden, um eine XDP-Vorlage, ein XDP-basiertes PDF-Dokument oder Acrobat Form (AcroForm) mit XML-Daten zu kombinieren, um PDF-Dokumente zu generieren. Mit Communications können Sie PDF- und XDP-Dokumente kombinieren, neu anordnen und erweitern sowie Informationen zu PDF-Dokumenten abrufen.

Neben den bereits erwähnten Vorgängen können Sie die im Cloud Service enthaltenen Schriftarten oder benutzerdefinierte Schriftarten (vom Unternehmen genehmigte Schriftarten) verwenden, um die erzeugten PDF-Dokumente zu rendern. Sie können das Cloud Service-Entwicklungsprojekt verwenden, um benutzerdefinierte Schriftarten zu Ihrer Cloud Service-Umgebung hinzuzufügen.

## Verhalten von PDF-Dokumenten

Sie können in ein PDF-Dokument [Schriftarten einbetten](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions). Wenn eine Schriftart eingebettet wird, hat das PDF-Dokument auf allen Plattformen das identische Erscheinungsbild. Verwenden Sie eingebettete Schriftarten, um ein einheitliches Look-and-Feel zu gewährleisten. Wenn eine Schriftart nicht eingebettet ist, hängt das Rendering der Schriftart von den Rendering-Einstellungen der PDF-Viewer-Clients wie Acrobat oder Acrobat Reader ab. Wenn die Schriftart auf dem Client-Computer verfügbar ist, verwendet die PDF-Datei die angegebene Schriftart, andernfalls wird die PDF-Datei mit einer Fallback-Schriftart gerendert.

## Hinzufügen benutzerdefinierter Schriftarten zu Ihrer Forms as a Cloud Service-Umgebung {#custom-fonts-cloud-service}

So fügen Sie benutzerdefinierte Schriftarten zu Ihrer Cloud Service-Umgebung hinzu:

1. Richten Sie das [lokale Entwicklungsprojekt](setup-local-development-environment.md) ein und öffnen Sie es. Sie können eine beliebige IDE verwenden.
1. Erstellen Sie in der Ordnerstruktur der obersten Ebene des Projekts ein(en) Ordner(modul), um benutzerdefinierte Schriftarten zu speichern und zum Ordner hinzuzufügen. Beispiel: fonts/src/main/resources
   ![Schriftartenordner](assets/fonts.png)

1. Öffnen Sie die Datei „pom.xml“ des Schriftartenmoduls des Entwicklungsprojekts.
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


1. Fügen Sie den Manifesteintrag `<Font-Archive-Version>` in die .pom-Datei ein und setzen Sie den Wert der Version auf 1:

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

1. Fügen Sie den Schriftartenordner zu `<modules>` hinzu, das in der POM-Datei aufgeführt ist. Beispiel:

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

   Der Ordner „Schriftarten“ enthält alle benutzerdefinierten Schriftarten.

1. Checken Sie den aktualisierten Code ein und [führen Sie die Pipeline aus](/help/implementing/cloud-manager/deploy-code.md), um die Schriftarten in Ihrer Cloud Service-Umgebung bereitzustellen.

1. (Optional) Öffnen Sie die Eingabeaufforderung, gehen Sie zum lokalen Projektordner und führen Sie den folgenden Befehl aus. Der Befehl packt die Schriftarten zusammen mit relevanten Informationen in eine JAR-Datei. Sie können die JAR-Datei verwenden, um benutzerdefinierte Schriftarten zu einer lokalen Entwicklungsumgebung des Forms Cloud-Service hinzuzufügen.

   ```shell
   mvn clean install
   ```

## Hinzufügen benutzerdefinierter Schriftarten zu Ihrer Forms Cloud-Service-Entwicklungsumgebung {#custom-fonts-cloud-service-sdk}

1. Starten Sie Ihre lokalen Entwicklungsumgebung.
1. Gehen Sie zum Ordner `<aem install directory>/crx-quickstart/install`.
1. Platzieren Sie die `<jar file contaning custom fonts and relevant deployment code>.jar` in den Installationsordner. Wenn Sie nicht über die JAR-Datei verfügen, führen Sie die Schritte aus, die im Abschnitt [Hinzufügen benutzerdefinierter Schriftarten zu Ihrer Forms as a Cloud Service-Umgebung](#custom-fonts-cloud-service) aufgeführt sind, um die Datei zu erzeugen.
1. Ausführen der [Docker-basierten SDK-Umgebung](setup-local-development-environment.md#docker-microservices)


   >[!NOTE]
   >
   >Wenn Sie eine aktualisierte JAR-Datei mit benutzerdefinierten Schriftarten in einer lokalen Entwicklungsumgebung bereitstellen, starten Sie die Docker-basierte SDK-Umgebung neu.
