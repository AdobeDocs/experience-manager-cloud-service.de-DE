---
Title: How to connect AEM Adaptive Forms with Azure Blob Storage?
Description: Learn how to create an Azure Blob Storage Configuration in AEM Forms and use it within your Adaptive Forms for efficient data storage.
keywords: Azure Blob Storage-Integration mit AEM Forms, Daten an Azure Storage übermitteln, Azure Storage-Konfiguration in AEM Forms erstellen, Azure Blob Storage in Übermittlungsaktion für adaptive Formulare verwenden
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
exl-id: 0c9f8f85-c4e9-4c79-bd0b-abdcac99a2d4
title: Wie konfiguriere ich eine Übermittlungsaktion für ein adaptives Formular?
role: User, Developer
source-git-commit: c0df3c6eaf4e3530cca04157e1a5810ebf5b4055
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 68%

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
    > 1. [Enable the AEM Advance Networking VPN support](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=de)
    > 1. [Enable dedicated egress IP link](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=de)
    > 1. [Map custom domain to azure blob storage](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-custom-domain-name?tabs=azure-portal)
-->

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Jetzt können Sie diese Azure Storage-Container-Konfiguration für die Sendeaktion in einem adaptiven Formular verwenden.

### Verwenden der Azure Storage-Konfiguration in einem adaptiven Formular {#use-azure-storage-configuartion-in-af}

Sie können die erstellte Azure Storage-Container-Konfiguration in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument im Azure Storage-Container zu speichern.

>[!NOTE]
>
> * Wählen Sie denselben [!UICONTROL Konfigurations-Container] für ein adaptives Formular, in dem Sie Ihren OneDrive-Speicher erstellt haben.
> * Wenn kein [!UICONTROL Konfigurations-Container] ausgewählt ist, erscheinen die globalen [!UICONTROL Speicherkonfigurations]-Ordner im Fenster mit den Eigenschaften der Übermittlungsaktion.

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Führen Sie die folgenden Schritte aus, um die Azure Storage-Container-Konfiguration in einem adaptiven Formular basierend auf Foundation-Komponenten zu verwenden:

1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare.
1. Wählen Sie aus **[!UICONTROL Dropdown]** Liste „Übermittlungsaktion“ die Option **[!UICONTROL An Azure Blob Storage übermitteln]**.

   ![Azure Blob Storage-GIF](/help/forms/assets/submit-to-azure-blob-fc.png){width=50%,height=50%}

   Sie können auch das Datensatzdokument (DoR) im Azure Blob-Speicher speichern.

1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular senden, werden die Daten in der angegebenen Azure Storage-Container-Konfiguration gespeichert.
Ordnerstruktur zum Speichern von Daten: `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!TAB Kernkomponente]

Führen Sie die folgenden Schritte aus, um die Azure Storage-Container-Konfiguration in einem adaptiven Formular basierend auf Kernkomponenten zu verwenden:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie aus **[!UICONTROL Dropdown]** Liste „Übermittlungsaktion“ die Option **[!UICONTROL An Azure Blob Storage übermitteln]**.

   ![Azure Blob Storage-GIF](/help/forms/assets/azure-submit-video.gif)

   Sie können auch das Datensatzdokument (DoR) im Azure Blob-Speicher speichern.

1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular senden, werden die Daten in der angegebenen Azure Storage-Container-Konfiguration gespeichert.
Ordnerstruktur zum Speichern von Daten: `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!TAB Universeller Editor]

Führen Sie die folgenden Schritte aus, um die Azure Storage-Container-Konfiguration in einem im universellen Editor erstellten adaptiven Formular zu verwenden:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Klicken Sie im Editor **die Erweiterung**&#x200B;Formulareigenschaften bearbeiten“.
Das **Formulareigenschaften** wird angezeigt.

   >[!NOTE]
   >
   > * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
   > * Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights&rbrace;.

1. Klicken Sie auf **Übermittlung** und wählen Sie **[!UICONTROL An Azure Blob Storage senden]** Übermittlungsaktion aus.
   ![Azure Blob Storage](/help/forms/assets/azure-blob-storage-ue.png)

   Wenn Sie **Anlagen mit Originalnamen speichern** wählen, werden die Anlagen unter Verwendung ihrer Originaldateinamen im Ordner gespeichert. Sie können auch das Datensatzdokument (DoR) im Azure Blob-Speicher speichern.

1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie **[!UICONTROL Speichern&amp;Schließen]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular senden, werden die Daten in der angegebenen Azure Storage-Container-Konfiguration gespeichert.
Die Ordnerstruktur zum Speichern von Daten ist `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!ENDTABS]

## Ähnliche Artikel

{{af-submit-action}}
