---
title: Edge Side Includes
description: Das Adobe Managed CDN unterstützt jetzt Edge Side Includes (ESI), eine Markup-Sprache für die dynamische Webinhaltassembly auf Edge-Ebene.
feature: Dispatcher
source-git-commit: fb7c793a975fd725ef1cebcab545e057de78fa9d
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 4%

---

# Edge Side Includes {#edge-side-includes}

>[!NOTE]
>Diese Funktion ist noch nicht allgemein verfügbar.  Um dem Early-Adopter-Programm beizutreten, senden Sie eine E-Mail an `aemcs-cdn-config-adopter@adobe.com` und beschreiben Sie Ihren Anwendungsfall.

Die Geschwindigkeit der Inhaltsbereitstellung profitiert von der aggressiven Zwischenspeicherung von Seiten, die durch Festlegen von Cache-Headern mit hoher Time-to-Live-Zeit-Werten (TTL) erreicht wird. Dies kann eine Herausforderung darstellen, wenn Seiten dynamische Inhalte enthalten, die häufig aktualisiert werden müssen oder möglicherweise überhaupt nicht zwischengespeichert werden können. Glücklicherweise gibt es Strategien, bei denen die übergeordnete HTML-Seite mit einer hohen TTL zwischengespeichert werden kann, indem der Abruf der dynamischeren Inhaltsfragmente entweder über Client-seitiges JavaScript oder im CDN auf einen späteren Zeitpunkt verschoben wird. Letzterer Ansatz ist ein Standard mit der Bezeichnung Edge Side Includes (ESI), der für Sites unterstützt wird, die mit AEM Publishing gerendert werden. Die HTML enthält ESI-Tags, die das CDN anweisen, die Bereitstellung der Seite an den Browser zu verschieben, bis es diese Tags auswertet, wodurch zusätzliche, dynamischere (niedrigere TTL) Inhalte aus der Quelle (oder CDN-Cache, wenn die TTL noch nicht abgelaufen ist) abgerufen werden.

Einige Anwendungsfälle, in denen Edge Side Includes nützlich sein kann:

* Anzeigen des Namens eines Endbenutzers oder anderer Informationen, die für einen Endbenutzer eindeutig sind.
* Hier finden Sie eine Liste aktueller Informationen, z. B. News-Artikel oder Börsenkurse.

## ESI-Syntax {#esi-syntax}

Die ESI-Syntax lautet wie folgt, wenn eine übergeordnete Seite `/content/page.html` enthält einen Snippet `content/snippets/mysnippet.html`.

```
<html>
  <head>
      <title>My Site</title>
  </head>
  <body>
    <div id="content">
      <esi:include src="/content/snippets/mysnippet.html" />
    </div>
  </body>
</html>
```

Siehe [ESI-Spezifikation](https://www.w3.org/TR/esi-lang/) für Details.

### Überlegungen {#esi-syntax-considerations}

* Die folgenden ESI-Tags werden unterstützt: include, comment, remove.
* ESI-Tags werden beim CDN sequenziell und nicht gleichzeitig verarbeitet, sodass viele ESI-Tags auf einer Seite mit niedrigen TTLs die Latenz zum Erlebnis des Endbenutzers hinzufügen können.
* Die maximale Tiefe der Verarbeitung von ESI:include beträgt 5.
* Die maximale Gesamtanzahl an ESI:include-Verarbeitungsfragmenten beträgt 256.


## Apache-Konfiguration {#esi-apache}

Wenn Sie Seiten mit ESI-Tags haben, sollten Sie die folgenden Eigenschaften in der Apache-Konfiguration deklarieren:

```
<LocationMatch "/parent-pages/*content/page.html">
   # disable dispatcher compression
   SetEnv no-gzip 1
   # enable esi processing 
   Header set x-aem-esi "on"
   # enable edgeCDN compression
   Header set x-aem-compress "on"

   # typically the main page is cached at the CDN
   Header always set Cache-Control "max-age=300"
 </LocationMatch>


<LocationMatch "/content/snippets/mysnippet.html">
  SetEnv no-gzip 1

  # typically the included page is either set to a lower TTL than the parent page, or not cached at all, as these 2 commented declarations show, respectively:
  #Header always set Cache-Control "no-cache"
  #Header always set Cache-Control "max-age=50"
 </LocationMatch> 
```

Die konfigurierten Eigenschaften weisen folgendes Verhalten auf:

| Eigenschaft | Verhalten |
|-----------|--------------------------|
| **no-gzip** | Wenn der Wert auf 1 gesetzt ist, wird die HTML-Seite unkomprimiert von Apache an das CDN übertragen. Dies ist für ESI erforderlich, da Inhalte unkomprimiert an CDN gesendet werden müssen, damit das CDN die ESI-Tags sehen und auswerten kann.<br/><br/>Sowohl die übergeordnete Seite als auch die enthaltenen Snippets sollten no-gzip auf 1 setzen.<br/><br/>Diese Einstellung setzt die Komprimierungseinstellung außer Kraft, die Apache basierend auf der Anforderung `Accept-Encoding` -Werte. |
| **x-aem-esi** | Wenn der Wert auf &quot;on&quot;gesetzt ist, bewertet das CDN die ESI-Tags der übergeordneten HTML-Seite.  Standardmäßig ist die Kopfzeile nicht festgelegt. |
| **x-aem-compress** | Wenn der Wert auf &quot;on&quot;gesetzt ist, komprimiert das CDN den Inhalt aus dem CDN in den Browser. Da die Übertragung der übergeordneten Seite von Apache zu CDN unkomprimiert sein muss, damit ESI funktioniert (no-gzip auf 1 gesetzt), kann dies die Latenz verringern.<br/><br/>Wenn diese Kopfzeile nicht festgelegt ist und das CDN unkomprimierte Inhalte aus der Quelle abruft, werden Inhalte auch unkomprimiert für den Client bereitgestellt. Daher ist es erforderlich, diese Kopfzeile festzulegen, wenn no-gzip auf 1 gesetzt ist (für ESI erforderlich) und Inhalte bereitgestellt werden sollen, die vom CDN in den Browser komprimiert wurden. |

## Sling Dynamic Include {#esi-sdi}

Nicht erforderlich, [Dynamischer Sling-Einschluss](https://sling.apache.org/documentation/bundles/dynamic-includes.html) (SDI) kann verwendet werden, um ESI-Snippets zu generieren, die im CDN interpretiert werden.

