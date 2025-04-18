---
title: Schnelle Entwicklungsumgebungen
description: Erfahren Sie, wie Sie schnelle Entwicklungsumgebungen für schnelle Entwicklungsiterationen in einer Cloud-Umgebung verwenden.
exl-id: 1e9824f2-d28a-46de-b7b3-9fe2789d9c68
feature: Developing
role: Admin, Architect, Developer
source-git-commit: bd0c83098f19f8cf7cad41233f043c608be39a0c
workflow-type: tm+mt
source-wordcount: '5390'
ht-degree: 52%

---

# Schnelle Entwicklungsumgebungen {#rapid-development-environments}

Zur Bereitstellung von Änderungen erfordern aktuelle Cloud-Entwicklungsumgebungen die Verwendung eines Prozesses, der umfassende Code-Sicherheits- und -Qualitätsregeln anwendet, die als CI/CD-Pipeline bezeichnet werden. Für Situationen, in denen schnelle und iterative Änderungen erforderlich sind, hat Adobe schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs) eingeführt.

RDEs ermöglichen es Entwicklerinnen und Entwicklern, Änderungen schnell bereitzustellen und zu überprüfen, wodurch der Zeitaufwand für das Testen von Funktionen, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren, minimiert wird.

Sobald die Änderungen in einer RDE getestet wurden, können sie über die Cloud Manager-Pipeline in einer regulären Cloud-Entwicklungsumgebung bereitgestellt werden.

