---
title: Wie werden Datenquellen konfiguriert?
description: Erfahren Sie, wie Sie RESTful-Web-Dienste, SOAP-basierte Web-Dienste und OData-Dienste als Datenquellen konfigurieren und diese zum Erstellen von Formulardatenmodellen (FDM) verwenden.
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: f913871da16b44d7a465e0fa00608835524ba7e3
workflow-type: tm+mt
source-wordcount: '2384'
ht-degree: 94%

---


# Konfigurieren von Datenquellen {#configure-data-sources}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/configure-data-sources.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

![Datenintegration](do-not-localize/data-integeration.png)

Mit der [!DNL Experience Manager Forms]-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herstellen. Die folgenden Datenquellen werden standardmäßig unterstützt:

* Relationale Datenbanken - MySQL, [!DNL Microsoft® SQL Server], [!DNL IBM® DB2®], PostgreSQL, Azure SQL und [!DNL Oracle RDBMS]
* RESTful-Webservices
* SOAP-basierte Webservices
* OData-Dienste (Version 4.0)
* Microsoft® Dynamics
* SalesForce
* Microsoft® Azure Blob-Speicher

Die Datenintegration unterstützt standardmäßig die Authentifizierungstypen OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung sowie API-Schlüssel und ermöglicht die Implementierung benutzerdefinierter Authentifizierung für den Zugriff auf Web-Services. Während RESTful-, SOAP-basierte und OData-Dienste in [!DNL Experience Manager] as a Cloud Service konfiguriert werden, werden JDBC für relationale Datenbanken und der Connector für [!DNL Experience Manager]-Benutzerprofile in der [!DNL Experience Manager]-Web-Konsole konfiguriert.

## Konfigurieren relationaler Datenbanken {#configure-relational-database}

### Voraussetzungen

Bevor Sie relationale Datenbanken mit [!DNL Experience Manager] Web-Konsolenkonfiguration konfigurieren, müssen Sie Folgendes tun:

