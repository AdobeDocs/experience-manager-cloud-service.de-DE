---
title: CIF-Hauptkomponenten anpassen
description: Erfahren Sie, wie Sie AEM CIF-Hauptkomponenten anpassen. Das Lernprogramm beschreibt, wie eine CIF-Core-Komponente sicher erweitert werden kann, um unternehmensspezifische Anforderungen zu erfüllen. Erfahren Sie, wie Sie eine GraphQL-Abfrage erweitern, um ein benutzerdefiniertes Attribut zurückzugeben und das neue Attribut in einer CIF-Core-Komponente anzuzeigen.
sub-product: Commerce
topics: Development
version: cloud-service
doc-type: tutorial
activity: develop
audience: developer
feature: Commerce Integration Framework
kt: 4279
thumbnail: customize-aem-cif-core-component.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '2550'
ht-degree: 4%

---


# Customize AEM CIF Core Components {#customize-cif-components}

Das [CIF Venia Project](https://github.com/adobe/aem-cif-guides-venia) ist eine Referenz-Codebasis für die Verwendung der [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components). In diesem Lernprogramm erweitern Sie die Komponente [Product Teaser](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) weiter, um ein benutzerdefiniertes Attribut aus Magento anzuzeigen. Außerdem erfahren Sie mehr über die GraphQL-Integration zwischen AEM und Magento und die Erweiterungshaken der CIF-Kernkomponenten.

>[!TIP]
>
> Verwenden Sie den [AEM Projektarchiv](https://github.com/adobe/aem-project-archetype) , wenn Sie Ihre eigene Commerce-Implementierung starten.

## Was Sie erstellen

Die Marke Venia hat vor kurzem begonnen, einige Produkte mit nachhaltigen Materialien zu produzieren und das Unternehmen möchte ein **umweltfreundliches** Zeichen als Teil des Product Teaser zeigen. Ein neues benutzerspezifisches Attribut wird in Magento erstellt, um anzugeben, ob ein Produkt das **umweltfreundliche** Material verwendet. Dieses benutzerspezifische Attribut wird dann als Teil der GraphQL-Abfrage hinzugefügt und im Product Teaser für bestimmte Produkte angezeigt.

![UMWELT - Freundliche Abzeichen - endgültige Implementierung](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## Voraussetzungen {#prerequisites}

Zum Abschluss dieses Lernprogramms ist eine lokale Umgebung erforderlich. Dazu gehört eine laufende Instanz von AEM, die konfiguriert ist und mit einer Magento-Instanz verbunden ist. Überprüfen Sie die Anforderungen und Schritte zum [Einrichten einer lokalen Entwicklung mit AEM als Cloud Service-SDK](../develop.md). Um dem Tutorial vollständig zu folgen, benötigen Sie Berechtigungen, um einem Produkt [in Magento](https://docs.magento.com/user-guide/catalog/product-attributes-add.html) Attribute hinzuzufügen.

Sie benötigen außerdem eine GraphQL IDE wie [GraphiQL](https://github.com/graphql/graphiql) oder eine Browsererweiterung, um die Codebeispiele und -tutorials auszuführen. Wenn Sie eine Browsererweiterung installieren, stellen Sie sicher, dass diese die Möglichkeit hat, Anforderungsheader festzulegen. In Google Chrome ist der [Altair GraphQL Client](https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja) eine Erweiterung, die den Auftrag ausführen kann.

## Clone the Venia project {#clone-venia-project}

Wir klonen das [Venia-Projekt](https://github.com/adobe/aem-cif-guides-venia) und überschreiben dann die Standardstile.

>[!NOTE]
>
> **Sie können ein vorhandenes Projekt** (basierend auf dem AEM Projekt Archetype mit CIF enthalten) verwenden und diesen Abschnitt überspringen.

1. Führen Sie den folgenden Befehl git aus, um das Projekt zu klonen:

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Erstellen Sie das Projekt und stellen Sie es auf einer lokalen Instanz AEM bereit:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. hinzufügen Sie die erforderlichen OSGi-Konfigurationen, um Ihre AEM mit einer Magento-Instanz zu verbinden oder die Konfigurationen dem neu erstellten Projekt hinzuzufügen.

1. An dieser Stelle sollten Sie über eine funktionierende Version eines Stores verfügen, der mit einer Magento-Instanz verbunden ist. Navigieren Sie zur Seite `US` > `Home` unter: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

   Sie sollten sehen, dass das Schaufenster derzeit das Thema Venia verwendet. Wenn Sie das Hauptmenü des Schaufensters erweitern, sollten Sie verschiedene Kategorien sehen, die darauf hinweisen, dass das Magento der Verbindung funktioniert.

   ![Storefront mit Venia-Design konfiguriert](../assets/customize-cif-components/venia-store-configured.png)

## Authoring des Produkt-Teasers {#author-product-teaser}

Die Komponente Product Teaser wird in diesem Lernprogramm erweitert. Als ersten Schritt fügen Sie der Startseite eine neue Instanz des Product Teaser hinzu, um die Grundfunktionen zu verstehen.

1. Navigieren Sie zur **Startseite** der Site: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

2. Fügen Sie eine neue **Product Teaser** -Komponente in den Container des Hauptlayouts auf der Seite ein.

   ![Produktbeschleuniger einfügen](../assets/customize-cif-components/product-teaser-add-component.png)

3. Erweitern Sie das Seitenbedienfeld (falls noch nicht umgeschaltet) und wechseln Sie in das Dropdown-Feld für die Asset-Suche zu **Produkte**. Dies sollte eine Liste der verfügbaren Produkte einer angeschlossenen Magento-Instanz anzeigen. Wählen Sie ein Produkt aus und **ziehen** Sie es per Drag &amp; Drop auf die Komponente **Product Teaser** auf der Seite.

   ![Drag &amp; Drop Product Teaser](../assets/customize-cif-components/drag-drop-product-teaser.png)

   >[!NOTE]
   >
   > Beachten Sie, dass Sie das angezeigte Produkt auch konfigurieren können, indem Sie die Komponente mithilfe des Dialogfelds konfigurieren (indem Sie auf das *Schraubenschlüsselsymbol* klicken).

4. Sie sollten nun sehen, dass ein Produkt vom Produkt-Teaser angezeigt wird. Der Name des Produkts und der Preis des Produkts sind Standardattribute, die angezeigt werden.

   ![Product Teaser - Standardstil](../assets/customize-cif-components/product-teaser-default-style.png)

## hinzufügen eines benutzerdefinierten Attributs in Magento {#add-custom-attribute}

Die in AEM angezeigten Produkte und Produktdaten werden im Magento gespeichert. Als Nächstes fügen Sie ein neues Attribut für **Eco Friendly** als Teil des Produktattributs hinzu, das mithilfe der Magento-Benutzeroberfläche festgelegt wurde.

>[!TIP]
>
> Sie haben bereits ein benutzerdefiniertes **Ja/Nein** -Attribut als Teil Ihres Produktattributs? Sie können es kostenlos nutzen und diesen Abschnitt überspringen.

1. Melden Sie sich bei Ihrer Magento-Instanz an.
1. Navigieren Sie zu **Katalog** > **Produkte**.
1. Aktualisieren Sie den Suchfilter, um das **konfigurierbare Produkt** zu finden, das verwendet wird, wenn es der Teaser-Komponente in der vorherigen Übung hinzugefügt wurde. Öffnen Sie das Produkt im Bearbeitungsmodus.

   ![Suche nach Valeria-Produkten](../assets/customize-cif-components/search-valeria-product.png)

1. Klicken Sie in der Ansicht &quot;product&quot;auf **Hinzufügen Attribut** > Neues Attribut **erstellen**.
1. Füllen Sie das Formular &quot; **Neues Attribut** &quot;mit den folgenden Werten aus (bei anderen Werten bleiben die Standardeinstellungen erhalten)

   | Feldsatz | Feldbezeichnung | Wert |
   |-----------|-------------|---------|
   | Attributeigenschaften | Attributbeschriftung | **Öko-freundlich** |
   | Attributeigenschaften | Katalogeingabetyp | **Ja/Nein** |
   | Erweiterte Attributeigenschaften | Attributcode | **eco_friendly** |

   ![Neues Attributformular](../assets/customize-cif-components/attribute-new-form.png)

   Click **Save Attribute** when finished.

1. Blättern Sie zum unteren Rand des Produkts und erweitern Sie die Überschrift &quot; **Attribute** &quot;. Sie sollten das neue Feld **Eco Friendly** sehen. Umschalten auf **Ja**.

   ![Umschalten auf Ja](../assets/customize-cif-components/eco-friendly-toggle-yes.png)

   **Speichern Sie** die Änderungen am Produkt.

   >[!TIP]
   >
   > Weitere Informationen zur Verwaltung von [Produktattributen finden Sie im Magento-Benutzerhandbuch](https://docs.magento.com/user-guide/catalog/attribute-best-practices.html).

1. Navigieren Sie zu **System** > **Tools** > **Cache-Verwaltung**. Da das Schema aktualisiert wurde, müssen wir einige der Cache-Typen in Magento für ungültig erklären.
1. Aktivieren Sie das Kontrollkästchen neben **Konfiguration** und senden Sie den Cachetyp zum **Aktualisieren**

   ![Configuration Cache-Typ aktualisieren](../assets/customize-cif-components/refresh-configuration-cache-type.png)

   >[!TIP]
   >
   > Weitere Informationen zur [Cache-Verwaltung finden Sie im Magento-Benutzerhandbuch](https://docs.magento.com/user-guide/system/cache-management.html).

## GraphQL-IDE zum Überprüfen von Attributen verwenden {#use-graphql-ide}

Bevor Sie in AEM Code springen, sollten Sie das [Magento GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/) mit einer GraphQL IDE untersuchen. Die Magento-Integration mit AEM erfolgt hauptsächlich über eine Reihe von GraphQL-Abfragen. Das Verstehen und Ändern der GraphQL-Abfragen ist eine der wichtigsten Erweiterungen der CIF-Kernkomponenten.

Verwenden Sie anschließend eine Grafik-QL-IDE, um zu überprüfen, ob das `eco_friendly` Attribut dem Produktattributsatz hinzugefügt wurde. Screenshots in diesem Tutorial verwenden den [Altair GraphQL Client](https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja).

1. Öffnen Sie die GraphQL IDE und geben Sie die URL `http://<magento-server>/graphql` in die URL-Leiste Ihrer IDE oder Erweiterung ein.
2. hinzufügen der folgenden [Abfrage](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) , bei der `YOUR_SKU` die **SKU** des in der vorherigen Übung verwendeten Produkts ist:

   ```json
     {
       products(
       filter: { sku: { eq: "YOUR_SKU" } }
       ) {
           items {
           name
           sku
           eco_friendly
           }
       }
   }
   ```

3. Führen Sie die Abfrage aus und Sie erhalten eine Antwort wie die folgende:

   ```json
   {
   "data": {
       "products": {
           "items": [
               {
               "name": "Valeria Two-Layer Tank",
               "sku": "VT11",
               "eco_friendly": 1
               }
           ]
           }
       }
   }
   ```

   ![Beispieldiagramm-QL-Antwort](../assets/customize-cif-components/sample-graphql-query.png)

   Beachten Sie, dass der Wert von **Yes** eine Ganzzahl von **1** ist. Dies ist nützlich, wenn wir die GraphQL Abfrage in Java schreiben.

   >[!TIP]
   >
   > Detailliertere Dokumentation zu [Magento GraphQL finden Sie hier](https://devdocs.magento.com/guides/v2.4/graphql/index.html).

## Aktualisieren des Sling-Modells für den Produkt-Teaser {#updating-sling-model-product-teaser}

Als Nächstes erweitern wir die Geschäftslogik des Product Teaser durch die Implementierung eines Sling-Modells. [Sling-Modelle](https://sling.apache.org/documentation/bundles/models.html)sind durch Anmerkungen angetriebene &quot;POJOs&quot;(Plain Old Java Objects), die eine beliebige Geschäftslogik implementieren, die von der Komponente benötigt wird. Sling-Modelle werden in Verbindung mit den HTML-Skripten als Teil der Komponente verwendet. Wir folgen dem [Delegationsmuster für Sling-Modelle](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) , sodass wir Teile des bestehenden Produktteaser-Modells einfach erweitern können.

Sling-Modelle werden als Java implementiert und können im **Kernmodul** des erstellten Projekts gefunden werden.

Verwenden Sie [die IDE Ihrer Wahl](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) , um das Venia-Projekt zu importieren. Die verwendeten Screenshots stammen aus der [Visual Studio Code-IDE](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code).

1. Navigieren Sie in Ihrer IDE unter dem **Kernmodul** zu: `core/src/main/java/com/venia/core/models/commerce/MyProductTeaser.java`.

   ![Hauptspeicherort-IDE](../assets/customize-cif-components/core-location-ide.png)

   `MyProductTeaser.java` ist eine Java-Schnittstelle, die die CIF- [ProductTeaser](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/models/productteaser/ProductTeaser.java) -Schnittstelle erweitert.

   Es wurde bereits eine neue Methode mit dem Namen `isShowBadge()` zur Anzeige eines Kennzeichens hinzugefügt, wenn das Produkt als &quot;Neu&quot;gilt.

1. hinzufügen einer neuen Methode an `isEcoFriendly()` der Schnittstelle:

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   
       public Boolean isEcoFriendly();
   }
   ```

   Dies ist eine neue Methode, die wir einführen werden, um die Logik zu kapseln, um anzugeben, ob das Produkt das `eco_friendly` Attribut auf **Ja** oder **Nein** gesetzt hat.

1. Überprüfen Sie dann das `MyProductTeaserImpl.java` at `core/src/main/java/com/venia/core/models/commerce/MyProductTeaserImpl.java`.

   Das [Delegationsmuster für Sling-Modelle](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) ermöglicht `MyProductTeaserImpl` die Referenz auf `ProductTeaser` das Modell über die `sling:resourceSuperType` Eigenschaft:

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   Für alle Methoden, die wir nicht überschreiben oder ändern möchten, können wir einfach den Wert zurückgeben, den die `ProductTeaser` zurückgeben. Beispiel:

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

   Dadurch wird die Menge an Java-Code, die eine Implementierung schreiben muss, minimiert.

1. Einer der zusätzlichen Erweiterungspunkte, die von AEM CIF Core Components bereitgestellt werden, ist der, `AbstractProductRetriever` der Zugriff auf bestimmte Produktattribute bietet. Inspect der `initModel()` Methode:

   ```java
   import javax.annotation.PostConstruct;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
       ...
       private AbstractProductRetriever productRetriever;
   
       /* add this method to intialize the proudctRetriever */
       @PostConstruct
       public void initModel() {
           productRetriever = productTeaser.getProductRetriever();
   
           if (productRetriever != null) {
               productRetriever.extendProductQueryWith(p -> p.createdAt());
           }
   
       }
   ...
   ```

   Die `@PostConstruct` Anmerkung stellt sicher, dass diese Methode aufgerufen wird, sobald das Sling-Modell initialisiert wurde.

   Beachten Sie, dass die GraphQL-Abfrage des Produkts bereits mit der `extendProductQueryWith` Methode zum Abrufen des zusätzlichen `created_at` Attributs erweitert wurde. Dieses Attribut wird später als Teil der `isShowBadge()` Methode verwendet.

1. Aktualisieren Sie die GraphQL-Abfrage, um das `eco_friendly` Attribut in die partielle Abfrage einzuschließen:

   ```java
   //MyProductTeaserImpl.java
   
   private static final String ECO_FRIENDLY_ATTRIBUTE = "eco_friendly";
   
   @PostConstruct
   public void initModel() {
       productRetriever = productTeaser.getProductRetriever();
   
       if (productRetriever != null) {
           productRetriever.extendProductQueryWith(p ->
                productRetriever.extendProductQueryWith(p -> p
                   .createdAt()
                   .addCustomSimpleField(ECO_FRIENDLY_ATTRIBUTE)
               );
           );
       }
   }
   ```

   Das Hinzufügen der `extendProductQueryWith` Methode ist eine leistungsstarke Methode, um sicherzustellen, dass dem Rest des Modells zusätzliche Produktattribute zur Verfügung stehen. Außerdem wird die Anzahl der ausgeführten Abfragen minimiert.

   Im obigen Code wird das`addCustomSimpleField` Attribut zum Abrufen des `eco_friendly` Attributs verwendet. Dies zeigt, wie Sie Abfragen für benutzerdefinierte Attribute durchführen können, die Teil des Magento-Schemas sind.

   >[!NOTE]
   >
   > Die `createdAt()` Methode wurde tatsächlich als Teil der [Produktoberfläche](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java)implementiert. Die meisten häufig gefundenen Schema-Attribute wurden implementiert. Verwenden Sie daher nur die `addCustomSimpleField` für echte benutzerdefinierte Attribute.

1. hinzufügen einer Protokollfunktion, um das Debugging des Java-Codes zu unterstützen:

   ```java
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
   
   private static final Logger LOGGER = LoggerFactory.getLogger(MyProductTeaserImpl.class);
   ```

1. Implementieren Sie anschließend die `isEcoFriendly()` Methode:

   ```java
   @Override
   public Boolean isEcoFriendly() {
   
       Integer ecoFriendlyValue;
       try {
           ecoFriendlyValue = productRetriever.fetchProduct().getAsInteger(ECO_FRIENDLY_ATTRIBUTE);
           if(ecoFriendlyValue != null && ecoFriendlyValue.equals(Integer.valueOf(1))) {
               LOGGER.info("*** Product is Eco Friendly**");
               return true;
           }
       } catch (SchemaViolationError e) {
           LOGGER.error("Error retrieving eco friendly attribute");
       }
       LOGGER.info("*** Product is not Eco Friendly**");
       return false;
   }
   ```

   Bei der obigen Methode `productRetriever` wird das Produkt abgerufen, und die `getAsInteger()` Methode wird verwendet, um den Wert des `eco_friendly` Attributs abzurufen. Basierend auf den GraphQL Abfragen, die wir zuvor ausgeführt haben, wissen wir, dass der erwartete Wert, wenn das `eco_friendly` Attribut auf &quot;**Yes**&quot; gesetzt ist, eigentlich eine Ganzzahl von **1** ist.

   Nachdem das Sling-Modell aktualisiert wurde, muss das Komponenten-Markup aktualisiert werden, um einen Indikator für **umweltverträglich** basierend auf dem Sling-Modell anzuzeigen.

## Anpassen des Markups des Produkt-Teasers {#customize-markup-product-teaser}

Eine häufige Erweiterung AEM Komponenten besteht darin, das von der Komponente generierte Markup zu ändern. Dies geschieht durch Überschreiben des [HTML-Skripts](https://docs.adobe.com/content/help/de-DE/experience-manager-htl/using/overview.html) , das die Komponente zum Rendern des Markups verwendet. HTML-Vorlagensprache (HTL) ist eine einfache Vorlagensprache, die AEM Komponenten verwenden, um Markup basierend auf erstellten Inhalten dynamisch zu rendern, sodass die Komponenten wiederverwendet werden können. So kann z.B. der Produktteaser immer wieder wiederverwendet werden, um verschiedene Produkte anzuzeigen.

In unserem Fall möchten wir ein Banner über dem Teaser rendern, um anzugeben, dass das Produkt &quot;Eco Friendly&quot; auf Basis eines benutzerspezifischen Attributs ist. Das Entwurfsmuster zum [Anpassen des Markups](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) einer Komponente ist eigentlich Standard für alle AEM Komponenten, nicht nur für die AEM CIF-Kernkomponenten.

1. Navigieren Sie in der IDE zum `ui.apps` Modul, erweitern Sie es und erweitern Sie die Ordnerhierarchie, um: `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser` und überprüfen Sie die `.content.xml` Datei.

   ![Product Teaser ui.apps](../assets/customize-cif-components/product-teaser-ui-apps-ide.png)

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="Venia - Commerce"/>
   ```

   Oben ist die Komponentendefinition für die Product Teaser Komponente in unserem Projekt. Beachten Sie die Eigenschaft `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"`. Dies ist ein Beispiel für das Erstellen einer [Proxy-Komponente](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/using.html#create-proxy-components). Anstatt alle Product Teaser HTL-Skripte aus den AEM CIF Core-Komponenten zu kopieren und einzufügen, können wir die Funktionalität mit `sling:resourceSuperType` übernehmen.

1. Öffnen Sie die Datei `productteaser.html`. Dies ist eine Kopie der `productteaser.html` Datei des [CIF-Produkt-Teaser](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html)

   ```html
   <!--/* productteaser.html */-->
   <sly data-sly-use.product="com.venia.core.models.commerce.MyProductTeaser"
       data-sly-use.templates="core/wcm/components/commons/v1/templates.html"
       data-sly-use.actionsTpl="actions.html"
       data-sly-test.isConfigured="${properties.selection}"
       data-sly-test.hasProduct="${product.url}">
   ```

   Beachten Sie, dass das Sling-Modell für `MyProductTeaser` verwendet und der `product` Variablen zugewiesen wird.

1. Ändern Sie, `productteaser.html` um einen Aufruf an die in der vorherigen Übung implementierte `isEcoFriendly` Methode durchzuführen:

   ```html
   ...
   <div data-sly-test="${isConfigured && hasProduct}" class="item__root" data-cmp-is="productteaser" data-virtual="${product.virtualProduct}">
       <div data-sly-test="${product.showBadge}" class="item__badge">
           <span>${properties.text || 'New'}</span>
       </div>
       <!--/* Insert call to Eco Friendly here */-->
       <div data-sly-test="${product.ecoFriendly}" class="item__eco">
           <span>Eco Friendly</span>
       </div>
   ...
   ```

   Beim Aufrufen einer Sling Model-Methode in HTML wird der `get` und `is` -Teil der Methode abgelegt und der erste Buchstabe wird verringert. Also `isShowBadge()` wird `.showBadge` und `isEcoFriendly` wird `.ecoFriendly`. Basierend auf dem booleschen Wert, der von zurückgegeben wird, `.isEcoFriendly()` bestimmt, ob der `<span>Eco Friendly</span>` Wert angezeigt wird.

   Weitere Informationen zu `data-sly-test` und anderen [HTL-Blockanweisungen finden Sie hier](https://docs.adobe.com/content/help/en/experience-manager-htl/using/htl/block-statements.html#test).

1. Speichern Sie die Änderungen und stellen Sie die Updates mithilfe Ihrer Maven-Fähigkeiten über ein Befehlszeilenterminal AEM bereit:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Öffnen Sie ein neues Browserfenster und navigieren Sie zu AEM und zur **OSGi-Konsole** > **Status** > **Sling-Modelle**: [http://localhost:4502/system/console/status-slingmodels](http://localhost:4502/system/console/status-slingmodels)

1. Suchen Sie nach `MyProductTeaserImpl` einer Zeile, die wie folgt aussehen sollte:

   ```plain
   com.venia.core.models.commerce.MyProductTeaserImpl - venia/components/commerce/productteaser
   ```

   Dies bedeutet, dass das Sling-Modell ordnungsgemäß bereitgestellt wurde und der richtigen Komponente zugeordnet wurde.

1. Aktualisieren Sie auf der **Venia-Startseite** unter [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html) , wo der Produktteaser hinzugefügt wurde.

   ![Öko-freundliche Meldung angezeigt](../assets/customize-cif-components/eco-friendly-text-displayed.png)

   Wenn das `eco_friendly` Attribut für das Produkt auf **Ja** eingestellt ist, sollte der Text &quot;Eco Friendly&quot;auf der Seite angezeigt werden. Versuchen Sie, zu anderen Produkten zu wechseln, um die Verhaltensänderung zu sehen.

1. Als Nächstes öffnen Sie die AEM, `error.log` um die Protokollerklärungen anzuzeigen, die wir hinzugefügt haben. Das `error.log` befindet sich an `<AEM SDK Install Location>/crx-quickstart/logs/error.log`.

   Suchen Sie in den AEM Protokollen nach den Protokollanweisungen, die im Sling-Modell hinzugefügt wurden:

   ```plain
   2020-08-28 12:57:03.114 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is Eco Friendly**
   ...
   2020-08-28 13:01:00.271 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is not Eco Friendly**
   ...
   ```

   >[!CAUTION]
   >
   > Es können auch einige Stapelspuren angezeigt werden, wenn das im Teaser verwendete Produkt nicht über das `eco_friendly` Attribut verfügt, das im Attributsatz des Produkts festgelegt ist.

## hinzufügen Stile für das Umweltzeichen {#add-styles}

An diesem Punkt funktioniert die Logik, wann das **Eco Friendly** Zeichen angezeigt werden soll, aber der Text könnte einige Stile verwenden. Fügen Sie dem `ui.frontend` Modul anschließend ein Symbol und Stile hinzu, um die Implementierung abzuschließen.

1. Laden Sie die Datei [eco_friendly.svg](../assets/customize-cif-components/eco_friendly.svg) herunter. Dies wird als **Eco Friendly** -Zeichen verwendet.
1. Kehren Sie zur IDE zurück und navigieren Sie zum `ui.frontend` Ordner.
1. hinzufügen Sie die `eco_friendly.svg` Datei in den `ui.frontend/src/main/resources/images` Ordner:

   ![Eco-freundliche SVG hinzugefügt](../assets/customize-cif-components/eco-friendly-svg-added.png)

1. Open the file `productteaser.scss` at `ui.frontend/src/main/styles/commerce/_productteaser.scss`.
1. hinzufügen die folgenden Segmentregeln innerhalb der `.productteaser` Klasse:

   ```scss
   .productteaser {
       ...
       .item__eco {
           width: 60px;
           height: 60px;
           left: 0px;
           overflow: hidden;
           position: absolute;
           padding: 5px;
   
       span {
           display: block;
           position: absolute;
           width: 45px;
           height: 45px;
           text-indent: -9999px;
           background: no-repeat center center url('../resources/images/eco_friendly.svg'); 
           }
       }
   ...
   }
   ```

   >[!NOTE]
   >
   > Weitere Informationen zu [den Front-End-Workflows finden Sie unter CIF-Kernkomponenten](./style-cif-component.md) .

1. Speichern Sie die Änderungen und stellen Sie die Updates mithilfe Ihrer Maven-Fähigkeiten über ein Befehlszeilenterminal AEM bereit:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Aktualisieren Sie auf der **Venia-Startseite** unter [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html) , wo der Produktteaser hinzugefügt wurde.

   ![UMWELT - Freundliche Abzeichen - endgültige Implementierung](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## Herzlichen Glückwunsch {#congratulations}

Sie haben gerade Ihre erste AEM CIF-Komponente angepasst! Laden Sie die [fertigen Lösungsdateien hier](../assets/customize-cif-components/customize-cif-component-SOLUTION_FILES.zip)herunter.

## Bonus-Herausforderung {#bonus-challenge}

Überprüfen Sie die Funktionalität des **neuen** Kennzeichens, das bereits im Product Teaser implementiert wurde. Versuchen Sie, ein zusätzliches Kontrollkästchen hinzuzufügen, damit Autoren steuern können, wann das **Umweltzeichen** angezeigt werden soll. Sie müssen das Komponentendialogfeld aktualisieren `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser/_cq_dialog/.content.xml`.

![Implementierung neuer Kennzeichen](../assets/customize-cif-components/new-badge-implementation-challenge.png)

## Zusätzliche Ressourcen {#additional-resources}

* [AEM](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html)
* [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components)
* [Anpassen AEM CIF-Hauptkomponenten](https://github.com/adobe/aem-core-cif-components/wiki/Customizing-CIF-Core-Components)
* [Anpassen der Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html)
* [Erste Schritte mit AEM Sites](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
