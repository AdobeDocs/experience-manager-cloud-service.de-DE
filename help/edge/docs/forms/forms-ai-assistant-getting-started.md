---
title: Erste Schritte mit Forms Experience Builder
description: Erfahren Sie, wie Sie mit Forms Experience Builder Formulare mit progressiver Offenlegung für alle Benutzertypen erstellen und verwalten können
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2013'
ht-degree: 6%

---


# Erste Schritte mit Forms Experience Builder

>[!NOTE]
>
> Die Funktion Forms Experience Builder ist im Rahmen des **Early Access (EA)-** verfügbar. Bei Interesse senden Sie eine kurze E-Mail von Ihrer Geschäftsadresse an `aem-forms-ea@adobe.com`, um Zugriff auf die Funktion zu beantragen.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Dokumentation wird derzeit mit dem Produkt getestet und unterliegt möglichen Aktualisierungen und Überarbeitungen. Funktionen, Befehle und Beispiele können sich ändern, während sich Forms Experience Builder während des Early Access-Programms weiterentwickelt.

Dieses umfassende Handbuch hilft Ihnen bei den ersten Schritten beim Erstellen und Verwalten von Formularen mithilfe der konversativen KI-Technologie. Unabhängig davon, ob Sie Anfänger sind oder Ihr erstes Formular erstellen möchten oder fortgeschrittene Benutzer, die komplexe Funktionen nutzen möchten, finden Sie hier detaillierte Informationen und praktische Beispiele, die Ihren Journey durch die Funktionen von Forms Experience Builder führen.

## Voraussetzungen und Einrichtung

### &#x200B;1. Zugriff anfordern

Forms Experience Builder ist derzeit als Teil des Early Access (EA)-Programms verfügbar. Um teilzunehmen und Zugang zu erhalten, benötigen Sie die folgenden Informationen:

**Erforderliche Informationen**

- **IMS-Organisations-ID**: Ihre Adobe-Organisationskennung
- **Programm-ID**: Ihre spezifische Programmkennung in Adobe Experience Cloud
- **Projektdetails**: Zeitlicher Ablauf, Umfang und vorgesehene Anwendungsfälle
- **Offizielle E-Mail**: Dem Adobe-Konto Ihres Unternehmens zugeordnet

**Abrufen der IMS-Organisations-ID und Programm-ID**

Detaillierte Anweisungen zum Suchen Ihrer IMS-Organisations-ID und Programm-ID finden Sie unter:

- [Einrichtungshandbuch für Adobe Experience Cloud-Organisationen](/help/onboarding/cloud-manager-introduction.md)
- [Programm- und Umweltmanagement](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

**Zugriff anfordern**

1. Erfassen Sie Ihre IMS-Organisations-ID und Programm-ID mithilfe der oben genannten Handbücher
2. Senden einer E-Mail an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) mit Zugriffsanfrage
3. In Ihre Anfrage einschließen:
   - Organisationsname und IMS-Organisations-ID
   - Programm-ID
   - Projektzeitplan und -umfang
   - Vorgesehene Anwendungsfälle und Geschäftsziele

>[!IMPORTANT]
>
> **Programm für eingeschränkte Verfügbarkeit**: Der Zugriff auf Forms Experience Builder muss von den internen Stakeholdern genehmigt werden. Adobe prüft Ihre Anfrage auf der Grundlage der Programmkapazität und der Ausrichtung an den Early-Access-Kriterien. Die Genehmigung ist nicht garantiert und hängt von der aktuellen Programmverfügbarkeit ab.

### &#x200B;2. Überprüfen, ob Forms aktiviert ist

Stellen Sie vor der Verwendung von Forms Experience Builder sicher, dass [AEM Forms für Ihre Umgebung aktiviert ](/help/forms/setup-forms-cloud-service.md).


### &#x200B;3. Einrichten der Umgebung


