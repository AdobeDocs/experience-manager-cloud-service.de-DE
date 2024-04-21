---
title: Genehmigen von Assets in Experience Manager
description: Erfahren Sie, wie Sie Assets in genehmigen [!DNL Experience Manager].
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 3%

---

# Genehmigen von Assets in [!DNL Experience Manager]

Brand Manager und Marketingexperten behalten die strenge Kontrolle über Marken-Assets. Es steht nur die genehmigte und neueste Version des Assets zur Verwendung zur Verfügung, wodurch Markenkonsistenz über alle Kanäle und Anwendungen hinweg gewährleistet ist.

Sie können Assets in AEM Assets genehmigen, um die Asset-Verwaltung zu optimieren und so einen kontrollierten und effizienten Prozess für die Verarbeitung von Assets sicherzustellen.

## Vorbereitung {#pre-requisites}

Sie müssen Zugriff auf AEM Assets as a Cloud Service haben und über Berechtigungen zum Bearbeiten der **[!UICONTROL Prüfungsstatus]** -Eigenschaft für ein Asset.

## Konfiguration

Sie müssen eine einmalige Aktualisierung des entsprechenden Metadatenschemas im [!DNL Experience Manager] bevor Sie ein Asset genehmigen können. Sie können diese Konfiguration überspringen für [!DNL Experience Manager Assets]. Führen Sie die folgenden Schritte aus, um das Metadatenschema zu konfigurieren:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
1. Wählen Sie das entsprechende Metadatenschema aus und klicken Sie auf **[!UICONTROL Bearbeiten]**. <br>Die **[!UICONTROL Metadatenschema-Formular-Editor]** mit dem **[!UICONTROL Allgemein]** hervorgehoben.
1. Scrollen Sie nach unten und klicken Sie auf **[!UICONTROL Prüfungsstatus]**.
1. Klicken Sie auf **[!UICONTROL Regeln]** Registerkarte im rechten Seitenbereich.
1. Deaktivieren **[!UICONTROL Bearbeitung deaktivieren]** und klicken **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Wenn Ihre Assets oder Ordner ein anderes Standardschema haben, stellen Sie sicher, dass diese Aktualisierung in diesem bestimmten Schema vorgenommen wird.

## Genehmigen von Assets {#approve-assets}

Sie können Assets in beiden [!DNL Experience Manager] und [!DNL Experience Manager Assets]. So genehmigen Sie Assets in [!DNL Experience Manager]führen Sie die folgenden Schritte aus:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Eigenschaften]** im oberen Bereich.
1. Im **[!UICONTROL Allgemein]** Registerkarte, nach unten scrollen **[!UICONTROL Prüfungsstatus]**.
1. Ändern Sie den Prüfungsstatus in **[!UICONTROL Genehmigt]**.
   ![Bild](/help/assets/assets/approve-old-ui.png)
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   Auf ähnliche Weise können Sie Assets mit dem [neue Asset-Ansicht](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-organize.html?lang=en#manage-asset-status).

## Massenvalidierung von Assets {#bulk-approve-assets}

Optimieren Sie Ihren Workflow, indem Sie mehrere Assets gleichzeitig genehmigen. Sie können Assets in großen Mengen genehmigen, um den Genehmigungsprozess zu beschleunigen, Zeit zu sparen und die Produktivität zu steigern.
<br>Führen Sie die folgenden Schritte aus, um Massen-Assets in zu genehmigen [!DNL Experience Manager]:

1. Erstellen Sie einen Ordner in der Autorenumgebung (https://author-pXXX-eYYY.adobeaemcloud.com). Ersetzen _XXX_ mit Ihrer Programm-ID und _YYY_ mit der Umgebungs-ID des Experience Managers.
1. Navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]**.
1. Klicks **[!UICONTROL Erstellen]** oben rechts auf der Seite.
1. Hinzufügen eines Profiltitels und Klicken **[!UICONTROL Erstellen]**. Das Metadatenprofil wurde erfolgreich erstellt.
1. Wählen Sie das neu erstellte Metadatenprofil aus und klicken Sie auf **[!UICONTROL Bearbeiten _e)_]**. <br>Die **[!UICONTROL Metadatenprofil bearbeiten]**Das Formular wird mit dem **[!UICONTROL Allgemein]**hervorgehoben.
1. Ziehen und Ablegen eines **[!UICONTROL Einzeiliges Textfeld]** aus dem **[!UICONTROL Formular erstellen]** rechts neben dem Abschnitt Metadaten im Formular.
1. Klicken Sie auf das neu hinzugefügte Feld und führen Sie dann die folgenden Aktualisierungen im **[!UICONTROL Einstellungen]** Bereich:
   1. Ändern Sie die **[!UICONTROL Feldbezeichnung]** nach _Genehmigte Assets_.
   1. Aktualisieren Sie die **[!UICONTROL Zu Eigenschaft zuordnen]** nach _./jcr:content/metadata/dam:status_.
   1. Ändern Sie den Standardwert in _genehmigt_.

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Im **[!UICONTROL Metadatenprofile]** wählen Sie das neu erstellte Metadatenprofil aus.
1. Klicks **[!UICONTROL Anwenden von Metadatenprofilen auf Ordner]** in der oberen Aktionsleiste aus.
1. Wählen Sie die zu validierenden Ordner aus und klicken Sie auf **[!UICONTROL Anwenden]**.
   <br> Die Berechtigung für den gesamten Ordner wird zur Genehmigung festgelegt und alle in diesen Ordner hochgeladenen Assets werden automatisch genehmigt.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>Bei diesem Ansatz werden die neu erstellten Assets im Ordner genehmigt. Für vorhandene Assets im Ordner müssen Sie sie manuell auswählen und genehmigen. <br> Alternativ können Sie die **[!UICONTROL Neuverarbeitung]** -Option, um die Änderungen vom Metadatenprofil auf ältere Assets anzuwenden.
