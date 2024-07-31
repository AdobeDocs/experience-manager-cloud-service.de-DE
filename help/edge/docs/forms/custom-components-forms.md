---
title: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
description: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 77e90657-38db-4a49-9aac-3f3774b62624
role: Admin, Architect, Developer
source-git-commit: 4356fcc73a9c33a11365b1eb3f2ebee5c9de24f0
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 4%

---

# Erstellen benutzerdefinierter Komponenten

Mit AEM Forms Edge Delivery Services können Sie die [nativen HTML-Formularkomponenten](/help/edge/docs/forms/form-components.md) anpassen und benutzerfreundliche und interaktive Formulare erstellen. Sie können die Formularkomponenten mit vordefiniertem Markup ändern, wie im Abschnitt [Formatieren von Formularfeldern](/help/edge/docs/forms/style-theme-forms.md) beschrieben, indem Sie benutzerdefinierte CSS (Cascading Style Sheets) und benutzerdefinierten Code zum Dekorieren der Komponente verwenden, wodurch das Erscheinungsbild von Formularfeldern in einem adaptiven Forms-Block verbessert wird.

![Benutzerdefinierte Komponente](/help/edge/assets/custom-component-image.png)

In diesem Dokument werden die Schritte zum Erstellen benutzerdefinierter Komponenten durch Formatieren der nativen HTML-Formularkomponenten beschrieben, um das Benutzererlebnis zu verbessern und die visuelle Attraktivität des Formulars zu erhöhen.

Nehmen wir ein Beispiel für eine `range` -Komponente, die die `Estimated trip cost` in einem Formular anzeigt. Die Komponente `range` wird als gerade Linie angezeigt, ohne Werte wie den minimalen, maximalen oder ausgewählten Wert anzuzeigen.

![Native Bereichskomponente](/help/edge/assets/native-range-component.png)

Beginnen wir mit der Anpassung des Felds `range`, um die minimalen, maximalen und ausgewählten Werte in der Zeile anzuzeigen, indem wir einen Stil mit CSS hinzufügen und eine benutzerdefinierte Funktion hinzufügen, um eine Komponente zu dekorieren.

![Benutzerdefinierte Bereichskomponente](/help/edge/assets/custom-range-component.png)

Am Ende dieses Artikels lernen Sie, benutzerdefinierte Komponenten zu erstellen, indem Sie Stile in die CSS-Datei und die benutzerdefinierte Funktion einfügen.

## Voraussetzungen

Bevor Sie mit der Erstellung Ihrer benutzerdefinierten Komponente beginnen, sollten Sie Folgendes tun:

* Sie verfügen über grundlegende Kenntnisse zu [nativen HTML-Komponenten](/help/edge/docs/forms/form-components.md).
* Erfahren Sie, wie Sie mit den CSS-Selektoren ](/help/edge/docs/forms/style-theme-forms.md) Formularfelder basierend auf dem Feldtyp formatieren.[


## Erstellen einer benutzerdefinierten Komponente


![Schritte zum Erstellen einer benutzerdefinierten Komponente](/help/edge/docs/forms/assets/steps-to-create-custom-component.png)

Im Folgenden werden die einzelnen Schritte im Detail beschrieben.

Gehen Sie wie unten beschrieben vor, um die Komponente `range` anzupassen, indem Sie auf die Tabelle [Anfrage](/help/edge/docs/forms/assets/enquiry.xlsx) zugreifen.

### Fügen Sie eine benutzerdefinierte Funktion hinzu, um die Komponente zu dekorieren

Die benutzerdefinierte Funktion, die in `[../Form Block/components]` hinzugefügt wird, besteht aus:

* **Funktionsdeklaration**: Definieren Sie den Funktionsnamen und die zugehörigen Parameter.
* **Logische Implementierung**: Schreiben Sie die Logik, um das benutzerdefinierte Verhalten für die Komponente hinzuzufügen.
* **Funktionsexport**: Machen Sie die Funktion in `[Form Block]` barrierefrei.

Erstellen Sie eine JavaScript-Datei mit dem Namen `range.js` , um die Bereichskomponente zu formatieren. So fügen Sie eine benutzerdefinierte Funktion hinzu:

1. Wechseln Sie auf Google Drive oder SharePoint zu Ihrem AEM-Projektordner.
1. Navigieren Sie zu `[../Form Block/components]`.
1. Fügen Sie eine neue Datei mit dem Namen `range.js` hinzu.
1. Fügen Sie die folgende Codezeile hinzu:

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

### Den Dekorateur in den Formularblock einfügen

Der `[Form Block]` verwendet die semantische HTML, um Formularfelder einschließlich Eingabefeldern, Beschriftungen und Hilfetext mit Standardattributen für die Barrierefreiheit wiederzugeben. Um den `[Form Block]` benutzerdefinierten Dekorator für eine bestimmte Komponente zu verwenden, definieren Sie ihn in der Datei `mappings.js` . Die Datei `mappings.js` importiert eine Funktion, die das Modul zurückgibt, das für das Dekorieren einer bestimmten Komponente verantwortlich ist. Die Funktion übernimmt die Feldeigenschaften und gibt eine Dekoratorfunktion für das Formularfeld zurück.

In unserem Fall überprüft die Funktion die Eigenschaft `fieldType` des Felds und gibt den benutzerdefinierten Bereichsdekorator aus der in `[../Form Block/components]` vorhandenen Datei `range.js` zurück.

So injizieren Sie den Dekorator in den Formularblock:

1. Gehen Sie zu `[../Form Block/]` und öffnen Sie `mapping.js`.
1. Fügen Sie die folgende Codezeile hinzu:

   ```javascript
   export default async function componentDecorator(fd) {
   const { ':type': type = '', fieldType } = fd;
   .... existing code ....
   if (fieldType === 'range') {
   const module = await import('./components/range.js');
   return module.default;
   }
    return null; // null should be returned to use the original markup
   }
   ```

1. Speichern Sie die Änderungen.

### Stil für die Komponente in der CSS-Datei hinzufügen

Sie können das Erscheinungsbild von Formularfeldern anhand von Feldtypen und Feldnamen mithilfe von CSS-Selektoren ändern, um eine konsistente oder eindeutige Formatierung basierend auf Anforderungen zu ermöglichen. Um die Komponente zu formatieren, fügen Sie Code in die Datei `form.css` ein, um das Erscheinungsbild der Formularkomponente zu ändern.

Um den Stil für die Komponente `range` anzupassen, fügen Sie ein CSS-Codefragment ein, das ein Eingabeelement `range` und die zugehörigen Komponenten in einem Formular formatiert. Dabei wird von einem strukturierten HTML-Layout mit Klassen wie `.form` und `.range-wrapper` ausgegangen.

So fügen Sie einen Stil für eine Komponente in der CSS-Datei hinzu:
1. Gehen Sie zu `[../Form Block/]` und öffnen Sie `form.css`.
1. Fügen Sie die folgende Codezeile hinzu:

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

Stellen Sie die aktualisierten Dateien `range.js`, `mapping.css` und `form.css` in Ihrem GitHub-Projekt bereit und überprüfen Sie, ob der Build erfolgreich war.

### Vorschau des Formulars mit dem AEM Sidekick

Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) , um eine Vorschau Ihres Formulars mit der neu implementierten Funktion anzuzeigen, die die `range` -Komponente formatiert.

![Benutzerdefiniertes Komponentenformular](/help/edge/assets/custom-componet-form.png)

Der neue Stil für die Komponente `range` zeigt die minimalen, maximalen und ausgewählten Werte in der Zeile an, indem Stile mit CSS und eine benutzerdefinierte Funktion hinzugefügt werden, die einen Dekorator für die Komponente enthält.


## Siehe auch

{{see-more-forms-eds}}



