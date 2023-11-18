---
title: Erweitern des Multi-Site-Managers
description: Erfahren Sie, wie Sie die Funktionalität des Multi-Site-Managers erweitern.
exl-id: 4b7a23c3-65d1-4784-9dea-32fcceca37d1
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '2425'
ht-degree: 67%

---

# Erweitern des Multi-Site-Managers {#extending-the-multi-site-manager}

In diesem Dokument erfahren Sie, wie Sie die Funktionalität des Multi-Site-Managers erweitern, und werden die folgenden Themen behandelt.

* Erfahren Sie mehr über die wichtigsten MSM-Java-APIs
* Erstellen Sie eine neue Synchronisierungsaktion, die in einer Rollout-Konfiguration verwendet werden kann
* Ändern Sie die Standardsprache und die Länder-Codes

>[!TIP]
>
>Diese Seite ist im Kontext des Dokuments leichter verständlich [Wiederverwenden von Inhalten: Multi Site Manager.](/help/sites-cloud/administering/msm/overview.md)

>[!CAUTION]
>
>Der Multi-Site-Manager und seine API werden beim Erstellen einer Website verwendet und sind daher nur für die Verwendung in einer Autorenumgebung vorgesehen.

## Überblick über die Java-API {#overview-of-the-java-api}

Multi Site Manager umfasst die folgenden Pakete:

* [com.day.cq.wcm.msm.api](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/package-frame.html)
* [com.day.cq.wcm.msm.commons](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/commons/package-frame.html)

