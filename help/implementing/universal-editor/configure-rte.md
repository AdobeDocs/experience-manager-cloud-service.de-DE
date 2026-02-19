---
title: Konfigurieren des RTE für den universellen Editor
description: Erfahren Sie, wie Sie den Rich-Text-Editor (RTE) im universellen Editor konfigurieren können.
feature: Developing
role: Admin, Developer
exl-id: 350eab0a-f5bc-49c0-8e4d-4a36a12030a1
source-git-commit: 39137052e9fa409f7f5494be53fa7693aaa60b17
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 1%

---

# Konfigurieren des RTE für den universellen Editor {#configure-rte}

Erfahren Sie, wie Sie den Rich-Text-Editor (RTE) im universellen Editor konfigurieren können.

## Überblick {#overview}

Der universelle Editor bietet sowohl im Kontext als auch im Eigenschaftenbereich einen Rich-Text-Editor (RTE), mit dem Autoren Formatierungsänderungen anwenden können, wenn sie ihren Text bearbeiten.

Dieser RTE kann mithilfe von [Komponentenfiltern konfiguriert werden.](/help/implementing/universal-editor/filtering.md) In diesem Dokument wird beschrieben, welche Konfigurationsoptionen zusammen mit Beispielen verfügbar sind.

>[!NOTE]
>
>Wenn Sie ein universelles Editor-Projekt starten, sind alle Rich-Text-Funktionen, die Ihr Backend unterstützt (AEM mit Edge Delivery- oder Headless-Implementierung), automatisch aktiv.
>
>* Sie können die Optionen deaktivieren, die Sie nicht benötigen.
>* Das Aktivieren von Optionen, die nicht mit Ihrem Projekttyp kompatibel sind, wird nicht unterstützt.

## Konfigurationsstruktur {#structure}

Die RTE-Konfiguration besteht aus zwei Teilen:

* [`toolbar`](#toolbar): Die Symbolleistenkonfiguration steuert, welche Bearbeitungsoptionen in der Benutzeroberfläche verfügbar sind und wie sie organisiert sind.
* [`actions`](#actions): Die Aktionskonfiguration ermöglicht es Ihnen, das Verhalten und das Erscheinungsbild einzelner Bearbeitungsaktionen anzupassen.

Diese Konfigurationen können als Teil eines [Komponentenfilters“ mit ](/help/implementing/universal-editor/filtering.md) Eigenschaft `rte` definiert werden.

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

## Aktionskonfiguration {#action}

Die Aktionskonfiguration ermöglicht es Ihnen, das Verhalten und das Erscheinungsbild einzelner Bearbeitungsaktionen anzupassen. Dies sind die verfügbaren Abschnitte.

### Allgemeine Aktionsoptionen {#common-action-options}

Die meisten Aktionen unterstützen die folgenden allgemeinen Optionen:

* `shortcut?`: Zeichenfolge - Überschreibt den standardmäßigen Tastaturbefehl für die Aktion (falls vorhanden)
* `label?`: Zeichenfolge - Überschreibt die für die Aktion in der Benutzeroberfläche verwendete Beschriftung
* `hideInline?`: Boolescher Wert - Blendet diese Aktion `true` aus der kontextbezogenen (Inline-)RTE-Editor-Symbolleiste aus.

```json
{
  "actions": {
    "bold": {
      "label": "Bold",
      "shortcut": "Mod-B",
      "hideInline": true
    }
  }
}
```

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

### Tabellenaktionen {#table-actions}

Tabellenaktionen unterstützen den Inhaltsumbruch zur Steuerung der HTML-Struktur in Tabellenzellen:

```json
{
  "actions": {
    "table": {
      "wrapInParagraphs": false, // <td>content</td> (default)
      "shortcut": "Mod-Alt-T",   // Custom shortcut
      "label": "Insert Table"    // Custom label
    }
  }
}
```

#### Tabellenkonfigurationsoptionen {#table-configuration-options}

* `wrapInParagraphs`: `false` (Standard) - Tabellenzellen enthalten nicht umschlossenen Textinhalt
* `wrapInParagraphs`: `true` - Tabellenzellen umschließen Inhalt in Absatz-Tags

Beispiele:

Wenn `wrapInParagraphs`: `false`:

```html
<!-- Single line -->
<td>Cell content</td>

<!-- Multiple paragraphs get <br> separation -->
<td>Line 1<br />Line 2</td>
```

Wenn `wrapInParagraphs`: `true`:

```html
<!-- Single paragraph -->
<td><p>Cell content</p></td>

<!-- Multiple paragraphs preserved -->
<td>
  <p>Line 1</p>
  <p>Line 2</p>
</td>
```

>[!NOTE]
>
>Beim Entpacken von Absätzen (`wrapInParagraphs`: `false`) fügt das Bereinigungsprogramm automatisch `<br>` Tags zwischen mehreren Absätzen ein, um visuelle Zeilenumbrüche beizubehalten. Dies folgt den HTML-Standards und gängigen Verfahren in allen gängigen Rich-Text-Editoren.

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

### Konfiguration der Einzüge {#indentation}

Einzüge verfügen über eine Konfiguration auf Funktionsebene, die den Umfang des Einrückungsverhaltens steuert, sowie über individuelle Aktionskonfigurationen für Tastaturbefehle und Beschriftungen.

```json
{
  "actions": {
    // Feature-level configuration
    "indentation": {
      "scope": "all"  // Controls what content can be indented (default: "all")
    },

    // Individual action configurations
    "indent": {
      "shortcut": "Tab",           // Custom keyboard shortcut
      "label": "Increase Indent"   // Custom button label
    },
    "outdent": {
      "shortcut": "Shift-Tab",     // Custom keyboard shortcut
      "label": "Decrease Indent"   // Custom button label
    }
  }
}
```

#### Optionen für Einzugsumfang {#indentation-options}

* `scope`: `all` (Standard) - Einzug/Auszug gilt für alle Inhalte:
   * Listen: Verschachtelte/verschachtelte Listenelemente
   * Absätze und Überschriften: Erhöhen/Verringern der allgemeinen Einrückung
* `scope`: `lists` - Einzug/Auszug gilt nur für Listenelemente:
   * Listen: Verschachtelte/verschachtelte Listenelemente
   * Absätze und Überschriften: Keine Einrückung (Schaltflächen für diese deaktiviert)

>[!NOTE]
>
>Die Verschachtelung von Listen über die Tabulatortaste/Umschalt+Tabulatortaste funktioniert unabhängig von den allgemeinen Einzugseinstellungen.

### Als Text einfügen {#paste-as-text}

Die `paste_text`-Editor-Aktion ermöglicht einen standardmäßigen Workflow zum Einfügen als reiner Text .

* **Standardbefehl:** Mod-Shift-V (Befehl+Umschalt+V unter macOS, Strg+Umschalt+V unter Windows/Linux)
* **Verhalten:** Einfügen aus Text/Nur (Quellformatierung wird ignoriert)
   * In Listen erstellen Zeilenumbrüche neue Listenelemente.

```json
{
  "toolbar": {
    "editor": ["removeformat", "paste_text"]
  },
  "actions": {
    "paste_text": {
      "shortcut": "Mod-Shift-v",
      "label": "Paste as Text"
    }
  }
}
```

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

### `wrapInPicture`{#wrapinpicture}

Die Option `wrapInPicture` für Bilder steuert die für Bildinhalte generierte HTML-Struktur.

#### wrapInPicture: false (Standard) {#wrapinpicture-false}

```html
<img src="image.jpg" alt="Description" />
```

#### wrapInPicture: true {#wrapinpicture-true}

```html
<picture>
  <img src="image.jpg" alt="Description" />
</picture>
```

Verwenden Sie `wrapInPicture: true` bei Bedarf:

* Unterstützung responsiver Bilder mit `<source>`.
* Möglichkeiten der künstlerischen Leitung.
* Zukunftssicherheit für erweiterte Bildfunktionen.
* Konsistente Bildelementstruktur.

>[!NOTE]
>
>Wenn `wrapInPicture: true` aktiviert ist, können Bilder mit zusätzlichen `<source>` für verschiedene Medienabfragen und Formate erweitert werden, wodurch sie flexibler für responsives Design sind.

### Optionen für Link-Zielgruppe {#link-target}

Die Option `hideTarget` für Links steuert, ob das Attribut `target` in generierten Links enthalten ist und ob das Dialogfeld für die Link-Erstellung ein Feld für die Zielauswahl enthält.

#### `hideTarget: false` (Standard) {#hideTarget-false}

```html
<a href="https://example.com" target="_self">Link text</a>
<a href="https://example.com" target="_blank">External link</a>
```

#### `hideTarget: true` {#hideTarget-true}

```html
<a href="https://example.com">Link text</a>
```

### Deaktivieren von Links auf Bildern {#disableforimages}

Die Option `disableForImages` für Links steuert, ob Benutzer Links auf Bildern und Bildelementen erstellen können. Dies gilt sowohl für Inline-`<img>` als auch für `<picture>` auf Blockebene.

#### `disableForImages: false` (Standard) {#disableforimages-false}

Benutzer können Bilder auswählen und sie in Links einschließen.

```html
<!-- Inline image with link -->
<a href="https://example.com">
  <img src="image.jpg" alt="Description" />
</a>

<!-- Block-level picture with link -->
<a href="https://example.com">
  <picture>
    <img src="image.jpg" alt="Description" />
  </picture>
</a>
```

#### disableForImages: true {#disableforimages-true}

Die Link-Schaltfläche ist deaktiviert, wenn ein Bild oder Bild ausgewählt wird. Benutzer können nur Links auf Textinhalten erstellen.

```html
<!-- Images remain standalone without links -->
<img src="image.jpg" alt="Description" />

<picture>
  <img src="image.jpg" alt="Description" />
</picture>

<!-- Links work normally on text -->
<a href="https://example.com">Link text</a>
```

Verwenden Sie `disableForImages: true`, wenn Sie Folgendes tun möchten:

* Wahrung der visuellen Konsistenz durch Verhinderung von verknüpften Bildern
* Vereinfachen Sie die Inhaltsstruktur, indem Sie Bilder von der Navigation trennen.
* Erzwingen von Inhaltsrichtlinien, die die Bildverknüpfung einschränken.
* Verringern Sie die Komplexität der Barrierefreiheit in Ihren Inhalten.

>[!NOTE]
>
>Diese Einstellung wirkt sich nur auf die Möglichkeit aus, neue Links auf Bildern zu erstellen. Vorhandene Links werden nicht aus Bildern im Inhalt entfernt.

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

## Nicht unterstützter HTML {#unsupported-html}

Unbekannte HTML-Tags werden standardmäßig entfernt, wenn sie vom Editor analysiert werden. Um sie beizubehalten, melden Sie sich über die `unsupportedHtml` an:

```javascript
const rteConfig = {
  unsupportedHtml: true, // preserve unknown HTML tags (default: false)
};
```

| Wert  | Verhalten |
|---|---|
| `false` (Standard) | Unbekannte HTML-Tags werden beim Analysieren entfernt. |
| `true` | Unbekannte HTML-Tags werden in einen benutzerdefinierten, nicht unterstützten Blockknoten eingeschlossen, damit Inhalte sicher umgeleitet werden können. |

Wenn diese Option aktiviert ist, rendert der Editor nicht unterstützte Knoten mit einer `rte-unsupported-block`. Consumer-Apps sollten den Stil für diese Klasse bereitstellen (z. B. Rahmen, Abstand, Hintergrund). Die Tag-Kennzeichnung innerhalb des Blocks verwendet `rte-unsupported-label`, die auch angepasst werden kann.
