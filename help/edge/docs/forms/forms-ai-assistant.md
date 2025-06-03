---
title: KI-Assistent für AEM Forms (Forms Experience Builder)
description: Schnelleres Erstellen leistungsstarker Formulare mithilfe von Formularfragmenten
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 2db966405b5326d735083a66b2625d6d973ad7db
workflow-type: tm+mt
source-wordcount: '2354'
ht-degree: 2%

---


# KI-Assistent für AEM Forms (Forms Experience Builder)

>[!NOTE]
>
>
> Die Funktion KI-Assistent für AEM Forms (Forms Experience Builder) ist unter dem **Early-Adopter-Programm** verfügbar. Bei Interesse senden Sie eine kurze E-Mail von Ihrer Geschäftsadresse an mailto:aem-forms-ea@adobe.com, um den Zugriff auf die Funktion anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Dokumentation wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Funktionen, Befehle und Beispiele können sich ändern, während sich der KI-Assistent für AEM Forms während des Early-Adopter-Programms weiterentwickelt.

Der KI-Assistent für AEM Forms (Forms Experience Builder) verbessert das Authoring-Erlebnis, indem allgemeine Formularerstellungsaufgaben durch natürliche Sprachaufforderungen optimiert werden. Er ist in der Forms-Verwaltungsoberfläche, im Editor für adaptive Forms und im universellen Editor verfügbar und ermöglicht es Ihnen, durch die Unterstützung von Erstellungs- und Konfigurationsaktionen intelligenter und schneller zu erstellen. Dieses Handbuch hilft Ihnen bei den ersten Schritten und dem optimalen Nutzen der Funktionen.

## Erste Schritte

Bevor wir in die Tiefe gehen, erläutern wir die Grundlagen des Zugriffs auf den KI-Assistenten und der Interaktion mit ihm.

### Zugriff auf den KI-Assistenten

Sie können von drei verschiedenen Standorten in AEM Forms aus auf den KI-Assistenten zugreifen:

1. **Forms-Verwaltungsoberfläche**
   - Navigieren Sie zu: Adobe Experience Manager > Forms > Forms und Dokumente
   - Suchen Sie auf der linken Seite der Benutzeroberfläche nach dem Symbol KI-Assistent .
   - Klicken Sie auf das Symbol, um das Bedienfeld KI-Assistent zu öffnen

   ![Symbol für KI-Assistenten*](/help/edge/docs/forms/assets/forms-manager.gif)

2. **Adaptive Forms-Editor**
   - Navigieren Sie zu: Adobe Experience Manager > Forms > Forms und Dokumente
   - Auswählen und Öffnen eines Formulars zur Bearbeitung
   - Klicken Sie in der Editor-Benutzeroberfläche auf das Symbol KI-Assistent .

   ![Symbol für KI-Assistenten*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif)

3. **Universeller Editor**

   - Navigieren Sie zu: Adobe Experience Manager > Forms > Forms und Dokumente
   - Suchen Sie auf der linken Seite der Benutzeroberfläche nach dem Symbol KI-Assistent .
   - Klicken Sie in der Editor-Benutzeroberfläche auf das Symbol KI-Assistent .

Der KI-Assistent passt seine Funktionen an Ihren aktuellen Standort und Ihre Aufgabe an und bietet für jeden Kontext relevante Unterstützung.

### Interaktion:

- Geben Sie Ihre Anfrage einfach in natürlicher Sprache ein.
- Verwenden Sie `/` , um eine Liste der verfügbaren Befehle oder Schnellaktionen anzuzeigen.
- Referenzieren Sie bestimmte Formularfelder mithilfe von `@fieldName` (z. B. `@firstName`, `@emailAddress`), wenn Sie möchten, dass der Assistent dieses bestimmte Feld konfiguriert oder aktualisiert.
- Sie können Bilder, PDFs, Figa-Dateien oder andere Design-Assets hochladen, damit der KI-Assistent Ihre Anforderungen besser versteht.


### Schnellstart

Sehen Sie sich unser Einführungsvideo an, um schnell loszulegen:

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)


In diesem Video wird der Start des Assistenten in allen Umgebungen, grundlegende Interaktionen und ein Überblick über seine Funktionen behandelt.

## Befehlsreferenz zum KI-Assistenten

