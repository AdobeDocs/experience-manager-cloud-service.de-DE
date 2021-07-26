---
title: Erstellen von Screens-Videoausgaben in Screens als Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Screens-Videoausgaben in Screens als Cloud Service erstellen.
source-git-commit: ec939ac6a91523a9ba64a555943eba8e6da071eb
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 1%

---


# Erstellen von Screens-Videoausgaben in Screens als Cloud Service {#creating-screens-video-renditions}

## Einführung {#introduction}

In diesem Handbuch wird beschrieben, wie Sie in Screens-Playern verwendete Videoausgabedarstellungen erstellen.

>[!IMPORTANT]
>Die in diesem Abschnitt hervorgehobenen Schritte müssen konfiguriert werden, wenn Sie Videos in Screens-Kanälen verwenden möchten.

## Schritte zum Erstellen von Screens-Videoausgaben in Screens als Cloud Service {#steps-creating-screens-video-renditions}

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


   >[!IMPORTANT]
   >Stellen Sie sicher, dass Sie den Kodierungsnamen verwenden, der mit &quot;screens-&quot;beginnt, dass nur diese Videoausgabedarstellungen als Cloud Service das Videoerlebnis in Screens as a wiedergeben. Geben Sie die Bitrate ein, die Ihren Videos entspricht (2500 kbps für 720 px Video und 5000 kbps für 1080 px)

   >[!NOTE]
   >Es können mehrere Videoausgabeformate mit unterschiedlicher Breite/Höhe/Bitrate hinzugefügt werden, aber beachten Sie, dass alle Screens- Ausgabeformate von den Screens-Geräten heruntergeladen werden, auch wenn das Gerät nur Videoausgabeformate wiedergibt.

1. Klicken Sie auf Speichern.

1. Wählen Sie das Verarbeitungsprofil aus und klicken Sie auf &quot;Profil auf Ordner anwenden&quot;.

1. Wählen Sie die Ordner aus, in denen Screens-Videos aufbewahrt werden, und klicken Sie auf Übernehmen .

1. Sie können mehrere Verarbeitungsprofile erstellen und auf die entsprechenden Ordner anwenden, sodass die Videos in diesen Ordnern die spezifischen Videoausgabeformate erhalten

1. Wenn Sie Videos in den Ordner hochladen, in dem das Verarbeitungsprofil angewendet wird, werden Videos verarbeitet und konfigurierte Ausgabedarstellungen erstellt, die von den Screens-Geräten zur Wiedergabe der Videos verwendet werden.

