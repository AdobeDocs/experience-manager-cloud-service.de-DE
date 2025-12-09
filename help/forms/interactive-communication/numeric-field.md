---
title: Komponente „Numerisches Feld“ im Editor für interaktive Kommunikation
description: Die Komponente „Numerisches Feld“ im Editor für interaktive Kommunikation in AEM Forms ermöglicht es Autorinnen und Autoren, numerische Eingaben von Benutzerinnen und Benutzern in einem kontrollierten Format zu erfassen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 7%

---


# Komponente „Numerisches Feld“ im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit der Komponente „Numerisches Feld“ im Editor für interaktive Kommunikation (IC) können Autoren numerische Eingaben von Benutzern in einem kontrollierten Format erfassen. Unabhängig davon, ob Sie Telefonnummern, PIN-Codes, Richtlinien-IDs oder Finanzdaten erfassen, stellt dieses Feld sicher, dass nur numerische Werte akzeptiert werden. Die Komponente unterstützt auch Stile, Formatierung, Validierung und Datenbindung, wodurch sie für strukturierte Kommunikation unerlässlich ist.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/numericfield.png)

## &#x200B;2. Eigenschaften

2.1 Basisfeld

- **Name:** Definieren Sie eine eindeutige Kennung für das Feld, die in Datenmodellen, Regeln und Skripten verwendet wird.

- **Beschriftung:** Zeigt den Benutzern die auf dem Bildschirm angezeigte Beschriftung an (z. B. „Kontaktnummer“ oder „Mitarbeiter-ID„).

- **Wert:** Ermöglicht Benutzern die Eingabe numerischer Werte wie Telefonnummern, IDs, Mengen oder Geldwerte.

- **Reservieren** Legen Sie die Ausrichtung des numerischen Werts fest - links, rechts, oben oder unten - oder geben Sie eine benutzerdefinierte Position mit Einheiten wie Millimetern (z. B. 20 mm) an.

- **Erscheinungsbild** Legen Sie für das Erscheinungsbild des Wertefelds „Keine“, „Durchgezogenes Feld“ oder „Unterstrichen“ fest, je nach gewünschtem visuellen Layout.

2.2 Typografie

Steuert den visuellen Stil der vom Benutzer eingegebenen numerischen Zeichen:

- **Schriftartvalidierung:** Sie Einschränkungen an, um sicherzustellen, dass nur gültige numerische Eingaben - wie Ganzzahlen, Dezimalzahlen oder Zahlenbereiche - basierend auf dem beabsichtigten Datentyp akzeptiert werden.

- **Schriftgröße:** Passen Sie die Größe des numerischen Textes mithilfe von Punktwerten wie 10 Punkt, 12 Punkt oder 20 Punkt an, um die Konsistenz und Lesbarkeit im gesamten Formular zu gewährleisten.

2.3 Position

Steuert die räumliche Position des numerischen Felds auf der Arbeitsfläche.

- **X- und Y-Koordinaten** Definieren Sie die exakte Feldplatzierung.

- **Breite und Höhe (in mm):** Bestimmt die Größe des Eingabefelds.

2.4 Spanne

Definiert einen Abstand um die Grenze des numerischen Felds für eine saubere Ausrichtung.

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

2.5 Erscheinungsbild

Formatiert den Container für numerische Eingabefelder entsprechend dem gewünschten visuellen Layout:

- **Fill** Legen Sie die Hintergrundfarbe des numerischen Felds fest. Auf diese Weise können Sie sie visuell von anderen Elementen trennen oder mit dem gesamten Design abgleichen.

- **Kontur** Fügen Sie Rahmen um das numerische Feld mit den folgenden anpassbaren Optionen hinzu:

- **Breite** Legen Sie die Rahmenstärke fest, um sie an die visuelle Hervorhebung anzupassen.

- **Stil:** Sie ein Rahmenmuster aus (einfarbig, gestrichelt oder gepunktet).

- **Edge:** Wählen Sie zwischen abgerundeten oder scharfen Ecken für den Rahmen.

- **Radius:** Passen Sie die Eckenrundung mithilfe spezifischer Radiuswerte (z. B. 4 px, 10 px) an, um das Erscheinungsbild des Felds zu erweichen oder zu schärfen.

2.6 Vorhandensein

Steuert die Sichtbarkeit des numerischen Felds zur Laufzeit.

- **Sichtbar:** Standardstatus; das Feld wird normal angezeigt.

- **Ausgeblendet (Platz bleibt):** Feld ist unsichtbar, aber im Layout wird Platz beibehalten.

2.7 Datenbindung

**Datenbindungstyp:** Verbindet das numerische Feld mit einer Datenquelle (XML oder JSON) für die Echtzeitintegration.

**Name verwenden:** Bindet das Feld an den eindeutigen Namen für die einfache Werterfassung.

**Globale Daten verwenden** Verknüpft das Feld mit einem freigegebenen Datenknoten über Formulare oder Fragmente hinweg.

**Keine Datenbindung:** Behält das Feld für die reine visuelle Verwendung oder die temporäre Eingabe bei.

## &#x200B;3. Verwendung

Numerische Felder sind ideal in Szenarien, in denen nur Ziffern eine gültige Eingabe sind. Häufige Anwendungsszenarien umfassen:

- Erfassen **Mobilfunknummern, OTPs und PINs**

- Eingabe **Richtliniennummern oder Mitarbeiter-IDs**

- Erfassen **numerische Mengen oder Geldwerte**

- Aktivieren **schrittbasierter Zahlenfelder** (z. B. Zähler oder Score-Einträge)

Autoren können numerische Felder in Layout-Containern oder Teilformularen platzieren und Validierungen (wie Längen-, Mindest- oder Höchstwertbeschränkungen) anwenden, um die Datenqualität zu verbessern.

## 4. Best Practices

- Numerische Felder ggf. eindeutig mit Einheiten kennzeichnen (z. B. „Betrag in ₹„).

- Wenden Sie die Formatvalidierung an (z. B. 10-stellige Grenzwerte für Telefonnummern), um die Genauigkeit zu verbessern.

- Verwenden Sie Reservewerte, wenn Felder obligatorisch sind, aber dynamische Daten fehlen können.

- Binden Sie numerische Felder sorgfältig an Schemapfade, um die Backend-Verarbeitung zu unterstützen.

- Halten Sie ein konsistentes Erscheinungsbild und Typografie aufrecht, um den Markenrichtlinien zu entsprechen.

Die **Numerisches Feld**-Komponente im Editor für interaktive Kommunikation ist ein präzises, zuverlässiges Tool für die ziffernbasierte Datenerfassung. Mit robuster Formatierung, Sichtbarkeitssteuerelementen und Datenbindungsoptionen wird sichergestellt, dass numerische Eingaben klar erfasst und nahtlos in digitale Formulare integriert werden. Wenn sie richtig formatiert und konfiguriert sind, werden die Benutzerfreundlichkeit der Formulare und die allgemeine Datengenauigkeit erheblich verbessert.


