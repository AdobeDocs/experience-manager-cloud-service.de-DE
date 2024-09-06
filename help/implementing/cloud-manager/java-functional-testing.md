---
title: Java™-Funktionstests
description: Erfahren Sie, wie Sie Java™-Funktionstests für AEM as a Cloud Service schreiben.
exl-id: e014b8ad-ac9f-446c-bee8-adf05a6b4d70
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 99%

---

# Java™-Funktionsprüfung

Erfahren Sie, wie Sie Java™-Funktionstests für AEM as a Cloud Service schreiben.

## Erste Schritte mit Funktionstests {#getting-started-functional-tests}

Nach der Erstellung eines neuen Code-Repositorys in Cloud Manager wird automatisch ein `it.tests`-Ordner mit Beispieltestfällen erstellt.

>[!NOTE]
>
>Wenn Ihr Repository erstellt wurde, bevor Cloud Manager automatisch `it.tests`-Ordner erstellt hat, können Sie die neueste Version auch mit dem [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) erstellen.

Sobald Sie den Inhalt der `it.tests`-Ordner haben, können Sie ihn als Grundlage für Ihre eigenen Tests verwenden und dann:

1. [Entwickeln Sie Ihre Testfälle](#writing-functional-tests).
1. [Führen Sie die Tests lokal aus](#local-test-execution).
1. Übertragen Sie Ihren Code in das Cloud Manager-Repository und führen Sie eine Cloud Manager-Pipeline aus.

## Schreiben von benutzerdefinierten Funktionstests {#writing-functional-tests}

Mit denselben Tools, die Adobe zum Schreiben von Produktfunktionstests verwendet, können Sie auch benutzerdefinierte Funktionstests schreiben. Verwenden Sie die [Produktfunktionstests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub als Beispiel für das Schreiben Ihrer Tests.

Der Code für den benutzerdefinierten Funktionstest ist Java™-Code im Ordner `it.tests` Ihres Projekts. Er sollte eine einzige JAR mit allen Funktionstests erstellen. Wenn der Build mehr als eine Test-JAR erzeugt, ist es nicht bestimmbar, welche JAR ausgewählt wird. Wenn keine Test-JARs erzeugt werden, ist der Testschritt standardmäßig bestanden. [Siehe den AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) für Beispieltests.

Die Tests werden auf der von Adobe verwalteten Testinfrastruktur ausgeführt, die mindestens zwei Authoring-Instanzen, zwei Publishing-Instanzen und eine Dispatcher-Konfiguration umfasst. Dieses Setup bedeutet, dass Ihre benutzerdefinierten Funktionstests für den gesamten AEM-Stapel ausgeführt werden.

### Struktur von Funktionstests {#functional-tests-structure}

Benutzerdefinierte Funktionstests müssen als separate JAR-Datei verpackt werden, die mit demselben Maven-Build erstellt wird wie die Artefakte, die in AEM bereitgestellt werden sollen. Im Allgemeinen ist dieser Build ein separates Maven-Modul. Die resultierende JAR-Datei muss alle erforderlichen Abhängigkeiten enthalten und wird im Allgemeinen mithilfe des `maven-assembly-plugin` mit dem Deskriptor `jar-with-dependencies` erstellt.

Darüber hinaus muss für die JAR-Datei der `Cloud-Manager-TestType`-Manifest-Header auf `integration-test`eingestellt sein.

Im Folgenden wird eine Beispielkonfiguration für das `maven-assembly-plugin` gezeigt.

```XML
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
</build>
```

Innerhalb dieser JAR-Datei müssen die Klassennamen der tatsächlich auszuführenden Tests in `IT` enden.

Beispielsweise würde eine Klasse mit dem Namen `com.myco.tests.aem.it.ExampleIT` ausgeführt, eine Klasse mit dem Namen `com.myco.tests.aem.it.ExampleTest` jedoch nicht.

Um Test-Code von der Abdeckungsprüfung des Code-Scans auszuschließen, muss der Test-Code unterhalb eines Pakets mit dem Namen `it` liegen (der Filter für den Abdeckungsausschluss lautet `**/it/**/*.java`).

Die Testklassen müssen normale JUnit-Tests sein. Die Testinfrastruktur ist so konzipiert und konfiguriert, dass sie mit den Konventionen der Testbibliothek von `aem-testing-clients` kompatibel ist. Entwicklerinnen und Entwicklern wird dringend empfohlen, diese Bibliothek zu verwenden und ihre Best Practices zu befolgen.

Weitere Informationen finden Sie im [`aem-testing-clients`GitHub-Repository](https://github.com/adobe/aem-testing-clients).

>[!TIP]
>
>[In diesem Video](https://www.youtube.com/watch?v=yJX6r3xRLHU) erfahren Sie, wie Sie mit benutzerdefinierten Funktionstests das Vertrauen in Ihre CI/CD-Pipelines verbessern können.

### Voraussetzungen {#prerequisites}

1. Die Tests in Cloud Manager werden von technischen Admins ausgeführt.

>[!NOTE]
>
>Erstellen Sie für die Ausführung der Funktionstests von Ihrem lokalen Computer aus eine Benutzerin oder einen Benutzer mit Admin-ähnlichen Berechtigungen, um dasselbe Verhalten zu erzielen.

1. Die Container-Infrastruktur, die für Funktionstests genutzt wird, ist durch die folgenden Grenzen begrenzt:


| Typ | Wert | Beschreibung |
|----------------------|-------|--------------------------------------------------------------------|
| CPU | 0.5 | Menge an CPU-Zeit, die pro Testausführung reserviert wird |
| Arbeitsspeicher | 0,5 Gi | Menge des für den Test zugewiesenen Speichers, Wert in Gibibytes |
| Zeitüberschreitung | 30 min | Die Dauer, nach der der Test beendet wird. |
| Empfohlene Dauer | 15 min | Adobe empfiehlt, Tests so zu schreiben, dass sie diese Dauer nicht überschreiten. |

>[!NOTE]
>
> Wenn Sie weitere Ressourcen benötigen, erstellen Sie einen Fall für die Kundenunterstützung und beschreiben Sie Ihren Anwendungsfall. Das Adobe-Team prüft Ihre Anfrage und leistet angemessene Unterstützung.

#### Abhängigkeiten

* aem-cloud-testing-clients:

Bevorstehende Änderungen an der Container-Infrastruktur, die zum Ausführen von Funktionstests verwendet wird, erfordern die Aktualisierung der Bibliothek [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients), die in Ihrem benutzerdefinierten Funktionstest verwendet wird, auf mindestens Version **1.2.1**
Stellen Sie sicher, dass Ihre Abhängigkeit in `it.tests/pom.xml` aktualisiert wurde.

```
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

>[!NOTE]
>
>Diese Änderung muss vor dem 6. April 2024 vorgenommen werden.
>Wenn die Abhängigkeitsbibliothek nicht aktualisiert wird, treten Pipeline-Fehler beim Schritt „Benutzerdefinierte Funktionstests“ auf.

### Lokale Testausführung {#local-test-execution}

Vor der Aktivierung von Funktionstests in einer Cloud Manager-Pipeline wird empfohlen, die Funktionstests lokal mit dem [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) oder einer tatsächlichen AEM as a Cloud Service-Instanz auszuführen.

#### Ausführung in einer IDE {#running-in-an-ide}

Da es sich bei den Testklassen um JUnit-Tests handelt, können sie von standardmäßigen Java™-IDEs wie Eclipse, IntelliJ und NetBeans ausgeführt werden. Da sowohl die Produktfunktionstests als auch die benutzerdefinierten Funktionstests auf der gleichen Technologie basieren, können beide lokal ausgeführt werden, indem die Produkttests in die benutzerdefinierten Tests kopiert werden.

Wenn diese Tests ausgeführt werden, müssen jedoch verschiedene Systemeigenschaften festgelegt werden, die von der Bibliothek von `aem-testing-clients` (und den zugrundeliegenden Sling Testing Clients) erwartet werden.

Die Systemeigenschaften lauten wie folgt.

| Eigenschaft | Beschreibung | Beispiel |
|-------------------------------------|------------------------------------------------------------------|-------------------------|
| `sling.it.instances` | Anzahl der Instanzen, sollte zur Übereinstimmung mit dem Cloud-Service auf `2` gesetzt werden | `2` |
| `sling.it.instance.url.1` | sollte auf die Author-URL gesetzt werden | `http://localhost:4502` |
| `sling.it.instance.runmode.1` | Ausführungsmodus der ersten Instanz, sollte auf `author` gesetzt werden | `author` |
| `sling.it.instance.adminUser.1` | sollte auf die Autoren-Admin-Benutzenden gesetzt werden. | `admin` |
| `sling.it.instance.adminPassword.1` | sollte auf das Adminpasswort des Autors oder der Autorin gesetzt werden. |                         |
| `sling.it.instance.url.2` | sollte auf die Veröffentlichungs-URL gesetzt werden | `http://localhost:4503` |
| `sling.it.instance.runmode.2` | Ausführungsmodus der zweiten Instanz, sollte auf `publish` gesetzt werden | `publish` |
| `sling.it.instance.adminUser.2` | sollte auf die Veröffentlichungs-Admin-Benutzenden gesetzt werden. | `admin` |
| `sling.it.instance.adminPassword.2` | sollte auf das Veröffentlichungs-Admin-Passwort gesetzt werden. |                         |



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

