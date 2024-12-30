---
title: Hinzufügen von Hilfetext für Felder in adaptiven AEM-Formularen
description: Mit AEM Forms können Sie kontextbezogene Hilfe zu Feldern und Panels in adaptiven Formularen als Text oder Rich Media, einschließlich Videos, hinzufügen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
exl-id: 9abc6e42-3b53-4dca-bd6a-ced5cf6c6ac4
source-git-commit: a9adbb1886dcfedfc3fccb6f56939c46ba1365ee
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 100%

---

# Verfassen von kontextsensitiver Hilfe für Formularfelder{#authoring-in-context-help-for-form-fields}

## Einführung {#introduction}

Es gibt Situationen, in denen sich Endbenutzer, die ein Formular ausfüllen, nicht sicher sind, wie Informationen in ein bestimmtes Formularfeld einzugeben sind. Für solche Fälle bieten adaptive Formulare die Möglichkeit, Text oder interaktive kontextbezogene Hilfe zu einem Formularfeld hinzuzufügen. Dies erleichtert das Ausfüllen des Formulars und vermeidet potenzielle Uneindeutigkeiten für Endbenutzende.

Dieser Artikel erläutert, wie Autorinnen und Autoren von Formularen kontextbezogene Hilfe beim Erstellen adaptiver Formulare hinzufügen können.

## Hinzufügen kontextbezogener Hilfe {#add-in-context-help}

Sie können kontextbezogene Hilfe mit den folgenden Optionen im Abschnitt „Hilfeinhalt“ der Registerkarte „Eigenschaften“ in der Seitenleiste angeben.

* [Kurzbeschreibung](authoring-in-field-help.md#p-short-description-p)
* [Lange Beschreibung](authoring-in-field-help.md#p-long-description-p)

![Kontextbezogene Hilfe für Formularfelder](assets/descriptions.png)

>[!NOTE]
>
>Die lange Beschreibung überschreibt die Kurzbeschreibung. Wenn Sie beide Optionen angegeben haben, wird nur die lange Beschreibung angezeigt.

### Kurzbeschreibung {#short-description}

Das Feld „Kurzbeschreibung“ ermöglicht die Angabe schneller und kurzer Hinweise zum Ausfüllen eines Formularfelds. Der im Feld „Kurzbeschreibung“ eingegebene Text wird beim Bewegen des Mauszeigers über das Feld als QuickInfo angezeigt.

![Kurzbeschreibung zum Hinzufügen von kontextbezogener Hilfe für Formularfelder](assets/tooltip.png)

>[!NOTE]
>
>Wählen Sie **Kurzbeschreibung immer anzeigen** aus, um den Hilfetext unterhalb des Felds immer anzuzeigen.

![Dauerhafte kontextbezogene kurze Hilfe unter dem Feld](assets/short1.png)

### Lange Beschreibung {#long-description}

Sie können das Feld „Lange Beschreibung“ verwenden, um langen Text anzugeben oder Rich-Media-Inhalte (einschließlich Videos) als kontextbezogene Hilfe einzubetten. Beispiel: Das folgende Bild zeigt, wie Sie ein Video als kontextbezogene Hilfe einbetten können.

![Hinzufügen von Rich-Media als kontextbezogene Hilfe für Formularfelder](assets/long-descriptions.png)

Wenn Sie eine lange Beschreibung hinzufügen, wird das Symbol **?** neben dem Feld angezeigt. Durch Klicken auf dieses Symbol wird der Inhalt angezeigt, der im Abschnitt „Lange Beschreibung“ hinzugefügt wurde.

![Beispiel für kontextbezogene Rich-Media-Hilfe](assets/photoshop.png)

### Hilfe auf Bereichsebene {#panel-level-help}

Zusätzlich zur kontextbezogenen Hilfe für Formularfelder können Sie auf der Registerkarte „Hilfeinhalt“ des Dialogfelds zum Bearbeiten von Bereichen auch Hilfe auf Bereichsebene angeben.

![Hinzufügen von kontextbezogener Hilfe für einen Formularbereich](assets/panel-level-help.png)

Wenn Sie Hilfe für ein Panel hinzufügen, wird das Symbol **?** neben der Beschreibung des Panels angezeigt. Durch Klicken auf das Symbol wird der Inhalt angezeigt, der im Abschnitt „Hilfeinhalt“ des Dialogfelds zur Bearbeitung des Panels hinzugefügt wurde.

![Beispiel für kontextbezogene Hilfe auf Formularbereichsebene](assets/photoshop-1.png)
