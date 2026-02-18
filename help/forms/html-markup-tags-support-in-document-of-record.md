---
title: Unterstützte HTML-Markup-Tags in Submission PDF (ehemals Document of Record)
description: Referenzhandbuch für HTML-Markup-Tags, die beim Generieren einer Übermittlungs-PDF (ehemals Datensatzdokument) unterstützt werden, einschließlich Überlegungen zum Rendering-Verhalten und zur Barrierefreiheit.
feature: Adaptive Forms
role: Developer, User
exl-id: 8481b0dc-aae7-4bd2-acfe-1f1b6d747683
source-git-commit: 0b112a5a1830fac9d0170771e052bbb2ef3cadbf
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 7%

---


# Unterstützte HTML-Markup-Tags in Submission PDF (ehemals Document of Record)

## Was wird in dieser Referenz behandelt?

AEM Forms unterstützt jetzt HTML-Markup-Tags in Rich-Text-Feldern beim Generieren einer PDF-PDF für die Übermittlung (ehemals Datensatzdokument). In diesem Handbuch wird erläutert, welche HTML-Markup-Tags Sie sicher in adaptiven Forms verwenden können und wie sie in der generierten Übermittlungs-PDF gerendert werden.

Wenn Sie Ihren Formularen Rich-Text-Inhalte (z. B. Fettformatierung, Listen oder Links) hinzufügen, ist es wichtig zu verstehen, welche Tags unterstützt werden und welche Einschränkungen sie möglicherweise haben. Mit dieser Referenz können Sie die entsprechenden Tags auswählen, um sicherzustellen, dass Ihr Inhalt korrekt angezeigt wird und in der Übermittlungs-PDF verfügbar bleibt.

## Bevor Sie beginnen

### Voraussetzungen

Sie sollten vertraut sein mit:

- Grundlegende Markup-Syntax in HTML
- [Grundlagen zur Übermittlung von PDF (ehemals Datensatzdokument)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
- Barrierefreiheitsprinzipien und WCAG-Richtlinien
- Barrierefreiheitsanforderungen für PDF
- Adaptive Formularkomponenten, die HTML-Markup akzeptieren

### Überlegungen

Die Übermittlungs-PDF (ehemals Document of Record) kann eine mit Tags versehene PDF sein, die die Barrierefreiheit und ordnungsgemäße Struktur für Hilfstechnologien sicherstellt. Um die Ausgabe mit Tags in PDF zu aktivieren[&#x200B; setzen Sie die XCI-Eigenschaft `config/present/pdf/tagged` auf `true`](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). Nachdem Sie Ihre PDF generiert haben, müssen Sie sicherstellen, dass Barrierefreiheits-Tags korrekt angewendet werden. Sie können [Adobe Acrobat verwenden, um Barrierefreiheits-Tags zu &#x200B;](https://helpx.adobe.com/in/acrobat/using/create-verify-pdf-accessibility.html) und sicherzustellen, dass Ihr Dokument den Barrierefreiheitsstandards entspricht.

### Neue Funktionen

Die Rich-Text-Unterstützung in Submission PDF wurde kürzlich verbessert. Zuvor wurden Rich-Text-Inhalte in generierten Dokumenten als Nur-Text-Inhalte angezeigt. Mit dieser neuen Funktion kann formatierter Inhalt in PDF-Ausgaben ordnungsgemäß gerendert werden.

## Referenz zur Tag-Unterstützung in HTML

### Vollständig unterstützte Tags

Diese Tags werden mit der ordnungsgemäßen Erstellung von Barrierefreiheits-Knoten vollständig unterstützt:

| HTML-Tag | Beschreibung | Unterstützung für Submission PDF | Barrierefreiheit | Beispiel |
|----------|-------------|-------------|---------------|---------|
| `<p>` | Absatz | Ja | Vollständig unterstützt - Korrigieren `<P>` Knoten | `<p>This is a paragraph.</p>` |
| `<br/>` | Zeilenumbruch | Ja | Vollständige Unterstützung - innerhalb `<P>` Knotens | `<p>Line 1<br/>Line 2</p>` |
| `<b>` | Fetter Text | Ja | Vollständige Unterstützung - innerhalb `<P>` Knotens | `<b>bold text</b>` |
| `<i>` | Kursiver Text | Ja | Vollständige Unterstützung - innerhalb `<P>` Knotens | `<i>italic text</i>` |
| `<span>` | Allgemeiner Inline-Container | Ja | Innerhalb von Blockelementen | `<span>styled text</span>` |
| `<sub>` | Tiefgestellt | Ja | Vollständig unterstützt - innerhalb von Blockelementen | `H<sub>2</sub>O` |
| `<sup>` | Hochgestellt | Ja | Vollständig unterstützt - Innerhalb von Blockelementen | `E=mc<sup>2</sup>` |
| `<a>` | Hyperlink | Ja | Eingeschränkter Support - erfordert eine ordnungsgemäße Verschachtelung | `<a href="url">link text</a>` |


#### Problem mit der Barrierefreiheit von Listen

Beim aktuellen Listen-Rendering werden `<P>` Knoten anstelle der richtigen Listenstruktur erstellt:

```
Current: <P>1. First item
Current: <P>2. Second item

Expected: <L>
Expected:   <LI>
Expected:     <LBL>1.
Expected:     <LBody>First item
```

### Nicht unterstützte Tags

Diese Tags werden nicht unterstützt und werden nicht ordnungsgemäß gerendert:

| HTML-Tag | Beschreibung | Alternativlösung |
|----------|-------------|---------------------|
| `<h1>`–`<h6>` | Überschriften-Tags | Verwenden von formatierten `<p>`-Tags oder Kopfzeilen auf Designebene |
| `<img>` | Bilder | Separate Bildfelder oder Design-Vorlagen verwenden |
| `<code>` | Code-Blöcke | Verwenden von Monospace-Schriftarten mit `<span>` |
| `<blockquote>` | Blocknotierungen | Verwenden formatierter `<p>` mit Einzug |
| `<table>` | Tabellen | Verwenden von Tabellenkomponenten adaptiver Formulare |

## Code-Beispiele

### Grundlegende Textformatierung

```html
<!--  Supported - renders correctly -->
<p>This paragraph contains <b>bold text</b> and <i>italic text</i>.</p>

<!--  Supported - combined formatting -->
<p>This text is <i><b>bold and italic</b></i>.</p>

<!--  Unsupported - headings don't work -->
<h1>This won't render as a heading</h1>
```

### Listen

```html
<!-- ⚠️ Partially supported - renders but not accessible -->
<ol>
  <li>First numbered item</li>
  <li>Second numbered item</li>
</ol>

<ul>
  <li>First bullet point</li>
  <li>Second bullet point</li>
</ul>
```

### Links

```html
<!--  Supported - but must be within block elements -->
<p>Visit our <a href="https://example.com">website</a> for more information.</p>

<!--  Incorrect - link not properly nested -->
<a href="https://example.com">Standalone link</a>
```

### wissenschaftliche Notation

```html
<!--  Supported - but limited accessibility -->
<p>Water formula: H<sub>2</sub>O</p>
<p>Einstein's equation: E=mc<sup>2</sup></p>
```

## Verwandte Inhalte


- [Generieren eines Übermittlungs-PDF (ehemals Datensatzdokument) für Adaptive Forms](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
- [Generieren einer Übermittlungs-PDF für Kernkomponenten](/help/forms/generate-document-of-record-core-components.md)
- [Anpassung der Übermittlungs-PDF-Vorlage](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record)

