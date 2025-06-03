---
title: AEM Forms AI Assistant - Prompt Library
description: Sammlung bewährter Eingabeaufforderungsmuster und Beispiele zum Erstellen von Formularen mit KI-Unterstützung in der Forms-Verwaltungsoberfläche, im adaptiven Forms-Editor und im universellen Editor.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: d3ade6ee9216b44b55d6808d8acffe83f1e263c9
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---



# AEM Forms AI Assistant - Prompt Library

Sammlung wiederverwendbarer Eingabeaufforderungsmuster und Beispiele für gängige Szenarien zur Formularerstellung. Stellen Sie sich diese Vorlagen vor, um sie an Ihre spezifischen Anforderungen anzupassen. In jedem Abschnitt wird ein bestimmtes Nutzungsszenario mit Hinweisen zur Verwendung und bewährten Beispielen behandelt.

>[!NOTE]
>
> Der KI-Assistent für AEM Forms ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie eine E-Mail von Ihrer Geschäftsadresse an mailto:aem-forms-ea@adobe.com , um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Eingabeaufforderungsbibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Eingabeaufforderungen, Beispiele und Best Practices können sich ändern, da sich der KI-Assistent für AEM Forms während des Early-Adopter-Programms weiterentwickelt.

## Best Practices für optimale Ergebnisse

Um den KI-Assistenten optimal zu nutzen, sollten Sie die folgenden Tipps beachten:

### Einfach beginnen, inkrementell erstellen

Beginnen Sie mit kleineren, spezifischen Befehlen (z. B. „Fügen Sie eine Texteingabe für „Vorname“ hinzu„) anstatt zu komplexer mehrstufiger Anfragen. Dieser Ansatz hilft, Genauigkeit sicherzustellen, und erleichtert die Fehlerbehebung, wenn etwas nicht wie erwartet funktioniert.

**Beispiel für einfachen Start:**

```
Add a text input field for "First Name" with placeholder "Enter your first name"
```

**Erstellen Sie dann inkrementell:**

```
Make @firstName mandatory and add validation message "First name is mandatory"
```

### Verwenden der Terminologie von AEM Forms

Verwenden Sie Begriffe wie „Bedienfeld“, „Texteingabefeld“, „Kontrollkästchen-Gruppe“, „Übermittlungsaktion“, „Regel“ usw., um das Verständnis durch den Assistenten zu verbessern. Dadurch wird sichergestellt, dass die KI Ihre Anfragen im AEM Forms-Kontext korrekt interpretiert.

**Bevorzugte Begriffe:**

- „Textfeld“ anstelle von „Textfeld“
- „Kontrollkästchen-Gruppe“ anstelle von „Kontrollkästchen“
- „Dropdown“ anstelle von „Liste auswählen“
- „Bedienfeld“ anstelle von „Abschnitt“ oder „Container“
- „Übermittlungsaktion“ anstelle von „Formularübermittlung“
- „Regel“ anstelle von „Logik“ oder „Bedingung“

### Referenzfelder klar

Verwenden Sie beim Konfigurieren vorhandener Felder die @fieldName (z. B. &quot;@firstName obligatorisch machen„). Dies hilft der KI, genau zu erkennen, auf welches Feld Sie sich beziehen, insbesondere in komplexen Formularen mit vielen Feldern.

**Beispiele:**

- `Make @email mandatory with real-time validation`
- `Show @spouseInfo panel when @maritalStatus equals "Married"`
- `Set @country default value to "United States"`

### Pläne immer überprüfen

Prüfen Sie die Pläne stets sorgfältig auf vom Assistenten vorgeschlagene Änderungen im universellen Editor, bevor Sie auf „Anwenden“ klicken. Die KI zeigt Ihnen, was sie plant - nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob dies Ihren Erwartungen entspricht.

### Manuell validieren

