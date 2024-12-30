---
Title: How to send data to a SharePoint storage on submission of an Adaptive Form?
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list or Document library when you submit the form.
keywords: Wie verbinde ich die SharePoint-Liste mit einem adaptiven Formular? Wie verbinde ich die SharePoint-Dokumentbibliothek mit einem adaptiven Formular, An SharePoint senden, Erstellen einer SharePoint-Dokumentbibliothekskonfiguration, Verwenden der Aktion „An SharePoint senden“ in einem adaptiven Formular, Verbinden Sie ein adaptives Formular mit der Microsoft® SharePoint-Liste.
feature: Adaptive Forms, Core Components
exl-id: e925a750-5fb5-4950-afd3-78551eec985d
title: Konfigurieren einer Übermittlungsaktion für ein adaptives Formular
role: User, Developer
source-git-commit: 5e1d08e82cafc3a8a715653727f42ce0048f2b1f
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 100%

---

# Verbinden eines adaptiven Formulars mit Microsoft® SharePoint

Die Sendeaktion **[!UICONTROL An SharePoint senden]** ermöglicht es Ihnen, ein adaptives Formular mit einem Microsoft® SharePoint-Speicher zu verbinden. Die Formulardaten werden nach dem Senden des Formulars an den gewünschten SharePoint-Speicher gesendet.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md).

## Vorteile

Die Übermittlung von Daten aus einem adaptiven Formular an den SharePoint-Speicher bietet unter anderem folgende Vorteile:

* Sie erleichtert die direkte Übermittlung von Formulardaten an SharePoint, wobei sie einen zentralen Speicherort für die Speicherung und Verwaltung von Informationen bietet.
* Durch die Anwendung der Zugriffssteuerungs- und Berechtigungsfunktionen von SharePoint wird sichergestellt, dass nur autorisierte Personen die übermittelten Daten anzeigen oder ändern können.

Die Aktion **[!UICONTROL An SharePoint senden]** ermöglicht Folgendes:

* [Verbinden eines adaptiven Formulars mit der SharePoint-Dokumentbibliothek](#connect-af-sharepoint-doc-library)
* [Verbinden eines adaptiven Formulars mit einer SharePoint-Liste](#connect-af-sharepoint-list)

## Verbinden eines adaptiven Formulars mit der SharePoint-Dokumentbibliothek {#connect-af-sharepoint-doc-library}

So verwenden Sie die Sendeaktion **[!UICONTROL An SharePoint-Dokumentbibliothek senden]** in einem adaptiven Formular:

1. [Konfiguration für die SharePoint-Dokumentbibliothek erstellen](#create-a-sharepoint-configuration-create-sharepoint-configuration): Dadurch wird AEM Forms mit Ihrem Microsoft® SharePoint-Speicher verbunden.
2. [Sendeaktion „An SharePoint senden“ in einem adaptiven Formular verwenden](#use-sharepoint-configuartion-in-af): Dadurch wird Ihr adaptives Formular mit dem konfigurierten Microsoft® SharePoint verbunden.

### Erstellen einer SharePoint-Dokumentbibliothekskonfiguration {#create-sharepoint-configuration}

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

1. Klicken Sie auf **[!UICONTROL Verbinden]**. Bei erfolgreicher Verbindung erscheint die Meldung `Connection Successful`.

1. Wählen Sie jetzt **SharePoint-Site** > **Dokumentbibliothek** > **SharePoint-Ordner**, um die Daten zu speichern.

   >[!NOTE]
   >
   >* Standardmäßig ist `forms-ootb-storage-adaptive-forms-submission` auf der ausgewählten SharePoint-Site vorhanden.
   >* Erstellen Sie einen Ordner als `forms-ootb-storage-adaptive-forms-submission`, wenn er nicht bereits in der `Documents`-Bibliothek der ausgewählten SharePoint-Site vorhanden ist, indem Sie auf **Ordner erstellen** klicken.

Jetzt können Sie die SharePoint-Sites-Konfiguration für die Sendeaktion in einem adaptiven Formular verwenden.

### Verwenden der SharePoint-Dokumentbibliothekskonfiguration in einem adaptiven Formular {#use-sharepoint-configuartion-in-af}

Sie können die erstellte Konfiguration für die SharePoint-Dokumentbibliothek in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument in einem SharePoint-Ordner zu speichern. Führen Sie die folgenden Schritte aus, um eine Speicherkonfiguration der SharePoint-Dokumentbibliothek in einem adaptiven Formular zu verwenden:

1. Erstellen Sie ein [adaptives Formular](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Wählen Sie denselben [!UICONTROL Konfigurations-Container] für ein adaptives Formular, in dem Sie den SharePoint-Dokumentbibliothekspeicher erstellt haben.
   > * Wenn kein [!UICONTROL Konfigurations-Container] ausgewählt ist, erscheinen die globalen [!UICONTROL Speicherkonfigurations]-Ordner im Fenster mit den Eigenschaften der Sendeaktion.

1. Wählen Sie **Sendeaktion** als **[!UICONTROL An SharePoint senden]**.
   ![Sharepoint-GIF](/help/forms/assets/sharedrive-video.gif)
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular senden, werden die Daten im angegebenen Microsoft® Sharepoint-Dokumentbibliothekspeicher gespeichert.
Ordnerstruktur zum Speichern von Daten: `/folder_name/form_name/year/month/date/submission_id/data`.

## Verbinden eines adaptiven Formulars mit einer Microsoft® SharePoint-Liste {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

So verwenden Sie die Sendeaktion [!UICONTROL An SharePoint senden] in einem adaptiven Formular:

1. [Erstellen einer SharePoint-Listenkonfiguration](#create-sharepoint-list-configuration): Dadurch wird AEM Forms mit Ihrem Microsoft® Sharepoint-Listenspeicher verbunden.
1. [Verwenden von „Senden mit Formulardatenmodell (FDM)“ in einem adaptiven Formular](#use-submit-using-fdm): Dadurch wird Ihr adaptives Formular mit dem konfigurierten Microsoft® SharePoint verbunden.

### Erstellen einer Microsoft SharePoint-Listenkonfiguration {#create-sharepoint-list-configuration}

So verbinden Sie AEM Forms mit Ihrer Microsoft® SharePoint-Liste:

1. Wechseln Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicken Sie in der Dropdown-Liste auf **[!UICONTROL Erstellen]** > **[!UICONTROL SharePoint-Liste]**. Der SharePoint-Konfigurationsassistent wird angezeigt.
1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Client-Geheimnis]** und **[!UICONTROL OAuth-URL]** an. Informationen zum Abrufen der Client-ID, des Client-Geheimnisses und der Mandanten-ID für die OAuth-URL finden Sie in der [Dokumentation von Microsoft®](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).
   * Sie können die `Client ID` und das `Client Secret` Ihrer App über das Microsoft® Azure-Portal abrufen.
   * Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` durch die URL Ihrer Autoreninstanz.
   * Fügen Sie die API-Berechtigungen `offline_access` und `Sites.Manage.All` auf der Registerkarte **Microsoft® Graph** hinzu, um Lese- und Schreibberechtigungen bereitzustellen. Fügen Sie die Berechtigung `AllSites.Manage` auf der Registerkarte **Sharepoint**  hinzu, um remote mit SharePoint-Daten zu interagieren.
   * Verwenden der OAuth-URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Ersetzen Sie `<tenant-id>` durch die `tenant-id` Ihrer App aus dem Microsoft® Azure-Portal.

     >[!NOTE]
     >
     > Ob das Feld **Client-Geheimnis** obligatorisch oder optional ist, hängt von der Konfiguration Ihrer Azure Active Directory-Anwendung ab. Wenn Ihre Anwendung so konfiguriert ist, dass sie ein Client-Geheimnis verwendet, ist die Angabe des Client-Geheimnisses obligatorisch.

1. Klicken Sie auf **[!UICONTROL Verbinden]**. Bei erfolgreicher Verbindung erscheint die Meldung `Connection Successful`.
1. Wählen Sie **[!UICONTROL SharePoint-Site]** und **[!UICONTROL SharePoint-Liste]** aus der Dropdown-Liste.
1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Konfiguration für die Microsoft® SharePoint-Liste zu erstellen.


### Verwenden von „Senden mit Formulardatenmodell (FDM)“ in einem adaptiven Formular {#use-submit-using-fdm}

Sie können die erstellte SharePoint-Listenkonfiguration in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument in einer SharePoint-Liste zu speichern. Führen Sie die folgenden Schritte aus, um eine SharePoint-Liste in einem adaptiven Formular zu verwenden:

1. [Erstellen eines Formulardatenmodells (FDM) mithilfe von Microsoft](/help/forms/create-form-data-models.md)
1. [Konfigurieren des Formulardatenmodells (FDM) zum Abrufen und Senden von Daten](/help/forms/work-with-form-data-model.md#configure-services)
1. [Erstellen eines adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)
1. [Konfigurieren einer Sendeaktion mit einem Formulardatenmodell (FDM)](/help/forms/using-form-data-model.md)

Wenn Sie das Formular absenden, werden die Daten im angegebenen Microsoft® Sharepoint-Listenspeicher gespeichert.

>[!NOTE]
>
> Die folgenden Spaltentypen werden in der Microsoft® SharePoint-Liste nicht unterstützt:
> * Bildspalte
> * Metadatenspalte
> * Personenspalte
> * Externe Datenspalte

## Ähnliche Artikel

{{af-submit-action}}
