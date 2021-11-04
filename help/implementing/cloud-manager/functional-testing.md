---
title: Funktionstests – Cloud Services
description: Funktionstests – Cloud Services
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 749daae8825b63dbf5b0101b4cab39730e9b1973
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 93%

---

# Funktionstests {#functional-testing}


>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Funktionstests"
>abstract="Funktionstests sind in drei Typen unterteilt: Produktfunktionstests, benutzerdefinierte Funktionstests und Tests von benutzerdefinierten Benutzeroberflächen"

Funktionstests werden in drei Typen eingeteilt:


* Funktionstests für das Produkt
* Benutzerdefinierte Funktionstests
* Benutzerdefinierte Benutzeroberflächentests

## Funktionstests für das Produkt {#product-functional-testing}

Funktionstests für das Produkt sind eine Reihe stabiler HTTP-Integrationstests (ITs) rund um die Kernfunktionalität in AEM (z. B. Authoring und Replikation), die verhindern, dass Kundenänderungen an ihrem Programm-Code bereitgestellt werden, wenn diese Kernfunktionalität verletzt wird.

Funktionstests für das Produkt werden automatisch ausgeführt, wenn ein Kunde neuen Code in Cloud Manager bereitstellt, und können nicht übersprungen werden.

Beispieltests finden Sie unter [Funktionstests für das Produkt](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke).

## Benutzerdefinierte Funktionstests {#custom-functional-testing}

Der Schritt für benutzerdefinierte Funktionstests in der Pipeline ist immer vorhanden und kann nicht übersprungen werden.

Der Build sollte entweder null oder eine Test-JARs generieren. Wenn keine Test-JARs erzeugt werden, wird der Testschritt standardmäßig durchgeführt. Wenn der Build mehr als eine Test-JARs erzeugt, ist die JAR-Datei nicht deterministisch.

>[!NOTE]
>Über die Schaltfläche **Protokoll herunterladen** können Sie auf eine ZIP-Datei zugreifen, die die Protokolle für das detaillierte Formular zur Testausführung enthält. Diese Protokolle enthalten nicht die Protokolle des eigentlichen AEM-Laufzeitprozesses – auf diese kann über die reguläre Download- oder Longtail-Protokollfunktionalität zugegriffen werden. Weitere Informationen finden Sie unter [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md).

## Benutzerdefinierte Benutzeroberflächentests {#custom-ui-testing}

AEM bietet seinen Kunden eine integrierte Suite mit Cloud Manager-Qualitätstests, um eine reibungslose Aktualisierung ihrer Programme sicherzustellen. Vor allem IT-Tests ermöglichen es Kunden bereits, eigene Tests zu erstellen und zu automatisieren, die AEM-APIs verwenden.

