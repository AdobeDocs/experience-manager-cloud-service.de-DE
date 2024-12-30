---
title: Digital Rights Management in [!DNL Assets]
description: Erfahren Sie, wie Sie den Asset-Ablaufstatus und Informationen für lizenzierte Assets in [!DNL Experience Manager] as a [!DNL Cloud Service] verwalten.
contentOwner: AG
feature: Asset Management,DRM
role: User, Admin
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 100%

---

# Digital Rights Management für digitale Assets {#digital-rights-management-in-assets}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/drm.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Digitale Assets sind oftmals mit einer Lizenz verbunden, in der die Bedingungen und die Nutzungsdauer festgelegt sind. Wenn Sie die [!DNL Experience Manager]-Plattform nutzen, können Sie Informationen zum Ablauf von Assets und zur Lizenzierung effizient verwalten.

## Asset-Ablauf {#asset-expiration}

Um Lizenzanforderungen für Assets durchzusetzen, verwenden Sie Asset-Ablaufinformationen. Die Ablaufinformationen stellen sicher, dass die Veröffentlichung des veröffentlichten Assets bei Ablauf der Gültigkeit aufgehoben wird, was eine Lizenzverletzung verhindert. Ein Benutzer ohne Administratorrechte kann ein abgelaufenes Asset weder bearbeiten, kopieren, verschieben, veröffentlichen noch herunterladen.

Sie können den Ablaufstatus eines Assets an den folgenden Stellen einsehen:

* **Kartenansicht**: Ein abgelaufenes Asset ist entsprechend auf der Karte gekennzeichnet.
* **Listenansicht**: Für abgelaufene Assets zeigt die Spalte **[!UICONTROL Status]** das Banner **[!UICONTROL Abgelaufen]** an.
* **Zeitleiste**: Sie können den Ablaufstatus eines Assets in der Zeitleiste einsehen. Wählen Sie das Asset und anschließend „Zeitleiste“ aus.
* **Leiste „Verweise“**: Sie können außerdem den Ablaufstatus von Assets in der Leiste **[!UICONTROL Verweise]** einsehen. Hier werden der Asset-Ablaufstatus und die Beziehungen zwischen ebenenübergreifenden Assets und referenzierten Teil-Assets, Sammlungen und Projekten verwaltet.

Gehen Sie wie folgt vor, um referenzierende Webseiten und ebenenübergreifende Assets für ein Asset anzuzeigen:

1. Gehen Sie zum Asset, wählen Sie das Asset aus und klicken Sie auf das ![Symbol für Inhaltsreferenzen in der linken Leiste](assets/do-not-localize/content-rail-icon.png). Die linke Leiste wird geöffnet.
1. Wählen Sie aus der linken Leiste **[!UICONTROL Verweise]** aus.
1. Bei abgelaufenen Assets zeigt [!UICONTROL Verweise] den Ablaufstatus als **[!UICONTROL Asset ist abgelaufen]** an. Sofern das Asset abgelaufene Teil-Assets aufweist, zeigt die Leiste [!UICONTROL Verweise] den Status **[!UICONTROL Asset enthält abgelaufene Teil-Assets]** an.

### Suchen nach abgelaufenen Assets {#search-expired-assets}

Gehen Sie wie folgt vor, um nach einem abgelaufenen Asset, einschließlich abgelaufener Teil-Assets, zu suchen:

1. Klicken Sie in der [!DNL Assets]-Konsole in der Symbolleiste auf **[!UICONTROL Suche]** und drücken Sie `Enter`.

1. Klicken Sie auf das GlobalNav-Symbol und wählen Sie die Option **[!UICONTROL Gültigkeitsstatus]** aus.

1. Wählen Sie **[!UICONTROL Abgelaufen]** aus. Die Suchergebnisse zeigen die abgelaufenen Assets an.

