---
title: Java&trade; Funktionstests
description: Erfahren Sie, wie Sie Java&trade schreiben. Funktionstests für AEM as a Cloud Service
exl-id: e449a62a-c8ad-4d39-a170-abacdda3f1b1
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 59%

---

# Java™-Funktionstests

Erfahren Sie, wie Sie Java™-Funktionstests für AEM as a Cloud Service schreiben.

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

Der Code für den benutzerdefinierten Funktionstest ist Java™-Code im `it.tests` Ordner Ihres Projekts. Er sollte eine einzige JAR mit allen Funktionstests erstellen. Wenn der Build mehr als eine Test-JAR erzeugt, ist es nicht bestimmbar, welche JAR ausgewählt wird. Wenn keine Test-JARs erzeugt werden, ist der Testschritt standardmäßig bestanden. [Siehe den AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) für Beispieltests.

Die Tests werden in einer von der Adobe gepflegten Testinfrastruktur ausgeführt, die mindestens zwei Autoreninstanzen, zwei Veröffentlichungsinstanzen und eine Dispatcher-Konfiguration umfasst. Diese Konfiguration bedeutet, dass Ihre benutzerdefinierten Funktionstests für den gesamten AEM ausgeführt werden.

### Struktur von Funktionstests {#functional-tests-structure}

Benutzerdefinierte Funktionstests müssen als separate JAR-Datei gepackt werden, die mit demselben Maven-Build erstellt wird wie die Artefakte, die in AEM bereitgestellt werden sollen. Im Allgemeinen wäre dieser Build ein separates Maven-Modul. Die resultierende JAR-Datei muss alle erforderlichen Abhängigkeiten enthalten und wird im Allgemeinen mithilfe des `maven-assembly-plugin` mit dem Deskriptor `jar-with-dependencies` erstellt.

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

Die Testklassen müssen normale JUnit-Tests sein. Die Testinfrastruktur ist so konzipiert und konfiguriert, dass sie mit den Konventionen der Testbibliothek von `aem-testing-clients` kompatibel ist. Entwicklern wird empfohlen, diese Bibliothek zu verwenden und die Best Practices zu befolgen.

Siehe [`aem-testing-clients` GitHub-Repository](https://github.com/adobe/aem-testing-clients) für weitere Details.

>[!TIP]
>
>[In diesem Video](https://www.youtube.com/watch?v=yJX6r3xRLHU) erfahren Sie, wie Sie mit benutzerdefinierten Funktionstests das Vertrauen in Ihre CI/CD-Pipelines verbessern können.

### Voraussetzungen {#prerequisites}

1. Die Tests in Cloud Manager werden von einem technischen Administrator ausgeführt.

>[!NOTE]
>
>Erstellen Sie für die Ausführung der Funktionstests von Ihrem lokalen Computer aus eine Benutzerin oder einen Benutzer mit Admin-ähnlichen Berechtigungen, um dasselbe Verhalten zu erzielen.

1. Die Container-Infrastruktur, die für Funktionstests genutzt wird, ist durch die folgenden Grenzen begrenzt:


| Typ | Wert | Beschreibung |
|----------------------|-------|--------------------------------------------------------------------|
| CPU | 0.5 | CPU-Zeit pro Testausführung reserviert |
| Arbeitsspeicher | 0,5 Gi | Menge des dem Test zugewiesenen Speichers, Wert in Byte |
| Zeitüberschreitung | 30 M | Die Dauer, nach der der Test beendet wird. |
| Empfohlene Dauer | 15 M | Adobe empfiehlt, die Tests nicht länger als diese Zeit zu schreiben. |

>[!NOTE]
>
> Wenn Sie weitere Ressourcen benötigen, erstellen Sie einen Fall für die Kundenunterstützung und beschreiben Sie Ihren Anwendungsfall. Das Team der Adobe prüft Ihre Anfrage und leistet angemessene Unterstützung.


### Lokale Testausführung {#local-test-execution}

Vor der Aktivierung von Funktionstests in einer Cloud Manager-Pipeline wird empfohlen, die Funktionstests lokal mit dem [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) oder einer tatsächlichen AEM as a Cloud Service-Instanz auszuführen.

#### Ausführung in einer IDE {#running-in-an-ide}

Da es sich bei Testklassen um JUnit-Tests handelt, können sie von standardmäßigen Java™-IDEs wie Eclipse, IntelliJ und NetBeans ausgeführt werden. Da sowohl die Produktfunktionstests als auch die benutzerdefinierten Funktionstests auf der gleichen Technologie basieren, können beide lokal ausgeführt werden, indem die Produkttests in die benutzerdefinierten Tests kopiert werden.

Beim Ausführen dieser Tests müssen jedoch verschiedene Systemeigenschaften festgelegt werden, die von der `aem-testing-clients` (und der zugrunde liegenden Sling Testing Clients)-Bibliothek.

Die Systemeigenschaften lauten wie folgt.

| Eigenschaft | Beschreibung | Beispiel |
|-------------------------------------|------------------------------------------------------------------|-------------------------|
| `sling.it.instances` | Anzahl der Instanzen, die mit dem Cloud-Service übereinstimmen, sollte auf `2` | `2` |
| `sling.it.instance.url.1` | sollte auf die Autoren-URL eingestellt sein | `http://localhost:4502` |
| `sling.it.instance.runmode.1` | Ausführungsmodus der ersten Instanz, sollte auf `author` | `author` |
| `sling.it.instance.adminUser.1` | sollte auf den Autoren-Admin-Benutzer festgelegt werden. | `admin` |
| `sling.it.instance.adminPassword.1` | sollte auf das Administratorkennwort des Autors festgelegt werden. |                         |
| `sling.it.instance.url.2` | auf die Veröffentlichungs-URL eingestellt werden | `http://localhost:4503` |
| `sling.it.instance.runmode.2` | Ausführungsmodus der zweiten Instanz, sollte auf `publish` | `publish` |
| `sling.it.instance.adminUser.2` | sollte auf den Veröffentlichungs-Admin-Benutzer festgelegt werden. | `admin` |
| `sling.it.instance.adminPassword.2` | sollte auf das Veröffentlichungs-Admin-Kennwort festgelegt werden. |                         |



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
