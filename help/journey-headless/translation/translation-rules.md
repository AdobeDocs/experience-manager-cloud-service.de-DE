---
title: Übersetzungsregeln konfigurieren
description: Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren.
index: true
hide: false
hidefromtoc: false
source-git-commit: 6605349c698325d432479fac0253a6fd53d7f175
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 4%

---

# Übersetzungsregeln konfigurieren {#configure-translation-rules}

Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Journey für die AEM Headless-Übersetzung [Konfigurieren des Übersetzungs-Connectors](configure-connector.md) haben Sie gelernt, wie Sie Ihren Übersetzungs-Connector installieren und konfigurieren und sollten jetzt:

* Machen Sie sich mit den wichtigen Parametern des Translation Integration Framework in AEM vertraut.
* Sie können Ihre eigene Verbindung zu Ihrem Übersetzungsdienst einrichten.

Nachdem Sie Ihren Connector eingerichtet haben, führt Sie dieser Artikel durch den nächsten Schritt, um herauszufinden, welche Inhalte übersetzt werden müssen.

## Ziele {#objective}

In diesem Dokument erfahren Sie, wie Sie AEM Übersetzungsregeln zur Identifizierung Ihres Übersetzungsinhalts verwenden. Nach Lesen dieses Dokuments sollten Sie über Folgendes verfügen:

* Machen Sie sich mit den Übersetzungsregeln vertraut.
* Sie können Ihre eigenen Übersetzungsregeln definieren.

## Übersetzungsregeln {#translation-rules}

Inhaltsfragmente, die Ihren Headless-Inhalt darstellen, können viele Informationen enthalten, die nach strukturierten Feldern organisiert sind. Je nach Ihren Projektanforderungen müssen wahrscheinlich nicht alle Felder in einem Inhaltsfragment übersetzt werden.

Übersetzungsregeln identifizieren den Inhalt, der in Übersetzungsprojekten enthalten oder von diesen ausgeschlossen ist. Wenn Inhalte übersetzt werden, extrahiert AEM den Inhalt oder sammelt ihn anhand dieser Regeln. Auf diese Weise werden nur Inhalte an den Übersetzungsdienst gesendet, die übersetzt werden müssen.

Zu den Übersetzungsregeln gehören die folgenden Informationen:

* Der Pfad des Inhalts, für den die Regel gilt
   * Die Regel gilt auch für die untergeordneten Elemente des Inhalts
* Die Namen der Eigenschaften, die den zu übersetzenden Inhalt enthalten
   * Die Eigenschaft kann sich speziell auf einen bestimmten Ressourcentyp oder auf alle Ressourcentypen beziehen

Da Inhaltsfragmentmodelle, die die Struktur Ihrer Inhaltsfragmente definieren, für Ihr eigenes Projekt eindeutig sind, ist es wichtig, Übersetzungsregeln einzurichten, damit AEM weiß, welche Elemente Ihrer Inhaltsmodelle übersetzt werden sollen.

