---
title: Responsives Design
description: Responsives Design ermöglicht die effektive Darstellung derselben Erlebnisse auf verschiedenen Geräten in verschiedenen Ausrichtungen.
exl-id: be645062-d6d6-45a2-97dc-d8aa235539b8
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 97%

---

# Responsives Design {#responsive-design}

Gestalten Sie Ihre Erlebnisse so, dass sie sich dem Client-Darstellungsfeld anpassen, auf dem sie angezeigt werden. Responsives Design ermöglicht die effektive Darstellung derselben Web-Seiten auf verschiedenen Geräten in beiden Ausrichtungen. Die folgende Abbildung zeigt einige Möglichkeiten, wie eine Seite auf Größenänderungen des Darstellungsfelds reagieren kann:

* Layout: Verwenden Sie einspaltige Layouts für kleinere Darstellungsfelder und mehrspaltige Layouts für größere Darstellungsfelder.
* Textgröße: Verwenden Sie in größeren Darstellungsfeldern eine größere Textgröße (wo passend, z. B. Überschriften).
* Inhalt: Schließen Sie bei der Anzeige auf kleineren Geräten nur die wichtigsten Inhalte ein.
* Navigation: Für den Zugriff auf andere Seiten werden gerätespezifische Tools bereitgestellt.
* Bilder: Stellen Sie anhand der Fenstergröße dem Client-Darstellungsfeld entsprechende Ausgabedarstellungen zur Verfügung.

![Beispiele für responsives Design](assets/responsive-example.png)

Entwickeln Sie Adobe Experience Manager (AEM)-Programme, die HTML5-Inhalte generieren, die sich an verschiedene Fenstergrößen und Ausrichtungen anpassen. Beispielsweise entsprechen die folgenden Breiten von Darstellungsfeldern verschiedenen Gerätetypen und -ausrichtungen.

* Maximale Breite von 480 Pixeln (Smartphone, Hochformat)
* Maximale Breite von 767 Pixeln (Smartphone, Querformat)
* Breite zwischen 768 Pixeln und 979 Pixeln (Tablet, Hochformat)
* Breite zwischen 980 Pixel und 1199 Pixel (Tablet, Querformat)
* Breite von 1200 Pixel oder mehr (Desktop)

Weitere Informationen finden Sie unter den folgenden Themen zur Implementierung von responsivem Design:

