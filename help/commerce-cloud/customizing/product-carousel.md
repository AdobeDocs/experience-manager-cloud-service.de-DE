---
title: Benutzerdefinierte Attribute zum CIF-Produktkarussell
description: Erfahren Sie, wie Sie die AEM CIF-Produktkarussellkomponente erweitern, indem Sie das Sling-Modell aktualisieren und das Markup anpassen.
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 758e0e13-c4d8-4d32-bcc9-91a36b3ffa98
source-git-commit: 11dfb2a69cd8e64c8105e5dd3945b0c341bcdf3b
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 100%

---

# Benutzerdefinierte Attribute zum CIF-Produktkarussell {#product-carousel}

## Einführung {#intro}

Die Produktkarussellkomponente wird im Laufe dieses Tutorials erweitert. Als ersten Schritt fügen Sie der Startseite eine Instanz des Produktkarussells hinzu, um sich mit den Grundfunktionen vertraut zu machen:

1. Navigieren Sie zur Startseite der Site, beispielsweise [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html).
1. Fügen Sie auf der Seite eine neue Produktkarussellkomponente in den Haupt-Layout-Container ein.
   ![Produktkarussellkomponente](/help/commerce-cloud/assets/product-carousel-component.png)
1. Erweitern Sie das seitliche Bedienfeld (falls noch nicht geschehen) und wechseln Sie im Dropdown-Menü der Asset-Suche zu **Produkte**.
 ![Karussell für Produkte](/help/commerce-cloud/assets/carousel-products.png)    
1. Nun sollte eine Liste mit verfügbaren Produkten einer verbundenen Adobe Commerce-Instanz angezeigt werden.
   ![Verbundene Instanz](/help/commerce-cloud/assets/connected-instance.png)
1. Produkte werden wie folgt mit Standardeigenschaften angezeigt:
   ![Angezeigtes Produkt mit Eigenschaften](/help/commerce-cloud/assets/discount.png)

## Aktualisieren des Sling-Modells {#update-sling-model}

Sie können die Geschäftslogik des Produktkarussells erweitern, indem Sie ein Sling-Modell implementieren:

1. Navigieren Sie in Ihrer IDE unter dem Kernmodul zu `core/src/main/java/com/venia/core/models/commerce` und erstellen Sie eine CustomCarousel-Oberfläche, die die CIF ProductCarousel-Oberfläche erweitert:

   ```
   package com.venia.core.models.commerce;
   import com.adobe.cq.commerce.core.components.models.productcarousel.ProductCarousel;
   public interface CustomCarousel extends ProductCarousel {
   }
   ```
1. Erstellen Sie anschließend eine Implementierungsklasse `CustomCarouselImpl.java` bei `core/src/main/java/com/venia/core/models/commerce/CustomCarouselImpl.java`.
Das Delegationsmuster für Sling-Modelle ermöglicht es `CustomCarouselImpl`, durch die Eigenschaft `sling:resourceSuperType` auf das Modell `ProductCarousel` zu verweisen:

   ```
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductCarousel productCarousel;
   ```

1. Die Anmerkung „@PostConstruct“ stellt sicher, dass diese Methode bei der Initialisierung des Sling-Modells aufgerufen wird. Die GraphQL-Produktabfrage wurde bereits mit der Methode „extendProductQueryWith“ erweitert, um Attribute abzurufen. Aktualisieren Sie die GraphQL-Abfrage, um das Attribut in die partielle Abfrage einzuschließen:

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

   Im obigen Code wird `addCustomSimpleField` zum Abrufen des Attributs `accessory_gemstone_addon` verwendet.

## Anpassen des Markups{#customize-markup}

Gehen Sie wie folgt vor, um das Markup weiter anzupassen:

1. Erstellen Sie eine Kopie von `productcard.html` aus `/apps/core/cif/components/commerce/productcarousel/v1/productcarousel` (CRXDE-Pfad der Kernkomponente) im ui.apps-Modul `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productcarousel/productcard.html`.

1. Bearbeiten Sie `productcard.html`, um das benutzerdefinierte Attribut aufzurufen, das in der Implementierungsklasse erwähnt wird:

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

1. Speichern Sie die Änderungen und stellen Sie die Aktualisierungen in AEM bereit. Verwenden Sie dazu Ihren Maven-Befehl in einem Befehlszeilen-Terminal. Sie können für die ausgewählten Produkte auf der Seite den Wert `accessory_gemstone_addon` des benutzerdefinierten Attributs sehen.
