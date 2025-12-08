---
title: Genehmigen von Assets für Content Hub
description: Erfahren Sie, wie Sie Assets in Assets as a Cloud Service genehmigen können, um sie in Content Hub verfügbar zu machen.
exl-id: fc849028-ab56-4388-b8d6-e36cac8f868f
source-git-commit: aec2bd06ad498e92ce1e69ac587ee7fcd5106268
workflow-type: tm+mt
source-wordcount: '1194'
ht-degree: 98%

---

# Genehmigen von Assets für Content Hub {#approve-assets-content-hub}

![Genehmigen von Assets für Content Hub](assets/content-hub-approve-assets.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub-Handbuch als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Markenverantwortliche und Marketing-Fachleute behalten die strenge Kontrolle über Marken-Assets. In Content Hub können nur genehmigte und neueste Versionen des Assets verwendet werden. Dadurch wird die Markenkonsistenz in allen Kanälen und Anwendungen sichergestellt.

Sie können Assets mithilfe von AEM Assets as a Cloud Service genehmigen, um das Asset-Management zu optimieren und so einen kontrollierten und effizienten Prozess für die Verarbeitung von Assets sicherzustellen.

## Bevor Sie beginnen {#pre-requisites}

Bevor Sie beginnen, sollten Sie über Folgendes verfügen:

* Zugriff auf AEM Assets as a Cloud Service

* Schreibrechte zum Bearbeiten von Asset-Metadaten, um das Feld **[!UICONTROL Status]** bearbeiten zu können, das in den [Asset-Eigenschaften](/help/assets/manage-organize-assets-view.md##manage-asset-status) für ein Asset verfügbar ist.

## Genehmigen von Assets für Content Hub{#approve-assets-for-content-hub}

Die Assets, die in Assets as a Cloud Service als `approved` markiert sind, sind automatisch in Content Hub verfügbar.

>[!NOTE]
>
>Assets as a Cloud Service und Content Hub müssen dieselbe Organisation verwenden, damit die Assets in Content Hub angezeigt werden.

So legen Sie den Asset-Status mithilfe der Assets-Ansicht in AEM as a Cloud Service auf `approved` fest:

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Details]**.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Allgemein]** in der Dropdown-Liste **[!UICONTROL Status]** die Option `approved` für den Asset-Status aus.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3433172)

Informationen zum Genehmigen von Assets mithilfe der Admin-Ansicht finden Sie unter [Genehmigen von Assets mithilfe der Admin-Ansicht](/help/assets/approve-assets.md#approve-assets).

## Genehmigen mehrerer Assets für Content Hub mithilfe der Assets-Ansicht {#bulk-approve-assets-content-hub}

Genehmigen Sie mehrere Assets als Ganzes mithilfe der Assets-Ansicht für AEM Assets as a Cloud Service. Anschließend stehen alle Assets, die als Ganzes genehmigt wurden, in Content Hub zur Verfügung.

So genehmigen Sie mehrere Assets in einem Ordner in der Assets-Ansicht als Ganzes:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Massenbearbeitung von Metadaten]**.

1. Wählen Sie im rechten Bereich im Abschnitt [!UICONTROL Eigenschaften] im Feld **[!UICONTROL Status]** die Option **[!UICONTROL Genehmigt]** aus.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Festlegen des Genehmigungsziels {#set-approval-target}

Mit der Assets-Ansicht können Sie genehmigte Assets in Dynamic Media veröffentlichen, wobei OpenAPI-Funktionen, Content Hub oder beides auf dem Wert basieren, den Sie im Feld **Genehmigungsziel** auf der Seite „Asset-Details“ festgelegt haben.

So legen Sie das Genehmigungsziel fest:

1. Wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Details]**.

1. Wählen Sie in der Registerkarte **[!UICONTROL Allgemein]** den Asset-Status aus der Dropdown-Liste **[!UICONTROL Status]** aus. Zu den zulässigen Werten gehören „Genehmigt“, „Abgelehnt“ und „Kein Status“ (Standard).

