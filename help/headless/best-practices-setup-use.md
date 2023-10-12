---
title: Best Practices für die Einrichtung und Verwendung von AEM GraphQL mit Inhaltsfragmenten
description: Erfahren Sie mehr über die empfohlenen Best Practices für die Einrichtung und Verwendung von AEM GraphQL mit Inhaltsfragmenten.
source-git-commit: 9a544fb9d2494862efdb2263f3b9b61214c4b8b9
workflow-type: tm+mt
source-wordcount: '737'
ht-degree: 29%

---


# Best Practices für die Einrichtung und Verwendung von AEM GraphQL mit Inhaltsfragmenten{#best-practices-setup-use-aem-graphql-content-fragments}

Diese Richtlinien fassen die empfohlenen Best Practices für die Einrichtung, Konfiguration und Verwendung von AEM mit GraphQL und Inhaltsfragmenten zusammen.

## Erste Schritte {#getting-started}

So machen Sie sich schneller:

* [Was ist Headless?](/help/headless/what-is-headless.md)
* Überblick über die verschiedenen Umgebungen in der AEM [Architektur](/help/headless/deployment/architecture.md)

## Einrichtung {#setup}

Um AEM GraphQL für die Verwendung mit Inhaltsfragmenten und Apps sicher einzurichten, müssen Sie verschiedene Komponenten konfigurieren.

### Erstellung von GraphQL-Endpunkten (einschließlich Sicherheit) {#graphql-endpoint-creation}

Der Endpunkt ist der Pfad, der für den Zugriff auf GraphQL für AEM verwendet wird. Diese Endpunkte müssen erstellt und veröffentlicht werden, damit sie sicher aufgerufen werden können.

#### Details {#details-graphql-endpoint-creation}

[Verwalten von GraphQL-Endpunkten in AEM](/help/headless/graphql-api/graphql-endpoint.md)

#### Umgebungen {#environments-graphql-endpoint-creation}

Endpunkte müssen konfiguriert werden in:

* Autor
* Vorschau
* Veröffentlichen 

Für:

* Entwicklung
* Testen
* Produktion

### AEM Dispatcher-Caching {#dispatcher-caching}

