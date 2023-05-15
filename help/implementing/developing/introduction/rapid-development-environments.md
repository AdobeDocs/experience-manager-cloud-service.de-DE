---
title: Schnelle Entwicklungsumgebungen
description: Erfahren Sie, wie Sie schnelle Entwicklungsumgebungen (Rapid Development Environments) für schnelle Entwicklungsdurchläufe in einer Cloud-Umgebung nutzen können.
exl-id: 1e9824f2-d28a-46de-b7b3-9fe2789d9c68
source-git-commit: 0095cb1fff99a52f5a048833b3d5a65643c1056d
workflow-type: tm+mt
source-wordcount: '3325'
ht-degree: 97%

---

# Schnelle Entwicklungsumgebungen {#rapid-development-environments}

Zur Bereitstellung von Änderungen erfordern aktuelle Cloud-Entwicklungsumgebungen die Verwendung eines Prozesses, der umfassende Code-Sicherheits- und Qualitätsregeln anwendet, die als CI/CD-Pipeline bezeichnet werden. Für Situationen, in denen schnelle und iterative Änderungen erforderlich sind, hat Adobe schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs) eingeführt.

RDEs ermöglichen es Entwicklern, Änderungen schnell bereitzustellen und zu überprüfen und so den Zeitaufwand für das Testen von Funktionen zu minimieren, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren.

Sobald die Änderungen in einer RDE getestet wurden, können sie über die Cloud Manager-Pipeline in einer regulären Cloud-Entwicklungsumgebung bereitgestellt werden.

