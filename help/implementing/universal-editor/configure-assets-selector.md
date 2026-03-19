---
title: Konfigurieren der Assets-Auswahl für den universellen Editor
description: Erfahren Sie, wie Sie den Asset-Wähler für die Verwendung mit dem universellen Editor konfigurieren können.
feature: Developing
role: Admin, Developer
source-git-commit: 0ed57393afaf9af3258dacdcb043487f4a098e03
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---


# Konfigurieren der Assets-Auswahl für den universellen Editor {#configure-assets-selector}

Erfahren Sie, wie Sie den Asset-Wähler für die Verwendung mit dem universellen Editor konfigurieren können.

## Überblick {#overview}

Der universelle Editor verwendet [die Asset-Auswahl](/help/assets/overview-asset-selector.md#using-asset-selector), damit Autoren Assets durchsuchen und auswählen können, die in ihren Inhalt eingefügt werden sollen.

Der Asset-Wähler kann im universellen Editor mithilfe von [Komponentenfiltern“ konfiguriert werden.](/help/implementing/universal-editor/filtering.md) In diesem Dokument wird beschrieben, welche Konfigurationsoptionen verfügbar sind.

>[!NOTE]
>
>Wenn Sie ein Projekt im universellen Editor starten, sind für den Asset-Wähler keine Filter vorhanden. Autoren haben Zugriff auf alle Assets, die ihre Benutzerberechtigungen normalerweise zulassen.

## Filterdefinition {#filter-definition}

Die Filterdefinition für den Asset-Wähler hat eine einfache Struktur.

```json
[
  {
    "id": "assets-filter",
    "assets": {...}
   }
]
```

## Filteroptionen {#filter-options}

Der `assets` kann die folgenden Optionen aufweisen.

* `deliveryTier?`: - Legt fest, welche der folgenden Versandstufen verwendet werden soll:
   * `dm`: Dynamic Media (empfohlen) mit Fallback auf `publish`, falls erforderlich
   * `publish`: AEM-Veröffentlichungsinstanz
* `repoNames?`: Zeichenfolge - Liste der AEM-Repositorys, in denen Bilder ausgewählt werden können.
   * Standard: alle Versand-Repos
* `selectionTier?`: Zeichenfolge - AEM-Stufen zur Auswahl von Assets aus
   * Standard: `["author", "delivery"]`
* `disableRemote?`: Boolesch - Deaktivieren der Remote-Repository-Unterstützung
* `preselectedTypes?`: Zeichenfolge - Vorausgewählte Dateitypen, die als Standardfilter in der Asset-Auswahl angewendet werden sollen
* `minMaxDimensions?`: Objekt - Stellt minimale und/oder maximale Abmessungen (in Pixel) bereit, die als Standardfilter im Asset-Wähler angewendet werden sollen
   * `widthMin?`: Zahl - Mindestbreite
   * `widthMax?`: Zahl - Maximale Breite
   * `heightMin?`: Zahl - Mindesthöhe
   * `heightMax?`: Zahl - Maximale Höhe
* `minMaxFileSize?`: Objekt - Angabe der minimalen und/oder maximalen Dateigröße (in Byte), die als Standardfilter im Asset-Wähler angewendet werden soll
   * `min?`: Zahl - Mindestdateigröße
   * `max?`: Zahl - Maximale Dateigröße
* `customFileTypeFilters?`: Objekt - Stellt benutzerdefinierte Dateitypfilter bereit, die in der Asset-Auswahl angezeigt werden
   * `label`: Zeichenfolge - Bezeichnung, die in der Benutzeroberfläche zur Asset-Auswahl angezeigt wird
   * `value`: Zeichenfolge - Wert des zu filternden Dateityps
* `displayFilters?`: Boolesch - Wird verwendet, um die Filter-Benutzeroberfläche im Asset-Wähler zu deaktivieren; standardmäßig „true“

## Beispiel {#example}

Das folgende Beispiel enthält die meisten Optionen zu Veranschaulichungszwecken.

```json
[
  {
    "id": "assets-filter",
    "assets": {
      "deliveryTier": "dm",
      "repoNames": ["thisRepo", "thatRepo"],
      "selectionTier": ["author", "delivery"],
      "disableRemote": true,
      "preselectedTypes": ["png", "svg", "jpg", "gif"],
      "minMaxDimensions": {
        "widthMin": 640,
        "widthMax": 640,
        "heightMin": 480,
        "heightMax": 480
      },
      "minMaxFileSize": {
        "min": 1024,
        "max": 1024
      }
    }
   }
]
```

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum Asset-Selektor finden Sie im Dokument [Micro-Frontend-Asset-Selektor](/help/assets/overview-asset-selector.md#using-asset-selector) in der Assets-Dokumentation.