Die Testfunktion der benutzerdefinierten Benutzeroberfläche ist eine [optionale Funktion](#customer-opt-in) damit unsere Kunden Benutzeroberflächentests für ihre Anwendungen erstellen und automatisch ausführen können. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen). Weitere Informationen zum Erstellen von Benutzeroberflächen und zum Schreiben von Benutzeroberflächentests finden Sie hier. Zusätzlich kann ein Benutzeroberflächentest-Projekt einfach mithilfe des AEM-Projektarchetyps erstellt werden.

Die Kunden können (über GIT) benutzerdefinierte Tests und eine Test-Suite für die Benutzeroberfläche erstellen. Der Benutzeroberflächentest wird als Teil eines speziellen Qualitätstests für jede Cloud Manager-Pipeline mit ihren spezifischen Schritt- und Feedback-Informationen ausgeführt. Alle Benutzeroberflächentests, einschließlich Regression und neuer Funktionen, ermöglichen die Erkennung und Meldung von Fehlern im Kundenkontext.

Die Benutzeroberflächentests des Kunden werden automatisch auf der Produktions-Pipeline unter dem Schritt „Benutzerdefinierte Benutzeroberflächentests“ ausgeführt.

Im Gegensatz zu benutzerdefinierten Funktionstests, bei denen es sich um HTTP-Tests handelt, die in Java geschrieben wurden, können die Benutzeroberflächentests ein Docker-Image mit Tests in jeder Sprache sein, sofern sie den unter [Erstellen von Benutzeroberflächentests](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html?lang=de#building-ui-tests) definierten Konventionen entsprechen.

>[!NOTE]
>Es wird empfohlen, die Struktur und Sprache *(js und wdio)* zu verwenden, die im [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) bereitgestellt werden.

### Kunden-Opt-in {#customer-opt-in}

Um Benutzeroberflächentests erstellen und ausführen zu können, müssen sich Kunden per Opt-in anmelden, indem sie eine Datei zu ihrem Code-Repository unter dem maven-Untermodul für Benutzeroberflächentests (neben der Datei pom.xml des Untermoduls für Benutzeroberflächentests) hinzufügen und sicherstellen, dass sich diese Datei im Stammverzeichnis der erstellten Datei befindet.`tar.gz`

*Dateiname*: `testing.properties`

*Inhalt*: `ui-tests.version=1`

Wenn dies nicht in der erstellten Datei `tar.gz` enthalten ist, werden die Erstellung und Ausführung von Benutzeroberflächentests übersprungen.

Um die Datei `testing.properties` im erstellten Artefakt hinzuzufügen, fügen Sie eine `include`-Anweisung in der Datei `assembly-ui-test-docker-context.xml` hinzu (im Untermodul Testen der Benutzeroberfläche):

    ```
    [...]
    &lt;includes>
    &lt;include>Dockerfile&lt;/include>
    &lt;include>wait-for-grid.sh&lt;/include>
    &lt;include>testing.properties&lt;/include> &lt;!- Opt-in-Testmodul in Cloud Manager -->
    &lt;/includes>
    [...]
    ```

>[!NOTE]
>Produktions-Pipelines, die vor dem 10. Februar 2021 erstellt wurden, müssen aktualisiert werden, damit die in diesem Abschnitt beschriebenen Benutzeroberflächentests verwendet werden können. Das bedeutet, dass der Benutzer die Produktions-Pipeline bearbeiten und in der Benutzeroberfläche auf **Speichern** klicken muss, selbst wenn keine Änderungen vorgenommen wurden.
>Weitere Informationen zur Pipeline-Konfiguration finden Sie unter [Konfigurieren Ihrer CI/CD-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=de#using-cloud-manager).

### Schreiben von Funktionstests {#writing-functional-tests}

Vom Kunden geschriebene Funktionstests müssen als separate JAR-Datei verpackt werden, die vom gleichen Maven-Build wie die Artefakte erstellt wird, die in AEM bereitgestellt werden sollen. Im Allgemeinen wäre dies ein separates Maven-Modul. Die resultierende JAR-Datei muss alle erforderlichen Abhängigkeiten enthalten und wird im Allgemeinen mithilfe des maven-assembly-Plug-ins mit dem Deskriptor jar-with-dependencies erstellt.

Darüber hinaus muss für die JAR-Datei der Manifest-Header „Cloud-Manager-TestType“ auf „integration-test“ eingestellt sein. In Zukunft werden voraussichtlich weitere Header-Werte unterstützt. Eine Beispielkonfiguration für das maven-assembly-Plug-in ist:

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

Innerhalb dieser JAR-Datei müssen die Klassennamen der tatsächlich auszuführenden Tests in „IT“ enden.

Beispielsweise würde eine Klasse mit dem Namen `com.myco.tests.aem.ExampleIT` ausgeführt, eine Klasse mit dem Namen `com.myco.tests.aem.ExampleTest` jedoch nicht.

Die Testklassen müssen normale JUnit-Tests sein. Die Testinfrastruktur ist so konzipiert und konfiguriert, dass sie mit den Konventionen der Testbibliothek von aem-testing-clients kompatibel ist. Entwicklern wird dringend empfohlen, diese Bibliothek zu verwenden und ihre Best Practices zu befolgen. Weitere Informationen finden Sie unter [Git-Link](https://github.com/adobe/aem-testing-clients).

### Lokale Testausführung {#local-test-execution}

Da es sich bei den Testklassen um JUnit-Tests handelt, können sie von standardmäßigen Java-IDEs wie Eclipse, IntelliJ, NetBeans usw. ausgeführt werden.

Wenn diese Tests jedoch ausgeführt werden, müssen verschiedene Systemeigenschaften festgelegt werden, die von den aem-testing-clients (und den zugrunde liegenden Sling Testing Clients) erwartet werden.

Die Systemeigenschaften lauten wie folgt:

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, e.g. admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the author URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`
