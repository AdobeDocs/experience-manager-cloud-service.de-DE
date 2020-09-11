---
title: Wichtige Änderungen beim AEM als Cloud Service
description: Es wurden erhebliche Änderungen an AEM Commerce als Cloud Service gegenüber Adobe Experience Manager 6.5 vorgenommen.
translation-type: tm+mt
source-git-commit: 2934d0d8d3977bb7884bae9654ac26e9fa57b34f
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 12%

---


# Notable changes to AEM Commerce as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer AEM-Projekte. In diesem Dokument werden die wichtigen Unterschiede zwischen Commerce-Integrationsrahmen (CIF) für On-Premise, Adobe Managed Service und Experience Manager als Cloud Service hervorgehoben. Weitere Änderungen finden Sie im Abschnitt zu den allgemeinen [Änderungen an Adobe Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Die Hauptunterschiede gegenüber Adobe Experience Manager 6.5 bestehen in den folgenden Bereichen:
* [Unterstützung für CIF Classic](#cif-classic)
* [Bereitstellung der CIF-Authoring-Werkzeuge](#cif-tools)
* [Umstellung von einem Vor-Ort- und Adobe-Managed Service](#moving-cif-cs)

## Unterstützung für CIF Classic/Quickstart auf Experience Manager als Cloud Service {#cif-classic}

Das Classic Commerce Integration Framework, das einen Product Importer zum Importieren und Speichern von Produktkatalogen in Experience Manager enthielt, ist in Experience Manager nicht mehr als Cloud Service verfügbar. Die Verwendung von Classic CIF wird in Experience Manager nicht unterstützt, da ein Cloud Service und Projekte, die Classic CIF verwenden, die Classic CIF-Implementierung durch die unterstützte Version ersetzen müssen, wie in [CIF auf Experience Manager als Cloud Service beschrieben](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/commerce/architecture/magento.html#overview)

## Bereitstellung von CIF {#deployment}

Nachfolgend sind die verschiedenen Bereitstellungsmodelle für Commerce Integration Framework für die verschiedenen AEM aufgeführt:

|  | AEM vor Ort | AEM Managed Services | AEM Cloud Service |
|-------------     |-----------|-----------|-----------|
| Bereitstellung von CIF-Authoring-Werkzeugen für Magento-Backend | [Informationen zu CIF Connector](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) , der auf AEM 6.5 unterstützt wird | [Informationen zu CIF Connector](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) , der auf AEM 6.5 unterstützt wird | AEM als Cloud Service muss mit CIF-Add-On bereitgestellt werden. Weitere Informationen erhalten Sie von Ihrem Vertriebsmitarbeiter |
| Bereitstellung des [CIF-Venia-Projekts](https://github.com/adobe/aem-cif-guides-venia) | AEM Paketinstallation | Bereitstellung über [Cloud Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) | Projekt in [Cloud Manager Git Repository](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) und Bereitstellung über [Cloud Manager verschoben](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/deploying/overview.html) |

>[!NOTE]
>
>Weitere Dokumentation zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)

>[!NOTE]
>
>CIF Classic/Quickstart Version von Commerce Integration Framework kann für AEM On-Premise-Angebot in sehr begrenzten Anwendungsfällen verwendet werden. Dies ist jedoch nicht die empfohlene Lösung.

## Auf dem Weg zu AEM Handel als Cloud Service von On-Premise und Managed Services {#moving-cif-cs}

Kunden, die von einer AEM-Installation vor Ort oder einer Managed Services-Installation zu AEM wechseln, müssen einige kleinere Anpassungen am AEM vornehmen.

Die erste Anpassung, wie oben beschrieben, ist für den CIF Connector erforderlich. Der CIF-Connector wird durch das CIF-Add-on ersetzt, das von der Adobe bereitgestellt wird. Installieren Sie daher CIF Connector nicht auf AEM als Cloud Service. Außerdem wird die Verwendung mit dem lokalen AEM Cloud SDK nicht unterstützt. Adobe bietet das CIF-Add-on auch für die [lokale Entwicklung](develop.md).

Zweitens sollten Sie die [AEM Projektstruktur](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) und die Merkmale von AEM als Cloud Service verstehen. Passen Sie Ihre Projekteinrichtung als Cloud Service-Layout an die AEM an.
Die wichtigsten Unterschiede sind:

* Das GraphQL Client OSGI Bundle **darf nicht** mehr in das AEM Projekt einbezogen werden, es wird über das CIF Add-on bereitgestellt
* OSGI-Konfigurationen für GraphQL-Client und Graphql Data Service **dürfen nicht** mehr in das AEM Projekt einbezogen werden

>[!TIP]
>
>Sehen Sie sich das Projekt [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) auf GitHub an. Dieses Projekt bietet Maven-Profile für die AEM als Cloud Service und für Bereitstellungen vor Ort, die den unterschiedlichen Rahmenbedingungen Rechnung tragen.
