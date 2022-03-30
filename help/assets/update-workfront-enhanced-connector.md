---
title: Aktualisieren [!DNL Workfront for Experience Manager enhanced connector]
description: Aktualisieren [!DNL Workfront for Experience Manager enhanced connector]
source-git-commit: 34f3cf925a3ea58de176521be459a61f4317eec3
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 5%

---

# Aktualisieren [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

[!UICONTROL Experience Manager Assets as a Cloud Service] ermöglicht es Ihnen, die [!DNL Workfront for Experience Manager enhanced connector] von einer vorherigen Version zur neuesten Version.

>[!TIP]
>
>Suchst du? [!DNL Workfront for Experience Manager enhanced connector] die Dokumentation für AEM 6.5 aktualisieren? Klicken [here](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=en##update-enhanced-connector-for-workfront).


So aktualisieren Sie die [!DNL Workfront for Experience Manager enhanced connector] auf die neueste Version:

1. Laden Sie die neueste Version des erweiterten Connectors von herunter. [Softwareverteilung von Adoben](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip).

1. [Zugriff](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) und klonen Sie Ihr AEM as a Cloud Service Repository aus Cloud Manager.

1. Öffnen Sie das as a Cloud Service Repository des geklonten Experience Managers mit einer IDE Ihrer Wahl.

1. Platzieren Sie die in Schritt 1 heruntergeladene ZIP-Datei des erweiterten Connectors im folgenden Pfad:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Wenn die Variable `resources` nicht vorhanden ist, erstellen Sie den Ordner .

1. Aktualisieren der verbesserten Connector-Version im übergeordneten Element `pom.xml`.

   ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version> updated enhanced connector version number</version>
         <scope>system</scope>
         <systemPath>${project.basedir}/ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
   ```

1. Aktualisieren Sie die Abhängigkeit in `all module pom.xml`.

   ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <scope>system</scope>
         <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
   ```

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie `<scope>` und `<systemPath>` auf die Abhängigkeiten in Schritt 5 und Schritt 6.

1. Aktualisieren `pom.xml` eingebettet. Fügen Sie die Pakete für den [!DNL Workfront for Experience Manager enhanced connector] in den Abschnitt `embeddeds` der `pom.xml` aller Ihrer Teilprojekte ein. Aktualisierungen in alle Module einbeziehen `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   Das Ziel des eingebetteten Abschnitts ist auf `/apps/<path-to-project-install-folder>/install`. Dieser JCR-Pfad `/apps/<path-to-project-install-folder>` muss in die Filterregeln im `all/src/main/content/META-INF/vault/filter.xml` -Datei. Die Filterregeln für das Repository werden normalerweise vom Programmnamen abgeleitet. Verwenden Sie den Namen des Ordners als Ziel in den vorhandenen Regeln.

1. [Entfernen der Abhängigkeiten von Hoodoo-Verteilungspunkten](remove-external-dependencies.md), falls vorhanden.

1. Übertragen Sie die Änderungen in das Repository.

1. Führen Sie die Pipeline aus, um [die Änderungen in Cloud Manager bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).
