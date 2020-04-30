---
title: AEM-Projektstruktur
description: Erfahren Sie, wie Sie Paketstrukturen für die Bereitstellung im Adobe Experience Manager Cloud-Dienst definieren.
translation-type: tm+mt
source-git-commit: 94182b95cb00923d3e055cb3c2e1d943db70c7a9

---


# AEM-Projektstruktur

>[!TIP]
>
>Machen Sie sich mit der grundlegenden [Verwendung des AEM-Projektarchetyps](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html) vertraut und dem [FileVault Content Maven-Plug-in](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html), da dieser Artikel auf diesen Erkenntnissen und Konzepten aufbaut.

In diesem Artikel werden die Änderungen erläutert, die erforderlich sind, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind, indem sichergestellt wird, dass sie die Aufteilung von veränderlichem und unveränderlichem Inhalt respektieren, dass die erforderlichen Abhängigkeiten zur Schaffung nicht widersprüchlicher, deterministischer Implementierungen festgelegt werden und dass sie in einer implementierbaren Struktur zusammengefasst sind.

AEM-Anwendungsimplementierungen müssen aus einem einzigen AEM-Paket bestehen. Dieses Paket sollte wiederum Unterpakete enthalten, die alles enthalten, was die Anwendung benötigt, um zu funktionieren, einschließlich Code, Konfiguration und unterstützenden Basisinhalten.

AEM erfordert eine Trennung von **Inhalt** und **Code**. Dies bedeutet, dass ein einzelnes Inhaltspaket **nicht** für **beide** `/apps` und für Laufzeitbereiche (z. B. `/content`, `/conf`, `/home` oder alles, was nicht `/apps` ist) des Repositorys bereitstellen kann. Stattdessen muss die Anwendung Code und Inhalt in separate Pakete für die Bereitstellung in AEM trennen.

Die in diesem Dokument beschriebene Paketstruktur ist mit lokalen Entwicklungsbereitstellungen **und** AEM Cloud Service-Bereitstellungen kompatibel.

