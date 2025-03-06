---
title: ' [!DNL Dynamic Media] Prime und Ultimate aktivieren'
description: Erfahren Sie, wie Sie [!DNL Dynamic Media] Prime- und Ultimate-Angebote aktivieren.
feature: Asset Management
role: User, Admin
exl-id: 0ee161f5-bf44-41f1-928e-c07574fd43cc
source-git-commit: 3962b687a7d0d3f5551b23fbe5c2ee2c21bd1d89
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 2%

---

# Aktivieren [!DNL Dynamic Media] Prime und Ultimate {#enable-dynamic-media-prime-and-ultimate}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

[!DNL Adobe Experience Manager] as a Cloud Service ermöglicht Ihnen den Zugriff auf [!DNL Dynamic Media] Prime- und Ultimate-Angebote, um Ihre digitalen Workflows zu optimieren und das Content-Management zu optimieren. Unter [Dynamic Media Prime und Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md) erfahren Sie mehr über die Vorteile und die wichtigsten Unterschiede zwischen ihnen.

Dieser Artikel enthält den kompletten Workflow zur Aktivierung der [!DNL Dynamic Media] Prime- und Ultimate-Angebote.

## [!DNL Dynamic Media] Ultimate aktivieren {#enable-dynamic-media-ultimate}

Führen Sie die folgenden Schritte in Ihrer Cloud Service-Umgebung aus, um [!DNL Dynamic Media] Ultimate zu aktivieren:

1. [Aktivieren [!DNL Dynamic Media with OpenAPI]](#activate-dynamic-media-with-openapi)
1. [Konfigurieren [!DNL Dynamic Media] Lösungen](#configure-dynamic-media-solutions)
1. [Erstellen und Auflisten  [!DNL Dynamic Media]  Unternehmen](#create-and-list-dynamic-media-companies)
1. [Benutzerdefinierte Domain in der Bereitstellungsebene konfigurieren](#configure-custom-domain-in-delivery-tier)
<!--
1. [Onboard API keys using the [!DNL AEM] [!DNL Dynamic Media] API card](#onboarding-api-keys)
-->
Wenn Sie [!DNL Dynamic Media Prime] aktivieren müssen, lesen Sie die unter „Aktivieren[ bereitgestellten  [!DNL Dynamic Media Prime]](#enable-dynamic-media-prime).

### Aktivieren [!DNL Dynamic Media with OpenAPI] {#activate-dynamic-media-with-openapi}

[!DNL Dynamic Media] mit den OpenAPI-Funktionen bildet das DAM den Kern eines agilen und effizienten Ökosystems für die Bereitstellung von Inhalten, um die Asset-Governance und -Bereitstellung sicherzustellen.

Der erste Schritt im Prozess der Aktivierung [!DNL Dynamic Media] Ultimate besteht darin, [[!DNL Dynamic Media] mit OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) für Ihre Cloud Service-Umgebung zu aktivieren.

#### Bereiten Sie sich auf den Einstieg vor {#prerequisites}

Stellen Sie sicher, dass Sie die folgenden Anforderungen erfüllen, bevor Sie den Aktivierungsprozess starten:

1. [Zugriff auf Cloud Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [Ihr Programm umfasst  [!DNL Dynamic Media]  Lösungen](#configure-dynamic-media-solutions).
1. Ihr Unternehmen hat mit OpenAPI-Credits [!DNL Dynamic Media].

#### Aktivieren von [!DNL Dynamic Media with OpenAPI] in Ihrer Cloud Service-Umgebung {#enable-dynamic-media-with-openapi-capabilites-in-your-CS-environment}

Führen Sie die folgenden Schritte aus, um [!DNL Dynamic Media with OpenAPI] für Ihre Cloud Service-Umgebung zu aktivieren:

1. [Navigieren Sie zur Cloud Manager-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).

1. [Erstellen einer Umgebung](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/create-environments) wenn Sie keinen Zugriff auf eine vorhandene haben.

1. Wählen **[!UICONTROL Zum Aktivieren klicken]** in der Zeile **[!UICONTROL Dynamic]**) des Abschnitts **[!UICONTROL Umgebungsinformationen]** auf der Seite Umgebungsdetails aus.

   ![Aktivieren von Dynamic Media mit OpenAPI-Funktionen](/help/assets/assets/activate-adv-capabiliites-of-dm-openAPI.png)

1. Klicken **[!UICONTROL im]** auf „Aktivieren“, um den [!DNL Dynamic Media with OpenAPI] zu starten. Nach erfolgreicher Aktivierung zeigt die Cloud Manager die folgenden Statusaktualisierungen an:
   1. **[!UICONTROL Umgebungsstufe]**: **[!UICONTROL Läuft]**
   1. ![DM activated](/help/assets/assets/Images_icon.svg)**[!UICONTROL Dynamic Media ]**:**[!UICONTROL  OpenAPI-Funktionen sind aktiviert ]**

      ![Aktivierung erfolgreich](/help/assets/assets/activation-successful.png){width="700" align="center"}

#### Aktivierung wiederholen {#retry-activation}

Wenn die Aktivierung fehlschlägt, zeigt die Cloud Manager die folgenden Statusaktualisierungen an:

* **[!UICONTROL Umgebungsstufe]**: **[!UICONTROL DM mit OpenAPI fehlgeschlagen]**
* ![DM activated](/help/assets/assets/Images_icon.svg)**[!UICONTROL Dynamic Media ]**:**[!UICONTROL  OpenAPI-Funktionen konnten nicht aktiviert werden ]**

  ![Aktivierung erneut versuchen](/help/assets/assets/retry-dm-openapi-failed-activation.png){width="700" align="center"}

Wählen Sie **[!UICONTROL Zum Wiederholen klicken]**, um die Aktivierung neu zu starten.

Führen Sie alternativ die folgenden Schritte aus, um den Aktivierungsprozess neu zu starten:

1. Navigieren Sie zu der Seite, auf der alle Umgebungen aufgelistet sind.

1. Klicken Sie auf Weitere Optionen ![weitere Optionen](/help/assets/assets/three-dots.svg) am Ende der Zeile „Umgebung“.

1. Wählen Sie **[!UICONTROL DM mit OpenAPI Activation erneut ausführen]**, um die Aktivierung neu zu starten.

   ![Wiederholen Sie die Aktivierung über die Seite mit den Umgebungsdetails](/help/assets/assets/restart-activation-process-from-list-environment-page.png)

### Konfigurieren von [!DNL Dynamic Media] {#configure-dynamic-media-solutions}

Konfigurieren Sie [!UICONTROL Dynamic Media]-Lösungen für die Verwendung der grundlegenden und erweiterten Funktionen von [Dynamic Media mit OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) in bestehenden oder neuen Umgebungen, die in Cloud Manager verfügbar sind.

#### Bereiten Sie sich auf den Einstieg vor {#prerequisites-to-configure-dynamic-media-solutions}

Stellen Sie sicher, dass Sie Folgendes zum Konfigurieren von [!UICONTROL Dynamic Media]Lösungen haben:

1. [Zugriff auf Cloud Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. Ihr Unternehmen verfügt über [!DNL Dynamic Media with OpenAPI] Credits.

#### Konfigurieren von [!DNL Dynamic Media]-Lösungen für die Asset-Bereitstellung {#configure-dynamic-media-solutions-for-asset-delivery}

Führen Sie die folgenden Schritte aus:

1. [Erstellen Sie ein neues Programm](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/create-program) oder navigieren Sie zu einem vorhandenen Programm und klicken Sie auf **[!UICONTROL Bearbeiten]**. Auf **[!UICONTROL Seite „Für Produktion einrichten]** wird die Registerkarte **[!UICONTROL Lösungen und Add-ons]** angezeigt.

1. Wählen Sie **[!UICONTROL Assets]**, **[!UICONTROL Assets Prime]**, **[!UICONTROL Assets Ultimate]** oder **[!UICONTROL Sites]** aus, um Ihrem Programm die **[!UICONTROL Dynamic Media]**-Lösung hinzuzufügen.

1. Wählen Sie **[!UICONTROL Dynamic Media]**-Lösung aus und klicken Sie auf **[!UICONTROL Weiter]**, um **[!UICONTROL Dynamic Media]**-Lösung zu Ihrem Programm hinzuzufügen. Mit dieser Aktion werden alle vorhandenen Umgebungen in Ihrem Programm neu gestartet und die [!DNL Dynamic Media] Lösung hinzugefügt. Außerdem wird jede neue Umgebung, die Sie unter Ihrem Programm erstellen, automatisch [!DNL Dynamic Media].

   ![Für die Produktion einrichten](/help/assets/assets/set-up-for-prod.png){width="500" align="center"}

Unter [Aktivieren [!DNL Dynamic Media with OpenAPI]](#activate-dynamic-media-with-openapi) finden Sie Informationen darüber, wie Sie die Funktionen von [!DNL Dynamic Media] mit OpenAPI-Funktionen in Ihrer Umgebung nutzen können.

### Erstellen und Auflisten [!DNL Dynamic Media] Unternehmen {#create-and-list-dynamic-media-companies}

Erstellen Sie [!DNL Dynamic Media] Unternehmen in Ihrer AEM Cloud Service-Umgebung und listen Sie sie auf, um Konfigurationen in Ihrer AEM-Umgebung zu verwalten.

#### Bereiten Sie sich auf den Einstieg vor {#prerequisites-to-create-and-list-dynamic-media-companies}

Um die vorhandenen Unternehmen (Konten) anzuzeigen oder ein neues [!DNL Dynamic Media] Unternehmen (Konto) in Ihrer IMS-Organisation hinzuzufügen, benötigen Sie Folgendes:

1. [Zugriff auf Cloud Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).

1. [!DNL Dynamic Media with OpenAPI] Credits in Ihrer Organisation.

#### Erstellen und Auflisten [!DNL Dynamic Media] Unternehmen in Ihrer IMS-Organisation {#create-and-list-dynamic-media-companies-in-your-ims-organisation}

Führen Sie die folgenden Schritte aus, um ein neues [!DNL Dynamic Media] (Konto) zu erstellen und aufzulisten, das in Ihrer [!DNL AEM] konfiguriert werden kann:

1. Navigieren Sie zur Lizenzseite für [Cloud Manager](https://experience-stage.adobe.com/#/@ssahnichstage/cloud-manager/license).

1. Klicken Sie auf **[!UICONTROL Firma hinzufügen]**. Das Dialogfeld **[!UICONTROL Dynamic Media-Firma erstellen]** wird angezeigt.

1. Geben Sie einen eindeutigen [!DNL Dynamic Media] Unternehmensnamen an, wählen Sie eine Unternehmensregion aus und fügen Sie eine Liste der E-Mail-IDs für Unternehmensadministratoren hinzu, getrennt durch Kommas.

   ![Dynamic Media-Unternehmen erstellen](/help/assets/assets/create-dynamic-media-company.png){width="500" align="center"}

1. Klicken Sie **[!UICONTROL Erstellen]**, um mit der Erstellung Ihrer Firma zu beginnen. Mit dieser Aktion wird eine neue Zeile zum Abschnitt **[!UICONTROL [!DNL Dynamic Media]Unternehmen hinzugefügt]** der **[!UICONTROL Wird eingerichtet]** als **[!UICONTROL des Unternehmens]**.

   ![Initiierte Dynamic Media-Unternehmenserstellung](/help/assets/assets/dm-company-creation-initiated.png)

1. **Optional:** Klicken Sie auf ![Infosymbol](/help/assets/assets/info-icon-solid-black.svg), um die Details des Unternehmens anzuzeigen. Der **[!UICONTROL STATUS]** wird auf **[!UICONTROL Bereit]** aktualisiert, wenn das Unternehmen erstellt wird.

   ![Unternehmensinformationen für Dynamic Media](/help/assets/assets/dm-company-information.png)

1. Überprüfen Sie als Dynamic Media-Administrator Ihr Postfach auf eine Begrüßungs-E-Mail, die eine Liste von Schritten enthält, um [ Unternehmen in Ihrer [!DNL AEM] Cloud Service-Umgebung zu konfigurieren [!DNL Dynamic Media]](/help/assets/dynamic-media/config-dm.md#architecture-diagram-of-dynamic-media) um zu beginnen.

   ![Willkommens-E-Mail](/help/assets/assets/welcome-email.png)

#### Unternehmenserstellung wiederholen {#retry-company-creation}

Wenn [!DNL Dynamic Media] Erstellung des Unternehmens fehlschlägt, führen Sie die folgenden Schritte basierend auf dem Fehlerstatus aus:

1. Wenn **[!UICONTROL Status]** „Ausstehend“ ist, wenden Sie sich zur Lösung des Problems an das Support-Team.

   ![Status „Ausstehend](/help/assets/assets/company-creation-pending-status.png){width="350" align="center"}

1. Wenn **[!UICONTROL Status]** fehlgeschlagen ist, versuchen Sie es basierend auf der Fehlerursache erneut.

   ![Status „Fehlgeschlagen](/help/assets/assets/company-creation-failure-status.png){width="380" align="center"}

### Optional: Konfigurieren einer benutzerdefinierten Domain in der Bereitstellungsebene {#configure-custom-domain-in-delivery-tier}

AEM as a Cloud Service verfügt zwar über eine Standard-Domain, kann jedoch nach Bedarf angepasst werden. Hängen Sie mithilfe von Cloud Manager eine benutzerdefinierte Domain an die Bereitstellungsebene an.

#### Bereiten Sie sich auf den Einstieg vor {#prerequisites-to-configure-custom-domain-in-delivery-tier}

Stellen Sie sicher, dass Sie die folgenden Anforderungen erfüllen, bevor Sie den Konfigurationsprozess starten:

1. [Zugriff auf Cloud Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [Bereits  [!DNL Dynamic Media with OpenAPI]  Ihrer Umgebung aktiviert](#activate-dynamic-media-with-openapi).
1. Aktivierte [!DNL Dynamic Media with OpenAPI] im Status „Bereit“.
1. EV- oder OV-Zertifikat für die Domain, die für die Bereitstellungsebene verwendet werden soll. Weitere Informationen finden [ unter „Einführung ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates) SSL-Zertifikate“.

#### Konfigurieren einer benutzerdefinierten Domain in der Bereitstellungsebene mithilfe von Cloud Manager {#configure-custom-domain-in-delivery-tier-using-cloud-manager}

Führen Sie die folgenden Schritte in Cloud Manager aus, um eine benutzerdefinierte Domain in der Bereitstellungsebene zu konfigurieren:

1. [Hinzufügen eines vom Kunden verwalteten SSL-Zertifikats](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate#add-customer-managed-ssl-cert).

1. [Benutzerdefinierten Domain-Namen hinzufügen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name#adding-cdn-settings).

1. Navigieren Sie zur Seite mit den Umgebungsdetails und [ Sie eine CDN-Konfiguration ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cdn-configurations/add-cdn-config). Wählen Sie beim Hinzufügen der Konfiguration **[!UICONTROL Versand]** im Feld **[!UICONTROL Ebene]** im Dialogfeld **[!UICONTROL CDN konfigurieren]** aus.

   ![Konfigurieren von CDN](/help/assets/assets/select-delivery-tier-in-configure-cdn-form.png)

   Nach dem Hinzufügen der Konfigurationen wird **[!UICONTROL STATUS]** von **[!UICONTROL CDN-Konfigurationen]** auf **[!UICONTROL Applied]** aktualisiert.

   ![Konfigurieren des CDN-Bereitstellungsstatus](/help/assets/assets/cdn-configuration-deployment-status.png)

1. Klicken Sie auf Weitere Optionen ![weitere Optionen](/help/assets/assets/three-dots.svg) und wählen Sie **[!UICONTROL Go-Live-Bereitschaft]** aus, um das Dialogfeld **[!UICONTROL Go-Live-]**&quot; anzuzeigen.

   ![Option „Go-Live-Bereitschaft“](/help/assets/assets/go-live-readiness-option.png)

1. Führen Sie die Schritte **[!UICONTROL Konfigurieren von CNAME]** aus, um [cdn.adobeaemcloud.com](http://cdn.adobeaemcloud.com/) (CNAME-Eintrag) im DNS-Eintrag des DNS-Dienstanbieters zuzuordnen. Diese Zuordnung stellt sicher, dass in der benutzerdefinierten Domain empfangene Anfragen an das CDN von Adobe weitergeleitet werden.

   ![Dialogfeld „Live-Bereitschaft“](/help/assets/assets/go-live-readiness-dialogbox.png){width="500" align="center"}

1. Klicken Sie auf **[!UICONTROL OK]**, wird **[!UICONTROL STATUS]** auf **[!UICONTROL Verifiziert]**. Die benutzerdefinierte Domain kann jetzt in der Versand-URL verwendet werden.


   ![Konfigurieren von CDN](/help/assets/assets/cdn-configurations-varified.png)



<!--
### Onboard API keys {#onboarding-api-keys}

Create an API key to access [!DNL Dynamic Media] with OpenAPIs and the delivery tier backed Asset Selector.

#### Prepare yourself for API keys onboarding process {#prerequisites-for-onboarding-api-keys} 

To start the API keys onboarding process, ensure you have:

1. [Access to Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [Activated [!DNL Dynamic Media with OpenAPI] in your environment](#activate-dynamic-media-with-openapi).
1. [Access to the Adobe Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis#create-adobe-developer-console-adc-project).

#### Onboard the API keys using [!DNL AEM Dynamic Media] API card {#onboarding-api-keys-using-aem-dynamic-media-api-card}

Use the [Adobe Developer Console](https://developer.adobe.com/developer-console/) to onboard the API keys to:

1. [Access Dynamic Media APIs](#access-dynamic-media-apis)
1. [Access Delivery tier backed Asset Selector](#access-delivery-tier-backed-asset-selector)

#### Create an API key to access [!DNL Dynamic Media] with OpenAPIs {#access-dynamic-media-apis}

Execute the following steps to create an API key to access [!DNL Dynamic Media] with OpenAPIs:

1. Navigate to the **[!UICONTROL Admin Console]**. The Admin Console displays the **[!UICONTROL author]**, **[!UICONTROL delivery]** and **[!UICONTROL publish]** instances.
![instances on admin console](/help/assets/assets/delivery-instance-admin-console.png)
1. Select the **[!UICONTROL delivery]** instance to display the product profile with **[!UICONTROL AEM Dynamic Media enable API Services]** enabled by default. The product profile looks like this: **[!UICONTROL AEM Assets DM OpenAPI Users - delivery  - Program [ID Number] - Environment [ID Number]]**. 

   ![product profile on admin console](/help/assets/assets/admin-console-product-profile.png)

   >[!NOTE]
   >
   >This delivery instance is common for [!DNL Content Hub] and [!DNL Dynamic Media] with OpenAPI capabilities.

1. Navigate to the [Adobe Developer console](https://developer.adobe.com/console) and [create a new project](https://developer.adobe.com/dep/guides/dev-console/create-project/). See [Invoke OpenAPI-based AEM APIs for server to server authentication](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) to learn about creating a new project.
1. Select **[!UICONTROL AEM Dynamic Media API]** to access to the [!DNL Dynamic Media with OpenAPI capabilities] and click **[!UICONTROL Next]**.
![adobe developer console](/help/assets/assets/adobe-developer-console.png)
1. Select **[!UICONTROL Server-to-Server Authentication]** and click **[!UICONTROL Next]**. See [Server to Server authentication](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/) to learn more about this authentication type.
![server-to-server-authentication](/help/assets/assets/server-to-server-authentication.png)
1. Select **[!UICONTROL OAuth Server-to-Server]**, specify a unique **[!UICONTROL Credential name]** and click **[!UICONTROL Next]**.
![oauth server to server credential](/help/assets/assets/oauth-server-server-and-credential-name.png)
1. Select your product profile (mentioned in step 2) to access the APIs using the environment's delivery endpoint and click **[!UICONTROL Save configured API]**.
![select product profile](/help/assets/assets/select-product-profile.png)
1. Select **[!UICONTROL AEM Dynamic Media API]**. Use the **[!UICONTROL OAuth Server-to-Server]** to fetch the **X-API-key** and access the token for the **authorization** header. 
![oauth server to server](/help/assets/assets/oauth-server-to-server-credentials.png)
Execute the below steps to use [Dynamic Media with OpenAPIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) using the **[!UICONTROL OAuth Server-to-Server]** credentials. 
    1. Copy the **[!UICONTROL API KEY (Client ID)]** and replace the `X-Api-Key` in the cURL.
    1. Click **[!UICONTROL Generate access token]** to generate an access token and replace `YOUR_JWT_HERE` with the token in the cURL.

The cURL looks like this:
```
headers: {
    'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    `},
```
See [Search Assets API](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/search-assets-api#search-assets-api-header) for more information.

### Access Delivery tier backed Asset Selector {#access-delivery-tier-backed-asset-selector}

TBD: Wiki in progress.
-->

## [!DNL Dynamic Media] Prime aktivieren {#enable-dynamic-media-prime}

Führen Sie die folgenden Schritte in Ihrer Cloud Service-Umgebung aus, um [!DNL Dynamic Media] Prime zu aktivieren:

1. [Aktivieren von Dynamic Media mit OpenAPI](#activate-dynamic-media-with-openapi)
1. [Optional: Konfigurieren einer benutzerdefinierten Domain in der Bereitstellungsebene](#configure-custom-domain-in-delivery-tier)

<!--
1. [Onboard API keys using the AEM Dynamic Media API card](#onboarding-api-keys)
-->
