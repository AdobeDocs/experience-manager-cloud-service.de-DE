---
title: Konfigurieren der Rich-Text-Editor-Plug-ins
description: Erfahren Sie, wie Sie die Rich-Text-Editor-Plug-ins von AEM konfigurieren, um einzelne Funktionen zu aktivieren.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b5af8cad55c8644ba613370cf65b6a04b3abf9ed
workflow-type: tm+mt
source-wordcount: '4348'
ht-degree: 76%

---


# Konfigurieren der Rich-Text-Editor-Plug-ins {#configure-the-rich-text-editor-plug-ins}

RTE-Funktionen werden über eine Reihe von Plug-ins mit jeweils einer Eigenschaft „features“ bereitgestellt. Sie können die Eigenschaft „features“ so konfigurieren, dass eine oder mehrere RTE-Funktionen aktiviert oder deaktiviert werden. In diesem Artikel wird beschrieben, wie Sie die RTE-Plug-Ins spezifisch konfigurieren.

For details about the other RTE configurations, see [configure Rich Text Editor](/help/implementing/developing/extending/rich-text-editor.md).

>[!NOTE]
>
>When working with CRXDE Lite, it is recommended to save the changes regularly using [!UICONTROL Save All] option.

## Aktivieren von Plug-ins und Konfigurieren der Eigenschaft „features“{#activateplugin}

Gehen Sie wie folgt vor, um ein Plug-in zu aktivieren. Einige Schritte sind nur erforderlich, wenn Sie ein Plug-in zum ersten Mal konfigurieren, da die entsprechenden Knoten noch nicht vorhanden sind.

By default, `format`, `link`, `list`, `justify`, and `control` plugins and all their features are enabled in RTE.

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

|  | Alle Funktionen aktivieren | Bestimmte Funktionen aktivieren | Alle Funktionen deaktivieren |
|---|---|---|---|
| Name | features | features | features |
| Typ | Zeichenfolge | String[] (multi-string; set Type to String and click Multi in CRXDE Lite) | Zeichenfolge |
| Wert | `*` (ein Sternchen) | Legen Sie einen oder mehrere Werte für die Eigenschaft „features“ fest. | - |

## Das findreplace-Plug-in {#findreplace}

The `findreplace` plug-in does not need any configuration. Es funktioniert aus der Schachtel.

Bei Verwendung der Funktion zum Ersetzen sollte die Zeichenfolge zum Ersetzen gleichzeitig mit der Suchzeichenfolge eingegeben werden. Sie können jedoch weiterhin auf „Suchen“ klicken, um nach der Zeichenfolge zu suchen, bevor Sie sie ersetzen. Wenn die Zeichenfolge zum Ersetzen eingegeben wird, nachdem auf „Suchen“ geklickt wurde, wird die Suche auf den Anfang des Textes zurückgesetzt.

Das Dialogfeld „Suchen und ersetzen“ wird transparent, wenn auf „Suchen“ geklickt wird, und undurchsichtig, wenn auf „Ersetzen“ geklickt wird. Dadurch kann der Autor den Text überprüfen, den der Autor ersetzen wird. Wenn der Benutzer auf „Alle ersetzen“ klickt, wird das Dialogfeld geschlossen und die Anzahl der vorgenommenen Ersetzungen angezeigt.

## Konfigurieren der Einfügemodi {#pastemodes}

Bei Verwendung des RTE können Autoren Inhalte in einem der drei folgenden Modi einfügen:

* **Browsermodus**: Fügen Sie Text mit der Standardfunktion des Browsers zum Einfügen ein. Dieses Verfahren wird nicht empfohlen, da es unerwünschte Markups verursachen kann.

* **Reiner Textmodus**: Fügen Sie Inhalte aus der Zwischenablage als Text ein. Dadurch werden alle Stil- und Formatierungselemente vom kopierten Inhalt entfernt, bevor er in eine AEM-Komponente eingefügt wird.

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

* Fügen Sie den Inhalt aus der Zwischenablage als Text ein. Dadurch werden alle Stil- und Formatierungselemente vom kopierten Inhalt entfernt, bevor er in eine AEM-Komponente eingefügt wird. Configured using `plaintext` below.

* Fügen Sie den Text, einschließlich Tabellen, mit Formatierung beim Kopieren aus Microsoft Word ein. Das Kopieren und Einfügen von Text aus einer anderen Quelle wie einer Webseite oder Microsoft Excel wird nicht unterstützt und dabei wird nur ein Teil der Formatierung beibehalten. Configured using `wordhtml` below.

1. In your component, navigate to `<rtePlugins-node>/edit` node. Erstellen Sie die Knoten, falls diese noch nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
1. Erstellen Sie im Knoten `edit` eine Eigenschaft mithilfe der folgenden Details:

   * **Name** `defaultPasteMode`
   * **Typ** `String`
   * **Wert** Einer der erforderlichen Einfügemodi `browser`, `plaintext`oder `wordhtml`.

### Konfigurieren der beim Einfügen von Inhalten zulässigen Formate {#pasteformats}