>[!NOTE]
>Wenn die Zwischenspeicherung im Dispatcher aktiviert ist, wird die [CORS-Einrichtung](#cors-setup) ist nicht erforderlich und kann daher ignoriert werden.

Die Zwischenspeicherung persistenter Abfragen ist im Dispatcher standardmäßig nicht aktiviert. Die Standardumaktivierung ist nicht möglich, da Kunden, die CORS (Cross-Origin Resource Sharing) mit mehreren Ursprüngen verwenden, ihre Dispatcher-Konfiguration überprüfen und möglicherweise aktualisieren müssen.

#### Details {#details-dispatcher-caching}

[Persistente GraphQL-Abfragen - Aktivierung der Zwischenspeicherung im Dispatcher](/help/headless/deployment/dispatcher-caching.md)

#### Umgebungen {#environments-dispatcher-caching}

Der Dispatcher ist normalerweise für Folgendes konfiguriert:

* Veröffentlichung: Produktion

### CORS-Einrichtung {#cors-setup}

>[!NOTE]
>Wenn die Zwischenspeicherung im [AEM Dispatcher](#dispatcher-caching) aktiviert ist, ist das CORS-Setup nicht erforderlich. Daher kann dieser Abschnitt ignoriert werden.

Um auf den GraphQL-Endpunkt zuzugreifen, muss eine CORS-Richtlinie konfiguriert und einem AEM-Projekt hinzugefügt werden, das in AEM über Cloud Manager bereitgestellt wird. Dazu wird eine entsprechende OSGi-CORS-Konfigurationsdatei für den/die gewünschten Endpunkt(e) hinzugefügt.

#### Details {#details-cors-setup}

[Konfiguration der herkunftsübergreifenden Ressourcennutzung (Cross-Origin Resource Sharing, CORS)](/help/headless/deployment/cross-origin-resource-sharing.md)

#### Umgebungen {#environments-cors-setup}

CORS ist in der Regel für Folgendes konfiguriert:

* Veröffentlichung: Produktion

### Authentifizierung {#authentication}

Ein Hauptanwendungsfall für die Adobe Experience Manager as a Cloud Service (AEM) GraphQL API für die Bereitstellung von Inhaltsfragmenten besteht darin, Remote-Abfragen von Drittanbieteranwendungen oder -diensten zu akzeptieren. Für diese Remote-Abfragen ist möglicherweise ein authentifizierter API-Zugriff erforderlich, um eine sichere, Headless-Content-Bereitstellung zu gewährleisten.

#### Details {#details-authentication}

[Authentifizierung für AEM-GraphQL-Remote-Abfragen in Inhaltsfragmenten](/help/headless/security/authentication.md)

#### Umgebungen {#environments-authentication}

Die Authentifizierung ist normalerweise für Folgendes konfiguriert:

* Vorschau
* Veröffentlichen 

Für:

* Entwicklung
* Testen
* Produktion

### Berechtigungen {#permissions}

Bei einer Headless-Implementierung gibt es mehrere Bereiche von Sicherheit und Berechtigungen, die berücksichtigt werden sollten. Berechtigungen und Rollen können je nach AEM-Umgebung, **Autor** oder **Veröffentlichung**, umfassend berücksichtigt werden. Jede Umgebung enthält unterschiedliche Rollen mit unterschiedlichen Anforderungen.

#### Details {#details-permissions}

[Überlegungen zu Berechtigungen für Headless-Inhalte](/help/headless/security/permissions.md)

#### Umgebungen {#environments-permissions}

Berechtigungen werden in der Regel für Folgendes konfiguriert:

* Autor
* Vorschau
* Veröffentlichen 

Für:

* Entwicklung
* Testen
* Produktion

### Verwenden eines Content Delivery Network (CDN) {#cdn}

GraphQL-Abfragen und ihre JSON-Antworten können zwischengespeichert werden, wenn sie als Ziel ausgewählt werden. `GET` Anfragen bei Verwendung eines CDN. Im Gegensatz dazu können nicht zwischengespeicherte Anfragen sehr (ressourcenintensiv) teuer und langsam verarbeitet werden, was weitere nachteilige Auswirkungen auf die Ressourcen des Ursprungs haben kann.

#### Details {#details-cdn}

[CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md)

#### Umgebungen {#environments-cdn}

Ein CDN ist in der Regel für Folgendes konfiguriert:

* Veröffentlichung: Produktion

### Konfigurieren und Erstellen von Inhaltsfragmenten {#cconfigure-create-content-fragments}

AEM GraphQL wird zum Abrufen von Informationen aus Ihren Inhaltsfragmenten verwendet. Diese müssen konfiguriert und dann eine Struktur und ein Ort definiert werden, bevor Sie den Inhalt erstellen können.

#### Details {#details-content-fragments}

* [Erstellen einer Konfiguration](/help/headless/setup/create-configuration.md)
* [Erstellen eines Inhaltsfragmentmodells](/help/headless/setup/create-content-model.md)
* [Erstellen eines Asset-Ordners](/help/headless/setup/create-assets-folder.md)
* [Erstellen und Bearbeiten von Inhaltsfragmenten](/help/headless/setup/create-content-fragment.md)

#### Umgebungen {#eenvironments-content-fragments}

Inhaltsfragmente werden definiert, erstellt, getestet, veröffentlicht und für folgende Zwecke aufgerufen:

* Autor
* Vorschau
* Veröffentlichen 

Für:

* Entwicklung
* Testen
* Produktion

## Verwenden von AEM GraphQL {#use-aem-graphql}

### GraphQL-Abfragen optimieren {#optimize-graphql-queries}

Diese Richtlinien helfen Ihnen bei der Vermeidung von Leistungsproblemen bei Ihren GraphQL-Abfragen.

#### Details {#details-optimize-graphql-queries}

[Optimieren von GraphQL-Abfragen](/help/headless/graphql-api/graphql-optimization.md)

>[!NOTE]
>
>Die Optimierungsrichtlinien betreffen die Cache-Konfiguration, die bereits unter [Einrichtung](#setup).

### Zugriff auf GraphQL über Ihre Apps {#access-graphql-from-your-apps}

AEM Headless-CMS gibt Entwicklern die Freiheit, außergewöhnliche Erlebnisse mithilfe von Sprachen, Frameworks und Tools zu erstellen und bereitzustellen, mit denen sie bereits vertraut sind.

#### Details {#details-your-apps}

* [Installieren und Verwenden des AEM SDK für die Entwicklung](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html?lang=de)
* [AEM Headless-Entwicklerressourcen](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* Beispiele, darunter [React](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/react-app.html), [Next.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/next-js.html), [Node.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/server-to-server-app.html), darunter

#### Umgebungen {#environments-your-apps}

Apps werden in der Regel entwickelt, getestet und für folgende Zwecke verwendet:

* Vorschau
* Veröffentlichen 

Für:

* Entwicklung
* Testen
* Produktion

### Weitere Ressourcen

Weitere Informationen zu AEM GraphQL und Inhaltsfragmenten finden Sie unter:

* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)
* [Verwenden der GraphiQL-IDE](/help/headless/graphql-api/graphiql-ide.md)
* [AEM Headless-Entwicklerressourcen](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
