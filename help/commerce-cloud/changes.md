---
title: Wesentliche Änderungen an AEM Commerce as a Cloud Service
description: Wesentliche Änderungen an AEM Commerce as a Cloud Service im Vergleich zu Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 2934d0d8d3977bb7884bae9654ac26e9fa57b34f
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 100%

---


# Wesentliche Änderungen an AEM Commerce as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer AEM-Projekte. In diesem Dokument wird auf die wichtigsten Unterschiede zwischen Commerce Integration Framework (CIF) für On-Premise, Adobe Managed Services und Experience Manager as a Cloud Service für die Commerce-Funktionen eingegangen. Weitere Änderungen finden Sie im Abschnitt zu den allgemeinen [Änderungen an Adobe Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Die Hauptunterschiede gegenüber Adobe Experience Manager 6.5 bestehen in den folgenden Bereichen:
* [Unterstützung für CIF Classic](#cif-classic)
* [Implementierung der CIF-Authoring-Tools](#cif-tools)
* [Umstellung von On-Premise und Adobe Managed Service](#moving-cif-cs)

## Unterstützung für CIF Classic/Quickstart für Experience Manager as a Cloud Service {#cif-classic}

Classic Commerce Integration Framework, das einen Produkt-Importer zum Importieren und Speichern von Produktkatalogen in Experience Manager enthielt, ist in Experience Manager as a Cloud Service nicht mehr verfügbar. Die Verwendung von Classic CIF wird in Experience Manager as a Cloud Service nicht unterstützt. Projekte, die Classic CIF verwenden, müssen die Classic CIF-Implementierung durch die unterstützte Version ersetzen, wie in [CIF in Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/commerce/architecture/magento.html#overview) beschrieben.

## CIF-Implementierung {#deployment}

Nachfolgend sind die verschiedenen Implementierungsmodelle für Commerce Integration Framework für die verschiedenen AEM-Angebote aufgeführt:

|  | AEM On-Premise | AEM Managed Services | AEM Cloud Service |
|-------------     |-----------|-----------|-----------|
| Implementierung von CIF-Authoring-Tools für das Magento-Backend | [Informationen zum CIF Connector](https://github.com/adobe/commerce-cif-connector/blob/master/README.md), der in AEM 6.5 unterstützt wird | [Informationen zum CIF Connector](https://github.com/adobe/commerce-cif-connector/blob/master/README.md), der in AEM 6.5 unterstützt wird | AEM as a Cloud Service muss mit CIF-Add-on bereitgestellt werden. Weitere Informationen erhalten Sie von Ihrem Vertriebsmitarbeiter. |
| Implementierung des [CIF Venia-Projekts](https://github.com/adobe/aem-cif-guides-venia) | AEM-Paketinstallation | Implementierung über [Cloud Manager](https://docs.adobe.com/content/help/de/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) | Projekt in das [Cloud Manager-Git-Repository](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) verschoben und Implementierung über [Cloud Manager](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/deploying/overview.html). |

>[!NOTE]
>
>Weitere Dokumentationen zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).

>[!NOTE]
>
>Die CIF Classic-/Quickstart-Version von Commerce Integration Framework kann bei AEM On-Premise-Angeboten für sehr begrenzte Anwendungsfälle verwendet werden. Dies ist jedoch nicht die empfohlene Lösung.

## Umstellung von On-Premise und Managed Services auf AEM Commerce as a Cloud Service {#moving-cif-cs}

Kunden, die von einer AEM On-Premise- oder Managed Services-Installation zu AEM as a Cloud Service wechseln, müssen einige geringfügige Anpassungen am AEM-Projekt vornehmen.

Die erste Anpassung, wie oben beschrieben, ist für den CIF Connector erforderlich. Der CIF Connector wird durch das CIF-Add-on ersetzt, das von Adobe bereitgestellt wird. Installieren Sie daher den CIF Connector nicht für AEM as a Cloud Service. Außerdem wird die Verwendung mit dem lokalen AEM Cloud SDK nicht unterstützt. Adobe bietet das CIF-Add-on auch für die [lokale Implementierung](develop.md) an.

Zweitens sollten Sie die [AEM-Projektstruktur](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) und die Funktionsweise von AEM as a Cloud Service verstehen. Passen Sie Ihr Projekt-Setup an das Layout von AEM as a Cloud Service an.
Die Hauptunterschiede sind:

* Das GraphQL-Client-OSGi-Bundle **darf nicht** mehr in das AEM-Projekt aufgenommen werden, sondern wird über das CIF-Add-on bereitgestellt.
* OSGi-Konfigurationen für den GraphQL-Client und GraphQL Data Service **dürfen nicht** mehr in das AEM-Projekt aufgenommen werden.

>[!TIP]
>
>Sehen Sie sich das Projekt [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) auf GitHub an. Dieses Projekt bietet Maven-Profile für AEM as a Cloud Service und für On-Premise-Implementierungen, die den unterschiedlichen Rahmenbedingungen Rechnung tragen.
