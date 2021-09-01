---
title: Übersetzten Inhalt veröffentlichen
description: Erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und die Übersetzungen bei der Inhaltsaktualisierung aktualisieren können.
index: true
hide: false
hidefromtoc: false
source-git-commit: 6605349c698325d432479fac0253a6fd53d7f175
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 0%

---

# Übersetzten Inhalt veröffentlichen {#publish-content}

Erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und die Übersetzungen bei der Inhaltsaktualisierung aktualisieren können.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Journey für die AEM Headless-Übersetzung [Übersetzen von Inhalten,](configure-connector.md) haben Sie gelernt, wie Sie AEM Übersetzungsprojekte verwenden können, um Ihre Headless-Inhalte zu übersetzen. Sie sollten jetzt:

* Verstehen Sie, was ein Übersetzungsprojekt ist.
* Sie können neue Übersetzungsprojekte erstellen.
* Verwenden Sie Übersetzungsprojekte, um Ihre Headless Content zu übersetzen.

Nachdem Ihre erste Übersetzung abgeschlossen ist, führt Sie dieser Artikel durch den nächsten Schritt zur Veröffentlichung dieses Inhalts und dazu, wie Sie Ihre Übersetzungen aktualisieren können, da sich der zugrunde liegende Inhalt im Sprachstamm ändert.

## Ziele {#objective}

In diesem Dokument erfahren Sie, wie Sie Headless Content in AEM veröffentlichen und einen kontinuierlichen Workflow erstellen, um Ihre Übersetzungen auf dem neuesten Stand zu halten. Nach dem Lesen dieses Dokuments sollten Sie:

* Machen Sie sich mit dem Author-Publish-Modell von AEM vertraut.
* Erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen.
* Sie können ein kontinuierliches Aktualisierungsmodell für Ihre übersetzten Inhalte implementieren.

## AEM Author-Publish-Modell {#author-publish}

Bevor Sie Ihren Inhalt veröffentlichen, sollten Sie AEM Authoring-Publishing-Modell verstehen. Vereinfacht ausgedrückt: AEM unterteilt Benutzer des Systems in zwei Gruppen.

1. Diejenigen, die Inhalte und System erstellen und verwalten
1. Diejenigen, die die Inhalte aus dem System konsumieren

AEM ist daher physisch in zwei Instanzen unterteilt.

1. Die **author** -Instanz ist das System, in dem Inhaltsautoren und -administratoren Inhalte erstellen und verwalten.
1. Die **publish**-Instanz ist das System, das den Inhalt für die Verbraucher bereitstellt.

Sobald Inhalte in der Autoreninstanz erstellt wurden, müssen sie in die Veröffentlichungsinstanz übertragen werden, damit sie zur Verwendung verfügbar sind. Der Prozess der Übertragung von der Autoren- zur Veröffentlichungsinstanz heißt **Veröffentlichung**.

## Veröffentlichen der übersetzten Inhalte {#publishing}

Sobald Sie mit dem Status Ihrer übersetzten Inhalte zufrieden sind, müssen diese veröffentlicht werden, damit Headless Services sie nutzen können. Diese Aufgabe fällt normalerweise nicht in die Zuständigkeit des Übersetzungsanbieters, sondern wird hier dokumentiert, um den gesamten Workflow zu veranschaulichen.

>[!NOTE]
>
>Nach Abschluss der Übersetzung informiert der Übersetzungs-Spezialist den Inhaltsverantwortlichen im Allgemeinen, dass die Übersetzungen veröffentlicht werden können. Die Inhaltsverantwortlichen veröffentlichen sie dann.
>
>Die folgenden Schritte werden zur Vollständigkeit bereitgestellt.

Die einfachste Möglichkeit, die Übersetzungen zu veröffentlichen, besteht darin, zum Ordner mit den Projekt-Assets zu navigieren.

```text
/content/dam/<your-project>/
```

Unter diesem Pfad befinden sich Unterordner für jede Übersetzungssprache und können auswählen, welche veröffentlicht werden soll.

1. Navigieren Sie zu **Navigation** -> **Assets** -> **Dateien** und öffnen Sie den Projektordner.
1. Hier sehen Sie den Ordner für den Sprachstamm und alle anderen Sprachordner. Wählen Sie die zu veröffentlichenden lokalisierten Sprachen aus.
   ![Sprachordner auswählen](assets/select-language-folder.png)
1. Tippen oder klicken Sie auf **Veröffentlichung verwalten**.
1. Stellen Sie im Fenster **Veröffentlichung verwalten** sicher, dass **Veröffentlichen** automatisch unter **Aktion** ausgewählt ist und **Jetzt** unter **Planung** ausgewählt ist. Tippen oder klicken Sie auf **Weiter**.
   ![Veröffentlichungsoptionen verwalten](assets/manage-publication-options.png)