| Befehl | Beschreibung | Zweck | Nutzungskontext | Beispiele | Wichtigste Funktionen |
|---------|-------------|---------|---------------|----------|--------------|
| /create-form | Beginnen Sie ein neues Formular in der Forms-Verwaltungsoberfläche oder im Forms-Editor | Startet die Erstellung eines komplett neuen Formulars von Grund auf | Benutzeroberfläche für die Verwaltung von Forms, Editor für adaptive Forms | Umfrage zum Kunden-Feedback auf der Grundlage des angehängten PDF | Stellt Optionen für die Formularstruktur bereit und erstellt das Formular. **Unterstützt Anlagen** für Design-Verweise |
| /add-form | Hinzufügen eines neuen Formulars im universellen Editor | Fügt einen neuen Formularblock oder eine neue Komponente im universellen Editor hinzu. | Universeller Editor für Edge Delivery Services | /add-form Kontaktformular mit Namen und E-Mail | Fügt Formularblöcke ein, arbeitet mit blockbasierter Bearbeitung. **Unterstützt Anlagen** für Layout-Anleitungen |
| /update-layout | Ändern des Layouts des Formulars in ein Akkordeon, einen tabulatorbasierten Assistenten oder ein responsives Design für eine einzelne Seite | Ändert das allgemeine strukturelle Layout und Navigationsmuster | Alle Bearbeitungsumgebungen | /update-layout-assistent mit 3 Schritten | Akkordeon, Registerkarten, Assistent, responsive Optionen für eine einzelne Seite |
| /update-field | Ändern der Eigenschaften und Konfiguration vorhandener Formularfelder | Ändert Feldattribute wie Beschriftungen, Validierung, Formatierung, Verhalten | Alle Bearbeitungsumgebungen | /update-field @email bei der Validierung erforderlich sein | Kennzeichnungen, Validierungsregeln, Feldtypen, Standardwerte, Sichtbarkeit. **Unterstützt Anlagen** für Beispiele für den Feldentwurf |
| /create-rule | Erstellen eines dynamischen Verhaltens und einer bedingten Logik für Formulare | Implementiert Geschäftslogik, Berechnungen, bedingte Interaktionen | Alle Bearbeitungsumgebungen | /create-rule - @spouseName anzeigen, wenn @maritalStatus gleich „Verheiratet“ ist | Bedingte Sichtbarkeit, Berechnungen, Validierung, Werteinstellung |
| /create-panel | Erstellen eines neuen Bedienfelds (Container für die Gruppierung verwandter Felder) | Fügt strukturelle Container hinzu, um Formularfelder logisch zu organisieren | Alle Bearbeitungsumgebungen | /create-panel Persönliche Informationen mit Name, E-Mail, Telefon | Feldergruppierung, Titel, Layout-Optionen, ausblendbare Abschnitte. **Unterstützt Anlagen** für Bereichslayoutverweise |
| /add-panel | Konvertieren eines Bilds in einen Formularbereich im universellen Editor | Verwendet KI zur Analyse hochgeladener Bilder und zur Konvertierung in strukturierte Formularbereiche | Universeller Editor | /add-panel aus hochgeladenem Formularbild | Bilderkennung, visuelle Umwandlung in eine Funktion, Beibehaltung des Layouts. **Erfordert Anhänge** für die Bildanalyse |
| /configure-submit | Einrichten von Formularübermittlungsaktionen und Datenverarbeitung | Definiert, was passiert, wenn Benutzer das ausgefüllte Formular senden | Alle Bearbeitungsumgebungen | /configure-submit zum Senden von E-Mails an `support@company.com` | E-Mail, REST-API, Workflows, Tabellen, Datenbanken, Power Automate |
| /help | Zugriff auf Hilfe und Dokumentation innerhalb des KI-Assistenten | Bietet kontextuelle Hilfe, Anleitungen und Antworten zu AEM Forms | Alle Bearbeitungsumgebungen | /help Wie erstelle ich mehrstufige Formulare? | Funktionserklärungen, Handbücher, Best Practices, Fehlerbehebung |

### Befehlskategorien

| Kategorie | Befehle | Primäre Anwendungsfälle |
|----------|----------|-------------------|
| Formularerstellung | /create-form, /add-form | Beginnen neuer Formulare, Hinzufügen von Formularblöcken |
| Struktur und Layout | /update-layout, /create-panel, /add-panel | Organisieren der Formularstruktur, visuelles Design |
| Außendienstverwaltung | /update-field | Konfigurieren einzelner Formularelemente |
| Logik und Regeln | /create-rule | Hinzufügen von dynamischem Verhalten und Validierung |
| Übermittlung | /configure-submit | Einrichten von Datenverarbeitung und Workflows |
| Support | /help | Hilfe und Dokumentation |

