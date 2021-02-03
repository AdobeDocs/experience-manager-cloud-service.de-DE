---
title: Varianten – Erstellen von Fragmentinhalten
description: Mit Varianten können Sie Inhalte für ein Fragment erstellen und je nach Bedarf (und falls erforderlich) Varianten dieses Inhalts erstellen.
translation-type: tm+mt
source-git-commit: 972d242527871660d55b9a788b9a53e88d020749
workflow-type: tm+mt
source-wordcount: '2186'
ht-degree: 78%

---


# Varianten – Erstellen von Fragmentinhalten{#variations-authoring-fragment-content}

[Varianten](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) sind eine wichtige Funktion für Inhaltsfragmente, da sie Ihnen die Möglichkeit bieten, Kopien des Master-Inhalts zu erstellen und zu bearbeiten und diese für bestimmte Kanäle und/oder Szenarien zu verwenden.

In der Registerkarte **Varianten** haben Sie folgende Möglichkeiten:

* [Eingeben des Inhalts](#authoring-your-content) für das Fragment,
* [Erstellen und Verwalten von Varianten](#managing-variations) des **Master**-Inhalts,

Ausführen einer Vielzahl weiterer Aktionen abhängig vom bearbeiteten Datentyp; z. B.:

* [Einfügen von visuellen Assets in Ihr Fragment](#inserting-assets-into-your-fragment) (Bilder)

* Auswählen zwischen [Rich-Text](#rich-text), [Nur Text](#plain-text) und [Markdown](#markdown) für die Bearbeitung

* [Inhalt hochladen](#uploading-content)

* [Anzeigen von Schlüsselstatistiken](#viewing-key-statistics) (über mehrzeiligen Text)

* [Zusammenfassen von Text](#summarizing-text)

* [Synchronisieren von Varianten mit dem Master-Inhalt](#synchronizing-with-master)

>[!CAUTION]
>
>Nachdem ein Fragment veröffentlicht und/oder referenziert wurde, zeigt AEM eine Warnmeldung an, wenn ein Autor das Fragment erneut zur Bearbeitung öffnet. Dies dient als Hinweis darauf, dass am Fragment vorgenommene Änderungen sich auch auf die referenzierten Seiten auswirken.

## Verfassen Ihres Inhalts {#authoring-your-content}

Wenn Sie Ihr Inhaltsfragment zur Bearbeitung öffnen, wird die Registerkarte **Varianten** standardmäßig geöffnet. Hier können Sie den Inhalt bearbeiten, und zwar den der Master-Version sowie sämtlicher Varianten. Das strukturierte Fragment enthält verschiedene Felder verschiedener Datentypen, die im Inhaltsmodell definiert wurden.

Sie haben folgende Möglichkeiten:

* Nehmen Sie Ihre Änderungen direkt in der Registerkarte **Varianten** vor

   * Jeder Datentyp bietet verschiedene Bearbeitungsoptionen

* Für die Felder **Mehrzeiliger Text** können Sie auch den [Vollbildeditor](#full-screen-editor) öffnen für:

   * das [Format](#formats) auszuwählen
   * weitere Bearbeitungsoptionen anzuzeigen ([Rich-Text](#rich-text)-Format)
   * auf eine Reihe von [Aktionen](#actions)zuzugreifen

Beispiel:

![Vollbild-Editor](assets/cfm-variations-02.png)

### Vollbildeditor {#full-screen-editor}

Beim Bearbeiten eines mehrzeiligen Textfelds können Sie den Editor für den Vollbildmodus öffnen. Tippen Sie auf oder klicken Sie in den eigentlichen Text und wählen Sie dann das folgende Aktionssymbol aus:

![Symbol für den Vollbild-Editor](assets/cfm-variations-03.png)

Dadurch wird der Texteditor im Vollbildmodus geöffnet:

![Vollbild-Editor](assets/cfm-variations-fullscreentexteditor.png)

Der Texteditor im Vollbildmodus bietet:

* Zugriff auf verschiedene [Aktionen](#actions)
* Je nach [Format](#formats) weitere Formatierungsoptionen ([Rich-Text](#rich-text))

### Aktionen    {#actions}

Die folgenden Aktionen sind ebenfalls verfügbar (für sämtliche [Formate](#formats)), wenn der Vollbild-Editor (d. h. mehrzeiliger Text) geöffnet ist:

* [Format](#formats) auswählen ([Rich-Text](#rich-text), [Nur Text](#plain-text), [Markdown](#markdown))

* [Inhalt hochladen](#uploading-content)

* [Textstatistiken anzeigen](#viewing-key-statistics)

* [Mit Master synchronisieren](#synchronizing-with-master) (beim Bearbeiten einer Variante)

* [Zusammenfassen von Text](#summarizing-text)

### Formate {#formats}

Die Optionen für das Bearbeiten von mehrzeiligem Text hängen vom ausgewählten Format ab: 

* [Rich-Text](#rich-text)
* [Nur Text](#plain-text)
* [Markdown](#markdown)

Das Format kann im Vollbild-Editor ausgewählt werden.

### Rich-Text {#rich-text}

Die Rich-Text-Bearbeitung ermöglicht folgende Formatierungen:

* Fett
* Kursiv
* Unterstrichen
* Ausrichtung: links, zentriert, rechts
* Stichpunktliste
* Nummerierte Liste
* Einzug: erhöhen, vermindern
* Erstellen/Aufheben von Hyperlinks
* Einfügen von Text aus Word
* Einfügen einer Tabelle
* Absatzformat: Absatz, Überschrift 1/2/3
* [Asset einfügen](#inserting-assets-into-your-fragment)
* Öffnen Sie den Vollbild-Editor, in dem die folgenden Formatierungsoptionen zur Verfügung stehen:
   * Suchen
   * Suchen/Ersetzen
   * Rechtschreibprüfung
   * [Anmerkungen](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Inhaltsfragment](#inserting-content-fragment-into-your-fragment) einfügen verfügbar, wenn Ihr  **mehrzeiliges** Textfeld mit  **Fragmentverweis** zulassen konfiguriert wurde.

Die [Aktionen](#actions) sind ebenfalls über den Vollbild-Editor verfügbar.

### Nur Text {#plain-text}

Nur Text ermöglicht die schnelle Eingabe von Inhalt ohne Formatierungs- oder Markdown-Informationen. Für weitere [Aktionen](#actions) können Sie auch den Vollbild-Editor öffnen.

>[!CAUTION]
>
>Wenn Sie **Nur Text** auswählen, gehen möglicherweise alle Formatierungen, Markierungen und/oder Assets verloren, die Sie in **Rich-Text** oder **Markdown** eingefügt haben.

### Markdown {#markdown}

>[!NOTE]
>
>Umfassende Informationen hierzu finden Sie in der [Markdown](/help/assets/content-fragments/content-fragments-markdown.md)-Dokumentation.

Auf diese Weise können Sie Ihren Text mithilfe von Markdowns formatieren. Sie können Folgendes definieren:

* Überschriften
* Absätze und Zeilenumbrüche
* Links
* Bilder
* Blockzitate
* Listen
* Hervorhebungen
* Code-Blöcke
* Umgekehrter Schrägstrich als Escape-Zeichen

Für weitere [Aktionen](#actions) können Sie auch den Vollbild-Editor öffnen.

>[!CAUTION]
>
>Wenn Sie zwischen **Rich-Text** und **Markdown** umschalten, treten möglicherweise unerwartete Effekte mit Blockzitaten und Code-Blöcken auf, da diese beiden Formate unterschiedlich verarbeitet werden.

### Fragmentverweise {#fragment-references}

Wenn das Inhaltsfragmentmodell Fragmentverweise enthält, stehen Ihren Fragmentverfassern möglicherweise zusätzliche Optionen zur Verfügung:

* [Inhaltsfragment bearbeiten](#fragment-references-edit-content-fragment)
* [Neues Inhaltsfragment](#fragment-references-new-content-fragment)

![Fragmentverweise](assets/cfm-variations-12.png)

#### Inhaltsfragment bearbeiten {#fragment-references-edit-content-fragment}

Die Option **Inhaltsfragment bearbeiten** wird geöffnet
eine neue Registerkarte des Browsers mit geöffnetem Inhaltsfragment im Inhaltsfragmenteditor.

#### Neues Inhaltsfragment {#fragment-references-new-content-fragment}

Mit der Option **Neues Inhaltsfragment** können Sie ein komplett neues Fragment erstellen. Um dies zu erreichen, wird eine Variante des Assistenten zum Erstellen von Inhaltsfragmenten im Editor geöffnet.

Anschließend können Sie ein neues Fragment erstellen, indem Sie:

1. Navigieren zum gewünschten Ordner und Auswählen des entsprechenden Ordners
1. Wählen Sie **Weiter**.
1. Festlegen von Eigenschaften; zum Beispiel **Title**.
1. Wählen Sie **Erstellen**.
1. Abschließend:
   1. **Geben Sie** das Fragment zurück (zum ursprünglichen Fragment) und verweisen Sie auf das neue Fragment.
   1. **** Open referenziert das neue Fragment und öffnet das neue Fragment zur Bearbeitung in einer neuen Browserregisterkarte.

### Anzeigen von Schlüsselstatistiken {#viewing-key-statistics}

Wenn der Vollbild-Editor geöffnet ist, zeigt die Aktion **Textstatistik** eine Reihe von Informationen über den Text an.

Beispiel:

![Statistiken](assets/cfm-variations-04.png)

### Hochladen von Inhalt {#uploading-content}

Um die Erstellung von Inhaltsfragmenten zu vereinfachen, können Sie Text hochladen, der in einem externen Editor vorbereitet wurde, und ihn direkt in das Fragment einfügen.

### Zusammenfassung von Text {#summarizing-text}

Mithilfe der Zusammenfassung von Text können Benutzer die Länge des Textes auf eine vordefinierte Anzahl von Wörtern verringern, während die wichtigen Punkte und die allgemeine Bedeutung beibehalten werden.

>[!NOTE]
>
>Auf einer technischeren Stufe behält das System die Sätze bei, die in Übereinstimmung mit bestimmten Algorithmen das *beste Verhältnis von Informationsdichte und Eindeutigkeit* bieten.

>[!CAUTION]
>
>Das Inhaltsfragment muss einen gültigen Sprachordner (ISO-Code) als Vorgänger haben, der verwendet wird, um das zu verwendende Sprachmodell zu bestimmen.
>
>Beispiel: `en/` wie im folgenden Pfad:
>
>  `/content/dam/my-brand/en/path-down/my-content-fragment`

>[!CAUTION]
Englisch ist standardmäßig verfügbar.
Andere Sprachen sind als Sprachmodellpakete über Package Share verfügbar:
* [Französisch (fr)](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-fr)
* [Deutsch (de)](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-de)
* [Italienisch (it)](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-it)
* [Spanisch (es)](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/smartcontent-model-es)



1. Wählen Sie **Master** oder die erforderliche Variante aus.
1. Öffnen Sie den Vollbild-Editor.

1. Wählen Sie in der Symbolleiste die Option **Text zusammenfassen** aus.

   ![Zusammenfassung](assets/cfm-variations-05.png)

1. Geben Sie den Zielwert der Wörter an und wählen Sie **Start**:
1. Der Originaltext wird neben der vorgeschlagenen Zusammenfassung angezeigt:

   * Zu beseitigende Sätze werden rot und durchgestrichen hervorgehoben.
   * Klicken Sie auf einen beliebigen hervorgehobenen Satz, um ihn im zusammengefassten Inhalt zu behalten.
   * Klicken Sie auf einen beliebigen nicht hervorgehobenen Satz, um ihn zu beseitigen.

1. Wählen Sie **Zusammenfassen** aus, um die Änderungen zu bestätigen.

1. Der Originaltext wird neben der vorgeschlagenen Zusammenfassung angezeigt:

   * Zu beseitigende Sätze werden rot und durchgestrichen hervorgehoben.
   * Klicken Sie auf einen beliebigen hervorgehobenen Satz, um ihn im zusammengefassten Inhalt zu behalten.
   * Klicken Sie auf einen beliebigen nicht hervorgehobenen Satz, um ihn zu beseitigen.

   ![Zusammenfassungsvergleich](assets/cfm-variations-06.png)

### Anmerkungen zu Inhaltsfragmenten {#annotating-a-content-fragment}

So fügen Sie Anmerkungen zu Fragmenten hinzu:

1. Wählen Sie **Master** oder die erforderliche Variante aus.

1. Öffnen Sie den Vollbild-Editor.

1. Das Symbol **Anmerken** ist in der Symbolleiste oben verfügbar. Sie können bei Bedarf Text auswählen.

   ![Anmerken](assets/cfm-variations-07.png)

1. Ein Dialogfeld wird geöffnet. Hier können Sie Ihre Anmerkungen eingeben.

   ![Anmerken](assets/cfm-variations-07a.png)

1. Wählen Sie **Apply** im Dialogfeld.

   ![Anmerken](assets/cfm-variations-annotations-apply-icon.png)

   Wenn die Anmerkung auf den ausgewählten Text angewendet wurde, bleibt dieser Text hervorgehoben.

   ![Anmerken](assets/cfm-variations-07b.png)

1. Schließen Sie den Editor für den Vollbildmodus, Anmerkungen werden weiterhin hervorgehoben. Wenn diese Option aktiviert ist, wird ein Dialogfeld geöffnet, in dem Sie die Anmerkung weiter bearbeiten können.

1. Wählen Sie **Speichern** aus.

1. Schließen Sie den Editor für den Vollbildmodus, Anmerkungen werden weiterhin hervorgehoben. Wenn diese Option aktiviert ist, wird ein Dialogfeld geöffnet, in dem Sie die Anmerkung weiter bearbeiten können.

   ![Anmerken](assets/cfm-variations-07c.png)

### Anzeigen, Bearbeiten und Löschen von Anmerkungen {#viewing-editing-deleting-annotations}

Anmerkungen:

* Werden sowohl im Vollbildmodus als auch im Normalmodus des Editors als hervorgehobener Text angezeigt. Die vollständigen Details einer Anmerkung können dann angezeigt, bearbeitet und/oder gelöscht werden, indem Sie auf den hervorgehobenen Text klicken. Dann wird das Dialogfeld erneut geöffnet.

   >[!NOTE]
   Eine Dropdown-Liste wird angezeigt, wenn mehrere Anmerkungen auf einen Textausschnitt angewendet wurden.

* Wenn Sie den gesamten Text löschen, auf den die Anmerkung angewendet wurde, wird der Kommentar ebenfalls gelöscht.

* Kann durch das Auswählen der Registerkarte **Anmerkungen** im Fragment-Editor aufgeführt und gelöscht werden.

   ![Anmerkungen](assets/cfm-variations-08.png)

* Kann in der [Timeline](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) für das ausgewählte Fragment angezeigt und gelöscht werden.

### Einfügen von Assets in das Fragment {#inserting-assets-into-your-fragment}

Um die Erstellung von Inhaltsfragmenten zu vereinfachen, können Sie [Assets](/help/assets/manage-digital-assets.md) (Bilder) direkt zum Fragment hinzufügen.

Sie werden der Absatzreihe des Fragments ohne jede Formatierung hinzugefügt. Die Formatierung kann erfolgen, wenn das [Fragment auf einer Seite verwendet/referenziert wird](/help/sites-cloud/authoring/fundamentals/content-fragments.md).

>[!CAUTION]
Diese Assets können auf einer referenzierenden Seite nicht verschoben oder gelöscht werden, sondern nur im Fragment-Editor.
Allerdings muss die Formatierung eines Assets (z. B. Größe) über den [Seiteneditor](/help/sites-cloud/authoring/fundamentals/content-fragments.md) erfolgen. Die Darstellung des Assets im Fragment-Editor dient lediglich der Erstellung des Inhaltsflusses.

>[!NOTE]
Es gibt verschiedene Methoden, um [Bilder](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) zu einem Fragment und/oder einer Seite hinzuzufügen.

1. Positionieren Sie den Cursor über der Position, an der Sie das Bild hinzufügen möchten.
1. Öffnen Sie das Suchdialogfeld mithilfe der Schaltfläche **Asset einfügen**.

   ![Symbol „Asset einfügen“](assets/cfm-variations-09.png)

1. In diesem Dialogfeld haben Sie folgende Möglichkeiten:

   * Navigieren zum gewünschten Asset in DAM
   * Suchen nach dem Asset in DAM

   Nachdem Sie das gewünschte Asset gefunden haben, wählen Sie es aus, indem Sie auf die Miniaturansicht klicken.

1. Verwenden Sie **Auswahl**, um das Asset dem Absatzsystem Ihres Content Fragments am aktuellen Speicherort hinzuzufügen.

   >[!CAUTION]
   Wenn Sie nach dem Hinzufügen eines Assets das Format ändern in:
   * **Klartext:** Das Asset geht im Fragment vollständig verloren.
   * **Markdown:** Das Asset wird nicht angezeigt, ist aber immer noch vorhanden, wenn Sie zu **Rich Text** zurückkehren.


### Einfügen eines Inhaltsfragments in Ihr Fragment {#inserting-content-fragment-into-your-fragment}

Um das Authoring von Inhaltsfragmenten zu vereinfachen, können Sie Ihrem Fragment auch ein anderes Inhaltsfragment hinzufügen.

Sie werden als Referenz an Ihrer aktuellen Position im Fragment hinzugefügt.

>[!NOTE]
Diese Option ist verfügbar, wenn Ihr **mehrzeiliger Text** mit **Fragmentverweis zulassen** konfiguriert ist.

>[!CAUTION]
Diese Assets können auf einer referenzierenden Seite nicht verschoben oder gelöscht werden, sondern nur im Fragment-Editor.
Allerdings muss die Formatierung eines Assets (z. B. Größe) über den [Seiteneditor](/help/sites-cloud/authoring/fundamentals/content-fragments.md) erfolgen. Die Darstellung des Assets im Fragment-Editor dient lediglich der Erstellung des Inhaltsflusses.

>[!NOTE]
Es gibt verschiedene Methoden, um [Bilder](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) zu einem Fragment und/oder einer Seite hinzuzufügen.

1. Positionieren Sie den Cursor an der Position, an der Sie das Fragment hinzufügen möchten.
1. Verwenden Sie das Symbol **Inhaltsfragment** einfügen, um das Suchdialogfeld zu öffnen.

   ![Inhaltsfragment-Symbol einfügen](assets/cfm-variations-13.png)

1. In diesem Dialogfeld haben Sie folgende Möglichkeiten:

   * zum erforderlichen Fragment im Ordner &quot;Assets&quot;navigieren
   * Suche nach dem Fragment

   Wählen Sie das gewünschte Fragment aus, indem Sie auf die Miniaturansicht klicken.

1. Verwenden Sie **Wählen Sie**, um dem aktuellen Inhaltsfragment (an der aktuellen Position) einen Verweis auf das ausgewählte Inhaltsfragment hinzuzufügen.

   >[!CAUTION]
   Wenn Sie nach dem Hinzufügen eines Verweises zu einem anderen Fragment das Format ändern in:
   * **Text**: der Verweis wird vollständig aus dem Fragment verloren.
   * **Markdown**: der Verweis bleibt bestehen.


## Verwalten von Varianten      {#managing-variations}

### Variante erstellen {#creating-a-variation}

Varianten ermöglichen die Abänderung von **Master**-Inhalt für einen bestimmten Zweck (sofern notwendig).

So erstellen Sie eine neue Variante:

1. Öffnen Sie Ihr Fragment und stellen Sie sicher, dass das seitliche Bedienfeld sichtbar ist.
1. Wählen Sie im seitlichen Bedienfeld in der Symbolleiste die Option **Varianten** aus.
1. Wählen Sie **Variante erstellen** aus.
1. Daraufhin wird ein Dialogfeld geöffnet, in dem der **Titel** und die **Beschreibung** für die neue Variante angegeben werden.
1. Wählen Sie **Hinzufügen** aus. Das Fragment **Master**[ wird in die neue Variante kopiert, die nun zur Bearbeitung geöffnet ist](#editing-a-variation).

   >[!NOTE]
   Wenn eine neue Variante erstellt wird, wird immer der **Master** kopiert, nicht die gerade geöffnete Variante.

### Bearbeiten einer Variante      {#editing-a-variation}

Sie können nach einer der folgenden Aktionen Änderungen am Inhalt der Variante vornehmen:

* [Erstellen einer Variante](#creating-a-variation).
* Öffnen eines vorhandenen Fragments und Auswahl der gewünschten Variante aus dem seitlichen Bedienfeld.

![Bearbeiten einer Variante](assets/cfm-variations-10.png)

### Umbenennen einer Variante {#renaming-a-variation}

So benennen Sie eine vorhandene Variante um:

1. Öffnen Sie das Fragment und wählen Sie über den Seitenbereich die Option **Varianten** aus.
1. Wählen Sie die gewünschte Variante aus.
1. Wählen Sie im Dropdown-Menü **Aktionen** die Option **Umbenennen** aus.

1. Geben Sie im Dialogfeld den neuen **Titel** und/oder die **Beschreibung** ein.

1. Bestätigen Sie die Aktion **Umbenennen**.

>[!NOTE]
Dies wirkt sich nur auf den **Namen** der Variante aus.

### Löschen einer Variante {#deleting-a-variation}

So löschen Sie eine vorhandene Variante:

1. Öffnen Sie das Fragment und wählen Sie über den Seitenbereich die Option **Varianten** aus.
1. Wählen Sie die gewünschte Variante aus.
1. Wählen Sie im Dropdown-Menü **Aktionen** die Option **Löschen** aus.

1. Bestätigen Sie im Dialogfeld die Aktion **Löschen**.

>[!NOTE]
**Master** kann nicht gelöscht werden.

### Mit Master synchronisieren {#synchronizing-with-master}

**Master** ist ein wesentlicher Bestandteil eines Inhaltsfragments und enthält die Masterkopie des Inhalts, während die Varianten einzelne aktualisierte und maßgeschneiderten Versionen des Inhalts enthalten. Wenn Master aktualisiert wird, können diese Änderungen auch für die Varianten relevant sein und müssen daher auf diese übertragen werden.

Beim Bearbeiten einer Variante haben Sie Zugriff auf die Aktion zur Synchronisierung des aktuellen Elements der Variante mit der Master-Version. Dadurch können Sie an Master vorgenommene Änderungen automatisch in die entsprechende Variante kopieren.

>[!CAUTION]
Die Synchronisierung ist nur verfügbar, um Änderungen *vom **Master**in die Variante* zu kopieren.
Es wird nur das aktuelle Element der Variante synchronisiert.
Die Synchronisierung funktioniert nur mit Datentypen mit **mehrzeiligem Text**.
Es ist nicht möglich, Änderungen *von einer Variante auf **Master*** zu übertragen.

1. Öffnen Sie das Inhaltsfragment im Fragment-Editor. Stellen Sie sicher, dass **Master** bearbeitet wurde.

1. Es gibt folgende Möglichkeiten, eine bestimmte Variante sowie die entsprechende Synchronisierung auszuwählen:

   * über den Dropdown-Selektor **Aktionen** – **Aktuelles Element mit Master synchronisieren**

      ![Mit Master synchronisieren](assets/cfm-variations-11a.png)

   * über die Symbolleiste des Vollbild-Editors – **Mit Master synchronisieren**

      ![Mit Master synchronisieren](assets/cfm-variations-11b.png)

1. Master und Variante werden nebeneinander angezeigt:

   * Grün zeigt an, dass Inhalt (zur Variante) hinzugefügt      wurde
   * Rot zeigt an, dass Inhalt entfernt wurde (aus der Variante)
   * Blau zeigt an, dass Text ersetzt wurde

   ![Mit Master synchronisieren](assets/cfm-variations-11c.png)

1. Wählen Sie **Synchronisieren**. Die Variante wird dann aktualisiert und angezeigt.
