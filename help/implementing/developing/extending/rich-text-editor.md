---
title: Konfigurieren Sie den Rich Text Editor, um Inhalte in Adobe Experience Manager als Cloud-Dienst zu erstellen.
description: Rich-Text-Editor konfigurieren, um Inhalte in Adobe Experience Manager als Cloud-Dienst zu erstellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 165dc4af656ce1bc431d2f921775ebda4cf4de9f
workflow-type: tm+mt
source-wordcount: '2078'
ht-degree: 53%

---


# Konfigurieren des Rich-Text-Editors {#configure-the-rich-text-editor}

Der Rich Text Editor (RTE) bietet Autoren eine breite Palette von Funktionen zum Bearbeiten von Textinhalten. Symbole, Auswahlfelder, Symbolleiste und Menüs werden für eine WYSIWYG-Textbearbeitung bereitgestellt. Administratoren konfigurieren die RTE, um die in den Authoring-Komponenten verfügbaren Funktionen zu aktivieren, zu deaktivieren und zu erweitern. Informationen zur Verwendung der Authoring-Funktionen des RTE finden Sie unter [Verwenden des Rich-Text-Editors für das Authoring](rich-text-editor.md). Erfahren Sie, wie Autoren RTE zum Authoring von [Webinhalten](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md) verwenden.

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

Die Symbolleiste enthält die Optionen für das WYSIWYG-Authoring-Erlebnis. Experience Manager-Administratoren können die in der Symbolleiste auf der Benutzeroberfläche verfügbaren Optionen konfigurieren. In Experience Manager stehen standardmäßig umfassende Bearbeitungsoptionen zur Verfügung. Entwickler können Experience Manager anpassen, um weitere Bearbeitungsoptionen hinzuzufügen.

## Verschiedene Bearbeitungsmodi {#editingmodes}

Autoren können Textinhalte in Experience Manager mit den verschiedenen Modi von Komponenten erstellen und bearbeiten. Die Symbolleistenoptionen für das Erstellen und Formatieren von Inhalten und das Benutzererlebnis von RTE-aktivierten Komponenten in verschiedenen Bearbeitungsmodi variieren je nach RTE-Konfiguration.

| Bearbeitungsmodus | Bearbeitungsbereich | Für die Aktivierung empfohlene Funktionen |
|--- |--- |--- |
| Inline | Bearbeitung im Kontext für schnelle, geringfügige Änderungen; Formatieren ohne Öffnen eines Dialogfelds | Minimale RTE-Funktionen |
| RTE-Vollbildschirm | Füllt die gesamte Seite aus | Alle erforderlichen RTE-Funktionen |
| Dialogfeld | Dialogfeld, das oberhalb des Seiteninhalts angezeigt wird, jedoch nicht die gesamte Seite einnimmt | Funktionen aktivieren |
| Dialogfeld-Vollbildmodus | Wie im Vollbildmodus; enthält neben dem RTE Felder des Dialogfelds | Alle erforderlichen RTE-Funktionen |

>[!NOTE]
>
>Die Funktion zum Bearbeiten der Quelle ist im Inline-Bearbeitungsmodus nicht verfügbar. Im Vollbildmodus können Sie Bilder nicht per Drag-and-Drop verschieben. Alle anderen Funktionen sind in allen Modi verfügbar.

### Inline-Bearbeitung {#inline-editing}

Beim Öffnen (mit langsamem Klicken auf die Dublette) können die Inhalte innerhalb der Seite bearbeitet werden. Dazu steht Ihnen eine kompakte Symbolleiste mit sehr grundlegenden Optionen zur Verfügung.

![Inline-Bearbeitung mit grundlegenden Optionen in der Symbolleiste](assets/inline-editing-mode-basic-options.png)

*Abbildung: Inline-Bearbeitung mit grundlegenden Optionen in der Symbolleiste.*

### Bearbeitung im Vollbildmodus {#full-screen-editing}

