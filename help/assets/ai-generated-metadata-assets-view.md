---
title: Verbessern der Inhaltssuche mit KI-generierten Metadaten
description: Erfahren Sie, wie Sie die Inhaltssuche mit KI-generierten Metadaten verbessern können
source-git-commit: 3f44e74488fc73c406fefb6decc41782859d029b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 94%

---


# Verbessern der Inhaltssuche mit KI-generierten Metadaten {#ai-smart-tags}

Anstatt dass Sie sich auf die manuelle Eingabe verlassen müssen, weist die KI digitalen Assets automatisch beschreibende Tags zu. Diese KI-generierten Tags verbessern die Metadatenqualität und erleichtern die Suche, Kategorisierung und Empfehlung von Assets. Dieser Ansatz verbessert nicht nur die Effizienz durch das Eliminieren des manuellen Taggings, sondern stellt auch die Konsistenz und Skalierbarkeit über große Mengen digitaler Inhalte hinweg sicher. Wenn das Asset beispielsweise ein Bild ist, kann die KI Objekte, Szenen, Emotionen oder sogar Markenlogos darin identifizieren und relevante Tags wie „Sonnenuntergang“, „Strand“, „Urlaub“ oder „Lächeln“ generieren. KI-generierte Inhalte können die Suche nach Assets verbessern, indem sie sowohl semantische als auch lexikalische Suchtechniken nutzen. Weitere Informationen finden Sie unter [Suchen von Assets](search-assets-view.md). <!--If the asset is a document, AI reads and interprets the text to assign meaningful keywords that summarize its content—such as "climate change," "policy," or "renewable energy.-->

![KI-generierte Metadaten](/help/assets/assets/enhanced-smart-tags.png)

## Wie werden KI-generierte Metadaten aktiviert? {#enable-ai-generated-metadata}

So aktivieren Sie KI-generierte Metadaten:

* Die mindestens erforderliche AEM-Release-Version ist `20626`.


## Verwenden von KI-generierten Metadaten {#using-ai-generated-smart-tags}

<!--[!NOTE]
>
>The enhanced smart tags capability is available only for the newly uploaded assets.
-->

Um die erweiterte Smart-Tags-Funktion zu verwenden, führen Sie die folgenden Schritte aus:

1. Wechseln Sie in der [!DNL Experience Manager]-Benutzeroberfläche zum gewünschten Ordner und klicken Sie auf **[!UICONTROL Assets hinzufügen]**. <!--Alternatively, to update enhanced smart tags in an existing content, click **[!UICONTROL reprocess]**.--> Die kompatiblen Bilddateiformate sind `png`, `jpg`, `jpeg`, `psd`, `tiff`, `gif`, `webp`, `crw`, `cr2`, `3fr`, `nef`, `arw` und `bmp`.

1. Warten Sie, bis das neu hochgeladene Asset verarbeitet wurde. Navigieren Sie abschließend zu den Asset-Details.

1. Navigieren Sie zur Registerkarte **[!UICONTROL KI-generiert]**. Wenn die [!DNL Experience Manager]-Version inkompatibel ist oder nicht aktualisiert wurde, ist diese Registerkarte nicht sichtbar. Die folgenden Felder sind vorhanden:

   * **[!UICONTROL Generierter Titel]:** Der Titel bietet eine klare und knappe Überschrift, die die Kernidee eines hochgeladenen Assets erfasst und es dadurch auf einen Blick leicht verständlich macht. Wenn Sie beim Hinzufügen eines Assets einen Titel angeben (in `dc:title`), wird dieser in der Ansicht zum Durchsuchen von Assets angezeigt. Wenn Sie das Feld leer lassen, wird automatisch ein von der KI generierter Titel zugewiesen.
   * **[!UICONTROL Generierte Beschreibung]:** Die Beschreibung bietet eine kurze, aber informative Zusammenfassung dessen, worum es bei dem Asset geht, und hilft Benutzenden und Suchmodulen, seine Relevanz schnell zu verstehen.
   * **[!UICONTROL Generierte Keywords]:** Die Keywords sind zielgerichtete Begriffe, die die Hauptthemen eines Assets darstellen und beim Tagging und Filtern von Inhalten helfen.

1. [Optional] Sie können zusätzliche Tags hinzufügen oder eigene erstellen, wenn Sie der Meinung sind, dass relevante Tags fehlen. Schreiben Sie dazu Ihre Tags in das Feld **[!UICONTROL Generierte Keywords]** und klicken Sie auf **[!UICONTROL Speichern]**.

Informationen zum Deaktivieren von KI-generierten Metadaten finden Sie unter [Deaktivieren von KI-generierten Metadaten](/help/assets/enhance-content-discovery-with-ai-generated-metadata.md#disable-ai-generated-metadata).