### Richtlinien zur Syntax

| Element | Format | Beispiel | Anmerkungen |
|---------|--------|---------|-------|
| Befehle | /command-name | /create-form | Immer mit Schrägstrich beginnen |
| Feldverweise | @fieldName | @email, @firstName | @-Symbol für vorhandene Felder verwenden |
| natürliche Sprache | Befehl + Beschreibung | /create-rule Feld bei Bedingung anzeigen | Kombinieren von Befehlen mit beschreibendem Text |
| Mehrere Aktionen | Separate Befehle | /create-panel und dann /update-layout | Jeweils einen Befehl anwenden |


### Umgebungsspezifische Funktionen

| Umgebung | Verfügbare Befehle | Besonderheiten |
|-------------|-------------------|------------------|
| Forms-Verwaltungsoberfläche | /create-form, /help | Erstellung und Verwaltung auf Formularebene |
| Adaptiver Forms-Editor und universeller Editor | Alle Befehle | Vollständiger Funktionssatz, detaillierte Konfiguration |



### Feldverweissyntax (kontextuelle Elemente)

Verwenden Sie `@fieldName`, um auf vorhandene Felder zu verweisen:

- `@firstName` - Feld Vorname
- `@email` - E-Mail-Feld
- `@phoneNumber` - Telefonnummernfeld
- `@dateOfBirth` - Feld Geburtsdatum

### Komponententypen

Diese Liste behandelt gängige Komponententypen. Die KI erkennt zwar Varianten oder speziellere Typen, aber die Verwendung dieser präzisen Begriffe liefert die besten Ergebnisse:

- `text input` - Einzeiliges Textfeld
- `text area` - Mehrzeiliges Textfeld
- `dropdown` - Liste auswählen
- `checkbox` - Einfaches Kontrollkästchen
- `checkbox group` - Mehrere Kontrollkästchen
- `radio group` - Optionsschaltflächengruppe
- `date picker` - Datumsauswahl
- `file upload` - Dateianhang
- `panel` - Container für Gruppierungsfelder


## Kernfunktionen und erweiterte Eingabeaufforderungsbeispiele

Der KI-Assistent versteht eine Vielzahl von Befehlen. Im Folgenden finden Sie einige Beispiele, um seine Leistungsfähigkeit zu veranschaulichen. Denken Sie daran, genaue Begriffe für Komponenten wie „Bedienfeld“, „Texteingabe“, „Kontrollkästchen“ usw. zu verwenden.

