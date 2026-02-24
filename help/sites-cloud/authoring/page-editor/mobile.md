---
title: Verfassen einer Seite für Mobilgeräte
description: Beim Verfassen für Mobilgeräte können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was die Endbenutzerinnen und -benutzer sehen
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: fabd4468-3304-402f-9522-342da3bbae94
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 98%

---

# Verfassen einer Seite für Mobilgeräte {#authoring-a-page-for-mobile-devices}

Adobe Experience Manager-Seiten basieren auf einem responsiven Layout. Durch ein [responsives Layout](/help/sites-cloud/authoring/page-editor/responsive-layout.md) werden Ihre Inhalte automatisch an das jeweilige Zielgerät angepasst, sodass Inhalte nicht speziell für bestimmte Geräte erstellt werden müssen.

Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was die Endbenutzerinnen und -benutzer beim Zugriff auf die Seite sehen.

Geräte sind entsprechend ihrer Fähigkeit zur Wiedergabe einer Seite in die Kategorien „Feature“, „Smart“ und „Touch“ eingeteilt. Wenn die Endbenutzerinnen und -benutzer auf eine mobile Seite zugreifen, erkennt AEM das Gerät und übermittelt die Darstellung, die der Gerätegruppe entspricht.

>[!NOTE]
>
>Zur Erstellung einer Website für Mobilgeräte auf der Grundlage einer bestehenden Standard-Site erstellen Sie eine Live Copy der Standard-Site. Weitere Information finden Sie unter [Erstellen von Live Copys](/help/sites-cloud/administering/msm/creating-live-copies.md).
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
1. [Ändern Sie das responsive Layout](/help/sites-cloud/authoring/page-editor/responsive-layout.md) der Seite und ihrer Komponenten je nach Gerät.

Die Seite sieht dann ähnlich wie die folgende aus:

![Beispiel für Mobilgeräte](/help/sites-cloud/authoring/assets/mobile.png)

>[!NOTE]
>
>Die Emulatoren sind deaktiviert, wenn eine Seite in der Autoreninstanz von einem Mobilgerät aus aufgerufen wird.
