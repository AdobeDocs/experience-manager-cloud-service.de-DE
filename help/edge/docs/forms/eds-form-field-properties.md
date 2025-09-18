---
title: Meistern der Feldeigenschaften von adaptiven Forms-Blöcken
description: Erstellen Sie leistungsstarke Formulare schneller mithilfe von Tabellen und adaptiven Forms-Blockfeldeigenschaften! In diesem Handbuch werden alle vom EDS Forms Block unterstützten Eigenschaften aufgelistet.
feature: Edge Delivery Services
source-git-commit: ccc6439f68d8199154d4cd664b9cdb6428460a64
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 4%

---


# Adaptive Forms-Blockfeldeigenschaften

In diesem Dokument wird zusammengefasst, wie das JSON-Schema gerenderten HTML in `blocks/form/form.js` zugeordnet ist, wobei der Schwerpunkt auf der Art und Weise liegt, wie Felder identifiziert und gerendert werden, auf allgemeinen Mustern und feldspezifischen Unterschieden.

## Wie werden Felder (`fieldType`) identifiziert?

Jedes Feld im JSON-Schema verfügt über eine `fieldType`-Eigenschaft, die bestimmt, wie es gerendert wird. `fieldType` kann sein:

- **Ein spezieller Typ**\
  Beispiele: `drop-down`, `radio-group`, `checkbox-group`, `panel`, `plain-text`, `image`, `heading` usw.
- **Ein gültiger HTML-Eingabetyp**\
  Beispiele: `text`, `number`, `email`, `date`, `password`, `tel`, `range`, `file` usw.
- **Ein Typ mit einem `-input` Suffix**\
  Beispiele: `text-input`, `number-input` usw. (normalisiert auf den Basistyp wie `text`, `number`).

Wenn der `fieldType` einem bestimmten Typ entspricht, wird **benutzerdefinierter Renderer** verwendet. Andernfalls wird er als **Standardeingabetyp“**.