1. Vergewissern Sie sich im nächsten Fenster **Veröffentlichung verwalten**, dass der/die richtige(n) Pfad(e) ausgewählt ist/sind. Tippen oder klicken Sie auf **Publish**.
   ![Umfang der Veröffentlichung verwalten](assets/manage-publication-scope.png)
1. AEM bestätigt die Veröffentlichungsaktion mit einer Popup-Meldung am unteren Bildschirmrand.
   ![Veröffentlichte Ressourcen-Banner](assets/resources-published-message.png)

Ihr übersetzter Headless-Inhalt ist jetzt veröffentlicht! Sie können jetzt von Ihren Headless-Services darauf zugreifen und sie nutzen.

>[!TIP]
>
>Sie können bei der Veröffentlichung mehrere Elemente (d. h. mehrere Sprachordner) auswählen, um mehrere Übersetzungen gleichzeitig zu veröffentlichen.

Es gibt zusätzliche Optionen bei der Veröffentlichung Ihres Inhalts, z. B. die Planung einer Veröffentlichungszeit, die über den Rahmen dieser Journey hinausgehen. Weitere Informationen finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende des Dokuments.

## Aktualisieren Ihrer übersetzten Inhalte {#updating-translations}

Übersetzen ist selten eine einmalige Übung. In der Regel fügen Ihre Inhaltsautoren Ihren Inhalt im Sprachstamm weiter hinzu und ändern ihn, nachdem die Erstübersetzung abgeschlossen ist. Dies bedeutet, dass Sie auch Ihre übersetzten Inhalte aktualisieren müssen.

Spezifische Projektanforderungen definieren, wie oft Sie Ihre Übersetzungen aktualisieren müssen und welcher Entscheidungsprozess befolgt wird, bevor Sie eine Aktualisierung durchführen. Sobald Sie sich entschieden haben, Ihre Übersetzungen zu aktualisieren, ist der Prozess in AEM sehr einfach. Da die ursprüngliche Übersetzung auf einem Übersetzungsprojekt basierte, so auch alle Aktualisierungen.

Allerdings unterscheidet sich der Prozess geringfügig, wenn Sie Ihr Übersetzungsprojekt automatisch erstellen oder Ihr Übersetzungsprojekt manuell erstellen.

### Aktualisieren eines automatisch erstellten Übersetzungsprojekts {#updating-automatic-project}

1. Navigieren Sie zu **Navigation** -> **Assets** -> **Dateien**. Beachten Sie, dass Headless-Inhalte in AEM als Assets gespeichert werden, die als Inhaltsfragmente bezeichnet werden.
1. Wählen Sie den Sprachstamm Ihres Projekts aus. In diesem Fall haben wir `/content/dam/wknd/en` ausgewählt.
1. Tippen oder klicken Sie auf die Schienenauswahl und zeigen Sie das Bedienfeld **Verweise** an.
1. Tippen oder klicken Sie auf **Sprachkopien**.
1. Aktivieren Sie das Kontrollkästchen **Sprachkopien** .
1. Erweitern Sie den Abschnitt **Sprachkopien aktualisieren** unten im Bereich &quot;Verweise&quot;.
1. Wählen Sie im Dropdown-Menü **Projekt** die Option **Zu einem vorhandenen Übersetzungsprojekt hinzufügen** aus.
1. Wählen Sie im Dropdown-Menü **Vorhandenes Übersetzungsprojekt** das für die Erstübersetzung erstellte Projekt aus.
1. Tippen oder klicken Sie auf **Start**.

![Hinzufügen von Elementen zu einem vorhandenen Übersetzungsprojekt](assets/add-to-existing-project.png)

Der Inhalt wird zum vorhandenen Übersetzungsprojekt hinzugefügt. So zeigen Sie das Übersetzungsprojekt an:

1. Navigieren Sie zu **Navigation** -> **Projekte**.
1. Tippen oder klicken Sie auf das soeben aktualisierte Projekt.
1. Tippen oder klicken Sie auf die Sprache oder eine der Sprachen, die Sie aktualisiert haben.

Sie sehen, dass dem Projekt eine neue Auftragskarte hinzugefügt wurde. In diesem Beispiel wurde eine weitere spanische Übersetzung hinzugefügt.

![Zusätzlicher Übersetzungsauftrag hinzugefügt](assets/additional-translation-job.png)

Sie werden feststellen, dass die auf der neuen Karte aufgelisteten Statistiken (Anzahl der Assets und Inhaltsfragmente) unterschiedlich sind. Dies liegt daran, dass AEM erkennt, was sich seit der letzten Übersetzung geändert hat, und nur den Inhalt enthält, der übersetzt werden muss. Dazu gehören die Neuübersetzung aktualisierter Inhalte sowie die Erstübersetzung neuer Inhalte.

