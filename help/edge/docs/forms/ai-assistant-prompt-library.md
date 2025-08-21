---
title: Forms Experience Builder - Bibliothek mit Eingabeaufforderung
description: Sammlung bewährter Prompt-Muster und Beispiele zum Erstellen von Formularen mit KI-Unterstützung in der Benutzeroberfläche für die Formularverwaltung, im Editor für adaptive Formulare und im universellen Editor.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 333d42e0-625f-432e-a61b-5d49bf08765a
source-git-commit: 8be2b09200af58c701721b3e8537ea5e6cc3e4a2
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 28%

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

- **Markenvorlagen** - Erstellen Sie standardisierte Formularvorlagen mit den Farben, Schriftarten und Layout-Mustern Ihrer Organisation
- **Stilrichtlinien** - Definieren von konsistentem Feldstil, Schaltflächendesigns und Abstandsstandards
- **Komponentenbibliothek** - Erstellen Sie wiederverwendbare Formularkomponenten, die Ihrer Markenidentität entsprechen
- **Visual Assets** - Bereiten Sie Logos, Symbole und Hintergrundelemente für die Formularintegration vor.

**Beispiel einer Eingabeaufforderung für eine Markenvorlage:**

```
Create a brand template for financial services forms with:
- Corporate blue (#003366) and silver (#C0C0C0) color scheme
- Open Sans font family for all text
- 16px minimum font size for accessibility
- Consistent 24px spacing between sections
- Corporate logo in header with proper sizing
- Professional button styling with hover effects
```

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Wenden Sie sich an Ihr Entwicklungs-Team, um Informationen zur Verwendung organisationsspezifischer Komponenten und deren Kompatibilität mit Forms Experience Builder zu erhalten, bevor Sie benutzerdefinierte Markenelemente implementieren.

>[!NOTE]
>
> Diese Eingabeaufforderungsbibliothek wurde aktualisiert, um die optimierten Forms Experience Builder-Funktionen widerzuspiegeln. Einige in Beispielen dargestellte erweiterte Integrations- und Testfunktionen erfordern möglicherweise eine zusätzliche Konfiguration.



## Beispiele für inkrementelle Entwicklung

Diese Beispiele zeigen, wie Sie Formulare Schritt für Schritt erstellen, indem Sie einfach anfangen und schrittweise Komplexität hinzufügen:

### Beispiel 1: Inkrementelles Erstellen eines Kontaktformulars

**Schritt 1 – Einfach starten:**

```
Create a basic contact form with name, email, and message fields
```

**Schritt 2 – Validierung hinzufügen:**

```
Make @name and @email mandatory fields with appropriate validation
```

**Schritt 3 – Verbessern des Benutzererlebnisses:**

```
Add placeholder text: @name "Your full name", @email "your.email@company.com", @message "Tell us how we can help"
```

**Schritt 4 – Erweiterte Funktionen hinzufügen:**

```
Add a dropdown @inquiryType with options: "General Question", "Support Request", "Sales Inquiry", "Partnership"
```

**Schritt 5 – Implementieren einer bedingten Logik:**

```
Show @urgencyLevel dropdown (Low, Medium, High) only when @inquiryType equals "Support Request"
```

### Beispiel 2: Inkrementelles Erstellen eines Registrierungsformulars

**Schritt 1 – Grundstruktur:**

```
Create a user registration form with personal information panel
```

**Schritt 2: Erforderliche Felder hinzufügen:**

```
Add fields for @firstName, @lastName, @email, @phoneNumber with appropriate validation
```

**Schritt 3: Hinzufügen einer Business-Logik:**

```
Create a rule: if @age is under 18, show parent/guardian information section
```

**Schritt 4: Verbessern mit Voreinstellungen:**

```
Add a preferences panel with @newsletterSubscription, @marketingConsent, @termsAccepted
```

**Schritt 5 - Datei-Upload hinzufügen:**

```
Include a file upload field for @profilePicture with size limit of 5MB
```

## Formularerstellung und -verwaltung

**Verwendung:** Wenn Sie neue Formulare erstellen oder vorhandene ändern müssen.

