---
title: Struktur von AEM-Projekten
description: Erfahren Sie, wie Sie Paketstrukturen für die Bereitstellung in Adobe Experience Manager Cloud Service definieren.
exl-id: 38f05723-5dad-417f-81ed-78a09880512a
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: tm+mt
source-wordcount: '2918'
ht-degree: 56%

---

# Struktur von AEM-Projekten

>[!TIP]
>
>Machen Sie sich mit der grundlegenden [Verwendung des AEM-Projektarchetyps](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) und dem [FileVault Content Maven-Plug-in](/help/implementing/developing/tools/maven-plugin.md) vertraut, da dieser Artikel auf diesen Erkenntnissen und Konzepten aufbaut.

In diesem Artikel werden die Änderungen erläutert, die erforderlich sind, damit Adobe Experience Manager Maven-Projekte AEM as a Cloud Service kompatibel sind, indem sichergestellt wird, dass sie die Aufteilung veränderlicher und unveränderlicher Inhalte berücksichtigen. Darüber hinaus werden Abhängigkeiten festgelegt, um nicht widersprüchliche, deterministische Implementierungen zu erstellen, und sie werden in einer bereitstellbaren Struktur zusammengefasst.

AEM Anwendungsbereitstellungen müssen aus einem einzigen AEM bestehen. Dieses Paket sollte wiederum Unterpakete enthalten, die alles enthalten, was die Anwendung benötigt, um zu funktionieren, einschließlich Code, Konfiguration und unterstützenden Grundlinien-Inhalten.

AEM erfordert eine Trennung von **Inhalt** und **Code**. Dies bedeutet, dass ein einzelnes Inhaltspaket **nicht** **sowohl** für `/apps` als auch für zur Laufzeit schreibbare Bereiche des Repositorys bereitstellen kann (z. B.`/content`, `/conf`, `/home` oder alles, was nicht `/apps` ist). Stattdessen muss die Anwendung Code und Inhalt in separaten Pakete für die Bereitstellung in AEM voneinander trennen.

Die in diesem Dokument beschriebene Paketstruktur ist mit lokalen Entwicklungsbereitstellungen **und** AEM Cloud Service-Bereitstellungen kompatibel.

