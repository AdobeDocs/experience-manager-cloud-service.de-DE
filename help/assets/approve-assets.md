---
title: Genehmigen von Assets in Experience Manager
description: Erfahren Sie, wie Sie Assets in [!DNL Experience Manager] genehmigen.
role: User
exl-id: fe61a0f1-94d3-409a-acb9-195979668c25
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: ht
source-wordcount: '1063'
ht-degree: 100%

---

# Genehmigen von Assets in [!DNL Experience Manager]

Markenverantwortliche und Marketing-Fachleute behalten die strenge Kontrolle über Marken-Assets. Es können nur genehmigte und neueste Versionen des Assets verwendet werden. Dadurch wird die Markenkonsistenz in allen Kanälen und Anwendungen sichergestellt.

Sie können Assets in AEM Assets genehmigen, um das Asset-Management zu optimieren und so einen kontrollierten und effizienten Prozess für den Umgang mit Assets sicherzustellen.

## Voraussetzungen {#pre-requisites}

Sie benötigen Zugriff auf AEM Assets as a Cloud Service und Berechtigungen, um die Eigenschaft **[!UICONTROL Überprüfungsstatus]** für ein Asset zu bearbeiten.

## Konfiguration

Sie müssen das entsprechende Metadatenschema in der Admin-Ansicht einmalig aktualisieren, bevor Sie ein Asset genehmigen können. Sie können diese Konfiguration für die Assets-Ansicht überspringen. Führen Sie die folgenden Schritte aus, um das Metadatenschema zu konfigurieren:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
1. Wählen Sie das entsprechende Metadatenschema aus und klicken Sie auf **[!UICONTROL Bearbeiten]**. <br>Der **[!UICONTROL Metadatenschema-Formular-Editor]** wird geöffnet und die Registerkarte **[!UICONTROL Allgemein]** ist hervorgehoben.
1. Scrollen Sie nach unten und klicken Sie auf **[!UICONTROL Überprüfungsstatus]**.
1. Klicken Sie im Bedienfeld auf der rechten Seite auf die Registerkarte **[!UICONTROL Regeln]**.
1. Deaktivieren Sie **[!UICONTROL Bearbeitung deaktivieren]**.
Um die Eigenschaft anzuzeigen, der das Feld **[!UICONTROL Überprüfungsstatus]** zugeordnet ist, navigieren Sie zur Registerkarte **[!UICONTROL Einstellungen]** und zeigen Sie den Wert `./jcr:content/metadata/dam:status` im Feld **[!UICONTROL Zu Eigenschaft zuordnen]** an.
1. Ziehen Sie ein **[!UICONTROL Dropdown-Feld]** per Drag-and-Drop aus dem Abschnitt **[!UICONTROL Formular erstellen]** auf der rechten Seite in den Abschnitt „Metadaten“ des Formulars.
1. Klicken Sie auf das neu hinzugefügte Feld und nehmen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** vor:
   1. Ändern Sie den **[!UICONTROL Feldtitel]** in _Genehmigungsziel_.
   1. Setzen Sie **[!UICONTROL Zu Eigenschaft zuordnen]** auf _./jcr:content/metadata/dam:activationTarget_.
   1. Fügen Sie die Auswahlmöglichkeiten mit `contenthub` und `delivery` als Optionswerte hinzu.

   >[!NOTE]
   >
   >Wenn Sie mithilfe der Assets-Ansicht „Content Hub“ als Genehmigungsziel auswählen, werden die Assets in Content Hub für die Benutzenden bereitgestellt, die derselben Organisation angehören. Wenn Sie „Genehmigungsziel“ für die Bereitstellung auswählen, stehen die Assets allen Benutzenden zur Verfügung.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Wenn Ihre Assets oder Ordner ein anderes Standardschema aufweisen, stellen Sie sicher, dass diese Aktualisierung in diesem Schema vorgenommen wird.

## Genehmigen von Assets {#approve-assets}

Führen Sie folgende Schritte aus, um Assets in [!DNL Experience Manager Admin view] zu genehmigen:

1. Wählen Sie die Assets aus und klicken Sie im oberen Bereich auf **[!UICONTROL Eigenschaften]**.
1. Scrollen Sie auf der Registerkarte **[!UICONTROL Allgemein]** nach unten zu **[!UICONTROL Überprüfungsstatus]**.
1. Ändern Sie den Überprüfungsstatus in **[!UICONTROL Genehmigt]**.
   ![Bild](/help/assets/assets/approve-old-ui.png)
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   Sie können Assets auch mithilfe der [neuen Assets-Ansicht](/help/assets/manage-organize-assets-view.md) genehmigen.

## Massengenehmigung von Assets {#bulk-approve-assets}

Optimieren Sie Ihren Workflow, indem Sie mehrere Assets gleichzeitig genehmigen. Sie können eine Massengenehmigung von Assets durchführen, um den Genehmigungsprozess zu beschleunigen, Zeit zu sparen und die Produktivität zu steigern.
<br>Führen Sie die folgenden Schritte aus, um gleichzeitig mehrere Assets in [!DNL Experience Manager Admin view] zu genehmigen:

1. Erstellen Sie einen Ordner in der Autorenumgebung (https://author-pXXX-eYYY.adobeaemcloud.com). Ersetzen Sie _XXX_ durch Ihre Programm-ID und _YYY_ durch die Umgebungs-ID aus Experience Manager.
1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]**.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Erstellen]**.
1. Fügen Sie einen Profiltitel hinzu und klicken Sie auf **[!UICONTROL Erstellen]**. Das Metadatenprofil wird erstellt.
1. Wählen Sie das neu erstellte Metadatenprofil aus und klicken Sie auf **[!UICONTROL Bearbeiten _(e)_]**. <br>Das Formular **[!UICONTROL Metadatenprofil bearbeiten]**wird geöffnet und die Registerkarte **[!UICONTROL Allgemein]**ist hervorgehoben.
1. Ziehen Sie ein **[!UICONTROL einzeiliges Textfeld]** per Drag-and-Drop aus dem Abschnitt **[!UICONTROL Formular erstellen]** auf der rechten Seite in den Abschnitt „Metadaten“ des Formulars.
1. Klicken Sie auf das neu hinzugefügte Feld und führen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** durch:
   1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** in _Genehmigte Assets_.
   1. Setzen Sie **[!UICONTROL Zu Eigenschaft zuordnen]** auf _./jcr:content/metadata/dam:status_.
   1. Ändern Sie den Standardwert in _genehmigt_.

1. Ziehen Sie ein **[!UICONTROL Dropdown-Feld]** per Drag-and-Drop aus dem Abschnitt **[!UICONTROL Formular erstellen]** auf der rechten Seite in den Abschnitt „Metadaten“ des Formulars.
1. Klicken Sie auf das neu hinzugefügte Feld und nehmen Sie dann die folgenden Aktualisierungen im Bedienfeld **[!UICONTROL Einstellungen]** vor:
   1. Ändern Sie den **[!UICONTROL Feldtitel]** in _Genehmigungsziel_.
   1. Setzen Sie **[!UICONTROL Zu Eigenschaft zuordnen]** auf _./jcr:content/metadata/dam:activationTarget_.
   1. Fügen Sie die Auswahlmöglichkeiten mit `contenthub` und `delivery` als Optionswerte hinzu.

   >[!NOTE]
   >
   >Wenn Sie mithilfe der Assets-Ansicht „Content Hub“ als Genehmigungsziel auswählen, werden die Assets in Content Hub für die Benutzenden bereitgestellt, die derselben Organisation angehören. Wenn Sie „Genehmigungsziel“ für die Bereitstellung auswählen, stehen die Assets allen Benutzenden zur Verfügung.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das neu erstellte Metadatenprofil aus.
