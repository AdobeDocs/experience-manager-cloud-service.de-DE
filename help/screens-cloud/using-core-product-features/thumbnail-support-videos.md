---
title: Unterstützung von Miniaturansichten für Videos in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie in Screens as a Cloud Service Miniaturansichten für Videos hinzufügen.
index: true
exl-id: 7b15d7cc-f089-4008-9039-5f48343a0f20
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 30%

---

# Unterstützung von Miniaturansichten für Videos {#thumbnail-support-videos}

## Einführung {#introduction}

Ein Inhaltsautor kann eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet wird, während das eigentliche Video vom entsprechenden Team fertig gestellt wird. Das Bild kann auch verwendet werden, wenn die Wiedergabe des Videos fehlschlägt.

Durch das Hinzufügen der Unterstützung für ein Miniaturbild in der Videokomponente kann der Kunde eine gültige Komponente mit tatsächlichem Inhalt zum Kanal hinzufügen und Zielgruppenkonfigurationen durchführen, bevor das Video bereitgestellt wird.

>[!NOTE]
>Das Miniaturbild wird wiedergegeben, wenn die Videokomponente einen Fehler bei der Videowiedergabe auf dem Player aufweist, sofern dies für die Videokomponente festgelegt wurde. Mit diesem Workflow können Sie die gewünschte Nachricht an die Zielgruppe senden (indem Sie Inhalte wiedergeben), anstatt sie vollständig zu überspringen.

Mit der Unterstützung von Miniaturansichten können Sie Folgendes tun:

* Ein Kanalerlebnis vorbereiten, wenn die Videos noch nicht fertig sind oder wenn Sie nicht unbedingt einen umfangreichen Asset-Download auf die Player testen möchten

* Einen Ausweichmechanismus festlegen, falls auf dem Gerät Wiedergabeprobleme auftreten.

## Verwenden von Miniaturansichten in Videos {#using-thumbnails}

>[!IMPORTANT]
>**Voraussetzungen**
>Bevor Sie erfahren, wie Sie Miniaturansichten für Videos verwenden, sollten Sie sich mit dem Erstellen von Videoausgabeformaten für Kanäle im as a Cloud Service Screens-Projekt vertraut machen. Siehe [Erstellen von Videoausgabeformaten in Screens as a Cloud Service](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md).

Gehen Sie wie folgt vor, um Miniaturansichten in Videos zu verwenden:

1. Navigieren Sie zu einem vorhandenen Screens-Kanal oder erstellen Sie einen Kanal.

   >[!NOTE]
   >Informationen zum Erstellen eines Kanals und Hinzufügen von Inhalten zu einem Kanal finden Sie unter [Erstellen und Verwalten eines Kanals in Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=en).

1. Wählen Sie den Kanal aus. Klicken Sie in der Aktionsleiste auf **Bearbeiten** , um den Editor zu öffnen.


   ![Schaltfläche &quot;Bearbeiten&quot;in der Aktionsleiste](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png).

1. Fügen Sie eine vorhandene Videokomponente hinzu oder bearbeiten Sie sie, wie in der folgenden Abbildung dargestellt.

   ![Hervorgehobenes Bild eines Video-Assets](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png).

1. Fügen Sie eine vorhandene Videokomponente hinzu oder bearbeiten Sie sie, wie in der folgenden Abbildung dargestellt.

1. Wählen Sie das Video aus und klicken Sie auf Konfigurieren (*Schraubenschlüssel*), um die Videoeigenschaften zu öffnen.

   ![Das ausgewählte Video-Asset-Bild mit dem Pfeil, der auf das Symbol &quot;Konfigurieren&quot;zeigt und als Schraubenschlüssel dargestellt wird. in der Symbolleiste](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png).

1. Die **Video** wird ein Dialogfeld geöffnet, in dem Sie die **Miniatur** Dropzone.

   ![Dialogfeld &quot;Video&quot;mit Bild des Video-Assets und dem Dropbox &quot;Miniatur&quot;](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png).

1. Ziehen Sie ein Bild aus der Asset-Auswahl in den Bereich **Miniatur** Dropzone und klicken Sie auf **Fertig**.

   ![Asset-Bildauswahl, die hinter dem Dialogfeld &quot;Video&quot;angezeigt wird, mit Bild-Asset, das im Dropdown-Feld &quot;Miniatur&quot;angezeigt wird](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png).

1. Klicken Sie auf **Vorschau**. 

1. Wenn ein Video für die Komponente festgelegt ist, wird das Video wiedergegeben. Wenn nicht, und die Miniaturansicht festgelegt ist, wird die Miniaturansicht wiedergegeben. Andernfalls wird die Komponente als nicht konfiguriert betrachtet und übersprungen.

## Unterstützte Anwendungsfälle bei der Verwendung von Miniaturansichten in Videos {#understand-use-case}

Miniaturansichten in Videos unterstützen die folgenden Anwendungsfälle:

* Eine Videokomponente ohne Einrichtung wird übersprungen.

* Eine Videokomponente mit nur der Miniaturansicht wird als Miniaturansicht angezeigt.

* Eine Videokomponente mit dem Video (wenn das Video die richtige Wiedergabe aufweist) und der Miniaturansicht wird das Video wiedergegeben.

* Eine Videokomponente mit dem Videoset gibt die Miniaturansicht wieder, wenn ein Wiedergabefehler auftritt, oder überspringt den Vorgang zum nächsten Element, falls die Miniaturansicht nicht konfiguriert ist.
