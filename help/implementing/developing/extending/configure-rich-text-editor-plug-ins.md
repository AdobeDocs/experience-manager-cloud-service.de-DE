---
title: Configure the Rich Text Editor plug-ins in [!DNL Adobe Experience Manager].
description: Learn to configure the [!DNL Adobe Experience Manager] Rich Text Editor plug-ins.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 739dde6f9a6a7f4fe773e27e53f23a395f2881dc
workflow-type: tm+mt
source-wordcount: '4301'
ht-degree: 60%

---


# Konfigurieren der Rich-Text-Editor-Plug-ins {#configure-the-rich-text-editor-plug-ins}

RTE-Funktionen werden über eine Reihe von Plug-ins mit jeweils einer Eigenschaft „features“ bereitgestellt. Sie können die Eigenschaft „features“ so konfigurieren, dass eine oder mehrere RTE-Funktionen aktiviert oder deaktiviert werden. In diesem Artikel wird beschrieben, wie Sie die RTE-Plug-Ins spezifisch konfigurieren.

For details about the other RTE configurations, see [configure Rich Text Editor](/help/implementing/developing/extending/rich-text-editor.md).

>[!NOTE]
>
>When working with CRXDE Lite, it is recommended to save the changes regularly using [!UICONTROL Save All] option.

## Aktivieren von Plug-ins und Konfigurieren der Eigenschaft „features“{#activateplugin}

Gehen Sie wie folgt vor, um ein Plug-in zu aktivieren. Einige Schritte sind nur erforderlich, wenn Sie ein Plug-in zum ersten Mal konfigurieren, da die entsprechenden Knoten noch nicht vorhanden sind.

By default, `format`, `link`, `list`, `justify`, and `control` plug-ins and all their features are enabled in RTE.

>[!NOTE]
>
>The respective `rtePlugins` node is referred to as `<rtePlugins-node>` to avoid duplication in this article.

1. Suchen Sie mithilfe von CRXDE Lite nach der Textkomponente für Ihr Projekt.
1. Create the parent node of `<rtePlugins-node>` if it does not exist, before configuring any RTE plug-ins:

   * Abhängig von Ihrer Komponente sind die übergeordneten Knoten:

      * `config: .../text/cq:editConfig/cq:inplaceEditing/config`
      * ein alternativer Konfigurationsknoten: `.../text/cq:editConfig/cq:inplaceEditing/inplaceEditingTextConfig`
      * `text: .../text/dialog/items/tab1/items/text`
   * Are of type: **jcr:primaryType** `cq:Widget`
   * Beide verfügen über die folgende Eigenschaft:

      * **Name** `name`
      * **Typ** `String`
      * **Wert** `./text`


1. Depending on the interface you are configuring for, create a node `<rtePlugins-node>`, if it does not exist:

   * **Name** `rtePlugins`
   * **Typ** `nt:unstructured`

1. Erstellen Sie unten einen Knoten für jedes Plugin, das Sie aktivieren möchten:

   * **Typ** `nt:unstructured`
   * **Name:** die Plug-in-ID des erforderlichen Plug-ins

After activating a plug-in, follow these guidelines to configure the `features` property.

|  | Alle Funktionen aktivieren | Bestimmte Funktionen aktivieren. | Alle Funktionen deaktivieren. |
|---|---|---|---|
| Name | features | features | features |
| Typ | Zeichenfolge | `String` (mehrere Zeichenfolgen; &quot;Typ&quot;auf `String` und klicken Sie `Multi` in CRXDE Lite) | Zeichenfolge |
| Wert | `*` (ein Sternchen) | Legen Sie einen oder mehrere Funktionswerte fest. | - |

## Das findreplace-Plug-in {#findreplace}

The `findreplace` plug-in does not need any configuration. Es funktioniert aus der Schachtel.

Bei Verwendung der Funktion zum Ersetzen sollte die Zeichenfolge zum Ersetzen gleichzeitig mit der Suchzeichenfolge eingegeben werden. Sie können jedoch weiterhin auf „Suchen“ klicken, um nach der Zeichenfolge zu suchen, bevor Sie sie ersetzen. Wenn die Zeichenfolge zum Ersetzen eingegeben wird, nachdem auf „Suchen“ geklickt wurde, wird die Suche auf den Anfang des Textes zurückgesetzt.

Das Dialogfeld „Suchen und ersetzen“ wird transparent, wenn auf „Suchen“ geklickt wird, und undurchsichtig, wenn auf „Ersetzen“ geklickt wird. Das Verhalten ermöglicht es dem Autor, den zu ersetzenden Text zu überprüfen. Wenn der Benutzer auf „Alle ersetzen“ klickt, wird das Dialogfeld geschlossen und die Anzahl der vorgenommenen Ersetzungen angezeigt.

## Konfigurieren der Einfügemodi {#pastemodes}

Bei Verwendung des RTE können Autoren Inhalte in einem der drei folgenden Modi einfügen:

* **Browsermodus**: Fügen Sie Text mit der Standardfunktion des Browsers zum Einfügen ein. Dieses Verfahren wird nicht empfohlen, da es unerwünschte Markups verursachen kann.

* **Reiner Textmodus**: Fügen Sie Inhalte aus der Zwischenablage als Text ein. It strips all elements of style and formatting from the copied content before inserting in [!DNL Experience Manager] component.

* **Microsoft Word-Modus**: Fügen Sie beim Kopieren aus Microsoft Word Text, einschließlich Tabellen, mitsamt Formatierung ein. Das Kopieren und Einfügen von Text aus einer anderen Quelle wie einer Webseite oder Microsoft Excel wird nicht unterstützt und dabei wird nur ein Teil der Formatierung beibehalten.

