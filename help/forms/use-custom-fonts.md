---
title: 'Verwenden benutzerdefinierter Schriftarten '
description: 'Verwenden benutzerdefinierter Schriftarten '
source-git-commit: f435751c9c4da8aa90ad0c6705476466bde33afc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---


# Verwenden benutzerdefinierter Schriftarten

**Cloud Service Communications-Dokumentation ist in der Beta-Phase**

Sie können Forms as a Cloud Service Communications verwenden, um eine XDP-Vorlage, ein XDP-basiertes PDF-Dokument oder Acrobat Form (AcroForm) mit XML-Daten zu kombinieren, um PDF-Dokumente zu generieren. Sie können in Cloud Service enthaltene Schriftarten oder benutzerdefinierte Schriftarten (vom Unternehmen genehmigte Schriftarten) verwenden, um die generierten PDF-Dokumente zu rendern. Sie können das Cloud Service-Entwicklungsprojekt verwenden, um benutzerdefinierte Schriftarten zu Ihrer Cloud Service-Umgebung hinzuzufügen.

## Verhalten von PDF-Dokumenten

Sie können [Schrift einbetten](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) zu einem PDF-Dokument. Wenn eine Schriftart eingebettet wird, wird das PDF-Dokument auf allen Plattformen identisch angezeigt (sieht aus). Sie verwendete eingebettete Schriftart, um ein einheitliches Erscheinungsbild zu gewährleisten. Wenn eine Schriftart nicht eingebettet ist, hängt das Rendering der Schriftart von den Rendering-Einstellungen des PDF-Viewer-Clients ab. Wenn die Schriftart auf dem Clientcomputer verfügbar ist, verwendet das PDF die angegebene Schriftart, andernfalls wird das PDF mit einer Fallback-Schriftart gerendert.

## Hinzufügen benutzerdefinierter Schriftarten zu Ihrer as a Cloud Service Forms-Umgebung {#custom-fonts-cloud-service}

So fügen Sie benutzerdefinierte Schriftarten zu Ihrer Cloud Service-Umgebung hinzu:

1. Einrichten und Öffnen der [lokales Entwicklungsprojekt](setup-local-development-environment.md). Sie können eine beliebige IDE Ihrer Wahl verwenden.
1. Erstellen Sie in der Ordnerstruktur der obersten Ebene des Projekts einen Ordner, um benutzerdefinierte Schriftarten zu speichern und benutzerdefinierte Schriftarten zum Ordner hinzuzufügen. Beispiel: fonts/src/main/resources
   ![Ordner &quot;Schriftarten&quot;](assets/fonts.png)

1. Öffnen Sie die Datei &quot;pom.xml&quot;der obersten Ebene des Entwicklungsprojekts.
1. Hinzufügen `<Font-Archive-Version>` Manifesteintrag in die .pom-Datei und setzen Sie den Wert von Version auf 1:

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   </addDefaultEntries>
                   </addDefaultImplementationEntries>
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

1. Checken Sie den aktualisierten Code ein und [Pipeline ausführen](/help/implementing/cloud-manager/deploy-code.md) , um die Schriftarten in Ihrer Cloud Service-Umgebung bereitzustellen.

1. Öffnen Sie die Eingabeaufforderung, navigieren Sie zum lokalen Projektordner und führen Sie den folgenden Befehl aus. Sie erstellt ein Paket der Schriftarten in einer JAR-Datei. Sie können die JAR-Datei für die lokale Implementierung des Projekts verwenden.

```shell
mvn clean install
```

## Fügen Sie benutzerdefinierte Schriftarten zu Ihrer lokalen Forms Cloud Service-Entwicklungsumgebung hinzu. {#custom-fonts-cloud-service-sdk}

1. Starten Sie Ihre lokale Entwicklungsumgebung.
1. Navigieren Sie zu [crx-repository]\install folder
1. Platzieren Sie die JAR-Datei mit benutzerdefinierten Schriften und dem entsprechenden Bereitstellungscode im Installationsordner. Wenn Sie nicht über die JAR-Datei verfügen, führen Sie die Schritte aus, die unter [Hinzufügen benutzerdefinierter Schriftarten zu Ihrer as a Cloud Service Forms-Umgebung](#custom-fonts-cloud-service) -Abschnitt, um die Datei zu generieren.
1. Führen Sie die [docker-basierte SDK-Umgebung](setup-local-development-environment.md#docker-microservices)


   >[!NOTE]
   >
   >Wenn Sie eine aktualisierte JAR-Datei bereitstellen, um benutzerdefinierte Schriftarten zur lokalen Bereitstellungsumgebung hinzuzufügen oder daraus zu entfernen, stoppen und starten Sie die docker-basierte SDK-Umgebung.