**Verwendung:** Wählen Sie einen von zwei Ansätzen: von Grund auf neu erstellen oder Importieren und Konvertieren (siehe [Erste Schritte](/help/edge/docs/forms/forms-ai-assistant-getting-started.md)).

**Beispielaufforderung - Einfache Formularerstellung:**

```
Create a customer feedback form with:
- Product rating (1-5 stars)
- Comment field for detailed feedback
- Customer email (optional)
- Submit to email notification
```

**Beispielaufforderung - Erstellung eines komplexen Formulars:**

```
Create a comprehensive employee onboarding form with:

**Personal Information Section:**
- Full name (first, middle, last)
- Date of birth with age validation
- Contact information (email, phone, address)
- Emergency contact details

**Employment Details:**
- Position and department selection
- Start date with business day validation
- Salary information with confidentiality notice
- Reporting structure

**Document Upload:**
- Resume/CV upload (PDF, DOC, DOCX)
- ID verification documents
- Tax forms and banking information
- Signed employment agreement

**Preferences:**
- Benefits selection with cost calculator
- Work schedule preferences
- Training requirements
- Equipment needs

**Validation Rules:**
- Email format validation
- Phone number format validation
- Age must be 18 or older
- All required documents must be uploaded
- Terms and conditions must be accepted

**Submit Actions:**
- Send confirmation email to new employee
- Notify HR department
- Create employee record in HR system
- Schedule orientation meeting
```

**Form Management-Eingabeaufforderungen:**

```
Import this PDF application form and convert it to an adaptive form with enhanced validation
```

```
Update the existing contact form to include social media handles and preferred contact method
```

```
Reorganize the registration form into a 3-step wizard: personal info, preferences, confirmation
```

## Feldverwaltung und -konfiguration

**Verwendung:** Wenn Sie Formularfelder hinzufügen, ändern oder konfigurieren müssen.

**Verwendung:** Geben Sie Feldtypen, Validierungsregeln und Anforderungen an das Benutzererlebnis besondere Informationen.

**Beispielaufforderung - Hinzufügen eines einfachen Felds:**

```
Add a text input field for "Company Name" with placeholder "Enter your company name"
```

**Beispielaufforderung - Erweiterte Feldkonfiguration:**

```
Add a comprehensive address section with:

**Street Address:**
- Address line 1 (required, max 100 characters)
- Address line 2 (optional, max 100 characters)
- City (required, dropdown with common cities)
- State/Province (required, dropdown)
- Postal code (required, format validation)
- Country (required, default to "United States")

**Validation Rules:**
- Postal code must match state selection
- Address line 1 cannot be empty
- City must be a valid city for selected state

**User Experience:**
- Auto-complete for address fields
- Clear labels and help text
- Mobile-friendly input fields
- Accessibility compliance
```

**Feldkonfigurationsaufforderungen:**

```
Make @email field required with real-time validation and custom error message
```

```
Add a dropdown for @country with options for USA, Canada, UK, Germany, France, and "Other"
```

```
Configure @phoneNumber field with format (XXX) XXX-XXXX and validation
```

```
Add a file upload field for @resume with PDF and DOC restrictions, max 5MB
```

## LLM-optimierte Smart Fields

**Verwendung:** Wenn Sie Felder mit vorausgefüllten Optionen benötigen, die die Wissensdatenbank der KI nutzen.

**Verwendung:** Anforderungsfelder, für die umfassende Datensätze erforderlich sind - die KI kann Optionen mithilfe ihres integrierten Wissens automatisch ausfüllen.

### Geografische Felder und Standortfelder

**Flughäfen und Verkehr:**

```
Add a dropdown for departure airports with all major international airports
Add arrival airport field with IATA codes and full names
Create a field for nearest airport to user location
Add a selection of train stations for European cities
```

**Verwaltungsregionen:**

```
Add a complete list of US states with abbreviations
Create a country dropdown with ISO codes and full names
Add a field for major world cities with time zones
Include a dropdown of Canadian provinces and territories
Add a field for UK counties and postal areas
```

