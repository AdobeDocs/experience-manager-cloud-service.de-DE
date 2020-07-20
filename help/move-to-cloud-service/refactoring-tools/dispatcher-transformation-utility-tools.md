---
title: AEM Dispatcher Converter-Tool
description: AEM Dispatcher Converter-Tool
translation-type: ht
source-git-commit: 66cf4fc7b5a336968dd3f8757cc56a11d6e4843e
workflow-type: ht
source-wordcount: '348'
ht-degree: 100%

---


# AEM Dispatcher Converter {#introduction}

Adobe Experience Manager Dispatcher Converter konvertiert vorhandene AMS Dispatcher-Konfigurationen in AEM as a Cloud Service-Konfigurationen.

## Einführung in Dispatcher {#introduction-dispatcher}

Dispatcher ist ein Tool von Adobe Experience Manager für das Zwischenspeichern und/oder den Lastenausgleich. Mit dem Dispatcher von AEM können Sie außerdem Ihren AEM-Server vor Angriffen schützen. Daher können Sie die Sicherheit Ihrer AEM-Instanz verbessern, indem Sie den Dispatcher in Verbindung mit einem Webserver der Unternehmensklasse verwenden.

>[!NOTE]
>Dispatcher wird am häufigsten zum Zwischenspeichern von Antworten aus einer **AEM-Veröffentlichungsinstanz** verwendet, um die Reaktionsfähigkeit und Sicherheit einer öffentlich zugänglichen veröffentlichten Website zu erhöhen.

Unter [Übersicht über Dispatcher](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/dispatcher.html) erfahren Sie, wie Dispatcher das Caching durchführt, Dokumente zurückgibt und den Lastenausgleich durchführt.

### Konfiguration und Testen von Apache und Dispatcher {#dispatcher-configurations-cloud}

Machen Sie sich damit vertraut, wie Sie die Apache- und Dispatcher-Konfigurationen von AEM as a Cloud Service strukturieren und vor der Bereitstellung in Cloud-Umgebungen lokal validieren und ausführen.

Weitere Informationen finden Sie unter [Dispatcher in der Cloud](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html)

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter ist ein Dienstprogramm zum Konvertieren vorhandener AMS Dispatcher-Konfigurationen in AEM as a Cloud Service-Dispatcher-Konfigurationen. Dieses Dienstprogramm ist für AMS-Instanzen vorgesehen.

Der implementierte Konverter ist **AEMDispatcherConfigConverter**, der den Transformationsrichtlinien folgt.

Informationen zum Konvertieren einer AMS-Konfiguration in eine Adobe Experience Manager as a Cloud Service-Dispatcher-Konfiguration finden Sie unter [Konvertieren einer AMS-Konfiguration in eine Adobe Experience Manager as a Cloud Service-Dispatcher-Konfiguration](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html#how-to-convert-an-ams-to-an-aem-as-a-cloud-service-dispatcher-configuration).

## Verwenden von AEM Dispatcher Converter {#using-dispatcher-converter}

Im folgenden Abschnitt werden die Ressourcen und Informationen beschrieben, die für die Verwendung des AEM Dispatcher Converter-Tools erforderlich sind.

Weitere Informationen zu Verwendung, Einschränkungen und Fehlerbehebung für dieses Tool finden Sie unter **[Git-Ressource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-dispatcher-converter)**.

>[!IMPORTANT]
>AEM Dispatcher Converter wurde mit Python 3.7.3 entwickelt. Es wird empfohlen, Python 3.5 oder neuer zu installieren.

## Beschränkungen {#limitations}

AEM Dispatcher Converter geht davon aus, dass die Struktur des bereitgestellten Dispatcher-Konfigurationsordners der in der Cloud Manager-Dispatcher-Konfiguration beschriebenen ähnelt.


