---
title: Teilformularkomponente im Editor für interaktive Kommunikation
description: Mit der Teilformularkomponente im Editor für interaktive Kommunikation in AEM Forms können Sie mehrere Formularelemente flexibel und strukturiert organisieren.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 60809974-1a39-4e69-9aa5-df9936a26362
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 2%

---

# Teilformularkomponente im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

## &#x200B;1. Einführung

Die **Teilformular**-Komponente im Editor für interaktive Kommunikation (IC) fungiert als dynamischer Layout-Container, mit dem Sie mehrere Formularelemente flexibel und strukturiert organisieren können. Sie wird häufig verwendet, um verwandte Felder zu gruppieren, wiederholte Abschnitte zu erstellen oder verschachtelte Datenstrukturen zu definieren, um das Benutzererlebnis und die Datenbindung zu verbessern.

Teilformulare können so konfiguriert werden, dass sie in verschiedenen Layouts, z. B. von oben nach unten oder von links nach rechts, fließen, wodurch sie sich ideal für komplexe Formularentwürfe und wiederverwendbare Abschnitte eignen.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/subform.png)

## &#x200B;2. Eigenschaften

2.1 Grundlegende Eigenschaften

- **Name:** Eindeutige Kennung für das Teilformular, das zum Referenzieren, für Datenmodelle und Geschäftsregeln verwendet wird.

- **Inhalt:** Definiert, wie Elemente innerhalb des Teilformulars angeordnet werden.

   - **Positioniert** Absolute Platzierung untergeordneter Elemente mithilfe von X- und Y-Koordinaten.

   - **Fließend (von oben nach unten):** Elemente vertikal angeordnet.

   - **Fließend (von links nach rechts):** Elemente horizontal angeordnet.

2.2 Position

- **Beschreibung:** Bestimmt die Platzierung des Teilformulars im Kommunikations-Layout.

- **Einstellungen:**

   - X- und Y-Koordinaten (in mm)

   - Breite und Höhe (in mm)

2.3 Erscheinungsbild

- **Fill:** Gibt die Hintergrundfarbe des Teilformularbereichs an.

- **Strich:** die Rahmenfarbe.

- **Breite:** Legt die Rahmenstärke fest.

- **Style:** Sie aus visuellen Vorgaben wie „flach“, „umrandet“ oder „erhöht“ aus.

- **Kanten:** Bestimmt den Eckstil - abgerundet oder scharf.

2.4 Vorhandensein

- **Beschreibung:** Steuert die Sichtbarkeit des Teilformulars während der Laufzeit.

- **Optionen:**

   - **Sichtbar:** immer angezeigt.

   - **Ausgeblendet:** nicht angezeigt, aber der Platz bleibt im Layout erhalten.

2.5 Datenbindung

- **Datenbindungstyp:** verknüpft das Teilformular mit einer Datenstruktur (normalerweise XML oder JSON).

- **Benutzername:** Binden von Daten unter Verwendung des zugewiesenen Namens des Teilformulars.

- **Globale Daten verwenden:** Verbindet das Teilformular mit einem globalen Schemapfad zur gemeinsamen Datennutzung.

- **Keine Datenbindung:** Teilformular speichert kein externes Datenmodell und interagiert nicht mit diesem.

## &#x200B;3. Verwendung

Teilformulare sind in Szenarien, in denen Feldergruppen gruppiert, verschachtelt oder wiederholt werden müssen, von entscheidender Bedeutung. Typische Anwendungen sind:

- Organisieren von Adressblöcken (z. B. Straße, Stadt, Postleitzahl)

- Wiederholungsabschnitte für Zeileneinträge oder mehrere Einträge

- Strukturieren von bedingter Formularlogik mithilfe von Sichtbarkeit und Regeln
Teilformulare können auch als Container für die Drag-and-Drop-Design-Ausrichtung sowohl in statischen als auch in dynamischen Layouts verwendet werden.

## 4. Best Practices

- Wählen Sie das richtige Layout (Fluss vs. Position) basierend auf Design- und Datenanforderungen.

- Verwenden Sie aussagekräftige Namen, um die Datenintegration und die Regelreferenzierung zu vereinfachen.

- Formatieren Sie Unterformulare, um gruppierte Abschnitte visuell zu unterscheiden.

- Stellen Sie bei Verwendung von wiederholten Teilformularen eine ordnungsgemäße Datenbindung an Array-Strukturen sicher.

- Wenden Sie bedingte Sichtbarkeitsregeln an, um das Benutzererlebnis in komplexen Formularen zu optimieren.

Die **Teilformular**-Komponente im Editor für interaktive Kommunikation bietet eine leistungsstarke Möglichkeit, komplexe Formularlayouts zu strukturieren und zu steuern. Unabhängig davon, ob Sie Eingabefelder organisieren, dynamische Inhalte verwalten oder einen modularen Entwurf ermöglichen, verbessern Teilformulare in allen Dokumentvorlagen sowohl die Benutzerfreundlichkeit als auch die Wartungsfreundlichkeit.
