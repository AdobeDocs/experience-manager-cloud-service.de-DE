---
title: Erweiterte URL-Konfigurationen
description: Informationen dazu, wie Sie die URLs für Produkt- und Kategorien-Seiten anpassen. Die Anpassung ermöglicht es, dass Implementierungen URLs für Suchmaschinen optimieren und ihr Auffinden fördern.
sub-product: Commerce
version: Experience Manager as a Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: ht
source-wordcount: '2059'
ht-degree: 100%

---

# Erweiterte URL-Konfigurationen {#url}

>[!NOTE]
>
> Suchmaschinenoptimierung (SEO) ist zu einem wichtigen Thema für viele Marketer geworden. Daher müssen SEO-Themen bei vielen Projekten in Adobe Experience Manager (AEM) as a Cloud Service berücksichtigt werden. Weitere Informationen finden Sie unter [Best Practices für SEO und URL-Verwaltung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/seo-and-url-management.html?lang=de).

Die [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) ermöglichen erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorieseiten. Bei vielen Implementierungen werden diese URLs zwecks Suchmaschinen-Optimierung (Search Engine Optimization, SEO) angepasst. Im folgenden Video wird beschrieben, wie Sie den `UrlProvider`-Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren können, um die URLs für Produkt- und Kategorieseiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/38581/?quality=12&captions=ger)

## Konfiguration {#configuration}

Um den `UrlProvider`-Service entsprechend den SEO-Anforderungen und -Bedürfnissen konfigurieren zu können, muss ein Projekt eine OSGi-Konfiguration für die _CIF-URL Provider-Konfiguration_ bereitstellen.

>[!NOTE]
>
> Seit Version 2.0.0 der CIF-Kernkomponenten von AEM bietet die URL-Provider-Konfiguration nur vordefinierte URL-Formate anstelle der von den Versionen 1.x bekannten, mit Freitext konfigurierbaren Formate. Darüber hinaus wurde die Verwendung von Selektoren zur Übergabe von Daten in URLs durch Suffixe ersetzt.

### URL-Format von Produktseiten {#product}

Konfiguriert die URLs der Produktseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (Standard)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

Wenn ein [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) vorhanden ist:

* `{{page}}` wird durch `/content/venia/us/en/products/product-page` ersetzt
* wird `{{sku}}` durch die Produkt-SKU ersetzt, z. B. `VP09`
* wird `{{url_key}}` wird durch die `url_key`-Eigenschaft des Produkts ersetzt, z. B. `lenora-crochet-shorts`
* wird `{{url_path}}` durch den `url_path` des Produkts ersetzt, z. B. `venia-bottoms/venia-pants/lenora-crochet-shorts`
* wird `{{variant_sku}}` wird durch die aktuell ausgewählte Variante ersetzt, z. B. `VP09-KH-S`

Da der `url_path` veraltet ist, verwenden die vordefinierten Formate für Produkt-URLs die `url_rewrites` eines Produkts und wählen das Format mit den meisten Pfadsegmenten als Alternative, wenn der `url_path` nicht verfügbar ist.

Mit den obigen Beispieldaten sieht eine mit dem Standard-URL-Format formatierte Produktvarianten-URL wie folgt aus: `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### URL-Format von Kategorieseiten {#product-list}

Konfiguriert die URLs der Kategorie- oder Produktlistenseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{url_path}}.html` (Standard)
* `{{page}}.html/{{url_key}}.html`

Wenn ein [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) vorhanden ist:

* `{{page}}` wird durch `/content/venia/us/en/products/category-page` ersetzt
* wird `{{url_key}}` durch die `url_key`-Eigenschaft der Kategorie ersetzt
* wird `{{url_path}}` durch den `url_path` der Kategorie ersetzt

Mit den obigen Beispieldaten sieht die URL einer Kategorieseite, die mit dem Standard-URL-Format formatiert ist, wie `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html` aus.

>[!NOTE]
> 
> Der `url_path` ist eine Verkettung aus dem `url_keys` der Vorgänger eines Produkts oder einer Kategorie und dem `url_key` des Produkts oder der Kategorie, getrennt durch einen Schrägstrich `/`. Jeder `url_key` wird innerhalb eines Stores als eindeutig betrachtet.

### Store-spezifische Konfiguration {#store-specific-urlformats}

Die systemweiten URL-Formate für Kategorien und Produktseiten, die in der _CIF-URL-Provider-Konfiguration_ festgelegt sind, können für jeden Store geändert werden.

In der CIF-Konfiguration können Redakteurinnen und Redakteure ein alternatives URL-Format für Produkt- oder Kategorieseiten auswählen. Wenn dort nichts ausgewählt ist, wird bei der Implementierung auf die systemweite Konfiguration zurückgegriffen.

