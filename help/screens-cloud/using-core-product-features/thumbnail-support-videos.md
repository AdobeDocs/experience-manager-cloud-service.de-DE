---
title: Unterstützung von Miniaturansichten für Videos in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Miniaturansichten für Videos in Screens als Cloud Service hinzufügen.
hide: true
index: false
source-git-commit: ea96e811c0164e3cc7d323e734c1617d3c0e9308
workflow-type: tm+mt
source-wordcount: '416'
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

Gehen Sie wie folgt vor, um Miniaturansichten in Videos zu verwenden:

1. Navigieren Sie zu einem vorhandenen Screens-Kanal oder erstellen Sie einen neuen Kanal.

   >[!NOTE]
   >Informationen zum Erstellen eines Kanals und Hinzufügen von Inhalten zu einem Kanal finden Sie unter [Erstellen und Verwalten eines Kanals in Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=en).

1. Wählen Sie den Kanal aus und klicken Sie in der Aktionsleiste auf **Bearbeiten** , um den Editor zu öffnen.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png)

1. Fügen Sie eine vorhandene Videokomponente hinzu oder bearbeiten Sie sie, wie in der folgenden Abbildung dargestellt.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png)

1. Bearbeiten Sie die Eigenschaften der Videokomponente.

1. Ziehen Sie ein Bild aus der Asset-Auswahl in die Dropzone Miniaturansicht .

1. Anzeigen einer Vorschau des Kanals

1. Wenn ein Video für die Komponente festgelegt ist, wird das Video wiedergegeben. Wenn nicht, und die Miniaturansicht festgelegt ist, wird die Miniaturansicht wiedergegeben. Andernfalls wird die Komponente als nicht konfiguriert betrachtet und übersprungen

## Unterstützte Anwendungsfälle bei der Verwendung von Miniaturansichten in Videos {#understand-use-case}

Beachten Sie bei der Verwendung von Miniaturansichten in Videos die folgenden Anwendungsfälle.

Eine Videokomponente mit:

* *Keine* Einrichtung wird übersprungen

* *Nur die Miniaturansicht* wird als Miniaturansicht angezeigt

* *Video- und Miniaturansicht-* Einstellungen geben das Video ab

* *Wenn ein Wiedergabefehler auftritt,* wird die Miniaturansicht im Video abgespielt oder einfach zum nächsten Element übersprungen, falls die Miniaturansicht nicht konfiguriert ist.
