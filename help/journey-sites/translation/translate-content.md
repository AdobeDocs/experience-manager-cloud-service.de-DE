---
title: Inhalte übersetzen
description: Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Inhalte zu übersetzen.
index: true
hide: false
hidefromtoc: false
exl-id: b8ab2525-3f15-4844-866c-da47bfc7518c
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: ht
source-wordcount: '2598'
ht-degree: 100%

---

# Inhalte übersetzen {#translate-content}

Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Inhalte zu übersetzen.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Sites-Übersetzungs-Tour, [Übersetzungsregeln konfigurieren](translation-rules.md), haben Sie gelernt, wie Sie die Übersetzungsregeln von AEM verwenden, um Ihre zu übersetzenden Inhalte zu ermitteln. Sie sollten jetzt:

* Verstehen, was die Übersetzungsregeln bewirken.
* Eigene Übersetzungsregeln definieren können.

Nachdem Ihr Connector und die Übersetzungsregeln eingerichtet sind, führt Sie dieser Artikel durch den nächsten Schritt zur Übersetzung Ihrer AEM Sites-Inhalte.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie AEM-Übersetzungsprojekte zusammen mit dem Connector und Ihren Übersetzungsregeln verwenden können, um Inhalte zu übersetzen. Nach Lesen dieses Dokuments sollten Sie Folgendes können:

* verstehen, was ein Übersetzungsprojekt ist.
* neue Übersetzungsprojekte erstellen können.
* Verwenden Sie Übersetzungsprojekte, um Ihre AEM Sites-Inhalte zu übersetzen.

## Übersetzungsprojekt erstellen {#creating-translation-project}

Mithilfe von Übersetzungsprojekten können Sie die Übersetzung von AEM-Inhalten verwalten. Ein Übersetzungsprojekt sammelt die zu übersetzenden Inhalte an einem Ort, um einen zentralen Überblick über den Übersetzungsaufwand zu erhalten.

Wenn einem Übersetzungsprojekt Inhalte hinzugefügt werden, wird ein Übersetzungsauftrag für sie erstellt. Aufträge beinhalten Befehle und Statusinformationen, mit denen Sie die Workflows für menschliche und maschinelle Übersetzungen, die für die Ressourcen ausgeführt werden, verwalten.

Übersetzungsprojekte können auf zwei Arten erstellt werden:

1. Wählen Sie den Sprachstamm der Inhalte aus und lassen Sie AEM das Übersetzungsprojekt automatisch basierend auf dem Inhaltspfad erstellen.
1. Erstellen Sie ein leeres Projekt und wählen Sie manuell den Inhalt aus, der zum Übersetzungsprojekt hinzugefügt werden soll.

Beide Ansätze unterscheiden sich in der Regel nur je nach der Rolle, die die Übersetzung durchführt:

* Der Übersetzungsprojekt-Manager (TPM) benötigt häufig die Flexibilität, die Inhalte manuell für das Übersetzungsprojekt auszuwählen.
* Wenn der Inhaltsverantwortliche auch für die Übersetzung verantwortlich ist, ist es oft einfacher, das Projekt anhand des ausgewählten Inhaltspfads automatisch durch AEM erstellen zu lassen.

Beide Ansätze werden in den folgenden Abschnitten beschrieben.

### Automatisches Erstellen eines Übersetzungsprojekts basierend auf dem Inhaltspfad {#automatically-creating}

Für Inhaltsverantwortliche, die auch für die Übersetzung verantwortlich sind, ist es oft einfacher, das Übersetzungsprojekt automatisch durch AEM erstellen zu lassen. So erstellt AEM automatisch ein Übersetzungsprojekt basierend auf Ihrem Inhaltspfad:

1. Gehen Sie zu **Navigation** > **Sites** und tippen oder klicken Sie auf Ihr Projekt.
1. Suchen Sie den Sprachstamm Ihres Projekts. Wenn Ihr Sprachstamm beispielsweise Englisch ist, `/content/<your-project>/en`.
   * Beachten Sie, dass vor der ersten Übersetzung die anderen Sprachordner leere Platzhalter sind. Diese werden normalerweise vom Inhaltsarchitekten erstellt.
