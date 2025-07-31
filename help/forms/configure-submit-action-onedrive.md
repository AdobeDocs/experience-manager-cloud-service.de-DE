---
Title: How to submit data from an Adaptive Form to Microsoft&reg; OneDrive?
Description: Explore the streamlined process of connecting AEM Forms with Microsoft&reg; OneDrive using the Submit to OneDrive Submit Action. Learn the step-by-step guide to configure OneDrive and set up submission actions for efficient data storage and retrieval
keywords: AEM Forms OneDrive-Integration, Verbindung zu Microsoft OneDrive, OneDrive-Konfigurationseinstellungen mit AEM-Formularen
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
exl-id: dbfa4094-1b92-4a7c-a799-f66973d27054
title: Wie konfiguriere ich eine Übermittlungsaktion für ein adaptives Formular?
role: User, Developer
source-git-commit: c0df3c6eaf4e3530cca04157e1a5810ebf5b4055
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 73%

---

# Senden eines adaptiven Formulars an Microsoft® OneDrive

Die Übermittlungsaktion **[!UICONTROL An OneDrive senden]** verbindet ein adaptives Formular mit Microsoft® OneDrive. Sie können die Formulardaten, Dateien, Anhänge oder Datensatzdokumente an den verbundenen Microsoft® OneDrive-Speicher senden.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/aem-forms-submit-action.md).

## Vorteile

Einige Vorteile der nahtlosen Integration von AEM Forms und Microsoft® OneDrive sind:

* Die geräteübergreifende Barrierefreiheit von OneDrive. Sie stellt sicher, dass gespeicherte Formulardaten auf verschiedenen Plattformen sofort verfügbar sind. Benutzende können auf die übermittelten Daten, Anhänge und Dokumente von Desktops, Laptops, Tablets und Mobilgeräten zugreifen, was die Barrierefreiheit und Flexibilität verbessert.
* Die Integration von OneDrive mit AEM-Formularen bietet eine zuverlässige und skalierbare Lösung für die effiziente Datenspeicherung. Alle Übermittlungen adaptiver Formulare, wie Dateien, Anhänge und Datensatzdokumente, können bequem in OneDrive gespeichert werden, was strukturierte und zugängliche Daten zu gewährleistet.

## Verbinden von OneDrive mit einem adaptiven Formular

