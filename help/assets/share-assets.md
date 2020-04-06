---
title: Freigeben von Assets, Ordnern und Sammlungen als Link
description: In diesem Artikel wird beschrieben, wie Sie Assets, Ordner und Sammlungen in Experience Manager Assets als Hyperlink freigeben.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Freigeben und Verteilen von in Experience Manager verwalteten Assets {#share-assets-from-aem}

Mit Adobe Experience Manager (AEM)-Assets können Sie Assets, Ordner und Sammlungen für Mitglieder Ihres Unternehmens und externe Entitäten, einschließlich Partner und Anbieter, freigeben. Sie können die folgenden Methoden verwenden, um Assets aus Experience Manager Assets als Cloud-Dienst freizugeben:

* Freigeben von als Link
* Herunterladen von Assets
* Über AEM-Desktop-App freigeben
* Über Adobe Asset Link freigeben
* (Anstehende Funktion) Freigeben mit dem Markenportal

## Freigeben von Assets als Link {#sharelink}

Sie generieren die URL für Assets, die Sie für Benutzer freigeben möchten, im Dialogfeld „Linkfreigabe“. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Die Freigabe von Assets über einen Link ist eine praktische Methode, um Ressourcen für externe Parteien verfügbar zu machen, ohne dass sich diese zunächst bei AEM Assets anmelden müssen.

>[!NOTE]
>
>* Sie benötigen die Berechtigung &quot;ACL bearbeiten&quot;für den Ordner oder das Asset, das Sie als Link freigeben möchten.
>* Bevor Sie einen Link für andere Benutzer freigeben, stellen Sie sicher, dass Day CQ Mail Service konfiguriert ist. Andernfalls tritt ein Fehler auf.


1. Wählen Sie in der Assets-Benutzeroberfläche das Asset aus, das als Link freigegeben werden soll.
1. Klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Link freigeben]**.

   An asset link is auto-created in the **[!UICONTROL Share Link]** field. Sie können diesen Link kopieren und für andere Benutzer freigeben. Die Standard-Ablaufzeit für den Link beträgt einen Tag.

   Alternativ dazu können Sie auch die Schritte 3 bis 7 dieses Verfahrens ausführen, um E-Mail-Empfänger hinzuzufügen, die Ablaufzeit für den Link zu konfigurieren und ihn aus dem Dialogfeld zu senden.

   >[!NOTE]
   >
   >Wenn ein freigegebenes Asset an einen anderen Speicherort verschoben wird, funktioniert der Link zum Asset nicht mehr. Erstellen Sie den Link erneut und geben Sie ihn erneut für die Benutzer frei.

1. Öffnen Sie in der Web Console die **[!UICONTROL Day CQ Link Externalizer]**-Konfiguration und ändern Sie die folgenden Eigenschaften im Feld **[!UICONTROL Domänen]** mit den jeweils angegebenen Werten:

   * local
   * Autor
   * veröffentlichen
   Für die Eigenschaften „local“ und „author“ geben Sie die URL für die entsprechenden Instanzen an. Wenn Sie eine einzelne AEM-Autoreninstanz ausführen, haben die Eigenschaften „local“ und „author“ denselben Wert. Geben Sie für die Eigenschaft „publish“ die URL für die Veröffentlichungsinstanz an.

1. Geben Sie im Dialogfeld **[!UICONTROL Linkfreigabe]** in das Feld „E-Mail-Adresse“ die E-Mail-ID des Benutzers ein, für den Sie den Link freigeben möchten. Sie können den Link auch für mehrere Benutzer freigeben.

   Wenn der Benutzer zu Ihrem Unternehmen gehört, wählen Sie die E-Mail-ID des Benutzers in den vorgeschlagenen E-Mail-IDs aus, die in der Liste unter dem Eingabebereich angezeigt werden. Geben Sie bei einem externen Benutzer die vollständige E-Mail-ID ein und wählen Sie diese dann aus der Liste aus.

   Damit E-Mails an Benutzer gesendet werden können, konfigurieren Sie die SMTP-Serverdetails in [Day CQ Mail Service](/help/assets/configure-asset-sharing.md#configmailservice).

   >[!NOTE]
   >
   >Wenn Sie die E-Mail-ID eines Benutzers eingeben, der nicht zu Ihrem Unternehmen gehört, wird den Worten „Externer Benutzer“ die E-Mail-ID des Benutzers vorangestellt.

1. Geben Sie in das Feld **[!UICONTROL Betreff]** einen Betreff für das freizugebende Asset ein.
1. Geben Sie im Feld **[!UICONTROL Meldung]** eine optionale Meldung ein.
1. Geben Sie im Feld **[!UICONTROL Ablauf]** mit der Datumsauswahl ein Ablaufdatum und eine Ablaufuhrzeit für den Link an. Standardmäßig ist das Ablaufdatum auf eine Woche nach dem Datum der Linkfreigabe gesetzt.
1. Damit Benutzer das Originalbild zusammen mit den Ausgabeformaten herunterladen können, wählen Sie die Option **[!UICONTROL Download der Originaldatei zulassen]** aus.

   >[!NOTE]
   >
   >Standardmäßig können Benutzer nur die Ausgabeformate des Assets herunterladen, das Sie als Link freigegeben haben.

1. Klicken Sie auf **[!UICONTROL Freigeben]**. Eine Meldung bestätigt, dass der Link per E-Mail für die jeweiligen Benutzer freigegeben wurde.
1. Um das freigegebene Asset anzeigen, klicken/tippen Sie auf den Link in der E-Mail, die dem Benutzer gesendet wird. Das freigegebene Asset wird auf der Seite **[!UICONTROL Adobe Marketing Cloud]** angezeigt.

   Klicken oder tippen Sie auf das Layout-Symbol in der Symbolleiste, um die Listenansicht umzuschalten.

1. Um eine Vorschau des Assets zu generieren, tippen/klicken Sie auf das freigegebene Asset. Um die Vorschau zu schließen und zur Seite **[!UICONTROL Experience Cloud]** zurückzukehren, tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Zurück]**. Wenn Sie einen Ordner freigegeben haben, tippen/klicken Sie auf **[!UICONTROL Übergeordneter Ordner]**, um zum übergeordneten Ordner zurückzukehren.

   >[!NOTE]
   >
   >AEM unterstützt das Generieren der Vorschau von Assets dieser MIME-Typen: JPG, PNG, GIF, BMP, INDD, PDF und PPT. Für Assets anderer MIME-Typen können Sie nur die Assets herunterladen.