Nachdem der Assistent Änderungen vorgenommen hat, sollten Sie Ihr Formular immer in der Vorschau anzeigen und testen, um sicherzustellen, dass es sich wie erwartet verhält und aussieht. KI ist ein leistungsstarkes Tool, aber die endgültige Validierung ist der Schlüssel zur Qualitätssicherung.

**Validierungs-Checkliste:**

- Testen der Formularfunktionalität im Vorschaumodus
- Überprüfen, ob die bedingte Logik ordnungsgemäß funktioniert
- Reaktionsfähigkeit auf Mobilgeräte prüfen
- Testformularübermittlung
- Validieren der Barrierefreiheitsfunktionen

### Iterieren und verfeinern

Wenn die erste Eingabeaufforderung nicht das genaue Ergebnis liefert, versuchen Sie, die Anfrage neu zu formulieren oder in kleinere Schritte aufzuteilen. Die KI lernt aus dem Kontext, sodass die Bereitstellung spezifischerer Details oft die Ergebnisse verbessert.

**Iterationsbeispiel:**

1. Erster Versuch: „Formular mobilfreundlich gestalten“
2. Verfeinert: „Optimieren Sie das Formular-Layout für mobile Bildschirme unter 768 Pixel mit einspaltigem Layout und größeren Touch-Zielen“

### Feedback geben

Verwenden Sie den integrierten Feedback-Mechanismus, damit die Assistenzkraft lernen und sich verbessern kann. Ihr Feedback hilft dabei, die KI für alle besser zu machen.


## Beispiele für inkrementelle Entwicklung

Diese Beispiele zeigen, wie Sie Formulare Schritt für Schritt erstellen, einfach anfangen und schrittweise Komplexität hinzufügen:

### Beispiel 1: Inkrementelles Erstellen eines Kontaktformulars

**Schritt 1 - Einfach starten:**

```
Create a basic contact form with name, email, and message fields
```

**Schritt 2: Validierung hinzufügen:**

```
Make @name and @email mandatory fields with appropriate validation
```

**Schritt 3: Verbessern des Benutzererlebnisses:**

```
Add placeholder text: @name "Your full name", @email "your.email@company.com", @message "Tell us how we can help"
```

**Schritt 4: Erweiterte Funktionen hinzufügen:**

```
Add a dropdown @inquiryType with options: "General Question", "Support Request", "Sales Inquiry", "Partnership"
```

**Schritt 5: Implementieren einer bedingten Logik:**

```
Show @urgencyLevel dropdown (Low, Medium, High) only when @inquiryType equals "Support Request"
```

### Beispiel 2: Inkrementelles Erstellen eines Registrierungsformulars

**Schritt 1: Grundstruktur:**

```
Create a user registration form with personal information panel
```

**Schritt 2: Hinzufügen von Kernfeldern:**

```
Add text input fields: @firstName, @lastName, @email, @phone to the personal information panel
```

**Schritt 3 - Validierung hinzufügen:**

```
Make @firstName, @lastName, and @email mandatory with real-time validation
```

**Schritt 4: Hinzufügen von Kontoinformationen:**

```
Create a new panel "Account Information" with @username and @password fields
```

**Schritt 5: Verbesserung der Sicherheit:**

```
Add password confirmation field @confirmPassword with validation to match @password
```

**Schritt 6: Voreinstellungen hinzufügen:**

```
Create "Preferences" panel with @newsletter checkbox and @communicationMethod radio group (Email, SMS, Phone)
```

Dieser inkrementelle Ansatz hilft Ihnen bei Folgendem:

- Probleme frühzeitig erkennen, bevor sie zunehmen
- Testen Sie jede Funktion gründlich
- Nehmen Sie Anpassungen auf der Grundlage des Benutzer-Feedbacks vor
- Bessere Kontrolle über den Entwicklungsprozess

## Starten von New Forms

**Verwendung:** Am Anfang jedes Formularprojekts. Diese Eingabeaufforderung hilft der KI, Ihre Anforderungen zu verstehen und die Foundation-Struktur zu erstellen.

