---
title: Konfigurieren von Übersetzungsregeln für Headless-Inhalte
description: Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren.
exl-id: 878ffd5d-0f10-4990-9779-bdf55cd95fac
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 73%

---

# Konfigurieren von Übersetzungsregeln {#configure-translation-rules}

Erfahren Sie, wie Sie Übersetzungsregeln definieren, um zu übersetzende Inhalte zu identifizieren.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Journey für die AEM Headless-Übersetzung [Übersetzungsintegration konfigurieren](configure-connector.md) Sie haben gelernt, wie Sie Ihre Übersetzungsintegration installieren und konfigurieren und sollten jetzt:

* die wichtigen Parameter des Translation Integration Framework in AEM verstehen.
* In der Lage sein, Ihre eigene Verbindung zu Ihrem Übersetzungsdienst einzurichten.

Nachdem Sie Ihre Integration eingerichtet haben, führt Sie dieser Artikel durch den nächsten Schritt, um zu ermitteln, welche Inhalte übersetzt werden müssen.

>[!CAUTION]
>
>Dieser Schritt der Dokumentations-Tour ist nur erforderlich, wenn Sie die Markierung **Übersetzbar** für Inhaltsfragmente nicht verwenden.
>
>* Die Markierung **Übersetzbar** erstellt automatisch Übersetzungsregeln für Sie und erfordert kein Eingreifen.
>* Die Markierung **Übersetzbar** wird nur verwendet, wenn die Konfiguration des Übersetzungsintegrations-Frameworks auf **[Inhaltsmodellfelder für die Übersetzung aktivieren](/help/sites-cloud/administering/translation/integration-framework.md)** festgelegt ist.
>* Durch Aktivierung dieser Option in der TIF-Konfiguration werden alle manuell erstellten Übersetzungsregeln ersetzt.|

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie die Übersetzungsregeln von AEM zur Identifizierung Ihres Übersetzungsinhalts nutzen. Nach dem Lesen dieses Dokuments sollten Sie Folgendes können:

* Verstehen, was die Übersetzungsregeln bewirken.
* Eigene Übersetzungsregeln definieren können.

## Übersetzungsregeln {#translation-rules}

Inhaltsfragmente, die Ihre Headless-Inhalte darstellen, können viele Informationen enthalten, die durch strukturierte Felder organisiert sind. Je nach Ihren Projektanforderungen müssen wahrscheinlich nicht alle Felder in einem Inhaltsfragment übersetzt werden.

Übersetzungsregeln identifizieren die Inhalte, die in Übersetzungsprojekten enthalten oder von diesen ausgeschlossen sind. Wenn Inhalte übersetzt werden, extrahiert AEM den Inhalt oder sammelt ihn anhand dieser Regeln. Auf diese Weise werden nur Inhalte an den Übersetzungs-Service gesendet, die übersetzt werden müssen.

Die Übersetzungsregeln umfassen die folgenden Informationen:

* Den Pfad der Inhalte, auf die die Regel angewendet wird
   * Die Regel gilt auch für die nachfolgenden Elemente der Inhalte
* Die Namen der Eigenschaften, die die zu übersetzenden Inhalte enthalten
   * Die Eigenschaft kann sich speziell auf einen bestimmten Ressourcentyp oder auf alle Ressourcentypen beziehen

Da Inhaltsfragmentmodelle, die die Struktur Ihrer Inhaltsfragmente definieren, für Ihr eigenes Projekt eindeutig sind, ist es wichtig, Übersetzungsregeln einzurichten. So weiß AEM, welche Elemente Ihrer Inhaltsmodelle übersetzt werden sollen.

