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
source-git-commit: af07bce8618c7b13b4dc5e287c7218316029f565
workflow-type: tm+mt
source-wordcount: '2039'
ht-degree: 80%

---

# Erweiterte URL-Konfigurationen {#url}

>[!NOTE]
>
> Suchmaschinenoptimierung (SEO) ist zu einem wichtigen Thema für viele Marketer geworden. Daher müssen SEO-Themen bei vielen Adobe Experience Manager (AEM) as a Cloud Service-Projekten berücksichtigt werden. Weitere Informationen finden Sie unter [Best Practices für SEO und URL-Verwaltung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/seo-and-url-management.html?lang=de).

Die [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) ermöglichen erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorieseiten. Viele Implementierungen passen diese URLs für die Suchmaschinenoptimierung (SEO) an. Im folgenden Video wird beschrieben, wie Sie den `UrlProvider`-Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren können, um die URLs für Produkt- und Kategorieseiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Konfiguration {#configuration}

Um den `UrlProvider`-Service entsprechend den SEO-Anforderungen und -Bedürfnissen konfigurieren zu können, muss ein Projekt eine OSGI-Konfiguration für die _CIF URL Provider-Konfiguration_ bereitstellen.

>[!NOTE]
>
> Seit Version 2.0.0 der CIF-Kernkomponenten von AEM bietet die URL-Provider-Konfiguration nur vordefinierte URL-Formate anstelle der von den Versionen 1.x bekannten, mit Freitext konfigurierbaren Formate. Darüber hinaus wurde die Verwendung von Selektoren zur Übergabe von Daten in URLs durch Suffixe ersetzt.

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

Da der `url_path` veraltet ist, verwenden die vordefinierten Formate für Produkt-URLs die `url_rewrites` eines Produkts und wählen unter ihnen das Format mit den meisten Pfadsegmenten als Alternative, wenn der `url_path` nicht verfügbar ist.

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
> Der `url_path` ist eine Verkettung aus dem `url_keys` der Vorgänger eines Produkts oder einer Kategorie und dem `url_key` des Produkts oder der Kategorie, getrennt durch einen Schrägstrich `/`. Jeder `url_key` wird innerhalb eines Stores als eindeutig betrachtet.

### Store-spezifische Konfiguration {#store-specific-urlformats}

Die systemweiten URL-Formate für Kategorien und Produktseiten, die in der _CIF-URL-Provider-Konfiguration_ festgelegt sind, können für jeden Shop geändert werden.

In der CIF-Konfiguration kann ein Editor ein alternatives URL-Format für Produkt- oder Kategorieseiten auswählen. Wenn dort nichts ausgewählt ist, wird bei der Implementierung auf die systemweite Konfiguration zurückgegriffen.

Eine Änderung des URL-Formats einer Live-Website kann sich negativ auf den organischen Traffic Ihrer Site auswirken. Bitte beachten Sie die [Best Practices](#best-practices) unten und planen Sie die Änderung des URL-Formats sorgfältig im Voraus.

![URL-Formate in der CIF-Konfiguration](assets/store-specific-url-formats.png)

>[!NOTE]
>
> Die Store-spezifische Konfiguration der URL-Formate erfordert [CIF-Kernkomponenten 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) und die neueste Version des Add-ons „Content and Commerce“ zu Adobe Experience Manager.

## Kategoriebezogene Produktseiten-URLs {#context-aware-pdps}

Da Kategorieinformationen in einer Produkt-URL codiert werden können, können Produkte, die sich in mehreren Kategorien befinden, auch durch mehrere Produkt-URLs adressiert werden.

Die Standard-URL-Formate wählen eine der möglichen Alternativen mithilfe des folgenden Schemas aus:

* wenn der `url_path` durch das E-Commerce-Backend definiert wird, wird dieser verwendet (nicht mehr unterstützt)
* von den `url_rewrites` werden diejenigen URLs, die mit dem `url_key` des Produkts enden, als Alternativen verwendet
* von diesen Alternativen wird die mit den meisten Pfadsegmenten verwendet
* wenn mehrere vorhanden sind, wird die erste in der Reihenfolge genommen, die vom E-Commerce-Backend angegeben wird.

Im Rahmen dieser Regelung wird `url_path` mit den meisten Vorgängern, basierend auf der Annahme, dass eine untergeordnete Kategorie spezifischer ist als die übergeordnete Kategorie. Die so ausgewählte `url_path` wird _kanonisch_ und wird immer als kanonischer Link auf Produktseiten oder in der Produkt-Sitemap verwendet.

Wenn ein Käufer jedoch von einer Kategorieseite zu einer Produktseite oder von einer Produktseite zu einer anderen zugehörigen Produktseite in derselben Kategorie navigiert, empfiehlt es sich, den aktuellen Kategoriekontext beizubehalten. In diesem Fall sollte die Auswahl des `url_path` Alternativen, die innerhalb des aktuellen Kategoriekontextes liegen, anstelle der oben beschriebenen _kanonischen_ Auswahl bevorzugen.

Diese Funktion muss in der _CIF-URL-Provider-Konfiguration_ aktiviert werden. Wenn die Auswahl aktiviert ist, werden Alternativen höher bewertet, wenn

* sie stimmen mit Teilen der `url_path` von Anfang an (Fuzzy-Präfixabgleich)
* oder sie mit der `url_key` an beliebiger Stelle (exakter Teilabgleich)

Betrachten Sie beispielsweise die Antwort für eine [Produktabfrage](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) unten. Wenn sich der Benutzer auf der Kategorieseite &quot;Neue Produkte/Neu im Sommer 2022&quot;befindet und der Store das standardmäßige Kategorieseiten-URL-Format verwendet, würde die Alternative &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;von Anfang an mit 2 der Pfadsegmente des Kontexts übereinstimmen: &quot;new-products&quot;und &quot;new-in-summer-2022&quot;. Wenn der Store ein Kategorieseiten-URL-Format verwendet, das nur die Kategorie enthält `url_key`, wird dieselbe Alternative weiterhin ausgewählt, da sie mit der `url_key` überall. In beiden Fällen wird die URL der Produktseite mit dem `url_path` „new-products/new-in-summer-2022/gold-cirque-earrings.html“ erstellt.

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

Es ist möglich, [mehrere Kategorie- und Produktseiten](../authoring/multi-template-usage.md) für nur eine bestimmte Untermenge von Kategorien oder Produkten eines Katalogs zu erstellen.

### Auswahlkriterien {#specific-pages-selection}

Die Auswahl einer bestimmten Kategorieseite versteht sich von selbst, basierend auf dem `url_path` oder `url_key` der Kategorie. Die Abgleichung für Unterkategorien wird nur für URL-Formate unterstützt, die den vollständigen `url_path` der Kategorie enthalten. Andernfalls ist nur eine exakte Übereinstimmung mit dem `url_key` möglich.

Spezifische Produktseiten werden entweder nach Produktnummer oder nach Kategorie des Produkts ausgewählt. Für die letztere müssen bestimmte Kategorieinformationen in der Produkt-URL codiert werden. Dies ist nur für einige der standardmäßigen URL-Formate verfügbar. In der folgenden Tabelle finden Sie einen Vergleich, welches URL-Format die spezifische Seitenauswahl nach Produktnummer oder Kategorie unterstützt.


| URL-Format | nach Produktnummer | nach Kategorie |
| ----------------------------------------------------- | ------ | ---------------- |
| `{{page}}.html/{{url_key}}.html` | nein | nein |
| `{{page}}.html/{{category}}/{{url_key}}.html` | nein | Nur exakte Übereinstimmung |
| `{{page}}.html/{{url_path}}.html` | nein | ja |
| `{{page}}.html/{{sku}}.html` | ja | nein |
| `{{page}}.html/{{sku}}/{{url_key}}.html` | ja | nein |
| `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html` | ja | Nur exakte Übereinstimmung |
| `{{page}}.html/{{sku}}/{{url_path}}.html` | ja | ja |

{style=&quot;table-layout:auto&quot;}

>[!NOTE]
>
> Die Auswahl bestimmter Produktseiten nach Kategorie erfordert [CIF-Kernkomponenten der Version 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) oder neuer.

### Tiefe Verknüpfung {#specific-pages-deep-linking}

`UrlProvider` ist vorkonfiguriert, um Deep-Links zu bestimmten Kategorie- und Produktseiten in Instanzen der Autorenebene zu erzeugen. Dies ist für Editoren nützlich, die eine Site im Vorschaumodus durchsuchen, zu einer bestimmten Produkt- oder Kategorieseite navigieren und zurück in den Bearbeitungsmodus wechseln, um die Seite zu bearbeiten.

Auf Instanzen der Veröffentlichungsebene hingegen sollten Katalogseiten-URLs stabil bleiben, um beispielsweise Verbesserungen bei Suchmaschinen-Rankings nicht zu verlieren. Deshalb rendern Instanzen der Veröffentlichungsebene standardmäßig keine Deep-Links von bestimmten Katalogseiten. Um dieses Verhalten zu ändern, kann die Variable für die _spezifische Seitenstrategie des CIF-URL-Providers_ so konfiguriert werden, dass immer bestimmte Seiten-URLs erzeugt werden.

## Anpassungen {#customization}

### Benutzerdefinierte URL-Formate {#custom-url-format}

Um ein benutzerdefiniertes URL-Format bereitzustellen, kann ein Projekt die Service-Schnittstelle [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) oder [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) implementieren und die Implementierung als OSGi-Service registrieren. Diese Implementierungen ersetzen das konfigurierte, vordefinierte Format, sofern verfügbar. Wenn mehrere Implementierungen registriert sind, ersetzt die Implementierung mit dem höheren Serviceranking die Implementierung(en) mit dem niedrigeren Serviceranking.

Die Implementierungen des benutzerdefinierten URL-Formats müssen ein Methodenpaar implementieren, um eine URL aus den angegebenen Parametern zu erstellen bzw. eine URL zu analysieren, um dieselben Parameter zurückzugeben.

### Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Neben `UrlProvider` können auch [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfiguriert werden, um URLs neu zu schreiben und zu verarbeiten. Das AEM-Archetyp-Projekt bietet außerdem [eine Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) zum Konfigurieren einiger Sling-Zuordnungen für Port 4503 (Veröffentlichungsinstanz) und Port 80 (Dispatcher).

### Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Neuschreibungen können auch mithilfe des AEM Dispatcher-HTTP-Servers mit dem Modul `mod_rewrite` erreicht werden. Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) stellt eine AEM Dispatcher-Referenzkonfiguration bereit, die bereits grundlegende [Neuschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Best Practices {#best-practices}

### Das beste URL-Format auswählen {#choose-url-format}

Wie bereits vor Auswahl eines der verfügbaren Standardformate oder sogar vor der Implementierung eines benutzerdefinierten Formats erwähnt, hängt in hohem Maße von den Anforderungen und Anforderungen eines Stores ab. Die folgenden Vorschläge können dabei helfen, eine fundierte Entscheidung zu treffen.

_**Verwenden Sie ein URL-Format für die Produktseite, das die SKU enthält.**_

Die CIF-Kernkomponenten verwenden die SKU als primäre Kennung in allen Komponenten. Wenn das URL-Format der Produktseite die SKU nicht enthält, ist eine GraphQL-Abfrage erforderlich, um sie zu beheben. Dies kann sich auf das Time-to-First-Byte auswirken. Es kann auch gewünscht werden, dass Käufer Produkte mithilfe von Suchmaschinen finden können.

_**Verwenden Sie ein URL-Format für die Produktseite, das den Kategoriekontext enthält.**_

Einige Funktionen des CIF-URL-Anbieters sind nur verfügbar, wenn Produkt-URL-Formate verwendet werden, die den Kategoriekontext kodieren, z. B. die Kategorie `url_key` oder der Kategorie `url_path`. Auch wenn diese Funktionen für einen neuen Store möglicherweise nicht erforderlich sind, trägt die Verwendung eines dieser URL-Formate am Anfang dazu bei, den Migrationsaufwand in Zukunft zu reduzieren.

_**Schaffen Sie ein Gleichgewicht zwischen URL-Länge und kodierten Informationen.**_

Je nach Kataloggröße, insbesondere Größe und Tiefe der Kategoriestruktur, ist es möglicherweise nicht sinnvoll, `url_path` mit den Kategorien in der URL vollständig zu kodieren. In diesem Fall kann die URL-Länge reduziert werden, indem nur die Kategorie `url_key` anstatt. Dies unterstützt die meisten Funktionen, die bei Verwendung der Kategorie verfügbar sind `url_path`.

Nutzen Sie außerdem [Sling-Zuordnungen](#sling-mapping), um die SKU mit `url_key` des Produkts zu kombinieren. In den meisten E-Commerce-Systemen folgt die SKU einem bestimmten Format und trennt die SKU von der `url_key` für eingehende Anfragen leicht möglich sein. Vor diesem Hintergrund sollte es möglich sein, eine Produktseiten-URL als `/p/{{category}}/{{sku}}-{{url_key}}.html` bzw. eine Kategorie-URL als `/c/{{url_key}}.html` neu zu schreiben. Die Präfixe `/p` und `/c` sind weiterhin erforderlich, um Produkt- und Kategorieseiten von anderen Inhaltsseiten zu unterscheiden.

### Migration zu einem neuen URL-Format {#migrate-url-formats}

Viele der Standard-URL-Formate sind in gewisser Weise miteinander kompatibel, d. h. URLs, die in einem der Formate erstellt wurden, können von einem anderen interpretiert werden. Dies hilft bei der Migration zwischen URL-Formaten.

Andererseits benötigen Suchmaschinen etwas Zeit, um alle Katalogseiten mit dem neuen URL-Format erneut zu durchsuchen. Um diesen Prozess zu unterstützen und auch das Endbenutzererlebnis zu verbessern, wird empfohlen, Umleitungen bereitzustellen, die den Benutzer von den alten URLs an die neuen weiterleiten.

Ein Ansatz dafür könnte sein, eine Staging-Umgebung mit dem Produktions-E-Commerce-Backend zu verbinden und es so zu konfigurieren, dass es das neue URL-Format verwendet. Rufen Sie anschließend die [Produkt-Sitemap, die von dem CIF-Produkt-Sitemap-Generator generiert wird](../../overview/seo-and-url-management.md) sowohl für die Staging- als auch für die Produktionsumgebung und verwenden Sie sie zum Erstellen einer [Apache httpd-Rewrite-Zuordnung](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). Diese Umschreibungszuordnung kann zusammen mit dem Rollout des neuen URL-Formats für den Dispatcher bereitgestellt werden.

## Beispiel {#example}

Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren. So können für jedes Projekt individuelle URL-Strukturen für Produkt- und Kategorieseiten entsprechend den SEO-Anforderungen eingerichtet werden. Es wird eine Kombination aus CIF-`UrlProvider` und Sling-Zuordnungen verwendet, wie oben beschrieben.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domain angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Host-Namens und der Domain. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Implementierung aktiviert werden. Benennen Sie dazu den Ordner `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domain-Namen um und aktivieren Sie diese Konfiguration, indem Sie `resource.resolver.map.location="/etc/map.publish"` zur `JcrResourceResolver`-Konfiguration des Projekts hinzufügen.

## Zusätzliche Ressourcen {#additional}

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [AEM-Ressourcenzuordnung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=de)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
