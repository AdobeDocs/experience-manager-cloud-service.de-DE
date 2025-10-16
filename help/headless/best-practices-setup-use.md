---
title: Best Practices für das Setup und die Verwendung von AEM GraphQL mit Inhaltsfragmenten
description: Erfahren Sie mehr über die empfohlenen Best Practices für das Setup und die Verwendung von AEM GraphQL mit Inhaltsfragmenten.
exl-id: 4d6a5aaa-c8be-4858-ad07-085dc4fb77e7
feature: Headless
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 100%

---

# Best Practices für das Setup und die Verwendung von AEM GraphQL mit Inhaltsfragmenten{#best-practices-setup-use-aem-graphql-content-fragments}

Diese Richtlinien fassen die empfohlenen Best Practices für das Setup, die Konfiguration und Verwendung von AEM mit GraphQL und Inhaltsfragmenten zusammen.

## Erste Schritte {#getting-started}

Machen Sie sich mit dem Thema vertraut:

* [Was ist Headless?](/help/headless/what-is-headless.md)
* Überblick über die verschiedenen Umgebungen in der [AEM-Architektur](/help/headless/deployment/architecture.md)

## Setup {#setup}

Um AEM GraphQL für die Verwendung mit Inhaltsfragmenten und Apps sicher einzurichten, müssen Sie verschiedene Komponenten konfigurieren.

### Erstellung von GraphQL-Endpunkten (einschließlich Sicherheit) {#graphql-endpoint-creation}

Der Endpunkt ist der Pfad, der für den Zugriff auf GraphQL für AEM verwendet wird. Diese Endpunkte müssen erstellt und veröffentlicht werden, damit sie sicher aufgerufen werden können.

#### Details {#details-graphql-endpoint-creation}

[Verwalten von GraphQL-Endpunkten in AEM](/help/headless/graphql-api/graphql-endpoint.md)

#### Umgebungen {#environments-graphql-endpoint-creation}

Endpunkte müssen konfiguriert werden in:

* Author
* Vorschau
* Publish

Für:

* Entwicklung
* Testen
* Produktion

### AEM Dispatcher-Caching {#dispatcher-caching}

