---
title: 'Verwenden von CRXDE Lite '
description: CRXDE Lite ist Teil des AEM Schnellstarts und steht Ihnen zur Verfügung, um auf das Repository in Ihren lokalen Entwicklungs-Umgebung im Browser zuzugreifen und es zu ändern.
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 21%

---


# Verwenden von CRXDE Lite  {#using-crxde-lite}

CRXDE Lite ist Teil des AEM Schnellstarts und steht Ihnen zur Verfügung, um auf das Repository in Ihren lokalen Entwicklungs-Umgebung im Browser zuzugreifen und es zu ändern. Mit der CRXDE Lite können Sie Dateien, Ordner, Knoten und Eigenschaften bearbeiten. Das gesamte Repository steht Ihnen in dieser benutzerfreundlichen Oberfläche zur Verfügung.

>[!NOTE]
>
>CRXDE Lite ist nur in Ihren Umgebung verfügbar. Es ist nicht als Cloud Service in AEM verfügbar.

## Erste Schritte mit CRXDE Lite {#getting-started-with-crxde-lite}

Erste Schritte mit der CRXDE Lite:

1. Beginn deinen örtlichen AEM Development Schnellstart.
1. In your browser, open the URL `https://<host>:<port>/crx/de`.
1. Geben Sie Ihren **Benutzernamen** und Ihr **Kennwort** ein.
1. Klicken Sie auf **OK**.

Die Benutzeroberfläche von CRXDE Lite sieht in Ihrem Browser wie folgt aus:

![Die Benutzeroberfläche &quot;CRXDE Lite&quot;](assets/crxde-lite.png)

Jetzt können Sie CRXDE Lite verwenden, um Ihre Anwendung zu entwickeln.

>[!TIP]
>
>Sie können auch über das AEM Menü auf die CRXDE Lite zugreifen. Wählen Sie im Hauptmenü **Extras** -> **Allgemein** -> **CRXDE Lite**.

## Überblick über die Benutzeroberfläche {#overview-of-the-user-interface}

Die Benutzeroberfläche von CRXDE Lite besteht aus vielen Teilen und hat viele Funktionen.

### Obere Wechselleiste {#top-switcher-bar}

Mit der Leiste &quot;Oberer Switch&quot;können Sie schnell zwischen CRXDE Lite, Package Manager und Package Share wechseln.

### Node Path Widget {#node-path-widget}

Das Node Path Widget zeigt den Pfad zum aktuell ausgewählten Knoten an.

Sie können damit auch zu einem Knoten springen, indem Sie den Pfad manuell eingeben oder von einer anderen Stelle einfügen und die Eingabetaste drücken.

Es bietet auch Unterstützung für die Suche nach Knoten mit bestimmtem Knotennamen. Geben Sie den Namen des Knotens ein, den Sie suchen möchten, und warten Sie (oder wählen Sie das Suchsymbol auf der rechten Seite). Wenn ein oder mehrere Knoten in den Explorer-Bereich geladen werden, wird die Liste angezeigt. Sie können den Pfad auswählen und die Eingabetaste drücken, um zu ihm zu navigieren. Beachten Sie, dass dies nur für die Knoten funktioniert, die derzeit in der CRXDE-Client-Anwendung im Browser geladen sind. If you want to search the whole repository, use **Tools** -&amp;gt: **Query**.

### Explorer Pane {#explorer-pane}

Im **Explorer-Bereich** wird eine Struktur aller Knoten im Repository angezeigt.

Klicken Sie auf einen Knoten, um seine Eigenschaften auf der Registerkarte **Eigenschaften** anzuzeigen. Nachdem Sie auf einen Knoten geklickt haben, können Sie eine Aktion in der Symbolleiste auswählen. Klicken Sie erneut auf den Knoten, um ihn umzubenennen.

