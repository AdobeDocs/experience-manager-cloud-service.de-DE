---
title: RTE konfigurieren, um barrierefreie Webseiten und Websites zu erstellen.
description: Hier erfahren Sie, wie Sie Rich Text Editor konfigurieren, um barrierefreie Sites in Adobe Experience Manager zu erstellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 78ec0ed2a1473797a07905baa346a83376779419
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 33%

---


# Configure RTE to create accessible sites {#configure-rte-accessible-sites}

Adobe Experience Manager unterstützt standardmäßige Barrierefreiheitsfunktionen wie alternativen Text für Bilder und zusätzliche Funktionen, auf die beim Erstellen von Inhalten zugegriffen werden kann. Inhaltsersteller verwenden diese Funktionen zusammen mit Komponenten, die den Rich-Text-Editor (RTE) verwenden. Dazu gehören alternativer Text, Strukturinformationen über Überschriften und Absatzelemente usw.

Informationen zu den typischen Konfigurationen von RTE finden Sie unter RTE-Plug-Ins [konfigurieren](rich-text-editor.md) und [konfigurieren für bestimmte Funktionen](configure-rich-text-editor-plug-ins.md).

Verwenden Sie die RTE-Plug-Ins-Konfiguration, um die Funktionen zur Barrierefreiheit zu konfigurieren und anzupassen. For example, use `paraformat` to add additional block level semantic elements, including extending the number of heading levels supported beyond the basic `H1`, `H2` and `H3` provided by default. Die Bearbeitung von Rich-Text ist mit vielen Komponenten der Authoring-Benutzeroberfläche möglich. Die am häufigsten verwendeten Komponenten sind Text, Bild, Download usw.

Die RTE-Funktion kann in vielen Komponenten zur Verfügung gestellt werden. Die primäre Komponente ist die `Text` Komponente.

Für die `Text` Komponente in Experience Manager wird im folgenden Screenshot der Rich-Text-Editor mit einer Reihe von Zusatzmodulen angezeigt, einschließlich `paraformat`:

![RTE-Text-Komponente im Vollbildmodus](assets/rte-toolbar-full-screen-mode.png)

## Plug-in-Funktionen konfigurieren {#configuring-the-plugin-features}

Anweisungen zum Konfigurieren von RTE finden Sie unter [Konfigurieren der Seite Rich Text Editor](rich-text-editor.md) . Der Artikel umfasst:

* [Plug-Ins und deren Funktionen](rich-text-editor.md#aboutplugins)
* [Konfigurationsspeicherorte](rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Aktivieren eines Plugins und Konfigurieren der Funktionseigenschaft](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Andere Funktionen der RTE konfigurieren](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

Um einige oder alle Funktionen eines Plug-Ins zu aktivieren, konfigurieren Sie das Plug-In in der entsprechenden `rtePlugins` Unterverzweigung in CRXDE Lite.

![Beispiel für ein rtePlugin in CRXDE Lite](assets/chlimage_1-208.png)

### Example - Specify paragraph formats available in RTE selection field {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Es können wie folgt neue semantische Blockformate zur Auswahl bereitgestellt werden:

1. Legen Sie den [Konfigurationsort](rich-text-editor.md#understand-the-configuration-paths-and-locations) abhängig von Ihrem RTE fest und navigieren Sie dorthin.
1. [Aktivieren Sie das Auswahlfeld](rich-text-editor.md) für Absätze, indem Sie das Plug-In [aktivieren](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Geben Sie die Formate an, die im Auswahlfeld](rich-text-editor.md)für Absätze verfügbar sein sollen.
1. Die Absatzformate sind dann für den Autor der Inhalte aus den Auswahlfeldern im RTE verfügbar.

Da Strukturelemente in der RTE über die Absatzformatoptionen verfügbar sind, bietet Experience Manager eine gute Grundlage für die Entwicklung barrierefreier Inhalte. Inhaltsautoren können den RTE für die Formatierung der Schriftgröße, der Farben oder anderer verwandter Attribute verwenden und dadurch die Erstellung einer Inline-Formatierung verhindern. Stattdessen müssen sie entsprechende Strukturelemente wie Überschriften auswählen und über die Option „Arten“ ausgewählte globale Formatarten verwenden. Dies sorgt für ein sauberes Markup, mehr Optionen für Benutzer, die die Suche mit ihren eigenen Formatvorlagen durchführen, sowie korrekt strukturierte Inhalte.

## Verwenden der Funktion „Quellenbearbeitung“ {#use-of-the-source-edit-feature}

In einigen Fällen halten Inhaltsautoren es für erforderlich, den mithilfe des RTE erstellten HTML-Quellcode zu untersuchen und anzupassen. So kann beispielsweise ein innerhalb des RTE erstellter Inhalt ein zusätzliches Markup erfordern, um Compliance mit WCAG 2.0 sicherzustellen. Dies lässt sich mit der Option [Quellenbearbeitung](rich-text-editor.md#aboutplugins) des RTE umsetzen. You can specify the [`sourceedit` feature on the `misctools` plugin](rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Use the `sourceedit` feature carefully. Tippfehler und/oder nicht unterstützte Funktionen können zusätzliche Probleme hervorrufen.

<!--
TBD ENGREVIEW: Is this only applicable to Classic UI? 

## Adding Support for Additional HTML Elements and Attributes {#adding-support-for-additional-html-elements-and-attributes}

To further extend the accessibility features of Experience Manager, it is possible to extend the existing components based on the RTE (such as the `Text` and `Table` components) with additional elements and attributes.

The following procedure illustrates how to extend the `Table` component with a `Caption` element that provides information about a data table to assistive technology users:

### Example: Add a caption to a table properties dialog {#example-adding-the-caption-to-the-table-properties-dialog}

In the constructor of the `TablePropertiesDialog`, add an additional text input field that is used for editing the caption. Set the `itemId` to `caption` (the DOM attribute’s name) to automatically handle its content.

In a `Table`, set the attribute to the DOM element or or remove it from the DOM element. The dialog in the `config` object passed the value. Set or remove the DOM attributes using the corresponding `CQ.form.rte.Common` methods (`com` is a shortcut for `CQ.form.rte.Common`). Using `CQ.form.rte.Common` methods avoids common pitfalls with browser implementations.

>[!NOTE]
>
>This procedure is only suitable for the classic UI.

### Step-by-step instructions {#step-by-step-instructions}

1. Start CRXDE Lite. For example: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)

1. Copy `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js` to `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`. Create intermediate folders if those do not exist.

1. Copy `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js` to `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Open `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js` file to edit.

1. In the `constructor` method, before the mention of `var dialogRef = this;`, add the following code:

   ```javascript
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Open `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js` file.

1. Add the following code at the end of the `transferConfigToTable` method:

   ```javascript
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. To save your changes, click **[!UICONTROL Save All]**.

## Best practices and limitations {#best-practices-limitations-tips}

* A plain text field is not the only type of input allowed for the value of the caption element. You can use any ExtJS widget, that provides the caption’s value through its `getValue()` method.
* To add editing capabilities for further additional elements and attributes, ensure that:

  * The `itemId` property for each corresponding field is set to the name of the appropriate DOM attribute (`TablePropertiesDialog`).
  * The attribute is set and/or removed on the DOM element explicitly (`Table`).
-->

>[!MORELIKETHIS]
>
>* [Eine schnelle Anleitung zu WCAG-Standards](/help/onboarding/accessibility/quick-guide-wcag.md)
>* [Barrierefreie Inhalte in Experience Manager erstellen](/help/sites-cloud/authoring/fundamentals/accessible-content.md)

