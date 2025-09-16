---
title: Anzeigen einer Vorschau von Assets vor deren Verwendung auf AEM Sites-Seiten
description: Dynamic Media mit OpenAPI-Funktionen ermöglicht die Vorschau von Assets auf Vorschauseiten von Adobe Experience Manager (AEM) Sites. Diese Asset-Vorschau ermöglicht es Ihnen und Ihren Stakeholdern, die Aktualisierungen Ihrer Assets zu überprüfen und zu validieren, bevor Sie die Authoring-Seiten (mit aktualisierten Assets) für den öffentlichen Gebrauch veröffentlichen.
role: Admin, User
exl-id: 6f071ca9-0f84-45fc-a6b3-047cca9d5e65
source-git-commit: 3f3e091d09b94418fc2cda0bd3b3ce950555b7a9
workflow-type: ht
source-wordcount: '731'
ht-degree: 100%

---


# Anzeigen einer Vorschau von Assets vor deren Verwendung auf AEM Sites-Seiten {#asset-preview-using-Dynamic-Media-with-OpenAPI-capabilities}

Mit [!DNL Dynamic Media with OpenAPI capabilities] können Sie eine Vorschau der auf Ihren Authoring-Seiten von [!DNL Adobe Experience Manager (AEM) Sites] verfügbaren Assets anzeigen, bevor Sie sie öffentlich verfügbar machen. Die Asset-Vorschau ist auf der Autoren- und Vorschauebene Ihrer Site verfügbar.

Um [eine Vorschau von Assets auf AEM Sites-Vorschauseiten](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities) zu erstellen, aktualisieren Sie die Authoring-Seiten Ihrer Site, indem Sie entweder die in der Vorschau anzuzeigenden Assets hinzufügen oder die auf Ihrer Live-Sites-Seite verfügbaren vorhandenen Assets ersetzen. Veröffentlichen Sie die aktualisierten Authoring-Seiten in der Vorschauebene, um eine Vorschau-URL zu generieren.

Geben Sie den Stakeholdern die Vorschauseite frei, um Feedback zur visuellen Qualität und kontextuellen Ausrichtung der aktualisierten Assets zu sammeln. Optimieren Sie die Assets basierend auf Feedback. Erstellen und verwalten Sie mehrere Versionen des Assets während des Überprüfungszyklus.

Nachdem Sie die Assets für die öffentliche Verwendung fertiggestellt haben, aktualisieren Sie sie auf Ihren Authoring-Seiten und veröffentlichen Sie die Seiten auf der Veröffentlichungsebene für den öffentlichen Zugriff.

## Voraussetzungen{#prerequisites-for-previewing-assets-using-Dynamic-Media-with-OpenAPI-capabilities}

Stellen Sie sicher, dass Sie über Folgendes verfügen:

* Sie haben Zugriff auf [!DNL AEM Assets as a Cloud Service].
* Berechtigung zum Bearbeiten der Eigenschaft „Status“ von Assets.
* [Der Wert [!UICONTROL Vorschau] wurde zur Metadateneigenschaft [!UICONTROL Status] hinzugefügt, die auf der Registerkarte [!UICONTROL Allgemein]](/help/assets/metadata-assets-view.md#edit-metadata-forms) des Metadatenformulars verfügbar ist, das auf den Ordner mit den in der Vorschau anzuzeigenden Assets angewendet wurde.
  ![Hinzufügen der Vorschauoption](/help/assets/assets/metedata-form-preview.png)
* Der Schlüssel zum Generieren des Vorschau-Tokens. [Wenden Sie sich an den Adobe-Support](https://helpx.adobe.com/de/contact.html) und fordern Sie den Schlüssel an.

## Anzeigen einer Assets-Vorschau auf der Sites-Vorschauseite {#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities}

Sie können neue Assets oder bereits genehmigte Assets in der Vorschau anzeigen. Genehmigte Assets werden nur auf Ihren Live-Sites-Seiten angezeigt.

Führen Sie die folgenden Schritte aus, um den Asset-Status in [!DNL Assets View] auf „Vorschau“ festzulegen, und veröffentlichen Sie dann Ihre Sites-Authoring-Seite auf der Vorschauebene, um eine Vorschau-URL der Seite zu generieren:

1. Legen Sie den Asset-Status auf **[!UICONTROL Vorschau]** fest, indem Sie die folgenden Schritte ausführen:

   1. Wählen Sie in [!DNL Assets View] **[!UICONTROL Assets]** aus und navigieren Sie zu Ihrem Ordner.
   1. Wählen Sie das in der Vorschau anzuzeigende Asset aus.
   1. Klicken Sie auf **[!UICONTROL Details]**.
   1. Legen Sie im Panel [!UICONTROL Informationen] den **[!UICONTROL Status]** auf **[!UICONTROL Vorschau]** fest und klicken Sie dann auf **[!UICONTROL Speichern]**.
      ![Vorschau](/help/assets/assets/preview-boat-at-bay.png)

1. Navigieren Sie zur Sites-Authoring-Seite. Führen Sie die Schritte im Abschnitt [Zugriff auf Remote-Assets im AEM-Seiteneditor](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor) aus, um über das Panel „Asset-Wähler“ das Asset auszuwählen, das Sie kürzlich auf „Vorschau“ (Status) gesetzt haben.

   >[!NOTE]
   >
   > Der Asset-Wähler zeigt Assets an, deren aktuelle Statusaktualisierung entweder auf „Genehmigt“ oder „Vorschau“ festgelegt ist.

1. Veröffentlichen Sie Ihre Seite auf der Vorschauebene über die Option **[!UICONTROL Veröffentlichung verwalten]**. Führen Sie die Schritte im Abschnitt [Veröffentlichen von Inhalten in der Vorschau](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/previewing-content) aus, um Ihre Seite in der Vorschauebene zu veröffentlichen. Generieren Sie nach dem Veröffentlichen eine Vorschau-URL Ihrer Seite. Auf der Seite „Vorschau“ werden die Assets (mit den neuesten Statusaktualisierungen) Ihrer Sites-Seite angezeigt.

Geben Sie diese Vorschau-URL für Überprüfung und Feedback an die Stakeholder weiter. Stellen Sie sicher, dass Ihre Stakeholder Zugriff auf die Vorschauseite haben. Informationen zum Gewähren von Zugriffs auf die Vorschauseiten finden Sie unter [Zugriff auf den Vorschau-Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments#access-preview-service).

>[!NOTE]
>
>Die [Kernkomponente Bild V3](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/wcm-components/image#version-and-compatibility) unterstützt standardmäßig die Vorschauversion von Assets. Wenn Sie eine Vorschauversion eines Assets (Asset mit Vorschaustatus) im Panel [Asset-Wähler](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/asset-selector-upload) auswählen, rendert die Bildkomponente V3 das Asset automatisch in der Vorschauebene (eine Vorschauversion auf der Sites-Authoring-Seite).

Nachdem Sie die Asset-Version fertiggestellt haben [veröffentlichen Sie Ihre Seiten auf der Veröffentlichungsebene](#publish-your-pages-to-publish-tier) für den öffentlichen Gebrauch.

## Veröffentlichen von Seiten mit genehmigten Assets für die öffentliche Verwendung{#publish-your-pages-to-publish-tier}

Nachdem Sie die Asset-Version für die öffentliche Verwendung fertiggestellt haben, setzen Sie den Asset-Status auf **[!UICONTROL Genehmigt]**. Veröffentlichen Sie dann Ihre Seiten auf der Veröffentlichungsebene. Führen Sie die folgenden Schritte aus, um Ihre Seiten zu veröffentlichen:

1. Befolgen Sie Schritt 1 im obigen Abschnitt [Anzeigen einer Assets-Vorschau auf der Sites-Vorschauseite](#asset-preview-on-sites-pages-using-Dynamic-Media-with-OpenAPI-capabilities), um den Asset-Status zu **[!UICONTROL Genehmigt]** zu ändern.
1. Navigieren Sie zu Ihrer Sites-Authoring-Seite und veröffentlichen Sie sie im [!DNL Publish tier]. Veröffentlichen Sie die Seiten, indem Sie die Schritte im Abschnitt [Veröffentlichen vom Seiteneditor aus](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/page-editor/publishing#publishing-from-the-page-editor) ausführen.
Alternativ können Sie die Schritte im Abschnitt [Veröffentlichen von Seiten über die Sites-Konsole](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/sites-console/publishing-pages#publishing-from-the-sites-console) ausführen, um Ihre Seite über die Sites-Konsole zu veröffentlichen.

   >[!NOTE]
   >
   > Es können nur genehmigte Assets auf der Veröffentlichungsebene bereitgestellt werden. Genehmigen Sie die Assets, bevor Sie Ihre Seite zur öffentlichen Verwendung auf der Veröffentlichungsebene veröffentlichen.

   ![Die Seite wurde veröffentlicht](/help/assets/assets/the-page-has-been-publushed.png)
Nach erfolgreicher Veröffentlichung wird die Bestätigungsmeldung **[!UICONTROL Die Seite wurde veröffentlicht]** angezeigt. Navigieren Sie auf der Veröffentlichungsebene zu Ihrer veröffentlichten Seite, um zu bestätigen, dass die Aktualisierungen live sind und der Inhalt wie erwartet angezeigt wird.
