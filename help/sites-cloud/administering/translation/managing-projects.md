---
title: Verwalten von Übersetzungsprojekten
description: Erfahren Sie, wie Sie sowohl maschinelle als auch menschliche Übersetzungsprojekte in AEM erstellen und verwalten.
translation-type: tm+mt
source-git-commit: 9518a3ddb253ede2e9b713b4a7d0077e8ba3f7e0
workflow-type: tm+mt
source-wordcount: '3825'
ht-degree: 37%

---


# Verwalten von Übersetzungsprojekten {#managing-translation-projects}

Mithilfe von Übersetzungsprojekten können Sie die Übersetzung von AEM-Inhalten verwalten. Ein Übersetzungsprojekt ist eine Art AEM [Projekt](/help/sites-cloud/authoring/projects/overview.md), das Ressourcen enthält, die in andere Sprachen übersetzt werden sollen. Bei diesen Ressourcen handelt es sich um Seiten und Assets der [Sprachkopien](preparation.md), die vom Sprach-Master erstellt werden.

Wenn einem Übersetzungsprojekt Ressourcen hinzugefügt werden, wird ein Übersetzungsauftrag für sie erstellt. Aufträge beinhalten Befehle und Statusinformationen, mit denen Sie die Workflows für menschliche und maschinelle Übersetzungen, die für die Ressourcen ausgeführt werden, verwalten.

Übersetzungsprojekte sind langfristige Elemente, die durch die Sprache und die Übersetzungsmethode/den Provider entsprechend den Grundsätzen der Organisationsführung hinsichtlich der Globalisierung definiert sind. Sie sollten einmal während der Erstübersetzung oder manuell initiiert werden und so lange gültig bleiben, wie Inhalts- und Übersetzungsaktualisierungsaktivitäten ausgeführt werden.

Übersetzungsprojekte und -aufträge werden in Übersetzungsvorbereitungs-Workflows erstellt. Diese Workflows umfassen drei Optionen für die Erstübersetzung (Erstellen und übersetzen) und für Aktualisierungen (Übersetzung aktualisieren):

