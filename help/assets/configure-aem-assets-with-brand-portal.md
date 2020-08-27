---
title: AEM Assets als Cloud Service mit dem Markenportal konfigurieren
description: Konfigurieren von AEM Assets mit Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: 830fd3a61d479a47b03cffc117f7192dd2c740cc
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 45%

---


# Configure AEM Assets as a Cloud Service with Brand Portal {#configure-aem-assets-with-brand-portal}

Durch die Konfiguration des Adobe Experience Manager Assets Brand Portal können Sie genehmigte Markenelemente aus Adobe Experience Manager Assets als Cloud Service-Instanz im Markenportal veröffentlichen und an die Markenportalbenutzer verteilen.

**Konfigurationsarbeitsablauf**

AEM Assets als Cloud Service wird über die Adobe Developer Console, die ein IMS-Token zur Autorisierung des Markenportals-Mandanten erhält, mit dem Markenportal konfiguriert. Es sind Konfigurationen sowohl in AEM Assets als auch in der Adobe Developer Console erforderlich.

1. Erstellen Sie in AEM Assets ein Konto für die Adobe Identity Management Services (IMS) und erstellen Sie einen öffentlichen Schlüssel (Zertifikat).
1. Erstellen Sie in der Adobe Developer Console ein Projekt für Ihren Brand Portal-Mandanten (Unternehmen).
1. Konfigurieren Sie unter dem Projekt eine API mit dem öffentlichen Schlüssel, um eine Dienstkontenverbindung zu erstellen.
1. Rufen Sie die Dienstkontoanmeldeinformationen und die JSON Web Token-(JWT-)Nutzlastinformationen ab.
1. Konfigurieren Sie in AEM Assets das IMS-Konto mit den Dienstkontoanmeldeinformationen und der JWT-Payload.
1. Konfigurieren Sie in AEM Assets den Markenportal-Cloud-Dienst mit dem IMS-Konto- und Markenportal-Endpunkt (Organisations-URL).
1. Testen Sie Ihre Konfiguration, indem Sie ein Asset aus AEM Assets in das Markenportal veröffentlichen.

>[!NOTE]
>
>Eine AEM Assets-Instanz darf nur mit einem Markenportal-Mieter konfiguriert werden.


## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes, um AEM Assets mit Brand Portal zu konfigurieren:

* Ein funktionsfähiges AEM Assets als Cloud Service-Instanz
* URL eines Pächter-Portals
* Ein Benutzer mit Systemadministrator-Berechtigungen für die IMS-Organisation des Markenportal-Mandanten

## Erstellen der Konfiguration {#create-new-configuration}

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um AEM Assets mit Markenportal zu konfigurieren.

