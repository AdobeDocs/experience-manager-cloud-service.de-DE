---
title: Testen der Benutzeroberfläche
description: Benutzerdefinierte UI-Tests sind eine optionale Funktion, mit der Sie Benutzeroberflächentests für Ihre benutzerdefinierten Anwendungen erstellen und automatisch ausführen können
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 05f9e9de0d5dbcc332466dc964e2d01569d16110
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 48%

---


# Testen der Benutzeroberfläche {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="Testen der Benutzeroberfläche"
>abstract="Benutzerdefinierte UI-Tests sind eine optionale Funktion, mit der Sie Benutzeroberflächentests für Ihre Anwendungen erstellen und automatisch ausführen können. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen)."

Benutzerdefinierte UI-Tests sind eine optionale Funktion, mit der Sie Benutzeroberflächentests für Ihre Anwendungen erstellen und automatisch ausführen können.

## Übersicht {#custom-ui-testing}

AEM bietet eine integrierte Suite von [Cloud Manager-Qualitätstests](/help/implementing/cloud-manager/custom-code-quality-rules.md) um eine reibungslose Aktualisierung benutzerdefinierter Programme zu gewährleisten. Insbesondere ermöglicht IT-Tests die bereits Erstellung und Automatisierung benutzerdefinierter Tests mithilfe von AEM-APIs.

Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen). Zusätzlich kann ein UI-Test-Projekt einfach durch die Verwendung von [den AEM Projektarchetyp.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)

UI-Tests werden als Teil eines bestimmten Qualitätstests für jede Cloud Manager-Pipeline mit einer [dediziert **Testen der benutzerdefinierten Benutzeroberfläche** Schritt.](/help/implementing/cloud-manager/deploy-code.md) Alle UI-Tests, einschließlich Regression und neuer Funktionen, ermöglichen die Erkennung und Meldung von Fehlern.

