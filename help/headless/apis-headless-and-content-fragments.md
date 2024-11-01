---
title: AEM-APIs für die Bereitstellung strukturierter Inhalte und die Verwaltung von Inhaltsfragmenten
description: Erfahren Sie mehr über die APIs, die für die Bereitstellung strukturierter Inhalte und für das Inhaltsfragmentmanagement verfügbar sind.
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
source-git-commit: 21599676916068f3529976410a93951b02f750b0
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 3%

---


# AEM APIs für die Bereitstellung und Verwaltung strukturierter Inhalte {#aem-apis-structured-content-delivery-and-management}

Adobe Experience Manager (AEM) as a Cloud Service bietet mehrere APIs für die Bereitstellung strukturierter Inhalte über Inhaltsfragmente und die Inhaltsfragmentverwaltung. Weitere Informationen zu den spezifischen APIs finden Sie auf den einzelnen Seiten .

* [AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten](/help/headless/aem-rest-openapi-content-fragment-delivery.md)
   * Diese API erstellt JSON-Antworten für die Bereitstellung strukturierter Inhalte aus Inhaltsfragmenten in AEM.
   * Es verwendet einen Pfad zu einem Inhaltsfragment als Endpunkt.
   * Diese API basiert auf REST.
   * Sie ist für die Bereitstellung von Inhalten optimiert, einschließlich der CDN-Integration.
* [GraphQL-API für die Bereitstellung von Inhaltsfragmenten AEM](/help/headless/graphql-api/content-fragments.md)
   * Diese API ist schemabasiert. API-Schemata werden durch Inhaltsfragmentmodelle dargestellt, die die Inhaltsstruktur definieren.
   * Diese API basiert auf GraphQL.
* [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md)
   * Diese APIs sind für das strukturierte Content Management gedacht.
   * Die jeweiligen GET sind nicht für die Inhaltsbereitstellung optimiert.
   * Diese API basiert auf REST.
* [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)
   * Die ursprüngliche API für die JSON-Ausgabe für die Bereitstellung strukturierter Inhalte in AEM.
      * Diese API ist zwar stabil und bewährt, liefert jedoch keine JSON-Ausgabe mit *vollem Hydrat*. Verweise werden nur als Pfade ausgegeben, sodass sekundäre API-Anfragen zum Abrufen weiterer Inhalte erforderlich sind.
   * Die Assets HTTP-API kann auch zum Verwalten der Inhaltsfragmente und Inhaltsfragmentmodelle (CRUD) verwendet werden.
   * Diese API basiert auf REST.
   * Die Unterstützung von Inhaltsfragmenten in der Assets-HTTP-API wird in Zukunft eingestellt, da sie durch die Edge Delivery Services-JSON-REST-API ersetzt wird. Der Zeitplan ist noch nicht festgelegt.

<!--
## JSON vs HTML {#json-vs-HTML}

The content delivery format used is driven by frontend implementation. Unstructured content/HTML for full-stack implementations, structured content/JSON for headless implementations, or a combination of both in hybrid implementations. 

Key considerations include:

* Definition
  * JSON (JavaScript Object Notation) - used to represent, access and process structured data. 
  * HTML (HyperText Markup Language) - a markup language of tags and elements in a hierarchical structure.
* Primary Purpose
  * JSON is often used for transferring structure content between the server and client app.
  * HTML is the standard markup language for creating and rendering web pages in a browser.
-->

## REST vs. GraphQL {#rest-vs-graphql}

Die verwendete API ist eine Entscheidung für die Entwickler - AEM unterstützt beide.

Viele Vergleiche sind online verfügbar, aber einige Highlights und Vorteile von REST sind:

* Einfachheit

   * Entwickler sind (häufig) mit HTTP und REST vertraut. Gemäß dem [Postman-Status des APIs-Berichts](https://www.postman.com/state-of-api/) verwendet ein hoher Prozentsatz der Entwickler REST.

   * Einfachheit bringt Vertrautheit mit sich. Bei REST gibt es keine organisatorischen Fragen, wer für die Abfragen verantwortlich ist und wem die App gehört, während diese Fragen bei GraphQL auftreten können.

   * Mit Vertrautheit (in der Regel) kommt eine breite Community und Tooling-Landschaft. Kein Nachteil von GraphQL, aber wahrscheinlich umfassender und tiefer für REST.

   * Der einfachere Ansatz kann auch die Sicherheitsimplementierung erleichtern. Mit REST erfolgt die Filterung zum Ermitteln des Inhalts, der gerendert werden soll, in der Client-App. Mit GraphQL erfolgt dies in einer schemabasierten Abfrage zwischen Client und Server.

* Flexibilität

   * Mit REST kann der Entwickler eine beliebige Ressource `GET` verwenden. Bei GraphQL sind sie auf Ressourcen beschränkt, die in einem Schema definiert sind.

* Caching

   * JSON-Antworten auf REST `GET`-Anfragen können grundsätzlich zwischengespeichert werden. GraphQL `POST` -Anforderungen können nicht zwischengespeichert werden, es sei denn, sie sind vorhanden. Dies kann beispielsweise durch die Verwendung AEM persistenten Abfragen geschehen, die auf dem Server gespeichert sind und mit REST-ähnlichen `GET`Anforderungen angefordert werden.

Zu den Vorteilen von GraphQL zählen:

* Effizienz der Inhaltsbereitstellung

   * Fokus

      * Mit GraphQL können Clientanwendungen genau den Inhalt anfordern, den sie für das Rendering benötigen - und nicht mehr. Dieser Ansatz verhindert eine Überlieferung von Inhalten mit übermäßiger Nutzlast und unnötigem Bandbreitenverbrauch.

   * Einzelendpunkt

      * Während in REST jede API-Anfrage ein -Endpunkt ist, gibt es in GraphQL nur einen gemeinsamen Endpunkt und verschiedene Inhaltsanforderungen werden als Abfragen mit diesem gemeinsamen Endpunkt ausgedrückt.

* Rapid Prototyping

   * Mit GraphQL ist dies ein einstufiger Prozess, der in der GraphQL-Abfrage zusammengeführt wird und die Prototypisierung vereinfachen kann. REST dagegen ist ein zweistufiger Prozess:

      1. Abrufen von Inhalten mit der API.
      2. Legen Sie in der JSON-Antwort fest, was für das Rendern in der Client-App verwendet werden soll.
