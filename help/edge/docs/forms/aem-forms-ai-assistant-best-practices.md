---
title: Forms Experience Builder - Best Practices
description: Umfassende Best Practices für die Erstellung effektiver Formulare mit Forms Experience Builder, einschließlich Design, Anwendererlebnis, Leistung und Markenkonsistenz.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2072'
ht-degree: 0%

---


# Forms Experience Builder - Best Practices

>[!NOTE]
>
> Der Forms Experience Builder ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie eine E-Mail von Ihrer Geschäftsadresse an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Dieses Handbuch mit Best Practices wird derzeit für das Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Best Practices, Empfehlungen und Beispiele können sich ändern, wenn Forms Experience Builder während des Early-Adopter-Programms weiterentwickelt wird.

Dieses umfassende Handbuch enthält bewährte Best Practices für die Erstellung effektiver, benutzerfreundlicher Formulare mit Forms Experience Builder. Diese Best Practices stammen aus erfolgreichen Implementierungen und Benutzer-Feedback aus verschiedenen Branchen und Anwendungsfällen.

## Best Practices für den Formularentwurf

### Einfach halten

**Beginnen Sie mit den grundlegenden Feldern**

- Beginnen Sie nur mit den wichtigsten Informationen, um die Benutzerüberlastung zu reduzieren.
- Je nach Benutzeranforderungen und Geschäftsanforderungen schrittweise komplexer gestalten
- Vermeiden Sie es, nach Informationen zu fragen, die Sie eigentlich gar nicht benötigen oder verwenden
- Berücksichtigen Sie beim Entwerfen von Formularen die Zeit und die kognitive Belastung des Benutzers

**Verwenden Sie klare, beschreibende Beschriftungen**

- Machen Sie die Feldzwecke mit beschreibenden Beschriftungen sofort offensichtlich
- Vermeiden Sie technischen Jargon oder interne Terminologie, die von Benutzern nicht verstanden wird.
- Verwenden von einheitlichen Beschriftungskonventionen in Ihren Formularen
- Kontext bereitstellen, wenn die Feldanforderungen möglicherweise nicht offensichtlich sind

**Hilfreiche Anleitungen geben**

- Hilfetext für komplexe Felder mit Beispielen und Formatierungsanforderungen einschließen
- Platzhaltertext zur Anzeige der erwarteten Eingabeformate verwenden
- Klare Anweisungen zum Hochladen von Dateien, einschließlich akzeptierter Formate und Größenbeschränkungen
- Führen Sie Benutzer durch mehrstufige Prozesse mit Fortschrittsanzeigen

**Gründlich testen**

- Validieren aller Benutzerpfade und Szenarien vor der Bereitstellung
- Testen von Formularen mit echten Benutzern aus Ihrer Zielgruppe
- Überprüfen, ob alle bedingten Logiken erwartungsgemäß funktionieren
- Sicherstellen, dass die Fehlerbehandlung für klares, umsetzbares Feedback sorgt

### progressive Offenlegung

**Anzeigen relevanter Felder basierend auf dem Kontext**

- Zusätzliche Felder nur anzeigen, wenn sie für die Benutzerauswahl relevant werden
- Verwenden der bedingten Logik zur Verringerung der kognitiven Belastung und der Formularlänge
- Gruppieren verwandter Felder in logischen Abschnitten
- Erweiterte Optionen ausblenden, bis Benutzer angeben, dass sie sie benötigen

**Beispielimplementierung:**

    Erstellen Sie eine Regel, die @spouseInformation Bedienfeld nur anzeigt, wenn @maritalStatus gleich „Verheiratet“

**Navigation und Fortschritt löschen**

- Helfen Sie Benutzern zu verstehen, wo sie sich in mehrstufigen Formularen befinden
- Klare Navigation zwischen Formularabschnitten ermöglichen
- Fortschrittsanzeigen für längere Formulare
- Benutzern erlauben, den Fortschritt zu speichern und später zurückzukehren

## Best Practices für das Benutzererlebnis

### Mobile-First-Design

**Responsive Layout-Optimierung**

- Erstellen von Formularen mit mobilen Benutzern als primäre Überlegung
- Verwenden von einspaltigen Layouts für Mobilgeräte
- Stellen Sie sicher, dass Touch-Ziele eine angemessene Größe aufweisen (mindestens 44 Pixel).
- Testformulare in verschiedenen Gerätegrößen und -ausrichtungen

**Touch-optimierte Interaktionen**

