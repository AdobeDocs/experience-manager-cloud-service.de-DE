---
title: AEM Screens für Ihre Demosite aktivieren
description: Erfahren Sie mehr über die Schritte zur Aktivierung des vollständigen as a Cloud Service AEM Screens-Erlebnisses auf Ihrer Demosite.
source-git-commit: df9b777e24e56ed0329895f833f50b45ecf2defa
workflow-type: tm+mt
source-wordcount: '2666'
ht-degree: 2%

---


# AEM Screens für Ihre Demosite aktivieren {#enable-screens}

Erfahren Sie mehr über die Schritte zur Aktivierung des vollständigen as a Cloud Service AEM Screens-Erlebnisses auf Ihrer Demosite.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM-Referenz-Demos-Add-On-Journey, [Demosite erstellen,](create-site.md) Sie haben eine neue Demosite erstellt, die auf den Vorlagen des Referenz-Demo-Add-ons basiert. Sie sollten jetzt:

* Erfahren Sie, wie Sie auf die AEM Authoring-Umgebung zugreifen.
* Erfahren Sie, wie Sie eine Site basierend auf einer Vorlage erstellen.
* Machen Sie sich mit den Grundlagen zum Navigieren in der Site-Struktur und Bearbeiten einer Seite vertraut.

Nachdem Sie nun über Ihre eigene Demosite verfügen, um die Tools zu untersuchen und zu verstehen, die Ihnen bei der Verwaltung Ihrer Demosites helfen, können Sie jetzt das gesamte as a Cloud Service Erlebnis von AEM Screens für Ihre Demosites aktivieren.

## Ziel {#objective}

Das AEM Reference Demos Add-On enthält AEM Screens-Inhalte für We.Cafe, einen vertikalen Café-Geschäftsbereich. In diesem Dokument erfahren Sie, wie Sie die Demoeinrichtung von We.Cafe im Kontext von AEM Screens ausführen. Nach dem Lesen sollten Sie:

* Machen Sie sich mit den Grundlagen von AEM Screens vertraut.
* Machen Sie sich mit dem Demoinhalt von We.Cafe vertraut.
* Erfahren Sie, wie Sie AEM Screens für We.Cafe konfigurieren.
   * Erfahren Sie, wie Sie ein Screens-Projekt für We.Cafe erstellen.
   * Sie können einen simulierten Wetterdienst mit Google Tabellen und APIs konfigurieren.
   * Simulieren Sie dynamisch ändernde Screens-Inhalte basierend auf Ihrem &quot;Wetterdienst&quot;.
   * Installieren und verwenden Sie den Screens-Player.

## Screens {#understand-screens}

AEM Screens as a Cloud Service ist eine Lösung für die digitale Beschilderung, mit der Marketer digitale Erlebnisse skaliert erstellen und verwalten können. Mit AEM Screens as a Cloud Service können Sie ansprechende und dynamische Erlebnisse für die digitale Beschilderung erstellen, die in öffentlichen Räumen genutzt werden sollen.