- **Für Edge Delivery Services (EDS):**

   - [Setup-Umgebung für Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
   - [Erstellen eines neuen Formulars mit der Edge Delivery Forms-Vorlage](/help/edge/docs/forms/universal-editor/create-forms.md)

- **Auf Kernkomponenten basierende Formulare:**

   - Gehen Sie in Ihrer Adobe Experience Manager-Instanz zu Forms > Forms und Dokumente .
   - [Erstellen einer neuen Seite mithilfe der Kernkomponentenvorlage](/help/forms/creating-adaptive-form-core-components.md)


## Schnellstart

### Zugriff auf Forms Experience Builder

Forms Experience Builder ist in der Benutzeroberfläche für die Verwaltung von Forms, im universellen Editor und im Editor für adaptive Forms verfügbar. Sie können jede dieser Methoden verwenden, um auf das Formular zuzugreifen:

**Benutzeroberfläche für die Forms-Verwaltung (für Kernkomponenten)**

1. **Navigieren Sie zu Forms**: Gehen Sie zu AEM > Forms > Forms und Dokumente
1. Klicken Sie auf das Symbol Forms Experience Builder in der Symbolleiste. Er befindet sich in der Nähe der oberen linken Ecke der Benutzeroberfläche.
   ![Symbol für den KI-Assistenten*](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}
1. Beginnen Sie mit der Erstellung des Formulars


**Adaptiver Forms-Editor (für Kernkomponenten)**

1. Gehen Sie zu AEM > Forms > Forms und Dokumente
2. [Erstellen eines neuen Formulars mit der Kernkomponentenvorlage](/help/forms/creating-adaptive-form-core-components.md)
3. Öffnen Sie ein Formular zur Bearbeitung
4. Klicken Sie auf das Forms Experience Builder-Symbol in der Editor-Symbolleiste
   ![Symbol für den KI-Assistenten*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

5. Beginnen Sie mit der Erstellung des Formulars


**Universeller Editor (für Edge Delivery Services Forms)**

1. Befolgen Sie die Anweisungen im [Edge Delivery Services-](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md), um Ihre EDS-Seite zu erstellen
1. Navigieren Sie im universellen Editor zu Ihrer EDS-Seite
1. Suchen Sie im rechten Bedienfeld nach dem Forms Experience Builder-Symbol
1. Zum Öffnen der Konversationsoberfläche klicken



### Ihr erstes Formular

| Beispiel für eine Unterhaltung |   |
|--------------------------------------------------------------------------------------------------------------------------------------------|---|
| **Versuchen Sie diese Konversation, um ein umfassendes Kontaktformular zu erstellen (basierend auf der Summit-Demo):**<br><br>**Sie:** „Erstellen Sie ein Kontaktformular, um persönliche Informationen zu erfassen, einschließlich des vollständigen Namens, der E-Mail-Adresse, der Telefonnummer, des Firmennamens, der Stellenbezeichnung und eines Nachrichtenfelds für Anfragen“<br><br>**KI:** Wählen Sie eine Vorlage<br>    Eine Dropdown-Liste zur Auswahl einer Vorlage <br><br>**KI:** Design auswählen<br>    Ein Dropdown-Menü zur Auswahl eines Designs/<br><br>**:** Formular erstellen | ![Ihr erstes Formular](/help/edge/docs/forms/assets/create-form.png) |
| <br>**AI:** Erstelltes Formular öffnen | </br> Das Formular wird im Editor erstellt und geöffnet |


### Wesentliche Befehle

| Symbol | Zweck | Anwendungsbeispiel |
|--------|---------|---------------|
| `/` | Schnellaktionen und Tastaturbefehle | `/create-form contact form`, `/help validation rules`, `/update-layout wizard` |
| `@` | Referenzieren vorhandener Formularfelder | `@email`, `@firstName`, `Make @phoneNumber required` |
| Nur Text | Natürliche Konversation | „Erforderliches Telefonnummernfeld hinzufügen“, „Validierung für E-Mail erstellen“ |

**Spezifische Befehlsbeispiele:**

- `/create-form customer survey` - Erstellt ein neues Kundenumfrageformular
- `/add-field @email validation`: Fügt Validierungen zu vorhandenem E-Mail-Feld hinzu
- `/create-rule show @spouse if @maritalStatus equals married` - Erstellt eine bedingte Logik
- `/configure-submit to email support@company.com` - Richtet die E-Mail-Übermittlung ein
- `/help multi-step forms` - Erhält Hilfe zur mehrstufigen Formularerstellung

### Tipps zum Erfolg

- **Sei spezifisch**: „Ein erforderliches E-Mail-Feld mit Validierung hinzufügen“ funktioniert besser als „E-Mail hinzufügen“
- **Vorhandene Felder referenzieren**: `@fieldName` beim Ändern von Formularen verwenden
- **Um Hilfe bitten**: Geben Sie `/help` ein, gefolgt von Ihrer Frage
- **Iterieren**: Führen Sie jeweils nur eine Änderung durch, um optimale Ergebnisse zu erzielen


## Möglichkeiten zum Erstellen eines Formulars

### &#x200B;1. Beginnen Sie mit den Eingabeaufforderungen in natürlicher Sprache

Beschreiben Sie Ihre Formularanforderungen in natürlicher Sprache, und Forms Experience Builder generiert die vollständige Formularstruktur:

**Beispiele:**

- „Erstellen eines Kreditantragsformulars mit persönlichen Informationen, finanziellen Details und Dokument-Uploads“
- „Erstellen Sie ein Formular für Kunden-Feedback mit Bewertungen, Kommentaren und Produktkategorien.“
- „Ich benötige ein mehrstufiges Anmeldeformular für eine Konferenz mit Zahlungsabwicklung“

### &#x200B;2. Importieren und Konvertieren

Transformieren vorhandener Formulare und Dokumente in moderne, interaktive Erlebnisse:

**Unterstützte Quellen:**

- **PDF forms**: Laden Sie statische PDFs hoch, um diese in interaktive digitale Formulare mit Validierungen zu konvertieren.
- **Screenshots oder Bilder**: Laden Sie Fotos von Papierformularen hoch, um funktionale digitale Versionen zu generieren
- **XFA Forms**: Konvertieren veralteter XFA-basierter Formulare in moderne responsive Formulare

**So importieren Sie:**

1. Klicken Sie auf das Anlagensymbol in der Benutzeroberfläche von Forms Experience Builder
2. Datei hochladen (PDF, Bild, Figma-Design usw.)
3. Beschreiben Sie Ihre Anforderungen:
   - „Konvertieren Sie dieses PDF-Formular in eine digitale Version.“
   - „Erstellen Sie ein Formular, das diesem Screenshot-Layout entspricht“
   - „Baue dieses Formular aus meinem Figma-Design“

**Unterstützte Dateitypen:**

- **Bilder** (PNG, JPG, GIF): Formularlayouts, Benutzeroberflächen-Mockups, gescannte Formulare, handgezeichnete Zeichnungen
- **PDF-Dateien**: Bestehende Formulare, Spezifikationen, Dokumente, AcroForms, XFA-Formulare
- **Screenshots**: Screenshots von Desktops/mobilen Apps, Fotos von Papierformularen, Whiteboard-Zeichnungen
- **Handgezeichnete Skizzen**: Serviettenskizzen, Drahtgitter, Konzeptzeichnungen (fotografiert)

### Wichtige Interaktionen

#### Hinzufügen von Formularelementen

**Einfache Ergänzungen:**

    👤 You: „Add a section for personal information“
    👤 You: „Include a file upload for resume“
    👤 You: „Add a dropdown for country selection“

**Detaillierte Spezifikationen:**

    👤 Sie: „Fügen Sie ein Bedienfeld für persönliche Informationen mit Feldern für vollständigen Namen, Geburtsdatum, Telefonnummer und E-Mail-Adresse hinzu“
    👤 Sie: „Fügen Sie eine sichere Datei-Upload-Komponente für Dokumente hinzu, die auf PDF-Dateien unter 5 MB beschränkt ist“
    👤 Sie: „Fügen Sie ein Dropdown-Menü für ein Land mit Optionen für die USA, Kanada, Großbritannien und Deutschland hinzu“

#### Erstellen von dynamischem Verhalten

**Einfache Logik:**

    👤 You: „Show additional fields when &#39;Other&#39; is selected“
    🤖 AI: „Created a conditional rule that shows additional fields when &#39;Other&#39; is selected“
    
    👤 You: „Make the email field required“
    🤖 AI: „Updated the email field to be required with validation“
    
    👤 You: „Calculate the total automatically“
    🤖 AI: „Added calculated logic to automatically compute total“

**Komplexe Geschäftsregeln:**

    👤 Sie: „Die Informationsfelder des Partners nur anzeigen, wenn der Familienstand auf „Verheiratet“ gesetzt ist“
    🤖 KI: „Bedingte Regel erstellt, die die Felder des Partners basierend auf dem Familienstand anzeigt“
    
    👤 Sie: „Berechnen Sie die Gesamtkosten durch Multiplikation von Menge und Preis, dann fügen Sie 10 % Steuer hinzu“
    🤖 KI: „Hinzugefügte Berechnungslogik mit Quantität, Preis und Steuerberechnung“
    
    👤 Sie: „Aktivieren Sie die Senden-Schaltfläche nur, wenn alle erforderlichen Felder ausgefüllt und Bedingungen akzeptiert sind“
    🤖 KI: „Erstellte Validierungslogik, die die Übermittlung nur ermöglicht, wenn alle Bedingungen erfüllt sind“

#### Formular-Layout und -Design

**Änderungen am Layout:**

    👤 You: „Make this a multi-step form“
    🤖 AI: „Converted the form to a progressive layout with navigation“
    
    👤 You: „Organize fields in two columns“
    🤖 AI: „Updated the layout to display fields in a two-column Arrangement“
    
    👤 You: „Convert to an accordion layout“
    🤖 AI: „Transformed the form to use accordion-style sections“

**Design-Verbesserungen:**

    👤 Sie: „Erstellen eines Formulars im Assistentenstil mit drei Schritten: persönliche Informationen, Voreinstellungen und Überprüfung“
    🤖 KI: „Erstellen eines Assistentenformulars mit drei verschiedenen Schritten und Navigation“
    
    👤 Sie: „Ordnen Sie die Adressfelder in einem kompakten zweispaltigen Layout an“
    🤖 KI: „Organisierte Adressfelder in einem kompakten zweispaltigen Format“
    
    👤 Sie: „Aktualisieren Sie das Layout, um es dem angehängten Wireframe anzupassen“
    🤖 KI: „Das Layout wurde so geändert, dass es der bereitgestellten Entwurfsreferenz entspricht“

### Konfiguration übermitteln

Forms Experience Builder kann verschiedene Übermittlungsendpunkte konfigurieren, um Ihre Formulare mit externen Systemen und Services zu verbinden:

| Übermittlungsaktionstyp | Setup-Befehl | Anwendungsfall |
|------------------|---------------|----------|
| **E-Mail** | „Formular an E-Mail senden“ | Benachrichtigungen und Bestätigungen für Formularübermittlungen |
| **REST-API** | „An REST-Endpunkt übermitteln“ | Benutzerdefinierte Anwendungen und Systeme von Drittanbietern |
| **Cloud-Speicher** | „In Azure/SharePoint speichern“ | Dokumentenspeicher und Dateiverwaltung |
| **Workflow** | „Verbindung zu Power Automate herstellen“ | Automatisierung und Validierungen von Geschäftsprozessen |
| **Marketing** | „Integration mit Marketo&quot; | Lead-Management und Marketing-Automatisierung |

**Beispiele für erweiterte Sende-Konfigurationen:**

    👤 Sie: „Senden Sie Formularübermittlungen an hr@company.com und erstellen Sie einen Fall in unserem CRM-System“
    🤖 KI: „Konfigurierte E-Mail-Übermittlung und CRM-Übermittlungsaktion“
    
    👤 Sie: „Übermitteln Sie Daten an unseren REST-API-Endpunkt und stellen Sie einen Trigger für den neuen Kunden-Workflow her“
    🤖 KI: „Richten Sie die REST-API-Übermittlung mit Workflow-Triggern ein“
    
    👤 Sie: „E-Mail-Antworten an das Vertriebsteam und fügen Sie den Lead zu unserer Marketing-Automatisierungsplattform hinzu“
    🤖 KI: „Konfigurierte Multi-Channel-Übermittlung mit E-Mail- und Marketing-Automatisierung“
&quot;&quot;&quot;




## Erweiterte Formularvorgänge


### Erstellung komplexer Regeln

Erstellen Sie eine ausgefeilte Validierungs- und Geschäftslogik, die auf Benutzerinteraktionen reagiert und die Datenintegrität sicherstellt:

    👤 You: „Show the address section only if the user selves &#39;Ship to different address&#39;&quot;
    🤖 KI: „Created a conditional rule that show/hids the address panel based on checkbox selection“

### Mehrstufige Formularerstellung

    👤 Sie: „Erstellen eines progressiven Formulars mit 3 Schritten: persönliche Informationen, Voreinstellungen, Bestätigung“
    🤖 KI: „Erstellen eines progressiven Formulars mit Navigation zwischen Schritten und Validierung in jedem Schritt“

### Erweiterte Feldtypen

- Datei-Upload mit Validierungs- und Größenbeschränkungen für die Dokumentenverwaltung
- Datumsauswahl mit Einschränkungen und Geschäftsregeln für die Planung
- Dropdown-Listen mit dynamischen Optionen, die sich je nach Benutzerauswahl ändern
- Optionsschaltflächen mit bedingter Logik für komplexe Entscheidungsbäume


### Konvertierung von PDF in Formulare

    👤 Sie: „Konvertieren Sie diese PDF in ein interaktives Formular“
    🤖 KI: „Analysierte die PDF und erstellte ein Formular mit entsprechenden Feldtypen und Validierungen“





## Produkthilfe und Lernprogramme

Mit dem Forms Experience Builder können Sie auch mehr über die Funktionen von AEM Forms erfahren:

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

## Best Practices

### Formularentwurf

- **Einfach halten**: Beginnen Sie mit wichtigen Feldern und fügen Sie Komplexität nur hinzu, wenn dies erforderlich ist, um eine Überlastung der Benutzer zu vermeiden
- **Klare Beschriftungen verwenden**: Machen Sie Feldzwecke mit beschreibenden Beschriftungen, die Benutzer durch das Formular führen, offensichtlich
- **Hilfetext bereitstellen**: Benutzende durch komplexe Felder mit kontextueller Hilfe und Beispielen führen
- **Gründlich testen**: Überprüfen Sie alle Benutzerpfade, um sicherzustellen, dass Formulare in allen Szenarien ordnungsgemäß funktionieren

### Benutzererlebnis

- **Fortschrittliche Offenlegung**: Zeigen Sie relevante Felder basierend auf dem Kontext an, um kognitive Belastung zu reduzieren und Abschlussraten zu verbessern
- **Übersichtliche Navigation**: Hilft Benutzern zu verstehen, wo sie sich im Formular befinden und welche Schritte verbleiben
- **Responsives Design**: Stellen Sie sicher, dass Formulare auf allen Geräten und in allen Bildschirmgrößen funktionieren, um eine maximale Barrierefreiheit zu gewährleisten
- **Barrierefreiheit**: Befolgen Sie die WCAG-Richtlinien, um Formulare für Menschen mit Behinderungen nutzbar zu machen

### Leistung

- **Felderanzahl optimieren**: Nur nach den erforderlichen Informationen fragen, um Formularabbrüche zu reduzieren und die Abschlussraten zu verbessern
- **Nutzen Sie die entsprechende Validierung**: Vermeiden Sie Fehler vor der Übermittlung, um sofortiges Feedback und Anleitung zu geben
- **Testabschlussraten**: Überwachen und verbessern Sie die Effektivität des Formulars durch Analysen und Benutzer-Feedback
- **Regelmäßige Updates**: Halten Sie Formulare mit den Geschäftsanforderungen und Benutzererwartungen auf dem neuesten Stand, um eine optimale Leistung zu erzielen

### Markenkonsistenz

- **Erstellen von Markenvorlagen**: Bereiten Sie gebrandete Formularvorlagen mit den Farben, Schriftarten und Stilen Ihres Unternehmens vor, bevor Sie mit der Erstellung des Formulars beginnen
- **Stilstandards definieren**: Konsistente Schaltflächenstile, Feld-Layouts und Abstandsrichtlinien festlegen, auf die in Eingabeaufforderungen verwiesen werden kann
- **Verwenden von Marken-Assets**: Bereiten Sie Logos, Farbcodes und Markenrichtlinien vor, die beim Erstellen von Formularen zur einfachen Referenz verwendet werden
- **Vorlagenbibliothek**: Erstellen Sie eine Sammlung von Formularvorlagen mit Branding für gängige Anwendungsfälle (Kontakt, Registrierung, Feedback)
- **Stil-Eingabeaufforderungen**: Beinhalten markenspezifische Anweisungen: „Verwenden Sie firmenblau (#1234AB) für Schaltflächen und die Firmenschriftart Helvetica“



## Fehlerbehebung

| Problem | Schnellkorrektur |
|-------|-----------|
| **Schnittstelle wird nicht geladen** | Browser aktualisieren, Internetverbindung prüfen |
| **Befehle funktionieren nicht** | Versuchen Sie es `/help` oder verwenden Sie stattdessen natürliche Sprache |
| **@fieldName nicht erkannt** | Rechtschreibprüfung, zuerst sicherstellen, dass das Feld vorhanden ist |
| **Datei-Upload schlägt fehl** | Verwenden von PDF/JPG/PNG unter 10 MB |
| **Formular sieht falsch aus** | Genauer gesagt: „Make it mobile-friendly“ |
| **Die Sendekonfiguration schlägt fehl** | API-Anmeldeinformationen und -Berechtigungen überprüfen |

**Brauchen Sie noch Hilfe?** Geben Sie `/help` ein, gefolgt von Ihrer spezifischen Frage, oder wenden Sie sich an Ihren Systemadministrator.

Weitere Unterstützung erhalten Sie in der Haupt-[Forms Experience Builder-Eingabeaufforderungsbibliothek ](ai-assistant-prompt-library.md) oder von Ihrem Systemadministrator bzgl. technischer Unterstützung.
