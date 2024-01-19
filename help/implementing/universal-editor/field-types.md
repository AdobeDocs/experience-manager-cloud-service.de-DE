---
title: Feldtypen
description: Erfahren Sie mehr über die verschiedenen Feldtypen, die der universelle Editor in der Komponentenleiste bearbeiten kann, mit Beispielen dafür, wie Sie Ihre eigene App instrumentieren können.
exl-id: cb4567b8-ebec-477c-b7b9-53f25b533192
source-git-commit: 7ef3efa6e074778b7b3e3a8159056200b2663b30
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 7%

---


# Feldtypen {#field-types}

Erfahren Sie mehr über die verschiedenen Feldtypen, die der universelle Editor in der Komponentenleiste bearbeiten kann, mit Beispielen dafür, wie Sie Ihre eigene App instrumentieren können.

{{universal-editor-status}}

## Übersicht {#overview}

Wenn Sie Ihre eigenen Apps für die Verwendung mit dem universellen Editor anpassen, müssen Sie die Komponenten instrumentieren und definieren, welche Datentypen sie in der Komponentenleiste des Editors bearbeiten können.

Dieses Dokument bietet einen Überblick über die verfügbaren Feldtypen sowie Beispielkonfigurationen.

>[!TIP]
>
>Wenn Sie nicht genau wissen, wie Sie Ihre App für den universellen Editor instruieren können, lesen Sie das Dokument . [Übersicht über den universellen Editor für AEM Entwickler.](/help/implementing/universal-editor/developer-overview.md)

## Boolesch {#boolean}

Ein boolesches Feld speichert einen einfachen true/false -Wert, der als Kontrollkästchen gerendert wird.

### Beispiel {#sample-boolean}

```json
{
  "fields": [   
   {
      "component": "boolean",
      "valueType": "boolean",
      "name": "field1",
      "label": "Boolean Field",
      "description": "This is a boolean field.",
      "required": true,
      "placeholder": null,
      "validation": {
        "customErrorMsg": "This is an error."
      }
    }
  ]
}
```

## Kontrollkästchen-Gruppe {#checkbox-group}

Ähnlich wie bei einem booleschen Wert ermöglicht eine Kontrollkästchengruppe die Auswahl mehrerer true/false -Elemente.

### Beispiel {#sample-checkbox-group}

```json
{
  "fields": [   
   {
      "component": "checkbox-group",
      "valueType": "string-array",
      "name": "field1",
      "label": "Checkbox Group",
      "description": "This is a checkbox group.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "First option", "value": "one" },
        { "name": "Second option", "value": "two" },
        { "name": "Third option", "value": "three" }
      ]
    }
  ]
}
```

## Datum/Uhrzeit {#date-time}

Ein Datums-/Uhrzeitfeld ermöglicht die Angabe eines Datums, einer Uhrzeit oder einer Kombination davon.

### Beispiel {#sample-date-time}

```json
{
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

## Zahl {#number}

Ein Zahlenfeld ermöglicht die Eingabe einer Zahl.

### Beispiel {#sample-number}

```json
{
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
        "numberMin": null,
        "numberMax": null,
        "customErrorMsg": "Please don't do that."
      }
    }
  ]
}
```

## Optionsfeldgruppe {#radio-group}

Eine Optionsfeldgruppe ermöglicht eine sich gegenseitig ausschließende Auswahl aus mehreren Optionen, die als Gruppe ähnlich einer Kontrollkästchengruppe gerendert werden.

### Beispiel {#sample-radio-group}

```json
{
  "fields": [   
   {
      "component": "radio-group",
      "valueType": "string",
      "name": "field1",
      "label": "Radio Group",
      "description": "This is a radio group.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "Option One", "value": "one" },
        { "name": "Option Two", "value": "two" },
        { "name": "Option Three", "value": "three" }
      ]
    }
  ]
}
```

## Verweis {#reference}

Eine Referenz ermöglicht die Spezifikation eines anderen Datenobjekts als Verweis vom aktuellen Objekt.

## Auswählen {#select}

Eine Auswahl ermöglicht die Auswahl einer oder mehrerer vordefinierter Optionen in einem Dropdown-Menü.

### Beispiel {#sample-select}

```json
{
  "fields": [   
   {
      "component": "select",
      "valueType": "string",
      "name": "field1",
      "label": "Select",
      "description": "This is a select.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "Option One", "value": "one" },
        { "name": "Option Two", "value": "two" },
        { "name": "Option Three", "value": "three" }
      ],
      "emptyOption": true
    }
  ]
}
```

## Textbereich {#text-area}

Ein Textbereich ermöglicht die mehrzeilige Texteingabe.

### Beispiel {#sample-text-area}

```json
{
  "fields": [   
   {
      "component": "text-area",
      "valueType": "string",
      "name": "field1",
      "label": "Text Area",
      "description": "This is a text area.",
      "required": true,
      "multi": true,
      "placeholder": null,
      "mimeType": "text/x-markdown"
    }
  ]
}
```

## Texteingabe {#text-input}

Eine Texteingabe ermöglicht eine einzelne Textzeile.

### Beispiel {#sample-text-input}

```json
{
  "fields": [   
   {
      "component": "text-input",
      "valueType": "string",
      "name": "field1",
      "label": "Text Input",
      "description": "This is a text input.",
      "required": true,
      "multi": true,
      "placeholder": null
    },
    {
      "component": "text-input",
      "valueType": "string",
      "name": "field2",
      "label": "Another Text Input",
      "description": "This is a text input with validation.",
      "required": true,
      "multi": true,
      "placeholder": null,
      "validation": {
        "minLength": 5,
        "maxLength": 10,
        "regExp": "^foo:.*",
        "customErrorMsg": "I'm sorry, Dave. I can't do that."
      }
    }
  ]
}
```

## Registerkarte {#tab}

Auf einer Registerkarte können Sie andere Eingabefelder auf mehreren Registerkarten gruppieren, um die Layout-Organisation für Autoren zu verbessern.

A `tab` -Definition kann als Trennzeichen im Array von `fields`. Alles, was hinter einer `tab` wird auf dieser Registerkarte platziert, bis eine neue `tab` gefunden wird, wobei die folgenden Elemente auf der neuen Registerkarte platziert werden.

Wenn Sie Elemente haben möchten, die über allen Registerkarten angezeigt werden, müssen diese vor allen Registerkarten definiert werden.

### Beispiel {#sample-tab}

```json
{
  "id": "title",
  "fields": [
    {
      "component": "tab",
      "label": "Tab",
      "name": "tab1"
    },
    {
      "component": "text-input",
      "name": "tab-response",
      "value": "",
      "placeholder": "Tab? I can't give you a tab unless you order something.",
      "label": "Lou",
      "valueType": "string"
    },
    {
      "component": "tab",
      "label": "Pepsi Free",
      "name": "tab2"
    },
    {
      "component": "text-input",
      "name": "pepsi-free-response",
      "value": "",
      "placeholder": "You want a Pepsi, pal, you're gonna pay for it.",
      "label": "Mr. Carruthers",
      "valueType": "string"
    },
    {
      "component": "select",
      "name": "without-sugar",
      "value": "coffee",
      "label": "Something without sugar",
      "valueType": "string",
      "options": [
        { "name": "Coffee", "value": "coffee" },
        { "name": "Hot Coffee", "value": "hot-coffee" },
        { "name": "Hotter Coffee", "value": "hotter-coffee" }
      ]
    }
  ]
}
```
