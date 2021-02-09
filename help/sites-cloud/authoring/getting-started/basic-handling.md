---
title: Grundlegende Handhabung
description: Machen Sie sich mit der Steuerung von AEM und seiner grundlegenden Verwendung vertraut.
translation-type: tm+mt
source-git-commit: 305f584d89bc92f89b3ddaa49bb5da2f10e567db
workflow-type: tm+mt
source-wordcount: '2864'
ht-degree: 100%

---


# Grundlegende Handhabung {#basic-handling}

Dieses Dokument soll einen Überblick über die grundlegende Handhabung der AEM-Autorenumgebung geben. Als Grundlage wird die **Sites-Konsole** verwendet.

>[!NOTE]
>
>* Einige Funktionen stehen nicht in allen Konsolen zur Verfügung und in einigen Konsolen können zusätzliche Funktionen zur Verfügung stehen. Detaillierte Informationen zu den einzelnen Konsolen und ihren jeweiligen Funktionen finden Sie auf den anderen Seiten.
>* In AEM stehen verschiedene Tastaturbefehle zur Verfügung, insbesondere bei [der Verwendung von Konsolen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) und [der Bearbeitung von Seiten](/help/sites-cloud/authoring/fundamentals/keyboard-shortcuts.md).


## Touch-optimierte Benutzeroberfläche {#a-touch-enabled-ui}

Die Benutzeroberfläche für AEM wurde für Touchscreens optimiert. Eine Touch-optimierte Benutzeroberfläche ermöglicht es Ihnen, mithilfe von Berührungen – Tippen, Berühren und Halten sowie Wischen – mit der Software zu interagieren. Da die AEM-Benutzeroberfläche Touch-optimiert ist, können Sie Berührungsgesten auf Ihren Touch-Geräten wie auf Ihrem Handy oder Tablet verwenden. Es sind jedoch auch Mausaktionen auf einem herkömmlichen Desktop-Gerät möglich, sodass Sie flexibel entscheiden können, wie Sie Ihre Inhalte erstellen möchten.

## Erste Schritte {#first-steps}

