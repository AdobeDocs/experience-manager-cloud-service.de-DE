---
title: Funktionstests
description: Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den AEM as a Cloud Service Implementierungsprozess integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: a936f056685f2233a272b4b3105d845f832d143c
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 21%

---


# Funktionstests {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Funktionstests"
>abstract="Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den AEM as a Cloud Service Implementierungsprozess integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen."

Lernen Sie die drei verschiedenen Arten von Funktionstests kennen, die in der [as a Cloud Service Bereitstellung AEM](/help/implementing/cloud-manager/deploy-code.md) um die Qualität und Zuverlässigkeit Ihres Codes zu gewährleisten.

## Übersicht {#overview}

Es gibt drei verschiedene Arten von Funktionstests in AEM as a Cloud Service.

* [Funktionstests für das Produkt](#product-functional-testing)
* [Benutzerdefinierte Funktionstests](#custom-functional-testing)
* [Benutzerdefinierte Benutzeroberflächentests](#custom-ui-testing)

Für alle Funktionstests können die detaillierten Testergebnisse als `.zip` mithilfe der **Build-Protokoll herunterladen** -Schaltfläche im Bildschirm mit der Build-Übersicht [Bereitstellungsprozess.](/help/implementing/cloud-manager/deploy-code.md)

Diese Protokolle enthalten nicht die Protokolle des eigentlichen AEM-Laufzeitprozesses. Informationen zum Zugriff auf diese Protokolle finden Sie im Dokument . [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md) für weitere Details.

Sowohl Produktfunktionstests als auch benutzerdefinierte Funktionstests basieren auf dem [AEM Testen von Clients.](https://github.com/adobe/aem-testing-clients)

## Funktionstests für das Produkt {#product-functional-testing}

Produktfunktionstests sind eine Reihe stabiler HTTP-Integrationstests (ITs) mit Kernfunktionen in AEM wie Authoring- und Replikationsaufgaben. Diese Tests werden von Adobe verwaltet und sollen verhindern, dass Änderungen am benutzerdefinierten Anwendungscode bereitgestellt werden, wenn dies die Kernfunktionalität beeinträchtigt.

Produktfunktionstests werden automatisch ausgeführt, wenn Sie neuen Code in Cloud Manager bereitstellen, und können nicht übersprungen werden.

Produktfunktionstests werden als Open-Source-Projekt verwaltet. Siehe [Produktfunktionstests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub .

## Benutzerdefinierte Funktionstests {#custom-functional-testing}

Während Produktfunktionstests durch Adobe definiert werden, können Sie Ihre eigenen Qualitätstests für Ihre eigene Anwendung schreiben. Dies wird als benutzerdefinierter Funktionstest im Rahmen der Produktions-Pipeline ausgeführt, um die Qualität Ihrer Anwendung sicherzustellen.

Benutzerdefinierte Funktionstests werden sowohl für Implementierungen mit benutzerdefiniertem Code als auch für Push-Upgrades ausgeführt. Dies ist besonders wichtig, um gute Funktionstests zu schreiben, die verhindern, dass AEM Code-Änderungen Ihren Anwendungscode beschädigen. Der benutzerdefinierte Funktionstestschritt ist immer vorhanden und kann nicht übersprungen werden.

### Schreiben benutzerdefinierter Funktionstests {#writing-functional-tests}

Die gleichen Tools, die Adobe zum Schreiben von Produktfunktionstests verwendet, können zum Schreiben Ihrer benutzerdefinierten Funktionstests verwendet werden. Verwenden Sie die [Produktfunktionstests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub als Beispiel für das Schreiben Ihrer Tests.

Der Code für den benutzerdefinierten Funktionstest ist Java-Code im `it.tests` Ordner Ihres Projekts. Es sollte eine einzige JAR mit allen Funktionstests erstellen. Wenn der Build mehr als eine Test-JAR-Datei erzeugt, ist die JAR-Datei nicht deterministisch. Wenn keine Test-JARs erzeugt werden, ist der Testschritt standardmäßig bestanden. [Siehe AEM Projektarchetyp .](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) für Beispieltests.

Die Tests werden in einer von der Adobe gepflegten Testinfrastruktur ausgeführt, die mindestens zwei Autoreninstanzen, zwei Veröffentlichungsinstanzen und eine Dispatcher-Konfiguration umfasst. Dies bedeutet, dass Ihre benutzerdefinierten Funktionstests mit dem gesamten AEM ausgeführt werden.

Benutzerdefinierte Funktionstests müssen als separate JAR-Datei verpackt werden, die vom selben Maven-Build wie die Artefakte erstellt wird, die AEM bereitgestellt werden sollen. Im Allgemeinen wäre dies ein separates Maven-Modul. Die resultierende JAR-Datei muss alle erforderlichen Abhängigkeiten enthalten und wird im Allgemeinen mithilfe der `maven-assembly-plugin` mithilfe der `jar-with-dependencies` Deskriptor.

Darüber hinaus muss die JAR-Datei über die `Cloud-Manager-TestType` Manifest-Header auf `integration-test`.

Im Folgenden finden Sie ein Beispiel für eine Konfiguration für die `maven-assembly-plugin`.

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

Die Testklassen müssen normale JUnit-Tests sein. Die Testinfrastruktur ist so konzipiert und konfiguriert, dass sie mit den Konventionen kompatibel ist, die von der `aem-testing-clients` Testbibliothek. Entwicklern wird dringend empfohlen, diese Bibliothek zu verwenden und ihre Best Practices zu befolgen.

Weitere Informationen finden Sie unter [`aem-testing-clients` GitHub-Repository](https://github.com/adobe/aem-testing-clients) für weitere Details.

>[!TIP]
>
>[Video ansehen](https://www.youtube.com/watch?v=yJX6r3xRLHU) darüber, wie Sie benutzerdefinierte Funktionstests verwenden können, um Ihr Vertrauen in Ihre CI/CD-Pipelines zu verbessern.

## Benutzerdefinierte Benutzeroberflächentests {#custom-ui-testing}

Benutzerdefinierte UI-Tests sind eine optionale Funktion, mit der Sie Benutzeroberflächentests für Ihre Anwendungen erstellen und automatisch ausführen können. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen).

Weitere Informationen finden Sie im Dokument . [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) für weitere Informationen.

## Lokale Testausführung {#local-test-execution}

Da es sich bei Testklassen um JUnit-Tests handelt, können sie von standardmäßigen Java-IDEs wie Eclipse, IntelliJ, NetBeans usw. ausgeführt werden. Da sowohl Funktionstests als auch benutzerdefinierte Funktionstests auf derselben Technologie basieren, können beide lokal ausgeführt werden, indem die Produkttests in Ihre benutzerdefinierten Tests kopiert werden.

Beim Ausführen dieser Tests müssen jedoch verschiedene Systemeigenschaften festgelegt werden, die von der `aem-testing-clients` (und der zugrunde liegenden Sling Testing Clients)-Bibliothek.

Die Systemeigenschaften lauten wie folgt.

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, e.g. admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the author URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`
