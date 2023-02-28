---
title: Testen der Benutzeroberfläche
description: Benutzerdefinierte Benutzeroberflächentests sind eine optionale Funktion, mit der Sie Benutzeroberflächentests für Ihre benutzerdefinierten Anwendungen erstellen und automatisch ausführen können.
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 3e31b065999d36717b81253d2773e41b76949954
workflow-type: tm+mt
source-wordcount: '2141'
ht-degree: 56%

---


# Testen der Benutzeroberfläche {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="Testen der Benutzeroberfläche"
>abstract="Die Testfunktion für die benutzerdefinierte Benutzeroberfläche ist eine optionale Funktion, mit der man Benutzeroberflächentests für Anwendungen erstellen und automatisch ausführen kann. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen)."

Die Testfunktion für die benutzerdefinierte Benutzeroberfläche ist eine optionale Funktion, mit der man Benutzeroberflächentests für Anwendungen erstellen und automatisch ausführen kann.

## Übersicht {#custom-ui-testing}

AEM bietet eine integrierte Suite mit [Cloud Manager-Qualitäts-Akzeptanztests](/help/implementing/cloud-manager/custom-code-quality-rules.md), um eine reibungslose Aktualisierung ihrer benutzerdefinierten Programme sicherzustellen. Insbesondere unterstützen IT-Testgeräte bereits die Erstellung und Automatisierung benutzerdefinierter Tests mithilfe von AEM-APIs.

Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen). Darüber hinaus kann ein UI-Test-Projekt einfach durch die Verwendung von [den AEM Projektarchetyp.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)

Benutzeroberflächentests werden als Teil eines bestimmten Qualitäts-Akzeptanztests für jede Cloud Manager-Pipeline mit einem [dedizierten Schritt für das **Testen der benutzerdefinierten Benutzeroberfläche** ausgeführt.](/help/implementing/cloud-manager/deploy-code.md) Alle Benutzeroberflächentests, einschließlich Regression und neuer Funktionen, ermöglichen die Erkennung und Meldung von Fehlern.

