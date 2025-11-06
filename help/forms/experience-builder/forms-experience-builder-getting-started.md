---
title: Erste Schritte mit Forms Experience Builder
description: Lernen Sie die Grundlagen der Erstellung Ihres ersten KI-gestützten Formulars mit Forms Experience Builder kennen. Schrittweises Tutorial mit Beispielen und Best Practices.
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: c4f838bc-a001-48e7-afaa-c2ff9034f5d4
source-git-commit: 1d378e6c8ac714779e77314d3457a14d40cd222f
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 3%

---

# Erste Schritte mit Forms Experience Builder {#getting-started-forms-experience-builder}

Forms Experience Builder revolutioniert die Formularerstellung, indem KI genutzt wird, um Beschreibungen in natürlicher Sprache in voll funktionsfähige digitale Formulare umzuwandeln. Dieses Handbuch hilft Ihnen, Ihr erstes Formular zu erstellen und die Kernkonzepte zu verstehen, die Forms Experience Builder leistungsstark machen.

## Was ist Forms Experience Builder? {#what-is-forms-experience-builder}

Forms Experience Builder ist ein KI-gestütztes Tool zur Formularerstellung, mit dem Sie anspruchsvolle digitale Formulare in Gesprächssprache erstellen können. Anstelle herkömmlicher Drag-and-Drop-Schnittstellen oder komplexer Codierung beschreiben Sie einfach, was Sie möchten, und die KI erstellt das Formular für Sie.

**Schlüsselfunktionen:**

* **Formularerstellung in natürlicher Sprache** - Beschreiben Sie Ihre Formularanforderungen in einfachem Englisch

* **Intelligenter Import und Konvertierung** - Umwandeln vorhandener Dokumente in interaktive Formulare

* **Generierung intelligenter Felder** - KI-gestützte Felder mit vorausgefüllten Optionen

* **Business-Logikautomatisierung** - Erstellen von bedingten Regeln und Validierungen durch Konversation

* **Systemintegration** - Verbinden von Formularen mit Ihren bestehenden Unternehmens-Workflows

## Voraussetzungen {#prerequisites-getting-started}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* **Zugriff auf Forms Experience Builder** - verfügbar über das Early Access-Programm
* **AEM Forms as a Cloud Service** - Produktions-Autorenumgebung mit Kernkomponenten für adaptive Forms
* **Grundlegendes** - Vertrautheit mit Formularkonzepten und Geschäftsanforderungen

Detaillierte technische Setup-Anforderungen und Umgebungskonfigurationen finden Sie unter [Bereitstellen und Konfigurieren von Forms Experience Builder](deploy-forms-experience-builder.md).

## Möglichkeiten zum Erstellen von Formularen {#two-ways-to-create-forms}

Nachdem Sie mit dem Forms-Assistenten eine [Kernkomponentenvorlage](/help/forms/creating-adaptive-form-core-components.md) oder eine [Edge Delivery Services](/help/edge/docs/forms/universal-editor/create-forms.md)-Vorlage, ein Design und andere Optionen ausgewählt haben, bietet Forms Experience Builder zwei Hauptansätze für die Formularerstellung:

### &#x200B;1. Erstellen von Grund auf {#create-from-scratch}

Erstellen Sie Formulare mit Beschreibungen Ihrer Anforderungen in natürlicher Sprache.

**Verwendung:**

* Erstellen neuer Formulare aus Anforderungen

* Erstellen von Formularen für neue Geschäftsprozesse

* Wenn Sie klare Spezifikationen, aber keine vorhandenen Dokumente haben

**Beispiel:**

    Erstellen Sie ein Formular für Kunden-Feedback mit:
    - Produktbewertung (1-5 Sterne)
    - Feld „Kommentar“ für detailliertes Feedback
    - Kunden-E-Mail (optional)

