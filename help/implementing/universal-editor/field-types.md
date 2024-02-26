---
title: Modelldefinitionen, Felder und Komponententypen
description: Erfahren Sie anhand von Beispielen mehr über Felder und Komponententypen, die der universelle Editor in der Eigenschaftenleiste bearbeiten kann. Erfahren Sie, wie Sie Ihre eigene App instrumentieren können, indem Sie eine Modelldefinition erstellen und mit der Komponente verknüpfen.
exl-id: cb4567b8-ebec-477c-b7b9-53f25b533192
source-git-commit: bbe02f66b5bce3b919be4abd3b2de482a235b6ee
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 9%

---


# Modelldefinitionen, Felder und Komponententypen {#field-types}

Erfahren Sie anhand von Beispielen mehr über Felder und Komponententypen, die der universelle Editor in der Eigenschaftenleiste bearbeiten kann. Erfahren Sie, wie Sie Ihre eigene App instrumentieren können, indem Sie eine Modelldefinition erstellen und mit der Komponente verknüpfen.

{{universal-editor-status}}

## Übersicht {#overview}

Wenn Sie Ihre eigenen Apps für die Verwendung mit dem universellen Editor anpassen, müssen Sie die Komponenten instrumentieren und definieren, welche Felder und Komponententypen sie in der Eigenschaftenleiste des Editors bearbeiten können. Erstellen Sie dazu ein Modell und verknüpfen Sie es über die Komponente mit diesem.

Dieses Dokument bietet einen Überblick über eine Modelldefinition sowie über die Felder und die verfügbaren Komponententypen sowie Beispielkonfigurationen.

>[!TIP]
>
>Wenn Sie nicht genau wissen, wie Sie Ihre App für den universellen Editor instruieren können, lesen Sie das Dokument . [Übersicht über den universellen Editor für AEM Entwickler.](/help/implementing/universal-editor/developer-overview.md)

## Modelldefinitionsstruktur {#model-structure}

Um eine Komponente über die Eigenschaftenleiste im universellen Editor zu konfigurieren, muss eine Modelldefinition vorhanden und mit der Komponente verknüpft sein.

Die Modelldefinition ist eine JSON-Struktur, die mit einem Array von Modellen beginnt.

```json
[
  {
    "id": "model-id",        // must be unique
    "fields": []             // array of fields which shall be rendered in the properties rail
  }
]
```

