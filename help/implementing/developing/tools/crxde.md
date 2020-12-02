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
1. Öffnen Sie in Ihrem Browser die URL `https://<host>:<port>/crx/de`.
1. Geben Sie Ihren **Benutzernamen** und Ihr **Kennwort** ein.
1. Klicken Sie auf **OK**.

Die Benutzeroberfläche von CRXDE Lite sieht in Ihrem Browser wie folgt aus:

![Die Benutzeroberfläche &quot;CRXDE Lite&quot;](assets/crxde-lite.png)

Jetzt können Sie CRXDE Lite verwenden, um Ihre Anwendung zu entwickeln.

>[!TIP]
>
>Sie können auch über das AEM Menü auf die CRXDE Lite zugreifen. Wählen Sie im Hauptmenü **Tools** -> **Allgemein** -> **CRXDE Lite**.

## Überblick über die Benutzeroberfläche {#overview-of-the-user-interface}

Die Benutzeroberfläche von CRXDE Lite besteht aus vielen Teilen und hat viele Funktionen.

### Obere Wechselleiste {#top-switcher-bar}

Mit der Leiste &quot;Oberer Switch&quot;können Sie schnell zwischen CRXDE Lite, Package Manager und Package Share wechseln.

### Node Path Widget {#node-path-widget}

Das Node Path Widget zeigt den Pfad zum aktuell ausgewählten Knoten an.

Sie können damit auch zu einem Knoten springen, indem Sie den Pfad manuell eingeben oder von einer anderen Stelle einfügen und die Eingabetaste drücken.

Es bietet auch Unterstützung für die Suche nach Knoten mit bestimmtem Knotennamen. Geben Sie den Namen des Knotens ein, den Sie suchen möchten, und warten Sie (oder wählen Sie das Suchsymbol auf der rechten Seite). Wenn ein oder mehrere Knoten in den Explorer-Bereich geladen werden, wird die Liste angezeigt. Sie können den Pfad auswählen und die Eingabetaste drücken, um zu ihm zu navigieren. Beachten Sie, dass dies nur für die Knoten funktioniert, die derzeit in der CRXDE-Client-Anwendung im Browser geladen sind. Wenn Sie das gesamte Repository durchsuchen möchten, verwenden Sie **Tools** -&amp;gt: **Abfrage**.

### Explorer-Bereich {#explorer-pane}

Das **Explorer-Fenster** zeigt eine Struktur aller Knoten im Repository an.

Klicken Sie auf einen Knoten, um seine Eigenschaften auf der Registerkarte **Eigenschaften** anzuzeigen. Nachdem Sie auf einen Knoten geklickt haben, können Sie eine Aktion in der Symbolleiste auswählen. Klicken Sie erneut auf den Knoten, um ihn umzubenennen.

Mit dem Baumnavigationsfilter (dem Symbol &quot;Ferngläser&quot;) können Sie die Knoten im Repository filtern, für die der Name den Eingabetext enthält. Gilt nur für Knoten, die lokal geladen wurden.

### Bearbeitungsbereich {#edit-pane}

Mit dem Bedienfeld **Bearbeiten** können Sie den Inhalt der aktuell ausgewählten Datei im Repository Ansicht haben. Jede geöffnete Datei wird als eigene Registerkarte im Bereich dargestellt.

Auf der Registerkarte **Home** können Sie nach Inhalten und/oder Dokumentationen suchen und auf die Entwicklerdokumentation und Adobe-Unterstützung zugreifen.

Klicken Sie mit der Dublette auf eine Datei im **Explorer-Bereich**, um deren Inhalt im **Bearbeitungsbereich** anzuzeigen. Anschließend können Sie sie ändern und die Änderungen speichern.

Nachdem eine Datei im Bereich **Bearbeiten** bearbeitet wurde, stehen in der Symbolleiste die folgenden Werkzeuge zur Verfügung:

* **In Baum**  anzeigen: Zeigt die Datei im Repository-Baum an.
* **Suchen/Ersetzen**  - Führt eine Suche oder einen Austausch durch.

