---
title: Einschränkungen beim Seiteneditor
description: Der Seiteneditor nutzt Überlagerungen zur Interaktion mit Inhalten, die in einem iframe enthalten sind. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickelnde.
exl-id: 6a4f0e43-1076-4da9-95dc-9c5bf83e30d0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8b38e26b16c1fb565f122777f0577d332f62c39c
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 88%

---


# Einschränkungen beim Seiteneditor {#editor-limitations}

[Der Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md) verwendet Überlagerungen zur Interaktion mit Inhalten, die in einem iframe eingeschlossen sind. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler. Diese Seite fasst diese Einschränkungen zusammen und bietet nach Möglichkeit Lösungen oder Umgehungen.

## Funktionale Einschränkungen {#functional-limitations}

Autoren sehen sich bei der Arbeit mit dem Editor zur Bearbeitung von Seiten möglicherweise mit den folgenden funktionalen Einschränkungen konfrontiert.

### Links nicht aktiv {#links-not-active}

Beim [Bearbeiten einer Seite](/help/sites-cloud/authoring/page-editor/edit-content.md) sind Links nicht aktiv.

* [Wechseln Sie in den Modus **Vorschau**](/help/sites-cloud/authoring/page-editor/introduction.md#preview-mode), um anhand der Links in den Inhalten zu navigieren.

### Strukturseiten {#structure-pages}

Seiten können nicht `structure` genannt werden. Seiten mit dem Namen `structure` können im Seiteneditor nicht bearbeitet werden.

## CSS-Einschränkungen {#css-limitations}

Entwickler sehen sich hinsichtlich der Interaktionen des Editors mit CSS möglicherweise mit den folgenden Einschränkungen konfrontiert.

### Absolut positionierte Elemente {#absolutely-positioned-elements}

Absolut positionierte Elemente können Probleme bei der Position ihrer Überlagerung verursachen.

* Stellen Sie in diesem Fall sicher, dass die Abmessungen des absolut positionierten Elements korrekt sind, da der Editor eine Überlagerung mit exakt denselben Abmessungen erstellt.

### vh-Einheiten {#vh-units}

`vh`-Einheiten werden nicht unterstützt, da die iframe-Höhe von AEM automatisch angepasst werden muss.

### Feste Hintergrundbilder {#fixed-background-images}

Feste Hintergrundbilder werden beim Scrollen nicht als fest angezeigt, weil sie in einen iframe eingebettet sind.

* Wird in der Kopfzeile **Seite als veröffentlicht anzeigen** ausgewählt, wird die Seite korrekt angezeigt.

### 100 % Höhe {#height}

100 % Höhe wird im Hauptteilelement einer Seite nicht unterstützt.

* Dieses Problem kann umgangen werden, um einen bildschirmfüllenden Hauptteil zu implementieren, indem das Hauptteilelement wie folgt gestreckt wird:

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Ausblenden des Seitenrands {#margin-collapsing}

Probleme beim Ausblenden des Seitenrands treten auf, wenn das erste untergeordnete Element des Hauptteilelements einen Seitenrand aufweist.

* Die Lösung besteht darin, auf Ebene des Hauptteilelements einen Clearfix wie folgt einzufügen:

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
