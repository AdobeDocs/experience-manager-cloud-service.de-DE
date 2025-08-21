---
title: Erste Schritte mit Forms Experience Builder
description: Erfahren Sie, wie Sie mit Forms Experience Builder Formulare mit progressiver Offenlegung für alle Benutzertypen erstellen und verwalten können
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: da429952-ccc0-4579-a243-8bddeb73a0fb
source-git-commit: 8be2b09200af58c701721b3e8537ea5e6cc3e4a2
workflow-type: tm+mt
source-wordcount: '1720'
ht-degree: 15%

---

# Erste Schritte mit Forms Experience Builder

>[!NOTE]
>
> Die Funktion Forms Experience Builder ist im Rahmen des **Early-Adopter-Programms** verfügbar. Bei Interesse senden Sie eine kurze E-Mail von Ihrer Geschäftsadresse an `aem-forms-ea@adobe.com`, um Zugriff auf die Funktion zu beantragen.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Dokumentation wird derzeit mit dem Produkt getestet und unterliegt möglichen Aktualisierungen und Überarbeitungen. Funktionen, Befehle und Beispiele können sich ändern, wenn Forms Experience Builder während des Early-Adopter-Programms weiterentwickelt wird.

Dieses umfassende Handbuch hilft Ihnen bei den ersten Schritten beim Erstellen und Verwalten von Formularen mithilfe der konversativen KI-Technologie. Unabhängig davon, ob Sie Anfänger sind oder Ihr erstes Formular erstellen möchten oder fortgeschrittene Benutzer, die komplexe Funktionen nutzen möchten, finden Sie hier detaillierte Informationen und praktische Beispiele, die Ihren Journey durch die Funktionen von Forms Experience Builder führen.

## Voraussetzungen und Einrichtung

### &#x200B;1. Zugriff anfordern

Wenn Sie keinen Zugriff auf Forms Experience Builder haben:

1. **Zugriff anfordern**: Senden einer E-Mail an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) von Ihrer geschäftlichen E-Mail
2. **Informationen einschließen**: Organisationsname und Projektdetails
3. **Auf Genehmigung warten**: Adobe prüft und stellt Onboarding-Anweisungen bereit

### &#x200B;2. Überprüfen, ob Forms aktiviert ist

Stellen Sie vor der Verwendung von Forms Experience Builder sicher, dass [AEM Forms für Ihre Umgebung aktiviert ](/help/forms/setup-forms-cloud-service.md).


### &#x200B;3. Einrichten der Umgebung


