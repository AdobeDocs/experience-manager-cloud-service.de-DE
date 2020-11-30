---
title: Stil AEM CIF-Kernkomponenten
description: Erfahren Sie, wie Sie die CIF-Hauptkomponenten gestalten AEM. Das Lernprogramm beschreibt, wie clientlibs und clientlibs zum Bereitstellen und Verwalten von CSS und JavaScript für eine Adobe Experience Manager (AEM) Commerce-Implementierung verwendet werden. In diesem Lernprogramm wird auch erläutert, wie das ui.frontend-Modul und ein Webpack-Projekt in den End-to-End-Build-Prozess integriert werden.
sub-product: Commerce
topics: Development
version: cloud-service
doc-type: tutorial
activity: develop
audience: developer
feature: Commerce Integration Framework
kt: 3456
thumbnail: 3456-style-cif.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '2592'
ht-degree: 5%

---


# Style AEM CIF Core Components {#style-aem-cif-core-components}

Das [CIF Venia Project](https://github.com/adobe/aem-cif-guides-venia) ist eine Referenz-Codebasis für die Verwendung der [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components). In diesem Tutorial werden Sie das Venia-Referenzprojekt untersuchen und verstehen, wie CSS und JavaScript von AEM CIF-Kernkomponenten organisiert werden. Außerdem erstellen Sie mithilfe von CSS einen neuen Stil, um den Standardstil der Komponente **Product Teaser** zu aktualisieren.

>[!TIP]
>
> Verwenden Sie den [AEM Projektarchiv](https://github.com/adobe/aem-project-archetype) , wenn Sie Ihre eigene Commerce-Implementierung starten.

## Was Sie erstellen

In diesem Lernprogramm wird ein neuer Stil für die Komponente Product Teaser implementiert, die einer Karte ähnelt. Die im Lernprogramm gelernten Lektionen können auf andere CIF-Kernkomponenten angewendet werden.

![Was Sie erstellen](../assets/style-cif-component/what-you-will-build.png)

## Voraussetzungen {#prerequisites}

Zum Abschluss dieses Lernprogramms ist eine lokale Umgebung erforderlich. Dazu gehört eine laufende Instanz von AEM, die konfiguriert ist und mit einer Magento-Instanz verbunden ist. Überprüfen Sie die Anforderungen und Schritte zum [Einrichten einer lokalen Entwicklung mit AEM als Cloud Service-SDK](../develop.md).

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

   ![Storefront mit Venia-Design konfiguriert](../assets/style-cif-component/venia-store-configured.png)

## Client-Bibliotheken und ui.frontend-Modul {#introduction-to-client-libraries}

Die CSS und JavaScript, die für die Wiedergabe des Themas/der Stile des Stores verantwortlich sind, werden in AEM von einer [Client-Bibliothek](/help/implementing/developing/introduction/clientlibs.md) oder clientlibs verwaltet. Client-Bibliotheken bieten einen Mechanismus zum Organisieren von CSS und JavaScript im Code eines Projekts und zur anschließenden Bereitstellung auf der Seite.

Markenspezifische Stile können auf AEM CIF-Kernkomponenten angewendet werden, indem das von diesen Clientbibliotheken verwaltete CSS hinzugefügt und überschrieben wird. Die Kenntnis, wie Client-Bibliotheken strukturiert und auf der Seite eingeschlossen sind, ist von entscheidender Bedeutung.

Das [ui.frontend](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/uifrontend.html) ist ein dediziertes [Webpack](https://webpack.js.org/) Projekt, um alle Front-End-Assets für ein Projekt zu verwalten. Dadurch können Front-End-Entwickler eine beliebige Anzahl von Sprachen und Technologien wie [TypeScript](https://www.typescriptlang.org/), [Sass](https://sass-lang.com/) und vieles mehr verwenden.

Das `ui.frontend` Modul ist auch ein Maven-Modul und mit dem größeren Projekt durch den Einsatz eines NPM-Moduls, dem [aem-clientlib-Generator](https://github.com/wcm-io-frontend/aem-clientlib-generator), integriert. Während eines Builds `aem-clientlib-generator` kopiert die kompilierte CSS- und JavaScript-Datei in eine Client-Bibliothek im `ui.apps` Modul.

![ui.frontend zur ui.apps-Architektur](../assets/style-cif-component/ui-frontend-architecture.png)

*Kompilierte CSS und JavaScript werden während eines Maven-Builds aus dem `ui.frontend` Modul als Client-Bibliothek in das `ui.apps` Modul kopiert*

## Teaser-Stil aktualisieren {#ui-frontend-module}

Nehmen Sie als Nächstes eine kleine Änderung am Teaser-Stil vor, um zu sehen, wie das `ui.frontend` Modul und die clientlibraries funktionieren. Verwenden Sie [die IDE Ihrer Wahl](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) , um das Venia-Projekt zu importieren. Die verwendeten Screenshots stammen aus der [Visual Studio Code-IDE](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code).

1. Navigieren Sie zum Modul **ui.frontend** und erweitern Sie die Ordnerhierarchie, um: `ui.frontend/src/main/styles/commerce`:

   ![ui.frontend commerce folder](../assets/style-cif-component/ui-frontend-commerce-folder.png)

   Beachten Sie, dass sich unter dem Ordner mehrere Sass-Dateien (`.scss`) befinden. Dies sind die Commerce-spezifischen Stile für jede der Commerce-Komponenten.

1. Öffnen Sie die Datei `_productteaser.scss`.

1. Aktualisieren Sie die `.item__image` Regel und ändern Sie die Rahmenregel:

   ```scss
   .item__image {
       border: #ea00ff 8px solid; /* <-- modify this rule */
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

   Mit der obigen Regel sollte der Komponente Product Teaser ein sehr fett rosa Rand hinzugefügt werden.

1. Öffnen Sie ein neues Terminalfenster und navigieren Sie zum `ui.frontend` Ordner:

   ```shell
   $ cd <project-location>/aem-cif-guides-venia/ui.frontend
   ```

1. Führen Sie den folgenden Maven-Befehl aus:

   ```shell
   $ mvn clean install
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  29.497 s
   [INFO] Finished at: 2020-08-25T14:30:44-07:00
   [INFO] ------------------------------------------------------------------------
   ```

   Inspect der Terminalausgabe. Sie werden sehen, dass der Maven Befehl mehrere NPM-Skripte ausgeführt hat, darunter auch `npm run build`. Der `npm run build` Befehl ist in der `package.json` Datei definiert und hat den Effekt, das Webpack-Projekt zu kompilieren und die Generierung der Client-Bibliothek auszulösen.

1. Inspect der Datei `ui.frontend/dist/clientlib-site/site.css`:

   ![Kompilierte Site-CSS](../assets/style-cif-component/comiled-site-css.png)

   Die Datei ist die kompilierte und minimierte Version aller Sass-Dateien im Projekt.

   >[!NOTE]
   >
   > Dateien wie diese werden von der Quellcodeverwaltung ignoriert, da sie während der Buildzeit generiert werden sollten.

1. Inspect die Datei `ui.frontend/clientlib.config.js`.

   ```js
   /* clientlib.config.js*/
   ...
   // Config for `aem-clientlib-generator`
   module.exports = {
       context: BUILD_DIR,
       clientLibRoot: CLIENTLIB_DIR,
       libs: [
           {
               ...libsBaseConfig,
               name: 'clientlib-site',
               categories: ['venia.site'],
               dependencies: ['venia.dependencies', 'aem-core-cif-react-components'],
               assets: {
   ...
   ```

   Dies ist die Konfigurationsdatei für [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator) und bestimmt, wo und wie das kompilierte CSS und JavaScript in eine AEM Client-Bibliothek umgewandelt werden.

1. Überprüfen Sie im `ui.apps` Modul die Datei: `ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-site/css/site.css`:

   ![Kompiliertes Site-CSS in ui.apps](../assets/style-cif-component/comiled-css-ui-apps.png)

   Dies ist die kopierte `site.css` Datei in das `ui.apps` Projekt. Es ist jetzt Teil einer clientlibrary mit dem Namen `clientlib-site` mit einer Kategorie von `venia.site`. Sobald die Datei Teil des `ui.apps` Moduls ist, kann sie AEM bereitgestellt werden.

   >[!NOTE]
   >
   > Dateien wie diese werden auch von der Quellcodeverwaltung ignoriert, da sie während der Buildzeit generiert werden sollten.

1. Überprüfen Sie anschließend die anderen vom Projekt generierten Clientbibliotheken:

   ![Andere Client-Bibliotheken](../assets/style-cif-component/other-clientlibs.png)

   Diese Client-Bibliotheken werden nicht vom `ui.frontend` Modul verwaltet. Stattdessen enthalten diese Clientbibliotheken CSS- und JavaScript-Abhängigkeiten, die von der Adobe bereitgestellt werden. Die Definition für diese clientlibraries befindet sich in der `.content.xml` Datei unter jedem Ordner.

   **clientlib-base** - Dies ist eine leere Client-Bibliothek, die einfach die erforderlichen Abhängigkeiten von [AEM Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html)einbettet. Die Kategorie ist `venia.base`.

   **clientlib-cif** - Dies ist auch eine leere Client-Bibliothek, die einfach die notwendigen Abhängigkeiten von [AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components)einbettet. Die Kategorie ist `venia.cif`.

   **clientlib-grid** - Dies umfasst das CSS, das zur Aktivierung AEM Funktion &quot;Responsive Grid&quot;erforderlich ist. Durch die Verwendung des AEM-Rasters wird der [Layoutmodus](https://docs.adobe.com/content/help/en/experience-manager-65/administering/operations/configuring-responsive-layout.html#include-the-responsive-css) im AEM-Editor aktiviert und Autoren von Inhalten erhalten die Möglichkeit, Komponenten neu zu formatieren. Die Kategorie ist `venia.grid` und ist in der `venia.base` Bibliothek eingebettet.

1. Inspect der Dateien `customheaderlibs.html` und `customfooterlibs.html` darunter `ui.apps/src/main/content/jcr_root/apps/venia/components/page`:

   ![Benutzerdefinierte Kopf- und Fußzeilenskripte](../assets/style-cif-component/custom-header-footer-script.png)

   Diese Skripten enthalten die Bibliotheken **venia.base** und **venia.cif** als Teil aller Seiten.

   >[!NOTE]
   >
   > Nur die Basisbibliotheken sind als Teil der Seitenskripte &quot;hartcodiert&quot;. `venia.site` nicht in diesen Dateien enthalten und stattdessen als Teil der Seitenvorlage einbezogen werden, um eine größere Flexibilität zu gewährleisten. Dies wird später überprüft.

1. Erstellen Sie das gesamte Projekt aus dem Terminal und stellen Sie es auf einer lokalen Instanz AEM:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

## Erstellen eines Produkt-Teasers {#author-product-teaser}

Nachdem die Codeaktualisierungen bereitgestellt wurden, fügen Sie der Startseite der Site mit den AEM Authoring-Werkzeugen eine neue Instanz der Komponente Product Teaser hinzu. Auf diese Weise können wir die aktualisierten Stile Ansicht haben.

1. Öffnen Sie eine neue Browserregisterkarte und navigieren Sie zur **Startseite** der Site: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Erweitern Sie die Asset-Suche (die Seitenleiste) im **Bearbeitungsmodus** . Wechseln Sie zum Asset-Filter zu **Produkte**.

   ![Erweitern der Asset-Suche und Filtern nach Produkten](../assets/style-cif-component/drag-drop-product-page.png)

1. Ziehen Sie ein neues Produkt auf die Startseite im Container &quot;Hauptlayout&quot;:

   ![Produkt-Teaser mit rosa Rand](../assets/style-cif-component/pink-border-product-teaser.png)

   Sie sollten sehen, dass der Product Teaser jetzt einen hellen rosa Rand hat, basierend auf der zuvor erstellten CSS-Regeländerung.

## Clientbibliotheken auf der Seite überprüfen {#verify-client-libraries}

Überprüfen Sie dann, ob die Clientbibliotheken auf der Seite enthalten sind.

1. Navigieren Sie zur **Startseite** der Site: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Wählen Sie das Menü **Seiteninformationen** aus und klicken Sie auf **Ansicht als veröffentlicht**:

   ![Als veröffentlicht anzeigen](../assets/style-cif-component/view-as-published.png)

   Dadurch wird die Seite geöffnet, ohne dass der AEM Autor Javascript geladen wurde, wie es auf der veröffentlichten Site angezeigt würde. Beachten Sie, dass an die URL der Parameter Abfrage `?wcmmode=disabled` angehängt ist. Bei der Entwicklung von CSS und JavaScript ist es eine gute Vorgehensweise, diesen Parameter zu verwenden, um die Seite zu vereinfachen, ohne dass AEM Autor etwas davon hat.

1. Ansicht der Seitenquelle und Sie sollten in der Lage sein, mehrere Client-Bibliotheken zu identifizieren sind enthalten:

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-site.min.css" type="text/css">
   </head>
   ...
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/core/wcm/components/commons/site/clientlibs/container.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-base.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/common.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-cif.min.js"></script>
   </body>
   </html>
   ```

   Client-Bibliotheken, die auf der Seite bereitgestellt werden, werden mit einem Präfix versehen `/etc.clientlibs` und über einen [Proxy](/help/implementing/developing/introduction/clientlibs.md) bereitgestellt, um zu vermeiden, dass vertrauliche Daten in `/apps` oder `/libs`angezeigt werden.

   Hinweis `venia/clientlibs/clientlib-site.min.css` und `venia/clientlibs/clientlib-site.min.js`. Dies sind die kompilierten CSS- und Javascript-Dateien, die vom `ui.frontend` Modul abgeleitet wurden.

## Einbindung der Client-Bibliothek in Seitenvorlagen {#client-library-inclusion-pagetemplates}

Es gibt mehrere Optionen zum Einschließen einer clientseitigen Bibliothek. Überprüfen Sie als Nächstes, wie das generierte Projekt die `clientlib-site` Bibliotheken über [Seitenvorlagen](https://docs.adobe.com/content/help/en/experience-manager-65/developing/platform/templates/page-templates-editable.html)enthält.

1. Navigieren Sie im AEM Editor zur **Startseite** der Site: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Wählen Sie das Menü **Seiteninformationen** aus und klicken Sie auf Vorlage **bearbeiten**:

   ![Bearbeiten der Vorlage](../assets/style-cif-component/edit-template.png)

   Dadurch wird die Vorlage für die **Landingpage** geöffnet, auf der die **Homepage** basiert.

   >[!NOTE]
   >
   > Um alle verfügbaren Vorlagen im Bildschirm &quot;AEM Beginn&quot;Ansicht, navigieren Sie zu **Werkzeuge** > **Allgemein** > **Vorlagen**.

1. Wählen Sie in der oberen linken Ecke das Symbol **Seiteninformationen** und klicken Sie auf **Seitenrichtlinie**.

   ![Menüelement Seitenrichtlinie](../assets/style-cif-component/page-policy-menu.png)

1. Dadurch wird die Seitenrichtlinie für die Vorlage &quot;Landingpage&quot;geöffnet:

   ![Seitenrichtlinie - Landingpage](../assets/style-cif-component/page-policy-properties.png)

   Auf der rechten Seite sehen Sie eine Liste der Client-Bibliotheken- **Kategorien** , die auf allen Seiten, die diese Vorlage verwenden, enthalten sind.

   * `venia.dependencies` - Bietet Bibliotheken von Anbietern, von denen `venia.site` sie abhängen.
   * `venia.site` - Dies ist die Kategorie für `clientlib-site` die das `ui.frontend` Modul generiert.

   Beachten Sie, dass andere Vorlagen die gleiche Richtlinie verwenden, **Inhaltsseite**, **Landingpage** usw... Durch die Wiederverwendung derselben Richtlinie können wir sicherstellen, dass dieselben Client-Bibliotheken auf allen Seiten enthalten sind.

   Der Vorteil der Verwendung von Vorlagen und Seitenrichtlinien zur Verwaltung der Einbeziehung von Clientbibliotheken besteht darin, dass Sie die Richtlinie pro Vorlage ändern können. Sie verwalten beispielsweise zwei verschiedene Marken innerhalb derselben AEM Instanz. Jede Marke hat ihren eigenen Stil oder *Design* , aber die Basisbibliotheken und der Code sind identisch. Ein weiteres Beispiel: Wenn Sie eine größere Client-Bibliothek hätten, die Sie nur auf bestimmten Seiten anzeigen möchten, könnten Sie eine eindeutige Seitenrichtlinie nur für diese Vorlage erstellen.

## Lokale Webpack-Entwicklung {#local-webpack-development}

In der vorherigen Übung wurde ein Update an einer Sass-Datei im `ui.frontend` Modul durchgeführt, und nach dem Erstellen eines Maven-Builds werden die Änderungen AEM bereitgestellt. Als Nächstes werden wir uns mit der Nutzung eines Webpack-dev-Servers befassen, um die Front-End-Stile schnell zu entwickeln.

Die webpack-dev-server proxies Bilder und einige der CSS/JavaScript aus der lokalen Instanz von AEM, erlaubt es dem Entwickler, die Stile und JavaScript im `ui.frontend` Modul zu ändern.

1. Navigieren Sie im Browser zur **Startseite** und zur **Ansicht wie veröffentlicht**: [http://localhost:4502/content/venia/us/en.html?wcmmode=disabled](http://localhost:4502/content/venia/us/en.html?wcmmode=disabled).

1. Ansicht der Seitenquelle und der **Kopie** des HTML-Rohdaten der Seite.

1. Kehren Sie zur IDE Ihrer Wahl unter dem `ui.frontend` Modul öffnen Sie die Datei: `ui.frontend/src/main/static/index.html`

   ![Statische HTML-Datei](../assets/style-cif-component/static-index-html.png)

1. Überschreiben Sie den Inhalt des im vorherigen Schritt kopierten HTML-Codes `index.html` und **fügen Sie ihn ein** .

1. Suchen Sie die Includes für `clientlib-site.min.css`und `clientlib-site.min.js` entfernen Sie **** sie.

   ```html
   <head>
       <!-- remove this link -->
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       ...
   </head>
   <body>
       ...
        <!-- remove this link -->
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
   </body>
   ```

   Diese werden entfernt, da sie die kompilierte Version des vom `ui.frontend` Modul generierten CSS und JavaScript darstellen. Lassen Sie die anderen Client-Bibliotheken so, wie sie von der laufenden AEM-Instanz proximiert werden.

1. Öffnen Sie ein neues Terminalfenster und navigieren Sie zum `ui.frontend` Ordner. Run the command `npm start`:

   ```shell
   $ cd ui.frontend
   $ npm start
   ```

   Dadurch wird der Webpack-dev-server unter [http://localhost:8080/ Beginn.](http://localhost:8080/)

   >[!CAUTION]
   >
   > Wenn Sie einen Fehler im Zusammenhang mit der Dimension erhalten, beenden Sie den Server und führen Sie den Befehl aus `npm rebuild node-sass` und wiederholen Sie die oben genannten Schritte. Dies kann vorkommen, wenn eine andere Version von `npm` und `node` dann im Projekt angegeben `aem-cif-guides-venia/pom.xml`.

1. Navigieren Sie auf einer neuen Registerkarte zum Ordner [http://localhost:8080/](http://localhost:8080/) mit demselben Browser wie eine angemeldete Instanz von AEM. Die Venia-Startseite sollte über den webpack-dev-server angezeigt werden:

   ![Webpack-Dev-Server auf Port 80](../assets/style-cif-component/webpack-dev-server-port80.png)

   Lassen Sie den Webpack-dev-server laufen. Es wird in der nächsten Übung verwendet werden.

## Implementieren des Kartenstils für den Produkt-Teaser {#update-css-product-teaser}

Ändern Sie anschließend die Assets im `ui.frontend` Modul, um einen kartenähnlichen Stil für den Product Teaser zu implementieren. Der Webpack-dev-server wird verwendet, um die Änderungen schnell zu sehen.

Kehren Sie zur IDE und zum erstellten Projekt zurück.

1. Im Modul **ui.frontend** öffnen Sie die Datei `_productteaser.scss` unter `ui.frontend/src/main/styles/commerce/_productteaser.scss`.

1. Nehmen Sie die folgenden Änderungen am Rand des Produkteditors vor:

   ```diff
       .item__image {
   -       border: #ea00ff 8px solid;
   +       border-bottom: 1px solid #c0c0c0;
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

   Speichern Sie die Änderungen und der Webpack-dev-server sollte automatisch mit den neuen Stilen aktualisiert werden.

1. hinzufügen Sie einen Schlagschatten und schließen Sie abgerundete Ecken in den Produktteaser ein.

   ```scss
    .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

1. Aktualisieren Sie den Produktnamen, damit er unten im Teaser angezeigt wird, und ändern Sie die Textfarbe.

   ```css
   .item__name {
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

1. Aktualisieren Sie den Produktpreis, damit er auch unten im Teaser angezeigt wird, und ändern Sie die Textfarbe.

   ```css
   .price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   
       ...
   ```

1. Aktualisieren Sie die Media-Abfrage am unteren Rand, um den Namen und den Preis in Bildschirmen mit einer Größe von weniger als **992 px** zu stapeln.

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

   Der Kartenstil sollte nun im webpack-dev-server angezeigt werden:

   ![Webpack Dev Server-Teaser-Änderungen](../assets/style-cif-component/webpack-dev-server-teaser-changes.png)

   Die Änderungen wurden jedoch noch nicht AEM bereitgestellt. Sie können die [Lösungsdatei hier](../assets/style-cif-component/_productteaser.scss)herunterladen.

1. Stellen Sie mithilfe Ihrer Maven-Fähigkeiten die Updates für AEM über ein Befehlszeilenterminal bereit:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

   >[!NOTE]
   >Es gibt zusätzliche [IDE-Einstellungen und -Tools](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) , die Projektdateien direkt mit einer lokalen AEM synchronisieren können, ohne einen vollständigen Maven-Build durchführen zu müssen.

## Ansicht - Aktualisierter Produkteditor {#view-updated-product-teaser}

Nachdem der Code für das Projekt in AEM bereitgestellt wurde, sollten wir nun die Änderungen am Product Teaser sehen können.

1. Kehren Sie zu Ihrem Browser zurück und aktualisieren Sie die Startseite: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html). Es sollten die aktualisierten Produkteaser-Stile angewendet werden.

   ![Aktualisierter Produkteaser-Stil](../assets/style-cif-component/product-teaser-new-style.png)

1. Experimentieren Sie, indem Sie zusätzliche Produktester hinzufügen. Mit dem Layoutmodus können Sie die Breite und den Versatz der Komponenten ändern, um mehrere Teaser in einer Zeile anzuzeigen.

   ![Mehrere Teaser](../assets/style-cif-component/multiple-teasers-final.png)

## Fehlerbehebung {#troubleshooting}

Sie können in [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) überprüfen, ob die aktualisierte CSS-Datei bereitgestellt wurde: [http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css](http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css)

Bei der Bereitstellung neuer CSS- und/oder JavaScript-Dateien ist es ebenfalls wichtig sicherzustellen, dass der Browser keine gestörten Dateien bereitstellt. Sie können dies vermeiden, indem Sie den Browser-Cache leeren oder eine neue Browsersitzung starten.

AEM versucht auch, Clientbibliotheken für die Leistung zwischenzuleiten. Gelegentlich werden nach einer Codebereitstellung die älteren Dateien verarbeitet. Mit dem Tool [Client-Bibliotheken neu erstellen können Sie den Cache AEM Client-Bibliothek manuell deaktivieren](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html). *Ungültige Caches sind die bevorzugte Methode, wenn Sie vermuten, dass AEM eine alte Version einer Client-Bibliothek zwischengespeichert hat. Die Wiederherstellung von Bibliotheken ist ineffizient und zeitaufwendig.*

## Herzlichen Glückwunsch {#congratulations}

Sie haben gerade Ihre erste AEM CIF Core-Komponente gestylt und einen Webpack dev Server verwendet!

## Bonus-Herausforderung {#bonus-challenge}

Verwenden Sie das [AEM-Stilsystem](https://docs.adobe.com/content/help/de-DE/experience-manager-65/developing/components/style-system.html) , um zwei Stile zu erstellen, die von einem Inhaltsersteller aktiviert/deaktiviert werden können. [Die Entwicklung mit dem Stilsystem](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html) umfasst detaillierte Schritte und Informationen dazu, wie dies zu erreichen ist.

![Bonus Challenge - Style System](../assets/style-cif-component/bonus-challenge.png)

## Zusätzliche Ressourcen {#additional-resources}

* [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
* [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components)
* [Einrichten einer Umgebung zur lokalen AEM](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html)
* [Client-seitige Bibliotheken](/help/implementing/developing/introduction/clientlibs.md)
* [Erste Schritte mit AEM Sites](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
* [Entwickeln mit dem Stilsystem](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html)
