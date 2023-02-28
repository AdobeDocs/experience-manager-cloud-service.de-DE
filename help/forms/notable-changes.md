---
title: Änderungen zwischen AEM 6.5 Forms und AEM Cloud Services
description: Verwenden Sie Experience Manager Forms und möchten auf Adobe Experience Manager Forms as a Cloud Service aktualisieren? In diesem Abschnitt erfahren Sie mehr über die wichtigsten Änderungen, bevor Sie auf Cloud Service aktualisieren oder migrieren.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: 2a464a0a11396a1948ba7211d5c0534769e6659c
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 26%

---

# Wesentliche Änderungen für bestehende Benutzer von Adobe Experience Manager 6.5 Forms  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service bringt einige wichtige Änderungen an bestehenden Funktionen im Vergleich zu Adobe Experience Manager Forms On-Premise und [!DNL Adobe-Managed Service] Umgebungen. Die wichtigsten Unterschiede sind im Folgenden aufgeführt:

| Funktion/Funktion | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms |
|---|---|---|
| Cloud-native Architektur | ✅ | ⛌ |
| Automatische Skalierung basierend auf der Last | ✅ | ⛌ |
| Keine Ausfallzeiten bei Upgrades | ✅ | ⛌ |
| Häufigkeit der Funktionsveröffentlichung | Agile* | Vierteljährlich |
| CDN (Content Delivery Network) enthalten | ✅ | ⛌ |
| Topologien, die für maximale Ausfallsicherheit und Effizienz optimiert sind | ✅ | ⛌ |
| Cloud-native Entwicklungsumgebung | ✅ | ⛌ |
| Self-Service über Cloud Manager | ✅ | ⛌ |
| Automatisierte Upgrades mit kontinuierlicher Integration und kontinuierlicher Bereitstellung (CI/CD) | ✅ | ⛌ |
| Integration mit [!DNL Micosoft Power Automate] | ✅ | ⛌ |
| Integration mit [!DNL DocuSign] | ✅ | ⛌ |
| Einfache Verbindung mit Microsoft Dynamics und Salesforce | ✅ | ⛌ |
| Einfache Konnektivität mit Microsoft Azure-Datenspeichern | ✅ | ⛌ |
| Härter Regeleditor | ✅ | ⛌ |
| Assistent zur Formularerstellung | ✅ | ⛌ |
| Benutzerdefinierte XCI-Unterstützung für Datensatzdokument | ✅ | ⛌ |
| Adaptives Forms <sup>1</sup> | ✅ | ✅ |
| Kommunikations-APIs (Document Services) <sup>2,3</sup> | ✅ | ✅ |
| automated forms conversion-Dienst <sup>4</sup> | ✅ | ✅ |
| Forms Portal <sup>5</sup> | ✅ | ✅ |
| Forms-Datenmodell <sup>6</sup> | ✅ | ✅ |
| HTML5 Forms <sup>7</sup> | ⛌ | ✅ |
| Document Security | ⛌ | ✅ |

Bevor Sie mit dem Dienst fortfahren, berücksichtigen Sie bitte die folgenden Ausnahmefälle:

+++ 1. Adaptives Forms

