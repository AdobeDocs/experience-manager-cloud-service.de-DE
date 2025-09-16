---
title: Forms Experience Builder – Best Practices
description: Umfassende Best Practices für die Erstellung effektiver Formulare mit Forms Experience Builder unter Berücksichtigung von Design, Anwendererlebnis, Leistung und Markenkonsistenz.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2072'
ht-degree: 100%

---


# Forms Experience Builder – Best Practices

>[!NOTE]
>
> Forms Experience Builder ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich noch ändern**: Diese Best Practices werden derzeit mit dem Produkt getestet und unterliegen Aktualisierungen und Überarbeitungen. Best Practices, Empfehlungen und Beispiele können sich ändern, wenn Forms Experience Builder während des Early-Adopter-Programms weiterentwickelt wird.

Dieses umfassende Handbuch enthält bewährte Best Practices für die Erstellung effektiver, benutzerfreundlicher Formulare mit Forms Experience Builder. Diese Best Practices stammen aus erfolgreichen Implementierungen und Benutzer-Feedback aus verschiedenen Branchen und Anwendungsfällen.

## Best Practices für das Formular-Design

### Halten Sie es einfach

**Start mit grundlegenden Feldern**

- Beginnen Sie mit den wichtigsten Informationen, um die Benutzerüberlastung zu reduzieren.
- Erhöhen Sie je nach Benutzer- und Geschäftsanforderungen schrittweise die Komplexität
- Vermeiden Sie es, nach Informationen zu fragen, die Sie eigentlich gar nicht benötigen oder verwenden
- Berücksichtigen Sie beim Entwerfen von Formularen die Zeit und die kognitive Belastung von Benutzenden

**Verwenden von klaren, beschreibenden Labels**

- Machen Sie den Zweck von Feldern mit beschreibenden Labels sofort offensichtlich
- Vermeiden Sie technischen Jargon oder interne Terminologie, die Benutzende nicht verstehen
- Verwenden Sie einheitliche Label-Konventionen in Ihren Formularen
- Fügen Sie Kontext hinzu, wenn die Feldanforderungen möglicherweise nicht offensichtlich sind

**Bereitstellen von hilfreichen Anleitungen**

- Fügen Sie Hilfetext für komplexe Felder mit Beispielen und Formatierungsanforderungen hinzu
- Verwenden Sie Platzhaltertext zur Anzeige der erwarteten Eingabeformate
- Formulieren Sie Anweisungen zum Hochladen von Dateien sowie zu akzeptierten Formaten und Größenbeschränkungen klar
- Führen Sie Benutzende durch mehrstufige Prozesse mit Fortschrittsanzeigen

**Gründliches Testen**

- Überprüfen Sie alle Benutzerpfade und Szenarien vor der Bereitstellung
- Testen Sie Formulare mit echten Benutzenden aus Ihrer Zielgruppe
- Überprüfen Sie, ob alle bedingten Logiken erwartungsgemäß funktionieren
- Stellen Sie sicher, dass die Fehlerbehandlung klares, umsetzbares Feedback zur Verfügung stellt

### Progressive Offenlegung

**Anzeigen relevanter Felder basierend auf dem Kontext**

- Zeigen Sie zusätzliche Felder nur an, wenn sie für die Benutzerauswahl relevant werden
- Verwenden Sie bedingte Logik zur Reduzierung der kognitiven Belastung und der Formularlänge
- Gruppieren Sie verwandte Felder in logischen Abschnitten
- Blenden Sie erweiterte Optionen aus, bis Benutzende diese benötigen

**Beispiel einer Implementierung:**

    Erstellen Sie eine Regel, die das Panel „@spouseInformation“ nur anzeigt, wenn „@maritalStatus“ gleich „verheiratet“ ist

**Klare Navigation und klarer Fortschritt**

- Stellen Sie sicher, dass Benutzende immer wissen, wo sie sich in mehrstufigen Formularen befinden
- Stellen Sie eine klare Navigation zwischen Formularabschnitten sicher
- Zeigen Sie Fortschrittsanzeigen für längere Formulare an
- Ermöglichen Sie es Benutzenden, den Fortschritt zu speichern und später zurückzukehren

