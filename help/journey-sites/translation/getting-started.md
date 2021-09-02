---
title: Erste Schritte mit der AEM Sites-Übersetzung
description: Lernen Sie, wie Sie Ihre AEM Sites-Inhalte organisieren und wie AEM Übersetzungs-Tools funktionieren.
index: true
hide: false
hidefromtoc: false
source-git-commit: 8c04ffde2cbafcb6d556de8d48fc19f5b130a2c1
workflow-type: tm+mt
source-wordcount: '1412'
ht-degree: 1%

---


# Erste Schritte mit der AEM Sites-Übersetzung {#getting-started}

Lernen Sie, wie Sie Ihre AEM Sites-Inhalte organisieren und wie AEM Übersetzungs-Tools funktionieren.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Sites-Übersetzungs-Journey [Erfahren Sie mehr über AEM Sites-Inhalte und die Übersetzung in AEM](learn-about.md) Sie haben die Grundtheorie von AEM Sites gelernt und sollten jetzt:

* Machen Sie sich mit den grundlegenden Konzepten der Inhaltserstellung in AEM Sites vertraut.
* Machen Sie sich damit vertraut, wie AEM Übersetzungen unterstützen.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie AEM Inhalte speichert und verwaltet und wie Sie AEM Übersetzungs-Tools verwenden können, um diese Inhalte zu übersetzen.

## Ziele {#objective}

In diesem Dokument erfahren Sie, wie Sie mit der Übersetzung von Site-Inhalten in AEM beginnen. Nach dem Lesen sollten Sie:

* Machen Sie sich mit der Bedeutung der Inhaltsstruktur für die Übersetzung vertraut.
* Erfahren Sie, wie AEM Inhalte speichert.
* Machen Sie sich mit AEM Übersetzungstools vertraut.

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Es gibt eine Reihe von Anforderungen, bevor Sie mit der Übersetzung Ihrer AEM beginnen.

### Kenntnisse {#knowledge}

* Erlebnis beim Übersetzen von Inhalten in ein CMS
* Erfahrung mit den grundlegenden Funktionen eines großen CMS
* Sie verfügen über Kenntnisse AEM grundlegenden Handhabung
* Grundlegendes zum verwendeten Übersetzungsdienst
* Grundlegendes zu den Inhalten, die Sie übersetzen

>[!TIP]
>
>Wenn Sie nicht mit der Verwendung eines umfangreichen CMS wie AEM vertraut sind, sollten Sie die [Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md)-Dokumentation lesen, bevor Sie fortfahren. Die Grundlegende Handling-Dokumentation ist nicht Teil des Journey, daher kehren Sie nach Abschluss des Vorgangs zu dieser Seite zurück.

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Übersetzung Ihres Inhalts
* Anmeldedaten für die Verbindung mit Ihrem bevorzugten Übersetzungsdienst
* Seien Sie Mitglied der Gruppe `project-administrators` in AEM

## Speichern von Inhalten AEM {#content-in-aem}

Für den Übersetzer ist es nicht wichtig, die Art und Weise, wie AEM Inhalte verwaltet, genau zu verstehen. Die Kenntnis der grundlegenden Konzepte und Terminologie ist jedoch hilfreich, wenn Sie später AEM Übersetzungstools verwenden. Vor allem müssen Sie Ihre eigenen Inhalte und ihre Struktur verstehen, um sie effektiv übersetzen zu können.

### Sites-Konsole {#sites-console}

Die Sites-Konsole bietet einen Überblick über die Struktur Ihres Inhalts, sodass Sie mühelos in Ihren Inhalt navigieren und ihn verwalten können, indem Sie neue Seiten erstellen, Seiten verschieben und kopieren sowie Inhalte veröffentlichen.

So greifen Sie auf die Sites-Konsole zu:

1. Klicken oder tippen Sie im globalen Navigationsmenü auf **Navigation** -> **Sites**.
1. Die Sites-Konsole wird auf der obersten Ebene Ihres Inhalts geöffnet.
1. Stellen Sie sicher, dass die **Spaltenansicht** mithilfe der Ansichtsauswahl oben rechts im Fenster ausgewählt ist.

   ![Spaltenansicht auswählen](assets/selecting-column-view.png)

1. Durch Tippen oder Klicken auf ein Element in einer Spalte wird der darunter liegende Inhalt in der Hierarchie in der Spalte rechts angezeigt.

   ![Inhaltshierarchie](assets/sites-console-hierarchy.png)

