---
Title: How to integrate AEM workflow with an Adaptive Form?
Description: Explore the process of automated workflow initiation with AEM Forms Submit Action.
keywords: AEM-Workflow, Integrieren eines adaptiven Formulars in einen AEM-Workflow, Aufrufen der AEM-Workflow-Übermittlungsaktion
feature: Adaptive Forms, Core Components
exl-id: b7788e3d-acd8-4867-b232-f9767cf6b2f5
title: Konfigurieren einer Übermittlungsaktion für ein adaptives Formular
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 100%

---

# Integrieren eines adaptiven AEM-Formulars in einen AEM-Workflow: Optimierung von Geschäftsprozessen

Die Übermittlungsaktion **[!UICONTROL AEM-Workflow aufrufen]** verknüpft ein adaptives Formular mit einem AEM-Workflow. Wenn ein Formular gesendet wird, startet der verknüpfte Workflow automatisch auf der Autoreninstanz. Sie können die Datendateien, Anhänge und das Datensatzdokument am Speicherort der Payload des Workflows oder in einer Variablen speichern. Wenn der Workflow für die externe Datenspeicherung markiert und für eine externe Datenspeicherung konfiguriert ist, ist nur die Variablenoption verfügbar. Sie können aus der Liste der für das Workflow-Modell verfügbaren Variablen auswählen. Wenn der Workflow für die externe Datenspeicherung zu einem späteren Zeitpunkt und nicht zum Zeitpunkt der Workflow-Erstellung markiert ist, stellen Sie sicher, dass die erforderlichen Variablenkonfigurationen vorhanden sind.

>[!NOTE]
>
>  Erfahren Sie, wie Sie [ein Workflow-Modell](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de#extending-aem) erstellen, um die Reihe der Schritte zu definieren, die ausgeführt werden, wenn Benutzende den Workflow starten. Sie können auch Modelleigenschaften definieren, um beispielsweise festzulegen, ob es sich um einen Übergangs-Workflow oder einen Workflow mit mehreren Ressourcen handelt.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md).

## Vorteile

Die Integration von AEM-Workflows in adaptive Formulare bietet unter anderem folgende Vorteile:

* Die AEM-Workflow-Integration ermöglicht die Automatisierung komplexer Geschäftsprozesse bei der Übermittlung von Formularen.
* Der AEM-Workflow unterstützt Bedingungslogik und ermöglicht so dynamische Entscheidungen basierend auf Formulardaten oder externen Faktoren.
* Der AEM-Workflow leitet Aufgaben basierend auf vordefinierten Regeln und Bedingungen weiter und stellt sicher, dass Aufgaben den richtigen Personen oder Gruppen zugewiesen werden.

<!--
## Prerequisites

Before using the **[!UICONTROL Invoke an AEM Workflow]** Submit Action configure the following for the **[!UICONTROL AEM DS settings service]** configuration: 

* **[!UICONTROL Processing Server URL]**: The Processing Server is the server where the Forms or AEM Workflow is triggered. This can be same as the URL of the AEM author instance or another server.

* **[!UICONTROL Processing Server User Name]**: Workflow user's username

* **[!UICONTROL Processing Server Password]**: Workflow user's password -->

## Integrieren von AEM-Workflows mit adaptiven Formularen {#steps-to-integrate-workflow-with-af}

Um einen automatisierten Prozess mit einem [AEM-Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de#extending-aem) für ein adaptives Formular festzulegen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Aktion übermitteln]** die Option **[!UICONTROL AEM-Workflow aufrufen]**.
   ![Aktionskonfiguration von „E-Mail senden“](/help/forms/assets/configure-invoke-aem-workflow.png)

1. Wählen Sie das Workflow-Modell aus der Dropdown-Liste **[!UICONTROL Workflow-Modell]**.
1. Wählen Sie eine Option aus der Dropdown-Liste **[!UICONTROL Datendatei speichern mit]**.

   **Datendatei**: Sie enthält Daten, die an das adaptive Formular gesendet werden. Mit der Option **[!UICONTROL Datendateipfad]** können Sie den Dateinamen und den Dateipfad relativ zur Payload angeben. Beispielsweise erstellt der Pfad `/addresschange/data.xml` einen Ordner mit dem Namen `addresschange` und platziert ihn relativ zur Payload. Sie können auch nur `data.xml` angeben, um nur die übermittelten Daten zu senden, ohne die Erstellung einer Ordnerhierarchie. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

1. Wählen Sie eine Option aus der Dropdown-Liste **[!UICONTROL Anhänge speichern mit]**.

   **Anlagen**: Mit der Option **[!UICONTROL Anlagenpfad]** können Sie den Ordnernamen zum Speichern der in das adaptive Formular hochgeladenen Anlagen angeben. Der Ordner wird immer relativ zur Payload erstellt. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

1. Wählen Sie eine Option aus der Dropdown-Liste **[!UICONTROL Datensatzdokumente mit]**.

   **Datensatzdokument**: Es enthält das Datensatzdokument, das für das adaptive Formular generiert wurde. Mit der Option **[!UICONTROL Pfad des Datensatzdokuments]** können Sie den Dateinamen des Datensatzdokuments sowie den Dateipfad relativ zur Payload angeben. Beispiel: Der Pfad `/addresschange/DoR.pdf` erstellt einen Ordner mit dem Namen `addresschange` relativ zur Payload und platziert `DoR.pdf` relativ zur Payload. Um nur das Datensatzdokument zu speichern, ohne eine Ordnerhierarchie zu erstellen, reicht die Angabe `DoR.pdf`. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!NOTE]
>
> Erfahren Sie mehr über [Formular-orientierte AEM-Workflows – Schrittreferenz zur Automatisierung von Geschäftsprozessen](/help/forms/aem-forms-workflow-step-reference.md).

<!--
## Best Practices

* When configuring the **[!UICONTROL Invoke an AEM Workflow]** Submit Action, select the appropriate workflow model that aligns with the desired business process.
* In case, the workflow involves external data storage, be sure to configure the workflow accordingly. It is recommended to set up variables appropriately and in accordance with any external storage requirements. -->

## Ähnliche Artikel

{{af-submit-action}}
