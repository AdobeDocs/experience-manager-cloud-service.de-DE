---
title: Skriptunterstützung für HTML5-Formulare
description: JavaScript, FormCalc-Eigenschaften und andere Methoden, die in HTML5-Formularen unterstützt werden.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
feature: HTML5 Forms,Mobile Forms
exl-id: bcb5afc5-2190-4269-aba2-63842db9df3f
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '3916'
ht-degree: 100%

---

# Skriptunterstützung für HTML5-Formulare {#scripting-support-for-html-forms}

Die folgenden JavaScript, FormCalc-Eigenschaften und Methoden werden in HTML5-Formularen unterstützt:

## $event {#event}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft </th>
   <th>Beschreibung<br /> </th>
   <th>Ausnahme</th>
  </tr>
  <tr>
   <td><code>prevText</code></td>
   <td>Gibt den Inhalt des Felds vor einer Änderung aufgrund von Benutzeraktionen an. Dieser Wert kann ähnlich wie bei einer Rückgängig-Funktion erneut aufgerufen werden.</td>
   <td><p>Er funktioniert nicht mit Dropdown-Menüs und Listenfeldern. <code>PrevText </code>funktioniert in folgenden Fällen nicht:</p>
    <ul>
     <li>Beim Eingeben von bestimmten Sonderzeichen (z. B. $ oder , oder &amp; oder @) in ein numerisches Feld auf einem iPad und </li>
     <li>Im Datumsfeld (wenn das Datum über den Kalender eingetragen wird).<br /> </li>
    </ul> <p>Das Festlegen eines Werts mithilfe eines Skripts wird nicht unterstützt.</p> </td>
  </tr>
  <tr>
   <td><code>target</code></td>
   <td>Gibt das Objekt an, für das das Ereignis ausgeführt wird.</td>
   <td>Das Festlegen eines Werts mithilfe eines Skripts wird nicht unterstützt.<br /> </td>
  </tr>
  <tr>
   <td><code>newtext</code></td>
   <td>Gibt den Inhalt des Feldes nach einer Änderung aufgrund von Benutzeraktionen an.</td>
   <td><p>Die Eigenschaft <code>newText</code> funktioniert in folgenden Fällen nicht ordnungsgemäß:</p>
    <ul>
     <li>Beim Markieren und Ersetzen von Texten</li>
     <li>Beim Löschen, Kopieren und Einfügen von Texten</li>
     <li>Beim Eingeben von bestimmten Sonderzeichen (z. B. $ oder , oder &amp; oder @) in numerische Felder<br /> </li>
     <li>Beim Verwenden der Kombination Umschalttaste+alphanumerisches Zeichen. </li>
     <li>Beim Verwenden von Datums- und Uhrzeitfeldern</li>
    </ul>
    <div>
      Das Festlegen eines Werts mithilfe eines Skripts wird nicht unterstützt.
    </div> </td>
  </tr>
  <tr>
   <td>ändern</td>
   <td>Gibt den Wert an, den Sie unmittelbar nach der Durchführung der Aktion in ein Feld eingeben oder einfügen. </td>
   <td><p>Die Eigenschaft „Ändern“ funktioniert in folgenden Fällen nicht ordnungsgemäß:</p>
    <ul>
     <li>Beim Markieren und Ersetzen von Texten</li>
     <li>Beim Löschen, Kopieren und Einfügen von Texten</li>
     <li>Beim Eingeben von bestimmten Sonderzeichen (z. B. $ oder , oder &amp; oder @) in numerische Felder<br /> </li>
     <li>Beim Verwenden der Kombination Umschalttaste+alphanumerisches Zeichen. </li>
     <li>Beim Verwenden von Datums- und Uhrzeitfeldern</li>
    </ul> <p>Das Festlegen eines Werts mithilfe eines Skripts wird nicht unterstützt.</p> </td>
  </tr>
  <tr>
   <td>keyDown</td>
   <td>Stellt fest, ob Benutzende die Auswahl durch Drücken einer Pfeiltaste treffen. Diese Eigenschaft ist nur für Listenfelder und Dropdown-Listen verfügbar.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>modifier</td>
   <td>Legt fest, ob bei Ausführung eines bestimmten Ereignisses die Modifizierungstaste (beispielsweise Strg unter Microsoft® Windows®) gedrückt wird.</td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

