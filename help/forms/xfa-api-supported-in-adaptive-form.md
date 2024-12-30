---
title: 'XFA-Unterstützung in XDP-basierten adaptiven Formularen '
description: Auflistung unterstützter XFA-Ereignisse, -Eigenschaften, -Skripte und -Validierungen in adaptiven Formularen.
uuid: 75d3c292-cfed-438f-afdb-4071d95a08b7
topic-tags: develop
discoiquuid: 05303b29-9058-4723-b134-4ba605fe40c7
feature: Adaptive Forms
role: User
hide: true
hidefromtoc: true
exl-id: 59ae0eed-d832-4f46-9f99-7bcca9f82306
source-git-commit: a9adbb1886dcfedfc3fccb6f56939c46ba1365ee
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 100%

---

# XFA-Unterstützung in XDP-basierten adaptiven Formularen {#xfa-support-in-xdp-based-adaptive-forms}

## Einführung {#introduction}

Adaptive Formulare bieten Unterstützung für verschiedene XFA-Ereignisse, -Eigenschaften, -Skripte und -Validierungen, die in einer XDP-Datei definiert sind, darunter:

* Ausführung von Skripten, die für Ereignisse in der XDP-Datei definiert wurden.
* Erfassen von Standardwerten und Verhaltenseigenschaften für Felder in der XDP-Datei.
* Ausführung von Validierungsskripten, die in der XDP-Datei definiert wurden.

Wenn ein adaptives Formular anhand einer XDP-Datei erstellt wurde, werden die Eigenschaften, Ereignisse und Validierungen in der Benutzeroberfläche zur Erstellung adaptiver Formulare automatisch ausgefüllt. Allerdings können Formularautoren einige dieser Elemente überschreiben, um ein anderes Erlebnis bereitzustellen.

Dieser Artikel erläutert die unterstützten XFA-Ereignisse, -Eigenschaften und -Validierungen, die in adaptiven Formularen berücksichtigt werden, und beschreibt, wie sie dort überschrieben werden können.

## Unterstützte XFA-Elemente und deren Zuordnung in adaptiven Formularen {#supported-xfa-elements-and-their-mapping-in-adaptive-forms-br}

### Felder {#fields}

Wenn ein adaptives Formular anhand einer XDP-Datei erstellt wird, können Sie ein XFA-Textfeld per Drag-and-drop auf das adaptive Formular ziehen. Die folgende Tabelle zeigt, wie den Feldern in adaptiven Formularen XFA-Felder zugeordnet werden.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA-Feld oder Container</strong></p> </td>
   <td><p><strong>Entsprechende Komponente des adaptiven Formulars</strong></p> </td>
  </tr>
  <tr>
   <td><p>Schaltfläche </p> </td>
   <td><p>Schaltfläche</p> </td>
  </tr>
  <tr>
   <td><p>Kontrollkästchen </p> </td>
   <td><p>Kontrollkästchen</p> </td>
  </tr>
  <tr>
   <td><p>Listenfeld </p> </td>
   <td><p>Dropdownliste</p> </td>
  </tr>
  <tr>
   <td><p>Datum-/Uhrzeitfeld </p> </td>
   <td><p>Datumsauswahl</p> </td>
  </tr>
  <tr>
   <td><p>Unterschrift freihändig</p> </td>
   <td><p>Freihändige Unterschrift</p> </td>
  </tr>
  <tr>
   <td><p>Numerisches Feld </p> </td>
   <td><p>Numerisches Feld</p> </td>
  </tr>
  <tr>
   <td><p>Dezimalfeld</p> </td>
   <td><p>Numerisches Feld</p> </td>
  </tr>
  <tr>
   <td><p>Textfeld </p> </td>
   <td><p>Textfeld</p> </td>
  </tr>
  <tr>
   <td><p>Kennwortfeld </p> </td>
   <td><p>Kennwortfeld</p> </td>
  </tr>
  <tr>
   <td><p>Bild</p> </td>
   <td><p>Bild</p> </td>
  </tr>
  <tr>
   <td><p>Text</p> </td>
   <td><p>Text</p> </td>
  </tr>
  <tr>
   <td><p>Teilformular </p> </td>
   <td><p>Bereich</p> </td>
  </tr>
  <tr>
   <td><p>Bereich (Gruppe)</p> </td>
   <td><p>Bereich</p> </td>
  </tr>
  <tr>
   <td><p>Teilformularsatz </p> </td>
   <td><p>Bereich</p> </td>
  </tr>
 </tbody>
</table>

### Eigenschaften {#properties}