Klicken Sie mit der Dublette auf die Statuszeile des **Bearbeitungsbereichs** öffnet das Dialogfeld **Gehe zu Zeile**, damit Sie eine bestimmte Zeilennummer eingeben können.

### Registerkarte „Eigenschaften“ {#properties-tab}

Das Register **Eigenschaften** zeigt die Eigenschaften des ausgewählten Knotens an. Sie können neue Eigenschaften hinzufügen oder die vorhandenen löschen.

### Registerkarte &quot;Zugriffskontrolle&quot; {#access-control-tab}

Die Registerkarte **Zugriffskontrolle** zeigt Berechtigungen basierend auf dem aktuellen Pfad, Repository oder Prinzipal an.

Die Berechtigungen sind in die folgenden Kategorien unterteilt.

* **Anwendbare Richtlinie**  für die Zugriffskontrolle - Die Richtlinien, die auf die aktuelle Auswahl angewendet werden können
* **Lokale Zugriffskontrollen**  - Die aktuellen Richtlinien, die lokal auf die aktuelle Auswahl angewendet werden
* **Richtlinien**  zur effektiven Zugriffskontrolle - Die aktuellen Richtlinien, die für die aktuelle Auswahl gelten und lokal festgelegt oder von übergeordneten Knoten übernommen werden können

>[!NOTE]
Um Informationen zur Zugriffskontrolle anzeigen zu können, muss der bei der CRXDE Lite angemeldete Benutzer über die Rechte zum Lesen von ACL-Einträgen verfügen.

### Replikationsregister {#replication-tab}

Das Register **Replikation** zeigt den Replizierungsstatus des aktuellen Knotens an. Sie können den aktuellen Knoten nachbilden oder nachbilden und löschen.

###  Konsolenregisterkarte {#console-tab}

Auf der Registerkarte **Konsole** werden Protokollmeldungen angezeigt. Sie können die Protokollebene konfigurieren, die Konsole löschen, an der ausgewählten Bildlaufposition anheften und die Anzeige von Meldungen aktivieren/deaktivieren.

### Registerkarte &quot;Build Info&quot;{#build-info-tab}

Die Registerkarte **Build Info** zeigt Informationen an, wenn ein Bundle erstellt wird.

### Schaltfläche {#refresh-button} aktualisieren

Die Schaltfläche **Aktualisieren** aktualisiert die aktuelle Auswahl. Änderungen von anderen Benutzern werden in Ihrer Ansicht des Repositorys aktualisiert. Änderungen, die Sie vorgenommen haben, sind nicht betroffen.

### Alle speichern-Schaltfläche {#save-all-button}

Die Schaltfläche **Alle speichern** speichert alle vorgenommenen Änderungen. Bis Sie sich zum Speichern entscheiden, sind die Änderungen temporär und gehen verloren, wenn Sie die Konsole verlassen.

* **Zurückkehren** : Verwirft alle Änderungen, die Sie seit der letzten Speicheraktion an dem ausgewählten Knoten vorgenommen haben, und lädt dann den aktuellen Status des Repository für den ausgewählten Knoten neu
* **Alle**  wiederherstellen: Verwirft alle Änderungen, die Sie seit der letzten Speicheraktion im gesamten Repository vorgenommen haben, und lädt dann den aktuellen Status des Repositorys neu

### Schaltfläche „Erstellen“{#create-button}

Die Schaltfläche &quot;Erstellen&quot;**ist ein Dropdown-Menü, um unter dem ausgewählten Knoten Folgendes zu erstellen:**

* Knoten - ein Knoten mit einem beliebigen Knotentyp
* Datei - ein `nt:file`-Knoten und der zugehörige nt:resource-Unterknoten
* Ordner - ein `nt:folder`-Knoten

### Schaltfläche {#delete-button} löschen

Die Schaltfläche **Löschen** löscht die ausgewählte Node.

