---
title: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
description: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: d71c5d6488935de4a02c8d3828f287542b979d0f
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 96%

---

# Erstellen benutzerdefinierter Komponenten

Mit Edge Delivery Services für AEM Forms können Sie die [nativen HTML-Formularkomponenten](/help/edge/docs/forms/form-components.md) anpassen und benutzerfreundliche, interaktive Formulare erstellen. So haben Sie die Möglichkeit, die Formularkomponenten mit vordefiniertem Markup zu ändern, wie unter [Formatieren von Formularfeldern](/help/edge/docs/forms/style-theme-forms.md) beschrieben, indem Sie benutzerdefinierte CSS (Cascading Style Sheets) und benutzerdefinierten Code zum Dekorieren der Komponente verwenden, wodurch das Erscheinungsbild von Formularfeldern in einem adaptiven Formularblock verbessert wird.

![Benutzerdefinierte Komponente](/help/edge/assets/custom-component-image.png)

In diesem Dokument werden die Schritte zum Erstellen benutzerdefinierter Komponenten durch Formatieren der nativen HTML-Formularkomponenten beschrieben, um das Anwendererlebnis zu verbessern und die visuelle Attraktivität des Formulars zu erhöhen.

Nehmen wir als Beispiel eine `range`-Komponente, die die `Estimated trip cost` in einem Formular anzeigt. Die `range`-Komponente wird als gerade Linie dargestellt, ohne Werte wie den minimalen, maximalen oder ausgewählten Wert anzuzeigen.

![Native Bereichskomponente](/help/edge/assets/native-range-component.png)

Passen Sie zunächst das Feld `range` an, um die minimalen, maximalen und ausgewählten Werte auf der Linie anzuzeigen. Fügen Sie dazu einen Stil mit CSS und eine benutzerdefinierte Funktion zum Dekorieren einer Komponente hinzu.

![Benutzerdefinierte Bereichskomponente](/help/edge/assets/custom-range-component.png)

Am Ende dieses Artikels erfahren Sie, wie Sie benutzerdefinierte Komponenten erstellen, indem Sie Stile in der CSS-Datei und benutzerdefinierten Funktion hinzufügen.

## Voraussetzungen

Bevor Sie mit der Erstellung Ihrer benutzerdefinierten Komponente beginnen, sollten Sie sicherstellen, dass Sie:

* grundlegende Kenntnisse zu [nativen HTML-Komponenten](/help/edge/docs/forms/form-components.md) besitzen
* wissen, wie Sie [mit der CSS-Auswahl Formularfelder basierend auf dem Feldtyp formatieren](/help/edge/docs/forms/style-theme-forms.md)


## Erstellen einer benutzerdefinierten Komponente


![Schritte zum Erstellen einer benutzerdefinierten Komponente](/help/edge/docs/forms/assets/steps-to-create-custom-component.png)

Im Folgenden werden die einzelnen Schritte im Detail beschrieben.

<!--Refer to the [enquiry spreadsheet](/help/edge/docs/forms/assets/enquiry.xlsx) to customize the `range` component, by following the steps as explained below.-->

### Hinzufügen einer benutzerdefinierten Funktion zum Dekorieren der Komponente

Die unter `[../Form Block/components]` hinzugefügte benutzerdefinierte Funktion besteht aus diesen Elementen:

* **Funktionsdeklaration**: Definieren Sie den Funktionsnamen und die zugehörigen Parameter.
* **Logische Implementierung**: Schreiben Sie die Logik, um das benutzerdefinierte Verhalten für die Komponente hinzuzufügen.
* **Funktionsexport**: Machen Sie die Funktion in `[Form Block]` verfügbar.

So fügen Sie eine benutzerdefinierte Funktion hinzu:

1. Navigieren Sie zu `[../Form Block/components]`.
1. Suchen Sie eine Datei mit dem Namen `range.js`. Wenn nicht vorhanden, erstellen Sie sie.
1. Fügen Sie die folgende Code-Zeile hinzu:

   ```javascript
   function updateBubble(input, element) {
   const step = input.step || 1;
   const max = input.max || 0;
   const min = input.min || 1;
   const value = input.value || 1;
   const current = Math.ceil((value - min) / step);
   const total = Math.ceil((max - min) / step);
   const bubble = element.querySelector('.range-bubble');
   // during initial render the width is 0. Hence using a default here.
   const bubbleWidth = bubble.getBoundingClientRect().width || 31;
   const left = `${(current / total) * 100}% - ${(current / total) * bubbleWidth}px`;
   bubble.innerText = `${value}`;
   const steps = {
   '--total-steps': Math.ceil((max - min) /    step),
   '--current-steps': Math.ceil((value - min) / step),
   };
   const style = Object.entries(steps).map(([varName, varValue]) => `${varName}:${varValue}`).join(';');
   bubble.style.left = `calc(${left})`;
   element.setAttribute('style', style);
   }
   // eslint-disable-next-line no-unused-vars
   export default function decorateRange(fieldDiv, field) {
   loadCSS('/blocks/form/components/range/range.css');
   const input = fieldDiv.querySelector('input');
   // modify the type in case it is not range.
   input.type = 'range';
   input.min = input.min || 1;
   // create a wrapper div to provide the min/max and current value
   const div = document.createElement('div');
   div.className = 'range-widget-wrapper';
   input.after(div);
   const hover = document.createElement('span');
   hover.className = 'range-bubble';
   const rangeMinEl = document.createElement('span');
   rangeMinEl.className = 'range-min';
   const rangeMaxEl = document.createElement('span');
   rangeMaxEl.className = 'range-max';
   rangeMinEl.innerText = `${input.min || 1}`;
   rangeMaxEl.innerText = `${input.max}`;
   div.appendChild(hover);
   // move the input element within the wrapper div
   div.appendChild(input);
   div.appendChild(rangeMinEl);
   div.appendChild(rangeMaxEl);
   input.addEventListener('input', (e) => {
       updateBubble(e.target, div);
   });
   updateBubble(input, div);
   // as a best practice add a custom css class to apply custom styling
   fieldDiv.classList.add('decorated');
   return fieldDiv;    
   }
   ```

1. Speichern Sie die Änderungen.

### Einfügen des Decorators in den Formularblock

Der `[Form Block]` verwendet semantisches HTML, um Formularfelder einschließlich Eingabefeldern, Beschriftungen und Hilfetext, mit Standardattributen zwecks Barrierefreiheit zu rendern. Damit der `[Form Block]` den benutzerdefinierten Decorator für eine bestimmte Komponente verwendet, müssen Sie ihn in der Datei `mappings.js` definieren. Die Datei `mappings.js` importiert eine Funktion, die das Modul zurückgibt, das für das Dekorieren einer bestimmten Komponente verantwortlich ist. Die Funktion übernimmt die Feldeigenschaften und gibt eine Decorator-Funktion für das Formularfeld zurück.

Im vorliegenden Fall überprüft die Funktion die Eigenschaft `fieldType` des Felds und gibt den benutzerdefinierten Bereichs-Decorator aus der unter `[../Form Block/components]` vorhandenen Datei `range.js` zurück.

So fügen Sie den Decorator in den Formularblock ein:

1. Gehen Sie zu `[../Form Block/]` und öffnen Sie `mapping.js`.
1. Fügen Sie die folgende Code-Zeile hinzu:

   ```javascript
   export default async function componentDecorator(fd) {
   const { ':type': type = '', fieldType } = fd;
   .... existing code ....
   if (fieldType === 'range') {
   const module = await import('./components/range.js');
   return module.default(element,fd);
   }
    return null; // null should be returned to use the original markup
   }
   ```

1. Speichern Sie die Änderungen.

### Hinzufügen eines Stils für die Komponente in der CSS-Datei

Sie können das Erscheinungsbild von Formularfeldern mithilfe der CSS-Auswahl gemäß dem Feldtyp und den Feldnamen ändern, was eine konsistente oder eindeutige Formatierung je nach den Anforderungen ermöglicht. Zum Formatieren der Komponente fügen Sie Code in der Datei `form.css` hinzu, um das Look-and-Feel der Formularkomponente zu ändern.

Um den Stil für die `range`-Komponente anzupassen, fügen Sie ein CSS-Code-Snippet ein, das ein `range`-Input-Element und die zugehörigen Komponenten in einem Formular formatiert. Dabei wird von einem strukturierten HTML-Layout mit Klassen wie `.form` und `.range-wrapper` ausgegangen.

So fügen Sie einen Stil für eine Komponente in der CSS-Datei hinzu:
1. Navigieren Sie zu `[../Form Block/]` und öffnen Sie `form.css`.
1. Fügen Sie die folgende Code-Zeile hinzu:

   ```javascript
       /** styling for range */
   main .form .range-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, var(--button-primary-color) calc(100% * var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% * var(--current-steps)/var(--total-steps)));
   }
   
   main .form .range-wrapper.decorated input[type="range"]:focus {
   outline: none;
   }
   
   .range-wrapper.decorated input[type="range"]::-webkit-slider-thumb {
   appearance: none;
   width: 25px;
   height: 25px;
   border-radius: 50%;
   background: #fff;
   border: 3px solid var(--button-primary-color);
   cursor: pointer;
   outline: 3px solid #fff;
   }
   
   .range-wrapper.decorated input[type="range"]:focus::-webkit-slider-thumb {
   border-color: var(--button-primary-color);
   }
   
   .range-wrapper.decorated .range-bubble {
   color: #17252e;
   font-size: 20px;
   line-height: 28px;
   position: relative;
   display: inline-block;
   padding-bottom: 12px;
   }
   
   .range-wrapper.decorated .range-min,
   .range-wrapper.decorated .range-max {
   font-size: 14px;
   line-height: 22px;
   color: #494f50;
   margin-top: 16px;
   display: inline-block;
   }
   
   .range-wrapper.decorated .range-max {
   float: right;
   }
   ```
