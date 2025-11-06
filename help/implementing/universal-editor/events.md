---
title: Ereignisse des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Ereignisse, die der universelle Editor sendet und mit denen Sie auf Änderungen an Inhalten oder an der Benutzeroberfläche in Ihrer Remote-App reagieren können.
exl-id: c9f7c284-f378-4725-a4e6-e4799f0f8175
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 100%

---

# Ereignisse des universellen Editors {#events}

Erfahren Sie mehr über die verschiedenen Ereignisse, die der universelle Editor sendet und mit denen Sie auf Änderungen an Inhalten oder an der Benutzeroberfläche in Ihrer Remote-App reagieren können.

## Einführung {#introduction}

Anwendungen können unterschiedliche Anforderungen bei der Aktualisierung von Seiten oder Komponenten haben. Daher sendet der universelle Editor definierte Ereignisse an Remote-Anwendungen. Wenn die Remote-Anwendung über keinen benutzerdefinierten Ereignis-Listener für das gesendete Ereignis verfügt, wird ein vom Paket `universal-editor-cors` bereitgestellter [Fallback-Ereignis-Listener](#fallback-listeners) ausgeführt.

Alle Ereignisse werden für das betroffene DOM-Element der Remote-Seite aufgerufen. Ereignisse werden an das Element `BODY` übergeben, bei dem der standardmäßige, vom Paket `universal-editor-cors` bereitgestellte Ereignis-Listener registriert ist. Es gibt Ereignisse für den Inhalt und Ereignisse für die Benutzeroberfläche.

Alle Ereignisse folgen einer Namenskonvention.

* `aue:<content-or-ui>-<event-name>`

Zum Beispiel `aue:content-update` und `aue:ui-select`

Ereignisse umfassen die Payload der Anfrage und der Antwort und werden ausgelöst, sobald der entsprechende Aufruf erfolgreich gewesen ist. Weitere Informationen zu Aufrufen und Beispielen für deren Payloads finden Sie im Dokument [Aufrufe im universellen Editor](/help/implementing/universal-editor/calls.md).

## Ereignisse zur Inhaltsaktualisierung {#content-events}

### aue:content-add {#content-add}

Das Ereignis `aue:content-add` wird ausgelöst, wenn einem Container eine neue Komponente hinzugefügt wird.

Die Payload sind Inhalte vom universellen Editor-Dienst mit Fallback-Inhalten aus der Komponentendefinition.

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

Das Ereignis `aue:content-details` wird ausgelöst, wenn eine Komponente im Bedienfeld „Eigenschaften“ geladen wird.

Die Payload ist der Inhalt der Komponente sowie optional ihr Schema.

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

Das Ereignis `aue:content-move` wird ausgelöst, wenn eine Komponente verschoben wird.

Die Payload ist die Komponente sowie der Quell- und Ziel-Container.

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

Das Ereignis `aue:content-patch` wird ausgelöst, wenn die Daten einer Komponente im Bedienfeld „Eigenschaften“ aktualisiert werden.

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

Das Ereignis `aue:content-remove` wird ausgelöst, wenn eine Komponente aus einem Container entfernt wird.

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

Das Ereignis `aue:content-update` wird ausgelöst, wenn die Eigenschaften einer Komponente im Kontext aktualisiert werden.

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

Bei allen Ereignissen zur Inhaltsaktualisierung werden die angeforderte Payload sowie die Antwort-Payload an das Ereignis übergeben. Bei einem Aktualisierungsaufruf sieht dies beispielsweise wie folgt aus.

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

Antwort-Payload:

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

### aue:ui-preview {#ui-preview}

Das Ereignis `aue:ui-preview` wird ausgelöst, wenn der Bearbeitungsmodus der Seite in **Vorschau** geändert wird.

Die Payload für dieses Ereignis ist leer.

```json
{
    details: {}
}
```

### aue:ui-edit {#ui-edit}

Das Ereignis `aue:ui-edit` wird ausgelöst, wenn der Bearbeitungsmodus der Seite in **Bearbeiten** geändert wird.

Die Payload für dieses Ereignis ist leer.

```json
{
    details: {}
}
```

### aue:ui-viewport-change {#ui-viewport-change}

Das Ereignis `aue:ui-viewport-change` wird ausgelöst, wenn die Viewport-Größe geändert wird.

Die Payload sind die Dimensionen des Viewports.

```json
{
    details: {
        height: number?;        // height of the viewport. Undefined when fullscreen
        width: number?;         // width of the viewport. Undefined when fullscreen
    }
}
```

### aue:initialized {#initialized}

Das Ereignis `aue:initialized` wird ausgelöst, um der Remote-Seite mitzuteilen, dass sie erfolgreich im universellen Editor geladen wurde.

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
| `aue:content-add` | Neuladen der Seite |
| `aue:content-details` | Nichts |
| `aue:content-move` | Verschieben der Inhalte/Struktur der Komponente in den Zielbereich |
| `aue:content-patch` | Neuladen der Seite |
| `aue:content-remove` | Entfernen des DOM-Elements |
| `aue:content-update` | Aktualisieren der `innerHTML` mit der Payload |

### Benutzeroberflächen-Ereignisse {#ui-event-fallbacks}

| Ereignis | Verhalten |
|---|---|
| `aue:ui-select` | Scrollen zum ausgewählten Element |
| `aue:ui-preview` | Hinzufügen von `class="adobe-ue-preview"` zum HTML-Tag |
| `aue:ui-edit` | Hinzufügen von `class=adobe-ue-edit"` zum HTML-Tag |
| `aue:ui-viewport-change` | Nichts |
| `aue:initialized` | Nichts |

## Zusätzliche Ressourcen {#additional-resources}

* [Aufrufe im universellen Editor](/help/implementing/universal-editor/calls.md)

