---
title: Veröffentlichen von Assets, Ordnern und Sammlungen in Brand Portal
description: Veröffentlichen von Assets, Ordnern und Sammlungen in Brand Portal.
contentOwner: Adobe
feature: Brand Portal, Asset Distribution, Configuration
role: User
exl-id: 1cc438bc-8cad-4421-af03-c1f6d750e0a8
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '1287'
ht-degree: 100%

---

# Veröffentlichen von Assets in Brand Portal {#publish-assets-to-brand-portal}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/brandportal/brand-portal-publish-assets) |
| AEM as a Cloud Service | Dieser Artikel |

Als Administrator von Adobe Experience Manager (AEM) Assets können Sie Assets, Ordner und Sammlungen über die AEM Assets Brand Portal-Instanz veröffentlichen. Außerdem können Sie den Veröffentlichungs-Workflow für ein Asset oder einen Ordner zu einem späteren Zeitpunkt einplanen. Nach der Veröffentlichung können die Benutzer von Brand Portal auf die Assets, Ordner und Sammlungen zugreifen und sie an andere Benutzer weiterleiten.

Allerdings müssen Sie zunächst AEM Assets mit Brand Portal konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der von AEM Assets mit Brand Portal](configure-aem-assets-with-brand-portal.md).

Spätere Änderungen am ursprünglichen Asset, Order oder an der ursprünglichen Sammlung in AEM Assets spiegeln sich erst bei erneuter Veröffentlichung von AEM Assets aus in Brand Portal wider. Mit dieser Funktion wird sichergestellt, dass Änderungen im Rahmen der laufenden Bearbeitung nicht in Brand Portal verfügbar sind. Nur genehmigte, von einem Administrator veröffentlichte Änderungen sind in Brand Portal verfügbar.

