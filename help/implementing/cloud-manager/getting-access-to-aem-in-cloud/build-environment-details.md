---
title: Build-Umgebung
description: Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
source-git-commit: 54135244d7b33ba3682633b455a5538474d3146e
workflow-type: ht
source-wordcount: '788'
ht-degree: 100%

---


# Build-Umgebung {#build-environment}

Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.

## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung.

* Die Build-Umgebung ist Linux-basiert und von Ubuntu 22.04 abgeleitet.
* Apache Maven 3.9.4 ist installiert.
   * Adobe empfiehlt Benutzenden, [ihre Maven-Repositorys zu aktualisieren, sodass sie HTTPS anstelle von HTTP verwenden](#https-maven).
* Die installierten Java-Versionen sind Oracle JDK 11.0.22 und Oracle JDK 8u401.
* **WICHTIG**: Standardmäßig wird die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk1.8.0_401` festgelegt, welches Oracle JDK 8u401 enthält. *_Diese Standardeinstellung sollte für AEM Cloud-Projekte überschrieben werden, damit JDK 11 verwendet wird_*. Weitere Einzelheiten finden Sie im Abschnitt [Einstellen der Maven JDK-Version](#alternate-maven-jdk-version).
* Es sind einige zusätzliche erforderliche Systempakete installiert.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere Pakete können zur Build-Zeit installiert werden, wie im Abschnitt [Installieren zusätzlicher Systempakete](#installing-additional-system-packages) beschrieben. 
* Jeder Build wird in einer unberührten Umgebung erstellt, der Build-Container speichert zwischen den Ausführungen keinen Status.
* Maven wird immer mit den folgenden drei Befehlen ausgeführt.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wird auf Systemebene mit einer `settings.xml`-Datei konfiguriert, die automatisch das öffentliche Adobe-Artefakt-Repository enthält und ein Profil namens `adobe-public` verwendet. (Weitere Informationen dazu finden Sie im [Adobe Public Maven Repository](https://repo1.maven.org/).)

>[!NOTE]
>
>Obwohl Cloud Manager keine bestimmte Version des Programms des `jacoco-maven-plugin` definiert, muss mindestens die Version `0.7.5.201505241946` verwendet werden.

## HTTPS-Maven-Repositorys {#https-maven}

Cloud Manager [Version 2023.10.0](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) hat eine rollierende Aktualisierung der Build-Umgebung gestartet (mit Version 2023.12.0 abgeschlossen), die eine Aktualisierung auf Maven 3.8.8 enthielt. Eine wesentliche Änderung, die in Maven 3.8.1 eingeführt wurde, war eine Sicherheitsverbesserung, die darauf abzielte, potenzielle Schwachstellen zu minimieren. Insbesondere deaktiviert Maven jetzt alle unsicheren `http://*`-Spiegelungen standardmäßig, wie in den [Maven-Versionshinweisen](http://maven.apache.org/docs/3.8.1/release-notes.html?lang=de#cve-2021-26291) beschrieben.

Aufgrund dieser Sicherheitsverbesserung können bei einzelnen Benutzenden während des Build-Schritts Probleme auftreten, insbesondere beim Herunterladen von Artefakten aus Maven-Repositorys, die unsichere HTTP-Verbindungen verwenden.

Um ein reibungsloses Erlebnis mit der aktualisierten Version zu gewährleisten, empfiehlt Adobe, dass Benutzende ihre Maven-Repositorys so aktualisieren, dass sie HTTPS anstelle von HTTP verwenden. Diese Anpassung steht im Einklang mit dem wachsenden Trend der Branche hin zu sicheren Kommunikationsprotokollen und trägt zur Aufrechterhaltung eines sicheren und zuverlässigen Build-Prozesses bei.

### Verwenden einer bestimmten Java-Version {#using-java-support}

Standardmäßig werden Projekte vom Cloud Manager-Build-Prozess mit dem Oracle 8 JDK erstellt. AEM Cloud Service-Kundinnen und -Kunden wird jedoch dringend empfohlen, die JDK-Version, die zum Ausführen von Maven verwendet wird, auf `11` einzustellen.

#### Einstellen der Maven-JDK-Version {#alternate-maven-jdk-version}

Es wird empfohlen, die JDK-Version für die gesamte Maven-Ausführung auf `11` in einer `.cloudmanager/java-version`-Datei einzustellen.

Erstellen Sie dazu eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Bearbeiten Sie die Datei so, dass sie nur den Text enthält, `11`. Cloud Manager akzeptiert zwar auch den Wert `8`, jedoch wird diese Version nicht mehr für AEM Cloud Service-Projekte unterstützt. Alle anderen Werte werden ignoriert. Wenn `11` angegeben ist, wird Oracle 11 verwendet und die Umgebungsvariable `JAVA_HOME` wird auf `/usr/lib/jvm/jdk-11.0.22` festgelegt.

## Umgebungsvariablen {#environment-variables}

### Standard-Umgebungsvariablen {#standard-environ-variables}

Je nach den Informationen über das Programm oder die Pipeline kann es notwendig sein, den Build-Prozess zu variieren.

Wenn beispielsweise eine JavaScript-Minimierung während der Build-Erstellung mithilfe eines Tools wie gulp durchgeführt wird, soll beim Erstellen für eine Entwicklungsumgebung möglicherweise eine andere Minimierungsstufe verwendet werden als beim Erstellen für eine Staging- oder Produktionsumgebung.

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

### Pipeline-Variablen {#pipeline-variables}

Der Build-Prozess kann von bestimmten Konfigurationsvariablen abhängen, die nicht im Git-Repository platziert werden können oder zwischen Pipeline-Ausführungen mit derselben Verzweigung variieren müssen.

Weitere Informationen finden Sie im Dokument [Konfigurieren von Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).

## Installieren zusätzlicher Systempakete {#installing-additional-system-packages}

Einige Builds erfordern die Installation zusätzlicher Systempakete, damit sie vollumfänglich funktionieren. So ist es z. B. möglich, dass ein Build ein Python- oder Ruby-Skript aufruft, wofür der entsprechende Sprach-Interpreter installiert sein muss. Dies kann durch Aufrufen des [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) in ihrer `pom.xml` erfolgen, wodurch APT aufgerufen wird. Diese Ausführung sollte im Allgemeinen in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen sein. In diesem Beispiel wird Python installiert.

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
