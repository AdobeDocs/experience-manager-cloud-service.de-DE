---
title: Optionsfeldobjekt im Editor für interaktive Kommunikation
description: Mit dem Optionsfeldobjekt im Editor für interaktive Kommunikation in AEM Forms können Autorinnen und Autoren Benutzenden eine Reihe von sich gegenseitig ausschließenden Auswahlmöglichkeiten präsentieren, d. h., es kann jeweils nur eine Option ausgewählt werden.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 9%

---


# Optionsfeldobjekt im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit **Komponente „Optionsschaltfläche** im Editor für interaktive Kommunikation (IC) können Autoren Benutzern eine Reihe sich gegenseitig ausschließender Optionen präsentieren, d. h., es kann jeweils nur eine Option ausgewählt werden. Dies macht ihn ideal für Anwendungsfälle wie Ja/Nein-Fragen, Geschlechterauswahl, Bewertungsstufen oder vordefinierte Kategorienantworten.
Optionsschaltflächen sind intuitiv, einfach zu konfigurieren und können an Back-End-Datenmodelle gebunden werden, um eine nahtlose Datenerfassung und -integration zu ermöglichen.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/radio.png)

## &#x200B;2. Eigenschaften

Das Optionsschaltflächen-Objekt enthält mehrere konfigurierbare Eigenschaften:

2.1. Grundfeld

- **Name:** Eine eindeutige Kennung für das Feld. Sie wird für Verweise innerhalb von Datenmodellen, Regeln und Geschäftslogik verwendet.

- **Umschalten** Ermöglicht die Definition jeder auswählbaren Auswahl in der Schaltflächengruppe. Jeder Umschalter stellt einen möglichen Wert dar.

- **Beschriftung:** Die Beschriftung, die der Optionsschaltflächengruppe zugeordnet ist, um den Benutzer zu leiten.

- **Reserve:** Optionaler Fallback-Wert, wenn keine Auswahl getroffen oder die Datenbindung leer ist.

2.2. Lage

Beschreibung: Steuert die räumliche Platzierung der Optionsfeldgruppe im Layout.

**Einstellungen:**

- **X- und Y-Koordinaten**

- **Höhe und Breite** (für responsives Layout in mm oder % definiert)

2.3. Spanne

Definieren Sie den Abstand um das Textfeld:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

2.4. Vorhandensein

- **Beschreibung:** Bestimmt die Sichtbarkeit des Optionsfeldobjekts zur Laufzeit.

- **Optionen:**

   - **Sichtbar:** Benutzern angezeigt und belegt Platz.

   - **Ausgeblendet (Leerzeichen werden beibehalten):** nicht sichtbar, behält aber den Layout-Abstand bei.



2.5. Datenbindung

- **Beschreibung:** Verbindet die Optionsschaltflächengruppe mit einem Datenmodell zum Erfassen der ausgewählten Option.

- **Bindungstypen:**

   - **Benutzername:** Verwendet den zugewiesenen Feldnamen als Referenz für die Bindung.

   - **Globale Daten verwenden:** Bindet das Feld an ein globales Datenmodell oder Schemaelement.

   - **Keine Datenbindung:** Die Optionsschaltflächen-Auswahl ist an keine Datenquelle gebunden und wird nur für das Verhalten der Benutzeroberfläche verwendet.

## &#x200B;3. Verwendung

Die Optionsschaltflächen-Komponente eignet sich gut für Szenarien, in denen Benutzende nur einen Wert aus einer Liste auswählen müssen. Typische Anwendungsfälle sind:

- Auswählen einer bevorzugten Kommunikationsmethode (E-Mail / Telefon / SMS)

- Bestätigen binärer Entscheidungen (Ja/Nein)

- Auswahl aus eingeschränkten Optionen (z. B. Geschlecht, Familienstand)

- Angabe der Zufriedenheitsgrade oder der Einverständnisskala (z. B. Nicht einverstanden / Neutral / Einverstanden)

Autoren können verwandte Optionsschaltflächen gruppieren und in Layout-Containern positionieren, um eine konsistente Ausrichtung zu gewährleisten. Je nach visuellen Design-Anforderungen können Beschriftungen inline oder über den Schaltflächen positioniert werden.

## 4. Best Practices

- Begrenzen Sie die Anzahl der Optionen auf 5 oder weniger, um zu vermeiden, dass der Benutzer überfordert wird.

- Verwenden Sie klare und knappe Beschriftungen, um zu beschreiben, was der Benutzer auswählt.

- Wählen Sie gegebenenfalls die häufigste oder sicherste Option vorab aus.

- Vermeiden Sie die Verwendung von Optionsschaltflächen, wenn Benutzende mehr als eine Option auswählen dürfen, verwenden Sie stattdessen Kontrollkästchen.

- Binden Sie Optionsschaltflächen bei der Integration mit Backend-Datenmodellen direkt an Schemaknoten.

- Verwenden Sie konsistente Abstände und Ausrichtung für eine bessere visuelle Klarheit, insbesondere in mobilfreundlichen Layouts.

Das Optionsfeldobjekt im Editor für interaktive Kommunikation ist eine grundlegende Eingabekomponente, die Endbenutzern eine saubere, strukturierte Entscheidungsfindung bietet. Wenn sie mit klaren Bezeichnungen, durchdachten Abständen und Datenbindung konfiguriert ist, sorgt sie für eine zuverlässige Datenerfassung und ein reibungsloseres Benutzererlebnis für Formulare, Umfragen und Onboarding-Workflows.