## Best Practices für das Anwendererlebnis

### Mobile-First-Design

**Optimierung des responsiven Layouts**

- Gestalten Sie Formulare mit mobilen Benutzenden als primäre Zielgruppe
- Verwenden Sie einspaltige Layouts für Mobilgeräte
- Stellen Sie sicher, dass Touch-Ziele eine angemessene Größe aufweisen (mindestens 44 px)
- Testen Sie Formulare auf Geräten verschiedener Größen und Ausrichtungen

**Touch-optimierte Interaktionen**

- Implementieren Sie größere Schaltflächen und Eingabefelder für Touch-Oberflächen
- Verwenden Sie geeignete Eingabetypen, um korrekte Mobiltastaturen auszulösen
- Vermeiden Sie Interaktionen, die eine Bewegung mit der Maus erfordern, da diese auf Touch-Geräten nicht funktionieren
- Geben Sie klares visuelles Feedback für Benutzerinteraktionen

### Compliance mit Barrierefreiheit

**WCAG 2.1-Richtlinien**

- Befolgen Sie die Richtlinien für Barrierefreiheit in Webinhalten, um ein inklusives Design zu ermöglichen
- Achten Sie auf angemessene Farbkontrastverhältnisse (mindestens 4,5:1 für normalen Text)
- Stellen Sie Alternativtext für alle Bilder und Symbole zur Verfügung
- Implementieren Sie korrekte Überschriftenstruktur und semantische HTML

**Navigation über die Tastatur**

- Stellen Sie sicher, dass auf alle Formularelemente über die Tastaturnavigation zugegriffen werden kann
- Stellen Sie klare Fokusindikatoren für alle interaktiven Elemente zur Verfügung
- Implementieren Sie eine logische Registerkartenreihenfolge durch Formularfelder
- Implementieren Sie Links zum Überspringend der Navigation für komplexe Formulare

**Unterstützung von Bildschirmlesehilfen**

- Verwenden Sie die richtigen ARIA-Labels und -Beschreibungen für Formularfelder
- Stellen Sie klare Fehlermeldungen zur Verfügung, die von Bildschirmlesehilfen angekündigt werden
- Stellen Sie sicher, dass Änderungen des dynamischen Inhalts ordnungsgemäß angekündigt werden
- Testen Sie Formulare mit aktueller Bildschirmlesehilfe-Software

### Leistungsoptimierung

**Ladegeschwindigkeit**

- Optimieren Sie die Ladezeiten von Formularen durch Minimieren der anfänglichen Paketgröße
- Implementieren Sie verzögertes Laden für nicht kritische Formularabschnitte
- Bilder und Assets für die Web-Bereitstellung optimieren
- Aktivieren Sie geeignete Caching-Strategien für statische Ressourcen

**Laufzeitleistung**

- Verwenden Sie einen geeigneten Validierungszeitpunkt, um Benutzererlebnis und Leistung aufeinander abzustimmen
- Implementieren Sie Debouncing für die Echtzeit-Validierung, um Server-Anfragen zu reduzieren
- Aktivieren Sie Caching von häufig aufgerufenen Daten und Validierungsergebnissen
- Optimieren Sie die Ausführung von bedingter Logik für komplexe Formulare

**Automatisches Speichern und Datenschutz**

- Implementieren Sie automatisches Speichern des Formularfortschritts, um Datenverlust zu vermeiden
- Bieten Sie nach Möglichkeit Offline-Funktionen für das Ausfüllen des Formulars an
- Implementieren Sie Wiederholungslogik für fehlgeschlagene Übermittlungen
- Bieten Sie Datenexportoptionen als Backup für Benutzende an

## Best Practices für die Markenkonsistenz

### Vorbereiten von Marken-Assets

**Erstellen von Markenvorlagen**

- Entwickeln Sie standardisierter Formularvorlagen mit der visuellen Identität Ihres Unternehmens
- Achten Sie auf konsistente Farbschemata, Typografie und Layout-Muster
- Bereiten Sie wiederverwendbarer Komponenten vor, die Ihren Markenrichtlinien entsprechen
- Dokumentieren Sie Stilstandards, um eine konsistente Implementierung in allen Teams zu gewährleisten

