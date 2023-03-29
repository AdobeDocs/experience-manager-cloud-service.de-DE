---
title: Unterschiede zwischen AEM 6.5 Forms und AEM Cloud Services
description: Verwenden Sie Experience Manager Forms und möchten auf Adobe Experience Manager Forms as a Cloud Service aktualisieren? Vergleichen Sie AEM 6.5 Forms und AEM Cloud Services und lernen Sie die wichtigsten Änderungen kennen, bevor Sie ein Upgrade durchführen oder zu Cloud Service migrieren.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: dea6c266e5c10135a320f923dc77d0fd2050988e
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 20%

---

# Wesentliche Änderungen für bestehende Benutzer von Adobe Experience Manager 6.5 Forms  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service bringt einige wichtige Änderungen an bestehenden Funktionen im Vergleich zu Adobe Experience Manager Forms On-Premise und [!DNL Adobe-Managed Service] Umgebungen. Die wichtigsten Unterschiede sind im Folgenden aufgeführt:

<!-- 
<table>
    <thead>
        <tr>
            <th>AEM Forms Components</th>
            <th>Feature/Capability</th>
            <th>[!DNL AEM Forms] as a Cloud Service</th>
            <th>AEM 6.5 Forms on-premise </th>
            <th>AEM 6.5 Forms Adobe Managed Services </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="6">Cloud native features</td>
            <td>Cloud-native architecture</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Auto-scaling based on load</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Zero downtime for upgrades</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Feature roll-out frequency</td>
            <td>Monthly</td>
            <td>Quarterly</td>
            <td>Quarterly</td>
        </tr>
        <tr>
            <td>CDN (content delivery network) included</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Topologies optimized for maximum resilience and efficiency</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td rowspan="3">Developer environment <sup>6</sup></td>
            <td>Self-Service via Cloud Manager</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Cloud-native development environment</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        <tr>
            <td>Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD)</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td rowspan="8">Third-party and Adobe integrations</td>
            <td>[!DNL Micosoft Power Automate] for business process automation</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL Microsoft Dynamics] and [!DNL Salesforce] for Customer Relationship Management (CRM)</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Integration with [!DNL Microsoft Azure] for data storage</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL DocuSign] for e-signatures</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL Adobe Sign] for e-signatures</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[Adobe Launch] to track usage and performance</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>[!DNL Adobe Analytics] to track usage and performance</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Google reCaptcha for adaptive challenges</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="11">Adaptive Forms</td>
            <td>Automated Forms Conversion Service<sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Core Components</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Foundation Components</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Form creation wizard</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Rule Editor<sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Prefill Service <sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Auto-save an adaptive form</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>XSD-Based adaptive forms <sup>1</sup></td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>In-form signing experience for adaptive forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Submit an adaptive form to AEM Forms on JEE Workflows (Process Management)</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Summary, Verify, and Scribble Signature components for adaptive forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="4">Forms Portal</td>
            <td>Drafts and Submission component <sup>2<sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Search & Lister component</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Link component</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>List forms for non-logged in users <sup>2</sup></td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="13">Data integration (Form Data Model) </td>
            <td>OData services</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Microsoft Dynamics</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>SalesForce</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Microsoft Azure Blob Storage</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>RESTful web services - Open API version 3.0 <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>RESTful web services - Open API version 2.0 <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>SOAP-based web services <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Microsoft SQL Server</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>MySQL</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>IBM DB2</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
                <tr>
            <td>Oracle RDBMS</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>AEM user profile</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Sybase</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="8">Communication APIs (Document Services)</td>
            <td>Document Generation (Output Service) <sup>3</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Document Manipulation (Assembler Service) <sup>3</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Signature Service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Encryption service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Reader Extension service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Send to printer service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Convert PDF service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Barcoded Forms service </td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Document Security</td>
            <td>Document Security Extension for Microsoft Office (Digital Rights Management)</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="2">HTML5 Forms <sup>5</sup></td>
            <td>HTML5 Forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Forms Workspace</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Interactive Communications</td>
            <td>Interactive Communications</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
    </tbody>
