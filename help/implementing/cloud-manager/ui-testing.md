---
title: Testen der Benutzeroberfläche
description: Benutzerdefinierte Benutzeroberflächentests sind eine optionale Funktion, mit der Sie Benutzeroberflächentests für Ihre benutzerdefinierten Anwendungen erstellen und automatisch ausführen können.
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 24796bd7d9c5e726cda13885bc4bd7e4155610dc
workflow-type: tm+mt
source-wordcount: '2238'
ht-degree: 89%

---


# Testen der Benutzeroberfläche {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="Testen der Benutzeroberfläche"
>abstract="Die Testfunktion für die benutzerdefinierte Benutzeroberfläche ist eine optionale Funktion, mit der man Benutzeroberflächentests für Anwendungen erstellen und automatisch ausführen kann. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen)."

Die Testfunktion für die benutzerdefinierte Benutzeroberfläche ist eine optionale Funktion, mit der man Benutzeroberflächentests für Anwendungen erstellen und automatisch ausführen kann.

## Übersicht {#custom-ui-testing}

AEM bietet eine integrierte Suite mit [Cloud Manager-Qualitäts-Akzeptanztests](/help/implementing/cloud-manager/custom-code-quality-rules.md), um eine reibungslose Aktualisierung ihrer benutzerdefinierten Programme sicherzustellen. Insbesondere IT-Testgates ermöglichen bereits die Erstellung und Automatisierung von benutzerdefinierten Tests mithilfe von AEM-APIs.

Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen). Darüber hinaus kann ein UI-Test-Projekt einfach durch die Verwendung von [AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de).

UI-Tests werden als Teil eines bestimmten Qualitätstests für jede Cloud Manager-Pipeline mit einer [**Testen der benutzerdefinierten Benutzeroberfläche** Schritt](/help/implementing/cloud-manager/deploy-code.md) in [Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) oder optional [produktionsfremde Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md). Alle Benutzeroberflächentests, einschließlich Regression und neuer Funktionen, ermöglichen die Erkennung und Meldung von Fehlern.