The paste-as-Microsoft-Word (`paste-wordhtml`) mode can be further configured so that you can explicitly define which styles are allowed when pasting in AEM from another program, such as Microsoft Word.

Wenn beispielsweise beim Einfügen in AEM nur fett formatierte Formate und Listen zulässig sein sollten, können Sie die anderen Formate herausfiltern. Dies wird als konfigurierbare Paste-Filterung bezeichnet, die für beide Aufgaben durchgeführt werden kann:

* [Text](#pastemodes)
* [Links](#linkstyles)

Für Links können Sie zudem die Protokolle definieren, die automatisch akzeptiert werden.

So konfigurieren Sie, welche Formate beim Einfügen von Text in AEM von einem anderen Programm aus zulässig sind:

1. In your component, navigate to the node `<rtePlugins-node>/edit`. Erstellen Sie die Knoten, falls diese noch nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
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

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>allowBlockTags</td>
   <td>Zeichenfolge[]</td>
   <td><p>Definiert die Liste der zulässigen Block-Tags.</p> <p>Zu den möglichen Block-Tags gehören:</p>
    <ul>
     <li>Überschriften (h1, h2, h3)</li>
     <li>Absätze (p)</li>
     <li>Listen (ol, ul)</li>
     <li>Tabellen (table)</li>
    </ul> </td>
  </tr>
  <tr>
   <td>fallbackBlockTag</td>
   <td>Zeichenfolge</td>
   <td><p>Definiert das Block-Tag, das für alle Blöcke mit einem Block-Tag verwendet wird, das nicht in „allowBlockTags“ eingeschlossen ist.</p> <p> „p“ sollte in den meisten Fällen ausreichen.</p> </td>
  </tr>
  <tr>
   <td>table</td>
   <td>nt:unstructured</td>
   <td><p>Definiert das Verhalten beim Einfügen von Tabellen.<br /> </p> <p>Dieser Knoten muss über die Eigenschaft <code>allow</code> (Typ <code>Boolean</code>) verfügen, um festzulegen, ob das Einfügen von Tabellen zulässig ist.</p> <p>If <code>allow</code> is set to <code>false</code>, you must specify the property <code>ignoreMode</code> (type<code> String</code>) to define how pasted table content is handled. Valid values for <code>ignoreMode</code> are:</p>
    <ul>
     <li><code>remove</code>: Entfernt Tabelleninhalte.</li>
     <li><code>paragraph</code>: Wandelt Tabellenzellen in Absätze um.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>list</td>
   <td>nt:unstructured</td>
   <td><p>Definiert das Verhalten beim Einfügen von Listen.<br /> </p> <p>Muss über die Eigenschaft <code>allow</code> (Typ <code>Boolean</code>) verfügen, um festzulegen, ob das Einfügen von Listen zulässig ist.</p> <p>If <code>allow</code> is set to <code>false</code>, you must specify the property <code>ignoreMode</code> (type <code>String</code>) to define how to handle any list content pasted. Valid values for <code>ignoreMode</code> are:</p>
    <ul>
     <li><code>remove</code>: Entfernt den Inhalt der Liste.</li>
     <li><code>paragraph</code>: Wandelt Listen in Absätze um.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Example of a valid `htmlPasteRules` structure:

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
* Geben Sie die Speicherorte der Stylesheets an.
* Geben Sie die einzelnen Stile an, die in der Dropdown-Liste „Stil“ auswählbar sein sollen.

Für spätere (Neu-) Konfigurationen, beispielsweise um weitere Stile hinzuzufügen, befolgen Sie nur die Anweisungen zum Verweisen auf ein neues Stylesheet und zum Angeben zusätzlicher Stile.

>[!NOTE]
>
>Auch für [Tabellen oder Tabellenzellen können Stile definiert werden](configure-rich-text-editor-plug-ins.md#tablestyles). Diese Konfigurationen erfordern unterschiedliche Vorgehensweisen.

### Aktivieren der Dropdown-Liste „Stil“{#styleselectorlist}

Aktivieren Sie dazu das styles-Plug-in.

1. In your component, navigate to the node `<rtePlugins-node>/styles`. Erstellen Sie die Knoten, falls diese noch nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).
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

>[!NOTE]
>
>Wenn Sie den RTE in einem Dialogfeld verwenden (klassische Benutzeroberfläche), können Sie Stylesheets festlegen, die optimal auf die Rich-Text-Bearbeitung abgestimmt sind. Aufgrund technischer Einschränkungen geht der CSS-Kontext im Editor verloren, daher sollten Sie diesen Kontext zur Verbesserung des WYSIWYG-Verhaltens emulieren.
>
>Der Rich-Text-Editor verwendet ein Container-DOM-Element mit einer ID von `CQrte`, die verwendet werden kann, um verschiedene Stile für die Anzeige und Bearbeitung bereitzustellen:
>
>
```
>#CQ td {
> // defines the style for viewing
> }
>```
>
>
```
>#CQrte td {
> // defines the style for editing
> }
>```

### Festlegen von Stilen, die in der Popup-Liste verfügbar sein sollen {#stylesindropdown}

1. In the component definition, navigate to the node `<rtePlugins-node>/styles`, as created in [Enabling the style drop-down selector](#styleselectorlist).
1. Erstellen Sie unter dem Knoten `styles` einen neuen Knoten (ebenfalls mit dem Namen `styles`), unter dem die zur Verfügung zu stellende Liste gespeichert werden soll:

   * **Name** `styles`
   * **Typ** `cq:WidgetCollection`

1. Erstellen Sie einen neuen Knoten unter dem Knoten `styles`, um einen einzelnen Stil zu repräsentieren:

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

Autoren, die AEM zum Erstellen von japanischen Sprachinhalten verwenden, können einen Stil auf Zeichen anwenden, um Zeilenumbrüche zu vermeiden, bei denen kein Umbruch erforderlich ist. Dadurch können Autoren die Sätze an der gewünschten Position umbrechen. Der Stil für diese Funktion basiert auf der CSS-Klasse, die im CSS-Stylesheet vordefiniert ist.

>[!NOTE]
>
>Für diese Funktion ist mindestens AEM 6.5 Service Pack 1 erforderlich.

Führen Sie folgende Schritte aus, um den Stil zu erstellen, den Autoren auf Japanisch anwenden können:

1. Erstellen Sie einen neuen Knoten unter dem Stil-Knoten. Siehe [Festlegen eines neuen Stils](#stylesindropdown).
   * Name: `jpn-word-wrap`
   * Typ: `nt:unstructure

1. Fügen Sie diesem Knoten die Eigenschaft `cssName` hinzu, um auf die CSS-Klasse zu verweisen. Dieser Klassenname ist ein reservierter Name für die japanische Wortumbruchfunktion.
   * Name: `cssName`
   * Typ: `String`
   * Wert: `jpn-word-wrap` (ohne vorherige Angaben `.`)

1. Fügen Sie den Text der Eigenschaft demselben Knoten hinzu. Der Wert ist der Name des Stils, den die Autoren beim Auswählen des Stils sehen.
   * Name: `text`
*Type: `String`
   * `String`

1. Wert: `Japanese word-wrap`](#locationofstylesheet)

   ```css
   .text span.jpn-word-wrap {
       display:inline-block;
   }
   .is-edited span.jpn-word-wrap {
       background-color: #ffddff;
   }
   ```

   Erstellen Sie ein Stylesheet und geben Sie seinen Pfad an. Siehe [Speicherort des Stylesheets angeben](#locationofstylesheet). Fügen Sie dem Stylesheet den folgenden Inhalt hinzu. Ändern Sie die Hintergrundfarbe wie gewünscht.

## ![Stylesheet zum Bereitstellen der japanischen Wortumbruchfunktion für Autoren verfügbar](assets/rte_jpwordwrap_stylesheet.jpg)

Konfigurieren der Absatzformate {#paraformats}`paraformat`

>Any text authored in RTE is placed within a block tag, the default being `<p>`. By enabling the `paraformat` plug-in, you specify additional block tags that can be assigned to paragraphs, using a drop-down selection list. Absatzformate bestimmen den Absatztyp durch Zuweisung des richtigen Block-Tags. Der Autor kann diese mithilfe der Format-Auswahl auswählen und zuweisen. Die Beispiel-Block-Tags beinhalten u. a. den Standardabsatz „&lt;p>“ und die Kopfzeilen „&lt;h1>“, „&lt;h2>“ usw.
>
>[!CAUTION]

>[!NOTE]Dieses Plug-in eignet sich nicht für Inhalte mit komplexer Struktur, beispielsweise Listen und Tabellen.
>
>[!NOTE]

Wenn ein Block-Tag, beispielsweise ein &lt;hr>-Tag, keinem Absatz zugewiesen werden kann, handelt es sich um keinen zulässigen Anwendungsfall für ein paraformat-Plug-in.

* Wenn das paraformat-Plug-in zum ersten Mal aktiviert wird, sind keine Standabsatzformate verfügbar. Die Popup-Liste ist leer. Gehen Sie wie folgt vor, um Absatzformate für Autoren bereitzustellen:
* Aktivieren Sie die Dropdown-Auswahl-Liste Format.

Legen Sie die Block-Tags fest, die als Absatzformate in der Dropdown-Liste ausgewählt werden können.

### Für spätere (Neu-)Konfigurationen, beispielsweise um weitere Formate hinzuzufügen, folgen Sie nur dem entsprechenden Teil der Anweisungen.{#formatselectorlist}

Aktivieren der Dropdown-Auswahl „Format“. {#formatselectorlist}

1. Aktivieren Sie zunächst das paraformat-Plug-in:`<rtePlugins-node>/paraformat`[](#activateplugin)
1. In your component, navigate to the node `<rtePlugins-node>/paraformat`. Erstellen Sie die Knoten, falls diese noch nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).

   * Create the `features` property on the `paraformat` node:`features`
   * **Name** `features`
   * **Typ** `String`

>**Wert** `*` (Sternchen)
[!NOTE]
* Wenn das Plug-in nicht weiter konfiguriert ist, werden die folgenden Standardformate aktiviert:`<p>`
* Absatz ( `<p>`)
* Überschrift 1 ( `<h1>`)
* Überschrift 2 ( `<h2>`)



>Überschrift 3 ( `<h3>`)
[!CAUTION]****

### Entfernen Sie beim Konfigurieren der Absatzformate des RTE nicht das Absatz-Tag „&lt;p>“ als Formatierungsoption. If the `<p>` tag is removed, then the content author can not select the **Paragraph formats** option even if there are additional formats configured.

Angeben der verfügbaren Absatzformate {#paraformatsindropdown}

1. Absatzformate werden wie folgt zur Auswahl bereitgestellt:`<rtePlugins-node>/paraformat`[](#styleselectorlist)
1. In the component definition, navigate to the node `<rtePlugins-node>/paraformat`, as created in [Enabling the format drop-down selector](#styleselectorlist).

   * Erstellen Sie unter dem Knoten `paraformat` einen neuen Knoten, unter dem die Liste der Formate gespeichert werden soll:**`formats`
   * **Name** `formats`

1. **Typ** `cq:WidgetCollection`

   * Erstellen Sie einen neuen Knoten unter dem Knoten `formats`, der die Details für ein einzelnes Format beinhaltet:**
   * **Name:** Sie können einen Namen angeben, dieser sollte jedoch dem Format entsprechen (z. B. myparagraph, myheading1).`nt:unstructured`

1. **Typ** `nt:unstructured`

   * **Fügen Sie diesem Knoten die Eigenschaft hinzu, um das verwendete Block-Tag zu definieren:**`tag`
   * **Name** `tag`
   * **Typ** `String`

      **Wert:** Das Block-Tag für das Format (z. B. p, h1, h2 usw.)

1. Es ist nicht notwendig, die abgrenzenden spitzen Klammern einzugeben.

   * **Fügen Sie demselben Knoten eine weitere Eigenschaft hinzu, damit ein beschreibender Text in der Dropdown-Liste angezeigt wird:**`description`
   * **Name** `description`
   * **Typ** `String`

1. **Wert:** der beschreibende Text für dieses Format, z. B. „Absatz“, „Überschrift 1“, „Überschrift 2“ usw. Dieser Text wird in der Auswahlliste „Format“ angezeigt.

   Speichern Sie die Änderungen.

>[!CAUTION]Wiederholen Sie die Schritte für jedes erforderliche Format.
[!CAUTION]`<h1>``<h2>``<h3>``<p>`

## If you define custom formats, the default formats (`<p>`, `<h1>`, `<h2>`, and `<h3>`) are removed. Re-create `<p>` format as it is the default format.

Konfigurieren von Sonderzeichen {#spchar}`specialchars`

Wenn in einer AEM-Standardinstallation das `misctools`-Plug-in für Sonderzeichen (`specialchars`) aktiviert wird, ist sofort eine Standardauswahl verfügbar, wie beispielsweise Copyright- und Markenzeichensymbole.

>[!CAUTION]Sie können den RTE aber auch so konfigurieren, dass Ihre eigene Auswahl an Zeichen zur Verfügung steht, entweder indem Sie einzelne Zeichen oder eine ganze Sequenz definieren.
[!CAUTION]

### Durch das Hinzufügen eigener Sonderzeichen wird die Standardauswahl überschrieben. Definieren Sie diese Zeichen bei Bedarf in Ihrer eigenen Auswahl (neu).{#definesinglechar}

1. Definieren einzelner Zeichen {#definesinglechar}[](#activateplugin)
1. In your component, navigate to the node `<rtePlugins-node>/misctools`. Erstellen Sie die Knoten, falls diese noch nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).

   * Create the `features` property on the `misctools` node:`features`
   * **Name** `features`
   * **Typ** `String[]`

      **Wert** `specialchars`

1.     (or `String / *` if applying all features for this plug-in)

   * Erstellen Sie unter `misctools` einen Knoten, um die Sonderzeichenkonfigurationen zu speichern:**`specialCharsConfig`
   * **Name** `specialCharsConfig`

1. **Typ** `nt:unstructured`

   * Erstellen Sie unter `specialCharsConfig` einen weiteren Knoten, unter dem die Liste der Zeichen gespeichert werden soll:**`chars`
   * **Name** `chars`

1. **Typ** `nt:unstructured`

   * Fügen Sie unter `chars` einen neuen Knoten hinzu, unter dem eine individuelle Zeichendefinition gespeichert werden soll:**
   * **Name:** Sie können einen Namen angeben, dieser sollte jedoch das Zeichen widerspiegeln, wie beispielsweise „half“ (Halb).`nt:unstructured`

1. **Typ** `nt:unstructured`

   * **Fügen Sie diesem Knoten die folgende Eigenschaft hinzu:**`entity`
   * **Name** `entity`
   * **Typ** `String`

1. **Wert** der HTML-Darstellung des erforderlichen Zeichens; zum Beispiel `&189;` für die Bruchteile eine Hälfte.

Speichern Sie die Änderungen.

![In CRXDE wird nach dem Speichern der Eigenschaft das angezeigte Zeichen angezeigt. Siehe „half“ im unten aufgeführten Beispiel. Wiederholen Sie die obigen Schritte, um weitere Sonderzeichen für Autoren verfügbar zu machen.](assets/chlimage_1-106.png "")

### ![Fügen Sie in CRXDE ein einzelnes Zeichen hinzu, das in der RTE-](assets/chlimage_1-106.png "Symbolleiste verfügbar gemacht werden soll. Fügen Sie in CRXDE ein einzelnes Zeichen hinzu, das in der RTE-Symbolleiste verfügbar gemacht werden soll.")

1. Definieren von Zeichenbereichen {#definerangechar}](#definingasinglecharacter)
1. Führen Sie dazu die Schritte 1 bis 3 im Abschnitt [Definieren eines einzelnen Zeichens](#definingasinglecharacter) aus.

   * Fügen Sie unter `chars` einen neuen Knoten hinzu, unter dem die Definition des Zeichenbereichs gespeichert werden soll:**
   * **Name:** Sie können einen Namen angeben, dieser sollte jedoch den Zeichenbereich widerspiegeln, wie beispielsweise „pencils“.`nt:unstructured`

1. **Typ** `nt:unstructured`

   * **Fügen Sie unter diesem Knoten (der entsprechend dem Sonderzeichenbereich benannt wurde) die folgenden beiden Eigenschaften hinzu:**`rangeStart`      **Name** `rangeStart`

      **Typ** `Long`
-ERR:REF-NOT-FOUND-

   *       **Name** `rangeEnd`

      **Typ** `Long`
-ERR:REF-NOT-FOUND-

1. 

   Speichern Sie die Änderungen.

   ![Wenn Sie zum Beispiel einen Bereich von 9998 bis 10000 definieren, erhalten Sie die folgenden Zeichen:](assets/chlimage_1-107.png)

   ![Definieren Sie in CRXDE einen Zeichenbereich, um ihn in der RTE-Symbolleiste verfügbar zu machen.](assets/chlimage_1-107.png)

   *Abbildung: Definieren Sie in CRXDE einen Zeichenbereich, der in RTE verfügbar gemacht werden soll.*")

## ![Sonderzeichen in RTE werden Autoren in einem Popup-](assets/rtepencil.png "Fenster angezeigt. Sonderzeichen in RTE werden Autoren in einem Popup-Fenster angezeigt")

Konfigurieren von Tabellenstilen {#tablestyles}

>[!NOTE]Neben der Definition von Stilen, die auf normalen Text angewendet werden, können Sie auch Stile (einen separaten Satz) für eine ganze Tabelle oder einzelne Tabellenzellen definieren. Diese können dann im Dialogfeld „Zellen-Eigenschaften“ oder „Tabelleneigenschaften“ im Auswahlfeld „Stil“ ausgewählt werden. Diese Stile sind nur verfügbar, wenn eine Tabelle in einer Textkomponente (oder einer abgeleiteten Komponente davon) und nicht in der standardmäßigen Tabellenkomponente bearbeitet wird.
[!NOTE]

>[!NOTE]Sie können Stile für Tabellen und Tabellenzellen nur in der klassischen Benutzeroberfläche definieren.
[!NOTE]

1. Die Funktion zum Kopieren und Einfügen von Tabellen in oder aus der RTE-Komponente ist Browser-abhängig. Sie wird nicht standardmäßig für alle Browser unterstützt. Je nach Tabellenstruktur und Browser können die Ergebnisse unterschiedlich ausfallen. Wenn Sie beispielsweise eine Tabelle in einer RTE-Komponente in Mozilla Firefox in der Benutzeroberfläche &quot;Klassisch&quot;und &quot;Touch&quot;kopieren und einfügen, wird das Layout der Tabelle nicht beibehalten.`<rtePlugins-node>/table`[](#activateplugin)
1. Navigieren Sie innerhalb Ihrer Komponente zum Knoten `<rtePlugins-node>/table`. Erstellen Sie die Knoten, falls diese noch nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).

   * Create the `features` property on the `table` node:`features`
   * **Name** `features`
   * **Typ** `String`
   >**Wert** `*`
   [!NOTE]
   * Wenn Sie nicht alle Tabellen-Features aktivieren möchten, erstellen Sie die `features`-Eigenschaft wie folgt:**`String[]`

   * **Typ** `String[]`
      * **Wert(e):** Nach Bedarf einen oder beide der folgenden Werte:
      * `table` die Bearbeitung von Tabelleneigenschaften zu ermöglichen; einschließlich der Stile.


1. `cellprops` , um die Bearbeitung von Zelleneigenschaften einschließlich der Stile zu ermöglichen.](#locationofstylesheet)[](#textstyles)
1. Definieren Sie den Speicherort von CSS-Stylesheets, um auf diese zu verweisen. Lesen Sie den Abschnitt [Festlegen des Speicherorts des Stylesheets](#locationofstylesheet), da die Vorgehensweise hier dieselbe ist wie beim Definieren von [Stilen für Text](#textstyles). Der Speicherort wurde möglicherweise bereits beim Definieren anderer Stile definiert.

   * Erstellen Sie unter dem Knoten `table` die folgenden neuen Knoten (nach Bedarf):**

      * So definieren Sie Stile für die komplette Tabelle (verfügbar unter **Tabelleneigenschaften**):`tableStyles`
      * **Name** `tableStyles`
   * **Typ** `cq:WidgetCollection`

      * So definieren Sie Stile für einzelne Tabellenzellen (verfügbar unter **Zellen-Eigenschaften**):`cellStyles`
      * **Name** `cellStyles`


1. **Typ** `cq:WidgetCollection`

   * Create a new node (under the `tableStyles` or `cellStyles` node as appropriate) to represent an individual style:
   * **Name** Sie können den Namen angeben, er sollte jedoch den Stil widerspiegeln.`nt:unstructured`

1. **Typ** `nt:unstructured`

   * Erstellen Sie in diesem Knoten die folgenden Eigenschaften:

      * **So definieren Sie den CSS-Stil, auf den verwiesen werden soll:**`cssName`
      * **Name** `cssName`
      * **Typ** `String``cssClass``.cssClass`
   * **Wert** des Namens der CSS-Klasse (ohne vorherige `.`z. B. `cssClass` anstelle von `.cssClass`)

      * **So definieren Sie einen beschreibenden Text, der im Dropdown-Selektor angezeigt werden soll:**`text`
      * **Name** `text`
      * **Typ** `String`


1. **Wert:** Der Text, der in der Auswahlliste angezeigt werden soll

Speichern Sie alle Änderungen.

### Wiederholen Sie die obigen Schritte für jeden erforderlichen Stil.{#hiddenheader}

Konfigurieren von ausgeblendeten Kopfzeilen in Tabellen, um die Zugänglichkeit zu verbessern {#hiddenheader}

Manchmal kann es sein, dass Sie Datentabellen ohne visuellen Text in einer Spaltenkopfzeile erstellen, da Sie voraussetzen, dass sich der Zweck der Kopfzeile durch die visuelle Beziehung der Spalte mit anderen Spalten ergibt. In diesem Fall ist es erforderlich, dass Sie ausgeblendeten inneren Text innerhalb der Zelle in der Kopfzeilenzelle bereitstellen, damit Bildschirmlesehilfen und andere unterstützende Technologien Benutzern mit unterschiedlichen Bedürfnissen helfen können, den Zweck der Spalte zu verstehen.

* `hiddenHeaderEditingCSS`Um die Zugänglichkeit in solchen Fällen zu verbessern, unterstützt der RTE ausgeblendete Kopfzeilenzellen. Darüber hinaus stellt er Konfigurationseinstellungen bezüglich der ausgeblendeten Kopfzeilen in Tabellen bereit. Mit diesen Einstellungen können Sie CSS-Stile auf ausgeblendete Kopfzeilen im Bearbeitungs- und Vorschau-Modus anwenden. Damit Autoren ausgeblendete Kopfzeilen im Bearbeitungsmodus besser identifizieren können, fügen Sie die folgenden Parameter in Ihren Code ein:
* `hiddenHeaderEditingCSS`: Gibt den Namen der CSS-Klasse an, die bei der Bearbeitung von RTE auf die Zelle der ausgeblendeten Kopfzeile angewendet wird.

`hiddenHeaderEditingStyle`: Gibt eine Stilzeichenfolge an, die bei der Bearbeitung der RTE auf die Zelle der ausgeblendeten Kopfzeile angewendet wird.

Wenn Sie sowohl die CSS- als auch die Stilzeichenfolge im Code angeben, hat die CSS-Klasse Vorrang vor der Stilzeichenfolge. Sie überschreibt möglicherweise Konfigurationsänderungen, die mittels der Stilzeichenfolge vorgenommen werden.

* `hiddenHeaderClassName`Um Autoren bei der Anwendung von CSS auf ausgeblendete Header im Vorschau-Modus zu unterstützen, können Sie die folgenden Parameter in Ihren Code einschließen:
* `hiddenHeaderClassName`: Gibt den Namen der CSS-Klasse an, die im Vorschaumodus auf die ausgeblendete Kopfzeilenzelle angewendet wird.

`hiddenHeaderStyle`: Gibt eine Stilzeichenfolge an, die im Vorschaumodus auf die ausgeblendete Kopfzeilenzelle angewendet wird

## Wenn Sie sowohl die CSS- als auch die Stilzeichenfolge im Code angeben, hat die CSS-Klasse Vorrang vor der Stilzeichenfolge. Sie überschreibt möglicherweise Konfigurationsänderungen, die mittels der Stilzeichenfolge vorgenommen werden.{#adddict}

Hinzufügen von Wörterbüchern für die Rechtschreibprüfung {#adddict}`/de/`

>Wenn das spellcheck-Plug-in aktiviert wird, verwendet der RTE Wörterbücher für jede entsprechende Sprache. Diese werden dann entsprechend der Sprache der Website ausgewählt, indem entweder die language-Eigenschaft der Unterstruktur verwendet oder die Sprache aus der URL extrahiert wird. the `/en/` branch is checked as English, the `/de/` branch as German.
[!NOTE]

Die Meldung „Rechtschreibprüfung fehlgeschlagen.“ wird angezeigt, wenn versucht wird, eine Überprüfung für eine Sprache durchzuführen, die nicht installiert ist.

* Eine AEM-Standardinstallation umfasst die Wörterbücher für:
* Amerikanisches Englisch (en_us)

>[!NOTE]Britisches Englisch (en_gb)
[!NOTE]

The standard dictionaries are located at `/libs/cq/spellchecker/dictionaries`, along with the appropriate readme files. Diese Dateien sollten nicht geändert werden.

1. Gehen Sie wie folgt vor, um ggf. weitere Wörterbücher hinzuzufügen.[-ERR:REF-NOT-FOUND-
1. 

   >[!CAUTION]Wählen Sie die gewünschte Sprache aus und laden Sie die ZIP-Datei mit den Rechtschreibedefinitionen herunter. Entpacken Sie den Inhalt des Archivs in Ihrem Dateisystem.
   [!CAUTION]

1. Nur Wörterbücher im `MySpell`-Format für OpenOffice.org v2.0.1 bzw. frühere Versionen werden unterstützt. Da die Wörterbücher jetzt Archivdateien sind, ist es ratsam, eine vollständige Prüfung nach dem Herunterladen durchzuführen.`de_de.dic`
1. Suchen Sie nach den *.aff- und *.dic-Dateien. Der Dateiname darf nur Kleinbuchstaben aufweisen. Zum Beispiel `de_de.aff` und `de_de.dic`.

>Load the .aff and .dic files in the repository at `/apps/cq/spellchecker/dictionaries`.
[!NOTE]
Die RTE-Rechtschreibprüfung ist nur auf Abruf verfügbar. Sie wird nicht automatisch ausgeführt, wenn Sie beginnen, Text einzugeben.
Aktivieren Sie die Rechtschreibprüfung, indem Sie in der Symbolleiste auf die Schaltfläche „Rechtschreibprüfung“ tippen/klicken. Der RTE überprüft die Rechtschreibprüfung der Wörter und markiert falsch geschriebene Wörter.

## Wenn Sie eine Änderung annehmen, die die Rechtschreibprüfung vorschlägt, ändert sich der Status des Textes und das falsch geschriebene Wort ist nicht länger markiert. Um die Rechtschreibprüfung auszuführen, tippen/klicken Sie erneut auf die Rechtschreibprüfung.{#undohistory}

Konfigurieren der Verlaufsgröße für die Aktionen „Rückgängig“ und „Wiederholen“{#undohistory}

1. Der RTE bietet Autoren die Möglichkeit, bei Bedarf die letzten Bearbeitungsschritte rückgängig zu machen bzw. zu wiederholen. Standardmäßig werden im Verlauf 50 Schritte gespeichert. Sie können diesen Wert nach Bedarf konfigurieren.`<rtePlugins-node>/undo`[](#activateplugin)
1. Navigieren Sie innerhalb Ihrer Komponente zum Knoten `<rtePlugins-node>/undo`. Erstellen Sie diese Knoten, falls sie nicht bereits vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).

   * Erstellen Sie im `undo`-Knoten die folgende Eigenschaft:**`maxUndoSteps`
   * **Name** `maxUndoSteps`
   * **Typ** `Long`

1. **Wert:** Die Anzahl an rückgängig zu machenden Schritten, die Sie im Verlauf speichern wollen. Standard: 50. Verwenden Sie diese Option, `0` um Rückgängig/Wiederholen vollständig zu deaktivieren.

## Speichern Sie die Änderungen.{#tabsize}

Konfigurieren der Tabulator-Schrittweite {#tabsize}

Wenn das Tabulatorzeichen innerhalb eines beliebigen Texts gedrückt wird, wird eine vordefinierte Anzahl von Leerzeichen eingefügt. Standardmäßig werden drei geschützte Leerzeichen und ein normales Leerzeichen eingefügt.

1. So definieren Sie die Tabulator-Schrittweite:`<rtePlugins-node>/keys`[](#activateplugin)
1. In your component, navigate to the node `<rtePlugins-node>/keys`. Erstellen Sie die Knoten, falls diese noch nicht vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).

   * Erstellen Sie im `keys`-Knoten die folgende Eigenschaft:**`tabSize`
   * **Name** `tabSize`
   * **Typ** `String`

1. **Wert:** Die Anzahl an für den Tabulator verwendeten Leerzeichen.

## Speichern Sie die Änderungen.{#indentmargin}

Festlegen des Einzugsrands {#indentmargin}

>[!NOTE]Wenn die Einzugsfunktion aktiviert ist (Standardeinstellung), können Sie die Einzugsgröße definieren:
[!NOTE]

1. Diese Einzugsgröße wird nur auf Absätze (Blöcke) des Texts angewendet. Sie wirkt sich nicht auf den Einzug von tatsächlichen Listen aus.`<rtePlugins-node>/lists`[](#activateplugin)
1. Navigieren Sie innerhalb Ihrer Komponente zum Knoten `<rtePlugins-node>/lists`. Erstellen Sie diese Knoten, falls sie nicht bereits vorhanden sind. Weitere Informationen finden Sie unter [Aktivieren von Plug-ins](#activateplugin).

   * On the `lists` node create the `identSize` parameter:`identSize`
   * **Name**: `identSize`
   * **Typ**: `Long`

## **Wert:** Die Anzahl an Pixel, die für den Einzugsrand erforderlich sind.

>Konfigurieren der Höhe des bearbeitbaren Bereichs {#editablespace}
[!NOTE]

Dies ist nur bei Verwendung der RTE in einem Dialogfeld möglich (nicht ersetzende Bearbeitung in der klassischen Benutzeroberfläche).

1. Sie können die Höhe des bearbeitbaren Bereichs definieren, der innerhalb des Komponenten-Dialogfelds angezeigt wird:`../items/text`

   * On the `../items/text` node in the dialog definition for the component, create a new property:**`height`
   * **Name** `height`
   * **Typ** `Long`
   >**Wert:** Die Höhe der Bearbeitungsfläche in Pixeln.
   [!NOTE]

1. Dies wirkt sich nicht auf die Höhe des Dialogfelds aus.

## Speichern Sie die Änderungen.{#linkstyles}

Konfigurieren von Stilen und Protokollen für Links {#linkstyles}

* Wenn Sie Links in AEM einfügen, können Sie Folgendes definieren:
* Die zu verwendenden CSS-Stile

Die Protokolle, die automatisch akzeptiert werden

1. Um zu konfigurieren, wie Links in AEM von einem anderen Programm aus hinzugefügt werden, müssen Sie HTML-Regeln definieren.
1. Suchen Sie mithilfe von CRXDE Lite nach der Textkomponente für Ihr Projekt.`<rtePlugins-node>``<rtePlugins-node>`

   * Create a new node at the same level as `<rtePlugins-node>`, that is, create the node under the parent node of `<rtePlugins-node>`:`htmlRules`
   * **Name** `htmlRules`
   >**Typ** `nt:unstructured`
   [!NOTE]
   * The `../items/text` node has the property:**`xtype`
   * **Name** `xtype`
   * **Typ** `String`
   **Wert** `richtext`
   * The location of the `../items/text` node can vary, depending on the structure of your dialog; two examples include:
   * `/apps/myProject>/components/text/dialog/items/text`


1. `/apps/<myProject>/components/text/dialog/items/panel/items/text`

   * Erstellen Sie unter `htmlRules` einen neuen Knoten.**`links`
   * **Name** `links`

1. **Typ** `nt:unstructured`

   * Definieren Sie unter dem `links`-Knoten die benötigten Eigenschaften:

      * **CSS-Stil für interne Links:**`cssInternal`
      * **Name** `cssInternal`
      * **Typ** `String``.cssClass`
   * **Wert:** Der Name der CSS-Klasse (ohne „.“ voranzustellen; for example, `cssClass` instead of `.cssClass`)

      * **CSS-Stil für externe Links**`cssExternal`
      * **Name** `cssExternal`
      * **Typ** `String``.cssClass`
   * **Wert:** Der Name der CSS-Klasse (ohne „.“ voranzustellen; for example, `cssClass` instead of `.cssClass`)

      * Array of valid **protocols** (including https://, https:// file://, mailto:, amongst others)`protocols`
      * **Name** `protocols`
      * **Typ** `String[]`
   * **Wert(e):** Ein oder mehrere Protokolle****

      * **defaultProtocol** (Eigenschaft des Typs **String**): Protokoll, das verwendet wird, wenn der Benutzer keines explizit festlegt
      * **Name** `defaultProtocol`
      * **Typ** `String`
   * **Wert(e):** Ein oder mehrere Standardprotokolle

      * **Definition der Art, wie das Zielattribut eines Links verarbeitet werden soll Erstellen Sie einen neuen Knoten:**`targetConfig`
      * **Name** `targetConfig`
      **Typ** `nt:unstructured`

      * Definieren Sie im Knoten `targetConfig` die erforderlichen Eigenschaften:

         * **Legen Sie den Zielmodus fest:**`mode`
         * **Name** `mode`
         * **Typ** `String`)

            * **Wert(e)**:

               `auto`: bedeutet, dass eine automatische Zielgruppe gewählt wird`targetInternal`

            * (durch die `targetExternal` Eigenschaft für externe Links oder `targetInternal` für interne Links angegeben).
            * `manual` : In diesem Kontext unzulässig
      * `blank` : In diesem Kontext unzulässig

         * **Das Ziel für interne Links:**`targetInternal`
         * **Name** `targetInternal`
         * **Typ** `String`
      * **Zielgruppe für interne Links bewerten** (nur verwenden, wenn der Modus `auto`)

         * **Das Ziel für externe Links:**`targetExternal`
         * **Name** `targetExternal`
         * **Typ** `String`








1. **Wert:** Das Ziel für externe Links (nur verwenden, wenn der Modus `auto` aktiv ist)
