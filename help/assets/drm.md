---
title: Digital Rights Management in Adobe Experience Manager Assets
description: Erfahren Sie, wie Sie den Assetablaufstatus und Informationen für lizenzierte Assets in AEM verwalten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7141e42f53c556c0ac21def6085182ef400f5a71

---


# Verwaltung digitaler Rechte in Experience Manager-Assets {#digital-rights-management-in-assets}

Digitale Assets sind oftmals mit einer Lizenz verbunden, in der die Bedingungen und die Nutzungsdauer festgelegt sind. Da Adobe Experience Manager (AEM) Assets vollständig in die AEM-Plattform integriert sind, können Sie Asset-Ablaufinformationen und Asset-Status effizient verwalten. Sie können Lizenzinformationen mit Assets verknüpfen.

## Asset-Ablauf {#asset-expiration}

Der Asset-Ablauf ist eine effektive Möglichkeit zum Durchsetzen von Lizenzanforderungen für Assets. Wenn ein veröffentlichtes Asset abläuft, wird seine Veröffentlichung aufgehoben und damit die Möglichkeit einer Lizenzverletzung unterbunden. Ein Benutzer ohne Administratorrechte kann ein abgelaufenes Asset weder bearbeiten, kopieren, verschieben, veröffentlichen noch herunterladen.

Sie können den Ablaufstatus eines Assets an den folgenden Orten Ansichten vornehmen:

* **Ansicht** der Karte: Bei abgelaufenen Assets gibt ein Flag auf der Karte an, dass sie abgelaufen ist.
* **Ansicht** der Liste: Bei abgelaufenen Assets zeigt die Spalte **[!UICONTROL Status]** das Banner **[!UICONTROL Abgelaufen]** an.
* **Zeitschiene**: Sie können den Ablaufstatus eines Assets in der Zeitleiste Ansicht haben. Wählen Sie das Asset aus und wählen Sie &quot;Zeitschiene&quot;.
* **Referenzleiste**: Sie können den Ablaufstatus von Assets auch in der Leiste &quot; **[!UICONTROL Referenzen]** &quot;Ansicht haben. Hier werden der Assetablaufstatus und die Beziehungen zwischen ebenenübergreifenden Assets und referenzierten Unter-Assets, Sammlungen und Projekten verwaltet.

1. Navigieren Sie zu dem Asset, für das Sie referenzierende Webseiten und ebenenübergreifende Assets anzeigen möchten.
1. Wählen Sie das Asset aus und klicken bzw. tippen Sie auf das Symbol für die globale Navigation.
1. Choose **[!UICONTROL References]** from the menu.
1. For expired assets, the References rail displays the expiry status **[!UICONTROL Asset is Expired]** at the top. If the asset has expired subassets, the References rail displays the status **[!UICONTROL Asset has Expired Sub-Assets]**.

### Suchen von abgelaufenen Assets {#search-expired-assets}

Sie können im Suchfeld nach abgelaufenen Assets einschließlich abgelaufener Unter-Assets suchen.

1. Klicken Sie in der Assets-Konsole auf das Suchsymbol in der Symbolleiste, um das Suchfeld anzuzeigen.

1. Drücken Sie mit dem Cursor in das Feld Omniture Search die Eingabetaste, um die Suchergebnisseite anzuzeigen.

1. Klicken Sie auf das GlobalNav-Symbol, um das Suchfeld anzuzeigen.

1. Klicken Sie auf die Option **[!UICONTROL Ablaufstatus]**, um sie zu erweitern.

1. Wählen Sie **[!UICONTROL Abgelaufen]** aus. Die abgelaufenen Assets werden in den Suchergebnissen angezeigt.

When you choose the **[!UICONTROL Expired]** option, the Assets console only displays the expired assets and subassets that are referenced by compound assets. Die ebenenübergreifenden Assets, die auf abgelaufene Unter-Assets verweisen, werden nicht sofort nach Ablauf eines Unter-Assets angezeigt. Stattdessen werden sie angezeigt, nachdem AEM Assets bei der nächsten Ausführung des Planers erkennt, dass sie auf abgelaufene Unter-Assets verweisen.

Wenn Sie das Ablaufdatum eines veröffentlichten Assets in ein Datum ändern, das vor dem aktuellen Planerzyklus liegt, erkennt der Planer das Asset als abgelaufenes Asset, wenn es das nächste Mal aufgeführt wird, und spiegelt dementsprechend seinen Status wider.

Wenn eine Störung oder ein Fehler verhindert, dass der Planer abgelaufene Assets im aktuellen Zyklus erkennt, untersucht der Planer diese Assets im nächsten Zyklus erneut und erkennt dann, dass sie abgelaufen sind.

Damit die Assets-Konsole die verknüpften Assets zusammen mit den abgelaufenen Teil-Assets anzeigen kann, konfigurieren Sie in AEM Configuration Manager einen Workflow für die **[!UICONTROL Benachrichtigung zum Ablauf von Adobe CQ-DAM]**.

