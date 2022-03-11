---
title: Datenschutzbestimmungen – Befolgung durch Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Unterstützung der verschiedenen Datenschutzbestimmungen durch Adobe Experience Manager as a Cloud Service, darunter die EU-Datenschutz-Grundverordnung (DSGVO), das kalifornische Verbraucherdatenschutzgesetz (CCPA) und die Einhaltung der Vorschriften bei der Implementierung eines neuen Projekts in AEM as a Cloud Service.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: e9c1ec6807f86ab00f89ef292a89a0c8efdf802b
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 100%

---

# Befolgung der Datenschutzbestimmungen durch Adobe Experience Manager as a Cloud Service {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion von Adobe auf Datenschutzprobleme und was dies für Sie als Adobe-Kunde bedeutet, finden Sie im [Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy.html).

Adobe stellt Dokumentationen und Verfahren (sofern verfügbar auch unter Verwendung von APIs) bereit, die Datenschutz- und AEM-Administratoren für die Handhabung von datenbezogenen Anfragen verwenden können und die unsere Kunden dabei unterstützen, die Anforderungen dieser Verordnungen zu erfüllen. Mithilfe der beschriebenen Verfahren können DSGVO-bezogene Anfragen entweder manuell oder API-gestützt (sofern verfügbar) über ein externes Portal oder einen externen Service verarbeitet werden.

>[!CAUTION]
>
>Die hier dokumentierten Details sind auf Adobe Experience Manager as a Cloud Service beschränkt.
>
>Daten aus einem anderen Adobe-On-Demand-Service und alle damit verbundenen Datenschutzanfragen erfordern, dass für diesen Service Maßnahmen ergriffen werden.
>
>Weitere Informationen finden Sie unter [Datenschutzzentrum von Adobe](https://www.adobe.com/privacy.html).

## Einführung {#introduction}

Die Instanzen von Adobe Experience Manager as a Cloud Service und die darauf ausgeführten Anwendungen liegen in der Verantwortung unserer Kunden und werden von ihnen betrieben.

Daher sind Datenschutzbestimmungen wie die DSGVO, der CCPA und andere größtenteils Sache der Kunden.

In einer kurzen Einführung enthalten die Vorschriften für Datenschutz neue Regeln, denen die nachstehenden Rollen folgen müssen:

* Unternehmens-Entitäten (CCPA) und/oder Datenverantwortliche (DSGVO)

* Dienstleister (CCPA) und/oder Auftragsverarbeiter (DSGVO)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. Erweiterte Definition personenbezogener Daten, um alle eindeutigen Kennungen einzuschließen; wie in direkt und indirekt identifizierbaren Daten.

2. Verschärfte Anforderungen an das Einverständnis.

3. Verstärkter Fokus auf Löschrechte (Datenlöschung).

4. Opt-out vom Verkauf von Daten.

Für Adobe Experience Manager as a Cloud Service:

* Die Instanzen und die darauf ausgeführten Anwendungen liegen in der Verantwortung unserer Kunden und werden von ihnen betrieben.

   * Dies bedeutet effektiv, dass der Kunde die regulatorischen Rollen verwaltet, darunter Unternehmens-Entitäten und Dienstleister, Datenverantwortliche und Auftragsverarbeiter.

   * Der Adobe Experience Platform Privacy Service ist nicht Teil des Workflows für AEM, wie in der folgenden Abbildung dargestellt.

* AEM umfasst Dokumentationen und Verfahren für den Datenschutzadministrator und/oder AEM-Administrator des Kunden, die Datenschutzanfragen manuell oder über APIs (sofern verfügbar) zu bearbeiten.

* Es wurde kein neuer Service und keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale von Kunden dokumentiert, die Datenschutzanfragen bearbeiten.

* AEM enthält keine vorkonfigurieren Tools zur Unterstützung des Workflows für Datenschutzanfragen.

   * Adobe stellt dem Datenschutzadministrator und/oder AEM Administrator des Kunden Dokumentationen und Verfahren zur Verfügung, mit denen er Anfragen im Zusammenhang mit den Datenschutzbestimmungen manuell bearbeiten kann.

Adobe bietet Verfahren für die Bearbeitung von Datenschutzanfragen im Zusammenhang mit Zugriff, Löschen und Opt-out für Adobe Experience Manager as a Cloud Service. In einigen Fällen sind APIs verfügbar, die von einem vom Kunden entwickelten Portal oder von Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Die folgende Abbildung zeigt, wie ein Workflow für Datenschutzanfragen aussehen könnte (unter Verwendung von Adobe Experience Manager 6.5):

![Datenschutz](assets/data-protection-and-privacy-01.png)

## Befolgung der Vorschriften durch Adobe Experience Manager as a Cloud Service {#aem-as-a-cloud-service-and-regulatory-readiness}

In den folgenden Abschnitten finden Sie die Dokumentation zu Vorschriften für einzelne Produktbereiche von AEM as a Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Siehe [AEM Foundation – Einhaltung von Datenschutzbestimmungen](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager as a Cloud Service Sites {#aem-sites}

[AEM Sites – Einhaltung von Datenschutzbestimmungen](/help/compliance/data-privacy-and-protection-readiness/sites-readiness.md).

## Integration von Adobe Experience Manager as a Cloud Service mit Adobe Target und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Adobe Experience Manager as a Cloud Service-Integrationen sind mit datenschutzfähigen Services (z. B. DSGVO) ausgestattet. In AEM werden keine personenbezogenen Daten von Adobe Target oder Adobe Analytics in Bezug auf die Integrationen gespeichert.
Weitere Informationen finden Sie unter:

* [Adobe Target – Datenschutzübersicht](https://experienceleague.adobe.com/docs/target/using/implement-target/before-implement/privacy/privacy.html?lang=de)

* [Adobe Analytics-Datenschutz-Workflow](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html?lang=de)
