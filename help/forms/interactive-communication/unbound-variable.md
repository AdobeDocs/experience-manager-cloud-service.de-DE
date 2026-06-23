---
title: Komponente „Ungebundene Variable“ im Editor für interaktive Kommunikation
description: Mit der Komponente „Ungebundene Variable“ im Editor für interaktive Kommunikation können Sie berechnete, skriptbasierte oder unabhängig eingestellte Werte mit vollständiger Formatierungssteuerung anzeigen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: unbound-variable-ic-editor
source-git-commit: b817bcb02c4ff6ac369973ef658d9fcbdce95c51
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 3%

---


# Komponente „Ungebundene Variable“ im Editor für interaktive Kommunikation


## &#x200B;1. Einführung

Mit **Komponente „Ungebundene Variable** im Editor für interaktive Kommunikation (IC) können Sie ein Feld platzieren, dessen Wert nicht an ein externes Datenmodell oder einen externen Schemaknoten gebunden ist. Stattdessen wird der Wert durch Skripterstellung, regelbasierte Berechnung oder einen statischen Standard bereitgestellt, sodass diese Komponente die richtige Wahl ist, wenn Sie einen berechneten oder zwischengeschalteten Anzeigewert benötigen, der nicht direkt aus einer gebundenen Datenquelle stammt.

Da eine ungebundene Variable nicht mit einem Formulardatenmodell verbunden ist, erhalten Sie zur Entwurfszeit und zur Laufzeit vollständige Autorenkontrolle über den Wert. Sie können damit berechnete Summen, dynamisch generierte Referenznummern, Zwischenergebnisse von Formeln oder andere Werte anzeigen, die von Ihrer Regel-Engine erzeugt werden.

Die Komponente unterstützt alle vier Datentypen **Text**, **Numerisch**, **Datum** und **Datum/Uhrzeit** und der aktive Datentyp bestimmt, welche Anzeigemuster-Syntax und Bildklauselsymbole gelten.

## &#x200B;2. Anzeigemuster

Sie können einem Feld **Ungebundene Variable** im Bedienfeld **Eigenschaften** ein Anzeigemuster zuweisen, indem Sie die gleichen Anzeigemuster-Steuerelemente verwenden, die für die Komponenten „Textfeld“, „Numerisches Feld“, „Datumsfeld“ und „Datum/Uhrzeit-Feld“ verfügbar sind. Dies ermöglicht die formatierte Darstellung berechneter oder referenzierter Werte in der Arbeitsfläche und in der generierten Ausgabe.

Das konfigurierte Muster wird sofort in der Vorschau der Arbeitsfläche angezeigt und bleibt über die Speicher- und Neuladungszyklen hinweg erhalten.

### Konfigurieren eines Anzeigemusters

1. Wählen Sie auf der Design-Arbeitsfläche die Komponente Ungebundene Variable aus.
2. Öffnen Sie das Bedienfeld **Eigenschaften**.
3. Wählen **im Abschnitt** ein vordefiniertes Muster aus oder geben Sie eine benutzerdefinierte Bildklausel ein.
4. Zeigen Sie eine Vorschau des formatierten Werts auf der Arbeitsfläche an.

### Auswählen des richtigen Musters

Da eine ungebundene Variable jeden Datentyp enthalten kann, muss die verwendete Bildklauselsyntax mit dem konfigurierten Datentyp des Felds übereinstimmen:

| Felddatentyp | Mustersyntax | Beispielausgabe | Referenz |
|-----------------|----------------|----------------|-----------|
| Text | `text{…}` | (555) 123-4567 | [Textfeld - Anzeigemuster](/help/forms/interactive-communication/text-box.md#2-display-pattern) |
| Nummerisch | `num{…}` | $1,234.21 | [Numerisches Feld - Anzeigemuster](/help/forms/interactive-communication/numeric-field.md#2-display-pattern) |
| Datum | `date{…}` | 01/04/2007 | [Datumsfeld - Anzeigemuster](/help/forms/interactive-communication/date-field.md#2-display-pattern) |
| Datum/Uhrzeit | `date{…} time{…}` | 04/01/2007 14:30 | [Feld Datum/Uhrzeit - Anzeigemuster](/help/forms/interactive-communication/date-time-field.md#2-display-pattern) |

>[!NOTE]
>
> Wenn der Datentyp des Felds Datum oder Datum/Uhrzeit ist, muss der zugrunde liegende Wert dem **ISO 8601**-Format (`YYYY-MM-DD` oder `YYYY-MM-DDTHH:MM`) entsprechen. Werte, die diesem Format nicht entsprechen, werden unverändert ohne angewendetes Anzeigemuster angezeigt.

## &#x200B;3. Eigenschaften

Die Komponente „Ungebundene Variable“ teilt sich einen gemeinsamen Eigenschaftssatz mit anderen Feldkomponenten, mit einem wichtigen Unterschied: Sie hat keine externen Datenbindungsoptionen, da ihr Wert definitionsgemäß ungebunden an eine beliebige Datenquelle ist.

3.1 Grundfeld

- **Name:** Ein eindeutiger Bezeichner für die Variable. Wird verwendet, um in Regeln, Skripten und Ausdrücken innerhalb der IC darauf zu verweisen.

- **Datentyp:** Gibt den Typ des Werts an, den diese Variable enthält **Text**, **Numerisch**, **Datum** oder **Datum/Uhrzeit**. Der ausgewählte Datentyp bestimmt, welche Anzeigemuster-Syntax angewendet wird und wie der Wert validiert wird.

- **Beschriftung:** Der Titel, der neben dem Feld auf der Arbeitsfläche angezeigt wird (z. B. „Berechnete Summe“ oder „Referenznummer„).

- **Wert:** Der im Feld angezeigte standardmäßige oder berechnete Wert. In den meisten Fällen wird dies programmgesteuert mithilfe des Regel-Editors oder eines Skripts festgelegt und nicht manuell eingegeben.

- **Reserve:** Ein Fallback-Wert, der angezeigt wird, wenn kein berechneter Wert verfügbar ist. Dies ist für eine schreibgeschützte oder schreibgeschützte Ausgabe nützlich, bei der ein leeres Feld nicht akzeptabel ist.

- **Erscheinungsbild** Eine visuelle Stilvorgabe (Ohne, Volltonrahmen oder Unterstrichen) für den Feld-Container.

3.2 Typografie

Steuert, wie der angezeigte Wert formatiert wird:

- **Schriftvariante:** Sie Schriftfamilie, Stärke (normal, fett) und Stil (kursiv) aus, um sie an den umgebenden Inhalt anzupassen.

- **Schriftgröße:** in der Regel standardmäßig auf 10 Punkt eingestellt; wird angepasst, um die visuelle Konsistenz mit dem Rest der Kommunikation zu wahren.

3.3 Position

Definiert die Platzierung der Komponente auf der Arbeitsfläche:

- **X- und Y-Koordinaten** Legen Sie die genaue horizontale und vertikale Position fest.

- **Breite und Höhe** Geben Sie Abmessungen in Millimetern an, um sie an benachbarten Elementen auszurichten.

3.4 Spanne

Definiert den Abstand um die Komponentenbegrenzung:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

3.5 Erscheinungsbild

Formatiert den Feld-Container:

- **Fill** Hintergrundfarbe des Felds.

- **Kontur** Rahmen um das Feld mit den folgenden Optionen:

   - **Breite:** Rahmenstärke.

   - **Style:** Durchgehend, gestrichelt oder gepunktet.

   - **Edge:** Abgerundete oder scharfe Ecken.

3.6 Anwesenheit

Kontrolliert die Sichtbarkeit zur Laufzeit:

- **Sichtbar:** Das Feld wird angezeigt und nimmt den Layout-Bereich ein.

- **Ausgeblendet (Platz bleibt):** Das Feld ist unsichtbar, aber sein Layout-Bereich bleibt erhalten. Dies ist nützlich, wenn die Sichtbarkeit mithilfe des Regeleditors dynamisch umgeschaltet wird.

## &#x200B;4. Nutzung

Verwenden Sie eine ungebundene Variable, wenn Sie folgenden Wert anzeigen möchten:

- **Wird durch eine Regel oder ein Skript**, z. B. eine laufende Summe, eine Steuerberechnung oder ein Rabattbetrag, der von anderen Feldwerten abgeleitet wird.

- **Programmgesteuert generiert** z. B. eine Referenznummer oder ein Trackingcode, der zur Laufzeit von der Backend-Logik zugewiesen wird.

- **Nicht im Datenmodell verfügbar** - z. B. ein Zwischenergebnis, das auf dem Bildschirm aussagekräftig ist, aber nicht als Schemafeld existiert.

- **Bedingt sichtbar** - Eine berechnete Nachricht oder ein berechneter Wert wird nur angezeigt, wenn bestimmte Bedingungen erfüllt sind. Verwenden Sie den Regeleditor, um Sichtbarkeit und Wert gemeinsam festzulegen.

Sie können eine ungebundene Variable in Teilformularen, Layout-Containern oder direkt auf der Design-Arbeitsfläche platzieren. Kombinieren Sie sie mit dem Regeleditor, um Ausdrücke zu schreiben, die ihren Wert basierend auf anderen gebundenen Feldern im IC berechnen.

## 5. Best Practices

- **Legen Sie einen aussagekräftigen Reservewert fest** sodass die Druckausgabe und die schreibgeschützte Vorschau nie ein leeres Feld anzeigen, wenn der berechnete Wert nicht verfügbar ist.

- **Datentyp an Ausgabe anpassen** - Wenn Sie einen Währungsbetrag berechnen, legen Sie den Datentyp auf „Numerisch“ fest und wenden Sie ein numerisches Anzeigemuster an. Wenn Sie ein Datum berechnen, legen Sie es auf „Datum“ fest und stellen Sie die ISO 8601-Eingabe sicher.

- **Eine klare Beschriftung verwenden** - Da der Wert berechnet und anhand einer Beschriftung nicht direkt erkennbar ist, verhindert eine beschreibende Beschriftung (z. B. „Zwischensumme (berechnet)„) Verwirrung sowohl für Prüfende als auch für Endbenutzende.

- **Vermeiden Sie die übermäßige Verwendung von ungebundenen Variablen für Daten, die in das Modell gehören** - Wenn ein Wert vernünftigerweise zum Formulardatenmodell hinzugefügt werden könnte, bevorzugen Sie die Bindung eines Standardfelds. Ungebundene Variablen für Werte reservieren, die wirklich transient oder abgeleitet sind.

- **Dokumentieren Sie Ihre Ausdrücke** - Fügen Sie im Regeleditor einen Kommentar hinzu, der beschreibt, was jede ungebundene Variable berechnet, sodass die Logik beibehalten werden kann, wenn die IC später bearbeitet wird.

## Siehe auch

- [Textfeld-Komponente](/help/forms/interactive-communication/text-box.md) - Anzeigemustersyntax für Textwerte
- [Numerische Feldkomponente](/help/forms/interactive-communication/numeric-field.md) - Mustersyntax für numerische und Währungswerte anzeigen
- [Datumsfeldkomponente](/help/forms/interactive-communication/date-field.md) - Anzeigemustersyntax für Datumsangaben
- [Datums-/Uhrzeitfeldkomponente](/help/forms/interactive-communication/date-time-field.md) - Anzeigemustersyntax für kombinierte Datums- und Uhrzeitwerte
- [Verwenden des Regeleditors im Editor für interaktive Kommunikation](/help/forms/interactive-communication/use-the-rule-editor.md) — Schreiben von Ausdrücken zum Berechnen und Zuweisen von Werten zu ungebundenen Variablen
- [Konfigurieren der Datenbindung im Editor für interaktive Kommunikation](/help/forms/interactive-communication/configure-data-binding.md)

