---
title: Die RemotePage-Komponente
description: Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente zur Bearbeitung von Remote-React-SPAs in AEM.
exl-id: d3465592-0392-49b0-b49d-de93983c1d6e
translation-type: tm+mt
source-git-commit: eaa59b6ecfa50c4a6b4e316e5e305e48cb3d5676
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 55%

---

# Die RemotePage-Komponente {#remote-page-component}

Wenn Sie entscheiden, [welchen Grad der Integration](/help/implementing/developing/headful-headless.md) Sie zwischen Ihrer externen SPA und AEM haben möchten, wird oft klar, dass Sie die SPA in AEM anzeigen und bearbeiten können müssen. Die RemotePage-Komponente ist eine benutzerdefinierte Seitenkomponente genau für diesen Zweck.

## Überblick {#overview}

Die RemotePage-Komponente ruft alle erforderlichen Assets aus dem generierten `asset-manifest.json` des Programms ab und verwendet diese zum Rendern der SPA in AEM.

* Mit RemotePage können Sie die Skripte und Stylesheets eines SPA im Textkörper einer AEM Seitenkomponente einfügen.
* Die Virtual Frontend-Komponenten ermöglichen es, Abschnitte im AEM SPA Editor als bearbeitbar zu markieren.
* Gemeinsam kann eine SPA, die auf einer anderen Domäne gehostet wird, in AEM editierbar gemacht werden.

Weitere Informationen zu bearbeitbaren, externen SPA in AEM finden Sie im Artikel [Bearbeiten eines externen SPA innerhalb AEM](editing-external-spa.md).

## Voraussetzungen {#requirements}

* CORS in der Entwicklung aktivieren
* Remote-URL in den Seiteneigenschaften konfigurieren
* SPA in AEM rendern
* Die Webanwendung muss ein Bundler-Asset-Manifest wie eine der folgenden verwenden und eine `asset-manifest.json`-Datei im Domänenstamm bereitstellen, die in einer `entrypoints property`-Liste aller zu ladenden CSS- und JS-Dateien  wird:
   * https://github.com/shellscape/webpack-manifest-plugin
   * https://github.com/webdeveric/webpack-assets-manifest
   * https://github.com/mugi-uno/parcel-plugin-bundle-manifest
      ![Beispiel für Einstiegspunkte-Eigenschaft](assets/asset-manifest-entrypoints.png)
* Die Anwendung muss in der Lage sein, unter dem `body`-Element in einem `<div id="root"></div>` zu initialisieren. Wenn ein anderes Markup erwartet wird, damit die App instanziiert wird, muss dies in den HTML-Skripten der Proxykomponente mit einem `sling:resourceSuperType="spa-project-core/components/remotepage` entsprechend angepasst werden.

## Beschränkungen {#limitations}

* Die aktuelle Implementierung der RemotePage-Komponente unterstützt nur Remote React-Programme.
* Internes CSS, das in der Stamm-HTML-Datei des Programms definiert ist, sowie Inline-CSS im Stamm-DOM-Knoten sind beim Remote-Rendering in AEM nicht verfügbar.

## Technische Details {#technical-details}

Wie der Rest des AEM-SPA-Projekts ist die RemotePage-Komponente eine Open Source-Komponente. Die vollständigen technischen Details der RemotePage-Komponente [finden Sie im GitHub-Repository.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
