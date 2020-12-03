---
title: UI-Tests - Cloud Services
description: UI-Tests - Cloud Services
translation-type: tm+mt
source-git-commit: bf3fb5178bc2ae72e19ecc1de82b08fac5089ecf
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---


# UI-Tests {#ui-testing}

>[!CAUTION]
>
>Diese Funktion ist noch nicht generell verfügbar.


UI-Tests sind Selenium-basierte Tests, die in einem Docker-Bild verpackt werden, um eine breite Auswahl in Sprache und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder ein anderes auf Selenium aufbauendes Framework und jede andere Technologie). Das Docker-Bild kann mit Standardwerkzeugen erstellt werden, muss jedoch bei der Ausführung bestimmte Konventionen einhalten. Beim Ausführen des Docker-Bildes wird automatisch ein Selenium-Server bereitgestellt. Die unten beschriebenen Laufzeitkonventionen ermöglichen es Ihrem Testcode, sowohl auf den Selenium-Server als auch auf die AEM Instanzen zuzugreifen, die derzeit getestet werden.

## Erstellen von UI-Tests {#building-ui-tests}

UI-Tests werden aus einem Docker-Buildkontext erstellt, der von einem Maven-Projekt generiert wurde. Cloud Manager verwendet den Docker-Buildkontext, um ein Docker-Bild zu generieren, das die tatsächlichen UI-Tests enthält. Zusammengefasst generiert ein Maven-Projekt einen Docker-Buildkontext und der Docker-Buildkontext beschreibt, wie ein Docker-Bild mit den UI-Tests erstellt wird.