* **Für Edge Delivery Services (EDS):**

   * [Setup-Umgebung für Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
   * [Erstellen eines neuen Formulars mit der Edge Delivery Forms-Vorlage](/help/edge/docs/forms/universal-editor/create-forms.md)

* **Auf Kernkomponenten basierende Formulare:**

   * Gehen Sie in Ihrer Adobe Experience Manager-Instanz zu Forms > Forms und Dokumente .
   * [Erstellen einer neuen Seite mithilfe der Kernkomponentenvorlage](/help/forms/creating-adaptive-form-core-components.md)

## Schnellstart

### Zugriff auf Forms Experience Builder

**Universeller Editor**

* Öffnen Sie Ihre EDS-Seite im universellen Editor
* Suchen Sie im linken Bedienfeld nach dem Forms Experience Builder-Symbol
* Zum Öffnen der Konversationsoberfläche klicken

**Editor für adaptive Formulare**

* Navigieren Sie zu: AEM > Forms > Forms und Dokumente
* Erstellen oder Öffnen eines auf Kernkomponenten basierenden Formulars zur Bearbeitung
* Klicken Sie auf das Forms Experience Builder-Symbol in der Editor-Symbolleiste

### Ihr erstes Formular

Versuchen Sie diese einfache Unterhaltung, um loszulegen:

```
👤 You: "Create a simple contact form"
🤖 AI: "I'll create a contact form with name, email, and message fields for you."

👤 You: "Make the email field required"
🤖 AI: "Updated the email field to be required with validation."
```

### Wesentliche Befehle

| Symbol | Zweck | Verwendung |
|--------|---------|------------|
| `/` | Schnellaktionen und Tastaturbefehle | Geben Sie `/create` für die Formularerstellung ein, `/help` Sie Hilfe benötigen |
| `@` | Referenzieren vorhandener Formularfelder | Geben Sie `@fieldName` ein, um bestimmte Felder zu ändern (z. B. `@email`) |
| Nur Text | Natürliche Konversation | Beschreiben Sie, was Sie möchten: „Erforderliches Telefonnummernfeld hinzufügen“ |

### Tipps zum Erfolg

* **Sei spezifisch**: „Ein erforderliches E-Mail-Feld mit Validierung hinzufügen“ funktioniert besser als „E-Mail hinzufügen“
* **Vorhandene Felder referenzieren**: `@fieldName` beim Ändern von Formularen verwenden
* **Um Hilfe bitten**: Geben Sie `/help` ein, gefolgt von Ihrer Frage
* **Iterieren**: Führen Sie jeweils nur eine Änderung durch, um optimale Ergebnisse zu erzielen

## Hauptfunktionen

### Zwei Möglichkeiten zum Erstellen von Forms

#### &#x200B;1. Erstellen von Grund auf

Beschreiben Sie Ihre Formularanforderungen in natürlicher Sprache, und Forms Experience Builder generiert die vollständige Formularstruktur:

**Beispiele:**

* „Erstellen eines Kreditantragsformulars mit persönlichen Informationen, finanziellen Details und Dokument-Uploads“
* „Erstellen Sie ein Formular für Kunden-Feedback mit Bewertungen, Kommentaren und Produktkategorien.“
* „Ich benötige ein mehrstufiges Anmeldeformular für eine Konferenz mit Zahlungsabwicklung“

#### &#x200B;2. Importieren und Konvertieren

Transformieren vorhandener Formulare und Dokumente in moderne, interaktive Erlebnisse:

**Unterstützte Quellen:**

* **PDF forms**: Laden Sie statische PDFs → interaktive digitale Formulare mit Validierung hoch
* **Screenshots/Bilder**: Foto von Papierformularen → funktionale digitale Versionen
* **HTML Forms**: Grundlegende Web-Formulare → Erweitertes AEM Forms mit erweiterten Funktionen
* **XFA Forms**: Ältere Adobe-Formulare → Moderne responsive Formulare
* **URLs**: Vorhandene Web-Formulare → native AEM Forms mit verbesserter Benutzerfreundlichkeit

**So importieren Sie:**

1. Klicken Sie auf das Anlagensymbol in der Benutzeroberfläche von Forms Experience Builder
2. Datei hochladen (PDF, Bild, Figma-Design usw.)
3. Beschreiben Sie Ihre Anforderungen:
   * „Konvertieren Sie dieses PDF-Formular in eine digitale Version.“
   * „Erstellen Sie ein Formular, das diesem Screenshot-Layout entspricht“
   * „Baue dieses Formular aus meinem Figma-Design“

**Unterstützte Dateitypen:**

* **Bilder** (PNG, JPG, GIF): Formular-Layouts, UI-Mockups, gescannte Formulare
* **PDF-Dateien**: Vorhandene Formulare, Spezifikationen, Dokumente
* **Figma Files**: Design-Prototypen, Markenrichtlinien
* **Design-Dateien**: Visuelle Verweise, Stilrichtlinien

### Wichtige Interaktionen

#### Hinzufügen von Formularelementen

**Einfache Ergänzungen:**

```
👤 You: "Add a section for personal information"
🤖 AI: "Added a personal information panel with standard fields"

👤 You: "Include a file upload for resume"
🤖 AI: "Added a secure file upload component for documents"

👤 You: "Add a dropdown for country selection"
🤖 AI: "Added a country dropdown with common options"
```

**Detaillierte Spezifikationen:**

```
👤 You: "Add a personal information panel with fields for full name, date of birth, phone number, and email address"
🤖 AI: "Created a personal information panel with all requested fields and appropriate validation"

👤 You: "Include a secure file upload component for documents, limited to PDF files under 5MB"
🤖 AI: "Added a file upload field with PDF restriction and 5MB size limit"

👤 You: "Add a country dropdown with options for USA, Canada, UK, and Germany"
🤖 AI: "Added a country dropdown with the specified options"
```

#### Erstellen von dynamischem Verhalten

**Einfache Logik:**

```
👤 You: "Show additional fields when 'Other' is selected"
🤖 AI: "Created a conditional rule that shows additional fields when 'Other' is chosen"

👤 You: "Make the email field required"
🤖 AI: "Updated the email field to be required with validation"

👤 You: "Calculate the total automatically"
🤖 AI: "Added calculation logic to automatically compute totals"
```

**Komplexe Geschäftsregeln:**

```
👤 You: "Show the spouse information fields only when marital status is set to 'Married'"
🤖 AI: "Created a conditional rule that displays spouse fields based on marital status"

👤 You: "Calculate the total cost by multiplying quantity and price, then add 10% tax"
🤖 AI: "Added calculation logic with quantity, price, and tax computation"

👤 You: "Enable the submit button only when all required fields are completed and terms are accepted"
🤖 AI: "Created validation logic that enables submission only when all conditions are met"
```

#### Formular-Layout und -Design

**Änderungen am Layout:**

```
👤 You: "Make this a multi-step form"
🤖 AI: "Converted the form to a progressive layout with navigation"

👤 You: "Organize fields in two columns"
🤖 AI: "Updated the layout to display fields in a two-column arrangement"

👤 You: "Convert to an accordion layout"
🤖 AI: "Transformed the form to use accordion-style sections"
```

**Design-Verbesserungen:**

```
👤 You: "Create a wizard-style form with 3 steps: personal info, preferences, and review"
🤖 AI: "Created a wizard form with three distinct steps and navigation"

👤 You: "Arrange the address fields in a compact two-column layout"
🤖 AI: "Organized address fields in a compact two-column format"

👤 You: "Update the layout to match the attached wireframe"
🤖 AI: "Modified the layout to match the provided design reference"
```

### Integrations-Setup

Forms Experience Builder kann verschiedene Übermittlungsendpunkte konfigurieren, um Ihre Formulare mit externen Systemen und Services zu verbinden:

| Integrationstyp | Setup-Befehl | Anwendungsfall |
|------------------|---------------|----------|
| **E-Mail** | „Formular an E-Mail senden“ | Benachrichtigungen und Bestätigungen für Formularübermittlungen |
| **REST-API** | „An REST-Endpunkt übermitteln“ | Benutzerdefinierte Anwendungen und Systeme von Drittanbietern |
| **Cloud-Speicher** | „In Azure/SharePoint speichern“ | Dokumentenspeicher und Dateiverwaltung |
| **Workflow** | „Verbindung zu Power Automate herstellen“ | Automatisierung und Validierungen von Geschäftsprozessen |
| **Marketing** | „Integration mit Marketo&quot; | Lead-Management und Marketing-Automatisierung |

**Beispiele für erweiterte Integrationen:**

```
👤 You: "Send form submissions to hr@company.com and create a case in our CRM system"
🤖 AI: "Configured email submission and CRM integration"

👤 You: "Submit data to our REST API endpoint and trigger the new customer workflow"
🤖 AI: "Set up REST API submission with workflow triggers"

👤 You: "Email responses to the sales team and add the lead to our marketing automation platform"
🤖 AI: "Configured multi-channel submission with email and marketing automation"
```





## Erweiterte Formularvorgänge


### Erstellung komplexer Regeln

Erstellen Sie eine ausgefeilte Validierungs- und Geschäftslogik, die auf Benutzerinteraktionen reagiert und die Datenintegrität sicherstellt:

```
👤 You: "Show the address section only if the user selects 'Ship to different address'"
🤖 AI: "Created a conditional rule that shows/hides the address panel based on checkbox selection"
```

### Mehrstufige Formularerstellung

```
👤 You: "Create a progressive form with 3 steps: personal info, preferences, confirmation"
🤖 AI: "Created a progressive form with navigation between steps and validation at each stage"
```

### Erweiterte Feldtypen

* Datei-Upload mit Validierungs- und Größenbeschränkungen für die Dokumentenverwaltung
* Datumsauswahl mit Einschränkungen und Geschäftsregeln für die Planung
* Dropdown-Listen mit dynamischen Optionen, die sich je nach Benutzerauswahl ändern
* Optionsschaltflächen mit bedingter Logik für komplexe Entscheidungsbäume


### Konvertierung von PDF in Formulare

```
👤 You: "Convert this PDF into an interactive form"
🤖 AI: "Analyzed the PDF and created a form with appropriate field types and validation"
```

### URL-Formular-Konvertierung

```
👤 You: "Create a form from this website"
🤖 AI: "Extracted form elements and created a native AEM Form with enhanced functionality"
```

### Leistungsanalyse

```
👤 You: "Analyze this form's conversion performance"
🤖 AI: "Provided insights on form effectiveness and suggested optimizations"
```

### Erweiterte Anpassung

#### Benutzerdefinierte Validierungsregeln

* Feldabhängigkeiten, die basierend auf Benutzereingaben ein dynamisches Formularverhalten erstellen
* Komplexe bedingte Logik, die das Formularerlebnis an die Benutzeranforderungen anpasst
* Benutzerdefinierte Fehlermeldungen, die Benutzern eine klare Anleitung bieten
* Feldübergreifende Validierung, die die Datenkonsistenz über mehrere Eingaben hinweg sicherstellt

#### Layout-Optimierung

* Schnelligkeit für Mobilgeräte, mit der Formulare auf allen Geräten nahtlos funktionieren
* Barrierefreiheit, die Formulare für Menschen mit Behinderungen nutzbar macht
* Verbesserungen am visuellen Design, die die Benutzerinteraktion und Abschlussraten verbessern
* Verbesserungen des Benutzererlebnisses, die Reibungsverluste reduzieren und die Zufriedenheit verbessern

#### Integrations-Workflows

* Mehrstufige Genehmigungsprozesse, die Formularübermittlungen durch Business-Workflows weiterleiten
* Datenumwandlung, die Formulardaten in Formate konvertiert, die für externe Systeme erforderlich sind
* Benutzerdefinierte Geschäftslogik, die bestimmte Regeln und Berechnungen auf Formularübermittlungen anwendet
* Erweiterte Fehlerbehandlung, die eine reibungslose Wiederherstellung nach Systemproblemen ermöglicht

## Befehlsreferenz

### Wesentliche Befehle

| Symbol | Zweck | Verwendung |
|--------|---------|------------|
| `/` | Schnellaktionen und Tastaturbefehle | Geben Sie `/create` für die Formularerstellung ein, `/help` Sie Hilfe benötigen |
| `@` | Referenzieren vorhandener Formularfelder | Geben Sie `@fieldName` ein, um bestimmte Felder zu ändern (z. B. `@email`) |
| Nur Text | Natürliche Konversation | Beschreiben Sie, was Sie möchten: „Erforderliches Telefonnummernfeld hinzufügen“ |

### Schrägstrichbefehle

| Befehl | Kontext | Anwendungsbeispiel |
|---------|---------|---------------|
| `/create-form` | Alle Umgebungen | `/create-form customer survey` |
| `/add-form` | Universeller Editor | `/add-form contact form` |
| `/update-layout` | Formular-Editor | `/update-layout wizard with 3 steps` |
| `/update-field` | Formular-Editor | `/update-field @email to be required` |
| `/create-rule` | Formular-Editor | `/create-rule show @spouse if married` |
| `/create-panel` | Formular-Editor | `/create-panel Personal Information` |
| `/configure-submit` | Formular-Editor | `/configure-submit to email support` |
| `/help` | Alle Umgebungen | `/help multi-step forms` |

### Feldverweise

Verwenden Sie `@fieldName`, um auf vorhandene Felder zu verweisen:

* `@firstName`, `@lastName` * Namensfelder
* `@email`, `@phoneNumber` * Kontaktfelder
* `@address`, `@city`, `@zipCode` * Adressfelder
* `@dateOfBirth`, `@startDate` * Datumsfelder

### Komponententypen

Verwenden Sie diese Begriffe für die Beschreibung von Formularelementen:

* `text input` * Einzeiliges Textfeld
* `text area` * Mehrzeiliges Textfeld
* `dropdown` * Liste mit Optionen auswählen
* `checkbox` * Einfaches Kontrollkästchen
* `checkbox group` * Mehrere Kontrollkästchen
* `radio group` * Optionsschaltflächengruppe
* `date picker` * Feld für Datumsauswahl
* `file upload` * Feld für Dateianhang
* `panel` * Container für Gruppierungsfelder

### Integrationsbefehle

| Service | Kommando in natürlicher Sprache | Voraussetzungen |
|---------|--------------------------|--------------|
| E-Mail | „Senden von Einreichungen an [E-Mail]&quot; | Gültige E-Mail-Adresse |
| REST-API | „An REST-Endpunkt übermitteln [URL]&quot; | API-Endpunkt und Anmeldedaten |
| Azure-Speicher | „Dateien im Azure-Speicher speichern“ | Konfiguration des Speicherkontos |
| SharePoint | „In SharePoint [Site speichern]&quot; | Zugriff auf SharePoint Sites |
| Power Automate | &quot;Trigger Power Automate-Fluss“ | Flusskonfiguration |
| Marketo | „Hinzufügen von Leads zu Marketo&quot; | Marketo API-Anmeldedaten |

### Tipps

1. **Natürliche Sprache verwenden**: Die KI versteht komplexe Anforderungen und kann detaillierte Anforderungen interpretieren
2. **Spezifisch**: Detaillierte Beschreibungen liefern bessere Ergebnisse und eine genauere Formulargenerierung
3. **Iterieren**: Verfeinern Sie Formulare durch Konversation, um das perfekte Benutzererlebnis zu erzielen
4. **Nutzen des Kontexts**: Verweisen auf vorhandene Formularelemente, um auf dem aufzubauen, was Sie bereits haben
5. **Gründlich testen**: Validieren Sie alle Benutzerszenarien, um sicherzustellen, dass Formulare erwartungsgemäß funktionieren

## Produkthilfe und Lernprogramme

Mit dem Forms Experience Builder können Sie auch mehr über die Funktionen von AEM Forms erfahren:

### Stellen Sie Fragen wie:

* „Wie erstelle ich ein mehrstufiges Formular?“
* „Was ist der Unterschied zwischen Panels und Abschnitten?“
* „Wie richte ich E-Mail-Benachrichtigungen ein?“
* „Was sind die Best Practices für mobilfreundliche Formulare?“
* „Wie kann ich Designs auf meine Formulare anwenden?“

### Holen Sie sich Hilfe zu:

* Konzepten und Terminologie von AEM Forms
* Schrittweisen Anleitungen für komplexe Funktionen
* Best Practices und Einschränkungen
* Fehlerbehebung bei Indizierungsproblemen

## Best Practices

### Formularentwurf

* **Einfach halten**: Beginnen Sie mit wichtigen Feldern und fügen Sie Komplexität nur hinzu, wenn dies erforderlich ist, um eine Überlastung der Benutzer zu vermeiden
* **Klare Beschriftungen verwenden**: Machen Sie Feldzwecke mit beschreibenden Beschriftungen, die Benutzer durch das Formular führen, offensichtlich
* **Hilfetext bereitstellen**: Benutzende durch komplexe Felder mit kontextueller Hilfe und Beispielen führen
* **Gründlich testen**: Überprüfen Sie alle Benutzerpfade, um sicherzustellen, dass Formulare in allen Szenarien ordnungsgemäß funktionieren

### Benutzererlebnis

* **Fortschrittliche Offenlegung**: Zeigen Sie relevante Felder basierend auf dem Kontext an, um kognitive Belastung zu reduzieren und Abschlussraten zu verbessern
* **Übersichtliche Navigation**: Hilft Benutzern zu verstehen, wo sie sich im Formular befinden und welche Schritte verbleiben
* **Responsives Design**: Stellen Sie sicher, dass Formulare auf allen Geräten und in allen Bildschirmgrößen funktionieren, um eine maximale Barrierefreiheit zu gewährleisten
* **Barrierefreiheit**: Befolgen Sie die WCAG-Richtlinien, um Formulare für Menschen mit Behinderungen nutzbar zu machen

### Leistung

* **Felderanzahl optimieren**: Nur nach den erforderlichen Informationen fragen, um Formularabbrüche zu reduzieren und die Abschlussraten zu verbessern
* **Nutzen Sie die entsprechende Validierung**: Vermeiden Sie Fehler vor der Übermittlung, um sofortiges Feedback und Anleitung zu geben
* **Testabschlussraten**: Überwachen und verbessern Sie die Effektivität des Formulars durch Analysen und Benutzer-Feedback
* **Regelmäßige Updates**: Halten Sie Formulare mit den Geschäftsanforderungen und Benutzererwartungen auf dem neuesten Stand, um eine optimale Leistung zu erzielen

### Markenkonsistenz

* **Erstellen von Markenvorlagen**: Bereiten Sie gebrandete Formularvorlagen mit den Farben, Schriftarten und Stilen Ihres Unternehmens vor, bevor Sie mit der Erstellung des Formulars beginnen
* **Stilstandards definieren**: Konsistente Schaltflächenstile, Feld-Layouts und Abstandsrichtlinien festlegen, auf die in Eingabeaufforderungen verwiesen werden kann
* **Verwenden von Marken-Assets**: Bereiten Sie Logos, Farbcodes und Markenrichtlinien vor, die beim Erstellen von Formularen zur einfachen Referenz verwendet werden
* **Vorlagenbibliothek**: Erstellen Sie eine Sammlung von Formularvorlagen mit Branding für gängige Anwendungsfälle (Kontakt, Registrierung, Feedback)
* **Stil-Eingabeaufforderungen**: Beinhalten markenspezifische Anweisungen: „Verwenden Sie firmenblau (#1234AB) für Schaltflächen und die Firmenschriftart Helvetica“

### Tipps, um bestmögliche Ergebnisse zu erzielen

**Einfach starten, aufbauen**

* Beginnen Sie mit grundlegenden Anfragen: „Erstelle ein Kontaktformular“
* Fügen Sie Details schrittweise hinzu: „Füge Validierung zum E-Mail-Feld hinzu“
* Testen und verfeinern Sie: „Mach das Telefonfeld optional“

**bei Bedarf spezifisch sein**

* Anstelle von: „Lass es gut aussehen“
* Probieren Sie: „Verwende professionelle Farben und saubere Typografie“

**Natürliche Sprache verwenden**

* Anstelle von „Füge eine Texteingabekomponente hinzu“
* Versuchen Sie: „Füge ein Feld für Vornamen hinzu“

**Vorhandene Elemente referenzieren**

* Verwenden Sie `@fieldName` für vorhandene Felder: „Mach @email zu einem Pflichtfeld“
* Seien Sie bei Feldnamen konkret: „Aktualisiere das Feld @phoneNumber“

**Schlüsseln Sie komplexe Anfragen auf**

* Versuchen Sie es statt mit einer großen Anfrage mit mehreren kleineren
* Bauen Sie Ihr Formular Schritt für Schritt auf
* Testen Sie jede Änderung, bevor Sie zur nächsten übergehen

## Fehlerbehebung

| Problem | Schnellkorrektur |
|-------|-----------|
| **Schnittstelle wird nicht geladen** | Browser aktualisieren, Internetverbindung prüfen |
| **Befehle funktionieren nicht** | Versuchen Sie es `/help` oder verwenden Sie stattdessen natürliche Sprache |
| **@fieldName nicht erkannt** | Rechtschreibprüfung, zuerst sicherstellen, dass das Feld vorhanden ist |
| **Datei-Upload schlägt fehl** | Verwenden von PDF/JPG/PNG unter 10 MB |
| **Formular sieht falsch aus** | Genauer gesagt: „Make it mobile-friendly“ |
| **Integration schlägt fehl** | API-Anmeldeinformationen und -Berechtigungen überprüfen |

**Brauchen Sie noch Hilfe?** Geben Sie `/help` ein, gefolgt von Ihrer spezifischen Frage, oder wenden Sie sich an Ihren Systemadministrator.

Weitere Unterstützung erhalten Sie in der Haupt-[Forms Experience Builder-Eingabeaufforderungsbibliothek ](/help/edge/docs/forms/ai-assistant-prompt-library.md) oder von Ihrem Systemadministrator bzgl. technischer Unterstützung.
