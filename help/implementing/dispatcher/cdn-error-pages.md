---
title: Konfigurieren von CDN-Fehlerseiten
description: Erfahren Sie, wie Sie die standardmäßige Fehlerseite außer Kraft setzen können, indem Sie statische Dateien in selbstgehostetem Speicher wie Amazon S3 oder Azure Blob Storage hosten und in einer Konfigurationsdatei auf diese verweisen, die mithilfe der Cloud Manager-Konfigurationspipeline bereitgestellt wird.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
role: Admin
source-git-commit: 3a10a0b8c89581d97af1a3c69f1236382aa85db0
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 57%

---


# Konfigurieren von CDN-Fehlerseiten {#cdn-error-pages}

Im unwahrscheinlichen Fall, dass das [Adobe-verwaltete CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) den AEM-Ursprung nicht erreichen kann, gibt das CDN standardmäßig eine ungebrandete, generische Fehlerseite aus, die angibt, dass der Server nicht erreicht werden kann. Sie können die Standardfehlerseite außer Kraft setzen, indem Sie statische Dateien in selbstgehostetem Speicher wie Amazon S3 oder Azure Blob Storage hosten und sie in einer Konfigurationsdatei referenzieren, die mithilfe der Cloud Manager [config-Pipeline](/help/operations/config-pipeline.md#managing-in-cloud-manager) bereitgestellt wird.

## Setup {#setup}

Bevor Sie die standardmäßige Fehlerseite außer Kraft setzen können, müssen Sie wie folgt vorgehen:

1. Erstellen Sie eine Datei mit dem Namen `cdn.yaml` oder eine ähnliche Datei, die auf den Syntax-Abschnitt unten verweist.

1. Platzieren Sie die Datei in einen Ordner der obersten Ebene mit dem Namen *config* oder einem ähnlichen Ordner, wie im Abschnitt [Konfiguration der Pipeline-Artikel](/help/operations/config-pipeline.md#folder-structure) beschrieben.

1. Erstellen Sie eine Konfigurations-Pipeline in Cloud Manager, wie im Artikel [Konfiguration der Pipeline ](/help/operations/config-pipeline.md#managing-in-cloud-manager) beschrieben.

1. Stellen Sie die Konfiguration bereit.

### Syntax {#syntax}

Die Fehlerseite wird als Einzelseitenanwendung (Single Page Application, SPA) implementiert und verweist auf eine Handvoll von Eigenschaften, wie im folgenden Beispiel gezeigt.   Die statischen Dateien, auf die von den URLs verwiesen wird, sollten von Ihnen in einem über das Internet zugänglichen Dienst wie Amazon S3 oder Azure Blob Storage gehostet werden.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```
Eine Beschreibung der Eigenschaften über dem Daten-Knoten finden Sie im Artikel [Konfiguration der Pipeline ](/help/operations/config-pipeline.md#common-syntax) . Der Wert der Eigenschaft type sollte *CDN* und die Eigenschaft `version` auf *1* eingestellt sein.


| Name | Zulässige Eigenschaften | Bedeutung |
|-----------|--------------------------|-------------|
| **spa** | title | Titel für die Fehlerseite. |
|     | icoUrl | URL zu einer Symboldatei. |
|     | cssUrl | URL zu einer CSS-Datei. |
|     | jsUrl | URL zu einer JavaScript-Datei. |

### Generierte Beispiel-HTML {#sample-generated-html}

Der HTML-Code, der vom CDN generiert und dem Client bereitgestellt wird, z. B. einem Browser, ähnelt dem folgenden Snippet (ist aber nicht identisch mit diesem):

```
<!DOCTYPE html>
<html lang="en">
    <head>
        ...
        <title>the error page</title>
        <link rel="icon" href="https://www.example.com/error.ico">
        <link rel="stylesheet" href="https://www.example.com/error.css">
    </head>
    <body>
        ...
        <div id="root" status="403"></div>
        <script src="https://www.example.com/error.js"> </script>
    </body>
</html>
```

### Testen {#testing}

Rufen Sie zu Testzwecken den dedizierten Endpunkt mit dem unterstützten Fehler-Code auf, z. B.:

```
curl "https://publish-pXXXXX-eXXXXXX.adobeaemcloud.com/cdnstatus?code=403"
```

Folgende Codes werden unterstützt: 403, 404, 406, 500 und 503.

Auf diese Weise können Sie den Fehler-Handler des CDN direkt auslösen, um die synthetische Antwort auf einen bestimmten Fehler-Code zu testen.
