---
title: AEM Assets-Cloud-Dienst mit Markenportal konfigurieren
description: AEM Assets-Cloud-Dienst mit Markenportal konfigurieren
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: 8dc3270b355e9e855179f6b41602a3c28202a5b7

---


# Konfigurieren von AEM Assets mit Brand Portal {#configure-aem-assets-with-brand-portal}

Adobe Experience Manager (AEM) Assets wird über Adobe I/O in Brand Portal konfiguriert. Dadurch wird ein IMS-Token zur Autorisierung Ihres Brand Portal-Mandanten abgerufen.

## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes, um AEM Assets mit Brand Portal zu konfigurieren:

* Eine AEM Assets-Cloud-Instanz, die läuft.
* Brand Portal-Mandanten-URL
* Ein Benutzer mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten

**Weitere Abfragen erhalten Sie vom Support** .

## Konfiguration erstellen {#create-new-configuration}

Sie können eine neue Konfiguration auf Adobe I/O erstellen, um Ihre AEM Assets-Cloud-Instanz mit Brand Portal zu konfigurieren.

Führen Sie die folgenden Schritte in der aufgeführten Reihenfolge durch:
1. [Erhalten eines öffentlichen Zertifikats](#public-certificate)
1. [Adobe I/O-Integration erstellen](#createnewintegration)
1. [Konfiguration des IMS-Kontos erstellen](#create-ims-account-configuration)
1. [Cloud-Dienst konfigurieren](#configure-the-cloud-service)
1. [Testkonfiguration](#test-configuration)

### IMS-Konfiguration erstellen {#create-ims-configuration}

Die IMS-Konfiguration authentifiziert Ihren Markenportal-Mandanten mit der Autoreninstanz von AEM Assets.

Die IMS-Konfiguration umfasst zwei Schritte:

* [Erhalten eines öffentlichen Zertifikats](#public-certificate)
* [Konfiguration des IMS-Kontos erstellen](#create-ims-account-configuration)

### Erhalten eines öffentlichen Zertifikats {#public-certificate}

Mit dem öffentlichen Zertifikat können Sie Ihr Profil auf Adobe I/O authentifizieren.

1. Anmelden bei Ihrer AEM Assets-Cloud-Instanz

1. Navigieren Sie im **Tool** ![Tools](assets/tools.png) -Bedienfeld zu **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**.

   ![Benutzeroberfläche der Adobe IMS-Kontokonfiguration](assets/ims-configuration1.png)

1. Die Seite &quot;Adobe IMS-Konfigurationen&quot;wird geöffnet.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Auf diese Weise gelangen Sie zur Seite &quot;Konfiguration **[!UICONTROL des technischen]** Adobe IMS-Kontos&quot;.

1. Standardmäßig wird die Registerkarte &quot; **Zertifikat** &quot;geöffnet.

   Wählen Sie in der **Cloud-Lösung** die Option **[!UICONTROL Adobe Brand Portal]**.

1. Markieren Sie das Kontrollkästchen Neues Zertifikat **** erstellen und geben Sie einen **Alias** für das Zertifikat an. Der Alias dient als Name des Dialogfelds.

1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Ein Dialogfeld wird angezeigt. Klicken Sie auf **[!UICONTROL OK]** , um das öffentliche Zertifikat zu generieren.

   ![Zertifikat erstellen](assets/ims-config2.png)

1. Click **[!UICONTROL Download Public Key]** and save the *AEM-Adobe-IMS.crt* certificate file on your machine. The certificate file is used to [create Adobe I/O integration](#createnewintegration).

   ![Zertifikat herunterladen](assets/ims-config3.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Auf der Registerkarte &quot; **Konto** &quot;erstellen Sie das Adobe IMS-Konto, dafür benötigen Sie jedoch die Integrationsdetails. Lassen Sie diese Seite jetzt offen.

   Öffnen Sie eine neue Registerkarte und [erstellen Sie die Adobe I/O-Integration](#createnewintegration) , um die Integrationsdetails für IMS-Kontokonfigurationen abzurufen.

### Adobe I/O-Integration erstellen {#createnewintegration}

Die Adobe-I/O-Integration generiert API-Schlüssel, geheimen Clientschlüssel und Payload (JWT), was für die Einrichtung der IMS-Kontokonfigurationen erforderlich ist.

1. Melden Sie sich bei der Adobe I/O Console mit Systemadministrator-Berechtigungen bei der IMS-Organisation des Markenportal-Mieters an.

   Standard-URL: [https://console.adobe.io/](https://console.adobe.io/)

1. Click **[!UICONTROL Create Integration]**.

1. Wählen Sie **[!UICONTROL Zugriff auf eine API]** und klicken Sie auf **[!UICONTROL Weiter]**.

   ![Neue Integration erstellen](assets/create-new-integration1.png)

1. Eine neue Integrationsseite wird geöffnet.

   Wählen Sie Ihre Organisation aus der Dropdown-Liste aus.

   Wählen Sie in **[!UICONTROL Experience Cloud]** das **[!UICONTROL AEM-Markenportal]** und klicken Sie auf **[!UICONTROL Weiter]**.

   If the Brand Portal option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. Wenn Sie Ihre Organisation nicht kennen, wenden Sie sich an Ihren Administrator.

   ![Integration erstellen](assets/create-new-integration2.png)

1. Geben Sie einen Namen und eine Beschreibung für die Integration ein. Click **[!UICONTROL Select a File from your computer]** and upload the `AEM-Adobe-IMS.crt` file downloaded in the [obtain public certificates](#public-certificate) section.

1. Wählen Sie das Profil Ihrer Organisation aus.

   Oder wählen Sie das Standard-Markenportal für Profil- **[!UICONTROL Assets aus]** und klicken Sie auf Integration **[!UICONTROL erstellen]**. Die Integration wird erstellt.

1. Click **[!UICONTROL Continue to integration details]** to view the integration information.

   Kopieren des **[!UICONTROL API-Schlüssels]**

   Klicken Sie auf **[!UICONTROL Clientgeheimnis abrufen]** und kopieren Sie den geheimen Schlüssel des Kunden.

   ![API-Schlüssel, Client Secret und Nutzdaten einer Integration ](assets/create-new-integration3.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL JWT]** und kopieren Sie die **[!UICONTROL JWT-Nutzlast]**.

   Die API-Schlüssel-, geheimer Clientschlüssel- und JWT-Nutzlastinformationen werden verwendet, um eine IMS-Kontokonfiguration zu erstellen.

### Konfiguration des IMS-Kontos erstellen {#create-ims-account-configuration}

Stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Erhalten eines öffentlichen Zertifikats](#public-certificate)
* [Adobe I/O-Integration erstellen](#createnewintegration)

**Schritte zum Erstellen der Konfiguration des IMS-Kontos:**

1. Öffnen Sie die Seite &quot;IMS-Konfiguration&quot;, Registerkarte &quot; **[!UICONTROL Konten]** &quot;. Sie haben die Seite am Ende des Abschnitts [Öffentliche Zertifikate abrufen](#public-certificate) geöffnet gelassen.

1. Geben Sie einen **[!UICONTROL Titel]** für das IMS-Konto an.

   Geben Sie in **[!UICONTROL Authorization Server]** die URL ein: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Fügen Sie den API-Schlüssel, den geheimen Clientschlüssel und die JWT-Nutzlast ein, die Sie am Ende der [Create Adobe I/O-Integration](#createnewintegration)kopiert haben.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Die Integration wird erstellt.

   ![IMS-Kontokonfiguration](assets/create-new-integration6.png)


1. Select the IMS configuration and click **[!UICONTROL Check Health]**. Das folgende Dialogfeld wird angezeigt.

   Klicken Sie auf **[!UICONTROL Überprüfen]**. Bei erfolgreicher Verbindung wird die Meldung *Token erfolgreich abgerufen* angezeigt.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Erstellen Sie nur eine gültige IMS-Konfiguration. Erstellen Sie nicht mehrere IMS-Konfigurationen.
>
> Stellen Sie sicher, dass die Konfiguration ordnungsgemäß ist. Falls die Konfiguration ungesund ist, löschen Sie sie und erstellen Sie eine neue, gesunde Konfiguration.


### Configure cloud service {#configure-the-cloud-service}

Führen Sie die folgenden Schritte aus, um die Konfiguration des Brand Portal-Cloud-Dienstes zu erstellen:

1. Anmelden bei Ihrer AEM Assets-Cloud-Instanz

1. Navigieren Sie im Bereich **Tools** ![Tools](assets/tools.png) zu **[!UICONTROL Cloud Services > AEM Brand Portal]**.

   Die Seite &quot;Konfiguration des Markenportals&quot;wird geöffnet.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Specify a **[!UICONTROL Title]** for the configuration.

   Wählen Sie die im Schritt erstellte IMS-Konfiguration aus und [erstellen Sie die IMS-Kontokonfiguration](#create-ims-account-configuration).

   Geben Sie in der **[!UICONTROL Dienst-URL]** die URL Ihres Markenportals-Mandanten ein.

   ![](assets/create-cloud-service.png)

1. Click **[!UICONTROL Save and Close]**. Die Cloud-Konfiguration wird erstellt. Ihre AEM Assets-Cloud-Instanz ist jetzt mit dem Markenportal-Mandanten konfiguriert.

### Test configuration {#test-configuration}

1. Melden Sie sich bei Ihrer AEM Assets-Cloud-Instanz an.

1. Navigieren Sie im **Tool** ![Tools](assets/tools.png) -Bedienfeld zu **[!UICONTROL Bereitstellung]** > **[!UICONTROL Verteilung]**.

   ![](assets/test-bpconfig1.png)

1. Die Verteilungsseite wird geöffnet.

   Unter &quot;In Markenportal `bpdistributionagent0` veröffentlichen&quot; **[!UICONTROL wird ein Vertriebsagenten für das Markenportal]** erstellt.

   Click **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Standardmäßig wird ein Distributionsagent für einen Mieter des Markenportals erstellt.

1. Die Seite mit dem Verteilungsagenten wird geöffnet. Standardmäßig wird die Registerkarte &quot; **[!UICONTROL Status]** &quot;geöffnet, in der die Verteilungswarteschlangen gefüllt werden.

   Ein Verteilungsagenten enthält zwei Warteschlangen:
   * Eine Verarbeitungswarteschlange für die Verteilung von Assets an das Markenportal.
   * Eine Fehlerwarteschlange für die Assets, bei denen die Verteilung fehlgeschlagen ist.
   Sie können einzelne Warteschlangen oder die Gesamtkonfiguration testen.

   ![](assets/test-bpconfig3.png)

1. Um die Verbindung zwischen AEM Assets und dem Markenportal zu überprüfen, klicken Sie auf **[!UICONTROL Verbindung]** testen.

   ![](assets/test-bpconfig4.png)

   Unten auf der Seite wird eine Meldung angezeigt, dass Ihr Testpaket erfolgreich bereitgestellt wurde.

   >[!NOTE]
   >
   >Deaktivieren Sie nicht den Distributionsagenten, da dies dazu führen kann, dass die Verteilung der Assets (in der Warteschlange) fehlschlägt.

Markenportal wurde erfolgreich mit Ihrer AEM Assets-Cloud-Instanz konfiguriert. Sie können jetzt:

* [Veröffentlichen von Assets aus AEM Assets im Markenportal](publish-to-brand-portal.md)
* [Veröffentlichen von Ordnern aus AEM Assets in Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Veröffentlichen von Sammlungen aus AEM Assets in Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)


## Verteilungsprotokolle {#distribution-logs}

In den Protokollen finden Sie detaillierte Informationen zu den Aktionen, die mit dem Distributionsagenten durchgeführt werden.

Beispielsweise haben wir ein Asset aus AEM Assets in Brand Portal veröffentlicht, um die Konfiguration zu überprüfen.

1. Führen Sie die Schritte (Schritt 1 bis 4) aus, wie in **[!UICONTROL Test Connection]** gezeigt, und navigieren Sie zur Seite &quot;Distribution Agent&quot;.

1. Wählen Sie die Verteilungswarteschlange **[!UICONTROL queue-bpdistributionAgent0]** und klicken Sie auf **[!UICONTROL Protokolle]** , um die Verteilungsprotokolle Ansicht.

   ![](assets/test-bpconfig5.png)

Der Verteilungsagenten generiert die folgenden Protokolle:

* INFO: Dies ist ein vom System generiertes Protokoll, das bei erfolgreicher Konfiguration ausgelöst wird und den Distributionsagenten aktiviert.
* DSTRQ1 (Anforderung 1): Wird bei Testverbindung ausgelöst.

Beim Veröffentlichen des Assets werden die folgenden Anforderungs- und Antwortprotokolle generiert:

**Distributionsagenten-Anfrage**:
* DSTRQ2 (Anforderung 2): Die Anfrage zur Veröffentlichung von Assets wird ausgelöst.
* DSTRQ3 (Anforderung 3): Das System löst eine weitere Anforderung zum Veröffentlichen des Ordners aus, in dem das Asset vorhanden ist, und repliziert den Ordner im Markenportal.

**Reaktion** des Verteilungsagenten:
* queue-bpdistributionAgent0 (DSTRQ2): Das Asset wird im Markenportal veröffentlicht.
* queue-bpdistributionAgent0 (DSTRQ3): Das System repliziert den Ordner, der das Asset im Markenportal enthält.

Im obigen Beispiel wird eine zusätzliche Anforderung und Antwort ausgelöst. Das System konnte den übergeordneten Ordner (auch als Hinzufügen Pfad bezeichnet) im Markenportal nicht finden, da das Asset zum ersten Mal veröffentlicht wurde. Daher wird eine zusätzliche Anforderung ausgelöst, einen übergeordneten Ordner mit demselben Namen im Markenportal zu erstellen, in dem das Asset veröffentlicht wird.

Wenn der übergeordnete Ordner mit demselben Namen vorhanden ist (alias Hinzufügen Pfad) im Markenportal wird keine zusätzliche Anforderung ausgelöst.

>[!NOTE]
>
>Um die Fehlerprotokolle Ansicht, wählen Sie die Verteilungswarteschlange **[!UICONTROL error-queue-bpdistributionAgent0]** aus und klicken Sie auf **[!UICONTROL Protokolle]**.


## Zusätzliche Informationen {#additional-information}

Gehen Sie zu `/system/console/slingmetrics` , um Statistiken zu verteilten Inhalten zu erhalten:

1. **Zählermetriken**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Zeitmetriken**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`


<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
