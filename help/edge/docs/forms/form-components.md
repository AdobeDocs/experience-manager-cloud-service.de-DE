---
title: Formularkomponenten und -eigenschaften
description: Dieses Dokument bietet einen Überblick über die Formularkomponenten und ihre Eigenschaften, die im AEM Forms Edge Delivery Service verfügbar sind.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: fd2e5df72e965ea6f9ad09b37983f815954f915c
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 3%

---


# Formularkomponenten und Eigenschaften: AEM Forms Edge Delivery Service

Mit AEM Forms Edge Delivery Service können Sie benutzerfreundliche und interaktive Formulare mit verschiedenen Komponenten erstellen. Diese Komponenten decken unterschiedliche Arten der Datenerfassung ab und können einfach an Ihre spezifischen Anforderungen angepasst werden.


![Eine Beispieltabelle mit einigen Komponenten und Eigenschaften](/help/edge/assets/sample-form-in-spreadsheet.png)

Der Baustein &quot;Adaptives Formular&quot;generiert eine [einheitliche HTML-Struktur](/help/edge/docs/forms/style-theme-forms.md) für alle Feldtypen und Container (Bereiche), die die Konsistenz sicherstellen. Diese einheitliche Struktur erleichtert [Formular formatieren](/help/edge/docs/forms/style-theme-forms.md).

## Verfügbare Komponenten

Im Folgenden finden Sie eine Übersicht über die verfügbaren Komponenten:

### Eingabefelder

- Alle gültigen HTML5 [Eingabetypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) und [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea). Beispiel: Schaltfläche, Kontrollkästchen, Farbe, Datum, Datum, lokale Zeit, E-Mail, Datei, ausgeblendet, Bild, Monat, Zahl, Kennwort, Optionsfeld, Bereich, Zurücksetzen, Senden, Tel, Text, Zeit, URL und Woche.

### Auswahldialog

- [Kontrollkästchengruppen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox): Zur Auswahl mehrerer Optionen.
- [Optionsgruppen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio): Zum Auswählen einer einzelnen Option aus einer Gruppe.
- [Dropdown-Menüs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select): Zum Anzeigen eines Optionsmenüs. Beispiel: Dropdown-Feld.

### Container

- Bedienfelder/Container: Zum Gruppieren von verwandten Formularelementen für eine bessere Organisation. Es handelt sich um eine Kombination aus [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) und [legend](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).






## Komponenteneigenschaften

Jede Formularkomponente enthält verschiedene Eigenschaften, mit denen Sie das Verhalten und Erscheinungsbild steuern können. Hier werden die Eigenschaften unterstützt, die von den Komponenten für adaptive Formularblöcke unterstützt werden:


| Property | Anwendbare Komponenten | Details |
|--------------|------------------------------|----------------------------------------------------------------------|
| Typ | Alle | Gibt den Typ der Komponente an. Diese Eigenschaft bestimmt das Verhalten und Erscheinungsbild des Eingabefelds. Bei Texteingaben kann der Typ beispielsweise &quot;text&quot;, &quot;email&quot; für E-Mail-Eingaben und &quot;password&quot; für Kennworteingaben lauten. Bausteine für adaptive Formulare unterstützen  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle gültigen HTML5-Eingabetypen</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, und <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a> als Typ. |
| Typ | Alle | Gibt den Typ der Komponente an. Diese Eigenschaft bestimmt das Verhalten und Erscheinungsbild des Eingabefelds. Bei Texteingaben kann der Typ beispielsweise &quot;text&quot;, &quot;email&quot; für E-Mail-Eingaben und &quot;password&quot; für Kennworteingaben lauten. Bausteine für adaptive Formulare unterstützen  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle gültigen HTML5-Eingabetypen</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, und <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a> als Typ. |
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



<!--

## Supported HTML 5 input types in Adaptive Form Block

