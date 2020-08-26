---
title: AEM Dispatcher Converter-Tool
description: AEM Dispatcher Converter-Tool
translation-type: tm+mt
source-git-commit: 50d26dbec8281afec07ca56595b4b2a7b915eca9
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 53%

---


# AEM Dispatcher Converter {#introduction}

Adobe Experience Manager Dispatcher Converter konvertiert bestehende AEM Dispatcher-Konfigurationen in AEM als Cloud Service-Dispatcher-Konfigurationen.

## Einführung in Dispatcher {#introduction-dispatcher}

Dispatcher ist ein Tool von Adobe Experience Manager für das Zwischenspeichern und/oder den Lastenausgleich. Mit dem Dispatcher von AEM können Sie außerdem Ihren AEM-Server vor Angriffen schützen. Daher können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden.

>[!NOTE]
>Dispatcher wird am häufigsten zum Zwischenspeichern von Antworten aus einer **AEM-Veröffentlichungsinstanz** verwendet, um die Reaktionsfähigkeit und Sicherheit einer öffentlich zugänglichen veröffentlichten Website zu erhöhen.

Unter [Übersicht über Dispatcher](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/dispatcher.html) erfahren Sie, wie Dispatcher das Caching durchführt, Dokumente zurückgibt und den Lastenausgleich durchführt.

### Konfiguration und Testen von Apache und Dispatcher {#dispatcher-configurations-cloud}

Machen Sie sich damit vertraut, wie Sie die Apache- und Dispatcher-Konfigurationen von AEM as a Cloud Service strukturieren und vor der Bereitstellung in Cloud-Umgebungen lokal validieren und ausführen.

Weitere Informationen finden Sie unter [Dispatcher in der Cloud](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html)

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter bietet die Möglichkeit, bestehende lokale oder Adobe Managed Services Dispatcher-Konfigurationen zu refactorieren, um sie als Cloud Service-kompatible Dispatcher-Konfiguration zu AEM.

## Verwenden von AEM Dispatcher Converter {#using-dispatcher-converter}

* Über Adobe I/O CLI: Es wird empfohlen, den AEM Dispatcher Converter über zu verwenden `aio-cli-plugin-aem-cloud-service-migration` (AEM als Cloud Service-Code-Refactoring-Plugin für die Adobe-I/O-CLI).

   Siehe **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** erfahren Sie, wie Sie das Plugin installieren und verwenden.

* Als eigenständiges Dienstprogramm: Das AEM Dispatcher Converter Tool kann auch als eigenständiges Dienstprogramm ausgeführt werden.

   Refer to **[Git Resource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** to learn about the usage and troubleshooting for this tool.

>[!IMPORTANT]
>AEM Dispatcher Converter wird mit NodeJS entwickelt. Es wird empfohlen, NodeJS 10.0+ zu installieren.

