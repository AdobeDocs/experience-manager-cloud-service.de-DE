---
title: Arbeiten mit Seitenversionen
description: Erfahren Sie, wie Sie verschiedene Versionen Ihrer Seiten erstellen, vergleichen und wiederherstellen können.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 33d8e43c-594d-4bba-9631-b2c42a1e910f
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 99%

---

# Arbeiten mit Seitenversionen {#working-with-page-versions}

Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung können Sie die folgenden Aktionen durchführen:

* Erstellen einer Version einer Seite.
* Reaktivieren einer früheren Version von einer oder mehreren Seiten, um:
   * Änderungen rückgängig zu machen, die an den Seiten vorgenommen wurden.
   * gelöschte Seiten wiederherzustellen.
   * einen Baum wiederherzustellen (wie er zu einem bestimmten Datum und einer bestimmten Uhrzeit war).
* Anzeigen der Vorschau einer Version.
* Vergleichen der aktuellen Version einer Seite mit einer früheren Version.
   * Unterschiede bei Text und Bildern werden hervorgehoben.
* Timewarp nutzt hierbei die Seitenversionen, um den Status der Veröffentlichungsumgebung zu ermitteln.

>[!NOTE]
>
>Im AEM-Repository wird nur der Inhalt versioniert. Dynamische Ressourcen wie Code, CSS und JavaScript werden nicht versioniert.
>
>* Beim Anzeigen von Versionen wird der Inhalt mit dem aktuellen Code, CSS und JavaScript des Repositorys angezeigt.
>* Beim Wiederherstellen von Versionen wird nur der Inhalt wiederhergestellt und der aktuelle Code, CSS und JavaScript des Repositorys werden darauf angewendet.

## Erstellen einer neuen Version {#creating-a-new-version}

Sie können eine Version Ihrer Ressource folgendermaßen erstellen:

* über die [Timeline](#creating-a-new-version-timeline)
* mithilfe der Option [Erstellen](#creating-a-new-version-create-with-a-selected-resource) (wenn eine Ressource ausgewählt ist)

### Erstellen einer neuen Version – Timeline {#creating-a-new-version-timeline}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Timeline**.
1. Wählen Sie die Auslassungszeichen neben dem Kommentarfeld aus, um die Optionen anzuzeigen:

   ![Versionen in der Timeline](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. Wählen Sie **Als Version speichern**.
1. Geben Sie gegebenenfalls eine **Beschriftung** und einen **Kommentar** ein.

   ![Bezeichnung für eine Version hinzufügen](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

   Die Informationen in der Timeline werden aktualisiert, um die neue Version anzuzeigen.

### Erstellen einer neuen Version – Erstellen mit einer ausgewählten Ressource {#creating-a-new-version-create-with-a-selected-resource}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Wählen Sie die Option **Erstellen** in der Symbolleiste
1. Das gleiche Dialogfeld wird geöffnet. Sie können eine **Beschriftung** und einen **Kommentar** eingeben, falls erforderlich.
1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

Die Timeline wird geöffnet und die Informationen werden aktualisiert, um die neue Version anzuzeigen.

## Reaktivierung von Versionen {#reinstating-versions}

Nachdem Sie eine Version Ihrer Seite erstellt haben, gibt es verschiedene Methoden, eine ältere Version zu reaktivieren:

* die Option **Auf diese Version zurück** in der [Timeline](/help/sites-cloud/authoring/basic-handling.md#timeline).

  Reaktivieren Sie eine frühere Version einer ausgewählten Seite.

* die Optionen zum **Wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar)

   * **Version wiederherstellen**

     Reaktiviert Versionen bestimmter Seiten im derzeit ausgewählten Ordner. Außerdem können auch Seiten wiederhergestellt werden, die zuvor gelöscht wurden.

   * **Baum wiederherstellen**

     Reaktiviert eine Version der gesamten Baumstruktur zu einem bestimmten Datum und einer bestimmten Uhrzeit. Außerdem kann sie auch Seiten enthalten, die zuvor gelöscht wurden.

>[!NOTE]
>
>Wenn eine Seite reaktiviert wird, gehört die erstellte Version zu einem neuen Zweig.
>
>Beispiel:
>
>1. Erstellen Sie Versionen einer beliebigen Seite.
>1. Die anfänglichen Beschriftungen und Versionsknotennamen lauten 1.0, 1.1, 1.2 usw.
>1. Reaktivieren Sie die erste Version, also 1.0.
>1. Erstellen Sie Versionen erneut.
>1. Die generierten Beschriftungen und Knotennamen lauten jetzt 1.0.0, 1.0.1, 1.0.2 usw.

### Auf eine Version zurücksetzen {#revert-to-a-version}

So können Sie für die ausgewählte Seite eine frühere Version **wiederherstellen**:

1. Navigieren Sie zu der Seite, für die Sie eine frühere Version wiederherstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Timeline** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus. Die Seitenversionen für die ausgewählte Seite werden aufgelistet.
1. Wählen Sie die Version aus, die Sie wiederherstellen möchten. Die möglichen Optionen werden angezeigt:

   ![Auf diese Version zurück](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Auf diese Version zurück**. Die ausgewählte Version wird wiederhergestellt und die Informationen in der Timeline werden aktualisiert.

### Version wiederherstellen {#restore-version}

Mit dieser Methode können Versionen bestimmter Seiten im aktuellen Ordner wiederhergestellt werden. Dies kann auch die Wiederherstellung von Seiten umfassen, die zuvor gelöscht wurden:

1. Navigieren Sie zum gewünschten Ordner und [wählen](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) Sie ihn aus.

1. Wählen Sie **Wiederherstellen** und dann **Version wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar).

   >[!NOTE]
   >
   >Wenn Sie:
   >
   >* entweder eine einzelne Seite ausgewählt haben, die noch nie untergeordnete Seiten hatte,
   >* oder keine der Seiten im Ordner Versionen enthält,
   >
   >wird die Anzeige leer, da keine zutreffenden Versionen vorhanden sind.

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

Mit dieser Methode können Sie eine Version eines Baums so wiederherstellen, wie sie zu einem bestimmten Datum und einer bestimmten Uhrzeit aussah. Sie kann Seiten umfassen, die zuvor gelöscht wurden:

1. Navigieren Sie zum gewünschten Ordner und [wählen](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) Sie ihn aus.

1. Wählen Sie **Wiederherstellen** und dann **Baum wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar). Die aktuelle Version des Baums wird angezeigt:

   ![Baum wiederherstellen](/help/sites-cloud/authoring/assets/versions-restore-tree-01.png)

1. Verwenden Sie die Datums- und Uhrzeitauswahl unter **Neueste Versionen am Datum**, um eine andere Version des Baums auszuwählen, nämlich die, die wiederhergestellt werden soll.

1. Setzen Sie bei Bedarf das Flag **Seiten ohne Versionsangabe beibehalten**:

   * Wenn diese Option aktiviert (markiert) ist, werden alle Seiten ohne Versionierung beibehalten und von der Wiederherstellung nicht beeinflusst.

   * Wenn diese Option inaktiv (nicht markiert) ist, werden alle Seiten ohne Versionierung entfernt, da sie nicht im versionierten Baum vorhanden waren.

1. Wählen Sie **Wiederherstellen** für die ausgewählte Version des Baums, die als *aktuelle* Version wiederhergestellt werden soll.

## Vorschau einer Version {#previewing-a-version}

Sie können eine Vorschau einer bestimmten Version anzeigen:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Timeline** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgelistet. Wählen Sie die Version, die Sie in der Vorschau anzeigen möchten:

   ![Vorschau der Version anzeigen](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Vorschau**. Die Seite wird in einer neuen Registerkarte angezeigt.

   >[!CAUTION]
   >
   >Wenn eine Seite verschoben wurde, können Sie keine Vorschau von Versionen mehr anzeigen, die vor dem Verschieben erstellt wurden.
   >
   >Wenn Probleme bei der Vorschau auftreten, überprüfen Sie in der [Timeline](/help/sites-cloud/authoring/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

## Vergleichen einer Version mit der aktuellen Seite {#comparing-a-version-with-current-page}

So vergleichen Sie eine frühere Version mit der aktuellen Seite:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Timeline** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgelistet. Wählen Sie die Version aus, die Sie vergleichen möchten.

   ![Versionen vergleichen](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Mit aktueller Version vergleichen** aus. Der [Seitenvergleich](/help/sites-cloud/authoring/sites-console/page-diff.md) wird geöffnet und zeigt die Unterschiede an.

## Timewarp {#timewarp}

Timewarp ist eine Funktion, die den *Veröffentlichungsstatus* einer Seite zu einer bestimmten Zeit in der Vergangenheit simuliert.

Da die Erstellung von Inhalten ein fortlaufender und kollaborativer Prozess ist, besteht der Zweck von Timewarp darin, Autorinnen und Autoren zu ermöglichen, die veröffentlichte Website im Laufe der Zeit zu verfolgen, um zu verstehen, wie sich der Inhalt verändert hat. Diese Funktion verwendet die Seitenversionen, um den Zustand der Publishing-Umgebung zu bestimmen.

So verwenden Sie diese Funktion:

* Das System sucht nach der Seitenversion, die zum ausgewählten Zeitpunkt aktiv war.
* Das bedeutet, dass die angezeigte Version *vor* dem in Timewarp gewählten Zeitpunkt erstellt/aktiviert wurde.
* Wenn Sie zu einer inzwischen gelöschten Seite navigieren, wird diese ebenfalls gerendert, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* Wenn keine veröffentlichte Version gefunden wird, kehrt Timewarp zum aktuellen Zustand der Seite in der Authoring-Umgebung zurück (der Grund dafür ist, eine Fehler/404-Seite zu vermeiden, die das Browsen verhindern würde).

>[!NOTE]
>
>Timewarp funktioniert für AEM-Seiten und ist für diese Verwendung vorgesehen – Versionen für den Verlauf und Launches für zukünftige Inhaltsstatus.
>
>Dies funktioniert nicht für verschachtelte Launches oder bei der Verwendung von Experience Fragments.

>[!TIP]
>
>[Timewarp kann auch mit Launches verwendet werden, um die Zukunft in der Vorschau anzuzeigen](/help/sites-cloud/authoring/launches/preview.md).

### Verwenden von Timewarp {#using-timewarp}

Timewarp ist ein [Modus](/help/sites-cloud/authoring/page-editor/introduction.md#page-modes) des Seiteneditors. Um ihn zu starten, aktivieren Sie ihn einfach wie jeden anderen Modus.

1. Starten Sie den Editor für die Seite, auf der Timewarp ausgeführt werden soll, und wählen Sie in der Modusauswahl **Timewarp** aus.

   ![Timewarp-Modus](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. Legen Sie im Dialogfeld ein Zieldatum und eine Uhrzeit fest und klicken Sie auf **Datum festlegen**. Wenn Sie keine Zeit auswählen, wird standardmäßig die aktuelle Zeit verwendet.

   ![Timewarp-Zieldatum](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. Die Seite wird basierend auf dem festgelegten Datum angezeigt. Der Timewarp-Modus ist durch die blaue Statusleiste am oberen Fensterrand gekennzeichnet. Verwenden Sie die Links in der Statusleiste, um ein neues Zieldatum auszuwählen oder den Timewarp-Modus zu verlassen.

   ![Im Timewarp-Modus](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### Timewarp-Beschränkungen {#timewarp-limitations}

Timewarp bemüht sich nach Kräften, eine Seite zu einem bestimmten Zeitpunkt zu reproduzieren. Aufgrund der Komplexität der kontinuierlichen Erstellung von Inhalten in AEM ist diese Reproduktion jedoch nicht immer möglich. Beachten Sie diese Einschränkungen bei der Verwendung von Timewarp.

* **Timewarp arbeitet auf der Grundlage veröffentlichter Seiten**: Timewarp funktioniert nur dann vollständig, wenn Sie die Seite bereits veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung an.
* **Timewarp verwendet Seitenversionen**: Wenn Sie zu einer inzwischen aus dem Repository gelöschten Seite navigieren, wird diese ebenfalls korrekt wiedergegeben, sofern die alten Versionen der Seite noch im Repository verfügbar sind.
* **Entfernte Versionen wirken sich auf Timewarp**: Wenn Versionen aus dem Repository entfernt wurden, kann Timewarp die korrekte Ansicht nicht anzeigen.
* **Timewarp ist schreibgeschützt**: Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen wollen, müssen Sie dies manuell mit [Wiederherstellen](#revert-to-a-version) tun.
* **Timewarp basiert auf dem Seiteninhalt** – Wenn sich Elemente zum Rendern der Website geändert haben, wie Code, CSS und Assets, unterscheidet sich die Ansicht von der ursprünglichen Ansicht. Diese Elemente werden im Repository nicht versioniert.
* Timewarp funktioniert nicht bei verschachtelten Launches oder bei der Verwendung von Experience Fragments.

>[!CAUTION]
>
>Timewarp wurde als Tool entwickelt, um Autoren beim Verstehen und Erstellen ihres Inhalts zu unterstützen. Es ist nicht als Auditprotokoll oder zu rechtlichen Zwecken gedacht.
