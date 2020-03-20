---
title: Integration mit Adobe Target
description: 'Integration mit Adobe Target '
translation-type: tm+mt
source-git-commit: ed8cfc564e198552ae4efabee1ff48950470790a

---


# Integration mit Adobe Target{#integrating-with-adobe-target}

As part of the Adobe Marketing Cloud, [Adobe Target](http://www.adobe.com/solutions/testing-targeting/testandtarget.html) lets you increase content relevance through targeting and measuring across all channels. Adobe Target wird von Marketing-Experten genutzt, um Online-Tests zu entwerfen und auszuführen, in kurzer Zeit Zielgruppensegmente zu erstellen (anhand des Verhaltens) und das Targeting für Inhalte und Onlineerlebnisse zu automatisieren. AEM als Cloud-Dienst hat den Targeting-Arbeitsablauf übernommen, der in Adobe Zielgruppe Standard verwendet wird. Wenn Sie Zielgruppe verwenden, sind Sie mit der Targeting-Umgebung zur Bearbeitung in AEM als Cloud-Dienst vertraut.

Integrieren Sie Ihre AEM-Sites in Adobe Target, um den Inhalt auf Ihren Seiten zu personalisieren:

* Implementieren Sie das Inhalts-Targeting.
* Verwenden Sie Target-Zielgruppen, um personalisierte Erlebnisse zu erstellen.
* Übermitteln Sie Kontextdaten an Target, wenn Besucher mit Ihren Seiten interagieren.
* Verfolgen Sie Konvertierungsraten nach.

>[!NOTE]
>
>Adobe Experience Manager als Cloud-Dienstkunden, die über kein bestehendes Zielgruppe-Konto verfügen, können den Zugriff auf das Zielgruppe Foundation Pack für Experience Cloud anfordern.  Das Foundation Pack bietet eine begrenzte Anzahl von Zielgruppen.


Führen Sie zur Integration in Target die folgenden Aufgaben durch:

* [Führen Sie vorbereitende Aufgaben durch](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html): Registrieren Sie sich bei Adobe Target und konfigurieren Sie bestimmte Aspekte der AEM-Autoreninstanz. Your Adobe Target account must have **approver** level permissions at a minimum. Darüber hinaus müssen Sie die Aktivitätseinstellungen auf dem Veröffentlichungsknoten so sichern, dass sie für Benutzer nicht zugänglich sind.

* Launch by Adobe ist das defacto-Tool zur Instrumentierung einer AEM-Site mit Zielgruppe-Funktionen (JS-Bibliotheken). Die Integration von AEM als Cloud-Dienst in Launch und Adobe-Zielgruppe erfolgt daher Hand in Hand (siehe die Links unten).

   * [Integration mit Adobe Zielgruppe mit Adobe I/O](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/integration-ims-adobe-io.html)
   * [Starten von Adobe integrieren](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
   * [Integration von AEM mit Adobe Launch über Adobe I/O](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
   * [Die AEM-Integration mit dem Start von Adobe, Analytics und der Zielgruppe](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)

>[!NOTE]
>
>Die IMS-Konfiguration (technische Konten) zum Starten durch Adobe ist in AEM als Cloud-Dienst vorkonfiguriert. Benutzer müssen diese Konfiguration nicht erstellen.

1. [Konfigurieren Sie die Aktivitäten](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html): Verknüpfen Sie Ihre Aktivitäten mit der Target-Cloud-Konfiguration.

>[!CAUTION]
>
>In AEM als Cloud-Dienst ist der Replizierungsagenten, der Angebot und Aktivitäten von AEM mit Adobe-Zielgruppe synchronisiert, standardmäßig deaktiviert. Wenden Sie sich an das [Adobe-Supportteam](https://helpx.adobe.com/contact/enterprise-support.ec.html#experience-manager) , wenn Sie den Replizierungsagenten erneut aktivieren möchten.

>[!NOTE]
>
>Wenn Sie Target mit einer benutzerdefinierten Proxy-Konfiguration verwenden, müssen Sie beide HTTP-Client-Proxy-Konfigurationen vornehmen, da manche Funktionen von AEM 3.x-APIs verwenden und andere wiederum 4.x-APIs:
>
>* 3.x is configured with [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wird mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)  konfiguriert.
>



>[!CAUTION]
>
>Sie müssen den Aktivitätseinstellungsknoten **cq:ActivitySettings** auf der Veröffentlichungsinstanz sichern, sodass dieser für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Dienst zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.
>
>Detaillierte Informationen finden Sie unter [Voraussetzungen für die Integration in Adobe Target](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html#securing-the-activity-settings-node).

When the integration is complete, you can [author targeted content](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/content-targeting-touch.html) that sends visitor data to Adobe Target. Beachten Sie, dass für Seitenkomponenten ein spezifischer Code erforderlich ist, um das Content-Targeting zu aktivieren. (See [Developing for Targeted Content](https://docs.adobe.com/content/help/en/experience-manager-65/developing/personlization/target.html).

>[!NOTE]
>
>Wenn Sie eine Komponente in AEM Author anvisieren, führt die Komponente eine Reihe von serverseitigen Aufrufen an Adobe Target durch, um die Kampagne zu registrieren, Angebote einzurichten und Adobe Target-Segmente abzurufen (falls konfiguriert). Es werden keine serverseitigen Aufrufe von AEM Publish an Adobe Target vorgenommen.

## Quellen für Hintergrundinformationen {#background-information-sources}

Die Integration von AEM als Cloud-Dienst mit Adobe Zielgruppe erfordert Kenntnisse über Adobe Zielgruppe, AEM Aktivitäten-Management und AEM Audiencen-Management. Sie sollten mit den folgenden Informationen vertraut sein:

* Adobe Target (See the [Adobe Target documentation](https://marketing.adobe.com/resources/help/en_US/target/)).
* AEM Activities console (See [Managing Activities](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html).
* AEM-Zielgruppen (siehe [Verwalten von Zielgruppen](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/managing-audiences.html).

>[!NOTE]
>
>Bei der Arbeit mit Adobe Target ist Folgendes die maximal zulässige Anzahl an Artefakten innerhalb einer Kampagne:
>
>* 50 Positionen
>* 2.000 Erlebnisse
>* 50 Metriken
>* 50 Berichtssegmente
>


