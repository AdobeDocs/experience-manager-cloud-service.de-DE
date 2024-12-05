---
title: Build-Umgebung von Cloud Manager
description: Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 7b9b9f3b957b27812c4a7e8f2dbcf96d8786b73e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Build-Umgebung {#build-environment}

Erfahren Sie mehr über die Build-Umgebung von Cloud Manager und darüber, wie sie den Code erstellt und testet.

## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung.

* Die Build-Umgebung ist Linux-basiert und von Ubuntu 22.04 abgeleitet.
* Apache Maven 3.9.4 ist installiert.
   * Adobe empfiehlt Benutzenden, [ihre Maven-Repositorys zu aktualisieren, um HTTPS anstelle von HTTP zu verwenden](#https-maven).
* Die installierten Java-Versionen sind Oracle JDK 11.0.22, Oracle JDK 17.0.10 und Oracle JDK 21.0.4.
* **WICHTIG:** Standardmäßig ist die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk1.8.0_401` eingestellt, die Oracle JDK 8u401 enthält. ***Dieser Standard sollte für AEM Cloud-Projekte überschrieben werden, damit JDK 21 (empfohlen), 17 oder 11*** verwendet wird. Weitere Einzelheiten finden Sie im Abschnitt [Einstellen der Maven JDK-Version](#alternate-maven-jdk-version).
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

### Verwenden einer bestimmten Java-Version {#using-java-support}

Der Cloud Manager-Build-Prozess verwendet das Oracle 8 JDK, um standardmäßig Projekte zu erstellen. AEM Cloud Service-Kunden sollten jedoch die Maven-Ausführungs-JDK-Version auf 21 (empfohlen), 17 oder 11 festlegen.

#### Einstellen der Maven-JDK-Version {#alternate-maven-jdk-version}

Adobe empfiehlt, die JDK-Version der Maven-Ausführung in einer `.cloudmanager/java-version` -Datei auf `21` oder `17` festzulegen.

Erstellen Sie dazu eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Bearbeiten Sie die Datei so, dass sie nur den Text, `21` oder `17` enthält. Cloud Manager akzeptiert zwar auch den Wert `8`, jedoch wird diese Version nicht mehr für AEM Cloud Service-Projekte unterstützt. Alle anderen Werte werden ignoriert. Wenn `21` oder `17` angegeben ist, wird Oracle Java 21 oder Oracle Java 17 verwendet und die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk-21` oder `/usr/lib/jvm/jdk-17` gesetzt.

#### Voraussetzungen für die Migration zum Erstellen mit Java 21 oder Java 17 {#prereq-for-building}

>[!NOTE]
>
>*Wenn Sie Ihre Anwendung in eine neue Java-Build- und -Laufzeitversion migrieren, sollten Sie diese gründlich in Entwicklungs- und Staging-Umgebungen testen, bevor Sie sie in der Produktion bereitstellen.
>Beachten Sie, dass die folgenden Funktionen noch nicht offiziell mit der Java 21-Laufzeit validiert wurden: [Forms](/help/forms/home.md), [Workflows](/help/sites-cloud/authoring/workflows/overview.md), [Posteingang](/help/sites-cloud/authoring/inbox.md) und [Projekte](/help/sites-cloud/authoring/projects/overview.md). Wenn Ihre Anwendung auf diese Funktionen angewiesen ist, stellen Sie sicher, dass umfassende Tests durchgeführt werden, um die Funktionalität zu überprüfen.*

##### Über einige Übersetzungsfunktionen {#translation-features}

Die folgenden Funktionen funktionieren möglicherweise nicht ordnungsgemäß beim Erstellen mit Java 21 oder Java 17, und Adobe erwartet, dass sie bis Anfang 2025 aufgelöst werden:

* `XLIFF` (XML Localization Interchange File Format) schlägt bei der Verwendung der menschlichen Übersetzung fehl.
* `I18n` (Internationalisierung) handhabt Sprachgebietsschemata Hebräisch (`he`), Indonesisch (`in`) und Jiddisch (`yi`) aufgrund von Änderungen im Locale-Konstruktor in neueren Java-Versionen nicht ordnungsgemäß.

#### Laufzeitanforderungen {#runtime-requirements}

Die Java 21-Laufzeit wird ab Februar 2025 für Builds auf Java 21, Java 17 und Java 11 verwendet. Zur Gewährleistung der Kompatibilität sind folgende Anpassungen erforderlich.

Bibliotheksaktualisierungen können jederzeit angewendet werden, da sie mit älteren Java-Versionen kompatibel bleiben.

* **Mindestversion von `org.objectweb.asm`:**
Aktualisieren Sie die Verwendung von `org.objectweb.asm` auf Version 9.5 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

* **Mindestversion von `org.apache.groovy`:**
Aktualisieren Sie die Verwendung von `org.apache.groovy` auf Version 4.0.22 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

  Dieses Paket kann indirekt durch Hinzufügen von Abhängigkeiten von Dritten wie der AEM Groovy Console eingeschlossen werden.

* **Bearbeiten eines Laufzeitparameters:**
Wenn Sie AEM lokal mit Java 21 ausführen, schlagen die Startskripte (`crx-quickstart/bin/start` oder `crx-quickstart/bin/start.bat`) aufgrund des Parameters `MaxPermSize` fehl. Entfernen Sie als Abhilfe entweder `-XX:MaxPermSize=256M` aus dem Skript oder definieren Sie die Umgebungsvariable `CQ_JVM_OPTS` und legen Sie sie auf `-Xmx1024m -Djava.awt.headless=true` fest.

  Adobe plant, dieses Problem in einer zukünftigen Version zu beheben.

>[!NOTE]
>
>Wenn `.cloudmanager/java-version` auf `21` oder `17` festgelegt ist, wird die Java 21-Laufzeit bereitgestellt. Im Februar oder März 2025 ist die Java 21-Laufzeit für die Bereitstellung für alle Kunden geplant, auch wenn Java 11 zum Erstellen Ihres Codes verwendet wird.

#### Zeitanforderungen erstellen

Die folgenden Anpassungen sind erforderlich, um das Erstellen des Projekts mit Java 21 und Java 17 zu ermöglichen. Sie können jederzeit aktualisiert werden, da sie mit älteren Java-Versionen kompatibel sind.

* **Mindestversion von `bnd-maven-plugin`:**
Aktualisieren Sie die Verwendung von `bnd-maven-plugin` auf Version 6.4.0, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

  Versionen 7 oder höher sind nicht mit Java 11 oder niedriger kompatibel. Daher wird eine Aktualisierung auf diese Version nicht empfohlen.

* **Mindestversion von `aemanalyser-maven-plugin`:**
Aktualisieren Sie die Verwendung von `aemanalyser-maven-plugin` auf Version 1.6.6 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

* **Mindestversion von `maven-bundle-plugin`:**
Aktualisieren Sie die Verwendung von `maven-bundle-plugin` auf Version 5.1.5 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

  Versionen 6 oder höher sind nicht mit Java 11 oder niedriger kompatibel. Daher wird eine Aktualisierung auf diese Version nicht empfohlen.

* **Aktualisieren von Abhängigkeiten in `maven-scr-plugin`:**
Die `maven-scr-plugin` ist nicht direkt mit Java 21 oder Java 17 kompatibel. Deskriptordateien können jedoch durch Aktualisierung der ASM-Abhängigkeitsversion in der Plug-in-Konfiguration generiert werden, wie im folgenden Beispiel gezeigt:

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
