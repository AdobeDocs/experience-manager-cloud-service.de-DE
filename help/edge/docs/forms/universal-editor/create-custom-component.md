---
title: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
description: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 0c6f024594e1b1fd98174914d2c0714dffecb241
workflow-type: tm+mt
source-wordcount: '1773'
ht-degree: 5%

---

# Erstellen benutzerdefinierter Komponenten beim WYSIWYG-Authoring

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> mit dem Namen Ihrer GitHub-Organisation und dem Repository-Namen. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Organisationsname adobe und der Repository-Name abc.</span>


Edge Delivery Services Forms bietet eine Anpassung, die es Frontend-Entwicklerinnen und -Entwicklern ermöglicht, maßgeschneiderte Formularkomponenten zu erstellen. Diese benutzerdefinierten Komponenten lassen sich nahtlos in das Authoring-Erlebnis von WYSIWYG integrieren und ermöglichen es Formularautoren, sie einfach im Formulareditor hinzuzufügen, zu konfigurieren und zu verwalten. Mit benutzerdefinierten Komponenten können Autoren die Funktionalität verbessern und gleichzeitig einen reibungslosen und intuitiven Authoring-Prozess sicherstellen.

In diesem Dokument werden die Schritte zum Erstellen benutzerdefinierter Komponenten durch Formatieren der nativen HTML-Formularkomponenten beschrieben, um das Anwendererlebnis zu verbessern und die visuelle Attraktivität des Formulars zu erhöhen.

## Voraussetzungen

Bevor Sie mit der Erstellung Ihrer benutzerdefinierten Komponente beginnen, sollten Sie sicherstellen, dass Sie:

* grundlegende Kenntnisse zu [nativen HTML-Komponenten](/help/edge/docs/forms/form-components.md) besitzen
* wissen, wie Sie [mit der CSS-Auswahl Formularfelder basierend auf dem Feldtyp formatieren](/help/edge/docs/forms/style-theme-forms.md)

## Erstellen einer benutzerdefinierten Komponente

Das Hinzufügen einer benutzerdefinierten Komponente im universellen Editor bedeutet, dass eine neue Komponente für Formularautoren verfügbar gemacht werden kann, die sie beim Entwerfen von Formularen verwenden können. Dazu gehört die Registrierung der Komponente, die Definition ihrer Eigenschaften und die Konfiguration, wo sie verwendet werden kann. Die Schritte zum Erstellen benutzerdefinierter Komponenten sind:

[1. Hinzufügen einer Struktur für eine neue benutzerdefinierte Komponente](#1-adding-structure-for-new-custom-component)
[2. Definieren der Eigenschaften der benutzerdefinierten Komponente für das Authoring](#2-defining-the-properties-of-your-custom-component-for-authoring)
[3.  So machen Sie Ihre benutzerdefinierte Komponente in der Komponentenliste von WYSIWYG sichtbar](#3-making-your-custom-component-visible-in-the-wysiwyg-component-list)
[4. Registrieren der benutzerdefinierten Komponente](#4-registering-your-custom-component)
[5. Hinzufügen des Laufzeitverhaltens für Ihre benutzerdefinierte Komponente](#5-adding-the-runtime-behaviour-for-your-custom-component)

Nehmen wir als Beispiel das Erstellen einer neuen benutzerdefinierten Komponente mit dem Namen **Bereich**. Die Bereichskomponente wird als gerade Linie angezeigt und zeigt Werte wie den minimalen, maximalen oder ausgewählten Wert an.

![Range-Komponentenstil](/help/edge/docs/forms/universal-editor/assets/custom-component-range-style.png)

Am Ende dieses Artikels erfahren Sie, wie Sie benutzerdefinierte Komponenten von Grund auf neu erstellen.

### 1. Hinzufügen einer Struktur für eine neue benutzerdefinierte Komponente

Bevor eine benutzerdefinierte Komponente verwendet werden kann, muss sie registriert werden, damit der universelle Editor sie als verfügbare Option erkennt. Dies wird durch eine Komponentendefinition erreicht, die eine eindeutige Kennung, Standardeigenschaften und die Struktur der Komponente enthält. Führen Sie die folgenden Schritte aus, um die benutzerdefinierte Komponente für das Formular-Authoring verfügbar zu machen:

1. **Neuen Ordner und Dateien hinzufügen**
Fügen Sie neue Ordner und Dateien für Ihre neue benutzerdefinierte Komponente in Ihrem AEM-Projekt hinzu.
   1. Öffnen Sie Ihr AEM-Projekt und navigieren Sie zu `../blocks/form/components/`.
   1. Fügen Sie `../blocks/form/components/<component_name>` einen neuen Ordner für Ihre benutzerdefinierte Komponente hinzu. In diesem Beispiel erstellen wir einen Ordner mit dem Namen `range`.
   1. Navigieren Sie zum neu erstellten Ordner unter `../blocks/form/components/<component_name>`. Navigieren Sie beispielsweise zu `../blocks/form/components/range` und fügen Sie die folgenden Dateien hinzu:
      * `/blocks/form/components/range/_range.json`: Enthält die Definition der benutzerdefinierten Komponente.
      * `../blocks/form/components/range/range.css`: Definiert den Stil für die benutzerdefinierte Komponente.
      * `../blocks/form/components/range/range.js`: Passt die benutzerdefinierte Komponente zur Laufzeit an.

        ![Hinzufügen der benutzerdefinierten Komponente zum Authoring](/help/edge/docs/forms/universal-editor/assets/adding-custom-component.png)

        >[!NOTE]
        >
        > Stellen Sie sicher, dass die JSON-Datei einen Unterstrich (_) als Präfix im Dateinamen enthält.

1. Navigieren Sie zur `/blocks/form/components/range/_range.json` und fügen Sie die Komponentendefinition für die benutzerdefinierte Komponente hinzu.

1. **Komponentendefinition hinzufügen**

   Um die Definition hinzuzufügen, müssen die folgenden Felder in der `_range.json`-Datei hinzugefügt werden:

   * **title**: Der Titel der Komponente, die im universellen Editor angezeigt wird.
   * **id**: Eine eindeutige Kennung der Komponente.
   * **fieldType**: Forms unterstützt verschiedene **fieldType** zur Erfassung bestimmter Typen von Benutzereingaben. Den [unterstützten fieldType finden Sie im Abschnitt Extra Byte](#supported-fieldtypes).
   * **resourceType**: Jeder benutzerdefinierten Komponente ist ein Ressourcentyp auf Grundlage ihres fieldType zugeordnet. Den [unterstützten resourceType finden Sie im Abschnitt Extra Byte](#supported-resourcetype).
   * **jcr:title**: Es ähnelt einem Titel, wird jedoch in der Komponentenstruktur gespeichert.
   * **fd:viewType**: Stellt den Namen der benutzerdefinierten Komponente dar. Dies ist die eindeutige Kennung der Komponente. Es ist erforderlich, eine benutzerdefinierte Ansicht für die Komponente zu erstellen.

Nach dem Hinzufügen der Komponentendefinition lautet die `_range.json` wie folgt:

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
  ]
}
```

>[!NOTE]
>
> Beim Hinzufügen von Blöcken zum universellen Editor verwenden alle formularbezogenen Komponenten denselben Ansatz wie Sites. Weitere Informationen finden Sie im [Erstellen von Blöcken, die für die Verwendung mit dem universellen Editor instrumentiert ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/create-block)).

### 2. Definieren der Eigenschaften der benutzerdefinierten Komponente für das Authoring

Die benutzerdefinierte Komponente enthält ein Komponentenmodell, das angibt, welche Eigenschaften vom Formularautor konfiguriert werden können. Diese Eigenschaften werden im Dialogfeld **Eigenschaften** des universellen Editors angezeigt und ermöglichen es Autoren, Einstellungen wie Beschriftungen, Validierungsregeln, Stile und andere Attribute anzupassen. So definieren Sie Eigenschaften:

1. Navigieren Sie zur `/blocks/form/components/range/_range.json` und fügen Sie das Komponentenmodell für die benutzerdefinierte Komponente hinzu.

1. **Komponentenmodell hinzufügen**

   Um das Komponentenmodell für Ihre benutzerdefinierte Komponente zu definieren, müssen Sie die entsprechenden Felder zur `_range.json`-Datei hinzufügen.

   1. **Neues Modell erstellen**

      * Fügen Sie im Modellarray ein neues -Objekt hinzu und legen Sie die `id` des Komponentenmodells so fest, dass sie mit der zuvor in der Komponentendefinition konfigurierten `fd:viewType` übereinstimmt.
      * Fügen Sie ein Feld-Array in dieses Objekt ein.

   2. **Felder für das Dialogfeld „Eigenschaft definieren“**

      * Jedes Objekt im Feld-Array sollte eine Komponente vom Typ Container sein, damit es als Registerkarte im Dialogfeld **Eigenschaft** angezeigt wird.
      * Einige Felder können auf wiederverwendbare Eigenschaften verweisen, die in `models/form-common` verfügbar sind.

   3. **Verwenden eines vorhandenen Komponentenmodells als Referenz**

      * Sie können den Inhalt eines vorhandenen Komponentenmodells kopieren, das Ihrem ausgewählten `fieldType` entspricht, und ihn nach Bedarf ändern. Beispielsweise wird die `number-input`-Komponente erweitert, um eine Komponente **Bereich** zu erstellen, sodass wir das Array der Modelle aus `models/form-components/_number-input.json` als Referenz verwenden können.

   Nach dem Hinzufügen des Komponentenmodells lautet die `_range.json` wie folgt:

   ```javascript
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
   ```

   >[!NOTE]
   >
   > Um dem Dialogfeld **Eigenschaft** einer benutzerdefinierten Komponente ein neues Feld hinzuzufügen, halten Sie sich an das [definierte Schema](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/field-types#loading-model).

   Sie können einer benutzerdefinierten Komponente auch [benutzerdefinierte Eigenschaften hinzufügen](#adding-custom-properties-for-your-custom-component), um ihre Funktionalität zu erweitern.

#### Hinzufügen benutzerdefinierter Eigenschaften für die benutzerdefinierte Komponente

Benutzerdefinierte Eigenschaften ermöglichen es Ihnen, bestimmte Verhaltensweisen auf der Grundlage von Werten zu definieren, die im Dialogfeld „Eigenschaft“ einer Komponente festgelegt wurden. Dies hilft, die Funktionalität der Komponente und die Anpassungsoptionen zu erweitern.

In diesem Beispiel fügen wir den Schrittwert als benutzerdefinierte Eigenschaft zur Bereichskomponente hinzu.

![Schrittwert für benutzerdefinierte Eigenschaft](/help/edge/docs/forms/universal-editor/assets/customcomponent-stepvalue.png)

Um die benutzerdefinierte Eigenschaft Schrittwert hinzuzufügen, hängen Sie das Komponentenmodell mit den folgenden Codezeilen in der Datei ` _<component>.json` an:

```javascript
      {
      "component": "number",
      "name": "stepValue",
      "label": "Step Value",
      "valueType": "number"
      }
```

Das JSON-Snippet definiert eine benutzerdefinierte Eigenschaft mit der Bezeichnung **Schrittwert** für eine Komponente **Bereich**. Nachstehend finden Sie eine Aufschlüsselung der einzelnen Felder:

* **component**: Gibt den Typ des Eingabefelds an, das im Dialogfeld „Eigenschaft“ verwendet wird. In diesem Fall gibt `number` an, dass das Feld numerische Werte akzeptiert.
* **name**: Die Kennung für die Eigenschaft, die verwendet wird, um in der Komponentenlogik darauf zu verweisen. Hier stellt der `stepValue` die Schrittwerteinstellung für den Bereich dar.
* **label**: Der Anzeigename der Eigenschaft, wie er im Dialogfeld „Eigenschaft“ angezeigt wird.
* **valueType**: Definiert den für die Eigenschaft erwarteten Datentyp. Der `number` stellt sicher, dass nur numerische Eingaben zulässig sind.

Sie können jetzt `stepValue` als benutzerdefinierte Eigenschaft in den JSON-Eigenschaften von `range.js` verwenden und dynamisches Verhalten basierend auf seinem Wert zur Laufzeit implementieren.

Daher lautet die endgültige `_range.json` nach dem Hinzufügen der Komponentendefinition, des Komponentenmodells und der benutzerdefinierten Eigenschaften wie folgt:

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

![Komponentendefinition und -modell](/help/edge/docs/forms/universal-editor/assets/custom-component-json-file.png)


### 3. Einblenden der benutzerdefinierten Komponente in der Komponentenliste von WYSIWYG

Ein Filter definiert, in welchem Abschnitt die benutzerdefinierte Komponente im universellen Editor verwendet werden kann. Dadurch wird sichergestellt, dass die Komponente nur in geeigneten Abschnitten verwendet werden kann, wobei Struktur und Benutzerfreundlichkeit erhalten bleiben.

So stellen Sie sicher, dass die benutzerdefinierte Komponente beim Erstellen von Formularen in WYSIWYG in der Liste der verfügbaren Komponenten angezeigt wird:

1. Navigieren Sie zur `/blocks/form/_form.json`.
1. Suchen Sie das Komponenten-Array innerhalb des -Objekts, das `id="form"` hat.
1. Fügen Sie den `fd:viewType` Wert aus dem `definitions[]` zum Komponenten-Array des -Objekts mit `id="form"` hinzu.

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

![Komponentenfilter](/help/edge/docs/forms/universal-editor/assets/custom-component-form-file.png)

### 4. Registrieren der benutzerdefinierten Komponente

Damit der Formularblock die benutzerdefinierte Komponente erkennen und ihre beim Formular-Authoring im Komponentenmodell definierten Eigenschaften laden kann, fügen Sie den `fd:viewType` aus der Komponentendefinition zur `mappings.js` hinzu.
So registrieren Sie eine Komponente:
1. Navigieren Sie zur `/blocks/form/mappings.js`.
1. Suchen Sie das `customComponents[]` Array.
1. Fügen Sie den `fd:viewType` Wert aus dem `definitions[]` Array zum `customComponents[]` Array hinzu.

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

![Komponentenzuordnung](/help/edge/docs/forms/universal-editor/assets/custom-component-mapping-file.png)

Nach Abschluss der oben genannten Schritte wird die benutzerdefinierte Komponente im universellen Editor in der Komponentenliste des Formulars angezeigt. Anschließend können Sie es per Drag-and-Drop in den Formularabschnitt ziehen.

![Bereichskomponente](/help/edge/docs/forms/universal-editor/assets/custom-component-range.png)

Der folgende Screenshot zeigt die Eigenschaften der `range` Komponente, die dem Komponentenmodell hinzugefügt wurde und die Eigenschaften angibt, die der Formularautor konfigurieren kann:

![Eigenschaften der Bereichskomponente](/help/edge/docs/forms/universal-editor/assets/range-properties.png)

Sie können jetzt das Laufzeitverhalten Ihrer benutzerdefinierten Komponente definieren, indem Sie Stile und Funktionen hinzufügen.

### 5. Hinzufügen des Laufzeitverhaltens für die benutzerdefinierte Komponente

Sie können benutzerdefinierte Komponenten mithilfe von vordefiniertem Markup ändern, wie unter [Formatieren von Formularfeldern“ ](/help/edge/docs/forms/style-theme-forms.md). Dies kann mit benutzerdefiniertem CSS (Cascading Style Sheets) und benutzerdefiniertem Code erreicht werden, um das Erscheinungsbild der Komponente zu verbessern. So fügen Sie das Laufzeitverhalten für Ihre Komponente hinzu:

1. Um die Formatierung hinzuzufügen, navigieren Sie zur `/blocks/form/components/range/range.css` und fügen Sie die folgende Codezeile hinzu:

   ```javascript
   /** Styling for range */
   main .form .range-widget-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, #ADD8E6 calc(100% * var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% * var(--current-steps)/var(--total-steps)));
   }
   
   main .form .range-widget-wrapper.decorated input[type="range"]:focus {
   outline: none;
   }
   
   .range-widget-wrapper.decorated input[type="range"]::-webkit-slider-thumb {
   appearance: none;
   width: 25px;
   height: 25px;
   border-radius: 50%;
   background: #00008B; /* Dark Blue */
   border: 3px solid #00008B; /* Dark Blue */
   cursor: pointer;
   outline: 3px solid #fff;
   }
   
   .range-widget-wrapper.decorated input[type="range"]:focus::-webkit-slider-thumb {
   border-color: #00008B; /* Dark Blue */
   }
   
   .range-widget-wrapper.decorated .range-bubble {
   color: #00008B; /* Dark Blue */
   font-size: 20px;
   line-height: 28px;
   position: relative;
   display: inline-block;
   padding-bottom: 12px;
   font-weight: bold;
   }
   
   .range-widget-wrapper.decorated .range-min,
   .range-widget-wrapper.decorated .range-max {
   font-size: 14px;
   line-height: 22px;
   color: #494f50;
   margin-top: 16px;
   display: inline-block;
   }
   
   .range-widget-wrapper.decorated .range-max {
   float: right;
   }
   ```
   Mit dem Code können Sie den Stil und das visuelle Erscheinungsbild der benutzerdefinierten Komponente definieren.

1. Um die Funktion hinzuzufügen, navigieren Sie zur `/blocks/form/components/range/range.js`-Datei und fügen Sie die folgende Codezeile hinzu:

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
       '--total-steps': Math.ceil((max - min) / step),
       '--current-steps': Math.ceil((value - min) / step),
   };
   const style = Object.entries(steps).map(([varName, varValue]) => `${varName}:${varValue}`).join(';');
   bubble.style.left = `calc(${left})`;
   element.setAttribute('style', style);
   }
   
   export default async function decorate(fieldDiv, fieldJson) {
   console.log('RANGE DIV: ', fieldDiv);
   console.log('RANGE JSON: fieldJson', fieldJson);
    const input = fieldDiv.querySelector('input');
   // modify the type in case it is not range.
   input.type = 'range';
   input.min = input.min || 10;
   input.max = input.max || 1000;
   // create a wrapper div to provide the min/max and current value
   const div = document.createElement('div');
   div.className = 'range-widget-wrapper decorated';
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
   return fieldDiv;
   }
   ```

   Sie steuert, wie die benutzerdefinierte Komponente mit Benutzereingaben interagiert, Daten verarbeitet und im universellen Editor in den Formularblock integriert wird.

   Nach der Integration von benutzerdefinierten Stilen und Funktionen werden Erscheinungsbild und Verhalten der Bereichskomponente verbessert. Das aktualisierte Design spiegelt die angewendeten Stile wider, während die zusätzliche Funktionalität ein dynamischeres und interaktiveres Benutzererlebnis gewährleistet.
Der folgende Screenshot zeigt die aktualisierte Bereichskomponente.

![Range-Komponentenstil](/help/edge/docs/forms/universal-editor/assets/custom-component-range-1.png)

## Häufig gestellte Fragen

* **Wenn ich Formatierungen sowohl in „component.css“ als auch in „forms.css“ hinzufüge, welche Priorität hat?**
Wenn Stile sowohl in `component.css` als auch in **forms.css** definiert sind, hat `component.css` Priorität. Dies liegt daran, dass Stile auf Komponentenebene spezifischer sind und globale Stile von `forms.css` überschreiben.

* **Meine benutzerdefinierte Komponente ist nicht in der Liste der verfügbaren Komponenten im universellen Editor sichtbar. Wie kann ich das beheben?**
Wenn Ihre benutzerdefinierte Komponente nicht angezeigt wird, überprüfen Sie die folgenden Dateien, um sicherzustellen, dass die Komponente korrekt registriert ist:
   * **component-definition.json**: Überprüfen Sie, ob die Komponente ordnungsgemäß definiert ist.
   * **component-filters.json**: Stellen Sie sicher, dass die Komponente in den entsprechenden Abschnitten zulässig ist.
   * **component-models.json**: Überprüfen Sie, ob das Komponentenmodell korrekt konfiguriert ist.

## Best Practices

* Es wird empfohlen, [eine lokale AEM-Entwicklungsumgebung einzurichten](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#set-up-local-aem-development-environment) um benutzerdefinierte Stile und Komponenten lokal zu entwickeln.


## zusätzliches Byte

### Unterstützter Ressourcentyp

| Feldtyp | Ressourcentyp |
|--------------|------------------------------------------------------------------|
| text-input | core/fd/components/form/textinput/v1/textinput |
| Zahleneingabe | core/fd/components/form/numberInput/v1/numberInput |
| date-input | core/fd/components/form/datepicker/v1/datepicker |
| panel | core/fd/components/form/panelContainer/v1/panelContainer |
| checkbox | core/fd/components/form/checkbox/v1/checkbox |
| Dropdown | core/fd/components/form/dropdown/v1/dropdown |
| Optionsfeldgruppe | core/fd/components/form/radiobutton/v1/radiobutton |
| Nur-Text | core/fd/components/form/text/v1/text |
| file-input | core/fd/components/form/fileinput/v2/fileinput |
| email | core/fd/components/form/emailinput/v1/emailinput |
| image | core/fd/components/form/image/v1/image |
| Schaltfläche | core/fd/components/form/button/v1/button |

### Unterstützte Feldtypen

Folgende Feldtypen werden für Formulare unterstützt:
* text-input
* Zahleneingabe
* date-input
* panel
* checkbox
* Dropdown
* Optionsfeldgruppe
* Nur-Text
* file-input
* email
* image
* Schaltfläche

## Siehe auch

{{universal-editor-see-also}}
