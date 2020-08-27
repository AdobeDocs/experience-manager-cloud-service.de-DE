---
title: Arbeiten mit Seitenversionen
description: Sie können verschiedene Versionen einer Seite erstellen, vergleichen und wiederherstellen.
translation-type: tm+mt
source-git-commit: 2d5c7ee7866f8334e67a36b120fdb8ad7a34e7f1
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 67%

---


# Arbeiten mit Seitenversionen {#working-with-page-versions}

Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung sind die folgenden Aktionen verfügbar:

* Erstellen einer Version einer Seite
* Frühere Version einer oder mehrerer Seiten neu angeben, um:
   * Rückgängigmachen von Änderungen, die an den Seiten vorgenommen wurden.
   * Wiederherstellen von gelöschten Seiten.
   * Wiederherstellen eines Baums (wie zu einem bestimmten Datum und einer bestimmten Uhrzeit).
* Vorschau einer Version.
* Vergleichen Sie die aktuelle Version einer Seite mit einer früheren Version.
   * Unterschiede im Text und bei Bildern werden hervorgehoben.
* Timewarp verwendet die Seitenversionen, um den Status der Veröffentlichungs-Umgebung zu bestimmen.

## Erstellen einer neuen Version   {#creating-a-new-version}

Sie können eine Version Ihrer Ressource folgendermaßen erstellen:

* über die [Timeline-Leiste](#creating-a-new-version-timeline)
* mithilfe der Option [Erstellen](#creating-a-new-version-create-with-a-selected-resource) (wenn eine Ressource ausgewählt ist)

### Erstellen einer neuen Version – Timeline {#creating-a-new-version-timeline}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die Leiste **Timeline**.
1. Klicken/tippen Sie auf die Auslassungszeichen neben dem Kommentarfeld, um die Optionen anzuzeigen:

   ![Versionen in der Timeline-Leiste](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. Wählen Sie **Als Version speichern**.
1. Geben Sie ein **Etikett** an und ggf. einen **Kommentar** ein.

   ![Bezeichnung für eine Version hinzufügen](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

   Die Informationen in der Timeline werden entsprechend der neuen Version aktualisiert.

### Erstellen einer neuen Version – Erstellen mit einer ausgewählten Ressource {#creating-a-new-version-create-with-a-selected-resource}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Wählen Sie in der Symbolleiste die Option **Erstellen**.
1. Dasselbe Dialogfeld wird geöffnet. Sie können ein **Etikett** angeben und ggf. einen **Kommentar** eingeben.
1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

Die Informationen in der Timeline werden entsprechend der neuen Version aktualisiert.

## Neueinstufung von Versionen {#reinstating-versions}

Nachdem Sie eine Version Ihrer Seite erstellt haben, gibt es verschiedene Methoden, eine ältere Version erneut zu installieren:

* Option **Auf Version** zurücksetzen in der [Zeitleiste](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

   Frühere Version einer ausgewählten Seite erneut angeben.

* die Optionen **Wiederherstellen** in der Symbolleiste der oberen [Aktionen](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)

   * **Version wiederherstellen**

      Neuzuordnen von Versionen bestimmter Seiten im derzeit ausgewählten Ordner; Dies kann auch die Wiederherstellung von zuvor gelöschten Seiten umfassen.

   * **Baum wiederherstellen**

      eine Version eines gesamten Baums zu einem bestimmten Datum und einer bestimmten Uhrzeit neu angeben; Dies kann Seiten umfassen, die zuvor gelöscht wurden.

>[!NOTE]
>
>Beim erneuten Installieren einer Seite wird die erstellte Version Teil einer neuen Verzweigung.
>
>Beispiel:
>
>1. Erstellen Sie Versionen einer beliebigen Seite.
>1. Die anfänglichen Etiketten und Versionsknotennamen lauten 1.0, 1.1, 1.2 usw.
>1. Die erste Version erneut angeben; d. h. 1.0.
>1. Erstellen Sie weitere neue Versionen.
>1. Die erzeugten Etiketten und Knotennamen lauten jetzt 1.0.0, 1.0.1, 1.0.2 usw.


### Revert to a Version {#revert-to-a-version}

So **stellen Sie** die ausgewählte Seite auf eine frühere Version zurück:

1. Navigieren Sie zu der Seite, für die Sie eine frühere Version wiederherstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die Spalte **Timeline** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus. Die Seitenversionen für die ausgewählte Seite werden aufgelistet.
1. Wählen Sie die Version, die Sie wiederherstellen möchten. Die möglichen Optionen werden angezeigt:

   ![Auf diese Version zurücksetzen](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Wählen Sie **Auf diese Version zurücksetzen**. Die ausgewählte Version wird wiederhergestellt und die Informationen in der Timeline werden aktualisiert.

### Version wiederherstellen {#restore-version}

Mit dieser Methode können Versionen bestimmter Seiten im aktuellen Ordner wiederhergestellt werden. Dies kann auch die Wiederherstellung von Seiten umfassen, die zuvor gelöscht wurden:

1. Navigate to, and [select](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources), the required folder.

1. Wählen Sie **Wiederherstellen** und dann **Wiederherstellen der Version** in der Symbolleiste [der](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)Aktionen oben.

   >[!NOTE]
   >
   >Wenn eine der folgenden Optionen:
   >* Sie haben eine einzelne Seite ausgewählt, die noch keine untergeordneten Seiten hatte,
   >* oder keine der Seiten im Ordner Versionen enthält,

   >
   >Dann ist die Anzeige leer, da keine Versionen verfügbar sind.

1. Die verfügbaren Versionen werden aufgelistet:

   ![Version wiederherstellen - Liste aller Seiten im Ordner](/help/sites-cloud/authoring/assets/versions-restore-version-01.png)

1. Verwenden Sie für eine bestimmte Seite die Dropdownauswahl unter &quot; **WIEDERHERSTELLEN ZU VERSION** &quot;, um die erforderliche Version für diese Seite auszuwählen.

   ![Version wiederherstellen - Version auswählen](/help/sites-cloud/authoring/assets/versions-restore-version-02.png)

1. Wählen Sie in der Hauptanzeige die zu wiederherzustellende Seite aus:

   ![Version wiederherstellen - Seite auswählen](/help/sites-cloud/authoring/assets/versions-restore-version-03.png)

1. Wählen Sie **Wiederherstellen** für die ausgewählte Version der ausgewählten Seite, die als *aktuelle* Version wiederhergestellt werden soll.

>[!NOTE]
>
>Die Reihenfolge, in der Sie eine erforderliche Seite und die zugehörige Version auswählen, ist austauschbar.

### Baum wiederherstellen {#restore-tree}

Diese Methode kann verwendet werden, um eine Version eines Baums zu einem bestimmten Datum und zu einem bestimmten Zeitpunkt wiederherzustellen; Dies kann Seiten umfassen, die zuvor gelöscht wurden:

1. Navigate to, and [select](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources), the required folder.

1. Wählen Sie **Wiederherstellen** und dann **Wiederherstellen der Struktur** in der Symbolleiste [der](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)Aktionen oben. Die aktuelle Version des Baums wird angezeigt:

   ![Baum wiederherstellen](/help/sites-cloud/authoring/assets/versions-restore-tree-01.png)

1. Verwenden Sie die Datums- und Uhrzeitauswahl unter &quot; **Neueste Versionen am Datum** &quot;, um eine andere Version des Baums auszuwählen, die wiederhergestellt werden soll.

1. Legen Sie das Flag &quot; **Preserve Non Version Pages** &quot;wie gewünscht fest:

   * Wenn diese Option aktiviert ist, werden alle Seiten ohne Versionsnummer beibehalten und von der Wiederherstellung nicht beeinflusst.

   * Wenn diese Option deaktiviert (nicht ausgewählt) ist, werden alle Seiten ohne Versionsnummer entfernt, da sie nicht in der Versionsstruktur vorhanden waren.

1. Wählen Sie &quot; **Wiederherstellen** &quot;für die ausgewählte Version des Baums, die als *aktuelle* Version wiederhergestellt werden soll.

## Vorschau einer Version   {#previewing-a-version}

Sie können eine Vorschau einer bestimmten Version anzeigen:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die Spalte **Timeline** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgeführt. Wählen Sie die Version, deren Vorschau Sie anzeigen möchten:

   ![Vorschau der Version anzeigen](/help/sites-cloud/authoring/assets/versions-revert.png)

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

## Timewarp   {#timewarp}

Timewarp ist eine Funktion, die den *Veröffentlichungsstatus* einer Seite zu einer bestimmten Zeit in der Vergangenheit simuliert.

Da die Erstellung von Inhalten ein fortlaufender und kollaborativer Prozess ist, besteht der Zweck von Timewarp darin, den Autoren zu ermöglichen, die veröffentlichte Website im Laufe der Zeit zu verfolgen, um zu verstehen, wie sich der Inhalt verändert hat. Diese Funktion verwendet die Seitenversionen, um den Zustand der Publishing-Umgebung zu bestimmen.

Gehen Sie hierfür wie folgt vor:

* Das System sucht die Seitenversion, die zum gewählten Zeitpunkt aktiv war.
* Dies bedeutet, dass die angezeigte Version *vor* dem in Timewarp ausgewählten Zeitpunkt erstellt/aktiviert wurde.
* Wenn Sie zu einer inzwischen gelöschten Seite navigieren, wird diese ebenfalls wiedergegeben, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* Wenn keine veröffentlichte Version gefunden wird, kehrt Timewarp zum aktuellen Status der Seite in der Autorenumgebung zurück (dadurch wird eine Fehler-/404-Seite vermieden, die dazu führen würde, dass Sie nicht weiter browsen können).

### Verwenden von Timewarp {#using-timewarp}

Timewarp ist ein [Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) des Seiteneditors. Um ihn zu starten, aktivieren Sie ihn einfach wie jeden anderen Modus.

1. Starten Sie den Editor für die Seite, auf der Timewarp ausgeführt werden soll, und wählen Sie in der Modusauswahl **Timewarp**.

   ![Timewarp-Modus](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. Legen Sie im Dialogfeld ein Datum und eine Uhrzeit fest und tippen/klicken Sie auf **Datum festlegen**. Wenn Sie keine Zeit auswählen, wird die aktuelle Zeit standardmäßig eingestellt.

   ![Timewarp-Zieldatum](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. Die Seite wird entsprechend dem eingestellten Datum angezeigt. Der Timewarp-Modus ist durch die blaue Statusleiste am oberen Fensterrand gekennzeichnet. Verwenden Sie die Links in der Statusleiste, um ein neues Datum auszuwählen oder den Timewarp-Modus zu beenden.

   ![Im Timewarp-Modus](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### Timewarp-Beschränkungen {#timewarp-limitations}

Timewarp versucht, eine Seite zu einem bestimmten Zeitpunkt zu reproduzieren. Aufgrund der Komplexität der kontinuierlichen Bearbeitung von Inhalten in AEM ist dies jedoch nicht immer möglich. Diese Einschränkungen sollten bei der Verwendung von Timewarp beachtet werden.

* **Timewarp funktioniert auf veröffentlichten Seiten**: Timewarp funktioniert nur dann vollständig, wenn Sie die Seite bereits veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung.
* **Timewarp verwendet Seitenversionen** : Wenn Sie zu einer inzwischen aus dem Repository gelöschten Seite navigieren, wird diese ebenfalls korrekt wiedergegeben, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* **Entfernte Versionen wirken sich auf Timewarp**: Wenn Versionen aus dem Repository entfernt wurden, kann Timewarp die korrekte Ansicht nicht anzeigen.
* **Timewarp ist schreibgeschützt**: Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen möchten, müssen Sie dies über [Wiederherstellen](#reverting-to-a-page-version) manuell ausführen.
* **Timewarp basiert nur auf dem Seiteninhalt**: Die Ansicht unterscheidet sich von der ursprünglichen Ansicht, wenn Elemente (Code, CSS, Assets/Bilder usw.) für die Anzeige der Website geändert wurden, da diese Elemente nicht im Repository versioniert werden.

>[!CAUTION]
>
>Timewarp wurde als Tool entwickelt, um Autoren beim Verstehen und Erstellen ihres Inhalts zu unterstützen. Es ist nicht als Prüfprotokoll oder zu rechtlichen Zwecken gedacht.