Siehe **[Felder](#fields)** in diesem Dokument finden Sie weitere Informationen zur Definition der `fields` Array.

Um die Modelldefinition mit einer Komponente zu verwenden, muss die `data-aue-model` -Attribut verwendet werden.

```html
<div data-aue-resource="urn:datasource:/content/path" data-aue-type="component"  data-aue-model="model-id">Click me</div>
```

## Modelldefinition laden {#loading-model}

Nachdem ein Modell erstellt wurde, kann es als externe Datei referenziert werden.

```html
<script type="application/vnd.adobe.aue.model+json" src="<url-of-model-definition>"></script>
```

Alternativ können Sie das Modell auch inline definieren.

```html
<script type="application/vnd.adobe.aue.model+json">
  { ... model definition ... }
</script>
```

## Felder {#fields}

Ein Feldobjekt hat die folgende Typdefinition.

| Konfiguration | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `component` | `ComponentType` | Renderer der Komponente | Ja |
| `name` | `string` | Eigenschaft, in der die Daten beibehalten werden sollen | Ja |
| `label` | `FieldLabel` | Feldbezeichnung | Ja |
| `description` | `FieldDescription` | Beschreibung des Felds | Nein |
| `placeholder` | `string` | Platzhalter für das Feld | Nein |
| `value` | `FieldValue` | Standardwert | Nein |
| `valueType` | `ValueType` | Standardvalidierung, kann `string`, `string[]`, `number`, `date`, `boolean` | Nein |
| `required` | `boolean` | Ist das erforderliche Feld? | Nein |
| `readOnly` | `boolean` | Ist das Feld schreibgeschützt | Nein |
| `hidden` | `boolean` | Ist das Feld standardmäßig ausgeblendet? | Nein |
| `condition` | `RulesLogic` | Regel zum Anzeigen oder Ausblenden des Felds basierend auf einer [Bedingung](/help/implementing/universal-editor/customizing.md#conditionally-hide) | Nein |
| `multi` | `boolean` | Ist das Feld ein Mehrfachfeld? | Nein |
| `validation` | `ValidationType` | Validierungsregeln für das Feld | Nein |
| `raw` | `unknown` | Rohdaten, die von der Komponente verwendet werden können | Nein |

### Komponententypen {#component-types}

Im Folgenden finden Sie die Komponententypen, die für das Rendern von Feldern verwendet werden können.

#### AEM Tag {#aem-tag}

Ein AEM Tag-Komponententyp aktiviert eine AEM Tag-Auswahl, die zum Anhängen von Tags an die Komponente verwendet werden kann.

>[!BEGINTABS]

>[!TAB Beispiel]

```json
{
  "id": "aem-tag-picker",
  "fields": [
    {
      "component": "aem-tag",
      "label": "AEM Tag Picker",
      "name": "cq:tags",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot AEM Tag-Komponententyps](assets/component-types/aem-tag-picker.png)

>[!ENDTABS]

#### AEM {#aem-content}

Der Typ AEM Inhaltskomponente ermöglicht eine AEM Inhaltsauswahl, die zum Festlegen von Inhaltsverweisen verwendet werden kann.

>[!BEGINTABS]

>[!TAB Beispiel]

```json
{
  "id": "aem-content-picker",
  "fields": [
    {
      "component": "aem-content",
      "name": "reference",
      "value": "",
      "label": "AEM Content Picker",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot AEM Inhaltskomponententyps](assets/component-types/aem-content-picker.png)

>[!ENDTABS]

#### Boolesch {#boolean}

Ein boolescher Komponententyp speichert einen einfachen true/false -Wert, der als Umschalter gerendert wird. Es bietet einen zusätzlichen Validierungstyp.

| Validierungstyp | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `customErrorMsg` | `string` | Meldung, die angezeigt wird, wenn der eingegebene Wert kein boolescher Wert ist | Nein |

>[!BEGINTABS]

>[!TAB Beispiel 1]

```json
{
  "id": "boolean",
  "fields": [
    {
      "component": "boolean",
      "label": "Boolean",
      "name": "boolean",
      "valueType": "boolean"
    }
  ]
}
```

>[!TAB Beispiel 2]

```json
{
  "id": "another-boolean",
  "fields": [
    {
      "component": "boolean",
      "label": "Boolean",
      "name": "boolean",
      "valueType": "boolean",
      "validation": {
        "customErrorMsg": "Think, McFly. Think!"
      }
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des booleschen Komponententyps](assets/component-types/boolean.png)

>[!ENDTABS]

#### Kontrollkästchen-Gruppe {#checkbox-group}

Ähnlich wie bei einem booleschen Wert ermöglicht ein Kontrollkästchengruppen-Komponententyp die Auswahl mehrerer true/false -Elemente, die als mehrere Kontrollkästchen gerendert werden.

>[!BEGINTABS]

>[!TAB Beispiel]

```json
{
  "id": "checkbox-group",
  "fields": [
    {
      "component": "checkbox-group",
      "label": "Checkbox Group",
      "name": "checkbox",
      "valueType": "string[]",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Kontrollkästchengruppen-Komponententyps](assets/component-types/checkbox-group.png)

>[!ENDTABS]

#### Container {#container}

Ein Container-Komponententyp ermöglicht die Gruppierung von Komponenten. Es bietet eine zusätzliche Konfiguration.

| Konfiguration | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `collapsible` | `boolean` | Ist der Container ausblendbar? | Nein |

>[!BEGINTABS]

>[!TAB Beispiel]

```json
 {
  "id": "container",
  "fields": [
    {
      "component": "container",
      "label": "Container",
      "name": "container",
      "valueType": "string",
      "collapsible": true,
      "fields": [
        {
          "component": "text-input",
          "label": "Simple Text 1",
          "name": "text",
          "valueType": "string"
        },
        {
          "component": "text-input",
          "label": "Simple Text 2",
          "name": "text2",
          "valueType": "string"
        }
      ]
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Container-Komponententyps](assets/component-types/container.png)

#### Inhaltsfragment {#content-fragment}

Mit der Auswahl für Inhaltsfragmente können Sie eine [Inhaltsfragment](/help/sites-cloud/authoring/fragments/content-fragments.md) und deren Varianten (falls erforderlich). Es bietet eine zusätzliche Konfiguration.

| Konfiguration | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `variationName` | `string` | Variablenname zum Speichern der ausgewählten Variante. Wenn nicht definiert, wird keine Variantenauswahl angezeigt | Nein |

>[!BEGINTABS]

>[!TAB Beispiel 1]

```json
[
  {
    "id": "aem-content-fragment",
    "fields": [
      {
        "component": "aem-content-fragment",
        "name": "picker",
        "label": "Content Fragment Picker",
        "valueType": "string",
        "variationName": "contentFragmentVariation"
      }
    ]
  }
]
```

>[!TAB Screenshot]

![Screenshot der Inhaltsfragmentauswahl](assets/component-types/aem-content-fragment.png)

>[!ENDTABS]

#### Datum/Uhrzeit {#date-time}

Ein Datums-/Uhrzeitkomponenten-Typ ermöglicht die Spezifikation eines Datums, einer Uhrzeit oder einer Kombination daraus. Es bietet zusätzliche Konfigurationen.

| Konfiguration | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `displayFormat` | `string` | Format für die Anzeige der Datums-Zeichenfolge | Ja |
| `valueFormat` | `string` | Format für die Speicherung der Datums-Zeichenfolge | Ja |

Es bietet außerdem einen zusätzlichen Validierungstyp.

| Validierungstyp | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `customErrorMsg` | `string` | Meldung, die bei `valueFormat` ist nicht erfüllt | Nein |

>[!BEGINTABS]

>[!TAB Beispiel 1]

```json
{
  "id": "date-time",
  "fields": [
    {
      "component": "date-time",
      "label": "Date & Time",
      "name": "date",
      "valueType": "date"
    }
  ]
}
```

>[!TAB Beispiel 2]

```json
{
  "id": "another-date-time",
  "fields": [
    {
      "component": "date-time",
       "valueType": "date-time",
      "name": "field1",
      "label": "Date Time",
      "description": "This is a date time field that stores both date and time.",
      "required": true,
      "placeholder": "YYYY-MM-DD HH:mm:ss",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Marty! You have to come back with me!"
      }
    },
    {
      "component": "date-time",
      "valueType": "date",
      "name": "field2",
      "label": "Another Date Time",
      "description": "This is another date time field that only stores the date.",
      "required": true,
      "placeholder": "YYYY-MM-DD",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Back to the future!"
      }
    },
    {
      "component": "date-time",
      "valueType": "time",
      "name": "field3",
      "label": "Yet Another Date Time",
      "description": "This is another date time field that only stores the time.",
      "required": true,
      "placeholder": "HH:mm:ss",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Great Scott!"
      }
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Datums- und Uhrzeitkomponenten-Typs](assets/component-types/date-time.png)

>[!ENDTABS]

#### Experience Fragment {#experience-fragment}

Mit der Experience Fragment-Auswahl können Sie eine [Experience Fragment](/help/sites-cloud/authoring/fragments/experience-fragments.md) und deren Varianten (falls erforderlich). Es bietet eine zusätzliche Konfiguration.

| Konfiguration | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `variationName` | `string` | Variablenname zum Speichern der ausgewählten Variante. Wenn nicht definiert, wird keine Variantenauswahl angezeigt | Nein |

>[!BEGINTABS]

>[!TAB Beispiel 1]

```json
[
  {
    "id": "aem-experience-fragment",
    "fields": [
      {
        "component": "aem-experience-fragment",
        "name": "picker",
        "label": "Experience Fragment Picker",
        "valueType": "string",
        "variationName": "experienceFragmentVariation"
      }
    ]
  }
]
```

>[!TAB Screenshot]

![Screenshot der Experience Fragment-Auswahl](assets/component-types/aem-experience-fragment.png)

>[!ENDTABS]


#### Mehrfachauswahl {#multiselect}

Ein Komponententyp &quot;multiselect&quot;zeigt mehrere Elemente zur Auswahl in einer Dropdown-Liste an, einschließlich der Möglichkeit, die auswählbaren Elemente zu gruppieren.

>[!BEGINTABS]

>[!TAB Beispiel 1]

```json
{
  "id": "multiselect",
  "fields": [
    {
      "component": "multiselect",
      "name": "multiselect",
      "label": "Multi Select",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB Beispiel 2]

```json
{
  "id": "multiselect-grouped",
  "fields": [
    {
      "component": "multiselect",
      "name": "property",
      "label": "Multiselect field",
      "valueType": "string",
      "required": true,
      "maxSize": 2,
      "options": [
        {
          "name": "Theme",
          "children": [
            { "name": "Light", "value": "light" },
            { "name": "Dark",  "value": "dark" }
          ]
        },
        {
          "name": "Type",
          "children": [
            { "name": "Alpha", "value": "alpha" },
            { "name": "Beta", "value": "beta" },
            { "name": "Gamma", "value": "gamma" }
          ]
        }
      ]
    }
  ]
}
```

>[!TAB Screenshots]

![Screenshot des Multiselect-Komponententyps](assets/component-types/multiselect.png)
![Screenshot des Multiselect-Komponententyps mit Gruppierung](assets/component-types/multiselect-group.png)

>[!ENDTABS]

#### Zahl {#number}

Ein Komponententyp vom Typ Zahl ermöglicht die Eingabe einer Zahl. Es bietet zusätzliche Validierungstypen.

| Validierungstyp | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `numberMin` | `number` | Mindestens zulässig | Nein |
| `numberMax` | `number` | Maximale zulässige Anzahl | Nein |
| `customErrorMsg` | `string` | Meldung, die bei `numberMin` oder `numberMax` ist nicht erfüllt | Nein |

>[!BEGINTABS]

>[!TAB Beispiel 1]

```json
{
  "id": "number",
  "fields": [
    {
      "component": "number",
      "name": "number",
      "label": "Number",
      "valueType": "number",
      "value": 0
    }
  ]
}
```

>[!TAB Beispiel 2]

```json
{
  "id": "another-number",
  "fields": [
   {
      "component": "number",
      "valueType": "number",
      "name": "field1",
      "label": "Number Field",
      "description": "This is a number field.",
      "required": true,
      "placeholder": null,
      "validation": {
        "numberMin": 0,
        "numberMax": 88,
        "customErrorMsg": "You also need 1.21 gigawatts."
      }
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Komponententyps &quot;Zahl&quot;](assets/component-types/number.png)

>[!ENDTABS]

#### Optionsfeldgruppe {#radio-group}

Ein Optionsfeldgruppen-Komponententyp ermöglicht eine sich gegenseitig ausschließende Auswahl aus mehreren Optionen, die als Gruppe ähnlich einer Kontrollkästchengruppe gerendert werden.

>[!BEGINTABS]

>[!TAB Beispiel]

```json
{
  "id": "radio-group",
  "fields": [
    {
      "component": "radio-group",
      "label": "Radio Group",
      "name": "radio",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Komponententyps einer Optionsfeldgruppe](assets/component-types/radio.png)

>[!ENDTABS]

#### Verweis {#reference}

Ein Referenzkomponententyp ermöglicht einen Verweis auf ein anderes Datenobjekt aus dem aktuellen Objekt.

>[!BEGINTABS]

>[!TAB Beispiel]

```json
{
  "id": "reference",
  "fields": [
    {
      "component": "reference",
      "label": "Reference",
      "name": "reference",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Referenzkomponententyps](assets/component-types/reference.png)

>[!ENDTABS]

#### Auswählen {#select}

Ein Typ &quot;Komponente auswählen&quot;ermöglicht die Auswahl einer einzelnen Option aus einer Liste vordefinierter Optionen in einem Dropdown-Menü.

>[!BEGINTABS]

>[!TAB Beispiel]

```json
{
  "id": "select",
  "fields": [
    {
      "component": "select",
      "label": "Select",
      "name": "select",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des ausgewählten Komponententyps](assets/component-types/select.png)

>[!ENDTABS]

#### Registerkarte {#tab}

Mit einem Registerkarten-Komponententyp können Sie andere Eingabefelder auf mehreren Registerkarten gruppieren, um die Layout-Organisation für Autoren zu verbessern.

A `tab` -Definition kann als Trennzeichen im Array von `fields`. Alles, was hinter einer `tab` wird auf dieser Registerkarte platziert, bis eine neue `tab` gefunden wird, wobei die folgenden Elemente auf der neuen Registerkarte platziert werden.

Wenn Sie Elemente haben möchten, die über allen Registerkarten angezeigt werden, müssen diese vor allen Registerkarten definiert werden.

>[!BEGINTABS]

>[!TAB Beispiel]

```json
{
  "id": "tab",
  "fields": [
    {
      "component": "tab",
      "label": "Tab 1",
      "name": "tab1"
    },
    {
      "component": "text-input",
      "label": "Text 1",
      "name": "text1",
      "valueType": "string"
    },
    {
      "component": "tab",
      "label": "Tab 2",
      "name": "tab2"
    },
    {
      "component": "text-input",
      "label": "Text 2",
      "name": "text2",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Registerkarten-Komponententyps](assets/component-types/tab.png)

>[!ENDTABS]

#### Textbereich {#text-area}

Ein Textbereich ermöglicht eine mehrzeilige Rich-Text-Eingabe. Es bietet zusätzliche Validierungstypen.

| Validierungstyp | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `maxSize` | `number` | Maximale Anzahl erlaubter Zeichen | Nein |
| `customErrorMsg` | `string` | Meldung, die bei `maxSize` überschritten wird | Nein |

>[!BEGINTABS]

>[!TAB Beispiel 1]

```json
{
  "id": "richtext",
  "fields": [
    {
      "component": "text-area",
      "name": "rte",
      "label": "Rich Text",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Beispiel 2]

```json
{
  "id": "another-richtext",
  "fields": [
    {
      "component": "text-area",
      "name": "rte",
      "label": "Rich Text",
      "valueType": "string",
      "validation": {
        "maxSize": 1000,
        "customErrorMsg": "That's about as funny as a screen door on a battleship."
      }
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Textbereich-Komponententyps](assets/component-types/richtext.png)

>[!ENDTABS]

#### Texteingabe {#text-input}

Eine Texteingabe ermöglicht eine einzelne Textzeile.  Es enthält zusätzliche Validierungstypen.

| Validierungstyp | Werttyp | Beschreibung | Erforderlich |
|---|---|---|---|
| `minLength` | `number` | Mindestens zulässige Zeichenanzahl | Nein |
| `maxLength` | `number` | Maximale Zeichenanzahl zulässig | Nein |
| `regExp` | `string` | Regulärer Ausdruck, der dem Eingabetext entsprechen muss | Nein |
| `customErrorMsg` | `string` | Meldung, die bei `minLength`, `maxLength`, und/oder `regExp` verletzt | Nein |

>[!BEGINTABS]

>[!TAB Beispiel 1]

```json
{
  "id": "simpletext",
  "fields": [
    {
      "component": "text-input",
      "name": "text",
      "label": "Simple Text",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Beispiel 2]

```json
{
  "id": "another simpletext",
  "fields": [
    {
      "component": "text-input",
      "name": "text",
      "label": "Simple Text",
      "valueType": "string",
      "description": "This is a text input with validation.",
      "required": true,
      "validation": {
        "minLength": 1955,
        "maxLength": 1985,
        "regExp": "^foo:.*",
        "customErrorMsg": "Why don't you make like a tree and get outta here?"
      }
    }
  ]
}
```

>[!TAB Screenshot]

![Screenshot des Komponententyps für die Texteingabe](assets/component-types/simpletext.png)

>[!ENDTABS]
