---
title: Autorenumgebung und Tools
description: Die Autorenumgebung von AEM bietet verschiedene Mechanismen für das Organisieren und Bearbeiten von Inhalten
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Autorenumgebung und Tools {#authoring-the-environment-and-tools}

Die Authoring-Umgebung von AEM bietet verschiedene Mechanismen zum Organisieren und Bearbeiten Ihrer Inhalte. Auf die bereitgestellten Tools können Sie von den verschiedenen Konsolen und Seiteneditoren aus zugreifen.

## Verwalten Ihrer Site {#managing-your-site}

The **Sites** console allows you to navigate and manage your website, using the header bar, toolbar, action icons (applicable for the selected resource), breadcrumbs, and, when selected, secondary rails (for example, timeline and references).

Zum Beispiel in der Spaltenansicht:

![Spaltenansicht](/help/sites-cloud/authoring/assets/column-view.png)

## Bearbeiten des Seiteninhalts {#editing-page-content}

Sie können eine Seite mit dem Seiten-Editor bearbeiten. Beispiel:

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

![Seiten-Editor](/help/sites-cloud/authoring/assets/page-editor.png)

>[!NOTE]
>
>Wenn Sie eine Seite zum ersten Mal zur Bearbeitung öffnen, werden Sie in einer Bildschirmpräsentation durch die Funktionen geführt.
>
>Sie können diese Tour überspringen und jederzeit wiederholen, indem Sie sie im Menü **Seiteninformationen** auswählen.

## Aufrufen der Hilfe {#accessing-help}

Wenn Sie eine Seite bearbeiten, können Sie folgendermaßen auf die **Hilfe** zugreifen:

* The [**Page Information **](/help/sites-cloud/authoring/fundamentals/page-properties.md#page-properties)selector which shows the introductory slides (as shown the first time you access the editor)
* The [configuration](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) dialog for specific components (using the ? Symbol in der Symbolleiste des Dialogfelds), das die kontextsensitive Hilfe anzeigt

In den Konsolen stehen weitere [Hilferessourcen zur Verfügung](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help).

## Komponenten-Browser {#components-browser}

Komponenten sind die Bausteine von AEM-Inhalten. Sie platzieren mehrere Komponenten auf einer Seite und konfigurieren deren Optionen, um Ihre Inhaltsseite mit AEM zu erstellen.

Der Komponenten-Browser enthält alle Komponenten, die zur Verwendung auf der aktuellen Seite verfügbar sind. Sie können diese an die gewünschte Position ziehen und dann bearbeiten, um Inhalte hinzuzufügen.

The components browser is a tab within the side panel (together with the [assets browser](#assets-browser) and [content tree](#content-tree)). Um das Bedienfeld zu öffnen (oder zu schließen), verwenden Sie das Symbol links oben in der Symbolleiste:

![Umschalten zwischen Seitenbedienfeld](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Wenn Sie das Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Wählen Sie hier ggf. die Registerkarte **Komponenten**. Wenn diese geöffnet ist, können Sie alle für die Seite verfügbaren Komponenten durchsuchen.

Das tatsächliche Aussehen und die Nutzung hängen vom verwendeten Gerätetyp ab:

* **Mobilgerät (z. B. iPad)**

   Der Komponenten-Browser deckt die gesamte bearbeitete Seite ab.

   Um der Seite eine Komponente hinzuzufügen, berühren und halten Sie die gewünschte Komponente und verschieben Sie sie nach rechts. Der Komponenten-Browser wird geschlossen und die Seite wird erneut angezeigt. Sie können die Komponente jetzt dort platzieren.

   ![Komponentenbrowser auf einem Mobilgerät](/help/sites-cloud/authoring/assets/component-browser-mobile.png)

* **Desktop-Gerät**

   Der Komponenten-Browser wird auf der linken Seite des Fensters geöffnet.

   Um der Seite eine Komponente hinzuzufügen, klicken Sie auf die gewünschte Komponente und ziehen Sie sie an die gewünschte Position.

   ![Komponenten-Browser auf dem Desktop](/help/sites-cloud/authoring/assets/component-browser-desktop.png)

   Komponenten werden wie folgt dargestellt:

   * Komponentenname
   * Komponentengruppe (grau)
   * Symbol oder Abkürzung
      * Die Symbole für die Standardkomponenten sind monochrom dargestellt.
      * Abkürzungen sind immer die ersten beiden Zeichen des Komponentennamen.
   In der oberen Symbolleiste des **Komponenten-Browsers** haben Sie folgende Möglichkeiten:

   * Komponenten nach Namen filtern
   * mittels Dropdown-Auswahl die Anzeige auf eine bestimmte Gruppe begrenzen
   Sofern verfügbar, können Sie zudem eine detaillierte Beschreibung zu einer Komponente aufrufen. Klicken oder tippen Sie dazu im **Komponenten-Browser** auf das Infosymbol neben der jeweiligen Komponente. Beispiel für das **Inhaltsfragment**:

   ![Komponenten-Browser-Informationen](/help/sites-cloud/authoring/assets/component-browser-information.png)

   Weiterführende Informationen zu den verfügbaren Komponenten finden Sie unter [Komponenten-Konsole](/help/sites-cloud/authoring/features/components-console.md).

>[!NOTE]
>
>Ein Mobilgerät wird erkannt, wenn die Breite weniger als 1024 Pixel beträgt. Dies kann auch bei einem kleinen Desktop-Fenster der Fall sein.

## Asset-Browser {#assets-browser}

Der Asset-Browser enthält alle Assets, die auf Ihrer aktuellen Seite direkt verwendet werden können. <!--The assets browser shows all [assets](/help/assets/home.md) that are available for direct use on your current page.-->

The assets browser is a tab within the side panel along with the [components browser](#components-browser) and [content tree](#content-tree). Um das Bedienfeld zu öffnen (oder zu schließen), verwenden Sie das Symbol links oben in der Symbolleiste:

![Umschalten zwischen Seitenbedienfeld](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Wenn Sie das Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Wählen Sie hier ggf. die Registerkarte **Assets**.

![Schaltfläche &quot;Asset Browser&quot;](/help/sites-cloud/authoring/assets/assets-browser-button.png)

Wenn der Asset-Browser geöffnet ist, können Sie alle für die Seite verfügbaren Assets durchsuchen. Bei Bedarf können Sie die Liste durch Scrollen unendlich erweitern.

![Asset-Browser](/help/sites-cloud/authoring/assets/assets-browser.png)

Um ein Asset zu der Seite hinzuzufügen, wählen Sie es aus und ziehen Sie es an die gewünschte Position. Dabei kann es sich um Folgendes handeln:

* Eine vorhandene Komponente des entsprechenden Typs.
   * Sie können beispielsweise ein Asset des Typs „Bild“ auf eine Bildkomponente ziehen.
* Ein [Platzhalter](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-placeholder) im Absatzsystem zum Erstellen einer neuen Komponente des entsprechenden Typs.
   * Sie können beispielsweise ein Asset vom Typ image in das Absatzsystem ziehen, um eine Bildkomponente zu erstellen.

>[!NOTE]
>
>Dies ist für spezielle Assets und Komponententypen verfügbar. Weitere Einzelheiten finden Sie unter [Einfügen einer Komponente mit dem Asset-Browser ](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-using-the-assets-browser).

In der Symbolleiste des Asset-Browsers können Sie Assets nach folgenden Kriterien filtern:

* Name
* Pfad
* Asset-Typ wie Bilder, Videos, Dokumente, Absätze, Inhaltsfragmente und Erlebnisfragmente
* Asset-Eigenschaften wie Ausrichtung und Stil
   * Nur für bestimmte Asset-Typen verfügbar

Das tatsächliche Aussehen und die Nutzung hängen vom verwendeten Gerätetyp ab:

* **Mobilgerät**

   Der Asset-Browser deckt die gesamte bearbeitete Seite ab.

   Um der Seite ein Asset hinzuzufügen, berühren und halten Sie das gewünschte Asset und verschieben Sie es nach rechts. Der Asset-Browser wird geschlossen und die Seite wird erneut angezeigt. Jetzt können Sie das Asset der gewünschten Komponente hinzufügen.

   ![Asset Browser auf Mobilgeräten](/help/sites-cloud/authoring/assets/assets-browser-mobile.png)

* **Desktop-Gerät**

   Der Asset-Browser wird auf der linken Seite des Fensters geöffnet.

   Um ein Asset zu Ihrer Seite hinzuzufügen, klicken Sie auf das gewünschte Asset und ziehen Sie es auf die benötigte Komponente oder Stelle.

   ![Asset Browser auf dem Desktop](/help/sites-cloud/authoring/assets/assets-browser-desktop.png)

>[!NOTE]
>
>Ein Mobilgerät wird erkannt, wenn die Breite geringer als 1024 Pixel ist, d. h. auch bei einem kleinen Desktop-Fenster.

Wenn Sie eine Änderung an einem der Assets vornehmen möchten, können Sie den Asset-Editor auch direkt über den Browser starten. Klicken Sie dazu einfach auf das Bearbeitungssymbol neben dem Asset-Namen. <!--If you need to quickly make a change to an asset, you can start the [asset editor](/help/assets/manage-digital-assets.md) directly from the asset browser by clicking the edit icon shown next to the asset's name.-->

![Schaltfläche zum Bearbeiten von Assets](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Inhaltsstruktur     {#content-tree}

Die **Inhaltsstruktur** bietet einen Überblick über alle auf der Seite verwendeten Komponenten in einer hierarchischen Darstellung, sodass Sie direkt feststellen können, wie die Seite aufgebaut ist.

Die Inhaltsstruktur befindet sich auf einer Registerkarte im seitlichen Bedienfeld (zusammen mit dem Asset-Browser). Um das Bedienfeld zu öffnen (oder zu schließen), verwenden Sie das Symbol links oben in der Symbolleiste:

![Schaltfläche &quot;Inhaltsstruktur&quot;](/help/sites-cloud/authoring/assets/content-tree-button.png)

Wenn Sie das Bedienfeld öffnen, wird es von der linken Seite aus eingeblendet. Select the **Content Tree** tab if necessary. Mit dieser Strukturansicht Ihrer Seite oder Vorlage können Sie leicht nachvollziehen, wie die darauf verwendeten Komponenten hierarchisch strukturiert sind. Auf einer komplexer gestalteten Seite können Sie so zudem einfacher zwischen Komponenten auf der Seite wechseln.

![Inhaltsstruktur    ](/help/sites-cloud/authoring/assets/content-tree-editor.png)

Eine Seite kann problemlos aus mehreren Komponenten desselben Typs bestehen, sodass der Inhaltsbaum (Komponenten) nach dem Namen des Komponententyps (in Schwarz) beschreibenden Text (grau) anzeigt. Der Text für diese Beschreibung wird aus den allgemeinen Eigenschaften der Komponente (z. B. Titel oder Text) entnommen.

Die Komponententypen werden in der für die Benutzeroberfläche ausgewählten Sprache angezeigt, die Beschreibung dagegen in der Sprache, die für die Seite verwendet wird.

Durch Klicken auf den Richtungspfeil neben einer Komponente wird die entsprechende Ebene ein- bzw. ausgeblendet.

![Content Tree chevron-Erweiterung](/help/sites-cloud/authoring/assets/content-tree-chevron.png)

Durch Klicken auf die Komponente wird diese im Seiten-Editor markiert. Die verfügbaren Aktionen hängen vom Status der Seite ab:

* Zum Beispiel bei einer einfachen Seite:

   ![Inhaltsstruktur hervorgehoben](/help/sites-cloud/authoring/assets/content-tree-highlighted.png)

   Die Komponenten einer Basisseite haben die üblichen Optionen.

   Wenn Sie in der Struktur auf eine Komponente klicken, die bearbeitbar ist, wird rechts neben ihrem Namen ein Schraubenschlüssel-Symbol angezeigt. Durch Klicken auf dieses Symbol können Sie das Dialogfeld für die Bearbeitung der Komponente direkt aufrufen.

   ![Schaltfläche zum Bearbeiten der Inhaltsstruktur](/help/sites-cloud/authoring/assets/content-tree-edit.png)

* Eine Seite, die Teil einer Livecopy ist und auf der Komponenten von einer anderen Seite geerbt werden, verfügt über eine eingeschränkte Auswahl an Optionen, einschließlich der Vererbungsoptionen. <!--A page that is part of a [livecopy](/help/sites-administering/msm.md), where components are inherited from another page:-->

>[!NOTE]
>
>Die Inhaltsstruktur ist nicht verfügbar, wenn Sie eine Seite auf einem Mobilgerät bearbeiten (wenn die Browserbreite unter 1024 px liegt).

## Fragmente: Browser für zugehörige Inhalte {#fragments-associated-content-browser}

Wenn Ihre Seite Inhaltsfragmente enthält, haben Sie auch Zugriff auf den [Browser für zugehörige Inhalte](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content). 

## Verweise {#references}

**Verweise** zeigen Verbindungen zur ausgewählten Seite an:

* Blueprints
* Launches
* Live Copys
* Sprachkopien
* Eingehende Links
* Verwendung der Referenzkomponente: geliehener und verliehener Inhalt

Open the required console, then navigate to the required resource and open **References** using:

![Referenzen, Option](/help/sites-cloud/authoring/assets/references.png)

[Wählen Sie die gewünschte Ressource aus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources), um eine Liste der Verweistypen anzuzeigen, die für diese Ressource relevant sind:

![Verweisdetails](/help/sites-cloud/authoring/assets/references-detail.png)

Wählen Sie den gewünschten Verweistyp, um weitere Informationen anzuzeigen: In bestimmten Situationen sind weitere Aktionen verfügbar, wenn Sie einen bestimmten Verweis auswählen:

* **Eingehende Links** enthält eine Liste der Seiten, die auf die Seite verweisen, und bietet direkten Zugriff zum **Bearbeiten** einer dieser Seiten, wenn Sie einen bestimmten Link auswählen. 
* Instanzen von geliehenen und verliehenen Inhalten, die die **Referenz**-Komponente verwenden. Sie können von hier aus zur referenzierten Seite navigieren.  
* [Starts](/help/sites-cloud/authoring/launches/overview.md), bietet Zugriff auf zugehörige Starts
* Live Copies displays the paths of all live copies that are based on the selected resource. <!--[Live Copies](/help/sites-administering/msm.md) displays the paths of all live copies that are based on the selected resource.-->
* Blueprint provides details and various actions <!--[Blueprint](/help/sites-administering/msm-best-practices.md), provides details and various actions-->
* Languages Copies provides details and various actions <!--[Languages Copies](/help/sites-administering/tc-manage.md#creating-translation-projects-using-the-references-panel), provides details and various actions-->

## Ereignisse: Timeline {#events-timeline}

Bei bestimmten Ressourcen (z. B. Seiten aus der **Sites-Konsole** oder Assets aus der **Asset-Konsole**) kann die [Timeline dazu verwendet werden, die zuletzt durchgeführten Aktivitäten für ausgewählte Elemente anzuzeigen](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline).

Open the required console, then navigate to the required resource and open **Timeline**, using:

![Zeitschiene](/help/sites-cloud/authoring/assets/timeline.png)

[Wählen Sie die gewünschte Ressource ](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)und danach entweder **Alle anzeigen** oder **Aktivitäten** aus, um die auf die ausgewählten Ressourcen zuletzt ausgeführten Aktionen aufzulisten:

![Details zur Zeitschiene](/help/sites-cloud/authoring/assets/timeline-detail.png)

## Seiteninformationen {#page-information}

Mit den Seiteninformationen (Equalizer-Symbol) wird ein Menü geöffnet, das auch Details zur letzten Bearbeitung und zur letzten Veröffentlichung enthält. Abhängig von den Eigenschaften der Seite (und der Website, zu der sie gehört) sind u. U. weitere Optionen verfügbar:

![Seiteninformationen, Option](/help/sites-cloud/authoring/assets/page-information.png)

* [Eigenschaften öffnen](/help/sites-cloud/authoring/fundamentals/page-properties.md)
* Seiten-Rollout <!--[Rollout Page](/help/sites-administering/msm.md#msm-from-the-ui)-->
* [Workflow starten](/help/sites-cloud/authoring/workflows/applying.md#starting-a-workflow-from-the-page-editor)
* [Seite sperren](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page)
* [Seite veröffentlichen](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-pages-1)
* [Veröffentlichen einer Seite rückgängig machen](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages)
* [Vorlage bearbeiten](/help/sites-cloud/authoring/features/templates.md)
* [Als veröffentlicht anzeigen](/help/sites-cloud/authoring/fundamentals/editing-content.md#view-as-published)
* [In Admin anzeigen](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
* [Hilfe](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help)
* [Launch](/help/sites-cloud/authoring/launches/promoting.md) bewerben (nur, wenn die Seite ein Launch ist)

Darüber hinaus können über die **Seiteninformationen** ggf. auch Analysen und Empfehlungen aufgerufen werden.

## Seitenmodi {#page-modes}

Für die Bearbeitung von Seiten stehen verschiedene Modi zur Verfügung, über die jeweils unterschiedliche Aktionen durchgeführt werden können:

* [Bearbeiten:](/help/sites-cloud/authoring/fundamentals/editing-content.md) Der Modus zum Bearbeiten des Seiteninhalts.
* [Layout](/help/sites-cloud/authoring/features/responsive-layout.md) - ermöglicht das Erstellen und Bearbeiten eines reaktionsfähigen Layouts je nach Gerät (wenn die Seite auf einem Layout-Container basiert)
* [Zielsetzung:](/help/sites-cloud/authoring/personalization/targeted-content.md) Steigerung der Inhaltsrelevanz durch Zielsetzung und Messung über alle Kanäle hinweg.
* [Timewarp](/help/sites-cloud/authoring/features/page-versions.md#timewarp): Ermöglicht es, eine Seite in dem Zustand anzuzeigen, den sie zu einem früheren Zeitpunkt aufgewiesen hat.
* [Live Copy-Status:](/help/sites-cloud/authoring/fundamentals/editing-content.md#live-copy-status) Für einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten übernommen oder nicht übernommen wurden.
* [Vorschau](/help/sites-cloud/authoring/fundamentals/editing-content.md#previewing-pages): Dient zur Anzeige der Darstellung der Seite in der Veröffentlichungsumgebung oder zur Navigation anhand der Links im Inhalt.
* [Anmerken](/help/sites-cloud/authoring/fundamentals/annotations.md): In diesem Modus können Sie Anmerkungen auf der Seite hinzufügen oder anzeigen.

Sie können darauf über das Symbol oben rechts im Bildschirm zugreifen. Das Symbol ändert abhängig vom verwendeten Modus:

![Seitenmodi](/help/sites-cloud/authoring/assets/page-modes.png)

>[!NOTE]
>
>* Abhängig von den Merkmalen der Seite sind einige Modi ggf. nicht verfügbar.
>* Für den Zugriff auf einige Modi sind die entsprechenden Berechtigungen erforderlich.
>* Aus Platzgründen steht der Entwicklermodus auf Mobilgeräten nicht zur Verfügung.
>* There is a [keyboard shortcut](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) ( `Ctrl-Shift-M`) to toggle between **Preview** and the currently selected mode (e.g. **Edit**, **Layout**, etc).
>



## Pfadauswahl {#path-selection}

Oft muss bei der Bearbeitung einer Seite eine andere Ressource ausgewählt werden (z. B. zum Definieren eines Links zu einer anderen Seite/Ressource oder zum Auswählen eines Bilds). Zur Vereinfachung der Pfadauswahl werden Eingaben in den [Pfad-Feldern](#path-fields) automatisch ausgefüllt. Ergänzend dazu stehen zudem leistungsstarke Auswahlfunktionen im [Pfadbrowser](#path-browser) zur Verfügung.

### Pfad-Felder {#path-fields}

Im vorliegenden Beispiel wird zur Verdeutlichung die Bildkomponente verwendet. Weitere Informationen zur Verwendung und Bearbeitung von Komponenten finden Sie unter [Komponenten für die Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/components.md).

Pfadfelder verfügen jetzt über eine Funktion zum automatischen Ausfüllen und Aussehen, um die Suche nach einer Ressource zu vereinfachen.

Durch Klicken auf die Schaltfläche **Auswahl-Dialogfeld öffnen** auf dem Pfad-Feld wird das Dialogfeld [Pfadbrowser](#path-browser) geöffnet, in dem Optionen für eine präzisere Auswahl zur Verfügung stehen.

![Schaltfläche &quot;Auswahldialogfeld öffnen&quot;](/help/sites-cloud/authoring/assets/open-selection-dialog-button.png)

Alternativ können Sie etwas in das Pfad-Feld eingeben und AEM schlägt Ihrer Eingabe entsprechend passende Pfade vor.

![Schaltfläche &quot;Auswahldialogfeld öffnen&quot;](/help/sites-cloud/authoring/assets/path-selection-completion.png)

### Pfadbrowser {#path-browser}

Der Pfadbrowser ist wie die [Spaltenansicht](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) der Sites-Konsole aufgebaut und ermöglicht eine präzisere Auswahl der Ressourcen.

![Pfadbrowser](/help/sites-cloud/authoring/assets/path-browser.png)

* Sobald eine Ressource ausgewählt wird, wird die Schaltfläche **Auswählen** oben rechts im Dialogfeld aktiviert. Klicken/tippen Sie darauf, um die Auswahl zu bestätigen, oder heben Sie die Auswahl über **Abbrechen** auf.
* Abhängig vom Kontext können auch mehrere Ressourcen ausgewählt werden. In diesem Fall wird durch Auswählen einer Ressource ebenfalls die Schaltfläche **Auswählen** aktiviert, wobei zusätzlich oben rechts im Fenster auch die Anzahl der ausgewählten Ressourcen angezeigt wird. Klicken Sie neben der Zahl auf **X**, wenn Sie die Auswahl für alle aufheben möchten.
* Wenn Sie durch den Baum navigieren, wird Ihre Position in den Breadcrumbs am oberen Rand des Dialogfelds angezeigt. Mithilfe der Breadcrumbs können Sie innerhalb der Ressourcenhierarchie schnell von einem Punkt zu einem anderen wechseln.
* Darüber hinaus können Sie auch jederzeit das Suchfeld oben im Dialogfeld verwenden. Klicken Sie im Suchfeld auf **X**, wenn Sie die Suche löschen möchten.
* Sie können Ihre Suche auch eingrenzen, indem Sie die Filteroptionen einblenden und die Ergebnisse nach Pfad filtern.

   ![Filter, Option](/help/sites-cloud/authoring/assets/filters-option.png)

## Tastaturbefehle {#keyboard-shortcuts}

Für die Bedienung stehen verschiedene [Tastaturbefehle](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) zur Verfügung.
