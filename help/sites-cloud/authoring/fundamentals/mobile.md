---
title: Verfassen einer Seite für Mobilgeräte
description: Beim Bearbeiten der Seite können Sie zwischen verschiedenen Emulatoren wechseln, um festzustellen, welche Darstellung der Endbenutzer sieht.
exl-id: fabd4468-3304-402f-9522-342da3bbae94
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 98%

---

# Verfassen einer Seite für Mobilgeräte {#authoring-a-page-for-mobile-devices}

Adobe Experience Manager-Seiten basieren auf einem responsiven Layout. Durch ein [responsives Layout](/help/sites-cloud/authoring/features/responsive-layout.md) werden Ihre Inhalte automatisch an das jeweilige Zielgerät angepasst, sodass Inhalte nicht speziell für bestimmte Geräte erstellt werden müssen.

Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen verschiedenen Emulatoren wechseln, um zu sehen, was der Endbenutzer sieht, wenn auf er die Seite zugreift.

Geräte sind entsprechend ihrer Fähigkeit zur Wiedergabe einer Seite in die Kategorien „Feature“, „Smart“ und „Touch“ eingeteilt. Wenn der Endbenutzer auf eine Seite für Mobilgeräte zugreift, ermittelt AEM das entsprechende Gerät und sendet die zu der entsprechenden Gerätegruppe gehörige Version der Seite.

>[!NOTE]
>
>Zur Erstellung einer Website für Mobilgeräte auf der Grundlage einer bestehenden Standard-Site erstellen Sie eine Live Copy der Standard-Site. Siehe [Erstellen von Live Copies.](/help/sites-cloud/administering/msm/creating-live-copies.md)
>
>AEM-Entwickler können neue Gerätegruppen erstellen. Siehe „Erstellen von Gerätegruppen-Filtern“.

<!--
>AEM developers can create new device groups. (See [Creating Device Group Filters](/help/sites-developing/groupfilters.md).)
-->

Gehen Sie wie folgt vor, um eine Seite für Mobilgeräte zu erstellen:

1. Öffnen Sie ausgehend von der globalen Navigation die **Sites-Konsole**.
1. Bearbeiten Sie eine Inhaltsseite.
1. Wechseln Sie durch Klicken auf das **Emulator**-Symbol am oberen Seitenrand zum gewünschten Emulator.

   ![Emulator-Symbol](/help/sites-cloud/authoring/assets/emulator.png)

1. Ziehen Sie Komponenten per Drag-and-Drop aus dem Komponenten-Browser oder Asset-Browser auf die Seite.
1. [Ändern Sie das responsive Layout](/help/sites-cloud/authoring/features/responsive-layout.md) der Seite und ihrer Komponenten je nach Gerät.

Die Seite sieht dann ähnlich wie die folgende aus:

![Beispiel für Mobilgeräte](/help/sites-cloud/authoring/assets/mobile.png)

>[!NOTE]
>
>Die Emulatoren sind deaktiviert, wenn eine Seite in der Autoreninstanz von einem Mobilgerät aus aufgerufen wird.
