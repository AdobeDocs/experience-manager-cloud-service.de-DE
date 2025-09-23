---
title: Einführung in AEM Forms as a Cloud Service
description: Entdecken Sie die Funktionen von AEM Forms zum Erstellen adaptiver Formulare, Automatisieren von Workflows und Verwalten digitaler Dokumente. Komplette Plattform für formularbasierte Geschäftsprozesse.
landing-page-description: Erfahren Sie, wie Sie mit AEM Forms as a Cloud Service adaptive Formulare erstellen, Dokumente verarbeiten und Unternehmens-Workflows automatisieren können.
keywords: AEM Forms, adaptive Formulare, Formular-Builder, digitale Formulare, Workflow-Automatisierung, Dokumenten-Services, Formulardatenmodell
role: Admin, Developer, User
feature: Adaptive Forms, Release Information
hide: true
hidefromtoc: true
index: false
source-git-commit: 51d9fed937ea5f12544ed476974d2812843fb457
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 1%

---


# Einführung in AEM Forms as a Cloud Service {#introduction}



Adobe Experience Manager Forms as a Cloud Service bietet eine umfassende Plattform zum Erstellen, Verwalten und Optimieren von digitalen Formularerlebnissen. Unternehmen verwenden AEM Forms, um papierbasierte Prozesse zu digitalisieren, responsive Web-Formulare zu erstellen, Dokumenten-Workflows zu automatisieren und skaliert personalisierte Kommunikation bereitzustellen.

Die Plattform kombiniert Formularerstellungsfunktionen mit robusten Backend-Services, sodass Sie alles von einfachen Kontaktformularen bis hin zu komplexen mehrstufigen Geschäftsanwendungen erstellen können. Mit der Cloud-nativen Architektur erhalten Sie automatische Aktualisierungen, flexible Skalierung und Sicherheit auf Unternehmensniveau, ohne die Infrastruktur verwalten zu müssen.

In diesem Handbuch werden die Kernfunktionen vorgestellt, die sich um den gesamten Lebenszyklus des Formulars drehen, vom ersten Entwurf bis hin zur fortlaufenden Optimierung.

## Neue Funktionen in AEM Forms {#whats-new}

**Die Highlights der neuesten Version:**

- **Datums- und Uhrzeiteingabekomponente** - Verbesserte Benutzereingabe mit Kalender- und Uhrenschnittstelle für eine präzise Datums- und Uhrzeitauswahl
- **Verbesserte Sicherheit beim Hochladen von Dateien** - Automatische Validierung und Überprüfung von Inhaltstypen, um nicht unterstützte Dateiformate zu verhindern
- **Verbesserte Fehlerbehandlung** - Besseres Debugging mit spezifischen Fehler-Codes für benutzerdefinierte Übermittlungsaktionen
- **Verbesserungen des Datensatzdokuments** - Option zum Ausschließen ausgeblendeter Felder für eine sauberere Dokumenterstellung

**Funktionen der Vorabversion:**

- **AFP-Formatunterstützung** - Druckfunktionen auf Unternehmensniveau mit Kommunikations-APIs
- **Verbesserungen des Regeleditors** - Moderne JavaScript-Unterstützung, dynamische Variablen und kontextabhängige Bereichsregeln
- **Verbesserte Validierungsmethoden** - Validierung auf Bedienfeld-, Feld- und Formularebene mit verbesserter Flexibilität