Im Gegensatz zu benutzerdefinierten Funktionstests, bei denen es sich um in Java geschriebene HTTP-Tests handelt, können UI-Tests ein Docker-Bild mit Tests sein, die in einer beliebigen Sprache geschrieben wurden, sofern sie den im Abschnitt definierten Konventionen entsprechen [Erstellen von UI-Tests](#building-ui-tests)

>[!TIP]
>
>Adobe empfiehlt, die in der Variablen [AEM Projektarchetyp.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)

### Kunden-Opt-in {#customer-opt-in}

Damit Cloud Manager Ihre UI-Tests erstellen und ausführen kann, müssen Sie diese Funktion aktivieren, indem Sie eine Datei zu Ihrem Repository hinzufügen.

* Der Dateiname muss `testing.properties` lauten.

* Der Dateiinhalt muss `ui-tests.version=1`.
* Die Datei muss sich für UI-Tests neben dem Maven-Untermodul befinden. `pom.xml` -Datei des UI-Tests-Untermoduls.
* Die Datei muss sich im Stammverzeichnis des erstellten `tar.gz` -Datei.

Der Build und die Ausführungen der Benutzeroberflächentests werden übersprungen, wenn diese Datei nicht vorhanden ist.

So fügen Sie eine `testing.properties` -Datei im Build-Artefakt ein `include` -Anweisung `assembly-ui-test-docker-context.xml` -Datei.

```xml
[...]
<includes>
    <include>Dockerfile</include>
    <include>wait-for-grid.sh</include>
    <include>testing.properties</include> <!- opt-in test module in Cloud Manager -->
</includes>
[...]
```

>[!NOTE]
>
>Wenn Ihr Projekt diese Zeile nicht enthält, müssen Sie die Datei bearbeiten, um UI-Tests zu aktivieren.
>
>Die Datei kann eine Zeile enthalten, die darauf hinweist, sie nicht zu bearbeiten. Dies liegt daran, dass sie in Ihr Projekt eingeführt wurde, bevor Opt-in-UI-Tests eingeführt wurden und die des Kunden nicht dazu bestimmt war, die Datei zu bearbeiten. Dies kann ignoriert werden.

## Erstellen von Benutzeroberflächentests {#building-ui-tests}

Ein Maven-Projekt generiert einen Docker-Build-Kontext. In diesem Docker-Build-Kontext wird beschrieben, wie Sie ein Docker-Bild erstellen, das die UI-Tests enthält und von den Cloud Manager-Benutzern ein Docker-Bild mit den tatsächlichen UI-Tests generieren kann.

In diesem Abschnitt werden die Schritte beschrieben, die zum Hinzufügen eines UI-Test-Projekts zu Ihrem Repository erforderlich sind.

>[!TIP]
>
>Die [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype) Sie können ein UI-Tests-Projekt erstellen, für das Sie keine speziellen Anforderungen an die Programmiersprache haben.

### Erstellen eines Docker-Build-Kontexts {#generate-docker-build-context}

Um einen Docker-Build-Kontext zu generieren, benötigen Sie ein Maven-Modul, das:

* ein Archiv erzeugt, das ein `Dockerfile` und jede andere Datei enthält, die zum Erstellen des Docker-Images mit Ihren Tests erforderlich ist.
* das Archiv mit dem `ui-test-docker-context`-Klassifikator markiert.

Am einfachsten ist es, die [Maven Assembly-Plugin](http://maven.apache.org/plugins/maven-assembly-plugin/) , um das Docker-Build-Kontextarchiv zu erstellen und ihm den richtigen Klassifizierer zuzuweisen.

Sie können Benutzeroberflächentests mit verschiedenen Technologien und Frameworks erstellen. In diesem Abschnitt wird jedoch davon ausgegangen, dass Ihr Projekt ähnlich wie folgt aufgebaut ist.

```text
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

Diese Ausführung weist das Maven Assembly-Plugin an, ein Archiv zu erstellen, das auf den Anweisungen in `assembly-ui-test-docker-context.xml`, die **Assemblydeskriptor** im Jargon des Plug-ins. Der Assembly-Deskriptor listet alle Dateien auf, die Teil des Archivs sein müssen.

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

Der Assembly-Deskriptor weist das Plug-in an, ein Archiv des Typs `.tar.gz` zu erstellen, und weist ihm den Klassifikator `ui-test-docker-context` zu. Außerdem werden die Dateien aufgelistet, die im Archiv enthalten sein müssen, einschließlich der folgenden.

* eine `Dockerfile`, obligatorisch für das Erstellen des Docker-Images
* das Skript `wait-for-grid.sh`, dessen Zwecke unten beschrieben werden
* Die eigentlichen Benutzeroberflächentests, die von einem Node.js-Projekt im Ordner `test-module` implementiert wurden

Der Assembly-Deskriptor schließt auch einige Dateien aus, die beim lokalen Ausführen der Benutzeroberflächentests generiert werden könnten. Dies garantiert ein kleineres Archiv und schnellere Builds.

Das Archiv, das den Docker-Build-Kontext enthält, wird automatisch von Cloud Manager abgerufen, das das Docker-Bild erstellt, das Ihre Tests während der Implementierungs-Pipelines enthält. Schließlich führt Cloud Manager das Docker-Image aus, um die Benutzeroberflächentests für das Programm auszuführen.

Der Build sollte entweder 0 oder 1 Archiv erzeugen. Wenn keine Archive erzeugt werden, wird der Testschritt standardmäßig durchgeführt. Wenn der Build mehr als ein Archiv erzeugt, ist das ausgewählte Archiv nicht deterministisch.

## Schreiben von Benutzeroberflächentests {#writing-ui-tests}

In diesem Abschnitt werden die Konventionen beschrieben, denen das Docker-Image mit Ihren Benutzeroberflächentests folgen muss. Das Docker-Image basiert auf dem im vorherigen Abschnitt beschriebenen Docker-Build-Kontext.

### Umgebungsvariablen {#environment-variables}

Die folgenden Umgebungsvariablen werden zur Laufzeit an Ihr Docker-Image übergeben.

| Variable | Beispiele | Beschreibung |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Die URL des Selenium-Servers |
| `SELENIUM_BROWSER` | `chrome` | Die vom Selenium-Server verwendete Browser-Implementierung |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | Die URL der AEM-Autoreninstanz |
| `AEM_AUTHOR_USERNAME` | `admin` | Der Benutzername, der bei der AEM Autoreninstanz angemeldet werden soll |
| `AEM_AUTHOR_PASSWORD` | `admin` | Das Passwort für die Anmeldung bei der AEM-Autoreninstanz |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | Die URL der AEM-Veröffentlichungsinstanz |
| `AEM_PUBLISH_USERNAME` | `admin` | Der Benutzername, der bei der AEM Veröffentlichungsinstanz angemeldet werden soll |
| `AEM_PUBLISH_PASSWORD` | `admin` | Das Passwort für die Anmeldung bei der AEM-Veröffentlichungsinstanz |
| `REPORTS_PATH` | `/usr/src/app/reports` | Der Pfad, in dem der XML-Bericht der Testergebnisse gespeichert werden muss |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Die URL, unter der die Datei hochgeladen werden muss, um sie für Selenium zugänglich zu machen |

### Warten auf Bereitschaft von Selenium {#waiting-for-selenium}

Bevor die Tests beginnen, muss das Docker-Image sicherstellen, dass der Selenium-Server betriebsbereit ist. Das Warten auf den Selenium-Service erfolgt in zwei Schritten.

1. Lesen der URL des Selenium-Service aus der Umgebungsvariablen `SELENIUM_BASE_URL`.
1. Abrufen des von der Selenium-API bereitgestellten [Statusendpunkts](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) in regelmäßigen Abständen.

Sobald der Status-Endpunkt von Selenium mit einer positiven Antwort antwortet, können die Tests beginnen.

### Testberichte generieren {#generate-test-reports}

Das Docker-Image muss Testberichte im JUnit-XML-Format generieren und in dem von der Umgebungsvariablen `REPORTS_PATH` angegebenen Pfad speichern. Das JUnit XML-Format ist ein häufig verwendetes Format für die Berichterstellung über die Testergebnisse. Wenn das Docker-Bild Java und Maven verwendet, werden Standardtestmodule wie [Maven Surefire-Plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) und [Maven Failsafe-Plug-in](https://maven.apache.org/surefire/maven-failsafe-plugin/) kann solche Berichte standardmäßig generieren.

Wenn das Docker-Bild mit anderen Programmiersprachen oder Test-Läufern implementiert ist, finden Sie in der Dokumentation die ausgewählten Tools zum Generieren von JUnit XML-Berichten.

### Hochladen von Dateien {#upload-files}

Tests müssen manchmal Dateien in die getestete Anwendung hochladen. Um die Bereitstellung von Selenium relativ zu Ihren Tests flexibel zu halten, ist es nicht möglich, ein Asset direkt in Selenium hochzuladen. Stattdessen sind für das Hochladen einer Datei die folgenden Schritte erforderlich.

1. Laden Sie die Datei unter der von der Umgebungsvariablen `UPLOAD_URL` angegebenen URL hoch.
   * Der Upload muss in einer POST-Anfrage mit einem mehrteiligen Formular durchgeführt werden.
   * Das mehrteilige Formular muss über ein einziges Dateifeld verfügen.
   * Dies entspricht `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Informationen zum Ausführen einer solchen HTTP-Anfrage finden Sie in der Dokumentation und in den Bibliotheken der im Docker-Image verwendeten Programmiersprache.
1. Wenn der Upload erfolgreich war, gibt die Anfrage eine `200 OK`-Antwort vom Typ `text/plain` zurück. 
   * Der Inhalt der Antwort ist ein undurchsichtiges Datei-Handle.
   * Sie können dieses Handle in einem `<input>`-Element anstelle eines Dateipfads verwenden, um das Hochladen von Dateien in Ihrem Programm zu testen.
