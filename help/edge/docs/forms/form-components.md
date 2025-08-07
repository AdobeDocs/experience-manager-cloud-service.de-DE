---
title: Komponenten von adaptiven Formularblöcken und ihre Eigenschaften
description: Dieses Dokument bietet einen Überblick über die Formularkomponenten und ihre Eigenschaften, die in Edge Delivery Services für AEM Forms verfügbar sind.
feature: Edge Delivery Services
exl-id: 7d087d41-9313-482a-a905-8955b0999781
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 100%

---

# Komponenten von adaptiven Formularblöcken und ihre Eigenschaften

Mit Edge Delivery Services für AEM Forms können Sie benutzerfreundliche und interaktive Formulare mit verschiedenen Komponenten erstellen. Diese Komponenten decken unterschiedliche Arten der Datenerfassung ab und können einfach an Ihre spezifischen Anforderungen angepasst werden.


![Eine Beispieltabelle mit einigen Komponenten und Eigenschaften](/help/edge/assets/sample-form-in-spreadsheet.png)

Der adaptive Formularblock generiert eine [einheitliche HTML-Struktur](/help/edge/docs/forms/style-theme-forms.md) für alle Feldtypen und Container (Bedienfelder) und stellt so Konsistenz sicher. Diese einheitliche Struktur erleichtert das [Formatieren eines Formulars](/help/edge/docs/forms/style-theme-forms.md).

## Verfügbare Komponenten

Im Folgenden finden Sie einen Überblick über die verfügbaren Komponenten:

### Eingabefelder

- Alle gültigen HTML5-[Eingabetypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) und [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea). Beispiel: button, checkbox, color, date, datetime-local, email, file, hidden, image, month, number, password, radio, range, reset, submit, tel, text, time, url, week.

### Auswahl-Steuerelemente

- [Kontrollkästchengruppen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox): Zum Auswählen mehrerer Optionen.
- [Optionsgruppen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio): Zum Auswählen einer einzelnen Option aus einer Gruppe.
- [Dropdown-Menüs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select): Zum Anzeigen eines Optionsmenüs. Zum Beispiel ein Dropdown-Feld.

### Container

- Bedienfelder/Container: Zum Gruppieren von verwandten Formularelementen für eine bessere Organisation. Es handelt sich um eine Kombination aus [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) und [legend](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).


## Komponenteneigenschaften

Jede Formularkomponente enthält verschiedene Eigenschaften, mit denen Sie das Verhalten und Erscheinungsbild steuern können. Die folgenden Eigenschaften werden von den Komponenten des adaptiven Formularblocks unterstützt:


| Eigenschaft | Anwendbare Komponenten | Details |
|--------------|------------------------------|----------------------------------------------------------------------|
| Typ | Alle | Legt den Stil der Komponente fest. Diese Eigenschaft bestimmt das Verhalten und Erscheinungsbild des Eingabefelds. Für Texteingaben kann der Typ beispielsweise „text“, für E-Mail-Eingaben „email“ und für Kennworteingaben „password“ lauten. Der adaptive Formularblock unterstützt <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle gültigen HTML5-Eingabetypen</a> sowie <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, und <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a> als Typ. |
| Name | Alle | Identifiziert die Komponente für die Formularübermittlung. Das Attribut „name“ wird verwendet, wenn die Formulardaten an den Server gesendet werden und die Benutzereingabe mit einem bestimmten Feld verknüpft wird. |
| Label | Alle | Stellt Benutzenden kontextbezogene Informationen bereit. Bei „label“ handelt es sich um den Text, der neben der Komponente angezeigt wird und der Benutzenden Hinweise dazu gibt, welche Informationen einzugeben sind. |
| Wert | Text, Kennwort, E-Mail, Zahl, Bereich, Datum und seine Varianten (datetime-local, month, week, time), Kontrollkästchen, Optionsfeld, Ausgeblendet, Absenden, Schaltfläche | Legt den anfänglichen Wert der Komponente fest. Bei „text inputs“, „textarea“ und „select elements“ ist dies der Standardtext oder die angezeigte Option. Bei den Komponenten „Optionsfeld“ und „Kontrollkästchen“ sind dies die Werte/Daten, die bei der Auswahl übermittelt werden. Das Attribut „value“ ist zwar optional, sollte jedoch für Kontrollkästchen und Optionsfelder als obligatorisch betrachtet werden. |
| Platzhalter | Text, Telefon, E-Mail, Kennwort, Datum (und seine Varianten wie month, week, time, datetime-local), Zahl, Bereich | Liefert Hinweise für die erwartete Eingabe. Das Attribut „placeholder“ bietet einen kurzen Hinweis, der den erwarteten Wert des Eingabefelds beschreibt. Er verschwindet, sobald etwas eingegeben wird. |
| Beschreibung | Alle | Stellt zusätzliche Informationen über die Komponente bereit und dient als Hilfetext. Das Beschreibungsfeld ermöglicht eine weitere Erläuterung des Zwecks oder der Anweisungen zum Ausfüllen der Komponente. Es hilft Benutzenden, den Kontext des Eingabefelds zu verstehen. |
| Visible | Alle | Steuert die anfängliche Sichtbarkeit. Das Attribut „visible“ ist eine boolesche Eigenschaft, die bestimmt, ob die Komponente beim Laden des Formulars anfänglich sichtbar oder ausgeblendet ist. Wenn der Wert auf „true“ gesetzt ist, wird das Feld angezeigt. Andernfalls wird es ausgeblendet. |
| Mandatory | Text, Telefon, E-Mail, Kennwort, Datum und seine Varianten (datetime-local, month, week, time), Zahl, Kontrollkästchen, Optionsfeld, Datei, Auswählen (Dropdown), Textarea | Gibt an, ob das Feld vor der Übermittlung ausgefüllt werden muss. Das Attribut „mandatory“ ist eine boolesche Eigenschaft, mit der festgelegt wird, ob vor dem Absenden des Formulars obligatorisch etwas in das Feld eingegeben werden muss. |
| Min. | Datum (und seine Varianten, z. B. month, week, time, datetime-local), Zahl, Bereich | Gibt den erlaubten Mindestwert an. Das Attribut „min“ legt den Mindestwert fest, den die Benutzerin bzw. der Benutzer in das Feld eingeben kann. Bei Zahleneingaben wird beispielsweise die niedrigste zulässige Zahl definiert. |
| Max | Datum (und seine Varianten, z. B. month, week, time, datetime-local), Zahl, Bereich | Gibt den maximal zulässigen Wert an. Das Attribut „max“ legt den Maximalwert fest, der in das Feld eingegeben werden kann. Für Datumsangaben wird beispielsweise das späteste zulässige Datum definiert. |
| Accept | Datei | Definiert die zulässigen Dateitypen. Das Attribut „accept“ ist eine kommagetrennte Liste eindeutiger Dateitypspezifikatoren, die die Dateitypen einschränken, die Benutzende in einem Dateieingabefeld auswählen können. |
| Multiple | Datei | Lässt eine Mehrfachauswahl zu.  Das Attribut „multiple“ ist eine boolesche Eigenschaft, die mit Dateieingabefeldern verwendet wird. Wenn der Wert auf „true“ gesetzt ist, können Benutzende mehr als eine Datei auswählen. |
| Optionen | Dropdown | Gibt Auswahlmöglichkeiten für Dropdown-Menüs an. Die Eigenschaft „options“ ist eine kommagetrennte Liste von Optionen für Dropdown-Menüs, die die auswählbaren Optionen definieren, die Benutzenden angezeigt werden. |
| Checked | Kontrollkästchen, Optionsfeld | Bestimmt, ob das Feld standardmäßig ausgewählt ist. Das Attribut „checked“ ist eine boolesche Eigenschaft, die mit Kontrollkästchen und Optionsfeldern verwendet wird. Wenn der Wert auf „true“ gesetzt ist, zeigt dies an, dass das Feld beim Laden des Formulars standardmäßig ausgewählt ist. |
| Fieldset | Alle | Gruppiert Felder, um visuell unterschiedliche Abschnitte in einem Formular zu erstellen. Das Element „fieldset“ gruppiert verwandte Felder in einem Formular, wobei sie visuell getrennt werden, um die Organisation und das Anwendererlebnis zu verbessern. </br> Um einen Satz von Feldern in einem „fieldset“ zu organisieren, verwenden Sie einfach die Eigenschaft `fieldset` und geben Sie das Attribut „name“ an. Im folgenden Beispiel wird gezeigt, wie Optionsfelder in einem einzelnen „fieldset“ zur besseren Organisation eingekapselt werden. ![Beispiel für „fieldset“](/help/edge/assets/fieldset-example.png) |
| Repeatable | Alle | Eine boolesche Eigenschaft für `fieldset`, die angibt, dass ein bestimmter Feldsatz entsprechend dem für `Min` und `Max` angegebenen Wert wiederholt werden kann. Die `Min`-Eigenschaft sollte auf 1 oder höher gesetzt sein. Legen Sie für die `Min`-Eigenschaft nicht den Wert 0 fest. |
| Sichtbarer Ausdruck | Alle | Ein sichtbarer Ausdruck bezieht sich auf eine Tabellenformel, die mit dem Tag „=“&#39; gekennzeichnet ist und zur Steuerung der Sichtbarkeit eines Felds verwendet wird. In dieser Formel kann nur die Werteigenschaft anderer Felder verwendet werden, sodass eine einfache Verwaltung der Feldsichtbarkeit innerhalb des Systems ermöglicht wird. |
| Wertausdruck | Alle | Ein Wertausdruck bezieht sich auf eine Tabellenformel, die durch das Tag „=“&#39; gekennzeichnet ist und zur Steuerung des Werts eines Felds verwendet wird. In dieser Formel kann nur die Werteigenschaft anderer Felder verwendet werden, sodass eine einfache Verwaltung des Feldwerts innerhalb des Systems ermöglicht wird. |
