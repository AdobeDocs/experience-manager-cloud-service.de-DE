---
title: Aktualisieren von  [!DNL Workfront for Experience Manager enhanced connector]
description: Aktualisieren von  [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 09276b4d-a7c8-4927-8c0a-40eda48e55a7
feature: Workfront Integrations and Apps
role: Admin
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 100%

---

# Aktualisieren von [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

[!UICONTROL Experience Manager Assets as a Cloud Service] ermöglicht es Ihnen, [!DNL Workfront for Experience Manager enhanced connector] von einer vorherigen Version auf die neueste Version zu aktualisieren.

>[!TIP]
>
>Suchen Sie nach der Dokumentation für die Aktualisierung von [!DNL Workfront for Experience Manager enhanced connector] für AEM 6.5? Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=de##update-enhanced-connector-for-workfront).


So aktualisieren Sie [!DNL Workfront for Experience Manager enhanced connector] auf die neueste Version:

1. Laden Sie die neueste Version des erweiterten Connectors von [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip) herunter.

1. [Greifen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=de) Sie auf Ihr AEM as a Cloud Service-Repository über Cloud Manager zu und klonen Sie es.

1. Öffnen Sie das geklonte Experience Manager as a Cloud Service-Repository mit einer IDE Ihrer Wahl.

1. Platzieren Sie die in Schritt 1 heruntergeladene ZIP-Datei des erweiterten Connectors im folgenden Pfad:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Wenn der Ordner `resources` nicht vorhanden ist, erstellen Sie ihn.

1. Aktualisieren Sie die Version des erweiterten Connectors in der übergeordneten `pom.xml`-Datei.

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
   >Stellen Sie sicher, dass Sie `<scope>` und `<systemPath>` zu den Abhängigkeiten in Schritt 5 und Schritt 6 hinzufügen.

1. Aktualisieren Sie eingebettete `pom.xml`-Dateien. Fügen Sie die [!DNL Workfront for Experience Manager enhanced connector]-Pakete in den Abschnitt `embeddeds` der `pom.xml` aller Ihrer Teilprojekte ein. Nehmen Sie die Aktualisierungen in alle `pom.xml`-Module auf.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   Das Ziel des eingebetteten Abschnitts ist auf `/apps/<path-to-project-install-folder>/install` festgelegt. Dieser JCR-Pfad `/apps/<path-to-project-install-folder>` muss in den Filterregeln in der Datei `all/src/main/content/META-INF/vault/filter.xml` enthalten sein. Die Filterregeln für das Repository werden normalerweise vom Programmnamen abgeleitet. Verwenden Sie den Namen des Ordners als Ziel in den vorhandenen Regeln.

1. [Entfernen der Abhängigkeiten von Hoodoo-Verteilungspunkten](remove-external-dependencies.md), falls vorhanden.

1. Übertragen Sie die Änderungen in das Repository.

1. Führen Sie die Pipeline aus, um [die Änderungen in Cloud Manager bereitzustellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de).
