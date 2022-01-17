---
title: Unterstützung von Miniaturansichten für Videos in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie in Screens as a Cloud Service Miniaturansichten für Videos hinzufügen.
index: true
exl-id: 7b15d7cc-f089-4008-9039-5f48343a0f20
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: ht
source-wordcount: '494'
ht-degree: 100%

---

# Unterstützung von Miniaturansichten für Videos {#thumbnail-support-videos}

## Einführung {#introduction}

Ein Inhaltsautor kann eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet werden können, während das eigentliche Video vom entsprechenden Team fertiggestellt wird. Das Bild kann auch verwendet werden, wenn die Wiedergabe des Videos fehlschlägt.

Durch das Hinzufügen der Unterstützung für ein Miniaturbild in der Videokomponente kann der Kunde eine gültige Komponente mit echtem Inhalt zum Kanal hinzufügen und Targeting-Konfigurationen durchführen, bevor das Video tatsächlich bereitgestellt wird.

>[!NOTE]
>Falls die Videowiedergabe auf dem Player fehlschlägt, wird das Miniaturbild wiedergegeben, sofern es in der Videokomponente festgelegt ist. Auf diese Weise können Sie die gewünschte Nachricht an die Zielgruppe senden (indem Sie Inhalte wiedergeben), anstatt sie vollständig zu überspringen.

Mit der Unterstützung von Miniaturansichten können Sie:

* Ein Kanalerlebnis vorbereiten, wenn die Videos noch nicht fertig sind oder wenn Sie nicht unbedingt einen umfangreichen Asset-Download auf die Player testen möchten

* Einen Ausweichmechanismus festlegen, falls auf dem Gerät Wiedergabeprobleme auftreten.

## Verwenden von Miniaturansichten in Videos {#using-thumbnails}

>[!IMPORTANT]
>**Voraussetzungen**
>Bevor Sie lernen, wie Sie Miniaturansichten für Videos verwenden, sollten Sie zunächst erfahren, wie Sie im Screens as a Cloud Service-Projekt Video-Ausgabedarstellungen für Kanäle erstellen. Weitere Informationen dazu finden Sie [hier](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md).

Gehen Sie wie folgt vor, um Miniaturansichten in Videos zu verwenden:

1. Gehen Sie zu einem vorhandenen Screens-Kanal oder erstellen Sie einen neuen Kanal.

   >[!NOTE]
   >Informationen zum Erstellen eines Kanals und Hinzufügen von Inhalten zu einem Kanal finden Sie unter [Erstellen und Verwalten eines Kanals in Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=de).

1. Wählen Sie den Kanal aus und klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png)

1. Fügen Sie eine vorhandene Videokomponente hinzu oder bearbeiten Sie sie, wie in der folgenden Abbildung dargestellt.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png)

1. Wählen Sie das Video aus und klicken Sie auf das Symbol *Schraubenschlüssel*, um die Videoeigenschaften zu öffnen.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png)

1. Das Dialogfeld **Video** wird geöffnet, in dem die Ablagefläche **Miniaturansicht** angezeigt wird.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png)

1. Ziehen Sie ein Bild aus der Asset-Auswahl in die Ablagefläche **Miniaturansicht** und klicken Sie auf **Fertig**.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png)

1. Klicken Sie auf **Vorschau**.

1. Wenn ein Video für die Komponente festgelegt ist, wird das Video wiedergegeben. Wenn das nicht der Fall ist und die Miniaturansicht festgelegt ist, wird die Miniaturansicht wiedergegeben. Andernfalls wird die Komponente als nicht konfiguriert betrachtet und übersprungen.

## Unterstützte Anwendungsfälle bei der Verwendung von Miniaturansichten in Videos {#understand-use-case}

Miniaturansichten in Videos unterstützen die folgenden Anwendungsfälle:

* Eine Videokomponente, für die nichts eingerichtet ist, wird übersprungen.

* Bei einer Videokomponente, für die nur die Miniaturansicht festgelegt ist, wird die Miniaturansicht wiedergegeben.

* Bei einer Videokomponente, für die sowohl das Video (wenn das Video eine korrekte Ausgabedarstellung hat) als auch die Miniaturansicht festgelegt sind, wird das Video abgespielt.

* Eine Videokomponente mit festgelegtem Video gibt im Falle eines Wiedergabefehlers die Miniaturansicht wieder oder springt einfach zum nächsten Element, wenn die Miniaturansicht nicht konfiguriert ist.
