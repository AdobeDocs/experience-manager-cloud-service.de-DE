---
title: Digital Rights Management in Adobe Experience Manager Assets
description: Erfahren Sie, wie Sie den Asset-Ablaufstatus und Informationen für lizenzierte Assets in AEM verwalten.
contentOwner: AG
translation-type: ht
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Digital Rights Management in Experience Manager Assets {#digital-rights-management-in-assets}

Digitale Assets sind oftmals mit einer Lizenz verbunden, in der die Bedingungen und die Nutzungsdauer festgelegt sind. Da Adobe Experience Manager (AEM) Assets vollständig mit der AEM-Plattform integriert ist, können Sie Asset-Ablaufinformationen und -Status effizient verwalten. Sie können Lizenzinformationen mit Assets verknüpfen.

## Asset-Ablauf {#asset-expiration}

Der Asset-Ablauf ist eine effektive Möglichkeit zum Durchsetzen von Lizenzanforderungen für Assets. Wenn ein veröffentlichtes Asset abläuft, wird seine Veröffentlichung aufgehoben und damit die Möglichkeit einer Lizenzverletzung unterbunden. Ein Benutzer ohne Administratorrechte kann ein abgelaufenes Asset weder bearbeiten, kopieren, verschieben, veröffentlichen noch herunterladen.

Sie können den Ablaufstatus eines Assets an den folgenden Stellen einsehen:

* **Kartenansicht**: Ein abgelaufenes Asset ist entsprechend auf der Karte gekennzeichnet.
* **Listenansicht**: Für abgelaufene Assets zeigt die Spalte **[!UICONTROL Status]** das Banner **[!UICONTROL Abgelaufen]** an.
* **Timeline**: Sie können den Ablaufstatus eines Assets in der Timeline einsehen. Wählen Sie das Asset und anschließend „Timeline“ aus.
* **Leiste „Verweise“**: Sie können außerdem den Ablaufstatus von Assets in der Leiste **[!UICONTROL Verweise]** einsehen. Hier werden der Asset-Ablaufstatus und die Beziehungen zwischen ebenenübergreifenden Assets und referenzierten Teil-Assets, Sammlungen und Projekten verwaltet.

1. Navigieren Sie zu dem Asset, für das Sie referenzierende Web-Seiten und ebenenübergreifende Assets anzeigen möchten.
1. Wählen Sie das Asset aus und klicken/tippen Sie auf das globale Navigationssymbol.
1. Wählen Sie im Menü **[!UICONTROL Verweise]** aus.
1. Für abgelaufene Assets zeigt die Leiste „Verweise“ im oberen Bereich den Ablaufstatus **[!UICONTROL Asset ist abgelaufen]** an. Sofern das Asset abgelaufene Teil-Assets aufweist, zeigt die Leiste „Verweise“ den Status **[!UICONTROL Asset enthält abgelaufene Teil-Assets]** an.

### Suchen nach abgelaufenen Assets {#search-expired-assets}

Sie können im Suchfeld nach abgelaufenen Assets einschließlich abgelaufener Teil-Assets suchen.

1. Klicken Sie in der Konsole „Assets“ auf das Suchsymbol in der Symbolleiste, um das Omnisearch-Feld anzuzeigen.

1. Betätigen Sie bei in das Omnisearch-Feld gesetztem Cursor die Eingabetaste, um die Seite mit den Suchergebnissen anzuzeigen.

1. Klicken Sie auf das GlobalNav-Symbol, um das Suchfeld anzuzeigen.

1. Klicken Sie auf die Option **[!UICONTROL Ablaufstatus]**, um sie zu erweitern.

1. Wählen Sie **[!UICONTROL Abgelaufen]** aus. Die abgelaufenen Assets werden in den Suchergebnissen angezeigt.

Bei Auswahl der Option **[!UICONTROL Abgelaufen]** zeigt die Konsole „Assets“ nur die abgelaufenen Assets und Teil-Assets an, auf die von ebenenübergreifenden Assets verwiesen wird. Die ebenenübergreifenden Assets, die auf abgelaufene Unter-Assets verweisen, werden nicht sofort nach Ablauf eines Unter-Assets angezeigt. Stattdessen werden sie angezeigt, nachdem AEM Assets bei der nächsten Ausführung des Planers erkennt, dass sie auf abgelaufene Unter-Assets verweisen.

Wenn Sie das Ablaufdatum eines veröffentlichten Assets in ein Datum ändern, das vor dem aktuellen Planerzyklus liegt, erkennt der Planer das Asset als abgelaufenes Asset, wenn es das nächste Mal aufgeführt wird, und spiegelt dementsprechend seinen Status wider.

Wenn eine Störung oder ein Fehler verhindert, dass der Planer abgelaufene Assets im aktuellen Zyklus erkennt, untersucht der Planer diese Assets im nächsten Zyklus erneut und erkennt dann, dass sie abgelaufen sind.

Damit die Konsole „Assets“ die verweisenden ebenenübergreifenden Assets neben den abgelaufenen Teil-Assets anzeigt, konfigurieren Sie in AEM Configuration Manager einen Workflow für **[!UICONTROL Adobe CQ DAM-Ablaufbenachrichtigungen]**.

1. Öffnen Sie AEM Configuration Manager.
1. Wählen Sie **[!UICONTROL Adobe CQ DAM-Ablaufbenachrichtigung]** aus. Standardmäßig wird **[!UICONTROL Zeitbasierter Planer]** ausgewählt, womit ein Auftrag geplant wird, der zu einem bestimmten Zeitpunkt prüft, ob ein Asset abgelaufene Teil-Assets aufweist. Nach Abschluss des Auftrags werden Assets mit abgelaufenen Teil-Assets und verwiesenen Assets in den Suchergebnissen als abgelaufen angezeigt.

1. Um den Auftrag regelmäßig auszuführen, löschen Sie das Feld **[!UICONTROL Regel für zeitbasierten Planer]** und ändern Sie die Dauer in Sekunden im Feld **[!UICONTROL Periodischer Planer]**. Beispiel: Der Beispielausdruck „0 0 0 &amp;ast; &amp;ast; ?“ löst den Auftrag um 00:00 Uhr aus.

<!-- 1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

   >[!NOTE]
   >
   >Only the asset creator (the person who uploads a particular asset to AEM Assets) receives an email when the asset expires. See how to configure email notification for additional details around configuring email notifications at the overall AEM level.
-->

1. Geben Sie im Feld **[!UICONTROL Vorabbenachrichtigung in Sekunden]** den Zeitpunkt in Sekunden vor dem Ablauf eines Assets an, zu dem Sie über den bevorstehenden Ablauf benachrichtigt werden möchten. Wenn Sie ein Administrator oder der Ersteller des Assets sind, werden Sie vor Ablauf des Assets darüber informiert, dass das Asset nach dem angegebenen Zeitraum ablaufen wird.

   Nachdem das Asset abgelaufen ist, erhalten Sie eine weitere Benachrichtigung, die den Ablauf bestätigt. Außerdem werden die abgelaufenen Assets deaktiviert.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Asset-Zustände {#asset-states}

Die Konsole „Assets“ in Adobe Experience Manager (AEM) Assets kann verschiedene Zustände für Assets anzeigen. Abhängig vom aktuellen Zustand eines bestimmten Assets zeigt die zugehörige Kartenansicht eine Beschreibung des Zustands an, z. B. „Abgelaufen“, „Veröffentlicht“, „Genehmigt“, „Abgelehnt“ usw.

1. Wählen Sie in der Assets-Benutzeroberfläche ein Asset aus.

1. Tippen/klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Veröffentlichen]**. Falls Sie das Symbol **Veröffentlichen** in der Symbolleiste nicht sehen, tippen oder klicken Sie dort auf **[!UICONTROL Mehr]** und suchen Sie das Symbol **[!UICONTROL Veröffentlichen]**.

1. Wählen Sie im Menü **[!UICONTROL Veröffentlichen]** aus und schließen Sie danach das Bestätigungsdialogfeld.
1. Beenden Sie den Auswahlmodus. Der Veröffentlichungsstatus des Assets wird in der Kartenansicht im unteren Bereich der Miniaturansicht des Assets angezeigt. In der Listenansicht zeigt die Spalte „Veröffentlicht“ die Zeit an, zu der das Asset veröffentlicht wurde.

1. Wählen Sie in der Assets-Benutzeroberfläche ein Asset aus und tippen oder klicken Sie auf das Symbol **[!UICONTROL Eigenschaften]**, um die zugehörige Detailseite anzuzeigen.

1. Geben Sie auf der Registerkarte „Erweitert“ ein Ablaufdatum für das Asset im Feld **[!UICONTROL Ablaufdatum]** an.

1. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL Schließen]**, um die Konsole „Assets“ anzuzeigen.
1. Der Veröffentlichungsstatus des Assets weist in der Kartenansicht im unteren Bereich der Miniaturansicht darauf hin, dass das Asset abgelaufen ist. In der Listenansicht wird der Status des Assets als **[!UICONTROL Abgelaufen]** angegeben.

