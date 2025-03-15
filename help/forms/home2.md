---
title: Einführung in  [!DNL AEM Forms]  as a Cloud Service
description: Entdecken Sie AEM Forms, um einsatzbereite Formulare zu entwerfen, Geschäftsprozess-Workflows zu erstellen und Dokumentendienste zum Erstellen und Schützen von Dokumenten zu verwenden.
landing-page-description: Erfahren Sie, wie Sie Formulare in AEM as a Cloud Service verwenden.
role: Admin, Developer, User
feature: Adaptive Forms, Release Information
hide: true
hidefromtoc: true
source-git-commit: a5bbcd19b41b3aeff94f900da13e98de65651f8c
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 7%

---


# AEM Forms as a Cloud Service {#introduction}

<!-- Version Navigation -->
<div class="version-selector">
  <p><strong>Suchen Sie eine Dokumentation für eine andere Version?</strong></p>
  <ul>
    <li><a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/home.html">Dokumentation zu AEM 6.5 Forms</a></li>
    <li><strong>AEM Forms as a Cloud Service</strong> (aktuell)</li>
  </ul>
</div>

## Was ist AEM Forms as a Cloud Service?

AEM Forms as a Cloud Service ist die Cloud-native Lösung von Adobe zum Erstellen, Verwalten und Bereitstellen digitaler Formulare und Kommunikationen. Damit können Unternehmen komplexe Transaktionen über den gesamten Kunden-Journey in einfache, digitale Erlebnisse umwandeln.

