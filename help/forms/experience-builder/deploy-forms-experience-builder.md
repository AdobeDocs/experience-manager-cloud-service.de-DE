---
title: Bereitstellen und Konfigurieren von Forms Experience Builder
description: Erfahren Sie, wie Sie mit Forms Experience Builder Formulare mit progressiver Offenlegung für alle Benutzertypen erstellen und verwalten können
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 977f227e-e941-4797-ba74-53d5b8c60ca9
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '1410'
ht-degree: 74%

---

# Bereitstellen und Konfigurieren von Forms Experience Builder

>[!NOTE]
>
> Forms Experience Builder ist im Rahmen eines Early-Access-Programms verfügbar. Bevor Sie beginnen, stellen Sie sicher, dass Sie Zugriff angefordert haben und erhalten haben. Vollständige Anweisungen finden Sie in den Informationen [Onboarding](product-overview.md#onboarding) .

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Dokumentation wird derzeit mit dem Produkt getestet und unterliegt möglichen Aktualisierungen und Überarbeitungen. Funktionen, Befehle und Beispiele können sich ändern, wenn Forms Experience Builder während des Early-Access-Programms weiterentwickelt wird.

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

| Beispiel für eine Konversation |   |
|--------------------------------------------------------------------------------------------------------------------------------------------|---|
| **Versuchen Sie diese Konversation, um ein umfassendes Kontaktformular zu erstellen (basierend auf der Summit-Demo):**<br><br>**Sie:** „Erstelle ein Kontaktformular zur Erfassung personenbezogener Informationen, einschließlich des vollständigen Namens, der E-Mail-Adresse, der Telefonnummer, des Firmennamens, der Stellenbezeichnung und eines Nachrichtenfelds für Anfragen“<br><br>**KI:** Vorlage auswählen<br>    Eine Dropdown-Liste zur Auswahl einer Vorlage <br><br>**KI:** Design auswählen<br>    Eine Dropdown-Liste zur Auswahl eines Designs/<br><br>**KI:** Formular erstellen | ![Ihr erstes Formular](/help/edge/docs/forms/assets/create-form.png) |
| <br>**AI:** Erstelltes Formular öffnen | </br> Das Formular wird im Editor erstellt und geöffnet. |


### Grundlegende Befehle

| Symbol | Zweck | Anwendungsbeispiel |
|--------|---------|---------------|
| `/` | Schnellaktionen und Tastaturbefehle | `/create-form contact form`, `/help validation rules`, `/update-layout wizard` |
| `@` | Referenzieren vorhandener Formularfelder | `@email`, `@firstName`, `Make @phoneNumber required` |
| Nur Text | Natürlicher Dialog | „Füge ein erforderliches Feld für die Telefonnummer hinzu“, „Erstelle eine Validierung für E-Mail“ |

**Spezifische Befehlsbeispiele:**

* `/create-form customer survey`: Erstellt ein neues Kundenumfrageformular
* `/add-field @email validation`: Fügt Validierungen zu vorhandenem Feld für die E-Mail-Adresse hinzu
* `/create-rule show @spouse if @maritalStatus equals married`: Erstellt eine bedingte Logik
* `/configure-submit to email support@company.com`: Richtet die E-Mail-Übermittlung ein
* `/help multi-step forms`: Bietet Hilfe zur Erstellung mehrstufiger Formulare

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

    👤 Sie: „Füge einen Abschnitt für personenbezogene Informationen hinzu“
    👤 Sie: „Füge eine Möglichkeit zum Datei-Upload von Lebensläufen hinzu“
    👤 Sie: „Füge eine Dropdown-Liste zur Länderauswahl hinzu“

**Detaillierte Spezifikationen:**

    👤 Sie: „Füge ein Panel für personenbezogene Informationen mit Feldern für vollständigen Namen, Geburtsdatum, Telefonnummer und E-Mail-Adresse hinzu“
    👤 Sie: „Füge eine Komponente für sicheres Hochladen von Dokumenten hinzu, die auf PDF-Dateien unter 5 MB beschränkt ist“
    👤 Sie: „Füge eine Dropdown-Liste zur Länderauswahl mit Optionen für die USA, Kanada, Großbritannien und Deutschland hinzu“

#### Dynamisches Verhalten erstellen

**Einfache Logik:**

    👤 Sie: „Zeige bei Auswahl von „Sonstiges“ zusätzliche Felder an“
    🤖 KI: „Eine bedingte Regel wurde erstellt, durch die bei Auswahl von „Sonstiges“ zusätzliche Felder angezeigt werden“
    
    👤 Sie: „Lege fest, dass das Feld für die E-Mail-Adresse erforderlich ist“
    🤖 KI: „Das Feld für die E-Mail-Adresse wurde aktualisiert, sodass es erforderlich ist und dies validiert wird“
    
    👤 Sie: „Berechne die Gesamtwerte automatisch“
    🤖 KI: „Berechnungslogik wurde hinzugefügt, durch die Gesamtwerte automatisch berechnet werden“

**Komplexe Geschäftsregeln:**

    👤 Sie: „Zeige die Felder für die Informationen der Partnerin bzw. des Partners nur dann an, wenn als Familienstand „Verheiratet“ festgelegt ist“
    🤖 KI: „Eine bedingte Regel wurde erstellt, die die Felder zur Partnerin bzw. zum Partners basierend auf dem Familienstand anzeigt“
    
    👤 Sie: „Berechne die Gesamtkosten durch Multiplikation von Menge und Preis und füge dann 10 % Steuer hinzu“
    🤖 KI: „Berechnungslogik mit Menge, Preis und Steuerberechnung wurde hinzugefügt“
    
    👤 Sie: „Aktiviere die Schaltfläche „Übermitteln“ nur, wenn alle erforderlichen Felder ausgefüllt und Bedingungen akzeptiert sind“
    🤖 KI: „Validierungslogik wurde erstellt, die die Übermittlung nur ermöglicht, wenn alle Bedingungen erfüllt sind“

#### Formularlayout und -design

**Änderungen am Layout:**

    👤 Sie: „Wandle dies in ein mehrstufiges Formular um“
    🤖 KI: „Das Formular wurde in ein Formular mit progressivem Layout und Navigation konvertiert“
    
    👤 Sie: „Ordne Felder in zwei Spalten an“
    🤖 KI: „Das Layout wurde aktualisiert, sodass Felder in zwei Spalten angezeigt werden“
    
    👤 Sie: „Konvertiere dies in ein Akkordeon-Layout“
    🤖 KI: „Das Formular wurde so umgewandelt, dass Abschnitte im Akkordeonstil angezeigt werden“

**Design-Verbesserungen:**

    👤 Sie: „Erstelle ein Formular mit Assistenten mit drei Schritten: personenbezogene Informationen, Voreinstellungen und Überprüfung“
    🤖 KI: „Ein Formular mit Assistenten, drei verschiedenen Schritten und Navigation wurde erstellt“
    
    👤 Sie: „Ordne die Adressfelder in einem kompakten zweispaltigen Layout an“
    🤖 KI: „Die Adressfelder wurden in einem kompakten zweispaltigen Format angeordnet“
    
    👤 Sie: „Aktualisiere das Layout, um es dem angehängten Wireframe anzupassen“
    🤖 KI: „Das Layout wurde so geändert, dass es der bereitgestellten Entwurfsreferenz entspricht“

### Konfiguration senden

Forms Experience Builder kann verschiedene Übermittlungsendpunkte konfigurieren, um Ihre Formulare mit externen Systemen und Diensten zu verbinden:

| Typ der Übermittlungsaktion | Setup-Befehl | Anwendungsfall |
|------------------|---------------|----------|
| **E-Mail** | „Formular an E-Mail senden“ | Benachrichtigungen und Bestätigungen für Formularübermittlungen |
| **REST-API** | „An REST-Endpunkt senden“ | Benutzerdefinierte Anwendungen und Systeme von Drittanbietern |
| **Cloud-Speicher** | „In Azure/SharePoint speichern“ | Dokumentenspeicher und Dateiverwaltung |
| **Workflow** | „Mit Power Automate verbinden“ | Automatisierung und Genehmigung von Geschäftsprozessen |
| **Marketing** | „Mit Marketo integrieren“ | Lead-Management und Marketing-Automatisierung |

**Beispiele für erweiterte Übermittlungskonfigurationen:**

    👤 Sie: „Sende die Formularübermittlungen an „hr@company.com“ und erstelle einen Fall in unserem CRM-System“
    🤖 KI: „E-Mail-Übermittlung und CRM-Übermittlungsaktion wurden konfiguriert“
    
    👤 Sie: „Übermittle Daten an unseren REST-API-Endpunkt und löse den neuen Kunden-Workflow aus“
    🤖 KI: „REST-API-Übermittlung mit Workflow-Triggern wurde eingerichtet“
    
    👤 Sie: „Sende Antworten per E-Mail an das Vertriebs-Team und füge den Lead zu unserer Marketing-Automatisierungsplattform hinzu“
    🤖 KI: „Multi-Channel-Übermittlung mit E-Mail- und Marketing-Automatisierung wurde konfiguriert“





## Erweiterte Formularvorgänge


### Erstellung komplexer Regeln

Erstellen Sie eine komplexe Validierungs- und Geschäftslogik, die auf Benutzerinteraktionen reagiert und die Datenintegrität sicherstellt:

    👤 Sie: „Zeige den Adressabschnitt nur dann an, wenn Benutzende „An andere Adresse liefern“ auswählen“
    🤖 KI: „Eine bedingte Regel wurde erstellt, durch die das Panel für die Adresse basierend auf Kontrollkästchenauswahl angezeigt/ausgeblendet wird“

### Mehrstufige Formularerstellung

    👤 Sie: „Erstelle ein progressives Formular mit 3 Schritten: personenbezogene Informationen, Voreinstellungen, Bestätigung“
    🤖 KI: „Ein progressives Formular mit Navigation zwischen Schritten und Validierung in jedem Schritt wurde erstellt“

### Erweiterte Feldtypen

* Datei-Upload mit Validierungs- und Größenbeschränkungen für die Dokumentenverwaltung
* Datumsauswahl mit Einschränkungen und Geschäftsregeln für die Planung
* Dropdown-Listen mit dynamischen Optionen, die sich je nach Benutzerauswahl ändern
* Optionsschaltflächen mit bedingter Logik für komplexe Entscheidungsbäume


### Konvertierung von PDF in Formulare

    👤 Sie: „Konvertieren Sie diese PDF in ein interaktives Formular“
    🤖 KI: „Die PDF wurde analysiert und ein Formular mit entsprechenden Feldtypen und Validierungen wurde erstellt“





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
