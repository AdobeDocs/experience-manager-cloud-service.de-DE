---
title: Forms Experience Builder - Häufig gestellte Fragen
description: Hier finden Sie Antworten auf häufig gestellte Fragen zu Forms Experience Builder, einschließlich Einrichtung, Verwendung, Fehlerbehebung und Best Practices.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 1%

---


# Forms Experience Builder - Häufig gestellte Fragen

>[!NOTE]
>
> Forms Experience Builder ist im Rahmen eines Early-Access-Programms verfügbar. Bevor Sie beginnen, stellen Sie sicher, dass Sie Zugriff angefordert haben und erhalten haben.

In diesen häufig gestellten Fragen werden die häufigsten Fragen zu Forms Experience Builder behandelt, von der einfachen Einrichtung bis hin zu erweiterten Funktionen und Fehlerbehebung.

## Allgemeine Fragen

### Was ist Forms Experience Builder?

Forms Experience Builder ist ein KI-gestütztes Tool zur Formularerstellung, mit dem Sie anspruchsvolle digitale Formulare in Gesprächssprache erstellen können. Anstelle herkömmlicher Drag-and-Drop-Schnittstellen oder komplexer Codierung beschreiben Sie einfach, was Sie möchten, und die KI erstellt das Formular für Sie.

### Wer kann Forms Experience Builder verwenden?

Forms Experience Builder wurde entwickelt für:

- **Formularersteller** die Formulare schnell und effizient erstellen möchten
- **Geschäftsbenutzer** die Formulare ohne technisches Fachwissen erstellen müssen
- **Entwickler** die KI für das schnelle Formular-Prototyping nutzen möchten
- **Administratoren** die Workflows für die Formularerstellung konfigurieren und verwalten müssen

### Ist Forms Experience Builder für alle AEM Forms-Kunden verfügbar?

Forms Experience Builder ist derzeit über ein Early Access-Programm verfügbar. Wenden Sie sich an den Adobe-Support, um Zugang zu erhalten und mehr über die Verfügbarkeit für Ihr Unternehmen zu erfahren.

## Einrichtung und Konfiguration

### Was sind die Voraussetzungen für die Verwendung von Forms Experience Builder?

Stellen Sie vor der Verwendung von Forms Experience Builder Folgendes sicher:

- Zugriff auf Forms Experience Builder über das Early Access-Programm
- AEM Forms as a Cloud Service mit Kernkomponenten für adaptive Forms
- Grundlegendes zu Formularkonzepten und Geschäftsanforderungen

Ausführliche technische Setup-Anforderungen finden Sie unter [Bereitstellen und Konfigurieren von Forms Experience Builder](deploy-forms-experience-builder.md).

### Wie aktiviere ich Forms Experience Builder in meiner Umgebung?

Das Setup von Forms Experience Builder hängt von Ihrer AEM Forms-Implementierung ab:

**Für Edge Delivery Services:**

- Vorbereiten Ihres Projekts für Edge Delivery Services Forms
- Aktivieren von Forms Experience Builder im universellen Editor

**Formulare, die auf Kernkomponenten basieren:**

- Stellen Sie sicher, dass Kernkomponenten für adaptive Forms aktiviert sind
- Konfigurieren von Forms Experience Builder im Editor für adaptive Forms

### Kann ich Forms Experience Builder mit vorhandenen Formularen verwenden?

Ja, Forms Experience Builder kann auf verschiedene Weise mit vorhandenen Formularen arbeiten:

- Importieren und Konvertieren von PDF forms
- Verbessern vorhandener adaptiver Formulare mit KI-gestützten Funktionen
- Hinzufügen intelligenter Felder zu aktuellen Formularstrukturen

## Erstellen von Formularen

### Wie erstelle ich mein erstes Formular?

Beginnen Sie mit einer einfachen Beschreibung dessen, was Sie möchten:

    Erstellen Sie ein Kontaktformular mit den Feldern Name, E-Mail und Nachricht

Die KI generiert die grundlegende Formularstruktur, die Sie dann mit zusätzlichen Funktionen, Validierungen und Stilen erweitern können.

### Welche Arten von Formularen kann ich erstellen?

Forms Experience Builder unterstützt verschiedene Formulartypen:

- Kontakt- und Feedback-Formulare
- Anmeldeformulare und Onboarding
- Erhebungs- und Bewertungsformulare
- Mehrstufige Formulare mit bedingter Logik
- Forms mit Datei-Uploads und komplexer Validierung

### Kann ich mehrstufige Formulare erstellen?

Ja, Sie können mehrstufige Formulare in natürlicher Sprache erstellen:

    Erstellen Sie ein progressives Formular mit 3 Schritten: persönliche Informationen, Voreinstellungen, Bestätigung

Die KI richtet automatisch die Formularstruktur ein, wobei die Navigation zwischen den Schritten erfolgt.

### Wie füge ich Validierungen zu Formularfeldern hinzu?

Hinzufügen von Validierungen mit Befehlen in natürlicher Sprache:

    @email ein Pflichtfeld mit E-Mail-Formatvalidierung festlegen
    US-Telefonnummernformatvalidierung hinzufügen, um &quot;
    &quot; festzulegen@phoneNumber Für @dateOfBirth muss 18 Jahre oder älter sein

## Erweiterte Funktionen

### Was sind LLM-optimierte Smart Fields?

LLM-optimierte Smart Fields sind intelligente Formularfelder, die mit relevanten Optionen aus KI-Wissensdatenbanken vorausgefüllt werden. Beispiel:

- Länder Dropdown mit allen Ländern der Welt
- Branchenklassifizierungen mit Standard-Codes
- Geografische Daten mit Bundesstaaten, Städten und Postleitzahlen

