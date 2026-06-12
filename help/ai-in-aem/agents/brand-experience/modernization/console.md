---
title: Experience Modernization Console
description: Referenzhandbuch für die Benutzeroberfläche und die Funktionen der Experience Modernization Console
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 43d8c124-fc87-4cec-a91d-ab12255ae321
source-git-commit: c80a2ad29839eaf4d8ad940f9a90d8575e5230f1
workflow-type: tm+mt
source-wordcount: '1332'
ht-degree: 0%

---


# Experience Modernization Console {#console-reference}

Referenzhandbuch für die Benutzeroberfläche und die Funktionen der Experience Modernization Console

>[!NOTE]
>
>Wenn Sie an der Verwendung der Experience Modernization Console interessiert sind, können Sie Zugriff anfordern, um ein reibungsloses Onboarding-Erlebnis zu gewährleisten.

## Überblick {#overview}

Die Experience Modernization Console ist eine gehostete, KI-unterstützte Entwicklungsumgebung für Edge Delivery Services, die als Web-Oberfläche unter [`aemcoder.adobe.io`.](https://aemcoder.adobe.io) Nachdem Sie eine Verbindung zu ihrem GitHub-Projekt hergestellt haben, können Sie sofort damit beginnen, Änderungen in natürlicher Sprache einzufordern, ohne dass Sie eine weitere Einrichtung oder lokale Umgebungskonfiguration benötigen.

>[!TIP]
>
>Wenn Sie daran interessiert sind, sofort mit der Konsole zu beginnen, lesen Sie das Dokument [Erste Schritte mit dem Experience Modernization Agent“](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md)

## Funktionen {#capabilities}

Kernfunktionen der Konsole:

* Interaktives Chat-Panel mit dem Agenten und seinen Fähigkeiten
* Live AEM-Vorschau für sofortiges visuelles Feedback zu Änderungen
* Inhaltsdatei-Browser und Markdown-Viewer
* Inhaltssynchronisierung mit [Dokumenterstellung](https://da.live)
* Code-Browser und Vergleichsansicht zur Überprüfung von vorgenommenen Änderungen
* GitHub-Integration mit der Möglichkeit, Pull-Anforderungen aus Änderungen zu erstellen

Die Entwickler behalten die volle Kontrolle darüber, was ausgeliefert wird. Alle über die Konsole vorgenommenen Änderungen müssen vor der Bereitstellung überprüft und genehmigt werden, um Governance, Markenkonsistenz und Sicherheit sicherzustellen.

## Navigation {#navigation}

Nach der Anmeldung bei der Konsole [aemcoder.adobe.io](https://aemcoder.adobe.io) gelangen Sie zur [Startseite](#home-page) der Konsole. Sobald Sie mit dem Chat begonnen haben, gelangen Sie bei nachfolgenden Besuchen [ Experience Modernization Agent direkt ](#chat-page) die Chat-Seite.

![Startbildschirm der Konsole](assets/console-home.png)

### Menüleiste {#menu-bar}

Die obere Menüleiste bietet:

* Ein **Adobe Experience Manager**-Titel auf der linken Seite, der beim Klicken auf die Startseite mit einem Link verbunden ist
* Eine Schaltfläche **Support anfordern** über die Sie Details zu allen aufgetretenen Problemen senden können
* Eine **Konto**-Schaltfläche auf der rechten Seite, mit der Sie in den Dunkelmodus wechseln und die Konsole abmelden können

## Startseite {#home-page}

Die **Startseite** ist Ihr Ausgangspunkt für die Verwendung der Konsole.

* Oben befindet sich eine [Eingabeaufforderung](#prompt-input) für Anfragen an die Konsole.
* Unter dem Eingabeaufforderungsbedienfeld finden Sie die empfohlenen Eingabeaufforderungen für den Einstieg in Ihr Projekt.
* Ein **Chat starten** Button, der Sie zur [Chatseite](#chat-page) bringt.
* Eine Schaltfläche **Einstellungen**, um auf die Seite [Projekteinstellungen](#settings-page) zuzugreifen

### Eingabeaufforderung {#prompt-input}

Die Eingabeaufforderung enthält Steuerelemente für die Interaktion mit der KI.

* **Plan-/Ausführungsmodi** (Glühbirnen- und Zauberstabsymbole): Wechseln zwischen Planungs- und Ausführungsmodi
   * **Planmodus**: Die KI analysiert Anfragen und umreißt einen Ansatz, ohne Änderungen vorzunehmen. Dies ist nützlich, um die Strategie vor der Zusage zu verstehen.
   * **Ausführungsmodus**: Die KI führt den Plan aus und nimmt die eigentlichen Dateiänderungen vor.
* **Dateien anhängen** (Papierklammer-Symbol): Laden Sie Dateien hoch und fügen Sie sie an die Eingabeaufforderung für zusätzlichen Kontext (z. B. Referenzdesigns, Screenshots, Spezifikationen) an
* **Eingabeaufforderungswarteschlange** (Uhrensymbol): Zusätzliche Eingabeaufforderungen können in die Warteschlange gestellt werden, um automatisch ausgeführt zu werden, sobald die aktuelle Eingabeaufforderung abgeschlossen ist.

## Chat-Seite {#chat-page}

Die [**Chat** Seite](https://aemcoder.adobe.io/chat) ist die Hauptbenutzeroberfläche für die Interaktion mit dem Experience Modernization Agent. Diese Seite ist in ein in der Größe veränderbares [Chat-Bedienfeld](#chat-panel) und [Arbeitsbereich-Bedienfeld.](#workspace-panel)

## Chat-Bedienfeld {#chat-panel}

Im Chat-Panel können Sie Ihre Unterhaltung mit dem Experience Modernization Agent anzeigen und fortsetzen. Das Chatbedienfeld enthält den Chatnachrichtenverlauf und eine [Eingabeaufforderung](#prompt-input) um zusätzliche Anfragen an die Konsole zu stellen.

Die Kopfzeile des Chat-Panels enthält Links zum Navigieren zur [Startseite](#home-page) und [Einstellungen](#settings-page) Ansichten und Chat-Aktionen.

* **Chat-Aktionen**
   * **Chat löschen**: Setzt die Konversation zurück und löscht das Kontextfenster der KI. Verwenden Sie diese Option, wenn eine neue Aufgabe gestartet wird, die in keinem Zusammenhang mit der vorherigen Unterhaltung steht.
   * **Chat herunterladen**: Dadurch wird der Unterhaltungsverlauf als Markdown-Datei heruntergeladen.

## Workspace Panel {#workspace-panel}

Im Arbeitsbereich-Bedienfeld werden der gesamte Inhalt und der Code für Ihre Site angezeigt. Die Kopfzeile am oberen Rand des Bedienfelds enthält eine Auswahl, um die spezifische Ansicht auszuwählen, auf die Sie sich konzentrieren möchten. Die in der Workspace-Kopfzeile verfügbaren Aktionen ändern sich je nach der aktuell ausgewählten Ansicht.

### Inhaltsansichten {#content-view}

Die **Inhaltsansichten** enthalten mehrere Modi zum Anzeigen des ausgewählten Seiteninhalts. Ein ausblendbarer Dateibrowser zeigt alle verfügbaren Seiteninhalte für Ihre Site an.

* **Vorschau** (Dokument mit Lupensymbol), um den gerenderten HTML-Inhalt anzuzeigen
* **Dokumentansicht** (Dokumentsymbol) zum Anzeigen der zugrunde liegenden Inhaltsstruktur für die Dokumenterstellung
* **HTML-Ansicht** (Code-Symbol) zum Anzeigen von unformatiertem HTML-Code
* **Markdown-Ansicht (AEM-Authoring)** (Absatzsymbol) zum Anzeigen der zugrunde liegenden Markdown-Inhaltsstruktur
* **JCR XML-Ansicht (AEM Authoring)** (Datensymbol) zum Anzeigen der resultierenden JCR XML-Inhaltsstruktur

![Inhaltsansicht](assets/content-imported.png)

Die folgenden Aktionen sind in den Inhaltsansichten verfügbar:

* **Aktualisieren**-Symbol zum Aktualisieren des Renderings des Vorschaubereichs.
* **Responsiver Modus**, um den gerenderten HTML-Inhalt in einer Desktop-, Tablet- oder Mobilansicht anzuzeigen
* **Prüfmodus** (Auswahlsymbol), um Elemente der Seite zu Ihrer Eingabeaufforderung für zusätzlichen Kontext hinzuzufügen
* **Neues Fenster** (Symbol „Öffnen in„) zum Öffnen der Vorschau-URL in einer neuen Registerkarte (für eine vollständige Desktop-Vorschau)
* **Löschen** entfernt die ausgewählte Seite aus dem Arbeitsbereich. Vorschau oder veröffentlichte Inhalte werden nicht gelöscht.
* **Fehler**-Schaltfläche (AEM Authoring) öffnet ein modales Fenster, in dem die Fehler auf der ausgewählten Seite angezeigt werden.
* **Inhalt hochladen** wird ein modales Fenster zum Hochladen von Dateien in AEM geöffnet.

![Inhalt hochladen](assets/upload-content.png)

### Code-Ansichten {#code-view}

Der **Codeansichten** bietet Tools zum Durchsuchen Ihrer Projektdateien und zum Verwalten von Codeänderungen. Die Ansicht enthält einen Datei-Browser mit einer Übersicht über Ihre Codedateien oder Änderungen als Unterschiede sowie einen Vorschaubereich zum Anzeigen der ausgewählten Datei oder Änderungen.

* **Dateien**, um die Codedateien im aktuellen Arbeitsbereich zu durchsuchen
* **Änderungen**, um die Unterschiede der durch Ihre Arbeit am Projekt erstellten Dateiänderungen anzuzeigen

![Code-Ansicht](assets/code-view.png)

#### Dateiaktionen {#file-actions}

* **Zum Chat hinzufügen** fügt die ausgewählte Datei (oder die ausgewählten Zeilen aus der Datei) dem Chat-Bedienfeld für den Kontext hinzu.
* **Herunterladen** Laden Sie die ausgewählte Datei auf Ihr lokales Dateisystem herunter

#### Aktionen für Änderungen {#changes-actions}

* **Hinzufügen** (+-Symbol) zum Staging der geänderten Datei
* **Verwerfen** (Pfeilsymbol) zum Verwerfen der geänderten Datei
* **Löschen** (Papierkorbsymbol) zum Löschen der nicht bereitgestellten Datei
* **Aktualisieren** (Aktualisierungssymbol), um die Liste der Änderungen zu aktualisieren
* **Verzweigung wechseln**: Wechselt Verzweigungen innerhalb desselben Repositorys
* **Synchronisieren**: Ruft die neuesten Änderungen von der Remote-Quelle ab.
* **Push**: Öffnet ein Modal, um Änderungen am Arbeitsbereich auf GitHub zu übertragen

Beim Pushen von Änderungen müssen Sie zunächst gestaffelte Änderungen in die Push-Benachrichtigung aufnehmen. Beim Pushen können Sie eine neue PR erstellen oder direkt zur aktuellen Verzweigung pushen

![Änderungen per Push übertragen](assets/push-changes.png)

Weitere GitHub-Projektaktionen können auf der Seite [Einstellungen“ ](#settings-page) werden.

## Einstellungsseite {#settings-page}

Die [**Einstellungen** ermöglicht ](https://aemcoder.adobe.io/settings) Verwaltung der grundlegenden Einstellungen der Konsole und ist in die folgenden Abschnitte unterteilt.

![Einstellungsansicht](assets/settings-view.png)

Wenn Sie einen Wert in einem der Abschnitte ändern, klicken Sie auf **Speichern**, um diese Änderungen im jeweiligen Abschnitt zu speichern. Klicken Sie auf das Symbol Zurück , um zur vorherigen Ansicht zurückzukehren.

* **Projekt** ermöglicht Ihnen das Anzeigen und Bearbeiten von Projekteinstellungen, wie z. B. das Verwalten Ihrer GitHub-Verbindung und das Anpassen der Bibliotheks-URL.
   * **Verbinden/Erneut verbinden**: Startet die GitHub-Authentifizierung
   * **Repository wechseln**: Ersetzt den Arbeitsbereich durch ein anderes Repository. Alle nicht zugesicherten Arbeiten gehen verloren.
   * **Abmelden**: Trennt die Verbindung zu GitHub
   * **Bibliotheks-URL** - Diese URL verweist auf eine Datei „library.json“, die verfügbare Blöcke, ihre Varianten und Beispielinhalte definiert.
   * **Site-Basis-URL** - Die Ursprungs-URL der migrierten Website
* **Agentenberechtigungen** - Zulassen, dass der Agent auf Konfigurationsoptionen zugreift
   * **Zulassen, dass LLM in meinem Namen auf admin.hlx.page zugreift** - Wenn diese Option aktiviert ist, kann der KI-Assistent Site-Konfigurationen und Metadaten mithilfe Ihrer IMS-Anmeldeinformationen aus Adobe Experience Manager abrufen.
   * **Benutzerdefiniertes IMS-Token** - Sie können ein benutzerdefiniertes IMS-Token bereitstellen, das anstelle Ihres standardmäßigen Sitzungs-Tokens verwendet werden soll.
* **Anmeldeinformationen** ermöglicht es Ihnen, ein persönliches Zugriffstoken für Figma anzugeben, damit die [Konsole auf Designblöcke für Ihr Projekt zugreifen kann.](/help/ai-in-aem/agents/brand-experience/modernization/prompting-guide.md#figma-block-migration)
   * Das Token erfordert die folgenden schreibgeschützten Bereiche:
      * `file_content:read`
      * `file_metadata:read`
      * `library_assets:read`
      * `library_content:read`
      * `team_library_content:read`
      * `file_dev_resources:read`
      * `projects:read`
   * [Weitere Informationen zum Einrichten persönlicher Zugriffstoken finden Sie ](https://help.figma.com/hc/en-us/articles/8085703771159-Manage-personal-access-tokens) der Figma-Dokumentation .
* **Support** fasst Informationen zusammen, die bei einer Support-Anfrage an das Adobe-Supportteam weitergegeben werden.
   * **Support anfordern** - Klicken Sie hier, um eine Support-Anfrage von Adobe zu starten, ohne die Konsole zu verlassen.
* **Gefahrenbereich** enthält Einstellungen, die Ihren Arbeitsbereich zurücksetzen können.
   * **Arbeitsbereich zurücksetzen** - Klicken Sie darauf, um den Arbeitsbereich auf den Ausgangszustand zurückzusetzen. Dies kann nicht rückgängig gemacht werden.