**Verwendung:** Beginnen Sie mit der grundlegenden Struktur und den grundlegenden Anforderungen. Geben Sie den Formulartyp, die Zielgruppe und den Hauptzweck an. Komplexität in nachfolgenden Eingabeaufforderungen hinzufügen.

**Beispielaufforderung - Einfaches Starten:**

```
Create a **customer onboarding form** for new bank account applications with:

**Purpose:** Collect personal information for account setup
**Target Users:** New customers applying for checking/savings accounts
**Basic Structure:** Single panel with essential fields
**Core Fields:** Name, email, phone, account type selection

Start with a simple layout that we can enhance step by step.
```

**Erstellen Sie dann inkrementell:**

```
Add an address panel to @customerOnboardingForm with street address, city, state, and zip code fields
```

```
Add employment information panel with @employer, @jobTitle, and @annualIncome fields
```

```
Add file upload field @identityDocuments for identity verification (Accept: .pdf,.jpg,.png)
```

**Alternative einfache Startaufforderungen:**

```
Create a basic **event registration form** with name, email, and event selection fields
```

```
Build a simple **contact form** with name, email, and message fields
```

```
Design a basic **feedback survey** with rating scale and comments field
```

## Formularstruktur und -layout

**Verwendung:** Wenn Sie komplexe Formulare organisieren oder das Benutzererlebnis durch besseres Layout-Design verbessern müssen.

**Verwendung:** Fokus auf die Benutzer-Journey und die logische Gruppierung von Informationen. Legen Sie Layout-Voreinstellungen und Navigationsmuster fest.

**Beispielaufforderung - Mehrstufige Formularstruktur:**

```
Convert this single-page form into a **3-step wizard** with:

**Step 1: Personal Information**
- Name, email, phone, address fields
- Progress indicator showing "Step 1 of 3"
- "Next" button (validate mandatory fields before proceeding)

**Step 2: Preferences & Requirements** 
- Service selection (checkbox group)
- Budget range (dropdown)
- Timeline preferences (radio group)
- Special requirements (text input field)

**Step 3: Review & Submit**
- Summary of all entered information
- Edit links to go back to specific steps
- Terms and conditions checkbox
- Submit button with confirmation

Include "Previous" and "Next" buttons, allow users to jump between completed steps, save progress automatically.
```

**Eingabeaufforderungen zur Layout-Optimierung:**

```
Reorganize this form using a **wizard layout** for desktop and single column for mobile. 
```

```
Convert this long form into an **accordion layout** where users can expand/collapse sections.
```

```
Create a **vertical tabbed interface** for this form with tabs for: Basic Info, Contact Details, Preferences, and Review.
```

## Feldverwaltung und -validierung

**Verwendung:** Wenn Sie Formularfelder mit bestimmten Validierungsregeln und -verhaltensweisen hinzufügen, ändern oder erweitern müssen.

**Verwendung:** Sie sich speziell mit Feldtypen, Validierungsanforderungen und Erwartungen an das Benutzererlebnis. Referenzieren Sie vorhandene Felder mithilfe @fieldName Syntax.

**Beispielaufforderung - Feldverbesserung:**

```
Enhance the form fields with these specific requirements:

**Email Field (@email):**
- Make mandatory with real-time validation
- Show green checkmark when valid format entered
- Display helpful error message: "Please enter a valid email address"
- Add placeholder: "your.email@company.com"

**Phone Number (@phone):**
- Type: tel for mobile optimization
- Make mandatory for business customers, optional for personal
- Add placeholder: "Enter your phone number"

**Date of Birth (@dateOfBirth):**
- Type: date with date picker
- Validate age is 18+ for account opening
- Show error if under 18: "Must be 18 or older to open account"

**File Upload (@documents):**
- Accept: .pdf,.doc,.docx
- Multiple: true for multiple document upload
- Show upload progress and file names after upload
```