The Adaptive Form Block supports a range of HTML 5 input types, and it also seamlessly renders forms created with AEM core components.
Here is the table which outlines how core components correspond to their HTML-5 input types in Edge Delivery:
<table>
 <tbody>
  <tr>
   <td><b>Core Components</b> </td>
   <td><b>HTML 5 input type</b> </td>
   <td><b>Details</b></td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html">Form Container</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#form">form </td>
   <td> Create a form to capture user inputs.
   </td>
  </tr>
  <tr>
   <td><a herf="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text-input.html">Text Input</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text">text</a></td>
   <td> Defines a single-line text input field. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input.html">Number Input</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number">number</a></td>
   <td>Lets user  enter a number input. You can also add built-in validation to reject non-numerical inputs. Lets user  enter a number input. You can also add built-in validation to reject non-numerical inputs. Initially, the input field is displayed as a number input. If a user applies a display pattern, it changes to text to allow the author to apply number formatting, since HTML 5 lacks support for display patterns. However, when the user clicks it, it returns to typing numbers.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker.html">Date Picker</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date">date </a></td>
   <td> Create an input field for entering a date. You have the option to input the date either through a text box, which validates the entry, or through a dedicated date picker interface. Initially, the native date input field is displayed. If a user applies a display pattern, it changes to text to allow the user to apply formatting, since HTML 5 lacks support for display patterns. However, when the user clicks it, it returns to typing a date.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment.html">File Attachment</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file">file</a></td>
   <td> Allows user to choose one or more files from the device storage. It supports enhanced file input validations, such as accepted file types, file size restrictions, and minimum/maximum file selection limits. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/drop-down.html"> Dropdown List</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a></td>
   <td> Allows users to select one or more options from a list of predefined options. The options can be of type String, Number, or Boolean.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group.html">Checkbox Group</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox">multiple checkbox</a></td>
   <td> Allow users to select one or more options from a list. Multiple checkboxes are generated with identical names, each corresponding to an item in the enum. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button.html">Radio Button Group</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio">multiple radio</a></td>
   <td> Allows a user to select one option from a group of related options. Multiple radio buttons are generated with identical names, each corresponding to an item in the enum.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/button.html">Button</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button">button</a></td>
   <td>A UI element that allows users to trigger an action when clicked. </td>
  </tr>
  <tr>
   <td><a href =""https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html">Panel</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset with legend</a></td>
   <td> Group sections within a form, where a nested *legend* element adds a caption for the form.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html">Wizard</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a></td>
   <td>Groups related sections within a form. It also controls the arrangement, supporting display options for positioning them at the top or at the left side. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text.html">Text</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p">p</a></td>
   <td>A p tag marks a paragraph. In visual content, paragraphs are chunks of text separated by blank lines or an indented first line</td>
  </tr>
     <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Submit button</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit">submit</a></td>
   <td> A UI element that enables users to submit a form to the server upon clicking. If a user adds a submit rule to a button, it functions as the submit button. </td>
  </tr>
     <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/reset-button.html">Reset button</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset">reset</a></td>
   <td>A UI element that resets a form upon clicking. If a user adds a reset rule to a button, it functions as the reset button. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/email-input.html">Email Input</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email">email</a></td>
   <td> Allows the user to enter and edit an email address. If the user adds the multiple attributes, a list of email addresses can be added or edited.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/telephone-input.html">Telephone Input</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel">tel</a></td>
   <td>Allows user to enter and edit a telephone number.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/header.html">Header</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header"> header</a></td>
   <td>It includes introductory content, typically a group of introductory or navigational aids. It is supported outside Form container. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/footer.html">Footer</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer">footer</a></td>
   <td> Contains information such as copyright data or links to related documents. It is supported outside Form container.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html">Accordion<a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Allows user to create expandable and collapsible sections in a form. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html">Horizontal tabs</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td>Organizes multiple sections of a form into separate tabs which are displayed horizontally.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/image.html">Image</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Allows user to include images in a form.</td>
  </tr><tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/title.html">Title</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Refers to the text that appears at the top of the form. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Switch</td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> A two-state toggle that allows user to select between two states such as enabling or disabling a feature, setting, or functionality.</td>
  </tr>
 </tbody>
</table> -->

## Mehr anzeigen

- [Erstellen und Anzeigen einer Vorschau eines Formulars](/help/edge/docs/forms/create-forms.md)
- [Formular zum Senden von Daten aktivieren](/help/edge/docs/forms/submit-forms.md)
- [Veröffentlichen eines Formulars auf der Siteseite](/help/edge/docs/forms/publish-forms.md)
- [Hinzufügen von Überprüfungen zu Formularfeldern](/help/edge/docs/forms/validate-forms.md)
- [Designs und Formularstil ändern](/help/edge/docs/forms/style-theme-forms.md)