<div class="card-container">
  <div class="card">
    <div class="card-header">
      <h3>Adaptive Formulare</h3>
    </div>
    <div class="card-body">
      <p>Erstellen Sie responsive, dynamische Formulare, die sich an Benutzereingaben und Gerätetypen anpassen:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components">Erstellen eines adaptiven Forms</a> - Erstellen Sie Formulare, die sich automatisch an verschiedene Bildschirmgrößen und Benutzereingaben anpassen</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type">Rich-Komponentenbibliothek</a> - Verwenden Sie eine Vielzahl von Eingabefeldern und UI-Komponenten</li>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components">Adaptive Forms formatieren</a> - Wenden Sie konsistentes Branding und visuelles Design auf Ihre Formulare an</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=de">Verwenden von vordefinierten Designs und Vorlagen</a> - Beschleunigen der Entwicklung mit einsatzbereiten Komponenten</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/rule-editor-core-components/rule-editor-core-components">Formularvalidierung</a> - Client- und Server-seitige Validierungsregeln implementieren</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/configure-submit-actions-core-components.html">Übermittlungsaktionen</a> Konfigurieren, was passiert, wenn Benutzer Formulare senden</li>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/generate-document-of-record-core-components">Datensatzdokument</a> - Erstellen permanenter Datensätze mit den übermittelten Formulardaten</li>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/create-or-add-an-adaptive-form-to-aem-sites-page">Forms zu AEM Sites-Seiten hinzufügen</a> - Nahtlose Integration von Formularen in Ihre Website</li>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/integrate/services/embed-adaptive-form-core-components-external-web-page">Forms zu den Webseiten von Drittanbietern hinzufügen</a> - Nahtlose Integration von Formularen in Ihre Website</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Edge Delivery Services für Forms</h3>
    </div>
    <div class="card-body">
      <p>Erstellen und Bereitstellen von Formularen mit Edge Delivery Services:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/overview">Übersicht über Edge Delivery Forms</a> - Erfahren Sie mehr über Formulare mit Edge Delivery Services</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/universal-editor/getting-started-universal-editor">Universeller Editor für Forms</a> - Erstellen von Formularen mit dem universellen Editor für WYSIWYG</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial">Dokumentenbasiertes Authoring</a> - Erstellen von Formularen mit Microsoft Word oder Google Docs</li>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/universal-editor/style-theme-forms">Stil von Edge Delivery Forms</a> - Anwenden benutzerdefinierter Stile auf Ihre Formulare</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Headless-Forms</h3>
    </div>
    <div class="card-body">
      <p>Bereitstellen von Formularerlebnissen über jeden Kanal oder jedes Frontend-Framework:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de">Einführung in Headless-Forms</a> - Erfahren Sie mehr über den Headless-Ansatz für Formulare</li>
        <li>Erstellen von Formularen mit React- oder anderen Frontend-Frameworks</li>
        <li>Integrieren von Formularen in Mobile Apps, Websites und Chat-Anwendungen</li>
        <li>Nutzen vorhandener UI-Komponenten mit Formularfunktionen</li>
        <li>Beibehaltung der Backend-Formularlogik bei gleichzeitiger Frontend-Flexibilität</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Kommunikations-APIs</h3>
    </div>
    <div class="card-body">
      <p>Programmgesteuertes Generieren, Bearbeiten und Schützen von Dokumenten:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?lang=de#document-generation">Personalisierte Kommunikation generieren</a> - Erstellen benutzerdefinierter Dokumente basierend auf Vorlagen und Daten</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?lang=de#document-manipulation">Zusammenführen und Bearbeiten von PDFs</a> - Kombinieren, Aufteilen und Ändern von PDF-Dokumenten</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-to-and-validate-pdfa-compliant-documents">Erstellen von PDF/A</a>Dokumenten: Erzeugen von Dokumenten in Archivierungsqualität</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html#flatten-interactive-pdf-documents">Reduzieren interaktiver PDFs</a> - Konvertieren interaktiver Felder in nicht interaktive Elemente</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#signature-apis">Signaturen anwenden</a> - Sichern von Dokumenten mit Signaturen</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#encryption-apis">Verschlüsseln und Entschlüsseln von PDFs</a> - Schützen sensibler Dokumentinhalte</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">XDP in PostScript konvertieren</a> - Transformieren von XDP-Dokumenten in das PostScript-Format</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">XDP in PCL konvertieren</a> - Konvertieren von XDP-Dokumenten in die Printer-Befehlssprache</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">XDP in ZPL konvertieren</a> - Transformieren von XDP-Dokumenten in Zebra-Drucksprache</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-to-and-validate-pdfa-compliant-documents">PDF in PDF/A-Standards konvertieren</a> - Erstellen archivierungskonformer PDF-Dokumente</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-pdf-documents-to-pdf-x-standards">Digitale Signaturen hinzufügen</a> - Digitales Signieren von Dokumenten für die Authentifizierung</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Workflow-Automatisierung</h3>
    </div>
    <div class="card-body">
      <p>Automatisieren Sie Geschäftsprozesse mit Formularen und Dokumenten:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#assign-task-step">Geschäftsprozesse erstellen</a> - Weiterleiten von Formularen für Genehmigung oder Feedback, Workflows nach der Übermittlung oder Backend-Workflows zur Verwaltung von Registrierungsprozessen</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#sign-document-step">Verwenden von Adobe Sign in einem AEM-Workflow</a> - Senden eines Dokuments zum Signieren </li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#generate-document-of-record-step">Generieren eines Datensatzdokuments </a> - Bei Bedarf oder bei Formularübermittlung generieren</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>E-Signaturen</h3>
    </div>
    <div class="card-body">
      <p>Hinzufügen rechtsverbindlicher elektronischer Signaturen zu Ihren Formularen und Dokumenten:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms">Adobe Sign-Integration</a> - Aktivieren von E-Signaturen in adaptiven Forms</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?lang=de#sign-document-step">E-Signaturen zu Workflows hinzufügen</a> - Signaturschritte in Geschäftsprozesse einschließen</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?lang=de#generate-document-of-record-step">Datensatzdokument mit Signaturen</a> - Generieren signierter Datensätze für Formularübermittlungen</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Analytics und Insights</h3>
    </div>
    <div class="card-body">
      <p>Gewinnen Sie Einblicke in die Verwendung und Leistung von Formularen:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.html?lang=de">Aktivieren von Adobe Analytics</a> - Verfolgen der Formularnutzung und -leistung</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-aem-forms-with-adobe-analytics.html?lang=de">Manuelle Analytics-Integration</a> - Einrichten der Analyse für das detaillierte Tracking</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/view-understand-aem-forms-analytics-reports.html">Analytics-Berichte anzeigen</a> - Analysieren der Formularleistung und des Benutzerverhaltens</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>-Datenintegration</h3>
    </div>
    <div class="card-body">
      <p>Verbinden von Formularen mit vorhandenen Datenquellen und Systemen:</p>
      <h4>Adobe-Ökosystem</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign">Adobe Sign</a> - Zum Senden elektronischer Signaturen über Adobe Sign</li>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-adaptive-form-with-market-engage/integrate-form-to-marketo-engage">Marketo Engage</a> - Integrieren von Formularen in Adobe Marketo Engage</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#invoke-an-aem-workflow">AEM-Workflow</a> - Trigger-AEM-Workflows mit Formularübermittlungen</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#workfront-fusion">Workfront</a> - Senden eines adaptiven Formulars an Adobe Workfront Fusion</li>
      </ul>
      <h4>Microsoft-Integrationen</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics">Microsoft Dynamics 365</a> - Integration mit Microsoft CRM</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html?lang=de">Azure Blob Storage</a> - Speichern von Formulardaten im Cloud-Speicher von Microsoft</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/connect-to-sharepoint/connect-forms-to-sharepoint-document-library">SharePoint-Dokumentbibliothek</a> - Mit Microsoft SharePoint-Dokumentbibliotheken verbinden</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#connect-af-sharepoint-list">SharePoint-Liste</a> - Mit Microsoft SharePoint-Liste verbinden</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#submit-to-onedrive">OneDrive</a> - Verbindung mit Microsoft OneDrive herstellen</li>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/integrate/services/forms-microsoft-power-automate-integration">Microsoft Power Automate</a> - Trigger Microsoft Power Automate-Flüsse</li>
      </ul>
      <h4>Andere Datenquellen und Services</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/aem-forms-salesforce-integration">Salesforce</a> - Integration mit Salesforce CRM</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#submit-to-rest-endpoint">RESTful-</a>: Herstellen einer Verbindung zu einem beliebigen REST-API-Endpunkt</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-data-sources.html?lang=de">RDBMS-Datenbanken</a> - Verbindung mit relationalen Datenbanken</li>
        <li><a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#send-email">E-</a>: Senden von Formulardaten per E-Mail</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/introduction-to-forms-portal/save-core-component-based-form-as-draft">Forms Portal</a> - An Forms Portal senden, um Entwurf zu speichern</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#send-pdf-via-email">PDF per E-Mail </a> - Senden einer PDF-Version des gesendeten Formulars per E-Mail</li>
        <li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#submit-using-form-data-model">Senden mit Formulardatenmodell</a> - Senden von Daten mit einem Formulardatenmodell</li>
      </ul>
    </div>
  </div>
