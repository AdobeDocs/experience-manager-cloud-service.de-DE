---
title: Inhalt übersetzen
description: Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Headless-Inhalte zu übersetzen.
source-git-commit: 016b1126effb96598c9700377291333fb326c292
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 3%

---

# Inhalt übersetzen {#translate-content}

Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Headless-Inhalte zu übersetzen.

## Was bisher geschah {#story-so-far}

Im vorherigen Dokument der Journey zur AEM Headless-Lokalisierung [Konfigurieren von Übersetzungsregeln](translation-rules.md) haben Sie gelernt, wie Sie AEM Übersetzungsregeln verwenden können, um Ihren Übersetzungsinhalt zu identifizieren. Sie sollten jetzt:

* Machen Sie sich mit den Übersetzungsregeln vertraut.
* Sie können Ihre eigenen Übersetzungsregeln definieren.

Nachdem Sie Ihre Regeln für Connector und Übersetzungen eingerichtet haben, führt Sie dieser Artikel durch den nächsten Schritt zur Übersetzung Ihrer Headless Content.

## Zielsetzung {#objective}

In diesem Dokument erfahren Sie, wie Sie AEM Übersetzungsprojekte zusammen mit dem Connector und Ihren Übersetzungsregeln verwenden können, um Inhalte zu übersetzen. Nach dem Lesen dieses Dokuments sollten Sie Folgendes tun:

* Verstehen Sie, was ein Übersetzungsprojekt ist.
* Sie können neue Übersetzungsprojekte erstellen.
* Verwenden Sie Übersetzungsprojekte, um Ihre Headless Content zu übersetzen.

## Erstellen eines Übersetzungsprojekts {#creating-translation-project}

Mithilfe von Übersetzungsprojekten können Sie die Übersetzung von Headless-AEM-Inhalten verwalten. Ein Übersetzungsprojekt enthält die Inhalte, die in andere Sprachen übersetzt werden sollen.

Wenn einem Übersetzungsprojekt Inhalte hinzugefügt werden, wird dafür ein Übersetzungsauftrag erstellt. Aufträge beinhalten Befehle und Statusinformationen, mit denen Sie die Workflows für menschliche und maschinelle Übersetzungen, die für die Ressourcen ausgeführt werden, verwalten.

So erstellen Sie ein Übersetzungsprojekt:

1. Navigieren Sie zu **Navigation** -> **Assets** -> **Dateien**. Beachten Sie, dass Headless-Inhalte in AEM als Assets gespeichert werden, die als Inhaltsfragmente bezeichnet werden.
1. Wählen Sie den Sprachstamm Ihres Projekts aus. In diesem Fall haben wir `/content/dam/wknd/en` ausgewählt.
1. Tippen oder klicken Sie auf die Schienenauswahl und zeigen Sie das Bedienfeld **Verweise** an.
1. Tippen oder klicken Sie auf **Sprachkopien**.
1. Aktivieren Sie das Kontrollkästchen **Sprachkopien** .
1. Erweitern Sie den Abschnitt **Sprachkopien aktualisieren** unten im Bereich &quot;Verweise&quot;.
1. Wählen Sie im Dropdown-Menü **Projekt** die Option **Übersetzungsprojekt(e)** erstellen.
1. Geben Sie einen geeigneten Titel für Ihr Übersetzungsprojekt an.
1. Tippen oder klicken Sie auf **Start**.

![Erstelle ein Übersetzungsprojekt](assets/create-translation-project.png)

Sie erhalten eine Nachricht, dass das Projekt erstellt wurde.

