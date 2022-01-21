---
title: Erweiterte URL-Konfigurationen
description: Informationen dazu, wie Sie die URLs für Produkt- und Kategorien-Seiten anpassen. Dies ermöglicht es, dass Implementierungen URLs für Suchmaschinen optimieren und ihr Auffinden fördern.
sub-product: Commerce
version: cloud-service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7,363cb465-c50a-422f-b149-b3f41c2ebc0f
source-git-commit: 78fa346cd2d6ed64c9700b7b2e611db58f7b3d11
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 29%

---

# Erweiterte URL-Konfigurationen {#url}

>[!NOTE]
>
> Suchmaschinenoptimierung (SEO) ist zu einem wichtigen Thema für viele Marketer geworden. Daher müssen SEO-Themen bei vielen Adobe Experience Manager (AEM) as a Cloud Service-Projekten berücksichtigt werden. Weitere Informationen finden Sie unter [Best Practices für SEO und URL-Verwaltung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/seo-and-url-management.html?lang=de).

[AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) stellen erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorieseiten bereit. Viele Implementierungen passen diese URLs für die Suchmaschinen-Optimierung (SEO) an. Im folgenden Video wird beschrieben, wie Sie den `UrlProvider`-Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren, um die URLs für Produkt- und Kategorieseiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Konfiguration {#configuration}

So konfigurieren Sie die `UrlProvider` -Dienst entsprechend den SEO-Anforderungen und benötigt ein Projekt, das eine OSGi-Konfiguration für die _CIF-URL-Provider-Konfiguration_.

>[!NOTE]
>
> Seit Version 2.0.0 der AEM CIF-Kernkomponenten bietet die URL-Provider-Konfiguration nur vordefinierte URL-Formate anstelle der von Version 1.x bekannten Freitext-konfigurierbaren Formate. Darüber hinaus wurde die Verwendung von Selektoren zur Übergabe von Daten in URLs durch Suffixe ersetzt.

### URL-Format von Produktseiten {#product}

Dies konfiguriert die URLs der Produktseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (default)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

Im Fall des [Venia Referenz-Shops](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wird durch `/content/venia/us/en/products/product-page` ersetzt
* `{{sku}}` wird durch die Produkt-SKU ersetzt, z. B. `VP09`
* `{{url_key}}` durch die `url_key`-Eigenschaft des Produkts ersetzt werden, z. B. `lenora-crochet-shorts`
* `{{url_path}}` wird durch den `url_path` des Produkts ersetzt, z. B. `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` wird durch die aktuell ausgewählte Variante ersetzt, z. B. `VP09-KH-S`

Seit `url_path` veraltet ist, verwenden die vordefinierten Produkt-URL-Formate die `url_rewrites` und wählen Sie das Segment mit den meisten Pfadsegmenten als Alternative aus, wenn die `url_path` ist nicht verfügbar.

Mit den obigen Beispieldaten sieht eine mit dem Standard-URL-Format formatierte Produktvarianten-URL wie `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S` aus.

### URL-Format von Kategorieseiten {#product-list}

Dies konfiguriert die URLs der Kategorieseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{url_path}}.html` (Standard)
* `{{page}}.html/{{url_key}}.html`

Im Fall des [Venia Referenz-Shops](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wird durch `/content/venia/us/en/products/category-page` ersetzt
* `{{url_key}}` wird durch die `url_key`-Eigenschaft der Kategorie ersetzt
* `{{url_path}}` wird durch den `url_path` der Kategorie ersetzt

Mit den obigen Beispieldaten sieht eine Kategorieseiten-URL, die mit dem Standard-URL-Format formatiert ist, wie `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html` aus.

>[!NOTE]
> 
> Der `url_path` ist eine Verkettung aus dem `url_keys` der Vorgänger eines Produkts oder einer Kategorie und dem `url_key` des Produkts oder der Kategorie, getrennt durch `/`-Schrägstrich. Jeder `url_key` wird innerhalb eines Stores als eindeutig betrachtet.

### Store-spezifische Konfiguration {#store-specific-urlformats}

Die systemweiten Kategorie- und Produktseiten-URL-Formate, die von der _CIF-URL-Provider-Konfiguration_ kann für jeden Store geändert werden.

In der CIF-Konfiguration kann ein Editor ein alternatives URL-Format für Produkt- oder Kategorieseiten auswählen. Wenn dort nichts ausgewählt ist, wird die Implementierung zur systemweiten Konfiguration zurückgreifen.

Eine Änderung des URL-Formats einer Live-Website kann sich negativ auf den organischen Traffic Ihrer Site auswirken. Weitere Informationen finden Sie unter [Best Practices](#best-practices) und planen Sie sorgfältig die Änderung des URL-Formats im Voraus.

![URL-Formate in der CIF-Konfiguration](assets/store-specific-url-formats.png)

>[!NOTE]
>
> Die speicherspezifische Konfiguration der URL-Formate erfordert [CIF-Kernkomponenten 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) und die neueste Version des Adobe Experience Manager Content and Commerce-Add-ons.

## Kategorienabhängige Produkt-URLs {#context-aware-pdps}

Da Kategorieinformationen in einer Produkt-URL kodiert werden können, können Produkte, die sich in mehreren Kategorien befinden, auch mit mehreren Produkt-URLs adressiert werden.

In der Standardkonfiguration wählen die Standard-URL-Formate eine der möglichen Alternativen mithilfe des folgenden Schemas aus:

* wenn die `url_path` wird durch das E-Commerce-Backend definiert, das es verwendet (nicht mehr unterstützt)
* von `url_rewrites` Verwenden Sie die URLs, die mit dem `url_key` als Alternativen
* aus diesen Alternativen verwenden die mit den meisten Pfadsegmenten
* Wenn mehrere vorhanden sind, nehmen Sie die erste in der Reihenfolge, die vom E-Commerce-Backend angegeben wird.

Im Rahmen dieser Regelung wird `url_path` , das die meisten Vorgänger hat, basierend auf der Annahme, dass eine untergeordnete Kategorie spezifischer ist als die übergeordnete Kategorie. Die so ausgewählte `url_path` wird _kanonisch_ und wird immer für den kanonischen Link auf Produktseiten oder in der Produkt-Sitemap verwendet.

Wenn ein Käufer jedoch von einer Kategorieseite zu einer Produktseite oder von einer Produktseite zu einer anderen zugehörigen Produktseite in derselben Kategorie navigiert, empfiehlt es sich, den aktuellen Kategoriekontext beizubehalten. In diesem Fall ist `url_path` Bei der Auswahl sollten Alternativen bevorzugt werden, die sich innerhalb des aktuellen Kategoriekontexts befinden, anstatt _kanonisch_ Auswahl beschrieben.

Diese Funktion muss im _CIF-URL-Provider-Konfiguration_. Wenn die Auswahl aktiviert ist, werden Alternativen höher bewertet, wenn

* sie stimmen mit Teilen einer bestimmten Kategorie überein `url_paths` von Anfang an (Fuzzy-Präfixabgleich)
* oder sie mit einer bestimmten Kategorie übereinstimmen `url_key` an beliebiger Stelle (exakter Teilabgleich)

Betrachten Sie beispielsweise die Antwort für eine [Produktabfrage](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) unten. Wenn sich der Benutzer auf der Kategorieseite &quot;Neue Produkte/Neu im Sommer 2022&quot;befindet und der Store das standardmäßige Kategorieseiten-URL-Format verwendet, würde die Alternative &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;von Anfang an mit 2 der Pfadsegmente des Kontexts übereinstimmen: &quot;new-products&quot;und &quot;new-in-summer-2022&quot;. Wenn der Store ein Kategorieseiten-URL-Format verwendet, das nur die `url_key`, wird dieselbe Alternative weiterhin ausgewählt, da sie mit der `url_key` überall. In beiden Fällen wird die Produktseiten-URL für die &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;erstellt `url_path`.

```
{
  "data": {
    "products": {
      "items": [
        {
          "sku": "VA18-GO-NA",
          "url_key": "gold-cirque-earrings",
          "url_rewrites": [
            {
              "url": "gold-cirque-earrings.html"
            },
            {
              "url": "venia-accessories/gold-cirque-earrings.html"
            },
            {
              "url": "venia-accessories/venia-jewelry/gold-cirque-earrings.html"
            },
            {
              "url": "new-products/gold-cirque-earrings.html"
            },
            {
              "url": "new-products/new-in-summer-2022/gold-cirque-earrings.html"
            }
          ]
        }
      ]
    }
  }
}
```

>[!NOTE]
>
> Für kategorisierte Produkt-URLs ist erforderlich [CIF-Kernkomponenten 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) oder neuer.

## Spezifische Kategorie- und Produktseiten {#specific-pages}

Es ist möglich, [mehrere Kategorie- und Produktseiten](../authoring/multi-template-usage.md) nur für eine bestimmte Untergruppe von Kategorien oder Produkten eines Katalogs.

### Auswahlkriterien {#specific-pages-selection}

Die Auswahl einer bestimmten Kategorieseite erfolgt direkt nach vorn, basierend auf der Kategorie `url_path` oder `url_key`. Die Übereinstimmung von Unterkategorien wird nur für URL-Formate unterstützt, die die vollständige Kategorie enthalten `url_path`. Andernfalls wird nur eine exakte Übereinstimmung mit der `url_key` ist möglich.

Bestimmte Produktseiten werden entweder nach der SKU oder Kategorie des Produkts ausgewählt. Für später müssen einige Kategorieinformationen in der Produkt-URL kodiert werden. Dies ist nur für einige der Standard-URL-Formate verfügbar. In der folgenden Tabelle finden Sie einen Vergleich, welches URL-Format die spezifische Seitenauswahl nach SKU oder Kategorie unterstützt.


| URL-Format | von SKU | nach Kategorie |
| ----------------------------------------------------- | ------ | ---------------- |
| `{{page}}.html/{{url_key}}.html` | keine | keine |
| `{{page}}.html/{{category}}/{{url_key}}.html` | keine | Nur exakte Übereinstimmung |
| `{{page}}.html/{{url_path}}.html` | keine | yes |
| `{{page}}.html/{{sku}}.html` | yes | keine |
| `{{page}}.html/{{sku}}/{{url_key}}.html` | yes | keine |
| `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html` | yes | Nur exakte Übereinstimmung |
| `{{page}}.html/{{sku}}/{{url_path}}.html` | yes | yes |

>[!NOTE]
>
> Die Auswahl bestimmter Produktseiten nach Kategorie erfordert [CIF-Kernkomponenten 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) oder neuer.

### Depp-Verknüpfung {#specific-pages-deep-linking}

Die `UrlProvider` ist vorkonfiguriert, um Deep-Links zu bestimmten Kategorie- und Produktseiten in Autorenebeneninstanzen zu generieren. Dies ist für Bearbeiter nützlich, die eine Site im Vorschaumodus durchsuchen, zu einer bestimmten Produkt- oder Kategorieseite navigieren und zurück in den Bearbeitungsmodus wechseln, um die Seite zu bearbeiten.

Auf Veröffentlichungsebenen-Instanzen hingegen sollten Katalogseiten-URLs stabil gehalten werden, um beispielsweise Gewinne bei Suchmaschinenrankings zu vermeiden. Aufgrund dieser Veröffentlichungsstufe rendern Instanzen standardmäßig keine Deep-Links zu bestimmten Katalogseiten. Um dieses Verhalten zu ändern, muss die Variable _CIF-URL-Provider-spezifische Seitenstrategie_ kann so konfiguriert werden, dass immer bestimmte Seiten-URLs generiert werden.

## Anpassungen {#customization}

### Benutzerdefinierte URL-Formate {#custom-url-format}

Um ein benutzerdefiniertes URL-Format bereitzustellen, kann ein Projekt entweder die [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) oder [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) -Dienstschnittstelle verwenden und die Implementierung als OSGi-Dienst registrieren. Diese Implementierungen ersetzen, sofern verfügbar, das konfigurierte, vordefinierte Format. Wenn mehrere Implementierungen registriert sind, ersetzt die Implementierung mit dem höheren Service-Rang die Implementierung(en) durch das niedrigere Service-Rang.

Die Implementierungen des benutzerdefinierten URL-Formats müssen zwei Methoden implementieren, um eine URL aus den angegebenen Parametern zu erstellen und eine URL zu analysieren, um dieselben Parameter zurückzugeben.

### Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Neben `UrlProvider` können auch [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfiguriert werden, um URLs neu zu schreiben und zu verarbeiten. Das AEM-Archetyp-Projekt bietet außerdem [eine Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) zum Konfigurieren einiger Sling-Zuordnungen für Port 4503 (Veröffentlichungsinstanz) und Port 80 (Dispatcher).

### Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Neuschreibungen können auch mithilfe AEM Dispatcher-HTTP-Servers mit `mod_rewrite` -Modul. Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) stellt eine AEM Dispatcher-Referenzkonfiguration bereit, die bereits grundlegende [Neuschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Best Practices {#best-practices}

### Das beste URL-Format auswählen {#choose-url-format}

Wie bereits erwähnt, hängt die Auswahl eines der verfügbaren Standardformate oder sogar die Implementierung eines benutzerdefinierten Formats stark von den Anforderungen und Anforderungen eines Stores ab. Die folgenden Vorschläge können dabei helfen, eine fundierte Entscheidung zu treffen.

_**Verwenden Sie ein URL-Format der Produktseite, das die SKU enthält.**_

Die CIF-Kernkomponenten verwenden die SKU als primäre Kennung in allen Komponenten. Wenn das URL-Format der Produktseite die SKU nicht enthält, ist eine GraphQL-Abfrage erforderlich, um sie aus dem `url_key`, was sich auf die Zeit-zu-1-Byte-Metrik auswirken kann. Außerdem kann es für Käufer interessant sein, in Suchmaschinen Produkte von SKU zu finden.

_**Verwenden Sie ein Produktseiten-URL-Format, das den Kategoriekontext enthält.**_

Einige Funktionen des CIF-URL-Anbieters sind nur verfügbar, wenn Produkt-URL-Formate verwendet werden, die den Kategoriekontext kodieren, z. B. die Kategorie `url_key` oder der Kategorie `url_path`. Auch wenn diese Funktionen für einen neuen Store möglicherweise nicht erforderlich sind, trägt die Verwendung eines dieser URL-Formate am Anfang dazu bei, den Migrationsaufwand in Zukunft zu reduzieren.

_**Gleichgewicht zwischen URL-Länge und kodierten Informationen.**_

Je nach Kataloggröße, insbesondere Größe und Tiefe des Kategoriebaums, ist es möglicherweise nicht sinnvoll, die vollständige Kodierung vorzunehmen `url_path` der Kategorien in die URL ein. In diesem Fall kann die URL-Länge durch Einbeziehung der Kategorie `url_key` anstatt. Dadurch werden fast alle Funktionen aktiviert, die bei Verwendung der Kategorie verfügbar sind `url_path`.

Nutzen Sie außerdem [Sling-Zuordnungen](#sling-mapping) um die SKU mit dem Produkt zu kombinieren `url_key`. In den meisten E-Commerce-Systemen folgt die SKU einem bestimmten Format und trennt die SKU von `url_key` für eingehende Anfragen leicht möglich sein. Vor diesem Hintergrund sollte es möglich sein, eine Produktseiten-URL in `/p/{{category}}/{{sku}}-{{url_key}}.html`und einer Kategorie-URL zu `/c/{{url_key}}.html` bzw. Die `/p` und `/c` -Präfix sind weiterhin erforderlich, um Produkt- und Kategorieseiten von anderen Inhaltsseiten zu unterscheiden.

### Migration von einem URL-Format zum anderen {#migrate-url-formats}

Viele der Standard-URL-Formate sind irgendwie miteinander kompatibel, d. h. URLs, die von einer formatiert wurden, können von einer anderen analysiert werden. Dies hilft bei der Migration zwischen den URL-Formaten.

Andererseits benötigen Suchmaschinen etwas Zeit, um alle Katalogseiten mit dem neuen URL-Format erneut zu durchsuchen. Um diesen Prozess zu unterstützen und auch das Endbenutzererlebnis zu verbessern, wird empfohlen, Umleitungen bereitzustellen, die den Benutzer von den alten URLs an die neuen weiterleiten.

Ein Ansatz dafür wäre, eine Staging-Umgebung mit dem Produktions-E-Commerce-Backend zu verbinden und es so zu konfigurieren, dass es das neue URL-Format verwendet. Rufen Sie anschließend die [Produkt-Sitemap, die von dem CIF-Produkt-Sitemap-Generator generiert wird](../../overview/seo-and-url-management.md) für die Staging- und Produktionsumgebung und verwenden Sie sie zum Erstellen einer [Apache httpd-Rewrite-Zuordnung](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). Diese Umschreibungszuordnung kann zusammen mit dem Rollout des neuen URL-Formats für den Dispatcher bereitgestellt werden.

## Beispiel {#example}

Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren. Dadurch kann jedes Projekt individuelle URL-Muster für Produkt- und Kategorieseiten entsprechend ihren SEO-Anforderungen einrichten. Es wird eine Kombination aus CIF-`UrlProvider` und Sling-Zuordnungen verwendet, wie oben beschrieben.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domain angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Host-Namens und der Domain. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Implementierung aktiviert werden. Benennen Sie dazu den Ordner `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domain-Namen um und aktivieren Sie diese Konfiguration, indem Sie `resource.resolver.map.location="/etc/map.publish"` zur `JcrResourceResolver`-Konfiguration des Projekts hinzufügen.

## Zusätzliche Ressourcen {#additional}

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [AEM-Ressourcenzuordnung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=de)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