**Feldspezifische Eingabeaufforderungen:**

```
Add a **file upload field** for resume with these specs: Accept only PDF/DOC/DOCX files, allow multiple files, show upload progress, display file names after upload.
```

```
Create a **dropdown field** for country selection with all countries listed. Set default value based on user's location if available.
```

```
Build a **repeatable panel** for work experience where users can add/remove multiple jobs. Each entry needs: company, title, start date, end date, description.
```

## Bedingte Logik und Regeln

**Verwendung:** Wenn Sie ein dynamisches Formularverhalten benötigen, das auf Benutzereingaben oder Geschäftsregeln basiert.

**Verwendung:** Definieren Sie die Bedingungen und die resultierenden Aktionen klar. Verwenden Sie bestimmte Feldverweise und logische Operatoren.

**Beispielaufforderung - Komplexe bedingte Logik:**

```
Implement these conditional rules for the application form:

**Business vs Personal Account Logic:**
- If @accountType equals "Business", show:
  - Business name field (mandatory)
  - Tax ID field (mandatory)
  - Business address section
  - Number of employees dropdown
- If @accountType equals "Personal", hide all business fields

**Income-Based Requirements:**
- If @annualIncome is less than 25000:
  - Show additional verification section
  - Make co-signer information mandatory
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

**Regelspezifische Eingabeaufforderungen:**

```
Create a **visibility rule** that shows @spouseInformation panel only when @maritalStatus equals "Married" or "Domestic Partnership".
```

```
Add **progressive disclosure** where additional questions appear based on previous answers. Start with basic info, then show relevant follow-ups.
```

```
Implement **smart defaults** where @country selection auto-sets related fields. Allow manual override.
```

## Datenintegration und -übertragung

**Verwendung:** Wenn Sie Formulare mit Backend-Systemen, Datenbanken oder externen Services verbinden müssen.

**Verwendung:** Beginnen Sie mit der grundlegenden Einrichtung der Übermittlung und fügen Sie dann schrittweise zusätzliche Integrationen hinzu. Geben Sie den Integrationstyp, die Datenformatanforderungen und die Voreinstellungen für die Fehlerbehandlung an.

**Beispielaufforderung - Beginn mit einfacher Übermittlung:**

```
Configure basic form submission for @applicationForm:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Format data as JSON
- Show success message: "Application submitted successfully"
- Show error message if submission fails: "Submission failed, please try again"
```

**Fügen Sie dann Sekundäre Aktionen schrittweise hinzu:**

```
Add email notification to @applicationForm: Send confirmation email to @email address with application reference number
```

```
Add CRM integration to @applicationForm: Create new lead record with @firstName, @lastName, @email, and set Status to "New Application"
```

**Beispielaufforderung - Erweiterte Multi-Channel-Übermittlung:**

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

**Integrationsspezifische Eingabeaufforderungen:**

```
Connect this form to **CRM system** to create new leads. Map @firstName to FirstName, @email to Email, set LeadSource to "Web Form", and Status to "New".
```

```
Set up **workflow trigger** when form is submitted. Pass all form data and trigger approval workflow with manager notification.
```

```
Configure **database integration** to save form submissions as records. Create new folder for each submission with uploaded documents.
```

## Design-Import und -Konversion

**Verwendung:** Wenn Sie bereits Formularentwürfe (PDF, Figma, Bilder) haben, die in funktionale AEM-Formulare konvertiert werden müssen.

**Verwendung:** Geben Sie einen klaren Kontext zum Quell-Design an und geben Sie alle erforderlichen Änderungen oder Verbesserungen an.

**Beispielaufforderung - PDF-Formularkonvertierung:**

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

Preserve all original field labels and help text, but improve the user experience with modern form interactions.
```

**Design-Importaufforderungen:**

```
Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness.
```

```
Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields.
```

```
Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes.
```

## Optimierung und Reaktionsgeschwindigkeit von Mobilgeräten

