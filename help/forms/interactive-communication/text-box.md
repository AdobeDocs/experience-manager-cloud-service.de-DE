---
title: Textfeldkomponente im Editor für interaktive Kommunikation
description: Die Textfeldkomponente im Editor für interaktive Kommunikation in AEM Forms ermöglicht es Autorinnen und Autoren, Textinhalte innerhalb einer Kommunikation einzugeben und anzuzeigen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 6bed824c-b959-4882-a5aa-dbb7fbf2f8a0
source-git-commit: ea372529b504ed70b74171e75d1d54f98fef432c
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 4%

---

# Textfeldkomponente im Editor für interaktive Kommunikation


## &#x200B;1. Einführung

Mit **Komponente „Textfeld** im Editor für interaktive Kommunikation können Autoren Textinhalte innerhalb einer Kommunikation eingeben und anzeigen. Es handelt sich dabei um eine der grundlegendsten und am häufigsten verwendeten Komponenten, die häufig zum Erfassen von Namen, Kommentaren, Feedback oder benutzerdefinierten Daten beim Entwerfen interaktiver Kommunikations- oder Kommunikationsfragmente verwendet wird.

Das Textfeld unterstützt **Datenbindung**, sodass Autoren statische und dynamische Inhalte nahtlos kombinieren können, z. B.: ***„Benutzername: @name“***, wobei @name ein gebundenes Datenfeld ist, das beim Speichern des Dokuments als PDF dynamisch ausgefüllt wird. Darüber hinaus unterstützt es Rich-Text-Formatierung und flexible Positionierung für eine präzise Layout-Steuerung.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/textbox.png)

## &#x200B;2. Anzeigemuster

Sie können einem Textfeld **Bereich** Eigenschaften **ein** zuweisen. Anzeigemuster steuern, wie Feldwerte den Endbenutzern in der Vorschau der Arbeitsfläche und in der generierten Ausgabe angezeigt werden - z. B. maskieren eines Texteintrags als Telefonnummer: **(555) 123-4567**.

Das konfigurierte Muster wird sofort in der Vorschau der Arbeitsfläche angezeigt und bleibt über die Speicher- und Neuladungszyklen hinweg erhalten. Für erweiterte Anwendungsfälle können Sie eine **benutzerdefinierte XFA-Bildklausel) definieren** um das gewünschte Ausgabeformat zu erzielen.

### Konfigurieren eines Anzeigemusters

1. Wählen Sie die Textfeldkomponente auf der Design-Arbeitsfläche aus.
2. Öffnen Sie das Bedienfeld **Eigenschaften**.
3. Wählen **im Abschnitt** ein vordefiniertes Muster aus oder geben Sie eine benutzerdefinierte Bildklausel ein.
4. Zeigen Sie eine Vorschau des formatierten Werts auf der Arbeitsfläche an.

### Beispiel für ein benutzerdefiniertes Muster (Text)

| Muster | Beispielausgabe | Beschreibung |
|---------|----------------|-------------|
| `text{(999) 999-9999}` | (555) 123-4567 | Rufnummernmaske |

**Picture-Klauselsymbole (Text):**

| Symbol | Bedeutung |
|--------|---------|
| 9 | Entspricht einer Ziffer |
| A | Passt zu einem Brief |
| O | Entspricht alphanumerischen Zeichen |
| X | Entspricht einem beliebigen Zeichen |

### Best Practices

- Wählen Sie ein Muster aus, das der Art und Weise entspricht, wie die Endbenutzer den Wert lesen möchten (Telefon, ID, Postleitzahl).
- Validieren von Beispieldaten auf der Arbeitsfläche vor der Veröffentlichung.
- Verwenden Sie benutzerdefinierte Bildklauseln nur, wenn vordefinierte Muster Ihre Formatierungsanforderungen nicht erfüllen.

## &#x200B;3. Eigenschaften

