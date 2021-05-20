---
title: Adobe Content Package Maven-Plug-in
description: Verwenden Sie das Content Package Maven-Plug-in, um AEM-Anwendungen bereitzustellen.
exl-id: d631d6df-7507-4752-862b-9094af9759a0
source-git-commit: 03b2237dfde6ec605d8dcd8789ec4f2aa67716ca
workflow-type: tm+mt
source-wordcount: '1855'
ht-degree: 98%

---

# Adobe Content Package Maven-Plug-in {#adobe-content-package-maven-plugin}

Verwenden Sie das Adobe Content Package Maven-Plug-in, um Paketbereitstellungs- und -verwaltungsaufgaben in Ihre Maven-Projekte zu integrieren.

Die Bereitstellung der erstellten Pakete in AEM wird vom Adobe Content Package Maven-Plug-in durchgeführt und ermöglicht die Automatisierung von Aufgaben, die normalerweise mit AEM Package Manager ausgeführt werden:

* Erstellen Sie neue Pakete anhand der Dateien im Dateisystem.
* Installieren und deinstallieren Sie Pakete in AEM.
* Erstellen Sie bereits in AEM definierte Pakete.
* Rufen Sie eine Liste der in AEM installierten Pakete ab.
* Entfernen Sie ein Paket aus AEM.