Unmittelbar nach der Anmeldung gelangen Sie zum [Navigationsfenster](#navigation-panel). Durch Auswahl einer der Optionen wird die entsprechende Konsole geöffnet.

![Navigationsfenster](/help/sites-cloud/authoring/assets/navigation.png)

Damit Sie ein gutes Verständnis der grundlegenden Funktionen in AEM erhalten, wurde für dieses Dokument die **Sites-Konsole** herangezogen. Klicken bzw. tippen Sie auf **Sites**, um zu beginnen.

## Produktnavigation {#product-navigation}

Wenn ein Benutzer zum ersten Mal auf eine Konsole zugreift, wird ein Tutorial zur Produktnavigation gestartet. Nehmen Sie sich einen Moment Zeit, um sich das Programm anzusehen und einen guten Überblick über den grundlegenden Umgang mit AEM zu erhalten.

![Navigations-Tutorial](/help/sites-cloud/authoring/assets/tutorial.png)

Klicken oder tippen Sie auf **Weiter**, um zur nächsten Seite der Übersicht zu wechseln. Klicken bzw. tippen Sie auf **Schließen** oder klicken Sie außerhalb des Überblicksfensters, um es zu schließen.

Die Übersicht wird bei Ihrem nächsten Zugriff auf eine Konsole wieder gestartet, sofern Sie nicht die Option **Nicht mehr anzeigen** aktivieren.

## Globale Navigation {#global-navigation}

Sie können mithilfe des globalen Navigationsfensters zwischen den Konsolen navigieren. Dieses Navigationsfenster wird als Vollbild-Dropdown angezeigt, wenn Sie auf den AEM-Link in der oberen linken Bildschirmecke klicken oder tippen.

Sie können das globale Navigationsfenster schließen, indem Sie auf **Schließen** klicken oder tippen. Sie kehren dann zu Ihrer vorherigen Position zurück.

![Navigationsfenster obere Leiste](/help/sites-cloud/authoring/assets/navigation-bar.png)

Die globale Navigation verfügt über zwei Fenster, die am linken Bildschirmrand durch Symbole dargestellt werden:

* **[Navigation](#navigation-panel)** – dargestellt durch einen Kompass  und das Standardfenster bei der Anmeldung in AEM
* **[Tools](#tools-panel)** – dargestellt durch einen Hammer

Die in diesen Fenstern verfügbaren Optionen werden im Folgenden beschrieben.

### Navigationsfenster  {#navigation-panel}

Das Navigationsfenster:

![Navigationsfenster](/help/sites-cloud/authoring/assets/navigation.png)

Der Titel der Browser-Registerkarte wird aktualisiert, um Ihren Standort während der Navigation durch die Konsolen und Inhalte widerzuspiegeln.

Im Navigationsfenster stehen folgende Konsolen zur Verfügung:

| Konsole | Zweck |
|---|---|
| Projekte | Die Projektekonsole bietet Ihnen direkten Zugriff auf Ihre Projekte. [Projekte sind virtuelle Dashboards](/help/sites-cloud/authoring/projects/overview.md), die zum Aufbau eines Teams verwendet werden können. Sie können diesem Team dann Zugriff auf Ressourcen, Workflows und Aufgaben gewähren, damit alle auf ein gemeinsames Ziel hinarbeiten. |
| Sites | Mit der Konsole „Sites“ können Sie [Websites erstellen, anzeigen und verwalten](/help/sites-cloud/authoring/fundamentals/organizing-pages.md), die auf Ihrer AEM-Instanz ausgeführt werden. Mithilfe dieser Konsole können Sie Seiten erstellen, bearbeiten, kopieren, verschieben, löschen und veröffentlichen sowie Workflows starten. |
| Experience Fragments | Bei einem [Experience Fragment](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) handelt es sich um ein einzelnes Erlebnis, das kanalübergreifend wiederverwendet werden kann und Varianten aufweist. So erübrigt sich das wiederholte Kopieren und Einfügen von Erlebnissen oder Teilen von Erlebnissen. |
| Assets | In der Konsole „Assets“ können Sie digitale Assets, wie Bilder, Videos, Dokumente und Audiodateien, importieren und verwalten. Diese Assets können dann von jeder Site verwendet werden, die auf derselben AEM-Instanz ausgeführt wird.<!--add some kind of assets link--> |
| Personalisierung | Diese Konsole bietet ein Framework aus Tools für die [Bearbeitung von Inhalt für eine bestimmte Zielgruppe und die Darstellung personalisierter Erlebnisse](/help/sites-cloud/authoring/personalization/overview.md). |

## Tools-Bereich {#tools-panel}

Im Tools-Bereich befindet sich ein seitliches Bedienfeld mit einem Bereich von Kategorien, in denen ähnliche Tools-Konsolen gruppiert sind. Die Tools-Konsolen bieten Zugriff auf eine Vielzahl spezialisierter Tools und Konsolen, mit denen Sie Websites, digitale Assets und andere Bereiche Ihres Inhalts-Repositorys verwalten können. <!--The [Tools consoles](/help/sites-administering/tools-consoles.md) provide access to a number of specialized tools and consoles that help you administer your websites, digital assets, and other aspects of your content repository.-->

![Tools-Bereich](/help/sites-cloud/authoring/assets/tools-panel.png)

## Die Kopfzeile {#the-header}

Die Kopfzeile befindet sich immer am oberen Rand der Bildschirmseite. Die meisten Optionen in der Kopfzeile bleiben unabhängig von Ihrer Position im System gleich, manche sind aber kontextspezifisch.

![Navigationskopfzeile](/help/sites-cloud/authoring/assets/navigation-bar.png)

* [Globale Navigation](#global-navigation)

   Wählen Sie den Link **Adobe Experience Manager** aus, um zwischen Konsolen zu navigieren.

   ![Globale Navigation](/help/sites-cloud/authoring/assets/global-navigation.png)

* [Suchen](/help/sites-cloud/authoring/getting-started/search.md)

   ![Suchsymbol](/help/sites-cloud/authoring/assets/search-icon.png)

   Sie können auch den [Tastaturbefehl](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `/` (Schrägstrich) verwenden, um von jeder beliebigen Konsole aus die Suche zu starten.

* [Lösungen](https://www.adobe.com/experience-cloud.html)

   ![Schaltfläche „Lösungen“](/help/sites-cloud/authoring/assets/solutions.png)

* [Hilfe](#accessing-help)

   ![Schaltfläche „Hilfe“](/help/sites-cloud/authoring/assets/help.png)

* [Benachrichtigungen](/help/sites-cloud/authoring/getting-started/inbox.md)

   ![Schaltfläche „Benachrichtigungen“](/help/sites-cloud/authoring/assets/notifications.png)

   Dieses Symbol wird mit der Anzahl der aktuell zugewiesenen unvollständigen Benachrichtigungen gekennzeichnet.

* [Benutzereigenschaften](/help/sites-cloud/authoring/getting-started/account-environment.md)

   ![Schaltfläche „Benutzereigenschaften“](/help/sites-cloud/authoring/assets/user-properties.png)

* [Schienenauswahl](#rail-selector)

   ![Schaltfläche „Schienenauswahl“](/help/sites-cloud/authoring/assets/rail-selector.png)

   Die angezeigten Optionen hängen von der jeweiligen Konsole ab. So können Sie z. B. in **Sites** nur Inhalt (Standard), die Zeitleiste, Verweise oder das seitliche Bedienfeld „Filter“ auswählen.

   ![Beispiel für Schienenauswahl](/help/sites-cloud/authoring/assets/rail-selector-example.png)

* Breadcrumb

   ![Breadcrumbs in der Navigationsleiste](/help/sites-cloud/authoring/assets/breadcrumbs-navigation.png)

   Breadcrumbs befinden sich immer in der Mitte der Leiste und zeigen die Beschreibung des aktuell ausgewählten Elements an. Sie ermöglichen Ihnen damit die Navigation innerhalb einer bestimmten Konsole. In der **Sites**-Konsole können Sie damit durch die Ebenen Ihrer Website navigieren.

   Klicken Sie einfach auf den Breadcrumb-Text, um eine Dropdown-Liste mit den Hierarchieebenen des aktuell ausgewählten Elements anzuzeigen. Klicken Sie auf einen Eintrag, um zu dieser Position zu gelangen.

   ![Beispiel für Breadcrumbs (erweitert)](/help/sites-cloud/authoring/assets/breadcrumbs-example.png)

* Schaltfläche **Erstellen**

   ![Schaltfläche „Erstellen“](/help/sites-cloud/authoring/assets/create.png)

   Wird hierauf geklickt, entsprechen die angezeigten Optionen der Konsole/dem Kontext.

* [Ansichten](#viewing-and-selecting-resources)

   Das Ansichtssymbol befindet sich ganz rechts in der AEM-Symbolleiste. Da es auch die aktuelle Ansicht anzeigt, ändert es sich. In der Standardansicht wird beispielsweise in der **Spaltenansicht** Folgendes angezeigt:

   ![Schaltfläche „Ansichten“](/help/sites-cloud/authoring/assets/views-button.png)

   Sie können zwischen der Spalten-, Karten- und Listenansicht wechseln; in der Listenansicht werden auch die Ansichtseinstellungen angezeigt.

   ![Ansichten](/help/sites-cloud/authoring/assets/view.png)

   >[!NOTE]
   >
   >Die Option **Ansichtseinstellungen** steht nur im Modus **Listenansicht** zur Verfügung.

* Navigation über die Tastatur

   Sie haben die Möglichkeit, auf einer Website nur mit der Tastatur zu navigieren. Dabei wird die Standard-Browser-Funktionalität der **TAB**-Taste (oder **WAHL+TAB**) verwendet, um zwischen fokussierbaren Elementen auf der Seite zu wechseln.

   In der **Sites**-Konsole gibt es die zusätzliche Option, **zum Hauptinhalt zu wechseln**. Diese wird sichtbar, wenn Sie durch die Kopfzeilenoptionen blättern, und beschleunigt Ihre Navigation, indem Sie die Standardelemente in der (Produkt-)Symbolleiste überspringen und direkt zum Hauptinhalt wechseln.

   ![Zum Hauptinhalt wechseln](/help/sites-cloud/authoring/assets/skip-to-main-content.png)

## Aufrufen der Hilfe {#accessing-help}

Ihnen stehen verschiedene Hilferessourcen zur Verfügung:

* **Konsolensymbolleiste**

   Durch Auswahl des Symbols **Hilfe** werden abhängig von Ihrer Position die geeigneten Ressourcen geöffnet:

   ![Hilfesymbol](/help/sites-cloud/authoring/assets/help-console.png)

* **Navigation**

   Beim erstmaligen Navigieren im System [wird die AEM-Navigation über eine Reihe von Folien vorgestellt](#product-navigation).

   ![Tutorial](/help/sites-cloud/authoring/assets/tutorial.png)

* **Seiten-Editor**

   Wenn Sie zum ersten Mal eine Seite bearbeiten, wird der Seiten-Editor durch eine Reihe von Folien vorgestellt.

   ![Editor-Tutorial](/help/sites-cloud/authoring/assets/editor-tutorial.png)

   Navigieren Sie in diesem Überblick wie im [Überblick zur Produktnavigation](#product-navigation) beim erstmaligen Öffnen einer Konsole.

   Im Menü [**Seiteninformationen** können Sie die Option **Hilfe**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#accessing-help) auswählen, um diese Folien jederzeit erneut anzuzeigen.

* **Tools-Konsole**

   Mit der **Tools-Konsole** können Sie auch die externen **Ressourcen** aufrufen:

   * **Dokumentation** –
Dokumentation für Web Experience Management anzeigen
   * **Entwicklungsressourcen** –Entwicklungsressourcen und Downloads

   >[!NOTE]
   >
   >Sie können jederzeit über den Hotkey `?` (Fragezeichen) in einer Konsole auf eine Übersicht der verfügbaren Tastaturbefehle zugreifen.
   >
   >Eine Aufstellung aller Tastaturbefehle finden Sie in den folgenden Dokumenten:
   >
   >* [Tastaturbefehle für die Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/keyboard-shortcuts.md)
   >* [Tastaturbefehle für Konsolen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)


## Aktionssymbolleiste {#actions-toolbar}

Bei der Auswahl einer Ressource (z. B. einer Seite oder eines Assets) werden in der Symbolleiste verschiedene durch Symbole und Text gekennzeichnete Aktionen angezeigt. Diese Aktionen sind abhängig von:

* der aktuellen Konsole
* dem aktuellen Kontext
* ob Sie sich im [Auswahlmodus](#viewing-and-selecting-resources) befinden

In der Symbolleiste werden immer nur jene Aktionen angezeigt, die Sie bei den jeweiligen Elementen durchführen können.

Wie Sie [eine Ressource auswählen](#viewing-and-selecting-resources), hängt von der Ansicht ab.

Aufgrund des eingeschränkten Anzeigebereichs in einigen Fenstern kann die Symbolleiste schnell länger als der verfügbare Platz werden. In diesem Fall werden weitere Optionen angezeigt. Durch Klicken oder Tippen auf die Auslassungspunkte (drei Punkte bzw. **…**) wird eine Dropdown-Auswahl geöffnet, die alle verbleibenden Aktionen enthält. Beispiel: Sie haben eine Seite in der **Sites-Konsole** ausgewählt:

![Zusätzliche Optionen](/help/sites-cloud/authoring/assets/additional-options.png)

>[!NOTE]
>
>Die einzelnen verfügbaren Symbole werden gemäß der/des jeweils zutreffenden Konsole/Funktion/Szenarios dokumentiert.

## Schnellaktionen   {#quick-actions}

In der [Kartenansicht](#card-view) sind bestimmte Aktionen sowohl als Schnellaktionssymbole als auch auf der Symbolleiste vorhanden. Schnellaktionssymbole sind für jeweils ein einzelnes Element verfügbar. Die Notwendigkeit der Vorauswahl entfällt dabei.

Die Schnellaktionen sind sichtbar, wenn Sie die Maus auf eine Ressourcenkarte bewegen (Desktopgerät). Die verfügbaren Schnellaktionen hängen von der Konsole und vom Kontext ab. Dies sind beispielsweise die Schnellaktionen für eine Seite in der **Sites-Konsole**:

![Zusätzliche Optionen](/help/sites-cloud/authoring/assets/quick-actions.png)

## Anzeigen und Auswählen von Ressourcen {#viewing-and-selecting-resources}

Anzeige, Navigation und Auswahl sind grundsätzlich in allen Ansichten gleich. Je nach verwendeter Ansicht kommt es aber zu geringfügigen Abweichungen bei der Verwendung.

Sie können Ressourcen in jeder der verfügbaren Ansichten anzeigen, darin navigieren und sie auswählen (für weitere Aktionen). Die einzelnen Ansichten können Sie mit dem Symbol oben rechts auswählen:

* [Spaltenansicht](#column-view)
* [Kartenansicht](#card-view)
* [Listenansicht](#list-view)

>[!NOTE]
>
>Standardmäßig zeigt AEM Assets in keiner der Ansichten die ursprüngliche Ausgabedarstellung von Assets als Miniaturansicht in der Benutzeroberfläche an. Administratoren können mithilfe von Überlagerungen AEM Assets so konfigurieren, dass ursprüngliche Ausgabedarstellungen als Miniaturen angezeigt werden.

### Auswählen von Ressourcen   {#selecting-resources}

Die Auswahl einer bestimmten Ressource hängt von der Kombination der Ansicht und des Geräts ab:

| Anzeigen | Touch aktivieren | Desktop aktivieren | Touch deaktivieren | Desktop deaktivieren |
|---|---|---|---|---|
| Spalte | Tippen Sie auf die Miniaturansicht | Klicken Sie auf die Miniaturansicht | Tippen Sie auf die Miniaturansicht | Klicken Sie auf die Miniaturansicht |
| Karte | Tippen und halten Sie die Karte | Fahren Sie mit dem Mauszeiger darüber und verwenden Sie dann die Schnellaktion mit Häkchen | Tippen Sie auf die Karte | Klicken Sie auf die Karte |
| Liste | Tippen Sie auf die Miniaturansicht | Klicken Sie auf die Miniaturansicht | Tippen Sie auf die Miniaturansicht | Klicken Sie auf die Miniaturansicht |

#### Alle auswählen {#select-all}

Sie können alle Elemente in einer Ansicht auswählen, indem Sie in der oberen rechten Ecke der Konsole auf die Option **Alles auswählen** klicken.

* In der **Kartenansicht** sind alle Karten ausgewählt.
* In der **Listenansicht** sind alle Elemente in der Liste ausgewählt.
* In der **Spaltenansicht** sind alle Elemente in der Spalte ganz links ausgewählt.

![Alle auswählen](/help/sites-cloud/authoring/assets/select-all.png)

#### Gesamte Auswahl aufheben {#deselecting-all}

In allen Fällen wird die Anzahl der ausgewählten Elemente in der rechten oberen Ecke der Symbolleiste angezeigt.

Sie können wie folgt die Auswahl aller Elemente aufheben und den Auswahlmodus beenden:

* Klicken oder tippen Sie auf das **X** neben der Anzahl,
* verwenden Sie die **Esc**-Taste oder nutzen Sie

![Gesamte Auswahl aufheben](/help/sites-cloud/authoring/assets/deselect-all.png).

In allen Ansichten kann die Auswahl aller Elemente aufgehoben werden, indem Sie die Esc-Taste auf der Tastatur drücken, wenn Sie ein Desktop-Gerät verwenden.

#### Auswahlbeispiel {#selecting-example}

1. Beispiel für die Kartenansicht:

   ![Auswahl von Kartenansicht](/help/sites-cloud/authoring/assets/card-view-select.png)

1. Nach Auswahl einer Ressource wird die obere Kopfzeile von der [Aktionssymbolleiste](#actions-toolbar) überdeckt, die Zugriff auf die Aktionen bietet, die für die ausgewählte Ressource verfügbar sind.

   Um den Auswahlmodus zu beenden, wählen Sie das **X** in der rechten oberen Ecke oder drücken Sie die **Esc-Taste**.

### Spaltenansicht {#column-view}

![Spaltenansicht](/help/sites-cloud/authoring/assets/column-view.png)

Die Spaltenansicht ermöglicht die Navigation durch einen Inhaltsbaum über mehrere untergeordnete Spalten. Mit dieser Ansicht können Sie die Baumstruktur Ihrer Website visualisieren und durchlaufen.

Durch die Auswahl einer Ressource in der Spalte ganz links werden die untergeordneten Ressourcen in einer Spalte rechts angezeigt. Wird eine Ressource in der rechten Spalte ausgewählt, werden die untergeordneten Ressourcen in einer weiteren Spalte rechts angezeigt usw.

* Sie können im Baum nach oben und unten navigieren, indem Sie auf einen Ressourcennamen oder den Pfeil rechts vom Ressourcennamen tippen oder klicken.

   * Beim Tippen bzw. Klicken werden Ressourcenname und Pfeil hervorgehoben.
   * Die untergeordneten Elemente der ausgewählten Ressource werden in der Spalte rechts neben der Ressource angezeigt.
   * Wenn Sie auf einen Ressourcennamen tippen oder klicken, der keine untergeordneten Elemente besitzt, werden die Ressourcendetails in der letzten Spalte angezeigt.

* Durch Tippen oder Klicken auf die Miniaturansicht wird die Ressource ausgewählt.

   * Dann erscheint ein Häkchen auf der Miniaturansicht und der Ressourcenname wird hervorgehoben dargestellt.
   * Die Details der ausgewählten Ressource werden in der letzten Spalte angezeigt.
   * Die Aktionssymbolleiste wird verfügbar.

   Wenn eine Seite in der Spaltenansicht ausgewählt wird, wird sie zusammen mit den folgenden Details in der letzten Spalte angezeigt:

   * Seitentitel
   * Seitenname (Teil der URL der Seite)
   * Vorlage, auf der die Seite basiert
   * Änderungsdetails
   * Sprache der Seite
   * Veröffentlichungsdetails


### Kartenansicht {#card-view}

![Kartenansicht](/help/sites-cloud/authoring/assets/card-view.png)

* In der Kartenansicht werden Informationskarten für jedes Element auf der aktuellen Ebene angezeigt. Diese bieten u. a. folgende Informationen:

   * eine visuelle Darstellung des Seiteninhalts
   * den Seitentitel
   * wichtige Daten (z. B. zuletzt bearbeitet, zuletzt veröffentlicht)
   * ob die Seite gesperrt, ausgeblendet oder Teil einer Live Copy ist
   * wann Sie im Zuge eines Workflows eine Aktion ausführen müssen (sofern zutreffend)
      * Markierungen, die auf erforderliche Aktionen hinweisen, können mit Einträgen in Ihrem [Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md) verknüpft werden.

* In dieser Ansicht sind auch [Schnellaktionen](#quick-actions) sowie die Auswahlfunktion und allgemeine Aktionen wie „Bearbeiten“ verfügbar.

   ![Schnellaktionen](/help/sites-cloud/authoring/assets/quick-actions.png)

* Sie können in der Struktur nach unten navigieren, indem Sie auf die Karten tippen/klicken (vermeiden Sie dabei die Schnellaktionen), und über die [Breadcrumbs in der Kopfzeile](#the-header) wieder nach oben navigieren.

### Listenansicht {#list-view}

![Listenansicht](/help/sites-cloud/authoring/assets/list-view.png)

* In der Listenansicht werden Informationen für jede Ressource auf der aktuellen Ebene aufgelistet.
* Sie können in der Struktur nach unten navigieren, indem Sie auf den Ressourcennamen tippen/klicken, und über die [Breadcrumbs in der Kopfzeile](#the-header) wieder nach oben navigieren.
* Um alle Elemente in der Liste auszuwählen, verwenden Sie das Kontrollkästchen links oben in der Liste.

   ![Gesamte Listenansicht auswählen](/help/sites-cloud/authoring/assets/list-view-select-all.png)

   * Wenn alle Elemente in der Liste ausgewählt wurden, ist dieses Kontrollkästchen aktiviert.

      * Klicken bzw. tippen Sie auf das Kontrollkästchen, um die Auswahl wieder aufzuheben.
   * Wurden nur einige Elemente ausgewählt, wird es mit einem Minuszeichen dargestellt.

      * Klicken bzw. tippen Sie auf das Kontrollkästchen, um alle auszuwählen.
      * Durch abermaliges Klicken oder Tippen auf das Kontrollkästchen heben Sie die Auswahl wieder auf.


* Wählen Sie mit der Option **Ansichtseinstellungen** unter der Schaltfläche „Ansichten“ die Spalten aus, die angezeigt werden sollen. Die folgenden Spalten können angezeigt werden:

   * **Name** – Seitenname, der in einer mehrsprachigen Autorenumgebung nützlich sein kann, da er Teil der Seiten-URL ist und unabhängig von der Sprache gleich bleibt
   * **Geändert** – Datum der letzten Änderung und der Benutzer, der die Änderung vorgenommen hat
   * **Veröffentlicht** – Veröffentlichungsstatus
   * **Vorlage** – Vorlage, auf der die Seite basiert
   * **Workflow** - Workflow, der derzeit auf die Seite angewendet ist. Weitere Informationen sind verfügbar, wenn Sie die Maus darauf bewegen oder die Zeitleiste öffnen.
   * **Seitenanalyse**
   * **Individuelle Besucher**
   * **Zeit auf Seite**

      ![Spalten auswählen](/help/sites-cloud/authoring/assets/select-columns.png)
   Standardmäßig wird die Spalte **Name** angezeigt, die Teil der URL der Seite ist. Unter Umständen muss der Autor auf Seiten zugreifen, die in einer anderen Sprache verfasst sind. In diesem Fall ist die Anzeige des Seitennamens (der sich normalerweise nicht ändert) äußerst hilfreich, wenn der Autor die Sprache der Seite nicht kennt.

* Ändern Sie die Reihenfolge der Elemente mithilfe des vertikalen gepunkteten Balkens am rechten Rand jedes Elements.

   >[!NOTE]
   >
   >Das Ändern der Reihenfolge funktioniert nur innerhalb eines sortierten Ordners, der den Wert `jcr:primaryType` als `sling:OrderedFolder` hat.

   ![Spaltenreihenfolge](/help/sites-cloud/authoring/assets/column-order.png)

   Klicken oder tippen Sie auf die vertikale Auswahlleiste und ziehen Sie das Element an die gewünschte Position in der Liste.

   ![Bestellliste](/help/sites-cloud/authoring/assets/order-list.png)

## Schienenauswahl {#rail-selector}

Die **Schienenauswahl** befindet sich im Fenster oben links. Je nach Konsole stehen unterschiedliche Optionen zur Verfügung.

![Schienenauswahl erweitert](/help/sites-cloud/authoring/assets/rail-selector-expanded.png)

So können Sie z. B. in **Sites** nur Inhalt (Standard), die Inhaltsstruktur, die Zeitleiste, Verweise oder das seitliche Bedienfeld „Filter“ auswählen.

Wenn „Nur Inhalt“ ausgewählt ist, wird lediglich das Schienensymbol angezeigt. Bei Auswahl einer anderen Option wird der Optionsname neben dem Schienensymbol angezeigt.

>[!NOTE]
>
>[Tastaturbefehle](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) sind verfügbar, um schnell zwischen Optionen zur Schienenanzeige wechseln zu können.

### Inhaltsstruktur {#content-tree}

Über die Inhaltsstruktur können Benutzer im seitlichen Bedienfeld schnell in der Website-Hierarchie navigieren und eine Vielzahl von Informationen zu den Seiten im aktuellen Ordner anzeigen.

Mit dem seitlichen Bedienfeld der Inhaltsstruktur und einer Listen- oder Kartenansicht können Benutzer die hierarchische Struktur von Projekten problemlos einsehen. Außerdem können sie mit dem seitlichen Bedienfeld der Inhaltsstruktur in der gesamten Inhaltsstruktur navigieren sowie ausführliche Seiteninformationen in der Listenansicht aufrufen.

![Inhaltsstruktur](/help/sites-cloud/authoring/assets/content-tree.png)

>[!NOTE]
>
>Sobald ein Eintrag in der Hierarchieansicht ausgewählt wurde, kann mit den Pfeiltasten schnell in der Hierarchie navigiert werden.
>
>Weitere Informationen finden Sie unter [Tastaturbefehle](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md).

### Zeitleiste {#timeline}

Die Zeitleiste kann zur Anzeige und/oder Einleitung von Ereignissen in Verbindung mit der ausgewählten Ressource verwendet werden. Öffnen Sie die Zeitleisten-Spalte über die Schienenauswahl:

![Zeitleisten-Struktur](/help/sites-cloud/authoring/assets/timeline.png)

Die Zeitleisten-Spalte bietet folgende Möglichkeiten:

* Anzeigen verschiedener Ereignisse im Zusammenhang mit einem ausgewählten Element

   * Sie können die Ereignistypen in der Dropdown-Liste auswählen:

      * Kommentare
      * [Anmerkungen](/help/sites-cloud/authoring/fundamentals/annotations.md)
      * [Aktivitäten](/help/sites-cloud/authoring/personalization/activities.md)
      * [Launches](/help/sites-cloud/authoring/launches/overview.md)
      * [Versionen](/help/sites-cloud/authoring/features/page-versions.md)
      * [Workflows](/help/sites-cloud/authoring/workflows/overview.md)
         * mit Ausnahme von Übergangs-Workflows, da keine Verlaufsinformationen für diese gespeichert werden <!--With the exception of [transient workflows](/help/sites-developing/workflows.md#transient-workflows) as no history information is saved for these-->
      * Alles anzeigen

* Hinzufügen/Anzeigen von Kommentaren zum gewählten Element Das Feld **Kommentare** wird unten in der Ereignisliste angezeigt. Wenn Sie einen Kommentar eingeben (und anschließend die Eingabetaste drücken), wird der Kommentar registriert. Er wird angezeigt, wenn **Kommentare** oder **Alle anzeigen** ausgewählt wird.

* Einige Konsolen weisen weitere Funktionalitäten auf. So können Sie z. B. in der Sites-Konsole

   * [eine Version speichern](/help/sites-cloud/authoring/features/page-versions.md)
   * [einen Workflow starten](/help/sites-cloud/authoring/workflows/applying.md)

Diese Optionen sind über den Pfeil neben dem **Kommentarfeld** aufrufbar.

![Kommentarfeld](/help/sites-cloud/authoring/assets/comments.png)

### Verweise {#references}

**Verweise** zeigen sämtliche Verbindungen zur ausgewählten Ressource. Beispiel: In der **Sites-Konsole** wird in den [Verweisen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#references) für Seiten Folgendes angezeigt:

* [Starts](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)
* Live Copies<!--[Live copies](/help/sites-administering/msm-livecopy-overview.md#openingthelivecopyoverviewfromreferences)-->
* Sprachkopien<!--[Language copies](/help/sites-administering/tc-prep.md#seeing-the-status-of-language-roots)-->
* Inhaltsverweise:

   * Links von anderen Seiten zur ausgewählten Seite
   * Inhalt, der von ausgewählten Seiten durch die Referenzkomponente geliehen oder verliehen wird

![Beispiel für Verweise](/help/sites-cloud/authoring/assets/references-example.png)

### Filter {#filter}

Hierdurch wird ein dem [Suchbereich](/help/sites-cloud/authoring/getting-started/search.md) ähnliches Fenster mit bereits entsprechend eingestellten Ortsfiltern geöffnet. So können Sie den für die Anzeige gewünschten Inhalt weiter filtern.

![Filterbeispiel](/help/sites-cloud/authoring/assets/filter.png)
