---
title: AEM Dispatcher Converter-Tool
description: Erfahren Sie, wie Sie bestehende Konfigurationen in AEM Dispatcher in Konfigurationen in AEM as a Cloud Service Dispatcher konvertieren.
exl-id: 2e95ff7b-cc94-477d-99ab-816a58998287
source-git-commit: f7ffe727ecc7f1331c1c72229a5d7f940070c011
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 94%

---

# AEM Dispatcher Converter {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="AEM Dispatcher Converter"
>abstract="Adobe Experience Manager Dispatcher Converter konvertiert vorhandene AEM-Dispatcher-Konfigurationen in AEM as a Cloud Service-Dispatcher-Konfigurationen."

Adobe Experience Manager Dispatcher Converter konvertiert vorhandene AEM-Dispatcher-Konfigurationen in AEM as a Cloud Service-Dispatcher-Konfigurationen.

## Einführung in Dispatcher {#introduction-dispatcher}

Der Dispatcher ist das Caching- und/oder Lastenausgleichs-Tool von Adobe Experience Manager. Die Verwendung des AEM-Dispatchers trägt außerdem dazu bei, Ihren AEM-Server vor Angriffen zu schützen. Somit können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden.

>[!NOTE]
>Dispatcher wird am häufigsten zum Zwischenspeichern von Antworten aus einer **AEM-Publishing-Instanz** verwendet, um die Reaktionsfähigkeit und Sicherheit einer öffentlich zugänglichen veröffentlichten Website zu erhöhen.

In der [Dispatcher-Übersicht](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) erfahren Sie, wie der Dispatcher das Caching durchführt, Dokumente zurückgibt und den Lastenausgleich vornimmt.

### Konfiguration und Testen von Apache und Dispatcher {#dispatcher-configurations-cloud}

Machen Sie sich damit vertraut, wie Sie die Apache- und Dispatcher-Konfigurationen von AEM as a Cloud Service strukturieren und vor der Bereitstellung in Cloud-Umgebungen lokal validieren und ausführen.

Weitere Informationen finden Sie unter [Dispatcher in der Cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=de)

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter bietet die Möglichkeit, bestehende lokale oder Adobe Managed Services Dispatcher-Konfigurationen in eine Adobe Experience Manager as a Cloud Service-kompatible Dispatcher-Konfiguration umzugestalten.

## Verwenden von AEM Dispatcher Converter {#using-dispatcher-converter}

* Über die Adobe Developer-CLI: Adobe empfiehlt die Verwendung des AEM Dispatcher Converter über `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service-Code-Refaktorierungs-Plug-in für die Adobe Developer-CLI).

  Unter **[Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** erfahren Sie, wie Sie das Plug-in installieren und verwenden können.

* Als eigenständiges Dienstprogramm: Das AEM Dispatcher Converter Tool kann auch als eigenständiges Dienstprogramm ausgeführt werden.

  Weitere Informationen finden Sie unter **[Git-Ressource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)**, damit Sie sich über die Verwendung und Fehlerbehebung für dieses Tool informieren können.

>[!IMPORTANT]
>AEM Dispatcher Converter wurde mit NodeJS entwickelt. Adobe empfiehlt, NodeJS 10.0 oder höher zu installieren.
