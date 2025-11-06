---
title: Intelligente Import- und Konvertierungsfunktionen
description: Erfahren Sie, wie Sie mithilfe der intelligenten Import- und Konvertierungsfunktionen von Forms Experience Builder vorhandene Dokumente, PDFs und Bilder in interaktive digitale Formulare umwandeln können.
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: 7268c4be-1e4a-4d31-aa76-9076d7ee83ce
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Intelligente Import- und Konvertierungsfunktionen

>[!NOTE]
>
> Forms Experience Builder ist im Rahmen eines Early-Access-Programms verfügbar. Bevor Sie beginnen, stellen Sie sicher, dass Sie Zugriff angefordert haben und erhalten haben.

Mit der intelligenten Import- und Konvertierungsfunktion von Forms Experience Builder können Sie vorhandene Dokumente, PDFs und Bilder mithilfe von KI-gestützter Analyse und Konvertierung in moderne, interaktive digitale Formulare umwandeln.

## Unterstützte Quellformate

### PDF-Dokumente

**AcroForm PDFs:**

- Interaktive PDF forms mit Formularfeldern
- Statische PDFs mit formularähnlichen Layouts
- Mehrseitige Dokumente mit strukturiertem Inhalt

**XFA-basierte PDFs:**

- Ältere XFA-Formulare (XML-Forms-Architektur)
- Komplexe Geschäftsformulare mit erweiterten Layouts
- Regierungs- und Unternehmensformen

**Statische PDFs:**

- Gescannte Dokumente und Formulare
- Druckfertige Formulare ohne interaktive Elemente
- Dokumente mit formularähnlichen Strukturen

### Bilddateien

**Unterstützte Formate:**

- PNG, JPG, JPEG, GIF
- Scans von Papierformularen mit hoher Auflösung
- Screenshots von digitalen Formularen
- Handgezeichnete Skizzen und Drahtmodelle

**Bildqualitätsanforderungen:**

- Mindestens 300 DPI für die Texterkennung
- Klarer, lesbarer Text und Formularelemente
- Guter Kontrast zwischen Text und Hintergrund
- Korrekte Ausrichtung (nicht gedreht)

### Design-Dateien

**Figma-Designs:**

- Formularmodelle und -prototypen
- UI/UX-Design-Dateien
- Komponentenbasierte Formularlayouts

**Andere Designformate:**

- Adobe XD-Dateien
- Skizzendesigns
- Wireframe-Dokumente

## Importieren und Konvertieren

### Schritt 1: Zugriff auf die Importfunktion

1. Öffnen Sie Forms Experience Builder
2. Klicken Sie auf das Anlagensymbol in der Benutzeroberfläche
3. Wählen Sie die Option „Importieren und konvertieren“
4. Quelldatei auswählen

### Schritt 2: Dokument hochladen

**Für PDF-Dateien:**

1. PDF-Dokument auswählen
2. Warten Sie, bis die KI die Struktur analysiert hat
3. Überprüfen der erkannten Formularelemente
4. Bestätigen der Konvertierungseinstellungen

**Für Bilddateien:**

1. Bild hochladen (PNG, JPG usw.)
2. Die KI analysiert Layout und Text
3. Überprüfen der erkannten Formularfelder
4. Nehmen Sie bei Bedarf Anpassungen vor

**Für Design-Dateien:**

1. Hochladen der Design-Datei
2. Die KI extrahiert Formularkomponenten
3. Überprüfen der konvertierten Elemente
4. Anpassen der Formularstruktur

### Schritt 3: Überprüfen und anpassen

Nach der ersten Konversion:

1. **Erkannte Felder überprüfen**: Überprüfen Sie, ob alle Formularelemente korrekt identifiziert wurden
2. **Feldtypen anpassen**: Ändern von Feldtypen (Text, Dropdown, Kontrollkästchen usw.)
3. **Validierung hinzufügen**: Einrichten von Feldvalidierungsregeln
4. **Anpassen des Stils**: Anwenden von Designs und Branding
5. **Testfunktion**: Überprüfen des Formularverhaltens und der Logik

## Konversionsbeispiele

### PDF-Formularkonvertierung

**Ursprüngliches PDF-Formular:**

- Statisches Kontaktformular mit Namen-, E-Mail- und Telefonfeldern
- Abschnitt „Unternehmensinformationen“
- Kommentarbereich

**Konvertiertes adaptives Formular:**

- Interaktive Textfelder mit Validierung
- Dropdown für Unternehmensgröße
- Mehrzeiliger Textbereich für Kommentare
- Senden-Schaltfläche mit E-Mail-Integration

### Konvertierung von Bildern in Formulare

**Originalbild:**

- Foto eines Registrierungsformulars in Papierform
- Handgeschriebenes Formular mit Kontrollkästchen
- Mehrere Abschnitte für verschiedene Informationen

**Konvertiertes adaptives Formular:**

