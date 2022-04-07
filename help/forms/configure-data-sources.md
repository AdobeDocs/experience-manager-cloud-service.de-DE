---
title: Konfigurieren von Data Sources
description: Mit der Experience Manager Forms-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herstellen. Erfahren Sie, wie Sie RESTful-Webservices, SOAP-basierte Webservices und OData-Services als Datenquellen konfigurieren und diese zum Erstellen von Formulardatenmodellen verwenden.
feature: Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: 7d3f553765580c1d81a80bea456e9df908939bc0
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 99%

---

# Konfigurieren von Datenquellen {#configure-data-sources}

![Datenintegration](do-not-localize/data-integeration.png)

Mit der [!DNL Experience Manager Forms]-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herstellen. Die folgenden Datenquellen werden standardmäßig unterstützt. Es ist jedoch möglich, mit nur wenigen Anpassungen auch andere Datenquellen zu integrieren.

<!-- * Relational databases - MySQL, [!DNL Microsoft SQL Server], [!DNL IBM DB2], and [!DNL Oracle RDBMS] 
* [!DNL Experience Manager] user profile  -->
* RESTful-Webservices
* SOAP-basierte Webservices
* OData-Services

Die Datenintegration unterstützt standardmäßig die Authentifizierungstypen OAuth2.0, Standardauthentifizierung sowie API-Schlüssel und ermöglicht die Implementierung benutzerdefinierter Authentifizierung für den Zugriff auf Webservices. RESTful-, SOAP-basierte und OData-Services werden in [!DNL Experience Manager] as a Cloud Service <!--, JDBC for relational databases --> konfiguriert und Connectoren für [!DNL Experience Manager]-Benutzerprofile werden in der [!DNL Experience Manager]-Web-Konsole konfiguriert.

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] unterstützt keine relationalen Datenbanken.

<!-- ## Configure relational database {#configure-relational-database}

You can configure relational databases using [!DNL Experience Manager] Web Console Configuration. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://server:host/system/console/configMgr`.
1. Look for **[!UICONTROL Apache Sling Connection Pooled DataSource]** configuration. Tap to open the configuration in edit mode.
1. In the configuration dialog, specify the details for the database you want to configure, such as:

    * Name of the data source
    * Data source service property that stores the data source name
    * Java class name for the JDBC driver
    * JDBC connection URI
    * Username and password to establish connection with the JDBC driver

   >[!NOTE]
   >
   >Ensure that you encrypt sensitive information like passwords before configuring the data source. To encrypt:
   >
   >    
   >    
   >    1. Go to https://'[server]:[port]'/system/console/crypto.
   >    1. In the **[!UICONTROL Plain Text]** field, specify the password or any string to encrypt and tap **[!UICONTROL Protect]**.
   >    
   >    
   >    
   >The encrypted text appears in the Protected Text field that you can specify in the configuration.

1. Enable **[!UICONTROL Test on Borrow]** or **[!UICONTROL Test on Return]** to specify that the objects are validated before being borrowed or returned from and to the pool, respectively.
1. Specify a SQL SELECT query in the **[!UICONTROL Validation Query]** field to validate connections from the pool. The query must return at least one row. Based on your database, specify one of the following:

    * SELECT 1 (MySQL and MS SQL) 
    * SELECT 1 from dual (Oracle)

1. Tap **[!UICONTROL Save]** to save the configuration. -->

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and tap to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties will be available for use in form data model. Use the following format to specify user profile properties:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Examples:

    * `name=profile/phoneNumber,type=string`
    * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The **&#42;** in the above example denotes all nodes under the `profile/empLocation/` node in [!DNL Experience Manager] user profile in CRXDE structure. It means that the Form Data Model can access the `city` property of type `string` present in any node under the `profile/empLocation/` node. However, the nodes that contain the specified property must follow a consistent structure.

1. Tap **[!UICONTROL Save]** to save the configuration. -->

## Einstellen des Ordners für Cloud-Service-Konfigurationen {#cloud-folder}

Die Konfiguration des Cloud Services-Ordners ist erforderlich, um Cloud Services für RESTful-, SOAP- und OData-Services zu konfigurieren.

Alle Cloud Service-Konfigurationen in [!DNL Experience Manager] sind im Ordner `/conf` im [!DNL Experience Manager]-Repository zusammengefasst. Standardmäßig enthält der Ordner `conf` den Ordner `global`, in dem Sie Cloud Service-Konfigurationen erstellen können. Sie müssen ihn jedoch manuell für Cloud-Konfigurationen aktivieren. Sie können auch zusätzliche Ordner in `conf` erstellen, um Cloud Service-Konfigurationen zu erstellen und zu organisieren.

Konfigurieren des Ordners für Cloud Service-Konfigurationen:

1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html?lang=de).
1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.

   1. Wählen Sie im **[!UICONTROL Konfigurationsbrowser]** den Ordner `global` aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.

   1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.

   1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Tippen Sie im **[!UICONTROL Konfigurationsbrowser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den für Cloud Service-Konfigurationen aktivierten Ordner zu erstellen.

## Konfigurieren von RESTful-Webservices {#configure-restful-web-services}

Der RESTful-Webservice kann mithilfe von [Swagger-Spezifikationen](https://swagger.io/specification/) im JSON- oder YAML-Format in einer [!DNL Swagger]-Definitionsdatei beschrieben werden. Um den RESTful-Webservice in [!DNL Experience Manager] as a Cloud Service zu konfigurieren, benötigen Sie entweder die [!DNL Swagger]-Datei auf Ihrem System oder die URL, wo die Datei gehostet wird.

Gehen Sie wie folgt vor, um RESTful-Services zu konfigurieren:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den RESTful-Service an:

   * Wählen Sie „URL“ oder „Datei“ aus der Dropdown-Liste [!UICONTROL Swagger-Quelle] aus und geben Sie dementsprechend die [!DNL Swagger URL] zur [!DNL  Swagger]-Definitionsdatei an oder laden Sie die [!DNL Swagger]-Datei aus Ihrem lokalen Dateisystem hoch.
   * Auf Grundlage der Eingabe der [!DNL  Swagger]-Quelle werden folgende Felder mit Werten vorbefüllt:

      * Schema: Die von der REST-API verwendeten Übertragungsprotokolle. Die Anzahl der in der Dropdown-Liste angezeigten Schematypen hängt von den Schemas ab, die in der [!DNL Swagger]-Quelle definiert wurden.
      * Host: Der Domain-Name oder die IP-Adresse des Hosts, der die REST-API bereitstellt. Dies ist ein Pflichtfeld.
      * Basispfad: Das URL-Präfix für alle API-Pfade. Dies ist ein optionales Feld.\
         Bearbeiten Sie bei Bedarf die vorbefüllten Werte für diese Felder.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0, Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den RESTful-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Service zu erstellen.

## SOAP-Webservices konfigurieren {#configure-soap-web-services}

SOAP-basierte Webservices werden mithilfe von [WSDL-Spezifikationen (Web Services Description Language)](https://www.w3.org/TR/wsdl) beschrieben. [!DNL Experience Manager Forms] unterstützt das WSDL-Modell im RPC-Stil nicht.

Um den SOAP-basierten Webservice in [!DNL Experience Manager] as a Cloud Service zu konfigurieren, benötigen Sie die WSDL-URL für den Webservice. Gehen Sie dann wie folgt vor:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL SOAP-Webservice]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie Folgendes für den SOAP-Webservice an:

   * WSDL-URL für den Webservice.
   * Service-Endpunkt. Geben Sie in diesem Feld einen Wert ein, um den in WSDL erwähnten Service-Endpunkt zu überschreiben.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0, Standardauthentifizierung oder benutzerdefinierte Authentifizierung – für den Zugriff auf den SOAP-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

      <!--If you select **[!UICONTROL X509 Token]** as the Authentication type, configure the X509 certificate. For more information, see [Set up certificates](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).-->
      <!--Specify the KeyStore alias for the X509 certificate in the **[!UICONTROL Key Alias]** field. Specify the time, in seconds, until the authentication request remains valid, in the **[!UICONTROL Time To Live]** field. Optionally, select to sign the message body or timestamp header or both.-->

      <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den SOAP-Webservice zu erstellen.

### Aktivieren der Verwendung von Importanweisungen in SOAP-Webservices WSDL {#enable-import-statements}

Sie können einen regulären Ausdruck angeben, der als Filter für absolute URLs dient, die als Importanweisungen in SOAP-Webservices WSDL zulässig sind. Standardmäßig ist in diesem Feld kein Wert vorhanden. [!DNL Experience Manager] blockiert daher alle in WSDL verfügbaren Importanweisungen. Wenn Sie `.*` als Wert in diesem Feld angeben, lässt [!DNL Experience Manager] alle Importanweisungen zu.

Legen Sie die `importAllowlistPattern`-Eigenschaft der Konfiguration **[!UICONTROL Formulardatenmodell Importzulassungsliste für SOAP-Webservices]** fest, um den regulären Ausdruck anzugeben. Folgende JSON-Datei zeigt ein Beispiel:

```json
{
  "importAllowlistPattern": ".*"
}
```

Um Konfigurationswerte festzulegen, [generieren Sie OSGi-Konfigurationen mit dem AEM-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und [stellen Sie die Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) in Ihrer Cloud Service-Instanz bereit.

## Konfigurieren von OData-Services {#config-odata}

Ein OData-Service wird anhand seiner Service-Stamm-URL identifiziert. Um einen OData-Service in [!DNL Experience Manager] as a Cloud Service zu konfigurieren, müssen Sie sicherstellen, dass Sie über die Service-Stamm-URL für den Service verfügen. Gehen Sie dann wie folgt vor:

>[!NOTE]
>
> Formulardatenmodell unterstützt [OData Version 4](https://www.odata.org/documentation/).
>Eine schrittweise Anleitung zum Konfigurieren von [!DNL Microsoft Dynamics 365], online oder On-Premise, finden Sie unter [[!DNL Microsoft Dynamics] OData-Konfiguration](ms-dynamics-odata-configuration.md).

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL OData-Service]** aus der **[!UICONTROL Dropdown-Liste „Service-Typ“]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den OData-Service an:

   * Service-Stamm-URL für den zu konfigurierenden OData-Service.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0, Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den OData-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   >[!NOTE]
   >
   >Sie müssen den OAuth 2.0-Authentifizierungstyp auswählen, um eine Verbindung mit [!DNL Microsoft Dynamics]-Services herzustellen, die den OData-Endpunkt als Service-Stamm nutzen.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den OData-Service zu erstellen.

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model, both the data source and [!DNL Experience Manager] Server running Form Data Model authenticate each other’s identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and tap **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and tap **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, tap **[!UICONTROL Select Certificate File]**, upload the certificate, and tap **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## Nächste Schritte {#next-steps}

Sie haben die Datenquellen konfiguriert. Als Nächstes können Sie ein Formulardatenmodell erstellen oder, falls Sie bereits ein Formulardatenmodell ohne Datenquelle erstellt haben, können Sie es den soeben konfigurierten Datenquellen zuordnen. Weitere Informationen finden Sie unter [Erstellen eines Formulardatenmodells](create-form-data-models.md).