Bei Auswahl der Option **[!UICONTROL Abgelaufen]** zeigt die [!DNL Assets]-Konsole nur die abgelaufenen Assets und Teil-Assets an, auf die von ebenenübergreifenden Assets verwiesen wird. Die ebenenübergreifenden Assets, die auf abgelaufene Teil-Assets verweisen, werden nicht sofort nach Ablauf eines Teil-Assets angezeigt. Stattdessen werden sie angezeigt, nachdem [!DNL Experience Manager] bei der nächsten Ausführung der Planung erkennt, dass sie auf abgelaufene Teil-Assets verweisen.

Es ist möglich, das Ablaufdatum eines veröffentlichten Assets in ein Datum vor dem aktuellen Planungszyklus zu ändern. Allerdings erkennt der Planer ein solches Asset weiterhin als abgelaufenes Asset, wenn er das nächste Mal ausgeführt wird, und [!DNL Experience Manager] spiegelt den Status in seinem Bericht wider. Das Ablaufdatum eines Assets wird für Benutzer in verschiedenen Zeitzonen unterschiedlich angezeigt.

Wenn ein Fehler verhindert, dass die Planung abgelaufene Assets im aktuellen Zyklus erkennt, untersucht die Planung diese Assets im nächsten Zyklus erneut und erkennt dann, dass sie abgelaufen sind.

Damit die [!DNL Assets]-Konsole die verweisenden ebenenübergreifenden Assets neben den abgelaufenen Teil-Assets anzeigt, konfigurieren Sie in [!DNL Experience Manager] einen Workflow für **[!UICONTROL Adobe CQ DAM-Ablaufbenachrichtigungen]**. Die zeitbasierte Planung plant einen Auftrag, um zu einem bestimmten Zeitpunkt zu überprüfen, ob ein Asset abgelaufene Teil-Assets aufweist. Nach Abschluss des Auftrags werden Assets mit abgelaufenen Teil-Assets und verwiesenen Assets in den Suchergebnissen als abgelaufen angezeigt.

1. Greifen Sie auf das [!DNL Cloud Manager]-Git-Repository zu, das Ihrer Umgebung zugeordnet ist.
1. Binden Sie eine Datei namens `com.day.cq.dam.core.impl.ExpiryNotificationJobImpl.cfg.json` im Repository mit folgendem Inhalt.

   ```json
   {
      "send_email":"false", "asset_expired_limit":"100", "prior_notification_seconds":"86400", "cq.dam.expiry.notification.url.protocol":"http", "cq.dam.expiry.notification.scheduler.istimebased":"true", "cq.dam.expiry.notification.scheduler.period.rule":"10", "cq.dam.expiry.notification.scheduler.timebased.rule":"0 0 0 * * ?"
   }
   ```

1. Weitere Informationen finden Sie unter [OSGi-Konfiguration in  [!DNL Experience Manager]  as a  [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md).

Sie können die Planung mit den folgenden Eigenschaften konfigurieren:

* Ein `true`-Wert der Eigenschaft `cq.dam.expiry.notification.scheduler.istimebased` initiiert die Planung. * Der Wert der Eigenschaft `cq.dam.expiry.notification.scheduler.timebased.rule` ist der reguläre Ausdruck, um die Zeit zu definieren. Im obigen Beispiel wird der Planungsauftrag um 00 Uhr gestartet.
* Wenn `send_email` auf `true` gesetzt ist, erhält der Ersteller des Assets (die Person, die ein bestimmtes Asset auf [!DNL Assets] hochlädt) eine E-Mail, wenn das Asset abläuft.
* Die maximale Anzahl von abgelaufenen Assets in einer Iteration der Planung ist der Wert der Eigenschaft `asset_expired_limit`.
* Um den Auftrag regelmäßig auszuführen, setzen Sie den Wert der Eigenschaft `cq.dam.expiry.notification.scheduler.istimebased` auf `false` und setzen den Wert der Eigenschaft `cq.dam.expiry.notification.scheduler.period.rule` auf die Zeit in Sekunden.

<!-- TBD: Web Console not available in CS.

1. Open [!DNL Experience Manager] Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time-based Scheduler]** is selected, which 

