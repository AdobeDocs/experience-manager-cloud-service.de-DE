---
title: Asset-Workflow-Migrations-Tool
description: 'Asset-Workflow-Migrations-Tool '
translation-type: tm+mt
source-git-commit: 3a438de3c460d4dc5a8b8617f0ec0eefc56f1665
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 46%

---


# Asset-Workflow-Migrations-Tool {#asset-workflow-migration}

Mit dem Asset-Workflow-Migrations-Tool können Sie Asset-Verarbeitungs-Workflows automatisch von On-Premise- oder AMS-Bereitstellungen von AEM zu Verarbeitungsprofilen und OSGi-Konfigurationen für die Verwendung in AEM Assets as a Cloud Service migrieren.

## Einführung {#introduction}

In diesem Abschnitt werden Ressourcen und Implementierungsdetails zum Asset-Workflow-Migrations-Tool beschrieben.

Mit diesem Dienstprogramm können die AEM-Entwickler bestehende AEM-Workflows für die Asset-Verarbeitung zu AEM as a Cloud Service migrieren.

## Unterstützte Workflows {#migration-support-for-workflows}

Die Workflows bieten unterschiedliche Migrationsunterstützung. Siehe diese [Liste spezifischer Workflows](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties). Die Workflows sind in den folgenden Kategorien je nach bereitgestellter Unterstützung eingeteilt. Adobe unterstützt die Migration von Workflows, die in `SUPPORTED`, `REQUIRED`oder `OPTIONAL` Kategorien aufgeführt sind. Die in den anderen Kategorien erwähnten Workflow-Schritte werden nicht unterstützt.

* `SUPPORTED`: Unterstützte Funktionen [!DNL Experience Manager Assets] als Cloud Service.
* `OPTIONAL`: Optionale Funktion [!DNL Experience Manager Assets] als Cloud Service.
* `REQUIRED`: Ein erforderlicher Schritt, der dem Workflow hinzugefügt wird.
* `UNNECESSARY`: Funktionalität ist nicht erforderlich [!DNL Experience Manager Assets] als Cloud Service.
* `NUI_OOTB`: Funktionen des [Asset Compute-Dienstes](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB`: Von Standard- [!DNL Dynamic Media] Connectors bereitgestellte Funktionalität.
* `NUI_MIGRATED`: Zu einem [verarbeitenden Profil für den Asset Compute-Dienst](/help/assets/asset-microservices-configure-and-use.md)migriert.
* `UNSUPPORTED`: Derzeit nicht unterstützt in [!DNL Experience Manager Assets] als Cloud Service.

## Installieren des Asset-Workflow-Migrations-Tools {#installing-tool}

Weitere Informationen zum Installieren und Erstellen von Code aus der Quelle finden Sie unter **[Git-Ressource: AEM Assets as a Cloud Service – Workflow-Migration](https://github.com/adobe/aem-cloud-migration)**.
