---
title: Kontrollkästchenobjekt im Editor für interaktive Kommunikation
description: Mit dem Kontrollkästchenobjekt im Editor für interaktive Kommunikation in AEM Forms können Benutzende eine oder mehrere binäre Auswahlen treffen (ja/nein, wahr/falsch).
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 8%

---


# Kontrollkästchenobjekt im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit der Kontrollkästchenkomponente im Editor für interaktive Kommunikation (IC) können Benutzer eine oder mehrere binäre Auswahlen treffen (ja/nein, wahr/falsch). Diese Funktion wird häufig für Nutzungsbedingungen, Voreinstellungen, Einverständnisfelder und Opt-ins verwendet und bietet eine schnelle Möglichkeit, boolesche Eingaben in einem Kommunikationsformular zu erfassen.

Das Kontrollkästchen unterstützt flexible Stile, Datenbindungsoptionen und Sichtbarkeitsregeln und ist daher ein leichtes, aber leistungsstarkes Tool beim Entwerfen interaktiver, benutzerfreundlicher Formulare.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/checkbox.png)

## &#x200B;2. Eigenschaften

2.1 Basisfeld

- **Name:** Eindeutige Kennung, die zum Referenzieren des Kontrollkästchens in Datenmodellen, Regeln oder Skripten verwendet wird.

- **Umschalten** Ermöglicht das Ein-/Ausschalten des Kontrollkästchens, wenn darauf geklickt wird. Dies kann im Einzelmodus oder im Gruppierungsmodus verwendet werden.

- **Beschriftung:** Die beschreibende Beschriftung, die neben dem Kontrollkästchen angezeigt wird und Benutzern anleitet, was sie akzeptieren oder auswählen.

- **Reserve:** Optionaler Platzhaltertext oder -symbol, der bzw. das im schreibgeschützten oder im Fallback-Modus angezeigt wird, wenn keine Interaktion stattfindet.

2.2 Position

Definiert, wo das Kontrollkästchen im Layout platziert wird:

- **X- und Y-Koordinaten** Legen Sie die Position des Kontrollkästchens innerhalb des Layout-Rasters fest.

- **Höhe und Breite** Definiert die Abmessungen des Kontrollkästchens (in mm oder px), insbesondere wenn benutzerdefinierte visuelle Stile oder Symbole verwendet werden.

2.3 Spanne

Ermöglicht einen Abstand um das Kontrollkästchen für Layout-Anpassungen:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

2.4 Erscheinungsbild

Steuert den visuellen Stil des Kontrollkästchens und seines Rahmens:

- **Fill** Hintergrundfarbe des Kontrollkästchens (wenn ausgewählt oder deaktiviert).

- **Kontur** Die Konturfarbe des Kontrollkästchenrahmens.

- **Strichbreite** Die Stärke der Rahmenlinie.

- **Style:** Durchgehend, gestrichelt oder benutzerdefiniertes Konturmuster.

- **Kanten:** Definiert die Eckformatierung des Kontrollkästchens: Abgerundete oder scharfe Kanten, je nach Design-Voreinstellung.

2.5 Präsenz

Bestimmt, wie und wann das Kontrollkästchen zur Laufzeit angezeigt wird:

- **Sichtbar:** wird normal angezeigt und nimmt Platz ein.

- **Ausgeblendet (Platz bleibt):** in der Benutzeroberfläche ausgeblendet, der Layout-Bereich wird jedoch beibehalten. Nützlich für bedingte Sichtbarkeit ohne Layout-Unterbrechung.

2.6 Datenbindung

Aktiviert das Kontrollkästchen für die Interaktion mit externen oder internen Datenquellen:

**Datenbindungstyp:**

**Benutzername:** den Wert unter Verwendung des Feldnamens der Komponente fest.

**Globale Daten verwenden:** Stellt eine Verbindung zu einem globalen Datenmodell her, das über die gesamte Kommunikation hinweg freigegeben wurde.

**Keine Datenbindung:** Kontrollkästchen bleibt eigenständig und wird nicht im Datenmodell gespeichert.

&#x200B;3. Verwendung

Kontrollkästchen werden häufig in Szenarien wie den folgenden verwendet:

- **Einverständnisfelder:**. B. „Ich stimme den Nutzungsbedingungen zu“

- **Benutzereinstellungen:** z. B. „Newsletter abonnieren“

- **Auswahl mehrerer Optionen:** z. B. „Alle anwendbaren Optionen auswählen“

- **Formularbestätigungen:**. B. „Ich bestätige, dass die obigen Angaben korrekt sind“

Kontrollkästchen können in Layout-Rastern oder Bedienfeldern platziert und zur besseren Organisation in Formularen gruppiert werden.

&#x200B;4. Best Practices

- Verwenden Sie klare, knappe Beschriftungen, um Benutzenden zu helfen zu verstehen, was sie auswählen.

- Vermeiden Sie Übersichtlichkeit, indem Sie Kontrollkästchen nur für binäre Eingaben verwenden - verwenden Sie Optionsschaltflächen für exklusive Optionen.

- Stellen Sie mithilfe von Rand- und Layout-Einstellungen für eine saubere Benutzeroberfläche einen angemessenen Abstand sicher.

- Binden Sie Kontrollkästchen an einen aussagekräftigen Datenmodellverweis, wenn die erfasste Auswahl gespeichert oder verarbeitet werden muss.

- Verwenden Sie Sichtbarkeitsregeln, wenn Kontrollkästchen von vorherigen Eingaben oder Bedingungen abhängig sind.

Das Kontrollkästchenobjekt im Editor für interaktive Kommunikation ist eine einfache, aber wesentliche Komponente für binäre Eingaben. Durch die Unterstützung für Formatierung, bedingte Präsenz und flexible Datenbindung spielt sie eine wichtige Rolle bei der Verbesserung der Interaktivität und Benutzerkontrolle in intelligenten digitalen Formularen. Wenn Kontrollkästchen mit durchdachten Beschriftungen, konsistentem Stil und aussagekräftiger Datenintegration implementiert werden, tragen sie erheblich zu einem reibungslosen und intuitiven Formularerlebnis bei.