In den folgenden Abschnitten finden Sie [vollständige HTML-Struktur und ](#common-html-structure) für jeden Feldtyp.

## Von Feldern verwendete allgemeine Eigenschaften

Im Folgenden finden Sie die von den meisten Feldern verwendeten Eigenschaften:

- `id`: Gibt die Element-ID an und unterstützt Barrierefreiheit.
- `name`: Definiert das `name` für Eingabe-, Auswahl- oder Feldsatzelemente.
- `label.value`, `label.richText`, `label.visible`: Gibt den Titel-/Legendentext, den HTML-Inhalt und die Sichtbarkeit an.
- `value`: Stellt den aktuellen Wert des Felds dar.
- `required`: Fügt das `required` oder Validierungsdaten hinzu.
- `readOnly`, `enabled`: Steuert, ob das Feld bearbeitbar oder deaktiviert ist.
- `description`: Zeigt Hilfetext unter dem Feld an.
- `tooltip`: Legt das `title` für Eingaben fest.
- `constraintMessages`: Bietet benutzerdefinierte Fehlermeldungen als Datenattribute.

## Allgemeine HTML-Struktur

Die meisten Felder werden in einem Wrapper gerendert, der eine Beschriftung und optionalen Hilfetext enthält. Das folgende Snippet veranschaulicht die Struktur:

```html
<div class="<fieldType>-wrapper field-wrapper field-<name>" data-id="<id>">
<label for="<id>" class="field-label">Label</label>
<!-- Field-specific input/element here -->
<div class="field-description" id="<id>-description">Description or error
message</div>
</div>
```

Für Gruppen (Optionsfelder/Kontrollkästchen) und Bereiche wird anstelle eines `<fieldset>` ein `<legend>` mit einem `<div>/<label>` verwendet. Der Hilfetext <div> ist nur vorhanden, wenn die Beschreibung festgelegt ist.

## Fehlermeldungsanzeige

Fehlermeldungen werden in demselben `.field-description` angezeigt, das für den Hilfetext verwendet wird und dynamisch aktualisiert wird.

**Wenn ein Feld ungültig ist**:

- Dem Wrapper (z. B. `.field-wrapper`) wird die Klasse `.field-invalid` zugewiesen.
- Der `.field-description` wird durch die entsprechende Fehlermeldung ersetzt.

**Wenn das Feld gültig wird**:

- Die `.field-invalid` wird entfernt.
- Die `.field-description` wird auf den ursprünglichen Hilfetext zurückgesetzt (falls verfügbar) oder entfernt, wenn kein Hilfetext vorhanden ist.

Benutzerdefinierte Fehlermeldungen können mithilfe der `constraintMessages`-Eigenschaft in der JSON definiert werden.\
Diese werden dem Wrapper als `data-<constraint>ErrorMessage`-Attribute hinzugefügt (z. B. `data-requiredErrorMessage`).

## Standardeingabetypen (HTML-Eingabe oder `*-input`)

Wenn `fieldType` kein spezieller Typ ist, wird er als standardmäßiger HTML-Eingabetyp oder als `<type>-input` behandelt, z. B. `text`, `number`, `email`, `date`, `text-input`, `number-input`.

- Das Suffix `-input` wird entfernt, und der Basistyp wird als `type` der Eingabe verwendet.
- Diese Typen werden standardmäßig in `renderField()` behandelt.
Gängige Standardeingabetypen sind `text`, `number`, `email`, `date`, `password`, `tel`, `range`, `file` usw.  Sie akzeptieren auch `text-input`, `number-input` usw., die auf den Basistyp normalisiert sind.

## Einschränkungen für Standardeingabetypen

Abhängig von JSON-Eigenschaften werden Begrenzungen als Attribute zum Eingabeelement hinzugefügt.

| JSON-Eigenschaft | HTML-Attribut | Gilt für |
|--------------|---------------|------------|
| maxLength | maxLength | Text, E-Mail, Passwort, Tel |
| minLength | minlength | Text, E-Mail, Passwort, Tel |
| pattern | pattern | Text, E-Mail, Passwort, Tel |
| maximum | max. | Zahl, Bereich, Datum |
| minimum | Min. | Zahl, Bereich, Datum |
| Schritt | Schritt | Zahl, Bereich, Datum |
| Akzeptieren der Bedingungen | Akzeptieren der Bedingungen | Datei |
| Mehrfach | Mehrfach | Datei |
| maxOccur | data-max | Bedienfeld |
| minOccur | data-min | Bedienfeld |

>[!NOTE]
>
> `multiple` ist eine boolesche Eigenschaft. Wenn „true“, wird das `multiple` hinzugefügt.

Diese Attribute werden automatisch vom Formular-Renderer auf der Grundlage der JSON-Definition des Felds festgelegt.

## Beispiel: HTML-Struktur mit Einschränkungen

Das folgende Beispiel zeigt, wie ein Zahlenfeld mit Validierungsbeschränkungen und Attributen zur Fehlerbehandlung gerendert wird.

```html
<div class="number-wrapper field-wrapper field-age" data-id="age"
data-required="true"
data-minimumErrorMessage="Too small" data-maximumErrorMessage="Too large">
<label for="age" class="field-label">Age</label>
<input type="number"
id="age" name="age"
value="30" required min="18"
max="99" step="1"
placeholder="Enter your age" />
<div class="field-description" id="age-description"> Description or error message
</div>
</div>
```

Jeder Teil der HTML-Struktur spielt eine Rolle bei der Datenbindung, Validierung und Anzeige von Hilfe- oder Fehlermeldungen.

## Feldspezifische Eigenschaften und ihre HTML-Strukturen

### Dropdown-Liste

**Zusätzliche Eigenschaften:**

- `enum`/`enumNames`: Definieren Sie die Optionswerte und deren Anzeigenamen für die Dropdown-Liste.
- `type`: Aktiviert die Mehrfachauswahl, wenn auf &quot;`array`&quot; gesetzt.
- `placeholder`: Fügt eine deaktivierte Platzhalteroption hinzu, um Benutzer vor der Auswahl zu führen.

Zum Beispiel:

```html
<div class="drop-down-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true"
data-requiredErrorMessage="This field is required">
<label for="<id>" class="field-label">Label</label>
<select id="<id>" name="<name>" required title="Tooltip" multiple>
<option disabled selected value="">Placeholder</option>
<option value="opt1">Option 1</option>
<option value="opt2">Option 2</option>
</select>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Nur Text

**Zusätzliche Eigenschaften**:

- `richText`: Wenn „true“, wird HTML im Absatz gerendert.

Zum Beispiel:

```html
<div class="plain-text-wrapper field-wrapper field-<name>" data-id="<id>">
<label for="<id>" class="field-label">Label</label>
<p>Text or <a href="..." target="_blank">link</a></p>
</div>
```

### Kontrollkästchen

**Zusätzliche Eigenschaften**:

- `enum`: Definiert die Werte für den aktivierten und den nicht aktivierten Status des Kontrollkästchens.
- `properties.variant / properties.alignment`: Gibt den visuellen Stil und die Ausrichtung für Kontrollkästchen im Switch-Stil an.

Zum Beispiel:

```html
<div class="checkbox-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true"
data-requiredErrorMessage="Please check this box">
<label for="<id>" class="field-label">Label</label>
<input type="checkbox"
id="<id>"
name="<name>" value="on"
required
data-unchecked-value="off" />
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Schaltfläche

**Zusätzliche Eigenschaften**:

- `buttonType`: Gibt das Verhalten der Schaltfläche an, indem der Typ (Schaltfläche, Senden oder Zurücksetzen) festgelegt wird.

Zum Beispiel:

```html
<div class="button-wrapper field-wrapper field-<name>" data-id="<id>">
<button id="<id>" name="<name>" type="submit" class="button"> Label
</button>
</div>
```

### mehrzeiliger Eingang

**Zusätzliche Eigenschaften**:

- `minLength`: Gibt die Mindestanzahl von Zeichen an, die in einer Text- oder Textbereichseingabe zulässig ist.
- `maxLength`: Gibt die maximale Anzahl von Zeichen an, die in einer Text- oder Textbereichseingabe zulässig ist.
- `pattern`: Definiert einen regulären Ausdruck, mit dem der Eingabewert übereinstimmen muss, damit er als gültig gilt.
- `placeholder`: Zeigt Platzhaltertext im Eingabe- oder Textbereich an, bis ein Wert eingegeben wird.

Zum Beispiel:

```html
<div class="multiline-wrapper field-wrapper field-<name>" data-id="<id>"
data-minLengthErrorMessage="Too short" data-maxLengthErrorMessage="Too long">
<label for="<id>" class="field-label">Label</label>
<textarea id="<id>"
name="<name>" required
minlength="2"
maxlength="100"
pattern="[A-Za-z]+"
placeholder="Type here..."></textarea>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Panel

**Zusätzliche Eigenschaften**:

- `repeatable`: Gibt an, ob der Bereich dynamisch wiederholt werden kann.
- `minOccur`: Legt die Mindestanzahl an erforderlichen Bereichsinstanzen fest.   maxOccur: Legt die maximal zulässige Anzahl von Bereichsinstanzen fest.
- `properties.variant`: Definiert den visuellen Stil oder die visuelle Variante des Bereichs.
- `properties.colspan`: Gibt an, wie viele Spalten sich der Bereich in einem Rasterlayout erstreckt.
- `index`: Gibt die Position des Bereichs innerhalb seines übergeordneten Containers an.
- `fieldset`: Gruppiert verwandte Felder unter einem `<fieldset>` mit einer Legende oder Beschriftung.

Zum Beispiel:

```html
<fieldset class="panel-wrapper field-wrapper field-<name>" data-id="<id>"
name="<name>"
data-repeatable="true" data-index="0">
<legend class="field-label">Label</legend>
<!-- Nested fields here -->
<button type="button" class="add">Add</button>
<button type="button" class="remove">Remove</button>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### Optionsfeld

**Zusätzliche Eigenschaften**:

- `enum`: Definiert den Satz zulässiger Werte für das Optionsfeld, die als Wertattribut für jede Optionsfeldoption verwendet werden.

Zum Beispiel:

```html
<div class="radio-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true">
<label for="<id>" class="field-label">Label</label>
<input type="radio" id="<id>" name="<name>" value="opt1" required />
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Optionsfeldgruppe

**Zusätzliche Eigenschaften**:

- `enum`: Definiert die Liste der Optionswerte für die Optionsfeldgruppe, die als Wert der einzelnen Optionsfelder verwendet wird.
- `enumNames`: Stellt Anzeigebeschriftungen für die Optionsfelder bereit, die mit der Reihenfolge der Aufzählung übereinstimmen.

Zum Beispiel:

```html
<fieldset class="radio-group-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true">
<legend class="field-label">Label</legend>
<div>
<input type="radio" id="<id>-0" name="<name>" value="opt1" required />
<label for="<id>-0">Option 1</label>
</div>
<div>
<input type="radio" id="<id>-1" name="<name>" value="opt2" />
<label for="<id>-1">Option 2</label>
</div>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### **Kontrollkästchen-Gruppe**

**Zusätzliche Eigenschaften**:

- `enum`: Definiert die Liste der Optionswerte für die Kontrollkästchen-Gruppe, die als Wert der einzelnen Kontrollkästchen verwendet werden.
- `enumNames`: Stellt Anzeigebeschriftungen für die Kontrollkästchen bereit, die mit der Reihenfolge der Aufzählung übereinstimmen.
- `minItems`: Legt die Mindestanzahl von Kontrollkästchen fest, die für die Gültigkeit ausgewählt werden müssen.
- `maxItems`: Legt die maximale Anzahl von Kontrollkästchen fest, die aktiviert werden können, bevor ein Fehler ausgelöst wird.

Zum Beispiel:

```html
<fieldset class="checkbox-group-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true" data-minItems="1"
data-maxItems="3">
<legend class="field-label">Label</legend>
<div>
<input type="checkbox" id="<id>-0" name="<name>" value="opt1" required />
<label for="<id>-0">Option 1</label>
</div>
<div>
<input type="checkbox" id="<id>-1" name="<name>" value="opt2" />
<label for="<id>-1">Option 2</label>
</div>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### Bild

**Zusätzliche Eigenschaften**:

- `value / properties['fd:repoPath']`: Definiert den Quellpfad des Bildes oder den Repository-Pfad für das Rendern des Bildes.
- `altText`: Bietet alternativen Text für das Bild (alt-Attribut), um die Barrierefreiheit zu verbessern.

Zum Beispiel:

```html
<div class="image-wrapper field-wrapper field-<name>" data-id="<id>">
<picture>
<img src="..." alt="..." />
<!-- Optimized sources -->
</picture>
</div>
```

### Überschrift

**Zusätzliche Eigenschaften**:

- `value`: Gibt den Textinhalt an, der innerhalb des Überschriftenelements angezeigt werden soll (z. B. `<h2>`).

Zum Beispiel:

```html
<div class="heading-wrapper field-wrapper field-<name>" data-id="<id>">
<h2 id="<id>">Heading Text</h2>
</div>
```

Weitere Informationen finden Sie in der Implementierung in `blocks/form/form.js` und `blocks/form/util.js`.


<!--Each form field is represented as a dedicated row in the spreadsheet, analogous to fields in a database table. The column headers act as labels for the various properties supported by the form field block.

Think of your form as a table in a spreadsheet, where each line represents a different question or piece of information you want to collect. The table headings tell you what kind of answers you can expect for each section.

The below table lists all the properties that are supported by the Adaptive Forms Block.

**Master Your Forms with These Adaptive Forms Block Field Properties:**

This table details all the properties you can use to customize your Adaptive Forms Block fields:

| Property | Description | Example |
|---|---|---|
| **Type** | [HTML input type](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) (text, email, number, etc.), [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), [select](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select), [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) | `text`, `email`, `radio`, `select` |
| **Name** | This defines the unique identifier for submitted data (e.g., 'email' for an email address field).  Choose a clear and unique name for each field, as the name serves as internal field identifier used for data mapping during submission. | `user_name`, `email_address` |
| **Label** | User-friendly field label | `"Full Name"`, `"Choose your country"` |
| **Value** | Default value displayed | `"John Doe"`, `"United States"` |
| **Placeholder** | Hint text within the field | `"Enter your email address"` |
| **Description** | Help text for users | `"Please enter a valid email address"` |
| **Visible** | Show/hide the field initially | `true`, `false` |
| **Mandatory** | Require a value from the user | `true`, `false` |
| **Min/Max** | Set minimum/maximum values (number, date, text length) | `18` (age), `2025-12-31` (date) |
| **Accept** | Allowed file types for file upload | `"image/jpeg,image/png"` |
| **Multiple** | Allow multiple file selections | `true`, `false` |
| **Options** | Comma-separated list for dropdown menus | `"Option 1, Option 2, Option 3"` |
| **Checked** | Default-selected radio button/checkbox | `true`, `false` |
| **Fieldset** | Group fields together | Fieldset name (e.g., `"Personal Information"`) |-->

