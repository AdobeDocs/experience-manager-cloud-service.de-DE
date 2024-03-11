---
title: Formularkomponenten und -eigenschaften
description: Dieses Dokument bietet einen Überblick über die Formularkomponenten und ihre Eigenschaften, die im AEM Forms Edge Delivery Service verfügbar sind.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 7d087d41-9313-482a-a905-8955b0999781
source-git-commit: 4144f9704aaf17ea684be147395adc3aa31641f2
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 2%

---

# Formularkomponenten und Eigenschaften: AEM Forms Edge Delivery Service

Mit AEM Forms Edge Delivery Services können Sie benutzerfreundliche und interaktive Formulare mit verschiedenen Komponenten erstellen. Diese Komponenten decken unterschiedliche Arten der Datenerfassung ab und können einfach an Ihre spezifischen Anforderungen angepasst werden.


![Eine Beispieltabelle mit einigen Komponenten und Eigenschaften](/help/edge/assets/sample-form-in-spreadsheet.png)

Der adaptive Forms-Block generiert eine [einheitliche HTML-Struktur](/help/edge/docs/forms/style-theme-forms.md) für alle Feldtypen und Container (Bereiche), die die Konsistenz sicherstellen. Diese einheitliche Struktur erleichtert [Formular formatieren](/help/edge/docs/forms/style-theme-forms.md).

## Verfügbare Komponenten

Im Folgenden finden Sie eine Übersicht über die verfügbaren Komponenten:

### Eingabefelder

* Alle gültigen HTML5 [Eingabetypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) und [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea). Beispiel: Schaltfläche, Kontrollkästchen, Farbe, Datum, Datum, lokale Zeit, E-Mail, Datei, ausgeblendet, Bild, Monat, Zahl, Kennwort, Optionsfeld, Bereich, Zurücksetzen, Senden, Tel, Text, Zeit, URL und Woche.

### Auswahldialog

* [Kontrollkästchengruppen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox): Zur Auswahl mehrerer Optionen.
* [Optionsgruppen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio): Zum Auswählen einer einzelnen Option aus einer Gruppe.
* [Dropdown-Menüs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select): Zum Anzeigen eines Optionsmenüs. Beispiel: Dropdown-Feld.

### Container

* Bedienfelder/Container: Zum Gruppieren von verwandten Formularelementen für eine bessere Organisation. Es handelt sich um eine Kombination aus [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) und [legend](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).


## Komponenteneigenschaften

Jede Formularkomponente enthält verschiedene Eigenschaften, mit denen Sie das Verhalten und Erscheinungsbild steuern können. Hier finden Sie die Eigenschaften, die von den Adaptive Forms Block-Komponenten unterstützt werden:


| Eigenschaft | Anwendbare Komponenten | Details |
|--------------|------------------------------|----------------------------------------------------------------------|
| Typ | Alle | Gibt den Typ der Komponente an. Diese Eigenschaft bestimmt das Verhalten und Erscheinungsbild des Eingabefelds. Bei Texteingaben kann der Typ beispielsweise &quot;text&quot;, &quot;email&quot; für E-Mail-Eingaben und &quot;password&quot; für Kennworteingaben lauten. Adaptiver Forms-Block unterstützt  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle gültigen HTML5-Eingabetypen</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, und <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a> als Typ. |
| Typ | Alle | Gibt den Typ der Komponente an. Diese Eigenschaft bestimmt das Verhalten und Erscheinungsbild des Eingabefelds. Bei Texteingaben kann der Typ beispielsweise &quot;text&quot;, &quot;email&quot; für E-Mail-Eingaben und &quot;password&quot; für Kennworteingaben lauten. Adaptiver Forms-Block unterstützt  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle gültigen HTML5-Eingabetypen</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, und <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a> als Typ. |
| Name | Alle | Identifiziert die Komponente für die Formularübermittlung. Das Attribut name wird verwendet, wenn die Formulardaten an den Server gesendet werden und die Benutzereingabe mit einem bestimmten Feld verknüpft wird. |
| Bezeichnung | Alle | Stellt Benutzern kontextbezogene Informationen bereit. Die Beschriftung ist der Text, der neben der Komponente angezeigt wird und Benutzern Hinweise dazu gibt, welche Informationen einzugeben sind. |
| Wert  | Text, Kennwort, E-Mail, Zahl, Bereich, Datum und seine Varianten (datetime-local, Monat, Woche, Zeit), Kontrollkästchen, Radio, Ausgeblendet, Senden, Schaltfläche | Gibt den Anfangswert der Komponente an. Bei Texteingaben, Textbereichen und ausgewählten Elementen ist dies der Standardtext oder die angezeigte Option. Bei Optionsfeld- und Kontrollkästchen-Komponenten ist dies der Wert/die Daten, der/die bei der Auswahl übermittelt wird. Das Attribut value ist optional, sollte jedoch für Kontrollkästchen und Optionsfelder als obligatorisch betrachtet werden. |
| Platzhalter | Text, Tel., E-Mail, Passwort, Datum (und seine Varianten wie Monat, Woche, Zeit, Datum/Uhrzeit), Zahl, Bereich | Bietet Hinweise für die erwartete Eingabe. Das Platzhalterattribut bietet einen kurzen Hinweis, der den erwarteten Wert des Eingabefelds beschreibt. Er verschwindet, sobald der Benutzer mit der Eingabe beginnt. |
| Beschreibung | Alle | Stellt zusätzliche Informationen über die Komponente bereit und dient als Hilfetext. Das Beschreibungsfeld ermöglicht eine weitere Erläuterung des Zwecks oder der Anweisungen zum Ausfüllen der Komponente. Es hilft Benutzern, den Kontext des Eingabefelds zu verstehen. |
| Sichtbar | Alle | Steuert die anfängliche Sichtbarkeit. Das Attribut visible ist eine boolesche Eigenschaft, die bestimmt, ob die Komponente beim Laden des Formulars anfänglich sichtbar oder ausgeblendet ist. Wenn der Wert auf &quot;true&quot;gesetzt ist, wird das Feld angezeigt. Andernfalls wird es ausgeblendet. |
| Obligatorisch | Text, Tel, E-Mail, Passwort, Datum und seine Varianten (datetime-local, month, week, time), Zahl, Kontrollkästchen, Radio, Datei, Auswahl (Dropdown), Textarea | Gibt an, ob das Feld vor der Übermittlung ausgefüllt werden muss. Das obligatorische Attribut ist eine boolesche Eigenschaft, mit der festgelegt wird, ob der Benutzer vor dem Senden des Formulars die Eingabe für das Feld angeben muss. |
| Min. | Datum (und seine Varianten, z. B. Monat, Woche, Zeit, Datum, Zeit, Ortszeit), Zahl, Bereich | Gibt den erlaubten Mindestwert an. Das Attribut min legt den Mindestwert fest, den der Benutzer in das Feld eingeben kann. Bei Zahleneingaben wird beispielsweise die niedrigste zulässige Zahl definiert. |
| Max | Datum (und seine Varianten, z. B. Monat, Woche, Zeit, Datum, Zeit, Ortszeit), Zahl, Bereich | Gibt den maximal zulässigen Wert an. Das Attribut max legt den Maximalwert fest, den der Benutzer in das Feld eingeben kann. Für Datumsangaben wird beispielsweise das höchstzulässige Datum definiert. |
| Akzeptieren | File | Definiert die zulässigen Dateitypen. Das Attribut accept ist eine kommagetrennte Liste eindeutiger Dateitypspezifikatoren, die die Dateitypen einschränken, die Benutzer in einem Dateieingabefeld auswählen können. |
| Mehrere | File | Ermöglicht mehrere Auswahlen. Das Attribut multiple ist eine boolesche Eigenschaft, die mit Dateieingabefeldern verwendet wird. Wenn der Wert auf &quot;true&quot;gesetzt ist, können Benutzer mehr als eine Datei auswählen. |
| Optionen | Dropdown | Gibt Optionen für Dropdown-Menüs an. Die options-Eigenschaft ist eine kommagetrennte Liste von Optionen für Dropdown-Menüs, die die auswählbaren Optionen definieren, die dem Benutzer angezeigt werden. |
| Aktiviert | Kontrollkästchen, Radio | Bestimmt, ob das Feld standardmäßig ausgewählt ist. Das angekreuzte Attribut ist eine boolesche Eigenschaft, die mit Kontrollkästchen und Optionsfeldern verwendet wird. Wenn der Wert auf &quot;true&quot;gesetzt ist, zeigt dies an, dass das Feld beim Laden des Formulars standardmäßig ausgewählt ist. |
| Fieldset | Alle | Gruppiert Felder, um visuell unterschiedliche Abschnitte in einem Formular zu erstellen. Das fieldset -Element gruppiert verwandte Felder in einem Formular, wobei es sie visuell trennt, um die Organisation und das Benutzererlebnis zu verbessern. </br> Um eine Gruppe von Feldern in einem Feldsatz zu organisieren, verwenden Sie einfach die `fieldset` -Eigenschaft und geben Sie das Namensattribut an. Im folgenden Beispiel wird gezeigt, wie Optionsfelder in einem einzelnen Feldset zur besseren Organisation eingekapselt werden. ![Beispiel für Feldsatz](/help/edge/assets/fieldset-example.png) |