>[!TIP]
>
>Im Allgemeinen stellt der Inhaltsarchitekte dem Übersetzungsspezialisten die **Eigenschaftsname** s aller für die Übersetzung erforderlichen Felder zur Verfügung. Diese Namen sind erforderlich, um Übersetzungsregeln zu konfigurieren. Als Übersetzungsspezialist finden Sie [diese **Eigenschaftsnamen** s selbst](getting-started.md#content-modlels), wie zuvor in dieser Journey beschrieben.

## Erstellen von Übersetzungsregeln {#creating-rules}

Es können mehrere Regeln erstellt werden, um komplexe Übersetzungsanforderungen zu unterstützen. Beispielsweise müssen für ein Projekt, an dem Sie arbeiten, alle Felder des Modells übersetzt werden, für ein anderes nur Beschreibungsfelder übersetzt werden, während Titel nicht übersetzt bleiben.

Übersetzungsregeln sind für solche Szenarien konzipiert. In diesem Beispiel veranschaulichen wir jedoch, wie Regeln erstellt werden, indem wir uns auf eine einfache, einzelne Konfiguration konzentrieren.

Zum Konfigurieren von Übersetzungsregeln steht eine Konsole **Übersetzungskonfiguration** zur Verfügung. So können Sie darauf zugreifen:

1. Navigieren Sie zu **Tools** -> **Allgemein**.
1. Tippen oder klicken Sie auf **Übersetzungskonfiguration**.

In der Benutzeroberfläche **Übersetzungskonfiguration** stehen eine Reihe von Optionen für Ihre Übersetzungsregeln zur Verfügung. Hier werden die wichtigsten und typischsten Schritte hervorgehoben, die für eine einfache, Headless-Lokalisierungskonfiguration erforderlich sind.

1. Tippen oder klicken Sie auf **Kontext hinzufügen**, um einen Pfad hinzuzufügen. Dies ist der Pfad des Inhalts, der von der Regel betroffen ist.
   ![Kontext hinzufügen](assets/add-translation-context.png)
1. Verwenden Sie den Pfad-Browser, um den erforderlichen Pfad auszuwählen, und tippen oder klicken Sie zum Speichern auf die Schaltfläche **Bestätigen** . Denken Sie daran, dass Inhaltsfragmente, die Headless-Inhalte enthalten, sich im Allgemeinen unter `/content/dam/<your-project>` befinden.
   ![Pfad auswählen](assets/select-context.png)
1. AEM speichert die Konfiguration.
1. Sie müssen den soeben erstellten Kontext auswählen und dann auf **Bearbeiten** tippen oder klicken. Dadurch wird der **Übersetzungsregel-Editor** geöffnet, um die Eigenschaften zu konfigurieren.
   ![Editor für Übersetzungsregeln](assets/translation-rules-editor.png)
1. Standardmäßig werden alle Konfigurationen vom übergeordneten Pfad übernommen, in diesem Fall `/content/dam`. Deaktivieren Sie die Option **Von`/content/dam`** übernehmen , um der Konfiguration zusätzliche Felder hinzuzufügen.
1. Fügen Sie nach der Deaktivierung im Abschnitt **Allgemein** der Liste die Eigenschaftsnamen der Inhaltsfragmentmodelle hinzu, die Sie [zuvor als zu übersetzende Felder identifiziert haben.](getting-started.md#content-models)
   1. Geben Sie den Eigenschaftsnamen in das Feld **Neue Eigenschaft** ein.
   1. Die Optionen **Übersetzen** und **Vererben** werden automatisch aktiviert.
   1. Tippen oder klicken Sie auf **Hinzufügen**.
   1. Wiederholen Sie diese Schritte für alle Felder, die Sie übersetzen müssen.
   1. Tippen oder klicken Sie auf **Speichern**.
      ![Eigenschaft hinzufügen](assets/add-property.png)

Sie haben jetzt Ihre Übersetzungsregeln konfiguriert.

## Erweiterte Verwendung {#advanced-usage}

Es gibt eine Reihe weiterer Eigenschaften, die als Teil Ihrer Übersetzungsregeln konfiguriert werden können. Darüber hinaus können Sie Ihre Regeln manuell als XML spezifizieren, was mehr Spezifität und Flexibilität ermöglicht.

Solche Funktionen sind im Allgemeinen nicht erforderlich, um mit der Lokalisierung Ihres Headless Content zu beginnen. Sie können sie jedoch im Abschnitt [Zusätzliche Ressourcen](#additional-resources) weiter lesen, wenn Sie daran interessiert sind.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Headless-Übersetzungs-Journey abgeschlossen haben, sollten Sie:

* Machen Sie sich mit den Übersetzungsregeln vertraut.
* Sie können Ihre eigenen Übersetzungsregeln definieren.

Erstellen Sie auf diesem Wissen und fahren Sie mit dem Journey der AEM Headless-Übersetzung fort, indem Sie sich das Dokument [Inhalt übersetzen](translate-content.md) ansehen. Hier erfahren Sie, wie Ihr Connector und Ihre Regeln zusammenarbeiten, um Headless Content zu übersetzen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Journey für die Headless-Übersetzung zu wechseln, indem Sie das Dokument [Inhalt übersetzen,](translate-content.md) im Folgenden finden Sie einige zusätzliche optionale, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber sie müssen nicht auf der Headless-Journey weiterarbeiten.

* [Identifizieren von zu übersetzenden Inhalten](/help/sites-cloud/administering/translation/rules.md)  - Erfahren Sie, wie Übersetzungsregeln Inhalte identifizieren, die übersetzt werden müssen.
