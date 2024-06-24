---
title: Erstellen von Inhaltsfragmenten
description: Erfahren Sie, wie Sie Inhalte für Ihre Inhaltsfragmente verfassen und dann je nach Zweck Varianten dieses Inhalts erstellen. Dies bietet mehr Flexibilität für die Headless-Bereitstellung und das Seiten-Authoring.
feature: Content Fragments
role: User, Developer, Architect
exl-id: a2f2b617-3bdf-4a22-ab64-95f2c65adc82
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '2668'
ht-degree: 100%

---

# Erstellen von Inhaltsfragmenten {#authoring-content-fragments}

Die Erstellung von Inhaltsfragmenten konzentriert sich sowohl auf die Headless-Bereitstellung als auch auf die Seitenbearbeitung.

Es gibt zwei Editoren für Inhaltsfragmente. Der Editor, der in diesem Abschnitt beschrieben wird:

* wurde für die Bereitstellung von Headless-Inhalten entwickelt (obwohl er für alle Szenarien verwendet werden kann)
* ist über die **Inhaltsfragmentkonsole** verfügbar.

Dieser Editor bietet Folgendes:

* [Automatisches Speichern](#saving-autosaving) zur Vermeidung von versehentlichen Verlusten von Bearbeitungen.
* [Online-Upload von Assets als Inhaltsverweise](#reference-images), ohne sie zuerst in Asset DAM hochladen zu müssen.
* [Generieren von Varianten](#generate-variations-ai): Zur Verwendung der generativen KI, um die Inhaltserstellung auf der Grundlage von Prompts zu beschleunigen.
* [Vorschau](#preview-content-fragment) des vom Inhaltsfragment bereitgestellten gerenderten Erlebnisses.
* Fähigkeit zum [Veröffentlichen](#publish-content-fragment) und [Aufheben der Veröffentlichung](#unpublish-content-fragment) über den Editor.
* Fähigkeit zum [Anzeigen und Öffnen zugehöriger Sprachkopien](#view-language-copies) im Editor.
* Fähigkeit zum [Anzeigen von Versionsdetails](#view-version-history) im Editor. Sie können auch eine ausgewählte Version wiederherstellen.
* Fähigkeit zum [Anzeigen und Öffnen von übergeordneten Verweisen](#view-parent-references).
* Eine hierarchische Ansicht des Inhaltsfragments und seiner Verweise mithilfe der [Baumstruktur](#structure-tree).

>[!WARNING]
>
>Der in diesem Abschnitt beschriebene Editor ist *nur* *online* in Adobe Experience Manager (AEM) as a Cloud Service verfügbar.

## Inhaltsfragmenteditor {#content-fragment-editor}

Beim ersten Öffnen des Inhaltsfragmenteditors werden vier Hauptbereiche angezeigt:

* obere Symbolleiste: für wichtige Informationen und Aktionen
   * ein Link zur Inhaltsfragmentkonsole (Startseiten-Symbol)
   * Informationen zum Modell und Ordner
   * Links zur [Vorschau (wenn das URL-Standardmuster für die Vorschau für das Modell konfiguriert ist)](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-fragment-model-properties)
   * die Aktionen [Veröffentlichen](#publish-content-fragment) und [Veröffentlichung aufheben](#unpublish-content-fragment)
   * eine Option zum Anzeigen aller **übergeordneten Verweise** (Verknüpfungssymbol)
   * der **[Status](/help/sites-cloud/administering/content-fragments/managing.md#statuses-content-fragments)** des Fragments und Informationen über die letzte Speicherung
   * ein Umschalter zum Umschalten auf den ursprünglichen (Assets-basierten) Editor

     >[!WARNING]
     >
     >Der ursprüngliche Editor wird auf derselben Registerkarte geöffnet. Es wird davon abgeraten, beide Editoren gleichzeitig geöffnet zu haben.

* linker Bereich: zeigt die **[Varianten](#variations)** für das Inhaltsfragment und dessen **Felder** an:
   * diese Links können verwendet werden, um [in der Inhaltsfragmentstruktur zu navigieren](#navigate-structure)
* rechter Bereich: enthält Registerkarten [mit den Eigenschaften (Metadaten) und Tags](#view-properties-tags), Informationen über den [Versionsverlauf](#view-version-history) sowie Informationen zu [Sprachkopien](#view-language-copies)
   * auf der Registerkarte **Eigenschaften** können Sie den **Titel** und die **Beschreibung** für das Fragment oder die **Variante** aktualisieren
* zentraler Bereich: zeigt die tatsächlichen Felder und den Inhalt der ausgewählten Variante an
   * ermöglicht das Bearbeiten des Inhalts
   * wenn **Registerkartenplatzhalter**-Felder innerhalb des hier gezeigten Modells definiert werden und für die Navigation verwendet werden können, werden sie entweder horizontal oder als Dropdown-Liste angezeigt.

  >[!NOTE]
  >
  >Abhängig von den Definitionen im zugrunde liegenden Modell können Felder bestimmten Arten von [Validierung](/help/assets/content-fragments/content-fragments-models.md#validation) unterliegen.

![Inhaltsfragmenteditor – Überblick](assets/cf-authoring-overview.png)

## In der Inhaltsfragmentstruktur navigieren {#navigate-structure}

Ein einzelnes Inhaltsfragment;

* Besteht aus zwei Ebenen:

   * **[Varianten](#variations)** des Inhaltsfragments
   * **Felder** – vom Inhaltsfragmentmodell definiert und von jeder Variante verwendet

* Kann eine Reihe von Verweisen enthalten.

### Varianten und Felder {#variations-and-fields}

Im linken Bereich können Sie Folgendes sehen:

* die Liste der **[Varianten](#variations)**, die für dieses Fragment erstellt wurden:
   * **Haupt** ist die Variante, die beim ersten Erstellen des Inhaltsfragments vorhanden ist. Sie können später weitere hinzufügen
   * Sie können mit der Funktion „Varianten generieren“ (#generate-variations) eine auf Prompts basierende Vorlage verwenden, die Adobe für einen bestimmten Anwendungsfall erstellt hat.
   * Sie können auch [eine Variante erstellen](#create-variation)
* die **Felder** innerhalb des Fragments und dessen Varianten:
   * das Symbol zeigt den [Datentyp](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types) an
   * der Text ist der Feldname
   * diese stellen gemeinsam einen direkten Link zum Feldinhalt im zentralen Bereich bereit (für die aktuelle Variante)

### Links folgen {#follow-links}

Das Link-Symbol wird in verschiedenen Bereichen des Editors angezeigt. Dies kann verwendet werden, um das angezeigte Element zu öffnen, z. B. ein Inhaltsfragmentmodell, einen übergeordneten Verweis oder ein Fragment, auf das verwiesen wird:

![Inhaltsfragmenteditor – Link-Symbol](assets/cf-authoring-link-icon.png)

### Baumstruktur {#structure-tree}

Öffnen Sie die Registerkarte **Baumstruktur** über die Editor-Symbolleiste, um die hierarchische Struktur des Inhaltsfragments und dessen Verweise anzuzeigen. Verwenden Sie die Link-Symbole, um zu den Verweisen zu navigieren.

![Inhaltsfragmenteditor – Baumstruktur](assets/cf-authoring-structure-tree.png)

>[!NOTE]
>
>Siehe [Analysieren der Struktur von Inhaltsfragmenten – Baumstruktur](/help/sites-cloud/administering/content-fragments/analysis.md#structure-tree) für weitere Details.

## Speichern und automatisches Speichern {#saving-autosaving}

<!-- CHECK: cannot be saved, no undo, redo -->

Das Inhaltsfragment wird bei jeder von Ihnen vorgenommenen Aktualisierung automatisch gespeichert. Die Zeit der letzten Speicherung wird in der oberen Symbolleiste angezeigt.

## Varianten {#variations}

[Varianten](/help/sites-cloud/administering/content-fragments/overview.md#main-and-variations) sind eine wichtige Funktion von AEM-Inhaltsfragmenten. Sie können damit Kopien des **Haupt-Inhalts** erstellen und bearbeiten, um sie in bestimmten Kanälen und Szenarien zu verwenden. Dadurch wird die Bereitstellung von Headless-Inhalten und die Seitenbearbeitung noch flexibler.

Über den Editor haben Sie folgende Möglichkeiten:

* [Erstellen von Varianten](#create-variation) des **Haupt-Inhalts**

* [Unter Verwendung der Funktion „Varianten generieren“ ](#generate-variations-ai) können Sie eine auf Prompts basierende Vorlage verwenden, die Adobe für einen bestimmten Anwendungsfall erstellt hat.

* Die erforderliche Variante zum Bearbeiten des Inhalts auswählen

* [Variante umbenennen](#rename-variation)

* [Variante löschen](#delete-variation)

### Variante erstellen {#create-variation}

So erstellen Sie eine Variante Ihres Inhaltsfragments:

1. Wählen Sie im linken Bereich das **Pluszeichen** (**Variante erstellen**), das sich rechts von **Varianten** befindet.

   >[!NOTE]
   >
   >Nach der Erstellung Ihrer ersten Variante werden vorhandene Varianten im selben Bereich aufgelistet.

   ![Inhaltsfragmenteditor – Erstellen Ihrer ersten Variante ](assets/cf-authoring-create-variation-01.png)

1. Geben Sie im Dialogfeld einen **Titel** für Ihre Variante und, wenn gewünscht, eine **Beschreibung** ein:

   ![Inhaltsfragmenteditor – Dialogfeld „Variante erstellen“](assets/cf-authoring-create-variation-02.png)

1. **Erstellen** Sie die Variante. Sie wird in der Liste angezeigt.

### Umbenennen einer Variante {#rename-variation}

So benennen Sie eine **Variante** um:

1. Wählen Sie die gewünschte Variante aus.

1. Öffnen Sie die Registerkarte **Eigenschaften** im rechten Bereich.

1. Aktualisieren Sie den **Titel** der Variante.

1. Drücken Sie entweder auf die **Return-Taste** oder wechseln Sie in ein anderes Feld, um die Änderung automatisch zu speichern. Der Titel wird im Bereich **Varianten** auf der linken Seite aktualisiert.

### Erstellen von Varianten mit GenAI durch Variantengenerierung {#generate-variations-ai}

Verwenden Sie generative Varianten, um die generative KI zu nutzen und so die Inhaltserstellung zu beschleunigen.

So verwenden Sie die generativen Varianten im Inhaltsfragmenteditor:

1. Öffnen Sie den Inhaltsfragmenteditor. In der Kopfzeile finden Sie den Einstiegspunkt zur Variantengenerierung:

   ![Generieren von Varianten im Inhaltsfragmenteditor](assets/cfm-generate-variations1.png)

1. „Varianten generieren“ wird auf einer neuen Registerkarte geöffnet. In der linken Leiste können Sie die AEM Cloud-Instanz und das Inhaltsfragment sehen, für das Sie Inhalte erstellen. Wählen Sie den zu verwendenden Prompt aus oder erstellen Sie einen neuen Prompt.

   >[!NOTE]
   >
   >Die Zahl der verfügbaren Vorlagen für Adobe-Prompts ist aktuell eingeschränkt, aber in zukünftigen Versionen werden mehr hinzugefügt.

   ![Exportieren, um Varianten im Inhaltsfragment zu generieren](assets/cfm-generate-variations2.png)

1. Erstellen Sie Inhalte, indem Sie die Prompts ausfüllen. Das Inhaltsmodell aus dem Fragment wird automatisch verwendet, um Inhalte mithilfe von GenAI zu generieren.

   >[!NOTE]
   >
   >Derzeit unterstützen wir nur Textfelder.

   ![Exportieren, um Varianten im Inhaltsfragment zu generieren](assets/cfm-generate-variations3.png)

1. Wählen Sie die gewünschte Variante aus und wählen Sie „Variante exportieren“. Bestätigen Sie den Namen der Inhaltsfragmentvariante und wählen Sie eine der folgenden Optionen aus:

   * **Export**: Exportieren Sie die Variante in das Inhaltsfragment und bleiben Sie in der Anwendung zum Generieren von Varianten.
   * **Exportieren und öffnen**: Exportieren Sie die Variante in das Inhaltsfragment und öffnen Sie eine neue Registerkarte, auf der das Inhaltsfragment mit der neuen Variante von GenAI angezeigt wird.

     ![Exportieren, um Varianten im Inhaltsfragment zu generieren](assets/cfm-generate-variations4.png)

1. Die erzeugten Varianten werden im Hauptinhaltsfragmenteditor angezeigt.

   ![Anzeigen von „Varianten generieren“ im Inhaltsfragment](assets/cfm-generate-variations5.png)

Weitere Informationen zum Generieren von Varianten finden Sie [hier](/help/generative-ai/generate-variations.md).

### Löschen einer Variante {#delete-variation}

So löschen Sie eine Variante Ihres Inhaltsfragments:

    >[!HINWEIS]
    >
    >Sie können die **Hauptversion** nicht löschen.

1. Wählen Sie die Variante aus.

1. Wählen Sie im Bereich **Variante** das Symbol „Löschen“ (Papierkorb) aus:

   ![Inhaltsfragmenteditor – Symbol „Variante löschen“](assets/cf-authoring-delete-variation.png)

1. Ein Dialogfeld wird geöffnet. Wählen Sie **Löschen** aus, um die Aktion zu bestätigen.

## Bearbeiten mehrzeiliger Textfelder – Nur-Text oder Markdown {#edit-multi-line-text-fields-plaintext-markdown}

**[Mehrzeilige Textfelder](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)** können eines von drei Formaten aufweisen:

* Nur Text
* [Markdown](/help/sites-cloud/administering/content-fragments/markdown.md)
* [Rich-Text](#edit-multi-line-text-fields-rich-text)

Bei Feldern, die als Nur-Text- oder Markdown-Felder definiert sind, handelt es sich um einfache Textfelder ohne Formatierungsoptionen (auf dem Bildschirm):

![Inhaltsfragmenteditor – Mehrzeiliger Text – Vollbild](assets/cf-authoring-multilinetext-plaintext-markdown.png)

## Bearbeiten mehrzeiliger Textfelder – Rich-Text {#edit-multi-line-text-fields-rich-text}

Für Felder mit **[mehrzeiligem Text](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)**, die als **Rich-Text** definiert sind, stehen verschiedene Funktionen zur Verfügung:

* Den Inhalt bearbeiten:
   * Rückgängig/Wiederholen
   * Als Text einfügen/einfügen
   * Kopieren
   * Absatzformat auswählen
   * Tabelle erstellen/verwalten
   * Text formatieren; fett, kursiv, unterstrichen, Farbe
   * Absatzausrichtung festlegen
   * Listen erstellen/verwalten, mit Aufzählungszeichen, mit Nummerierung
   * Texteinzug; verringern, erhöhen
   * Aktuelle Formatierung löschen
   * Links einfügen
   * Verweise auf Bild-Assets auswählen und einfügen
   * Sonderzeichen hinzufügen
* [Vollbild-Editor](#full-screen-editor-rich-text) – Zwischen Vollbild und Textfluss umschalten
* [Statistiken](#statistics-rich-text)
* [Vergleichen und Synchronisieren](#compare-and-synchronize-rich-text)

Zum Beispiel:

![Inhaltsfragmenteditor – Mehrzeiliger Text – Umschalter im Vollbild](assets/cf-authoring-multilinetext-fullscreen-toggle.png)

>[!NOTE]
>
>Mehrzeilige Textfelder werden auch durch das entsprechende [Symbol](#fields-datatypes-icons) im Bereich **Felder** angezeigt.

### Vollbild-Editor – Rich-Text {#full-screen-editor-rich-text}

Der Vollbild-Editor bietet dieselben Bearbeitungsoptionen wie im Textfluss, lässt jedoch mehr Platz für den Text.

Zum Beispiel:

![Inhaltsfragmenteditor – Mehrzeiliger Text – Vollbild](assets/cf-authoring-multilinetext-fullscreen.png)

### Statistiken – Rich-Text {#statistics-rich-text}

Die Aktion **Statistik** zeigt eine Reihe von Informationen über den Text in einem mehrzeiligen Feld an.

Zum Beispiel:

![Inhaltsfragmenteditor – Statistik](assets/cf-authoring-multilinetext-statistics.png)

### Vergleichen und Synchronisieren – Rich-Text {#compare-and-synchronize-rich-text}

Die Aktion **Vergleichen** ist für mehrzeilige Felder verfügbar, wenn eine **Variante** geöffnet ist.

Dadurch wird das mehrzeilige Feld im Vollbild geöffnet und:

* es wird der Inhalt für die **Hauptvariante** und die aktuelle **Variante** parallel angezeigt, wobei alle Unterschiede hervorgehoben werden.

* Unterschiede sind farblich gekennzeichnet:

   * Grün zeigt an, dass der Inhalt (zur Variante) hinzugefügt wurde
   * Rot zeigt an, dass Inhalt entfernt wurde (aus der Variante)
   * Blau zeigt an, dass Text ersetzt wurde

* stellt die Aktion **Synchronisieren** zur Verfügung, die den Inhalt der **Hauptvariante** mit der aktuellen Variante synchronisiert.

   * wenn die **Hauptvariante** aktualisiert wurde, werden diese Änderungen in die Variante übertragen.
   * wenn die Variante aktualisiert wurde, werden diese Änderungen mit dem Inhalt der **Hauptvariante** überschrieben.

  >[!CAUTION]
  >
  >Die Synchronisierung ist nur verfügbar, um Änderungen *von der **Hauptvariante**in die Variante* zu kopieren.
  >
  >Es ist nicht möglich, Änderungen *von einer Variante auf die **Hauptvariante*** zu übertragen.

Beispiel: ein Szenario, in dem der Varianteninhalt vollständig umgeschrieben wurde, sodass eine Synchronisierung diesen neuen Inhalt durch den Inhalt aus der **Hauptvariante** ersetzt:

![Inhaltsfragmenteditor – Vergleichen und Synchronisieren](assets/cf-authoring-multilinetext-compare.png)

## Verweise verwalten {#manage-references}

### Fragmentreferenzen {#fragment-references}

[Fragmentreferenzen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#fragment-reference-nested-fragments) können für Folgendes verwendet werden:

* [einen Verweis auf ein vorhandenes Inhaltsfragment erstellen](#create-reference-existing-content-fragment)
* [ein Inhaltsfragment erstellen und dann darauf verweisen](#create-reference-content-fragment)

#### einen Verweis auf ein vorhandenes Inhaltsfragment erstellen {#create-reference-existing-content-fragment}

So erstellen Sie einen Verweis auf ein vorhandenes Inhaltsfragment:

1. Wählen Sie das Feld aus.
1. Wählen Sie **Vorhandenes Fragment hinzufügen** aus.
1. Wählen Sie das erforderliche Fragment aus der Fragmentauswahl aus.

   >[!NOTE]
   >
   >Sie können jeweils nur ein Fragment auswählen.

#### Ein Inhaltsfragment erstellen und darauf verweisen {#create-reference-content-fragment}

Alternativ können Sie [**Neues Fragment erstellen** auswählen, um das Dialogfeld **Erstellen** zu öffnen](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment). Nach der Erstellung wird auf dieses Fragment verwiesen.

### Inhaltsverweise {#content-references}

[Inhaltsverweise](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference) werden verwendet, um auf andere AEM-Inhaltstypen zu verweisen, z. B. Bilder, Seiten und Experience Fragments.

#### Auf Bilder verweisen {#reference-images}

In **Inhaltsverweis**-Feldern haben Sie beide Möglichkeiten:

* Auf Assets verweisen, die bereits im Repository vorhanden sind
* Sie können sie direkt in das Feld hochladen, wodurch es nicht nötig ist, die **Assets**-Konsole zum Hochladen zu verwenden

  >[!NOTE]
  >
  >Damit ein Bild direkt in das Feld **Inhaltsverweis** hochgeladen werden kann, **muss** es Folgendes erfüllen:
  >
  >* Es muss über einen definierten **Stammpfad** verfügen (im [Inhaltsfragmentmodell](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference)). Dieser gibt an, wo das Bild gespeichert wird.
  >* Es muss ein **Bild** entsprechend der Liste der akzeptierten Inhaltstypen enthalten

Um ein Asset hinzuzufügen, haben Sie folgende Möglichkeiten:

* ziehen Sie die neue Asset-Datei direkt (z. B. aus Ihrem Dateisystem) in das Feld **Inhaltsverweis**
* verwenden Sie die Aktion **Asset hinzufügen** und wählen Sie anschließend entweder **Assets durchsuchen** oder **Hochladen** aus, um die entsprechende Auswahl zu öffnen, die Sie verwenden möchten:

  ![Inhaltsfragmenteditor – Asset-Optionen hinzufügen](assets/cf-authoring-add-asset-options.png)

#### Auf Seiten verweisen {#reference-pages}

So fügen Sie Verweise zu AEM-Seiten, Experience Fragments oder anderen Inhaltsypen hinzu:

1. Wählen Sie **Inhaltspfad hinzufügen** aus.

1. Fügen Sie im Eingabefeld den erforderlichen Pfad hinzu.

1. Bestätigen Sie mit **Hinzufügen**.

### Anzeigen übergeordneter Verweise {#view-parent-references}

Durch Auswahl des Link-Symbols in der oberen Symbolleiste wird eine Liste aller übergeordneten Verweise geöffnet.

Zum Beispiel:

![Inhaltsfragmenteditor – Verweise anzeigen](assets/cf-authoring-show-references-link.png)

Ein Fenster mit allen zugehörigen Verweisen wird geöffnet. Wählen Sie zum Öffnen eines Verweises den Namen, den Titel oder das Link-Symbol aus.

Zum Beispiel:

![Inhaltsfragmenteditor – Verweise anzeigen](assets/cf-authoring-show-references.png)

## Anzeigen von Eigenschaften und Tags {#view-properties-tags}

Auf der Registerkarte „Eigenschaften“des rechten Bereichs können Eigenschaften (Metadaten) und Tags angezeigt werden. Die Eigenschaften können wie folgt lauten:

* für das **Inhaltsfragment** – wenn derzeit die **Hauptvariante** ausgewählt ist
* für eine bestimmte **Variante**

![Inhaltsfragmenteditor – Eigenschaften](assets/cf-authoring-properties.png)

### Bearbeiten von Eigenschaften und Tags {#edit-properties-tags}

Auf der Registerkarte „Eigenschaften“(rechter Bereich) können Sie auch Folgendes bearbeiten:

* **Titel**
* **Beschreibung**
* **Tags**: über die Dropdown-Liste oder das Dialogfeld „Auswahl“

  ![Inhaltsfragmenteditor – Tags verwalten](assets/cf-authoring-edit-tags.png)

### Öffnen des Inhaltsfragmentmodells {#open-content-fragment-model}

Wenn Sie die **Hauptvariante** ausgewählt haben, wird der Name des zugrunde liegenden Inhaltsfragmentmodells im Abschnitt „Eigenschaften“ angezeigt. Wenn Sie das Symbol „Link“ auswählen, wird das Modell auf einer separaten Registerkarte geöffnet.

Zum Beispiel:

![Inhaltsfragmenteditor – Inhaltsfragmentmodell öffnen](assets/cf-authoring-open-model.png)

## Anzeigen des Versionsverlaufs {#view-version-history}

Auf der Registerkarte **Versionsverlauf** im rechten Bereich werden Details zu der aktuellen und vorherigen Version angezeigt:

>[!NOTE]
>
>Eine neue Version wird erstellt, wenn das Inhaltsfragment veröffentlicht wird.

![Inhaltsfragmenteditor – Überblick über den Versionsverlauf](assets/cf-authoring-version-history-overview.png)

### Vergleichen der Version {#compare-version}

Für ein Inhaltsfragment können Sie eine frühere Version mit der aktuellen Version vergleichen.

So vergleichen Sie eine frühere Version mit der aktuellen:

1. Wählen Sie das Symbol mit den drei Punkten neben der Version aus.

1. Wählen Sie **Vergleichen**.

![Inhaltsfragmenteditor – Versionsverlaufs-Vergleich](assets/cf-authoring-version-history-compare.png)

Es wird eine Ansicht geöffnet, die Unterschiede zwischen der aktuellen Version und der ausgewählten vorherigen Version des Inhaltsfragments anzeigt. Aus der Dropdown-Liste **Varianten mit Änderungen** können Sie auswählen, ob Sie Unterschiede zum Hauptinhalt und/oder zum Inhalt einer Variante anzeigen möchten.

Unterschiede sind farblich gekennzeichnet:

* Grün zeigt an, dass Inhalte (zur aktuellen Version) hinzugefügt wurden.
* Rot zeigt an, dass Inhalte (aus der aktuellen Version) entfernt wurden.

![Inhaltsfragmenteditor – Versionsverlauf-Vergleich](assets/cf-authoring-version-history-compare-versions.png)

### Auf eine Version zurücksetzen {#revert-version}

Sie können eine beliebige Version wiederherstellen.

So stellen Sie eine bestimmte Version wieder her:

1. Wählen Sie das Symbol mit den drei Punkten neben der Version aus.

1. Wählen Sie **Wiederherstellen** aus.

![Inhaltsfragmenteditor – Versionsverlauf wiederherstellen](assets/cf-authoring-version-history-revert.png)

## Anzeigen der Sprachkopien {#view-language-copies}

Auf der Registerkarte **Spracheigenschaften** werden Details zu zugehörigen Sprachkopien angezeigt. Durch Auswahl eines Link-Symbols wird die Kopie auf einer separaten Registerkarte geöffnet.

Zum Beispiel:

![Inhaltsfragmenteditor – Sprachkopie öffnen](assets/cf-authoring-open-language-copies.png)

>[!NOTE]
>
>Weitere Informationen zum Übersetzen eines Inhaltsfragments und Erstellen von Sprachkopien finden Sie unter [AEM Headless-Übersetzungs-Journey](/help/journey-headless/translation/overview.md).


## Vorschau des Fragments anzeigen {#preview-content-fragment}

Der Inhaltsfragmenteditor bietet Autorinnen und Autoren die Möglichkeit, die Vorschau von Bearbeitungen in einer externen Frontend-Anwendung anzuzeigen.

Für die Verwendung dieser Funktion müssen Sie zunächst wie folgt vorgehen:

* Arbeiten Sie mit Ihrem IT-Team zusammen, um die externe Frontend-Anwendung einzurichten, die das Inhaltsfragment rendert, indem sie die JSON-Ausgabe nutzt.
* Wenn die externe Frontend-Anwendung eingerichtet ist, muss das **Standard-URL-Vorschaumuster** als [-Eigenschaft des entsprechenden Inhaltsfragmentmodells](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties) definiert werden.

Wenn die URL definiert wurde, wird die Schaltfläche **Vorschau** aktiv. Sie können diese Schaltfläche auswählen, um die externe Anwendung (auf einer separaten Registerkarte) zum Rendern des Inhaltsfragments zu starten.

## Veröffentlichen Ihres Fragments {#publish-content-fragment}

Sie können Ihr Fragment für Folgendes **veröffentlichen**:

* Vorschauinstanz
* Veröffentlichungsinstanz

Sie können das Fragment entweder über den Editor oder die Konsole veröffentlichen. Die vollständigen Details finden Sie unter [Veröffentlichen und Anzeigen der Vorschau eines Fragments](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment).

## Veröffentlichung des Fragments aufheben {#unpublish-content-fragment}

Sie können für Ihr Fragment auch die **Veröffentlichung aufheben**, und zwar in beiden Instanzen:

* Vorschauinstanz
* Veröffentlichungsinstanz

Sie können die Veröffentlichung des Fragments über den Editor oder die Konsole aufheben. Die vollständigen Details finden Sie unter [Aufheben der Veröffentlichung eines Fragments](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment).

## Felder, Datentypen und Symbole {#fields-datatypes-icons}

Im Bereich **Felder** sind alle Felder im Inhaltsfragment aufgeführt. Das Symbol zeigt den **[Datentyp](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)** an:

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><p><b>Einzeilentext</b></p> </td>
   <td><p> <img src="assets/cf-authoring-single-line-text-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Mehrzeilentext</b></p> </td>
   <td><p> <img src="assets/cf-authoring-multi-line-text-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Zahl</b></p> </td>
   <td><p> <img src="assets/cf-authoring-number-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Boolesch</b></p> </td>
   <td><p> <img src="assets/cf-authoring-boolean-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Datum und Uhrzeit</b></p> </td>
   <td><p> <img src="assets/cf-authoring-date-time-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Aufzählung</b></p> </td>
   <td><p> <img src="assets/cf-authoring-enumeration-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Tags</b></p> </td>
   <td><p> <img src="assets/cf-authoring-tags-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Inhaltsreferenz</b></p> </td>
   <td><p> <img src="assets/cf-authoring-content-reference-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Fragmentreferenz</b></p> </td>
   <td><p> <img src="assets/cf-authoring-fragment-reference-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>JSON-Objekt</b></p> </td>
   <td><p> <img src="assets/cf-authoring-json-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Registerkartenplatzhalter</b></p><p>Obwohl nicht durch ein tatsächliches Symbol dargestellt, wird ein <b>Registerkartenplatzhalter</b> wird im linken Bereich angezeigt. <br>Er wird auch im zentralen Bereich angezeigt, entweder horizontal wie gezeigt oder in einer Dropdown-Liste (wenn für eine horizontale Anzeige zu viele vorhanden sind).</p> </td>
   <td><p> <img src="assets/cf-authoring-tab-icon.png"> </p></td>
  </tr>
 </tbody>
</table>

## Wissenswertes {#good-to-know}

* Um ein Inhaltsfragment zu bearbeiten, benötigen Sie [die entsprechenden Berechtigungen](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions). Wenden Sie sich an Ihre Systemadmins, falls Probleme auftreten.

  Wenn Sie beispielsweise nicht über `edit`-Berechtigungen verfügen, ist der Editor schreibgeschützt.

* Ein Inhaltsfragmentmodell kann häufig Datenfelder mit dem Namen **Titel** und **Beschreibung** definieren. Wenn diese Felder vorhanden sind, handelt es sich um benutzerdefinierte Felder, die im *zentralen Bereich* beim Bearbeiten des Fragments aktualisiert werden können.

  Das Inhaltsfragment und seine Varianten verfügen auch über Metadatenfelder (Varianteneigenschaften) namens **Titel** und **Beschreibung**. Diese Felder sind integraler Bestandteil jedes Inhaltsfragments und werden beim Fragment anfänglich definiert. Sie können im *rechten Bereich* beim Bearbeiten des Fragments aktualisiert werden.

* Umfassende Informationen zum [ursprünglichen Inhaltsfragmenteditor](/help/assets/content-fragments/content-fragments-variations.md) finden Sie in der Assets-Dokumentation. Diese ist über die **Assets-Konsole** und die **Inhaltsfragmentkonsole** verfügbar.

* Ihr Projekt-Team kann die Konsole bei Bedarf anpassen. Weitere Details hierzu finden Sie unter [Anpassen von Inhaltsfragmentkonsole und Editor](/help/implementing/developing/extending/content-fragments-console-and-editor.md).
