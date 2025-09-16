---
title: KI-Assistent für AEM Forms (Forms Experience Builder)
description: Schnelleres Erstellen leistungsstarker Formulare mithilfe von Formularfragmenten
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 100%

---


# Erste Schritte mit dem KI-Assistenten für AEM Forms (Forms Experience Builder)

>[!NOTE]
>
>
> Der KI-Assistent für AEM Forms (Forms Experience Builder) ist unter dem **Early-Adopter-Programm** verfügbar. Wenn Sie Interesse haben, senden Sie eine kurze E-Mail von Ihrer Geschäftsadresse an mailto::aem-forms-ea@adobe.com, um Zugriff auf die Funktion anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Dokumentation wird derzeit mit dem Produkt getestet und unterliegt möglichen Aktualisierungen und Überarbeitungen. Funktionen, Befehle und Beispiele können sich ändern, wenn der KI-Assistent für AEM Forms während des Early-Adopter-Programms weiterentwickelt wird.

Der KI-Assistent für AEM Forms transformiert die Art und Weise, wie Sie Formulare erstellen – beschreiben Sie einfach in natürlicher Sprache, was Sie benötigen, und sehen Sie dann zu, wie Ihre Formulare zum Leben erweckt werden. Der in der Benutzeroberfläche für die Formularverwaltung, im Editor für adaptive Formulare und im universellen Editor verfügbare Assistent versteht Ihre Absichten und erstellt genau das, wonach Sie suchen.

## Erste Schritte: Sprechen Sie einfach zu ihm

Der KI-Assistent funktioniert wie ein Gespräch mit einer sachkundigen Kollegin oder einem sachkundigen Kollegen. Anstatt sich mit komplexen Menüs und Einstellungen vertraut zu machen, beschreiben Sie einfach, was Sie erstellen möchten.

### Schnellstart

Sehen Sie sich unser Einführungsvideo an, um schnell loszulegen:

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)

### Zugriff auf den KI-Assistenten

Sie können von drei verschiedenen Stellen in AEM Forms aus auf den KI-Assistenten zugreifen:

1. **Benutzeroberfläche für die Formularverwaltung**
   - Navigieren Sie zu: „Adobe Experience Manager“ > „Formulare“ > „Formulare und Dokumente“
   - Suchen Sie auf der linken Seite der Benutzeroberfläche nach dem Symbol „KI-Assistent“.
   - Klicken Sie auf das Symbol, um das Bedienfeld „KI-Assistent“ zu öffnen

   ![Symbol für den KI-Assistenten*](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}

