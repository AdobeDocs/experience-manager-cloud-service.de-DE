---
title: Forms Experience Builder - Prompt-Bibliothek
description: Sammlung bewährter Prompt-Muster und Beispiele zum Erstellen von Formularen mit KI-Unterstützung in der Benutzeroberfläche für die Formularverwaltung, im Editor für adaptive Formulare und im universellen Editor.
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: 48eb137c-fe12-4e4f-b845-3321ca8b6075
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 99%

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

- **Markenvorlagen**: Bereiten Sie standardisierte Formularvorlagen mit Farben, Schriften und Layout-Mustern Ihrer Organisation vor
- **Stilrichtlinien**: Definieren Sie konsistente Feldstile, Schaltflächen-Designs und Abstandsstandards, die Forms Experience Builder anwenden kann
- **Komponentenbibliothek**: Arbeiten Sie mit Ihrem Entwicklungs-Team zusammen, um wiederverwendbare Formularkomponenten vorzubereiten, die Ihrer Markenidentität entsprechen
- **Grafik-Assets**: Bereiten Sie Logos, Symbole und Hintergrundelemente für die Formularintegration vor


## Beispiele für inkrementelle Entwicklung

Diese Beispiele zeigen, wie Sie Formulare Schritt für Schritt erstellen, indem Sie einfach anfangen und schrittweise Komplexität hinzufügen:

### Beispiel 1: Inkrementelles Erstellen eines Kontaktformulars

**Schritt 1 – Einfach starten:**

    Erstelle ein simples Kontaktformular mit Feldern für Name, E-Mail, Telefon und Nachricht

**Schritt 2 – Validierung hinzufügen:**

    Erstelle die Pflichtfelder @name und @email mit entsprechender Validierung

**Schritt 3 – Benutzererlebnis verbessern:**

    Füge Platzhaltertext hinzu: @name „Ihr vollständiger Name“, @email „your.email@company.com“, @message „Wie können wir Ihnen helfen?“

**Schritt 4 – Erweiterte Funktionen hinzufügen:**

    Füge einen Dropdown-inquireType mit Optionen hinzu: „Allgemeine Frage“, „Support-Anfrage“, „Vertriebsanfrage“, „Partnerschaft“

**Schritt 5 – Eine bedingte Logik implementieren:**

    /create-rule Zeige Dropdown-Liste @urgencyLevel („Niedrig“, „Mittel“, „Hoch“) nur an, wenn @inquiryType gleich „Support-Anfrage“ ist

### Beispiel 2: Inkrementelles Erstellen eines Registrierungsformulars

**Schritt 1 – Grundstruktur:**

    Erstelle ein Formular zur Benutzerregistrierung mit Panel für personenbezogene Daten

**Schritt 2 – Kernfelder hinzufügen:**

    Füge Felder für @firstName, @lastName, @email und @phoneNumber mit entsprechender Validierung hinzu

**Schritt 3 – Business-Logik hinzufügen:**

    Erstelle eine Regel: Wenn @age jünger als 18 Jahre ist, zeige einen Abschnitt mit Informationen zu Eltern/Erziehungsberechtigten an

**Schritt 4 – Mit Voreinstellungen verbessern:**

    Füge ein Panel mit Voreinstellungen mit „@newsletterSubscription“, „@marketingConsent“, „@termsAccepted“ hinzu

**Schritt 5 - Datei-Upload hinzufügen:**

    Füge ein Feld zum Datei-Upload für @profilePicture mit einer Größenbeschränkung von 5 MB hinzu

## Formularerstellung und -verwaltung

**Anwendungsfall:** Sie müssen neue Formulare erstellen oder vorhandene ändern.

