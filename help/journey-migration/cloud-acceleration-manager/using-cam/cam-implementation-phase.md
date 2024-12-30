---
title: Implementierungsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Implementierungsphase in Cloud Acceleration Manager.
exl-id: e6ac88f0-4b3f-43a1-98bc-8c6608713784
feature: Migration
role: Admin
source-git-commit: f86d681c8f8cb6d602058ef30b648c53ff7bad69
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 100%

---

# Implementierungsphase in Cloud Acceleration Manager {#implementation-phase-cam}

Die Implementierungsphase umfasst:

* [Lokale Entwicklung](#local-development)
* [Code-Refaktorierung](#code-refactoring)
* [Bereitstellung von AEM as a Cloud Service](#aem-as-a-cloud-service-deployment)
* [Inhaltstransfer](#content-transfer)


Klicken Sie auf Ihre Projektkarte, um die Projekt-Landingpage zu öffnen, und navigieren Sie zum Abschnitt **Implementierung**, wie in der folgenden Abbildung dargestellt.

![Projekt-Landingpage – Implementierung](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Weitere Informationen finden Sie unter [Erstellen und Verwalten eines Projekts in Cloud Acceleration Manager](getting-started-cam.md#create-project).


## Verwenden der Karte „Lokale Entwicklung“ {#local-development}

Die Karte „Lokale Entwicklung“ enthält alle relevanten Inhalte, die Ihnen beim Einrichten Ihrer lokalen AEM-Entwicklungsumgebung zu Beginn der Implementierungsphase Ihrer Migration helfen.

In diesem Abschnitt erhalten Sie Informationen zur Aktivitätskarte „Lokale Entwicklung“:

1. Klicken Sie auf **Anzeigen** auf der Karte **Lokale Entwicklung**.

   ![Karte „Lokale Entwicklung“](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration an.

   ![Karussell „Lokale Entwicklung“](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## Verwenden der Karte „Code-Umgestaltung“ {#code-refactoring}

Die Aktivitätskarte „Code-Refaktorierung“ enthält alle relevanten Informationen und hebt die Bereiche der Umgestaltung des Codes hervor, die Sie beim Wechsel zu AEM as a Cloud Service überprüfen und auflösen müssen.

In diesem Abschnitt erhalten Sie Informationen zur Aktivitätskarte „Code-Refaktorierung“:

1. Klicken Sie auf der Aktivitätskarte **Code-Refaktorierung** auf die Schaltfläche **Überprüfen**.

   ![Karte „Code-Refaktorierung“](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. Auf der Seite wird eine Liste der Code-Refaktorierungsaktivitäten nach Schweregrad angezeigt. Weitere Informationen erhalten Sie, wenn Sie auf die beiden hervorgehobenen Symbole klicken.

   Auf der Seite sind auf drei Registerkarten die verschiedenen Aspekte der Code-Umgestaltung aufgeführt:

   * Überblick
   * Dispatcher
   * Testen

>[!NOTE]
>Lesen Sie den Inhalt dieser Registerkarten, um einige zusätzliche Bereiche zu verstehen, die nicht vom Best Practices Analyzer abgedeckt werden.

Die Registerkarte **Dispatcher** enthält Informationen dazu, wie Sie die Apache- und Dispatcher-Konfigurationen von AEM as a Cloud Service strukturieren und vor der Bereitstellung in Cloud-Umgebungen lokal validieren und ausführen. Außerdem wird das Debugging in Cloud-Umgebungen beschrieben.

![Registerkarte „Dispatcher“](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

Die Registerkarte **Testen** enthält Informationen zu Funktions-, Erlebnis-Audit- und Benutzeroberflächentests.

![Registerkarte „Testen“](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## Verwenden der Karte „Bereitstellung von AEM as a Cloud Service“ {#aem-as-a-cloud-service-deployment}

Die Karte „Implementierung in AEM as a Cloud Service“ enthält alle relevanten Inhalte, die Ihnen bei der Implementierung Ihres Codes in AEM as a Cloud Service helfen.

In diesem Abschnitt erfahren Sie, wie Sie die Aktivitätskarte „Bereitstellung in AEM as a Cloud Service“ nutzen:

1. Klicken Sie auf der Aktivitätskarte **Bereitstellung in AEM as a Cloud Service** auf **Anzeigen**.

   ![Bereitstellung von AEM as a Cloud Service – Karte](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration an.

   ![Bereitstellung von AEM as a Cloud Service – Karussell](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Verwenden der Karte „Inhaltstransfer“ {#content-transfer}

Mit der Karte „Inhaltstransfer“ können Sie den Inhaltstransfer von Ihrer aktuellen AEM-Instanz zu AEM as a Cloud Service starten und verwalten.

In diesem Abschnitt erfahren Sie mehr über die Aktivitätskarte „Inhaltstransfer“:

1. Klicken Sie in der Aktivitätskarte **Inhaltsübertragung** auf **Überprüfen**. 

   ![Inhaltstransfer – Überprüfung](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-1.png)

1. Um einen Inhaltstransfer zu starten, müssen Sie einen Migrationssatz erstellen. Klicken Sie auf **Migrationssatz erstellen**. Ein Migrationssatz ermöglicht die Übertragung von Inhalten zu AEM as a Cloud Service.

   ![Erstellen eines Migrationssatzes](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-2.png)

   >[!NOTE]
   >Ein Migrationssatz läuft nach einer längeren Inaktivitätsdauer ab. Weitere Informationen finden Sie unter [Ablauf des Migrationssatzes](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry).

   >[!NOTE]
   >Siehe [Voraussetzungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=de) und die [Best Practices und Richtlinien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de), bevor Sie das Content Transfer Tool verwenden.

1. Laden Sie das Content Transfer Tool herunter und installieren Sie es, um den Migrationssatz zu füllen und die Extraktionsphase des Inhaltstransfers abzuschließen. Lesen Sie [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de), um zu erfahren, wie man das Content Transfer Tool verwendet.

1. Um Inhalte aus dem Migrationssatz in eine Umgebung von AEM as a Cloud Service aufzunehmen, müssen Sie eine Aufnahme starten. Navigieren Sie zu **Aufnahmevorgänge** und klicken Sie auf **Neue Aufnahme**. Lesen Sie [Aufnehmen von Inhalten in Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md), um zu erfahren, wie Sie die Aufnahmephase des Inhaltstransfers abschließen.

   ![Aufnahmevorgänge](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-3.png)

<!--### Estimating Content Transfer Time {#calculating}

A Content Transfer Tool calculator has been provided to estimate how long it could take to complete the content transfer activity. You can use the content repository size slider to select the size that applies to your project. The transfer times vary for the extraction and ingestion phases. 

   ![Content Transfer Tool calculator](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-4.png)

   >[!NOTE]
   >These times are estimates only. Factor such as network speeds and time to scale up instances have not been accounted for in these estimates.

To estimate the size of the AEM Repository, you can run the Disk Usage report under `http://HOST:PORT/etc/reports/diskusage.html`. 

You can also estimate the size of specific repository paths by using the `path` parameter, for example, `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`. -->

## So geht es weiter {#whats-next}

Nachdem Sie jetzt wissen, wie Sie sich bei Cloud Acceleration Manager anmelden und die Implementierungsphase nutzen, können Sie sich mit dem nächsten Schritt beschäftigen: der [Live-Schaltungsphase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=de).