Mit dem Baumnavigationsfilter (dem Symbol &quot;Ferngläser&quot;) können Sie die Knoten im Repository filtern, für die der Name den Eingabetext enthält. Gilt nur für Knoten, die lokal geladen wurden.

### Edit Pane {#edit-pane}

Der **Bearbeitungsbereich** ermöglicht die Ansicht des Inhalts der aktuell ausgewählten Datei im Repository. Jede geöffnete Datei wird als eigene Registerkarte im Bereich dargestellt.

Auf der Registerkarte &quot; **Startseite** &quot;können Sie nach Inhalten und/oder Dokumentationen suchen und auf die Entwicklerdokumentation und Adobe zugreifen.

Klicken Sie mit der Dublette auf eine Datei im **Explorer-Bereich** , um deren Inhalt im **Bearbeitungsbereich** anzuzeigen. Anschließend können Sie sie ändern und die Änderungen speichern.

Once a file is edited in the **Edit Pane**, the following tools are available on the toolbar:

* **In Struktur** anzeigen: Zeigt die Datei im Repository-Baum an.
* **Suchen/Ersetzen** - Führt eine Suche oder einen Austausch durch.

Double-click on the status line of the **Edit Pane** opens the **Go to line** dialog so you can enter a specific line number.

### Registerkarte „Eigenschaften“ {#properties-tab}

Auf der Registerkarte &quot; **Eigenschaften&quot;** werden die Eigenschaften des ausgewählten Knotens angezeigt. Sie können neue Eigenschaften hinzufügen oder die vorhandenen löschen.

### Access Control Tab {#access-control-tab}

Auf der Registerkarte &quot; **Zugriffskontrolle&quot;** werden Berechtigungen basierend auf dem aktuellen Pfad, Repository oder Prinzipal angezeigt.

Die Berechtigungen sind in die folgenden Kategorien unterteilt.

* **Anwendbare Richtlinie** zur Zugriffskontrolle - Richtlinien, die auf die aktuelle Auswahl angewendet werden können
* **Lokale Zugriffskontrollen** - Die aktuellen Richtlinien, die lokal auf die aktuelle Auswahl angewendet werden
* **Richtlinien** zur effektiven Zugriffskontrolle - Die aktuellen Richtlinien, die für die aktuelle Auswahl gelten und lokal festgelegt oder von übergeordneten Knoten übernommen werden können

>[!NOTE]
Um Informationen zur Zugriffskontrolle anzeigen zu können, muss der bei der CRXDE Lite angemeldete Benutzer über die Rechte zum Lesen von ACL-Einträgen verfügen.

### Replication Tab {#replication-tab}

Auf der Registerkarte &quot; **Replikation&quot;** wird der Replikationsstatus des aktuellen Knotens angezeigt. Sie können den aktuellen Knoten nachbilden oder nachbilden und löschen.

###  Console Tab {#console-tab}

Auf der Registerkarte &quot; **Konsole&quot;** werden Meldungen angezeigt. Sie können die Protokollebene konfigurieren, die Konsole löschen, an der ausgewählten Bildlaufposition anheften und die Anzeige von Meldungen aktivieren/deaktivieren.

### Build Info Tab {#build-info-tab}

Auf der Registerkarte &quot; **Build Info&quot;** werden Informationen angezeigt, wenn ein Bundle erstellt wird.

### Schaltfläche &quot;Aktualisieren&quot; {#refresh-button}

Über die Schaltfläche &quot; **Aktualisieren&quot;** wird die aktuelle Auswahl aktualisiert. Änderungen von anderen Benutzern werden in Ihrer Ansicht des Repositorys aktualisiert. Änderungen, die Sie vorgenommen haben, sind nicht betroffen.

### Schaltfläche &quot;Alle speichern&quot; {#save-all-button}

Die Schaltfläche &quot;Alle **speichern&quot;** speichert alle Änderungen, die Sie vorgenommen haben. Bis Sie sich zum Speichern entscheiden, sind die Änderungen temporär und gehen verloren, wenn Sie die Konsole verlassen.