Ab diesem Zeitpunkt [Starten und verwalten Sie Ihren Übersetzungsauftrag genauso wie das Original.](translate-content.md#using-translation-project)

### Aktualisieren eines manuell erstellten Übersetzungsprojekts {#updating-manual-project}

Um eine Übersetzung zu aktualisieren, können Sie Ihrem vorhandenen Projekt einen neuen Auftrag hinzufügen, der für die Übersetzung der aktualisierten Inhalte verantwortlich ist.

1. Navigieren Sie zu **Navigation** -> **Projekte**.
1. Tippen oder klicken Sie auf das Projekt, das Sie aktualisieren müssen.
1. Tippen oder klicken Sie oben im Fenster auf die Schaltfläche **Hinzufügen** .
1. Tippen oder klicken Sie im Fenster **Kachel** hinzufügen auf **Übersetzungsauftrag** und dann auf **Senden**.

   ![Kachel hinzufügen](assets/add-translation-job-tile.png)

1. Tippen oder klicken Sie auf der Karte des neuen Übersetzungsauftrags oben auf der Karte auf die Pfeilschaltfläche und wählen Sie **Ziel aktualisieren** aus, um die Zielsprache des neuen Auftrags zu definieren.

   ![Ziel aktualisieren](assets/update-target.png)

1. Wählen Sie im Dialogfeld **Wählen Sie Zielsprache** aus, wählen Sie die Sprache aus der Dropdown-Liste aus und tippen oder klicken Sie auf **Fertig**.

   ![Zielsprache auswählen](assets/select-target-language.png)

1. Sobald die Zielsprache Ihres neuen Übersetzungsauftrags festgelegt ist, tippen oder klicken Sie unten auf der Auftragskarte auf die Suchschaltfläche , um die Details des Auftrags anzuzeigen.
1. Der Auftrag ist beim ersten Erstellen leer. Fügen Sie Inhalte zum Auftrag hinzu, indem Sie auf die Schaltfläche **Hinzufügen** tippen oder klicken und den Pfad-Browser [verwenden, wie Sie es bei der ursprünglichen Erstellung des Übersetzungsprojekts getan haben.](translate-content.md##manually-creating)

>[!TIP]
>
>Die leistungsstarken Filter des Pfad-Browsers können wieder nützlich sein, um nur den aktualisierten Inhalt zu finden.
>
>Weitere Informationen zum Pfad-Browser finden Sie im Abschnitt [Zusätzliche Ressourcen .](#additional-resources)

Ab diesem Zeitpunkt [Starten und verwalten Sie Ihren Übersetzungsauftrag genauso wie das Original.](translate-content.md#using-translation-project)

## Ende der Journey? {#end-of-journey}

Herzlichen Glückwunsch! Sie haben die Headless-Übersetzungs-Journey abgeschlossen! Sie sollten jetzt:

* Verschaffen Sie sich einen Überblick darüber, was die Headless Content-Bereitstellung ist.
* Verstehen Sie AEM Headless-Funktionen.
* Verstehen Sie AEM Übersetzungsfunktionen und deren Zusammenhang mit Headless Content.
* Sie haben die Möglichkeit, Ihre eigenen Headless Content zu übersetzen.

Jetzt können Sie Ihre eigenen Headless Content in AEM übersetzen. AEM ist jedoch ein leistungsstarkes Tool und es gibt viele zusätzliche Optionen. Sehen Sie sich einige der zusätzlichen Ressourcen an, die im Abschnitt [Zusätzliche Ressourcen](#additional-resources) verfügbar sind, um mehr über die Funktionen zu erfahren, die Sie auf dieser Journey gesehen haben.

## Zusätzliche Ressourcen {#additional-resources}

* [Verwalten von Übersetzungsprojekten](/help/sites-cloud/administering/translation/managing-projects.md)  - Erfahren Sie mehr über die Details von Übersetzungsprojekten und zusätzliche Funktionen wie Workflows für menschliche Übersetzung und Projekte mit mehreren Sprachen.
* [Authoring-Konzepte](/help/sites-cloud/authoring/getting-started/concepts.md)  - Erfahren Sie mehr über das Autoren- und Veröffentlichungsmodell von AEM. Dieses Dokument konzentriert sich nicht auf Inhaltsfragmente, sondern auf das Erstellen von Seiten, aber die Theorie gilt weiterhin.
* [Seiten veröffentlichen](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)  - Erfahren Sie mehr über die zusätzlichen Funktionen, die beim Veröffentlichen von Inhalten verfügbar sind. Dieses Dokument konzentriert sich nicht auf Inhaltsfragmente, sondern auf das Erstellen von Seiten, aber die Theorie gilt weiterhin.
* [Authoring-Umgebung und Tools](/help/sites-cloud/authoring/fundamentals/environment-tools.md##path-selection)  - AEM bietet verschiedene Mechanismen für die Organisation und Bearbeitung von Inhalten, einschließlich eines robusten Pfad-Browsers.
