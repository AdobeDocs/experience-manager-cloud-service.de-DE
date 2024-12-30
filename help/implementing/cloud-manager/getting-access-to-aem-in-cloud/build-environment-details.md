---
title: Build-Umgebung von Cloud Manager
description: Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 3bc9ec12de604818f6be1c0717566a5f16c6a7b9
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 89%

---


# Build-Umgebung {#build-environment}

Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.

## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung.

* Die Build-Umgebung ist Linux-basiert und von Ubuntu 22.04 abgeleitet.
* Apache Maven 3.9.4 ist installiert.
   * Adobe empfiehlt Benutzenden, [ihre Maven-Repositorys zu aktualisieren, um HTTPS anstelle von HTTP zu verwenden](#https-maven).
* <!-- OLD --> Die installierten Java-Versionen sind Oracle JDK 11.0.22 und Oracle JDK 8u401.
<!-- NEW but needed to be removed 12/5/24 * The Java versions installed are Oracle JDK 11.0.22, Oracle JDK 17.0.10, and Oracle JDK 21.0.4. -->
<!-- OLD --> * **WICHTIG:** Standardmäßig ist die Umgebungsvariable JAVA_HOME auf `/usr/lib/jvm/jdk1.8.0_401` festgelegt, das Oracle JDK 8u401 enthält. Dieser Standard sollte für AEM-Cloud-Projekte überschrieben werden, um JDK 11 zu verwenden. Weitere Informationen finden Sie im Abschnitt Festlegen der Maven-JDK-Version .
<!-- NEW but needed to be removed 12/5/24 * **IMPORTANT:** By default, the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk1.8.0_401`, which contains Oracle JDK 8u401. ***This default should be overridden for AEM Cloud Projects to use JDK 21 (preferred), 17, or 11***. See the [Setting the Maven JDK Version](#alternate-maven-jdk-version) section for more details. -->
* Es werden einige zusätzliche erforderliche Systempakete installiert.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere Pakete können zur Build-Zeit installiert werden, wie im Abschnitt [Installieren zusätzlicher Systempakete](#installing-additional-system-packages) beschrieben.
* Jeder Build wird in einer sauberen Umgebung ausgeführt, wobei der Build-Container keinen Status zwischen den Ausführungen behält.
* Maven wird immer mit den folgenden drei Befehlen ausgeführt.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wird auf Systemebene mit einer `settings.xml`-Datei konfiguriert, die automatisch das öffentliche Adobe-Artefakt-Repository enthält und ein Profil namens `adobe-public` verwendet. (Weitere Informationen dazu finden Sie im [Adobe Public Maven Repository](https://repo1.maven.org/).)

>[!NOTE]
>
>Obwohl Cloud Manager keine bestimmte Version des Programms des `jacoco-maven-plugin` definiert, muss mindestens die Version `0.7.5.201505241946` verwendet werden.

## HTTPS-Maven-Repositorys {#https-maven}

Cloud Manager [Version 2023.10.0](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) hat eine rollierende Aktualisierung der Build-Umgebung gestartet (mit Version 2023.12.0 abgeschlossen), die eine Aktualisierung auf Maven 3.8.8 enthielt. Eine wesentliche Änderung, die in Maven 3.8.1 eingeführt wurde, war eine Sicherheitsverbesserung, die darauf abzielte, potenzielle Schwachstellen zu minimieren. Insbesondere deaktiviert Maven nun alle unsicheren `http://*`-Spiegelungen standardmäßig, wie in den [Maven-Versionshinweisen](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291) beschrieben.

Aufgrund dieser Sicherheitsverbesserung können bei einzelnen Benutzenden während des Build-Schritts Probleme auftreten, insbesondere beim Herunterladen von Artefakten aus Maven-Repositorys, die unsichere HTTP-Verbindungen verwenden.

Um ein reibungsloses Erlebnis mit der aktualisierten Version zu gewährleisten, empfiehlt Adobe, dass Benutzende ihre Maven-Repositorys so aktualisieren, dass sie HTTPS anstelle von HTTP verwenden. Diese Anpassung steht im Einklang mit dem wachsenden Trend der Branche hin zu sicheren Kommunikationsprotokollen und trägt zur Aufrechterhaltung eines sicheren und zuverlässigen Build-Prozesses bei.

<!-- OLD below -->

### Verwenden einer bestimmten Java-Version

Der Cloud Manager-Build-Prozess verwendet standardmäßig das Oracle 8-JDK, um Projekte zu erstellen. AEM Cloud Service-Kunden sollten die Maven-Ausführung-JDK-Version jedoch auf 11 setzen.

<!-- OLD below -->

#### Einstellen der Maven-JDK-Version

Adobe empfiehlt, die JDK-Version für die gesamte Maven-Ausführung auf `11` in einem `.cloudmanager/java-version file` festzulegen.

Erstellen Sie dazu eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Bearbeiten Sie die Datei so, dass sie nur den Text enthält, `11`. Cloud Manager akzeptiert zwar auch den Wert `8`, jedoch wird diese Version nicht mehr für AEM Cloud Service-Projekte unterstützt. Alle anderen Werte werden ignoriert. Wenn `11` angegeben ist, wird Oracle 11 verwendet und die Umgebungsvariable `JAVA_HOME` wird auf `/usr/lib/jvm/jdk-11.0.22` festgelegt.

<!-- NEW but needed to be removed 12/5/24 ### Use a specific Java version {#using-java-support}

The Cloud Manager build process uses the Oracle 8 JDK to build projects by default, but AEM Cloud Service customers should set the Maven execution JDK version to 21 (preferred), 17, or 11.

#### Set the Maven JDK version {#alternate-maven-jdk-version}

Adobe recommends setting the Maven execution JDK version to `21` or `17` in a `.cloudmanager/java-version` file.

To do so, create a file named `.cloudmanager/java-version` in the Git repository branch used by the pipeline. Edit the file so that it contains only the text, `21` or `17`. While Cloud Manager also accepts a value of `8`, this version is no longer supported for AEM Cloud Service projects. Any other value is ignored. When `21` or `17` is specified, Oracle Java 21 or Oracle Java 17 is used and the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk-21` or `/usr/lib/jvm/jdk-17`.

#### Prerequisites for migrating to building with Java 21 or Java 17 {#prereq-for-building}

>[!NOTE]
>
>*When migrating your application to a new Java build version and runtime version, thoroughly test in dev and stage environments before deploying to production.
>Of special note, the following features have not yet been formally validated with Java 21 runtime: [Forms](/help/forms/home.md), [Workflows](/help/sites-cloud/authoring/workflows/overview.md), [Inbox](/help/sites-cloud/authoring/inbox.md), and [Projects](/help/sites-cloud/authoring/projects/overview.md). If your application relies on these features, ensure comprehensive testing to verify functionality.*

##### About some translation features {#translation-features}

The following features might not function correctly when building with Java 21 or Java 17, and Adobe expects to resolve them by early 2025:

* `XLIFF` (XML Localization Interchange File Format) fails when using Human Translation.  
* `I18n` (Internationalization) does not properly handle language locales Hebrew (`he`), Indonesian (`in`), and Yiddish (`yi`) due to changes in the Locale constructor in newer Java versions.

#### Runtime requirements {#runtime-requirements}

The Java 21 runtime is used for builds on Java 21, Java 17, and Java 11 starting in February 2025. To ensure compatibility, the following adjustments are necessary. 

Library updates can be applied anytime, as they remain compatible with older Java versions.

* **Minimum version of `org.objectweb.asm`:**
Update the usage of `org.objectweb.asm` to version 9.5 or higher to ensure support for newer JVM runtimes.

* **Minimum version of `org.apache.groovy`:**
Update the usage of `org.apache.groovy` to version 4.0.22 or higher to ensure support for newer JVM runtimes.

  This bundle can be indirectly included by adding third party dependencies such as the AEM Groovy Console.

* **Edit a runtime parameter:**
When running AEM locally with Java 21, the start scripts (`crx-quickstart/bin/start` or `crx-quickstart/bin/start.bat`) fail due to the `MaxPermSize` parameter. As a remedy, either remove `-XX:MaxPermSize=256M` from the script or define the environment variable `CQ_JVM_OPTS`, setting it to `-Xmx1024m -Djava.awt.headless=true`.

  Adobe plans to resolve this issue in a future release.

>[!NOTE]
>
>When `.cloudmanager/java-version` is set to `21` or `17`, the Java 21 runtime is deployed. In February or March 2025, the Java 21 runtime is planned for deployment to all customers, even if Java 11 is used to build your code. 

#### Build time requirements

The following adjustments are required to allow building the project with Java 21 and Java 17. They can be updated at any time as they are compatible with older versions of Java.

* **Minimum version of `bnd-maven-plugin`:**
Update the usage of `bnd-maven-plugin` to version 6.4.0 to ensure support for newer JVM runtimes. 

  Versions 7 or higher are not compatible with Java 11 or lower so an upgrade to that version is not recommended.

* **Minimum version of `aemanalyser-maven-plugin`:**
Update the usage of `aemanalyser-maven-plugin` to version 1.6.6 or higher to ensure support for newer JVM runtimes.

* **Minimum version of `maven-bundle-plugin`:**
Update the usage of `maven-bundle-plugin` to version 5.1.5 or higher to ensure support for newer JVM runtimes. 

  Versions 6 or higher are not compatible with Java 11 or lower so an upgrade to that version is not recommended.

* **Update dependencies in `maven-scr-plugin`:**
The `maven-scr-plugin` is not directly compatible with Java 21 or Java 17. However, descriptor files can be generated by updating the ASM dependency version in the plugin configuration, as shown in the following example:

```XML
<project>
  ...
  <build>
    ...
    <plugins>
      ...
      <plugin>
        <groupId>org.apache.felix</groupId>
        <artifactId>maven-scr-plugin</artifactId>
        <version>1.26.4</version>
        <executions>
          <execution>
            <id>generate-scr-scrdescriptor</id>
            <goals>
              <goal>scr</goal>
            </goals>
          </execution>
        </executions>
        <dependencies>
          <dependency>
            <groupId>org.ow2.asm</groupId>
            <artifactId>asm-analysis</artifactId>
            <version>9.7.1</version>
            <scope>compile</scope>
          </dependency>
        </dependencies>
      </plugin>
      ...
    </plugins>
    ...
  </build>
  ...
</project>
```
-->


## Umgebungsvariablen – Standard {#environment-variables}

Je nach den Informationen über das Programm oder die Pipeline kann es notwendig sein, den Build-Prozess zu variieren.

Wenn beispielsweise die Minimierung von JavaScript zur Erstellungszeit mithilfe eines Tools wie Gulp erfolgt, können für verschiedene Umgebungen unterschiedliche Minimierungsstufen als Voreinstellung festgelegt werden. Ein Entwicklungs-Build verwendet möglicherweise eine geringere Minimierungsstufe als Staging und Produktion.

Um dies zu unterstützen, fügt Cloud Manager diese Standard-Umgebungsvariablen bei jeder Ausführung dem Build-Container hinzu.

| Variablenname | Definition |
|---|---|
| `CM_BUILD` | Immer auf `true` (wahr) festgelegt |
| `BRANCH` | Die konfigurierte Verzweigung für die Ausführung |
| `CM_PIPELINE_ID` | Numerische Pipeline-Kennung |
| `CM_PIPELINE_NAME` | Name der Pipeline |
| `CM_PROGRAM_ID` | Numerische Programmkennung |
| `CM_PROGRAM_NAME` | Name des Programms |
| `ARTIFACTS_VERSION` | Die von Cloud Manager generierte synthetische Version bei einer Staging- oder Produktions-Pipeline |
| `CM_AEM_PRODUCT_VERSION` | Die Release-Version |

## Umgebungsvariablen – Pipeline {#pipeline-variables}

Ihr Build-Prozess erfordert möglicherweise bestimmte Konfigurationsvariablen, die nicht im Git-Repository gespeichert werden sollten. Darüber hinaus müssen Sie diese Variablen möglicherweise zwischen den Pipeline-Ausführungen anpassen, die dieselbe Verzweigung verwenden.

Weitere Informationen finden Sie unter [Konfigurieren von Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).

## Installieren zusätzlicher Systempakete {#installing-additional-system-packages}

Einige Builds erfordern zusätzliche Systempakete, um vollständig zu funktionieren. So ist es z. B. möglich, dass ein Build ein Python- oder Ruby-Skript aufruft, wofür der entsprechende Sprach-Interpreter installiert sein muss. Dieser Installationsprozess kann durch einen Aufruf von [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) in Ihrer `pom.xml` gesteuert werden, um APT aufzurufen. Diese Ausführung sollte im Allgemeinen in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen sein. In diesem Beispiel wird Python installiert.

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

Mit derselben Methode können Sie auch sprachspezifische Pakete installieren, z. B. mit `gem` für RubyGems oder mit `pip` für Python-Pakete.

>[!NOTE]
>
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es nicht in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein Systempaket in der AEM-Umgebung installieren möchten, wenden Sie sich an Ihre Adobe-Support-Mitarbeiter.

>[!TIP]
>
>Weitere Informationen zur Frontend-Build-Umgebung finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
