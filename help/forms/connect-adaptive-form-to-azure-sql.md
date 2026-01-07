---
Title: How to Connect AEM Adaptive Forms with Azure SQL Storage
Description: Learn how to configure an Azure SQL Database connection in AEM Forms and integrate it with your Adaptive Forms to store or retrieve data efficiently using JDBC.
Keywords: Azure SQL integration with AEM Forms, Connecting Adaptive Forms to Azure SQL Database, JDBC connection for Azure SQL in AEM Forms, Storing Adaptive Form data in Azure SQL
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: e29f70aa1a8164787c7d310a05c24d7e501803e5
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 16%

---

# Verbinden eines adaptiven Formulars mit dem Azure SQL-Speicher

Adaptive Forms in Adobe Experience Manager (AEM) kann mit externen Datenbanken integriert werden, um Daten zu speichern oder abzurufen.
In diesem Artikel wird beschrieben, wie Sie ein adaptives Formular mithilfe von JDBC über AEM as a Cloud Service mit einer Azure SQL-Datenbank verbinden.

>
> 
> Dieses Handbuch gilt für Nicht-Sandbox-AEM as a Cloud Service-Umgebungen mit aktivierten erweiterten Netzwerkfunktionen.

## Vorteile

Die Integration von Adaptive Forms mit Azure SQL bietet mehrere Vorteile:

* **Echtzeit-Dateninteraktion:** Ermöglicht das Lesen und Schreiben von Daten zwischen Formularen und der Azure-Datenbank.
* **Skalierbarkeit:** Azure SQL bietet eine skalierbare Datenbankleistung, die für Anwendungen auf Unternehmensebene geeignet ist.
* **Zentrale Datenspeicherung:** Sichere Speicherung von Formularübermittlungen und abgerufenen Daten an einem zentralen Ort.
* **Sicherheitskonformität:** Nutzt die integrierten Netzwerk-, Firewall- und Verschlüsselungsoptionen von Azure, um eine sichere Kommunikation zu gewährleisten.
* **Cloud-native Integration:** Ideal für moderne Cloud-First-Architekturen unter Verwendung von AEM as a Cloud Service.

## Voraussetzungen

* Erstellen Sie [Azure SQL](https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal)Datenbank und stellen Sie sicher, **Proxy-Verbindung** aktiviert ist.

  >[!NOTE]
  >
  > Navigieren Sie zu: `Azure Portal → SQL Server → Security → Networking → Connectivity` , um **Proxy-Verbindung“** aktivieren.

  ![Azure DB erstellen](/help/forms/assets/create-azure-db.png)

* Aktivieren [Erweiterte Netzwerke mit einer dedizierten Ausgangs-IP konfiguriert](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/dedicated-egress-ip-address) für die erstellte Azure-Datenbank.

  >[!NOTE]
  >
  >    Nach der Aktivierung der dedizierten Ausgangs-IP. Gehen Sie zu `Azure Portal → SQL Server → Security → Networking → Public Access` und fügen Sie die Ausgangs-IP zu den Firewall-Regeln hinzu.

  ![Egress-IP](/help/forms/assets/cretae-azure-db-egress-ip.png)

* Festlegen der Port-Weiterleitung in der Cloud-Umgebung mit:
   * **portOrigin**: Zwischen `30000–30999`
   * **portDest**: `1433` (Standardport für Azure SQL)
Beispiel: `portOrigin: 30433 → portDest: 1433`

     >
     > 
     > Sie können sich an den Adobe Cloud Manager-Support wenden, um die Port-Weiterleitung zu konfigurieren.


## Schritte zum Verbinden von Adaptive Forms mit Azure SQL

**Schritt 1: Klonen Sie das AEM as a Cloud Service-Git-Repository**

