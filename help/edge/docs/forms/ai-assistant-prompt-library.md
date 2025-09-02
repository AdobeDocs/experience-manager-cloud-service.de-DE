---
title: Forms Experience Builder - Bibliothek mit Eingabeaufforderung
description: Sammlung bewährter Prompt-Muster und Beispiele zum Erstellen von Formularen mit KI-Unterstützung in der Benutzeroberfläche für die Formularverwaltung, im Editor für adaptive Formulare und im universellen Editor.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: c8f64082-a23f-4919-ad66-042faad77d31
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 13%

---


# Forms Experience Builder - Bibliothek mit Eingabeaufforderung

Sammlung wiederverwendbarer Eingabeaufforderungsmuster und Beispiele, die für Forms Experience Builder optimiert wurden. Diese optimierte Bibliothek konzentriert sich auf die beiden Kernerstellungsmethoden „Erstellen von Grund auf“ und „Importieren und Konvertieren“ mit verbesserter Unterstützung für LLM-gestützte intelligente Felder und Markenkonsistenz.

>[!NOTE]
>
> Der Forms Experience Builder ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie eine E-Mail von Ihrer Geschäftsadresse an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Eingabeaufforderungen, Beispiele und Best Practices können sich ändern, wenn Forms Experience Builder während des Early-Adopter-Programms weiterentwickelt wird.

## Verwenden dieser Eingabeaufforderungsbibliothek