1. For example, the example expression '0 0 0 &ast; &ast; ?' triggers the job at 0000 hrs.

1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

1. In the **[!UICONTROL Prior notification in seconds]** field, specify the time in seconds before the asset expiry when you want to receive a notification. If you are an administrator or the asset creator, you receive a message before the expiration of the asset. After the asset expiry, you receive another notification that confirms the expiration. In addition, the expired asset is deactivated.

1. Select **[!UICONTROL Save]**.
-->

## Asset-Status {#asset-states}

Die [!DNL Assets]-Konsole kann verschiedene Status für Assets anzeigen. Abhängig vom aktuellen Status eines bestimmten Assets zeigt die zugehörige Kartenansicht eine Beschreibung des Zustands an, z. B. „Abgelaufen“, „Veröffentlicht“, „Genehmigt“, „Abgelehnt“ usw.

1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche ein Asset aus.

1. Wählen Sie **[!UICONTROL Veröffentlichen]** aus der Symbolleiste aus. Falls Sie das Symbol [!UICONTROL Veröffentlichen] in der Symbolleiste nicht sehen, klicken Sie dort auf **[!UICONTROL Mehr]** und suchen Sie nach der Option **[!UICONTROL Veröffentlichen]**.

1. Wählen Sie im Menü **[!UICONTROL Veröffentlichen]** aus und schließen Sie danach das Bestätigungsdialogfeld.

1. Beenden Sie den Auswahlmodus. Der Veröffentlichungsstatus des Assets wird in der Kartenansicht im unteren Bereich der Miniatur des Assets angezeigt. In der Listenansicht zeigt die Spalte „Veröffentlicht“ die Zeit an, zu der das Asset veröffentlicht wurde.

1. Um die Seite mit den Asset-Details anzuzeigen, wählen Sie in der [!DNL Assets]-Benutzeroberfläche ein Asset aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.

1. Geben Sie auf der Registerkarte [!UICONTROL Erweitert] ein Ablaufdatum für das Asset im Feld **[!UICONTROL Ablaufdatum]** an.

1. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL Schließen]**, um die Asset-Konsole anzuzeigen.

1. Der Veröffentlichungsstatus des Assets weist in der Kartenansicht im unteren Bereich der Miniatur darauf hin, dass das Asset abgelaufen ist. In der Listenansicht wird der Status des Assets als **[!UICONTROL Abgelaufen]** angegeben.

1. Wählen Sie in der [!DNL Assets]-Konsole einen Ordner aus und erstellen Sie eine Prüfungsaufgabe für den Ordner.

1. Prüfen und bestätigen Sie das Asset in der Prüfungsaufgabe (bzw. lehnen Sie es ab) und klicken Sie auf **[!UICONTROL Fertig]**.

1. Navigieren Sie zu dem Ordner, für den Sie die Prüfungsaufgabe erstellt haben. Der Status des Assets, das Sie bestätigt oder abgelehnt haben, wird unten in der Kartenansicht angezeigt. In der Listenansicht werden Bestätigungs- und Ablaufstatus in entsprechenden Spalten angezeigt.

1. Um nach Assets auf Grundlage ihres Status zu suchen, klicken Sie auf **[!UICONTROL Suchen]**, um die Sucheiste anzuzeigen.

1. Wählen Sie `Return` aus und klicken Sie auf [!DNL Experience Manager].

1. Klicken Sie im Suchbedienfeld auf **[!UICONTROL Veröffentlichungsstatus]** und wählen Sie **[!UICONTROL Veröffentlicht]** aus, um in [!DNL Assets] nach veröffentlichten Assets zu suchen.

1. Um nach genehmigten oder abgelehnten Assets zu suchen, wählen Sie **[!UICONTROL Genehmigungsstatus]** aus und wählen Sie die entsprechende Option aus.