1. Suchen Sie den Sprachstamm Ihres Projekts.
1. Tippen oder klicken Sie auf die Auswahlleiste und zeigen Sie den Bereich **Verweise** an.
1. Tippen oder klicken Sie auf **Sprachkopien**.
1. Aktivieren Sie das Kontrollkästchen **Sprachkopien**.
1. Erweitern Sie den Abschnitt **Sprachkopien aktualisieren** unten im Bereich „Verweise“.
1. Wählen Sie in der Dropdowm-Liste **Projekt** **Übersetzungsprojekt(e) erstellen** aus.
1. Geben Sie einen geeigneten Titel für Ihr Übersetzungsprojekt an.
1. Tippen oder klicken Sie auf **Aktualisieren**.

![Erstelle ein Übersetzungsprojekt](assets/create-translation-project.png)

Sie erhalten eine Nachricht, dass das Projekt erstellt wurde.

>[!NOTE]
>
>Es wird davon ausgegangen, dass die für die Übersetzungen erforderliche Sprachstruktur bereits im Rahmen der [Definition der Inhaltsstruktur erstellt wurde.](getting-started.md#content-structure) Dies sollte in Zusammenarbeit mit dem Inhaltsarchitekten erfolgen.
>
>Wenn die Sprachordner nicht vorzeitig erstellt werden, können Sie keine Sprachkopien wie in den vorherigen Schritten beschrieben erstellen.

### Manuelles Erstellen eines Übersetzungsprojekts durch Auswahl der Inhalte {#manually-creating}

Für Übersetzungsprojekt-Manager ist es oft erforderlich, bestimmte Inhalte, die in ein Übersetzungsprojekt aufgenommen werden sollen, manuell auszuwählen. Um ein solches manuelles Übersetzungsprojekt zu erstellen, müssen Sie zunächst ein leeres Projekt erstellen und dann die hinzuzufügenden Inhalte auswählen.

1. Gehen Sie zu **Navigation** > **Projekte**.
1. Tippen oder klicken Sie auf **Erstellen** > **Ordner**, um einen Ordner für Ihre Projekte zu erstellen.
   * Dies ist optional, aber hilfreich, um Ihr Übersetzungsvorhaben zu organisieren.
1. Fügen Sie im Fenster **Projekt erstellen** einen **Titel** für den Ordner hinzu und tippen oder klicken Sie dann auf **Erstellen**.

   ![Projektordner erstellen](assets/create-project-folder.png)

1. Tippen oder klicken Sie auf den Ordner, um ihn zu öffnen.
1. Tippen oder klicken Sie in Ihrem neuen Projektordner auf **Erstellen** > **Projekt**.
1. Projekte basieren auf Vorlagen. Tippen oder klicken Sie auf die Vorlage für das **Übersetzungsprojekt**, um sie auszuwählen und tippen oder klicken Sie auf **Weiter**.

   ![Übersetzungsprojekt-Vorlage auswählen](assets/select-translation-project-template.png)

1. Geben Sie auf der Registerkarte **Allgemein** einen Namen für Ihr neues Projekt ein.

   ![Registerkarte „Standard“ des Projekts](assets/project-basic-tab.png)

1. Verwenden Sie auf der Registerkarte **Erweitert** die Dropdown-Liste **Zielsprache**, um die Sprache auszuwählen, in die die Inhalte übersetzt werden sollen. Tippen oder klicken Sie auf **Erstellen**.

   ![Registerkarte „Erweitert“ des Projekts](assets/project-advanced-tab.png)

1. Tippen oder klicken Sie im Bestätigungsdialog auf **Öffnen**.

   ![Bestätigungsdialog des Projekts](assets/project-confirmation-dialog.png)

Das Projekt wurde erstellt, enthält jedoch keine zu übersetzenden Inhalte. Im nächsten Abschnitt wird beschrieben, wie das Projekt strukturiert ist und wie man Inhalte hinzufügt.

## Verwenden eines Übersetzungsprojekts {#using-translation-project}

Übersetzungsprojekte dienen dazu, alle Inhalte und Aufgaben im Zusammenhang mit einem Übersetzungsvorhaben an einem Ort zu sammeln, um Ihre Übersetzung einfach zu verwalten.

So zeigen Sie das Übersetzungsprojekt an:

1. Gehen Sie zu **Navigation** > **Projekte**.
1. Tippen oder klicken Sie auf das Projekt, das im vorherigen Abschnitt erstellt wurde (entweder [Automatisches Erstellen eines Übersetzungsprojekts basierend auf dem Inhaltspfad](#automatically-creating) oder [Manuelles Erstellen eines Übersetzungsprojekts durch Auswahl der Inhalte](#manually-creating) abhängig von Ihrer Situation).

![Übersetzungsprojekt](assets/translation-project.png)

Das Projekt ist in mehrere Karten unterteilt.

* **Zusammenfassung**: Diese Karte zeigt die grundlegenden Kopfzeileninformationen des Projekts, einschließlich des Verantwortlichen, der Sprache und des Übersetzungsdienstleisters.
* **Übersetzungsauftrag**: Diese Karte bzw. diese Karten bieten einen Überblick über den tatsächlichen Übersetzungsauftrag, einschließlich Status, Anzahl der Assets usw. Im Allgemeinen gibt es pro Sprache einen Auftrag, wobei der ISO-2-Sprachcode an den Auftragsnamen angehängt wird.
   * Beachten Sie, dass AEM bei der [automatischen Erstellung von Übersetzungsaufträgen](#automatically-creating) die Aufträge asynchron erstellt und sie möglicherweise nicht sofort im Projekt erscheinen.
* **Team**: Auf dieser Karte werden die Benutzer angezeigt, die an diesem Übersetzungsprojekt mitarbeiten. Diese Tour behandelt dieses Thema nicht.
* **Aufgaben**: Zusätzliche Aufgaben im Zusammenhang mit der Übersetzung des Inhalts, z. B. zum Ausführen von Elementen oder Workflow-Elementen. Diese Tour behandelt dieses Thema nicht.

Um den Übersetzungsfluss in AEM besser zu verstehen, ist eine Änderung an den Projekteinstellungen nützlich. Dieser Schritt ist nicht für Produktionsübersetzungen erforderlich, sondern hilft beim Verständnis des Prozesses.

1. Tippen oder klicken Sie unten auf der Karte **Zusammenfassung** auf die Schaltfläche mit den Auslassungspunkten.
1. Deaktivieren Sie auf der Registerkarte **Erweitert** die Option **Launch nach Weiterleitung löschen**.

   ![Launch nach der Weiterleitung löschen](assets/delete-launch-option.png)

1. Tippen oder klicken Sie auf **Speichern und schließen**.

Jetzt können Sie Ihr Übersetzungsprojekt verwenden. Wie Sie ein Übersetzungsprojekt verwenden, hängt davon ab, wie es erstellt wurde: entweder automatisch durch AEM oder manuell.

### Verwenden eines automatisch erstellten Übersetzungsprojekts {#using-automatic-project}

Beim automatischen Erstellen des Übersetzungsprojekts bewertet AEM die Inhalte unter dem von Ihnen ausgewählten Pfad anhand der zuvor definierten Übersetzungsregeln. Basierend auf dieser Auswertung extrahiert es den Inhalt, der übersetzt werden muss, in ein neues Übersetzungsprojekt.

So sehen Sie die Details der in diesem Projekt enthaltenen Inhalte:

1. Tippen oder klicken Sie unten auf der Karte **Übersetzungsauftrag** auf die Schaltfläche mit den Auslassungspunkten.
1. Das Fenster **Übersetzungsauftrag** listet alle Elemente des Auftrags auf.

   ![Details des Übersetzungsauftrags](assets/translation-job-detail.png)

1. Tippen oder klicken Sie auf eine Zeile, um die Details dieser Zeile anzuzeigen. Dabei ist zu beachten, dass eine Zeile mehrere zu übersetzende Inhaltselemente darstellen kann.
1. Tippen oder klicken Sie auf das Auswahl-Kontrollkästchen für ein Zeilenelement, um weitere Optionen anzuzeigen, z. B. die Option, es aus dem Auftrag zu löschen oder es in der Sites-Konsole anzuzeigen.

   ![Optionen für Übersetzungsaufträge](assets/translation-job-options.png)

Normalerweise beginnt der Inhalt für den Übersetzungsauftrag im Status **Entwurf**, entsprechend den Angaben in der Spalte **Status** im Fenster **Übersetzungsauftrag**.

Um den Übersetzungsauftrag zu starten, kehren Sie zur Übersicht des Übersetzungsprojekts zurück und tippen oder klicken Sie auf die Pfeil-Schaltfläche oben in der Karte **Übersetzungsauftrag** und wählen Sie **Starten** aus.

![Übersetzungsauftrag starten](assets/start-translation-job.png)

AEM kommuniziert nun mit Ihrer Übersetzungskonfiguration und dem Connector, um den Inhalt an den Übersetzungsdienstleister zu senden. Sie können den Fortschritt der Übersetzung sehen, indem Sie zum Fenster **Übersetzungsauftrag** zurückgehen und die Spalte **Status** der Einträge anzeigen.

![Übersetzungsauftrag genehmigt](assets/translation-job-approved.png)

Maschinelle Übersetzungen werden automatisch mit dem Status **Genehmigt** zurückgegeben. Die menschliche Übersetzung ermöglicht mehr Interaktion, aber das würde den Rahmen dieser Tour sprengen.

>[!TIP]
>
>Die Verarbeitung eines Übersetzungsauftrags kann einige Zeit in Anspruch nehmen. Möglicherweise wechseln Ihre Übersetzungselemente vom Status **Entwurf** nach **Übersetzung läuft** und zu **Bereit zur Überprüfung**, bevor sie den Status **Genehmigt** erhalten. Dies ist zu erwarten.

>[!NOTE]
>
>Wenn Sie die Projektoption **Launch nach Weiterleitung löschen** nicht deaktiviert haben, wie [im vorherigen Abschnitt beschrieben,](#using-translation-project) erscheinen übersetzte Elemente mit dem Status **Gelöscht**. Dies ist normal, da AEM die Übersetzungseinträge automatisch verwirft, sobald die übersetzten Elemente eintreffen. Die übersetzten Elemente wurden als Sprachkopien importiert, nur die Übersetzungseinträge wurden gelöscht, da sie nicht mehr benötigt werden.
>
>Machen Sie sich keine Gedanken, wenn das unklar ist. Dies sind ausführliche Details, wie AEM funktioniert und beeinflussen nicht Ihr Verständnis der Tour. Wenn Sie mehr darüber erfahren möchten, wie AEM Übersetzungen verarbeitet, lesen Sie bitte den Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Artikels.

### Verwenden eines manuell erstellten Übersetzungsprojekts {#using-manual-project}

Beim manuellen Erstellen eines Übersetzungsprojekts erstellt AEM die erforderlichen Aufträge, wählt jedoch nicht automatisch die Inhalte aus, die in diese Aufträge aufgenommen werden sollen. Dadurch kann der Übersetzungsprojekt-Manager flexibel entscheiden, welche Inhalte übersetzt werden sollen.

So fügen Sie einem Übersetzungsauftrag Inhalte hinzu:

1. Tippen oder klicken Sie auf die Schaltfläche mit den Auslassungszeichen unten in einer der Karten **Übersetzungsauftrag**.
1. Stellen Sie sicher, dass der Auftrag keine Inhalte enthält. Tippen oder klicken Sie auf die Schaltfläche **Hinzufügen** oben im Fenster und wählen Sie dann aus der Dropdown-Liste **Assets/Seiten** aus.

   ![Leerer Übersetzungsauftrag](assets/empty-translation-job.png)

1. Ein Pfad-Browser wird geöffnet, in dem Sie auswählen können, welche Inhalte hinzugefügt werden sollen. Suchen Sie Ihre Inhalte und tippen oder klicken Sie zur Auswahl darauf.

   ![Pfad-Browser](assets/path-browser.png)

1. Tippen oder klicken Sie auf **Auswählen**, um die ausgewählten Inhalte zum Auftrag hinzuzufügen.
1. Geben Sie im Dialogfeld **Übersetzen** an, dass Sie eine **Sprachkopie erstellen** möchten.

   ![Sprachkopie erstellen](assets/translate-copy-master.png)

1. Die Inhalte sind jetzt im Auftrag enthalten.

   ![Zum Übersetzungsauftrag hinzugefügte Inhalte](assets/content-added.png)

1. Tippen oder klicken Sie auf das Auswahl-Kontrollkästchen für ein Zeilenelement, um weitere Optionen anzuzeigen, z. B. die Option, es aus dem Auftrag zu löschen oder es in der Sites-Konsole anzuzeigen.

   ![Optionen für Übersetzungsaufträge](assets/translation-job-options.png)

1. Wiederholen Sie diese Schritte, um alle erforderlichen Inhalte in den Auftrag einzuschließen.

>[!TIP]
>
>Der Pfad-Browser ist ein leistungsstarkes Tool, mit dem Sie Inhalte suchen, filtern und darin navigieren können. Tippen oder klicken Sie auf die Schaltfläche **Nur Inhalt/Filter** zum Umschalten des Seitenbereichs und zum Einblenden erweiterter Filter wie **Änderungsdatum** oder **Übersetzungsstatus**.
>
>Weitere Informationen zum Pfad-Browser finden Sie im [Abschnitt mit zusätzlichen Ressourcen.](#additional-resources)

Sie können die vorherigen Schritte verwenden, um die erforderlichen Inhalte zu allen Sprachen (Aufträgen) für das Projekt hinzuzufügen. Nachdem Sie alle Inhalte ausgewählt haben, können Sie mit der Übersetzung beginnen.

Normalerweise beginnt der Inhalt für den Übersetzungsauftrag im Status **Entwurf**, entsprechend den Angaben in der Spalte **Status** im Fenster **Übersetzungsauftrag**.

Um den Übersetzungsauftrag zu starten, kehren Sie zur Übersicht des Übersetzungsprojekts zurück und tippen oder klicken Sie auf die Pfeil-Schaltfläche oben in der Karte **Übersetzungsauftrag** und wählen Sie **Starten** aus.

![Übersetzungsauftrag starten](assets/start-translation-job.png)

AEM kommuniziert nun mit Ihrer Übersetzungskonfiguration und dem Connector, um den Inhalt an den Übersetzungsdienstleister zu senden. Sie können den Fortschritt der Übersetzung sehen, indem Sie zum Fenster **Übersetzungsauftrag** zurückgehen und die Spalte **Status** der Einträge anzeigen.

![Übersetzungsauftrag genehmigt](assets/translation-job-approved.png)

Maschinelle Übersetzungen werden automatisch mit dem Status **Genehmigt** zurückgegeben. Die menschliche Übersetzung ermöglicht mehr Interaktion, aber das würde den Rahmen dieser Tour sprengen.

>[!TIP]
>
>Die Verarbeitung eines Übersetzungsauftrags kann einige Zeit in Anspruch nehmen. Möglicherweise wechseln Ihre Übersetzungselemente vom Status **Entwurf** nach **Übersetzung läuft** und zu **Bereit zur Überprüfung**, bevor sie den Status **Genehmigt** erhalten. Dies ist zu erwarten.

>[!NOTE]
>
>Wenn Sie die Projektoption **Launch nach Weiterleitung löschen** nicht deaktiviert haben, wie [im vorherigen Abschnitt beschrieben,](#using-translation-project) erscheinen übersetzte Elemente mit dem Status **Gelöscht**. Dies ist normal, da AEM die Übersetzungseinträge automatisch verwirft, sobald die übersetzten Elemente eintreffen. Die übersetzten Elemente wurden als Sprachkopien importiert, nur die Übersetzungseinträge wurden gelöscht, da sie nicht mehr benötigt werden.
>
>Machen Sie sich keine Gedanken, wenn das unklar ist. Dies sind ausführliche Details, wie AEM funktioniert und beeinflussen nicht Ihr Verständnis der Tour. Wenn Sie mehr darüber erfahren möchten, wie AEM Übersetzungen verarbeitet, lesen Sie bitte den Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Artikels.

## Überprüfen übersetzter Inhalte {#reviewing}

[Wie bereits erwähnt,](#using-translation-project) fließen maschinell übersetzte Inhalte mit dem Status **Genehmigt** zurück in AEM, da davon ausgegangen wird, dass aufgrund der maschinellen Übersetzung kein menschliches Eingreifen erforderlich ist. Natürlich ist es noch möglich, die übersetzten Inhalte zu überprüfen.

Wechseln Sie einfach zum abgeschlossenen Übersetzungsauftrag und wählen Sie ein Zeilenelement aus, indem Sie auf das Kontrollkästchen tippen oder klicken. Das Symbol **Vorschau in Sites** wird in der Symbolleiste angezeigt.

![In Sites einblenden](assets/reveal-in-sites.png)

Tippen oder klicken Sie auf dieses Symbol, um die übersetzten Inhalte in der Konsole zu öffnen und die Details der übersetzten Inhalte anzuzeigen.

![Eine übersetzte Seite](assets/translated-page.png)

Sie können die übersetzten Inhalte nötigenfalls weiter verändern, vorausgesetzt Sie verfügen über die entsprechenden Berechtigungen, aber die Bearbeitung von Inhalten sprengt den Rahmen dieser Tour. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

Ziel des Projekts ist es, alle Ressourcen, die mit einer Übersetzung verbunden sind, an einem Ort zu sammeln, um einen einfachen Zugriff und einen klaren Überblick zu erhalten. Wie Sie jedoch sehen können, indem Sie die Details eines übersetzten Elements anzeigen, fließen die Übersetzungen selbst zurück in den Sites-Ordner der Übersetzungssprache. In diesem Beispiel lautet der Ordner

```text
/content/<your-project>/es
```

Wenn Sie über **Navigation** > **Sites** zu diesem Ordner gehen, sehen Sie die übersetzten Inhalte.

![Struktur der Ordner mit übersetzten Inhalten](assets/translated-sites-content.png)

Das AEM-Übersetzungs-Framework erhält die Übersetzungen vom Übersetzungs-Connector und erstellt dann automatisch die Inhaltsstruktur basierend auf dem Sprachstamm und unter Verwendung der vom Connector bereitgestellten Übersetzungen.

Es ist wichtig zu verstehen, dass diese Inhalte nicht veröffentlicht werden und daher nicht für den Verbrauch verfügbar sind. Im nächsten Schritt der Übersetzungs-Tour lernen wir diese Autoren- und Veröffentlichungstruktur kennen und erfahren, wie wir unsere übersetzten Inhalte veröffentlichen.

## Menschliche Übersetzung {#human-translation}

Wenn Ihr Übersetzungsdienstleister menschliche Übersetzung bereitstellt, bietet der Überprüfungsprozess mehr Optionen. Übersetzungen gelangen beispielsweise mit dem Status **Entwurf** zurück in das Projekt und müssen manuell überprüft und genehmigt oder abgelehnt werden.

Die menschliche Übersetzung sprengt den Rahmen dieser Tour zur Lokalisierung. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments. Abgesehen von den zusätzlichen Validierungsoptionen ist der Workflow für menschliche Übersetzungen mit den maschinellen Übersetzungen identisch, wie in dieser Tour beschrieben.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM Sites-Übersetzungs-Tour abgeschlossen haben, sollten Sie:

* verstehen, was ein Übersetzungsprojekt ist.
* neue Übersetzungsprojekte erstellen können.
* Übersetzen Sie Ihre Inhalte mithilfe von Übersetzungsprojekten.

Bauen Sie auf diesem Wissen auf und setzen Sie Ihre AEM Sites-Übersetzungs-Tour fort, indem Sie als Nächstes das Dokument [Veröffentlichen von übersetzten Inhalten](publish-content.md) lesen, in dem Sie lernen, wie Sie Ihre übersetzten Inhalte veröffentlichen und wie Sie diese Übersetzungen aktualisieren, wenn sich Ihr Sprachstamminhalt ändert.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Übersetzungs-Tour voranzuschreiten, indem Sie das Dokument [Veröffentlichen von übersetzten Inhalten](publish-content.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Sie sind jedoch nicht erforderlich, um mit der Tour fortzufahren.

* [Verwalten von Übersetzungsprojekten](/help/sites-cloud/administering/translation/managing-projects.md) – Erfahren Sie mehr über die Einzelheiten von Übersetzungsprojekten und zusätzliche Funktionen wie Workflows für menschliche Übersetzung und mehrsprachige Projekte.
* [Autorenumgebung und Tools](/help/sites-cloud/authoring/fundamentals/environment-tools.md##path-selection) – AEM bietet verschiedene Mechanismen für die Organisation und Bearbeitung von Inhalten, einschließlich eines robusten Pfadbrowsers.