>[!VIDEO](https://video.tv.adobe.com/v/3424864/connect-aem-adaptive-form-to-onedrive/?quality=12&learn=on)

Um OneDrive für die Übermittlung von AEM-Formularen zu konfigurieren, führen Sie die folgenden Schritte aus:

1. [Erstellen einer OneDrive-Konfiguration](#create-a-onedrive-configuration-create-onedrive-configuration): Dadurch wird AEM Forms mit Ihrem Microsoft® OneDrive-Speicher verbunden.
2. [Verwenden der Übermittlungsaktion „An OneDrive senden“ in einem adaptiven Formular](#use-onedrive-configuration-in-an-adaptive-form-use-onedrive-configuartion-in-af): Dadurch wird Ihr adaptives Formular mit dem konfigurierten Microsoft® OneDrive verbunden.

### Erstellen einer OneDrive-Konfiguration {#create-onedrice-configuration}

Verbinden von AEM Forms mit dem Microsoft® OneDrive-Speicher:

1. Gehen Sie zu Ihrer **AEM Forms-Autoreninstanz** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® OneDrive]**.
1. Wenn Sie **[!UICONTROL Microsoft® OneDrive]** auswählen, werden Sie zum **[!UICONTROL OneDrive-Browser]** weitergeleitet.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Der OneDrive-Konfigurationsassistent wird angezeigt.

   ![OneDrive-Konfigurationsbildschirm](/help/forms/assets/onedrive-configuration.png)

1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Client-Geheimnis]** und **[!UICONTROL OAuth-URL]** an. Informationen zum Abrufen der Client-ID, des Client-Geheimnisses und der Mandanten-ID für die OAuth-URL finden Sie in der [Dokumentation von Microsoft®](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).
   * Sie können die `Client ID` und das `Client Secret` Ihrer App über das Microsoft® Azure-Portal abrufen.
   * Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/onedrive/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` durch die URL Ihrer Autoreninstanz.
   * Fügen Sie die API-Berechtigungen `offline_access` und `Files.ReadWrite.All` hinzu, um Lese- und Schreibberechtigungen bereitzustellen.
   * Verwenden der OAuth-URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

   >[!NOTE]
   >
   > Ob das Feld **Client-Geheimnis** obligatorisch oder optional ist, hängt von der Konfiguration Ihrer Azure Active Directory-Anwendung ab. Wenn Ihre Anwendung so konfiguriert ist, dass sie ein Client-Geheimnis verwendet, ist die Angabe des Client-Geheimnisses obligatorisch.

1. Klicken Sie auf **[!UICONTROL Verbinden]**. Bei erfolgreicher Verbindung erscheint die Meldung `Connection Successful`.

1. Wählen Sie jetzt **[!UICONTROL OneDrive-Container]** > **[OneDrive-Ordner]**, um die Daten zu speichern.

   >[!NOTE]
   >
   >* Standardmäßig ist `forms-ootb-storage-adaptive-forms-submission` im OneDrive-Container vorhanden.
   > * Erstellen Sie einen Ordner als `forms-ootb-storage-adaptive-forms-submission`, falls noch nicht vorhanden, indem Sie auf **Ordner erstellen** klicken.

Jetzt können Sie diese OneDrive-Speicherkonfiguration für die Sendeaktion in einem adaptiven Formular verwenden.

### Verwenden der OneDrive-Konfiguration in einem adaptiven Formular {#use-onedrive-configuartion-in-af}

Sie können die erstellte OneDrive-Speicherkonfiguration in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument in einem OneDrive-Ordner zu speichern.

>[!NOTE]
>
> * Wählen Sie denselben [!UICONTROL Konfigurations-Container] für ein adaptives Formular, in dem Sie Ihren OneDrive-Speicher erstellt haben.
> * Wenn kein [!UICONTROL Konfigurations-Container] ausgewählt ist, erscheinen die globalen [!UICONTROL Speicherkonfigurations]-Ordner im Fenster mit den Eigenschaften der Übermittlungsaktion.

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Führen Sie die folgenden Schritte aus, um die OneDrive-Speicherkonfiguration in einem auf Foundation-Komponenten basierenden adaptiven Formular zu verwenden:

1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare.
1. Wählen Sie aus der **[!UICONTROL -Liste]** Aktion übermitteln **[!UICONTROL die Option „An OneDrive senden]**.
   ![OneDrive GIF](/help/forms/assets/wubmit-to-onedrive-fc.png){width=50%,height=50%}
Sie können auch das Datensatzdokument (DoR) in OneDrive speichern.
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular übermitteln, werden die Daten im angegebenen Microsoft® OneDrive-Speicher gespeichert.
Die Ordnerstruktur zum Speichern von Daten ist `/folder_name/form_name/year/month/date/submission_id/data`.

>[!TAB Kernkomponente]

Führen Sie die folgenden Schritte aus, um die OneDrive-Speicherkonfiguration in einem adaptiven Formular basierend auf der Kernkomponente zu verwenden:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie aus der **[!UICONTROL -Liste]** Aktion übermitteln **[!UICONTROL die Option „An OneDrive senden]**.
   ![OneDrive GIF](/help/forms/assets/onedrive-video.gif)
Sie können auch das Datensatzdokument (DoR) in OneDrive speichern.
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

>[!TAB Universeller Editor]

Führen Sie die folgenden Schritte aus, um die OneDrive-Speicherkonfiguration in einem im universellen Editor erstellten adaptiven Formular zu verwenden:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Klicken Sie im Editor **die Erweiterung**Formulareigenschaften bearbeiten“.
Das **Formulareigenschaften** wird angezeigt.

   >[!NOTE]
   >
   > * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
   > * Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights}.
1. Klicken Sie auf **Übermittlung** und wählen Sie **[!UICONTROL An OneDrive senden]** aus.
   ![OneDrive GIF](/help/forms/assets/submit-to-onedrive-ue.png)
Wenn Sie **Anlagen mit Originalnamen speichern** wählen, werden die Anlagen unter Verwendung ihrer Originaldateinamen im Ordner gespeichert. Sie können auch das Datensatzdokument (DoR) im Azure Blob-Speicher speichern.
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**

>[!ENDTABS]

## Verwandte Artikel

{{af-submit-action}}