* **Zurückkehren** - Verwirft alle Änderungen, die Sie seit der letzten Speicheraktion an dem ausgewählten Knoten vorgenommen haben, und lädt dann den aktuellen Status des Repository für den ausgewählten Knoten neu
* **Alle** wiederherstellen: Verwirft alle Änderungen, die Sie seit der letzten Speicheraktion im gesamten Repository vorgenommen haben, und lädt dann den aktuellen Status des Repository neu

### Schaltfläche „Erstellen“{#create-button}

Die Schaltfläche **Erstellen** ist ein Dropdown-Menü, um unter dem ausgewählten Knoten Folgendes zu erstellen:

* Knoten - ein Knoten mit einem beliebigen Knotentyp
* Datei - ein `nt:file` Knoten und dessen Unterknoten nt:resource
* Ordner - ein `nt:folder` Knoten

### Delete Button {#delete-button}

Die **Schaltfläche** &quot;Löschen&quot;löscht die ausgewählte Node.

### Copy Button {#copy-button}

Die **Schaltfläche** &quot;Kopieren&quot;kopiert die ausgewählte Node.

## Paste Button {#paste-button}

Mit der **Schaltfläche** &quot;Einfügen&quot;wird der kopierte Knoten unter dem ausgewählten Knoten eingefügt.

### Move Button {#move-button}

The **Move Button** moves the selected node to the node that is set through the dialog.

### Umbenennen {#rename-button}

Die Schaltfläche &quot; **Umbenennen&quot;** benennt die ausgewählte Node um.

### Mixins {#mixins-button}

Mit der **Mixins-Schaltfläche** können Sie Mixin-Typen zum Knotentyp hinzufügen. Die Mixin-Typen werden meist verwendet, um erweiterte Funktionen hinzuzufügen.

### Tools {#tools-button}

Die Schaltfläche **Tools** ist ein Dropdown-Menü mit den folgenden verfügbaren Tools:

* **Serverkonfiguration** - Zugriff auf die Felix-Konsole (auch unter `https://<host>:<port>/system/console/configMgr`)
* **Abfrage** - zur Abfrage des Repositorys
* **Berechtigungen** - zur Ansicht und zum Hinzufügen von Berechtigungen
* **Zugriffskontrolle** testen - Testen der Berechtigung für bestimmte Pfade und/oder Prinzipale
* **Knotentyp** exportieren - um Knotentypen im System als CND-Notation zu exportieren
* **Node Type** importieren - zum Importieren von Node-Typen mithilfe der CND-Notation.

### Login Widget {#login-widget}

Das **Anmelde-Widget** zeigt den derzeit angemeldeten Benutzer an.

Klicken Sie darauf, um sich als ein anderer Benutzer anzumelden oder sich erneut anzumelden. Der `@crx.default` stellt dar, dass Sie sich im Standardarbeitsbereich (und nur) im Repository befinden.

Mit der Option **Voreinstellungen** können Sie Ihre Benutzeroberflächensprache festlegen, die Hotkeys für verschiedene Aktionen wie Speichern, Suchen, Erstellen von Notizen usw. Ansicht und anpassen.

## Erstellen eines Ordners {#creating-a-folder}

So erstellen Sie einen Ordner mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. In the Navigation pane, right-click the folder under which you want to create the new folder, select **Create ...**, then **Create Folder ...**.

1. Geben Sie den **Namen** des Ordners ein und klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

## Erstellen eines Knotens {#creating-a-node}

