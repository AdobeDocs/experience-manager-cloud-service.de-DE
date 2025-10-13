---
title: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
description: Erstellen benutzerdefinierter Komponenten für ein EDS-Formular
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 9664495d17ad8a8101c886408bee1584b3d48f1e
workflow-type: tm+mt
source-wordcount: '2103'
ht-degree: 99%

---


# Erstellen einer benutzerdefinierten Formularkomponente im adaptiven Formularblock

Edge Delivery Services Forms bietet eine Anpassung, die es Frontend-Entwicklerinnen und -Entwicklern ermöglicht, maßgeschneiderte Formularkomponenten zu erstellen. Diese benutzerdefinierten Komponenten lassen sich nahtlos in das WYSIWYG-Authoring-Erlebnis integrieren und können im Formulareditor einfach hinzugefügt, konfiguriert und verwaltet werden. Mit benutzerdefinierten Komponenten können Sie die Funktionalität verbessern und gleichzeitig einen reibungslosen und intuitiven Authoring-Prozess sicherstellen.

In diesem Dokument werden die Schritte zum Erstellen benutzerdefinierter Komponenten durch Formatieren der nativen HTML-Formularkomponenten beschrieben, um das Anwendererlebnis zu verbessern und den visuellen Reiz des Formulars zu erhöhen.

## Architekturüberblick

Die benutzerdefinierte Komponente für den Formularblock folgt einem Architekturmuster des Typs **MVC (Model-View-Controller)**:

### Modell

- Wird durch das JSON-Schema für jede `field/component` definiert.

- Bearbeitbare Eigenschaften sind in der entsprechenden JSON-Datei angegeben (siehe „blocks/form/models/form-components“).

- Diese Eigenschaften stehen Autorinnen und Autoren im Formular-Builder zur Verfügung und werden als Teil der Felddefinition (fd) an die Komponente übergeben.

### Anzeigen

- Die HTML-Struktur für jeden Feldtyp wird in „form-field-types“ beschrieben.

- Dies ist die Basisstruktur für Ihre Komponente, die erweitert oder geändert werden kann.

- Die HTML-Basisstruktur für jede vordefinierte Komponente wird in „form-field-types“ dokumentiert.

### Controller-/Komponentenlogik

- In JavaScript implementiert, entweder als vorkonfigurierte oder benutzerdefinierte Komponenten.  – Befindet sich in `blocks/form/components` für benutzerdefinierte Komponenten.

## Vorkonfigurierte Komponenten

**Vorkonfigurierte Komponenten** bieten die Grundlage für die benutzerdefinierte Entwicklung:

- Vorkonfigurierte Komponenten befinden sich in `blocks/form/models/form-components`.

- Jede vorkonfigurierte Komponente verfügt über eine JSON-Datei, die ihre bearbeitbaren Eigenschaften definiert (z. B. ` _text-input.json`,`_drop-down.json`).

- Diese Eigenschaften stehen Autorinnen und Autoren im Formular-Builder zur Verfügung und werden als Teil der Felddefinition (fd) an die Komponente übergeben.

- Die HTML-Basisstruktur für jede vordefinierte Komponente wird in „form-field-types“ dokumentiert.

Durch das Erweitern einer vorhandenen vorkonfigurierten Komponente können Sie deren Grundstruktur, Verhalten und Eigenschaften wiederverwenden und sie an Ihre Anforderungen anpassen.

- Benutzerdefinierte Komponenten müssen aus einem vordefinierten Satz vorkonfigurierter Komponenten erweitert werden.

- Das System identifiziert, welche vorkonfigurierte Komponente erweitert werden soll, basierend auf der `viewType`-Eigenschaft im JSON-Code des Felds.

- Das System verwaltet eine Registrierung zulässiger benutzerdefinierter Komponentenvarianten. Nur in dieser Registrierung aufgeführte Varianten können verwendet werden, z. B. `customComponents[]` in `mappings.js`.

- Beim Rendern eines Formulars prüft das System die Varianteneigenschaft oder `:type/fd:viewType`. Wenn dies mit einer registrierten benutzerdefinierten Komponente übereinstimmt, werden die entsprechenden JS- und CSS-Dateien aus dem Ordner `blocks/form/components` geladen.

