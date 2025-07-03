---
title: JSON-LD-Metadaten
description: Erfahren Sie, wie Sie die JSON+LD-Funktion in AEM CIF aktivieren und überprüfen.
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 547d3721-e094-4a42-8a7c-27e4ef97ea9c
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 100%

---

# JSON-LD-Metadaten {#json-ld}

In diesem Handbuch wird erläutert, wie Sie die JSON+LD-Funktion in AEM CIF aktivieren und überprüfen.

>[!NOTE]
>
> Diese Funktion ist experimentell.

## Aktivieren von JSON+LD in der CIF-Konfiguration {#enabling}

Standardmäßig ist das Kontrollkästchen **JSON+LD aktivieren** in der CIF-Konfiguration nicht sichtbar. Um diese Funktion zu aktivieren, muss das Projekt die erforderliche OSGi-Konfiguration enthalten, mit der das Kontrollkästchen angezeigt werden kann. Diese Konfiguration ermöglicht es Benutzenden, die Unterstützung von JSON+LD-Skripten auf Produktseiten ein- oder auszuschalten.
Um das Kontrollkästchen **JSON+LD aktivieren** in der CIF-Konfiguration verfügbar zu machen, fügen Sie die folgende OSGi-Konfiguration zu Ihrem Projekt hinzu: `
com.adobe.cq.cif.components.models.JsonLdFeatureEnable`.
Weitere Informationen zum Hinzufügen dieser Konfiguration finden Sie unter [Hinzufügen der Konfiguration für JSON-LD](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.cif.components.models.JsonLdFeatureEnable.cfg.json) im öffentlichen Repository „aem-cif-guides-venia“.

Sobald diese Konfiguration hinzugefügt und bereitgestellt wurde, wird das Kontrollkästchen in den CIF-Konfigurationseinstellungen angezeigt. Im Folgenden finden Sie die Schritte zum Aktivieren von **JSON+LD**:

1. Navigieren Sie zur CIF-Konfiguration in AEM.
1. Brechen Sie die Vererbung ab.
1. Aktivieren Sie das Kontrollkästchen **JSON+LD aktivieren**.
1. Speichern Sie die Konfiguration.

## Überprüfen von JSON+LD auf einer Produktdetailseite (Product Detail Page, PDP) {#verify}

Um die Schritte zur Überprüfung von JSON+LD zu veranschaulichen, wird das Venia-Projekt als Beispiel verwendet, bei dem die erforderliche JSON+LD-Konfiguration bereits hinzugefügt wurde, um die Funktion zu aktivieren. Die folgenden Schritte sind zu befolgen:

1. Navigieren Sie zu Ihrer lokalen AEM-Instanz und öffnen Sie die Produktdetailseite (PDP): http://localhost:4502/editor.html/content/venia/us/en/products/product-page.html
1. Erstellen Sie ein Produkt auf der Produktdetailseite (PDP).
1. Wechseln Sie in den Modus **Als Veröffentlichung anzeigen**.
1. Öffnen Sie in Ihrem Browser **Seitenquelle anzeigen**.
1. Suchen Sie in der Seitenquelle nach JSON+LD.

Bei korrekter Konfiguration finden Sie das JSON+LD-Skript, das mit dem Produkt verknüpft ist, das in die Seite eingefügt wurde.

## JSON+LD-Beispielstruktur für ein Produkt {#sample}

Nachfolgend finden Sie eine **JSON+LD**-Struktur für den Agatha-Rock, die auf der PDP-Seite im Venia-Projekt verfasst wurde:

```
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "Product",
  "sku": "VSK05",
  "name": "Agatha Skirt",
  "image": "https://mcstaging.catalogservice4commerce.fun/media/catalog/product/cache/926ea6fc2ad48a7202ff4587b6c2768e/v/s/vsk05-pe_main_2.jpg",
  "description": "The Agatha Skirt has a large circumference that lends itself to all sorts of drama...",
  "@id": "product-ef4fa1dc72",
  "offers": [
    {
      "@type": "Offer",
      "sku": "VSK05-KH-S",
      "url": "/content/venia/us/en/products/product-page.html/agatha-skirt.html",
      "priceCurrency": "USD",
      "price": 78.0
    },
    {
      "@type": "Offer",
      "sku": "VSK05-RN-XS",
      "availability": "InStock",
      "priceSpecification": {
        "@type": "UnitPriceSpecification",
        "priceType": "https://schema.org/ListPrice",
        "price": 18.0,
        "priceCurrency": "USD"
      },
      "price": 46.0
    }
  ]
}
</script>
```

## Zuordnen von JSON+LD-Attributen zu GraphQL {#mapping}

JSON- und LD-Attribute können GraphQL-Abfragen in AEM CIF zugeordnet werden, um sicherzustellen, dass strukturierte Daten dynamisch Produktinformationen widerspiegeln, die über GraphQL abgerufen wurden.

### Beispiel für eine Produktzuordnung {#example}

| JSON+LD-Attribut | Magento GraphQL-Attribut | Erforderlich (J/N) |
|---------------------------------|-------------------|---|
| SKU | SKU | N |
| offers.url | Benutzerdefinierte Logik | N |
| offers.SpecialPriceDate | special_to_date | N |
| offers.sku | SKU | N |
| offers.priceSpecification.priceCurrency | Währung | J |
| offers.priceSpecification.price | regular_price | N |
| offers.priceCurrency | Währung | J |
| offers.price | special_price | J |
| offers.image | media_gallery.url | N |
| offers.availability | stock_status | N |
| name | name | J |
| image | media_gallery.url | J |
| Beschreibung | Beschreibung | N |
| aggregateRating.reviewCount | review_count | N |
| aggregateRating.ratingValue | rating_summary | N |
| @id | id | N |

Diese Zuordnung stellt sicher, dass das JSON+LD-Skript basierend auf Produktdaten, die über GraphQL-Abfragen abgerufen werden, dynamisch befüllt wird.

Um Ihre JSON+LD-Struktur zu testen, können Sie den [Rich-Results-Test – Google Search Console](https://search.google.com/test/rich-results/result?id=wtU3LVIEM8H7Aaf5qqK9qw) verwenden. Dieses Tool bietet detailliertes Feedback, einschließlich der Frage, ob die erforderlichen Attribute vorhanden sind oder fehlen, und hilft sicherzustellen, dass Ihre strukturierten Daten korrekt implementiert werden.
