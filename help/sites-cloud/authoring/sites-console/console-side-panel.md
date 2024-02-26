---
title: Seitenbereich der Sites-Konsole
description: Erfahren Sie, wie Sie den Seitenbereich in der Konsole AEM Sites verwenden können, um Ihre Inhalte besser zu verstehen und zu navigieren.
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 23%

---


# Seitenbereich der Sites-Konsole {#side-panel}

Erfahren Sie, wie Sie den Seitenbereich im AEM verwenden **Sites** -Konsole, um Ihre Inhalte besser zu verstehen und darin zu navigieren.

## Ausrichtung {#orientation}

Der Seitenbereich wird standardmäßig geschlossen, wenn Sie die **Sites** Konsole. Auf diese Weise wird der Bildschirm vollständig Ihren Inhalten gewidmet.

Tippen oder klicken Sie auf **Seitenbereich** im **Sites** Konsolensymbolleiste, um das Seitenbedienfeld zu aktivieren und Ihre Ansicht des Inhalts auszuwählen.

* [Nur Inhalte](#content-only)
* [Inhaltsstruktur](#content-tree)
* [Zeitleiste](#timeline)
* [Verweise](#references)
* [Site](#site)
* [Filter](#filter)
* [Analytics einrichten](#setup-analytics)

![Seitenansichten der Sites-Konsole](assets/sites-console-side-panel-views.png)

Die aktuell ausgewählte Ansicht wird durch ein blaues Häkchen in der Dropdown-Liste gekennzeichnet und das Seitensymbol in der Symbolleiste wird mit dem Namen der ausgewählten Ansicht aktualisiert.

## Nur Inhalte {#content-only}

Mit dieser Ansicht des Seitenbereichs wird es effektiv deaktiviert, d. h. es wird nur der Inhalt Ihrer Site angezeigt.

>[!TIP]
>
>Gravis/Backtick verwenden `´` Tastaturbefehl, um zur Ansicht &quot;Nur Inhalt&quot;des Seitenbereichs zu wechseln.

## Inhaltsstruktur {#content-tree}

Diese Ansicht des Seitenbereichs zeigt Ihren Inhalt in einer Baumstruktur an. Die Inhaltsstruktur kann verwendet werden, um schnell in der Site-Hierarchie im Seitenbereich zu navigieren und viele Informationen über die Seiten im aktuellen Ordner anzuzeigen.

![Die Inhaltsbaumansicht des Seitenbereichs](assets/console-side-panel-content-tree.png)

Ein nach rechts zeigender Pfeil neben einem Element im Baum zeigt einen Knoten an, der erweitert werden kann, um seine untergeordneten Elemente anzuzeigen. Tippen oder klicken Sie auf den Pfeil, um die untergeordneten Elemente anzuzeigen.

Die Konsole zeigt den Inhalt des aktuell ausgewählten Elements in der Inhaltsstruktur an.

Mithilfe des Seitenbereichs der Inhaltsstruktur in Verbindung mit einer Listen- oder Kartenansicht können Sie die hierarchische Struktur des Projekts einfach erkennen, mit dem Seitenbereich der Inhaltsstruktur einfach durch die Inhaltsstruktur navigieren und detaillierte Seiteninformationen in der Listenansicht anzeigen.

>[!TIP]
>
>* Verwenden Sie die `Alt+1` Tastaturbefehl, um zur Inhaltsbaumansicht des Seitenbereichs zu wechseln.
>* Sobald ein Eintrag in der Hierarchieansicht ausgewählt ist, können Sie mithilfe der Pfeiltasten schnell in der Hierarchie navigieren.
>* Weitere Informationen finden Sie unter [Tastaturbefehle](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md).

## Zeitleiste {#timeline}

Die Timeline kann verwendet werden, um Ereignisse anzuzeigen, die die ausgewählte Ressource beeinflusst haben. Sie können damit auch bestimmte Ereignisse wie Workflows oder Versionen starten.

![Zeitleisten-Details](/help/sites-cloud/authoring/assets/timeline-detail.png)

Die **Timeline** im seitlichen Bedienfeld können Sie verschiedene Ereignisse im Zusammenhang mit einem ausgewählten Element anzeigen, die als Typen aus einer Dropdown-Liste ausgewählt werden können:

* Kommentare
* [Anmerkungen](/help/sites-cloud/authoring/page-editor/annotations.md)
* [Aktivitäten](/help/sites-cloud/authoring/personalization/activities.md)
* [Launches](/help/sites-cloud/authoring/launches/overview.md)
* [Versionen](/help/sites-cloud/authoring/sites-console/page-versions.md)
* [Workflows](/help/sites-cloud/authoring/workflows/overview.md)
   * Beachten Sie, dass für Verlaufs-Workflows keine Informationen angezeigt werden, da für diese keine Verlaufsinformationen gespeichert werden.<!--With the exception of [transient workflows](/help/sites-developing/workflows.md#transient-workflows) as no history information is saved for these-->
* Alles anzeigen

Darüber hinaus können Sie Kommentare zum ausgewählten Element hinzufügen/anzeigen, indem Sie die **Kommentar** unten in der Ereignisliste angezeigt. Geben Sie einen Kommentar ein, gefolgt von `Return` registriert den Kommentar. Es wird angezeigt, wenn **Kommentare** oder **Alle anzeigen** ausgewählt ist.

Im **Sites** -Konsole können Sie auch über die Suchschaltfläche neben **Kommentar** -Feld.

* [eine Version speichern](/help/sites-cloud/authoring/sites-console/page-versions.md)
* [einen Workflow starten](/help/sites-cloud/authoring/workflows/applying.md)

![Kommentarfeld für die Sites-Konsole](assets/sites-console-comment-ellipsis.png)

>[!TIP]
>
>* Verwenden Sie die `Alt+2` Tastaturbefehl, um zur Timeline-Ansicht des Seitenbereichs zu wechseln.
>* Weitere Informationen finden Sie unter [Tastaturbefehle](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md).

## Verweise {#references}

Die **Verweise** -Ansicht zeigt eine Liste der Verweistypen, von der auf die in der Konsole ausgewählte Ressource verweist.

![Verweisdetails](assets/console-side-panel-references-detail.png)

Wählen Sie den gewünschten Verweistyp, um weitere Informationen anzuzeigen: In bestimmten Situationen sind weitere Aktionen verfügbar, wenn Sie einen bestimmten Verweis auswählen:

* **Eingehende Links** bietet eine Liste der Seiten, die auf die Seite verweisen, sowie direkten Zugriff auf **Bearbeiten** eine dieser Seiten, wenn Sie einen bestimmten Link auswählen.
   * Dies kann nur statische Links anzeigen, nicht dynamisch generierte Links, z. B. aus der Listenkomponente.
* [Launches](/help/sites-cloud/authoring/launches/overview.md) bietet Zugriff auf zugehörige Launches.
* [Live Copies](/help/sites-cloud/administering/msm/overview.md) zeigt die Pfade aller Live Copies an, die auf der gewählten Ressource basieren.
* [Blueprint](/help/sites-cloud/administering/msm/best-practices.md) bietet Details und verschiedene Aktionen.
* [Sprachenkopien](/help/sites-cloud/administering/translation/managing-projects.md#creating-translation-projects-using-the-references-panel) bietet Details und verschiedene Aktionen

## Site {#site}

Die **Site** Ansicht des Seitenbereichs zeigt Details zu Sites an [mit einer Site-Vorlage erstellt wurde.](/help/sites-cloud/administering/site-creation/create-site.md)

![Site-Bereich](assets/console-side-panel-site-paenl.png)

Siehe Dokument . [Verwalten des Site-Designs mithilfe des Site-Bedienfelds](/help/sites-cloud/administering/site-creation/site-rail.md) Weitere Informationen dazu, wie Sie den Bereich zum Verwalten der [Design Ihrer Site.](/help/sites-cloud/administering/site-creation/site-themes.md).

Wenn Sie die Front-End-Pipeline noch nicht eingerichtet haben, um die themenbasierte Site-Erstellung zu aktivieren, bietet das Seitenbedienfeld diese Option an.

![Option zum Aktivieren der Front-End-Pipeline im Seitenbereich](assets/sites-console-side-panel-site.png)

>[!TIP]
>
>Eine vollständige Beschreibung des Prozesses zum Erstellen einer Site aus einer Vorlage und zum Anpassen ihres Designs finden Sie im Abschnitt [Tour zum Quick Site Creation](/help/journey-sites/quick-site/overview.md).

## Filter {#filter}

Die **Filter** ähnelt dem [Suchfunktion](/help/sites-cloud/authoring/search.md) mit den entsprechenden Ortsfiltern, die bereits festgelegt wurden, können Sie den Inhalt, den Sie anzeigen möchten, weiter filtern.

![Filterbeispiel](assets/console-side-panel-filter.png)

Im Gegensatz zu anderen Ansichten des Seitenbedienfelds können Sie durch Tippen oder Klicken auf die Schaltfläche `X` im Suchfeld.

## Analytics einrichten {#setup-analytics}

Mit dieser Ansicht können Sie Adobe Analytics für eine bestimmte Site schnell einrichten.

![Einrichten von Analytics](assets/sites-console-side-panel-setup-analytics.png)
