---
title: Benutzerdefinierte Attribute zum CIF von Produktkarussells
description: Erfahren Sie, wie Sie die AEM CIF Produktkarussell-Komponente erweitern, indem Sie das Sling-Modell aktualisieren und das Markup anpassen.
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 594f0e6ec88851c86134be8d5d7f1719f74ddf4f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Benutzerdefinierte Attribute zum CIF von Produktkarussells {#product-carousel}

## Einführung {#intro}

Die Komponente &quot;Karussell&quot;wurde in diesem Tutorial erweitert. Fügen Sie als ersten Schritt eine Instanz des Produktkarussells zur Startseite hinzu, um die Grundfunktionen zu verstehen:

1. Navigieren Sie zur Homepage der Site, z. B. [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)
1. Fügen Sie auf der Seite eine neue Komponente des Produktkarussells in den Haupt-Layout-Container ein.
   ![Komponente &quot;Produktkarussell&quot;](/help/commerce-cloud/assets/product-carousel-component.png)
1. Erweitern Sie das seitliche Bedienfeld (falls noch nicht umgeschaltet) und wechseln Sie im Dropdown-Menü für die Asset-Suche zu **Produkte**.
     ![Karussellprodukte](/help/commerce-cloud/assets/carousel-products.png)    
1. Dadurch sollte eine Liste der verfügbaren Produkte aus einer verbundenen Adobe Commerce-Instanz angezeigt werden.
   ![Connected Instance](/help/commerce-cloud/assets/connected-instance.png)
1. Produkte werden wie folgt mit Standardeigenschaften angezeigt:
   ![Produkt mit Eigenschaften angezeigt](/help/commerce-cloud/assets/discount.png)

## Sling-Modell aktualisieren {#update-sling-model}

Sie können die Geschäftslogik des Produktkarussells erweitern, indem Sie ein Sling-Modell implementieren:

1. Navigieren Sie in Ihrer IDE unter dem Kernmodul zu `core/src/main/java/com/venia/core/models/commerce` und erstellen Sie eine CustomCarousel-Oberfläche, die die CIF ProductCarousel-Oberfläche erweitert:

   ```
   package com.venia.core.models.commerce;
   import com.adobe.cq.commerce.core.components.models.productcarousel.ProductCarousel;
   public interface CustomCarousel extends ProductCarousel {
   }
   ```
1. Erstellen Sie anschließend eine Implementierungsklasse. `CustomCarouselImpl.java` at `core/src/main/java/com/venia/core/models/commerce/CustomCarouselImpl.java`.
Das Delegationsmuster für Sling-Modelle ermöglicht `CustomCarouselImpl` Verweis `ProductCarousel` -Modell über die `sling:resourceSuperType` Eigenschaft:

   ```
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductCarousel productCarousel;
   ```

1. Die @PostConstruct -Anmerkung stellt sicher, dass diese Methode aufgerufen wird, wenn das Sling-Modell initialisiert wird. Die GraphQL-Produktabfrage wurde bereits mit der Methode expandProductQueryWith erweitert, um Attribute abzurufen. Aktualisieren Sie die GraphQL-Abfrage, um das -Attribut in die partielle Abfrage einzuschließen:

   ```
   @PostConstruct
   private void initModel() {
   productsRetriever = productCarousel.getProductsRetriever();
   
   if(productCarousel.getProductsRetriever() != null)
   productCarousel.getProductsRetriever().extendProductQueryWith(p -> p
   .createdAt()
   .addCustomSimpleField("accessory_gemstone_addon")
   );
   }
   ```

   Im obigen Code wird die `addCustomSimpleField` wird verwendet, um die `accessory_gemstone_addon` -Attribut.

## Anpassen des Markups {#customize-markup}

So passen Sie das Markup weiter an:

1. Erstellen Sie eine Kopie von `productcard.html` von `/apps/core/cif/components/commerce/productcarousel/v1/productcarousel` (Kernkomponentencrxde-Pfad) zum Modul ui.apps `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productcarousel/productcard.html`.

1. Bearbeiten `productcard.html` um das benutzerdefinierte Attribut aufzurufen, das in der Implementierungsklasse erwähnt wird:

   ```xml
   ..
   <div
       data-product-sku="${product.commerceIdentifier.value}"
       data-product-base-sku="${product.combinedSku.baseSku}"
       id="${product.id}"
       data-cmp-data-layer="${product.data.json}"
       class="card product__card">
       <span>${product.product.responseData['accessory_gemstone_addon']}</span>
       <a href="${product.URL}"
           target="${productCarousel.linkTarget}"
   ..
   ```

1. Speichern Sie die Änderungen und stellen Sie die Aktualisierungen über Ihren Maven-Befehl in einem Befehlszeilen-Terminal auf AEM bereit. Sie können das benutzerdefinierte Attribut sehen `accessory_gemstone_addon` für die ausgewählten Produkte auf der Seite.
