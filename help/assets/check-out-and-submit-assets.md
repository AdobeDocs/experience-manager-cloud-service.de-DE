---
title: Ein- und Auschecken von Dateien in  [!DNL Assets]
description: Erfahren Sie, wie Sie Assets für die Bearbeitung auschecken und nach Abschluss der Änderungen wieder einchecken können.
contentOwner: AG
feature: Asset Management
role: User
exl-id: adb94a31-d949-4f4a-89bc-44f1b4f67e14
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '471'
ht-degree: 100%

---

# Ein- und Auschecken von Dateien im DAM von [!DNL Experience Manager] {#check-in-and-check-out-files-in-assets}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Mit [!DNL Adobe Experience Manager Assets] können Sie Assets zum Bearbeiten auschecken und dann wieder einchecken, wenn Sie keine weiteren Änderungen vornehmen möchten. Wenn Sie ein Asset ausgecheckt haben, können nur Sie das Asset bearbeiten, mit Anmerkungen versehen, veröffentlichen, verschieben oder löschen. Beim Auschecken eines Assets wird das Asset gesperrt. Andere Benutzer können diese Vorgänge erst dann für das Asset ausführen, wenn Sie das Asset wieder in [!DNL Assets] eingecheckt haben. Allerdings können Sie nach wie vor die Metadaten für das gesperrte Asset ändern.

Um Assets aus-/einchecken zu können, benötigen Sie entsprechenden Schreibzugriff.

Mithilfe dieser Funktion können Sie verhindern, dass Benutzer die von einem Autor vorgenommenen Änderungen überschreiben, wenn mehrere Benutzer Team-übergreifend im Rahmen von Bearbeitungs-Workflows zusammenarbeiten.

## Auschecken von Assets {#checking-out-assets}

1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche das Asset aus, das ausgecheckt werden soll. Sie können auch mehrere Assets zum Auschecken auswählen.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Auschecken]**. Die Option **[!UICONTROL Auschecken]** wird zu **[!UICONTROL Einchecken]** umgeschaltet.
Um zu überprüfen, ob andere Benutzer das von Ihnen ausgecheckte Asset bearbeiten können, melden Sie sich unter einem anderen Benutzernamen an. Das Symbol ![Checkout-Sperrsymbol](assets/do-not-localize/checkout_lock.png) wird auf der Miniatur des Assets angezeigt, das Sie ausgecheckt haben.

   ![Checkout-Symbol in der Kartenansicht](assets/checkout-icon-card-view.png)

   Wählen Sie das Asset aus. In der Symbolleiste werden keine Optionen zum Bearbeiten, Kommentieren, Veröffentlichen oder Löschen des Assets angezeigt.

   ![chlimage_1-472](assets/checkout-asset-toolbar-options.png)

   Um die Metadaten für das gesperrte Asset zu bearbeiten, klicken Sie auf **[!UICONTROL Eigenschaften anzeigen]**.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Asset im Bearbeitungsmodus zu öffnen.

1. Bearbeiten Sie das Asset und speichern Sie die Änderungen. Schneiden Sie beispielsweise das Bild zu und speichern Sie es. Sie können das Asset auch mit Anmerkungen versehen oder es veröffentlichen.

1. Wählen Sie das bearbeitete Asset in der [!DNL Assets]-Benutzeroberfläche aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Einchecken]**. Das geänderte Asset wird in [!DNL Assets] eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

## Erzwungenes Einchecken {#forced-check-in}

Admins können von anderen Benutzern ausgecheckte Assets einchecken.

1. Melden Sie sich bei [!DNL Assets] als Admin an.
1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche ein bzw. mehrere Assets, das bzw. die von anderen Benutzern ausgecheckt wurde(n).

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Sperre aufheben]**. Das Asset wird wieder eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

## Best Practices und Einschränkungen {#tips-limitations}

* Es ist möglich, einen *Ordner* zu löschen, der ausgecheckte Asset-Dateien enthält. Stellen Sie vor dem Löschen eines Ordners sicher, dass er keine von Benutzern ausgecheckte digitale Assets enthält.

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

>[!MORELIKETHIS]
>
>* [Einchecken und Auschecken in der [!DNL Experience Manager] Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#how-app-works2)
>* [Video-Tutorial zum Ein- und Auschecken in  [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html?lang=de)
