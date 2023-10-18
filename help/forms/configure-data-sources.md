---
title: Konfigurieren von Data Sources
description: Erfahren Sie, wie Sie RESTful-Webdienste, SOAP-basierte Webdienste und OData-Dienste als Datenquellen für ein Formulardatenmodell konfigurieren.
feature: Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: 0f8aed76af4d2640094a76f2805f73a0a619e33f
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 87%

---


# Konfigurieren von Datenquellen {#configure-data-sources}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/configure-data-sources.html) |
| AEM as a Cloud Service | Dieser Artikel |

![Datenintegration](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] Mit der Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und eine Verbindung zu ihnen herstellen. Die folgenden Datenquellen werden standardmäßig unterstützt:

* Relationale Datenbanken – MySQL, [!DNL Microsoft® SQL Server], [!DNL IBM® DB2®] und [!DNL Oracle RDBMS]
* RESTful-Webservices
* SOAP-basierte Webservices
* OData-Services   (Version 4.0)
* Microsoft® Dynamics
* SalesForce
* Microsoft® Azure Blob-Speicher

Die Datenintegration unterstützt standardmäßig die Authentifizierungstypen OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung sowie API-Schlüssel und ermöglicht die Implementierung benutzerdefinierter Authentifizierung für den Zugriff auf Web-Services. Während RESTful-, SOAP-basierte und OData-Dienste in [!DNL Experience Manager] as a Cloud Service konfiguriert werden, werden JDBC für relationale Datenbanken und der Connector für [!DNL Experience Manager]-Benutzerprofile in der [!DNL Experience Manager]-Web-Konsole konfiguriert.

## Konfigurieren relationaler Datenbanken {#configure-relational-database}

### Voraussetzungen

