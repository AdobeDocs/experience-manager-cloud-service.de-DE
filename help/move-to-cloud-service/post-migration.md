---
title: Phase nach der Migration
description: Phase nach der Migration
source-git-commit: 96aa0ef43613e6ae72bf4c454be46329abb19a0c
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 100%

---


# Nach der Migration {#post-migration}

In der Phase nach der Migration sollten Sie die Bereinigung temporärer Dateien sicherstellen, Best Practices für die kontinuierliche Entwicklung überprüfen und Protokolle verwalten.

Die folgenden Tools stehen zur Fehlerbehebung in AEM as a Cloud Service-Umgebungen zur Verfügung:

* **Entwicklerkonsole**
* **CRXDE Lite**
* **Verwalten von Protokollen**


## Entwicklerkonsole {#developer-console}

AEM as a Cloud Service-Entwicklungsumgebungen zum Debuggen sind in der Entwicklerkonsole für Entwicklungs-, Staging- und Produktionsumgebungen verfügbar.

Weitere Informationen zu Entwicklungs-Tools finden Sie unter [Implementieren für AEM as a Cloud Service](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools).

## CRXDE Lite {#crxde-lite}

Als ein Benutzer können Sie in der Entwicklungsumgebung auf **CRXDE Lite** zugreifen, jedoch nicht in der Staging- oder Produktionsumgebung.

>[!IMPORTANT]
>Das Schreiben in unveränderliche Repositorys wie `/libs` und `/apps` zur Laufzeit führt zu Fehlern. Darüber hinaus haben Sie als Kunde keinen Zugriff auf Entwickler-Tools für Staging- und Produktionsumgebungen.

Informationen zum Entwickeln Ihrer AEM-Anwendung mit CRXDE Lite finden Sie unter [Entwickeln mit CRXDE Lite](/help/implementing/developing/tools/crxde.md).

## Verwalten von Protokollen {#managing-logs}

Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Unter [Zugreifen auf und Verwalten von Protokollen](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html) erfahren Sie, wie Sie über die Benutzeroberfläche oder über die API über Cloud Manager auf Protokolle zugreifen und diese verwalten.

### Zusätzliche Unterstützung {#additional-support}

Wenden Sie sich bei Fragen zum Zugriff auf Cloud Service an Ihren Adobe-Support-Mitarbeiter oder das Adobe AEM CQ-Support-Portal.
