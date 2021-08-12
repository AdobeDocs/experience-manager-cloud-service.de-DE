---
title: Digital Rights Management in [!DNL Assets]
description: Erfahren Sie, wie Sie den Asset-Ablaufstatus und Informationen für lizenzierte Assets in [!DNL Experience Manager] as a [!DNL Cloud Service] verwalten.
contentOwner: AG
feature: Asset-Management,DRM
role: User,Admin
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
source-git-commit: f993148a9f678cfdaf0693e4964f02b9163cf2ff
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 49%

---

# Digital Rights Management für digitale Assets {#digital-rights-management-in-assets}

Digitale Assets sind häufig mit einer Lizenz verknüpft, in der die Nutzungsbedingungen und die Nutzungsdauer angegeben sind. Mit der Plattform [!DNL Experience Manager] können Sie Asset-Ablaufinformationen und Lizenzinformationen effizient verwalten.

## Asset-Ablauf {#asset-expiration}

Verwenden Sie zum Erzwingen von Lizenzanforderungen für Assets Asset-Ablaufinformationen. Die Ablaufinformationen stellen sicher, dass die Veröffentlichung des veröffentlichten Assets bei Ablauf der Gültigkeit aufgehoben wird, was eine Lizenzverletzung verhindert. Ein Benutzer ohne Administratorrechte kann ein abgelaufenes Asset weder bearbeiten, kopieren, verschieben, veröffentlichen noch herunterladen.

Sie können den Ablaufstatus eines Assets an den folgenden Stellen einsehen:

* **Kartenansicht**: Ein abgelaufenes Asset ist entsprechend auf der Karte gekennzeichnet.
* **Listenansicht**: Bei einem abgelaufenen Asset zeigt die  **** Spalte Status das  **** Abgelaufene Banner an.
* **Zeitleiste**: Sie können den Ablaufstatus eines Assets in der Zeitleiste einsehen. Wählen Sie das Asset und anschließend „Zeitleiste“ aus.
* **Leiste „Verweise“**: Sie können außerdem den Ablaufstatus von Assets in der Leiste **[!UICONTROL Verweise]** einsehen. Hier werden der Asset-Ablaufstatus und die Beziehungen zwischen ebenenübergreifenden Assets und referenzierten Teil-Assets, Sammlungen und Projekten verwaltet.

Gehen Sie wie folgt vor, um referenzierende Webseiten und ebenenübergreifende Assets für ein Asset anzuzeigen:

1. Navigieren Sie zum Asset, wählen Sie das Asset aus und klicken Sie auf das Symbol ![Inhaltsreferenzen in der linken Leiste](assets/do-not-localize/content-rail-icon.png). Die linke Leiste wird geöffnet.
1. Wählen Sie in der linken Leiste **[!UICONTROL Verweise]** aus.
1. Bei abgelaufenen Assets zeigt [!UICONTROL Verweise] den Ablaufstatus als **[!UICONTROL Asset ist abgelaufen]** an. Wenn das Asset abgelaufene Teil-Assets aufweist, zeigt die Leiste [!UICONTROL Verweise] den Status **[!UICONTROL Asset hat abgelaufene Unter-Assets]** an.

### Suchen nach abgelaufenen Assets {#search-expired-assets}

Gehen Sie wie folgt vor, um nach einem abgelaufenen Asset, einschließlich abgelaufener Teil-Assets, zu suchen:

1. Klicken Sie in der [!DNL Assets]-Konsole in der Symbolleiste auf **[!UICONTROL Suchen]** und drücken Sie `Enter`.

1. Klicken Sie auf das GlobalNav-Symbol und wählen Sie die Option **[!UICONTROL Ablaufstatus]** aus.

1. Wählen Sie **[!UICONTROL Abgelaufen]** aus. Die Suchergebnisse zeigen die abgelaufenen Assets an.

