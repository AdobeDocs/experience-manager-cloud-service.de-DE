---
title: Installieren des  [!DNL Workfront for Experience Manager enhanced connector]
description: Installieren des  [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Workfront Integrations and Apps
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '764'
ht-degree: 100%

---

# Installieren des [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Ein Benutzer mit Administratorzugriff in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] installiert den erweiterten Connector. Überprüfen Sie vor der Installation die Plattformunterstützung und andere [Voraussetzungen für den Connector](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Seit Juni 2022 bietet Adobe eine neue native Integration für die Verbindung von Workfront mit Adobe Experience Manager Assets as a Cloud Service. Diese Integration ist zu einer erforderlichen Methode geworden, um diese beiden Lösungen miteinander zu verbinden. Jede künftige neue Implementierung des erweiterten Connectors (1.9.8 und höher) zur Verbindung von Workfront mit AEM Assets as a Cloud Service wird blockiert. Weitere Informationen zum Einrichten dieser Integration finden Sie unter [Konfigurieren der Integration von Experience Manager Assets as a Cloud Service](workfront-connector-configure.md).

>[!IMPORTANT]
>
>* Adobe erfordert die Bereitstellung und Konfiguration des [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird diese ohne zertifizierten Partner oder [!DNL Adobe Professional Services] bereitgestellt oder konfiguriert, wird sie von Adobe nicht unterstützt.
>
>* Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager], die diesen Connector redundant machen. In diesem Fall kann es erforderlich sein, dass Kunden diesen Connector nicht mehr verwenden.
>
>* Adobe unterstützt die Versionen 1.7.4 und höher des erweiterten Connectors. Frühere Vorabversionen und benutzerdefinierte Versionen werden nicht unterstützt. Informationen zum Überprüfen der erweiterten Connector-Version finden Sie in Schritt 5(a) der [Installationsanweisungen für den erweiterten Connector](workfront-connector-install.md).
>
>* Siehe [Partnerzertifizierungsprüfung für den erweiterten Connector von Workfront for Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Informationen zur Prüfung finden Sie im [Prüfungshandbuch](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

Führen Sie vor der Installation des Connectors die folgenden Vorinstallationsschritte aus:

1. Wenn für Ihr AEM as a Cloud Service-Programm erweiterte Netzwerkfunktionen konfiguriert sind und die IP-Zulassungsauflistung aktiviert ist, müssen Sie die Workfront-IPs dieser Zulassungsliste hinzufügen, damit Ereignisabonnements und verschiedene API-Aufrufe an AEM weitergeleitet werden können.

   * [Workfront Cluster-IPs](https://experienceleague.adobe.com/docs/workfront/using/administration-and-setup/get-started-administration/configure-your-firewall.html?lang=de#ip-addresses-to-allow-for-clusters-1-2-3-5-7-8-and-9). Für Details zum IP-Cluster in [!DNL Workfront] navigieren Sie zu **[!UICONTROL Einrichtung]** > **[!UICONTROL System]** > **[!UICONTROL Kundeninformationen]**.

   * [Workfront Ereignisabonnement-API-IPs](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-api/event-subscriptions/event-subs-api.html?lang=de)

   >[!IMPORTANT]
   >
   >* Wenn Sie für Ihr Programm erweiterte Netzwerkfunktionen konfiguriert haben und die IP-Zulassungsauflistung verwenden, müssen Sie aufgrund einer Beschränkung mit der erweiterten Workfront Connector-Architektur auch die Ausgangs-IP des Programms zur Zulassungsliste in Cloud Manager hinzufügen.
   >
   >* p{PROGRAM_ID}.external.adobeaemcloud.com
   >
   >* Um die IP-Adresse Ihres Programms zu finden, öffnen Sie ein Terminal-Fenster und führen Sie einen Befehl aus wie z. B.:
   >
   >    ```
   >    dscacheutil -q host -a name p{PROGRAM_ID}.external.adobeaemcloud.com
   >
   >    ```

1. Stellen Sie sicher, dass die folgenden Überlagerungen nicht im [!DNL Experience Manager]-Repository vorhanden sind. Wenn Sie bereits vorhandene Überlagerungen auf diesen Pfaden haben, müssen Sie entweder die Überlagerungen entfernen oder das Delta der Änderungen zwischen den beiden Pfaden zusammenführen:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`
   * `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`

1. Diese Installation erfordert Kenntnisse darüber, wie man ein Maven-Projekt in [!DNL Experience Manager] as a [!DNL Cloud Service] einrichtet. Verwenden Sie die folgenden Ressourcen, um zu verstehen, wie Sie ein Drittanbieter-Paket in Ihr Maven-Projekt einbeziehen:

   * [Einbeziehen eines Drittanbieterpakets in Ihr Maven-Projekt](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=de#including-third-party).
   * [Bereitstellen mit [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de).

Um das Add-on in [!DNL Experience Manager] as a [!DNL Cloud Service] zu installieren, gehen Sie wie folgt vor:

1. Laden Sie den erweiterten Connector von [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip) herunter.

1. [Greifen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=de) Sie auf Ihr AEM as a Cloud Service-Repository über Cloud Manager zu und klonen Sie es.

1. Öffnen Sie das geklonte AEM as a Cloud Service-Repository mithilfe einer IDE Ihrer Wahl.

1. Platzieren Sie die in Schritt 1 heruntergeladene ZIP-Datei des erweiterten Connectors im folgenden Pfad:

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Wenn der Ordner `resources` nicht vorhanden ist, erstellen Sie ihn.


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
      >Stellen Sie sicher, dass Sie die Versionsnummer des erweiterten Connectors aktualisieren, bevor Sie die Abhängigkeit in das übergeordnete `pom.xml` kopieren.

   1. Fügen Sie in `all module pom.xml` eine Abhänigigkeit hinzu.

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
            <scope>system</scope>
            <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
         </dependency>
      ```


1. Fügen Sie `pom.xml`-Einbettungen hinzu. Fügen Sie die [!DNL Workfront for Experience Manager enhanced connector]-Pakete in den Abschnitt `embeddeds` der `pom.xml` aller Ihrer Teilprojekte ein. Muss in die `pom.xml` aller Module eingebettet werden.

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

1. Übertragen Sie die Änderungen in das Repository.

1. Führen Sie die Pipeline aus, um [die Änderungen in Cloud Manager bereitzustellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de).

1. Um eine Systembenutzerkonfiguration zu erstellen, erstellen Sie `wf-workfront-users` in der [!DNL Experience Manager]-Benutzergruppe und weisen Sie die Berechtigung `jcr:all` an `/content/dam` zu. Ein `workfront-tools`-Systembenutzer wird automatisch erstellt und die erforderlichen Berechtigungen werden automatisch verwaltet. Alle Benutzer von [!DNL Workfront], die den erweiterten Connector verwenden, werden automatisch als Teil dieser Gruppe hinzugefügt.

Klicken Sie [hier](update-workfront-enhanced-connector.md), um Informationen zur Aktualisierung des [!DNL Workfront for Experience Manager enhanced connector] von einer früheren Version auf die neueste Version zu erhalten.

## Konfigurieren der Verbindung zwischen [!DNL Experience Manager] as a [!DNL Cloud Service] und [!DNL Workfront] {#configure-connection}

Um eine Verbindung mit [!DNL Workfront] zu erstellen, führen Sie die folgenden Schritte aus:

1. Wählen Sie in [!DNL Experience Manager] die Option **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront-Tools]**.

1. Wählen Sie `workfront-tools` im linken Bedienfeld aus und wählen Sie **[!UICONTROL Erstellen]** oben rechts auf der Seite.

1. Tragen Sie im Dialogfeld **[!UICONTROL Workfront-Verbindung]** die erforderlichen Details für Ihre [!DNL Workfront]-Bereitstellung ein und wählen Sie die Option **[!UICONTROL Mit Workfront verbinden]**. Sobald die Verbindung erfolgreich hergestellt wurde, wird die benutzerdefinierte Dokumentenintegration von [!DNL Workfront] automatisch in der [!DNL Workfront]-Umgebung erstellt.

   ![Verbinden Sie [!DNL Experience Manager] und [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL Erweitert]** und wählen Sie die Option **[!UICONTROL Ist der Server AEM as a Cloud Service]** aus.
