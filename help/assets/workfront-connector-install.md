---
title: Installieren [!DNL Workfront for Experience Manager enhanced connector]
description: Installieren des  [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: 7ffac94eace3eaa276f0ad1705e0b32c886c795c
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 65%

---

# Installieren des [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

Ein Benutzer mit Administratorzugriff in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] installiert den erweiterten Connector. Überprüfen Sie vor der Installation die Plattformunterstützung und andere [Voraussetzungen für den Connector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Adobe fordert, dass die Bereitstellung und Konfiguration des [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services] durchgeführt wird. Wird diese ohne zertifizierten Partner oder [!DNL Adobe Professional Services] bereitgestellt oder konfiguriert, wird sie von Adobe nicht unterstützt.
>
>Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager], die diesen Connector redundant machen. In diesem Fall kann es erforderlich sein, dass Kunden diesen Connector nicht mehr verwenden.

Führen Sie vor der Installation des Connectors die folgenden Vorinstallationsschritte aus:

1. [Konfigurieren der Firewall](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html?lang=de). Für weitere Informationen zum IP-Cluster in [!DNL Workfront] navigieren Sie zu [!UICONTROL Einrichtung] > [!UICONTROL System] > [!UICONTROL Kundeninformationen].

1. Lassen Sie im Dispatcher HTTP-Kopfzeilen zu, die `authorization`, `username` und `apikey` heißen. Lassen Sie `GET`-, `POST`- und `PUT`-Anfragen an `/bin/workfront-tools` zu.

1. Stellen Sie sicher, dass die folgenden Pfade nicht im [!DNL Experience Manager]-Repository vorhanden sind:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Diese Installation erfordert Kenntnisse darüber, wie man ein Maven-Projekt in [!DNL Experience Manager] as a [!DNL Cloud Service] einrichtet. Verwenden Sie die folgenden Ressourcen, um zu verstehen, wie Sie ein Drittanbieter-Paket in Ihr Maven-Projekt einbeziehen:

   * [Einbeziehen eines Drittanbieterpakets in Ihr Maven-Projekt](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=de#including-third-party).
   * [Bereitstellen mit [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de).

Um das Add-on in [!DNL Experience Manager] as a [!DNL Cloud Service] zu installieren, gehen Sie wie folgt vor:

1. Laden Sie den erweiterten Connector von herunter. [Softwareverteilung von Adoben](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip).

1. [Zugriff](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) und klonen Sie Ihr AEM as a Cloud Service Repository aus Cloud Manager.

1. Öffnen Sie das geklonte AEM as a Cloud Service Repository mithilfe einer IDE Ihrer Wahl.

1. Platzieren Sie die in Schritt 1 heruntergeladene ZIP-Datei des erweiterten Connectors im folgenden Pfad:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Wenn die Variable `resources` nicht vorhanden ist, erstellen Sie den Ordner .


1. Hinzufügen von `pom.xml`-Abhängigkeiten:

   1. Fügen Sie in der übergeordneten `pom.xml` eine Abhängigkeit hinzu.

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


1. Fügen Sie `pom.xml`-Einbettungen hinzu. Fügen Sie die Pakete für den [!DNL Workfront for Experience Manager enhanced connector] in den Abschnitt `embeddeds` der `pom.xml` aller Ihrer Teilprojekte ein. Muss in die `pom.xml` aller Module eingebettet werden.

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

1. Um eine Systembenutzerkonfiguration zu erstellen, erstellen Sie `wf-workfront-users` in der [!DNL Experience Manager]-Benutzergruppe und weisen Sie die Berechtigung `jcr:all` an `/content/dam` zu. Ein `workfront-tools`-Systembenutzer wird automatisch erstellt und die erforderlichen Berechtigungen werden automatisch verwaltet. Alle Benutzer von [!DNL Workfront], die den erweiterten Connector verwenden, werden automatisch als Teil dieser Gruppe hinzugefügt.

Informationen zum Aktualisieren der [!DNL Workfront for Experience Manager enhanced connector] von einer vorherigen Version zur neuesten Version, klicken Sie auf [here](update-workfront-enhanced-connector.md).

## Konfigurieren der Verbindung zwischen [!DNL Experience Manager] as a [!DNL Cloud Service] und [!DNL Workfront] {#configure-connection}

Um eine Verbindung mit [!DNL Workfront] zu erstellen, führen Sie die folgenden Schritte aus:

1. Wählen Sie in [!DNL Experience Manager] die Option **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront-Tools]**.

1. Wählen Sie `workfront-tools` im linken Bedienfeld aus und wählen Sie **[!UICONTROL Erstellen]** oben rechts auf der Seite.

1. Tragen Sie im Dialogfeld **[!UICONTROL Workfront-Verbindung]** die erforderlichen Details für Ihre [!DNL Workfront]-Bereitstellung ein und wählen Sie die Option **[!UICONTROL Mit Workfront verbinden]**. Sobald die Verbindung erfolgreich hergestellt wurde, wird die benutzerdefinierte Dokumentenintegration von [!DNL Workfront] automatisch in der [!DNL Workfront]-Umgebung erstellt.

   ![Verbinden Sie [!DNL Experience Manager] und [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL Erweitert]** und wählen Sie die Option **[!UICONTROL Ist der Server AEM as a Cloud Service]** aus.