1. Wenn Sie in Schritt 2 **Genehmigt** auswählen, wählen Sie ein Genehmigungsziel aus. Zu den möglichen Werten gehören „Bereitstellung“ und „Content Hub“.

   * **Bereitstellung** ist die im Dropdown-Menü ausgewählte Standardoption. Das Asset wird sowohl in [Dynamic Media mit OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) als auch in [Content Hub](/help/assets/product-overview.md) veröffentlicht, sofern beide für Experience Manager Assets aktiviert sind.

   * Bei Auswahl von **Content Hub** wird das Asset nur in Content Hub veröffentlicht. Content Hub wird nur dann als Option angezeigt, wenn es für Experience Manager Assets aktiviert ist.

   * Wenn Sie keine Option aus der Dropdown-Liste auswählen, wird automatisch die für Ihre AEM as a Cloud Service-Umgebung aktivierte Standardoption auf das Asset angewendet.


   Weitere Informationen zu den verfügbaren Optionen finden Sie unter [Standardmäßige Genehmigungsziele und Veröffentlichungsziele für genehmigte Assets](#default-approval-target-options-publish-destinations).

   ![Genehmigungsstatus](/help/assets/assets/approval-status-delivery.png)

1. Geben Sie andere Asset-Eigenschaften an und klicken Sie auf **[!UICONTROL Speichern]**.

Weitere zu beachtende Punkte sind:

* Wenn Sie nicht das Standard-Metadatenformular verwenden und das Feld **[!UICONTROL Genehmigungsziel]** nicht sehen können, [bearbeiten Sie Ihr Metadatenformular](/help/assets/metadata-assets-view.md#metadata-forms), indem Sie das Feld **[!UICONTROL Genehmigung für]** aus den verfügbaren Komponenten in Ihr Metadatenformular ziehen, und klicken Sie auf **[!UICONTROL Speichern]**.

* Wenn Sie das Genehmigungsziel mithilfe der Assets-Ansicht als `Content Hub` auswählen, werden die Assets in Content Hub für die Benutzenden bereitgestellt, die derselben Organisation angehören.

### Standardmäßige Genehmigungsziele und Veröffentlichungsziele für genehmigte Assets {#default-approval-target-options-publish-destinations}

Die folgende Tabelle zeigt die Voraussetzungen für die Anzeige der Dropdown-Liste `Approval Target` und des standardmäßigen Validierungsziels, basierend auf der Aktivierung von DM mit OpenAPI und Content Hub in Ihrer AEM as a Cloud Service-Umgebung:

| Dynamic Media mit OpenAPI | Content Hub | Wird die Dropdown-Liste „Genehmigungsziel“ angezeigt? | Standardmäßiges Genehmigungsziel für genehmigte Assets | Veröffentlichungsziel |
| --- | --- | --- | --- |---|
| Aktiviert | Aktiviert | Ja | Bereitstellung | Dynamic Media mit OpenAPI und Content Hub |
| Nicht aktiviert | Aktiviert | Ja | Content Hub | Content Hub |
| Aktiviert | Nicht aktiviert | Ja | Bereitstellung | Dynamic Media mit OpenAPI |
| Nicht aktiviert | Nicht aktiviert | Nein | Nicht zutreffend | Nicht zutreffend |

## Automatisierte Genehmigung für neu aufgenommene Assets in der Admin-Ansicht {#automate-approval-newly-ingested-assets}

Nachdem Sie von der Assets-Ansicht zur Admin-Ansicht gewechselt haben, können Sie Ordnereinstellungen einrichten, damit alle neuen Assets, die zum Ordner hinzugefügt werden, automatisch genehmigt werden.

Sie können wie folgt zwischen der Admin- und Assets-Ansicht wechseln:
![Übersicht über „Mein Arbeitsbereich“](assets/assets-view.png)

Führen Sie die folgenden Schritte aus, um die Genehmigung für neu aufgenommene Assets in [!DNL Experience Manager Admin view] zu automatisieren:

1. Erstellen Sie einen Ordner in der Autorenumgebung (https://author-pXXX-eYYY.adobeaemcloud.com). Ersetzen Sie _XXX_ durch Ihre Programm-ID und _YYY_ durch die Umgebungs-ID aus Experience Manager.
1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]**.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Erstellen]**.
1. Fügen Sie einen Profiltitel hinzu und klicken Sie auf **[!UICONTROL Erstellen]**. Das Metadatenprofil wird erstellt.
1. Wählen Sie das neu erstellte Metadatenprofil aus und klicken Sie auf **[!UICONTROL Bearbeiten _(e)_]**. <br>Das Formular **[!UICONTROL Metadatenprofil bearbeiten]**wird geöffnet und die Registerkarte **[!UICONTROL Allgemein]**ist hervorgehoben.
1. Ziehen Sie ein **[!UICONTROL einzeiliges Textfeld]** per Drag-and-Drop aus dem Abschnitt **[!UICONTROL Formular erstellen]** auf der rechten Seite in den Abschnitt „Metadaten“ des Formulars.
1. Klicken Sie auf das neu hinzugefügte Feld und führen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** durch:
   1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** in _Genehmigte Assets_.
   1. Aktualisieren Sie **[!UICONTROL Zu Eigenschaft zuordnen]** auf _./jcr:content/metadata/dam :status_.
   1. Ändern Sie den Standardwert in _genehmigt_.

1. Ziehen Sie ein **[!UICONTROL einzeiliges Textfeld]** per Drag-and-Drop aus dem Abschnitt **[!UICONTROL Formular erstellen]** auf der rechten Seite in den Abschnitt „Metadaten“ des Formulars.
1. Klicken Sie auf das neu hinzugefügte Feld und nehmen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** vor:
   1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** in _Aktivierungsziel_.
   1. Aktualisieren Sie **[!UICONTROL Zu Eigenschaft zuordnen]** auf _./jcr:content/metadata/dam :activationTarget_.
   1. Ändern Sie den Standardwert in _contenthub_.

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das neu erstellte Metadatenprofil aus.
1. Klicken Sie in der oberen Aktionsleiste auf **[!UICONTROL Metadatenprofil auf Ordner anwenden]**.
1. Wählen Sie die Ordner aus, die Sie genehmigen müssen, und klicken Sie auf **[!UICONTROL Übernehmen]**.
   <br> Die Genehmigung ist als Berechtigung für den gesamten Ordner festgelegt und alle in diesen Ordner hochgeladenen Assets werden automatisch genehmigt.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>Bei diesem Ansatz werden die neu erstellten Assets im Ordner genehmigt. Assets, die bereits im Ordner vorhanden sind, müssen Sie manuell auswählen und genehmigen.

## Verwalten von mit Content Hub hochgeladenen Assets {#manage-assets-uploaded-using-content-hub}

[Content Hub-Benutzende mit Berechtigungen zum Hinzufügen von Assets](/help/assets/deploy-content-hub.md#onboard-content-hub-users-add-assets) können [Assets zu Content Hub hinzufügen](/help/assets/upload-brand-approved-assets.md). Assets können aus dem lokalen Dateisystem hinzugefügt oder aus OneDrive- oder Dropbox-Datenquellen importiert werden. Alle Assets werden unabhängig von der Ordnerstruktur in Ihrem lokalen Dateisystem oder den OneDrive- und Dropbox-Datenquellen auf der obersten Ebene in Content Hub angezeigt, um die Suchfunktionen zu verbessern.

Ob die mit Content Hub hochgeladenen Assets angezeigt werden, hängt davon ab, ob Sie [den Umschalter für die automatische Genehmigung aktiviert haben](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub):

* Wenn der Umschalter **[!UICONTROL Automatische Genehmigung]** aktiviert ist, sind die Assets, die Sie mit Content Hub hochladen, automatisch verfügbar.

* Wenn der Umschalter **[!UICONTROL Automatische Genehmigung]** deaktiviert ist, werden die Assets, die Sie mit Content Hub hochladen, nicht automatisch angezeigt. Die Assets sind im Ordner `hydrated-assets` Ihrer Assets as a Cloud Service-Umgebung verfügbar. Navigieren Sie zu dem Ordner und ändern Sie die Status dieser Assets [gemeinsam](#bulk-approve-assets-content-hub) in `Approved`, damit diese Assets in Content Hub angezeigt werden.

![Content Hub-Genehmigungsprozess](/help/assets/assets/content-hub-approval.png)
