---
title: '''[!DNL Live Search] Komponente "CIF der Produktlistungsseite"'
description: Aktivieren von CIF Komponenten [!DNL Live Search] Komponente "Produktlistungsseite"auf einer AEM Site
source-git-commit: eaec541c191fc8f68d78662f2b6ab9140460aa9f
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# [!DNL Live Search] CIF Komponente {#live-search-cif-component}

Die Live-Suche für Adobe Commerce bietet ein schnelles, relevantes und intuitives Sucherlebnis ohne zusätzliche Kosten. Die von Adobe Sensei unterstützte Live-Suche verwendet künstliche Intelligenz und Algorithmen des maschinellen Lernens, um eine tiefgehende Analyse aggregierter Besucherdaten durchzuführen. Diese Daten führen in Kombination mit Ihrem Adobe Commerce-Katalog zu relevanten und personalisierten Einkaufserlebnissen.

Hier wird die Verwendung einer AEM CIF-Komponente zur Implementierung der [!DNL Live Search] Produkt-Listing-Seite (PLP) in Ihre AEM Site ein.

## Voraussetzungen {#prerequisites}

Bei diesem Thema wird davon ausgegangen, dass Sie über eine lokale [AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html?lang=de) einrichten.

Die PLP-Komponente erfordert die [[!DNL Live Search] Popover-CIF](live-search-popover.md) installiert werden. Für das PLP-Widget ist eine vom Popover generierte Browser-Sitzungsvariable erforderlich.

## Update Composer {#update-composer}

Hinzufügen von Ereignismodulen zu `ui.frontend/package.json`.

In Zeile 27 ändern Sie:

```json
...
  },

  "devDependencies": {

    "@babel/core": "^7.3.4",
...
```

in:

```json
...
  },
  "type": "module",
  "devDependencies": {
    "@adobe/magento-storefront-event-collector": "^1.5.4",
    "@adobe/magento-storefront-events-sdk": "^1.5.4",
    "@babel/core": "^7.3.4",
...
```

## Dateiänderungen {#files-changes}

Mehrere Dateien müssen aktualisiert werden, um [!DNL Live Search] Funktionalität. Bearbeiten Sie die folgenden Dateien. Die Zeilennummern unterscheiden sich möglicherweise geringfügig von den hier gezeigten.

* ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-cif/.content.xml

  Anhängen `core.cif.productlist.v1` der `embed` Linie.

  ```
  embed="[core.cif.components.common,core.cif.components.product.v3,core.cif.components.productcarousel.v1,core.cif.components.productcollection.v2,core.cif.components.productteaser.v1,core.cif.components.searchbar.v2,core.cif.components.header.v1,core.cif.components.carousel.v1,core.cif.components.categorycarousel.v1,core.cif.components.featuredcategorylist.v1,core.cif.components.storefront-events.v1,core.cif.components.extensions.product-recs.storefront-events-collector.v1,core.wcm.components.commons.site.link,core.cif.productlist.v1]"
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/.content.xml

  Datei erstellen `.content.xml`:

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
    jcr:primaryType="cq:ClientLibraryFolder"
    allowProxy="{Boolean}true"
    categories="[core.cif.productlist.v1]"
    jsProcessor="[default:none,min:none]"/>
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/css.txt

  Datei erstellen `css.txt`:

  ```text
  #base=css
  
  productlist.css
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/css/productlist.css

  Datei erstellen `productlist.css`

  ```css
    /* #search-plp-root */
  
  html {
    font-size: 62.5% !important;
  }
  
  body {
    font-size: 1.6rem;
  }
  
  .root.container {
    max-width: inherit;
  }
  
  .container {
    margin-left: auto;
    margin-right: auto;
  }
  
  div.ds-sdk-sort-dropdown {
    z-index: 9;
  }
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/js.txt

  Datei erstellen `js.txt`:

  ```text
  js/productlist.js
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/js/productlist.js

  Datei erstellen `productlist.js`:

  ```javascript
  /*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ~ Copyright 2023 Adobe
  ~
  ~ Licensed under the Apache License, Version 2.0 (the "License");
  ~ you may not use this file except in compliance with the License.
  ~ You may obtain a copy of the License at
  ~
  ~     http://www.apache.org/licenses/LICENSE-2.0
  ~
  ~ Unless required by applicable law or agreed to in writing, software
  ~ distributed under the License is distributed on an "AS IS" BASIS,
  ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  ~ See the License for the specific language governing permissions and
  ~ limitations under the License.
  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
  "use strict";
  
  class ProductList {
    constructor() {
      const stateObject = {
        categoryName: null,
        currentCategoryUrlPath: null,
      };
      this._state = stateObject;
      this._init();
    }
  
    _init() {
      this._initWidgetPLP();
    }
  
    _injectStoreScript(src) {
      const script = document.createElement("script");
      script.type = "text/javascript";
      script.src = src;
  
      document.head.appendChild(script);
    }
  
    async _getStoreData() {
      // get from session storage
      const sessionData = sessionStorage.getItem(
        "WIDGET_STOREFRONT_INSTANCE_CONTEXT"
      );
      // WIDGET_STOREFRONT_INSTANCE_CONTEXT is set from searchbar/clientlibs/js/searchbar.js
      // if not, we will need to retrieve from graphql separately here.
  
      if (sessionData) {
        this._state.dataServicesSessionContext = JSON.parse(sessionData);
        return;
      }
    }
  
    getStoreConfigMetadata() {
      const storeConfig = JSON.parse(
        document
          .querySelector("meta[name='store-config']")
          .getAttribute("content")
      );
  
      const { storeRootUrl } = storeConfig;
      const redirectUrl = storeRootUrl.split(".html")[0];
      return { storeConfig, redirectUrl };
    }
  
    async _initWidgetPLP() {
      if (!window.LiveSearchPLP) {
        const liveSearchPlpSrc =
          "https://plp-widgets-ui.magento-ds.com/v1/search.js";
        this._injectStoreScript(liveSearchPlpSrc);
        // wait until script is loaded
        await new Promise((resolve) => {
          const interval = setInterval(() => {
            if (window.LiveSearchPLP && window.LiveSearchAutocomplete) {
              // Widget expects LiveSearchAutocomplete already loaded to rely on data-service-graphql
              clearInterval(interval);
              resolve();
            }
          }, 200);
        });
      }
      await this._getStoreData();
      const { dataServicesSessionContext } = this._state;
      if (!dataServicesSessionContext) {
        console.log("no dataServicesSessionContext");
        return;
      }
  
      const root = document.getElementById("search-plp-root");
      if (!root) {
        console.log("plp root not found.");
        return;
      }
      // get dataset from root
      const categoryUrlPath = root.getAttribute("data-plp-urlPath") || "";
      const categoryName = root.getAttribute("data-plp-title") || "";
      const storeDetails = {
        environmentId: dataServicesSessionContext.environment_id,
        environmentType: dataServicesSessionContext.environment,
        apiKey: dataServicesSessionContext.api_key,
        websiteCode: dataServicesSessionContext.website_code,
        storeCode: dataServicesSessionContext.store_code,
        storeViewCode: dataServicesSessionContext.store_view_code,
        config: {
          pageSize: dataServicesSessionContext.page_size,
          perPageConfig: {
            pageSizeOptions: dataServicesSessionContext.page_size_options,
            defaultPageSizeOption:
              dataServicesSessionContext.default_page_size_option,
          },
          minQueryLength: dataServicesSessionContext.min_query_length,
          currencySymbol: dataServicesSessionContext.currency_symbol,
          currencyRate: dataServicesSessionContext.currency_rate,
          displayOutOfStock: dataServicesSessionContext.display_out_of_stock,
          allowAllProducts: dataServicesSessionContext.allow_all_products,
          locale: dataServicesSessionContext.locale,
          currentCategoryUrlPath: categoryUrlPath,
          categoryName,
          displayMode: "", // "" for plp || "PAGE" for category/catalog
        },
        context: {
          customerGroup: dataServicesSessionContext.customer_group,
        },
        route: ({ sku }) => {
          return `${
            this.getStoreConfigMetadata().redirectUrl
          }.cifproductredirect.html/${sku}`;
        },
        searchQuery: "search_query",
      };
      setTimeout(() => {
        console.log("init PLP");
        window.LiveSearchPLP({ storeDetails, root });
      }, 0);
    }
  }
  
  (function () {
    function onDocumentReady() {
      new ProductList({});
    }
  
    if (document.readyState !== "loading") {
      onDocumentReady();
    } else {
      document.addEventListener("DOMContentLoaded", onDocumentReady);
    }
  })();
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/productlist.html

  Datei erstellen `productlist.html`:

  ```html
  <div
  data-sly-use.productList="com.adobe.cq.commerce.core.components.models.productlist.ProductList"
  id="search-plp-root"
  class="productlist__root"
  data-plp-urlPath="${productList.storefrontContext.urlPath}"
  data-plp-title="${productList.title}">
  </div>
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/searchresults/.content.xml

  Bearbeiten `.content.xml` bei Zeile 6:

  ```xml
  sling:resourceSuperType="venia/components/commerce/productlist"
  ```

* ui.content/src/main/content/jcr_root/content/venia/language-masters/en/search/.content.xml

  Bearbeiten `.content.xml` in Zeile 21-22:

  ```xml
  sling:resourceType="venia/components/commerce/productlist"
  ```

* ui.content/src/main/content/jcr_root/content/venia/us/en/search/.content.xml

  Bearbeiten `.content.xml` in Zeile 26:

  ```xml
  sling:resourceType="venia/components/commerce/productlist"
  ```

* ui.frontend/src/main/components/App/App.js

  Bearbeiten `App.js` in Zeile 47, direkt über dem `../../site/main.scss`:

  ```javascript
  import '@adobe/magento-storefront-event-collector';
  ```

* ui.tests/test-module/specs/venia/productlist-dialog.js

  Bearbeiten `productlist-dialog.js` und ändern `describe` nach `describe.skip` in Zeile 20:

  ```javascript
  describe.skip('Product List Component Dialog', function () {
  ```

## Nicht-PLP-Seiten {#non-plp-pages}

Es kann einige Kategorien geben, in denen die Standardkategorie oder Katalogseite gewünscht wird, anstatt das PLP-Widget zu verwenden. In AEM müssen diese Kategorieseiten manuell konfiguriert werden.

1. Wählen Sie auf der Autorenseite eine Kategorieseitenvorlage aus. _Venia Store - Startseite_ > _Katalogseite_ > _Venia-Store - Kategorieseite_ und wählen Sie &quot;Look Shop the look&quot;oder erstellen Sie eine neue Seitenvorlage.

![Vorlage auswählen](../assets/cif-widget-1.jpg)

1. Klicken Sie auf _Eigenschaften_ und wählen Sie _Handel_ Registerkarte.

![Eigenschaften auswählen](../assets/cif-widget-2.jpg)

1. Wählen Sie die Kategorie aus, die mit der ausgewählten Kategorieseitenvorlage angezeigt werden soll.

![Kategorie auswählen](../assets/cif-widget-3.jpg)
