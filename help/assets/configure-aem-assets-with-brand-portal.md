---
title: Konfigurieren von AEM Assets as a  [!DNL Cloud Service]  mit Brand Portal
description: Konfigurieren von AEM Assets mit Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: b6283cfff0a0476cc45eb9da75a3a9b2bfdef7bd
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 71%

---


# Konfigurieren von AEM Assets as a [!DNL Cloud Service] mit Brand Portal {#configure-aem-assets-with-brand-portal}

Durch das Konfigurieren von Adobe Experience Manager Assets mit Brand Portal können Sie genehmigte Marken-Assets aus der Adobe Experience Manager Assets as a [!DNL Cloud Service]-Instanz in Brand Portal veröffentlichen und an die Brand Portal-Anwender verteilen.

## Aktivieren des Markenportals mit Cloud Manager {#activate-brand-portal}

Der Cloud Manager-Benutzer aktiviert das Markenportal für ein AEM Assets als [!DNL Cloud Service]-Instanz. Der Arbeitsablauf für die Aktivierung erstellt die erforderlichen Konfigurationen (Autorisierungstoken, IMS-Konfiguration und den Markenportal-Cloud-Dienst) am Backend und gibt den Status des Markenportal-Mandanten in Cloud Manager wieder.

**Voraussetzungen**

Sie benötigen Folgendes, um das Markenportal auf Ihrem AEM Assets als [!DNL Cloud Service]-Instanz zu aktivieren:

* Eine AEM Assets as a [!DNL Cloud Service]-Instanz, die ausgeführt wird.
* Ein Benutzer, der Zugriff auf Cloud Manager hat und Profilen des Cloud Manager-Produkts zugewiesen ist. Weitere Informationen finden Sie unter [Zugriff auf Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#accessing-cloud-manager).

>[!NOTE]
>
>Ein AEM Assets als [!DNL Cloud Service]-Instanz ist berechtigt, nur einen Markenportal-Mandanten zu verbinden. Sie können mehrere Umgebung (Entwicklung, Produktion und Phase) für Ihr AEM Assets als [!DNL Cloud Service]-Instanz erstellen, wobei das Markenportal nur auf einer Umgebung aktiviert wird.

**Schritte zur Aktivierung des Markenportals**

Sie können das Markenportal aktivieren, während Sie die Umgebung für Ihr AEM Assets als [!DNL Cloud Service]-Instanz erstellen, oder separat. Nehmen wir einmal an, dass die Umgebung bereits erstellt wurden und Sie nun das Markenportal aktivieren müssen.

1. Melden Sie sich bei Adobe Cloud Manager an und navigieren Sie zu **[!UICONTROL Umgebung]**.

   Auf der Seite **[!UICONTROL Umgebungen]** wird die Liste aller vorhandenen Umgebung angezeigt.

1. Wählen Sie die Umgebung (einzeln) aus der Liste aus, um die Details zur Umgebung Ansicht.

   Das Markenportal hat eine Berechtigung für eine der verfügbaren Umgebung und wird unter **[!UICONTROL Umgebung Information]** angezeigt.

   Sobald Sie die mit dem Markenportal verknüpfte Umgebung gefunden haben, klicken Sie auf die Schaltfläche **[!UICONTROL Markenportal aktivieren]**, um den Arbeitsablauf für die Aktivierung zu starten.

   ![Brand Portal aktivieren](assets/create-environment4.png)

1. Es kann einige Minuten dauern, bis der Markenportal-Mieter aktiviert ist, da der Arbeitsablauf für die Aktivierung die erforderlichen Konfigurationen am Backend erstellt. Sobald der Pächter des Markenportals aktiviert ist, wird der Status aktiviert.

   ![Status der Ansicht](assets/create-environment5.png)

**Siehe auch**:
* [hinzufügen und Rollen in AEM Assets als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/add-users-roles.html?lang=en#role-definitions)

* [Umgebung in Cloud Manager verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#adding-environments)


**Melden Sie sich bei Ihrem Brand Portal-Mandanten an**:

Nach der Aktivierung Ihres Markenportal-Mandanten in Cloud Manager können Sie sich von der Admin Console aus oder direkt über die Mandanten-URL beim Markenportal anmelden.

Die Standard-URL Ihres Markenportal-Mandanten lautet: `https://<tenant-id>.brand-portal.adobe.com/`.

Führen Sie die folgenden Schritte aus, wenn Sie sich nicht sicher sind, wie die URL des Markenportals aussieht:

1. Melden Sie sich bei [Admin Console](http://adminconsole.adobe.com/) an und navigieren Sie zu **[!UICONTROL Produkte]**.
1. Wählen Sie in der linken Leiste **[!UICONTROL Adobe Experience Manager Markenportal - Markenportal]** aus.
1. Klicken Sie auf **[!UICONTROL Zu Markenportal]**, um das Markenportal direkt im Browser zu öffnen.

   Oder kopieren Sie die URL des Markenportals-Mieters und fügen Sie sie in Ihren Browser ein, um die Oberfläche des Markenportals zu öffnen.

   ![Markenportal aufrufen](assets/access-bp-on-cloud.png)


**Testen Sie die Verbindung.**

Führen Sie die folgenden Schritte aus, um die Verbindung zwischen Ihrem AEM Assets als [!DNL Cloud Service]-Instanz und dem Markenportal-Mandanten zu validieren:

1. Melden Sie sich bei AEM Assets an.

1. Navigieren Sie im Bedienfeld **Tools** zu **[!UICONTROL Bereitstellung]** > **[!UICONTROL Verteilung]**.

   ![](assets/test-bpconfig1.png)

   Ein Brand Portal-Verteilungsagent (**[!UICONTROL bpdistributionagent0]**) wird unter **[!UICONTROL Im Brand Portal veröffentlichen]** erstellt.

   ![](assets/test-bpconfig2.png)


1. Klicken Sie auf **[!UICONTROL Im Brand Portal veröffentlichen]**, um den Verteilungsagenten zu öffnen.

   Ihnen werden dann die Verteilungswarteschlangen auf der Registerkarte **[!UICONTROL Status]** angezeigt.

   Ein Verteilungsagent enthält zwei Warteschlangen:
   * **Verarbeitungswarteschlange (processing-queue)**: für die Verteilung von Assets an Brand Portal.

   * **Fehlerwarteschlange (error-queue)**: für die Assets, bei denen die Verteilung fehlgeschlagen ist.
   >[!NOTE]
   >
   >Es wird empfohlen, die Fehler zu überprüfen und die **Fehlerwarteschlange** regelmäßig zu löschen.

   ![](assets/test-bpconfig3.png)

1. Um die Verbindung zwischen AEM Assets as a [!DNL Cloud Service] und Brand Portal zu überprüfen, klicken Sie auf das Symbol **[!UICONTROL Verbindung testen]**.

   ![](assets/test-bpconfig4.png)

   Ihnen wird eine Meldung angezeigt, dass Ihr *Testpaket erfolgreich bereitgestellt wurde*.

   >[!NOTE]
   >
   >Vermeiden Sie das Deaktivieren des Verteilungsagenten, da dies dazu führen kann, dass die Verteilung der Assets (in der Warteschlange) fehlschlägt.

Um die Verbindung zwischen Ihrem AEM Assets als [!DNL Cloud Service]-Instanz und dem Markenportal-Mandanten zu überprüfen, veröffentlichen Sie ein Asset von AEM Assets in das Markenportal. Wenn die Verbindung erfolgreich hergestellt wurde, ist das veröffentlichte Asset in der Benutzeroberfläche des Markenportals sichtbar.


Sie haben nun die folgenden Möglichkeiten:

* [Veröffentlichen von Assets aus AEM Assets in Brand Portal](publish-to-brand-portal.md)
* [Veröffentlichen von Ordnern aus AEM Assets in Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Veröffentlichen von Sammlungen aus AEM Assets in Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Veröffentlichen von Assets vom Markenportal nach AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=en)  - Asset-Beschaffung im Markenportal
* [Veröffentlichen von Vorgaben, Schemata und Facetten in Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Veröffentlichen von Tags in Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

Weitere Informationen finden Sie in der [Dokumentation zu Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/home.html).

**Verteilungsprotokolle**

Sie können die Verteilungsagenten-Protokolle für den Asset-Veröffentlichungs-Workflow überwachen.

Beispielsweise haben wir ein Asset aus AEM Assets in Brand Portal veröffentlicht, um die Konfiguration zu validieren.

1. Führen Sie die Schritte (1–4) aus, wie im Abschnitt [Konfiguration testen](#test-configuration) gezeigt, und navigieren Sie zur Seite des Verteilungsagenten.
1. Klicken Sie auf **[!UICONTROL Protokolle]**, um die Verarbeitungs- und Fehlerprotokolle anzuzeigen.

   ![](assets/test-bpconfig5.png)

Der Verteilungsagent hat die folgenden Protokolle generiert:

* INFO: Dies ist ein vom System erstelltes Protokoll, das bei einer erfolgreichen Konfiguration des Verteilungsagenten ausgelöst wird.
* DSTRQ1 (Anfrage 1): Wird bei der Testverbindung ausgelöst.

Beim Veröffentlichen des Assets werden die folgenden Anfrage- und Antwortprotokolle generiert:

**Anfrage des Verteilungsagenten**:

* DSTRQ2 (Anfrage 2): Die Anfrage zur Veröffentlichung des Assets wird ausgelöst.
* DSTRQ3 (Anfrage 3): Das System löst eine weitere Anfrage zum Veröffentlichen des AEM Assets-Ordners aus, in dem sich das Asset befindet, und repliziert den Ordner in Brand Portal.

**Antwort des Verteilungsagenten**:

* queue-bpdistributionagent0 (DSTRQ2): Das Asset wird in Brand Portal veröffentlicht.
* queue-bpdistributionagent0 (DSTRQ3): Das System repliziert den AEM Assets-Ordner, der das Asset enthält, in Brand Portal.

Im obigen Beispiel werden eine zusätzliche Anfrage und Antwort ausgelöst. Das System konnte den übergeordneten Ordner (Hinzufügen-Pfad) in Brand Portal nicht finden, da das Asset zum ersten Mal veröffentlicht wurde. Daher wurde eine zusätzliche Anfrage ausgelöst, einen übergeordneten Ordner mit demselben Namen in Brand Portal zu erstellen, in dem das Asset veröffentlicht wird.

>[!NOTE]
>
>Es wird eine zusätzliche Anfrage generiert, wenn der übergeordnete Ordner nicht in Brand Portal vorhanden ist oder in AEM Assets geändert wurde.

Neben dem Automatisierungs-Workflow zur Aktivierung des Markenportals unter AEM Assets als [!DNL Cloud Service] gibt es eine weitere Methode, um AEM Assets manuell als [!DNL Cloud Service] mit Markenportal zu konfigurieren, wobei die Adobe Developer Console verwendet wird, die nicht mehr empfohlen wird.

>[!NOTE]
>
>Wenden Sie sich an den Kundendienst, wenn Sie während der Aktivierung Ihres Markenportal-Mandanten Probleme haben.

## Manuelle Konfiguration mit Adobe Developer Console {#manual-configuration}

Im folgenden Abschnitt wird die manuelle Konfiguration von AEM Assets als [!DNL Cloud Service] mit Markenportal mithilfe der Adobe Developer Console beschrieben.

Zuvor wurde AEM Assets als [!DNL Cloud Service] manuell mit dem Markenportal über die Adobe Developer Console konfiguriert, die ein Adobe Identity Management Services (IMS)-Kontotoken zur Autorisierung des Markenportal-Mieters abruft. Dazu sind Konfigurationen sowohl in AEM Assets als auch in der Adobe Developer Console erforderlich.

1. Erstellen Sie in AEM Assets ein IMS-Konto und generieren Sie einen öffentlichen Schlüssel (Zertifikat).
1. Erstellen Sie in der Adobe Developer Console ein Projekt für Ihren Brand Portal-Mandanten (Organisation).
1. Konfigurieren Sie unter dem Projekt eine API mithilfe des öffentlichen Schlüssels, um eine Service-Konto-Verbindung zu erstellen.
1. Rufen Sie die Anmeldedaten für das Service-Konto und die JWT-Payload-Informationen (JSON Web Token) ab.
1. Konfigurieren Sie in AEM Assets das IMS-Konto mit den Anmeldedaten für das Service-Konto und die JWT-Payload.
1. Konfigurieren Sie in AEM Assets den Brand Portal-Cloud Service mit dem IMS-Konto und dem Brand Portal-Endpunkt (Organisations-URL).
1. Testen Sie die Konfiguration, indem Sie ein Asset aus AEM Assets in Brand Portal veröffentlichen.

>[!NOTE]
>
>Eine AEM Assets as a [!DNL Cloud Service]-Instanz darf nur mit einem Brand Portal-Mandanten konfiguriert werden.

**Voraussetzungen**

Sie benötigen Folgendes, um AEM Assets mit Brand Portal zu konfigurieren:

* Eine AEM Assets as a [!DNL Cloud Service]-Instanz, die ausgeführt wird
* Eine Brand Portal-Mandanten-URL
* Ein Anwender mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten

## Erstellen der Konfiguration {#create-new-configuration}

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um AEM Assets mit Brand Portal zu konfigurieren.

1. [Abrufen eines öffentlichen Zertifikats](#public-certificate)
1. [Erstellen einer JWT-Verbindung (Service-Konto)](#createnewintegration)
1. [Konfigurieren des IMS-Kontos](#create-ims-account-configuration)
1. [Konfigurieren von Cloud Service](#configure-the-cloud-service)

### Erstellen der IMS-Konfiguration {#create-ims-configuration}

Die IMS-Konfiguration authentifiziert Ihre AEM Assets as a [!DNL Cloud Service]-Instanz beim Brand Portal-Mandanten.

Die IMS-Konfiguration umfasst zwei Schritte:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Konfigurieren des IMS-Kontos](#create-ims-account-configuration)

### Abrufen eines öffentlichen Zertifikats {#public-certificate}

Der öffentliche Schlüssel (Zertifikat) authentifiziert Ihr Profil in der Adobe Developer Console.

1. Melden Sie sich bei AEM Assets an.
1. Navigieren Sie im Bedienfeld **Tools** zu **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**.
1. Klicken Sie auf der Seite mit den Adobe IMS-Konfigurationen auf **[!UICONTROL Erstellen]**. Sie werden zur Seite für die **[!UICONTROL Konfiguration des technischen Adobe IMS-Kontos]** weitergeleitet. Standardmäßig wird die Registerkarte **Zertifikat** geöffnet.
1. Wählen Sie **[!UICONTROL Adobe Brand Portal]** in der Dropdown-Liste **[!UICONTROL Cloud-Lösung]** aus.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Neues Zertifikat erstellen]** und geben Sie einen **Alias** für den öffentlichen Schlüssel an. Der Alias dient als Name des öffentlichen Schlüssels.
1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Klicken Sie auf **[!UICONTROL OK]**, um den öffentlichen Schlüssel zu generieren.

   ![Zertifikat erstellen](assets/ims-config2.png)

1. Klicken Sie auf das Symbol **[!UICONTROL Öffentlichen Schlüssel herunterladen]** und speichern Sie die CRT-Datei auf Ihrem Computer.

   Der öffentliche Schlüssel wird später zum Konfigurieren der API für Ihren Brand Portal-Mandanten und zum Generieren von Anmeldedaten für Service-Konten in der Adobe Developer Console verwendet.

   ![Zertifikat herunterladen](assets/ims-config3.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Auf der Registerkarte **Konto** wird das Adobe IMS-Konto erstellt. Dafür werden die Anmeldedaten für Service-Konten benötigt, die in der Adobe Developer Console generiert werden. Lassen Sie diese Seite vorerst offen.

   Öffnen Sie eine neue Registerkarte und [erstellen Sie in der Adobe Developer Console eine JWT-Verbindung (Service-Konto)](#createnewintegration), um die Anmeldedaten und die JWT-Payload für die Konfiguration des IMS-Kontos abzurufen.

### Erstellen einer JWT-Verbindung (Service-Konto) {#createnewintegration}

In der Adobe Developer Console werden Projekte und APIs auf Brand Portal-Mandantenebene (Organisationsebene) konfiguriert. Beim Konfigurieren einer API wird eine Service-Konto-Verbindung (JWT-Verbindung) hergestellt. Es gibt zwei Methoden zum Konfigurieren der API: Generieren eines Schlüsselpaars (privater und öffentlicher Schlüssel) oder Hochladen eines öffentlichen Schlüssels. Um AEM Assets mit Brand Portal zu konfigurieren, müssen Sie einen öffentlichen Schlüssel (Zertifikat) in AEM Assets generieren und Anmeldedaten in der Adobe Developer Console erstellen, indem Sie den öffentlichen Schlüssel hochladen. Diese Anmeldedaten werden zum Konfigurieren des IMS-Kontos in AEM Assets benötigt. Sobald das IMS-Konto konfiguriert ist, können Sie den Brand Portal-Cloud Service in AEM Assets konfigurieren.

Führen Sie die folgenden Schritte aus, um die Anmeldedaten für das Service-Konto und die JWT-Payload zu generieren:

1. Melden Sie sich bei der Adobe Developer Console mit Systemadministratorrechten für die IMS-Organisation (den Brand Portal-Mandanten) an. Die Standardeinstellung ist  [https://www.adobe.com/go/devs_console_ui_de](https://www.adobe.com/go/devs_console_ui_de).


   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie die richtige IMS-Organisation (Brand Portal-Mandant) aus der Dropdown-Liste (Organisation) oben rechts ausgewählt haben.

1. Klicken Sie auf **[!UICONTROL Neues Projekt erstellen]**. Für Ihre Organisation wird ein leeres Projekt mit einem systemgenerierten Namen erstellt.

   Klicken Sie auf **[!UICONTROL Projekt bearbeiten]**, um den **[!UICONTROL Projekttitel]** und die **[!UICONTROL Projektbeschreibung]** zu aktualisieren, und klicken Sie auf **[!UICONTROL Speichern]**.

1. Klicken Sie auf der Registerkarte mit der **[!UICONTROL Projektübersicht]** auf **[!UICONTROL API hinzufügen]**.

1. Wählen Sie im Fenster **[!UICONTROL API hinzufügen]** die Option **[!UICONTROL AEM Brand Portal]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   Stellen Sie sicher, dass Sie Zugriff auf den AEM Brand Portal-Service haben.

1. Klicken Sie im Fenster **[!UICONTROL API konfigurieren]** auf **[!UICONTROL Öffentlichen Schlüssel hochladen]**. Klicken Sie dann auf **[!UICONTROL Datei auswählen]** und laden Sie den öffentlichen Schlüssel (.crt-Datei) hoch, den Sie im Abschnitt zum [Abrufen des öffentlichen Zertifikats](#public-certificate) heruntergeladen haben.

   Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Öffentlichen Schlüssel hochladen](assets/service-account3.png)

1. Überprüfen Sie den öffentlichen Schlüssel und klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie **[!UICONTROL Assets Brand Portal]** als Standardproduktprofil aus und klicken Sie auf **[!UICONTROL Konfigurierte API speichern]**.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![Profil auswählen](assets/service-account4.png)

1. Sobald die API konfiguriert ist, werden Sie zur Seite mit der API-Übersicht weitergeleitet. Klicken Sie in der linken Navigation unter **[!UICONTROL Anmeldedaten]** auf die Option **[!UICONTROL Service-Konto (JWT)]**.

   >[!NOTE]
   >
   >Sie können die Anmeldedaten einsehen und weitere Aktionen durchführen, beispielsweise JWT-Token generieren, Anmeldedaten kopieren und Client-Geheimnisse abrufen.

1. Kopieren Sie auf der Registerkarte **[!UICONTROL Client-Anmeldedaten]** die **[!UICONTROL Client-ID]**.

   Klicken Sie auf **[!UICONTROL Client-Geheimnis abrufen]** und kopieren Sie das **[!UICONTROL Client-Geheimnis]**.

   ![Service-Konto-Anmeldedaten](assets/service-account5.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL JWT generieren]** und kopieren Sie die Informationen zur **[!UICONTROL JWT-Payload]**.

Sie können jetzt die Client-ID (API-Schlüssel), das Client-Geheimnis und die JWT-Payload verwenden, um das [IMS-Konto in AEM Assets zu konfigurieren](#create-ims-account-configuration).

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
* [Erstellen einer JWT-Verbindung (Service-Konto)](#createnewintegration)

Gehen Sie wie folgt vor, um das IMS-Konto zu konfigurieren.

1. Öffnen Sie die IMS-Konfiguration und navigieren Sie zur Registerkarte **[!UICONTROL Konto]**. Sie haben die Seite offen gelassen, während Sie das [öffentliche Zertifikat abgerufen](#public-certificate) haben.

1. Geben Sie einen **[!UICONTROL Titel]** für das IMS-Konto an.

   Geben Sie im Feld **[!UICONTROL Autorisierungs-Server]** die URL ein: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/).

   Fügen Sie die Client-ID im Feld **[!UICONTROL API-Schlüssel]** sowie das **[!UICONTROL Client-Geheimnis]** und die **[!UICONTROL Payload]** (JWT-Payload) ein, die Sie beim [Erstellen der JWT-Verbindung (Service-Konto)](#createnewintegration) kopiert haben.

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

1. Navigieren Sie im Bedienfeld **Tools** zu **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klicken Sie auf der Seite mit den Brand Portal-Konfigurationen auf **[!UICONTROL Erstellen]**.

1. Geben Sie einen **[!UICONTROL Titel]** für die Konfiguration ein.

   Wählen Sie die IMS-Konfiguration aus, die Sie beim [Konfigurieren des IMS-Kontos](#create-ims-account-configuration) erstellt haben.

   Geben Sie im Feld **[!UICONTROL Dienst-URL]** Ihre Brand Portal-Mandanten-URL (Organisations-URL) ein.

   ![](assets/create-cloud-service.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Konfiguration wird erstellt.

   Ihre AEM Assets as a [!DNL Cloud Service]-Instanz ist jetzt mit dem Brand Portal-Mandanten konfiguriert.

Sie können die Konfiguration jetzt testen, indem Sie den Verteilungsagenten überprüfen und Assets im Markenportal veröffentlichen.

<!--
### Test configuration {#test-configuration}

Perform the following steps to validate the configuration:

1. Log in to AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

    ![](assets/test-bpconfig1.png)

   A Brand Portal distribution agent (**[!UICONTROL bpdistributionagent0]**) is created under **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)


1. Click **[!UICONTROL Publish to Brand Portal]** to open the distribution agent. 

   You can see the distribution queues under the **[!UICONTROL Status]** tab. 
   
   A distribution agent contains two queues: 
   * **processing-queue**: for the distribution of assets to Brand Portal. 

   * **error-queue**: for the assets where distribution has failed. 
   
   >[!NOTE]
   >
   >It is recommended to review the failures and  clear the **error-queue** periodically.  

   ![](assets/test-bpconfig3.png)

1. To verify the connection between AEM Assets as a [!DNL Cloud Service] and Brand Portal, click on the **[!UICONTROL Test Connection]** icon.

   ![](assets/test-bpconfig4.png)

   A message appears that your *test package is successfully delivered*.

   >[!NOTE]
   >
   >Avoid disabling the distribution agent, as it can cause the distribution of the assets (running-in-queue) to fail.

You can now:

* [Publish assets from AEM Assets to Brand Portal](publish-to-brand-portal.md)
* [Publish folders from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publish collections from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Publish assets from Brand Portal to AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=en) - Asset Sourcing in Brand Portal
* [Publish presets, schemas, and facets to Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Publish tags to Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

See [Brand Portal documentation](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) for more information.

## Distribution logs {#distribution-logs}

You can monitor the distribution agent logs for the asset publishing workflow. 

For example, we have published an asset from AEM Assets to Brand Portal to validate the configuration. 

1. Follow the steps (from 1 to 4) as shown in the [Test Configuration](#test-configuration) section and navigate to the distribution agent page.
1. Click **[!UICONTROL Logs]** to view the processing and error logs.

   ![](assets/test-bpconfig5.png)

The distribution agent has generated the following logs:

* INFO: This is a system-generated log that triggers on successful configuration of the distribution agent. 
* DSTRQ1 (Request 1): Triggers on test connection.

On publishing the asset, the following request and response logs are generated:

**Distribution agent request**:

* DSTRQ2 (Request 2): The asset publishing request is triggered.
* DSTRQ3 (Request 3): The system triggers another request to publish the AEM Assets folder (in which the asset exists) and replicates the folder in Brand Portal.

**Distribution agent response**:

* queue-bpdistributionagent0 (DSTRQ2): The asset is published to Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): The system replicates the AEM Assets folder (containing the asset) in Brand Portal.

In the above example, an additional request and response is triggered. The system could not find the parent folder (Add Path) in Brand Portal because the asset was published for the first time, therefore, it triggered an additional request to create a parent folder with the same name in Brand Portal where the asset is published.  

>[!NOTE]
>
>Additional request is generated in case the parent folder does not exist in Brand Portal or has been modified in AEM Assets. 
-->

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
