---
title: Markdown
description: Erfahren Sie, wie der Inhaltsfragment-Editor die Markdown-Syntax verwendet, um Ihnen die einfache Erstellung von Inhalten für die Seitenbearbeitung und die Headless-Bereitstellung zu ermöglichen.
feature: Content Fragments
role: User
exl-id: 6fbf8128-3b7f-4eda-bbbd-3336578d2586
solution: Experience Manager Sites
source-git-commit: be60f0371e652549cec6e57d1449b6e07b996514
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 77%

---

# Markdown {#markdown}

Beim [&#x200B; (Authoring](/help/sites-cloud/administering/content-fragments/authoring.md#edit-multi-line-text-fields-plaintext-markdown) von Inhaltsfragmenten [&#x200B; möglicherweise (mehrzeilige Textfelder](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types) mit dem **Standardtyp** von **Markdown** definiert. Der Inhaltsfragmenteditor verwendet eine *Markdown*-Syntax, mit der Sie Inhalte für die Seitenbearbeitung und die Headless-Bereitstellung einfach erstellen können:

![Mehrzeiliges Markdown-Textfeld im Editor](/help/sites-cloud/administering/content-fragments/assets/cf-markdown-field-edit.png)

Sie können Folgendes definieren:

* [Überschriftsnotation](/help/sites-cloud/administering/content-fragments/markdown.md#heading-notation)
* [Absätze und Zeilenumbrüche](/help/sites-cloud/administering/content-fragments/markdown.md#paragraphs-and-line-breaks)
* [Links](/help/sites-cloud/administering/content-fragments/markdown.md#links)
* [Bilder](/help/sites-cloud/administering/content-fragments/markdown.md#images)
* [Blockzitate](/help/sites-cloud/administering/content-fragments/markdown.md#block-quotes)
* [Listen](/help/sites-cloud/administering/content-fragments/markdown.md#lists)
* [Hervorhebungen](/help/sites-cloud/administering/content-fragments/markdown.md#emphasis)
* [Code-Blöcke](/help/sites-cloud/administering/content-fragments/markdown.md#code-blocks)
* [Umgekehrter Schrägstrich als Escape-Zeichen](/help/sites-cloud/administering/content-fragments/markdown.md#backslash-escapes)

## Überschriftsnotation {#heading-notation}

Um eine Kopfzeile zu erstellen, platzieren Sie ein Hash-Symbol (#) vor der Überschrift. Ein Hash-Symbol (#) gibt einen H1-Wert an, zwei Hash-Symbole (##) einen H2-Wert usw. Sie können bis zu sechs Hash-Symbole verwenden. Beispiel:

    `## This is an H2`

    `### This is an H3`

    `###### This is a H6`

Optional können Sie eine Ü1 erstellen, indem Sie den Text mit Gleichheitszeichen unterstreichen, und eine Ü2, indem Sie den Text mit Minuszeichen unterstreichen. Beispiel:

    `This is an H1`

    `=============`

    `This is an H2`

    `-------------`

## Absätze und Zeilenumbrüche {#paragraphs-and-line-breaks}

Ein Absatz ist einfach eine oder mehrere aufeinander folgende Textzeilen, die durch eine oder mehrere leere Zeilen getrennt sind. Eine leere Zeile ist eine Zeile, die höchstens Leerzeichen oder Tabulatoren enthält. Normale Absätze sollten nicht mit Leerzeichen oder Tabulatoren eingerückt werden.

Ein Zeilenumbruch wird durch Beenden einer Zeile mit zwei oder mehr Leerzeichen und Zeilenschalter erstellt.

## Links {#links}

Sie können eingebundene und Verweis-Links erstellen.

In beiden Formaten wird der Link-Text durch eckige Klammern `[]` abgetrennt.

Dies sind Beispiele für eingebundene Links:

    `This is [an example](https://example.com/ "Title") inline link.`

    `This is [an example (non-standard) of an email link](emailto:myaddress@mydomain.info)`

    `[This link](https://example.net/) has no title attribute.`

Ein Verweis-Link weist die folgende Syntax auf:

    `Hey you should [checkout][0] this [cool thing][wiki] that I [made][].`

    `[0]: https://www.google.ca`

    `[wiki]: https://www.wikipedia.org`

    `[made]: https://www.stackoverflow.com`

## Bilder {#images}

Die Syntax für Bilder ist der von Links ähnlich. Sie können eingebundene und referenzierte Bilder erstellen.

Ein eingebundenes Bild hat zum Beispiel die folgende Syntax:

    `![Alt text](/path/to/img.jpg)`

    `![Alt text](/path/to/img.jpg "Optional title")`

Die Syntax enthält:

* Ein Ausrufezeichen: !;
* gefolgt von einem Satz eckiger Klammern, die den alt-Attributtext für das Bild enthalten;
* gefolgt von einem Satz Klammern, die die URL oder den Pfad zum Bild enthalten, und einem optionalen title-Attribut, das in doppelten oder einfachen Anführungszeichen eingeschlossen ist.

Ein referenziertes Bild weist die folgende Syntax auf:

    `![Alt text][id]`

Wobei „id“ der Name eines definierten Bildverweises ist. Bildverweise werden mithilfe der Syntax definiert, die mit den Link-Verweisen identisch ist:

    `[id]: url/to/image "Optional title attribute"`

## Blockzitate {#block-quotes}

Sie können Text zitieren, indem Sie das Symbol > vor dem Text einfügen. Beispiel:

    `>This is block quotes`

Sie können verschachtelte Blockzitate nutzen. Beispiel:

    `> This is the first level of quoting.`

    `>`

        `>> This is a nested blockquote.`

    `>`

    `> Back to the first level.`

## Listen {#lists}

Sie können sowohl sortierte als auch unsortierte Listen erstellen

Um eine ungeordnete Liste zu erstellen, verwenden Sie das Symbol &quot;*&quot; (*) vor den Elementen in der Liste. Beispiel:

    `* item in list`

    `* item in list`

    `* item in list`

Um eine sortierte Liste zu erstellen, fügen Sie vor jedem Element in der Liste die Nummer und danach einen Punkt hinzu. Beispiel:

    `1. First item in list.`

    `2. Second item in list.`

    `3. Third item in list.`

## Hervorhebungen {#emphasis}

Sie können den Text kursiv oder fett formatieren.

Sie können wie folgt Kursiv hinzufügen:

    `*single asterisks*`

    `_single underscores_`

    `Keyboard shortcut: Ctrl-I (Cmd-I)`

Sie können Text wie folgt fett formatieren:

    `**double asterisks**`

    `__double underscores__`

    `Keyboard shortcut: Ctrl-B (Cmd-B)`

Um einen Codebereich anzugeben, schließen Sie ihn in einfache Anführungszeichen (&#39;) ein. Im Gegensatz zu vorformatierten Code-Blöcken zeigt ein Code-Bereich Code innerhalb eines normalen Absatzes an.

Beispiel:

    ``Use the `printf()` function.``

## Code-Blöcke {#code-blocks}

Code-Blöcke werden in der Regel verwendet, um den Quell-Code zu veranschaulichen. Sie können Codeblöcke durch Einrücken des Codes mit Tabulator oder mindestens 4 Leerzeichen erstellen. Beispiel:

    `This is a normal paragraph.`

        `This is a code block.`

## Umgekehrter Schrägstrich als Escape-Zeichen {#backslash-escapes}

Sie können umgekehrte Schrägstriche verwenden, um Literalzeichen zu generieren, die auch in der Formatierungssyntax eine besondere Bedeutung haben. Wenn Sie beispielsweise ein Wort mit literalen Sternchen (anstelle eines HTML &lt;em>-Tags) umgeben möchten, können Sie vor den Sternchen umgekehrte Schrägstriche wie den folgenden verwenden:

    `\\*literal asterisks\\*`

Umgekehrte Schrägstriche als Escape-Zeichen sind für die folgenden Zeichen verfügbar:

    ` \ backslash`

    `` ` backtick``

    ` * asterisk`

    ` _ underscore`

    ` {} curly braces`

    ` [] square brackets`

    ` () parentheses`

    ` # hash mark`

    ` + plus sign`

    ` - minus sign (hyphen)`

    ` . dot`
