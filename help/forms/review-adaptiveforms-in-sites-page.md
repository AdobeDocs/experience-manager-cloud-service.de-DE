---
title: Übermittlung eines adaptiven Formulars zur Überprüfung Wie werden Überprüfungen für ein adaptives AEM-Formular verwaltet?
description: Die Überprüfung ist ein Mechanismus, mit dem Überprüfende mithilfe des Schritts „Aufgabe zuweisen“ verschiedene Aufgaben für adaptive Formulare durchführen können.
feature: Adaptive Forms
hide: true
hidefromtoc: true
role: User
exl-id: e53535a8-cd6b-4f30-9523-773243098757
source-git-commit: a9adbb1886dcfedfc3fccb6f56939c46ba1365ee
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 100%

---

# Erstellen und Verwalten von Überprüfungen eines adaptiven Formulars {#review-step-forms-aem-sites-page}

Unter Verwendung von [Schritt zuweisen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?lang=de#assign-task-step) des AEM-Workflows prüfen Überprüfende das gesendete Formular und führt Aktionen dafür durch. Gehen Sie wie folgt vor, um das gesendete Formular mit dem Schritt „Aufgabe zuweisen“ zu überprüfen:

1. [Erstellen eines AEM-Workflows](#create-an-aem-workflow)
1. [Konfigurieren der Übermittlungsaktion des Containers für adaptive Formulare](#configure-submit-action)
1. [Übermittlung eines adaptiven Formulars nach Überprüfung](#submit-af-after-review)

## Erstellen eines AEM-Workflows {#create-an-aem-workflow}

1. Öffnen Sie Ihre Autoreninstanz im Bearbeitungsmodus.
1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL Erstellen]** > **[!UICONTROL Modell erstellen]**
1. Geben Sie den Titel des Workflows an und fügen Sie den Schritt **[Aufgabe zuweisen]** hinzu
1. Wählen Sie ![settings_icon](assets/settings_icon.png) in der Aktionsleiste. Das Dialogfeld **[!UICONTROL Aufgabe zuweisen]** wird geöffnet.
1. Öffnen Sie die Registerkarte [!UICONTROL Formular und Dokument] und öffnen Sie das Dropdown-Menü [!UICONTROL Vorausgefüllt] und geben Sie Folgendes an:

   * Eingabedatei auswählen mit
   * Eingabeanhänge auswählen mit

   ![Schritt überprüfen](/help/forms/assets/assigntask-review1.gif)

1. Öffnen Sie die Registerkarte **[!UICONTROL Bevollmächtigte Person]** und öffnen Sie das Dropdown-Menü [!UICONTROL Vorausgefüllt] und geben Sie **[!UICONTROL Optionen zuweisen]** wie folgt an:

   ![Schritt überprüfen](/help/forms/assets/review-assignstep.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern.

## Konfigurieren der Übermittlungsaktion {#configure-submit-action}

Konfigurieren Sie nun die Übermittlungsaktion einer Container-Komponente für adaptive Formulare auf der Sites-Seite:

1. Navigieren Sie zur Sites-Seite.
1. Wählen Sie ![settings_icon](assets/settings_icon.png) eines Containers für adaptive Formulare. Das Dialogfeld **[!UICONTROL Container für adaptive Formulare]** wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]** und geben Sie **[!UICONTROL Übermittlungsaktion]** an, um [einen AEM-Workflow auszulösen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=de#invoke-an-aem-workflow)

1. Klicken Sie auf [Fertig], um die Einstellungen zu speichern.

![submissiontab-reviewstep](/help/forms/assets/submissiontab-reviewstep.gif)

## Übermittlung eines adaptiven Formulars nach Überprüfung {#submit-af-after-review}

So überprüfen und bestätigen Sie das gesendete adaptive Formular:

1. Gehen Sie zu [!UICONTROL Tools] > [!UICONTROL Workflow] > [!UICONTROL Instanzen]
1. Im Posteingang sehen Sie, dass eine Instanz erstellt wird.
1. Wählen Sie die Instanz aus und klicken Sie auf [!UICONTROL Öffnen].
1. Jetzt können Sie das gesendete Formular sehen.

Überprüfende führen verschiedene Aktionen durch:

* **Übermitteln**: Die Überprüfenden füllen das Formular aus und senden es zur weiteren Verarbeitung.
* **Speichern**: Die Überprüfenden speichern das Formular in ihrem aktuellen Status, ohne zu übermitteln.
* **Zurücksetzen**: Die Überprüfenden löschen alle Änderungen, die am Formular vorgenommen wurden, und stellen es in den Originalzustand zurück.
* **Delegieren**: Die Überprüfenden übertragen das Eigentum an dem Formular zur weiteren Bearbeitung oder Überprüfung an eine andere Person.
