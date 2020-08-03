---
title: CIF-Hauptkomponenten anpassen
description: CIF-Hauptkomponenten anpassen
translation-type: tm+mt
source-git-commit: dd6973085ae34dd6ea7296c36d0a14f699440269
workflow-type: tm+mt
source-wordcount: '2520'
ht-degree: 2%

---


# Anpassen AEM CIF-Hauptkomponenten {#customize-cif-components}

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bieten einen Standardsatz von Commerce-Komponenten, mit denen ein Projekt beschleunigt werden kann, das Adobe Experience Manager- (AEM-) und Magento-Lösungen integriert. Diese Komponenten sind produktionsbereit und können [einfach mit CSS](style-cif-component.md)formatiert werden. Viele Implementierungen möchten diese Komponenten auch erweitern, um unternehmensspezifischen Anforderungen gerecht zu werden.

In diesem Tutorial werden wir einige verschiedene Erweiterungspunkte von AEM CIF Core-Komponenten und AEM im Allgemeinen überprüfen. Dazu erweitern wir die Funktionalität der Komponente [Product Teaser](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) um die Möglichkeit, ein &quot;neues&quot;Banner zu rendern. Inhaltsersteller können dieses Banner umschalten und bestimmen, wie lange das Banner angezeigt werden soll. Das &quot;Alter&quot;des Magentos basiert auf dem Erstellungsdatum im Produktkatalog. Sobald ein Produkt eine bestimmte Anzahl von Tagen alt ist, sollte das Banner &quot;Neu&quot;automatisch verschwinden.

![Neues Banner erweitert](/help/commerce-cloud/assets/customize-cif-components/new-banner-productteaser.png)

## Voraussetzungen {#prerequisites}

Folgende Werkzeuge und Technologien sind erforderlich:

* [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html)
* [Apache Maven](https://maven.apache.org/) (3.3.9 oder neuer)
* [AEM Cloud-SKD mit CIF-Add-on](../develop.md)
* Magento mit CIF-Kernkomponenten

Es wird empfohlen, die folgenden Inhalte zu überprüfen, bevor Sie mit diesem Lernprogramm fortfahren:

* [Einführung des Commerce-Integrationsrahmens auf AEM als Cloud Service](/help/commerce-cloud/overview.md)
* [Stil AEM CIF-Kernkomponenten - Tutorial](style-cif-component.md)

## Starterprojekt

Wir haben ein Startprojekt zur Verwendung mit diesem Tutorial zur Verfügung gestellt. Das Projekt wurde mit [v0.7.0](https://github.com/adobe/aem-cif-project-archetype/releases/tag/cif-project-archetype-0.7.0) des CIF-Projektarchetyps erstellt. Es wird als Best Practice angesehen, immer die [neueste Version](https://github.com/adobe/aem-cif-project-archetype/releases/latest) des Archetyps zu verwenden, wenn ein neues Projekt gestartet wird.

1. Laden Sie das Startprojekt [**acme-store.zip **](/help/commerce-cloud/assets/customize-cif-components/acme-store.zip)auf Ihren Desktop herunter.

1. Dekomprimieren Sie **acme-store.zip** , und Sie sollten die folgende Ordnerstruktur sehen:

   ```plain
   /acme-store
      /ui.content
      /ui.apps
      /samplecontent
      /core
      /all
      + pom.xml
      + README.md
   ```

1. Öffnen Sie ein neues Terminalfenster und erstellen Sie das Projekt und stellen Sie es auf einer lokalen Instanz von AEM bereit.

   ```shell
   $ cd acme-store/
   $ mvn clean install -PautoInstallAll
   ```

1. Hinzufügen Sie die erforderlichen OSGi-Konfigurationen, um Ihre AEM mit einer Magento-Instanz zu verbinden oder die Konfigurationen dem neu erstellten Projekt hinzuzufügen.

1. An dieser Stelle sollten Sie über eine funktionierende Version eines Stores verfügen, der mit einer Magento-Instanz verbunden ist. Navigieren Sie zur Seite `US` > `Home` unter: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

   Sie sollten sehen, dass das Schaufenster derzeit das Thema Venia verwendet. Wenn Sie das Hauptmenü des Schaufensters erweitern, sollten Sie verschiedene Kategorien sehen, die darauf hinweisen, dass das Magento der Verbindung funktioniert.

   ![Schaufenster mit Venia-Design konfiguriert](/help/commerce-cloud/assets/customize-cif-components/acme-store-configured.png)

## Authoring des Produkt-Teasers {#author-product-teaser}

Wir werden die Komponente Product Teaser in diesem Tutorial erweitern. Als ersten Schritt fügen wir der Startseite eine neue Instanz des Product Teaser hinzu, um die Grundfunktionen zu verstehen.

1. Navigieren Sie zur **Startseite** der Site: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

1. Fügen Sie eine neue **Product Teaser** -Komponente in den Container des Hauptlayouts auf der Seite ein.

   ![Produktbeschleuniger einfügen](/help/commerce-cloud/assets/customize-cif-components/product-teaser-add-component.png)

1. Erweitern Sie das Seitenbedienfeld (falls noch nicht umgeschaltet) und wechseln Sie in das Dropdown-Feld für die Asset-Suche zu **Produkte**. Dies sollte eine Liste der verfügbaren Produkte einer angeschlossenen Magento-Instanz anzeigen. Wählen Sie ein Produkt aus und **ziehen** Sie es per Drag &amp; Drop auf die Komponente **Product Teaser** auf der Seite.

   ![Drag &amp; Drop Product Teaser](/help/commerce-cloud/assets/customize-cif-components/drag-drop-product-teaser.png)

   > Beachten Sie, dass Sie das angezeigte Produkt auch konfigurieren können, indem Sie die Komponente mithilfe des Dialogfelds konfigurieren (indem Sie auf das *Schraubenschlüsselsymbol* klicken).

1. Sie sollten nun sehen, dass ein Produkt vom Produkt-Teaser angezeigt wird. Der Name des Produkts und der Preis des Produkts sind Standardattribute, die angezeigt werden.

   ![Product Teaser - Standardstil](/help/commerce-cloud/assets/customize-cif-components/product-teaser-default-style.png)

## Anpassen des Markups des Produkt-Teasers {#customize-markup-product-teaser}

Eine häufige Erweiterung AEM Komponenten besteht darin, das von der Komponente generierte Markup zu ändern. Dies geschieht durch Überschreiben des [HTML-Skripts](https://docs.adobe.com/content/help/de-DE/experience-manager-htl/using/overview.html) , das die Komponente zum Rendern des Markups verwendet. HTML-Vorlagensprache (HTL) ist eine einfache Vorlagensprache, die AEM Komponenten verwenden, um Markup basierend auf erstellten Inhalten dynamisch zu rendern, sodass die Komponenten wiederverwendet werden können. So kann z.B. der Produktteaser immer wieder wiederverwendet werden, um verschiedene Produkte anzuzeigen.

In unserem Fall möchten wir ein Banner über dem Teaser rendern, um anzuzeigen, dass das Produkt &quot;Neu&quot; ist und kürzlich dem Katalog hinzugefügt wurde. Das Entwurfsmuster zum [Anpassen des Markups](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) einer Komponente ist eigentlich Standard für alle AEM Komponenten, nicht nur für die AEM CIF-Kernkomponenten.

Verwenden Sie die IDE Ihrer Wahl, um das Startprojekt zu [öffnen, das zu Beginn des Lernprogramms heruntergeladen wurde](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) .

1. Navigieren Sie zum Modul **ui.apps** und erweitern Sie die Ordnerhierarchie um: `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser` und überprüfen Sie die `.content.xml` Datei.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="acme"/>
   ```

   Oben ist die Komponentendefinition für die Product Teaser Komponente in unserem Projekt. Beachten Sie die Eigenschaft `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"`. Dies ist ein Beispiel für das Erstellen einer [Proxy-Komponente](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/using.html#create-proxy-components). Anstatt alle Product Teaser HTL-Skripte aus den AEM CIF Core-Komponenten zu kopieren und einzufügen, können wir die Funktionalität mit `sling:resourceSuperType` übernehmen.

1. Öffnen Sie einen neuen Browser und navigieren Sie in AEM zu [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp#/apps/core/cif/components/commerce/productteaser/v1/productteaser) . Erweitern Sie die Struktur, um die `productteaser` Komponente unter: `/apps/core/cif/components/commerce/productteaser/v1/productteaser`:

   ![CRXDE Lite Product Teaser](/help/commerce-cloud/assets/customize-cif-components/crxde-productteaser.png)

   Dies ist die vollständige Komponentendefinition für die Komponente Product Teaser.

1. Wechseln Sie zurück zu Ihrem IDE- und dem Acme Store-Projekt. Erstellen Sie eine neue Datei mit dem Namen `productteaser.html` darunter `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser`.

1. Kopieren Sie den Inhalt von `productteaser.html` aus [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp#/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html) und fügen Sie ihn in das Acme-Store-Projekt in der neu erstellten `productteaser.html` Datei ein.

   ![Product Teaser html-Überschreiben](/help/commerce-cloud/assets/customize-cif-components/productteaser-html-overwrite.png)

1. Ändern Sie im Acme-Store-Projekt die `productteaser.html` Datei und fügen Sie ein neues div ein, das eine Markierung über dem Produktbild-Markup darstellt:

   ```html
   ...
   <div data-sly-test.isvalid="${product.url}" class="item__root" data-cmp-is="productteaser">
       <!-- Add Badge -->
       <div class="item__badge">
           <span>New</span>
       </div>
       <!-- end add badge -->
       <a class="item__images" href=${product.url}>
           <img class="item__image" width="100%" height="100%"
                   src="${product.image}" alt="${product.image}"/>
       </a>
       <a class="item__name" href=${product.url}><span>${product.name}</span></a>
       <div class="item__price">
           <span> ${product.formattedPrice} </span>
       </div>
       <sly data-sly-call="${actionsTpl.actions @ product=product}"></sly>
   </div>
   ```

1. Stellen Sie den aktualisierten Code für die lokale Instanz von AEM bereit, indem Sie Ihre Fähigkeiten und Fähigkeiten nutzen oder [die Funktionen Ihrer IDE](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment)verwenden:

   ```shell
   $ cd ui.apps
   $ mvn -PautoInstallPackage clean install
   ```

1. Kehren Sie im Browser zur [Homepage der Schaufensterfront](http://localhost:4502/editor.html/content/acme/us/en.html) in AEM zurück. Aktualisieren und Sie sollten sehen, dass oben rechts in der Komponente ein &quot;neues&quot;Banner angezeigt wird.

   ![Neues Banner erweitert](/help/commerce-cloud/assets/customize-cif-components/new-banner-productteaser.png)

   Derzeit gibt es keine Logik, wann das Banner angezeigt wird. In den nächsten Übungen werden wir das korrigieren.

   > Beachten Sie, dass das CSS zum Rendern des Banners als Teil des Startprojekts bereitgestellt wurde und unter folgender Adresse zu finden ist: `ui.apps/../apps/acme/clientlibs/theme/components/productteaser/teaser.css`. Weitere Informationen finden Sie im Tutorial [Styling CIF-Kernkomponenten](style-cif-component.md).

## Anpassen des Dialogfelds des Produkteditors {#customize-dialog-product-teaser}

Als Nächstes passen wir den Dialog der Komponente &quot;Product Teaser&quot;an, damit ein Autor den Datumsbereich bestimmen kann, für den ein Produkt als &quot;neu&quot;gilt, und ob das Banner angezeigt werden soll. Dazu [passen wir den Dialog](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-dialogs) des Produkt-Teasers im Rahmen des Acme Store-Projekts an.

1. Öffnen Sie das Acme Store-Projekt in der IDE Ihrer Wahl und navigieren Sie zu `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser`.

1. Fügen Sie unter dem `productteaser` Ordner einen neuen Ordner mit dem Namen `_cq_dialog`hinzu. Hinzufügen Sie eine neue Datei in den `_cq_dialog` Ordner `.content.xml`. Sie sollten jetzt die folgende Dateistruktur haben:

   ```plain
   ../acme
       /components
           /commerce
               /productteaser
                  /_cq_dialog
                     + .content.xml
                  /_cq_template
                  + .content.xml
                  + productteaser.html
   ```

1. Aktualisieren Sie `_cq_dialog/.content.xml` mit der folgenden XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
       xmlns:cq="http://www.day.com/jcr/cq/1.0" 
       xmlns:jcr="http://www.jcp.org/jcr/1.0" 
       xmlns:nt="http://www.jcp.org/jcr/nt/1.0" 
       jcr:primaryType="nt:unstructured" 
       jcr:title="My Product Teaser" 
       sling:resourceType="cq/gui/components/authoring/dialog" 
       trackingFeature="cif-core-components:productteaser:v1">
       <content jcr:primaryType="nt:unstructured" 
           sling:resourceType="granite/ui/components/coral/foundation/container">
           <items jcr:primaryType="nt:unstructured">
               <tabs jcr:primaryType="nt:unstructured" 
                   sling:resourceType="granite/ui/components/coral/foundation/tabs" 
                   maximized="{Boolean}true">
                   <items jcr:primaryType="nt:unstructured">
                       <badge jcr:primaryType="nt:unstructured" 
                           jcr:title="Badge" 
                           sling:resourceType="granite/ui/components/coral/foundation/container" 
                           margin="{Boolean}true">
                           <items jcr:primaryType="nt:unstructured">
                               <columns jcr:primaryType="nt:unstructured" 
                                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns" 
                                   margin="{Boolean}true">
                                   <items jcr:primaryType="nt:unstructured">
                                       <column jcr:primaryType="nt:unstructured" 
                                           sling:resourceType="granite/ui/components/coral/foundation/container">
                                           <items jcr:primaryType="nt:unstructured">
                                               <badge jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/coral/foundation/form/checkbox" 
                                                   text="Display 'New' badge" 
                                                   value="true" 
                                                   uncheckedValue="false" 
                                                   name="./badge" />
                                               <age jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield" 
                                                   fieldDescription="The maximum age in days the 'new' badge should be shown" 
                                                   fieldLabel="Max Product Age" 
                                                   name="./age"
                                                   min="{Long}0" 
                                                   value="10" />
                                               <ageTypeHint jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/foundation/form/hidden" 
                                                   ignoreData="{Boolean}true" 
                                                   name="./age@TypeHint" 
                                                   value="Long" />
                                           </items>
                                       </column>
                                   </items>
                               </columns>
                           </items>
                       </badge>
                   </items>
               </tabs>
           </items>
       </content>
   </jcr:root>
   ```

   Oben haben wir 2 weitere Felder als Teil einer neuen Registerkarte und ein einzelnes verstecktes Feld hinzugefügt.

   1. Kontrollkästchen zum Anzeigen des Zeichens &quot;Neu&quot;
   2. Zahlenfeld zum Definieren des maximalen Produktalters
   3. Ausgeblendetes Feld, um sicherzustellen, dass das maximale Produktalter als lang gespeichert wird (weitere Informationen finden Sie unter [@TypeHint](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) )

   Dialoge, die als Teil einer Proxykomponente definiert wurden, übernehmen alle vorhandenen Dialogfelder mit einer Funktion, die als [Sling Resource Merger](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/sling-resource-merger.html)bezeichnet wird. Daher müssen wir die vorhandenen Felder, die Teil des Product Teaser sind, nicht neu definieren.

1. Aktualisieren `productteaser.html` und fügen Sie eine `data-sly-test` zum `<div>` Zeichen hinzu. Dies ist ein einfacher Test, bei dem entschieden wird, das Zeichen zu rendern, wenn der Benutzer &quot;true&quot;markiert hat.

   ```html
       ...
       <div data-sly-test.isvalid="${product.url}" class="item__root" data-cmp-is="productteaser">
   
           <!--/* add test to see if properties.badge equals true */-->
           <div data-sly-test="${properties.badge == 'true'}" class="item__badge">
               <span>New</span>
           </div>
   ...
   ```

1. Stellen Sie den aktualisierten Code auf der lokalen Instanz der AEM mithilfe der Funktionen Ihrer IDE oder mithilfe Ihrer Maven-Fähigkeiten bereit:

   ```shell
   $ cd ui.apps
   $ mvn -PautoInstallPackage clean install
   ```

1. Kehren Sie zur Komponente &quot;Product Teaser&quot;zurück und klicken Sie auf das *Schraubenschlüsselsymbol* , um das Dialogfeld zu öffnen. Es sollte nun eine Registerkarte für **Abzeichen** mit zwei weiteren Feldern angezeigt werden. Das Aktualisieren dieser Felder behält die zu AEM Werte bei. Sie sollten die Markierung mit dem Kontrollkästchen aktivieren/deaktivieren können:

   ![Markierung umschalten](/help/commerce-cloud/assets/customize-cif-components/toggle-badge-checkbox.gif)

   Dadurch erhält der Autor eine gewisse Kontrolle darüber, wann das Zeichen angezeigt wird. Es wäre jedoch ideal, wenn das Zeichen automatisch verschwinden würde, sobald das Produkt ein bestimmtes Tagesalter erreicht hat, basierend auf dem Eintrag für **Max. Produktalter**. Dazu müssen wir eine gewisse Backend-Logik implementieren.

## Aktualisieren des Sling-Modells für den Product Teaser {#updating-sling-model-product-teaser}

Als Nächstes erweitern wir die Geschäftslogik des Product Teaser durch die Implementierung eines Sling-Modells. [Sling-Modelle](https://sling.apache.org/documentation/bundles/models.html)sind durch Anmerkungen angetriebene &quot;POJOs&quot;(Plain Old Java Objects), die eine beliebige Geschäftslogik implementieren, die von der Komponente benötigt wird. Sling-Modelle werden in Verbindung mit den HTML-Skripten als Teil der Komponente verwendet. Wir folgen dem [Delegationsmuster für Sling-Modelle](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) , sodass wir Teile des bestehenden Produktteaser-Modells einfach erweitern können.

Sling-Modelle werden als Java implementiert und können im **Kernmodul** des erstellten Projekts gefunden werden.

1. Öffnen Sie das Acme Store-Projekt in der IDE Ihrer Wahl und navigieren Sie unter dem **Core** -Modul zu: `core/src/main/java/com/acme/cif/core/models/MyProductTeaser.java`. **MyProductTeaser.java** ist eine von uns vorab erstellte Java-Schnittstelle, die die CIF- **ProductTeaser** -Schnittstelle erweitert.

1. Öffnen Sie als Nächstes die Datei **MyProductTeaserImpl.java** unter: `core/src/main/java/com/acme/cif/core/models/MyProductTeaserImpl.java`. `MyProductTeaserImpl` ist die Implementierungsklasse für die Schnittstelle `MyProductTeaser`.

   Mithilfe des [Delegationsmusters für Sling-Modelle](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) können wir die `ProductTeaser` Klasse über die `sling:resourceSuperType` Eigenschaft referenzieren:

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   Für alle Methoden, die wir nicht überschreiben oder ändern möchten, können wir einfach den `ProductTeaser` zurückgegebenen Wert zurückgeben:

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

1. Einer der zusätzlichen Erweiterungspunkte von AEM CIF Core Components ist der, `AbstractProductRetriever` der uns den Zugriff auf bestimmte Produktattribute erlaubt. Hinzufügen Sie die folgende Methode, um die `AbstractProductRetriever` in der `init()` Methode zu initialisieren:

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
   
       }
   ...
   ```

1. Testen Sie diese Änderungen, indem Sie den formatierten Preis ändern und die Logik in `getFormattedPrice()`überschreiben. Nehmen Sie die folgenden Aktualisierungen vor, damit wir den Preis explizit nach dem deutschen Gebietsschema formatieren. (oder wählen Sie ein anderes Land aus!)

   ```java
           import java.util.Locale;
           import java.text.NumberFormat;
            ...
   
               @Override
                   public String getFormattedPrice() 
                   {
                   //return productTeaser.getFormattedPrice();
                   NumberFormat germanCurrencyFormat = NumberFormat.getCurrencyInstance(Locale.GERMANY);
                   Double price =  productRetriever.fetchProduct().getPrice().getRegularPrice().getAmount().getValue();
                       if(price != null) 
                       {
                           return germanCurrencyFormat.format(price);
                       }
                   return null;
                   }
   ```

   Beachten Sie, wie das `productRetriever` Objekt uns Zugriff auf das `ProductInterface` Objekt über die `fetchProduct()` Methode gibt. Hier sehen Sie alle [verfügbaren Methoden](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java).

   > Hinweis* Das Ändern des Gebietsschemas in Deutsch ist nur ein lustiges Beispiel, um die Außerkraftsetzung zu sehen. In Wirklichkeit verwendet der ProductTeaser das Gebietsschema der [Seite, um das Format](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/internal/models/v1/productteaser/ProductTeaserImpl.java#L173)zu bestimmen.

1. Als Nächstes müssen wir die Datei **productteaser.html** im Modul **ui.apps** aktualisieren, um auf unser neues Sling-Modell zu verweisen unter: `com.acme.cif.core.models.MyProductTeaser`.

   ```diff
     <!--/* productteaser.html - change the use.product to point to MyProductTeaser */-->
     <sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html"
   -  data-sly-use.product="com.adobe.cq.commerce.core.components.models.productteaser.ProductTeaser"
   +  data-sly-use.product="com.acme.cif.core.models.MyProductTeaser"
      data-sly-use.actionsTpl="actions.html">
       ...
   ```

   Speichern Sie die Änderungen in `productteaser.html`.

1. Stellen Sie die Codebasis auf der lokalen Instanz von AEM bereit. Da Änderungen sowohl an den **ui.apps** - als auch an den **Core** -Modulen vorgenommen wurden, erstellen und stellen Sie das Projekt im Stammordner bereit:

   ```shell
   $ cd acme-store
   $ mvn -PautoInstallPackage clean install
   ```

1. Öffnen Sie einen Browser und navigieren Sie zu: [http://localhost:4502/system/console/status-slingmodels](http://localhost:4502/system/console/status-slingmodels). Diese Konsole zeigt alle Sling-Modelle an, die im System registriert sind. Überprüfen Sie die Dublette, um sicherzustellen, dass MyTeaserModelImpl bereitgestellt wurde und korrekt zugeordnet ist. Sie sollten Folgendes sehen können:

   ```plain
   com.acme.cif.core.models.MyProductTeaserImpl - acme/components/commerce/productteaser
   ```

1. Navigieren Sie schließlich zu dem Punkt, an dem Sie die Komponente Product Teaser erstellt haben, und Sie sollten nun den Preis im deutschen Währungsformat sehen:

   ![Preisformat aktualisiert](/help/commerce-cloud/assets/customize-cif-components/german-currency-update.png)

## Implementierung der Logik isShowBadge {#implement-isshowbadge}

Nun, da wir die Möglichkeit hatten, mit der Außerkraftsetzung der Sling-Modell-Methoden zu experimentieren, lassen Sie die Logik für den Zeitpunkt implementieren, wann das &quot;neue&quot; Zeichen anzuzeigen.

1. Kehren Sie zu Ihrer IDE zurück und öffnen Sie die Datei **MyProductTeaser.java** unter: `core/src/main/java/com/acme/cif/core/models/MyProductTeaser.java`.

1. Hinzufügen einer neuen Methode an `isShowBadge()` der Schnittstelle:

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   }
   ```

   Dies ist eine neue Methode, die wir einführen werden, um die Logik zu verkörpern, ob das Zeichen gezeigt werden soll oder nicht.

1. Als Nächstes öffnen Sie **MyProductTeaserImpl.java** unter `core/src/main/java/com/acme/cif/core/models/MyProductTeaserImpl.java`.

1. Die Logik, wie lange das &quot;neue&quot;Zeichen angezeigt wird, basiert auf dem `created_at` Attribut des Produkts. Um Zugriff auf dieses Attribut zu haben, müssen wir die **GraphQL** -Abfrage des ProductTeaser erweitern. Dazu aktualisieren wir die `init()` Methode in **MyProductTeaserImpl.java**:

   ```java
   //MyProductTeaserImpl.java
   
   @PostConstruct
   public void initModel() {
       productRetriever = productTeaser.getProductRetriever();
   
       if (productRetriever != null) {
           // Pass your custom partial query to the ProductRetriever. This class will
           // automatically take care of executing your query as soon
           // as you try to access any product property.
           productRetriever.extendProductQueryWith(p ->
               p.addCustomSimpleField("created_at")
           );
       }
   }
   ```

   Das Hinzufügen der `extendProductQueryWith` Methode ist eine leistungsstarke Methode, um sicherzustellen, dass dem Rest des Modells zusätzliche Produktattribute zur Verfügung stehen. Außerdem wird die Anzahl der ausgeführten Abfragen minimiert.

   >[!NOTE]
   >Im obigen Code verwenden wir die`addCustomSimpleField` , um die `created_at` Eigenschaft abzurufen. Dies zeigt, wie Sie Abfragen für benutzerdefinierte Attribute durchführen können, die Teil des Magento-Schemas sind.
   >
   > Die `created_at` Eigenschaft wurde jedoch im Rahmen der [Produktoberfläche](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java) implementiert, und eine bessere Vorgehensweise wäre die Wiederverwendung der Methode wie die folgende: `productRetriever.extendProductQueryWith(p -> p.createdAt());`. Die meisten häufig gefundenen Schema-Attribute wurden implementiert. Verwenden Sie daher nur die `addCustomSimpleField` für echte benutzerdefinierte Attribute.

1. Als Nächstes werden wir die `isShowBadge()` Methode implementieren:

   ```java
   import java.time.format.DateTimeFormatter;
   import java.util.Locale;
   import java.time.temporal.ChronoUnit;
   
   ...
   
   @Override
   public Boolean isShowBadge() {
        final DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
   
        //Look at the checkbox from the dialog to see if we should even attempt to show the badge
        final boolean showBadge = properties.get("badge", false);
        if (showBadge) {
   
            //Look at the numberfield set from the dialog to determine the max "age" in days to compare too
            final int maxAgeProp = properties.get("age", 0);
   
           String createdAtString;
           try {
               //Grab the created_at property from the product
               //Here we show the example of retrieving the attribute as if it was a custom attribute
               // an alternative that would work is productRetriever.fetchProduct().getCreatedAt()
               createdAtString = productRetriever.fetchProduct().getAsString("created_at");
               log.info("***CREATED_AT**** " + createdAtString);
           } catch (SchemaViolationError e) {
               //it is possible that a schema error could be thrown if the attribute is not part of the schema
               log.error("Error determining to showBadge" , e);
               return false;
           }
   
            // Custom code to calc the date difference of the product creation
            // compared to today
           final LocalDate createdAt = LocalDate.parse(createdAtString, formatter);
            if (createdAt != null) {
   
                final long ageInDays = ChronoUnit.DAYS.between(createdAt, LocalDate.now());
                if (ageInDays < maxAgeProp) {
                    return true;
                }
            }
        }
        return false;
    }
   ```

   In der obigen Methode überprüfen wir zunächst, ob der Autor die Abzeichen-Funktion mit dem Kontrollkästchen aktiviert hat. Als Nächstes lesen wir in den Wert der Eigenschaft, `age` die als Teil des Dialogs festgelegt wird und die maximale Anzahl der Tage, die ein Produkt sein sollte, bis das Banner verschwindet. Schließlich berechnen wir, wie alt das Produkt auf dem `created_at` Datum basiert. Wenn wir nach dem Vergleich der beiden Werte zurückkehren, `true` um das Zeichen anzuzeigen, in allen anderen Fällen `false` .

1. Schließlich muss noch eine weitere Ergänzung zum `productteaser.html` Skript vorgenommen werden, um die `isShowBadge()` Methode aufzurufen. Öffnen Sie die Datei unter `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser/productteaser.html`. Führen Sie die folgende Aktualisierung durch:

   ```diff
   ...
   - <div data-sly-test="${properties.badge == 'true'}" class="item__badge">
   + <div data-sly-test="${product.showBadge}" class="item__badge">
        <span>New</span>
    </div>
   ...
   ```

1. Stellen Sie die Codebasis auf der lokalen Instanz von AEM bereit. Da Änderungen sowohl an den **ui.apps** - als auch an den **Core** -Modulen vorgenommen wurden, erstellen und stellen Sie das Projekt im Stammordner bereit:

   ```shell
   $ cd acme-store
   $ mvn -PautoInstallPackage clean install
   ```

1. Kehren Sie zur Komponente ProductTeaser zurück und experimentieren Sie mit verschiedenen Zahlen, um das maximale Alter des Produkts anzuzeigen. Je nachdem, wie alt das Produkt ist, müssen Sie möglicherweise sehr große Zahlen eingeben, um das Zeichen anzuzeigen.

   ![Max. Produktalter 999](/help/commerce-cloud/assets/customize-cif-components/max-age-working.png)

1. Suchen Sie schließlich nach den AEM Protokollen, um die in Schritt 5 eingegebene Protokollanweisung anzuzeigen. Dadurch wird der Wert der `created_at` Eigenschaft gedruckt, die von Magento stammt. Sie können die Protokolle der AEM durch Öffnen der `error.log` Datei Ansicht werden. Diese Datei befindet sich unter der `crx-quickstart/logs/error.log` , in der die AEM JAR installiert wurde. Es wird erwartet, dass ein Zeileneintrag wie der folgende angezeigt wird:

   ```plain
   com.acme.cif.core.models.MyProductTeaser ***CREATED_AT**** 2019-06-05 06:51:33
   ```

   Jetzt können Sie überprüfen, ob die Logik, die wir implementiert haben, korrekt ist!

### Herzlichen Glückwunsch {#congratulations}

Sie haben gerade Ihre erste AEM CIF-Komponente angepasst! Laden Sie das [fertige Lösungspaket hier](/help/commerce-cloud/assets/customize-cif-components/acme-store-solution.zip)herunter.

## Zusätzliche Ressourcen {#additional-resources}

* [AEM](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)
* [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components)
* [Anpassen AEM CIF-Hauptkomponenten](https://github.com/adobe/aem-core-cif-components/wiki/Customizing-CIF-Core-Components)
* [Anpassen der Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html)
