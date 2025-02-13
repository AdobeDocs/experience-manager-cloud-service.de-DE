---
title: Konfigurieren von Unified Storage Connector (USC) für AEM Forms?
description: Erfahren Sie, wie Sie Unified Storage Connector (USC) für AEM Forms verwalten. Verwenden Sie Unified Storage Connector (USC), um AEM Forms mit externen Datenspeichern zu verbinden.
role: Admin, Developer, User
feature: Adaptive Forms, Workflow
exl-id: c93d0242-0c15-4d69-82a1-d6fcc7da4bae
source-git-commit: c17e4e70fa8cec176c908983230b03f2899bc1ca
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 99%

---

# Verwalten von Unified Storage Connector (USC) für AEM Forms {#manage-unified-storage-connector}

Sie können Unified Storage Connector (USC) verwenden, um AEM Forms mit externen Datenspeichern zu verbinden.

Beispielsweise können Sie Werte für Felder in einem adaptiven Formular ausfüllen und an einen AEM-Workflow senden. Sie können AEM-Workflows außerdem so konfigurieren, dass Daten in einem externen Datenspeicher wie dem Microsoft Azure-Speicher-Server gespeichert werden. Verwenden Sie Unified Storage Connector (USC), um eine Verbindung zwischen AEM-Workflows und dem externen Datenspeicher herzustellen.

## Verbinden von AEM-Workflows mit einem Microsoft Azure-Speicher-Server {#connect-workflows-with-azure}

Erstellen Sie eine Azure-Speicherkonfiguration und verweisen Sie mit Unified Storage Connector (USC) auf diese Konfiguration. Anschließend können Sie AEM-Workflow-Modelle konfigurieren, um den Datenspeicher zu externalisieren und ihn mit einem Azure-Speicher-Server zu verbinden.

### Erstellen einer [!DNL Azure]-Speicherkonfiguration {#create-azure-storage-configuration}

Stellen Sie vor dem Ausführen dieser Schritte sicher, dass Sie über ein [!DNL Azure]-Speicherkonto und einen Zugriffsschlüssel verfügen, um den Zugriff auf das [!DNL Azure]-Speicherkonto zu autorisieren.

Führen Sie die folgenden Schritte aus, um eine [!DNL Azure]-Speicherkonfiguration zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure-Speicher]**.
1. Wählen Sie einen Ordner aus, um die Konfiguration zu erstellen, und wählen Sie anschließend die Option **[!UICONTROL Erstellen]** aus.
1. Geben Sie im Feld **[!UICONTROL Titel]** einen Titel für die Konfiguration an.
1. Geben Sie den Namen des [!DNL Azure]-Speicherkontos im Feld **[!UICONTROL Azure-Speicherkonto]** an.
1. Geben Sie den Schlüssel für den Zugriff auf das Azure-Speicherkonto im Feld **[!UICONTROL Azure-Zugriffsschlüssel]** an und wählen Sie **[!UICONTROL Speichern]** aus.

### Konfigurieren von Unified Storage Connector (USC) für AEM-Workflows {#configure-unified-storage-connector-workflows}

Führen Sie die folgenden Schritte aus, um Unified Storage Connector (USC) für AEM-Workflows zu konfigurieren:

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.

1. Wählen Sie im Abschnitt **[!UICONTROL Workflow]** den Eintrag **[!UICONTROL Azure]** aus der Dropdown-Liste „Speicher“ aus.
1. Geben Sie im Feld **[!UICONTROL Pfad für Speicherkonfiguration]** den [Konfigurationspfad für die Azure-Speicherkonfiguration](#create-azure-storage-configuration) an.
1. Wählen Sie **[!UICONTROL Veröffentlichen]** und anschließend **[!UICONTROL Speichern]** aus, um die Konfiguration zu speichern.

### Konfigurieren eines AEM-Workflow-Modells für die externe Datenspeicherung {#configure-workflow-external-data-storage}

Führen Sie die folgenden Schritte aus, um ein AEM-Workflow-Modell für einen externen Datenspeicher zu konfigurieren:

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie einen Modellnamen aus und tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Tippen Sie auf das Symbol für die Seiteninformationen und dann auf **[!UICONTROL Eigenschaften öffnen]**.
1. Wählen Sie **[!UICONTROL Workflow für Datenspeicherung externalisieren]** aus.
1. Klicken Sie zum Speichern der Eigenschaften auf **[!UICONTROL Speichern und schließen]**.

>[!NOTE]
>
>Die Optionen zum Speichern des Schritts „Aufgabe zuweisen“ als Entwurf und zum Abrufen des Verlaufs des Schritts „Aufgabe zuweisen“ sind nicht verfügbar, wenn Sie ein AEM-Workflow-Modell für die externe Datenspeicherung konfigurieren.

### Richtlinien für AEM-Workflows zur externen Datenspeicherung {#guidelines-workflows-external-data-storage}

Im Folgenden finden Sie die Richtlinien für die Verwendung von AEM-Workflows und die Speicherung von Daten in externen Datenspeichern wie Microsoft Azure-Speicher-Server:

* Verwenden Sie Variablen zum Speichern von Daten beim Definieren von Eingabe- und Ausgabedatendateien und Anlagen in Workflow-Modellschritten. Wählen Sie nicht die Optionen **[!UICONTROL Relativ zur Payload]** und **[!UICONTROL Verfügbar unter einem absoluten Pfad]** aus. Die Optionen **[!UICONTROL Relativ zur Payload]** und **[!UICONTROL Verfügbar unter einem absoluten Pfad]** werden beim [Konfigurieren eines AEM-Workflow-Modells für die externe Datenspeicherung](#configure-workflow-external-data-storage) nicht automatisch angezeigt.

* Verwenden Sie beim Senden eines adaptiven Formulars an einen AEM-Workflow Variablen zum Speichern von Datendateien und Anlagen. Wählen Sie beim Senden eines adaptiven Formulars an einen AEM-Workflow nicht die Option **[!UICONTROL Relativ zur Payload]**. Die Option **[!UICONTROL Relativ zur Payload]** wird beim [Konfigurieren eines AEM-Workflow-Modells für die externe Datenspeicherung](#configure-workflow-external-data-storage) nicht automatisch angezeigt.

* Verwenden Sie in einem Workflow-Modell keinen benutzerdefinierten AEM-Workflow-Schritt, um Daten im CRX DE-Repository zu speichern.

* Wenn Sie [ein AEM Workflow-Modell für die externe Datenspeicherung konfigurieren](#configure-workflow-external-data-storage), erstellen Sie keine benutzerdefinierten Spalten für den AEM-Posteingang, da die Werte der benutzerdefinierten Spalten nicht abgerufen werden, wenn das Arbeitselement im AEM Posteingang zu einem Workflow gehört, der für die externe Datenspeicherung markiert ist.

>[!MORELIKETHIS]
>
>* [Konfigurieren von Datenquellen für AEM Forms](/help/forms/configure-data-sources.md)
>* [Konfigurieren von Azure Storage für AEM-Formulare](/help/forms/configure-azure-storage.md)
>* [Integrieren von Microsoft Dynamics 365](/help/forms/configure-msdynamics.md)
>  [Hinzufügen des Formularportals zu einer AEM Sites-Seite](/help/forms/configure-forms-portal.md)
