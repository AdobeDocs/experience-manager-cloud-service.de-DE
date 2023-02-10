---
title: Schnelle Entwicklungsumgebungen
description: Erfahren Sie, wie Sie Rapid Development Environments für schnelle Entwicklungsdurchläufe in einer Cloud-Umgebung nutzen können.
source-git-commit: 400e9fa0263b3e9bdae10dc80d524b291f99496d
workflow-type: tm+mt
source-wordcount: '2898'
ht-degree: 6%

---


# Schnelle Entwicklungsumgebungen {#rapid-development-environments}

>[!AVAILABILITY]
>
>Diese Funktion soll im Laufe des Monats Februar schrittweise für Kunden eingeführt werden.

Um Änderungen bereitzustellen, erfordern aktuelle Cloud-Entwicklungsumgebungen die Verwendung eines Prozesses, der umfassende Code-Sicherheits- und Qualitätsregeln anwendet, die als CI/CD-Pipeline bezeichnet werden. Für Situationen, in denen schnelle und iterative Änderungen erforderlich sind, hat Adobe Rapid Development Environments (RDEs für kurze Zeit) eingeführt.

RDEs ermöglichen es Entwicklern, Änderungen schnell bereitzustellen und zu überprüfen und so den Zeitaufwand für das Testen von Funktionen zu minimieren, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren.

Sobald die Änderungen in einer RDE getestet wurden, können sie über die Cloud Manager-Pipeline in einer regulären Cloud-Entwicklungsumgebung bereitgestellt werden.

## Einführung {#introduction}

RDEs können für Code-, Inhalts- und Apache- oder Dispatcher-Konfigurationen verwendet werden. Im Gegensatz zu normalen Cloud-Entwicklungsumgebungen können Entwickler lokale Befehlszeilen-Tools verwenden, um Code zu synchronisieren, der lokal auf einer RDE erstellt wurde.

Jedes Programm verfügt über einen RDE. Bei Sandbox-Konten werden sie nach einigen Stunden Nichtverwendung in den Ruhezustand versetzt.

Normalerweise wird ein RDE von einem einzelnen Entwickler gleichzeitig zum Testen und Debuggen einer bestimmten Funktion verwendet. Wenn die Entwicklungssitzung abgeschlossen ist, kann der RDE für die nächste Verwendung in einen Standardstatus zurückgesetzt werden.

Zusätzliche RDEs können für Produktions-(Nicht-Sandbox-)Programme lizenziert sein.

## Aktivieren von RDE in einem Programm {#enabling-rde-in-a-program}

Führen Sie diese Schritte aus, um Cloud Manager zum Erstellen eines RDE für Ihr Programm zu verwenden.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, dem Sie einen RDE hinzufügen möchten, um dessen Details anzuzeigen.

   * RDEs können zu beiden hinzugefügt werden [Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) und [Produktionsprogramme.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md)

