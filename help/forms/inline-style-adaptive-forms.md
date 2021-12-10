---
title: Wie werden Inline-Stile auf Komponenten adaptiver Formulare angewendet?
description: Auf ein adaptives Formular können Sie benutzerdefinierte Stile anwenden, und auf einzelne Komponenten eines adaptiven Formulars sind auch Inline-CSS-Eigenschaften anwendbar. Erfahren Sie, wie Sie Inline-Stile auf Komponenten eines adaptiven Formulars anwenden. Vertiefen Sie das anhand eines Beispiels, in dem Sie einen Inline-Stil auf eine Textfeldkomponente anwenden.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 25adabfb-ff19-4cb2-aef5-0a8086d2e552
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 100%

---

# Inline-Formatierung von Komponenten adaptiver Formulare {#inline-styling-of-adaptive-form-components}

Sie können das allgemeine Erscheinungsbild und Design eines adaptiven Formulars definieren, indem Sie mit dem [Design-Editor](themes.md) Stile definieren. Außerdem können Sie Inline-CSS-Stile auf einzelne Komponenten anwenden und die Änderungen direkt in der Vorschau anzeigen. Inline-Stile überschreiben die Formatierung, die im Design bereitgestellt wird.

## Verwenden von Inline-CSS-Eigenschaften {#apply-inline-css-properties}

Hinzufügen von Inline-Stilen zu einer Komponente:

1. Öffnen Sie das Formular im Formular-Editor und ändern Sie den Modus in Stilmodus. Um den Stilmodus zu aktivieren, tippen Sie in der Symbolleiste der Seite auf ](assets/Smock_ChevronDown.svg)Arbeitsfläche-Dropdown![ > **[!UICONTROL Stil]**.
1. Wählen Sie eine Komponente auf der Seite aus und tippen Sie auf die Schaltfläche „Bearbeiten“ ![Bearbeiten-Schaltfläche](assets/edit.svg). In der Randleiste geöffnete Stileigenschaften.

   Sie können auch Komponenten aus der Hierarchiestruktur in der Seitenleiste auswählen. Die Hierarchiestruktur für das Formular ist als „Formularobjekte“ in der Seitenleiste verfügbar.

   Im Modus [!UICONTROL Stil] können Sie Komponenten sehen, die unter „Formularobjekte“ aufgeführt sind. Allerdings führt „Formularobjekte“ in der Seitenleiste Komponenten wie Felder und Bereiche auf. Felder und Bereiche sind generische Komponenten, die Komponenten wie Textfelder und Optionsschaltflächen enthalten können.

   Wenn Sie eine Komponente in der Seitenleiste auswählen, sehen Sie alle aufgelisteten Unterkomponenten sowie die Eigenschaften der ausgewählten Komponente. Sie können eine bestimmte Unterkomponente auswählen und formatieren.

1. Klicken Sie auf eine Registerkarte in der Randleiste, um CSS-Eigenschaften festzulegen. Sie können Eigenschaften wie die folgenden angeben:

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
   <td><p>100px</p> </td>
   <td><p>Stellt die Breite als 100px für die Beschriftung ein</p> </td>
  </tr>
  <tr>
   <td>Feld Hilfe Symbol</td>
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
