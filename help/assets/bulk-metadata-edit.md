---
title: Massenbearbeitung von Metadaten in der Assets-Ansicht
description: Erfahren Sie, wie Sie einen vordefinierten Satz von Standard-Metadatenfeldern für mehrere Assets aktualisieren können, die gleichzeitig in der Assets-Ansicht verfügbar sind.
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 5%

---

# Massenbearbeitung von Metadaten in der Assets-Ansicht{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

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

Mit **Funktion „Massenbearbeitung von**&quot; in der Assets-Ansicht können Benutzende einen vordefinierten Satz von Standard-Metadatenfeldern für mehrere Asset-Dateien gleichzeitig bearbeiten. Wählen Sie mehrere Assets aus und führen Sie eine Massenaktualisierung ihres vordefinierten Satzes von Standardmetadaten gleichzeitig durch, anstatt diese Standardmetadaten für jedes Asset einzeln zu aktualisieren. Diese Funktion verbessert die Effizienz, Konsistenz und Genauigkeit von Standard-Metadateneigenschaften in einem großen Satz von Assets und verbessert so die Durchsuchbarkeit und Organisation von Assets.

## Massenbearbeitung von Asset-Metadaten {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

Führen Sie diese Schritte aus, um die Metadaten mehrerer Assets gleichzeitig in großen Mengen zu bearbeiten:

1. Klicken Sie in der Assets-Ansicht auf **Assets**.
1. Suchen Sie nach bestimmten Assets oder suchen Sie sie mithilfe von Keywords in der Suchleiste.
1. Wählen Sie die Assets aus und klicken Sie **oberen Menü auf**Massenbearbeitung von Metadaten“.
   ![bulk-metadata-edit](/help/assets/assets/bulk-metadata-edit1.png)
1. Bearbeiten Sie auf der Seite „Metadaten bearbeiten“ die folgenden Felder im Bedienfeld **Eigenschaften**:
   * **Status** Wählen Sie einen Status für die ausgewählten Assets aus.
   * **Ablaufdatum:** Sie ein Datum ein, nach dem die Assets nicht mehr gültig oder benötigt werden.
   * **Autor:** Geben Sie den Namen des Autors an.
   * **Schlüsselwörter:** Fügen Sie bestimmte Begriffe oder Textzeichenfolgen hinzu, die allgemeine Informationen über die Assets enthalten, um ihre Auffindbarkeit zu verbessern. Fügen Sie ein Keyword hinzu und drücken Sie die Eingabetaste oder die Eingabetaste, um der Liste ein weiteres Keyword hinzuzufügen.
   * **Tags:** Klicken Sie auf ![Tags-Symbol](/help/assets/assets/tags-icon.svg), um Tags aus den verfügbaren Optionen auszuwählen. Tags bieten spezifischere Informationen über die Assets und verbessern ihre Auffindbarkeit. Auf die ausgewählten Assets bereits angewendete Tags werden im Bedienfeld **Eigenschaften** angezeigt. Wenn Sie die entsprechenden Tags nicht finden können, erstellen Sie sie und weisen Sie sie den ausgewählten Assets zu. Weitere Informationen [ Erstellen und Zuweisen von Tags zu Assets ](/help/assets/tagging-management-assets-view.md) Sie unter „Verwalten von Tags in der Assets-Ansicht .
   * Klicken Sie **Speichern**, um die oben genannten Metadaten-Aktualisierungen auf die ausgewählten Assets anzuwenden. Nach dem Speichern werden Keywords und Tags angehängt, während die aktualisierten Details für Status, Ablaufdatum und Autor ihre vorhandenen Details überschreiben.
     ![save-bulk-metadata-edit-properties](/help/assets/assets/save-bulk-metadata-edit-properties2.png)

     >[!NOTE]
     >
     >Sie können die Metadaten von jeweils 100 Assets gleichzeitig bearbeiten.

Um die auf ein Asset angewendeten Metadaten-Aktualisierungen anzuzeigen, navigieren Sie zur Asset-Detailseite (wählen Sie das Asset aus und klicken Sie auf **Details**) und klicken Sie auf ![](/help/assets/assets/info-icon-solid-black.svg), um die Metadaten des Assets im Bedienfeld **Informationen** anzuzeigen.

>[!NOTE]
>
>**Status**, **Ablaufdatum**, **Autor**, **Keywords** und **Tags** sind Standard-Metadateneigenschaften, die unabhängig von ordnerspezifischen Metadaten für die Massenbearbeitung verfügbar sind. Diese Metadateneigenschaften werden nur dann auf der Seite mit den Asset-Details angezeigt, wenn sie in dem Metadatenformular enthalten sind, das auf den Ordner des Assets angewendet wurde. Wenn Sie diese Standard-Metadateneigenschaften auf der Seite mit den Asset-Details nicht finden können, bearbeiten Sie das Metadatenformular des Asset-Ordners, um sie einzuschließen. Unter [Metadaten in der Assets-Ansicht](/help/assets/metadata-assets-view.md) erfahren Sie, wie Sie ein Metadatenformular erstellen oder bearbeiten und es auf einen Ordner anwenden.
