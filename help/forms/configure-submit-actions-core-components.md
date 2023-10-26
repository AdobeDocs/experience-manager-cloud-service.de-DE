---
title: Konfigurieren einer Übermittlungsaktion für ein adaptives Formular?
description: Ein adaptives Formular bietet verschiedene Übermittlungsaktionen. Eine Übermittlungsaktion bestimmt die Verarbeitung eines adaptiven Formulars nach dem Senden. Sie können integrierte Übermittlungsaktionen verwenden oder eigene erstellen
keywords: Anleitung zum Auswählen einer Sendeaktion für ein adaptives Formular, Verbinden eines adaptiven Formulars mit einer Sharepoint-Liste, Verbinden eines adaptiven Formulars mit einer SharePoint-Dokumentbibliothek, Verbinden eines adaptiven Formulars mit einem Formulardatenmodell
exl-id: 495948e8-30a7-4e7c-952f-c71de15520f0
source-git-commit: f79ed400ac2c1956dd7946cec2881f4e77d4bd41
workflow-type: tm+mt
source-wordcount: '3658'
ht-degree: 81%

---

# Übermittlungsaktion für adaptive Formulare {#configuring-the-submit-action}

<span class="preview"> Adobe empfiehlt die Verwendung von Kernkomponenten für [Adaptive Forms zu einer AEM Sites-Seite hinzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) oder [eigenständige adaptive Forms erstellen](/help/forms/creating-adaptive-form-core-components.md). </span>


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service | Dieser Artikel |
| Gilt für | ✅ Kernkomponenten des adaptiven Formulars, ❎ [Adaptive Form Foundation-Komponenten](/help/forms/configuring-submit-actions.md) |


Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Wird ausgelöst, wenn ein Benutzer auf die **[!UICONTROL Einsenden]** auf einem adaptiven Formular. Forms as a Cloud Service bietet für &quot;Adaptive Forms&quot;, das auf Kernkomponenten basiert, eine Reihe vordefinierter Sendeaktionen. Diese vordefinierten Übermittlungsaktionen ermöglichen Ihnen Folgendes:

* Senden Sie Formulardaten einfach per E-Mail.
* Starten Sie Microsoft Power Automate Workflows oder AEM Workflows beim Senden der Daten.
* Übermitteln Sie die Formulardaten direkt an Microsoft SharePoint Server, Microsoft Azure Blob Storage oder Microsoft OneDrive.
* Senden Sie die Daten nahtlos mit dem Formulardatenmodell an eine konfigurierte Datenquelle.
* Senden Sie die Daten bequem an einen REST-Endpunkt.

Sie können auch [Standardmäßige Übermittlungsaktionen erweitern](custom-submit-action-form.md) , um eine eigene Übermittlungsaktion zu erstellen.

## Auswählen und Konfigurieren einer Sendeaktion für ein adaptives Formular {#select-and-configure-submit-action}

So wählen Sie eine Übermittlungsaktion für Ihr Formular aus und konfigurieren sie:

1. Öffnen Sie den Inhaltsbrowser und wählen Sie die **[!UICONTROL Guide Container]** -Komponente Ihres adaptiven Formulars.
1. Klicken Sie auf die Guide Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare wird geöffnet.

1. Klicken Sie auf  **[!UICONTROL Einsendung]** Registerkarte.

   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptive Formulare zu öffnen und eine Sendeaktion zu konfigurieren.](/help/forms/assets/adaptive-forms-submit-message.png)

