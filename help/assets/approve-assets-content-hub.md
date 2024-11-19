---
title: Genehmigen von Assets für Content Hub
description: Erfahren Sie, wie Sie Assets in Assets as a Cloud Service genehmigen, um sie in Content Hub verfügbar zu machen.
exl-id: fc849028-ab56-4388-b8d6-e36cac8f868f
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 6%

---

# Genehmigen von Assets für Content Hub {#approve-assets-content-hub}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Genehmigen von Assets für Content Hub](assets/content-hub-approve-assets.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub Guide PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Brand Manager und Marketingexperten behalten die strenge Kontrolle über Marken-Assets. In Content Hub können nur genehmigte und neueste Versionen des Assets verwendet werden. Dadurch wird Markenkonsistenz in allen Kanälen und Anwendungen sichergestellt.

Sie können Assets mithilfe von AEM Assets as a Cloud Service genehmigen, um die Asset-Verwaltung zu optimieren und so einen kontrollierten und effizienten Prozess für die Verarbeitung von Assets sicherzustellen.

## Vorbereitung {#pre-requisites}

Bevor Sie beginnen, sollten Sie Folgendes haben:

* Zugriff auf AEM Assets as a Cloud Service

* Schreiben Sie Berechtigungen zum Bearbeiten von Asset-Metadaten, um das Feld **[!UICONTROL Status]** bearbeiten zu können, das in den [Asset-Eigenschaften](/help/assets/manage-organize-assets-view.md##manage-asset-status) für ein Asset verfügbar ist.

## Genehmigen von Assets für Content Hub{#approve-assets-for-content-hub}

Die Assets, die in Assets as a Cloud Service als `approved` markiert sind, sind automatisch in Content Hub verfügbar.

>[!NOTE]
>
Assets as a Cloud Service und Content Hub müssen dieselbe Organisation verwenden, damit die Assets in Content Hub angezeigt werden.

So legen Sie den Asset-Status mithilfe der Assets-Ansicht in AEM as a Cloud Service auf &quot;`approved`&quot;fest:

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Details]**.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Einfach]** den Asset-Status als `approved` aus der Dropdownliste **[!UICONTROL Status]** aus.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3433172)

Informationen zum Genehmigen von Assets mithilfe der Admin-Ansicht finden Sie unter [Genehmigen von Assets mithilfe der Admin-Ansicht](/help/assets/approve-assets.md#approve-assets).

## Massengenehmigen von Assets für Content Hub mithilfe der Assets-Ansicht {#bulk-approve-assets-content-hub}

Massenvalidierung von Assets mit der Assets-Ansicht für AEM Assets as a Cloud Service. Alle Assets, die stapelweise genehmigt wurden, stehen dann in Content Hub zur Verfügung.

So genehmigen Sie Assets in einem Ordner in der Assets-Ansicht stapelweise:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Massenmetadaten bearbeiten]**.

1. Wählen Sie **[!UICONTROL Genehmigt]** im Feld **[!UICONTROL Status]** aus, das im Abschnitt [!UICONTROL Eigenschaften] im rechten Bereich verfügbar ist.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Automatisierte Genehmigung für neu aufgenommene Assets in der Admin-Ansicht {#automate-approval-newly-ingested-assets}

Nachdem Sie von der Assets-Ansicht zur Admin-Ansicht gewechselt haben, können Sie Ordnereinstellungen einrichten, damit alle neuen Assets, die zum Ordner hinzugefügt werden, automatisch genehmigt werden.

Sie können wie folgt zwischen Admin- und Assets-Ansichten wechseln:
![Übersicht über meine Workspace](assets/assets-view.png)

Führen Sie die folgenden Schritte aus, um die Genehmigung für neu aufgenommene Assets in [!DNL Experience Manager Admin view] zu automatisieren:

1. Erstellen Sie einen Ordner in der Autorenumgebung (https://author-pXXX-eYYY.adobeaemcloud.com). Ersetzen Sie _XXX_ durch Ihre Programm-ID und _YYY_ durch die Umgebungs-ID des Experience Managers.
1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]**.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Erstellen]** .
1. Fügen Sie einen Profiltitel hinzu und klicken Sie auf **[!UICONTROL Erstellen]**. Das Metadatenprofil wurde erfolgreich erstellt.
1. Wählen Sie das neu erstellte Metadatenprofil aus und klicken Sie auf **[!UICONTROL Bearbeiten _(e)_]**. <br>Das Formular **[!UICONTROL Metadatenprofil bearbeiten]**wird mit der Registerkarte **[!UICONTROL Einfach]**geöffnet.
1. Ziehen Sie ein **[!UICONTROL einzeiliges Textfeld]** aus dem Abschnitt **[!UICONTROL Formular erstellen]** rechts in den Abschnitt &quot;Metadaten&quot;des Formulars.
1. Klicken Sie auf das neu hinzugefügte Feld und führen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** durch:
   1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** in _Genehmigte Assets_.
   1. Aktualisieren Sie die **[!UICONTROL Zuordnung zu Eigenschaft]** auf _./jcr:content/metadata/dam:status_.
   1. Ändern Sie den Standardwert in _authorised_.

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das neu erstellte Metadatenprofil aus.
1. Klicken Sie in der oberen Aktionsleiste auf **[!UICONTROL Metadatenprofil auf Ordner anwenden]** .
1. Wählen Sie die Ordner aus, die Sie genehmigen müssen, und klicken Sie auf **[!UICONTROL Anwenden]**.
   <br> Die Berechtigung für den gesamten Ordner wird zur Genehmigung festgelegt und alle in diesen Ordner hochgeladenen Assets werden automatisch genehmigt.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
Bei diesem Ansatz werden die neu erstellten Assets im Ordner genehmigt. Für vorhandene Assets im Ordner müssen Sie sie manuell auswählen und genehmigen.

## Verwalten von mit Content Hub hochgeladenen Assets {#manage-assets-uploaded-using-content-hub}

[Content Hub-Benutzer mit Berechtigungen zum Hinzufügen von Assets](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) können [Assets zur Content Hub](/help/assets/upload-brand-approved-assets.md) hinzufügen, entweder aus dem lokalen Dateisystem oder Assets aus OneDrive- oder Dropbox-Datenquellen importieren. Alle Assets werden unabhängig von der Ordnerstruktur in Ihrem lokalen Dateisystem oder den OneDrive- und Dropbox-Datenquellen auf der obersten Ebene in Content Hub angezeigt, um die Suchfunktionen zu verbessern.

Die Anzeige von Assets, die mit Content Hub hochgeladen wurden, hängt davon ab, ob Sie [den Umschalter für die automatische Genehmigung aktiviert haben](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub):

* Wenn der Umschalter **[!UICONTROL Automatische Genehmigung]** aktiviert ist, sind die Assets, die Sie mit Content Hub hochladen, automatisch verfügbar.

* Wenn der Umschalter **[!UICONTROL Automatische Genehmigung]** deaktiviert ist, werden die Assets, die Sie mit Content Hub hochladen, nicht automatisch angezeigt. Die Assets sind im Ordner &quot;`hydrated-assets`&quot;Ihrer Assets as a Cloud Service-Umgebung verfügbar. Navigieren Sie zum Ordner und bearbeiten Sie [stapelweise](#bulk-approve-assets-content-hub) den Status dieser Assets in `Approved` , damit diese Assets in Content Hub angezeigt werden.

![Content Hub-Genehmigungsprozess](/help/assets/assets/content-hub-approval.png)
