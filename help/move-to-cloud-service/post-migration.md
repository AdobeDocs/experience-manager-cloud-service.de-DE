---
title: Phase nach der Migration
description: Phase nach der Migration
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 9%

---


# Nach der Migration {#post-migration}

In der Phase nach der Migration sollten Sie sicherstellen, dass temporäre Dateien bereinigt werden, bewährte Verfahren für die kontinuierliche Entwicklung überprüfen und Protokolle verwalten.

Die folgenden Tools stehen zur Fehlerbehebung bei AEM als Cloud-Service-Umgebung zur Verfügung:

* **Entwicklerkonsole**
* **CRXDE Lite**
* **Verwalten von Protokollen**


## Entwicklerkonsole {#developer-console}

Das Debugging von AEM als Cloud-Dienstentwicklungs-Umgebung ist in der Developer Console für Umgebung in Entwicklung, Phase und Produktion verfügbar.

Weitere Informationen zu Entwicklungstools finden Sie unter [Implementierung von AEM als Cloud-Dienst](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools) .

## CRXDE Lite {#crxde-lite}

Als Benutzer können Sie auf **CRXDE Lite** auf der Entwicklungs-Umgebung zugreifen, jedoch nicht auf die Stufe oder Produktion.

>[WICHTIG]
>Das Schreiben in unveränderbare Repositorys wie `/libs` und `/apps` zur Laufzeit führt zu Fehlern. Darüber hinaus haben Sie als Kunde keinen Zugriff auf die Entwicklerwerkzeuge für Staging- und Produktions-Umgebung.

Informationen zum Entwickeln Ihrer AEM-Anwendung mit CRXDE Lite finden Sie unter [Entwickeln mit CRXDE Lite](https://docs.adobe.com/help/en/experience-manager-65/developing/devtools/developing-with-crxde-lite.html) .

## Verwalten von Protokollen {#managing-logs}

Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Informationen zum Zugriff auf und Verwalten von Protokollen [über die Benutzeroberfläche oder über die API über Cloud Manager finden Sie unter](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html) Zugriff auf Protokolle und Verwalten von Protokollen.

### Zusätzliche Unterstützung {#additional-support}

Wenden Sie sich bei Fragen zum Zugriff auf den Cloud-Dienst an Ihren Adobe-Kundenbetreuer oder das Adobe AEM CQ-Supportportal.
