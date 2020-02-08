---
title: Digital Rights Management in Adobe Experience Manager Assets
description: Erfahren Sie, wie Sie den Assetablaufstatus und Informationen für lizenzierte Assets in AEM verwalten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Verwaltung digitaler Rechte in Experience Manager-Assets {#digital-rights-management-in-assets}

Digitale Assets sind oftmals mit einer Lizenz verbunden, in der die Bedingungen und die Nutzungsdauer festgelegt sind. Da Adobe Experience Manager (AEM) Assets vollständig in die AEM-Plattform integriert sind, können Sie Asset-Ablaufinformationen und Asset-Status effizient verwalten. Sie können Lizenzinformationen mit Assets verknüpfen.

## Asset-Ablauf {#asset-expiration}

Der Asset-Ablauf ist eine effektive Möglichkeit zum Durchsetzen von Lizenzanforderungen für Assets. Wenn ein veröffentlichtes Asset abläuft, wird seine Veröffentlichung aufgehoben und damit die Möglichkeit einer Lizenzverletzung unterbunden. Ein Benutzer ohne Administratorrechte kann ein abgelaufenes Asset weder bearbeiten, kopieren, verschieben, veröffentlichen noch herunterladen.

Sie können den Ablaufstatus eines Assets an den folgenden Stellen anzeigen:

* **Kartenansicht**: Bei abgelaufenen Assets gibt ein Flag auf der Karte an, dass sie abgelaufen ist.
* **Listenansicht**: Bei abgelaufenen Assets zeigt die Spalte **[!UICONTROL Status]** das Banner **[!UICONTROL Abgelaufen]** an.
* **Zeitschiene**: Sie können den Ablaufstatus eines Assets in der Zeitleiste anzeigen. Wählen Sie das Asset aus und wählen Sie &quot;Zeitschiene&quot;.
* **Referenzleiste**: Sie können den Ablaufstatus von Assets auch in der Leiste &quot; **[!UICONTROL Referenzen]** &quot;anzeigen. Hier werden der Assetablaufstatus und die Beziehungen zwischen ebenenübergreifenden Assets und referenzierten Unter-Assets, Sammlungen und Projekten verwaltet.

1. Navigieren Sie zu dem Asset, für das Sie referenzierende Webseiten und ebenenübergreifende Assets anzeigen möchten.
1. Wählen Sie das Asset aus und klicken bzw. tippen Sie auf das Symbol für die globale Navigation.
1. Choose **[!UICONTROL References]** from the menu.
1. For expired assets, the References rail displays the expiry status **[!UICONTROL Asset is Expired]** at the top. If the asset has expired subassets, the References rail displays the status **[!UICONTROL Asset has Expired Sub-Assets]**.

### Suchen von abgelaufenen Assets {#search-expired-assets}

Sie können im Suchfeld nach abgelaufenen Assets einschließlich abgelaufener Unter-Assets suchen.

1. Klicken Sie in der Assets-Konsole auf das Suchsymbol in der Symbolleiste, um das Feld &quot;Omni-Suche&quot;anzuzeigen.

1. Betätigen Sie bei in das Omni-Suchfeld gesetztem Cursor die Eingabetaste, um die Seite mit den Suchergebnissen anzuzeigen.

1. Klicken Sie auf das GlobalNav-Symbol, um das Suchfeld anzuzeigen.

1. Klicken/tippen Sie auf die Option **[!UICONTROL Gültigkeitsstatus]**, um sie zu erweitern.

1. Wählen Sie **[!UICONTROL Abgelaufen]** aus. Die abgelaufenen Assets werden in den Suchergebnissen angezeigt.

When you choose the **Expired** option, the Assets console only displays the expired assets and subassets that are referenced by compound assets. Die ebenenübergreifenden Assets, die auf abgelaufene Unter-Assets verweisen, werden nicht sofort nach Ablauf eines Unter-Assets angezeigt. Stattdessen werden sie angezeigt, nachdem AEM Assets bei der nächsten Ausführung des Planers erkennt, dass sie auf abgelaufene Unter-Assets verweisen.

Wenn Sie das Ablaufdatum eines veröffentlichten Assets in ein Datum ändern, das vor dem aktuellen Planerzyklus liegt, erkennt der Planer das Asset als abgelaufenes Asset, wenn es das nächste Mal aufgeführt wird, und spiegelt dementsprechend seinen Status wider.

Wenn eine Störung oder ein Fehler verhindert, dass der Planer abgelaufene Assets im aktuellen Zyklus erkennt, untersucht der Planer diese Assets im nächsten Zyklus erneut und erkennt dann, dass sie abgelaufen sind.

To enable the Assets console to display the referencing compound assets along with the expired subassets, configure an **Adobe CQ DAM Expiry Notification** workflow in AEM Configuration Manager.

1. Öffnen Sie AEM Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time based Scheduler]** is selected, which schedules a job to check at a specific time whether an asset has expired subassets. Nach Abschluss des Auftrags werden Assets mit abgelaufenen Unter-Assets und verwiesenen Assets in den Suchergebnissen als abgelaufen angezeigt.

