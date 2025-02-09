---
title: UI-Tests
description: Benutzerdefinierte Benutzeroberflächentests sind eine optionale Funktion, mit der Sie Benutzeroberflächentests für Ihre benutzerdefinierten Anwendungen erstellen und automatisch ausführen können.
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8703240a5b7b8ed751620f602470da45025f7b74
workflow-type: tm+mt
source-wordcount: '2698'
ht-degree: 100%

---


# UI-Tests {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI-Tests"
>abstract="Die Testfunktion für die benutzerdefinierte Benutzeroberfläche ist eine optionale Funktion, mit der man Benutzeroberflächentests für Anwendungen erstellen und automatisch ausführen kann. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen)."

Die Testfunktion für die benutzerdefinierte Benutzeroberfläche ist eine optionale Funktion, mit der man Benutzeroberflächentests für Anwendungen erstellen und automatisch ausführen kann.

## Übersicht {#custom-ui-testing}

AEM bietet eine integrierte Suite mit [Cloud Manager-Qualitäts-Akzeptanztests](/help/implementing/cloud-manager/custom-code-quality-rules.md), um eine reibungslose Aktualisierung ihrer benutzerdefinierten Programme sicherzustellen. Insbesondere IT-Testgates ermöglichen bereits die Erstellung und Automatisierung von benutzerdefinierten Tests mithilfe von AEM-APIs.

UI-Tests werden in einem Docker-Bild zusammengefasst, um eine große Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Cypress, Selenium, Java und Maven sowie JavaScript). Ein Projekt für UI-Tests kann auch einfach mithilfe des [AEM-Projektarchetyps](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/overview) erzeugt werden.

Adobe empfiehlt die Verwendung von Cypress, da es Echtzeit-Neuladen und automatisches Warten ermöglicht, was Zeit spart und die Produktivität beim Testen steigert. Cypress bietet außerdem eine einfache und intuitive Syntax, die auch für Testneulinge leicht zu erlernen und anzuwenden ist.