| Funktionskategorie | Beschreibung | Beispiel-Eingabeaufforderungen |
| ------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Formularerstellung** | Beginnen Sie ein neues Formular von Grund auf neu oder basierend auf einer Beschreibung. | `Create a new form titled 'Employee Onboarding'.` <br> `Generate a customer feedback form with fields for name, email, rating (1-5 stars), and comments.` <br> `Start a simple contact form with name, email, and message fields.` <br> `Design a multi-page registration form for an event.` <br> `Create a form based on the attached PDF template.` |
| **Design importieren** | Konvertieren eines bestehenden Designs (image, Figma, PDF) in ein AEM-Formular. | `Import the form design from this uploaded PDF file.` <br> `Convert the uploaded Figma design into an adaptive form, focusing on the 'User Profile' frame.` <br> `Use this JPEG image of our old paper form to create a new digital version.` <br> `Create a form based on the layout of the attached PNG.` <br> `Recreate the form shown in the attached screenshot with modern styling.` |
| **Hinzufügen von Komponenten und Bedienfeldern** | Fügen Sie verschiedene Formularfelder und strukturelle Container (Bedienfelder) hinzu. | `Add a text input field for 'First Name'.` <br> `Add a 'Personal Details' panel with fields for full name, date of birth, and phone number.` <br> `Insert a checkbox group for 'Interests' with options: Technology, Sports, Music.` <br> `Add a file upload component for 'Resume'.` <br> `Create a repeatable panel named 'WorkExperience' with fields for company, title, and dates.` <br> `Add a panel matching the layout shown in the attached design mockup.` |
| **Layout-Anpassungen** | Ändern Sie die Struktur und das Erscheinungsbild des Formularlayouts. | `Change the 'Personal Details' panel to a two-column layout.` <br> `Set the overall form layout to a wizard (multi-step) navigation.` <br> `Make the header section span the full width of the form.` <br> `Adjust the spacing between fields in the 'Address' panel to be compact.` <br> `Align all field labels to the left.` <br> `Update the form layout to match the attached wireframe.` |
| **Regelerstellung und Logik** | Implementieren Sie dynamisches Verhalten, Berechnungen und bedingte Sichtbarkeit. | `Make the 'Spouse Name' field visible only if 'Marital Status' is selected as 'Married'.` <br> `Calculate the 'Total Amount' by multiplying @quantity and @price.` <br> `Enable the submit button only when the @termsAndConditions checkbox is checked.` <br> `Set the value of @countryCode to '+1' if @country is 'United States'.` <br> `If @age is less than 18, show a message 'Must be 18 or older'.` |
| **Aktualisierung der Feldeigenschaften** | Ändern von Attributen bestimmter Formularfelder wie Beschriftungen, Platzhalter usw. | `Change the label of @email to 'Primary Email Address'.` <br> `Set the @comment field to be a multi-line text area.` <br> `Make the @phoneNumber field mandatory.` <br> `Add placeholder text 'Enter your ZIP code' to the @zipCode field.` <br> `Change the @country field to a dropdown and populate it with: USA, Canada, UK, Germany.` <br> `Update the help description for @password to 'Must include an uppercase letter, a number, and be at least 8 characters long.'` <br> `Set the maximum length of the @username field to 15 characters.` <br> `Configure the @dateOfBirth field to use a date picker.` <br> `Style the @email field to match the design shown in the attached image.` |
| **Aktionen übermitteln** | Definieren, was passiert, wenn ein Benutzer das Formular sendet. | `Configure the form to submit data to the REST endpoint /api/v2/application-submit.` <br> `Set up an email submission to hr@example.com and sales@example.com on successful submission.` <br> `Trigger an AEM workflow named 'NewLeadProcessing' when this form is submitted.` <br> `On submit, redirect the user to a thank you page at /content/thankyou.html.` |
| **Themen** | Vorhandene AEM Forms-Designs auf das Formular anwenden. | `Apply the 'Modern Business' theme to this form.` <br> `Switch to the 'Accessible Dark' theme.` <br> `Revert to the default canvas theme.` <br> `Apply styling that matches the brand guidelines shown in the attached style guide.` |
| **Navigation und Struktur** | Fügen Sie Navigationselemente hinzu oder organisieren Sie Teile des Formulars neu. | `Add a 'Next' button to the current panel and a 'Previous' button to the next panel.` <br> `Create a Table of Contents based on the form's panels.` <br> `Move the 'Address' panel to be before the 'Contact Information' panel.` |
| **Validierung** | Legen Sie spezifische Validierungsregeln für Felder fest. | `Set a regex pattern for the @employeeID field to be 'EMP\d{5}'.` <br> `Ensure the @age field only accepts numeric values between 18 and 99.` <br> `Validate the @email field to ensure it is a valid email format.` |
| **Plan überprüfen** (universeller Editor) | Vorschau der vorgeschlagenen Änderungen des Assistenten vor der Ausführung | `Add a contact form with fields for name, email, subject, and message.` (Der Assistent zeigt einen Plan der von ihm erstellten Komponenten und Eigenschaften an und klickt dann auf „Anwenden„). <br> `Create a form based on the attached design file.` (Der Assistent analysiert den Anhang und zeigt vor der Implementierung einen detaillierten Plan an.) |

## Best Practices für optimale Ergebnisse

Um den KI-Assistenten optimal zu nutzen, sollten Sie die folgenden Tipps beachten:

- **Einfach starten, inkrementell erstellen:** Mit kleineren, spezifischen Befehlen beginnen (z. B. „Texteingabe für „Vorname“ hinzufügen„), anstatt zunächst übermäßig komplexe mehrstufige Anfragen zu erstellen.
- **AEM Forms-Terminologie verwenden** Verwenden Sie Begriffe wie „Bedienfeld“, „Texteingabefeld“, „Kontrollkästchen-Gruppe“, „Übermittlungsaktion“, „Regel“ usw., um das Verständnis durch den Assistenten zu verbessern.
- **Referenzfelder:** Verwenden Sie beim Konfigurieren vorhandener Felder die `@fieldName` (z. B. `Make @firstName mandatory`).
- **Pläne überprüfen** Prüfen Sie Pläne stets sorgfältig auf Änderungen, die vom Assistenten im universellen Editor vorgeschlagen wurden, bevor Sie auf „Anwenden“ klicken.
- **Manuell validieren** Nachdem der Assistent Änderungen vorgenommen hat, sollten Sie Ihr Formular immer in der Vorschau anzeigen und testen, um sicherzustellen, dass es sich wie erwartet verhält und aussieht. KI ist ein leistungsstarkes Tool, doch die endgültige Validierung ist von entscheidender Bedeutung.
- **Iterieren und verfeinern:** Wenn die erste Eingabeaufforderung nicht das genaue Ergebnis liefert, versuchen Sie, die Anfrage neu zu formulieren oder in kleinere Schritte aufzuteilen.
- **Feedback geben:** Verwenden Sie den integrierten Feedback-Mechanismus, um dem Assistenten beim Lernen und Verbessern zu helfen (siehe Abschnitt „Feedback und Support„).

## Produkthilfe mit dem KI-Assistenten

Der KI-Assistent für AEM Forms dient nicht nur dem Erstellen von Inhalten. Er kann Ihnen auch dabei helfen, verschiedene Funktionen von AEM Forms zu lernen, zu verstehen und zu verwenden.

### Unterstützte Hilfethemen

Fragen können an den Assistenten gerichtet werden wie:

- „Wie erstelle ich ein neues adaptives Formular von Grund auf?“
- „Was ist ein Bedienfeld in Adaptive Forms und wie wird es verwendet?“
- „Erläutert, wie ein Design auf ein Formular angewendet wird.“
- „Welche Layouttypen werden für Formulare und Bedienfelder unterstützt?“
- „Wie konfiguriere ich verschiedene Übermittlungsaktionen wie das Senden einer E-Mail?“
- „Können Sie mir ein Figma-Design als Anleitung für das Erstellen eines Formulars geben?“
- „Wie kann ich ein mehrstufiges Formular am besten erstellen?“

### So bitten Sie um Hilfe:

1. Öffnen Sie den KI-Assistenten in der Verwaltungsoberfläche von Forms oder im Editor für adaptive Forms.
2. Geben Sie Ihre Frage in natürlicher Sprache ein (z. B. „Wie füge ich ein wiederholbares Bedienfeld hinzu?„).
3. Der Assistent antwortet mit:
   - Schrittweise Anleitungen.
   - Erläuterungen zu AEM Forms-Konzepten.
   - Links zur relevanten Adobe Experience League-Dokumentation, falls zutreffend.

### Tipps für eine bessere Hilfe:

- **Seien Sie spezifisch:** Stellen Sie jeweils nur eine klare Frage.
- **Schlüsselwörter verwenden:** Schließen Sie Schlüsselwörter ein, die für AEM Forms-Funktionen oder Benutzeroberflächenelemente relevant sind (z. B. „Editor für adaptive Formulare“, „Regeleditor“, „Design„).
- **Bei Bedarf umformulieren:** Wenn der Assistent die gewünschten Informationen nicht versteht oder bereitstellt, versuchen Sie, Ihre Frage zu vereinfachen oder andere Begriffe zu verwenden.


## Beheben häufiger Probleme

- **Assistent reagiert nicht:**
   - Stellen Sie sicher, dass Sie aktiv in einer unterstützten Umgebung arbeiten (Forms-Verwaltungsoberfläche, Editor für adaptive Forms oder universeller Editor).
   - Überprüfen Sie Ihre Internetverbindung.
   - Versuchen Sie, das Bedienfeld „KI-Assistent“ zu schließen und erneut zu öffnen.

- **Ungenaue oder unerwartete Antworten:**
   - Formulieren Sie Ihre Anfrage neu, um sie spezifischer oder einfacher zu gestalten.
   - Schlüsseln Sie eine komplexe Anfrage in kleinere, einzelne Befehle auf.
   - Stellen Sie sicher, dass Sie die Standardterminologie von AEM Forms verwenden.

- **Probleme beim Import von Designs (PDF/Figma/Image):**
   - Überprüfen Sie, ob die Designdatei klar, gut strukturiert und lesbar ist.
   - Stellen Sie sicher, dass das Dateiformat unterstützt wird (PDF, Figma-Link, allgemeine Bildtypen wie PNG, JPG).
   - Stellen Sie bei Figma sicher, dass der Frame, auf den Sie abzielen, klar definiert und zugänglich ist.

