---
title: Build-Umgebung von Cloud Manager
description: Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 4dd6a9576092c2389f1416377b8e936360a7c7f8
workflow-type: tm+mt
source-wordcount: '1522'
ht-degree: 54%

---


# Build-Umgebung von Cloud Manager {#build-environment}

Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.

>[!TIP]
>
>In diesem Dokument wird die Build-Umgebung von Cloud Manager für die Entwicklung Ihres AEM as a Cloud Service-Projekts beschrieben. Einzelheiten zu den von AEM as a Cloud Service für die Inhaltserstellung unterstützten Client-Plattformen finden Sie unter [Unterstützte Client-Plattformen](/help/overview/supported-platforms.md).

## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung.

* Die Build-Umgebung ist Linux-basiert und von Ubuntu 22.04 abgeleitet.
* Apache Maven 3.9.4 ist installiert.
   * Adobe empfiehlt Benutzenden, [ihre Maven-Repositorys zu aktualisieren, um HTTPS anstelle von HTTP zu verwenden](#https-maven).
<!-- OLD Removed 1/16/25 * The Java versions installed are Oracle JDK 11.0.22 and Oracle JDK 8u401. -->
* Die installierten Java-Versionen sind Oracle JDK 11.0.22, Oracle JDK 17.0.10 und Oracle JDK 21.0.4.

<!-- OLD Removed 1/16/25 * **IMPORTANT:** By default, the JAVA_HOME environment variable is set to `/usr/lib/jvm/jdk1.8.0_401`, which contains Oracle JDK 8u401. This default should be overridden for AEM Cloud Projects to use JDK 11. See the Setting the Maven JDK Version section for more details. -->
* **WICHTIG**: Standardmäßig ist die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk1.8.0_401` festgelegt, was Oracle JDK 8u401 enthält. ***Überschreiben Sie diesen Standardwert für AEM Cloud-Projekte, um JDK 21 (empfohlen), 17 oder 11*** verwenden. Weitere Einzelheiten finden Sie im Abschnitt [Einstellen der Maven JDK-Version](#alternate-maven-jdk-version).
* Es sind einige zusätzliche erforderliche Systempakete installiert.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere Pakete werden zur Build-Zeit installiert, wie im Abschnitt [Installieren zusätzlicher Systempakete“ ](#installing-additional-system-packages).
* Jeder Build wird in einer neuen Umgebung ausgeführt. Der Build-Container speichert die Daten zwischen den Ausführungen nicht.
* Maven wird immer mit den folgenden drei Befehlen ausgeführt.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wird auf Systemebene mit einer `settings.xml`-Datei konfiguriert, die automatisch das öffentliche Adobe-Artefakt-Repository enthält und ein Profil namens `adobe-public` verwendet. (Weitere Informationen dazu finden Sie im [Adobe Public Maven Repository](https://repo1.maven.org/).)

>[!NOTE]
>
>Cloud Manager gibt keine bestimmte Version des `jacoco-maven-plugin` an, aber die erforderliche Version hängt von der Java-Version des Projekts ab. Für Java 8 muss die Plug-in-Version mindestens `0.7.5.201505241946` sein, während neuere Java-Versionen eine neuere Version erfordern.

## HTTPS-Maven-Repositorys {#https-maven}

Cloud Manager [Version 2023.10.0](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) begann mit einem rollierenden Update der Build-Umgebung (abgeschlossen mit Version 2023.12.0), das ein Update auf Maven 3.8.8 enthielt. Eine wichtige Änderung, die in Maven 3.8.1 eingeführt wurde, war eine Sicherheitsverbesserung, die darauf abzielte, potenzielle Schwachstellen zu beheben. Insbesondere deaktiviert Maven nun alle unsicheren `http://*`-Spiegelungen standardmäßig, wie in den [Maven-Versionshinweisen](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291) beschrieben.

Einige Benutzende stoßen während des Build-Schritts auf Probleme beim Herunterladen von Artefakten aus Maven-Repositorys, die unsichere HTTP-Verbindungen verwenden.

Um ein reibungsloses Erlebnis mit der aktualisierten Version zu gewährleisten, empfiehlt Adobe, dass Benutzende ihre Maven-Repositorys so aktualisieren, dass sie HTTPS anstelle von HTTP verwenden. Diese Anpassung entspricht der Umstellung der Branche auf sichere Kommunikationsprotokolle und trägt dazu bei, einen sicheren und zuverlässigen Build-Prozess aufrechtzuerhalten.

<!--
 OLD below Removed 1/16/25

### Use a specific Java version

The Cloud Manager build process uses the Oracle 8 JDK to build projects by default, but AEM Cloud Service customers should set the Maven execution JDK version to 11.
-->

<!--
 OLD below Removed 1/16/25

#### Set the Maven JDK version

Adobe recommends that you set the JDK version for the entire Maven execution to `11` in a `.cloudmanager/java-version file`.

To do so, create a file named `.cloudmanager/java-version` in the git repository branch used by the pipeline. Edit the file so that it contains only the text, `11`. While Cloud Manager also accepts a value of `8`, this version is no longer supported for AEM Cloud Service projects. Any other value is ignored. When `11` is specified, Oracle 11 is used and the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk-11.0.22`.
-->

### Verwenden einer bestimmten Java-Version {#using-java-support}

Der Cloud Manager-Build-Prozess verwendet standardmäßig das Oracle 8 JDK, um Projekte zu erstellen. AEM Cloud Service-Kunden legen die Maven-Ausführungs-JDK-Version jedoch auf 21 (empfohlen), 17 oder 11 fest.

#### Festlegen der Maven-JDK-Version {#alternate-maven-jdk-version}

Erstellen Sie zum Festlegen der JDK-Version zur Maven-Ausführung eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Bearbeiten Sie die Datei so, dass sie nur den Text enthält, `21` oder `17`. Cloud Manager akzeptiert zwar auch den Wert `8`, jedoch wird diese Version nicht mehr für AEM Cloud Service-Projekte unterstützt. Alle anderen Werte werden ignoriert. Wenn `21` oder `17` angegeben ist, wird Oracle Java 21 oder Oracle Java 17 verwendet.


#### Voraussetzungen für die Migration zur Build-Erstellung mit Java 21 oder Java 17 {#prereq-for-building}

Zum Erstellen mit Java 21 oder Java 17 verwendet Cloud Manager jetzt SonarQube 9.9, das mit diesen Java-Versionen kompatibel ist. Diese Änderung wurde mit Cloud Manager Version 2025.1.0 eingeführt. Für ein Upgrade von SonarQube ist keine Kundenaktion erforderlich. Weitere Informationen zur Änderung finden Sie in den [Versionshinweisen für Cloud Manager 2025.1.0](/help/implementing/cloud-manager/release-notes/2025/2025-1-0.md).

Wenn Sie Ihre Anwendung auf eine neue Java-Build- und Runtime-Version migrieren, testen Sie sie gründlich in Entwicklungs- und Staging-Umgebungen, bevor Sie sie in der Produktion bereitstellen.

Adobe empfiehlt die folgende Bereitstellungsstrategie:

1. Führen Sie Ihre lokale SDK mit Java 21 aus. Diese Datei können Sie von https://experience.adobe.com/#/downloads herunterladen, Ihr Programm für das Programm bereitstellen und seine Funktionalität überprüfen. Um sicherzustellen, dass keine Fehler auftreten, die auf Probleme beim Laden von Klassen oder beim Web-Bytecode hinweisen, überprüfen Sie die Protokolle.
1. Um Java 21 als Java-Version zur Build-Zeit zu verwenden, konfigurieren Sie eine Verzweigung in Ihrem Cloud Manager-Repository, konfigurieren Sie eine DEV-Pipeline für die Verwendung dieser Verzweigung und führen Sie die Pipeline aus. Führen Sie Validierungstests durch.
1. Wenn die Ergebnisse bei Verwendung von Java 21 als Java-Version zur Build-Zeit zufriedenstellend sind, konfigurieren Sie Ihre Staging-/Produktions-Pipeline und führen Sie die Pipeline aus.

##### Übersetzungsfunktionen {#translation-features}

Die folgenden Funktionen funktionieren bei der Bereitstellung zur Java 21-Laufzeit nicht ordnungsgemäß und Adobe geht davon aus, dass sie bis Anfang 2025 behoben werden:

* `XLIFF` (XML Localization Interchange File Format) schlägt bei menschlichen Übersetzungen fehl.
* `I18n` (Internationalisierung) behandelt die Sprachgebietsschemata Hebräisch (`he`), Indonesisch (`in`) und Jiddisch (`yi`) nicht ordnungsgemäß, da der Gebietsschema-Konstruktor in neueren Java-Versionen geändert wurde.

#### Laufzeitanforderungen {#runtime-requirements}

Die Java 21-Laufzeitumgebung wurde auf alle zulässigen Umgebungen angewendet, d. h. Umgebungen in AEM ab Version 17098, die die folgenden Kriterien erfüllen. Wenn eine Umgebung die Kriterien nicht erfüllt, müssen Sie Anpassungen vornehmen, um Leistung, Verfügbarkeit und Sicherheit sicherzustellen.

* **Mindestversion von ASM:**
Aktualisieren Sie die Verwendung des Java-Pakets`org.objectweb.asm`, das häufig in `org.ow2.asm.*` Artefakten gebündelt ist, auf Version 9.5 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

* **Mindestversion von Groovy:**
Aktualisieren Sie die Verwendung der Java-Pakete `org.apache.groovy` oder `org.codehaus.groovy` auf Version 4.0.22 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

  Dieses Paket kann indirekt durch Hinzufügen von Abhängigkeiten von Dritten wie der AEM Groovy Console eingeschlossen werden.

* **Mindestversion von Aries SPIFly:**
Aktualisieren Sie die Verwendung des Java-Pakets `org.apache.aries.spifly.dynamic.bundle` auf Version 1.3.6 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

Das AEM Cloud Service SDK unterstützt Java 21 und ermöglicht es, die Kompatibilität Ihres Projekts mit Java 21 zu überprüfen, bevor eine Cloud Manager-Pipeline ausgeführt wird.

* **Laufzeitparameter bearbeiten:**
Beim lokalen Ausführen von AEM mit Java 21 schlagen die Startskripte (`crx-quickstart/bin/start` oder `crx-quickstart/bin/start.bat`) aufgrund des `MaxPermSize` fehl. Alternativ können Sie entweder `-XX:MaxPermSize=256M` aus dem Skript entfernen oder die `CQ_JVM_OPTS` der Umgebungsvariable definieren und sie auf `-Xmx1024m -Djava.awt.headless=true` festlegen.

  Dieses Problem wurde in der AEM Cloud Service SDK-Version 19149 und höher behoben.

>[!IMPORTANT]
>
>Wenn eine Umgebung noch nicht automatisch auf die Java 21-Laufzeit aktualisiert wurde, können Sie dies durch Erstellen mit Java 17 oder 21 auslösen. Sie konfigurieren dies, indem Sie `.cloudmanager/java-version` auf `21` oder `17` setzen. Wenden Sie sich bei Fragen an Adobe unter [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com).

#### Anforderungen zur Build-Zeit: {#build-time-reqs}

Die folgenden Anpassungen sind erforderlich, um das Erstellen des Projekts mit Java 21 und Java 17 zu ermöglichen. Sie können sogar vor der Ausführung von Java 21 und Java 17 aktualisiert werden, da sie mit älteren Java-Versionen kompatibel sind.

Kundinnen und Kunden von AEM Cloud Service wird empfohlen, ihre Projekte so früh wie möglich mit Java 21 zu erstellen, um neue Sprachfunktionen nutzen zu können.

* **Mindestversion von `bnd-maven-plugin`:**
Aktualisieren Sie die Verwendung von `bnd-maven-plugin` auf Version 6.4.0, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

  Version 7 oder höher ist nicht mit Java 11 oder niedriger kompatibel. Daher wird eine Aktualisierung auf diese Version nicht empfohlen.

* **Mindestversion von `aemanalyser-maven-plugin`:**
Aktualisieren Sie die Verwendung von `aemanalyser-maven-plugin` auf Version 1.6.16 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

* **Mindestversion von `maven-bundle-plugin`:**
Aktualisieren Sie die Verwendung von `maven-bundle-plugin` auf Version 5.1.5 oder höher, um die Unterstützung für neuere JVM-Laufzeiten sicherzustellen.

  Version 6 oder höher ist nicht mit Java 11 oder niedriger kompatibel. Daher wird eine Aktualisierung auf diese Version nicht empfohlen.

* **Aktualisieren von Abhängigkeiten in `maven-scr-plugin`:**
Die `maven-scr-plugin` ist nicht direkt mit Java 21 oder Java 17 kompatibel. Es können jedoch Deskriptordateien generiert werden, indem die Version der ASM-Abhängigkeit in der Plug-in-Konfiguration aktualisiert wird, wie im folgenden Beispiel dargestellt:

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

Konfigurieren Sie den Build-Prozess basierend auf Informationen zum Programm oder zur Pipeline.

Wenn beispielsweise die JavaScript-Minimierung zur Build-Zeit mithilfe eines Tools wie gulp erfolgt, werden für verschiedene Umgebungen verschiedene Minimierungsstufen bevorzugt. Ein Entwicklungs-Build verwendet im Vergleich zu Staging und Produktion eine niedrigere Minimierungsstufe.

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

Ihr Build-Prozess erfordert bestimmte Konfigurationsvariablen, die nicht im Git-Repository gespeichert sind. Darüber hinaus müssen Sie diese Variablen zwischen Pipeline-Ausführungen anpassen, indem Sie dieselbe Verzweigung verwenden.

Weitere Informationen finden Sie unter [Konfigurieren von Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).

## Installieren zusätzlicher Systempakete {#installing-additional-system-packages}

Einige Builds erfordern zusätzliche Systempakete, um vollständig zu funktionieren. Beispielsweise ruft ein Build ein Python- oder Ruby-Skript auf und muss über einen entsprechenden Sprach-Interpreter verfügen. Dieser Installationsprozess kann durch einen Aufruf von [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) in Ihrer `pom.xml` gesteuert werden, um APT aufzurufen. Diese Ausführung ist in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen. In diesem Beispiel wird Python installiert.

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
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es nicht in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein Systempaket in der AEM-Umgebung installieren möchten, wenden Sie sich an den Adobe-Support.

>[!TIP]
>
>Weitere Informationen zur Frontend-Build-Umgebung finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
