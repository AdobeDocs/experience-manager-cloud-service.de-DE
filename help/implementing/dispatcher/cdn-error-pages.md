---
title: Konfigurieren von CDN-Fehlerseiten
description: Erfahren Sie, wie Sie die standardmäßige Fehlerseite außer Kraft setzen können, indem Sie statische Dateien in einer selbstgehosteten Datenspeicherung wie Amazon S3 oder Azure Blob Storage hosten und darauf in einer Konfigurationsdatei verweisen, die mithilfe der Cloud Manager-Konfigurations-Pipeline bereitgestellt wird.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
role: Admin
source-git-commit: 3a46db9c98fe634bf2d4cffd74b54771de748515
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---


# Konfigurieren von CDN-Fehlerseiten {#cdn-error-pages}

Im unwahrscheinlichen Fall, dass das [Adobe-verwaltete CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) den AEM-Ursprung nicht erreichen kann, gibt das CDN standardmäßig eine ungebrandete, generische Fehlerseite aus, die angibt, dass der Server nicht erreicht werden kann. Sie können die standardmäßige Fehlerseite außer Kraft setzen, indem Sie statische Dateien einer selbstgehosteten Datenspeicherung wie Amazon S3 oder Azure Blob Storage hosten und darauf in einer Konfigurationsdatei verweisen, die mithilfe der Cloud Manager-[Konfigurations-Pipeline](/help/operations/config-pipeline.md#managing-in-cloud-manager) bereitgestellt wird.

## Setup {#setup}

Bevor Sie die standardmäßige Fehlerseite außer Kraft setzen können, müssen Sie wie folgt vorgehen:

1. Erstellen Sie eine Datei mit dem Namen `cdn.yaml` oder ähnlich, die auf den nachfolgenden Syntax-Abschnitt verweist.

1. Platzieren Sie die Datei unter einem Ordner der obersten Ebene mit dem Namen *config* oder ähnlich, wie in [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) beschrieben.

1. Erstellen Sie in Cloud Manager eine Konfigurations-Pipeline, wie in [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#managing-in-cloud-manager) beschrieben.

1. Stellen Sie die Konfiguration bereit.

### Syntax {#syntax}

Die Fehlerseite wird als Einzelseitenanwendung (Single Page Application, SPA) implementiert und verweist auf eine Handvoll von Eigenschaften, wie im folgenden Beispiel gezeigt.   Die statischen Dateien, auf die von den URLs verwiesen wird, sollten von Ihnen in einem über das Internet zugänglichen Dienst wie Amazon S3 oder Azure Blob Storage gehostet werden.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
data:
  errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```

Eine Beschreibung der Eigenschaften oberhalb des Datenknotens finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Eigenschaftswert „kind“ sollte *CDN* sein, und die Eigenschaft `version` sollte auf *1* festgelegt werden.


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

### Tutorial

Eine schrittweise Anleitung zum Erstellen, Bereitstellen und Testen der vom CDN bereitgestellten Fehlerseiten finden Sie im Tutorial [CDN-Fehlerseiten](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/content-delivery/custom-error-pages#cdn-error-pages).