* [Medienabfragen](#using-media-queries)
* [Fließende Raster](#developing-a-fluid-grid)
* [Adaptive Bilder](#using-adaptive-images)

Nutzen Sie während des Design-Vorgangs die **Emulator**-Symbolleiste, um Vorschauen Ihrer Seiten in verschiedenen Bildschirmgrößen anzuzeigen.

## Vor dem Entwicklungsvorgang  {#before-you-develop}

Vor der Entwicklung eines AEM-Programms, das Ihre Web-Seiten unterstützt, müssen Sie einige Design-Entscheidungen treffen. Sie müssen beispielsweise über die folgenden Informationen verfügen:

* Auf welche Geräte der Entwicklungsprozess ausgerichtet ist
* Die Größe der Zieldarstellungsfelder
* Die Seiten-Layouts für die berücksichtigten Zieldarstellungsfelder

### Anwendungsstruktur {#application-structure}

Die typische AEM-Programmstruktur unterstützt alle Implementierungen responsiven Designs:

* Seitenkomponenten befinden sich unter `/apps/<application_name>/components`
* Vorlagen befinden sich unter `/apps/<application_name>/templates`

## Nutzung von Medienabfragen  {#using-media-queries}

Medienabfragen ermöglichen die selektive Verwendung von CSS-Stilen für das Rendern von Seiten. AEM-Entwicklungs-Tools und -funktionen ermöglichen Ihnen die effektive und effiziente Implementierung von Medienabfragen in Programmen.

Die W3C-Gruppe stellt die [Medienabfragen](https://www.w3.org/TR/css3-mediaqueries/)-Empfehlung zur Verfügung, die diese CSS3-Funktion und die Syntax beschreibt.

### Erstellen der CSS-Datei {#creating-the-css-file}

Definieren Sie in der CSS-Datei Medienabfragen anhand der Eigenschaften der Zielgeräte. Die folgende Implementierungsstrategie kann für die Verwaltung der Stile der verschiedenen Medienabfragen verwendet werden:

* Verwenden Sie einen [Client-Bibliotheksordner](clientlibs.md), um das CSS zu definieren, das zusammengestellt wird, wenn die Seite gerendert wird.
* Definieren Sie die Medienabfragen und die zugehörigen Stile in separaten CSS-Dateien. Es ist nützlich, Dateinamen zu verwenden, die die Geräteeigenschaften der Medienabfrage darstellen.
* Definieren Sie Stile, die alle Geräte gemeinsam haben, in einer separaten CSS-Datei.
* Sortieren Sie in der Datei „css.txt“ des Client-Bibliotheksordners die Liste der CSS-Dateien, wie es in der zusammengestellten CSS-Datei erforderlich ist.

Das [WKND-Tutorial](develop-wknd-tutorial.md) verwendet diese Strategie zur Definition von Stilen beim Website-Design. Die von WKND verwendete CSS-Datei befindet sich unter `/apps/wknd/clientlibs/clientlib-grid/less/grid.less`.

### Verwenden von Medienabfragen bei AEM-Seiten {#using-media-queries-with-aem-pages}

[Das WKND-Beispielprojekt](/help/implementing/developing/introduction/develop-wknd-tutorial.md) und der [AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)Projektarchetyp verwenden die [Seitenkernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/page.html?lang=de), die die Clientlibs über die Seitenrichtlinie enthält.

Wenn Ihre eigene Seitenkomponente nicht auf der Seitenkernkomponente basiert, können Sie auch den Client-Bibliotheksordner in das HTL- oder JSP-Skript einschließen. Dadurch wird die CSS-Datei mit den Medienabfragen generiert und referenziert, die für die Funktion des responsiven Rasters erforderlich sind.

#### HTL {#htl}

```html
<sly data-sly-use.clientlib="${'/libs/granite/sightly/templates/clientlib.html'}">
<sly data-sly-call="${clientlib.all @ categories='apps.weretail.all'}"/>
```

#### JSP {#jsp}

```xml
<ui:includeClientLib categories="apps.weretail.all"/>
```

Das JSP-Skript generiert den folgenden HTML-Code, der auf die Stylesheets verweist:

```xml
<link rel="stylesheet" href="/etc/designs/weretail/clientlibs-all.css" type="text/css">
<link href="/etc/designs/weretail.css" rel="stylesheet" type="text/css">
```

## Anzeigen der Vorschau für bestimmte Geräte {#previewing-for-specific-devices}

Mit dem Emulator können Sie eine Vorschau Ihrer Seiten in verschiedenen Viewport-Größen anzeigen, um das Verhalten Ihres responsiven Designs zu testen. Wenn Sie eine Seite in der Sites-Konsole bearbeiten, können Sie auf das Symbol **Emulator** tippen oder klicken, um den Emulator zu öffnen.

![Das Emulator-Symbol in der Symbolleiste](assets/emulator-icon.png)

In der Symbolleiste des Emulators können Sie auf das Symbol **Geräte** tippen oder klicken, um ein Dropdown-Menü aufzurufen, in dem Sie ein Gerät auswählen können. Wenn Sie ein Gerät auswählen, passt sich die Seite der jeweiligen Darstellungsfeldgröße an.

![Die Emulator-Symbolleiste](assets/emulator.png)

### Festlegen von Gerätegruppen {#specifying-device-groups}

Um die Gerätegruppen festzulegen, die in der Liste **Geräte** erscheinen sollen, fügen Sie dem Knoten `jcr:content` der Vorlagenseite Ihrer Site eine `cq:deviceGroups`-Eigenschaft hinzu. Der Wert der Eigenschaft ist ein Array von Pfaden zu den Gerätegruppenknoten.

Die Vorlagenseite der WKND-Website ist zum Beispiel `/conf/wknd/settings/wcm/template-types/empty-page/structure`. Und der darunter liegende `jcr:content`-Knoten enthält die folgenden Eigenschaften:

* Name: `cq:deviceGroups`
* Typ: `String[]`
* Wert: `mobile/groups/responsive`

Gerätegruppenknoten befinden sich im Ordner `/etc/mobile/groups`.

## Responsive Bilder {#responsive-images}

Responsive Seiten passen sich dynamisch an das Gerät an, auf dem sie gerendert werden, und bieten dadurch den Benutzenden ein besseres Erlebnis. Es ist jedoch auch wichtig, dass Assets auf den Breakpoint und das Gerät optimiert werden, um die Seitenladezeit zu minimieren.

[Die Kernkomponenten-Bildkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html?lang=de) bietet Funktionen wie die adaptive Bildauswahl.

* Standardmäßig verwendet die Bildkomponente das [Adaptive Bild-Servlet](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/adaptive-image-servlet.html?lang=de), um die richtige Wiedergabe zu liefern.
* [Web-optimierte Bildbereitstellung](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html?lang=de) ist auch über ein einfaches Kontrollkästchen in der Richtlinie verfügbar, das Bild-Assets aus dem DAM im WebP-Format bereitstellt und die Download-Größe eines Bildes im Durchschnitt um ca. 25 % reduzieren kann.

## Der Layout-Container {#layout-container}

Mit dem Layout-Container von AEM können Sie ein responsives Layout effizient und effektiv implementieren, um die Seitendimensionen an den Client-Viewport anzupassen.

Im Dokument [Konfiguration von Layout-Container und Layout-Modus](/help/sites-cloud/administering/responsive-layout.md) finden Sie weitere Informationen darüber, wie der Layout-Container funktioniert und wie Sie responsive Layouts für Ihre Inhalte aktivieren.
