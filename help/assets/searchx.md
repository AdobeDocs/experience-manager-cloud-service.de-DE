---
title: Erweitern der Suchoptionen und Funktionen in Adobe Experience Manager Assets
description: Erweitern Sie die Suchfunktionen von Assets.
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Erweitern der Asset-Suche {#extend-assets-search}

Sie können die Suchfunktionen von Adobe Experience Manager (AEM) Assets erweitern. Standardmäßig sucht AEM Assets anhand von Zeichenfolgen nach Assets.

Die Suchfunktion wird über die QueryBuilder-Schnittstelle durchgeführt und lässt sich mit mehreren Eigenschaften anpassen. Sie können den Standardsatz der Eigenschaften im folgenden Verzeichnis überlagern: `/apps/dam/content/search/searchpanel/facets`.

Sie können dem Admin-Bedienfeld von AEM Assets auch zusätzliche Registerkarten hinzufügen.

## Überlagerung {#overlay}

Um die vorkonfigurierten Eigenschaften zu überlagern, kopieren Sie den Knoten `facets` aus `/libs/dam/content/search/searchpanel` nach `/apps/dam/content/search/searchpanel/` oder geben Sie eine weitere `facetURL`-Eigenschaft in die Konfiguration des Suchfensters ein (standardmäßig `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

>[!NOTE]
>
>Standardmäßig ist die Verzeichnisstruktur unter `/apps` nicht vorhanden und muss erstellt werden. Stellen Sie sicher, dass die Knotentypen den Typen unter `/libs` entsprechen.

### Hinzufügen von Registerkarten {#add-tabs}

Sie können zusätzliche Suchregisterkarten hinzufügen, indem Sie sie im Admin-Bedienfeld von AEM Assets konfigurieren. So erstellen Sie weitere Registerkarten:

1. Erstellen Sie die Ordnerstruktur `/apps/wcm/core/content/damadmin/tabs,`, falls noch nicht vorhanden, kopieren Sie den Knoten `tabs` aus `/libs/wcm/core/content/damadmin` und fügen Sie ihn ein.
1. Erstellen und konfigurieren Sie die zweite Registerkarte wie gewünscht.

   >[!NOTE]
   >
   >Achten Sie bei Erstellung eines zweiten `siteadminsearchpanel` auf die Festlegung einer `id`-Eigenschaft, um Formularkonflikte zu vermeiden.

### Erstellen benutzerdefinierter Eigenschaften {#create-custom-predicates}

AEM Assets umfasst einen Satz vordefinierter Eigenschaften, mit denen eine Asset-Freigaben-Seite angepasst werden kann.
<!-- In addition to using pre-existing predicates, AEM developers can also create their own predicates using the [Query Builder API](/help/sites-developing/querybuilder-api.md). -->

Um benutzerdefinierte Eigenschaften erstellen zu können, benötigen Sie Grundlagenkenntnisse über das [Widget-Framework](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html).

Als Best Practice hat es sich erwiesen, eine vorhandene Eigenschaft zu kopieren und anzupassen. Beispiel-Eigenschaften befinden sich unter **/libs/cq/search/components/predicates**.

#### Beispiel: Einfaches Eigenschaftsprädikat erstellen   {#example-build-a-simple-property-predicate}

So erstellen Sie ein Eigenschaftsprädikat:

1. Erstellen Sie einen Komponentenordner in Ihrem Projektverzeichnis, z. B.**/ apps/geometrixx/components/titlepredicate**.
1. Fügen Sie **content.xml** hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Fügen Sie `titlepredicate.jsp` hinzu.

   ```xml
   <%--
   
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
       });
   </script>
   ```

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeitbar zu machen, fügen Sie in CRXDE einen Knoten **cq:editConfig** des primären Typs **cq:EditConfig** hinzu. Um Absätze entfernen zu können, fügen Sie eine **cq:actions**-Mehrwerteigenschaft mit **DELETE** als einzigem Wert hinzu.
1. Navigieren Sie zu Ihrem Browser und wechseln Sie auf Ihrer Beispielseite (z. B. **press.html**) in den Designmodus. Aktivieren Sie Ihre neue Komponente für das Eigenschaften-Absatzsystem (z. B. **links**).

1. Im Modus **Bearbeiten** ist die neue Komponente jetzt im Sidekick verfügbar (in der **Suchgruppe**). Fügen Sie die Komponente in die Spalte **Eigenschaften** ein, geben Sie einen Suchbegriff – z. B. **Raute** – ein und klicken Sie auf das Lupensymbol, um die Suche zu starten.

   >[!NOTE]
   >
   >Stellen Sie beim Suchen sicher, dass der Begriff korrekt eingegeben wird und auch die Groß-/Kleinschreibung stimmt.

#### Beispiel: Einfache Gruppeneigenschaft erstellen {#example-build-a-simple-group-predicate}

So erstellen Sie eine Gruppeneigenschaft:

1. Erstellen Sie einen Komponentenordner in Ihrem Projektverzeichnis, z. B. **/apps/geometrixx/components/picspredicate**.
1. Fügen Sie **content.xml** hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Fügen Sie **titlepredicate.jsp** hinzu:

   ```xml
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
       });
   ```

1. Sie müssen die Komponente bearbeiten, um sie verfügbar zu machen. Um eine Komponente bearbeitbar zu machen, fügen Sie in CRXDE einen Knoten **cq:editConfig** des primären Typs **cq:EditConfig** hinzu. Um Absätze entfernen zu können, fügen Sie eine **cq:actions**-Mehrwerteigenschaft mit **DELETE** als einzigem Wert hinzu.
1. Navigieren Sie zu Ihrem Browser und wechseln Sie auf Ihrer Beispielseite (z. B. **press.html**) in den Designmodus. Aktivieren Sie Ihre neue Komponente für das Eigenschaften-Absatzsystem (z. B. **links**).
1. Im Modus **Bearbeiten** ist die neue Komponente jetzt im Sidekick verfügbar (in der **Suchgruppe**). Fügen Sie die Komponente in die Spalte **Eigenschaften** ein.

### Installierte Eigenschaften-Widgets {#installed-predicate-widgets}

Die folgenden Eigenschaften sind als vorkonfigurierte ExtJS-Widgets verfügbar.

#### FulltextPredicate   {#fulltextpredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<br /> </strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Zeichenfolge</td>
   <td>Name der Eigenschaft. Standardwert ist „fulltext“</td>
  </tr>
  <tr>
   <td>searchCallback</td>
   <td>Funktion</td>
   <td>Callback zum Auslösen der Suche bei Ereignis „keyup“. Standardwert ist „CQ.wcm.SiteAdmin.doSearch“</td>
  </tr>
 </tbody>
</table>

#### PropertyPredicate {#propertypredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<br /> </strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Zeichenfolge</td>
   <td>Name der Eigenschaft. Standardwert ist „property“</td>
  </tr>
  <tr>
   <td>propertyName</td>
   <td>Zeichenfolge </td>
   <td>Name der JCR-Eigenschaft. Standardwert ist „jcr:title“</td>
  </tr>
  <tr>
   <td>defaultValue<br /> </td>
   <td>Zeichenfolge<br /> </td>
   <td>Vorgegebener Standardwert.<br /> </td>
  </tr>
 </tbody>
</table>

#### PathPredicate {#pathpredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<br /> </strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Zeichenfolge</td>
   <td>Name der Eigenschaft. Standardwert ist „path“</td>
  </tr>
  <tr>
   <td>rootPath</td>
   <td>Zeichenfolge </td>
   <td>Stammpfad der Eigenschaft. Standardwert ist „/content/dam“</td>
  </tr>
  <tr>
   <td>pathFieldPredicateName</td>
   <td>Zeichenfolge</td>
   <td>Standardwert ist „folder“</td>
  </tr>
  <tr>
   <td>showFlatOption</td>
   <td>Boolesch</td>
   <td>Markierung, um Kontrollkästchen „Suche in Unterordnern“ anzuzeigen. Standardwert ist „true“.</td>
  </tr>
 </tbody>
</table>

#### DatePredicate {#datepredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<br /> </strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Zeichenfolge</td>
   <td>Name der Eigenschaft. Standardwert ist „daterange“</td>
  </tr>
  <tr>
   <td>propertyname</td>
   <td>Zeichenfolge</td>
   <td>Name der JCR-Eigenschaft. Standardwert ist „jcr:content/jcr:lastModified“</td>
  </tr>
  <tr>
   <td>defaultValue </td>
   <td>Zeichenfolge </td>
   <td>Vorgegebener Standardwert </td>
  </tr>
 </tbody>
</table>

#### OptionsPredicate {#optionspredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<br /> </strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>title </td>
   <td>Zeichenfolge </td>
   <td>Fügt einen zusätzlichen oberen Titel hinzu </td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Zeichenfolge</td>
   <td>Name der Eigenschaft. Standardwert ist „daterange“</td>
  </tr>
  <tr>
   <td>propertyname</td>
   <td>Zeichenfolge</td>
   <td>Name der JCR-Eigenschaft. Standardwert ist „jcr:content/metadata/cq:tags“</td>
  </tr>
  <tr>
   <td>collapse</td>
   <td>Zeichenfolge</td>
   <td>Ebene der Reduzierung. Standardwert ist „level1“</td>
  </tr>
  <tr>
   <td>triggerSearch</td>
   <td>Boolesch </td>
   <td>Markierung zum Auslösen der Suche nach Aktivierung. Standardwert ist „false“</td>
  </tr>
  <tr>
   <td>searchCallback</td>
   <td>Funktion</td>
   <td>Callback zum Auslösen der Suche. Standardwert ist „CQ.wcm.SiteAdmin.doSearch“</td>
  </tr>
  <tr>
   <td>searchTimeoutTime</td>
   <td>Nummer</td>
   <td>Zeitlimit, nach dem searchCallback ausgelöst wird. Standardwert ist 800 ms.</td>
  </tr>
 </tbody>
</table>
