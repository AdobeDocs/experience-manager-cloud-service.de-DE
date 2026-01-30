---
title: Erste Schritte mit dem Experience Modernization Agent
description: Lernen Sie die ersten Schritte kennen, um mit dem Experience Modernization Agent mithilfe der Experience Modernization Console schnell produktiv zu werden.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: c80ce5a9fc5f208fd910d5cef72225085248fb4d
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 0%

---


# Erste Schritte mit dem Experience Modernization Agent {#getting-started}

Lernen Sie die ersten Schritte kennen, um mit dem Experience Modernization Agent mithilfe der Experience Modernization Console schnell produktiv zu werden.

>[!NOTE]
>
>Wenn Sie an der Verwendung der Experience Modernization Console interessiert sind, können Sie Zugriff anfordern, um ein reibungsloses Onboarding-Erlebnis zu gewährleisten.

## Vorbereiten eines Edge Delivery GitHub-Repositorys {#prepare-repo}

1. Wählen Sie ein [Edge Delivery Services](/help/edge/overview.md)-Repository zur Verwendung mit der Experience Modernization Console aus.
   * Dabei kann es sich um ein bestehendes Edge Delivery Services-Projekt handeln. Sie können aber auch nach dem [Entwickler-Tutorial](https://www.aem.live/developer/tutorial) ein neues erstellen, indem Sie das [Textbausteinrepository“ verwenden.](https://github.com/adobe/aem-boilerplate)
1. Stellen Sie sicher, dass [AEMY GitHub](https://github.com/apps/aem-aemy)App) im Repository installiert ist.
   * Dadurch kann die Konsole Ihren Code überprüfen.
1. Stellen Sie sicher, dass die [AEM Code Sync GitHub](https://github.com/apps/aem-code-sync)App im Repository installiert ist.
   * Dadurch kann Edge Delivery Services Ihren Code synchronisieren.
   * Wenn Ihr Repository auf dem Tutorial basiert, ist dieser Schritt bereits abgeschlossen.

## Öffnen der Experience Modernization Console {#open-console}

1. Navigieren Sie zu [`aemcoder.adobe.io`.](https://aemcoder.adobe.io)
1. Melden Sie sich mit Ihrer Adobe ID an.

## Verbinden Ihres GitHub-Repositorys {#connect-repo}

Die Konsole fordert Sie bei der ersten Anmeldung zur Angabe eines Repositorys auf.

![Erster Anmeldebildschirm der Konsole](assets/first-sign-on.png)

1. Klicken Sie auf **Repository verbinden**.
1. Dadurch wird die AEM-App auf einer neuen Browser-Registerkarte geöffnet. Klicken Sie **AEM AEMY autorisieren**.
1. Wählen Sie zurück in der Konsole **Inhaber**, **Repository** und **Verzweigungsauswahl** und klicken Sie auf **In Arbeitsbereich auschecken**.
   ![Verbindung zum GitHub-Projekt herstellen](assets/connect-to-github-project.png)
1. Wenn Sie aufgefordert werden **„Vorhandenen Arbeitsbereich ersetzen**, klicken Sie auf **Arbeitsbereich ersetzen**.
   ![Vorhandenen Arbeitsbereich ersetzen](assets/replace-existing-workspace.png)

Ihr GitHub-Projekt ist jetzt mit der Konsole verbunden und Sie befinden sich auf dem Startbildschirm.

![Konsole - Startseite](assets/console-home.png)

## Eingabeaufforderung starten {#start-prompting}

Jetzt, da Ihre Konsole auf Ihren Code zugreifen kann, können Sie mit der Eingabeaufforderung beginnen.

1. Zu Beginn können Sie den Inhalt einer Site importieren:
   * „Migrieren Sie die `https://wknd-trendsetters.site`.“
1. Dadurch wird der Inhalt der Site importiert.
   * Die Konsole beobachtet die Trennung von Belangen und verarbeitet Inhalte und Präsentation separat.
   * Der erste Import des Inhalts einer Site kann mehrere Minuten dauern.
   * Die Konsole bietet Ihnen laufendes Feedback zu Beginn ihrer Arbeit, einschließlich eines Überblicks über die geplanten Schritte.
     ![Content-Import](assets/content-import.png)
1. Nachdem die Site importiert wurde, werden die Seiten im Bedienfeld **Workspace** angezeigt. Wählen Sie eine Seite aus, um sie im rechten Bedienfeld in der Vorschau anzuzeigen.
   ![Inhalt importiert](assets/content-imported.png)
1. Nachdem Sie nun über Inhalte verfügen, können Sie auffordern, die Stile aus derselben Quelle zu importieren.
   * „Importieren Sie die allgemeinen Stile aus `https://wknd-trendsetters.site`.“
1. Wie beim ersten Inhaltsimport kann der Import mehrere Minuten dauern. Die Konsole gibt Feedback bei der Verarbeitung Ihrer Anfrage und beim Importieren der Stile. Sobald die Aufgabe abgeschlossen ist, klicken Sie im rechten Bedienfeld **Vorschau aktualisieren**, um den formatierten Inhalt anzuzeigen.
   ![Stile importiert](assets/styles-imported.png)

Jetzt haben Sie sowohl den Inhalt als auch die Stile in die Konsole importiert.

## Inhalt hochladen {#upload-content}

So laden Sie Ihre Inhalte in [Dokumenterstellung](https://da.live) hoch:

1. Stellen Sie sicher, dass Sie sich in der **Inhalt** befinden, und klicken Sie dann oben rechts auf **Schaltfläche** Inhalt hochladen.
   * Standardmäßig befinden Sie sich in der **Content**-Ansicht, wenn Sie die Konsole aufrufen.
   * Ihre Ansicht wird durch das hervorgehobene Symbol in der Seitenleiste auf der linken Seite der Konsole angezeigt.
1. Das Dialogfeld **Inhalt hochladen** wird mit der Ziel-Organisation und dem Repository geöffnet, die aus Ihrer `fstab.yaml` vorausgefüllt sind.
   * Wenn in Ihrem verbundenen Repository keine `fstab.yaml` vorhanden ist, müssen Sie Ihre **Organisation“** „Repository **manuell**.
   * Wenn Sie das Textbaustein verwendet haben, wird ein `fstab.yaml` bereitgestellt.
1. Wählen Sie die Dateien aus, die Sie hochladen möchten, und klicken Sie auf **Hochladen**.
   ![Dialogfeld „Inhalt hochladen“](assets/upload-content.png)
1. Die Konsole zeigt den Upload-Prozess durch Ausgrauen der Schaltfläche **Hochladen** an.
   ![Upload](assets/uploading.png)
1. Nach Abschluss des Vorgangs wird unten in der Konsole eine Benachrichtigung angezeigt.
   ![In AEM anzeigen](assets/view-in-aem.png)

Um auf die hochgeladenen Inhalte in der Dokumenterstellung zuzugreifen, klicken Sie optional auf **In AEM anzeigen** in der Benachrichtigung, wenn der Upload abgeschlossen ist, oder navigieren Sie zu `https://da.live/#/{organization}/{repository}`.

![Inhalt beim Erstellen von Dokumenten](assets/content-in-document-authoring.png)

Ihr importierter Inhalt befindet sich jetzt in der Dokumenterstellung.

## Push-Code-Änderungen {#push-code-changes}

Sobald Sie mit den Änderungen zufrieden sind, die Sie an Ihrem Code vorgenommen haben, können Sie sie an Ihr GitHub-Repository pushen.

1. Wechseln Sie zur **Code**-Ansicht (`</>`-Symbol in der linken Seitenleiste) und dann zur Registerkarte **Git-**&quot; (Verzweigungs-Symbol oben rechts).
   ![Code-Ansicht](assets/code-view-git-changes.png)
1. Wenn in der Liste der geänderten Dateien einige Dateien als nicht verfolgt angezeigt werden, klicken Sie auf ihre `+`-Schaltfläche, um sie bereitzustellen.
1. Klicken Sie oben rechts auf **GitHub** Aktionen“ und wählen Sie dann **Push** aus der Dropdown-Liste aus.
1. Wählen **Dialogfeld „Änderungen** Push übertragen“, um Änderungen an eine neue PR (Standard) oder die aktuelle Verzweigung zu pushen, und klicken Sie auf **Bestätigen**, um sie zu pushen.
   * Im Zweifelsfall können Sie zum aktuellen Zweig pushen, um die Dinge einfach zu halten.
1. Nach Abschluss des Vorgangs wird unten in der Konsole eine Benachrichtigung angezeigt.
   ![Anzeigen von PR](assets/view-pr.png)

Wenn Sie direkt auf die gepushten Änderungen in GitHub zugreifen möchten, klicken Sie auf **PR anzeigen** in der Benachrichtigung, wenn die Push-Benachrichtigung abgeschlossen ist.

![Code in GitHub](assets/code-in-github.png)

Ihr Code befindet sich jetzt in GitHub.

## Site-Vorschau {#preview-site}

So zeigen Sie die Änderungen in der Vorschau-Umgebung an:

1. Zurück zur Dokumenterstellung.
   * Möglicherweise ist sie weiterhin in einer Browser-Registerkarte geöffnet, die Sie nach dem Hochladen des Inhalts durch Klicken **In AEM anzeigen** geöffnet haben.
   * Oder navigieren Sie zu `https://da.live/#/{organization}/{repository}`
1. Öffnen Sie eine der Seiten, die Sie zuvor in AEM hochgeladen haben.
1. Klicken Sie oben rechts auf das Papierebenensymbol und wählen Sie **Vorschau** aus.
   ![In Vorschau veröffentlichen](assets/publish-to-preview.png)

Herzlichen Glückwunsch! Ihre migrierten Inhalte und Stile sind jetzt in der AEM-Vorschauumgebung verfügbar.

![Veröffentlichte Vorschauinhalte](assets/published-preview.png)

Wenn Sie den Code an eine andere Verzweigung als `main` gepusht haben, werden die Stile in der aus der Dokumenterstellung geöffneten Vorschau nicht angezeigt. Wechseln Sie zur Verzweigung, indem Sie die URL der Vorschau aktualisieren, damit Ihre Stile angezeigt werden.

## Zusätzliche Ressourcen {#additional-resources}

Die folgenden Dokumente können nützlich sein, wenn Sie den Experience Modernization Agent und seine Konsole weiter erkunden.

* [Experience Modernization Console](/help/ai-in-aem/agents/modernization/console.md) - Details zur Konsole, ihren Ansichten, Optionen und Funktionen
* [Edge Delivery Services-Entwickler-](https://www.aem.live/developer/tutorial): Nützlich, wenn Sie neu bei AEM- und Edge Delivery Services-Projekten sind
* [Dokumenterstellung](https://da.live) Nützlich, wenn Sie mit der Dokumenterstellung für das Content-Management noch nicht vertraut sind