- Implementieren größerer Schaltflächen und Eingabefelder für Touch-Oberflächen
- Verwenden Sie geeignete Eingabetypen, um Trigger-Tastaturen zu korrigieren
- Vermeiden von Hover-abhängigen Interaktionen, die auf Touch-Geräten nicht funktionieren
- Klare visuelle Rückmeldung für Benutzerinteraktionen

### Einhaltung der Barrierefreiheitsanforderungen

**WCAG 2.1-Richtlinien**

- Befolgen der Richtlinien für barrierefreien Webinhalt für inklusives Design
- Sicherstellen von angemessenen Farbkontrastverhältnissen (mindestens 4,5 % :1 normalem Text)
- Alternativtext für alle Bilder und Symbole angeben
- Implementieren der korrekten Überschriftenstruktur und semantischen HTML

**Tastaturnavigation**

- Sicherstellen, dass der Zugriff auf alle Formularelemente über die Tastaturnavigation erfolgt
- Bereitstellung klarer Fokusindikatoren für alle interaktiven Elemente
- Implementieren der logischen Registerkartenreihenfolge durch Formularfelder
- Überspringen von Navigations-Links für komplexe Formulare einschließen

**Screen Reader Support**

- Verwenden der richtigen ARIA-Bezeichnungen und -Beschreibungen für Formularfelder
- Bereitstellung klarer Fehlermeldungen, die an Bildschirmlesehilfen ausgegeben werden
- Sicherstellen, dass dynamische Inhaltsänderungen ordnungsgemäß angekündigt werden
- Testen von Formularen mit aktueller Bildschirmlesehilfe-Software

### Leistungsoptimierung

**Ladegeschwindigkeit**

- Optimieren der Ladezeiten von Formularen durch Minimieren der anfänglichen Paketgröße
- Implementieren von verzögertem Laden für nicht kritische Formularabschnitte
- Optimieren von Bildern und Assets für die Web-Bereitstellung
- Aktivieren geeigneter Caching-Strategien für statische Ressourcen

**Laufzeitleistung**

- Verwenden Sie einen geeigneten Validierungszeitpunkt, um Benutzererlebnis und Leistung aufeinander abzustimmen.
- Implementieren des Bounces für die Echtzeit-Validierung, um Server-Anfragen zu reduzieren
- Häufig aufgerufene Daten und Validierungsergebnisse zwischenspeichern
- Optimieren der Ausführung von bedingten Logiken für komplexe Formulare

**Automatisches Speichern und Datenschutz**

- Automatisches Speichern des Formularfortschritts implementieren, um Datenverlust zu vermeiden
- Bieten Sie nach Möglichkeit Offline-Funktionen für das Ausfüllen des Formulars.
- Wiederholungslogik für fehlgeschlagene Übermittlungen einschließen
- Datenexportoptionen als Backup für Benutzer anbieten

## Best Practices für die Markenkonsistenz

### Vorbereiten von Brand Assets

**Erstellen von Markenvorlagen**

- Entwicklung standardisierter Formularvorlagen mit der visuellen Identität Ihres Unternehmens
- Konsistente Farbschemata, Typografie und Layout-Muster einschließen
- Vorbereiten wiederverwendbarer Komponenten, die Ihren Markenrichtlinien entsprechen
- Dokumentenstilstandards für eine konsistente Implementierung in allen Teams

**Definieren von Stilrichtlinien**

- Konsistente Feldstile, Schaltflächenentwürfe und Abstandsstandards
- Erstellen Sie ein Stil-Handbuch, das Farb-Codes, Schriftspezifikationen und Layout-Regeln enthält
- Definieren von Interaktionsmustern und Animationsrichtlinien
- Vorbereiten markenspezifischer Fehlermeldungen und Hilfetexte

**Komponentenbibliothek erstellen**

- Erstellen Sie wiederverwendbare Formularkomponenten, die Ihrer Markenidentität entsprechen
- Konsistente Navigationsmuster und Elemente der Benutzeroberfläche entwickeln
- Vorbereiten von Markensymbolen, Logos und visuellen Assets für die Formularintegration
- Erstellen von Vorlagen für allgemeine Formulartypen (Kontakt, Registrierung, Feedback)

### Strategien zur Markenimplementierung

**Stil fordert zur Konsistenz auf**

