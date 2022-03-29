---
title: REST-APIs
description: Screens as a Cloud Service bietet eine einfache RESTful-API, die der Siren-Spezifikation entspricht. Auf dieser Seite erfahren Sie, wie Sie in der Inhaltsstruktur navigieren und Befehle an Geräte in der Umgebung senden können.
exl-id: 2c52583f-0dd9-4fa3-880b-7671442989ae
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 100%

---

# REST-APIs {#rest-apis}

AEM Screens stellt eine einfache RESTful-API bereit, die der [Siren](https://github.com/kevinswiber/siren)-Spezifikation entspricht. Sie ermöglicht die Navigation in der Inhaltsstruktur und das Senden von Befehlen an Geräte in der Umgebung.

Die API steht unter [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json) zur Verfügung.

## Navigieren in der Inhaltsstruktur {#navigating-content-structure}

Die von den API-Aufrufen zurückgegebene JSON-Datei listet die Entitäten auf, die im Zusammenhang mit der aktuellen Ressource stehen. Über den aufgeführten Selbst-Link kann auf jede dieser Entitäten wieder als REST-Ressource zugegriffen werden.

Um beispielsweise auf die Bildschirme an unserem Demo-Flagship-Standort zuzugreifen, können Sie Folgendes aufrufen:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

Oder mithilfe von cURL:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

Das Ergebnis sieht dann wie folgt aus:

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

Und um dann auf den einzelnen Bildschirm zuzugreifen, können Sie Folgendes aufrufen:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## Ausführen von Aktionen auf Ressourcen {#executing-actions-on-the-resource}

Die von den API-Aufrufen zurückgegebene JSON-Datei kann eine Liste von Aktionen enthalten, die für die Ressource verfügbar sind.

Auf dem Bildschirm wird beispielsweise eine Aktion *broadcast-command* aufgeführt, die es erlaubt, einen Befehl an alle diesem Bildschirm zugeordneten Geräte zu senden.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

Oder mithilfe von cURL:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***Ergebnis:***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

Um diese Aktion auszulösen, muss Folgendes aufgerufen werden:

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

Oder mithilfe von cURL:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```
