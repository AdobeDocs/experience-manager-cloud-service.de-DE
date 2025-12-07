---
title: Verbessern der Inhaltserkennung mit KI-generierten Metadaten in der Admin-Ansicht
description: Erfahren Sie, wie Sie die Inhaltssuche mit KI-generierten Metadaten in der Admin-Ansicht verbessern können
feature: Smart Tags,Tagging
role: Admin,User
source-git-commit: f83324be68bdab65e5c76ef336eb7e4a2e318dd1
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 84%

---


# Verbessern der Inhaltssuche mit KI-generierten Metadaten {#ai-smart-tags}

| Benutzeroberflächen | Artikel-Link |
| -------- | ---------------------------- |
| Assets-Ansicht | [Hier klicken](/help/assets/ai-generated-metadata-assets-view.md) |
| Administratoransicht | Dieser Artikel |

Anstatt dass Sie sich auf die manuelle Eingabe verlassen müssen, weist die KI digitalen Assets automatisch beschreibende Tags zu. Diese KI-generierten Tags verbessern die Metadatenqualität und erleichtern die Suche, Kategorisierung und Empfehlung von Assets. Dieser Ansatz verbessert nicht nur die Effizienz durch das Eliminieren des manuellen Taggings, sondern stellt auch die Konsistenz und Skalierbarkeit über große Mengen digitaler Inhalte hinweg sicher. Wenn das Asset beispielsweise ein Bild ist, kann die KI Objekte, Szenen, Emotionen oder sogar Markenlogos darin identifizieren und relevante Tags wie „Sonnenuntergang“, „Strand“, „Urlaub“ oder „Lächeln“ generieren. KI-generierte Inhalte können die Suche nach Assets verbessern, indem sie sowohl semantische als auch lexikalische Suchtechniken nutzen. Weitere Informationen finden Sie unter [Suchen von Assets](search-assets.md). <!--If the asset is a document, AI reads and interprets the text to assign meaningful keywords that summarize its content—such as "climate change," "policy," or "renewable energy.-->

![Optimierte Smart-Tags](assets/enhanced-smart-tags1.png)

## Wie werden KI-generierte Metadaten aktiviert? {#enable-ai-generated-metadata}

So aktivieren Sie KI-generierte Metadaten:

* Die mindestens erforderliche AEM-Release-Version ist `20626`.

## Konfigurieren KI-generierter Titel {#configure-ai-generated-titles}

Mit AEM können Sie auf der Seite „Asset-Suche“ die Anzeige von Asset-Titeln in der Karten- oder Listenansicht konfigurieren. Sie können den von Ihnen definierten Asset-Titel und einen KI-generieren Titel oder nur einen KI-generierten Titel anzeigen, wenn für das Asset kein Titel vorhanden ist.

So konfigurieren Sie KI-generierte Titel:

1. Navigieren Sie zu **[!UICONTROL Tools > Assets > Assets-Konfigurationen > Smart-Tag-Verbesserungskonfiguration]**.

1. Wählen Sie eine der folgenden Optionen aus:

   * **DC-Titel anzeigen (Standard)**: Geben Sie den Titel im Feld **[!UICONTROL Titel]** an, das in den Asset-Eigenschaften verfügbar ist, um ihn in der Karten- oder Listenansicht anzuzeigen. Wenn der Asset-Titel nicht definiert ist, zeigt AEM Assets den Dateinamen an.

   * **KI-generierten Titel anzeigen**: Zeigt den KI-generierten Titel an und ignoriert den in den Asset-Eigenschaften angegebenen Titel. Wenn für ein Asset kein KI-generierter Titel verfügbar ist, zeigt AEM Assets den Standardtitel des Assets an, der in dessen Eigenschaften verfügbar ist.

   * **KI-generierten Titel nur anzeigen, wenn kein DC-Titel vorhanden ist**: AEM Assets zeigt den KI-generierten Titel nur an, wenn für ein Asset kein Asset-Titel definiert ist.

     ![Konfigurieren von KI-generierten Titeln](assets/configure-title-ai-generated.png)

## Verwenden von KI-generierten Metadaten {#using-ai-generated-smart-tags}

<!--[!NOTE]
>
>The enhanced smart tags capability is available only for the newly uploaded assets.
-->

Um die erweiterte Smart-Tags-Funktion zu verwenden, führen Sie die folgenden Schritte aus:

1. Wechseln Sie in der [!DNL Experience Manager]-Benutzeroberfläche zum gewünschten Ordner und klicken Sie auf **[!UICONTROL Assets hinzufügen]**. <!--Alternatively, to update enhanced smart tags in an existing content, click **[!UICONTROL reprocess]**.--> Die kompatiblen Bilddateiformate sind `png`, `jpg`, `jpeg`, `psd`, `tiff`, `gif`, `webp`, `crw`, `cr2`, `3fr`, `nef`, `arw` und `bmp`.

1. Warten Sie, bis das neu hochgeladene Asset verarbeitet wurde. Navigieren Sie anschließend zu den Asset-Eigenschaften.

1. Navigieren Sie zur Registerkarte **[!UICONTROL KI-generiert]**. Wenn die [!DNL Experience Manager]-Version inkompatibel ist oder nicht aktualisiert wurde, ist diese Registerkarte nicht sichtbar. Die folgenden Felder sind vorhanden:

   * **[!UICONTROL Generierter Titel]:** Der Titel bietet eine klare und knappe Überschrift, die die Kernidee eines hochgeladenen Assets erfasst und es dadurch auf einen Blick leicht verständlich macht. Wenn Sie beim Hinzufügen eines Assets einen Titel angeben (in `dc:title`), wird dieser in der Ansicht zum Durchsuchen von Assets angezeigt. Wenn Sie das Feld leer lassen, wird automatisch ein von der KI generierter Titel zugewiesen.
   * **[!UICONTROL Generierte Beschreibung]:** Die Beschreibung bietet eine kurze, aber informative Zusammenfassung dessen, worum es bei dem Asset geht, und hilft Benutzenden und Suchmodulen, seine Relevanz schnell zu verstehen.
   * **[!UICONTROL Generierte Keywords]:** Die Keywords sind zielgerichtete Begriffe, die die Hauptthemen eines Assets darstellen und beim Tagging und Filtern von Inhalten helfen.

1. [Optional] Sie können zusätzliche Tags hinzufügen oder eigene erstellen, wenn Sie der Meinung sind, dass relevante Tags fehlen. Schreiben Sie dazu Ihre Tags in das Feld **[!UICONTROL Generierte Keywords]** und klicken Sie auf **[!UICONTROL Speichern]**.

## Deaktivieren von KI-generierten Metadaten {#disable-ai-generated-metadata}

So deaktivieren Sie KI-generierte Metadaten:

1. Navigieren Sie zu **[!UICONTROL Tools > Assets > Assets-Konfigurationen > Smart-Tag-Verbesserungskonfiguration]**.

1. Wählen Sie **[!UICONTROL Smart-Tag-Verbesserungen deaktivieren]** aus.

1. Klicken Sie **[!UICONTROL Speichern]** .

Die KI-generierten Metadaten sind für die neuen Assets oder Ordner, die Sie in AEM Assets hochladen, deaktiviert. Die vorhandenen Assets oder Ordner, für die bereits KI-generierte Metadatenfelder generiert wurden, zeigen diese Felder weiterhin an.