---
Title: How to integrate Adaptive Form to a SharePoint Document Library?
Description: This article explains how to send data from your Adaptive Form to a SharePoint  Document library when you submit the form.
keywords: Verbinden der SharePoint-Dokumentbibliothek für ein adaptives Formular, Senden an SharePoint, Erstellen einer SharePoint-Dokumentbibliothek, Verwenden der Übermittlungsaktion „An SharePoint senden“ in einem adaptiven Formular, AEM Forms-Datenmodell SharePoint-Dokumentbibliothek, Forms-Datenmodell SharePoint-Dokumentbibliothek, Integrieren des Forms-Datenmodells in die SharePoint-Dokumentbibliothek
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
role: User, Developer
exl-id: a00b4a93-2324-4c2a-824f-49146dc057b0
source-git-commit: c0df3c6eaf4e3530cca04157e1a5810ebf5b4055
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 63%

---

# Verbinden eines adaptiven Formulars mit der Microsoft® SharePoint-Dokumentbibliothek {#connect-af-sharepoint-doc-library}

>[!VIDEO](https://video.tv.adobe.com/v/3444368/formautomation-productivitytools-adaptiveforms--sharepointintegration-documentlibrary/?quality=12&learn=on)

So verwenden Sie die Sendeaktion **[!UICONTROL An SharePoint-Dokumentbibliothek senden]** in einem adaptiven Formular:

1. [Konfiguration für die SharePoint-Dokumentbibliothek erstellen](#1-create-a-sharepoint-document-library-configuration): Dadurch wird AEM Forms mit Ihrem Microsoft® SharePoint-Speicher verbunden.
2. [Sendeaktion „An SharePoint senden“ in einem adaptiven Formular verwenden](#2-use-sharepoint-document-library-configuration-in-an-adaptive-form): Dadurch wird Ihr adaptives Formular mit dem konfigurierten Microsoft® SharePoint verbunden.

## &#x200B;1. Erstellen Sie eine SharePoint-Dokumentbibliothekskonfiguration

So verbinden Sie AEM Forms mit Ihrem Microsoft® Sharepoint-Dokumentbibliothekspeicher:

1. Gehen Sie zu Ihrer **AEM Forms-Autoreninstanz** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Sobald Sie **[!UICONTROL Microsoft® SharePoint]** auswählen, werden Sie zum **[!UICONTROL SharePoint-Browser]** weitergeleitet.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL SharePoint-Dokumentenbibliothek]** in der Dropdown-Liste. Der SharePoint-Konfigurationsassistent wird angezeigt.

   ![SharePoint-Konfiguration](/help/forms/assets/sharepoint_configuration.png)

1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Client-Geheimnis]** und **[!UICONTROL OAuth-URL]** an. Informationen zum Abrufen der Client-ID, des Client-Geheimnisses und der Mandanten-ID für die OAuth-URL finden Sie in der [Dokumentation von Microsoft®](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).
   * Sie können die `Client ID` und das `Client Secret` Ihrer App über das Microsoft® Azure-Portal abrufen.
   * Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` durch die URL Ihrer Autoreninstanz.
   * Fügen Sie die API-Berechtigungen `offline_access` und `Sites.Manage.All` hinzu, um Lese-/Schreibberechtigungen zu gewähren. `Sites.Manage.All` ist ein Berechtigungsbereich in der Microsoft Graph-API, der einer Anwendung die Fähigkeit gewährt, alle Aspekte von SharePoint-Sites zu verwalten, z. B. das Löschen oder Ändern von Sites.

     >[!NOTE]
     >
     > Sie können die [SharePoint-Sites mit eingeschränktem Zugriff auch ](/help/forms/configure-sharepoint-site-limited-access.md) konfigurieren, indem Sie den Berechtigungsbereich `Sites.Selected` in der Microsoft Graph-API verwenden. `Sites.Selected` ist ein Berechtigungsbereich in der Microsoft Graph-API, der einen stärker granularen und eingeschränkten Zugriff auf SharePoint-Sites ermöglicht.

   * Verwenden der OAuth-URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

     >[!NOTE]
     >
     > Ob das Feld **Client-Geheimnis** obligatorisch oder optional ist, hängt von der Konfiguration Ihrer Azure Active Directory-Anwendung ab. Wenn Ihre Anwendung so konfiguriert ist, dass sie ein Client-Geheimnis verwendet, ist die Angabe des Client-Geheimnisses obligatorisch.

1. Der `offline_access Sites.Selected` Berechtigungsbereich in der Graph-API von Microsoft, der einen detaillierteren und eingeschränkteren Zugriff auf SharePoint-Sites ermöglicht. Der `offline_access Sites.Manage.All` Berechtigungsbereich in der Graph API von Microsoft, der den vollständigen Zugriff auf SharePoint-Sites ermöglicht.
1. Klicken Sie auf **[!UICONTROL Verbinden]**. Bei erfolgreicher Verbindung erscheint die Meldung `Connection Successful`.

1. Wählen Sie jetzt **SharePoint-Site** > **Dokumentbibliothek** > **SharePoint-Ordner**, um die Daten zu speichern.

   >[!NOTE]
   >
   >* Standardmäßig ist `forms-ootb-storage-adaptive-forms-submission` auf der ausgewählten SharePoint-Site vorhanden.
   >* Erstellen Sie einen Ordner als `forms-ootb-storage-adaptive-forms-submission`, wenn er nicht bereits in der `Documents`-Bibliothek der ausgewählten SharePoint-Site vorhanden ist, indem Sie auf **Ordner erstellen** klicken.

Jetzt können Sie die SharePoint-Sites-Konfiguration für die Sendeaktion in einem adaptiven Formular verwenden.

### &#x200B;2. Verwenden der SharePoint-Dokumentbibliothekskonfiguration in einem adaptiven Formular

Sie können die erstellte SharePoint-Dokumentbibliothekskonfiguration in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument in einem SharePoint-Ordner zu speichern.

>[!NOTE]
>
> * Wählen Sie denselben [!UICONTROL Konfigurations-Container] für ein adaptives Formular, in dem Sie den SharePoint-Dokumentbibliothekspeicher erstellt haben.
> * Wenn kein [!UICONTROL Konfigurations-Container] ausgewählt ist, erscheinen die globalen [!UICONTROL Speicherkonfigurations]-Ordner im Fenster mit den Eigenschaften der Sendeaktion.

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Führen Sie die folgenden Schritte aus, um eine SharePoint Document Library-Speicherkonfiguration in einem adaptiven Formular zu verwenden, das auf Foundation-Komponenten basiert:

1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste „Übermittlungsaktion“ die Option **Übermittlungsaktion** als **[!UICONTROL An SharePoint übermitteln]**.
   ![Sharepoint-GIF](/help/forms/assets/submit-to-sharepoint-fc.png){width=50%}
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

>[!NOTE]
>
> * Wenn Sie das Formular senden, werden die Daten im angegebenen Microsoft® Sharepoint-Dokumentbibliotheksspeicher gespeichert. Die Ordnerstruktur zum Speichern von Daten ist `/folder_name/form_name/year/month/date/submission_id/data`.
> * Anlagen werden auch im Verzeichnis `/folder_name/form_name/year/month/date/submission_id/data` gespeichert. Wenn Sie jedoch **Anhänge mit dem ursprünglichen Namen speichern** auswählen, werden die Anlagen im Ordner unter Verwendung ihrer ursprünglichen Dateinamen gespeichert.

>[!TAB Kernkomponente]

Führen Sie die folgenden Schritte aus, um eine SharePoint Document Library-Speicherkonfiguration in einem adaptiven Formular basierend auf der Kernkomponente zu verwenden:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie in **[!UICONTROL Dropdown]** Liste „Übermittlungsaktion“ die Option **Übermittlungsaktion** als **[!UICONTROL An SharePoint übermitteln]**.
   ![Sharepoint-GIF](/help/forms/assets/sharedrive-video.gif)
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

>[!NOTE]
>
> * Wenn Sie das Formular senden, werden die Daten im angegebenen Microsoft® Sharepoint-Dokumentbibliotheksspeicher gespeichert. Die Ordnerstruktur zum Speichern von Daten ist `/folder_name/form_name/year/month/date/submission_id/data`.
> * Anlagen werden auch im Verzeichnis `/folder_name/form_name/year/month/date/submission_id/data` gespeichert. Wenn Sie jedoch **Anhänge mit dem ursprünglichen Namen speichern** auswählen, werden die Anlagen im Ordner unter Verwendung ihrer ursprünglichen Dateinamen gespeichert.

>[!TAB Universeller Editor]

Führen Sie die folgenden Schritte aus, um eine SharePoint Document Library-Speicherkonfiguration in einem adaptiven Formular zu verwenden, das im universellen Editor verfasst wurde:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Klicken Sie im Editor **die Erweiterung**Formulareigenschaften bearbeiten“.
Das **Formulareigenschaften** wird angezeigt.

   >[!NOTE]
   >
   > * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
   > * Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights}.

1. Klicken Sie auf **Übermittlung** und wählen Sie **[!UICONTROL An SharePoint übermitteln]** Übermittlungsaktion aus.
   ![Sharepoint-GIF](/help/forms/assets/submit-to-sharepoint-ue.png)
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie **[!UICONTROL Speichern&amp;Schließen]**, um die Sendeeinstellungen zu speichern.

>[!NOTE]
>
> * Wenn Sie das Formular senden, werden die Daten im angegebenen Microsoft® Sharepoint-Dokumentbibliotheksspeicher gespeichert. Die Ordnerstruktur zum Speichern von Daten ist `/folder_name/form_name/year/month/date/submission_id/data`.
> * Anlagen werden auch im Verzeichnis `/folder_name/form_name/year/month/date/submission_id/data` gespeichert. Wenn Sie jedoch **Anhänge mit dem ursprünglichen Namen speichern** auswählen, werden die Anlagen im Ordner unter Verwendung ihrer ursprünglichen Dateinamen gespeichert.

>[!ENDTABS]

## Verwandte Artikel

{{af-submit-action}}
