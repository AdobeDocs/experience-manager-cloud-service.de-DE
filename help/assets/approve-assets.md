---
title: Genehmigen von Assets in Experience Manager
description: Erfahren Sie, wie Sie Assets in [!DNL Experience Manager] genehmigen.
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 2%

---

# Genehmigen von Assets in [!DNL Experience Manager]

Brand Manager und Marketingexperten behalten die strenge Kontrolle über Marken-Assets. Es steht nur die genehmigte und neueste Version des Assets zur Verwendung zur Verfügung, wodurch Markenkonsistenz über alle Kanäle und Anwendungen hinweg gewährleistet ist.

Sie können Assets in AEM Assets genehmigen, um die Asset-Verwaltung zu optimieren und so einen kontrollierten und effizienten Prozess für die Verarbeitung von Assets sicherzustellen.

## Vorbereitung {#pre-requisites}

Sie müssen Zugriff auf AEM Assets as a Cloud Service und Berechtigungen haben, um die Eigenschaft **[!UICONTROL Prüfungsstatus]** für ein Asset zu bearbeiten.

## Konfiguration

Sie müssen das entsprechende Metadatenschema in der Admin-Ansicht nur einmal aktualisieren, bevor Sie ein Asset genehmigen können. Sie können diese Konfiguration für die Assets-Ansicht überspringen. Führen Sie die folgenden Schritte aus, um das Metadatenschema zu konfigurieren:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
1. Wählen Sie das entsprechende Metadatenschema aus und klicken Sie auf **[!UICONTROL Bearbeiten]**. <br> Der **[!UICONTROL Metadatenschema-Formular-Editor]** wird geöffnet, wobei die Registerkarte **[!UICONTROL Einfach]** hervorgehoben ist.
1. Scrollen Sie nach unten und klicken Sie auf **[!UICONTROL Prüfungsstatus]**.
1. Klicken Sie im rechten Seitenbereich auf die Registerkarte **[!UICONTROL Regeln]** .
1. Deaktivieren Sie **[!UICONTROL Bearbeitung deaktivieren]** und klicken Sie auf **[!UICONTROL Speichern]**.
Wenn Sie die Eigenschaft anzeigen müssen, der das Feld **[!UICONTROL Prüfungsstatus]** zugeordnet ist, navigieren Sie zur Registerkarte **[!UICONTROL Einstellungen]** und zeigen Sie den Wert `./jcr:content/metadata/dam:status` im Feld **[!UICONTROL Zu Eigenschaft zuordnen]** an.

>[!NOTE]
>
>Wenn Ihre Assets oder Ordner ein anderes Standardschema haben, stellen Sie sicher, dass diese Aktualisierung in diesem bestimmten Schema vorgenommen wird.

## Genehmigen von Assets {#approve-assets}

Sie können Assets sowohl in [!DNL Experience Manager] als auch in [!DNL Experience Manager Assets] genehmigen. Gehen Sie wie folgt vor, um Assets in [!DNL Experience Manager] zu genehmigen:

1. Wählen Sie das Asset(s) aus und klicken Sie im oberen Bereich auf **[!UICONTROL Eigenschaften]** .
1. Scrollen Sie auf der Registerkarte **[!UICONTROL Einfach]** nach unten zu **[!UICONTROL Prüfungsstatus]**.
1. Ändern Sie den Prüfungsstatus in &quot;**[!UICONTROL Genehmigt]**&quot;.
   ![Bild](/help/assets/assets/approve-old-ui.png)
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   Gleichermaßen können Sie Assets mithilfe der [neuen Assets-Ansicht](/help/assets/manage-organize-assets-view.md) genehmigen.

## Massenvalidierung von Assets {#bulk-approve-assets}

Optimieren Sie Ihren Workflow, indem Sie mehrere Assets gleichzeitig genehmigen. Sie können Assets in großen Mengen genehmigen, um den Genehmigungsprozess zu beschleunigen, Zeit zu sparen und die Produktivität zu steigern.
<br>Führen Sie die folgenden Schritte aus, um Massen-Assets in [!DNL Experience Manager] zu genehmigen:

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
>Bei diesem Ansatz werden die neu erstellten Assets im Ordner genehmigt. Für vorhandene Assets im Ordner müssen Sie sie manuell auswählen und genehmigen. <br> Alternativ können Sie die Option **[!UICONTROL Neu verarbeiten]** verwenden, um die Änderungen vom Metadatenprofil auf ältere Assets anzuwenden.

So genehmigen Sie Assets in einem Ordner in der Assets-Ansicht stapelweise:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Massenmetadaten bearbeiten]**.

1. Wählen Sie **[!UICONTROL Genehmigt]** im Feld **[!UICONTROL Status]** aus, das im Abschnitt [!UICONTROL Eigenschaften] im rechten Bereich verfügbar ist.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Versand-URL für genehmigte Assets kopieren {#copy-delivery-url-approved-assets}

Die Bereitstellungs-URL für alle genehmigten Assets im Repository ist verfügbar, wenn Sie [!UICONTROL Dynamic Media mit OpenAPI-Funktionen] in Ihrer AEM as a Cloud Service-Instanz aktiviert haben.

So kopieren Sie die Bereitstellungs-URL für ein genehmigtes Asset im Repository:

1. Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Details]**.

1. Klicken Sie im rechten Bereich auf das Symbol Ausgabeformate .

1. Wählen Sie im Abschnitt **[!UICONTROL Dynamisch]** die Option **[!UICONTROL Dynamic Media mit OpenAPI]** aus.

1. Klicken Sie auf **[!UICONTROL URL kopieren]** , um die Bereitstellungs-URL des Assets zu kopieren.
   ![Versand-URL kopieren](/help/assets/assets/copy-delivery-url.png)

   >[!NOTE]
   >
   >Die Option zum Kopieren der Bereitstellungs-URL für genehmigte Assets ist nur in der Assets-Ansicht verfügbar.