Diese Bibliothek bietet wiederverwendbare Eingabeaufforderungsmuster für gängige Szenarien zur Formularerstellung. Umfassende Best Practices finden Sie im Handbuch zu den ersten Schritten mit Forms Experience Builder [&#128279;](forms-ai-assistant-getting-started.md#best-practices).

### Schnelltipps für diese Bibliothek

- **Mit Beispielen beginnen** - Verwenden Sie bereitgestellte Eingabeaufforderungen als Vorlagen und passen Sie sie an Ihre Anforderungen an
- **Zwei Erstellungsmethoden** Wählen Sie Erstellen von Grund auf oder Import- und Konvertierungsansätze
- **Spezifisch sein** - Fügen Sie allgemeine Beispiele um Ihre eigenen Details
- **Gründlich testen** - Ergebnisse immer in Ihrer spezifischen Umgebung validieren

### Markenvorlagen und -stile

**Bereiten Sie Marken-Assets im Voraus für eine konsistente Formularerstellung vor:**

- **Markenvorlagen** - Bereiten Sie standardisierte Formularvorlagen mit den Farben, Schriftarten und Layout-Mustern Ihres Unternehmens vor
- **Stilrichtlinien** - Definieren Sie konsistente Feldstile, Schaltflächendesigns und Abstandsstandards, die Forms Experience Builder anwenden kann
- **Komponentenbibliothek** - Arbeiten Sie mit Ihrem Entwicklungs-Team zusammen, um wiederverwendbare Formularkomponenten vorzubereiten, die Ihrer Markenidentität entsprechen
- **Visual Assets** - Bereiten Sie Logos, Symbole und Hintergrundelemente für die Formularintegration vor.

<!-- **Example Brand Application Prompt:**

    Apply our financial services brand template with:
    - Corporate blue (#003366) and silver (#C0C0C0) color scheme
    - Open Sans font family for all text
    - 16px minimum font size for accessibility
    - Consistent 24px spacing between sections
    - Corporate logo in header with proper sizing
    - Professional button styling with hover effects

>[!NOTE]
>
>**Custom Components**: Check with your development team about using organization-specific components and their compatibility with Forms Experience Builder before implementing custom brand elements.

>[!NOTE]
>
> This prompt library has been updated to reflect the streamlined Forms Experience Builder capabilities. Some advanced integration and testing features shown in examples may require additional configuration.

-->


## Beispiele für inkrementelle Entwicklung

Diese Beispiele zeigen, wie Sie Formulare Schritt für Schritt erstellen, indem Sie einfach anfangen und schrittweise Komplexität hinzufügen:

### Beispiel 1: Inkrementelles Erstellen eines Kontaktformulars

**Schritt 1 – Einfach starten:**

    Erstellen Sie ein einfaches Kontaktformular mit den Feldern Name, E-Mail und Nachricht

**Schritt 2 – Validierung hinzufügen:**

    Erstellen Sie @name und @email Pflichtfelder mit entsprechender Validierung

**Schritt 3 – Verbessern des Benutzererlebnisses:**

    Fügen Sie Platzhaltertext hinzu: @name „Ihr vollständiger Name“, @email &quot;your.email@company.com&quot; @message „Sagen Sie uns, wie wir helfen können“

**Schritt 4 – Erweiterte Funktionen hinzufügen:**

    Dropdown-Anfrage hinzufügenTyp mit Optionen: „Allgemeine Frage“, „Support-Anfrage“, „Verkaufsanfrage“, „Partnerschaft“

**Schritt 5 – Implementieren einer bedingten Logik:**

    /create-rule zeigen @urgencyLevel Dropdown-Liste (Niedrig, Medium, Hoch) nur an, wenn @inquiryType gleich „Support-Anfrage“

### Beispiel 2: Inkrementelles Erstellen eines Registrierungsformulars

**Schritt 1 – Grundstruktur:**

    Erstellen eines Benutzerregistrierungsformulars mit Bedienfeld für personenbezogene Daten

**Schritt 2: Erforderliche Felder hinzufügen:**

    Felder für @firstName, @lastName, @email und @phoneNumber mit entsprechender Validierung hinzufügen

**Schritt 3: Hinzufügen einer Business-Logik:**

    Regel erstellen: Wenn @age jünger als 18 Jahre ist, Abschnitt mit Informationen zu Eltern/Erziehungsberechtigten anzeigen

**Schritt 4: Verbessern mit Voreinstellungen:**

    Bedienfeld „Voreinstellungen“ mit @newsletterSubscription, @marketingConsent, @termsAccepted hinzufügen

**Schritt 5 - Datei-Upload hinzufügen:**

    Ein Datei-Upload-Feld für @profilePicture mit einer Größenbeschränkung von 5 MB wird einbezogen

## Formularerstellung und -verwaltung

**Verwendung:** Wenn Sie neue Formulare erstellen oder vorhandene ändern müssen.

**Verwendung:** Wählen Sie einen von zwei Ansätzen: von Grund auf neu erstellen oder Importieren und Konvertieren (siehe [Erste Schritte](forms-ai-assistant-getting-started.md#two-ways-to-create-forms)).

**Beispielaufforderung - Einfache Formularerstellung:**

    Erstellen Sie ein Formular für Kunden-Feedback mit:
    - Produktbewertung (1-5 Sterne)
    - Feld „Kommentar“ für detailliertes Feedback
    - Kunden-E-Mail (optional)
    - An E-Mail-Benachrichtigung senden

**Beispielaufforderung - Erstellung eines komplexen Formulars:**

    Erstellen eines umfassenden Onboarding-Formulars für Mitarbeiter mit:
    
    **Abschnitt „Persönliche Informationen“:**
    - Vollständiger Name (Vor-, Mittel-, Nachname)
    - Geburtsdatum mit Altersvalidierung
    - Kontaktinformationen (E-Mail, Telefon, Adresse)
    - Kontaktinformationen für Notfälle
    
    **Beschäftigungsdetails:**
    - Auswahl von Positionen und Abteilungen
    - Startdatum mit der Validierung des Geschäftstags
    - Gehaltsinformationen mit Vertraulichkeitshinweis
    - Berichtsstruktur
    
    **Dokument-Upload:**
    - Wiederaufnahme/Lebenslauf (PDF, DOC, DOCX)
    )
    - ID-Bestätigungsdokumente
    - und Bankinformationen
    
    - Unterzeichnete Beschäftigung Vereinbarung
    Voreinstellungen:**
    - Leistungsauswahl mit Kostenrechner
    - Voreinstellungen für den Arbeitsplan
    - Schulungsanforderungen&#x200B;**Validierungsregeln:**&#x200B;Validierung des E-Mail-FormatsValidierungAlter muss 18 oder älter sein**- Alle erforderlichen Dokumente müssen hochgeladen werden
    
    - Bedingungen müssen akzeptiert werden&#x200B;**Aktionen senden:**&#x200B;Bestätigungs-E-Mail an neueMitarbeiter senden
    - HR- Personalabteilung benachrichtigen
    - Erstellen Sie einen Datensatz in einem HR
     
     
     
    
     
     
     
     
     
&#x200B;-
**Form Management-Eingabeaufforderungen:**

    Importieren Sie dieses PDF-Antragsformular und konvertieren Sie es in ein adaptives Formular mit erweiterter Validierung
    
    Aktualisieren Sie das bestehende Kontaktformular, um Social-Media-Handles und bevorzugte Kontaktmethode einzuschließen
    
    Organisieren Sie das Registrierungsformular in einen 3-stufigen Assistenten: Persönliche Informationen, Voreinstellungen, Bestätigung

## Feldverwaltung und -konfiguration

**Verwendung:** Wenn Sie Formularfelder hinzufügen, ändern oder konfigurieren müssen.

**Verwendung:** Geben Sie Feldtypen, Validierungsregeln und Anforderungen an das Benutzererlebnis besondere Informationen.

**Beispielaufforderung - Hinzufügen eines einfachen Felds:**

    Fügen Sie ein Texteingabefeld für „Firmenname“ mit dem Platzhalter „Geben Sie Ihren Firmennamen ein“

**Beispielaufforderung - Erweiterte Feldkonfiguration:**

    Fügen Sie einen umfassenden Adressabschnitt mit folgender Adresse hinzu:
    
    **Straßenadresse:**
    - Adresszeile 1 (erforderlich, max. 100 Zeichen)
    - Adresszeile 2 (optional, max. 100 Zeichen)
    - Stadt (erforderlich, Dropdown mit allgemeinen Städten)
    - Bundesland/Provinz (erforderlich, Dropdown)
    - Postleitzahl (erforderlich, Formatvalidierung)
    - Land (erforderlich, Standard „Vereinigte Staaten„)
    
    **Validierungsregeln:**
    - Postleitzahl muss mit der Statusauswahl übereinstimmen
    - Adresszeile 1 darf nicht leer sein
    - Stadt muss eine gültige Stadt für das ausgewählte Bundesland sein
    
    **Benutzererlebnis:**
    - Automatische Vervollständigung für Adressfelder
    - Entfernen von Kennzeichnungen und Hilfetext
    - Mobile-freundliche Eingabefelder
    - Einhaltung der Barrierefreiheit

**Feldkonfigurationsaufforderungen:**

    @email Feld mit Echtzeitvalidierung und benutzerdefinierter Fehlermeldung erforderlich machen
    
    Dropdown für @country @phoneNumber mit Optionen für die USA, Kanada, Großbritannien, Deutschland, Frankreich und „Sonstige“
    
    Feld mit Format (XXX) XXX-XXXX konfigurieren und Validierung
    
    Feld für den Datei-Upload für @resume mit PDF- und DOC-Einschränkungen hinzufügen, max. 5 MB

## LLM-optimierte Smart Fields

**Verwendung:** Wenn Sie Felder mit vorausgefüllten Optionen benötigen, die die Wissensdatenbank der KI nutzen.

**Verwendung:** Anforderungsfelder, für die umfassende Datensätze erforderlich sind - die KI kann Optionen mithilfe ihres integrierten Wissens automatisch ausfüllen.

### Geografische Felder und Standortfelder

**Flughäfen und Verkehr:**

    Dropdown für Abflughäfen mit allen wichtigen internationalen Flughäfen hinzufügen
    Feld „Ankunftsflughafen“ mit IATA-Codes und vollständigen Namen hinzufügen
    Feld für den nächstgelegenen Flughafen zum Benutzerstandort erstellen
    Eine Auswahl an Bahnhöfen für europäische Städte hinzufügen

**Verwaltungsregionen:**

    Vollständige Liste der US-Bundesstaaten mit Abkürzungen hinzufügen
    Erstellen Sie eine Dropdownliste mit ISO-Codes und vollständigen Namen
    Fügen Sie ein Feld für die größten Städte der Welt mit Zeitzonen hinzu
    Fügen Sie eine Dropdown-Liste der kanadischen Provinzen und Territorien hinzu
    Fügen Sie ein Feld für britische Countys und Postgebiete hinzu

### Unternehmens- und Branchendaten

**Unternehmensklassifizierungen:**

    Feld für die Branchenklassifizierung mit NAICS-Codes hinzufügen
    Erstellen Sie eine Dropdown-Liste der Typen von Geschäftseinheiten (LLC, Corporation, Partnerschaft usw.)
    Feld für Unternehmensgrößenkategorien hinzufügen (Start, KMU, Unternehmen)
    Abteilungsauswahl für große Organisationen einbeziehen
    Feld für professionelle Servicetypen hinzufügen

**Berufsklassifikationen:**

    Feld für Stellenbezeichnungen mit gemeinsamen Branchenrollen hinzufügen
    Erstellen Sie ein Dropdown-Menü mit professionellen Zertifizierungen nach Feld
    Schulungsstufen mit Abschlussarten einbeziehen
    Feld für jahrelange Erfahrung hinzufügen
    Erstellen Sie eine Auswahl für Programmiersprachen und Frameworks

### Normen und Vorschriften

**Finanz- und Rechtsfragen:**

    Feld für Währungs-Codes mit Symbolen und Wechselkursen hinzufügen
    Erstellen Sie eine Dropdown-Liste der Steuer-ID-Typen nach Land
    Feld für juristische Dokumenttypen einschließen
    Zahlungsmethode-Optionen mit Sicherheitsmerkmalen hinzufügen
    Erstellen Sie eine Auswahl für Bankinstitute nach Land

**Technische Normen:**

    Dropdown-Liste mit Dateitypen mit Erweiterungen hinzufügen
    Optionen für Netzwerkprotokolle einschließen
    Feld für Datenbanktypen und Versionen hinzufügen
    Auswahl für API-Authentifizierungsmethoden erstellen

### Gesundheitswesen und Medizin

**Medizinische Klassifikationen:**

    Feld für medizinische Fachgebiete hinzufügen
    Erstellen Sie eine Dropdown-Liste mit allgemeinen Medikamenten mit generischen Namen
    Feld für Versicherungsanbietertypen einschließen
    Eine Auswahl für medizinische Notfallkontakte hinzufügen
    Erstellen Sie ein Feld für Ernährungseinschränkungen und Allergien

### Zeit- und Kalenderinformationen

**Datums- und Uhrzeitfelder:**

    Feld für Geschäftszeiten mit Zeitzonenverarbeitung hinzufügen
    Erstellen Sie eine Dropdown-Liste der Feiertage nach Land
    Saisonale Optionen mit Datumsbereichen einschließen
    Feld für die Buchung von Konferenzräumen mit Verfügbarkeit hinzufügen
    Auswahl für Muster wiederkehrender Meetings erstellen

### Produkt- und Servicekategorien

**E-Commerce-Klassifizierungen:**

    Feld für Produktkategorien mit Unterkategorien hinzufügen
    Erstellen eines Dropdown-Menüs der Versandmethoden mit Versandschätzungen
    Feld für Rückgaberichtlinienoptionen einbeziehen
    Auswahl für Kundenprioritätsstufen hinzufügen
    Feld für Abonnement-Abrechnungszyklen erstellen

**Beispiel: Smart-Feld-Eingabeaufforderungen:**

    „Ein Feld für Abflughäfen mit allen wichtigen Flughäfen weltweit hinzufügen, einschließlich IATA-Codes und Städtenamen“
    
    „Erstellen Sie ein umfassendes Branchenfeld mit der standardmäßigen NAICS-Klassifizierung mit Technologie-Unterkategorien“
    
    „Schließen Sie ein Dropdown-Menü für die Zertifizierung ein, das sich auf der Grundlage des ausgewählten Arbeitsfelds anpasst“
    
    „Fügen Sie ein Feld für internationale Telefonnummern hinzu, das Formate auf der Grundlage des ausgewählten Landes“
    
    „Erstellen Sie ein Auswahlfeld für Universitäten mit wichtigen Institutionen, die nach Land und Ranking organisiert sind“

## Regelerstellung und Geschäftslogik

**Verwendung:** Wenn Sie bedingte Logik, Validierungsregeln oder Geschäftsprozesse implementieren müssen.

**Verwendung:** Beschreiben Sie die Geschäftslogik klar und geben Sie Bedingungen und Aktionen an.

**Beispielaufforderung - Einfache bedingte Logik:**

    Erstellen Sie eine Regel, die @spouseInformation Bedienfeld nur anzeigt, wenn @maritalStatus gleich „Verheiratet“

**Beispielaufforderung - Komplexe Geschäftsregeln:**

    Umfassende Validierung des Kreditantrags implementieren:
    
    **Einkommensvalidierung:**
    - Bei @annualIncome kleiner als 30000:
    - Warnmeldung anzeigen: „Das Einkommen kann für den angeforderten Darlehensbetrag nicht ausreichen“
    - Zusätzliche Einkommensdokumentation anfordern
    - Meldung anzeigen: „Zusätzliche Dokumentation kann erforderlich sein“
    - Wenn @annualIncome größer als 100000:
    - Optionen für Premium-Services anzeigen
    - Checkbox für die Prioritätsverarbeitung aktivieren
    
    **Altersbasierte Validierung:**
    - Wenn @age unter 18:
    - Informationen für Eltern/Erziehungsberechtigten anzeigen
    - Übergeordnetes Hochladen obligatorisch machen
    - Schaltflächentnehmen-Text zu „Zur Überprüfung übermitteln“
    &quot;- Wenn @age 65 oder älter:
    - Senior-Rabattoptionen anzeigen
    - Abschnitt „Voreinstellungen für Barrierefreiheit hinzufügen“

**Regelspezifische Prompts:**

    Erstellen Sie eine **Sichtbarkeitsregel** die @spouseInformation Bedienfeld nur dann anzeigt, wenn @maritalStatus gleich „Verheiratet“ oder „Inländische Partnerschaft“
    
    Hinzufügen **progressive Offenlegung** ist, wenn zusätzliche Fragen basierend auf früheren Antworten angezeigt werden. Beginnen Sie mit den grundlegenden Informationen und zeigen Sie dann relevante 
    
     an **Smart Defaults** in denen @country Auswahl automatisch verwandte Felder festlegt. Manuelles Überschreiben zulassen

## Datenintegration und -übertragung

**Verwendung:** Wenn Sie Formulare mit Backend-Systemen, Datenbanken oder externen Services verbinden müssen.

**Verwendung:** Beginnen Sie mit der grundlegenden Einrichtung der Übermittlung und fügen Sie dann schrittweise zusätzliche Integrationen hinzu. Geben Sie den Integrationstyp, die Datenformatanforderungen und die Voreinstellungen für die Fehlerbehandlung an.

**Beispiel-Prompt – Beginn mit einfacher Übermittlung:**

    Konfigurieren der einfachen Formularübermittlung für @applicationForm:
    
    **Primäre Übermittlung:**
    - Senden von Formulardaten an REST-Endpunkt: &quot;/api/v1/applications“
    - Formatieren von Daten als JSON
    - Erfolgsmeldung anzeigen: „Anwendung erfolgreich gesendet“
    - Fehlermeldung anzeigen, wenn die Übermittlung fehlschlägt: „Übermittlung fehlgeschlagen, bitte erneut versuchen“

**Fügen Sie dann schrittweise sekundäre Aktionen hinzu:**

    E-Mail-Benachrichtigung zu @applicationForm hinzufügen: Bestätigungs-E-Mail an @email Adresse mit Anwendungs-Referenznummer senden
    
    CRM-Integration zu @applicationForm hinzufügen: Neuen Lead-Datensatz mit @firstName, @lastName, @email erstellen und Status auf „Neue Anwendung“ setzen

**Beispiel-Eingabeaufforderung - Standard-Multi-Channel-Übermittlung:**

**     Formularübermittlung mit mehreren Datenzielen konfigurieren:
    
    **Primäre Übermittlung:**
    - Formulardaten an REST-Endpunkt senden: &quot;/api/v1/Applications“
    - Authentifizierungs-Header mit API-Schlüssel einschließen
    - Daten als JSON mit verschachtelten Objekten für Adresse und Beschäftigung formatieren
    - Erfolgsantwort verarbeiten (201) durch Anzeige der Dankesmeldung verarbeiten
    
    **Sekundäre Aktionen:**
    - Benachrichtigungs-E-Mail an Antragsteller unter @email senden
    - Anwendungsdaten in Tracking-System kopieren
    - Trigger-Workflow für Genehmigungsprozess
    - Datensatz im CRM erstellen mit Lead-Status „Neue Anwendung 
    
    &quot;
    &quot;
    -Fehlerbehandlung:-Wenn Die primäre Übermittlung schlägt fehl, Daten werden lokal gespeichert und erneut versucht
    - Benutzerfreundliche Fehlermeldung anzeigen: „Übermittlung vorübergehend nicht verfügbar“
    - Option zum Herunterladen von Formulardaten als Sicherung angeben
    
    - Warnhinweis-E-Mail an Admin-Team über fehlgeschlagene Übermittlung senden
    **Erfolgsfluss:**
    - Zur Bestätigungsseite mit Anwendungs-Referenznummer umleiten
    - Bestätigungs-E-Mail mit den nächsten Schritten senden
- Geschätzte Verarbeitungszeitleiste anzeigen
**Integrationsspezifische Prompts:**

    Verbinden Sie dieses Formular mit dem **CRM-System**, um neue Leads zu erstellen. Ordnen Sie beim Senden des Formulars @firstName FirstName, @email E-Mail zu, legen Sie LeadSource auf „Web-Formular“ und Status 
    
    Neu“ fest **Workflow-Trigger &#x200B;**. Alle Formulardaten und den Workflow für die Trigger-Genehmigung mit Manager-Benachrichtigung 
    
    **Datenbankintegration** übergeben, um Formularübermittlungen als Datensätze zu speichern Erstellen Sie für jede Übermittlung mit hochgeladenen Dokumenten einen neuen Ordner

<!-- ## Import & Convert Existing Forms

**When to use:** When you have existing forms, documents, or designs to transform into modern AEM forms.

**How to use:** Upload your source file and describe the conversion requirements (see [Import Guide](forms-ai-assistant-getting-started.md#2-import-and-convert)).


**Design Import Prompts:**

    Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness

    Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields

    Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes

## Mobile Optimization & Responsiveness

**When to use:** When forms need to work seamlessly across all device types and screen sizes.

**How to use:** Start with basic mobile optimization, then enhance with advanced features. Emphasize mobile-first approach and specify breakpoint behaviors incrementally.

**Example Prompt - Start with Basic Mobile Optimization:**

    Make @contactForm mobile-friendly with:
    
    **Basic Mobile Layout:**
    - Single column layout for all form sections
    - Larger touch targets for buttons and inputs
    - Responsive design that works on phones and tablets

**Then Add Advanced Mobile Features:**

    Enhance @contactForm mobile experience with:
    - Sticky submit button at bottom of screen
    - Touch-friendly date pickers
    - Swipe gestures for multi-step navigation

**Example Prompt - Comprehensive Mobile-First Optimization:**

    Optimize this form for **mobile-first responsive design**:
    
    **Mobile Layout (320px - 768px):**
    - Single column layout for all form sections
    - Larger touch targets (minimum 44px height)
    - Simplified navigation with collapsible sections
    - Sticky submit button at bottom of screen
    - Auto-zoom disabled on input focus
    
    **Tablet Layout (768px - 1024px):**
    - Two-column layout for shorter fields (name, email)
    - Single column for complex fields (address, comments)
    - Side navigation for multi-step forms
    - Optimized for both portrait and landscape
    
    **Desktop Layout (1024px+):**
    - Multi-column layouts where appropriate
    - Horizontal form sections for related fields
    - Sidebar navigation for long forms
    - Hover states and advanced interactions

**Mobile-Specific Prompts:**

    Make this form **touch-friendly** with larger buttons and simplified navigation for mobile users

    Optimize form for **tablet users** with appropriate field sizes and navigation patterns

    Add **swipe gestures** for multi-step form navigation on mobile devices

## Accessibility & Compliance

**When to use:** When forms need to meet accessibility standards (WCAG) or compliance requirements.

**How to use:** Specify the required compliance level and any specific accessibility features needed.

**Example Prompt - Basic Accessibility:**

    Make @contactForm accessible with:
    
    **Basic Accessibility:**
    - Proper ARIA labels for all form fields
    - Keyboard navigation support
    - High contrast color scheme
    - Screen reader compatibility
    - Focus indicators for all interactive elements

**Example Prompt - Advanced Accessibility:**

    Implement comprehensive accessibility for @applicationForm:
    
    **WCAG 2.1 AA Compliance:**
    
    - Semantic HTML structure with proper headings
    - ARIA landmarks and roles for navigation
    - Color contrast ratio of at least 4.5:1
    - Keyboard-only navigation support
    - Screen reader announcements for dynamic content
    
    **Form-Specific Accessibility:**
    
    - Error messages announced to screen readers
    - Field validation with clear error descriptions
    - Progress indicators for multi-step forms
    - Skip navigation links for keyboard users
    - Alternative text for all images and icons
    
    **User Experience:**
    
    - Clear focus indicators on all interactive elements
    - Logical tab order through form fields
    - Descriptive link text and button labels
    - Help text available for complex fields
    - Timeout warnings for session expiration

**Accessibility-Specific Prompts:**

    Add **screen reader support** to this form with proper ARIA labels and announcements

    Implement **keyboard navigation** for all form interactions and navigation elements

    Ensure **color contrast** meets WCAG AA standards for all text and interactive elements  

## Performance Optimization

**When to use:** When forms need to load quickly and perform well under various conditions.

**How to use:** Specify performance requirements and optimization strategies.

**Example Prompt - Basic Performance:**

    
Optimize @contactForm for performance:

**Loading Optimization:**

- Lazy load non-critical form sections
- Minimize initial bundle size
- Optimize images and assets
- Enable caching for static resources
    

**Example Prompt - Advanced Performance:**

    
Implement comprehensive performance optimization for @applicationForm:

**Loading Performance:**

- Progressive loading of form sections
- Optimize images with WebP format
- Minimize JavaScript bundle size
- Enable gzip compression for all assets

**Runtime Performance:**

- Debounce validation calls to reduce API requests
- Optimize conditional logic execution
- Cache frequently used data
- Implement virtual scrolling for long lists

**User Experience:**

- Show loading indicators for async operations
- Provide offline capability for form data
- Auto-save form progress every 30 seconds
- Optimize form submission with retry logic

**Monitoring:**

- Track form load times and user interactions
- Monitor validation performance
- Measure submission success rates
- Alert on performance degradation
    

**Performance-Specific Prompts:**

    
Optimize form **loading speed** by implementing progressive loading and asset optimization
    

    
Add **auto-save functionality** to prevent data loss during form completion
    

    
Implement **offline support** so users can complete forms without internet connection
    

## Testing & Quality Assurance

**When to use:** When forms need comprehensive testing to ensure reliability and user satisfaction.

**How to use:** Specify testing scenarios, validation requirements, and quality metrics.

**Example Prompt - Basic Testing:**

    
Add comprehensive testing for @contactForm:

**Functional Testing:**

- Test all form field validations
- Verify submit functionality works correctly
- Test error handling and user feedback
- Validate conditional logic and rules
    

**Example Prompt - Advanced Testing:**

    
Implement comprehensive testing strategy for @applicationForm:

**Functional Testing:**

- Unit tests for all validation rules
- Integration tests for submit actions
- End-to-end testing for complete user flows
- Cross-browser compatibility testing

**User Experience Testing:**

- Usability testing with target user groups
- Accessibility testing with screen readers
- Mobile device testing on various screen sizes
- Performance testing under load conditions

**Quality Assurance:**

- Automated testing for regression prevention
- Manual testing for edge cases and scenarios
- Security testing for data protection
- Compliance testing for regulatory requirements

**Monitoring:**

- Track form completion rates and abandonment
- Monitor error rates and user feedback
- Measure performance metrics and load times
- Analyze user behavior and interaction patterns
    

**Testing-Specific Prompts:**

    
Add **automated testing** for all form validations and submit functionality
    

    
Implement **user acceptance testing** scenarios for complete form workflows
    

    
Set up **performance monitoring** to track form load times and user interactions
    
-->

## Befehlsreferenz

### Wesentliche Befehle

| Befehl | Bester Anwendungsfall | Beispiel |
|---------|---------------|---------|
| `/create-form` | Starten neuer Formulare | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Hinzufügen von Formularen zu Seiten | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | Änderung der Formularstruktur | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Ändern von Feldeigenschaften | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Hinzufügen von dynamischem Verhalten | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Organisieren von Formularabschnitten | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Konvertieren von Designs | `/add-panel from uploaded form image with field recognition` |
| `/help` | Hilfe erhalten | `/help how to implement multi-step validation?` |

### Feldverweise

Verwenden Sie `@fieldName` Syntax, um in Ihren Eingabeaufforderungen auf vorhandene Felder zu verweisen:

- `@email` - E-Mail-Referenzfeld
- `@firstName` - Referenzvornamenfeld
- `@maritalStatus` - Referenzfeld „Familienstand“

### Komponententypen

**Eingabekomponenten:**

- `text`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `dropdown`, `file`, `textarea`

**Container-Komponenten:**

- `fieldset`, `panel`, `repeatable`, `wizard`

### Komponenteneigenschaften

**Universelle Eigenschaften (alle Komponenten):**

- **type**: Komponententyp
- **Name**: Feldkennung für die Formularübermittlung
- **Label**: Zeigt Text für das Feld an
- **Beschreibung**: Hilfetext für das Feld
- **Sichtbar**: Boolescher Wert für anfängliche Sichtbarkeit
- **Obligatorisch**: Boolescher Wert für erforderliche Felder

**Eingabefeld-Eigenschaften:**

- **Wert**: Standard-/Anfangswert
- **Platzhalter**: Hinweistext für Eingabefelder
- **Min**: Mindestwert (für Zahlen/Datumsangaben)
- **Max**: Höchstwert (für Zahlen/Datumsangaben)

**Eigenschaften für Datei-Uploads:**

- **Akzeptieren**: Dateitypen (.pdf, .doc, .docx, .jpg, .png usw.)
- **Mehrere**: Boolescher Wert für die Auswahl mehrerer Dateien

**Eigenschaften des Auswahlsteuerelements:**

- **Optionen**: Optionen für Dropdown-Listen (durch Kommas getrennte Liste)
- **Aktiviert**: Standardauswahl für Kontrollkästchen/Optionsfelder

**Container-Eigenschaften:**

- **Feldsatz**: Gruppieren verwandter Felder
- **Wiederholbar**: Boolescher Wert für wiederholbare Abschnitte

**Erweiterte Eigenschaften:**

- **Sichtbarer Ausdruck**: Formel für bedingte Sichtbarkeit (=Formel)
- **Wertausdruck**: Formel für berechnete Werte (=Formel)

### Integrationsbefehle

**Übermittlungsaktionen:**

- E-Mail-Benachrichtigungen
- REST-API-Übermittlungen
- Cloud-Speicher (Azure, SharePoint)
- Workflow-Automatisierung (Power Automate, Workfront Fusion)
- Marketing-Plattformen (Marketo)
- CRM-Integrationen

### Richtlinien zur Eingabeaufforderungssyntax

- **Feldverweise**: `@fieldName` für vorhandene Felder verwenden
- **Befehle**: `/command` für bestimmte Aktionen verwenden
- **Natürliche Sprache**: Anforderungen klar und spezifisch beschreiben

### Validierungs-Checkliste

Umfassende Best Practices und Validierungsrichtlinien finden Sie im Abschnitt Erste Schritte mit Forms Experience Builder [&#128279;](forms-ai-assistant-getting-started.md#best-practices).

*Diese Eingabeaufforderungsbibliothek wird laufend auf der Grundlage von Benutzer-Feedback und neuen Forms Experience Builder-Funktionen aktualisiert. Die neuesten Funktionen und Beispiele finden Sie in der [Dokumentation zu AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=de).*
