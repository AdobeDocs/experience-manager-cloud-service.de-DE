---
title: Tabellenobjekt im Editor für interaktive Kommunikation
description: Mit dem Tabellenobjekt im Editor für interaktive Kommunikation in AEM Forms können Autorinnen und Autoren auf einfache Weise anpassbare Tabellen in Kommunikationsvorlagen einfügen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 8%

---


# Tabellenobjekt im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit dem Tabellenobjekt im Editor für interaktive Kommunikation (IC) können Autoren auf einfache Weise anpassbare Tabellen in Kommunikationsvorlagen einfügen. Dieses Objekt unterstützt tabellarische Datendarstellungen für Anwendungsfälle wie Zusammenfassungen, Elementauflistungen, strukturierte Eingaben oder Vergleichslayouts.

Autoren können die Tabellenkomponente per Drag-and-Drop auf die Arbeitsfläche ziehen, die Anzahl der Zeilen und Spalten konfigurieren und Optionen wie Kopf- und Fußzeilen einschließen oder die Layout-Richtung festlegen. Tabellen können als Standardvorlagen definiert werden, um die Konsistenz über mehrere Kommunikationen hinweg zu gewährleisten.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/table.png)

## &#x200B;2. Eigenschaften

Das Tabellenobjekt enthält mehrere konfigurierbare Eigenschaften, mit denen Autoren das Verhalten und das Erscheinungsbild der Tabelle anpassen können:


2.1 Basisfeld

- **Name:** Eindeutige Kennung für die Tabelle. Dieser Name wird intern für die Referenzierung der Tabelle in Datenmodellen und Logik verwendet.

- **Zeilen:** Gibt die Anzahl der Inhaltszeilen an (ohne Kopf- und Fußzeile).

- **Spalten:** die Anzahl der Spalten in der Tabelle.

- **Kopfzeile:** Option zum Einschließen einer Kopfzeile am Anfang der Tabelle für Spaltentitel.

- **Fußzeile:** Option, um eine Fußzeile für Gesamtwerte oder Zusammenfassungswerte einzuschließen.

- **Als Standard festlegen:** Ermöglicht Benutzern das Speichern der aktuellen Konfiguration als Standardtabellenvorlage für die zukünftige Verwendung.

- **Layout-Richtung** Definiert, wie Zeilen ausgefüllt werden - normalerweise von links nach rechts festgelegt.

2.2 Position

- **Beschreibung:** Steuert die Platzierung der Tabelle innerhalb des Layouts.

- **Einstellungen:**

   - **X- und Y-Koordinaten** Legt die horizontale (X) und vertikale (Y) Position der Tabelle auf der Arbeitsfläche fest.

   - **Höhe und Breite:** Definiert die Gesamtgröße der Tabelle (in mm), sodass der Platz flexibel zugewiesen werden kann.

2.3 Erscheinungsbild

**Erscheinungsbild:** Legt den visuellen Stil der Tabelle fest. Autoren können aus vordefinierten Vorgaben auswählen, z. B. Rahmen, flach oder erhöht.

- **Fill** Hintergrundfarbe der Tabelle(n).

- **Kontur** Rahmenfarbe um die Tabelle oder bestimmte Zellen.

- **Breite** Die Stärke der Rahmenlinien.

- **Style:** Wählen Sie Kantentypen - abgerundete Ecken oder scharfe Ecken.

- **Kanten** Konfigurieren Sie die Sichtbarkeit der Zellenränder und des Eckenradius.

2.4 Vorhandensein

- **Beschreibung:** Bestimmt die Sichtbarkeit der Tabelle zur Laufzeit.

- **Optionen:**

   - **Sichtbar:** Zeigt die Tabelle normal in der Ausgabe an.

   - **Ausgeblendet:** Blendet die Tabelle aus, behält jedoch im Layout Platz bei.

2.5 Datenbindung

**Datenbindung:** Verbinden Sie die Tabelle mit einer Datenquelle (z. B. JSON, XML-Schema), um Zeilen und Spalten während der Generierung dynamisch mit Werten zu füllen. Dies ist nützlich für Einzelposten-Abrechnungen, Transaktionsdatensätze oder Produktlisten.

## &#x200B;3. Verwendung

Das Tabellenobjekt eignet sich ideal zur Anzeige von strukturierten oder sich wiederholenden Informationen. Typische Anwendungsfälle sind:

- Rechnungen und Rechnungen mit Artikelzeilen

- Richtlinien- oder Planvergleiche

- Zusammenfassungen von Profil- oder Kontodaten

- Produktkataloge oder Funktionsmatrizen

Autoren können die Anzahl der Zeilen und Spalten konfigurieren, bedingte Sichtbarkeit anwenden oder Daten binden, um dynamische Informationen anzuzeigen.

## 4. Best Practices

- Verwenden Sie zur besseren Lesbarkeit Kopfzeilen, um jede Spalte klar zu kennzeichnen.

- Wenden Sie gegebenenfalls Fußzeilen auf Gesamtwerte oder wichtige Hinweise an.

- Nutzen Sie die Datenbindung, um Zeilen basierend auf strukturierten Eingaben dynamisch zu füllen.

- Achten Sie auf einheitliche Stile und Abstände mithilfe der Einstellungen für Erscheinungsbild und Ränder.

- Stellen Sie beim Ausblenden einer Tabelle die Kontinuität des Layouts sicher, indem Sie festlegen, ob der Platz beibehalten werden soll oder nicht.

- Verwenden Sie Standardvorlagen, um tabellarische Inhalte für alle Dokumente zu standardisieren.

Das Table -Objekt im IC-Editor ist eine flexible, datenfreundliche Komponente, die strukturierte Inhalte in Ihrer Kommunikation unterstützt. Mit anpassbaren Layout-Optionen, Styling-Funktionen und leistungsstarker Datenbindung ermöglicht sie es Autoren, Informationen klar und effektiv darzustellen.