### Schaltfläche &quot;Kopieren&quot; {#copy-button}

Die **Schaltfläche Kopieren** kopiert die ausgewählte Node.

## Einfügen-Schaltfläche {#paste-button}

Die Schaltfläche **Einfügen** fügt den kopierten Knoten unter den ausgewählten Knoten ein.

### Schaltfläche {#move-button}

Die Schaltfläche **Verschieben** verschiebt den ausgewählten Knoten zu dem Knoten, der durch das Dialogfeld festgelegt wird.

### Umbenennen {#rename-button}

Die **Umbenennen-Schaltfläche** benennt den ausgewählten Knoten um.

### Mixins {#mixins-button}

Mit der **Mixins-Schaltfläche** können Sie Mixin-Typen zum Node-Typ hinzufügen. Die Mixin-Typen werden meist verwendet, um erweiterte Funktionen hinzuzufügen.

### Tools {#tools-button}

Die Schaltfläche **Tools** ist ein Dropdown-Menü mit den folgenden verfügbaren Tools:

* **Serverkonfiguration**  - Zugriff auf die Felix-Konsole (auch verfügbar unter  `https://<host>:<port>/system/console/configMgr`)
* **Abfrage** - zur Abfrage des Repositorys
* **Berechtigungen**  - zur Ansicht und zum Hinzufügen von Berechtigungen
* **Testen der Zugriffskontrolle** : Testen der Berechtigung für bestimmte Pfade und/oder Prinzipale
* **Knotentyp**  exportieren - um Knotentypen im System als CND-Notation zu exportieren
* **Node Type**  importieren - um Node-Typen mithilfe der CND-Notation zu importieren.

### Anmelde-Widget {#login-widget}

Das **Anmelde-Widget** zeigt den derzeit angemeldeten Benutzer an.

Klicken Sie darauf, um sich als ein anderer Benutzer anzumelden oder sich erneut anzumelden. `@crx.default` bedeutet, dass Sie sich im Standard-Arbeitsbereich (und nur) im Repository befinden.

Die Option **Voreinstellungen** kann verwendet werden, um die Benutzeroberflächensprache festzulegen und die Hotkeys für verschiedene Aktionen wie Speichern, Suchen, Erstellen von Notizen usw. Ansicht und anzupassen.

## Erstellen eines Ordners {#creating-a-folder}

So erstellen Sie einen Ordner mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsbereich mit der rechten Maustaste auf den Ordner, unter dem Sie den neuen Ordner erstellen möchten, und wählen Sie **Erstellen ...**, dann **Ordner erstellen ...**.

1. Geben Sie den **Namen** des Ordners ein und klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

## Erstellen eines Knotens {#creating-a-node}