1. Öffnen Sie AEM Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time based Scheduler]** is selected, which schedules a job to check at a specific time whether an asset has expired subassets. Nach Abschluss des Auftrags werden Assets mit abgelaufenen Unter-Assets und verwiesenen Assets in den Suchergebnissen als abgelaufen angezeigt.

1. Um den Auftrag regelmäßig auszuführen, löschen Sie das Feld **[!UICONTROL Zeitbasierte Planungsregel]** und ändern Sie die Zeit im Feld **[!UICONTROL Periodische Planung]** in Sekunden. Beispiel: Der Beispielausdruck „0 0 0 &amp;ast; &amp;ast; ?“ löst den Auftrag um 00 Uhr aus.
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

1. Tippen/Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Veröffentlichen]**. Wenn das Symbol **Veröffentlichen** in der Symbolleiste nicht angezeigt wird, tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Mehr]** und suchen Sie das Symbol **[!UICONTROL Veröffentlichen]**.

1. Choose **[!UICONTROL Publish]** from the menu, and then close the confirmation dialog.
1. Beenden Sie den Auswahlmodus. Der Veröffentlichungsstatus des Assets wird in der Kartenansicht im unteren Bereich der Miniaturansicht des Assets angezeigt. In der Listenansicht zeigt die Spalte „Veröffentlicht“ die Zeit an, zu der das Asset veröffentlicht wurde.

1. Wählen Sie in der Assets-Benutzeroberfläche ein Asset aus und tippen oder klicken Sie auf das Symbol **[!UICONTROL Eigenschaften]**, um die zugehörige Detailseite anzuzeigen.

1. In the Advanced tab, and set an expiration date for the asset from the **[!UICONTROL Expires]** field under.

1. Click **[!UICONTROL Save]** and then click **[!UICONTROL Close]** to display the Asset console.
1. Der Veröffentlichungsstatus des Assets weist in der Kartenansicht im unteren Bereich der Miniaturansicht darauf hin, dass das Asset abgelaufen ist. In the list view, the status of the asset is displayed as **[!UICONTROL Expired]**.

1. Wählen Sie in der Konsole „Assets“ einen Ordner aus und erstellen Sie eine Prüfungsaufgabe für den Ordner.
1. Review and approve/reject the assets in the review task and click **[!UICONTROL Complete]**.
1. Navigieren Sie zu dem Ordner, für den Sie die Prüfungsaufgabe erstellt haben. Der Status des Assets, das Sie bestätigt oder abgelehnt haben, wird unten in der Kartenansicht angezeigt. In der Ansicht &quot;Liste&quot;werden die Genehmigungs- und Ablaufstatus in den entsprechenden Spalten angezeigt.

1. To search for assets based on their status, click/tap the **[!UICONTROL Search]** icon to display the Omnisearch bar.

1. Drücken Sie die Eingabetaste und klicken Sie dann auf das AEM-Symbol bzw. tippen Sie darauf, um das Suchfeld anzuzeigen.
1. Tippen/Klicken Sie im Suchbedienfeld auf **[!UICONTROL Veröffentlichungsstatus]** und wählen Sie **[!UICONTROL Veröffentlicht]**, um in AEM Assets nach veröffentlichten Assets zu suchen.

1. Tippen/Klicken Sie auf **[!UICONTROL Genehmigungsstatus]** und dann auf die entsprechende Option, um nach genehmigten oder abgelehnten Assets zu suchen.

1. Um nach Assets basierend auf dem Ablaufstatus zu suchen, wählen Sie im Suchfeld die Option **[!UICONTROL Ablaufstatus]** und anschließend die entsprechende Option aus.

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
1. Wählen Sie auf der Seite **[!UICONTROL Copyright-Management]** das Asset aus, das Sie herunterladen möchten.
1. Wählen Sie im Lizenzfenster **[!UICONTROL Zustimmen]**. Möglicherweise erscheint ein Häkchen neben dem Asset, für das Sie die Lizenzvereinbarung angenommen haben. Tap/click the **[!UICONTROL Download]** button.

   >[!NOTE]
   >
   >Die Schaltfläche **[!UICONTROL Herunterladen]** ist nur aktiviert, wenn Sie der Lizenzvereinbarung für ein geschütztes Asset zustimmen. Wenn Ihre Auswahl jedoch sowohl geschützte als auch ungeschützte Assets umfasst, werden nur die geschützten Assets im linken Bereich aufgelistet und die Schaltfläche **[!UICONTROL Herunterladen]** ist aktiviert, um die ungeschützten Assets herunterzuladen. Um gleichzeitig Lizenzvereinbarungen für mehrere geschützte Assets zu akzeptieren, wählen Sie die Assets aus der Liste aus und dann **[!UICONTROL Zustimmen]**.

1. In the dialog, tap/click **[!UICONTROL Download]** to download the asset or its renditions.