>[!TIP]
>
>Die vollständigen Informationen zu AEM Screens as a Cloud Service finden Sie im [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

Durch die Installation des Add-On für AEM Referenz-Demos haben Sie automatisch We.Cafe-Inhalte für AEM Screens in Ihrer Demo-Authoring-Umgebung zur Verfügung. Die im Abschnitt [Bereitstellen eines Demo Screens-Projekts](#deploy-project) ermöglichen es Ihnen, das gesamte AEM Screens-Erlebnis zu aktivieren, indem Sie diese Inhalte veröffentlichen und für Medienplayer bereitstellen usw.

## Grundlegendes zum Demoinhalt {#demo-content}

Das Café We.Cafe besteht aus drei Geschäften an drei Standorten in den USA. Alle drei Geschäfte bieten drei ähnliche Erlebnisse:

* Eine Menüplatine über dem Zähler mit zwei oder drei vertikalen Bedienfeldern
* Eine Eingangsanzeige gegenüber der Straße mit einer horizontalen oder vertikalen Leiste, die die Kunden in den Laden einlädt
* Ein Schnellbestellungs-Kiosk, um die Warteschlange mit einem vertikalen Tablet zu umgehen

>[!NOTE]
>
>Nur die Anzeige des Eingangs kann in der aktuellen Version der Demo getestet werden. Andere Anzeigen folgen in einer zukünftigen Version.
>
>Der Kiosk ist nicht in der aktuellen Version der Demo enthalten. Sie wird in einer zukünftigen Version enthalten sein.

Die Lage in New York wird als kleiner Laden angenommen, der nicht viel Platz hat und daher:

* Die Menükarte hat nur zwei vertikale Bedienfelder anstelle von drei für San Francisco und San Jose
* Die Eingangsanzeige wird vertikal statt horizontal positioniert

>[!NOTE]
>
>Wenn Sie sich für eine Verbindung mit dem Screens-Cloud Service im [Verbinden von Screens as a Cloud Service](#connect-screens) erstellen Sie die Speicherorte als Ordner unter &quot;Anzeigen&quot;. Siehe [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments weitere Informationen zu Anzeigen.

### Café-Layouts {#care-layouts}

Die Standorte von We.Cafe haben die folgenden Layouts:

![We.Cafe-Layouts](assets/cafe-layouts.png)

>[!NOTE]
>
>Die Messungen für die Bildschirme sind in Zoll angegeben.

### Eintritt {#entrance}

Die Eingangsanzeige ist tagsgegliedert und ändert nur das erste Bild von morgens bis nachmittags. Bei jedem Durchgang der Sequenz wird auch eine andere spezielle Kaffeezubereitung beworben, bei der jedes Mal eine gezählte eingebettete Sequenz verwendet wird, um ein anderes Element wiederzugeben.

Das letzte Bild auf den Eingangskanälen ist ebenfalls zielgerichtet (d. h. dynamisch geändert), basierend auf der Außentemperatur, die simuliert werden kann, wie im Abschnitt [Simulierte Datenquelle erstellen](#data-source) Abschnitt.

## Bereitstellen eines Demo Screens-Projekts {#deploy-project}

Um den Demoinhalt in der Sandbox zu verwenden, die Sie in der [Programm erstellen](create-program.md) Schritt, muss eine Site basierend auf einer Vorlage erstellt werden.

Wenn Sie noch keine Demosite von We.Cafe erstellt haben, führen Sie einfach die gleichen Schritte wie im [Demosite erstellen](create-site.md) Abschnitt. Wählen Sie bei der Auswahl der Vorlage einfach die **We.Cafe-Website-Vorlage**.

![We.Cafe-Vorlage](assets/wecafe-template.png)

Sobald der Assistent abgeschlossen ist, finden Sie den Inhalt, der unter Sites bereitgestellt wird, und können wie jeder andere Inhalt navigieren und durchsuchen.

![We.Cafe-Inhalte](assets/wecafe-content.png)

Nachdem Sie jetzt über Demoinhalte von We.Cafe verfügen, können Sie entscheiden, wie Sie AEM Screens testen möchten:

* Wenn Sie den Inhalt nur in der AEM Sites-Konsole untersuchen möchten, sollten Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) Abschnitt! keine weiteren Maßnahmen erforderlich sind.
* Wenn Sie die dynamischen Funktionen von AEM Screens vollständig nutzen möchten, fahren Sie mit dem nächsten Abschnitt fort: [Dynamische Änderung des Screens-Inhalts.](#dynamically-change)

## Dynamisches Ändern von Screens-Inhalten {#dynamically-change}

Genau wie AEM Sites kann AEM Screens Inhalte dynamisch kontextabhängig ändern. In der Demo von We.Cafe sind Kanäle konfiguriert, um je nach aktueller Temperatur unterschiedliche Inhalte anzuzeigen. Um dies zu simulieren, müssen wir unseren eigenen einfachen Wetterdienst erstellen.

### Simulierte Datenquelle erstellen {#data-source}

Da es sehr schwierig ist, das Wetter während einer Demo oder während des Tests zu ändern, müssen Temperaturänderungen simuliert werden. Wir simulieren einen Wetterdienst, indem wir einen Temperaturwert in einer Google Tabellen-Tabelle speichern, AEM ContextHub aufruft, um die Temperatur abzurufen.

#### Erstellen eines Google API-Schlüssels {#create-api-key}

Zunächst müssen wir einen Google-API-Schlüssel erstellen, um den Datenaustausch zu erleichtern.

1. Melden Sie sich bei einem Google-Konto an.
1. Öffnen Sie die Cloud-Konsole über diesen Link. `https://console.cloud.google.com`.
1. Erstellen Sie ein neues Projekt, indem Sie oben links in der Symbolleiste nach dem **Google Cloud Platform** Beschriftung.

   ![Google Cloud Console](assets/google-cloud-console.png)

1. Klicken Sie im Dialogfeld &quot;Projektauswahl&quot;auf **NEUES PROJEKT**.

   ![Neues Projekt](assets/new-project.png)

1. Benennen Sie das Projekt und klicken Sie auf **ERSTELLEN**.

   ![Projekt erstellen](assets/create-project.png)

1. Vergewissern Sie sich, dass Ihr neues Projekt ausgewählt ist, und wählen Sie dann über das Menü &quot;Hamburger&quot;im Dashboard der Cloud Console die Option **APIs und Dienste**.

   ![APIs und Dienste](assets/apis-services.png)

1. Klicken Sie im linken Bereich des Fensters &quot;APIs &amp; Services&quot;auf **Anmeldeinformationen** Klicken Sie oben im Fenster auf **CREDENTIALS** und **API-Schlüssel**.

   ![Berechtigungen](assets/credentials.png)

1. Kopieren Sie im Dialogfeld Ihren neuen API-Schlüssel und speichern Sie ihn zur späteren Verwendung. Klicken **SCHLIESSEN** , um das Dialogfeld zu schließen.

#### Google Tabellen-API aktivieren {#enable-sheets}

Um den Austausch von Google Tabellen-Daten mithilfe Ihres API-Schlüssels zu ermöglichen, müssen Sie die Google Tabellen-API aktivieren.

1. Kehren Sie zur Google Cloud Console zurück unter `https://console.cloud.google.com` für Ihr Projekt und wählen Sie dann über das Hamburger-Menü **APIs und Dienste -> Bibliothek**.

   ![API-Bibliothek](assets/api-library.png)

1. Scrollen Sie im Bildschirm &quot;API-Bibliothek&quot;zu unserer Suche nach **Google Tabellen-API**. Klicken Sie darauf.

   ![API-Bibliothekssuche](assets/api-library-search.png)

1. Im **Google Tabellen-API** Fensterklick **AKTIVIEREN**.

   ![Google-Tabellen-API](assets/sheets-api.png)

#### Google Tabellen-Tabelle erstellen {#create-spreadsheet}

Jetzt können Sie eine Google Tabellen-Tabelle erstellen, in der Ihre Wetterdaten gespeichert werden.

1. Navigieren Sie zu `https://docs.google.com` und erstellen Sie eine neue Google Tabellen-Tabelle.
1. Definieren Sie die Temperatur durch Eingabe von `32` in Zelle A2.
1. Freigeben des Dokuments durch Klicken auf **Freigeben** oben rechts im Fenster und unter **Link abrufen** click **Änderung**.

   ![Freigabeseite](assets/share-sheet.png)

1. Kopieren Sie den Link für den nächsten Schritt.

   ![Link freigeben](assets/share-link.png)

1. Suchen Sie die Tabellenkennung.

   * Die Tabellen-ID ist die zufällige Zeichenfolge im Tabellenlink, die Sie nach `d/` und davor `/edit`.
   * Beispiel:
      * Wenn Ihre URL `https://docs.google.com/spreadsheets/d/1cNM7j1B52HgMdsjf8frCQrXpnypIb8NkJ98YcxqaEP30/edit#gid=0`
      * Die Tabellenkennung lautet `1cNM7j1B52HgMdsjf8frCQrXpnypIb8NkJ98YcxqaEP30`.

1. Kopieren Sie die Tabellenkennung für die zukünftige Verwendung.

#### Testen Ihres Wetterdienstes {#test-weather-service}

Nachdem Sie Ihre Datenquelle als Google Tabellen-Tabelle erstellt und den Zugriff über API aktiviert haben, testen Sie sie, um sicherzustellen, dass Ihr &quot;Wetterdienst&quot;zugänglich ist.

1. Öffnen Sie einen Webbrowser.

1. Geben Sie die folgende Anfrage ein und ersetzen Sie dabei die Tabellen-ID und API-Schlüsselwerte, die Sie zuvor gespeichert haben.

   ```
   https://sheets.googleapis.com/v4/spreadsheets/<yourSheetID>/values/Sheet1?key=<yourAPIKey>
   ```

1. Wenn Sie JSON-Daten ähnlich den folgenden erhalten, richten Sie sie ordnungsgemäß ein.

   ```json
   {
     "range": "Sheet1!A1:Z1000",
     "majorDimension": "ROWS",
     "values": [
       [],
       [
         "32"
       ]
     ]
   }
   ```

AEM Screens kann denselben Dienst verwenden, um auf die simulierten Wetterdaten zuzugreifen. Dies wird im nächsten Schritt konfiguriert.

### Konfigurieren von ContextHub {#configure-contexthub}

AEM Screens kann Inhalte dynamisch kontextabhängig ändern. Die Demo von We.Cafe verfügt über Kanäle, die so konfiguriert sind, dass je nach aktueller Temperatur unterschiedliche Inhalte angezeigt werden, indem AEM ContextHub genutzt wird.

>[!TIP]
>
>Die vollständigen Informationen zu ContextHub finden Sie im [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

Wenn der Bildschirminhalt angezeigt wird, ruft ContextHub Ihren Wetterdienst auf, um die aktuelle Temperatur zu ermitteln, um zu bestimmen, welcher Inhalt angezeigt werden soll.

Zu Demozwecken können die Werte im Blatt geändert werden. ContextHub erkennt dies und der Inhalt wird im Kanal entsprechend der aktualisierten Temperatur angepasst.

1. Wechseln Sie in der AEMaaCS-Autoreninstanz zu **Globale Navigation -> Tools -> Sites -> ContextHub**.
1. Wählen Sie den Konfigurationscontainer aus, der denselben Namen hat wie der, den Sie beim Erstellen des Screens-Projekts aus dem **We.Cafe-Website-Vorlage**.
1. Auswählen **Konfiguration > ContextHub-Konfiguration > Google Tabellen** Klicken Sie dann auf **Nächste** oben rechts.
1. Die Konfiguration sollte bereits über vorkonfigurierte JSON-Daten verfügen. Es gibt zwei Werte, die geändert werden müssen:
   1. Ersetzen `[your Google Sheets id]` mit der Tabellenkennung [haben Sie zuvor gespeichert.](#create-spreadsheet)
   1. Ersetzen `[your Google API Key]` mit dem API-Schlüssel [haben Sie zuvor gespeichert.](#create-api-key)
1. Klicken Sie auf **Speichern**.

Jetzt können Sie den Temperaturwert in Ihrer Google Tabellenspalte ändern, und ContextHub aktualisiert Screens dynamisch, wenn es &quot;die Wetteränderung sieht&quot;.

### Testen dynamischer Daten {#test-dynamic}

Nachdem AEM Screens und ContextHub mit Ihrem Wetterdienst verbunden sind, können Sie ihn testen, um zu sehen, wie Bildschirme Inhalte dynamisch aktualisieren können.

1. Rufen Sie Ihre Sandbox-Autoreninstanz auf.
1. Navigieren Sie zur Sites-Konsole über **Globale Navigation -> Sites** und wählen Sie die folgende Seite aus **Screens -> &lt;project-name> -> Kanäle -> Einstiegsmorgens (Hochformat)**.

   ![Demoprojektinhalt auswählen](assets/project-content.png)

1. Klicken Sie in der Symbolleiste auf Bearbeiten oder geben Sie den Tastaturbefehl ein `e` , um die Seite zu bearbeiten.

1. Im Editor können Sie den Inhalt sehen. Beachten Sie, dass ein Bild blau mit einem Targeting-Symbol in der Ecke hervorgehoben ist.

   ![Screens-Inhalt im Editor](assets/screens-content-editor.png)

1. Ändern Sie die Temperatur, die Sie in Ihr Arbeitsblatt eingegeben haben, von 32 auf 70 und beobachten Sie die Inhaltsänderung.

   ![Screens-Inhalt im Editor](assets/screens-content-editor-2.png)

Aufgrund der Temperaturänderung von 32°F (0°C) bis hin zu einer bequemen 70°F (21°C) wurde das Bild von einem wärmenden Teetassen zu einem kühlen eisigen Kaffee geändert.

>[!IMPORTANT]
>
>Verwenden Sie die beschriebene Google Tabellen-Lösung nur zu Demozwecken. Die Verwendung von Google Tabellen in Produktionsumgebungen wird von Adobe nicht unterstützt.

## Verbinden von Screens as a Cloud Service {#connect-screens}

Wenn Sie auch ein echtes Digital Signage-Erlebnis einrichten möchten, einschließlich eines Players, der auf einem Digital Signage-Gerät oder auf Ihrem Computer ausgeführt wird, führen Sie die nächsten Schritte aus.

Alternativ können Sie die Demo einfach im Kanal-Editor in AEMaaCS in der Vorschau anzeigen.

>[!TIP]
>
>Ausführliche Informationen zum Kanal-Editor finden Sie im [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

### AEM Screens as a Cloud Service konfigurieren {#configure-screens}

Zunächst müssen Sie Ihre Screens-Demoinhalte as a Cloud Service in AEM Screens veröffentlichen und den Dienst konfigurieren.

1. Veröffentlichen Sie den Inhalt Ihres Demoscreens-Projekts.
1. Navigieren Sie zu Screens as a Cloud Service unter `https://experience.adobe.com/screens` und melden Sie sich an.
1. Vergewissern Sie sich oben rechts im Bildschirm, dass Sie sich in der richtigen Organisation befinden.

   ![Überprüfen der Screens-Organisation](assets/screens-org.png)

1. Klicken Sie oben links auf die **Einstellungen bearbeiten** Symbol, geformt wie ein Gang.

   ![Einstellungen bearbeiten](assets/screens-edit-settings.png)

1. Geben Sie die URLs der Autoren- und Veröffentlichungsinstanzen von AEMaaCS an, in denen Sie Ihre Demosite erstellt haben, und klicken Sie auf **Speichern**.

   ![Screens-Einstellung](assets/screens-settings.png)

1. Sobald Screens mit Ihren Demo-Instanzen verbunden ist, ruft es Ihren Kanalinhalt ab. Klicken Sie auf **Kanäle** im linken Bereich, um Ihre veröffentlichten Kanäle anzuzeigen. Es kann einen Moment dauern, bis die Informationen ausgefüllt sind. Sie können auf Blau klicken **Synchronisieren** rechts oben im Bildschirm, um die Informationen zu aktualisieren.

   ![Demo-Kanalinformationen](assets/screens-channels.png)

1. Klicken Sie auf **Anzeigen** im linken Bereich. Sie haben noch keinen für Ihre Demo erstellt. Wir simulieren die Standorte von We.Cafe, indem wir jeweils Ordner erstellen. Klicken Sie auf **Erstellen** oben rechts im Bildschirm, und wählen Sie **Ordner**.

   ![Anzeige erstellen](assets/screens-displays.png)

1. Geben Sie im Dialogfeld einen Ordnernamen wie **San Jose** und klicken Sie auf **Erstellen**.

1. Öffnen Sie den Ordner, indem Sie darauf klicken und dann auf **Erstellen** oben rechts und wählen Sie **Anzeige**.

1. Geben Sie einen Anzeigenamen ein und klicken Sie auf **Erstellen**.

   ![Anzeige erstellen](assets/create-display.png)

1. Nachdem der Kanal erstellt wurde, klicken Sie darauf, um Details anzuzeigen. Der Anzeige muss ein Kanal zugewiesen werden, der von Ihrer Demosite synchronisiert wurde. Klicken Sie auf **Kanal zuweisen** oben rechts auf dem Bildschirm.

   ![Kanaldetail](assets/channel-detail.png)

1. Wählen Sie im Dialogfeld den Kanal aus und klicken Sie auf **Zuweisen**.

   ![Kanal zuweisen](assets/assign-channel.png)

Sie können diese Schritte für Ihre zusätzlichen Standorte und Anzeigen wiederholen. Nach Abschluss des Vorgangs haben Sie Ihre Demosite mit AEM Screens verknüpft und die erforderliche Konfiguration abgeschlossen.

Sie können die Demovorschau einfach im Kanal-Editor in AEMaaCS anzeigen.

### Verwenden des Screens-Players {#screens-player}

Um den Inhalt auf einem tatsächlichen Bildschirm anzuzeigen, können Sie den Player herunterladen und lokal einrichten. AEM Screens as a Cloud Service stellt dann Inhalte für Ihren Player bereit

#### Generieren eines Registrierungs-Codes {#registration-code}

Zunächst müssen Sie einen Registrierungs-Code erstellen, um einen Player sicher mit AEM Screens as a Cloud Service zu verbinden.

1. Navigieren Sie zu Screens as a Cloud Service unter `https://experience.adobe.com/screens` und melden Sie sich an.
1. Vergewissern Sie sich oben rechts im Bildschirm, dass Sie sich in der richtigen Organisation befinden.

   ![Überprüfen der Screens-Organisation](assets/screens-org.png)

1. Klicken Sie im linken Bereich auf **Player-Verwaltung -> Registrierungs-Codes** und klicken Sie anschließend auf **Code erstellen** oben rechts auf dem Bildschirm.

![Registrierungs-Codes](assets/registration-codes.png)

1. Geben Sie einen Namen für den Code ein und klicken Sie auf **Erstellen**.

   ![Code erstellen](assets/create-code.png)

1. Nachdem der Code erstellt wurde, wird er in der Liste angezeigt. Klicken Sie auf , um den Code zu kopieren.

   ![Registrierungs-Code](assets/registration-code.png)

#### Installieren und Konfigurieren des Players {#install-player}

1. Laden Sie den Player für Ihre Plattform von herunter. `https://download.macromedia.com/screens/` und installieren Sie es.
1. Führen Sie den Player aus und wechseln Sie zur **Konfiguration** Registerkarte, scrollen Sie nach unten, um auf klicken und bestätigen Sie beide **Auf Factory zurücksetzen** und dann **Wechsel zum Cloud-Modus**.

   ![Player-Einstellungen](assets/player-configuration.png)

1. Der Player ändert sich automatisch in **Player-Registrierung** Registerkarte. Geben Sie den zuvor generierten Code ein und klicken Sie auf **registrieren**.

   ![Player-Registrierung](assets/player-registration-code.png)

1. Wechseln Sie zu **Systeminformationen** um zu bestätigen, dass der Player registriert wurde.

   ![Registrierter Player](assets/player-registered.png)

#### Player einer Anzeige zuweisen {#assign-player}

1. Navigieren Sie zu Screens as a Cloud Service unter `https://experience.adobe.com/screens` und melden Sie sich an.
1. Vergewissern Sie sich oben rechts im Bildschirm, dass Sie sich in der richtigen Organisation befinden.

   ![Überprüfen der Screens-Organisation](assets/screens-org.png)

1. Klicken Sie im linken Bereich auf **Player-Verwaltung -> Player** und Sie sehen den Player, den Sie zuvor installiert und registriert haben.

   ![Player](assets/players.png)

1. Klicken Sie auf den Player-Namen, um die Details zu öffnen, und klicken Sie dann auf **Zur Anzeige zuweisen** oben rechts im Bildschirm.

   ![Player zur Anzeige zuweisen](assets/assign-to-display.png)

1. Wählen Sie im Dialogfeld die zuvor erstellte Anzeige aus und klicken Sie auf **Auswählen**.

   ![Anzeige zuweisen](assets/assign-a-display.png)

#### Wiedergabe! {#playback}

Nachdem Sie einem Player eine Anzeige zugewiesen haben, stellt AEM Screens as a Cloud Service den Inhalt für Ihren Player dort bereit, wo er sichtbar ist.

![Hochformat des Eintritts](assets/entrance-portrait.jpg)

![Einstiegslandschaft](assets/entrance-landscape.jpg)

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der AEM Referenz-Demo-Add-On-Journey abgeschlossen haben, sollten Sie Folgendes tun:

* Machen Sie sich mit den Grundlagen von AEM Screens vertraut.
* Machen Sie sich mit dem Demoinhalt von We.Cafe vertraut.
* Erfahren Sie, wie Sie AEM Screens für We.Cafe konfigurieren.

Sie können jetzt die Funktionen von AEM Screens mit Ihren eigenen Demosites erkunden. Fahren Sie mit dem nächsten Abschnitt des Journey fort, [Verwalten Ihrer Demosites,](manage.md) Hier erfahren Sie mehr über die Tools, die Ihnen bei der Verwaltung Ihrer Demosites zur Verfügung stehen und wie Sie diese entfernen können.

Sie können auch einige der zusätzlichen Ressourcen im Abschnitt [Abschnitt &quot;Zusätzliche Ressourcen&quot;](#additional-resources) um mehr über die Funktionen zu erfahren, die Sie auf dieser Journey gesehen haben.

## Zusätzliche Ressourcen {#additional-resources}

* [ContextHub-Dokumentation](/help/sites-cloud/authoring/personalization/contexthub.md) - Erfahren Sie, wie ContextHub verwendet werden kann, um Inhalte basierend auf dem Benutzerkontext über Wetterbedingungen hinaus zu personalisieren.
* [Verwenden von API-Schlüsseln - Dokumentation zu Google](https://developers.google.com/maps/documentation/javascript/get-api-key) - Eine praktische Referenz für Details zur Verwendung von Google-API-Schlüsseln.
* [Anzeigen](/help/screens-cloud/creating-content/creating-displays-screens-cloud.md) - Erfahren Sie mehr darüber, was eine Anzeige in AEM Screens ist und was sie tun kann.
* [Player herunterladen](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md) - Erfahren Sie, wie Sie auf den Screens-Player zugreifen und wie Sie ihn installieren.
* [Player registrieren](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) - Erfahren Sie, wie Sie einen Player für Ihr AEM Screens-Projekt einrichten und registrieren.
* [Zuweisen eines Players zu einer Anzeige](/help/screens-cloud/managing-players-registration/assigning-player-display.md) - Konfigurieren Sie einen Player für die Anzeige Ihres Inhalts.