2. **Editor für adaptive Formulare**
   - Navigieren Sie zu: „Adobe Experience Manager“ > „Formulare“ > „Formulare und Dokumente“
   - Auswählen und Öffnen eines Formulars zur Bearbeitung
   - Klicken Sie in der Editor-Benutzeroberfläche auf das Symbol „KI-Assistent“.

   ![Symbol für den KI-Assistenten*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

3. **Universeller Editor**

   - Navigieren Sie zu: „Adobe Experience Manager“ > „Formulare“ > „Formulare und Dokumente“
   - Suchen Sie auf der linken Seite der Benutzeroberfläche nach dem Symbol „KI-Assistent“.
   - Klicken Sie in der Editor-Benutzeroberfläche auf das Symbol „KI-Assistent“.

### So beginnen Sie: Einfache Unterhaltungen

Der beste Weg, mit dem KI-Assistenten zu beginnen, ist durch natürliche Sprache. So funktioniert es:

**Beschreiben Sie einfach, was Sie benötigen:**

- „Erstelle ein Kontaktformular für meine Website“
- „Ich benötige ein Formular für Kunden-Feedback mit Bewertungsskalen“
- „Erstelle ein Registrierungsformular für meine bevorstehende Veranstaltung“
- „Mach eine einfache Umfrage zur Produktzufriedenheit“

**Fügen Sie nach und nach Details hinzu:**

- „Erstelle ein Kontaktformular mit den Feldern Name, E-Mail, Telefon und Nachricht“
- „Ich benötige ein mehrstufiges Anmeldeformular für eine Konferenz“
- „Erstelle ein Formular für Kunden-Feedback mit 5-Sterne-Bewertungen und Kommentar-Abschnitten“

**Vorhandene Felder referenzieren:**

- „Mach das E-Mail-Feld erforderlich“ (für @email)
- „Füge eine Validierung zum Telefonnummernfeld hinzu“ (für @phoneNumber)
- „Die Angaben zum Ehepartner sollen nur angezeigt werden, wenn Verheiratet ausgewählt ist“ (für @spouseInfo und @maritalStatus)

### Weitere Möglichkeiten

Über die natürliche Sprache hinaus bietet der KI-Assistent zusätzliche Möglichkeiten zur Interaktion:

- **Dateien hochladen**: Hängen Sie Bilder, PDFs oder Figma-Designs an, um der KI zu zeigen, was Sie sich vorstellen
- **Schnellbefehle verwenden**: Geben Sie `/` ein, um die verfügbaren Tastaturbefehle für häufige Aktionen anzuzeigen
- **Referenzspezifische Felder**: Verwenden Sie `@fieldName`, um vorhandene Formularfelder zu ändern (z. B. `@firstName`, `@emailAddress`)

## Was Sie erstellen können: Beispiele, die funktionieren

Im Folgenden finden Sie echte Beispiele dafür, was Sie mit einfacher, natürlicher Sprache erreichen können:

### Erstellen eines neuen Formulars

**Einfacher Ansatz:**

```
"Create a contact form"
```

**Detaillierterer Ansatz:**

```
"Create a professional contact form for a law firm with fields for name, email, phone, case type, and message. Make it mobile-friendly."
```

**Mit Design-Referenz:**

```
"Create a contact form based on the attached design mockup. Include all the fields shown in the layout."
```

### Hinzufügen von Formularelementen

**Einfache Ergänzungen:**

```
"Add a section for personal information"
"Include a file upload for resume"
"Add a dropdown for country selection"
```

**Detaillierte Spezifikationen:**

```
"Add a personal information panel with fields for full name, date of birth, phone number, and email address"
"Include a secure file upload component for documents, limited to PDF files under 5MB"
"Add a country dropdown with options for USA, Canada, UK, and Germany"
```

### Erstellen von dynamischem Verhalten

**Einfache Logik:**

```
"Show additional fields when 'Other' is selected"
"Make the email field required"
"Calculate the total automatically"
```

**Komplexe Geschäftsregeln:**

```
"Show the spouse information fields only when marital status is set to 'Married'"
"Calculate the total cost by multiplying quantity and price, then add 10% tax"
"Enable the submit button only when all required fields are completed and terms are accepted"
```

### Formular-Layout und -Design

**Änderungen am Layout:**

```
"Make this a multi-step form"
"Organize fields in two columns"
"Convert to an accordion layout"
```

**Design-Verbesserungen:**

```
"Create a wizard-style form with 3 steps: personal info, preferences, and review"
"Arrange the address fields in a compact two-column layout"
"Update the layout to match the attached wireframe"
```

### Übermittlung und Integration

**Einfache Übermittlung:**

```
"Send form data to our email"
"Save responses to a spreadsheet"
"Redirect to a thank you page"
```

**Erweiterte Integration:**

```
"Send form submissions to hr@company.com and create a case in our CRM system"
"Submit data to our REST API endpoint and trigger the new customer workflow"
"Email responses to the sales team and add the lead to our marketing automation platform"
```

## Arbeiten mit Anlagen

Laden Sie Dateien hoch, damit die KI genau versteht, wonach Sie suchen:

### Unterstützte Dateitypen

| Dateityp | Am besten geeignet für | Beispiel |
|-----------|----------|-------------|
| **Bilder** (PNG, JPG, GIF) | Formular-Layouts, UI-Mockups, gescannte Papierformulare | „Erstelle ein Formular, das diesem Layout entspricht“ |
| **PDF-Dateien** | Bestehende Formulare zum Konvertieren, Spezifikationen | „Konvertiere dieses PDF-Formular in ein digitales“ |
| **Figma-Dateien** | Design-Prototypen, Markenrichtlinien | „Erstelle dieses Formular aus meinem Figma-Design“ |
| **Design-Dateien** | Visuelle Verweise, Styleguides | „Passe den Stil in diesem Design an“ |

### Verwendung von Anhängen

1. **Klicken Sie auf das Anlagensymbol** in der Benutzeroberfläche des KI-Assistenten
2. **Wählen Sie die Datei** auf Ihrem Gerät aus
3. **Beschreiben Sie, was Sie möchten**, indem Sie auf die angehängte Datei verweisen:
   - „Erstelle ein Formular basierend auf diesem angehängten PDF&quot;
   - „Erstelle ein Kontaktformular entsprechend dem Layout in diesem Bild“
   - „Konvertiere dieses Papierformular in eine digitale Version.“

### Best Practices mit Anhängen

- **Verwenden Sie klare, hochwertige Bilder** für eine bessere KI-Analyse
- **Konzentrieren Sie sich auf nur ein Konzept pro Anhang** (Layout, Stil usw.)
- **Beschreiben Sie, was Sie wollen** zusammen mit dem Anhang.
- **Halten Sie die Dateien unter 10 MB** für eine optimale Verarbeitung

## Tipps für bestmögliche Ergebnisse

### Einfach starten, dann aufbauen

- Beginnen Sie mit grundlegenden Anfragen: „Erstelle ein Kontaktformular“
- Fügen Sie Details schrittweise hinzu: „Füge Validierung zum E-Mail-Feld hinzu“
- Testen und verfeinern Sie: „Mach das Telefonfeld optional“

### Seien Sie bei Bedarf spezifisch

- Anstelle von: „Lass es gut aussehen“
- Probieren Sie: „Verwende professionelle Farben und saubere Typografie“

### Verwenden Sie natürliche Sprache

- Anstelle von „Füge eine Texteingabekomponente hinzu“
- Versuchen Sie: „Füge ein Feld für Vornamen hinzu“

### Beziehen Sie sich auf vorhandene Elemente

- Verwenden Sie `@fieldName` für vorhandene Felder: „Mach @email zu einem Pflichtfeld“
- Seien Sie bei Feldnamen konkret: „Aktualisiere das Feld @phoneNumber“

### Schlüsseln Sie komplexe Anfragen auf

- Versuchen Sie es statt mit einer großen Anfrage mit mehreren kleineren
- Bauen Sie Ihr Formular Schritt für Schritt auf
- Testen Sie jede Änderung, bevor Sie zur nächsten übergehen

## Produkthilfe und Lernprogramme

Der KI-Assistent kann Sie auch über die Funktionen von AEM Forms informieren:

### Stellen Sie Fragen wie:

- „Wie erstelle ich ein mehrstufiges Formular?“
- „Was ist der Unterschied zwischen Panels und Abschnitten?“
- „Wie richte ich E-Mail-Benachrichtigungen ein?“
- „Was sind die Best Practices für mobilfreundliche Formulare?“
- „Wie kann ich Designs auf meine Formulare anwenden?“

### Holen Sie sich Hilfe zu:

- Konzepten und Terminologie von AEM Forms
- Schrittweisen Anleitungen für komplexe Funktionen
- Best Practices und Einschränkungen
- Fehlerbehebung bei Indizierungsproblemen

## Referenz zu erweiterten Funktionen

Für Benutzende, die erweiterte Funktionen erkunden möchten:

### Schnellbefehle

Geben Sie `/` ein, um die verfügbaren Tastaturbefehle anzuzeigen:

| Befehl | Zweck | Beispiel |
|---------|---------|---------|
| `/create-form` | Neues Formular starten | `/create-form customer survey` |
| `/add-form` | Formular im universellen Editor hinzufügen | `/add-form contact form` |
| `/update-layout` | Formularstruktur ändern | `/update-layout wizard with 3 steps` |
| `/update-field` | Feldeigenschaften ändern | `/update-field @email to be required` |
| `/create-rule` | Dynamisches Verhalten hinzufügen | `/create-rule show @spouse if married` |
| `/create-panel` | Feld-Container hinzufügen | `/create-panel Personal Information` |
| `/configure-submit` | Die Formularübermittlung einrichten | `/configure-submit to email support` |
| `/help` | Hilfe erhalten | `/help multi-step forms` |

### Feldverweissyntax

Verwenden Sie `@fieldName`, um auf vorhandene Felder zu verweisen:

- `@firstName` – Feld „Vorname“
- `@email` – Feld „E-Mail“
- `@phoneNumber` – Feld „Telefonnummer“
- `@dateOfBirth` – Feld „Geburtsdatum“

### Komponententypen

Verwenden Sie diese Begriffe, um optimale Ergebnisse zu erzielen:

- `text input` – Einzeiliges Textfeld
- `text area` – Mehrzeiliges Textfeld
- `dropdown` – Liste auswählen
- `checkbox` – Einfaches Kontrollkästchen
- `checkbox group` – Mehrere Kontrollkästchen
- `radio group` – Optionsfeldgruppe
- `date picker` – Datumsauswahl
- `file upload` – Dateianhang
- `panel` – Container für Gruppierungsfelder

## Fehlerbehebung

### Häufige Probleme und Lösungen

**KI-Assistent reagiert nicht:**

- Überprüfen Sie Ihre  Internet-Verbindung
- Stellen Sie sicher, dass Sie sich in einer unterstützten Umgebung befinden
- Schließen Sie das Bedienfeld „KI-Assistent“ und öffnen Sie es erneut

**Unerwartete Ergebnisse:**

- Formulieren Sie Ihre Anfrage genauer
- Unterteilen Sie komplexe Anforderungen in kleinere Schritte
- Verwenden Sie die Standardterminologie von AEM Forms

**Feldverweise funktionieren nicht:**

- Überprüfen Sie, ob die Feldnamen genau so geschrieben sind, wie sie angezeigt werden
- Verwenden Sie die Syntax `@fieldName` für vorhandene Felder
- Sicherstellen, dass das Feld vorhanden ist, bevor darauf verwiesen wird

**Probleme beim Design-Import:**

- Überprüfen Sie, ob die Dateien klar und gut strukturiert sind
- Verwenden Sie unterstützte Formate (PDF, PNG, JPG, Figma)
- Stellen Sie sicher, dass die Dateigröße weniger als 10 MB beträgt

## Feedback und Support

Helfen Sie uns, den KI-Assistenten zu verbessern:

- **Feedback geben**: Verwenden Sie die Schaltfläche „Feedback“ in der Benutzeroberfläche des KI-Assistenten
- **Probleme melden**: Wenden Sie sich über die offiziellen Kanäle an den Adobe-Support
- **Erfahrungen austauschen**: Ihr Input hilft, den Assistenten für alle besser zu machen

## Zugehörige Ressourcen

[AEM Forms KI-Assistent – Bibliothek für Prompts](/help/edge/docs/forms/ai-assistant-prompt-library.md)
