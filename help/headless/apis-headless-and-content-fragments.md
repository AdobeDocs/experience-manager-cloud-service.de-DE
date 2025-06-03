---
title: AEM-APIs für die Bereitstellung strukturierter Inhalte und die Verwaltung von Inhaltsfragmenten
description: Erfahren Sie mehr über die APIs, die für die Bereitstellung strukturierter Inhalte und die Verwaltung von Inhaltsfragmenten verfügbar sind.
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: 95aecd30-566a-42a9-b97a-7efe45fd389c
source-git-commit: 243adc6f6428cea23c04ca788bd8ad0bda7e4501
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 94%

---

# AEM-APIs für die Bereitstellung und Verwaltung strukturierter Inhalte {#aem-apis-structured-content-delivery-and-management}

Adobe Experience Manager (AEM) as a Cloud Service bietet mehrere APIs für die Bereitstellung strukturierter Inhalte über Inhaltsfragmente und die Verwaltung von Inhaltsfragmenten. Weitere Informationen zu den spezifischen APIs finden Sie auf den einzelnen Seiten.

* [Bereitstellung von AEM-Inhaltsfragmenten mit OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)
   * Diese API erstellt JSON-Antworten für die Bereitstellung strukturierter Inhalte aus Inhaltsfragmenten in AEM.
   * Sie verwendet einen Pfad zu einem Inhaltsfragment als Endpunkt.
   * Diese API basiert auf REST.
   * Sie ist für die Bereitstellung von Inhalten optimiert, einschließlich der CDN-Integration.
* [AEM-GraphQL-API für die Bereitstellung von Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)
   * Diese API ist schemabasiert. API-Schemata werden durch Inhaltsfragmentmodelle dargestellt, die die Inhaltsstruktur definieren.
   * Diese API basiert auf GraphQL.
* [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md)
   * Diese APIs sind für die Verwaltung strukturierter Inhalte vorgesehen.
   * Die jeweiligen GET-Operatoren sind nicht für die Inhaltsbereitstellung optimiert.
   * Diese API basiert auf REST.

>[!NOTE]
>
>[Unterstützung von Inhaltsfragmenten in der Assets-HTTP](/help/assets/content-fragments/assets-api-content-fragments.md)API ist jetzt [veraltet](/help/release-notes/deprecated-removed-features.md). Sie wurde ersetzt durch [Bereitstellung von Inhaltsfragmenten mit OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md) zusammen mit [OpenAPIs für die Verwaltung von Inhaltsfragmentmodellen](/help/headless/content-fragment-openapis.md).

## REST im Vergleich zu GraphQL {#rest-vs-graphql}

Welche API verwendet wird, ist die Entscheidung der Entwicklerinnen und Entwickler – AEM unterstützt beide.

Viele Vergleiche sind online verfügbar, aber einige Highlights und Vorteile von REST sind:

* Einfachheit

   * Entwicklerinnen und Entwickler sind (häufig) mit HTTP und REST vertraut. Gemäß dem Bericht [Postman State of the APIs](https://www.postman.com/state-of-api/) verwendet ein hoher Prozentsatz der Entwicklerinnen und Entwickler REST.

   * Einfachheit schafft Vertrautheit. Bei REST gibt es keine organisatorischen Fragen, wem die Abfragen oder die App gehören, während diese Fragen bei GraphQL auftreten können.

   * Die Vertrautheit geht (in der Regel) mit einer breiten Landschaft von Communitys und Tools einher. Dies ist kein inhärenter Nachteil von GraphQL, aber bei REST ist dies wahrscheinlich umfassender und tiefgreifender.

   * Der einfachere Ansatz kann auch die Sicherheitsimplementierung erleichtern. Mit REST erfolgt die Filterung zum Ermitteln der Inhalte, die gerendert werden sollen, in der Client-App. Mit GraphQL erfolgt dies in einer schemabasierten Abfrage zwischen Client und Server.

* Flexibilität

   * Mit REST kann das Entwicklungs-Team `GET` für jede beliebige Ressource ausführen. Bei GraphQL ist es auf Ressourcen beschränkt, die in einem Schema definiert sind.

* Caching

   * JSON-Antworten auf REST-`GET`-Anfragen können grundsätzlich zwischengespeichert werden. GraphQL-`POST`-Anfragen können nicht zwischengespeichert werden, es sei denn, sie werden so konfiguriert, z. B. durch die Verwendung von persistierten AEM-Abfragen, die auf dem Server gespeichert und mit REST-ähnlichen `GET`-Anfragen angefordert werden.

Zu den Vorteilen von GraphQL zählen:

* Effizienz der Inhaltsbereitstellung

   * Fokus

      * Mit GraphQL können Client-Anwendungen genau die Inhalte anfordern, die sie für die Darstellung benötigen – und nicht mehr. Dieser Ansatz verhindert eine Überlieferung von Inhalten mit übermäßiger Nutzlast und unnötigem Bandbreitenverbrauch.

   * Einzelner Endpunkt

      * Während in REST jede API-Anfrage ein Endpunkt ist, gibt es in GraphQL nur einen gemeinsamen Endpunkt, und verschiedene Inhaltsanfragen werden als Abfragen unter Verwendung dieses gemeinsamen Endpunkts ausgedrückt.

* Schnelle Prototypen

   * Mit GraphQL ist dies ein einstufiger Prozess, der in der GraphQL-Abfrage zusammengefasst wird und die Erstellung von Prototypen erleichtern kann. REST dagegen ist ein zweistufiger Prozess:

      1. Abrufen von Inhalten mit der API.
      2. In der JSON-Antwort wird festgelegt, was für die Darstellung in der Client-App verwendet werden soll.