### $host {#host}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
   <th>Ausnahme</th>
  </tr>
  <tr>
   <td><code>apptype</code></td>
   <td>Gibt den Anwendungstyp des Hosts zurück. Nur für Client-Anwendungen verfügbar.</td>
   <td>Rückgabe <code>HTML 5</code>.</td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td>Gibt den Namen der aktuellen Anwendung zurück.</td>
   <td>Gibt den Browsernamen und die Version zurück. Beim Browser Chrome wird beispielsweise folgender Wert zurückgegeben: <code>Chrome &lt;version&gt;.</code></td>
  </tr>
  <tr>
   <td><code>numPages</code></td>
   <td>Gibt die Anzahl der Seiten im Dokument zurück.</td>
   <td>Die Paginierungsrichtlinie in HTML5-Formularen unterscheidet sich von der entsprechenden Richtlinie in PDF-Formularen. Die numPages-API gibt daher in den beiden Fällen eventuell unterschiedliche Werte zurück.</td>
  </tr>
  <tr>
   <td><code>platform</code></td>
   <td>Gibt eine Zeichenfolge zurück, die für die Plattform des Computers steht, auf dem das Skript ausgeführt wird.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>title</code></td>
   <td>Gibt den Titel des Dokuments an. Nur für Client-Anwendungen verfügbar.</td>
   <td>Gibt nicht wie im Fall von PDF-Formularen den Metadatentitel des Formulars, sondern den Titel des HTML-Dokuments im Formular zurück.</td>
  </tr>
  <tr>
   <td><code>version</code></td>
   <td>Gibt eine Zeichenfolge zurück, die die Versionsnummer der aktuellen Anwendung darstellt.</td>
   <td>Gibt die Version des Formulars zurück.</td>
  </tr>
  <tr>
   <td><code>calculationsEnabled</code></td>
   <td>Gibt an, ob Berechnungsskripte ausgeführt werden.<br /> </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>validationsEnabled</code></td>
   <td>Gibt an, ob Überprüfungsskripte ausgeführt werden.<br /> </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>pageUp</code></td>
   <td>Wechselt zur vorherigen Seite.</td>
   <td>HTML5-Formulare folgen nicht derselben Paginierungsrichtlinie wie PDF-Formulare. Daher unterscheidet sich die vorherige Seite eines HTML5-Formulars von der vorherigen Seite eines PDF-Formulars.</td>
  </tr>
  <tr>
   <td><code>pageDown</code></td>
   <td>Wechselt zur nächsten Seite eines Formulars. Verwendet die pageDown-Methode zur Laufzeit.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>setFocus</code></td>
   <td>Stellt den Tastaturfokus auf das angegebene Feld ein. Das Feld wird als Objekt oder durch den SOM-Ausdruck des Felds definiert. Nur für Client-Anwendungen verfügbar.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>resetdata</code></td>
   <td>Setzt die Felder auf ihre Standardwerte in einem Dokument zurück.</td>
   <td>Löscht alle Daten in einem Formular mit zusammengeführten Daten, anstatt die Standardwerte wiederherzustellen.</td>
  </tr>
  <tr>
   <td><code>messageBox</code></td>
   <td>Zeigt ein Dialogfeld auf dem Bildschirm an. Nur für Client-Anwendungen verfügbar.</td>
   <td>Das Meldungsfeld vom Typ „Ja/Nein“ wird in ein Feld vom Typ „OK/Abbrechen“ konvertiert. Ein Meldungsfeld mit drei Schaltflächen wird nicht unterstützt.</td>
  </tr>
  <tr>
   <td>currentPage</td>
   <td><p>Legt die aktuell aktive Seite eines Dokuments zur Laufzeit fest.</p> <p>Seitenzahlen sind 0-basiert, d. h., die erste Seite eines Dokuments gibt den Wert 0 zurück.</p> <p>Die currentPage-Eigenschaft ist verfügbar, wenn „layout:ready“ auf einem Client ausgeführt wird. Sie ist jedoch nicht verfügbar, wenn „layout:ready“ auf dem Server ausgeführt wird, da die Eigenschaft nur in Verbindung mit dem Formular-Layout ausgeführt wird.</p> </td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

### field {#field}