Die folgende Tabelle erfasst, wie verschiedene XFA-Skripte, die in den XDP-Dateien definiert sind, sich in adaptiven Formularen verhalten.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA-Komponenteneigenschaften</strong></p> </td>
   <td><p><strong>Entsprechendes Verhalten in adaptiven Formularen</strong></p> </td>
  </tr>
  <tr>
   <td><p>somExpression </p> </td>
   <td><p>Der Eigenschaft der Verbindungsreferenz (bindRef) im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>presence </p> </td>
   <td><p>Der visible-Eigenschaft im adaptiven Formular zugeordnet. Sie können sie mit dem Sichtbarkeitsausdruck überschreiben.</p> </td>
  </tr>
  <tr>
   <td><p>access </p> </td>
   <td><p>Der enable-Eigenschaft im adaptiven Formular zugeordnet. Sie können sie mit dem Zugriffsausdruck überschreiben.</p> </td>
  </tr>
  <tr>
   <td><p>Barrierefreiheit: role </p> </td>
   <td><p>Der role-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>Barrierefreiheit: speakPriority </p> </td>
   <td><p>Der speakPriority-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>Barrierefreiheit: speakText</p> </td>
   <td><p>Dem benutzerdefinierten Barrierefreiheits-Text im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>Barrierefreiheit: QuickInfo </p> </td>
   <td><p>Der short description-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>caption<em> (alle Feldtypen)</em></p> </td>
   <td><p>Der Title-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>displayFormat<em> (alle Feldtypen)</em></p> </td>
   <td><p>Dem Anzeigemuster im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>rawValue<em> (alle Feldtypen)</em></p> </td>
   <td><p>Der value-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>items<em> (Listenfeld, Kontrollkästchen)</em></p> </td>
   <td><p>Der options-Eigenschaft im adaptiven Formular zugeordnet. Mit dem Optionsausdruck überschreibbar.</p> </td>
  </tr>
  <tr>
   <td><p>maxChar<em> (Textfeld)</em></p> </td>
   <td><p>Der Maximum characters allowed-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>multiline<em> (Textfeld)</em></p> </td>
   <td><p>Der Allow multiple lines-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>fracDigit<em> (numerisches Feld, Dezimalfeld)</em></p> </td>
   <td><p>Der Frac digits-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>leadDigit<em> (numerisches Feld, Dezimalfeld)</em></p> </td>
   <td><p>Der Lead digits-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>multiSelect<em> (Listenfeld)</em></p> </td>
   <td><p>Der Allows multiple selection-Eigenschaft im adaptiven Formular zugeordnet.</p> </td>
  </tr>
 </tbody>
</table>

### Skripte {#scripts}

Die folgende Tabelle erfasst, wie verschiedene XFA-Skripte, die in den XDP-Dateien definiert sind, sich in adaptiven Formularen verhalten.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA-Skriptereignisse</strong></p> </td>
   <td><p><strong>Entsprechendes Verhalten in adaptiven Formularen</strong></p> </td>
  </tr>
  <tr>
   <td><p>initialize </p> </td>
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht überschrieben werden.</p> </td>
  </tr>
  <tr>
   <td><p>calculate</p> </td>
   <td><p>Dem Calculate-Ausdruck im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>validate </p> </td>
   <td><p>Dem Validation-Ausdruck im adaptiven Formular zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>validationState </p> </td>
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht überschrieben werden.<br /> </p> </td>
  </tr>
  <tr>
   <td><p>exit </p> </td>
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht überschrieben werden.</p> </td>
  </tr>
  <tr>
   <td><p>click (Schaltflächen)</p> </td>
   <td><p>Dem Klickereignis-Ausdruck der Schaltfläche zugeordnet.</p> </td>
  </tr>
  <tr>
   <td><p>Unterstützung für Server-seitiges Skript</p> </td>
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht überschrieben werden.</p> </td>
  </tr>
  <tr>
   <td><p>Unterstützung für Web-Dienste</p> </td>
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht überschrieben werden.</p> </td>
  </tr>
  <tr>
   <td><p>Change (Scribble-Feld, Optionsschalter, Kontrollkästchen)</p> </td>
   <td><p>Dieses Skript wird zur Laufzeit ausgeführt und kann im adaptiven Formular nicht überschrieben werden.</p> </td>
  </tr>
 </tbody>
</table>

### Validierungen {#validations}

Die folgende Tabelle zeigt, wie XFA-Validierungen den Validierungen in adaptiven Formularen zugeordnet sind.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA-Validierung</strong></p> </td>
   <td><p><strong>Entsprechende Validierung im adaptiven Formular</strong></p> </td>
  </tr>
  <tr>
   <td><p>Validierungsmuster (formatTest)</p> </td>
   <td><p>validatePictureClause</p> </td>
  </tr>
  <tr>
   <td><p>Validierungsmuster-Meldung (formatTestMessage)</p> </td>
   <td><p>validatePictureMessage</p> </td>
  </tr>
  <tr>
   <td><p>Erforderlich (nullTest)</p> </td>
   <td><p>mandatory </p> </td>
  </tr>
  <tr>
   <td><p>Meldung bei leerem Feld (nullTestMessage) </p> </td>
   <td><p>mandatoryMessage</p> </td>
  </tr>
  <tr>
   <td><p>Skript validieren (scriptTest)</p> </td>
   <td><p>validateExp</p> </td>
  </tr>
  <tr>
   <td><p>Überprüfungsskript-Meldung (scriptTestMessage)</p> </td>
   <td><p>validateMessage</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Es ist nicht möglich, die obligatorische Eigenschaft für die Optionsfeld- und Kontrollkästchengruppe im adaptiven Formular außer Kraft zu setzen, die an XFA-Kontrollkästchen gebunden sind.
