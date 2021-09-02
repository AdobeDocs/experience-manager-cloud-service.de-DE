---
title: Übersetzungsregeln konfigurieren
description: Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren.
index: true
hide: false
hidefromtoc: false
source-git-commit: 08127d72c84d6f47f5058ef631dc3128114f1953
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 4%

---


# Übersetzungsregeln konfigurieren {#configure-translation-rules}

Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Sites-Übersetzungs-Journey [Konfigurieren des Übersetzungs-Connectors](configure-connector.md) haben Sie gelernt, wie Sie Ihren Übersetzungs-Connector installieren und konfigurieren und sollten jetzt:

* Machen Sie sich mit den wichtigen Parametern des Translation Integration Framework in AEM vertraut.
* Sie können Ihre eigene Verbindung zu Ihrem Übersetzungsdienst einrichten.

Nachdem Sie Ihren Connector eingerichtet haben, führt Sie dieser Artikel durch den nächsten Schritt, um herauszufinden, welche Inhalte übersetzt werden müssen.

## Ziele {#objective}

In diesem Dokument erfahren Sie, wie Sie AEM Übersetzungsregeln zur Identifizierung Ihres Übersetzungsinhalts verwenden. Nach Lesen dieses Dokuments sollten Sie über Folgendes verfügen:

* Machen Sie sich mit den Übersetzungsregeln vertraut.
* Sie können Ihre eigenen Übersetzungsregeln definieren.

## Übersetzungsregeln {#translation-rules}

AEM Sites-Seiten können viele Informationen enthalten. Je nach Ihren Projektanforderungen müssen wahrscheinlich nicht alle Informationen auf einer Seite übersetzt werden.

Übersetzungsregeln identifizieren den Inhalt, der in Übersetzungsprojekten enthalten oder von diesen ausgeschlossen ist. Wenn Inhalte übersetzt werden, extrahiert AEM den Inhalt oder sammelt ihn anhand dieser Regeln. Auf diese Weise werden nur Inhalte an den Übersetzungsdienst gesendet, die übersetzt werden müssen.

Zu den Übersetzungsregeln gehören die folgenden Informationen:

* Der Pfad des Inhalts, für den die Regel gilt
   * Die Regel gilt auch für die untergeordneten Elemente des Inhalts
* Die Namen der Eigenschaften, die den zu übersetzenden Inhalt enthalten
   * Die Eigenschaft kann sich speziell auf einen bestimmten Ressourcentyp oder auf alle Ressourcentypen beziehen

AEM erstellt automatisch Übersetzungsregeln für Siteseiten. Da jedoch die Anforderungen jedes Projekts unterschiedlich sind, ist es wichtig, dass Sie wissen, wie Sie die Regeln überprüfen und an Ihr Projekt anpassen können.

## Erstellen von Übersetzungsregeln {#creating-rules}

Es können mehrere Regeln erstellt werden, um komplexe Übersetzungsanforderungen zu unterstützen. Beispielsweise müssen für ein Projekt, an dem Sie arbeiten, alle Seiteninformationen übersetzt werden. Auf einer anderen Seite dürfen jedoch nur Beschreibungen übersetzt werden, während Titel nicht übersetzt bleiben.

Übersetzungsregeln sind für solche Szenarien konzipiert. In diesem Beispiel veranschaulichen wir jedoch, wie Regeln erstellt werden, indem wir uns auf eine einfache, einzelne Konfiguration konzentrieren.

Zum Konfigurieren von Übersetzungsregeln steht eine Konsole **Übersetzungskonfiguration** zur Verfügung.

So können Sie darauf zugreifen:

1. Navigieren Sie zu **Tools** -> **Allgemein**.
1. Tippen oder klicken Sie auf **Übersetzungskonfiguration**.

AEM erstellt automatisch Übersetzungsregeln für alle Inhalte. So zeigen Sie diese Regeln an:

1. Wählen Sie den Kontext `/content` und dann die Option **Bearbeiten** in der Symbolleiste aus.
1. Der Editor für Übersetzungsregeln wird mit den Regeln geöffnet, die automatisch für den Pfad `/content` erstellt AEM.

   ![Editor für Übersetzungsregeln](assets/translation-rules-editor.png)

1. Seiteneigenschaften, die übersetzt werden sollen, befinden sich im Abschnitt **Allgemein** der Liste. Sie können vorhandene Eigenschaftsnamen hinzufügen oder aktualisieren, die Sie explizit in die Übersetzung aufnehmen möchten.
   1. Geben Sie den Eigenschaftsnamen in das Feld **Neue Eigenschaft** ein.
   1. Die Optionen **Übersetzen** und **Vererben** werden automatisch aktiviert.
   1. Tippen oder klicken Sie auf **Hinzufügen**.
   1. Wiederholen Sie diese Schritte für alle Felder, die Sie übersetzen müssen.
   1. Tippen oder klicken Sie auf **Speichern**.

Sie haben jetzt Ihre Übersetzungsregeln konfiguriert.

>[!NOTE]
>
>AEM erstellt automatisch Übersetzungsregeln. Für eine einfache Einrichtung oder zum Testen eines Übersetzungs-Workflows ist es nicht erforderlich, neue Regeln zu erstellen oder die vorhandenen, automatisch erstellten Regeln zu ändern. Die Details dieser Schritte werden erläutert, wie die Regeln funktionieren und wie AEM Übersetzungen verarbeitet werden.

>[!TIP]
>
>Es ist auch möglich, Regeln nur für Ihren bestimmten Pfad oder Projekt zu erstellen, indem Sie in der Konsole &quot;Übersetzungskonfiguration&quot;auf die Schaltfläche **Kontext hinzufügen** tippen oder klicken. Dies geht über den Rahmen dieser Journey hinaus.

## Erweiterte Verwendung {#advanced-usage}

Es gibt eine Reihe weiterer Eigenschaften, die als Teil Ihrer Übersetzungsregeln konfiguriert werden können. Darüber hinaus können Sie Ihre Regeln manuell als XML spezifizieren, was mehr Spezifität und Flexibilität ermöglicht.

Solche Funktionen sind im Allgemeinen nicht erforderlich, um mit der Lokalisierung Ihres Inhalts zu beginnen. Sie können sie jedoch im Abschnitt [Zusätzliche Ressourcen](#additional-resources) weiter lesen, wenn Sie daran interessiert sind.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der AEM Sites-Übersetzungs-Journey abgeschlossen haben, sollten Sie Folgendes tun:

* Machen Sie sich mit den Übersetzungsregeln vertraut.
* Sie können Ihre eigenen Übersetzungsregeln definieren.

Verschaffen Sie sich diese Kenntnisse und setzen Sie die Journey Ihrer AEM Sites-Übersetzung fort, indem Sie sich das Dokument [Inhalt übersetzen](translate-content.md) ansehen. Hier erfahren Sie, wie Ihr Connector und Ihre Regeln zusammenarbeiten, um Inhalte zu übersetzen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Journey zu wechseln, indem Sie das Dokument [Inhalt übersetzen,](translate-content.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, jedoch nicht auf dem Journey weiterarbeiten müssen.

* [Identifizieren von zu übersetzenden Inhalten](/help/sites-cloud/administering/translation/rules.md)  - Erfahren Sie, wie Übersetzungsregeln Inhalte identifizieren, die übersetzt werden müssen.
