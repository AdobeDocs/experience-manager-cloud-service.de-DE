---
title: AEM-Projektstruktur
description: Erfahren Sie, wie Sie Paketstrukturen für die Bereitstellung im Adobe Experience Manager Cloud-Dienst definieren.
translation-type: tm+mt
source-git-commit: a6efcbb85949e65167ebab0e2a8dae06eaeaa07f

---


# AEM-Projektstruktur

>[!TIP]
>
>Machen Sie sich mit der grundlegenden Verwendung [des](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM Project Archetype vertraut und dem [FileVault Content Maven-Plug-in](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html) , das auf diesen Erkenntnissen und Konzepten aufbaut.

In diesem Artikel werden die Änderungen erläutert, die erforderlich sind, damit Adobe Experience Manager Maven-Projekte mit AEM Cloud Service kompatibel sind, indem sichergestellt wird, dass sie die Aufteilung von veränderlichem und unveränderlichem Inhalt respektieren. dass die erforderlichen Abhängigkeiten zur Schaffung nicht widersprüchlicher, deterministischer Einsätze festgelegt werden; und dass sie in einer bereitstellbaren Struktur zusammengefasst sind.

Die Bereitstellung von AEM-Anwendungen muss aus einem einzigen AEM-Paket bestehen. Dieses Paket sollte wiederum Unterpakete enthalten, die alles enthalten, was die Anwendung benötigt, um zu funktionieren, einschließlich Code, Konfiguration und unterstützendem Basisinhalt.

AEM erfordert eine Trennung von **Inhalt** und **Code**. Dies bedeutet, dass ein einzelnes Inhaltspaket **nicht** **sowohl** für `/apps` als auch für zur Laufzeit schreibbar Bereiche des Repositorys bereitstellen kann (z. B. `/content`, `/conf`, `/home` oder alles andere als `/apps`). Stattdessen muss die Anwendung Code und Inhalt in separaten Pakete für die Implementierung in AEM voneinander trennen.

Die in diesem Dokument beschriebene Paketstruktur ist **sowohl** mit lokalen Entwicklungsbereitstellungen als auch mit AEM Cloud Service-Bereitstellungen kompatibel.

>[!TIP]
>
>Die in diesem Dokument beschriebenen Konfigurationen werden von [AEM Project Maven Archetype 21 oder höher](https://github.com/adobe/aem-project-archetype/releases)bereitgestellt.

## Veränderliche und nicht veränderliche Bereiche des Repositorys {#mutable-vs-immutable}

`/apps` und `/libs` werden als **unveränderliche** Bereiche von AEM betrachtet, da sie nach dem Start von AEM (d. h. zur Laufzeit) nicht mehr geändert werden können (erstellen, aktualisieren, löschen). Jeder Versuch, einen unveränderlichen Bereich zur Laufzeit zu ändern, schlägt fehl.

Alles andere im Repository, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`usw. sind alle **veränderbare** Bereiche, d.h. sie können zur Laufzeit geändert werden.

>[!WARNING]
>
> Wie in früheren Versionen von AEM sollten Sie `/libs` keine Änderungen vornehmen. Nur der AEM-Produktcode darf bereitgestellt werden für `/libs`.

## Empfohlene Paketstruktur {#recommended-package-structure}

![Experience Manager-Projektpaket-Struktur](assets/content-package-organization.png)

Dieses Diagramm bietet eine Übersicht über die empfohlene Projektstruktur und die empfohlenen Artefakte zur Paketbereitstellung.

Die empfohlene Anwendungsbereitstellungsstruktur lautet wie folgt:

+ Das `ui.apps` Paket bzw. das Inhaltspaket enthält den gesamten bereitzustellenden Code und stellt nur für `/apps`die Bereitstellung bereit. Zu den gebräuchlichen Elementen des `ui.apps` Pakets gehören:
   + OSGi-Pakete
      + `/apps/my-app/install`
   + OSGi-Konfigurationen
      + `/apps/my-app/config`
   + HTML-Skripten
      + `/apps/my-app/components`
   + JavaScript und CSS (über Client-Bibliotheken)
      + `/apps/my-app/clientlibs`
   + Überlagerungen von /libs
      + `/apps/cq`, `/apps/dam/`, usw.
   + Kontextabhängige Ersatzkonfigurationen
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
+ Das `ui.content` Paket bzw. das Codepaket enthält alle Inhalte und Konfigurationen. Zu den gebräuchlichen Elementen des `ui.content` Pakets gehören:
   + Kontextsensitive Konfigurationen
      + `/conf`
   + Erforderliche, komplexe Inhaltsstrukturen (d. h. Inhaltsaufbau, der auf in Repo Init definierten Inhaltsstrukturen aufbaut und diese erweitert.
      + `/content`, `/content/dam`, usw.
   + Steuerbare Taggategruppen
      + `/content/cq:tags`
   + Eichenindizes
      + `/oak:index`
   + Ältere Knoten
      + `/etc`
+ Das `all`-Paket ist ein Containerpaket, das NUR die `ui.apps`- und `ui.content`-Pakete als Einbettung enthält. Das `all`-Paket darf **keinen eigenen Inhalt** haben, sondern muss alle Implementierungen für das Repository an die Unterpakete delegieren.

   Pakete werden jetzt mit der Einbettungskonfiguration [des Maven](#embeddeds)FileVault Package Maven-Plug-Ins anstelle der `<subPackages>` Konfiguration enthalten.

   Bei komplexen Experience Manager-Bereitstellungen ist es möglicherweise wünschenswert, mehrere `ui.apps` und `ui.content` mehrere Projekte/Pakete zu erstellen, die bestimmte Sites oder Mieter in AEM darstellen. Ist dies der Fall, stellen Sie sicher, dass die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt eingehalten wird und die erforderlichen Inhaltspakete als Unterpakete im `all` Container-Inhaltspaket hinzugefügt werden.

   Beispielsweise könnte eine komplexe Struktur eines Inhaltspakets für die Bereitstellung wie folgt aussehen:

   + `all` Inhaltspaket bettet die folgenden Pakete ein, um ein einzelnes Bereitstellungsartefakt zu erstellen
      + `ui.apps.common` stellt Code bereit, der **sowohl** für Site A als auch für Website B erforderlich ist.
      + `ui.apps.site-a` stellt Code bereit, der für Site A erforderlich ist.
      + `ui.content.site-a` Bereitstellung von Inhalt und Konfiguration, die für Site A erforderlich sind
      + `ui.apps.site-b` stellt Code bereit, der für Website B erforderlich ist.
      + `ui.content.site-b` Bereitstellung von Inhalt und Konfiguration, die für Website B erforderlich sind

## Pakettypen {#package-types}

Die Pakete sind mit ihrem erklärten Pakettyp zu kennzeichnen.

+ Container-Pakete dürfen keine `packageType` Sets haben.
+ Code-Pakete (unveränderlich) müssen ihre `packageType` auf `application`.
+ Inhaltspakete (veränderlich) müssen ihre `packageType` auf `content`.

Weitere Informationen finden Sie in der Dokumentation [zum](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType) Apache Jackrabbit FileVault - Package Maven Plugin und dem [Konfigurationsfragment](#marking-packages-for-deployment-by-adoube-cloud-manager) FileVault Maven unten.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-package-types) unten.

## Markieren von Paketen für die Bereitstellung durch Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}

Adobe Cloud Manager sammelt standardmäßig alle Pakete, die vom Maven-Build erstellt wurden. Da jedoch das Containerpaket (`all`) das einzige Implementierungsartefakt ist, das alle Code- und Inhaltspakete enthält, muss sichergestellt werden, dass **nur** das Containerpaket (`all`) bereitgestellt wird. Dazu müssen andere Pakete, die der Maven-Build erstellt, mit der FileVault Content Package Maven Plug-In-Konfiguration von `<properties><cloudManagerTarget>none</cloudManageTarget></properties>` gekennzeichnet werden.

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
>Ein vollständiges Snippet finden Sie im Abschnitt [Repo Init Snippets](#snippet-repo-init) weiter unten.

## Repository-Strukturpaket {#repository-structure-package}

Codepakete müssen die Konfiguration des FileVault Maven-Plug-Ins so konfigurieren, dass auf eine `<repositoryStructurePackage>` Weise verwiesen wird, die die Richtigkeit struktureller Abhängigkeiten erzwingt (um sicherzustellen, dass ein Codepaket nicht über ein anderes installiert wird). Sie können Ihr eigenes Repository-Strukturpaket für Ihr Projekt [erstellen](repository-structure-package.md).

Dies ist **nur** für Code-Pakete erforderlich, d. h. für alle Pakete, die mit `<packageType>application</packageType>` gekennzeichnet sind.

Informationen zum Erstellen eines Repository-Strukturpakets für Ihre Anwendung finden Sie unter [Entwickeln eines Repository-Strukturpakets](repository-structure-package.md).

Beachten Sie, dass für Inhaltspakete (`<packageType>content</packageType>`) dieses Repository-Strukturpaket **nicht** erforderlich ist.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-repository-structure-package) unten.

## Einbetten von Unterpaketen in das Container-Paket{#embeddeds}

Inhalts- oder Codepakete werden in einen speziellen &quot;Side-Car&quot;-Ordner eingefügt und können für die Installation auf AEM-Autor, AEM-Veröffentlichung oder auf beide mithilfe der `<embeddeds>` Konfiguration des FileVault Maven-Plug-Ins ausgelegt werden. Beachten Sie, dass die `<subPackages>` Konfiguration nicht verwendet werden sollte.

Häufige Anwendungsfälle sind:

+ ACLs/Berechtigungen, die sich zwischen AEM-Autor- und AEM-Veröffentlichungsbenutzern unterscheiden
+ Konfigurationen, die dazu verwendet werden, Aktivitäten nur auf AEM Authoring zu unterstützen
+ Code wie Integrationen mit Back-Office-Systemen, die nur für die Ausführung mit AEM Authoring erforderlich sind

![Einbetten von Paketen](assets/embeddeds.png)

Für die Zielgruppe von AEM-Autor, AEM-Veröffentlichung oder beidem wird das Paket im `all` Container-Paket an einem speziellen Speicherort im folgenden Format eingebettet:

`/apps/<app-name>-packages/(content|application)/install(.author|.publish)?`

Unterbrechen der Ordnerstruktur:

+ Der Ordner der ersten Ebene **muss vorhanden sein** `/apps`.
+ Der Ordner auf der zweiten Ebene stellt die Anwendung dar, deren Ordnername nach dem `-packages` Fixieren festgelegt ist. Oft gibt es nur einen einzigen Ordner auf 2. Ebene, in den alle Unterpakete eingebettet sind. Es können jedoch beliebig viele Ordner auf 2. Ebene erstellt werden, um die logische Struktur der Anwendung am besten darzustellen:
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`
   >[!WARNING]
   >
   >Eingebettete Ordner mit Unterpaketen werden standardmäßig mit dem Suffix von `-packages` benannt. Dadurch wird sichergestellt, dass der Implementierungscode und die Inhaltspakete **nicht** im/in den Zielordner(n) einer Unterpaket-`/apps/<app-name>/...` bereitgestellt werden, was zu destruktivem und zyklischem Installationsverhalten führt.

+ Der Ordner der dritten Ebene muss entweder
   `application` oder `content` ermöglichen.
   + Der `application` Ordner enthält Codepakete
   + Der `content` Ordner golds content packagesDieser Ordnername muss den [Pakettypen](#package-types) der darin enthaltenen Pakete entsprechen.
+ Der Ordner der vierten Stufe enthält die Unterpakete und eine der folgenden Optionen muss darauf zutreffen:
   + `install` zur Installation **sowohl** auf AEM Authoring als auch auf AEM Publishing
   + `install.author` **nur** zur Installation auf AEM-Autor
   + `install.publish` um **nur** auf AEM zu installierenBeachten Sie, dass nur `install.author` und `install.publish` werden unterstützt. Andere Ausführungsmodi werden **nicht** unterstützt.

Eine Bereitstellung mit AEM Authoring- und Veröffentlichungsspezifischen Paketen könnte z. B. wie folgt aussehen:

+ `all` Container-Paket bettet die folgenden Pakete ein, um ein einzelnes Bereitstellungsartefakt zu erstellen
   + `ui.apps` eingebettet in `/apps/my-app-packages/application/install` stellt Code für AEM-Autor und AEM-Veröffentlichung bereit
   + `ui.apps.author` eingebettet in `/apps/my-app-packages/application/install.author` stellt Code nur für AEM-Autor bereit
   + `ui.content` eingebettet in `/apps/my-app-packages/content/install` Bereitstellung von Inhalt und Konfiguration für AEM-Autor und AEM-Veröffentlichung
   + `ui.content.publish` eingebettet in `/apps/my-app-packages/content/install.publish` Bereitstellung von Inhalt und Konfiguration nur für AEM-Veröffentlichung

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-embeddeds) unten.

### Filterdefinition des Container-Pakets {#container-package-filter-definition}

Aufgrund der Einbettung der Code- und Content-Unterpakete in das Container-Paket müssen die eingebetteten Zielgruppen-Pfade zu den Container-Projektpfaden hinzugefügt werden, `filter.xml` um sicherzustellen, dass die eingebetteten Pakete beim Erstellen im Container-Paket enthalten sind.

Fügen Sie einfach die `<filter root="/apps/<my-app>-packages"/>` Einträge für Ordner der zweiten Ebene hinzu, die zu bereitzustellende Unterpakete enthalten.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-container-package-filters) unten.

## Einbetten von Drittanbieter-Paketen {#embedding-3rd-party-packages}

Alle Pakete müssen über das öffentliche Maven-Artefaktrepository [von](https://repo.adobe.com/nexus/content/groups/public/com/adobe/) Adobe oder über ein öffentlich zugängliches Maven-Artefakt-Repository von Drittanbietern verfügbar sein.

Wenn sich die Drittanbieter-Pakete im **öffentlichen Maven-Artefakt-Repository von Adobe** befinden, ist keine weitere Konfiguration erforderlich, damit Adobe Cloud Manager die Artefakte auflösen kann.

Wenn sich die Pakete von Drittanbietern in einem **öffentlichen Maven-Artefakt-Repository von Drittanbietern** befinden, muss dieses Repository im Projekt-`pom.xml` registriert und nach der oben [beschriebenen](#embeddeds) Methode eingebettet werden. Wenn die Drittanbieteranwendung/der Drittanbieter-Connector sowohl Code- als auch Inhaltspakete erfordert, müssen alle Pakete in die richtigen Positionen im Container-Paket (`all`) eingebettet werden.

Das Hinzufügen von Maven-Abhängigkeiten erfolgt nach den üblichen Maven-Verfahren. Die Einbettung von Artefakten von Drittanbietern (Code- und Inhaltspaketen) wird oben [erläutert](#embedding-3rd-party-packages).

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-3rd-party-maven-repositories) unten.

## Paketabhängigkeiten zwischen den `ui.apps` von `ui.content` Paketen {#package-dependencies}

Um eine ordnungsgemäße Installation der Pakete sicherzustellen, wird empfohlen, Abhängigkeiten zwischen Paketen zu erstellen.

Die allgemeine Regel ist, dass Pakete mit veränderlichem Inhalt (`ui.content`) vom unveränderlichen Inhalt (`ui.apps`) abhängen sollten, der die Wiedergabe und Verwendung des veränderlichen Inhalts unterstützt.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-package-dependencies) unten.

Die allgemeinen Muster für Abhängigkeiten von Inhaltspaketen sind:

### Abhängigkeiten von einfachen Bereitstellungspaketen {#simple-deployment-package-dependencies}

Der einfache Fall legt fest, dass das `ui.content` veränderliche Inhaltspaket vom `ui.apps` unveränderlichen Codepaket abhängt.

+ `all` hat keine Abhängigkeiten
   + `ui.apps` hat keine Abhängigkeiten
   + `ui.content` hängt von `ui.apps`

### Abhängigkeiten von komplexen Bereitstellungspaketen {#complex-deploxment-package-dependencies}

Komplexe Bereitstellungen erweitern sich auf einfache Weise und stellen Abhängigkeiten zwischen den entsprechenden veränderlichen Inhalten und unveränderlichen Codepaketen ein. Abhängigkeiten können bei Bedarf auch zwischen unveränderlichen Codepaketen festgestellt werden.

+ `all` hat keine Abhängigkeiten
   + `ui.apps.common` hat keine Abhängigkeiten
   + `ui.apps.site-a` hängt von `ui.apps.common`
   + `ui.content.site-a` hängt von `ui.apps.site-a`
   + `ui.apps.site-b` hängt von `ui.apps.common`
   + `ui.content.site-b` hängt von `ui.apps.site-b`

## Lokale Entwicklung und Bereitstellung {#local-development-and-deployment}

Die in diesem Artikel beschriebenen Projektstrukturen und -organisationen sind mit AEM-Instanzen für die lokale Entwicklung **vollständig kompatibel** .

## POM-XML-Snippets {#pom-xml-snippets}

Im Folgenden finden Sie Maven- `pom.xml` Konfigurationssnippets, die zu Maven-Projekten hinzugefügt werden können, um sie an die oben genannten Empfehlungen anzupassen.

### Pakettypen {#xml-package-types}

Code- und Inhaltspakete, die als Unterpakete bereitgestellt werden, müssen je nachdem, was sie enthalten, einen Pakettyp für die **Anwendung** oder den **Inhalt** deklarieren.

#### Container-Pakettypen {#container-package-types}

Das Container- `all/pom.xml` Projekt **deklariert keine** `<packageType>`.

#### Code-Pakettypen (nicht mehr verwendbar) {#immutable-package-types}

Codepakete müssen ihren Wert `packageType` auf `application`.

In der `ui.apps/pom.xml`deklariert die `<packageType>application</packageType>` Build-Konfigurationsanleitung der `filevault-package-maven-plugin` Plug-In-Deklaration den Pakettyp.

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

#### Inhaltspakettypen (variabel) {#mutable-package-types}

Inhaltspakete müssen ihren Wert `packageType` auf `content`.

In der `ui.content/pom.xml`deklariert die `<packageType>content</packageType>` Build-Konfigurationsanweisung der `filevault-package-maven-plugin` Plug-In-Deklaration den Pakettyp.

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

### Markieren von Paketen für die Bereitstellung von Adobe Cloud Manager {#cloud-manager-target}

Fügen Sie in jedem Projekt, das ein Paket generiert, **mit Ausnahme** des Containerprojekts (`all`), `<cloudManagerTarget>none</cloudManagerTarget>` der `<properties>`-Konfiguration für die `filevault-package-maven-plugin`-Plug-in-Deklaration hinzu, um sicherzustellen, dass sie von Adobe Cloud Manager **nicht** bereitgestellt werden. Das Containerpaket (`all`) sollte das Einzelpaket sein, das über Cloud Manager bereitgestellt wird. Dadurch werden wiederum alle erforderlichen Code- und Inhaltspakete eingebettet.

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

Fügen Sie im `ui.apps/pom.xml` und allen anderen Elementen, `pom.xml` die ein Codepaket deklarieren (`<packageType>application</packageType>`), die folgende Repository-Struktur-Paketkonfiguration zum FileVault Maven-Plug-In hinzu. Sie können Ihr eigenes Repository-Strukturpaket für Ihr Projekt [erstellen](repository-structure-package.md).

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
              <artifactId>repository-structure-pkg</artifactId>
              <version>${project.version}</version>
          </repositoryStructurePackage>
        </repositoryStructurePackages>
      </configuration>
    </plugin>
    ...
```

### Einbetten von Unterpaketen in das Container-Paket {#xml-embeddeds}

Fügen Sie `all/pom.xml`der Plug-in-Deklaration die folgenden `<embeddeds>` Anweisungen hinzu `filevault-package-maven-plugin` . Denken Sie daran, **verwenden Sie nicht** die `<subPackages>` Konfiguration, da dies die Unterpakete in `/etc/packages` statt `/apps/my-app-packages/<application|content>/install(.author|.publish)?`.

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

Schließen Sie im `all`-Projekt-`filter.xml` (`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`) alle Ordner **ein** `-packages`, die Unterpakete enthalten, die bereitgestellt werden sollen:

```xml
<filter root="/apps/my-app-packages"/>
```

Wenn mehrere in den Zielgruppen von embeddeds verwendet `/apps/*-packages` werden, müssen sie alle hier aufgezählt werden.

### Maven-Repositorys von Drittanbietern {#xml-3rd-party-maven-repositories}

>[!WARNING]
> Durch das Hinzufügen von mehr Maven-Repositorys können die Maven-Buildzeiten verlängert werden, da zusätzliche Maven-Repositorys auf Deep-Threads überprüft werden.

Fügen Sie im Reaktorprojekt die erforderlichen Richtlinien für das öffentliche Maven-Repository `pom.xml`von Drittanbietern hinzu. Die vollständige `<repository>` Konfiguration sollte beim Repository Provider des Drittanbieters verfügbar sein.

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

### Paketabhängigkeiten zwischen den `ui.apps` von `ui.content` Paketen {#xml-package-dependencies}

Fügen Sie `ui.content/pom.xml`der Plug-in-Deklaration die folgenden `<dependencies>` Anweisungen hinzu `filevault-package-maven-plugin` .

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

### Bereinigen des Zielgruppe-Ordners des Container-Projekts {#xml-clean-container-package}

Fügen Sie im `all/pom.xml` Plug-in das `maven-clean-plugin` Plug-In hinzu, das den Ordner &quot;Zielgruppe&quot;vor einem Maven-Build bereinigt.

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
+ [FileVault Content Package Maven Plug-in](http://jackrabbit.apache.org/filevault-package-maven-plugin/)