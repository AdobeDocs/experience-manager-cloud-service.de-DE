---
title: Implementierungsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Implementierungsphase in Cloud Acceleration Manager.
exl-id: e6ac88f0-4b3f-43a1-98bc-8c6608713784
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 31%

---

# Implementierungsphase in Cloud Acceleration Manager {#implementation-phase-cam}

Die Implementierungsphase umfasst:

* [Lokale Entwicklung](#local-development)
* [Code-Refaktorierung](#code-refactoring)
* [Bereitstellung von AEM as a Cloud Service](#aem-as-a-cloud-service-deployment)
* [Inhaltstransfer](#content-transfer)


Klicken Sie auf Ihre Projektkarte, damit Sie die Projekt-Landingpage öffnen und zur **Implementierung** -Abschnitt, wie in der folgenden Abbildung dargestellt.

![Bild](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Siehe [Erstellen und Verwalten eines Projekts in Cloud Acceleration Manager](getting-started-cam.md#create-project) , um mehr zu erfahren.


## Verwenden der Karte „Lokale Entwicklung“ {#local-development}

Die Karte Lokale Entwicklung bietet alle relevanten Inhalte, die Ihnen bei der Einrichtung Ihrer lokalen AEM-Entwicklungsumgebung während der Implementierungsphase Ihrer Migration-Journey helfen können.

Gehen Sie wie in diesem Abschnitt beschrieben vor, um die Karte für die Aktivität &quot;Lokale Entwicklung&quot;zu erkunden:

1. Klicks **Ansicht** aus dem **Lokale Entwicklung** Karte.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration an.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## Verwenden der Karte „Code-Umgestaltung“ {#code-refactoring}

Die Karte für die Code-Refaktorierungs-Aktivität enthält alle relevanten Informationen und hebt die Code-Refaktorierungsbereiche hervor, die beim Wechsel zu AEM as a Cloud Service zu überprüfen und zu beheben sind.

Gehen Sie wie in diesem Abschnitt beschrieben vor, um die Karte der Code-Refaktorierungs-Aktivität zu erkunden:

1. Klicks **Überprüfen** aus dem **Code-Umgestaltung** Aktivitätskarte.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. Auf der Seite wird eine Liste der Code-Umgestaltungsaktivitäten nach Schweregrad angezeigt. Weitere Informationen erhalten Sie durch Klicken auf die beiden hervorgehobenen Symbole.

   Auf der Seite sind auf drei Registerkarten die verschiedenen Aspekte der Code-Umgestaltung aufgeführt:

   * Übersicht
   * Dispatcher
   * Testen

>[!NOTE]
>Lesen Sie den Inhalt in diesen Registerkarten, um einige zusätzliche Bereiche zu verstehen, die nicht von Best Practices Analyzer abgedeckt werden.

Die **Dispatcher** -Tab enthält Informationen zum Strukturieren der AEM as a Cloud Service Apache- und Dispatcher-Konfigurationen und zum lokalen Validieren und Ausführen vor der Bereitstellung in Cloud-Umgebungen. Außerdem wird das Debugging in Cloud-Umgebungen beschrieben.

![image](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

Die Registerkarte **Testen** enthält Informationen zu Funktions-, Erlebnis-Audit- und UI-Tests.

![image](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## Verwenden der Karte „Bereitstellung von AEM as a Cloud Service“ {#aem-as-a-cloud-service-deployment}

AEM as a Cloud Service Bereitstellungskarte enthält alle relevanten Inhalte, mit denen Sie Ihren Code für AEM as a Cloud Service bereitstellen können.

Gehen Sie wie in diesem Abschnitt beschrieben vor, um AEM Karte der as a Cloud Service Bereitstellungskarte zu sehen:

1. Klicks **Ansicht** aus dem **AEM as a Cloud Service Bereitstellung** Aktivitätskarte.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration an.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Verwenden der Karte „Inhaltstransfer“ {#content-transfer}

Mit der Karte Inhaltstransfer können Sie den Inhaltstransfer von Ihrer aktuellen AEM auf AEM as a Cloud Service starten und verwalten.

Folgen Sie diesem Abschnitt, damit Sie die Karte der Aktivität Inhaltstransfer erkunden können:

1. Klicks **Überprüfen** aus dem **Content Transfer** Aktivitätskarte.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-1.png)

1. Um einen Inhaltstransfer zu starten, müssen Sie einen Migrationssatz erstellen. Klicks **Migrationssatz erstellen**. Ein Migrationssatz ermöglicht die Übertragung von Inhalten zu AEM as a Cloud Service.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-2.png)

   >[!NOTE]
   >Ein Migrationssatz läuft nach einer längeren Inaktivitätsdauer ab. Siehe [Ablauf des Migrationssatzes](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) für Details.

   >[!NOTE]
   >Siehe [Voraussetzungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html) und [Best Practices und Richtlinien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de) vor der Verwendung des Content Transfer Tool.

1. Laden Sie das Content Transfer Tool herunter und installieren Sie es, um den Migrationssatz zu füllen und die Extraktionsphase der Inhaltstransfer abzuschließen. Lesen Sie [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de), um zu erfahren, wie man das Content Transfer Tool verwendet.

1. Um as a Cloud Service Inhalte aus dem Migrationssatz in eine Umgebung aufzunehmen, müssen Sie eine Aufnahme starten. Navigieren Sie zu **Aufnahmevorgänge** und klicken **Neue Erfassung**. Überprüfen [Erfassen von Inhalten in Target](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html?lang=de) damit Sie lernen können, wie Sie die Aufnahmephase der Inhaltstransfer abschließen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-3.png)

<!--### Estimating Content Transfer Time {#calculating}

A Content Transfer Tool calculator has been provided to estimate how long it could take to complete the content transfer activity. You can use the content repository size slider to select the size that applies to your project. The transfer times vary for the extraction and ingestion phases. 

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-4.png)

   >[!NOTE]
   >These times are estimates only. Factor such as network speeds and time to scale up instances have not been accounted for in these estimates.

To estimate the size of the AEM Repository, you can run the Disk Usage report under `http://HOST:PORT/etc/reports/diskusage.html`. 

You can also estimate the size of specific repository paths by using the `path` parameter, for example, `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`. -->

## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie sich bei Cloud Acceleration Manager anmelden und wie Sie die Implementierungsphase verwenden, können Sie den nächsten Schritt im [Live-Phase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-golive-phase.html).
