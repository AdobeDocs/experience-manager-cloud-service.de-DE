---
title: AEM Application Project - Cloud Service
description: AEM Application Project - Cloud Service
translation-type: tm+mt
source-git-commit: 57206e36725e28051b2468d47da726e318bd763b
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 92%

---


# Erstellen eines AEM-Anwendungsprojekts {#aem-application-project}

## Arbeiten mit dem Assistenten zum Erstellen eines AEM-Anwendungsprojekts {#using-wizard-to-create-an-aem-application-project}

Um neuen Kunden die ersten Schritte zu erleichtern, kann Cloud Manager jetzt als Ausgangspunkt ein minimales AEM-Projekt erstellen. Dieser Vorgang basiert auf dem [**AEM-Projektarchetyp **](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Gehen Sie wie folgt vor, um ein AEM-Anwendungsprojekt in Cloud Manager zu erstellen:

1. Wenn Sie sich bei Cloud Manager anmelden und die grundlegende Programmeinrichtung abgeschlossen haben und das Repository zu diesem Zeitpunkt leer ist, wird im Bildschirm **Überblick** eine spezielle Aktionskarte angezeigt.

   ![](assets/create-wizard1.png)

1. Klicken Sie auf **Erstellen**, um zum Bildschirm **Verzweigung und Projekt erstellen** zu navigieren.

   ![](assets/create-wizard2.png)

1. Die Kachel &quot; **Projekterstellung in Bearbeitung** &quot;wird im Bildschirm &quot; *Programm-Übersicht* &quot;angezeigt.

   ![](assets/create-wizard3.png)

1. Sobald die Programmerstellung abgeschlossen ist, wird die Kachel **Umgebung hinzufügen** auf der Seite *Programmübersicht* angezeigt.
   ![](assets/create-wizard4.png)

   Informationen zum Hinzufügen und Verwalten von Umgebung finden Sie unter [Verwalten Ihrer Umgebung](/help/implementing/cloud-manager/manage-environments.md) .

## Einrichten des Projekts {#setting-up-your-project}

### Ändern der Projekteinstellungen {#modifying-project-setup-details}

Damit vorhandene AEM-Projekte erfolgreich in Cloud Manager erstellt und bereitgestellt werden können, müssen einige grundlegende Regeln berücksichtigt werden:

* Projekte müssen mit Apache Maven erstellt werden.
* Im Stammverzeichnis des Git-Repositorys muss eine Datei *pom.xml* vorhanden sein. Diese *pom.xml*-Datei kann ggf. auf beliebig viele Untermodule verweisen (die wiederum weitere Untermodule umfassen usw.) wie nötig.

* Sie können Verweise auf weitere Maven-Artefakt-Repositorys in Ihren *pom.xml*-Dateien hinzufügen. Allerdings wird der Zugriff auf kennwortgeschützte oder netzwerkgeschützte Artefakte nicht unterstützt.
* Bereitstellbare Inhaltspakete werden erkannt, wenn Sie nach Inhaltspaketen im *ZIP*-Format suchen, die in einem Verzeichnis mit dem Namen *target* enthalten sind. Eine beliebige Anzahl von Untermodulen kann Inhaltspakete produzieren.

* Bereitstellbare Dispatcher-Artefakte werden erkannt, wenn Sie nach *ZIP*-Dateien (ebenfalls in einem Verzeichnis namens *target*) suchen, die Verzeichnisse mit den Namen *conf* und *conf.d* enthalten.

* Wenn mehrere Inhaltspakete vorhanden sind, ist die Reihenfolge der Paketbereitstellungen nicht garantiert. Wenn eine bestimmte Reihenfolge benötigt wird, können die Abhängigkeiten des Inhaltspakets zum Definieren der Reihenfolge verwendet werden. Pakete können bei der Bereitstellung [übersprungen](#skipping-content-packages) werden.


## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung. Diese Umgebung weist die folgenden Attribute auf:

* Die Erstellungsumgebung ist Linux-basiert und von Ubuntu 18.04 abgeleitet.
* Apache Maven 3.6.0 ist installiert.
* Die installierte Java-Version ist Oracle JDK 8u202.
* Es sind einige zusätzliche erforderliche Systempakete installiert:

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick

* Andere Pakete können zur Erstellungszeit wie [unten](#installing-additional-system-packages) beschrieben installiert werden.
* Jeder Build wird in einer unberührten Umgebung erstellt, der Build-Container speichert zwischen den Ausführungen keinen Status.
* Maven wird immer mit folgendem Befehl ausgeführt: *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* Maven wird auf Systemebene mit einer settings.xml-Datei konfiguriert, die automatisch das öffentliche Adobe-**Artefakt**-Repository enthält. (Weitere Informationen dazu finden Sie im [Adobe Public Maven Repository](https://repo.adobe.com/)).


## Umgebungsvariablen {#environment-variables}

### Standard-Umgebungsvariablen {#standard-environ-variables}

In einigen Fällen müssen Kunden den Build-Prozess je nach Informationen zum Programm oder zur Pipeline variieren.

Wenn beispielsweise eine JavaScript-Minimierung während der Build-Erstellung mithilfe eines Tools wie gulp durchgeführt wird, soll beim Erstellen für eine Entwicklungsumgebung möglicherweise eine andere Minimierungsstufe verwendet werden als beim Erstellen für eine Staging- oder Produktionsumgebung.

Um dies zu unterstützen, fügt Cloud Manager diese Standard-Umgebungsvariablen bei jeder Ausführung dem Build-Container hinzu.

| **Variablenname** | **Definition** |
|---|---|
| CM_BUILD | Immer auf „true“ (wahr) festgelegt |
| BRANCH | Die konfigurierte Verzweigung für die Ausführung |
| CM_PIPELINE_ID | Numerische Pipeline-Kennung |
| CM_PIPELINE_NAME | Name der Pipeline |
| CM_PROGRAM_ID | Numerische Programmkennung |
| CM_PROGRAM_NAME | Name des Programms |
| ARTIFACTS_VERSION | Die von Cloud Manager generierte synthetische Version bei einer Staging- oder Produktions-Pipeline |
| CM_AEM_PRODUCT_VERSION | Der Name der Version |


### Benutzerdefinierte Umgebungsvariablen {#custom-environ-variables}

In einigen Fällen kann der Build-Prozess eines Kunden von bestimmten Konfigurationsvariablen abhängen, die nicht im Git-Repository platziert werden sollten. Cloud Manager ermöglicht die kundenspezifische Konfiguration dieser Variablen durch einen Adobe-Kundenbetreuer. Sie werden an einem sicheren Speicherort gespeichert und sind nur im Build-Container für den jeweiligen Kunden sichtbar. Kunden, die diese Funktion verwenden möchten, müssen sich an ihren Adobe-Kundenbetreuer wenden, um ihre Variablen zu konfigurieren.

Nach der Konfiguration sind diese Variablen als Umgebungsvariablen verfügbar. Um sie als Maven-Eigenschaften zu verwenden, können Sie sie in Ihrer Datei pom.xml referenzieren, ggf. in einem Profil wie oben beschrieben:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>Namen von Umgebungsvariablen dürfen nur alphanumerische Zeichen und Unterstriche (_) enthalten. Dabei sollten Großbuchstaben verwendet werden.

## Aktivieren von Maven-Profilen in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In einigen wenigen Fällen müssen Sie den Build-Prozess möglicherweise etwas anders gestalten, wenn er in Cloud Manager und auf Entwickler-Workstations ausgeführt wird. In diesen Fällen können Sie mit [Maven-Profilen](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) definieren, wie der Build in verschiedenen Umgebungen (einschließlich Cloud Manager) abweichen soll.

Die Aktivierung eines Maven-Profils in der Cloud Manager-Build-Umgebung sollte über die oben beschriebene Umgebungsvariable CM_BUILD erfolgen. Beim Erstellen eines Profils, das nur außerhalb der Cloud Manager-Build-Umgebung verwendet werden soll, sollte hingegen das Nichtvorhandensein dieser Variable verifiziert werden.

Wenn zum Beispiel eine einfache Nachricht nur dann ausgegeben werden soll, wenn der Build innerhalb von Cloud Manager ausgeführt wird, verwenden Sie Folgendes:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Um dieses Profil auf einer Entwickler-Workstation zu testen, können Sie es entweder in der Befehlszeile (mit `-PcmBuild`) oder in der integrierten Entwicklungsumgebung (IDE) aktivieren.

Wenn zum Beispiel eine einfache Nachricht nur dann ausgegeben werden soll, wenn der Build außerhalb von Cloud Manager ausgeführt wird, verwenden Sie Folgendes:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```


## Installieren zusätzlicher Systempakete {#installing-additional-system-packages}

Einige Builds erfordern die Installation zusätzlicher Systempakete, damit sie vollumfänglich funktionieren. So ist es z. B. möglich, dass ein Build ein Python- oder Ruby-Skript aufruft, wofür der entsprechende Sprach-Interpreter installiert sein muss. Dies kann durch Abfrage von [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) erfolgen, wodurch APT aufgerufen wird. Diese Ausführung sollte im Allgemeinen in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen sein. So installieren Sie beispielsweise Python:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Mit derselben Methode können Sie auch sprachspezifische Pakete installieren, d. h. mit `gem` für RubyGems oder mit `pip` für Python-Pakete.

>[!NOTE]
>
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es **nicht** in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein auf der AEM-Umgebung installiertes Systempaket benötigen, wenden Sie sich an Ihren Adobe-Kundenbetreuer.

## Überspringen von Inhaltspaketen {#skipping-content-packages}

In Cloud Manager können Builds eine beliebige Anzahl von Inhaltspaketen generieren.
Aus vielerlei Gründen kann es sinnvoll sein, ein Inhaltspaket zu erstellen, es jedoch nicht bereitzustellen. Dies kann nützlich sein, etwa für Inhaltspakete, die nur zum Testen erstellt wurden, oder für Pakete, die in einem anderen Schritt im Build-Prozess (also als Unterpaket eines anderen Pakets) neu verpackt werden.

Um diese Szenarien zu berücksichtigen, sucht Cloud Manager in den Eigenschaften erstellter Inhaltspakete nach einer Eigenschaft namens ***cloudManagerTarget***. Wenn diese Eigenschaft auf „Ohne“ festgelegt ist, wird das Paket übersprungen und nicht bereitgestellt. Der Mechanismus zum Festlegen dieser Eigenschaft hängt davon ab, wie der Build das Inhaltspaket erzeugt. Mit dem filevault-maven-Plugin würden Sie beispielsweise das Plugin wie folgt konfigurieren:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Mit dem content-package-maven-Plugin ist es ähnlich:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```
