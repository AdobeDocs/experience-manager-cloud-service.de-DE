---
title: Asset-Workflow-Migrations-Tool
description: Asset-Workflow-Migrations-Tool
exl-id: 18490295-ead6-4691-8983-a6d4054e4264
source-git-commit: d443ab32e5d2dddded58693483a2bda825ea3048
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 76%

---

# Asset-Workflow-Migrations-Tool {#asset-workflow-migration}

Mit dem Asset-Workflow-Migrations-Tool können Sie Asset-Verarbeitungs-Workflows automatisch von On-Premise- oder AMS-Implementierungen von AEM zu Verarbeitungsprofilen und OSGi-Konfigurationen für die Verwendung in AEM Assets as a Cloud Service migrieren.

## Einführung {#introduction}

In diesem Abschnitt werden Ressourcen und Implementierungsdetails zum Asset-Workflow-Migrations-Tool beschrieben.

Mit diesem Dienstprogramm können die AEM-Entwickler bestehende AEM-Workflows für die Asset-Verarbeitung zu AEM as a Cloud Service migrieren.

## Unterstützte Workflows {#migration-support-for-workflows}

Die Workflows bieten in unterschiedlichem Maß Unterstützung für Migrationen. Weitere Informationen finden Sie in dieser [Liste spezifischer Workflows](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties). Die Workflows sind je nach bereitgestellter Unterstützung in die folgenden Kategorien unterteilt. Adobe unterstützt die Migration von Workflows, die in den Kategorien `SUPPORTED`, `REQUIRED`oder `OPTIONAL` aufgeführt sind. Die in den anderen Kategorien erwähnten Workflow-Schritte werden nicht unterstützt.

* `SUPPORTED`: Unterstützte Funktionalität in [!DNL Experience Manager Assets] as a Cloud Service.
* `OPTIONAL`: Optionale Funktionalität in [!DNL Experience Manager Assets] as a Cloud Service.
* `REQUIRED`: Ein erforderlicher Schritt, der zum Workflow hinzugefügt wird.
* `UNNECESSARY`: Funktionalität ist nicht erforderlich in [!DNL Experience Manager Assets] as a Cloud Service.
* `NUI_OOTB`: Funktionalität, die vom [Asset Compute Service](/help/assets/asset-microservices-configure-and-use.md) bereitgestellt wird.
* `DMS7_OOTB`: Funktionalität, die von standardmäßigen [!DNL Dynamic Media]-Connectoren bereitgestellt wird.
* `NUI_MIGRATED`: Zu einem [Verarbeitungsprofil für den Asset Compute Service](/help/assets/asset-microservices-configure-and-use.md) migriert.
* `UNSUPPORTED`: Derzeit nicht unterstützt in [!DNL Experience Manager Assets] as a Cloud Service.

## Asset Workflow-Migrations-Tool {#use-workflow-migrator} verwenden

* **[!DNL Adobe I/O]CLI**: Adobe empfiehlt die Verwendung des Asset-Workflow-Migrationstools über  `aio-cli-plugin-aem-cloud-service-migration` ([!DNL Experience Manager] als  [!DNL Cloud Service] Code-Refaktorierungs-Plug-in für die  [!DNL Adobe I/O] CLI). Informationen zur Installation und Verwendung des Plug-ins finden Sie unter [Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction).

* **Eigenständiges Dienstprogramm**: Das Asset Workflow-Migrations-Tool kann auch als eigenständiges Dienstprogramm ausgeführt werden. Weitere Informationen zum Installieren und Erstellen von Code aus der Quelle finden Sie unter [Git-Ressource: [!DNL Experience Manager Assets] as a [!DNL Cloud Service] - Workflow-Migration](https://github.com/adobe/aem-cloud-migration).