1. Um nach Assets auf Grundlage ihres Ablaufstatus zu suchen, wählen Sie im Suchfeld **[!UICONTROL Gültigkeitsstatus]** und danach die entsprechende Option aus.

1. Sie können auch auf Grundlage einer Kombination von Statusangaben mit verschiedenen Suchfacetten nach Assets suchen. Sie können beispielsweise nach veröffentlichten Assets suchen, die in einer Prüfungsaufgabe genehmigt wurden und nicht abgelaufen sind. Um nach solchen Assets zu suchen, wählen Sie die entsprechenden Optionen in den Suchfacetten aus.

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

Die DRM-Funktion setzt die Annahme der Lizenzvereinbarung zwingend voraus. Erst nach diesem Schritt können lizenzierte Assets von [!DNL Assets] heruntergeladen werden.

Wenn Sie ein geschütztes Asset auswählen und auf **[!UICONTROL Herunterladen]** klicken, werden Sie auf die Lizenzseite weitergeleitet, um die Lizenzvereinbarung anzunehmen. Wenn Sie die Lizenzvereinbarung nicht annehmen, steht die Option **[!UICONTROL Herunterladen]** nicht zur Verfügung.

Falls die Auswahl mehrere geschützte Assets enthält, wählen Sie jeweils eines aus, nehmen Sie die Lizenzvereinbarung an und fahren Sie mit dem Herunterladen des Assets fort.

Ein Asset gilt als geschützt, wenn eine der folgenden Bedingungen erfüllt ist:

* Die `xmpRights:WebStatement`-Metadateneigenschaft des Assets verweist auf den Pfad der Seite, die die Lizenzvereinbarung für das Asset enthält.
* Beim Wert der `adobe_dam:restrictions`-Metadateneigenschaft des Assets handelt es sich um unformatierten HTML-Code, der die Lizenzvereinbarung angibt.

>[!NOTE]
>
>Der Speicherort `/etc/dam/drm/licences` wurde verwendet, um Lizenzen in früheren Versionen von [!DNL Experience Manager] zu speichern. Dieser Speicherort wird jetzt nicht mehr unterstützt. Wenn Sie Lizenzseiten erstellen oder ändern oder die Seiten aus früheren [!DNL Experience Manager] -Versionen verwenden, empfiehlt Adobe, diese Assets unter den Speicherorten `/apps/settings/dam/drm/licenses` oder `/conf/*/settings/dam/drm/licenses` zu speichern.

### Herunterladen von DRM-geschützten Assets {#downloading-drm-assets}

1. Wählen Sie die gewünschten Assets in der Kartenansicht aus und klicken Sie auf **[!UICONTROL Herunterladen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Copyright-Management]** das Asset aus, das Sie herunterladen möchten.
1. Wählen Sie im [!UICONTROL Lizenzfenster] die Option **[!UICONTROL Zustimmen]** aus. Neben dem Asset erscheint ein Häkchen. Wählen Sie die Option **[!UICONTROL Herunterladen]** aus.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Herunterladen]** ist nur dann verfügbar, wenn Sie der Lizenzvereinbarung für ein geschütztes Asset zustimmen. Wenn Ihre Auswahl jedoch sowohl geschützte als auch ungeschützte Assets umfasst, werden nur die geschützten Assets im Bereich aufgelistet und die Option **[!UICONTROL Herunterladen]** ist aktiviert, um die ungeschützten Assets herunterzuladen. Sie können mehrere Lizenzvereinbarungen für verschiedene geschützte Assets gleichzeitig akzeptieren, indem Sie die Assets in der Liste auswählen und anschließend auf **[!UICONTROL Zustimmen]** klicken.

1. Um das Asset oder seine Ausgabedarstellungen herunterzuladen, wählen Sie im Dialogfeld die Option **[!UICONTROL Herunterladen]** aus.

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