Experience Manager-Komponenten können in Ansicht im Vollbildmodus geöffnet werden, die den Seiteninhalt ausblendet und den verfügbaren Bildschirm einnimmt. Die Bearbeitung im Vollbildmodus ist quasi eine detaillierte Version der Inline-Bearbeitung, da sie die meisten Bearbeitungsmöglichkeiten bietet. It can be opened by clicking ![rte_fullscreen](assets/rte_fullscreen.png), from the compact toolbar when using the inline editing mode.

Im Dialogfeld-Vollbildmodus stehen neben einer detaillierten RTE-Symbolleiste auch die in einem Dialogfeld verfügbaren Optionen und Komponenten zur Verfügung. Dies gilt nur für ein Dialogfeld, das neben anderen Komponenten einen RTE enthält.

![Die detaillierte RTE-Symbolleiste beim Bearbeiten im Vollbildmodus](assets/rte-toolbar-full-screen-mode.png)

*Abbildung: Die detaillierte RTE-Symbolleiste beim Bearbeiten im Vollbildmodus.*

### Bearbeitung in einem Dialogfeld {#dialog-editing}

Wenn Sie auf eine Komponente doppelklicken, öffnet sich ein Dialogfeld zur Bearbeitung des Inhalts. Das Dialogfeld öffnet sich oben auf der jeweiligen Seite. In bestimmten Fällen kann dieses Dialogfeld auch als Popup-Fenster geöffnet werden. Wenn eine Textkomponente beispielsweise Teil einer Spalte in einem mehrspaltigen Seitenlayout ist und der für das Dialogfeld verfügbare Bereich kleiner ist.

![Dialogbearbeitungsmodus](assets/dialog_editing_modetouchui.png)

*Abbildung: Dialogfeldbearbeitungsmodus.*

## RTE-Plug-ins und die zugehörigen Funktionen {#aboutplugins}

Die Funktionen werden über eine Reihe von Plug-ins zur Verfügung gestellt, jeweils mit:

* Eine `features` Eigenschaft, die

   * Dient zum Aktivieren bzw. Deaktivieren der grundlegenden Funktionen für dieses Plug-In.
   * Konfiguriert mit einem standardisierten Verfahren.

* weiteren Eigenschaften und Optionen, die eine spezielle Konfiguration erfordern.

Die grundlegenden RTE-Funktionen sind durch den Wert der Eigenschaft `features` auf einem Knoten aktiviert oder deaktiviert, der spezifisch für das entsprechende Plug-in ist.

In der folgenden Tabelle sind die aktuellen Plug-ins und Folgendes aufgeführt:

* Plug-in-IDs mit einem Link zur API-Dokumentation. Die ID wird bei [Aktivierung eines Plug-ins](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin) als Knotenname verwendet.
* Zulässige Werte für die Eigenschaft `features`.
* Eine Beschreibung der vom Plug-in bereitgestellten Funktion.

