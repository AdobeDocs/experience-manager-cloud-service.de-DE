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
source-git-commit: c956aab4dbbbb7daede3e115616ae923f7a68b90
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 97%

---

# Erweiterte URL-Konfigurationen {#url}

>[!NOTE]
>
> Suchmaschinenoptimierung (SEO) ist zu einem wichtigen Thema für viele Marketer geworden. Daher müssen SEO-Themen bei vielen Adobe Experience Manager (AEM) as a Cloud Service-Projekten berücksichtigt werden. Bitte lesen [Best Practices für SEO und URL-Verwaltung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/seo-and-url-management.html) für weitere Informationen.

[AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) stellen erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorieseiten bereit. Viele Implementierungen passen diese URLs für die Suchmaschinen-Optimierung (SEO) an.  Im folgenden Video wird beschrieben, wie Sie den `UrlProvider`-Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren, um die URLs für Produkt- und Kategorieseiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Konfiguration {#configuration}

Um den Service `UrlProvider` gemäß den SEO-Anforderungen zu konfigurieren, muss ein Projekt eine OSGi-Konfiguration für die „CIF URL-Provider-Konfiguration“ bereitstellen.

>[!NOTE]
>
> Seit Version 2.0.0 der AEM CIF-Kernkomponenten bietet die URL-Provider-Konfiguration nur vordefinierte URL-Formate anstelle der von 1.x-Versionen bekannten Freitext-konfigurierbaren Formate. Darüber hinaus wurde die Verwendung von Selektoren zur Übergabe von Daten in URLs durch Suffixe ersetzt.

### URL-Format von Produktseiten {#product}

Dies konfiguriert die URLs der Produktseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (default)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

Im Fall des [Venia Referenz-Shops](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wird durch `/content/venia/us/en/products/product-page` ersetzt
* `{{sku}}` wird durch die Produkt-SKU ersetzt, z. B. `VP09`
* `{{url_key}}` durch die `url_key`-Eigenschaft des Produkts ersetzt werden, z. B. `lenora-crochet-shorts`
* `{{url_path}}` wird durch den `url_path` des Produkts ersetzt, z. B. `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` wird durch die aktuell ausgewählte Variante ersetzt, z. B. `VP09-KH-S`

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
> Der `url_path` ist eine Verkettung aus dem `url_keys` der Vorgänger eines Produkts oder einer Kategorie und dem `url_key` des Produkts oder der Kategorie, getrennt durch `/`-Schrägstrich.

## Benutzerdefinierte URL-Formate {#custom-url-format}

Um ein benutzerdefiniertes URL-Format bereitzustellen, kann ein Projekt die [`UrlFormat`-Schnittstelle ](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/UrlFormat.html) implementieren und die Implementierung als OSGi-Service registrieren, wobei es entweder als Kategorieseiten- oder Produktseiten-URL-Format verwendet wird. Die `UrlFormat#PROP_USE_AS`-Service-Eigenschaft gibt an, welche der konfigurierten vordefinierten Formate ersetzt werden sollen:

* `useAs=productPageUrlFormat`, ersetzt das konfigurierte URL-Format der Produktseite
* `useAs=categoryPageUrlFormat`, ersetzt das konfigurierte URL-Format der Kategorieseite

Wenn es mehrere Implementierungen von `UrlFormat` gibt, die als OSGi-Services registriert sind, ersetzt die Implementierung mit dem höheren Service-Rang die Implementierung(en) mit dem niedrigeren Service-Rang.

Der `UrlFormat` muss ein Paar von Methoden implementieren, um eine URL aus einer gegebenen Parameterzuordnung zu erstellen und eine URL zu parsen, um dieselbe Parameterzuordnung zurückzugeben. Die Parameter sind dieselben wie oben beschrieben. Nur für Kategorien wird ein zusätzlicher Parameter `{{uid}}` für `UrlFormat` bereitgestellt.

## Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Neben `UrlProvider` können auch [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfiguriert werden, um URLs neu zu schreiben und zu verarbeiten. Das AEM-Archetyp-Projekt bietet außerdem [eine Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) zum Konfigurieren einiger Sling-Zuordnungen für Port 4503 (Veröffentlichungsinstanz) und Port 80 (Dispatcher).

## Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Neuschreibungen können auch mithilfe des AEM Dispatcher-HTTP-Servers mit dem Modul `mod_rewrite` erreicht werden. Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) stellt eine AEM Dispatcher-Referenzkonfiguration bereit, die bereits grundlegende [Neuschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Beispiel

Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren. Dadurch können für jedes Projekt individuelle URL-Muster für Produkt- und Kategorieseiten entsprechend ihren SEO-Anforderungen eingerichtet werden. Es wird eine Kombination aus CIF-`UrlProvider` und Sling-Zuordnungen verwendet, wie oben beschrieben.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domain angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Host-Namens und der Domain. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Implementierung aktiviert werden. Benennen Sie dazu den Ordner `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domain-Namen um und aktivieren Sie diese Konfiguration, indem Sie `resource.resolver.map.location="/etc/map.publish"` zur `JcrResourceResolver`-Konfiguration des Projekts hinzufügen.

## Zusätzliche Ressourcen

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [AEM-Ressourcenzuordnung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=de)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