1. [Abrufen eines öffentlichen Zertifikats](#public-certificate)
1. [Erstellen einer JWT-Verbindung (Dienstkonto)](#createnewintegration)
1. [Konfigurieren des IMS-Kontos](#create-ims-account-configuration)
1. [Konfigurieren von Cloud Service](#configure-the-cloud-service)
1. [Testen der Konfiguration](#test-configuration)

### Erstellen der IMS-Konfiguration {#create-ims-configuration}

Die IMS-Konfiguration authentifiziert Ihren Markenportal-Mieter mit AEM Assets.

Die IMS-Konfiguration umfasst zwei Schritte:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Konfigurieren des IMS-Kontos](#create-ims-account-configuration)

### Abrufen eines öffentlichen Zertifikats {#public-certificate}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in der Adobe Developer Console.

1. Melden Sie sich bei AEM Assets an.

1. Navigieren Sie im Bedienfeld **** Tools zu **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**.


1. Klicken Sie auf der Seite mit den Adobe IMS-Konfigurationen auf **[!UICONTROL Erstellen]**. It will redirect to the **[!UICONTROL Adobe IMS Technical Account Configuration]** page. Standardmäßig wird die Registerkarte **Zertifikat** geöffnet.

1. Wählen Sie die Cloud-Lösung **[!UICONTROL Adobe Brand Portal]** aus.

1. Aktivieren Sie das Kontrollkästchen Neues Zertifikat **** erstellen und geben Sie einen **Alias** für den öffentlichen Schlüssel an. Der Alias dient als Name des öffentlichen Schlüssels.

1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Then, click **[!UICONTROL OK]** to generate the public key.

   ![Zertifikat erstellen](assets/ims-config2.png)

1. Klicken Sie auf **[!UICONTROL Öffentlichen Schlüssel herunterladen]** und speichern Sie die Zertifikatdatei (.crt) auf Ihrem Computer.

   Die Zertifikatdatei wird später verwendet, um die API für Ihren Markenportal-Mandanten zu konfigurieren und Anmeldeinformationen für das Dienstkonto in der Adobe Developer Console zu generieren.

   ![Zertifikat herunterladen](assets/ims-config3.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Auf der Registerkarte &quot; **Konto** &quot;wird ein Adobe-IMS-Konto erstellt, für das die Anmeldeinformationen des Dienstkontos erforderlich sind, die in der Adobe Developer Console generiert werden. Lassen Sie diese Seite vorerst offen.

   Öffnen Sie eine neue Registerkarte und [erstellen Sie in der Adobe Developer Console eine JWT-Verbindung (Dienstkonto)](#createnewintegration), um die Anmeldedaten und die JWT-Payload für die Konfiguration des IMS-Kontos abzurufen.

### Erstellen einer JWT-Verbindung (Dienstkonto) {#createnewintegration}

In der Adobe Developer Console werden Projekte und APIs auf der Ebene des Markenportals-Mandanten (der Organisation) konfiguriert. Beim Konfigurieren einer API wird eine JWT-Verbindung (Service Account) erstellt. Es gibt zwei Methoden zum Konfigurieren der API: Generieren eines Schlüsselpaars (privater und öffentlicher Schlüssel) oder Hochladen eines öffentlichen Schlüssels. Um AEM Assets mit dem Markenportal zu konfigurieren, müssen Sie ein öffentliches Zertifikat (öffentlichen Schlüssel) in AEM Assets generieren und Anmeldeinformationen in der Adobe Developer Console erstellen, indem Sie den öffentlichen Schlüssel hochladen. Dieser öffentliche Schlüssel wird zum Konfigurieren der API für den ausgewählten Markenportal-Mandanten verwendet und generiert die Anmeldeinformationen und die JWT-Nutzlast für das Dienstkonto. Diese Anmeldeinformationen sind erforderlich, um das IMS-Konto in AEM Assets zu konfigurieren. Nachdem das IMS-Konto konfiguriert wurde, können Sie den Markenportal-Cloud-Dienst in AEM Assets konfigurieren.

Führen Sie die folgenden Schritte aus, um die Anmeldedaten für das Dienstkonto und die JWT-Payload zu generieren:

1. Melden Sie sich bei der Adobe Developer Console mit Systemadministratorrechten für die IMS-Organisation (den Brand Portal-Mandanten) an. Die Standardeinstellung ist [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie die richtige IMS-Organisation (Markenportal-Mieter) aus der Dropdown-Liste (Unternehmen) oben rechts ausgewählt haben.

1. Klicken Sie auf **[!UICONTROL Neues Projekt erstellen]**. Für Ihre Organisation wird ein leeres Projekt erstellt.

   Klicken Sie auf **[!UICONTROL Projekt bearbeiten]**, um den **[!UICONTROL Projekttitel]** und die **[!UICONTROL Projektbeschreibung]** zu aktualisieren, und klicken Sie auf **[!UICONTROL Speichern]**.

1. In the **[!UICONTROL Project overview]** tab, click **[!UICONTROL Add API]**.

1. In the **[!UICONTROL Add an API window]**, select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Next]**.

   Stellen Sie sicher, dass Sie Zugriff auf den AEM Brand Portal-Dienst haben.

1. In the **[!UICONTROL Configure API]** window, click **[!UICONTROL Upload your public key]**. Klicken Sie dann auf **[!UICONTROL Datei auswählen]** und laden Sie das öffentliche Zertifikat (.crt-Datei) hoch, das Sie im Abschnitt zum [Abrufen des öffentlichen Zertifikats](#public-certificate) heruntergeladen haben.

   Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Öffentlichen Schlüssel hochladen](assets/service-account3.png)

1. Überprüfen Sie das öffentliche Zertifikat und klicken Sie auf **[!UICONTROL Weiter]**.

1. Select the default product profile **[!UICONTROL Assets Brand Portal]** and click **[!UICONTROL Save configured API]**.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![Profil auswählen](assets/service-account4.png)

1. Nach der Konfiguration der API werden Sie zur Übersichtsseite der API weitergeleitet. Klicken Sie in der linken Navigation unter **[!UICONTROL Anmeldedaten]** auf **[!UICONTROL Dienstkonto (JWT)]**.

   >[!NOTE]
   >
   >Sie können die Anmeldeinformationen Ansicht und Aktionen wie das Generieren von JWT-Token, das Kopieren von Berechtigungsdetails, das Abrufen des Clientgeheimnisses usw. durchführen.

1. Kopieren Sie auf der Registerkarte **[!UICONTROL Client-Anmeldedaten]** die **[!UICONTROL Client-ID]**.

   Klicken Sie auf **[!UICONTROL Client-Geheimnis abrufen]** und kopieren Sie das **[!UICONTROL Client-Geheimnis]**.

   ![Dienstkonto-Anmeldedaten](assets/service-account5.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL JWT generieren]** und kopieren Sie die **[!UICONTROL JWT-Payload]**.

You can now use the client ID (API key), client secret, and JWT payload to [configure the IMS account](#create-ims-account-configuration) in AEM Assets.

<!--
1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create a new integration page opens. 
   
   Select your organization from the drop-down list.

   In **[!UICONTROL Experience Cloud]**, Select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Continue]**. 

   If the Brand Portal option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. If you do not know your organization, contact your administrator.

   ![Create Integration](assets/create-new-integration2.png)

1. Specify a name and description for the integration. Click **[!UICONTROL Select a File from your computer]** and upload the `AEM-Adobe-IMS.crt` file downloaded in the [obtain public certificates](#public-certificate) section.

1. Select the profile of your organization. 

   Or, select the default profile **[!UICONTROL Assets Brand Portal]** and click **[!UICONTROL Create Integration]**. The integration is created.

1. Click **[!UICONTROL Continue to integration details]** to view the integration information. 

   Copy the **[!UICONTROL API Key]** 
   
   Click **[!UICONTROL Retrieve Client Secret]** and copy the Client Secret key.

   ![API Key, Client Secret, and payload information of an integration](assets/create-new-integration3.png)

1. Navigate to **[!UICONTROL JWT]** tab, and copy the **[!UICONTROL JWT payload]**.

   The API Key, Client Secret key, and JWT payload information will be used to create IMS account configuration.

-->

### Konfigurieren des IMS-Kontos {#create-ims-account-configuration}

Stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Erstellen einer JWT-Verbindung (Dienstkonto)](#createnewintegration)

Führen Sie die folgenden Schritte aus, um das IMS-Konto zu konfigurieren.

1. Open the IMS Configuration and navigate to the **[!UICONTROL Account]** tab. You kept the page open while [obtaining the public certificate](#public-certificate).

1. Geben Sie einen **[!UICONTROL Titel]** für das IMS-Konto an.

   In the **[!UICONTROL Authorization Server]** field, specify the URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Specify client ID in the **[!UICONTROL API key]** field, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]** (JWT payload) that you have copied while [creating the service account (JWT) connection](#createnewintegration).

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Das IMS-Konto ist konfiguriert.

   ![IMS-Kontokonfiguration](assets/create-new-integration6.png)


1. Wählen Sie die IMS-Kontokonfiguration aus und klicken Sie auf **[!UICONTROL Systemdiagnose]**.

   Klicken Sie im Dialogfeld auf **[!UICONTROL Prüfen]**. Bei erfolgreicher Konfiguration wird eine Meldung angezeigt, dass das *Token erfolgreich abgerufen* wurde.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Sie dürfen nur eine IMS-Konfiguration haben.
>
>Vergewissern Sie sich, dass die IMS-Konfiguration die Konsistenzprüfung besteht. Wenn die Konfiguration die Konsistenzprüfung nicht besteht, ist sie ungültig. Sie müssen sie löschen und eine neue gültige Konfiguration erstellen.



### Konfigurieren von Cloud Service {#configure-the-cloud-service}

Führen Sie die folgenden Schritte aus, um den Brand Portal-Cloud Service zu konfigurieren:

1. Melden Sie sich bei AEM Assets an.

1. Navigieren Sie im **Tool** ![Tools](assets/tools.png)-Bedienfeld zu **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klicken Sie auf der Seite mit den Brand Portal-Konfigurationen auf **[!UICONTROL Erstellen]**.

1. Geben Sie einen **[!UICONTROL Titel]** für die Konfiguration ein.

   Select the IMS configuration that you created while [configuring the IMS account](#create-ims-account-configuration).

   In the **[!UICONTROL Service URL]** field, specify your Brand Portal tenant (organization) URL.

   ![](assets/create-cloud-service.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Konfiguration wird erstellt.

   Ihr AEM Assets als Cloud Service-Instanz ist jetzt mit dem Markenportal-Mandanten konfiguriert.

### Testen der Konfiguration {#test-configuration}

Führen Sie zur Validierung der Konfiguration folgende Schritte aus:

1. Melden Sie sich bei AEM Assets an.

1. Navigieren Sie im Bedienfeld **Tool**   zu **[!UICONTROL Bereitstellung]** > **[!UICONTROL Verteilung]**.

   ![](assets/test-bpconfig1.png)

   A Brand Portal distribution agent (**[!UICONTROL bpdistributionagent0]**) is created under **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Standardmäßig wird für einen Brand Portal-Mandanten ein Verteilungsagent erstellt.

1. Klicken Sie auf In Markenportal **[!UICONTROL veröffentlichen]** , um den Verteilungsagenten zu öffnen.

   Die Verteilungswarteschlangen finden Sie auf der Registerkarte &quot; **[!UICONTROL Status]** &quot;.

   Ein Verteilungsagent enthält zwei Warteschlangen:
   * **Verarbeitungswarteschlange (processing-queue)**: für die Verteilung von Assets an Brand Portal.

   * **Fehlerwarteschlange (error-queue)**: für die Assets, bei denen die Verteilung fehlgeschlagen ist.
   >[!NOTE]
   >
   >Es wird empfohlen, die Fehler zu überprüfen und die **Fehlerwarteschlange** regelmäßig zu löschen.

   ![](assets/test-bpconfig3.png)

1. Um die Verbindung zwischen AEM Assets als Cloud Service und Markenportal zu überprüfen, klicken Sie auf das Symbol **[!UICONTROL Verbindung]** testen.

   ![](assets/test-bpconfig4.png)

   A message appears at the bottom of the page that your *test package is successfully delivered*.

   >[!NOTE]
   >
   >Vermeiden Sie das Deaktivieren des Verteilungsagenten, da dies dazu führen kann, dass die Verteilung der Assets (in der Warteschlange) fehlschlägt.


Sie können jetzt:

* [Veröffentlichen von Assets aus AEM Assets in Brand Portal](publish-to-brand-portal.md)
* [Veröffentlichen von Ordnern aus AEM Assets in Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Veröffentlichen von Sammlungen aus AEM Assets in Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)

* [Veröffentlichen von Vorgaben, Schemata und Facetten in Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Veröffentlichen von Tags in Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


See [Brand Portal documentation](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/home.html) for more information.


## Verteilungsprotokolle {#distribution-logs}

Sie können die Verteilungsagenten-Protokolle für den Asset-Veröffentlichungs-Workflow überwachen.

Beispielsweise haben wir ein Asset aus AEM Assets in Brand Portal veröffentlicht, um die Konfiguration zu validieren.

1. Führen Sie die Schritte (1–4) aus, wie im Abschnitt [Konfiguration testen](#test-configuration) gezeigt, und navigieren Sie zur Seite des Verteilungsagenten.

1. Klicken Sie auf **[!UICONTROL Protokolle]** , um die Verarbeitungs- und Fehlerprotokolle Ansicht.

   ![](assets/test-bpconfig5.png)

Der Verteilungsagenten generiert die folgenden Protokolle:

* INFO: Dies ist ein vom System erstelltes Protokoll, das bei einer erfolgreichen Konfiguration des Distributionsagenten ausgelöst wird.
* DSTRQ1 (Anfrage 1): Wird bei der Testverbindung ausgelöst.

Beim Veröffentlichen des Assets werden die folgenden Anfrage- und Antwortprotokolle generiert:

**Anfrage des Verteilungsagenten**:
* DSTRQ2 (Anfrage 2): Die Anfrage zur Veröffentlichung des Assets wird ausgelöst.
* DSTRQ3 (Anforderung 3): Das System löst eine weitere Anforderung zum Veröffentlichen des AEM Assets-Ordners aus (in dem sich das Asset befindet) und repliziert den Ordner im Markenportal.

**Antwort des Verteilungsagenten**:
* queue-bpdistributionagent0 (DSTRQ2): Das Asset wird in Brand Portal veröffentlicht.
* queue-bpdistributionAgent0 (DSTRQ3): Das System repliziert den AEM Assets-Ordner (mit dem Asset) im Markenportal.

Im obigen Beispiel wird eine zusätzliche Anforderung und Antwort ausgelöst. Das System konnte den übergeordneten Ordner (Hinzufügen Pfad) im Markenportal nicht finden, da das Asset zum ersten Mal veröffentlicht wurde. Daher wurde eine zusätzliche Anforderung ausgelöst, einen übergeordneten Ordner mit demselben Namen im Markenportal zu erstellen, in dem das Asset veröffentlicht wird.

>[!NOTE]
>
>Zusätzliche Anforderungen werden generiert, wenn der übergeordnete Ordner nicht im Markenportal vorhanden ist oder in AEM Assets geändert wurde.



<!--

## Additional information {#additional-information}

Go to `/system/console/slingmetrics` for statistics related to the distributed content:

1. **Counter metrics**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Time metrics**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`

-->

<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
