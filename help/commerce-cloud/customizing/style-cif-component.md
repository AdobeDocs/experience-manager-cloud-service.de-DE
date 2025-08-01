---
title: Stile für Adobe Experience Manager CIF-Kernkomponenten gestalten
description: Erfahren Sie, wie Sie Stile für Adobe Experience Manager (AEM) CIF-Kernkomponenten gestalten können. In diesem Tutorial wird beschrieben, wie sich Client-seitige Bibliotheken (auch clientlibs genannt) zum Bereitstellen und Verwalten von CSS- und JavaScript-Dateien für eine AEM Commerce-Implementierung verwenden lassen. Zudem wird in dem Tutorial erläutert, wie sich das ui.frontend-Modul und ein webpack-Projekt in den End-to-End-Build-Prozess integrieren lassen.
sub-product: Commerce
topics: Development
version: Experience Manager as a Cloud Service
doc-type: tutorial
activity: develop
audience: developer
feature: Commerce Integration Framework
kt: 3456
thumbnail: 3456-style-cif.jpg
exl-id: 521c1bb8-7326-4ee8-aba3-f386727e2b34
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: ht
source-wordcount: '2342'
ht-degree: 100%

---

# Stile für AEM CIF-Kernkomponenten festlegen {#style-aem-cif-core-components}