* **XSD-basierte adaptive Forms:** Der Dienst unterstützt keine HTML5 Forms (Mobile Forms). Wenn Sie Ihre XDP-basierten Formulare als HTML5 Forms wiedergeben, können Sie die Funktion weiterhin in AEM 6.5 Forms verwenden. Sie können XDP-Vorlage verwenden, um eine Vorlage für Dokument für Datensatz zu entwerfen. Der Dienst unterstützt keine XFA-basierten adaptiven Forms
* **Importieren von Vorlagen für adaptive Formulare:** Verwenden Sie die Build-Pipeline und das entsprechende Git-Repository Ihres Programms, um vorhandene adaptive Formularvorlagen zu importieren.
* **Regeleditor:** AEM Forms as a Cloud Service bietet eine härtere [Regeleditor](rule-editor.md#visual-rule-editor). Der Code-Editor ist nicht auf Forms as a Cloud Service verfügbar. Das Migrationsdienstprogramm hilft Ihnen bei der Migration Ihrer Formulare mit benutzerdefinierten Regeln (die im Code-Editor erstellt wurden). Das Dienstprogramm konvertiert solche Regeln in benutzerdefinierte Funktionen, die von Forms as a Cloud Service unterstützt werden. Sie können die wiederverwendbaren Funktionen mit dem Regeleditor verwenden, um weiterhin Ergebnisse zu erhalten, die mit Regelskripten erzielt wurden. `onSubmitError` oder `onSubmitSuccess` -Funktionen sind jetzt als Aktionen im Regeleditor verfügbar.
* **Entwürfe und Übermittlungen:** Der Dienst speichert keine Metadaten für Entwürfe und übermittelte adaptive Forms.
* **Vorbefüllungsdienst:** Standardmäßig führt der Vorbefüllungs-Dienst Daten mit einem adaptiven Formular auf dem Client zusammen, anstatt Daten auf dem Server in AEM 6.5 Forms zusammenzuführen. Die Funktion hilft, die zum Vorausfüllen eines adaptiven Formulars erforderliche Zeit zu verbessern. Sie können immer konfigurieren, dass die Zusammenführungsaktion auf dem Adobe Experience Manager Forms-Server ausgeführt wird.
* **Übermittlungsaktionen:** Die **E-Mail als PDF** -Aktion nicht verfügbar ist. Die Übermittlungsaktion **E-Mail** bietet Optionen zum Senden von Anhängen und zum Anhängen von Datensatzdokumenten (Document of Record, DoR) per E-Mail.
* **Komponenten**: Der Dienst unterstützt keine Formularsignaturerfahrung und enthält nicht die Komponenten &quot;Zusammenfassung&quot;und &quot;Überprüfen&quot;für adaptive Forms.



+++


+++ 2. Document Services: Document Manipulation APIs (Assembler-Dienst)


Der Dienst unterstützt keine von anderen Diensten oder Anwendungen abhängigen Vorgänge:

* Die Konvertierung von Dokumenten im Nicht-PDF-Format in das PDF-Format wird nicht unterstützt. Beispielsweise werden Microsoft Word zum PDF, Microsoft Excel zum PDF und HTML zum PDF nicht unterstützt. Wenn Ihre Dokumente nicht im PDF-Format vorliegen. Konvertieren Sie diese Dokumente in das PDF-Format, bevor Sie sie mit den Kommunikations Document Manipulation-APIs verwenden. Wenn sich Ihre Dokumente beispielsweise im Microsoft Office-, HTML-, PostScript- (PS) und XDP-Format befinden, konvertieren Sie diese Dokumente in das PDF-Format, bevor Sie sie mit PDF-Dokumenten verwenden.
* Adobe Distiller-basierte Konvertierungen werden nicht unterstützt. Zum Beispiel PostScript(PS) zu PDF
* Forms Service-basierte Konvertierungen werden nicht unterstützt. Beispielsweise XDP auf PDF forms.
* Der Dienst unterstützt nicht die Konvertierung einer signierten PDF oder Transparent-PDF in ein anderes PDF-Format.
* Das Anwenden von Verwendungsrechten mithilfe des Reader Extensions-Dienstes ist nicht verfügbar.
* Der Dienst bietet keine Möglichkeit, signierte oder transparente PDF-Dokumente in das PDF/A-Format zu konvertieren.

+++


+++ 3. Document Services: Document Generation APIs (Output Service)

In einem einzelnen API-Aufruf oder Batch können Sie nur eine Vorlage mit mehreren DATA XML-Dateien verwenden. Die Verwendung mehrerer Vorlagen mit mehreren Datendateien in einem einzelnen API-Aufruf wird nicht unterstützt.

+++

+++ 4. Automated forms conversion-Dienst

Der Dienst stellt kein Metamodell für den Automated forms conversion-Dienst bereit. Sie können [Laden Sie es aus der Automated forms conversion-Service-Dokumentation herunter.](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

+++

+++ 5. Forms Portal

Die anonyme Nutzung von Forms Portal wird nicht standardmäßig unterstützt (OOTB). Sie können das Forms Portal anpassen, um die Anzeige von Formularen für nicht angemeldete Benutzer zu aktivieren.

+++

+++ 6. Formulardatenmodell

* Das Forms-Datenmodell unterstützt nur HTTP- und HTTP-Endpunkte zum Senden von Daten. Der Dienst unterstützt keine gegenseitige SSL-Authentifizierung für REST-Connector und x509 zertifikatbasierte Authentifizierung für SOAP-Datenquellen.

* Forms as a Cloud Service ermöglicht die Verwendung von Microsoft Azure Blob-, Microsoft Sharepoint-, Microsoft OneDrive- und Services, die allgemeine CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) als Datenspeicher unterstützen. Sowohl die Open API-Spezifikation 2.0 als auch die Open API-Spezifikation werden unterstützt. Der Dienst unterstützt auch den JDBC-Connector.

+++


+++ 7. HTML5 Forms

* Der Dienst unterstützt keine HTML5 Forms (Mobile Forms). Wenn Sie Ihre XDP-basierten Formulare als HTML5 Forms wiedergeben, können Sie die Funktion weiterhin in AEM 6.5 Forms verwenden.

* Wenn Sie einen Anwendungsfall haben, um Daten offline zu erfassen und sie zu synchronisieren, wenn Sie das nächste Mal online zurückkehren, können Sie die [AEM Forms Workspace](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) Funktion in AEM 6.5 Forms.

+++





+++ 8. Entwicklungsumgebung

* Eine Cloud-native Umgebung verfügt nicht über Web Console (Konfigurations-Manager). Sie können das [[!DNL AEM Forms] as a Cloud Service SDK verwenden, um Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und eine CI/CD-Pipeline zur [Bereitstellung der Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) für Ihre Cloud Service-Instanz zu generieren.
* E-Mail unterstützt standardmäßig nur HTTP- und HTTPS-Protokolle. [Kontaktieren Sie das Support-Team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email), um Ports für den Versand von E-Mails und das SMTP-Protokoll für Ihre Umgebung zu aktivieren.
* Der Dienst unterstützt nicht die Konvertierung einer signierten PDF oder Transparent-PDF in ein anderes PDF-Format. Kompilieren Sie vor der Verwendung Ihrer Kundenpakete mit Forms as a Cloud Service Ihren benutzerdefinierten Code mit der neuesten Version der adobe-aemfd-docmanager* URL-Konvention des lokalisierten adaptiven Forms jetzt unterstützt, ein Gebietsschema in der URL anzugeben. Die neue URL-Konvention ermöglicht das Caching lokalisierter Formulare in einem Dispatcher oder CDN. Verwenden Sie in der Cloud Service-Umgebung, um die lokalisierte Version eines adaptiven Formulars anzufordern, das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html` statt `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe empfiehlt die Verwendung von Dispatcher- oder CDN-Caching. Auf diese Weise wird das Rendern vorausgefüllter Formulare beschleunigt
* Adobe Experience Manager Forms as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für Ihre AEM-Projekte. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Im Allgemeinen erfordert AEM eine Trennung von Inhalt und Code in separate Unterpakete, um die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt zu berücksichtigen. Verwenden Sie das Tool [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=de), um bestehende Projektpakete neu zu strukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden. So gewährleisten Sie die Kompatibilität der Pakete mit der Projektstruktur, die für Adobe Experience Manager as a Cloud Service definiert wurde.


+++

<!-- 

### HTML5 Forms (Mobile Forms)

The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms.

### Adaptive Forms 

* **XSD-Based Adaptive Forms:** The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms. You can use XDP-template to design a template for Document for Record. The service does not support XFA based Adaptive Forms  
* **Importing Adaptive Form templates:** Use build pipeline and corresponding Git repository of your program to import existing Adaptive Form templates. 
*  **Rule editor:** AEM Forms as a Cloud Service provides a hardened [Rule editor](rule-editor.md#visual-rule-editor). The code editor is not available on Forms as a Cloud Service. The migration utility helps you migrate your forms that have custom rules (created in code editor). The utility converts such rules into custom functions supported on Forms as a Cloud Service. You can use the reusable functions with Rule editor to continue obtaining results obtained with rule scripts  The `onSubmitError` or `onSubmitSuccess` functions are now available as actions the Rule Editor.  
* **Drafts and submissions:** The service does not retain metadata for drafts and submitted Adaptive Forms.  
* **Prefill Service:** By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server. 
* **Submit actions:** The **Email as PDF** action is not available. The **Email** submit action provide options to send attachments and attach Document of Record (DoR) with email. 
* **Components**:  The service does not support in-form signing experience and does not include the Summary and Verify components for Adaptive Forms.  
* **Forms portal**: Support for anonymous use of Forms portal is not available out of the box (OOTB). You can customize the forms portal to enable displaying forms for non-logged in users.

### Form Data Model

* Forms data model supports only HTTP and HTTPs endpoints to submit data. The service does not support Mutual SSL for REST connector and x509 certificate-based authentication for SOAP data sources. * Forms as a Cloud Service allows to use Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive, and services supporting general CRUD (Create, Read, Update, and Delete) operations as data stores, both Open API specification 2.0 and Open API specification are supported. The service also provides support for JDBC connector.


### Automated Forms Conversion Service     

The service does not provide meta-model for Automated Forms Conversion Service. You can [download it from Automated Forms Conversion Service documentation](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).


### Configurations

* Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment.  
* If you use custom bundles, recompile your code with latest version of adobe-aemfd-docmanager before using these bundles with Forms as a Cloud Service. 


### Document Services: Document Manipulation APIs (Assembler Service)

The service does not support operations dependent on other services or applications:  

* Conversion of documents in a non-PDF format to a PDF format is not supported. For example, Microsoft Word to PDF, Microsoft Excel to PDF, and HTML to PDF are not supported. If your documents are in a non-PDF format. Convert such documents to PDF format before using those with Communications Document Manipulation APIs. For example, if your documents are in Microsoft Office, HTML, PostScript (PS), XDP format, convert these documents to PDF format before using those with PDF documents. 
* Adobe Distiller-based conversions are not supported. For example, PostScript(PS) to PDF
* Forms Service-based conversions are not supported. For example, XDP to PDF Forms.
* The service does not support converting a Signed PDF or Transparent PDF to another PDF format.
* Applying usage rights using Reader Extensions Service is not available. 
* The service does not provide the ability to convert signed or transparent PDF Documents to PDF/A format. 

### Document Services: Document Generation APIs (Output Service)

* In a single API call or batch, you can use one template with multiple DATA XML files. Using mutiple templates with multiple data files in a single API call is not supported. 

### Other differences

* A cloud-native environment does not have web console (configuration manager). You can use [[!DNL AEM Forms] as a Cloud Service SDK to generate configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) and CI/CD pipeline to [deploy the configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) to your Cloud Service instance.
* Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment.
* The service does not support converting a Signed PDF or Transparent PDF to another PDF format.* Before using your customer bundles with Forms as a Cloud Service, recompile your custom code with the latest version of adobe-aemfd-docmanager* URL convention of localized Adaptive Forms now supports specifying a locale in the URL. New URL convention enables caching localized forms on a Dispatcher or CDN. On Cloud Service environment, use the URL format `http://host:port/content/forms/af/<afName>.<locale>.html` to request a localized version of an Adaptive Form instead of `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe recommends using Dispatcher or CDN caching. It helps improve rendering speed of prefilled forms 
* Adobe Experience Manager Forms as a Cloud Service brings many new features and possibilities into your AEM Projects. However, there are some changes required to Adobe Experience Manager Maven projects to be compatible with AEM Cloud Service. At a high-level, AEM requires a separation of content and code into discrete subpackages to respect the split between mutable and immutable content. Use the [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) tool to restructure existing project packages by separating content and code into discrete packages to be compatible with the project structure defined for Adobe Experience Manager as a Cloud Service.
-->




