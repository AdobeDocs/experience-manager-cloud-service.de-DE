---
title: Unterstützung von Miniaturansichten für Videos in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie in Screens as a Cloud Service Miniaturansichten für Videos hinzufügen.
index: true
exl-id: 7b15d7cc-f089-4008-9039-5f48343a0f20
source-git-commit: a77e5dc4273736b969e9a4a62fcac75664495ee6
workflow-type: ht
source-wordcount: '548'
ht-degree: 100%

---

# Unterstützung von Miniaturansichten für Videos {#thumbnail-support-videos}

## Einführung {#introduction}

Inhaltsautorinnen und -autoren können eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet werden können, während das eigentliche Video vom entsprechenden Team fertiggestellt wird. Das Bild kann auch für den Fall verwendet werden, dass die Wiedergabe des Videos fehlschlägt.

Durch das Hinzufügen der Unterstützung für ein Miniaturbild in der Videokomponente können Kundinnen und Kunden eine gültige Komponente mit echtem Inhalt zum Kanal hinzufügen und Targeting-Konfigurationen durchführen, bevor das Video bereitgestellt wird.

>[!NOTE]
>Falls die Videowiedergabe auf dem Player fehlschlägt, wird das Miniaturbild wiedergegeben, sofern es in der Videokomponente festgelegt ist. Mit diesem Workflow können Sie die gewünschte Nachricht an die Zielgruppe senden (indem Inhalte wiedergegeben werden), anstatt sie vollständig zu überspringen.

Mit der Unterstützung von Miniaturansichten können Sie Folgendes tun:

* Ein Kanalerlebnis vorbereiten, wenn die Videos noch nicht fertig sind oder wenn Sie nicht unbedingt einen umfangreichen Asset-Download auf die Player testen möchten

* Einen Ausweichmechanismus festlegen, falls auf dem Gerät Wiedergabeprobleme auftreten.

## Verwenden von Miniaturansichten in Videos {#using-thumbnails}

>[!IMPORTANT]
>**Voraussetzungen**
>Bevor Sie lernen, wie Sie Miniaturansichten für Videos verwenden, sollten Sie zunächst erfahren, wie Sie im Screens as a Cloud Service-Projekt Video-Ausgabedarstellungen für Kanäle erstellen. Weitere Informationen finden Sie unter [Erstellen von Video-Ausgabedarstellungen in Screens as a Cloud Service](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md)

Gehen Sie wie folgt vor, um Miniaturansichten in Videos zu verwenden:

1. Gehen Sie zu einem vorhandenen Screens-Kanal oder erstellen Sie einen Kanal.

   >[!NOTE]
   >Informationen zum Erstellen eines Kanals und Hinzufügen von Inhalten zu einem Kanal finden Sie unter [Erstellen und Verwalten eines Kanals in Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=de).

1. Wählen Sie den Kanal aus. Klicken Sie in der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen.


   ![Schaltfläche „Bearbeiten“ in der Aktionsleiste](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png).

1. Fügen Sie eine vorhandene Videokomponente hinzu oder bearbeiten Sie sie, wie in der folgenden Abbildung dargestellt.

   ![Hervorgehobenes Bild eines Video-Assets](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png).

1. Fügen Sie eine vorhandene Videokomponente hinzu oder bearbeiten Sie sie, wie in der folgenden Abbildung dargestellt.

1. Wählen Sie das Video aus und klicken Sie auf das Symbol „Konfigurieren“ (*Schraubenschlüssel*), um die Videoeigenschaften zu öffnen.

   ![Bild eines ausgewählten Video-Assets mit Pfeil, der auf das Symbol „Konfigurieren“ zeigt, das als Schraubenschlüssel dargestellt ist. In der Symbolleiste](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png).

1. Das Dialogfeld **Video** wird geöffnet, in dem die Ablagefläche **Miniaturansicht** angezeigt wird.

   ![Das Video-Dialogfeld zeigt ein Bild des Video-Assets und die Dropbox für die Miniaturansicht](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png).

1. Ziehen Sie ein Bild aus der Asset-Auswahl in die Ablagefläche **Miniaturansicht** und klicken Sie auf **Fertig**.

   ![Die Asset-Bildauswahl wird hinter dem Video-Dialogfeld angezeigt, wobei das Bild in der Dropbox „Miniaturansicht“ angezeigt wird](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png).

1. Klicken Sie auf **Vorschau**. 

1. Wenn für die Komponente ein Video festgelegt ist, wird das Video wiedergegeben. Wenn das nicht der Fall ist und die Miniaturansicht festgelegt ist, wird die Miniaturansicht wiedergegeben. Andernfalls wird die Komponente als nicht konfiguriert betrachtet und übersprungen.

## Unterstützte Anwendungsfälle bei der Verwendung von Miniaturansichten in Videos {#understand-use-case}

Miniaturansichten in Videos unterstützen die folgenden Anwendungsfälle:

* Eine Videokomponente, für die nichts eingerichtet ist, wird übersprungen.

* Bei einer Videokomponente, für die nur die Miniaturansicht festgelegt ist, wird die Miniaturansicht wiedergegeben.

* Bei einer Videokomponente, für die sowohl das Video (wenn das Video eine korrekte Ausgabedarstellung hat) als auch die Miniaturansicht festgelegt sind, wird das Video abgespielt.

* Eine Videokomponente, für die das Video festgelegt ist, spielt die Miniaturansicht ab, wenn ein Wiedergabefehler auftritt, oder springt zum nächsten Element, falls die Miniaturansicht nicht konfiguriert ist.
