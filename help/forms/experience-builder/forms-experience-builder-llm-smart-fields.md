---
title: LLM-optimierte Smart Fields in Forms Experience Builder
description: Erfahren Sie, wie Sie mithilfe der KI-Wissensdatenbank für geografische Daten, Geschäftsklassifizierungen und Branchenstandards intelligente Formularfelder mit vorausgefüllten Optionen erstellen.
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: a03b247c-1e50-4dee-9182-bc81fb83a48b
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1474'
ht-degree: 24%

---

# LLM-optimierte Smart Fields in Forms Experience Builder {#llm-enhanced-smart-fields}

Forms Experience Builder nutzt die Leistungsfähigkeit großer Sprachmodelle (LLMs), um intelligente Formularfelder mit vorausgefüllten Optionen zu erstellen, die aus umfassenden Wissensdatenbanken schöpfen. Dank dieser Funktion müssen umfangreiche Datensätze nicht mehr manuell recherchiert und eingegeben werden, was die Effizienz und Genauigkeit der Formularerstellung erheblich verbessert.

## Was sind LLM-optimierte Smart Fields? {#what-are-llm-smart-fields}

LLM-optimierte Smart Fields sind Formularfelder, die mithilfe der integrierten Wissensdatenbank der KI automatisch mit umfassenden, genauen Daten gefüllt werden. Anstatt Dropdown-Listen oder Optionssätze manuell zu erstellen, können Sie Felder anfordern, für die umfangreiche Datensätze erforderlich sind, und die KI generiert automatisch die entsprechenden Optionen.

**Wichtigste Vorteile:**

* **Umfassende Datensätze** - Zugriff auf umfassende, aktuelle Informationen über mehrere Domains hinweg
* **Automatische Population** - Es müssen keine Daten manuell recherchiert und eingegeben werden
* **Standardisierte Formate** - Verwendet Branchenstandard-Codes, Klassifizierungen und Benennungskonventionen
* **Kontextabhängige Optionen** - Felder können basierend auf anderen Formularauswahlen angepasst werden
* **Zeitsparend** - Verringert die Zeit bei der Formularerstellung von Stunden auf Minuten

## Verwendung von LLM-erweiterten Smart-Feldern {#when-to-use-smart-fields}

Verwenden Sie LLM-erweiterte Smart-Felder, wenn Sie Folgendes benötigen:

* **Umfassende Datensätze** - Felder, für die umfangreiche, standardisierte Informationen erforderlich sind
* **Branchenstandards** - Klassifizierungen, Codes oder regulatorische Daten
* **Geografische Informationen** - Standorte, Regionen oder Verwaltungsbereiche
* **Berufliche Daten** - Berufsbezeichnungen, Zertifizierungen oder Branchenklassifizierungen
* **Technische**: Dateiformate, Protokolle oder Systemspezifikationen

## Geografische Felder und Standortfelder {#geographic-location-fields}

Erstellen Sie standortbasierte Felder mit umfassenden geografischen Daten und administrativen Informationen.

### Flughäfen und Transport

**Internationale Flughäfen mit IATA-Codes:**

    Füge eine Dropdown-Liste für Abflughäfen mit allen wichtigen internationalen Flughäfen hinzu
    Füge ein Feld für Ankunftsflughäfen mit IATA-Codes und vollständigen Namen hinzu
    Erstelle ein Feld für den nächstgelegenen Flughafen zum Benutzerstandort
    Füge eine Auswahl an Bahnhöfen europäischer Städte hinzu

**Beispielaufforderungen:**

* „Fügen Sie ein Feld Abflughafen mit allen wichtigen Flughäfen weltweit hinzu, einschließlich IATA-Codes und Stadtnamen“
* „Erstellen einer Dropdown-Liste für Ankunftsflughäfen mit nach Kontinent geordneten internationalen Flughäfen“
* „Eine Auswahl an Bahnhöfen für europäische Großstädte mit Bahnhofscodes aufnehmen“

### Verwaltungsbezirke

**Länder, Bundesstaaten und Provinzen:**

    Füge eine vollständige Liste der US-Bundesstaaten mit Abkürzungen hinzu
    Erstelle eine Dropdown-Liste mit ISO-Codes und vollständigen Namen
    Füge ein Feld für die größten Städte der Welt mit Zeitzonen hinzu
    Füge eine Dropdown-Liste der kanadischen Provinzen und Territorien hinzu
    Füge ein Feld für britische Countys und Postgebiete hinzu

