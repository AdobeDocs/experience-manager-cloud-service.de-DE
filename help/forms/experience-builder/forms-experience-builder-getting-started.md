---
title: Erste Schritte mit Forms Experience Builder
description: Lernen Sie die Grundlagen der Erstellung Ihres ersten KI-gestützten Formulars mit Forms Experience Builder kennen. Schrittweises Tutorial mit Beispielen und Best Practices.
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: c4f838bc-a001-48e7-afaa-c2ff9034f5d4
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 8%

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

    Erstelle ein Formular für Kunden-Feedback mit:
    – Produktbewertung (1–5 Sterne)
    – Kommentarfeld für detailliertes Feedback
    – Kunden-E-Mail (optional)
    – An E-Mail-Benachrichtigung übermitteln

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

    &#x200B;- Abschnitt für Firmeninformationen hinzufügen
    &#x200B;- Dropdown zur Abteilungsauswahl erstellen
    &#x200B;- Datei-Upload für Wiederaufnahme einschließen
    &#x200B;- E-Mail-Benachrichtigungen einrichten, wenn das Formular gesendet wird

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
    &#x200B;- Name (erforderlich)
    &#x200B;- E-Mail (erforderlich, validiert)
    &#x200B;- Dropdown-Liste „Betreff“ (Allgemein, Support, Vertrieb, Partnerschaft)
    &#x200B;- Nachricht (erforderlich, mehrzeilig)
    &#x200B;- Schaltfläche „Senden“

**Formular für Kunden-Feedback:**

    Erstelle ein Formular für Kunden-Feedback mit:
    – Produktbewertung (1–5 Sterne)
    – Kommentarfeld für detailliertes Feedback
    – Kunden-E-Mail (optional)
    – An E-Mail-Benachrichtigung übermitteln

### Anmeldeformulare und Onboarding {#registration-onboarding-forms}

**Benutzerregistrierung:**

    Erstellen Sie ein Benutzerregistrierungsformular mit:
    &#x200B;- Persönliche Informationen (Name, E-Mail, Telefon)
    &#x200B;- Kontovoreinstellungen (Newsletter, Benachrichtigungen)
    &#x200B;- Annahme der Geschäftsbedingungen
    &#x200B;- Kennworterstellung mit Stärkenvalidierung

**Mitarbeiter-Onboarding:**

    Erstellen eines Onboarding-Formulars für Mitarbeiter mit:
    &#x200B;- Persönliche Daten und Kontaktinformationen
    &#x200B;- Informationen zur Beschäftigung und zum Startdatum
    &#x200B;- Dokument-Uploads (Lebenslauf, ID, Steuerformulare)
    &#x200B;- Auswahl und Voreinstellungen für Vorteile

### Erhebungs- und Bewertungsformulare {#survey-assessment-forms}

**Umfrage zur Kundenzufriedenheit:**

    Erstellen Sie eine Umfrage zur Kundenzufriedenheit mit:
    &#x200B;- Gesamtbewertung (Skala 1-10)
    &#x200B;- Kategoriebewertungen (Produkt, Service, Support)
    &#x200B;- Abschnitte mit offenem Feedback
    &#x200B;- Demografische Informationen (optional)

**Kompetenzbewertung:**

    Erstellen Sie ein Formular zur Kompetenzbewertung mit:
    &#x200B;- Kompetenzkategorien mit 
    &#x200B;- Erlebnisdauer für jede 
    &#x200B;- Zertifizierungs- und Schulungsinformationen
    &#x200B;- Selbstbewertung und Ziele

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

## Nächste Schritte {#next-steps}

Nachdem Sie nun die Grundlagen verstanden haben, sollten Sie sich mit diesen fortgeschrittenen Themen beschäftigen:

* **[LLM-optimierte Smart Fields](forms-experience-builder-llm-smart-fields.md)** - Erstellen von Feldern mit vorausgefüllten Optionen mithilfe von KI-Wissen
* **[KI-gestützte Formularerstellung](forms-experience-builder-prompt-examples-library.md)** - Erweiterte Eingabeaufforderungsmuster und Beispiele
* **[Intelligenter Import und Konvertierung](intelligent-import-conversion.md)** - Umwandeln vorhandener Dokumente in Formulare
* **[Formularübermittlung und -integration](form-submission-integration.md)** - Verbinden von Formularen mit Ihren Geschäftssystemen


## Verwandte Artikel

* [Übersicht über Forms Experience Builder](product-overview.md)
* [LLM-optimierte Smart Fields](forms-experience-builder-llm-smart-fields.md)
* [KI-gestützte Formularerstellung](forms-experience-builder-prompt-examples-library.md)
* [Intelligente Import- und Konvertierungsfunktionen](intelligent-import-conversion.md)
* [Formularübermittlung und -integration](form-submission-integration.md)
* [Häufig gestellte Fragen](forms-experience-builder-frequently-asked-questions.md)