In diesem Dokument wird erläutert, wie Sie diese Aufgaben mit Maven verwalten können. Es ist jedoch auch wichtig zu verstehen, [wie AEM Projekte und ihre Pakete strukturiert sind.](#aem-project-structure)

>[!NOTE]
>
>Die Paketerstellung wird jetzt über das [Apache Jackrabbit FileVault Package Maven-Plug-in](https://jackrabbit.apache.org/filevault-package-maven-plugin/) durchgeführt. Die Bereitstellung der erstellten Pakete in AEM erfolgt wie hier beschrieben über das Adobe Content Package Maven-Plug-in.

## Pakete und die AEM-Projektstruktur {#aem-project-structure}

AEM as a Cloud Service hält sich an die neuesten Best Practices für Package Management und Projektstruktur, die vom neuesten AEM Projektarchetyp implementiert wurden.

>[!TIP]
>
>Weitere Informationen finden Sie im Artikel [AEM-Projektstruktur](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) in der AEM as a Cloud Service -Dokumentation sowie in der Dokumentation zum [AEM-Projektarchetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html). Beide werden für AEM 6.5 vollständig unterstützt.

## Abrufen des Content Package Maven-Plug-ins {#obtaining-the-content-package-maven-plugin}

Das Plug-in ist im [Maven Central Repository](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public) verfügbar.

## Ziele und Parameter des Content Package Maven-Plug-ins

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

## Ziele des Inhaltspaket-Maven-Plug-ins  {#goals-of-the-content-package-maven-plugin}

Die durch das Inhaltspaket-Plug-in bereitgestellten Ziele und Zielparameter werden in den folgenden Abschnitten beschrieben. Die im Abschnitt „Allgemeine Parameter“ beschriebenen Parameter können für die meisten der Ziele verwendet werden. Parameter, die für ein Ziel zutreffen, werden im Abschnitt für das jeweilige Ziel beschrieben.

### Plug-in-Präfix {#plugin-prefix}

Das Plug-in-Präfix lautet `content-package`. Verwenden Sie dieses Präfix, um ein Ziel über die Befehlszeile auszuführen, wie dies im folgenden Beispiel gezeigt wird:

```shell
mvn content-package:build
```

### Parameterpräfix {#parameter-prefix}

Soweit nicht anderweitig gekennzeichnet, verwenden die Plug-in-Ziele und -Parameter das Präfix `vault`. Dies gilt auch für das folgende Beispiel:

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### Proxys {#proxies}

Ziele, die Proxys für AEM verwenden, verwenden die erste gültige Proxy-Konfiguration, die in den Maven-Einstellungen gefunden wurde. Wenn keine Proxy-Konfiguration gefunden wird, wird kein Proxy verwendet. Siehe hierzu den Parameter `useProxy` im Abschnitt [Allgemeine Parameter](#common-parameters).

### Allgemeine Parameter {#common-parameters}

Die Parameter in der folgenden Tabelle gelten für alle Ziele, sofern kein entsprechender Hinweis in der Spalte **Ziele** vorliegt.

| Name | Typ | Erforderlich | Standardwert | Beschreibung | Ziele |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | Nein | `false` | Der Wert `true` führt zum Fehlschlagen des Builds, wenn ein Fehler auftritt. Der Wert `false` führt dazu, dass der Build den Fehler ignoriert. | Alle Ziele mit Ausnahme von `package` |
| `name` | `String` | `build`: Ja, `install`: Nein, `rm`: Ja | `build`: Kein Standard, `install`: Der Wert der Eigenschaft `artifactId` des Maven-Projekts | Der Name des zu bearbeitenden Pakets | Alle Ziele mit Ausnahme von `ls` |
| `password` | `String` | Ja | `admin` | Das für die Authentifizierung mit AEM verwendete Passwort | Alle Ziele mit Ausnahme von `package` |
| `serverId` | `String` | Nein | Die Server-ID, über die der Benutzername und das Passwort für die Authentifizierung abgerufen werden | Alle Ziele mit Ausnahme von `package` |
| `targetURL` | `String` | Ja | `http://localhost:4502/crx/packmgr/service.jsp` | Die URL der HTTP-Service-API von AEM Package Manager | Alle Ziele mit Ausnahme von `package` |
| `timeout` | `int` | Nein | `5` | Die Verbindungszeitüberschreitung für die Kommunikation mit dem Package Manager-Service in Sekunden | Alle Ziele mit Ausnahme von `package` |
| `useProxy` | `boolean` | Nein | `true` | Der Wert von `true` veranlasst Maven, die erste aktive Proxy-Konfiguration zu verwenden, die gefunden wurde, um Anforderungen an Package Manager zu senden. | Alle Ziele mit Ausnahme von `package` |
| `userId` | `String` | Ja | `admin` | Der Benutzername zur Authentifizierung bei AEM | Alle Ziele mit Ausnahme von `package` |
| `verbose` | `boolean` | Nein | `false` | Aktiviert oder deaktiviert die ausführliche Protokollierung | Alle Ziele mit Ausnahme von `package` |

### build {#build}

Erstellt ein Inhaltspaket, das bereits auf einer AEM-Instanz definiert ist.

>[!NOTE]
>
>Dieses Ziel muss nicht in einem Maven-Projekt ausgeführt werden.

#### Parameter {#parameters}

Alle Parameter für das Build-Ziel werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

### install {#install}

Installiert ein Paket im Repository. Für die Ausführung dieses Ziels ist kein Maven-Projekt erforderlich. Das Ziel ist an die `install`-Phase des Maven-Build-Lebenszyklus gebunden.

#### Parameter {#parameters-1}

Lesen Sie neben den folgenden Parametern die Beschreibungen im Abschnitt [Allgemeine Parameter](#common-parameters).

| Name | Typ | Erforderlich | Standardwert | Beschreibung |
|---|---|---|---|---|---|
| `artifact` | `String` | Nein | Der Wert der Eigenschaft `artifactId` des Maven-Projekts | Eine Zeichenfolge in der Form `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | Nein | Kein | Die ID des einzubettenden Artefakts. |
| `groupId` | `String` | Nein | Kein | Die `groupId` des zu installierenden Artefakts |
| `install` | `boolean` | Nein | `true` | Bestimmt, ob das Paket beim Hochladen automatisch entpackt werden soll |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | Nein | Der Wert der Systemvariablen `localRepository` | Das lokale Maven-Repository, das nicht über die Plug-in-Konfiguration konfiguriert werden kann, da immer die Systemeigenschaft verwendet wird |
| `packageFile` | `java.io.File` | Nein | Das für das Maven-Projekt definierte primäre Artefakt | Der Name der zu installierenden Paketdatei |
| `packaging` | `String` | Nein | `zip` | Der Verpackungstyp des zu installierenden Artefakts. |
| `pomRemoteRepositories` | `java.util.List` | Ja | Der Wert der für das Maven-Projekt definierten Eigenschaft `remoteArtifactRepositories` | Dieser Wert kann nicht mit der Plug-in-Konfiguration konfiguriert werden und muss im Projekt angegeben werden. |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Das Projekt, für das das Plug-in konfiguriert ist | Das Maven-Projekt, welches implizit ist, da das Projekt die Plug-in-Konfiguration enthält |
| `repositoryId` (POM), `repoID` (Befehlszeile) | `String` | Nein | `temp` | Die ID des Repositorys, vom dem das Artefakt abgerufen wird |
| `repositoryUrl` (POM), `repoURL` (Befehlszeile) | `String` | Nein | Kein | Die URL des Repositorys, vom dem das Artefakt abgerufen wird |
| Version | Zeichenfolge | Nein | Kein | Die Version des zu installierenden Artefakts |

### ls {#ls}

Führt die im Paketmanager bereitgestellten Pakete auf.

#### Parameter {#parameters-2}

Alle Parameter des Ziels „Is“ werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

### rm {#rm}

Entfernt ein Paket aus dem Paketmanager.

#### Parameter {#parameters-3}

Alle Parameter des Ziels „rm“ werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

### uninstall {#uninstall}

Deinstalliert ein Paket. Das Paket verbleibt auf dem Server mit dem deinstallierten Status.

#### Parameter {#parameters-4}

Alle Parameter des Ziels „uninstall“ werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

### package {#package}

Erstellt ein Inhaltspaket. Die Standardkonfiguration des Paketziels umfasst die Inhalte des Verzeichnisses, in dem kompilierte Dateien gespeichert sind. Für die Ausführung des Paketziels muss die Phase der Build-Kompilierung abgeschlossen sein. Das Paketziel ist an die Paketphase des Maven-Build-Lebenszyklus gebunden.

#### Parameter {#parameters-5}

Lesen Sie neben den folgenden Parametern die Beschreibung des Parameters `name` im Abschnitt [Allgemeine Parameter](#common-parameters).

| Name | Typ | Erforderlich | Standardwert | Beschreibung |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | Nein | Kein | Die zu verwendende Archivkonfiguration |
| `builtContentDirectory` | `java.io.File` | Ja | Der Wert des Ausgabeverzeichnisses des Maven-Builds | Das Verzeichnis mit den in das Paket einzuschließenden Inhalten |
| `dependencies` | `java.util.List` | Nein | Kein |  |
| `embeddedTarget` | `java.lang.String` | Nein | Kein |  |
| `embeddeds` | `java.util.List` | Nein | Kein |  |
| `failOnMissingEmbed` | `boolean` | Ja | `false` | Der Wert `true` führt zum Fehlschlagen des Builds, wenn ein eingebettetes Artefakt in den Projektabhängigkeiten nicht gefunden werden kann. Der Wert `false` führt dazu, dass der Build solche Fehler ignoriert. |
| `filterSource` | `java.io.File` | Nein | Kein | Dieser Parameter definiert eine die Quelle des Arbeitsbereichsfilters angebende Datei. Die in der Konfiguration angegebenen und über Einbettungen oder Teilpakete eingefügten Filter werden mit dem Dateiinhalt zusammengeführt. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | Nein | Kein | Dieser Parameter enthält Filterelemente, die den Paketinhalt definieren. Bei der Ausführung werden die Filter in der Datei `filter.xml` eingeschlossen. Siehe hierzu im Folgenden den Abschnitt [Verwenden von „filters“](#using-filters). |
| `finalName` | `java.lang.String` | Ja | Der im Maven-Projekt (Build-Phase) definierte `finalName` | Der Name der generierten ZIP-Paketdatei ohne die Dateierweiterung `.zip` |
| `group` | `java.lang.String` | Ja | Die im Maven-Projekt definierte `groupID` | Die `groupId` des generierten Inhaltspakets, die Teil des Ziel-Installationspfads für das Inhaltspaket ist |
| `outputDirectory` | `java.io.File` | Ja | Das im Maven-Projekt definierte Build-Verzeichnis | Das lokale Verzeichnis, in dem das Inhaltspaket gespeichert ist |
| `prefix` | `java.lang.String` | Nein | Kein |  |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Kein | Das Maven-Projekt |
| `properties` | `java.util.Map` | Nein | Kein | Diese Parameter definieren zusätzliche Eigenschaften, die Sie in der Datei `properties.xml` festlegen können. Diese Eigenschaften können die folgenden vordefinierten Eigenschaften nicht außer Kraft setzen: `group` (Parameter `group` zum Festlegen verwenden), `name` (Parameter `name` zum Festlegen verwenden), `version` (Parameter `version` zum Festlegen verwenden), `description` (festgelegt anhand der Projektbeschreibung), `groupId` (`groupId` des Maven-Projektdeskriptors), `artifactId` (`artifactId` des Maven-Projektdeskriptors), `dependencies` (Parameter `dependencies` zum Festlegen verwenden), `createdBy` (Wert der Systemeigenschaft `user.name`), `created` (die aktuelle Systemzeit), `requiresRoot` (Parameter `requiresRoot` zum Festlegen verwenden), `packagePath` (automatisch generiert anhand des Gruppen- und Paketnamens) |
| `requiresRoot` | `boolean` | Ja | false | Definiert, ob für das Paket „root“ erforderlich ist. Dies wird zur `requiresRoot`-Eigenschaft der `properties.xml`-Datei. |
| `subPackages` | `java.util.List` | Nein | Kein |  |
| `version` | `java.lang.String` | Ja | Die im Maven-Projekt definierte Version | Die Version des Inhaltspakets |
| `workDirectory` | `java.io.File` | Ja | Das im Maven-Projekt (Build-Phase) definierte Verzeichnis | Das Verzeichnis mit den in das Paket einzuschließenden Inhalten |

#### Verwenden von „filters“ {#using-filters}

Verwenden Sie das Element „filters“ zum Definieren des Paketinhalts. Die Filter werden zum Element `workspaceFilter` in der Datei `META-INF/vault/filter.xml` des Pakets hinzugefügt.

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
* **Replace:** Inhalt im Paket, der sich nicht im Repository befindet, wird zum Repository hinzugefügt. Inhalt im Repository wird durch übereinstimmenden Inhalt im Paket ersetzt. Inhalt wird aus dem Repository entfernt, wenn er im Paket nicht vorhanden ist.
* **Update:** Inhalt im Paket, der sich nicht im Repository befindet, wird zum Repository hinzugefügt. Inhalt im Repository wird durch übereinstimmenden Inhalt im Paket ersetzt. Vorhandener Inhalt wird aus dem Repository entfernt.

Wenn der Filter kein `mode`-Element aufweist, wird der Standardwert `replace` verwendet.

### help {#help}

#### Parameter {#parameters-6}

| Name | Typ | Erforderlich | Standardwert | Beschreibung |
|---|---|---|---|---|
| `detail` | `boolean` | Nein | `false` | Bestimmt, ob alle festlegbaren Eigenschaften für jedes Ziel angezeigt werden sollen |
| `goal` | `String` | Nein | Kein | Dieser Parameter definiert den Namen des Ziels, für das die Hilfe angezeigt werden soll. Wenn kein Wert angegeben wird, wird die Hilfe für alle Ziele angezeigt. |
| `indentSize` | `int` | Nein | `2` | Die Anzahl der für die Einrückung jeder Ebene zu verwendenden Leerzeichen (muss positiv sein, wenn definiert) |
| `lineLength` | `int` | Nein | `80` | Die maximale Länge einer Anzeigelinie (muss positiv sein, wenn definiert) |

## Einbeziehen eines Miniaturbilds oder einer Eigenschaftsdatei im Paket {#including-a-thumbnail-image-or-properties-file-in-the-package}

Ersetzen Sie die standardmäßigen Paketkonfigurationsdateien, um die Paketeigenschaften anzupassen. Verwenden Sie beispielsweise ein Miniaturbild, um das Paket im Paketmanager und in Package Share voneinander zu unterscheiden.

Die Quelldateien können sich überall in Ihrem Dateisystem befinden. Definieren Sie in der POM-Datei die Build-Ressourcen, um die Quelldateien nach `target/vault-work/META-INF` zu kopieren, um sie ins Paket einzuschließen.

Im folgenden POM-Code werden die Dateien im Ordner `META-INF` der Projektquelle zum Paket hinzugefügt:

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

Im folgenden POM-Code wird nur ein Miniaturbild zum Paket hinzugefügt. Das Miniaturbild muss `thumbnail.png` benannt werden und sich im Ordner `META-INF/vault/definition` des Pakets befinden. In diesem Beispiel befindet sich die Quelldatei im Ordner `/src/main/content/META-INF/vault/definition` des Projekts:

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

## Verwenden des AEM-Projektarchetyps zum Erzeugen von AEM-Projekten {#using-archetypes}

Der aktuelle AEM-Projektarchetyp implementiert die Best Practice-Paketstruktur sowohl für On-Premise- als auch für AMS-Implementierungen und wird für alle AEM-Projekte empfohlen.

>[!TIP]
>
>Weitere Informationen finden Sie im Artikel [AEM-Projektstruktur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) in der AEM as a Cloud Service -Dokumentation sowie in der Dokumentation zum [AEM-Projektarchetyp](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html). Beide werden für AEM 6.5 vollständig unterstützt.
