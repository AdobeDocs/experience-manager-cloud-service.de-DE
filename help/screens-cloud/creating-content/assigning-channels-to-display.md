---
title: Zuweisen eines Kanals zu einem Display in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie in Screens as a Cloud Service einen Kanal einem Display zuweisen.
exl-id: ba001c18-7b05-4ae2-aa7f-9ebb320fedd0
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 62%

---

# Zuweisen eines Kanals zu einem Display in Screens as a Cloud Service {#assign-channel-displays-screens-cloud}

Nachdem die Projekteinrichtung abgeschlossen ist, müssen Sie den Kanal einer Anzeige zuweisen, um den Inhalt anzuzeigen.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie einem Display einen Kanal zuweisen, sobald das Display bereit ist und Sie Inhalt zu Ihrem Kanal hinzugefügt und veröffentlicht haben. Nach dem Lesen sollten Sie verstehen, wie Sie einen Kanal einer Anzeige vom Screens Services Provider zuweisen.

## Voraussetzungen {#prerequisites}

Bevor Sie die folgenden Schritte ausführen, um einen Kanal einem Display zuzuweisen, müssen Sie das Folgende gelernt haben:

* Erstellen und Verwalten von Displays
* Erstellen und Verwalten von Kanälen

## Schritte für das Zuweisen eines Kanals zu einem Display {#assign-channel-to-display}

Gehen Sie wie folgt vor, um einer Anzeige einen Kanal zuzuweisen:

1. Gehen Sie zu Screens Services Provider und wählen Sie **Displays** aus dem linken Navigationsbereich aus.

1. Klicken **Kanal zuweisen** zur Anzeige hinzu.

   ![image](/help/screens-cloud/assets/display/assignchannel-1.png)

1. Füllen Sie die folgenden Felder im Dialogfeld **Kanal zuweisen** aus.

   ![image](/help/screens-cloud/assets/display/assignchannel-2.png)

   1. Wählen Sie den Kanalnamen aus der Dropdown-Liste aus.
   1. Wählen Sie die Priorität aus.

      >[!NOTE]
      >Mit „Priorität“ können Zuweisungen geordnet werden, falls mehrere die Wiedergabekriterien erfüllen. Der Wert mit dem höchsten Wert hat immer Vorrang vor niedrigeren Werten. Wenn es beispielsweise zwei Kanäle A und B gibt. A hat die Priorität 1 und B die Priorität 2, wird Kanal B angezeigt, da er eine höhere Priorität als A hat.

   1. Wählen Sie in **Aktivierung** das Start- und Enddatum aus.

1. Klicken **+ Wiederholung hinzufügen** , um einen Intervallzeitplan für Ihren Kanal hinzuzufügen.

   ![image](/help/screens-cloud/assets/create-content/recurrence-1.png)

   >[!NOTE]
   >Sie können Ihrem Kanal mehrere Intervallzeitpläne hinzufügen. Mit den Intervallzeitplänen wird Dayparting eingeführt, mit dem Sie einen globalen Zeitplan mit mehreren Kanälen festlegen können, die zu bestimmten Tageszeiten ausgeführt werden, und diese für alle Anzeigen wiederverwenden können.

   Sie können die folgenden Optionen festlegen:

   * **Name**: Titel des Intervallzeitplans.
   * **Wiederholen**: Wählen Sie aus, ob der Plan täglich, wöchentlich, monatlich oder jährlich ausgeführt werden soll.
   * **Anfang**: Die Startzeit Ihres Zeitplans.
   * **Ende**: Die Endzeit Ihres Zeitplans. Sie können sie nach Zeit oder Dauer festlegen.
   * **Zeit**: Der Zeitplan endet zu einem bestimmten Zeitpunkt.
   * **Dauer**: Der Zeitplan wird für eine bestimmte Zeitdauer in Stunden oder Minuten ausgeführt.

1. Klicken Sie auf **Erstellen**. Sie können sehen, dass ein Kanal für diese Anzeige zugewiesen ist, wie in der folgenden Abbildung dargestellt.

   ![image](/help/screens-cloud/assets/display/assignchannel-3.png)


## Wie geht es weiter {#whats-next}

Nachdem Sie nun den Kanal einem Display zugewiesen haben, sollten Sie Ihre Screens as a Cloud Service-Tour fortsetzen, indem Sie das Dokument [Installieren und Konfigurieren des Screens-Players für AEM as a Cloud Service](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md) lesen.