Eine Änderung des URL-Formats einer Live-Website kann sich negativ auf den organischen Traffic Ihrer Site auswirken. Bitte beachten Sie die [Best Practices](#best-practices) unten und planen Sie die Änderung des URL-Formats sorgfältig im Voraus.

![URL-Formate in der CIF-Konfiguration](assets/store-specific-url-formats.png)

>[!NOTE]
>
> Die Store-spezifische Konfiguration der URL-Formate erfordert [CIF-Kernkomponenten 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) und die neueste Version des Add-ons „Content and Commerce“ zu Adobe Experience Manager.

## Kategoriesensitive Produktseiten-URLs {#context-aware-pdps}

Da Kategorieinformationen in einer Produkt-URL codiert werden können, können Produkte, die sich in mehreren Kategorien befinden, auch durch mehrere Produkt-URLs adressiert werden.

Die Standard-URL-Formate wählen eine der möglichen Alternativen nach dem folgenden Schema aus:

* wenn der `url_path` durch das E-Commerce-Backend definiert wird, wird dieser verwendet (nicht mehr unterstützt)
* von den `url_rewrites` werden diejenigen URLs, die mit dem `url_key` des Produkts enden, als Alternativen verwendet
* von diesen Alternativen wird die mit den meisten Pfadsegmenten verwendet
* wenn mehrere vorhanden sind, wird die erste in der Reihenfolge genommen, die vom E-Commerce-Backend angegeben wird.

Bei diesem Schema wird der `url_path` mit den meisten Vorgängern ausgewählt, basierend auf der Annahme, dass eine untergeordnete Kategorie spezifischer ist als ihre übergeordnete Kategorie. Der ausgewählte `url_path` gilt als _kanonisch_ und wird immer für den kanonischen Link auf Produktseiten oder in der Produkt-Sitemap verwendet.

Wenn eine Käuferin oder ein Käufer jedoch von einer Kategorieseite zu einer Produktseite oder von einer Produktseite zu einer anderen zugehörigen Produktseite in derselben Kategorie navigiert, empfiehlt es sich, den aktuellen Kategoriekontext beizubehalten. In diesem Fall sollte die Auswahl des `url_path` Alternativen bevorzugen, die innerhalb des aktuellen Kategoriekontextes liegen, anstelle der oben beschriebenen _kanonischen_ Auswahl.

Diese Funktion muss in der _CIF-URL-Provider-Konfiguration_ aktiviert werden. Wenn die Auswahl aktiviert ist, werden Alternativen höher bewertet, wenn

* sie mit Teilen des `url_path` einer bestimmten Kategorie von Anfang an übereinstimmen (unscharfer Präfixabgleich)
* oder sie mit dem `url_key` einer bestimmten Kategorie an beliebiger Stelle (exakter Teilabgleich) übereinstimmen.

Betrachten Sie beispielsweise die Antwort für eine [Produktabfrage](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) unten. Angenommen, es gibt folgenden Fall:

* Jemand befindet sich auf der Kategorieseite „Neue Produkte/Neu im Sommer 2022“.
* der Store verwendet das standardmäßige URL-Format für Kategorieseiten

Die Alternative „neue-produkte/neu-im-sommer-2022/goldene-kreisförmige-Ohrringe.html“ entspricht von Anfang an zweien der Pfadsegmente des Kontexts. Das sind „neue-produkte“ und „neu-im-sommer-2022“. Wenn der Store ein URL-Format für Kategorieseiten verwendet, das nur den `url_key` der Kategorie enthält, wird dieselbe Alternative weiterhin ausgewählt, da sie überall zum `url_key` passt. In beiden Fällen wird die URL der Produktseite für den `url_path` „neue-produkte/neu-im-sommer-2022/goldene-kreisförmige-ohrringe.html“ erstellt.

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

Es ist möglich, [Mehrkategorien- und Produktseiten](../authoring/multi-template-usage.md) nur für eine bestimmte Untermenge von Kategorien oder Produkten eines Katalogs zu erstellen.

### Auswahlkriterien {#specific-pages-selection}

Die Auswahl einer bestimmten Kategorieseite versteht sich von selbst, basierend auf dem `url_path` oder `url_key` der Kategorie. Die Abgleichung für Unterkategorien wird nur für URL-Formate unterstützt, die den vollständigen `url_path` der Kategorie enthalten. Andernfalls ist nur eine exakte Übereinstimmung mit dem `url_key` möglich.

Spezifische Produktseiten werden entweder nach SKU oder nach Kategorie des Produkts ausgewählt. Für die letztere müssen bestimmte Kategorieinformationen in der Produkt-URL codiert sein. Dies ist nur für einige der standardmäßigen URL-Formate verfügbar. In der folgenden Tabelle finden Sie einen Vergleich, der angibt, welches URL-Format eine bestimmte Seitenauswahl nach SKU oder Kategorie unterstützt.


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

`UrlProvider` ist vorkonfiguriert, um Deep-Links zu bestimmten Kategorie- und Produktseiten in Instanzen der Authoring-Ebene zu erzeugen. Dies ist für Redaktionsmitglieder nützlich, die eine Site im Vorschaumodus durchsuchen, zu einer bestimmten Produkt- oder Kategorieseite navigieren und zurück in den Bearbeitungsmodus wechseln, um die Seite zu bearbeiten.

Auf Instanzen der Veröffentlichungsebene hingegen sollten Katalogseiten-URLs stabil bleiben, um beispielsweise Verbesserungen bei Suchmaschinen-Rankings nicht zu verlieren. Deshalb rendern Instanzen der Publishing-Ebene standardmäßig keine Deep-Links von bestimmten Katalogseiten. Um dieses Verhalten zu ändern, kann die _spezifische Seitenstrategie des CIF-URL-Providers_ so konfiguriert werden, dass immer bestimmte Seiten-URLs erzeugt werden.

### Mehrere Katalogseiten {#multiple-product-pages}

Wenn Redaktionsmitglieder die vollständige Kontrolle über die Navigation einer Site auf oberster Ebene haben möchten, ist die Verwendung einer einzelnen Katalogseite zum Rendern der Kategorien auf oberster Ebene eines Katalogs möglicherweise nicht wünschenswert. Stattdessen können Redaktionsmitglieder mehrere Katalogseiten erstellen, nämlich eine für jede Kategorie des Katalogs, die sie in die Navigation auf oberster Ebene aufnehmen möchten.

Für diesen Anwendungsfall kann jede der Katalogseiten einen Verweis auf eine Produkt- und Kategorieseite haben, die spezifisch für die Kategorie ist, die für die Katalogseite konfiguriert wurde. Der `UrlProvider` verwendet diese Verbindungen zum Erstellen von Links für die Seiten und Kategorien in der konfigurierten Kategorie. Aus Leistungsgründen werden jedoch nur die direkt untergeordneten Katalogseiten des Navigationsstamms/der Landingpage einer Site berücksichtigt.

Es wird empfohlen, dass die Produkt- und Kategorieseiten einer Katalogseite dieser Katalogseite untergeordnet sind. Andernfalls funktionieren Komponenten wie die Navigation oder Breadcrumb möglicherweise nicht ordnungsgemäß.

>[!NOTE]
>
> Zur vollständigen Unterstützung für mehrere Katalogseiten sind die [CIF-Kernkomponenten 2.10.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0) oder neuer erforderlich.

## Anpassungen {#customization}

### Benutzerdefinierte URL-Formate {#custom-url-format}

Um ein benutzerdefiniertes URL-Format bereitzustellen, kann ein Projekt die Service-Schnittstelle [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) oder [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) implementieren und die Implementierung als OSGi-Service registrieren. Diese Implementierungen ersetzen das konfigurierte, vordefinierte Format, sofern verfügbar. Wenn mehrere Implementierungen registriert sind, ersetzt die Implementierung mit dem höheren Service-Ranking die mit dem niedrigeren Service-Ranking.

Die Implementierungen des benutzerdefinierten URL-Formats müssen ein Methodenpaar implementieren, um eine URL aus den angegebenen Parametern zu erstellen bzw. eine URL zu analysieren, um dieselben Parameter zurückzugeben.

### Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Neben `UrlProvider` können auch [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfiguriert werden, um URLs neu zu schreiben und zu verarbeiten. Das AEM-Archetypen-Projekt bietet außerdem [eine Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) zum Konfigurieren einiger Sling-Zuordnungen für Port 4503 (Veröffentlichung) und Port 80 (Dispatcher).

### Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Neuschreibungen können auch mithilfe des AEM Dispatcher-HTTP-Servers mit dem Modul `mod_rewrite` erreicht werden. Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) stellt eine AEM Dispatcher-Referenzkonfiguration bereit, die bereits grundlegende [Neuschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Best Practices {#best-practices}

### Auswählen des besten URL-Formats {#choose-url-format}

Wie bereits erwähnt, hängt die Auswahl eines der verfügbaren Standardformate oder sogar die Implementierung eines benutzerdefinierten Formats stark von den Bedürfnissen und Anforderungen eines Stores ab. Die folgenden Vorschläge können dabei helfen, eine fundierte Entscheidung zu treffen.

_**Verwenden Sie ein URL-Format für die Produktseite, das die SKU enthält.**_

Die CIF-Kernkomponenten verwenden die SKU als primäre Kennung in allen Komponenten. Wenn das URL-Format der Produktseite die SKU nicht enthält, ist eine GraphQL-Abfrage erforderlich, um sie aufzulösen. Diese Auflösung kann sich auf die Time-to-First-Byte auswirken. Es kann auch gewünscht sein, dass Käuferinnen und Käufer Produkte nach SKU mithilfe von Suchmaschinen finden können.

_**Verwenden Sie ein URL-Format für die Produktseite, das den Kategoriekontext enthält.**_

Einige Funktionen des CIF-URL-Providers sind nur verfügbar, wenn Produkt-URL-Formate verwendet werden, die den Kategoriekontext codieren, z. B. den `url_key` oder den `url_path` der Kategorie. Auch wenn diese Funktionen für einen neuen Store möglicherweise nicht erforderlich sind, trägt die Verwendung eines dieser URL-Formate zu Beginn dazu bei, den Migrationsaufwand in Zukunft zu reduzieren.

_**Schaffen Sie ein Gleichgewicht zwischen URL-Länge und kodierten Informationen.**_

Je nach Kataloggröße, insbesondere Größe und Tiefe der Kategoriestruktur, ist es möglicherweise nicht sinnvoll, `url_path` mit den Kategorien in der URL vollständig zu kodieren. In diesem Fall kann die URL-Länge durch Einbeziehen des `url_key` der Kategorie reduziert werden. Mit dieser Methode werden fast alle Funktionen unterstützt, die bei Verwendung des `url_path` der Kategorie verfügbar sind.

Verwenden Sie außerdem [Sling-Zuordnungen](#sling-mapping), um die SKU mit dem `url_key` des Produkts zu kombinieren. In den meisten E-Commerce-Systemen folgt die SKU einem bestimmten Format, und das Trennen der SKU vom `url_key` sollte für eingehende Anfragen leicht möglich sein. Vor diesem Hintergrund sollte es möglich sein, eine Produktseiten-URL als `/p/{{category}}/{{sku}}-{{url_key}}.html` bzw. eine Kategorie-URL als `/c/{{url_key}}.html` neu zu schreiben. Die Präfixe `/p` und `/c` sind weiterhin erforderlich, um Produkt- und Kategorieseiten von anderen Inhaltsseiten zu unterscheiden.

### Migration zu einem neuen URL-Format {#migrate-url-formats}

Viele der standardmäßigen URL-Formate sind in gewisser Weise miteinander kompatibel, d. h. URLs, die in einem der Formate erstellt wurden, können von einem anderen interpretiert werden. Dies hilft bei der Migration zwischen URL-Formaten.

Andererseits benötigen Suchmaschinen etwas Zeit, um alle Katalogseiten mit dem neuen URL-Format erneut zu durchsuchen. Um diesen Prozess zu unterstützen und auch das Endbenutzererlebnis zu verbessern, wird empfohlen, Umleitungen bereitzustellen, die Benutzerinnen und Benutzer von den alten URLs an die neuen weiterleiten.

Ein Ansatz dafür wäre, eine Staging-Umgebung mit dem E-Commerce-Backend der Produktion zu verbinden und sie so zu konfigurieren, dass sie das neue URL-Format verwendet. Beschaffen Sie sich anschließend die [Produkt-Sitemap, die von dem CIF-Produkt-Sitemap-Generator erzeugt wird](../../overview/seo-and-url-management.md), sowohl für die Staging- als auch für die Produktionsumgebung und verwenden Sie sie zum Erstellen einer [Apache-HTTPD-Umschreibungszuordnung](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). Diese Umschreibungszuordnung kann zusammen mit dem Rollout des neuen URL-Formats für den Dispatcher bereitgestellt werden.

## Beispiel {#example}

Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren. Mit dieser Konfiguration können für jedes Projekt individuelle URL-Strukturen für Produkt- und Kategorieseiten entsprechend den SEO-Anforderungen eingerichtet werden. Es wird eine Kombination aus CIF-`UrlProvider` und Sling-Zuordnungen verwendet, wie oben beschrieben.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domain angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Host-Namens und der Domain. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Bereitstellung aktiviert werden. Benennen Sie dazu den Sling-Zuordnungsordner `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domain-Namen um und aktivieren Sie diese Konfiguration, indem Sie `resource.resolver.map.location="/etc/map.publish"` zur `JcrResourceResolver`-Konfiguration des Projekts hinzufügen.

## Zusätzliche Ressourcen {#additional}

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [AEM-Ressourcenzuordnung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=de)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
