---
title: Übermittlungs-Workflow für Associate UI - IC-Generierung der PDF-Ausgabe
description: Erfahren Sie, wie Übermittlung und Workflow für die Associate-Benutzeroberfläche funktionieren, und folgen Sie einem Beispiel-Workflow, der PDF aus JSON für interaktive Kommunikation (IC) generiert.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 9d8a33e4-e206-48e6-9daf-b15feb9c67a3
source-git-commit: fa8035f826a4d08c18bc0d2b7664015c6fc82698
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 4%

---

# Übermittlungs-Workflow für die Associate-Benutzeroberfläche

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

In diesem Artikel wird erläutert, wie Übermittlung und Workflow funktionieren, wenn Sie einen Workflow für die Benutzeroberfläche „Verknüpfen“ aktivieren. Anschließend wird erläutert, wie ein Übermittlungs-Workflow konfiguriert wird. In der exemplarischen Vorgehensweise wird das Generieren einer PDF aus der IC-Payload (Interactive Communication) als Beispiel verwendet. Sie können die Schritte für andere Workflow-Typen anpassen.

<!--
## Submission and workflow behavior {#submission-and-workflow-behavior}

When you enable **Configure Workflow for Update** for an Associate UI, submissions from the Associate UI can trigger an AEM workflow. The following explains where workflows run, who uses which environment, and how to plan for data and access.

### Where workflows run

AEM workflows always run on the **Author** instance. It does not matter whether the person submitting is an author or an associate—the workflow runs on Author. Plan your user groups and where you store workflow data with this in mind.

### Where associates use the Associate UI

Customer-facing associates use the Associate UI on the **Publish** instance only. You publish the Interactive Communication and expose the Associate UI through your Publish environment (for example, via your application or dispatcher). Associates do not use the Author instance. For step-by-step integration and how to invoke the Associate UI on the Publish instance, see [Integrate Associate UI in Your Application](/help/forms/interactive-communication/invoke-associate-ui.md).

### When an author submits from the Author instance

Authors can open the Associate UI on the Author instance—for example, to test the Interactive Communication or to submit on behalf of a customer. When they submit, the request is handled on Author and the workflow runs there. For this to work, the author must be in both **forms-associates** (to access the Associate UI) and **workflow-users** (to run the workflow).

### When an associate submits from the Publish instance

Associates open the Associate UI on the Publish instance, using the integration you set up. When they submit, the submission is sent to the Author instance and the workflow runs on Author. Associates sign in on Publish (for example, via [Microsoft Entra ID](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id)) and do not need access to Author. To set up how associates open the Associate UI on Publish, see [Integrate Associate UI in Your Application](/help/forms/interactive-communication/invoke-associate-ui.md).
-->

## Übermittlungs-Workflow konfigurieren

Die folgenden Schritte zeigen, wie Sie einen Workflow erstellen, der ausgeführt wird, wenn Benutzer ihn über die Benutzeroberfläche „Verknüpfen“ übermitteln. Hier verwenden wir **Rendern der IC in PDF** als Beispiel mit dem vorkonfigurierten Schritt **IC-Rendering der PDF-Ausgabe** . Wenn ein(e) Benutzende(r) eine E-Mail über die Benutzeroberfläche von Associate sendet, wird die Payload an den Workflow gesendet. Dieser Schritt verwendet **communicationDom** (IC-JSON) aus der Payload, um die PDF zu erstellen.

### Payload-Struktur

Der Workflow erhält eine JSON-Payload. Das **communicationDom**-Feld enthält das für die PDF-Generierung verwendete IC-JSON. Der **IC Render PDF Output**-Schritt verwendet ihn als Vorlageneingabe.

| Feld | Beschreibung |
|-------|-------------|
| communicationDom | Generieren von IC-JSON für PDF |
| auditMetadata | Audit-Informationen |
| submitData | Übermittelte Formulardaten (JSON) |
| prefillData | Vorbefüllungsdaten (JSON) |
| Referer, Cookies, queryString, clientIP, userAgent, formSubmitter | Metadaten anfordern |

### Erstellen eines Workflow-Modells

1. **Allgemein** Erstellen Sie ein Workflow-Modell (fügen Sie beispielsweise einen Workflow als hinzu **pdfrenderworkflow**).

   ![Registerkarte „Standard“ des Workflow-Modells](/help/forms/assets/associate-ui-add-workflow.png)

1. **Variablen:** Fügen Sie Variablen hinzu, die mit der Payload und dem Schritt übereinstimmen: **communicationDom** (JSON), **auditMetadata** (JSON), **outputDocument** (Document).

   ![Workflow-Variablen](/help/forms/assets/associate-ui-add-variables.png)

1. **Schritt:** Fügen Sie den Schritt **IC Render PDF Output“**.
   ![Workflow-Schritt hinzufügen](/help/forms/assets/associate-ui-add-step.png)

1. Legen Sie auf der Registerkarte **Eingabe** den Wert **Vorlage auswählen (JsonObject)** auf **Variable** → **communicationDom**. Speichern Sie den Schritt und das Modell.

   ![IC-Render - PDF-Ausgabe - Registerkarte „Eingabe“](/help/forms/assets/associate-ui-input-variable.png)

1. Legen Sie auf der Registerkarte **Ausgabe** auf **Vorlage auswählen (JsonObject)** den Wert **Variable** → **communicationDom**. Speichern Sie den Schritt und das Modell.

   ![Workflow-Variablen und Arbeitsfläche](/help/forms/assets/assocaite-ui-output-variable.png)

### Workflow mit der Benutzeroberfläche verknüpfen

Aktivieren [ in „Benutzeroberfläche von Associate aktivieren und konfigurieren](/help/forms/interactive-communication/enable-configure-associate-ui.md) die Option „Ansicht verknüpfen“ und **Workflow** legen Sie **Workflow für Aktualisierung konfigurieren** auf „Ein“ fest und wählen Sie dieses Workflow-Modell aus. Veröffentlichen Sie die IC und [integrieren Sie die Associate-Benutzeroberfläche](/help/forms/interactive-communication/invoke-associate-ui.md) sodass Übermittlungen den Trigger für diesen Workflow bilden.

![Einstellungen für interaktive Kommunikation - Workflow-Konfiguration für die Benutzeroberfläche von Associate](/help/forms/assets/associate-ui-configure-workflow.png)

Wenn **Workflow-Datenspeicher externalisieren** aktiviert ist, konfigurieren Sie den Externalizer so, dass Workflow-Daten in Ihrem externen Speicher (z. B. Azure) gespeichert werden. Siehe [Workflow-Daten externalisieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/create-aem-workflow/externalize-workflow.html).

## Siehe auch

- [Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Aktivieren und Konfigurieren der Associate-Benutzeroberfläche für interaktive Kommunikation](/help/forms/interactive-communication/enable-configure-associate-ui.md)
- [Integrieren der Associate-Benutzeroberfläche in Ihr Programm](/help/forms/interactive-communication/invoke-associate-ui.md)
- [Workflow-Daten externalisieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/create-aem-workflow/externalize-workflow.html)
