---
title: Verwenden von Sling-Adaptern
description: Mit Sling wird ein Adaptermuster zum bequemen Übersetzen von Objekten bereitgestellt, die zum Implementieren der Adaptable-Schnittstelle verwendet werden
exl-id: 8ffe3bbd-01fe-44c2-bf60-7a4d25a6ba2b
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '2214'
ht-degree: 28%

---

# Verwenden von Sling-Adaptern {#using-sling-adapters}

Mit [Sling](https://sling.apache.org) wird ein [Adaptermuster](https://sling.apache.org/documentation/the-sling-engine/adapters.html) zum bequemen Übersetzen von Objekten bereitgestellt, die zum Implementieren der [Adaptable](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29)-Schnittstelle verwendet werden. Diese Schnittstelle bietet eine generische [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) -Methode, die das Objekt in den Klassentyp übersetzt, der als Argument übergeben wird.

Um beispielsweise ein Ressourcenobjekt in das entsprechende Knotenobjekt zu übersetzen, können Sie einfach Folgendes tun:

```java
Node node = resource.adaptTo(Node.class);
```

## Anwendungsfälle {#use-cases}

Es gibt die folgenden Nutzungsszenarien:

* Rufen Sie spezifische Objekte für die Implementierung ab.

  Eine JCR-basierte Implementierung der generischen [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html)-Schnittstelle ermöglicht beispielsweise Zugriff auf das zugrunde liegende JCR-[`Node`](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html)-Element.

* Erstellung von direkten Verknüpfungen für Objekte, für die interne Kontextobjekte übergeben werden müssen.

  Beispielsweise die JCR-basierte [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) enthält einen Verweis auf die [`JCR Session`](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html), was wiederum für viele Objekte benötigt wird, die auf dieser Anforderungssitzung basieren, z. B. die [`PageManager`](https://developer.adobe.com/de/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) oder [`UserManager`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/security/UserManager.html).

* Direkte Verknüpfung mit Services.

  Dies ist ein seltener Fall, da `sling.getService()` bereits eine einfache Möglichkeit darstellt.

### NULL-Rückgabewert {#null-return-value}

`adaptTo()` Kann null zurückgeben.

Es gibt verschiedene Gründe für die Null-Rückgabe, darunter die folgenden:

* die Implementierung unterstützt den Zieltyp nicht
* Eine Adapterfabrik, die diesen Fall verarbeitet, ist nicht aktiv (z. B. aufgrund fehlender Dienstverweise).
* Interne Bedingung fehlgeschlagen
* Service ist nicht verfügbar

Es ist wichtig, dass Sie die Groß-/Kleinschreibung &quot;null&quot;korrekt handhaben. Für JSP-Renderings kann es akzeptabel sein, dass die JSP fehlschlägt, wenn dies zu einem leeren Inhaltselement führt.

### Caching {#caching}

Zur Verbesserung der Leistung dürfen Implementierungen das Objekt zwischenspeichern, das über einen `obj.adaptTo()`-Aufruf zurückgegeben wird. Wenn das `obj` gleich ist, ist auch das zurückgegebene Objekt dasselbe.

Diese Zwischenspeicherung wird für alle auf `AdapterFactory` basierenden Fälle durchgeführt.

Es gibt jedoch keine allgemeine Regel - das Objekt kann entweder eine neue oder eine vorhandene Instanz sein. Daher können Sie sich auf keines der beiden Verhalten verlassen. Es ist also – vor allem innerhalb von `AdapterFactory` – wichtig, dass Objekte bei diesem Szenario wiederverwendet werden können.

### Funktionsweise {#how-it-works}

Es gibt verschiedene Möglichkeiten, `Adaptable.adaptTo()` zu implementieren:

* Über das Objekt selbst. Die eigentliche Methode wird implementiert. Anschließend erfolgt die Zuordnung zu bestimmten Objekten.
* Über ein [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), mit dem zufällige Objekte zugeordnet werden können.

  Die Objekte müssen trotzdem noch die `Adaptable`-Schnittstelle implementieren und [`SlingAdaptable`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (übergibt den `adaptTo`-Aufruf an einen zentralen Adapter-Manager) erweitern.

  Diese Methode ermöglicht Hooks für die `adaptTo` Mechanismus für bestehende Klassen, wie `Resource`.

* Eine Kombination beider Vorgehensweisen.

Im ersten Fall kann in den Java™-Dokumenten angegeben werden, `adaptTo-targets` möglich sind. Für bestimmte Unterklassen wie die JCR-basierte Ressource ist diese Anweisung jedoch oft nicht möglich. Im letzteren Fall `AdapterFactory` sind normalerweise Teil der privaten Klassen eines Bundles und werden daher nicht in einer Client-API verfügbar gemacht und auch nicht in Java™-Dokumenten aufgeführt. Theoretisch ist der Zugriff auf alle `AdapterFactory` Implementierungen von [OSGi](/help/implementing/deploying/configuring-osgi.md) -Dienstlaufzeit und sehen Sie sich die Konfigurationen der &quot;adaptierbaren Elemente&quot;(Quellen und Ziele) an, aber nicht, um sie einander zuzuordnen. Letztlich hängt es von der internen Logik ab, die dokumentiert werden muss. Daher ist dieser Verweis.

## Verweis {#reference}

### Sling {#sling}

Adaption von [**Resource**](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knoten</a></td>
   <td>Wenn es eine auf einem JCR-Knoten basierende Ressource oder eine JCR-Eigenschaft ist, referenzieren Sie einen Knoten</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Eigenschaft</a></td>
   <td>Wenn es eine auf einer JCR-Eigenschaft basierende Ressource ist</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Element</a></td>
   <td>Wenn es eine JCR-basierte Ressource ist (Knoten oder Eigenschaft)</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Map.html">Map</a></td>
   <td>Gibt eine Zuordnung der Eigenschaften zurück, wenn es sich um eine auf einem JCR-Knoten basierende Ressource handelt (oder eine andere Ressource, die Wertzuordnungen unterstützt)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Gibt eine benutzerfreundliche Zuordnung der Eigenschaften zurück, wenn es sich um eine auf einem JCR-Knoten basierende Ressource handelt (oder eine andere Ressource, die Wertzuordnungen unterstützt). Kann (einfacher) auch durch die Verwendung von<br /> <code><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ResourceUtil.html">ResourceUtil.getValueMap(Resource)</a></code> (behandelt NULL-Groß-/Kleinschreibung usw.)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Erweiterung der <a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> , wodurch die Hierarchie der Ressourcen bei der Suche nach Eigenschaften berücksichtigt werden kann</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModifiableValueMap</a></td>
   <td>Eine Erweiterung der <a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, mit der Sie Eigenschaften auf diesem Knoten ändern können</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Gibt den binären Inhalt einer Dateiressource zurück (wenn es sich um eine auf einem JCR-Knoten basierende Ressource handelt und der Knotentyp <code>nt:file</code> oder <code>nt:resource</code>; wenn es eine Bundle-Ressource ist; Dateiinhalt, wenn es eine Dateisystemressource ist). Oder gibt die Daten einer binären JCR-Eigenschaftsressource zurück.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Gibt eine URL für die Ressource zurück (Repository-URL dieses Knotens, wenn es eine auf einem JCR-Knoten basierende Ressource ist); jar bundle URL , wenn es eine Bundle-Ressource ist; Datei-URL, wenn es eine Dateisystemressource ist)</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/File.html">File</a></td>
   <td>Wenn es eine Dateisystemressource ist</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Wenn die Ressource ein Skript ist (z. B. eine JSP-Datei), für das ein Skriptmodul bei Sling registriert ist</td>
  </tr>
  <tr>
   <td><a href="https://www.oracle.com/java/technologies/servlet-technology.html">Servlet</a></td>
   <td>Wenn die Ressource ein Skript ist (z. B. eine JSP-Datei), für das ein Skriptmodul bei Sling registriert ist, oder wenn es eine Servlet-Ressource ist</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html">String</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html">Boolean</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html">Long</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Double.html">Double</a><br /><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html"> Calendar</a><br /><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html"> Value</a><br /><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html"> String[]</a><br /><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html"> Boolean[]</a><br /><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html"> Long[]</a><br /><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html"> Calendar[]</a><br /><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html"> Value[]</a></td>
   <td>Gibt die Werte aus, wenn es sich um eine auf einer JCR-Eigenschaft basierende Ressource handelt (und der Wert passt)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Wenn es eine auf einem JCR-Knoten basierende Ressource ist</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/de/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Page.html">Seite </a></td>
   <td>Wenn es eine auf einem JCR-Knoten basierende Ressource ist und der Knoten eine <code>cq:Page</code> (oder <code>cq:PseudoPage</code>)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/Component.html">Komponente</a></td>
   <td>Wenn es eine <code>cq:Component</code> Knotenressource</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/designer/Design.html">Design</a></td>
   <td>Wenn es sich um einen Designknoten handelt (<code>cq:Page</code>)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Template.html">Vorlage  </a></td>
   <td>Wenn es eine <code>cq:Template</code> Knotenressource</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Blueprint</a></td>
   <td>Wenn es eine <code>cq:Template</code> Knotenressource</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/Asset.html">Asset</a></td>
   <td>Wenn es eine dam:Asset-Knotenressource ist</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/Rendition.html">Rendition</a></td>
   <td>Wenn es eine dam:Asset-Ausgabedarstellung ist (nt:file unter dem Ordner "rendition"eines dam:Asset-Assets)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/Tag.html">Tag</a></td>
   <td>Wenn es eine <code>cq:Tag</code> Knotenressource</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Basierend auf der JCR-Sitzung, wenn es eine JCR-basierte Ressource ist und der Benutzer über Berechtigungen für den Zugriff auf UserManager verfügt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a></td>
   <td>Die Authorizable-Funktion ist die allgemeine Basisschnittstelle für Benutzer und Gruppe</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a></td>
   <td>User ist ein spezieller Fall von Authorizable, der authentifiziert und personifiziert werden kann</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Sucht unter der Ressource (oder verwenden Sie setSearchIn()), ob es sich um eine JCR-basierte Ressource handelt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Workflow-Status für den jeweiligen Seiten-/Workflow-Payload-Knoten</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Replikationsstatus für die jeweilige Ressource oder den zugehörigen Unterknoten „jcr:content“ (wird zuerst geprüft)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Gibt eine angepasste Connector-Ressource für bestimmte Typen zurück, wenn es sich um eine auf einem JCR-Knoten basierende Ressource handelt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>Wenn es eine <code>cq:ContentSyncConfig</code> Knotenressource</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>Wenn sie unter einer <code>cq:ContentSyncConfig</code> Knotenressource</td>
  </tr>
 </tbody>
</table>

Adaption von [**ResourceResolver**](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ResourceResolver.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Session</a></td>
   <td>JCR-Sitzung der Anfrage, wenn es sich um einen JCR-basierten Ressourcen-Resolver handelt (Standard)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/de/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Basierend auf der JCR-Sitzung, wenn es ein JCR-basierter Ressourcen-Resolver ist</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>Basierend auf der JCR-Sitzung, wenn es ein JCR-basierter Ressourcen-Resolver ist</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>Der UserManager bietet Zugriff auf autorisierbare Objekte, d. h. Benutzer und Gruppen, und ermöglicht deren Pflege. Der UserManager ist an eine bestimmte Sitzung gebunden
   </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a> </td>
   <td>Der aktuelle Benutzer</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/User.html">Benutzer</a><br /> </td>
   <td>Der aktuelle Benutzer</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html">Externalizer</a></td>
   <td>Für das Externalisieren von absoluten URLs, auch ohne Anforderungsobjekt<br /> </td>
  </tr>
 </tbody>
</table>

Adaptierung von [**SlingHttpServletRequest**](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) für:

Es sind noch keine Ziele vorhanden, aber „Adaptable“ wird implementiert und kann als Quelle in einer benutzerdefinierten „AdapterFactory“ verwendet werden.

Adaptierung von [**SlingHttpServletResponse**](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) für:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>Wenn es eine Sling-Rewriter-Antwort ist</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

Adaption von **[Page](https://developer.adobe.com/de/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Page.html)** für:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td>
   <td>Ressource der Seite.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Bezeichnete Ressource (== this).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td>
   <td>Knoten der Seite.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alle Elemente, für die die Ressource der Seite adaptiert werden kann.</td>
  </tr>
 </tbody>
</table>

Adaption von **[Component](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/Component.html)** für:

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource der Komponente. |
|---|---|
| [LabeledResource](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html) | Bezeichnete Ressource (== this). |
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten der Komponente. |
| ... | Alle Elemente, für die die Ressource der Komponente adaptiert werden kann. |

Adaption von **[Template](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Template.html)** für:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Ressource der Vorlage.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Bezeichnete Ressource (== this).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td>
   <td>Knoten dieser Vorlage.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alle Elemente, für die die Ressource der Vorlage adaptiert werden kann.</td>
  </tr>
 </tbody>
</table>

#### Sicherheit {#security}

**Authorizable**, **Benutzer** und **Gruppe** angepasst an:

| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Gibt den Stammknoten des Benutzers/der Gruppe zurück. |
|---|---|
| [ReplicationStatus](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/ReplicationStatus.html) | Gibt den Replizierungsstatus für den Stammknoten des Benutzers/der Gruppe zurück. |

#### DAM {#dam}

Adaption von **Asset** für:

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource des Assets. |
|---|---|
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten des Assets. |
| ... | Alle Elemente, für die die Ressource des Assets adaptiert werden kann. |

#### Tagging {#tagging}

Adaption von **Tag** für:

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource des Tags. |
|---|---|
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knoten des Tags. |
| ... | Alle Elemente, für die die Ressource des Tags adaptiert werden kann. |

#### Andere {#other}

Über Sling/JCR/OCM wird außerdem eine [`AdapterFactory`](https://sling.apache.org/documentation/the-sling-engine/adapters.html) für anwenderdefinierte OCM-Objekte ([Object Content Mapping](https://jackrabbit.apache.org/jcr/object-content-mapping.html)) bereitgestellt.
