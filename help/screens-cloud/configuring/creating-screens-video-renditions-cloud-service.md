---
title: Erstellen von Video-Ausgabedarstellungen in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Video-Ausgabedarstellungen in Screens as a Cloud Service erstellen.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
source-git-commit: 900cdc53475446b9d93cb071f281da5dbe043888
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 93%

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
   >Weitere Informationen finden Sie unter [Verwenden von Screens Content Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=de#screens-content-provider).

1. Klicken Sie in der linken Navigationsleiste auf den Abschnitt „Tools“, dann auf **Assets** und dann auf **Verarbeitungsprofile**.

   ![Klicken auf „Verarbeitungsprofile“](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Klicken Sie auf **Erstellen**, um ein Verarbeitungsprofil zu erstellen.

   ![Klicken auf „Erstellen“](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Geben Sie den **Namen** ein, z. B. **ScreensVerarbeitungsProfil**.

   ![Dialogfeld &quot;Verarbeitungsprofil&quot;mit hervorgehobenem Feld &quot;Name&quot;](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Navigieren Sie zur Registerkarte **Video**, um eine Videocodierung hinzuzufügen, und klicken Sie dann auf **Neue hinzufügen**.

   ![Dialogfeld &quot;Verarbeitungsprofil&quot;mit hervorgehobener Schaltfläche &quot;Neu hinzufügen&quot;](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Geben Sie den **Codierungsnamen** wie z. B. **screens-fullhd** und die **Bitrate** als **2500** ein.

   ![Dialogfeld &quot;Verarbeitungsprofil&quot;mit hervorgehobener Schaltfläche Speichern.](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Verwenden Sie den Codierungsnamen, der mit „screens-“ beginnt. Nur bei diesen Videoausgabedarstellungen wird davon ausgegangen, dass sie das Videoerlebnis in Screens as a Cloud Service wiedergeben. Geben Sie die Bitrate ein, mit der Ihre Videos funktionieren (2500 kbps für Videos mit 720 px und 5000 kbps für 1080 px).

   >[!NOTE]
   >Für Ihre Videos können mehrere Video-Ausgabedarstellungen mit unterschiedlicher Breite/Höhe/Bitrate hinzugefügt werden. Alle „screens-“-Ausgabedarstellungen werden von den Screens-Geräten heruntergeladen, auch wenn das Gerät nur Video-Ausgabedarstellungen wiedergibt.

1. Klicken Sie auf **Speichern**.

1. Wählen Sie das Verarbeitungsprofil aus und klicken Sie auf **Profil auf Ordner anwenden**.

   ![Profil auf Ordner anwenden](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Wählen Sie die Ordner aus, in denen Screens-Videos gespeichert werden, und klicken Sie auf **Anwenden**.

   ![Klicken auf „Übernehmen“](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >
   >* Sie können mehrere Verarbeitungsprofile erstellen und sie auf die entsprechenden Ordner anwenden, sodass die Videos in diesen Ordnern die spezifischen Video-Ausgabedarstellungen erhalten.
   >* Wenn Sie Videos in einen Ordner hochladen, auf den ein Verarbeitungsprofil angewendet wird, werden die Videos verarbeitet. Es werden konfigurierte Ausgabedarstellungen erstellt, die von den Screens-Geräten zur Wiedergabe der Videos verwendet werden.