1. [Neues Projekt erstellen](#creating-translation-projects-using-the-references-panel)
1. [Zu vorhandenem Projekt hinzufügen](#adding-pages-to-a-translation-project)
1. [Nur Inhaltsstruktur](#creating-the-structure-of-a-language-copy)

AEM erkennt, ob ein Übersetzungsprojekt zur Erstübersetzung des Inhalts oder zur Aktualisierung von bereits übersetzten Sprachkopien erstellt werden soll. Wenn Sie ein Übersetzungsprojekt für eine Seite erstellen und die Sprachkopien angeben, für die Sie eine Übersetzung benötigen, erkennt AEM, ob die Quellseite bereits in den Zielsprachkopien vorhanden ist:

* **Die Sprachkopie enthält keine Seite:** AEM behandelt diese Situation als Ausgangsübersetzung. Die Seite wird sofort in die Sprachkopie kopiert und in das Projekt eingefügt. Wenn die übersetzte Seite in AEM importiert wird, kopiert AEM diese direkt in die Sprachkopie.
* **Die Sprachkopie enthält bereits die Seite:** AEM behandelt diese Situation als aktualisierte Übersetzung. Es wird ein Lauch erstellt, eine Kopie der Seite dem Launch hinzugefügt und dieser in das Projekt eingefügt. Mithilfe von Launches können Sie aktualisierte Übersetzungen vor dem Einfügen in die Sprachkopie überprüfen:

   * Wenn die übersetzte Seite in AEM importiert wird, wird die Seite im Launch überschrieben.
   * Die übersetzte Seite überschreibt die Sprachkopie nur, wenn der Launch weitergeleitet (beworben) wird.

Beispielsweise wird der `/content/wknd/fr` Sprachstamm für die französische Übersetzung der `/content/wknd/en`-Sprache Übergeordnet erstellt. Es gibt keine anderen Seiten in der französischen Sprachkopie.

* Ein Übersetzungsprojekt wird für die `/content/wknd/en/products`-Seite und alle untergeordneten Seiten erstellt, wobei die französische Sprachkopie verwendet wird. Da die Sprachkopie nicht die Seite `/content/wknd/fr/products` enthält, kopiert AEM sofort die Seite `/content/wknd/en/products` und alle untergeordneten Seiten in die französische Sprachkopie. Die Kopien werden auch in das Übersetzungsprojekt eingefügt.
* Ein Übersetzungsprojekt wird für die `/content/wknd/en`-Seite und alle untergeordneten Seiten erstellt, wobei die französische Sprachkopie verwendet wird. Da die Sprachkopie die Seite enthält, die der `/content/wknd/en`-Seite entspricht (der Sprachstamm), kopiert AEM die `/content/wknd/en`-Seite und alle untergeordneten Seiten und fügt sie einem Start hinzu. Die Kopien werden auch in das Übersetzungsprojekt eingefügt.

## Übersetzung aus der Sites-Konsole {#performing-initial-translations-and-updating-existing-translations}

Übersetzungsprojekte können direkt über die Sites-Konsole erstellt oder aktualisiert werden.

### Erstellen von Übersetzungsprojekten mithilfe des Bedienfelds „Verweise“{#creating-translation-projects-using-the-references-panel}

Erstellen Sie Übersetzungsprojekte so, dass Sie den Workflow zur Übersetzung der Ressourcen Ihres Sprach-Masters ausführen und verwalten können. Wenn Sie Projekte erstellen, legen Sie die Seite im Sprach-Master, die Sie übersetzen wollen, und die Sprachkopien, für die Sie die Übersetzung durchführen wollen, fest:

* Die Cloud-Konfiguration des Übersetzungsintegrations-Frameworks, das mit der ausgewählten Seite verknüpft ist, bestimmt viele Eigenschaften der Übersetzungsprojekte, z. B. die zu verwendenden Übersetzungs-Workflows.
* Es wird ein Projekt für jede ausgewählte Sprachkopie erstellt.
* Es wird eine Kopie der ausgewählten Seite und der zugehörigen Assets erstellt und jedem Projekt hinzugefügt. Diese Kopien werden später zum Übersetzen an den Übersetzungsanbieter gesendet.

Sie können festlegen, dass die untergeordneten Seiten der ausgewählten Seite ebenfalls ausgewählt werden. In diesem Fall werden jedem Projekt auch die Kopien der untergeordneten Seiten hinzugefügt, sodass sie übersetzt werden. Wenn untergeordnete Seiten unterschiedlichen Konfigurationen des Translation-Integration-Frameworks zugeordnet sind, erstellt AEM zusätzliche Projekte.

Sie können auch [Übersetzungsprojekte manuell erstellen](#creating-a-translation-project-using-the-projects-console).

>[!NOTE]
>
>Um ein Projekt zu erstellen, muss Ihr Konto Mitglied der Gruppe `project-administrators` sein.

### Erstübersetzungen und Aktualisieren von Übersetzungen {#initial-and-updating}

Das Bedienfeld „Verweise“ zeigt an, ob Sie vorhandene Sprachkopien aktualisieren oder die erste Version der Sprachkopien erstellen. Falls eine Sprachkopie für die ausgewählte Seite vorhanden ist, wird die Registerkarte „Sprachkopien aktualisieren“ angezeigt, auf der Sie auf projektspezifische Befehle zugreifen können.

![Sprachkopien aktualisieren](../assets/update-language-copies.png)

Nach der Übersetzung können Sie [die Übersetzung überprüfen](#reviewing-and-promoting-updated-content), bevor Sie die Sprachkopie damit überschreiben. Wenn keine Sprachkopie für die ausgewählte Seite vorhanden ist, wird die Registerkarte „Erstellen und übersetzen“ angezeigt, auf der Sie auf projektspezifische Befehle zugreifen können.

![Erstellen und übersetzen](../assets/create-and-translate.png)

### Erstellen von Übersetzungsprojekten für eine neue Sprachkopie {#create-translation-projects-for-a-new-language-copy}

1. Verwenden Sie die Sites-Konsole, um die Seite auszuwählen, die Sie den Übersetzungsprojekten hinzufügen.

1. Öffnen Sie in der Symbolleiste die Leiste **References**.

   ![Verweise](../assets/references.png)

1. Wählen Sie **Sprachkopien** und wählen Sie dann die Sprachkopien aus, für die Sie die Quellseiten übersetzen möchten.
1. Klicken Sie auf oder tippen Sie auf **Erstellen und übersetzen** und konfigurieren Sie dann den Übersetzungsauftrag:

   * Verwenden Sie die Dropdownliste **Sprachen**, um eine Sprachkopie auszuwählen, für die Sie übersetzen möchten. Wählen Sie bei Bedarf weitere Sprachen aus. Die in der Liste angezeigten Sprachen entsprechen den [Sprach-Stämmen, die Sie erstellt haben](preparation.md#creating-a-language-root).
      * Durch Auswahl mehrerer Sprachen wird ein Projekt mit einem Übersetzungsauftrag für jede Sprache erstellt.
   * Um die ausgewählte Seite und alle untergeordneten Seiten zu übersetzen, wählen Sie **Wählen Sie alle Unterseiten** aus. Um nur die von Ihnen ausgewählten Seiten zu übersetzen, wählen Sie diese Option ab.
   * Wählen Sie für **Projekt** **Übersetzungsprojekt(e)** erstellen.
   * Wählen Sie optional für **Project Übergeordnet** ein Projekt aus, aus dem Benutzerrollen und -berechtigungen geerbt werden sollen.
   * Geben Sie unter **Titel** einen Namen für das Projekt ein.

   ![Übersetzungsprojekt erstellen](../assets/create-translation-project.png)

1. Klicken oder tippen Sie auf **Erstellen**.

### Erstellen von Übersetzungsprojekten für vorhandene Sprachkopien {#create-translation-projects-for-an-existing-language-copy}

1. Verwenden Sie die Sites-Konsole, um die Seite auszuwählen, die Sie den Übersetzungsprojekten hinzufügen.

1. Öffnen Sie in der Symbolleiste die Leiste **References**.

   ![Verweise](../assets/references.png)

1. Wählen Sie **Sprachkopien** und wählen Sie dann die Sprachkopien aus, für die Sie die Quellseiten übersetzen möchten.
1. Klicken Sie auf oder tippen Sie auf **Sprachkopien aktualisieren** und konfigurieren Sie dann den Übersetzungsauftrag:

   * Um die ausgewählte Seite und alle untergeordneten Seiten zu übersetzen, wählen Sie **Wählen Sie alle Unterseiten** aus. Um nur die von Ihnen ausgewählten Seiten zu übersetzen, wählen Sie diese Option ab.
   * Wählen Sie für **Projekt** **Übersetzungsprojekt(e)** erstellen.
   * Wählen Sie optional für **Project Übergeordnet** ein Projekt aus, aus dem Benutzerrollen und -berechtigungen geerbt werden sollen.
   * Geben Sie unter **Titel** einen Namen für das Projekt ein.

   ![Projekt zum Aktualisieren von Sprachkopien erstellen](../assets/create-update-language-copies-project.png)

1. Klicken oder tippen Sie auf **Erstellen**.

### Hinzufügen von Seiten zu einem Übersetzungsprojekt {#adding-pages-to-a-translation-project}

Nachdem Sie ein Übersetzungsprojekt erstellt haben, können Sie die Leiste **Ressourcen** verwenden, um dem Projekt Seiten hinzuzufügen. Das Hinzufügen von Seiten ist dann hilfreich, wenn Sie Seiten von verschiedenen Verzweigungen in dasselbe Projekt einfügen.

Wenn Sie einem Übersetzungsprojekt Seiten hinzufügen, werden die Seiten in einen neuen Übersetzungsauftrag eingefügt. Sie können also [Seiten zu einem vorhandenen Auftrag hinzufügen](#adding-pages-assets-to-a-translation-job).

So wie beim Erstellen eines neuen Projekts werden beim Hinzufügen von Seiten bei Bedarf Kopien der Seiten zu einem Launch hinzugefügt, um zu verhindern, dass vorhandene Sprachkopien überschrieben werden. (Siehe [Erstellen von Übersetzungsprojekten für vorhandene Sprachkopien](#performing-initial-translations-and-updating-existing-translations).)

1. Verwenden Sie die Sites-Konsole, um die Seite auszuwählen, die Sie dem Übersetzungsprojekt hinzufügen.

1. Öffnen Sie in der Symbolleiste die Leiste **References**.

   ![Verweise](../assets/references.png)

1. Wählen Sie **Sprachkopien** und wählen Sie dann die Sprachkopien aus, für die Sie die Quellseiten übersetzen möchten.

   ![Aktualisieren von Sprachkopien der Bezugsleiste](../assets/update-language-copies-references.png)

1. Klicken Sie auf oder tippen Sie auf **Sprachkopien aktualisieren** und konfigurieren Sie dann die Eigenschaften:

   * Um die ausgewählte Seite und alle untergeordneten Seiten zu übersetzen, wählen Sie **Wählen Sie alle Unterseiten** aus. Um nur die von Ihnen ausgewählten Seiten zu übersetzen, wählen Sie diese Option ab.
   * Wählen Sie für **Projekt** **Hinzufügen zu vorhandenem Übersetzungsprojekt**.
   * Wählen Sie das Projekt unter **Vorhandenes Übersetzungsprojekt** aus.

   >[!NOTE]
   >
   >Die im Übersetzungsprojekt eingestellte Zielgruppe sollte mit dem Pfad der Sprachkopie übereinstimmen, wie in der Referenzleiste dargestellt.

1. Klicken Sie auf oder tippen Sie auf **Aktualisieren**.

### Erstellen der Struktur einer Sprachkopie {#creating-the-structure-of-a-language-copy}

Es ist möglich, nur die Struktur der Sprachkopie zu erstellen, sodass Sie Inhalte und strukturelle Änderungen in der Sprache Übergeordnet in (nicht übersetzte) Sprachkopien kopieren können. Dies steht in keinem Zusammenhang mit einem Übersetzungsauftrag oder -projekt. Sie können diese Option verwenden, um Ihre Sprach-Master auch ohne Übersetzung zu synchronisieren.

Füllen Sie Ihre Sprachkopie so, dass sie Inhalte aus der Master-Sprache enthält, die Sie übersetzen. Bevor Sie Ihre Sprachkopie ausfüllen, müssen Sie [den Sprachstamm](preparation.md#creating-a-language-root) der Sprachkopie erstellt haben.

1. Verwenden Sie die Sites-Konsole, um den Sprachstamm der Übergeordnet verwendeten Sprache auszuwählen, die Sie als Quelle verwenden.
1. Öffnen Sie die Bezugsleiste, indem Sie in der Symbolleiste auf **Referenzen** klicken oder darauf tippen.

   ![Verweise](../assets/references.png)

1. Wählen Sie **Sprachkopien** und wählen Sie dann die Sprachkopien aus, die Sie ausfüllen möchten.

   ![Sprachkopien auswählen](../assets/language-copy-structure-select.png)

1. Klicken oder tippen Sie auf **Sprachkopien aktualisieren**, um die Übersetzungstools anzuzeigen und die Eigenschaften zu konfigurieren:

   * Wählen Sie die Option **Alle Unterseiten** aus.
   * Wählen Sie für **Projekt** **Nur Struktur erstellen**.

   ![Nur Struktur](../assets/language-copy-structure-only.png)

1. Klicken Sie auf oder tippen Sie auf **Aktualisieren**.

### Aktualisieren des Translation Memory {#updating-translation-memory}

Für manuelle Bearbeitungen von übersetzten Inhalten kann wieder eine Synchronisierung mit dem System für die Übersetzungsverwaltung (Translation Management System, TMS) durchgeführt werden, um das Translation Memory zu trainieren.

1. Wählen Sie in der Sites-Konsole nach der Aktualisierung des Textinhalts auf einer übersetzten Seite **Translation Memory** aktualisieren.
1. In einer Listenansicht werden die Quelle und die Übersetzung für jede bearbeitete Textkomponente nebeneinander verglichen. Wählen Sie aus, welche Übersetzungsaktualisierungen mit dem Translation Memory synchronisiert werden sollen, und wählen Sie **Speicher aktualisieren**.

![Änderungen im Translation Memory vergleichen](../assets/update-translation-memory-compare.png)

AEM sendet eine XML-Darstellung der ausgewählten Zeichenfolgen zurück an das Translation Management System.

### Überprüfen des Übersetzungsstatus einer Seite {#check-translation-status}

Eine Eigenschaft kann in der Ansicht &quot;Liste&quot;der Site-Konsole ausgewählt werden, die anzeigt, ob eine Seite übersetzt wurde, sich in der Übersetzung befindet oder noch nicht übersetzt wurde.

1. Wechseln Sie in der Site-Konsole zu [Liste-Ansicht.](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
1. Tippen oder klicken Sie auf **Ansicht Settings** in der Dropdown-Liste Ansicht.
1. Markieren Sie im Dialogfeld die Eigenschaft **Translated** und tippen oder klicken Sie auf **Update**.

Die Sites-Konsole zeigt jetzt die Spalte **Übersetzt** mit dem Übersetzungsstatus der aufgelisteten Seiten an.

![Übersetzungsstatus in der Ansicht der Liste](../assets/translation-status-list-view.png)

## Verwalten von Übersetzungsprojekten über die Projektkonsole

Auf viele Aufgaben und erweiterte Optionen kann in der Projektkonsole zugegriffen werden.

### Die Projektkonsole

Übersetzungsprojekte in AEM verwenden die standardmäßige Projektkonsole [AEM.](/help/sites-cloud/authoring/projects/overview.md) Wenn Sie mit AEM Projekten nicht vertraut sind, lesen Sie bitte die Dokumentation.

Wie jedes andere Projekt besteht auch ein Übersetzungsprojekt aus Kacheln, die einen Überblick über die Aufgaben des Projekts bieten.

![Übersetzungsprojekt](../assets/translation-project.png)

* **Zusammenfassung**  - Ein Überblick über das Projekt
* **Aufgaben**  - Eine oder mehrere Aufgaben
* **Team**  - Benutzer arbeiten am Übersetzungsprojekt zusammen
* **Aufgaben** : Elemente, die im Rahmen des Übersetzungsprozesses ausgefüllt werden müssen

Verwenden Sie die Befehle und die Auslassungsschaltflächen am oberen bzw. unteren Rand der Kacheln, um Zugriffskontrollen und Optionen für die verschiedenen Kacheln anzuzeigen.

![Schaltfläche &quot;Befehle&quot;](../assets/context.png)

![Schaltfläche mit Auslassungspunkten](../assets/ellipsis.png)

### Erstellen von Übersetzungsprojekten mithilfe der Projektekonsole {#creating-a-translation-project-using-the-projects-console}

Sie können ein Übersetzungsprojekt manuell erstellen, wenn Sie lieber die Projektkonsole anstelle der Sites-Konsole verwenden möchten.

>[!NOTE]
>
>Um ein Projekt zu erstellen, muss Ihr Konto Mitglied der Gruppe `project-administrators` sein.

Wenn Sie ein Übersetzungsprojekt manuell erstellen, müssen Sie neben den [grundlegenden Eigenschaften](/help/sites-cloud/authoring/projects/managing.md#creating-a-project) Werte für die folgenden übersetzungsspezifischen Eigenschaften angeben:

* **Name:** Projektname
* **Ausgangssprache:** Die Sprache des Quellinhalts
* **Sprache der Zielgruppe:** Die Sprache(n), in die/denen der Inhalt übersetzt wird
   * Wenn mehrere Sprachen ausgewählt sind, wird für jede Sprache im Projekt ein Auftrag erstellt.
* **Übersetzungsmethode:****Wählen Sie „Menschliche Übersetzung“ aus, um anzugeben, dass die Übersetzung manuell durchgeführt werden soll.**

1. Klicken Sie in der Symbolleiste der Projektkonsole auf oder tippen Sie auf **Erstellen**.
1. Wählen Sie die Vorlage **Übersetzungsprojekt** und klicken Sie dann auf **Weiter** oder tippen Sie darauf.
1. Geben Sie Werte für die Registerkarte &quot;**Einfach**&quot;Eigenschaften ein.
1. Klicken Sie auf oder tippen Sie auf **Erweitert** und geben Sie Werte für die übersetzungsbezogenen Eigenschaften ein.
1. Klicken oder tippen Sie auf **Erstellen**. Klicken Sie im Bestätigungsfeld auf oder tippen Sie auf **Fertig**, um zur Projektkonsole zurückzukehren, oder klicken oder tippen Sie auf **Projekt öffnen**, um das Projekt zu öffnen und Beginn zu verwalten.

### Hinzufügen von Seiten und Assets zu einem Übersetzungsauftrag {#adding-pages-assets-to-a-translation-job}

Sie können dem Übersetzungsauftrag Ihres Übersetzungsprojekts Seiten, Assets oder Tags hinzufügen. So fügen Sie Seiten oder Assets hinzu:

1. Klicken Sie am unteren Rand der Übersetzungsauftragskachel Ihres Übersetzungsprojekts auf oder tippen Sie auf das Auslassungszeichen.

   ![Titel des Übersetzungsauftrags](../assets/translation-job.png)

1. Klicken Sie im nächsten Fenster in der Symbolleiste auf die Schaltfläche **Hinzufügen** und wählen Sie **Assets/Pages**.

   ![hinzufügen](../assets/add-to-project.png)

1. Wählen Sie im modalen Fenster das oberste Element der Verzweigung aus, die Sie hinzufügen möchten, und klicken Sie dann auf das Häkchensymbol oder tippen Sie darauf. In diesem Fenster ist die Mehrfachauswahl aktiviert.

   ![Seiten auswählen](../assets/select-pages.png)

1. Alternativ können Sie das Symbol „Suchen“ auswählen, um schnell und einfach nach Seiten oder Assets zu suchen, die Sie Ihrem Übersetzungsauftrag hinzufügen möchten.

   ![Suchen nach Inhalt](../assets/search-for-content.png)

1. Tippen oder klicken Sie nach Auswahl auf **Auswahl**. Ihre Seiten und/oder Assets werden dem Übersetzungsauftrag hinzugefügt.

>[!TIP]
>
>Diese Methode fügt dem Projekt Seiten/Assets und deren untergeordnete Elemente hinzu. Wählen Sie **Asset/Seite (ohne untergeordnete Elemente)**, wenn Sie nur die übergeordneten Elemente hinzufügen möchten.

### Hinzufügen von Tags zu einem Übersetzungsauftrag {#adding-tags-to-a-translation-job}

Sie können Tags zu einem Übersetzungsprojekt hinzufügen, ähnlich wie [wie Sie Assets und Seiten zu einem Projekt hinzufügen.](#adding-pages-assets-to-a-translation-job) Wählen Sie einfach  **** Tags unter dem Menü  **** Hinzufügen und folgen Sie dann den gleichen Schritten.

### Anzeigen von Details eines Übersetzungsprojekts {#seeing-translation-project-details}

Auf die Eigenschaften des Übersetzungsprojekts kann über die Auslassungsschaltfläche der Kachel &quot;Projektzusammenfassung&quot;zugegriffen werden. Zusätzlich zu den generischen [Projektinformationen](/help/sites-cloud/authoring/projects/overview.md#project-info) enthalten die Eigenschaften des Übersetzungsprojekts übersetzungsspezifisch.

Klicken oder tippen Sie in Ihrem Übersetzungsprojekt unten auf der Kachel Zusammenfassung der Übersetzung auf die Auslassungspunkte. Die meisten projektspezifischen Eigenschaften befinden sich auf der Registerkarte **Erweitert**.

* **Ausgangssprache:** Die Sprache der zu übersetzenden Seiten
* **Sprache der Zielgruppe:** Die Sprache(n), in die/denen die Seiten übersetzt werden
* **Cloud-Konfiguration:** Die Cloud-Konfiguration für den Übersetzungs-Service-Connector, der für das Projekt verwendet wird
* **Übersetzungsmethode:** Der Übersetzungs-Workflow, entweder  **Human** Translation oder  **Machine Translation**
* **Übersetzungsanbieter:** Der Dienstleister, der die Übersetzung ausführt
* **Content-Kategorie:** (maschinelle Übersetzung) Die Content-Kategorie, die für die Übersetzung verwendet wird
* **Berechtigung für Übersetzungsanbieter:** Die Anmeldeinformationen, die beim Anbieter angemeldet werden sollen
* **Automatische Förderung von Übersetzungsstarts:** Nach Erhalt übersetzter Inhalte werden Übersetzungsstarts automatisch gefördert
   * **Nach der Promotion starten löschen:** Wenn Übersetzungsstarts automatisch beworben werden, löschen Sie den Start nach der Promotion
* **Übersetzungen automatisch genehmigen:** Nach Erhalt übersetzter Inhalte werden Übersetzungsaufträge automatisch genehmigt
* **Wiederholte Übersetzung:** Konfigurieren Sie die wiederholte Ausführung eines Übersetzungsprojekts, indem Sie die Häufigkeit auswählen, mit der das Projekt automatisch Übersetzungsaufträge erstellt und ausführt

Wenn ein Projekt mithilfe der Bezugsleiste einer Seite erstellt wird, werden diese Eigenschaften automatisch auf der Grundlage der Eigenschaften der Quellseite konfiguriert.

![Eigenschaften von Übersetzungsprojekten](../assets/translation-project-properties.png)

### Überwachen des Status von Übersetzungsaufträgen {#monitoring-the-status-of-a-translation-job}

Die Kachel des Übersetzungsauftrags eines Übersetzungsprojekts enthält den Status eines Übersetzungsauftrags sowie die Anzahl der Seiten und Assets im Auftrag.

![Übersetzungsauftrag](../assets/translation-job.png)

Die folgende Tabelle beschreibt die einzelnen Status, die ein Auftrag oder ein Element im Auftrag haben kann:

| Status | Beschreibung |
|---|---|
| **Draft** | Der Übersetzungsauftrag wurde noch nicht gestartet. Übersetzungsaufträge erhalten beim Erstellen den Status **Entwurf****. |
| **Übermittelt** | Dateien im Übersetzungsauftrag erhalten diesen Status, wenn sie erfolgreich an den Übersetzungsdienst gesendet wurden. Dieser Status kann nach der Ausgabe des Befehls **Anforderungsbereich** oder des Befehls **Beginn** auftreten. |
| **Berechnung angefragt** | Für den Arbeitsablauf für die manuelle Übersetzung wurden die Dateien des Auftrags zum Scoping an den Übersetzungsdienstleister gesendet. Dieser Status wird angezeigt, nachdem der Befehl **Anforderungsbereich** ausgegeben wurde. |
| **Berechnung abgeschlossen** | Der Verkäufer hat den Übersetzungsauftrag abgespielt. |
| **Übersetzungsauftrag** | Der Projekteigentümer hat den Anwendungsbereich akzeptiert. Dieser Status zeigt an, dass der Übersetzungsanbieter mit der Übersetzung der Dateien im Auftrag beginnen soll. |
| **Übersetzung läuft** | Bei einem Auftrag ist die Übersetzung einer oder mehrerer Dateien im Auftrag noch nicht abgeschlossen. Hinsichtlich eines Elements im Auftrag besagt der Status, dass das Element übersetzt wird. |
| **Übersetzt** | Bei einem Auftrag ist die Übersetzung aller Dateien im Auftrag abgeschlossen. Hinsichtlich eines Elements im Auftrag besagt der Status, dass das Element übersetzt ist. |
| **Bereit für Review** | Das Element im Auftrag wird übersetzt und die Datei wurde in AEM importiert. |
| **Fertig stellen** | Der Projekteigentümer hat mitgeteilt, dass der Übersetzungsvertrag abgeschlossen ist. |
| **Abbrechen** | Gibt an, dass der Übersetzungsanbieter die Arbeit an einem Übersetzungsauftrag beenden soll. |
| **Fehler-Aktualisierung** | Beim Übertragen von Dateien zwischen AEM und dem Übersetzungsdienst ist ein Fehler aufgetreten. |
| **Unbekannter Status** | Es ist ein unbekannter Fehler aufgetreten. |

Klicken oder tippen Sie auf die Ellipse am unteren Rand der Kachel, um den Status der einzelnen Dateien im Auftrag anzuzeigen.

### Festlegen des Fälligkeitsdatums von Übersetzungsaufträgen {#setting-the-due-date-of-translation-jobs}

Geben Sie das Datum an, bis zu dem Ihr Übersetzungsanbieter die übersetzten Dateien zurückgeben muss. Die Festlegung eines Fälligkeitsdatums funktioniert nur dann richtig, wenn der Übersetzungsanbieter diese Funktion unterstützt.

1. Klicken oder tippen Sie auf das Auslassungszeichen am unteren Rand der Kachel für die Übersetzungszusammenfassung.

   ![Übersetzungszusammenfassungselement](../assets/translation-summary-tile.png)

1. Wählen Sie auf der Registerkarte **Einfach** mit der Datumsauswahl der Eigenschaft **Fälligkeitsdatum** das Fälligkeitsdatum aus.

   ![Eigenschaften von Übersetzungsprojekten](../assets/translation-project-properties-basic.png)

1. Klicken Sie auf oder tippen Sie auf **Speichern &amp; Schließen**.

### Berechnen des Umfangs eines Übersetzungsauftrags {#scoping-a-translation-job}

Berechnen Sie den Umfang eines Übersetzungsauftrags, um eine Kostenschätzung für die Übersetzung von Ihrem Übersetzungsdienstanbieter zu erhalten. Wenn Sie den Umfang eines Auftrags berechnen, werden die Quelldateien an den Übersetzungsanbieter übermittelt, der den Text mit seinem Pool an gespeicherten Übersetzungen (Translation Memory) vergleicht. Normalerweise ist der Umfang die Anzahl an Wörtern, die übersetzt werden müssen.

Weitere Informationen zu den Umfangsberechnungsergebnissen erhalten Sie von Ihrem Übersetzungsanbieter.

>[!NOTE]
>
>Scoping ist optional und gilt nur für die menschliche Übersetzung. Sie können einen Übersetzungsauftrag auch ohne Berechnung des Umfangs starten.

Wenn Sie den Umfang eines Übersetzungsauftrags berechnen, lautet der Status des Auftrags **Berechnung angefragt**. Wenn der Übersetzungsanbieter die Berechnung des Umfangs übermittelt, wechselt der Status zu **Berechnung abgeschlossen**. Nach Abschluss des Scoping können Sie den Befehl **Scope anzeigen** verwenden, um die Scoping-Ergebnisse zu überprüfen.

Die Umfangsberechnung funktioniert nur dann richtig, wenn der Übersetzungsanbieter diese Funktion unterstützt.

1. Öffnen Sie in der Projektkonsole Ihr Übersetzungsprojekt.
1. Tippen oder klicken Sie im Titel des Übersetzungsauftrags auf das Menü &quot;Befehle&quot;und dann auf **Anforderungsbereich**.
1. Wenn der Auftragsstatus in **Bereich Abgeschlossen** geändert wird, klicken Sie auf oder tippen Sie auf das Befehlsmenü und dann auf **Bereich anzeigen**.

### Starten von Übersetzungsaufträgen {#starting-translation-jobs}

Starten Sie einen Übersetzungsauftrag, um die Quellseiten in die Zielsprache zu übersetzen. Die Übersetzung wird entsprechend den Eigenschaftswerten der Übersetzungszusammenfassungskachel durchgeführt.

Sie können einen einzelnen Auftrag aus dem Projekt heraus Beginn haben.

1. Öffnen Sie in der Projektkonsole das Übersetzungsprojekt.
1. Klicken Sie auf der Kachel des Übersetzungsauftrags auf das Menü &quot;Befehle&quot;oder tippen Sie dann auf **Beginn** oder klicken Sie darauf.
1. Klicken Sie im Aktionsdialogfeld, das den Beginn der Übersetzung bestätigt, auf oder tippen Sie auf **Schließen**.

Nach dem Beginn des Übersetzungsauftrags zeigt die Kachel des Übersetzungsauftrags die Übersetzung im Status **Wird ausgeführt** an.

Sie können auch alle Übersetzungsaufträge für ein Projekt Beginn haben.

1. Wählen Sie in der Projektkonsole das Übersetzungsprojekt aus.
1. Tippen oder klicken Sie in der Symbolleiste auf **Übersetzungsauftrag(e)** für Beginn.
1. Überprüfen Sie im Dialogfeld die Liste der Aufträge, die gestartet werden, und bestätigen Sie dann mit **Beginn** oder Abbrechen mit **Abbrechen**.

### Abbrechen von Übersetzungsaufträgen {#canceling-a-translation-job}

Brechen Sie einen Übersetzungsauftrag ab, um den Übersetzungsprozess anzuhalten und den Übersetzungsanbieter daran zu hindern, weitere Übersetzungen auszuführen. Sie können Aufträge mit dem Status **Übersetzung beauftragt** oder **Übersetzung läuft** abbrechen.

1. Öffnen Sie in der Projektkonsole das Übersetzungsprojekt.
1. Klicken Sie auf der Kachel des Übersetzungsauftrags auf oder tippen Sie auf das Menü &quot;Befehle&quot;und dann auf **Abbrechen**.
1. Klicken Sie im Aktionsdialogfeld, das die Löschung der Übersetzung bestätigt, auf oder tippen Sie auf **OK**.

### Workflow {#accept-reject-workflow} akzeptieren und ablehnen

Wenn der Inhalt nach der Übersetzung zurückkommt und sich im Status **Bereit für Überprüfung** befindet, können Sie den Übersetzungsauftrag aufrufen und Inhalte akzeptieren/ablehnen.

Wenn Sie **Übersetzung ablehnen** auswählen, haben Sie die Möglichkeit, einen Kommentar hinzuzufügen.

Wenn Inhalte abgelehnt werden, wird sie an den Übersetzungsanbieter zurückgesendet, wo sie den Kommentar sehen können.

### Abschließen und Archivieren von Übersetzungsaufträgen {#completing-and-archiving-translation-jobs}

Schließen Sie einen Übersetzungsauftrag ab, nachdem Sie die übersetzten Dateien vom Anbieter überprüft haben.

1. Öffnen Sie in der Projektkonsole das Übersetzungsprojekt.
1. Klicken Sie auf der Kachel des Übersetzungsauftrags auf das Menü &quot;Befehle&quot;oder tippen Sie dann auf **Complete** oder klicken Sie auf Complete.
1. Der Auftrag hat jetzt den Status **Complete**.

Bei Workflows einer Übersetzung zeigt das Abschließen einer Übersetzung dem Anbieter an, dass der Übersetzungsvertrag erfüllt wurde und die Übersetzung in seinem Translation Memory gespeichert werden sollte.

Archivieren Sie einen Übersetzungsauftrag, nachdem er abgeschlossen ist und Sie die Auftragsstatusdetails nicht länger einsehen müssen.

1. Öffnen Sie in der Projektkonsole das Übersetzungsprojekt.
1. Klicken Sie auf der Kachel des Übersetzungsauftrags auf das Menü &quot;Befehle&quot;oder tippen Sie dann auf **Archivieren** oder klicken Sie darauf.

Wenn Sie den Auftrag archivieren, wird die Kachel des Übersetzungsauftrags aus dem Projekt entfernt.

## Überprüfen und Verwenden von übersetzten Inhalten {#reviewing-and-promoting-updated-content}

Sie können die Sites-Konsole verwenden, um Inhalte zu überprüfen, Sprachkopien zu vergleichen und den Inhalt zu aktivieren.

### Hochstufen von aktualisierten Inhalten {#promoting-updated-content}

Wenn Inhalte für eine vorhandene Sprachkopie übersetzt werden, überprüfen Sie die Übersetzungen, nehmen Sie bei Bedarf Änderungen vor und leiten Sie dann die Übersetzungen weiter, um die Übersetzungen in die Sprachkopie zu verschieben. Sie können übersetzte Dateien überprüfen, wenn der Übersetzungsauftrag den Status **Bereit für Überprüfung** anzeigt.

![Überprüfungsbereit](../assets/job-ready-for-review.png)

1. Wählen Sie die Seite Übergeordnet aus, klicken Sie auf oder tippen Sie auf **References** und klicken Sie dann auf **Sprachkopien** oder klicken Sie auf Sprachkopien.
1. Klicken bzw. tippen Sie auf die zu überprüfende Sprachkopie.

   ![Sprachkopie zum Review bereit](../assets/language-copy-ready-for-review.png)

1. Klicken Sie auf oder tippen Sie auf **Launch**, um die startbezogenen Befehle anzuzeigen.

   ![Starten](../assets/language-copy-launch.png)

1. Um die Startkopie der Seite zum Überprüfen und Bearbeiten des Inhalts zu öffnen, klicken Sie auf **Seite öffnen**.
1. Nachdem Sie den Inhalt geprüft und die erforderlichen Änderungen vorgenommen haben, klicken Sie zum Anzeigen der Startkopie auf **Fördern**.
1. Geben Sie auf der Seite **Launch fördern** an, welche Seiten beworben werden sollen, und klicken Sie dann auf **Fördern**.

### Vergleichen von Sprachkopien {#comparing-language-copies}

So vergleichen Sie Sprachkopien mit Übergeordnet:

1. Navigieren Sie in der Sites-Konsole zu der Sprachkopie, die Sie vergleichen möchten.
1. Öffnen Sie die Leiste [Referenzen.](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)
1. Wählen Sie unter der Überschrift **Kopien** **Sprachkopien.**
1. Wählen Sie die gewünschte Sprachkopie aus und klicken Sie dann entweder auf **Mit Übergeordnet** vergleichen oder auf **Mit Vorherigen vergleichen** (falls zutreffend).

   ![Vergleichen von Sprachkopien](../assets/language-copy-compare.png)

1. Die beiden Seiten (Launch und Quelle) werden nebeneinander geöffnet.
   * Weitere Informationen zur Verwendung dieser Funktion finden Sie unter [Seitenvergleich](/help/sites-cloud/authoring/features/page-diff.md).

## Importieren und Exportieren von Übersetzungsaufträgen {#import-export}

Obwohl AEM Angebote eine Reihe von Übersetzungslösungen und -schnittstellen bieten, ist es auch möglich, Übersetzungsauftragsinformationen manuell zu importieren und zu exportieren.

### Exportieren von Übersetzungsaufträgen {#exporting-a-translation-job}

Sie können die Inhalte eines Übersetzungsauftrags herunterladen, um sie z. B. an einen Übersetzungsanbieter zu senden, der nicht über einen Connector in AEM integriert ist, oder um die Inhalte zu überprüfen.

1. Klicken Sie im Dropdownmenü der Kachel des Übersetzungsauftrags auf oder tippen Sie auf **Export**.
1. Klicken Sie im Dialogfeld auf oder tippen Sie auf **Exportierte Datei herunterladen** und speichern Sie die Datei gegebenenfalls im Webbrowser-Dialogfeld.
1. Klicken Sie im Dialogfeld auf oder tippen Sie auf **Schließen**.

### Importieren von Übersetzungsaufträgen {#importing-a-translation-job}

Sie können übersetzte Inhalte in AEM importieren, zum Beispiel wenn Ihr Übersetzungsanbieter die Inhalte an Sie sendet, da er nicht über einen Connector in AEM integriert ist.

1. Klicken Sie im Dropdownmenü der Kachel des Übersetzungsauftrags auf oder tippen Sie auf **Import**.
1. Wählen Sie im Dialogfeld des Webbrowsers die zu importierende Datei aus.
1. Klicken Sie im Dialogfeld auf oder tippen Sie auf **Schließen**.
