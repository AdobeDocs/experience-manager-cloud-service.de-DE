---
title: Testen der Benutzeroberfläche – Cloud Services
description: Testen der Benutzeroberfläche – Cloud Services
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 710f156e606902ab5548169661d4a82c8cf4f819
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 93%

---

# Testen der Benutzeroberfläche {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="Testen der Benutzeroberfläche"
>abstract="Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen). Das Docker-Image kann mit Standard-Tools erstellt werden, muss jedoch bei der Ausführung bestimmte Konventionen einhalten. Beim Ausführen des Docker-Images wird automatisch ein Selenium-Server bereitgestellt. Die unten beschriebenen Laufzeitkonventionen ermöglichen es Ihrem Test-Code, sowohl auf den Selenium-Server als auch auf die AEM-Instanzen zuzugreifen, die derzeit getestet werden."

Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen). Das Docker-Image kann mit Standard-Tools erstellt werden, muss jedoch bei der Ausführung bestimmte Konventionen einhalten. Beim Ausführen des Docker-Images wird automatisch ein Selenium-Server bereitgestellt. Die unten beschriebenen Laufzeitkonventionen ermöglichen es Ihrem Test-Code, sowohl auf den Selenium-Server als auch auf die AEM-Instanzen zuzugreifen, die derzeit getestet werden.

>[!NOTE]
> Die vor dem 10. Februar 2021 erstellten Straging- und Produktions-Pipelines müssen aktualisiert werden, damit die auf dieser Seite beschriebenen Benutzeroberflächentests verwendet werden können.
> Siehe [CI/CD-Pipelines in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) Informationen zur Pipelinekonfiguration.

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

Um die Datei `testing.properties` im erstellten Artefakt hinzuzufügen, fügen Sie eine `include`-Anweisung in der Datei `assembly-ui-test-docker-context.xml` hinzu (im Untermodul Testen der Benutzeroberfläche).

>[!NOTE]
>Wenn Ihr Projekt die Zeile nicht enthält, müssen Sie diese Datei bearbeiten, um sich für UI-Tests anmelden zu können. Wenn die Datei eine Zeile enthält, die darauf hinweist, sie nicht zu bearbeiten, ignorieren Sie diese Empfehlung.

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

## Erstellen von Benutzeroberflächentests {#building-ui-tests}

Benutzeroberflächentests werden aus einem Docker-Build-Kontext erstellt, der von einem Maven-Projekt generiert wurde. Cloud Manager verwendet den Docker-Build-Kontext, um ein Docker-Image zu generieren, das die eigentlichen Benutzeroberflächentests enthält. Zusammenfassend lässt sich sagen, dass ein Maven-Projekt einen Docker-Build-Kontext generiert. Im Docker-Build-Kontext wird beschrieben, wie ein Docker-Image mit den Benutzeroberflächentests erstellt wird.

In diesem Abschnitt werden die Schritte beschrieben, die zum Hinzufügen eines Projekts mit Benutzeroberflächentests zum Repository erforderlich sind. Wenn Sie es eilig haben oder keine besonderen Anforderungen an die Programmiersprache haben, kann der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) ein Projekt mit Benutzeroberflächentests für Sie generieren.

### Erstellen eines Docker-Build-Kontexts {#generate-docker-build-context}

Um einen Docker-Build-Kontext zu generieren, benötigen Sie ein Maven-Modul, das:

- ein Archiv erzeugt, das ein `Dockerfile` und jede andere Datei enthält, die zum Erstellen des Docker-Images mit Ihren Tests erforderlich ist.
- das Archiv mit dem `ui-test-docker-context`-Klassifikator markiert.