>[!NOTE]
> Wenden Sie sich an die RDE-Entwickler auf dem Adobe-Kanal [Discord](https://discord.com/channels/1131492224371277874/1245304281184079872). Sie können Fragen stellen oder Feedback zu RDE-Themen geben.

>[!VIDEO](https://video.tv.adobe.com/v/3415582/?quality=12&learn=on)


Sie können sich weitere Videos ansehen, in denen die [Einrichtung](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup), [Verwendung](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use) und der [Entwicklungslebenszyklus](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/development-life-cycle) mit RDE gezeigt werden.

## Einführung {#introduction}

RDEs können für Code-, Inhalts- und Apache- oder Dispatcher-Konfigurationen verwendet werden. Im Gegensatz zu regulären Cloud-Entwicklungsumgebungen können Entwickler lokale Befehlszeilen-Tools verwenden, um lokal in einer RDE erstellten Code zu synchronisieren.

Jedes Programm verfügt über eine RDE. Wenn Sandbox-Konten vorhanden sind, werden sie nach einigen Stunden Nichtverwendung in den Ruhezustand versetzt.

Nach der Erstellung werden RDEs auf die neueste verfügbare Adobe Experience Manager(AEM)-Version festgelegt. Beim Zurücksetzen einer RDE, das mit Cloud Manager durchgeführt werden kann, wird die RDE überprüft und auf die neueste AEM-Version festgelegt.

Normalerweise wird eine RDE von einem einzelnen Entwickler zu einer bestimmten Zeit zum Testen und Debuggen einer bestimmten Funktion verwendet. Wenn die Entwicklungssitzung abgeschlossen ist, kann die RDE für die nächste Verwendung in einen Standardstatus zurückgesetzt werden.

Für Produktionsprogramme (ohne Sandbox) können zusätzliche RDEs lizenziert werden.

## Aktivieren der RDE in einem Programm {#enabling-rde-in-a-program}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, dem Sie eine RDE hinzufügen möchten, um deren Details anzuzeigen.

   * RDEs können sowohl zu [Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) als auch zu [Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) hinzugefügt werden.

1. Klicken Sie auf der **&quot;**&quot; auf der Karte **Umgebungen** auf **Umgebung hinzufügen**.

   ![Karte „Umgebung“](/help/implementing/cloud-manager/assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

     ![Registerkarte Umgebungen](/help/implementing/cloud-manager/assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Gehen Sie im Dialogfeld **Umgebung hinzufügen** wie folgt vor:

   * Wählen Sie unter der Überschrift **Umgebungstyp auswählen** die Option **Schnelle Entwicklung** aus.
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Umgebungstyp angezeigt.
   * Geben Sie in **Name** einen Namen für die Umgebung an.
   * Geben Sie eine optionale **Beschreibung** für die Umgebung an.
   * Wählen Sie eine **Cloud-Region**.

   ![Dialogfeld „Umgebung hinzufügen“](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Der Bildschirm **Überblick** zeigt nun in der Karte **Umgebungen** Ihre neue Umgebung an.

Nach der Erstellung werden RDEs auf die neueste AEM Version eingestellt. Das Zurücksetzen einer RDE, das auch mit Cloud Manager durchgeführt werden kann, führt einen Zyklus der RDE durch und setzt sie auf die neueste AEM Version.

Weitere Informationen zur Verwendung von Cloud Manager zum Erstellen von Umgebungen, zum Verwalten von Zugriffsrechten und zum Zuweisen benutzerdefinierter Domains finden Sie unter [Programme und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) in der Dokumentation zu Cloud Manager.

## Installieren der RDE-Befehlszeilen-Tools {#installing-the-rde-command-line-tools}

Nachdem Sie mit Cloud Manager eine RDE für Ihr Programm hinzugefügt haben, können Sie damit interagieren, indem Sie die Befehlszeilen-Tools wie in den folgenden Schritten beschrieben einrichten:

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie Version 20 von [Node und NPM installiert haben](https://nodejs.org/en/download/), damit Adobe I/O CLI und die zugehörigen Plug-ins richtig funktionieren.


1. Installieren Sie die Adobe I/O-CLI-Tools gemäß dem [hier](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) beschriebenen Verfahren.
1. So installieren Sie das AEM-RDE-Plug-in für Adobe I/O-CLI-Tools:

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Melden Sie sich mit dem aio-Client an.

   ```
   aio login
   ```

   Die Anmeldeinformationen (Token) werden in der globalen aio-Konfiguration gespeichert und unterstützen daher nur eine einzige Anmeldung und Organisation. Wenn Sie mehrere RDEs verwenden möchten, die unterschiedliche Anmeldungen oder Organisationen benötigen, führen Sie das folgende Beispiel aus, indem Sie Kontexte einführen.

   <details><summary>Mit diesem Beispiel können Sie einen lokalen Kontext für eine Ihrer RDE-Anmeldungen einrichten</summary>
   Gehen Sie wie folgt vor, um die Anmeldeinformationen lokal in einer Datei ".aio“ im aktuellen Verzeichnis in einem bestimmten Kontext zu speichern. Ein Kontext ist auch eine clevere Möglichkeit, eine CI/CD-Umgebung oder ein Skript einzurichten.  Um diese Funktion zu verwenden, stellen Sie sicher, dass Sie mindestens aio-cli Version 10.3.1 verwenden. Aktualisieren Sie sie mit „npm install -g @adobe/aio-cli“.

   Erstellen Sie nun einen Kontext mit dem Namen m`ycontext`, den Sie mithilfe des Authentifizierungs-Plug-ins als Standardkontext festlegen, bevor Sie den Anmeldebefehl aufrufen.

   ```
   aio config set --json -l "ims.contexts.mycontext" "{ cli.bare-output: false }"
   aio auth ctx -s mycontext
   aio login --no-open
   ```

   >[!NOTE]
   > Der Anmeldebefehl mit der Option `--no-open` gibt eine URL im Terminal aus, anstatt den Standardbrowser zu öffnen. Sie können sie kopieren und mit einem **Inkognito**-Fenster Ihres Browsers öffnen. Dadurch wird sichergestellt, dass Ihre aktuelle Sitzung im Hauptfenster des Browsers nicht beeinträchtigt wird, sodass Sie sich mit dem spezifischen Konto und der Organisation anmelden können, die für Ihre Aufgabe erforderlich sind.

   Der erste Befehl erstellt eine neue Konfiguration des Anmeldekontexts mit dem Namen `mycontext` in Ihrer lokalen `.aio`-Konfigurationsdatei (die Datei wird bei Bedarf erstellt). Der zweite Befehl legt den Kontext `mycontext` den „aktuellen“ Kontext fest, d. h. den Standardwert.

   Mit dieser Konfiguration speichert der Anmeldebefehl automatisch die Anmelde-Token im Kontext `mycontext` und behält sie somit lokal bei.

   Mehrere Kontexte können durch Speichern lokaler Konfigurationen in mehreren Ordnern verwaltet werden. Alternativ können Sie auch mehrere Kontexte in einer einzelnen Konfigurationsdatei einrichten und zwischen ihnen wechseln, indem Sie den „aktuellen“ Kontext ändern.
   </details>

1. Konfigurieren Sie das RDE-Plug-in für die Verwendung Ihrer Organisation, Ihres Programms und Ihrer Umgebung. Der folgende Setup-Befehl stellt dem Benutzer interaktiv eine Liste der Programme in seiner Organisation bereit und zeigt die RDE-Umgebungen in diesem Programm zur Auswahl an.

   ```
   aio aem:rde:setup
   ```

   Sie können den Einrichtungsschritt überspringen, wenn Sie eine skriptbasierte Umgebung verwenden. Schließen Sie in diesem Fall die Werte für Organisation, Programm und Umgebung direkt in jeden Befehl ein. [Weitere Informationen finden Sie unter RDE-Befehle ](#rde-cli-commands).

### Interaktives Setup {#installing-the-rde-command-line-tools-interactive}

Der Setup-Befehl fragt, ob die angegebene Konfiguration lokal oder global gespeichert werden soll.

```
Setup the CLI configuration necessary to use the RDE commands.
? Do you want to store the information you enter in this setup procedure locally? (y/N)
```

Wählen Sie `no`, um

* Organisation, Programm und Umgebung global in Ihrer aio-Konfiguration zu speichern.
* nur mit einer einzigen RDE zu arbeiten.

Wählen Sie `yes` aus, um Folgendes zu tun:

* Speichern Sie Organisation, Programm und Umgebung lokal im aktuellen Verzeichnis in einer `.aio`. Dieser Ansatz ist praktisch, wenn Sie die Datei in die Versionskontrolle übertragen möchten, damit andere Benutzer, die das Git-Repository klonen, sie verwenden können.
* Sie können mit vielen RDEs arbeiten, sodass beim Wechsel zu einem anderen Verzeichnis stattdessen diese Konfiguration verwendet wird.
* Verwenden Sie die Konfiguration in einem programmgesteuerten Kontext wie einem Skript, das darauf verweisen kann.


Sobald die lokale oder globale Konfiguration ausgewählt ist, versucht der Befehl setup , die Organisations-ID aus Ihrer aktuellen Anmeldung zu lesen und dann die Programme des Unternehmens zu lesen. Falls die Organisation nicht gefunden werden kann, können Sie sie mithilfe von Anweisungen manuell eingeben.

```
Selected only organization: XYXYXYXYXYXYXYXXYY
retrieving programs of your organization ...
```

Sobald die Programme abgerufen wurden, kann der Benutzer aus der Liste auswählen und auch eingeben, um zu filtern. Wenn das Programm ausgewählt ist, wird eine Liste der RDE-Umgebungen aufgelistet, aus denen Sie auswählen können. Wenn nur ein Programm, nur eine RDE-Umgebung oder beides verfügbar ist, wird sie automatisch ausgewählt.

Führen Sie die folgenden Schritte aus, um den aktuellen Umgebungskontext anzuzeigen:

```aio aem rde setup --show```

Der Befehl antwortet mit einem Ergebnis, das dem folgenden ähnelt:

```Current configuration: cm-p1-e1: programName - environmentName (organization: ...@AdobeOrg)```

### Manuelles Setup in einer nicht interaktiven Umgebung {#manual-setup}

In Umgebungen, in denen kein Benutzer den Setup-Befehl interaktiv ausführen kann (z. B. CI/CD oder Skripte), ist eine manuelle Konfiguration erforderlich. Sie können die Parameter für Organisation, Programm und Umgebung wie folgt festlegen.


<details>
  <summary>Erweitern, um Details zur manuellen Konfiguration zu finden</summary>

1. Konfigurieren Sie Ihre Organisations-ID und ersetzen Sie die alphanumerische Zeichenfolge durch Ihre eigene Organisations-ID.

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   * Ihre eigene Organisations-ID kann mithilfe der unter [Anzeigen Ihrer Organisations-ID](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255) dokumentierten Methode nachgeschlagen werden.

1. Konfigurieren Sie anschließend Ihre Programm-ID:

   `aio config:set cloudmanager_programid 12345`

1. Konfigurieren Sie danach die Umgebungs-ID, mit der die RDE verknüpft werden soll:

   `aio config:set cloudmanager_environmentid 123456`

1. Nachdem Sie die Konfiguration des Plug-ins abgeschlossen haben, melden Sie sich mit folgendem Befehl an:

   `aio login`

   Für diese Schritte müssen Sie Mitglied des Cloud Manager-Produktprofils **Entwickler – Cloud Service** sein müssen. Weitere Informationen finden Sie unter [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen – Zuweisen des Entwicklerproduktprofils](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer).

Sehen Sie sich für weitere Informationen und Demonstrationen das Video-Tutorial [Einrichten eines RDE (06:24)](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup) an.
</details>

## Verwenden der RDE bei der Entwicklung einer neuen Funktion {#using-rde-while-developing-a-new-feature}

Adobe empfiehlt den folgenden Workflow für die Entwicklung einer neuen Funktion:

* Wenn ein Zwischenmeilenstein erreicht und erfolgreich lokal mit AEM as a Cloud Service SDK validiert wurde, committen Sie den Code an einen Git-Funktionszweig. Der Zweig sollte noch nicht Teil des Hauptstamms sein. Der Commit an Git ist jedoch optional. Was ein „Zwischenmeilenstein“ ist, hängt von den Gewohnheiten des jeweiligen Teams ab. Beispiele wären etwa einige neue Code-Zeilen, ein halber Arbeitstag oder das Fertigstellen einer Unterfunktion.

* Setzen Sie die RDE zurück, wenn sie von einer anderen Funktion verwendet wurde und Sie sie [auf den Standardstatus zurücksetzen](#reset-rde) möchten. <!-- Alexandru: hiding for now, do not delete This can be done by way of [Cloud Manager](#reset-the-rde-cloud-manager) or by way of the [command line](#reset-the-rde-command-line). -->Das Zurücksetzen dauert einige Minuten, und der gesamte vorhandene Inhalt samt Code wird gelöscht. Sie können den RDE-Statusbefehl verwenden, um zu bestätigen, dass die RDE bereit ist. Die RDE wird mit der neuesten Version von AEM wiederhergestellt.

  >[!IMPORTANT]
  >
  >Wenn Ihre Staging- und Produktionsumgebungen keine automatischen AEM-Versionsaktualisierungen erhalten und sich hinter der neuesten Version befinden, kann die RDE eine andere Version von AEM ausführen. Daher stimmt das Code-Verhalten in der RDE möglicherweise nicht mit der Funktionsweise in der Staging- und Produktionsumgebung überein. In diesem Fall ist es wichtig, den Code beim Staging gründlich zu testen, bevor er in der Produktion bereitgestellt wird.


* Synchronisieren Sie den lokalen Code über die RDE-Befehlszeilenschnittstelle mit der RDE. Sie können verschiedene Arten von Dateien installieren, darunter die folgenden:

   * Inhaltspakete
   * Spezifische Bundles
   * OSGi-Konfigurationsdateien
   * Inhaltsdateien
   * ZIP-Dateien mit Apache-/Dispatcher-Konfigurationen

  Es ist auch möglich, auf ein Remote-Inhaltspaket zu verweisen. Weitere Informationen finden Sie unter [RDE-Befehlszeilen-Tools](/help/implementing/developing/introduction/rapid-development-environments.md#rde-cli-commands). Mit dem Statusbefehl können Sie überprüfen, ob die Bereitstellung erfolgreich war. Optional können Sie Package Manager verwenden, um Inhaltspakete zu installieren.

* Testen Sie den Code in der RDE. Autoren- und Veröffentlichungs-URLs sind in Cloud Manager verfügbar.

* Wenn sich der Code nicht wie erwartet verhält, verwenden Sie standardmäßige Debugging-Methoden, um den Fehler zu identifizieren, und nehmen Sie die entsprechenden Änderungen vor. Verwenden Sie die lokale CLI, um den Code mit der RDE zu synchronisieren, ohne die Code-Änderungen an Git zu committen (da sie nicht validiert wurden). Wiederholen Sie diese Schritte, bis das Problem behoben ist.

* Sobald sich der Code erwartungsgemäß verhält, committen Sie den Code an den Git-Funktionszweig.

* Der mit der RDE synchronisierte Code verwendet keine Cloud Manager-Pipeline. Daher sollten Sie jetzt eine produktionsfremde Cloud Manager-Pipeline verwenden, um den Git-Funktionszweig in der Cloud-Entwicklungsumgebung bereitzustellen. Durch diesen Prozess wird überprüft, ob der Code die Cloud Manager-Qualitätstests besteht, und Sie können sicher sein, dass der Code später mithilfe der Cloud Manager-Produktions-Pipeline erfolgreich bereitgestellt wird.

* Wiederholen Sie die obigen Schritte für jeden Zwischenmeilenstein, bis der gesamte Code für die Funktion bereit ist und sowohl in der RDE als auch in der Cloud-Entwicklungsumgebung ordnungsgemäß ausgeführt wird.

* Implementieren Sie den Code über die Cloud Manager-Produktions-Pipeline.

## Verwenden der RDE zum Debuggen einer vorhandenen Funktion {#use-rde-to-debug-an-existing-feature}

Der Workflow entspricht in etwa der Entwicklung einer neuen Funktion. Der Unterschied besteht darin, dass der mit der RDE synchronisierte Code die Git-Kennzeichnung dessen widerspiegelt, was in die Umgebung gepusht wurde, in der das Problem aufgetreten ist. Dieser Workflow sorgt für Konsistenz bei der Untersuchung oder Reproduktion des Problems. Darüber hinaus kann es nützlich sein, Inhalte bereitzustellen, die der vorgelagerten Umgebung entsprechen. Dieser Ansatz kann durch den Export und Import von Inhaltspaketen erreicht werden.

## Zusammenarbeit mehrerer Entwickler an derselben RDE {#multiple-developers-collaborating-on-the-same-rde}

Eine RDE unterstützt immer nur jeweils ein Projekt. Da Code von einer lokalen Entwicklungsumgebung mit der RDE-Umgebung synchronisiert wird, wird sie normalerweise von einem Entwickler bzw. einer Entwicklerin allein verwendet.

Bei sorgfältiger Koordinierung ist es jedoch möglich, dass mehrere Entwickelnde gleichzeitig an der Prüfung einer Funktion oder der Behebung eines Fehlers arbeiten. Entscheidend ist dabei, dass alle Entwickler ihre lokalen Projekte synchron halten, sodass von einem bestimmten Entwickler bzw. einer Entwicklerin vorgenommene Code-Änderungen von den anderen Entwicklerinnen und Entwicklern übernommen werden. Andernfalls könnte ein Entwickler versehentlich den Code des anderen überschreiben. Es wird empfohlen, dass alle Entwickelnden ihre Änderungen vor der Synchronisierung mit der RDE an eine gemeinsame Git-Verzweigung committen, sodass die anderen Entwickelnden die Änderungen abrufen, bevor sie ihre eigenen Änderungen vornehmen.

## RDE-Befehlszeilen-Tools - Befehle {#rde-cli-commands}

### Hilfe/allgemeine Informationen {#help}

* Um eine Liste von Befehlen anzuzeigen, geben Sie Folgendes ein:

  `aio aem:rde`

* Um detaillierte Hilfe zu einem Befehl zu erhalten, geben Sie Folgendes ein:

  `aio aem rde <command> --help`

### Globale Flags {#global-flags}

* Verwenden Sie für eine weniger ausführliche Ausgabe das Flag „leise“:

  `aio aem rde <command> --quiet`

  Diese Markierung entfernt bestimmte Elemente wie beispielsweise Spinner und Fortschrittsbalken und begrenzt den Bedarf an Benutzereingaben.

* Verwenden Sie für JSON anstelle der Konsolenprotokollausgabe das JSON-Flag:

  `aio aem rde <command> --json`

  Dieses Flag gibt ein gültiges JSON zurück, während die Konsolenausgabe unterdrückt wird. Weitere Informationen finden Sie in den JSON-Beispielen weiter unten.

* Um zu vermeiden, dass die RDE-Verbindungsinformationen mit dem Setup-Befehl oder einer beliebigen aio-Konfigurationserstellung konfigurieren werden, verwenden Sie die drei Flags für Organisation, Programm und Umgebung:

  `aio aem rde <command> --organizationId=<value> --programId=<value> --environmentId=<value>`

  Erfordert die Durchführung eines ```aio login```.

### Bereitstellen in einer RDE {#deploying-to-rde}

In diesem Abschnitt wird erläutert, wie Sie mit der RDE-CLI verschiedene Ressourcen bereitstellen, installieren oder aktualisieren können. Zu diesen Ressourcen gehören die folgenden:

* Inhaltspakete
* OSGi-Konfigurationen
* Bundles
* Inhaltsdateien
* Apache- oder Dispatcher-Konfigurationen

Das allgemeine Nutzungsmuster lautet `aio aem:rde:install <artifact>`.

Nachfolgend finden Sie einige Beispiele:

#### Bereitstellen eines Inhaltspakets {#deploy-content-package}

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

Die Antwort auf eine erfolgreiche Bereitstellung sieht ähnlich der folgenden aus:

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

Optional können Sie auf ein Remote-Repository verweisen:

`aio aem:rde:install -t content-package "https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip"`

Standardmäßig werden die Artefakte sowohl auf der Autoren- als auch auf der Veröffentlichungsebene bereitgestellt, aber mit der `-s`-Markierung kann eine bestimmte Ebene ausgewählt werden.

Jedes AEM-Paket kann bereitgestellt werden, z. B. Pakete mit Code, Inhalt oder ein [Container-Paket](/help/implementing/developing/introduction/aem-project-content-package-structure.md#container-packages) (auch als „all“-Paket bezeichnet).

>[!IMPORTANT]
>
>Die obige Inhaltspaketinstallation stellt die Dispatcher-Konfiguration für das WKND-Projekt nicht bereit. Stellen Sie sie separat bereit, indem Sie die Schritte „Bereitstellen einer Apache-/Dispatcher-Konfiguration“ befolgen.

#### Bereitstellen einer OSGi-Konfiguration {#deploy-OSGI-config}

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

Die Antwort auf eine erfolgreiche Bereitstellung sieht ähnlich aus wie die folgende:

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

#### Bundle bereitstellen {#deploy-bundle}

Verwenden Sie zum Bereitstellen eines Bundles Folgendes:

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

Die Antwort auf eine erfolgreiche Bereitstellung sieht ähnlich aus wie die folgende:

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

#### Bereitstellen einer Inhaltsdatei {#deploy-content-file}

Verwenden Sie zum Bereitstellen einer Inhaltsdatei Folgendes:

`aio aem:rde:install world.txt -p /apps/hello.txt`

Die Antwort auf eine erfolgreiche Bereitstellung sieht ähnlich aus wie die folgende:

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

#### Bereitstellen einer Apache-/Dispatcher-Konfiguration {#deploy-apache-config}

Für diese Art von Konfiguration muss die gesamte Ordnerstruktur in Form einer ZIP-Datei vorliegen.

Aus dem Modul `dispatcher` eines AEM-Projekts können Sie die Dispatcher-Konfiguration komprimieren, indem Sie den folgenden Maven-Befehl ausführen:

`mvn clean package`

Oder Sie nutzen den folgenden ZIP-Befehl aus dem Verzeichnis `src` des Moduls `dispatcher`:

`zip -y -r dispatcher.zip .`

Stellen Sie dann die Konfiguration mithilfe dieses Befehls bereit:

`aio aem:rde:install target/aem-guides-wknd.dispatcher.cloud-X.X.X-SNAPSHOT.zip`

>[!TIP]
>
>Der obige Befehl setzt voraus, dass Sie die Dispatcher-Konfigurationen des Projekts [WKND](https://github.com/adobe/aem-guides-wknd) bereitstellen. Stellen Sie sicher, dass Sie `X.X.X` durch die entsprechende WKND-Projektversionsnummer bzw. Ihre projektspezifische Versionsnummer ersetzen, wenn Sie die Dispatcher-Konfiguration Ihres Projekts bereitstellen.

>[!NOTE]
>
>RDE unterstützt die Dispatcher-Konfiguration „Flexibler Modus“, nicht jedoch die Dispatcher-Konfiguration „Legacy-Modus“. Siehe die [Dispatcher-Dokumentation](/help/implementing/dispatcher/disp-overview.md#validation-debug) mit weiteren Informationen zu den beiden Modi. Sie können auch die Dokumentation über das [Migrieren zum flexiblen Modus](/help/implementing/dispatcher/validation-debug.md#migrating) konsultieren, falls noch nicht geschehen.

Bei erfolgreicher Implementierung wird eine Antwort generiert, die der folgenden ähnelt:

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

Der in RDE bereitgestellte Code unterliegt keiner Cloud Manager-Pipeline und den zugehörigen Qualitäts-Gates. Der Code durchläuft jedoch einige Analysen, die die Fehler melden, wie im folgenden Code-Beispiel dargestellt:

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

Das obige Code-Beispiel veranschaulicht das Verhalten, wenn ein Paket nicht aufgelöst wird. In diesem Fall wird es „bereitgehalten“ und erst dann installiert, wenn die jeweiligen Anforderungen (in diesem Fall fehlende Importe) durch Installation von weiterem Code erfüllt werden.

#### Pipeline-bezogene Konfiguration für Konfiguration bereitstellen (YAML-Konfigurationen) {#deploy-config-pipeline}

Die im Artikel [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md) beschriebenen umgebungsspezifischen Konfigurationen (eine oder mehrere YAML-Dateien) können wie folgt bereitgestellt werden:

`aio aem:rde:install -t env-config ./my-config-folder`
Dabei ist `my-config-folder` der übergeordnete Ordner, der Ihre YAML-Konfigurationen enthält.

Alternativ können Sie auch eine ZIP-Datei installieren, die die Baumstruktur des Konfigurationsordners enthält:

`aio aem:rde:install -t env-config config.zip`

Beachten Sie, dass das envTypes-Array der yaml-Datei den Wert `rde` enthält, wie im folgenden Beispiel gezeigt:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["rde"]
```

### Bereitstellen von Frontend-Code basierend auf Site-Designs und Site-Vorlagen {#deploying-themes-to-rde}

RDEs unterstützen Frontend-Code, der mit [Site-](/help/sites-cloud/administering/site-creation/site-themes.md) und [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md) erstellt wurde. Anstatt die Cloud Manager [Frontend-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md) wie andere Umgebungstypen zu verwenden, stellen RDEs Frontend-Pakete mithilfe einer Befehlszeilenanweisung bereit.

Erstellen Sie wie gewohnt Ihr Frontend-Paket mit npm:

`npm run build`

Es wird ein `dist/` Ordner generiert, sodass Ihr Frontend-Paketordner eine `package.json`-Datei und `dist` Ordner enthält:

```
ls ./path-to-frontend-pkg-folder/
...
dist
package.json
```

Jetzt können Sie das Frontend-Paket in der RDE bereitstellen, indem Sie wie folgt auf den Frontend-Paketordner verweisen:

```
aio aem:rde:install -t frontend ./path-to-frontend-pkg-folder/
...
#1: deploy completed for frontend frontend-pipeline.zip on author,publish - done by ... at 2024-01-18T15:33:22.898Z
Logs:
> Deployed artifact wknd-1.0.0-1705592008-26e7ec1a
> with workspace hash 692021864642a20d6d298044a927d66c0d9cf2adf42d4cca0c800a378ac3f8d3
```

Alternativ können Sie die Datei `package.json` und den Ordner `dist` komprimieren und diese ZIP-Datei bereitstellen:

`zip -r frontend-pkg.zip ./path-to-frontend-pkg-folder/dist ./path-to-frontend-pkg-folder/package.json`

```
aio aem:rde:install -t frontend frontend-pkg.zip
...
#1: deploy completed for frontend frontend-pipeline.zip on author,publish - done by ... at 2024-01-18T15:33:22.898Z
Logs:
> Deployed artifact wknd-1.0.0-1705592008-26e7ec1a
> with workspace hash 692021864642a20d6d298044a927d66c0d9cf2adf42d4cca0c800a378ac3f8d3
```

>[!NOTE]
>
>Die Benennung der Dateien im Frontend-Paket muss den folgenden Benennungskonventionen entsprechen:
>
> * `dist` für den NPM-Build-Ausgabepaket-Ordner
> * `package.json` für das npm dependencies-Paket

>[!TIP]
>
>Wenn Sie Ihre RDE vor April 2023 erstellt haben und bei der ersten Verwendung der Frontend-Funktion auf die `UNEXPECTED_API_ERROR` stoßen, kann dies auf ein veraltetes Setup zurückzuführen sein. Um dieses Problem zu beheben, löschen Sie die Umgebung und erstellen Sie eine neue.

## Bereitstellen in einer RDE von externen Git-Anbietern {#deploy-to-rde}

>[!NOTE]
>
>Diese Funktion ist über das Early-Adopter-Programm verfügbar. Wenn Sie diese neue Funktion testen und Ihr Feedback geben möchten, senden Sie von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse eine E-](mailto:cloudmanager_byog@adobe.com) an [CloudManager_BYOG@adobe.com. Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

Cloud Manager unterstützt die Bereitstellung von Code in einer RDE direkt von externen Git-Anbietern bei Verwendung der [Bring Your Own Git (BYOG)-Konfiguration](/help/implementing/cloud-manager/managing-code/external-repositories.md).

Für die Bereitstellung in RDEs aus einem externen Git-Repository ist Folgendes erforderlich:

* Die Verwendung eines externen Git-Repositorys, das in Cloud Manager integriert ist (BYOG-Setup).
* Für Ihr Projekt muss mindestens eine RDE-Umgebung bereitgestellt werden.
* Wenn Sie `github.com` verwenden, müssen Sie die aktualisierte GitHub-App-Installation überprüfen und akzeptieren, um die erforderlichen neuen Berechtigungen zu gewähren.

**Nutzungshinweise**

* Die Bereitstellung in der RDE wird derzeit nur für AEM-Inhalte und Dispatcher-Pakete unterstützt.
* Die Bereitstellung anderer Pakettypen (z. B. vollständige AEM-Anwendungspakete) wird noch nicht unterstützt.
* Derzeit wird das Zurücksetzen einer RDE-Umgebung mithilfe eines Kommentars nicht unterstützt. Kunden müssen die vorhandenen AIO-CLI-Befehle verwenden, wie [hier beschrieben](/help/implementing/developing/introduction/rapid-development-environments.md).

**Funktionsweise**

1. **Validierungsmeldung zur Code-Qualität.**

   Trigger Wenn eine Pull Request (PR) eine Code-Qualitäts-Pipeline ausführt, geben die Validierungsergebnisse an, ob die Bereitstellung in einer RDE-Umgebung fortgesetzt werden kann.

   So sieht es auf GitHub Enterprise aus:
   ![Validierungsmeldung zur Code-Qualität auf GitHub Enterprise](/help/implementing/developing/introduction/assets/rde-gitlab-code-quality-validation-message.png)

   So sieht es auf GitLab aus:
   ![Validierungsmeldung zur Code-Qualität auf GitLab](/help/implementing/developing/introduction/assets/rde-gitlab-code-quality-validation-message.png)

   Wie es auf Bitbucket aussieht:
   ![Validierungsmeldung der Code-Qualität auf Bitbucket](/help/implementing/developing/introduction/assets/rde-bitbucket-code-quality-validation-message.png)

1. **Trigger-Bereitstellung unter Verwendung eines Kommentars.**

   Um die Bereitstellung zu starten, fügen Sie dem PR einen Kommentar im folgenden Format hinzu: `deploy on rde-environment-<envName>`

   ![Trigger-Bereitstellung unter Verwendung eines Kommentars](/help/implementing/developing/introduction/assets/rde-trigger-deployment-using-comment.png)

   Der `<envName>` muss mit dem Namen einer vorhandenen RDE-Umgebung übereinstimmen. Wenn der Name nicht gefunden wird, wird ein Kommentar zurückgegeben, der angibt, dass die Umgebung ungültig ist.

   Wenn der Umgebungsstatus nicht bereit ist, erhalten Sie den folgenden Kommentar:

   ![Umgebung ist nicht bereit zur Bereitstellung](/help/implementing/developing/introduction/assets/rde-environment-not-ready.png)

1. **Umgebungsprüfung und Artefaktbereitstellung.**

   Wenn die RDE bereit ist, sendet Cloud Manager eine neue Prüfung an den PR.

   So sieht es auf GitHub Enterprise aus:

   ![Status der Umgebung auf GitHub](/help/implementing/developing/introduction/assets/rde-github-environment-status-is-ready.png)

   So sieht es auf GitLab aus:

   ![Status der Umgebung auf GitLab](/help/implementing/developing/introduction/assets/rde-gitlab-deployment-1.png)

   Wie es auf Bitbucket aussieht:

   ![Status der Umgebung auf Bitbucket](/help/implementing/developing/introduction/assets/rde-bitbucket-deployment-1.png)

1. **Erfolgreiche Bereitstellungsmeldung.**

   Wenn die Bereitstellung abgeschlossen ist, veröffentlicht Cloud Manager eine Erfolgsmeldung, in der die in der Zielumgebung bereitgestellten Artefakte zusammengefasst werden.

   So sieht es auf GitHub Enterprise aus:

   ![Bereitstellungsstatus der Umgebung auf GitHub](/help/implementing/developing/introduction/assets/rde-github-environment-deployed-artifacts.png)

   So sieht es auf GitLab aus:

   ![Bereitstellungsstatus der Umgebung auf GitLab](/help/implementing/developing/introduction/assets/rde-gitlab-deployment-2.png)

   Wie es auf Bitbucket aussieht:

   ![Bereitstellungsstatus der Umgebung auf Bitbucket](/help/implementing/developing/introduction/assets/rde-bitbucket-deployment-2.png)


### Überprüfen des Status der RDE {#checking-rde-status}

Sie können die RDE-CLI verwenden, um zu überprüfen, ob die Umgebung bereit für die Implementierung ist und welche Implementierungen über das RDE-Plug-in vorgenommen wurden.

Folgendes ausführen:

`aio aem:rde:status`

Gibt mit folgendem Inhalt zurück:

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

### Bereitstellungsverlauf anzeigen {#show-deployment-history}

Sie können den Verlauf der in der RDE vorgenommenen Bereitstellungen überprüfen, indem Sie Folgendes ausführen:

`aio aem:rde:history`

Daraufhin wird eine Antwort in folgendem Format zurückgegeben:

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### Löschen aus einer RDE {#deleting-from-rde}

Sie können die CLI-Tools verwenden, um Konfigurationen und Bundles zu löschen, die Sie zuvor in der RDE bereitgestellt haben. Verwenden Sie den Befehl `status` , um eine Liste der zu löschenden Elemente zu erhalten. Diese Liste enthält die `bsn` für Bundles und `pid` für Konfigurationen, auf die im Löschbefehl verwiesen werden muss.

Wenn beispielsweise `com.adobe.granite.demo.MyServlet.cfg.json` installiert wurde, dann lautet `bsn` einfach `com.adobe.granite.demo.MyServlet`, ohne das Suffix **cfg.json**.

Das Löschen von Inhaltspaketen oder Inhaltsdateien wird nicht unterstützt. Um sie zu entfernen, setzen Sie die RDE zurück, wodurch sie auf den Standardstatus zurückgesetzt wird.

Weitere Informationen finden Sie im folgenden Beispiel:

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

Weitere Informationen und Demonstrationen finden Sie im Video-Tutorial [Verwendung von RDE-Befehlen (10:01)](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use).

## Protokolle {#rde-logging}

Wie andere Umgebungstypen können auch die Protokollebenen durch Ändern von OSGi-Konfigurationen festgelegt werden. Wie oben beschrieben, verwendet das Bereitstellungsmodell für RDEs jedoch eine Befehlszeile und keine Cloud Manager-Implementierung. Weitere Informationen zum Anzeigen, Herunterladen und Interpretieren von Protokollen finden Sie in der [Protokollierungsdokumentation](/help/implementing/developing/introduction/logging.md).

Die RDE-CLI verfügt außerdem über einen eigenen Protokollbefehl, mit dem schnell konfiguriert werden kann, welche Klassen und Pakete auf welcher Protokollebene protokolliert werden. Diese Konfigurationen können als temporär betrachtet werden, da sie die OSGi-Eigenschaften in der Versionskontrolle nicht ändern. Diese Funktion konzentriert sich auf das Verfolgen von Protokollen in Echtzeit, anstatt nach Protokollen aus der weit zurückliegenden Vergangenheit zu suchen.

Das folgende Beispiel zeigt, wie die Autorenebene verfolgt wird, wobei ein Paket auf eine Debugging-Protokollebene und zwei Pakete (durch Leerzeichen getrennt) auf eine Info-Debugging-Ebene eingestellt sind. Eine Ausgabe, die ein **auth**-Paket enthält, ist hervorgehoben.

`aio aem:rde:logs --target=author --debug=org.apache.sling --info=org.apache.sling.commons.threads.impl org.apache.sling.jcr.resource.internal.helper.jcr -H .auth.`

>[!TIP]
>
>Falls der Fehler `RDECLI:UNEXPECTED_API_ERROR` angezeigt wird, wenn Sie die Protokollbefehle für den Author-Service ausprobieren, setzen Sie Ihre Umgebung zurück und versuchen Sie es erneut. Dieser Fehler wird ausgegeben, wenn Ihr letzter Zurücksetzungsvorgang vor Ende Mai 2024 erfolgte.
>
>```
>aio aem:rde:reset
>```

Weitere Informationen zum vollständigen Satz von Befehlszeilenoptionen finden Sie unter `aio aem:rde:logs --help`.

Zu den Funktionen gehören:

* Deklarieren von Protokollebenen auf Paket- oder Klassenebene
* Anpassen des Protokollausgabeformats
* Nachverfolgen von bis zu vier aktuellen Protokollkonfigurationen, jeweils in einem eigenen Terminal
* Hervorheben spezifischer Protokolle

Beachten Sie, dass Protokolle im Speicher der RDE gespeichert werden. Diese Protokolle werden recycelt und daher verworfen, wenn sie nicht nachverfolgt werden oder wenn das Netzwerk zu langsam ist.


## Zurücksetzen der RDE {#reset-rde}

Durch Zurücksetzen der RDE werden der gesamte benutzerdefinierte Code, Konfigurationen und Inhalte aus der Autoren- und Veröffentlichungsinstanz entfernt. Das Zurücksetzen der RDE ist hilfreich, wenn Sie mit dem Testen einer Funktion fertig sind und die Umgebung in einen Standardzustand zurückversetzen möchten, bevor Sie eine andere testen.

Durch Zurücksetzen wird die RDE auf die neueste AEM-Version festgelegt.

Sie können die RDE entweder mit [Cloud Manager](#reset-the-rde-cloud-manager) oder der [Befehlszeile“ ](#reset-the-rde-command-line). Dieser Vorgang dauert einige Minuten. Der gesamte vorhandene Inhalt samt Code wird dabei gelöscht.

>[!NOTE]
>
>Vergewissern Sie sich, dass Ihnen die Cloud Manager-Entwicklerrolle zugewiesen wurde, bevor Sie die Funktion zum Zurücksetzen verwenden. Andernfalls schlägt die Aktion zum Zurücksetzen mit einem Fehler fehl.

### Zurücksetzen der RDE über die Befehlszeile {#reset-the-rde-command-line}

Sie können die RDE zurücksetzen und sie auf einen Standardstatus zurücksetzen, indem Sie Folgendes ausführen:

`aio aem:rde:reset`

Dieser Vorgang dauert in der Regel einige Minuten und meldet ```Environment reset.``` bei Erfolg oder ```Failed to reset the environment.``` von Fehlern. Eine strukturierte Ausgabe finden Sie weiter unten im Kapitel über ```--json```-Ausgaben.

Verwenden Sie den [Statusbefehl](#checking-rde-status), um zu überprüfen, ob die Umgebung wieder bereit ist.

### Zurücksetzen der RDE in Cloud Manager {#reset-the-rde-cloud-manager}

Sie können Cloud Manager verwenden, um Ihre RDE zurückzusetzen, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie die RDE zurücksetzen möchten.

1. Klicken Sie auf der Seite **Überblick** auf die Registerkarte **Umgebungen** oben auf dem Bildschirm.

   ![Registerkarte „Umgebungen“](/help/implementing/cloud-manager/assets/environments-tab2.png)

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

Nachdem das Zurücksetzen der RDE gestartet wurde, dauert es in der Regel einige Minuten, bis der Vorgang abgeschlossen ist und die Umgebung wieder ihren Standardstatus annimmt. Sie können den Zurücksetzungsstatus jederzeit in der Spalte **Status** der Karte **Umgebungen** oder im Fenster einsehen.

![RDE-Zurücksetzungsstatus](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

Sie können die RDE auch direkt auf der Seite **Übersicht** auf der Karte **Umgebungen** mit der Schaltfläche mit den Auslassungszeichen zurücksetzen.

![RDE über die Karte „Umgebungen“ zurücksetzen](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Weitere Informationen zur Verwendung von Cloud Manager zur Verwaltung Ihrer Umgebungen finden Sie in der [Dokumentation zu Cloud Manager](/help/implementing/cloud-manager/manage-environments.md).

## Befehle, die die JSON-Ausgabe unterstützen {#json-commands}

Die meisten Befehle unterstützen das globale Flag ```--json```, das die Konsolenausgabe unterdrückt und gültige JSON_Dateien zurückgibt, die in Skripten verarbeitet werden sollen. Im Folgenden finden Sie einige unterstützte Befehle mit Beispielen für die JSON-Ausgabe.

### Status {#status}

<details>
  <summary>Erweitern, um Statusbeispiele anzuzeigen</summary>

#### Eine saubere RDE {#clean-rde}

```$ aio aem rde status --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Modification in progress | Deployment in progress | Upload in progress | Ready (instances are currently deploying) | Ready",
  "author": {
    "osgiBundles": [],
    "osgiConfigs": []
  },
  "publish": {
    "osgiBundles": [],
    "osgiConfigs": []
  }
}
```

#### Eine RDE mit einigen installierten Bundles {#rde-installed-bundles}

```$ aio aem rde status --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Ready",
  "author": {
    "osgiBundles": [
      {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "updateId": "80",
        "service": "author",
        "type": "osgi-bundle",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        }
      }
    ],
    "osgiConfigs": [
      {
        "id": "publish_osgi-config_com.adobe.granite.demo.MyServlet",
        "updateId": "80",
        "service": "publish",
        "type": "osgi-config",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "configPid": "com.adobe.granite.demo.MyServlet"
        }
      }
    ]
  },
  "publish": {
    "osgiBundles": [
      {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "updateId": "80",
        "service": "author",
        "type": "osgi-bundle",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        }
      }
    ],
    "osgiConfigs": [
      {
        "id": "publish_osgi-config_com.adobe.granite.demo.MyServlet",
        "updateId": "80",
        "service": "publish",
        "type": "osgi-config",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "configPid": "com.adobe.granite.demo.MyServlet"
        }
      }
    ]
  }
}
```

</details>

### Installieren {#install}

<details>
  <summary>Erweitern, um Installationsbeispiele anzuzeigen</summary>

```$ aio aem rde install ~/Downloads/hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "items": [
    {
      "updateId": "4",
      "info": "deploy",
      "action": "deploy",
      "metadata": {
        "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip"
      },
      "services": [
        "author",
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:30:44.578Z",
        "processed": "2024-05-21T12:31:07.886468Z"
      },
      "user": "userId",
      "type": "content-package",
      "hash": "2ad73507",
      "logs": [
        "No logs available for this update."
      ]
    }
  ]
}
```

</details>

### Löschen {#delete}

<details>
  <summary>Erweitern, um Beispiele zum Löschen anzuzeigen</summary>

```$ aio aem rde delete com.adobe.granite.hotdev.demo-1.0.0.SNAPSHOT --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "items": [
    {
      "updateId": "84",
      "info": "delete author_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "author"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T11:49:16.889Z",
        "processed": "2024-05-21T11:49:18.188420Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "author",
        "type": "osgi-bundle",
        "updateId": "83"
      },
      "hash": "636f6d2e",
      "logs": [
        "No logs available for this update."
      ]
    },
    {
      "updateId": "85",
      "info": "delete publish_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T11:49:23.857Z",
        "processed": "2024-05-21T11:49:25.237930Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "publish_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "publish",
        "type": "osgi-bundle",
        "updateId": "83"
      },
      "hash": "636f6d2e",
      "logs": [
        "No logs available for this update."
      ]
    }
  ]
}
```

</details>

### Verlauf {#history}

<details>
  <summary>Erweitern, um Verlaufsbeispiele anzuzeigen</summary>

```$ aio aem rde history --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Ready",
  "items": [
    {
      "updateId": "112",
      "info": "delete publish_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:53:07.934Z",
        "processed": "2024-05-21T12:53:09.118766Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "publish_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "publish",
        "type": "osgi-bundle",
        "updateId": "110"
      },
      "hash": "636f6d2e"
    },
    {
      "updateId": "111",
      "info": "delete author_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "author"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:53:00.824Z",
        "processed": "2024-05-21T12:53:02.101560Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "author",
        "type": "osgi-bundle",
        "updateId": "110"
      },
      "hash": "636f6d2e"
    },
    {
      "updateId": "110",
      "info": "deploy",
      "action": "deploy",
      "metadata": {
        "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip"
      },
      "services": [
        "author",
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:52:12.123Z",
        "processed": "2024-05-21T12:52:31.026147Z"
      },
      "user": "userId",
      "type": "content-package",
      "hash": "2ad73507"
    }
  ]
}
```

</details>

### Zurücksetzen {#reset}

<details>
  <summary>Erweitern, um Beispiele zum Zurücksetzen anzuzeigen</summary>

#### Feuern und vergessen, kein Warten {#fire-no-wait}

```$ aio aem rde reset --no-wait --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "resetting"
}
```

#### Auf Abschluss warten, erfolgreich zurückgesetzt {#wait-success}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset"
}
```

