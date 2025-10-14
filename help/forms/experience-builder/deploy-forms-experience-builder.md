---
title: Bereitstellen und Konfigurieren von Forms Experience Builder
description: Erfahren Sie, wie Sie mit Forms Experience Builder Formulare mit progressiver Offenlegung für alle Benutzertypen erstellen und verwalten können
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1404'
ht-degree: 32%

---


# Bereitstellen und Konfigurieren von Forms Experience Builder

>[!NOTE]
>
> Forms Experience Builder ist im Rahmen eines Early-Access-Programms verfügbar. Bevor Sie beginnen, stellen Sie sicher, dass Sie Zugriff angefordert haben und erhalten haben. Vollständige Anweisungen finden Sie in den Informationen [Onboarding](product-overview.md#onboarding) .

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Dokumentation wird derzeit mit dem Produkt getestet und unterliegt möglichen Aktualisierungen und Überarbeitungen. Funktionen, Befehle und Beispiele können sich ändern, während sich Forms Experience Builder während des Early Access-Programms weiterentwickelt.

Dieses umfassende Handbuch hilft Ihnen bei den ersten Schritten zum Erstellen und Verwalten von Formularen mit der dialogbasierten KI-Technologie. Ob Sie noch am Anfang stehen und Ihr erstes Formular erstellen möchten oder schon über Erfahrung verfügen und komplexe Funktionen nutzen möchten: Hier finden Sie detaillierte Informationen und praktische Beispiele, die Ihren Weg durch die Funktionen von Forms Experience Builder hilfreich begleiten.

## Voraussetzungen und Einrichtung

### Zugriffsanforderungen

Stellen Sie vor der Verwendung von Forms Experience Builder Folgendes sicher:

* **Zugriff auf Forms Experience Builder** - verfügbar über das Early Access-Programm
* **AEM Forms as a Cloud Service** - Produktions-Autorenumgebung mit Kernkomponenten für adaptive Forms
* **Grundlegendes** - Vertrautheit mit Formularkonzepten und Geschäftsanforderungen

### Überprüfen, ob Formulare aktiviert sind

Stellen Sie vor der Verwendung von Forms Experience Builder sicher, dass [AEM Forms für Ihre Umgebung aktiviert ist](/help/forms/setup-forms-cloud-service.md).

### Einrichten Ihrer Arbeitsumgebung

Ihr Einrichtungsprozess hängt von Ihrer AEM Forms-Implementierung ab. Wählen Sie den Pfad aus, der Ihrem Projekt entspricht.

**Für Edge Delivery Services**

Wenn Sie Edge Delivery Services Forms verwenden und hauptsächlich den universellen Editor verwenden. [Bereiten Sie Ihr Projekt für Edge Delivery Services Forms &#x200B;](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md). Dies ist eine einmalige Einrichtung zum Aktivieren von Forms Experience Builder.

**Für Formulare, die auf Kernkomponenten basieren**

Wenn Sie adaptive Forms verwenden, die auf Kernkomponenten in der AEM-Autorenumgebung basieren, stellen Sie sicher, [Kernkomponenten für adaptive Forms aktiviert sind](/help/forms/enable-adaptive-forms-core-components.md) für Ihre Umgebung.



## Schnellstart

### Zugriff auf Forms Experience Builder

Sie können auf Forms Experience Builder je nach Workflow und Formulartyp von drei Hauptspeicherorten aus zugreifen.


**1. Adaptiver Forms-Editor (für Kernkomponenten)**

Sie können den Builder direkt starten, während Sie ein bestimmtes Formular bearbeiten.

1. Navigieren Sie zu **AEM > Forms > Forms und Dokumente**.
1. [Erstellen Sie ein neues Formular mit einer Kernkomponentenvorlage](/help/forms/creating-adaptive-form-core-components.md) oder öffnen Sie ein vorhandenes.
1. Wählen Sie das Symbol **Forms Experience Builder** in der Symbolleiste des Editors aus, um die Konversationsoberfläche zu öffnen.

   ![Symbol für den KI-Assistenten*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

**1. Universeller Editor (für Edge Delivery Services Forms)**

Bei Formularen, die über Edge Delivery Services bereitgestellt werden, ist der Builder in den universellen Editor integriert.

1. Öffnen Sie Ihr Edge Delivery Services-Formular im universellen Editor.
2. Wählen Sie das Symbol **Forms Experience Builder** im rechten Bedienfeld, um die Konversationsoberfläche zu starten.

### Ihr erstes Formular

| Beispiel für eine Unterhaltung |   |
|--------------------------------------------------------------------------------------------------------------------------------------------|---|
| **Versuchen Sie diese Konversation, um ein umfassendes Kontaktformular zu erstellen (basierend auf der Summit-Demo):**<br><br>**Sie:** „Erstellen Sie ein Kontaktformular, um persönliche Informationen zu erfassen, einschließlich des vollständigen Namens, der E-Mail-Adresse, der Telefonnummer, des Firmennamens, der Stellenbezeichnung und eines Nachrichtenfelds für Anfragen“<br><br>**KI:** Wählen Sie eine Vorlage<br>    Eine Dropdown-Liste zur Auswahl einer Vorlage <br><br>**KI:** Design auswählen<br>    Ein Dropdown-Menü zur Auswahl eines Designs/<br><br>**:** Formular erstellen | ![Ihr erstes Formular](/help/edge/docs/forms/assets/create-form.png) |
| <br>**AI:** Erstelltes Formular öffnen | </br> Das Formular wird im Editor erstellt und geöffnet |


### Grundlegende Befehle

| Symbol | Zweck | Anwendungsbeispiel |
|--------|---------|---------------|
| `/` | Schnellaktionen und Tastaturbefehle | `/create-form contact form`, `/help validation rules`, `/update-layout wizard` |
| `@` | Referenzieren Sie vorhandene Formularfelder | `@email`, `@firstName`, `Make @phoneNumber required` |
| Nur Text | Natürlicher Dialog | „Erforderliches Telefonnummernfeld hinzufügen“, „Validierung für E-Mail erstellen“ |

**Spezifische Befehlsbeispiele:**

* `/create-form customer survey` - Erstellt ein neues Kundenumfrageformular
* `/add-field @email validation`: Fügt Validierungen zu vorhandenem E-Mail-Feld hinzu
* `/create-rule show @spouse if @maritalStatus equals married` - Erstellt eine bedingte Logik
* `/configure-submit to email support@company.com` - Richtet die E-Mail-Übermittlung ein
* `/help multi-step forms` - Erhält Hilfe zur mehrstufigen Formularerstellung

### Tipps für den Erfolg

* **Seien Sie spezifisch**: „Ein erforderliches E-Mail-Feld mit Validierung hinzufügen“ funktioniert besser als „E-Mail hinzufügen“
* **Referenzieren Sie vorhandene Felder**: Verwenden Sie `@fieldName` beim Ändern von Formularen
* **Bitten Sie um Hilfe**: Geben Sie `/help` gefolgt von Ihrer Frage ein 
* **Iterieren Sie**: Führen Sie jeweils nur eine Änderung durch, um optimale Ergebnisse zu erzielen


## Möglichkeiten zum Erstellen eines Formulars

### Beginnen Sie mit der Eingabe natürlicher Sprachen

Beschreiben Sie Ihre Formularanforderungen in natürlicher Sprache und Forms Experience Builder generiert die vollständige Formularstruktur:

**Beispiele:**

* „Erstelle ein Kreditantragsformular mit persönlichen Informationen, finanziellen Details und Dokument-Uploads“
* „Erstelle ein Kunden-Feedback-Formular mit Bewertungen, Kommentaren und Produktkategorien“
* „Ich benötige ein mehrstufiges Anmeldeformular für eine Konferenz, einschließlich Zahlungsverarbeitung“


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

#### Dynamisches Verhalten erstellen

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

#### Formularlayout und -design

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

### Konfiguration senden

Der Forms Experience Builder kann verschiedene Übermittlungsendpunkte konfigurieren, um Ihre Formulare mit externen Systemen und Diensten zu verbinden:

| Übermittlungsaktionstyp | Setup-Befehl | Anwendungsfall |
|------------------|---------------|----------|
| **E-Mail** | „Formular an E-Mail senden“ | Benachrichtigungen und Bestätigungen für Formularübermittlungen |
| **REST-API** | „An REST-Endpunkt senden“ | Benutzerdefinierte Anwendungen und Systeme von Drittanbietern |
| **Cloud-Speicher** | „In Azure/SharePoint speichern“ | Dokumentenspeicher und Dateiverwaltung |
| **Workflow** | „Mit Power Automate verbinden“ | Automatisierung und Genehmigung von Geschäftsprozessen |
| **Marketing** | „Mit Marketo integrieren“ | Lead-Management und Marketing-Automatisierung |

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

Erstellen Sie eine komplexe Validierungs- und Geschäftslogik, die auf Benutzerinteraktionen reagiert und die Datenintegrität sicherstellt:

    👤 You: „Show the address section only if the user selves &#39;Ship to different address&#39;&quot;
    🤖 KI: „Created a conditional rule that show/hids the address panel based on checkbox selection“

### Mehrstufige Formularerstellung

    👤 Sie: „Erstellen eines progressiven Formulars mit 3 Schritten: persönliche Informationen, Voreinstellungen, Bestätigung“
    🤖 KI: „Erstellen eines progressiven Formulars mit Navigation zwischen Schritten und Validierung in jedem Schritt“

### Erweiterte Feldtypen

* Datei-Upload mit Validierungs- und Größenbeschränkungen für die Dokumentenverwaltung
* Datumsauswahl mit Einschränkungen und Geschäftsregeln für die Planung
* Dropdown-Listen mit dynamischen Optionen, die sich je nach Benutzerauswahl ändern
* Optionsschaltflächen mit bedingter Logik für komplexe Entscheidungsbäume


### Konvertierung von PDF in Formulare

    👤 Sie: „Konvertieren Sie diese PDF in ein interaktives Formular“
    🤖 KI: „Analysierte die PDF und erstellte ein Formular mit entsprechenden Feldtypen und Validierungen“





## Produkthilfe und Lernprogramme

Der Forms Experience Builder kann Sie auch über die Funktionen von AEM Forms informieren:

### Stellen Sie Fragen wie:

* „Wie erstelle ich ein mehrstufiges Formular?“
* „Was ist der Unterschied zwischen Panels und Abschnitten?“
* „Wie richte ich E-Mail-Benachrichtigungen ein?“
* „Was sind die Best Practices für mobilfreundliche Formulare?“
* „Wie kann ich Designs auf meine Formulare anwenden?“

### Hilfe zu:

* Konzepten und Terminologie von AEM Forms
* Schrittweisen Anleitungen für komplexe Funktionen
* Best Practices und Einschränkungen
* Fehlerbehebung bei Indizierungsproblemen


Weitere Unterstützung erhalten Sie in der primären [Forms Experience Builder-Prompt-Bibliothek](/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md) oder wenden Sie sich für Hilfe bei technischen Problemen an Ihren Systemadmin.
