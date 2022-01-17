---
title: Erstellen von Video-Ausgabedarstellungen in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Video-Ausgabedarstellungen in Screens as a Cloud Service erstellen.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: ht
source-wordcount: '346'
ht-degree: 100%

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
   >Weitere Informationen finden Sie unter [Verwenden von Screens Content Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=de#screens-content-provider).

1. Klicken Sie in der linken Navigationsleiste auf den Abschnitt „Tools“, dann auf **Assets** und dann auf **Verarbeitungsprofile**.

   ![](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Klicken Sie auf **Erstellen**, um ein neues Verarbeitungsprofil zu erstellen.

   ![](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Geben Sie den **Namen** ein, z. B. **ScreensVerarbeitungsprofil**.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Gehen Sie zur Registerkarte **Video**, um eine Videokodierung hinzuzufügen, und klicken Sie auf **Neue hinzufügen**.

   ![](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Geben Sie den **Kodierungsnamen**, wie z. B. **screens-fullhd** und die **Bitrate** als **2500** ein.

   ![](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Achten Sie darauf, dass Sie einen Kodierungsnamen verwenden, der mit „screens-“ beginnt. Nur diese Video-Ausgabedarstellungen werden für die Wiedergabe des Videoerlebnisses in Screens as a Cloud Service berücksichtigt. Geben Sie die Bitrate ein, mit der Ihre Videos funktionieren (2500 kbps für Videos mit 720 px und 5000 kbps für 1080 px).

   >[!NOTE]
   >Für Videos können mehrere Video-Ausgabedarstellungen mit unterschiedlicher Breite/Höhe/Bitrate hinzugefügt werden. Beachten Sie, dass alle „screens-“-Ausgabedarstellungen von den Screens-Geräten heruntergeladen werden, auch wenn das Gerät nur Video-Ausgabedarstellungen wiedergibt.

1. Klicken Sie auf **Speichern**.

1. Wählen Sie das Verarbeitungsprofil aus und klicken Sie auf **Profil auf Ordner anwenden**.

   ![](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Wählen Sie die Ordner aus, in denen Screens-Videos gespeichert werden, und klicken Sie auf **Anwenden**.

   ![](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >* Sie können mehrere Verarbeitungsprofile erstellen und sie auf die entsprechenden Ordner anwenden, sodass die Videos in diesen Ordnern die spezifischen Video-Ausgabedarstellungen erhalten.
   >* Wenn Sie Videos in den Ordner hochladen, auf den das Verarbeitungsprofil angewendet wird, werden Videos verarbeitet und konfigurierte Ausgabedarstellungen erstellt, die von den Screens-Geräten zur Wiedergabe der Videos verwendet werden.