<table>
 <tbody>
  <tr>
   <th><strong><span>Eigenschaft</span></strong></th>
   <th><strong><span>Beschreibung<br /> </span></strong></th>
   <th><strong><span>Ausnahme</span></strong></th>
  </tr>
  <tr>
   <td><code>presence</code></td>
   <td>Steuert die Teilnahme des zugehörigen Objekts in den verschiedenen Phasen der Verarbeitung. Wenn das Objekt ein Container ist, werden alle Einschränkungen dieses Steuerelements für den Inhalt des Containers übernommen.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>access</code></td>
   <td>Steuert den Benutzerzugriff auf den Inhalt.</td>
   <td>Funktioniert nicht mit die Ausschlussgruppe. Außerdem werden nicht interaktive und geschützte Objekte in HTML5-Formularen auf dieselbe Weise behandelt.<br /> </td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td>Eine Kennung, die verwendet wird, um dieses Element in Skriptausdrücken eindeutig zu kennzeichnen.</td>
   <td>In HTML5-Formulare kann die Eigenschaft „name“ nicht für Objekte festgelegt werden. Es handelt sich um eine schreibgeschützte Eigenschaft für HTML5-Formulare.</td>
  </tr>
  <tr>
   <td><code>value</code></td>
   <td>Ein Inhaltselement, das eine Dateninhaltseinheit umfasst.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>rawValue</code></td>
   <td>Gibt den nicht formatierten Wert für dieses Feld an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>formattedValue</code></td>
   <td>Gibt den formatierten Wert für dieses Feld an.</td>
   <td>Das Festlegen des Werts <code>formattedValue</code> mithilfe eines Skripts wird nicht unterstützt.</td>
  </tr>
  <tr>
   <td><code>editValue</code></td>
   <td>Gibt den bearbeiteten Wert für dieses Feld an.</td>
   <td>Das Festlegen des Werts <code>editValue </code> mithilfe eines Skripts wird nicht unterstützt.</td>
  </tr>
  <tr>
   <td><code>formatMessage</code></td>
   <td>Gibt die Zeichenfolge der Meldung zur Formatprüfung für dieses Feld an.</td>
   <td>Das Festlegen des Werts <code>formatMessage </code> mithilfe eines Skripts wird nicht unterstützt.</td>
  </tr>
  <tr>
   <td><code>fillcolor</code></td>
   <td>Gibt den Wert der Hintergrundfarbe für dieses Feld an. Sie müssen die Eigenschaft border.fill.presence separat als sichtbar einstellen.</td>
   <td>Sie gibt die Standardfarbe des Feldes nicht richtig zurück.</td>
  </tr>
  <tr>
   <td><code>border</code></td>
   <td>Das border-Objekt beschreibt den Rahmen, der ein Objekt umgibt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>ui</code></td>
   <td>Das ui-Objekt umfasst die Beschreibung der Benutzeroberfläche eines Formularobjekts.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>mandatory</code></td>
   <td>Gibt den nullTest-Wert für das Feld an.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>borderColor</code></td>
   <td>Gibt den Rahmenfarbwert für dieses Feld an. Sie müssen die Eigenschaft border.edge.presence separat als sichtbar einstellen.</td>
   <td>Sie gibt die Standardfarbe des Feldes nicht richtig zurück.</td>
  </tr>
  <tr>
   <td><code>length</code></td>
   <td>Die Anzahl der Elemente in der Liste.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>addItem</code></td>
   <td>Fügt dem aktuellen Feld neue Elemente hinzu.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>clearItem</code></td>
   <td>Entfernt alle Elemente aus dem Feld.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>boundItem</code></td>
   <td>Ruft den Bindewert eines bestimmten Anzeigeelements aus einer Dropdown-Liste oder aus einem Listenfeld ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>execCalculate</code></td>
   <td>Führt das Berechnungsskript des Feldes aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>execValidate</code></td>
   <td>Führt das Überprüfungsskript des Feldes aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>execEvent</code></td>
   <td>Führt das Ereignisskript des Objekts aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>getItemState</code></td>
   <td>Gibt den Auswahlstatus des angegebenen Elements zurück.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>setItemState</code></td>
   <td>Legt den Auswahlstatus des angegebenen Elements fest.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>getDisplayItem</code></td>
   <td>Ruft den Elementanzeigetext für den angegebenen Elementindex ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>getSaveItem</code></td>
   <td>Ruft den Datenwert für den angegebenen Elementindex ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>deleteItem</code></td>
   <td>Entfernt das Element an der angegebenen Indexposition.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>setItems</code></td>
   <td>Legt die angegebenen Elemente im aktuellen Feld fest. Ersetzt die bereits vorhandenen Elemente.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Eine Maßeinheit für die Höhe des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Eine Maßeinheit für die Breite des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Gibt die X-Koordinate für den Ankerpunkt des Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung anhand eines positionierten Layouts an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Gibt die Y-Koordinate für den Ankerpunkt eines Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung anhand eines positionierten Layouts an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>caption</td>
   <td>Das caption-Objekt stellt eine beschreibende Beschriftung dar, die mit einem Formularentwurfsobjekt verknüpft ist.<br /> </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Das validate-Objekt steuert die Überprüfung von Daten, die benutzerseitig in einem Formular eingegeben werden. Das validate-Objekt kann während der Lebensdauer eines Formulars mehrmals aktiviert werden.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>parentSubform</td>
   <td>Gibt das übergeordnete Teilformular (Seite) dieses Felds an.</td>
   <td>Gibt immer übergeordnete Teilformulare zurück statt zuerst übergeordnete Teilformulare ohne Scoping.<br /> </td>
  </tr>
  <tr>
   <td>selectedIndex</td>
   <td>Der Index des ersten ausgewählten Elements.</td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## Formular {#form}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| formNodes | Gibt eine Liste mit allen Formularmodellobjekten zurück, die an ein bestimmtes Datenobjekt gebunden sind. |  |

## InstanceManager {#instancemanager}

| Eigenschaft | Beschreibung |
|---|---|
| `name` | Ein Bezeichner, der verwendet wird, um dieses Element in Skriptausdrücken eindeutig zu kennzeichnen. |
| `occur` | Beschreibt die Einschränkungen in Bezug auf die Anzahl der zulässigen Instanzen für den zugehörigen einschließenden Container. |
| `min` | Gibt die Mindestanzahl der Instanzen an, die instanziiert werden können. |
| `max` | Gibt die Höchstanzahl der Instanzen an, die instanziiert werden können. |
| `count` | Gibt die aktuelle Anzahl der instanziierten Instanzen an. |
| `setInstances` | Fügt die angegebenen Teilformulare oder Teilformularsätze von diesem Knoten zurück oder entfernt diese. |
| `addInstance` | Fügt diese Knoten eine neue Instanz eines Teilformulars oder Teilformularsatzes hinzu. |
| `removeInstance` | Entfernt ein Teilformular oder einen Teilformularsatz von diesem Knoten. |
| `moveInstance` | Verschiebt ein untergeordnetes Objekt eines Formularmodellobjekts an einen anderen angegebenen Speicherort innerhalb des Formularmodells. Die entsprechenden Datenmodellinformationen für das Objekt ziehen innerhalb des Datenmodells ebenfalls um. |
| `insertInstance` | Fügt diesem Knoten eine neue Instanz eines Teilformulars oder Teilformularsatzes hinzu. |

## list {#list}

