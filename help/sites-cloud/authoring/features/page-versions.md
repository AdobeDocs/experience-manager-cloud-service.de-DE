---
title: Arbeiten mit Seitenversionen
description: Erstellen, Vergleichen und Wiederherstellen von Versionen einer Seite
exl-id: 33d8e43c-594d-4bba-9631-b2c42a1e910f
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1512'
ht-degree: 76%

---

# Arbeiten mit Seitenversionen {#working-with-page-versions}

Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung können Sie die folgenden Aktionen durchführen:

* Erstellen Sie eine Version einer Seite.
* Reaktivieren einer früheren Version von einer oder mehreren Seiten, um:
   * Änderungen rückgängig zu machen, die an den Seiten vorgenommen wurden.
   * gelöschte Seiten wiederherzustellen.
   * einen Baum wiederherzustellen (wie er zu einem bestimmten Datum und einer bestimmten Uhrzeit war).
* Anzeigen der Vorschau einer Version.
* Vergleichen der aktuellen Version einer Seite mit einer früheren Version.
   * Unterschiede bei Text und Bildern werden hervorgehoben.
* Timewarp nutzt hierbei die Seitenversionen, um den Status der Veröffentlichungsumgebung zu ermitteln.

## Erstellen einer neuen Version {#creating-a-new-version}

Sie können eine Version Ihrer Ressource folgendermaßen erstellen:

* über die [Zeitleiste](#creating-a-new-version-timeline)
* mithilfe der Option [Erstellen](#creating-a-new-version-create-with-a-selected-resource) (wenn eine Ressource ausgewählt ist)

### Erstellen einer neuen Version – Timeline {#creating-a-new-version-timeline}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste**.
1. Klicken/tippen Sie auf die Auslassungszeichen neben dem Kommentarfeld, um die Optionen anzuzeigen:

   ![Versionen in der Zeitleiste](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. Auswählen **Als Version speichern**.
1. Geben Sie eine **Beschriftung** an und ggf. einen **Kommentar** ein.

   ![Bezeichnung für eine Version hinzufügen](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

   Die Informationen in der Zeitleiste werden entsprechend der neuen Version aktualisiert.

### Erstellen einer neuen Version – Erstellen mit einer ausgewählten Ressource {#creating-a-new-version-create-with-a-selected-resource}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Wählen Sie die **Erstellen** in der Symbolleiste.
1. Dasselbe Dialogfeld wird geöffnet. Sie können eine **Beschriftung** angeben und ggf. einen **Kommentar** eingeben.
1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

Die Informationen in der Zeitleiste werden entsprechend der neuen Version aktualisiert.

## Reaktivierung von Versionen {#reinstating-versions}

Nachdem Sie eine Version Ihrer Seite erstellt haben, gibt es verschiedene Methoden, eine ältere Version zu reaktivieren:

* die Option **Auf diese Version zurück** in der [Zeitleiste](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline).

  Reaktivieren Sie eine frühere Version einer ausgewählten Seite.

* die Optionen zum **Wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)

   * **Version wiederherstellen**

     Reaktivieren Sie Versionen bestimmter Seiten im derzeit ausgewählten Ordner; dies kann auch die Wiederherstellung von zuvor gelöschten Seiten umfassen.

   * **Baum wiederherstellen**

     Reaktivieren Sie eine Version eines gesamten Baums zu einem bestimmten Datum und einer bestimmten Uhrzeit; dies kann Seiten umfassen, die zuvor gelöscht wurden.

>[!NOTE]
>
>Wenn eine Seite reaktiviert wird, gehört die erstellte Version zu einem neuen Zweig.
>
>Beispiel:
>
>1. Erstellen Sie Versionen einer beliebigen Seite.
>1. Die anfänglichen Beschriftungen und Versionsknotennamen lauten 1.0, 1.1, 1.2 usw.
>1. Reaktivieren Sie die erste Version, d. h. Version 1.0.
>1. Erstellen Sie erneut neue Versionen.
>1. Die generierten Bezeichnungen und Knotennamen lauten jetzt 1.0.0, 1.0.1, 1.0.2 usw.

### Auf eine Version zurücksetzen {#revert-to-a-version}

So können Sie die ausgewählte Seite in einer früheren Version **wiederherstellen**:

1. Navigieren Sie zu der Seite, für die Sie eine frühere Version wiederherstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus. Die Seitenversionen für die ausgewählte Seite werden aufgelistet.
1. Wählen Sie die Version, die Sie wiederherstellen möchten. Die möglichen Optionen werden angezeigt:

   ![Auf diese Version zurück](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Auf diese Version zurück**. Die ausgewählte Version wird wiederhergestellt und die Informationen in der Zeitleiste werden aktualisiert.

### Version wiederherstellen {#restore-version}

Mit dieser Methode können Versionen bestimmter Seiten im aktuellen Ordner wiederhergestellt werden. Dies kann auch die Wiederherstellung von Seiten umfassen, die zuvor gelöscht wurden:

1. Navigieren Sie zum gewünschten Ordner und [wählen](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) Sie ihn aus.

1. Wählen Sie **Wiederherstellen** und dann **Version wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar).

   >[!NOTE]
   >
   >Wenn Sie:
   >* eine einzelne Seite ausgewählt haben, die noch nie untergeordnete Seiten hatte,
   >* oder keine der Seiten im Ordner Versionen enthält,
   >
   >ist die Anzeige leer, da keine Versionen verfügbar sind.

1. Die verfügbaren Versionen sind aufgeführt:

   ![Version wiederherstellen – Liste aller Seiten im Ordner](/help/sites-cloud/authoring/assets/versions-restore-version-01.png)

1. Verwenden Sie für eine bestimmte Seite die Dropdown-Auswahl unter **WIEDERHERZUSTELLENDE VERSION**, um die erforderliche Version für diese Seite auszuwählen.

   ![Version wiederherstellen – Version auswählen](/help/sites-cloud/authoring/assets/versions-restore-version-02.png)

1. Wählen Sie in der Hauptanzeige die zu wiederherzustellende Seite aus:

   ![Version wiederherstellen – Seite auswählen](/help/sites-cloud/authoring/assets/versions-restore-version-03.png)

1. Wählen Sie für die ausgewählte Version der ausgewählten Seite, die als aktuelle Version wiederhergestellt werden soll, die Option **Wiederherstellen**.

>[!NOTE]
>
>Die Reihenfolge, in der Sie eine erforderliche Seite und die zugehörige Version auswählen, ist austauschbar.

### Baum wiederherstellen {#restore-tree}

Diese Methode kann verwendet werden, um eine Version eines Baums, wie er zu einem bestimmten Datum und zu einer bestimmten Zeit war, wiederherzustellen; dies kann Seiten umfassen, die zuvor gelöscht wurden:

1. Navigieren Sie zum gewünschten Ordner und [wählen](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) Sie ihn aus.

1. Wählen Sie **Wiederherstellen** und dann **Baum wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar). Die aktuelle Version des Baums wird angezeigt:

   ![Baum wiederherstellen](/help/sites-cloud/authoring/assets/versions-restore-tree-01.png)

1. Verwenden Sie die Datums- und Uhrzeitauswahl unter **Neueste Versionen am Datum**, um eine andere Version des Baums auszuwählen – und zwar die, die wiederhergestellt werden soll.

1. Setzen Sie bei Bedarf das Flag **Seiten ohne Versionsangabe beibehalten**:

   * Wenn diese Option aktiviert (ausgewählt) ist, werden alle Seiten ohne Versionierung beibehalten und von der Wiederherstellung nicht beeinflusst.

   * Wenn diese Option deaktiviert (nicht ausgewählt) ist, werden alle Seiten ohne Versionierung entfernt, da sie in der versionierten Struktur nicht vorhanden waren.

1. Wählen Sie **Wiederherstellen** für die ausgewählte Version des Baums, die als *aktuelle* Version wiederhergestellt werden soll.

## Vorschau einer Version {#previewing-a-version}

Sie können eine Vorschau einer bestimmten Version anzeigen:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgelistet. Wählen Sie die Version aus, die Sie in der Vorschau anzeigen möchten:

   ![Vorschau der Version anzeigen](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Vorschau**. Die Seite wird in einer neuen Registerkarte angezeigt.

   >[!CAUTION]
   >
   >Wenn eine Seite verschoben wurde, können Sie keine Vorschau mehr für Versionen anzeigen, die vor dem Verschieben vorgenommen wurden.
   >
   >Wenn Probleme bei der Vorschau auftreten, überprüfen Sie in der [Zeitleiste](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

## Vergleichen einer Version mit der aktuellen Seite {#comparing-a-version-with-current-page}

So vergleichen Sie eine frühere Version mit der aktuellen Seite:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgelistet. Wählen Sie die Version aus, die Sie vergleichen möchten:

   ![Versionen vergleichen](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Auswählen **Mit aktueller Version vergleichen**. Die [Seitenvergleich](/help/sites-cloud/authoring/features/page-diff.md) öffnet und zeigt die Unterschiede an.

## Timewarp {#timewarp}

Timewarp ist eine Funktion, die den *Veröffentlichungsstatus* einer Seite zu einer bestimmten Zeit in der Vergangenheit simuliert.

>[!TIP]
>
>[Timewarp kann auch mit Launches verwendet werden, damit Sie künftige Versionen in der Vorschau betrachten können.](/help/sites-cloud/authoring/launches/preview.md)

Da es sich bei der Inhaltserstellung um einen fortlaufenden und kollaborativen Prozess handelt, besteht der Zweck von Timewarp darin, Autoren zu ermöglichen, die veröffentlichte Website im Laufe der Zeit zu verfolgen, damit sie verstehen können, wie sich der Inhalt verändert hat. Diese Funktion verwendet die Seitenversionen, um den Zustand der Veröffentlichungsumgebung zu bestimmen.

Gehen Sie hierfür wie folgt vor:

* Das System sucht nach der Seitenversion, die zum ausgewählten Zeitpunkt aktiv war.
* Dies bedeutet, dass die angezeigte Version erstellt/aktiviert wurde *before* den in Timewarp ausgewählten Zeitpunkt.
* Wenn Sie zu einer inzwischen gelöschten Seite navigieren, wird diese ebenfalls wiedergegeben, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* Wenn keine veröffentlichte Version gefunden wird, kehrt Timewarp zum aktuellen Status der Seite in der Autorenumgebung zurück (dadurch wird eine Fehler-/404-Seite vermieden, die dazu führen würde, dass Sie nicht weiter browsen können).

### Verwenden von Timewarp {#using-timewarp}

Timewarp ist eine [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) des Seiteneditors. Um es zu starten, wechseln Sie es einfach wie jeder andere Modus.

1. Starten Sie den Editor für die Seite, auf der Sie Timewarp starten möchten, und wählen Sie dann **Timewarp** in der Modusauswahl.

   ![Timewarp-Modus](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. Legen Sie im Dialogfeld ein Datum und eine Uhrzeit fest und tippen/klicken Sie auf **Datum einstellen**. Wenn Sie keine Zeit auswählen, wird die aktuelle Zeit standardmäßig eingestellt.

   ![Timewarp-Zieldatum](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. Die Seite wird basierend auf dem festgelegten Datum angezeigt. Der Timewarp-Modus wird über die blaue Statusleiste am oberen Rand des Fensters angezeigt. Verwenden Sie die Links in der Statusleiste, um ein neues Zieldatum auszuwählen oder den Timewarp-Modus zu beenden.

   ![Im Timewarp-Modus](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### Timewarp-Beschränkungen {#timewarp-limitations}

Timewarp versucht, eine Seite zu einem bestimmten Zeitpunkt zu reproduzieren. Aufgrund der Komplexität der kontinuierlichen Bearbeitung von Inhalten in AEM ist dies jedoch nicht immer möglich. Diese Einschränkungen sollten bei der Verwendung von Timewarp beachtet werden.

* **Timewarp funktioniert auf veröffentlichten Seiten**: Timewarp funktioniert nur dann vollständig, wenn Sie die Seite bereits veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung.
* **Timewarp verwendet Seitenversionen**: Wenn Sie zu einer inzwischen aus dem Repository gelöschten Seite navigieren, wird diese ebenfalls korrekt wiedergegeben, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* **Entfernte Versionen wirken sich auf Timewarp**: Wenn Versionen aus dem Repository entfernt wurden, kann Timewarp die korrekte Ansicht nicht anzeigen.
* **Timewarp ist schreibgeschützt**: Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen möchten, müssen Sie dies über [Wiederherstellen](#revert-to-a-version) manuell ausführen.
* **Timewarp basiert nur auf dem Seiteninhalt**: Die Ansicht unterscheidet sich von der ursprünglichen Ansicht, wenn Elemente (Code, CSS, Assets/Bilder usw.) für die Anzeige der Website geändert wurden, da diese Elemente nicht im Repository versioniert werden.

>[!CAUTION]
>
>Timewarp wurde als Tool entwickelt, um Autoren beim Verstehen und Erstellen ihres Inhalts zu unterstützen. Es ist nicht als Prüfprotokoll oder zu rechtlichen Zwecken gedacht.