Bei Auswahl der Option **[!UICONTROL Abgelaufen]** zeigt die [!DNL Assets]-Konsole nur die abgelaufenen Assets und Teil-Assets an, auf die von ebenenübergreifenden Assets verwiesen wird. Die ebenenübergreifenden Assets, die auf abgelaufene Teil-Assets verweisen, werden nicht sofort nach Ablauf eines Teil-Assets angezeigt. Stattdessen werden sie angezeigt, nachdem [!DNL Experience Manager] erkennt, dass sie beim nächsten Ausführen der Planung auf abgelaufene Teil-Assets verweisen.

Es ist möglich, das Ablaufdatum eines veröffentlichten Assets in ein Datum vor dem aktuellen Planungszyklus zu ändern. Allerdings erkennt der Zeitplan ein solches Asset weiterhin als abgelaufenes Asset, wenn es das nächste Mal ausgeführt wird, und [!DNL Experience Manager] spiegelt den Status in seinem Bericht wider. Das Ablaufdatum eines Assets wird für Benutzer in verschiedenen Zeitzonen unterschiedlich angezeigt.

Wenn außerdem ein Fehler verhindert, dass die Planung abgelaufene Assets im aktuellen Zyklus erkennt, überprüft die Planung diese Assets im nächsten Zyklus erneut und erkennt deren abgelaufenen Status.

Damit die Konsole [!DNL Assets] die verweisenden ebenenübergreifenden Assets zusammen mit den abgelaufenen Teil-Assets anzeigt, konfigurieren Sie den Workflow **[!UICONTROL Adobe CQ DAM-Ablaufbenachrichtigung]** in [!DNL Experience Manager]. Der zeitbasierte Planer plant einen Auftrag, um zu einem bestimmten Zeitpunkt zu überprüfen, ob ein Asset abgelaufene Teil-Assets aufweist. Nach Abschluss des Auftrags werden Assets mit abgelaufenen Teil-Assets und verwiesenen Assets in den Suchergebnissen als abgelaufen angezeigt.

1. Greifen Sie auf das [!DNL Cloud Manager]-Git-Repository zu, das Ihrer Umgebung zugeordnet ist.
1. Binden Sie eine Datei namens `com.day.cq.dam.core.impl.ExpiryNotificationJobImpl.cfg.json` im Repository mit folgendem Inhalt.

   ```json
   {
      "send_email":"false", "asset_expired_limit":"100", "prior_notification_seconds":"86400", "cq.dam.expiry.notification.url.protocol":"http", "cq.dam.expiry.notification.scheduler.istimebased":"true", "cq.dam.expiry.notification.scheduler.period.rule":"10", "cq.dam.expiry.notification.scheduler.timebased.rule":"0 0 0 * * ?"
   }
   ```

1. Befolgen Sie die Anweisungen von [wie Sie die OSGi-Konfiguration in [!DNL Experience Manager] als a [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md) durchführen.

Sie können den Planer mit den folgenden Eigenschaften konfigurieren:

* Ein `true` -Wert der Eigenschaft `cq.dam.expiry.notification.scheduler.istimebased` initiiert die Planung. * Der Wert der Eigenschaft `cq.dam.expiry.notification.scheduler.timebased.rule` ist der reguläre Ausdruck zur Definition der Zeit. Im obigen Beispiel wird der Planungsauftrag um 00 Stunden initiiert.
* Wenn `send_email` auf `true` gesetzt ist, erhält der Asset-Ersteller (die Person, die ein bestimmtes Asset auf [!DNL Assets] hochlädt) eine E-Mail, wenn das Asset abläuft.
* Die maximale Anzahl von Assets, die in einer Iteration der Planung abgelaufen sind, ist der Wert der Eigenschaft `asset_expired_limit`.
* Um den Auftrag regelmäßig auszuführen, setzen Sie den Wert der Eigenschaft `cq.dam.expiry.notification.scheduler.istimebased` auf `false` und legen Sie den Wert der Eigenschaft `cq.dam.expiry.notification.scheduler.period.rule` mit der Zeit in Sekunden fest.

<!-- TBD: Web Console not available in CS.

1. Open [!DNL Experience Manager] Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time-based Scheduler]** is selected, which 

