---
title: Formularübermittlung und -integration
description: Erfahren Sie, wie Sie Formularübermittlungen konfigurieren und Forms Experience Builder-Formulare mit externen Systemen, APIs und Business-Workflows integrieren.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: c772556b-dab6-4fa8-b728-1fe52c6596a4
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 1%

---

# Formularübermittlung und -integration

>[!NOTE]
>
> Forms Experience Builder ist im Rahmen eines Early-Access-Programms verfügbar. Bevor Sie beginnen, stellen Sie sicher, dass Sie Zugriff angefordert haben und erhalten haben.

Forms Experience Builder bietet leistungsstarke Integrationsfunktionen zur Verbindung Ihrer Formulare mit externen Systemen, APIs und Business-Workflows. In diesem Handbuch wird beschrieben, wie Sie Formularübermittlungen konfigurieren und verschiedene Integrationsszenarien einrichten.

## Konfigurationsoptionen für die Übermittlung

### E-Mail-Sendungen

Konfigurieren von Formularen zum Senden von Übermittlungen per E-Mail:

**Einfache E-Mail-Einrichtung:**

- Empfänger-E-Mail-Adressen festlegen
- Konfigurieren von E-Mail-Vorlagen
- Hinzufügen von CC- und BCC-Empfängern
- Einrichten von E-Mail-Benachrichtigungen

**Erweiterte E-Mail-Funktionen:**

- Dynamische Empfängerauswahl
- E-Mail-Vorlagen mit Formulardaten
- Umgang mit Anhängen
- E-Mail-Versandbestätigung

### REST-API-Integration

Verbinden von Formularen mit externen APIs und Services:

**API-Endpunktkonfiguration:**

- Festlegen von REST-API-URLs
- Authentifizierungsmethoden konfigurieren
- Festlegen von Anfragekopfzeilen und -parametern
- Verarbeiten von Antwortdaten

**Datenzuordnung:**

- Formularfelder API-Parametern zuordnen
- Umwandeln von Datenformaten
- Behandeln verschachtelter JSON-Strukturen
- Verwalten von Fehlerantworten

### Cloud-Speicherintegration

Speichern von Formularübermittlungen in Cloud-Speicher-Services:

**Unterstützte Plattformen:**

- Microsoft Azure Blob Storage
- Amazon S3
- Google Cloud-Speicher
- SharePoint Online

**Konfigurationsoptionen:**

- Festlegen von Speicheranmeldeinformationen
- Konfigurieren von Ordnerstrukturen
- Festlegen von Dateibenennungskonventionen
- Verwalten von Zugriffsberechtigungen

### Workflow-Integration

Verbinden von Formularen mit Geschäftsprozess-Workflows:

**Microsoft Power Automate:**

- Trigger-Workflows bei der Formularübermittlung
- Übergeben von Formulardaten an Workflow-Schritte
- Workflow-Antworten verarbeiten
- Genehmigungsprozesse verwalten

**Adobe-Workflow:**

- Integration mit AEM Workflow
- Einrichten von Genehmigungsketten
- Konfigurieren von Benachrichtigungsschritten
- Dokumentverarbeitung verwalten

## Einrichten von Formularübermittlungen

### Schritt 1: Konfiguration der Zugriffsübermittlung

1. Öffnen Sie das Formular in Forms Experience Builder
2. Zu den Sendeeinstellungen navigieren
3. Wählen Sie „Formularübermittlung konfigurieren“
4. Integrationstyp auswählen

### Schritt 2: Konfigurieren von E-Mail-Übermittlungen

**Einfache E-Mail-Einrichtung:**

    Konfigurieren der E-Mail-Übermittlung an hr@company.com mit:
    - Betreff: „Neuer Mitarbeiter-Antrag“
    - Formulardaten in E-Mail-Textkörper einschließen
    - Bestätigung an Bewerber senden

**Erweiterte E-Mail-Konfiguration:**

    Dynamisches E-Mail-Routing einrichten:
    - Wenn Abteilung gleich „IT“ ist, an it-hr@company.com senden
    - Wenn Abteilung gleich „Vertrieb“ ist, an sales-hr@company.com senden
    - Standardwert ist hr@company.com

### Schritt 3: Einrichten der API-Integration

**REST-API-Konfiguration:**

    Senden von Formulardaten an REST-Endpunkt:
    - URL: https://api.company.com/forms/submit
    - Methode: POST
    - Authentifizierung: Bearer-Token
    - Content-Type: application/json

**Beispiel für die Datenzuordnung:**

    Formularfelder API zuordnen:
    - firstName -> user.first_name
    - lastName -> user.last_name
    -> user.email_address
    - Department -> user.department_id

### Schritt 4: Konfigurieren des Cloud-Speichers

**Azure Blob Storage-Einrichtung:**

    Speichern von Formularübermittlungen in Azure:
    - Container: form-submissions
    - Ordner: /{year}/{month}/{day}/
    - Dateiformat: JSON mit Anlagen
    - Zugriffsebene: Privat

## Integrationsbeispiele

### Formular für Kunden-Feedback

**Übermittlungskonfiguration:**

- E-Mail-Benachrichtigung an Support-Team
- Speichern von Daten im CRM-System über API
- Support-Ticket automatisch erstellen
- Bestätigungs-E-Mail an Kunde senden

**Implementierung:**
Formular für Kunden-Feedback senden an:
1. E-Mail-<support@company.com> mit Formulardetails
2. POST an CRM-API zur Erstellung eines Kundendatensatzes
3. Workflow zur Erstellung von Trigger-Support-Tickets
4. Dankesmail an Kunden senden

### Onboarding-Formular für Mitarbeiter