1. Öffnen Sie die Befehlszeile und wählen Sie einen Ordner zum Speichern des AEM as a Cloud Service-Repositorys aus, z. B. `/cloud-service-repository/`.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```

   **Wo finden Sie diese Informationen?**

   Eine schrittweise Anleitung zum Auffinden dieser Details finden Sie im Adobe Experience League-Artikel [Zugriff auf Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).

   Wenn der Befehl erfolgreich abgeschlossen wurde, wird in Ihrem lokalen Verzeichnis ein neuer Ordner erstellt. Dieser Ordner ist nach Ihrer Anwendung benannt.

1. Öffnen Sie den Repository-Ordner in einem Editor.

**Schritt 2: Erforderliche JARs hinzufügen**

Fügen Sie die [SQL-Treiberabhängigkeit](https://central.sonatype.com/artifact/com.microsoft.sqlserver/mssql-jdbc/12.8.0.jre11?smo=true) über das `all`-Paket in das AEM-Projekt ein:

>[!NOTE]
>
> Informationen zum Einschließen der SQL-Abhängigkeit in Ihr Projekt finden Sie im Abschnitt [SQL-](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool#mysql-driver-dependencies)&quot;.

**Schritt 3: Hinzufügen der JDBC-Konfiguration**

1. Navigieren Sie zum folgenden Verzeichnis in Ihrem `<application folder>`, in dem die OSGi-Konfiguration für den JDBC-Pool platziert werden soll:

   ```bash
   cd ui.config/src/jcr_root/apps/<application folder>/osgiconfig/config/
   ```

**Schritt 4: Erstellen Sie die Azure SQL-Verbindungskonfigurationsdatei**

1. Erstellen Sie die Datei :

   ```bash
   com.day.commons.datasource.jdbcpool.JdbcPoolService~<application folder>-sql.cfg.json
   ```

1. Fügen Sie die folgenden Codezeilen hinzu:

   ```json
   {
   "datasource.name": "azuredbshr",
   "jdbc.driver.class": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
   "jdbc.username": "<azureuser>",
   "jdbc.connection.uri": "jdbc:sqlserver://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30433;database=testdb;user=<azureuser>;password=<azurepassword>;encrypt=true;trustServerCertificate=false;hostNameInCertificate=*.database.windows.net;loginTimeout=30;",
   "jdbc.password": "******",
   "jdbc.validation.query": "SELECT 1"
       }
   ```

   >
   >
   > Ersetzen Sie `jdbc.username` durch den tatsächlichen Azure-Benutzernamen und `jdbc.password` durch das tatsächliche sichere Kennwort.

**Schritt 5: Übergeben und Übertragen der Änderungen**

Öffnen Sie das Terminal und führen Sie die folgenden Befehle aus:

```bash
git add .
git commit -m "<commit message>"
git push 
```

**Schritt 6: Bereitstellen der Änderungen über die Cloud Manager-Pipeline**

1. Anmelden bei **AEM Cloud Manager**.
1. Navigieren Sie zu Ihrem Projekt und führen Sie die Pipeline aus , um die Änderungen bereitzustellen.

**Schritt 7: Erstellen eines Formulardatenmodells (FDM)**

Sobald die Einrichtung von AEM und Azure abgeschlossen ist und die Code-Änderungen bereitgestellt wurden:

1. Wechseln Sie zur AEM-Autoreninstanz.
1. Navigieren Sie **Tools** > **Forms** > **Datenintegrationen**.
1. Neues **Formulardatenmodell** erstellen.
1. Wählen **auf der Registerkarte** die erstellte JDBC-Konfiguration aus.
1. Klicken Sie **[!UICONTROL Erstellen]** und überprüfen Sie die Verbindung.

![Erstellen von Formulardatenmodellen](/help/forms/assets/create-azure-sql-fdm.png)

**Schritt 8: Verwenden des erstellten FDM in einem adaptiven Formular**

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.
1. Wählen Sie das im vorherigen Schritt erstellte FDM als Datenmodell aus.
1. Verwenden Sie [Datenbindungen, um Formularfelder mit der Azure SQL-Datenquelle zu verbinden](/help/forms/work-with-form-data-model.md#add-data-model-objects-and-services) und die Übermittlungsaktion zu konfigurieren.

## Best Practices

* Verwenden Sie **Geheimnisverwaltung**, um in Konfigurationsdateien hartcodierte Kennwörter zu vermeiden.
* Rotieren Sie regelmäßig die Datenbankanmeldeinformationen und aktualisieren Sie die Konfiguration sicher.
* Überwachen Sie JDBC-Verbindungsprotokolle auf Fehler und Latenzen.
* Befolgen Sie die Best Practices von Azure zum Schützen von SQL-Datenbanken und Firewall-Konfigurationen.
* Vermeiden Sie die Verwendung von Datenbankkonten mit hohen Berechtigungen für den Formularzugriff.

## Verwandte Artikel

{{af-submit-action}}