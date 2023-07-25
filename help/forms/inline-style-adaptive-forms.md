---
title: Wie werden Inline-Stile auf Komponenten adaptiver Formulare angewendet?
description: Auf ein adaptives Formular können Sie benutzerdefinierte Stile anwenden, und auf einzelne Komponenten eines adaptiven Formulars sind auch Inline-CSS-Eigenschaften anwendbar. Erfahren Sie, wie Sie Inline-Stile auf Komponenten eines adaptiven Formulars anwenden. Vertiefen Sie das anhand eines Beispiels, in dem Sie einen Inline-Stil auf eine Textfeldkomponente anwenden.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 25adabfb-ff19-4cb2-aef5-0a8086d2e552
source-git-commit: ca0c9f102488c38dbe8c969b54be7404748cbc00
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 68%

---

# Inline-Formatierung von Komponenten adaptiver Formulare {#inline-styling-of-adaptive-form-components}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/creating-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/inline-style-adaptive-forms.html) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können das allgemeine Erscheinungsbild und Design eines adaptiven Formulars definieren, indem Sie mit dem [Design-Editor](themes.md) Stile definieren. Außerdem können Sie Inline-CSS-Stile auf einzelne Komponenten anwenden und die Änderungen direkt in der Vorschau anzeigen. Inline-Stile überschreiben die Formatierung, die im Design bereitgestellt wird.

## Verwenden von Inline-CSS-Eigenschaften {#apply-inline-css-properties}

So fügen Sie einer Komponente Inline-Stile hinzu:

1. Öffnen Sie das Formular im Formular-Editor und ändern Sie den Modus in den Formatierungsmodus. Um den Stilmodus zu aktivieren, tippen Sie in der Symbolleiste der Seite auf ](assets/Smock_ChevronDown.svg)Arbeitsfläche-Dropdown![ > **[!UICONTROL Stil]**.
1. Wählen Sie eine Komponente auf der Seite aus und tippen Sie auf die Schaltfläche „Bearbeiten“ ![Bearbeiten-Schaltfläche](assets/edit.svg). Die Stileigenschaften werden in der Seitenleiste geöffnet.

   Sie können auch Komponenten aus der Formularhierarchie in der Seitenleiste auswählen. Die Hierarchie des Formulars ist als Formularobjekte in der Seitenleiste verfügbar.

   Im Modus [!UICONTROL Stil] können Sie Komponenten sehen, die unter „Formularobjekte“ aufgeführt sind. Die Liste &quot;Formularobjekte&quot;in der Seitenleiste listet jedoch Komponenten wie Felder und Bereiche auf. Felder und Bedienfelder sind allgemeine Komponenten, die Komponenten wie Textfelder und Optionsfelder enthalten können.

   Wenn Sie eine Komponente in der Seitenleiste auswählen, sehen Sie alle aufgelisteten Unterkomponenten sowie die Eigenschaften der ausgewählten Komponente. Sie können eine bestimmte Unterkomponente auswählen und formatieren.

1. Klicken Sie auf eine Registerkarte in der Seitenleiste, um CSS-Eigenschaften anzugeben. Sie können Eigenschaften angeben, z. B.:

   * [!UICONTROL Abmessungen und Position] (Anzeigeeinstellung, Auffüllung, Höhe, Breite, Ränder, Position, Z-Index, „Float“, „Clear“, Überlauf)
   * [!UICONTROL Text] (Schriftfamilie, Stärke, Farbe, Größe, Zeilenhöhe und Ausrichtung)
   * [!UICONTROL Hintergrund] (Bild und Verlauf, Hintergrundfarbe)
   * [!UICONTROL Rahmen] (Breite, Stil, Farbe, Radius)
   * [!UICONTROL Effekte] (Schatten, Deckkraft)
   * [!UICONTROL Erweitert] (Ermöglicht das Schreiben benutzerdefinierten CSS für die Komponente)

1. Ebenso können Sie Stile auf andere Teile einer Komponente wie [!UICONTROL Widget], [!UICONTROL Beschriftung] und [!UICONTROL Hilfe] anwenden.
1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu bestätigen, oder auf **[!UICONTROL Abbrechen]**, um die Änderungen zu verwerfen.

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
   <td>Ändert die Farbe des Gesichts des Hilfesymbols.</td>
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

Sie können einen Stil auch von einer Komponente kopieren und in eine andere Komponente in einem adaptiven Formular einfügen. Tippen Sie im Modus **[!UICONTROL Stil]** auf die Komponente und dann auf das Symbol „Kopieren“ ![Kopieren](assets/property-copy-icon.svg).

Tippen Sie auf die andere Komponente desselben Typs und dann auf das Symbol „Einfügen“ ![Einfügen](assets/Smock_Paste_18_N.svg), um den kopierten Stil einzufügen. Sie können auch auf das Symbol „Stil entfernen“ ![Stil entfernen](assets/clear-style-icon.svg) tippen, um den angewendeten Stil zu entfernen.

## Stile für verschiedene Zustände einer Komponente festlegen {#set-styles-for-states}

Sie können Stile für verschiedene Statuszustände eines Komponententyps festlegen. Zu den verschiedenen Statuszuständen gehören: [!UICONTROL Fokus], [!UICONTROL Deaktiviert], [!UICONTROL Mausberührung], [!UICONTROL Fehler], [!UICONTROL Erfolg] und [!UICONTROL Obligatorisch].

So definieren Sie die Formatierung für einen Status einer Komponente:

1. Tippen Sie im Modus **[!UICONTROL Stil]** auf die Komponente und dann auf das Symbol „Bearbeiten“ ![Bearbeiten](assets/Smock_Edit_18_N.svg).

1. Wählen Sie mit der Dropdownliste **[!UICONTROL Status]** den Status der Komponente aus.

   ![Status auswählen](assets/select-state.png)

1. Definieren Sie die Formatierung für den ausgewählten Status der Komponente und tippen Sie auf ![Speichern](assets/save_icon.svg), um die Eigenschaften zu speichern.

Sie können die Statuszustände „Erfolg“ und „Fehler“ auch simulieren. Tippen Sie auf das Symbol „Erweitern“, um die Optionen **[!UICONTROL Erfolg simulieren]** und **[!UICONTROL Fehler simulieren]** anzuzeigen.

![Status simulieren](assets/simulate-states.png)
