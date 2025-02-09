---
title: Build-Umgebung von Cloud Manager
description: Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: d5461217cfec894a922b2f476aabfc04df45d9d0
workflow-type: tm+mt
source-wordcount: '1488'
ht-degree: 44%

---


# Build-Umgebung {#build-environment}

Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.

## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung.

* Die Build-Umgebung ist Linux-basiert und von Ubuntu 22.04 abgeleitet.
* Apache Maven 3.9.4 ist installiert.
   * Adobe empfiehlt Benutzenden, [ihre Maven-Repositorys zu aktualisieren, um HTTPS anstelle von HTTP zu verwenden](#https-maven).
<!-- OLD Removed 1/16/25 * The Java versions installed are Oracle JDK 11.0.22 and Oracle JDK 8u401. -->
* Die installierten Java-Versionen sind Oracle JDK 11.0.22, Oracle JDK 17.0.10 und Oracle JDK 21.0.4.

<!-- OLD Removed 1/16/25 * **IMPORTANT:** By default, the JAVA_HOME environment variable is set to `/usr/lib/jvm/jdk1.8.0_401`, which contains Oracle JDK 8u401. This default should be overridden for AEM Cloud Projects to use JDK 11. See the Setting the Maven JDK Version section for more details. -->
* **WICHTIG:** Standardmäßig ist die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk1.8.0_401` festgelegt, was Oracle JDK 8u401 enthält. ***Dieser Standardwert sollte für AEM-Cloud-Projekte überschrieben werden, um JDK 21 (empfohlen), 17 oder 11*** verwenden. Weitere Einzelheiten finden Sie im Abschnitt [Einstellen der Maven JDK-Version](#alternate-maven-jdk-version).
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

<!-- OLD below Removed 1/16/25

### Use a specific Java version

The Cloud Manager build process uses the Oracle 8 JDK to build projects by default, but AEM Cloud Service customers should set the Maven execution JDK version to 11. -->

<!-- OLD below Removed 1/16/25

#### Set the Maven JDK version

Adobe recommends that you set the JDK version for the entire Maven execution to `11` in a `.cloudmanager/java-version file`.

To do so, create a file named `.cloudmanager/java-version` in the git repository branch used by the pipeline. Edit the file so that it contains only the text, `11`. While Cloud Manager also accepts a value of `8`, this version is no longer supported for AEM Cloud Service projects. Any other value is ignored. When `11` is specified, Oracle 11 is used and the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk-11.0.22`. -->

### Verwenden einer bestimmten Java-Version {#using-java-support}

Der Cloud Manager-Build-Prozess verwendet standardmäßig das Oracle 8-JDK, um Projekte zu erstellen. AEM Cloud Service-Kunden sollten jedoch die Maven-Ausführungs-JDK-Version auf 21 (empfohlen), 17 oder 11 festlegen.

#### Festlegen der Maven-JDK-Version {#alternate-maven-jdk-version}

Um das Maven-Ausführungs-JDK festzulegen, erstellen Sie eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Bearbeiten Sie die Datei so, dass sie nur den Text, die `21` oder die `17` enthält. Cloud Manager akzeptiert zwar auch den Wert `8`, jedoch wird diese Version nicht mehr für AEM Cloud Service-Projekte unterstützt. Alle anderen Werte werden ignoriert. Wenn `21` oder `17` angegeben ist, wird Oracle Java 21 oder Oracle Java 17 verwendet.


#### Voraussetzungen für die Migration zu einem Build mit Java 21 oder Java 17 {#prereq-for-building}

Um mit Java 21 oder Java 17 zu Building zu migrieren, müssen Sie zunächst ein Upgrade auf die neueste SonarQube-Version durchführen. Weitere Informationen finden Sie unter [Versionshinweise für Cloud Manager 2025.1.0](/help/implementing/cloud-manager/release-notes/current.md#what-is-new).

Wenn Sie Ihre Anwendung auf eine neue Java-Build-Version und Laufzeitversion migrieren, testen Sie sie gründlich in Entwicklungs- und Staging-Umgebungen, bevor Sie sie in der Produktion bereitstellen.

Wir empfehlen die folgende Bereitstellungsstrategie:

1. Führen Sie Ihre lokale SDK mit Java 21 aus, die Sie von https://experience.adobe.com/#/downloads herunterladen können, und stellen Sie Ihr Programm dafür bereit und überprüfen Sie die Funktionalität. Überprüfen Sie die Protokolle auf Fehler, die auf Probleme beim Classloading oder Bytecode Weaving hinweisen.
1. Konfigurieren Sie eine Verzweigung im Cloud Manager-Repository für die Verwendung von Java 21 als Java-Version zur Build-Zeit, konfigurieren Sie eine DEV-Pipeline für die Verwendung dieser Verzweigung und führen Sie die Pipeline aus. Führen Sie Ihre Validierungstests durch.
1. Wenn alles gut aussieht, konfigurieren Sie Ihre Staging-/Produktions-Pipeline so, dass Java 21 als Build-Time-Java-Version verwendet wird, und führen Sie die Pipeline aus.

##### Über einige Übersetzungsfunktionen {#translation-features}

Die folgenden Funktionen funktionieren möglicherweise nicht ordnungsgemäß, wenn sie auf der Java 21-Laufzeitumgebung bereitgestellt werden, und Adobe geht davon aus, dass sie bis Anfang 2025 behoben werden:

* `XLIFF` (XML Localization Interchange File Format) schlägt fehl, wenn eine menschliche Übersetzung verwendet wird.
* `I18n` (Internationalisierung) behandelt die Sprachgebietsschemata Hebräisch (`he`), Indonesisch (`in`) und Jiddisch (`yi`) aufgrund von Änderungen im Gebietsschema-Konstruktor in neueren Java-Versionen nicht ordnungsgemäß.

#### Laufzeitanforderungen {#runtime-requirements}

Die Java 21-Laufzeit wird für Builds mit Java 21 und Java 17 verwendet und nach und nach auch auf Java 11-Builds angewendet (siehe Hinweis unten). Um das Java 21-Update zu erhalten, muss die Umgebung auf AEM-Version 17098 oder neuer sein. Um die Kompatibilität sicherzustellen, sind die folgenden Anpassungen erforderlich.

Bibliotheksaktualisierungen können jederzeit angewendet werden, da sie mit älteren Java-Versionen kompatibel bleiben.

* **Mindestversion von ASM:**
Aktualisieren Sie die Verwendung des Java-Pakets`org.objectweb.asm`, das häufig in `org.ow2.asm.*` Artefakten gebündelt ist, auf Version 9.5 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

* **Mindestversion von Groovy:**
Aktualisieren Sie die Verwendung der Java-Pakete `org.apache.groovy` oder `org.codehaus.groovy` auf Version 4.0.22 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

  Dieses Paket kann indirekt durch Hinzufügen von Abhängigkeiten von Dritten wie der AEM Groovy Console eingeschlossen werden.

AEM Cloud Service SDK ist mit Java 21 kompatibel und kann verwendet werden, um die Kompatibilität Ihres Projekts mit Java 21 zu überprüfen, bevor Sie eine Cloud Manager-Pipeline ausführen.

* **Laufzeitparameter bearbeiten:**
Beim lokalen Ausführen von AEM mit Java 21 schlagen die Startskripte (`crx-quickstart/bin/start` oder `crx-quickstart/bin/start.bat`) aufgrund des `MaxPermSize` fehl. Entfernen Sie als Abhilfe entweder `-XX:MaxPermSize=256M` aus dem Skript oder definieren Sie die `CQ_JVM_OPTS` der Umgebungsvariable, indem Sie sie auf `-Xmx1024m -Djava.awt.headless=true` setzen.

  Dieses Problem wurde in der AEM Cloud Service SDK-Version 19149 und höher behoben.

>[!IMPORTANT]
>
>Wenn `.cloudmanager/java-version` auf `21` oder `17` gesetzt ist, wird die Java 21-Laufzeitumgebung bereitgestellt. Die Java 21-Laufzeitumgebung soll ab Dienstag, dem 4. Februar 2025, schrittweise für alle Umgebungen (nicht nur für die Umgebungen, deren Code mit Java 11 erstellt wurde) bereitgestellt werden. Der Rollout beginnt mit Sandboxes und Entwicklungsumgebungen und führt dann im April 2025 einen Rollout in alle Produktionsumgebungen durch. Kunden, die die Java 21-Laufzeitumgebung (früher *übernehmen möchten,* sich unter [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) an Adobe.


#### Anforderungen an die Erstellungszeit {#build-time-reqs}

Die folgenden Anpassungen sind erforderlich, um das Erstellen des Projekts mit Java 21 und Java 17 zu ermöglichen. Sie können sogar vor der Ausführung von Java 21 und Java 17 aktualisiert werden, da sie mit älteren Java-Versionen kompatibel sind.

AEM Cloud Service-Kunden wird empfohlen, ihre Projekte so früh wie möglich mit Java 21 zu erstellen, um neue Sprachfunktionen nutzen zu können.

* **Mindestversion von `bnd-maven-plugin`:**
Aktualisieren Sie die Verwendung von `bnd-maven-plugin` auf Version 6.4.0, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

  Versionen 7 oder höher sind nicht mit Java 11 oder niedriger kompatibel. Daher wird ein Upgrade auf diese Version nicht empfohlen.

* **Mindestversion von `aemanalyser-maven-plugin`:**
Aktualisieren Sie die Verwendung von `aemanalyser-maven-plugin` auf Version 1.6.6 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

* **Mindestversion von `maven-bundle-plugin`:**
Aktualisieren Sie die Verwendung von `maven-bundle-plugin` auf Version 5.1.5 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

  Versionen 6 oder höher sind nicht mit Java 11 oder niedriger kompatibel. Daher wird ein Upgrade auf diese Version nicht empfohlen.

* **Aktualisieren von Abhängigkeiten in `maven-scr-plugin`:**
Die `maven-scr-plugin` ist nicht direkt mit Java 21 oder Java 17 kompatibel. Sie können jedoch Deskriptordateien generieren, indem Sie die AEM-Abhängigkeitsversion in der Plug-in-Konfiguration aktualisieren, wie im folgenden Beispiel gezeigt:

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