1. Wählen Sie in der Konsole „Assets“ einen Ordner aus und erstellen Sie eine Prüfungsaufgabe für den Ordner.
1. Prüfen und bestätigen Sie das Asset in der Prüfungsaufgabe (bzw. lehnen Sie es ab) und klicken Sie auf **[!UICONTROL Fertig]**.
1. Navigieren Sie zu dem Ordner, für den Sie die Prüfungsaufgabe erstellt haben. Der Status des Assets, das Sie bestätigt oder abgelehnt haben, wird unten in der Kartenansicht angezeigt. In der Listenansicht werden Bestätigungs- und Ablaufstatus in entsprechenden Spalten angezeigt.

1. Um nach Assets auf Grundlage ihres Status zu suchen, klicken/tippen Sie auf das Symbol **[!UICONTROL Suchen]**, um die Omni-Suchleiste anzuzeigen.

1. Drücken Sie die Eingabetaste und klicken/tippen Sie anschließend auf das AEM-Symbol, um das Suchbedienfeld anzuzeigen.
1. Tippen oder klicken Sie im Suchfeld auf **[!UICONTROL Veröffentlichungsstatus]** und wählen Sie **[!UICONTROL Veröffentlicht]** aus, um in AEM Assets nach veröffentlichten Assets zu suchen.

