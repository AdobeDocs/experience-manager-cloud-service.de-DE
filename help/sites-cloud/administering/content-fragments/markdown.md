---
title: Markdown
description: Erfahren Sie, wie der Inhaltsfragment-Editor die Markdown-Syntax verwendet, um Ihnen die einfache Erstellung von Inhalten für die Seitenbearbeitung und die Headless-Bereitstellung zu ermöglichen.
feature: Content Fragments
role: User
exl-id: 6fbf8128-3b7f-4eda-bbbd-3336578d2586
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: ht
source-wordcount: '561'
ht-degree: 100%

---

# Markdown {#markdown}

Beim [Bearbeiten](/help/sites-cloud/administering/content-fragments/authoring.md#edit-multi-line-text-fields-plaintext-markdown) Ihrer Inhaltsfragmente haben Sie möglicherweise [mehrzeilige Textfelder](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types) mit **Markdown** als dem **Standardtyp** definiert. Der Inhaltsfragmenteditor verwendet eine *Markdown*-Syntax, mit der Sie Inhalte für die Seitenbearbeitung und die Headless-Bereitstellung einfach erstellen können:

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

Zum Erstellen einer Kopfzeile durch Platzieren eines Hashtags (#) vor der Überschrift. Ein Hashtag (#) wird für eine H1 verwendet, zwei Hashtags (##) für eine H2 usw. Sie können bis zu 6 Hashtags verwenden. Zum Beispiel:

    `## This is an H2`

    `### This is an H3`

    `###### This is a H6`

Optional können Sie eine Ü1 erstellen, indem Sie den Text mit Gleichheitszeichen unterstreichen, und eine Ü2, indem Sie den Text mit Minuszeichen unterstreichen. Zum Beispiel:

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

Sie können Text zitieren, indem Sie das Symbol > vor dem Text einfügen. Zum Beispiel:

    `>This is block quotes`

    `>asdhfjlkasdhlf`

    `>asdfahsdlfasdfj`

Sie können verschachtelte Blockzitate nutzen. Zum Beispiel:

    `> This is the first level of quoting.`

    `>`

        `>> This is nested blockquote.`

    `>`

    `> Back to the first level.`

## Listen {#lists}

Sie können sowohl sortierte als auch unsortierte Listen erstellen

Um eine unsortierte Liste zu erstellen, verwenden Sie das Symbol „*“ vor den Elementen in der Liste. Zum Beispiel:

    `* item in list`

    `* item in list`

    `* item in list`

Um eine sortierte Liste zu erstellen, fügen Sie vor jedem Element in der Liste die Nummer und danach einen Punkt hinzu. Zum Beispiel:

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

Um einen Codebereich anzugeben, schließen Sie ihn in einfache Anführungszeichen (&#39;) ein. Im Gegensatz zu vorformatierten Code-Blöcken zeigt ein Code-Bereich Code innerhalb eines normalen Absatzes an.

Zum Beispiel:

    ``Use the `printf()` function.``

## Code-Blöcke {#code-blocks}

Code-Blöcke werden in der Regel verwendet, um den Quell-Code zu veranschaulichen. Sie können Codeblöcke durch Einrücken des Codes mit Tabulator oder mindestens 4 Leerzeichen erstellen. Zum Beispiel:

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
