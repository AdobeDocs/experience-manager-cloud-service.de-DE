---
title: Erstellen von Videoausgaben in Screens als Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Videoausgabeformate in Screens als Cloud Service erstellen.
source-git-commit: 102aab1d550e950ea880d9b9288bdab41866add6
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Erstellen von Videoausgaben in Screens als Cloud Service {#creating-screens-video-renditions}

## Einführung {#introduction}

In diesem Handbuch wird beschrieben, wie Sie in Screens-Playern verwendete Videoausgabedarstellungen erstellen.

>[!IMPORTANT]
>Die in diesem Abschnitt hervorgehobenen Schritte müssen konfiguriert werden, wenn Sie Videos in Screens-Kanälen verwenden möchten.

## Schritte zum Erstellen von Videoausgaben in Screens als Cloud Service {#steps-creating-screens-video-renditions}

Gehen Sie wie folgt vor, um Videoausgabeformate in Screens as a Cloud Service vom Screens Content Provider zu erstellen:

1. Navigieren Sie in Screens Content Provider zu Ihrem Kanal.

   >[!NOTE]
   >Weitere Informationen finden Sie unter [Verwenden des Screens Content Providers](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=en#screens-content-provider) .

1. Klicken Sie in der linken Navigationsleiste auf den Abschnitt Tools und dann auf **Assets** und dann auf **Verarbeitungsprofile**.

   ![](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Klicken Sie auf **Erstellen** , um ein neues Verarbeitungsprofil zu erstellen.

   ![](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Geben Sie den **Namen** ein, z. B. **ScreensProcessingProfile**.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Navigieren Sie zur Registerkarte **Video** , um eine Videokodierung hinzuzufügen, und klicken Sie auf **Neu hinzufügen**.

   ![](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Geben Sie den **Kodierungsnamen** wie **screens-fullhd** und die **Bitrate** als **2500** ein.

   ![](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Stellen Sie sicher, dass Sie den Kodierungsnamen verwenden, der mit &quot;screens-&quot;beginnt, dass nur diese Videoausgabedarstellungen als Cloud Service das Videoerlebnis in Screens wiedergeben. Geben Sie die Bitrate ein, mit der Ihre Videos funktionieren (2500 kbps für 720 px Video und 5000 kbps für 1080 px).

   >[!NOTE]
   >Für Videos können mehrere Videoausgabeformate mit unterschiedlicher Breite/Höhe/Bitrate hinzugefügt werden. Beachten Sie, dass alle Screens-Ausgabeformate von den Screens-Geräten heruntergeladen werden, auch wenn das Gerät nur Videoausgabedarstellungen wiedergibt.

1. Klicken Sie auf **Save**.

1. Wählen Sie das Verarbeitungsprofil aus und klicken Sie auf **Profil auf Ordner anwenden**.

   ![](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Wählen Sie die Ordner aus, in denen Screens-Videos aufbewahrt werden, und klicken Sie auf **Anwenden**.

   ![](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >* Sie können mehrere Verarbeitungsprofile erstellen und auf die entsprechenden Ordner anwenden, sodass die Videos in diesen Ordnern die jeweiligen Videoausgabedarstellungen erhalten.
   >* Wenn Sie Videos in den Ordner hochladen, in den das Verarbeitungsprofil angewendet wird, werden Videos verarbeitet und konfigurierte Ausgabedarstellungen erstellt, die von den Screens-Geräten zur Wiedergabe der Videos verwendet werden.


