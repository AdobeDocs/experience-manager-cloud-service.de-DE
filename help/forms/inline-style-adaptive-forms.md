---
title: Wie werden Inline-Stile auf Komponenten adaptiver Formulare angewendet?
description: Erfahren Sie, wie Sie benutzerdefinierte Stile für ein adaptives Formular und für einzelne Komponenten auch Inline-CSS-Eigenschaften anwenden können.
feature: Adaptive Forms, Foundation Components
role: User
level: Intermediate
exl-id: 25adabfb-ff19-4cb2-aef5-0a8086d2e552
source-git-commit: eaab351460363b83c7d3667e048235506cc71c41
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 83%

---

# Inline-Formatierung von Komponenten adaptiver Formulare {#inline-styling-of-adaptive-form-components}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/creating-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/inline-style-adaptive-forms.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können das allgemeine Erscheinungsbild und Design eines adaptiven Formulars definieren, indem Sie mit dem [Design-Editor](themes.md) Stile definieren. Außerdem können Sie Inline-CSS-Stile auf einzelne Komponenten anwenden und die Änderungen direkt in der Vorschau anzeigen. Inline-Stile überschreiben die Formatierung, die im Design bereitgestellt wird.

## Verwenden von Inline-CSS-Eigenschaften {#apply-inline-css-properties}

So fügen Sie Inline-Stile zu einer Komponente hinzu:

1. Öffnen Sie das Formular im Formulareditor und ändern Sie den Modus in den Stilmodus. Um den Stilmodus zu ändern, wählen Sie in der Seitensymbolleiste die Option ![Arbeitsfläche-Dropdown](assets/Smock_ChevronDown.svg) > **[!UICONTROL Stil]**.
1. Wählen Sie eine Komponente auf der Seite aus und klicken Sie auf die Schaltfläche &quot;Bearbeiten&quot; ![edit-button](assets/edit.svg). In der Seitenleiste geöffnete Stileigenschaften.

   Sie können auch Komponenten aus der Hierarchiestruktur in der Seitenleiste auswählen. Die Hierarchiestruktur für das Formular ist als „Formularobjekte“ in der Seitenleiste verfügbar.

   Im Modus [!UICONTROL Stil] können Sie Komponenten sehen, die unter „Formularobjekte“ aufgeführt sind. Allerdings führt „Formularobjekte“ in der Seitenleiste Komponenten wie Felder und Bereiche auf. Felder und Bereiche sind generische Komponenten, die Komponenten wie Textfelder und Optionsschaltflächen enthalten können.

   Wenn Sie eine Komponente in der Seitenleiste auswählen, sehen Sie alle aufgelisteten Unterkomponenten sowie die Eigenschaften der ausgewählten Komponente. Sie können eine bestimmte Unterkomponente auswählen und formatieren.

1. Klicken Sie auf eine Registerkarte in der Seitenleiste, um CSS-Eigenschaften festzulegen. Sie können Eigenschaften wie die folgenden angeben:

   * [!UICONTROL Abmessungen und Position] (Anzeigeeinstellung, Auffüllung, Höhe, Breite, Ränder, Position, Z-Index, „Float“, „Clear“, Überlauf)
   * [!UICONTROL Text] (Schriftfamilie, Stärke, Farbe, Größe, Zeilenhöhe und Ausrichtung)
   * [!UICONTROL Hintergrund] (Bild und Verlauf, Hintergrundfarbe)
   * [!UICONTROL Rahmen] (Breite, Stil, Farbe, Radius)
   * [!UICONTROL Effekte] (Schatten, Deckkraft)
   * [!UICONTROL Erweitert] (Ermöglicht das Schreiben benutzerdefinierten CSS für die Komponente)

1. Ebenso können Sie Stile auf andere Teile einer Komponente wie [!UICONTROL Widget], [!UICONTROL Beschriftung] und [!UICONTROL Hilfe] anwenden.
1. Auswählen **[!UICONTROL Fertig]** zur Bestätigung der Änderungen oder **[!UICONTROL Abbrechen]** , um die Änderungen zu verwerfen.

## Beispiel: Inline-Formatvorlagen für eine Feldkomponente {#example-inline-styles-for-a-field-component}

Die folgenden Bilder zeigen ein Textfeld, bevor und nachdem Inline-Stile darauf angewendet wurden.

![Textfeldkomponente vor der Anwendung von Inline-Formatierung](assets/no-style.png)

Textfeldkomponente vor der Anwendung von Inline-Stil-Eigenschaften

Beachten Sie die Änderung im Textfeldstil in der folgenden Abbildung, nachdem die folgenden CSS-Eigenschaften angewendet wurden.