**Verwendung:** Formulare müssen nahtlos über alle Gerätetypen und Bildschirmgrößen hinweg funktionieren.

**Verwendung:** Sie mit der grundlegenden Optimierung für Mobilgeräte und erweitern Sie sie dann mit erweiterten Funktionen. Mobile-First-Ansatz betonen und Breakpoint-Verhalten inkrementell angeben.

**Beispielaufforderung - Beginn mit der grundlegenden Optimierung für Mobilgeräte:**

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

**Beispielaufforderung - Umfassende Mobile-First-Optimierung:**

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

**Touch Optimization:**
- Larger checkbox and radio button targets
- Swipe gestures for multi-step navigation
- Pull-to-refresh for saved drafts
- Touch-friendly date/time pickers

**Performance:**
- Lazy load non-critical form sections
- Optimize images and icons for mobile
- Minimize JavaScript for faster loading
- Progressive enhancement approach
```

**Mobile-spezifische einfache Eingabeaufforderungen:**

```
Make @checkoutForm mobile-optimized with large buttons and one-thumb navigation
```

```
Add touch-friendly controls to @surveyForm for tablet users
```

```
Enable offline functionality for @applicationForm with local data saving
```

## Barrierefreiheit und Compliance

**Verwendung:** Wenn Formulare Barrierefreiheitsstandards (WCAG 2.1 AA) oder Compliance-Anforderungen erfüllen müssen.

**Verwendung:** Geben Sie die Anforderungen an die Barrierefreiheit und die Compliance-Standards an, die erfüllt werden müssen.

**Beispielaufforderung - Implementierung der Barrierefreiheit:**

```
Make this form **WCAG 2.1 AA compliant** with these accessibility features:

**Keyboard Navigation:**
- Logical tab order through all form elements
- Skip links to main content and form sections
- Keyboard shortcuts for common actions
- Focus indicators clearly visible on all interactive elements

**Screen Reader Support:**
- Proper ARIA labels for all form fields
- Descriptive error messages announced to screen readers
- Form section headings with proper hierarchy (h1, h2, h3)
- Progress announcements for multi-step forms

**Visual Accessibility:**
- Color contrast ratio minimum 4.5:1 for text
- Don't rely solely on color to convey information
- Text size minimum 16px for body text
- Scalable up to 200% without horizontal scrolling

**Motor Accessibility:**
- Large click targets (minimum 44x44px)
- Generous spacing between interactive elements
- No time limits or provide extension options
- Alternative input methods support

**Cognitive Accessibility:**
- Clear, simple language in all instructions
- Consistent navigation and layout patterns
- Error prevention and clear error recovery
- Help text and examples for complex fields

**Testing Requirements:**
- Test with screen readers (NVDA, JAWS, VoiceOver)
- Verify keyboard-only navigation
- Check color contrast with automated tools
- Validate HTML for semantic correctness
```

**Compliance-spezifische Eingabeaufforderungen:**

```
Ensure this **healthcare form meets HIPAA requirements** with proper data encryption, audit logging, and privacy controls.
```

```
Make this **financial form PCI DSS compliant** with secure payment field handling and data protection measures.
```

```
Create a **government form meeting Section 508 standards** with full accessibility and plain language requirements.
```

## Assurance für Tests und Qualität

**Verwendung:** Wenn Sie die Formularfunktionalität, das Benutzererlebnis und die technische Leistung überprüfen müssen.

**Verwendung:** Geben Sie Testszenarien, Edge-Fälle und Qualitätskriterien an, die überprüft werden müssen.

**Beispielaufforderung - Umfassende Formulartests:**

```
Create a **comprehensive testing plan** for this application form:

**Functional Testing:**
- Test all field validations with valid and invalid data
- Verify conditional logic shows/hides fields correctly
- Test file upload with various file types and sizes
- Validate calculation fields update correctly
- Test form submission with complete and incomplete data