So erstellen Sie einen Knoten mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Bereich [**Exploerer**,](#explorer-pane) mit der rechten Maustaste auf den Knoten, auf dem Sie den neuen Knoten erstellen möchten, wählen Sie **Erstellen** und dann **Knoten erstellen**.
1. Geben Sie **Name** ein und wählen Sie **Typ**.
1. Klicken Sie auf **OK**.
1. Klicken Sie auf die Schaltfläche [**Alle speichern**](#save-all-button), um die Änderungen auf dem Server zu speichern.

Jetzt können Sie den Knoten an Ihre Anforderungen anpassen, indem Sie die Eigenschaften ändern oder neue Knoten erstellen.

>[!NOTE]
Bei den meisten Bearbeitungsvorgängen, einschließlich **Knoten erstellen**, werden alle Änderungen im Arbeitsspeicher gespeichert und nur beim Speichern (unter Verwendung der Schaltfläche [**Alle speichern**](#save-all-button)) im Repository gespeichert. Einige Vorgänge wie Verschieben werden jedoch automatisch beibehalten.
Die Überprüfung, ob der neu erstellte Knoten vom Knotentyp des übergeordneten Knotens zugelassen ist, wird auch vom Repository beim Speichern von Änderungen durchgeführt. Wenn Sie beim Speichern einer Node eine Fehlermeldung erhalten, überprüfen Sie bitte, ob die Inhaltsstruktur gültig ist (z. B. können Sie keine `nt:unstructured`-Node als untergeordnetes Element der `nt:folder`-Node erstellen).

## Erstellen einer Eigenschaft {#creating-a-property}

So erstellen Sie eine Eigenschaft mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie im Bereich [**Exploerer**](#explorer-pane) den Knoten aus, dem Sie die neue Eigenschaft hinzufügen möchten.
1. Geben Sie im unteren Bereich unter der Registerkarte [**Eigenschaften**](#properties-tab) die Variablen **Name**, **Typ** und **Wert** ein.
1. Klicken Sie auf **Hinzufügen**.
1. Klicken Sie auf die Schaltfläche [**Alle speichern**](#save-all-button), um die Änderungen auf dem Server zu speichern.

## Erstellen einer Datei {#creating-a-file}

So erstellen Sie eine neue Datei mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Bereich [**Exploerer**,](#explorer-pane) mit der rechten Maustaste auf die Komponente, in der Sie die Datei erstellen möchten, wählen Sie **Erstellen** und dann **Datei erstellen**.
1. Geben Sie die Datei **Name** einschließlich der Erweiterung ein.
1. Klicken Sie auf **OK**.
1. Die neue Datei wird als Registerkarte im Bereich [**Bearbeiten** geöffnet.](#edit-pane)
1. Bearbeiten Sie die Datei.
1. Klicken Sie auf die Schaltfläche [**Alle speichern**](#save-all-button), um die Änderungen zu speichern.

## Exportieren und Importieren von Knotentypen {#exporting-and-importing-node-types}

Mit der CRXDE Lite können Sie Knotentypdefinitionen in [Compact Namensraum and Node Type Definition (CND) Node](https://jackrabbit.apache.org/jcr/node-type-notation.html) importieren und/oder exportieren.

So exportieren Sie eine Knotentypdefinition in CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie Ihren gewünschten Knoten aus.
1. Wählen Sie **Tools** und dann **Knotentyp exportieren**.
1. Die Definition wird in der CND-Notation in einer neuen Registerkarte in Ihrem Browser angezeigt.
1. Speichern Sie die Informationen (falls erforderlich).

So importieren Sie eine Knotentypdefinition:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie **Tools** und dann **Knotentyp importieren**.
1. Eine neue Registerkarte wird im Bereich [**Bearbeiten**](#edit-pane) mit der Bezeichnung **Knotentyp importieren** geöffnet.
1. Geben Sie die CND-Notation für die Definition in das Textfeld der Registerkarte **Node-Typ importieren** ein.
1. Aktivieren Sie **Aktualisierung zulassen**, wenn Sie eine vorhandene Definition aktualisieren.
1. Wählen Sie **Importieren**.

## Protokollierung {#logging}

Mit der CRXDE Lite können Sie die Datei `error.log` anzeigen, die sich im Dateisystem unter `<aem-install-dir>/crx-quickstart/logs` befindet, und sie mit der entsprechenden Protokollierungsstufe filtern. Gehen Sie wie folgt vor:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie im Dropdown-Menü rechts neben der Registerkarte [**Konsole**](#console-tab) unten im Fenster **Serverprotokolle**.
1. Klicken Sie auf das **Stopp-Symbol**, um die Nachrichten anzuzeigen.

Sie haben folgende Möglichkeiten:

* Passen Sie die Protokollparameter in der Felix-Konsole an, indem Sie auf das Symbol **Protokollierungskonfigurationen** klicken.
* Löschen Sie die Meldungen, indem Sie auf das Symbol **Konsole löschen** klicken.
* Veröffentlichen Sie die Nachricht an der aktuellen Auswahl, indem Sie auf das Symbol **Pin Console** klicken.
* Aktivieren oder deaktivieren Sie die Anzeige von Meldungen, indem Sie auf das **Stopp-Symbol** klicken.
