---
title: Editor-Einschränkungen
description: Der Editor in der Touch-optimierten Benutzeroberfläche nutzt Überlagerungen, um mit dem Inhalt eines iframe zu interagieren. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler.
exl-id: 6a4f0e43-1076-4da9-95dc-9c5bf83e30d0
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 100%

---

# Editor-Einschränkungen {#editor-limitations}

Der Editor in der Touch-optimierten Benutzeroberfläche nutzt Überlagerungen, um mit dem Inhalt eines iframe zu interagieren. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler. Auf dieser Seite werden diese Einschränkungen zusammengefasst und, wo möglich, Lösungen bzw. Problemumgehungen zur Verfügung gestellt.

## Funktionale Einschränkungen  {#functional-limitations}

Autoren sehen sich bei der Arbeit mit dem Editor zur Bearbeitung von Seiten möglicherweise mit den folgenden funktionalen Einschränkungen konfrontiert.

### Links nicht aktiv   {#links-not-active}

Beim [Bearbeiten einer Seite](/help/sites-cloud/authoring/fundamentals/editing-content.md) sind Links nicht aktiv.

* [Wechseln Sie in den Modus **Vorschau**](/help/sites-cloud/authoring/fundamentals/editing-content.md#preview-mode), um anhand der Links in den Inhalten zu navigieren.

### Strukturseiten {#structure-pages}

Seiten dürfen nicht `structure` genannt werden. Seiten mit dem Namen `structure` können im Seiteneditor nicht bearbeitet werden.

## CSS-Einschränkungen {#css-limitations}

Entwickler sehen sich hinsichtlich der Interaktionen des Editors mit CSS möglicherweise mit den folgenden Einschränkungen konfrontiert.

### Absolut positionierte Elemente   {#absolutely-positioned-elements}

Absolut positionierte Elemente können Probleme bei der Positionierung ihrer Überlagerung verursachen.

* Ist dies der Fall, müssen Sie darauf achten, dass die Abmessungen des absolut positionierten Elements korrekt sind, weil der Editor eine Überlagerung mit den gleichen Abmessungen erstellt.

### vh-Einheiten   {#vh-units}

`vh`-Einheiten werden nicht unterstützt, da die iframe-Höhe von AEM automatisch angepasst werden muss.

### Feste Hintergrundbilder {#fixed-background-images}

Feste Hintergrundbilder werden beim Scrollen nicht als fest angezeigt, weil sie in einen iframe eingebettet sind.

* Wird in der Kopfzeile **Seite als veröffentlicht anzeigen** ausgewählt, wird die Seite korrekt angezeigt.

### 100 % Höhe {#height}

100 % Höhe wird im Hauptteilelement einer Seite nicht unterstützt.

* Dieses Problem kann umgangen werden, um einen Vollbildhauptteil zu implementieren, indem das Hauptteilelement wie folgt gestreckt wird:

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
