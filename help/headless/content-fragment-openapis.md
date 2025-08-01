---
title: OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle
description: Erfahren Sie mehr über die OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle.
exl-id: 077eed73-a066-4273-b2f5-da4bf5cd900c
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: d683051387af5c0de45917a50003c2194d887bc4
workflow-type: ht
source-wordcount: '190'
ht-degree: 100%

---

# OpenAPIs für das Management von Inhaltsfragmenten und Inhaltsfragmentmodellen {#content-fragments-and-content-fragment-models-management-openapis}

Die modernisierte OpenAPI-Implementierung der API für die Verwaltung von Inhaltsfragmenten ermöglicht es Entwicklerinnen und Entwicklern, programmgesteuert Vorgänge zum Erstellen, Lesen, Aktualisieren und Löschen auf der AEM-Autoreninstanz durchzuführen, um die in AEM gespeicherten Inhaltsfragmentmodelle und Inhaltsfragmente zu verwalten. Diese APIs unterstützen eine Reihe von Anwendungsfällen. 

Die bestehende Verwendung des [Assets-HTTP-API](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/admin/mac-api-assets) für Inhaltsfragmente sollte auf das neue OpenAPI für die Verwaltung von Inhaltsfragmenten migriert werden. Eine vollständige Dokumentation finden Sie unter [API für die Verwaltung von Inhaltsfragmenten](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de).

>[!NOTE]
>
>Für den Zugriff auf die OpenAPI ist eine Autorisierung erforderlich, wenn Sie nicht bei AEM angemeldet sind, z. B. wenn die OpenAPI von einem anderen Produkt im Rahmen einer Integration verwendet wird.
>
>Weitere Informationen zur Autorisierung Ihres Zugriffs auf die OpenAPI finden Sie unter [OpenAPI-basierte APIs](/help/implementing/developing/open-api-based-apis.md).

>[!CAUTION]
>
>Standardmäßig ist das OpenAPI für die Inhaltsfragmentverwaltung bei der Veröffentlichung deaktiviert. Stattdessen empfehlen wir für bereitstellungsorientierte Anwendungsfälle die Verwendung des [OpenAPI für die Bereitstellung von Inhaltsfragmenten](/help/headless/aem-content-fragment-delivery-with-openapi.md).

>[!NOTE]
>
>Unter [AEM-APIs für die Bereitstellung und Verwaltung strukturierter Inhalte](/help/headless/apis-headless-and-content-fragments.md) finden Sie einen Überblick über die verschiedenen verfügbaren APIs und einen Vergleich einiger der damit verbundenen Konzepte.