In diesem Abschnitt werden die Schritte beschrieben, die zum Hinzufügen eines UI-Tests-Projekts zum Repository erforderlich sind. Wenn Sie eilig sind oder keine speziellen Anforderungen an die Programmiersprache haben, kann der [AEM Projektarchiv](https://github.com/adobe/aem-project-archetype) ein UI-Tests-Projekt für Sie erstellen.

### Erstellen eines Docker-Buildkontexts {#generate-docker-build-context}

Um einen Docker-Buildkontext zu generieren, benötigen Sie ein Maven-Modul, das:

- Erzeugt ein Archiv, das ein `Dockerfile` und jede andere Datei enthält, die zum Erstellen des Docker-Bildes mit Ihren Tests erforderlich ist.
- Kennzeichnet das Archiv mit dem Klassifizierer `ui-test-docker-context`.

Die einfachste Möglichkeit, dies zu erreichen, besteht darin, das [Maven Assembly Plugin](http://maven.apache.org/plugins/maven-assembly-plugin/) zu konfigurieren, um das Docker Build-Kontextarchiv zu erstellen und ihm den richtigen Classification zuzuweisen.

Sie können UI-Tests mit verschiedenen Technologien und Frameworks erstellen. In diesem Abschnitt wird jedoch davon ausgegangen, dass Ihr Projekt auf eine ähnliche Weise wie folgt entworfen wird.

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

Die `pom.xml`-Datei übernimmt den Maven-Build. hinzufügen eine Ausführung des Maven Assembly Plugins ähnlich der folgenden.

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

Diese Ausführung weist das Maven Assembly-Plugin an, ein Archiv zu erstellen, das auf den Anweisungen basiert, die in `assembly-ui-test-docker-context.xml` enthalten sind, die als &quot;Assemblydeskriptor&quot;im Jargon des Plugins bezeichnet werden. Der Assemblydeskriptor Liste alle Dateien, die Teil des Archivs sein müssen.

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

Der Assemblydeskriptor weist das Plug-In an, ein Archiv des Typs `.tar.gz` zu erstellen, und weist ihm den Klassifizierer `ui-test-docker-context` zu. Außerdem werden die Dateien, die im Archiv enthalten sein müssen, Liste:

- Ein `Dockerfile`, obligatorisch für das Erstellen des Dockerbilds.
- Das Skript `wait-for-grid.sh`, dessen Zwecke unten beschrieben werden.
- Die tatsächlichen UI-Tests, die von einem Node.js-Projekt im Ordner `test-module` implementiert wurden.

Der Assemblydeskriptor schließt auch einige Dateien aus, die beim lokalen Ausführen der UI-Tests generiert werden könnten. Dies garantiert ein kleineres Archiv und schnellere Builds.

Das Archiv, das den Docker-Build-Kontext enthält, wird automatisch von Cloud Manager abgerufen, der das Docker-Bild mit Ihren Tests während der Bereitstellungs-Pipelines erstellt. Schließlich führt Cloud Manager das Docker-Bild aus, um die UI-Tests für Ihre Anwendung auszuführen.

## Schreiben von UI-Tests {#writing-ui-tests}

In diesem Abschnitt werden die Konventionen beschrieben, denen das Docker-Bild mit Ihren UI-Tests folgen muss. Das Docker-Bild wird aus dem im vorherigen Abschnitt beschriebenen Docker-Buildkontext erstellt.

### Umgebungsvariablen {#environment-variables}

Die folgenden Umgebung werden zur Laufzeit an Ihr Dockerbild übergeben.

| Variable | Beispiele | Beschreibung |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Die URL des Selenium-Servers |
| `SELENIUM_BROWSER` | `chrome`, `firefox` | Die vom Selenium-Server verwendete Browserimplementierung |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | Die URL der AEM Autoreninstanz |
| `AEM_AUTHOR_USERNAME` | `admin` | Der Benutzername für die Anmeldung bei der AEM Autoreninstanz |
| `AEM_AUTHOR_PASSWORD` | `admin` | Das Kennwort zur Anmeldung bei der AEM Autoreninstanz |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | Die URL der AEM Veröffentlichungsinstanz |
| `AEM_PUBLISH_USERNAME` | `admin` | Der Benutzername für die Anmeldung bei der AEM Veröffentlichungsinstanz |
| `AEM_PUBLISH_PASSWORD` | `admin` | Das Kennwort zum Anmelden bei der AEM Veröffentlichungsinstanz |
| `REPORTS_PATH` | `/usr/src/app/reports` | Der Pfad, in dem der XML-Bericht der Testergebnisse gespeichert werden muss |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Die URL, in die die Datei hochgeladen werden muss, damit sie für Selenium zugänglich gemacht werden kann |

### Warten auf Fertigstellung von Selen {#waiting-for-selenium}

Vor dem Test-Beginn ist es Aufgabe des Docker-Bildes sicherzustellen, dass der Selenium-Server betriebsbereit ist. Warten auf den Selenium-Dienst erfolgt in zwei Schritten:

1. Lesen Sie die URL des Selenium-Dienstes aus der Variablen `SELENIUM_BASE_URL` Umgebung.
2. Umfrage in regelmäßigen Abständen zum [Status-Endpunkt](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready), der von der Selen-API offen gelegt wird.

Sobald der Status-Endpunkt des Selenums mit einer positiven Antwort beantwortet ist, können die Tests endlich zum Beginn kommen.

### Erstellen Sie die Testberichte {#generate-test-reports}

Das Docker-Bild muss Testberichte im JUnit XML-Format generieren und in dem Pfad speichern, der durch die Umgebung `REPORTS_PATH` angegeben wird. Das JUnit-XML-Format ist ein weit verbreitetes Format zum Berichte der Testergebnisse. Wenn das Docker-Bild Java und Maven verwendet, sowohl das [Maven Surefire-Plugin](https://maven.apache.org/surefire/maven-surefire-plugin/) als auch das [Maven Failsafe-Plugin](https://maven.apache.org/surefire/maven-failsafe-plugin/). Wenn das Docker-Bild mit anderen Programmiersprachen oder Testläufern implementiert ist, lesen Sie in der Dokumentation die ausgewählten Tools, um zu erfahren, wie Sie JUnit-XML-Berichte erstellen.

### Hochladen von Dateien (#upload-files)

Tests müssen manchmal Dateien in die zu testende Anwendung hochladen. Um die Bereitstellung von Selen relativ zu Ihren Tests flexibel zu halten, ist es nicht möglich, ein Asset direkt nach Selen hochzuladen. Stattdessen führt das Hochladen einer Datei einige Zwischenschritte durch:

1. Laden Sie die Umgebung unter der URL hoch, die in der Variablen `UPLOAD_URL` angegeben ist. Der Hochladevorgang muss in einer POST mit einem mehrteiligen Formular durchgeführt werden. Das mehrteilige Formular muss über ein einziges Dateifeld verfügen. Dies entspricht `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`. Lesen Sie die Dokumentation und die Bibliotheken der im Docker-Bild verwendeten Programmiersprache, um zu erfahren, wie eine solche HTTP-Anforderung ausgeführt wird.
2. Wenn der Upload erfolgreich war, gibt die Anforderung eine Antwort vom Typ `200 OK` zurück. `text/plain` Der Inhalt der Antwort ist ein undurchsichtiger Dateigriff. Sie können diesen Handle anstelle eines Dateipfads in einem `<input>`-Element verwenden, um Datei-Uploads in Ihrer Anwendung zu testen.