UI-Tests werden als Teil eines bestimmten Qualitätstests für jede Cloud Manager-Pipeline mit dem Schritt](/help/implementing/cloud-manager/deploy-code.md) [**Testen der benutzerdefinierten Benutzeroberfläche** in [Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) oder optional [produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) ausgeführt. Alle UI-Tests, einschließlich Regression und neue Funktionen, ermöglichen die Erkennung und Meldung von Fehlern.

Im Gegensatz zu benutzerdefinierten Funktionstests, bei denen es sich um HTTP-Tests handelt, die in Java geschrieben wurden, können die UI-Tests ein Docker-Image mit Tests in einer beliebigen Sprache sein, sofern sie den unter [Erstellen von UI-Tests](#building-ui-tests) definierten Konventionen entsprechen.

>[!TIP]
>
>Adobe empfiehlt, Cypress für UI-Tests zu verwenden und dabei den Code aus dem [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress) einzusetzen.
> 
>Adobe bietet auch Beispiele für UI-Testmodule, die auf JavaScript mit WebdriverIO basieren (siehe [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)) und Java mit WebDriver (siehe [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver)).

## Erste Schritte mit Benutzeroberflächentests {#get-started-ui-tests}

In diesem Abschnitt werden die Schritte beschrieben, die zum Einrichten von Benutzeroberflächentests für die Ausführung in Cloud Manager erforderlich sind.

1. Entscheiden Sie, welches Test-Framework Sie verwenden möchten.

   * Verwenden Sie für Cypress (Standard) den Beispiel-Code aus dem [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress) oder verwenden Sie den Beispiel-Code, der automatisch im Ordner `ui.tests` Ihres Cloud Manager-Repositorys generiert wird.

   * Verwenden Sie für Cypress den Beispiel-Code aus dem [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright).

   * Verwenden Sie für Webdriver.IO den Beispiel-Code aus dem [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio).

   * Verwenden Sie für Selenium WebDriver den Beispiel-Code aus dem [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver).

   * Weitere Informationen zu anderen Programmiersprachen finden Sie im Abschnitt [Erstellen von UI-Tests](#building-ui-tests) in diesem Dokument zum Einrichten des Testprojekts.

1. Stellen Sie sicher, dass das Testen der UI gemäß Abschnitt [Kunden-Opt-in](#customer-opt-in) in diesem Dokument aktiviert ist.

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

Der Assembly-Deskriptor weist das Plug-in an, ein Archiv des Typs `.tar.gz` zu erstellen, und weist ihm den Klassifikator `ui-test-docker-context` zu. Darüber hinaus werden die Dateien aufgelistet, die im Archiv enthalten sein müssen, einschließlich der folgenden:

* Eine `Dockerfile`, obligatorisch für das Erstellen des Docker-Images
* Das Skript `wait-for-grid.sh`, dessen Zwecke unten beschrieben werden
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

Um eine Datei `testing.properties` in das Build-Artefakt aufzunehmen, fügen Sie eine `include`-Anweisung in die Datei `assembly-ui-test-docker-context.xml` ein.

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
>Falls Ihr Projekt diese Zeile nicht enthält, müssen Sie die Datei bearbeiten, um sich für Tests der Benutzeroberfläche anmelden zu können.
>
>Die Datei kann eine Zeile enthalten, in der empfohlen wird, sie nicht zu bearbeiten. Das liegt daran, dass die Datei in Ihr Projekt aufgenommen wurde, bevor Opt-in-Benutzeroberflächentests eingeführt wurden, und dass die Kundschaft die Datei nicht bearbeiten sollte. Dies kann ignoriert werden.

Wenn Sie die von Adobe bereitgestellten Beispiele verwenden:

* Für den JavaScript-basierten Ordner `ui.tests`, der auf der Grundlage des [AEM-Projektarchetyps](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) erstellt wurde, können Sie den folgenden Befehl ausführen, um die erforderliche Konfiguration hinzuzufügen.

  ```shell
  echo "ui-tests.version=1" > testing.properties
  
  if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
    awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
  fi
  ```

* In den von Adobe bereitgestellten Cypress- und Java-Selenium-Testbeispielen ist die Opt-in-Markierung bereits gesetzt.

## Schreiben von Benutzeroberflächentests {#writing-ui-tests}

In diesem Abschnitt werden die Konventionen beschrieben, denen das Docker-Image mit Ihren Benutzeroberflächentests folgen muss. Das Docker-Image basiert auf dem im vorherigen Abschnitt beschriebenen Docker-Build-Kontext.

### Umgebungsvariablen {#environment-variables}

Die folgenden Umgebungsvariablen werden zur Laufzeit an Ihr Docker-Image übergeben, abhängig von Ihrem Framework.

>[!NOTE]
>
> Diese Werte werden während der Pipeline-Ausführung automatisch festgelegt. Sie müssen nicht manuell als Pipeline-Variablen festgelegt werden.

| Variable | Beispiele | Beschreibung | Test-Framework |
|----------------------------|----------------------------------|----------------------------------------------------------------------------------------------------|---------------------|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Die URL des Selenium-Servers | Nur Selenium |
| `SELENIUM_BROWSER` | `chrome` | Die vom Selenium-Server verwendete Browser-Implementierung | Nur Selenium |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | Die URL der AEM-Autoreninstanz | Alle |
| `AEM_AUTHOR_USERNAME` | `admin` | Der Benutzername für die Anmeldung bei der AEM-Autoreninstanz | Alle |
| `AEM_AUTHOR_PASSWORD` | `admin` | Das Passwort für die Anmeldung bei der AEM-Autoreninstanz | Alle |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | Die URL der AEM-Veröffentlichungsinstanz | Alle* |
| `AEM_PUBLISH_USERNAME` | `admin` | Der Benutzername für die Anmeldung bei der AEM-Veröffentlichungsinstanz | Alle* |
| `AEM_PUBLISH_PASSWORD` | `admin` | Das Passwort für die Anmeldung bei der AEM-Veröffentlichungsinstanz | Alle* |
| `REPORTS_PATH` | `/usr/src/app/reports` | Der Pfad, in dem der XML-Bericht der Testergebnisse gespeichert werden muss | Alle |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Die URL, an die die Datei hochgeladen werden muss, damit sie für das Test-Framework verfügbar ist | Alle |
| `PROXY_HOST` | `proxy-host` | Der Host-Name des internen HTTP-Proxys, der vom Test-Framework verwendet werden soll | Alle außer Selenium |
| `PROXY_HTTPS_PORT` | `8071` | Der Proxy-Server-Listening-Anschluss für HTTPS-Verbindungen (kann leer sein) | Alle außer Selenium |
| `PROXY_HTTP_PORT` | `8070` | Der Proxy-Server-Listening-Anschluss für HTTP-Verbindungen (kann leer sein) | Alle außer Selenium |
| `PROXY_CA_PATH` | `/path/to/root_ca.pem` | Der Pfad zum Zertifizierungsstellen-Zertifikat, das vom Test-Framework verwendet werden soll | Alle außer Selenium |
| `PROXY_OBSERVABILITY_PORT` | `8081` | Der HTTP-Konsistenzprüfungsanschluss des Proxy-Servers | Alle außer Selenium |
| `PROXY_RETRY_ATTEMPTS` | `12` | Empfohlene Anzahl von Wiederholungsversuchen beim Warten auf Bereitschaft des Proxy-Servers | Alle außer Selenium |
| `PROXY_RETRY_DELAY` | `5` | Empfohlene Verzögerung zwischen Wiederholungsversuchen beim Warten auf Bereitschaft des Proxy-Servers | Alle außer Selenium |

`* these values will be empty if there is no publish instance`

Die Adobe-Testbeispiele bieten Hilfsfunktionen für den Zugriff auf die Konfigurationsparameter:

* Cypress: Verwenden der Standardfunktion `Cypress.env('VARIABLE_NAME')`
* JavaScript: Siehe das Modul [`lib/config.js`](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests.wdio/test-module/lib/config.js)
* Java: Siehe die Klasse [`Config`](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java)

### Generieren von Testberichten {#generate-test-reports}

Das Docker-Image muss Testberichte im JUnit-XML-Format generieren und in dem von der Umgebungsvariablen `REPORTS_PATH` angegebenen Pfad speichern. Das JUnit-XML-Format ist ein weitverbreitetes Format für Testergebnisberichte. Wenn das Docker-Image Java und Maven verwendet, können Standard-Testmodule wie das [Maven Surefire Plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) und das [Maven Failsafe Plug-in](https://maven.apache.org/surefire/maven-failsafe-plugin/) solche Berichte vorkonfiguriert erstellen.

Wenn das Docker-Image mit anderen Programmiersprachen oder Test-Runnern implementiert ist, lesen Sie in der Dokumentation der ausgewählten Tools nach, wie Sie JUnit-XML-Berichte erzeugen.

>[!NOTE]
>
>Das Ergebnis des Benutzeroberflächen-Testschritts wird nur anhand der Testberichte ausgewertet. Stellen Sie sicher, dass Sie den Bericht entsprechend Ihrer Testausführung generieren.
>
>Verwenden Sie Assertionen, anstatt einfach einen Fehler in STDERR zu protokollieren oder einen Exit-Code ungleich Null zurückzugeben, da Ihre Bereitstellungs-Pipeline sonst normal weiterlaufen kann.
>
>Wenn während der Testausführung ein HTTP-Proxy verwendet wurde, enthalten die Ergebnisse eine Datei `request.log`.

### Voraussetzungen {#prerequisites}

* Die Tests in Cloud Manager werden von technischen Admins ausgeführt.

>[!NOTE]
>
>Erstellen Sie für die Ausführung der Funktionstests von Ihrem lokalen Computer aus eine Benutzerin oder einen Benutzer mit Admin-ähnlichen Berechtigungen, um dasselbe Verhalten zu erzielen.

* Die Container-Infrastruktur, die für Funktionstests genutzt wird, ist durch die folgenden Grenzen begrenzt:

| Typ | Wert | Beschreibung |
|----------------------|-------|-----------------------------------------------------------------------|
| CPU | 2.0 | Menge an CPU-Zeit, die pro Testausführung reserviert wird. |
| Arbeitsspeicher | 1Gi | Menge des für den Test zugewiesenen Speichers; Wert in Gibibyte. |
| Zeitüberschreitung | 30m | Die Dauer, nach der der Test beendet wird. |
| Empfohlene Dauer | 15m | Adobe empfiehlt, Tests so zu schreiben, dass sie diese Dauer nicht überschreiten. |

>[!NOTE]
>
> Wenn Sie weitere Ressourcen benötigen, erstellen Sie einen Fall für die Kundenunterstützung und beschreiben Sie Ihren Anwendungsfall. Unser Team wird Ihre Anfrage überprüfen und entsprechende Unterstützung anbieten.

## Selenium-spezifische Details

>[!NOTE]
>
>Dieser Abschnitt gilt nur, wenn Selenium die ausgewählte Testinfrastruktur ist.

### Warten auf Selenium {#waiting-for-selenium}

Bevor die Tests beginnen, muss das Docker-Image sicherstellen, dass der Selenium-Server betriebsbereit ist. Das Warten auf den Selenium-Service erfolgt in zwei Schritten.

1. Lesen der URL des Selenium-Service aus der Umgebungsvariablen `SELENIUM_BASE_URL`.
1. Abrufen des von der Selenium-API bereitgestellten [Statusendpunkts](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) in regelmäßigen Abständen.

Sobald der Statusendpunkt von Selenium positiv antwortet, können die Tests beginnen.

Die Testbeispiele der Adobe-Benutzeroberfläche behandeln dies mit dem Skript `wait-for-grid.sh`, das beim Start des Dockers ausgeführt wird und die tatsächliche Testausführung erst startet, wenn das Raster bereit ist.

### Erfassen von Screenshots und Videos {#capture-screenshots}

Das Docker-Bild kann zusätzliche Testausgaben generieren (z. B. Screenshots oder Videos) und sie in dem Pfad speichern, der durch die Umgebungsvariable `REPORTS_PATH` angegeben wird. Jede Datei, die sich unter dem Verzeichnis `REPORTS_PATH` befindet, wird in das Testergebnisarchiv aufgenommen.

Die von Adobe bereitgestellten Testbeispiele erstellen standardmäßig Screenshots für fehlgeschlagene Tests.

Mithilfe der Hilfsfunktionen können Sie Screenshots durch Ihre Tests erstellen.

* JavaScript: [Befehl takeScreenshot](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java: [Befehle](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java)

Wenn während der Ausführung eines Benutzeroberflächen-Tests ein Testergebnisarchiv erstellt wird, können Sie es über die Schaltfläche `Download Details` unter dem Schritt [**Benutzerdefinierte Benutzeroberflächentests** aus Cloud Manager herunterladen](/help/implementing/cloud-manager/deploy-code.md).

### Hochladen von Dateien {#upload-files}

Tests müssen manchmal Dateien in das zu testende Programm hochladen. Um die Bereitstellung von Selenium in Bezug auf Ihre Tests flexibel zu halten, ist es nicht möglich, ein Asset direkt in Selenium hochzuladen. Stattdessen sind für das Hochladen einer Datei die folgenden Schritte erforderlich.

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

## Details zu Cypress

>[!NOTE]
>
>Dieser Abschnitt gilt nur, wenn Cypress die ausgewählte Testinfrastruktur ist.

### Einrichten eines HTTP-Proxys

Der Einstiegspunkt des Docker-Containers muss den Wert der Umgebungsvariablen `PROXY_HOST` berücksichtigen.

Wenn dieser Wert leer ist, sind keine zusätzlichen Schritte erforderlich und die Tests sollten ohne HTTP-Proxy ausgeführt werden.

Wenn er nicht leer ist, gilt für das Einstiegspunkt-Skript Folgendes:

1. Es muss eine HTTP-Proxy-Verbindung für die Ausführung von UI-Tests konfigurieren. Dies kann durch den Export der Umgebungsvariablen `HTTP_PROXY` erfolgen, die mithilfe der folgenden Werte erstellt wird:
   * Proxy-Host, bereitgestellt von der Variablen `PROXY_HOST`
   * Proxy-Port, der von der Variablen `PROXY_HTTPS_PORT` oder `PROXY_HTTP_PORT` bereitgestellt wird (die Variable mit einem nicht leeren Wert wird verwendet)
2. Es muss das Zertifizierungsstellen-Zertifikat festgelegt werden, das beim Herstellen einer Verbindung zum HTTP-Proxy verwendet wird. Seine Lage wird durch die Variable `PROXY_CA_PATH` angegeben.
   * Dies lässt sich durch den Export der Umgebungsvariablen `NODE_EXTRA_CA_CERTS` erreichen.
3. Es muss warten, bis der HTTP-Proxy bereit ist.
   * Anhand der Umgebungsvariablen `PROXY_HOST`, `PROXY_OBSERVABILITY_PORT`, `PROXY_RETRY_ATTEMPTS` und `PROXY_RETRY_DELAY` kann geprüft werden, ob er bereit ist.
   * Sie können dies mit einer cURL-Anfrage überprüfen, wobei cURL in Ihrer `Dockerfile` installiert sein muss.

Eine Beispielimplementierung finden Sie im Einstiegspunkt des Cypress-Beispieltestmoduls auf [GitHub](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/run.sh).

## Details zu Playwright

>[!NOTE]
>
> Dieser Abschnitt gilt nur, wenn Playwright die ausgewählte Testinfrastruktur ist.

### Einrichten eines HTTP-Proxys

>[!NOTE]
>
> In den vorgestellten Beispielen wird davon ausgegangen, dass Chrome als Projekt-Browser verwendet wird.

Ähnlich wie bei Cypress müssen Tests den HTTP-Proxy nutzen, wenn eine nicht leere Umgebungsvariable `PROXY_HOST` bereitgestellt wird.

Dazu müssen die folgenden Änderungen vorgenommen werden.

#### Dockerfile

Installieren Sie cURL und `libnss3-tools`, was `certutil.` bereitstellt

```dockerfile
RUN apt -y update \
    && apt -y --no-install-recommends install curl libnss3-tools \
    && rm -rf /var/lib/apt/lists/*
```

#### Entrypoint-Skript

Schließen Sie ein Bash-Skript ein, das Folgendes ausführt, falls die Umgebungsvariable `PROXY_HOST` bereitgestellt wird:

1. Proxy-bezogene Variablen exportieren, z. B. `HTTP_PROXY` und `NODE_EXTRA_CA_CERTS`
2. Das Proxy-CA-Zertifikat für Chrome unter Verwendung von `certutil` installieren
3. Warten, bis der HTTP-Proxy bereit ist (bzw. ihn bei einem Fehler beenden)

Beispielimplementierung:

```bash
# setup proxy environment variables and CA certificate
if [ -n "${PROXY_HOST:-}" ]; then
  if [ -n "${PROXY_HTTPS_PORT:-}" ]; then
    export HTTP_PROXY="https://${PROXY_HOST}:${PROXY_HTTPS_PORT}"
  elif [ -n "${PROXY_HTTP_PORT:-}" ]; then
    export HTTP_PROXY="http://${PROXY_HOST}:${PROXY_HTTP_PORT}"
  fi
  if [ -n "${PROXY_CA_PATH:-}" ]; then
    echo "installing certificate"
    mkdir -p $HOME/.pki/nssdb
    certutil -d sql:$HOME/.pki/nssdb -A -t "CT,c,c" -n "EaaS Client Proxy Root" -i $PROXY_CA_PATH
    export NODE_EXTRA_CA_CERTS=${PROXY_CA_PATH}
  fi
  if [ -n "${PROXY_OBSERVABILITY_PORT:-}" ] && [ -n "${HTTP_PROXY:-}" ]; then
    echo "waiting for proxy"
    curl --silent  --retry ${PROXY_RETRY_ATTEMPTS:-3} --retry-connrefused --retry-delay ${PROXY_RETRY_DELAY:-10} \
      --proxy ${HTTP_PROXY} --proxy-cacert ${PROXY_CA_PATH:-""} \
      ${PROXY_HOST}:${PROXY_OBSERVABILITY_PORT}
    if [ $? -ne 0 ]; then
      echo "proxy is not ready"
      exit 1
    fi
  fi
fi
```

#### Playwright-Konfiguration

Ändern Sie die Playwright-Konfiguration (z. B. in `playwright.config.js`), um einen Proxy zu verwenden, falls die Umgebungsvariable `HTTP_PROXY` festgelegt ist.

Beispielimplementierung:

```javascript
const proxyServer = process.env.HTTP_PROXY || ''
```

```javascript
// enable proxy if set
if (proxyServer !== '') {
 cfg.use.proxy = {
  server: proxyServer,
 }
}
```

>[!NOTE]
>
> Eine Beispielimplementierung finden Sie im Playwright-Beispieltestmodul auf [GitHub](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-playwright/).


## Ausführen von lokalen Benutzeroberflächentests {#run-ui-tests-locally}

Vor dem Aktivieren von UI-Tests in einer Cloud Manager-Pipeline wird empfohlen, die UI-Tests lokal entweder mit dem [AEM as a Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) oder mit einer tatsächlichen AEM as a Cloud Service-Instanz auszuführen.

### Cypress-Testbeispiel {#cypress-sample}

1. Öffnen Sie eine Shell und navigieren Sie zum Ordner `ui.tests/test-module` im Repository

1. Installieren Sie Cypress und andere Voraussetzungen

   ```shell
   npm install
   ```

1. Legen Sie die Umgebungsvariablen fest, die für die Testausführung erforderlich sind

   ```shell
   export AEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com
   export AEM_AUTHOR_USERNAME=<user>
   export AEM_AUTHOR_PASSWORD=<password>
   export AEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com
   export AEM_PUBLISH_USERNAME=<user>
   export AEM_PUBLISH_PASSWORD=<password>
   export REPORTS_PATH=target/
   ```

1. Führen Sie Tests mit einem der folgenden Befehle aus

   ```shell
   npm test              # Using default Cypress browser
   npm run test-chrome   # Using Google Chrome browser
   npm run test-firefox  # Using Firefox browser
   ```

>[!NOTE]
>
>Die Protokolldateien werden im Ordner `target/` Ihres Repositorys gespeichert.
>
>Weitere Informationen finden Sie unter [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/README.md).

### Beispieltest für JavaScript WebdriverIO {#javascript-sample}

1. Öffnen Sie eine Shell und navigieren Sie zum Ordner `ui.tests` im Repository

1. Führen Sie den folgenden Befehl aus, um die Tests mit Maven zu starten:

   ```shell
   mvn verify -Pui-tests-local-execution \
    -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_AUTHOR_USERNAME=<user> \
    -DAEM_AUTHOR_PASSWORD=<password> \
    -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_PUBLISH_USERNAME=<user> \
    -DAEM_PUBLISH_PASSWORD=<password>
   ```

>[!NOTE]
>
>* Dadurch wird eine eigenständige Selenium-Instanz gestartet und die Tests werden damit ausgeführt.
>* Die Protokolldateien werden im Ordner `target/reports` Ihres Repositorys gespeichert
>* Sie müssen sicherstellen, dass Sie die neueste Chrome-Version verwenden, da der Test die neueste Version von ChromeDriver automatisch zum Testen herunterlädt.
>
>Weitere Informationen finden Sie unter [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio).

### Playwright-Testbeispiel {#playwright-sample}

1. Öffnen Sie eine Shell und navigieren Sie zum Ordner `ui.tests` in Ihrem Repository

1. Führen Sie den folgenden Befehl aus, um ein Docker-Image mit Maven zu erstellen:

   ```shell
   mvn clean package -Pui-tests-docker-build
   ```

1. Führen Sie den folgenden Befehl aus, um die Tests mit Maven zu starten:

   ```shell
   mvn verify -Pui-tests-docker-execution \
    -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_AUTHOR_USERNAME=<user> \
    -DAEM_AUTHOR_PASSWORD=<password> \
    -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_PUBLISH_USERNAME=<user> \
    -DAEM_PUBLISH_PASSWORD=<password>
   ```

>[!NOTE]
>
>Die Protokolldateien werden im Ordner `target/` Ihres Repositorys gespeichert.
>
>Weitere Informationen finden Sie unter [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright).


### Beispieltest für Java Selenium WebDriver {#java-sample}

1. Öffnen Sie eine Shell und navigieren Sie zum Ordner `ui.tests/test-module` im Repository

1. Führen Sie den folgenden Befehl aus, um die Tests mit Maven zu starten

   ```shell
   # Start selenium docker image
   # we mount /tmp/shared as a shared volume that will be used between selenium and the test module for uploads
   docker run -d -p 4444:4444 -v /tmp/shared:/tmp/shared selenium/standalone-chromium:latest
   
   # Run the tests using the previously started Selenium instance
   mvn verify -Pui-tests-local-execution -DSELENIUM_BASE_URL=http://<server>:4444
   ```

>[!NOTE]
>
>Die Protokolldateien werden im Ordner `target/reports` Ihres Repositorys gespeichert.
>
>Weitere Informationen finden Sie unter [AEM-Testbeispiele-Repository](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md).
