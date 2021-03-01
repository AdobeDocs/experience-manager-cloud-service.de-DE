---
title: Seitenvergleich
description: Die Seitenvergleichsfunktion ermöglicht einen bequemen Vergleich von zwei Seiten, die nebeneinander angezeigt werden und deren Unterschiede hervorgehoben sind.
translation-type: tm+mt
source-git-commit: 95ac5e5f6c49d5a2d7aef5dcf30d8298fd459457
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 100%

---


# Seitenvergleich  {#page-diff}

## Einführung {#introduction}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Ein Autor muss die Möglichkeit haben, die aktuelle Seite direkt mit der anderen Seite zu vergleichen.

Die Seitenvergleichsfunktion ermöglicht einen bequemen Vergleich von zwei Seiten, die nebeneinander angezeigt werden und deren Unterschiede hervorgehoben sind.

>[!NOTE]
>
>Der Benutzer muss über die Berechtigung zum **Ändern/Erstellen/Löschen** auf dem Knoten `/content/versionhistory` verfügen, um die Funktion verwenden zu können.
>
>Weitere Informationen zu dieser Funktion finden Sie unter [Entwicklung und Seitenvergleich](/help/implementing/developing/introduction/page-diff.md#operation-details).

## Verwenden Sie {#use}

Folgendes kann verglichen werden:

* [Versionen](/help/sites-cloud/authoring/features/page-versions.md#comparing-a-version-with-current-page) – frühere Version einer Seite mit ihrem aktuellen Status
* [](/help/sites-cloud/administering/msm/creating-live-copies.md#comparing-a-live-copy-page-with-a-blueprint-page)Live Copies – Live Copy mit ihrer Blueprint
* [Launches](/help/sites-cloud/authoring/launches/editing.md#comparing-a-launch-page-to-its-source-page) – Launch mit seiner Quelle
* [](/help/sites-cloud/administering/translation/managing-projects.md#comparing-language-copies)Sprachkopien – eine Seite vor und nach der (erneuten) Übersetzung

Informieren Sie sich unter den entsprechenden Themen, wie der Seitenvergleich im gegebenen Zusammenhang verwendet wird.

### Darstellung von Unterschieden   {#presentation-of-differences}

Unabhängig vom verglichenen Inhalt bleibt die Darstellung der Unterschiede gleich.

* Nachdem Sie den Seitenvergleich gestartet haben, wird der ausgewählte Inhalt auf der linken Seite angezeigt (der Differenzeinstiegspunkt).
* Rechts wird der zu vergleichende Inhalt angezeigt (der mit dem ausgewählten Inhalt verglichen wird).

Wenn Sie z. B. Versionen vergleichen, wird die aktuelle Version auf der linken Seite und die Vorversion auf der rechten Seite angezeigt.

Die Quelle beider Seiten wird deutlich in der Kopfzeile am oberen Rand des Browser-Fensters angezeigt.

![Seitenvergleich der Versionen](/help/sites-cloud/authoring/assets/versions-side-by-side.png)

Der Seitenvergleich erkennt Änderungen an der Komponente und der HTML-Ebene. Geänderte Elemente werden mit verschiedenen Farben hervorgehoben.

**Komponentenänderungen**

* Hellgrün – Komponente hinzugefügt
* Rosa – Komponente entfernt

**HTML-Änderungen**

* Dunkelgrün – HTML hinzugefügt
* Rot – HTML entfernt

>[!NOTE]
>
>Beim Vergleich von Sprachkopien ist die Hervorhebung deaktiviert, da sich in einer Übersetzung alles ändert und Hervorhebung nutzlos wäre.

### Vollbild und Beenden   {#fullscreen-and-exiting}

Damit Sie sich auf einen bestimmten Inhalt konzentrieren können, haben Sie die Möglichkeit, auf jeder Seite des Seitenvergleichs auf das Vollbildsymbol zu klicken, um die Ansicht auf das ganze Browser-Fenster zu vergrößern.

![Schaltfläche „Vollbild“](/help/sites-cloud/authoring/assets/versions-full-screen.png)

Die gewählte Seite füllt dann das gesamte Fenster aus, aber die Leiste am oberen Rand bleibt weiterhin angezeigt und bietet Ihnen die Möglichkeit, zwischen den zwei Seiten zu wechseln.

![Vollbildmodus](/help/sites-cloud/authoring/assets/versions-full-screen-mode.png)

>[!NOTE]
>
>Wenn die Browser-Breite nicht beide Seitennamen in der Vollbildansicht aufnehmen kann, wird nur der Name der angezeigten Seite angezeigt und der andere Name ist über die Auslassungspunkte verfügbar.

Sie können die Vollbildansicht auch schließen, indem Sie auf das Symbol „Vollbildmodus beenden“ klicken.

![Vollbildmodus beenden](/help/sites-cloud/authoring/assets/versions-exit-full-screen.png)

Sie können den Seitenvergleich jederzeit beenden, indem Sie in der Kopfzeile auf die Schaltfläche „Schließen“ klicken.

## Beschränkungen {#limitations}

In manchen Fällen erkennt der Seitenvergleich einen Unterschied nicht wie erwartet.

* Beim Vergleich von Versionen und Launches berücksichtigt der Seitenvergleich keine dynamischen Komponenten wie Breadcrumbs, Menüs, Produktlisten oder Logos (Komponenten, die die Site-Struktur zur Darstellung ihres Inhalts nutzen).
* Bei Versionen erstellt der Vergleich die Richtlinien zur Zugriffssteuerung und die Live Copy-Beziehungen nicht neu.
* Wenn eine Seite verschoben wird, können Sie keinen Vergleich mit Versionen mehr durchführen, die vor dem Verschieben erstellt wurden.
   * Wenn Probleme beim Vergleich auftreten, überprüfen Sie in der [Zeitleiste](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

>[!NOTE]
>
>Versionen können nicht miteinander verglichen werden. Nur die aktuelle Version kann mit anderen Versionen der Seite verglichen werden. Die aktuelle Version ist immer die Version, deren Änderungen hervorgehoben sind.

>[!NOTE]
>
>Weitere Informationen zum Ablauf des Seitenvergleichsmechanismus sowie Einschränkungen, die sich auf den Seitenvergleich auswirken können, finden Sie in der [Entwickler-Dokumentation](/help/implementing/developing/introduction/page-diff.md) zu dieser Funktion.