* [Aktivieren Sie erweiterte Netzwerkfunktionen über die Cloud Manager-API](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=de), da die Ports standardmäßig deaktiviert sind.
* [Hinzufügen von JDBC-Treiberabhängigkeiten in Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html?lang=de#mysql-driver-dependencies).


### Schritte zum Konfigurieren einer relationalen Datenbank

Sie können relationale Datenbanken mithilfe der [!DNL Experience Manager] Web-Konsolenkonfiguration konfigurieren. Gehen Sie folgendermaßen vor:

**Schritt 1: Klonen Sie das AEM as a Cloud Service-Git-Repository**

1. Öffnen Sie die Befehlszeile und wählen Sie einen Ordner zum Speichern des AEM as a Cloud Service-Repositorys aus, z. B. `/cloud-service-repository/`.

2. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```

   **Wo finden Sie diese Informationen?**

   Eine schrittweise Anleitung zum Auffinden dieser Details finden Sie im Adobe Experience League-Artikel [Zugriff auf Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).

   Wenn der Befehl erfolgreich abgeschlossen wurde, wird in Ihrem lokalen Verzeichnis ein neuer Ordner erstellt. Dieser Ordner ist nach Ihrer Anwendung benannt.

**Schritt 2: Navigieren Sie zum Konfigurationsordner**

1. Öffnen Sie den Repository-Ordner in einem Editor.

1. Navigieren Sie zum folgenden Verzeichnis in Ihrem `<application folder>`, in dem die OSGi-Konfiguration für den JDBC-Pool platziert werden soll:

   ```bash
   cd ui.config/src/jcr_root/apps/<application folder>/osgiconfig/config/
   ```

**Schritt 3: Erstellen Sie die MySQL-Verbindungskonfigurationsdatei**

1. Erstellen Sie die Datei :

   ```bash
   com.day.commons.datasource.jdbcpool.JdbcPoolService~<application folder>-mysql.cfg.json
   ```

1. Fügen Sie die folgenden Codezeilen hinzu:

```json
{
  "jdbc.driver.class": "com.mysql.cj.jdbc.Driver",
  "jdbc.connection.uri": "jdbc:mysql://<hostname>:<port>/<database>?useSSL=false",
  "jdbc.username": "<your-db-username>",
  "jdbc.password": "<your-db-password>",
  "datasource.name": "<application folder>-mysql",
  "datasource.svc.prop.name": "<application folder>-mysql"
}
```

> 
>
> Ersetzen Sie Platzhalter wie `<application folder>`, `<hostname>`, `<database>`, `<your-db-username>` und `<your-db-password>` durch tatsächliche Werte.

**Schritt 4: Übergeben und Übertragen der Änderungen**

Öffnen Sie das Terminal und führen Sie die folgenden Befehle aus:

```bash
git add .
git commit -m "<commit message>"
git push 
```

**Schritt 5: Bereitstellen der Änderungen über die Cloud Manager-Pipeline**

1. Anmelden bei **AEM Cloud Manager**.
1. Navigieren Sie zu Ihrem Projekt und führen Sie die Pipeline aus , um die Änderungen bereitzustellen.

>[!NOTE]
>
> Weitere Informationen finden Sie unter [SQL-Verbindungen mit JDBC DataSourcePool](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html?lang=de).

<!--
1. Go to [!DNL Experience Manager] web console at `https://server:host/system/console/configMgr`.
2. Locate **[!UICONTROL Day Commons JDBC Connections Pools]** configuration. Select to open the configuration in edit mode.

   ![JDBC Connector Pool](/help/forms/assets/jdbc_connector.png)

3. In the configuration dialog, specify the details for the database you want to configure, such as:

    * Java&trade; class name for the JDBC driver
    * JDBC connection URI
    * Username and password to establish connection with the JDBC driver
    * Specify a SQL SELECT query in the **[!UICONTROL Validation Query]** field to validate connections from the pool. The query must return at least one row. Based on your database, specify one of the following:
      * SELECT 1 (MySQL and MS&reg; SQL) 
      * SELECT 1 from dual (Oracle)
    * Name of the data source

   Sample strings for configuring a relational database:

   ```text
      "datasource.name": "sqldatasourcename-mysql",
      "jdbc.driver.class": "com.mysql.jdbc.Driver",
      "jdbc.connection.uri": "jdbc:mysql://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30001/sqldatasourcename"
   ```


    
4. Select **[!UICONTROL Save]** to save the configuration.

Now, you can use the configured relational database with your Form Data Model (FDM). 

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and select to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties are available for use in form data model (FDM). Use the following format to specify user profile properties:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Examples:

    * `name=profile/phoneNumber,type=string`
    * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The **&#42;** in the above example denotes all nodes under the `profile/empLocation/` node in [!DNL Experience Manager] user profile in CRXDE structure. It means that the Form Data Model (FDM) can access the `city` property of type `string` present in any node under the `profile/empLocation/` node. However, the nodes that contain the specified property must follow a consistent structure.

1. Select **[!UICONTROL Save]** to save the configuration. -->

## Einstellen des Ordners für Cloud-Service-Konfigurationen {#cloud-folder}

Die Konfiguration des Cloud-Services-Ordners ist erforderlich, um Cloud-Services für RESTful-, SOAP- und OData-Services zu konfigurieren.

Alle Cloud-Service-Konfigurationen in [!DNL Experience Manager] sind im Ordner `/conf` im [!DNL Experience Manager]-Repository zusammengefasst. Standardmäßig enthält der Ordner `conf` den Ordner `global`, in dem Sie Cloud-Service-Konfigurationen erstellen können. Sie müssen ihn jedoch manuell für Cloud-Konfigurationen aktivieren. Sie können auch zusätzliche Ordner in `conf` erstellen, um Cloud-Service-Konfigurationen zu erstellen und zu organisieren.

Konfigurieren des Ordners für Cloud-Service-Konfigurationen:

1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html?lang=de).
1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloud-Konfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud-Service-Konfigurationen zu erstellen und zu konfigurieren.

   1. Wählen Sie im **[!UICONTROL Konfigurations-Browser]** den Ordner `global` aus und wählen Sie **[!UICONTROL Eigenschaften]**.

   1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.

   1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Wählen Sie im **[!UICONTROL Konfigurations-Browser]** die Option **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**.