### Unternehmens- und Branchendaten

**Unternehmensklassifizierungen:**

```
Add a field for industry classification with NAICS codes
Create a dropdown of business entity types (LLC, Corporation, Partnership, etc.)
Add a field for company size categories (startup, SME, enterprise)
Include department selection for large organizations
Add a field for professional service types
```

**Berufsklassifikationen:**

```
Add a field for job titles with common industry roles
Create a dropdown of professional certifications by field
Include education levels with degree types
Add a field for years of experience ranges
Create a selection for programming languages and frameworks
```

### Normen und Vorschriften

**Finanz- und Rechtsfragen:**

```
Add a field for currency codes with symbols and exchange rates
Create a dropdown of tax ID types by country
Include a field for legal document types
Add payment method options with security features
Create a selection for banking institutions by country
```

**Technische Normen:**

```
Add a dropdown of file format types with extensions
Include network protocol options
Add a field for database types and versions
Create a selection for API authentication methods
```

### Gesundheitswesen und Medizin

**Medizinische Klassifikationen:**

```
Add a field for medical specialties
Create a dropdown of common medications with generic names
Include a field for insurance provider types
Add a selection for medical emergency contact relationships
Create a field for dietary restrictions and allergies
```

### Zeit- und Kalenderinformationen

**Datums- und Uhrzeitfelder:**

```
Add a field for business hours with time zone handling
Create a dropdown of public holidays by country
Include seasonal options with date ranges
Add a field for conference room booking with availability
Create a selection for recurring meeting patterns
```

### Produkt- und Servicekategorien

**E-Commerce-Klassifizierungen:**

```
Add a field for product categories with subcategories
Create a dropdown of shipping methods with delivery estimates
Include a field for return policy options
Add a selection for customer priority levels
Create a field for subscription billing cycles
```

**Beispiel: Smart-Feld-Eingabeaufforderungen:**

```
"Add a departure airport field with all major airports worldwide including IATA codes and city names"
```

```
"Create a comprehensive industry field using standard NAICS classification with technology subcategories"
```

```
"Include a professional certification dropdown that adapts based on the selected job field"
```

```
"Add an international phone number field that formats based on the selected country"
```

```
"Create a university selection field with major institutions organized by country and ranking"
```

## Regelerstellung und Geschäftslogik

**Verwendung:** Wenn Sie bedingte Logik, Validierungsregeln oder Geschäftsprozesse implementieren müssen.

**Verwendung:** Beschreiben Sie die Geschäftslogik klar und geben Sie Bedingungen und Aktionen an.

**Beispielaufforderung - Einfache bedingte Logik:**

```
Create a rule that shows @spouseInformation panel only when @maritalStatus equals "Married"
```

**Beispielaufforderung - Komplexe Geschäftsregeln:**

```
Implement comprehensive loan application validation:

**Income Validation:**
- If @annualIncome is less than 30000:
  - Show warning message: "Income may be insufficient for requested loan amount"
  - Require additional income documentation
  - Display message: "Additional documentation may be required"
- If @annualIncome is greater than 100000:
  - Show premium services options
  - Enable priority processing checkbox

**Age-Based Validation:**
- If @age is under 18:
  - Show parent/guardian information section
  - Make parent signature upload mandatory
  - Change submit button text to "Submit for Review"
- If @age is 65 or older:
  - Show senior discount options
  - Add accessibility preferences section
```

**Regelspezifische Prompts:**

```
Create a **visibility rule** that shows @spouseInformation panel only when @maritalStatus equals "Married" or "Domestic Partnership"
```

```
Add **progressive disclosure** where additional questions appear based on previous answers. Start with basic info, then show relevant follow-ups
```

```
Implement **smart defaults** where @country selection auto-sets related fields. Allow manual override
```

## Datenintegration und -übertragung

**Verwendung:** Wenn Sie Formulare mit Backend-Systemen, Datenbanken oder externen Services verbinden müssen.