1. Speichern Sie die Änderungen.

### Bereitstellen der Dateien und Erstellen des Projekts

Stellen Sie die aktualisierten Dateien `range.js`, `mapping.js` und `form.css` in Ihrem GitHub-Projekt bereit und überprüfen Sie, ob der Build erfolgreich war.

### Anzeigen einer Vorschau des Formulars mit dem AEM Sidekick

Zeigen Sie eine Vorschau des Formulars mit der neu implementierten Funktion an, die die `range` formatiert.

![Benutzerdefiniertes Komponentenformular](/help/edge/assets/custom-componet-form.png)

Der neue Stil für die Komponente `range` zeigt den minimalen, maximalen und ausgewählten Wert in der Zeile an, indem Stile mit CSS und eine benutzerdefinierte Funktion hinzugefügt werden, die einen Dekorator für die Komponente enthält.
<!--
Now, you can extend the created custom component for WYSIWYG based authoring.

## Enable Component for WYSIWYG authoring

To enable component for WYSIWYG authoring:

1. Navigate to  `[../Form Block/components]`.
2. Locate a file named `_range.json`. if not present, create it.
3. Add the following code in the  `_range.json` file:

    ```javascript
    {
    "definitions": [
        {
         "title": "Range",
         "id": "range",
        "plugins": {
          "xwalk": {
           "page": {
               "resourceType": "core/fd/components/form/numberinput/v1/numberinput",
              "template": {
              "jcr:title": "Range",
              "fieldType": "number-input",
              "fd:viewType": "range",
              "enabled": true,
              "visible": true
             }
            }
            }
        }
        }
    ],
    "models": [
     {
          "id": "range",
        "fields": [
          {
              "component": "container",
             "name": "basic",
             "label": "Basic",
             "collapsible": false,
             "...": "../../../../models/form-common/_basic-input-fields.json"
             {
             "component": "number",
             "name": "stepValue",
             "label": "Step Value",
              "valueType": "number"
        }
         },
         {
              "...": "../../../../models/form-common/_help-container.json"
            },
            {
          "component": "container",
          "name": "validation",
          "label": "Validation",
          "collapsible": true,
          "...": "../../../../models/form-common/_number-validation-fields.json"
            }
        ]
        }
    ]
    }
    ```

    The above code snippet in the `_range.json` file includes the component definition, component model and custom properties for your custom component.


    ![component definition and model](/help/edge/docs/forms/universal-editor/assets/custom-component-json-file.png)

4. Navigate to the `/blocks/form/_form.json` file and add the `fd:viewType` value from the `definitions[]` to the components array of the object with `id="form"`.

    ```javascript

        "filters": [
        {
         "id": "form",
        "components": [
        "captcha",
        "checkbox",
        "checkbox-group",
        "date-input",
        "drop-down",
        "email",
        "file-input",
        "form-accordion",
        "form-button",
        "form-fragment",
        "form-image",
        "form-modal",
        "form-reset-button",
        "form-submit-button",
        "number-input",
        "panel",
        "plain-text",
        "radio-group",
        "rating",
        "telephone-input",
        "text-input",
        "tnc",
        "wizard",
        "range"
      ]
        }
    ]
      ```

    The above code snippet defines the section in which the custom component can be used in Universal Editor.
    
    ![component filter](/help/edge/docs/forms/universal-editor/assets/custom-component-form-file.png)

5. Navigate to the `/blocks/form/mappings.js` file and add the `fd:viewType` value from the `definitions[]` array to the `customComponents[]` array.

    ```javascript
    let customComponents = ["range"];
    const OOTBComponentDecorators = ['file-input',
                                 'wizard', 
                                 'modal', 'tnc',
                                'toggleable-link',
                                'rating',
                                'datetime',
                                'list',
                                'location',
                                'accordion'];
    ```

The above code snippet enables the form block to recognize the custom component and load its properties defined in the component model during form authoring in Universal Editor.

![component mapping](/help/edge/docs/forms/universal-editor/assets/custom-component-mapping-file.png)

Now, you can see your custom component in the WYSIWYG based authoring:

![Range component](/help/edge/docs/forms/universal-editor/assets/custom-component-range-doc-based.png)

>[!NOTE]
>
> For detailed steps on creating a custom component for the Universal Editor, refer to the [Create Custom Component in WYSIWYG based authoring](/help/edge/docs/forms/universal-editor/create-custom-component) article. -->

## Siehe auch

{{see-more-forms-eds}}




