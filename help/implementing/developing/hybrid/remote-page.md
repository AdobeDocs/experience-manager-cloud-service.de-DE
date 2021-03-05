---
title: Die RemotePage-Komponente
description: Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente zur Bearbeitung von Remote-React-SPA in AEM.
translation-type: tm+mt
source-git-commit: 9a1048f6d185d2d3229bab05b8e827845444d11c
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---

# Die RemotePage-Komponente {#remote-page-component}

Bei der Entscheidung darüber, welche Integrationsstufe](/help/implementing/developing/headful-headless.md) Sie zwischen Ihren externen SPA und AEM haben möchten, ist häufig klar, dass Sie in der Lage sein müssen, die SPA innerhalb AEM zu bearbeiten. [ Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente, die nur zu diesem Zweck verwendet wird.

## Überblick {#overview}

Die RemotePage-Komponente ruft alle erforderlichen Elemente aus dem generierten Element `asset-manifest.json` der Anwendung ab und verwendet diese zum Rendern des SPA in AEM.

* Mit RemotePage können Sie die Skripte und Stylesheets eines SPA im Textkörper einer AEM Seitenkomponente einfügen.
* Die Virtual Frontend-Komponenten ermöglichen es, Abschnitte im AEM SPA Editor als bearbeitbar zu markieren.
* Gemeinsam kann eine SPA, die auf einer anderen Domäne gehostet wird, in AEM editierbar gemacht werden.

Weitere Informationen zu bearbeitbaren, externen SPA in AEM finden Sie im Artikel [Bearbeiten eines externen SPA innerhalb AEM](editing-external-spa.md).

## Voraussetzungen {#requirements}

* Aktivieren von CORS in der Entwicklung
* Remote-URL in Seiteneigenschaften konfigurieren
* SPA in AEM wiedergeben

## Beschränkungen {#limitations}

* Die aktuelle Implementierung der RemotePage-Komponente unterstützt nur Remote React-Anwendungen.
* Internes CSS, das in der Stamm-HTML-Datei der Anwendung definiert ist, sowie Inline-CSS auf dem Stamm-DOM-Knoten sind beim Remote-Rendering in AEM nicht verfügbar.

## Technische Details {#technical-details}

Wie der Rest des AEM SPA ist die RemotePage-Komponente eine Open Source-Komponente. Die vollständigen technischen Details der RemotePage-Komponente finden Sie im GitHub-Repository.[](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
