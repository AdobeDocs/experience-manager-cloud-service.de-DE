---
title: Berichte zur Nutzung und Freigabe
description: Berichte zu Ihren Assets in  [!DNL Adobe Experience Manager Assets] , die Ihnen dabei helfen, Nutzung, Aktivität und Freigabe Ihrer digitalen Assets zu verstehen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 3ee2e53268ea77949057ac18fcb4a8f8b1e01cb2
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 100%

---


# Asset-Berichte  {#asset-reports}

Mit Asset-Berichten können Sie die Nützlichkeit Ihrer [!DNL Adobe Experience Manager Assets]-Implementierung bewerten. Mit [!DNL Assets] können Sie verschiedene Berichte für Ihre digitalen Assets erstellen. Die Berichte bieten hilfreiche Informationen über die Nutzung Ihres Systems, über die Art und Weise, wie Benutzer mit Assets interagieren, und die Frage, welche Assets heruntergeladen und freigegeben werden.

Verwenden Sie die Informationen aus den Berichten, um wesentliche Erfolgsmetriken abzuleiten und so festzustellen, wie gut [!DNL Assets] innerhalb Ihrer Organisation und von Ihren Kunden angenommen wird.

Das [!DNL Assets]-Berichterstellungs-Framework nutzt [!DNL Sling]-Aufträge, um Berichtsanfragen auf überschaubare Art asynchron zu verarbeiten. Es ist für große Repositorys skalierbar. Die asynchrone Berichtsverarbeitung steigert die Effizienz und Geschwindigkeit der Berichtsgenerierung.

Die Berichtsverwaltungsoberfläche ist intuitiv und umfasst detaillierte Optionen und Steuerelemente für den Zugriff auf archivierte Berichte und das Anzeigen des Ausführungsstatus von Berichten („Erfolg“, „Fehlgeschlagen“ und „In Warteschlange“).

Wenn ein Bericht generiert wird, werden Sie mit <!-- through an email (optional) and --> einer Benachrichtigung im Posteingang benachrichtigt. Sie können einen Bericht auf der Berichtslistenseite anzeigen, herunterladen oder löschen. Dort werden alle zuvor generierten Berichte angezeigt.

## Erstellen von Berichten {#generate-reports}

[!DNL Experience Manager Assets] generiert die folgenden standardmäßigen Berichte für Sie:

* Hochladen
* Download
* Ablauf
* Änderung
* Veröffentlichung
* [!DNL Brand Portal]-Veröffentlichung
* Festplattenauslastung
* Dateien
* Link-Freigabe

[!DNL Adobe Experience Manager]-Administratoren können diese Berichte einfach für Ihre Implementierung erstellen und anpassen. Um einen Bericht zu erstellen, müssen Administratoren folgende Schritte durchführen:

1. Klicken Sie in der [!DNL Experience Manager]-Benutzeroberfläche auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Berichte]**.

   ![Tools-Seite zum Navigieren in Asset-Berichten](assets/navigation.png)

1. Klicken Sie auf der Seite [!UICONTROL Asset-Berichte] in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Bericht erstellen]** den Bericht aus, den Sie erstellen möchten, und klicken Sie auf **[!UICONTROL Weiter]**.

   ![Berichtstyp auswählen](assets/choose_report.png)

<!-- TBD: How do enable this in CS now? Is it done using some OSGi config now?
   >[!NOTE]
   >
   >Before you can generate an **[!UICONTROL Asset Downloaded]** report, ensure that the Asset Download service is enabled. From the web console (`https://[aem_server]:[port]/system/console/configMgr`), open the **[!UICONTROL Day CQ DAM Event Recorder]** configuration, and select the **[!UICONTROL Asset Downloaded (DOWNLOADED)]** option in Event Types if not already selected.
-->

