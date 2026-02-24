---
title: Verwenden von Inhaltsfragmenten mit Adobe Journey Optimizer
description: 'Erfahren Sie, wie Sie Inhaltsfragmente mit Adobe Journey Optimizer integrieren und verwenden können. '
feature: Content Fragments
role: User, Developer
solution: Experience Manager Sites
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 4090ee41-80f1-4389-8961-e4af891f01ff
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 97%

---

# Inhaltsfragmente mit Adobe Journey Optimizer {#content-fragments-with-journey-optimizer}

[Adobe Journey Optimizer](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/get-started) hilft Ihnen dabei, vernetzte, kontextbezogene und personalisierte Erlebnisse für Ihre Kundschaft bereitzustellen. Durch die Integration von Adobe Experience Manager (AEM) as a Cloud Service mit Adobe Journey Optimizer (AJO) können Sie AEM-Inhalte in Ihren AJO-Inbound-Kanälen und in Ihren AJO-Outbound-Kanälen wiederverwenden, einschließlich Web, SMS, E-Mail und anderen.

Sie haben beispielsweise folgende Möglichkeiten:

* Nahtlose Integration Ihrer [AEM-Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md) in Inhalte von [Journey Optimizer-E-Mails](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/email/email-landing-page)
* Vorschau des AJO-Erlebnisses direkt aus AEM

Die Vernetzung von Inhaltsfragmenten mit AJO vereinfacht den Abruf und die Nutzung von AEM-Inhalten und ermöglicht die Erstellung personalisierter und dynamischer Kampagnen und Journeys.

Weitere Informationen erhalten Sie in der Dokumentation zu AJO:

* [Verwenden von Inhaltsfragmenten in AEM](https://experienceleague.adobe.com/docs/journey-optimizer/using/integrations/aem-fragments.html#integrations)
* [Integration von AJO-Angeboten mit Inhaltsfragmenten](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/managing-offers-in-the-offer-library/configure-offers/add-representations#urls)

## Dispatcher-Konfiguration {#dispatcher-configuration}

Damit AJO über die [API zur Inhaltsfragmentverwaltung](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/) auf die AEM-Inhaltsfragmente zugreifen kann, müssen Sie den Dispatcher konfigurieren:

* In `dispatcher/src/conf.dispatcher.d/filters/filters.any`:

* Hinzufügen:

  ```xml
  # Allow Content Fragments API requests, required for integration with AJO 
  /200 {/type "allow" /url "/adobe/sites/cf/*" }
  ```

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie unter:

* Die [Erweiterung für externe AJO-Verweise](/help/sites-cloud/administering/content-fragments/extension-content-fragment-ajo-external-references.md)