### Wie importiere ich vorhandene Dokumente in Formulare?

Sie können verschiedene Dokumenttypen importieren:

- **PDF forms**: Hochladen von statischen oder interaktiven PDFs
- **Bilder**: Hochladen von Fotos von Papierformularen oder Screenshots
- **Design-Dateien**: Importieren Sie Figma-Designs oder andere Design-Formate

Verwenden Sie das Anlagensymbol in Forms Experience Builder, um Ihr Dokument hochzuladen und Ihre Konvertierungsanforderungen zu beschreiben.

### Kann ich Formulare in externe Systeme integrieren?

Ja, Forms Experience Builder unterstützt verschiedene Integrationsoptionen:

- E-Mail-Übermittlungen mit benutzerdefinierten Vorlagen
- REST-API-Integration mit externen Services
- Cloud-Speicherintegration (Azure, AWS, Google Cloud)
- Workflow-Integration (Power Automate, AEM Workflow)

## Fehlerbehebung

### Die KI versteht meine Anfrage nicht. Was soll ich tun?

Probieren Sie die folgenden Ansätze aus:

- Geben Sie Ihre Beschreibung genauer an
- Unterteilen Sie komplexe Anforderungen in kleinere Schritte
- Verwenden von Feldverweisen (@fieldName) für zielgerichtete Änderungen
- Geben Sie klare Beispiele für das, was Sie möchten

### Meine Formularüberprüfung funktioniert nicht. Wie behebe ich das?

Überprüfen Sie diese häufigen Probleme:

- Überprüfen, ob die Feldnamen genau übereinstimmen (Groß-/Kleinschreibung beachten)
- Stellen Sie sicher, dass die Validierungssyntax korrekt ist
- Validierungsregeln einzeln testen
- Überprüfen von Fehlermeldungen auf bestimmte Probleme

### Bedingte Logik wird nicht richtig ausgelöst. Was ist los?

Fehlerbehebung bei bedingter Logik durch:

- Sicherstellen, dass Feldnamen korrekt referenziert werden
- Überprüfen der Regelsyntax und Bedingungen
- Testen mit verschiedenen Eingabekombinationen
- Überprüfen, ob Feldtypen den Regelanforderungen entsprechen

### Die Benutzeroberfläche wird nicht geladen. Was soll ich tun?

Probieren Sie die folgenden Lösungen aus:

- Browser aktualisieren und Cache löschen
- Überprüfen Sie Ihre  Internet-Verbindung
- Stellen Sie sicher, dass Sie über geeignete Zugriffsberechtigungen verfügen
- Wenden Sie sich an Ihren Systemadministrator, wenn das Problem weiterhin besteht

## Best Practices

### Wie kann ich mit Forms Experience Builder bessere Formulare erstellen?

Befolgen Sie die folgenden Best Practices:

- **Spezifisch sein** Geben Sie detaillierte Beschreibungen dessen an, was Sie möchten
- **Einfach beginnen** Beginnen Sie mit der grundlegenden Struktur und fügen Sie schrittweise Komplexität hinzu
- **Gründlich testen**: Validieren aller Formularfunktionen vor der Bereitstellung
- **Inkrementelle Entwicklung verwenden**: Erstellen von Formularen Schritt für Schritt

### Was sollte ich beim Erstellen von Formularen vermeiden?

Vermeiden Sie diese häufigen Fehler:

- Zu vage in Ihren Beschreibungen
- Alles auf einmal erstellen
- Überspringen von Tests und Validierung
- Reaktionsfähigkeit auf Mobilgeräten wird nicht berücksichtigt

### Wie stelle ich sicher, dass meine Formulare barrierefrei sind?

Forms Experience Builder enthält Funktionen für Barrierefreiheit:

- Automatische WCAG-Konformitätsprüfung
- Kompatibilität mit Sprachausgaben
- Unterstützung der Tastaturnavigation
- Optionen für den kontrastreichen Modus

## Integration und Bereitstellung

### Wie stelle ich mit Forms Experience Builder erstellte Formulare bereit?

Forms, die mit Forms Experience Builder erstellt wurden, folgen den standardmäßigen AEM Forms-Bereitstellungsprozessen:

- Veröffentlichen von Formularen über die AEM-Autorenumgebung
- Konfigurieren von Formularübermittlungsendpunkten
- Einrichten von Workflows für die Formularverarbeitung
- Testformulare in der Produktionsumgebung

### Kann ich die KI-Antworten und das Verhalten anpassen?

Ja, Sie können verschiedene Aspekte konfigurieren:

- Antwortstil (kurz, detailliert, ausgewogen)
- Sprachvoreinstellungen und Terminologie
- Anpassungsoptionen der Benutzeroberfläche
- Einstellungen zur Barrierefreiheit

### Wie erhalte ich Hilfe zu Forms Experience Builder?

Für zusätzliche Unterstützung:

- Weitere Informationen finden [ im Handbuch „Erste Schritte](forms-experience-builder-getting-started.md)
- Lesen Sie das [Bereitstellungs- und Konfigurationshandbuch](deploy-forms-experience-builder.md)
- Wenden Sie sich an Ihren Systemadministrator
- Wenden Sie sich bei technischen Problemen an den Adobe-Support

## Verwandte Artikel

- [Übersicht über Forms Experience Builder](product-overview.md)
- [Erste Schritte mit Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Bereitstellen und Konfigurieren von Forms Experience Builder](deploy-forms-experience-builder.md)
- [LLM-optimierte Smart Fields](forms-experience-builder-llm-smart-fields.md)
- [Intelligente Import- und Konvertierungsfunktionen](intelligent-import-conversion.md)
- [Formularübermittlung und -integration](form-submission-integration.md)
