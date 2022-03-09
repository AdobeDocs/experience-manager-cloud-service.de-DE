---
title: Funktionstests
description: Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den AEM as a Cloud Service Implementierungsprozess integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 15de47e28e804fd84434d5e8e5d2fe8fe6797241
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 20%

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

Für alle Funktionstests können die detaillierten Testergebnisse als `.zip` mithilfe der **Build-Protokoll herunterladen** -Schaltfläche im Bildschirm mit der Build-Übersicht [Bereitstellungsprozess.](/help/implementing/cloud-manager/deploy-code.md) Diese Protokolle enthalten nicht die Protokolle des eigentlichen AEM-Laufzeitprozesses. Informationen zum Zugriff auf diese Protokolle finden Sie im Dokument . [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md) für weitere Details.

## Funktionstests für das Produkt {#product-functional-testing}

Produktfunktionstests sind eine Reihe stabiler HTTP-Integrationstests (ITs) mit Kernfunktionen in AEM wie Authoring- und Replikationsaufgaben. Diese Tests verhindern, dass Kundenänderungen an benutzerdefiniertem Anwendungs-Code bereitgestellt werden, wenn dies die Kernfunktionalität beeinträchtigt.

Produktfunktionstests werden automatisch ausgeführt, wenn Sie neuen Code in Cloud Manager bereitstellen, und können nicht übersprungen werden.

Siehe [Produktfunktionstests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub für Beispieltests.

## Benutzerdefinierte Funktionstests {#custom-functional-testing}

Benutzerdefinierte funktionstests in der Pipeline sind immer vorhanden und können nicht übersprungen werden.

Der Build sollte entweder null oder eine Test-JARs generieren. Wenn keine Test-JARs erzeugt werden, wird der Testschritt standardmäßig durchgeführt. Wenn der Build mehr als eine Test-JARs erzeugt, ist die JAR-Datei nicht deterministisch.

### Schreiben von Funktionstests {#writing-functional-tests}

Benutzerdefinierte Funktionstests müssen als separate JAR-Datei verpackt werden, die vom selben Maven-Build wie die Artefakte erstellt wird, die AEM bereitgestellt werden sollen. Im Allgemeinen wäre dies ein separates Maven-Modul. Die resultierende JAR-Datei muss alle erforderlichen Abhängigkeiten enthalten und wird im Allgemeinen mithilfe der `maven-assembly-plugin` mithilfe der `jar-with-dependencies` Deskriptor.

Darüber hinaus muss die JAR-Datei über die `Cloud-Manager-TestType` Manifest-Header auf `integration-test`. In Zukunft werden voraussichtlich weitere Header-Werte unterstützt.

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

Innerhalb dieser JAR-Datei müssen die Klassennamen der tatsächlichen Tests, die ausgeführt werden sollen, in `IT`.

Beispielsweise eine Klasse mit dem Namen `com.myco.tests.aem.it.ExampleIT` ausgeführt werden, aber eine Klasse mit dem Namen `com.myco.tests.aem.it.ExampleTest` nicht.

Außerdem muss der Testcode unterhalb eines Pakets mit dem Namen `it` (Der Filter zum Ausschluss der Abdeckung ist `**/it/**/*.java`).

Die Testklassen müssen normale JUnit-Tests sein. Die Testinfrastruktur ist so konzipiert und konfiguriert, dass sie mit den Konventionen kompatibel ist, die von der `aem-testing-clients` Testbibliothek. Entwicklern wird dringend empfohlen, diese Bibliothek zu verwenden und ihre Best Practices zu befolgen.

Weitere Informationen finden Sie unter [`aem-testing-clients` GitHub-Repository](https://github.com/adobe/aem-testing-clients) für weitere Details.

## Benutzerdefinierte Benutzeroberflächentests {#custom-ui-testing}

Benutzerdefinierte UI-Tests sind eine optionale Funktion, mit der Sie Benutzeroberflächentests für Ihre Anwendungen erstellen und automatisch ausführen können. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen).

Weitere Informationen finden Sie im Dokument . [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) für weitere Informationen.

## Lokale Testausführung {#local-test-execution}

Da es sich bei Testklassen um JUnit-Tests handelt, können sie von standardmäßigen Java-IDEs wie Eclipse, IntelliJ, NetBeans usw. ausgeführt werden.

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
