---
title: Details der Build-Umgebung
description: Details zur Umgebung erstellen - Cloud Services
translation-type: tm+mt
source-git-commit: 34087724d41de1fc4303ddbbb92122760d360e77
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 82%

---


# Grundlagen zur Build-Umgebung {#understanding-build-environment}

## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung. Diese Umgebung weist die folgenden Attribute auf:

* Die Erstellungsumgebung ist Linux-basiert und von Ubuntu 18.04 abgeleitet.
* Apache Maven 3.6.0 ist installiert.
* Die installierten Java-Versionen sind Oracle JDK 8u202 und 11.0.2.
* Es sind einige zusätzliche erforderliche Systempakete installiert:

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick

* Andere Pakete können zur Erstellungszeit wie [unten](#installing-additional-system-packages) beschrieben installiert werden.
* Jeder Build wird in einer unberührten Umgebung erstellt, der Build-Container speichert zwischen den Ausführungen keinen Status.
* Maven wird immer mit den folgenden drei Befehlen ausgeführt:

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent packageco-maven-plugin:prepare-agent package`
* Maven wird auf Systemebene mit einer settings.xml-Datei konfiguriert, die automatisch das öffentliche Adobe-**Artefakt**-Repository enthält. (See [Adobe Public Maven Repository](https://repo.adobe.com/) for more details).

>[!NOTE]
>Obwohl Cloud Manager keine bestimmte Version des Programms des `jacoco-maven-plugin` definiert, muss mindestens die Version `0.7.5.201505241946` verwendet werden.

### Java 11-Unterstützung verwenden {#using-java-support}

Cloud Manager unterstützt jetzt das Erstellen von Kundenprojekten mit Java 8 und Java 11. Standardmäßig werden Projekte mit Java 8 erstellt.

Customers who want to use Java 11 in their projects can do so using the [Apache Maven Toolchains Plugin](https://maven.apache.org/plugins/maven-toolchains-plugin/).

Fügen Sie dazu der Datei „pom.xml“ einen `<plugin>`-Eintrag hinzu, der wie folgt aussieht:

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
           </jdk>
        </toolchains>
    </configuration>
</plugin>
```

>[!NOTE]
>Supported vendor values are `oracle`  and `sun`and the supported version values are `1.8`, `1.11`, and `11`.

>[!NOTE]
>Der Cloud Manager-Projekterstellung nutzt weiterhin Java 8, um Maven aufzurufen. Daher funktioniert das Überprüfen oder Erzwingen der im Toolchain-Plugin konfigurierten Java-Version über Plugins wie das [Apache Maven Enforcer-Plugin](https://maven.apache.org/enforcer/maven-enforcer-plugin/) nicht und solche Plugins dürfen nicht verwendet werden.

## Umgebungsvariablen {#environment-variables}

### Standard-Umgebungsvariablen {#standard-environ-variables}

In einigen Fällen müssen Kunden den Build-Prozess je nach Informationen zum Programm oder zur Pipeline variieren.

Wenn beispielsweise eine JavaScript-Minimierung während der Build-Erstellung mithilfe eines Tools wie gulp durchgeführt wird, soll beim Erstellen für eine Entwicklungsumgebung möglicherweise eine andere Minimierungsstufe verwendet werden als beim Erstellen für eine Staging- oder Produktionsumgebung.

Um dies zu unterstützen, fügt Cloud Manager diese Standard-Umgebungsvariablen bei jeder Ausführung dem Build-Container hinzu.

| **Variablenname** | **Definition** |
|---|---|
| CM_BUILD | Immer auf „true“ (wahr) festgelegt |
| BRANCH | Die konfigurierte Verzweigung für die Ausführung |
| CM_PIPELINE_ID | Numerische Pipeline-Kennung |
| CM_PIPELINE_NAME | Name der Pipeline |
| CM_PROGRAM_ID | Numerische Programmkennung |
| CM_PROGRAM_NAME | Name des Programms |
| ARTIFACTS_VERSION | Die von Cloud Manager generierte synthetische Version bei einer Staging- oder Produktions-Pipeline |
| CM_AEM_PRODUCT_VERSION | Der Name der Version |

### Pipeline-Variablen {#pipeline-variables}

In einigen Fällen kann der Build-Prozess eines Kunden von bestimmten Konfigurationsvariablen abhängen, die nicht im Git-Repository platziert werden können oder zwischen Pipeline-Ausführungen mit derselben Verzweigung variieren müssen.

Cloud Manager ermöglicht die Konfiguration dieser Variablen über die Cloud Manager-API oder die Cloud Manager-CLI individuell für die Pipelines. Variablen können entweder als reiner Test oder mit Data-at-Rest-Verschlüsselung gespeichert werden. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die in der `pom.xml`-Datei oder anderen Build-Skripten referenziert werden kann.

Um eine Variable mithilfe der CLI festzulegen, führen Sie einen Befehl wie den folgenden aus:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

Aktuelle Variablen können aufgelistet werden:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Variablennamen dürfen nur alphanumerische Zeichen und Unterstriche (_) enthalten. Dabei sollten Großbuchstaben verwendet werden. Pro Pipeline sind maximal 200 Variablen zulässig. Jeder Name darf maximal 100 Zeichen und jeder Wert maximal 2048 Zeichen lang sein.

Bei Verwendung in einer `Maven pom.xml`-Datei ist es in der Regel hilfreich, diese Variablen Maven-Eigenschaften mit einer ähnlichen Syntax zuzuordnen:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Installieren zusätzlicher Systempakete {#installing-additional-system-packages}

Einige Builds erfordern die Installation zusätzlicher Systempakete, damit sie vollumfänglich funktionieren. So ist es z. B. möglich, dass ein Build ein Python- oder Ruby-Skript aufruft, wofür der entsprechende Sprach-Interpreter installiert sein muss. Dies kann durch Abfrage von [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) erfolgen, wodurch APT aufgerufen wird. Diese Ausführung sollte im Allgemeinen in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen sein. So installieren Sie beispielsweise Python:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Mit derselben Methode können Sie auch sprachspezifische Pakete installieren, d. h. mit `gem` für RubyGems oder mit `pip` für Python-Pakete.

>[!NOTE]
>
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es **nicht** in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein auf der AEM Umgebung installiertes Systempaket benötigen, wenden Sie sich an Ihren Kundenbetreuer für Adobe.