- **Feld `@fieldName` nicht erkannt:**
   - Überprüfen Sie den genauen Namen des Felds in Ihrem Formular. Bei Feldnamen wird zwischen Groß- und Kleinschreibung unterschieden und sie müssen genau übereinstimmen.
   - Stellen Sie sicher, dass das Feld bereits vorhanden ist, wenn Sie versuchen, es zu ändern.


## Feedback und Support

Ihr Beitrag ist für die kontinuierliche Verbesserung des KI-Assistenten von unschätzbarem Wert.

- **Feedback geben:** Verwenden Sie den integrierten **Befehl oder die Schaltfläche „Feedback geben** in der Benutzeroberfläche des KI-Assistenten, um Ihre Erlebnisse mitzuteilen, Probleme zu melden oder Verbesserungen vorzuschlagen. (Sie können z. B. `/feedback` eingeben oder nach einem Feedback-Symbol suchen.)
- **Offizieller Support:** Bei kritischen Problemen oder weiterer Unterstützung wenden Sie sich bitte über die offiziellen Adobe-Support-Kanäle oder die vom Unternehmen benannten Support-Kontakte.



## Arbeiten mit Anhängen

Der KI-Assistent unterstützt Dateianhänge, um die Formularerstellung und -konfiguration zu verbessern. Sie können verschiedene Dateitypen anhängen, um visuellen Kontext, Entwurfsverweise oder vorhandene Formulare zum Konvertieren bereitzustellen.

### Unterstützte Anlagentypen

| Dateityp | Anwendungsfälle | Befehle, die Anhänge unterstützen | Beispiele |
|-----------|-----------|-----------------------------------|----------|
| **images** (PNG, JPG, JPEG, GIF) | Formular-Layout-Referenzen, UI-Mockups, Scans von Papierformularen | /create-form, /add-form, /create-panel, /add-panel, /update-field | Hochladen eines Screenshots des gewünschten Layouts |
| **PDF-Dateien** | Bestehende Formulare zum Konvertieren, Entwurfsspezifikationen | /create-form, /add-form, /create-panel, /add-panel | Konvertieren von PDF-Anwendungsformularen |
| **FIGMA-Dateien** | Design-Systemverweise, Benutzeroberflächen-Prototypen | /create-form, /add-form, /create-panel | Importieren von Figma-Designrahmen |
| **Design-Dateien** (Skizze, Adobe XD-Exporte) | Visuelle Entwurfsverweise | /create-form, /add-form, /create-panel | Komponenten des Referenzentwurfssystems |

### Verwendung von Anhängen

1. **Fügen Sie vor oder mit Ihrem Befehl hinzu:**

   - Klicken Sie auf das Anlagensymbol in der Benutzeroberfläche des KI-Assistenten.
   - Datei(en) auf dem Gerät auswählen
   - Geben Sie den Befehl ein, der auf die angehängte Datei verweist

2. **Referenzanlagen in Befehlen:**

   ```
   /create-form based on the attached PDF application form
   /add-panel using the layout shown in the uploaded image
   /create-panel following the design in the attached Figma file
   /update-field @email to match the style in the attached screenshot
   ```

3. **Mehrere Anhänge:**

   - Sie können mehrere Dateien zum Vergleich oder zur Referenz anhängen
   - Angabe, welcher Anhang verwendet werden soll: „Verwenden des ersten angehängten Bildes“ oder „basierend auf der PDF-Datei“

### Best Practices für Anhänge

- **Klare, hochwertige Bilder:** Stellen Sie sicher, dass hochgeladene Bilder klar und lesbar sind, um eine bessere KI-Analyse zu ermöglichen
- **Relevante Dateinamen:** Verwenden Sie beschreibende Dateinamen, damit die KI den Kontext besser versteht.
- **Einzelfokus** Jede Anlage sollte sich auf einen bestimmten Aspekt (Layout, Felddesign usw.)
- **Unterstützte Formate:** Für optimale Kompatibilität an gängigen Formaten (PNG, JPG, PDF) festhalten
- **Dateigröße:** Anlagen unter 10 MB für optimale Verarbeitungsgeschwindigkeit

### Beispiel für Anhänge-Workflows

**Konvertieren eines Papierformulars:**

