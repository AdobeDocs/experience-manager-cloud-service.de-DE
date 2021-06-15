---
title: Ausführen einer Pipeline
description: Auf dieser Seite wird die Ausführung einer Pipeline für Screens als Cloud Service-Projekt in Cloud Manager beschrieben.
hide: true
hidefromtoc: true
index: false
source-git-commit: 83d2ac2d22827ebe13578b900907dd089d8d7e45
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 8%

---


# Ausführen einer Pipeline für Screens as a Cloud Service-Programm in Cloud Manager {#run-pipeline-screens-cloud}

In diesem Abschnitt wird beschrieben, wie Sie die Pipeline ausführen und Ihren Code für Ihr Programm in Cloud Manager bereitstellen.

>[!NOTE]
>Unter [Konfigurieren der CD-CD-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en) und [Bereitstellen Ihres Codes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de) erfahren Sie, wie Sie die Pipeline für Ihr Programm in Cloud Manager ausführen können.

## Vorgabe {#objective}

Im folgenden Abschnitt wird beschrieben, wie Sie die CI/CD-Pipeline konfigurieren und Ihren Code für Ihr Programm in Cloud Manager bereitstellen.

## Schritte zum Ausführen einer Pipeline für Ihr Screens-Projekt in Cloud Manager {#steps-branch-creation}

1. Sobald die Einrichtung der Umgebung erfolgreich abgeschlossen ist, wird auf der Seite **Übersicht** von Cloud Manager das Update der Aktionskarte angezeigt.

   ![image](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. Klicken Sie auf **Pipeline** auf der Seite **Übersicht** .

1. Klicken Sie auf **Weiter** , nachdem Sie die Verzweigung ausgewählt haben.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. Wählen Sie Ihre Optionen im Assistenten **Pipeline** einrichten aus. Klicken Sie auf **Save**.

   >[!NOTE]
   >Weitere Informationen zu den Optionen im Assistenten Pipeline einrichten finden Sie unter [Konfigurieren der Pipeline-Einstellungen von Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en) .

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. Sobald die Einrichtungs-Pipeline abgeschlossen ist, wird die Aktionskarte aktualisiert, wie in der folgenden Abbildung dargestellt. Klicken Sie auf Bereitstellen .

   >[!NOTE]
   >Weitere Informationen zu den Bereitstellungsetappen in Cloud Manager finden Sie unter [Bereitstellen Ihres Codes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en).

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. Klicken Sie auf **Build** , um den Build-Prozess zu starten.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. Sobald der Build-Prozess abgeschlossen ist, wird ein Autorenlink von der Karte **Umgebungen** auf der Seite **Übersicht** von Cloud Manager angezeigt.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## Wie geht es weiter {#whats-next}

Sobald Sie wissen, wie Sie eine Umgebung für Ihr Programm in Cloud Manager einrichten, können Sie mit dem nächsten Schritt im Onboarding-Prozess fortfahren, d. h. [Navigieren Sie zum Screens-Dienstanbieter](/help/screens-cloud/configuring/navigating-to-screens-services-provider.md).