1. Klicken Sie in der oberen Aktionsleiste auf **[!UICONTROL Metadatenprofil auf Ordner anwenden]**.
1. Wählen Sie die Ordner aus, die Sie genehmigen müssen, und klicken Sie auf **[!UICONTROL Übernehmen]**.
   <br> Die Genehmigung ist als Berechtigung für den gesamten Ordner festgelegt und alle in diesen Ordner hochgeladenen Assets werden automatisch genehmigt.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>Bei diesem Ansatz werden die neu erstellten Assets im Ordner genehmigt. Assets, die bereits im Ordner vorhanden sind, müssen Sie manuell auswählen und genehmigen. <br> Alternativ können Sie die Option **[!UICONTROL Erneut verarbeiten]** verwenden, um die Änderungen vom Metadatenprofil auf ältere Assets anzuwenden.

So genehmigen Sie gleichzeitig mehrere Assets in einem Ordner in der Assets-Ansicht:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Massenbearbeitung von Metadaten]**.

1. Wählen Sie im rechten Bereich im Abschnitt [!UICONTROL Eigenschaften] im Feld **[!UICONTROL Status]** die Option **[!UICONTROL Genehmigt]** aus.

   Wenn Sie als Status `Approved` auswählen und [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) und/oder [Content Hub](/help/assets/product-overview.md) für Experience Manager Assets aktiviert sind, können Sie die Optionen für `Delivery` und `Content Hub` anzeigen, die im Feld **[!UICONTROL Genehmigungsziel]** verfügbar sind.

   * Wählen Sie **[!UICONTROL Bereitstellung]** aus, um die Assets sowohl für Dynamic Media mit OpenAPI-Funktionen als auch für Content Hub verfügbar zu machen. Wenn Sie Content Hub nicht aktiviert haben, werden die Assets bei Auswahl dieser Option nur für Dynamic Media mit OpenAPI-Funktionen verfügbar.
   * Wählen Sie **[!UICONTROL Content Hub]** aus, um die Assets für Content Hub verfügbar zu machen.

   ![Genehmigungsstatus](/help/assets/assets/approval-status-delivery.png)

   Wenn Sie nicht das Standard-Metadatenformular verwenden und das Feld **[!UICONTROL Genehmigungsziel]** nicht anzeigen können, [bearbeiten Sie Ihr Metadatenformular](/help/assets/metadata-assets-view.md#metadata-forms), um das Feld **[!UICONTROL Genehmigung für]** aus den verfügbaren Komponenten in Ihr Metadatenformular zu ziehen, und klicken Sie auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Wenn Sie mithilfe der Assets-Ansicht einer Organisation `Content Hub` als Genehmigungsziel auswählen, werden die Assets in Content Hub für die Benutzenden bereitgestellt, die derselben Organisation angehören.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Kopieren der Bereitstellungs-URL für genehmigte Assets {#copy-delivery-url-approved-assets}

Die Bereitstellungs-URL für alle genehmigten Assets im Repository ist verfügbar, wenn Sie [!UICONTROL Dynamic Media mit OpenAPI-Funktionen] in Ihrer Instanz von AEM as a Cloud Service aktiviert haben.

So kopieren Sie die Bereitstellungs-URL für ein genehmigtes Asset im Repository:

1. Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Details]**.

1. Klicken Sie auf das Symbol „Dynamic Media“ im rechten Bedienfeld.

1. Wählen Sie **[!UICONTROL Dynamic Media mit OpenAPI]** aus, das im Bedienfeld **[!UICONTROL Dynamic Media]** verfügbar ist.

1. Klicken Sie auf **[!UICONTROL URL kopieren]**, um die Bereitstellungs-URL des Assets zu kopieren.
   ![Dynamische Ausgabedarstellungen](/help/assets/assets/dm-with-openapi-non-image-assets.png)

   >[!NOTE]
   >
   >Die Option zum Kopieren der Bereitstellungs-URL für genehmigte Assets ist nur in der Assets-Ansicht verfügbar.

Informationen zu anderen Ausgabedarstellungen, die im Dynamic Media-Bedienfeld angezeigt werden, finden Sie unter [Anzeigen und Herunterladen von Dynamic Media-Ausgabedarstellungen](/help/assets/renditions.md#view-download-dm-renditions).