**User Experience Testing:**
- Test form completion time (target: under 10 minutes)
- Verify error messages are helpful and actionable
- Test progress saving and restoration
- Validate mobile touch interactions
- Check form accessibility with assistive technologies

**Edge Case Testing:**
- Test with extremely long text inputs
- Verify behavior with special characters and emojis
- Test with slow internet connections
- Validate offline functionality if applicable
- Test browser back/forward button behavior

**Performance Testing:**
- Measure form load time (target: under 3 seconds)
- Test with large file uploads
- Verify memory usage with long form sessions
- Test concurrent user submissions
- Validate database performance under load

**Security Testing:**
- Test input sanitization and XSS prevention
- Verify CSRF protection is working
- Test file upload security restrictions
- Validate data encryption in transit and at rest
- Check authentication and authorization controls

**Cross-Browser Testing:**
- Test on Chrome, Firefox, Safari, Edge
- Verify mobile browsers (iOS Safari, Chrome Mobile)
- Test on different operating systems
- Validate older browser fallbacks
- Check print functionality across browsers
```

**Testspezifische Eingabeaufforderungen:**

```
Create **automated test scripts** for this form's critical user paths: successful submission, validation errors, and conditional logic.
```

```
Design a **user acceptance testing plan** with realistic scenarios and success criteria for business stakeholders.
```

```
Set up **performance monitoring** to track form completion rates, abandonment points, and submission success rates.
```

## Erweiterte Funktionen und Integrationen

**Verwendung:** Wenn Sie ausgereifte Formularfunktionen wie KI-Unterstützung, erweiterte Workflows oder komplexe Integrationen benötigen.

**Verwendung:** Definieren Sie die erweiterten Funktions- und Integrationsanforderungen klar.

**Beispielaufforderung - KI-verbessertes Formular:**

```
Add **AI-powered features** to enhance this application form:

**Smart Auto-Complete:**
- Use AI to suggest company names as user types
- Auto-populate address fields from partial input
- Suggest job titles based on industry selection
- Provide intelligent form completion suggestions

**Dynamic Question Generation:**
- Generate follow-up questions based on previous answers
- Adapt form complexity to user's experience level
- Show relevant optional fields based on user profile
- Personalize form sections for different user types

**Intelligent Validation:**
- Use AI to detect potentially incorrect information
- Suggest corrections for common data entry errors
- Validate business information against public databases
- Flag suspicious or inconsistent responses

**Content Optimization:**
- A/B test different form layouts automatically
- Optimize field order based on completion patterns
- Adjust form length based on user engagement
- Personalize help text based on user behavior

**Predictive Analytics:**
- Predict likelihood of form completion
- Identify users who might need assistance
- Suggest optimal times for form completion reminders
- Analyze drop-off points and suggest improvements

**Natural Language Processing:**
- Allow voice input for text fields
- Convert speech to text for accessibility
- Analyze open-text responses for sentiment
- Extract structured data from unstructured input
```

**Eingabeaufforderungen zur erweiterten Integration:**

```
Integrate with **CRM system** to pre-populate known customer data, update records in real-time, and trigger automated follow-up sequences.
```

```
Connect to **payment gateway** for secure transaction processing with PCI compliance, fraud detection, and multiple payment methods.
```

```
Implement **blockchain verification** for document authenticity, immutable audit trails, and decentralized identity verification.
```

## Fehlerbehebung und Optimierung

**Verwendung:** Wenn Formulare Leistungsprobleme, Probleme mit dem Benutzererlebnis oder technische Schwierigkeiten aufweisen.

**Verwendung:** Beschreiben Sie das spezifische Problem und das gewünschte Ergebnis klar und deutlich.

**Beispielaufforderung - Leistungsoptimierung:**

```
Optimize this form for **better performance and user experience**:

**Current Issues:**
- Form takes 8+ seconds to load on mobile
- Users are abandoning at the address section (60% drop-off)
- File uploads frequently fail or timeout
- Validation errors are confusing users

