---
title: Implementierungsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Implementierungsphase in Cloud Acceleration Manager.
exl-id: e6ac88f0-4b3f-43a1-98bc-8c6608713784
source-git-commit: 24331b974ded34ef949cc3d6fb157b124c145dee
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 100%

---

# Implementierungsphase in Cloud Acceleration Manager {#implementation-phase-cam}

Die Implementierungsphase umfasst:

* [Lokale Entwicklung](#local-development)
* [Code-Refaktorierung](#code-refactoring)
* [Bereitstellung von AEM as a Cloud Service](#aem-as-a-cloud-service-deployment)
* [Inhaltstransfer](#content-transfer)


Klicken Sie auf Ihre Projektkarte, um die Projekt-Landingpage zu öffnen, und navigieren Sie zum Abschnitt **Implementierung**, wie in der folgenden Abbildung dargestellt.

![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Weitere Informationen finden Sie unter [Erstellen und Verwalten eines Projekts in Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=de#create-project).


## Verwenden der Karte „Lokale Entwicklung“ {#local-development}

Die Karte „Lokale Entwicklung“ enthält alle relevanten Inhalte, die Ihnen beim Einrichten Ihrer lokalen AEM-Entwicklungsumgebung zu Beginn der Implementierungsphase Ihrer Migration helfen.

In diesem Abschnitt erhalten Sie Informationen zur Aktivitätskarte „Lokale Entwicklung“:

1. Klicken Sie auf der Karte **Lokale Entwicklung** auf die Schaltfläche **Ansicht**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration an.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## Verwenden der Karte „Code-Umgestaltung“ {#code-refactoring}

Die Aktivitätskarte „Code-Refaktorierung“ enthält alle relevanten Informationen und hebt die Bereiche der Umgestaltung des Codes hervor, die Sie beim Wechsel zu AEM as a Cloud Service überprüfen und auflösen müssen.

In diesem Abschnitt erhalten Sie Informationen zur Aktivitätskarte „Code-Umgestaltung“:

1. Klicken Sie auf der Aktivitätskarte **Code-Umgestaltung** auf die Schaltfläche **Überprüfen**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. Auf der Seite wird eine Liste der Code-Umgestaltungsaktivitäten nach Schweregrad angezeigt. Weitere Informationen erhalten Sie, wenn Sie auf die beiden hervorgehobenen Symbole klicken.

   Auf der Seite sind auf drei Registerkarten die verschiedenen Aspekte der Code-Umgestaltung aufgeführt:

   * Übersicht
   * Dispatcher
   * Testen

>[!NOTE]
>Lesen Sie den Inhalt dieser Registerkarten, um einige zusätzliche Bereiche zu verstehen, die nicht vom Best Practices Analyzer abgedeckt werden.

Die Registerkarte **Dispatcher** enthält Informationen dazu, wie Sie die Apache- und Dispatcher-Konfigurationen von AEM as a Cloud Service strukturieren und vor der Bereitstellung in Cloud-Umgebungen lokal validieren und ausführen. Außerdem wird das Debugging in Cloud-Umgebungen beschrieben.

![image](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

Die Registerkarte **Testen** enthält Informationen zu Funktions-, Erlebnis-Audit- und UI-Tests.

![image](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## Verwenden der Karte „Implementierung von AEM as a Cloud Service“ {#aem-as-a-cloud-service-deployment}

Die Karte „Implementierung von AEM as a Cloud Service“ enthält alle relevanten Inhalte, die Ihnen bei der Bereitstellung Ihres Codes für AEM as a Cloud Service helfen.

In diesem Abschnitt erfahren Sie, wie Sie die Aktivitätskarte „Implementierung von AEM as a Cloud Service“ nutzen:

1. Klicken Sie auf der Aktivitätskarte **Implementierung von AEM as a Cloud Service** auf die Schaltfläche **Ansicht**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration an.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Verwenden der Karte „Inhaltstransfer“ {#content-transfer}

Mit der Karte „Inhaltstransfer“ können Sie den Inhaltstransfer von Ihrer aktuellen AEM zu AEM as a Cloud Service starten und verwalten.

In diesem Abschnitt erfahren Sie mehr über die Aktivitätskarte „Inhaltstransfer“:

1. Klicken Sie auf der Aktivitätskarte **Inhaltstransfer** auf die Schaltfläche **Ansicht**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-1.png)

1. Um einen Inhaltstransfer zu starten, müssen Sie einen Migrationssatz erstellen. Klicken Sie auf **Migrationssatz erstellen**. Ein Migrationssatz ermöglicht die Übertragung von Inhalten zu AEM as a Cloud Service.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-2.png)

   >[!NOTE]
   >Lesen Sie die [Voraussetzungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=de) und die [Best Practices und Richtlinien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de), bevor Sie das Content Transfer Tool verwenden.

1. Sie müssen das Content Transfer Tool herunterladen und installieren, um den Migrationssatz zu füllen und die Extraktionsphase des Inhaltstransfers abzuschließen. Lesen Sie [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de), um zu erfahren, wie man das Content Transfer Tool verwendet.

1. Um Inhalte aus dem Migrationssatz in eine Umgebung von AEM as a Cloud Service aufzunehmen, müssen Sie eine Aufnahme starten. Gehen Sie zu **Aufnahmevorgänge** und klicken Sie auf **Neue Aufnahme**. Lesen Sie [Aufnehmen von Inhalten in Target](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html?lang=de), um zu erfahren, wie Sie die Aufnahmephase des Inhaltstransfers abschließen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-3.png)

### Schätzen der Inhaltstransferdauer {#calculating}

Der Content Transfer Tool-Rechner schätzt, wie lange es bis zum Abschluss des Inhaltstransfers dauern könnte. Mit dem Größenregler des Content-Repositorys können Sie die Größe für Ihr Projekt auswählen. Die Übertragungszeiten sind in Extraktions- und Aufnahmephase unterschiedlich.

![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-4.png)

>[!NOTE]
>Die Zeiten sind lediglich Schätzungen. Faktoren wie Netzwerkgeschwindigkeiten und die Zeit zum Hochsetzen von Instanzen wurden bei diesen Schätzungen nicht berücksichtigt.

Um die Größe des AEM-Repositorys zu schätzen, können Sie den Bericht zur Festplattenauslastung unter `http://HOST:PORT/etc/reports/diskusage.html` ausführen.

Sie können die Größe bestimmter Repository-Pfade auch mithilfe des Parameters `path` schätzen, z. B. `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`.

## Wie geht es weiter {#whats-next}

Sobald Sie wissen, wie Sie sich bei Cloud Acceleration Manager anmelden und die Implementierungsphase nutzen, können Sie sich mit dem nächsten Schritt beschäftigen: der [Live-Phase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=de).