>[!NOTE]
>
>Standardmäßig sind die Inhaltsfragmente und Link-Freigaben im Bericht [!UICONTROL Download] für das Asset enthalten. Wählen Sie die passende Option aus, um einen Bericht zu Link-Freigaben zu erstellen oder Inhaltsfragmente aus dem Download-Bericht auszuschließen.

>[!NOTE]
>
>Der Bericht [!UICONTROL Download] zeigt nur Details zu den Assets an, die heruntergeladen werden, nachdem sie einzeln ausgewählt wurden, bzw. die per Schnellzugriff heruntergeladen werden. Er enthält jedoch keine Details zu den Assets, die sich in einem heruntergeladenen Ordner befinden.

1. Konfigurieren Sie die Berichtdetails wie Titel, Beschreibung, Miniaturansicht sowie den Ordnerpfad im CRX-Repository, der den Speicherort des Berichts angibt. Der standardmäßige Ordnerpfad lautet `/content/dam`. Sie können auch einen anderen Pfad festlegen.

   ![Seite zum Hinzufügen von Berichtsdetails](assets/report_configuration.png)

   Wählen Sie den Datumsbereich für Ihren Bericht aus.

   Sie können den Bericht wahlweise sofort oder zu einem zukünftigen Zeitpunkt generieren lassen.

   >[!NOTE]
   >
   >Wenn Sie sich dafür entscheiden, den Bericht für einen späteren Zeitpunkt zu planen, geben Sie unbedingt das Datum und die Uhrzeit in das Feld „Datum und Uhrzeit“ ein. Wenn Sie keinen Wert angeben, behandelt die Reporting-Engine den Bericht als einen sofort zu erstellenden Bericht.

   Die Konfigurationsfelder unterscheiden sich möglicherweise basierend auf der Art des erstellten Berichts. Beispielsweise bietet der Bericht zur **[!UICONTROL Festplattenauslastung]** Optionen, um bei der Berechnung des von Assets genutzten Festplattenvolumens Asset-Ausgabedarstellungen miteinzubeziehen. Sie können Assets in Unterordnern bei der Berechnung der Festplattenauslastung miteinbeziehen oder ausschließen.

   >[!NOTE]
   >
   >Der Bericht zur **[!UICONTROL Festplattenauslastung]** umfasst keine Felder für den Datumsbereich, da er nur den aktuellen Speicherbedarf angibt.

   ![Detailseite des Berichts „Festplattenauslastung“](assets/disk_usage_configuration.png)

   Wenn Sie den Bericht **[!UICONTROL Dateien]** erstellen, können Sie Unterordner miteinbeziehen/ausschließen. Bei diesem Bericht können Sie jedoch keine Asset-Ausgabedarstellungen miteinbeziehen.

   ![Detailseite des Berichts „Dateien“](assets/files_report.png)

   Der Bericht **[!UICONTROL Link-Freigabe]** zeigt URLs zu Assets an, die für externe Benutzer aus [!DNL Assets] freigegeben wurden. <!-- It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. --> Die Spalten können nicht angepasst werden.

   Der Bericht **[!UICONTROL Link-Freigabe]** umfasst keine Optionen für Unterordner und Ausgabedarstellungen, da er lediglich die freigegebenen URLs veröffentlicht, die unter `/var/dam/share` zu finden sind.

   ![Detailseite des Berichts „Link-Freigabe“](assets/link_share.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Weiter]**.

