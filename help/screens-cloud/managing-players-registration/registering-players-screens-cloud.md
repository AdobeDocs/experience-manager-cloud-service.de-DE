---
title: Registrieren von Playern in Screens als Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Player in Screens als Cloud Service registrieren.
hide: true
hidefromtoc: true
index: false
source-git-commit: f0e005ddc59c575188d15986cabdbe04cb48ad03
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 2%

---


# Registrieren von Playern in Screens als Cloud Service {#registering-players-screens-cloud}

Nachdem Sie Player für Screens als Cloud Service installiert und konfiguriert haben, müssen Sie die Player registrieren.

## Vorgabe {#objective}

In diesem Dokument erfahren Sie, wie Sie Player im Screens-Dienstanbieter registrieren. Nach dem Lesen sollten Sie in der Lage sein:

* Informationen zur Registrierung von Playern
* wie Sie den Registrierungsprozess von Screens Services Provider abschließen

## Schritte zum Registrieren eines Screens-Players {#register-players}

Sobald Sie Ihren Player in Screens als Cloud Service installiert haben, können Sie den Player über den Screens-Dienstleister registrieren.

Gehen Sie wie folgt vor, um den Player zu registrieren:

1. Melden Sie sich bei Screens Services Provider an.

1. Navigieren Sie im linken Navigationsbereich zu **Registrierungscodes** unter **Player-Verwaltung** und klicken Sie auf **Code erstellen**.

   >[!NOTE]
   >Wenn keine gültigen/nicht abgelaufenen Codes vorhanden sind, klicken Sie auf Code erstellen , geben Sie einen Namen für den Code ein und wählen Sie die Ablaufeinstellungen gemäß Ihren Anforderungen aus.

   ![image](/help/screens-cloud/assets/player/register-player1.png)

1. Füllen Sie die folgenden Felder im Dialogfeld **Registrierungscode** erstellen aus:

   ![image](/help/screens-cloud/assets/player/register-player2.png)

   1. **Name des Registrierungs-Codes**: Name Ihres Registrierungscodes
   1. **Ablauf des Registrierungs-Codes**: Ablaufdatum für Ihren Registrierungscode
   1. **Nutzung begrenzen**: Schalten Sie die Schaltfläche um, um die Nutzungsbegrenzung Ihres Registrierungs-Codes zu deaktivieren. Standardmäßig ist die Option Nutzung begrenzen deaktiviert.
   1. **Nutzungsbeschränkung**: Wählen Sie die Nummer für Ihr Nutzungslimit aus.

1. Klicken Sie auf **Erstellen** , um den Registrierungs-Code zu erstellen. Ihr Player wird mit dem Registrierungs-Code in der Liste angezeigt.

   ![image](/help/screens-cloud/assets/player/register-player3.png)

1. Klicken Sie auf den Wert unter der Spalte **REGISTRIERUNGSCODE** , um den Wert in die Zwischenablage zu kopieren.

1. Fügen Sie diesen Wert in das Feld **Geben Sie Code** auf der Registerkarte **Player-Registrierung** in der Admin-Benutzeroberfläche des AEM Screens-Players ein und klicken Sie auf **Registrieren**.

   ![image](/help/screens-cloud/assets/player/register-player4.png)


1. Nachdem Sie den Code hinzugefügt haben, sehen Sie, dass der Player jetzt über die Admin-Benutzeroberfläche des Players registriert ist.

   ![image](/help/screens-cloud/assets/player/register-player5.png)

1. Sie sollten sehen, dass dieser Player jetzt im linken Navigationsbereich unter **Player** angezeigt wird. Der im Screens-Dienstanbieter angezeigte Code stimmt mit dem Bedienfeld **Systeminformationen** in der Admin-Benutzeroberfläche unter Player-Code überein.

   ![image](/help/screens-cloud/assets/player/register-player6.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie den Player im Cloud -Modus installiert und konfiguriert haben, sollten Sie Screens als Cloud Service-Journey weiterführen, indem Sie das Dokument [Player in Screens as a Cloud Service zuweisen](/help/screens-cloud/managing-players-registration/assigning-player-display.md) vom Screens-Dienstanbieter erneut ansehen.