- Die benutzerdefinierte Komponente wird dann auf die HTML-Basisstruktur der vorkonfigurierten Komponente angewendet, sodass Sie ihr Verhalten und Aussehen erweitern oder überschreiben können.

## Struktur der benutzerdefinierten Komponente

Um benutzerdefinierte Komponenten zu erstellen, können Sie die **Strukturvorlagen-CLI** verwenden und so die für Ihre Komponente erforderlichen Dateien und Ordner einrichten und dann Code für Ihre benutzerdefinierte Komponente hinzufügen.

- Benutzerdefinierte Komponenten befinden sich im Ordner `blocks/form/components`.

- Jede benutzerdefinierte Komponente muss in einem eigenen, nach der Komponente benannten Ordner platziert werden, z. B. „cards“ für Karten. Innerhalb des Ordners sollten die folgenden Dateien sein:

   - **_cards.json**: JSON-Datei, die die Komponentendefinition einer vorkonfigurierten Komponente erweitert und ihre bearbeitbaren Eigenschaften (models[]) sowie die Inhaltsstruktur beim Laden definiert (definitions[]).
   - **cards.js**: Die JavaScript-Datei, die die Hauptlogik enthält.
   - **cards.css**: Optional, für Stile.

- Der Name des Ordners und die JS-/CSS-Dateien müssen übereinstimmen.

### Wiederverwenden und Erweitern von Feldern in benutzerdefinierten Komponenten

Befolgen Sie beim Definieren von Feldern im JSON-Code Ihrer benutzerdefinierten Komponente (für beliebige Feldergruppen, Standard, Validierung, Hilfe usw.) die folgenden Best Practices, um die Wartung und Konsistenz zu gewährleisten:

- Sie können Standardfelder/freigegebene Felder wiederverwenden, indem Sie auf vorhandene freigegebene Container oder Felddefinitionen verweisen (z. B. `../form-common/_basic-input-placeholder-fields.json#/fields`, `../form-common/_basic- validation-fields.json#/fields`). Dadurch wird sichergestellt, dass alle Standardoptionen übernommen werden, ohne dass sie dupliziert werden.

- Fügen Sie nur neue oder benutzerdefinierte Felder explizit in Ihrem Container hinzu. Dadurch bleibt Ihr Schema DRY und fokussiert.

- Entfernen oder vermeiden Sie das Duplizieren von Feldern, die bereits über Verweise enthalten sind. Definieren Sie nur Felder, die für die Logik Ihrer Komponente eindeutig sind.

- Verweisen Sie nach Bedarf auf Hilfe-Container und andere freigegebene Inhalte (z. B. `../form-common/_help-container.json`), um Konsistenz und Verwaltbarkeit zu gewährleisten.

>[!TIP]
>
> - Dieses Muster erleichtert die zukünftige Aktualisierung oder Erweiterung der Logik und stellt sicher, dass Ihre benutzerdefinierten Komponenten mit dem Rest des Formularsystems konsistent bleiben.
> - Prüfen Sie immer, ob freigegebene Container oder Felddefinitionen vorhanden sind, bevor Sie neue hinzufügen.

### Definieren neuer Eigenschaften für benutzerdefinierte Komponenten

- Wenn Sie neue Eigenschaften für Ihre benutzerdefinierte Komponente von Autorinnen und Autoren erfassen müssen, können Sie dies tun, indem Sie ein Feld im Array `fields[]` der Komponente in der JSON der Komponente definieren.

- Die benutzerdefinierte Komponente wird mithilfe der Eigenschaft :type identifiziert, die als `fd:viewType` in der JSON-Datei festgelegt werden kann (z. B. `fd:viewType: cards`). So kann das System die richtige benutzerdefinierte Komponente erkennen und laden. Daher ist dies für benutzerdefinierte Komponenten obligatorisch.

- Alle neuen Eigenschaften, die in der JSON-Definition hinzugefügt werden, sind in der Felddefinition als Eigenschaften verfügbar. `<propertyName>` in der JS-Logik Ihrer Komponente.