**Verwendung:** Beginnen Sie mit der grundlegenden Einrichtung der Übermittlung und fügen Sie dann schrittweise zusätzliche Integrationen hinzu. Geben Sie den Integrationstyp, die Datenformatanforderungen und die Voreinstellungen für die Fehlerbehandlung an.

**Beispiel-Prompt – Beginn mit einfacher Übermittlung:**

```
Configure basic form submission for @applicationForm:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Format data as JSON
- Show success message: "Application submitted successfully"
- Show error message if submission fails: "Submission failed, please try again"
```

**Fügen Sie dann schrittweise sekundäre Aktionen hinzu:**

```
Add email notification to @applicationForm: Send confirmation email to @email address with application reference number
```

```
Add CRM integration to @applicationForm: Create new lead record with @firstName, @lastName, @email, and set Status to "New Application"
```

**Beispiel-Eingabeaufforderung - Standard-Multi-Channel-Übermittlung:**

```
Configure form submission with multiple data destinations:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Include authentication header with API key
- Format data as JSON with nested objects for address and employment
- Handle success response (201) by showing thank you message

**Secondary Actions:**
- Send notification email to applicant at @email address
- Copy application data to tracking system
- Trigger workflow for approval process
- Create record in CRM with lead status "New Application"

**Error Handling:**
- If primary submission fails, save data locally and retry
- Show user-friendly error message: "Submission temporarily unavailable"
- Provide option to download form data as backup
- Send alert email to admin team about failed submission

**Success Flow:**
- Redirect to confirmation page with application reference number
- Send confirmation email with next steps
- Display estimated processing timeline
```

**Integrationsspezifische Prompts:**

```
Connect this form to **CRM system** to create new leads. Map @firstName to FirstName, @email to Email, set LeadSource to "Web Form", and Status to "New"
```

```
Set up **workflow trigger** when form is submitted. Pass all form data and trigger approval workflow with manager notification
```

```
Configure **database integration** to save form submissions as records. Create new folder for each submission with uploaded documents
```

## Importieren und Konvertieren von Forms

**Verwendung:** Wenn Sie über vorhandene Formulare, Dokumente oder Designs verfügen, die in moderne AEM-Formulare umgewandelt werden sollen.

**Verwendung:** Laden Sie Ihre Quelldatei hoch und beschreiben Sie die Konvertierungsanforderungen (siehe [Importleitfaden](/help/edge/docs/forms/forms-ai-assistant-getting-started.md)).

**Beispiel-Prompt – PDF-Formularkonvertierung:**

```
Convert this uploaded **PDF application form** into a functional AEM adaptive form:

**Source Analysis:**
- Analyze the PDF layout and identify all form fields
- Preserve the visual hierarchy and grouping
- Maintain the professional appearance and branding

**Field Mapping:**
- Convert PDF text fields to adaptive form text inputs
- Transform checkboxes to checkbox components
- Convert dropdown lists to AEM dropdown components
- Map signature areas to digital signature fields

**Enhancements:**
- Add real-time validation that wasn't possible in PDF
- Implement conditional logic for dependent fields
- Make the form responsive for mobile devices
- Add progress saving capability
- Include accessibility improvements (ARIA labels, keyboard navigation)

**Styling:**
- Match the original color scheme and fonts
- Maintain professional business appearance
- Ensure consistent spacing and alignment
- Add subtle animations for better user experience

Preserve all original field labels and help text, but improve the user experience with modern form interactions
```

**Prompts für den Design-Import:**

```
Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness
```

```
Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields
```

```
Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes
```

## Optimierung und Reaktionsgeschwindigkeit bei Mobilgeräten

**Verwendung:** Wenn Formulare nahtlos über alle Gerätetypen und Bildschirmgrößen hinweg funktionieren sollen.

**Verwendung:** Beginnen Sie mit der grundlegenden Optimierung für Mobilgeräte und erweitern Sie sie dann mit erweiterten Funktionen. Betonen Sie den Mobile-First-Ansatz und legen Sie schrittweise das Verhalten bei Breakpoints fest.

**Beispiel-Prompt – Beginn mit der grundlegenden Optimierung für Mobilgeräte:**