Die einfachste Möglichkeit, dies zu erreichen, besteht darin, das [Maven Assembly-Plug-in](http://maven.apache.org/plugins/maven-assembly-plugin/) so zu konfigurieren, dass das Docker-Build-Kontextarchiv erstellt und ihm der richtige Klassifikator zugewiesen wird.

Sie können Benutzeroberflächentests mit verschiedenen Technologien und Frameworks erstellen. In diesem Abschnitt wird jedoch davon ausgegangen, dass Ihr Projekt ähnlich wie folgt aufgebaut ist.

```
├── Dockerfile
├── assembly-ui-test-docker-context.xml
├── pom.xml
├── test-module
│   ├── package.json
│   ├── index.js
│   └── wdio.conf.js
└── wait-for-grid.sh
```

Die `pom.xml`-Datei übernimmt den Maven-Build. Fügen Sie dem Maven Assembly-Plug-in eine Ausführung hinzu, die der folgenden ähnelt.

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <configuration>
        <descriptors>
            <descriptor>${project.basedir}/assembly-ui-test-docker-context.xml</descriptor>
        </descriptors>
        <tarLongFileMode>gnu</tarLongFileMode>
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
```

Diese Ausführung weist das Maven Assembly Plug-in an, ein Archiv basierend auf den in `assembly-ui-test-docker-context.xml` enthaltenen Anweisungen zu erstellen, das im Jargon des Plug-ins als „Assembly-Deskriptor“ bezeichnet wird. Der Assembly-Deskriptor listet alle Dateien auf, die Teil des Archivs sein müssen.

```xml
<assembly>
    <id>ui-test-docker-context</id>
    <includeBaseDirectory>false</includeBaseDirectory>
    <formats>
        <format>tar.gz</format>
    </formats>
    <fileSets>
        <fileSet>
            <directory>${basedir}</directory>
            <includes>
                <include>Dockerfile</include>
                <include>wait-for-grid.sh</include>
            </includes>
        </fileSet>
        <fileSet>
            <directory>${basedir}/test-module</directory>
            <excludes>
                <exclude>node/**</exclude>
                <exclude>node_modules/**</exclude>
                <exclude>reports/**</exclude>
            </excludes>
        </fileSet>
    </fileSets>
</assembly>
```

Der Assembly-Deskriptor weist das Plug-in an, ein Archiv des Typs `.tar.gz` zu erstellen, und weist ihm den Klassifikator `ui-test-docker-context` zu. Darüber hinaus werden die Dateien aufgelistet, die im Archiv enthalten sein müssen:

- eine `Dockerfile`, obligatorisch für das Erstellen des Docker-Images.
- das Skript `wait-for-grid.sh`, dessen Zwecke unten beschrieben werden.
- Die eigentlichen Benutzeroberflächentests, die von einem Node.js-Projekt im Ordner `test-module` implementiert wurden.

Der Assembly-Deskriptor schließt auch einige Dateien aus, die beim lokalen Ausführen der Benutzeroberflächentests generiert werden könnten. Dies garantiert ein kleineres Archiv und schnellere Builds.

Das Archiv, das den Docker-Build-Kontext enthält, wird automatisch von Cloud Manager abgerufen, der das Docker-Image mit Ihren Tests während der Bereitstellungs-Pipelines erstellt. Schließlich führt Cloud Manager das Docker-Image aus, um die Benutzeroberflächentests für das Programm auszuführen.

Der Build sollte entweder null oder ein Archiv erzeugen. Wenn kein Archiv erzeugt wird, wird der Testschritt standardmäßig durchgeführt. Wenn der Build mehr als ein Archiv erzeugt, ist das ausgewählte Archiv nicht deterministisch.

## Schreiben von Benutzeroberflächentests {#writing-ui-tests}

In diesem Abschnitt werden die Konventionen beschrieben, denen das Docker-Image mit Ihren Benutzeroberflächentests folgen muss. Das Docker-Image basiert auf dem im vorherigen Abschnitt beschriebenen Docker-Build-Kontext.

### Umgebungsvariablen {#environment-variables}

Die folgenden Umgebungsvariablen werden zur Laufzeit an Ihr Docker-Image übergeben.

| Variable | Beispiele | Beschreibung |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Die URL des Selenium-Servers |
| `SELENIUM_BROWSER` | `chrome`, `firefox` | Die vom Selenium-Server verwendete Browser-Implementierung |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | Die URL der AEM-Autoreninstanz |
| `AEM_AUTHOR_USERNAME` | `admin` | Der Benutzername für die Anmeldung bei der AEM-Autoreninstanz |
| `AEM_AUTHOR_PASSWORD` | `admin` | Das Passwort für die Anmeldung bei der AEM-Autoreninstanz |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | Die URL der AEM-Veröffentlichungsinstanz |
| `AEM_PUBLISH_USERNAME` | `admin` | Der Benutzername für die Anmeldung bei der AEM-Veröffentlichungsinstanz |
| `AEM_PUBLISH_PASSWORD` | `admin` | Das Passwort für die Anmeldung bei der AEM-Veröffentlichungsinstanz |
| `REPORTS_PATH` | `/usr/src/app/reports` | Der Pfad, in dem der XML-Bericht der Testergebnisse gespeichert werden muss |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Die URL, unter der die Datei hochgeladen werden muss, um sie für Selenium zugänglich zu machen |

### Warten auf Selenium {#waiting-for-selenium}

Bevor die Tests beginnen, muss das Docker-Image sicherstellen, dass der Selenium-Server betriebsbereit ist. Das Warten auf den Selenium-Service erfolgt in zwei Schritten:

1. Lesen der URL des Selenium-Service aus der Umgebungsvariablen `SELENIUM_BASE_URL`.
2. Abrufen des von der Selenium-API bereitgestellten [Statusendpunkts](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) in regelmäßigen Abständen.

Sobald der Statusendpunkt von Selenium positiv antwortet, können die Tests beginnen.

### Erstellen der Testberichte {#generate-test-reports}

Das Docker-Image muss Testberichte im JUnit-XML-Format generieren und in dem von der Umgebungsvariablen `REPORTS_PATH` angegebenen Pfad speichern. Das JUnit-XML-Format ist ein weitverbreitetes Format für Testergebnisberichte. Wenn das Docker-Image Java und Maven verwendet, sowohl das [Maven Surefire-Plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) als auch das [Maven Failsafe-Plug-in](https://maven.apache.org/surefire/maven-failsafe-plugin/). Wenn das Docker-Image mit anderen Programmiersprachen oder Testläufern implementiert ist, lesen Sie in der Dokumentation der ausgewählten Tools nach, wie Sie JUnit-XML-Berichte erstellen.

### Dateien hochladen {#upload-files}

Tests müssen manchmal Dateien in das zu testende Programm hochladen. Um den Einsatz von Selenium in Bezug auf Ihre Tests flexibel zu halten, ist es nicht möglich, ein Asset direkt in Selenium hochzuladen. Stattdessen durchläuft das Hochladen einer Datei einige Zwischenschritte:

1. Laden Sie die Datei unter der von der Umgebungsvariablen `UPLOAD_URL` angegebenen URL hoch. Der Upload muss in einer POST-Anfrage mit einem mehrteiligen Formular durchgeführt werden. Das mehrteilige Formular muss über ein einziges Dateifeld verfügen. Dies entspricht `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`. Informationen zum Ausführen einer solchen HTTP-Anfrage finden Sie in der Dokumentation und in den Bibliotheken der im Docker-Image verwendeten Programmiersprache.
2. Wenn der Upload erfolgreich war, gibt die Anfrage eine `200 OK`-Antwort vom Typ `text/plain` zurück. Der Inhalt der Antwort ist ein undurchsichtiges Datei-Handle. Sie können dieses Handle in einem `<input>`-Element anstelle eines Dateipfads verwenden, um das Hochladen von Dateien in Ihrem Programm zu testen.