| Eigenschaft | Beschreibung |
|---|---|
| `length` | Die Anzahl der Elemente in der Liste. |
| `item` | Index auf der Basis Null zur Sammlung. |
| `append` | Fügt am Ende der Liste der Nodes eine Node an. |
| `remove` | Entfernt einen Knoten aus der Knotenliste. |
| `insert` | Fügt einen Knoten vor einem bestimmten Knoten in die Knotenliste ein. |

## node {#node}

| Eigenschaft | Beschreibung | Ausnahme |
|---|---|---|
| createNode | Erstellt einen neuen Knoten basierend auf einem gültigen Klassennamen. | Ohne |
| `isContainer` | Gibt an, ob dieses Objekt ein Container-Objekt ist. | Ohne |
| `isNull` | Gibt an, ob der aktuelle Datenwert ein Nullwert ist. | Ohne |
| `resolveNode` | Wertet den angegebenen SOM-Ausdruck aus, angefangen mit dem aktuellen Objekt des XML-Formularobjektmodells, und gibt den Wert des im SOM-Ausdruck angegebenen Objekts zurück. | Ohne |
| `resolveNodes` | Wertet den angegebenen SOM-Ausdruck aus, angefangen mit dem aktuellen Objekt des XML-Formularobjektmodells, und gibt den Wert des im SOM-Ausdruck angegebenen Objekts zurück. | Ohne |
| oneOfChild | Erstellt einen neuen Knoten basierend auf einem gültigen Klassennamen. | Ohne |
| getElement | Gibt ein bestimmtes untergeordnetes Objekt zurück. | Ohne |
| getAttribute | Ruft den Wert einer angegebenen Eigenschaft ab. | Ohne |
| setAttribute | Legt den Wert einer angegebenen Eigenschaft fest. | Ohne |

## model {#model}

| Eigenschaft | Beschreibung | Ausnahme |
|---|---|---|
| nicht vorhanden | nicht vorhanden | nicht vorhanden |

## Teilformular {#subform}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
   <th>Ausnahme</th>
  </tr>
  <tr>
   <td>instanceIndex</td>
   <td>Gibt den Index des Objekts relativ zu den anderen instanziierten Instanzen an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>execEvent</td>
   <td>Führt das Ereignisskript des Objekts aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>getInvalidObjects</td>
   <td>Gibt eine Liste von Knoten in dem Teilformular (einschließlich) zurück, bei denen der Test zur Überprüfung fehlgeschlagen ist.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>border</td>
   <td>Das border-Objekt beschreibt den Rahmen, der ein Objekt umgibt.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>borderColor</td>
   <td>Gibt den Rahmenfarbwert für dieses Feld an. Sie müssen die Eigenschaft border.edge.presence separat als sichtbar einstellen.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Eine Maßeinheit für die Höhe des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Eine Maßeinheit für die Breite des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Gibt die X-Koordinate für den Ankerpunkt des Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung anhand eines positionierten Layouts an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Gibt die Y-Koordinate für den Ankerpunkt eines Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung anhand eines positionierten Layouts an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Das validate-Objekt steuert die Überprüfung von Daten, die benutzerseitig in einem Formular eingegeben werden. Das validate-Objekt kann während der Lebensdauer eines Formulars mehrmals aktiviert werden.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>name</td>
   <td>Eine Kennung, die verwendet wird, um dieses Element in Skriptausdrücken eindeutig zu kennzeichnen.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Gibt die Sichtbarkeit eines Objekts an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>access</td>
   <td>Steuert den Benutzerzugriff auf den Inhalt eines Container-Objekts, beispielsweise ein Teilformular.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>execValidate</td>
   <td>Berechnet den Index eines Teilformulars oder Teilformularsatzes anhand dessen Position im Verhältnis zu anderen Instanzen des gleichen Formularobjekts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>InstanceManager</td>
   <td>Das instanceManager-Objekt verwaltet das Erstellen, Entfernen und Verschieben einer Instanz von Formularmodellobjekten.<br /> </td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

### submit {#submit}

| Eigenschaft | Beschreibung |
|---|---|
| target | Die URL, an die die Daten gesendet werden. Bei Auslassung dieses Attributs ruft die XFA-Verarbeitungsanwendung den URI mithilfe eines produktspezifischen Verfahrens ab, z. B. durch Zugreifen auf produktspezifische Informationen im config-Objekt. |

## tree {#tree}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
   <th>Ausnahme</th>
  </tr>
  <tr>
   <td>Knoten</td>
   <td>Gibt eine Liste aller untergeordneten Objekte des aktuellen Objekts zurück.</td>
   <td>
    <ul>
     <li>Nicht unterstützt für xfa.nodes, desc</li>
     <li>Unterschiedliche Anzahl der für PDF und HTML übermittelten Knoten. </li>
    </ul> </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Gibt den Namen dieses Knotens an.</td>
   <td>In HTML kann der Name mithilfe von Skripten nicht festgelegt werden.</td>
  </tr>
  <tr>
   <td>parent</td>
   <td>Ruft den übergeordneten Knoten dieses Knotens ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>index</td>
   <td>Gibt die Position dieses Knotens in der zugehörigen Sammlung von untergeordneten Knoten mit gleichen Namen im Bereich zurück.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>somExpression</td>
   <td>Ruft den SOM-Ausdruck für diesen Knoten ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>resolveNode</td>
   <td>Wertet den angegebenen SOM-Ausdruck aus, angefangen mit dem aktuellen Objekt des XML-Formularobjektmodells, und gibt den Wert des im SOM-Ausdruck angegebenen Objekts zurück.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>resolveNodes</td>
   <td>Wertet den angegebenen SOM-Ausdruck aus, angefangen mit dem aktuellen Objekt des XML-Formularobjektmodells, und gibt den Wert des im SOM-Ausdruck angegebenen Objekts zurück.</td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## subformset {#subformset}