>[!VIDEO](https://video.tv.adobe.com/v/3415582/?quality=12&learn=on)


Sie können sich weitere Videos ansehen, in denen die [Einrichtung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup.html?lang=de), [Verwendung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use.html?lang=de) und der [Entwicklungslebenszyklus](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/development-life-cycle.html?lang=de) mit RDE gezeigt werden.

## Einführung {#introduction}

RDEs können für Code-, Inhalts- und Apache- oder Dispatcher-Konfigurationen verwendet werden. Im Gegensatz zu regulären Cloud-Entwicklungsumgebungen können Entwickler lokale Befehlszeilen-Tools verwenden, um lokal in einer RDE erstellten Code zu synchronisieren.

Jedes Programm verfügt über eine RDE. Bei Sandbox-Konten werden sie nach einigen Stunden Nichtverwendung in den Ruhezustand versetzt.

Nach der Erstellung werden RDEs auf die neueste AEM Version eingestellt. Beim Zurücksetzen der RDE, das mit Cloud Manager durchgeführt werden kann, wird die RDE überprüft und auf die neueste AEM Version festgelegt.

Normalerweise wird eine RDE immer nur von einem einzelnen Entwickler zum Testen und Debuggen einer bestimmten Funktion verwendet. Wenn die Entwicklungssitzung abgeschlossen ist, kann die RDE für die nächste Verwendung in einen Standardstatus zurückgesetzt werden.

Für Produktionsprogramme (ohne Sandbox) können zusätzliche RDEs lizenziert werden.

## Aktivieren einer RDE in einem Programm {#enabling-rde-in-a-program}

Führen Sie diese Schritte aus, um Cloud Manager zum Erstellen einer RDE für Ihr Programm zu verwenden.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, dem Sie eine RDE hinzufügen möchten, um deren Details anzuzeigen.

   * RDEs können sowohl zu [Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) als auch zu [Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) hinzugefügt werden.

1. Klicken Sie auf der Seite **Programmübersicht** auf der Karte **Umgebungen** auf **Umgebung hinzufügen**, um eine Umgebung hinzuzufügen.

   ![Karte „Umgebung“](/help/implementing/cloud-manager/assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

      ![Registerkarte Umgebungen](/help/implementing/cloud-manager/assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Im Dialogfeld **Umgebung hinzufügen** wird Folgendes angezeigt:

   * Wählen Sie unter der Überschrift **Umgebungstyp auswählen** die Option **Schnelle Entwicklung** aus.
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Umgebungstyp angezeigt.
   * Geben Sie in **Name** einen Namen für die Umgebung an.
   * Geben Sie eine optionale **Beschreibung** für die Umgebung an.
   * Wählen Sie eine **Cloud-Region**.

   ![Dialogfeld „Umgebung hinzufügen“](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Der Bildschirm **Überblick** zeigt nun in der Karte **Umgebungen** Ihre neue Umgebung an.

Nach der Erstellung werden RDEs auf die neueste AEM Version eingestellt. Das Zurücksetzen der RDE, das auch mit Cloud Manager durchgeführt werden kann, führt einen Zyklus der RDE durch und setzt sie auf die neueste AEM Version.

Weitere Informationen zur Verwendung von Cloud Manager zum Erstellen von Umgebungen, zum Verwalten von Zugriffsrechten und zum Zuweisen benutzerdefinierter Domains finden Sie in der [Dokumentation zu Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

## Installieren der RDE-Befehlszeilen-Tools {#installing-the-rde-command-line-tools}

Nachdem Sie mit Cloud Manager eine RDE für Ihr Programm hinzugefügt haben, können Sie damit interagieren, indem Sie die Befehlszeilen-Tools wie in den folgenden Schritten beschrieben einrichten:

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie die neueste Version von [Node und NPM installiert haben](https://nodejs.org/de/download/), damit Adobe I/O CLI und die zugehörigen Plugins richtig funktionieren.


1. Installieren Sie die Adobe I/O-CLI-Tools gemäß dem [hier](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) beschriebenen Verfahren.
1. Installieren Sie das Cloud Manager-Plugin der Adobe I/O-CLI-Tools und konfigurieren Sie diese wie [hier](https://github.com/adobe/aio-cli-plugin-cloudmanager) beschrieben.
1. Installieren Sie das AEM RDE-Plug-in der Adobe I/O CLI-Tools, indem Sie die folgenden Befehle ausführen:

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Konfigurieren Sie das Cloud Manager-Plugin für Ihre Organisations-ID:

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   und ersetzen Sie die alphanumerische Zeichenfolge durch Ihre eigene Organisations-ID, die mithilfe des [hier](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de#concept_EA8AEE5B02CF46ACBDAD6A8508646255) beschriebenen Verfahrens abgerufen werden kann.

1. Konfigurieren Sie anschließend Ihre Programm-ID:

   `aio config:set cloudmanager_programid 12345`

1. Konfigurieren Sie danach die Umgebungs-ID, mit der die RDE verknüpft werden soll:

   `aio config:set cloudmanager_environmentid 123456`

1. Nachdem Sie das Plug-in konfiguriert haben, melden Sie sich an, indem Sie Folgendes durchführen:

   `aio login`

   Die Antwort auf eine erfolgreiche Anmeldung sollte der unten dargestellten Ausgabe ähneln, Sie können jedoch die hier angezeigten Werte ignorieren.

   ```
   ...
   You are currently in:
   1. Org: <no org selected>
   2. Project: <no project selected>
   3. Workspace: <no workspace selected>
   ```

1. Überprüfen Sie, ob die Anmeldung erfolgreich abgeschlossen wurde, indem Sie Folgendes ausführen:

   `aio cloudmanager:list-programs`

   Daraufhin sollten alle Programme unter Ihrer konfigurierten Organisation aufgelistet werden.

   Beachten Sie, dass Sie Mitglied des Cloud Manager-Produktprofils **Entwickler - Cloud Service** sein müssen. Weitere Informationen finden Sie auf [dieser Seite](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer).

   Andernfalls können Sie auch dadurch bestätigen, dass Sie über diese Entwicklerrolle verfügen, indem Sie sich bei der Entwicklerkonsole anmelden, indem Sie diesen Befehl ausführen:

   `aio cloudmanager:environment:open-developer-console`

   >[!TIP]
   >
   >Wenn Sie den Fehler `Warning: cloudmanager:list-programs is not a aio command.` sehen, müssen Sie den [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager) installieren, indem Sie den folgenden Befehl ausführen:
   >
   >
   ```
   >aio plugins:install @adobe/aio-cli-plugin-cloudmanager
   >```

Weitere Informationen und Demonstrationen finden Sie im Video-Tutorial [Einrichten einer RDE](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup.html?lang=de).

## Verwenden der RDE bei der Entwicklung einer neuen Funktion {#using-rde-while-developing-a-new-feature}

Adobe empfiehlt den folgenden Workflow für die Entwicklung einer neuen Funktion:

* Wenn ein Zwischenmeilenstein erreicht und erfolgreich lokal mit dem AEM as a Cloud Service-SDK validiert wurde, sollte der Code in einen Git-Funktionszweig committet werden, der noch nicht Teil des Hauptstamms ist. Der Commit an Git ist jedoch optional. Was ein „Zwischenmeilenstein“ ist, hängt vom jeweiligen Team ab. Beispiele sind einige neue Code-Zeilen, ein halber Arbeitstag oder das Fertigstellen einer Unterfunktion.

* Setzen Sie die RDE zurück, wenn sie von einer anderen Funktion verwendet wurde und Sie sie [auf den Standardstatus zurücksetzen](#reset-rde) möchten. <!-- Alexandru: hiding for now, please don't delete This can be done via [Cloud Manager](#reset-the-rde-cloud-manager) or via the [command line](#reset-the-rde-command-line). -->Das Zurücksetzen dauert einige Minuten, und der gesamte vorhandene Inhalt samt Code wird gelöscht. Sie können den RDE-Statusbefehl verwenden, um zu bestätigen, dass die RDE bereit ist. Die RDE wird mit der neuesten Version von AEM wiederhergestellt.

   >[!IMPORTANT]
   >
   > Wenn Ihre Staging- und Produktionsumgebungen keine automatischen AEM-Release-Updates erhalten und sich weit hinter der neuesten AEM-Release-Version befinden, achten Sie darauf, dass der Code, der auf der RDE ausgeführt wird, möglicherweise nicht mit der Funktionsweise des Codes für Staging und Produktion übereinstimmt. In diesem Fall ist es besonders wichtig, den Code beim Staging gründlich zu testen, bevor er in der Produktion bereitgestellt wird.


* Synchronisieren Sie den lokalen Code über die RDE-Befehlszeilenschnittstelle mit der RDE. Zu den Optionen gehören die Installation eines Inhaltspakets, eines bestimmten Bundles, einer OSGi-Konfigurationsdatei, einer Inhaltsdatei und einer ZIP-Datei einer Apache/Dispatcher-Konfiguration. Es ist auch möglich, auf ein Remote-Inhaltspaket zu verweisen. Weitere Informationen finden Sie unter [RDE-Befehlszeilen-Tools](#rde-cli-commands). Mit dem Statusbefehl können Sie überprüfen, ob die Bereitstellung erfolgreich war. Optional können Sie Package Manager verwenden, um Inhaltspakete zu installieren.

* Testen Sie den Code in der RDE. Autoren- und Veröffentlichungs-URLs sind in Cloud Manager verfügbar.

* Wenn sich der Code nicht wie erwartet verhält, verwenden Sie standardmäßige Debugging-Methoden, um den Fehler zu identifizieren, und nehmen Sie die entsprechenden Änderungen vor. Verwenden Sie die lokale CLI, um den Code mit der RDE zu synchronisieren, ohne die Code-Änderungen an Git zu committen (da sie nicht validiert wurden). Wiederholen Sie diese Schritte, bis das Problem behoben ist.

* Sobald sich der Code erwartungsgemäß verhält, committen Sie den Code an den Git-Funktionszweig.

* Der mit der RDE synchronisierte Code verwendet keine Cloud Manager-Pipeline. Daher sollten Sie jetzt eine Nicht-Produktions-Pipeline von Cloud Manager verwenden, um den Git-Funktionszweig in der Cloud-Entwicklungsumgebung bereitzustellen. Dadurch wird überprüft, ob der Code die Cloud Manager-Qualitätstests erfolgreich durchläuft, und Sie können sicher sein, dass der Code später über die Cloud Manager-Produktions-Pipeline erfolgreich bereitgestellt wird.

* Wiederholen Sie die obigen Schritte für jeden Zwischenmeilenstein, bis der gesamte Code für die Funktion bereit ist und sowohl in der RDE als auch in der Cloud-Entwicklungsumgebung ordnungsgemäß ausgeführt wird.

* Stellen Sie den Code über die Cloud Manager-Produktions-Pipeline in der Produktionsumgebung bereit.

## Verwenden der RDE zum Debuggen einer vorhandenen Funktion {#use-rde-to-debug-an-existing-feature}

Der Workflow entspricht in etwa der Entwicklung einer neuen Funktion. Der Unterschied besteht darin, dass der mit der RDE synchronisierte Code die Git-Markierung des Codes enthält, der in die Umgebung gepusht wurde, in der das Problem aufgetreten ist. Darüber hinaus kann es nützlich sein, Inhalte bereitzustellen, die der vorgelagerten Umgebung entsprechen. Dies kann durch den Export und Import von Inhaltspaketen erreicht werden.

## Zusammenarbeit mehrerer Entwickelnden in derselben RDE {#multiple-developers-collaborating-on-the-same-rde}

Eine RDE unterstützt immer nur jeweils ein Projekt. Da Code von einer lokalen Entwicklungsumgebung mit der RDE-Umgebung synchronisiert wird, wird sie normalerweise von einem Entwickler bzw. einer Entwicklerin allein verwendet.

Bei sorgfältiger Koordinierung ist es jedoch möglich, dass mehrere Entwickelnde gleichzeitig an der Prüfung einer Funktion oder der Behebung eines Fehlers arbeiten. Entscheidend ist hierbei, dass alle Entwickelnden ihre lokalen Projekte synchron halten, sodass von einem Entwickler bzw. einer Entwicklerin vorgenommene Code-Änderungen von den anderen Entwickelnden übernommen werden. Andernfalls könnte ein Entwickler bzw. eine Entwicklerin versehentlich den Code anderer Entwickelnden überschreiben. Die empfohlene Vorgehensweise besteht darin, dass alle Entwickelnden ihre Änderungen vor der Synchronisierung mit der RDE an einen gemeinsam genutzten Git-Zweig committen, sodass die anderen Entwickelnden die Änderungen abrufen, bevor sie selbst Änderungen vornehmen.

## Befehle von RDE-Befehlszeilen-Tools {#rde-cli-commands}

### Hilfe/allgemeine Informationen {#help}

* Um eine Liste von Befehlen anzuzeigen, geben Sie Folgendes ein:

   `aio aem:rde`

* Um detaillierte Hilfe zu einem Befehl zu erhalten, geben Sie Folgendes ein:

   `aio aem rde <command> --help`

### Bereitstellen in einer RDE {#deploying-to-rde}

In diesem Abschnitt wird die Verwendung der RDE-CLI zum Bereitstellen, Installieren oder Aktualisieren von Bundles, OSGi-Konfigurationen, Inhaltspaketen, einzelnen Inhaltsdateien und Apache- oder Dispatcher-Konfigurationen beschrieben.

Das allgemeine Nutzungsmuster lautet `aio aem:rde:install <artifact>`.

Nachfolgend finden Sie einige Beispiele:

<u>Bereitstellen eines Inhaltspakets</u>

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

Die Antwort auf eine erfolgreiche Bereitstellung sieht ähnlich der folgenden aus:

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

Optional können Sie auf ein Remote-Repository verweisen:

`aio aem:rde:install -t content-package "https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip"`

Standardmäßig werden die Artefakte sowohl auf der Autor- als auch auf der Veröffentlichungs-Ebene bereitgestellt, aber mit der Markierung „s“ kann eine bestimmte Ebene ausgewählt werden.

Jedes AEM kann bereitgestellt werden, z. B. Pakete mit Code, Inhalt oder einem [Container-Paket](/help/implementing/developing/introduction/aem-project-content-package-structure.md#container-packages) (auch als &quot;all&quot;-Paket bezeichnet).

>[!IMPORTANT]
>
>Die Dispatcher-Konfiguration für das Projekt WKND wird nicht über die Installation des obigen Inhaltspakets bereitgestellt. Sie müssen sie separat bereitstellen, indem Sie die Schritte „Bereitstellen einer Apache-/Dispatcher-Konfiguration“ befolgen.

<u>Bereitstellen einer OSGi-Konfiguration</u>

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

Die Antwort auf eine erfolgreiche Bereitstellung sieht ähnlich der folgenden aus:

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

<u>Bereitstellen eines Bundles</u>

Verwenden Sie zum Bereitstellen eines Bundles Folgendes:

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

Die Antwort auf eine erfolgreiche Bereitstellung sieht ähnlich der folgenden aus:

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

<u>Bereitstellen einer Inhaltsdatei</u>

Verwenden Sie zum Bereitstellen einer Inhaltsdatei Folgendes:

`aio aem:rde:install world.txt -p /apps/hello.txt`

Die Antwort auf eine erfolgreiche Bereitstellung sieht ähnlich der folgenden aus:

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

<u>Bereitstellen einer Apache-/Dispatcher-Konfiguration</u>

Für diese Art von Konfiguration muss die gesamte Ordnerstruktur in Form einer ZIP-Datei vorliegen.

Aus dem Modul `dispatcher` eines AEM-Projekts können Sie die Dispatcher-Konfiguration komprimieren, indem Sie den folgenden Maven-Befehl ausführen:

`mvn clean package`

oder mithilfe des folgenden ZIP-Befehls aus dem Verzeichnis `src` des Moduls `dispatcher`:

`zip -y -r dispatcher.zip .`

Stellen Sie dann die Konfiguration mithilfe dieses Befehls bereit:

`aio aem:rde:install target/aem-guides-wknd.dispatcher.cloud-X.X.X-SNAPSHOT.zip`

>[!TIP]
>
>Der obige Befehl setzt voraus, dass Sie die Dispatcher-Konfigurationen des Projekts [WKND](https://github.com/adobe/aem-guides-wknd) bereitstellen. Bitte stellen Sie sicher, dass Sie die `X.X.X` durch die entsprechende WKND-Projektversionsnummer oder Ihre projektspezifische Versionsnummer ersetzen, wenn Sie die Dispatcher-Konfiguration Ihres Projekts bereitstellen.

>[!NOTE]
>
>RDE unterstützt die Dispatcher-Konfiguration &quot;Flexibler Modus&quot;, nicht jedoch die Dispatcher-Konfiguration &quot;Legacy-Modus&quot;. Siehe [Dispatcher-Dokumentation](/help/implementing/dispatcher/disp-overview.md#validation-debug) für Informationen zu den beiden Modi. Weitere Informationen finden Sie in der Dokumentation unter [Migration in den flexiblen Modus](/help/implementing/dispatcher/validation-debug.md#migrating), falls noch nicht geschehen.

Bei erfolgreicher Bereitstellung wird eine Antwort generiert, die der folgenden ähnelt:

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

Code, der in der RDE bereitgestellt wird, unterliegt keiner Cloud Manager-Pipeline und den zugehörigen Quality Gates. Der Code durchläuft jedoch eine Analyse, die ggf. Fehler meldet, wie im folgenden Code-Beispiel dargestellt:

```
$ aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar
...
#19: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D74FR1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
Logs:
The analyser found the following errors for author :
[requirements-capabilities] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Artifact com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8 requires [org.apache.felix.gogo.jline/1.1.8] org.apache.felix.gogo; filter:="(&(org.apache.felix.gogo=command.implementation)(version>=1.0.0)(!(version>=2.0.0)))"; effective:=active in start level 20 but no artifact is providing a matching capability in this start level.
[api-regions-exportsimports] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Bundle org.apache.felix.gogo.jline:1.1.8 is importing package(s) [org.jline.builtins, org.jline.utils, org.apache.felix.service.command, org.apache.felix.service.threadio, org.jline.terminal, org.jline.reader, org.apache.felix.gogo.runtime, org.jline.reader.impl] in start level 20 but no bundle is exporting these for that start level.
The analyser found the following errors for publish :
[requirements-capabilities] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Artifact com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8 requires [org.apache.felix.gogo.jline/1.1.8] org.apache.felix.gogo; filter:="(&(org.apache.felix.gogo=command.implementation)(version>=1.0.0)(!(version>=2.0.0)))"; effective:=active in start level 20 but no artifact is providing a matching capability in this start level.
[api-regions-exportsimports] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Bundle org.apache.felix.gogo.jline:1.1.8 is importing package(s) [org.jline.builtins, org.jline.utils, org.apache.felix.service.command, org.apache.felix.service.threadio, org.jline.terminal, org.jline.reader, org.apache.felix.gogo.runtime, org.jline.reader.impl] in start level 20 but no bundle is exporting these for that start level.
```

Das obige Code-Beispiel veranschaulicht das Verhalten, wenn ein Bundle nicht aufgelöst wird. In diesem Fall wird es „bereitgehalten“ und erst dann installiert, wenn die jeweiligen Anforderungen (in diesem Fall fehlende Importe) durch Installation von weiterem Code erfüllt werden.

### Überprüfen des Status der RDE {#checking-rde-status}

Sie können die RDE-CLI verwenden, um zu überprüfen, ob die Umgebung bereit für die Bereitstellung ist und welche Bereitstellungen über das RDE-Plug-in vorgenommen wurden.

Wird ausgeführt:

`aio aem:rde:status`

Rückgabe:

```
Info for cm-p12345-e987654
Environment: Ready
- Bundles Author:
 com.adobe.granite.sample.demo-1.0.0.SNAPSHOT
- Bundles Publish:
 com.adobe.granite.sample.demo-1.0.0.SNAPSHOT
- Configurations Author:
 com.adobe.granite.demo.MyServlet
- Configurations Publish:
 com.adobe.granite.demo.MyServlet
```

Selbst wenn der Befehl einen Hinweis zur Bereitstellung von Instanzen zurückgibt, können Sie mit der nächsten Aktualisierung fortfahren, doch Ihre letzte Aktualisierung ist möglicherweise noch nicht in der Instanz sichtbar.

### Anzeigen des Bereitstellungsverlaufs {#show-deployment-history}

Sie können den Verlauf der in der RDE vorgenommenen Bereitstellungen überprüfen, indem Sie Folgendes ausführen:

`aio aem:rde:history`

Daraufhin wird eine Antwort in folgendem Format zurückgegeben:

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### Löschen aus einer RDE {#deleting-from-rde}

Sie können Konfigurationen und Bundles, die zuvor in einer RDE bereitgestellt wurden, über das CLI-Tool löschen. Verwenden Sie den Befehl `status`, um eine Liste der zu löschenden Elemente zu erhalten. Diese Liste enthält `bsn` für Bundles und `pid` für Konfigurationen, auf die im Löschbefehl verwiesen werden muss.

Wenn beispielsweise `com.adobe.granite.demo.MyServlet.cfg.json` installiert wurde, dann lautet `bsn` einfach `com.adobe.granite.demo.MyServlet`, ohne das Suffix **cfg.json**.

Das Löschen von Inhaltspaketen oder Inhaltsdateien wird nicht unterstützt. Um sie zu entfernen, sollte die RDE zurückgesetzt werden, sodass der Standardzustand wiederhergestellt wird.

Weitere Informationen finden Sie im folgenden Beispiel:

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

Weitere Informationen und Demonstrationen finden Sie im Video-Tutorial [Verwendung von RDE-Befehlen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use.html?lang=de).

## Zurücksetzen {#reset-rde}

Durch Zurücksetzen der RDE werden der gesamte benutzerdefinierte Code, Konfigurationen und Inhalte aus der Autoren- und Veröffentlichungsinstanz entfernt. Dies kann beispielsweise nützlich sein, wenn die RDE zum Testen einer bestimmten Funktion verwendet wurde und Sie sie auf den Standardzustand zurücksetzen möchten, um eine andere Funktion zu testen.

Durch Zurücksetzen wird die RDE auf die neueste AEM Version festgelegt.

<!-- Alexandru: hiding for now, please don't delete

Resetting can be done via [Cloud Manager](#reset-the-rde-cloud-manager) or via the [command line](#reset-the-rde-command-line). Resetting takes a few minutes and all existing content and code will be deleted from the RDE.

>[NOTE!]
>
>You must be assigned the Cloud Manager Developer role in order to be able to use the reset feature. If not, a reset action will result in an error.

### Reset the RDE via Command Line {#reset-the-rde-command-line}

You can reset the RDE and return it to a default state by running:

`aio aem:rde:reset`

This usually takes a few minutes. Use the [status command](#checking-rde-status) to check when the environment is ready again.

### Reset the RDE in Cloud Manager {#reset-the-rde-cloud-manager} -->

Sie können Cloud Manager verwenden, um Ihre RDE zurückzusetzen, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie die RDE zurücksetzen möchten.

1. Klicken Sie auf der Seite **Überblick** auf die Registerkarte **Umgebungen** oben im Bildschirm.

   ![Registerkarte Umgebungen](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * Alternativ können Sie auf die Schaltfläche **Alle anzeigen** auf der Karte **Umgebungen** klicken, um direkt zur Registerkarte **Umgebungen** zu gelangen.

      ![Option „Alle anzeigen“](/help/implementing/cloud-manager/assets/environment-showall.png)

1. Das Fenster **Umgebungen** wird geöffnet. Darin sind alle Umgebungen für das Programm aufgelistet.

   ![Registerkarte „Umgebungen“](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten für die RDE, die Sie zurücksetzen möchten, und wählen Sie dann **Zurücksetzen** aus.

   ![Anzeigen von Umgebungsdetails](/help/implementing/cloud-manager/assets/rde-reset.png)

1. Bestätigen Sie, dass Sie die RDE zurücksetzen möchten, indem Sie im Dialogfeld auf **Zurücksetzen** klicken.

   ![Bestätigen des Zurücksetzungsprozesses](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager bestätigt über eine Banner-Benachrichtigung, dass der Zurücksetzungsprozess gestartet wurde.

   ![Zurücksetzen der Banner-Benachrichtigung](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

Nach dem Start des RDE-Zurücksetzungsprozesses dauert es in der Regel einige Minuten, bis er abgeschlossen ist und die Umgebung in den Standardzustand zurückversetzt wird. Der Status des Zurücksetzungsprozesses kann jederzeit in der Spalte **Status** der Registerkarte **Umgebungen** oder im Fenster **Umgebungen** eingesehen werden.

![RDE-Zurücksetzungsstatus](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

Sie können die RDE auch direkt auf der Seite **Übersicht** auf der Karte **Umgebungen** mit der Schaltfläche mit den Auslassungszeichen zurücksetzen.

![RDE über die Karte „Umgebungen“ zurücksetzen](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Weitere Informationen zur Verwendung von Cloud Manager zur Verwaltung Ihrer Umgebungen finden Sie in der [Dokumentation zu Cloud Manager](/help/implementing/cloud-manager/manage-environments.md).

## Ausführungsmodi {#runmodes}

RDE-spezifische OSGi-Konfigurationen können mithilfe von Suffixen auf den Ordnernamen angewendet werden, wie in den folgenden Beispielen:

* `config.rde`
* `config.author.rde`
* `config.publish.rde`

Allgemeine Informationen zu den Ausführungsmodi finden Sie in der [Dokumentation Ausführungsmodi](/help/implementing/deploying/overview.md#runmodes).

>[!NOTE]
>
>Die RDE-OSGi-Konfiguration ist insofern eindeutig, als sie die Werte aller OSGi-Eigenschaften erbt, die durch den `dev`-Ausführungsmodus des Bundles deklariert wurden.

RDEs unterscheiden sich von anderen Umgebungen darin, dass Inhalte in einem install.rde-Ordner (bzw. install.author.rde oder install.publish.rde) unter /apps installiert werden können. Auf diese Weise können Sie Inhalte mithilfe des Befehlszeilen-Tools an Git übertragen und an die RDE übermitteln.

## Mit Inhalt füllen {#populating-content}

Wenn eine RDE zurückgesetzt wird, werden alle Inhalte entfernt, sodass, falls gewünscht, explizit Maßnahmen ergriffen werden müssen, um Inhalte hinzuzufügen. Als Best Practice empfiehlt es sich, einen Satz von Inhalten zusammenzustellen, die als Testinhalt für die Validierung oder das Debugging von Funktionen in der RDE verwendet werden können. Es gibt mehrere mögliche Strategien zum Ausfüllen der RDE mit diesem Inhalt:

1. Synchronisieren Sie das Inhaltspaket explizit mit der RDE mithilfe der Befehlszeilen-Tools

1. Platzieren und übertragen Sie den Beispielinhalt in Git in einem install.rde-Ordner unter /apps und synchronisieren Sie dann das übergeordnete Inhaltspaket mit der RDE mithilfe der Befehlszeilen-Tools.

1. Verwenden Sie die [Content Copy-Tool](/help/implementing/developing/tools/content-copy.md) , um einen definierten Inhalt aus einer Produktions-, Staging- oder Entwicklungsumgebung oder aus einer anderen RDE zu kopieren.

1. Verwenden Sie den Package Manager

Beachten Sie, dass Sie beim Synchronisieren von Inhaltspaketen auf 1 GB beschränkt sind.

## Protokollierung {#logging}

Protokollebenen können durch Ändern von OSGi-Konfigurationen festgelegt werden. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/introduction/logging.md).

## Worin unterscheiden sich RDEs von Cloud-Entwicklungsumgebungen? {#how-are-rds-different-from-cloud-development-environments}

Die RDE ähnelt zwar in vielerlei Hinsicht einer Cloud-Entwicklungsumgebung, es gibt jedoch einige geringfügige Unterschiede in der Architektur, um eine schnelle Synchronisierung von Code zu ermöglichen. Ein Unterschied besteht darin, wie Code zur RDE transferiert wird: Bei RDEs wird der Code über eine lokale Entwicklungsumgebung synchronisiert, während bei Cloud-Entwicklungsumgebungen der Code über Cloud Manager bereitgestellt wird.

Aus diesen Gründen wird empfohlen, den Code nach seiner Validierung in einer RDE mithilfe der Nicht-Produktions-Pipeline in einer Cloud-Entwicklungsumgebung bereitzustellen. Testen Sie schließlich den Code, bevor Sie ihn mit der Produktions-Pipeline bereitstellen.

Beachten Sie außerdem die folgenden Überlegungen:

* RDEs enthalten keine Vorschauebene
* RDEs unterstützen derzeit nicht das Anzeigen und Debuggen von Frontend-Code, der mithilfe der Frontend-Pipeline von Cloud Manager bereitgestellt wird.
* RDEs unterstützen derzeit nicht den Vorabversionskanal.


## Wie viele RDEs benötige ich? {#how-many-rds-do-i-need}

Für jede lizenzierte Lösung steht eine RDE zur Verfügung. Darüber hinaus bietet Adobe zusätzliche RDEs an, die für Produktionsprogramme (ohne Sandbox) lizenziert werden können.

Die Anzahl der benötigten RDEs hängt von der Zusammensetzung und den Prozessen eines Unternehmens ab. Das flexibelste Model ist das, bei dem ein Unternehmen für jedes Mitglied seines Entwicklungsteams von AEM Cloud Service eine dedizierte RDE erwirbt. In diesem Modell können alle Entwickelnden den eigenen Code auf der RDE testen, ohne sich mit anderen Team-Mitgliedern darüber abzustimmen, ob eine RDE-Umgebung verfügbar ist.

Auf der anderen Seite kann ein Team mit einer einzelnen RDE interne Prozesse verwenden, um zu koordinieren, welche Person die Umgebung zu einem bestimmten Zeitpunkt verwenden kann. Dies kann der Fall sein, wenn eine Person des Entwicklungs-Teams einen Zwischenfunktions-Meilenstein erreicht hat und bereit ist, diesen in einer Cloud-Umgebung zu validieren, in der schnell die benötigten Änderungen vorgenommen werden können.

Bei einem Zwischenmodell kauft ein Unternehmen eine Reihe von RDEs, sodass eine höhere Wahrscheinlichkeit besteht, dass ein nicht verwendetes RDE verfügbar ist. Eine Strategie könnte darin bestehen, pro Scrum-Team oder Hauptfunktion eine RDE zuzuweisen. Interne Prozesse können zur Koordinierung der Nutzung der Umgebungen verwendet werden.

## Wie unterscheidet sich eine schnelle Entwicklungsumgebung (RDE) in AEM Forms Cloud Service von anderen Umgebungen? {#how-are-forms-rds-different-from-cloud-development-environments}

Entwicklerinnen und Entwickler von Forms können die schnelle Entwicklungsumgebung bei AEM Forms Cloud Service verwenden, um schnell adaptive Formulare, Workflows und Anpassungen zu entwickeln, z. B. die Anpassung von Kernkomponenten, Integrationen mit Drittanbietersystemen und mehr. Die schnelle Entwicklungsumgebung (RDE) bei AEM Forms Cloud Service unterstützt keine Kommunikations-APIs und Funktionen, für die ein Datensatzdokument erforderlich ist, z. B. das Generieren eines Datensatzdokuments bei der Übermittlung eines adaptiven Formulars. Die folgenden aufgelisteten Funktionen von AEM Forms sind in einer schnellen Enticklungsumgebung (RDE) nicht verfügbar:

* Konfigurieren eines Datensatzdokuments für ein adaptives Formular
* Generieren eines Datensatzdokuments bei Übermittlung eines adaptiven Formulars oder mit einem Workflow-Schritt
* Senden des Datensatzdokuments als Anhang mit der Aktion „E-Mail senden“ oder mit dem Schritt „E-Mail“ in einem Workflow
* Verwenden von Adobe Sign in einem adaptiven Formular oder in einem Workflow-Schritt
* Kommunikations-APIs

>[!NOTE]
>
> Es gibt keinen Unterschied zwischen der Benutzeroberfläche der schnellen Entwicklungsumgebung (RDE) und anderen Cloud Service-Umgebungen für Forms. Alle mit Datensatzdokument verbundenen Optionen, z. B. die Auswahl einer Datensatzdokumentvorlage für ein adaptives Formular, werden weiterhin in der Benutzeroberfläche angezeigt. Diese Umgebungen verfügen über keine Kommunikations-APIs und Datensatzdokument-Funktionen, um solche Optionen zu testen. Wenn Sie also eine Option auswählen, für die Kommunikations-APIs oder Datensatzdokumentfunktionen erforderlich sind, wird keine Aktion ausgeführt und eine Fehlermeldung angezeigt oder zurückgegeben.

## RDE-Tutorial

Informationen zu RDE in AEM as a Cloud Service finden Sie im Video-Tutorial [, das die Einrichtung, die Verwendung und den Entwicklungslebenszyklus veranschaulicht](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/overview.html?lang=de)