* [Veröffentlichen von Assets in Brand Portal](#publish-assets-to-bp)
* [Veröffentlichen von Ordnern in Brand Portal](#publish-folders-to-brand-portal)
* [Veröffentlichen von Sammlungen in Brand Portal](#publish-collections-to-brand-portal)

>[!NOTE]
>
>Adobe empfiehlt eine gestaffelte Veröffentlichung, vorzugsweise außerhalb der Spitzenzeiten, sodass die AEM-Autoreninstanz keine übermäßigen Ressourcen belegt.
>>Assets sollten in Stapeln veröffentlicht werden. Die Empfehlung für die Stapelgröße beträgt 15.000.
>> Für [!DNL Experience Manager Assets] as a [!DNL Cloud Service] beträgt die Übertragungsrate unter Laborbedingungen 1000 Assets pro Stunde. Die Rate wird bei einer durchschnittlichen Asset-Größe von 10 MB beobachtet.

## Veröffentlichen von Assets in Brand Portal {#publish-assets-to-bp}

Im Folgenden werden die Schritte zum Veröffentlichen von Assets aus AEM Assets in Brand Portal beschrieben:

1. Öffnen Sie in der Assets-Konsole den übergeordneten Ordner, wählen Sie alle Assets aus, die Sie veröffentlichen möchten, und klicken Sie in der Symbolleiste auf **[!UICONTROL Quick Publish]**.

   ![publish2bp-2](assets/publish2bp.png)

1. Im Folgenden finden Sie zwei Möglichkeiten, Assets zu veröffentlichen:
   * [Sofort veröffentlichen](#publish-to-bp-now) (Assets sofort veröffentlichen)
   * [Später veröffentlichen](#publish-to-bp-later) (Veröffentlichung von Assets terminieren)

### Sofortiges Veröffentlichen von Assets {#publish-to-bp-now}

Um die ausgewählten Assets in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

* Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus. Klicken Sie dann im Menü auf **[!UICONTROL In Brand Portal veröffentlichen]**.

* Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

   1. Wählen Sie unter **[!UICONTROL Aktion]** die Option **[!UICONTROL In Brand Portal veröffentlichen]** aus.

      Wählen Sie unter **[!UICONTROL Planung]** die Option **[!UICONTROL Jetzt]** aus.

      Klicken Sie auf **[!UICONTROL Weiter]**.

   2. Bestätigen Sie Ihre Auswahl in **[!UICONTROL Umfang]** und klicken Sie auf **[!UICONTROL In Brand Portal veröffentlichen]**.

Eine Meldung erscheint, die besagt, dass die Assets zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurden. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um die veröffentlichten Assets zu sehen.

### Assets später veröffentlichen {#publish-to-bp-later}

So planen Sie die Veröffentlichung der Assets in Brand Portal zu einem späteren Zeitpunkt:

1. Wählen Sie die Assets aus, die Sie für die Veröffentlichung planen möchten, und klicken Sie oben in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** die Option **[!UICONTROL In Brand Portal veröffentlichen]** unter **[!UICONTROL Aktion]** aus.

   Wählen Sie **[!UICONTROL Später]** unter **[!UICONTROL Planung]** aus.

   <!--![publishlaterbp-1](assets/publishlaterbp-1.png)-->

   ![Später veröffentlichen](assets/publish-later.png)

1. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie ein **Aktivierungsdatum** aus und geben Sie die Zeit an. Klicken Sie auf **Weiter**.

1. Geben Sie einen **[!UICONTROL Workflow-Titel]** in **[!UICONTROL Workflows]** an. Klicken Sie auf **[!UICONTROL Später veröffentlichen]**.

   <!--![publishworkflow](assets/publishworkflow.png)-->

   ![Workflow veröffentlichen](assets/publish-workflow.png)

>[!NOTE]
>
> * Die vorhandenen Benutzenden, die Teil der DAM-Benutzergruppe sind, haben Lesezugriff auf den Pfad „/conf/global/settings/cloudconfigs/mediaportal“
> * Die neuen Benutzenden (oder Benutzenden ohne Administratorrechte) benötigen die folgenden Berechtigungen für Veröffentlichungen auf dem Brand Portal.
>   > Pfade:
>   > `"/conf/global/settings/cloudconfigs/mediaportal" : jcr:read `
>   >`/libs : jcr:read`
>   >`/conf : jcr:read`
>   >`/content : jcr:read, crx:replicate`
>   >`/content/dam/ : jcr:read,modify, crx:replicate`

## Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal}

Sie können Asset-Ordner sofort veröffentlichen oder deren Veröffentlichung aufheben oder einen späteren Zeitpunkt festlegen.

### Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-bp}

1. Wählen Sie in der Assets-Konsole die Ordner aus, die Sie veröffentlichen möchten, und klicken Sie in der Symbolleiste auf **[!UICONTROL Quick Publish]**.

   ![publish2bp](assets/publish2bp.png)

1. **Ordner jetzt veröffentlichen**

   Um die ausgewählten Ordner in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus.

     Wählen Sie im Menü **[!UICONTROL In Brand Portal veröffentlichen]** aus.

   * Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

      1. Wählen Sie unter **[!UICONTROL Aktion]** die Option **[!UICONTROL In Brand Portal veröffentlichen]** aus.

         Wählen Sie unter **[!UICONTROL Planung]** die Option **[!UICONTROL Jetzt]** aus.

         Klicken Sie auf **Weiter**.

      1. Bestätigen Sie Ihre Auswahl in **[!UICONTROL Umfang]** und klicken Sie auf **[!UICONTROL In Brand Portal veröffentlichen]**.

   Eine Meldung erscheint, die besagt, dass der Ordner zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurde. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um die veröffentlichten Ordner zu sehen.

1. **Ordner später veröffentlichen**
Wenn Sie die Asset-Ordner zu einem späteren Zeitpunkt veröffentlichen möchten:

   1. Wählen Sie die Ordner aus, die Sie für die Veröffentlichung planen möchten, und wählen Sie oben in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.
   1. Wählen Sie unter **[!UICONTROL Aktion]** die Option **[!UICONTROL In Brand Portal veröffentlichen]** aus.

      Wählen Sie unter **[!UICONTROL Planung]** die Option **[!UICONTROL Später]** aus.

   1. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Klicken Sie auf **[!UICONTROL Weiter]**.

      <!--![publishlaterbp](assets/publishlaterbp.png)-->

   ![Ordner später veröffentlichen](assets/publish-later-folder.png)

   1. Bestätigen Sie Ihre Auswahl unter **[!UICONTROL Umfang]**. Klicken Sie auf **[!UICONTROL Weiter]**.

   1. Geben Sie einen Workflow-Titel unter **[!UICONTROL Workflows]** an. Klicken Sie auf **[!UICONTROL Später veröffentlichen]**.

      <!--![manageschedulepub](assets/manageschedulepub.png)-->

   ![Workflow veröffentlichen](assets/publish-workflow.png)

### Ansicht der veröffentlichten Datei oder des Ordners in Brand Portal {#view-published-file-folder}

1. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um die veröffentlichten Assets zu sehen (je nach Ihrem geplanten Zeitpunkt).

   ![bp_landingpage](assets/bp_landingpage.png)

1. Wechseln Sie zur ![Listenansicht](assets/list-view.svg), um den aktuellen Veröffentlichungsstatus des Assets anzuzeigen.

<!--2. On the [Asset Reports page](#https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/admin/asset-reports), you can see the current state of the report job, for example, Success, Failed, Queued, or Scheduled.-->

![generierter Berichtsstatus](assets/report-status.JPG)

### Veröffentlichung von Ordnern in Brand Portal rückgängig machen {#unpublish-folders-from-brand-portal}

Sie können alle in Brand Portal veröffentlichten Assets/Ordner entfernen, indem Sie die Veröffentlichung über die AEM Assets-Instanz rückgängig machen. Nachdem Sie die Veröffentlichung des ursprünglichen Ordners aufgehoben haben, ist dessen Kopie nicht mehr für Brand Portal-Benutzer verfügbar.

Sie können die Veröffentlichung von Asset-Ordnern in Brand Portal sofort aufheben oder einen späteren Zeitpunkt festlegen.

So machen Sie die Veröffentlichung von Assets/Ordnern in Brand Portal rückgängig:

1. Wählen Sie in der Assets-Konsole die Asset-Ordner aus, deren Veröffentlichung Sie aufheben möchten, und klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**.

   ![publish2bp-1](assets/publish2bp.png)

1. **Sofortiges Rückgängigmachen der Veröffentlichung von Assets**

   Wenn Sie die Veröffentlichung des ausgewählten Ordners in Brand Portal sofort rückgängig machen möchten:

   1. Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

   1. Wählen Sie unter **[!UICONTROL Aktion]** die Option **[!UICONTROL Veröffentlichung in Brand Portal rückgängig machen]** aus.

      Wählen Sie unter **[!UICONTROL Planung]** die Option **[!UICONTROL Jetzt]** aus.

      Klicken Sie auf **[!UICONTROL Weiter]**.

   1. Bestätigen Sie Ihre Auswahl in **[!UICONTROL Umfang]** und klicken Sie auf **[!UICONTROL Veröffentlichung in Brand Portal rückgängig machen]**.

      ![confirm-unpublish](assets/confirm-unpublish.png)

1. **Späteres Rückgängigmachen der Veröffentlichung von Assets**

   Wenn Sie die Veröffentlichung eines Asset-Ordners zu einem späteren Zeitpunkt aufheben möchten:

   1. Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

   1. Wählen Sie unter **[!UICONTROL Aktion]** die Option **[!UICONTROL Veröffentlichung in Brand Portal rückgängig machen]** aus.

      Wählen Sie unter **[!UICONTROL Planung]** die Option **[!UICONTROL Später]** aus.

   1. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Klicken Sie auf **[!UICONTROL Weiter]**.

   1. Bestätigen Sie Ihre Auswahl unter **[!UICONTROL Umfang]** und klicken Sie auf **[!UICONTROL Weiter]**.

   1. Geben Sie einen **[!UICONTROL Workflow-Titel]** in **[!UICONTROL Workflows]** an. Klicken Sie auf **[!UICONTROL Veröffentlichung später rückgängig machen]**.

      ![unpublishworkflows](assets/unpublishworkflows.png)

## Veröffentlichen von Sammlungen in Brand Portal {#publish-collections-to-brand-portal}

Sie können Sammlungen in Ihrer AEM Assets-Cloud-Instanz veröffentlichen oder deren Veröffentlichung aufheben.

>[!NOTE]
>
>Inhaltsfragmente können nicht in Brand Portal veröffentlicht werden. Wenn Sie daher in der AEM Assets-Instanz Inhaltsfragmente auswählen, ist die Aktion **[!UICONTROL In Brand Portal veröffentlichen]** nicht verfügbar.
>
>Wenn Sammlungen, die Inhaltsfragmente enthalten, über AEM Assets in Brand Portal veröffentlicht werden, wird der gesamte Inhalt des Ordners mit Ausnahme der Inhaltsfragmente in der Brand Portal-Oberfläche repliziert.

### Veröffentlichen von Sammlungen {#publish-collections}

Im Folgenden werden die Schritte zum Veröffentlichen von Sammlungen aus AEM Assets in Brand Portal beschrieben:

1. Klicken Sie in der Benutzeroberfläche von AEM Assets auf das AEM-Logo.

1. Gehen Sie von der Seite **Navigation** aus zu **[!UICONTROL Assets]** > **[!UICONTROL Sammlungen]**.

1. Wählen Sie in der Konsole **Sammlungen** die Sammlung aus, die Sie in Brand Portal veröffentlichen möchten.

   ![Sammlung auswählen](assets/select_collection.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL In Brand Portal veröffentlichen]**.

1. Klicken Sie im Bestätigungsdialogfeld auf **[!UICONTROL Veröffentlichen]**.

1. Schließen Sie die Bestätigungsmeldung.

   Melden Sie sich bei Brand Portal als Administrator an. Die veröffentlichte Sammlung steht in der Konsole „Sammlungen“ zur Verfügung.

   ![Veröffentlichte Sammlung](assets/published_collection.png)

### Veröffentlichung von Sammlungen aufheben {#unpublish-collections}

Sie können alle in Brand Portal veröffentlichte Sammlungen entfernen, indem Sie die Veröffentlichung über die AEM Assets-Instanz aufheben. Nachdem Sie die Veröffentlichung der ursprünglichen Sammlung rückgängig gemacht haben, ist deren Kopie nicht mehr für Brand Portal-Benutzer verfügbar.

Im Folgenden werden die Schritte zum Aufheben der Veröffentlichung einer Sammlung beschrieben:

1. Wählen Sie über die Konsole **Sammlungen** der AEM Assets-Instanz die Sammlung aus, deren Veröffentlichung rückgängig gemacht werden soll.

   ![Sammlung auswählen](assets/select_collection-1.png)

1. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Aus Brand Portal löschen]**.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Veröffentlichung aufheben]**.
1. Schließen Sie die Bestätigungsmeldung. Die Sammlung wird aus der Brand Portal-Oberfläche entfernt.

Darüber hinaus können Sie Metadatenschemata, Bildvorgaben, Suchfacetten und Tags von AEM Assets in Brand Portal veröffentlichen.

* [Veröffentlichen von Vorgaben, Schemata und Facetten in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html?lang=de)
* [Veröffentlichen von Tags in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html?lang=de)


Weitere Informationen finden Sie in der [Dokumentation zu Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=de).


<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)