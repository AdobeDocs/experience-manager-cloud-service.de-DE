---
title: Ausführen einer Pipeline
description: Auf dieser Seite wird die Ausführung einer Pipeline für ein Screens as a Cloud Service-Projekt in Cloud Manager beschrieben.
exl-id: 3203cff7-5668-4f50-a2c5-80ae474b439d
feature: Screens Deployments
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 100%

---

# Ausführen einer Pipeline für ein Screens as a Cloud Service-Programm in Cloud Manager {#run-pipeline-screens-cloud}

In diesem Abschnitt wird beschrieben, wie Sie die Pipeline ausführen und Ihren Code für Ihr Programm in Cloud Manager bereitstellen.

>[!NOTE]
>Unter [Konfigurieren der CD/CD-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/configuring-production-pipelines.html?lang=de) und [Bereitstellen von Codes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de) erfahren Sie, wie Sie die Pipeline für Ihr Programm in Cloud Manager ausführen können.

## Ziel {#objective}

Im folgenden Abschnitt wird beschrieben, wie Sie die CI/CD-Pipeline konfigurieren und Ihren Code für Ihr Programm in Cloud Manager bereitstellen.

## Schritte zum Ausführen einer Pipeline für ein Screens-Projekt in Cloud Manager {#steps-branch-creation}

1. Nachdem die Einrichtung der Umgebung erfolgreich abgeschlossen wurde, wird auf der Seite **Überblick** von Cloud Manager das Update der Karte mit dem Aktionsaufruf angezeigt.

   ![Bild](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. Klicken Sie auf der Seite **Überblick** auf **Pipeline einrichten**.

1. Klicken Sie auf **Weiter**, nachdem Sie die Verzweigung ausgewählt haben.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. Wählen Sie im Assistenten **Pipeline einrichten** Ihre Optionen aus. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >Weitere Informationen zu den Optionen im Assistenten „Pipeline einrichten“ finden Sie unter [Konfigurieren der Pipeline-Einstellungen von Cloud Manager aus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/configuring-production-pipelines.html?lang=de).

   ![Bild](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. Wenn die Einrichtung der Pipeline abgeschlossen ist, wird die Karte mit dem Aktionsaufruf aktualisiert.

   >[!NOTE]
   >Weitere Informationen zu den Phasen der Bereitstellung in Cloud Manager finden Sie unter [Bereitstellen von Code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de).

   ![Bild](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. Klicken Sie auf **Bereitstellen**.

1. Klicken Sie auf **Erstellen**, um den Erstellungsprozess zu starten.

   ![Bild](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. Sobald der Build-Prozess abgeschlossen ist, wird ein Autoren-Link von der Karte **Umgebungen** auf der Seite **Überblick** von Cloud Manager angezeigt.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie erfahren haben, wie Sie eine Umgebung für Ihr Programm in Cloud Manager einrichten, können Sie mit dem nächsten Schritt im Onboarding-Prozess fortfahren, d. h. [Navigieren zu Screens Services Provider](/help/screens-cloud/configuring/navigating-to-screens-services-provider.md).