</div>

## Erste Schritte mit AEM Forms as a Cloud Service

<div class="card-container">
  <div class="card">
    <div class="card-header">
      <h3>Für Business-Anwender</h3>
    </div>
    <div class="card-body">
      <ol>
        <li><strong>Grundlegendes</strong>: Erfahren Sie mehr über <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/introduction-forms-authoring.html">Adaptive Forms</a> und wie sie Sie bei der Digitalisierung Ihrer Geschäftsprozesse unterstützen können.</li>
        <li><strong>Vorlagen erkunden</strong>: Durchsuchen Sie die <a href="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=de">vordefinierten Vorlagen und Designs</a> um einen Vorsprung bei Ihren Formularprojekten zu erhalten.</li>
        <li><strong>Erfahren Sie mehr über das Formular</strong>: Befolgen Sie die <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/introduction-forms-authoring.html?lang=de">Anleitung zum Erstellen von Formularen</a>, um Ihr erstes Formular zu erstellen.</li>
      </ol>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Für Entwickler</h3>
    </div>
    <div class="card-body">
      <ol>
        <li><strong>Ihre Umgebung einrichten</strong>: Konfigurieren Sie Ihre <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-local-development-environment.html?lang=de">lokale Entwicklungsumgebung</a> für AEM Forms.</li>
        <li><strong>Architektur kennenlernen</strong>: Die <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/aem-forms-cloud-service-architecture">Architektur von AEM Forms as a Cloud Service</a> verstehen.</li>
        <li><strong>APIs erkunden</strong>: Machen Sie sich mit den <a href="https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/"> verfügbaren APIs </a> SDKs für die Erweiterung und Integration von Forms vertraut.</li>
      </ol>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Für Administratoren</h3>
    </div>
    <div class="card-body">
      <ol>
        <li><strong>Einführung in Cloud Service</strong>: Befolgen Sie die <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service.html?lang=de">Onboarding-Handbuch</a>, um AEM Forms as a Cloud Service einzurichten.</li>
        <li><strong>Services konfigurieren</strong>: Einrichten von <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.html?lang=de">Integrationen mit anderen Adobe-Services</a> wie Adobe Analytics.</li>
        <li><strong>Migration von AEM 6.5</strong>: Wenn Sie von AEM 6.5 kommen, befolgen Sie die <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/migrate-to-forms-as-a-cloud-service.html">Migrationshandbuch</a> um zu Cloud Service zu wechseln.</li>
      </ol>
    </div>
  </div>