Das [CIF-Venia-Projekt](https://github.com/adobe/aem-cif-guides-venia) ist eine Referenz-Code-Basis für die Verwendung von [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components). In diesem Tutorial können Sie sich das Venia-Referenzprojekt ansehen und erfahren, wie von AEM CIF-Kernkomponenten verwendete CSS- und JavaScript-Dateien organisiert werden. Außerdem erstellen Sie mithilfe von CSS einen Stil, um den Standardstil der Komponente **Produkt-Teaser** zu aktualisieren.

>[!TIP]
>
> Verwenden Sie den [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype), wenn Sie Ihre eigene Commerce-Implementierung starten.

## Was Sie erstellen werden

In diesem Tutorial wird ein neuer Stil für die Produkt-Teaser-Komponente implementiert, der einer Karte ähnlich ist.  Das im Tutorial erworbene Wissen kann auf andere CIF-Kernkomponenten angewendet werden.

![Was Sie erstellen werden](../assets/style-cif-component/what-you-will-build.png)

## Voraussetzungen {#prerequisites}

Zum Absolvieren dieses Tutorials ist eine lokale Entwicklungsumgebung erforderlich. Diese Umgebung umfasst eine laufende Instanz von AEM, die konfiguriert und mit einer Adobe Commerce-Instanz verbunden ist. Überprüfen Sie die Anforderungen und Schritte zum [Einrichten einer lokalen Entwicklungsumgebung mit dem AEM as a Cloud Service SDK](../develop.md).

## Venia-Projekt klonen {#clone-venia-project}

Klonen Sie das [Venia-Projekt](https://github.com/adobe/aem-cif-guides-venia) und überschreiben Sie dann die Standardstile.

>[!NOTE]
>
> **Sie können auch ein vorhandenes Projekt** nutzen (basierend auf dem AEM-Projektarchetyp mit enthaltenem CIF) und diesen Abschnitt überspringen.

1. Führen Sie den folgenden Git-Befehl aus, damit Sie das Projekt klonen können:

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Erstellen Sie das Projekt und stellen Sie es in einer lokalen Instanz von AEM bereit:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Fügen Sie die erforderlichen OSGi-Konfigurationen hinzu, um so Ihre AEM-Instanz mit einer Adobe Commerce-Instanz zu verbinden, oder fügen Sie die Konfigurationen zum erstellten Projekt hinzu.

1. An diesem Punkt sollten Sie über eine funktionierende Version einer Storefront verfügen, die mit einer Adobe Commerce-Instanz verbunden ist. Navigieren Sie zur Seite `US` > `Home` unter: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

   Sie sollten sehen, dass die Storefront derzeit im Venia-Design erscheint. Wenn Sie das Hauptmenü der Storefront erweitern, sollten verschiedene Kategorien angezeigt werden, was darauf hinweist, dass die Verbindung mit Adobe Commerce funktioniert.

   ![Storefront mit konfiguriertem Venia-Design](../assets/style-cif-component/venia-store-configured.png)

## Client-Bibliotheken und ui.frontend-Modul {#introduction-to-client-libraries}

Die CSS- und JavaScript-Dateien, die für das Rendern der Designs/Stile der Storefront verantwortlich sind, werden in AEM von einer [Client-Bibliothek](/help/implementing/developing/introduction/clientlibs.md) (kurz „clientlibs“) verwaltet. Client-Bibliotheken bieten ein Verfahren zum Organisieren von CSS- und JavaScript-Dateien im Code eines Projekts und zum anschließenden Bereitstellen auf der Seite.

Markenspezifische Stile können auf AEM CIF-Kernkomponenten angewendet werden, indem das von diesen Client-Bibliotheken verwaltete CSS hinzugefügt und überschrieben wird. Kenntnisse dazu, wie Client-Bibliotheken strukturiert sind und auf der Seite eingeschlossen werden, sind von entscheidender Bedeutung.

Das [ui.frontend](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html?lang=de) ist ein dediziertes [webpack](https://webpack.js.org/)-Projekt für die Verwaltung aller Frontend-Assets eines Projekts. Mit diesem webppack können Frontend-Entwicklerinnen und -Entwickler eine beliebige Zahl von Sprachen und Technologien wie [TypeScript](https://www.typescriptlang.org/), [Sass](https://sass-lang.com/) und vieles mehr nutzen.

Das `ui.frontend`-Modul ist ebenfalls ein Maven-Modul und mit dem größeren Projekt durch Einsatz eines NPM-Moduls (dem [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator)) integriert. Während eines Builds kopiert der `aem-clientlib-generator` die kompilierten CSS- und JavaScript-Dateien im `ui.apps`-Modul in eine Client-Bibliothek.

![ui.frontend-zu-ui.apps-Architektur](../assets/style-cif-component/ui-frontend-architecture.png)

*Kompilierte CSS- und JavaScript-Dateien werden bei einem Maven-Build aus dem `ui.frontend`-Modul als Client-Bibliothek in das `ui.apps`-Modul kopiert*.

## Teaser-Stil aktualisieren {#ui-frontend-module}

Nehmen Sie als Nächstes eine kleine Änderung am Teaser-Stil vor, um zu sehen, wie das `ui.frontend`-Modul und die Client-Bibliotheken funktionieren. Verwenden Sie [eine IDE Ihrer Wahl](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#set-up-the-development-ide), um das Venia-Projekt zu importieren. Die verwendeten Screenshots stammen aus der [Visual Studio Code-IDE](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#microsoft-visual-studio-code).

1. Navigieren Sie zum Modul **ui.frontend** und erweitern Sie es. Erweitern Sie dann die Ordnerhierarchie zu: `ui.frontend/src/main/styles/commerce`:

   ![ui.frontend-Commerce-Ordner](../assets/style-cif-component/ui-frontend-commerce-folder.png)

   Beachten Sie, dass sich unter dem Ordner mehrere Sass-Dateien (`.scss`) befinden. Diese Dateien sind Commerce-spezifische Stile für die einzelnen Commerce-Komponenten.

1. Öffnen Sie die Datei `_productteaser.scss`.

1. Aktualisieren Sie die `.item__image`-Regel und ändern Sie die Rahmenregel:

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

   Mit der obigen Regel sollte der Produkt-Teaser-Komponente ein dicker rosa Rahmen hinzugefügt werden.

1. Öffnen Sie ein neues Terminal-Fenster und navigieren Sie zum Ordner `ui.frontend`:

   ```shell
   $ cd <project-location>/aem-cif-guides-venia/ui.frontend
   ```

1. Führen Sie folgenden Maven-Befehl aus:

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

   Prüfen Sie die Terminal-Ausgabe. Beachten Sie, dass der Maven-Befehl mehrere NPM-Skripte ausgeführt hat, darunter `npm run build`. Der `npm run build`-Befehl wird in der `package.json`-Datei definiert und kompiliert das webpack-Projekt und die Trigger der Client-Bibliothekserstellung.

1. Prüfen Sie die Datei `ui.frontend/dist/clientlib-site/site.css`:

   ![Kompilierte Site-CSS](../assets/style-cif-component/comiled-site-css.png)

   Die Datei ist die kompilierte und minimierte Version aller Sass-Dateien in dem Projekt.

   >[!NOTE]
   >
   > Dateien wie diese werden von der Quell-Code-Verwaltung ignoriert, da sie während der Build-Zeit erstellt werden sollten.

1. Prüfen Sie die Datei `ui.frontend/clientlib.config.js`.

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

   Dies ist die Konfigurationsdatei für [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator) und bestimmt, wo und wie die kompilierten CSS- und JavaScript-Dateien in eine AEM-Client-Bibliothek umgewandelt werden.

1. Überprüfen Sie im `ui.apps`-Modul die Datei: `ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-site/css/site.css`:

   ![Kompilierte Site-CSS in ui.apps](../assets/style-cif-component/comiled-css-ui-apps.png)

   Bei dieser Datei handelt es sich um `site.css`, die in das `ui.apps`-Projekt kopiert ist. Sie ist jetzt Teil einer Client-Bibliothek namens `clientlib-site` mit der Kategorie `venia.site`. Sobald die Datei Teil des `ui.apps`-Moduls ist, kann sie in AEM bereitgestellt werden.

   >[!NOTE]
   >
   > Dateien wie diese werden von der Quell-Code-Verwaltung ebenfalls ignoriert, da sie zur Build-Zeit erstellt werden sollten.

1. Überprüfen Sie anschließend die anderen vom Projekt erstellten Client-Bibliotheken:

   ![Andere Client-Bibliotheken](../assets/style-cif-component/other-clientlibs.png)

   Diese Client-Bibliotheken werden nicht vom `ui.frontend`-Modul verwaltet. Stattdessen enthalten sie CSS- und JavaScript-Abhängigkeiten, die von Adobe bereitgestellt werden. Die Definitionen für diese Client-Bibliotheken befinden sich in der `.content.xml`-Datei unter dem jeweiligen Ordner.

   **clientlib-base**: Eine leere Client-Bibliothek, die die erforderlichen Abhängigkeiten von [AEM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) einfach einbettet. Die Kategorie lautet `venia.base`.

   **clientlib-cif**: Eine leere Client-Bibliothek, die die erforderlichen Abhängigkeiten von [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) einfach einbettet. Die Kategorie lautet `venia.cif`.

   **clientlib-grid**: Umfasst die CSS, die zur Aktivierung der Funktion „Responsives Raster“ von AEM erforderlich ist. Durch Verwendung des AEM-Rasters wird der [Layout-Modus](/help/sites-cloud/authoring/page-editor/responsive-layout.md) im AEM-Editor aktiviert und Inhaltsautorinnen und -autoren erhalten die Möglichkeit, die Größe von Komponenten zu ändern. Die Kategorie lautet `venia.grid` und ist in der `venia.base`-Bibliothek eingebettet.

1. Überprüfen Sie die Dateien `customheaderlibs.html` und `customfooterlibs.html` unter `ui.apps/src/main/content/jcr_root/apps/venia/components/page`:

   ![Benutzerdefinierte Kopf- und Fußzeilenskripte](../assets/style-cif-component/custom-header-footer-script.png)

   Diese Skripte enthalten die Bibliotheken **venia.base** und **venia.cif** als Bestandteil aller Seiten.

   >[!NOTE]
   >
   > Nur die Basisbibliotheken sind als Teil der Seitenskripte „hartkodiert“. `venia.site` ist nicht in diesen Dateien enthalten, sondern für mehr Flexibilität Bestandteil der Seitenvorlage. Dieser Prozess wird später überprüft.

1. Erstellen Sie das gesamte Projekt aus dem Terminal und stellen Sie es in einer lokalen Instanz von AEM bereit:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

## Produkt-Teaser erstellen {#author-product-teaser}

Nachdem die Code-Aktualisierungen bereitgestellt wurden, fügen Sie mit den AEM-Authoring-Tools der Startseite der Site eine Instanz der Produkt-Teaser-Komponente hinzu. Auf diese Weise können wir die aktualisierten Stile anzeigen.

1. Öffnen Sie eine neue Registerkarte im Browser und navigieren Sie zur **Startseite** der Site: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Erweitern Sie die Asset-Suche (die Seitenleiste) im Modus **Bearbeitung**. Wechseln Sie im Asset-Filter zu **Produkte**.

   ![Asset-Suche erweitern und nach Produkten filtern](../assets/style-cif-component/drag-drop-product-page.png)

1. Ziehen Sie ein neues Produkt auf die Startseite im Haupt-Layout-Container:

   ![Produkt-Teaser mit rosa Rahmen](../assets/style-cif-component/pink-border-product-teaser.png)

   Sie sollten sehen, dass der Produkt-Teaser nun einen rosa Rahmen hat, der auf der zuvor erstellten CSS-Regeländerung basiert.

## Client-Bibliotheken auf der Seite überprüfen {#verify-client-libraries}

Überprüfen Sie dann, ob die Client-Bibliotheken auf der Seite enthalten sind.

1. Navigieren Sie zur **Startseite** der Site: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Wählen Sie das Menü **Seiteninformationen** und klicken Sie auf **Als veröffentlicht anzeigen**:

   ![Als veröffentlicht anzeigen](../assets/style-cif-component/view-as-published.png)

   Die Seite wird geöffnet, ohne dass das AEM-Author-JavaScript geladen wird (so, wie die Seite auf der veröffentlichten Site angezeigt würde). Beachten Sie, dass an die URL der Abfrageparameter `?wcmmode=disabled` angehängt ist. Bei der Entwicklung von CSS und JavaScript ist es eine gute Idee, diesen Parameter zur Vereinfachung der Seite zu verwenden (ohne Elemente von AEM Author).

1. Wenn Sie die Seitenquelle anzeigen, sollten Sie in der Lage sein, mehrere enthaltene Client-Bibliotheken zu identifizieren:

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

   Client-Bibliotheken, die auf der Seite bereitgestellt werden, sind mit dem Präfix `/etc.clientlibs` versehen und werden über einen [Proxy](/help/implementing/developing/introduction/clientlibs.md) bereitgestellt, um zu verhindern, dass in `/apps` oder `/libs` vertrauliche Daten angezeigt werden.

   Achten Sie auf `venia/clientlibs/clientlib-site.min.css` und `venia/clientlibs/clientlib-site.min.js`. Diese Dateien sind die kompilierten CSS- und JavaScript-Dateien, die vom `ui.frontend`-Modul abgeleitet wurden.

## Einschließen von Client-Bibliotheken mit Seitenvorlagen {#client-library-inclusion-pagetemplates}

Es gibt mehrere Optionen zum Einschließen einer Client-seitigen Bibliothek. Sehe Sie sich zunächst an, wie das generierte Projekt die `clientlib-site`-Bibliotheken über [Seitenvorlagen](/help/implementing/developing/components/templates.md) enthält.

1. Navigieren Sie im AEM-Editor zur **Startseite** der Site: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Wählen Sie das Menü **Seiteninformationen** und klicken Sie auf **Vorlage bearbeiten**:

   ![Vorlage bearbeiten](../assets/style-cif-component/edit-template.png)

   Die **Landingpage**-Vorlage, auf der die **Startseite** basiert, wird geöffnet.

   >[!NOTE]
   >
   > Um alle verfügbaren Vorlagen aus dem AEM-Startbildschirm anzuzeigen, navigieren Sie zu **Tools** > **Allgemein** > **Vorlagen**.

1. Wählen Sie in der oberen linken Ecke das Symbol **Seiteninformationen** und klicken Sie auf **Seitenrichtlinie**.

   ![Menüelement „Seitenrichtlinie“](../assets/style-cif-component/page-policy-menu.png)

1. Die Seitenrichtlinie für die Landingpage-Vorlage wird geöffnet:

   ![Seitenrichtlinie – Landingpage](../assets/style-cif-component/page-policy-properties.png)

   Auf der rechten Seite sehen Sie eine Liste mit **Kategorien** von Client-Bibliotheken, die auf allen Seiten, die diese Vorlage nutzen, enthalten sind.

   * `venia.dependencies`: Stellt beliebige Anbieterbibliotheken bereit, auf die `venia.site` angewiesen ist.
   * `venia.site`: Die Kategorie für `clientlib-site`, die das `ui.frontend`-Modul generiert.

   Beachten Sie, dass andere Vorlagen die gleiche Richtlinie verwenden: **Inhaltsseite**, **Landingpage** usw. Durch die Wiederverwendung derselben Richtlinie wird sichergestellt, dass auf allen Seiten dieselben Client-Bibliotheken enthalten sind.

   Der Vorteil einer Nutzung von Vorlagen und Seitenrichtlinien zur Verwaltung des Einschließens von Client-Bibliotheken besteht darin, dass Sie die Richtlinie je nach Vorlage ändern können. Möglicherweise verwalten Sie zwei verschiedene Marken innerhalb derselben AEM-Instanz. Jede Marke weist ihren eigenen Stil oder ihr eigenes *Design* auf, doch die Basisbibliotheken und der Code sind identisch. Ein weiteres Beispiel: Wenn Sie über eine größere Client-Bibliothek verfügen, die Sie nur auf bestimmten Seiten anzeigen möchten, können Sie eine Einzelseitenrichtlinie nur für diese Vorlage erstellen.

## Lokale Webpack-Entwicklung {#local-webpack-development}

In der vorherigen Übung wurde an einer Sass-Datei im `ui.frontend`-Modul eine Aktualisierung vorgenommen. Nach dem Erstellen eines Maven-Builds werden die Änderungen dann in AEM bereitgestellt. Als Nächstes sehen Sie sich die Verwendung eines webpack-dev-Servers an, um die Frontend-Stile schnell zu entwickeln.

Der webpack-Dev-Server dient als Proxy für Bilder und einige der CSS/JavaScript-Dateien aus der lokalen Instanz von AEM, erlaubt es dem Entwickler jedoch, die Stile und JavaScript im `ui.frontend`-Modul zu ändern.

1. Navigieren Sie im Browser zur **Startseite** und dann zu **Als veröffentlicht anzeigen**: [http://localhost:4502/content/venia/us/en.html?wcmmode=disabled](http://localhost:4502/content/venia/us/en.html?wcmmode=disabled).

1. Zeigen Sie den Quell-Code der Seite an und **kopieren** Sie den rohen HTML-Code der Seite.

1. Kehren Sie zur IDE Ihrer Wahl zurück und öffnen Sie unter dem `ui.frontend`-Modul die folgende Datei: `ui.frontend/src/main/static/index.html`.

   ![Statische HTML-Datei](../assets/style-cif-component/static-index-html.png)

1. Überschreiben Sie den Inhalt von `index.html` und **fügen** Sie den im vorherigen Schritt kopierten HTML-Code ein.

1. Suchen Sie nach den Einbeziehungen für `clientlib-site.min.css` sowie `clientlib-site.min.js` und **entfernen** Sie diese.

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

   Diese Einbeziehungen werden entfernt, da sie die kompilierte Version der vom `ui.frontend`-Modul generierten CSS- und JavaScript-Dateien darstellen. Bearbeiten Sie die anderen Client-Bibliotheken nicht, da sie von der laufenden AEM-Instanz als Proxy übermittelt werden.

1. Öffnen Sie ein neues Terminal-Fenster und navigieren Sie zum Ordner `ui.frontend`. Führen Sie den Befehl `npm start` aus:

   ```shell
   $ cd ui.frontend
   $ npm start
   ```

   Mit diesem Befehl wird der webpack-Dev-Server auf [http://localhost:8080/](http://localhost:8080/) gestartet

   >[!CAUTION]
   >
   > Wenn Sie einen Sass-bezogenen Fehler erhalten, stoppen Sie den Server und führen Sie den Befehl `npm rebuild node-sass` aus; wiederholen Sie dann die oben genannten Schritte. Dieser Fehler kann auftreten, wenn Sie eine andere Version von `npm` und `node` haben, als im Projekt `aem-cif-guides-venia/pom.xml` angegeben.

1. Navigieren Sie mit demselben Browser als angemeldeter AEM-Instanz in einer neuen Registerkarte zu [http://localhost:8080/](http://localhost:8080/). Über den webpack-Dev-Server sollte die Venia-Startseite angezeigt werden:

   ![webpack-Dev-Server an Port 80](../assets/style-cif-component/webpack-dev-server-port80.png)

   Lassen Sie den webpack-Dev-Server laufen. Er wird in der nächsten Übung erneut verwendet.

## Kartenstil für den Produkt-Teaser implementieren {#update-css-product-teaser}

Ändern Sie anschließend die Sass-Dateien im `ui.frontend`-Modul, um für den Produkt-Teaser einen kartenähnlichen Stil zu implementieren. Der webpack-dev-Server dient dazu, die Änderungen schnell anzuzeigen.

Kehren Sie zur IDE und zum erstellten Projekt zurück.

1. Öffnen Sie im Modul **ui.frontend** erneut die Datei `_productteaser.scss` unter `ui.frontend/src/main/styles/commerce/_productteaser.scss`.

1. Nehmen Sie folgende Änderungen am Rahmen des Produkt-Teasers vor:

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

   Speichern Sie die Änderungen. Der webpack-Dev-Server sollte mit den neuen Stilen automatisch aktualisiert werden.

1. Fügen Sie dem Produkt-Teaser einen Schlagschatten sowie abgerundete Ecken hinzu.

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

1. Aktualisieren Sie den Produktnamen so, dass er unten im Teaser angezeigt wird, und ändern Sie die Textfarbe.

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

1. Aktualisieren Sie den Produktpreis so, dass er ebenfalls unten im Teaser angezeigt wird, und ändern Sie die Textfarbe.

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

1. Aktualisieren Sie die Medienabfrage unten, damit Sie den Namen und den Preis in Bildschirmen, die kleiner als **992 Pixel** sind, stapeln können.

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

   Der Kartenstil sollte sich nun im webpack-Dev-Server widerspiegeln:

   ![Änderungen am webpack-Dev-Server-Teaser](../assets/style-cif-component/webpack-dev-server-teaser-changes.png)

   Die Änderungen wurden jedoch noch nicht in AEM bereitgestellt. Sie können die Lösungsdatei [hier](../assets/style-cif-component/_productteaser.scss) herunterladen.

1. Stellen Sie Aktualisierungen mithilfe Ihrer Maven-Kenntnisse über ein Befehlszeilen-Terminal in AEM bereit:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

   >[!NOTE]
   >Es gibt zusätzliche [IDE-Einstellungen und -Tools](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html?lang=de#set-up-an-integrated-development-environment), die Projektdateien direkt mit einer lokalen AEM-Instanz synchronisieren können, ohne dass ein vollständiger Maven-Build erforderlich ist.

## Aktualisierten Produkt-Teaser anzeigen {#view-updated-product-teaser}

Nachdem der Code für das Projekt in AEM bereitgestellt wurde, sollten Sie die Änderungen am Produkt-Teaser nun sehen können.

1. Kehren Sie zu Ihrem Browser zurück und aktualisieren Sie die Startseite: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html). Sie sollten erkennen, dass die aktualisierten Produkt-Teaser-Stile angewendet worden sind.

   ![Aktualisierter Produkt-Teaser-Stil](../assets/style-cif-component/product-teaser-new-style.png)

1. Experimentieren Sie, indem Sie zusätzliche Produkt-Teaser hinzufügen. Mit dem Layout-Modus können Sie die Breite und den Versatz der Komponenten ändern, um mehrere Teaser in einer Zeile anzuzeigen.

   ![Mehrere Produkt-Teaser](../assets/style-cif-component/multiple-teasers-final.png)

## Fehlerbehebung {#troubleshooting}

Sie können in [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) prüfen, ob die aktualisierte CSS-Datei bereitgestellt wurde: [http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css](http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css)

Bei der Bereitstellung neuer CSS-, JavaScript-Dateien, oder beiden, muss sichergestellt werden, dass der Browser keine veralteten Dateien bereitstellt. Sie können dieses potenzielle Problem vermeiden, indem Sie den Browsercache leeren oder eine neue Browser-Sitzung starten.

Außerdem versucht AEM, Client-Bibliotheken für höhere Leistung zwischenzuspeichern. Gelegentlich werden nach einer Code-Implementierung die älteren Dateien bereitgestellt. Mit dem [Tool zur Neuerstellung von Client-Bibliotheken](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html) können Sie den Cache der Client-Bibliothek von AEM manuell invalidieren. *Die Invalidierung des Cache ist die bevorzugte Methode, wenn Sie vermuten, dass AEM eine alte Version einer Client-Bibliothek zwischengespeichert hat. Die Neuerstellung von Bibliotheken ist ineffizient und zeitaufwendig.*

## Herzlichen Glückwunsch {#congratulations}

Sie haben den Stil Ihrer ersten AEM CIF-Kernkomponente festgelegt und dafür einen webpack-Entwicklungs-Server verwendet.

## Bonusaufgabe {#bonus-challenge}

Verwenden Sie das [AEM-Stilsystem](/help/sites-cloud/authoring/page-editor/style-system.md), um zwei Stile einzurichten, die von einer Inhaltsautorin bzw. einem Inhaltsautor aktiviert bzw. deaktiviert werden können. [Entwickeln mit dem Stilsystem](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/style-system.html?lang=de) umfasst detaillierte Schritte und Informationen dazu, wie Sie dabei vorgehen.

![Bonusaufgabe – Stilsystem](../assets/style-cif-component/bonus-challenge.png)

## Zusätzliche Ressourcen {#additional-resources}

* [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
* [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components)
* [Lokale AEM-Entwicklungsumgebung einrichten](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=de)
* [Client-seitige Bibliotheken](/help/implementing/developing/introduction/clientlibs.md)
* [Erste Schritte mit AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de)
* [Entwickeln mit dem Stilsystem](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/style-system.html?lang=de)