**Übermittlungskonfiguration:**

- E-Mail an HR-Team mit neuen Einstellungsinformationen
- Speichern von Dokumenten in SharePoint
- Onboarding-Workflow für Trigger
- Erstellen von Benutzerkonten in verschiedenen Systemen

**Implementierung:**
Onboarding von Mitarbeitern verarbeiten:
1. E-Mail-<hr@company.com> mit Mitarbeiterdetails
2. Hochladen von Dokumenten in den Mitarbeiterordner von SharePoint
3. Starten des Onboarding-Workflows in Power Automate
4. Erstellen von Konten in HR-System, E-Mail und anderen Tools

### Formular Lead-Generierung

**Übermittlungskonfiguration:**

- Lead-Daten in Marketing-Automatisierungsplattform speichern
- Benachrichtigung an Vertriebsteam senden
- Lead zum CRM-System hinzufügen
- E-Mail-Folge zur Nachbereitung von Triggern

**Implementierung:**
Lead-Generierung verarbeiten:
1. POST-Lead-Daten an Marketo-API
2. Lead-Datensatz in Salesforce erstellen
3. E-Mail an Vertriebsteam mit Lead-Details
4. Starten einer automatisierten E-Mail-Pflegesequenz

## Erweiterte Integrationsszenarien

### Mehrstufige Formularverarbeitung

**Komplexe Workflow-Integration:**

- Validieren von Formulardaten anhand externer Systeme
- Zahlungen über Zahlungs-Gateways verarbeiten
- Dokumente und Verträge generieren
- Senden von Benachrichtigungen an mehrere Stakeholder

### Validierung von Echtzeitdaten

**API-basierte Validierung:**

- Validieren von E-Mail-Adressen mit dem Unternehmensverzeichnis
- Überprüfen der Produktverfügbarkeit im Inventarsystem
- Überprüfen von Kundeninformationen in CRM
- Zahlungsinformationen validieren

### Bedingte Weiterleitung von Übermittlungen

**Dynamisches Routing basierend auf Formulardaten:**

- Je nach Abfragetyp zu unterschiedlichen Abteilungen weiterleiten
- Je nach Kundenebene an verschiedene Systeme senden
- Je nach Formularausfüllungsstatus unterschiedlich verarbeiten
- Verarbeiten Sie verschiedene Geschäftsregeln pro Region

## Sicherheit und Compliance

### Datenschutz

**Verschlüsselung und Sicherheit:**

- Verschlüsseln sensibler Daten während der Übertragung
- Sichere API-Anmeldeinformationen und Token
- Implementieren angemessener Zugriffssteuerungen
- Befolgen der Richtlinien zur Datenaufbewahrung

### Compliance-Anforderungen

**DSGVO und Datenschutz:**

- Implementieren der Einverständnisverwaltung
- Bereitstellen von Datenexportfunktionen
- Datenlöschanfragen aktivieren
- Audit-Trails verwalten

**Branchenstandards:**

- HIPAA-Konformität für Formulare im Gesundheitswesen
- PCI DSS für die Zahlungsabwicklung
- SOX-Konformität für Finanzformulare
- Branchenspezifische Vorschriften

## Tests und Validierung

### Übermittlungstests

**Testszenarien:**

- Überprüfen des E-Mail-Versands und der Formatierung
- Testen der API-Konnektivität und Datenzuordnung
- Validieren von Uploads des Cloud-Speichers
- Workflow-Trigger-Funktionalität überprüfen

**Fehlerbehandlung:**

- Testen von Szenarien für Netzwerkausfälle
- Anzeige der Fehlermeldung validieren
- Prüfen der Wiederholungsmechanismen
- Fallback-Optionen überprüfen

### Leistungsoptimierung

**Optimierungsstrategien:**

- Asynchrone Verarbeitung implementieren
- Verwenden von Batch-Vorgängen für Massendaten
- API-Aufruffrequenz optimieren
- Häufig verwendete Daten zwischenspeichern

## Fehlerbehebung bei Integrationsproblemen

### Häufige Probleme

**Probleme mit dem E-Mail-Versand:**

- SMTP-Server-Konfiguration überprüfen
- E-Mail-Adressen der Empfänger überprüfen
- Spam-Filtereinstellungen überprüfen
- E-Mail-Vorlagenformatierung testen

**Probleme bei der API-Integration:**

- Überprüfen der API-Endpunkt-URLs
- Authentifizierungsdaten überprüfen
- Validieren des Anfrageformats und der Kopfzeilen
- Überprüfen der API-Antwortverarbeitung

**Probleme mit der Speicherintegration:**

- Speicheranmeldeinformationen bestätigen
- Überprüfen von Ordnerberechtigungen
- Überprüfen der Dateiuploadbeschränkungen
- Testen der Netzwerkverbindung

### Hilfe wird abgerufen

Bei Integrationsproblemen:

- Lesen Sie die [Häufig gestellten Fragen zu Forms Experience Builder](forms-experience-builder-frequently-asked-questions.md)
- Lesen Sie [&#x200B; Erste Schritte &#x200B;](forms-experience-builder-getting-started.md)
- Wenden Sie sich an Ihren Systemadministrator, um technische Unterstützung zu erhalten
- Siehe API-Dokumentation für externe Services

## Verwandte Artikel

- [Übersicht über Forms Experience Builder](product-overview.md)
- [Erste Schritte mit Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Bereitstellen und Konfigurieren von Forms Experience Builder](deploy-forms-experience-builder.md)
- [Intelligente Import- und Konvertierungsfunktionen](intelligent-import-conversion.md)
- [Häufig gestellte Fragen](forms-experience-builder-frequently-asked-questions.md)
