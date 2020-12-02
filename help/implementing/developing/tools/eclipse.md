---
title: AEM Developer Tools for Eclipse
description: AEM Developer Tools für Eclipse
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 28%

---


# AEM Developer Tools für Eclipse{#aem-developer-tools-for-eclipse}

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

* Laden Sie [Eclipse IDE for Enterprise Java Developers](https://www.eclipse.org/downloads/packages/) herunter und installieren Sie es.
* Konfigurieren Sie Ihre eclipse-Installation, um sicherzustellen, dass Sie über mindestens 1 Gigabyte Heap-Speicher verfügen, indem Sie die Konfigurationsdatei `eclipse.ini` bearbeiten, wie in der [Eclipse FAQ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse) beschrieben.

>[!NOTE]
>
>Unter macOS müssen Sie mit der rechten Maustaste auf **Eclipse.app** klicken und dann **Paketinhalt anzeigen** auswählen, um Ihre `eclipse.ini`**zu finden.**

## Installieren der AEM Developer Tools für Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Nachdem Sie die obigen [Anforderungen](#requirements) erfüllt haben, können Sie das Plugin wie folgt installieren:

1. Öffnen Sie die Website [AEM Developer Tools.](https://eclipse.adobe.com/aem/dev-tools/)

1. Kopieren Sie den **Installationslink**.

   Beachten Sie, dass Sie alternativ ein Archiv herunterladen können, anstatt den Installationslink zu verwenden. Dies ermöglicht Offlineinstallation, aber Sie werden auf diese Weise automatische Update-Benachrichtigungen verpassen.

1. Öffnen Sie in Eclipse das Menü **Hilfe**.
1. Klicken Sie auf **Neue Software installieren**.
1. Klicken Sie auf **Hinzufügen...**.
1. Geben Sie unter **Name** `AEM Developer Tools` ein.
1. Unter **Standort** kopieren Sie die Installations-URL.
1. Klicken Sie auf **Hinzufügen**.
1. Überprüfen Sie **AEM**- und **Sling**-Plug-ins.
1. Klicken Sie auf **Weiter**.
1. Klicken Sie im Fenster **Installationsdetails** erneut auf **Weiter**.
1. Akzeptieren Sie die Lizenzvereinbarungen und klicken Sie auf **Fertigstellen**.
1. Klicken Sie auf **Jetzt neu starten**, um Eclipse neu zu starten.

## Die AEM-Perspektive {#the-aem-perspective}

In Eclipse bestimmt eine Perspektive die Aktionen und Ansichten, die in einem Fenster verfügbar sind, und ermöglicht eine Aufgabe-orientierte Interaktion mit Ressourcen in Eclipse. Weitere Informationen zur Perspektive finden Sie in der [Eclipse-Dokumentation.](https://help.eclipse.org)

Die AEM Entwicklungstools für Eclipse bieten eine AEM Perspektive, mit der Sie die vollständige Kontrolle über Ihre AEM Projekte und Instanzen haben. So öffnen Sie die AEM:

1. Wählen Sie in der Eclipse-Menüleiste **Fenster** -> **Perspektive** -> **Perspektive öffnen** -> **Andere**.
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
   * **appId** : Sie müssen die  **** erweiterten Optionen erweitern, um diesen Wert festzulegen.
   * **appTitle**  - Möglicherweise müssen Sie die erweiterten  **** Optionen erweitern, um diesen Wert festzulegen.
   * **Paket** : Sie müssen die erweiterten  **** Optionen erweitern, um diesen Wert festzulegen.

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

Mit der Funktion **Neues Projekt** können Sie die richtige Struktur für Sie erstellen:

1. Befolgen Sie die Anweisungen, um ein [Beispiel-Multi-Module-Projekt](#sample-multi-module-project) zu erstellen. Anschließend werden die folgenden Projekte für Sie erstellt, die eine gesunde Trennung der Bedenken ermöglichen:

   * `PROJECT.ui.apps` für  `/apps` und  `/etc` Inhalte
   * `PROJECT.ui.content` für  `/content` die
   * `PROJECT.core` für Java-Pakete (diese werden interessant, sobald Sie Java-Code hinzufügen möchten)
   * `PROJECT.it.launcher` und  `PROJECT.it.tests` für Integrationstests

1. Ersetzen Sie den Inhalt Ihres `PROJECT.ui.apps`-Projekts durch die Ordner `apps` und `etc` Ihres Pakets:

   1. Blenden Sie im ProjektExplorer-Bedienfeld `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps` aus.
   1. Klicken Sie mit der rechten Maustaste auf den Ordner `apps` und wählen Sie **Anzeigen in** > **System Explorer**.
   1. Löschen Sie die Ordner `apps` und `etc`, die jetzt angezeigt werden sollen, und platzieren Sie hier die Ordner `apps` und `etc` Ihres Inhaltspakets.
   1. Klicken Sie in Eclipse mit der rechten Maustaste auf das Projekt `PROJECT.ui.apps` und wählen Sie **Aktualisieren**.

1. Führen Sie dann dasselbe für `PROJECT.ui.content` aus und ersetzen Sie den Inhaltsordner durch das Paket:

   1. Blenden Sie im ProjektExplorer-Bedienfeld `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content` aus.
   1. Klicken Sie mit der rechten Maustaste auf den Ordner für den tieferen Inhalt und wählen Sie **Anzeigen in** -> **System Explorer**.
   1. Löschen Sie den Inhaltsordner, den Sie jetzt sehen sollten, und platzieren Sie hier den Inhaltsordner Ihres Inhaltspakets.
   1. Klicken Sie in Eclipse mit der rechten Maustaste auf das Projekt `PROJECT.ui.content` und wählen Sie **Aktualisieren**.

1. Jetzt müssen Sie die `filter.xml` Dateien dieser beiden Projekte aktualisieren, um dem Inhalt Ihres Inhaltspakets zu entsprechen. Öffnen Sie dazu die Datei `META-INF/vault/filter.xml` Ihres Inhaltspakets in einem separaten Text-/Code-Editor.

   * Dies ist ein Beispiel dafür, wie Ihre `filter.xml`-Datei aussehen kann:

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

1. Was den Inhalt Ihres Pakets betrifft, das in zwei Projekte aufgeteilt wurde, müssen Sie diese Filterregeln auch in zwei unterteilen und die `filter.xml`-Dateien der beiden Projekte entsprechend aktualisieren.

   1. Öffnen Sie in Eclipse `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. Ersetzen Sie den Inhalt des `<workspaceFilter>`-Elements durch die Regeln Ihres Pakets, das durch `/apps` und `/etc` Beginn wird.
      * Beispiel:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/apps/foo"/>
            <filter root="/apps/foundation/components/bar"/>
            <filter root="/etc/designs/foo"/>
         </workspaceFilter>
         ```
   1. Öffnen Sie dann `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. Ersetzen Sie die Regeln durch die Regeln Ihres Pakets, das mit `/content` Beginn wird.
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
1. Klicken Sie auf das Symbol **Clean and Publish**.

Nach Abschluss des Vorgangs sollte das Paket auf Ihrer Instanz ausgeführt werden, und beim Speichern werden alle Änderungen automatisch mit der Instanz synchronisiert.

Wenn Sie ein Paket aus Ihrem Projekt neu erstellen möchten, klicken Sie mit der rechten Maustaste auf `PROJECT.ui.apps` oder `PROJECT.ui.content` und wählen Sie **Ausführen als** -> **Maven Install**.

Sie haben jetzt einen Zielgruppe-Ordner, der mit Ihrem Paket erstellt wurde (genannt z.B. `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Fehlerbehebung {#troubleshooting}

### Ungültige Projektdefinition beheben {#resolving-invalid-project-definition}

Um ungültige Abhängigkeiten und Projektdefinitionen aufzulösen, gehen Sie wie folgt vor:

1. Wählen Sie alle erstellten Projekte.
1. Kicken Sie mit der rechten Maustaste.
1. Wählen Sie im Kontextmenü **Maven** -> **Projekte aktualisieren**.
1. Aktivieren Sie **Aktualisierungen von Snapshots/Releases erzwingen**.
1. Klicken Sie auf **OK**.

Eclipse lädt die erforderlichen Abhängigkeiten herunter. Das könnte einen Moment dauern.

## Weitere Informationen {#more-information}

Die offizielle Website „Apache Sling IDE tooling for Eclipse“ bietet Ihnen nützliche Informationen:

* Die [**Apache Sling IDE-Werkzeuge für Eclipse** Benutzerhandbuch](https://sling.apache.org/documentation/development/ide-tooling.html), diese Dokumentation führt Sie durch die Gesamtkonzepte, die Serverintegration und die Bereitstellungsfunktionen, die von den AEM Development Tools unterstützt werden.
* Der [Abschnitt zur Fehlerbehebung](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* Die [Liste der bekannten Probleme](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

Die folgende offizielle [Eclipse](https://eclipse.org/)-Dokumentation kann dabei helfen, Ihre Umgebung einzurichten:

* [Erste Schritte mit Eclipse](https://eclipse.org/users/)
* [Eclipse Luna-Hilfesystem](https://help.eclipse.org/luna/index.jsp)
* [Maven-Integration (m2eclipse)](https://www.eclipse.org/m2e/)
