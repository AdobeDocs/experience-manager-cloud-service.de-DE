---
title: Erstellen von Screens-Videoausgaben in Screens als Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Screens-Videoausgaben in Screens als Cloud Service erstellen.
source-git-commit: b8691bb77079eeb7efd141ce89c44c5a312262b3
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---


# Erstellen von Screens-Videoausgaben in Screens als Cloud Service {#creating-screens-video-renditions}

## Einführung {#introduction}

In diesem Handbuch wird beschrieben, wie Sie in Screens-Playern verwendete Videoausgabedarstellungen erstellen.

>[!IMPORTANT]
>Die in diesem Abschnitt hervorgehobenen Schritte müssen konfiguriert werden, wenn Sie Videos in Screens-Kanälen verwenden möchten.

## Schritte zum Erstellen von Screens-Videoausgaben in Screens als Cloud Service {#steps-creating-screens-video-renditions}

1. Navigieren Sie in der Benutzeroberfläche von Screens Cloud zu Kanälen.
1. Klicken Sie links oben auf die Adobe Experience Manager, um zum Screens Content Provider zu navigieren, d. h. AEM als Cloud Service.
1. Klicken Sie jetzt im Hauptnavigationsmenü auf den Bereich Tools , dann auf &quot;Assets&quot; und dann auf &quot;Verarbeitungsprofile&quot;.

1. Klicken Sie auf &quot;Erstellen&quot;, um ein neues Verarbeitungsprofil zu erstellen.
1. Geben Sie einen Namen an, z. B. &quot;ScreensProcessingProfile&quot;
1. Navigieren Sie zur Registerkarte Video , um eine Videokodierung hinzuzufügen, und klicken Sie auf &quot;Neu hinzufügen&quot;


   >[!IMPORTANT]
   >Stellen Sie sicher, dass Sie den Kodierungsnamen verwenden, der mit &quot;screens-&quot;beginnt, dass nur diese Videoausgabedarstellungen als Cloud Service das Videoerlebnis in Screens as a wiedergeben. Geben Sie die Bitrate ein, die Ihren Videos entspricht (2500 kbps für 720 px Video und 5000 kbps für 1080 px)

   >[!NOTE]
   >Es können mehrere Videoausgabeformate mit unterschiedlicher Breite/Höhe/Bitrate hinzugefügt werden, aber beachten Sie, dass alle Screens- Ausgabeformate von den Screens-Geräten heruntergeladen werden, auch wenn das Gerät nur Videoausgabeformate wiedergibt.

1. Klicken Sie auf Speichern.

1. Wählen Sie das Verarbeitungsprofil aus und klicken Sie auf &quot;Profil auf Ordner anwenden&quot;.

1. Wählen Sie die Ordner aus, in denen Screens-Videos aufbewahrt werden, und klicken Sie auf Übernehmen .

1. Sie können mehrere Verarbeitungsprofile erstellen und auf die entsprechenden Ordner anwenden, sodass die Videos in diesen Ordnern die spezifischen Videoausgabeformate erhalten

1. Wenn Sie Videos in den Ordner hochladen, in dem das Verarbeitungsprofil angewendet wird, werden Videos verarbeitet und konfigurierte Ausgabedarstellungen erstellt, die von den Screens-Geräten zur Wiedergabe der Videos verwendet werden.

