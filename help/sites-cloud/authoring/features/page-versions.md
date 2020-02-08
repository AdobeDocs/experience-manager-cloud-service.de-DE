---
title: Arbeiten mit Seitenversionen
description: Sie können verschiedene Versionen einer Seite erstellen, vergleichen und wiederherstellen.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Arbeiten mit Seitenversionen {#working-with-page-versions}

Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung sind die folgenden Aktionen verfügbar:

* Erstellen einer Version einer Seite
* Wiederherstellen einer früheren Seitenversion, um z. B. eine Änderung rückgängig zu machen
* Vergleichen der aktuellen Version einer Seite mit einer früheren Version, wobei die Unterschiede in Text und Bildern hervorgehoben sind

## Erstellen einer neuen Version {#creating-a-new-version}

Sie können eine Version Ihrer Ressource folgendermaßen erstellen:

* The [Timeline rail](#creating-a-new-version-timeline)
* The [Create](#creating-a-new-version-create-with-a-selected-resource) option (when a resource is selected)

### Creating a New Version - Timeline {#creating-a-new-version-timeline}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Open the **Timeline** rail.
1. Klicken/tippen Sie auf das Auslassungszeichen durch das Kommentarfeld, um die Optionen anzuzeigen:

   ![Versionen in der Zeitschiene](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. Wählen Sie **Als Version speichern**.
1. Geben Sie ein **Etikett** an und ggf. einen **Kommentar** ein.

   ![Beschriftung für eine Version hinzufügen](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

   Die Informationen in der Timeline werden entsprechend der neuen Version aktualisiert.

### Creating a New Version - Create with a Selected Resource {#creating-a-new-version-create-with-a-selected-resource}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Wählen Sie in der Symbolleiste die Option **Erstellen**.
1. Das gleiche Dialogfeld wird geöffnet. Sie können ein **Etikett** angeben und ggf. einen **Kommentar** eingeben.
1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

Die Informationen in der Timeline werden entsprechend der neuen Version aktualisiert. 

## Wiederherstellen einer früheren Seitenversion {#reverting-to-a-page-version}

Nachdem eine Version erstellt wurde, können Sie diese Version bei Bedarf wiederherstellen.

>[!NOTE]
>
>Wenn eine Seite wiederhergestellt wird, gehört die erstellte Version zu einem neuen Zweig.
>
>Beispiel:
>
>1. Erstellen Sie Versionen einer beliebigen Seite.
>1. Die anfänglichen Etiketten und Versionsknotennamen lauten 1.0, 1.1, 1.2 usw.
>1. Stellen Sie die erste Version wieder her, d. h. Version 1.0.
>1. Erstellen Sie weitere neue Versionen.
>1. Die erzeugten Etiketten und Knotennamen lauten jetzt 1.0.0, 1.0.1, 1.0.2 usw.


So stellen Sie eine frühere Version wieder her:

1. Navigieren Sie zu der Seite, für die Sie eine frühere Version wiederherstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die Spalte **Timeline** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus. Die Seitenversionen für die ausgewählte Seite werden aufgeführt.
1. Wählen Sie die Version, die Sie wiederherstellen möchten. Die möglichen Optionen werden angezeigt:

   ![Version wiederherstellen](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Auf diese Version zurücksetzen**. Die ausgewählte Version wird wiederhergestellt und die Informationen in der Timeline werden aktualisiert.

## Vorschau einer Version {#previewing-a-version}

Sie können eine Vorschau einer bestimmten Version anzeigen:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die Spalte **Timeline** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgeführt. Wählen Sie die Version, deren Vorschau Sie anzeigen möchten:

   ![Vorschau](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Vorschau**. Die Seite wird auf einer neuen Registerkarte angezeigt.

   >[!CAUTION]
   >
   >Wenn eine Seite verschoben wurde, können Sie keine Vorschau von Versionen mehr anzeigen, die vor dem Verschieben erstellt wurden.
   >
   >Wenn Probleme bei der Vorschau auftreten, überprüfen Sie in der [Timeline](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

## Vergleichen einer Version mit der aktuellen Seite {#comparing-a-version-with-current-page}

So vergleichen Sie eine frühere Version mit der aktuellen Seite:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die Spalte **Timeline** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgeführt. Wählen Sie die Version, die Sie vergleichen möchten:

   ![Versionen vergleichen](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Mit akt. Version vergleichen** aus. Die Seite [Differenz](/help/sites-cloud/authoring/features/page-diff.md) wird geöffnet. Sie enthält alle vorhandenen Unterschiede.

## Timewarp {#timewarp}

Timewarp ist eine Funktion, die den *Veröffentlichungsstatus* einer Seite zu einer bestimmten Zeit in der Vergangenheit simuliert.

Da es sich bei der Inhaltserstellung um einen fortlaufenden und gemeinschaftlichen Prozess handelt, besteht der Zweck von Timewarp darin, Autoren zu ermöglichen, die veröffentlichte Website im Laufe der Zeit zu verfolgen, um zu verstehen, wie sich der Inhalt verändert hat. Diese Funktion verwendet die Seitenversionen, um den Status der Veröffentlichungsumgebung zu bestimmen.

Gehen Sie hierfür wie folgt vor:

* Das System sucht die Seitenversion, die zum gewählten Zeitpunkt aktiv war.
* Dies bedeutet, dass die angezeigte Version *vor* dem in Timewarp ausgewählten Zeitpunkt erstellt/aktiviert wurde.
* Wenn Sie zu einer gelöschten Seite navigieren, wird diese auch gerendert - solange die alten Versionen der Seite noch im Repository verfügbar sind.
* Wenn keine veröffentlichte Version gefunden wird, kehrt Timewarp zum aktuellen Status der Seite in der Autorenumgebung zurück (dadurch wird eine Fehler-/404-Seite vermieden, die dazu führen würde, dass Sie nicht weiterbrowsen können).

### Verwenden von Timewarp {#using-timewarp}

Timewarp ist ein [Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) des Seiteneditors. Um ihn zu starten, aktivieren Sie ihn einfach wie jeden anderen Modus.

1. Starten Sie den Editor für die Seite, auf der Timewarp ausgeführt werden soll, und wählen Sie in der Modusauswahl **Timewarp**.

   ![Zeitwarp-Modus](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. Legen Sie im Dialogfeld das gewünschte Datum und die Uhrzeit fest und klicken oder tippen Sie auf **Datum einstellen**. Wenn Sie keine Zeit auswählen, wird standardmäßig die aktuelle Zeit verwendet.

   ![Zieldatum für Zeitverkrümmung](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. Die Seite wird entsprechend dem eingestellten Datum angezeigt. Der Timewarp-Modus ist durch die blaue Statusleiste am oberen Fensterrand gekennzeichnet. Verwenden Sie die Links in der Statusleiste, um ein neues Datum auszuwählen oder den Timewarp-Modus zu beenden.

   ![Im Zeitwarp-Modus](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### Timewarp-Beschränkungen {#timewarp-limitations}

Timewarp versucht, eine Seite zu einem bestimmten Zeitpunkt zu reproduzieren. Aufgrund der Komplexität des kontinuierlichen Authoring von Inhalten in AEM ist dies jedoch nicht immer möglich. Diese Einschränkungen sollten bei der Verwendung von Timewarp beachtet werden.

* **Timewarp funktioniert auf veröffentlichten Seiten** - Timewarp funktioniert nur dann vollständig, wenn Sie die Seite bereits veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung.
* **&quot;Zeitverkrümmung&quot;verwendet Seitenversionen** - Wenn Sie zu einer Seite navigieren, die aus dem Repository entfernt/gelöscht wurde, wird sie korrekt wiedergegeben, wenn ältere Versionen der Seite noch im Repository verfügbar sind.
* **Entfernte Versionen wirken sich auf Zeitwarp** aus - Wenn Versionen aus dem Repository entfernt werden, kann Timewarp nicht die richtige Ansicht anzeigen.
* **Zeitwarp ist schreibgeschützt** - Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen möchten, müssen Sie dies über [Wiederherstellen](#reverting-to-a-page-version) manuell ausführen.
* **Timewarp basiert nur auf Seiteninhalt** - Wenn Elemente (wie Code, CSS, Assets/Bilder usw.) zum Rendern der Website geändert wurden, unterscheidet sich die Ansicht von der ursprünglich verwendeten, da diese Elemente nicht im Repository versioniert sind.

>[!CAUTION]
>
>Timewarp wurde als Tool entwickelt, um Autoren beim Verstehen und Erstellen ihres Inhalts zu unterstützen. Es ist nicht als Prüfprotokoll oder zu rechtlichen Zwecken gedacht.
