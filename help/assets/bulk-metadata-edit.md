---
title: Massenbearbeitung von Metadaten in [!DNL Assets View]
description: Erfahren Sie, wie Sie einen vordefinierten Satz von Standard-Metadatenfeldern für mehrere Assets aktualisieren können, die im [DNL! Assets-Ansicht] gleichzeitig anzeigen.
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Massenbearbeitung von Metadaten in [!DNL Assets View]{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

Die **[!DNL Bulk Metadata Edit]** Funktion von [!DNL Assets View] ermöglicht es Ihnen, einen vordefinierten Satz von Standard-Metadatenfeldern für mehrere Asset-Dateien gleichzeitig zu bearbeiten. Wählen Sie mehrere Assets aus und führen Sie eine Massenaktualisierung ihres vordefinierten Satzes von Standardmetadaten gleichzeitig durch, anstatt diese Standardmetadaten für jedes Asset einzeln zu aktualisieren. Diese Funktion sorgt für die Effizienz, Konsistenz und Genauigkeit des Satzes von Standard-Metadateneigenschaften in allen großen Sätzen von Assets und verbessert die Durchsuchbarkeit und Organisation dieser Assets.

## Massenbearbeitung von Asset-Metadaten {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

Führen Sie diese Schritte aus, um die Metadaten mehrerer Assets gleichzeitig in großen Mengen zu bearbeiten:

1. Navigieren Sie zu **[!DNL Assets View]** und klicken Sie auf **[!UICONTROL Assets]**.
1. Suchen Sie nach bestimmten Assets oder suchen Sie sie mithilfe von Keywords in der Suchleiste.
1. Wählen Sie die Assets aus und klicken Sie **[!UICONTROL oberen Menü auf]**Massenbearbeitung von Metadaten“.
   ![bulk-metadata-edit](/help/assets/assets/bulk-metadata-edit1.png)
1. Bearbeiten Sie auf [!UICONTROL  Seite „Metadaten bearbeiten] die folgenden Felder im Bedienfeld **[!UICONTROL Eigenschaften]**:
   * **[!UICONTROL Status]:** Wählen Sie einen Status für die ausgewählten Assets aus.
   * **[!UICONTROL Ablaufdatum]:** Legen Sie ein Datum fest, nach dem die Assets nicht mehr gültig oder benötigt werden.
   * **[!UICONTROL Autor]:** Geben Sie den Namen des Autors an.
   * **[!UICONTROL Keywords]:** Fügen Sie bestimmte Begriffe oder Textzeichenfolgen hinzu, die allgemeine Informationen über die Assets bereitstellen, um ihre Auffindbarkeit zu verbessern. Fügen Sie ein Keyword hinzu und drücken Sie **Eingabetaste** oder **Zurück**, um der Liste ein weiteres Keyword hinzuzufügen.
   * **[!UICONTROL Tags]:** Klicken Sie auf ![Massenbearbeitung von ](/help/assets/assets/tags-icon.svg)), um Tags aus den verfügbaren Optionen auszuwählen. Tags bieten spezifischere Informationen über die Assets und verbessern ihre Auffindbarkeit. Auf die ausgewählten Assets bereits angewendete Tags werden im Bedienfeld **[!UICONTROL Eigenschaften]** angezeigt. Wenn Sie die entsprechenden Tags nicht finden können, erstellen Sie sie und weisen Sie sie den ausgewählten Assets zu. Weitere Informationen [ Erstellen und Zuweisen von Tags zu Assets finden  [!DNL Assets view]](/help/assets/tagging-management-assets-view.md) unter „Verwalten von Tags in“.
   * Klicken Sie **[!UICONTROL Speichern]**, um die oben genannten Metadaten-Aktualisierungen auf die ausgewählten Assets anzuwenden. Nach dem Speichern werden **[!UICONTROL Keywords]** und **[!UICONTROL Tags]** angehängt, während die aktualisierten Details für **[!UICONTROL Status]**, **[!UICONTROL Ablaufdatum]** und **[!UICONTROL Autor]** ihre vorhandenen Details überschreiben.
     ![save-bulk-metadata-edit-properties](/help/assets/assets/save-bulk-metadata-edit-properties2.png)

     >[!NOTE]
     >
     >Sie können die Metadaten von jeweils 100 Assets gleichzeitig bearbeiten.

Um die auf ein Asset angewendeten Metadatenaktualisierungen anzuzeigen, navigieren Sie zum [!DNL asset details page] (wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Details]**) und klicken Sie auf ![Massenbearbeitung von Metadaten](/help/assets/assets/info-icon-solid-black.svg), um die Metadaten des Assets im **[!UICONTROL Informations]** Bedienfeld anzuzeigen.

>[!NOTE]
>
>**[!UICONTROL Status]**, **[!UICONTROL Ablaufdatum]**, **[!UICONTROL Autor]**, **[!UICONTROL Keywords]** und **[!UICONTROL Tags]** sind Standard-Metadateneigenschaften, die unabhängig von ordnerspezifischen Metadaten für die Massenbearbeitung verfügbar sind. Diese Metadateneigenschaften werden nur dann auf der [!UICONTROL Asset-Detailseite] angezeigt, wenn sie in dem Metadatenformular enthalten sind, das auf den Ordner des Assets angewendet wurde. Wenn Sie diese Standard-Metadateneigenschaften auf der Seite [!UICONTROL Asset-Details] nicht finden können, bearbeiten Sie das Metadatenformular des Asset-Ordners, um sie einzuschließen. Unter [Metadaten in [!DNL Assets View]](/help/assets/metadata-assets-view.md) erfahren Sie, wie Sie ein Metadatenformular erstellen oder bearbeiten und es auf einen Ordner anwenden.
