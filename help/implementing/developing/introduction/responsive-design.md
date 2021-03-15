---
title: Responsives Design
description: Responsives Design ermöglicht die effektive Darstellung derselben Erlebnisse auf verschiedenen Geräten in verschiedenen Ausrichtungen.
translation-type: tm+mt
source-git-commit: a3b2a66958fd8d3a68b450938c5c18053f00b998
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 100%

---


# Responsives Design {#responsive-design}

Gestalten Sie Ihre Erlebnisse so, dass sie sich dem Client-Darstellungsfeld anpassen, auf dem sie angezeigt werden. Responsives Design ermöglicht die effektive Darstellung derselben Web-Seiten auf verschiedenen Geräten in beiden Ausrichtungen. Die folgende Grafik zeigt eine Reihe von Möglichkeiten, wie eine Seite auf Änderungen der Fenstergröße reagieren kann:

* Layout: Verwenden Sie einspaltige Layouts für kleinere Fenstergrößen und mehrspaltige Layouts für größere Fenstergrößen.
* Textgröße: Verwenden Sie für größere Fenstergrößen größere Schriftgrößen (wo passend, z. B. Überschriften).
* Inhalt: Zeigen Sie auf kleineren Geräten nur die wichtigsten Inhalte an.
* Navigation: Gerätespezifische Tools werden für den Zugriff auf andere Seiten zur Verfügung gestellt.
* Bilder: Stellen Sie anhand der Fenstergröße dem Client-Darstellungsfeld entsprechende Ausgabedarstellungen zur Verfügung.

![Beispiele für responsives Design](assets/responsive-example.png)

Entwickeln Sie Adobe Experience Manager (AEM)-Programme, die HTML5-Inhalte generieren, die sich an verschiedene Fenstergrößen und Ausrichtungen anpassen. Beispielsweise entsprechen die folgenden Darstellungsfeldbreiten unterschiedlichen Gerätetypen und Ausrichtungen:

* Maximale Breite von 480 Pixel (Smartphone, Hochformat)
* Maximale Breite von 767 Pixel (Smartphone, Querformat)
* Breite zwischen 768 Pixel und 979 Pixel (Tablet, Hochformat)
* Breite zwischen 980 Pixel und 1199 Pixel (Tablet, Querformat)
* Breite von 1200 Pixel oder mehr (Desktop)

Weitere Informationen finden Sie unter den folgenden Themen zur Implementierung von responsivem Design:

* [Medienabfragen](#using-media-queries)
* [Fließende Raster](#developing-a-fluid-grid)
* [Adaptive Bilder](#using-adaptive-images)

Nutzen Sie während des Design-Vorgangs die **Emulator**-Symbolleiste, um Vorschauen Ihrer Seiten in verschiedenen Bildschirmgrößen anzuzeigen.

## Vor dem Entwicklungsvorgang {#before-you-develop}

Vor der Entwicklung eines AEM-Programms, das Ihre Web-Seiten unterstützt, müssen Sie einige Design-Entscheidungen treffen. Beispielsweise benötigen Sie die folgenden Informationen:

* Auf welche Geräte der Entwicklungsprozess ausgerichtet ist
* Die Größe der Zieldarstellungsfelder
* Die Seiten-Layouts für die berücksichtigten Zieldarstellungsfelder

### Programmstruktur {#application-structure}

Die typische AEM-Programmstruktur unterstützt alle Implementierungen responsiven Designs:

* Seitenkomponenten befinden sich unter `/apps/<application_name>/components`
* Vorlagen befinden sich unter `/apps/<application_name>/templates`

## Nutzung von Medienabfragen {#using-media-queries}

Medienabfragen ermöglichen die selektive Nutzung von CSS-Stilen für das Seiten-Rendering. AEM-Entwicklungs-Tools und -funktionen ermöglichen Ihnen die effektive und effiziente Implementierung von Medienabfragen in Programmen.

Die W3C-Gruppe stellt die [Medienabfragen](https://www.w3.org/TR/css3-mediaqueries/)-Empfehlung zur Verfügung, die diese CSS3-Funktion und die Syntax beschreibt.

### Erstellen der CSS-Datei {#creating-the-css-file}

Definieren Sie in der CSS-Datei Medienabfragen anhand der Eigenschaften der Zielgeräte. Die folgende Implementierungsstrategie kann für die Verwaltung der Stile der verschiedenen Medienabfragen verwendet werden:

* Verwenden Sie einen [Client-Bibliotheksordner](clientlibs.md), um das CSS zu definieren, das zusammengestellt wird, wenn die Seite gerendert wird.
* Definieren Sie die Medienabfragen und die zugehörigen Stile in separaten CSS-Dateien. Dabei ist es hilfreich, Dateinamen zu verwenden, die die Geräteeigenschaften der Medienabfrage darstellen.
* Definieren Sie Stile, die alle Geräte gemeinsam haben, in einer separaten CSS-Datei.
* Sortieren Sie in der Datei „css.txt“ des Client-Bibliotheksordners die Liste der CSS-Dateien, wie es in der zusammengestellten CSS-Datei erforderlich ist.

Das [WKND-Tutorial](develop-wknd-tutorial.md) verwendet diese Strategie zur Definition von Stilen beim Website-Design. Die von WKND verwendete CSS-Datei befindet sich unter `/apps/wknd/clientlibs/clientlib-grid/less/grid.less`.
