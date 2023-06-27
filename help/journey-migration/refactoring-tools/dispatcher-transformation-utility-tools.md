---
title: AEM Dispatcher Converter-Tool
description: AEM Dispatcher Converter-Tool
exl-id: 2e95ff7b-cc94-477d-99ab-816a58998287
source-git-commit: a9aa82c8258e6a5f43680069c65518093c0baf8d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 34%

---

# AEM Dispatcher Converter {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="AEM Dispatcher Converter"
>abstract="Adobe Experience Manager Dispatcher Converter konvertiert vorhandene Konfigurationen in AEM Dispatcher in Konfigurationen in AEM as a Cloud Service Dispatcher."

Adobe Experience Manager Dispatcher Converter konvertiert vorhandene Konfigurationen in AEM Dispatcher in Konfigurationen in AEM as a Cloud Service Dispatcher.

## Einführung in Dispatcher {#introduction-dispatcher}

Der Dispatcher ist das Caching- oder Lastenausgleichs-Tool von Adobe Experience Manager oder beides. Die Verwendung AEM Dispatcher hilft auch, Ihren AEM-Server vor Angriffen zu schützen. Daher können Sie die Sicherheit Ihrer AEM-Instanz erhöhen, indem Sie den Dispatcher mit einem Webserver der Unternehmensklasse verwenden.

>[!NOTE]
>Dispatcher wird am häufigsten zum Zwischenspeichern von Antworten aus einer **AEM-Veröffentlichungsinstanz** verwendet, um die Reaktionsfähigkeit und Sicherheit einer öffentlich zugänglichen veröffentlichten Website zu erhöhen.

Siehe [Dispatcher-Übersicht](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) , um zu erfahren, wie der Dispatcher das Zwischenspeichern durchführt, Dokumente zurückgibt und den Lastenausgleich durchführt.

### Konfiguration und Testen von Apache und Dispatcher {#dispatcher-configurations-cloud}

Erfahren Sie, wie Sie die AEM as a Cloud Service Apache- und Dispatcher-Konfigurationen strukturieren und vor der Bereitstellung in Cloud-Umgebungen validieren und lokal ausführen können.

Siehe [Dispatcher in der Cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=de) für weitere Informationen.

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter bietet die Möglichkeit, bestehende lokale oder Adobe Managed Services Dispatcher-Konfigurationen in eine Adobe Experience Manager as a Cloud Service-kompatible Dispatcher-Konfiguration umzugestalten.

## Verwenden von AEM Dispatcher Converter {#using-dispatcher-converter}

* Über Adobe Developer CLI : Adobe empfiehlt die Verwendung des AEM Dispatcher Converter über `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service Code-Refaktorierungs-Plug-in für die Adobe Developer-CLI).

  Siehe **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** damit Sie lernen können, wie Sie das Plug-in installieren und verwenden.

* Als eigenständiges Dienstprogramm : Das AEM Dispatcher Converter-Tool kann auch als eigenständiges Dienstprogramm ausgeführt werden.

  Siehe **[Git-Ressource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** damit Sie mehr über die Verwendung und Fehlerbehebung dieses Tools erfahren können.

>[!IMPORTANT]
>AEM Dispatcher Converter wird mit NodeJS entwickelt. Adobe empfiehlt, NodeJS 10.0 oder höher zu installieren.
