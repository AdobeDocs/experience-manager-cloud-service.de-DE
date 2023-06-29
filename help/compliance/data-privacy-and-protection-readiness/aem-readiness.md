---
title: Datenschutzbestimmungen – Befolgung durch Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Adobe Experience Manager as a Cloud Service-Unterstützung für die verschiedenen Datenschutzbestimmungen. Zu diesen Vorschriften gehören die Datenschutz-Grundverordnung (DSGVO) der EU, das kalifornische Verbraucherdatenschutzgesetz und die Einhaltung der Vorschriften bei der Implementierung eines neuen AEM as a Cloud Service Projekts.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 45%

---

# Befolgung der Datenschutzbestimmungen durch Adobe Experience Manager as a Cloud Service {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion der Adobe auf Datenschutzprobleme und was dieser Datenschutz für Sie als Adobe bedeutet, finden Sie unter [Datenschutzzentrum der Adobe](https://www.adobe.com/de/privacy.html).

Adobe stellt dem Datenschutzadministrator oder AEM Administrator für Kunden Dokumentationen und Vorgehensweisen bereit (mit APIs, sofern verfügbar). Diese Dokumentation hilft Administratoren bei der Verarbeitung von Datenschutz- und Datenschutzanfragen und hilft Adoben-Kunden bei der Einhaltung dieser Vorschriften. Die dokumentierten Verfahren ermöglichen es Kunden, die regulatorischen Anforderungen manuell auszuführen oder APIs, sofern verfügbar, über ein externes Portal oder einen externen Dienst aufzurufen.

>[!CAUTION]
>
>Die hier dokumentierten Details sind auf Adobe Experience Manager as a Cloud Service beschränkt.
>
>Daten aus einem anderen Adobe-On-Demand-Dienst erfordern zusammen mit allen damit verbundenen Datenschutzanfragen, dass für diesen Dienst Maßnahmen ergriffen werden.
>
>Weitere Informationen finden Sie unter [Datenschutzzentrum der Adobe](https://www.adobe.com/de/privacy.html).

## Einführung {#introduction}

Instanzen von Adobe Experience Manager as a Cloud Service und die darauf ausgeführten Anwendungen werden von Adobe-Kunden kontrolliert und betrieben.

Daher sind Datenschutzbestimmungen wie die DSGVO, der CCPA und andere größtenteils Sache der Kunden.

In einer kurzen Einführung enthalten die Vorschriften für Datenschutz und Datenschutz neue Regeln, denen die Rollen folgender Personen folgen müssen:

* Unternehmens-Entitäten (CCPA) und/oder Datenverantwortliche (DSGVO)

* Dienstleister (CCPA) und/oder Auftragsverarbeiter (DSGVO)

Die wichtigsten Bestimmungen dieser Verordnungen sind:

1. Erweiterte Definition personenbezogener Daten, um alle eindeutigen Kennungen einzuschließen; wie in direkt und indirekt identifizierbaren Daten.

2. Verschärfte Anforderungen an das Einverständnis.

3. Verstärkter Fokus auf Löschrechte (Datenlöschung).

4. Opt-out vom Verkauf von Daten.

Für Adobe Experience Manager as a Cloud Service:

* Die Instanzen und die darauf ausgeführten Anwendungen liegen in der Verantwortung unserer Kunden und werden von ihnen betrieben.

   * Diese Eigentümerschaft bedeutet effektiv, dass der Kunde die regulatorischen Rollen, darunter Geschäftseinheiten und Dienstleister, Datenverantwortlicher und Datenverarbeiter, verwaltet.

   * Die Adobe Experience Platform Privacy Service ist nicht Teil des Workflows für AEM, wie in der folgenden Abbildung dargestellt.

* AEM umfasst Dokumentationen und Verfahren für den Datenschutzadministrator und/oder AEM-Administrator des Kunden, die Datenschutzanfragen manuell oder über APIs (sofern verfügbar) zu bearbeiten.

* Es wurde kein neuer Service und keine neue Benutzeroberfläche hinzugefügt.

   * Stattdessen werden Verfahren und APIs für die Verwendung durch die Benutzeroberflächen/Portale von Kunden dokumentiert, die Datenschutzanfragen bearbeiten.

* AEM enthält keine nativen Tools zur Unterstützung des Workflows für Datenschutzanfragen.

   * Adobe bietet dem Datenschutzadministrator oder AEM Administrator des Kunden oder beidem Dokumentationen und Vorgehensweisen, mit denen er Anfragen im Zusammenhang mit den Datenschutzbestimmungen manuell ausführen kann.

Adobe bietet Verfahren für die Verarbeitung von Datenschutzanfragen im Zusammenhang mit Zugriff, Löschen und Opt-out für Adobe Experience Manager as a Cloud Service. Manchmal sind APIs verfügbar, die von einem kundenentwickelten Portal oder von Skripten aufgerufen werden können, um die Automatisierung zu unterstützen.

Die folgende Abbildung zeigt, wie ein Workflow für Datenschutzanfragen aussehen könnte (unter Verwendung von Adobe Experience Manager 6.5):

![Datenschutz](assets/data-protection-and-privacy-01.png)

## Befolgung der Vorschriften durch Adobe Experience Manager as a Cloud Service {#aem-as-a-cloud-service-and-regulatory-readiness}

In den folgenden Abschnitten finden Sie eine Dokumentation zu AEM as a Cloud Service Produktbereichen.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Siehe [AEM Foundation – Einhaltung von Datenschutzbestimmungen](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager as a Cloud Service Sites {#aem-sites}

[AEM Sites – Einhaltung von Datenschutzbestimmungen](/help/compliance/data-privacy-and-protection-readiness/sites-readiness.md)

## Integration von Adobe Experience Manager as a Cloud Service mit Adobe Target und Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Diese Integrationen in Adobe Experience Manager as a Cloud Service sind mit datenschutzbereiten und datenschutzbereiten Diensten (z. B. DSGVO) ausgestattet. In AEM werden keine personenbezogenen Daten von Adobe Target oder Adobe Analytics in Bezug auf die Integrationen gespeichert.
Weitere Informationen finden Sie unter:

* [Adobe Target – Datenschutzübersicht](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/cmp-privacy-and-general-data-protection-regulation.html)

* [Adobe Analytics-Datenschutz-Workflow](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html)