1. Klicken Sie auf der Seite **Programmübersicht** auf der Karte **Umgebungen** auf **Umgebung hinzufügen**, um eine Umgebung hinzuzufügen.

   ![Karte „Umgebung“](/help/implementing/cloud-manager/assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

      ![Registerkarte Umgebungen](/help/implementing/cloud-manager/assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Im Dialogfeld **Umgebung hinzufügen** wird Folgendes angezeigt:

   * Auswählen **Schnelle Entwicklung** unter **Umgebungstyp auswählen** -Überschrift.
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Umgebungstyp angezeigt.
   * Bereitstellung einer **Name** für die Umwelt.
   * Angeben eines optionalen **Beschreibung** für die Umwelt.
   * Wählen Sie eine **Cloud-Region**.

   ![Dialogfeld „Umgebung hinzufügen“](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Der Bildschirm **Überblick** zeigt nun in der Karte **Umgebungen** Ihre neue Umgebung an.

Weitere Informationen zur Verwendung von Cloud Manager zum Erstellen von Umgebungen, zum Verwalten, wer Zugriff darauf hat, und zum Zuweisen benutzerdefinierter Domänen finden Sie unter [die Dokumentation zu Cloud Manager.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

## Installieren der RDE-Befehlszeilenwerkzeuge {#installing-the-rde-command-line-tools}

Nachdem Sie mit Cloud Manager ein RDE für Ihr Programm hinzugefügt haben, können Sie damit interagieren, indem Sie die Befehlszeilen-Tools einrichten, wie in den folgenden Schritten beschrieben:

>[!IMPORTANT]
>
>Vergewissern Sie sich, dass die neueste Version von [Knoten und installiertes NPM](https://nodejs.org/en/download/) für Adobe I/O CLI und zugehörige Plug-ins ordnungsgemäß funktionieren.


1. Installieren Sie die Adobe I/O-CLI-Tools gemäß dem Verfahren. [here](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).
1. Installieren Sie das Cloud Manager-Plugin für die Adobe I/O CLI-Tools und konfigurieren Sie es wie beschrieben [here](https://github.com/adobe/aio-cli-plugin-cloudmanager).
1. Installieren Sie die Adobe I/O CLI-Tools AEM RDE-Plug-in, indem Sie die folgenden Befehle ausführen:

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Konfigurieren Sie das Cloud Manager-Plugin für Ihre Organisations-ID:

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   und ersetzen Sie die alphanumerische Zeichenfolge durch Ihre eigene Organisations-ID, die mithilfe der Strategie nachgeschlagen werden kann. [here](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255).

1. Konfigurieren Sie anschließend Ihre Programm-ID:

   `aio config:set cloudmanager_programid 12345`

1. Konfigurieren Sie dann die Umgebungs-ID, an die der RDE angehängt werden soll:

   `aio config:set cloudmanager_environmentid 123456`

1. Sobald Sie das Plugin konfiguriert haben, melden Sie sich an, indem Sie

   `aio login`

   Die Antwort bei einer erfolgreichen Anmeldung sollte der Ausgabe unten entsprechen, Sie können jedoch die angezeigten Werte ignorieren.

   ```
   ...
   You are currently in:
   1. Org: <no org selected>
   2. Project: <no project selected>
   3. Workspace: <no workspace selected>
   ```

1. Überprüfen Sie, ob die Anmeldung erfolgreich abgeschlossen wurde, indem Sie

   `aio cloudmanager:list-programs`

   Dies sollte alle Programme unter Ihrer konfigurierten Organisation auflisten.

   Beachten Sie, dass Sie Mitglied von Cloud Manager sein müssen. **Entwickler - Cloud Service** Produktprofil. Weitere Informationen finden Sie auf [dieser Seite](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer).

   Sie können auch bestätigen, dass Sie über diese Entwicklerrolle verfügen, wenn Sie sich bei der Entwicklerkonsole anmelden können, indem Sie diesen Befehl ausführen:

   `aio cloudmanager:environment:open-developer-console`

   >[!TIP]
   >
   >Wenn die Variable `Warning: cloudmanager:list-programs is not a aio command.` -Fehler, müssen Sie die [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager) durch Ausführen des folgenden Befehls:
   >
   >
   ```
   >aio plugins:install @adobe/aio-cli-plugin-cloudmanager
   >```


## Verwenden von RDE bei der Entwicklung einer neuen Funktion {#using-rde-while-developing-a-new-feature}

Adobe empfiehlt den folgenden Workflow für die Entwicklung einer neuen Funktion:

* Wenn ein Zwischenschritt erreicht und erfolgreich lokal mit dem AEM as a Cloud Service SDK validiert wird, sollte der Code in eine Git-Funktionsverzweigung übertragen werden, die noch nicht Teil der Hauptzeile ist, obwohl die Zuweisung zu Git optional ist. Was einen &quot;Zwischenschritt&quot;ausmacht, hängt von den jeweiligen Teamgewohnheiten ab. Beispiele sind einige neue Codezeilen, ein halber Arbeitstag oder das Abschließen einer Unterfunktion.

* Setzen Sie den RDE zurück, wenn er von einer anderen Funktion verwendet wurde und Sie [Zurücksetzen auf den Standardstatus](#reset-rde). <!-- Alexandru: hiding for now, please don't delete This can be done via [Cloud Manager](#reset-the-rde-cloud-manager) or via the [command line](#reset-the-rde-command-line). -->Zurücksetzen dauert einige Minuten, und der gesamte vorhandene Inhalt und Code werden gelöscht. Sie können den RDE-Statusbefehl verwenden, um zu bestätigen, dass der RDE bereit ist.

* Synchronisieren Sie den lokalen Code über die RDE-Befehlszeilenschnittstelle mit dem RDE. Zu den Optionen gehören die Installation eines Inhaltspakets, eines bestimmten Bundles, einer OSGi-Konfigurationsdatei, einer Inhaltsdatei und einer ZIP-Datei einer Apache/Dispatcher-Konfiguration. Es ist auch möglich, auf ein Remote-Inhaltspaket zu verweisen. Siehe [RDE-Befehlszeilenwerkzeuge](#rde-cli-commands) für weitere Informationen. Mit dem Befehl status können Sie überprüfen, ob die Bereitstellung erfolgreich war. Verwenden Sie optional Package Manager , um Inhaltspakete zu installieren.

* Testen Sie den Code im RDE. Autoren- und Veröffentlichungs-URLs sind in Cloud Manager verfügbar.

* Wenn sich der Code nicht wie erwartet verhält, sollten Sie standardmäßige Debugging-Methoden verwenden, um das Problem zu verstehen und die entsprechenden Änderungen vorzunehmen. Verwenden Sie die lokale CLI, ohne die Code-Änderungen an Git zu übertragen (da sie nicht validiert wurden), um den Code mit dem RDE zu synchronisieren. Führen Sie die Iteration fort, bis das Problem behoben ist.

* Sobald sich der Code erwartungsgemäß verhält, übertragen Sie den Code in die Git-Funktionsverzweigung.

* Der mit RDE synchronisierte Code verwendet keine Cloud Manager-Pipeline. Daher sollten Sie jetzt eine Nicht-Produktions-Pipeline von Cloud Manager verwenden, um die Git-Funktionsverzweigung in der Cloud-Entwicklungsumgebung bereitzustellen. Dadurch wird überprüft, ob der Code die Cloud Manager-Qualitätstests erfolgreich durchläuft, und Sie können sicher sein, dass der Code später mithilfe der Cloud Manager-Produktions-Pipeline erfolgreich bereitgestellt wird.

* Wiederholen Sie die obigen Schritte für jeden Zwischenschritt, bis der gesamte Code für die Funktion bereit ist und sowohl in der RDE- als auch in der Cloud-Entwicklungsumgebung ordnungsgemäß ausgeführt wird.

* Stellen Sie den Code über die Cloud Manager-Produktions-Pipeline für die Produktion bereit.

## Verwenden von RDE zum Debuggen einer vorhandenen Funktion {#use-rde-to-debug-an-existing-feature}

Der Workflow ähnelt der Entwicklung einer neuen Funktion. Der Unterschied besteht darin, dass der mit RDE synchronisierte Code die Git-Beschriftung dessen widerspiegelt, was in die Umgebung gesendet wurde, in der das Problem gefunden wurde. Darüber hinaus kann es nützlich sein, Inhalte bereitzustellen, die mit der Upstream-Umgebung übereinstimmen. Dies kann durch den Export und Import von Inhaltspaketen erreicht werden.

## Mehrere Entwickler arbeiten mit demselben RDE zusammen {#multiple-developers-collaborating-on-the-same-rde}

Ein RDE unterstützt jeweils nur ein Projekt. Da Code von einer lokalen Entwicklungsumgebung mit der RDE-Umgebung synchronisiert wird, ist es für einen Entwickler am natürlichsten, ihn zu einer bestimmten Zeit selbst zu verwenden.

Bei sorgfältiger Koordinierung ist es jedoch möglich, dass mehrere Entwickler eine bestimmte Funktion validieren oder ein bestimmtes Problem beheben. Der Schlüssel besteht darin, dass jeder Entwickler seine lokalen Projekte synchron hält, sodass von einem bestimmten Entwickler vorgenommene Code-Änderungen von den anderen Entwicklern übernommen werden. Andernfalls könnte ein Entwickler versehentlich den Code des anderen überschreiben. Die empfohlene Strategie besteht darin, dass jeder Entwickler seine Änderungen in eine freigegebene Git-Verzweigung vor der Synchronisierung mit dem RDE übertragen muss, damit die anderen Entwickler die Änderungen abrufen, bevor sie ihre eigenen Änderungen vornehmen.

## Befehle für RDE-Befehlszeilenwerkzeuge {#rde-cli-commands}

### Hilfe/allgemeine Informationen {#help}

* Geben Sie für eine Liste von Befehlen Folgendes ein:

   `aio aem:rde`

* Geben Sie zur detaillierten Hilfe für einen Befehl Folgendes ein:

   `aio aem rde <command> --help`

### Bereitstellen in RDE {#deploying-to-rde}

In diesem Abschnitt wird die Verwendung der RDE-CLI zum Bereitstellen, Installieren oder Aktualisieren von Bundles, OSGi-Konfigurationen, Inhaltspaketen, individuellen Inhaltsdateien und Apache- oder Dispatcher-Konfigurationen beschrieben.

Das allgemeine Nutzungsmuster lautet `aio aem:rde:install <artifact>`.

Nachfolgend finden Sie einige Beispiele:

<u>Bereitstellen eines Inhaltspakets</u>

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

Die Antwort für eine erfolgreiche Implementierung sieht wie folgt aus:

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

Optional können Sie auf ein Remote-Repository verweisen:

`aio aem:rde:install -t content-package "https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip"`

Standardmäßig werden Artefakte sowohl für die Autoren- als auch für die Veröffentlichungsstufe bereitgestellt, aber das Flag &quot;-s&quot;kann verwendet werden, um eine bestimmte Ebene als Ziel festzulegen.

>[!IMPORTANT]
>
>Die Dispatcher-Konfiguration für das WKND-Projekt wird nicht über die obige Inhaltspaket-Installation bereitgestellt. Sie müssen sie separat bereitstellen, indem Sie die Schritte &quot;Bereitstellen einer Apache-/Dispatcher-Konfiguration&quot;befolgen.

<u>Bereitstellen einer OSGi-Konfiguration</u>

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

wobei die Antwort für eine erfolgreiche Bereitstellung der folgenden ähnelt:

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

<u>Bereitstellen eines Bundles</u>

Verwenden Sie zum Bereitstellen eines Bundles Folgendes:

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

wobei die Antwort für eine erfolgreiche Bereitstellung der folgenden ähnelt:

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

<u>Bereitstellen einer Inhaltsdatei</u>

Verwenden Sie zum Bereitstellen einer Inhaltsdatei Folgendes:

`aio aem:rde:install world.txt -p /apps/hello.txt`

wobei die Antwort für eine erfolgreiche Bereitstellung der folgenden ähnelt:

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

<u>Bereitstellen einer Apache-/Dispatcher-Konfiguration</u>

Die gesamte Ordnerstruktur muss in Form einer ZIP-Datei für diese Art von Konfiguration vorliegen. Sie können sie komprimieren, indem Sie diesen Befehl aus dem Stammverzeichnis eines Dispatcher-Konfigurationsordners ausführen:

`zip -y -r dispatcher.zip`

Stellen Sie dann die Konfiguration mithilfe dieses Befehls bereit:

`aio aem:rde:install -t dispatcher-config dispatcher-wknd-2.1.0.zip`

Bei erfolgreicher Bereitstellung wird eine Antwort generiert, die der folgenden ähnelt:

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

Code, der in RDE bereitgestellt wird, unterliegt keiner Cloud Manager-Pipeline und den zugehörigen Quality Gates. Der Code durchläuft jedoch einige Analysen, die die Fehler melden, wie im folgenden Codebeispiel dargestellt:

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

Das obige Codebeispiel veranschaulicht das Verhalten, wenn ein Bundle nicht aufgelöst wird. In diesem Fall ist es &quot;gestaffelt&quot;und wird nur installiert, wenn seine Anforderungen (in diesem Fall fehlende Importe) durch Installation von anderem Code erfüllt werden.

### Überprüfen des Status des RDE {#checking-rde-status}

Sie können die RDE-CLI verwenden, um zu überprüfen, ob die Umgebung bereit für die Bereitstellung ist und welche Implementierungen über das RDE-Plug-in vorgenommen wurden.

Wird ausgeführt:

`aio aem:rde:status`

wird zurückgegeben:

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

Wenn der Befehl einen Hinweis zur Bereitstellung von Instanzen zurückgibt, können Sie dennoch mit der nächsten Aktualisierung fortfahren, aber Ihre letzte Aktualisierung ist möglicherweise noch nicht in der Instanz sichtbar.

### Implementierungsverlauf anzeigen {#show-deployment-history}

Sie können den Verlauf der im RDE vorgenommenen Implementierungen überprüfen, indem Sie Folgendes ausführen:

`aio aem:rde:history`

, die eine Antwort in folgender Form zurückgibt:

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### Löschen aus RDE {#deleting-from-rde}

Sie können Konfigurationen und Bundles, die zuvor in RDE bereitgestellt wurden, über das CLI-Tool löschen. Verwenden Sie die `status` -Befehl für eine Liste der zu löschenden Elemente, einschließlich `bsn` für Pakete und `pid` für Konfigurationen, die im Befehl zum Löschen referenziert werden sollen.

Wenn beispielsweise `com.adobe.granite.demo.MyServlet.cfg.json` installiert wurde, wurde die `bsn` ist einfach `com.adobe.granite.demo.MyServlet`, ohne **cfg.json** Suffix.

Das Löschen von Inhaltspaketen oder Inhaltsdateien wird nicht unterstützt. Um sie zu entfernen, sollte der RDE zurückgesetzt werden, um ihn in den Standardzustand zu versetzen.

Weitere Informationen finden Sie im folgenden Beispiel:

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

## Zurücksetzen {#reset-rde}

Durch Zurücksetzen des RDE werden der gesamte benutzerdefinierte Code, Konfigurationen und Inhalt aus der Autoren- und Veröffentlichungsinstanz entfernt. Dies kann beispielsweise nützlich sein, wenn der RDE zum Testen einer bestimmten Funktion verwendet wurde und Sie sie auf einen Standardstatus zurücksetzen möchten, um eine andere Funktion zu testen.

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

Sie können Cloud Manager verwenden, um Ihren RDE zurückzusetzen, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie den RDE zurücksetzen möchten.

1. Klicken Sie auf der Seite **Überblick** auf die Registerkarte **Umgebungen** oben im Bildschirm.

   ![Registerkarte Umgebungen](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * Alternativ können Sie auf die Schaltfläche **Alle anzeigen** auf der Karte **Umgebungen** klicken, um direkt zur Registerkarte **Umgebungen** zu gelangen.

      ![Option „Alle anzeigen“](/help/implementing/cloud-manager/assets/environment-showall.png)

1. Die **Umgebungen** öffnet sich und listet alle Umgebungen für das Programm auf.

   ![Registerkarte „Umgebungen“](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. Klicken Sie auf die Suchschaltfläche des RDE, den Sie zurücksetzen möchten, und wählen Sie dann **Zurücksetzen**.

   ![Anzeigen von Umgebungsdetails](/help/implementing/cloud-manager/assets/rde-reset.png)

1. Bestätigen Sie, dass Sie den RDE zurücksetzen möchten, indem Sie auf **Zurücksetzen** im Dialogfeld.

   ![Zurücksetzen bestätigen](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager bestätigt über eine Bannerbenachrichtigung, dass der Zurücksetzungsprozess gestartet wurde.

   ![Bannerbenachrichtigung zurücksetzen](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

Sobald der RDE-Reset-Prozess gestartet wurde, dauert es in der Regel einige Minuten, bis er abgeschlossen ist und die Umgebung wieder in den Standardzustand versetzt wird. Der Status des Zurücksetzungsprozesses kann jederzeit im **Status** Spalte **Umgebungen** oder im **Umgebungen** Fenster.

![RDE-Zurücksetzungsstatus](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

Sie können den RDE auch direkt über die Suchschaltfläche **Umgebungen** auf der Karte **Übersicht** Seite.

![RDE aus Umgebungskarte zurücksetzen](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Weitere Informationen zur Verwendung von Cloud Manager zur Verwaltung Ihrer Umgebungen finden Sie unter [die Dokumentation zu Cloud Manager.](/help/implementing/cloud-manager/manage-environments.md)

## Ausführungsmodi {#runmodes}

RDE-spezifische OSGi-Konfigurationen können mithilfe von Suffixen auf dem Ordnernamen angewendet werden, wie in den folgenden Beispielen:

* `config.rde`
* `config.author.rde`
* `config.publish.rde`

Siehe [runmode-Dokumentation](/help/implementing/deploying/overview.md#runmodes) für allgemeine Informationen zu Ausführungsmodi.

>[!NOTE]
>
>Die RDE-OSGi-Konfiguration ist insofern eindeutig, als sie die Werte aller OSGi-Eigenschaften übernimmt, die vom Bundle deklariert wurden `dev` Ausführungsmodus.

RDEs unterscheiden sich von anderen Umgebungen darin, dass Inhalte in einem install.rde -Ordner (bzw. install.author.rde oder install.publish.rde) unter /apps installiert werden können. Auf diese Weise können Sie Inhalte mithilfe des Befehlszeilen-Tools an Git übertragen und an das RDE übermitteln.

## Mit Inhalt füllen {#populating-content}

Wenn ein RDE zurückgesetzt wird, wird der gesamte Inhalt entfernt und bei Bedarf muss daher explizit vorgegangen werden, um Inhalte hinzuzufügen. Als Best Practice empfiehlt es sich, einen Satz von Inhalten zusammenzustellen, die als Testinhalt für die Validierung oder das Debugging von Funktionen im RDE verwendet werden können. Es gibt mehrere mögliche Strategien zum Ausfüllen des RDE mit diesem Inhalt:

1. Synchronisieren Sie das Inhaltspaket explizit mit dem RDE mithilfe der Befehlszeilenwerkzeuge

1. Platzieren und übertragen Sie den Beispielinhalt in Git in einem Ordner install.rde unter /apps und synchronisieren Sie dann das übergeordnete Inhaltspaket mit dem RDE mithilfe der Befehlszeilenwerkzeuge.

1. Package Manager verwenden

Beachten Sie, dass Sie beim Synchronisieren von Inhaltspaketen auf 1 GB beschränkt sind.

## Protokollierung {#logging}

Protokollebenen können durch Ändern von OSGi-Konfigurationen festgelegt werden. Überprüfen Sie die [Dokumentation](/help/implementing/developing/introduction/logging.md) für weitere Informationen.

## Worin unterscheiden sich RDEs von Cloud-Entwicklungsumgebungen? {#how-are-rds-different-from-cloud-development-environments}

Der RDE ähnelt zwar auf vielerlei Weise einer Cloud-Entwicklungsumgebung, es gibt jedoch einige geringfügige Unterschiede in der Architektur, um eine schnelle Synchronisierung von Code zu ermöglichen. Der Mechanismus für den Code-Transfer zu RDE ist anders - für RDEs synchronisiert ein Code aus einer lokalen Entwicklungsumgebung, während für Cloud-Entwicklungsumgebungen ein Code über Cloud Manager bereitgestellt wird.

Aus diesen Gründen wird empfohlen, den Code nach der Validierung des Codes in einer RDE-Umgebung mithilfe der Nicht-Produktions-Pipeline in einer Cloud-Entwicklungsumgebung bereitzustellen. Testen Sie schließlich den Code, bevor Sie ihn mit der Produktions-Pipeline bereitstellen.

Beachten Sie außerdem die folgenden Überlegungen:

* RDEs unterstützen derzeit nicht das Anzeigen und Debugging von Frontend-Code, der mithilfe der Frontend-Pipeline von Cloud Manager bereitgestellt wird.
* RDEs unterstützen den Kanal der Vorabversion derzeit nicht.


## Wie viele RDEs benötige ich? {#how-many-rds-do-i-need}

Für jede lizenzierte Adobe ist ein RDE verfügbar. Außerdem bietet eine RDE zusätzliche RDEs, die für Produktionsprogramme (nicht Sandbox) lizenziert werden können.

Die Anzahl der benötigten RDEs hängt von der Zusammensetzung und den Prozessen eines Unternehmens ab. Am flexibelsten ist es, wenn ein Unternehmen für jeden seiner AEM Cloud Service-Entwickler eine dedizierte RDE kauft. In diesem Modell kann jeder Entwickler seinen Code auf dem RDE testen, ohne sich mit anderen Team-Mitgliedern darüber abzustimmen, ob eine RDE-Umgebung verfügbar ist.

Auf der anderen Seite kann ein Team mit einem einzelnen RDE interne Prozesse verwenden, um zu koordinieren, welcher Entwickler die Umgebung zu einem bestimmten Zeitpunkt verwenden kann. Dies kann der Fall sein, wenn ein Entwickler einen ZwischenFunktions-Meilenstein erreicht hat und bereit ist, diese in einer Cloud-Umgebung zu validieren, in der er schnell die benötigten Änderungen vornehmen kann.

Bei einem Zwischenmodell kauft ein Unternehmen eine Reihe von RDEs, sodass eine höhere Wahrscheinlichkeit besteht, dass ein nicht verwendetes RDE verfügbar ist. Eine Strategie könnte darin bestehen, eine RDE pro Scrum-Team oder einer wichtigen Funktion zuzuweisen. Interne Prozesse können zur Koordinierung der Nutzung der Umgebungen verwendet werden.

## Inwiefern unterscheidet sich eine AEM Forms Cloud Service Rapid Development Environment (RDE) von anderen Umgebungen? {#how-are-forms-rds-different-from-cloud-development-environments}

Forms-Entwickler können die AEM Forms Cloud Service-Rapid-Entwicklungsumgebung verwenden, um schnell Adaptive Forms, Workflows und Anpassungen zu entwickeln, z. B. die Anpassung von Kernkomponenten, Integrationen mit Drittanbietersystemen und mehr. Die AEM Forms Cloud Service Rapid Development Environment (RDE) unterstützt keine Kommunikations-APIs und Funktionen, für die Datensatzdokumente erforderlich sind, z. B. das Generieren eines Datensatzdokuments bei der Übermittlung eines adaptiven Formulars. Die folgenden aufgelisteten AEM Forms-Funktionen sind in einer Rapid Development Environment (RDE) nicht verfügbar:

* Konfigurieren eines Datensatzdokuments für ein adaptives Formular
* Generieren eines Datensatzdokuments bei Übermittlung eines adaptiven Formulars oder mit einem Workflow-Schritt
* Senden des Datensatzdokuments als Anlage mit der Aktion &quot;E-Mail senden&quot;oder mit dem Schritt &quot;E-Mail&quot;in einem Workflow
* Verwenden von Adobe Sign in einem adaptiven Formular oder in einem Workflow-Schritt
* Kommunikations-APIs

>[!NOTE]
>
> Es gibt keine Änderung zwischen der Benutzeroberfläche der Rapid Development Environment (RDE) und anderen Cloud Service-Umgebungen für Forms. Alle mit Datensatzdokument verbundenen Optionen, z. B. die Auswahl einer Datensatzdokumentvorlage für ein adaptives Formular, werden weiterhin in der Benutzeroberfläche angezeigt. Diese Umgebungen verfügen über keine Kommunikations-APIs und Datensatzdokument-Funktionen, um solche Optionen zu testen. Wenn Sie also eine Option auswählen, für die Kommunikations-APIs oder Datensatzdokumentfunktionen erforderlich sind, wird keine Aktion ausgeführt und eine Fehlermeldung angezeigt oder zurückgegeben.