So erstellen Sie einen Knoten mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. In the [**Exploerer Pane**,](#explorer-pane) right-click the node where you want to create the new node, select **Create**, then **Create Node**.
1. Enter the **Name** and select the **Type**.
1. Klicken Sie auf **OK**.
1. Click the [**Save All Button**](#save-all-button) to save the changes on the server.

Jetzt können Sie den Knoten an Ihre Anforderungen anpassen, indem Sie die Eigenschaften ändern oder neue Knoten erstellen.

>[!NOTE]
Most of the edit operations, including **Create Node**, keeps all the changes in memory, and only stores them in the repository upon saving (using the [**Save All Button**](#save-all-button)). Einige Vorgänge wie Verschieben werden jedoch automatisch beibehalten.
Die Überprüfung, ob der neu erstellte Knoten vom Knotentyp des übergeordneten Knotens zugelassen ist, wird auch vom Repository beim Speichern von Änderungen durchgeführt. If you receive an error message while saving a node, please check if the content structure is valid (e.g. you cannot create an `nt:unstructured` node as a child of `nt:folder` node).

## Erstellen einer Eigenschaft {#creating-a-property}

So erstellen Sie eine Eigenschaft mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. In the [**Exploerer Pane**,](#explorer-pane) select the node where you want to add the new property.
1. In the [**Properties Tab**](#properties-tab) in the bottom pane, enter the **Name**, the **Type**, and the **Value**.
1. Klicken Sie auf **Hinzufügen**.
1. Click the [**Save All Button**](#save-all-button) to save the changes on the server.

## Erstellen einer Datei {#creating-a-file}

So erstellen Sie eine neue Datei mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. In the [**Exploerer Pane**,](#explorer-pane) right-click the component where you want to create the file, select **Create**, then **Create File**.
1. Enter the file **Name** including its extension.
1. Klicken Sie auf **OK**.
1. The new file opens as a tab in the [**Edit Pane**.](#edit-pane)
1. Bearbeiten Sie die Datei.
1. Click the [**Save All Button**](#save-all-button) to save the changes.

## Exportieren und Importieren von Knotentypen {#exporting-and-importing-node-types}

With CRXDE Lite you can import and/or export node type definitions in [Compact Namespace and Node Type Definition (CND) notation](https://jackrabbit.apache.org/jcr/node-type-notation.html).

So exportieren Sie eine Knotentypdefinition in CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie Ihren gewünschten Knoten aus.
1. Wählen Sie **Tools** und dann **Knotentyp exportieren**.
1. Die Definition wird in der CND-Notation in einer neuen Registerkarte in Ihrem Browser angezeigt.
1. Speichern Sie die Informationen (falls erforderlich).

So importieren Sie eine Knotentypdefinition:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie **Tools** und dann **Knotentyp importieren**.
1. Eine neue Registerkarte wird im Bereich [**&quot;Bearbeiten&quot;**](#edit-pane) mit der Bezeichnung &quot; **Knotentyp** importieren&quot;geöffnet.
1. Geben Sie die CND-Notation für die Definition in das Textfeld der Registerkarte &quot; **Knotentyp** importieren&quot;ein.
1. Aktivieren Sie **Aktualisierung zulassen**, wenn Sie eine vorhandene Definition aktualisieren.
1. Wählen Sie **Importieren**.

## Protokollierung {#logging}

With CRXDE Lite you can display the file `error.log` that is located on the file system at `<aem-install-dir>/crx-quickstart/logs` and filter it with the appropriate log level. Gehen Sie wie folgt vor:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie im Dropdown-Menü rechts neben der Registerkarte &quot; [**Konsole&quot;**](#console-tab) unten im Fenster die Option &quot; **Serverprotokolle**&quot;aus.
1. Klicken Sie auf das **Stopp-Symbol**, um die Nachrichten anzuzeigen.

Sie haben folgende Möglichkeiten:

* Adjust the log parameters in the Felix Console by clicking the **Logging Configurations** icon.
* Clear the messages by clicking the **Clear Console** icon.
* Pin the message at the current selection by clicking the **Pin Console** icon.
* Aktivieren oder deaktivieren Sie die Anzeige von Meldungen, indem Sie auf das **Stopp-Symbol** klicken.
