---
title: Konfigurieren des RTE für den universellen Editor
description: Erfahren Sie, wie Sie den Rich-Text-Editor (RTE) im universellen Editor konfigurieren können.
feature: Developing
role: Admin, Developer
exl-id: 350eab0a-f5bc-49c0-8e4d-4a36a12030a1
source-git-commit: 0557379b8d70205043ed87e104d9576ed40a13ce
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 1%

---

# Konfigurieren des RTE für den universellen Editor {#configure-rte}

Erfahren Sie, wie Sie den Rich-Text-Editor (RTE) im universellen Editor konfigurieren können.

>[!NOTE]
>
>Diese Dokumentation bezieht sich auf den neuen RTE für den universellen Editor, der als Early-Adopter-Funktion verfügbar ist. Wenn Sie diese neue Funktion testen möchten, lesen [&#x200B; die Versionshinweise , um weitere Informationen zu erhalten.](/help/release-notes/universal-editor/current.md#new-rte)

## Überblick {#overview}

Der universelle Editor bietet sowohl im Kontext als auch im Eigenschaftenbereich einen Rich-Text-Editor (RTE), mit dem Autoren Formatierungsänderungen anwenden können, wenn sie ihren Text bearbeiten.

Dieser RTE kann mithilfe von [Komponentenfiltern konfiguriert werden.](/help/implementing/universal-editor/filtering.md) In diesem Dokument wird beschrieben, welche Konfigurationsoptionen zusammen mit Beispielen verfügbar sind.

## Konfigurationsstruktur {#structure}

Die RTE-Konfiguration besteht aus zwei Teilen:

* [`toolbar`](#toolbar): Die Symbolleistenkonfiguration steuert, welche Bearbeitungsoptionen in der Benutzeroberfläche verfügbar sind und wie sie organisiert sind.
* [`actions`](#actions): Die Aktionskonfiguration ermöglicht es Ihnen, das Verhalten und das Erscheinungsbild einzelner Bearbeitungsaktionen anzupassen.

Diese Konfigurationen können als Teil eines [Komponentenfilters“ mit &#x200B;](/help/implementing/universal-editor/filtering.md) Eigenschaft `rte` definiert werden.

```json
[
  {
    "id": "richtext",
    "rte": {
      "toolbar": {
        // Toolbar configuration
      },
      "actions": {
        // Action-specific configurations
      }
    },
    "components": [
      "richtext"
    ]
  }
]
```

## Symbolleistenkonfiguration {#toolbar}

Die Konfiguration der Symbolleiste steuert, welche Bearbeitungsoptionen in der Benutzeroberfläche verfügbar sind und wie sie organisiert sind. Dies sind die verfügbaren Abschnitte

```json
{
  "toolbar": {
    // Text formatting options
    "format": ["bold", "italic", "underline", "strike"],
    // Text alignment options
    "alignment": ["left", "center", "right", "justify"],
    // Text direction options, right-to-left or left-to-right
    "direction": ["rtl", "ltr"],
    // Indentation controls
    "indentation": ["indent", "outdent"],
    // Block-level elements
    "blocks": ["paragraph", "h1", "h2", "h3", "h4", "h5", "h6", "code_block"],
    // List options
    "list": ["bullet_list", "ordered_list"],
    // Content insertion
    "insert": ["link", "unlink", "image"],
    // Superscript/subscript
    "sr_script": ["superscript", "subscript"],
    // Editor utilities
    "editor": ["removeformat"],
    // Section ordering (optional)
    "sections": ["format", "alignment", "list"]
  }
}
```

## Konfiguration von Aktionen {#actions}

Die Aktionskonfiguration ermöglicht es Ihnen, das Verhalten und das Erscheinungsbild einzelner Bearbeitungsaktionen anzupassen. Dies sind die verfügbaren Abschnitte.

### Aktionen formatieren {#format}

Formatierungsaktionen werden verwendet, um Formatierungen anzuwenden und den Wechsel zwischen HTML-Tags zur Auswahl semantischer Varianten zu unterstützen. Die folgenden Abschnitte sind verfügbar.

```json
{
  "actions": {
    "bold": {
      "tag": "strong",      // Use <strong> instead of <b>
      "shortcut": "Mod-B",  // Custom keyboard shortcut
      "label": "Make Bold"  // Custom button label 
    },
    "italic": {
      "tag": "em",          // Use <em> instead of <i>
      "shortcut": "Mod-I",
      "label": "Italicize"
    },
    "strike": {
      "tag": "del"          // Use <del> instead of <s>
    }
  }
}
```

### Aktionen auflisten {#list}

Listenaktionen unterstützen den Inhaltsumbruch zur Steuerung der HTML-Struktur. Die folgenden Abschnitte sind verfügbar.

```json
{
  "actions": {
    "bullet_list": {
      "wrapInParagraphs": true,    // <ul><li><p>content</p></li></ul>
      "shortcut": "Mod-Shift-8",   // Custom shortcut
      "label": "Bullet List"       // Custom label
    },
    "ordered_list": {
      "wrapInParagraphs": false,   // <ol><li>content</li></ol> (default)
      "shortcut": "Mod-Shift-9"
    }
  }
}
```

### Aktionen verknüpfen {#link}

Link-Aktionen unterstützen die Steuerung der Zielattribute zur Verwaltung des Link-Verhaltens. Die folgenden Abschnitte sind verfügbar.

```json
{
  "actions": {
    "link": {
      "hideTarget": false,       // Show target attribute options (default)
      "shortcut": "Mod-K",       // Custom keyboard shortcut
      "label": "Insert Link"     // Custom button label
    },
    "unlink": {
      "shortcut": "Mod-Shift-K", // Custom keyboard shortcut
      "label": "Remove Link"     // Custom button label
    }
  }
}
```

#### Link-Konfigurationsoptionen {#link-options}

* `hideTarget`: `false` (Standard) - Zielattribut in Links einschließen, `_self`, `_blank` usw.
* `hideTarget`: `true` - Zielattribut vollständig von Links ausschließen

Die `unlink` Aktion wird nur angezeigt, wenn der Cursor in einem vorhandenen Link positioniert wird. Die Link-Formatierung wird entfernt, während der Textinhalt beibehalten wird.

### Bildaktionen {#image}

Bildaktionen unterstützen das Umbrechen von Bildelementen, um ein responsives Bild-Markup zu generieren. Die folgenden Abschnitte sind verfügbar.

```json
{
  "actions": {
    "image": {
      "wrapInPicture": false,     // Use <img> tag (default)
      "shortcut": "Mod-Shift-I",  // Custom keyboard shortcut
      "label": "Insert Image"     // Custom button label
    }
  }
}
```

#### Bildkonfigurationsoptionen {#image-options}

* `wrapInPicture`: `false` (Standard) - Generieren einfacher `<img>`
* `wrapInPicture`: `true` - Umschließen von Bildern in `<picture>` für responsives Design

### Sonstige Aktionen {#other}

Alle anderen Aktionen unterstützen grundlegende Anpassungen. Die folgenden Abschnitte sind verfügbar.

```json
{
  "actions": {
    "h1": {
      "shortcut": "Mod-Alt-1",
      "label": "Large Heading"
    },
    "paragraph": {
      "shortcut": "Mod-Alt-0",
      "label": "Normal Text"
    },
    "link": {
      "shortcut": "Mod-K",
      "label": "Insert Link",
      "hideTarget": false    // Show target attribute options (default: false)
    }
  }
}
```

## Vollständiges Beispiel {#example}

Im Folgenden finden Sie ein Beispiel für eine vollständige Konfiguration.

```json
[
  {
    "id": "richtext",
    "rte": {
      // Configure which tools appear in toolbar
      "toolbar": {
        "format": [
          "bold",
          "italic"
        ],
        "blocks": [
          "paragraph",
          "h1",
          "h2"
        ],
        "list": [
          "bullet_list",
          "ordered_list"
        ],
        "insert": [
          "link",
          "unlink"
        ],
        "sections": [
          "format",
          "blocks",
          "list",
          "insert"
        ]
      },
      // Customize individual action behavior
      "actions": {
        // Format actions with HTML tag choices
        "bold": {
          "tag": "strong",
          "shortcut": "Mod-B",
          "label": "Bold"
        },
        "italic": {
          "tag": "em",
          "shortcut": "Mod-I"
        },
        // List actions with content wrapping
        "bullet_list": {
          "wrapInParagraphs": true,
          "label": "Bullet List"
        },
        "ordered_list": {
          "wrapInParagraphs": false
        },
        // Link actions with target control
        "link": {
          "hideTarget": false,
          "shortcut": "Mod-K",
          "label": "Add Link"
        },
        "unlink": {
          "label": "Remove Link"
        },
        // Other actions with basic customization
        "h1": {
          "shortcut": "Mod-Alt-1",
          "label": "Main Heading"
        }
      }
    }
  }
]
```

## Details zur Aktionsoption {#action-details}

Mehrere Optionen bieten zusätzliche Details, die Sie beachten sollten.

### `wrapInParagraphs` {#wrapInParagraphs}

Die `wrapInParagraphs` für Listen steuert die HTML-Struktur.

#### `wrapInParagraphs: false` (Standard) {#wrapInParagraphs-false}

```html
<ul>
  <li>Simple text content</li>
  <li>Another item</li>
</ul>
```

#### `wrapInParagraphs: true` {#wrapInParagraphs-true}

```html
<ul>
  <li><p>Text wrapped in paragraphs</p></li>
  <li><p>Supports rich formatting within items</p></li>
</ul>
```

Verwenden Sie `wrapInParagraphs: true` bei Bedarf:

* Rich-Formatierung in Listenelementen
* Mehrere Absätze pro Listenelement
* Konsistente Formatierung auf Blockebene

### Optionen für Link-Zielgruppe {#link-target}

Die Option `hideTarget` für Links steuert, ob das Attribut `target` in generierten Links enthalten ist und ob das Dialogfeld für die Link-Erstellung ein Feld für die Zielauswahl enthält.

#### `hideTarget: false` (Standard) {#hideTarget-false}

```html
<a href="https://example.com" target="_self">Link text</a>
<a href="https://example.com" target="_blank">External link</a>
```

### `hideTarget: true` {#hideTarget-true}

```html
<a href="https://example.com">Link text</a>
```

### Tag-Optionen {#tag}

Formataktionen ermöglichen den Wechsel zwischen HTML-Varianten.

| Aktion | Standard-Tag | Alternative Tags | Anwendungsfall |
|---|---|---|---|
| `bold` | `<strong>` | `<b>` | Semantische vs. visuelle Hervorhebung |
| `italic` | `<em>` | `<i>` | Semantischer vs. visueller Stil |
| `strike` | `<del>` | `<s>` | Visuelles vs. semantisches Löschen |

Wählen Sie semantische Tags (`<strong>`, `<em>`, `<del>`) für bessere Barrierefreiheit und SEO.

### Tastaturbefehle {#keyboard-shortcuts}

Bei den Tastaturbefehlen wird/werden das Format `Mod-Key`(en) verwendet, wobei:

* `Mod` = `Cmd` unter Mac, `Ctrl` unter Windows/Linux
* Beispiele: `Mod-B`, `Mod-Shift-8`, `Mod-Alt-1`
