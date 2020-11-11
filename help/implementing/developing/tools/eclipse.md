---
title: AEM Developer Tools for Eclipse
description: AEM Developer Tools for Eclipse
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 28%

---


# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![](assets/eclipse-logo.png)

## Übersicht {#overview}

AEM Developer Tools for Eclipse ist ein Eclipse-Plug-in, das auf dem [Eclipse-Plug-in für Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) basiert, das unter der Apache-Lizenz 2 veröffentlicht wurde.

Es bietet mehrere Funktionen, die die AEM-Entwicklung vereinfachen:

* Nahtlose Integration mit AEM-Instanzen über Eclipse Server Connector
* Synchronisierung für Inhalte und OSGi-Pakete
* Debugging-Unterstützung mit Funktionen zum Hot-Swap-Code
* Einfacher Bootstrap von AEM-Projekten über einen speziellen Projekterstellungsassistenten
* Einfache Bearbeitung von JCR-Eigenschaften

## Voraussetzungen {#requirements}

Bevor Sie die AEM Developer Tools verwenden, müssen Sie:

* Download and install [Eclipse IDE for Enterprise Java Developers](https://www.eclipse.org/downloads/packages/).
* Configure your eclipse installation to ensure that you have at least 1 gigabyte of heap memory by editing your `eclipse.ini` configuration file as described in the [Eclipse FAQ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse).

>[!NOTE]
>
>On macOS, you need to right-click on **Eclipse.app** and then select **Show Package Contents** in order to find your `eclipse.ini`**.**

## How to Install the AEM Developer Tools for Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Once you have fulfilled the [requirements](#requirements) above, you can install the plugin as follows:

1. Open the [AEM Developer Tools Web Site.](https://eclipse.adobe.com/aem/dev-tools/)

1. Kopieren Sie den **Installationslink**.

   Beachten Sie, dass Sie alternativ ein Archiv herunterladen können, anstatt den Installationslink zu verwenden. Dies ermöglicht Offlineinstallation, aber Sie werden auf diese Weise automatische Update-Benachrichtigungen verpassen.

1. Öffnen Sie in Eclipse das Menü **Hilfe**.
1. Klicken Sie auf **Neue Software installieren**.
1. Klicken Sie auf **Hinzufügen...**.
1. Geben Sie in **Name** ein `AEM Developer Tools`.
1. Unter **Standort** kopieren Sie die Installations-URL.
1. Klicken Sie auf **Hinzufügen**.
1. Überprüfen Sie **AEM**- und **Sling**-Plug-ins.
1. Klicken Sie auf **Weiter**.
1. Klicken Sie im Fenster **Installationsdetails** erneut auf **Weiter** .
1. Accept the license agreements and click **Finish**.
1. Click **RestartNow** in order to restart Eclipse.

## Die AEM-Perspektive {#the-aem-perspective}

In Eclipse bestimmt eine Perspektive die Aktionen und Ansichten, die in einem Fenster verfügbar sind, und ermöglicht eine Aufgabe-orientierte Interaktion mit Ressourcen in Eclipse. Weitere Informationen zur Perspektive finden Sie in der [Eclipse-Dokumentation.](https://help.eclipse.org)

Die AEM Entwicklungstools für Eclipse bieten eine AEM Perspektive, mit der Sie die vollständige Kontrolle über Ihre AEM Projekte und Instanzen haben. So öffnen Sie die AEM:

1. Wählen Sie in der Eclipse-Menüleiste **Fenster** -> **Perspektive** -> Perspektive **** öffnen -> **Andere**.
1. Wählen Sie **AEM** im Dialogfeld aus und klicken Sie auf **Öffnen**.

![Die AEM-Perspektive in Eclipse](assets/eclipse-aem-perspective.png)

## Multi-Modul-Beispielprojekt {#sample-multi-module-project}

Die AEM Developer Tools for Eclipse werden mit einem Beispielprojekt mit mehreren Modulen geliefert, mit dem Sie schnell mit der Projektkonfiguration in Eclipse vertraut werden und das als Best Practice-Leitfaden für mehrere AEM-Funktionen dienen kann. [Erfahren Sie mehr über den Projektarchetyp](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

Führen Sie folgende Schritte aus, um das Beispielprojekt zu erstellen:

1. Im Menü **Datei** > **Neu** > **Projekt** navigieren Sie zum **AEM**-Bereich und wählen Sie **AEM Beispiel-Multi-Modul Projekt**.

   ![AEM Beispiel für ein Multi-Module-Projekt](assets/aem-sample-project.png)

1. Klicken Sie auf **Weiter**.

   >[!NOTE]
   >
   >Dieser Schritt kann einen Moment dauern, da m2eclipse die Archetypkataloge scannen muss.

1. Wählen Sie `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` aus dem Menü und klicken Sie dann auf **Weiter**.

   ![Archetyp-Version auswählen](assets/select-archetype.png)

1. Geben Sie die folgenden Felder für das Beispielprojekt ein:

   * **Name**
   * **Gruppen-ID**
   * **Artefakt-ID**
   * **appId** - Möglicherweise müssen Sie die **erweiterten** Optionen erweitern, um diesen Wert festzulegen.
   * **appTitle** - Möglicherweise müssen Sie die **erweiterten** Optionen erweitern, um diesen Wert festzulegen.
   * **Paket** - Möglicherweise müssen Sie die **erweiterten** Optionen erweitern, um diesen Wert festzulegen.

   ![Definieren von Archetypeigenschaften](assets/archetype-properties.png)

1. Klicken Sie auf **Weiter**.

1. Anschließend konfigurieren Sie einen AEM Server, zu dem Eclipse eine Verbindung herstellen soll.

   Um die Debugger-Funktion verwenden zu können, müssen Sie AEM im Debug-Modus gestartet haben, was z. B. durch Hinzufügen der folgenden Informationen zur Befehlszeile erreicht werden kann:

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![Verbindung mit AEM Server](assets/connect-server.png)

1. Klicken Sie auf **Beenden**. Die Projektstruktur wird erstellt.

   >[!NOTE]
   >
   >Bei einer Neuinstallation (genauer gesagt, wenn keine Abhängigkeiten heruntergeladen wurden) wird das Projekt möglicherweise mit Fehlern erstellt. In diesem Fall folgen Sie den Anweisungen unter [Ungültige Projektdefinition beheben](#resolving-invalid-project-definition).

## Anleitung zum Importieren vorhandener Projekte {#how-to-import-existing-projects}

Mit der Funktion &quot; **Neues Projekt** &quot;können Sie die richtige Struktur für Sie erstellen:

1. Befolgen Sie die Anweisungen, um ein [Beispiel-Multi-Module-Projekt](#sample-multi-module-project) zu erstellen, und Sie werden die folgenden Projekte erstellen lassen, die eine gesunde Trennung der Bedenken ermöglichen:

   * `PROJECT.ui.apps` für `/apps` und `/etc` Inhalte
   * `PROJECT.ui.content` für `/content` die
   * `PROJECT.core` für Java-Pakete (diese werden interessant, sobald Sie Java-Code hinzufügen möchten)
   * `PROJECT.it.launcher` und `PROJECT.it.tests` für Integrationstests

1. Ersetzen Sie den Inhalt Ihres `PROJECT.ui.apps` Projekts durch die Ordner `apps` und `etc` Ordner Ihres Pakets:

   1. Blenden Sie im Bedienfeld &quot;Project Explorer&quot; `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Klicken Sie mit der rechten Maustaste auf den `apps` Ordner und wählen Sie **Anzeigen in** > **System Explorer**.
   1. Löschen Sie die Ordner `apps` und `etc` Ordner, die jetzt angezeigt werden sollen, und platzieren Sie die Ordner `apps` und `etc` Ordner Ihres Inhaltspakets hier.
   1. Klicken Sie in Eclipse mit der rechten Maustaste auf das `PROJECT.ui.apps` Projekt und wählen Sie **Aktualisieren**.

1. Führen Sie dann dasselbe für das Paket aus `PROJECT.ui.content` und ersetzen Sie den Inhaltsordner durch das Paket:

   1. Blenden Sie im Bedienfeld &quot;Project Explorer&quot; `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Klicken Sie mit der rechten Maustaste auf den Ordner für den tieferen Inhalt und wählen Sie **Anzeigen in** -> **System Explorer**.
   1. Löschen Sie den Inhaltsordner, den Sie jetzt sehen sollten, und platzieren Sie hier den Inhaltsordner Ihres Inhaltspakets.
   1. Klicken Sie in Eclipse mit der rechten Maustaste auf das `PROJECT.ui.content` Projekt und wählen Sie **Aktualisieren**.

1. Jetzt müssen Sie die `filter.xml` Dateien dieser beiden Projekte aktualisieren, um dem Inhalt Ihres Inhaltspakets zu entsprechen. Öffnen Sie dazu die `META-INF/vault/filter.xml` Datei Ihres Inhaltspakets in einem separaten Text-/Code-Editor.

   * Dies ist ein Beispiel dafür, wie Ihre `filter.xml` Datei aussehen kann:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       <filter root="/apps/foo"/>
       <filter root="/apps/foundation/components/bar"/>
       <filter root="/etc/designs/foo"/>
       <filter root="/content/foo"/>
       <filter root="/content/dam/foo"/>
       <filter root="/content/usergenerated/content/foo"/>
   </workspaceFilter>
   ```

1. Was den Inhalt Ihres Pakets betrifft, das in zwei Projekte aufgeteilt wurde, müssen Sie diese Filterregeln auch in zwei unterteilen und die `filter.xml` Dateien der beiden Projekte entsprechend aktualisieren.

   1. Öffnen Sie in Eclipse `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. Ersetzen Sie den Inhalt des `<workspaceFilter>` Elements durch die Regeln Ihres Pakets, mit denen der Beginn `/apps` und `/etc`
      * Beispiel:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/apps/foo"/>
            <filter root="/apps/foundation/components/bar"/>
            <filter root="/etc/designs/foo"/>
         </workspaceFilter>
         ```
   1. Dann öffnen Sie `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. Ersetzen Sie die Regeln durch die Regeln Ihres Pakets, mit denen Beginn `/content`.
      * Beispiel:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/content/foo"/>
            <filter root="/content/dam/foo"/>
            <filter root="/content/usergenerated/content/foo"/>
         </workspaceFilter>
         ```


1. Achten Sie darauf, alle Änderungen zu speichern. Sie können diesen neuen Inhalt jetzt mit Ihrer AEM synchronisieren.

1. Stellen Sie im Bedienfeld &quot;Server&quot;sicher, dass die Verbindung gestartet wurde und falls nicht, dass sie Beginn wird.
1. Klicken Sie auf das Symbol **Bereinigen und Veröffentlichen** .

Nach Abschluss des Vorgangs sollte das Paket auf Ihrer Instanz ausgeführt werden, und beim Speichern werden alle Änderungen automatisch mit der Instanz synchronisiert.

Wenn Sie ein Paket aus Ihrem Projekt neu erstellen möchten, klicken Sie mit der rechten Maustaste auf das `PROJECT.ui.apps` oder `PROJECT.ui.content` und wählen Sie **Ausführen als** -> **Maven-Installation**.

Sie haben jetzt einen Zielgruppe-Ordner, der mit Ihrem Paket erstellt wurde (genannt z.B. `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Fehlerbehebung {#troubleshooting}

### Ungültige Projektdefinition beheben {#resolving-invalid-project-definition}

Um ungültige Abhängigkeiten und Projektdefinitionen aufzulösen, gehen Sie wie folgt vor:

1. Wählen Sie alle erstellten Projekte.
1. Kicken Sie mit der rechten Maustaste.
1. Wählen Sie im Kontextmenü **Maven** -> Projekte **aktualisieren**.
1. Aktivieren Sie **Aktualisierungen von Snapshots/Releases erzwingen**.
1. Klicken Sie auf **OK**.

Eclipse lädt die erforderlichen Abhängigkeiten herunter. Das könnte einen Moment dauern.

## Weitere Informationen {#more-information}

Die offizielle Website „Apache Sling IDE tooling for Eclipse“ bietet Ihnen nützliche Informationen:

* The [**Apache Sling IDE tooling for Eclipse** User Guide](https://sling.apache.org/documentation/development/ide-tooling.html), this documentation will guide you through the overall concepts, server integration and deployment capabilities supported by the AEM Development Tools.
* Der [Abschnitt zur Fehlerbehebung](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* Die [Liste der bekannten Probleme](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

Die folgende offizielle [Eclipse](https://eclipse.org/)-Dokumentation kann dabei helfen, Ihre Umgebung einzurichten:

* [Erste Schritte mit Eclipse](https://eclipse.org/users/)
* [Eclipse Luna-Hilfesystem](https://help.eclipse.org/luna/index.jsp)
* [Maven-Integration (m2eclipse)](https://www.eclipse.org/m2e/)
