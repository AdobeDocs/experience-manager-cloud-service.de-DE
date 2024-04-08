---
title: Ereignisse des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Ereignisse, die der universelle Editor sendet und mit denen Sie auf Änderungen an Inhalten oder Benutzeroberfläche in Ihrer Remote-App reagieren können.
exl-id: c9f7c284-f378-4725-a4e6-e4799f0f8175
source-git-commit: 11a244b7dd4810fbfec92b3effc362102e7322dc
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 3%

---

# Ereignisse des universellen Editors {#events}

Erfahren Sie mehr über die verschiedenen Ereignisse, die der universelle Editor sendet und mit denen Sie auf Änderungen an Inhalten oder Benutzeroberfläche in Ihrer Remote-App reagieren können.

## Einführung {#introduction}

Anwendungen können unterschiedliche Anforderungen für Seiten- oder Komponentenaktualisierungen haben. Daher sendet der universelle Editor definierte Ereignisse an Remote-Anwendungen. Wenn die Remote-Anwendung keinen benutzerdefinierten Ereignis-Listener für das gesendete Ereignis hat, wird ein [Fallback-Ereignis-Listener](#fallback-listeners) von `universal-editor-cors` -Paket ausgeführt wird.

Alle Ereignisse werden auf dem betroffenen DOM-Element der Remote-Seite aufgerufen. Ereignisse, die an die `BODY` -Element, bei dem der standardmäßige Ereignis-Listener, der von der `universal-editor-cors` -Paket registriert ist. Es gibt Ereignisse für den Inhalt und die Ereignisse für die Benutzeroberfläche.

Alle Ereignisse folgen einer Namenskonvention.

* `aue:<content-or-ui>-<event-name>`

Beispiel: `aue:content-update` und `aue:ui-select`

Ereignisse umfassen die Payload der Anfrage und der Antwort und werden ausgelöst, sobald der entsprechende Aufruf erfolgreich war. Weitere Informationen zu Aufrufen und Beispielen für deren Payloads finden Sie im Dokument . [Universal-Editor-Aufrufe.](/help/implementing/universal-editor/calls.md)

## Inhaltsaktualisierungsereignisse {#content-events}

### aue:content-add {#content-add}

Die `aue:content-add` -Ereignis ausgelöst wird, wenn einem Container eine neue Komponente hinzugefügt wird.

Die Payload ist Inhalt vom Universal Editor-Dienst mit Fallback-Inhalt aus der Komponentendefinition.

```json
{
    details: {
        request: request payload;   // what is sent to the service
        response: {                 // what is returned by the service
            resource: string;       // newly created content resource
            updates: [{
                resource: string;   // resource to update
                type: string;       // type of instrumentation
                content?: string;   // content to replace
            }]
        }
    }
}
```

### aue:content-details {#content-details}

Die `aue:content-details` -Ereignis ausgelöst wird, wenn eine Komponente in der Eigenschaftenleiste geladen wird.

Die Payload ist der Inhalt der Komponente und optional ihr Schema.

```json
{
    details: {
        content: object             // content object
        model: [object]             // model object
        request: request payload;   // what is sent to the service
        response: response payload; // what is returned by the service
    }
}
```

### aue:content-move {#content-move}

Die `aue:content-move` -Ereignis ausgelöst wird, wenn eine Komponente verschoben wird.

Die Payload ist der Komponenten-, Quell-Container- und Ziel-Container.

```json
{
    details: {
        from: string;                   // container we move the component from
        component: string;              // component we move
        to: string;                     // container we move the component to
        before: string;                    // before which component shall we place the component
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-patch {#content-patch}

Die `aue:content-patch` -Ereignis ausgelöst wird, wenn die Daten einer Komponente in der Eigenschaftenleiste aktualisiert werden.

Die Payload ist ein JSON-Patch der aktualisierten Eigenschaften.

```json
{
    details: {
        patch: {
            name: string;               // attribute which is updated
            value: string;              // new value which is stored to the attribute
        },
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-remove {#content-remove}

Die `aue:content-remove` -Ereignis ausgelöst wird, wenn eine Komponente aus einem Container entfernt wird.

Die Payload ist die Element-ID der entfernten Komponente.

```json
{
    details: {
        resource: string;               // the resource which got removed
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-update {#content-update}

Die `aue:content-update` -Ereignis ausgelöst wird, wenn die Eigenschaften einer Komponente im Kontext aktualisiert werden.

Die Payload ist der aktualisierte Wert.

```json
{
    details: {
        value: string;                  // updated value
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service 
    }
}
```

### Weitergeben von Payloads {#passing-payloads}

Bei allen Inhaltsupdate-Ereignissen werden die angeforderte Payload sowie die Antwort-Payload an das Ereignis übergeben. Beispiel für einen Aktualisierungsaufruf:

Anfrage-Payload:

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-p7452-e12433.adobeaemcloud.com"
    }
  ],
  "target": {
    "resource": "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
    "type": "text",
    "prop": "title"
  },
  "value": "Alhoa Spirit Northern Norway!"
}
```

Antwort-Payload

```json
{
    "updates": [
        {
            "resource": "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
            "prop": "title",
            "type": "text"
        }
    ]
}
```

## Benutzeroberflächen-Ereignisse {#ui-events}

### aue:ui-publish {#ui-publish}

Die `aue:ui-publish` -Ereignis ausgelöst wird, wenn der Inhalt veröffentlicht wird (mit Aufruf am `BODY` Ebene).

Die Payload ist eine Liste von Element-IDs und ihrem Veröffentlichungsstatus.

### aue:ui-select {#ui-select}

Die `aue:ui-select` -Ereignis ausgelöst wird, wenn eine Komponente ausgewählt wird.

Die Payload ist die Element-ID, Elementeigenschaften und Elementtyp der ausgewählten Komponente.

```json
{
    details: {
        resource: string;       // resource of the selected
        prop: string;           // prop of the selected
        type: string;           // type of the selected
        selected: boolean;      // was selected or unselected
    }
}
```

### aue:ui-preview {#ui-preview}

Die `aue:ui-preview` -Ereignis ausgelöst wird, wenn der Bearbeitungsmodus der Seite in **Vorschau**.

Die Payload für dieses Ereignis ist leer.

```json
{
    details: {}
}
```

### aue:ui-edit {#ui-edit}

Die `aue:ui-edit` -Ereignis ausgelöst wird, wenn der Bearbeitungsmodus der Seite in **Bearbeiten**.

Die Payload für dieses Ereignis ist leer.

```json
{
    details: {}
}
```

### aue:ui-viewport-change {#ui-viewport-change}

Die `aue:ui-viewport-change` -Ereignis ausgelöst wird, wenn die Darstellungsfeldgröße geändert wird.

Die Nutzlast ist die Abmessungen des Viewports.

```json
{
    details: {
        height: number?;        // height of the viewport. Undefined when fullscreen
        width: number?;         // width of the viewport. Undefined when fullscreen
    }
}
```

### aue:initialized {#initialized}

Die `aue:initialized` -Ereignis ausgelöst wird, um der Remote-Seite mitzuteilen, dass sie erfolgreich im universellen Editor geladen wurde.

Die Payload für dieses Ereignis ist leer.

```json
{
    details: {}
}
```

## Fallback-Ereignis-Listener {#fallback-listeners}

### Inhaltsaktualisierungen {#content-update-fallbacks}

| Ereignis | Verhalten |
|---|---|
| `aue:content-add` | Seitenneuladung |
| `aue:content-details` | Nichts tun |
| `aue:content-move` | Verschieben Sie den Inhalt/die Struktur der Komponente in den Zielbereich |
| `aue:content-patch` | Seitenneuladung |
| `aue:content-remove` | Entfernen des DOM-Elements |
| `aue:content-update` | Aktualisieren Sie die `innerHTML` mit der Payload |

### Benutzeroberflächen-Ereignisse {#ui-event-fallbacks}

| Ereignis | Verhalten |
|---|---|
| `aue:ui-publish` | Nichts tun |
| `aue:ui-select` | Scrollen Sie zum ausgewählten Element |
| `aue:ui-preview` | Hinzufügen `class="adobe-ue-preview"` zum HTML-Tag |
| `aue:ui-edit` | Hinzufügen `class=adobe-ue-edit"` zum HTML-Tag |
| `aue:ui-viewport-change` | Nichts tun |
| `aue:initialized` | Nichts tun |

## Zusätzliche Ressourcen {#additional-resources}

* [Aufrufe im universellen Editor](/help/implementing/universal-editor/calls.md)