>[!NOTE]
>
>Es wird davon ausgegangen, dass die erforderliche Sprachstruktur für die Übersetzungssprachen bereits im Rahmen der [Definition Ihrer Inhaltsstruktur erstellt wurde.](getting-started.md#content-structure) Dies sollte in Zusammenarbeit mit dem Inhaltsarchitekten erfolgen.

## Verwenden eines Übersetzungsprojekts {#using-translation-project}

AEM hat beim Erstellen des Übersetzungsprojekts den Headless-Inhalt unter dem von Ihnen ausgewählten Pfad sowie anhand der zuvor definierten Regeln ausgewertet. Basierend auf diesen Regeln wurde der Inhalt extrahiert, der übersetzt werden muss, in ein neues Übersetzungsprojekt.

So zeigen Sie das Übersetzungsprojekt an:

1. Navigieren Sie zu **Navigation** -&amp; **Projekte**.
1. Tippen oder klicken Sie auf das Projekt, das im vorherigen Abschnitt erstellt wurde.

![Übersetzungsprojekt](assets/translation-project.png)

Das Projekt ist in mehrere Karten unterteilt.

* **Zusammenfassung**  - Diese Karte zeigt die grundlegenden Kopfzeileninformationen des Projekts, einschließlich des Eigentümers, der Sprache und des Übersetzungsanbieters.
* **Übersetzungsauftrag**  - Auf dieser Karte wird ein Überblick über den eigentlichen Übersetzungsauftrag einschließlich Status, Anzahl der Assets usw. angezeigt.
* **Team**  - Auf dieser Karte werden die Benutzer angezeigt, die an diesem Übersetzungsprojekt mitarbeiten. Diese Journey wird dieses Thema nicht behandeln.
* **Aufgaben**  - Zusätzliche Aufgaben im Zusammenhang mit der Übersetzung von Inhalten, z. B. zum Ausführen von Elementen oder Workflow-Elementen. Diese Journey wird dieses Thema nicht behandeln.

So sehen Sie die Details des Headless-Inhalts in diesem Projekt:

1. Tippen oder klicken Sie unten auf der Karte **Übersetzungsauftrag** auf die Suchschaltfläche mit Auslassungspunkten.
1. Im Fenster **Übersetzungsauftrag** werden alle Elemente des Auftrags aufgelistet.
   ![Detail des Übersetzungsauftrags](assets/translation-job-detail.png)
1. Tippen oder klicken Sie auf eine Zeile, um die Details dieser Zeile anzuzeigen. Dabei ist zu beachten, dass eine Zeile mehrere zu übersetzende Inhaltselemente darstellen kann.
1. Tippen oder klicken Sie auf das Auswahlkästchen für ein Zeilenelement, um weitere Optionen anzuzeigen, z. B. die Option, es aus dem Auftrag zu löschen oder in den Konsolen &quot;Inhaltsfragmente&quot;oder &quot;Assets&quot;anzuzeigen.

![Optionen für Übersetzungsaufträge](assets/translation-job-options.png)

Normalerweise beginnt der Inhalt für den Übersetzungsauftrag im Status **Entwurf** , wie in der Spalte **Status** im Fenster **Übersetzungsauftrag** angegeben.

Um den Übersetzungsauftrag zu starten, kehren Sie zur Übersicht des Übersetzungsprojekts zurück, tippen oder klicken Sie auf die Schaltfläche &quot;Chevron&quot;oben auf der Karte **Übersetzungsauftrag** und wählen Sie **Start** aus.

![Übersetzungsauftrag starten](assets/start-translation-job.png)

AEM kommuniziert nun mit Ihrer Übersetzungskonfiguration und Ihrem Connector, um den Inhalt an den Übersetzungsdienst zu senden. Sie können den Fortschritt der Übersetzung anzeigen, indem Sie zum Fenster **Übersetzungsauftrag** zurückkehren und die Spalte **Status** der Einträge anzeigen.

![Übersetzungsauftrag genehmigt](assets/translation-job-approved.png)

Maschinelle Übersetzungen werden automatisch mit dem Status **Genehmigt** zurückgegeben. Menschliche Übersetzung ermöglicht mehr Interaktion, ist aber über den Rahmen dieser Journey hinaus.

## Überprüfen übersetzter Inhalte {#reviewing}

[Wie bereits erwähnt, fließen ](#using-translation-project) maschinell übersetzte Inhalte zurück in AEM mit dem Status  **** Genehmigt , da die Annahme darin besteht, dass aufgrund der Verwendung der maschinellen Übersetzung keine menschliche Intervention erforderlich ist. Natürlich ist es noch möglich, die übersetzten Inhalte zu überprüfen.

Wechseln Sie einfach zum abgeschlossenen Übersetzungsauftrag und wählen Sie ein Zeilenelement aus, indem Sie auf das Kontrollkästchen tippen oder klicken. Das Symbol **In Inhaltsfragment einblenden** wird in der Symbolleiste angezeigt.

![In Inhaltsfragment einblenden](assets/reveal-in-content-fragment.png)

Tippen oder klicken Sie auf dieses Symbol, um das übersetzte Inhaltsfragment in der Editor-Konsole zu öffnen, um die Details des übersetzten Inhalts anzuzeigen.

![Ein übersetztes Inhaltsfragment](assets/translated-content-fragment.png)

Sie können das Inhaltsfragment nach Bedarf weiter ändern, vorausgesetzt Sie verfügen über die entsprechenden Berechtigungen, aber die Bearbeitung von Inhaltsfragmenten fällt nicht in den Geltungsbereich dieser Journey. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

Aufgabe des Projekts ist es, alle Ressourcen, die mit einer Übersetzung verbunden sind, an einem Ort zu sammeln, um einen einfachen Zugriff und einen klaren Überblick zu erhalten. Wie Sie jedoch sehen können, indem Sie die Details eines übersetzten Elements anzeigen, fließen die Übersetzungen selbst in den Asset-Ordner der Übersetzungssprache zurück. In unserem Beispiel hier

```text
/content/dam/wknd/es
```

Wenn Sie über **Navigation** -> **Dateien** -> **Assets** zu diesem Ordner navigieren, wird der übersetzte Inhalt angezeigt.

![Struktur übersetzter Inhaltsordner](assets/translated-file-content.png)

AEM Übersetzungs-Framework erhält die Übersetzungen vom Übersetzungs-Connector und erstellt dann automatisch die Inhaltsstruktur basierend auf dem Sprachstamm und unter Verwendung der vom Connector bereitgestellten Übersetzungen.

Es ist wichtig zu verstehen, dass dieser Inhalt nicht veröffentlicht wird. Er bleibt in der Authoring-Instanz von AEM, bis Sie sich entscheiden, dass er zur Veröffentlichung bereit ist. Wir werden sehen, wie dies im nächsten Schritt der Lokalisierungs-Journey durchgeführt wird.

## Menschliche Übersetzung {#human-translation}

Wenn Ihr Übersetzungsdienst menschliche Übersetzung bereitstellt, bietet der Überprüfungsprozess mehr Optionen. Übersetzungen gelangen beispielsweise wieder in das Projekt mit dem Status **Entwurf** und müssen überprüft und manuell genehmigt oder abgelehnt werden.

Die menschliche Übersetzung geht über den Rahmen dieser Journey zur Lokalisierung hinaus. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Headless-Lokalisierungs-Journey abgeschlossen haben, sollten Sie:

* Verstehen Sie, was ein Übersetzungsprojekt ist.
* Sie können neue Übersetzungsprojekte erstellen.
* Verwenden Sie Übersetzungsprojekte, um Ihre Headless Content zu übersetzen.

Auf diesem Wissen aufbauen und mit der Journey zur  Lokalisierung fortfahren, indem Sie sich das Dokument [Übersetzten Inhalt veröffentlichen](publish-content.md) ansehen. Hier erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und diese Übersetzungen aktualisieren, wenn sich der Sprachstamm ändert.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Headless-Lokalisierungs-Journey zu wechseln, indem Sie sich das Dokument [Übersetzten Inhalt veröffentlichen,](publish-content.md) ansehen. Im Folgenden finden Sie einige zusätzliche optionale, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte bieten, aber sie müssen nicht mit der Headless-Journey weitermachen.

* [Verwalten von Übersetzungsprojekten](/help/sites-cloud/administering/translation/managing-projects.md)  - Erfahren Sie mehr über die Details von Übersetzungsprojekten und zusätzliche Funktionen wie Workflows für menschliche Übersetzung und Projekte mit mehreren Sprachen.
