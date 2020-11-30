---
title: Routing SPA
description: Bei Einzelseitenanwendungen in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.
translation-type: tm+mt
source-git-commit: c075bcc415b68ba0deaeca61d6d179bd7263ca5f
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 10%

---


# Routing SPA{#spa-model-routing}

Bei Einzelseitenanwendungen in AEM ist die App für das Routing verantwortlich. In diesem Dokument werden der Routing-Mechanismus, der Vertrag und die verfügbaren Optionen beschrieben.

## Project Routing {#project-routing}

Die App ist im Besitz des Routings und wird dann von den Frontend-Entwicklern des Projekts implementiert. Dieses Dokument beschreibt das Routing, das für das vom AEM zurückgegebene Modell spezifisch ist. Die Datenstruktur des Seitenmodells stellt die URL der zugrunde liegenden Ressource dar. Das Front-End-Projekt kann eine benutzerdefinierte Bibliothek oder eine Bibliothek eines Drittanbieters verwenden, die Routing-Funktionen bereitstellt. Sobald eine Route ein Fragment des Modells erwartet, kann ein Aufruf an die `PageModelManager.getData()` Funktion durchgeführt werden. Wenn eine Modellroute geändert wurde, muss ein Ereignis ausgelöst werden, um Listening-Bibliotheken wie den Seiten-Editor zu warnen.

## Architektur {#architecture}

Eine ausführliche Beschreibung finden Sie im Abschnitt [PageModelManager](blueprint.md#pagemodelmanager) im Dokument SPA Blueprint.

## ModelRouter {#modelrouter}

Die `ModelRouter` - sofern aktiviert - kapselt die HTML5-Verlauf-API-Funktionen `pushState` und `replaceState` gewährleistet, dass ein bestimmtes Modellfragment vorab abgerufen und verfügbar ist. Anschließend benachrichtigt er die registrierte Front-End-Komponente, dass das Modell geändert wurde.

## Manuelles oder automatisches Routing {#manual-vs-automatic-model-routing}

Das `ModelRouter` automatisiert das Abrufen von Fragmenten des Modells. Aber wie jedes automatisierte Werkzeug kommt es mit Einschränkungen. Bei Bedarf `ModelRouter` kann das Element deaktiviert oder so konfiguriert werden, dass Pfade mithilfe von Metaeigenschaften ignoriert werden (siehe Abschnitt &quot;Metaeigenschaften&quot;im Dokument [SPA Seitenkomponenten](page-component.md) ). Front-End-Entwickler können dann ihre eigene Modellebene implementieren, indem sie die `PageModelManager` zum Laden eines bestimmten Modellfragments mithilfe der `getData()` Funktion auffordern.

>[!CAUTION]
>
>Die aktuelle Version von `ModelRouter` unterstützt nur eine Verwendung von URLs, die auf den tatsächlichen Ressourcenpfad von Sling Model-Einstiegspunkten verweisen. Die Verwendung von Vanity-URLs oder Aliasnamen wird nicht unterstützt.

## Routing-Vertrag {#routing-contract}

Die aktuelle Implementierung basiert auf der Annahme, dass das SPA Projekt die HTML5-Verlauf-API zum Routing der verschiedenen Anwendungsseiten verwendet.

### Konfiguration {#configuration}

Das `ModelRouter` unterstützt das Modellkonzept, da es auf Modellfragmente wartet `pushState` und diese `replaceState` aufruft. Intern löst es das Laden des Modells aus, das einer bestimmten URL entspricht, und löst ein `PageModelManager` `cq-pagemodel-route-changed` Ereignis aus, auf das andere Module hören können.

Standardmäßig ist dieses Verhalten automatisch aktiviert. Um es zu deaktivieren, sollte die SPA die folgende Meta-Eigenschaft rendern:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Note that every route of the SPA should correspond to an accessible resource in AEM (e.g., &quot; `/content/mysite/mypage"`) since the `PageModelManager` will automatically try to load the corresponding page model once the route is selected. Though, if needed, the SPA can also define a &quot;block list&quot; of routes that should be ignored by the `PageModelManager`:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