>[!VIDEO](https://video.tv.adobe.com/v/3473104)



### &#x200B;2. Importieren und Konvertieren {#import-and-convert}

Umwandeln vorhandener Dokumente in interaktive digitale Formulare.

Laden Sie vor Verwendung dieser Option Ihre PDF-Datei oder ein Bild des Formulars hoch. Die PDF kann entweder ein AcroForm- oder ein XFA-basiertes PDF-Formular sein. Bei [anderen Typen von PDF forms](https://experienceleague.adobe.com/en/docs/experience-manager-learn/forms/document-services/pdf-forms-and-documents) verwenden Sie die Option [Formular vorbereiten](https://helpx.adobe.com/in/acrobat/using/creating-distributing-pdf-forms.html) in Adobe Acrobat, um sie in ein AcroForm zu konvertieren

**Verwendung:**

* Konvertieren des bestehenden PDF formss

* Modernisierung von papiergestützten Prozessen

* Wenn Sie über vorhandene Formularentwürfe zur Verbesserung verfügen

**Beispiel:**

    /create-form konvertiert die angehängte PDF-Datei in ein adaptives Formular

>[!VIDEO](https://video.tv.adobe.com/v/3474042)


## Ihr erstes Formular: Schrittweises Tutorial {#first-form-tutorial}

Erstellen wir ein einfaches Kontaktformular, um den grundlegenden Workflow zu verstehen.

### Schritt 1: Mit einer einfachen Beschreibung beginnen {#step-1-simple-description}

Beginnen Sie mit einer einfachen Formularbeschreibung:

    Erstelle ein simples Kontaktformular mit Feldern für Name, E-Mail, Telefon und Nachricht

Dadurch wird ein Formular mit drei wesentlichen Feldern erstellt.

![Formular mit drei wesentlichen Feldern - mit natürlicher Eingabeaufforderung erstellt](/help/forms/assets/forms-experience-builder-contact-us-form.png)

### Schritt 2: Hinzufügen von Validierungen und Anforderungen {#step-2-add-validation}

Erweitern des Formulars mit Validierungsregeln:

    Erstelle die Pflichtfelder @name und @email mit entsprechender Validierung

Das `@`-Symbol verweist auf bestimmte Felder für zielgerichtete Änderungen.

![Es wurde eine Validierung in Form Experience Builder mithilfe einer Eingabeaufforderung in natürlicher Sprache hinzugefügt](/help/forms/assets/forms-experience-builder-contact-us-form-add-validation.png)


### Schritt 3: Verbessern des Benutzererlebnisses {#step-3-improve-ux}

Fügen Sie hilfreichen Platzhaltertext und Anleitungen hinzu:

    Füge Platzhaltertext hinzu: @name „Ihr vollständiger Name“, @email „your.email@company.com“, @message „Wie können wir Ihnen helfen?“

![Es wurde eine Validierung mithilfe von Eingabeaufforderungen in natürlicher Sprache in Forms Experience Builder hinzugefügt](/help/forms/assets/forms-experience-builder-contact-us-form-add-placeholder.png)

### Schritt 4: Erweiterte Funktionen hinzufügen {#step-4-advanced-features}

Zusätzliche Funktionen einschließen:

    Fügen Sie zwei Dropdown-
    
     hinzuAnfrageTyp mit Optionen: „Allgemeine Frage“, „Support-Anfrage“, „Vertriebsanfrage“, „Partnerschaft“ 
    
    -Dringlichkeitsstufe mit Optionen (Niedrig, Medium, Hoch)


![Es wurden Dropdown-Komponenten mit Eingabeaufforderungen in Experience Builder für Formulare in natürlicher Sprache hinzugefügt](/help/forms/assets/forms-experience-builder-contact-us-form-add-dropdown.png)


### Schritt 5: Bedingte Logik implementieren {#step-5-conditional-logic}

Erstellen Sie intelligentes, kontextbezogenes Verhalten, indem Sie Regeln hinzufügen, z. B.:

    @urgencyLevel Dropdown beim Laden des Formulars ausblenden
    @urgencyLevel Dropdown-Liste (Niedrig, Medium, Hoch) nur anzeigen, wenn @inquiryType gleich „Support-Anfrage“ ist

Hierbei handelt es sich um zwei separate Regeln: Eine blendet das Dropdown-Menü für die Dringlichkeitsstufe aus, wenn das Formular geladen wird, und die andere zeigt es nur an, wenn der Anfragetyp „Support-Anfrage“ ist. Sie müssen jede Regel mit einer separaten Eingabeaufforderung erstellen. Es kann jeweils nur eine Regel erstellt werden.

## Grundlegendes zum Ansatz der KI-Konversation {#ai-conversation-approach}

Forms Experience Builder verwendet eine Gesprächsoberfläche, in der Sie:

### Referenzfelder mit @-Symbolen {#reference-fields}

Verwenden Sie `@fieldName`, um auf bestimmte Felder zu verweisen:

    @email ein erforderliches Feld festlegen
    Validierung zu @phoneNumber für US-Format hinzufügen
    @submitButtonText in „Nachricht senden“ ändern

>[!VIDEO](https://video.tv.adobe.com/v/3474043)


### Befehle in natürlicher Sprache verwenden {#natural-language-commands}

Beschreiben Sie, was Sie möchten, in einfachem Englisch:

    - Abschnitt für Firmeninformationen hinzufügen
    - Dropdown zur Abteilungsauswahl erstellen
    - Datei-Upload zur Wiederaufnahme einschließen

### Inkrementelles Erstellen {#build-incrementally}

Einfach anfangen und schrittweise Komplexität hinzufügen:

1. **Grundstruktur** - Erstellen Sie zuerst die wesentlichen Felder.
2. **Validierung hinzufügen** - Implementieren erforderlicher Felder und Formatvalidierung
3. **Erweitern von UX** - Hinzufügen von Platzhaltern, Hilfetext und Stil
4. **Logik implementieren** - Hinzufügen bedingter Regeln und Geschäftslogik
5. **Übermittlung konfigurieren** - Formularverarbeitung und Benachrichtigungen einrichten


## Häufige Formularmuster {#common-form-patterns}

### Kontakt- und Feedback-Formulare {#contact-feedback-forms}

**Basiskontaktformular:**

    Erstellen eines Kontaktformulars mit:
    - Name (erforderlich)
    - E-Mail (erforderlich, validiert)
    - Dropdown-Liste „Betreff“ (Allgemein, Support, Vertrieb, Partnerschaft)
    - Nachricht (erforderlich, mehrzeilig)

**Formular für Kunden-Feedback:**

    Erstellen Sie ein Formular für Kunden-Feedback mit:
    - Produktbewertung (1-5 Sterne)
    - Feld „Kommentar“ für detailliertes Feedback
    - Kunden-E-Mail (optional)

### Anmeldeformulare und Onboarding {#registration-onboarding-forms}

**Benutzerregistrierung:**

    Erstellen Sie ein Benutzerregistrierungsformular mit:
    - Persönliche Informationen (Name, E-Mail, Telefon)
    - Kontovoreinstellungen (Newsletter, Benachrichtigungen)
    - Annahme der Geschäftsbedingungen
    - Kennworterstellung mit Stärkenvalidierung

**Mitarbeiter-Onboarding:**

    Erstellen eines Onboarding-Formulars für Mitarbeiter mit:
    - Persönliche Daten und Kontaktinformationen
    - Informationen zur Beschäftigung und zum Startdatum
    - Dokument-Uploads (Lebenslauf, ID, Steuerformulare)
    - Auswahl und Voreinstellungen für Vorteile

### Erhebungs- und Bewertungsformulare {#survey-assessment-forms}

**Umfrage zur Kundenzufriedenheit:**

    Erstellen Sie eine Umfrage zur Kundenzufriedenheit mit:
    - Gesamtbewertung (Skala 1-10)
    - Kategoriebewertungen (Produkt, Service, Support)
    - Abschnitte mit offenem Feedback
    - Demografische Informationen (optional)

**Kompetenzbewertung:**

    Erstellen Sie ein Formular zur Kompetenzbewertung mit:
    - Kompetenzkategorien mit 
    - Erlebnisdauer für jede 
    - Zertifizierungs- und Schulungsinformationen
    - Selbstbewertung und Ziele

## Tests und Validierung {#testing-validation}

### Formulare immer testen {#always-test-forms}

Vor der Bereitstellung eines Formulars:

1. **Alle Felder testen** - Sicherstellen, dass die Validierung ordnungsgemäß funktioniert

2. **Bedingte Logik überprüfen** - Überprüfen Sie, ob der Regeln-Trigger ordnungsgemäß funktioniert

3. **Testübermittlung** - Bestätigen der korrekten Verarbeitung von Daten

4. **Validieren auf verschiedenen Geräten** - Sicherstellen der Kompatibilität mit Mobilgeräten

5. **Mit Stakeholdern besprechen** - Feedback von Endbenutzern erhalten

### Häufige Validierungsmuster {#validation-patterns}

**E-Mail-Validierung:**

    Hinzufügen der Validierung des E-Mail-Formats zu @email Feld

**Überprüfung der Telefonnummer:**

    Fügen Sie die US-Telefonnummernformatvalidierung zu @phoneNumber hinzu

**Altersvalidierung:**

    Altersvalidierung hinzufügen: muss für @dateOfBirth 18 Jahre oder älter sein

**Validierung des Datei-Uploads:**

    Validierung des Dateityps hinzufügen: nur PDF, DOC, DOCX erlaubt für @resume
    Dateigrößenbeschränkung hinzufügen: maximal 5 MB für @resume

<!-- 

## Next steps {#next-steps}

Now that you understand the basics, explore these advanced topics:

* **[LLM-enhanced smart fields](forms-experience-builder-llm-smart-fields.md)** - Create fields with pre-populated options using AI knowledge
* **[AI-powered form creation](forms-experience-builder-prompt-examples-library.md)** - Advanced prompt patterns and examples
* **[Intelligent import and conversion](intelligent-import-conversion.md)** - Transform existing documents into forms
* **[Form submission and integration](form-submission-integration.md)** - Connect forms to your business systems

-->


## Verwandte Artikel

* [Übersicht über Forms Experience Builder](product-overview.md)

<!-- 
* [LLM-enhanced smart fields](forms-experience-builder-llm-smart-fields.md)
* [AI-powered form creation](forms-experience-builder-prompt-examples-library.md)
* [Intelligent import and conversion](intelligent-import-conversion.md)
* [Form submission and integration](form-submission-integration.md)
* [Frequently asked questions](forms-experience-builder-frequently-asked-questions.md)

-->