Bevor Sie relationale Datenbanken mit [!DNL Experience Manager] Web-Konsolenkonfiguration konfigurieren, müssen Sie Folgendes tun:
* [Erweiterte Vernetzung über die Cloud Manager-API aktivieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=de), da die Ports standardmäßig deaktiviert sind.
* [Hinzufügen von JDBC-Treiberabhängigkeiten in Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html?lang=de#mysql-driver-dependencies).


### Schritte zum Konfigurieren einer relationalen Datenbank

Sie können relationale Datenbanken mithilfe der [!DNL Experience Manager] Web-Konsolenkonfiguration konfigurieren. Gehen Sie folgendermaßen vor:

1. Gehen Sie zur [!DNL Experience Manager] Web-Konsole unter `https://server:host/system/console/configMgr`.
1. Suchen Sie die Konfiguration **[!UICONTROL Day Commons JDBC Connections Pools]**. Tippen Sie, um die Konfiguration im Bearbeitungsmodus zu öffnen.

   ![JDBC-Verbindungs-Pool](/help/forms/assets/jdbc_connector.png)

1. Geben Sie im Konfigurationsdialogfeld die Details für die Datenbank an, die Sie konfigurieren möchten, z. B.:

   * Klassenname von Java™ für den JDBC-Treiber
   * JDBC-Verbindungs-URI
   * Benutzername und Passwort zum Herstellen der Verbindung mit dem JDBC-Treiber
   * Geben Sie eine SQL SELECT-Abfrage im Feld **[!UICONTROL Überprüfungsabfrage]** ein, um Verbindungen aus dem Pool zu validieren. Die Abfrage muss mindestens eine Zeile zurückgeben. Legen Sie je nach Datenbank eine der folgenden Optionen fest:
      * SELECT 1 (MySQL und MS® SQL)
      * SELECT 1 from dual (Oracle)
   * Name der Datenquelle

   Beispielzeichenfolgen zum Konfigurieren einer relationalen Datenbank:

   ```text
      "datasource.name": "sqldatasourcename-mysql",
      "jdbc.driver.class": "com.mysql.jdbc.Driver",
      "jdbc.connection.uri": "jdbc:mysql://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30001/sqldatasourcename"
   ```

   >[!NOTE]
   >
   > Weitere Informationen finden Sie unter [SQL-Verbindungen mit JDBC DataSourcePool](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html?lang=de).

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

Jetzt können Sie die konfigurierte relationale Datenbank mit Ihrem Formulardatenmodell verwenden.

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and tap to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties are available for use in form data model. Use the following format to specify user profile properties:

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

RESTful-Webdienste können mithilfe von [Swagger-Spezifikationen](https://swagger.io/specification/v2/) im JSON- oder YAML-Format in einer [!DNL Swagger] Definitionsdatei. Um den RESTful-Webservice in [!DNL Experience Manager] as a Cloud Service zu konfigurieren, benötigen Sie entweder die [!DNL Swagger]-Datei ([Swagger Version 2.0](https://swagger.io/specification/v2/)) oder [!DNL Swagger]-Datei ([Swagger Version 3.0](https://swagger.io/specification/v3/)) auf Ihrem Dateisystem oder die URL, unter der die Datei gehostet wird.

### Konfigurieren von RESTful-Services für Open API Spezifikation Version 2.0 {#configure-restful-services-open-api-2.0}

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den RESTful-Service an:

   * Wählen Sie eine URL oder Datei aus dem [!UICONTROL Swagger Source] und geben Sie dementsprechend die [!DNL Swagger URL] der[!DNL  Swagger] Definitionsdatei oder laden Sie die [!DNL Swagger] -Datei aus Ihrem lokalen Dateisystem.
   * Auf der Grundlage der [!DNL  Swagger] Quelleingabe, werden die folgenden Felder mit Werten vorausgefüllt:

      * Schema: Die von der REST-API verwendeten Übertragungsprotokolle. Die Anzahl der in der Dropdown-Liste angezeigten Schematypen hängt von den Schemas ab, die in der [!DNL Swagger]-Quelle definiert wurden.
      * Host: Der Domain-Name oder die IP-Adresse des Hosts, der die REST-API bereitstellt. Dies ist ein Pflichtfeld.
      * Basispfad: Das URL-Präfix für alle API-Pfade. Dies ist ein optionales Feld.\
        Bearbeiten Sie bei Bedarf die vorbefüllten Werte für diese Felder.

   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den RESTful-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Service zu erstellen.

### Konfigurieren von RESTful-Services für Open API Spezifikation Version 3.0 {#configure-restful-services-open-api-3.0}

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den RESTful-Service an:

   * Wählen Sie eine URL oder Datei aus dem [!UICONTROL Swagger Source] und geben Sie dementsprechend die [!DNL Swagger 3.0 URL] der[!DNL  Swagger] Definitionsdatei oder laden Sie die [!DNL Swagger] -Datei aus Ihrem lokalen Dateisystem.
   * Basierend auf den [!DNL  Swagger] Quelleingabe, werden die Verbindungsinformationen zum Zielserver angezeigt.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den RESTful-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Service zu erstellen.

Einige der von RESTful Services Open API Specifikation Version 3.0 nicht unterstützten Vorgänge sind:
* Rückrufe
* oneof/anyof
* Remote-Referenz
* Links
* Verschiedene Anfrageinstanzen für verschiedene MIME-Typen für einen einzelnen Vorgang

Weitere Informationen finden Sie unter [OpenAPI 3.0-Spezifikation](https://swagger.io/specification/v3/).

### HTTP-Client-Konfiguration des Formulardatenmodells zur Leistungsoptimierung {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] bei der Integration mit RESTful-Webdiensten ein Datenmodell erstellen, da die Datenquelle HTTP-Client-Konfigurationen zur Leistungsoptimierung enthält.

Legen Sie die folgenden Eigenschaften der Konfiguration für das **[!UICONTROL Formulardatenmodell HTTP-Client-Konfiguration für REST-Datenquelle]** zum Angeben des regulären Ausdrucks fest:

* Verwenden Sie die `http.connection.max.per.route`-Eigenschaft zum Festlegen der maximal zulässigen Anzahl von Verbindungen zwischen dem Formulardatenmodell und RESTful-Webservices. Der Standardwert ist 20 Verbindungen.

* Verwenden Sie die `http.connection.max`-Eigenschaft, um die maximale Anzahl zulässiger Verbindungen für jede Route anzugeben. Der Standardwert ist 40 Verbindungen.

* Verwenden Sie die `http.connection.keep.alive.duration`-Eigenschaft, um die Dauer anzugeben, für die eine persistente HTTP-Verbindung aktiv gehalten wird. Der Standardwert ist 15 Sekunden.

* Verwenden Sie die `http.connection.timeout`-Eigenschaft, um die Dauer anzugeben, für die der [!DNL Experience Manager Forms]-Server auf die Einrichtung einer Verbindung wartet. Der Standardwert ist 10 Sekunden.

* Verwenden Sie die `http.socket.timeout`-Eigenschaft zum Angeben des maximalen Zeitraums für Inaktivität zwischen zwei Datenpaketen. Der Standardwert ist 30 Sekunden.

Folgende JSON-Datei zeigt ein Beispiel:


```json
{   
   "http.connection.keep.alive.duration":"15",   
   "http.connection.max.per.route":"20",   
   "http.connection.timeout":"10",   
   "http.socket.timeout":"30",   
   "http.connection.idle.connection.timeout":"15",   
   "http.connection.max":"40" 
} 
```

1. Tippen Sie auf **[!UICONTROL Formulardatenmodell HTTP-Client-Konfiguration für REST-Datenquelle]**.

1. Führen Sie im Dialog [!UICONTROL Formular-Datenmodell HTTP-Client-Konfiguration für REST-Datenquelle] folgende Schritte aus:

   * Geben Sie die maximal zulässige Anzahl von Verbindungen zwischen dem Formulardatenmodell und RESTful-Webservices im Feld **[!UICONTROL Verbindungslimit insgesamt]** an. Der Standardwert ist 20 Verbindungen.

   * Geben Sie die maximal zulässige Anzahl von Verbindungen für jede Route im Feld **[!UICONTROL Verbindungslimit pro Route]** an. Der Standardwert ist zwei Verbindungen.

   * Geben Sie die Dauer, für die eine persistente HTTP-Verbindung aufrechterhalten wird, im Feld **[!UICONTROL Aufrechterhalten]** an. Der Standardwert ist 15 Sekunden.

   * Geben Sie im Feld **[!UICONTROL Verbindungs-Zeitüberschreitung]** die Dauer an, für die der [!DNL Experience Manager Forms]-Server auf eine Verbindung wartet. Der Standardwert ist 10 Sekunden.

   * Geben Sie im Feld **[!UICONTROL Socket-Zeitüberschreitung]** den maximalen Zeitraum für die Inaktivität zwischen zwei Datenpaketen an. Der Standardwert ist 30 Sekunden.

## SOAP-Webservices konfigurieren {#configure-soap-web-services}

SOAP-basierte Webservices werden mithilfe von [WSDL-Spezifikationen (Web Services Description Language)](https://www.w3.org/TR/wsdl) beschrieben. [!DNL Experience Manager Forms] unterstützen das WSDL-Modell im RPC-Stil nicht.

Um den SOAP-basierten Webservice in [!DNL Experience Manager] as a Cloud Service zu konfigurieren, benötigen Sie die WSDL-URL für den Webservice. Gehen Sie dann wie folgt vor:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL SOAP-Webservice]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie Folgendes für den SOAP-Webservice an:

   * WSDL-URL für den Webservice.
   * Service-Endpunkt. Geben Sie in diesem Feld einen Wert ein, um den in WSDL erwähnten Service-Endpunkt zu überschreiben.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung oder benutzerdefinierte Authentifizierung – für den Zugriff auf den SOAP-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

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
> Das Formulardatenmodell unterstützt [OData Version 4](https://www.odata.org/documentation/).
>Eine schrittweise Anleitung zum Konfigurieren von [!DNL Microsoft®® Dynamics 365], online oder vor Ort, siehe [[!DNL Microsoft® Dynamics] OData-Konfiguration](ms-dynamics-odata-configuration.md).

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tippen Sie, um den Ordner auszuwählen, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](#cloud-folder).

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten für das Erstellen von Datenquellkonfigurationen]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL OData-Service]** aus der **[!UICONTROL Dropdown-Liste „Service-Typ“]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und tippen Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den OData-Service an:

   * Service-Stamm-URL für den zu konfigurierenden OData-Service.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den OData-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   >[!NOTE]
   >
   Sie müssen den OAuth 2.0-Authentifizierungstyp auswählen, mit dem eine Verbindung hergestellt werden soll [!DNL Microsoft®® Dynamics] Dienste, die den OData-Endpunkt als Dienststamm verwenden.

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den OData-Service zu erstellen.

## Microsoft® SharePoint-Liste konfigurieren {#config-sharepoint-list}

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unsere [Pre-Release-Kanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

Verwenden Sie zum Speichern von Daten in Tabellenform die Microsoft® SharePoint-Liste. So konfigurieren Sie eine Microsoft SharePoint-Liste in [!DNL Experience Manager] Gehen Sie as a Cloud Service wie folgt vor:

1. Navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Service]** >  **[!UICONTROL Microsoft® SharePoint]**.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicks **[!UICONTROL Erstellen]** > **[!UICONTROL SharePoint-Liste]** aus der Dropdown-Liste. Der SharePoint-Konfigurationsassistent wird angezeigt.
1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Client-Geheimnis]** und **[!UICONTROL OAuth-URL]** an. Informationen zum Abrufen der Client-ID, des Client-Geheimnisses und der Mandanten-ID für die OAuth-URL finden Sie in der [Dokumentation von Microsoft®](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).
   * Sie können die `Client ID` und das `Client Secret` Ihrer App über das Microsoft® Azure-Portal abrufen.
   * Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` mit der URL Ihrer Autoreninstanz.
   * API-Berechtigungen hinzufügen `offline_access` und `Sites.Manage.All` im **Microsoft® Diagramm** Registerkarte, um Lese-/Schreibberechtigungen bereitzustellen. Hinzufügen `AllSites.Manage` -Berechtigung in der **Sharepoint** -Tab, um remote mit SharePoint-Daten zu interagieren.
   * Verwenden der OAuth-URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

     >[!NOTE]
     >
     Ob das Feld **Client-Geheimnis** obligatorisch oder optional ist, hängt von der Konfiguration Ihrer Azure Active Directory-Anwendung ab. Wenn Ihre Anwendung so konfiguriert ist, dass sie ein Client-Geheimnis verwendet, ist die Angabe des Client-Geheimnisses obligatorisch.

1. Klicken Sie auf **[!UICONTROL Verbinden]**. Bei erfolgreicher Verbindung erscheint die Meldung `Connection Successful`.
1. Auswählen **[!UICONTROL SharePoint-Site]** und **[!UICONTROL SharePoint-Liste]** aus der Dropdown-Liste.
1. Tippen **[!UICONTROL Erstellen]** , um die Cloud-Konfiguration für die Microsoft® SharePointList zu erstellen.

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model, both the data source and [!DNL Experience Manager] Server running Form Data Model authenticate each other's identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and tap **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and tap **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, tap **[!UICONTROL Select Certificate File]**, upload the certificate, and tap **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## Nächste Schritte {#next-steps}

Sie haben die Datenquellen konfiguriert. Als Nächstes können Sie ein Formulardatenmodell erstellen oder, falls Sie bereits ein Formulardatenmodell ohne eine Datenquelle erstellt haben, können Sie es den schon konfigurierten Datenquellen zuordnen. Weitere Informationen finden Sie unter [Erstellen eines Formulardatenmodells](create-form-data-models.md).


<!--

>[!MORELIKETHIS]
>
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)
>*  [Add Forms Portal to an AEM Sites page](/help/forms/configure-forms-portal.md)

-->