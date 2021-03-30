---
title: Ein- und Auschecken von Dateien in [!DNL Assets]
description: Erfahren Sie, wie Sie Assets für die Bearbeitung auschecken und nach Abschluss der Änderungen wieder einchecken können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8db9f899cee8f01a4c2aac93ccecc052f9780bc0
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 49%

---


# Checkin- und Checkout-Dateien in [!DNL Experience Manager] DAM {#check-in-and-check-out-files-in-assets}

Mit [!DNL Adobe Experience Manager Assets] können Sie Assets zum Bearbeiten auschecken und dann wieder einchecken, wenn Sie keine weiteren Änderungen vornehmen möchten. Wenn Sie ein Asset ausgecheckt haben, können nur Sie das Asset bearbeiten, mit Anmerkungen versehen, veröffentlichen, verschieben oder löschen. Beim Auschecken eines Assets wird das Asset gesperrt. Andere Benutzer können für das Asset erst dann einen dieser Vorgänge ausführen, wenn Sie das Asset wieder in [!DNL Assets] einchecken. Allerdings können Sie nach wie vor die Metadaten für das gesperrte Asset ändern.

Um Assets aus-/einchecken zu können, benötigen Sie entsprechenden Schreibzugriff.

Mithilfe dieser Funktion können Sie verhindern, dass Benutzer die von einem Autor vorgenommenen Änderungen überschreiben, wenn mehrere Benutzer Team-übergreifend im Rahmen von Bearbeitungs-Workflows zusammenarbeiten.

## Assets {#checking-out-assets}

1. Wählen Sie in der Benutzeroberfläche [!DNL Assets] das Asset aus, das Sie auschecken möchten. Sie können auch mehrere Assets zum Auschecken auswählen.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Checkout]**. Die Option **[!UICONTROL Checkout]** wechselt zu **[!UICONTROL Checkin]**.
Um zu überprüfen, ob andere Benutzer das von Ihnen ausgecheckte Asset bearbeiten können, melden Sie sich unter einem anderen Benutzernamen an. Das Symbol ![Checkout-Sperrsymbol](assets/do-not-localize/checkout_lock.png) wird auf der Miniaturansicht des Assets angezeigt, das Sie ausgecheckt haben.

   ![Checkout-Symbol in der Ansicht der Karte](assets/checkout-icon-card-view.png)

   Wählen Sie das Asset aus. In der Symbolleiste werden keine Optionen zum Bearbeiten, Kommentieren, Veröffentlichen oder Löschen des Assets angezeigt.

   ![chlimage_1-472](assets/checkout-asset-toolbar-options.png)

   Um die Metadaten für das gesperrte Asset zu bearbeiten, klicken Sie auf **[!UICONTROL Eigenschaften der Ansicht]**.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Asset im Bearbeitungsmodus zu öffnen.

1. Bearbeiten Sie das Asset und speichern Sie die Änderungen. Schneiden Sie beispielsweise das Bild zu und speichern Sie es. Sie können das Asset auch mit Anmerkungen versehen oder es veröffentlichen.

1. Wählen Sie das bearbeitete Asset in der [!DNL Assets]-Oberfläche aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Checkin]**. Das geänderte Asset ist bei [!DNL Assets] eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

## Erzwungenes Einchecken {#forced-check-in}

Administratoren können von anderen Benutzern ausgecheckte Assets einchecken.

1. Melden Sie sich bei [!DNL Assets] als Administrator an.
1. Wählen Sie in der Benutzeroberfläche [!DNL Assets] ein oder mehrere Assets aus, die von anderen Benutzern ausgecheckt wurden.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Sperren]**. Das Asset wird wieder eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

## Best Practices und Einschränkungen {#tips-limitations}

* Es ist möglich, einen *Ordner* zu löschen, der ausgecheckte Asset-Dateien enthält. Bevor Sie einen Ordner löschen, stellen Sie sicher, dass keine digitalen Assets von Benutzern ausgecheckt werden.

>[!MORELIKETHIS]
>
>* [Einchecken und Auschecken der  [!DNL Experience Manager] Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#how-app-works2)
>* [Videoschulung zum Einchecken und Auschecken [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html)