1. Wählen Sie **[!UICONTROL Erstellen]**, um den für Cloud-Service-Konfigurationen aktivierten Ordner zu erstellen.

## Konfigurieren von RESTful-Webservices {#configure-restful-web-services}

RESTful-Webservices können mithilfe von [Swagger-Spezifikationen](https://swagger.io/specification/v2/) im JSON- oder YAML-Format in einer [!DNL Swagger]-Definitionsdatei oder einem Dienstendpunkt beschrieben werden.

>[!NOTE]
> Um den RESTful-Webservice in [!DNL Experience Manager] as a Cloud Service zu konfigurieren, benötigen Sie entweder die [!DNL Swagger]-Datei ([Swagger Version 2.0](https://swagger.io/specification/v2/)) oder [!DNL Swagger]-Datei ([Swagger Version 3.0](https://swagger.io/specification/v3/)) auf Ihrem Dateisystem oder die URL, unter der die Datei gehostet wird.

### Konfigurieren von RESTful-Services für Open API Spezifikation Version 2.0 {#configure-restful-services-open-api-2.0}

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Datenquellen]**. Wählen Sie den Ordner aus, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud-Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Wählen Sie **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten zum Erstellen der Datenquellenkonfiguration]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und wählen Sie **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den RESTful-Service an:

   * Wählen Sie eine URL oder Datei aus der Dropdown-Liste [!UICONTROL Swagger-Quelle] aus und geben Sie dementsprechend die [!DNL Swagger URL] zur [!DNL &#x200B; Swagger]-Definitionsdatei an oder laden Sie die [!DNL Swagger]-Datei aus Ihrem lokalen Dateisystem hoch.
   * Auf der Grundlage der [!DNL &#x200B; Swagger] Quelleingabe, werden die folgenden Felder mit Werten vorausgefüllt:

      * Schema: Die von der REST-API verwendeten Übertragungsprotokolle. Die Anzahl der in der Dropdown-Liste angezeigten Schematypen hängt von den Schemas ab, die in der [!DNL Swagger]-Quelle definiert wurden.
      * Host: Der Domain-Name oder die IP-Adresse des Hosts, der die REST-API bereitstellt. Dies ist ein Pflichtfeld.
      * Basispfad: Das URL-Präfix für alle API-Pfade. Dies ist ein optionales Feld.\
        Bearbeiten Sie bei Bedarf die vorbefüllten Werte für diese Felder.

   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den RESTful-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Wählen Sie **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Service zu erstellen.

### Konfigurieren von RESTful-Services für Open API Spezifikation Version 3.0 {#configure-restful-services-open-api-3.0}

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Datenquellen]**. Wählen Sie den Ordner aus, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud-Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Wählen Sie **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten zum Erstellen der Datenquellenkonfiguration]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und wählen Sie **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den RESTful-Service an:

   * Wählen Sie eine URL oder Datei aus der Dropdown-Liste [!UICONTROL Swagger-Quelle] aus und geben Sie dementsprechend die [!DNL Swagger 3.0 URL] zur [!DNL &#x200B; Swagger]-Definitionsdatei an oder laden Sie die [!DNL Swagger]-Datei aus Ihrem lokalen Dateisystem hoch.
   * Basierend auf der [!DNL &#x200B; Swagger]-Quelleingabe werden die Verbindungsinformationen zum Ziel-Server angezeigt.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den RESTful-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Wählen Sie **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den RESTful-Service zu erstellen.

Einige der von RESTful Services Open API Specifikation Version 3.0 nicht unterstützten Vorgänge sind:

* Rückrufe
* oneof/anyof
* Remote-Referenz
* Links
* Verschiedene Anfrageinstanzen für verschiedene MIME-Typen für einen einzelnen Vorgang

Weitere Informationen finden Sie unter [OpenAPI 3.0-Spezifikation](https://swagger.io/specification/v3/).

### Konfigurieren von RESTful-Diensten mithilfe des Dienstendpunkts {#configure-restful-services-service-endpoint}

<span class="preview"> Die Funktion „Dienstendpunkt“ ist im Rahmen des Early-Adopter-Programms verfügbar und gilt nur für Kernkomponenten. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Datenquellen]**. Wählen Sie den Ordner aus, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud-Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Wählen Sie **[!UICONTROL Erstellen]** aus, um den Assistenten **[!UICONTROL Datenquellkonfiguration erstellen]** zu öffnen.

1. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL RESTful-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und wählen Sie **[!UICONTROL Weiter]**.

1. Wählen Sie auf der nächsten Seite aus der Dropdwon-Liste **[!UICONTROL RESTful-Dienst]** die Option **[!UICONTROL Dienstendpunkt]** aus.

   ![Dienstendpunkt](/help/forms/assets/select-service-endpoint.png)

1. Geben Sie die **[!UICONTROL Dienstendpunkt-URL]** an.

   >[!NOTE]
   > Standardmäßig ist „Methodentyp“ auf „POST“ eingestellt.
1. Wählen Sie einen gewünschten Inhaltstyp aus der Dropdown-Liste aus. Inhaltstypen sind mehrteilige Formulardaten, JSON und URL-kodiert (Schlüssel-Wert-Paar).
1. Wählen Sie nun einen Authentifizierungstyp, z. B. „OAuth 2.0“, „Einfache Authentifizierung“, „API-Schlüssel“, „Benutzerdefinierte Authentifizierung“, aus der Dropdown-Liste aus.
   ![Authentifizierungstyp des Dienstendpunkts](/help/forms/assets/service-endpoint-authtype.png)
1. Klicken Sie auf „Erstellen“.

### HTTP-Client-Konfiguration eines Formulardatenmodells (FDM) zur Leistungsoptimierung {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] bildet bei der Integration mit RESTful-Web-Diensten ein Formulardatenmodell, da die Datenquelle HTTP-Client-Konfigurationen zur Leistungsoptimierung enthält.

Legen Sie die folgenden Eigenschaften der Konfiguration für das **[!UICONTROL Formulardatenmodell HTTP-Client-Konfiguration für REST-Datenquelle]** zum Angeben des regulären Ausdrucks fest:

* Verwenden Sie die Eigenschaft `http.connection.max.per.route` zum Festlegen der maximal zulässigen Anzahl von Verbindungen zwischen dem Formulardatenmodell (FDM) und RESTful-Web-Diensten. Der Standardwert ist 20 Verbindungen.

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

1. Wählen Sie **[!UICONTROL HTTP-Client-Konfiguration des Formulardatenmodells für REST-Datenquellen]**.

1. Führen Sie im Dialog [!UICONTROL Formulardatenmodell HTTP-Client-Konfiguration für REST-Datenquelle] folgende Schritte aus:

   * Geben Sie im Feld **[!UICONTROL Verbindungsgrenze insgesamt]** die maximal zulässige Anzahl von Verbindungen zwischen dem Formulardatenmodell (FDM) und RESTful-Web-Diensten ein. Der Standardwert ist 20 Verbindungen.

   * Geben Sie die maximal zulässige Anzahl von Verbindungen für jede Route im Feld **[!UICONTROL Verbindungslimit pro Route]** an. Der Standardwert ist zwei Verbindungen.

   * Geben Sie die Dauer, für die eine persistente HTTP-Verbindung aufrechterhalten wird, im Feld **[!UICONTROL Aufrechterhalten]** an. Der Standardwert ist 15 Sekunden.

   * Geben Sie im Feld **[!UICONTROL Verbindungs-Zeitüberschreitung]** die Dauer an, für die der [!DNL Experience Manager Forms]-Server auf eine Verbindung wartet. Der Standardwert ist 10 Sekunden.

   * Geben Sie im Feld **[!UICONTROL Socket-Zeitüberschreitung]** den maximalen Zeitraum für die Inaktivität zwischen zwei Datenpaketen an. Der Standardwert ist 30 Sekunden.

## SOAP-Webservices konfigurieren {#configure-soap-web-services}

SOAP-basierte Webservices werden mithilfe von [WSDL-Spezifikationen (Web Services Description Language)](https://www.w3.org/TR/wsdl) beschrieben. [!DNL Experience Manager Forms] unterstützt das WSDL-Modell im RPC-Stil nicht.

Um den SOAP-basierten Webservice in [!DNL Experience Manager] as a Cloud Service zu konfigurieren, benötigen Sie die WSDL-URL für den Webservice. Gehen Sie dann wie folgt vor:

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Datenquellen]**. Wählen Sie den Ordner aus, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud-Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](configure-data-sources.md#cloud-folder).

1. Wählen Sie **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten zum Erstellen der Datenquellenkonfiguration]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL SOAP-Webservice]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration, und wählen Sie **[!UICONTROL Weiter]**.
1. Geben Sie Folgendes für den SOAP-Webservice an:

   * WSDL-URL für den Webservice.
   * Service-Endpunkt. Geben Sie in diesem Feld einen Wert ein, um den in WSDL erwähnten Service-Endpunkt zu überschreiben.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung oder benutzerdefinierte Authentifizierung – für den Zugriff auf den SOAP-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

     <!--If you select **[!UICONTROL X509 Token]** as the Authentication type, configure the X509 certificate. For more information, see [Set up certificates](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).-->
     <!--Specify the KeyStore alias for the X509 certificate in the **[!UICONTROL Key Alias]** field. Specify the time, in seconds, until the authentication request remains valid, in the **[!UICONTROL Time To Live]** field. Optionally, select to sign the message body or timestamp header or both.-->

     <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Wählen Sie **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den SOAP-Webservice zu erstellen.

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
> Das Formulardatenmodell (FDM) unterstützt [OData Version 4](https://www.odata.org/documentation/).
>Eine schrittweise Anleitung zum Konfigurieren von [!DNL Microsoft®® Dynamics 365], online oder lokal finden Sie unter [[!DNL Microsoft® Dynamics] OData-Konfiguration](ms-dynamics-odata-configuration.md).

1. Wechseln Sie zu **[!UICONTROL Tools > Cloud Services > Datenquellen]**. Wählen Sie den Ordner aus, in dem Sie eine Cloud-Konfiguration erstellen möchten.

   Weitere Informationen zum Erstellen und Konfigurieren eines Ordners für Cloud-Service-Konfigurationen finden Sie unter [Konfigurieren des Ordners für Cloud Service-Konfigurationen](#cloud-folder).

1. Wählen Sie **[!UICONTROL Erstellen]**, um den **[!UICONTROL Assistenten zum Erstellen der Datenquellenkonfiguration]** zu öffnen. Geben Sie einen Namen und optional einen Titel für die Konfiguration ein, wählen Sie **[!UICONTROL OData-Service]** aus der Dropdown-Liste **[!UICONTROL Service-Typ]** aus, suchen Sie optional nach einem Miniaturbild für die Konfiguration und wählen Sie **[!UICONTROL Weiter]**.
1. Geben Sie folgende Details für den OData-Service an:

   * Service-Stamm-URL für den zu konfigurierenden OData-Service.
   * Wählen Sie den Authentifizierungstyp – Ohne, OAuth2.0 ([Autorisierungs-Code](https://oauth.net/2/grant-types/authorization-code/), [Client-Anmeldeinformationen](https://oauth.net/2/grant-types/client-credentials/)), Standardauthentifizierung, API-Schlüssel oder benutzerdefinierte Authentifizierung – für den Zugriff auf den OData-Service aus und geben Sie dementsprechend die Details für die Authentifizierung an.

   Wenn Sie **[!UICONTROL API-Schlüssel]** als Authentifizierungstyp auswählen, geben Sie den Wert für den API-Schlüssel an. Der API-Schlüssel kann als Anforderungskopfzeile oder als Abfrageparameter gesendet werden. Wählen Sie eine dieser Optionen aus der Dropdown-Liste **[!UICONTROL Speicherort]** und geben Sie den Namen der Kopfzeile oder des Abfrageparameters im Feld **[!UICONTROL Parametername]** entsprechend an.

   >[!NOTE]
   >
   >Wählen Sie den Authentifizierungstyp OAuth 2.0 aus, um eine Verbindung mit [!DNL Microsoft®® Dynamics]-Services herzustellen, die den OData-Endpunkt als Service-Stamm nutzen.

1. Wählen Sie **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für den OData-Service zu erstellen.

<!--
## Configure Microsoft&reg; SharePoint List {#config-sharepoint-list}

<span class="preview"> This is a pre-release feature and accessible through our [pre-release channel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

To save data in a tabular form use, Microsoft&reg; SharePoint List. To configure a Microsoft SharePoint List in [!DNL Experience Manager] as a Cloud Service, do the following:

1. Go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft&reg; SharePoint]**.   
1. Select a **Configuration Container**. The configuration is stored in the selected Configuration Container. 
1. Click **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** from the drop-down list. The SharePoint configuration wizard appears.  
1. Specify the **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** and **[!UICONTROL OAuth URL]**. For information on how to retrieve Client ID, Client Secret, Tenant ID for OAuth URL, see [Microsoft&reg; Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
    * You can retrieve the `Client ID` and `Client Secret` of your app from the Microsoft&reg; Azure portal.
    * In the Microsoft&reg; Azure portal, add the Redirect URI as `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Replace `[author-instance]` with the URL of your Author instance.
    * Add the API permissions `offline_access` and `Sites.Manage.All` in the **Microsoft&reg; Graph** tab to provide read/write permissions. Add `AllSites.Manage` permission in the **Sharepoint** tab to interact remotely with SharePoint data.
    * Use OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Replace `<tenant-id>` with the `tenant-id` of your app from the Microsoft&reg; Azure portal.

      >[!NOTE]
      >
      > The **client secret** field is mandatory or optional depends upon your Azure Active Directory application configuration. If your application is configured to use a client secret, it is mandatory to provide the client secret.

1. Click **[!UICONTROL Connect]**. On a successful connection, the `Connection Successful` message appears.
1. Select **[!UICONTROL SharePoint Site]** and **[!UICONTROL SharePoint List]** from the drop-down list.
1. Select **[!UICONTROL Create]** to create the cloud configuration for the Microsoft&reg; SharePointList.

-->

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model (FDM), both the data source and [!DNL Experience Manager] Server running Form Data Model (FDM) authenticate each other's identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model (FDM) on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and select **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and select **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, select **[!UICONTROL Select Certificate File]**, upload the certificate, and select **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## Nächste Schritte {#next-steps}

Sie haben die Datenquellen konfiguriert. Als Nächstes können Sie ein Formulardatenmodell (FDM) erstellen oder, falls Sie bereits ein Formulardatenmodell (FDM) ohne eine Datenquelle erstellt haben, können Sie es den schon konfigurierten Datenquellen zuordnen. Weitere Informationen finden Sie unter [Erstellen eines Formulardatenmodells](create-form-data-models.md).

<!--

>[!MORELIKETHIS]
>
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)
>*  [Add Forms Portal to an AEM Sites page](/help/forms/configure-forms-portal.md)

-->