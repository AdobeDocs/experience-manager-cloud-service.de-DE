---
title: Details zum Einrichten des Projekts
description: Details zum Einrichten des Projekts - Cloud Services
translation-type: tm+mt
source-git-commit: 17971405c174e2559879335ade437c5fec2868a3
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 77%

---


# Einrichten des Projekts {#project-setup-details}

## Ändern der Projekteinstellungen {#modifying-project-setup-details}

Damit vorhandene AEM-Projekte erfolgreich in Cloud Manager erstellt und bereitgestellt werden können, müssen einige grundlegende Regeln berücksichtigt werden:

* Projekte müssen mit Apache Maven erstellt werden.
* Im Stammverzeichnis des Git-Repositorys muss eine Datei *pom.xml* vorhanden sein. This *pom.xml* file can refer to as many sub-modules (which in turn may have other sub-modules, etc.) wie nötig.

* Sie können Verweise auf weitere Maven-Artefakt-Repositorys in Ihren *pom.xml*-Dateien hinzufügen. Der Zugriff auf [kennwortgeschützte Artefakt-Repositorys](#password-protected-maven-repositories) wird bei entsprechender Konfiguration unterstützt. Allerdings wird der Zugriff auf netzwerkgeschützte Artefakte nicht unterstützt.
* Bereitstellbare Inhaltspakete werden erkannt, wenn Sie nach Inhaltspaketen im *ZIP*-Format suchen, die in einem Verzeichnis mit dem Namen *target* enthalten sind. Eine beliebige Anzahl von Untermodulen kann Inhaltspakete erzeugen.

* Bereitstellbare Dispatcher-Artefakte werden erkannt, wenn Sie nach *ZIP*-Dateien (ebenfalls in einem Verzeichnis namens *target*) suchen, die Verzeichnisse mit den Namen *conf* und *conf.d* enthalten.

* Wenn mehrere Inhaltspakete vorhanden sind, ist die Reihenfolge der Paketbereitstellungen nicht garantiert. Wenn eine bestimmte Reihenfolge benötigt wird, können die Abhängigkeiten des Inhaltspakets zum Definieren der Reihenfolge verwendet werden. Pakete können bei der Bereitstellung [übersprungen](#skipping-content-packages) werden.


## Aktivieren von Maven-Profilen in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In einigen wenigen Fällen müssen Sie den Build-Prozess möglicherweise etwas anders gestalten, wenn er in Cloud Manager und auf Entwickler-Workstations ausgeführt wird. In diesen Fällen können Sie mit [Maven-Profilen](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) definieren, wie der Build in verschiedenen Umgebungen (einschließlich Cloud Manager) abweichen soll.

Die Aktivierung eines Maven-Profils in der Cloud Manager-Build-Umgebung sollte über die oben beschriebene Umgebungsvariable CM_BUILD erfolgen. Umgekehrt sollte ein Profil, das nur außerhalb der Cloud Manager-Build-Umgebung verwendet werden soll, ausgeführt werden, indem nach dem Fehlen dieser Variablen gesucht wird.

Wenn zum Beispiel eine einfache Nachricht nur dann ausgegeben werden soll, wenn der Build innerhalb von Cloud Manager ausgeführt wird, verwenden Sie Folgendes:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Um dieses Profil auf einer Entwickler-Workstation zu testen, können Sie es entweder in der Befehlszeile (mit `-PcmBuild`) oder in der integrierten Entwicklungsumgebung (IDE) aktivieren.

Wenn zum Beispiel eine einfache Nachricht nur dann ausgegeben werden soll, wenn der Build außerhalb von Cloud Manager ausgeführt wird, verwenden Sie Folgendes:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Unterstützung für kennwortgeschütztes Maven-Repository {#password-protected-maven-repositories}

>[!NOTE]
>Artefakte aus einem kennwortgeschützten Maven-Repository sollten nur sehr vorsichtig verwendet werden, da Code, der über diesen Mechanismus bereitgestellt wird, derzeit nicht über die Qualitätsdaten von Cloud Manager ausgeführt wird. Daher sollte es nur in seltenen Fällen und für Code, der nicht an AEM gebunden ist, verwendet werden. Es wird empfohlen, neben der Binärdatei auch die Java-Quellen sowie den gesamten Projektquellcode bereitzustellen.

Um ein kennwortgeschütztes Maven-Repository aus Cloud Manager zu verwenden, geben Sie das Kennwort (und optional den Benutzernamen) als geheime [Pipeline-Variable](#pipeline-variables) an und verweisen Sie dann in einer Datei im git-Repository mit dem Namen `.cloudmanager/maven/settings.xml` auf dieses Geheimnis. Diese Datei folgt dem Schema der [Maven-Einstellungsdatei](https://maven.apache.org/settings.html). Wenn der Build-Vorgang von Cloud Manager gestartet wird, wird das `<servers>`-Element in dieser Datei mit der von Cloud Manager bereitgestellten `settings.xml`-Standarddatei zusammengeführt. Server-IDs, die mit `adobe` und `cloud-manager` beginnen, gelten als reserviert und sollten nicht von kundenspezifischen Servern verwendet werden. Server-IDs, die **nicht** mit eine, dieser Praefice oder der Standard-ID `central` übereinstimmen, werden vom Cloud Manager niemals gespiegelt. Wenn diese Datei vorhanden ist, wird die Server-ID von innerhalb eines `<repository>`- und/oder `<pluginRepository>`-Elements in der `pom.xml`-Datei referenziert. Im Allgemeinen wären diese `<repository>`- und/oder `<pluginRepository>`-Elemente in einem [Cloud Manager-spezifischen Profil](#activating-maven-profiles-in-cloud-manager) enthalten, auch wenn dies nicht unbedingt erforderlich ist.

Beispiel: Das Repository befindet sich unter https://repository.myco.com/maven2, der von Cloud Manager zu verwendende Benutzername lautet `cloudmanager` und das Kennwort lautet `secretword`.

Legen Sie zunächst in der Pipeline das Kennwort als geheim fest:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

Verweisen Sie anschließend aus der `.cloudmanager/maven/settings.xml`-Datei darauf:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

Verweisen Sie schließlich auf die Server-ID in der `pom.xml`-Datei:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### Bereitstellen von Quellen {#deploying-sources}

Es empfiehlt sich, die Java-Quellen zusammen mit der Binärdatei in einem Maven-Repository bereitzustellen.

Konfigurieren Sie das maven-source-Plugin in Ihrem Projekt:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### Bereitstellen von Projektquellen {#deploying-project-sources}

Es ist eine gute Praxis, die gesamte Projektquelle zusammen mit der Binärdatei in einem Maven-Repository bereitzustellen - dies ermöglicht es, das genaue Artefakt neu zu erstellen.

Konfigurieren Sie das Plugin maven-assembly in Ihrem Projekt:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## Überspringen von Inhaltspaketen {#skipping-content-packages}

In Cloud Manager können Builds eine beliebige Anzahl von Inhaltspaketen generieren.
Aus vielerlei Gründen kann es sinnvoll sein, ein Inhaltspaket zu erstellen, es jedoch nicht bereitzustellen. Dies kann nützlich sein, etwa für Inhaltspakete, die nur zum Testen erstellt wurden, oder für Pakete, die in einem anderen Schritt im Build-Prozess (also als Unterpaket eines anderen Pakets) neu verpackt werden.

Um diese Szenarien zu berücksichtigen, sucht Cloud Manager in den Eigenschaften erstellter Inhaltspakete nach einer Eigenschaft namens ***cloudManagerTarget***. Wenn diese Eigenschaft auf „Ohne“ festgelegt ist, wird das Paket übersprungen und nicht bereitgestellt. Der Mechanismus zum Festlegen dieser Eigenschaft hängt davon ab, wie der Build das Inhaltspaket erzeugt. Mit dem filevault-maven-Plugin würden Sie beispielsweise das Plugin wie folgt konfigurieren:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Mit dem content-package-maven-Plugin ist es ähnlich:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```
