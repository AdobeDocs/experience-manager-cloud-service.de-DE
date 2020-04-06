---
title: Veröffentlichen von Assets, Ordnern und Sammlungen im Markenportal
seo-title: Veröffentlichen von Assets, Ordnern und Sammlungen im Markenportal
description: Erfahren Sie, wie Sie Assets, Ordner und Sammlungen im Markenportal veröffentlichen und die Veröffentlichung rückgängig machen.
seo-description: Erfahren Sie, wie Sie Assets, Ordner und Sammlungen im Markenportal veröffentlichen und die Veröffentlichung rückgängig machen.
uuid: null
contentOwner: Vishabh Gupta
products: SG_EXPERIENCEMANAGER/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: null
translation-type: tm+mt
source-git-commit: 7a98b0f77177612bf81d904e8b0fb3645baf1435

---


# Veröffentlichen von Assets, Ordnern und Sammlungen im Markenportal {#publish-aem-assets-to-brand-portal}

Als Asset-Administrator von Adobe Experience Manager (AEM) können Sie Assets, Ordner und Sammlungen in der AEM Assets Brand Portal-Instanz veröffentlichen. Außerdem können Sie den Veröffentlichungsarbeitsablauf für ein Asset oder einen Ordner auf ein späteres Datum oder eine spätere Uhrzeit einstellen. Nach der Veröffentlichung können die Benutzer des Markenportals auf die Assets, Ordner und Sammlungen zugreifen und sie an andere Benutzer weiterleiten.

Zunächst müssen Sie jedoch AEM Assets mit dem Markenportal konfigurieren. For details, see [Configure AEM Assets with Brand Portal](configure-aem-assets-with-brand-portal.md).

Wenn Sie nachfolgende Änderungen am ursprünglichen Asset, Ordner oder der Sammlung in AEM Assets vornehmen, werden die Änderungen erst dann im Markenportal angezeigt, wenn Sie die Veröffentlichung von AEM Assets erneut durchführen. Mit dieser Funktion wird sichergestellt, dass derzeit vorgenommene Änderungen nicht im Markenportal verfügbar sind. Nur genehmigte Änderungen, die von einem Administrator veröffentlicht werden, sind im Markenportal verfügbar.