1. Durch Tippen oder Klicken auf das Kontrollkästchen eines Elements in einer Spalte wird dieses Element ausgewählt, die Details des ausgewählten Elements werden rechts in der Spalte angezeigt sowie eine Reihe von Aktionen angezeigt, die für das ausgewählte Element in der Symbolleiste oben verfügbar sind.

   ![Inhaltsauswahl](assets/sites-console-selection.png)

1. Durch Tippen oder Klicken auf die Schienenauswahl oben links können Sie auch die Ansicht **Inhaltsstruktur** anzeigen, um eine Baumstruktur mit Ihrem Inhalt anzuzeigen.

   ![Inhaltsbaumansicht](assets/sites-console-content-tree.png)

Mithilfe dieser einfachen Tools können Sie intuitiv durch Ihre Inhaltsstruktur navigieren.

>[!NOTE]
>
>Der Inhaltsarchitekt definiert normalerweise die Inhaltsstruktur, während die Inhaltsautoren den Inhalt in dieser Struktur erstellen.
>
>Als Übersetzer ist es wichtig, einfach zu verstehen, wie man durch diese Struktur navigiert und wo sich die Inhalte befinden.

### Seiteneditor {#page-editor}

Die Sites-Konsole ermöglicht Ihnen die Navigation in Ihrem Inhalt und bietet einen Überblick über dessen Struktur. Um die Details einer einzelnen Seite anzuzeigen, müssen Sie den Sites-Editor verwenden.

So bearbeiten Sie eine Seite:

1. Verwenden Sie die Sites-Konsole, um eine Seite zu suchen und auszuwählen. Denken Sie daran, dass Sie auf das Kontrollkästchen einer einzelnen Seite tippen oder klicken müssen, um sie auszuwählen.

   ![Auswahl einer zu bearbeitenden Seite](assets/sites-editor-select-page.png)

1. Tippen Sie in der Symbolleiste auf die Option **Bearbeiten** .
1. Der Sites-Editor wird geöffnet, wobei die ausgewählte Seite in einer neuen Browser-Registerkarte zur Bearbeitung geladen wird.
1. Wenn Sie den Mauszeiger über den Inhalt bewegen oder darauf tippen, werden Selektoren für einzelne Komponenten angezeigt. Komponenten sind die Drag &amp; Drop-Bausteine, aus denen die Seite besteht.

   ![Bearbeiten einer Seite](assets/sites-editor-title.png)

Sie können jederzeit zur Sites-Konsole zurückkehren, indem Sie in Ihrem Browser zu dieser Registerkarte zurückkehren. Mit dem Sites-Editor können Sie den Inhalt der Seite schnell anzeigen, da die Inhaltsautoren und Ihre Zielgruppe ihn sehen werden.

>[!NOTE]
>
>Die Inhaltsautoren erstellen Ihren Site-Inhalt mit dem Sites-Editor.
>
>Als Übersetzer ist es wichtig, einfach zu verstehen, wie die Details dieses Inhalts mit dem Sites-Editor angezeigt werden.

## Struktur ist der Schlüssel {#content-structure}

AEM Inhalt wird durch seine Struktur bestimmt. AEM stellt nur wenige Anforderungen an die Inhaltsstruktur, doch kann eine sorgfältige Berücksichtigung Ihrer Inhaltshierarchie im Rahmen der Projektplanung die Übersetzung erheblich vereinfachen.

>[!TIP]
>
>Planen Sie die Übersetzung am Anfang Ihres AEM. Arbeiten Sie frühzeitig mit dem Projektmanager und den Inhaltsarchitekten zusammen.
>
>Ein Internationalisierungsprojekt-Manager kann als eigenständige Person erforderlich sein, deren Aufgabe es ist zu definieren, welche Inhalte übersetzt werden sollen und welche nicht und welche übersetzten Inhalte von regionalen oder lokalen Inhaltserstellern geändert werden können.

## Empfohlene Inhaltsstruktur {#recommended-structure}

Arbeiten Sie wie zuvor empfohlen mit Ihrem Inhaltsarchitekten zusammen, um die geeignete Inhaltsstruktur für Ihr eigenes Projekt zu ermitteln. Das Folgende ist jedoch eine bewährte, einfache und intuitive Struktur, die sehr effektiv ist.

Definieren Sie einen Basisordner für Ihr Projekt unter `/content`.

```text
/content/<your-project>
```

Die Sprache, in der Ihr Inhalt erstellt wird, wird als Sprachstamm bezeichnet. In unserem Beispiel ist es Englisch und sollte unter diesem Pfad liegen.

```text
/content/<your-project>/en
```

