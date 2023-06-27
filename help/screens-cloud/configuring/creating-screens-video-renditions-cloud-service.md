---
title: Erstellen von Video-Ausgabedarstellungen in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Video-Ausgabedarstellungen in Screens as a Cloud Service erstellen.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 50%

---

# Erstellen von Video-Ausgabedarstellungen in Screens as a Cloud Service {#creating-screens-video-renditions}

## Einführung {#introduction}

In diesem Abschnitt wird beschrieben, wie Sie in Screens-Playern verwendete Video-Ausgabedarstellungen erstellen.

>[!IMPORTANT]
>Die in diesem Abschnitt hervorgehobenen Schritte müssen konfiguriert werden, wenn Sie Videos in Screens-Kanälen verwenden möchten.

## Schritte zum Erstellen von Video-Ausgabedarstellungen in Screens as a Cloud Service {#steps-creating-screens-video-renditions}

Gehen Sie wie folgt vor, um von Screens Content Provider aus Video-Ausgabedarstellungen in Screens as a Cloud Service zu erstellen:

1. Gehen Sie in Screens Content Provider zu Ihrem Kanal.

   >[!NOTE]
   >Weitere Informationen finden Sie unter [Verwenden von Screens Content Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=en#screens-content-provider).

1. Klicken Sie in der linken Navigationsleiste auf den Bereich Tools und dann auf **Assets** und klicken Sie anschließend auf **Verarbeitungsprofile**.

   ![Auf Verarbeitungsprofile klicken](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Klicken **Erstellen** , um ein Verarbeitungsprofil zu erstellen.

   ![Klicken Sie auf Erstellen](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Geben Sie den **Namen** ein, z. B. **ScreensVerarbeitungsprofil**.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Navigieren Sie zu **Video** Registerkarte, damit Sie eine Videokodierung hinzufügen können, und klicken Sie dann auf **Neu hinzufügen**.

   ![](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Geben Sie den **Kodierungsnamen**, wie z. B. **screens-fullhd** und die **Bitrate** als **2500** ein.

   ![](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Verwenden Sie den Kodierungsnamen, der mit &quot;screens-&quot;beginnt. Nur bei diesen Videoausgabeformaten wird davon ausgegangen, dass sie das Videoerlebnis in Screens as a Cloud Service wiedergeben. Geben Sie die Bitrate ein, mit der Ihre Videos funktionieren (2500 kBit/s für 720 px und 5000 kBit/s für 1080 px).

   >[!NOTE]
   >Für Videos können mehrere Video-Ausgabedarstellungen mit unterschiedlicher Breite/Höhe/Bitrate hinzugefügt werden. Alle Bildschirme und Ausgabedarstellungen werden von den Screens-Geräten heruntergeladen, auch wenn das Gerät nur die Videoausgabedarstellung wiedergibt.

1. Klicken Sie auf **Speichern**.

1. Wählen Sie das Verarbeitungsprofil aus und klicken Sie auf **Anwenden von Profilen auf Ordner**.

   ![Profil auf Ordner anwenden](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Wählen Sie die Ordner aus, in denen Screens-Videos aufbewahrt werden, und klicken Sie auf **Anwenden**.

   ![Klicken Sie auf Übernehmen](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >
   >* Sie können mehrere Verarbeitungsprofile erstellen und sie auf die entsprechenden Ordner anwenden, sodass die Videos in diesen Ordnern die spezifischen Video-Ausgabedarstellungen erhalten.
   >* Wenn Sie Videos in den Ordner hochladen, auf den ein Verarbeitungsprofil angewendet wird, werden Videos verarbeitet. Konfigurierte Ausgabeformate werden erstellt, die von den Screens-Geräten zur Wiedergabe der Videos verwendet werden.
