---
title: 'AEM Project Repository Structure Package  '
description: Für Adobe Experience Manager als Cloud Service Maven-Projekte ist eine Definition des Unterpakets "Repository-Struktur"erforderlich, deren einziger Zweck darin besteht, die Wurzeln des JCR-Repositorys zu definieren, in denen die Code-Unterpakete des Projekts bereitgestellt werden.
translation-type: tm+mt
source-git-commit: fb398147c5a2635f58250b8de886159b4ace2943

---


# AEM Project Repository Structure Package

Für erstellte Projekte für Adobe Experience Manager als Cloud-Dienst ist eine Definition des Unterpakets &quot;Repository-Struktur&quot;erforderlich, deren einziger Zweck darin besteht, die Wurzeln des JCR-Repositorys zu definieren, in denen die Code-Unterpakete des Projekts bereitgestellt werden. Dadurch wird sichergestellt, dass die Installation von Paketen in Experience Manager erfolgt, da ein Cloud-Dienst automatisch nach JCR-Ressourcenabhängigkeiten geordnet wird. Fehlende Abhängigkeiten können zu Szenarien führen, in denen Unterstrukturen vor ihren übergeordneten Strukturen installiert und daher unerwartet entfernt werden, was die Bereitstellung unterbricht.

Wenn Ihr Codepaket an einem Speicherort bereitgestellt wird, der **nicht vom Codepaket abgedeckt** wird, müssen alle übergeordneten Ressourcen (JCR-Ressourcen näher am JCR-Stamm) im Repository-Strukturpaket aufgezählt werden, um diese Abhängigkeiten zu schaffen.

![Repository-Strukturpaket](./assets/repository-structure-packages.png)

Das Repository-Strukturpaket definiert den erwarteten, allgemeinen Zustand, in `/apps` dem der Paket-Validator Bereiche &quot;sicher vor potenziellen Konflikten&quot;als Standardwurzeln ermittelt.

Die typischsten Pfade, die in das Repository-Strukturpaket aufgenommen werden sollen, sind:

+ `/apps` der ein vom System bereitgestellter Knoten ist
+ `/apps/cq/...`, `/apps/dam/...`, `/apps/wcm/...`und `/apps/sling/...` die allgemeine Überlagerungen bereitstellen `/libs`.
+ `/apps/settings` der freigegebene kontextabhängige Konfigurationsstammpfad ist

Beachten Sie, dass dieses Unterpaket **keinen Inhalt hat** und nur aus einer `pom.xml` Definition der Filterwurzeln besteht.

## Erstellen des Repository-Strukturpakets

Um ein Repository-Strukturpaket für Ihr Maven-Projekt zu erstellen, erstellen Sie ein neues leeres Maven-Unterprojekt mit dem folgenden `pom.xml`und aktualisieren Sie die Projektmetadaten entsprechend Ihrem übergeordneten Maven-Projekt.

Aktualisieren Sie `<filters>` die, um alle JCR-Repository-Pfade einzuschließen, in denen Ihre Codepakete bereitgestellt werden.

