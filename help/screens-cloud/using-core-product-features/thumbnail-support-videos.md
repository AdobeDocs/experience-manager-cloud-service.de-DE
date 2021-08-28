---
title: Unterstützung von Miniaturansichten für Videos in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Miniaturansichten für Videos in Screens als Cloud Service hinzufügen.
index: true
source-git-commit: e5dc848ca58e176b89861414d0e711866f96eb0e
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---


# Unterstützung von Miniaturansichten für Videos {#thumbnail-support-videos}

## Einführung {#introduction}

Ein Inhaltsautor kann eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet werden kann, während das eigentliche Video vom entsprechenden Team fertig gestellt wird. Das Bild kann auch verwendet werden, falls die Wiedergabe des Videos fehlschlägt.

Durch das Hinzufügen der Unterstützung für ein Miniaturbild in der Videokomponente kann der Kunde eine gültige Komponente mit tatsächlichem Inhalt zum Kanal hinzufügen und Zielgruppenkonfigurationen durchführen, bevor das Video tatsächlich bereitgestellt wird.

>[!NOTE]
>Das Miniaturbild wird wiedergegeben, wenn es in der Videokomponente festgelegt ist, falls die Videowiedergabe auf dem Player fehlschlägt. Auf diese Weise können Sie die gewünschte Nachricht an die Zielgruppe senden (indem Sie Inhalte wiedergeben), anstatt sie vollständig zu überspringen.

Mit der Unterstützung von Miniaturansichten können Sie:

* Bereiten Sie ein Kanalerlebnis vor, wenn die Videos noch nicht bereit sind oder Sie nicht unbedingt einen großen Asset-Download auf den Playern testen möchten

* Legen Sie einen Ausweichmechanismus fest, falls auf dem Gerät Wiedergabeprobleme auftreten.

## Verwenden von Miniaturansichten in Videos {#using-thumbnails}

>[!IMPORTANT]
>**Voraussetzungen**
>Bevor Sie lernen, wie Sie Miniaturansichten für Videos verwenden, sollten Sie wissen, wie Sie Videoausgabeformate für Kanäle in Screens as a Cloud Service erstellen. Weitere Informationen finden Sie unter [hier](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md) .

Gehen Sie wie folgt vor, um Miniaturansichten in Videos zu verwenden:

1. Navigieren Sie zu einem vorhandenen Screens-Kanal oder erstellen Sie einen neuen Kanal.

   >[!NOTE]
   >Informationen zum Erstellen eines Kanals und Hinzufügen von Inhalten zu einem Kanal finden Sie unter [Erstellen und Verwalten eines Kanals in Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=en).

1. Wählen Sie den Kanal aus und klicken Sie in der Aktionsleiste auf **Bearbeiten** , um den Editor zu öffnen.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png)

1. Fügen Sie eine vorhandene Videokomponente hinzu oder bearbeiten Sie sie, wie in der folgenden Abbildung dargestellt.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png)

1. Wählen Sie das Video aus und klicken Sie auf das Symbol *Schraubenschlüssel* , um die Videoeigenschaften zu öffnen.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png)

1. Das Dialogfeld **Video** wird geöffnet, in dem Sie die Dropzone **Miniaturansicht** anzeigen.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png)

1. Ziehen Sie ein Bild aus der Asset-Auswahl in die Dropzone **Miniatur** und klicken Sie auf **Fertig**.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png)

1. Klicken Sie auf **Vorschau**.

1. Wenn ein Video für die Komponente festgelegt ist, wird das Video wiedergegeben. Wenn nicht, und die Miniaturansicht festgelegt ist, wird die Miniaturansicht wiedergegeben. Andernfalls wird die Komponente als nicht konfiguriert betrachtet und übersprungen.

## Unterstützte Anwendungsfälle bei der Verwendung von Miniaturansichten in Videos {#understand-use-case}

Miniaturansichten in Videos unterstützen die folgenden Anwendungsfälle:

* Eine Videokomponente, für die nichts eingerichtet ist, wird übersprungen.

* Eine Videokomponente mit nur der Miniaturansicht wird die Miniaturansicht wiedergegeben.

* Eine Videokomponente mit sowohl dem Video (wenn das Video die richtige Wiedergabe aufweist) als auch dem Miniaturbild-Set gibt das Video wieder.

* Eine Videokomponente mit dem Videoset gibt die Miniaturansicht im Fall eines Wiedergabefehlers wieder oder springt einfach zum nächsten Element, falls die Miniaturansicht nicht konfiguriert ist.