1. Auswählen und Konfigurieren eines **[!UICONTROL Übermittlungsaktion]**, basierend auf Ihren Anforderungen. Detaillierte Informationen zur ausgewählten Übermittlungsaktion finden Sie unter:

   * [E-Mail senden](#send-email)
   * [An SharePoint senden](#submit-to-sharedrive)
   * [Senden mit Formulardatenmodell](#submit-using-form-data-model)
   * [Senden an Azure Blob-Speicher](#azure-blob-storage)
   * [An REST-Endpunkt übermitteln](#submit-to-rest-endpoint)
   * [An OneDrive senden](#submit-to-onedrive)
   * [AEM-Workflow aufrufen](#invoke-an-aem-workflow)
   * [An Power Automate übermitteln](#microsoft-power-automate)

## E-Mail senden {#send-email}

Wenn Sie nach erfolgreicher Übermittlung des Formulars eine E-Mail an einen oder mehrere Empfänger senden möchten, können Sie die Variable **[!UICONTROL E-Mail senden]** Übermittlungsaktion Mit dieser Aktion können Sie eine E-Mail erstellen, die Formulardaten in einem vordefinierten Format enthält. Betrachten Sie beispielsweise die folgende Vorlage, bei der Kundenname, Versandadresse, Statusname und Postleitzahl aus den gesendeten Formulardaten abgerufen werden:

    „
    
    Hallo ${customer_name},
    
    Ihre Standard-Versandadresse lautet:
    ${customer_name},
    ${customer_Shipping_Address},
    ${customer_state},
    ${customer_ZIPCode}
    
    Mit freundlichen Grüßen
    WKND
    
    “

>[!NOTE]
>
> * Es ist wichtig, dass alle Formularfelder eindeutige Elementnamen haben, auch wenn sie in verschiedenen Bereichen in einem adaptiven Formular platziert werden.
> * Bei der Verwendung AEM as a Cloud Service E-Mail ist eine Verschlüsselung der ausgehenden E-Mail erforderlich. Standardmäßig ist die Funktion für ausgehende E-Mails deaktiviert. Senden Sie zum Aktivieren ein Support-Ticket an [Zugriff anfordern](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email).

Darüber hinaus **[!UICONTROL E-Mail senden]** Die Übermittlungsaktion bietet die Möglichkeit, Anlagen und ein Datensatzdokument (DoR) in die E-Mail einzuschließen.

So aktivieren Sie die [!UICONTROL Datensatzdokument anhängen] , siehe die Dokumentation unter [Konfigurieren des adaptiven Formulars zum Generieren eines Datensatzdokuments (DoR)](generate-document-of-record-core-components.md). Sie können diese Option in den Eigenschaften des adaptiven Formulars aktivieren.

<!-- [!NOTE]
>
>Send PDF via Email Submit Action is applicable only to Adaptive Forms that use XFA template as form model. 

>[!NOTE]
>
>Ensure that the [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>exists. The directory is required to temporarily store attachments. If the directory does not exist, create it. -->

<!--

>[!CAUTION]
>
>If you  [prefill](prepopulate-adaptive-form-fields.md) a form template,  a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema , form template, or form data model) that is data does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost. 

>[!CAUTION]
>
>If you [prefill](prepopulate-adaptive-form-fields.md) a form template, a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema, or form data model) that does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost.


-->

## An SharePoint senden {#submit-to-sharedrive}

Die Sendeaktion **[!UICONTROL An SharePoint senden]** verbindet ein adaptives Formular mit einem Microsoft® SharePoint-Speicher. Sie können die Formulardatendatei, die Anlagen oder das Datensatzdokument an den verbundenen Microsoft® Sharepoint-Speicher senden.

<!--
Using Submit to SharePoint, you can:
* [Connect an Adaptive Form to SharePoint Document Library](#connect-af-sharepoint-doc-library)
* [Connect an Adaptive Form to SharePoint List](#connect-af-sharepoint-list)
-->

### Verbinden eines adaptiven Formulars mit der SharePoint Document Library {#connect-af-sharepoint-doc-library}

So verwenden Sie die **[!UICONTROL An SharePoint Document Library übermitteln]** Sendeaktion in einem adaptiven Formular:

1. [Erstellen einer SharePoint Document Library-Konfiguration](#create-a-sharepoint-configuration-create-sharepoint-configuration): Dadurch wird AEM Forms mit Ihrem Microsoft® SharePoint-Speicher verbunden.
2. [Verwenden der Sendeaktion „An SharePoint senden“ in einem adaptiven Formular](#use-sharepoint-configuartion-in-af): Dadurch wird Ihr adaptives Formular mit dem konfigurierten Microsoft® SharePoint verbunden.

#### Erstellen einer SharePoint Document Library-Konfiguration {#create-sharepoint-configuration}

So verbinden Sie AEM Forms mit Ihrem Microsoft® Sharepoint Document Library-Speicher:

1. Gehen Sie zu Ihrer **AEM Forms-Autoreninstanz** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Sobald Sie **[!UICONTROL Microsoft® SharePoint]** auswählen, werden Sie zum **[!UICONTROL SharePoint-Browser]** weitergeleitet.
1. Wählen Sie einen **Konfigurations-Container**. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicks **[!UICONTROL Erstellen]** > **[!UICONTROL SharePoint Document Library]** aus der Dropdown-Liste. Der SharePoint-Konfigurationsassistent wird angezeigt.

![SharePoint-Konfiguration](/help/forms/assets/sharepoint_configuration.png)
1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Client-ID]**, **[!UICONTROL Client-Geheimnis]** und **[!UICONTROL OAuth-URL]** an. Informationen zum Abrufen der Client-ID, des Client-Geheimnisses und der Mandanten-ID für die OAuth-URL finden Sie in der [Dokumentation von Microsoft®](https://learn.microsoft.com/de-de/graph/auth-register-app-v2).
   * Sie können die `Client ID` und das `Client Secret` Ihrer App über das Microsoft® Azure-Portal abrufen.
   * Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` mit der URL Ihrer Autoreninstanz.
   * Fügen Sie die API-Berechtigungen `offline_access` und `Sites.Manage.All` hinzu, um Lese- und Schreibberechtigungen bereitzustellen.
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

#### Verwenden der SharePoint Document Library-Konfiguration in einem adaptiven Formular {#use-sharepoint-configuartion-in-af}

Sie können die erstellte SharePoint Document Library-Konfiguration in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument in einem SharePoint-Ordner zu speichern. Führen Sie die folgenden Schritte aus, um eine SharePoint Document Library-Speicherkonfiguration in einem adaptiven Formular zu verwenden:

1. Erstellen eines [adaptives Formular](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Gleiches auswählen [!UICONTROL Konfigurations-Container] für ein adaptives Formular, in dem Sie den SharePoint Document Library-Speicher erstellt haben.
   > * Wenn kein [!UICONTROL Konfigurations-Container] ausgewählt ist, erscheinen die globalen [!UICONTROL Speicherkonfigurations]-Ordner im Fenster mit den Eigenschaften der Sendeaktion.

1. Wählen Sie **Sendeaktion** als **[!UICONTROL An SharePoint senden]**.
   ![Sharepoint-GIF](/help/forms/assets/sharedrive-video.gif)
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular übermitteln, werden die Daten im angegebenen Microsoft® Sharepoint Document Library-Speicher gespeichert.
Ordnerstruktur zum Speichern von Daten: `/folder_name/form_name/year/month/date/submission_id/data`.

<!--

### Connect an Adaptive Form to Microsoft® SharePoint List {#connect-af-sharepoint-list}

<span class="preview"> This is a pre-release feature and accessible through our [pre-release channel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

To use the [!UICONTROL Submit to SharePoint List] Submit Action in an Adaptive Form:

1. [Create a SharePoint List Configuration](#create-sharepoint-list-configuration): It connects AEM Forms to your Microsoft® Sharepoint List Storage.
1. [Use the Submit using Form Data Model in an Adaptive Form](#use-submit-using-fdm): It connects your Adaptive Form to configured Microsoft® SharePoint.

#### Create a SharePoint List Configuration {#create-sharepoint-list-configuration}

To connect AEM Forms to your Microsoft&reg; Sharepoint List:

1. Go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® SharePoint]**.   
1. Select a **Configuration Container**. The configuration is stored in the selected Configuration Container. 
1. Click **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** from the drop-down list. The SharePoint configuration wizard appears.  
1. Specify the **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** and **[!UICONTROL OAuth URL]**. For information on how to retrieve Client ID, Client Secret, Tenant ID for OAuth URL, see [Microsoft&reg; Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
    * You can retrieve the `Client ID` and `Client Secret` of your app from the Microsoft&reg; Azure portal.
    * In the Microsoft&reg; Azure portal, add the Redirect URI as `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Replace `[author-instance]` with the URL of your Author instance.
    * Add the API permissions `offline_access` and `Sites.Manage.All` in the **Microsoft® Graph** tab to provide read/write permissions. Add `AllSites.Manage` permission in the **Sharepoint** tab to interact remotely with SharePoint data.
    * Use OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Replace `<tenant-id>` with the `tenant-id` of your app from the Microsoft&reg; Azure portal.

      >[!NOTE]
      >
      > The **client secret** field is mandatory or optional depends upon your Azure Active Directory application configuration. If your application is configured to use a client secret, it is mandatory to provide the client secret.

1. Click **[!UICONTROL Connect]**. On a successful connection, the `Connection Successful` message appears.
1. Select **[!UICONTROL SharePoint Site]** and **[!UICONTROL SharePoint List]** from the drop-down list.
1. Tap **[!UICONTROL Create]** to create the cloud configuration for the Microsoft® SharePointList.


#### Use the Submit using Form Data Model in an Adaptive Form {#use-submit-using-fdm}

You can use the created SharePoint List configuration in an Adaptive Form, to save data or generated Document of Record in a SharePoint List folder. Perform the following steps to use a SharePoint List storage configuration in an Adaptive Form as:

1. [Create a Form Data Model using Microsoft® SharePoint List configuration](/help/forms/create-form-data-models.md)
1. [Configure the Form Data Model to retrieve and send data](/help/forms/work-with-form-data-model.md#configure-services)
1. [Create an Adaptive Form](/help/forms/creating-adaptive-form-core-components.md)
1. [Configure Submit action using a Form Data Model](/help/forms/configuring-submit-actions.md#submit-using-form-data-model)

When you submit the form, the data is saved in the specified Microsoft&reg; Sharepoint List Storage. 

>[!NOTE]
>
> In Microsoft® SharePoint List, the following column types are not supported:
> * image column
> * metadata column
> * person column
> * external data column

-->

## Senden mit Formulardatenmodell {#submit-using-form-data-model}

Die Übermittlungsaktion **[!UICONTROL Senden mit Formulardatenmodell]** schreibt gesendete Daten eines adaptiven Formulars für das angegebene Datenmodellobjekt in die Datenquelle eines Formulardatenmodells. Beim Konfigurieren der Übermittlungsaktion können Sie ein Datenmodellobjekt auswählen, dessen übermittelte Daten in die Datenquelle zurückgeschrieben werden sollen.

Sie können ein adaptives Formular mithilfe der Übermittlungsaktion &quot;Formulardatenmodell&quot;mit einer Microsoft SharePoint-Liste verbinden.

Darüber hinaus können Sie einen Formularanhang mit einem Formulardatenmodell und einem Datensatzdokument (Document of Record) an die Datenquelle senden. Weitere Informationen zum Formulardatenmodell finden Sie unter [[!DNL AEM Forms] Datenintegration](data-integration.md).

## An REST-Endpunkt übermitteln {#submit-to-rest-endpoint}

Verwenden Sie die Aktion **[!UICONTROL An REST-Endpunkt übermitteln]**, um die übertragenen Daten an eine Rest-URL zu veröffentlichen. Die URL kann sich auf einem internen (dem Server, auf dem das Formular gerendert wird) oder auf einem externen Server befinden.

Um Daten auf einem internen Server zu senden, geben Sie den Pfad der Ressource an. Die Daten werden an den Pfad der Ressource gesendet. Beispiel: /content/restEndPoint. Für solche Sende-Anfragen werden die Authentifizierungsinformationen der Versandanfrage verwendet.

Geben Sie eine URL an, um Daten an einen externen Server zu senden. Das Format der URL ist `https://host:port/path_to_rest_end_point`. Stellen Sie sicher, dass Sie den Pfad zum Handhaben der POST-Anforderung anonym konfigurieren.

![Zuordnung zur Weitergabe von Feldwerten als Anforderungsparameter für die Dankeseite](assets/post-enabled-actionconfig.png)

Im obigen Beispiel hat der Benutzer Informationen in die `textbox` eingegeben, die mithilfe von Parameter `param1` erfasst werden. Die Syntax zur Veröffentlichung erfasster Daten mithilfe von `param1` lautet:

`String data=request.getParameter("param1");`

Auch Parameter, die Sie für die Veröffentlichung von XML-Daten und Anlagen verwenden, sind `dataXml` und `attachments`.

Beispielsweise können Sie diese beiden Parameter in Ihrem Skript verwenden, um Daten an einem REST-Endpunkt zu analysieren. Verwenden Sie die folgende Syntax, um Daten zu speichern und zu analysieren:

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

In diesem Beispiel speichert `data` die XML-Daten, und `att` speichert Anlagendaten.

Die Übermittlungsoption **[!UICONTROL An REST-Endpunkt übermitteln]** wird verwendet, wenn Sie die im Formular eingetragenen Daten zu einer konfigurierten Bestätigungsseite im Rahmen der HTTP GET-Anforderung weiterleiten möchten. Sie können den Namen der Felder hinzufügen, die angefordert werden sollen. Das Format der Anfrage lautet:

`{fieldName}={request parameter name}`

Wie in der folgenden Abbildung dargestellt, werden `param1` und `param2` als Parameter mit Werten, die aus den Feldern **textbox** und **numericbox** kopiert wurden, für die nächste Aktion weitergeleitet.

![Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](assets/action-config.png)

Sie können auch **[!UICONTROL POST-Anforderungen aktivieren]** und eine URL eingeben, um die Anforderung zu veröffentlichen. Um Daten an den AEM-Server, auf dem sich das Formular befindet, zu senden, verwenden Sie einen relativen Pfad entsprechend dem Stammpfad des AEM-Servers. Beispiel: `/content/forms/af/SampleForm.html`. Wenn Sie Daten an irgendeinen anderen Server senden, verwenden Sie den absoluten Pfad.

>[!NOTE]
>
>Alle Felder müssen über verschiedene Elementnamen verfügen, um als Parameter in der REST-URL weitergeleitet zu werden, auch dann, wenn die Felder in verschiedenen Bereichen platziert sind.

<!-- ## Send PDF via Email {#send-pdf-via-email}

The **Send PDF via Email** Submit Action sends an email with a PDF containing form data, to one or more recipients on successful submission of the form.

>[!NOTE]
>
>This Submit Action is available for XFA-based Adaptive Forms and XSD-based adaption forms that have the Document of Record template. -->

<!-- ## Invoke a forms workflow {#invoke-a-forms-workflow}

The **Submit to Forms workflow** submit option sends a data xml and file attachments (if any) to an existing Adobe LiveCycle or [!DNL AEM Forms] on JEE process.

For information about how to configure the Submit to forms workflow Submit Action, see [Submitting and processing your form data using forms workflows](submit-form-data-livecycle-process.md). -->



<!--
## Forms Portal Submit Action {#forms-portal-submit-action}

The **Forms Portal Submit Action** option makes form data available through an [!DNL AEM Forms] portal.

For more information about the Forms Portal and Submit Action, see [Drafts and submissions component](draft-submission-component.md). -->

## AEM-Workflow aufrufen {#invoke-an-aem-workflow}

Die Übermittlungsaktion **[!UICONTROL AEM-Workflow aufrufen]** verknüpft ein adaptives Formular mit einem [AEM-Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de#extending-aem). Wenn ein Formular gesendet wird, startet der verknüpfte Workflow automatisch auf der Autoreninstanz. Sie können die Datendatei, die Anhänge und das Datensatzdokument am Payload-Speicherort des Workflows oder in einer Variablen speichern. Wenn der Workflow für die externe Datenspeicherung markiert und für eine externe Datenspeicherung konfiguriert ist, ist nur die Variablenoption verfügbar. Sie können aus der Liste der für das Workflow-Modell verfügbaren Variablen auswählen. Wenn der Workflow für die externe Datenspeicherung zu einem späteren Zeitpunkt und nicht zum Zeitpunkt der Workflow-Erstellung markiert ist, stellen Sie sicher, dass die erforderlichen Variablenkonfigurationen vorhanden sind.

Die Übermittlungsaktion platziert Folgendes im Payload-Speicherort des Workflows oder der Variablen, wenn der Workflow für die externe Datenspeicherung markiert ist:

* **Datendatei**: Sie enthält Daten, die an das adaptive Formular gesendet werden. Mit der Option **[!UICONTROL Datendateipfad]** können Sie den Dateinamen und den Dateipfad relativ zur Payload angeben. Beispielsweise erstellt der Pfad `/addresschange/data.xml` einen Ordner mit dem Namen `addresschange` und platziert ihn relativ zur Payload. Sie können auch nur `data.xml` angeben, um nur die übermittelten Daten zu senden, ohne die Erstellung einer Ordnerhierarchie. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

* **Anlagen**: Mit der Option **[!UICONTROL Anlagenpfad]** können Sie den Ordnernamen zum Speichern der in das adaptive Formular hochgeladenen Anlagen angeben. Der Ordner wird immer relativ zur Payload erstellt. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

* **Datensatzdokument**: Es enthält das Datensatzdokument, das für das adaptive Formular generiert wurde. Mit der Option **[!UICONTROL Pfad des Datensatzdokuments]** können Sie den Dateinamen des Datensatzdokuments sowie den Dateipfad relativ zur Payload angeben. Beispiel: Der Pfad `/addresschange/DoR.pdf` erstellt einen Ordner mit dem Namen `addresschange` relativ zur Payload und platziert `DoR.pdf` relativ zur Payload. Um nur das Datensatzdokument zu speichern, ohne eine Ordnerhierarchie zu erstellen, reicht die Angabe `DoR.pdf`. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

Bevor Sie die Übermittlungsaktion **[!UICONTROL AEM-Workflow aufrufen]** verwenden, richten Sie die Konfiguration des **[!UICONTROL AEM DS-Konfigurations-Service]** wie folgt ein:

* **[!UICONTROL Verarbeitungs-Server-URL]**: Der Verarbeitungs-Server ist der Server, auf dem der Forms- oder AEM-Workflow ausgelöst wird. Diese URL kann mit der URL der AEM-Autoreninstanz oder eines anderen Servers identisch sein.

* **[!UICONTROL Verarbeitungs-Server-Benutzername]**: Benutzername des Workflow-Benutzenden

* **[!UICONTROL Verarbeitungs-Serverkennwort]**: Das Kennwort des Workflow-Benutzenden



## An OneDrive senden {#submit-to-onedrive}

Die Übermittlungsaktion **[!UICONTROL An OneDrive senden]** verbindet ein adaptives Formular mit Microsoft® OneDrive. Sie können die Formulardaten, Dateien, Anhänge oder Datensatzdokumente an den verbundenen Microsoft® OneDrive-Speicher senden.

>[!VIDEO](https://video.tv.adobe.com/v/3424864/connect-aem-adaptive-form-to-onedrive/?quality=12&learn=on)

Verwenden der Übermittlungsaktion [!UICONTROL An OneDrive senden] in einem adaptiven Formular:

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
   * Fügen Sie im Microsoft® Azure-Portal den Umleitungs-URI als `https://[author-instance]/libs/cq/onedrive/content/configurations/wizard.html` hinzu. Ersetzen Sie `[author-instance]` mit der URL Ihrer Autoreninstanz.
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

Sie können die erstellte OneDrive-Speicherkonfiguration in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument in einem OneDrive-Ordner zu speichern. Führen Sie die folgenden Schritte aus, um die OneDrive-Speicherkonfiguration in einem adaptiven Formular zu verwenden:
1. Erstellen Sie ein [adaptives Formular](/help/forms/creating-adaptive-form.md).

   >[!NOTE]
   >
   > * Wählen Sie denselben [!UICONTROL Konfigurations-Container] für ein adaptives Formular, in dem Sie Ihren OneDrive-Speicher erstellt haben.
   > * Wenn kein [!UICONTROL Konfigurations-Container] ausgewählt ist, erscheinen die globalen [!UICONTROL Speicherkonfigurations]-Ordner im Fenster mit den Eigenschaften der Übermittlungsaktion.

1. Wählen Sie **Aktion übermitteln** als **[!UICONTROL An OneDrive senden]**.
   ![OneDrive-GIF](/help/forms/assets/onedrive-video.gif)
1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular übermitteln, werden die Daten im angegebenen Microsoft® OneDrive-Speicher gespeichert.
Ordnerstruktur zum Speichern von Daten: `/folder_name/form_name/year/month/date/submission_id/data`.

## Senden an Azure Blob-Speicher {#submit-to-azure-blob-storage}

Die Übermittlungsaktion **[!UICONTROL An Azure Blob Storage senden]** verbindet ein adaptives Formular mit einem Microsoft Azure-Portal. Sie können die Formulardaten, Dateien, Anhänge oder Datensatzdokumente an die verbundenen Azure Storage-Container senden. Verwenden der Übermittlungsaktion für Azure Blob-Speicher:

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

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Jetzt können Sie diese Azure Storage-Container-Konfiguration für die Sendeaktion in einem adaptiven Formular verwenden.

### Verwenden der Azure Storage-Konfiguration in einem adaptiven Formular {#use-azure-storage-configuartion-in-af}

Sie können die erstellte Azure Storage-Container-Konfiguration in einem adaptiven Formular verwenden, um Daten zu speichern oder das generierte Datensatzdokument im Azure Storage-Container zu speichern. Führen Sie die folgenden Schritte aus, um die Konfiguration des Azure Storage-Containers in einem adaptiven Formular zu verwenden:
1. Erstellen Sie ein [adaptives Formular](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Wählen Sie denselben [!UICONTROL Konfigurations-Container] für ein adaptives Formular, in dem Sie Ihren OneDrive-Speicher erstellt haben.
   > * Wenn kein [!UICONTROL Konfigurations-Container] ausgewählt ist, erscheinen die globalen [!UICONTROL Speicherkonfigurations]-Ordner im Fenster mit den Eigenschaften der Übermittlungsaktion.

1. Wählen Sie **Aktion übermitteln** als **[!UICONTROL Senden an Azure Blob Storage]**.
   ![Azure Blob Storage-GIF](/help/forms/assets/azure-submit-video.gif)

1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

Wenn Sie das Formular senden, werden die Daten in der angegebenen Azure Storage-Container-Konfiguration gespeichert.
Ordnerstruktur zum Speichern von Daten: `/configuration_container/form_name/year/month/date/submission_id/data`.

Um Konfigurationswerte festzulegen, [generieren Sie OSGi-Konfigurationen mit dem AEM-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und [stellen Sie die Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) in Ihrer Cloud Service-Instanz bereit.




## An Power Automate übermitteln {#microsoft-power-automate}

Sie können ein adaptives Formular so konfigurieren, dass bei der Übermittlung ein Cloud-Fluss bei Microsoft® Power Automate ausgeführt wird. Das konfigurierte adaptive Formular sendet erfasste Daten, Anhänge und das Datensatzdokument zur Verarbeitung an den Cloud-Fluss von Power Automate. Dies hilft Ihnen beim Erstellen benutzerdefinierter Datenerfassungsprozesse und nutzt gleichzeitig die Leistungsfähigkeit von Microsoft® Power Automate, um Geschäftslogiken zu erfassten Daten zu erstellen und Kunden-Workflows zu automatisieren. Im Folgenden finden Sie einige Beispiele dafür, was Sie nach der Integration eines adaptiven Formulars in Microsoft® Power Automate tun können:

* Verwenden Sie Daten von adaptiven Formularen in einem Power Automate-Geschäftsprozess
* Verwenden Sie Power Automate, um erfasste Daten an mehr als 500 Datenquellen oder eine beliebige öffentlich verfügbare API zu senden
* Führen Sie komplexe Berechnungen für erfasste Daten durch
* Speichern Sie die Daten von adaptiven Formularen in Speichersystemen nach einem vordefinierten Zeitplan

Der adaptive Forms-Editor stellt die **Microsoft® Power Automate Flow aufrufen** Übermittlungsaktion zum Senden von Daten, Anlagen und Datensatzdokumenten für adaptive Formulare an Power Automate Cloud Flow. Um mithilfe der Übermittlungsaktion erfasste Daten an Microsoft® Power Automate zu senden, [verbinden Sie Ihre Instanz von Forms as a Cloud Service mit Microsoft® Power Automate](forms-microsoft-power-automate-integration.md).

Verwenden Sie nach erfolgreicher Konfiguration die [Microsoft® Power Automate Flow aufrufen](forms-microsoft-power-automate-integration.md#use-the-invoke-a-microsoft&reg;-power-automate-flow-submit-action-to-send-data-to-a-power-automate-flow-use-the-invoke-microsoft-power-automate-flow-submit-action) Übermittlungsaktion zum Senden von Daten an einen Power Automate Flow.

## Verwenden synchroner oder asynchroner Übermittlung {#use-synchronous-or-asynchronous-submission}

Eine Übermittlungsaktion kann die synchrone oder asynchrone Übermittlungsmethode verwenden.

**Synchrone Übermittlung**: Web-Formulare werden im Allgemeinen für die synchrone Übermittlung konfiguriert. Bei der synchronen Übermittlung werden Benutzer, die ein Formular senden, zu einer Bestätigungsseite, zu einer Dankeseite oder bei fehlgeschlagener Übermittlung zu einer Fehlerseite umgeleitet. Sie können die Option **[!UICONTROL Verwendung von asynchroner Übermittlung]** wählen, um die Benutzer zu einer Web-Seite umzuleiten oder eine Nachricht beim Senden anzuzeigen.

![Konfigurieren der Übermittlungsaktion](assets/thank-you-setting.png)

**Asynchrone Übermittlung**: Moderne Web-Erlebnisse wie Einzelseitenanwendungen sind zunehmend beliebt. Dabei bleibt die Web-Seite unverändert, während die Client-Server-Interaktion im Hintergrund abläuft. Für adaptive Formulare können Sie diese Erfahrung nun bieten, indem Sie die [asynchrone Übermittlung konfigurieren](asynchronous-submissions-adaptive-forms.md).

## Server-seitige Überprüfung im adaptiven Formular {#server-side-revalidation-in-adaptive-form}

Normalerweise platzieren Entwickler in jedem Online-Datenerfassungssystem einige Javascript-Validierungen auf Client-Seite, um Geschäftsregeln durchzusetzen. Moderne Browser bieten Endbenutzern jedoch Möglichkeiten, diese Validierungen zu umgehen und Übermittlungen mithilfe verschiedener Techniken wie beispielsweise die Web Browser DevTools-Konsole manuell durchzuführen. Diese Techniken sind auch für adaptive Formulare gültig. Entwicklerinnen und Entwickler von Formularen können verschiedene Validierungslogiken erstellen, aber aus technischer Sicht können Endbenutzerinnen und -benutzer diese Validierungslogiken umgehen und ungültige Daten an den Server senden. Ungültige Daten verstoßen gegen die Geschäftsregeln, die eine Formularautorin bzw. ein -autor durchgesetzt hat.

Die Funktion für eine erneute Server-seitige Überprüfung enthält die Möglichkeit, auch Validierungen durchzuführen, die von einem Autor für adaptive Formulare beim Entwerfen eines adaptiven Formulars auf dem Server bereitgestellt wurden. Sie verhindert jede mögliche Beeinträchtigung von Datenübertragungen und Verstöße gegen Geschäftsregeln, die hinsichtlich Formularvalidierungen auftreten können.

### Was soll auf dem Server validiert werden? {#what-to-validate-on-server-br}

Alle standardmäßig einsetzbaren Feldvalidierungen eines adaptiven Formulars, die erneut auf dem Server ausgeführt werden:

* Erforderlich
* Validierungbild-Klausel
* Validierungsausdruck

### Aktivieren von Server-seitiger Validierung {#enabling-server-side-validation-br}

Verwenden Sie das Kontrollkästchen **[!UICONTROL Auf dem Server erneut überprüfen]** im Container für adaptive Formulare in der Seitenleiste, um die Server-seitige Validierung für das aktuelle Formular zu aktivieren oder zu deaktivieren.

![Aktivieren von Server-seitiger Validierung](assets/revalidate-on-server.png)

Aktivieren von Server-seitiger Validierung

Wenn Endbenutzerinnen oder -benutzer diese Validierungen umgehen und die Formulare senden, führt der Server die Validierung erneut durch. Wenn die Validierung Server-seitig fehlschlägt, wird die Übermittlung abgebrochen. Dem Endbenutzer wird das ursprüngliche Formular erneut präsentiert. Die erfassten Daten und die gesendeten Daten werden dem Benutzer als Fehler angezeigt.

>[!NOTE]
>
>Die Server-seitige Validierung prüft das Formularmodell. Es wird empfohlen, eine separate Client-Bibliothek für Validierungen zu erstellen und sie nicht mit anderen Elementen wie HTML-Stil und DOM-Manipulation in derselben Client-Bibliothek zu mischen.

### Unterstützende benutzerdefinierte Funktionen in Validierungsausdrücken {#supporting-custom-functions-in-validation-expressions-br}

Bisweilen befindet sich bei komplexen **Validierungsregeln** das exakte Validierungsskript in den benutzerdefinierten Funktionen. Der Autor kann diese benutzerdefinierten Funktionen über den Ausdruck für die Feldvalidierung abrufen. Um diese benutzerdefinierte Funktionsbibliothek bei Server-seitigen Validierungen bekannt und verfügbar zu machen, kann der Formularautor den Namen der AEM-Client-Bibliothek auf der Registerkarte **[!UICONTROL Allgemein]** des Dialogfelds „Container für adaptive Formulare bearbeiten“, wie nachfolgend dargestellt konfigurieren.

![Unterstützende benutzerdefinierte Funktionen in Validierungsausdrücken](assets/clientlib-cat.png)

Unterstützende benutzerdefinierte Funktionen in Validierungsausdrücken

Der Autor kann eine benutzerdefinierte JavaScript-Bibliothek für jedes adaptive Formular konfigurieren. Legen Sie in der Bibliothek nur die wiederverwendbaren Funktionen ab, die von den Drittanbieter-Bibliotheken „jquery“ und „underscore“ abhängen.

## Fehlerbehandlung bei Übermittlungsaktionen {#error-handling-on-submit-action}

Konfigurieren Sie im Rahmen der AEM-Richtlinie für Sicherheit und Absicherung benutzerdefinierte Fehlerseiten wie 400.jsp, 404.jsp und 500.jsp. Diese Handler werden aufgerufen, wenn beim Senden eines Formulars die Fehler-Codes 400, 404 oder 500 auftreten. Die Handler werden auch aufgerufen, wenn diese Fehler-Codes auf einem Veröffentlichungsknoten ausgelöst werden. Sie können JSP-Seiten auch für andere HTTP-Fehler-Codes erstellen.

Wenn Sie ein Formulardatenmodell oder ein Schema-basiertes adaptives Formular mit XML- oder JSON-Daten ausfüllen, die konform zu einem Schema sind, bei dem Daten keine `<afData>`-, `<afBoundData>`- und `</afUnboundData>`-Tags enthalten, gehen die Daten der ungebundenen Felder des adaptiven Formulars verloren. Das Schema kann ein XML-Schema, ein JSON-Schema oder ein Formulardatenmodell sein. Ungebundene Felder sind Felder des adaptiven Formulars ohne die Eigenschaft `bindref`.

<!-- For more information, see [Customizing Pages shown by the Error Handler](/help/sites-developing/customizing-errorhandler-pages.md). -->


## Siehe nächste Punkte

* [Erstellen von Stilen oder Designs für Ihre Formulare](using-themes-in-core-components.md)
* [Erstellen eines adaptiven Formulars (Kernkomponenten)](/help/forms/creating-adaptive-form-core-components.md)
* [Erstellen einer benutzerdefinierten Sende-Aktion für adaptive Formulare](/help/forms/custom-submit-action-form.md)


## Siehe auch {#see-also}

{{see-also}}