**Performance Improvements:**
- Implement lazy loading for non-critical form sections
- Optimize images and reduce bundle size
- Add progressive loading indicators
- Cache frequently used data (country lists, etc.)
- Minimize JavaScript execution time

**User Experience Fixes:**
- Simplify the address section with auto-complete
- Add inline validation with helpful error messages
- Implement smart defaults based on user location
- Add progress saving every 30 seconds
- Provide clear instructions for each section

**Technical Optimizations:**
- Implement chunked file uploads with resume capability
- Add client-side validation before server submission
- Optimize database queries for faster responses
- Implement proper error handling and retry logic
- Add comprehensive logging for debugging

**Monitoring & Analytics:**
- Set up form analytics to track user behavior
- Monitor completion rates by section
- Track error rates and types
- Measure performance metrics continuously
- A/B test improvements with real users
```

**Eingabeaufforderungen zur Fehlerbehebung:**

```
**Debug this form submission error:** Users report getting "500 Internal Server Error" when submitting. Check validation logic, server endpoints, and data formatting.
```

```
**Fix mobile layout issues:** Form fields are overlapping on iPhone screens and submit button is not visible. Ensure proper responsive design.
```

```
**Resolve validation conflicts:** Some users can't submit even with valid data. Review validation rules for conflicts and edge cases.
```

## Umgebungsspezifische Best Practices

### Forms-Verwaltungsoberfläche

**Verwendung:** Für allgemeine Aufgaben zur Formularerstellung und -verwaltung.

```
In Forms Management UI, create a new **customer survey template** that can be reused across different departments. Include standard branding, common field types, and configurable sections.
```

### Adaptiver Forms-Editor

**Verwendung:** Für eine detaillierte Formularkonfiguration und die Erstellung komplexer Regeln.

```
In the Adaptive Forms Editor, configure **advanced business rules** for this loan application: calculate debt-to-income ratio, determine eligibility, and show appropriate next steps.
```

### Universeller Editor

**Verwendung:** Für Edge Delivery Services Forms mit visueller Bearbeitung.

```
In Universal Editor, create a **responsive contact form** for the company website. Ensure it matches the site design and integrates with the existing content management workflow.
```

## Kurzanleitung zur Befehlsreferenz

| Befehl | Best-Use-Case | Beispiel |
|---------|---------------|---------|
| `/create-form` | Starten neuer Formulare | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Hinzufügen von Formularen zu Seiten | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | Änderung der Formularstruktur | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Ändern von Feldeigenschaften | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Dynamisches Verhalten hinzufügen | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Organisieren von Formularabschnitten | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Konvertieren von Designs | `/add-panel from uploaded form image with field recognition` |
| `/configure-submit` | Einrichten der Datenverarbeitung | `/configure-submit to CRM and send confirmation email` |
| `/help` | Hilfe anfordern | `/help how to implement multi-step validation?` |

## Referenz zu unterstützten Komponenteneigenschaften

### Universelle Eigenschaften (alle Komponenten)

- **Typ**: Komponententyp (Text, E-Mail, Nummer, Tel, Datum, Kontrollkästchen, Radio, Dropdown, Datei usw.)
- **Name**: Feldkennung für die Formularübermittlung
- **Label**: Zeigt Text für das Feld an
- **Beschreibung**: Hilfetext für das Feld
- **Visible**: Boolesch für anfängliche Sichtbarkeit
- **Obligatorisch**: Boolesch für erforderliche Felder

### Eingabefeld-Eigenschaften

- **Wert**: Standard-/Anfangswert
- **Platzhalter**: Hinweistext für Eingabefelder
- **Min**: Mindestwert (für Zahlen/Daten)
- **Max**: Höchstwert (für Zahlen/Daten)

### Eigenschaften des Datei-Uploads

- **Accept**: Dateitypen (.pdf, .doc, .docx, .jpg, .png usw.)
- **multiple**: Boolescher Wert für die Auswahl mehrerer Dateien

### Eigenschaften des Auswahlsteuerelements

- **Optionen**: Optionen für Dropdown-Listen (durch Kommas getrennte Liste)
- **aktiviert**: Standardauswahl für Kontrollkästchen/Optionsfelder

### Container-Eigenschaften

- **FieldSet**: Gruppieren verwandter Felder
- **repeatable**: Boolescher Wert für wiederholbare Abschnitte

### Erweiterte Eigenschaften

- **Sichtbarer Ausdruck**: Formel für bedingte Sichtbarkeit (=Formel)
- **Wert Ausdruck**: Formel für berechnete Werte (=Formel)

## Zusammenfassung der Best Practices

### Technische Leitlinien

- **Nur unterstützte Eigenschaften verwenden** aus der offiziellen AEM Forms-Komponentenspezifikation
- **Die korrekte Syntax** für Feldverweise (@fieldName) und Ausdrücke (=Formel)
- **Inkrementelles** nach jeder Änderung, um Probleme frühzeitig zu erkennen
- **Planen Sie die** von Anfang an, nicht als nachträgliche Überlegung
- **Bei jeder Design** Entscheidung werden mobile Benutzer berücksichtigt
- **Komplexe Regeln dokumentieren** für die zukünftige Wartung und Team-Zusammenarbeit

### Strategischer Ansatz

- **Mit Benutzeranforderungen beginnen** - Konzentrieren Sie sich auf die Aufgaben, die Benutzer erfüllen müssen, nicht nur auf technische Funktionen
- **Design für die Vervollständigung** - Minimieren Sie Reibung und kognitive Belastung im Formularentwurf
- **Datenfluss planen** frühzeitig - Überlegen Sie, wie Daten verarbeitet, gespeichert und verwendet werden
- **Für Skalierung erstellen** - Entwerfen Sie Formulare, die das erwartete Benutzervolumen und Datenwachstum verarbeiten können
- **Progressive Verbesserung implementieren** - Sicherstellen, dass die grundlegenden Funktionen funktionieren, und dann erweiterte Funktionen hinzufügen

### Häufige zu vermeidende Fehler

- **Zu komplexe anfängliche Anfragen** - Unterteilen Sie große Aufgaben in kleinere, verwaltbare Schritte
- **Verwenden nicht unterstützter Eigenschaften** nicht in der AEM Forms-Spezifikation
- **Mobile Erlebnisse werden** bis zum Ende des Entwicklungsprozesses ignoriert
- **Benutzertests überspringen** mit echten Szenarien und Edge-Fällen
- **Vorausgesetzt, dass KI den Kontext versteht** ohne klare, spezifische Anweisungen zu geben
- **Vergessen von Barrierefreiheit** und Compliance-Anforderungen
- **Änderungen werden nicht**, bevor mit dem nächsten Schritt fortgefahren wird

### Assurance-Qualitätsansatz

1. **Häufig Vorschau** - Überprüfen Sie Ihre Arbeit im Vorschaumodus nach jeder wichtigen Änderung.
2. **Testen von Randfällen** - Versuchen Sie ungewöhnliche Eingaben, langen Text, Sonderzeichen
3. **Geräteübergreifend validieren** - Testen auf Smartphones, Tablets und Desktop
4. **Barrierefreiheit überprüfen** - Überprüfen Sie die Tastaturnavigation und die Kompatibilität der Bildschirmlesehilfen.
5. **Leistungstest** - Sicherstellen, dass Formulare schnell geladen werden und reibungslos reagieren
6. **Benutzerakzeptanztests** Lassen Sie echte Benutzer das Formular vor der Bereitstellung testen


*Diese Eingabeaufforderungsbibliothek wird laufend auf der Grundlage von Benutzer-Feedback und neuen KI-Assistenten-Funktionen aktualisiert. Die neuesten Funktionen und Beispiele finden Sie in der [Dokumentation zu AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=de).*
