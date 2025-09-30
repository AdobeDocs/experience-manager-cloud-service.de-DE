---
title: Textfeld-Objekt im Editor für interaktive Kommunikation
description: Mit dem Textfeld-Objekt im Editor für interaktive Kommunikation in AEM Forms können Autorinnen und Autoren Textinhalte innerhalb einer Kommunikation eingeben und anzeigen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 11%

---


# Textfeld-Objekt im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Das **Textfeld**-Objekt im Editor für interaktive Kommunikation ermöglicht es Autoren, Textinhalte innerhalb einer Kommunikation einzugeben und anzuzeigen. Es handelt sich dabei um eine der grundlegendsten und am häufigsten verwendeten Komponenten, die häufig zum Erfassen von Namen, Kommentaren, Feedback oder benutzerdefinierten Daten beim Entwerfen interaktiver Kommunikations- oder Kommunikationsfragmente verwendet wird.

Das Textfeld unterstützt **Datenbindung**, sodass Autoren statische und dynamische Inhalte nahtlos kombinieren können, z. B.: ***„Benutzername: @name“***, wobei @name ein gebundenes Datenfeld ist, das beim Speichern des Dokuments als PDF dynamisch ausgefüllt wird. Darüber hinaus unterstützt es Rich-Text-Formatierung und flexible Positionierung für eine präzise Layout-Steuerung.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/textbox.png)

## &#x200B;2. Eigenschaften

Das Textfeld-Objekt stellt eine Vielzahl von Eigenschaften bereit, die bei der Konfiguration von Erscheinungsbild, Verhalten und Verhalten helfen.

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



## &#x200B;3. Verwendung

Das Textfeld wird verwendet für:

- Erfassen von Kundeninformationen wie Namen, Kommentaren oder Feedback.

- Alphanumerische Werte eingeben.

- Integrieren von personalisierten Nachrichten mithilfe von gebundenen Datenmodellen.

- Einbetten in Fragmente zur wiederholten Verwendung in Dokumenten.

Autoren können das Textfeld aus der Objektbibliothek in die Design-Ansicht oder die Master-Ansicht ziehen und sein Verhalten mithilfe des Bedienfelds Eigenschaften konfigurieren.

## 4. Best Practices

- Verknüpfen Sie Textfelder immer mit aussagekräftigen Feldbezeichnungen, um die Barrierefreiheit zu verbessern.

- Verwenden Sie geeignete Eingabevalidierungen, um Fehler bei der Dateneingabe zu vermeiden.

- Stellen Sie ein responsives Layout sicher, indem Sie Ränder und Breiten relativ zu den übergeordneten Containern festlegen.

- Vermeiden Sie übermäßige Schriftstile, die die Lesbarkeit beeinträchtigen könnten.

Durch sorgfältige Konfiguration der Eigenschaften von Textfeldern können Autorinnen und Autoren im Editor für interaktive Kommunikation in AEM interaktive, responsive und benutzerfreundliche Kommunikationserlebnisse erstellen.