</table>


<!-- 

## Cloud native features 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native architecture | &#x2705;  | --- |
| Auto-scaling based on load | &#x2705;  | --- |
| Zero downtime for upgrades | &#x2705;  | --- |
| Feature roll-out frequency | Agile*  | Quarterly |
| CDN (content delivery network) included | &#x2705;  | --- | 
| Topologies optimized for maximum resilience and efficiency| &#x2705;  | --- | 

## Integrations 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Integration with [!DNL Micosoft Power Automate] | &#x2705; | --- | 
| Integration with [!DNL DocuSign] | &#x2705; | --- | 
| Integration with [!DNL Microsoft Dynamics] and [!DNL Salesforce] | &#x2705; | --- |  
| Integration with Microsoft Azure data stores | &#x2705; | --- | 
| Integration with [!DNL Adobe Sign] | &#x2705; | &#x2705; | 
| Integration with [!DNL AEM Sites] | &#x2705;| &#x2705; | 
| Integration with [!DNL Adobe Launch] | &#x2705; | &#x2705; | 
| Integration with [!DNL Adobe Analytics] | &#x2705; | &#x2705; |
| Data integration (Form Data Model) | &#x2705; | &#x2705; |
 
## Adaptive forms <sup> 1 </sup>

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Automated Forms Conversion Service  | &#x2705; | &#x2705; |
| Forms Portal Submissions | &#x2705; | &#x2705; | 
| Google Captcha integrations | &#x2705; | &#x2705; |
| Repeatable sections in an adaptive form | &#x2705;| &#x2705; |
| Form fragments | &#x2705; | --- |
| Hardened rule editor | &#x2705; | --- | 
| Form creation wizard | &#x2705; | --- |
| Auto-save an adaptive form | --- | &#x2705; |
| Scribble Signatures | --- | &#x2705; |
| XSD-Based adaptive forms | --- | &#x2705; |
| Using Adobe Sign to add signatures within an Adaptive Form | --- | &#x2705; |
|Submit to AEM Forms on JEE Workflows (Process Management)| --- | &#x2705; | 

## Communication APIs (Document Services <sup> 2 </sup>) and Document Security 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Document Generation (Output Service)| &#x2705; | &#x2705; |
| Document Manipulation (Assembler Service) | &#x2705; | &#x2705; |
| Signature service | --- | &#x2705; |
| Encryption service | --- | &#x2705; |
| Reader Extension service | --- | &#x2705; |
| Send to printer service | --- | &#x2705; |
| Convert PDF service | --- | &#x2705; |
| Barcoded Forms service | --- | &#x2705; |
| Document Security Extension for Microsoft Office (Digital Rights Management) | --- | &#x2705; | 

## Data integration (Form Data Model) <sup> 3 </sup>

| Data Sources | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| OData services | &#x2705; (Version 4.0)|  --- | 
| Microsoft Dynamics| &#x2705;  | --- | 
| SalesForce|  &#x2705; | ---| 
| Microsoft Azure Blob Storage| &#x2705;  | --- | 
| RESTful web services Open API version 3.0| &#x2705; | --- |
| RESTful web services Open API version 2.0| &#x2705; | &#x2705; |
| SOAP-based web services| &#x2705;| &#x2705; |   
| MySQL| &#x2705; | &#x2705; | 
| Microsoft SQL Server| &#x2705; | &#x2705; | 
| IBM DB2| &#x2705; | &#x2705; | 
| Oracle RDBMS| &#x2705; | &#x2705; | 
| Sybase|  ---  | &#x2705; | 
| AEM user profile| --- | &#x2705; | 

## Form-centric workflows

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
|Submit to AEM Forms on JEE Workflows (Process Management)| --- | &#x2705; | 

## HTML5 Forms<sup> 4 </sup> and Interactive Communications 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| HTML5 Forms | --- | &#x2705; | 
| HTML5 Workspace| --- | &#x2705; | 
| Interactive Communications | --- | &#x2705; | 