1. Scannen oder fotografieren Sie das Papierformular deutlich
2. Hochladen der Bilddatei
3. Befehl verwenden: `/create-form based on the attached form image, converting all fields to digital equivalents`

**Abgleichen eines Entwurfssystems:**

1. Exportieren oder Screenshot relevanter Design-Komponenten
2. Design-Referenz anfügen
3. Befehl verwenden: `/create-panel following the visual style and layout shown in the attached design`

**Feldstil-Referenz:**

1. Screenshot des gewünschten Felderscheinungsbildes anfügen
2. Befehl verwenden: `/update-field @email to match the styling and layout shown in the attached image`

## Verwandte Inhalte

[AEM Forms AI Assistant - Prompt Library](/help/edge/docs/forms/ai-assistant-prompt-library.md)

## Arbeiten mit Anhängen

Der KI-Assistent unterstützt Dateianhänge, um die Formularerstellung und -konfiguration zu verbessern. Sie können verschiedene Dateitypen anhängen, um visuellen Kontext, Entwurfsverweise oder vorhandene Formulare zum Konvertieren bereitzustellen.

### Unterstützte Anlagentypen

| Dateityp | Anwendungsfälle | Befehle, die Anhänge unterstützen | Beispiele |
|-----------|-----------|-----------------------------------|----------|
| **images** (PNG, JPG, JPEG, GIF) | Formular-Layout-Referenzen, UI-Mockups, Scans von Papierformularen | /create-form, /add-form, /create-panel, /add-panel, /update-field | Hochladen eines Screenshots des gewünschten Layouts |
| **PDF-Dateien** | Bestehende Formulare zum Konvertieren, Entwurfsspezifikationen | /create-form, /add-form, /create-panel, /add-panel | Konvertieren von PDF-Anwendungsformularen |
| **FIGMA-Dateien** | Design-Systemverweise, Benutzeroberflächen-Prototypen | /create-form, /add-form, /create-panel | Importieren von Figma-Designrahmen |
| **Design-Dateien** (Skizze, Adobe XD-Exporte) | Visuelle Entwurfsverweise | /create-form, /add-form, /create-panel | Komponenten des Referenzentwurfssystems |

### Verwendung von Anhängen

1. **Fügen Sie vor oder mit Ihrem Befehl hinzu:**

   - Klicken Sie auf das Anlagensymbol in der Benutzeroberfläche des KI-Assistenten.
   - Datei(en) auf dem Gerät auswählen
   - Geben Sie den Befehl ein, der auf die angehängte Datei verweist

2. **Referenzanlagen in Befehlen:**

   ```
   /create-form based on the attached PDF application form
   /add-panel using the layout shown in the uploaded image
   /create-panel following the design in the attached Figma file
   /update-field @email to match the style in the attached screenshot
   ```

3. **Mehrere Anhänge:**

   - Sie können mehrere Dateien zum Vergleich oder zur Referenz anhängen
   - Angabe, welcher Anhang verwendet werden soll: „Verwenden des ersten angehängten Bildes“ oder „basierend auf der PDF-Datei“

### Best Practices für Anhänge

- **Klare, hochwertige Bilder:** Stellen Sie sicher, dass hochgeladene Bilder klar und lesbar sind, um eine bessere KI-Analyse zu ermöglichen
- **Relevante Dateinamen:** Verwenden Sie beschreibende Dateinamen, damit die KI den Kontext besser versteht.
- **Einzelfokus** Jede Anlage sollte sich auf einen bestimmten Aspekt (Layout, Felddesign usw.)
- **Unterstützte Formate:** Für optimale Kompatibilität an gängigen Formaten (PNG, JPG, PDF) festhalten
- **Dateigröße:** Anlagen unter 10 MB für optimale Verarbeitungsgeschwindigkeit

### Beispiel für Anhänge-Workflows

**Konvertieren eines Papierformulars:**

1. Scannen oder fotografieren Sie das Papierformular deutlich
2. Hochladen der Bilddatei
3. Befehl verwenden: `/create-form based on the attached form image, converting all fields to digital equivalents`

**Abgleichen eines Entwurfssystems:**

1. Exportieren oder Screenshot relevanter Design-Komponenten
2. Design-Referenz anfügen
3. Befehl verwenden: `/create-panel following the visual style and layout shown in the attached design`

**Feldstil-Referenz:**

1. Screenshot des gewünschten Felderscheinungsbildes anfügen
2. Befehl verwenden: `/update-field @email to match the styling and layout shown in the attached image`
