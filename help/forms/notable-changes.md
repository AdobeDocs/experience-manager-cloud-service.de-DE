---
title: Unterschiede zwischen AEM 6.5 Forms und AEM Cloud Services
description: Verwenden Sie Experience Manager Forms und möchten auf Adobe Experience Manager Forms as a Cloud Service aktualisieren? Vergleichen Sie AEM 6.5 Forms und AEM Cloud Services und lernen Sie die wichtigsten Änderungen kennen, bevor Sie ein Upgrade durchführen oder zu Cloud Service migrieren.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: 54a1ae1cc030030e44612b502b70c9b567144538
workflow-type: tm+mt
source-wordcount: '1352'
ht-degree: 15%

---

# Wesentliche Änderungen für bestehende Benutzer von Adobe Experience Manager 6.5 Forms  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service bringt einige wichtige Änderungen an bestehenden Funktionen im Vergleich zu Adobe Experience Manager Forms On-Premise und [!DNL Adobe-Managed Service] Umgebungen. Die wichtigsten Unterschiede sind im Folgenden aufgeführt:

## Native Cloud-Funktionen

* Der Dienst verfügt über eine Cloud-native Architektur, die eine automatische Skalierung basierend auf Auslastung, ohne Ausfallzeiten für Aktualisierungen, häufige und nach der Einführung neuer Funktionen und Aktualisierungen sowie Topologien ermöglicht, die für maximale Ausfallsicherheit und Effizienz optimiert sind.

* Der Dienst enthält keine Sendeaktionen, mit denen Daten an Adobe Experience Manager-Cloud Service-Instanzen gespeichert werden, wodurch sie supersicher sind. Über Formulare erfasste Daten werden direkt an konfigurierte Datenspeicher gesendet.

* Darüber hinaus ist ein kostenloses CDN (Content Delivery Network) enthalten, mit dem Sie Formulare schneller bereitstellen und wiedergeben können.


## Aktualisierungen des Entwicklungsflusses

* Der Dienst bietet ein SDK zum Entwickeln und Testen von benutzerdefiniertem Code in einer lokalen Umgebung (auf einem lokalen Computer), bevor der Code auf einem Cloud Service bereitgestellt wird. Entwickler entwickeln und testen benutzerdefinierte Komponenten, Designs, Workflows, Anwendungen, Konfigurationen, Vorlagen und mehr mithilfe des SDK auf ihren lokalen Computern. Nach dem Testen des benutzerspezifischen Codes in der lokalen Entwicklungsumgebung stellen sie den benutzerspezifischen Code in einer [Entwicklung oder Staging-Umgebung von Forms CS](/help/implementing/cloud-manager/deploy-code.md) für weitere Tests, bevor sie in eine Produktionsumgebung weitergeleitet werden.

* Entwickler verwalten Code für die Cloud Service- und lokale Entwicklungsumgebung in einer gemeinsamen [Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). Ein auf AEM Archetyp basierendes Git-Repository wird bei der Erstellung eines AEM as a Cloud Service Programms automatisch erstellt.

   ![](/help/forms/assets/git-repo-local-and-forms-cs.png)

* Der Entwicklungsfluss für Forms wird as a Cloud Service an AEM Archetyp für AEM Cloud Service ausgerichtet. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Im Allgemeinen erfordert AEM eine Trennung von Inhalt und Code in separate Unterpakete, um die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt zu berücksichtigen. Verwenden Sie das Tool [](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=de)Repository Modernizer, um bestehende Projektpakete neu zu strukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden. So gewährleisten Sie die Kompatibilität der Pakete mit der Projektstruktur, die für Adobe Experience Manager as a Cloud Service definiert wurde.

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

* **Komponenten**: Sie können [Adaptive Forms-Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md) , um Formulare zu entwerfen. Diese Komponenten basieren auf WCM-Kernkomponenten, befolgen BEM-Standards und können einfach angepasst werden. Der Dienst unterstützt keine Formularsignaturerfahrung und enthält nicht die Komponenten &quot;Zusammenfassung&quot;und &quot;Überprüfen&quot;für adaptives Formular

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

* Der Dienst unterstützt auch JDBC-Connector, Microsoft Dynamics, SalesForce, SOAP-basierte Webdienste und Dienste, die OData unterstützen.

* Sie können auch AEM Benutzerprofil verbinden, um Benutzerinformationen abzurufen und zu aktualisieren.

* Das Forms-Datenmodell unterstützt nur HTTP- und HTTPS-Endpunkte zum Senden von Daten. Der Dienst unterstützt keine gegenseitige SSL-Authentifizierung für REST-Connector und x509 zertifikatbasierte Authentifizierung für SOAP-Datenquellen.

* Forms as a Cloud Service ermöglicht die Verwendung von Microsoft Azure Blob-, Microsoft Sharepoint-, Microsoft OneDrive- und Services, die allgemeine CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) als Datenspeicher unterstützen. Die Spezifikation der Open API-Spezifikation 2.0 und der Open API 3.0 werden unterstützt.


## Elektronische Signatur

* Der Dienst bietet eine OOTB-Integration mit Adobe Sign und unterstützt DocuSign für E-Signaturen.

* Der Dienst unterstützt auch Adobe Sign-Rollen. Sie können die Rollen im adaptiven Forms-Editor für Geschäftsbenutzer konfigurieren, um die Signatur-Workflows einfach zu konfigurieren.


## HTML5-Formulare

* Sie können eine Forms-Umgebung AEM 6.5 für folgende Zwecke verwenden:

   * Rendern Sie Ihre XDP-basierten Formulare als HTML5 Forms. Der Dienst unterstützt keine HTML5 Forms (Mobile Forms).

   * Daten offline erfassen und synchronisieren, wenn Sie das nächste Mal online sind mit [AEM Forms Workspace](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) App.

## Interaktive Kommunikation

* Sie können Kommunikations-APIs verwenden, um personalisierte Dokumente bei Bedarf oder in Stapeln auf Forms as a Cloud Service zu erstellen. Sie können eine AEM 6.5 Forms-Umgebung für Anwendungsfälle der interaktiven Kommunikation und der Benutzeroberfläche für Agenten verwenden.