>[!TIP]
>
>Die in diesem Dokument beschriebenen Konfigurationen werden von [AEM-Projektarchetyp 21 oder höher](https://github.com/adobe/aem-project-archetype/releases) bereitgestellt.

## Veränderliche und nicht veränderliche Bereiche des Repositorys {#mutable-vs-immutable}

`/apps` und `/libs` werden als **unveränderliche** Bereiche von AEM betrachtet, da sie nach dem Start von AEM (d. h. zur Laufzeit) nicht mehr geändert (erstellt, aktualisiert, gelöscht) werden können . Jeder Versuch, einen unveränderlichen Bereich zur Laufzeit zu ändern, schlägt fehl.

Everything else in the repository, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`, etc. sind alles **veränderliche** Bereiche, d. h. sie können zur Laufzeit geändert werden.

>[!WARNING]
>
> Wie in früheren Versionen von AEM sollten `/libs` nicht geändert werden. Nur der AEM-Produkt-Code darf für `/libs` bereitstellen.

## Empfohlene Paketstruktur {#recommended-package-structure}

![Experience Manager-Projektpaketstruktur](assets/content-package-organization.png)

Dieses Diagramm bietet eine Übersicht über die empfohlene Projektstruktur und die empfohlenen Artefakte zur Paketbereitstellung.

Die empfohlene Bereitstellungsstruktur für Anwendungen lautet wie folgt:

+ The `ui.apps` package, or Code Package, contains all the code to be deployed and only deploys to `/apps`. Zu den gebräuchlichen Elementen des `ui.apps`-Pakets gehören unter anderem:
   + OSGi-Bundles
      + `/apps/my-app/install`
   + OSGi-Konfigurationen
      + `/apps/my-app/config`
   + HTML-Skripte
      + `/apps/my-app/components`
   + JavaScript und CSS (über Client-Bibliotheken)
      + `/apps/my-app/clientlibs`
   + Überlagerungen von /libs
      + `/apps/cq`, `/apps/dam/` usw.
   + Kontextabhängige Ausweichkonfigurationen
      + `/apps/settings`
   + ACLs (Berechtigungen)
      + Alle `rep:policy` für einen Pfad unter `/apps`
   + Repo Init OSGi-Konfigurationsanweisungen (und zugehörige Skripten)
      + [Repo Init](#repo-init) ist die empfohlene Methode zum Bereitstellen (veränderlicher) Inhalte, die logisch Teil der AEM-Anwendung sind. Repo Init sollte verwendet werden, um Folgendes zu definieren:
         + Grundlegende Inhaltsstrukturen
            + `/conf/my-app`
            + `/content/my-app`
            + `/content/dam/my-app`
         + Benutzer
         + Dienstbenutzer
         + Gruppen
         + ACLs (Berechtigungen)
            + Beliebig `rep:policy` für alle Pfade (veränderlich oder unveränderlich)
+ The `ui.content` package, or Content Package, contains all content and configuration. Das Inhaltspaket enthält alles, was nicht im `ui.apps` Paket enthalten ist, oder mit anderen Worten, alles, was nicht in `/apps` oder `/oak:index`. Zu den gebräuchlichen Elementen des `ui.content`-Pakets gehören unter anderem:
   + Kontextabhängige Konfigurationen
      + `/conf`
   + Erforderliche, komplexe Inhaltsstrukturen (d. h. Inhaltsaufbau, der auf in Repo Init definierten Inhaltsstrukturen aufbaut und diese erweitert.
      + `/content`, `/content/dam` usw.
   + Geregelte Tagging-Taxonomien
      + `/content/cq:tags`
   + Veraltete etc-Knoten
      + `/etc`
+ Das `all`-Paket ist ein Container-Paket, das NUR die `ui.apps`- und `ui.content`-Pakete als Einbettung enthält. Das `all`-Paket darf keinen eigenen Inhalt **** haben, sondern muss die Bereitstellung an das Repository an seine Unterpakete delegieren.

   Pakete werden jetzt mit der [eingebetteten Konfiguration des FileVault Package Maven-Plug-ins](#embeddeds) eingebunden, anstatt mit der `<subPackages>`-Konfiguration.

   Bei komplexen Experience Manager-Bereitstellungen ist es möglicherweise wünschenswert, mehrere `ui.apps`- und `ui.content`-Projekte/-Pakete zu erstellen, die bestimmte Sites oder Mandanten in AEM darstellen. Ist dies der Fall, stellen Sie sicher, dass die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt eingehalten wird und die erforderlichen Inhaltspakete als Unterpakete im Container-Inhaltspaket `all` hinzugefügt werden.

   Beispielsweise könnte eine komplexe Struktur eines Inhaltspakets für die Bereitstellung wie folgt aussehen:

   + Inhaltspaket `all` bettet die folgenden Pakete ein, um ein einzelnes Bereitstellungsartefakt zu erstellen
      + `ui.apps.common` stellt Code bereit, der **sowohl** für Site A als auch für Site B erforderlich ist
      + `ui.apps.site-a` stellt Code bereit, der für Site A erforderlich ist
      + `ui.content.site-a` stellt Inhalte und Konfigurationen bereit, die für Site A erforderlich sind
      + `ui.apps.site-b` stellt Code bereit, der für Site B erforderlich ist
      + `ui.content.site-b` stellt Inhalte und Konfigurationen bereit, die für Site B erforderlich sind

## Pakettypen {#package-types}

Die Pakete sind mit ihrem deklarierten Pakettyp zu kennzeichnen.

+ Container-Pakete dürfen keinen `packageType`-Satz haben.
+ (Unveränderliche) Code-Pakete müssen `packageType` auf `application` setzen.
+ (Veränderliche) Inhaltspakete müssen `packageType` auf `content` setzen.

Weitere Informationen finden Sie in der [Dokumentation zum Apache Jackrabbit FileVault Package Maven-Plug-in](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType) und dem [Konfigurations-Snippet für FileVault Maven](#marking-packages-for-deployment-by-adoube-cloud-manager) unten.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-package-types) unten.

## Markieren von Paketen für die Bereitstellung durch Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}

Standardmäßig sammelt Adobe Cloud Manager alle vom Maven-Build erstellten Pakete. Da jedoch das Container-Paket (`all`) das einzige Bereitstellungs-Artefakt ist, das alle Code- und Inhaltspakete enthält, müssen wir sicherstellen, dass **nur** das Container-Paket (`all`) bereitgestellt wird. Um dies sicherzustellen, müssen andere Pakete, die der Maven-Build generiert, mit der FileVault Content Package Maven Plug-in-Konfiguration von `<properties><cloudManagerTarget>none</cloudManageTarget></properties>` gekennzeichnet werden.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#pom-xml-snippets) unten.

## Repo-Init{#repo-init}

Repo Init enthält Anweisungen oder Skripten, mit denen JCR-Strukturen definiert werden, von allgemeinen Knotenstrukturen wie Ordnerbäumen bis hin zu Benutzern, Dienstbenutzern, Gruppen und ACL-Definition.

Die wichtigsten Vorteile von Repo Init sind die impliziten Berechtigungen, alle von ihren Skripten definierten Aktionen durchzuführen, und sie werden frühzeitig im Bereitstellungslebenszyklus aufgerufen, um sicherzustellen, dass alle erforderlichen JCR-Strukturen vorhanden sind, bis der Code ausgeführt wird.

Während Repo Init-Skripte selbst als Skripten im `ui.apps` Projekt live sind, können und sollten sie zum Definieren der folgenden veränderbaren Strukturen verwendet werden:

+ Grundlegende Inhaltsstrukturen
   + Examples: `/content/my-app`, `/content/dam/my-app`, `/conf/my-app/settings`
+ Dienstbenutzer
+ Benutzer
+ Gruppen
+ ACLs

Repo-Init-Skripten werden als Einträge in `scripts` `RepositoryInitializer` OSGi-Werkskonfigurationen gespeichert und können daher implizit durch den Ausführungsmodus Targeting erfolgen. Dies ermöglicht Unterschiede zwischen den Repo Init-Skripten von AEM Author und AEM Publish Services oder sogar zwischen Envs (Dev, Stage und Prod).

Beachten Sie, dass bei der Definition von Benutzern und Gruppen nur Gruppen als Teil der Anwendung betrachtet werden und dass hier als integraler Bestandteil ihrer Funktion definiert werden sollte. Organisationsbenutzer und -gruppen sollten weiterhin zur Laufzeit in AEM definiert werden. Wenn beispielsweise ein benutzerdefinierter Arbeitsablauf einer benannten Gruppe Aufgaben zuweist, sollte diese Gruppe in der AEM-Anwendung über Repo Init definiert werden. Wenn die Gruppierung jedoch lediglich organisatorisch ist, wie &quot;Wendy&#39;s Team&quot;und &quot;Sean&#39;s Team&quot;, sind diese am besten definiert und werden zur Laufzeit in AEM verwaltet.

>[!TIP]
>
>Repo Init-Skripten *müssen* im Inline- `scripts` Feld definiert werden, und die `references` Konfiguration funktioniert nicht.

Das vollständige Vokabular für Repo Init-Skripte ist in der [Apache Sling Repo Init-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)verfügbar.

>[!TIP]
>
>See the [Repo Init Snippets](#snippet-repo-init) section below for a complete snippet.

## Repository-Strukturpaket {#repository-structure-package}

Code-Pakete müssen das FileVault Maven-Plug-in so konfigurieren, dass auf ein `<repositoryStructurePackage>` verwiesen wird, das die Richtigkeit struktureller Abhängigkeiten erzwingt (um sicherzustellen, dass ein Code-Paket nicht über ein anderes installiert wird). Sie können [Ihr eigenes Repository-Strukturpaket für Ihr Projekt erstellen](repository-structure-package.md).

Dies ist **nur für Code-Pakete erforderlich**, d. h. für alle Pakete, die mit `<packageType>application</packageType>` gekennzeichnet sind.

Informationen zum Erstellen eines Repository-Strukturpakets für Ihre Anwendung finden Sie unter [Entwickeln eines Repository-Strukturpakets](repository-structure-package.md).

Beachten Sie, dass dieses Repository-Strukturpaket für Inhaltspakete (`<packageType>content</packageType>`) **nicht** erforderlich ist.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-repository-structure-package) unten.

## Einbetten von Unterpaketen in das Container-Paket{#embeddeds}

Inhalts- oder Code-Pakete werden in einem speziellen „Side-Car“-Ordner abgelegt und können mithilfe der `<embeddeds>`-Konfiguration des FileVault Maven-Plug-ins entweder auf AEM Autor, AEM Publish oder beiden installiert werden. Beachten Sie, dass die `<subPackages>`-Konfiguration nicht verwendet werden sollte.

Häufige Anwendungsfälle sind:

+ ACLs/Berechtigungen, die sich zwischen AEM Author- und AEM Publish-Benutzern unterscheiden
+ Konfigurationen, die nur zur Unterstützung von Aktivitäten in AEM Author verwendet werden
+ Code, wie z.B. Integrationen mit Backoffice-Systemen, die nur auf in AEM Author laufen müssen

![Einbetten von Paketen](assets/embeddeds.png)

Um AEM Author, AEM Publish oder beides als Ziel festzulegen, wird das Paket in das `all`-Container-Paket an einem bestimmten Ordnerspeicherort im folgenden Format eingebettet:

`/apps/<app-name>-packages/(content|application)/install(.author|.publish)?`

Aufschlüsselung dieser Ordnerstruktur:

+ Der Ordner der ersten Ebene **muss** `/apps` sein.
+ Der Ordner der zweiten Ebene stellt die Anwendung dar, wobei `-packages` an den Ordnernamen angehängt wird. Häufig gibt es nur einen einzigen Ordner der zweiten Ebene, unter dem alle Unterpakete eingebettet sind. Es können jedoch beliebig viele Ordner der zweiten Ebene erstellt werden, um die logische Struktur der Anwendung bestmöglich darzustellen:
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`
   >[!WARNING]
   >
   >Konventionell werden eingebettete Unterpakete mit dem Suffix `-packages` benannt. Dadurch wird sichergestellt, dass der Bereitstellungs-Code und die Inhaltspakete **nicht** in den Zielordnern eines Unterpakets `/apps/<app-name>/...` bereitgestellt werden, was zu destruktiven und zyklischen Installationsverhalten führt.

+ Der Ordner der dritten Ebene muss
   `application` oder `content` sein.
   + Der `application`-Ordner enthält Code-Pakete
   + Der `content`-Ordner enthält Inhaltspakete
Dieser Ordnername muss den [Pakettypen](#package-types) der darin enthaltenen Pakete entsprechen.
+ Der Ordner der vierten Ebene enthält die Unterpakete und muss einer der folgenden sein:
   + `install` zur Installation auf **beiden**, AEM Author und AEM Publish
   + `install.author` zur Installation **nur** auf AEM Author
   + `install.publish` zur Installation **nur** auf AEM Publish
Beachten Sie, dass nur `install.author` und `install.publish` unterstützte Ziele sind. Andere Ausführungsmodi werden **nicht** unterstützt.

Beispielsweise kann eine Bereitstellung, die AEM Author- und Publish-spezifische Pakete enthält, wie folgt aussehen:

+ Container-Paket `all` bettet die folgenden Pakete ein, um ein einzelnes Bereitstellungsartefakt zu erstellen
   + `ui.apps` eingebettet in `/apps/my-app-packages/application/install` stellt Code für AEM Author und AEM Publish bereit
   + `ui.apps.author` eingebettet in `/apps/my-app-packages/application/install.author` stellt Code nur für AEM Author bereit
   + `ui.content` eingebettet in `/apps/my-app-packages/content/install` stellt Inhalte und Konfiguration für AEM Author und AEM Publish bereit
   + `ui.content.publish` eingebettet in `/apps/my-app-packages/content/install.publish` stellt Inhalte und Konfiguration nur für AEM Publish bereit

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-embeddeds) unten.

### Filterdefinition des Container-Pakets {#container-package-filter-definition}

Aufgrund der Einbettung von Code- und Inhalts-Unterpaketen in das Container-Paket müssen die eingebetteten Zielpfade zu `filter.xml` des Container-Projekts hinzugefügt werden, um sicherzustellen, dass die eingebetteten Pakete beim Erstellen im Container-Paket enthalten sind.

Fügen Sie einfach die `<filter root="/apps/<my-app>-packages"/>`-Einträge für alle Ordner der zweiten Ebene hinzu, die zu bereitzustellende Unterpakete enthalten.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-container-package-filters) unten.

