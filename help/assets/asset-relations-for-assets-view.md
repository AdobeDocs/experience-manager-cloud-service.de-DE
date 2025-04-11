---
title: Asset-Beziehungen
description: Erfahren Sie, wie Sie digitale Assets mit gemeinsamen Attributen verknüpfen. Erstellen Sie außerdem von der Quelle abgeleitete Beziehungen zwischen digitalen Assets mithilfe von Asset-Beziehungen.
role: User
feature: Collaboration,Asset Management
solution: Experience Manager, Experience Manager Assets
source-git-commit: 77dab2731f8d442bf999bf1614ef060944794574
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 59%

---

# Asset-Beziehungen {#related-assets}

Mit [!DNL Adobe Experience Manager Assets] können Sie Assets manuell entsprechend den Anforderungen Ihres Unternehmens verknüpfen. Verwenden Sie hierfür die Funktion „Verknüpfte Assets“. Beispielsweise können Sie einem Asset oder einem Bild/Video mit einer Lizenzdatei zu einem ähnlichen Thema verknüpfen. Sie können Assets verknüpfen, die bestimmte Attribute gemeinsam haben. Mit der Funktion können Sie außerdem Quellbeziehungen/abgeleitete Beziehungen zwischen Assets erstellen. Beispielsweise können Sie PDF-Dateien, die aus einer INDD-Datei generiert wurden, mit der INDD-Quelldatei verknüpfen.

Mit dieser Funktion können Sie eine PDF- oder JPG-Datei mit niedriger Auflösung für Anbieter oder Agenturen freigeben und die hochauflösende INDD-Datei nur auf Anfrage verfügbar machen.

>[!NOTE]
>
>Nur Benutzer mit Bearbeitungsberechtigungen für Assets können die Assets verknüpfen und die Verknüpfung aufheben.

## Schritte zum Verknüpfen von Assets {#steps-to-relate-assets}

1. Öffnen Sie in der [!DNL Experience Manager]-Benutzeroberfläche von die Seite **[!UICONTROL Eigenschaften]** für ein Asset, das Sie verknüpfen möchten.

   ![Öffnen der Seite „Eigenschaften“ eines Assets, um das Asset zu verknüpfen](assets/asset-properties-relate-assets.png)

1. Um dem ausgewählten Asset ein anderes Asset zuzuordnen, klicken Sie auf **[!UICONTROL Asset-Beziehungen]** ![Verknüpfen von Assets](assets/do-not-localize/link-relate.png).
1. Führen Sie einen der folgenden Schritte aus:

   * Um die Quelldatei für das Asset zu verknüpfen, wählen Sie **[!UICONTROL Source hinzufügen]** aus der Liste aus. Sie können nur ein einzelnes Asset als Quelle verknüpfen.
   * Um eine abgeleitete Datei zu verknüpfen, wählen **[!UICONTROL Abgeleitete hinzufügen]** aus der Liste aus. Sie können mehrere Assets in dieser Kategorie verknüpfen.
   * Um eine bidirektionale Beziehung zwischen den Assets zu erstellen, wählen Sie **[!UICONTROL Weitere hinzufügen]** aus der Liste aus. Sie können mehrere Assets in dieser Kategorie verknüpfen.

1. Navigieren Sie **[!UICONTROL Bildschirm &quot;Assets]**&quot; zum Speicherort des Assets, das Sie verknüpfen möchten, und wählen Sie es aus. Sie können ein einzelnes Asset oder mehrere Assets gleichzeitig auswählen, indem Sie beim Klicken die Umschalttaste gedrückt halten, was eines der [unterstützten Dateiformate in der Assets-Ansicht“ ](/help/assets/supported-file-formats-assets-view.md) kann.

   ![Verknüpftes Asset hinzufügen](assets/add-related-asset.png)

1. Klicken Sie **[!UICONTROL Auswählen]**. Je nach Auswahl der Beziehung in Schritt 3 wird das verknüpfte Asset unter einer entsprechenden Kategorie im Abschnitt **[!UICONTROL Asset-Beziehungen]** aufgeführt. Beispiel: Wenn das verknüpfte Asset die Quelldatei des aktuellen Elements ist, wird es unter **[!UICONTROL Quelle]** aufgeführt.

   Beispiel für eine ![Assets-Beziehung](assets/asset-relations-example.png)

1. Klicken Sie auf **[!UICONTROL Verknüpfung aufheben]** ![Verknüpfung von Assets aufheben](assets/do-not-localize/link-unrelate-icon.png) , die für alle zugehörigen Assets in jedem Abschnitt ([!UICONTROL Source], [!UICONTROL Abgeleitet] und [!UICONTROL Andere]) verfügbar sind, um die Verknüpfung eines Assets aufzuheben.

## Übersetzen verknüpfter Assets {#translating-related-assets}

Für die Übersetzungs-Workflows ist die Erstellung von Quellbeziehungen / abgeleiteten Beziehungen zwischen Assets mit der Funktion „Verknüpfte Assets“ nützlich. Wenn Sie für ein abgeleitetes Asset einen Übersetzungs-Workflow ausführen, ruft [!DNL Experience Manager Assets] automatisch beliebige Assets ab, die von der Quelldatei referenziert werden, und nimmt sie in die Übersetzung auf. Auf diese Weise wird das vom Quell-Asset referenzierte Asset zusammen mit dem Quell-Asset und den abgeleiteten Assets übersetzt. Ist die Quelldatei mit einem anderen Asset verknüpft, ruft [!DNL Experience Manager Assets] das referenzierte Asset ab und nimmt es in die Übersetzung auf.

Siehe [Übersetzen von Assets in AEM](/help/assets/translate-assets.md).

## Nächste Schritte {#next-steps}

* Geben Sie Produkt-Feedback über die Option [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht

* Geben Sie Feedback zur Dokumentation durch ![Bearbeiten der Seite](assets/do-not-localize/edit-page.png) über die Option [!UICONTROL Diese Seite bearbeiten] oder durch ![Erstellen eines GitHub-Themas](assets/do-not-localize/github-issue.png) über die Option [!UICONTROL Problem protokollieren] in der rechten Seitenleiste

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/de?support-solution=General#support)

>[!MORELIKETHIS]
>
>* [Anzeigen von Versionen eines Assets](/help/assets/manage-organize-assets-view.md#view-versions)
>* [Übersetzen von Assets in AEM](/help/assets/translate-assets.md)
>* [Unterstützte Dateiformate in der Assets-Ansicht](/help/assets/supported-file-formats-assets-view.md).
