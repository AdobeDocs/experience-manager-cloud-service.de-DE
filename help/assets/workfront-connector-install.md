---
title: Installieren [!DNL Workfront for Experience Manager enhanced connector]
description: Installieren [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: a5776453b261e6f4e6c891763934b236bade8f7f
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

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

1. Laden Sie den erweiterten Connector von herunter. [Softwareverteilung von Adoben](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

1. [Zugriff](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) und klonen Sie Ihr AEM as a Cloud Service Repository aus Cloud Manager.

1. Öffnen Sie das geklonte AEM as a Cloud Service Repository mithilfe einer IDE Ihrer Wahl.

1. Platzieren Sie die in Schritt 1 heruntergeladene ZIP-Datei des erweiterten Connectors im folgenden Pfad:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Wenn die Variable `resources` nicht vorhanden ist, erstellen Sie den Ordner .


1. Hinzufügen `pom.xml` dependencies:

   1. Hinzufügen einer Abhängigkeit im übergeordneten Element `pom.xml`.

      ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version>enhanced connector version number</version>
         <scope>system</scope>
         <systemPath>${project.basedir}/ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
      ```

      >[!NOTE]
      >
      >Stellen Sie sicher, dass die verbesserte Versionsnummer des Connectors aktualisiert wird, bevor Sie die Abhängigkeit in die übergeordnete `pom.xml`.

   1. Eine Abhängigkeit hinzufügen in `all module pom.xml`.

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
            <scope>system</scope>
            <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
         </dependency>
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

   Das Ziel des eingebetteten Abschnitts ist auf `/apps/<path-to-project-install-folder>/install`. Dieser JCR-Pfad `/apps/<path-to-project-install-folder>` muss in die Filterregeln im `all/src/main/content/META-INF/vault/filter.xml` -Datei. Die Filterregeln für das Repository werden normalerweise vom Programmnamen abgeleitet. Verwenden Sie den Namen des Ordners als Ziel in den vorhandenen Regeln.

1. Übertragen Sie die Änderungen in das Repository.

1. Führen Sie die Pipeline aus, um [die Änderungen in Cloud Manager bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

1. Erstellen Sie zum Erstellen einer Systembenutzerkonfiguration `wf-workfront-users` in [!DNL Experience Manager] Benutzergruppe und Berechtigung zuweisen `jcr:all` nach `/content/dam`. Ein Systembenutzer `workfront-tools` automatisch erstellt wird und die erforderlichen Berechtigungen automatisch verwaltet werden. Alle Benutzer von [!DNL Workfront] die den erweiterten Connector verwenden, werden automatisch als Teil dieser Gruppe hinzugefügt.

## Konfigurieren Sie die Verbindung zwischen [!DNL Experience Manager] as a [!DNL Cloud Service] und [!DNL Workfront] {#configure-connection}

So erstellen Sie eine Verbindung mit [!DNL Workfront]führen Sie die folgenden Schritte aus:

1. In [!DNL Experience Manager]auswählen **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront Tools]**.

1. Auswählen `workfront-tools` im linken Bereich und wählen Sie **[!UICONTROL Erstellen]** im rechten oberen Bereich der Seite.

1. Im **[!UICONTROL Workfront-Verbindung]** -Dialogfeld die erforderlichen Details für Ihre [!DNL Workfront] Bereitstellung und Auswahl **[!UICONTROL Verbindung zu Workfront herstellen]** -Option. Sobald die Verbindung erfolgreich hergestellt wurde, wird die [!DNL Workfront] Die benutzerdefinierte Dokumentenintegration wird automatisch im [!DNL Workfront] Umgebung.

   ![Verbinden [!DNL Experience Manager] und [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Navigieren Sie zum **[!UICONTROL Erweitert]** und wählen Sie die Option aus **[!UICONTROL Ist der Server AEM as a Cloud Service?]**.
