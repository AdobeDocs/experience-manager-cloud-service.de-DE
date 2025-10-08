---
title: Bildfeldkomponente im Editor für interaktive Kommunikation
description: Mit der Bildfeldkomponente im Editor für interaktive Kommunikation in AEM Forms können Autorinnen und Autoren Bilder in ein Kommunikations-Layout einfügen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 10%

---


# Bildfeldkomponente im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit der Bildfeldkomponente im Editor für interaktive Kommunikation können Autoren Bilder in ein Kommunikations-Layout einfügen. Es eignet sich ideal für Anwendungsfälle wie Fotoidentifizierung, Dokumentenüberprüfung oder visuelle Validierung, bei denen die Anzeige eines Bildes für den Endbenutzer unerlässlich ist.

Diese Komponente unterstützt gängige Formate wie **JPEG** und **PNG** und bietet flexible Konfigurationsoptionen, mit denen definiert werden kann, wie das Bild angezeigt, gespeichert und gestaltet wird. Autoren können dem Bildfeld auch **einen Namen oder eine Beschriftung zuweisen** wodurch das Layout klarer und besser organisiert wird.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/imagefield.png)

## &#x200B;2. Eigenschaften

Die Bildfeldkomponente enthält mehrere konfigurierbare Eigenschaften:

2.1. Grundfeld

- **Name:** Definieren Sie eine eindeutige Kennung für das Feld, die zum Verweisen auf Datenmodelle und Regeln verwendet wird.

- **Beschriftung:** Zeigt den Benutzern die Beschriftung an, die auf der Benutzeroberfläche angezeigt wird.

- **Bild auswählen:** Erlauben Sie dem Autor, ein Bild mit dieser Eigenschaft hochzuladen, die häufig für Logos, IDs oder andere visuelle Elemente verwendet wird.

- **Reservebild:** Definieren Sie die Ausrichtung des Bildes (links, rechts, oben oder unten) oder geben Sie eine **benutzerdefinierte Position)** Einheiten wie Millimeter (z. B. 20 mm) an.

2.2. Lage

Steuert die räumliche Platzierung des Bildes im Layout.

- X- und Y-Koordinaten

- Höhe und Breite (in mm)

2.3. Spanne

Definieren Sie den Abstand um das Textfeld:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

2.4. Erscheinungsbild

Erscheinungsbild: Definiert den visuellen Stil des Bildfelds, wählen Sie Vorgaben wie umrandet, flach oder erhöht und passen Sie mit Füllfarbe, Strichbreite und Eckstil (abgerundet oder scharf) an.

2.5. Vorhandensein

Bestimmt die Sichtbarkeit der Bildkomponente zur Laufzeit.

- Visible

- Ausgeblendet (Platz einsparend)

2.6. Datenbindung

Verknüpfen Sie das Bildfeld mit einer Datenquelle, um dynamische Bildinhalte innerhalb der Kommunikation abzurufen und anzuzeigen.

**Datenbindungstyp:**, wie das Bildfeld eine Verbindung zur zugrunde liegenden Datenstruktur oder zum Schema herstellt.

**Benutzername:** Bindet das Bildfeld unter Verwendung des im Datenmodell oder Schema angegebenen Feldnamens, sodass das Bild zur Laufzeit dynamisch ausgefüllt werden kann.

**Globale Daten verwenden:** Verbindet das Bildfeld mit globalen Daten, die über die gesamte Kommunikation hinweg gemeinsam genutzt werden, und stellt so die Konsistenz der visuellen Inhalte sicher.

**Keine Datenbindung:** das Feld von allen Backend-Daten getrennt, ideal für Fälle, in denen ein statisches Bild angezeigt wird oder wenn das Bild ausschließlich über Benutzeroberflächeneinstellungen gesteuert wird.

## &#x200B;3. Verwendung

Das Bildfeld ist in Kontexten nützlich, in denen eine visuelle Inhaltsübermittlung erforderlich ist. Häufige Anwendungsszenarien umfassen:

- Hochladen des ID-Korrekturabzugs (Pass, Lizenz)

- Einreichen von Profilen oder persönlichen Fotos

- Visuelles Anhängen von Begleitdokumenten

Autoren können das Feld zur Ausrichtung in Teilformularen oder Layout-Containern platzieren und benutzerdefinierte Validierungsregeln verwenden, um die akzeptierten Dateitypen und -größen zu steuern.

## 4. Best Practices

- Verwenden Sie bei der Aufforderung zum Hochladen von Bildern klare Beschriftungen oder Anweisungen.

- Begrenzen Sie die Dateigröße und Formate durch die Validierung der Leistung.

- Sicherstellen, dass Fallback-Bilder (reserviert) für Barrierefreiheit verfügbar sind.

- Binden des Felds an einen aussagekräftigen Schemapfad bei der Integration mit dem Backend

Die Bildfeldkomponente im Editor für interaktive Kommunikation ist eine vielseitige Komponente, die die Formularinteraktivität verbessert, indem sie das Hochladen visueller Inhalte ermöglicht. Wenn sie mit Stilen, Validierung und Datenbindung entwickelt wurde, unterstützt sie ein nahtloses Benutzererlebnis und eine effiziente Datenerfassung für bildbasierte Übermittlungen.