### Konfigurieren der in der RTE-Symbolleiste verfügbaren Einfüge-Optionen  {#configure-paste-options-available-on-the-rte-toolbar}

Sie können Ihren Autoren in der RTE-Symbolleiste nur manche, alle oder keine dieser drei Symbole zur Verfügung stellen:

* **[!UICONTROL Einfügen (STRG+V)]**: Kann vorkonfiguriert werden, um einem der drei obigen Einfügemodi zu entsprechen.

* **[!UICONTROL Als Text]** einfügen: Bietet Funktionen im Textmodus.

* **[!UICONTROL Aus Word einfügen]**: Bietet die Funktionen des Microsoft Word-Modus.

Um die Anzeige der Symbole in RTE zu konfigurieren, führen Sie folgende Schritte aus.

1. Navigieren Sie zu Ihrer Komponente, z. B. `/apps/<myProject>/components/text`.
1. Navigate to the node `rtePlugins/edit`. Lesen Sie die Informationen unter [Aktivieren von Plug-ins](#activateplugin), falls noch kein Knoten vorhanden ist.
1. Erstellen Sie die Eigenschaft `features` auf dem Knoten `edit` und fügen Sie eine oder mehrere Funktionen hinzu. Speichern Sie alle Änderungen.

### Verhalten des Symbols bzw. der Tastenkombination „Einfügen (STRG+V)“ konfigurieren {#configure-the-behavior-of-the-paste-ctrl-v-icon-and-shortcut}

Sie können das Verhalten des Symbols **[!UICONTROL Einfügen (STRG+V)]** mit folgenden Schritten vorkonfigurieren. Diese Konfiguration definiert auch das Verhalten der Tastenkombination (STRG+V), mit der Autoren Inhalte einfügen können.

Die Konfiguration ermöglicht die drei folgenden Anwendungsfälle:

* Fügen Sie Text mit der Standardfunktion des Browsers zum Einfügen ein. Dieses Verfahren wird nicht empfohlen, da es unerwünschte Markups verursachen kann. Configured using `browser` below.

* Fügen Sie den Inhalt aus der Zwischenablage als Text ein. It strips all elements of style and formatting from the copied content before inserting in [!DNL Experience Manager] component. Configured using `plaintext` below.

* Fügen Sie den Text, einschließlich Tabellen, mit Formatierung beim Kopieren aus Microsoft Word ein. Das Kopieren und Einfügen von Text aus einer anderen Quelle wie einer Webseite oder Microsoft Excel wird nicht unterstützt und dabei wird nur ein Teil der Formatierung beibehalten. Configured using `wordhtml` below.

1. In your component, navigate to `<rtePlugins-node>/edit` node. Erstellen Sie die Knoten, wenn die Knoten nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Erstellen Sie im Knoten `edit` eine Eigenschaft mithilfe der folgenden Details:

   * **Name** `defaultPasteMode`
   * **Typ** `String`
   * **Der Wert** ist einer der erforderlichen Einfügemodi aus `browser`, `plaintext`oder `wordhtml` .

### Konfigurieren der beim Einfügen von Inhalten zulässigen Formate {#pasteformats}

Der Einfügemodus als Microsoft-Word (`paste-wordhtml`) kann weiter konfiguriert werden, sodass Sie beim Einfügen [!DNL Experience Manager] aus einem anderen Programm, wie z. B. [!DNL Microsoft Word], explizit einige Stile zulassen können.

For example, if only bold formats and lists should be allowed when pasting in [!DNL Experience Manager], you can filter out the other formats. Dies wird als konfigurierbare Paste-Filterung bezeichnet, die für beide Aufgaben durchgeführt werden kann:

* [Text](#pastemodes)
* [Links](#linkstyles)

Für Links können Sie zudem die Protokolle definieren, die automatisch akzeptiert werden.

To configure which formats are allowed when pasting text into [!DNL Experience Manager] from another program:

1. In your component, navigate to the node `<rtePlugins-node>/edit`. Erstellen Sie die Knoten, wenn der Knoten nicht vorhanden ist. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Erstellen Sie unter dem Knoten `edit` einen Knoten, unter dem die HTML-Einfügeregeln gespeichert werden sollen:

   * **Name** `htmlPasteRules`
   * **Typ** `nt:unstructured`

1. Erstellen Sie unter `htmlPasteRules` einen Knoten, unter dem die Details der zulässigen grundlegenden Formate gespeichert werden sollen:

   * **Name** `allowBasics`
   * **Typ** `nt:unstructured`

1. Erstellen Sie zur Steuerung der einzelnen akzeptierten Formate eine oder mehrere der folgenden Eigenschaften im Knoten `allowBasics`:

   * **Name** `bold`
   * **Name** `italic`
   * **Name** `underline`
   * **Name:** `anchor` (sowohl für Links als auch für benannte Anker)
   * **Name** `image`

   All properties are of **Type** `Boolean`, so in the appropriate **Value** you can either select or remove the check mark to enable or disable the functionality.

   >[!NOTE]
   >
   >Ist der Wert nicht explizit festgelegt, wird der Standardwert „true“ verwendet und das Format akzeptiert.

1. Es können mithilfe einer Reihe anderer Eigenschaften oder Knoten auch andere Formate auf den Knoten `htmlPasteRules` angewendet werden:

| Eigenschaft | Typ | Beschreibung |
|--- |--- |--- |
| `allowBlockTags` | `String` | Definiert die Liste der zulässigen Block-Tags. Zu den Blocktags gehören Überschriften (h1, h2, h3), Absätze (p), Listen (ol, ul) und Tabellen (Tabelle). |
| `fallbackBlockTag` | `String` | Defines the block tag used for any blocks having a block tag not included in `allowBlockTags`. Normalerweise reicht `p` es. |
| `table` | `nt:unstructured` | Definiert das Verhalten beim Einfügen von Tabellen. Dieser Knoten muss über die Eigenschaft allow (Typ Boolean) verfügen, um festzulegen, ob das Einfügen von Tabellen zulässig ist. Wenn allow auf false gesetzt ist, müssen Sie den Wert für die Eigenschaft ignoreMode (Typ String) angeben, um festzulegen, wie eingefügte Tabelleninhalte verarbeitet werden sollen. Gültige Werte für ignoreMode sind `remove` das Entfernen von Tabelleninhalten und das `paragraph` Umwandeln von Tabellenzellen in Absätze. |
| `list` | `nt:unstructured` | Definiert das Verhalten beim Einfügen von Listen. Muss über die Eigenschaft `allow` (Typ Boolean) verfügen, um festzulegen, ob das Einfügen von Listen zulässig ist. If `allow` is set to `false`, specify the property `ignoreMode` (type `String`) to define how to handle any list content pasted. Die gültigen Werte für ignoreMode sind `remove` das Entfernen von Listen-Inhalten und das `paragraph` Umwandeln von Listen in Absätze. |

Ein Beispiel für eine gültige `htmlPasteRules` Struktur ist unten aufgeführt:

```xml
"htmlPasteRules": {
    "allowBasics": {
        "italic": true,
        "link": true
    },
    "allowBlockTags": [
        "p", "h1", "h2", "h3"
    ],
    "list": {
        "allow": false,
        "ignoreMode": "paragraph"
    },
    "table": {
        "allow": true,
        "ignoreMode": "paragraph"
    }
}
```

1. Speichern Sie alle Änderungen.

## Konfigurieren von Textstilen {#textstyles}

Autoren können Stile anwenden, um das Erscheinungsbild eines Textabschnitts zu ändern. Die Stile basieren auf CSS-Klassen, die Sie in Ihrem CSS-Stylesheet vordefinieren. Stilisierter Inhalt wird in `span`-Tags eingeschlossen, wobei das Attribut `class` zum Verweis auf die CSS-Klasse verwendet wird. Beispiel:

`<span class=monospaced>Monospaced Text Here</span>`

Wenn das styles-Plug-in zum ersten Mal aktiviert wird, sind keine Standardstile verfügbar. Die Popup-Liste ist leer. Gehen Sie wie folgt vor, um Stile für Autoren bereitzustellen:

* Aktivieren Sie die Dropdown-Auswahl „Stil“.
* Geben Sie eine oder mehrere Positionen der Stylesheets an.
* Geben Sie die einzelnen Stile an, die aus der Popup-Liste &quot;Stil&quot;ausgewählt werden können.

Für spätere Neukonfigurationen, z. B. um weitere Stile hinzuzufügen, folgen Sie nur den Anweisungen, um auf ein neues Stylesheet zu verweisen und die zusätzlichen Stile anzugeben.

>[!NOTE]
>
>Auch für [Tabellen oder Tabellenzellen können Stile definiert werden](configure-rich-text-editor-plug-ins.md#tablestyles). Diese Konfigurationen erfordern unterschiedliche Vorgehensweisen.

### Aktivieren der Dropdown-Liste „Stil“{#styleselectorlist}

Aktivieren Sie dazu das styles-Plug-in.

1. In your component, navigate to the node `<rtePlugins-node>/styles`. Erstellen Sie die Knoten, wenn die Knoten nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Create the `features` property on the `styles` node:

   * **Name** `features`
   * **Typ** `String`
   * **Wert** `*` (Sternchen)

1. Speichern Sie alle Änderungen.

>[!NOTE]
>
>Sobald das styles-Plug-in aktiviert ist, wird die Dropdown-Liste „Stil“ im Dialogfeld „Bearbeiten“ angezeigt. Allerdings ist die Liste leer, da keine Stile konfiguriert sind.

### Festlegen der Speicherorte für Stylesheets {#locationofstylesheet}

Geben Sie dann die Speicherorte für die Stylesheets an, auf die Sie verweisen möchten:

1. Navigate to the root node of your text component, for example `/apps/<myProject>/components/text`.
1. Add the property `externalStyleSheets` to the parent node of `<rtePlugins-node>`:

   * **Name** `externalStyleSheets`
   * **Typ** `String[]` (mehrere Zeichenfolgen) auf **Multi** in CRXDE klicken)
   * **Wert(e):** Der Pfad und der Dateiname von jedem Stylesheet, das eingeschlossen werden soll. Verwenden Sie Repository-Pfade.

   >[!NOTE]
   >
   >Sie können jederzeit Verweise auf weitere Stylesheets hinzufügen.

1. Speichern Sie alle Änderungen.

Bei Verwendung von RTE in einem Dialogfeld (klassische Benutzeroberfläche) können Sie Stylesheets angeben, die für die Bearbeitung von Rich-Text optimiert sind. Aufgrund technischer Einschränkungen geht der CSS-Kontext im Editor verloren, sodass Sie diesen Kontext emulieren können, um das WYSIWYG-Erlebnis zu verbessern.

Der Rich-Text-Editor verwendet ein Container-DOM-Element mit einer ID, `CQrte` die verschiedene Stile zur Ansicht und Bearbeitung bereitstellt:

```css
#CQ td {
// defines the style for viewing
 }
```

```css
#CQrte td {
 // defines the style for editing
 }
```

### Festlegen von Stilen, die in der Popup-Liste verfügbar sein sollen {#stylesindropdown}

1. In the component definition, navigate to the node `<rtePlugins-node>/styles`, as created in [Enabling the style drop-down selector](#styleselectorlist).
1. Under the node `styles`, create a node (also called `styles`) to hold the list being made available:

   * **Name** `styles`
   * **Typ** `cq:WidgetCollection`

1. Create a node under the `styles` node to represent an individual style:

   * **Name:** Sie können einen Namen angeben, dieser sollte jedoch dem Stil entsprechen.
   * **Typ** `nt:unstructured`

1. Fügen Sie diesem Knoten die Eigenschaft `cssName` hinzu, um auf die CSS-Klasse zu verweisen:

   * **Name** `cssName`
   * **Typ** `String`
   * **Wert:** Der Name der CSS-Klasse (ohne „.“ voranzustellen; for example, `cssClass` instead of `.cssClass`)

1. Fügen Sie demselben Knoten die Eigenschaft `text` hinzu. Dadurch wird der im Auswahlfeld angezeigte Text definiert:

   * **Name** `text`
   * **Typ** `String`
   * **Wert:** Beschreibung des Stils, der in der Dropdown-Auswahl „Stil“ angezeigt wird.

1. Speichern Sie die Änderungen.

   Wiederholen Sie die obigen Schritte für jeden erforderlichen Stil.

### RTE für optimale Wortumbrüche auf Japanisch konfigurieren {#jpwordwrap}

Authors using [!DNL Experience Manager] to author Japanese language content can apply a style to characters to avoid line break where a break is not required. Dadurch können Autoren die Sätze an der gewünschten Position umbrechen. Der Stil für diese Funktion basiert auf der CSS-Klasse, die im CSS-Stylesheet vordefiniert ist.

Führen Sie folgende Schritte aus, um den Stil zu erstellen, den Autoren auf Japanisch anwenden können:

1. Erstellen Sie einen Knoten unter dem Knoten &quot;Stile&quot;. See [specify a style](#stylesindropdown).
   * Name: `jpn-word-wrap`
   * Typ: `nt:unstructure`

1. Fügen Sie diesem Knoten die Eigenschaft `cssName` hinzu, um auf die CSS-Klasse zu verweisen. Dieser Klassenname ist ein reservierter Name für die japanische Wortumbruchfunktion.
   * Name: `cssName`
   * Typ: `String`
   * Wert: `jpn-word-wrap` (ohne vorherige Angaben `.`)

1. Fügen Sie den Text der Eigenschaft demselben Knoten hinzu. Der Wert ist der Name des Stils, den die Autoren beim Auswählen des Stils sehen.
   * Name: `text`
*Type: 
`String`
   * Wert: `Japanese word-wrap`

1. Erstellen Sie ein Stylesheet und geben Sie den Pfad an. Siehe [Speicherort des Stylesheets angeben](#locationofstylesheet). Fügen Sie dem Stylesheet den folgenden Inhalt hinzu. Ändern Sie die Hintergrundfarbe wie gewünscht.

   ```css
   .text span.jpn-word-wrap {
       display:inline-block;
   }
   .is-edited span.jpn-word-wrap {
       background-color: #ffddff;
   }
   ```

   ![Stylesheet, mit dem Autoren japanische Wrapper-Funktionen zur Verfügung gestellt werden](assets/rte_jpwordwrap_stylesheet.jpg)

## Konfigurieren der Absatzformate {#paraformats}

Any text authored in RTE is placed within a block tag, the default being `<p>`. By enabling the `paraformat` plug-in, you specify additional block tags that can be assigned to paragraphs, using a drop-down selection list. Absatzformate bestimmen den Absatztyp durch Zuweisung des richtigen Block-Tags. Der Autor kann diese mithilfe der Format-Auswahl auswählen und zuweisen. Die Beispiel-Block-Tags beinhalten u. a. den Standardabsatz „&lt;p>“ und die Kopfzeilen „&lt;h1>“, „&lt;h2>“ usw.

>[!CAUTION]
>
>Dieses Plug-in eignet sich nicht für Inhalte mit komplexer Struktur, beispielsweise Listen und Tabellen.

>[!NOTE]
>
>If a block tag, for example an `<hr>` tag, can&#39;t be assigned to a paragraph, it is not a valid use case for a `paraformat` plug-in.

Wenn das paraformat-Plug-in zum ersten Mal aktiviert wird, sind keine Standabsatzformate verfügbar. Die Popup-Liste ist leer. Gehen Sie wie folgt vor, um den Autoren Absatzformate bereitzustellen:

* Enable the [!UICONTROL Format] pop-up selector list.
* Geben Sie die Block-Tags an, die im Popupmenü als Absatzformate ausgewählt werden können.

Für spätere Neukonfigurationen, z. B. um weitere Formate hinzuzufügen, folgen Sie nur dem entsprechenden Teil der Anweisungen.

### Aktivieren der Dropdown-Auswahl „Format“.{#formatselectorlist}

Gehen Sie wie folgt vor, um das `paraformat` Plug-In zu aktivieren:

1. In your component, navigate to the node `<rtePlugins-node>/paraformat`. Erstellen Sie die Knoten, wenn die Knoten nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Create the `features` property on the `paraformat` node:

   * **Name** `features`
   * **Typ** `String`
   * **Wert** `*` (Sternchen)

>[!NOTE]
>
>Wenn das Plug-In nicht weiter konfiguriert ist, sind die Standardformate Absatz ( `<p>`), Überschrift 1 ( `<h1>`), Überschrift 2 ( `<h2>`) und Überschrift 3 ( `<h3>`) aktiviert.

>[!CAUTION]
>
>Entfernen Sie beim Konfigurieren der Absatzformate des RTE nicht das Absatz-Tag „&lt;p>“ als Formatierungsoption. If the `<p>` tag is removed, then the content author can not select the [!UICONTROL Paragraph formats] option even if there are additional formats configured.

### Angeben der verfügbaren Absatzformate {#paraformatsindropdown}

Absatzformate stehen zur Auswahl zur Verfügung durch:

1. In the component definition, navigate to the node `<rtePlugins-node>/paraformat`, as created in [Enabling the format drop-down selector](#styleselectorlist).
1. Under the `paraformat` node create a node, to hold the list of formats:

   * **Name** `formats`
   * **Typ** `cq:WidgetCollection`

1. Create a node under the `formats` node, this holds details for an individual format:

   * **Name:** Sie können einen Namen angeben, dieser sollte jedoch dem Format entsprechen (z. B. myparagraph, myheading1).
   * **Typ** `nt:unstructured`

1. Fügen Sie diesem Knoten die Eigenschaft hinzu, um das verwendete Block-Tag zu definieren:

   * **Name** `tag`
   * **Typ** `String`
   * **Wert:** Das Block-Tag für das Format (z. B. p, h1, h2 usw.)

      Es ist nicht notwendig, die abgrenzenden spitzen Klammern einzugeben.

1. Fügen Sie demselben Knoten eine weitere Eigenschaft hinzu, damit ein beschreibender Text in der Dropdown-Liste angezeigt wird:

   * **Name** `description`
   * **Typ** `String`
   * **Wert:** der beschreibende Text für dieses Format, z. B. „Absatz“, „Überschrift 1“, „Überschrift 2“ usw. Dieser Text wird in der Auswahlliste „Format“ angezeigt.

1. Speichern Sie die Änderungen.

   Wiederholen Sie die Schritte für jedes erforderliche Format.

>[!CAUTION]
If you define custom formats, the default formats (`<p>`, `<h1>`, `<h2>`, and `<h3>`) are removed. Re-create `<p>` format as it is the default format.

## Konfigurieren von Sonderzeichen {#spchar}

In a standard [!DNL Experience Manager] installation, when the `misctools` plug-in is enabled for special characters (`specialchars`) a default selection is immediately available for use; for example, the copyright and trademark symbols.

Sie können die RTE so konfigurieren, dass Ihre Auswahl an Zeichen verfügbar ist. entweder durch Definition von eindeutigen Zeichen oder durch Angabe einer ganzen Sequenz.

>[!CAUTION]
Wenn Sie Sonderzeichen hinzufügen, wird die Standardauswahl außer Kraft gesetzt. Definieren Sie diese Zeichen bei Bedarf neu.

### Definieren einzelner Zeichen {#definesinglechar}

1. In your component, navigate to the node `<rtePlugins-node>/misctools`. Erstellen Sie die Knoten, wenn die Knoten nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Create the `features` property on the `misctools` node:

   * **Name** `features`
   * **Typ** `String[]`
   * **Wert** `specialchars`

          (or `String / *` if applying all features for this plug-in)

1. Erstellen Sie unter `misctools` einen Knoten, um die Sonderzeichenkonfigurationen zu speichern:

   * **Name** `specialCharsConfig`
   * **Typ** `nt:unstructured`

1. Erstellen Sie unter `specialCharsConfig` einen weiteren Knoten, unter dem die Liste der Zeichen gespeichert werden soll:

   * **Name** `chars`
   * **Typ** `nt:unstructured`

1. Under `chars` add a node to hold an individual character definition:

   * **Name:** Sie können einen Namen angeben, dieser sollte jedoch das Zeichen widerspiegeln, wie beispielsweise „half“ (Halb).
   * **Typ** `nt:unstructured`

1. Fügen Sie diesem Knoten die folgende Eigenschaft hinzu:

   * **Name** `entity`
   * **Typ** `String`
   * **Wert** der HTML-Darstellung des erforderlichen Zeichens; zum Beispiel `&189;` für die Bruchteile eine Hälfte.

1. Speichern Sie die Änderungen.

In CRXDE wird nach dem Speichern der Eigenschaft das angezeigte Zeichen angezeigt. Siehe „half“ im unten aufgeführten Beispiel. Wiederholen Sie die obigen Schritte, um weitere Sonderzeichen für Autoren verfügbar zu machen.

![Fügen Sie in CRXDE ein einzelnes Zeichen hinzu, das in der RTE-](assets/chlimage_1-106.png "Symbolleiste verfügbar gemacht werden soll. Fügen Sie in CRXDE ein einzelnes Zeichen hinzu, das in der RTE-Symbolleiste verfügbar gemacht werden soll.")

### Definieren von Zeichenbereichen {#definerangechar}

1. Use steps 1 to 3 from [Define a single character](#definesinglechar).
1. Under `chars` add a node to hold the definition of the character range:

   * **Name:** Sie können einen Namen angeben, dieser sollte jedoch den Zeichenbereich widerspiegeln, wie beispielsweise „pencils“.
   * **Typ** `nt:unstructured`

1. Fügen Sie unter diesem Knoten (der entsprechend dem Sonderzeichenbereich benannt wurde) die folgenden beiden Eigenschaften hinzu:

   * **Name** `rangeStart`

      **Typ** `Long`
      **Wert** der [Unicode](https://unicode.org/) -Darstellung (Dezimalzahl) des ersten Zeichens im Bereich

   * **Name** `rangeEnd`

      **Typ** `Long`
      **Wert** der [Unicode](https://unicode.org/) -Darstellung (Dezimalzahl) des letzten Zeichens im Bereich

1. Speichern Sie die Änderungen.

   Wenn Sie zum Beispiel einen Bereich von 9998 bis 10000 definieren, erhalten Sie die folgenden Zeichen:

   ![Definieren Sie in CRXDE einen Zeichenbereich, um ihn in der RTE-Symbolleiste verfügbar zu machen.](assets/chlimage_1-107.png)

   *Abbildung: Definieren Sie in CRXDE einen Zeichenbereich, der in RTE verfügbar gemacht werden soll.*

   ![Sonderzeichen in RTE werden Autoren in einem Popup-](assets/rtepencil.png "Fenster angezeigt. Sonderzeichen in RTE werden Autoren in einem Popup-Fenster angezeigt")

## Konfigurieren von Tabellenstilen {#tablestyles}

Neben der Definition von Stilen, die auf normalen Text angewendet werden, können Sie auch Stile (einen separaten Satz) für eine ganze Tabelle oder einzelne Tabellenzellen definieren. Diese können dann im Dialogfeld „Zellen-Eigenschaften“ oder „Tabelleneigenschaften“ im Auswahlfeld „Stil“ ausgewählt werden. Diese Stile sind nur verfügbar, wenn eine Tabelle in einer Textkomponente (oder einer abgeleiteten Komponente davon) und nicht in der standardmäßigen Tabellenkomponente bearbeitet wird.

>[!NOTE]
Sie können Stile für Tabellen und Tabellenzellen nur in der klassischen Benutzeroberfläche definieren.

>[!NOTE]
Die Funktion zum Kopieren und Einfügen von Tabellen in oder aus der RTE-Komponente ist Browser-abhängig. Sie wird nicht standardmäßig für alle Browser unterstützt. Je nach Tabellenstruktur und Browser können die Ergebnisse unterschiedlich ausfallen. Wenn Sie beispielsweise eine Tabelle in einer RTE-Komponente in Mozilla Firefox in der Benutzeroberfläche &quot;Klassisch&quot;und &quot;Touch&quot;kopieren und einfügen, wird das Layout der Tabelle nicht beibehalten.

1. Navigieren Sie innerhalb Ihrer Komponente zum Knoten `<rtePlugins-node>/table`. Erstellen Sie die Knoten, wenn die Knoten nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Create the `features` property on the `table` node:

   * **Name** `features`
   * **Typ** `String`
   * **Wert** `*`

   >[!NOTE]
   Wenn Sie nicht alle Tabellen-Features aktivieren möchten, erstellen Sie die `features`-Eigenschaft wie folgt:
   * **Typ** `String[]`

   * **Wert(e):** Nach Bedarf einen oder beide der folgenden Werte:
      * `table` die Bearbeitung von Tabelleneigenschaften zu ermöglichen; einschließlich der Stile.
      * `cellprops` , um die Bearbeitung von Zelleneigenschaften einschließlich der Stile zu ermöglichen.


1. Definieren Sie den Speicherort von CSS-Stylesheets, um auf diese zu verweisen. Lesen Sie den Abschnitt [Festlegen des Speicherorts des Stylesheets](#locationofstylesheet), da die Vorgehensweise hier dieselbe ist wie beim Definieren von [Stilen für Text](#textstyles). Der Speicherort wurde möglicherweise bereits beim Definieren anderer Stile definiert.
1. Under the `table` node create the following nodes as required:

   * So definieren Sie Stile für die komplette Tabelle (verfügbar unter **[!UICONTROL Tabelleneigenschaften]**):

      * **Name** `tableStyles`
      * **Typ** `cq:WidgetCollection`
   * So definieren Sie Stile für einzelne Tabellenzellen (verfügbar unter **[!UICONTROL Zellen-Eigenschaften]**),

      * **Name** `cellStyles`
      * **Typ** `cq:WidgetCollection`


1. Create a node (under the `tableStyles` or `cellStyles` node as appropriate) to represent an individual style,

   * **Name** Sie können den Namen angeben, er sollte jedoch den Stil widerspiegeln.
   * **Typ** `nt:unstructured`

1. Erstellen Sie in diesem Knoten die folgenden Eigenschaften:

   * So definieren Sie den CSS-Stil, auf den verwiesen wird:

      * **Name** `cssName`
      * **Typ** `String`
      * **Wert** des Namens der CSS-Klasse (ohne vorherige `.`z. B. `cssClass` anstelle von `.cssClass`)
   * So definieren Sie einen beschreibenden Text, der in der Popup-Auswahl angezeigt werden soll,

      * **Name** `text`
      * **Typ** `String`
      * **Wert:** Der Text, der in der Auswahlliste angezeigt werden soll


1. Speichern Sie alle Änderungen.

Wiederholen Sie die obigen Schritte für jeden erforderlichen Stil.

### Konfigurieren von ausgeblendeten Kopfzeilen in Tabellen, um die Zugänglichkeit zu verbessern {#hiddenheader}

Manchmal kann es sein, dass Sie Datentabellen ohne visuellen Text in einer Spaltenkopfzeile erstellen, da Sie voraussetzen, dass sich der Zweck der Kopfzeile durch die visuelle Beziehung der Spalte mit anderen Spalten ergibt. In diesem Fall ist es erforderlich, dass Sie ausgeblendeten inneren Text innerhalb der Zelle in der Kopfzeilenzelle bereitstellen, damit Bildschirmlesehilfen und andere unterstützende Technologien Benutzern mit unterschiedlichen Bedürfnissen helfen können, den Zweck der Spalte zu verstehen.

Um die Zugänglichkeit in solchen Fällen zu verbessern, unterstützt der RTE ausgeblendete Kopfzeilenzellen. Darüber hinaus stellt er Konfigurationseinstellungen bezüglich der ausgeblendeten Kopfzeilen in Tabellen bereit. Mit diesen Einstellungen können Sie CSS-Stile auf ausgeblendete Kopfzeilen im Bearbeitungs- und Vorschau-Modus anwenden. Damit Autoren ausgeblendete Kopfzeilen im Bearbeitungsmodus besser identifizieren können, fügen Sie die folgenden Parameter in Ihren Code ein:

* `hiddenHeaderEditingCSS`: Gibt den Namen der CSS-Klasse an, die bei der Bearbeitung von RTE auf die Zelle der ausgeblendeten Kopfzeile angewendet wird.
* `hiddenHeaderEditingStyle`: Gibt eine Stilzeichenfolge an, die bei der Bearbeitung der RTE auf die Zelle der ausgeblendeten Kopfzeile angewendet wird.

Wenn Sie sowohl die CSS- als auch die Stilzeichenfolge im Code angeben, hat die CSS-Klasse Vorrang vor der Stilzeichenfolge. Sie überschreibt möglicherweise Konfigurationsänderungen, die mittels der Stilzeichenfolge vorgenommen werden.

Um Autoren bei der Anwendung von CSS auf ausgeblendete Header im Vorschau-Modus zu unterstützen, können Sie die folgenden Parameter in Ihren Code einschließen:

* `hiddenHeaderClassName`: Gibt den Namen der CSS-Klasse an, die im Vorschaumodus auf die ausgeblendete Kopfzeilenzelle angewendet wird.
* `hiddenHeaderStyle`: Gibt eine Stilzeichenfolge an, die im Vorschaumodus auf die ausgeblendete Kopfzeilenzelle angewendet wird

Wenn Sie sowohl die CSS- als auch die Stilzeichenfolge im Code angeben, hat die CSS-Klasse Vorrang vor der Stilzeichenfolge. Sie überschreibt möglicherweise Konfigurationsänderungen, die mittels der Stilzeichenfolge vorgenommen werden.

## Hinzufügen von Wörterbüchern für die Rechtschreibprüfung {#adddict}

Wenn das spellcheck-Plug-in aktiviert wird, verwendet der RTE Wörterbücher für jede entsprechende Sprache. Diese werden dann entsprechend der Sprache der Website ausgewählt, indem entweder die language-Eigenschaft der Unterstruktur verwendet oder die Sprache aus der URL extrahiert wird. the `/en/` branch is checked as English, the `/de/` branch as German.

>[!NOTE]
Die Meldung „Rechtschreibprüfung fehlgeschlagen.“ wird angezeigt, wenn versucht wird, eine Überprüfung für eine Sprache durchzuführen, die nicht installiert ist.

Eine Standardinstallation für Experience Manager beinhaltet die Wörterbücher für:

* Amerikanisches Englisch (en_us)
* Britisches Englisch (en_gb)

>[!NOTE]
The standard dictionaries are located at `/libs/cq/spellchecker/dictionaries`, along with the appropriate ReadMe files. Diese Dateien sollten nicht geändert werden.

Gehen Sie wie folgt vor, um ggf. weitere Wörterbücher hinzuzufügen.

1. Navigieren Sie zur Seite [https://extensions.openoffice.org/](https://extensions.openoffice.org/).
1. Wählen Sie die gewünschte Sprache aus und laden Sie die ZIP-Datei mit den Rechtschreibedefinitionen herunter. Entpacken Sie den Inhalt des Archivs in Ihrem Dateisystem.

   >[!CAUTION]
   Nur Wörterbücher im `MySpell`-Format für OpenOffice.org v2.0.1 bzw. frühere Versionen werden unterstützt. Da die Wörterbücher jetzt Archivdateien sind, ist es ratsam, eine vollständige Prüfung nach dem Herunterladen durchzuführen.

1. Suchen Sie nach den *.aff- und *.dic-Dateien. Der Dateiname darf nur Kleinbuchstaben aufweisen. Zum Beispiel `de_de.aff` und `de_de.dic`.
1. Load the .aff and .dic files in the repository at `/apps/cq/spellchecker/dictionaries`.

>[!NOTE]
Die RTE-Rechtschreibprüfung ist nur auf Abruf verfügbar. Sie wird nicht automatisch ausgeführt, wenn Sie beginnen, Text einzugeben.
Aktivieren Sie die Rechtschreibprüfung, indem Sie in der Symbolleiste auf die Schaltfläche „Rechtschreibprüfung“ tippen/klicken. Der RTE überprüft die Rechtschreibprüfung der Wörter und markiert falsch geschriebene Wörter.
Wenn Sie eine Änderung annehmen, die die Rechtschreibprüfung vorschlägt, ändert sich der Status des Textes und das falsch geschriebene Wort ist nicht länger markiert. Um die Rechtschreibprüfung auszuführen, tippen/klicken Sie erneut auf die Rechtschreibprüfung.

## Konfigurieren der Verlaufsgröße für die Aktionen „Rückgängig“ und „Wiederholen“{#undohistory}

Der RTE bietet Autoren die Möglichkeit, bei Bedarf die letzten Bearbeitungsschritte rückgängig zu machen bzw. zu wiederholen. Standardmäßig werden im Verlauf 50 Schritte gespeichert. Sie können diesen Wert nach Bedarf konfigurieren.

1. Navigieren Sie innerhalb Ihrer Komponente zum Knoten `<rtePlugins-node>/undo`. Erstellen Sie diese Knoten, falls sie nicht bereits vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Erstellen Sie im `undo`-Knoten die folgende Eigenschaft:

   * **Name** `maxUndoSteps`
   * **Typ** `Long`
   * **Wert:** Die Anzahl an rückgängig zu machenden Schritten, die Sie im Verlauf speichern wollen. Standard: 50. Verwenden Sie diese Option, `0` um Rückgängig/Wiederholen vollständig zu deaktivieren.

1. Speichern Sie die Änderungen.

## Konfigurieren der Tabulator-Schrittweite {#tabsize}

Wenn das Tabulatorzeichen innerhalb eines beliebigen Texts gedrückt wird, wird eine vordefinierte Anzahl von Leerzeichen eingefügt. Standardmäßig werden drei geschützte Leerzeichen und ein normales Leerzeichen eingefügt.

So definieren Sie die Tabulator-Schrittweite:

1. In your component, navigate to the node `<rtePlugins-node>/keys`. Erstellen Sie die Knoten, wenn die Knoten nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Erstellen Sie im `keys`-Knoten die folgende Eigenschaft:

   * **Name** `tabSize`
   * **Typ** `String`
   * **Wert:** Die Anzahl an für den Tabulator verwendeten Leerzeichen.

1. Speichern Sie die Änderungen.

## Festlegen des Einzugsrands {#indentmargin}

Wenn die Einzugsfunktion aktiviert ist (Standardeinstellung), können Sie die Einzugsgröße definieren:

>[!NOTE]
Diese Einzugsgröße wird nur auf Absätze (Blöcke) des Texts angewendet. Sie wirkt sich nicht auf den Einzug von tatsächlichen Listen aus.

1. Navigieren Sie innerhalb Ihrer Komponente zum Knoten `<rtePlugins-node>/lists`. Erstellen Sie diese Knoten, falls sie nicht bereits vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. On the `lists` node create the `identSize` parameter:

   * **Name**: `identSize`
   * **Typ**: `Long`
   * **Wert:** Die Anzahl an Pixel, die für den Einzugsrand erforderlich sind.

## Konfigurieren der Höhe des bearbeitbaren Bereichs {#editablespace}

Sie können die Höhe des bearbeitbaren Bereichs definieren, der innerhalb des Komponenten-Dialogfelds angezeigt wird. Die Konfiguration ist nur bei Verwendung der RTE in einem Dialogfeld anwendbar. Die Höhe des Dialogfensters wird durch die Konfiguration nicht geändert.

1. In the `../items/text` node, in the dialog definition for the component, create a property:

   * **Name** `height`
   * **Typ** `Long`
   * **Wert:** Die Höhe der Bearbeitungsfläche in Pixeln.

1. Speichern Sie die Änderungen.

## Konfigurieren von Stilen und Protokollen für Links {#linkstyles}

Beim Hinzufügen von Links in [!DNL Experience Manager]können Sie die zu verwendenden CSS-Stile und die Protokolle definieren, die automatisch akzeptiert werden sollen. To configure how links are added in [!DNL Experience Manager] from another program, define the HTML rules.

1. Suchen Sie mithilfe von CRXDE Lite nach der Textkomponente für Ihr Projekt.
1. Create a node at the same level as `<rtePlugins-node>`, that is, create the node under the parent node of `<rtePlugins-node>`:

   * **Name** `htmlRules`
   * **Typ** `nt:unstructured`

   >[!NOTE]
   The `../items/text` node has the property:
   * **Name** `xtype`
   * **Typ** `String`
   * **Wert** `richtext`

   The location of the `../items/text` node can vary, depending on the structure of your dialog. Zwei Beispiele sind `/apps/myProject>/components/text/dialog/items/text` und `/apps/<myProject>/components/text/dialog/items/panel/items/text`.

1. Erstellen Sie `htmlRules`unter einen Knoten.

   * **Name** `links`
   * **Typ** `nt:unstructured`

1. Definieren Sie unter dem `links`-Knoten die benötigten Eigenschaften:

   * CSS-Stil für interne Links:

      * **Name** `cssInternal`
      * **Typ** `String`
      * **Wert:** Der Name der CSS-Klasse (ohne „.“ voranzustellen; for example, `cssClass` instead of `.cssClass`)
   * CSS-Stil für externe Links

      * **Name** `cssExternal`
      * **Typ** `String`
      * **Wert:** Der Name der CSS-Klasse (ohne „.“ voranzustellen; for example, `cssClass` instead of `.cssClass`)
   * Array gültiger **[!UICONTROL Protokolle]** , einschließlich `https://`, `https://`, `file://`, `mailto:`und andere,

      * **Name** `protocols`
      * **Typ** `String[]`
      * **Wert(e):** Ein oder mehrere Protokolle
   * **defaultProtocol** (Eigenschaft des Typs **String**): Protokoll, das verwendet wird, wenn der Benutzer keines explizit festlegt

      * **Name** `defaultProtocol`
      * **Typ** `String`
      * **Wert(e):** Ein oder mehrere Standardprotokolle
   * Definition der Art, wie das Zielattribut eines Links verarbeitet werden soll Knoten erstellen:

      * **Name** `targetConfig`
      * **Typ** `nt:unstructured`

      Definieren Sie im Knoten `targetConfig` die erforderlichen Eigenschaften:

      * Legen Sie den Zielmodus fest:

         * **Name** `mode`
         * **Typ** `String`)
         * **Wert(e)**:

            * `auto`: bedeutet, dass eine automatische Zielgruppe gewählt wird

               (durch die `targetExternal` Eigenschaft für externe Links oder `targetInternal` für interne Links angegeben).

            * `manual` : In diesem Kontext unzulässig
            * `blank` : In diesem Kontext unzulässig
      * Das Ziel für interne Links:

         * **Name** `targetInternal`
         * **Typ** `String`
         * **Zielgruppe für interne Links bewerten** (nur verwenden, wenn der Modus `auto`)
      * Das Ziel für externe Links:

         * **Name** `targetExternal`
         * **Typ** `String`
         * **Wert:** Das Ziel für externe Links (nur verwenden, wenn der Modus `auto` aktiv ist)








1. Speichern Sie alle Änderungen.
