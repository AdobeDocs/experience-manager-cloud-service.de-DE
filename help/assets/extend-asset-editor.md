---
title: Erweitern des Asset-Editors
description: Erfahren Sie, wie Sie die Funktionen des Assets-Editors mit benutzerdefinierten Komponenten erweitern.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Erweitern des Asset-Editors {#extending-asset-editor}

Beim Asset-Editor handelt es sich um die Seite, die geöffnet wird, wenn auf ein über die Asset-Freigabe gefundenes Asset geklickt wird. Er ermöglicht dem Benutzer das Bearbeiten von Aspekten des Assets wie Metadaten, Miniatur, Titel und Tags.

Configuration of the editor using the predefined editing components is covered in [Creating and Configuring an Asset Editor Page](https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-finder-editor.html).

Zusätzlich zur Verwendung von vorhandenen Bearbeiterkomponenten können Adobe Experience Manager (AEM)-Entwickler ihre eigenen Komponenten erstellen.

## Erstellen einer Asset-Editor-Vorlage {#creating-an-asset-editor-template}

Die folgenden Beispielseiten sind in Geometrixx enthalten:

* Geometrixx-Beispielseite: `/content/geometrixx/en/press/asseteditor.html`
* Beispielvorlage: `/apps/geometrixx/templates/asseteditor`
* Beispielseitenkomponente: `/apps/geometrixx/components/asseteditor`

### Konfigurieren der clientlib {#configuring-clientlib}

AEM Assets-Komponenten verwenden eine Erweiterung der WCM-clientlib zur Bearbeitung. Die clientlibs werden normalerweise in `init.jsp` geladen.

Anders als beim Laden der Standard-clientlib (in `init.jsp` des Kerns) muss eine AEM Assets-Vorlage Folgendes enthalten:

* The template must include the `cq.dam.edit` clientlib (instead of `cq.wcm.edit`).

* Die clientlib muss auch im deaktivierten WCM-Modus (z. B. beim **Veröffentlichen** geladen) verfügbar sein, um die Eigenschaften, Aktionen und Linsen darzustellen.

In most cases, copying the existing sample `init.jsp` (`/apps/geometrixx/components/asseteditor/init.jsp`) should meet these needs.

### Konfigurieren von JS-Aktionen {#configuring-js-actions}

Some of the AEM Assets components require JS functions defined in `component.js`. Kopieren Sie diese Datei in Ihr Komponentenverzeichnis und verknüpfen Sie sie.

```xml
<script type="text/javascript" src="<%= component.getPath() %>/component.js"></script>
```

The sample loads this javascript source in `head.jsp`(`/apps/geometrixx/components/asseteditor/head.jsp`).

### Zusätzliche Stylesheets {#additional-style-sheets}

Einige der AEM Assets-Komponenten verwenden die AEM Widgets-Bibliothek. Damit sie im Inhaltskontext ordnungsgemäß gerendert werden, muss ein zusätzliches Stylesheet geladen werden. Die Tag-Aktionskomponente erfordert ein weiteres zusätzliches Stylesheet.

```xml
<link href="/etc/designs/geometrixx/ui.widgets.css" rel="stylesheet" type="text/css">
```

### Geometrixx-Stylesheet {#geometrixx-style-sheet}

The sample page components require that all selectors start with `.asseteditor` of `static.css` (`/etc/designs/geometrixx/static.css`). Best practice: Copy all `.asseteditor` selectors to your style sheet and adjust the rules as desired.

### FormChooser: Anpassungen für Ressourcen, die irgendwann geladen werden {#formchooser-adjustments-for-eventually-loaded-resources}

Der Asset-Editor verwendet die Formularauswahl, mit der Sie Ressourcen – in diesem Fall Assets – auf derselben Formularseite bearbeiten können, indem Sie der URL des Assets einfach einen Formularselektor und den Pfad des Formulars hinzufügen.

Beispiel:

* Einfache Formularseite: [http://localhost:4502/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/geometrixx/en/press/asseteditor.html)
* In der Formularseite geladenes Asset: [http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html)

The sample handles in `head.jsp` (`/apps/geometrixx/components/asseteditor/head.jsp`) do the following:

* Sie erkennen, wenn ein Asset geladen wird oder wenn das einfache Formular angezeigt werden muss.
* Wenn ein Asset geladen wird, deaktivieren sie den WCM-Modus, da ParSys nur auf einer einfachen Formularseite bearbeitet werden kann.
* Wenn ein Asset geladen wird, verwenden Sie dessen Titel anstelle des Titels auf der Formularseite.

```java
 List<Resource> resources = FormsHelper.getFormEditResources(slingRequest);
    if (resources != null) {
        if (resources.size() == 1) {
            // single resource
            FormsHelper.setFormLoadResource(slingRequest, resources.get(0));
        } else if (resources.size() > 1) {
            // multiple resources
            // not supported by CQ 5.3
        }
    }
    Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
    String title;
    if (loadResource != null) {
        // an asset is loaded: disable WCM
        WCMMode.DISABLED.toRequest(request);

        String path = loadResource.getPath();
        Asset asset = loadResource.adaptTo(Asset.class);
        try {
            // it might happen that the adobe xmp lib creates an array
            Object titleObj = asset.getMetadata("dc:title");
            if (titleObj instanceof Object[]) {
                Object[] titleArray = (Object[]) titleObj;
                title = (titleArray.length > 0) ? titleArray[0].toString() : "";
            } else {
                title = titleObj.toString();
            }
        }
        catch (NullPointerException e) {
            title = path.substring(path.lastIndexOf("/") + 1);
        }
    }
    else {
        title = currentPage.getTitle() == null ? currentPage.getName() : currentPage.getTitle();
    }
```

Verwenden Sie im HTML-Teil den vorhergehenden festgelegten Titel (entweder Asset- oder Seitentitel):

```xml
<title><%= title %></title>
```

## Erstellen einer Feldkomponente für ein einfaches Formular {#creating-a-simple-form-field-component}

In diesem Beispiel wird das Erstellen einer Komponente beschrieben, die die Metadaten eines geladenen Assets anzeigt.

1. Create a component folder in your projects directory, for example, `/apps/geometrixx/components/samplemeta`.
1. Fügen Sie `content.xml` das folgende Codefragment hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Dimension"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Asset Editor"/>
   ```

1. Fügen Sie `samplemeta.jsp` das folgende Codefragment hinzu:

   ```xml
   <%--
   
     Sample metadata field comopnent
   
   --%><%@ page import="com.day.cq.dam.api.Asset,
                    java.security.AccessControlException" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       String value = "";
       String name = "dam:sampleMetadata";
       boolean readOnly = false;
   
       // If the form page is requested for an asset loadResource will be the asset.
       Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
   
       if (loadResource != null) {
   
           // Determine if the loaded asset is read only.
           Session session = slingRequest.getResourceResolver().adaptTo(Session.class);
           try {
               session.checkPermission(loadResource.getPath(), "set_property");
               readOnly = false;
           }
           catch (AccessControlException ace) {
               // checkPermission throws exception if asset is read only
               readOnly = true;
           }
           catch (RepositoryException re) {}
   
           // Get the value of the metadata.
           Asset asset = loadResource.adaptTo(Asset.class);
           try {
               value = asset.getMetadata(name).toString();
           }
           catch (NullPointerException npe) {
               // no metadata dc:description available
           }
       }
   %>
   <div class="form_row">
       <div class="form_leftcol">
           <div class="form_leftcollabel">Sample Metadata</div>
       </div>
       <div class="form_rightcol">
           <%
           if (readOnly) {
               %><c:out value="<%= value %>"/><%
           }
           else {
               %><input class="text" type="text" name="./jcr:content/metadata/<%= name %>" value="<c:out value="<%= value %>" />"><%
           }%>
       </div>
   </div>
   ```

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. To make a component editable, in CRXDE Lite, add a node `cq:editConfig` of primary type `cq:EditConfig`. Um Absätze entfernen zu können, fügen Sie eine `cq:actions`-Mehrwerteigenschaft mit `DELETE` als einzigem Wert hinzu.

1. Navigieren Sie zu Ihrem Browser, wechseln Sie auf Ihrer Beispielseite (z. B.`asseteditor.html`) in den Designmodus und aktivieren Sie Ihre neue Komponente für das Absatzsystem.

1. Im **Bearbeitungsmodus** ist die neue Komponente (z. B. **Beispielmetadaten**) jetzt im Sidekick (in der Gruppe **Asset-Editor**) verfügbar. Fügen Sie die Komponente ein. Um die Metadaten speichern zu können, muss sie dem Metadatenformular hinzugefügt werden.

## Ändern von Metadatenoptionen {#modifying-metadata-options}

Sie können die im [Metadatenformular](https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-finder-editor.html) verfügbaren Namespaces ändern.

Currently available metadata are defined in `/libs/dam/options/metadata`:

* Die erste Ebene innerhalb dieses Verzeichnisses enthält die Namespaces.
* Die Elemente in den einzelnen Namespaces stellen Metadaten dar, beispielsweise Ergebnisse in einem lokalen Teilelement.
* Die Metadaten enthalten die Informationen für den Typ und die Optionen mit mehreren Werten.

The options can be overwritten in `/apps/dam/options/metadata`:

1. Copy the directory from `/libs` to `/apps`.

1. Sie können Elemente entfernen, ändern und hinzufügen.

>[!NOTE]
>
>Wenn Sie neue Namespaces hinzufügen, müssen diese in Ihrem Repository/CRX registriert sein. Andernfalls tritt beim Übermitteln des Metadatenformulars ein Fehler auf.