## Einbetten von Drittanbieter-Paketen {#embedding-3rd-party-packages}

Alle Pakete müssen über das [öffentliche Maven-Artefakt-Repository von Adobe](https://repo.adobe.com/nexus/content/groups/public/com/adobe/) oder ein öffentlich zugängliches, referenzierbares Maven-Artefakt-Repository von Drittanbietern verfügbar sein.

Wenn sich die Pakete von Drittanbietern im **öffentlichen Maven-Artefakt-Repository von Adobe** befinden, ist für Adobe Cloud Manager keine weitere Konfiguration erforderlich, um die Artefakte aufzulösen.

Wenn sich die Pakete von Drittanbietern in einem **öffentlichen Maven-Artefakt-Repository von Drittanbietern** befinden, muss dieses Repository in der `pom.xml` des Projekts registriert und gemäß der [oben beschriebenen](#embeddeds) Methode eingebettet werden. Wenn für die Anwendung/den Connector eines Drittanbieters sowohl Code- als auch Inhaltspakete erforderlich sind, muss jedes an den richtigen Speicherorten in Ihrem Container (`all`)-Paket eingebettet sein.

Das Hinzufügen von Maven-Abhängigkeiten folgt den Standardpraktiken von Maven, und das Einbetten von Artefakten von Drittanbietern (Code- und Inhaltspakete) ist [oben beschrieben](#embedding-3rd-party-packages).

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-3rd-party-maven-repositories) unten.

## Paketabhängigkeiten zwischen den `ui.apps` von `ui.content`-Paketen {#package-dependencies}

Um eine ordnungsgemäße Installation der Pakete sicherzustellen, wird empfohlen, Abhängigkeiten zwischen Paketen zu erstellen.

Die allgemeine Regel ist, dass Pakete mit veränderlichem Inhalt (`ui.content`) vom unveränderlichen Inhalt (`ui.apps`) abhängen sollten, der die Wiedergabe und Verwendung des veränderlichen Inhalts unterstützt.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-package-dependencies) unten.

Die üblichen Muster für Abhängigkeiten von Inhaltspaketen sind:

### Abhängigkeiten von einfachen Bereitstellungspaketen {#simple-deployment-package-dependencies}

Im einfachen Fall hängt das veränderliche Inhaltspaket `ui.content` vom unveränderlichen Code-Paket `ui.apps` ab.

+ `all` hat keine Abhängigkeiten
   + `ui.apps` hat keine Abhängigkeiten
   + `ui.content` hängt von `ui.apps` ab

### Abhängigkeiten von komplexen Bereitstellungspaketen {#complex-deploxment-package-dependencies}

Komplexe Implementierungen gehen über den einfachen Fall hinaus und legen Abhängigkeiten zwischen den entsprechenden veränderbaren Inhalten und unveränderlichen Code-Paketen fest. Abhängigkeiten können bei Bedarf auch zwischen unveränderlichen Code-Paketen festgelegt werden.

+ `all` hat keine Abhängigkeiten
   + `ui.apps.common` hat keine Abhängigkeiten
   + `ui.apps.site-a` hängt von `ui.apps.common` ab
   + `ui.content.site-a` hängt von `ui.apps.site-a` ab
   + `ui.apps.site-b` hängt von `ui.apps.common` ab
   + `ui.content.site-b` hängt von `ui.apps.site-b` ab

## Lokale Entwicklung und Bereitstellung {#local-development-and-deployment}

Die in diesem Artikel beschriebenen Projektstrukturen und -organisationen sind mit AEM-Instanzen für die lokale Entwicklung **vollständig kompatibel**.

## POM-XML-Snippets {#pom-xml-snippets}

Im Folgenden finden Sie Maven `pom.xml`-Konfigurations-Snippets, die zu Maven-Projekten hinzugefügt werden können, um sie an die oben genannten Empfehlungen anzupassen.

### Pakettypen {#xml-package-types}

Code- und Inhaltspakete, die als Unterpakete bereitgestellt werden, müssen abhängig davon, was sie enthalten, **application** oder **content** als Pakettyp deklarieren.

#### Container-Pakettypen {#container-package-types}

Das Container-Projekt `all/pom.xml` deklariert **keinen** `<packageType>`.

#### (Unveränderliche) Code-Pakettypen {#immutable-package-types}

Code-Pakete müssen ihren `packageType` auf `application` setzen.

In der `ui.apps/pom.xml` deklariert die `<packageType>application</packageType>`-Build-Konfigurationsanweisung der `filevault-package-maven-plugin`-Plug-in-Deklaration den Pakettyp.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        <group>${project.groupId}</group>
        <name>${my-app.ui.apps}</name>
        <packageType>application</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

#### (Veränderliche) Code-Pakettypen {#mutable-package-types}

Inhaltspakete müssen ihren `packageType` auf `content` setzen.

In der `ui.content/pom.xml` deklariert die `<packageType>content</packageType>`-Build-Konfigurationsanweisung der `filevault-package-maven-plugin`-Plug-in-Deklaration den Pakettyp.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        <group>${project.groupId}</group>
        <name>${my-app.ui.content}</name>
        <packageType>content</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### Markieren von Paketen für die Bereitstellung über Adobe Cloud Manager {#cloud-manager-target}

Fügen Sie in jedem Projekt, das ein Paket generiert, **mit Ausnahme** des Container-Projekts (`all`), `<cloudManagerTarget>none</cloudManagerTarget>` der `<properties>`-Konfiguration der `filevault-package-maven-plugin`-Plug-in-Deklaration hinzu, um sicherzustellen, dass sie **nicht** von Adobe Cloud Manager bereitgestellt werden. Das Container-Paket (`all`) sollte das Einzelpaket sein, das über Cloud Manager bereitgestellt wird. Dadurch werden alle erforderlichen Code- und Inhaltspakete eingebettet.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### Repo-Init{#snippet-repo-init}

Repo Init-Skripten, die die Repo Init-Skripten enthalten, werden in der `RepositoryInitializer` OSGi-Factory-Konfiguration über die `scripts` Eigenschaft definiert. Beachten Sie, dass diese Skripte, die in OSGi-Konfigurationen definiert sind, einfach per Ausführungsmodus mithilfe der üblichen `../config.<runmode>` Ordnersemantik überprüft werden können.

Da Skripten in der Regel mehrzeilige Deklarationen sind, ist es einfacher, sie in der `.config` Datei zu definieren, als das XML-Basenformat `sling:OsgiConfig` .

`/apps/my-app/config.author/org.apache.sling.jcr.repoinit.RepositoryInitializer-author.config`

```plain
scripts=["
    create service user my-data-reader-service

    set ACL on /var/my-data
        allow jcr:read for my-data-reader-service
    end

    create path (sling:Folder) /conf/my-app/settings
"]
```

Die `scripts` OSGi-Eigenschaft enthält Direktiven, die von der Repo Init-Sprache [des](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)Apache Sling definiert werden.

### Repository-Strukturpaket {#xml-repository-structure-package}

Fügen Sie in `ui.apps/pom.xml` und allen anderen `pom.xml`, die ein Code-Paket (`<packageType>application</packageType>`) deklarieren, die folgende Repository-Strukturpaketkonfiguration zum FileVault Maven-Plug-in hinzu. Sie können [Ihr eigenes Repository-Strukturpaket für Ihr Projekt erstellen](repository-structure-package.md).

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <repositoryStructurePackages>
          <repositoryStructurePackage>
              <groupId>${project.groupId}</groupId>
              <artifactId>ui.apps.structure</artifactId>
              <version>${project.version}</version>
          </repositoryStructurePackage>
        </repositoryStructurePackages>
      </configuration>
    </plugin>
    ...
```

### Einbetten von Unterpaketen in das Container-Paket {#xml-embeddeds}

Fügen Sie in `all/pom.xml` der `filevault-package-maven-plugin`-Plug-in-Deklaration die folgenden `<embeddeds>`-Anweisungen hinzu. Denken Sie daran, die `<subPackages>`-Konfiguration **nicht** zu verwenden, da dies die Unterpakete in `/etc/packages` anstatt in `/apps/my-app-packages/<application|content>/install(.author|.publish)?` einschließt.

```xml
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <embeddeds>

          <!-- Include the application's ui.apps and ui.content packages -->
          <!-- Ensure the artifactIds are correct -->

          <!-- Code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

          <!-- Code package that deploys ONLY to AEM Author -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps.author</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install.author</target>
          </embedded>

          <!-- Content package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.content</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/content/install</target>
          </embedded>

          <!-- Content package that deploys ONLY to AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.content.publish-only</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/content/install.publish</target>
          </embedded>

          <!-- Include any other extra packages such as AEM WCM Core Components -->
          <embedded>
              <groupId>com.adobe.cq</groupId>
              <!-- Not to be confused; WCM Core Components' Code package's artifact is named `.content` -->
              <artifactId>core.wcm.components.content</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/application/install</target>
          </embedded>

          <embedded>
              <groupId>com.adobe.cq</groupId>
              <!-- Not to be confused; WCM Core Components' Content package's artifact is named `.conf` -->
              <artifactId>core.wcm.components.conf</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/content/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

### Filterdefinition des Container-Pakets {#xml-container-package-filters}

In der `filter.xml` des `all`-Projekts (`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`) **schließen Sie** alle `-packages`-Ordner ein, die bereitzustellende Unterpakete enthalten:

```xml
<filter root="/apps/my-app-packages"/>
```

Wenn mehrere `/apps/*-packages` in den eingebetteten Zielen verwendet werden, müssen sie hier alle aufgezählt werden.

### Maven-Repositorys von Drittanbietern {#xml-3rd-party-maven-repositories}

>[!WARNING]
> Durch das Hinzufügen von mehr Maven-Repositorys können die Maven-Buildzeiten verlängert werden, da zusätzliche Maven-Repositorys auf Deep-Threads überprüft werden.

Fügen Sie im `pom.xml` des Reaktorprojekts alle erforderlichen öffentlichen Maven-Repository-Anweisungen von Drittanbietern hinzu. Die vollständige `<repository>`-Konfiguration sollte beim Repository-Drittanbieter erhältlich sein.

```xml
<repositories>
  ...
  <repository>
      <id>3rd-party-repository</id>
      <name>Public 3rd Party Repository</name>
      <url>https://repo.3rdparty.example.com/...</url>
      <releases>
          <enabled>true</enabled>
          <updatePolicy>never</updatePolicy>
      </releases>
      <snapshots>
          <enabled>false</enabled>
      </snapshots>
  </repository>
  ...
</repositories>
```

### Paketabhängigkeiten zwischen den `ui.apps` von `ui.content`-Paketen {#xml-package-dependencies}

Fügen Sie in `ui.content/pom.xml` der `filevault-package-maven-plugin`-Plug-in-Deklaration die folgenden `<dependencies>`-Anweisungen hinzu.

```xml
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <dependencies>
        <!-- Declare the content package dependency in the ui.content/pom.xml on the ui.apps project -->
        <dependency>
            <groupId${project.groupId}</groupId>
            <artifactId>my-app.ui.apps</artifactId>
            <version>${project.version}</version>
        </dependency>
      </dependencies>
    ...
  </configuration>
</plugin>
...
```

### Bereinigen des Zielordners des Container-Projekts {#xml-clean-container-package}

Fügen Sie `all/pom.xml` das `maven-clean-plugin`-Plug-in hinzu, welches den Zielordner vor einem Maven-Build bereinigt.

```xml
<plugins>
  ...
  <plugin>
    <artifactId>maven-clean-plugin</artifactId>
    <executions>
      <execution>
        <id>auto-clean</id>
        <!-- Run at the beginning of the build rather than the default, which is after the build is done -->
        <phase>initialize</phase>
        <goals>
          <goal>clean</goal>
        </goals>
      </execution>
    </executions>
  </plugin>
  ...
</plugins>
```

## Zusätzliche Ressourcen {#additional-resources}

+ [Verwalten von Paketen mithilfe von Maven](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html)
+ [FileVault Content Package Maven-Plug-in](http://jackrabbit.apache.org/filevault-package-maven-plugin/)