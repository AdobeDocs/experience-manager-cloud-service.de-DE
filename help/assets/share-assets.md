---
title: Freigeben von Assets, Ordnern und Sammlungen als Link
description: In diesem Artikel wird beschrieben, wie Sie Assets, Ordner und Sammlungen in Experience Manager Assets als Hyperlink freigeben.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Freigeben und Verteilen von in Experience Manager verwalteten Assets {#share-assets-from-aem}

Mit Adobe Experience Manager (AEM)-Assets können Sie Assets, Ordner und Sammlungen für Mitglieder Ihres Unternehmens und externe Entitäten, einschließlich Partner und Anbieter, freigeben. Verwenden Sie die folgenden Methoden, um Assets aus Experience Manager Assets als Cloud-Dienst freizugeben:

* Als Link freigeben.
* Laden Sie Assets herunter und geben Sie sie separat frei.
* Freigeben über die AEM-Desktop-App.
* Über Adobe Asset Link freigeben.
* (Anstehende Funktion) Freigeben mit dem Markenportal.

## Freigeben von Assets als Link {#sharelink}

Sie generieren die URL für Assets, die Sie für Benutzer freigeben möchten, im Dialogfeld „Linkfreigabe“. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei AEM Assets anmelden müssen.

>[!NOTE]
>
>* Sie benötigen die Berechtigung &quot;ACL bearbeiten&quot;für den Ordner oder das Asset, das Sie als Link freigeben möchten.
>* Bevor Sie einen Link für andere Benutzer freigeben, stellen Sie sicher, dass Day CQ Mail Service konfiguriert ist. Andernfalls tritt ein Fehler auf.


1. Wählen Sie in der Assets-Benutzeroberfläche das Asset aus, das als Link freigegeben werden soll.
1. Klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Link freigeben]**. An asset link is auto-created in the **[!UICONTROL Share Link]** field. Sie können diesen Link kopieren und für andere Benutzer freigeben. Die Standard-Ablaufzeit für den Link beträgt einen Tag.

   >[!NOTE]
   >
   >Wenn ein freigegebenes Asset an einen anderen Speicherort verschoben wird, funktioniert der Link zum Asset nicht mehr. Erstellen Sie den Link erneut und geben Sie ihn für die Benutzer frei.

<!--
## Share assets as a link {#sharelink}

To generate the URL for assets you want to share with users, use the Link Sharing dialog. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Sharing assets through a link is a convenient way of making resources available to external parties without them having to first log in to AEM Assets.

>[!NOTE]
>
>* You need Edit ACL permission on the folder or the asset that you want to share as a link.
>* Before you share a link with users, ensure that Day CQ Mail Service is configured. Otherwise, an error occurs.

1. In the Assets user interface, select the asset to share as a link.
1. From the toolbar, click/tap the **[!UICONTROL Share Link]**.

   An asset link is auto-created in the **[!UICONTROL Share Link]** field. Copy this link and share it with the users. The default expiration time for the link is one day.

   Alternatively, proceed to perform steps 3-7 of this procedure to add email recipients, configure the expiration time for the link, and send it from the dialog.

   >[!NOTE]
   >
   >If a shared asset is moved to a different location, its link stops working. Re-create the link and re-share with the users.

1. From the web console, open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against each:

    * local
    * author
    * publish

   For the local and author properties, provide the URL for the local and author instance respectively. Both local and author properties have the same value if you run a single AEM author instance. For publish, provide the URL for the publish instance.

