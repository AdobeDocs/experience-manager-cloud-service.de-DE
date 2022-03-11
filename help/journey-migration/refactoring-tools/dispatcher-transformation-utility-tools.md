---
title: AEM Dispatcher Converter-Tool
description: AEM Dispatcher Converter-Tool
exl-id: 2e95ff7b-cc94-477d-99ab-816a58998287
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 100%

---

# AEM Dispatcher Converter {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="AEM Dispatcher Converter"
>abstract="Adobe Experience Manager Dispatcher Converter konvertiert vorhandene AEM Dispatcher-Konfigurationen in AEM as a Cloud Service-Konfigurationen."

Adobe Experience Manager Dispatcher Converter konvertiert vorhandene AEM Dispatcher-Konfigurationen in AEM as a Cloud Service-Konfigurationen.

## Einführung in Dispatcher {#introduction-dispatcher}

Dispatcher ist ein Tool von Adobe Experience Manager für das Zwischenspeichern und/oder den Lastenausgleich. Mit dem Dispatcher von AEM können Sie außerdem Ihren AEM-Server vor Angriffen schützen. Daher können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden.

>[!NOTE]
>Dispatcher wird am häufigsten zum Zwischenspeichern von Antworten aus einer **AEM-Veröffentlichungsinstanz** verwendet, um die Reaktionsfähigkeit und Sicherheit einer öffentlich zugänglichen veröffentlichten Website zu erhöhen.

Unter [Übersicht über Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) erfahren Sie, wie Dispatcher das Caching durchführt, Dokumente zurückgibt und den Lastenausgleich durchführt.

### Konfiguration und Testen von Apache und Dispatcher {#dispatcher-configurations-cloud}

Machen Sie sich damit vertraut, wie Sie die Apache- und Dispatcher-Konfigurationen von AEM as a Cloud Service strukturieren und vor der Implementierung in Cloud-Umgebungen lokal validieren und ausführen.

Weitere Informationen finden Sie unter [Dispatcher in der Cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=de)

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter bietet die Möglichkeit, bestehende lokale oder Adobe Managed Services Dispatcher-Konfigurationen in eine AEM as a Cloud Service-kompatible Dispatcher-Konfiguration umzugestalten.

## Verwenden von AEM Dispatcher Converter {#using-dispatcher-converter}

* Über die Adobe I/O-CLI: Es wird empfohlen, den AEM Dispatcher Converter via `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service-Code-Refactoring-Plug-in für die Adobe I/O-CLI) zu verwenden.

   Siehe **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)**, um zu erfahren, wie Sie das Plug-in installieren und verwenden.

* Als eigenständiges Dienstprogramm: Das AEM Dispatcher Converter Tool kann auch als eigenständiges Dienstprogramm ausgeführt werden.

   Weitere Informationen zu Verwendung und Fehlerbehebung für dieses Tool finden Sie unter **[Git-Ressource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)**.

>[!IMPORTANT]
>AEM Dispatcher Converter wird mit NodeJS entwickelt. Es wird empfohlen, NodeJS 10.0 oder höher zu installieren.