| Eigenschaft | Beschreibung | Ausnahme |
|---|---|---|
| InstanceManager | Das instanceManager-Objekt verwaltet das Erstellen, Entfernen und Verschieben einer Instanz von Formularmodellobjekten. | Ohne |

## content {#content}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| isNull | Gibt an, ob der aktuelle Datenwert der Nullwert ist. |  |

## dataValue {#datavalue}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| isNull | Gibt an, ob der aktuelle Datenwert der Nullwert ist. |  |

## edge {#edge}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft </strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Eigenschaft „color“ beschreibt eine eindeutige Farbe für das Musterobjekt.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell angezeigt und sind zur Skripterstellung verfügbar, werden aber nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht auf der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## fill {#fill}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die color-Eigenschaften legen eine eindeutige Füllfarbe fest.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell angezeigt und sind zur Skripterstellung verfügbar, werden aber nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht auf der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## linear {#linear}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die color-Eigenschaft beschreibt eine eindeutige Farbe für einen linearen Farbverlauf in einem Formular.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell angezeigt und sind zur Skripterstellung verfügbar, werden aber nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht auf der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Zeile {#line}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Das edge-Objekt beschreibt einen Bogen, eine Linie oder eine Seite eines Rahmens oder Rechtecks.<br /> </td>
   <td>Attribute wie „color“, „cap“ usw. werden nicht unterstützt.<br /> </td>
  </tr>
 </tbody>
</table>

## pattern {#pattern}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Eigenschaft „color“ beschreibt eine eindeutige Farbe für das Musterobjekt. </td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell angezeigt und sind zur Skripterstellung verfügbar, werden aber nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht auf der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## radial {#radial}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die color-Eigenschaft beschreibt eine eindeutige Farbe für das radial-Objekt.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell angezeigt und sind zur Skripterstellung verfügbar, werden aber nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht auf der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## stipple {#stipple}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die color-Eigenschaft beschreibt eine eindeutige Farbe für das stipple-Objekt.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell angezeigt und sind zur Skripterstellung verfügbar, werden aber nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht auf der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## draw {#draw}

<table>
 <tbody>
  <tr>
   <td>Eigenschaft</td>
   <td>Beschreibung</td>
   <td>Ausnahme</td>
  </tr>
  <tr>
   <td>ui</td>
   <td>Das ui-Objekt umfasst die Beschreibung der Benutzeroberfläche eines Formularobjekts.<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td>caption</td>
   <td>Das caption-Objekt beschreibt eine beschreibende Bezeichnung, die mit einem Formularentwurfsobjekt verknüpft ist.</td>
   <td> </td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Gibt die Sichtbarkeit eines Objekts an.</td>
   <td> </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Gibt eine Kennung an, mit der dieses Objekt oder Ereignis in Skriptausdrücken angegeben werden kann.</td>
   <td>Die Festlegung des Werts zur Laufzeit wird nicht unterstützt</td>
  </tr>
  <tr>
   <td>value</td>
   <td>Das value-Objekt umfasst eine einzige Dateninhaltseinheit.<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

## corner {#corner}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die color-Eigenschaft beschreibt eine eindeutige Farbe für das corner-Objekt.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell angezeigt und sind zur Skripterstellung verfügbar, werden aber nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht auf der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## checkButton {#checkbutton}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Das border-Objekt beschreibt den Rahmen, der das checkButton-Objekt umgibt. </td>
   <td>Die Änderungen werden im Modell angezeigt und sind zur Skripterstellung verfügbar, werden aber nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht auf der Benutzeroberfläche angezeigt.<br /> </td>
  </tr>
 </tbody>
</table>

## choiceList {#choicelist}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<br /> </strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Das border-Objekt beschreibt den Rahmen, der das choiceList-Objekt umgibt.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## dateTimeEdit {#datetimeedit}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| border | Das border-Objekt beschreibt den Rahmen, der das dateTimeEdit-Objekt umgibt. |  |

## Bild {#image}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>contentType</td>
   <td>Gibt den Inhaltstyp im referenzierten Dokument an, ausgedrückt als MIME-Typ.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>name<br /> </td>
   <td>Eine Kennung, die verwendet wird, um dieses Element in Skriptausdrücken eindeutig zu kennzeichnen.</td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## imageEdit {#imageedit}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| border | Das border-Objekt beschreibt den Rahmen, der das imageEdit-Objekt umgibt. |  |

## numericEdit {#numericedit}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| border | Das border-Objekt beschreibt den Rahmen, der ein Objekt umgibt. | keine |

## object {#object}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>className</td>
   <td>Legt den Namen der Klasse dieses Objekts fest.<br /> </td>
   <td>keine</td>
  </tr>
 </tbody>
</table>

## rectangle {#rectangle}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Das edge-Objekt beschreibt einen Bogen, eine Linie oder eine Seite eines Rahmens oder Rechtecks.<br /> </td>
   <td>Attribute wie „color“, „cap“ usw. werden nicht unterstützt.</td>
  </tr>
 </tbody>
