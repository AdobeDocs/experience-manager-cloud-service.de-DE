---
title: Erstellen und Verwalten von Überprüfungen von adaptiven Forms, die in die Sites-Seite eingebettet oder erstellt wurden
seo-title: Review is a mechanism that allows reviewer to perform different tasks for adaptive forms using Assign Task step
description: '"Überprüfen"ist ein Mechanismus, mit dem der Überprüfer mithilfe des Schritts "Aufgabe zuweisen"verschiedene Aufgaben für adaptive Formulare ausführen kann.'
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: daeb407e27b9f1d390fe40151ca16ec0196712e6
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 6%

---


# Schritt zum Überprüfen von Forms auf der Seite der Site {#review-step-forms-aem-sites-page}

Verwenden der [Schritt zuweisen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html#assign-task-step) des AEM-Workflows prüft der Validierer das gesendete Formular und führt Aktionen dafür durch. Gehen Sie wie folgt vor, um das gesendete Formular mit dem Schritt Aufgabe zuweisen zu überprüfen:

1. [Erstellen eines AEM-Workflows](#create-an-aem-workflow)
1. [Konfigurieren der Sendeaktion des Containers für adaptive Formulare](#configure-submit-action)
1. [Senden eines adaptiven Formulars nach Überprüfung](#submit-af-after-review)

## Erstellen eines AEM-Workflows {#create-an-aem-workflow}

1. Öffnen Sie Ihre Autoreninstanz im Bearbeitungsmodus.
1. Navigieren Sie zu **[!UICONTROL Instrumente]** >  **[!UICONTROL Workflow]** >  **[!UICONTROL Modelle]** > **[!UICONTROL Erstellen]** > **[!UICONTROL Modell erstellen]**
1. Geben Sie den Titel des Workflows an und fügen Sie den **[Aufgabe zuweisen]** Schritt
1. Tippen ![settings_icon](assets/settings_icon.png) in der Aktionsleiste. Die **[!UICONTROL Aufgabe zuweisen]** wird geöffnet.
1. Öffnen [!UICONTROL Formular und Dokument] Registerkarte und öffnen [!UICONTROL Vorausgefüllt] Dropdown-Liste und geben Sie Folgendes an:

   * Eingabedatei auswählen mit
   * Eingabeanhänge auswählen mit

   ![Schritt überprüfen](/help/forms/assets/assigntask-review1.gif)

1. Öffnen **[!UICONTROL Bevollmächtigter]** Registerkarte und öffnen [!UICONTROL Vorausgefüllt] Dropdown-Liste und **[!UICONTROL Optionen zuweisen]**:

   ![Schritt überprüfen](/help/forms/assets/review-assignstep.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern.

## Konfigurieren der Übermittlungsaktion {#configure-submit-action}

Konfigurieren Sie nun die Übermittlungsaktion einer Container-Komponente für adaptive Formulare auf der Seite der Site :

1. Navigieren Sie zur Seite der Site.
1. Tippen ![settings_icon](assets/settings_icon.png) eines Containers für adaptive Formulare. Die **[!UICONTROL Container für adaptive Formulare]** wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Einsendung]** Registerkarte und geben Sie **[!UICONTROL Übermittlungsaktion]** nach [AEM Workflow aufrufen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=en#invoke-an-aem-workflow)

1. Klicken Sie auf [Fertig], um die Einstellungen zu speichern.

![submit-tab-reviewstep](/help/forms/assets/submissiontab-reviewstep.gif)

## Senden eines adaptiven Formulars nach Überprüfung {#submit-af-after-review}

So überprüfen und bestätigen Sie das gesendete adaptive Formular:

1. Navigieren Sie zu [!UICONTROL Instrumente] >  [!UICONTROL Workflow] >  [!UICONTROL Instanzen]
1. Im Posteingang sehen Sie, dass eine Instanz erstellt wird.
1. Wählen Sie die Instanz aus und klicken Sie auf [!UICONTROL Öffnen].
1. Jetzt können Sie das gesendete Formular sehen.

Der Validierer führt verschiedene Aktionen durch:

* **Einsenden**: Der Überprüfer füllt das Formular aus und sendet es zur weiteren Verarbeitung.
* **Speichern**: Der Validierer speichert das Formular in seinem aktuellen Status, ohne es zu übermitteln.
* **Zurücksetzen**: Der Validierer löscht alle Änderungen, die am Formular vorgenommen wurden, und stellt es in den Originalzustand zurück.
* **Delegieren**: Der Validierer überträgt das Eigentum an dem Formular zur weiteren Bearbeitung oder Überprüfung an eine andere Person.
