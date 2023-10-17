---
title: Dispatcher-Endpunktkonfiguration mit AEM Headless
description: Der Dispatcher ist eine Caching- und Sicherheitsebene vor den Adobe Experience Manager-Veröffentlichungsumgebungen. Es werden verschiedene Konfigurationen verwendet, um GraphQL-Endpunkte für Headless-Anwendungen zu öffnen.
feature: Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
source-git-commit: 316680823fe4bc85e1f4359305047c0d1f517dc7
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 94%

---


# Dispatcher - Endpunktkonfiguration mit AEM Headless

Der [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) ist eine Caching- und Sicherheitsebene vor den Adobe Experience Manager-Veröffentlichungsumgebungen. Standardmäßig sind mehrere Konfigurationen enthalten, um GraphQL-Endpunkte für Headless-Anwendungen zu öffnen.

>[!NOTE]
>
>Eine ausführliche Dokumentation zum Dispatcher finden Sie im [Handbuch zum Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de).

Im Rahmen eines AEM-Projekts ist ein Dispatcher-Modul enthalten, das Konfigurationen für den Dispatcher enthält. Neu erstellte Projekte aus dem [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) schließen automatisch [Filter](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#defining-a-filter) ein, die GraphQL-Endpunkte aktivieren.

## GraphQL-Endpunkte

Als Teil der Standardfilter werden [GraphQL-Endpunkte](/help/headless/graphql-api/graphql-endpoint.md) mit der folgenden Regel geöffnet:

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Der `*`-Platzhalter öffnet mehrere Endpunkte in der AEM-Instanz. Die Abfrage mit einem GraphQL-Endpunkt erfolgt über `POST`, wobei die Antwort **nicht** zwischengespeichert wird.

## GraphQL – Persistierte Abfragen

Die Anfrage für persistierte Abfragen erfolgt an einem anderen Endpunkt. Im Rahmen der Standardfilterkonfiguration werden die URLs für [Persistierte Abfragen](/help/headless/graphql-api/persisted-queries.md) mit der folgenden Regel geöffnet:

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

Persistierte Abfragen können mit `GET` angefragt werden, indem die Antwort auf Dispatcher- und CDN-Ebene zwischengespeichert wird. Weitere Informationen zur Zwischenspeicherung und Cache-Invalidierung finden Sie [hier](/help/implementing/dispatcher/caching.md).
