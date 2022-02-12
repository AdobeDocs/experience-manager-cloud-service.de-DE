---
title: Dispatcher-Konfiguration mit AEM Headless
description: Der Dispatcher ist eine Caching- und Sicherheitsschicht vor Adobe Experience Manager-Veröffentlichungsumgebungen. Es werden verschiedene Konfigurationen verwendet, um GraphQL-Endpunkte für Headless-Anwendungen zu öffnen.
feature: Dispatcher, GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 6%

---


# Dispatcher-Konfiguration mit AEM Headless

Die [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) ist eine Caching- und Sicherheitsschicht vor Adobe Experience Manager-Veröffentlichungsumgebungen. Standardmäßig sind mehrere Konfigurationen enthalten, um GraphQL-Endpunkte für Headless-Anwendungen zu öffnen.

>[!NOTE]
>
>Eine ausführliche Dokumentation zum Dispatcher finden Sie unter [Dispatcher-Anleitung](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)

Im Rahmen eines AEM-Projekts ist ein Dispatcher-Modul enthalten, das Konfigurationen für den Dispatcher enthält. Neu erstellte Projekte aus dem [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype) automatisch eingeschlossen [Filter](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?#defining-a-filter) , das GraphQL-Endpunkte aktiviert.

## GraphQL-Endpunkt(e)

Als Teil der Standardfilter [GraphQL-Endpunkte](/help/headless/graphql-api/graphql-endpoint.md) werden mit der folgenden Regel geöffnet:

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Die `*` -Platzhalter öffnet mehrere Endpunkte in der AEM-Instanz. Die Abfrage mit einem GraphQL-Endpunkt erfolgt über `POST` und die Antwort **not** zwischengespeichert werden.

## GraphQL - Beständige Abfragen

Die Anfrage für persistente Abfragen erfolgt an einem anderen Endpunkt. Im Rahmen der Standardfilterkonfiguration muss die URL für [Beständige Abfragen](/help/headless/graphql-api/persisted-queries.md) werden mit der folgenden Regel geöffnet:

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

Persistente Abfragen können mit `GET`, wodurch die Antwort auf Dispatcher- und CDN-Ebene zwischengespeichert wird. Weitere Informationen zur Zwischenspeicherung und Cache-Invalidierung finden Sie unter [here](/help/implementing/dispatcher/caching.md).
