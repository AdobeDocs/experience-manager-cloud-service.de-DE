---
title: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
description: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: ht
source-wordcount: '1802'
ht-degree: 100%

---

# Erstellen benutzerdefinierter Komponenten beim WYSIWYG-Authoring

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, die über unseren <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features">Vorabveröffentlichungskanal</a> verfügbar ist. </span>


Edge Delivery Services Forms bietet eine Anpassung, die es Frontend-Entwicklerinnen und -Entwicklern ermöglicht, maßgeschneiderte Formularkomponenten zu erstellen. Diese benutzerdefinierten Komponenten lassen sich nahtlos in das WYSIWYG-Authoring-Erlebnis integrieren und können im Formulareditor einfach hinzugefügt, konfiguriert und verwaltet werden. Mit benutzerdefinierten Komponenten können Sie die Funktionalität verbessern und gleichzeitig einen reibungslosen und intuitiven Authoring-Prozess sicherstellen.

In diesem Dokument werden die Schritte zum Erstellen benutzerdefinierter Komponenten durch Formatieren der nativen HTML-Formularkomponenten beschrieben, um das Anwendererlebnis zu verbessern und den visuellen Reiz des Formulars zu erhöhen.

## Voraussetzungen

Bevor Sie mit der Erstellung Ihrer benutzerdefinierten Komponente beginnen, sollten Sie sicherstellen, dass Sie:

* grundlegende Kenntnisse zu [nativen HTML-Komponenten](/help/edge/docs/forms/form-components.md) besitzen
* wissen, wie Sie [mit der CSS-Auswahl Formularfelder basierend auf dem Feldtyp formatieren](/help/edge/docs/forms/style-theme-forms.md)

## Erstellen einer benutzerdefinierten Komponente

Das Hinzufügen einer benutzerdefinierten Komponente im universellen Editor bedeutet, dass eine neue Komponente verfügbar gemacht wird, die beim Entwerfen von Formularen verwendet werden kann. Dazu gehört die Registrierung der Komponente, die Definition ihrer Eigenschaften und die Konfiguration, wo sie verwendet werden kann. Die Schritte zum Erstellen benutzerdefinierter Komponenten sind die folgenden:

[1. Hinzufügen einer Struktur für eine neue benutzerdefinierte Komponente](#1-adding-structure-for-new-custom-component)
[2. Definieren der Eigenschaften der benutzerdefinierten Komponente für das Authoring](#2-defining-the-properties-of-your-custom-component-for-authoring)
[3.  Sichtbarmachen der benutzerdefinierten Komponente in der WYSIWYG-Komponentenliste](#3-making-your-custom-component-visible-in-the-wysiwyg-component-list)
[4. Registrieren der benutzerdefinierten Komponente](#4-registering-your-custom-component)
[5. Hinzufügen des Laufzeitverhaltens der benutzerdefinierten Komponente](#5-adding-the-runtime-behaviour-for-your-custom-component)

Nehmen wir als Beispiel das Erstellen einer neuen benutzerdefinierten Komponente mit dem Namen **range**. Die Komponente „range“ wird als gerade Linie dargestellt und zeigt Werte wie den minimalen, maximalen oder ausgewählten Wert an.

![Eine visuelle Darstellung einer Bereichskomponente mit einem Schieberegler mit Mindest- und Höchstwerten und einem Indikator für ausgewählte Werte](/help/edge/docs/forms/universal-editor/assets/custom-component-range-style.png)

Am Ende dieses Artikels erfahren Sie, wie Sie benutzerdefinierte Komponenten von Grund auf neu erstellen.

### &#x200B;1. Hinzufügen einer Struktur für eine neue benutzerdefinierte Komponente

Bevor eine benutzerdefinierte Komponente verwendet werden kann, muss sie registriert werden, damit der universelle Editor sie als verfügbare Option erkennt. Dies wird durch eine Komponentendefinition erreicht, die eine eindeutige Kennung, Standardeigenschaften und die Struktur der Komponente enthält. Führen Sie die folgenden Schritte aus, um die benutzerdefinierte Komponente für die Formularerstellung verfügbar zu machen:

1. **Hinzufügen eines neuen Ordners und neuer Dateien**
Fügen Sie neue Ordner und Dateien für Ihre neue benutzerdefinierte Komponente in Ihrem AEM-Projekt hinzu.
   1. Öffnen Sie Ihr AEM-Projekt und navigieren Sie zu `../blocks/form/components/`.
   1. Fügen Sie unter `../blocks/form/components/<component_name>` einen neuen Ordner für Ihre benutzerdefinierte Komponente hinzu. In diesem Beispiel erstellen wir einen Ordner mit dem Namen `range`.
   1. Navigieren Sie zum neu erstellten Ordner unter `../blocks/form/components/<component_name>`. Navigieren Sie beispielsweise zu `../blocks/form/components/range` und fügen Sie die folgenden Dateien hinzu:
      * `/blocks/form/components/range/_range.json`: Enthält die Definition der benutzerdefinierten Komponente.
      * `../blocks/form/components/range/range.css`: Definiert den Stil für die benutzerdefinierte Komponente.
      * `../blocks/form/components/range/range.js`: Passt die benutzerdefinierte Komponente zur Laufzeit an.

        ![Hinzufügen der benutzerdefinierten Komponente zum Authoring](/help/edge/docs/forms/universal-editor/assets/adding-custom-component.png)

        >[!NOTE]
        >
        > Stellen Sie sicher, dass die JSON-Datei einen Unterstrich (_) als Präfix im Dateinamen enthält.

1. Navigieren Sie zur Datei `/blocks/form/components/range/_range.json` und fügen Sie die Komponentendefinition für die benutzerdefinierte Komponente hinzu.

1. **Hinzufügen der Komponentendefinition**

   Um die Definition hinzuzufügen, müssen die folgenden Felder in der Datei `_range.json` hinzugefügt werden:

   * **title**: Der Titel der Komponente, die im universellen Editor angezeigt wird.
   * **id**: Eine eindeutige Kennung der Komponente.
   * **fieldType**: Formulare unterstützen verschiedene **fieldType**-Werte zur Erfassung bestimmter Typen von Benutzereingaben. Die [unterstützten fieldType-Werte finden Sie im Abschnitt „Zusätzliches Byte“](#supported-fieldtypes).
   * **resourceType**: Jeder benutzerdefinierten Komponente ist ein Ressourcentyp auf Grundlage ihres fieldType-Werts zugeordnet. Die [unterstützten fieldType-Werte finden Sie im Abschnitt „Zusätzliches Byte“](#supported-resourcetype).
   * **jcr:title**: Ähnelt einem Titel, wird jedoch innerhalb der Komponentenstruktur gespeichert.
   * **fd:viewType**: Stellt den Namen der benutzerdefinierten Komponente dar. Dies ist die eindeutige Kennung für die Komponente. Sie müssen eine benutzerdefinierte Ansicht für die Komponente erstellen.

Nach dem Hinzufügen der Komponentendefinition sieht die Datei `_range.json` wie folgt aus:

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
> Beim Hinzufügen von Blöcken zum universellen Editor verwenden alle formularbezogenen Komponenten denselben Ansatz wie Sites. Weitere Informationen finden Sie im Artikel [Erstellen von für den universellen Editor instrumentierten Blöcken](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/create-block).

### &#x200B;2. Definieren der Eigenschaften der benutzerdefinierten Komponente für das Authoring

Die benutzerdefinierte Komponente enthält ein Komponentenmodell, das angibt, welche Eigenschaften bei der Formularerstellung konfiguriert werden können. Diese Eigenschaften werden im Dialogfeld **Eigenschaften** des universellen Editors angezeigt und ermöglichen es, Einstellungen wie Beschriftungen, Überprüfungsregeln, Stile und andere Attribute anzupassen. So definieren Sie Eigenschaften:

1. Navigieren Sie zur Datei `/blocks/form/components/range/_range.json` und fügen Sie das Komponentenmodell für die benutzerdefinierte Komponente hinzu.

1. **Hinzufügen des Komponentenmodells**

   Um das Komponentenmodell für Ihre benutzerdefinierte Komponente zu definieren, müssen Sie die entsprechenden Felder zur Datei `_range.json` hinzufügen.

   1. **Erstellen eines neuen Modells**

      * Fügen Sie im Modell-Array ein neues Objekt hinzu und legen Sie die `id` des Komponentenmodells so fest, dass dies mit der zuvor in der Komponentendefinition konfigurierten Eigenschaft `fd:viewType` übereinstimmt.
      * Fügen Sie ein Felder-Array in dieses Objekt ein.

   2. **Definieren von Feldern für das Dialogfeld „Eigenschaft“**

      * Jedes Objekt im Felder-Array sollte eine Komponente vom Typ Container sein, damit es als Registerkarte im Dialogfeld **Eigenschaft** angezeigt wird.
      * Einige Felder können auf wiederverwendbare Eigenschaften verweisen, die in `models/form-common` verfügbar sind.

   3. **Verwenden eines vorhandenen Komponentenmodells als Referenz**

      * Sie können den Inhalt eines vorhandenen Komponentenmodells kopieren, das Ihrer `fieldType`-Auswahl entspricht, und ihn nach Bedarf ändern. Beispielsweise wird die Komponente `number-input` erweitert, um eine **range**-Komponente zu erstellen, sodass wir das Modell-Array aus `models/form-components/_number-input.json` als Referenz verwenden können.

   Nach dem Hinzufügen des Komponentenmodells sieht die Datei `_range.json` wie folgt aus:

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
   > Wenn Sie dem Dialogfeld **Eigenschaften** einer benutzerdefinierten Komponente ein neues Feld hinzufügen, beachten Sie das [definierte Schema](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/field-types#loading-model).

   Sie können einer benutzerdefinierten Komponente auch [benutzerdefinierte Eigenschaften hinzufügen](#adding-custom-properties-for-your-custom-component), um ihre Funktionalität zu erweitern.

#### Hinzufügen benutzerdefinierter Eigenschaften zu Ihrer benutzerdefinierten Komponente

Benutzerdefinierte Eigenschaften ermöglichen es Ihnen, bestimmte Verhaltensweisen auf der Grundlage von Werten zu definieren, die im Dialogfeld „Eigenschaft“ einer Komponente festgelegt wurden. Dadurch können die Funktionalität und die Anpassungsoptionen der Komponente erweitert werden.

In diesem Beispiel fügen wir „Step Value“ als benutzerdefinierte Eigenschaft zur Komponente „range“ hinzu.

![„Step Value“ als benutzerdefinierte Eigenschaft](/help/edge/docs/forms/universal-editor/assets/customcomponent-stepvalue.png)

Um die benutzerdefinierte Eigenschaft „Step Value“ hinzuzufügen, fügen Sie das Komponentenmodell mit den folgenden Code-Zeilen in der Datei ` _<component>.json` an:

```javascript
      {
      "component": "number",
      "name": "stepValue",
      "label": "Step Value",
      "valueType": "number"
      }
```

Das JSON-Snippet definiert eine benutzerdefinierte Eigenschaft mit der Bezeichnung **Step Value** für die Komponente **Range**. Nachstehend finden Sie eine Aufschlüsselung der einzelnen Felder:

* **component**: Gibt den Typ des Eingabefelds an, das im Dialogfeld „Eigenschaft“ verwendet wird. In diesem Fall gibt `number` an, dass das Feld numerische Werte akzeptiert.
* **name**: Die Kennung für die Eigenschaft, mit der in der Logik der Komponente darauf verwiesen wird. Hier stellt `stepValue` die Schrittwerteinstellung für den Bereich dar.
* **label**: Der Anzeigename der Eigenschaft, wie er im Dialogfeld „Eigenschaft“ angezeigt wird.
* **valueType**: Definiert den für die Eigenschaft erwarteten Datentyp. `number` stellt sicher, dass nur numerische Eingaben zulässig sind.

Sie können jetzt `stepValue` als benutzerdefinierte Eigenschaft in den JSON-Eigenschaften von `range.js` verwenden und dynamisches Verhalten basierend auf deren Wert zur Laufzeit implementieren.

Daher sieht die endgültige Datei `_range.json` nach dem Hinzufügen der Komponentendefinition, des Komponentenmodells und der benutzerdefinierten Eigenschaften wie folgt aus:

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


### &#x200B;3. Sichtbarmachen der benutzerdefinierten Komponente in der WYSIWYG-Komponentenliste

Ein Filter definiert, in welchem Abschnitt die benutzerdefinierte Komponente im universellen Editor verwendet werden kann. Dadurch wird sichergestellt, dass die Komponente nur in geeigneten Abschnitten verwendet werden kann, sodass Struktur und Benutzerfreundlichkeit erhalten bleiben.

So stellen Sie sicher, dass die benutzerdefinierte Komponente beim Erstellen von Formularen in WYSIWYG in der Liste der verfügbaren Komponenten angezeigt wird:

1. Navigieren Sie zur Datei `/blocks/form/_form.json`.
1. Suchen Sie das Komponenten-Array innerhalb des Objekts, das `id="form"` enthält.
1. Fügen Sie den Wert `fd:viewType` aus `definitions[]` zum Komponenten-Array des Objekts mit `id="form"` hinzu.

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

### &#x200B;4. Registrieren der benutzerdefinierten Komponente

Damit der Formularblock die benutzerdefinierte Komponente erkennen und beim Formular-Authoring ihre im Komponentenmodell definierten Eigenschaften laden kann, fügen Sie den Wert `fd:viewType` aus der Komponentendefinition zur Datei `mappings.js` hinzu.
So registrieren Sie eine Komponente:
1. Navigieren Sie zur Datei `/blocks/form/mappings.js`.
1. Suchen Sie das Array `customComponents[]`.
1. Fügen Sie den Wert `fd:viewType` aus dem Array `definitions[]` zum Array `customComponents[]` hinzu.

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

Nach Abschluss der oben genannten Schritte wird die benutzerdefinierte Komponente im universellen Editor in der Komponentenliste des Formulars angezeigt. Anschließend können Sie sie per Drag-and-Drop in den Formularabschnitt ziehen.

![Screenshot der Palette der Komponente „Universeller Editor“ mit der benutzerdefinierten Bereichskomponente, die per Drag-and-Drop in Formulare gezogen werden kann](/help/edge/docs/forms/universal-editor/assets/custom-component-range.png)

Der folgende Screenshot zeigt die Eigenschaften der Komponente `range` an. Diese wurde dem Komponentenmodell hinzugefügt, das die Eigenschaften angibt, die bei der Formularerstellung konfiguriert werden können:

![Screenshot des Panels für Eigenschaften des universellen Editors mit konfigurierbaren Einstellungen für die Bereichskomponente, einschließlich grundlegender Eigenschaften, Validierungsregeln und Stiloptionen](/help/edge/docs/forms/universal-editor/assets/range-properties.png)

Sie können jetzt das Laufzeitverhalten Ihrer benutzerdefinierten Komponente definieren, indem Sie Formatierung und Funktionen hinzufügen.

### &#x200B;5. Hinzufügen des Laufzeitverhaltens der benutzerdefinierten Komponente

Sie können benutzerdefinierte Komponenten mithilfe von vordefiniertem Markup ändern, wie unter [Formatieren von Formularfeldern](/help/edge/docs/forms/style-theme-forms.md) erläutert. Sie können benutzerdefinierte CSS (Cascading Style Sheets) und benutzerdefinierten Code verwenden, um das Erscheinungsbild der Komponente zu verbessern. So fügen Sie das Laufzeitverhalten für Ihre Komponente hinzu:

1. Um die Formatierung hinzuzufügen, navigieren Sie zur Datei `/blocks/form/components/range/range.css` und fügen Sie die folgende Code-Zeile hinzu:

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
   Mit dem Code können Sie die Formatierung und das visuelle Erscheinungsbild der benutzerdefinierten Komponente definieren.

1. Um die Funktionen hinzuzufügen, navigieren Sie zur Datei `/blocks/form/components/range/range.js` und fügen Sie die folgende Code-Zeile hinzu:

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

   Sie steuert, wie die benutzerdefinierte Komponente mit Benutzereingaben interagiert, Daten verarbeitet und im universellen Editor mit dem Formularblock integriert wird.

   Nach der Integration von benutzerdefinierten Formatierungen und Funktionen haben sich Erscheinungsbild und Verhalten der Komponente „range“ verbessert. Das aktualisierte Design spiegelt die angewendeten Formatierungen wider, während die zusätzlichen Funktionen ein dynamischeres und stärker interaktives Benutzererlebnis gewährleisten.
Der folgende Screenshot zeigt die aktualisierte Komponente „range“.

![Die endgültige Bereichskomponente in Aktion zeigt einen formatierten Schieberegler mit Anzeige von Wertblasen und interaktiver Funktionalität im universellen Editor](/help/edge/docs/forms/universal-editor/assets/custom-component-range-1.png)

## Häufig gestellte Fragen

* **Wenn ich Formatierungen sowohl in „component.css“ als auch in „forms.css“ hinzufüge, welche erhalten die Priorität?**
Wenn Formatierungen in `component.css` und in **forms.css** definiert sind, erhält `component.css` die Priorität. Dies liegt daran, dass Formatierungen auf Komponentenebene spezifischer sind und globale Formatierungen aus `forms.css` überschreiben.

* **Meine benutzerdefinierte Komponente ist im universellen Editor nicht in der Liste der verfügbaren Komponenten sichtbar. Wie kann ich das beheben?**
Wenn Ihre benutzerdefinierte Komponente nicht angezeigt wird, überprüfen Sie die folgenden Dateien, um sicherzustellen, dass die Komponente korrekt registriert wurde:
   * **component-definition.json**: Überprüfen Sie, ob die Komponente ordnungsgemäß definiert ist.
   * **component-filters.json**: Stellen Sie sicher, dass die Komponente in den entsprechenden Abschnitten zulässig ist.
   * **component-models.json**: Überprüfen Sie, ob das Komponentenmodell korrekt konfiguriert ist.

## Best Practices

* Es empfiehlt sich, [eine lokale AEM-Entwicklungsumgebung einzurichten](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#set-up-local-aem-development-environment), um benutzerdefinierte Formatierungen und Komponenten lokal zu entwickeln. 


## Zusätzliches Byte

### Unterstützter Ressourcentyp

| Feldtyp | Ressourcentyp |
|--------------|------------------------------------------------------------------|
| Texteingabe | core/fd/components/form/textinput/v1/textinput |
| Zahleneingabe | core/fd/components/form/numberinput/v1/numberinput |
| Datumseingabe | core/fd/components/form/datepicker/v1/datepicker |
| Bedienfeld | core/fd/components/form/panelContainer/v1/panelContainer |
| Kontrollkästchen | core/fd/components/form/checkbox/v1/checkbox |
| Dropdown | core/fd/components/form/dropdown/v1/dropdown |
| Optionsfeldgruppe | core/fd/components/form/radiobutton/v1/radiobutton |
| Nur-Text | core/fd/components/form/text/v1/text |
| Dateieingabe | core/fd/components/form/fileinput/v2/fileinput |
| E-Mail | core/fd/components/form/emailinput/v1/emailinput |
| Bild | core/fd/components/form/image/v1/image |
| Schaltfläche | core/fd/components/form/button/v1/button |

### Unterstützte Feldtypen

Folgende Feldtypen werden für Formulare unterstützt:
* Texteingabe
* Zahleneingabe
* Datumseingabe
* Bedienfeld
* Kontrollkästchen
* Dropdown
* Optionsfeldgruppe
* Nur-Text
* Dateieingabe
* E-Mail
* Bild
* Schaltfläche

## Siehe auch

{{universal-editor-see-also}}