Im Gegensatz zu benutzerdefinierten Funktionstests, bei denen es sich um in Java geschriebene HTTP-Tests handelt, können UI-Tests ein Docker-Bild mit Tests sein, die in einer beliebigen Sprache geschrieben wurden, sofern sie den im Abschnitt definierten Konventionen entsprechen [Erstellen von UI-Tests](#building-ui-tests).

>[!TIP]
>
>Adobe empfiehlt, die in der Variablen [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests).
>
>Adobe bietet außerdem ein Beispiel für ein Benutzeroberflächen-Testmodul, das auf Java und WebDriver basiert. Einzelheiten finden Sie unter [AEM Testbeispiel-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver).

## Erste Schritte mit Benutzeroberflächentests {#get-started-ui-tests}

In diesem Abschnitt werden die Schritte beschrieben, die zum Einrichten von Benutzeroberflächentests für die Ausführung in Cloud Manager erforderlich sind.

1. Entscheiden Sie, welche Programmiersprache Sie verwenden möchten.

   * Verwenden Sie für JavaScript und WDIO den Beispielcode, der automatisch im Ordner `ui.tests` Ihres Cloud Manager-Repositorys generiert wird.

      >[!NOTE]
      >
      >Wenn Ihr Repository vor der automatischen Erstellung von Cloud Manager erstellt wurde `it.tests` -Ordnern können Sie auch die neueste Version mithilfe der [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests).

   * Verwenden Sie für Java und WebDriver den Beispielcode aus dem [AEM Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver).

   * Weitere Informationen zu anderen Programmiersprachen finden Sie im Abschnitt [Erstellen von Benutzeroberflächentests](#building-ui-tests) in diesem Dokument, um das Testprojekt einzurichten.

1. Stellen Sie sicher, dass das Testen der Benutzeroberfläche gemäß Abschnitt [Kunden-Opt-In](#customer-opt-in) in diesem Dokument aktiviert ist.

1. Entwickeln Sie Ihre Testfälle und [führen Sie diese Tests lokal aus](#run-ui-tests-locally).

1. Übertragen Sie Ihren Code in das Cloud Manager-Repository und führen Sie eine Cloud Manager-Pipeline aus.

## Erstellen von Benutzeroberflächentests {#building-ui-tests}

Ein Maven-Projekt generiert einen Docker-Build-Kontext. In diesem Docker-Build-Kontext wird beschrieben, wie ein Docker-Image erstellt wird, das die Benutzeroberflächentests enthält, damit Benutzerinnen und Benutzer von Cloud Manager ein Docker-Image erzeugen können, das die eigentlichen Benutzeroberflächentests enthält.

In diesem Abschnitt werden die Schritte beschrieben, die zum Hinzufügen eines Projekts mit Benutzeroberflächentests zum Repository erforderlich sind.

>[!TIP]
>
>Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) kann ein Projekt für Benutzeroberflächentests für Sie generieren, das der folgenden Beschreibung entspricht, wenn Sie keine speziellen Anforderungen für die Programmiersprache haben.

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

Damit Cloud Manager Ihre Benutzeroberflächentests erstellen und ausführen kann, müssen Sie diese Funktion aktivieren, indem Sie eine Datei zu Ihrem Repository hinzufügen.

* Der Dateiname muss `testing.properties` lauten.

* Der Inhalt der Datei muss `ui-tests.version=1` lauten.
* Die Datei muss sich unter dem Maven-Submodul für Benutzeroberflächentests neben der `pom.xml`-Datei des Submoduls für Benutzeroberflächentests befinden.
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

* Für den JavaScript-basierten Ordner `ui.tests`, der auf der Grundlage des [AEM-Projektarchetyps](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) erstellt wurde, können Sie den folgenden Befehl ausführen, um die erforderliche Konfiguration hinzuzufügen.

   ```shell
   echo "ui-tests.version=1" > testing.properties
   
   if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
     awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
   fi
   ```

* Für die angegebenen Java-Testbeispiele ist bereits die Opt-in-Markierung gesetzt.

## Schreiben von Benutzeroberflächentests {#writing-ui-tests}

In diesem Abschnitt werden die Konventionen beschrieben, denen das Docker-Image mit Ihren Benutzeroberflächentests folgen muss. Das Docker-Image basiert auf dem im vorherigen Abschnitt beschriebenen Docker-Build-Kontext.

### Umgebungsvariablen {#environment-variables}

Die folgenden Umgebungsvariablen werden zur Laufzeit an Ihr Docker-Image übergeben.

| Variable | Beispiele | Beschreibung |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Die URL des Selenium-Servers |
| `SELENIUM_BROWSER` | `chrome` | Die vom Selenium-Server verwendete Browser-Implementierung |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | Die URL der AEM-Autoreninstanz |
| `AEM_AUTHOR_USERNAME` | `admin` | Der Benutzername für die Anmeldung bei der AEM-Autoreninstanz |
| `AEM_AUTHOR_PASSWORD` | `admin` | Das Kennwort für die Anmeldung bei der AEM-Autoreninstanz |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | Die URL der AEM-Veröffentlichungsinstanz |
| `AEM_PUBLISH_USERNAME` | `admin` | Der Benutzername für die Anmeldung bei der AEM-Veröffentlichungsinstanz |
| `AEM_PUBLISH_PASSWORD` | `admin` | Das Kennwort für die Anmeldung bei der AEM-Veröffentlichungsinstanz |
| `REPORTS_PATH` | `/usr/src/app/reports` | Der Pfad, in dem der XML-Bericht der Testergebnisse gespeichert werden muss |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Die URL, unter der die Datei hochgeladen werden muss, um sie für Selenium zugänglich zu machen |

Die Adobe-Testbeispiele bieten Hilfsfunktionen für den Zugriff auf die Konfigurationsparameter:

* JavaScript: Siehe das Modul [lib/config.js](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/config.js)
* Java: Siehe die Klasse [Konfiguration](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java) 

### Warten auf Selenium {#waiting-for-selenium}

Bevor die Tests beginnen, muss das Docker-Image sicherstellen, dass der Selenium-Server betriebsbereit ist. Das Warten auf den Selenium-Service erfolgt in zwei Schritten.

1. Lesen der URL des Selenium-Service aus der Umgebungsvariablen `SELENIUM_BASE_URL`.
1. Abrufen des von der Selenium-API bereitgestellten [Statusendpunkts](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) in regelmäßigen Abständen.

Sobald der Statusendpunkt von Selenium positiv antwortet, können die Tests beginnen.

Die Testbeispiele der Adobe-Benutzeroberfläche behandeln dies mit dem Skript `wait-for-grid.sh`, das beim Start des Dockers ausgeführt wird und die tatsächliche Testausführung erst startet, wenn das Raster bereit ist.

### Generieren von Testberichten {#generate-test-reports}

Das Docker-Image muss Testberichte im JUnit-XML-Format generieren und in dem von der Umgebungsvariablen `REPORTS_PATH` angegebenen Pfad speichern. Das JUnit-XML-Format ist ein weitverbreitetes Format für Testergebnisberichte. Wenn das Docker-Image Java und Maven verwendet, können Standard-Testmodule wie das [Maven Surefire Plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) und das [Maven Failsafe Plug-in](https://maven.apache.org/surefire/maven-failsafe-plugin/) solche Berichte vorkonfiguriert erstellen.

Wenn das Docker-Image mit anderen Programmiersprachen oder Test-Runnern implementiert ist, lesen Sie in der Dokumentation der ausgewählten Tools nach, wie Sie JUnit-XML-Berichte erzeugen.

>[!NOTE]
>
>Das Ergebnis des Benutzeroberflächen-Testschritts wird nur anhand der Testberichte ausgewertet. Stellen Sie sicher, dass Sie den Bericht entsprechend Ihrer Testausführung generieren.
>
>Verwenden Sie Assertionen, anstatt einfach einen Fehler in STDERR zu protokollieren oder einen Exit-Code ungleich Null zurückzugeben, da Ihre Implementierungs-Pipeline sonst normal weiterlaufen kann.

### Erfassen von Screenshots und Videos {#capture-screenshots}

Das Docker-Bild kann zusätzliche Testausgaben generieren (z. B. Screenshots oder Videos) und sie in dem Pfad speichern, der durch die Umgebungsvariable `REPORTS_PATH` angegeben wird. Jede Datei, die sich unter dem Verzeichnis `REPORTS_PATH` befindet, wird in das Testergebnisarchiv aufgenommen.

Die von Adobe bereitgestellten Testbeispiele erstellen standardmäßig Screenshots für fehlgeschlagene Tests.

Mithilfe der Hilfsfunktionen können Sie Screenshots durch Ihre Tests erstellen.

* JavaScript: [Befehl takeScreenshot](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java: [Befehle](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java)

Wenn während der Ausführung eines Benutzeroberflächen-Tests ein Testergebnisarchiv erstellt wird, können Sie es über die Schaltfläche `Download Details` unter dem Schritt [**Benutzerdefinierte Benutzeroberflächentests** aus dem Cloud Manager herunterladen](/help/implementing/cloud-manager/deploy-code.md).

### Hochladen von Dateien {#upload-files}

Tests müssen manchmal Dateien in das zu testende Programm hochladen. Um den Einsatz von Selenium in Bezug auf Ihre Tests flexibel zu halten, ist es nicht möglich, ein Asset direkt in Selenium hochzuladen. Stattdessen sind für das Hochladen einer Datei die folgenden Schritte erforderlich.

1. Laden Sie die Datei unter der von der Umgebungsvariablen `UPLOAD_URL` angegebenen URL hoch.
   * Der Upload muss in einer POST-Anfrage mit einem mehrteiligen Formular durchgeführt werden.
   * Das mehrteilige Formular muss über ein einziges Dateifeld verfügen.
   * Dies entspricht `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Informationen zum Ausführen einer solchen HTTP-Anfrage finden Sie in der Dokumentation und in den Bibliotheken der im Docker-Image verwendeten Programmiersprache.
   * Die Adobe-Testbeispiele bieten Hilfsfunktionen zum Hochladen von Dateien:
      * JavaScript: Siehe den Befehl [getFileHandleForUpload](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js).
      * Java: Siehe die Klasse [FileHandler](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java).
1. Wenn der Upload erfolgreich war, gibt die Anfrage eine `200 OK`-Antwort vom Typ `text/plain` zurück. 
   * Der Inhalt der Antwort ist ein undurchsichtiges Datei-Handle.
   * Sie können dieses Handle in einem `<input>`-Element anstelle eines Dateipfads verwenden, um das Hochladen von Dateien in Ihrem Programm zu testen.

### Voraussetzungen {#prerequisites}

1. Die Tests in Cloud Manager werden von einem technischen Admin ausgeführt.

>[!NOTE]
>
>Erstellen Sie für die Ausführung der Funktionstests von Ihrem lokalen Computer aus eine Benutzerin oder einen Benutzer mit Admin-ähnlichen Berechtigungen, um dasselbe Verhalten zu erzielen.

1. Die Container-Infrastruktur, die für Funktionstests genutzt wird, ist durch die folgenden Grenzen begrenzt:

| Typ | Wert | Beschreibung |
|----------------------|-------|--------------------------------------------------------------------|
| CPU | 2.0 | CPU-Zeit pro Testausführung reserviert |
| Arbeitsspeicher | 1Gi | Menge des dem Test zugewiesenen Speichers, Wert in Byte |
| Zeitüberschreitung | 30m | Die Dauer, nach der der Test beendet wird. |
| Empfohlene Dauer | 15m | Es wird empfohlen, die Tests so zu schreiben, dass sie nicht länger als diese Zeit dauern. |

>[!NOTE]
>
> Wenn Sie weitere Ressourcen benötigen, erstellen Sie einen Fall für die Kundenunterstützung und beschreiben Sie Ihren Anwendungsfall. Unser Team wird Ihre Anfrage überprüfen und Ihnen angemessene Unterstützung bieten.


## Ausführen von lokalen Benutzeroberflächentests {#run-ui-tests-locally}

Vor der Aktivierung von UI-Tests in einer Cloud Manager-Pipeline wird empfohlen, die UI-Tests lokal für die [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
oder gegen eine tatsächliche AEM as a Cloud Service Instanz.

### JavaScript-Testbeispiel {#javascript-sample}

1. Öffnen Sie eine Shell und navigieren Sie zum Ordner `ui.tests` im Repository

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
>* Dadurch wird eine eigenständige Selenium-Instanz gestartet und die Tests werden dagegen ausgeführt.
>* Die Protokolldateien werden im Ordner `target/reports` Ihres Repositorys gespeichert
>* Sie müssen sicherstellen, dass Sie die neueste Chrome-Version verwenden, da der Test die neueste Version von ChromeDriver automatisch zum Testen herunterlädt.
>
>Weitere Informationen finden Sie unter [AEM-Projektarchetyp-Repository](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/README.md).

### Java-Testbeispiel {#java-sample}

1. Öffnen Sie eine Shell und navigieren Sie zum Ordner `ui.tests/test-module` im Repository

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
>* Die Protokolldateien werden im Ordner `target/reports` Ihres Repositorys gespeichert.
>
>Weitere Informationen finden Sie unter dem [AEM Testbeispielen-Repository](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md).
