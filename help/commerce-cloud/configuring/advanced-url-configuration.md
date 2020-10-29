---
title: Erweiterte URL-Konfigurationen
description: Erfahren Sie, wie Sie die URLs für Produkt- und Kategorien-Seiten anpassen. Dies ermöglicht Implementierungen, URLs für Suchmaschinen zu optimieren und die Erkennung zu fördern.
sub-product: Commerce
version: cloud-service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 4%

---


# Erweiterte URL-Konfigurationen {#url}

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bieten erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorien-Seiten. Viele Implementierungen passen diese URLs für Suchmaschinenoptimierung (SEO) an.  Im folgenden Video wird beschrieben, wie Sie den `UrlProvider` Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren, um die URLs für Produkt- und Kategorien-Seiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Konfiguration {#configuration}

Um den `UrlProvider` Dienst gemäß den SEO-Anforderungen zu konfigurieren und ein Projekt muss eine OSGI-Konfiguration für die Konfiguration &quot;CIF URL Provider&quot; angeben und konfigurieren Sie den Dienst wie unten beschrieben.

>[!NOTE]
>
> Das [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) -Projekt, siehe unten, enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorien-Seiten zu demonstrieren.

### URL-Vorlage der Produktseite {#product}

Dadurch werden die URLs der Produktseiten mit den folgenden Eigenschaften konfiguriert:

* **Produkt-URL-Vorlage**: definiert das Format von URLs mit einem Satz von Platzhaltern. Der Standardwert ist `{{page}}.{{url_key}}.html#{{variant_sku}}`, wodurch letztendlich URLs generiert werden, z. B. `/content/venia/us/en/products/product-page.chaz-kangeroo-hoodie.html#MH01-M-Orange` wo
   * `{{page}}` ersetzt durch `/content/venia/us/en/products/product-page`
   * `{{url_key}}` durch die `url_key` Eigenschaft des Magentos ersetzt wurde, hier `chaz-kangeroo-hoodie`
   * `{{variant_sku}}` durch die aktuell ausgewählte Variante ersetzt wurde, hier `MH01-M-Orange`
* **Speicherort** der Produkt-ID: definiert den Speicherort der ID, die zum Abrufen der Produktdaten verwendet wird. Der Standardwert ist `SELECTOR`der andere mögliche Wert `SUFFIX`. Bei der vorherigen Beispiel-URL bedeutet dies, dass der Bezeichner zum Abrufen der Produktdaten verwendet `chaz-kangeroo-hoodie` wird.
* **Produktidentifizierungstyp**: definiert den Typ der ID, die beim Abrufen der Produktdaten verwendet wird. Der Standardwert ist `URL_KEY`der andere mögliche Wert `SKU`. Mit der vorherigen Beispiel-URL bedeutet dies, dass die Produktdaten mit einem Magento-GraphQL-Filter wie `filter:{url_key:{eq:"chaz-kangeroo-hoodie"}}`.

### URL-Vorlage der Produktseite Liste {#product-list}

Dadurch werden die URLs der Listen der Kategorie oder des Produkts mit den folgenden Eigenschaften konfiguriert:

* **Kategorie-URL-Vorlage**: definiert das Format von URLs mit einem Satz von Platzhaltern. Der Standardwert ist `{{page}}.{{id}}.html`, wodurch letztendlich URLs generiert werden, z. B. `/content/venia/us/en/products/category-page.3.html` wo
   * `{{page}}` ersetzt durch `/content/venia/us/en/products/category-page`
   * `{{id}}` durch das `id` Eigentum von Magento der Kategorie ersetzt wurde, hier `3`
* **Speicherort** der Kategorie: definiert den Speicherort der ID, die zum Abrufen der Produktdaten verwendet wird. Der Standardwert ist `SELECTOR`der andere mögliche Wert `SUFFIX`. Bei der vorherigen Beispiel-URL bedeutet dies, dass der Bezeichner zum Abrufen der Produktdaten verwendet `3` wird.
* **Kategorien-ID-Typ**: definiert den Typ der ID, die beim Abrufen der Produktdaten verwendet wird. Der Standardwert und derzeit nur der unterstützte Wert ist `ID`. Bei der vorherigen Beispiel-URL bedeutet dies, dass die Daten der Kategorie mit einem Magento-GraphQL-Filter wie `category(id:3)`.

Es ist möglich, benutzerdefinierte Eigenschaften für jede Vorlage hinzuzufügen, solange die entsprechenden Daten von den Komponenten, die die Vorlage verwenden, festgelegt werden `UrlProvider`. Überprüfen Sie beispielsweise den Code der `ProductListItemImpl` Klasse, um herauszufinden, wie dieser implementiert wird.

Es ist auch möglich, den `UrlProvider` Dienst durch einen komplett benutzerdefinierten OSGi-Dienst zu ersetzen. In diesem Fall muss man die `UrlProvider` Schnittstelle implementieren und mit einer höheren Dienstrang registrieren, um die Standardimplementierung zu ersetzen.

## Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Zusätzlich `UrlProvider`ist es möglich, [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) zu konfigurieren, um URLs umzuschreiben und zu verarbeiten. Das AEM Archetype-Projekt bietet außerdem [eine Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) zum Konfigurieren einiger Sling-Zuordnungen für Port 4503 (publish) und 80 (dispatcher).

## Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Umschreibungen können auch über AEM Dispatcher HTTP-Server mit `mod_rewrite` Modul erreicht werden. Der [AEM Projektarchiv](https://github.com/adobe/aem-project-archetype) stellt eine Referenz AEM Dispatcher-Konfiguration bereit, die bereits grundlegende [Umschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Beispiel

Das [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) -Projekt enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorien-Seiten zu demonstrieren. Dadurch kann jedes Projekt individuelle URL-Muster für Produktseiten und Kategorien entsprechend ihren SEO-Anforderungen einrichten. Es wird eine Kombination aus CIF- `UrlProvider` und Sling-Zuordnungen wie oben beschrieben verwendet.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domäne angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Hostnamens und der Domäne. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Bereitstellung aktiviert werden. Benennen Sie dazu den `hostname.adobeaemcloud.com` Ordner &quot;Sling Mapping&quot; `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domänennamen um und aktivieren Sie diese Konfiguration, indem Sie `resource.resolver.map.location="/etc/map.publish"` zur `JcrResourceResolver` Konfiguration des Projekts hinzufügen.

## Zusätzliche Ressourcen

* [Venedig-Referenzspeicher](https://github.com/adobe/aem-cif-guides-venia)
* [AEM](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
