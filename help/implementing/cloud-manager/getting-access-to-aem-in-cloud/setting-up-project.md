---
title: Projekt-Setup
description: Erfahren Sie, wie AEM Projekte mit Maven erstellt werden und welche Standards Sie bei der Erstellung Ihres eigenen Projekts einhalten müssen.
exl-id: 76af0171-8ed5-4fc7-b5d5-7da5a1a06fa8
source-git-commit: 4b2ea300f61ad7d1218a984f7238365c5b170a8e
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 100%

---

# Projekt-Setup {#project-setup}

Erfahren Sie, wie AEM Projekte mit Maven erstellt werden und welche Standards Sie bei der Erstellung Ihres eigenen Projekts einhalten müssen.

## Einzelheiten der Projekteinstellung {#project-setup-details}

Damit AEM-Projekte erfolgreich mit Cloud Manager erstellt und bereitgestellt werden können, müssen einige grundlegende Regeln berücksichtigt werden:

* Projekte müssen mit [Apache Maven](https://maven.apache.org) erstellt werden.
* Im Stammverzeichnis des Git-Repositorys muss eine `pom.xml`-Datei vorhanden sein. Diese `pom.xml`-Datei kann ggf. auf beliebig viele Untermodule verweisen (die wiederum weitere Untermodule umfassen usw.) wie nötig.
* Sie können Verweise auf weitere Maven-Artefakt-Repositorys in Ihren `pom.xml`-Dateien hinzufügen.
   * Der Zugriff auf [kennwortgeschützte Artefakt-Repositorys](#password-protected-maven-repositories) wird bei entsprechender Konfiguration unterstützt. Allerdings wird der Zugriff auf netzwerkgeschützte Artefakte nicht unterstützt.
* Bereitstellbare Inhaltspakete werden erkannt, wenn Sie nach Inhaltspaketen im `.zip`-Format suchen, die in einem Verzeichnis namens `target` enthalten sind.
   * Eine beliebige Anzahl von Untermodulen kann Inhaltspakete produzieren.
* Bereitstellbare Dispatcher-Artefakte werden erkannt, wenn Sie nach `.zip`-Dateien (ebenfalls in einem Verzeichnis namens `target`) suchen, die Verzeichnisse mit den Namen `conf` und `conf.d` enthalten.
* Wenn mehrere Inhaltspakete vorhanden sind, ist die Reihenfolge der Paketimplementierungen nicht garantiert.
   * Wenn eine bestimmte Reihenfolge benötigt wird, können die Abhängigkeiten des Inhaltspakets zum Definieren der Reihenfolge verwendet werden.
* Pakete können bei der Implementierung [übersprungen](#skipping-content-packages) werden.

## Aktivieren von Maven-Profilen in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In einigen wenigen Fällen müssen Sie den Build-Prozess möglicherweise etwas anders gestalten, wenn er in Cloud Manager und nicht auf Entwickler-Workstations ausgeführt wird. In diesen Fällen können Sie mit [Maven-Profilen](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) definieren, wie der Build in verschiedenen Umgebungen (einschließlich Cloud Manager) abweichen soll.

Die Aktivierung eines Maven-Profils innerhalb der Cloud Manager-Build-Umgebung sollte durch die Suche nach der Umgebungsvariablen `CM_BUILD`[ erfolgen.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) Ebenso sollte bei einem Profil, das nur außerhalb der Cloud Manager-Build-Umgebung verwendet werden soll, darauf geachtet werden, dass diese Variable nicht vorhanden ist.

Wenn zum Beispiel eine einfache Nachricht nur dann ausgegeben werden soll, wenn der Build innerhalb von Cloud Manager ausgeführt wird, verwenden Sie Folgendes.

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

Wenn zum Beispiel eine einfache Nachricht nur dann ausgegeben werden soll, wenn der Build außerhalb von Cloud Manager ausgeführt wird, verwenden Sie Folgendes.

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
>
>Artefakte aus einem passwortgeschützten Maven-Repository sollten nur sehr vorsichtig verwendet werden, da Code, der über diesen Mechanismus bereitgestellt wird, derzeit nicht alle [Codequalitätsregeln](/help/implementing/cloud-manager/custom-code-quality-rules.md) durchläuft, die in den Quality Gates von Cloud Manager implementiert sind. Daher sollten sie nur in seltenen Fällen und nur für Code verwendet werden, der nicht an AEM gebunden ist. Es wird empfohlen, neben der Binärdatei auch die Java-Quellen sowie den gesamten Projektquell-Code bereitzustellen.

So verwenden Sie ein passwortgeschütztes Maven-Repository in Cloud Manager:

1. Geben Sie das Passwort (und optional den Benutzernamen) als geheime [Pipeline-Variable](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) an.
1. Dann verweisen Sie auf dieses Geheimnis in einer Datei namens `.cloudmanager/maven/settings.xml` im Git-Repository, die dem Schema der [Maven-Einstellungsdatei](https://maven.apache.org/settings.html) folgt.

Wenn der Build-Prozess von Cloud Manager gestartet wird:

* Das `<servers>`-Element in dieser Datei wird in die von Cloud Manager bereitgestellte Standard-`settings.xml`-Datei eingefügt.
   * Server-IDs, die mit `adobe` und `cloud-manager` beginnen, gelten als reserviert und sollten nicht von kundenspezifischen Servern verwendet werden.
   * Server-IDs, die nicht mit einem dieser Präfixe oder der Standard-ID `central` übereinstimmen, werden von Cloud Manager niemals gespiegelt.
* Wenn diese Datei vorhanden ist, wird die Server- ID von innerhalb eines `<repository>`- und/oder `<pluginRepository>`-Elements in der `pom.xml`-Datei referenziert.
* Im Allgemeinen wären diese `<repository>`- und/oder `<pluginRepository>`-Elemente in einem [Cloud Manager-spezifischen Profil](#activating-maven-profiles-in-cloud-manager) enthalten, auch wenn dies nicht unbedingt erforderlich ist.

Beispiel: Das Repository befindet sich unter `https://repository.myco.com/maven2`, der von Cloud Manager zu verwendende Benutzername lautet `cloudmanager` und das Kennwort lautet `secretword`. Sie würden die folgenden Schritte ausführen.

1. Legen Sie in der Pipeline das Passwort als Geheimnis fest.

   ```text
   $ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`
   ```

1. Verweisen Sie anschließend aus der `.cloudmanager/maven/settings.xml`-Datei darauf.

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

1. Verweisen Sie schließlich auf die Server-ID in der `pom.xml`-Datei:

   ```xml
   <profiles>
       <profile>
           <id>cmBuild</id>
           <activation>
                   <property>
                       <name>env.CM_BUILD</name>
                   </property>
           </activation>
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
       </profile>
   </profiles>
   ```

### Bereitstellen von Quellen {#deploying-sources}

Es empfiehlt sich, die Java-Quellen zusammen mit der Binärdatei in einem Maven-Repository bereitzustellen.

Konfigurieren Sie dazu das Maven-Source-Plug-in in Ihrem Projekt.

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

Es empfiehlt sich, die gesamte Projektquelle zusammen mit den Binärdaten in einem Maven-Repository bereitzustellen. Dies erlaubt die Neuerstellung des exakten Artefakts.

Konfigurieren Sie dazu das Maven-Assembly-Plug-in in Ihrem Projekt.

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

In Cloud Manager können Builds eine beliebige Anzahl von Inhaltspaketen generieren. Aus vielerlei Gründen kann es sinnvoll sein, ein Inhaltspaket zu erstellen, es jedoch nicht bereitzustellen. Ein Beispiel wäre die Erstellung von Inhaltspaketen, die nur zu Testzwecken verwendet werden oder die in einem anderen Schritt des Erstellungsprozesses neu gepackt werden, d. h. als Unterpaket eines anderen Pakets.

Um diese Szenarien zu berücksichtigen, sucht Cloud Manager in den Eigenschaften erstellter Inhaltspakete nach einer Eigenschaft namens `cloudManagerTarget`. Wenn diese Eigenschaft auf `none` festgelegt ist, wird das Paket übersprungen und nicht bereitgestellt.

Der Mechanismus zum Festlegen dieser Eigenschaft hängt davon ab, wie der Build das Inhaltspaket erzeugt. Mit dem `filevault-maven-plugin` würden Sie beispielsweise das Plug-in wie folgt konfigurieren.

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

Das `content-package-maven-plugin` weist eine ähnliche Konfiguration auf.

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

## Wiederverwendung von Build-Artefakten {#build-artifact-reuse}

In vielen Fällen wird derselbe Code in mehreren AEM-Umgebungen bereitgestellt. Wenn festgestellt wird, dass derselbe Git-Commit in mehreren Pipeline-Ausführungen mit vollem Stapel verwendet wird, verhindert Cloud Manager, dass die Code-Basis neu erstellt wird.

Wenn eine Ausführung gestartet wird, wird der aktuelle HEAD-Commit für die Zweig-Pipeline extrahiert. Der Commit-Hash ist in der Benutzeroberfläche und über die API sichtbar. Wenn der Build-Schritt erfolgreich abgeschlossen wurde, werden die resultierenden Artefakte basierend auf diesem Commit-Hash gespeichert und können in nachfolgenden Pipeline-Ausführungen wiederverwendet werden.

Pakete werden in allen Pipelines wiederverwendet, wenn sie sich im selben Programm befinden. Bei der Suche nach Paketen, die wiederverwendet werden können, ignoriert AEM Verzweigungen und verwendet Artefakte in allen Verzweigungen wieder.

Wenn eine Wiederverwendung erfolgt, werden die Build- und Code-Qualitätsschritte effektiv durch die Ergebnisse der ursprünglichen Ausführung ersetzt. In der Protokolldatei für den Build-Schritt werden die Artefakte und die Ausführungsinformationen aufgelistet, die ursprünglich zum Erstellen verwendet wurden.

Im Folgenden finden Sie ein Beispiel für eine solche Protokollausgabe.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Das Protokoll des Code-Qualitätsschritts enthält ähnliche Informationen.

### Beispiele {#example-reuse}

#### Beispiel 1 {#example-1}

Beachten Sie, dass Ihr Programm über zwei Entwicklungs-Pipelines verfügt:

* Pipeline 1 auf Verzweigung `foo`
* Pipeline 2 auf Verzweigung `bar`

Beide Verzweigungen befinden sich auf derselben Commit-ID.

1. Wenn Sie zuerst Pipeline 1 ausführen, werden die Pakete normal erstellt.
1. Wenn Sie dann Pipeline 2 ausführen, werden von Pipeline 1 erstellte Pakete wiederverwendet.

#### Beispiel 2 {#example-2}

Beachten Sie, dass Ihr Programm zwei Verzweigungen hat:

* Verzweigung `foo`
* Verzweigung `bar`

Beide Verzweigungen haben dieselbe Commit-ID.

1. Eine Entwicklungs-Pipeline erstellt `foo` und führt sie aus.
1. Anschließend erstellt eine Produktions-Pipeline `bar` und führt sie aus.

In diesem Fall wird das Artefakt von `foo` für die Produktions-Pipeline wiederverwendet, da derselbe Commit-Hash erkannt wurde.

### Deaktivieren {#opting-out}

Falls gewünscht, kann das Wiederverwendungsverhalten für bestimmte Pipelines deaktiviert werden, indem die Pipeline-Variable `CM_DISABLE_BUILD_REUSE` auf `true` festgelegt wird. Wenn diese Variable festgelegt ist, wird der Commit-Hash weiterhin extrahiert und die resultierenden Artefakte werden zur späteren Verwendung gespeichert, aber alle zuvor gespeicherten Artefakte werden nicht wiederverwendet. Um dieses Verhalten zu verstehen, sehen Sie sich das folgende Szenario an.

1. Eine neue Pipeline wird erstellt.
1. Die Pipeline wird ausgeführt (Ausführung #1) und der aktuelle HEAD-Commit lautet `becdddb`. Die Ausführung ist erfolgreich und die resultierenden Artefakte werden gespeichert.
1. Die Variable `CM_DISABLE_BUILD_REUSE` ist festgelegt.
1. Die Pipeline wird erneut ausgeführt, ohne dass der Code geändert wird. Obwohl es gespeicherte Artefakte gibt, die mit `becdddb` verknüpft sind, werden sie aufgrund der Variablen `CM_DISABLE_BUILD_REUSE` nicht wiederverwendet.
1. Der Code wird geändert und die Pipeline wird ausgeführt. Der HEAD-Commit ist jetzt `f6ac5e6`. Die Ausführung ist erfolgreich und die resultierenden Artefakte werden gespeichert.
1. Die Variable `CM_DISABLE_BUILD_REUSE` wird gelöscht.
1. Die Pipeline wird erneut ausgeführt, ohne dass der Code geändert wird. Da es gespeicherte Artefakte gibt, die mit `f6ac5e6` verknüpft sind, werden diese Artefakte wiederverwendet.

### Einschränkungen {#caveats}

* Build-Artefakte werden nicht in verschiedenen Programmen wiederverwendet, unabhängig davon, ob der Commit-Hash identisch ist.
* Build-Artefakte werden innerhalb desselben Programms wiederverwendet, selbst wenn die Verzweigung und/oder die Pipeline unterschiedlich sind.
* Der [Umgang mit Maven-Versionen](/help/implementing/cloud-manager/managing-code/project-version-handling.md) ersetzt die Projektversion nur in Produktions-Pipelines. Wenn daher derselbe Commit sowohl für die Ausführung einer Entwicklungsbereitstellung als auch für die Ausführung einer Produktions-Pipeline verwendet wird und die Pipeline der Entwicklungsbereitstellung zuerst ausgeführt wird, werden die Versionen in der Staging- und Produktionsumgebung bereitgestellt, ohne dass Änderungen vorgenommen werden. In diesem Fall wird jedoch weiterhin ein Tag erstellt.
* Wenn das Abrufen der gespeicherten Artefakte nicht erfolgreich ist, wird der Build-Schritt so ausgeführt, als ob keine Artefakte gespeichert worden wären.
* Andere Pipeline-Variablen als `CM_DISABLE_BUILD_REUSE` werden nicht berücksichtigt, wenn Cloud Manager beschließt, zuvor erstellte Build-Artefakte wiederzuverwenden.
