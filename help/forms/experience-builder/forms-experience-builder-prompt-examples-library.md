---
title: Forms Experience Builder - Prompt-Bibliothek
description: Sammlung bewährter Prompt-Muster und Beispiele zum Erstellen von Formularen mit KI-Unterstützung in der Benutzeroberfläche für die Formularverwaltung, im Editor für adaptive Formulare und im universellen Editor.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: c8f64082-a23f-4919-ad66-042faad77d31
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 38%

---


# Forms Experience Builder - Prompt-Bibliothek

Eine Sammlung wiederverwendbarer Prompt-Muster und Beispiele, die für Forms Experience Builder optimiert ist. Diese optimierte Bibliothek konzentriert sich auf die beiden wesentlichen Methoden „Von Grund auf neu erstellen“ und „Importieren und konvertieren“ mit verbesserter Unterstützung für LLM-gestützte intelligente Felder und Markenkonsistenz.

>[!NOTE]
>
> Forms Experience Builder ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## Verwenden dieser Prompt-Bibliothek

Diese Bibliothek bietet wiederverwendbare Prompt-Muster für gängige Szenarien bei der Formularerstellung. Umfassende Best Practices finden Sie im Handbuch [Forms Experience Builder – Erste Schritte](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

### Schnelltipps für diese Bibliothek

- **Beginnen Sie mit Beispielen**: Verwenden Sie die bereitgestellten Prompts als Vorlagen und passen Sie sie an Ihre Anforderungen an
- **Zwei Erstellungsmethoden**: Wählen Sie den Ansatz „Von Grund auf neu erstellen“ oder „Importieren und konvertieren“
- **Seien Sie spezifisch**: Fügen Sie allgemeinen Beispielen eigene Details hinzu
- **Testen Sie gründlich**: Validieren Sie Ergebnisse immer in Ihrer spezifischen Umgebung

### Markenvorlagen und -stile

**Bereiten Sie Marken-Assets vorab für eine konsistente Formularerstellung vor:**

- **Markenvorlagen** - Bereiten Sie standardisierte Formularvorlagen mit den Farben, Schriftarten und Layout-Mustern Ihres Unternehmens vor
- **Stilrichtlinien** - Definieren Sie konsistente Feldstile, Schaltflächendesigns und Abstandsstandards, die Forms Experience Builder anwenden kann
- **Komponentenbibliothek** - Arbeiten Sie mit Ihrem Entwicklungs-Team zusammen, um wiederverwendbare Formularkomponenten vorzubereiten, die Ihrer Markenidentität entsprechen
- **Grafik-Assets**: Bereiten Sie Logos, Symbole und Hintergrundelemente für die Formularintegration vor


## Beispiele für inkrementelle Entwicklung

Diese Beispiele zeigen, wie Sie Formulare Schritt für Schritt erstellen, indem Sie einfach anfangen und schrittweise Komplexität hinzufügen:

### Beispiel 1: Inkrementelles Erstellen eines Kontaktformulars

**Schritt 1 – Einfach starten:**

    Erstellen Sie ein einfaches Kontaktformular mit den Feldern Name, E-Mail und Nachricht

**Schritt 2 – Validierung hinzufügen:**

    Erstellen Sie @name und @email Pflichtfelder mit entsprechender Validierung

**Schritt 3 – Verbessern des Benutzererlebnisses:**

    Fügen Sie Platzhaltertext hinzu: @name „Ihr vollständiger Name“, @email &quot;your.email@company.com&quot; @message „Sagen Sie uns, wie wir helfen können“

**Schritt 4 – Erweiterte Funktionen hinzufügen:**

    Dropdown-Anfrage hinzufügenTyp mit Optionen: „Allgemeine Frage“, „Support-Anfrage“, „Verkaufsanfrage“, „Partnerschaft“

**Schritt 5 – Implementieren einer bedingten Logik:**

    /create-rule zeigen @urgencyLevel Dropdown-Liste (Niedrig, Medium, Hoch) nur an, wenn @inquiryType gleich „Support-Anfrage“

### Beispiel 2: Inkrementelles Erstellen eines Registrierungsformulars

**Schritt 1 – Grundstruktur:**

    Erstellen eines Benutzerregistrierungsformulars mit Bedienfeld für personenbezogene Daten

**Schritt 2 – Kernfelder hinzufügen:**

    Felder für @firstName, @lastName, @email und @phoneNumber mit entsprechender Validierung hinzufügen

**Schritt 3 – Business-Logik hinzufügen:**

    Regel erstellen: Wenn @age jünger als 18 Jahre ist, Abschnitt mit Informationen zu Eltern/Erziehungsberechtigten anzeigen

**Schritt 4 – Mit Voreinstellungen verbessern:**

    Bedienfeld „Voreinstellungen“ mit @newsletterSubscription, @marketingConsent, @termsAccepted hinzufügen

**Schritt 5 - Datei-Upload hinzufügen:**

    Ein Datei-Upload-Feld für @profilePicture mit einer Größenbeschränkung von 5 MB wird einbezogen

## Formularerstellung und -verwaltung

**Anwendungsfall:** Sie müssen neue Formulare erstellen oder vorhandene ändern.

**Verwendung:** Wählen Sie einen von zwei Ansätzen: von Grund auf neu erstellen oder Importieren und Konvertieren (siehe [Erste Schritte](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

**Beispiel-Prompt – Einfaches Formular erstellen:**

    Erstellen Sie ein Formular für Kunden-Feedback mit:
    - Produktbewertung (1-5 Sterne)
    - Feld „Kommentar“ für detailliertes Feedback
    - Kunden-E-Mail (optional)
    - An E-Mail-Benachrichtigung senden

**Beispiel-Prompt – Komplexes Formular erstellen:**

    Erstellen eines umfassenden Onboarding-Formulars für Mitarbeiter mit:
    
    **Abschnitt „Persönliche Informationen“:**
    - Vollständiger Name (Vor-, Mittel-, Nachname)
    - Geburtsdatum mit Altersvalidierung
    - Kontaktinformationen (E-Mail, Telefon, Adresse)
    - Kontaktinformationen für Notfälle
    
    **Beschäftigungsdetails:**
    - Auswahl von Positionen und Abteilungen
    - Startdatum mit der Validierung des Geschäftstags
    - Gehaltsinformationen mit Vertraulichkeitshinweis
    - Berichtsstruktur
    
    **Dokument-Upload:**
    - Wiederaufnahme/Lebenslauf (PDF, DOC, DOCX)
    )
    - ID-Bestätigungsdokumente
    - und Bankinformationen
    
    - Unterzeichnete Beschäftigung Vereinbarung
    Voreinstellungen:**
    - Leistungsauswahl mit Kostenrechner
    - Voreinstellungen für den Arbeitsplan
    - Schulungsanforderungen**Validierungsregeln:**Validierung des E-Mail-FormatsValidierungAlter muss 18 oder älter sein**- Alle erforderlichen Dokumente müssen hochgeladen werden
    
    - Bedingungen müssen akzeptiert werden**Aktionen senden:**Bestätigungs-E-Mail an neueMitarbeiter senden
    - HR- Personalabteilung benachrichtigen
    - Erstellen Sie einen Datensatz in einem HR
     
     
     
    
     
     
     
     
     
-
**Prompts zur Formularverwaltung:**

    Importieren Sie dieses PDF-Antragsformular und konvertieren Sie es in ein adaptives Formular mit erweiterter Validierung
    
    Aktualisieren Sie das bestehende Kontaktformular, um Social-Media-Handles und bevorzugte Kontaktmethode einzuschließen
    
    Organisieren Sie das Registrierungsformular in einen 3-stufigen Assistenten: Persönliche Informationen, Voreinstellungen, Bestätigung

## Feldverwaltung und -konfiguration

**Anwendungsfall:** Sie müssen Formularfelder hinzufügen, ändern oder konfigurieren.

**Verwendung:** Seien Sie präzise in Bezug auf Feldtypen, Validierungsregeln und Anforderungen an das Benutzererlebnis.

**Beispiel-Prompt - Einfaches Feld hinzufügen:**

    Fügen Sie ein Texteingabefeld für „Firmenname“ mit dem Platzhalter „Geben Sie Ihren Firmennamen ein“

**Beispiel-Prompt – Erweiterte Feldkonfiguration:**

    Fügen Sie einen umfassenden Adressabschnitt mit folgender Adresse hinzu:
    
    **Straßenadresse:**
    - Adresszeile 1 (erforderlich, max. 100 Zeichen)
    - Adresszeile 2 (optional, max. 100 Zeichen)
    - Stadt (erforderlich, Dropdown mit allgemeinen Städten)
    - Bundesland/Provinz (erforderlich, Dropdown)
    - Postleitzahl (erforderlich, Formatvalidierung)
    - Land (erforderlich, Standard „Vereinigte Staaten„)
    
    **Validierungsregeln:**
    - Postleitzahl muss mit der Statusauswahl übereinstimmen
    - Adresszeile 1 darf nicht leer sein
    - Stadt muss eine gültige Stadt für das ausgewählte Bundesland sein
    
    **Benutzererlebnis:**
    - Automatische Vervollständigung für Adressfelder
    - Entfernen von Kennzeichnungen und Hilfetext
    - Mobile-freundliche Eingabefelder
    - Einhaltung der Barrierefreiheit

**Prompts zur Feldkonfiguration:**

    @email Feld mit Echtzeitvalidierung und benutzerdefinierter Fehlermeldung erforderlich machen
    
    Dropdown für @country @phoneNumber mit Optionen für die USA, Kanada, Großbritannien, Deutschland, Frankreich und „Sonstige“
    
    Feld mit Format (XXX) XXX-XXXX konfigurieren und Validierung
    
    Feld für den Datei-Upload für @resume mit PDF- und DOC-Einschränkungen hinzufügen, max. 5 MB

## LLM-optimierte intelligente Felder

**Anwendungsfall:** Sie benötigen Felder mit vorausgefüllten Optionen, die die Wissensdatenbank der KI nutzen.

**Verwendung:** Fordern Sie Felder an, für die umfassende Datensätze erforderlich sind. Die KI kann Optionen dank des integrierten Wissens automatisch ausfüllen.

### Geografische Felder und Standortfelder

**Flughäfen und Verkehr:**

    Dropdown für Abflughäfen mit allen wichtigen internationalen Flughäfen hinzufügen
    Feld „Ankunftsflughafen“ mit IATA-Codes und vollständigen Namen hinzufügen
    Feld für den nächstgelegenen Flughafen zum Benutzerstandort erstellen
    Eine Auswahl an Bahnhöfen für europäische Städte hinzufügen

**Verwaltungsregionen:**

    Vollständige Liste der US-Bundesstaaten mit Abkürzungen hinzufügen
    Erstellen Sie eine Dropdownliste mit ISO-Codes und vollständigen Namen
    Fügen Sie ein Feld für die größten Städte der Welt mit Zeitzonen hinzu
    Fügen Sie eine Dropdown-Liste der kanadischen Provinzen und Territorien hinzu
    Fügen Sie ein Feld für britische Countys und Postgebiete hinzu

### Unternehmens- und Branchendaten

**Unternehmensklassifizierungen:**

    Feld für die Branchenklassifizierung mit NAICS-Codes hinzufügen
    Erstellen Sie eine Dropdown-Liste der Typen von Geschäftseinheiten (LLC, Corporation, Partnerschaft usw.)
    Feld für Unternehmensgrößenkategorien hinzufügen (Start, KMU, Unternehmen)
    Abteilungsauswahl für große Organisationen einbeziehen
    Feld für professionelle Servicetypen hinzufügen

**Berufsklassifiizierungen:**

    Feld für Stellenbezeichnungen mit gemeinsamen Branchenrollen hinzufügen
    Erstellen Sie ein Dropdown-Menü mit professionellen Zertifizierungen nach Feld
    Schulungsstufen mit Abschlussarten einbeziehen
    Feld für jahrelange Erfahrung hinzufügen
    Erstellen Sie eine Auswahl für Programmiersprachen und Frameworks

### Normen und Vorschriften

**Finanz- und Rechtsfragen:**

    Feld für Währungs-Codes mit Symbolen und Wechselkursen hinzufügen
    Erstellen Sie eine Dropdown-Liste der Steuer-ID-Typen nach Land
    Feld für juristische Dokumenttypen einschließen
    Zahlungsmethode-Optionen mit Sicherheitsmerkmalen hinzufügen
    Erstellen Sie eine Auswahl für Bankinstitute nach Land

**Technische Standards:**

    Dropdown-Liste mit Dateitypen mit Erweiterungen hinzufügen
    Optionen für Netzwerkprotokolle einschließen
    Feld für Datenbanktypen und Versionen hinzufügen
    Auswahl für API-Authentifizierungsmethoden erstellen

### Gesundheitswesen und Medizin

**Medizinische Klassifizierungen:**

    Feld für medizinische Fachgebiete hinzufügen
    Erstellen Sie eine Dropdown-Liste mit allgemeinen Medikamenten mit generischen Namen
    Feld für Versicherungsanbietertypen einschließen
    Eine Auswahl für medizinische Notfallkontakte hinzufügen
    Erstellen Sie ein Feld für Ernährungseinschränkungen und Allergien

### Zeit- und Kalenderintelligenz

**Datums- und Uhrzeitfelder:**

    Feld für Geschäftszeiten mit Zeitzonenverarbeitung hinzufügen
    Erstellen Sie eine Dropdown-Liste der Feiertage nach Land
    Saisonale Optionen mit Datumsbereichen einschließen
    Feld für die Buchung von Konferenzräumen mit Verfügbarkeit hinzufügen
    Auswahl für Muster wiederkehrender Meetings erstellen

### Produkt- und Service-Kategorien

**E-Commerce-Klassifizierungen:**

    Feld für Produktkategorien mit Unterkategorien hinzufügen
    Erstellen eines Dropdown-Menüs der Versandmethoden mit Versandschätzungen
    Feld für Rückgaberichtlinienoptionen einbeziehen
    Auswahl für Kundenprioritätsstufen hinzufügen
    Feld für Abonnement-Abrechnungszyklen erstellen

**Beispiel-Prompts für intelligente Felder:**

    „Ein Feld für Abflughäfen mit allen wichtigen Flughäfen weltweit hinzufügen, einschließlich IATA-Codes und Städtenamen“
    
    „Erstellen Sie ein umfassendes Branchenfeld mit der standardmäßigen NAICS-Klassifizierung mit Technologie-Unterkategorien“
    
    „Schließen Sie ein Dropdown-Menü für die Zertifizierung ein, das sich auf der Grundlage des ausgewählten Arbeitsfelds anpasst“
    
    „Fügen Sie ein Feld für internationale Telefonnummern hinzu, das Formate auf der Grundlage des ausgewählten Landes“
    
    „Erstellen Sie ein Auswahlfeld für Universitäten mit wichtigen Institutionen, die nach Land und Ranking organisiert sind“

## Regelerstellung und Geschäftslogik

**Anwendungsfall:** Sie müssen bedingte Logik, Validierungsregeln oder Geschäftsprozesse implementieren.

**Verwendung:** Beschreiben Sie die Geschäftslogik klar und geben Sie Bedingungen und Aktionen an.

**Beispiel-Prompt – Einfache bedingte Logik:**

    Erstellen Sie eine Regel, die das Panel „@spouseInformation“ nur anzeigt, wenn „@maritalStatus“ gleich „verheiratet“ ist

**Beispiel-Prompt –  Komplexe Geschäftsregeln:**

    Umfassende Validierung des Kreditantrags implementieren:
    
    **Einkommensvalidierung:**
    - Bei @annualIncome kleiner als 30000:
    - Warnmeldung anzeigen: „Das Einkommen kann für den angeforderten Darlehensbetrag nicht ausreichen“
    - Zusätzliche Einkommensdokumentation anfordern
    - Meldung anzeigen: „Zusätzliche Dokumentation kann erforderlich sein“
    - Wenn @annualIncome größer als 100000:
    - Optionen für Premium-Services anzeigen
    - Checkbox für die Prioritätsverarbeitung aktivieren
    
    **Altersbasierte Validierung:**
    - Wenn @age unter 18:
    - Informationen für Eltern/Erziehungsberechtigten anzeigen
    - Übergeordnetes Hochladen obligatorisch machen
    - Schaltflächentnehmen-Text zu „Zur Überprüfung übermitteln“
    &quot;- Wenn @age 65 oder älter:
    - Senior-Rabattoptionen anzeigen
    - Abschnitt „Voreinstellungen für Barrierefreiheit hinzufügen“

**Regelspezifische Prompts:**

    Erstellen Sie eine **Sichtbarkeitsregel** die @spouseInformation Bedienfeld nur dann anzeigt, wenn @maritalStatus gleich „Verheiratet“ oder „Inländische Partnerschaft“
    
    Hinzufügen **progressive Offenlegung** ist, wenn zusätzliche Fragen basierend auf früheren Antworten angezeigt werden. Beginnen Sie mit den grundlegenden Informationen und zeigen Sie dann relevante 
    
     an **Smart Defaults** in denen @country Auswahl automatisch verwandte Felder festlegt. Manuelles Überschreiben zulassen

## Datenintegration und -übertragung

**Verwendung:** Wenn Sie Formulare mit Backend-Systemen, Datenbanken oder externen Services verbinden müssen.

**Verwendung:** Beginnen Sie mit der grundlegenden Einrichtung der Übermittlung und fügen Sie dann schrittweise zusätzliche Integrationen hinzu. Geben Sie den Integrationstyp, die Datenformatanforderungen und die Voreinstellungen für die Fehlerbehandlung an.

**Beispiel-Prompt – Beginn mit einfacher Übermittlung:**

    Konfigurieren der einfachen Formularübermittlung für @applicationForm:
    
    **Primäre Übermittlung:**
    - Senden von Formulardaten an REST-Endpunkt: &quot;/api/v1/applications“
    - Formatieren von Daten als JSON
    - Erfolgsmeldung anzeigen: „Anwendung erfolgreich gesendet“
    - Fehlermeldung anzeigen, wenn die Übermittlung fehlschlägt: „Übermittlung fehlgeschlagen, bitte erneut versuchen“

**Fügen Sie dann schrittweise sekundäre Aktionen hinzu:**

    E-Mail-Benachrichtigung zu @applicationForm hinzufügen: Bestätigungs-E-Mail an @email Adresse mit Anwendungs-Referenznummer senden
    
    CRM-Integration zu @applicationForm hinzufügen: Neuen Lead-Datensatz mit @firstName, @lastName, @email erstellen und Status auf „Neue Anwendung“ setzen

**Beispiel-Prompt – Standardmäßige Multi-Channel-Übermittlung:**

**     Formularübermittlung mit mehreren Datenzielen konfigurieren:
    
    **Primäre Übermittlung:**
    - Formulardaten an REST-Endpunkt senden: &quot;/api/v1/Applications“
    - Authentifizierungs-Header mit API-Schlüssel einschließen
    - Daten als JSON mit verschachtelten Objekten für Adresse und Beschäftigung formatieren
    - Erfolgsantwort verarbeiten (201) durch Anzeige der Dankesmeldung verarbeiten
    
    **Sekundäre Aktionen:**
    - Benachrichtigungs-E-Mail an Antragsteller unter @email senden
    - Anwendungsdaten in Tracking-System kopieren
    - Trigger-Workflow für Genehmigungsprozess
    - Datensatz im CRM erstellen mit Lead-Status „Neue Anwendung 
    
    &quot;
    &quot;
    -Fehlerbehandlung:-Wenn Die primäre Übermittlung schlägt fehl, Daten werden lokal gespeichert und erneut versucht
    - Benutzerfreundliche Fehlermeldung anzeigen: „Übermittlung vorübergehend nicht verfügbar“
    - Option zum Herunterladen von Formulardaten als Sicherung angeben
    
    - Warnhinweis-E-Mail an Admin-Team über fehlgeschlagene Übermittlung senden
    **Erfolgsfluss:**
    - Zur Bestätigungsseite mit Anwendungs-Referenznummer umleiten
    - Bestätigungs-E-Mail mit den nächsten Schritten senden
- Geschätzte Verarbeitungszeitleiste anzeigen
**Integrationsspezifische Prompts:**

    Verbinden Sie dieses Formular mit dem **CRM-System**, um neue Leads zu erstellen. Ordnen Sie beim Senden des Formulars @firstName FirstName, @email E-Mail zu, legen Sie LeadSource auf „Web-Formular“ und Status 
    
    Neu“ fest **Workflow-Trigger **. Alle Formulardaten und den Workflow für die Trigger-Genehmigung mit Manager-Benachrichtigung 
    
    **Datenbankintegration** übergeben, um Formularübermittlungen als Datensätze zu speichern Erstellen Sie für jede Übermittlung mit hochgeladenen Dokumenten einen neuen Ordner



## Befehlsreferenz

### Wichtige Befehle

| Befehl | Bester Anwendungsfall | Beispiel |
|---------|---------------|---------|
| `/create-form` | Starten neuer Formulare | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Hinzufügen von Formularen zu Seiten | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | Änderung der Formularstruktur | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Ändern von Feldeigenschaften | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Hinzufügen von dynamischem Verhalten | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Organisieren von Formularabschnitten | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Konvertieren von Designs | `/add-panel from uploaded form image with field recognition` |
| `/help` | Hilfe erhalten | `/help how to implement multi-step validation?` |

### Feldverweise

Verwenden Sie die `@fieldName`-Syntax, um in Ihren Prompts auf vorhandene Felder zu verweisen:

- `@email`: Verweis auf Feld „E-Mail“
- `@firstName`: Verweis auf Feld „Vorname“
- `@maritalStatus`: Verweis auf Feld „Familienstand“

### Komponententypen

**Eingabekomponenten:**

- `text`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `dropdown`, `file`, `textarea`

**Container-Komponenten:**

- `fieldset`, `panel`, `repeatable`, `wizard`

### Komponenteneigenschaften

**Universelle Eigenschaften (alle Komponenten):**

- **Typ**: Komponententyp
- **Name**: Feldkennung für die Formularübermittlung
- **Label**: Zeigt Text für das Feld an
- **Beschreibung**: Hilfetext für das Feld
- **Sichtbar**: Boolescher Wert für anfängliche Sichtbarkeit
- **Obligatorisch**: Boolescher Wert für erforderliche Felder

**Eingabefeldeigenschaften:**

- **Wert**: Standard-/Anfangswert
- **Platzhalter**: Hinweistext für Eingabefelder
- **Min**: Mindestwert (für Zahlen/Datumsangaben)
- **Max**: Höchstwert (für Zahlen/Datumsangaben)

**Datei-Upload-Eigenschaften:**

- **Akzeptieren**: Dateitypen (.pdf, .doc, .docx, .jpg, .png usw.)
- **Mehrere**: Boolescher Wert für die Auswahl mehrerer Dateien

**Eigenschaften von Auswahlsteuerelementen:**

- **Optionen**: Optionen für Dropdown-Listen (durch Kommas getrennte Liste)
- **Aktiviert**: Standardauswahl für Kontrollkästchen/Optionsfelder

**Container-Eigenschaften:**

- **Feldsatz**: Gruppieren verwandter Felder
- **Wiederholbar**: Boolescher Wert für wiederholbare Abschnitte

**Erweiterte Eigenschaften:**

- **Sichtbarer Ausdruck**: Formel für bedingte Sichtbarkeit (=Formel)
- **Wertausdruck**: Formel für berechnete Werte (=Formel)

### Integrationsbefehle

**Übermittlungsaktionen:**

- E-Mail-Benachrichtigungen
- REST-API-Übermittlungen
- Cloud-Speicher (Azure, SharePoint)
- Workflow-Automatisierung (Power Automate, Workfront Fusion)
- Marketing-Plattformen (Marketo)
- CRM-Integrationen

### Richtlinien zur Prompt-Syntax

- **Feldverweise**: Verwenden Sie `@fieldName` für vorhandene Felder
- **Befehle**: Verwenden Sie `/command` für spezifische Aktionen
- **Natürliche Sprache**: Beschreiben Sie Anforderungen eindeutig und spezifisch

### Validierungs-Checkliste

Umfassende Best Practices und Validierungsrichtlinien finden Sie im Handbuch [Forms Experience Builder – Erste Schritte](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

*Diese Prompt-Bibliothek wird auf Basis von Benutzer-Feedback und neuen Forms Experience Builder-Funktionen fortlaufend aktualisiert. Die neuesten Funktionen und Beispiele finden Sie in der [Dokumentation zu AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html\lang=de).*