**Verwendung:** Wählen Sie einen von zwei Ansätzen: von Grund auf neu erstellen oder Importieren und Konvertieren (siehe [Erste Schritte](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

**Beispiel-Prompt – Einfaches Formular erstellen:**

    Erstelle ein Formular für Kunden-Feedback mit:
    – Produktbewertung (1–5 Sterne)
    – Kommentarfeld für detailliertes Feedback
    – Kunden-E-Mail (optional)
    – An E-Mail-Benachrichtigung übermitteln

**Beispiel-Prompt – Komplexes Formular erstellen:**

    Erstelle ein umfassendes Onboarding-Formular für Mitarbeitende mit:
    
    **Abschnitt für personenbezogene Informationen:**
    – Vollständiger Name (Vor-, Zweit-, Nachname)
    – Geburtsdatum mit Altersvalidierung
    – Kontaktinformationen (E-Mail, Telefon, Adresse)
    – Kontaktinformationen für Notfälle
    
    **Beschäftigungsdetails:**
    – Auswahl von Stelle und Abteilung
    – Startdatum mit der Validierung des Geschäftstags
    – Gehaltsinformationen mit Vertraulichkeitshinweis
    – Berichtsstruktur
    
    **Dokument-Upload:**
    – Lebenslauf (PDF, DOC, DOCX)
    – Ausweisbestätigungsdokumente
    – Steuerformulare und Bankinformationen
    – Unterzeichneter Arbeitsvertrag
    
    **Voreinstellungen:**
    – Leistungsauswahl mit Kostenrechner
    – Voreinstellungen für den Arbeitsplan
    – Schulungsanforderungen
    – Ausrüstungsanforderungen
    
    **Validierungsregeln:**
    – Validierung des E-Mail-Formats
    – Validierung des Telefonnummernformats
    – Alter muss 18 oder älter sein
    – Alle erforderlichen Dokumente müssen hochgeladen werden
    – Bedingungen müssen akzeptiert werden
    
    **Übermittlungsaktionen:**
    – Bestätigungs-E-Mail an neue Mitarbeitende senden
    – Personalabteilung benachrichtigen
    – Mitarbeitereintrag im Personalabteilungssystem erstellen
    – Einweisungsbesprechung ansetzen

**Prompts zur Formularverwaltung:**

    Importiere dieses PDF-Antragsformular und konvertiere es in ein adaptives Formular mit erweiterter Validierung
    
    Aktualisiere das bestehende Kontaktformular und füge Social-Media-Namen und bevorzugte Kontaktmethode hinzu
    
    Strukturiere das Registrierungsformular als 3-stufigen Assistenten neu: personenbezogene Informationen, Voreinstellungen, Bestätigung

## Feldverwaltung und -konfiguration

**Anwendungsfall:** Sie müssen Formularfelder hinzufügen, ändern oder konfigurieren.

**Verwendung:** Seien Sie präzise in Bezug auf Feldtypen, Validierungsregeln und Anforderungen an das Benutzererlebnis.

**Beispiel-Prompt - Einfaches Feld hinzufügen:**

    Füge ein Texteingabefeld für „Firmenname“ mit dem Platzhalter „Geben Sie Ihren Firmennamen ein“ hinzu

**Beispiel-Prompt – Erweiterte Feldkonfiguration:**

    Füge einen umfassenden Adressabschnitt mit Folgendem hinzu:
    
    **Adresse:**
    – Adresszeile 1 (erforderlich, max. 100 Zeichen)
    – Adresszeile 2 (optional, max. 100 Zeichen)
    – Stadt (erforderlich, Dropdown-Liste mit bekannten Städten)
    – Region/Provinz (erforderlich, Dropdown-Liste)
    – Postleitzahl (erforderlich, Formatvalidierung)
    – Land (erforderlich, Standard „Vereinigte Staaten“)
    
    **Validierungsregeln:**
    – Postleitzahl muss mit der Auswahl von Region/Provinz übereinstimmen
    – Adresszeile 1 darf nicht leer sein
    – Stadt muss eine gültige Stadt für die ausgewählte Region sein
    
    **Benutzererlebnis:**
    – Automatische Vervollständigung für Adressfelder
    – Entfernen von Labels und Hilfetext
    – Eingabefelder, die auch auf Mobilgeräten funktionieren
    – Einhaltung der Barrierefreiheit

**Prompts zur Feldkonfiguration:**

    Lege fest, dass Feld @email mit Echtzeitvalidierung und benutzerdefinierter Fehlermeldung erforderlich ist
    
    Füge eine Dropdown-Liste für @country mit Optionen für die USA, Kanada, Großbritannien, Deutschland, Frankreich und „Sonstige“ hinzu
    
    Konfiguriere das Feld @phoneNumber mit Format (XXX) XXX-XXXX und Validierung
    
    Füge ein Feld für den Datei-Upload für @resume mit PDF- und DOC-Einschränkungen hinzu, max. 5 MB

## LLM-optimierte intelligente Felder

**Anwendungsfall:** Sie benötigen Felder mit vorausgefüllten Optionen, die die Wissensdatenbank der KI nutzen.

**Verwendung:** Fordern Sie Felder an, für die umfassende Datensätze erforderlich sind. Die KI kann Optionen dank des integrierten Wissens automatisch ausfüllen.

### Geografische Felder und Standortfelder

**Flughäfen und Verkehr:**

    Füge eine Dropdown-Liste für Abflughäfen mit allen wichtigen internationalen Flughäfen hinzu
    Füge ein Feld für Ankunftsflughäfen mit IATA-Codes und vollständigen Namen hinzu
    Erstelle ein Feld für den nächstgelegenen Flughafen zum Benutzerstandort
    Füge eine Auswahl an Bahnhöfen europäischer Städte hinzu

**Verwaltungsregionen:**

    Füge eine vollständige Liste der US-Bundesstaaten mit Abkürzungen hinzu
    Erstelle eine Dropdown-Liste mit ISO-Codes und vollständigen Namen
    Füge ein Feld für die größten Städte der Welt mit Zeitzonen hinzu
    Füge eine Dropdown-Liste der kanadischen Provinzen und Territorien hinzu
    Füge ein Feld für britische Countys und Postgebiete hinzu

### Unternehmens- und Branchendaten

**Unternehmensklassifizierungen:**

    Füge ein Feld für die Branchenklassifizierung mit NAICS-Codes hinzu
    Erstelle eine Dropdown-Liste der Typen von Geschäftseinheiten (LLC, Corporation, Partnerschaft usw.)
    Füge ein Feld für Unternehmensgrößenkategorien hinzu (Startup, KMU, Unternehmen)
    Füge eine Abteilungsauswahl für große Organisationen hinzu
    Füge ein Feld für Typen professioneller Dienstleistungen hinzu

**Berufsklassifizierungen:**

    Füge ein Feld für Stellenbezeichnungen mit üblichen Branchenrollen hinzu
    Erstelle eine Dropdown-Liste mit professionellen Zertifizierungen nach Feld
    Füge Ausbildungsstufen mit Abschlussarten hinzu
    Füge ein Feld für Zeitbereiche für Erfahrung hinzu
    Erstelle eine Auswahl für Programmiersprachen und Frameworks

### Normen und Vorschriften

**Finanz- und Rechtsfragen:**

    Füge ein Feld für Währungs-Codes mit Symbolen und Wechselkursen hinzu
    Erstelle eine Dropdown-Liste mit Steuer-ID-Typen nach Land
    Füge ein Feld für Typen rechtlicher Dokumente hinzu
    Füge Optionen für Zahlungsmethoden mit Sicherheitsmerkmalen hinzu
    Erstelle eine Auswahl für Bankinstitute nach Land

**Technische Standards:**

    Füge eine Dropdown-Liste mit Dateitypen mit Erweiterungen hinzu
    Füge Optionen für Netzwerkprotokolle hinzu
    Füge ein Feld für Datenbanktypen und -versionen hinzu
    Erstelle eine Auswahl für API-Authentifizierungsmethoden

### Gesundheitswesen und Medizin

**Medizinische Klassifizierungen:**

    Füge ein Feld für medizinische Fachgebiete hinzu
    Erstelle eine Dropdown-Liste mit gängigen Medikamenten mit generischen Namen
    Füge ein Feld für Versicherungsanbietertypen hinzu
    Füge eine Auswahl für Kontakte bei medizinischen Notfällen hinzu
    Erstelle ein Feld für Ernährungseinschränkungen und Allergien

### Zeit- und Kalenderintelligenz

**Datums- und Uhrzeitfelder:**

    Füge ein Feld für Geschäftszeiten mit Zeitzonenverarbeitung hinzu
    Erstelle eine Dropdown-Liste mit Feiertagen nach Land
    Füge saisonale Optionen mit Datumsbereichen hinzu
    Füge ein Feld für die Buchung von Konferenzräumen mit Verfügbarkeit hinzu
    Erstelle eine Auswahl für Muster wiederkehrender Besprechungen

### Produkt- und Service-Kategorien

**E-Commerce-Klassifizierungen:**

    Füge ein Feld für Produktkategorien mit Unterkategorien hinzu
    Erstelle eine Dropdown-Liste mit Versandmethoden mit Versandschätzungen
    Füge ein Feld für Optionen für Rückgaberichtlinien hinzu
    Füge eine Auswahl für Kundenprioritätsstufen hinzu
    Erstelle ein Feld für Abonnement-Abrechnungszyklen

**Beispiel-Prompts für intelligente Felder:**

    „Füge ein Feld für Abflughäfen mit allen wichtigen Flughäfen weltweit mit IATA-Codes und Städtenamen hinzu“
    
    „Erstelle ein Feld mit eine umfassenden Auswahl an Branchen mit der standardmäßigen NAICS-Klassifizierung mit Technologie-Unterkategorien“
    
    „Füge eine Dropdown-List für professionelle Zertifizierungen ein, das sich auf der Grundlage des ausgewählten Arbeitsfelds anpasst“
    
    „Füge ein Feld für internationale Telefonnummern hinzu, das Formate auf der Grundlage des ausgewählten Landes festlegt“
    
    „Erstelle ein Auswahlfeld für Universitäten mit wichtigen Institutionen, die nach Land und Rangfolge organisiert sind“

## Regelerstellung und Geschäftslogik

**Anwendungsfall:** Sie müssen bedingte Logik, Validierungsregeln oder Geschäftsprozesse implementieren.

**Verwendung:** Beschreiben Sie die Geschäftslogik klar und geben Sie Bedingungen und Aktionen an.

**Beispiel-Prompt – Einfache bedingte Logik:**

    Erstelle eine Regel, die das Panel „@spouseInformation“ nur anzeigt, wenn „@maritalStatus“ gleich „verheiratet“ ist

**Beispiel-Prompt – Komplexe Geschäftsregeln:**

    Implementiere eine umfassende Prüfung des Kreditantrags:
    
    **Einkommensprüfung:**
    – Wenn @annualIncome kleiner als 30.000 ist:
    – Zeige folgende Warnmeldung an: „Das Einkommen ist für den angeforderten Kreditbetrag möglicherweise nicht ausreichend“
    – Fordere zusätzliche Einkommensdokumentation an
    – Zeige folgende Meldung an: „Zusätzliche Dokumentation ist möglicherweise erforderlich“
    – Wenn @annualIncome größer als 100.000 ist:
    – Zeige Optionen für Premium-Services an
    – Aktiviere das Kontrollkästchen für die Prioritätsverarbeitung
    
    **Altersbasierte Validierung:**
    – Wenn @age unter 18 ist:
    – Zeige Informationen für Eltern/Erziehungsberechtigten an
    – Mache Hochladen der Signatur von Elternteil obligatorisch
    – Ändere Text der Schaltfläche zum Übermittlung zu „Zur Überprüfung übermitteln“
    – Wenn @age 65 oder älter:
    – Zeige Rabattoptionen für Senioren an
    – Füge Abschnitt mit Voreinstellungen für Barrierefreiheit hinzu

**Regelspezifische Prompts:**

    Erstelle eine **Sichtbarkeitsregel** die das Panel @spouseInformation nur dann anzeigt, wenn @maritalStatus gleich „Verheiratet“ oder „Eingetragene Partnerschaft“ ist
    
    Füge **progressive Offenlegung** hinzu, wobei zusätzliche Fragen basierend auf früheren Antworten angezeigt werden. Beginne mit den grundlegenden Informationen und zeige dann relevante Folgeinformationen an
    
    Implementiere **intelligente Standardwerte**, wobei die Auswahl von @country automatisch verknüpfte Felder befüllt. Lasse manuelles Überschreiben zu

## Datenintegration und -übertragung

**Verwendung:** Wenn Sie Formulare mit Backend-Systemen, Datenbanken oder externen Services verbinden müssen.

**Verwendung:** Beginnen Sie mit der grundlegenden Einrichtung der Übermittlung und fügen Sie dann schrittweise zusätzliche Integrationen hinzu. Geben Sie den Integrationstyp, die Datenformatanforderungen und die Voreinstellungen für die Fehlerbehandlung an.

**Beispiel-Prompt – Beginn mit einfacher Übermittlung:**

    Konfiguriere einfache Formularübermittlung für @applicationForm:
    
    **Primäre Übermittlung:**
    – Sende Formulardaten an REST-Endpunkt: „/api/v1/applications“
    – Formatiere Daten als JSON
    – Zeige Erfolgsmeldung an: „Antrag erfolgreich übermittelt“
    – Zeige Fehlermeldung an, wenn die Übermittlung fehlschlägt: „Übermittlung fehlgeschlagen, bitte erneut versuchen“

**Fügen Sie dann schrittweise sekundäre Aktionen hinzu:**

    Füge E-Mail-Benachrichtigung zu @applicationForm hinzu: Sende Bestätigungs-E-Mail an @email-Adresse mit Antragsreferenznummer
    
    Füge CRM-Integration zu @applicationForm hinzu: Erstelle neuen Lead-Datensatz mit @firstName, @lastName, @email und lege den Status auf „Neuer Antrag“ fest

**Beispiel-Prompt – standardmäßige Multi-Channel-Übermittlung:**

    Konfiguriere Formularübermittlungen mit mehreren Datenzielen:
    
    **Primäre Übermittlung:**
    – Sende Formulardaten zu REST-Endpunkt hinzu: „/api/v1/applications“
    – Füge Authentifizierungs-Header mit API-Schlüssel hinzu
    – Formatiere Daten als JSON mit verschachtelten Objekten für Adresse und Arbeit
    – Verarbeite die Erfolgsantwort (201) durch Anzeigen einer Dankesnachricht
    
    **Sekundäre Aktionen:**
    – Sende Benachrichtigungs-E-Mail an die @email-Adresse der antragstellenden Person
    – Kopiere Antragsdaten in Tracking-System
    – Löse Workflow für Genehmigungsprozess aus
    – Erstelle Eintrag in CRM mit Lead-Status „Neuer Antrag“
    
    **Fehlerbehebung:**
    – Wenn primäre Übermittlung fehlschlägt, speichere Daten lokal und versuche es erneut
    – Zeige benutzerfreundliche Fehlermeldung an: „Übermittlung vorübergehend nicht verfügbar“
    – Stelle Option zum Herunterladen von Formulardaten als Backup zur Verfügung
    – Sende Warn-E-Mail über fehlgeschlagene Übermittlung an Admin-Team
    
    **Erfolgreicher Ablauf:**
    – Leite an Bestätigungsseite mit Antragsreferenznummer weiter
    – Sende Bestätigungs-E-Mail mit weiteren Schritten
    – Zeige die geschätzte Verarbeitungszeit an

**Integrationsspezifische Prompts:**

    Verbinde dieses Formular mit dem **CRM-System**, um neue Leads zu erstellen. Ordne @firstName dem Vornamen und @email der E-Mail-Adresse zu, lege LeadSource auf „Web-Formular“ und Status auf „Neu“ fest
    
    Richte einen **Workflow-Trigger &#x200B;** beim Übermitteln des Formulars ein. Übergib alle Formulardaten und löse den Genehmigungs-Workflow für die Manager-Benachrichtigung aus
    
    Konfiguriere die **Datenbankintegration**, um Formularübermittlungen als Einträge zu speichern. Erstelle für jede Übermittlung mit hochgeladenen Dokumenten einen neuen Ordner



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