Alle Projektinhalte, die möglicherweise lokalisiert werden müssen, sollten im Sprachstamm platziert werden.

```text
/content/<your-project>/en/<your-project-content>
```

Übersetzungen sollten als gleichrangige Ordner neben dem Sprachstamm erstellt werden, wobei ihr Ordnername den ISO-2-Sprachcode der Sprache darstellt. Beispielsweise hätte Deutsch den folgenden Pfad.

```text
/content/<your-project>/de
```

>[!NOTE]
>
>Der Inhaltsarchitekt ist im Allgemeinen für die Erstellung dieser Sprachordner verantwortlich. Wenn sie nicht erstellt werden, können AEM später keine Übersetzungsaufträge erstellen.

Die endgültige Struktur kann etwa wie folgt aussehen:

```text
/content
    |- your-project
        |- en
            |- some
            |- exciting
            |- sites
            |- content
        |- de
        |- fr
        |- it
        |- ...
    |- another-project
    |- ...
```

Beachten Sie den spezifischen Pfad Ihres Inhalts, da er später zur Konfiguration Ihrer Übersetzung erforderlich ist.

>[!NOTE]
>
>In der Regel ist es Aufgabe des Inhaltsarchitekten, die Inhaltsstruktur zu definieren, oft in Zusammenarbeit mit dem Übersetzungsanbieter.
>
>Sie wird hier zur Vollständigkeit detailliert beschrieben.

## AEM Übersetzungswerkzeuge {#translation-tools}

Nachdem Sie nun die Sites-Konsole und den Editor sowie die Bedeutung der Inhaltsstruktur kennen, können wir uns ansehen, wie Inhalte übersetzt werden. Die Übersetzungs-Tools in AEM sind sehr leistungsstark, aber einfach zu verstehen auf einer hohen Ebene.

* **Übersetzungs-Connector**  - Der Connector ist die Verknüpfung zwischen AEM und dem von Ihnen verwendeten Übersetzungsdienst.
* **Übersetzungsregeln**  - Regeln definieren, welche Inhalte unter bestimmten Pfaden übersetzt werden sollen.
* **Übersetzungsprojekte** : Übersetzungsprojekte sammeln Inhalte, die als einziger Übersetzungsprozess angesprochen werden sollten, und verfolgen den Fortschritt der Übersetzung, stellen eine Verbindung mit dem Connector her, um die zu übersetzenden Inhalte zu übertragen und sie vom Übersetzungsdienst zurückzuerhalten.

Normalerweise richten Sie Ihren Connector nur einmal für Ihre Instanz und Regeln pro Projekt ein. Dann verwenden Sie Übersetzungsprojekte, um Ihre Inhalte zu übersetzen und die Übersetzungen laufend auf dem neuesten Stand zu halten.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der AEM Sites-Übersetzungs-Journey abgeschlossen haben, sollten Sie Folgendes tun:

* Machen Sie sich mit der Bedeutung der Inhaltsstruktur für die Übersetzung vertraut.
* Erfahren Sie, wie AEM Inhalte speichert.
* Machen Sie sich mit AEM Übersetzungstools vertraut.

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit der Journey Ihrer AEM Sites-Übersetzung fort, indem Sie sich das Dokument [Konfigurieren des Übersetzungs-Connectors](configure-connector.md) ansehen. Hier erfahren Sie, wie Sie AEM mit einem Übersetzungsdienst verbinden.|

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Journey zu wechseln, indem Sie das Dokument [Konfigurieren des Übersetzungs-Connectors](configure-connector.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, jedoch nicht auf dem Journey weiterarbeiten müssen.

* [AEM Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md)  - Lernen Sie die Grundlagen der AEM Benutzeroberfläche kennen, um bequem zu navigieren und wichtige Aufgaben wie das Auffinden von Inhalten durchzuführen.
* [Identifizieren von zu übersetzenden Inhalten](/help/sites-cloud/administering/translation/rules.md)  - Erfahren Sie, wie Übersetzungsregeln Inhalte identifizieren, die übersetzt werden müssen.
* [Konfigurieren des Übersetzungsintegrations-Frameworks](/help/sites-cloud/administering/translation/integration-framework.md)  - Erfahren Sie, wie Sie das Übersetzungsintegrations-Framework konfigurieren, um es in Übersetzungsdienste von Drittanbietern zu integrieren.
* [Verwalten von Übersetzungsprojekten](/help/sites-cloud/administering/translation/managing-projects.md)  - Erfahren Sie, wie Sie in AEM Übersetzungsprojekte für Übersetzer und Übersetzer erstellen und verwalten.
