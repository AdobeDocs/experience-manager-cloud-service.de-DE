---
title: Konfigurieren Sie den Rich-Text-Editor, um Inhalte [!DNL Adobe Experience Manager] als Cloud Service zu erstellen.
description: Rich-Text-Editor konfigurieren, um Inhalte [!DNL Adobe Experience Manager] als Cloud Service zu erstellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 739dde6f9a6a7f4fe773e27e53f23a395f2881dc
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 43%

---


# Konfigurieren des Rich-Text-Editors {#configure-the-rich-text-editor}

Der Rich Text Editor (RTE) bietet Autoren eine breite Palette von Funktionen zum Bearbeiten von Textinhalten. Symbole, Auswahlfelder, Symbolleiste und Menüs werden für eine WYSIWYG-Textbearbeitung bereitgestellt. Administratoren konfigurieren die RTE, um die in den Authoring-Komponenten verfügbaren Funktionen zu aktivieren, zu deaktivieren und zu erweitern. Erfahren Sie, wie Autoren RTE zum Authoring von [Webinhalten](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md) verwenden.

Die RTE-Konzepte und -Schritte, die für ihre Konfiguration erforderlich sind, sind unten aufgeführt.

| RTE-Konzepte verstehen | Erforderliche Funktionen aktivieren | Konfigurieren einzelner Funktionen |
|---|---|---|
| [Benutzeroberfläche](#understand-rte-ui) | [Konfigurationsspeicherorte verstehen und festlegen](#understand-the-configuration-paths-and-locations) | [Plug-ins konfigurieren](#enable-rte-functionalities-by-activating-plug-ins) |
| [Arten von Bearbeitungsmodi](#editingmodes) | [Aktivieren von Plug-Ins](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin) | [Festlegen von Funktionseigenschaften](#aboutplugins) |
| [Informationen zu Plug-ins](#aboutplugins) | [RTE-Werkzeugleisten konfigurieren](#dialogfullscreen) | [Konfigurieren der Einfügemodi](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) |

## Verstehen der Benutzeroberfläche, die Autoren zur Verfügung steht {#understand-rte-ui}

Die RTE-Oberfläche Angebot ein [reaktionsfähiges Design](/help/sites-cloud/authoring/features/responsive-layout.md) für die Authoring-Umgebung. Die Oberfläche ist für die Verwendung auf Touch- und Desktop-Geräten konzipiert.

![Rich-Text-Editor, Symbolleiste](assets/rte-toolbar-full-screen-mode.png)

*Abbildung: Rich Text Editor-Symbolleiste mit allen verfügbaren Optionen.*

Die Symbolleiste enthält die Optionen für das WYSIWYG-Authoring-Erlebnis. [!DNL Experience Manager] Administratoren können die in der Symbolleiste auf der Benutzeroberfläche verfügbaren Optionen konfigurieren. In [!DNL Experience Manager]sind standardmäßig umfassende Bearbeitungsoptionen verfügbar. Entwickler können die Bearbeitung anpassen, [!DNL Experience Manager] um weitere Optionen hinzuzufügen.

## Verschiedene Bearbeitungsmodi {#editingmodes}

Authors can create and edit textual content in [!DNL Experience Manager] using the different modes of components. Die Symbolleistenoptionen für das Erstellen und Formatieren von Inhalten und das Benutzererlebnis von RTE-aktivierten Komponenten in verschiedenen Bearbeitungsmodi variieren je nach RTE-Konfiguration.

| Bearbeitungsmodus | Bearbeitungsbereich | Für die Aktivierung empfohlene Funktionen |
|--- |--- |--- |
| Inline | Bearbeitung im Kontext für schnelle, geringfügige Änderungen; Formatieren ohne Öffnen eines Dialogfelds. | Minimale RTE-Funktionen. |
| RTE im Vollbildmodus | Füllt die gesamte Seite aus. | Alle erforderlichen RTE-Funktionen. |
| Dialogfeld | Dialogfeld, das oberhalb des Seiteninhalts angezeigt wird, jedoch nicht die gesamte Seite einnimmt. | Aktivieren Sie Funktionen. |
| Dialogfeld im Vollbildmodus | wie Vollbildmodus; enthält Felder des Dialogfelds neben RTE. | Alle erforderlichen RTE-Funktionen. |

>[!NOTE]
>
>Die Funktion zum Bearbeiten der Quelle ist im Inline-Bearbeitungsmodus nicht verfügbar. Sie können Bilder nicht im Vollbildmodus ziehen. Alle anderen Funktionen sind in allen Modi verfügbar.

### Inline-Bearbeitung {#inline-editing}

Um den Inhalt auf einer Seite zu bearbeiten, öffnen Sie den Inhalt mit einem langsamen Klick auf die Dublette. Dazu steht Ihnen eine kompakte Symbolleiste mit grundlegenden Optionen zur Verfügung.

![Inline-Bearbeitung mit grundlegenden Optionen in der Symbolleiste](assets/inline-editing-mode-basic-options.png)

*Abbildung: Inline-Bearbeitung mit grundlegenden Optionen in der Symbolleiste.*

### Full-screen editing {#full-screen-editing}

[!DNL Experience Manager] Komponenten können in einer Vollbildansicht geöffnet werden, die den Seiteninhalt ausblendet und den verfügbaren Bildschirm einnimmt. Erwägen Sie die Vollbildbearbeitung, um eine detaillierte Version der Inline-Bearbeitung zu bearbeiten, da sie die meisten Bearbeitungsoptionen Angebot. Sie können sie öffnen, indem Sie auf ![Symbol klicken, um RTE im Vollbildmodus](assets/rte_fullscreen.png)zu öffnen, und zwar in der Kompaktsymbolleiste, wenn Sie den Inline-Bearbeitungsmodus verwenden.

Im Vollbildmodus des Dialoges stehen neben einer detaillierten RTE-Symbolleiste auch die Optionen und Komponenten zur Verfügung, die in einem Dialogfeld verfügbar sind. Dies gilt nur für ein Dialogfeld, das neben anderen Komponenten einen RTE enthält.

![Die detaillierte RTE-Symbolleiste beim Bearbeiten im Vollbildmodus](assets/rte-toolbar-full-screen-mode.png)

*Abbildung: Die detaillierte RTE-Symbolleiste beim Bearbeiten im Vollbildmodus.*

### Bearbeitung in einem Dialogfeld {#dialog-editing}

Wenn Sie auf eine Komponente doppelklicken, öffnet sich ein Dialogfeld zur Bearbeitung des Inhalts. Das Dialogfeld öffnet sich oben auf der jeweiligen Seite. In bestimmten Fällen kann dieses Dialogfeld auch als Popup-Fenster geöffnet werden. Dies ist beispielsweise der Fall, wenn eine Textkomponente Teil einer Spalte in einem mehrspaltigen Seitenlayout ist und zu wenig Platz für die Anzeige des Dialogfelds vorhanden ist.

![Dialogbearbeitungsmodus](assets/dialog_editing_modetouchui.png)

*Abbildung: Dialogfeldbearbeitungsmodus.*

## RTE-Plug-ins und die zugehörigen Funktionen {#aboutplugins}

Die Funktionen werden über eine Reihe von Plug-ins zur Verfügung gestellt, jeweils mit:

* Eine `features` Eigenschaft, die

   * Dient zum Aktivieren bzw. Deaktivieren der grundlegenden Funktionen für dieses Plug-In.
   * Konfiguriert mit einem standardisierten Verfahren.

* Gegebenenfalls weitere Eigenschaften und Optionen, die eine spezielle Konfiguration erfordern.

Die grundlegenden RTE-Funktionen sind durch den Wert der Eigenschaft `features` auf einem Knoten aktiviert oder deaktiviert, der spezifisch für das entsprechende Plug-in ist.

In der folgenden Tabelle sind die aktuellen Plug-ins und Folgendes aufgeführt:

* Plug-in-IDs mit einem Link zur API-Dokumentation. Die ID wird bei [Aktivierung eines Plug-ins](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin) als Knotenname verwendet.
* Zulässige Werte für die Eigenschaft `features`.
* Eine Beschreibung der vom Plug-in bereitgestellten Funktion.

| Plug-in-ID | features | Beschreibung |
|--- |--- |--- |
| edit | `cut`, `copy`, `paste-default`, `paste-plaintext`, `paste-wordhtml` | [Ausschneiden, Kopieren und drei Einfügemodi](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) |
| [findreplace](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | `find`, `replace` | Suchen und Ersetzen. |
| [format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | `bold`, `italic`, `underline` | [Grundlegende Textformatierung](configure-rich-text-editor-plug-ins.md#textstyles) |
| [image](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | `image` | Grundlegende Bildunterstützung (Ziehen aus der Inhaltssuche oder Inhaltssuche). Nutzungsverhalten für Autoren kann je nach verwendetem Browser variieren |
| [keys](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) | - | Informationen zum Definieren dieses Werts finden Sie unter [Registerkarten-Größe](configure-rich-text-editor-plug-ins.md#tabsize). |
| [justify](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | `justifyleft`, `justifycenter`, `justifyright` | Absatzausrichtung |
| [links](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | `modifylink`, `unlink`, `anchor` | [Hyperlinks und Anker](configure-rich-text-editor-plug-ins.md#linkstyles) |
| [lists](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | `ordered`, `unordered`, `indent`, `outdent` | This plug-in controls both [indentation and lists](configure-rich-text-editor-plug-ins.md#indentmargin); including nested lists. |
| [misctools](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | `specialchars`, `sourceedit` | Miscellaneous tools let authors to enter [special characters](configure-rich-text-editor-plug-ins.md#spchar) or edit the HTML source. Also, you can add a [range of special characters](configure-rich-text-editor-plug-ins.md#definerangechar) if you want to define your own list. |
| Paraformat | `paraformat` | The default paragraph formats are Paragraph, Heading 1, Heading 2, and Heading 3 (`<p>`, `<h1>`, `<h2>`, and `<h3>`). Sie können [weitere Absatzformate](configure-rich-text-editor-plug-ins.md#paraformats) hinzufügen oder die Liste erweitern. |
| spellcheck | `checktext` | [Rechtschreibprüfung mit Spracherkennung](configure-rich-text-editor-plug-ins.md#adddict). |
| styles | `styles` | Unterstützung für die Formatierung mit einer CSS-Klasse. [Hinzufügen Sie neue Textstile](configure-rich-text-editor-plug-ins.md#textstyles) , wenn Sie Ihren eigenen Stilbereich für die Verwendung mit Text hinzufügen (oder erweitern) möchten. |
| subsuperscript | `subscript`, `superscript` | Erweiterungen zu den grundlegenden Formaten, indem Sie Unterskript- und Super-Skript hinzufügen. |
| table | `table`, `removetable`, `insertrow`, `removerow`, `insertcolumn`, `removecolumn`, `cellprops`, `mergecells`, `splitcell`, `selectrow`, `selectcolumns` | See [configure table styles](configure-rich-text-editor-plug-ins.md#tablestyles) to add your own styles for entire tables or individual cells. |
| undo | `undo`, `redo` | History size of [undo and redo](configure-rich-text-editor-plug-ins.md#undohistory) operations. |

>[!NOTE]
>
>Das Vollbild-Plug-in wird im Dialogmodus nicht unterstützt. Use of the `dialogFullScreen` setting to configure the toolbar for full-screen mode.

## Grundlegendes zu den Konfigurationspfaden und -speicherorten {#understand-the-configuration-paths-and-locations}

The [mode of RTE editing and the interface](#editingmodes) that you provide for your authors decide the location for the configuration details when you are [activating the RTE plug-ins](configure-rich-text-editor-plug-ins.md#activateplugin). Die Speicherorte sind:

* Inline-Modus: `cq:editConfig/cq:inplaceEditing`.
* Vollbildmodus: `cq:editConfig/cq:inplaceEditing`.
* Dialogfeldmodus: `cq:dialog`.
* Vollbildmodus, Dialogmodus: `cq:dialog`.

>[!NOTE]
>
>Do not name the node under `cq:inplaceEditing` as `config`. On `cq:inplaceEditing` node, define the following properties:
>
>* **Name**: `configPath`
>* **Typ**: `String`
>* **Wert**: Pfad des Knotens, der die tatsächliche Konfiguration enthält
>
>
Benennen Sie den RTE-Konfigurationsknoten nicht mit `config`. Otherwise, the RTE configurations take effect for only the administrators and not for the users in the group `content-author`.

Konfigurieren Sie die folgenden Eigenschaften, die im Dialogfeldbearbeitungsmodus gelten:

* `useFixedInlineToolbar`: Sie können die RTE-Symbolleiste fixieren und nicht schwebend. Legen Sie diese auf dem RTE-Knoten definierte boolesche Eigenschaft mit sling:resourceType= `cq/gui/components/authoring/dialog/richtext` auf `True`fest. Wenn diese Eigenschaft auf `True`festgelegt ist, wird die Bearbeitung von Rich-Text auf dem `foundation-contentloaded` Ereignis gestartet. To prevent this, set the property `customStart` to `True` and trigger the `rte-start` event to start RTE editing. Ist diese Eigenschaft `true`aktiviert, wird beim Klicken keine RTE Beginn, und dies ist das Standardverhalten.

* `customStart`: Setzen Sie diese boolesche Eigenschaft, die im RTE-Knoten definiert ist, auf `True`, um den RTE-Startzeitpunkt zu steuern, indem Sie das Ereignis `rte-start` auslösen.

* `rte-start`: Lösen Sie dieses Ereignis bei `contenteditable-div` des RTE aus, wenn die RTE-Bearbeitung gestartet werden soll. It works only if `customStart` has been set to `true`.

Wenn RTE im Dialogfeld mit aktivierter Touch-Funktion verwendet wird, legen Sie die Eigenschaft `useFixedInlineToolbar` so fest, `true` dass Probleme vermieden werden.

## Aktivieren von RTE-Funktionen durch Aktivieren von Plug-ins {#enable-rte-functionalities-by-activating-plug-ins}

RTE-Funktionen werden über eine Reihe von Plug-ins mit jeweils einer Eigenschaft „features“ bereitgestellt. Sie können die Funktionseigenschaft konfigurieren, um die verschiedenen Funktionen jedes Plug-ins zu (de-)aktivieren.

Ausführliche Konfigurationen des RTE-Plug-ins finden Sie unter [Aktivieren und Konfigurieren von RTE-Plug-ins](configure-rich-text-editor-plug-ins.md).

<!-- TBD ENGREVIEW: To confirm if the sample works in CS or not?
**Sample**: Download [this sample configuration](/help/sites-administering/assets/rte-sample-all-features-enabled-10.zip) that illustrates how to configure RTE. In this package all the features are enabled. -->

The [Core Components text component](https://docs.adobe.com/content/help/de/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor) lets template editors to configure many RTE plug-ins using the user interface as content policies, eliminating the need for technical configuration. Inhaltsrichtlinien können mit RTE-UI-Konfigurationen verwendet werden, wie in diesem Dokument beschrieben ist. For more information, see [create page templates](/help/sites-cloud/authoring/features/templates.md) and the [Core Components developer documentation](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/developing.html).

>Zu Referenzzwecken finden Sie die standardmäßigen Textkomponenten (bereitgestellt im Rahmen einer Standardinstallation) unter:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>
Um eine eigene Textkomponente zu erstellen, kopieren Sie die oben stehende Komponente, anstatt diese Komponenten zu bearbeiten.

## RTE-Symbolleiste konfigurieren {#dialogfullscreen}

[!DNL Experience Manager] Sie können die Benutzeroberfläche für den Rich-Text-Editor für die verschiedenen Bearbeitungsmodi unterschiedlich konfigurieren. Die Standardeinstellungen finden Sie unten. Sie können diese Standardwerte entsprechend Ihren Anforderungen überschreiben. Sie passen nur die Symbolleisteneigenschaften an, die Sie Ihren Autoren zur Verfügung stellen wollen. Sie brauchen nicht alle Symbolleistenkonfigurationen anzugeben.

Um die Symbolleiste für `dialogFullScreen` zu konfigurieren, verwenden Sie die folgende Beispielkonfiguration.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

Für den Inline- und Vollbildmodus werden verschiedene Benutzeroberflächeneinstellungen verwendet. Die Eigenschaft toolbar gibt die Option der Symbolleiste an.

For example, if the option is itself a feature (for example, `Bold`), it is specified as `PluginName#FeatureName` (for example, `links#modifylink`).

If the option is a pop over (containing some features of a plug-in), it is specified as `#PluginName` (for example, `#format`).

Separators (`|`) between a group of option can be specified with `-`.

Der Popupknoten im Inline- oder Vollbildmodus enthält eine Liste der verwendeten Popupfenster. Each child node under the `popovers` node is named after the plug-in (for example, format). Er verfügt über eine Eigenschaft „items“, die eine Liste der Funktionen des Plug-ins beinhaltet (z. B. „format#bold“).

## Einstellungen für die RTE-Benutzeroberfläche und Content-Richtlinien {#rtecontentpolicies}

Administratoren können die RTE-Optionen mithilfe von Content-Richtlinien steuern, anstatt die Konfiguration wie oben beschrieben durchzuführen. Content-Richtlinien definieren die Designeigenschaften einer Komponente, wenn sie als Teil einer [bearbeitbaren Vorlage](/help/sites-cloud/authoring/features/templates.md) verwendet wird. Wenn zum Beispiel eine Textkomponente, die den RTE verwendet, mit einer bearbeitbaren Vorlage verwendet wird, kann die Content-Richtlinie definieren, dass die fettgedruckte Option und einige Absatzformatierungsoptionen verfügbar sind. Content-Richtlinien sind wiederverwendbar und können auf eine Vielzahl von Vorlagen angewendet werden.

Die verfügbaren Optionen im RTE werden von der Benutzeroberflächenkonfiguration abwärts zu den Inhaltsrichtlinien übertragen.

* Die Benutzeroberflächen-Konfigurationseinstellungen definieren, welche Optionen für die Content-Richtlinien verfügbar sind.
* Wenn die Benutzeroberflächenkonfiguration des RTE entfernt wurde oder ein Element nicht aktiviert wird, kann die Inhaltsrichtlinie es nicht konfigurieren.
* Ein Autor hat nur auf die Funktionen Zugriff, die durch die Benutzeroberflächen-Konfigurationen und Content-Richtlinien zur Verfügung gestellt werden.

Beispielsweise können Sie die [Text-Core Component-Dokumentation](https://docs.adobe.com/help/de/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor) sehen.

## Anpassen der Zuordnung zwischen Symbolleistenelementen und Befehlen {#iconstoolbar}

Sie können die Zuordnung zwischen in der RTE-Symbolleiste angezeigten Coral-Symbolen und den verfügbaren Befehlen anpassen. Sie können keine anderen Symbole als Coral-Symbole verwenden.

1. Create a node named `icons` under `uiSettings/cui`.

1. Erstellen Sie Knoten für die einzelnen Symbole darunter.
1. Geben Sie auf jeder einzelnen Symbol-Node ein Korallensymbol und einen Befehl ein, der dem Symbol zugeordnet werden soll.

Below is a sample snippet to map the command `Bold` to the Coral icon named `textItalic`.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true">
    <rtePlugins jcr:primaryType="nt:unstructured">
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/>
    </rtePlugins>
    <uiSettings jcr:primaryType="nt:unstructured">
        <cui jcr:primaryType="nt:unstructured">
            <inline jcr:primaryType="nt:unstructured"
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]">
            </inline>
            <icons jcr:primaryType="nt:unstructured">
                <bold jcr:primaryType="nt:unstructured"
                    command="format#bold"
                    icon="textItalic"/>
            </icons>
        </cui>
    </uiSettings>
</text>
```

## Bekannte Einschränkungen {#known-limitations}

[!DNL Experience Manager]Für die RTE-Funktion gelten folgende Einschränkungen:

* RTE capabilities are supported only in [!DNL Experience Manager] component dialogs. RTE wird nicht auf Assistenten oder Foundation-Formularen unterstützt.

* [!DNL Experience Manager] funktioniert nicht auf Hybrid-Geräten. <!-- TBD: Check. This is not mentioned in Known Issue /help/release-notes/known-issues.md-->

* Do not name the RTE configuration node `config`. Otherwise, the RTE configuration takes effect for only the administrators and not for the users in the group `content-author`.

* RTE unterstützt nicht das Einbetten von Inhalten in Inline-Rahmen oder iframe.

## Best practices and tips {#best-practices-and-tips}

* Aktivieren Sie für ein unverankertes Dialogfeld nur die Zusatzmodule ohne Popup-Dialogfeld. Plug-ins ohne Popup-Fenster sind kleiner und eignen sich am besten für einen schwebenden Dialog.
* Enable the plug-ins with larger pop-up, such as the `Paste` plug-in, only in the full-screen dialog mode or in full-screen mode. Plug-ins mit einem größeren Popup-Fenster beanspruchen mehr Platz auf dem Bildschirm, um ein gutes Authoring-Erlebnis zu ermöglichen.
* Wenn Sie benutzerdefinierte Plug-ins für den RTE von CoralUI nutzen, verwenden Sie die Bibliothek `rte.coralui3`3.

>[!MORELIKETHIS]
>
>* [Konfigurieren von RTE-Plug-ins](configure-rich-text-editor-plug-ins.md)
>* [Verwenden des Rich-Text-Editors für das Authoring](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md)
>* [Konfigurieren des RTE für barrierefreie Websites](rte-accessible-content.md)
>* [Tutorial-Beispiel für die Erstellung von kombinierten Mehrfeld-Komponenten](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