## JavaScript-API für benutzerdefinierte Komponenten

Die JavaScript-API für benutzerdefinierte Komponenten definiert, wie das Verhalten, das Erscheinungsbild und die Reaktivität Ihrer benutzerdefinierten Formularkomponente gesteuert werden.

### Funktion „decorate“

Die Funktion **decorate** ist der Einstiegspunkt für Ihre benutzerdefinierte Komponente. Sie initialisiert die Komponente, verknüpft sie mit ihrer JSON-Definition und ermöglicht es Ihnen, ihre HTML-Struktur und ihr Verhalten zu bearbeiten.

>[!NOTE]
>
> Die JavaScript-Datei der benutzerdefinierten Komponente muss eine Standardfunktion als „decorate“ exportieren:

#### Funktionssignatur:

```javascript
export default function decorate(element, fieldJson, container, formId) 
{
  // element: The HTML structure of the OOTB component you are extending
  // fieldJson: The JSON field definition (all authorable properties)
  // container: The parent element (fieldset or form)
  // formId: The id of the form

  // ... your logic here ...
}
```

Sie kann:

- **Das Element ändern**: Fügt Ereignis-Listener hinzu, aktualisiert Attribute oder fügt zusätzliches Markup ein.

- **Auf JSON-Eigenschaften zugreifen**: Verwenden Sie `fd.properties.<propertyName>`, um die im JSON-Schema definierten Werte zu lesen und in der Komponentenlogik anzuwenden.

## Funktion „subscribe“

Die Funktion **subscribe** ermöglicht es Ihrer Komponente, auf Änderungen von Feldwerten oder benutzerspezifische Ereignisse zu reagieren. Dadurch wird sichergestellt, dass die Komponente mit dem Formulardatenmodell synchron bleibt und ihre Benutzeroberfläche dynamisch aktualisieren kann.

### Funktionssignatur:

```javascript
import { subscribe } from '../../rules/index.js';
export default function decorate(fieldDiv, fieldJson, container, formId) {
  // Access custom properties defined in the JSON
  const { initialText, finalText, time } = fieldJson?.properties;

  // ... setup logic ...

  subscribe(fieldDiv, formId, (_fieldDiv, fieldModel) => {
    fieldModel.subscribe(() => {
      // React to custom event (e.g., resetCardOption)
      // ... logic ...
    }, 'resetCardOption');
  });
}
```

Sie kann:

- **Einen Rückruf registrieren**: Der Aufruf von **subscribe(element, formId, callback)** registriert Ihren Rückruf so, dass er ausgeführt wird, wenn sich die Felddaten ändern. Verwenden Sie zwei Rückrufparameter:
   - **element**: Das HTML-Element, das das Feld darstellt.
   - **fieldModel**: Das Objekt, das den Status des Felds und die Ereignis-APIs darstellt.

- **Änderungen oder Ereignisse überwachen**: Verwenden Sie `fieldModel.subscribe((event) => { ... }, 'eventName')`, um Logik auszuführen, wenn sich ein Wert ändert oder ein benutzerspezifisches Ereignis ausgelöst wird. Das Ereignisobjekt enthält Details zu den Änderungen.

## Erstellen einer benutzerdefinierten Komponente

In diesem Abschnitt erfahren Sie, wie Sie eine **benutzerdefinierte Kartenkomponente** erstellen, indem Sie die vorkonfigurierte Optionsfeldkomponente erweitern.

