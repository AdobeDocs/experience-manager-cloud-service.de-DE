---
title: AEM Developer Tools for Eclipse
description: AEM Developer Tools für Eclipse
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 100%

---


# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![](assets/eclipse-logo.png)

## Überblick {#overview}

AEM Developer Tools for Eclipse ist ein Eclipse-Plug-in, das auf dem [Eclipse-Plug-in für Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) basiert, das unter der Apache-Lizenz 2 veröffentlicht wurde.

Es bietet mehrere Funktionen, die die AEM-Entwicklung vereinfachen:

* Nahtlose Integration mit AEM-Instanzen über Eclipse Server Connector
* Synchronisierung für Inhalte und OSGI-Bundles
* Debugging-Unterstützung mit Code-Hot-Swapping-Funktion
* Einfacher Bootstrap von AEM-Projekten über einen speziellen Projekterstellungsassistenten
* Einfache Bearbeitung von JCR-Eigenschaften

## Voraussetzungen {#requirements}

Bevor Sie die AEM Developer Tools verwenden, müssen Sie Folgendes tun:

* Downloaden und installieren Sie [Eclipse IDE for Enterprise Java Developers](https://www.eclipse.org/downloads/packages/).
* Konfigurieren Sie Ihre Eclipse-Installation, um sicherzustellen, dass Sie mindestens 1 GB an Heap-Speicher haben, indem Sie Ihre Konfigurationsdatei `eclipse.ini` bearbeiten, wie in den [Eclipse-FAQ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse) beschrieben.

>[!NOTE]
>
>Unter Mac OS X müssen Sie mit der rechten Maustaste auf **Eclipse.app** klicken und dann **Paketinhalt anzeigen** auswählen, um Ihre `eclipse.ini`**zu finden.**

## Installieren der AEM Developer Tools for Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Sobald Sie die oben genannten [Voraussetzungen](#requirements) erfüllt haben, können Sie das Plug-in wie folgt installieren:

1. Durchsuchen Sie die [AEM Developer Tools-Website](https://eclipse.adobe.com/aem/dev-tools/).

1. Kopieren Sie den **Installations-Link**.

   Beachten Sie, dass Sie alternativ ein Archiv herunterladen können, anstatt den Installations-Link zu verwenden. Dies ermöglicht Offlineinstallation, aber Sie werden auf diese Weise automatische Update-Benachrichtigungen verpassen.

1. Öffnen Sie in Eclipse das Menü **Hilfe**.
1. Klicken Sie auf **Neue Software installieren**.
1. Klicken Sie auf **Hinzufügen...**.
1. Geben Sie `AEM Developer Tools` unter **Name** ein.
1. Unter **Standort** kopieren Sie die Installations-URL.
1. Klicken Sie auf **Hinzufügen**.
1. Überprüfen Sie **AEM**- und **Sling**-Plug-ins.
1. Klicken Sie auf **Weiter**.
1. Klicken Sie im Fenster **Installationsdetails** erneut auf **Weiter**.
1. Akzeptieren Sie die Lizenzvereinbarungen und klicken Sie auf **Beenden**.
1. Klicken Sie auf **Jetzt neu starten**, um Eclipse neu zu starten.

## Die AEM-Perspektive {#the-aem-perspective}

In Eclipse bestimmt eine Perspektive die Aktionen und Ansichten, die in einem Fenster verfügbar sind, und ermöglicht eine aufgabenorientierte Interaktion mit Ressourcen in Eclipse. Weitere Informationen zu Perspektiven finden Sie in der [Eclipse-Dokumentation](https://help.eclipse.org).

Die AEM Development Tools for Eclipse enthalten eine AEM-Perspektive, die Ihnen die volle Kontrolle über Ihre AEM-Projekte und -Instanzen bietet. So öffnen Sie die AEM-Perspektive:

1. Wählen Sie in der Eclipse-Menüleiste **Fenster** > **Perspektive** > **Perspektive öffnen** > **Andere** aus.
1. Wählen Sie im Dialogfeld **AEM** aus und klicken Sie auf **Öffnen**.

![Die AEM-Perspektive in Eclipse](assets/eclipse-aem-perspective.png)

## Multi-Modul-Beispielprojekt {#sample-multi-module-project}

Die AEM Developer Tools for Eclipse werden mit einem Beispielprojekt mit mehreren Modulen geliefert, mit dem Sie schnell mit der Projektkonfiguration in Eclipse vertraut werden und das als Best Practice-Leitfaden für mehrere AEM-Funktionen dienen kann. [Erfahren Sie mehr über den Projektarchetyp](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

Führen Sie folgende Schritte aus, um das Beispielprojekt zu erstellen:

1. Im Menü **Datei** > **Neu** > **Projekt** navigieren Sie zum **AEM**-Bereich und wählen Sie **AEM Beispiel-Multi-Modul Projekt**.

   ![AEM-Multi-Modul-Beispielprojekt](assets/aem-sample-project.png)

1. Klicken Sie auf **Weiter**.

   >[!NOTE]
   >
   >Dieser Schritt kann einige Zeit in Anspruch nehmen, da m2eclipse die Archetypkataloge scannen muss.

1. Wählen Sie im Menü `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` aus und klicken Sie dann auf **Weiter**.

   ![Auswählen der Archetypversion ](assets/select-archetype.png)

1. Geben Sie in die folgenden Felder Daten für das Beispielprojekt ein:

   * **Name**
   * **Gruppen-ID**
   * **Artefakt-ID**
   * **appID** – Sie müssen die Optionen unter **Erweitert** erweitern, um diesen Wert festzulegen.
   * **appTitle** – Sie müssen ggf. die Optionen unter **Erweitert** erweitern, um diesen Wert festzulegen.
   * **Package** – Sie müssen die Optionen unter **Erweitert** erweitern, um diesen Wert festzulegen.

   ![Definieren von Archetypeigenschaften](assets/archetype-properties.png)

1. Klicken Sie auf **Weiter**.

1. Sie sollten dann einen AEM-Server konfigurieren, zu dem Eclipse eine Verbindung herstellt.

   Um das Debugger-Feature zu verwenden, müssen Sie AEM im Debug-Modus starten. Dies kann z. B. erreicht werden, indem Sie Folgendes zur Befehlszeile hinzufügen:

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![Herstellen einer Verbindung zum AEM-Server](assets/connect-server.png)

1. Klicken Sie auf **Beenden**. Die Projektstruktur wird erstellt.

   >[!NOTE]
   >
   >Bei einer Neuinstallation (genauer gesagt: wenn die Abhängigkeiten von Maven noch nie heruntergeladen wurden) wird das Projekt möglicherweise mit Fehlern erstellt. In diesem Fall folgen Sie den Anweisungen unter [Ungültige Projektdefinition beheben](#resolving-invalid-project-definition).

## Anleitung zum Importieren vorhandener Projekte {#how-to-import-existing-projects}

Mit der Funktion **Neues Projekt** können Sie die richtige Struktur für Ihre Anforderungen erstellen:

1. Befolgen Sie die Anweisungen, um ein [Multi-Modul-Beispielprojekt](#sample-multi-module-project) zu erstellen. Anschließend werden die folgenden Projekte für Sie erstellt, die eine sinnvolle Trennung der Belange ermöglichen:

   * `PROJECT.ui.apps` für `/apps`- und `/etc`-Inhalte
   * `PROJECT.ui.content` für `/content`, der erstellt wird
   * `PROJECT.core` für Java-Bundles (diese werden relevant, sobald Sie Java-Code hinzufügen möchten)
   * `PROJECT.it.launcher` und `PROJECT.it.tests` für Integrationstests

1. Ersetzen Sie den Inhalt Ihres `PROJECT.ui.apps`-Projekts durch die Ordner `apps` und `etc` Ihres Pakets:

   1. Erweitern Sie im Bedienfeld „Projekt-Explorer“ `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Klicken Sie mit der rechten Maustaste auf den Ordner `apps` und wählen Sie **Anzeigen in** > **System-Explorer** aus.
   1. Löschen Sie die Ordner `apps` und `etc`, die jetzt angezeigt werden sollten, und platzieren Sie hier die Ordner `apps` und `etc` Ihres Inhaltspakets.
   1. Klicken Sie in Eclipse mit der rechten Maustaste auf das Projekt `PROJECT.ui.apps` und wählen Sie **Aktualisieren** aus.

1. Führen Sie dann dasselbe für `PROJECT.ui.content` aus und ersetzen Sie den Inhaltsordner durch den Ordner aus Ihrem Paket:

   1. Erweitern Sie im Bedienfeld „Projekt-Explorer“ `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Klicken Sie mit der rechten Maustaste auf den unteren Inhaltsordner und wählen Sie **Anzeigen in** > **System-Explorer** aus.
   1. Löschen Sie die Inhaltsordner, der jetzt angezeigt werden sollte, und platzieren Sie hier den Inhaltsordner Ihres Inhaltspakets.
   1. Klicken Sie in Eclipse mit der rechten Maustaste auf das Projekt `PROJECT.ui.content` und wählen Sie **Aktualisieren** aus.

1. Jetzt müssen Sie die `filter.xml`-Dateien dieser beiden Projekte aktualisieren, damit sie dem Inhalt Ihres Inhaltspakets entsprechen. Öffnen Sie dazu die Datei `META-INF/vault/filter.xml` Ihres Inhaltspakets in einem gesonderten Text-/Code-Editor.

   * Dies ist ein Beispiel dafür, wie Ihre Datei `filter.xml`aussehen kann:

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

1. Für den Inhalt Ihres Pakets, das in zwei Projekte aufgeteilt wurde, müssen Sie diese Filterregeln ebenfalls in zwei Teile aufteilen und die `filter.xml`-Dateien der beiden Projekte entsprechend aktualisieren.

   1. Öffnen Sie in Eclipse `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. Ersetzen Sie den Inhalt des `<workspaceFilter>`-Elements durch die Regeln Ihres Pakets, die mit `/apps` und `/etc` beginnen.
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
   1. Ersetzen Sie die Regeln durch die Ihres Pakets, die mit `/content` beginnen.
      * Beispiel:

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/content/foo"/>
            <filter root="/content/dam/foo"/>
            <filter root="/content/usergenerated/content/foo"/>
         </workspaceFilter>
         ```


1. Denken Sie daran, alle Änderungen zu speichern. Sie können diesen neuen Inhalt jetzt mit Ihrer AEM-Instanz synchronisieren.

1. Stellen Sie im Bedienfeld „Server“ sicher, dass die Verbindung hergestellt wurde. Andernfalls starten Sie sie.
1. Klicken Sie auf das Symbol **Bereinigen und veröffentlichen**.

Nach Abschluss des Vorgangs sollte das Paket auf Ihrer Instanz ausgeführt werden und beim Speichern werden alle Änderungen automatisch mit der Instanz synchronisiert.

Wenn Sie ein Paket aus Ihrem Projekt neu erstellen möchten, klicken Sie mit der rechten Maustaste auf `PROJECT.ui.apps` oder `PROJECT.ui.content` und wählen Sie **Ausführen als** > **Maven-Installation** aus.

Jetzt verfügen Sie über einen Zielordner, der Ihr Paket enthält (z. B. als `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip` bezeichnet).

## Fehlerbehebung {#troubleshooting}

### Ungültige Projektdefinition beheben {#resolving-invalid-project-definition}

Um ungültige Abhängigkeiten und Projektdefinitionen aufzulösen, gehen Sie wie folgt vor:

1. Wählen Sie alle erstellten Projekte.
1. Klicken Sie mit der rechten Maustaste.
1. Wählen Sie im Kontextmenü **Maven** > **Projekte aktualisieren** aus.
1. Aktivieren Sie **Aktualisierungen von Snapshots/Releases erzwingen**.
1. Klicken Sie auf **OK**.

Eclipse lädt die erforderlichen Abhängigkeiten herunter. Das kann einen Moment dauern.

## Weitere Informationen {#more-information}

Die offizielle Website „Apache Sling IDE tooling for Eclipse“ bietet Ihnen nützliche Informationen:

* Das [**Handbuch zu** Apache Sling IDE tooling for Eclipse](https://sling.apache.org/documentation/development/ide-tooling.html) führt Sie durch die von den AEM-Entwicklungs-Tools unterstützten Konzepte, Serverintegrationen und Implementierungsfunktionen.
* Der [Abschnitt zur Fehlerbehebung](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* Die [Liste der bekannten Probleme](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

Die folgende offizielle [Eclipse](https://eclipse.org/)-Dokumentation kann dabei helfen, Ihre Umgebung einzurichten:

* [Erste Schritte mit Eclipse](https://eclipse.org/users/)
* [Eclipse Luna-Hilfesystem](https://help.eclipse.org/luna/index.jsp)
* [Maven-Integration (m2eclipse)](https://www.eclipse.org/m2e/)