## Developer environment <sup> 5 </sup>

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native development environment | &#x2705;  | --- | 
| Self-Service via Cloud Manager | &#x2705;  | --- | 
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD) | &#x2705;  | --- | 


-->

## Native Cloud-Funktionen

* Der Dienst verfügt über eine Cloud-native Architektur, die eine automatische Skalierung basierend auf Auslastung, ohne Ausfallzeiten für Aktualisierungen, häufige und nach der Einführung neuer Funktionen und Aktualisierungen sowie Topologien ermöglicht, die für maximale Ausfallsicherheit und Effizienz optimiert sind.

* Der Dienst bietet Funktionen zur Datenexternalisierung (Daten werden bei keiner Verarbeitung auf dem Server gespeichert) und enthält keine Sendeaktionen, mit denen Daten an Adobe Experience Manager-Cloud Service-Instanzen gespeichert werden, was die Sicherheit erhöht. Über Formulare erfasste Daten werden direkt an konfigurierte Datenspeicher gesendet.

* Darüber hinaus ist ein kostenloses CDN (Content Delivery Network) enthalten, mit dem Sie Formulare schneller bereitstellen und wiedergeben können.


## Aktualisierungen des Entwicklungsflusses

* Der Dienst bietet ein SDK zum Entwickeln und Testen von benutzerdefiniertem Code in einer lokalen Umgebung (auf einem lokalen Computer), bevor der Code auf einem Cloud Service bereitgestellt wird. Entwickler entwickeln und testen benutzerdefinierte Komponenten, Designs, Workflows, Anwendungen, Konfigurationen, Vorlagen und mehr mithilfe des SDK auf ihren lokalen Computern. Nach dem Testen des benutzerspezifischen Codes in der lokalen Entwicklungsumgebung stellen sie den benutzerspezifischen Code in einer [Entwicklung oder Staging-Umgebung von Forms CS](/help/implementing/cloud-manager/deploy-code.md) für weitere Tests, bevor sie in eine Produktionsumgebung weitergeleitet werden.

* Entwickler verwalten Code für die Cloud Service- und lokale Entwicklungsumgebung in einer gemeinsamen [Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). Ein auf AEM Archetyp basierendes Git-Repository wird bei der Erstellung eines AEM as a Cloud Service Programms automatisch erstellt.

   ![](/help/forms/assets/git-repo-local-and-forms-cs.png)


