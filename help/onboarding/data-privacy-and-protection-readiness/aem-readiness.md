---
title: Datenschutzbestimmungen und Datenschutzbestimmungen - Adobe Experience Manager as a Cloud Service Readiness
description: Erfahren Sie mehr über Adobe Experience Manager as a Cloud Service Support für die verschiedenen Datenschutzbestimmungen. darunter die EU-Datenschutz-Grundverordnung (DSGVO), das kalifornische Verbraucherdatenschutzgesetz und die Einhaltung der Vorschriften bei der Implementierung eines neuen AEM als Cloud Service.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 2%

---

# Adobe Experience Manager as a Cloud Service Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion der Adobe auf Datenschutzprobleme und was dies für Sie als Adobe bedeutet, finden Sie im [Datenschutzzentrum der Adobe](https://www.adobe.com/privacy.html).

Adobe stellt Dokumentationen und Vorgehensweisen bereit (mit APIs, sofern verfügbar), damit der Datenschutzadministrator oder AEM Administrator Datenschutzanfragen bearbeiten und unsere Kunden bei der Einhaltung dieser Vorschriften unterstützen kann. Die dokumentierten Verfahren ermöglichen es den Kunden, die regulatorischen Anfragen manuell oder durch Aufruf von APIs, sofern verfügbar, über ein externes Portal oder einen externen Dienst auszuführen.

>[!CAUTION]
>
>Die hier dokumentierten Details sind auf Adobe Experience Manager as a Cloud Service beschränkt.
>
>Daten aus einem anderen Adobe-On-Demand-Dienst erfordern zusammen mit allen damit verbundenen Datenschutzanfragen, dass für diesen Dienst Maßnahmen ergriffen werden.
>
>Weitere Informationen finden Sie unter [Datenschutzzentrum der Adobe](https://www.adobe.com/privacy.html).

## Einführung {#introduction}

Die Instanzen von Adobe Experience Manager als Cloud Service und die darauf ausgeführten Anwendungen gehören unseren Kunden.

Daher sind Datenschutzbestimmungen wie die DSGVO, der CCPA und andere größtenteils Sache der Kunden.

In einer kurzen Einführung enthalten die Vorschriften für Datenschutz und Datenschutz neue Regeln, denen die Rollen folgender Personen folgen müssen:

* Unternehmen (CCPA) und/oder Datenverantwortliche (DSGVO)

* Dienstleister (CCPA) und/oder Datenverarbeiter (DSGVO)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. Erweiterte Definition personenbezogener Daten, um alle eindeutigen Kennungen einzuschließen; wie in direkt und indirekt identifizierbaren Daten.

2. Verbesserte Genehmigungsanforderungen.

3. Der Fokus wurde verstärkt auf Löschrechte (Datenlöschung) gelegt.

4. Opt-out vom Verkauf von Daten.

Für Adobe Experience Manager as a Cloud Service:

* Die Instanzen und Anwendungen, die auf ihnen ausgeführt werden, gehören dem Kunden und werden von ihm betrieben.

   * Dies bedeutet effektiv, dass der Kunde die regulatorischen Rollen verwaltet, darunter Geschäftseinheiten und Dienstleister, Datenverantwortlicher und Datenverarbeiter.

   * Die Adobe Experience Platform Privacy Service ist nicht Teil des Workflows für AEM, wie in der folgenden Abbildung dargestellt.

* AEM umfasst Dokumentationen und Verfahren für den Datenschutzadministrator und/oder AEM Administrator des Kunden, die Datenschutzanfragen auszuführen. entweder manuell oder über APIs, sofern verfügbar.

* Es wurde kein neuer Dienst oder keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale von Kunden dokumentiert, die Datenschutzanfragen verarbeiten.

* AEM enthält keine nativen Tools zur Unterstützung des Workflows für Datenschutzanfragen.

   * Adobe stellt dem Datenschutzadministrator und/oder AEM Administrator des Kunden Dokumentationen und Verfahren zur Verfügung, mit denen er Anfragen im Zusammenhang mit den Datenschutzbestimmungen manuell ausführen kann.

Adobe bietet Verfahren für die Bearbeitung von Datenschutzanfragen im Zusammenhang mit Zugriff, Löschen und Opt-out für Adobe Experience Manager as a Cloud Service. In einigen Fällen sind APIs verfügbar, die von einem kundenentwickelten Portal oder von Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Das folgende Diagramm zeigt, wie ein Workflow für Datenschutzanfragen aussehen könnte (in der Abbildung von Adobe Experience Manager 6.5):

![Datenschutz und Privatsphäre](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager as a Cloud Service and Regulatory Readiness {#aem-as-a-cloud-service-and-regulatory-readiness}

In den folgenden Abschnitten finden Sie eine Dokumentation zu Produktbereichen von AEM als Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Siehe [AEM Foundation Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## Sites in Adobe Experience Manager as a Cloud Service {#aem-sites}

Siehe [AEM Sites Readiness for Data Protection and Data Privacy Regulations.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager as a Cloud Service Integration mit Adobe Target und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Adobe Experience Manager as a Cloud Service-Integrationen sind mit datenschutzbereiten und datenschutzbereiten Diensten (z. B. DSGVO) ausgestattet. In AEM werden keine personenbezogenen Daten von Adobe Target oder Adobe Analytics in Bezug auf die Integrationen gespeichert.
Weitere Informationen finden Sie unter:

* [Adobe Target - Datenschutzübersicht](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Adobe Analytics-Datenschutz-Workflow](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
