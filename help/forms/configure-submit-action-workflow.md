---
Title: How to integrate AEM workflow with an Adaptive Form?
Description: Explore the process of automated workflow initiation with AEM Forms Submit Action.
keywords: AEM Workflow, Integrieren des adaptiven Formulars in AEM Workflow, Aufrufen AEM Workflow-Übermittlungsaktion
feature: Adaptive Forms, Core Components
source-git-commit: 95af49839d206f67ac02116730229f5b0531c5bb
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 59%

---


# Integrieren AEM adaptiven Formulars in AEM Workflow: Optimierung von Geschäftsprozessen

Die **[!UICONTROL Aufrufen eines AEM Workflows]** Übermittlungsaktion ordnet ein adaptives Formular einem AEM Workflow zu. Wenn ein Formular gesendet wird, startet der verknüpfte Workflow automatisch auf der Autoreninstanz. Sie können die Datendateien, Anlagen und das Datensatzdokument am Payload-Speicherort des Workflows oder in einer Variablen speichern. Wenn der Workflow für die externe Datenspeicherung markiert und für eine externe Datenspeicherung konfiguriert ist, ist nur die Variablenoption verfügbar. Sie können aus der Liste der für das Workflow-Modell verfügbaren Variablen auswählen. Wenn der Workflow für die externe Datenspeicherung zu einem späteren Zeitpunkt und nicht zum Zeitpunkt der Workflow-Erstellung markiert ist, stellen Sie sicher, dass die erforderlichen Variablenkonfigurationen vorhanden sind.

>[!NOTE]
>
>  Erfahren Sie, wie [Erstellen eines Workflow-Modells](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de#extending-aem) , um die Schritte zu definieren, die beim Starten des Workflows ausgeführt werden. Sie können auch Modelleigenschaften definieren, um beispielsweise festzulegen, ob es sich um einen Übergangs-Workflow oder einen Workflow mit mehreren Ressourcen handelt.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Abschnitt [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md)  Artikel.

## Vorteile

Die Integration AEM Workflows in Adaptive Forms bietet unter anderem folgende Vorteile:

* AEM Workflow-Integration ermöglicht die Automatisierung komplexer Geschäftsprozesse bei der Übermittlung von Formularen.
* AEM Workflow unterstützt Bedingungslogik und ermöglicht so dynamische Entscheidungen basierend auf Formulardaten oder externen Faktoren.
* AEM Workflow leitet Aufgaben basierend auf vordefinierten Regeln und Bedingungen weiter und stellt sicher, dass Aufgaben den richtigen Personen oder Gruppen zugewiesen werden.

<!--
## Prerequisites

Before using the **[!UICONTROL Invoke an AEM Workflow]** Submit Action configure the following for the **[!UICONTROL AEM DS settings service]** configuration: 

* **[!UICONTROL Processing Server URL]**: The Processing Server is the server where the Forms or AEM Workflow is triggered. This can be same as the URL of the AEM author instance or another server.

* **[!UICONTROL Processing Server User Name]**: Workflow user's username

* **[!UICONTROL Processing Server Password]**: Workflow user's password -->

## Integrieren AEM Workflows mit Adaptive Forms {#steps-to-integrate-workflow-with-af}

So richten Sie einen automatisierten Prozess ein mit [AEM Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de#extending-aem) Führen Sie für ein adaptives Formular die folgenden Schritte aus:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Aus dem **[!UICONTROL Übermittlungsaktion]** Dropdown-Liste auswählen **[!UICONTROL Aufrufen eines AEM Workflows]** .
   ![Aktionskonfiguration von E-Mail senden](/help/forms/assets/configure-invoke-aem-workflow.png)

1. Wählen Sie das Workflow-Modell aus dem **[!UICONTROL Workflow-Modell]** Dropdown-Liste.
1. Wählen Sie die Option aus dem **[!UICONTROL Datendatei speichern mit]** Dropdown-Liste.

   **Datendatei**: Sie enthält Daten, die an das adaptive Formular gesendet werden. Mit der Option **[!UICONTROL Datendateipfad]** können Sie den Dateinamen und den Dateipfad relativ zur Payload angeben. Beispielsweise erstellt der Pfad `/addresschange/data.xml` einen Ordner mit dem Namen `addresschange` und platziert ihn relativ zur Payload. Sie können auch nur `data.xml` angeben, um nur die übermittelten Daten zu senden, ohne die Erstellung einer Ordnerhierarchie. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

1. Wählen Sie die Option aus dem **[!UICONTROL Speichern von Anlagen mithilfe von]** Dropdown-Liste.

   **Anlagen**: Mit der Option **[!UICONTROL Anlagenpfad]** können Sie den Ordnernamen zum Speichern der in das adaptive Formular hochgeladenen Anlagen angeben. Der Ordner wird immer relativ zur Payload erstellt. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

1. Wählen Sie die Option aus dem **[!UICONTROL Datensatzdokumente mit]** Dropdown-Liste.

   **Datensatzdokument**: Es enthält das Datensatzdokument, das für das adaptive Formular generiert wurde. Mit der Option **[!UICONTROL Pfad des Datensatzdokuments]** können Sie den Dateinamen des Datensatzdokuments sowie den Dateipfad relativ zur Payload angeben. Beispiel: Der Pfad `/addresschange/DoR.pdf` erstellt einen Ordner mit dem Namen `addresschange` relativ zur Payload und platziert `DoR.pdf` relativ zur Payload. Um nur das Datensatzdokument zu speichern, ohne eine Ordnerhierarchie zu erstellen, reicht die Angabe `DoR.pdf`. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!NOTE]
>
> Weitere Informationen [Forms-zentrierte AEM Workflows - Schrittreferenz zur Automatisierung von Geschäftsprozessen](/help/forms/aem-forms-workflow-step-reference.md).

<!--
## Best Practices

* When configuring the **[!UICONTROL Invoke an AEM Workflow]** Submit Action, select the appropriate workflow model that aligns with the desired business process.
* In case, the workflow involves external data storage, be sure to configure the workflow accordingly. It is recommended to set up variables appropriately and in accordance with any external storage requirements. -->

## Ähnliche Artikel

{{af-submit-action}}