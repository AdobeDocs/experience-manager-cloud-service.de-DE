---
title: Erweiterte URL-Konfigurationen
description: Informationen dazu, wie Sie die URLs für Produkt- und Kategorien-Seiten anpassen. Durch die Anpassung können Implementierungen URLs für Suchmaschinen optimieren und die Erkennung fördern.
sub-product: Commerce
version: Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '2172'
ht-degree: 48%

---

# Erweiterte URL-Konfigurationen {#url}

>[!NOTE]
>
> Suchmaschinenoptimierung (SEO) ist zu einem wichtigen Thema für viele Marketer geworden. Daher müssen SEO-Bedenken bei vielen Projekten auf Adobe Experience Manager (AEM) as a Cloud Service behandelt werden. Siehe [Best Practices für SEO und URL-Verwaltung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/seo-and-url-management.html) für weitere Informationen.

Die [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) ermöglichen erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorieseiten. Viele Implementierungen passen diese URLs für Suchmaschinenoptimierung (SEO) an. Im folgenden Video wird beschrieben, wie Sie den `UrlProvider`-Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren können, um die URLs für Produkt- und Kategorieseiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Konfiguration {#configuration}

So konfigurieren Sie die `UrlProvider` -Dienst entsprechend den SEO-Anforderungen und -Anforderungen, muss ein Projekt eine OSGi-Konfiguration für die _CIF-URL-Provider-Konfiguration_.

>[!NOTE]
>
> Seit Version 2.0.0 der CIF-Kernkomponenten von AEM bietet die URL-Provider-Konfiguration nur vordefinierte URL-Formate anstelle der von den Versionen 1.x bekannten, mit Freitext konfigurierbaren Formate. Darüber hinaus wurde die Verwendung von Selektoren zur Übergabe von Daten in URLs durch Suffixe ersetzt.

### URL-Format von Produktseiten {#product}

Konfiguriert die URLs der Produktseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (default)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

Wenn die Variable [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` ersetzt durch `/content/venia/us/en/products/product-page`
* `{{sku}}` durch die SKU des Produkts ersetzt wird, beispielsweise `VP09`
* `{{url_key}}` durch die `url_key` -Eigenschaft, z. B. `lenora-crochet-shorts`
* `{{url_path}}` durch die `url_path`, beispielsweise `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` durch die aktuell ausgewählte Variante ersetzt wird, beispielsweise `VP09-KH-S`

Seit `url_path` veraltet ist, verwenden die vordefinierten Produkt-URL-Formate die `url_rewrites` und wählen Sie alternativ eines mit den meisten Pfadsegmenten aus, wenn die `url_path` ist nicht verfügbar.

Bei den obigen Beispieldaten sieht eine mit dem Standard-URL-Format formatierte Produktvarianten-URL wie folgt aus: `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### URL-Format von Kategorieseiten {#product-list}

Konfiguriert die URLs der Kategorie- oder Produktlistenseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{url_path}}.html` (default)
* `{{page}}.html/{{url_key}}.html`

Wenn die Variable [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` ersetzt durch `/content/venia/us/en/products/category-page`
* `{{url_key}}` durch die Kategorie `url_key` property
* `{{url_path}}` durch die Kategorie `url_path`

Bei den obigen Beispieldaten sieht eine Kategorieseiten-URL, die im Standard-URL-Format formatiert ist, wie folgt aus `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
> Der `url_path` ist eine Verkettung aus dem `url_keys` der Vorgänger eines Produkts oder einer Kategorie und dem `url_key` des Produkts oder der Kategorie, getrennt durch einen Schrägstrich `/`. Jeder `url_key` wird innerhalb eines Stores als eindeutig betrachtet.

### Store-spezifische Konfiguration {#store-specific-urlformats}

Die systemweiten Kategorie- und Produktseiten-URL-Formate, die von der _CIF-URL-Provider-Konfiguration_ kann für jeden Store geändert werden.

In der CIF-Konfiguration kann ein Editor ein alternatives URL-Format für Produkt- oder Kategorieseiten auswählen. Wenn dort nichts ausgewählt ist, wird die Implementierung auf die systemweite Konfiguration zurückgesetzt.

Eine Änderung des URL-Formats einer Live-Website kann sich negativ auf den organischen Traffic Ihrer Site auswirken. Siehe [Best Practices](#best-practices) und planen Sie sorgfältig die Änderung des URL-Formats im Voraus.

![URL-Formate in der CIF-Konfiguration](assets/store-specific-url-formats.png)

>[!NOTE]
>
> Die speicherspezifische Konfiguration der URL-Formate erfordert [CIF-Kernkomponenten 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) und die neueste Version des Adobe Experience Manager Content and Commerce-Add-ons.

## Kategoriesensitive Produktseiten-URLs {#context-aware-pdps}

Da Kategorieinformationen in einer Produkt-URL codiert werden können, können Produkte, die sich in mehreren Kategorien befinden, auch durch mehrere Produkt-URLs adressiert werden.

Die Standard-URL-Formate wählen eine der möglichen Alternativen mithilfe des folgenden Schemas aus:

* wenn der `url_path` durch das E-Commerce-Backend definiert wird, wird dieser verwendet (nicht mehr unterstützt)
* von den `url_rewrites` werden diejenigen URLs, die mit dem `url_key` des Produkts enden, als Alternativen verwendet
* von diesen Alternativen wird die mit den meisten Pfadsegmenten verwendet
* wenn mehrere vorhanden sind, wird die erste in der Reihenfolge genommen, die vom E-Commerce-Backend angegeben wird.

Diese Regelung wählt die `url_path` mit den meisten Vorgängern, basierend auf der Annahme, dass eine untergeordnete Kategorie spezifischerer ist als ihre übergeordnete Kategorie. Die ausgewählte `url_path` wird _kanonisch_ und wird immer als kanonischer Link auf Produktseiten oder in der Produkt-Sitemap verwendet.

Wenn ein Käufer jedoch von einer Kategorieseite zu einer Produktseite oder von einer Produktseite zu einer anderen zugehörigen Produktseite in derselben Kategorie navigiert, empfiehlt es sich, den aktuellen Kategoriekontext beizubehalten. In diesem Fall wird die `url_path` Bei der Auswahl sollten Alternativen bevorzugt werden, die sich innerhalb des aktuellen Kategoriekontexts befinden, anstatt _kanonisch_ Auswahl beschrieben.

Diese Funktion muss im _CIF-URL-Provider-Konfiguration_. Wenn die Auswahl aktiviert ist, werden Alternativen höher bewertet, wenn

* sie mit Teilen des `url_path` einer bestimmten Kategorie von Anfang an übereinstimmen (unscharfer Präfixabgleich)
* oder sie mit dem `url_key` einer bestimmten Kategorie an beliebiger Stelle (exakter Teilabgleich) übereinstimmen.

Betrachten Sie beispielsweise die Antwort für eine [Produktabfrage](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) unten. Folgendes wird angezeigt:

* Der Benutzer befindet sich auf der Kategorieseite &quot;Neue Produkte/Neu im Sommer 2022&quot;.
* Der Speicher verwendet das standardmäßige Kategorieseiten-URL-Format

Die Alternative &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;entspricht zwei Pfadsegmenten des Kontexts vom Anfang an. Das heißt &quot;Neue Produkte&quot;und &quot;Neu-im-Sommer-2022&quot;. Wenn der Store ein URL-Format für Kategorieseiten verwendet, das nur den `url_key` der Kategorie enthält, wird dieselbe Alternative weiterhin ausgewählt, da sie überall zum `url_key` passt. In beiden Fällen wird die Produktseiten-URL für die &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;erstellt `url_path`.

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
> Für kategoriebezogene Produkt-URLs sind die [CIF-Kernkomponenten 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) oder neuer erforderlich.

## Spezifische Kategorie- und Produktseiten {#specific-pages}

Es ist möglich, [Mehrkategorie- und Produktseiten](../authoring/multi-template-usage.md) nur für eine bestimmte Untergruppe von Kategorien oder Produkten eines Katalogs.

### Auswahlkriterien {#specific-pages-selection}

Die Auswahl einer bestimmten Kategorieseite versteht sich von selbst, basierend auf dem `url_path` oder `url_key` der Kategorie. Übereinstimmende Unterkategorien werden nur für URL-Formate unterstützt, die die vollständige Kategorie enthalten `url_path`. Andernfalls ist nur eine exakte Übereinstimmung mit dem `url_key` möglich.

Bestimmte Produktseiten werden entweder durch die SKU oder Kategorie des Produkts ausgewählt. Letzteres erfordert, dass einige Kategorieinformationen in der Produkt-URL kodiert werden. Diese Funktion ist nur für einige der Standard-URL-Formate verfügbar. In der folgenden Tabelle finden Sie einen Vergleich, der angibt, welches URL-Format eine bestimmte Seitenauswahl nach SKU oder Kategorie unterstützt.


| URL-Format | nach SKU | nach Kategorie |
| ----------------------------------------------------- | ------ | ---------------- |
| `{{page}}.html/{{url_key}}.html` | nein | nein |
| `{{page}}.html/{{category}}/{{url_key}}.html` | nein | Nur exakte Übereinstimmung |
| `{{page}}.html/{{url_path}}.html` | nein | ja |
| `{{page}}.html/{{sku}}.html` | ja | nein |
| `{{page}}.html/{{sku}}/{{url_key}}.html` | ja | nein |
| `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html` | ja | Nur exakte Übereinstimmung |
| `{{page}}.html/{{sku}}/{{url_path}}.html` | ja | ja |

{style="table-layout:auto"}

>[!NOTE]
>
> Die Auswahl bestimmter Produktseiten nach Kategorie erfordert [CIF-Kernkomponenten der Version 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) oder neuer.

### Tiefe Verknüpfung {#specific-pages-deep-linking}

`UrlProvider` ist vorkonfiguriert, um Deep-Links zu bestimmten Kategorie- und Produktseiten in Instanzen der Autorenebene zu erzeugen. Diese Möglichkeit ist für Bearbeiter nützlich, die eine Site im Vorschaumodus durchsuchen, zu einer bestimmten Produkt- oder Kategorieseite navigieren und zurück in den Bearbeitungsmodus wechseln, um die Seite zu bearbeiten.

Auf Instanzen der Veröffentlichungsebene hingegen sollten Katalogseiten-URLs stabil bleiben, um beispielsweise Verbesserungen bei Suchmaschinen-Rankings nicht zu verlieren. Aufgrund dieser Veröffentlichungsstufe rendern Instanzen standardmäßig keine Deep-Links zu bestimmten Katalogseiten. Um dieses Verhalten zu ändern, muss die Variable _CIF-URL-Provider-spezifische Seitenstrategie_ kann so konfiguriert werden, dass immer bestimmte Seiten-URLs generiert werden.

### Mehrere Katalogseiten {#multiple-product-pages}

Wenn Editoren die vollständige Kontrolle über die Navigation einer Site auf oberster Ebene haben möchten, ist die Verwendung einer einzelnen Katalogseite zum Rendern der Kategorien auf oberster Ebene eines Katalogs möglicherweise nicht wünschenswert. Stattdessen können Editoren mehrere Katalogseiten erstellen, eine für jede Kategorie des Katalogs, den sie in die Navigation auf oberster Ebene aufnehmen möchten.

Für diesen Anwendungsfall kann jede Katalogseite einen Verweis auf eine Produkt- und Kategorieseite haben, die für die für die Katalogseite konfigurierte Kategorie spezifisch ist. Die `UrlProvider` verwendet diese Verbindungen, um Links für die Seiten und Kategorien in der konfigurierten Kategorie zu erstellen. Aus Leistungsgründen werden jedoch nur die direkt untergeordneten Katalogseiten des Navigationsstamms/der Landingpage einer Site berücksichtigt.

Es wird empfohlen, dass die Produkt- und Kategorieseiten einer Katalogseite dieser Katalogseite untergeordnet sind. Andernfalls funktionieren Komponenten wie die Navigation oder Breadcrumb möglicherweise nicht ordnungsgemäß.

>[!NOTE]
>
> Zur vollständigen Unterstützung für mehrere Katalogseiten sind die [CIF-Kernkomponenten 2.10.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0) oder neuer erforderlich.

## Anpassungen {#customization}

### Benutzerdefinierte URL-Formate {#custom-url-format}

Um ein benutzerdefiniertes URL-Format bereitzustellen, kann ein Projekt entweder die [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) oder [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) -Dienstschnittstelle verwenden und die Implementierung als OSGi-Dienst registrieren. Diese Implementierungen ersetzen, sofern verfügbar, das konfigurierte, vordefinierte Format. Wenn mehrere Implementierungen registriert sind, ersetzt die mit dem höheren Service-Rang die Implementierungen durch das niedrigere Service-Rang.

Die Implementierungen des benutzerdefinierten URL-Formats müssen ein Methodenpaar implementieren, um eine URL aus den angegebenen Parametern zu erstellen bzw. eine URL zu analysieren, um dieselben Parameter zurückzugeben.

### Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Zusätzlich zu den `UrlProvider`, ist es auch möglich, [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) , um URLs neu zu schreiben und zu verarbeiten. Das AEM Archetyp-Projekt bietet außerdem [Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) um einige Sling-Zuordnungen für Port 4503 (Veröffentlichung) und Port 80 (Dispatcher) zu konfigurieren.

### Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Neuschreibungen können auch mithilfe des AEM Dispatcher-HTTP-Servers mit dem Modul `mod_rewrite` erreicht werden. Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) stellt eine AEM Dispatcher-Referenzkonfiguration bereit, die bereits grundlegende [Neuschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Best Practices {#best-practices}

### Auswählen des besten URL-Formats {#choose-url-format}

Wie bereits erwähnt, hängt die Auswahl eines der verfügbaren Standardformate oder sogar die Implementierung eines benutzerdefinierten Formats stark von den Bedürfnissen und Anforderungen eines Stores ab. Die folgenden Vorschläge können dazu beitragen, eine fundierte Entscheidung zu treffen.

_**Verwenden Sie ein Produktseiten-URL-Format, das die SKU enthält.**_

Die CIF-Kernkomponenten verwenden die SKU als primäre Kennung in allen Komponenten. Wenn das URL-Format der Produktseite die SKU nicht enthält, ist eine GraphQL-Abfrage erforderlich, um sie zu beheben. Diese Auflösung kann sich auf das Time-to-First-Byte auswirken. Es kann auch gewünscht werden, dass Käufer Produkte von SKU mithilfe von Suchmaschinen finden können.

_**Verwenden Sie ein URL-Format für die Produktseite, das den Kategoriekontext enthält.**_

Einige Funktionen des CIF-URL-Anbieters sind nur verfügbar, wenn Produkt-URL-Formate verwendet werden, die den Kategoriekontext kodieren, z. B. die Kategorie `url_key` oder der Kategorie `url_path`. Auch wenn diese Funktionen für einen neuen Store möglicherweise nicht erforderlich sind, trägt die Verwendung eines dieser URL-Formate zu Beginn dazu bei, den Migrationsaufwand in Zukunft zu reduzieren.

_**Schaffen Sie ein Gleichgewicht zwischen URL-Länge und kodierten Informationen.**_

Je nach Kataloggröße, insbesondere Größe und Tiefe der Kategoriestruktur, ist es möglicherweise nicht sinnvoll, `url_path` mit den Kategorien in der URL vollständig zu kodieren. In diesem Fall kann die URL-Länge reduziert werden, indem nur der `url_key` anstatt. Diese Methode unterstützt die meisten Funktionen, die bei Verwendung der Kategorie verfügbar sind `url_path`.

Verwenden Sie außerdem [Sling-Zuordnungen](#sling-mapping) , um die SKU mit dem Produkt zu kombinieren `url_key`. In den meisten E-Commerce-Systemen folgt die SKU einem bestimmten Format und trennt die SKU von der `url_key` für eingehende Anfragen leicht möglich sein. Vor diesem Hintergrund sollte es möglich sein, eine Produktseiten-URL in `/p/{{category}}/{{sku}}-{{url_key}}.html`und einer Kategorie-URL zu `/c/{{url_key}}.html` bzw. Die `/p` und `/c` -Präfix ist weiterhin erforderlich, um Produkt- und Kategorieseiten von anderen Inhaltsseiten zu unterscheiden.

### Migration zu einem neuen URL-Format {#migrate-url-formats}

Viele der Standard-URL-Formate sind irgendwie miteinander kompatibel, d. h., durch eine URL formatierte URLs können durch eine andere analysiert werden. Dies hilft bei der Migration zwischen URL-Formaten.

Andererseits brauchen Suchmaschinen Zeit, um alle Katalogseiten mit dem neuen URL-Format neu zu durchsuchen. Um diesen Prozess zu unterstützen und auch das Endbenutzererlebnis zu verbessern, wird empfohlen, Umleitungen bereitzustellen, die den Benutzer von den alten URLs an die neuen weiterleiten.

Ein Ansatz dafür wäre, eine Staging-Umgebung mit dem E-Commerce-Backend der Produktion zu verbinden und sie so zu konfigurieren, dass sie das neue URL-Format verwendet. Beschaffen Sie sich anschließend die [Produkt-Sitemap, die von dem CIF-Produkt-Sitemap-Generator erzeugt wird](../../overview/seo-and-url-management.md), sowohl für die Staging- als auch für die Produktionsumgebung und verwenden Sie sie zum Erstellen einer [Apache-HTTPD-Umschreibungszuordnung](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). Diese Umschreibungszuordnung kann dann zusammen mit dem Rollout des neuen URL-Formats im Dispatcher bereitgestellt werden.

## Beispiel {#example}

Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren. Diese Konfiguration ermöglicht es jedem Projekt, individuelle URL-Muster für Produkt- und Kategorieseiten entsprechend ihren SEO-Anforderungen einzurichten. Es wird eine Kombination aus CIF-`UrlProvider` und Sling-Zuordnungen verwendet, wie oben beschrieben.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domain angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Host-Namens und der Domain. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Bereitstellung aktiviert werden. Benennen Sie dazu die Sling-Zuordnung um `hostname.adobeaemcloud.com` Ordner in `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domänennamen und aktivieren Sie diese Konfiguration durch Hinzufügen von `resource.resolver.map.location="/etc/map.publish"` der `JcrResourceResolver` Konfiguration des Projekts.

## Zusätzliche Ressourcen {#additional}

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [AEM-Ressourcenzuordnung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=de)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
