---
title: Textfeldkomponente im Editor für interaktive Kommunikation
description: Die Textfeldkomponente im Editor für interaktive Kommunikation in AEM Forms ermöglicht es Autorinnen und Autoren, Informationen wie Namen, Adressen, Kommentare oder numerische IDs anzuzeigen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 7%

---


# Textfeldkomponente im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Die Textfeldkomponente im Editor für interaktive Kommunikation (IC) ermöglicht es Autoren, Informationen wie Namen, Adressen, Kommentare oder numerische IDs anzuzeigen. Der im Textfeld angezeigte Wert ist entweder vordefiniert (statisch) oder mithilfe der Datenbindung dynamisch ausgefüllt. Sie unterstützt Einzelzeileneinträge, Validierungsregeln und flexible Formatierungen und ist damit eines der am häufigsten verwendeten und vielseitigsten Elemente in der personalisierten Kommunikation.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/textfield.png)

## &#x200B;2. Eigenschaften

2.1 Basisfeld

- **Name:** Definieren Sie eine eindeutige Kennung für das Feld, die in Datenmodellen, Regeln und Skripten verwendet wird.

- **Beschriftung:** Zeigt Benutzern die auf dem Bildschirm angezeigte Beschriftung an (z. B. „Vorname„).

- **Wert:** Zeigt Text wie Namen, Adressen, Anmerkungen oder andere Details an. Der Wert ist entweder statisch oder von der Datenbindung abgeleitet.

- **Reservieren** Legen Sie die Ausrichtung des Werts für links, rechts, oben oder unten fest oder geben Sie eine benutzerdefinierte Position mit Einheiten wie Millimetern (z. B. 20 mm) an.

- **Erscheinungsbild** Legen Sie für das Erscheinungsbild des Wertefelds „Keine“, „Durchgezogenes Feld“ oder „Unterstrichen“ fest, je nach gewünschtem visuellen Layout.

2.2 Typografie

Steuert den visuellen Stil der eingegebenen Zeichen:

- **Schriftartvalidierung:** Sie optionale Einschränkungen an, um das Format des angezeigten Werts zu überprüfen, z. B. nur Alphabete, Zahlen oder bestimmte benutzerdefinierte Muster zuzulassen.

- **Schriftgröße:** Passen Sie die Textgröße innerhalb des Felds mit Punktwerten wie 10 Punkt, 12 Punkt, 20 Punkt usw. an, um Lesbarkeit und Ausrichtung an Designstandards sicherzustellen.

2.3 Position

Definiert die Platzierung des Felds innerhalb des Layouts:

- **X/Y-Koordinaten**

- **Breite und Höhe** (mm, px oder %)

2.4 Spanne

Gibt den Abstand um den Feld-Container an:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

2.5 Erscheinungsbild

Formatiert den Feld-Container selbst:

- **Fill** Legen Sie die Hintergrundfarbe des Textfelds fest. Dadurch können Sie Eingabefelder unterscheiden oder mit Markenfarben abstimmen.

- **Kontur** Fügen Sie Rahmen um das Textfeld mit den folgenden anpassbaren Eigenschaften hinzu:

- **Breite** Definieren Sie die Stärke des Rahmens.

- **Style:** Sie zwischen den Stilen Durchgehend, Gestrichelt oder Gestrichelt.

- **Edge:** Wählen Sie die Form der Ecken aus - entweder abgerundet oder scharf.

- **Radius:** Passen Sie die Eckkrümmung mithilfe von Radiuswerten (z. B. 4 px, 10 px) an, um einen weicheren oder winkligeren Look zu erzielen.

2.6 Vorhandensein

Bestimmt die Sichtbarkeit zur Laufzeit:

- **Sichtbar:** angezeigt und belegt Platz

- **Ausgeblendet (Platz bleibt):** unsichtbar, aber der Layout-Bereich ist reserviert

2.7 Datenbindung

Verknüpft das Textfeld mit einer Datenquelle, um Werte dynamisch oder statisch innerhalb der Kommunikation anzuzeigen.

- **Datenbindungstyp:**, wie das Feld eine Verbindung zu einer Datenquelle oder einem Schema herstellt.

- **Benutzername:** bindet das Textfeld unter Verwendung des im Datenmodell oder Schema definierten Feldnamens, sodass dynamischer Text auf der Grundlage externer Daten angezeigt wird.

- **Globale Daten verwenden:** Verbindet das Feld mit globalen Daten, die über die gesamte Kommunikation hinweg freigegeben werden, um eine konsistente Informationsanzeige zu gewährleisten.

- **Keine Datenbindung:** Behält die Verknüpfung des Felds mit einer Backend-Quelle bei. Sie wird verwendet, um statische Werte oder Text anzuzeigen, die nur für visuellen Kontext bestimmt sind.

## &#x200B;3. Verwendung

Zu häufigen Szenarien gehören:

- Erfassen persönlicher Daten (Namen, Adressen, Telefonnummern)

- Akzeptieren von Kommentaren oder Feedback (mehrzeilig)

- Richtliniennummern oder Konto-IDs eingeben

- Erfassen kurzer numerischer Werte wie PIN-Codes oder OTPs

Autoren können das Feld zur Ausrichtung in Teilformularen oder Layout-Rastern platzieren und Validierungsregeln (Längenbeschränkungen, Regex-Muster) anhängen, um eine saubere Eingabe sicherzustellen.

## &#x200B;4. Best Practices

- Anwenden der Validierung (obligatorische Flags, Musterprüfungen) für sofortiges Feedback.

- Geben Sie einen aussagekräftigen Reservetext für gedruckte oder schreibgeschützte Ansichten an.

- Halten Sie die Typografie in Übereinstimmung mit den Markenrichtlinien.

- Verringern Sie die Feldbreite auf Layouts für Mobilgeräte, um kleinere Bildschirme zu integrieren.

- Für einfachere Wartung möglichst direkt an das Datenmodell binden.

Die Textfeldkomponente im IC-Editor ist ein vielseitiger Baustein, der die Datenerfassung optimiert. Durch eine sorgfältige Konfiguration mit gut ausgewählter Typografie, klaren Beschriftungen, ordnungsgemäßer Validierung und solider Datenbindung bietet sie ein nahtloses, benutzerfreundliches Erlebnis und zuverlässige Daten für die nachgelagerte Verarbeitung.