1.  For example, the example expression '0 0 0 &ast; &ast; ?' triggers the job at 0000 hrs.

1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

1. In the **[!UICONTROL Prior notification in seconds]** field, specify the time in seconds before the asset expiry when you want to receive a notification. If you are an administrator or the asset creator, you receive a message before the expiration of the asset. After the asset expiry, you receive another notification that confirms the expiration. In addition, the expired asset is deactivated.

1. Select **[!UICONTROL Save]**.
-->

## Asset-Status {#asset-states}

Die [!DNL Assets]-Konsole kann verschiedene Status für Assets anzeigen. Abhängig vom aktuellen Status eines bestimmten Assets zeigt die zugehörige Kartenansicht eine Beschreibung des Zustands an, z. B. „Abgelaufen“, „Veröffentlicht“, „Genehmigt“, „Abgelehnt“ usw.

1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche ein Asset aus.

1. Wählen Sie **[!UICONTROL Publish]** aus der Symbolleiste aus. Wenn die Option [!UICONTROL Publish] in der Symbolleiste nicht angezeigt wird, klicken Sie in der Symbolleiste auf **[!UICONTROL Mehr]** und suchen Sie nach der Option **[!UICONTROL Publish]** .

1. Wählen Sie im Menü **[!UICONTROL Veröffentlichen]** aus und schließen Sie danach das Bestätigungsdialogfeld.

1. Beenden Sie den Auswahlmodus. Der Veröffentlichungsstatus des Assets wird in der Kartenansicht im unteren Bereich der Miniaturansicht des Assets angezeigt. In der Listenansicht zeigt die Spalte „Veröffentlicht“ die Zeit an, zu der das Asset veröffentlicht wurde.

1. Um die Seite mit den Asset-Details anzuzeigen, wählen Sie in der [!DNL Assets]-Benutzeroberfläche ein Asset aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.

1. Geben Sie auf der Registerkarte [!UICONTROL Erweitert] ein Ablaufdatum für das Asset im Feld **[!UICONTROL Ablaufdatum]** an.

1. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL Schließen]**, um die Asset-Konsole anzuzeigen.

1. Der Veröffentlichungsstatus des Assets weist in der Kartenansicht im unteren Bereich der Miniaturansicht darauf hin, dass das Asset abgelaufen ist. In der Listenansicht wird der Status des Assets als **[!UICONTROL Abgelaufen]** angegeben.

1. Wählen Sie in der [!DNL Assets]-Konsole einen Ordner aus und erstellen Sie eine Prüfungsaufgabe für den Ordner.

1. Prüfen und bestätigen Sie das Asset in der Prüfungsaufgabe (bzw. lehnen Sie es ab) und klicken Sie auf **[!UICONTROL Fertig]**.

1. Navigieren Sie zu dem Ordner, für den Sie die Prüfungsaufgabe erstellt haben. Der Status des Assets, das Sie bestätigt oder abgelehnt haben, wird unten in der Kartenansicht angezeigt. In der Listenansicht werden Bestätigungs- und Ablaufstatus in entsprechenden Spalten angezeigt.

1. Um nach Assets basierend auf ihrem Status zu suchen, klicken Sie auf **[!UICONTROL Suchen]** , um die Suchleiste anzuzeigen.

1. Wählen Sie `Return` und klicken Sie auf [!DNL Experience Manager].

1. Klicken Sie im Suchbedienfeld auf **[!UICONTROL Veröffentlichungsstatus]** und wählen Sie **[!UICONTROL Veröffentlicht]** aus, um in [!DNL Assets] nach veröffentlichten Assets zu suchen.

1. Um nach genehmigten oder abgelehnten Assets zu suchen, wählen Sie **[!UICONTROL Genehmigungsstatus]** und danach die entsprechende Option aus.

