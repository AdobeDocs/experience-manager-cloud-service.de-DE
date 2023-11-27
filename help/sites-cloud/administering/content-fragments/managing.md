---
title: Verwalten von Inhaltsfragmenten
description: Erfahren Sie, wie Sie Ihre AEM Inhaltsfragmente über die Konsole und den Editor als Grundlage für Ihren Headless Content oder für die Seitenbearbeitung verwalten.
feature: Content Fragments
role: User, Developer, Architect
exl-id: bcaa9f06-b15d-4790-bc4c-65db6a2d5e56
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '2531'
ht-degree: 50%

---

# Verwalten von Inhaltsfragmenten {#managing-content-fragments}

Erfahren Sie, wie Sie Ihre **Inhaltsfragmente** in Adobe Experience Manager (AEM as a Cloud Service) von der dedizierten [Konsole &quot;Inhaltsfragmente&quot;](#content-fragments-console), und [Inhaltsfragmente-Editor](/help/sites-cloud/administering/content-fragments/authoring.md#content-fragment-editor). Diese Inhaltsfragmente können als Grundlage für Ihren Headless-Inhalt oder für die Seitenbearbeitung verwendet werden.

>[!NOTE]
>
>Ihr Projektteam kann die Konsole und den Editor bei Bedarf anpassen. Siehe [Anpassen der Inhaltsfragment-Konsole und des Editors](/help/implementing/developing/extending/content-fragments-console-and-editor.md) für weitere Informationen.

Nach der Definition von [Inhaltsfragmentmodelle](#creating-a-content-model) Sie können diese für Folgendes verwenden:

* [Erstellen von Inhaltsfragmenten](#creating-a-content-fragment).
* Öffnen Sie dann die [Inhaltsfragment-Editor](#opening-the-fragment-editor) nach [Inhalte erstellen und Varianten verwalten](#editing-the-content-of-your-fragment).
* [Tags verwalten](#manage-tags)
* [Eigenschaften (Metadaten) anzeigen und bearbeiten](#viewing-and-editing-properties)
* [Strukturbaum anzeigen](/help/sites-cloud/administering/content-fragments/authoring.md#structure-tree)

>[!NOTE]
>
>Inhaltsfragmente können in folgenden Fällen verwendet werden:
>
>* Für [Headless-Bereitstellung mithilfe von Inhaltsfragmenten mit GraphQL](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md),
>* Beim Erstellung von Seiten. Siehe [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).

>[!NOTE]
>
>Inhaltsfragmente werden als **Assets** gespeichert. Sie werden hauptsächlich über die **Inhaltsfragment**-Konsole verwaltet, können jedoch auch über die [Assets](/help/assets/content-fragments/content-fragments-managing.md)-Konsole verwaltet werden.

## Die Inhaltsfragmentkonsole {#content-fragments-console}

Die Inhaltsfragmentkonsole dient der Verwaltung, Suche und Erstellung von Inhaltsfragmenten. Sie wurde für die Verwendung in einem Headless-Kontext optimiert, wird aber auch beim Erstellen von Inhaltsfragmenten für die Seitenbearbeitung verwendet.

Die Inhaltsfragmentkonsole bietet direkten Zugriff auf Ihre Fragmente und zugehörige Aufgaben. Die Konsole kann direkt von der obersten Ebene der globalen Navigation aus aufgerufen werden.

![Globale Navigation – Inhaltsfragmentkonsole](assets/cf-managing-global-navigation.png)

Weitere Einzelheiten finden Sie unter:

* [Grundlegende Struktur und Handhabung der Inhaltsfragmentkonsole](#basic-structure-handling-content-fragments-console)

* [Die bereitgestellten Informationen zu Ihren Inhaltsfragmenten](#information-content-fragments)

* [Aktionen für ein Inhaltsfragment in der Inhaltsfragmentkonsole](#actions-selected-content-fragment)

* [Spalten auswählen, die in der Konsole angezeigt werden](#select-columns-console)

* [Suchen und Filtern in der Inhaltsfragmentkonsole](#filtering-fragments)

* [&#128279;](/help/sites-cloud/administering/content-fragments/keyboard-shortcuts.md)In dieser Konsole stehen verschiedene Tastaturbefehle zur Verfügung

>[!NOTE]
>
>In dieser Konsole werden nur Inhaltsfragmente angezeigt. Andere Asset-Typen wie Bilder und Videos werden nicht angezeigt.

>[!CAUTION]
>
>Diese Konsole *only* verfügbar in der Online-Adobe Experience Manager (AEM) as a Cloud Service.

### Grundlegende Struktur und Handhabung der Konsole {#basic-structure-handling-content-fragments-console}

Auswählen **Inhaltsfragmente** öffnet die Konsole in einer neuen Registerkarte.

![Inhaltsfragmentkonsole – Übersicht](assets/cf-managing-console-overview.png)

Hier können Sie sehen, dass es drei Hauptbereiche gibt:

* Die obere Symbolleiste
   * Bietet die standardmäßigen AEM-Funktionen
   * Zeigt auch Ihre IMS-Organisation an
   * Bietet verschiedene [Aktionen](#actions-unselected)
* Das linke Bedienfeld
   * Hier können Sie die Ordnerstruktur ein- oder ausblenden
   * Sie können einen bestimmten Zweig des Baums auswählen
   * Die Größe kann geändert werden, um verschachtelte Ordner anzuzeigen
* Das Haupt-/rechte Bedienfeld – von hier aus können Sie:
   * Eine Liste aller Inhaltsfragmente im ausgewählten Zweig des Baums anzeigen:
      * Inhaltsfragmente aus dem ausgewählten Ordner und alle untergeordneten Ordner werden angezeigt:
         * Der Speicherort wird durch die Breadcrumbs angegeben. Diese können auch verwendet werden, um den Speicherort zu ändern:
      * [Informationen zu den einzelnen Fragmenten werden angezeigt](#information-content-fragments)
         * [Sie können auswählen, welche Spalten angezeigt werden sollen](#select-columns-console)
      * [Verschiedene Informationsfelder](#information-content-fragments) zu einem Inhaltsfragment stellen Links bereit. Je nach Feld können diese:
         * Das entsprechende Fragment im Editor öffnen,
         * Informationen zu Verweisen anzeigen,
         * Informationen zu Sprachversionen des Fragments anzeigen.
      * [Bestimmte andere Informationsfelder](#information-content-fragments) über ein Inhaltsfragment verwendet werden kann für [Schnelles Filtern](#fast-filtering):
         * Wert in der Spalte auswählen und sofort als Filter angewendet werden
         * Die schnelle Filterung wird für die **Modell**, **Status**, **Geändert von**, **Tags** und **Veröffentlicht von** Spalten.
      * Wenn Sie den Mauszeiger über die Spaltenüberschriften bewegen, werden ein Selektor der Dropdown-Aktionen und ein Breitenregler angezeigt. Diese ermöglichen Ihnen Folgendes:
         * Sortieren – Wählen Sie die entsprechende Aktion für aufsteigende bzw. absteigende Darstellung aus. 
Dadurch wird die gesamte Tabelle nach dieser Spalte sortiert. Die Sortierung ist nur für die entsprechenden Spalten verfügbar.
         * Ändern Sie die Größe der Spalte – entweder mithilfe der Aktion oder der Breitenregler
      * Wählen Sie ein oder mehrere Fragmente für weitere [action](#actions-selected-content-fragment)
   * Verwenden Sie die [Suche](#searching-fragments) box
   * Öffnen Sie die [Filterbereich](#filtering-fragments)

### Aktionen {#actions}

In der Konsole gibt es eine Reihe von Aktionen, die Sie entweder direkt oder nach Auswahl eines bestimmten Fragments verwenden können:

* Verschiedene Aktionen sind direkt [von der Konsole aus verfügbar](#actions-unselected)
* Sie können [ein oder mehrere Inhaltsfragmente auswählen, um entsprechende Aktionen anzuzeigen](#actions-selected-content-fragment)

#### Aktionen (nicht ausgewählt) {#actions-unselected}

Bestimmte Aktionen sind über die Konsole verfügbar, ohne ein bestimmtes Inhaltsfragment auszuwählen:

* Ein neues Inhaltsfragment **[erstellen](#creating-a-content-fragment)**
* Die Inhaltsfragmente entsprechend einer Auswahl von Eigenschaften [filtern](#filtering-fragments) und den Filter für die zukünftige Verwendung speichern
* Die Inhaltsfragmente [durchsuchen](#searching-fragments)
* [Die Tabellenansicht so anpassen, dass ausgewählte Spalten mit Informationen angezeigt werden](#select-columns-console)
* Verwenden Sie **In Assets öffnen**, um den aktuellen Speicherort direkt in der **Assets**-Konsole zu öffnen

  >[!NOTE]
  >
  >Die **Assets** -Konsole wird verwendet, um auf Assets wie Bilder, Videos usw. zuzugreifen.  Auf die Konsole kann wie folgt zugegriffen werden:
  >
  >* mithilfe des Links **In Assets öffnen** (in der Konsole „Inhaltsfragmente“)
  >* direkt von der globalen **Navigation** Bereich

#### Aktionen für ein (ausgewähltes) Inhaltsfragment {#actions-selected-content-fragment}

Wenn Sie ein bestimmtes Fragment auswählen, wird eine Symbolleiste geöffnet, die sich auf die für dieses Fragment verfügbaren Aktionen konzentriert. Sie können auch mehrere Fragmente auswählen. Die Auswahl der Aktionen wird dann entsprechend angepasst.

![Konsole „Inhaltsfragmente“ – Symbolleiste für ein ausgewähltes Fragment](assets/cf-managing-console-fragment-toolbar.png)

* **[Im neuen Editor öffnen](#editing-the-content-of-your-fragment)**
* **[Öffnen](/help/assets/content-fragments/content-fragments-variations.md)** (im ursprünglichen Editor)
* **[Veröffentlichen](#publishing-and-previewing-a-fragment)** (und **[Veröffentlichung rückgängig machen](#unpublishing-a-fragment)**)
* **[Tags verwalten](#manage-tags)**
* **[Kopieren](/help/assets/manage-digital-assets.md)**
* **[Verschieben](/help/assets/manage-digital-assets.md)**
* **[Umbenennen](/help/assets/manage-digital-assets.md)**
* **[Löschen](#deleting-a-fragment)**

<!--
* **[Replace](#find-and-replace)**
-->

>[!NOTE]
>
>Verwendung **Öffnen** , um das ausgewählte Fragment im *original* Editor.

>[!NOTE]
>
>Aktionen wie Veröffentlichen, Veröffentlichung rückgängig machen, Löschen, Verschieben, Umbenennen und Kopieren jedes Triggers eines asynchronen Auftrags. Der Fortschritt dieses Vorgangs kann über die AEM-Benutzeroberfläche für asynchrone Vorgänge überwacht werden.

### Die bereitgestellten Informationen zu Ihren Inhaltsfragmenten {#information-content-fragments}

Der Haupt-/rechte Bereich (Tabellenansicht) der Konsole enthält eine Reihe von Informationen zu Ihren Inhaltsfragmenten. Einige Elemente bieten auch direkte Links zu weiteren Aktionen und/oder Informationen:

* **Name**
   * Stellt einen Link zum Öffnen des Fragments im Editor bereit.
* **Modell**
   * Nur Informationen.
   * Kann für [Schnelles Filtern](#fast-filtering)
* **Ordner**
   * Stellt einen Link zum Öffnen des Ordners in der Konsole bereit.
Wenn Sie den Mauszeiger über einen Ordnernamen bewegen, wird der JCR-Pfad angezeigt.
* **Status**
   * Nur Informationen.
   * Kann für [Schnelles Filtern](#fast-filtering)
* **Vorschau**
   * Nur Informationen:
      * **Synchronisiert**: Inhaltsfragment ist mit den **Autoren-** und **Vorschau-** Services synchronisiert.
      * **Nicht synchronisiert**: Inhaltsfragment ist nicht mit den **Autoren-** und **Vorschau-** Services synchronisiert. Sie müssen **Veröffentlichen** für eine **Vorschau** einrichten, um sicherzustellen, dass die beiden Instanzen wieder synchronisiert werden.
      * leer: Das Inhaltsfragment existert nicht im **Vorschau**-Service.
* **Geändert**
   * Nur Informationen.
* **Geändert von**
   * Nur Informationen.
   * Kann für [Schnelles Filtern](#fast-filtering).
* **Tags**
   * Nur Informationen.
   * Zeigt alle Tags an, die sich auf das Inhaltsfragment beziehen, sowohl Hauptinhalt als auch alle Varianten.
   * Kann für [Schnelles Filtern](#fast-filtering).
* **Veröffentlicht um**
   * Nur Informationen.
* **Herausgeber**
   * Nur Informationen.
   * Kann für [Schnelles Filtern](#fast-filtering).
* **Referenziert von**:
   * Enthält einen Link, der ein Dialogfeld öffnet, in dem alle [übergeordnete Verweise](#parent-references-fragment)  dieses Fragments, einschließlich der Referenzierung von Inhaltsfragmenten, Experience Fragments und Seiten. Um eine bestimmte Referenz zu öffnen, klicken Sie auf die **Titel** im Dialogfeld.

     ![Inhaltsfragmentkonsole – Dialogfeld „Verweise“](assets/cf-managing-console-references-dialog.png)

* **Sprache**: Geben Sie eine [Sprache](#language-copies-fragment) copy

   * Gibt das Gebietsschema des Inhaltsfragments zusammen mit der Gesamtzahl der lokalen/regionalen[Sprache](#language-copies-fragment)  mit dem Inhaltsfragment verknüpfte Kopien.

     ![Inhaltsfragmentkonsole – Sprachindikator](assets/cf-managing-console-language-indicator.png)

   * Wählen Sie die Anzahl aus, um ein Dialogfeld zu öffnen, das alle Sprachkopien anzeigt. Um eine bestimmte Sprachkopie zu öffnen, klicken Sie auf das **Titel** im Dialogfeld.

     ![Inhaltsfragmentkonsole – Dialogfeld „Sprache“](assets/cf-managing-console-languages-dialog.png)


## Erstellen von Inhaltsfragmenten {#creating-content-fragments}

Vor der Erstellung des Inhaltsfragments muss das zugrunde liegende Inhaltsfragmentmodell erstellt werden.

### Erstellen von Inhaltsmodellen {#creating-a-content-model}

[Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) vor der Erstellung von Inhaltsfragmenten mit strukturiertem Inhalt aktiviert und erstellt werden.

### Erstellen eines Inhaltsfragments {#creating-a-content-fragment}

So erstellen Sie ein Inhaltsfragment:

1. Wählen Sie in der **Inhaltsfragment**-Konsole **Erstellen** (oben rechts).

   >[!NOTE]
   >
   >Damit der Speicherort des neuen Fragments vordefiniert ist, können Sie zu dem Ordner navigieren, in dem Sie das Fragment erstellen möchten, oder Sie können den Speicherort während des Erstellungsprozesses angeben.

1. Die **Neues Inhaltsfragment** wird geöffnet. Hier können Sie Folgendes angeben:

   * **Standort** - wird automatisch mit dem aktuellen Speicherort ausgefüllt, Sie können jedoch bei Bedarf einen anderen Speicherort auswählen.
   * **Inhaltsfragmentmodell** – Wählen Sie aus der Dropdown-Liste das Modell aus, das als Grundlage für das Fragment verwendet werden soll.
   * **Titel**
   * **Name** - wird basierend auf der Variablen **Titel**, kann aber bei Bedarf bearbeitet werden
   * **Beschreibung**

   ![Dialogfeld „Neues Inhaltsfragment“](assets/cf-managing-new-cf-dialog.png)

1. Wählen Sie **Erstellen** oder, um Ihre Definition beizubehalten, **Erstellen und öffnen** aus.

## Status von Inhaltsfragmenten {#statuses-content-fragments}

Während seines Bestehens kann ein Inhaltsfragment mehrere Status haben, wie in der [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) und [Inhaltsfragmente-Editor](/help/sites-cloud/administering/content-fragments/authoring.md):

* **Neu** (grau) Ein neues Inhaltsfragment wurde erstellt, hat jedoch keinen Inhalt, da es noch nie im Inhaltsfragment-Editor bearbeitet oder geöffnet wurde.
* **Entwurf** (blau) Das (neue) Inhaltsfragment wurde im Inhaltsfragment-Editor bearbeitet oder geöffnet - es wurde jedoch noch nicht veröffentlicht.
* **Veröffentlicht** (grün) Das Inhaltsfragment wurde veröffentlicht.
* **Geändert** (orange) Das Inhaltsfragment wurde nach seiner Veröffentlichung (aber vor der Veröffentlichung der Änderung) bearbeitet.
* **Veröffentlichung rückgängig gemacht** (Rot) Die Veröffentlichung des Inhaltsfragments wurde rückgängig gemacht.

## Bearbeiten des Inhalts Ihres Fragments (und der Varianten) {#editing-the-content-of-your-fragment}

>[!IMPORTANT]
>
>Ausführliche Informationen finden Sie unter [siehe Erstellen von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/authoring.md)

So öffnen Sie ein Fragment zur Bearbeitung:

1. Navigieren Sie in der **Inhaltsfragmentkonsole** zum Speicherort des gewünschten Inhaltsfragments.
1. Öffnen Sie das Fragment zur Bearbeitung, indem Sie das Fragment auswählen und dann **Im neuen Editor öffnen** aus der Symbolleiste.

1. Der Fragmenteditor wird geöffnet. Wählen Sie Ihre Anforderungen aus **Variante** können Ihre Änderungen nach Bedarf vornehmen (sie werden automatisch gespeichert):

   ![Fragmenteditor](assets/cf-managing-editor.png)

## Anzeigen und Verwalten von Tags {#manage-tags}

In der Konsole &quot;Inhaltsfragmente&quot;können Sie alle angewendeten Tags im **Tags** -Spalte, nachdem sichergestellt wurde, dass [die Spalte](#select-columns-console).

### Tags verwalten (Konsole) {#manage-tags-console}

So verwalten Sie die Tags:

1. Navigieren Sie zur Konsole Inhaltsfragment .
1. Wählen Sie ein Inhaltsfragment aus.
1. Auswählen **Verwalten von Tags** in der Symbolleiste.
1. Verwenden Sie die Tag-Auswahl, um Tags auszuwählen, die angewendet oder entfernt werden sollen:

   ![Tags verwalten](assets/cf-managing-manage-tags.png)

1. **Speichern** aktualisiert. Dadurch kehren Sie zur Konsole zurück.

### Anzeigen und Bearbeiten von Tags (Editor) {#viewing-and-editing-tags}

Sie können die auf ein Fragment angewendeten Tags auch mithilfe der [Eigenschaften](/help/sites-cloud/administering/content-fragments/authoring.md) des Editors. Die angezeigten Informationen unterscheiden sich zwischen **Main** und **Varianten**.

## Anzeigen und Bearbeiten von Eigenschaften (Editor) {#viewing-and-editing-properties}

Sie können die Eigenschaften (Metadaten) eines Fragments mithilfe der [Eigenschaften](/help/sites-cloud/administering/content-fragments/authoring.md) des Editors. Die angezeigten Informationen unterscheiden sich zwischen **Main** und **Varianten**.

## Veröffentlichen und Anzeigen von Fragmenten in der Vorschau {#publishing-and-previewing-a-fragment}

Sie können Ihre Inhaltsfragmente hier veröffentlichen:

* der **[Publishing-Service](/help/headless/deployment/architecture.md)** – für uneingeschränkten öffentlichen Zugriff

* der **[Vorschau-Service](/help/headless/deployment/architecture.md)** – um den Inhalt for der vollständigen Verfügbarkeit in der Vorschau zu sehen

  >[!CAUTION]
  >
  >Das Veröffentlichen von Inhaltsfragmenten im **Vorschau-Service** ist nur über die Inhaltsfragmentkonsole mithilfe der Aktion **Veröffentlichen** verfügbar.

  >[!NOTE]
  >
  >Weitere Informationen zu Vorschauumgebungen finden Sie unter folgenden Themen:
  >
  >* [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#access-preview-service)
  >* [Konfigurieren der OSGi-Einstellungen für die Vorschauebene](/help/implementing/preview-tier/preview-tier-configuring-osgi.md#configuring-osgi-settings-for-the-preview-tier)
  >* [Debuggen der Vorschau mithilfe der Developer Console](/help/implementing/preview-tier/preview-tier-configuring-osgi.md#debugging-preview-using-the-developer-console)

>[!CAUTION]
>
>Wenn das Fragment auf einem Modell basiert, sollten Sie sicherstellen, dass das [Modell veröffentlicht wurde](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#publishing-a-content-fragment-model).
>
>Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

### Veröffentlichung {#publishing}

Sie können Ihre Inhaltsfragmente mit dem **Veröffentlichen** -Option entweder:

* Symbolleiste der [Konsole &quot;Inhaltsfragmente&quot;](#actions-selected-content-fragment)

   * Wählen Sie ein oder mehrere Fragmente aus der Liste aus.

* Symbolleiste der [Inhaltsfragmente-Editor](/help/sites-cloud/administering/content-fragments/authoring.md#content-fragment-editor)

Nach Auswahl der **Veröffentlichen** Aktion:

1. Wählen Sie eine der folgenden Optionen aus, um das entsprechende Dialogfeld zu öffnen:

   * **Jetzt** - Wählen Sie entweder die **Veröffentlichungsdienst** oder die **Vorschaufunktion** Nach der Bestätigung wird das Fragment sofort veröffentlicht
   * **Zeitplan** - Zusätzlich zum erforderlichen Dienst können Sie auch das Datum und die Uhrzeit der Veröffentlichung des Fragments auswählen

1. Geben Sie alle Details im Dialogfeld an. Beispiel für eine geplante Veröffentlichungsanfrage:

   ![Dialogfeld „Veröffentlichen“](assets/cf-managing-publish-dialog.png)

   >[!NOTE]
   >
   >Bei Bedarf müssen Sie die Verweise auf die Veröffentlichung angeben. Standardmäßig werden Verweise auch im Vorschau-Service veröffentlicht, um sicherzustellen, dass keine Brüche im Inhalt vorhanden sind.

1. Bestätigen Sie die Veröffentlichungsaktion.

Nach der Veröffentlichung wird der Fragmentstatus aktualisiert und im Editor und in der Konsole angezeigt. Wenn Sie eine geplante Veröffentlichung festgelegt haben, werden Informationen angezeigt.

>[!NOTE]
>
>Wenn Sie [eine Seite veröffentlichen, in der das Fragment verwendet wird](/help/sites-cloud/authoring/fundamentals/content-fragments.md#publishing), wird das Fragment außerdem in den Seitenverweisen aufgeführt.

## Rückgängigmachen der Veröffentlichung eines Fragments {#unpublishing-a-fragment}

Sie können die Veröffentlichung von Inhaltsfragmenten rückgängig machen:

* Symbolleiste der [Konsole &quot;Inhaltsfragmente&quot;](#actions-selected-content-fragment)

   * Wählen Sie ein oder mehrere Fragmente aus der Liste aus.

* Symbolleiste der [Inhaltsfragmente-Editor](/help/sites-cloud/administering/content-fragments/authoring.md#content-fragment-editor)

Wählen Sie in beiden Fällen **Veröffentlichung rückgängig machen** in der Symbolleiste, gefolgt von **Jetzt** oder **Geplant**.

Wenn das entsprechende Dialogfeld geöffnet wird, können Sie den entsprechenden Dienst auswählen:

![Dialogfeld &quot;Rückgängig&quot;](assets/cf-managing-unpublish-dialog.png)

>[!NOTE]
>
>Die **Veröffentlichung rückgängig machen** -Aktion ist nur sichtbar, wenn veröffentlichte Fragmente verfügbar sind.

>[!CAUTION]
>
>Wenn das Fragment bereits von einem anderen Fragment oder von einer Seite referenziert wird, wird eine Warnmeldung angezeigt, in der Sie zur Bestätigung des Vorgangs aufgefordert werden.

<!--
## Find and Replace {#find-and-replace}

The **Replace** option is available to find, and replace, specified text in your selected Content Fragment:

![Unpublish dialog](assets/cf-managing-find-replace.png)
-->

## Löschen von Fragmenten {#deleting-a-fragment}

So löschen Sie ein Fragment:

1. Navigieren Sie in der **Inhaltsfragmentkonsole** zum Speicherort des Inhaltsfragments.
1. Wählen Sie das Fragment aus.
1. Wählen Sie **Löschen** in der Symbolleiste aus.
1. Bestätigen Sie die **Löschaktion**.

>[!NOTE]
>
>Die **Löschen** nicht für Fragmente verfügbar ist, die derzeit veröffentlicht werden, sondern zuerst depubliziert werden müssen.

## Suchen von übergeordneten Referenzen Ihres Fragments {#parent-references-fragment}

Details der übergeordneten Verweise können über das

* **Verweise** Spalte der Inhaltsfragmentkonsole
* die [Link zu übergeordneten Verweisen in der oberen Symbolleiste des Inhaltsfragmente-Editors](/help/sites-cloud/administering/content-fragments/authoring.md#view-parent-references)

Beide bieten einen Link, der ein Dialogfeld öffnet, in dem alle übergeordneten Verweise dieses Fragments aufgelistet werden, einschließlich Verweisen auf Inhaltsfragmente, Experience Fragments und Seiten. Um eine bestimmte Referenz zu öffnen, klicken Sie auf die **Titel** oder das Verknüpfungssymbol im Dialogfeld.

Beispiel:

![Inhaltsfragmentkonsole – Dialogfeld „Verweise“](assets/cf-managing-console-references-dialog.png)

## Suchen von Sprachkopien Ihres Fragments {#language-copies-fragment}

Details zu Sprachkopien sind abrufbar unter:

* die **Sprache** Spalte [Inhaltsfragmentkonsole](#information-content-fragments)
* die [Registerkarte &quot;Sprachkopien&quot;des Inhaltsfragmente-Editors](/help/sites-cloud/administering/content-fragments/authoring.md#view-language-copies)

Das Symbol zeigt das Gebietsschema des Inhaltsfragments zusammen mit der Gesamtzahl der mit dem Inhaltsfragment verknüpften Gebietsschemata/Sprachkopien an. Beispielsweise in der Konsole:

![Inhaltsfragmentkonsole – Sprachindikator](assets/cfc-console-language-indicator.png)

Wählen Sie die Anzahl aus, um ein Dialogfeld zu öffnen, das alle Sprachkopien anzeigt. Um eine bestimmte Sprachkopie zu öffnen, klicken Sie auf das **Titel** im Dialogfeld.

![Inhaltsfragmentkonsole – Dialogfeld „Sprache“](assets/cf-managing-console-languages-dialog.png)

## Spalten auswählen, die in der Konsole angezeigt werden {#select-columns-console}

Wie bei anderen Konsolen können Sie konfigurieren, welche Spalten sichtbar und für eine Aktion verfügbar sind:

![Inhaltsfragmentkonsole – Spaltenkonfiguration](assets/cf-managing-console-column-icon.png)

Daraufhin wird eine Liste von Spalten angezeigt, die Sie ausblenden oder anzeigen können:

![Inhaltsfragmentkonsole – Spaltenkonfiguration](assets/cf-managing-console-column-selection.png)

## Filtern von Fragmenten {#filtering-fragments}

Der Filterbereich bietet folgende Optionen:

* eine Auswahl von Prädikaten;
   * einschließlich Inhaltsfragmentmodellen, Lokalisierung, Tags, Statusfelder usw.
   * Es können mindestens ein Prädikat ausgewählt und kombiniert werden, um den Filter zu erstellen
* die Möglichkeit, Ihre Konfiguration zu **speichern**
* die Option zum Abrufen eines gespeicherten Suchfilters für die Wiederverwendung

Nach der Auswahl wird die **Filtern nach** -Optionen angezeigt werden (unter dem Suchfeld). Sie können von dort aus abgewählt werden. Beispiel:

![Inhaltsfragmentkonsole – Filtern](assets/cf-managing-console-filter.png)

### Schnelles Filtern {#fast-filtering}

Sie können auch ein Prädikat auswählen, indem Sie auf einen bestimmten Spaltenwert in der Liste klicken. Sie können einen oder mehrere Werte auswählen, um Eigenschaften zu kombinieren.

Wählen Sie zum Beispiel **Veröffentlicht** in der Spalte **Status**:

>[!NOTE]
>
>Die schnelle Filterung wird nur für die **Modell**, **Status**, **Geändert von**, **Tags**, und **Veröffentlicht von** Spalten.

![Inhaltsfragmentkonsole – Filtern](assets/cf-managing-console-fast-filter-overview.png)

Nach der Auswahl wird dies als Filtereigenschaft angezeigt und die Liste entsprechend gefiltert:

![Konsole „Inhaltsfragmente“ – Filtern](assets/cf-managing-console-fast-filter-criteria.png)

## Suchen von Fragmenten {#searching-fragments}

Das Suchfeld unterstützt die Volltextsuche. Geben Sie Ihre Suchbegriffe in das Suchfeld ein:

![Konsole „Inhaltsfragmente“ – Suchen](assets/cf-managing-console-search-specification.png)

Die ausgewählten Ergebnisse werden bereitgestellt:

![Konsole „Inhaltsfragmente“ – Suchergebnisse](assets/cf-managing-console-search-results.png)

Das Suchfeld bietet außerdem schnellen Zugriff auf die **letzten Inhaltsfragmente** und die **gespeicherten Suchvorgänge**:

![Konsole „Inhaltsfragmente“ – Zuletzt und gespeichert](assets/cf-managing-console-search-saved.png)