1. To run the job periodically, clear the **[!UICONTROL Time Based Scheduler Rule]** field and modify the time in seconds in the **[!UICONTROL Periodic Scheduler]** field. Beispiel: Der Beispielausdruck &quot;0 0 0 &amp;ast; &amp;ast; ?&#39; löst den Auftrag um 00:00 Uhr aus.
1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

   >[!NOTE]
   >
   >Nur der Ersteller eines Assets (die Person, die ein bestimmtes Asset in AEM Assets hochlädt) erhält eine E-Mail, wenn das Asset abläuft. Weitere Informationen zum Konfigurieren von E-Mail-Benachrichtigungen auf AEM-Ebene finden Sie unter Konfigurieren von E-Mail-Benachrichtigungen.

1. Geben Sie im Feld **[!UICONTROL Vorabbenachrichtigung in Sekunden]** den Zeitpunkt in Sekunden vor dem Ablauf eines Assets an, zu dem Sie über den bevorstehenden Ablauf benachrichtigt werden möchten. Wenn Sie ein Administrator oder der Ersteller des Assets sind, werden Sie vor Ablauf des Assets darüber informiert, dass das Asset nach dem angegebenen Zeitraum ablaufen wird.

   Nachdem das Asset abgelaufen ist, erhalten Sie eine weitere Benachrichtigung, die den Ablauf bestätigt. Außerdem werden die abgelaufenen Assets deaktiviert.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Asset-Zustände {#asset-states}

Die Konsole „Assets“ in Adobe Experience Manager (AEM) Assets kann verschiedene Zustände für Assets anzeigen. Abhängig vom aktuellen Zustand eines bestimmten Assets zeigt die zugehörige Kartenansicht eine Beschreibung des Zustands an, z. B. „Abgelaufen“, „Veröffentlicht“, „Genehmigt“, „Abgelehnt“ usw.

1. Wählen Sie in der Assets-Benutzeroberfläche ein Asset aus.

1. Tap/click the **[!UICONTROL Publish]** icon from the toolbar. If you can&#39;t see the **Publish** icon on the toolbar, tap/click **[!UICONTROL More]** on the toolbar and locate the **[!UICONTROL Publish]** icon.

1. Choose **[!UICONTROL Publish]** from the menu, and then close the confirmation dialog.
1. Beenden Sie den Auswahlmodus. Der Veröffentlichungsstatus des Assets wird in der Kartenansicht im unteren Bereich der Miniaturansicht des Assets angezeigt. In der Listenansicht zeigt die Spalte „Veröffentlicht“ die Zeit an, zu der das Asset veröffentlicht wurde.

1. Wählen Sie in der Assets-Benutzeroberfläche ein Asset aus und tippen oder klicken Sie auf das Symbol **[!UICONTROL Eigenschaften]**, um die zugehörige Detailseite anzuzeigen.

1. In the Advanced tab, and set an expiration date for the asset from the **[!UICONTROL Expires]** field under.

1. Click **[!UICONTROL Save]** and then click **[!UICONTROL Close]** to display the Asset console.
1. Der Veröffentlichungsstatus des Assets weist in der Kartenansicht im unteren Bereich der Miniaturansicht darauf hin, dass das Asset abgelaufen ist. In the list view, the status of the asset is displayed as **[!UICONTROL Expired]**.

1. Wählen Sie in der Konsole „Assets“ einen Ordner aus und erstellen Sie eine Prüfungsaufgabe für den Ordner.
1. Review and approve/reject the assets in the review task and click **[!UICONTROL Complete]**.
1. Navigieren Sie zu dem Ordner, für den Sie die Prüfungsaufgabe erstellt haben. Der Status des Assets, das Sie bestätigt oder abgelehnt haben, wird unten in der Kartenansicht angezeigt. In der Listenansicht werden die Status der Genehmigung und des Ablaufs in den entsprechenden Spalten angezeigt.

1. To search for assets based on their status, click/tap the **[!UICONTROL Search]** icon to display the Omnisearch bar.

1. Hit the Return key and then click/tap the **[!UICONTROL GlobalNav]** icon to display the Search panel.
1. In the Search panel, tap/click **[!UICONTROL Publish Status]** and select **[!UICONTROL Published]** to search for published assets in AEM Assets.

1. Tap/click **[!UICONTROL Approval Status]** and click the appropriate option to search for approved or rejected assets.

1. To search for assets based on their expiration status, select **[!UICONTROL Expiry Status]** in the Search panel and choose the appropriate option.

1. Sie können auch auf Grundlage einer Kombination von Statusangaben mit verschiedenen Suchfacetten nach Assets suchen. Sie können beispielsweise nach veröffentlichten Assets suchen, die in einer Prüfungsaufgabe bestätigt wurden und noch nicht abgelaufen sind, indem Sie die entsprechenden Optionen in den Suchfacetten auswählen.

## Verwaltung digitaler Rechte in Experience Manager-Assets {#digital-rights-management-in-assets-1}

Diese Funktion setzt die Annahme der Lizenzvereinbarung zwingend voraus. Erst nach diesem Schritt können lizenzierte Assets von Adobe Experience Manager (AEM) Assets heruntergeladen werden.

Wenn Sie ein geschütztes Asset auswählen und auf das Symbol **[!UICONTROL Herunterladen]** klicken, werden Sie auf die Lizenzseite weitergeleitet, auf der Sie die Lizenzvereinbarung annehmen können. Wenn Sie die Lizenzvereinbarung nicht annehmen, wird die Schaltfläche **[!UICONTROL Herunterladen]** deaktiviert.

Falls die Auswahl mehrere geschützte Assets enthält, wählen Sie jeweils eines aus, nehmen Sie die Lizenzvereinbarung an und fahren Sie mit dem Herunterladen des Assets fort.

Ein Asset gilt als geschützt, wenn eine der folgenden Bedingungen erfüllt ist:

* Die `xmpRights:WebStatement`-Metadateneigenschaft des Assets verweist auf den Pfad der CQ-Seite, die die Lizenzvereinbarung für das Asset enthält.
* Beim Wert der `adobe_dam:restrictions`-Metadateneigenschaft des Assets handelt es sich um nicht formatierten HTML-Code, der die Lizenzvereinbarung angibt.

>[!NOTE]
>
>The location `/etc/dam/drm/licences` used for storing licenses in earlier releases of AEM is deprecated.
>
>Wenn Sie Lizenzseiten erstellen, ändern oder aus früheren AEM-Versionen importieren, empfiehlt Adobe, die Seiten unter `/apps/settings/dam/drm/licenses` oder `/conf/*/settings/dam/drm/licenses`zu speichern.

### DRM-Assets herunterladen {#downloading-drm-assets}

1. Wählen Sie die gewünschten Assets in der Kartenansicht aus und klicken Sie auf das Symbol **[!UICONTROL Herunterladen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Copyright-Management]** das Asset aus, das Sie von der Liste herunterladen möchten.
1. Wählen Sie im Lizenzfenster **[!UICONTROL Zustimmen]**. Möglicherweise erscheint ein Häkchen neben dem Asset, für das Sie die Lizenzvereinbarung angenommen haben. Tap/click the **[!UICONTROL Download]** button.

   >[!NOTE]
   >
   >The **[!UICONTROL Download]** button is enabled only when you choose to agree to the license agreement for a protected asset. However, if your selection comprises both protected and unprotected assets, only the protected assets are listed in the left pane and the **[!UICONTROL Download]** button is enabled to download the unprotected assets. Sie können mehrere Lizenzvereinbarungen für verschiedene geschützte Assets gleichzeitig annehmen, indem Sie die Assets in der Liste auswählen und anschließend auf **[!UICONTROL Zustimmen]** klicken.

1. In the dialog, tap/click **[!UICONTROL Download]** to download the asset or its renditions.
