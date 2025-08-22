---
title: Verwenden von Inhaltsfragmenten mit Adobe Journey Optimizer
description: Erfahren Sie, wie Inhaltsfragmente in Adobe Journey Optimizer integriert und verwendet werden können.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
exl-id: 4090ee41-80f1-4389-8961-e4af891f01ff
source-git-commit: 0fd7b2633488ceb14d34b1978a91a3a830d8762a
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 10%

---

# Inhaltsfragmente mit Adobe Journey Optimizer {#content-fragments-with-journey-optimizer}

Mit [Adobe Journey Optimizer](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/get-started) können Sie Ihren Kunden vernetzte, kontextuelle und personalisierte Erlebnisse bereitstellen. Durch die Integration von Adobe Experience Manager (AEM) as a Cloud Service mit Adobe Journey Optimizer (AJO) können Sie AEM-Inhalte in Ihren AJO-Eingangskanälen und in Ihren AJO-Ausgangskanälen wiederverwenden, einschließlich Web, SMS, E-Mail und anderen.

Sie haben beispielsweise folgende Möglichkeiten:

* Nahtlose Integration Ihrer [AEM-Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md) in Ihre [Journey Optimizer-E-Mail](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/email/email-landing-page)Inhalte
* Vorschau des AJO-Erlebnisses direkt aus AEM

Die Verbindung zwischen Inhaltsfragmenten und AJO vereinfacht den Zugriff auf und die Nutzung von AEM-Inhalten und ermöglicht die Erstellung personalisierter und dynamischer Kampagnen und Journey.

Weitere Informationen erhalten Sie in der Dokumentation zu AJO:

* [Verwenden von Inhaltsfragmenten in AJO](https://experienceleague.adobe.com/docs/journey-optimizer/using/integrations/aem-fragments.html?lang=de#integrations)
* [Integration von AJO-Angeboten mit Inhaltsfragmenten](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/managing-offers-in-the-offer-library/configure-offers/add-representations#urls)

## Dispatcher-Konfiguration {#dispatcher-configuration}

Damit AJO über die Inhaltsfragmentverwaltungs-[ auf die AEM](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)Inhaltsfragmente zugreifen kann, müssen Sie die Dispatcher konfigurieren:

* In `dispatcher/src/conf.dispatcher.d/filters/filters.any`:

* Hinzufügen:

  ```xml
  # Allow Content Fragments API requests, required for integration with AJO 
  /200 {/type "allow" /url "/adobe/sites/cf/*" }
  ```

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie unter:

* Die Erweiterung [AJO External References](/help/sites-cloud/administering/content-fragments/extension-content-fragment-ajo-external-references.md)