* Eine Cloud-native Umgebung verfügt nicht über Web Console (Konfigurations-Manager). Sie können das [[!DNL AEM Forms] as a Cloud Service SDK verwenden, um Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und eine CI/CD-Pipeline zur [Bereitstellung der Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) für Ihre Cloud Service-Instanz zu generieren.

* Adobe Experience Manager Forms as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für Ihre AEM-Projekte. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Im Allgemeinen erfordert AEM eine Trennung von Inhalt und Code in separate Unterpakete, um die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt zu berücksichtigen. Verwenden Sie das Tool [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=de), um bestehende Projektpakete neu zu strukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden. So gewährleisten Sie die Kompatibilität der Pakete mit der Projektstruktur, die für Adobe Experience Manager as a Cloud Service definiert wurde.

* Kompilieren Sie vor der Verwendung Ihrer Kundenpakete mit Forms as a Cloud Service Ihren benutzerdefinierten Code mit der neuesten Version von adobe-aemfd-docmanager neu.

* Verwendung [AEM Forms as a Cloud Service Migration](/help/forms/migrate-to-forms-as-a-cloud-service.md) , um Ihre adaptiven Forms, Designs, Vorlagen und Cloud-Konfigurationen vorzubereiten und zu migrieren von <!-- AEM 6.3 Forms--> AEM 6.4 Forms auf OSGi und AEM 6.5 Forms auf OSGi auf [!DNL AEM] as a Cloud Service. Verwendung [Git-Repository Ihres Programms](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) um vorhandene Vorlagen für adaptive Formulare zu importieren.

* E-Mail unterstützt standardmäßig nur HTTP- und HTTP-Protokolle. [Kontaktieren Sie das Support-Team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email), um Ports für den Versand von E-Mails und das SMTP-Protokoll für Ihre Umgebung zu aktivieren.

## Lokalisierung

* Die URL-Konvention von lokalisierten adaptiven Formularen unterstützt nun die Angabe eines Gebietsschemas in der URL. Die neue URL-Konvention ermöglicht das Caching lokalisierter Formulare in einem Dispatcher oder CDN. Verwenden Sie in einer Cloud Service-Umgebung das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html` , um eine lokalisierte Version eines adaptiven Formulars anzufordern, anstatt `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`.

* Adobe empfiehlt die Verwendung von Dispatcher- oder CDN-Caching. Auf diese Weise wird das Rendern vorausgefüllter Formulare beschleunigt.


## Adaptive Formulare

* **Regeleditor:** AEM Forms as a Cloud Service bietet eine härtere [Regeleditor](rule-editor.md#visual-rule-editor). Der Code-Editor ist nicht auf Forms as a Cloud Service verfügbar.

   Die [Migrationsdienstprogramm](/help/forms/migrate-to-forms-as-a-cloud-service.md) migriert Ihre Formulare mit benutzerdefinierten Regeln (die im Code-Editor erstellt werden). Das Dienstprogramm konvertiert solche Regeln in benutzerdefinierte Funktionen, die von Forms as a Cloud Service unterstützt werden. Sie können die wiederverwendbaren Funktionen mit dem Rule Editor verwenden, um weiterhin Ergebnisse zu erhalten, die mit Regelskripten erzielt wurden. Die `onSubmitError` oder `onSubmitSuccess` -Funktionen sind jetzt als Aktionen im Regeleditor verfügbar.

* **Vorbefüllungsdienst:** Standardmäßig führt der Vorbefüllungs-Dienst Daten mit einem adaptiven Formular auf dem Client zusammen, anstatt Daten auf dem Server in AEM 6.5 Forms zusammenzuführen. Die Funktion hilft, die zum Vorausfüllen eines adaptiven Formulars erforderliche Zeit zu verbessern. Sie können immer konfigurieren, dass die Zusammenführungsaktion auf dem Adobe Experience Manager Forms-Server ausgeführt wird.

* **Übermittlungsaktionen:** Die **Email** Übermittlungsaktion bietet Optionen zum Senden von Anhängen und Anhängen des Datensatzdokuments (DoR) an E-Mails. Sie können sie anstelle der **E-Mail als PDF** Aktion verfügbar in AEM 6.5 Forms.

* **automated forms conversion-Dienst**: Der Dienst stellt kein Metamodell für den Automated forms conversion-Dienst bereit. Sie können [Laden Sie es aus der Automated forms conversion-Service-Dokumentation herunter.](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

* **XSD-basierte adaptive Forms:** Sie können XDP-Vorlage verwenden, um eine Vorlage für Dokument für Datensatz zu entwerfen. Der Dienst unterstützt keine XFA-basierten adaptiven Forms

* **Komponenten**: Der Dienst unterstützt keine Formularsignaturerfahrung und enthält nicht die Komponenten &quot;Zusammenfassung&quot;und &quot;Überprüfen&quot;für adaptive Forms.

## Formularportal

* Sie können die Komponenten &quot;Search &amp; Lister&quot;, &quot;Drafts and Submissions&quot;und &quot;Link&quot;von Forms Portal verwenden, um Formulare für angemeldete Benutzer aufzulisten. Die anonyme Nutzung von Forms Portal wird nicht standardmäßig unterstützt (OOTB). Sie können das Forms Portal anpassen, um die Anzeige von Formularen für nicht angemeldete Benutzer zu aktivieren.

* Der Dienst speichert keine Metadaten für Entwürfe und übermittelte adaptive Forms.

## Document Services:

Forms as a Cloud Service stellt RESTful-APIs für die Dokumenterstellung und Dokumentbearbeitung bereit. Sie können diese APIs verwenden, um Dokumente bei Bedarf oder in Stapeln zu generieren oder zu bearbeiten:

* **Document Services: Document Generation APIs (Output Service)**: In einem einzelnen API-Aufruf oder Batch können Sie nur eine Vorlage mit mehreren DATA XML-Dateien verwenden. Die Verwendung mehrerer Vorlagen mit mehreren Datendateien in einem einzelnen API-Aufruf wird nicht unterstützt.

* **Document Manipulation APIs (Assembler-Dienst)**:

   * Vorgänge, die auf Document Services oder Anwendungen basieren, sind nicht verfügbar. Beispielsweise werden Microsoft Word zu PDF, Microsoft Excel zu PDF und HTML zu PDF, PostScript (PS) zu PDF und XDP zu PDF forms nicht unterstützt. Diese Vorgänge sind auf Microsoft Office, Adobe Acrobat, Adobe Distiller bzw. Forms Document Service angewiesen.

   * Konvertieren Sie Dokumente, die nicht im PDF-Format vorliegen, in ein PDF-Format, bevor Sie sie mit Kommunikations-Dokument-Manipulations-APIs verwenden. Wenn sich Ihre Dokumente beispielsweise im Microsoft Office-, HTML-, PostScript- (PS) und XDP-Format befinden, konvertieren Sie diese Dokumente in das PDF-Format, bevor Sie sie mit PDF-Dokumenten verwenden. Sie können die [ConvertPDF](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html) -Dienst für solche Konvertierungen.

* Sie können eine AEM 6.5 Forms-Umgebung für Digital Signature, Encryption, Reader Extension, Send to printer, Convert PDF und Barcoded Forms-Dienst verwenden.


## Datenintegration (Formulardatenmodell)

* Forms as a Cloud Service ermöglicht die Verwendung von Microsoft Azure Blob-, Microsoft Sharepoint-, Microsoft OneDrive- und Services, die allgemeine CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) als Datenspeicher unterstützen. Die Spezifikation der Open API-Spezifikation 2.0 und der Open API 3.0 werden unterstützt.

* Der Dienst unterstützt auch JDBC-Connector, Microsoft Dynamics, SalesForce, SOAP-basierte Webdienste und Dienste, die OData unterstützen.

* Sie können auch AEM Benutzerprofil verbinden, um Benutzerinformationen abzurufen und zu aktualisieren.

* Das Forms-Datenmodell unterstützt nur HTTP- und HTTPS-Endpunkte zum Senden von Daten. Der Dienst unterstützt keine gegenseitige SSL-Authentifizierung für REST-Connector und x509 zertifikatbasierte Authentifizierung für SOAP-Datenquellen.


## Elektronische Signatur

* Der Dienst bietet eine OOTB-Integration mit Adobe Sign und unterstützt DocuSign für E-Signaturen.


## HTML5-Formulare

* Sie können eine Forms-Umgebung AEM 6.5 für folgende Zwecke verwenden:

   * Rendern Sie Ihre XDP-basierten Formulare als HTML5 Forms. Der Dienst unterstützt keine HTML5 Forms (Mobile Forms).

   * Daten offline erfassen und synchronisieren, wenn Sie das nächste Mal online sind mit [AEM Forms Workspace](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) App.

## Interaktive Kommunikation

* Sie können Kommunikations-APIs verwenden, um personalisierte Dokumente bei Bedarf oder in Stapeln zu erstellen. Sie können eine AEM 6.5 Forms-Umgebung für Webkanäle und die Benutzeroberfläche für Agenten verwenden.

## Document Security Extension for Microsoft Office

* Document Security Extension for Microsoft Office (Digital Rights Management) unterstützt AEM 6.5 Forms. Die -Erweiterung ist nicht für Forms as a Cloud Service verfügbar.








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