>[!TIP]
>
>Im Allgemeinen stellt der Inhaltsarchitekte dem Übersetzungsanbieter die **Eigenschaftsname** ist von allen Feldern, die für die Übersetzung benötigt werden. Diese Namen sind erforderlich, um Übersetzungsregeln zu konfigurieren. Als Übersetzungsspezialist [können Sie diese **Eigenschaftsnamen** selbst finden](getting-started.md#content-modlels), wie zuvor in dieser Tour beschrieben.

## Erstellen von Übersetzungsregeln {#creating-rules}

Sie können mehrere Regeln erstellen, um komplexe Übersetzungsanforderungen zu unterstützen. Beispielsweise müssen für ein Projekt, an dem Sie arbeiten, alle Felder des Modells übersetzt werden, für ein anderes müssen nur Beschreibungsfelder übersetzt werden, während Titel unübersetzt bleiben.

Übersetzungsregeln sind für solche Szenarien konzipiert. In diesem Beispiel veranschaulichen wir jedoch, wie Regeln erstellt werden, indem wir uns auf eine einfache, einzelne Konfiguration konzentrieren.

Es gibt eine **Übersetzungskonfigurations**-Konsole, die zum Konfigurieren von Übersetzungsregeln verfügbar ist. So können Sie darauf zugreifen:

1. Navigieren Sie zu **Instrumente** > **Allgemein**.
1. Wählen Sie **Übersetzungskonfiguration** aus.

Im **Übersetzungskonfiguration** -Benutzeroberfläche gibt es mehrere Optionen für Ihre Übersetzungsregeln. Hier werden die wichtigsten und typischsten Schritte hervorgehoben, die für eine einfache Headless-Lokalisierungskonfiguration erforderlich sind.

1. Auswählen **Kontext hinzufügen** , um einen Pfad hinzuzufügen. Dies ist der Pfad der Inhalte, die von der Regel betroffen sind.
   ![Kontext hinzufügen](assets/add-translation-context.png)
1. Verwenden Sie den Pfad-Browser, um den erforderlichen Pfad auszuwählen und **Bestätigen** speichern. Denken Sie daran, dass Inhaltsfragmente, die Headless-Inhalte enthalten, sich im Allgemeinen unter `/content/dam/<your-project>` befinden.
   ![Pfad auswählen](assets/select-context.png)
1. Wählen Sie den soeben erstellten Kontext aus und klicken Sie auf **Bearbeiten**. Dadurch wird der **Editor für Übersetzungsregeln** geöffnet, in dem die Eigenschaften konfiguriert werden können.
   ![Editor für Übersetzungsregeln](assets/translation-rules-editor.png)
1. Standardmäßig werden alle Konfigurationen vom übergeordneten Pfad übernommen, in diesem Fall `/content/dam`. Deaktivieren Sie die Option **Übernehmen von`/content/dam`**, um der Konfiguration zusätzliche Felder hinzuzufügen.
1. Wenn diese Option deaktiviert ist, finden Sie unter der **Allgemein** Fügen Sie die Eigenschaftsnamen der von Ihnen erstellten Inhaltsfragmentmodelle hinzu. [zuvor als zu übersetzende Felder identifiziert.](getting-started.md#content-models)
   1. Im **Neue Eigenschaft** Geben Sie den Eigenschaftsnamen ein. Beachten Sie, dass die Optionen **Übersetzen** und **Vererben** automatisch aktiviert werden.
   1. Klicken Sie auf **Hinzufügen**.
   1. Wiederholen Sie diese Schritte für alle Felder, die Sie übersetzen müssen.
   1. Wählen Sie **Speichern** aus.

      ![Eigenschaft hinzufügen](assets/add-property.png)

Sie haben jetzt Ihre Übersetzungsregeln konfiguriert.

## Erweiterte Verwendung {#advanced-usage}

Es gibt mehrere zusätzliche Eigenschaften, die als Teil Ihrer Übersetzungsregeln konfiguriert werden können. Darüber hinaus können Sie Ihre Regeln manuell als XML spezifizieren, was mehr Spezifität und Flexibilität ermöglicht.

Solche Funktionen sind im Allgemeinen nicht erforderlich, um mit der Lokalisierung Ihrer Headless-Inhalte zu beginnen. Sie finden jedoch weitere Informationen dazu im Abschnitt [Zusätzliche Ressourcen](#additional-resources), wenn Sie Interesse haben.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Headless-Übersetzungs-Tour abgeschlossen haben, sollten Sie:

* Verstehen, was die Übersetzungsregeln bewirken.
* Eigene Übersetzungsregeln definieren können.

Auf diesen Erkenntnissen aufbauen und Ihre Journey-zur Headless-AEM-Übersetzung fortsetzen, indem Sie das Dokument erneut überprüfen. [Inhalt übersetzen](translate-content.md) Hier erfahren Sie, wie Ihre Integration und Regeln zusammenarbeiten, um Headless-Inhalte zu übersetzen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, mit dem nächsten Teil der Headless-Übersetzungs-Tour fortzufahren, indem Sie das Dokument [Inhalte übersetzen](translate-content.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Sie sind jedoch nicht erforderlich, um mit der Headless-Tour fortzufahren.

* [Ermitteln von zu übersetzenden Inhalten](/help/sites-cloud/administering/translation/rules.md): Erfahren Sie, wie Übersetzungsregeln Inhalte ermitteln, die übersetzt werden müssen.