| Plug-in-ID | features | Beschreibung |
|--- |--- |--- |
| edit | cut copy paste-default paste-plaintext paste-wordhtml | [Ausschneiden, Kopieren und drei Einfügemodi](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) |
| [findreplace](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | find replace | Suchen und Ersetzen. |
| [format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | fette kursive Unterstreichung | [Grundlegende Textformatierung](configure-rich-text-editor-plug-ins.md#textstyles) |
| [image](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | image | Grundlegende Bildunterstützung (Ziehen aus der Inhaltssuche oder Inhaltssuche). Nutzungsverhalten für Autoren kann je nach verwendetem Browser variieren |
| [keys](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | Informationen zum Definieren dieses Werts finden Sie unter [Registerkarten-Größe](configure-rich-text-editor-plug-ins.md#tabsize). |
| [justify](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justifyleft justifycenter justifyright | Absatzausrichtung |
| [links](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | modifylink unlink anchor | [Hyperlinks und Anker](configure-rich-text-editor-plug-ins.md#linkstyles) |
| [lists](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | ordered unordered indent outdent | This plug-in controls both [indentation and lists](configure-rich-text-editor-plug-ins.md#indentmargin); including nested lists. |
| [misctools](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | specialchars sourceedit | Miscellaneous tools allow authors to enter [special characters](configure-rich-text-editor-plug-ins.md#spchar) or edit the HTML source. Also, you can add a whole [range of special characters](configure-rich-text-editor-plug-ins.md#definerangechar) if you want to define your own list. |
| Paraformat | paraformat | The default paragraph formats are Paragraph, Heading 1, Heading 2, and Heading 3 (`<p>`, `<h1>`, `<h2>`, and `<h3>`). Sie können [weitere Absatzformate](configure-rich-text-editor-plug-ins.md#paraformats) hinzufügen oder die Liste erweitern. |
| spellcheck | checktext | [Rechtschreibprüfung mit Spracherkennung](configure-rich-text-editor-plug-ins.md#adddict). |
| styles | styles | Unterstützung für die Formatierung mit einer CSS-Klasse. [Hinzufügen Sie neue Textstile](configure-rich-text-editor-plug-ins.md#textstyles) , wenn Sie Ihren eigenen Stilbereich für die Verwendung mit Text hinzufügen (oder erweitern) möchten. |
| subsuperscript | subscript superscript | Erweiterungen zu den grundlegenden Formaten, indem Sie Unter- und Super-Skript hinzufügen. |
| table | table removetable insertrow removerow insertcolumn removecolumn cellprops mergecells splitcell selectrow selectcolumns | See [configure table styles](configure-rich-text-editor-plug-ins.md#tablestyles), if you want to add your own styles for either entire tables or individual cells. |
| undo | undo redo | History size of [undo and redo](configure-rich-text-editor-plug-ins.md#undohistory) operations. |

>[!NOTE]
>
>Das Plug-in für den Vollbildmodus wird im Dialogfeldmodus nicht unterstützt. Use of the `dialogFullScreen` setting to configure the toolbar for full screen mode.

## Grundlegendes zu den Konfigurationspfaden und -speicherorten {#understand-the-configuration-paths-and-locations}

Der [RTE-Bearbeitungsmodus (und die Benutzeroberfläche)](#editingmodes), den Sie Ihren Autoren bereitstellen, legt den Speicherort für die Konfigurationsdetails fest, wenn Sie [die RTE-Plug-ins aktivieren](configure-rich-text-editor-plug-ins.md#activateplugin):

* Inline-Modus: `cq:editConfig/cq:inplaceEditing`
* Vollbildmodus: `cq:editConfig/cq:inplaceEditing`
* Dialogfeldmodus: `cq:dialog`
* Vollbildmodus: `cq:dialog`

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

* `useFixedInlineToolbar`: Legen Sie diese boolesche Eigenschaft, die auf dem RTE-Knoten definiert ist (mit sling:resourceType= `cq/gui/components/authoring/dialog/richtext`), auf `True`fest, damit die RTE-Symbolleiste nicht schwebend, sondern fixiert wird.

   Wenn diese Eigenschaft auf „true“ gesetzt ist, wird die Rich-Text-Bearbeitung standardmäßig bei dem Ereignis „foundation-contentloaded“ gestartet.

   Um dies zu verhindern, setzen Sie die Eigenschaft `customStart` auf `True` und lösen Sie das Ereignis „rte-start“ zum Starten der RTE-Bearbeitung aus. Wenn diese Eigenschaft auf „true“ gesetzt ist, funktioniert das Standardverhalten, d. h. das Starten des RTE bei Klicken, nicht.

* `customStart`: Setzen Sie diese boolesche Eigenschaft, die im RTE-Knoten definiert ist, auf `True`, um den RTE-Startzeitpunkt zu steuern, indem Sie das Ereignis `rte-start` auslösen.

* `rte-start`: Lösen Sie dieses Ereignis bei `contenteditable-div` des RTE aus, wenn die RTE-Bearbeitung gestartet werden soll. Dies funktioniert nur, wenn `customStart` auf „true“ gesetzt ist.

Wenn RTE im Dialogfeld mit aktivierter Touch-Funktion verwendet wird, legen Sie die Eigenschaft `useFixedInlineToolbar` so fest, `true` dass Probleme vermieden werden.

## Aktivieren von RTE-Funktionen durch Aktivieren von Plug-ins {#enable-rte-functionalities-by-activating-plug-ins}

RTE-Funktionen werden über eine Reihe von Plug-ins mit jeweils einer Eigenschaft „features“ bereitgestellt. Sie können die Funktionseigenschaft konfigurieren, um die verschiedenen Funktionen jedes Plug-ins zu (de-)aktivieren.

Ausführliche Konfigurationen des RTE-Plug-ins finden Sie unter [Aktivieren und Konfigurieren von RTE-Plug-ins](configure-rich-text-editor-plug-ins.md).

<!-- TBD ENGREVIEW: To confirm if the sample works in CS or not?
**Sample**: Download [this sample configuration](/help/sites-administering/assets/rte-sample-all-features-enabled-10.zip) that illustrates how to configure RTE. In this package all the features are enabled. -->

The [Core Components text component](https://docs.adobe.com/content/help/de/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor) allows template editors to configure many RTE plugins using the user interface as content policies, eliminating the need for technical configuration. Inhaltsrichtlinien können mit RTE-UI-Konfigurationen verwendet werden, wie in diesem Dokument beschrieben ist. For more information, see [create page templates](/help/sites-cloud/authoring/features/templates.md) and the [Core Components developer documentation](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/developing.html).

>Zu Referenzzwecken finden Sie die standardmäßigen Textkomponenten (bereitgestellt im Rahmen einer Standardinstallation) unter:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`

>
>
Um eine eigene Textkomponente zu erstellen, kopieren Sie die oben stehende Komponente, anstatt diese Komponenten zu bearbeiten.

## RTE-Symbolleiste konfigurieren {#dialogfullscreen}

Mit Experience Manager können Sie die Benutzeroberfläche für den Rich-Text-Editor für die verschiedenen Bearbeitungsmodi unterschiedlich konfigurieren. Die Standardeinstellungen finden Sie unten. Sie können diese Standardwerte entsprechend Ihren Anforderungen überschreiben. Sie passen nur die Symbolleisteneigenschaften an, die Sie Ihren Autoren zur Verfügung stellen wollen. Sie brauchen nicht alle Symbolleistenkonfigurationen anzugeben.

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

Für den Inline-Modus und den Vollbildmodus werden verschiedene Benutzeroberflächen-Einstellungen verwendet. Die Symbolleisten-Eigenschaft wird verwendet, um die Schaltflächen der Symbolleiste festzulegen.

For example, if the button is itself a feature (for example, `Bold`), it is specified as `PluginName#FeatureName` (for example, `links#modifylink`).

If the button is a popover (containing some features of a plug-in), it is specified as `#PluginName` (for example, `#format`).

Separators (`|`) between a group of buttons can be specified with `-`.

Der Knoten „pop-up“ im Inline- oder Vollbildmodus enthält eine Liste der verwendeten Popovers. Jeder untergeordnete Knoten unter dem Knoten „popovers“ wird nach dem Plug-in benannt (z. B. „format“). Er verfügt über eine Eigenschaft „items“, die eine Liste der Funktionen des Plug-ins beinhaltet (z. B. „format#bold“).

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

Below is a sample snippet to map the command Bold to the Coral icon named `textItalic`.

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

Die RTE-Funktion von Experience Manager unterliegt folgenden Einschränkungen:

* RTE-Funktionen werden nur in Experience Manager-Komponentendialogen unterstützt. RTE wird nicht auf Assistenten oder Foundation-Formularen unterstützt.

* Experience Manager funktioniert nicht auf Hybrid-Geräten. <!-- TBD: Check. This is not mentioned in Known Issue /help/release-notes/known-issues.md-->

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