Fügen Sie in Ihre Eingabeaufforderungen markenspezifische Anweisungen ein:

    Erstellen Sie ein professionelles Kontaktformular mit:
    - Unternehmensblau (#003366) für primäre Schaltflächen und Kopfzeilen
    - Offene Sans-Schriftfamilie für alle Textelemente
    - Mindestschriftgröße von 16 Pixel für Barrierefreiheit
    - Konsistenter 24-Pixel-Abstand zwischen Formularabschnitten
    - Firmenlogo in der Kopfzeile mit korrekter Markenpositionierung

**Vorlagenbibliotheksverwaltung**

- Pflegen einer Sammlung von Formularvorlagen mit Branding für gängige Anwendungsfälle
- Versionskontrolle Ihrer Markenvorlagen zur Sicherstellung der Konsistenz
- Bereitstellung einer klaren Dokumentation zur Verwendung und Anpassung von Vorlagen
- Regelmäßige Überprüfung und Aktualisierung der Marken-Assets zur Einhaltung aktueller Standards

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Koordinieren Sie sich mit Ihrem Entwicklungs-Team, um organisationsspezifische Komponenten und deren Kompatibilität mit Forms Experience Builder zu verwenden, bevor Sie benutzerdefinierte Markenelemente implementieren.

## Best Practices für Inhalt und Kommunikation

### Ansätze der Formularerstellung

**Zwei Primäre Methoden**

Wählen Sie die für Ihre Anforderungen am besten geeignete Erstellungsmethode aus:

1. **Erstellen von Grund auf**: Optimiert für neue Formulare mit spezifischen Anforderungen
2. **Importieren und Konvertieren**: Ideal für die Modernisierung vorhandener Formulare und Dokumente

**Natürliche Spracheingabe**

- Seien Sie in Ihren Formularbeschreibungen spezifisch und detailliert
- Verwendung klarer, auf Geschäftsabläufe fokussierter Terminologie anstelle von technischen Begriffen
- Kontext über den Zweck und die Zielgruppe des Formulars bereitstellen
- Einschließen von Validierungs- und Geschäftsregelanforderungen in anfängliche Eingabeaufforderungen

### Inkrementelle Entwicklungsstrategie

**Einfach anfangen, Komplexität aufbauen**

- Beginnen Sie mit der grundlegenden Formularstruktur und den wesentlichen Feldern
- Inkrementelles Hinzufügen von Validierungsregeln und Geschäftslogik
- Testen Sie jede Ergänzung, bevor Sie mit der nächsten Verbesserung fortfahren.
- Sammeln von Benutzer-Feedback in jeder Entwicklungsphase

**Beispiel für inkrementellen Ansatz:**

    Schritt 1: „Erstellen eines einfachen Kontaktformulars mit Namen-, E-Mail- und Nachrichtenfeldern“
    Schritt 2: &quot;@name und @email Pflichtfelder mit entsprechender Validierung machen“
    Schritt 3: „Platzhaltertext und Hilfetext zur Benutzeranleitung hinzufügen“
    Schritt 4: „Bedingte Logik auf der Grundlage des Anfragetyps hinzufügen“

### Best Practices für Feldreferenzen

**Konsistente Benennungskonventionen**

- Verwenden Sie klare, beschreibende Feldnamen, die ihrem Zweck entsprechen.
- Beibehalten konsistenter Benennungsmuster in allen Formularen
- Verwenden Sie camelCase oder snake_case konsistent in Ihren Formularen.
- Benennungskonventionen für Dokumentfelder zur Gewährleistung der Team-Konsistenz

**Effektive Feldverweise**

- `@fieldName` beim Ändern vorhandener Felder verwenden
- Geben Sie an, auf welche Felder Sie in komplexen Formularen verweisen
- Gruppieren Sie verwandte Feldänderungen in einzelnen Anfragen.
- Feldnamen überprüfen, bevor sie in der bedingten Logik verwendet werden

## Best Practices für Integration und Übermittlung

### Multi-Channel-Übermittlungsstrategie

**Primäre und Sekundäre Aktionen**

- Konfigurieren von primären Übermittlungsendpunkten für zentrale Geschäftsprozesse
- Einrichten sekundärer Aktionen für Benachrichtigungen, Bestätigungen und Datensicherung
- Implementieren der Fehlerbehandlung und Wiederholungslogik für fehlgeschlagene Übermittlungen
- Geben Sie Benutzer-Feedback für alle Übermittlungsstatus (Erfolg, Fehler, Verarbeitung)

**Integrationsplanung**

- Beginnen Sie mit der grundlegenden Übermittlungskonfiguration und fügen Sie Integrationen schrittweise hinzu.
- Testen Sie jede Integration separat, bevor Sie mehrere Endpunkte kombinieren.
- Document API-Anforderungen und -Authentifizierungsmethoden
- Planen der Datenumwandlungs- und Zuordnungsanforderungen

### Fehlerbehandlung und Wiederherstellung

**Benutzerfreundliche Fehlermeldungen**

- Bereitstellung klarer, umsetzbarer Fehlermeldungen, die Benutzern beim Lösen von Problemen helfen
- Vermeiden Sie technische Fehlercodes oder Systemmeldungen in benutzerfreundlichen Inhalten
- Alternative Aktionen anbieten, wenn die primäre Übermittlung fehlschlägt
- Kontaktinformationen für Benutzer einschließen, die zusätzliche Hilfe benötigen

**Datenschutz und Wiederherstellung**

- Implementieren des lokalen Datenspeichers für die Formularwiederherstellung nach Fehlern
- Optionen für Benutzer bereitstellen, um ihre Formulardaten als Backup herunterzuladen
- Einrichten von Überwachung und Warnhinweisen für fehlgeschlagene Übermittlungen
- Planen von Wiederherstellungsverfahren bei Systemausfällen oder Wartungsarbeiten

## Best Practices für Leistung und Analyse

### Überwachung und Optimierung

**Wichtige Leistungsmetriken**

- Verfolgen der Formularabschlussraten und -abbruchpunkte
- Ladezeiten und Interaktionsmuster von Benutzern überwachen
- Messung der Validierungs-Effektivität und der Fehlerquoten
- Analysieren des Feedbacks und der Zufriedenheitswerte der Benutzer

**Kontinuierliche Verbesserung**

- Regelmäßige Überprüfung der Formularanalyse zur Ermittlung von Optimierungsmöglichkeiten
- A/B-Tests verschiedener Formularentwürfe und Benutzerabläufe
- Sammlung und Analyse von Benutzer-Feedback für iterative Verbesserungen
- Benchmarking der Leistung anhand von Branchenstandards

### Datenqualität und -validierung

**Intelligente Validierungsstrategien**

- Echtzeit-Validierung für sofortiges Benutzer-Feedback implementieren
- Verwenden der progressiven Validierung, um Benutzer durch komplexe Anforderungen zu führen
- Klare Validierungsmeldungen bereitstellen, die erklären, wie Fehler behoben werden
- Abwägen der Schärfe der Validierung mit Überlegungen zum Benutzererlebnis

**Datenintegrität**

- Implementieren von feldübergreifenden Validierungen für Datenkonsistenz
- Verwenden Sie geeignete Eingabetypen und Einschränkungen, um ungültige Daten zu verhindern
- Bereitstellung von Beispielen für Datenformate und Anleitungen für komplexe Felder
- Regelmäßige Prüfung der Qualität der übermittelten Daten und der Validierungswirksamkeit

## Best Practices für Sicherheit und Compliance

### Datenschutz

**Datenschutz per Design**

- Sammeln Sie nur die für Ihren Geschäftszweck erforderlichen Mindestdaten
- Implementieren geeigneter Richtlinien zur Datenaufbewahrung und Löschung
- Klare Datenschutzhinweise und Einverständnismechanismen bereitstellen
- Gewährleistung der Einhaltung relevanter Datenschutzbestimmungen (DSGVO, CCPA usw.)

**Sicherheitsimplementierung**

- HTTPS-Verschlüsselung für alle Formularübermittlungen und Datenübertragungen verwenden
- Implementieren einer ordnungsgemäßen Eingabevalidierung und Bereinigung
- Einrichten eines sicheren Datei-Uploads mit entsprechenden Einschränkungen und Virenprüfungen
- Regelmäßige Sicherheits-Audits und Schwachstellenbewertungen

### Überlegungen zur Konformität

**Vorschriften**

- Branchenspezifische Compliance-Anforderungen verstehen und implementieren
- Dokumentieren von Compliance-Maßnahmen zu Auditzwecken
- Regelmäßige Überprüfung von Änderungen der Rechtsvorschriften und ihrer Auswirkungen auf Formulare
- Mitarbeiterschulung zu Compliance-Anforderungen und Umsetzung

**Barrierefreiheit**

- Befolgen der WCAG 2.1 AA-Richtlinien für Barrierefreiheit
- Regelmäßige Zugänglichkeitstests mit Hilfstechnologien
- Benutzertests mit Menschen mit Behinderungen
- Dokumentation von Barrierefreiheitsfunktionen und Compliance-Maßnahmen

## Best Practices für Team Collaboration

### Dokumentation und Wissensaustausch

**Formulardokumentation**

- Klare Dokumentation der Formularzwecke, Anforderungen und Geschäftsregeln
- Document Integration-Endpunkte, Datenflüsse und Abhängigkeiten
- Versionsverlauf und Änderungsprotokolle für Formularaktualisierungen aufbewahren
- Austausch von Best Practices und Erfahrungen über Teams hinweg

**Schulung und Einführung**

- Bieten Sie Schulungen für Team-Mitglieder zu den Funktionen von Forms Experience Builder an
- Festlegen von Richtlinien für die konsistente Formularerstellung im gesamten Unternehmen
- Regelmäßige Wissensaustauschsitzungen für neue Funktionen und Best Practices
- Mentoring-Programme für neue Benutzer der Plattform

### Qualitätssicherung

**Überprüfungsprozesse**

- Implementieren von Peer-Review-Prozessen für den Formularentwurf und die Implementierung
- Erstellen von Testprotokollen für Formularfunktionalität und Benutzererlebnis
- Regelmäßige Prüfungen vorhandener Formulare zur Optimierung
- Feedback-Sammlung sowohl von internen Benutzern als auch von Endbenutzern

**Standards und Richtlinien**

- Entwicklung von Organisationsstandards für Formularentwurf und -implementierung
- Erstellen von Vorlagen und Richtlinien für allgemeine Formulartypen
- Einrichten von Genehmigungsprozessen für neue Formulare und größere Änderungen
- Regelmäßige Überprüfung und Aktualisierung von Organisationsstandards

## Erweiterte Best Practices

### LLM-optimierte Smart Fields

**Nutzen von KI-Wissen**

- Nutzen Sie das integrierte Wissen der KI für umfassende Feldoptionen
- Anfordern intelligenter Felder für geografische Daten, Unternehmensklassifizierungen und Branchenstandards
- Implementieren einer intelligenten Feldpopulation für ein verbessertes Benutzererlebnis
- Testen der Genauigkeit und Vollständigkeit von Smart-Feldern für Ihre spezifischen Anwendungsfälle

**Beispiele für intelligente Felder**

    „Fügen Sie ein Feld Abflughafen mit allen wichtigen Flughäfen weltweit hinzu, einschließlich IATA-Codes“
    „Erstellen Sie ein umfassendes Branchenfeld mit der standardmäßigen NAICS-Klassifizierung“
    „Schließen Sie ein Dropdown-Menü für die professionelle Zertifizierung ein, das sich je nach Tätigkeitsfeld anpasst“

### Erweiterte Formularlogik

**Komplexe Geschäftsregeln**

- Aufspaltung komplexer Geschäftslogik in kleinere, testbare Komponenten
- Anforderungen an Geschäftsregeln vor der Implementierung klar dokumentieren
- Testen Sie Edge-Fälle und Ausnahmeszenarien gründlich
- Bereitstellung von klarem Benutzer-Feedback für Verstöße gegen Geschäftsregeln

**Dynamisches Formularverhalten**

- Progressive Offenlegung verwenden, um relevante Felder basierend auf der Benutzereingabe anzuzeigen
- Implementieren intelligenter Standardwerte, die von Benutzern überschrieben werden können
- Erstellen adaptiver Formulare, die sich an das Benutzerverhalten und die Voreinstellungen anpassen
- Balance zwischen Automatisierung mit Benutzerkontrolle und Transparenz

## Validierung und Tests

### Umfassende Teststrategie

**Tests auf mehreren Ebenen**

- Komponententests für einzelne Formularkomponenten und Validierungsregeln
- Integrationstests für Übermittlungsendpunkte und Datenflüsse
- Benutzerakzeptanztests mit repräsentativen Benutzergruppen
- Leistungstests unter verschiedenen Lastbedingungen

**Plattformübergreifende Validierung**

- Testen von Formularen in verschiedenen Browsern und Versionen
- Mobile Erlebnisse auf verschiedenen Geräten und Bildschirmgrößen validieren
- Zugänglichkeitstests mit verschiedenen Hilfstechnologien
- Netzwerkzustandstests für verschiedene Verbindungsgeschwindigkeiten

### Qualitätsmetriken

**Erfolgsindikatoren**

- Formularausfüllungsraten über branchenüblichen Benchmarks
- Niedrige Fehlerquoten und hohe Benutzerzufriedenheit
- Schnelle Ladezeiten und responsive Benutzerinteraktionen
- Erfolgreiche Integration mit Backend-Systemen und -Prozessen

**Kontinuierliche Überwachung**

- Regelmäßige Überprüfung der Formularleistungsmetriken und des Benutzer-Feedbacks
- Proaktive Identifizierung und Lösung von Problemen
- Trendanalyse zur Nutzung und Effektivität von Formularen
- Benchmarking anhand von Branchenstandards und Best Practices

Weitere Anleitungen und ausführliche Beispiele finden Sie im Handbuch zu den ersten Schritten mit Forms Experience Builder [&#128279;](forms-ai-assistant-getting-started.md) und in der Eingabeaufforderungsbibliothek zu Forms Experience Builder[.](ai-assistant-prompt-library.md)