**Definieren von Stilrichtlinien**

- Erstellen Sie konsistente Feldstile, Schaltflächen-Designs und Abstandsstandards
- Erstellen Sie ein Stil-Handbuch, das Farb-Codes, Schriftspezifikationen und Layout-Regeln enthält
- Definieren Sie Interaktionsmustern und Animationsrichtlinien
- Bereiten Sie markenspezifische Fehlermeldungen und Hilfetexte vor

**Bibliothek mit Bausteinkomponenten**

- Erstellen Sie wiederverwendbare Formularkomponenten, die Ihrer Markenidentität entsprechen
- Entwickeln Sie konsistente Navigationsmuster und Elemente der Benutzeroberfläche
- Bereiten Sie Markensymbolen, Logos und visuelle Assets für die Formularintegration vor
- Erstellen Sie Vorlagen für allgemeine Formulartypen (Kontakt, Registrierung, Feedback)

### Strategien zur Markenimplementierung

**Stil-Prompts für Konsistenz**

Fügen Sie markenspezifische Anweisungen in Ihre Prompts ein:

    Erstellen Sie ein professionelles Kontaktformular unter Verwendung von:
    – Unternehmensblau (#003366) für primäre Schaltflächen und Kopfzeilen
    – Schriftfamilie „Open Sans“ für alle Textelemente
    – Mindestschriftgröße von 16 px zur Compliance mit Barrierefreiheit
    – Konsistenter Abstand von 24 px zwischen Formularabschnitten
    – Firmenlogo in der Kopfzeile mit korrekter Markenpositionierung

**Verwaltung der Vorlagenbibliothek**

- Pflegen Sie eine Sammlung von Formularvorlagen mit Branding für gängige Anwendungsfälle
- Verwenden Sie eine Versionskontrolle Ihrer Markenvorlagen zur Sicherstellung der Konsistenz
- Stellen Sie eine klaren Dokumentation zur Verwendung und Anpassung von Vorlagen zur Verfügung
- Überprüfen und aktualisieren Sie Marken-Assets zur Einhaltung aktueller Standards regelmäßig

>[!NOTE]
>
>**Benutzerdefinierte Komponenten**: Koordinieren Sie sich mit Ihrem Entwicklungs-Team, um organisationsspezifische Komponenten und deren Kompatibilität mit dem Forms Experience Builder zu verwenden, bevor Sie benutzerdefinierte Markenelemente implementieren.

## Best Practices für Inhalt und Kommunikation

### Ansätze der Formularerstellung

**Zwei Hauptmethoden**

Wählen Sie die für Ihre Anforderungen am besten geeignete Erstellungsmethode aus:

1. **Erstellen von Grund auf**: Ideal für neue Formulare mit spezifischen Anforderungen
2. **Importieren und Konvertieren**: Ideal für die Modernisierung vorhandener Formulare und Dokumente

**Prompts in natürlicher Sprache**

- Formulieren Sie Ihre Formularbeschreibungen spezifisch und detailliert
- Verwenden Sie klare, auf Geschäftsabläufe fokussierte Terminologie anstelle von technischen Begriffen
- Stellen Sie Kontext über den Zweck und die Zielgruppe des Formulars zur Verfügung
- Nehmen Sie Validierungs- und Geschäftsregelanforderungen in anfängliche Prompts auf

### Strategie für inkrementelle Entwicklung

**Einfaches Starten, Aufbauen der Komplexität**

- Beginnen Sie mit der grundlegenden Formularstruktur und den wesentlichen Feldern
- Fügen Sie Validierungsregeln und Geschäftslogik schrittweise hinzu
- Testen Sie jede Änderung, bevor Sie zur nächsten Erweiterung übergehen
- Sammeln Sie Benutzer-Feedback in jeder Entwicklungsphase

**Beispiel für inkrementellen Ansatz:**

    Schritt 1: „Erstellen Sie ein einfache Kontaktformular mit Namen-, E-Mail- und Nachrichtenfeldern“
    Schritt 2: „Machen Sie die Felder „@name“ und „@email“ zu Pflichtfeldern mit entsprechender Validierung“
    Schritt 3: „Fügen Sie Platzhaltertext und Hilfetext zur Benutzeranleitung hinzu“
    Schritt 4: „Fügen Sie bedingte Logik auf der Grundlage des Anfragetyps hinzu“

### Best Practices für Feldverweise

**Konsistente Benennungskonventionen**

- Verwenden Sie klare, beschreibende Feldnamen, die ihrem Zweck entsprechen
- Behalten Sie konsistenter Benennungsmuster in allen Formularen bei
- Verwenden Sie camelCase oder snake_case konsistent in Ihren Formularen
- Dokumentieren Sie Benennungskonventionen für Felder zur Gewährleistung der Team-Konsistenz

**Effektive Feldverweise**

- Verwenden Sie die Syntax `@fieldName`, wenn Sie vorhandene Felder bearbeiten
- Geben Sie klar an, auf welche Felder Sie in komplexen Formularen verweisen
- Gruppieren Sie verwandte Feldbearbeitungen in einzelnen Anfragen
- Überprüfen Sie Feldnamen, bevor sie Sie in bedingter Logik verwenden

## Best Practices für Integration und Übermittlung

### Multi-Channel-Übermittlungsstrategie

**Primäre und sekundäre Aktionen**

- Konfigurieren Sie primäre Übermittlungsendpunkten für zentrale Geschäftsprozesse
- Richten Sie sekundäre Aktionen für Benachrichtigungen, Bestätigungen und Daten-Backup ein
- Implementieren Sie Fehlerbehandlung und Wiederholungslogik für fehlgeschlagene Übermittlungen
- Geben Sie Benutzer-Feedback für alle Übermittlungsstatus (Erfolg, Fehler, Verarbeitung)

**Integrationsplanung**

- Beginnen Sie mit der grundlegenden Übermittlungskonfiguration und fügen Sie Integrationen schrittweise hinzu
- Testen Sie jede Integration separat, bevor Sie mehrere Endpunkte kombinieren
- Dokumentieren Sie API-Anforderungen und -Authentifizierungsmethoden
- Planen Sie Datenumwandlungs- und Zuordnungsanforderungen

### Fehlerbehandlung und Wiederherstellung

**Benutzerfreundliche Fehlermeldungen**

- Formulieren Sie klare, umsetzbare Fehlermeldungen, die Benutzenden beim Lösen von Problemen helfen
- Vermeiden Sie technische Fehler-Codes oder Systemmeldungen in Inhalten für Benutzende
- Bieten Sie alternative Aktionen an, wenn die primäre Übermittlung fehlschlägt
- Geben Sie Benutzenden Kontaktinformationen an, wenn sie zusätzliche Hilfe benötigen

**Datenschutz und Wiederherstellung von Daten**

- Implementieren Sie einen lokalen Datenspeicher für die Formularwiederherstellung nach Fehlern
- Stellen Sie Optionen für Benutzende bereit, mit denen Sie ihre Formulardaten als Backup herunterladen können
- Richten Sie eine Überwachung und Warnhinweise für fehlgeschlagene Übermittlungen ein
- Planen Sie Wiederherstellungsverfahren bei Systemausfällen oder Wartungsarbeiten

## Best Practices für Leistung und Analyse

### Überwachung und Optimierung

**Wichtige Leistungsmetriken**

- Verfolgen Sie Formularabschlussraten und -abbruchpunkte
- Überwachen Sie Ladezeiten und Interaktionsmuster von Benutzenden
- Messen Sie Validierungseffektivität und Fehlerraten
- Analysieren Sie Feedback und Zufriedenheitswerte von Benutzenden

**Kontinuierliche Verbesserung**

- Überprüfen Sie die Formularanalyse zur Ermittlung von Optimierungsmöglichkeiten regelmäßig
- Führen Sie A/B-Tests verschiedener Formular-Designs und Benutzerabläufe durch
- Sammeln und analysieren Sie Benutzer-Feedback für iterative Verbesserungen
- Führen Sie Benchmarking der Leistung anhand von Branchenstandards durch

### Datenqualität und -validierung

**Intelligente Validierungsstrategien**

- Implementieren Sie Echtzeitvalidierung für sofortiges Benutzer-Feedback
- Verwenden Sie progressive Validierung, um Benutzende durch komplexe Anforderungen zu führen
- Stellen Sie klare Validierungsmeldungen bereit, die erklären, wie Fehler behoben werden
- Wägen Sie die Schärfe der Validierung mit Überlegungen zum Anwendererlebnis ab

**Datenintegrität**

- Implementieren Sie feldübergreifenden Validierungen für Datenkonsistenz
- Verwenden Sie geeignete Eingabetypen und Einschränkungen, um ungültige Daten zu verhindern
- Stellen Sie Beispiele für Datenformate und Anleitungen für komplexe Felder zur Verfügung
- Prüfen Sie die Qualität der übermittelten Daten und die Effektivität der Validierung regelmäßig

## Best Practices für Sicherheit und Compliance

### Datenschutz

**Standardmäßiger Datenschutz**

- Sammeln Sie nur die für Ihren Geschäftszweck erforderlichen Mindestdaten
- Implementieren Sie geeignete Richtlinien zur Datenspeicherung und -löschung
- Stellen Sie klare Datenschutzhinweise und Einverständnismechanismen bereit
- Stellen Sie Compliance mit relevanten Datenschutzbestimmungen (DSGVO, CCPA usw.) sicher

**Implementierung von Sicherheit**

- Nutzen Sie HTTPS-Verschlüsselung für alle Formularübermittlungen und Datenübertragungen
- Implementieren Sie eine ordnungsgemäße Eingabevalidierung und -bereinigung
- Richten Sie sichere Datei-Uploads mit entsprechenden Einschränkungen und Virenprüfungen ein
- Führen Sie regelmäßige Sicherheitsaudits und Schwachstellenbewertungen durch

### Überlegungen zur Compliance

**Behördliche Vorschriften**

- Machen Sie sich mit branchenspezifische Compliance-Anforderungen vertraut und implementieren Sie diese
- Dokumentieren Sie Compliance-Maßnahmen zu Auditzwecken
- Überprüfen Sie Änderungen von behördlichen Vorschriften und ihre Auswirkungen auf Formulare regelmäßig
- Führen Sie Personalschulungen zu Compliance-Anforderungen und -Umsetzung durch

**Compliance mit Barrierefreiheit**

- Befolgen Sie WCAG 2.1 AA-Richtlinien für Barrierefreiheit
- Testen Sie Barrierefreiheit mit Unterstützungstechnologien regelmäßig
- Führen Sie regelmäßig Benutzertests mit Personen mit Behinderungen durch
- Dokumentieren Sie Barrierefreiheitsfunktionen und Compliance-Maßnahmen

## Best Practices für Team-Zusammenarbeit

### Dokumentation und Wissensaustausch

**Dokumentation für Formulare**

- Pflegen Sie eine klare Dokumentation der Zwecke, Anforderungen und Geschäftsregeln von Formularen
- Dokumentieren Sie Integrationsendpunkte, Datenflüsse und Abhängigkeiten
- Pflegen Sie einen Versionsverlauf und Änderungsprotokolle für Formularaktualisierungen
- Tauschen Sie Best Practices und Erfahrungen über Teams aus

**Schulung und Einführung**

- Bieten Sie Schulungen für Team-Mitglieder zu den Funktionen des Forms Experience Builder an
- Legen Sie Richtlinien für die konsistente Formularerstellung im gesamten Unternehmen fest
- Führen Sie regelmäßige Sitzungen zum Wissensaustausch zu neuen Funktionen und Best Practices durch
- Stellen Sie Mentoring-Programme für neue Benutzende der Plattform zur Verfügung

### Qualitätssicherung

**Überprüfungsprozesse**

- Implementieren Sie Peer-Review-Prozesse für Formularentwurf und -implementierung
- Erstellen Sie Testprotokolle für Formularfunktionalität und Anwendererlebnis
- Führen Sie regelmäßige Audits vorhandener Formulare zur Optimierung durch
- Sammeln Sie Feedback sowohl von internen Benutzenden als auch von Endbenutzenden

**Standards und Richtlinien**

- Entwickeln Sie Organisationsstandards für Formularentwurf und -implementierung
- Erstellen Sie Vorlagen und Richtlinien für allgemeine Formulartypen
- Erstellen Sie Genehmigungsprozessen für neue Formulare und größere Änderungen
- Überprüfen und aktualisieren Sie Organisationsstandards regelmäßig

## Erweiterte Best Practices

### LLM-optimierte intelligente Felder

**Nutzen von KI-Wissen**

- Nutzen Sie das integrierte Wissen von KI für umfassende Feldoptionen
- Fordern Sie intelligente Felder für geografische Daten, Unternehmensklassifizierungen und Branchenstandards an
- Implementieren Sie intelligente Feldpopulation für ein verbessertes Anwendererlebnis
- Testen Sie Genauigkeit und Vollständigkeit von intelligenten Feldern für Ihre spezifischen Anwendungsfälle

**Beispiele für intelligente Felder**

    „Füge ein Feld für Abflughafen mit allen wichtigen Flughäfen weltweit hinzu, einschließlich IATA-Codes“
    „Erstelle ein Feld für umfassende Branchen mit der standardmäßigen NAICS-Klassifizierung“
    „Füge ein Dropdown-Menü für professionelle Zertifizierungen hinzu, das sich je nach Tätigkeitsfeld anpasst“

### Erweiterte Formularlogik

**Komplexe Geschäftsregeln**

- Schlüsseln Sie komplexe Geschäftslogik in kleinere, testbare Komponenten auf
- Dokumentieren Sie Anforderungen an Geschäftsregeln vor der Implementierung klar
- Testen Sie Grenzfälle und Ausnahmeszenarien gründlich
- Stellen Sie klares Benutzer-Feedback für Verstöße gegen Geschäftsregeln bereit

**Verhalten dynamisch Formulare**

- Verwenden Sie progressive Offenlegung, um relevante Felder basierend auf der Benutzereingabe anzuzeigen
- Implementieren Sie intelligente Standardwerte, die von Benutzenden überschrieben werden können
- Erstellen Sie adaptive Formulare, die sich an das Benutzerverhalten und die Voreinstellungen anpassen
- Wägen Sie Automatisierung mit Benutzerkontrolle und Transparenz ab

## Validierung und Tests

### Strategie für umfassende Tests

**Mehrstufige Tests**

- Modultests für einzelne Formularkomponenten und Validierungsregeln
- Integrationstests für Übermittlungsendpunkte und Datenflüsse
- Benutzerakzeptanztests mit repräsentativen Benutzergruppen
- Leistungstests unter verschiedenen Lastbedingungen

**Plattformübergreifende Validierung**

- Testen Sie Formulare in verschiedenen Browsern und Versionen
- Validieren Sie mobile Erlebnisse auf verschiedenen Geräten und Bildschirmgrößen
- Führen Sie Barrierefreiheitstests mit verschiedenen Unterstützungstechnologien durch
- Führen Sie Netzwerkzustandstests für verschiedene Verbindungsgeschwindigkeiten durch

### Qualitätsmetriken

**Erfolgsindikatoren**

- Formularabschlussraten über branchenüblichen Benchmarks
- Niedrige Fehlerraten und hohe Benutzerzufriedenheitswerte
- Schnelle Ladezeiten und responsive Benutzerinteraktionen
- Erfolgreiche Integration mit Backend-Systemen und -Prozessen

**Kontinuierliche Überwachung**

- Regelmäßige Überprüfung von Formularleistungsmetriken und Benutzer-Feedback
- Proaktive Identifizierung und Lösung von Problemen
- Trendanalyse zur Nutzung und Effektivität von Formularen
- Benchmarking anhand von Branchenstandards und Best Practices

Weitere Anleitungen und ausführliche Beispiele finden Sie im Handbuch zu den [ersten Schritten mit dem Forms Experience Builder](forms-ai-assistant-getting-started.md) und zur [ Prompt-Bibliothek des Forms Experience Builder](ai-assistant-prompt-library.md).
