---
title: Installieren [!DNL Workfront for Experience Manager enhanced connector]
description: Installieren [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
source-git-commit: 8ca25f86a8d0d61b40deaff0af85e56e438efbdc
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 2%

---


# Installieren [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

Ein Benutzer mit Administratorzugriff in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] installiert den erweiterten Connector. Überprüfen Sie vor der Installation den Plattformsupport und andere [Voraussetzungen für den Connector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Adobe erfordert Bereitstellung und Konfiguration der [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird ohne zertifizierten Partner bereitgestellt und konfiguriert oder [!DNL Adobe Professional Services], wird sie von Adobe nicht unterstützt.
>
>Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager] die diesen Connector redundant machen; In diesem Fall kann es erforderlich sein, dass Kunden von der Verwendung dieses Connectors übergehen.

Führen Sie vor der Installation des Connectors die folgenden Schritte vor der Installation aus:

1. [Konfigurieren der Firewall](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html). Informationen zum IP-Cluster in [!DNL Workfront], navigieren Sie zu [!UICONTROL Einrichtung] > [!UICONTROL System] > [!UICONTROL Kundeninformationen].

1. Lassen Sie im Dispatcher HTTP-Header zu, die `authorization`, `username`und `apikey`. Zulassen `GET`, `POST`und `PUT` Anforderungen an `/bin/workfront-tools`.

1. Stellen Sie sicher, dass die folgenden Pfade in [!DNL Experience Manager] repository:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Diese Installation erfordert das Wissen, ein Maven-Projekt in [!DNL Experience Manager] as a [!DNL Cloud Service]. Verwenden Sie die folgenden Ressourcen, um zu verstehen, wie Sie ein Drittanbieter-Paket in Ihr Maven-Projekt einbeziehen:

   * [Drittanbieterpaket in Ihr Maven-Projekt einschließen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#including-third-party).
   * [Bereitstellen mit [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de).

So installieren Sie das Add-on in [!DNL Experience Manager] as a [!DNL Cloud Service]führen Sie die folgenden Schritte aus:

1. Hinzufügen `pom.xml` dependencies:

   1. Hinzufügen einer Abhängigkeit im übergeordneten Element `pom.xml`.

      ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version>1.7.4</version>
      </dependency>
      ```

   1. Hinzufügen einer Abhängigkeit in allen Modulen [!DNL pom.xml].

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
         </dependency>
      ```

1. Hinzufügen `pom.xml` Authentifizierung.

   1. Fügen Sie die folgende Repository-Konfiguration in die pom.xml im adobe-public -Profil ein, damit die (oben) Connector-Abhängigkeiten zur Build-Zeit aufgelöst werden können (sowohl lokal als auch von Cloud Manager). Anmeldeinformationen für den Repository-Zugriff werden beim Erwerb einer Lizenz bereitgestellt. Die Anmeldeinformationen müssen der Datei settings.xml im Abschnitt &quot;Server&quot;hinzugefügt werden.

      ```XML
      <repository>
         <id>hoodoo-maven</id>
         <name>Hoodoo Repository</name>
         <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
      </repository>
      ```

   1. Erstellen Sie eine Datei mit dem Namen `./cloudmanager/maven/settings.xml` im Projektstamm. Informationen zur Unterstützung eines kennwortgeschützten Maven-Repositorys finden Sie unter [Einrichten des Projekts](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md). Zusätzlich wird ein Beispiel `settings.xml` -Datei als Referenz. Aktualisieren Sie abschließend Ihre lokale `settings.xml` lokal zu kompilieren.

      ```XML
         <server>
            <id>hoodoo-maven</id>
            <configuration>
               <httpHeaders>
                     <property>
                        <name>Deploy-Token</name>
                        <value>xxxxxxxxxxxxxxxx</value>
                     </property>
               </httpHeaders>
            </configuration>
         </server>
      ```

1. Hinzufügen `pom.xml` eingebettet. Fügen Sie die [!DNL Workfront for Experience Manager enhanced connector] Pakete in `embeddeds` Abschnitt `pom.xml` Ihres gesamten Unterprojekts. Benötigt sie im Modul &quot;all&quot;. `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

1. Erstellen Sie zum Erstellen einer Systembenutzerkonfiguration `wf-workfront-users` in [!DNL Experience Manager] Benutzergruppe und Berechtigung zuweisen `jcr:all` nach `/content/dam`. Ein Systembenutzer `workfront-tools` automatisch erstellt wird und die erforderlichen Berechtigungen automatisch verwaltet werden. Alle Benutzer von [!DNL Workfront] die den erweiterten Connector verwenden, werden automatisch als Teil dieser Gruppe hinzugefügt.

## Konfigurieren Sie die Verbindung zwischen [!DNL Experience Manager] as a [!DNL Cloud Service] und [!DNL Workfront] {#configure-connection}

So erstellen Sie eine Verbindung mit [!DNL Workfront]führen Sie die folgenden Schritte aus:

1. In [!DNL Experience Manager]auswählen **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront Tools]**.

1. Auswählen `workfront-tools` im linken Bereich und wählen Sie **[!UICONTROL Erstellen]** im rechten oberen Bereich der Seite.

1. Im **[!UICONTROL Workfront-Verbindung]** -Dialogfeld die erforderlichen Details für Ihre [!DNL Workfront] Bereitstellung und Auswahl **[!UICONTROL Verbindung zu Workfront herstellen]** -Option. Sobald die Verbindung erfolgreich hergestellt wurde, wird die [!DNL Workfront] Die benutzerdefinierte Dokumentenintegration wird automatisch im [!DNL Workfront] Umgebung.

   ![Verbinden [!DNL Experience Manager] und [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Navigieren Sie zum **[!UICONTROL Erweitert]** und wählen Sie die Option aus **[!UICONTROL Ist der Server AEM as a Cloud Service?]**.
