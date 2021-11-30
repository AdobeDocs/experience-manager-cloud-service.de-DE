---
title: Registrieren von Playern in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Player in Screens as a Cloud Service registrieren.
exl-id: 1a0d6b22-71b1-4f3c-acaa-82d8d9c0f81a
source-git-commit: 489cc9963910ba9f94d30906127beb75f9ad37df
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 78%

---

# Registrieren von Playern in Screens as a Cloud Service {#registering-players-screens-cloud}

Nachdem Sie Player für Screens as a Cloud Service installiert und konfiguriert haben, müssen Sie die Player registrieren.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie Player in Screens Services Provider registrieren. Nach dem Lesen sollten Sie Folgendes können:

* verstehen, wie man Player registriert
* den Registrierungsprozess von Screens Services Provider aus abschließen

## Schritte zum Registrieren eines Screens-Players {#register-players}

Sobald Sie Ihren Player in Screens as a Cloud Service installiert haben, können Sie den Player über Screens Services Provider registrieren.

Gehen Sie wie folgt vor, um den Player zu registrieren:

1. Melden Sie sich bei Screens Services Provider an.

1. Gehen Sie im linken Navigationsbereich zu **Registrierungs-Codes** unter **Player-Verwaltung** und klicken Sie auf **Code erstellen**.

   >[!NOTE]
   >Wenn keine gültigen/nicht abgelaufenen Codes vorhanden sind, klicken Sie auf „Code erstellen“, geben Sie einen Namen für den Code ein und wählen Sie die Ablaufeinstellungen gemäß Ihren Anforderungen aus.

   ![image](/help/screens-cloud/assets/player/register-player1.png)

1. Füllen Sie im Dialogfeld **Registrierungs-Code erstellen** die folgenden Felder aus:

   ![image](/help/screens-cloud/assets/player/register-player2.png)

   1. **Name des Registrierungs-Codes**: Name Ihres Registrierungs-Codes
   1. **Ablauf des Registrierungs-Codes**: Ablaufdatum für Ihren Registrierungscode
   1. **Nutzung begrenzen**: Schalten Sie die Schaltfläche um, um die Nutzungsbegrenzung Ihres Registrierungs-Codes zu deaktivieren. Standardmäßig ist die Option Nutzung begrenzen deaktiviert.
   1. **Nutzungsbeschränkung**: Wählen Sie die Zahl für IhreNutzungsbeschränkung aus.

1. Klicken Sie auf **Erstellen**, um den Registrierungs-Code zu erstellen. Ihr Player wird mit dem Registrierungs-Code in der Liste angezeigt.

   ![image](/help/screens-cloud/assets/player/register-player3.png)

1. Klicken Sie auf den Wert unter der Spalte **REGISTRIERUNGS-CODE**, um den Wert in die Zwischenablage zu kopieren.

1. Fügen Sie diesen Wert in das Feld **Code eingeben** auf der Registerkarte **Player-Registrierung** in der Admin-Benutzeroberfläche des AEM Screens-Players ein und klicken Sie auf **Registrieren**.

   ![image](/help/screens-cloud/assets/player/register-player4.png)


1. Nachdem Sie den Code hinzugefügt haben, sehen Sie, dass der Player jetzt über die Admin-Benutzeroberfläche des Players registriert ist.

   ![image](/help/screens-cloud/assets/player/register-player5.png)

1. Sie sollten sehen, dass dieser Player jetzt im linken Navigationsbereich unter **Player** angezeigt wird. Der in Screens Services Provider angezeigte Code stimmt mit dem Bedienfeld **Systeminformationen** in der Admin-Benutzeroberfläche unter Player-Code überein.

   ![image](/help/screens-cloud/assets/player/register-player6.png)

>[!IMPORTANT]
>**Best Practices für die Sicherheit bei Verwendung des Registrierungs-Codes
>Als Best Practice können Sie die Verwendung des Registrierungs-Codes einschränken. Wenn ein Registrierungs-Code kompromittiert ist, aber eine Grenze von 100 Registrierungen hat, kann sich der Angreifer nur bis zu dieser Zahl registrieren, aber nicht mehr. Sie können die Nutzungsbeschränkung jederzeit aktualisieren, nachdem der Registrierungs-Code erstellt und einige der Player des Kunden bereits registriert wurden. Wenn der Kunde eine ungewöhnliche Registrierungsaktivität für einen bestimmten Registrierungs-Code beobachtet, kann er den Grenzwert in Echtzeit senken, während er untersucht, und die Zahl kann erhöht werden, wenn es sich um einen falschen Alarm handelt, ohne dass sich dies auf die bereits registrierten Player auswirkt.


## Wie geht es weiter {#whats-next}

Nachdem Sie den Player im Cloud-Modus installiert und konfiguriert haben, sollten Sie die Screens as a Cloud Service-Tour fortführen, indem Sie das Dokument [Zuweisen von Playern in Screens as a Cloud Service](/help/screens-cloud/managing-players-registration/assigning-player-display.md) in Screens Services Provider erneut lesen.
