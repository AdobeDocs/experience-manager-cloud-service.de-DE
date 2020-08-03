---
title: Stil AEM CIF-Kernkomponenten
description: Stil AEM CIF-Kernkomponenten
translation-type: tm+mt
source-git-commit: 48805b21500ff3f2629efd6aecb40bb1cdc38cd6
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 4%

---


# Stil AEM CIF-Kernkomponenten {#style-aem-cif-core-components}

Der [CIF-Projektarchetyp](https://github.com/adobe/aem-cif-project-archetype) bildet einen minimalen Adobe Experience Manager (AEM) CIF als Ausgangspunkt für Kundenprojekte mit [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components). Ein Standardstil, bekannt als &quot;Venia&quot;, wird zunächst auf die Site angewendet. In diesem Tutorial werden Sie ein neues AEM CIF-Projekt, generiert durch den Archetyp und verstehen, wie CSS und JavaScript verwendet von AEM CIF Core Komponenten organisiert werden. Sie erstellen außerdem einen neuen Stil mit CSS, um den Standardstil der Komponente Product Teaser zu ersetzen.

![Was Sie erstellen](/help/commerce-cloud/assets/style-cif-component/what-you-will-build.png)

>[!NOTE]
> Für die Komponente Product Teaser, die einer Karte ähnelt, wird ein neuer Stil implementiert.

## Voraussetzungen {#prerequisites}

Folgende Werkzeuge und Technologien sind erforderlich:

* [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/index.html) oder [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html) (nur AEM 6.5+)
* [Apache Maven](https://maven.apache.org/) (3.3.9 oder neuer)
* Adobe Experience Manager (lokale Instanz)
   * [AEM 6.5](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/introduction/technical-requirements.html)
   * [AEM 6.4.4+](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/sp-release-notes.html)
* Magento mit einer mit dem Archetyp kompatiblen [Version](https://github.com/adobe/aem-cif-project-archetype#requirements)

## Projekt erstellen {#generate-project}

Wir erstellen ein neues AEM CIF-Projekt mit dem [CIF-Projektarchetyp](https://github.com/adobe/aem-cif-project-archetype) und überschreiben dann die Standardstile.

**Sie können ein vorhandenes Projekt** (basierend auf dem CIF-Projektarchiv) verwenden und diesen Abschnitt überspringen.

1. Bestimmen Sie die neueste Version des CIF-Projektarchetyps, indem Sie [die neueste Version auf GitHub](https://github.com/adobe/aem-cif-project-archetype/releases/latest)anzeigen. Ersetzen Sie im nächsten Schritt `x.y.z` die Version der neuesten Version.

1. Führen Sie den folgenden Maven-Befehl aus, um ein neues Projekt im [Stapelmodus](https://maven.apache.org/archetype/maven-archetype-plugin/examples/generate-batch.html)zu erstellen.

   ```terminal
   mvn archetype:generate -B \
       -DarchetypeGroupId="com.adobe.commerce.cif" \
       -DarchetypeArtifactId="cif-project-archetype" \
       -DarchetypeVersion=x.y.z \
       -DgroupId="com.acme.cif" \
       -DartifactId="acme-store" \
       -Dversion=0.0.1-SNAPSHOT \
       -Dpackage="com.acme.cif" \
       -DappsFolderName="acme" \
       -DartifactName="Acme Store" \
       -DcontentFolderName="acme" \
       -DpackageGroup="acme" \
       -DsiteName="Acme Store" \
       -DoptionAemVersion=6.5.0 \
       -DoptionIncludeExamples=y \
       -DoptionEmbedConnector=y
   ```

1. Erstellen Sie das Projekt und stellen Sie es auf einer lokalen Instanz AEM bereit:

   ```shell
   $ cd acme-store/
   $ mvn clean install -PautoInstallAll
   ```

1. Hinzufügen Sie die erforderlichen OSGi-Konfigurationen, um Ihre AEM mit einer Magento-Instanz zu verbinden oder die Konfigurationen dem neu erstellten Projekt hinzuzufügen.

1. An dieser Stelle sollten Sie über eine funktionierende Version eines Stores verfügen, der mit einer Magento-Instanz verbunden ist. Navigieren Sie zur Seite `US` > `Home` unter: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

   Sie sollten sehen, dass das Schaufenster derzeit das Thema Venia verwendet. Wenn Sie das Hauptmenü des Schaufensters erweitern, sollten Sie verschiedene Kategorien sehen, die darauf hinweisen, dass das Magento der Verbindung funktioniert.

   ![Schaufenster mit Venia-Design konfiguriert](/help/commerce-cloud/assets/style-cif-component/acme-store-configured.png)

## Einführung in Client-Bibliotheken {#introduction-to-client-libraries}

Die CSS und JavaScript, die für die Wiedergabe des Themas/der Stile des Stores verantwortlich sind, werden in AEM von einer [Client-Bibliothek](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html) oder clientlibs verwaltet. Client-Bibliotheken bieten einen Mechanismus zum Organisieren von CSS und JavaScript im Code eines Projekts und zur anschließenden Bereitstellung auf der Seite.

Die Anwendung markenspezifischer Stile auf die CIF-Kernkomponenten erfolgt durch Hinzufügen und Überschreiben des von diesen Client-Bibliotheken verwalteten CSS. Die Kenntnis, wie Client-Bibliotheken strukturiert und auf der Seite eingeschlossen sind, ist von entscheidender Bedeutung.

### Projektclientbibliotheken {#project-client-libraries}

Als Nächstes werden wir die vom Archetyp automatisch generierten Client-Bibliotheken überprüfen. Verwenden Sie die IDE Ihrer Wahl, um das in der vorherigen Übung [erstellte Projekt zu](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment)importieren.

1. Navigieren Sie zum Modul **ui.apps** und erweitern Sie die Ordnerhierarchie um: `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs`:

   ![ui.apps clientlibs](/help/commerce-cloud/assets/style-cif-component/ui-apps-clientli-folder.png)

   Es gibt zwei Ordner unter, **clientlib-base** und **theme**.

1. **clientlib-base** - Dies ist eine leere Client-Bibliothek, die einfach die erforderlichen Abhängigkeiten von [AEM Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html)einbettet.

   ![Clientlib-base](/help/commerce-cloud/assets/style-cif-component/clientlib-base-folderhierarchy.png)

   Nachfolgend finden Sie die XML-Definition von **clientlib-base** (die `.content.xml` -Datei):

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:ClientLibraryFolder"
       allowProxy="{Boolean}true"
       categories="[acme.wcm.base]"
       embed="[core.wcm.components.accordion.v1,core.wcm.components.tabs.v1,core.wcm.components.carousel.v1,core.wcm.components.image.v2,core.wcm.components.breadcrumb.v2,core.wcm.components.search.v1,core.wcm.components.form.text.v2]"/>
   ```

   `acme.wcm.base` ist die Kategorie für diese Client-Bibliothek. Stellen Sie sich eine Kategorie als Tag vor. Auf diese Weise wird die Bibliothek auf der Seite eingefügt oder eingebettet.

   Beachten Sie die `embed` Eigenschaft und das Array anderer clientlib-Kategorien. Jede dieser Kategorien stellt eine Client-Bibliothek dar. Enthält beispielsweise `core.wcm.components.accordion.v1` das Javascript, das erforderlich ist, damit die [Akkordeon-Komponente](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/accordion.html) funktioniert.

   Mithilfe der `embed` und- `categories` Eigenschaften können Sie Clientbibliotheken aus verschiedenen Projekten verwalten und einschließen.

   `allowProxy=true` stellt sicher, dass die Client-Bibliothek CSS und JavaScript von einem Pfad bereitgestellt wird, dem Folgendes vorangestellt wird: `/etc.clientlibs`. Dadurch wird sichergestellt, dass der Anwendungscode unter `/apps` dem Schutz vor Endbenutzern bleibt, dass jedoch CSS und JavaScript, die für die Funktion der Website erforderlich sind, anonym bereitgestellt werden können. More details about the [allowProxy property can be found here](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet).

1. **theme** - Dies ist die Client-Bibliothek, die das Startthema und CSS für das CIF-Projekt enthält. Diese Client-Bibliothek ist für jede Implementierung angepasst. Es ist hilfreich, mit einigen vorhandenen Stilen Beginn zu führen, damit die Komponenten für den Beginn verwendet werden können.

   ![theme clientlibrary](/help/commerce-cloud/assets/style-cif-component/clientlib-theme-folder-hierarchy.png)

   Nachfolgend finden Sie die XML-Definition des **Designs**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:ClientLibraryFolder"
       allowProxy="{Boolean}true"
       categories="[acme.theme]"/>
   ```

   `acme.theme` ist die Kategorie für diese Client-Bibliothek und so wird die Client-Bibliothek auf der Seite eingeschlossen.

1. Unter der **Design** -Client-Bibliothek sollte eine Datei mit dem Namen **css.txt** angezeigt werden: `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs/theme/css.txt`:

   ```plain
   #base=.
   common/common.css
   
   components/button/button.css
   
   components/featuredcategorylist/categorylist.css
   
   ...
   ```

   Die Datei **css.txt** (und **js.txt**) fungiert als Manifest, das die Reihenfolge vorgibt, in der einzelne Dateien in der endgültigen CSS-Datei enthalten sind. Bestellen ist wichtig sowohl für CSS als auch für JavaScript und es ist schön, mehrere Dateien zu erstellen, um den Code besser zu verwalten. Wenn Sie sich die Datei **css.txt** ansehen, sehen Sie, dass die Dateien von den Komponenten organisiert sind, auf die die Stile angewendet werden.

1. Inspect Sie die CSS-Dateien unter dem **Design/den Komponenten** , um eine Vorstellung von den OOB-Komponentenstilen zu erhalten. Einige dieser Dateien werden später im Tutorial aktualisiert.

### Einbindung der Client-Bibliothek in die Basisseitenkomponente

Als Nächstes werden wir überprüfen, wie Client-Bibliotheken auf einer Seite mit [HTL](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#using-htl) und der Seitenkomponente eingeschlossen werden.

1. Navigieren Sie im **Modul ui.apps** zur `page` Komponentendefinition unter: `ui.apps/src/main/content/jcr_root/apps/acme/components/structure/page`. Diese vom Archetyp generierte **Seitenkomponente** ist der Einstiegspunkt, der zum Rendern aller Seiten im Projekt verwendet wird.

1. Wenn Sie die Definition ( **) der** Seitenkomponente`page/.content.xml`überprüfen, wird eine Eigenschaft angezeigt, auf die `sling:resourceSuperType` verweist `core/cif/components/structure/page/v1/page`. Das bedeutet, dass die **Seitenkomponente** unseres Projekts (Acme) alle Funktionen der [CIF-Core-Page](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/structure/page/v1/page) -Komponente erbt und es uns ermöglicht, weniger Code zu verwalten.

1. Unter der **Seitenkomponente** befinden sich zwei Dateien: **customheaderlibs.html** und **customfooterlibs.html**.

   ```html
   <!--/* customheaderlibs.html */-->
   <sly data-sly-use.clientLib="/libs/granite/sightly/templates/clientlib.html"
    data-sly-call="${clientlib.css @ categories='acme.wcm.base'}"/>
   ```

   **customheaderlibs.html** ist ein HTML-Skript, das am Anfang der Seite wiedergegeben wird. Es ist ein gängiges Skript, um projektspezifische Logik zu überschreiben und hinzuzufügen. In diesem Fall verwenden wir es, um die Client-Bibliothek mit einer Kategorie von einzuschließen `acme.wcm.base`. Nach den Best Practices für die Webentwicklung nehmen wir nur die CSS in den Kopf der Seite.

   ```html
   <!--/* customfooterlibs.html */-->
   <sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
       <sly data-sly-call="${clientlib.js @ categories='acme.wcm.base'}"/>
   </sly>
   ```

   **customfooterlibs.html** ist ein HTML-Skript, das am Ende der Seite direkt vor dem schließenden `</body>` -Tag gerendert wird. Wieder wird die Kategorie von verwendet, aber diesmal wird nur das JavaScript der Client-Bibliothek geladen. `acme.wcm.base`

Das Ändern der HTML-Skripten der **Seitenkomponente** ist, wie auf allen Seiten eingeschlossen `acme.wcm.base` wird. Was aber ist mit `acme.theme`? In der nächsten Übung werden wir eine weitere Möglichkeit prüfen, Client-Bibliotheken einzubeziehen.

### Einbindung der Client-Bibliothek in Seitenvorlagen {#client-library-inclusion-pagetemplates}

Es gibt mehrere Optionen zum Einschließen einer clientseitigen Bibliothek. Als Nächstes prüfen wir, wie das generierte Projekt die clientseitigen Designbibliotheken über [Seitenvorlagen](https://docs.adobe.com/content/help/en/experience-manager-65/developing/platform/templates/page-templates-editable.html)enthält.

Öffnen Sie einen neuen Browser und melden Sie sich bei der AEM Instanz an, in der Sie das Projekt zu Beginn dieses Lernprogramms bereitgestellt haben.

1. Navigieren Sie im Bildschirm &quot;AEM Beginn&quot;zu **Extras** > **Allgemein** > **Vorlagen**.

   ![Vorlagennavigation](/help/commerce-cloud/assets/style-cif-component/template-location.png)

1. Navigieren Sie zum Ordner &quot; **Acme Store-Konfiguration** &quot;. Öffnen Sie die Seitenvorlage **der** Kategorie, indem Sie auf das *Stiftsymbol* klicken.

   ![Vorlagenkarte der Kategorie](/help/commerce-cloud/assets/style-cif-component/category-page-template.png)

1. Wählen Sie in der oberen linken Ecke das Symbol **Seiteninformationen** und klicken Sie auf **Seitenrichtlinie**.

   ![Menüelement Seitenrichtlinie](/help/commerce-cloud/assets/style-cif-component/page-policy-menu.png)

1. Dadurch wird die Seitenrichtlinie für die Vorlage &quot;Katalogseite&quot;geöffnet:

   ![Seitenrichtlinie - Katalogseite](/help/commerce-cloud/assets/style-cif-component/page-policy-properties.png)

   Auf der rechten Seite sehen Sie eine Liste der Client-Bibliotheken- **Kategorien** , die auf allen Seiten, die diese Vorlage verwenden, enthalten sind.

   * **wcm.foundation.components.page.responsive** - Stellt die CSS bereit, die zum Aktivieren [responsiver Layout](https://docs.adobe.com/content/help/de-DE/experience-manager-65/authoring/siteandpage/responsive-layout.html) -Steuerelemente durch Autoren erforderlich sind.
   * **acme.theme** - Dies ist das Startthema, das der Archetyp automatisch generiert. Standardmäßig ist dieser Stil wie der Beispiel-Venia Demo Store. Wie Sie jedoch aus dem Namen sehen können, ist er für die Implementierung des Projekts vorgesehen. *Das wird im nächsten Abschnitt geändert!*
   * **core.cif.components.response** - Dies ist eine kompilierte Client-Bibliothek mit mehreren React-Komponenten, die für dynamische Funktionen wie den Warenkorb verwendet werden. More [information can be found here](https://github.com/adobe/aem-core-cif-components/tree/master/react-components).

   Beachten Sie, dass andere Vorlagen die gleiche Richtlinie verwenden, **Inhaltsseite**, **Landingpage** usw... Durch die Wiederverwendung derselben Richtlinie können wir sicherstellen, dass dieselben Client-Bibliotheken auf allen Seiten enthalten sind.

   Der Vorteil der Verwendung von Vorlagen und Seitenrichtlinien zur Verwaltung der Einbeziehung von Clientbibliotheken besteht darin, dass Sie die Richtlinie pro Vorlage ändern können. Sie verwalten beispielsweise zwei verschiedene Marken innerhalb derselben AEM Instanz. Jede Marke hat ihren eigenen Stil oder *Design* , aber die Basisbibliotheken und der Code sind identisch. Ein weiteres Beispiel: Wenn Sie eine größere Client-Bibliothek hätten, die Sie nur auf bestimmten Seiten anzeigen möchten, könnten Sie eine eindeutige Seitenrichtlinie nur für diese Vorlage erstellen. Der andere Vorteil

### Clientbibliotheken auf der Seite überprüfen {#verify-client-libraries}

An diesem Punkt haben wir überprüft, wie Client-Bibliotheken mit HTML mit den **customheaderlibs.html** - und **customfooterlibs.html** -Skripten eingeschlossen werden und wie die Seitenrichtlinie einer Vorlage verwendet werden kann, um zusätzliche Client-Bibliotheken einzuschließen. Als Nächstes überprüfen wir die Einbeziehung der Client-Bibliotheken auf der Website.

1. Navigieren Sie im Bildschirm AEM Beginn zu **Sites** > **Acme Store** > **Vereinigte Staaten** > **Englisch** und öffnen Sie die Seite zur Bearbeitung: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html).

1. Wählen Sie das Menü **Seiteninformationen** aus und klicken Sie auf **Ansicht als veröffentlicht**:

   ![Als veröffentlicht anzeigen](/help/commerce-cloud/assets/style-cif-component/view-as-published.png)

   Dadurch wird die Seite geöffnet, ohne dass der AEM Autor Javascript geladen wurde, wie es auf der veröffentlichten Site angezeigt würde. Beachten Sie, dass an die URL der Parameter Abfrage `?wcmmode=disabled` angehängt ist. Bei der Entwicklung von CSS und JavaScript ist es eine gute Vorgehensweise, diesen Parameter zu verwenden, um die Seite zu vereinfachen, ohne dass AEM Autor etwas davon hat.

1. Ansicht der Seitenquelle und Sie sollten die folgenden Client-Bibliotheken identifizieren können: **acme.wcm.base**, **wcm.foundation.components.page.responsive**, **acme.theme**, **core.cif.components.response**

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/acme/clientlibs/clientlib-base.css" type="text/css">
       <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/acme/clientlibs/theme.css" type="text/css">
   </head>
   ...
   
       <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/react-components.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/acme/clientlibs/clientlib-base.js"></script>
   </body>
   </html>
   ```

## Stil des Produkt-Teasers {#style-product-teaser}

Nachdem wir nun die vom Archetyp generierte Client-Bibliotheksstruktur verstehen, können wir beginnen, die AEM CIF-Kernkomponenten anzupassen. Wir werden die Stile der Komponente Product Teaser ändern, sodass sie eher wie eine &quot;Karte&quot; aussieht.

### Authoring des Produkt-Teasers {#author-product-teaser}

Als ersten Schritt fügen wir der Startseite unserer Site mithilfe der AEM Authoring-Werkzeuge eine neue Instanz der Komponente Product Teaser hinzu.

1. Öffnen Sie eine neue Browserregisterkarte und navigieren Sie zur **Startseite** der Site: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html).

1. Fügen Sie eine neue **Product Teaser** -Komponente in den Container des Hauptlayouts auf der Seite ein.

   ![Produktbeschleuniger einfügen](/help/commerce-cloud/assets/style-cif-component/product-teaser-add-component.png)

1. Erweitern Sie das Seitenbedienfeld (falls noch nicht umgeschaltet) und wechseln Sie in das Dropdown-Feld für die Asset-Suche zu **Produkte**. Dies sollte eine Liste der verfügbaren Produkte einer angeschlossenen Magento-Instanz anzeigen. Wählen Sie ein Produkt aus und **ziehen** Sie es per Drag &amp; Drop auf die Komponente **Product Teaser** auf der Seite.

   ![Drag &amp; Drop Product Teaser](/help/commerce-cloud/assets/style-cif-component/drag-drop-product-teaser.png)

   > Beachten Sie, dass Sie das angezeigte Produkt auch konfigurieren können, indem Sie die Komponente mithilfe des Dialogfelds konfigurieren (indem Sie auf das *Schraubenschlüsselsymbol* klicken).

1. Sie sollten nun sehen, dass ein Produkt vom Produkt-Teaser angezeigt wird. Der Name des Produkts und der Preis des Produkts sind Standardattribute, die angezeigt werden.

   ![Product Teaser - Standardstil](/help/commerce-cloud/assets/style-cif-component/product-teaser-default-style.png)

### CSS für den Produkt-Teaser aktualisieren {#update-css-product-teaser}

Als Nächstes wird das CSS in der **Design** -Client-Bibliothek geändert, um einen kartenähnlichen Stil für den Product Teaser zu implementieren.

Kehren Sie zur IDE und zum erstellten Projekt zurück.

1. Navigieren Sie im **Modul ui.apps** zu Ordner: `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs/theme/components/productteaser`. Hier werden alle Stile für den Product Teaser definiert.

1. Öffnen Sie die Datei &quot; **teaser.css** &quot;und aktualisieren Sie die entsprechenden CSS-Regeln (oder laden Sie die [Lösungsdatei &quot;teaser.css&quot;herunter und ersetzen Sie sie](/help/commerce-cloud/assets/style-cif-component/solution-teaser.css) ).

   Hinzufügen Sie einen Schlagschatten und schließen Sie abgerundete Ecken in den Produktteaser ein.

   ```css
    .productteaser .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .productteaser .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

   Ändern Sie den Rahmen für das Bild im Produktester.

   ```css
   .productteaser .item__image {
       border-bottom: 1px solid #c0c0c0;
       display: block;
       grid-area: main;
       height: auto;
       opacity: 1;
       transition-duration: 512ms;
       transition-property: opacity, visibility;
       transition-timing-function: ease-out;
       visibility: visible;
       width: 100%;
    }
   ```

   Aktualisieren Sie den Produktnamen, damit er unten im Teaser angezeigt wird, und ändern Sie die Textfarbe.

   ```css
   .productteaser .item__name {
       color: #000;
       display: block;
       float: left;
       font-size: 22px;
       font-weight: 900;
       line-height: 1em;
       padding: 0.75em;
       text-transform: uppercase;
       width: 75%;
   }
   ```

   Aktualisieren Sie den Produktpreis, damit er auch unten im Teaser angezeigt wird, und ändern Sie die Textfarbe.

   ```css
   .productteaser .item__price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   }
   ```

   Aktualisieren Sie die Media-Abfrage am unteren Rand, um den Namen und den Preis in Bildschirmen unter 992 px zu stapeln.

   ```css
   @media (max-width: 992px) {
       .productteaser .item__name {
           font-size: 18px;
           width: 100%;
       }
       .productteaser .item__price {
           font-size: 14px;
           width: 100%;
       }
   }
   ```

   Speichern Sie die Änderungen in **teaser.css**. Sie können die [Lösungsdatei teaser.css hier](/help/commerce-cloud/assets/style-cif-component/solution-teaser.css)herunterladen.

1. Stellen Sie die Updates des Moduls **ui.apps** bereit, damit Sie Ihre Maven-Fähigkeiten AEM verwenden, über ein Befehlszeilenterminal:

   ```shell
           $ cd acme-store/ui.apps/
           $ mvn -PautoInstallPackage clean install
           ...
           saving approx 0 nodes...
           Package imported.
           Package installed in 61ms.
           [INFO] ------------------------------------------------------------------------
           [INFO] BUILD SUCCESS
           [INFO] ------------------------------------------------------------------------
           [INFO] Total time:  6.903 s
           [INFO] Finished at: 2020-02-06T13:21:36-08:00
            [INFO] ------------------------------------------------------------------------
   ```

   >[!NOTE]
   >Es gibt zusätzliche [IDE-Einstellungen und -Tools](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) , die Projektdateien direkt mit einer lokalen AEM synchronisieren können, ohne einen vollständigen Maven-Build durchführen zu müssen.

### Ansicht - Aktualisierter Produkteditor {#view-updated-product-teaser}

Nachdem der Code für das Projekt in AEM bereitgestellt wurde, sollten wir nun die Änderungen am Product Teaser sehen können.

1. Kehren Sie zu Ihrem Browser zurück und aktualisieren Sie die Startseite: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html). Es sollten die aktualisierten Produkteaser-Stile angewendet werden.

   ![Aktualisierter Produkteaser-Stil](/help/commerce-cloud/assets/style-cif-component/product-teaser-new-style.png)

1. Experimentieren Sie, indem Sie zusätzliche Produktester hinzufügen. Mit dem Layoutmodus können Sie die Breite und den Versatz der Komponenten ändern, um mehrere Teaser in einer Zeile anzuzeigen.

   ![Mehrere Teaser](/help/commerce-cloud/assets/style-cif-component/multiple-teasers-final.png)

   >[!NOTE]
   >Jeder Produkt-Teaser enthält denselben Stil.

### Fehlerbehebung {#troubleshooting}

Sie können in [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) überprüfen, ob die aktualisierte CSS-Datei bereitgestellt wurde: [http://localhost:4502/crx/de/index.jsp#/apps/acme/clientlibs/theme/components/productteaser/teaser.css](http://localhost:4502/crx/de/index.jsp#/apps/acme/clientlibs/theme/components/productteaser/teaser.css)

Bei der Bereitstellung neuer CSS- und/oder JavaScript-Dateien ist es ebenfalls wichtig sicherzustellen, dass der Browser keine gestörten Dateien bereitstellt. Sie können dies vermeiden, indem Sie den Browser-Cache leeren oder eine neue Browsersitzung starten.

AEM versucht auch, Clientbibliotheken für die Leistung zwischenzuleiten. Gelegentlich werden nach einer Codebereitstellung die älteren Dateien verarbeitet. Mit dem Tool [Client-Bibliotheken neu erstellen können Sie den Cache AEM Client-Bibliothek manuell deaktivieren](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html). *Ungültige Caches sind die bevorzugte Methode, wenn Sie vermuten, dass AEM eine alte Version einer Client-Bibliothek zwischengespeichert hat. Die Wiederherstellung von Bibliotheken ist ineffizient und zeitaufwendig.*

### Herzlichen Glückwunsch {#congratulations}

Sie haben gerade Ihre erste AEM CIF Core-Komponente gestylt!

### Bonus-Herausforderung {#bonus-challenge}

Verwenden Sie das [AEM-Stilsystem](https://docs.adobe.com/content/help/de-DE/experience-manager-65/developing/components/style-system.html) , um zwei Stile zu erstellen, die von einem Inhaltsersteller aktiviert/deaktiviert werden können. [Die Entwicklung mit dem Stilsystem](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html) umfasst detaillierte Schritte und Informationen dazu, wie dies zu erreichen ist.

![Bonus Challenge - Style System](/help/commerce-cloud/assets/style-cif-component/bonus-challenge.png)

## Zusätzliche Ressourcen {#additional-resources}

* [AEM CIF-Archetyp](https://github.com/adobe/aem-cif-project-archetype)

* [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components)

* [Einrichten einer Umgebung zur lokalen AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)

* [Client-seitige Bibliotheken](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html)
* [Erste Schritte mit AEM Sites](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

* [Entwickeln mit dem Stilsystem](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html)