</table>

## textEdit {#textedit}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Das border-Objekt beschreibt den Rahmen, der ein Objekt umgibt.<br /> </td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## exclGroup {#exclgroup}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>layout</td>
   <td>Gibt die von diesem Objekt zu verwendende Layout-Strategie an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>border</td>
   <td>Gibt den Rahmen an, der dieses Feld umgibt.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>mandatory</td>
   <td>Gibt den nullTest-Wert für das Feld an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>borderColor</td>
   <td>Gibt den Rahmenfarbwert für dieses Feld an. Bevor die Farbe mithilfe der Skripterstellung geändert werden kann, muss ein Rahmen definiert werden.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>borderWidth</td>
   <td>Gibt die Rahmenbreite für dieses Feld an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Eine Maßeinheit für die Höhe des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>transient</td>
   <td>Gibt an, ob die verarbeitende Anwendung den Wert der Ausschlussgruppe im Rahmen eines Formularsende- oder -speichervorgangs speichern muss.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Eine Maßeinheit für die Breite des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Gibt die X-Koordinate für den Ankerpunkt des Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung anhand eines positionierten Layouts an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Gibt die Y-Koordinate für den Ankerpunkt eines Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung anhand eines positionierten Layouts an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>caption</td>
   <td>Das caption-Objekt stellt eine beschreibende Beschriftung dar, die mit einem Formularentwurfsobjekt verknüpft ist.<br /> </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Das validate-Objekt steuert die Überprüfung von Daten, die benutzerseitig in einem Formular eingegeben werden. Das validate-Objekt kann während der Lebensdauer eines Formulars mehrmals aktiviert werden.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>dataNode</td>
   <td>Ruft den Datenknoten ab, an den ein Formularknoten nach dem Zusammenführen gebunden ist.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Gibt die Sichtbarkeit eines Objekts an.</td>
   <td> </td>
  </tr>
  <tr>
   <td>access</td>
   <td>Steuert den Benutzerzugriff auf den Inhalt eines Container-Objekts, beispielsweise ein Teilformular.</td>
   <td>Wird für einzelne Elemente der exclgrp immer offen zurückgegeben. </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Gibt eine Kennung an, mit der dieses Objekt oder Ereignis in Skriptausdrücken angegeben werden kann.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>members</td>
   <td>Gibt die Elemente einer Ausschlussgruppe an. </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>selectedMember</td>
   <td>Gibt das ausgewählte Element einer Ausschlussgruppe zurück.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>execCalculate</td>
   <td>Führt Skripte für das calculate-Ereignis des angegebenen Objekts und etwaiger untergeordneter Objekte aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>calculate</td>
   <td>Das calculate-Objekt steuert die Berechnung des Werts eines Felds.<br /> </td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## arc {#arc}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<strong></strong></strong></td>
   <td><strong>Beschreibung<strong></strong></strong></td>
   <td><strong>Ausnahme<strong></strong></strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Das edge-Objekt beschreibt einen Bogen, eine Linie oder eine Seite eines Rahmens oder Rechtecks.<br /> </td>
   <td>Attribute wie „color“, „cap“ usw. werden nicht unterstützt. </td>
  </tr>
 </tbody>
</table>

## border {#border}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<strong></strong></strong></td>
   <td><strong>Beschreibung<strong></strong></strong></td>
   <td><strong>Ausnahme<strong></strong></strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Das edge-Objekt beschreibt einen Bogen, eine Linie oder eine Seite eines Rahmens oder Rechtecks.<br /> </td>
   <td>Attribute wie „color“, „cap“ usw. werden nicht unterstützt. </td>
  </tr>
 </tbody>
</table>

## $layout {#layout}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>h</td>
   <td>Bestimmt die Höhe eines angegebenen Formularentwurfsobjekts.<br /> </td>
   <td>
    <ul>
     <li>Die Eigenschaft „Höhe“ (h) wird für Seiten- und Inhaltsbereiche nicht unterstützt. </li>
     <li>Parameter „Offset vom ersten Inhaltsbereich, in dem das XFA-Formularobjekt auftritt“ wird nicht unterstützt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>w</td>
   <td>Bestimmt die Breite eines angegebenen Formularentwurfsobjekts.</td>
   <td>
    <ul>
     <li>Die Eigenschaft „Breite“ (w) wird für Seiten- und Inhaltsbereiche nicht unterstützt. </li>
     <li>Parameter „Offset vom ersten Inhaltsbereich, in dem das XFA-Formularobjekt auftritt“ wird nicht unterstützt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>x</td>
   <td>Bestimmt die X-Koordinate eines angegebenen Formularentwurfsobjekts relativ zum übergeordneten Objekt.</td>
   <td>
    <ul>
     <li>Die Eigenschaft „X-Koordinate“ (x) wird für Seiten- und Inhaltsbereiche nicht unterstützt. </li>
     <li>Parameter „Offset vom ersten Inhaltsbereich, in dem das XFA-Formularobjekt auftritt“ wird nicht unterstützt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>y</td>
   <td>Bestimmt die Y-Koordinate eines angegebenen Formularentwurfsobjekts relativ zum übergeordneten Objekt.</td>
   <td>
    <ul>
     <li>Die Eigenschaft „Y-Koordinate“ (y) wird für Seiten- und Inhaltsbereiche nicht unterstützt. </li>
     <li>Parameter „Offset vom ersten Inhaltsbereich, in dem das XFA-Formularobjekt auftritt“ wird nicht unterstützt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>pagecount</td>
   <td>Bestimmt die Anzahl der Seiten des aktuellen Formulars.</td>
   <td>
    <ul>
     <li>Die Methode „layout.pageCount()“ gibt unterschiedliche Werte für PDF- und HTML-Formulare zurück.</li>
     <li>Die Methode „absPageCount“ gibt bei geringerer Seitenzahl durch ausgeblendete Objekte einen falschen Wert zurück.<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>pagecontent</td>
   <td>Ruft Formularentwurfsobjekttypen von einer angegebenen Seite eines Formulars ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>absPageCount</td>
   <td>Bestimmt die Seitenzahl des aktuellen Formulars.</td>
   <td>
    <ul>
     <li>Die Methode „layout.pageCount()“ gibt unterschiedliche Werte für PDF- und HTML-Formulare zurück.</li>
     <li>Die Methode „absPageCount“ gibt bei geringerer Seitenzahl durch ausgeblendete Objekte einen falschen Wert wieder.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## items {#items}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| presence | Gibt die Sichtbarkeit eines Objekts an. | Ohne |

