---
title: Konfigurieren von CDN-Fehlerseiten
description: Erfahren Sie, wie Sie die standardmäßige Fehlerseite außer Kraft setzen können, indem Sie statische Dateien in selbstgehostetem Speicher wie Amazon S3 oder Azure Blob Storage hosten und darauf in einer Konfigurationsdatei verweisen, die mithilfe der Cloud Manager-Konfigurations-Pipeline bereitgestellt wird.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
source-git-commit: 69ffcccae150a5e49c6344973890733f3e5b74ae
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 100%

---

# Konfigurieren von CDN-Fehlerseiten {#cdn-error-pages}

Im unwahrscheinlichen Fall, dass das [Adobe-verwaltete CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) den AEM-Ursprung nicht erreichen kann, gibt das CDN standardmäßig eine ungebrandete, generische Fehlerseite aus, die angibt, dass der Server nicht erreicht werden kann. Sie können die standardmäßige Fehlerseite außer Kraft setzen, indem Sie statische Dateien in selbstgehostetem Speicher wie Amazon S3 oder Azure Blob Storage hosten und darauf in einer Konfigurationsdatei verweisen, die mithilfe der [Cloud Manager-Konfigurations-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline) bereitgestellt wird.

## Setup {#setup}

Bevor Sie die standardmäßige Fehlerseite außer Kraft setzen können, müssen Sie wie folgt vorgehen:

* Erstellen Sie diesen Ordner und die Dateistruktur im obersten Ordner Ihres Git-Projekts:

```
config/
     cdn.yaml
```

* Die Konfigurationsdatei `cdn.yaml` sollte sowohl Metadaten als auch die Regeln enthalten, die in den nachfolgenden Beispielen beschrieben sind. Der Parameter `kind` sollte auf `CDN` und die Version auf die Schemaversion eingestellt sein (derzeit `1`). 

* Erstellen Sie eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager. Siehe [Konfigurieren von Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

**Anmerkungen**

* RDEs unterstützen derzeit nicht die Konfigurations-Pipeline.
* Sie können `yq` verwenden, um die YAML-Formatierung Ihrer Konfigurationsdatei lokal zu überprüfen (z. B. `yq cdn.yaml`).

### Konfiguration {#configuration}

Die Fehlerseite wird als Einzelseitenanwendung (Single Page Application, SPA) implementiert und verweist auf eine Handvoll von Eigenschaften, wie im folgenden Beispiel gezeigt.   Die statischen Dateien, auf die von den URLs verwiesen wird, sollten von Ihnen in einem über das Internet zugänglichen Dienst wie Amazon S3 oder Azure Blob Storage gehostet werden.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```

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
