---
title: Build-Umgebung
description: Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie der Code erstellt und getestet wird.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
source-git-commit: 5f344682aa0427d46dc6ca75fe83b0071348ad83
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 52%

---

# Build-Umgebung {#build-environment}

Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie der Code erstellt und getestet wird.

## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung.

* Die Erstellungsumgebung ist Linux-basiert und von Ubuntu 18.04 abgeleitet.
* Apache Maven 3.6.0 ist installiert.
* Die installierten Java-Versionen sind Oracle JDK 8u202 und Oracle JDK 11.0.2.
* Standardmäßig wird die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk1.8.0_202` festgelegt, was Oracle JDK 8u202 enthält. Weitere Einzelheiten finden Sie im Abschnitt [Alternative Maven-Ausführung JDK-Version](#alternate-maven-jdk-version).
* Es sind einige zusätzliche erforderliche Systempakete installiert.

   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`

* Andere Pakete können zur Build-Zeit installiert werden, wie im Abschnitt beschrieben. [Installieren zusätzlicher Systempakete.](#installing-additional-system-packages)
* Jeder Build wird in einer unberührten Umgebung erstellt, der Build-Container speichert zwischen den Ausführungen keinen Status.
* Maven wird immer mit den folgenden drei Befehlen ausgeführt.

* `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
* `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
* `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent packageco-maven-plugin:prepare-agent package`
* Maven wird auf Systemebene mit einer `settings.xml` -Datei, die automatisch das Artefakt-Repository der öffentlichen Adobe mit einem Profil namens `adobe-public`. (Weitere Informationen dazu finden Sie im [Adobe Public Maven Repository](https://repo1.maven.org/)).

>[!NOTE]
>
>Obwohl Cloud Manager keine bestimmte Version des Programms des `jacoco-maven-plugin` definiert, muss mindestens die Version `0.7.5.201505241946` verwendet werden.

### Verwenden einer bestimmten Java-Version {#using-java-support}

Standardmäßig werden Projekte vom Cloud Manager-Build-Prozess mit dem Oracle 8 JDK erstellt. Kunden, die ein alternatives JDK verwenden möchten, haben zwei Optionen.

* [Verwenden Sie Maven-Toolchain.](#maven-toolchains)
* [Wählen Sie eine alternative JDK-Version für den gesamten Maven-Ausführungsprozess aus.](#alternate-maven-jdk-version)

#### Maven Toolchains {#maven-toolchains}

Das [Maven Toolchain-Plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) ermöglicht es Projekten, ein bestimmtes JDK (oder Toolchain) auszuwählen, das im Kontext von Toolchain-fähigen Maven-Plug-ins verwendet werden soll. Dies geschieht in der `pom.xml`-Datei des Projekts, indem ein Anbieter und ein Versionswert angegeben werden.

```xml
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

Dies führt dazu, dass alle Toolchain-fähigen Maven-Plug-ins das Oracle JDK, Version 11 verwenden.

Bei Verwendung dieser Methode wird Maven selbst weiterhin mit dem standardmäßigen JDK (Oracle 8) ausgeführt und die `JAVA_HOME`-Umgebungsvariable wird nicht geändert. Daher funktioniert das Überprüfen oder Erzwingen der Java-Version über Plug-ins wie das Apache Maven Enforcer-Plug-in nicht und solche Plug-ins dürfen nicht verwendet werden.

Die derzeit verfügbaren Anbieter-/Versionskombinationen sind:

| Anbieter | Version |
|---|---|
| `oracle` | `1.8` |
| `oracle` | `1.11` |
| `oracle` | `11` |
| `sun` | `1.8` |
| `sun` | `1.11` |
| `sun` | `11` |

>[!NOTE]
>
>Ab April 2022 wird Oracle JDK das Standard-JDK für die Entwicklung und den Betrieb von AEM-Anwendungen sein. Der Build-Prozess von Cloud Manager wechselt automatisch zur Verwendung von Oracle JDK, auch wenn in der Maven-Toolchain explizit eine alternative Option ausgewählt ist. Weitere Informationen finden Sie in den Versionshinweisen vom April , sobald sie veröffentlicht wurden.

## Umgebungsvariablen {#environment-variables}

### Standard-Umgebungsvariablen {#standard-environ-variables}

Möglicherweise ist es erforderlich, den Build-Prozess basierend auf Informationen über das Programm oder die Pipeline zu variieren.

Wenn beispielsweise die JavaScript-Minimierung während der Build-Erstellung über ein Tool wie gulp erfolgt, kann es sinnvoll sein, beim Erstellen für eine Entwicklungsumgebung eine andere Minimierungsstufe zu verwenden als beim Erstellen für Staging und Produktion.

Um dies zu unterstützen, fügt Cloud Manager diese Standard-Umgebungsvariablen bei jeder Ausführung dem Build-Container hinzu.

| Variablenname | Definition |
|---|---|
| `CM_BUILD` | Immer auf `true` |
| `BRANCH` | Die konfigurierte Verzweigung für die Ausführung |
| `CM_PIPELINE_ID` | Numerische Pipeline-Kennung |
| `CM_PIPELINE_NAME` | Name der Pipeline |
| `CM_PROGRAM_ID` | Numerische Programmkennung |
| `CM_PROGRAM_NAME` | Name des Programms |
| `ARTIFACTS_VERSION` | Die von Cloud Manager generierte synthetische Version bei einer Staging- oder Produktions-Pipeline |
| `CM_AEM_PRODUCT_VERSION` | Die Versionsversion |

### Pipeline-Variablen {#pipeline-variables}

Ihr Build-Prozess kann von bestimmten Konfigurationsvariablen abhängen, die nicht in das Git-Repository platziert werden können. Andernfalls müssen Sie sie zwischen Pipeline-Ausführungen mit derselben Verzweigung variieren.

Cloud Manager ermöglicht die Konfiguration dieser Variablen über die Cloud Manager-API oder die Cloud Manager-CLI individuell für die Pipelines. Variablen können entweder als reiner Test oder mit Data-at-Rest-Verschlüsselung gespeichert werden. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die in der `pom.xml`-Datei oder anderen Build-Skripten referenziert werden kann.

Dieser CLI-Befehl legt eine Variable fest.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Dieser Befehl listet Variablen auf.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Variablennamen müssen die folgenden Konventionen einhalten.

* Variablen dürfen nur alphanumerische Zeichen und den Unterstrich (`_`).
* Die Namen sollten in Großbuchstaben eingegeben werden.
* Pro Pipeline sind maximal 200 Variablen zulässig.
* Jeder Name muss weniger als 100 Zeichen enthalten.
* Jeder `string` darf nicht länger als 2048 Zeichen sein.
* Jeder `secretString` Der Variablenwert type darf maximal 500 Zeichen enthalten.

Bei Verwendung in einem Maven `pom.xml` -Datei, ist es in der Regel hilfreich, diese Variablen Maven-Eigenschaften mit einer ähnlichen Syntax zuzuordnen.

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

Einige Builds erfordern die Installation zusätzlicher Systempakete, damit sie vollumfänglich funktionieren. Beispielsweise kann ein Build ein Python- oder Ruby-Skript aufrufen und muss einen entsprechenden Sprachinterpreter installiert haben. Dies kann durch Aufruf der [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) in `pom.xml` , um APT aufzurufen. Diese Ausführung sollte im Allgemeinen in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen sein. In diesem Beispiel wird Python installiert.

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

Dieselbe Technik kann zur Installation sprachspezifischer Pakete verwendet werden, z. B. mithilfe von `gem` für RubyGems oder `pip` für Python-Pakete.

>[!NOTE]
>
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es nicht in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein Systempaket in der AEM-Umgebung installieren möchten, wenden Sie sich an Ihre Adobe-Support-Mitarbeiter.
