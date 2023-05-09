---
title: Verfassen von kontextsensitiver Hilfe für Formularfelder
seo-title: Authoring in-context help for form fields
description: Mit AEM Forms können Sie Feldern und Bereichen in adaptiven Formularen kontextbezogene Hilfe als Text oder Rich-Media (einschließlich Videos) hinzufügen.
seo-description: AEM Forms allows you to add in-context help to Adaptive Form fields and panels, as text or rich media, including videos.
uuid: 1865bf7b-66fc-4f89-bd98-904daa409320
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 78000342-a6a7-4c2e-acab-a88851b82c2a
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 58%

---


# Verfassen von kontextsensitiver Hilfe für Formularfelder {#authoring-in-context-help-for-form-fields}

## Einführung {#introduction}

Es gibt Situationen, in denen sich Endbenutzer, die ein Formular ausfüllen, nicht sicher sind, wie Informationen in ein bestimmtes Formularfeld einzugeben sind. Für solche Fälle bieten adaptive Formulare die Möglichkeit, Text oder interaktive kontextbezogene Hilfe zu einem Formularfeld hinzuzufügen. Dadurch wird das Ausfüllen des Formulars verbessert und Unklarheiten für Endbenutzer vermieden.

In diesem Artikel wird erläutert, wie Formularautoren kontextbezogene Hilfe beim Authoring von Adaptive Forms hinzufügen können.

## Hinzufügen kontextbezogener Hilfe {#add-in-context-help}

Sie können kontextbezogene Hilfe mithilfe der folgenden Optionen im Abschnitt Hilfe-Inhalt auf der Registerkarte Eigenschaften in der Seitenleiste angeben.

* [Kurzbeschreibung](authoring-in-field-help.md#p-short-description-p)
* [Lange Beschreibung](authoring-in-field-help.md#p-long-description-p)

![Kontextbezogene Hilfe für Formularfelder](assets/descriptions.png)

>[!NOTE]
>
>Eine lange Beschreibung überschreibt die Kurzbeschreibung. Wenn Sie beide Optionen angegeben haben, wird nur die lange Beschreibung angezeigt.

### Kurzbeschreibung {#short-description}

Das Feld &quot;Kurzbeschreibung&quot;dient dazu, schnelle und kurze Hinweise zum Ausfüllen eines Formularfelds bereitzustellen. Der im Feld Kurzbeschreibung angegebene Text wird als QuickInfo angezeigt, wenn Sie den Mauszeiger über das Feld bewegen.

![Kurzbeschreibung zum Hinzufügen von kontextbezogener Hilfe für Formularfelder](assets/tooltip.png)

>[!NOTE]
>
>Wählen Sie **Kurzbeschreibung immer anzeigen** aus, um den Hilfetext unterhalb des Felds immer anzuzeigen.

![Dauerhafte kontextbezogene kurze Hilfe unter dem Feld](assets/short1.png)

### Lange Beschreibung {#long-description}

Sie können das Feld „Lange Beschreibung“ verwenden, um langen Text anzugeben oder Rich-Media-Inhalte (einschließlich Videos) als kontextbezogene Hilfe einzubetten. Beispiel: Das folgende Bild zeigt, wie Sie ein Video als kontextbezogene Hilfe einbetten können.

![Hinzufügen von Rich-Media als kontextbezogene Hilfe für Formularfelder](assets/long-descriptions.png)

Durch Hinzufügen einer langen Beschreibung wird eine **?** neben dem Feld. Durch Klicken auf das Symbol wird der Inhalt angezeigt, der im Abschnitt &quot;Lange Beschreibung&quot;hinzugefügt wurde.

![Beispiel für kontextbezogene Rich-Media-Hilfe](assets/photoshop.png)

### Hilfe auf Bereichsebene {#panel-level-help}

Zusätzlich zur kontextbezogenen Hilfe für Formularfelder können Sie auf der Registerkarte „Hilfeinhalt“ des Dialogfelds zum Bearbeiten von Bereichen auch Hilfe auf Bereichsebene angeben.

![Hinzufügen von kontextbezogener Hilfe für einen Formularbereich](assets/panel-level-help.png)

Wenn Sie Hilfe für das Bedienfeld hinzufügen, wird eine **?** neben der Bedienfeldbeschreibung. Durch Klicken auf das Symbol wird der Inhalt angezeigt, der im Abschnitt &quot;Hilfe-Inhalt&quot;des Dialogfelds zum Bearbeiten des Bedienfelds hinzugefügt wurde.

![Beispiel für kontextbezogene Hilfe auf Formularbereichsebene](assets/photoshop-1.png)