1. Um nach Assets basierend auf ihrem Ablaufstatus zu suchen, wählen Sie **[!UICONTROL Ablaufstatus]** im Suchfeld und wählen Sie die entsprechende Option aus.

1. Sie können auch auf Grundlage einer Kombination von Statusangaben mit verschiedenen Suchfacetten nach Assets suchen. Sie können beispielsweise nach veröffentlichten Assets suchen, die in einer Prüfungsaufgabe genehmigt wurden und nicht abgelaufen sind. Um nach solchen Assets zu suchen, wählen Sie die entsprechenden Optionen in den Suchfacetten aus.

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

Die DRM-Funktion erzwingt die Annahme der Lizenzvereinbarung, bevor Sie ein lizenziertes Asset von [!DNL Assets] herunterladen können.

Wenn Sie ein geschütztes Asset auswählen und auf **[!UICONTROL Herunterladen]** klicken, werden Sie auf die Lizenzseite weitergeleitet, um die Lizenzvereinbarung anzunehmen. Wenn Sie die Lizenzvereinbarung nicht annehmen, steht die Option **[!UICONTROL Herunterladen]** nicht zur Verfügung.

Falls die Auswahl mehrere geschützte Assets enthält, wählen Sie jeweils eines aus, nehmen Sie die Lizenzvereinbarung an und fahren Sie mit dem Herunterladen des Assets fort.

Ein Asset gilt als geschützt, wenn eine der folgenden Bedingungen erfüllt ist:

* Die `xmpRights:WebStatement`-Metadateneigenschaft des Assets verweist auf den Pfad der Seite, die die Lizenzvereinbarung für das Asset enthält.
* Beim Wert der `adobe_dam:restrictions`-Metadateneigenschaft des Assets handelt es sich um unformatierten HTML-Code, der die Lizenzvereinbarung angibt.

>[!NOTE]
>
>Der Speicherort `/etc/dam/drm/licences` wurde verwendet, um Lizenzen in früheren Versionen von [!DNL Experience Manager] zu speichern. Der Standort wird jetzt nicht mehr unterstützt. Wenn Sie Lizenzseiten erstellen oder ändern oder die Seiten aus früheren [!DNL Experience Manager]-Versionen portieren, empfiehlt Adobe, diese Assets an `/apps/settings/dam/drm/licenses`- oder `/conf/*/settings/dam/drm/licenses`-Speicherorten zu speichern.

### Herunterladen von DRM-geschützten Assets {#downloading-drm-assets}

1. Wählen Sie in der Kartenansicht die Assets aus, die Sie herunterladen möchten, und wählen Sie **[!UICONTROL Download]** aus.
1. Wählen Sie auf der Seite **[!UICONTROL Copyright-Management]** das Asset aus, das Sie herunterladen möchten.
1. Wählen Sie im [!UICONTROL Lizenzfenster] die Option **[!UICONTROL Zustimmen]** aus. Neben dem Asset erscheint ein Häkchen. Wählen Sie die Option **[!UICONTROL Download]** aus.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Herunterladen]** ist nur dann verfügbar, wenn Sie der Lizenzvereinbarung für ein geschütztes Asset zustimmen. Wenn Ihre Auswahl jedoch sowohl geschützte als auch ungeschützte Assets umfasst, werden nur die geschützten Assets im Bereich aufgelistet und die Option **[!UICONTROL Download]** steht zum Herunterladen der ungeschützten Assets zur Verfügung. Sie können mehrere Lizenzvereinbarungen für verschiedene geschützte Assets gleichzeitig akzeptieren, indem Sie die Assets in der Liste auswählen und anschließend auf **[!UICONTROL Zustimmen]** klicken.

1. Um das Asset oder seine Ausgabeformate herunterzuladen, wählen Sie **[!UICONTROL Download]** im Dialogfeld aus.
