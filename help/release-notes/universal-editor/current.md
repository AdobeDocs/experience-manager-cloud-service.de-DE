---
title: Universeller Editor – Versionshinweise für 2025.02.17
description: Dies sind die Versionshinweise für die Version 2025.02.17 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: af04ad7e3f89247580c48c276cb371d78ac56a49
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 22%

---


# Universeller Editor – Versionshinweise für 2025.02.17 {#release-notes}

Dies sind die Versionshinweise für die Version vom 17. Februar 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **In Vorschau veröffentlichen** - Beim Veröffentlichen (oder Rückgängigmachen der Veröffentlichung) Ihrer Inhalte mit dem universellen Editor können Sie jetzt auswählen, ob Sie zusätzlich zu Ihrer Veröffentlichungsumgebung in Ihrer Vorschau veröffentlichen möchten
   * Dies ermöglicht die Überprüfung Ihrer Inhalte vor der öffentlichen Veröffentlichung.
* **Modell und Filter können in der Komponentendefinition definiert werden** - Sie können jetzt definieren, welches Modell und welcher Filter eine Komponente in der Komponentendefinition verwendet.
   * Diese Informationen können zentral in der Definition verwaltet werden und müssen nicht in der Instrumentierung angegeben werden.
   * Auf diese Weise können Sie Komponenten über Container hinweg verschieben.
* **Untergeordnete Elemente von Containern werden implizit als Komponenten betrachtet** - Wenn ein Element mit einem `data-aue-resource` als direkt untergeordnetes Element in einem Container platziert wird, wird es als Komponente betrachtet und kann verschoben werden, ohne dass `data-aue-behavior="component"` angegeben werden muss.

## Andere Verbesserungen {#other-improvements}

* **AEM 6.5-Asset-Wähler** - Der 6.5-Asset-Wähler wird jetzt ordnungsgemäß geöffnet, wenn der universelle Editor mit AEM 6.5 ausgeführt wird.