![Benutzerdefinierte Kartenkomponente](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### 1. Code-Einrichtung

#### 1.1 Dateien und Ordner

Der erste Schritt besteht darin, die erforderlichen Dateien der benutzerdefinierten Komponente einzurichten und sie mit dem Code im Repository zu verbinden. Dieser Vorgang wird automatisch von der **AEM Forms-Strukturvorlagen-CLI** durchgeführt, wodurch die Strukturierung und Verbindung der erforderlichen Dateien beschleunigt wird.

>[!VIDEO](https://video.tv.adobe.com/v/3474752)

1. Öffnen Sie das Terminal und navigieren Sie zum Stammverzeichnis Ihres Formularprojekts.
2. Führen Sie die folgenden Befehle aus:

```bash
npm install
npm run create:custom-component
```

![Strukturvorlagen-CLI](/help/edge/docs/forms/universal-editor/assets/scaffolder-cli.png)

Sie werden:

- **Aufgefordert**, die neue Komponente zu benennen. Verwenden Sie in diesem Fall beispielsweise „cards“.
- **Gebeten**, eine Basiskomponente (Optionsfeldgruppe) auszuwählen

Dadurch werden alle erforderlichen Ordner und Dateien erstellt, einschließlich:

```
blocks/form/
└── components/
  └── cards/
    ├── cards.js
    └── cards.css
    └── _cards.json
```

Außerdem wird alles mit dem Rest des Codes im Repository verbunden, wie in der Ausgabe der CLI gezeigt.
Die folgenden Funktionen werden automatisch ausgeführt:

- Karten werden zu den Filtern hinzugefügt, damit sie innerhalb des adaptiven Formularblocks hinzugefügt werden können.
- Die Zulassungsliste von `mappings.js` wird aktualisiert, sodass sie die neue Kartenkomponente enthält.
- Die Definition der Kartenkomponente wird unter der Auflistung **Benutzerdefinierte Komponenten** im universellen Editor registriert.

>[!NOTE]
>
> Sie können eine benutzerdefinierte Komponente auch mit der manuellen Methode (Legacy-Methode) erstellen. Einzelheiten zum Erstellen benutzerdefinierter Komponenten finden Sie im Abschnitt [Manuelle Methode oder Legacy-Methode](#manual-or-legacy-method-to-create-custom-component).

#### 1.2 Verwenden der Komponente im universellen Editor

1. **Aktualisieren des universellen Editors**: Öffnen Sie das Formular im universellen Editor und aktualisieren Sie die Seite, um sicherzustellen, dass der neueste Code aus dem Repository geladen wird.

2. **Hinzufügen der benutzerdefinierten Komponente**

   1. Klicken Sie auf der Formulararbeitsfläche auf die Schaltfläche **Hinzufügen (+)**.
   2. Scrollen Sie zum Abschnitt „Benutzerdefinierte Komponenten“.
   3. Wählen Sie die neu erstellte **Kartenkomponente** aus, um sie in Ihr Formular einzufügen.

      ![Auswählen der benutzerdefinierten Komponente](/help/edge/docs/forms/universal-editor/assets/select-custom-component.png)

Da innerhalb von `cards.js` kein Code vorhanden ist, wird benutzerdefinierte Komponente als Optionsfeldgruppe gerendert.

#### 1.3 Lokale Vorschau und Tests

Da das Formular nun die benutzerdefinierte Komponente enthält, können Sie das Formular als Proxy verwenden und lokal Änderungen daran vornehmen und diese anzeigen:

1. Navigieren Sie zu Ihrem Terminal und führen Sie `aem up` aus.

2. Öffnen Sie den unter `http://localhost:3000/{path-to-your-form}` gestarteten Proxy-Server (Pfadbeispiel: `/content/forms/af/custom-component-form`).


### 2. Implementieren von benutzerdefiniertem Verhalten für Ihre benutzerdefinierte Komponente

#### 2.1 Gestalten der benutzerdefinierten Komponente

Fügen Sie der Komponente zur Gestaltung die Klasse **card** und für jedes Optionsfeld ein Bild hinzu. Verwenden Sie dazu den folgenden Code.

**Gestalten Sie die Komponente mit card.js**

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');

  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper) => {
    const image = createOptimizedPicture(
      'https://main--afb--jalagari.hlx.live/lab/images/card.png',
      'card-image'
    );
    radioWrapper.appendChild(image);
  });

  return element;
}
```

**Laufzeitverhalten mithilfe von cards.css hinzufügen**

```javascript
.card .radio-wrapper {
  min-width: 320px; /* or whatever width fits your design */
  max-width: 340px;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  flex: 0 0 auto;
  scroll-snap-align: start;
  padding: 24px 16px;
  margin-bottom: 0;
  position: relative;
  transition: box-shadow 0.2s;
  display: flex;
  align-items: flex-start;
  gap: 12px;
}
```

Die Kartenkomponente sieht nun wie folgt aus:

![Hinzufügen von „cards.css“ und „cards.js“](/help/edge/docs/forms/universal-editor/assets/add-card-css.png)

#### 2.2 Hinzufügen von dynamischem Verhalten mithilfe der Funktion „subscribe“

Wenn die Dropdown-Liste geändert wird, werden die Karten abgerufen und in der Aufzählung der Optionsfeldgruppe festgelegt. Die Ansicht kann dies jedoch derzeit nicht verarbeiten. Daher wird dies wie unten dargestellt gerendert:

![Funktion „subscribe“](/help/edge/docs/forms/universal-editor/assets/card-subscribe.png)

Beim Aufruf der API wird das Feldmodell festgelegt. Die Änderungen müssen überwacht und die Ansicht entsprechend gerendert werden. Dies wird mithilfe der **Funktion „subscribe“** erreicht.

Konvertieren Sie den Ansichts-Code im vorherigen Schritt in eine Funktion und rufen Sie dies wie unten dargestellt in der Funktion „subscribe“ in `cards.js` auf:

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';
import { subscribe } from '../../rules/index.js';

function createCard(element, enums) {
  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper, index) => {
    if (enums[index]?.name) {
      let label = radioWrapper.querySelector('label');

      if (!label) {
        label = document.createElement('label');
        radioWrapper.appendChild(label);
      }

      label.textContent = enums[index]?.name;
    }

    const image = createOptimizedPicture(
      enums[index]?.image || 'https://main--afb--jalagari.hlx.page/lab/images/card.png',
      'card-image'
    );

    radioWrapper.appendChild(image);
  });
}

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');
  createCard(element, fieldJson.enum);

  subscribe(element, formId, (fieldDiv, fieldModel) => {
    fieldModel.subscribe((e) => {
      const { payload } = e;

      payload?.changes?.forEach((change) => {
        if (change?.propertyName === 'enum') {
          createCard(element, change.currentValue);
        }
      });
    });
  });

  return element;
}
```