1. In the email address box of the **[!UICONTROL Link Sharing]** dialog, type the email ID of the user you want to share the link with. You can also share the link with multiple users.

   If the user is a member of your organization, select the user's email ID from the suggested email IDs that appear in the list below the typing area. For an external user, type the complete email ID and then select it from the list.

   To enable emails to be sent out to users, configure the SMTP server details in [Day CQ Mail Service](/help/assets/configure-asset-sharing.md#configmailservice).

   >[!NOTE]
   >
   >If you enter an email ID of a user that is not a member of your organization, the words "External User" are prefixed with the email ID of the user.

1. In the **[!UICONTROL Subject]** box, enter a subject for the asset you want to share.
1. In the **[!UICONTROL Message]** box, enter an optional message.
1. In the **[!UICONTROL Expiration]** field, specify an expiration date and time for the link using the date picker. By default, the expiration date is set for a week from the date you share the link.
1. To let users download the original image along with the renditions, select **[!UICONTROL Allow download of original file]**.

   >[!NOTE]
   >
   >By default, users can only download the renditions of the asset that you share as a link.

1. Click **[!UICONTROL Share]**. A message confirms that the link is shared with the users through an email.
1. To view the shared asset, click/tap the link in the email that is sent to the user. The shared asset is displayed in the **[!UICONTROL Adobe Marketing Cloud]** page.

   To toggle to the list view, click/tap the layout icon in the toolbar.

1. To generate a preview of the asset, click/tap the shared asset. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click/tap **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click/tap **[!UICONTROL Parent Folder]** to return to the parent folder.

   >[!NOTE]
   >
   >AEM supports generating the preview of assets of these MIME types: JPG, PNG, GIF, BMP, INDD, PDF, and PPT. You can only download the assets of the other MIME types.

1. To download the shared asset, click/tap **[!UICONTROL Select]** from the toolbar, click/tap the asset, and then click/tap **[!UICONTROL Download]** from the toolbar.
1. To view the assets you shared as links, go to the Assets user interface and click/tap the GlobalNav icon. Choose **[!UICONTROL Navigation]** from the list to display the Navigation pane.
1. From the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.
1. To un-share an asset, select it and tap/click **[!UICONTROL Unshare]** from the toolbar.

A message confirms that you unshared the asset. In addition, the entry for the asset is removed from the list.
-->

## Herunterladen und Freigeben von Assets {#download-and-share-assets}

Benutzer können einige Assets herunterladen und diese außerhalb von Experience Manager freigeben. Weitere Informationen finden Sie unter [Suchen nach Assets](/help/assets/search-assets.md), [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)und [Herunterladen von Sammlungen.](manage-collections.md#download-a-collection)

## Freigeben von Assets für Kreativprofis {#share-with-creatives}

Marketingexperten und Anwender aus der Branche können genehmigte Assets mit ihren Kreativprofis problemlos gemeinsam verwenden.

* **AEM-Desktop-App**: Die App funktioniert unter Windows und Mac. Siehe Übersicht über [Desktop-Apps](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html). Informationen dazu, wie autorisierte Desktop-Benutzer problemlos auf die freigegebenen Assets zugreifen können, finden Sie unter [Durchsuchen-, Such- und Vorschauen-Assets](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#browse-search-preview-assets). Die Desktop-Benutzer können Assets erstellen und sie für ihre AEM-Benutzer freigeben, indem sie beispielsweise neue Bilder hochladen. Siehe [Hochladen von Assets mit der Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

* **Adobe Asset Link**: Die Kreativprofis können Assets direkt in Adobe InDesign, Adobe Illustrator und Adobe Fotoshop suchen und verwenden.

## Konfigurieren der Asset-Freigabe {#configure-sharing}

Die verschiedenen Optionen zum Freigeben der Assets erfordern eine bestimmte Konfiguration und müssen spezifische Voraussetzungen erfüllen.

### Asset-Linkfreigabe konfigurieren {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

Sie generieren die URL für Assets, die Sie für Benutzer freigeben möchten, im Dialogfeld „Linkfreigabe“. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei AEM Assets anmelden müssen.

>[!NOTE]
>
>Wenn Sie Links von Ihrer AEM Authoring-Instanz an externe Entitäten freigeben möchten, stellen Sie sicher, dass Sie nur die folgenden URLs für `GET` Anforderungen bereitstellen. Sperren Sie andere URLs, um sicherzustellen, dass Ihre AEM Author-Instanz sicher ist.
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


<!--
## Configure Day CQ mail service {#configmailservice}

Before you can share assets as links, configure the email service.

1. Click or tap the AEM logo, and then navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. From the list of services, locate **[!UICONTROL Day CQ Mail Service]**.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **Day CQ Mail Service]** with the details mentioned against their names:

    * SMTP server host name: email server host name
    * SMTP server port: email server port
    * SMTP user: email server user name
    * SMTP password: email server password

1. Click/tap **[!UICONTROL Save]**.
-->

### Konfigurieren der maximal zulässigen Datengröße {#maxdatasize}

Wenn Sie Assets herunterladen, die mithilfe der Linkfreigabe-Funktion freigegeben wurden, komprimiert AEM die Asset-Hierarchie aus dem Repository und gibt anschließend das Asset in einer ZIP-Datei zurück. Da jedoch die Datenmenge, die in einer ZIP-Datei komprimiert werden kann, nicht begrenzt wird, führt das bei großen komprimierten Datenmengen zu Speicherfehlern in JVM. Um das System aufgrund dieser Situation vor einem möglichen DoS-Angriff zu schützen, können Sie die maximale Größe der heruntergeladenen Dateien konfigurieren. Wenn die unkomprimierte Größe des Assets den konfigurierten Wert überschreitet, werden Asset-Download-Anforderungen abgelehnt. Der Standardwert lautet 100 MB.

1. Tippen/Klicken Sie auf das AEM-Logo und gehen Sie dann zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web Console]**.
1. From the web console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Open the configuration in edit mode, and modify the value of the **[!UICONTROL Max Content Size (uncompressed)]** parameter.
1. Speichern Sie die Änderungen.

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->

### Aktivieren von Desktop-Aktionen für die Verwendung mit der Desktop-App {#desktop-actions}

Über die Assets-Benutzeroberfläche in einem Browser können Sie zu den Asset-Speicherorten navigieren oder Assets auschecken und öffnen, um sie in Ihrem Desktop-Programm zu bearbeiten. Diese Optionen werden als &quot;Desktop-Aktionen&quot;bezeichnet. Um sie zu aktivieren, finden Sie unter [Aktivieren von Desktop-Aktionen in der AEM-Weboberfläche](https://docs.adobe.com/help/en/experience-manager-desktop-app/using/using.html#desktopactions-v2).

![Desktop-Aktionen aktivieren, die beim Arbeiten mit der Desktop-App als Verknüpfung verwendet werden](assets/enable_desktop_actions.png)

### Konfigurationen zur Verwendung von Adobe Asset Link {#configure-asset-link}

Adobe Asset Link optimiert die Zusammenarbeit zwischen Kreativen und Marketingexperten bei der Inhaltserstellung. Es verbindet Adobe Experience Manager (AEM)-Assets mit Creative Cloud-Desktop-Apps Adobe InDesign, Adobe Fotoshop und Adobe Illustrator. Über das Bedienfeld &quot;Adobe Asset-Link&quot;können kreative Elemente auf in AEM Assets gespeicherte Inhalte zugreifen und diese bearbeiten, ohne die Kreativ-Apps zu verlassen, mit denen sie am besten vertraut sind.

Siehe [Konfigurieren von AEM für die Verwendung mit Adobe Asset Link](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html).

## Best Practices und Fehlerbehebung {#bestpractices}

* Asset-Ordner oder -Sammlungen, die einen Whitespace in ihrem Namen enthalten, werden möglicherweise nicht freigegeben.
* Wenn Benutzer die freigegebenen Assets nicht herunterladen können, fragen Sie bei Ihrem AEM-Administrator nach den [Download-Beschränkungen](#maxdatasize).

<!--
* If you cannot send email with links to shared assets or if the other users cannot receive your email, check with your AEM administrator if the [email service](/help/assets/configure-asset-sharing.md#configmailservice) is configured or not. 
* If you cannot share assets using link sharing functionality, ensure that you have the appropriate permissions. See [share assets](#sharelink).
-->

<!--
Add content or link about how to share using Brand Portal when it is available on Cloud Service.
-->