Im Gegensatz zu benutzerdefinierten Funktionstests, bei denen es sich um HTTP-Tests handelt, die in Java geschrieben wurden, können die Benutzeroberflächentests ein Docker-Image mit Tests in jeder Sprache sein, sofern sie den unter [Erstellen von Benutzeroberflächentests](#building-ui-tests) definierten Konventionen entsprechen.

>[!TIP]
>
>Adobe empfiehlt, sich an die Struktur und Sprache (JavaScript und WDIO) zu halten, die im [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) bereitgestellt werden.
>
>Adobe bietet außerdem ein UI-Testmodulbeispiel, das auf Java und WebDriver basiert. Weitere Informationen finden Sie unter [AEM Testbeispielspeicher](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver) für Details.

## Erste Schritte mit UI-Tests {#get-started-ui-tests}

In diesem Abschnitt werden die Schritte beschrieben, die zum Einrichten von UI-Tests für die Ausführung in Cloud Manager erforderlich sind.

1. Entscheiden Sie, welche Programmiersprache Sie verwenden möchten.

   * Verwenden Sie für JavaScript und WDIO den Beispielcode, der automatisch im `ui.tests` Ordner Ihres Cloud Manager-Repositorys.

      >[!NOTE]
      >
      >Wenn Ihr Repository vor der automatischen Erstellung von Cloud Manager erstellt wurde `it.tests` -Ordnern können Sie auch die neueste Version mithilfe der [AEM Projektarchetyp.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests)

   * Verwenden Sie für Java und WebDriver den Beispielcode aus dem [AEM Testbeispielen-Repository.](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver)

   * Weiterführende Informationen zu anderen Programmiersprachen finden Sie im Abschnitt . [Erstellen von UI-Tests](#building-ui-tests) in diesem Dokument, um das Testprojekt einzurichten.

1. Stellen Sie sicher, dass der UI-Test gemäß Abschnitt aktiviert ist. [Kunden-Opt-in](#customer-opt-in) in diesem Dokument.

1. Entwickeln Sie Ihre Testfälle und [Führen Sie diese Tests lokal aus.](#run-ui-tests-locally)

1. Übertragen Sie Ihren Code in das Cloud Manager-Repository und führen Sie eine Cloud Manager-Pipeline aus.

## Erstellen von Benutzeroberflächentests {#building-ui-tests}

Ein Maven-Projekt generiert einen Docker-Build-Kontext. In diesem Docker-Build-Kontext wird beschrieben, wie Sie ein Docker-Bild erstellen, das die UI-Tests enthält, die Cloud Manager verwendet, um ein Docker-Bild zu generieren, das die tatsächlichen UI-Tests enthält.

In diesem Abschnitt werden die Schritte beschrieben, die zum Hinzufügen eines Projekts mit Benutzeroberflächentests zum Repository erforderlich sind.

>[!TIP]
>
>Die [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype) Sie können ein UI-Test-Projekt für Sie generieren, das der folgenden Beschreibung entspricht, wenn Sie keine speziellen Anforderungen für die Programmiersprache haben.

### Generieren eines Docker-Build-Kontexts {#generate-docker-build-context}

Um einen Docker-Build-Kontext zu generieren, benötigen Sie ein Maven-Modul, das:

* ein Archiv erzeugt, das ein `Dockerfile` und jede andere Datei enthält, die zum Erstellen des Docker-Images mit Ihren Tests erforderlich ist.
* das Archiv mit dem `ui-test-docker-context`-Klassifikator markiert.

Die einfachste Möglichkeit, dies zu erreichen, besteht darin, das [Maven Assembly-Plug-in](https://maven.apache.org/plugins/maven-assembly-plugin/) so zu konfigurieren, dass das Docker-Build-Kontextarchiv erstellt und ihm der richtige Klassifikator zugewiesen wird.

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

Diese Ausführung weist das Maven Assembly Plug-in an, ein Archiv basierend auf den in `assembly-ui-test-docker-context.xml` enthaltenen Anweisungen zu erstellen, das im Jargon des Plug-ins als **Assembly-Deskriptor** bezeichnet wird. Der Assembly-Deskriptor listet alle Dateien auf, die Teil des Archivs sein müssen.

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

Der Assembly-Deskriptor weist das Plug-in an, ein Archiv des Typs `.tar.gz` zu erstellen, und weist ihm den Klassifikator `ui-test-docker-context` zu. Darüber hinaus werden die Dateien, einschließlich der folgenden, aufgelistet, die im Archiv enthalten sein folgen müssen.

* eine `Dockerfile`, obligatorisch für das Erstellen des Docker-Images
* das Skript `wait-for-grid.sh`, dessen Zwecke unten beschrieben werden
* Die eigentlichen Benutzeroberflächentests, die von einem Node.js-Projekt im Ordner `test-module` implementiert wurden

Der Assembly-Deskriptor schließt auch einige Dateien aus, die beim lokalen Ausführen der Benutzeroberflächentests generiert werden könnten. Dies garantiert ein kleineres Archiv und schnellere Builds.

Das Archiv, das den Docker-Build-Kontext enthält, wird automatisch von Cloud Manager abgerufen, der das Docker-Image mit Ihren Tests während der Ausführung seiner Bereitstellungs-Pipelines erstellt. Schließlich führt Cloud Manager das Docker-Image aus, um die Benutzeroberflächentests für das Programm auszuführen.

Der Build sollte entweder 0 oder 1 Archiv erzeugen. Wenn kein Archiv erzeugt wird, wird der Testschritt standardmäßig durchgeführt. Wenn der Build mehr als ein Archiv erzeugt, ist das ausgewählte Archiv nicht deterministisch.

### Kunden-Opt-in {#customer-opt-in}

Damit Cloud Manager Ihre UI-Tests erstellen und ausführen kann, müssen Sie diese Funktion aktivieren, indem Sie eine Datei zu Ihrem Repository hinzufügen.

* Der Dateiname muss `testing.properties` lauten.

* Der Inhalt der Datei muss `ui-tests.version=1` lauten.
* Die Datei muss sich für UI-Tests neben dem Maven-Untermodul befinden `pom.xml` -Datei des UI-Tests-Untermoduls.
* Die Datei muss sich im Stammverzeichnis der erstellten `tar.gz`-Datei befinden.

Wenn diese Datei nicht vorhanden ist, werden die Erstellung und Ausführung der Benutzeroberflächentests übersprungen.

Um eine `testing.properties`-Datei in das Build-Artefakt aufzunehmen, fügen Sie eine `include`-Anweisung in die `assembly-ui-test-docker-context.xml`-Datei ein.

```xml
[...]
<includes>
    <include>Dockerfile</include>
    <include>wait-for-grid.sh</include>
    <include>testing.properties</include> <!-- opt-in test module in Cloud Manager -->
</includes>
[...]
```

>[!NOTE]
>
>Falls Ihr Projekt die Zeile nicht enthält, müssen Sie diese Datei bearbeiten, um sich für Tests der Benutzeroberfläche anmelden zu können.
>
>Die Datei kann eine Zeile enthalten, in der empfohlen wird, sie nicht zu bearbeiten. Das liegt daran, dass die Datei in Ihr Projekt aufgenommen wurde, bevor Opt-in-Benutzeroberflächentests eingeführt wurden, und dass die Kunden die Datei nicht bearbeiten sollten. Dies kann ignoriert werden.

Wenn Sie die von Adobe bereitgestellten Beispiele verwenden:

* Für JavaScript-basierte `ui.tests` Ordner, der basierend auf dem [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)können Sie den folgenden Befehl ausführen, um die erforderliche Konfiguration hinzuzufügen.

   ```shell
   echo "ui-tests.version=1" > testing.properties
   
   if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
     awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
   fi
   ```

* Für die angegebenen Java-Testbeispiele ist bereits das Opt-in-Flag gesetzt.

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
| `AEM_AUTHOR_PASSWORD` | `admin` | Das Kennwort zur Anmeldung bei der AEM-Autoreninstanz |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | Die URL der AEM-Veröffentlichungsinstanz |
| `AEM_PUBLISH_USERNAME` | `admin` | Der Benutzername, der bei der AEM Veröffentlichungsinstanz angemeldet werden soll |
| `AEM_PUBLISH_PASSWORD` | `admin` | Das Kennwort für die Anmeldung bei der AEM Veröffentlichungsinstanz |
| `REPORTS_PATH` | `/usr/src/app/reports` | Der Pfad, in dem der XML-Bericht der Testergebnisse gespeichert werden muss |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Die URL, unter der die Datei hochgeladen werden muss, um sie für Selenium zugänglich zu machen |

Die Adobe-Testbeispiele bieten Hilfsfunktionen für den Zugriff auf die Konfigurationsparameter:

* JavaScript: Siehe [lib/config.js](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/config.js) Modul
* Java: Siehe [Konfiguration](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java) class

### Warten auf Selenium {#waiting-for-selenium}

Bevor die Tests beginnen, muss das Docker-Image sicherstellen, dass der Selenium-Server betriebsbereit ist. Das Warten auf den Selenium-Service erfolgt in zwei Schritten.

1. Lesen der URL des Selenium-Service aus der Umgebungsvariablen `SELENIUM_BASE_URL`.
1. Abrufen des von der Selenium-API bereitgestellten [Statusendpunkts](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) in regelmäßigen Abständen.

Sobald der Statusendpunkt von Selenium positiv antwortet, können die Tests beginnen.

Die Testbeispiele der Adobe-Benutzeroberfläche behandeln dies mit dem Skript `wait-for-grid.sh`, der beim Start des Dockers ausgeführt wird und die tatsächliche Testausführung erst startet, wenn das Raster bereit ist.

### Generieren von Testberichten {#generate-test-reports}

Das Docker-Image muss Testberichte im JUnit-XML-Format generieren und in dem von der Umgebungsvariablen `REPORTS_PATH` angegebenen Pfad speichern. Das JUnit-XML-Format ist ein weitverbreitetes Format für Testergebnisberichte. Wenn das Docker-Image Java und Maven verwendet, können Standard-Testmodule wie das [Maven Surefire Plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) und das [Maven Failsafe Plug-in](https://maven.apache.org/surefire/maven-failsafe-plugin/) solche Berichte vorkonfiguriert erstellen.

Wenn das Docker-Image mit anderen Programmiersprachen oder Test-Runnern implementiert ist, lesen Sie in der Dokumentation der ausgewählten Tools nach, wie Sie JUnit-XML-Berichte erzeugen.

>[!NOTE]
>
>Das Ergebnis des UI-Testschritts wird nur anhand der Testberichte ausgewertet. Stellen Sie sicher, dass Sie den Bericht entsprechend für Ihre Testausführung generieren.
>
>Verwenden Sie Zusicherungen, anstatt nur einen Fehler an STDERR zu protokollieren oder einen Exitcode ungleich null zurückzugeben. Andernfalls wird Ihre Bereitstellungs-Pipeline normal fortgesetzt.

### Erfassen von Screenshots und Videos {#capture-screenshots}

Das Docker-Bild kann zusätzliche Testausgabe generieren (z. B. Screenshots oder Videos) und sie in dem Pfad speichern, der durch die Umgebungsvariable angegeben wird `REPORTS_PATH`. Jede Datei, die sich unter dem Verzeichnis `REPORTS_PATH` befindet, wird in das Testergebnisarchiv aufgenommen.

Die von Adobe bereitgestellten Testbeispiele erstellen standardmäßig Screenshots für fehlgeschlagene Tests.

Mithilfe der Hilfsfunktionen können Sie Screenshots durch Ihre Tests erstellen.

* JavaScript: [takeScreenshot, Befehl](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java: [Befehle](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java)

Wenn während der Testausführung der Benutzeroberfläche ein Testergebnisarchiv erstellt wird, können Sie es mithilfe der `Download Details` unter der Schaltfläche [**Testen der benutzerdefinierten Benutzeroberfläche** Schritt.](/help/implementing/cloud-manager/deploy-code.md)

### Hochladen von Dateien {#upload-files}

Tests müssen manchmal Dateien in das zu testende Programm hochladen. Um den Einsatz von Selenium in Bezug auf Ihre Tests flexibel zu halten, ist es nicht möglich, ein Asset direkt in Selenium hochzuladen. Stattdessen sind für das Hochladen einer Datei die folgenden Schritte erforderlich.

1. Laden Sie die Datei unter der von der Umgebungsvariablen `UPLOAD_URL` angegebenen URL hoch.
   * Der Upload muss in einer POST-Anfrage mit einem mehrteiligen Formular durchgeführt werden.
   * Das mehrteilige Formular muss über ein einziges Dateifeld verfügen.
   * Dies entspricht `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Informationen zum Ausführen einer solchen HTTP-Anfrage finden Sie in der Dokumentation und in den Bibliotheken der im Docker-Image verwendeten Programmiersprache.
   * Die Adobe-Testbeispiele bieten Hilfsfunktionen zum Hochladen von Dateien:
      * JavaScript: Siehe [getFileHandleForUpload](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js) Befehl.
      * Java: Siehe [FileHandler](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java) -Klasse.
1. Wenn der Upload erfolgreich war, gibt die Anfrage eine `200 OK`-Antwort vom Typ `text/plain` zurück. 
   * Der Inhalt der Antwort ist ein undurchsichtiges Datei-Handle.
   * Sie können dieses Handle in einem `<input>`-Element anstelle eines Dateipfads verwenden, um das Hochladen von Dateien in Ihrem Programm zu testen.

## Lokales Ausführen von UI-Tests {#run-ui-tests-locally}

Vor der Aktivierung von UI-Tests in einer Cloud Manager-Pipeline wird empfohlen, die UI-Tests lokal für die [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) oder in einer tatsächlichen AEM as a Cloud Service Instanz.

### Voraussetzungen {#prerequisites}

Die Tests in Cloud Manager werden von einem technischen Administrator ausgeführt.

Erstellen Sie zum Ausführen der UI-Tests von Ihrem lokalen Computer aus einen Benutzer mit admin-ähnlichen Berechtigungen, um dasselbe Verhalten zu erzielen.

### JavaScript-Testbeispiel {#javascript-sample}

1. Öffnen Sie eine Shell und navigieren Sie zur `ui.tests` Ordner im Repository

1. Führen Sie den folgenden Befehl aus, um die Tests mit Maven zu starten

   ```shell
   mvn verify -Pui-tests-local-execution \
   -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
   -DAEM_AUTHOR_USERNAME=<user> \
   -DAEM_AUTHOR_PASSWORD=<password> \
   -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
   -DAEM_PUBLISH_USERNAME=<user> \
   -DAEM_PUBLISH_PASSWORD=<password> \
   -DHEADLESS_BROWSER=true \
   -DSELENIUM_BROWSER=chrome
   ```

>[!NOTE]
>
>* Dadurch wird eine eigenständige Seleninstanz gestartet und die Tests werden dagegen ausgeführt.
>* Die Protokolldateien werden im `target/reports` Ordner Ihres Repositorys
>* Sie müssen sicherstellen, dass Sie die neueste Chrome-Version verwenden, da der Test die neueste Version von ChromeDriver automatisch zum Testen herunterlädt.
>
>Weitere Informationen finden Sie unter [AEM Projektarchetyp-Repository.](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/README.md)

### Java-Testbeispiel {#java-sample}

1. Öffnen Sie eine Shell und navigieren Sie zur `ui.tests/test-module` Ordner im Repository

1. Führen Sie den folgenden Befehl aus, um die Tests mit Maven zu starten

   ```shell
   # Start selenium docker image (for x64 CPUs)
   docker run --platform linux/amd64 -d -p 4444:4444 selenium/standalone-chrome-debug:latest
   
   # Start selenium docker image (for ARM CPUs)
   docker run -d -p 4444:4444 seleniarm/standalone-chromium
   
   # Run the tests using the previously started Selenium instance
   mvn verify -Pui-tests-local-execution -DSELENIUM_BASE_URL=http://<server>:<port>
   ```

>[!NOTE]
>
>* Die Protokolldateien werden im `target/reports` Ordner Ihres Repositorys.
>
>Weitere Informationen finden Sie unter [AEM Testbeispielen-Repository.](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md)