## FormCalc {#formcalc}

„FormCalc“ ist eine XFA-spezifische Sprache zum Erstellen von E-Formular-orientierter Logik und Berechnungsstämmen. „FormCalculation“ stellt einen umfangreichen Satz an Erstellungsfunktionen bereit.

### Von FormCalc unterstützte Funktionen {#formcalc-supported-functions}

### Von FormCalc unterstützte Ausdrücke {#formcalc-expression-support}

<table>
 <tbody>
  <tr>
   <td><strong>Kategorie </strong></td>
   <td><strong>Beschreibung </strong></td>
   <td><strong>Beispiel </strong></td>
  </tr>
  <tr>
   <td>Einfacher Ausdruck</td>
   <td>Addieren, subtrahieren, multiplizieren, dividieren und Klammern</td>
   <td>(a+b)*3</td>
  </tr>
  <tr>
   <td>Variablendeklaration</td>
   <td>Definieren einer Variablen</td>
   <td>var a<br /> var a=3<br /> a=3</td>
  </tr>
  <tr>
   <td>Logischer Ausdruck</td>
   <td>
    <ul>
     <li>Logik (und/oder)</li>
     <li>Vergleich (größer/kleiner/gleich)</li>
    </ul> </td>
   <td>A oder 1<br /> 1 &lt;&gt; 2<br /> A NE B<br /> A oder 1<br /> 1 &lt;&gt; 2<br /> A NE B</td>
  </tr>
  <tr>
   <td>If-Ausdruck</td>
   <td><br type="_moz" /> </td>
   <td>if (a&gt;b) then 2 endif</td>
  </tr>
  <tr>
   <td>Zeit</td>
   <td><br type="_moz" /> </td>
   <td>while (i lt 5) do i = i + 1 endwhile</td>
  </tr>
  <tr>
   <td> für </td>
   <td><br type="_moz" /> </td>
   <td>for i = 100 downto 1 <br /> do s = s + i endfor</td>
  </tr>
  <tr>
   <td>for each</td>
   <td><br type="_moz" /> </td>
   <td>for each i in (1, 2, 3) <br /> do s = s + i endfor</td>
  </tr>
  <tr>
   <td>Funktionsdeklaration</td>
   <td>Definieren einer benutzerdefinierten Funktion in FormCalc</td>
   <td>func foo(n) do var f = n endfunc</td>
  </tr>
 </tbody>
</table>

### Acrobat-API-Unterstützung {#acrobat-api-support}

1. **Arithmetik-Funktionen**

   1. Abs()
   1. Avg()
   1. Ceil()
   1. Anzahl()
   1. Floor()
   1. Maximal()
   1. Min()
   1. Mod()
   1. Round()
   1. Sum()

1. **Wissenschaftliche Funktionen**

   1. Acos()
   1. Asin()
   1. Atan()
   1. Atan2()
   1. Cos()
   1. Sin()
   1. Tan()
   1. Exp()
   1. Log()
   1. Pow()
   1. Sqrt()
   1. Deg2Rad()
   1. Rad2Deg()
   1. Pi()

1. **Finanzfunktionen**

   1. Apr()
   1. Cterm()
   1. Fv()
   1. Ipmt()
   1. Npv()
   1. Pmt()
   1. Ppmt()
   1. Pv()
   1. Rate()
   1. Begriff()

1. **Logikfunktionen**

   1. Choose()
   1. If()
   1. Oneof()
   1. Within()

1. **Zeichenfolgen-Funktionen**

   1. At()
   1. Concat()
   1. Left()
   1. Len()
   1. Lower()
   1. Ltrim()
   1. Ersetzen()
   1. Right()
   1. Rtrim()
   1. Space()
   1. Stuff()
   1. Substr()
   1. Upper()
   1. WordNum()

1. **Datum und Uhrzeit**

   1. Datum()
   1. num2date()
   1. DateFmt()

