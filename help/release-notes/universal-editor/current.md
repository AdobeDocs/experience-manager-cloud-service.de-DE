---
title: Universeller Editor – Versionshinweise für 2025.02.17
description: Dies sind die Versionshinweise für die Version 2025.02.17 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: c88aa13c6bc75c8f9cd624d00ef768290981c840
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 23%

---


# Universeller Editor – Versionshinweise für 2025.02.17 {#release-notes}

Dies sind die Versionshinweise für die Version vom 17. Februar 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **In Vorschau veröffentlichen** - [Beim Veröffentlichen (oder Rückgängigmachen der Veröffentlichung) Ihrer Inhalte ](/help/sites-cloud/authoring/universal-editor/publishing.md) dem universellen Editor können Sie jetzt auswählen, ob Sie zusätzlich zu Ihrer Veröffentlichungsumgebung in Ihrer [Vorschauumgebung ](/help/sites-cloud/authoring/sites-console/previewing-content.md) möchten
   * Dies ermöglicht die Überprüfung Ihrer Inhalte vor der öffentlichen Veröffentlichung.
* **Modell und Filter können in der Komponentendefinition definiert werden** - Sie können jetzt definieren, welches Modell und welcher Filter eine Komponente verwendet [in der Komponentendefinition.](/help/implementing/universal-editor/component-definition.md#template)
   * Diese Informationen können zentral in der Definition verwaltet werden und müssen nicht in der Instrumentierung angegeben werden.
   * Auf diese Weise können Sie Komponenten über Container hinweg verschieben.
* **Untergeordnete Elemente von Containern werden implizit als Komponenten betrachtet** - Wenn [ein Element mit `data-aue-resource`](/help/implementing/universal-editor/attributes-types.md#data-properties) als direkt untergeordnetes Element in einen Container eingefügt wird, wird es als Komponente betrachtet und kann verschoben werden, ohne dass `data-aue-behavior="component"` angegeben werden muss.

## Andere Verbesserungen {#other-improvements}

* **AEM 6.5-Asset-Selektor** - Der 6.5-Asset-Selektor wird jetzt ordnungsgemäß geöffnet, wenn [den universellen Editor mit AEM 6.5 ausführen.](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)
