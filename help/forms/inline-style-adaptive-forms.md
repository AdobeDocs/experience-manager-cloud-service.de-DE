---
title: Wie werden Inline-Stile auf Komponenten adaptiver Formulare angewendet?
description: Erfahren Sie, wie Sie benutzerdefinierte Stile auf ein adaptives Formular anwenden können. Sie können auch Inline-CSS-Eigenschaften auf einzelne Komponenten eines adaptiven Formulars anwenden.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 25adabfb-ff19-4cb2-aef5-0a8086d2e552
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 54%

---

# Inline-Formatierung von Komponenten adaptiver Formulare {#inline-styling-of-adaptive-form-components}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/creating-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/inline-style-adaptive-forms.html) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können das allgemeine Erscheinungsbild und Design eines adaptiven Formulars definieren, indem Sie mit dem [Design-Editor](themes.md) Stile definieren. Außerdem können Sie Inline-CSS-Stile auf einzelne Komponenten anwenden und die Änderungen direkt in der Vorschau anzeigen. Inline-Stile überschreiben die Formatierung, die im Design bereitgestellt wird.

## Verwenden von Inline-CSS-Eigenschaften {#apply-inline-css-properties}

Hinzufügen von Inline-Stilen zu einer Komponente:

1. Öffnen Sie das Formular im Formular-Editor und ändern Sie den Modus in den Formatierungsmodus. Um den Stilmodus zu ändern, wählen Sie in der Seitensymbolleiste die Option ![Arbeitsfläche-Dropdown](assets/Smock_ChevronDown.svg) > **[!UICONTROL Stil]**.
1. Wählen Sie eine Komponente auf der Seite aus und klicken Sie auf die Schaltfläche &quot;Bearbeiten&quot; ![edit-button](assets/edit.svg). Die Stileigenschaften werden in der Seitenleiste geöffnet.

   Sie können auch Komponenten aus der Formularhierarchie in der Seitenleiste auswählen. Die Hierarchie des Formulars ist als Formularobjekte in der Seitenleiste verfügbar.

   Im Modus [!UICONTROL Stil] können Sie Komponenten sehen, die unter „Formularobjekte“ aufgeführt sind. Die Liste &quot;Formularobjekte&quot;in der Seitenleiste listet jedoch Komponenten wie Felder und Bereiche auf. Felder und Bedienfelder sind allgemeine Komponenten, die Komponenten wie Textfelder und Optionsfelder enthalten können.

   Wenn Sie eine Komponente in der Seitenleiste auswählen, sehen Sie alle aufgelisteten Unterkomponenten sowie die Eigenschaften der ausgewählten Komponente. Sie können eine bestimmte Unterkomponente auswählen und formatieren.

1. Klicken Sie auf eine Registerkarte in der Seitenleiste, um CSS-Eigenschaften anzugeben. Sie können Eigenschaften wie die folgenden angeben:

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

Textfeldkomponente vor dem Anwenden von Inline-Stil-Eigenschaften

Beachten Sie die Änderung des Textfeldstils, die in der folgenden Abbildung gezeigt wird, nachdem die folgenden CSS-Eigenschaften angewendet wurden.

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
   <td><p>Border width =2px</p> <p>Border style=Solid</p> <p>Rahmenfarbe=#1111</p> </td>
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
   <td>Feld Hilfe Symbol</td>
   <td>Text &gt; Schriftfarbe</td>
   <td>#2ECC40</td>
   <td>Ändert die Farbe des Hilfesymbol-Gesichts.</td>
  </tr>
  <tr>
   <td><p>Lange Beschreibung</p> </td>
   <td><p>text-align</p> </td>
   <td><p>Zentriert</p> </td>
   <td><p>Richtet die lange Beschreibung der Hilfe zentriert aus</p> </td>
  </tr>
 </tbody>
</table>

![Textfelddesign nach der Anwendung von Inline-Formatierung](assets/applied-style.png)

Textfeldkomponente nach dem Anwenden von Inline-Stileigenschaften

Mit den oben beschriebenen Schritten können Sie andere Komponenten wie Bedienfelder, Senden-Schaltflächen und Optionsfelder auswählen und formatieren.

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