1. To download the shared asset, click/tap **[!UICONTROL Select]** from the toolbar, click/tap the asset, and then click/tap **[!UICONTROL Download]** from the toolbar.
1. Um die Assets anzuzeigen, die Sie als Links freigegeben haben, wechseln Sie zur Assets-Benutzeroberfläche und klicken oder tippen Sie auf das GlobalNav-Symbol. Choose **[!UICONTROL Navigation]** from the list to display the Navigation pane.
1. Wählen Sie im Navigationsbereich **[!UICONTROL Freigegebene Links]**, um eine Liste der freigegebenen Assets anzuzeigen.
1. To un-share an asset, select it and tap/click **[!UICONTROL Unshare]** from the toolbar.

Eine Meldung bestätigt, dass Sie die Asset-Freigabe aufgehoben haben. Außerdem wird der Eintrag für das Asset aus der Liste entfernt.

## Herunterladen und Freigeben von Assets {#download-and-share-assets}

Benutzer können einige Assets herunterladen und diese außerhalb von Experience Manager freigeben. Weitere Informationen finden Sie unter [Suchen nach Assets](/help/assets/search-assets.md), [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)und [Herunterladen von Sammlungen.](manage-collections.md#download-a-collection)

## Freigeben von Assets für Kreativprofis {#share-with-creatives}

Marketingexperten und Anwender aus der Branche können genehmigte Assets mit ihren Kreativprofis problemlos gemeinsam verwenden.

* **AEM-Desktop-App**: Die App funktioniert unter Windows und Mac. Siehe Übersicht über [Desktop-Apps](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html). Informationen dazu, wie autorisierte Desktop-Benutzer problemlos auf die freigegebenen Assets zugreifen können, finden Sie unter [Durchsuchen-, Such- und Vorschauen-Assets](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#browse-search-preview-assets). Die Desktop-Benutzer können neue Assets erstellen und diese dann für ihre AEM-Benutzer freigeben, indem sie beispielsweise neue Bilder hochladen. Siehe [Hochladen von Assets mit der Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

* **Adobe Asset Link**: Die Kreativprofis können Assets direkt in Adobe InDesign, Adobe Illustrator und Adobe Fotoshop suchen und verwenden.

### Best Practices und Fehlerbehebung {#bestpractices}

* Asset-Ordner oder -Sammlungen, die einen Whitespace in ihrem Namen enthalten, werden möglicherweise nicht freigegeben.
* Wenn Benutzer die freigegebenen Assets nicht herunterladen können, fragen Sie bei Ihrem AEM-Administrator nach den [Download-Beschränkungen](/help/assets/configure-asset-sharing.md#maxdatasize).
* Wenn Sie keine E-Mail mit Links zu freigegebenen Assets senden können oder die anderen Benutzer Ihre E-Mail nicht empfangen können, fragen Sie Ihren AEM-Administrator, ob der [E-Mail-Dienst](/help/assets/configure-asset-sharing.md#configmailservice) konfiguriert wurde.
* Wenn Sie Assets nicht mit der Funktion zum Freigeben von Links freigeben können, stellen Sie sicher, dass Sie über die entsprechenden Berechtigungen verfügen. Siehe [Freigeben von Assets](#sharelink).

<!--
Add content or link about how to share using BP, DA, AAL, etc.
-->
