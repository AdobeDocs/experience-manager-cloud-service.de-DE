---
title: Implementierungsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Implementierungsphase in Cloud Acceleration Manager.
exl-id: 4ea13f12-7251-448f-9f54-c8d710aef2ba
source-git-commit: e786fe40d97294b4ab5e8657920f2ecbb401d8e9
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 5%

---

# Implementierungsphase in Cloud Acceleration Manager {#implementation-phase-cam}

Die Implementierungsphase umfasst:

* [Lokale Entwicklung](#local-development)
* [Code-Umgestaltung](#code-refactoring)
* [Bereitstellung AEM Cloud Service](#aem-as-a-cloud-service-deployment)
* [Inhaltstransfer](#content-transfer)


Klicken Sie auf Ihre Projektkarte, um die Projekt-Landingpage zu öffnen und zum Abschnitt **Implementierung** zu navigieren, wie in der folgenden Abbildung dargestellt.

![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Weitere Informationen finden Sie unter [Erstellen und Verwalten eines Projekts in Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en#create-project) .


## Verwenden der lokalen Entwicklungskarte {#local-development}

Die Karte Lokale Entwicklung enthält alle relevanten Inhalte, die Ihnen beim Einrichten Ihrer lokalen AEM-Entwicklungsumgebung während der Implementierungsphase Ihrer Migration-Journey helfen.

In diesem Abschnitt erhalten Sie Informationen zur Karte der Aktivität &quot;Lokale Entwicklung&quot;:

1. Klicken Sie auf die Schaltfläche **Ansicht** auf der Karte **Lokale Entwicklung** .

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-2.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration-Journey an.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-3.png)


## Verwenden der Code-Refaktorierungskarte {#code-refactoring}

Die Karte der Code-Refaktorierungs-Aktivität enthält alle relevanten Informationen und hebt die Code-Refaktorierungsbereiche hervor, die Sie beim Wechsel zu AEM als Cloud Service überprüfen und auflösen müssen.

In diesem Abschnitt erfahren Sie, wie Sie die Karte für die Code-Refaktorierungs-Aktivität aufrufen:

1. Klicken Sie auf die Schaltfläche **Überprüfen** auf der Aktivitätskarte **Code-Refaktorierung** .

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-4.png)

1. Auf der Seite wird die Liste der Code-Refaktorierungs-Aktivitäten nach Schweregrad-Ebene angezeigt. Weitere Informationen erhalten Sie, wenn Sie auf die beiden hervorgehobenen Symbole klicken.

   Auf der Seite werden die Überlegungen zur Code-Umgestaltung auf drei verschiedenen Registerkarten angezeigt:

   * Übersicht
   * Dispatcher
   * Tests

>[!NOTE]
>Lesen Sie den Inhalt in diesen Registerkarten, um einige zusätzliche Bereiche zu verstehen, die nicht von Best Practices Analyzer abgedeckt werden.

Die Registerkarte **Dispatcher** enthält Informationen zur Struktur der Apache- und Dispatcher-Konfigurationen für AEM als Cloud Service sowie dazu, wie sie vor der Bereitstellung in Cloud-Umgebungen lokal validiert und ausgeführt werden. Außerdem wird das Debugging in Cloud-Umgebungen beschrieben.

![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/coderefactoring-2.png)

Die Registerkarte **Testen** enthält Informationen zu Funktions-, Erlebnis-Audit- und UI-Tests.

![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/coderefactoring-3.png)


## AEM as a Cloud Service Deployment Card verwenden {#aem-as-a-cloud-service-deployment}

AEM as a Cloud Service Deployment-Karte enthält alle relevanten Inhalte, die Ihnen bei der Bereitstellung Ihres Codes für AEM als Cloud Service helfen.

In diesem Abschnitt erfahren Sie, wie Sie die Aktivitätskarte AEM as a Cloud Service Deployment Card nutzen:

1. Klicken Sie auf die Schaltfläche **Anzeigen** auf der Aktivitätskarte **AEM als Cloud Service-Bereitstellung** .

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-6.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration-Journey an.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Verwenden der Content Transfer Card {#content-transfer}

Die Karte für die Aktivität &quot;Inhaltstransfer&quot;enthält Anleitungen und Überlegungen, die bei Verwendung des Content Transfer Tool überprüft werden sollten, um Inhalte von Ihrer aktuellen AEM-Instanz in AEM als Cloud Service zu verschieben.

In diesem Abschnitt erfahren Sie mehr über die Karte der Aktivität &quot;Inhaltstransfer&quot;:

1. Klicken Sie auf die Schaltfläche **Ansicht** auf der Aktivitätskarte **Inhaltstransfer** .

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-8.png)

1. Ein Inhaltskarussell zeigt die relevanten Informationen für diese Phase der Migration-Journey an.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/content-transfertool-card.png)

   >[!NOTE]
   >Lesen Sie die [Voraussetzungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en) und die [Best Practices und Richtlinien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de) , bevor Sie das Content Transfer Tool verwenden.

### Schätzen der Content Transfer Time {#calculating}

Es wurde ein neuer Content Transfer Tool-Rechner bereitgestellt, der schätzt, wie lange es dauern könnte, bis die Aktivität zur Inhaltstransfer abgeschlossen ist. Mit dem Größenregler des Inhalts-Repositorys können Sie die Größe auswählen, die für Ihr Projekt gilt. Die Übertragungszeiten variieren je nach Extraktions- und Aufnahmephase.

>[!NOTE]
>Diese Zeiten sind nur Schätzungen. Faktoren wie Netzwerkgeschwindigkeiten und die Zeit zum Vergrößern von Instanzen wurden in diesen Schätzungen nicht berücksichtigt.

Um die Größe des AEM-Repositorys zu schätzen, können Sie den Bericht zur Festplattenauslastung unter `http://HOST:PORT/etc/reports/diskusage.html` ausführen.

Sie können die Größe bestimmter Repository-Pfade auch mithilfe des Parameters `path` schätzen, z. B. `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`.

## Wie geht es weiter {#whats-next}

Sobald Sie erfahren haben, wie Sie sich bei Cloud Acceleration Manager anmelden und wie Sie die Implementierungsphase nutzen, können Sie nun den nächsten Schritt im Abschnitt [Go Live Phase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=en) überprüfen.