**Verwenden der Funktion „subscribe“, um die Ereignisänderungen in „cards.js“ zu überwachen**

Wenn Sie jetzt die Dropdown-Liste ändern, werden die Karten wie unten dargestellt befüllt:

![Funktion „subscribe“](/help/edge/docs/forms/universal-editor/assets/card-subscribe-final.png)

#### 2.3 Synchronisieren von Ansichtsaktualisierungen mit dem Feldmodell

Zum Synchronisieren der Ansichtsänderungen mit dem Feldmodell müssen Sie den Wert der ausgewählten Karte festlegen. Fügen Sie also den folgenden Änderungsereignis-Listener in „cards.js“ wie unten dargestellt hinzu:

**Verwenden der Feldmodell-API in „cards.js“**

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';
import { subscribe } from '../../rules/index.js';

function createCard(element, enums) {
  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper, index) => {
    if (enums[index]?.name) {
      let label = radioWrapper.querySelector('label');

      if (!label) {
        label = document.createElement('label');
        radioWrapper.appendChild(label);
      }

      label.textContent = enums[index]?.name;
    }

    // Attach index to input element for later reference
    radioWrapper.querySelector('input').dataset.index = index;

    const image = createOptimizedPicture(
      enums[index]?.image || 'https://main--afb--jalagari.hlx.page/lab/images/card.png',
      'card-image'
    );

    radioWrapper.appendChild(image);
  });
}

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');
  createCard(element, fieldJson.enum);

  subscribe(element, formId, (fieldDiv, fieldModel) => {
    fieldModel.subscribe((e) => {
      const { payload } = e;

      payload?.changes?.forEach((change) => {
        if (change?.propertyName === 'enum') {
          createCard(element, change.currentValue);
        }
      });
    });

    element.addEventListener('change', (e) => {
      e.stopPropagation();
      const value = fieldModel.enum?.[parseInt(e.target.dataset.index, 10)];
      fieldModel.value = value.name;
    });
  });

  return element;
}
```

Jetzt wird die benutzerdefinierte Kartenkomponente angezeigt, wie unten dargestellt:

![Benutzerdefinierte Kartenkomponente](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### 3. Committen und Übertragen von Änderungen

Nachdem Sie JavaScript und CSS für Ihre benutzerdefinierte Komponente implementiert und lokal überprüft haben, committen Sie die Änderungen in Ihr Git-Repository.

```bash
git add . && git commit -m "Add card custom component" && git push
```

Sie haben in wenigen einfachen Schritten erfolgreich eine komplexe benutzerdefinierte Kartenauswahlkomponente erstellt.

+++ **Manuelle Methode oder Legacy-Methode zum Erstellen benutzerdefinierter Komponenten**

Die Legacy-Methode besteht darin, die unten beschriebenen Schritte manuell auszuführen:

1. **Wählen Sie eine vorkonfigurierte Komponente** aus, die erweitert werden soll (z. B. Schaltfläche, Dropdown-Liste, Texteingabe usw.). Erweitern Sie in diesem Fall die Optionsfeldkomponente.

2. **Erstellen Sie einen Ordner** in `blocks/form/components` mit dem Namen Ihrer Komponente (in diesem Fall „cards“).

3. **Fügen Sie eine JS-Datei** mit demselben Namen hinzu:
   - `blocks/form/components/cards/cards.js`.

4. (Optional) **Fügen Sie eine CSS-Datei** für benutzerdefinierte Stile hinzu:
   - `blocks/form/components/cards/cards.css.`

5. **Definieren Sie eine neue JSON-Datei** (z. B. ` _cards.json`) im selben Ordner wie Ihre **JS-Komponentendatei** (`blocks/form/components/cards/_cards.json`). Diese JSON sollte eine vorhandene Komponente erweitern und in ihren Definitionen `fd:viewType` auf den Namen Ihrer Komponente festlegen (in diesem Fall „cards“):

   - Fügen Sie für alle Feldergruppen (Standard, Validierung, Hilfe usw.) Ihre benutzerdefinierten Felder explizit hinzu.

6. **Implementieren Sie die JS- und CSS-Logik:**
   - Exportieren Sie eine Standardfunktion wie oben beschrieben.
   - Verwenden Sie den Parameter **element**, um die HTML-Basisstruktur zu ändern.
   - Verwenden Sie bei Bedarf den Parameter **fieldJson** für Standardfelddaten.
   - Verwenden Sie die Funktion **subscribe**, um bei Bedarf Feldänderungen oder benutzerspezifische Ereignisse zu überwachen.

     >[!NOTE]
     >
     >Implementieren Sie die JS- und CSS-Logik für Ihre benutzerdefinierte Komponente wie oben beschrieben.

7. Registrieren Sie Ihre Komponente als Variante im Formular-Builder und legen Sie die Varianteneigenschaft oder
   `fd:viewType/:type` in der JSON auf den Namen Ihrer Komponente fest. Fügen Sie beispielsweise den Wert `fd:viewType` aus `definitions[]` als Karten zum Komponenten-Array des Objekts mit `id="form` hinzu.

   ```
       {
     "definitions": [
       {
         "title": "Cards",
         "id": "cards",
         "plugins": {
           "xwalk": {
             "page": {
               "resourceType": "core/fd/components/form/radiobutton/v1/radiobutton",
               "template": {
                 "jcr:title": "Cards",
                 "fieldType": "radio-button",
                 "fd:viewType": "cards",
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

8. **Aktualisieren Sie „mappings.js“**: Fügen Sie den Namen Ihrer Komponente zur Liste **OOTBComponentDecorators** (für Komponenten im vorkonfigurierten Stil) oder **customComponents** hinzu, damit sie vom System erkannt und geladen wird.

   ```javascript
   let customComponents = ["cards"];
   const OOTBComponentDecorators = [];
   ```

9. **Aktualisieren Sie „_form.json“**: Fügen Sie den Namen Ihrer Komponente zum Array `filters.components` hinzu, damit sie in der Authoring-Benutzeroberfläche abgelegt werden kann.

   ```javascript
   "filters": [
   {
       "id": "form",
       "components": [ "cards"]}
       ]
   ```

10. **Aktualisieren Sie „_component-definition.json“**: Aktualisieren Sie in `models/_component-definition.json` das Array innerhalb der Gruppe mit `id custom-components` mit einem Objekt wie folgt:

   ```javascript
   {
   "...":"../blocks/form/components/cards/_cards.json#/definitions"
   }
   ```

   Dadurch wird der Verweis auf die neue Kartenkomponente bereitgestellt, die mit dem Rest der Komponenten erstellt werden soll.

11. **Führen Sie das Build:json-Skript aus**: Führen Sie `npm run build:json` aus, um alle Komponenten-JSON-Definitionen zu kompilieren und in einer einzigen Datei zusammenzuführen, die vom Server bereitgestellt wird. Dadurch wird sichergestellt, dass das Schema der neuen Komponente in der zusammengeführten Ausgabe enthalten ist.

12. Committen und übertragen Sie Ihre Änderungen in das Git-Repository.

Jetzt können Sie die benutzerdefinierte Komponente zu Ihrem Formular hinzufügen.

+++

## Erstellen einer zusammengesetzten Komponente

Eine zusammengesetzte Komponente wird durch Kombinieren mehrerer Komponenten erstellt.
Eine zusammengesetzte Komponente des Typs „Nutzungsbedingungen“ besteht beispielsweise aus einem übergeordneten Panel, das Folgendes enthält:

- Ein Klartextfeld zur Anzeige der Bedingungen

- Ein Kontrollkästchen zum Erfassen der Benutzerzustimmung

Diese Kompositionsstruktur wird als Vorlage innerhalb der JSON-Datei der jeweiligen Komponente definiert. Das folgende Beispiel zeigt, wie Sie eine Vorlage für eine Komponente des Typs „Nutzungsbedingungen“ definieren:

```javascript
{
  "definitions": [
    {
      "title": "Terms and conditions",
      "id": "tnc",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/termsandconditions/v1/termsandconditions",
            "template": {
              "jcr:title": "Terms and conditions",
              "fieldType": "panel",
              "fd:viewType": "tnc",
              "text": {
                "value": "Text related to the terms and conditions come here.",
                "sling:resourceType": "core/fd/components/form/text/v1/text",
                "fieldType": "plain-text",
                "textIsRich": true
              },
              "approvalcheckbox": {
                "name": "approvalcheckbox",
                "jcr:title": "I agree to the terms & conditions.",
                "sling:resourceType": "core/fd/components/form/checkbox/v1/checkbox",
                "fieldType": "checkbox",
                "required": true,
                "type": "string",
                "enum": [
                  "true"
                ]
              }
            }
          }
        }
      }
    }
  ],
  ...
}
```

## Best Practices

Beachten Sie die folgenden Punkte, bevor Sie Ihre eigene benutzerdefinierte Komponente erstellen:

- **Konzentrieren der Komponentenlogik**: Fügen Sie nur das hinzu bzw. überschreiben Sie nur das, was für Ihr benutzerdefiniertes Verhalten erforderlich ist.

- **Nutzen der Basisstruktur**: Verwenden Sie das vorkonfigurierte HTML als Ausgangspunkt.

- **Verwenden bearbeitbarer Eigenschaften:** Legen Sie konfigurierbarer Optionen über das JSON-Schema frei.

- **Namespace Ihres CSS**: Vermeiden Sie Stilkollisionen durch die Verwendung eindeutiger Klassennamen.

## Verweise

- [form-field-types](/help/edge/docs/forms/eds-form-field-properties.md): HTML-Basisstrukturen und -Eigenschaften für alle Feldtypen.

- **blocks/form/models/form-components**: Definitionen von vorkonfigurierten und benutzerdefinierten Komponenteneigenschaften.

- **blocks/form/components**: Ort für Ihre benutzerdefinierten Komponenten. `blocks/form/components/countdown-timer/_countdown-timer.json` zeigt beispielsweise, wie eine Basiskomponente erweitert und neue Eigenschaften hinzugefügt werden.