```
Make @contactForm mobile-friendly with:

**Basic Mobile Layout:**
- Single column layout for all form sections
- Larger touch targets for buttons and inputs
- Responsive design that works on phones and tablets
```

**Fügen Sie dann erweiterte Funktionen für Mobilgeräte hinzu:**

```
Enhance @contactForm mobile experience with:
- Sticky submit button at bottom of screen
- Touch-friendly date pickers
- Swipe gestures for multi-step navigation
```

**Beispiel-Prompt – Umfassende Mobile-First-Optimierung:**

```
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
```

**Mobile-spezifische Eingabeaufforderungen:**

```
Make this form **touch-friendly** with larger buttons and simplified navigation for mobile users
```

```
Optimize form for **tablet users** with appropriate field sizes and navigation patterns
```

```
Add **swipe gestures** for multi-step form navigation on mobile devices
```

## Barrierefreiheit und Compliance

**Verwendung:** Wenn Formulare Barrierefreiheitsstandards (WCAG) oder Compliance-Anforderungen erfüllen müssen.

**Verwendung:** Geben Sie die erforderliche Konformitätsstufe und alle erforderlichen spezifischen Barrierefreiheitsfunktionen an.

**Beispielaufforderung - Grundlegende Barrierefreiheit:**

```
Make @contactForm accessible with:

**Basic Accessibility:**
- Proper ARIA labels for all form fields
- Keyboard navigation support
- High contrast color scheme
- Screen reader compatibility
- Focus indicators for all interactive elements
```

**Beispielaufforderung - Erweiterter Zugriff:**

```
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
```

**Barrierefreiheits-spezifische Eingabeaufforderungen:**

```
Add **screen reader support** to this form with proper ARIA labels and announcements
```

```
Implement **keyboard navigation** for all form interactions and navigation elements
```

```
Ensure **color contrast** meets WCAG AA standards for all text and interactive elements
```

## Leistungsoptimierung

**Verwendung:** Wenn Formulare schnell geladen werden und unter verschiedenen Bedingungen eine gute Leistung erzielen sollen.

**Verwendung:** Leistungsanforderungen und Optimierungsstrategien angeben.

**Beispielaufforderung - Grundlegende Leistung:**

```
Optimize @contactForm for performance:

**Loading Optimization:**
- Lazy load non-critical form sections
- Minimize initial bundle size
- Optimize images and assets
- Enable caching for static resources
```

**Beispielaufforderung - Erweiterte Leistung:**

```
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
```

**Leistungsspezifische Eingabeaufforderungen:**

```
Optimize form **loading speed** by implementing progressive loading and asset optimization
```

```
Add **auto-save functionality** to prevent data loss during form completion
```

```
Implement **offline support** so users can complete forms without internet connection
```

## Tests und Qualitätssicherung

**Verwendung:** Formulare müssen umfassend getestet werden, um Zuverlässigkeit und Benutzerzufriedenheit sicherzustellen.

**Verwendung:** Geben Sie Testszenarien, Validierungsanforderungen und Qualitätsmetriken an.

**Beispielaufforderung - Einfache Tests:**

```
Add comprehensive testing for @contactForm:

**Functional Testing:**
- Test all form field validations
- Verify submit functionality works correctly
- Test error handling and user feedback
- Validate conditional logic and rules
```

**Beispielaufforderung - Erweiterte Tests:**

```
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
```

**Testspezifische Prompts:**

```
Add **automated testing** for all form validations and submit functionality
```

```
Implement **user acceptance testing** scenarios for complete form workflows
```

```
Set up **performance monitoring** to track form load times and user interactions
```

## Fehlerbehebung

Schnelle Lösungen für häufige Probleme mit Forms Experience Builder:

| Problem | Schnellkorrektur |
|-------|-----------|
| Formular wird nicht gesendet | Konfiguration der Übermittlungsaktion und Validierungsregeln überprüfen |
| Validierungsfehler werden nicht angezeigt | Überprüfen der Feldüberprüfungseinstellungen und der Platzierung von Fehlermeldungen |
| Layoutprobleme für Mobilgeräte | Überprüfen der responsiven Designeinstellungen und der Feldgröße |
| Felder werden nicht angezeigt | Überprüfen von bedingten Logik- und Sichtbarkeitsregeln |
| Fehler beim Importieren | Überprüfen der Dateiformatkompatibilität und der Größenbeschränkungen |
| Integrationsfehler | Validieren von API-Endpunkten und Authentifizierungsberechtigungen |
| Leistungsprobleme | Optimieren Sie die Anzahl der Felder und entfernen Sie unnötige Validierungen |
| Probleme mit der Barrierefreiheit | Feldbezeichnungen, ARIA-Attribute und Registerkartenreihenfolge überprüfen |

**Debug-Modus-Eingabeaufforderung:**

```
Enable debug mode to identify issues with form submission and field validation
```

**Eingabeaufforderung zur Fehleranalyse:**

```
Analyze form errors: check validation rules, API responses, and user input patterns
```

## Erweiterte Analysen und Erkenntnisse

**Verwendung:** Wenn Sie die Formularleistung und das Benutzerverhalten verstehen müssen.

**Verwendung:** Sie die erforderlichen Analytics-Anforderungen und -Einblicke an.

**Beispielaufforderung - Einfache Analyse:**

```
Add analytics to @contactForm:

**Basic Metrics:**
- Form completion rates
- Field abandonment rates
- Submit success/failure rates
- User session duration
```

**Beispielaufforderung - Erweiterte Analyse:**

```
Implement comprehensive analytics for @applicationForm:

**User Behavior Analytics:**
- Track field completion rates and abandonment
- Monitor user session duration and patterns
- Analyze form navigation and user flow
- Identify bottlenecks and friction points

**Performance Analytics:**
- Measure form load times and performance
- Track API response times and failures
- Monitor validation rule effectiveness
- Analyze submission success rates

**Business Intelligence:**
- Generate reports on form effectiveness
- Track conversion rates and ROI
- Monitor user satisfaction and feedback
- Identify opportunities for optimization

**Predictive Analytics:**
- Predict form completion likelihood
- Identify users likely to abandon
- Recommend form improvements
- Optimize user experience based on data
```

**Analytics-spezifische Eingabeaufforderungen:**

```
Add **conversion tracking** to measure form completion rates and user behavior
```

```
Implement **A/B testing** to compare different form designs and optimize performance
```

```
Create **analytics dashboard** to monitor form performance and user insights
```

## Sicherheit und Datenschutz

**Verwendung:** Formulare verarbeiten sensible Daten und benötigen Sicherheitsmaßnahmen.

**Verwendung:** Geben Sie Sicherheitsanforderungen und Datenschutzmaßnahmen an.

**Beispielaufforderung - Einfache Sicherheit:**

```
Add security measures to @contactForm:

**Basic Security:**
- HTTPS encryption for all data transmission
- Input validation and sanitization
- CSRF protection for form submissions
- Secure session management
```

**Beispielaufforderung - Erweiterte Sicherheit:**

```
Implement comprehensive security for @applicationForm:

**Data Protection:**
- End-to-end encryption for sensitive data
- PII data masking and anonymization
- Secure file upload with virus scanning
- Data retention and deletion policies

**Access Control:**
- Role-based access control for form data
- Multi-factor authentication for admin access
- Audit logging for all data access
- Secure API authentication and authorization

**Compliance:**
- GDPR compliance for data handling
- HIPAA compliance for health information
- PCI DSS compliance for payment data
- SOC 2 compliance for data security

**Monitoring:**
- Real-time security monitoring and alerts
- Intrusion detection and prevention
- Data breach notification systems
- Regular security audits and assessments
```

**Sicherheitsspezifische Eingabeaufforderungen:**

```
Implement **data encryption** for sensitive form submissions and user information
```

```
Add **access control** to restrict form data access based on user roles and permissions
```

```
Set up **security monitoring** to detect and prevent unauthorized access to form data
```

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
| `/configure-submit` | Einrichten der Datenverarbeitung | `/configure-submit to CRM and send confirmation email` |
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
