---
title: Konfigurieren von CDN-Fehlerseiten
description: Erfahren Sie, wie Sie die standardmäßige Fehlerseite außer Kraft setzen können, indem Sie statische Dateien in selbstgehostetem Speicher wie Amazon S3 oder Azure Blob Storage hosten und in einer Konfigurationsdatei auf diese verweisen, die mithilfe der Cloud Manager-Konfigurationspipeline bereitgestellt wird.
feature: Dispatcher
source-git-commit: 11036c3e95f0444fc5d865232a7dccab5b7f26ae
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---


# Konfigurieren von CDN-Fehlerseiten {#cdn-error-pages}

>[!NOTE]
>Diese Funktion ist noch nicht allgemein verfügbar. Um dem Programm für frühe Anwender beizutreten, senden Sie eine E-Mail `aemcs-cdn-config-adopter@adobe.com` und beschreiben Sie Ihren Anwendungsfall.

Im unwahrscheinlichen Fall wird die [Adobe-verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) kann den AEM nicht erreichen, gibt das CDN standardmäßig eine ungebrandete, generische Fehlerseite aus, die angibt, dass der Server nicht erreicht werden kann. Sie können die Standardfehlerseite außer Kraft setzen, indem Sie statische Dateien in selbstgehostetem Speicher wie Amazon S3 oder Azure Blob Storage hosten und sie in einer Konfigurationsdatei referenzieren, die mithilfe des [Cloud Manager-Konfigurations-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline).

## Setup {#setup}

Bevor Sie die standardmäßige Fehlerseite überschreiben können, müssen Sie Folgendes tun:

* Erstellen Sie zunächst diesen Ordner und die Dateistruktur im Ordner der obersten Ebene Ihres Git-Projekts:

```
config/
     cdn.yaml
```

* Zweitens, die `cdn.yaml` Die Konfigurationsdatei sollte Metadaten und die Fehlerseitenverweise enthalten, wie unten beschrieben.

### Konfiguration {#configuration}

Die Fehlerseite wird als Einzelseitenanwendung (SPA) implementiert und verweist auf eine Handvoll von Eigenschaften, wie im folgenden Beispiel gezeigt.  Die statischen Dateien, auf die von den URLs verwiesen wird, sollten von Ihnen in einem Internet-zugänglichen Dienst wie Amazon S3 oder Azure Blob Storage gehostet werden.

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

### Beispielgenerierte HTML {#sample-generated-html}

Der HTML-Code, der vom CDN generiert und dem Client bereitgestellt wird, z. B. ein Browser, ähnelt dem folgenden Snippet (ist aber nicht identisch mit):

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

Rufen Sie zu Testzwecken den dedizierten -Endpunkt mit dem unterstützten Fehlercode auf, z. B.:

```
curl "https://publish-pXXXXX-eXXXXXX.adobeaemcloud.com/cdnstatus?code=403"
```

Folgende Codes werden unterstützt: 403, 404, 406, 500 und 503.

Auf diese Weise können Sie den Fehler-Handler des CDN direkt Trigger haben, um die synthetische Antwort auf den angegebenen Fehlercode zu testen.
