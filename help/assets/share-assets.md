---
title: Freigeben von Assets, Ordnern und Sammlungen als Link
description: In diesem Artikel wird beschrieben, wie Sie Assets, Ordner und Sammlungen in [!DNL Experience Manager Assets] als Hyperlink freigeben.
contentOwner: AG
feature: Asset-Management, Zusammenarbeit, Asset-Verteilung
role: Business Practitioner,Administrator
exl-id: 14e897cc-75c2-42bd-8563-1f5dd23642a0
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 88%

---

# Freigeben und Verteilen von in verwalteten Assets in [!DNL Experience Manager] {#share-assets-from-aem}

Mit [!DNL Adobe Experience Manager Assets] können Sie Assets, Ordner und Sammlungen für Mitglieder Ihres Unternehmens und externe Einheiten (z. B. Partner und Anbieter) freigeben. Verwenden Sie die folgenden Methoden, um Assets aus [!DNL Experience Manager Assets] as a [!DNL Cloud Service] freizugeben:

* Freigeben als Link.
* [Herunterladen von Assets und separates Freigeben.](/help/assets/download-assets-from-aem.md)
* Freigeben mit dem [[!DNL Experience Manager] Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=de).
* Freigeben mit [[!DNL Adobe Asset Link]](https://www.adobe.com/de/creativecloud/business/enterprise/adobe-asset-link.html).
* Freigeben mit [[!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html?lang=de).

## Freigeben von Assets als Link {#sharelink}

Die URL für Assets, die Sie für Benutzer freigeben möchten, generieren Sie im Dialogfeld „Link-Freigabe“. Benutzer mit Administratorrechten oder mit Leserechten für den Speicherort `/var/dam/share` können dann die Links sehen, die für sie freigegeben sind. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei [!DNL Assets] anmelden müssen.

>[!NOTE]
>
>* Sie benötigen für die Ordner bzw. Assets, die Sie als Link freigeben möchten, zunächst die Berechtigung „ACL bearbeiten“.
>* Bevor Sie einen Link für Benutzer freigeben, stellen Sie sicher, dass [ausgehende E-Mails aktiviert sind](/help/implementing/developing/introduction/development-guidelines.md#sending-email). Andernfalls tritt ein Fehler auf.


1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche das Asset aus, das als Link freigegeben werden soll.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Link freigeben]**. Im Feld **[!UICONTROL Link freigeben]** wird automatisch ein Asset-Link erstellt. Sie können diesen Link kopieren und für andere Benutzer freigeben. Die Standard-Ablaufzeit für den Link beträgt einen Tag.

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

Benutzer können benötigte Assets herunterladen und diese außerhalb von [!DNL Experience Manager] freigeben. Weitere Informationen finden Sie unter [Suchen von Assets](/help/assets/search-assets.md), [Herunterladen von Assets](/help/assets/download-assets-from-aem.md) und [Herunterladen von Sammlungen](manage-collections.md#download-a-collection).

## Freigeben von Assets für Kreativschaffende {#share-with-creatives}

Marketing-Experten und Anwender aus der Branche können genehmigte Assets problemlos für ihre Kreativschaffenden freigeben.

* **Experience Manager-Desktop-Programm**: Das Programm funktioniert unter Windows und Mac. Siehe [Überblick über das AEM-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html). Informationen dazu, wie autorisierte Desktop-Benutzer problemlos auf die freigegebenen Assets zugreifen können, finden Sie unter [Durchsuchen, Suchen und Anzeigen einer Vorschau von Assets](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#browse-search-preview-assets). Die Desktop-Benutzer können Assets erstellen und diese dann für ihre AEM-Benutzer freigeben, indem sie beispielsweise neue Bilder hochladen. Siehe [Hochladen von Assets mit dem Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#upload-and-add-new-assets-to-aem).

* **Adobe Asset Link**: Kreativschaffende können Assets direkt in [!DNL Adobe InDesign], [!DNL Adobe Illustrator] und [!DNL Adobe Photoshop] suchen und verwenden.

## Konfigurieren der Asset-Freigabe {#configure-sharing}

Die verschiedenen Optionen zum Freigeben der Assets erfordern eine spezifische Konfiguration und müssen bestimmte Voraussetzungen erfüllen.

### Konfigurieren der Asset-Link-Freigabe {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

Die URL für Assets, die Sie für Benutzer freigeben möchten, generieren Sie im Dialogfeld „Link-Freigabe“. Benutzer mit Administratorrechten oder mit Leserechten für den Speicherort `/var/dam/share` können dann die Links sehen, die für sie freigegeben sind. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei [!DNL Assets] anmelden müssen.

>[!NOTE]
>
>Wenn Sie Links von Ihrer Autoreninstanz für externe Entitäten freigeben möchten, stellen Sie sicher, dass Sie nur die folgenden URLs für `GET`-Anfragen bereitstellen. Blockieren Sie andere URLs, um sicherzustellen, dass Ihre Autoreninstanz sicher ist.
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

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.
### Configure maximum data size {#maxdatasize}

When you download assets from the link shared using the Link Sharing feature, AEM compresses the asset hierarchy from the repository and then returns the asset in a ZIP file. However, in the absence of limits to the amount of data that can be compressed in a ZIP file, huge amounts of data is subjected to compression, which causes out of memory errors in JVM. To secure the system from a potential denial of service attack due to this situation, you can configure the maximum size of the downloaded files. If uncompressed size of the asset exceeds the configured value, asset download requests are rejected. The default value is 100 MB.

1. Click/Tap the AEM logo and then go to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. From the web console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Open the configuration in edit mode, and modify the value of the **[!UICONTROL Max Content Size (uncompressed)]** parameter.
1. Save the changes.
-->

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->

### Aktivieren von Desktop-Aktionen für die Verwendung mit dem Desktop-Programm {#desktop-actions}

Über die [!DNL Assets]-Benutzeroberfläche in einem Browser können Sie zu den Asset-Speicherorten navigieren oder das Asset auschecken und öffnen, um es in Ihrem Desktop-Programm zu bearbeiten. Diese Optionen werden als Desktop-Aktionen bezeichnet. Um sie zu aktivieren, lesen Sie [Aktivieren von Desktop-Aktionen in [!DNL Assets] Web-Schnittstelle](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#desktopactions-v2).

![Aktivieren von Desktop-Aktionen, die beim Arbeiten mit dem Desktop-Programm als Verknüpfung verwendet werden](assets/enable_desktop_actions.png)

### Konfigurationen zur Verwendung von [!DNL Adobe Asset Link] {#configure-asset-link}

Adobe Asset Link optimiert die Zusammenarbeit zwischen Kreativen und Marketern bei der Inhaltserstellung. Es verbindet [!DNL Adobe Experience Manager Assets] mit den [!DNL Creative Cloud]-Desktop-Programmen [!DNL Adobe InDesign], [!DNL Adobe Photoshop] und [!DNL Adobe Illustrator]. Über das [!DNL Adobe Asset Link]-Bedienfeld können Kreativschaffende auf in [!DNL Assets] gespeicherte Inhalte zugreifen und diese bearbeiten, ohne die Kreativprogramme zu verlassen, mit denen sie am besten vertraut sind.

Siehe [Konfigurieren von [!DNL Assets] für die Verwendung mit [!DNL Adobe Asset Link]](https://helpx.adobe.com/de/enterprise/using/configure-aem-assets-for-asset-link.html).

## Best Practices und Fehlerbehebung {#bestpractices}

* Asset-Ordner oder Sammlungen, die ein Leerzeichen im Namen enthalten, werden möglicherweise nicht freigegeben.
* Wenn Benutzer die freigegebenen Assets nicht herunterladen können, fragen Sie bei Ihrem AEM-Administrator nach den [Download-Beschränkungen](#maxdatasize).
* Damit ein Benutzer eine Vorschau eines Videos anzeigen kann, das über die Linkfreigabe freigegeben wird, muss das Video über eine statische Videowiedergabe verfügen, die unter `/jcr:content/renditions` im Videoknoten im Repository verfügbar ist. Die Vorschau hängt nicht von der Verfügbarkeit eines [!DNL Dynamic Media] -Ausgabeformats ab.
* Beim Herunterladen eines Video-Assets über die Linkfreigabe werden die [!DNL Dynamic Media]-Ausgabeformate nicht im heruntergeladenen Archiv enthalten.

<!--
* If you cannot send email with links to shared assets or if the other users cannot receive your email, check with your AEM administrator if the [email service](/help/assets/configure-asset-sharing.md#configmailservice) is configured or not. 
* If you cannot share assets using link sharing functionality, ensure that you have the appropriate permissions. See [share assets](#sharelink).
-->

<!-- TBD: Add content or link about how to share using Brand Portal when it is available on [!DNL Cloud Service].
-->