>[!NOTE]
>Wenn die Caching-Funktion im Dispatcher aktiviert ist, wird das [CORS-Setup](#cors-setup) nicht benötigt und kann daher ignoriert werden.

Das Caching persistierter Abfragen ist im Dispatcher standardmäßig nicht aktiviert. Eine Standardaktivierung ist nicht möglich, da Kundinnen und Kunden, die CORS (Cross-Origin Resource Sharing) mit mehreren Ursprüngen verwenden, ihre Dispatcher-Konfiguration überprüfen und möglicherweise aktualisieren müssen.

#### Details {#details-dispatcher-caching}

[Persistierte GraphQL-Abfragen – Aktivieren der Caching-Funktion im Dispatcher](/help/headless/deployment/dispatcher-caching.md)

#### Umgebungen {#environments-dispatcher-caching}

Der Dispatcher wird normalerweise für Folgendes konfiguriert:

* Publish: Produktion

### CORS-Setup {#cors-setup}

>[!NOTE]
>Wenn die Caching-Funktion im [AEM-Dispatcher](#dispatcher-caching) aktiviert ist, wird das CORS-Setup nicht benötigt, sodass dieser Abschnitt ignoriert werden kann.

Um auf den GraphQL-Endpunkt zuzugreifen, muss eine CORS-Richtlinie konfiguriert und einem AEM-Projekt hinzugefügt werden, das in AEM über Cloud Manager bereitgestellt wird. Dazu wird eine entsprechende OSGi-CORS-Konfigurationsdatei für den/die gewünschten Endpunkt(e) hinzugefügt.

#### Details {#details-cors-setup}

[Konfiguration der herkunftsübergreifenden Ressourcennutzung (Cross-Origin Resource Sharing, CORS)](/help/headless/deployment/cross-origin-resource-sharing.md)

#### Umgebungen {#environments-cors-setup}

CORS wird in der Regel für Folgendes konfiguriert:

* Publish: Produktion

### Authentifizierung {#authentication}

Ein primäres Anwendungsbeispiel für die GraphQL-API von Adobe Experience Manager as a Cloud Service (AEM) für die Bereitstellung von Inhaltsfragmenten ist das Annehmen von Remote-Abfragen von Drittanbieter-Programmen oder -Services. Diese Remote-Abfragen erfordern möglicherweise einen authentifizierten API-Zugriff, um die Bereitstellung von Headless-Inhalten zu sichern.

#### Details {#details-authentication}

[Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten](/help/headless/security/authentication.md)

#### Umgebungen {#environments-authentication}

Die Authentifizierung ist normalerweise für Folgendes konfiguriert:

* Vorschau
* Publish

Für:

* Entwicklung
* Testen
* Produktion

### Berechtigungen {#permissions}

Bei einer Headless-Implementierung gibt es mehrere Bereiche von Sicherheit und Berechtigungen, die berücksichtigt werden sollten. Berechtigungen und Rollen können je nach AEM-Umgebung, **Autor** oder **Veröffentlichung**, umfassend berücksichtigt werden. Jede Umgebung enthält unterschiedliche Rollen mit unterschiedlichen Anforderungen.

#### Details {#details-permissions}

[Überlegungen zu Berechtigungen für Headless-Inhalte](/help/headless/security/permissions.md)

#### Umgebungen {#environments-permissions}

Berechtigungen werden normalerweise für Folgendes konfiguriert:

* Author
* Vorschau
* Publish

Für:

* Entwicklung
* Testen
* Produktion

### Verwenden eines Content Delivery Network (CDN) {#cdn}

GraphQL-Abfragen und ihre JSON-Antworten können im Cache gespeichert werden, wenn sie bei Verwendung eines CDN als `GET`-Anfragen anvisiert werden. Im Gegensatz dazu können nicht zwischengespeicherte Anfragen sehr teuer (ressourcenintensiv) sein und nur langsam verarbeitet werden, was weitere nachteilige Auswirkungen auf die Ursprungsressourcen bedeuten kann.

#### Details {#details-cdn}

[CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md)

#### Umgebungen {#environments-cdn}

Ein CDN ist normalerweise für Folgendes konfiguriert:

* Publish: Produktion

### Konfigurieren und Erstellen von Inhaltsfragmenten {#cconfigure-create-content-fragments}

AEM GraphQL wird zum Abrufen von Informationen aus Ihren Inhaltsfragmenten verwendet. Diese müssen nicht nur konfiguriert werden, sondern es sind auch eine Struktur und ein Speicherort zu definieren, bevor Sie den Inhalt erstellen können.

#### Details {#details-content-fragments}

* [Erstellen einer Konfiguration](/help/headless/setup/create-configuration.md)
* [Erstellen eines Inhaltsfragmentmodells](/help/headless/setup/create-content-model.md)
* [Erstellen eines Asset-Ordners](/help/headless/setup/create-assets-folder.md)
* [Erstellen und Bearbeiten von Inhaltsfragmenten](/help/headless/setup/create-content-fragment.md)

#### Umgebungen {#eenvironments-content-fragments}

Inhaltsfragmente werden in folgenden Umgebungen definiert, erstellt, getestet, veröffentlicht und abgerufen:

* Author
* Vorschau
* Publish

Für:

* Entwicklung
* Testen
* Produktion

## Verwenden von AEM GraphQL {#use-aem-graphql}

### Optimieren Ihrer GraphQL-Abfragen {#optimize-graphql-queries}

Diese Richtlinien helfen Ihnen bei der Vermeidung von Leistungsproblemen bei Ihren GraphQL-Abfragen.

#### Details {#details-optimize-graphql-queries}

[Optimieren von GraphQL-Abfragen](/help/headless/graphql-api/graphql-optimization.md)

>[!NOTE]
>
>Die Optimierungsrichtlinien betreffen die Cache-Konfiguration, die bereits unter [Setup](#setup) erläutert wurde.

### Zugriff auf GraphQL über Ihre Apps {#access-graphql-from-your-apps}

AEM Headless-CMS bietet Entwickelnden die Freiheit, außergewöhnliche Erlebnisse mithilfe von Sprachen, Frameworks und Tools zu erstellen und bereitzustellen, mit denen sie bereits vertraut sind.

#### Details {#details-your-apps}

* [AEM SDK für die Entwicklung installieren und verwenden](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html?lang=de)
* [AEM Headless-Entwicklerressourcen](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* Beispiele, darunter [React](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/react-app.html?lang=de), [Next.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/next-js.html?lang=de), [Node.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/server-to-server-app.html?lang=de)

#### Umgebungen {#environments-your-apps}

Apps werden in der Regel für Folgendes entwickelt, getestet und verwendet:

* Vorschau
* Publish

Für:

* Entwicklung
* Testen
* Produktion

### Zusätzliche Ressourcen

Weitere Informationen zu AEM GraphQL und Inhaltsfragmenten finden Sie unter:

* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)
* [Verwenden der GraphiQL-IDE](/help/headless/graphql-api/graphiql-ide.md)
* [AEM Headless-Entwicklerressourcen](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