- Dem Layout entsprechende digitale Textfelder
- Interaktive Kontrollkästchen und Optionsfelder
- Organisierte Abschnitte mit ordnungsgemäßem Abstand
- Responsives Design für Mobilgeräte

### Konvertierung der Designdatei

**Original Figma Design:**

- Modernes UI-Mockup mit Formularkomponenten
- Markenstil und Farben
- Komplexes Layout mit mehreren Bereichen

**Konvertiertes adaptives Formular:**

- Pixelgenaue Nachbildung des Designs
- Interaktive Formularelemente
- Responsives Verhalten auf allen Geräten
- Markenkonsistentes Styling

## Erweiterte Konvertierungsfunktionen

### Intelligente Felderkennung

Die KI erkennt und konvertiert automatisch:

- **Textfelder**: Ein- und mehrzeilige Textbereiche
- **Auswahlfelder**: Dropdown-Listen, Optionsfelder, Kontrollkästchen
- **Datumsfelder**: Datumsauswahl mit richtiger Formatierung
- **Zahlenfelder**: Numerische Eingaben mit Validierung
- **Datei-Uploads**: Bereiche für das Hochladen von Dokumenten und Bildern

### Beibehaltung des Layouts

Die Konversion behält Folgendes bei:

- **Originalstruktur**: Behält das Layout und die Organisation bei
- **Visuelle Hierarchie**: Behält Überschriften und Abschnittsumbrüche bei
- **Abstand und Ausrichtung**: Behält den korrekten Formularabstand bei
- **Markenelemente**: Behält Logos und Stilelemente bei

### Intelligente Validierung

Fügt automatisch die entsprechende Validierung hinzu:

- **E-Mail-Felder**: Validierung des E-Mail-Formats
- **Telefonnummern**: Überprüfung des Telefonnummernformats
- **Erforderliche Felder**: Markiert Pflichtfelder
- **Datumsbereiche**: Legt die entsprechenden Datumsbeschränkungen fest

## Best Practices für Import und Konversion

### Quelldokumente werden vorbereitet

**Für PDF-Dateien:**

- Sicherstellen, dass Text auswählbar ist (nicht nur Bilder)
- Verwenden von hochwertigen Scans für statische PDFs
- Organisieren von Inhalten in logischen Abschnitten
- Einschließen von Feldkennzeichnungen zum Löschen

**Für Bilder:**

- Verwenden Sie hochauflösende Bilder (300+ DPI)
- Sicherstellen von gutem Kontrast und Lesbarkeit
- Verdrehte oder verzerrte Bilder vermeiden
- Alle Formularelemente in das Bild einbeziehen

**Für Design-Dateien:**

- Verwenden einer konsistenten Benennung für Formularkomponenten
- Logisches Organisieren von Ebenen
- Einschließen aller erforderlichen Formularelemente
- Export in hoher Qualität

### Optimierung nach der Konversion

**Überprüfen und Testen:**

- Testen aller Formularfelder und Validierung
- Überprüfen der Reaktionsfähigkeit auf Mobilgeräten
- Prüfen der Barrierefreiheit
- Funktion der Testübermittlung

**Anpassen und Verbessern:**

- Hinzufügen von Geschäftslogik und bedingten Regeln
- Implementieren einer ordnungsgemäßen Fehlerbehandlung
- Konfigurieren von Übermittlungsendpunkten
- Anwenden von Markenstilen und Designs

## Fehlerbehebung bei Konversionsproblemen

### Häufige Probleme

**Schlechte Felderkennung:**

- Verbesserung der Bildqualität oder der Textklarheit in PDF
- Manuelles Anpassen der Feldtypen nach der Konvertierung
- Verwenden von aussagekräftigeren Feldbezeichnungen in der Quelle

**Layout-Probleme:**

- Abstand und Ausrichtung manuell anpassen
- Responsive Design-Prinzipien verwenden
- Testen auf verschiedenen Bildschirmgrößen

**Fehlende Elemente:**

- Manuelles Hinzufügen fehlender Felder
- Erneuter Import mit besserer Quellqualität
- Inkrementellen Konversionsansatz verwenden

### Hilfe wird abgerufen

Bei Konvertierungsproblemen:

- Lesen Sie die [Häufig gestellten Fragen zu Forms Experience Builder](forms-experience-builder-frequently-asked-questions.md)
- Lesen Sie [&#x200B; Erste Schritte &#x200B;](forms-experience-builder-getting-started.md)
- Wenden Sie sich an Ihren Systemadministrator, um technische Unterstützung zu erhalten

## Verwandte Artikel

- [Übersicht über Forms Experience Builder](product-overview.md)
- [Erste Schritte mit Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Bereitstellen und Konfigurieren von Forms Experience Builder](deploy-forms-experience-builder.md)
- [Formularübermittlung und -integration](form-submission-integration.md)
- [Häufig gestellte Fragen](forms-experience-builder-frequently-asked-questions.md)