#### Warten auf Abschluss, Zurücksetzen fehlgeschlagen {#wait-failed}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset_failed"
}
```

</details>

### Neu starten {#restart}

<details>
  <summary>Erweitern um Neustartbeispiele zu sehen</summary>

```$ aio aem rde restart --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "restarted"
}
```

</details>

## Ausführungsmodi {#runmodes}

RDE-spezifische OSGi-Konfigurationen können mithilfe von Suffixen auf den Ordnernamen angewendet werden, wie in den folgenden Beispielen:

* `config.rde`
* `config.author.rde`
* `config.publish.rde`

Allgemeine Informationen zu den Ausführungsmodi finden Sie in der [Dokumentation zu Ausführungsmodi](/help/implementing/deploying/overview.md#runmodes).

>[!NOTE]
>
>Die RDE-OSGi-Konfiguration ist insofern eindeutig, als sie die Werte aller OSGi-Eigenschaften erbt, die durch den `dev`-Ausführungsmodus des Bundles deklariert wurden.

RDEs unterscheiden sich von anderen Umgebungen darin, dass Inhalte in einem `install.rde` Ordner (oder `install.author.rde` oder `install.publish.rde`) unter `/apps` installiert werden können. Mit dieser Funktion können Sie Inhalte mithilfe der Befehlszeilen-Tools an Git übertragen und an die RDE übermitteln.

## Mit Inhalt füllen {#populating-content}

Wenn eine RDE zurückgesetzt wird, werden alle Inhalte entfernt, sodass, falls gewünscht, explizit Maßnahmen ergriffen werden müssen, um Inhalte hinzuzufügen. Als Best Practice empfiehlt es sich, einen Satz von Inhalten zusammenzustellen, die als Testinhalt für die Validierung oder das Debugging von Funktionen in der RDE verwendet werden können. Es gibt mehrere mögliche Strategien zum Ausfüllen der RDE mit diesem Inhalt:

1. Synchronisieren Sie das Inhaltspaket explizit mit der RDE mithilfe der Befehlszeilen-Tools

1. Platzieren und übertragen Sie den Beispielinhalt in Git in einem `install.rde` Ordner unter `/apps` und synchronisieren Sie dann das übergeordnete Inhaltspaket mit der RDE mithilfe der Befehlszeilen-Tools.

1. Verwenden Sie das [Tool zum Kopieren von Inhalten](/help/implementing/developing/tools/content-copy.md), um ein definiertes Inhaltsset aus einer Produktions-, Staging- oder Entwicklungsumgebung oder aus einer anderen RDE zu kopieren.

1. Verwenden Sie den Package Manager

Sie sind beim Synchronisieren von Inhaltspaketen auf 1 GB beschränkt.


## Wie unterscheiden sich RDEs von Cloud-Entwicklungsumgebungen? {#how-are-rds-different-from-cloud-development-environments}

Obwohl die RDE in vielerlei Hinsicht einer Cloud-Entwicklungsumgebung ähnelt, gibt es einige geringfügige Unterschiede in der Architektur, die eine schnelle Synchronisierung von Code ermöglichen. Bei RDEs wird Code über eine lokale Entwicklungsumgebung synchronisiert. Bei Cloud-Entwicklungsumgebungen wird Code hingegen über Cloud Manager bereitgestellt.

Aus diesen Gründen wird empfohlen, den Code nach der Validierung in einer RDE mithilfe der produktionsfremden Pipeline in einer Cloud-Entwicklungsumgebung bereitzustellen. Testen Sie schließlich den Code, bevor Sie ihn mit der Produktions-Pipeline bereitstellen.

Beachten Sie außerdem die folgenden Überlegungen:

* RDEs enthalten keine Vorschauebene
* RDEs unterstützen derzeit nicht den Vorabversionskanal.


## Wie viele RDEs benötige ich? {#how-many-rds-do-i-need}

Für jede lizenzierte Lösung steht eine RDE zur Verfügung. Darüber hinaus bietet Adobe zusätzliche RDEs an, die für Produktionsprogramme (ohne Sandbox) lizenziert werden können.

Die Anzahl der benötigten RDEs hängt von der Zusammensetzung und den Prozessen eines Unternehmens ab. Das flexibelste Model ist das, bei dem ein Unternehmen für jedes Mitglied seines Entwicklungsteams von AEM Cloud Service eine dedizierte RDE erwirbt. In diesem Modell kann jeder Entwickler seinen Code in der RDE testen, ohne sich mit anderen Team-Mitgliedern darüber abzustimmen, ob eine RDE-Umgebung verfügbar ist.

Auf der anderen Seite kann sich ein Team mit nur einer RDE auf die interne Koordinierung verlassen, um zu entscheiden, welcher Entwickler die Umgebung zu einem bestimmten Zeitpunkt verwendet. Dieser Ansatz funktioniert gut, wenn ein Entwickler einen Funktions-Meilenstein erreicht und seine Arbeit in einer Cloud-Umgebung mit der Flexibilität validieren muss, schnelle Änderungen vorzunehmen.

Bei einem Zwischenmodell kauft ein Unternehmen mehrere RDEs, sodass eine höhere Wahrscheinlichkeit besteht, dass eine nicht verwendete RDE verfügbar ist. Eine Strategie könnte darin bestehen, pro Scrum-Team oder Hauptfunktion eine RDE zuzuweisen. Interne Prozesse können zur Koordinierung der Nutzung der Umgebungen verwendet werden.

## Wie unterscheidet sich eine AEM Forms Cloud Service-RDE von anderen Umgebungen? {#how-are-forms-rds-different-from-cloud-development-environments}

Forms-Entwicklerinnen und -Entwickler können die schnelle Entwicklungsumgebung von AEM Forms Cloud Service verwenden, um schnell adaptive Forms, Workflows und Anpassungen zu entwickeln, z. B. die Anpassung von Kernkomponenten, Integrationen mit Drittanbietersystemen und mehr. Die schnelle Entwicklungsumgebung (RDE) in AEM Forms Cloud Service unterstützt keine Kommunikations-APIs. Sie unterstützt auch keine Funktionen, für die ein Datensatzdokument erforderlich ist, z. B. das Generieren eines Datensatzdokuments bei der Übermittlung eines adaptiven Formulars. Die folgenden aufgelisteten Funktionen von AEM Forms sind in einer schnellen Enticklungsumgebung (RDE) nicht verfügbar:

* Konfigurieren eines Datensatzdokuments für ein adaptives Formular
* Generieren eines Datensatzdokuments bei Übermittlung eines adaptiven Formulars oder mit einem Workflow-Schritt
* Senden des Datensatzdokuments als Anhang mit der Aktion „E-Mail senden“ oder mit dem Schritt „E-Mail“ in einem Workflow
* Verwenden von Adobe Sign in einem adaptiven Formular oder in einem Workflow-Schritt
* Kommunikations-APIs

>[!NOTE]
>
> Es gibt keinen Unterschied zwischen der Benutzeroberfläche der schnellen Entwicklungsumgebung (RDE) und anderen Cloud Service-Umgebungen für Forms. Alle mit dem Datensatzdokument verbundenen Optionen, z. B. die Auswahl einer Datensatzdokumentvorlage für ein adaptives Formular, werden weiterhin in der Benutzeroberfläche angezeigt. Diese Umgebungen verfügen über keine Kommunikations-APIs und Datensatzdokument-Funktionen, um solche Optionen zu testen. Wenn Sie also eine Option auswählen, für die Kommunikations-APIs oder Datensatzdokumentfunktionen erforderlich sind, führt das System die Aktion nicht aus. Stattdessen wird eine Fehlermeldung angezeigt.

## RDE-Tutorial

Informationen zu RDE in AEM as a Cloud Service finden Sie im Video-Tutorial, das die [Einrichtung, die Verwendung und den Entwicklungslebenszyklus veranschaulicht (01:25)](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/developing/rde/overview).

## Fehlerbehebung {#troubleshooting}

### Fehlerbehebung bei RDE (#rde-troublehooting)

#### Abrufen der neuesten AEM-Version für eine vorhandene RDE {#get-latest-aem-version}

Nach der Erstellung werden RDEs auf die neueste verfügbare Adobe Experience Manager(AEM)-Version festgelegt. Ein [RDE-Zurücksetzen](#reset-rde) das mit Cloud Manager oder dem `aio aem:rde:reset`-Befehl durchgeführt werden kann, durchläuft die RDE und setzt sie auf die neueste AEM-Version.

### Fehlerbehebung beim aio-RDE-Plug-in {#aio-rde-plugin-troubleshooting}

#### Fehler wegen unzureichender Berechtigungen {#insufficient-permissions}

Um das RDE-Plug-in verwenden zu können, müssen Sie Mitglied des Cloud Manager-Produktprofils **Entwickler – Cloud Service** sein. Weitere Informationen finden Sie unter [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen – Zuweisen des Entwicklerproduktprofils](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer).

Alternativ können Sie durch Ausführen des folgenden Befehls bestätigen, dass Sie über diese Entwicklerrolle verfügen, wenn Sie sich bei der Entwicklerkonsole anmelden:

`aio cloudmanager:environment:open-developer-console`

>[!TIP]
>
>Wenn Sie den `Warning: cloudmanager:* is not a aio command.` Fehler sehen, müssen Sie den [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager) installieren, indem Sie den folgenden Befehl ausführen:
>
>```
>aio plugins:install @adobe/aio-cli-plugin-cloudmanager
>```

Vergewissern Sie sich, dass die Anmeldung erfolgreich abgeschlossen wurde, indem Sie Folgendes ausführen:

`aio cloudmanager:list-programs`

Dieser Prozess listet alle Programme unter Ihrer konfigurierten Organisation auf und bestätigt, dass Ihnen die richtige Rolle zugewiesen wurde.

#### Veraltete `aio-cli-plugin-cloudmanager` verwenden {#aio-rde-plugin-troubleshooting-deprecatedcontext}

Aufgrund des Verlaufs der `aio-cli-plugin-aem-rde` wurde der Kontextname `aio-cli-plugin-cloudmanager` einige Zeit verwendet. Das RDE-Plug-in verwendet jetzt die IMS-Methode zur Verwaltung von Kontextinformationen, sodass Sie Kontext entweder global oder lokal speichern können. Sie können auch einen Standardkontext konfigurieren, der automatisch auf alle AIO-Aufrufe angewendet wird. Der konfigurierte Standardkontext wird lokal gespeichert und ermöglicht es den Entwickelnden, einzelne Kontexte und deren Informationen in einem Ordner zu verfolgen und zu verwenden. Weitere Informationen finden Sie [Beispiel zum Einrichten eines lokalen Kontexts](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) oben.

Entwickler, die beide Plug-ins, das `aio-cli-plugin-cloudmanager` und das `aio-cli-plugin-aem-rde`, verwenden und alle Informationen im selben Kontext behalten möchten, haben jetzt zwei Möglichkeiten:

##### Weiter `aio-cli-plugin-cloudmanager` verwenden

Der Kontext kann weiterhin verwendet werden. Im RDE-Plug-in wird eine Warnung vor veralteten Elementen angezeigt. Diese Warnung kann im ```--quiet```-Modus weggelassen werden. Neuere Versionen des RDE-Plug-ins bieten nicht mehr die Möglichkeit, den Kontext `aio-cli-plugin-cloudmanager` lesen. Um ihn weiterhin zu verwenden, konfigurieren Sie einfach den Standardkontext für `aio-cli-plugin-cloudmanager`. Siehe [Beispiel zum Einrichten eines lokalen Kontexts](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) oben.

##### Verwenden Sie einen anderen Kontextnamen auch für das Cloud Manager-Plug-in.

Die Cloud Manager-Plug-ins bieten einen -Parameter zum Definieren eines zu verwendenden Kontexts. Die standardmäßige IMS-Kontextkonfiguration wird noch nicht unterstützt. Konfigurieren Sie dazu das RDE-Plug-in mit [Beispiel zum Einrichten eines lokalen Kontexts](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) und weisen Sie das Cloud Manager-Plug-in an, bei jedem Aufruf `myContext` wie ```--imsContextName=myContext``` zu verwenden.
