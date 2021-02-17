---
title: Phase nach der Live-Schaltung
description: Phase nach der Live-Schaltung
translation-type: tm+mt
source-git-commit: 5a90db8791dd92cceb811b9ed2beda3ecb4a974d
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 100%

---


# Nach der Live-Schaltung {#post-go-live}

In der Phase nach der Live-Schaltung sollten Sie die Bereinigung temporärer Dateien sicherstellen, Best Practices für die kontinuierliche Entwicklung überprüfen und Protokolle verwalten.

Die folgenden Tools stehen zur Fehlerbehebung in AEM as a Cloud Service-Umgebungen zur Verfügung:

* **Developer Console**
* **CRX/DE Lite**
* **Verwalten von Protokollen**


## Entwicklerkonsole {#developer-console}

AEM as a Cloud Service-Entwicklungsumgebungen zum Debuggen sind in der Entwicklerkonsole für Entwicklungs-, Staging- und Produktionsumgebungen verfügbar.

Weitere Informationen zu Entwicklungs-Tools finden Sie unter [Implementieren für AEM as a Cloud Service](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools).

## CRX/DE Lite {#crxde-lite}

Als ein Benutzer können Sie in der Entwicklungsumgebung auf CRX/DE Lite zugreifen, jedoch nicht in der Staging- oder Produktionsumgebung.

>[!IMPORTANT]
>Das Schreiben in unveränderliche Repositorys wie `/libs` und `/apps` zur Laufzeit führt zu Fehlern. Darüber hinaus haben Sie als Kunde keinen Zugriff auf Entwickler-Tools für Staging- und Produktionsumgebungen.

Informationen zum Entwickeln Ihrer AEM-Anwendung mit CRX/DE Lite finden Sie unter [Entwickeln mit CRX/DE Lite](https://docs.adobe.com/help/de-DE/experience-manager-65/developing/devtools/developing-with-crxde-lite.html).

## Verwalten von Protokollen {#managing-logs}

Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Unter [Zugreifen auf und Verwalten von Protokollen](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html) erfahren Sie, wie Sie über die Benutzeroberfläche oder über die API über Cloud Manager auf Protokolle zugreifen und diese verwalten.

### Zusätzliche Unterstützung {#additional-support}

Wenden Sie sich bei Fragen zum Zugriff auf Cloud Service an Ihren Adobe-Support-Mitarbeiter oder das Adobe AEM CQ-Support-Portal.