[Anzeigen der vollständigen Versionshinweise →](/help/release-notes/release-notes-cloud/release-notes-current.md#forms)

## EARLY ACCESS-Programm {#early-access}

Erhalten Sie exklusiven Zugriff auf hochmoderne AEM Forms-Innovationen, bevor diese allgemein verfügbar sind.

**Aktuelle Early-Access-Funktionen:**

- **AEM Forms AI Assistant** - Generative KI für die automatisierte Formularerstellung, Bedienfelderstellung und Optimierungsempfehlungen
- **Komponente „Freihandsignatur** - Direkte Signaturerfassung in Formularen mit Maus, Stift oder Touchscreen
- **Direkte API-Integration** - Verbinden mit APIs im Regeleditor, ohne dass eine Einrichtung des Formulardatenmodells erforderlich ist
- **Forms-Optimierung** - Vorschläge für eine KI-gestützte Leistungsanalyse und eine Verbesserung der Konversionsrate

**Am Programm teilnehmen:**
Seien Sie unter den Ersten, die Zugang zu Innovationen erhalten und die Zukunft von AEM Forms mitgestalten.

[→ anfordern](mailto:aem-forms-ea@adobe.com) | [Weitere Informationen →](/help/forms/early-access-ea-features.md)


## Kernfunktionen {#core-capabilities}

AEM Forms unterstützt das vollständige Journey digitaler Formulare, von der ersten Erstellung bis zur fortlaufenden Optimierung. Jede Phase baut auf der vorherigen auf und schafft eine umfassende Plattform für formularbasierte Geschäftsprozesse.

**AEM Forms Workflow-Journey:**

    ERSTELLEN → STEUERN → VERÖFFENTLICHEN → ERFASSEN → PROZESSES → INTEGRIEREN → VERFOLGEN → ARCHIVIEREN → VERBESSERN
    ↓        ↓        ↓         ↓         ↓         ↓          ↓       ↓        ↓ 
     Design   Überprüfung   Bereitstellen   einsammeln   Handgriff   Verbinden   Monitorspeicher   Optimieren
    ↑                                                                              ↓
    ←←←←←←←←←←←←←←← Continuous Improvement Loop ←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←

### Erstellen: Formularentwurf und -entwicklung {#create}

Erstellen Sie adaptive Formulare mithilfe mehrerer Authoring-Ansätze, die auf verschiedene Anforderungen und technische Anforderungen zugeschnitten sind.

**Visual Form Builder**
Entwerfen Sie responsive Formulare über Drag-and-Drop-Schnittstellen mithilfe von [Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md), [Foundation-](/help/forms/creating-adaptive-form.md) oder [Edge Delivery Services](/help/edge/docs/forms/overview.md). Der visuelle Editor bietet sofortiges Feedback bei gleichzeitiger Beibehaltung eines sauberen, semantischen Markups, das geräteübergreifend und über Hilfstechnologien hinweg funktioniert.

**Dokumentenbasiertes Authoring**
Erstellen Sie Formulare mit bekannten Tools wie Microsoft Excel bis [Edge Delivery Services](/help/edge/docs/forms/overview.md). Dieser Ansatz ermöglicht es Inhaltsautorinnen und -autoren, ohne technisches Know-how leistungsstarke Formulare zu erstellen und gleichzeitig außergewöhnliche Google Lighthouse-Werte zu erzielen.

**Vorlagen und Designs**
Beschleunigen Sie die Formularerstellung mithilfe vordefinierter [Vorlagen](/help/forms/template-editor-core-components.md) die die Struktur und den anfänglichen Inhalt definieren. Wenden Sie konsistentes Branding mit [Designs](/help/forms/using-themes-in-core-components.md) an, die visuelle Stile für mehrere Formulare steuern, um die Designkonsistenz sicherzustellen und die Entwicklungszeit zu verkürzen.

**Datenintegrationen**
Verbinden von Formularen mit Backend-Systemen während der Design-Phase. Das [Formulardatenmodell](/help/forms/create-form-data-models.md) bietet eine einheitliche Schnittstelle für mehrere Datenquellen, die [Vorausfüllen](/help/forms/prepopulate-adaptive-form-fields.md), [Validierungsregeln](/help/forms/rule-editor-core-components.md) und einen nahtlosen Datenfluss zwischen Formularen und Geschäftssystemen ermöglicht.

**Validierungen und Bedingungslogik**
Implementieren Sie [Bedingungslogik](/help/forms/rule-editor-core-components.md) progressive Offenlegung und adaptive Validierung, um Benutzer durch komplexe Prozesse zu führen. [Mit der Funktion „Speichern und ](/help/forms/save-core-component-based-form-as-draft.md)&quot; können Benutzer Formulare sitzungsübergreifend ausfüllen.

**HTML5 Forms**
XFA-basierte Formulare für Mobilgeräte und ältere Browser [&#128279;](/help/forms/introductionhtml5.md)HTML5-Formulare“ rendern. HTML5 Forms bietet ein natives mobiles Erlebnis ohne Plug-ins, während die Formularlogik und die Validierung aus XDP-Originalvorlagen beibehalten werden.

**Interaktive Kommunikation**
Erstellen Sie dokumentorientierte Kommunikationen wie Auszüge, Rechnungen und Benachrichtigungen mit einem visuellen Editor. [Interaktive Kommunikation](/help/forms/introduction-to-interactive-communication.md) Kombinieren Sie statische Inhalte mit dynamischen Daten, um personalisierte Kommunikation über Print- und digitale Kanäle zu generieren.

### Governance: Überprüfung und Einhaltung {#govern}

Einführung von Aufsichts- und Genehmigungsprozessen, um sicherzustellen, dass die Formulare den organisatorischen Standards und rechtlichen Anforderungen entsprechen.

**Workflow-basierte Genehmigungen**
Routing von Formularentwürfen durch mehrstufige Prüfprozesse mit rollenbasierten Zuweisungen. Stakeholder können Formulare [überprüfen](/help/forms/create-reviews-forms.md) [ (kommentieren](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) und genehmigen, bevor sie veröffentlicht werden. Dabei bleiben Qualitätskontrolle und Compliance-Überwachung mithilfe von [AEM-Workflows](/help/forms/aem-forms-workflow.md).

**Versionsverwaltung**
Verfolgen Sie Formularversionen und pflegen Sie Audit-Trails zur Einhaltung von Vorschriften. Die integrierte [Versionierung](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) stellt sicher, dass Sie Änderungen zurücksetzen, Iterationen vergleichen und historische Datensätze für Compliance-Audits verwalten können.

**Zugriffssteuerung und Berechtigungen**
Definieren Sie granulare Berechtigungen für die Erstellung, Bearbeitung und Veröffentlichung von Formularen. [Rollenbasierter Zugriff](/help/forms/forms-groups-privileges-tasks.md) stellt sicher, dass nur autorisierte Benutzer Formulare ändern können, während die Aufgabentrennung für sensible Geschäftsprozesse beibehalten wird.

### Veröffentlichung: Multi-Channel-Verteilung {#publish}

Stellen Sie Formulare über mehrere Kanäle und Touchpoints bereit, um Benutzer überall zu erreichen.

**Omni-Channel-Publishing**
Veröffentlichen von Formularen in [AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md), eigenständigen Webseiten, mobilen Anwendungen oder [Einbetten in Drittanbietersysteme](/help/forms/embed-adaptive-form-core-components-external-web-page.md). Single-Source-Publishing sorgt für Konsistenz bei gleichzeitiger Anpassung an unterschiedliche Kanalanforderungen.

**Lokalisierung und Personalization**
Stellen Sie Formulare mithilfe der Übersetzungs-Workflows von [AEM in mehreren Sprachen bereit](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md) wobei sowohl [von links nach rechts als auch von rechts nach links unterstützt ](/help/forms/right-left-languages.md). Integration mit Adobe Target zur Personalisierung von Formularerlebnissen basierend auf Benutzersegmenten, Verhalten oder kontextuellen Daten.

**Leistungsoptimierung**
Nutzen Sie Edge Delivery Services für extrem schnelles Laden von Formularen und optimale SEO-Leistung. Netzwerke zur Inhaltsbereitstellung sorgen für globale Barrierefreiheit mit minimaler Latenz.

**Forms Portal**
Erstellen Sie zentralisierte Formular-Repositorys, in denen Benutzer Formulare finden, darauf zugreifen und sie verwalten können. [Forms Portal](/help/forms/configure-forms-portal.md) bietet Suchfunktionen, Formularkategorisierung, Entwurfsverwaltung und Sendungsverfolgung in einer zentralen Oberfläche für ein optimiertes Benutzererlebnis.

### Erfassen: Benutzererlebnis und Datenerfassung {#capture}

Optimieren Sie das Ausfüllen des Formulars, um die Abschlussraten und die Datenqualität zu maximieren.

**Responsives Design**
Forms passt sich automatisch an verschiedene Bildschirmgrößen und Eingabemethoden an. Touch-optimierte Steuerelemente, Tastaturnavigation und die Kompatibilität mit Sprachausgaben stellen [Barrierefreiheit](/help/forms/creating-accessible-adaptive-forms.md) für alle Benutzertypen sicher.

**Digitale Signaturen**
Integration von [Adobe Sign](/help/forms/working-with-adobe-sign.md) für rechtsverbindliche elektronische Signaturen im Formularerlebnis. Benutzer können Dokumente signieren, ohne das Formular zu verlassen, was die Genehmigungsprozesse optimiert und den Abbruch reduziert.

**Übermittlungsaktionen**
Konfigurieren Sie [Übermittlungsaktionen](/help/forms/configure-submit-actions-core-components.md) um festzulegen, was passiert, wenn Benutzer Formulare ausfüllen und senden. Weiterleiten von Daten an E-Mail-Adressen, Datenbanken, Workflows oder externe Systeme bei gleichzeitiger Bereitstellung von sofortigem Feedback und Bestätigung für Benutzer.

### Prozess: Handhabung von Übermittlungen und Routing {#process}

Verarbeiten Sie Formularübermittlungen mit robusten Verarbeitungs-, Validierungs- und Routing-Funktionen.

**Datenvalidierung und -verarbeitung**
Stellen Sie die Datenintegrität durch Server-seitige Validierung und automatisierte Verarbeitungsregeln sicher. Transformieren, Validieren und Weiterleiten gesendeter Daten beim Generieren von Quittungen, Bestätigungen oder Folgematerialien für Benutzer.

**Kommunikations-API**
Programmgesteuertes Generieren, Bearbeiten und Schützen von Dokumenten über [RESTful-APIs](/help/forms/aem-forms-cloud-service-communications-introduction.md). Erstellen Sie PDFs, druckfertige Formate, stellen Sie Dokumente zusammen, wenden Sie digitale Signaturen an und verarbeiten Sie umfangreiche [Batch-Vorgänge](/help/forms/aem-forms-cloud-service-communications-batch-processing.md) für Dokumenten-Workflows im Unternehmensmaßstab.

**Datensatzdokument**
Automatisches Generieren von PDF-Datensätzen von Formularübermittlungen zur Compliance und Benutzerbestätigung. [Datensatzdokument](/help/forms/generate-document-of-record-core-components.md) erstellt formatierte, druckbare Versionen ausgefüllter Formulare mit übermittelten Daten und stellt eine offizielle Dokumentation für Transaktionen und rechtliche Anforderungen bereit.

**Workflow-Orchestrierung**
Trigger komplexer Geschäftsprozesse auf der Grundlage von Formularübermittlungen. Daten durch Validierungsketten leiten, Aufgaben bestimmten Benutzern zuweisen und Routinevorgänge automatisieren und dabei Audit-Trails pflegen.

**Fehlerbehandlung und Wiederherstellung**
Integrierte Wiederholungsmechanismen und Fallback-Verarbeitung stellen sicher, dass keine Übermittlungen verloren gehen. Eine umfassende Protokollierung hilft bei der Fehlerbehebung und der Einhaltung von Service Level Agreements.

### Integrieren: Backend-Konnektivität {#integrate}

Verbinden von Formularen mit vorhandenen Geschäftssystemen und Datenquellen für einen nahtlosen Informationsfluss.

**Vorkonfigurierte Connectoren**
Native Integration mit [Salesforce](/help/forms/configure-salesforce.md), [Microsoft Dynamics](/help/forms/configure-msdynamics.md), [SharePoint](/help/forms/connect-forms-to-sharepoint-document-library.md) und Adobe Experience Cloud-Lösungen. Vorkonfigurierte Connectoren verkürzen die Entwicklungszeit und sorgen gleichzeitig für eine zuverlässige Datensynchronisation.

**RESTful-API-Integration**
Stellen Sie über RESTful-APIs über [Übermittlungsaktionen) oder ](/help/forms/configure-submit-action-restpoint.md)Datenintegration[ eine Verbindung zu einem Service her, auf ](/help/forms/data-integration.md) über Web zugegriffen werden kann. Das Formulardatenmodell abstrahiert die Integrationskomplexität und bietet eine konsistente Schnittstelle unabhängig von der zugrunde liegenden Systemarchitektur.

**Echtzeit-Datenaustausch**
Bidirektionalen Datenfluss zwischen Formularen und Geschäftssystemen aktivieren. Formulare aus vorhandenen Datensätzen vorab ausfüllen, mit Live-Daten validieren und mehrere Systeme gleichzeitig bei der Übermittlung durch umfassende [Datenintegration](/help/forms/data-integration.md) aktualisieren

### Tracking: Analyse und Leistungsüberwachung {#track}

Verstehen Sie die Formularleistung und das Benutzerverhalten durch umfassende Analysen und Überwachung.

**Formularanalyse**
Verfolgen Sie Abschlussraten, Abbruchmuster und Interaktionen auf Feldebene über die [Adobe Analytics-Integration](/help/forms/integrate-aem-forms-with-adobe-analytics.md). Identifizieren Sie Reibungspunkte, messen Sie Konversionstrichter und verstehen Sie das Benutzerverhalten über verschiedene Segmente hinweg.

**Leistungsüberwachung**
Überwachen Sie Ladezeiten, Erfolgsraten bei der Übermittlung und Systemleistung von Formularen. Echtzeit-Dashboards bieten Einblicke in technische Konsistenz- und Benutzererlebnismetriken.

**Business Intelligence**
Berichte zur Formularnutzung, zum Übermittlungsvolumen und zur Prozesseffizienz generieren. Analytics liefert Informationen zu Kapazitätsplanung, Optimierung des Benutzererlebnisses und Verbesserungen der Geschäftsprozesse.

**Transaktionsberichte**
Überwachen Sie die API-Nutzung, das Volumen der Dokumenterstellung und [abrechnungsfähigen Transaktionen](/help/forms/transaction-reports-billable-apis.md) in Ihrer AEM Forms-Bereitstellung. Verfolgen Sie Verbrauchsmuster, optimieren Sie die Ressourcenzuweisung und halten Sie die Einhaltung von nutzungsbasierten Lizenzanforderungen aufrecht.

### Archiv: Dokumentenmanagement und Compliance {#archive}

Sicheres Speichern und Verwalten von Formularübermittlungen und generierten Dokumenten für eine langfristige Aufbewahrung und Compliance.

**Dokumentenspeicher**
Speichern Sie generierte Dokumente und Formularübermittlungen im Digital Asset Management-System von AEM oder integrieren Sie sie in externe Dokumentenspeicher wie [SharePoint](/help/forms/configure-submit-action-sharepoint.md), [OneDrive](/help/forms/configure-submit-action-onedrive.md) oder [Azure Blob Storage](/help/forms/configure-submit-action-azure-blob-storage.md).

**Compliance und Kundenbindung**
Implementieren Sie Richtlinien zur Datenaufbewahrung, die den gesetzlichen Anforderungen, einschließlich DSGVO, CCPA und HIPAA, entsprechen. [Automatisierte Archivierungsprozesse](/help/forms/aem-forms-cloud-service-communications-batch-processing.md) stellen sicher, dass Dokumente für erforderliche Zeiträume aufbewahrt und bei Bedarf sicher entsorgt werden.

**Sicherheit und Zugriffskontrolle**
Wenden Sie Verschlüsselung, digitale Signaturen und [rollenbasierte Zugriffssteuerungen](/help/forms/forms-groups-privileges-tasks.md) auf archivierte Dokumente an. Audit-Protokolle verfolgen den Dokumentzugriff und die Änderungen für Compliance-Berichte und Sicherheitsüberwachung.

### Verbesserung: Optimierung und Verbesserung {#improve}

Kontinuierliche Optimierung der Formularleistung und des Benutzererlebnisses durch datengesteuerte Einblicke und Tests.

**A/B-Testintegration**
Verwenden Sie Adobe Target, um verschiedene Formularlayouts, Feldanordnungen und Benutzerflüsse zu testen. Mithilfe der statistischen Analyse können Sie die effektivsten Ansätze für verschiedene Benutzersegmente und Anwendungsfälle ermitteln.

**Analytics-gesteuerte Optimierung**
Analyse der Daten zum Benutzerverhalten, um Verbesserungsmöglichkeiten zu identifizieren. [Anzeigen und Verstehen von Analyseberichten](/help/forms/view-understand-aem-forms-analytics-reports.md) für Heatmap-, Feldinteraktionsanalyse und Mustererkennung bei Abbrüchen, um Informationen zu Verbesserungen beim iterativen Design zu erhalten.

**Iterative Verbesserung**
Implementieren Sie kontinuierliche Verbesserungsprozesse basierend auf Benutzer-Feedback, Leistungsmetriken und Geschäftsanforderungen. [Versionskontrolle](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) und Rollback-Funktionen ermöglichen sicheres Experimentieren und schnelle Iteration.

## Erste Schritte {#getting-started}

Welchen Ansatz Sie wählen, hängt von Ihren unmittelbaren Bedürfnissen und langfristigen Zielen ab.

### Schnellstart: Einfache Forms {#quick-start}

Wählen Sie Ihren bevorzugten Authoring-Ansatz basierend auf Ihrem technischen Hintergrund und Ihren Leistungsanforderungen:

**Visual Form Building:**

1. **[Erstellen adaptiver Formulare mit Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md)** für moderne, responsive Formulare
2. **[Konfigurieren von Übermittlungsaktionen](/help/forms/configure-submit-actions-core-components.md)** zur Verarbeitung von Formulardaten
3. **[Formulare in AEM Sites einbetten](/help/forms/embed-adaptive-form-aem-sites.md)** oder über direkte Links freigeben

**Dokumentenbasiertes Authoring:**

1. **[Erstellen von Formularen mit Excel](/help/edge/docs/forms/create-forms.md)** mit Edge Delivery Services für leistungsstarke Formulare
2. **[In Edge Delivery veröffentlichen](/help/edge/docs/forms/publish-forms.md)** für optimale Ladegeschwindigkeiten und SEO

**Legacy-Formularunterstützung:**

- **[HTML5 Forms](/help/forms/introductionhtml5.md)** für die für Mobilgeräte optimierte XFA-Formularwiedergabe

### Erweiterte Implementierung: Geschäftsprozesse {#advanced-implementation}

Für komplexe Anforderungen, die mehrere Systeme, Dokumenterstellungs- und Genehmigungs-Workflows umfassen:

**Datenintegration und Workflows:**

1. **[Einrichten von Formulardatenmodellen](/help/forms/create-form-data-models.md)** zum Verbinden von Backend-Systemen
2. **[Entwerfen von Workflow-Prozessen](/help/forms/aem-forms-workflow.md)** für Genehmigung und Routing
3. **[Konfigurieren von](/help/forms/integrate-aem-forms-with-adobe-analytics.md)** zur Leistungsmessung

**Document Services und Kommunikation:**

1. **[Implementieren von Kommunikations-APIs](/help/forms/aem-forms-cloud-service-communications-introduction.md)** für die automatisierte Dokumenterstellung
2. **[Interaktive Kommunikation erstellen](/help/forms/introduction-to-interactive-communication.md)** für personalisierte Anweisungen und Benachrichtigungen
3. **[Einrichten von Forms Portal](/help/forms/configure-forms-portal.md)** für die zentralisierte Formularverwaltung

### Enterprise-Bereitstellung: Skalierbarkeit und Governance {#enterprise-deployment}

Für organisationsweite Bereitstellungen, die Governance, Compliance und Überwachung erfordern:

**Architektur und Governance:**

1. **[Überprüfen von Architekturmustern](/help/forms/aem-forms-cloud-service-architecture.md)** für eine skalierbare Bereitstellung
2. **[Konfigurieren der Benutzerverwaltung](/help/forms/forms-groups-privileges-tasks.md)** und Zugriffssteuerungen
3. **[Einrichten von Entwicklungs-Workflows](/help/forms/setup-local-development-environment.md)** für die Zusammenarbeit mit Teams

**Migration und Überwachung:**

1. **[Planen von Migrationsstrategien](/help/forms/migrate-to-forms-as-a-cloud-service.md)** aus vorhandenen Systemen
2. **[Transaktionsüberwachung implementieren](/help/forms/transaction-reports-billable-apis.md)** für Nutzungsverfolgung und Compliance

<details>
<summary><strong>❓ Häufig gestellte Fragen</strong></summary>

**Was ist ein Formular-Builder?**
Ein Formular-Builder ist ein Tool, mit dem Sie digitale Formulare ohne Programmierung erstellen können. Sie können Formulare mithilfe von Drag-and-Drop-Schnittstellen entwerfen, Felder wie Textfelder und Dropdown-Listen hinzufügen und sie online veröffentlichen, um Daten von Benutzern zu erfassen.

**Wie erstelle ich ein Online-Formular?**
Mit AEM Forms können Sie adaptive Formulare mithilfe von Kernkomponenten über einen visuellen Drag-and-Drop-Editor erstellen, leistungsstarke Formulare mit Edge Delivery Services erstellen oder Foundation-Komponenten für etablierte Workflows verwenden. Wählen Sie zunächst eine Vorlage aus, fügen Sie Formularfelder hinzu, konfigurieren Sie Datenverbindungen und veröffentlichen Sie über mehrere Kanäle hinweg.

**Was macht ein gutes Online-Formular aus?**
Gute Online-Formulare reagieren auf Mobilgeräte, laden schnell, haben klare Beschriftungen, verwenden eine logische Feldreihenfolge, beinhalten Validierungen, um Fehler zu vermeiden, und geben Benutzern beim Übermitteln sofortiges Feedback.

**Kann ich Formulare in andere Geschäftssysteme integrieren?**
Ja, moderne Formularersteller bieten umfangreiche Integrationsfunktionen. Sie können Formulare mit CRM-Systemen, E-Mail-Marketing-Plattformen, Datenbanken, Cloud-Speicher und Tools zur Workflow-Automatisierung verbinden, um Ihre Geschäftsprozesse zu optimieren.

**Sind Online-Formulare sicher?**
Professionelle Formularersteller verfügen über Sicherheitsfunktionen auf Unternehmensniveau wie Datenverschlüsselung, sichere Datenübertragung, Zugriffskontrollen und die Einhaltung von Vorschriften wie DSGVO, HIPAA und CCPA zum Schutz sensibler Informationen.

**Wie füge ich meinen Formularen E-Signaturen hinzu?**
Digitale Signaturen können mit Adobe Sign oder anderen E-Signatur-Anbietern direkt in Formulare integriert werden. Dadurch können Benutzer Dokumente im Formularerlebnis signieren, sodass keine separaten Signatur-Workflows mehr erforderlich sind und der Formularabbruch reduziert wird.

**Können Formulare automatisch PDF-Dokumente generieren?**
Ja, moderne Formularplattformen können beim Senden von Formularen automatisch PDF-Quittungen, Bestätigungen oder Datensatzdokumente generieren. Dies ist für die Einhaltung von Vorschriften, die Aufbewahrung von Aufzeichnungen und die sofortige Bestätigung der Benutzer unerlässlich.

**Wie kann ich die Formularleistung und -analysen verfolgen?**
Die Formularanalyse hilft Ihnen, Abschlussraten, Abbruchmuster und das Benutzerverhalten zu verstehen. Die Integration mit Analyseplattformen wie Adobe Analytics bietet Einblicke, welche Felder Reibungspunkte verursachen und wie Konversionsraten optimiert werden können.

**Was ist die Automatisierung von Formular-Workflows?**
Durch die Automatisierung des Formular-Workflows werden Übermittlungen durch Genehmigungsprozesse weitergeleitet, Teammitgliedern werden Aufgaben zugewiesen, und es werden Trigger-Aktionen in anderen Geschäftssystemen ausgeführt. Dies eliminiert die manuelle Verarbeitung und stellt eine konsistente Verarbeitung der Formulardaten sicher.

**Wie mache ich Formulare für Benutzer mit Behinderungen barrierefrei?**
[Barrierefreie Formulare](/help/forms/creating-accessible-adaptive-forms.md) umfassen eine ordnungsgemäße Beschriftung, Tastaturnavigation, Kompatibilität mit Sprachausgaben und die Einhaltung der WCAG-Richtlinien. Dadurch wird sichergestellt, dass alle Benutzer Formulare unabhängig von ihren Fähigkeiten oder Hilfstechnologien ausfüllen können.

**Wie viel kosten Formularersteller?**
Die Preise für AEM Forms as a Cloud Service hängen von Ihren spezifischen Anforderungen, dem Nutzungsvolumen und den Funktionsanforderungen ab. Wenden Sie sich an den Adobe-Vertrieb oder Ihren Adobe-Support-Mitarbeiter, um detaillierte Preisinformationen zu erhalten und eine auf Ihr Unternehmen zugeschnittene Lösung zu besprechen.

</details>

## Nächste Schritte {#next-steps}

Erkunden Sie die Funktionen, die Ihren aktuellen Prioritäten entsprechen:

- **[Erstellen Sie Ihr erstes Formular](/help/forms/creating-adaptive-form-core-components.md)** um die Authoring-Umgebung kennenzulernen
- **[Überprüfen der](/help/forms/aem-forms-cloud-service-architecture.md)** für die Bereitstellungsplanung
- **[Einrichten der Entwicklungsumgebung](/help/forms/setup-local-development-environment.md)** für die Zusammenarbeit mit Teams
- **[Erkunden von Integrationsoptionen](/help/forms/data-integration.md)** zum Verbinden vorhandener Systeme

Für umfassende Implementierungshandbücher sollten Sie Adobe Professional Services in Betracht ziehen, um Ihre Bereitstellung zu beschleunigen und von Anfang an Best Practices sicherzustellen.
