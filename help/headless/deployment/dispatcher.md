---
title: Dispatcher-Konfiguration mit AEM Headless
description: Der Dispatcher ist eine Caching- und Sicherheitsebene vor den Adobe Experience Manager-Veröffentlichungsumgebungen. Es werden verschiedene Konfigurationen verwendet, um GraphQL-Endpunkte für Headless-Anwendungen zu öffnen.
feature: Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 56%

---

# Dispatcher-Konfiguration mit AEM Headless

Der [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) ist eine Caching- und Sicherheitsebene vor den Adobe Experience Manager-Veröffentlichungsumgebungen. Standardmäßig sind mehrere Konfigurationen enthalten, um GraphQL-Endpunkte für Headless-Anwendungen zu öffnen.

>[!NOTE]
>
>Eine ausführliche Dokumentation zum Dispatcher finden Sie in der [Dispatcher-Anleitung](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de).

Im Rahmen eines AEM-Projekts ist ein Dispatcher-Modul enthalten, das Konfigurationen für den Dispatcher enthält. Neu erstellte Projekte aus dem [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype) automatisch einschließen [Filter](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#defining-a-filter) , die GraphQL-Endpunkte aktivieren.

## GraphQL-Endpunkte

Als Teil der Standardfilter werden [GraphQL-Endpunkte](/help/headless/graphql-api/graphql-endpoint.md) mit der folgenden Regel geöffnet:

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Der `*`-Platzhalter öffnet mehrere Endpunkte in der AEM-Instanz. Die Abfrage mit einem GraphQL-Endpunkt erfolgt über `POST` und die Antwort lautet **not** zwischengespeichert.

## GraphQL – Persistierte Abfragen

Die Anfrage für beständige Abfragen erfolgt an einem anderen Endpunkt. Im Rahmen der Standardfilterkonfiguration muss die URL für [Beständige Abfragen](/help/headless/graphql-api/persisted-queries.md) wird mit der folgenden Regel geöffnet:

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

Beständige Abfragen können mit `GET`, indem Sie die Antwort auf Dispatcher- und CDN-Ebene zwischenspeichern. Weitere Informationen zur Zwischenspeicherung und Cache-Invalidierung finden Sie [hier](/help/implementing/dispatcher/caching.md).