**Beispielaufforderungen:**

* „Erstellen eines Länderauswahlfelds mit ISO-Ländercodes und vollständigen Namen“
* „Hinzufügen eines Dropdown-Menüs für den US-Bundesstaat mit Landeskürzeln und vollständigen Namen“
* „Ein Feld in der kanadischen Provinz mit Gebieten und Postleitzahlen“
* „Ein Feld für Weltstädte mit großen Ballungsräumen und Zeitzonen schaffen“

## Unternehmens- und Branchendaten {#business-industry-data}

Nutzen Sie umfassende Geschäftsklassifizierungen und professionelle Daten für Unternehmensformulare.

### Unternehmensklassifizierungen

**Branchen- und Geschäftsentitätstypen:**

    Füge ein Feld für die Branchenklassifizierung mit NAICS-Codes hinzu
    Erstelle eine Dropdown-Liste der Typen von Geschäftseinheiten (LLC, Corporation, Partnerschaft usw.)
    Füge ein Feld für Unternehmensgrößenkategorien hinzu (Startup, KMU, Unternehmen)
    Füge eine Abteilungsauswahl für große Organisationen hinzu
    Füge ein Feld für Typen professioneller Dienstleistungen hinzu

**Beispielaufforderungen:**

* „Erstellen eines umfassenden Branchenfelds mithilfe der standardmäßigen NAICS-Klassifizierung mit Technologie-Unterkategorien“
* „Hinzufügen einer Dropdown-Liste für den Typ der Geschäftseinheit mit rechtlichen Strukturen und Beschreibungen“
* „Ein Feld „Unternehmensgröße“ mit Bereichen für die Mitarbeiteranzahl und Umsatzstufen einbeziehen“

### Berufsklassifikationen

**Berufsbezeichnungen und Zertifizierungen:**

    Füge ein Feld für Stellenbezeichnungen mit üblichen Branchenrollen hinzu
    Erstelle eine Dropdown-Liste mit professionellen Zertifizierungen nach Feld
    Füge Ausbildungsstufen mit Abschlussarten hinzu
    Füge ein Feld für Zeitbereiche für Erfahrung hinzu
    Erstelle eine Auswahl für Programmiersprachen und Frameworks

**Beispielaufforderungen:**

* „Schließen Sie ein Dropdown-Menü für professionelle Zertifizierungen ein, das sich auf der Grundlage des ausgewählten Jobfelds anpasst.“
* „Erstellen Sie ein Feld für die Stellenbezeichnung mit gemeinsamen Rollen in den Bereichen Technologie, Gesundheitswesen und Finanzen“
* „Hinzufügen eines Felds auf Bildungsebene mit Studientypen und Fachgebieten“

## Normen und regulatorische Daten {#standards-regulatory-data}

Zugriff auf standardisierte Codes, Klassifizierungen und behördliche Informationen für Compliance-orientierte Formulare.

### Finanzielle und rechtliche Aspekte

**Währungs-, Steuer- und Zahlungsinformationen:**

    Füge ein Feld für Währungs-Codes mit Symbolen und Wechselkursen hinzu
    Erstelle eine Dropdown-Liste mit Steuer-ID-Typen nach Land
    Füge ein Feld für Typen rechtlicher Dokumente hinzu
    Füge Optionen für Zahlungsmethoden mit Sicherheitsmerkmalen hinzu
    Erstelle eine Auswahl für Bankinstitute nach Land

**Beispielaufforderungen:**

* „Erstellen Sie ein Währungsauswahlfeld mit ISO-Codes, Symbolen und wichtigen Wechselkursen“
* „Feld vom Typ Steuer-ID mit länderspezifischen Steueridentifizierungsformaten hinzufügen“
* „Dropdown-Liste für Zahlungsmethoden mit Sicherheitsfunktionen und Verarbeitungszeiten einfügen“

### Technische Standards

**Dateiformate und Protokolle:**

    Füge eine Dropdown-Liste mit Dateitypen mit Erweiterungen hinzu
    Füge Optionen für Netzwerkprotokolle hinzu
    Füge ein Feld für Datenbanktypen und -versionen hinzu
    Erstelle eine Auswahl für API-Authentifizierungsmethoden

