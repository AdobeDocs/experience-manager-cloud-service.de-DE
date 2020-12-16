---
title: 'Integrieren mit Adobe Analytics '
description: 'Integration mit Adobe Analytics '
translation-type: tm+mt
source-git-commit: ec747361935b94a729cdd5b6712aee6d3ce1b8a2
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 100%

---


# Integrieren mit Adobe Analytics{#integrating-with-adobe-analytics}

Die Integration von Adobe Analytics und AEM as a Cloud Service ermöglicht es Ihnen, Web-Seitenaktivität zu erfassen:

* Eine Adobe Analytics-Konfiguration ermöglicht AEM die Authentifizierung mit Adobe Analytics.
* Ein Framework identifiziert die Daten, die an die Adobe Analytics-Report Suite übermittelt werden.

Die Daten umfassen Seiten- und Benutzerdaten, z. B.:

* Daten, die von AEM-Komponenten erfasst werden
* Link-Klicks
* Videonutzungsdaten
* die Anzahl von Seitenbesuchen aus Adobe Analytics

Die unten aufgeführten Seiten können Ihnen bei der Konfiguration der Integration helfen. Beachten Sie, dass Adobe Experience Platform Launch das Tool zur Instrumentierung einer AEM-Site mit Analytics-Funktionen (JS-Bibliotheken) ist. Daher erfolgt die Integration von AEM as a Cloud Service in Experience Platform Launch und Adobe Analytics Hand in Hand.

* [Herstellen einer Verbindung zu Adobe Analytics und Erstellen von Frameworks](https://docs.adobe.com/content/help/de/experience-manager-65/administering/integration/adobeanalytics-connect.html) - Beachten Sie, dass „Analytics-Frameworks“ in AEM veraltet sind und sie in AEM as a Cloud Service nicht erstellt werden können, da hierfür die klassische Benutzeroberfläche erforderlich ist. Stattdessen sollte Adobe Experience Platform Launch sowohl für die Variablenzuordnung als auch für die Implementierung von JS-Bibliotheken auf Seiten verwendet werden.
* [Integrieren von Adobe Experience Platform Launch](https://docs.adobe.com/content/help/de/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [Integrieren von AEM mit Adobe Experience Platform Launch über Adobe I/O](https://helpx.adobe.com/de/experience-manager/using/aem_launch_adobeio_integration.html)
* [Grundlegendes zur AEM-Integration mit Adobe Experience Platform Launch, Analytics und Target](https://helpx.adobe.com/de/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Konfigurieren des Linktrackings für Adobe Analytics](https://docs.adobe.com/content/help/de/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [Zuordnen von Komponentendaten mit Adobe Analytics-Eigenschaften](https://docs.adobe.com/content/help/de/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Konfigurieren von Videotracking für Adobe Analytics](https://docs.adobe.com/content/help/de/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Adobe Classifications](https://docs.adobe.com/content/help/de/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>Kunden mit Adobe Experience Manager as a Cloud Service, die kein Analytics-Konto haben, können Zugriff auf Analytics Foundation Pack für Experience Cloud anfordern. Dieses Foundation Pack bietet eine eingeschränkte Verwendung von Analytics.

>[!NOTE]
>
>Die IMS-Konfiguration (technische Konten) für Adobe Experience Platform Launch ist in AEM as a Cloud Service vorkonfiguriert. Benutzer müssen diese Konfiguration nicht erstellen.

## Weiterführende Informationen {#further-information}

Siehe:

* [Erweitern der Adobe Analytics-Integration](https://docs.adobe.com/content/help/de/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html), um Informationen zur Entwicklung von Komponenten zu erhalten, die Benutzerdaten erfassen, und zur Anpassung des Adobe Analytics-Frameworks. Beachten Sie, dass „Analytics-Frameworks“ in AEM veraltet sind und sie in AEM as a Cloud Service nicht erstellt werden können, da hierfür die klassische Benutzeroberfläche erforderlich ist. Stattdessen sollte Adobe Experience Platform Launch sowohl für die Variablenzuordnung als auch für die Implementierung von JS-Bibliotheken auf Seiten verwendet werden.
* den Knowledgebase-Artikel [Adobe Analytics-Integration – Problembehebung](https://helpx.adobe.com/de/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), um Information zur Behebung von Problemen mit der Adobe Analytics-Integration zu erhalten.

>[!NOTE]
>
>Wenn Sie Adobe Analytics mit einer benutzerdefinierten Proxykonfiguration verwenden, müssen Sie zwei OSGi-Pakete[ (z. B. mit der Web Console) ](https://docs.adobe.com/content/help/de/experience-manager-65/deploying/configuring/configuring-osgi.html)konfigurieren, die für die **Apache HTTP Client**-Proxykonfigurationen erforderlich sind. Beide sind erforderlich, da einige Funktionen von AEM die 3.x-APIs verwenden, während andere die 4.x-APIs verwenden. Konfigurieren:
>
>* **Day Commons HTTP Client 3.1** zum Konfigurieren der 3.x-API;
   >  Beispiel: [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Apache HTTP Components Proxy Configuration** zum Konfigurieren der 4.x-API;
   >  Beispiel: [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>


