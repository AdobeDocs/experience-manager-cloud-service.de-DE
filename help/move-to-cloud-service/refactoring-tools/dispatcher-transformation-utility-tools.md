---
title: AEM Dispatcher Converter Tool
description: AEM Dispatcher Converter Tool
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 17%

---


# AEM Dispatcher Converter {#introduction}

Adobe Experience Manager Dispatcher Converter konvertiert vorhandene AMS Dispatcher-Konfigurationen als Cloud Service Dispatcher-Konfigurationen in AEM.

## Einführung in Dispatcher {#introduction-dispatcher}

Dispatcher ist ein Tool von Adobe Experience Manager für das Zwischenspeichern und/oder den Lastenausgleich. Mit dem Dispatcher von AEM können Sie außerdem Ihren AEM-Server vor Angriffen schützen. Daher können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden.

>[!NOTE]
>The most common use of Dispatcher is to cache responses from an **AEM publish instance**, to increase the responsiveness and security of your externally facing published website.

Lesen Sie die [Dispatcher-Übersicht](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/dispatcher.html) , um zu erfahren, wie Dispatcher die Zwischenspeicherung durchführt, Dokumente zurückgibt und Lastenausgleich ausführt.

### Apache and Dispatcher Configuration and Testing {#dispatcher-configurations-cloud}

Sie müssen lernen, wie AEM als Cloud-Dienst-Apache- und Dispatcher-Konfigurationen strukturiert wird und wie Sie es vor der Bereitstellung in Cloud-Umgebung lokal validieren und ausführen.

Weitere Informationen finden Sie unter [Dispatcher in der Cloud](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/dispatcher/overview.html) .

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter ist ein Dienstprogramm zum Konvertieren vorhandener AMS Dispatcher-Konfigurationen in AEM als Cloud-Service-Dispatcher-Konfigurationen. Dieses Dienstprogramm ist für AMS-Instanzen vorgesehen.

Der implementierte Konverter ist **AEMDispatcherConfigConverter** , der den Transformationsrichtlinien folgt.

Informationen zum Konvertieren eines AMS in einen Adobe Experience Manager als Cloud-Service-Dispatcher-Konfiguration [finden Sie unter Konvertieren eines AMS in eine Adobe Experience Manager-Konfiguration als Cloud-Service-Dispatcher-Konfiguration](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/dispatcher/overview.html#how-to-convert-an-ams-to-an-aem-as-a-cloud-service-dispatcher-configuration) .

## Verwenden von AEM Dispatcher Converter {#using-dispatcher-converter}

Im folgenden Abschnitt werden die Ressourcen und Informationen beschrieben, die für die Verwendung des AEM Dispatcher Converter-Tools erforderlich sind.

Siehe **[Git-Ressource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-dispatcher-converter)**, um mehr über Nutzung, Einschränkungen und Fehlerbehebung für dieses Tool zu erfahren.

>[!IMPORTANT]
>AEM Dispatcher Converter wird mit Python 3.7.3 entwickelt. Es wird empfohlen, Python 3.5 oder höher zu installieren.

## Beschränkungen {#limitations}

AEM Dispatcher Converter funktioniert unter der Annahme, dass die Struktur des angegebenen Dispatcher-Konfigurationsordners der in der Cloud Manager-Dispatcher-Konfiguration beschriebenen ähnelt.