* [Veröffentlichen von Assets in Brand Portal](#publish-assets-to-bp)
* [Veröffentlichen von Ordnern in Brand Portal](#publish-folders-to-brand-portal)
* [Veröffentlichen von Sammlungen in Brand Portal](#publish-collections-to-brand-portal)

>[!NOTE]
>
>Adobe empfiehlt eine gestaffelte Veröffentlichung, vorzugsweise außerhalb der Spitzenzeiten, sodass die AEM-Autoreninstanz keine übermäßigen Ressourcen belegt.


## Veröffentlichen von Assets in Brand Portal {#publish-assets-to-bp}

Im Folgenden werden die Schritte zum Veröffentlichen von Assets aus AEM Assets im Markenportal beschrieben:

1. Öffnen Sie in der Assets-Konsole den übergeordneten Ordner, wählen Sie alle Assets aus, die Sie veröffentlichen möchten, und klicken Sie in der Symbolleiste auf &quot; **[!UICONTROL Schnelle Veröffentlichung]** &quot;.


   ![publish2bp-2](assets/publish2bp.png)

1. Im Folgenden finden Sie zwei Möglichkeiten, Assets zu veröffentlichen:
   * [Jetzt](#publish-to-bp-now) veröffentlichen (Assets sofort veröffentlichen)
   * [Später](#publish-to-bp-now) veröffentlichen (Planen der Veröffentlichung von Assets)

### Assets jetzt veröffentlichen {#publish-to-bp-now}

Um die ausgewählten Assets in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

* From the toolbar, select **[!UICONTROL Quick Publish]**. From the menu, click **[!UICONTROL Publish to Brand Portal]**.

* From the toolbar, select **[!UICONTROL Manage Publication]**.

   1. From **[!UICONTROL Action]**, select **[!UICONTROL Publish to Brand Portal]**, and from **[!UICONTROL Scheduling]**, select **[!UICONTROL Now]**. Klicken Sie auf **[!UICONTROL Weiter]**.

   2. Bestätigen Sie Ihre Auswahl in **[!UICONTROL Scope]** und klicken Sie auf In Markenportal **[!UICONTROL veröffentlichen]**.

Eine Meldung erscheint, die besagt, dass die Assets zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurden. Melden Sie sich bei der Oberfläche des Markenportals an, um die veröffentlichten Assets anzuzeigen.

### Assets später veröffentlichen {#publish-to-bp-later}

So planen Sie die Veröffentlichung der Assets in Brand Portal zu einem späteren Zeitpunkt:

1. Wählen Sie die Assets aus, die Sie für die Veröffentlichung planen möchten, und wählen Sie oben in der Symbolleiste die Option &quot;Veröffentlichung **[!UICONTROL verwalten]** &quot;aus.

1. On **[!UICONTROL Manage Publication]** page, select **[!UICONTROL Publish to Brand Portal]** from **[!UICONTROL Action]**, and select **[!UICONTROL Later]** from **[!UICONTROL Scheduling]**.

   ![publishlatbp-1](assets/publishlaterbp-1.png)

1. Select an **Activation date** and specify time. Klicken Sie auf **Weiter**.

1. Specify a **[!UICONTROL Workflow title]** in **[!UICONTROL Workflows]**. Click **[!UICONTROL Publish Later]**.

   ![publishworkflow](assets/publishworkflow.png)

Melden Sie sich bei der Oberfläche des Markenportals an, um zu sehen, ob die veröffentlichten Assets verfügbar sind.

![bp_landing_page](assets/bp_landing_page.png)

<!--

End - Publish assets to Brand Portal
Start- Publish folders to Brand Portal
-->


## Veröffentlichen von Ordnern in Brand Portal{#publish-folders-to-brand-portal}

Sie können Asset-Ordner sofort veröffentlichen oder die Veröffentlichung rückgängig machen oder einen späteren Zeitpunkt planen.

### Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal-1}

1. Wählen Sie in der Assets-Konsole die zu veröffentlichenden Ordner aus und klicken Sie in der Symbolleiste auf die Option &quot; **[!UICONTROL Schnelle Veröffentlichung]** &quot;.

   ![publish2bp](assets/publish2bp.png)

1. **Ordner jetzt veröffentlichen** 

   Um die ausgewählten Ordner in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

   * From the toolbar, select **[!UICONTROL Quick Publish]**. Wählen Sie im Menü **[!UICONTROL Im Brand Portal veröffentlichen]** aus.

   * From the toolbar, select **[!UICONTROL Manage Publication]**.

      1. Wählen Sie in **[!UICONTROL Aktion]** die Option In Markenportal **[!UICONTROL veröffentlichen]**. Wählen Sie in **[!UICONTROL Planung]** die Option **[!UICONTROL Jetzt]**. Klicken Sie auf **[!UICONTROL Weiter]**.
      1. Bestätigen Sie Ihre Auswahl in **[!UICONTROL Scope]** und klicken Sie auf In Markenportal **[!UICONTROL veröffentlichen]**.
   Eine Meldung erscheint, die besagt, dass der Ordner zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurde. Melden Sie sich bei Ihrer Markenportal-Oberfläche an, um den veröffentlichten Ordner anzuzeigen.

1. **Ordner später veröffentlichen**

   So planen Sie die Veröffentlichung der Asset-Ordner zu einem späteren Zeitpunkt.

   1. Wählen Sie die Ordner, die Sie für die Veröffentlichung planen möchten, und wählen Sie oben in der Symbolleiste die Option &quot;Veröffentlichung **[!UICONTROL verwalten]** &quot;aus.
   1. From **[!UICONTROL Action]**, select **[!UICONTROL Publish to Brand Portal]**, and from **[!UICONTROL Scheduling]** select **[!UICONTROL Later]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   1. Select an **[!UICONTROL Activation date]** and specify time. Klicken Sie auf **[!UICONTROL Weiter]**.
   1. Confirm your selection in **[!UICONTROL Scope]**. Klicken Sie auf **[!UICONTROL Weiter]**.
   1. Specify a Workflow title under **[!UICONTROL Workflows]**. Click **[!UICONTROL Publish Later]**.

      ![manageschedulepub](assets/manageschedulepub.png)

### Veröffentlichung von Ordnern in Brand Portal rückgängig machen {#unpublish-folders-from-brand-portal}

Sie können jeden im Markenportal veröffentlichten Asset-Ordner entfernen, indem Sie die Veröffentlichung in Ihrer AEM Assets-Instanz rückgängig machen. Nachdem Sie die Veröffentlichung des Originalordners rückgängig gemacht haben, steht die Kopie nicht mehr den Benutzern des Markenportals zur Verfügung.

Sie können die Veröffentlichung von Asset-Ordnern aus dem Markenportal sofort rückgängig machen oder sie für einen späteren Zeitpunkt planen.

So machen Sie die Veröffentlichung von Assets/Ordnern in Brand Portal rückgängig:

1. Wählen Sie in der AEM Assets-Konsole den Ordner aus, dessen Veröffentlichung Sie rückgängig machen möchten.

   ![publish2bp-1](assets/publish2bp.png)

1. From the toolbar, Click **[!UICONTROL Manage Publication]**.

1. **Veröffentlichung in Brand Portal jetzt rückgängig machen**

   So heben Sie die Veröffentlichung des ausgewählten Ordners im Markenportal sofort auf:

   1. From the toolbar, select **Manage Publication**.
   1. From **Action**, select **Unpublish from Brand Portal**, and from **Scheduling**, select **Now**. Klicken Sie auf **Weiter.**
   1. Bestätigen Sie Ihre Auswahl in **Scope** und klicken Sie auf **Veröffentlichung im Markenportal** rückgängig machen.
   ![verify-unpublish](assets/confirm-unpublish.png)

1. **Rückgängigmachen der Veröffentlichung aus dem Markenportal später**

   So planen Sie das Rückgängigmachen der Veröffentlichung eines Ordners aus dem Markenportal auf ein späteres Datum und eine spätere Uhrzeit:

   1. From the toolbar, select **Manage Publication**.
   1. From **Action**, select **Unpublish from Brand Portal**, and from **Scheduling** select **Later**.
   1. Select an **Activation date** and specify the time. Klicken Sie auf **Weiter**.
   1. Bestätigen Sie Ihre Auswahl in **Scope** und klicken Sie auf **Weiter**.
   1. Specify a **Workflow title** in **Workflows**. Click **Unpublish Later.**

      ![unpublishworkflows](assets/unpublishworkflows.png)


<!--
End - Publish folders to Brand Portal
Start- Publish Collections to Brand Portal

-->

## Veröffentlichen von Sammlungen in Brand Portal {#publish-collections-to-brand-portal}

Sie können Sammlungen in Ihrer AEM Assets-Instanz veröffentlichen oder die Veröffentlichung rückgängig machen.

>[!NOTE]
>
>Inhaltsfragmente können nicht in Brand Portal veröffentlicht werden. Therefore, if you select content fragment(s) in AEM Asset, then **[!UICONTROL Publish to Brand Portal]** action is not available.
>
>Wenn Sammlungen, die Inhaltsfragmente enthalten, aus AEM Assets in Brand Portal veröffentlicht werden, wird der gesamte Inhalt des Ordners mit Ausnahme von Inhaltsfragmenten auf die Benutzeroberfläche des Brand Portal repliziert.

### Veröffentlichen von Sammlungen {#publish-a-collection-to-brand-portal}

Im Folgenden werden die Schritte zum Veröffentlichen von Sammlungen aus AEM Assets im Markenportal beschrieben:

1. Klicken Sie in der AEM Assets-Benutzeroberfläche auf AEM-Logo.
1. From **Navigation** page, go to **[!UICONTROL Assets]** > **[!UICONTROL Collections]**.
1. From the **Collections** console, select the collections that you want to publish to Brand Portal.

   ![select_collection](assets/select_collection.png)

1. From the toolbar, click **[!UICONTROL Publish to Brand Portal]**.
1. In the confirmation dialog, click **[!UICONTROL Publish]**.
1. Schließen Sie die Bestätigungsmeldung.

   Melden Sie sich beim Markenportal als Administrator an. The published collection is available in the **[!UICONTROL Collections]** console.

   ![veröffentlichte Sammlung](assets/published_collection.png)

## Veröffentlichung von Sammlungen rückgängig machen {#unpublish-collections}

Sie können alle im Markenportal veröffentlichten Sammlungen entfernen, indem Sie die Veröffentlichung in Ihrer AEM Assets-Instanz rückgängig machen. Nachdem Sie die Veröffentlichung der ursprünglichen Sammlung rückgängig gemacht haben, ist die Kopie für die Benutzer des Markenportals nicht mehr verfügbar.

Im Folgenden werden die Schritte zum Rückgängigmachen der Veröffentlichung von Sammlungen beschrieben:

1. Wählen Sie in der Sammlungskonsole Ihrer AEM Assets-Instanz die Sammlung aus, deren Veröffentlichung Sie rückgängig machen möchten.

   ![select_collection-1](assets/select_collection-1.png)

1. From the toolbar, click **[!UICONTROL Remove from Brand Portal]** icon.
1. In the dialog, click **[!UICONTROL Unpublish]**.
1. Schließen Sie die Bestätigungsmeldung. Die Sammlung wird aus der Benutzeroberfläche des Markenportals entfernt.

Weitere Informationen zur Verteilung von Assets, Ordnern und Sammlungen an Endbenutzer finden Sie in der Dokumentation [zum](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) Markenportal.

<!--

End - Publish Collections to Brand Portal

-->

