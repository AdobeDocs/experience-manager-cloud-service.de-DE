---
title: Datums-/Uhrzeitfeld im Editor für interaktive Kommunikation
description: Datums-/Uhrzeitfeldkomponente im Editor für interaktive Kommunikation in AEM Forms, mit der Autorinnen und Autoren Felder einfügen können, in denen Benutzende Datums- und/oder Uhrzeitwerte auswählen oder eingeben können.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 8%

---


# Datums-/Uhrzeitfeld-Komponente im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit **Komponente „Datum/Uhrzeit** im Editor für interaktive Kommunikation (IC) können Autoren Felder einfügen, in denen Benutzer Datums- und/oder Zeitwerte auswählen oder eingeben können. Diese Komponente wird häufig verwendet, um Informationen wie Geburtsdatum, Terminpläne, Buchungs-Slots oder Ausstellungs-/Ablaufdaten von Dokumenten zu erfassen.

Das Feld unterstützt verschiedene Formatierungsoptionen (z. B. TT/MM/JJJJ, 24-Stunden- oder 12-Stunden-Formate), Validierungsbeschränkungen und die Anpassung des Erscheinungsbilds an das Kommunikationsdesign. Es verbessert das Benutzererlebnis, indem Fehler bei der manuellen Eingabe reduziert werden und die Konsistenz bei der Datenerfassung gefördert wird.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/datetime.png)

## &#x200B;2. Eigenschaften

Die Komponente „Datum/Uhrzeit-Feld“ enthält mehrere konfigurierbare Eigenschaften:

2.1. Grundfeld

- **Name:** Eine eindeutige Kennung für das Feld. Wird für Referenzierungen in Regeln, Ausdrücken und Datenbindungen verwendet.

- **Beschriftung:** Die Bezeichnung, die neben dem Feld angezeigt wird, um den Zweck anzugeben (z. B. „Geburtsdatum„).

- **Datum** Ermöglicht Benutzenden die Auswahl oder Eingabe eines Kalenderdatums.

- **Time:** Ermöglicht die Eingabe oder Auswahl bestimmter Zeitwerte, falls konfiguriert.

- **Reserve:** Ein Fallback-Wert, der angezeigt wird, wenn keine Eingabe angegeben wird. Dies ist für schreibgeschützte oder Druckszenarien nützlich.

- **Erscheinungsbild** Wählen Sie einen visuellen Stil aus, z. B. unterstrichen, umrandet oder flach für eine konsistente Darstellung der Benutzeroberfläche.

2.2. Typografie

Steuert den Stil des Textes innerhalb des Datums-/Uhrzeitfelds:

- **Schriftartvariante:** Optionen umfassen je nach Design-Anforderungen Normal, Fett oder Kursiv.

- **Schriftgröße:** Standardeinstellung ist 10 pt, um die Konsistenz mit dem Formularlayout zu wahren.

2.3. Lage

- **Beschreibung:** Definiert die Platzierung des Datums-/Uhrzeitfelds im Formularlayout.

- **Einstellungen:**

   - **X- und Y-Koordinaten**

   - **Höhe und Breite** (gemessen in mm oder Pixeln) für die präzise Größenbestimmung des Felds.

2.4. Spanne

Definiert Abstände um das Feld für saubere Ausrichtung und Layout-Flexibilität:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

2.5. Erscheinungsbild

Definiert den Stil des Containers, um visuelle Konsistenz und Klarheit zu gewährleisten:

- **Fill** Hintergrundfarbe des Felds.

- **Kontur** Rahmenfarbe um das Feld.

- **Breite** Die Rahmenstärke.

- **Style:** Rahmentypen wie einfarbig, gestrichelt oder keine.

- **Kanten** Wählen Sie je nach Formulardesign aus scharfen oder abgerundeten Ecken.

2.6. Vorhandensein

Bestimmt, wie sich das Feld zur Laufzeit verhält:

- **Sichtbar:** Das Feld wird Benutzern angezeigt und belegt Layout-Bereich.

- **Ausgeblendet (Platz bleibt):** Feld ist nicht sichtbar, aber im Layout ist immer noch Platz dafür reserviert.

2.7. Datenbindung

Verknüpft das Feld mit einer Datenquelle, um Werte zu speichern oder abzurufen.

- **Datenbindungstyp:**, wie das Feld eine Verbindung zu Daten herstellt.

- **Benutzername:** das Feld unter Verwendung des im Schema definierten Feldnamens.

- **Globale Daten verwenden:** Verbindet das Feld mit Daten auf globaler Ebene, die über die gesamte Kommunikation hinweg freigegeben werden.

- **Keine Datenbindung:** Feld ist mit keinen Backend-Daten verbunden (nur für visuelle oder berechnete Werte verwendet).

## &#x200B;3. Verwendung

Das Datums-/Uhrzeitfeld eignet sich ideal für Szenarien, in denen konsistente zeitliche Daten erforderlich sind. Häufige Anwendungsszenarien umfassen:

- Geburtsdatum, Termindatum oder Ereigniszeit erfassen

- Problem-/Ablaufdatum des Protokolldokuments

- Versand- oder Abholautomaten auswählen

- Transaktionszeitstempel aufzeichnen

Autoren können das Feld mit Layout-Containern, Validierungen oder bedingten Regeln kombinieren, um das Format, die erforderlichen Felder und die kontextsensitive Sichtbarkeit zu steuern.

## 4. Best Practices

- Verwenden Sie klare Beschriftungen wie „Datum auswählen“ oder „Terminzeit“, um Benutzer zu leiten.

- Aktivieren Sie die Datums-/Uhrzeitauswahl, um eine bessere Benutzerfreundlichkeit und weniger Eingabefehler zu erzielen.

- Wenden Sie bei Bedarf Formatbeschränkungen an (z. B. nur für zukünftige Datumsangaben).

- Geben Sie einen Reservewert für Barrierefreiheit oder Druckausfall an.

- Halten Sie Typografie und Erscheinungsbild mit dem gesamten Formularentwurf konsistent.

- Binden Sie das Feld an einen gültigen Schemapfad, um eine ordnungsgemäße Datenerfassung und -verarbeitung sicherzustellen.

Die Komponente „Datum/Uhrzeit-Feld“ im Editor für interaktive Kommunikation ist eine leistungsstarke und benutzerfreundliche Komponente, die die zeitbasierte Eingabe optimiert. Mit der richtigen Konfiguration für Stil, Datenverarbeitung und Layout-Steuerelemente ermöglicht es saubere, zuverlässige und intuitive Formularerlebnisse sowohl für Benutzer als auch für Backend-Systeme.