Stellen Sie sicher, dass Sie dieses neue Maven-Unterprojekt zur `<modules>` Liste der übergeordneten Projekte hinzufügen.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- ====================================================================== -->
    <!-- P A R E N T  P R O J E C T  D E S C R I P T I O N                      -->
    <!-- ====================================================================== -->
    <parent>
        <groupId>com.my-company</groupId>
        <artifactId>my-app</artifactId>
        <version>x.x.x</version>
        <relativePath>../pom.xml</relativePath>
    </parent>

    <!-- ====================================================================== -->
    <!-- P R O J E C T  D E S C R I P T I O N                                   -->
    <!-- ====================================================================== -->
    <artifactId>ui.apps.structure</artifactId>
    <packaging>content-package</packaging>
    <name>UI Apps Structure - Repository Structure Package for /apps</name>

    <description>
        Empty package that defines the structure of the Adobe Experience Manager repository the code packages in this project deploy into.
        Any roots in the code packages of this project should have their parent enumerated in the filters list below.
    </description>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.jackrabbit</groupId>
                <artifactId>filevault-package-maven-plugin</artifactId>
                <extensions>true</extensions>
                <properties>
                    <!-- Set Cloud Manager Target to none, else this package will be deployed and remove all defined filter roots -->
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
                <configuration>
                    <properties>
                        <!-- Set Cloud Manager Target to none, else this package will be deployed and remove all defined filter roots -->
                        <cloudManagerTarget>none</cloudManagerTarget>
                    </properties>
                    <filters>

                        <!-- /apps root -->
                        <filter><root>/apps</root></filter>

                        <!--
                        Examples of complex roots


                        Overlays of /libs typically require defining the overlayed structure, at each level here.

                        For example, adding a new section to the main AEM Tools navigation, necessitates the following rules:

                        <filter><root>/apps/cq</root></filter>
                        <filter><root>/apps/cq/core</root></filter>
                        <filter><root>/apps/cq/core/content</root></filter>
                        <filter><root>/apps/cq/core/content/nav/</root></filter>
                        <filter><root>/apps/cq/core/content/nav/tools</root></filter>


                        Any /apps level Context-aware configurations need to enumerated here. 
                        
                        For example, providing email templates under `/apps/settings/notification-templates/com.day.cq.replication` necessitates the following rules:

                        <filter><root>/apps/settings</root></filter>
                        <filter><root>/apps/settings/notification-templates</root></filter>
                        <filter><root>/apps/settings/notification-templates/com.day.cq.replication</root></filter>
                        -->

                    </filters>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

## Referenzieren des Repository Structure-Pakets

Um das Repository-Strukturpaket zu verwenden, referenzieren Sie es über das gesamte Codepaket (die Unterpakete, die für `/apps`) Maven-Projekte über das FileVault-Inhaltspaket Maven-Plug-Ins- `<repositoryStructurePackage>` Konfiguration.

Fügen Sie im `ui.apps/pom.xml`und anderen Code-Paketen `pom.xml`einen Verweis auf die Repository-Strukturpaket-Konfiguration des Projekts (#repository-structure-package) zum FileVault-Paket Maven-Plug-In hinzu.

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
</build>
<dependencies>
    <!-- Add the dependency for the repository structure package so it resolves -->
    <dependency>
        <groupId>${project.groupId}</groupId>
        <artifactId>ui.apps.structure</artifactId>
        <version>${project.version}</version>
        <type>zip</type>
    </dependency>
    ...
</dependencies>
```

## Anwendungsfall für Multi-Code-Pakete

Weniger häufig verwendete und komplexere Anwendungsfälle unterstützen die Bereitstellung mehrerer Codepakete, die in denselben Bereichen des JCR-Repositorys installiert werden.

Beispiel:

+ Codepaket A wird in `/apps/a`
+ Codepaket B wird bereitgestellt in `/apps/a/b`

Wenn keine Abhängigkeit auf Paketebene aus dem Code-Paket B auf dem Code-Paket A festgestellt wird, kann Codepaket B zuerst in bereitgestellt werden, gefolgt von `/apps/a`dem Code-Paket B, in dem `/apps/a`die Bereitstellung erfolgt, was zum Entfernen der zuvor installierten Pakete führt `/apps/a/b`.

In diesem Fall:

+ Codepaket A sollte eine `<repositoryStructurePackage>` Beschreibung des Repository-Strukturpakets des Projekts (für das ein Filter verwendet werden sollte) enthalten `/apps`.
+ Code-Paket B sollte ein `<repositoryStructurePackage>` auf Code-Paket A definieren, da das Codepaket B in dem von Codepaket A freigegebenen Speicherplatz bereitgestellt wird.

## Fehler und Debugging

Wenn die Repository-Strukturpakete nicht korrekt eingerichtet sind, wird beim Maven-Build ein Fehler gemeldet:

```
1 error(s) detected during dependency analysis.
Filter root's ancestor '/apps/some/path' is not covered by any of the specified dependencies.
```

Dies zeigt an, dass das Umbruchcode-Paket keine Listen `<repositoryStructurePackage>` in seiner Filter-Liste enthält `/apps/some/path` .

## Zusätzliche Ressourcen

+ [FileVault Content Package Maven Plug-in](http://jackrabbit.apache.org/filevault-package-maven-plugin/)