>[!TIP]
>
>Die in diesem Dokument beschriebenen Konfigurationen werden von [AEM-Projektarchetyp 24 oder höher](https://github.com/adobe/aem-project-archetype/releases) bereitgestellt.

## Veränderliche und unveränderliche Bereiche des Repositorys {#mutable-vs-immutable}

Die `/apps` und `/libs` AEM **unveränderlich** weil sie nach dem Start (d. h. zur Laufzeit) nicht mehr geändert (erstellt, aktualisiert, gelöscht) werden können. Jeder Versuch, einen unveränderlichen Bereich zur Laufzeit zu ändern, schlägt fehl.

Alles andere im Repository, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`usw. sind alle **veränderlich** -Bereiche, d. h. sie können zur Laufzeit geändert werden.

>[!WARNING]
>
>Wie in früheren Versionen von AEM sollten `/libs` nicht geändert werden. Nur der AEM-Produkt-Code darf für `/libs` bereitstellen.

### Oak-Indizes {#oak-indexes}

Oak-Indizes (`/oak:index`) werden vom AEM as a Cloud Service Bereitstellungsprozess verwaltet. Der Grund dafür ist, dass Cloud Manager warten muss, bis ein neuer Index bereitgestellt und vollständig neu indiziert wird, bevor zum neuen Codebild gewechselt wird.

Aus diesem Grund müssen Oak-Indizes, obwohl sie zur Laufzeit veränderbar sind, als Code bereitgestellt werden, damit sie installiert werden können, bevor veränderbare Pakete installiert werden. Daher sind `/oak:index`-Konfigurationen Teil des Code-Pakets und nicht Teil des Inhaltspakets, [wie unten beschrieben](#recommended-package-structure).

>[!TIP]
>
>Weitere Informationen zur Indizierung in AEM as a Cloud Service finden Sie unter [Inhaltssuche und -indizierung](/help/operations/indexing.md).

## Empfohlene Paketstruktur {#recommended-package-structure}

![Experience Manager-Projektpaketstruktur](assets/content-package-organization.png)

Dieses Diagramm bietet einen Überblick über die empfohlene Projektstruktur und die empfohlenen Artefakte zur Paketbereitstellung.

Die empfohlene Bereitstellungsstruktur für Programme lautet wie folgt:

### Code-Pakete/OSGi-Pakete

+ Die Jar-Datei des OSGi-Pakets wird generiert und direkt in das gesamte Projekt eingebettet.

+ Das `ui.apps`-Paket enthält den ganzen bereitzustellenden Code und wird nur für `/apps` bereitgestellt. Zu den gebräuchlichen Elementen des `ui.apps`-Pakets gehören unter anderem:
   + [Komponentendefinitionen und HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de)-Skripte
      + `/apps/my-app/components`
   + JavaScript und CSS (über [Client-Bibliotheken](/help/implementing/developing/introduction/clientlibs.md))
      + `/apps/my-app/clientlibs`
   + [Überlagerungen](/help/implementing/developing/introduction/overlays.md) von `/libs`
      + `/apps/cq`, `/apps/dam/`, und so weiter.
   + Kontextabhängige Ausweichkonfigurationen
      + `/apps/settings`
   + ACLs (Berechtigungen)
      + Alle `rep:policy` für einen Pfad unter `/apps`
   + [Vorkompilierte Paket-Skripte](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/precompiled-bundled-scripts.html?lang=de)

>[!NOTE]
>
>Derselbe Code muss in allen Umgebungen bereitgestellt werden. Dieser Code gewährleistet ein Maß an Konfidenz, dass Validierungen in der Staging-Umgebung ebenfalls in Produktion sind. Weitere Informationen finden Sie im Abschnitt zu [Ausführungsmodi](/help/implementing/deploying/overview.md#runmodes).


### Inhaltspakete

+ Das `ui.content`-Paket enthält alle Inhalte und Konfigurationen. Das Inhaltspaket umfasst alle Knotendefinitionen, die nicht in den `ui.apps`- oder `ui.config`-Paketen enthalten sind, bzw. alles, was nicht in `/apps` oder `/oak:index` enthalten ist. Zu den gebräuchlichen Elementen des `ui.content`-Pakets gehören unter anderem:
   + Kontextabhängige Konfigurationen
      + `/conf`
   + Erforderliche, komplexe Inhaltsstrukturen (d. h. Erstellung von Inhalten, die auf in Repo Init definierten grundlegenden Inhaltsstrukturen aufbauen und diese erweitern).
      + `/content`, `/content/dam`, und so weiter.
   + Geregelte Tagging-Taxonomien
      + `/content/cq:tags`
   + Alte etc-Knoten (idealerweise migrieren Sie diese Knoten zu Nicht-/etc-Speicherorten)
      + `/etc`

### Container-Pakete

+ Die `all` -Paket ist ein Container-Paket, das NUR bereitstellbare Artefakte, die Jar-Datei des OSGi-Pakets, enthält. `ui.apps`, `ui.config`und `ui.content` Packages als Einbettung. Die `all` darf nicht **beliebiger Inhalt oder Code** von selbst, sondern delegieren alle Implementierungen an das Repository an seine Unterpakete oder Jar-Dateien des OSGi-Pakets.

  Pakete werden jetzt mit dem Maven eingeschlossen [Eingebettete Konfiguration des FileVault Package Maven-Plug-ins](#embeddeds)anstatt der `<subPackages>` Konfiguration.

  Bei komplexen Experience Manager-Bereitstellungen ist es möglicherweise wünschenswert, mehrere `ui.apps`, `ui.config`und `ui.content` Projekte/Pakete, die bestimmte Sites oder Mandanten in AEM darstellen. Wenn dies der Fall ist, stellen Sie sicher, dass die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt eingehalten wird und die erforderlichen Inhaltspakete und Jar-Dateien des OSGi-Pakets als Unterpakete in die `all` Container-Inhaltspaket.

  Beispielsweise könnte eine komplexe Struktur eines Inhaltspakets für die Bereitstellung wie folgt aussehen:

   + Inhaltspaket `all` bettet die folgenden Pakete ein, um ein einzelnes Bereitstellungsartefakt zu erstellen
      + `common.ui.apps` stellt Code bereit, der **sowohl** für Site A als auch für Site B erforderlich ist
      + `site-a.core` Jar-Datei des OSGi-Pakets, erforderlich für Site A
      + `site-a.ui.apps` stellt Code bereit, der für Site A erforderlich ist
      + `site-a.ui.config` stellt OSGi-Konfigurationen bereit, die für Site A erforderlich sind
      + `site-a.ui.content` stellt Inhalte und Konfigurationen bereit, die für Site A erforderlich sind
      + `site-b.core` Jar-Datei des OSGi-Pakets, erforderlich für Site B
      + `site-b.ui.apps` stellt Code bereit, der für Site B erforderlich ist
      + `site-b.ui.config` stellt OSGi-Konfigurationen bereit, die für Site B erforderlich sind
      + `site-b.ui.content` stellt Inhalte und Konfigurationen bereit, die für Site B erforderlich sind

+ Das `ui.config`-Paket enthält alle [OSGi-Konfigurationen](/help/implementing/deploying/configuring-osgi.md):
   + Gilt als Code und gehört zu OSGi-Bundles, enthält jedoch keine regulären Inhaltsknoten. Daher wird es als Container-Paket markiert
   + Organisatorischer Ordner mit Run-Modus-spezifischen OSGi-Konfigurationsdefinitionen
      + `/apps/my-app/osgiconfig`
   + Allgemeiner OSGi-Konfigurationsordner mit standardmäßigen OSGi-Konfigurationen, die für alle AEM as a Cloud Service-Bereitstellungsziele gelten
      + `/apps/my-app/osgiconfig/config`
   + Ausführungsmodusspezifische OSGi-Konfigurationsordner mit standardmäßigen OSGi-Konfigurationen, die für alle Ziel-AEM-as a Cloud Service Bereitstellungsziele gelten
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + Repo Init OSGi-Konfigurationsskripte
      + [Repo Init](#repo-init) ist die empfohlene Methode zum Bereitstellen (veränderlicher) Inhalte, die logischerweise Teil des AEM-Programms sind. Die Repo Init OSGi-Konfigurationen sollten wie oben beschrieben im entsprechenden `config.<runmode>`-Ordner platziert und zur Definition folgender Elemente verwendet werden:
         + Grundlegende Inhaltsstrukturen
         + Benutzer
         + Service-Benutzer
         + Gruppen
         + ACLs (Berechtigungen)

### Zusätzliche Anwendungspakete{#extra-application-packages}

Wenn andere AEM Projekte - die selbst aus ihren eigenen Code- und Inhaltspaketen bestehen - von der AEM-Implementierung verwendet werden, sollten ihre Container-Pakete in die `all` Paket.

Ein AEM Projekt, das zwei Anwendungen von Anbietern AEM, könnte beispielsweise wie folgt aussehen:

+ Inhaltspaket `all` bettet die folgenden Pakete ein, um ein einzelnes Bereitstellungsartefakt zu erstellen
   + `core` Jar-Datei des OSGi-Pakets, erforderlich für das AEM-Programm
   + `ui.apps` stellt Code bereit, der für das AEM-Programm erforderlich ist
   + `ui.config` stellt OSGi-Konfigurationen bereit, die für das AEM-Programm erforderlich sind
   + `ui.content` stellt Inhalte und Konfigurationen bereit, die für das AEM-Programm erforderlich sind
   + `vendor-x.all` stellt alle erforderlichen Elemente (Code und Inhalt) bereit, die für das Programm von Anbieter X benötigt werden
   + `vendor-y.all` stellt alle erforderlichen Elemente (Code und Inhalt) bereit, die für das Programm von Anbieter Y benötigt werden

## Pakettypen {#package-types}

Die Pakete sind mit ihrem deklarierten Pakettyp zu kennzeichnen. Mithilfe von Pakettypen lässt sich der Zweck und die Bereitstellung eines Pakets verdeutlichen.

+ Container-Pakete müssen ihren `packageType` auf `container` einstellen. Container-Pakete dürfen keine Standardknoten enthalten. Nur OSGi-Bundles, Konfigurationen und Unterpakete sind zulässig. Container in AEM as a Cloud Service dürfen keine [Installations-Hooks](https://jackrabbit.apache.org/filevault/installhooks.html) verwenden.
+ (Unveränderliche) Code-Pakete müssen `packageType` auf `application` setzen.
+ (Veränderliche) Inhaltspakete müssen `packageType` auf `content` setzen.


Weitere Informationen finden Sie in der [Dokumentation zu Apache Jackrabbit FileVault - Package Maven-Plug-in](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType), [Apache Jackrabbit-Pakettypen](https://jackrabbit.apache.org/filevault/packagetypes.html) und dem [Konfigurations-Snippet für FileVault Mavent](#marking-packages-for-deployment-by-adoube-cloud-manager) unten.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-package-types) unten.

## Markieren von Paketen für die Bereitstellung durch Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}

Standardmäßig sammelt Adobe Cloud Manager alle vom Maven-Build erstellten Pakete. Da jedoch der Container (`all`)-Paket ist das einzige Implementierungsartefakt, das alle Code- und Inhaltspakete enthält. Stellen Sie sicher, dass **only** der Behälter (`all`) bereitgestellt. Um dies sicherzustellen, müssen andere Pakete, die der Maven-Build generiert, mit der FileVault Content Package Maven Plug-in-Konfiguration von `<properties><cloudManagerTarget>none</cloudManageTarget></properties>` gekennzeichnet werden.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#pom-xml-snippets) unten.

## Repo Init{#repo-init}

Repo Init enthält Anweisungen oder Skripte, die JCR-Strukturen definieren, von allgemeinen Knotenstrukturen wie Ordnerbäumen bis hin zu Benutzern, Dienstbenutzern, Gruppen und ACL-Definitionen.

Die Hauptvorteile von Repo Init sind, dass sie implizite Berechtigungen zum Ausführen aller Aktionen haben, die von ihren Skripten definiert werden. Außerdem werden solche Skripte frühzeitig im Bereitstellungslebenszyklus aufgerufen, um sicherzustellen, dass alle erforderlichen JCR-Strukturen vorhanden sind, bis der Zeitcode ausgeführt wird.

Während Repo Init-Skripte selbst als Skripte im `ui.config`-Projekt vorhanden sind, können und sollten sie zum Definieren der folgenden veränderbaren Strukturen verwendet werden:

+ Grundlegende Inhaltsstrukturen
+ Service-Benutzer
+ Benutzer
+ Gruppen
+ ACLs

Repo Init-Skripte werden als `scripts` Einträge von `RepositoryInitializer` OSGi-Werkskonfigurationen. Daher können sie implizit vom Ausführungsmodus angesprochen werden, wodurch Unterschiede zwischen den Repo Init-Skripten der AEM-Autoren- und AEM-Veröffentlichungsdienste oder sogar zwischen Umgebungen (Entwicklung, Staging und Produktion) berücksichtigt werden.

Repo Init OSGi-Konfigurationen werden am besten im [`.config` OSGi-Konfigurationsformat](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1) geschrieben, da es mehrere Zeilen unterstützt. Dies stellt eine Ausnahme bei den Best Practices dar, [`.cfg.json` zur Definition von OSGi-Konfigurationen](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1) zu verwenden.

Beim Definieren von Benutzern und Gruppen werden nur Gruppen als Teil der Anwendung und als integraler Bestandteil ihrer Funktion betrachtet. Sie definieren Organisationsbenutzer und -gruppen weiterhin zur Laufzeit in AEM. Wenn beispielsweise ein benutzerdefinierter Workflow einer benannten Gruppe Arbeit zuweist, definieren Sie diese Gruppe über Repo Init in der AEM. Wenn die Gruppierung jedoch nur organisatorisch ist, z. B. &quot;Wendy&#39;s Team&quot;und &quot;Sean&#39;s Team&quot;, sind diese Gruppen am besten zur Laufzeit in AEM definiert und verwaltet.

>[!TIP]
>
>Repo Init-Skripte *must* im Inline-Modus definiert werden `scripts` oder das `references` -Konfiguration funktioniert nicht.

Das vollständige Vokabular für Repo Init-Skripte ist in der [Apache Sling Repo Init-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language) verfügbar.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [Repo Init-Snippets](#snippet-repo-init) unten.

## Repository-Strukturpaket {#repository-structure-package}

Code-Pakete müssen die Konfiguration des FileVault Maven-Plug-ins so konfigurieren, dass sie auf eine `<repositoryStructurePackage>` , die die Richtigkeit struktureller Abhängigkeiten erzwingt (um sicherzustellen, dass ein Code-Paket nicht über ein anderes installiert wird). Sie können [Ihr eigenes Repository-Strukturpaket für Ihr Projekt erstellen](repository-structure-package.md).

**Nur erforderlich** für Code-Pakete, d. h. alle Pakete, die mit `<packageType>application</packageType>`.

Informationen zum Erstellen eines Repository-Strukturpakets für Ihr Programm finden Sie unter [Entwickeln eines Repository-Strukturpakets](repository-structure-package.md).

Inhaltspakete (`<packageType>content</packageType>`) **nicht** dieses Repository-Strukturpaket benötigen.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-repository-structure-package) unten.

## Einbetten von Unterpaketen in das Container-Paket{#embeddeds}

Inhalts- oder Code-Pakete werden in einem speziellen „Side-Car“-Ordner abgelegt und können mithilfe der `<embeddeds>`-Konfiguration des FileVault Maven-Plug-ins entweder auf AEM Autor, AEM Publish oder beiden installiert werden. Verwenden Sie nicht das `<subPackages>` Konfiguration.

Häufige Anwendungsfälle sind:

+ ACLs/Berechtigungen, die sich zwischen AEM Author- und AEM Publish-Benutzern unterscheiden
+ Konfigurationen, die nur zur Unterstützung von Aktivitäten in AEM Author verwendet werden
+ Code, wie z.B. Integrationen mit Backoffice-Systemen, die nur auf in AEM Author laufen müssen

![Einbetten von Paketen](assets/embeddeds.png)

Um AEM Autor als Ziel festzulegen, wird AEM veröffentlicht oder beides wird in das Paket eingebettet `all` Container-Paket an einem bestimmten Ordnerspeicherort im folgenden Format:

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

Aufschlüsseln dieser Ordnerstruktur:

+ Der Ordner der ersten Ebene **muss** `/apps` sein.
+ Der Ordner der zweiten Ebene stellt das Programm dar, wobei `-packages` an den Ordnernamen angehängt wird. Häufig ist nur ein einzelner Ordner der zweiten Ebene vorhanden, in den alle Unterpakete eingebettet sind. Es können jedoch beliebig viele Ordner der zweiten Ebene erstellt werden, um die logische Struktur der Anwendung am besten darzustellen:
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`

  >[!WARNING]
  >
  >Eingebettete Ordner mit Unterpaketen werden standardmäßig mit dem Suffix von `-packages`. Diese Benennung stellt sicher, dass der Bereitstellungscode und die Inhaltspakete **not** die Zielordner aller Unterpakete bereitgestellt haben `/apps/<app-name>/...`  was zu destruktivem und zyklischem Installationsverhalten führt.

+ Der Ordner der dritten Ebene muss
  `application`, `content` oder `container`
   + Der `application`-Ordner enthält Code-Pakete
   + Der `content`-Ordner enthält Inhaltspakete
   + Der `container`-Ordner enthält alle [zusätzlichen Programmpakete](#extra-application-packages), die ggf. im AEM-Programm enthalten sind.
Dieser Ordnername entspricht dem [Pakettypen](#package-types) der Pakete, die es enthält.
+ Der Ordner der vierten Ebene enthält die Unterpakete und muss einer der folgenden sein:
   + `install` installieren Sie auf **both** AEM der Autoren- und AEM Veröffentlichungsinstanz
   + `install.author` installieren **only** AEM Autor
   + `install.publish` installieren **only** Nur AEM veröffentlichen `install.author` und `install.publish` werden unterstützt. Andere Ausführungsmodi werden **nicht** unterstützt.

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

Aufgrund der Einbettung von Code- und Inhalts-Unterpaketen in das Container-Paket müssen die eingebetteten Zielpfade zum Container-Projekt hinzugefügt werden `filter.xml`. Dadurch wird sichergestellt, dass die eingebetteten Pakete beim Erstellen im Container-Paket enthalten sind.

Fügen Sie einfach die `<filter root="/apps/<my-app>-packages"/>` Einträge für alle Ordner der zweiten Ebene, die zu bereitzustellende Unterpakete enthalten.

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-container-package-filters) unten.

## Einbetten von Drittanbieter-Paketen {#embedding-3rd-party-packages}

Alle Packages müssen über die [Öffentliches Maven-Artefakt-Repository der Adobe](https://repo1.maven.org/maven2/com/adobe/) oder ein öffentlich zugängliches, referenzierbares Maven-Artefakt-Repository von Drittanbietern.

Wenn sich die Pakete von Drittanbietern in **Öffentliches Maven-Artefakt-Repository der Adobe**, ist keine weitere Konfiguration erforderlich, damit Adobe Cloud Manager die Artefakte auflösen kann.

Wenn sich die Pakete von Drittanbietern in einer **öffentliches Maven-Artefakt-Repository von Drittanbietern**, muss dieses Repository im Projekt-Repository registriert sein. `pom.xml` und eingebettet nach der Methode [oben](#embeddeds).

Anwendungen/Connectoren von Drittanbietern sollten mit ihrer eingebettet werden `all` als Container im Container Ihres Projekts (`all`).

Das Hinzufügen von Maven-Abhängigkeiten folgt den standardmäßigen Maven-Verfahren, und das Einbetten von Artefakten von Drittanbietern (Code- und Inhaltspakete) erfolgt [oben](#embedding-3rd-party-packages).

>[!TIP]
>
>Ein vollständiges Snippet finden Sie im Abschnitt [POM XML-Snippets](#xml-3rd-party-maven-repositories) unten.

## Paketabhängigkeiten zwischen den `ui.apps` von `ui.content`-Paketen {#package-dependencies}

Um eine ordnungsgemäße Installation der Pakete sicherzustellen, wird empfohlen, Abhängigkeiten zwischen Paketen zu erstellen.

Die allgemeine Regel ist, dass Pakete mit veränderlichem Inhalt (`ui.content`) vom unveränderlichen Code (`ui.apps`) abhängen sollten, der die Wiedergabe und Verwendung des veränderlichen Inhalts unterstützt.

Eine wichtige Ausnahme von dieser allgemeinen Regel ist, wenn das unveränderliche Code-Paket (`ui.apps` oder jedes andere) __nur__ OSGi-Bundles enthält. Ist dies der Fall sollte kein AEM-Paket eine Abhängigkeit angeben. Der Grund dafür ist, dass unveränderliche Code-Pakete __only__ enthalten OSGi-Bundles, sind nicht bei AEM registriert [Package Manager](/help/implementing/developing/tools/package-manager.md). Daher hat jedes AEM Paket, das davon abhängig ist, eine nicht zufrieden stellende Abhängigkeit und kann nicht installiert werden.

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

Komplexe Bereitstellungen gehen über den einfachen Fall hinaus und legen Abhängigkeiten zwischen den entsprechenden veränderbaren Inhalten und unveränderlichen Code-Paketen fest. Abhängigkeiten können bei Bedarf auch zwischen unveränderlichen Code-Paketen festgelegt werden.

+ `all` hat keine Abhängigkeiten
   + `common.ui.apps.common` hat keine Abhängigkeiten
   + `site-a.ui.apps` hängt von `common.ui.apps` ab
   + `site-a.ui.content` hängt von `site-a.ui.apps` ab
   + `site-b.ui.apps` hängt von `common.ui.apps` ab
   + `site-b.ui.content` hängt von `site-b.ui.apps` ab

## Lokale Entwicklung und Bereitstellung {#local-development-and-deployment}

Die in diesem Artikel beschriebenen Projektstrukturen und -organisationen sind mit AEM-Instanzen für die lokale Entwicklung **vollständig kompatibel**.

## POM-XML-Snippets {#pom-xml-snippets}

Im Folgenden finden Sie Maven `pom.xml`-Konfigurations-Snippets, die zu Maven-Projekten hinzugefügt werden können, um sie an die oben genannten Empfehlungen anzupassen.

### Pakettypen {#xml-package-types}

Code- und Inhaltspakete, die als Unterpakete bereitgestellt werden, müssen einen Pakettyp deklarieren von **application** oder **content**, je nachdem, was sie enthalten.

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
        <name>my-app.ui.apps</name>
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
        <name>my-app.ui.content</name>
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

### Repo Init{#snippet-repo-init}

Repo Init-Skripte, die die Repo Init-Skripte enthalten, werden in der `RepositoryInitializer`-OSGi-Werkskonfiguration über die `scripts`-Eigenschaft definiert. Da diese Skripte in OSGi-Konfigurationen definiert sind, können sie mithilfe des üblichen `../config.<runmode>` Ordnersemantik.

Da es sich bei Skripten normalerweise um mehrzeilige Deklarationen handelt, ist es einfacher, sie in der `.config` -Datei anstatt der JSON-basierten `.cfg.json` Format.

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

Die `scripts`-OSGi-Eigenschaft enthält Anweisungen, die in der [Repo Init-Sprache von Apache Sling](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language) definiert sind.

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

Fügen Sie in `all/pom.xml` der `filevault-package-maven-plugin`-Plug-in-Deklaration die folgenden `<embeddeds>`-Anweisungen hinzu. Denken Sie daran, **nicht** die `<subPackages>` Konfiguration. Der Grund dafür ist, dass es die Unterpakete in `/etc/packages` anstelle von `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?`.

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

          <!-- OSGi Bundle Jar file that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.core</artifactId>
              <type>jar</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

          <!-- Code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

           <!-- OSGi configuration code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.config</artifactId>
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

          <!-- Include any other extra packages  -->
          <embedded>
              <groupId>com.vendor.x</groupId>
              <artifactId>vendor.plug-in.all</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/container/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

### Filterdefinition des Container-Pakets {#xml-container-package-filters}

Im `all` des Projekts `filter.xml` (`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`), **include** any `-packages` Ordner, die zu bereitzustellende Unterpakete enthalten:

```xml
<filter root="/apps/my-app-packages"/>
```

Wenn mehrere `/apps/*-packages` in den eingebetteten Zielen verwendet werden, müssen sie hier alle aufgezählt werden.

### Maven-Repositorys von Drittanbietern {#xml-3rd-party-maven-repositories}

>[!WARNING]
>
>Das Hinzufügen weiterer Maven-Repositorys kann die Maven-Build-Zeiten verlängern, da zusätzliche Maven-Repositorys auf Abhängigkeiten überprüft werden.

Im Reaktorprojekt `pom.xml`, fügen Sie alle erforderlichen öffentlichen Maven-Repository-Anweisungen von Drittanbietern hinzu. Die vollständige `<repository>` -Konfiguration sollte vom Repository-Provider eines Drittanbieters verfügbar sein.

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

Im `all/pom.xml`, fügen Sie die `maven-clean-plugin` -Plug-in, das das Zielverzeichnis vor einem Maven-Build bereinigt.

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

+ [Verwalten von Paketen mithilfe von Maven](/help/implementing/developing/tools/maven-plugin.md)
+ [FileVault Content Package Maven-Plug-in](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