1. Auf der Seite **[!UICONTROL Spalten konfigurieren]** sind einige Spalten standardmäßig für den Bericht ausgewählt. Sie können zusätzliche Spalten auswählen. Heben Sie die Auswahl einer Spalte auf, wenn sie nicht im Bericht angezeigt werden soll.

   ![Berichtsspalten auswählen oder Auswahl aufheben](assets/configure_columns.png)

   Um einen benutzerdefinierten Spaltennamen oder Eigenschaftspfad anzuzeigen, konfigurieren Sie die Eigenschaften für die Asset-Binärdatei im `jcr:content`-Knoten in CRX. Alternativ können Sie sie über die Auswahl für den Eigenschaftspfad hinzufügen.

   ![Berichtsspalten auswählen oder Auswahl aufheben](assets/custom_columns.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**. Eine Meldung benachrichtigt Sie darüber, dass die Berichtserstellung startet.
1. Auf der Seite [!UICONTROL Asset-Berichte] basiert der angezeigte Berichterstellungsstatus auf dem aktuellen Status des Berichtauftrags, zum Beispiel [!UICONTROL Erfolg], [!UICONTROL Fehlgeschlagen], [!UICONTROL In Warteschlange] oder [!UICONTROL Geplant]. Derselbe Status wird auch im Benachrichtigungseingang angezeigt. Klicken Sie zur Ansicht der Berichtsseite auf den Berichts-Link. Alternativ wählen Sie den Bericht aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Anzeigen]**.

   ![Ein generierter Bericht](assets/report_page.png)

   Klicken Sie in der Symbolleiste auf **[!UICONTROL Download]**, um den Bericht im CSV-Format herunterzuladen.

## Hinzufügen benutzerdefinierter Spalten   {#add-custom-columns}

Sie können folgenden Berichten benutzerdefinierte Spalten hinzufügen, um weitere Daten für Ihre speziellen Anforderungen anzuzeigen:

* Hochladen
* Herunterladen
* Ablauf
* Änderung
* Veröffentlichung
* [!DNL Brand Portal]-Veröffentlichung
* Dateien

Gehen Sie wie folgt vor, um den Berichten benutzerspezifische Spalten hinzuzufügen:

1. Klicken Sie in der [!DNL Manager interface] auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Berichte]**.
1. Klicken Sie auf der Seite [!UICONTROL Asset-Berichte] in der Symbolleiste auf **[!UICONTROL Erstellen]**.

1. Wählen Sie auf der Seite **[!UICONTROL Bericht erstellen]** den Bericht aus, den Sie erstellen möchten, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Konfigurieren Sie je nach Bedarf Berichtdetails wie den Titel, eine Beschreibung, eine Miniaturansicht, den Ordnerpfad und den Datumsbereich.

1. Um eine benutzerdefinierte Spalte anzuzeigen, geben Sie den Namen der Spalte unter **[!UICONTROL Benutzerdefinierte Spalten]** an.

   ![Namen für benutzerdefinierte Berichtsspalte angeben](assets/custom_columns-1.png)

1. Fügen Sie den Eigenschaftspfad mit der Auswahl für den Eigenschaftspfad im `jcr:content`-Knoten in CRXDE hinzu. Alternativ können Sie den Pfad im Feld „Eigenschaftspfad“ eingeben.

   ![Den Eigenschaftspfad in den Pfaden in jcr:content zuordnen](assets/property_picker.png)

   Klicken Sie auf **[!UICONTROL Hinzufügen]** und wiederholen Sie die Schritte 5 und 6, um weitere benutzerdefinierte Spalten hinzuzufügen.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**. Eine Meldung benachrichtigt Sie darüber, dass die Berichtserstellung startet.

<!-- TBD: How to configure purge now? Is it using OSGi configurations?

## Configure purging service {#configure-purging-service}

To remove reports that you no longer require, configure the DAM Report Purge service from the web console to purge existing reports based on their quantity and age.

1. Access the web console (configuration manager) from `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL DAM Report Purge Service]** configuration.
1. Specify the frequency (time interval) for the purging service in the `scheduler.expression.name` field. You can also configure the age and the quantity threshold for reports.
1. Save the changes.
-->

## Informationen zur Fehlerbehebung, Tipps und Einschränkungen {#best-practices-and-limitations}

* Wenn der Bericht zur Speichernutzung nicht generiert wird und Sie [!DNL Dynamic Media] verwenden, stellen Sie sicher, dass alle Assets ordnungsgemäß verarbeitet werden. Verarbeiten Sie zur Behebung die Assets erneut und erstellen Sie dann den Bericht erneut.