</div>

## Early Adopter-Funktionen

<div class="card">
  <div class="card-header">
    <h3>AEM Forms Early Access-Programm</h3>
  </div>
  <div class="card-body">
    <p>Das <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features">AEM Forms Early Access</a>Programm bietet exklusiven Zugriff auf hochmoderne Funktionen, bevor diese allgemein verfügbar sind, darunter:</p>
    <ul>
      <li><strong>AEM Forms-KI-Assistent (Gen-KI)</strong> - Schnellere Erstellung von Formularen mit KI-gestützten Vorschlägen</li>
      <li><strong>AEM Forms Workfront Fusion Connector</strong> - Automatisieren von Workflows, die durch Formularübermittlungen ausgelöst werden</li>
      <li><strong>Konversativer Forms</strong> - Erstellen von Chat-ähnlichen Formularerlebnissen auf jeder AEM Sites-Seite</li>
      <li><strong>WYSIWYG-Authoring für Edge Delivery</strong> - Erstellen von Formularen mit dem universellen Editor für Edge Delivery Services</li>
      <li><strong>AEM Forms-zu-Marketo-Connector</strong> - Integrieren von Formularübermittlungen mit Marketo Engage</li>
    </ul>
    <p>Eine vollständige Liste der Early-Access-Innovationen und eine detaillierte Dokumentation finden Sie auf der Seite <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features">AEM Forms Early-Access-Programm</a>.</p>
  </div>
</div>

<div class="cta-card">
  <h3>Bereit für den Einstieg?</h3>
  <p><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service">Beginnen Sie noch heute mit der </a> von AEM Forms as a Cloud Service und gestalten Sie das digitale Formularerlebnis Ihres Unternehmens um.</p>
</div>

<style>
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  margin-bottom: 30px;
}

.card {
  flex: 1 1 calc(50% - 20px);
  min-width: 300px;
  border: 1px solid #e1e1e1;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
}

.card-header {
  background-color: #f5f5f5;
  padding: 15px 20px;
  border-bottom: 1px solid #e1e1e1;
}

.card-header h3 {
  margin: 0;
  color: #2c2c2c;
  font-size: 1.25rem;
}

.card-body {
  padding: 20px;
  background-color: #ffffff;
}

.card-body ul, .card-body ol {
  margin-top: 10px;
  padding-left: 25px;
}

.card-body li {
  margin-bottom: 8px;
}

.cta-card {
  background-color: #f0f7ff;
  border-left: 4px solid #1473e6;
  padding: 20px;
  margin: 30px 0;
  border-radius: 4px;
}

.cta-card h3 {
  margin-top: 0;
  color: #1473e6;
}

.cta-card a {
  font-weight: bold;
  color: #1473e6;
}

@media (max-width: 768px) {
  .card {
    flex: 1 1 100%;
  }
}
</style>