1. Tippen oder klicken Sie auf **[!UICONTROL Genehmigungsstatus]** und danach auf die entsprechende Option, um nach bestätigten oder abgelehnten Assets zu suchen.

1. Um nach Assets auf Grundlage ihres Ablaufstatus zu suchen, wählen Sie im Suchfeld **[!UICONTROL Gültigkeitsstatus]** und danach die entsprechende Option aus.

1. Sie können auch auf Grundlage einer Kombination von Statusangaben mit verschiedenen Suchfacetten nach Assets suchen. Sie können beispielsweise nach veröffentlichten Assets suchen, die in einer Prüfungsaufgabe bestätigt wurden und noch nicht abgelaufen sind, indem Sie die entsprechenden Optionen in den Suchfacetten auswählen.

## Digital Rights Management in Experience Manager Assets {#digital-rights-management-in-assets-1}

Diese Funktion setzt die Annahme der Lizenzvereinbarung zwingend voraus. Erst nach diesem Schritt können lizenzierte Assets von Adobe Experience Manager (AEM) Assets heruntergeladen werden.

Wenn Sie ein geschütztes Asset auswählen und auf das Symbol **[!UICONTROL Herunterladen]** klicken, werden Sie auf die Lizenzseite weitergeleitet, auf der Sie die Lizenzvereinbarung annehmen können. Wenn Sie die Lizenzvereinbarung nicht annehmen, wird die Schaltfläche **[!UICONTROL Herunterladen]** deaktiviert.

Falls die Auswahl mehrere geschützte Assets enthält, wählen Sie jeweils eines aus, nehmen Sie die Lizenzvereinbarung an und fahren Sie mit dem Herunterladen des Assets fort.

Ein Asset gilt als geschützt, wenn eine der folgenden Bedingungen erfüllt ist:

* Die `xmpRights:WebStatement`-Metadateneigenschaft des Assets verweist auf den Pfad der CQ-Seite, die die Lizenzvereinbarung für das Asset enthält.
* Beim Wert der `adobe_dam:restrictions`-Metadateneigenschaft des Assets handelt es sich um nicht formatierten HTML-Code, der die Lizenzvereinbarung angibt.

>[!NOTE]
>
>Der Speicherort `/etc/dam/drm/licences`, der in den früheren Versionen von AEM zum Speichern von Lizenzen verwendet wurde, wird nicht mehr unterstützt.
>
>Wenn Sie Lizenzseiten erstellen, ändern oder aus früheren AEM-Versionen importieren, empfiehlt Adobe, die Seiten unter `/apps/settings/dam/drm/licenses` oder `/conf/*/settings/dam/drm/licenses` zu speichern.

### Herunterladen von DRM-Assets {#downloading-drm-assets}

1. Wählen Sie die gewünschten Assets in der Kartenansicht aus und klicken Sie auf das Symbol **[!UICONTROL Herunterladen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Copyright-Management]** das Asset aus, das Sie herunterladen möchten.
1. Wählen Sie im Lizenzfenster **[!UICONTROL Zustimmen]**. Möglicherweise erscheint ein Häkchen neben dem Asset, für das Sie die Lizenzvereinbarung angenommen haben. Klicken oder tippen Sie auf die Schaltfläche **[!UICONTROL Herunterladen]**.

   >[!NOTE]
   >
   >Die Schaltfläche **[!UICONTROL Herunterladen]** ist nur dann verfügbar, wenn Sie der Lizenzvereinbarung für ein geschütztes Asset zustimmen. Wenn Ihre Auswahl jedoch sowohl geschützte als auch nicht geschützte Assets enthält, erscheinen nur die geschützten Assets im linken Bereich und die Schaltfläche **[!UICONTROL Herunterladen]** ist für den Download der nicht geschützten Assets verfügbar. Sie können mehrere Lizenzvereinbarungen für verschiedene geschützte Assets gleichzeitig annehmen, indem Sie die Assets in der Liste auswählen und anschließend auf **[!UICONTROL Zustimmen]** klicken.

1. Tippen oder klicken Sie im Dialogfeld auf **[!UICONTROL Herunterladen]**, um das Asset oder seine Ausgabeformate herunterzuladen.