<table>
 <tbody>
  <tr>
   <td><p>Selektor</p> </td>
   <td><p>CSS-Eigenschaft</p> </td>
   <td><p>Wert</p> </td>
   <td><p>Ergebnis</p> </td>
  </tr>
  <tr>
   <td><p>Feld</p> </td>
   <td><p>border</p> </td>
   <td><p>Border width =2px</p> <p>Border style=Solid</p> <p>Border color=#1111</p> </td>
   <td><p>Erstellt einen schwarzen, 2 Pixel breiten Rahmen um das Feld</p> </td>
  </tr>
  <tr>
   <td><p>Textfeld</p> </td>
   <td><p>background-color</p> </td>
   <td><p>#6495ED</p> </td>
   <td><p>Ändert die Hintergrundfarbe zu Kornblumenblau (#6495ED)</p> <p>Hinweis: Sie können einen Farbnamen oder den zugehörigen Hexadezimalcode im Wertefeld angeben.</p> </td>
  </tr>
  <tr>
   <td><p>Bezeichnung</p> </td>
   <td><p>Abmessungen und Position &gt; Breite</p> </td>
   <td><p>100 px</p> </td>
   <td><p>Stellt die Breite für die Beschriftung auf 100 px ein</p> </td>
  </tr>
  <tr>
   <td>Feldhilfesymbol</td>
   <td>Text &gt; Schriftfarbe</td>
   <td>#2ECC40</td>
   <td>Ändert die Farbe des Hilfesymbols.</td>
  </tr>
  <tr>
   <td><p>Lange Beschreibung</p> </td>
   <td><p>text-align</p> </td>
   <td><p>center</p> </td>
   <td><p>Richtet die Langbeschreibung für die Hilfe mittig aus</p> </td>
  </tr>
 </tbody>
</table>

![Textfelddesign nach der Anwendung von Inline-Formatierung](assets/applied-style.png)

Textfeldkomponente nach der Anwendung der Inline-Stil-Eigenschaften

Wenn Sie den obigen Schritten folgen, können Sie andere Komponenten wie Bereiche, Sendeschaltflächen und Optionsschaltflächen auswählen und formatieren.

>[!NOTE]
>
>Designeigenschaften variieren je nach ausgewählter Komponente.

## Kopieren und Einfügen von Stilen {#copy-paste-styles}

Sie können einen Stil auch von einer Komponente kopieren und in eine andere Komponente in einem adaptiven Formular einfügen. Im **[!UICONTROL Stil]** -Modus wählen Sie die Komponente aus und klicken Sie auf das Symbol Kopieren . ![Kopieren](assets/property-copy-icon.svg).

Wählen Sie die andere Komponente desselben Typs aus und klicken Sie auf das Symbol Einfügen . ![Kopieren](assets/Smock_Paste_18_N.svg) , um den kopierten Stil einzufügen. Sie können auch das Symbol Stil löschen auswählen ![Kopieren](assets/clear-style-icon.svg) , um den angewendeten Stil zu löschen.

## Stile für verschiedene Zustände einer Komponente festlegen {#set-styles-for-states}

Sie können Stile für verschiedene Statuszustände eines Komponententyps festlegen. Zu den verschiedenen Statuszuständen gehören: [!UICONTROL Fokus], [!UICONTROL Deaktiviert], [!UICONTROL Mausberührung], [!UICONTROL Fehler], [!UICONTROL Erfolg] und [!UICONTROL Obligatorisch].

So definieren Sie die Formatierung für einen Status einer Komponente:

1. Im **[!UICONTROL Stil]** -Modus wählen Sie die Komponente aus und klicken Sie auf das Symbol Bearbeiten . ![Bearbeiten](assets/Smock_Edit_18_N.svg).

1. Wählen Sie mit der Dropdownliste **[!UICONTROL Status]** den Status der Komponente aus.

   ![Status auswählen](assets/select-state.png)

1. Definieren Sie den Stil für den ausgewählten Status der Komponente und wählen Sie ![Speichern](assets/save_icon.svg) , um die Eigenschaften zu speichern.

Sie können die Statuszustände „Erfolg“ und „Fehler“ auch simulieren. Wählen Sie das Symbol Erweitern aus, um die **[!UICONTROL Erfolg simulieren]** und **[!UICONTROL Fehler simulieren]** Optionen.

![Status simulieren](assets/simulate-states.png)


## Siehe auch {#see-also}

{{see-also}}


<!--

>[!MORELIKETHIS]
>
>* [Use themes in Adaptive Form Core Components ](/help/forms/using-themes-in-core-components.md)

-->