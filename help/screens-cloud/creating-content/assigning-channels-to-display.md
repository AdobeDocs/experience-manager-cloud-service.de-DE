---
title: Zuweisen eines Kanals zu einer Anzeige in Screens als Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie einen Kanal einer Anzeige in Screens als Cloud Service zuweisen.
hide: true
hidefromtoc: true
index: false
source-git-commit: c65eeaf74ddfd81d37eb7090b84c8bf6f876dc72
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 41%

---


# Zuweisen eines Kanals zu einer Anzeige in Screens als Cloud Service {#assign-channel-displays-screens-cloud}

Nachdem das Projekt fertig eingerichtet wurde, müssen Sie den Kanal einer Anzeige zuweisen, um den Inhalt anzuzeigen.

## Vorgabe {#objective}

In diesem Dokument erfahren Sie, wie Sie einer Anzeige einen Kanal zuweisen, sobald die Anzeige fertig ist und Sie Inhalt zu Ihrem Kanal hinzugefügt und veröffentlicht haben. Nach der Lektüre sollten Sie verstehen, wie Sie einen Kanal einer Anzeige vom Screens Services Provider zuweisen.

## Voraussetzungen {#prerequisites}

Bevor Sie die folgenden Schritte ausführen, um einen Kanal einer Anzeige zuzuweisen, müssen Sie das Lernen abgeschlossen haben:

* Erstellen und Verwalten von Anzeigen
* Erstellen und Verwalten von Kanälen

## Schritte zum Zuweisen eines Kanals zu einer Anzeige {#assign-channel-to-display}

Gehen Sie wie folgt vor, um einer Anzeige einen Kanal zuzuweisen:

1. Navigieren Sie zu Screens Services Provider und wählen Sie **Displays** aus dem linken Navigationsbereich aus.

1. Klicken Sie auf **Kanal** zur Anzeige zuweisen.

   ![image](/help/screens-cloud/assets/display/assignchannel-1.png)

1. Füllen Sie die folgenden Felder aus dem Dialogfeld **Kanal zuweisen** aus.

   ![image](/help/screens-cloud/assets/display/assignchannel-2.png)

   1. Wählen Sie den Kanalnamen aus der Dropdown-Liste aus.
   1. Wählen Sie die Priorität aus.

      >[!NOTE]
      >Mit „Priorität“ können Zuweisungen geordnet werden, falls mehrere die Wiedergabekriterien erfüllen. Höhere Werte haben stets Vorrang vor niedrigeren Werten. Wenn es beispielsweise die beiden Kanäle A und B gibt und A eine Priorität von 1 und B eine Priorität von 2 hat, wird Kanal B angezeigt, da er eine höhere Priorität als A hat.
   1. Wählen Sie in **Activation** das Start- und Enddatum aus.

1. Klicken Sie auf **+ Wiederholung hinzufügen** , um einen Intervallzeitplan für Ihren Kanal hinzuzufügen.

   ![image](/help/screens-cloud/assets/create-content/recurrence-1.png)

   >[!NOTE]
   >Sie können Ihrem Kanal mehrere Intervallzeitpläne hinzufügen. Mit den Intervallzeitplänen wird Dayparting eingeführt, sodass Sie einen globalen Zeitplan mit mehreren Kanälen festlegen können, die zu bestimmten Tageszeiten ausgeführt werden. Diese Einstellung kann dann für alle Anzeigen wiederverwendet werden.

   Sie können die folgenden Optionen festlegen:

   * **Name**: Titel des Intervallzeitplans.
   * **Wiederholen**: Wählen Sie aus, ob der Plan täglich, wöchentlich, monatlich oder jährlich ausgeführt werden soll.
   * **Anfang**: Die Startzeit Ihres Zeitplans.
   * **Ende**: Die Endzeit Ihres Zeitplans. Sie können die Einstellung nach Zeit oder Dauer festlegen.
   * **Zeit**: Der Zeitplan endet zu einer bestimmten Zeit.
   * **Dauer**: Der Zeitplan wird für eine bestimmte Zeitdauer in Stunden oder Minuten ausgeführt.

1. Klicken Sie auf **Erstellen** und jetzt sehen Sie, dass ein Kanal für diese Anzeige zugewiesen ist, wie in der folgenden Abbildung dargestellt.

   ![image](/help/screens-cloud/assets/display/assignchannel-3.png)


## Wie geht es weiter {#whats-next}

Nachdem Sie nun den Kanal einer Anzeige zugewiesen haben, sollten Sie Ihren Screens-Player als Cloud Service-Journey fortsetzen, indem Sie das Dokument **Installieren und Konfigurieren des Screens-Players für AEM als Cloud Service** erneut ansehen.
