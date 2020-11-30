---
title: Datenschutzbestimmungen und Datenschutzbestimmungen - Adobe Experience Manager als Cloud Service Readiness
description: 'Erfahren Sie mehr über Adobe Experience Manager als Cloud Service für die verschiedenen Datenschutzbestimmungen und Datenschutzbestimmungen. einschließlich der EU-Datenschutzverordnung (GDPR), des kalifornischen Verbraucherschutzgesetzes und der Frage, wie bei der Umsetzung eines neuen AEM als Cloud Service-Projekt einzuhalten ist. '
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 2%

---


# Adobe Experience Manager als Cloud Service Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Für Informationen zu Datenschutzbestimmungen und Datenschutzbestimmungen wenden Sie sich bitte an die Rechtsabteilung Ihrer Firma.

>[!NOTE]
>
>Weitere Informationen über die Reaktion der Adobe auf Datenschutzfragen und was das für Sie als Adobe bedeutet, finden Sie im Datenschutzzentrum der [Adobe](https://www.adobe.com/privacy.html).

Adobe stellt Dokumentation und Vorgehensweisen (mit APIs, falls verfügbar) bereit, damit der Datenschutzadministrator oder AEM Administrator Daten- und Datenschutzanfragen bearbeiten und unsere Kunden bei der Einhaltung dieser Vorschriften unterstützen kann. Die dokumentierten Verfahren ermöglichen es den Kunden, die regulatorischen Anfragen manuell oder, falls verfügbar, über ein externes Portal oder einen externen Dienst in APIs auszuführen.

>[!CAUTION]
>
>Die hier dokumentierten Details sind auf Adobe Experience Manager als Cloud Service beschränkt.
>
>Daten aus einem anderen On-Demand-Dienst der Adobe sowie alle damit zusammenhängenden Datenschutzanforderungen erfordern Maßnahmen, die in Bezug auf diesen Dienst ergriffen werden müssen.
>
>Weitere Informationen finden Sie im Datenschutzzentrum der [Adobe](https://www.adobe.com/privacy.html).

## Einführung {#introduction}

Die Instanzen von Adobe Experience Manager als Cloud Service und die Anwendungen, die auf ihnen laufen, gehören unseren Kunden und werden von ihnen betrieben.

Daher sind Datenschutzbestimmungen wie GDPR, CCPA und andere weitgehend in der Verantwortung der Kunden.

Die Vorschriften für den Datenschutz und den Datenschutz enthalten in Kürze neue Vorschriften, denen die Rollen folgender Personen folgen müssen:

* Geschäftseinheiten (CCPA) und/oder Datenkontrolleure (GDPR)

* Dienstleister (CCPA) und/oder Datenprozessoren (GDPR)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. erweiterte Definition der personenbezogenen Daten, um alle eindeutigen IDs einzuschließen; wie in direkt oder indirekt identifizierbaren Daten.

2. Verbesserte Anforderungen an die Zustimmung.

3. Verbesserter Fokus auf Löschrechte (Datenlöschung).

4. Ausschluss des Verkaufs von Daten.

Adobe Experience Manager als Cloud Service:

* Die Instanzen und Anwendungen, die auf ihnen ausgeführt werden, gehören dem Kunden und werden von ihm betrieben.

   * Dies bedeutet, dass der Kunde die regulatorischen Aufgaben, einschließlich Geschäftseinheiten und Dienstleister, Datencontroller und Datenprozessor, unter anderem verwaltet.

   * Das Adobe Experience Platform Privacy Service ist nicht Teil des Arbeitsablaufs für AEM, wie in der Abbildung unten dargestellt.

* AEM umfasst Unterlagen und Verfahren, die dem Datenschutzadministrator und/oder AEM Administrator des Kunden zur Durchführung der Datenschutzverordnung zur Verfügung stehen; entweder manuell oder über APIs, falls verfügbar.

* Es wurde kein neuer Dienst oder keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale des Kunden dokumentiert, die Datenschutzanforderungen bearbeiten.

* AEM enthält keine standardmäßigen Werkzeuge zur Unterstützung des Arbeitsablaufs für Datenschutzanforderungen.

   * Adobe stellt Dokumentation und Verfahren für den Datenschutzadministrator und/oder AEM Administrator bereit, damit diese Anfragen im Zusammenhang mit den Datenschutzbestimmungen manuell ausführen können.

Adobe bietet Verfahren zur Bearbeitung von Datenschutzanforderungen in Zusammenhang mit Zugriff, Löschen und Abwählen von Adobe Experience Manager als Cloud Service. In einigen Fällen stehen APIs zur Verfügung, die von einem vom Kunden entwickelten Portal oder Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Das folgende Diagramm zeigt, wie ein Arbeitsablauf für Datenschutzanfragen aussehen könnte (illustriert mit Adobe Experience Manager 6.5):

![Datenschutz und Datenschutz](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager als Cloud Service und Regulierungsbereitschaft {#aem-as-a-cloud-service-and-regulatory-readiness}

Die nachstehende Dokumentation zu den Produktbereichen AEM als Cloud Service finden Sie in den folgenden Abschnitten.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

See [AEM Foundation Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## Sites in Adobe Experience Manager as a Cloud Service {#aem-sites}

See [AEM Sites Readiness for Data Protection and Data Privacy Regulations.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager als Cloud Service-Integration mit Adobe Target und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Adobe Experience Manager als Cloud Service-Integrationen sind mit datenschutzfertigen Diensten (z.B. GDPR) ausgestattet. Im Zusammenhang mit den Integrationen werden keine personenbezogenen Daten von Adobe Target oder Adobe Analytics AEM gespeichert.
Weitere Informationen finden Sie unter:

* [Adobe Target - Datenschutzübersicht](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Adobe Analytics Data Privacy Workflow](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
