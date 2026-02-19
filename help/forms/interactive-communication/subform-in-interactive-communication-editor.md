---
title: Teilformular im Editor für interaktive Kommunikation
description: Teilformulare im Editor für interaktive Kommunikation verwalten Layouts, steuern die Objektpositionierung und definieren, wie Inhalte über Seiten hinweg fließen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 2%

---


# Teilformular im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

## &#x200B;1. Einführung

Ein Teilformular im Editor für interaktive Kommunikation ist ein Container-Objekt, das zum Gruppieren von Feldern, Objekten und Komponenten in einem logischen Abschnitt verwendet wird. Es hilft bei der Verwaltung von Layouts, der Kontrolle der Objektpositionierung und der Definition, wie Inhalte über Seiten fließen. Teilformulare sind für das Erstellen strukturierter, wiederverwendbarer und responsiver Kommunikation unerlässlich, insbesondere wenn es um dynamische oder wiederholte Inhalte geht.

Durch die Verwendung von Teilformularen können Autoren die Konsistenz gewährleisten, die Paginierung verwalten und ganze Abschnitte an strukturierte Datenquellen binden.

## &#x200B;2. Eigenschaften

2.1 Formularentwurf-Layouts

- **Festes Layout:**-Objekte behalten exakte Positionen auf der Seite bei. Am besten geeignet für statische Entwürfe, bei denen eine präzise Platzierung erforderlich ist (z. B. Rechnungen oder offizielle Briefe).

- **Fließfähiges Layout:** Objekte passen sich dynamisch an, basierend auf der Inhaltslänge und der Bildschirmgröße. Geeignet für Kommunikationen, die responsives Design oder unterschiedliche Datenlängen erfordern.

2.2 Positionierung des Teilformulars

- **Paginierung:** Steuern Sie, wie Teilformulare über Seiten verteilt werden. Zu den Optionen gehören das Zusammenhalten von Teilformularen oder das Zulassen von Seitenumbrüchen innerhalb derselben.

- **Position:** Geben Sie an, ob das Teilformular relativ zum übergeordneten Container platziert werden soll oder natürlich innerhalb des Layouts fließen soll.

- **Erscheinungsbild** Definieren Sie Hintergrund, Rahmen und Stile für das Teilformular, um Inhalte visuell zu trennen.

- **Präsenz** Konfigurieren Sie Sichtbarkeitseinstellungen - sichtbar, ausgeblendet oder bedingt - je nach Geschäftsregeln oder Datenwerten.

2.3 Datenbindung

- Teilformulare können direkt an Knoten **Formulardatenmodell (FDM) oder**-Arrays gebunden werden.

- Durch die Bindung kann sich das Teilformular dynamisch für jeden Datensatz in einer Sammlung wiederholen (z. B. mehrere Richtlinien, Transaktionen oder Adressen).

- Unterstützt sowohl eine statische als auch eine dynamische Inhalts-Population basierend auf der Datenstruktur.

## &#x200B;3. Verwendung

Teilformulare werden häufig verwendet für:

- Strukturieren von Dokumenten in Abschnitte wie Kopf- und Textkörper sowie Fußzeile.

- Wiederholte Inhalte wie Tabellen, Einzelaufstellungen von Rechnungen oder Listen von Richtlinien.

- Die Seitenumbrüche so verwalten, dass gruppierte Inhalte zusammenbleiben.

- Bedingte Anzeige von Abschnitten basierend auf Regeln oder Datenwerten.

- Anwenden der Layout-Steuerung (fest oder fließend) je nach Kommunikationstyp.

Autoren können ein Teilformular aus der Objektbibliothek in die Arbeitsfläche ziehen und sein Layout, seine Positionierung und Bindung über das Bedienfeld Eigenschaften anpassen.

## 4. Best Practices

- **Wählen Sie das Layout mit Bedacht** Verwenden Sie das feste Layout für Formulare, für die eine exakte Platzierung erforderlich ist, und das fließende Layout für dynamische, datengesteuerte Kommunikation.

- **Sorgfältiges Binden von Sammlungen:** Binden Sie für Listen oder Arrays Teilformulare direkt mit FDM-Sammlungen in Vorlagenzeilen.

- **Seitenumbruch optimieren** Vermeiden Sie umständliche Umbrüche, indem Sie verwandte Objekte in einem Teilformular gruppieren.

- **Bedingtes Vorhandensein verwenden** Ausblenden oder Anzeigen von Teilformularen dynamisch basierend auf Datenwerten.

- **Hierarchie beibehalten:** Verschachteln Sie Teilformulare logisch, um die Verwaltung komplexer Layouts zu vereinfachen.

- **Testen mit unterschiedlichen Daten:** Vorschau mit kurzen, langen und leeren Datensätzen, um sicherzustellen, dass das Design korrekt angepasst wird.

Durch die effektive Nutzung von Teilformularen können Autoren sauberere Layouts erzielen, die Kontrolle über dynamische Inhalte verbessern und sicherstellen, dass sich die Kommunikation nahtlos an datengesteuerte und statische Szenarien anpasst.
