---
title: Funktionstests
description: Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den Implementierungsprozess von AEM as a Cloud Service integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: cd0b40ffa54eac0d7488b23329c4d2666c992da7
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 94%

---


# Funktionstests {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Funktionstests"
>abstract="Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den Implementierungsprozess von AEM as a Cloud Service integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen."

Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den [Implementierungsprozess von AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md) integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.

## Übersicht {#overview}

Es gibt drei verschiedene Arten von Funktionstests in AEM as a Cloud Service.

* [Funktionstests für das Produkt](#product-functional-testing)
* [Benutzerdefinierte Funktionstests](#custom-functional-testing)
* [Benutzerdefinierte Benutzeroberflächentests](#custom-ui-testing)

Für alle Funktionstests können die detaillierten Ergebnisse der Tests als `.zip`-Datei heruntergeladen werden, indem Sie im Build-Übersichtsbildschirm als Teil des [Implementierungsprozesses](/help/implementing/cloud-manager/deploy-code.md) die Schaltfläche **Build-Protokoll herunterladen** verwenden.

Diese Protokolle enthalten nicht die Protokolle des eigentlichen AEM-Laufzeitprozesses. Um auf diese Protokolle zuzugreifen, lesen Sie bitte das Dokument [Zugriff auf und Verwaltung von Protokollen](/help/implementing/cloud-manager/manage-logs.md). Dort erfahren Sie weitere Einzelheiten.

Sowohl die Produktfunktionstests als auch die benutzerdefinierten Funktionstests basieren auf den [AEM Testing Clients.](https://github.com/adobe/aem-testing-clients)

### Funktionstests für das Produkt {#product-functional-testing}

Produktfunktionstests sind eine Reihe stabiler HTTP-Integrationstests (ITs) mit Kernfunktionen in AEM wie Authoring- und Replikationsaufgaben. Diese Tests werden von Adobe verwaltet und sollen verhindern, dass Änderungen am benutzerdefinierten Anwendungscode implementiert werden, wenn sie die Kernfunktionen beeinträchtigen.

* [Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md): Produktfunktionstests werden automatisch ausgeführt, wenn Sie neuen Code in Cloud Manager bereitstellen, und können nicht übersprungen werden.
* [Nicht-Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md): Produktfunktionstests können optional zum Ausführen ausgewählt werden, wenn Sie Ihre produktionsfremde Pipeline ausführen.

Produktfunktionstests werden als Open-Source-Projekt verwaltet. Einzelheiten finden Sie in den [Produktfunktionstests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub.

### Benutzerdefinierte Funktionstests {#custom-functional-testing}

Während die Produktfunktionstests von Adobe definiert werden, können Sie Ihre eigenen Qualitätstests für Ihr eigenes Programm schreiben. Dies wird als benutzerdefinierter Funktionstest im Rahmen der [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) oder optional [produktionsfremde Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) , um die Qualität Ihrer Anwendung sicherzustellen.

Benutzerdefinierte Funktionstests werden sowohl für benutzerdefinierte Code-Implementierungen als auch für Push-Upgrades durchgeführt. Daher ist es besonders wichtig, gute Funktionstests zu schreiben, die verhindern, dass AEM-Code-Änderungen Ihren Programm-Code beschädigen. Der Schritt für benutzerdefinierte Funktionstests ist immer vorhanden und kann nicht übersprungen werden.

### Benutzerdefinierte Benutzeroberflächentests {#custom-ui-testing}

Die Testfunktion für die benutzerdefinierte Benutzeroberfläche ist eine optionale Funktion, mit der man Benutzeroberflächentests für Anwendungen erstellen und automatisch ausführen kann. Benutzeroberflächentests sind Selenium-basierte Tests, die in einer Docker-Grafik verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen, z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen.

Weitere Informationen finden Sie in dem Dokument [Tests von benutzerdefinierten Benutzeroberflächen](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing)

## Erste Schritte mit Funktionstests {#getting-started-functional-tests}

Nach der Erstellung eines neuen Code-Repositorys in Cloud Manager wird automatisch ein `it.tests`-Ordner mit Beispieltestfällen erstellt.

>[!NOTE]
>
>Wenn Ihr Repository erstellt wurde, bevor Cloud Manager automatisch `it.tests`-Ordner erstellt hat, können Sie die neueste Version auch mit dem [AEM-Projekt-Archetyp](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) erstellen.

Sobald Sie den Inhalt der `it.tests`-Ordner haben, können Sie ihn als Grundlage für Ihre eigenen Tests verwenden und dann:

1. [Entwickeln Sie Ihre Testfälle.](#writing-functional-tests)
1. [Führen Sie die Tests lokal aus.](#local-test-execution)
1. Übertragen Sie Ihren Code in das Cloud Manager-Repository und führen Sie eine Cloud Manager-Pipeline aus.

## Schreiben von benutzerdefinierten Funktionstests {#writing-functional-tests}

Mit denselben Tools, die Adobe zum Schreiben von Produktfunktionstests verwendet, können Sie auch benutzerdefinierte Funktionstests schreiben. Verwenden Sie die [Produktfunktionstests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub als Beispiel für das Schreiben Ihrer Tests.

Der Code für den benutzerdefinierten Funktionstest ist Java-Code im Ordner `it.tests` Ihres Projekts. Er sollte eine einzige JAR mit allen Funktionstests erstellen. Wenn der Build mehr als eine Test-JAR erzeugt, ist es nicht bestimmbar, welche JAR ausgewählt wird. Wenn keine Test-JARs erzeugt werden, ist der Testschritt standardmäßig bestanden. [Siehe den AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) für Beispieltests.

Die Tests werden auf der von Adobe verwalteten Testinfrastruktur ausgeführt, die mindestens zwei Autoreninstanzen, zwei Veröffentlichungsinstanzen und eine Dispatcher-Konfiguration umfasst. Das bedeutet, dass Ihre benutzerdefinierten Funktionstests für den gesamten AEM-Stack ausgeführt werden.

### Struktur von Funktionstests {#functional-tests-structure}

Benutzerdefinierte Funktionstests müssen als separate JAR-Datei gepackt werden, die mit demselben Maven-Build erstellt wird wie die Artefakte, die in AEM bereitgestellt werden sollen. Im Allgemeinen wäre dies ein separates Maven-Modul. Die resultierende JAR-Datei muss alle erforderlichen Abhängigkeiten enthalten und wird im Allgemeinen mithilfe des `maven-assembly-plugin` mit dem Deskriptor `jar-with-dependencies` erstellt.

Darüber hinaus muss für die JAR-Datei der `Cloud-Manager-TestType`-Manifest-Header auf `integration-test`eingestellt sein.

Im Folgenden wird eine Beispielkonfiguration für das `maven-assembly-plugin` gezeigt.

```java
<build>
    <plugins>
        <!-- Create self-contained jar with dependencies -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <version>3.1.0</version>
            <configuration>
                <descriptorRefs>
                    <descriptorRef>jar-with-dependencies</descriptorRef>
                </descriptorRefs>
                <archive>
                    <manifestEntries>
                        <Cloud-Manager-TestType>integration-test</Cloud-Manager-TestType>
                    </manifestEntries>
                </archive>
            </configuration>
            <executions>
                <execution>
                    <id>make-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
```

Innerhalb dieser JAR-Datei müssen die Klassennamen der tatsächlich auszuführenden Tests in `IT` enden.

Beispielsweise würde eine Klasse mit dem Namen `com.myco.tests.aem.it.ExampleIT` ausgeführt, eine Klasse mit dem Namen `com.myco.tests.aem.it.ExampleTest` jedoch nicht.

Um Test-Code von der Abdeckungsprüfung des Code-Scans auszuschließen, muss der Test-Code unterhalb eines Pakets mit dem Namen `it` liegen (der Filter für den Abdeckungsausschluss lautet `**/it/**/*.java`).

Die Testklassen müssen normale JUnit-Tests sein. Die Testinfrastruktur ist so konzipiert und konfiguriert, dass sie mit den Konventionen der Testbibliothek von `aem-testing-clients` kompatibel ist. Entwicklern wird dringend empfohlen, diese Bibliothek zu verwenden und ihre Best Practices zu befolgen.

Weitere Details finden Sie im [`aem-testing-clients` GitHub Repo](https://github.com/adobe/aem-testing-clients).

>[!TIP]
>
>[In diesem Video](https://www.youtube.com/watch?v=yJX6r3xRLHU) erfahren Sie, wie Sie mit benutzerdefinierten Funktionstests das Vertrauen in Ihre CI/CD-Pipelines verbessern können.

### Lokale Testausführung {#local-test-execution}

Vor der Aktivierung von Funktionstests in einer Cloud Manager-Pipeline wird empfohlen, die Funktionstests lokal mit dem [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) oder einer tatsächlichen AEM as a Cloud Service-Instanz auszuführen.

#### Voraussetzungen {#prerequisites}

Die Tests in Cloud Manager werden von einem technischen Admin ausgeführt.

Erstellen Sie für die Ausführung der Funktionstests von Ihrem lokalen Computer aus eine Benutzerin oder einen Benutzer mit Admin-ähnlichen Berechtigungen, um dasselbe Verhalten zu erzielen.

#### Ausführung in einer IDE {#running-in-an-ide}

Da es sich bei den Testklassen um JUnit-Tests handelt, können sie von standardmäßigen Java-IDEs wie Eclipse, IntelliJ und NetBeans ausgeführt werden. Da sowohl die Produktfunktionstests als auch die benutzerdefinierten Funktionstests auf der gleichen Technologie basieren, können beide lokal ausgeführt werden, indem die Produkttests in die benutzerdefinierten Tests kopiert werden.

Wenn diese Tests jedoch ausgeführt werden, müssen verschiedene Systemeigenschaften festgelegt werden, die von der Bibliothek der `aem-testing-clients` (und den zugrunde liegenden Sling Testing Clients) erwartet werden.

Die Systemeigenschaften lauten wie folgt.

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, for example, admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the publish URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`

#### Ausführen aller Tests mit Maven {#using-maven}

1. Öffnen Sie eine Shell und navigieren Sie zum Ordner `it.tests` in Ihrem Repository.

1. Führen Sie den folgenden Befehl aus, indem Sie die erforderlichen Parameter angeben, um die Tests mit Maven zu starten.

```shell
mvn verify -Plocal \
    -Dit.author.url=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.author.user=<user> \
    -Dit.author.password=<password> \
    -Dit.publish.url=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.publish.user=<user> \
    -Dit.publish.password=<password>
```
