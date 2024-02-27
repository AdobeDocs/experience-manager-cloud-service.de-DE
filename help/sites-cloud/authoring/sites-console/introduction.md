---
title: Die Sites-Konsole
description: Erfahren Sie, wie Sie mit der Sites-Konsole Ihre AEM verwalten und organisieren können.
source-git-commit: 91ce6a0c880436327f4dd333a2eb3d36a4e89a4d
workflow-type: tm+mt
source-wordcount: '1628'
ht-degree: 49%

---


# Die Sites-Konsole {#sites-console}

Erfahren Sie, wie Sie die **Sites** -Konsole, um Ihre AEM zu verwalten und zu ordnen.

## Ausrichtung {#orientation}

Die **Sites** -Konsole können Sie Ihre Seitenhierarchie anzeigen.

![Spaltenansicht der Sites-Konsole mit einem ausgewählten Element](assets/sites-console-column-view-selected.png)

Es bietet verschiedene Ansichten und Symbolleisten, mit denen Sie Ihre Seiten verwalten und organisieren können.

* [Symbolleiste der Konsole](#toolbar) ist immer vorhanden, um Ihnen bei der Navigation zu helfen.
* [Drei verschiedene Ansichten](#views) können Sie Ihre Seite einfach finden und auswählen.
* [Symbolleiste der Aktion](#action-toolbar) angezeigt, wenn Sie ein Element ausgewählt haben, das bearbeitet werden soll.
* [Seitenbereich](#side-panel) verfügt über mehrere Optionen zum Anzeigen detaillierter Informationen auf einer ausgewählten Seite.

## Symbolleiste der Konsole {#console-toolbar}

Die Konsolen-Symbolleiste befindet sich immer in der Konsole und hilft Ihnen, sich in Ihren Inhalt zu orientieren und in den Inhalt zu navigieren.

![Die Symbolleiste der Sites-Konsole](assets/sites-console-toolbar.png)

### Seitenbereich-Auswahl {#side-panel-selector}

Mit der Seitenbereichsauswahl können Sie zusätzliche Informationen zum ausgewählten Element in der Konsole anzeigen.

![Schaltfläche für Seitenbereichsauswahl](assets/sites-console-side-panel-button.png)

Die angezeigten Optionen hängen von der jeweiligen Konsole ab. So können Sie z. B. in **Sites** nur Inhalt (Standard), die Zeitleiste, Verweise oder das seitliche Bedienfeld „Filter“ auswählen.

![Beispiel für eine Seitenbereichsauswahl](assets/sites-console-side-panel-selector.png)

Weitere Informationen zum seitlichen Bedienfeld finden Sie im Dokument [Seitenbereich der Sites-Konsole.](/help/sites-cloud/authoring/sites-console/console-side-panel.md)

### Breadcrumbs {#breadcrumbs}

Die Breadcrumbs befinden sich immer in der Mitte der Leiste und zeigen die Beschreibung des aktuell ausgewählten Elements an. Sie ermöglichen es Ihnen, durch die Ebenen Ihrer Website zu navigieren.

![Breadcrumbs in der Navigationsleiste](assets/sites-console-breadcrumbs-navigation.png)


Tippen oder klicken Sie auf den Breadcrumb-Text, um eine Dropdown-Liste mit den Hierarchieebenen des aktuell ausgewählten Elements anzuzeigen. Tippen oder klicken Sie auf einen Eintrag, um zu diesem Speicherort zu springen.

![Beispiel für Breadcrumbs (erweitert)](assets/sites-console-breadcrumbs-example.png)

### Alle auswählen {#select-all}

Tippen oder klicken Sie auf **Alle auswählen** -Schaltfläche ausgewählt alle Elemente in der aktuellen Ansicht der Konsole.

![Schaltfläche &quot;Alle auswählen&quot;](assets/sites-console-select-all.png)

Wenn Sie alle Elemente ausgewählt haben, wird die Anzahl der ausgewählten Elemente oben rechts in der Symbolleiste angezeigt, wobei die **Alle auswählen** angezeigt.

Sie können wie folgt die Auswahl aller Elemente aufheben und den Auswahlmodus beenden:

* Klicken oder tippen Sie auf **X** neben der Anzahl.
* Verwenden der **escape** Schlüssel.

![Gesamte Auswahl aufheben](assets/sites-console-deselect-all.png).

### Schaltfläche „Erstellen“ {#create-button}

Die **Erstellen** -Schaltfläche können Sie neue Seiten zu Ihrer Site hinzufügen und zusätzliche Sites-Objekte wie Live Copies oder Launches erstellen.

![Schaltfläche „Erstellen“](assets/sites-console-create.png)

Nach dem Klicken passen die angezeigten Optionen zur Konsole/zum Kontext. Die häufigsten sind:

* [Page](/help/sites-cloud/authoring/sites-console/creating-pages.md)
* [Site](/help/sites-cloud/administering/site-creation/create-site.md)
* [Live Copy](/help/sites-cloud/administering/msm/overview.md)
* [Launch](/help/sites-cloud/authoring/launches/overview.md)
* [Sprachkopie](/help/sites-cloud/administering/translation/overview.md)
* [CSV-Bericht](/help/sites-cloud/authoring/sites-console/csv-export.md)

Weitere Informationen zur Funktionsweise finden Sie unter den Links zu diesen Funktionen .

## Anzeigen und Auswählen von Seiten {#views}

Die **Sites** -Konsole bietet drei verschiedene Ansichten Ihrer Inhaltshierarchie. Sie können Ihre Ressourcen in einer der verfügbaren Ansichten anzeigen, durch sie navigieren und sie auswählen (für weitere Aktionen).

* [Spaltenansicht](#column-view)
* [Kartenansicht](#card-view)
* [Listenansicht](#list-view)

Die **Ansicht** rechts neben der AEM-Symbolleiste die aktuell ausgewählte Ansicht.

Durch Tippen oder Klicken darauf können Sie eine andere Ansicht auswählen.

![Schaltfläche „Ansichten“](assets/sites-console-views-button.png)

Sie können zwischen der Spalten-, Karten- und Listenansicht wechseln; in der Listenansicht werden auch die Ansichtseinstellungen angezeigt.

![Ansichten](assets/sites-console-view.png)

>[!NOTE]
>
>Die Option **Ansichtseinstellungen** steht nur im Modus **Listenansicht** zur Verfügung.

Anzeige, Navigation und Auswahl sind grundsätzlich in allen Ansichten gleich. Je nach verwendeter Ansicht kommt es aber zu geringfügigen Abweichungen bei der Verwendung.

>[!NOTE]
>
>Standardmäßig zeigt AEM Assets in keiner der Ansichten die ursprüngliche Ausgabedarstellung von Assets als Miniatur in der Benutzeroberfläche an. Administratoren können mithilfe von Überlagerungen AEM Assets so konfigurieren, dass ursprüngliche Ausgabedarstellungen als Miniaturen angezeigt werden.

### Auswählen von Ressourcen {#selecting-resources}

Die Auswahl einer bestimmten Ressource hängt von der Kombination der Ansicht und des Geräts ab:

| Anzeigen | Touch aktivieren | Desktop aktivieren | Touch deaktivieren | Desktop deaktivieren |
|---|---|---|---|---|
| Spalte | Auswählen der Miniaturansicht | Klicken Sie auf die Miniatur | Auswählen der Miniaturansicht | Klicken Sie auf die Miniatur |
| Karte | Karte auswählen und halten | Fahren Sie mit dem Mauszeiger darüber und verwenden Sie dann die Schnellaktion mit Häkchen | Auswählen der Karte | Klicken Sie auf die Karte |
| Liste | Auswählen der Miniaturansicht | Klicken Sie auf die Miniatur | Auswählen der Miniaturansicht | Klicken Sie auf die Miniatur |

#### Auswahlbeispiel {#selecting-example}

1. Beispiel für die Kartenansicht:

   ![Auswahl von Kartenansicht](assets/sites-console-card-view-select.png)

1. Nach Auswahl einer Ressource wird die obere Kopfzeile von der [Aktionssymbolleiste](#actions-toolbar) überdeckt, die Zugriff auf die Aktionen bietet, die für die ausgewählte Ressource verfügbar sind.

1. Um den Auswahlmodus zu beenden, wählen Sie das **X** in der rechten oberen Ecke oder drücken Sie die **Esc-Taste**.

### Spaltenansicht {#column-view}

Die Spaltenansicht ermöglicht die visuelle Navigation eines Inhaltsbaums durch eine Reihe kaskadierender Spalten. Mit dieser Ansicht können Sie die Baumstruktur Ihrer Website visualisieren und durchlaufen.

![Spaltenansicht](assets/sites-console-column-view.png)

Wenn Sie eine Ressource in der Spalte ganz links auswählen, werden die untergeordneten Ressourcen in einer Spalte rechts angezeigt. Wenn Sie eine Ressource in der rechten Spalte auswählen, werden die ihr untergeordneten Ressourcen in einer anderen Spalte rechts angezeigt usw.

* Sie können in der Baumstruktur nach oben und unten navigieren, indem Sie auf den Ressourcennamen oder den Pfeil rechts neben dem Ressourcennamen tippen/klicken.

   * Beim Tippen bzw. Klicken werden der Ressourcenname und der Pfeil hervorgehoben.
   * Die untergeordneten Elemente der angeklickten/angetippten Ressource werden in der Spalte rechts neben der angeklickten/angetippten Ressource angezeigt.
   * Wenn Sie einen Ressourcennamen auswählen, der keine untergeordneten Elemente besitzt, werden die Ressourcendetails in der letzten Spalte angezeigt.

* Durch Tippen oder Klicken auf die Miniaturansicht wird die Ressource ausgewählt.

   * Wenn diese Option ausgewählt ist, wird ein Häkchen auf der Miniaturansicht angezeigt und zudem wird der Ressourcenname hervorgehoben.
   * Die Details der ausgewählten Ressource werden in der letzten Spalte angezeigt.
   * Die Aktionssymbolleiste wird verfügbar.

* Wenn eine Seite in der Spaltenansicht ausgewählt wird, wird die ausgewählte Seite in der letzten Spalte zusammen mit den folgenden Details angezeigt:

   * Seitentitel
   * Seitenname (Teil der URL der Seite)
   * Vorlage, auf der die Seite basiert
   * Änderungsdetails
   * Sprache der Seite
   * Veröffentlichen und Vorschau von Details

### Kartenansicht {#card-view}

In der Kartenansicht wird jedes Element auf der aktuellen Hierarchieebene als große Karte angezeigt.

![Kartenansicht](assets/sites-console-card-view.png)

* Die Karten enthalten Informationen wie:

   * eine visuelle Darstellung des Seiteninhalts
   * den Seitentitel
   * wichtige Daten (z. B. zuletzt bearbeitet, zuletzt veröffentlicht)
   * Wenn die Seite gesperrt, ausgeblendet oder Teil einer Live Copy ist.
   * Gibt an, ob Sie das Element im Rahmen eines Workflows bearbeiten müssen.

Kartenansicht bietet auch [Schnellaktionen](#quick-actions) für die Elemente wie Auswahl und allgemeine Aktionen wie Bearbeiten.

![Schnellaktionen](assets/sites-console-quick-actions.png)

Sie können in der Struktur nach unten navigieren, indem Sie auf die Karten tippen/klicken (vermeiden Sie dabei, auf die Schnellaktionen zu tippen), und über die [Breadcrumbs in der Kopfzeile](#the-header).

### Listenansicht {#list-view}

Die Listenansicht bietet Informationen zu den einzelnen Ressourcen auf der aktuellen Ebene in einer Liste.

![Listenansicht](assets/sites-console-list-view.png)

* Sie können in der Struktur nach unten navigieren, indem Sie auf den Ressourcennamen tippen/klicken, und über die [Breadcrumbs in der Kopfzeile](#the-header) wieder nach oben navigieren.
* Um alle Elemente in der Liste einfach auszuwählen, verwenden Sie die [**Alle auswählen** in der Symbolleiste.](#select-all)

* Wählen Sie mit der Option **Ansichtseinstellungen** unter der Schaltfläche „Ansichten“ die Spalten aus, die angezeigt werden sollen. Die folgenden Spalten stehen zur Anzeige zur Verfügung:

   * **Name** – Seitenname, der in einer mehrsprachigen Authoring-Umgebung nützlich sein kann, da er Teil der URL der Seite ist und sich unabhängig von der Sprache nicht ändert
   * **Geändert** – Datum und Person der letzten Änderung
   * **Veröffentlicht** – Veröffentlichungsstatus
   * **Vorschau** – Vorschaustatus
   * **Vorlage** – Vorlage, auf der die Seite basiert
   * **Vorgang**
   * **Workflow** – Workflow, der derzeit auf die Seite angewendet ist. Weitere Informationen sind verfügbar, wenn Sie die Maus darüber bewegen oder die Timeline öffnen.
   * **Übersetzt**
   * **Seitenansichten**
   * **Unique Visitors**
   * **Besuchszeit pro Seite**

![Konfigurieren der Spalten](assets/sites-console-select-columns.png)

Standardmäßig wird die Spalte **Name** angezeigt, die Teil der URL der Seite ist. Unter Umständen muss der Autor auf Seiten zugreifen, die in einer anderen Sprache verfasst sind. In diesem Fall ist die Anzeige des Seitennamens (der sich normalerweise nicht ändert) äußerst hilfreich, wenn der Autor die Sprache der Seite nicht kennt.

* Ändern Sie die Reihenfolge der Elemente mithilfe des vertikalen gepunkteten Balkens am rechten Rand jedes Elements.

![Spaltenreihenfolge](assets/sites-console-column-order.png)

Wählen Sie die vertikale Auswahlleiste aus und ziehen Sie das Element an eine neue Position in der Liste.

![Liste sortieren](assets/sites-console-order-list.png)

>[!NOTE]
>
>Das Ändern der Reihenfolge funktioniert nur innerhalb eines sortierten Ordners, der den Wert `jcr:primaryType` als `sling:OrderedFolder` hat.

## Aktionssymbolleiste {#actions-toolbar}

Bei jeder Auswahl einer Ressource können Sie verschiedene Aktionen für das ausgewählte Element ausführen. Diese Aktionen werden in der Aktionssymbolleiste angezeigt.

![Aktionen-Symbolleiste](assets/introduction-actions-toolbar.png)

Die Aktionssymbolleiste wird nur angezeigt, wenn eine Ressource in der Konsole ausgewählt ist. Die in der Aktionssymbolleiste verfügbare Aktion ändert sich entsprechend den Aktionen, die Sie für die ausgewählten Elemente ausführen können. Die häufigsten Aktionen sind:

* [**Erstellen**](#create-action) - Erstellen neuer Inhalte oder inhaltsbezogener Aktionen
* **Bearbeiten** - Je nachdem, wie die ausgewählte Seite erstellt wurde, wird die **Bearbeiten** -Aktion öffnet den entsprechenden Editor.
   * [Seiten-Editor](/help/sites-cloud/authoring/page-editor/introduction.md) - Für Seiten, die mit dem AEM Seiten-Editor erstellt wurden
   * [Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) - Für mit dem Universal Editor erstellte Seiten
* [**Eigenschaften**](/help/sites-cloud/authoring/sites-console/page-properties.md) - Öffnet das Fenster &quot;Seiteneigenschaften&quot;.
* [**Sperren**](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page) - Sperren einer Seite, um zu verhindern, dass andere sie ändern
* [**Kopieren**](/help/sites-cloud/authoring/sites-console/managing-pages.md#copying-and-pasting-a-page) - Eine Seite kopieren
* [**Verschieben**](/help/sites-cloud/authoring/sites-console/managing-pages.md#moving-or-renaming-a-page) - Verschieben oder Umbenennen einer Seite
* [**Quick Publish**](/help/sites-cloud/authoring/sites-console/publishing-pages.md#quick-publish) - Sofortiges Veröffentlichen von Seiten
* [**Veröffentlichung verwalten**](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication) - Eine oder mehrere Seiten für die Veröffentlichung planen
* [**Wiederherstellen**](/help/sites-cloud/authoring/sites-console/page-versions.md#restore-version) - Wiederherstellen einer Version einer Seite oder eines Seitenbaums
* [**Löschen**](/help/sites-cloud/authoring/sites-console/managing-pages.md#deleting-a-page) - Löschen von Seiten

Aufgrund des eingeschränkten Anzeigebereichs in einigen Fenstern kann die Symbolleiste schnell länger als der verfügbare Platz werden. In diesem Fall werden weitere Optionen angezeigt. Klicken oder tippen Sie auf die Auslassungspunkte (die drei Punkte oder **...**) öffnet eine Dropdown-Auswahl, die alle verbleibenden Aktionen enthält.

![Zusätzliche Optionen](assets/sites-console-additional-options.png)

### Aktion erstellen {#create-action}

Die Erstellungsaktion bietet ähnliche Optionen wie die [**Erstellen** Symbolleistenschaltfläche](#create-button) zum Erstellen neuer Seiten und ähnlicher Elemente.

Darüber hinaus bietet es die Möglichkeit, seitenbezogene Aktionen zu erstellen.

* [**Workflow**](/help/sites-cloud/authoring/workflows/overview.md) - Anwenden eines Workflows auf eine Seite
* [**Version**](/help/sites-cloud/authoring/sites-console/page-versions.md) - Erstellen einer Seitenversion

## Vorlagen

Durch Auswählen der Seite in der [**Spaltenansicht**](/help/sites-cloud/authoring/basic-handling.md#column-view) oder [**Listenansicht**](/help/sites-cloud/authoring/basic-handling.md#list-view) können Sie schnell und einfach feststellen, auf welcher Vorlage die Seite basiert.
