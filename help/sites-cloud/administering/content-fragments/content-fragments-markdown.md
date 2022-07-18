---
title: Markdown
description: Erfahren Sie, wie der Inhaltsfragment-Editor die Markdown-Syntax verwendet, um Ihnen die einfache Erstellung von Inhalten für die Seitenbearbeitung und die Headless-Bereitstellung zu ermöglichen.
exl-id: 4e9b076e-7429-466b-bb53-2164da379650
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 91%

---

# Markdown {#markdown}

Wann Sie [Authoring](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#authoring-your-content)verwendet der Inhaltsfragment-Editor *Markdown* -Syntax verwenden, damit Sie mühelos Inhalte für die Seitenbearbeitung und die Headless-Bereitstellung schreiben können:

![Markdown-Editor](/help/sites-cloud/administering/content-fragments/assets/cfm-markdown-01.png)

Sie können Folgendes definieren:

* [Überschriftsnotation](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#heading-notation)
* [Absätze und Zeilenumbrüche](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#paragraphs-and-line-breaks)
* [Links](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#links)
* [Bilder](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#images)
* [Blockzitate](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#block-quotes)
* [Listen](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#lists)
* [Hervorhebungen](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#emphasis)
* [Code-Blöcke](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#code-blocks)
* [Umgekehrter Schrägstrich als Escape-Zeichen](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md#backslash-escapes)

## Überschriftsnotation {#heading-notation}

Zum Erstellen einer Kopfzeile durch Platzieren eines Rautezeichens (#) vor der Überschrift. Ein Rautezeichen (#) wird für Ü1, zwei Rautezeichen (# #) werden für Ü2 usw. verwendet. Sie können bis zu 6 Rautezeichen verwenden. Beispiel:

    `## This is an H2`

    `### This is an H3`

    `###### This is a H6`

Optional können Sie eine Ü1 erstellen, indem Sie den Text mit Gleichheitszeichen unterstreichen, und eine Ü2, indem Sie den Text mit Minuszeichen unterstreichen. Beispiel:

    `This is an H1`

    `=============`

    `This is an H2`

    `-------------`

## Absätze und Zeilenumbrüche {#paragraphs-and-line-breaks}

Bei einem Absatz handelt es sich einfach um eine oder mehrere aufeinander folgende Textzeilen, durch eine oder mehrere leere Zeilen getrennt. Eine leere Zeile ist eine Zeile, die nur Leerzeichen oder Tabulatoren enthält. Normale Absätze sollten nicht mit Leerzeichen oder Tabulatoren eingerückt werden.

Ein Zeilenumbruch wird durch Beenden einer Zeile mit zwei oder mehr Leerzeichen und Zeilenschalter erstellt.

## Links {#links}

Sie können eingebundene und Verweis-Links erstellen.

In beiden Formaten wird der Link-Text durch eckige Klammern `[]` abgetrennt.

Dies sind Beispiele für eingebundene Links:

    `This is [an example](https://example.com/ "Title") inline link.`

    `This is [an example of an email link](emailto:myaddress@mydomain.info)`

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

Sie können Text zitieren, indem Sie das Symbol > vor dem Text hinzufügen. Beispiel:

    `>This is block quotes`

    `>asdhfjlkasdhlf`

    `>asdfahsdlfasdfj`

Sie können verschachtelte Blockzitate nutzen. Beispiel:

    `> This is the first level of quoting.`

    `>`

        `>> This is nested blockquote.`

    `>`

    `> Back to the first level.`

## Listen {#lists}

Sie können sowohl sortierte als auch unsortierte Listen erstellen

Um eine unsortierte Liste zu erstellen, verwenden Sie das Symbol „&amp;ast;“ vor den Elementen in der Liste. Beispiel:

    `* item in list`

    `* item in list`

    `* item in list`

Um eine sortierte Liste zu erstellen, fügen Sie die Nummern, gefolgt von einem Punkt, vor jedem Element in der Liste hinzu. Beispiel:

    `1. First item in list.`

    `2. Second item in list.`

    `3. Third item in list.`

## Hervorhebungen {#emphasis}

Sie können den Text kursiv oder fett formatieren.

Sie können Text wie folgt kursiv formatieren:

    `*single asterisks*`

    `_single underscores_`

    `Keyboard shortcut: Ctrl-I (Cmd-I)`

Sie können Text wie folgt fett formatieren:

    `**double asterisks**`

    `__double underscores__`

    `Keyboard shortcut: Ctrl-B (Cmd-B)`

Um einen Codebereich anzugeben, schließen Sie ihn in einfache Anführungszeichen (&#39;) ein. Anders als ein vorformatierten Codeblock zeigt ein Codebereich Code in einem normal Absatz an.

Beispiel:

    ``Use the `printf()` function.``

## Code-Blöcke {#code-blocks}

Code-Blöcke werden in der Regel verwendet, um den Quell-Code zu veranschaulichen. Sie können Codeblöcke durch Einrücken des Codes mit Tabulator oder mindestens 4 Leerzeichen erstellen. Beispiel:

    `This is a normal paragraph.`

        `This is a code block.`

## Umgekehrter Schrägstrich als Escape-Zeichen {#backslash-escapes}

Sie können umgekehrte Schrägstriche als Escape-Zeichen verwenden, um tatsächliche Zeichen zu erzeugen, die eine besondere Bedeutung in der Formatierungssyntax haben. Wenn Sie zum Beispiel ein Wort mit tatsächlichen Sternchen umgeben wollten (anstelle eines &lt;em>-HTML-Tags), können Sie umgekehrte Schrägstriche vor den Sternchen wie folgt verwenden:

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
