---
title: Seitenvergleich
description: Die Seitenvergleichsfunktion ermöglicht einen bequemen Vergleich von zwei Seiten, die nebeneinander angezeigt werden und deren Unterschiede hervorgehoben sind.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Seitenvergleich {#page-diff}

## Einführung {#introduction}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Ein Autor muss die Möglichkeit haben, die aktuelle Seite direkt mit der anderen Seite zu vergleichen.

Die Seitenvergleichsfunktion ermöglicht einen bequemen Vergleich von zwei Seiten, die nebeneinander angezeigt werden und deren Unterschiede hervorgehoben sind.

>[!CAUTION]
>
>The user must have the **Modify/Create/Delete** permission on the node `/content/versionhistory` in order to use the feature.
>
>Weitere Informationen zu dieser Funktion finden Sie unter Entwicklung und Seitenvergleich. <!-- See [Developing and Page Diff](/help/sites-developing/pagediff.md#operation-details) for more technical details on this feature.-->

## Verwenden Sie:{#use}

Folgendes kann verglichen werden:

* [Versionen](/help/sites-cloud/authoring/features/page-versions.md#comparing-a-version-with-current-page) - Frühere Version einer Seite mit dem aktuellen Status
* Live Copies - Live Copy with its Blueprint <!-- [Live Copies](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) - Live Copy with its Blueprint-->
* [Starts](/help/sites-cloud/authoring/launches/editing.md#comparing-a-launch-page-to-its-source-page) - Start mit der Quelle
* Language Copies - A page before and after (re-)translation <!-- [Language Copies](/help/sites-administering/tc-manage.md#comparing-language-copies) - A page before and after (re-)translation-->

Informieren Sie sich unter den entsprechenden Themen, wie der Seitenvergleich im gegebenen Zusammenhang verwendet wird.

### Darstellung von Unterschieden {#presentation-of-differences}

Unabhängig vom verglichenen Inhalt bleibt die Darstellung der Unterschiede gleich.

* Nachdem Sie den Seitenvergleich gestartet haben, wird der ausgewählte Inhalt auf der linken Seite angezeigt (der Differenzeinstiegspunkt).
* Rechts wird der zu vergleichende Inhalt angezeigt (der mit dem ausgewählten Inhalt verglichen wird).

Wenn Sie z. B. Versionen vergleichen, wird die aktuelle Version auf der linken Seite und die Vorversion auf der rechten Seite angezeigt.

Die Quelle beider Seiten wird deutlich in der Kopfzeile am oberen Rand des Browserfensters angezeigt.

![Versionen nebeneinander](/help/sites-cloud/authoring/assets/versions-side-by-side.png)

Der Seitenvergleich erkennt Änderungen an der Komponente und der HTML-Ebene. Geänderte Elemente werden mit verschiedenen Farben hervorgehoben.

**Komponentenänderungen**

* Hellgrün – Komponente hinzugefügt
* Rosa – Komponente entfernt
* Blau – Komponente geändert
* Blau – Komponente verschoben

Hinweis: Die Farben für geänderte und verschobene Elemente sind identisch.

**HTML-Änderungen** 

* Dunkelgrün – HTML hinzugefügt
* Rot - HTML entfernt

>[!NOTE]
>
>Beim Vergleich von Sprachkopien ist die Hervorhebung deaktiviert, da sich in einer Übersetzung alles ändert und Hervorhebung nutzlos wäre.

### Vollbild und Beenden {#fullscreen-and-exiting}

Damit Sie sich auf einen bestimmten Inhalt konzentrieren können, haben Sie die Möglichkeit, auf jeder Seite des Seitenvergleichs auf das Vollbildsymbol zu klicken, um die Ansicht auf das ganze Browserfenster zu vergrößern.

![Schaltfläche &quot;Vollbild&quot;](/help/sites-cloud/authoring/assets/versions-full-screen.png)

Die gewählte Seite füllt dann das gesamte Fenster aus, aber die Leiste am oberen Rand bleibt weiterhin angezeigt und bietet Ihnen die Möglichkeit, zwischen den zwei Seiten zu wechseln.

![Vollbildmodus](/help/sites-cloud/authoring/assets/versions-full-screen-mode.png)

>[!NOTE]
>
>Wenn die Browserbreite nicht für beide Seitennamen in der Vollbildansicht geeignet ist, wird nur der Name der angezeigten Seite angezeigt und der andere hinter der Auslassungszeichen.

Sie können die Vollbildansicht auch schließen, indem Sie auf das Symbol „Vollbildmodus beenden“ klicken.

![Vollbildmodus verlassen](/help/sites-cloud/authoring/assets/versions-exit-full-screen.png)

Sie können den Seitenvergleich jederzeit beenden, indem Sie in der Kopfzeile auf die Schaltfläche „Schließen“ klicken.

## Beschränkungen {#limitations}

In manchen Fällen erkennt der Seitenvergleich einen Unterschied nicht wie erwartet.

* Beim Vergleich von Versionen und Launches berücksichtigt der Seitenvergleich keine dynamischen Komponenten wie Breadcrumbs, Menüs, Produktlisten oder Logos (Komponenten, die die Site-Struktur zur Darstellung ihres Inhalts nutzen).
* Bei Versionen erstellt der Seitenvergleich die Richtlinien zur Zugriffssteuerung und die Live Copy-Beziehungen nicht neu.
* Wenn Änderungen an einem Bild vorgenommen werden, z. B. Änderungen an den Attributen &quot;alt&quot;, &quot;title&quot;oder &quot;src&quot;, wird es blau hervorgehoben, sobald es geändert wurde. In einigen Fällen hat das Bild jedoch eine Base64-Darstellung des Attributs src, und auch wenn beide Bilder gleich aussehen, werden sie aufgrund der unterschiedlichen src-Attribute vom Diff als verschieden gekennzeichnet.
* Der Seitenvergleich erkennt keine Bilddrehung.
* Wenn eine Seite verschoben wird, können Sie keinen Vergleich mit Versionen mehr durchführen, die vor dem Verschieben erstellt wurden.
   * Wenn Probleme beim Vergleich auftreten, überprüfen Sie in der [Timeline](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

>[!NOTE]
>
>Versionen können nicht miteinander verglichen werden. Nur die aktuelle Version kann mit anderen Versionen der Seite verglichen werden. Die aktuelle Version ist immer die Version, deren Änderungen hervorgehoben sind.

>[!NOTE]
>
>For more details about the operation of the page diff mechanism as well as limitations which can affect page diff, please see the developer documentation of this feature. <!-- For more details about the operation of the page diff mechanism as well as limitations which can affect page diff, please see the [developer documentation](/help/sites-developing/pagediff.md) of this feature.-->