**Beispielaufforderungen:**

* „Erstellen eines Dropdown-Menüs „Dateiformat“ mit allgemeinen Erweiterungen und MIME-Typen“
* „Hinzufügen eines Datenbankauswahlfelds mit Versionen und Funktionsvergleichen“
* „Feld für eine API-Authentifizierungsmethode mit Sicherheitsstufen einschließen“

## Gesundheitswesen und Medizin {#healthcare-medical-fields}

Spezialisierte medizinische Daten und Gesundheitsdaten für branchenspezifische Formulare.

### Medizinische Klassifikationen

**Fachgebiete und medizinische Daten:**

    Füge ein Feld für medizinische Fachgebiete hinzu
    Erstelle eine Dropdown-Liste mit gängigen Medikamenten mit generischen Namen
    Füge ein Feld für Versicherungsanbietertypen hinzu
    Füge eine Auswahl für Kontakte bei medizinischen Notfällen hinzu
    Erstelle ein Feld für Ernährungseinschränkungen und Allergien

**Beispielaufforderungen:**

* „Erstellen Sie ein Fachgebiet mit Unterspezialitäten und Zertifizierungen der Pinnwand“
* „Ein Feld für Medikamente mit generischen Namen, Markennamen und Darreichungsformen hinzufügen“
* „Ein Feld „Versicherungsanbieter“ mit wichtigen Beförderern und Planarten einschließen“

## Zeit- und Kalenderinformationen {#time-calendar-intelligence}

Intelligente Datums- und Zeitfelder mit Geschäftskontext und Planungsintelligenz.

### Datums- und Uhrzeitfelder

**Geschäftszeiten und Zeitplan:**

    Füge ein Feld für Geschäftszeiten mit Zeitzonenverarbeitung hinzu
    Erstelle eine Dropdown-Liste mit Feiertagen nach Land
    Füge saisonale Optionen mit Datumsbereichen hinzu
    Füge ein Feld für die Buchung von Konferenzräumen mit Verfügbarkeit hinzu
    Erstelle eine Auswahl für Muster wiederkehrender Besprechungen

**Beispielaufforderungen:**

* „Erstellen eines Felds „Geschäftszeiten“ mit Zeitzonen und Feiertagsausnahmen“
* „Auswahl an Feiertagen mit länderspezifischen Empfehlungen hinzufügen“
* „Feld für wiederkehrende Besprechungsmuster mit Häufigkeitsoptionen einbeziehen“

## Produkt- und Servicekategorien {#product-service-categories}

E-Commerce und serviceorientierte Felder mit umfassender Kategorisierung.

### E-Commerce-Klassifizierungen

**Produkt- und Servicedaten:**

    Füge ein Feld für Produktkategorien mit Unterkategorien hinzu
    Erstelle eine Dropdown-Liste mit Versandmethoden mit Versandschätzungen
    Füge ein Feld für Optionen für Rückgaberichtlinien hinzu
    Füge eine Auswahl für Kundenprioritätsstufen hinzu
    Erstelle ein Feld für Abonnement-Abrechnungszyklen

**Beispielaufforderungen:**

* „Feld für Produktkategorien mit E-Commerce-Unterkategorien und SKU-Mustern erstellen“
* „Dropdown-Liste Versandmethode mit Lieferzeiten und Kostenschätzungen hinzufügen“
* „Feld für Abrechnungszyklus für Abonnements mit Zahlungsintervallen einbeziehen“

## Best Practices für LLM-erweiterte intelligente Felder {#best-practices-smart-fields}

### Seien Sie bei Ihren Anfragen spezifisch

**Gute Beispiele:**

* „Dropdown-Liste „Land“ mit ISO-Codes, vollständigen Namen und Währungsinformationen hinzufügen“
* „Erstellen Sie ein Fachgebiet mit Zertifizierungen und Subspezialitäten des Vorstands“
* „Ein Feld für Programmiersprachen mit Frameworks und Kenntnissen einfügen“

**Vermeiden Sie vage Anfragen:**

* „Feld „Land hinzufügen“
* „Dropdown-Liste zur Erstellung eines Auftragstitels“
* „Feld für Produktkategorie einschließen“

### Kombinieren mit bedingter Logik

