---
title: Vorschau von Assets vor deren Verwendung auf AEM Sites-Seiten
description: Dynamic Media mit OpenAPI-Funktionen ermöglicht die Vorschau von Assets auf Adobe Experience Manager Sites-Vorschauseiten (AEM). Diese Asset-Vorschau ermöglicht es Ihnen und Ihren Stakeholdern, die Aktualisierungen Ihrer Assets zu überprüfen und zu validieren, bevor Sie die Autorenseiten (mit aktualisierten Assets) für den öffentlichen Gebrauch veröffentlichen.
role: Admin, User
source-git-commit: e343cc5754ec5565e57a5a932d59d7bfe78c6027
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Vorschau von Assets vor deren Verwendung auf AEM Sites-Seiten {#asset-preview-using-Dynamic-Media-with-OpenAPI-capabilities}

[!DNL Dynamic Media with OpenAPI capabilities] können Sie eine Vorschau der auf Ihren [!DNL Adobe Experience Manager (AEM) Sites]-Autorenseiten verfügbaren Assets anzeigen, bevor Sie sie öffentlich verfügbar machen. Die Asset-Vorschau ist auf der Autoren- und Vorschauebene Ihrer Site verfügbar.

Um [Vorschau von Assets auf AEM Sites-Vorschauseiten](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities) zu erstellen, aktualisieren Sie die Autorenseiten Ihrer Site, indem Sie entweder die Assets hinzufügen, die Sie in der Vorschau anzeigen möchten, oder die vorhandenen Assets ersetzen, die auf Ihrer Live-Sites-Seite verfügbar sind. Veröffentlichen Sie dann die aktualisierten Autorenseiten in der Vorschauebene, um eine Vorschau-URL zu generieren.

Geben Sie die Vorschauseite für die Beteiligten frei, um Feedback zur visuellen Qualität und kontextuellen Ausrichtung der aktualisierten Assets zu sammeln. Verfeinern von Assets basierend auf Feedback. Erstellen und verwalten Sie mehrere Versionen des Assets während des Prüfungszyklus.

Nachdem Sie die Assets für die öffentliche Verwendung fertig gestellt haben, aktualisieren Sie sie auf Ihren Autorenseiten und veröffentlichen Sie die Seiten auf der Veröffentlichungsebene für den öffentlichen Zugriff.

## Bevor Sie beginnen{#prerequisites-for-previewing-assets-using-Dynamic-Media-with-OpenAPI-capabilities}

Stellen Sie sicher, dass Sie Folgendes haben:

* Sie haben Zugriff auf [!DNL AEM Assets as a Cloud Service].
* Berechtigung zum Bearbeiten der Status-Eigenschaft von Assets.
* [Der Wert [!UICONTROL Vorschau] wurde zur Metadateneigenschaft [!UICONTROL Status] hinzugefügt, die auf der Registerkarte [!UICONTROL Standard] des Metadatenformulars ](/help/assets/metadata-assets-view.md#edit-metadata-forms) ist, das auf den Ordner mit den Assets angewendet wurde, die in der Vorschau angezeigt werden sollen.
  ![Option „Vorschau hinzufügen“](/help/assets/assets/metedata-form-preview.png)
* Der Schlüssel zum Generieren des Vorschau-Tokens. [Kontaktieren Sie den Adobe](https://helpx.adobe.com/in/contact.html)Support und fordern Sie den Schlüssel an.

## Asset-Vorschau auf der Sites-Vorschauseite {#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities}

Sie können neue Assets oder bereits genehmigte Assets in der Vorschau anzeigen. Genehmigte Assets werden nur auf Ihren Live-Sites-Seiten angezeigt.

Führen Sie die folgenden Schritte aus, um den Asset-Status auf Vorschau in [!DNL Assets View] festzulegen, und veröffentlichen Sie dann Ihre Sites-Authoring-Seite auf der Vorschauebene, um eine Vorschau-URL der Seite zu generieren:

1. Legen Sie den Asset-Status **[!UICONTROL Vorschau]** fest, indem Sie die folgenden Schritte ausführen:

   1. Wählen Sie in [!DNL Assets View] **[!UICONTROL Assets]** aus und navigieren Sie zu Ihrem Ordner.
   1. Wählen Sie das Asset aus, das Sie in der Vorschau anzeigen möchten.
   1. Klicken Sie auf **[!UICONTROL Details]**.
   1. Legen Sie im [!UICONTROL Informationsbereich] &quot;**[!UICONTROL &quot;]** &quot;**[!UICONTROL Vorschau]** fest und klicken Sie dann auf **[!UICONTROL Speichern]**.
      ![Vorschau](/help/assets/assets/preview-boat-at-bay.png)

1. Navigieren Sie zu Ihrer Sites-Authoring-Seite. Führen Sie die Schritte im Abschnitt [Zugriff auf Remote-Assets im AEM](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor)Seiteneditor aus, um das Asset auszuwählen, das Sie kürzlich im Asset-Auswahlbereich als Vorschau (Status) festgelegt haben.

   >[!NOTE]
   >
   > Der Asset-Wähler zeigt Assets mit dem aktuellen Status-Update an, das entweder auf Genehmigt oder Vorschau festgelegt ist.

1. Veröffentlichen Sie Ihre Seite auf der Vorschauebene mit der Option **[!UICONTROL Veröffentlichung verwalten]**. Führen Sie die Schritte im Abschnitt [Veröffentlichen von Inhalten in der Vorschau](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/previewing-content) aus, um Ihre Seite in der Vorschauebene zu veröffentlichen. Generieren Sie nach dem Veröffentlichen eine Vorschau-URL Ihrer Seite. Auf der Seite Vorschau werden die Assets (mit den neuesten Statusaktualisierungen) auf Ihrer Sites-Seite angezeigt.

Geben Sie diese Vorschau-URL zur Überprüfung und für Feedback an die Stakeholder weiter. Stellen Sie sicher, dass Ihre Stakeholder Zugriff auf die Vorschauseite haben. Informationen [ Gewähren des Zugriffs auf die Vorschauseiten finden ](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments#access-preview-service) unter „Zugriff auf den Vorschau-Service“.

>[!NOTE]
>
>Die [Image V3-Kernkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/wcm-components/image#version-and-compatibility) unterstützt standardmäßig die Vorschauversion von Assets. Wenn Sie eine Vorschauversion eines Assets (Asset mit Vorschaustatus) im Bedienfeld [Asset-Selektor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/asset-selector-upload) auswählen, rendert die Bild-V3-Komponente das Asset automatisch in der Vorschauebene (eine Vorschauversion auf der Sites-Autorenseite).

Nachdem Sie die Asset-Version fertig gestellt haben[ veröffentlichen Sie Ihre Seiten auf der ](#publish-your-pages-to-publish-tier) für den öffentlichen Gebrauch.

## Veröffentlichen von Seiten mit genehmigten Assets für die öffentliche Verwendung{#publish-your-pages-to-publish-tier}

Nachdem Sie die Asset-Version für die öffentliche Verwendung fertig gestellt haben, setzen Sie den Asset-Status auf **[!UICONTROL Genehmigt]**. Veröffentlichen Sie dann Ihre Seiten auf der Veröffentlichungsebene. Führen Sie die folgenden Schritte aus, um Ihre Seite zu veröffentlichen:

1. Befolgen Sie Schritt 1 [ obigen Abschnitt „Vorschau von Assets auf ](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities) Sites-Vorschauseite“, um den Asset-Status in &quot;**[!UICONTROL &quot;]** ändern.
1. Navigieren Sie zu Ihrer Sites-Autorenseite und veröffentlichen Sie sie in der [!DNL Publish tier]. Veröffentlichen Sie die Seiten, indem Sie die Schritte im Abschnitt [Veröffentlichen im Seiteneditor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/page-editor/publishing#publishing-from-the-page-editor) ausführen.
Alternativ können Sie die Schritte im Abschnitt [Veröffentlichen von Seiten über die Sites](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/publishing-pages#publishing-from-the-sites-console) ausführen, um Ihre Seite über die Konsole Ihrer Site zu veröffentlichen.

   >[!NOTE]
   >
   > Auf der Veröffentlichungsebene können nur genehmigte Assets bereitgestellt werden. Genehmigen Sie die Assets, bevor Sie Ihre Seite zur öffentlichen Verwendung auf der Veröffentlichungsebene veröffentlichen.

   ![Die Seite wurde veröffentlicht](/help/assets/assets/the-page-has-been-publushed.png)
Nach erfolgreicher Veröffentlichung wird **[!UICONTROL Bestätigungsmeldung „Die]** wurde veröffentlicht“ angezeigt. Navigieren Sie auf der Veröffentlichungsebene zu Ihrer veröffentlichten Seite, um zu bestätigen, dass die Aktualisierungen live sind und der Inhalt wie erwartet angezeigt wird.

