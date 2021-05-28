---
title: Phase nach der Live-Schaltung
description: Phase nach der Live-Schaltung
exl-id: f9b0b2fa-e29c-4faa-a5e7-e5edd04b25ca
source-git-commit: dfbd0f38017d02810da05ccadbc5f2fbd5826aa3
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 79%

---

# Nach der Live-Schaltung {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Beheben von Fehlern in AEM"
>abstract="Überprüfen Sie die Best Practices für die kontinuierliche Entwicklung und verwalten Sie Protokolle zusammen mit Tools wie Developer Console und CRXDE Lite, um Ihnen bei der Fehlerbehebung von Problemen mit AEM zu helfen."
>additional-url="https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html" text="Zugreifen auf und Verwalten von Protokollen"
>additional-url="https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools" text="Entwicklungs-Tools für AEM as a Cloud Service"


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

Informationen zum Entwickeln Ihrer AEM-Anwendung mit CRX/DE Lite finden Sie unter [Entwickeln mit CRX/DE Lite](/help/implementing/developing/tools/crxde.md).

## Verwalten von Protokollen {#managing-logs}

Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Unter [Zugreifen auf und Verwalten von Protokollen](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html) erfahren Sie, wie Sie über die Benutzeroberfläche oder über die API über Cloud Manager auf Protokolle zugreifen und diese verwalten.

### Zusätzliche Unterstützung {#additional-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Hilfe und Support"
>abstract="Wenden Sie sich an unser AEM Support-Team, um nähere Informationen zu erhalten oder um etwaige Bedenken auszuräumen."
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Experience Cloud-Support"

Wenn Sie Fragen zum Zugriff auf Cloud Service haben, wenden Sie sich an Ihren Kundenbetreuer oder [Support für Experience Cloud](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html), um weitere Informationen zu erhalten.