Die wichtigsten MSM-API-Objekte interagieren wie folgt (siehe auch den Abschnitt ) [Verwendete Begriffe](/help/sites-cloud/administering/msm/overview.md#terms-used)):

![Haupt-MSM-API-Objekte](assets/msm-api-interaction.png)

* **`Blueprint`** - Ein `Blueprint` (wie in [Blueprint-Konfiguration](/help/sites-cloud/administering/msm/overview.md#source-blueprints-and-blueprint-configurations)) legt die Seiten fest, von denen eine Live Copy Inhalte erben kann.

  ![Blueprint](assets/msm-blueprint-interaction.png)

   * Die Verwendung einer Blueprint-Konfiguration (`Blueprint`) ist optional, aber sie:

      * Dadurch kann der Autor die **Rollout** -Option in der Quelle verwenden, um explizit Änderungen an Live Copies zu pushen, die von dieser Quelle erben.
      * Dadurch kann der Autor **Site erstellen**, wodurch der Benutzer einfach Sprachen auswählen und die Struktur der Live Copy konfigurieren kann.
      * Sie definiert die standardmäßige Rollout-Konfiguration für alle resultierenden Live Copies.

* **`LiveRelationship`** - Die `LiveRelationship` legt die Verbindung (Beziehung) zwischen einer Ressource im Live Copy-Zweig und der entsprechenden Quelle/Blueprint-Ressource fest.

   * Die Beziehungen werden bei der Umsetzung der Vererbung und des Rollouts genutzt.
   * `LiveRelationship`-Objekte bieten Zugriff (Verweise) auf die Rollout-Konfigurationen (`RolloutConfig`), `LiveCopy` und `LiveStatus`-Objekte, die mit der Beziehung zusammenhängen.

   * Beispiel: Eine Live Copy wird unter `/content/copy/us` von der Quelle / dem Blueprint unter `/content/wknd/language-masters` erstellt. Die Ressourcen `/content/wknd/language-masters/en/jcr:content` und `/content/copy/us/en/jcr:content` bilden eine Beziehung.

* **`LiveCopy`** - A `LiveCopy` enthält Konfigurationsdetails für die Beziehungen (`LiveRelationship`) zwischen den Live Copy-Ressourcen und ihren Quell-/Blueprint-Ressourcen.

   * Über die Klasse `LiveCopy` können Sie auf den Pfad der Seite, den Pfad der Quell-/Blueprint-Seite und die Rollout-Konfigurationen zugreifen und festlegen, ob die untergeordneten Seiten ebenfalls in der `LiveCopy` enthalten sind.

   * Ein `LiveCopy`-Knoten wird immer erstellt, wenn **Website erstellen** oder **Live Copy erstellen** genutzt wird.

* **`LiveStatus`** - `LiveStatus` -Objekte bieten Zugriff auf den Laufzeitstatus eines `LiveRelationship`. Sie können damit den Synchronisierungsstatus einer Live Copy abfragen.

* **`LiveAction`** - Eine `LiveAction` ist eine Aktion, die auf jeder Ressource, die am Rollout beteiligt ist, ausgeführt wird.

   * `LiveAction`s werden nur von `RolloutConfig`s.

* **`LiveActionFactory`** - A `LiveActionFactory` erstellt `LiveAction` Objekte, die `LiveAction` Konfiguration. Konfigurationen werden als Ressourcen im Repository gespeichert.

* **`RolloutConfig`** - Die `RolloutConfig` enthält eine Liste der `LiveActions`, die nach der Auslösung zum Einsatz kommen sollen. Die `LiveCopy` erbt die `RolloutConfig` und das Ergebnis befindet sich in der `LiveRelationship`.

   * Beim erstmaligen Einrichten einer Live Copy wird auch eine `RolloutConfig` (Trigger der `LiveAction`s).

## Erstellen einer neuen Synchronisierungsaktion {#creating-a-new-synchronization-action}

Sie können benutzerdefinierte Synchronisierungsaktionen erstellen, die mit Ihren Rollout-Konfigurationen verwendet werden. Dies kann nützlich sein, wenn die Variable [installierte Aktionen](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) Ihre spezifischen Anwendungsanforderungen nicht erfüllen.

Erstellen Sie dazu zwei Klassen:

* eine Implementierung der Schnittstelle [`com.day.cq.wcm.msm.api.LiveAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveAction.html), die die Aktion ausführt
* Eine OSGi-Komponente, die die [`com.day.cq.wcm.msm.api.LiveActionFactory`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) -Benutzeroberfläche und erstellt Instanzen Ihrer `LiveAction` class

`LiveActionFactory` erstellt Instanzen der Klasse `LiveAction` für eine bestimmte Konfiguration:

* `LiveAction`-Klassen umfassen die folgenden Methoden:

   * `getName` - Gibt den Namen der Aktion zurück

      * Der Name wird verwendet, um auf die Aktion zu verweisen, z. B. in Rollout-Konfigurationen.

   * `execute` - Führt die Aufgabe der Aktion aus

* `LiveActionFactory`-Klassen umfassen die folgenden Mitglieder:

   * `LIVE_ACTION_NAME` - Ein Feld, das den Namen des zugeordneten `LiveAction`

      * Dieser Name muss mit dem Wert übereinstimmen, der von der Methode `getName` der Klasse `LiveAction` zurückgegeben wird.

   * `createAction` - Erstellt eine Instanz der `LiveAction`

      * Der optionale Parameter `Resource` kann verwendet werden, um Konfigurationsdaten bereitzustellen.

   * `createsAction` - Gibt den Namen der verknüpften `LiveAction`

### Zugreifen auf den LiveAction-Konfigurationsknoten {#accessing-the-liveaction-configuration-node}

Mit dem `LiveAction`-Konfigurationsknoten im Repository können Sie Informationen speichern, die das Laufzeitverhalten der `LiveAction`-Instanz beeinflussen. Der Knoten im Repository, in dem die `LiveAction`-Konfiguration gespeichert ist, steht dem `LiveActionFactory`-Objekt zur Laufzeit zur Verfügung. Somit können Sie Eigenschaften zum Konfigurationsknoten hinzufügen und sie bei Bedarf in Ihrer `LiveActionFactory`-Implementierung nutzen.

Beispiel: eine `LiveAction` muss den Namen des Blueprint-Autors speichern. Eine Eigenschaft des Konfigurationsknotens umfasst den Eigenschaftsnamen der Blueprint-Seite, in der die Informationen gespeichert werden. Zur Laufzeit ruft die `LiveAction` den Eigenschaftsnamen von der Konfiguration ab und erhält dann den Eigenschaftswert.

Der Parameter der Methode [`LiveActionFactory.createAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) ist ein `Resource`-Objekt. Diese `Resource` -Objekt stellt die `cq:LiveSyncAction` Knoten für diese Live-Aktion in der Rollout-Konfiguration.

Siehe [Erstellen einer Rollout-Konfiguration](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration) für weitere Informationen.

Wie bei Konfigurationsknoten gewohnt, sollten Sie ihn an ein `ValueMap`-Objekt anpassen:

```java
public LiveAction createAction(Resource resource) throws WCMException {
        ValueMap config;
        if (resource == null || resource.adaptTo(ValueMap.class) == null) {
            config = new ValueMapDecorator(Collections.<String, Object>emptyMap());
        } else {
            config = resource.adaptTo(ValueMap.class);
        }
        return new MyLiveAction(config, this);
}
```

### Zugreifen auf Zielknoten, Quellknoten und die LiveRelationship {#accessing-target-nodes-source-nodes-and-the-liverelationship}

Die folgenden Objekte sind als Parameter der `execute`-Methode vom `LiveAction`-Objekt verfügbar:

* A [`Resource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) -Objekt, das die Quelle der Live Copy darstellt
* A `Resource` -Objekt, das die Zielgruppe der Live Copy darstellt.
* Die [`LiveRelationship`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/LiveRelationship.html) -Objekt für die Live Copy
   * Der Wert `autoSave` gibt an, ob die `LiveAction` am Repository vorgenommene Änderungen speichern soll
   * Die `reset` gibt den Rollout-Reset-Modus an.

Aus diesen Objekten können Sie Informationen zu den `LiveCopy`. Mit den `Resource`-Objekten können Sie auch die `ResourceResolver`-, `Session`- und `Node`-Objekte abrufen. Diese Objekte sind bei der Bearbeitung der Repository-Inhalte hilfreich:

In der ersten Zeile des folgenden Codes ist das `Resource`-Objekt der Quellseite die Quelle:

```java
ResourceResolver resolver = source.getResourceResolver();
Session session = resolver.adaptTo(javax.jcr.Session.class);
Node sourcenode = source.adaptTo(javax.jcr.Node.class);
```

>[!NOTE]
>
>Die `Resource`-Argumente können `null`- oder `Resources`-Objekte sein, die sich nicht an `Node`-Objekte anpassen, z. B. [`NonExistingResource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/NonExistingResource.html)-Objekte.

## Erstellen einer neuen Rollout-Konfiguration {#creating-a-new-rollout-configuration}

Sie können eine Rollout-Konfiguration erstellen, wenn die installierten Rollout-Konfigurationen Ihre Anwendungsanforderungen nicht erfüllen. Führen Sie dazu die folgenden zwei Schritte aus:

* [Erstellen Sie die Rollout-Konfiguration](#create-the-rollout-configuration)
* [Fügen Sie Synchronisierungsaktionen zur Rollout-Konfiguration hinzu](#add-synchronization-actions-to-the-rollout-configuration)

Die neue Rollout-Konfiguration steht dann zur Verfügung, wenn Sie die Rollout-Konfigurationen auf einer Blueprint oder einer Live Copy-Seite festlegen.

>[!TIP]
>
>Informationen hierzu finden Sie auch unter [Best Practices zum Anpassen von Rollouts](/help/sites-cloud/administering/msm/best-practices.md#customizing-rollouts).

### Erstellen der Rollout-Konfiguration {#create-the-rollout-configuration}

So erstellen Sie eine Rollout-Konfiguration:

1. Öffnen Sie CRXDE Lite unter `https://<host>:<port>/crx/de`.

1. Navigieren Sie zu `/apps/msm/<your-project>/rolloutconfigs`, die benutzerdefinierte Version von Ihrem Projekt `/libs/msm/wcm/rolloutconfigs`.

   * Wenn dies Ihre erste Konfiguration ist, muss die Verzweigung `/libs` als Vorlage verwendet werden, die neue Verzweigung unter `/apps` zu erstellen.

1. Erstellen Sie unter diesem Speicherort einen Knoten mit den folgenden Eigenschaften:

   * **Name**: Der Knotenname der Rollout-Konfiguration, beispielsweise `contentCopy` oder `workflow`
   * **Typ**: `cq:RolloutConfig`

1. Fügen Sie diesem Knoten die folgenden Eigenschaften hinzu:

   * **Name**: `jcr:title`
     **Typ**: `String`
     **Wert**: Ein Identifizierungstitel, der in der Benutzeroberfläche angezeigt wird

   * **Name**: `jcr:description`
     **Typ**: `String`
     **Wert**: Eine optionale Beschreibung.

   * **Name**: `cq:trigger`
     **Typ**: `String`
     **Wert**: Der zu verwendende [Rollout-Trigger](/help/sites-cloud/administering/msm/live-copy-sync-config.md#rollout-triggers)
      * `rollout`
      * `modification`
      * `publish`
      * `deactivate`

1. Klicken Sie auf **Alle speichern**.

### Hinzufügen von Synchronisierungsaktionen zur Rollout-Konfiguration {#add-synchronization-actions-to-the-rollout-configuration}

Rollout-Konfigurationen werden unter dem [Rollout-Konfigurationsknoten](#create-the-rollout-configuration) , die Sie unter der `/apps/msm/<your-project>/rolloutconfigs` Knoten.

Fügen Sie untergeordnete Knoten des Typs `cq:LiveSyncAction` hinzu, um Synchronisierungsaktionen zur Rollout-Konfiguration hinzuzufügen. Die Reihenfolge der Synchronisierungsaktionsknoten bestimmt die Reihenfolge, in der die Aktionen durchgeführt werden.

1. Wählen Sie unter CRXDE Lite Ihre [Rollout-Konfiguration](#create-the-rollout-configuration) Knoten, z. B. `/apps/msm/myproject/rolloutconfigs/myrolloutconfig`.

1. Erstellen Sie einen Knoten mit den folgenden Knoteneigenschaften:

   * **Name**: Der Knotenname der Synchronisierungsaktion
      * Der Name muss mit dem **Aktionsname** in der Tabelle unter [Synchronisierungsaktionen](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) wie `contentCopy` oder `workflow`.
   * **Typ**: `cq:LiveSyncAction`

1. Fügen Sie so viele Synchronisierungsaktionsknoten hinzu wie erforderlich und konfigurieren Sie sie.

1. Ordnen Sie die Aktionsknoten so an, dass sie die Reihenfolge aufweisen, in der sie ausgeführt werden sollen.
   * Der oberste Aktionsknoten wird zuerst ausgeführt.

## Erstellen und Verwenden einer einfachen LiveActionFactory-Klasse {#creating-and-using-a-simple-liveactionfactory-class}

Mit den Verfahren, die in diesem Abschnitt erläutert werden, können Sie eine `LiveActionFactory` entwickeln und in einer Rollout-Konfiguration verwenden. Für die Entwicklung und Bereitstellung der `LiveActionFactory` werden Maven und Eclipse verwendet:

1. [Erstellen Sie das Maven-Projekt](#create-the-maven-project) und importieren Sie es in Eclipse.
1. [Fügen Sie Abhängigkeiten](#add-dependencies-to-the-pom-file) zur POM-Datei hinzu.
1. [Implementieren des `LiveActionFactory` Benutzeroberfläche](#implement-liveactionfactory) und stellen Sie das OSGi-Bundle bereit.
1. [Erstellen Sie die Rollout-Konfiguration](#create-the-example-rollout-configuration).
1. [Erstellen Sie die Live Copy](#create-the-live-copy).

[Das Maven-Projekt und der Quell-Code der Java-Klasse sind im öffentlichen Git-Repository verfügbar.](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout)

### Erstellen des Maven-Projekts {#create-the-maven-project}

Für das folgende Verfahren müssen Sie die `adobe-public` Profil zu Ihrer Maven-Einstellungsdatei hinzufügen.

* Weitere Informationen zum Profil „adobe-public“ finden Sie unter [Abrufen des Inhaltspaket-Maven-Plug-ins](/help/implementing/developing/tools/maven-plugin.md#obtaining-the-content-package-maven-plugin)
* Weitere Informationen zur Maven-Einstellungsdatei finden Sie in der [Referenz zu den Einstellungen](https://maven.apache.org/settings.html) für Maven.

1. Öffnen Sie eine Terminal- oder Befehlszeilensitzung und ändern Sie das Verzeichnis in den Ort, an dem Sie das Projekt erstellen möchten.
1. Geben Sie den folgenden Befehl ein:

   ```text
   mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault -DarchetypeArtifactId=multimodule-content-package-archetype -DarchetypeVersion=1.0.0 -DarchetypeRepository=adobe-public-releases
   ```

1. Geben Sie in der interaktiven Eingabeaufforderung die folgenden Werte an:

   * **`groupId`**: `com.adobe.example.msm`
   * **`artifactId`**: `MyLiveActionFactory`
   * **`version`**: `1.0-SNAPSHOT`
   * **`package`**: `MyPackage`
   * **`appsFolderName`**: `myapp`
   * **`artifactName`**: `MyLiveActionFactory package`
   * **`packageGroup`**: `myPackages`

1. Starten Sie Eclipse und [importieren Sie das Maven-Projekt.](/help/implementing/developing/tools/eclipse.md#import-the-maven-project-into-eclipse)

### Hinzufügen von Abhängigkeiten zur POM-Datei {#add-dependencies-to-the-pom-file}

Fügen Sie Abhängigkeiten hinzu, damit der Eclipse-Compiler auf die Klassen verweisen kann, die im `LiveActionFactory`-Code verwendet werden.

1. Wählen Sie im Eclipse-Projekt-Explorer folgende Datei aus `MyLiveActionFactory/pom.xml`.

1. Klicken Sie im Editor auf die Registerkarte `pom.xml` und suchen Sie den Abschnitt `project/dependencyManagement/dependencies`.

1. Fügen Sie den folgenden XML-Code zum Element `dependencyManagement` hinzu und speichern Sie dann die Datei.

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
     <version>5.6.2</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
     <version>2.4.3-R1488084</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
     <version>5.6.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
     <version>2.0.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
     <version>2.0.0</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
   ```

1. Öffnen Sie im **Projekt-Explorer** unter `MyLiveActionFactory-bundle/pom.xml` die POM-Datei für das Bundle.

1. Klicken Sie im Editor auf die Registerkarte `pom.xml` und suchen Sie den Abschnitt project/dependencies. Fügen Sie den folgenden XML-Code zum Element „dependencies“ hinzu und speichern Sie dann die Datei:

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
   ```

### Implementieren von LiveActionFactory {#implement-liveactionfactory}

Die folgende `LiveActionFactory`-Klasse implementiert eine `LiveAction`, die Nachrichten zu Quell- und Zielseiten protokolliert und die Eigenschaft `cq:lastModifiedBy` vom Quell- zum Zielknoten kopiert. Der Name der Live-Aktion lautet `exampleLiveAction`.

1. Klicken Sie Projekt-Explorer von Eclipse mit der rechten Maustaste auf das Paket `MyLiveActionFactory-bundle/src/main/java/com.adobe.example.msm` und klicken Sie auf **Neu** > **Klasse**.

1. Geben Sie als **Name** den Wert `ExampleLiveActionFactory` ein und klicken Sie dann auf **Fertig**.

1. Öffnen Sie die Datei `ExampleLiveActionFactory.java`, ersetzen Sie den Inhalt durch den folgenden Code und speichern Sie die Datei.

   ```java
   package com.adobe.example.msm;
   
   import java.util.Collections;
   
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.apache.sling.api.resource.Resource;
   import org.apache.sling.api.resource.ResourceResolver;
   import org.apache.sling.api.resource.ValueMap;
   import org.apache.sling.api.wrappers.ValueMapDecorator;
   import org.apache.sling.commons.json.io.JSONWriter;
   import org.apache.sling.commons.json.JSONException;
   
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   
   import com.day.cq.wcm.msm.api.ActionConfig;
   import com.day.cq.wcm.msm.api.LiveAction;
   import com.day.cq.wcm.msm.api.LiveActionFactory;
   import com.day.cq.wcm.msm.api.LiveRelationship;
   import com.day.cq.wcm.api.WCMException;
   
   @Component(metatype = false)
   @Service
   public class ExampleLiveActionFactory implements LiveActionFactory<LiveAction> {
    @Property(value="exampleLiveAction")
    static final String actionname = LiveActionFactory.LIVE_ACTION_NAME;
   
    public LiveAction createAction(Resource config) {
     ValueMap configs;
     /* Adapt the config resource to a ValueMap */
           if (config == null || config.adaptTo(ValueMap.class) == null) {
               configs = new ValueMapDecorator(Collections.<String, Object>emptyMap());
           } else {
               configs = config.adaptTo(ValueMap.class);
           }
   
     return new ExampleLiveAction(actionname, configs);
    }
    public String createsAction() {
     return actionname;
    }
    /************* LiveAction ****************/
    private static class ExampleLiveAction implements LiveAction {
     private String name;
     private ValueMap configs;
     private static final Logger log = LoggerFactory.getLogger(ExampleLiveAction.class);
   
     public ExampleLiveAction(String nm, ValueMap config){
      name = nm;
      configs = config;
     }
   
     public void execute(Resource source, Resource target,
       LiveRelationship liverel, boolean autoSave, boolean isResetRollout)
         throws WCMException {
   
      String lastMod = null;
   
      log.info(" *** Executing ExampleLiveAction *** ");
   
      /* Determine if the LiveAction is configured to copy the cq:lastModifiedBy property */
      if ((Boolean) configs.get("repLastModBy")){
   
       /* get the source's cq:lastModifiedBy property */
       if (source != null && source.adaptTo(Node.class) !=  null){
        ValueMap sourcevm = source.adaptTo(ValueMap.class);
        lastMod = sourcevm.get(com.day.cq.wcm.msm.api.MSMNameConstants.PN_PAGE_LAST_MOD_BY, String.class);
       }
   
       /* set the target node's la-lastModifiedBy property */
       Session session = null;
       if (target != null && target.adaptTo(Node.class) !=  null){
        ResourceResolver resolver = target.getResourceResolver();
        session = resolver.adaptTo(javax.jcr.Session.class);
        Node targetNode;
        try{
         targetNode=target.adaptTo(javax.jcr.Node.class);
         targetNode.setProperty("la-lastModifiedBy", lastMod);
         log.info(" *** Target node lastModifiedBy property updated: {} ***",lastMod);
        }catch(Exception e){
         log.error(e.getMessage());
        }
       }
       if(autoSave){
        try {
         session.save();
        } catch (Exception e) {
         try {
          session.refresh(true);
         } catch (RepositoryException e1) {
          e1.printStackTrace();
         }
         e.printStackTrace();
        }
       }
      }
     }
     public String getName() {
      return name;
     }
   
     /************* Deprecated *************/
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
       ActionConfig arg2, boolean arg3) throws WCMException {
     }
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
       ActionConfig arg2, boolean arg3, boolean arg4)
         throws WCMException {
     }
     @Deprecated
     public String getParameterName() {
      return null;
     }
     @Deprecated
     public String[] getPropertiesNames() {
      return null;
     }
     @Deprecated
     public int getRank() {
      return 0;
     }
     @Deprecated
     public String getTitle() {
      return null;
     }
     @Deprecated
     public void write(JSONWriter arg0) throws JSONException {
     }
    }
   }
   ```

1. Ändern Sie über eine Terminal- oder Befehlszeilensitzung das Verzeichnis in das Verzeichnis `MyLiveActionFactory` (das Maven-Projektverzeichnis). Geben Sie dann den folgenden Befehl ein:

   ```shell
   mvn -PautoInstallPackage clean install
   ```

1. Die AEM `error.log` sollte anzeigen, dass das Bundle gestartet wurde, sichtbar in den Protokollen unter `https://<host>:<port>/system/console/status-slinglogs`.

   ```text
   13.08.2013 14:34:55.450 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent RESOLVED
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTING
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTED
   13.08.2013 14:34:55.453 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle Service [com.adobe.example.msm.ExampleLiveActionFactory,2188] ServiceEvent REGISTERED
   13.08.2013 14:34:55.454 *INFO* [OsgiInstallerImpl] org.apache.sling.audit.osgi.installer Started bundle com.adobe.example.msm.MyLiveActionFactory-bundle [316]
   ```

### Erstellen der Rollout-Beispielkonfiguration {#create-the-example-rollout-configuration}

Erstellen Sie die MSM-Rollout-Konfiguration, die die von Ihnen erstellte `LiveActionFactory` nutzt:

1. Erstellen und konfigurieren Sie eine [Rollout-Konfiguration mit dem Standardverfahren](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration) unter Verwendung der Eigenschaften:

   * **Titel**: Beispiel-Rollout-Konfiguration
   * **Name**: examplerolloutconfig
   * **cq:trigger**: `publish`

### Hinzufügen der Live-Aktion zur Rollout-Beispielkonfiguration {#add-the-live-action-to-the-example-rollout-configuration}

Konfigurieren Sie die beim vorhergehenden Verfahren erstellte Rollout-Konfiguration so, dass sie die Klasse `ExampleLiveActionFactory` verwendet.

1. Öffnen Sie CRXDE Lite.

1. Erstellen Sie den entsprechenden Knoten unter `/apps/msm/rolloutconfigs/examplerolloutconfig/jcr:content`:

   * **Name**: `exampleLiveAction`
   * **Typ**: `cq:LiveSyncAction`

1. Klicken Sie auf **Alle speichern**.

1. Wählen Sie die `exampleLiveAction` -Knoten und fügen Sie eine Eigenschaft hinzu, die der `ExampleLiveAction` -Klasse die `cq:LastModifiedBy` -Eigenschaft sollte von der Quelle zum Zielknoten repliziert werden.

   * **Name**: `repLastModBy`
   * **Typ**: `Boolean`
   * **Wert**: `true`

1. Klicken Sie auf **Alle speichern**.

### Erstellen der Live Copy {#create-the-live-copy}

[Erstellen einer Live Copy](/help/sites-cloud/administering/msm/creating-live-copies.md#creating-a-live-copy-of-a-page) der englischen/Products-Verzweigung der WKND-Referenz-Website unter Verwendung Ihrer Rollout-Konfiguration:

* **Quelle**: `/content/wknd/language-masters/en/products`

* **Rollout-Konfiguration**: Rollout-Beispielkonfiguration

Aktivieren Sie die (englische) Seite **Products** des Quellzweigs und beobachten Sie die Protokollnachrichten, die von der Klasse `LiveAction` erzeugt werden:

```xml
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***ExampleLiveAction has been executed.***
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***Target node lastModifiedBy property updated: admin ***
```

## Ändern von Sprachnamen und Standardländern {#changing-language-names-and-default-countries}

AEM verwendet einen Standardsatz von Sprach- und Länder-Codes.

* Der standardmäßige Sprach-Code ist der aus zwei Buchstaben bestehende Code in Kleinbuchstaben gemäß ISO-639-1.
* Der standardmäßige Länder-Code ist der aus zwei Klein- oder Großbuchstaben bestehende Code gemäß ISO 3166.

MSM bestimmt anhand einer gespeicherten Liste von Sprach- und Ländercodes den Namen des Landes, das mit dem Namen der Sprachversion Ihrer Seite verknüpft ist. Die folgenden Elemente der Liste können Sie bei Bedarf ändern:

* Sprachtitel
* Ländernamen
* Standardländer für Sprachen (für Codes wie `en`, `de`, u. a.)

Die Sprachliste ist unter dem Knoten `/libs/wcm/core/resources/languages` gespeichert. Jeder untergeordnete Knoten steht für eine Sprache oder ein Sprachland:

* Der Name des Knotens ist der Sprachcode (z. B. `en` oder `de`) oder dem Sprachcode_country (z. B. `en_us` oder `de_ch`).

* In der Eigenschaft `language` des Knotens wird der volle Name der Sprache für den Code gespeichert.
* In der Eigenschaft `country` des Knotens wird der volle Name des Landes für den Code gespeichert.
* Wenn der Knotenname nur aus einem Sprach-Code besteht (z. B. `en`), ist die Ländereigenschaft `*` und die zusätzliche Eigenschaft `defaultCountry` speichert den Code des Sprachlandes, um das zu verwendende Land anzugeben.

![Sprachdefinition](assets/msm-language-manager.png)

So bearbeiten Sie die Sprachen:

1. Öffnen Sie CRXDE Lite.
1. Wählen Sie den Ordner `/apps` aus und klicken Sie auf **Erstellen** und dann auf **Ordner erstellen**.

1. Geben Sie dem neuen Ordner den Namen `wcm`.

1. Wiederholen Sie diesen Schritt, um die Ordnerstruktur `/apps/wcm/core` zu erstellen. Erstellen Sie in `sling:Folder` einen Knoten des Typs `core` mit dem Namen `resources`.

1. Klicken Sie mit der rechten Maustaste auf den Knoten `/libs/wcm/core/resources/languages` und klicken Sie auf **Kopieren**.
1. Klicken Sie mit der rechten Maustaste auf den Ordner `/apps/wcm/core/resources` und klicken Sie auf **Einfügen**. Ändern Sie die untergeordneten Knoten nach Bedarf.
1. Klicken Sie auf **Alle speichern**.
1. Klicken Sie auf **Tools** > **Vorgänge** > **Web-Konsole**. Klicken Sie in dieser Konsole auf **OSGi** > **Konfiguration**.
1. Suchen Sie **Day CQ WCM Language Manager**, klicken Sie darauf und ändern Sie den Wert von **Language List** in `/apps/wcm/core/resources/languages`. Klicken Sie dann auf **Speichern**.

   ![Day CQ WCM Language Manager](assets/msm-language-manager.png)

## Konfigurieren von MSM-Sperren für Seiteneigenschaften {#configuring-msm-locks-on-page-properties}

Beim Erstellen einer benutzerdefinierten Seiteneigenschaft müssen Sie ggf. überlegen, ob die neue Eigenschaft für den Rollout auf allen Live Copies qualifiziert sein soll.

Beispiel: Zwei neue Seiteneigenschaften werden hinzugefügt:

* Kontakt-E-Mail:

   * Diese Eigenschaft muss nicht bereitgestellt werden, da sie in jedem Land (oder bei jeder Marke usw.) anders ausfällt.

* Wichtigster visueller Stil:

   * Die Projektanforderung gibt das Bereitstellen dieser Eigenschaft vor, da sie (in der Regel) in allen Ländern (oder bei allen Marken usw.) gleich ist.

Dann müssen Sie Folgendes sicherstellen:

* Kontakt-E-Mail:

   * ist von den Rollout-Eigenschaften ausgeschlossen.
   * Siehe [Live Copy-Synchronisierung konfigurieren](/help/sites-cloud/administering/msm/live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) für weitere Informationen.

* Wichtigster visueller Stil:

   * Stellen Sie sicher, dass Sie diese Eigenschaft nur bearbeiten dürfen, wenn die Vererbung abgebrochen wurde.
   * Stellen Sie außerdem sicher, dass Sie dann die Vererbung erneut aktivieren können. Dies wird gesteuert, indem auf die Kettenlinks/unterbrochenen Kettenlinks geklickt wird, um den Status der Verbindung anzuzeigen.

Ob für eine Seiteneigenschaft ein Rollout durchgeführt werden muss und daher beim Bearbeiten die Vererbung abgebrochen/reaktiviert werden kann, wird durch die folgende Dialogeigenschaft gesteuert:

* `cq-msm-lockable`

   * Dadurch wird das Kettenverknüpfungssymbol im Dialogfeld erstellt.
   * Dies ermöglicht nur die Bearbeitung, wenn die Vererbung abgebrochen wurde (das Kettenglied ist beschädigt).
   * Dies gilt nur für die erste untergeordnete Ebene der Ressource
      * **Typ**: `String`
      * **Wert**: Enthält den Namen der betreffenden Immobilie und ist mit dem Wert der Immobilie vergleichbar `name`
         * Ein Beispiel finden Sie unter
           `/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title`

Wenn `cq-msm-lockable` definiert wurde, interagiert das Öffnen oder Schließen der Kettenverbindung mit MSM wie folgt:

* Wenn der Wert von `cq-msm-lockable` ist:

   * **Relativ** (zum Beispiel: `myProperty` oder `./myProperty`)

      * Durch Aufbrechen der Kette wird die Eigenschaft hinzugefügt und aus entfernt. `cq:propertyInheritanceCancelled`.

   * **Absolut** (zum Beispiel: `/image`)

      * Wenn Sie die Kette durchbrechen, wird die Vererbung durch Hinzufügen der `cq:LiveSyncCancelled` Mixin zu `./image` und Einstellung `cq:isCancelledForChildren` nach `true`.

      * Wenn Sie die Kette schließen, wird die Vererbung zurückgesetzt.

>[!NOTE]
>
>`cq-msm-lockable` gilt für die erste untergeordnete Ebene der Ressource, die bearbeitet werden soll, und funktioniert nicht auf einem Vorläuferelement auf einer tieferen Ebene, unabhängig davon, ob der Wert als absolut oder relativ definiert ist.

>[!NOTE]
>
>Wenn Sie die Vererbung erneut aktivieren, wird die Eigenschaft der Live Copy-Seite nicht automatisch mit der Quelleigenschaft synchronisiert. Sie können ggf. manuell eine Synchronisierung anfordern.
