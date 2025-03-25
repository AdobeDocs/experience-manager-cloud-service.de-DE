---
title: Massenbearbeitung von Metadaten in [DNL! Assets [Ansicht]
description: Erfahren Sie, wie Sie einen vordefinierten Satz von Standard-Metadatenfeldern für mehrere Assets aktualisieren können, die im [DNL! Assets-Ansicht] gleichzeitig anzeigen.
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: 9b5191bd05bfb06fb4eb1a9b710b98cc132ffeda
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 3%

---

# Massenbearbeitung von Metadaten in [!DNL Assets View]{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

Die **[!DNL Bulk Metadata Edit]** Funktion von [!DNL Assets View] ermöglicht es Ihnen, einen vordefinierten Satz von Standard-Metadatenfeldern für mehrere Asset-Dateien gleichzeitig zu bearbeiten. Wählen Sie mehrere Assets aus und führen Sie eine Massenaktualisierung ihres vordefinierten Satzes von Standardmetadaten gleichzeitig durch, anstatt diese Standardmetadaten für jedes Asset einzeln zu aktualisieren. Diese Funktion, mit der Sie den Standardsatz von Metadateneigenschaften für mehrere Assets gleichzeitig in großen Mengen bearbeiten können, sorgt für die Effizienz, Konsistenz und Genauigkeit dieser Standard-Metadateneigenschaften in allen Assets, wodurch die Durchsuchbarkeit und Organisation dieser Assets verbessert wird.

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
