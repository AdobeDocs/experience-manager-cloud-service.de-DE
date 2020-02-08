---
title: Integrieren mit Adobe Analytics
description: 'Integrieren mit Adobe Analytics '
translation-type: tm+mt
source-git-commit: 6754693da488b0bc44a71aa9f0402fc1308b703a

---


# Integrieren mit Adobe Analytics{#integrating-with-adobe-analytics}

Durch die Integration von Adobe Analytics und AEM als Cloud-Dienst können Sie die Aktivität Ihrer Webseite verfolgen:

* Eine Adobe Analytics-Konfiguration ermöglicht AEM die Authentifizierung mit Adobe Analytics.
* Ein Framework identifiziert die Daten, die an Ihre Adobe Analytics-Report Suite gesendet werden.

Zu den Daten gehören z. B. Seiten- und Benutzerdaten:

* Daten, die von AEM-Komponenten erfasst werden
* Link-Klicks
* Videonutzungsdaten
* die Anzahl von Seitenbesuchen von Adobe Analytics

Die unten aufgeführten Seiten können Ihnen bei der Konfiguration der Integration helfen. Beachten Sie, dass Launch by Adobe das defacto-Tool zur Instrumentierung einer AEM-Site mit Analytics-Funktionen (JS-Bibliotheken) ist. Die Integration von AEM als Cloud-Dienst in Launch und Adobe Analytics erfolgt daher Hand in Hand.

* [Herstellen einer Verbindung zu Adobe Analytics und Erstellen von Frameworks](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-connect.html) - Beachten Sie, dass &quot;Analytics-Frameworks&quot;in AEM veraltet sind und ihre Erstellung nicht in AEM als Cloud-Dienst funktioniert, da hierfür die klassische Benutzeroberfläche erforderlich ist. Der Start von Adobe sollte stattdessen sowohl für die Variablenzuordnung als auch für die Bereitstellung von JS-Bibliotheken auf Seiten verwendet werden.
* [Starten von Adobe integrieren](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [Integration von AEM mit Adobe Launch über Adobe I/O](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
* [Die AEM-Integration mit dem Start von Adobe, Analytics und Target](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Konfigurieren der Link-Überwachung für Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [Zuordnen von Komponentendaten mit Adobe Analytics-Eigenschaften](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Konfigurieren von Videotracking für Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Adobe Classifications](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>Kunden mit Adobe Experience Manager als Cloud-Service, die kein Analytics-Konto haben, können Zugriff auf das Analytics Foundation Pack für Experience Cloud anfordern.  Dieses Foundation Pack bietet eine mengenbegrenzte Verwendung von Analytics.

>[!NOTE]
>
>Die IMS-Konfiguration (technische Konten) zum Starten durch Adobe ist in AEM als Cloud-Dienst vorkonfiguriert. Benutzer müssen diese Konfiguration nicht erstellen.

## Weiterführende Informationen {#further-information}

Siehe:

* [Erweitern der Adobe Analytics-Integration](https://docs.adobe.com/content/help/en/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html) für Informationen zur Entwicklung von Komponenten, die Benutzerdaten erfassen und das Adobe Analytics-Framework anpassen. Beachten Sie, dass &quot;Analytics-Frameworks&quot;in AEM veraltet sind und ihre Erstellung in AEM nicht als Cloud-Dienst funktioniert, da hierfür die klassische Benutzeroberfläche erforderlich ist. Der Start von Adobe sollte stattdessen sowohl für die Variablenzuordnung als auch für die Bereitstellung von JS-Bibliotheken auf Seiten verwendet werden.
* The knowledge base article, [Adobe Analytics integration - troubleshooting issues](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), for information about troubleshooting your Adobe Analytics integration.

>[!NOTE]
>
>Sie müssen [zwei OSGi-Bundles konfigurieren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/configuring-osgi.html) (z. B. mit der Web-Konsole), die für **Apache HTTP Client**-Proxykonfigurationen erforderlich sind, wenn Sie Adobe Analytics mit einer benutzerdefinierten Proxykonfiguration verwenden. Beide sind erforderlich, da einige Funktionen von AEM die 3.x-APIs verwenden, während andere die 4.x-APIs verwenden. Konfigurieren Sie Folgendes:
>
>* **Day Commons HTTP Client 3.1** zum Konfigurieren der 3.x-API;
   >  Beispiel: [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Apache HTTP-Komponenten-Proxy-Konfiguration** zum Konfigurieren der 4.x-API;
   >  Beispiel: [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>


