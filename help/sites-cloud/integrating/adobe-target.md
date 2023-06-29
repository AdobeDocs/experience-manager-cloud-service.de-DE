---
title: Integrieren mit Adobe Target
description: Integrieren mit Adobe Target
exl-id: 2b4cf35e-2b75-4303-8d09-f6644ad99274
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 62%

---

# Integrieren mit Adobe Target{#integrating-with-adobe-target}

Als Teil der Adobe Experience Cloud [Adobe Target](https://business.adobe.com/products/target/adobe-target.html) ermöglicht Ihnen die Steigerung der Inhaltsrelevanz durch Targeting und Messungen über alle Kanäle hinweg. Adobe Target wird von Marketing-Experten genutzt, um Online-Tests zu entwerfen und auszuführen, in kurzer Zeit Zielgruppensegmente zu erstellen (anhand des Verhaltens) und das Targeting für Inhalte und Online-Erlebnisse zu automatisieren. AEM as a Cloud Service hat den Targeting-Workflow übernommen, der in Adobe Target Standard verwendet wird. Wenn Sie Target verwenden, sind Sie mit der Targeting-Bearbeitungsumgebung in AEM as a Cloud Service vertraut.

Integrieren Sie Ihre AEM-Sites in Adobe Target, damit Sie Inhalte auf Ihren Seiten personalisieren können:

* Implementieren Sie Content-Targeting.
* Verwenden Sie Target-Zielgruppen, um personalisierte Erlebnisse zu erstellen.
* Senden Sie Kontextdaten an Target, wenn Besucher mit Ihren Seiten interagieren.
* Verfolgen Sie Konversionsraten.

>[!NOTE]
>
>Kunden, die kein Target-Konto haben, können zum Experience Cloud Zugriff auf das Target Foundation Pack anfordern. Das Foundation Pack bietet eine eingeschränkte Verwendung von Target.


Führen Sie zur Integration mit Target die folgenden Aufgaben durch:

* [Führen Sie vorbereitende Aufgaben durch](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html?lang=de): Registrieren Sie sich bei Adobe Target und konfigurieren Sie bestimmte Aspekte der AEM-Autoreninstanz. Ihre Adobe Target-Konto muss mindestens über Berechtigungen auf der Ebene **Genehmigende Person** verfügen. Darüber hinaus müssen Sie die Aktivitätseinstellungen auf dem Veröffentlichungsknoten so sichern, dass sie für Benutzer nicht zugänglich sind.

* Experience Platform Launch ist das Tool zur Instrumentierung einer AEM-Site mit Target-Funktionen (JS-Bibliotheken). Daher erfolgt die Integration von AEM as a Cloud Service in Launch und Adobe Target Hand in Hand (siehe die Links unten).

   * [Integration mit Adobe Target über Adobe I/O](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/integration-target-ims.html)
   * [Integrieren von Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html)
   * [Integrieren von AEM in Adobe Launch über Adobe I/O](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html?lang=en)
   * [Grundlegendes zur AEM-Integration mit Adobe Experience Platform Launch, Analytics und Target](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html)

>[!NOTE]
>
>Die IMS-Konfiguration (technische Konten) für Adobe Experience Platform Launch ist in AEM as a Cloud Service vorkonfiguriert. Benutzer müssen diese Konfiguration nicht erstellen.

1. [Konfigurieren Sie die Aktivitäten](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html?lang=de): Verknüpfen Sie Ihre Aktivitäten mit der Target-Cloud-Konfiguration.

>[!CAUTION]
>
>In AEM as a Cloud Service ist der Replikations-Agent, der Angebote und Aktivitäten von AEM mit Adobe Target synchronisiert, standardmäßig deaktiviert. Kontaktieren Sie die [Adobe-Support](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de#support) Team, wenn Sie den Replikationsagenten erneut aktivieren müssen.

>[!NOTE]
>
>Wenn Sie Target mit einer benutzerdefinierten Proxy-Konfiguration verwenden, müssen Sie beide HTTP-Client-Proxy-Konfigurationen konfigurieren, da einige Funktionen von AEM die 3.x-APIs und andere die 4.x-APIs verwenden:
>
>* 3.x wird mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert.
>* 4.x wird mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.
>

>[!CAUTION]
>
>Sichern des Aktivitätseinstellungsknotens **cq:ActivitySettings** auf der Veröffentlichungsinstanz, sodass sie für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Service zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.
>
>Siehe [Voraussetzungen für die Integration in Adobe Target](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html?lang=de#securing-the-activity-settings-node) für detaillierte Informationen.

Wenn die Integration abgeschlossen ist, können Sie [gezielte Inhalte verfassen](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/content-targeting-touch.html?lang=de), die Besucherdaten an Adobe Target senden. Seitenkomponenten benötigen spezifischen Code, um das Inhalts-Targeting zu aktivieren. (Siehe [Entwicklung im Hinblick auf gezielte Inhalte](https://experienceleague.adobe.com/docs/experience-manager-65/developing/personlization/target.html?lang=de)).

>[!NOTE]
>
>Wenn Sie eine Komponente in AEM Author anvisieren, führt die Komponente eine Reihe von Server-seitigen Aufrufen an Adobe Target durch, um die Kampagne zu registrieren, Angebote einzurichten und Adobe Target-Segmente abzurufen (falls konfiguriert). Es werden keine Server-seitigen Aufrufe von AEM Publish an Adobe Target vorgenommen.

## Quellen für Hintergrundinformationen {#background-information-sources}

Die Integration von AEM as a Cloud Service mit Adobe Target erfordert Kenntnisse über Adobe Target, AEM-Aktivitäts-Management und AEM-Zielgruppen-Management. Sie sollten mit den folgenden Informationen vertraut sein:

* Adobe Target (siehe [Adobe Target-Dokumentation](https://experienceleague.adobe.com/docs/target/using/target-home.html?lang=de)).
* AEM-Aktivitätskonsole (siehe [Verwalten von Aktivitäten](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html?lang=de)).
* AEM-Zielgruppen (siehe [Verwalten von Zielgruppen](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/managing-audiences.html?lang=de)).

>[!NOTE]
>
>Bei der Arbeit mit Adobe Target ist die maximale Anzahl von Artefakten, die in einer Kampagne zulässig ist:
>
>* 50 Standorte
>* 2.000 Erlebnisse
>* 50 Metriken
>* 50 Berichtssegmente
