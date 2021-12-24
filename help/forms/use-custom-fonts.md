---
title: 'Verwenden benutzerdefinierter Schriftarten '
description: 'Verwenden benutzerdefinierter Schriftarten '
source-git-commit: 7dd3785206b6d79caa500a155d3a6f3597303e65
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Verwenden benutzerdefinierter Schriftarten

**Cloud Service Communications-Dokumentation ist in der Beta-Phase**

Sie können Forms as a Cloud Service Communications verwenden, um XDP-Vorlagen, XDP-basierte PDF-Dokumente oder Acrobat Forms (AcroForm) mit XML-Daten zu kombinieren, um PDF-Dokumente zu generieren. Sie können Systemschriftarten (Schriftarten, die in Cloud Service enthalten sind) oder benutzerdefinierte Schriftarten (vom Unternehmen genehmigte Schriftarten) verwenden, um die generierten PDF-Dokumente zu rendern.

Systemschriftarten sind bereits im Cloud Service verfügbar. Sie können das Cloud Service-Entwicklungsprojekt verwenden, um benutzerdefinierte Schriftarten zu Ihrer Cloud Service-Umgebung hinzuzufügen.

## Verhalten von PDF-Dokumenten

Sie können [Schrift einbetten](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) zu einem PDF-Dokument oder geben Sie einfach den Namen einer Schriftart an. Wenn eine Schriftart eingebettet wird, wird das PDF-Dokument auf allen Plattformen identisch angezeigt (sieht aus). Sie verwendete eingebettete Schriftart, um ein einheitliches Erscheinungsbild zu gewährleisten. Wenn keine Schrift eingebettet ist, sucht der PDF Rendering-Client auf dem Clientcomputer nach der Schrift. Wenn die Schriftart auf dem Clientcomputer verfügbar ist, verwendet das PDF die angegebene Schriftart, andernfalls wird das PDF mit einer Fallback-Schriftart gerendert.

## Hinzufügen benutzerdefinierter Schriftarten zu Ihrer as a Cloud Service Forms-Umgebung

So fügen Sie benutzerdefinierte Schriftarten zu Ihrer Cloud Service-Umgebung hinzu:

1. Richten Sie das lokale Entwicklungsprojekt ein und öffnen Sie es. Sie können eine beliebige IDE Ihrer Wahl verwenden.
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
