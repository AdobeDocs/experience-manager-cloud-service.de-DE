---
title: Verbinden von AEM Adaptive Forms mit Azure Blob Storage
description: Erfahren Sie, wie Sie eine Azure Blob Storage-Konfiguration in AEM Forms erstellen und in Ihrem adaptiven Forms verwenden, um eine effiziente Datenspeicherung zu gewährleisten.
keywords: Azure Blob Storage-Integration mit AEM Forms, Daten an Azure Storage übermitteln, Azure Storage-Konfiguration in AEM Forms erstellen, Azure Blob Storage in Übermittlungsaktion für adaptive Formulare verwenden
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
exl-id: 0c9f8f85-c4e9-4c79-bd0b-abdcac99a2d4
role: User, Developer
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 95%

---

# Senden eines adaptiven Formulars an Azure Blob Storage

Die Übermittlungsaktion **[!UICONTROL An Azure Blob Storage senden]** verbindet ein adaptives Formular mit einem Microsoft Azure-Portal. Sie können die Formulardaten, Dateien, Anhänge oder Datensatzdokumente an die verbundenen Azure Storage-Container senden.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/aem-forms-submit-action.md).

## Vorteile

Einige der Vorteile der Integration von Azure Blob Storage mit AEM Forms sind:

* Sie hilft beim Optimieren des Prozesses zum Übermitteln von adaptiven Formulardaten, Dateien, Anhängen und Datensatzdokumenten an Azure Storage-Container.
* Azure Blob Storage wird für die zentralisierte und organisierte Speicherung von Übermittlungen von adaptiven Formularen verwendet.

## Verbinden von AEM Forms mit Microsoft® Azure Blob Storage

So verwenden Sie Azure Blob Storage in einer Übermittlungsaktion für adaptive Formulare:

1. [Erstellen eines Azure Blob Storage-Containers](#create-a-azure-blob-storage-container-create-azure-configuration): Dadurch wird AEM Forms mit Azure Storage-Containern verbunden.
2. [Azure Storage-Konfiguration in einem adaptiven Formular verwenden](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af): Dadurch wird Ihr adaptives Formular mit konfigurierten Azure Storage-Containern verbunden.

### Erstellen eines Azure Blob Storage-Containers {#create-azure-configuration}

Verbinden von AEM Forms mit den Azure Storage-Containern:

1. Gehen Sie zu Ihrer **AEM Forms-Autoren**-Instanz > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]**.
1. Sobald Sie **[!UICONTROL Azure Storage]** ausgewählt haben, werden Sie zum **[!UICONTROL Azure Storage-Browser]** weitergeleitet.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Der Assistent zum Erstellen der Azure Storage-Konfiguration wird angezeigt.

   ![Azure Storage-Konfiguration](/help/forms/assets/azure-storage-configuration.png)

1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Azure Storage-Konto]** und **[!UICONTROL Azure-Zugriffsschlüssel]** an.

   * Sie können den `Azure Storage Account`-Namen und den `Azure Access key` über die Speicherkonten im Microsoft Azure-Portal abrufen.
<!--

    >[!NOTE]
    >
    > The URL for **[!UICONTROL Azure Blob Endpoint]** is automatically appended to the textbox when a value is entered for **[!UICONTROL Azure Storage Account]**. You can update the Azure Blob End Point URL with your custom domain. Steps to update URL for **[!UICONTROL Azure Blob End Point]**:
    > 1. [Enable the AEM Advance Networking VPN support](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html)
    > 1. [Enable dedicated egress IP link](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html)
    > 1. [Map custom domain to azure blob storage](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-custom-domain-name?tabs=azure-portal)
-->

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Jetzt können Sie diese Azure Storage-Container-Konfiguration für die Sendeaktion in einem adaptiven Formular verwenden.

### Verwenden der Azure Storage-Konfiguration in einem adaptiven Formular {#use-azure-storage-configuartion-in-af}

Sie können die erstellte Azure Storage-Container-Konfiguration in einem adaptiven Formular verwenden, um Daten oder das generierte Datensatzdokument im Azure Storage-Container zu speichern.

>[!NOTE]
>
> * Wählen Sie denselben [!UICONTROL Konfigurations-Container] für ein adaptives Formular, in dem Sie Ihren OneDrive-Speicher erstellt haben.
> * Wenn kein [!UICONTROL Konfigurations-Container] ausgewählt ist, erscheinen die globalen [!UICONTROL Speicherkonfigurations]-Ordner im Fenster mit den Eigenschaften der Übermittlungsaktion.

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Führen Sie die folgenden Schritte aus, um die Konfiguration des Azure Storage-Containers in einem auf Foundation-Komponenten basierenden adaptiven Formular zu verwenden:

1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare.
1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** die Option **[!UICONTROL An Azure Blob-Speicher senden]**.

   ![Azure Blob-Speicher-GIF](/help/forms/assets/submit-to-azure-blob-fc.png){width=50%,height=50%}

   Sie können auch einen Nachweis im Azure Blob-Speicher speichern.

1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]** aus, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular senden, werden die Daten in der angegebenen Azure Storage-Container-Konfiguration gespeichert.
Ordnerstruktur zum Speichern von Daten: `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!TAB Kernkomponente]

Führen Sie die folgenden Schritte aus, um die Konfiguration des Azure Storage-Containers in einem auf Kernkomponenten basierenden adaptiven Formular zu verwenden:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** die Option **[!UICONTROL An Azure Blob-Speicher senden]**.

   ![Azure Blob Storage-GIF](/help/forms/assets/azure-submit-video.gif)

   Sie können auch einen Nachweis im Azure Blob-Speicher speichern.

1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]** aus, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular senden, werden die Daten in der angegebenen Azure Storage-Container-Konfiguration gespeichert.
Ordnerstruktur zum Speichern von Daten: `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!TAB Universeller Editor]

Führen Sie die folgenden Schritte aus, um die Konfiguration des Azure Storage-Containers in einem im universellen Editor erstellten adaptiven Formular zu verwenden:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Klicken Sie im Editor auf die Erweiterung **Formulareigenschaften bearbeiten**.
Das Dialogfeld **Formulareigenschaften** wird angezeigt.

   >[!NOTE]
   >
   > * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** im Extension Manager.
   > * Informationen zum Aktivieren und Deaktivieren von Erweiterungen im universellen Editor finden Sie im Artikel [Extension Manager – Highlights der Funktionen](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

1. Klicken Sie auf **Übermittlung** und wählen Sie die Übermittlungsaktion **[!UICONTROL An Azure Blob-Speicher senden]** aus.
   ![Azure Blob Storage](/help/forms/assets/azure-blob-storage-ue.png)

   Wenn Sie **Anhänge mit dem ursprünglichen Namen speichern** auswählen, werden die Anlagen im Ordner unter ihren ursprünglichen Dateinamen gespeichert. Sie können auch einen Nachweis im Azure Blob-Speicher speichern.

1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]** aus, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**, um die Übermitllungseinstellungen zu speichern.

Wenn Sie das Formular senden, werden die Daten in der angegebenen Azure Storage-Container-Konfiguration gespeichert.
Die Ordnerstruktur zum Speichern von Daten ist `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!ENDTABS]

## Verwandte Artikel

{{af-submit-action}}