Die Textfeldkomponente bietet eine Vielzahl von Eigenschaften, die Ihnen bei der Konfiguration von Erscheinungsbild, Verhalten und Verhalten helfen.

2.1 Typografie

**Schriftfamilie:** Ermöglicht die Auswahl von Schriftstilen wie Arial, Helvetica, Times New Roman usw.

**Schriftartvalidierung** Es können optionale Eingabeeinschränkungen angewendet werden, um sicherzustellen, dass nur Text-, numerische oder spezielle Formate akzeptiert werden.

**Textausrichtung:** Optionen umfassen linke, rechte, zentrierte oder Blocksatz-Ausrichtung.

**Textstile:** Aktivieren Sie die Textformatierung mit Fett-, Kursiv-, Durchgestrichen- und Unterstrichfunktionen.

**Listen:** Unterstützt das Einfügen von sortierten (nummerierten) und unsortierten (Aufzählungslisten) Listen.

2.2 Position

**Breite und Höhe** Legen Sie die Abmessungen des Textfelds in Pixeln oder Prozentsätzen relativ zum Container fest.

2.3 Spanne

Definieren Sie den Abstand um das Textfeld:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

2.4 Erscheinungsbild

- **Textfüllung:** Farbe und Transparenz für Text anpassen.

- **Fill** Legen Sie die Hintergrundfarbe des Textfelds fest.

- **Kontur:** Rahmen mit anpassbarem Element hinzufügen:

   - Breite (Stärke)

   - Stil (einfarbig, gestrichelt, gepunktet)

   - Edge (abgerundete oder spitze Ecken)

2.5 Präsenz

**Sichtbar:** Standardeinstellung; dem Benutzer wird ein Textfeld angezeigt.

**Ausgeblendet:** Textfeld ist im Formular enthalten, wird jedoch nicht angezeigt.



## &#x200B;4. Nutzung

Das Textfeld wird verwendet für:

- Erfassen von Kundeninformationen wie Namen, Kommentaren oder Feedback.

- Alphanumerische Werte eingeben.

- Integrieren von personalisierten Nachrichten mithilfe von gebundenen Datenmodellen.

- Einbetten in Fragmente zur wiederholten Verwendung in Dokumenten.

Autoren können das Textfeld aus der Komponentenbibliothek in die Design-Ansicht oder die Master-Ansicht ziehen und sein Verhalten mithilfe des Bedienfelds „Eigenschaften“ konfigurieren.

## 5. Best Practices

- Verknüpfen Sie Textfelder immer mit aussagekräftigen Feldbezeichnungen, um die Barrierefreiheit zu verbessern.

- Verwenden Sie geeignete Eingabevalidierungen, um Fehler bei der Dateneingabe zu vermeiden.

- Stellen Sie ein responsives Layout sicher, indem Sie Ränder und Breiten relativ zu den übergeordneten Containern festlegen.

- Vermeiden Sie übermäßige Schriftstile, die die Lesbarkeit beeinträchtigen könnten.

Durch sorgfältige Konfiguration der Eigenschaften von Textfeldern können Autorinnen und Autoren im Editor für interaktive Kommunikation in AEM interaktive, responsive und benutzerfreundliche Kommunikationserlebnisse erstellen.

## Siehe auch

- [Numerische Feldkomponente](/help/forms/interactive-communication/numeric-field.md)
- [Komponente „Datumsfeld“](/help/forms/interactive-communication/date-field.md)
- [Datum/Uhrzeit-Feldkomponente](/help/forms/interactive-communication/date-time-field.md)
- [Ungebundene Variablenkomponente](/help/forms/interactive-communication/unbound-variable.md)
- [Konfigurieren der Datenbindung im Editor für interaktive Kommunikation](/help/forms/interactive-communication/configure-data-binding.md)
- [Verwenden des Regeleditors im Editor für interaktive Kommunikation](/help/forms/interactive-communication/use-the-rule-editor.md)
