---
title: Adobe Content Package Maven Plugin
description: Verwenden Sie das Content Package Maven-Zusatzmodul, um AEM Anwendungen bereitzustellen
translation-type: tm+mt
source-git-commit: 2cdbbe9b8f6608cbdd299889be515d421e3d9ad3
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 45%

---


# Adobe Content Package Maven Plugin {#adobe-content-package-maven-plugin}

Verwenden Sie das Maven-Plugin für das Adobe Content Package, um Paketbereitstellungs- und -verwaltungslösungen in Ihre Maven-Aufgaben zu integrieren.

Die Bereitstellung der erstellten Pakete für AEM wird vom Adobe Content Package Maven-Plug-in durchgeführt und ermöglicht die Automatisierung von Aufgaben, die normalerweise mit AEM Package Manager ausgeführt werden:

* Erstellen Sie neue Pakete anhand der Dateien im Dateisystem.
* Installieren und deinstallieren Sie Pakete auf AEM.
* Erstellen Sie Pakete, die bereits auf AEM definiert sind.
* Besorgen Sie sich eine Liste von Paketen, die auf AEM installiert sind.
* Entfernen Sie ein Paket aus AEM.

In diesem Dokument wird erläutert, wie Sie diese Aufgaben mit dem Maven verwalten können. Es ist jedoch auch wichtig zu verstehen, wie AEM Projekte und ihre Pakete strukturiert sind.](#aem-project-structure)[

>[!NOTE]
>
>Die Paketerstellung ist jetzt im Besitz des Plugins [Apache Jackrabbit FileVault Package Maven](https://jackrabbit.apache.org/filevault-package-maven-plugin/). Die Bereitstellung der zu AEM erstellten Pakete wird vom Adobe Content Package Maven Plug-in wie hier beschrieben ausgeführt.

## Pakete und die AEM Projektstruktur {#aem-project-structure}

AEM 6.5 befolgt die neuesten Best Practices für Paketverwaltung und Projektstruktur, wie sie von der neuesten AEM Project Archetype sowohl für Vor-Ort- als auch AMS-Implementierungen implementiert wurden.

>[!TIP]
>
>Weitere Informationen finden Sie im Artikel [AEM Projektstruktur](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) in der AEM als Cloud Service-Dokumentation sowie in der [AEM Projektarchiv](https://docs.adobe.com/content/help/de/experience-manager-core-components/using/developing/archetype/overview.html)-Dokumentation. Beide werden für AEM 6.5 vollständig unterstützt.

## Abrufen des Inhaltspaket-Maven-Plug-ins {#obtaining-the-content-package-maven-plugin}

Das Plugin ist im Maven Central Repository verfügbar.[](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

## Inhaltspaket - Maven Plugin-Ziele und Parameter

Fügen Sie zum Verwenden des Inhaltspaket-Maven-Plug-ins das folgende Plug-in-Element im Buid-Element Ihrer POM-Datei hinzu:

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>0.0.24</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Verwenden Sie das im Abschnitt [Abrufen des Inhaltspaket-Maven-Plug-ins](#obtaining-the-content-package-maven-plugin) auf dieser Seite angegebene Profil, um Maven für das Herunterladen des Plug-ins zu aktivieren.

## Ziele des Inhaltspaket-Maven-Plug-ins {#goals-of-the-content-package-maven-plugin}

Die durch das Inhaltspaket-Plug-in bereitgestellten Ziele und Zielparameter werden in den folgenden Abschnitten beschrieben. Die im Abschnitt „Allgemeine Parameter“ beschriebenen Parameter können für die meisten der Ziele verwendet werden. Parameter, die für ein Ziel zutreffen, werden im Abschnitt für das jeweilige Ziel beschrieben.

### Plug-in-Präfix {#plugin-prefix}

Das Plugin-Präfix ist `content-package`. Verwenden Sie dieses Präfix, um ein Ziel über die Befehlszeile auszuführen, wie dies im folgenden Beispiel gezeigt wird:

```shell
mvn content-package:build
```

### Parameterpräfix {#parameter-prefix}

Sofern nicht anders angegeben, verwenden die Plug-in-Ziele und -Parameter das Präfix `vault`, wie im folgenden Beispiel:

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### Proxys {#proxies}

Ziele, die Proxys für AEM verwenden, verwenden die erste gültige Proxy-Konfiguration in den Maven-Einstellungen. Wenn keine Proxykonfiguration gefunden wird, wird kein Proxy verwendet. Siehe Parameter `useProxy` im Abschnitt [Allgemeine Parameter](#common-parameters).

### Allgemeine Parameter {#common-parameters}

Die Parameter in der folgenden Tabelle gelten für alle Ziele, außer wenn sie in der Spalte **Ziele** vermerkt sind.

| Name | Typ | Erforderlich | Standardwert | Beschreibung | Ziele |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | Nein | `false` | Der Wert `true` führt zum Fehlschlagen des Builds, wenn ein Fehler auftritt. Der Wert `false` führt dazu, dass der Build den Fehler ignoriert. | Alle Ziele außer `package` |
| `name` | `String` | `build`: Ja,  `install`: Nein,  `rm`: Ja | `build`: Keine Standardeinstellung  `install`: Der Wert der  `artifactId` Eigenschaft des Maven-Projekts | Der Name des zu bearbeitenden Pakets | Alle Ziele außer `ls` |
| `password` | `String` | Ja | `admin` | Das für die Authentifizierung mit AEM verwendete Kennwort | Alle Ziele außer `package` |
| `serverId` | `String` | Nein | Die Server-ID, über die der Benutzername und das Kennwort für die Authentifizierung abgerufen werden | Alle Ziele außer `package` |
| `targetURL` | `String` | Ja | `http://localhost:4502/crx/packmgr/service.jsp` | Die URL der HTTP-Dienst-API des AEM Paketmanagers | Alle Ziele außer `package` |
| `timeout` | `int` | Nein | `5` | Die Verbindungs-Zeitüberschreitung für die Kommunikation mit dem Paketmanagerdienst in Sekunden | Alle Ziele außer `package` |
| `useProxy` | `boolean` | Nein | `true` | Der Wert `true` bewirkt, dass Maven die erste aktive Proxykonfiguration verwendet, die gefunden wurde, um Anforderungen an den Package Manager zu verändern. | Alle Ziele außer `package` |
| `userId` | `String` | Ja | `admin` | Der Benutzername, der bei AEM authentifiziert werden soll | Alle Ziele außer `package` |
| `verbose` | `boolean` | Nein | `false` | Aktiviert oder deaktiviert die ausführliche Protokollierung | Alle Ziele außer `package` |

### Build {#build}

Erstellt ein Inhaltspaket, das bereits für eine AEM Instanz definiert ist.

>[!NOTE]
>
>Dieses Ziel muss nicht in einem Maven-Projekt ausgeführt werden.

#### Parameter {#parameters}

Alle Parameter für das Erstellungsziel werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

### Installieren {#install}

Installiert ein Paket im Repository. Für die Ausführung dieses Ziels ist kein Maven-Projekt erforderlich. Das Ziel ist an die `install`-Phase des Maven-Build-Lebenszyklus gebunden.

#### Parameter {#parameters-1}

Weitere Informationen zu den folgenden Parametern finden Sie in den Beschreibungen im Abschnitt [Allgemeine Parameter](#common-parameters).

| Name | Typ | Erforderlich | Standardwert | Beschreibung |
|---|---|---|---|---|---|
| `artifact` | `String` | Nein | Der Wert der Eigenschaft `artifactId` des Maven-Projekts | Eine Zeichenfolge des Formulars `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | Nein | Kein | Die ID des einzubettenden Artefakts. |
| `groupId` | `String` | Nein | Kein | Das `groupId` des zu installierenden Artefakts |
| `install` | `boolean` | Nein | `true` | Bestimmt, ob das Paket beim Hochladen automatisch entpackt werden soll |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | Nein | Der Wert der Systemvariablen `localRepository` | Das lokale Maven-Repository, das nicht mit der Plug-In-Konfiguration konfiguriert werden kann, da die Systemeigenschaft immer verwendet wird |
| `packageFile` | `java.io.File` | Nein | Das für das Maven-Projekt definierte primäre Artefakt | Der Name der zu installierenden Paketdatei |
| `packaging` | `String` | Nein | `zip` | Der Verpackungstyp des zu installierenden Artefakts. |
| `pomRemoteRepositories` | `java.util.List` | Ja | Der Wert der `remoteArtifactRepositories`-Eigenschaft, der für das Maven-Projekt definiert ist | Dieser Wert kann nicht mit der Plug-in-Konfiguration konfiguriert werden und muss im Projekt angegeben werden. |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Das Projekt, für das das Plugin konfiguriert ist | Das Maven-Projekt, das implizit ist, weil das Projekt die Plugin-Konfiguration enthält |
| `repositoryId` (POM),  `repoID` (Befehlszeile) | `String` | Nein | `temp` | Die ID des Repositorys, vom dem das Artefakt abgerufen wird |
| `repositoryUrl` (POM),  `repoURL` (Befehlszeile) | `String` | Nein | Kein | Die URL des Repositorys, vom dem das Artefakt abgerufen wird |
| Version | Zeichenfolge | Nein | Kein | Die Version des zu installierenden Artefakts |

### ls {#ls}

Führt die im Paketmanager bereitgestellten Pakete auf.

#### Parameter {#parameters-2}

Alle Parameter des ls-Ziels werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

### rm {#rm}

Entfernt ein Paket aus dem Paketmanager.

#### Parameter {#parameters-3}

Alle Parameter des rm-Ziels werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

### Deinstallieren {#uninstall}

Deinstalliert ein Paket. Das Paket verbleibt auf dem Server mit dem deinstallierten Status.

#### Parameter {#parameters-4}

Alle Parameter des Deinstallationsziels werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

### package {#package}

Erstellt ein Inhaltspaket. Die Standardkonfiguration des Paketziels umfasst die Inhalte des Verzeichnisses, in dem kompilierte Dateien gespeichert sind. Für die Ausführung des Paketziels muss die Phase der Build-Kompilierung abgeschlossen sein. Das Paketziel ist an die Paketphase des Maven-Build-Lebenszyklus gebunden.

#### Parameter {#parameters-5}

Zusätzlich zu den folgenden Parametern finden Sie in der Beschreibung des Parameters `name` im Abschnitt [Allgemeine Parameter](#common-parameters) weitere Informationen.

| Name | Typ | Erforderlich | Standardwert | Beschreibung |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | Nein | Kein | Die zu verwendende Archivkonfiguration |
| `builtContentDirectory` | `java.io.File` | Ja | Der Wert des Ausgabeverzeichnisses des Maven-Builds | Das Verzeichnis mit den in das Paket einzuschließenden Inhalten |
| `dependencies` | `java.util.List` | Nein | Kein |  |
| `embeddedTarget` | `java.lang.String` | Nein | Kein |  |
| `embeddeds` | `java.util.List` | Nein | Kein |  |
| `failOnMissingEmbed` | `boolean` | Ja | `false` | Der Wert `true` führt dazu, dass der Build fehlschlägt, wenn kein eingebettetes Artefakt in den Projektabhängigkeiten gefunden wird. Der Wert `false` bewirkt, dass der Build diese Fehler ignoriert. |
| `filterSource` | `java.io.File` | Nein | Kein | Dieser Parameter definiert eine Datei, die die Quelle des Arbeitsbereichfilters angibt. Die in der Konfiguration angegebenen und über Einbettungen oder Teilpakete eingefügten Filter werden mit dem Dateiinhalt zusammengeführt. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | Nein | Kein | Dieser Parameter enthält Filterelemente, die den Paketinhalt definieren. Bei Ausführung werden die Filter in die Datei `filter.xml` aufgenommen. Siehe den Abschnitt [Verwenden von Filtern](#using-filters) weiter unten. |
| `finalName` | `java.lang.String` | Ja | Das im Maven-Projekt definierte `finalName` (Build-Phase) | Der Name der generierten ZIP-Datei des Pakets ohne die Dateierweiterung `.zip` |
| `group` | `java.lang.String` | Ja | Das im Maven-Projekt definierte `groupID` | Das `groupId` des generierten Inhaltspakets, das zum Installationspfad der Zielgruppe für das Inhaltspaket gehört |
| `outputDirectory` | `java.io.File` | Ja | Das im Maven-Projekt definierte Build-Verzeichnis | Das lokale Verzeichnis, in dem das Inhaltspaket gespeichert ist |
| `prefix` | `java.lang.String` | Nein | Kein |  |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Kein | Das Maven-Projekt |
| `properties` | `java.util.Map` | Nein | Kein | Diese Parameter definieren zusätzliche Eigenschaften, die Sie in der Datei `properties.xml` festlegen können. Diese Eigenschaften können die folgenden vordefinierten Eigenschaften nicht überschreiben: `group` (set mithilfe des Parameters `group`), `name` (set mit dem Parameter `name`), `version` (set mit dem Parameter `version`), `description` (aus der Projektbeschreibung festgelegt), `groupId` (`groupId` des Maven-Projektdeskriptors), `artifactId` (`artifactId` Maven-Projektdeskriptor), `dependencies` (verwenden Sie `dependencies`-Parameter festzulegen), `createdBy` (der Wert der `user.name`-Systemeigenschaft), `created` (die aktuelle Systemzeit), `requiresRoot` (verwenden Sie `requiresRoot`-Parameter, um festzulegen), &lt;a1 8/> (wird automatisch aus dem Gruppen- und Paketnamen generiert)`packagePath` |
| `requiresRoot` | `boolean` | Ja | false | Definiert, ob für das Paket „root“ erforderlich ist Dies wird zur `requiresRoot`-Eigenschaft der `properties.xml`-Datei. |
| `subPackages` | `java.util.List` | Nein | Kein |  |
| `version` | `java.lang.String` | Ja | Die im Maven-Projekt definierte Version | Die Version des Inhaltspakets |
| `workDirectory` | `java.io.File` | Ja | Der im Maven-Projekt definierte Ordner (Build-Phase) | Das Verzeichnis mit den in das Paket einzuschließenden Inhalten |

#### Verwenden von „filters“{#using-filters}

Verwenden Sie das Element „filters“ zum Definieren des Paketinhalts. Die Filter werden dem Element `workspaceFilter` in der Datei `META-INF/vault/filter.xml` des Pakets hinzugefügt.

Im folgenden Filterbeispiel wird die zu verwendende XML-Struktur gezeigt:

```xml
<filter>
   <root>/apps/myapp</root>
   <mode>merge</mode>
       <includes>
              <include>/apps/myapp/install/</include>
              <include>/apps/myapp/components</include>
       </includes>
       <excludes>
              <exclude>/apps/myapp/config/*</exclude>
       </excludes>
</filter>
```

##### Importmodus {#import-mode}

Das Element `mode` definiert, wie sich das Importieren des Pakets auf den Inhalt im Repository auswirkt. Die folgenden Werte können verwendet werden:

* **Merge:** Inhalt im Paket, der sich nicht bereits im Repository befindet, wird hinzugefügt. Inhalt, der sich im Paket und Repository befindet, verbleibt unverändert. Es wird kein Inhalt aus dem Repository entfernt.
* **Ersetzen:** Inhalte im Paket, die sich nicht im Repository befinden, werden dem Repository hinzugefügt. Inhalt im Repository wird durch übereinstimmenden Inhalt im Paket ersetzt. Inhalt wird aus dem Repository entfernt, wenn er im Paket nicht vorhanden ist.
* **Update:** Inhalt im Paket, der sich nicht im Repository befindet, wird zum Repository hinzugefügt. Inhalt im Repository wird durch übereinstimmenden Inhalt im Paket ersetzt. Vorhandener Inhalt wird aus dem Repository entfernt.

Wenn der Filter kein `mode`-Element aufweist, wird der Standardwert `replace` verwendet.

### help {#help}

#### Parameter {#parameters-6}

| Name | Typ | Erforderlich | Standardwert | Beschreibung |
|---|---|---|---|---|
| `detail` | `boolean` | Nein | `false` | Bestimmt, ob alle festlegbaren Eigenschaften für jedes Ziel angezeigt werden sollen |
| `goal` | `String` | Nein | Kein | Diese Parameter definieren den Namen des Ziels, für das die Hilfe angezeigt werden soll. Wenn kein Wert angegeben wird, wird die Hilfe für alle Ziele angezeigt. |
| `indentSize` | `int` | Nein | `2` | Die Anzahl der Leerzeichen, die für die Einrückung jeder Ebene verwendet werden müssen (muss positiv sein, wenn definiert) |
| `lineLength` | `int` | Nein | `80` | Die maximale Länge einer Anzeigelinie (muss positiv sein, wenn definiert) |

## Einbeziehen eines Miniaturbilds oder einer Eigenschaftsdatei im Paket {#including-a-thumbnail-image-or-properties-file-in-the-package}

Ersetzen Sie die standardmäßigen Paketkonfigurationsdateien, um die Paketeigenschaften anzupassen. Verwenden Sie beispielsweise ein Miniaturbild, um das Paket im Paketmanager und in Package Share voneinander zu unterscheiden.

Die Quelldateien können sich überall in Ihrem Dateisystem befinden. Definieren Sie in der POM-Datei Buildressourcen, um die Quelldateien in das `target/vault-work/META-INF` zu kopieren und in das Paket einzuschließen.

Mit dem folgenden POM-Code werden die Dateien im Ordner `META-INF` der Projektquelle zum Paket hinzugefügt:

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail etc.) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

Im folgenden POM-Code wird nur ein Miniaturbild zum Paket hinzugefügt. Das Miniaturbild muss den Namen `thumbnail.png` haben und sich im Ordner `META-INF/vault/definition` des Pakets befinden. In diesem Beispiel befindet sich die Quelldatei im Ordner `/src/main/content/META-INF/vault/definition` des Projekts:

```xml
<build>
    <resources>
        <!-- thumbnail only -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF/vault/definition</directory>
            <targetPath>../vault-work/META-INF/vault/definition</targetPath>
        </resource>
    </resources>
</build>
```

## Verwenden des AEM Projektarchivs zum Generieren AEM Projekte {#using-archetypes}

Das neueste AEM Project Archetype implementiert die Best-Practice-Paketstruktur für lokale und AMS-Implementierungen und wird für alle AEM Projekte empfohlen.

>[!TIP]
>
>Weitere Informationen finden Sie im Artikel [AEM Projektstruktur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) in der AEM als Cloud Service-Dokumentation sowie in der [AEM Projektarchiv](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)-Dokumentation. Beide werden für AEM 6.5 vollständig unterstützt.
