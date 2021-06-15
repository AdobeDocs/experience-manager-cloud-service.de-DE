---
title: Implementierungsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Implementierungsphase in Cloud Acceleration Manager.
hide: true
hidefromtoc: true
index: false
source-git-commit: 5af319d30198329fd2312c11d88bf326bc4cdae7
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 3%

---


# Implementierungsphase in Cloud Acceleration Manager {#implementation-phase-cam}

Die Implementierungsphase umfasst:

* [Lokale Entwicklung](#local-development)
* [Code-Umgestaltung](#code-refactoring)
* [Bereitstellung AEM Cloud Service](#aem-as-a-cloud-service-deployment)
* [Inhaltstransfer](#content-transfer)

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-1.png)

## Verwenden der lokalen Entwicklungskarte {#local-development}

Die Karte Lokale Entwicklung enthält alle relevanten Inhalte, die Ihnen beim Einrichten Ihrer lokalen AEM-Entwicklungsumgebung während der Implementierungsphase Ihrer Migration-Journey helfen.

In diesem Abschnitt erhalten Sie Informationen zur Karte der Aktivität &quot;Lokale Entwicklung&quot;:

1. Klicken Sie auf die Schaltfläche **Ansicht** auf der Karte **Lokale Entwicklung** .

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-2.png)

1. Es wird ein Inhaltskarussell mit relevanten Informationen für diese Journey-Phase der Migration angezeigt.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-3.png)


## Verwenden der Code-Refaktorierungs-Karte {#code-refactoring}

Die Karte der Code-Refaktorierungs-Aktivität enthält alle relevanten Informationen und hebt die Code-Refaktorierungsbereiche hervor, die Sie beim Wechsel zu AEM as a Cloud Service überprüfen müssen.

In diesem Abschnitt erfahren Sie, wie Sie die Karte für die Code-Refaktorierungs-Aktivität aufrufen:

1. Klicken Sie auf die Schaltfläche **Überprüfen** auf der Aktivitätskarte **Code-Refaktorierung** .

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-4.png)

1. Auf der Seite wird die Liste der Code-Refaktorierungs-Aktivitäten nach Schweregrad-Ebene angezeigt. Weitere Informationen erhalten Sie, wenn Sie auf die beiden hervorgehobenen Symbole klicken.

   >[!NOTE]
   >Lesen Sie außerdem den Inhalt auf den Registerkarten der Seite, um mehr über einige zusätzliche Bereiche zu erfahren, die nicht von Best Practices Analyzer abgedeckt werden.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5.png)


## Verwenden der AEM als Cloud Service-Bereitstellungskarte {#aem-as-a-cloud-service-deployment}

AEM as a Cloud Service Deployment-Karte enthält alle relevanten Inhalte, die Ihnen bei der Bereitstellung Ihres Codes für AEM als Cloud Service helfen.

In diesem Abschnitt erfahren Sie, wie Sie die Aktivitätskarte AEM as a Cloud Service Deployment Card nutzen:

1. Klicken Sie auf die Schaltfläche **Anzeigen** auf der Karte **AEM als Cloud Service-Bereitstellung** .

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-4.png)

1. Es wird ein Inhaltskarussell mit relevanten Informationen für diese Journey-Phase der Migration angezeigt.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5.png)


## Verwenden der Content Transfer-Karte {#content-transfer}

Die Karte für die Aktivität &quot;Inhaltstransfer&quot;enthält Anleitungen und Überlegungen, die bei Verwendung des Content Transfer Tool überprüft werden sollten, um Inhalte von Ihrer aktuellen AEM-Instanz in AEM als Cloud Service zu verschieben.

In diesem Abschnitt erfahren Sie mehr über die Karte der Aktivität &quot;Inhaltstransfer&quot;:

1. Klicken Sie auf die Schaltfläche **Ansicht** auf der Karte **Lokale Entwicklung** .

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-4.png)

1. Es wird ein Inhaltskarussell mit relevanten Informationen für diese Journey-Phase der Migration angezeigt.

   ![image](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5.png)

>[!NOTE]
>Lesen Sie die [Voraussetzungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en) und die [Best Practices und Richtlinien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en) , bevor Sie das Content Transfer Tool verwenden.

Es wurde ein neuer Content Transfer Tool-Rechner bereitgestellt, der schätzt, wie lange es dauern könnte, bis die Aktivität zur Inhaltstransfer abgeschlossen ist. Mit dem Größenregler des Inhalts-Repositorys können Sie die Größe auswählen, die für Ihr Projekt gilt. Die Übertragungszeiten variieren je nach Extraktions- und Aufnahmephase. Um die Größe des AEM-Repositorys zu schätzen, können Sie den Bericht zur Festplattenauslastung unter `http://HOST:PORT/etc/reports/diskusage.html` ausführen.

Sie können die Größe bestimmter Repository-Pfade auch mithilfe des Parameters `path` schätzen, z. B. `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`.
