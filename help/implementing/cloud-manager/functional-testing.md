---
title: Funktionstests – Cloud Services
description: Funktionstests – Cloud Services
translation-type: tm+mt
source-git-commit: 3bf7defc9aa36c831e061e7209a765f2d60cfb33
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 89%

---


# Funktionstests {#functional-testing}

Funktionstests werden in zwei Typen eingeteilt:

* Funktionstests für das Produkt
* Benutzerdefinierte Funktionstests
* Benutzerdefinierte Benutzeroberflächentests

## Funktionstests für das Produkt {#product-functional-testing}

Funktionstests für das Produkt sind eine Reihe stabiler HTTP-Integrationstests (ITs) rund um die Kernfunktionalität in AEM (z. B. Authoring und Replikation), die verhindern, dass Kundenänderungen an ihrem Anwendungs-Code bereitgestellt werden, wenn diese Kernfunktionalität verletzt wird.

Funktionstests für das Produkt werden automatisch ausgeführt, wenn ein Kunde neuen Code in Cloud Manager bereitstellt, und können nicht übersprungen werden.

Beispieltests finden Sie unter [Funktionstests für das Produkt](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke).

## Benutzerdefinierte Funktionstests {#custom-functional-testing}

Der Schritt für benutzerdefinierte Funktionstests in der Pipeline ist immer vorhanden und kann nicht übersprungen werden.

Wenn jedoch keine Test-JAR vom Build erzeugt wird, wird der Test standardmäßig erfolgreich durchgeführt.

>[!NOTE]
>Über die Schaltfläche **Protokoll herunterladen** können Sie auf eine ZIP-Datei zugreifen, die die Protokolle für das detaillierte Formular zur Testausführung enthält. Diese Protokolle enthalten nicht die Protokolle des eigentlichen AEM-Laufzeitprozesses – auf diese kann über die reguläre Download- oder Longtail-Protokollfunktionalität zugegriffen werden. Weitere Informationen finden Sie unter [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md).

## Benutzerdefinierte Benutzeroberflächentests {#custom-ui-testing}

Benutzerdefinierte UI-Tests können geschrieben werden und ermöglichen es Kunden, schnell Test-Automatisierungs-Suites zu erstellen, um Web- und mobile Apps zu validieren, die auf AEM basieren.

Weitere Informationen zum Schreiben benutzerdefinierter UI-Tests finden Sie unter [Erstellen von UI-Tests](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html#building-ui-tests).


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