<table>
 <tbody>
  <tr>
   <td><strong>API</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Abweichung</strong></td>
  </tr>
  <tr>
   <td>console.println()</td>
   <td>Diese Acrobat-API gibt die Ausgabe an die JavaScript-Konsole aus.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.alert()</td>
   <td>Diese Acrobat-API sendet eine Warnmeldung als JavaScript-Popup.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.beep()</td>
   <td>Lässt das System einen Ton abspielen.</td>
   <td>Es wird keine Aktion ausgeführt.</td>
  </tr>
  <tr>
   <td>app.execDialog()</td>
   <td>Zeigt Benutzenden ein modales Dialogfeld an. Modale Dialogfelder müssen zuerst geschlossen werden, um die Host-Anwendung direkt wieder verwenden zu können.</td>
   <td>Es wird keine Aktion ausgeführt.<br /> </td>
  </tr>
  <tr>
   <td>app.launchURL()</td>
   <td>Startet eine URL in einem Browser-Fenster.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.setInterval()</td>
   <td>Gibt ein JavaScript-Skript und einen Zeitraum an. Das Skript wird jedes Mal ausgeführt, wenn dieser Zeitraum abgelaufen ist. Der Rückgabewert dieser Methode muss in einer JavaScript-Variable erfasst werden. Andernfalls unterliegt das Intervallobjekt der Garbage Collection und die Uhr würde angehalten werden. Um die regelmäßige Ausführung zu beenden, übergeben Sie das zurückgegebene Intervallobjekt an clearInterval.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.setTimeOut()</td>
   <td>Gibt ein JavaScript-Skript und einen Zeitraum an. Das Skript wird nur einmal nach dem Ablauf des Zeitraums ausgeführt. Der Rückgabewert dieser Methode muss in einer JavaScript-Variable erfasst werden. Andernfalls unterliegt das Zeitüberschreitungsobjekt der Garbage Collection und die Uhr würde angehalten werden. Um das Zeitüberschreitungsereignis zu beenden, übergeben Sie das zurückgegebene Zeitüberschreitungsobjekt an clearTimeOut.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.clearInterval()</td>
   <td>Bricht ein zuvor registriertes Intervall ab, das anfangs mit der Methode setInterval festgelegt wurde.</td>
   <td>Die API wird in HTML5-Formularen nicht ordnungsgemäß ausgeführt.</td>
  </tr>
  <tr>
   <td>app.clearTimeOut()</td>
   <td>Bricht ein zuvor registriertes Zeitüberschreitungsintervall ab. Ein solches Intervall wird anfangs mit setTimeOut festgelegt.</td>
   <td>Die API wird in HTML5-Formularen nicht ordnungsgemäß ausgeführt.<br /> </td>
  </tr>
  <tr>
   <td>app.eval()</td>
   <td>Führt ein bestimmtes Skript aus.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.activeDocs</td>
   <td>Ein Array, das das doc-Objekt für jedes aktive Dokument enthält. Wenn keine Dokumente aktiv sind, gibt activeDocs keinen Wert zurück. Das heißt, es weist das gleiche Verhalten auf wie d = new Array(0) im Core-JavaScript.</td>
   <td>Gibt ein leeres Array für HTML5-Formulare zurück.</td>
  </tr>
  <tr>
   <td>app.calculate</td>
   <td>Wenn „true“ (Standardwert), können Berechnungen ausgeführt werden. Wenn „false“, werden keine Berechnungen zugelassen.</td>
   <td>Bei HTML5-Formularen ist der Wert immer „true“.</td>
  </tr>
  <tr>
   <td>app.constants</td>
   <td>Ein Wrapper-Objekt zum Erfassen von verschiedenen konstanten Werten. Derzeit gibt diese Eigenschaft ein Objekt mit einer Eigenschaft zurück, nämlich „align“.</td>
   <td>HTML5-Formulare geben ein leeres align-Objekt zurück.</td>
  </tr>
  <tr>
   <td>app.focusRect</td>
   <td>Aktiviert und deaktiviert das Fokusrechteck. Das Fokusrechteck ist die schwach gepunktete Linie um die Schaltflächen, Kontrollkästchen, Optionsfelder und Signaturen und zeigt an, dass das Formularfeld den Tastaturfokus hat. Mit dem Wert „true“ wird das Fokusrechteck aktiviert.</td>
   <td>Bei HTML5-Formularen ist der Wert immer „true“.</td>
  </tr>
  <tr>
   <td>app.formsVersion</td>
   <td>Die Versionsnummer der Viewer-Formular-Software. Aktivieren Sie diese Eigenschaft, um festzulegen, ob Objekte, Eigenschaften oder Methoden in den neueren Versionen der Software verfügbar sind, wenn Sie die Abwärtskompatibilität in den Skripten beibehalten möchten.</td>
   <td>Immer 11.001.</td>
  </tr>
  <tr>
   <td>app.language</td>
   <td>Die Sprache des aktuellen Acrobat Viewer.</td>
   <td>In HTML5-Formularen immer „ENU“.</td>
  </tr>
 </tbody>
</table>

## Unterstützte XFA-Ereignisse {#supported-xfa-events}

Folgende Client-seitige XFA-Ereignisse werden unterstützt:

* Initialisieren
* Validieren
* Berechnen
* Klicken Sie auf
* Geben Sie ein
* Beenden
* Änderung
* ValidationState

>[!NOTE]
>
>HTML5-Formulare werden clientseitig (im Browser) wiedergegeben. Verwenden Sie Client-seitige **Validierungs**- und **Berechnungsskripte** anstelle Server-seitiger Skripte.
