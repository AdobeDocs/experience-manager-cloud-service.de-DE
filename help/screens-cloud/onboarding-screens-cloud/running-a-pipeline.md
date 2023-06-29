---
title: Ausführen einer Pipeline
description: Auf dieser Seite wird die Ausführung einer Pipeline für ein Screens as a Cloud Service-Projekt in Cloud Manager beschrieben.
exl-id: 3203cff7-5668-4f50-a2c5-80ae474b439d
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 39%

---

# Ausführen einer Pipeline für ein Screens as a Cloud Service-Programm in Cloud Manager {#run-pipeline-screens-cloud}

In diesem Abschnitt wird beschrieben, wie Sie die Pipeline ausführen und Ihren Code für Ihr Programm in Cloud Manager bereitstellen.

>[!NOTE]
>Siehe [Konfigurieren der CI/CD-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/configuring-production-pipelines.html?lang=en) und [Bereitstellen Ihres Codes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de) , um zu erfahren, wie Sie die Pipeline für Ihr Programm in Cloud Manager ausführen können.

## Ziel {#objective}

Im folgenden Abschnitt wird beschrieben, wie Sie die CI/CD-Pipeline konfigurieren und Ihren Code für Ihr Programm in Cloud Manager bereitstellen.

## Schritte zum Ausführen einer Pipeline für ein Screens-Projekt in Cloud Manager {#steps-branch-creation}

1. Nachdem die Einrichtung der Umgebung erfolgreich abgeschlossen wurde, wird die Karte für Aktionsaufrufe in der Cloud Manager-Konsole aktualisiert. **Übersicht** Seite.

   ![Bild](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. Klicken **Pipeline einrichten** von **Übersicht** Seite.

1. Klicken **Nächste** nach Auswahl der Verzweigung.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. Wählen Sie im Assistenten **Pipeline einrichten** Ihre Optionen aus. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >Weitere Informationen zu den Optionen im Assistenten &quot;Pipeline einrichten&quot;finden Sie unter [Konfigurieren der Pipeline-Einstellungen über Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/configuring-production-pipelines.html?lang=en) für weitere Details.

   ![Bild](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. Nachdem die Setup-Pipeline abgeschlossen ist, wird die Aktionsaufruf-Karte aktualisiert.

   >[!NOTE]
   >Informationen zu den Phasen der Implementierung in Cloud Manager finden Sie unter [Bereitstellen des Codes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de) für weitere Details.

   ![Bild](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. Klicken **Bereitstellen**.

1. Klicken **Build** , um den Build-Prozess zu starten.

   ![Bild](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. Nach Abschluss des Build-Prozesses wird ein Autorenlink aus dem **Umgebungen** Karte aus dem Cloud Manager **Übersicht** Seite.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie eine Umgebung für Ihr Programm in Cloud Manager einrichten, können Sie mit dem nächsten Schritt im Onboarding-Prozess fortfahren: [Navigieren zum Screens Services Provider](/help/screens-cloud/configuring/navigating-to-screens-services-provider.md).
