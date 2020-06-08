---
title: Datenschutzbestimmungen und Datenschutzbestimmungen - Adobe Experience Manager als Cloud-Dienst-Bereitschaftsdienst
description: 'Informieren Sie sich über Adobe Experience Manager als Cloud-Service-Unterstützung für die verschiedenen Datenschutzbestimmungen und Datenschutzbestimmungen. einschließlich der EU-Datenschutzverordnung (GDPR), des kalifornischen Datenschutzgesetzes für Verbraucher und wie bei der Implementierung eines neuen AEM als Cloud-Service-Projekt einzuhalten ist. '
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 1%

---


# Adobe Experience Manager als Cloud Service Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Für Informationen zu Datenschutzbestimmungen und Datenschutzbestimmungen wenden Sie sich bitte an die Rechtsabteilung Ihrer Firma.

>[!NOTE]
>
>Weitere Informationen über die Reaktion von Adobe auf Datenschutzprobleme und was dies für Sie als Adobe-Kunde bedeutet, finden Sie im Datenschutzzentrum von [Adobe](https://www.adobe.com/privacy.html).

Adobe stellt Dokumentation und Vorgehensweisen bereit (mit APIs, sofern verfügbar), damit der Datenschutzadministrator oder AEM-Administrator Datenschutzanforderungen bearbeiten und unsere Kunden bei der Einhaltung dieser Vorschriften unterstützen kann. Die dokumentierten Verfahren ermöglichen es den Kunden, die regulatorischen Anfragen manuell oder, falls verfügbar, über ein externes Portal oder einen externen Dienst in APIs auszuführen.

>[!CAUTION]
>
>Die hier beschriebenen Details sind auf Adobe Experience Manager als Cloud-Dienst beschränkt.
>
>Daten eines anderen Adobe On-Demand-Dienstes erfordern zusammen mit allen damit zusammenhängenden Datenschutzanforderungen Maßnahmen, die für diesen Dienst durchgeführt werden müssen.
>
>Weitere Informationen finden Sie im Datenschutzzentrum von [Adobe](https://www.adobe.com/privacy.html).

## Einführung {#introduction}

Instanzen von Adobe Experience Manager als Cloud-Dienst und die darauf ausgeführten Anwendungen gehören unseren Kunden und werden von ihnen betrieben.

Daher sind Datenschutzbestimmungen wie GDPR, CCPA und andere weitgehend in der Verantwortung der Kunden.

Die Vorschriften für den Datenschutz und den Datenschutz enthalten in Kürze neue Vorschriften, denen die Rollen folgender Personen folgen müssen:

* Geschäftseinheiten (CCPA) und/oder Datenkontrolleure (GDPR)

* Dienstleister (CCPA) und/oder Datenprozessoren (GDPR)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. erweiterte Definition der personenbezogenen Daten, um alle eindeutigen IDs einzuschließen; wie in direkt oder indirekt identifizierbaren Daten.

2. Verbesserte Anforderungen an die Zustimmung.

3. Verbesserter Fokus auf Löschrechte (Datenlöschung).

4. Ausschluss des Verkaufs von Daten.

Für Adobe Experience Manager als Cloud-Dienst:

* Die Instanzen und Anwendungen, die auf ihnen ausgeführt werden, gehören dem Kunden und werden von ihm betrieben.

   * Dies bedeutet, dass der Kunde die regulatorischen Aufgaben, einschließlich Geschäftseinheiten und Dienstleister, Datencontroller und Datenprozessor, unter anderem verwaltet.

   * Der Datenschutzdienst für Adobe Experience Platform ist nicht Teil des Arbeitsablaufs für AEM, wie in der Abbildung unten dargestellt.

* AEM umfasst Dokumentation und Verfahren für den Datenschutzadministrator des Kunden und/oder AEM-Administrator, um die Datenschutzregulierungsanforderungen auszuführen. entweder manuell oder über APIs, falls verfügbar.

* Es wurde kein neuer Dienst oder keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale des Kunden dokumentiert, die Datenschutzanforderungen bearbeiten.

* AEM enthält keine standardmäßigen Werkzeuge zur Unterstützung des Arbeitsablaufs für Datenschutzanforderungen.

   * Adobe stellt Dokumentation und Vorgehensweisen für den Datenschutzadministrator und/oder AEM-Administrator bereit, damit diese Anforderungen im Zusammenhang mit den Datenschutzbestimmungen manuell ausführen können.

Adobe stellt Verfahren für die Verarbeitung von Datenschutzanforderungen im Zusammenhang mit Zugriff, Löschen und Abmelden für Adobe Experience Manager als Cloud-Dienst bereit. In einigen Fällen stehen APIs zur Verfügung, die von einem vom Kunden entwickelten Portal oder Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Das folgende Diagramm zeigt, wie ein Arbeitsablauf für Datenschutzanforderungen aussehen könnte (dargestellt mit Adobe Experience Manager 6.5):

![Datenschutz und Datenschutz](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager als Cloud-Dienst und regulatorische Bereitschaft {#aem-as-a-cloud-service-and-regulatory-readiness}

In den folgenden Abschnitten finden Sie die Dokumentation zu den Produktbereichen von AEM als Cloud-Dienst.

## Adobe Experience Manager als Cloud Service Foundation {#aem-foundation}

See [AEM Foundation Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## Sites in Adobe Experience Manager as a Cloud Service {#aem-sites}

See [AEM Sites Readiness for Data Protection and Data Privacy Regulations.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager als Cloud-Service-Integration mit Adobe Zielgruppe und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Adobe Experience Manager als Cloud-Service-Integrationen sind mit datenschutzfertigen Diensten (z. B. GDPR) ausgestattet. In AEM werden keine personenbezogenen Daten von Adobe Zielgruppe oder Adobe Analytics in Bezug auf die Integrationen gespeichert.
Weitere Informationen finden Sie unter:

* [Adobe-Zielgruppe - Datenschutzübersicht](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Adobe Analytics Data Privacy Workflow](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