Intelligente Felder funktionieren mit bedingten Regeln außergewöhnlich gut:

    Erstellen Sie ein Feld für die berufliche Zertifizierung, das relevante Optionen basierend auf der ausgewählten Branche anzeigt
    Fügen Sie ein Feld für die Stadt hinzu, das nach dem ausgewählten Land filtert
    Schließen Sie ein Hochschulfeld ein, das sich auf der Grundlage des ausgewählten Studienfelds anpasst

### Validieren und Anpassen

LLM-erweiterte Felder bieten umfassende Daten, aber immer:

* **Überprüfen der generierten Optionen** auf Genauigkeit und Relevanz
* **Benutzerdefinierte Optionen hinzufügen** speziell für Ihre Organisation
* **Entfernen Sie irrelevante Optionen** um das Benutzererlebnis zu optimieren
* **Testen mit echten Benutzern** um die Benutzerfreundlichkeit sicherzustellen

## Erweiterte Smart-Field-Techniken {#advanced-smart-field-techniques}

### Kontextabhängige Felder

Erstellen Sie Felder, die sich basierend auf anderen Formularauswahlen anpassen:

    Universitätsauswahlfeld mit wichtigen, nach Land und Ranking geordneten Institutionen hinzufügen
    Erstellen Sie ein Dropdown-Menü für die Zertifizierung, in dem die relevanten Optionen auf der Grundlage der Stellenbezeichnung angezeigt werden
    Fügen Sie ein Stadtfeld hinzu, das nach ausgewähltem Land und ausgewählter Region filtert

### Mehrstufige Klassifizierungen

Erstellen hierarchischer Datenstrukturen:

    Erstellen Sie ein Feld für die Produktkategorie mit den Hauptkategorien, Unterkategorien und Produkttypen
    Fügen Sie ein geografisches Feld mit den Ebenen Land, Bundesland/Region und Stadt hinzu
    Schließen Sie ein Feld für die Kompetenzbewertung mit den Kategorien, Unterkategorien und Kompetenzniveaus ein

### Integration mit externen Daten

Kombinieren Sie LLM-Wissen mit den Daten Ihres Unternehmens:

    Feld „Abteilung“ hinzufügen, das sowohl die standardmäßigen Unternehmensabteilungen als auch die spezifischen Abteilungen Ihres Unternehmens enthält
    Feld „Produkt“ erstellen, in dem Kategorien nach Branchenstandard mit Ihrem Produktkatalog kombiniert werden
    Feld „Standort“ einfügen, in dem geografische Daten mit Ihren Bürostandorten zusammengeführt werden

## Fehlerbehebung bei Smart-Feldern {#troubleshooting-smart-fields}

### Häufige Probleme und Lösungen

**Problem: Zu viele Optionen generiert**

* **Lösung**: Geben Sie in Ihrer Anfrage genauere Werte an oder fügen Sie Filterkriterien hinzu
* **Beispiel**: Anstelle von „alle Länder“ fordern Sie „wichtige Handelspartnerländer“ an.

**Problem: Fehlende spezifische Optionen**

* **Lösung**: Benutzerdefinierte Optionen hinzufügen oder Eingabeaufforderung verfeinern
* **Beispiel**: „Umfasst die wichtigsten Länder plus [Ihre spezifischen Länder]&quot;

**Problem: Veraltete Informationen**

* **Lösung**: Aktuelle Daten anfordern oder Datumsbereiche angeben
* **Beispiel**: „Aktuelle Feiertage für 2024 hinzufügen“

### Leistungsoptimierung

* **Optionen begrenzen**: Verwenden Sie Filter, um die Anzahl der generierten Optionen zu reduzieren
* **Progressive Offenlegung**: Zuerst die grundlegenden Optionen anzeigen und dann die Erweiterung zulassen.
* **Caching**: Speichern Sie häufig verwendete Smart-Field-Daten zwischen

## Verwandte Artikel

* [Erste Schritte mit Forms Experience Builder](forms-experience-builder-getting-started.md)
* [KI-gestützte Formularerstellung](forms-experience-builder-prompt-examples-library.md)
* [Regelerstellung und Geschäftslogik](forms-experience-builder-prompt-examples-library.md#rule-creation--business-logic)
* [Formularübermittlung und -integration](form-submission-integration.md)
