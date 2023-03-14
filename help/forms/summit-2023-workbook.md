---
title: Forms mit Kernkomponenten und Headless integrieren
seo-title: Build Engaging Forms Using Core Components and Headless
description: Forms mit Kernkomponenten und Headless integrieren
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
source-git-commit: b68902ef4f7c61f77aa0d03ad718d5bf3023dea0
workflow-type: tm+mt
source-wordcount: '2465'
ht-degree: 1%

---


# Forms mit Kernkomponenten und Headless integrieren

## Lab-Übersicht

In diesem praktischen Labor lernen Sie:

Verwendung von AEM Forms zur einfachen Erstellung adaptiver Formulare mithilfe der neuesten Kernkomponenten, die mit AEM Sites konsistent sind, Erlebnisse für die Omnichannel-Datenerfassung ermöglichen, indem adaptive Formulare als Headless-Formulare an Web, Mobile und Chat übermittelt werden. Außerdem lernen Sie Best Practices rund um die Formatierung, Anpassungen und Front-End-Entwicklung kennen.

## Wichtige Schritte

* **Geschäftliche Agilität**: Als Business-Anwender kann ich mühelos Formularerlebnisse für mehrere Kanäle erstellen.

* **Unterstützung für Frontend-Entwickler**: Als Frontend-Entwickler kann ich das Benutzererlebnis mit Headless-Formularen steuern.

* **EntwicklerVelocity**: Als Entwickler kann ich mühelos und konsistent Sites- und Forms-Komponenten anpassen.

## Voraussetzungen

AEM Forms als Cloud Service-Sandbox

## Lektion 1

### Ziel

Machen Sie sich mit der as a Cloud Service AEM Forms-Umgebung vertraut.

### Lektionskontext

In dieser Lektion lernen Sie die as a Cloud Service AEM Forms-Umgebung kennen, indem Sie in der Benutzeroberfläche navigieren.

### Übung

1. Öffnen Sie den Browser und geben Sie die URL der Autorenumgebung des Cloud Service ein. Beispiel:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Melden Sie sich in der Autorenumgebung des Cloud Service gemäß den freigegebenen Anmeldedaten an. Beispiel: Benutzername: [L716+001@summitlab.us](mailto:L716%2B001@summitlab.us)
Kennwort: 
**Adobe123!**

1. Nachdem Sie angemeldet sind, navigieren Sie zur AEM Forms-Benutzeroberfläche. Klicken **Forms**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. Klicken **Forms und Dokumente**. Schließen Sie alle Popups, die sich auf Voreinstellungen oder Informationen beziehen.

   ![](/help/forms/assets/screenshot2028113929.png)

   Alle verfügbaren Formulare werden angezeigt.

   ![](/help/forms/assets/screenshot2028114029.png)

## Lektion 2

### Ziel

Erstellen Sie ein adaptives Formular mit den neuesten Kernkomponenten, konfigurieren und senden Sie es.

## Lektionskontext

In dieser Lektion erstellen Sie als Geschäftsbenutzer ein adaptives Formular für mehrere Kanäle wie Web, Mobile und Chat, indem Sie adaptive Formulare erstellen und standardisierte OOTB-Kernkomponenten für die Datenerfassung verwenden.

## Übung

1. Erstellen Sie einen Übermittlungsendpunkt für das Formular:

   1. Öffnen <https://requestbin.com/> in einer neuen Browser-Registerkarte.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. Klicken **Öffentlichen Ordner erstellen** und kopieren Sie die Endpunkt-URL.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. Erstellen Sie ein adaptives Formular über die Benutzeroberfläche des Assistenten:

   1. Navigieren Sie auf der in Lektion 1 verwendeten Browser-Registerkarte zur AEM Forms als Cloud Service-Webschnittstelle und navigieren Sie zu Forms und Dokumenten.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. Klicken **Erstellen** und wählen Sie Adaptives Formular aus.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. Wählen Sie die **Leer mit Kernkomponenten** Vorlage auf dem Vorlagenauswahlbildschirm wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Klicken Sie auf **Stil** und wählen Sie die **wknd-theme** Design wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Klicken Sie auf **Einsendung** und wählen Sie die **An REST-Endpunkt übermitteln** und geben Sie den öffentlichen Ordner im
      **URL für die POST-Anforderung** wie unten gezeigt:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Klicken Sie auf **Erstellen**. Geben Sie einen Namen und einen Titel für Ihr Formular an. Beispiel: **contactus**. Klicken Sie auf **Erstellen**.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. Der Editor für adaptive Formulare wird geöffnet. Schließen Sie alle Popups oder Dialogfelder für Voreinstellungen oder Informationen. Klicken Sie in der linken Leiste auf den Komponenten-Browser und fügen Sie die **Fußzeile** -Komponente am unteren Rand des leeren Formulars.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. Fügen Sie die **Kopfzeile** -Komponente am Anfang des Formulars.
      ![](/help/forms/assets/screenshot2028122029.png)

   1. Hinzufügen einer **Titel** -Komponente in die Mitte des Formulars.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. Hinzufügen einer **Texteingabe** -Komponente nach der Titelkomponente.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. Hinzufügen einer **Zahleneingabe** -Komponente.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. Hinzufügen einer **Senden-Schaltfläche** -Komponente in das Formular ein.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. Klicken Sie auf **Titel** -Komponente **Popup-Menü** angezeigt. Klicken Sie auf **Symbol Bearbeiten** im Menü, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. Eingabe `Contact Us` als Titeltext.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. Klicken Sie auf **Texteingabe** -Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie auf **Symbol Bearbeiten** im Menü, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. Eingabe **Vollständiger Name** als Feldbezeichnung.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. Klicken Sie auf **Zahleneingabe** -Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie auf **Symbol Bearbeiten** im Menü, um den Titel zu bearbeiten.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. Geben Sie die **Telefonnummer** als Feldbezeichnung.
      ![](/help/forms/assets/screenshot2028123829.png)


1. Fügen Sie Validierungen zum Formular hinzu:

   1. Klicken Sie auf **Telefonnummer** -Komponente, damit das Popup-Menü angezeigt wird. Klicken Sie auf **Schraubensymbol** im Menü, um das Feld zu konfigurieren.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. Öffnen Sie die **Registerkarte &quot;Validierungen&quot;**, markieren Sie das Feld **Erforderlich** und klicken Sie auf **Fertig**. Die Erfolgsmeldung wird angezeigt.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. Klicken **Vorschau** , um eine Vorschau des Formulars aus der Perspektive des Endbenutzers anzuzeigen.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. Füllen Sie das Formular mit Platzhalterdaten aus
      ![](/help/forms/assets/screenshot2028125629.png)

   1. Formular senden
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Überprüfen Sie im Tab Anforderungs-bin die gesendeten Daten.
      ![](/help/forms/assets/screenshot2028125829.png)

Verwenden Sie nun für die verbleibende Übung ein vorab erstelltes Registrierungsformular.

1. Öffnen Sie beispielsweise die AEM Forms-Verwaltungsoberfläche. `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`und wählen Sie das Registrierungsformular aus.

   ![](/help/forms/assets/screenshot2028115529.png)

1. Klicken Sie auf **Veröffentlichen**.

   ![](/help/forms/assets/screenshot2028115629.png)

   Die Erfolgsmeldung wird angezeigt.

   ![](/help/forms/assets/screenshot2028115729.png)

   Die Veröffentlichungs-URL des Formulars ähnelt der `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. Ersetzen Sie zum Anzeigen des veröffentlichten Formulars die Programm-ID (pXXXXXX) und die Umgebungs-ID (eXXXXXX) in der obigen URL durch die IDs Ihrer Umgebung.

## Lektion 3

### Ziel

Aktualisieren Sie Stile mithilfe der Best Practices für die Frontend-Entwicklung.

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwickler, wie Sie die Formatierung für das zuvor erstellte adaptive Formular einfach aktualisieren können.

### Übung

Lokales Repository des Designs einrichten:

1. Öffnen Sie die Eingabeaufforderung oder Shell mit Administratorrechten:

   ![](/help/forms/assets/screenshot2028115829.png)

1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zu **c:\git** Ordner

   ```Shell
   cd c:\git
   ```

1. Verwenden Sie den folgenden Befehl, um den Frontend-Code des Designs zu klonen:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Verwenden Sie den folgenden Befehl in der angegebenen Reihenfolge, um zum **aem-forms-theme-canvas** und öffnen Sie Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. Auswählen **Den Autoren aller Dateien im übergeordneten Ordner vertrauen** und klicken Sie auf **Ja, ich vertraue den Autoren**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. Um das in Ihrer Cloud Service-Veröffentlichungsumgebung gehostete Formular wiederzugeben, benennen Sie die `env_template` -Datei.  Um die Datei umzubenennen, klicken Sie mit der rechten Maustaste auf das **env_template** und wählen Sie die **Umbenennen** -Option.

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest und speichern Sie die Datei:

   * **AEM_URL**: Geben Sie Ihre Veröffentlichungsumgebung für den Cloud-Service an. Beispiel: `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: Geben Sie den Pfad des Formulars an. Wenn der Formularpfad beispielsweise `/content/forms/af/registration`, würde der Wert dieser Variablen `registration`.

   ![](/help/forms/assets/screenshot2028116429.png)


1. Führen Sie im Fenster Eingabeaufforderung den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Wenn Sie eine Meldung erhalten, in der Sie aufgefordert werden, npm über die `npm notice Run npm nstall -g npm@9.6.0`-Befehl, ignorieren Sie die Nachricht.
   > * Führen Sie keine anderen npm-Befehle aus, es sei denn, dies wird in der Arbeitsmappe angewiesen.


1. Führen Sie nun den folgenden Befehl aus, um eine Vorschau des Formulars anzuzeigen.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   Warten Sie nach Ausführung des oben genannten Befehls auf die `webpack compiled` Nachricht. Das Formular wird auf einer Browser-Registerkarte angezeigt.

   >[!NOTE]
   >
   >Wenn nach der Ausführung des `npm run live` Befehl für mehr als 3-4 Minuten, ändern Sie `localhost` in der Browser-URL auf 127.0.0.1 und Treffer **Eingabe**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. Öffnen Sie in Visual Studio Code die `PROJECT\src\site\_variables.scss` -Datei. Beachten Sie die `$error` Farbe ist ein Farbton von RED.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Senden Sie im Browser das Formular, um die rote Farbe im **Vorname** -Feld.

   ![](/help/forms/assets/screenshot2028120829.png)

1. Legen Sie die **$error** Farbe auf **#5736eb** und speichern Sie die Datei.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Aktualisieren Sie den Browser und senden Sie das Formular. Die Fehlerfarbe für das Vorname-Feld wurde entsprechend geändert.

   ![](/help/forms/assets/screenshot2028121129.png)

1. Drücken Sie in der Eingabeaufforderung die **Strg+C**, eingeben **Y** und drücken Sie **Eingabe** zum Beenden des npm-Prozesses. Es ist wichtig, den npm-Server zu stoppen, damit er nicht mit dem nächsten Satz von Übungen in Konflikt gerät.
1. Schließen Sie die Fenster Visual Studio Code und Eingabeaufforderung .

## Lektion 4

### Ziel

Wiedergabe des Formulars auf Web/Mobile- und anderen Schnittstellen als Headless-Formular.

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwickler, wie Sie das zuvor erstellte adaptive Formular mithilfe des Framework für das React-Spektrum-Design als Headless-Formular rendern können.

### Übung

Lokales Repository mithilfe des React-Starter-Projekts einrichten:

1. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.

   ![](/help/forms/assets/screenshot2028115829.png)

1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zu **c:\git** Ordner

   ```Shell
   cd c:\git
   ```

1. Verwenden Sie den folgenden Befehl, um das React-Starter-Projekt des adaptiven Formulars zu klonen:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. Verwenden Sie die folgenden Befehle in der angegebenen Reihenfolge, um zum **react-starter-kit-aem-headless-forms** und öffnen Sie Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   Das Fenster Visual Studio Code wird geöffnet.

   ![](/help/forms/assets/screenshot2028117429.png)

So rendern Sie das in Ihrer Cloud Service-Veröffentlichungsumgebung gehostete Formular:

1. Benennen Sie die Datei env_template in .env -Datei um. Klicken Sie zum Umbenennen mit der rechten Maustaste auf die **env_template** und wählen Sie die **Umbenennen** -Option.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest. Speichern Sie nach dem Aktualisieren der Variablen die Datei.

   * **AEM_URL**: Geben Sie die URL der Veröffentlichungsumgebung des Cloud-Service an. Beispiel: `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: Geben Sie den Pfad des adaptiven Formulars an, das in der vorherigen Lektion erstellt wurde. Beispiel: `/content/forms/af/registration/`

      ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Öffnen Sie das Befehlsfenster, stellen Sie sicher, dass Sie sich im Ordner &quot;react-starter-kit-aem-headless-forms&quot;befinden, und führen Sie den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. Führen Sie im Fenster Eingabeaufforderung den folgenden Befehl aus:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   Der obige Befehl startet einen lokalen Entwicklungsserver, der die von AEM abgerufene Formulardefinition mit der Frontend-Bibliothek &quot;React-Spektrum&quot;per Headless-Implementierung rendert.

   >[!NOTE]
   >
   > 
   > Wenn nach der Ausführung des `npm start` Befehl für mehr als 3-4 Minuten, ändern Sie `localhost` in der Browser-URL auf 127.0.0.1 und Treffer **Eingabe**.

   ![](/help/forms/assets/screenshot2028118229.png)

Überprüfen wir die Ausführung der Regeln in dieser Headless-Form:

1. Wählen Sie die **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten.** -Option. Die nachfolgende Option zum Anwenden einer Kreditkarte ist deaktiviert.

   ![](/help/forms/assets/screenshot2028126229.png)

1. Deaktivieren **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten.** um die Kreditkartenoption zu aktivieren.

   ![](/help/forms/assets/screenshot2028126329.png)

Nehmen wir als Geschäftsbenutzer Änderungen am Formular auf dem Server vor und zeigen Sie die Änderungen automatisch im Headless-Formular an.

1. Öffnen Sie die AEM Forms-Verwaltungsoberfläche im Browser. Beispiel: [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Wählen Sie die **registrierung** Formular und klicken Sie auf **Bearbeiten.** Das Formular wird im Editor für adaptive Formulare geöffnet.

   ![](/help/forms/assets/screenshot2028118529.png)

1. Wählen Sie die **Telefonnummer** und klicken Sie auf **Symbol &quot;Bearbeiten&quot;(Bleistiftsymbol)** in der Symbolleiste. Wenn Sie die Popup-Symbolleiste nicht sehen können, wechseln Sie in den Bearbeitungsmodus, indem Sie auf **Bearbeiten** Schaltfläche oben rechts, von links nach **Vorschau** Schaltfläche.

   ![](/help/forms/assets/screenshot2028119629.png)

1. Ändern Sie den Titel in Mobiltelefonnummer. Klicken Sie auf eine leere Stelle im Formular und die am Formular vorgenommenen Änderungen werden gespeichert.

   ![](/help/forms/assets/screenshot2028119729.png)

Veröffentlichen wir das aktualisierte Formular, um die Änderungen in die Veröffentlichungsumgebung zu übertragen.

1. Wählen Sie im Tab Verwaltungsoberfläche von AEM Forms das Registrierungsformular aus und klicken Sie auf **Veröffentlichung rückgängig machen**. Wenn die Variable **Veröffentlichung rückgängig machen** auf, fahren Sie mit Schritt 3 fort, um die Änderungen direkt zu veröffentlichen.

   ![](/help/forms/assets/screenshot2028119829.png)

1. Klicken Sie auf **Veröffentlichung aufheben**. Klicken **Schließen** im entsprechenden Dialogfeld.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. Nachdem der Browser aktualisiert wurde, wählen Sie das Registrierungsformular aus und klicken Sie auf **Veröffentlichen**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. Klicken Sie auf **Veröffentlichen**. Klicken **Schließen** im entsprechenden Dialogfeld.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Aktualisieren Sie die Browser-Registerkarte mit dem Headless-Formular. Beachten Sie, dass die Bezeichnung für die Telefonnummer in Mobiltelefonnummer geändert wurde.

   ![](/help/forms/assets/screenshot2028120529.png)

1. Öffnen Sie das Fenster Eingabeaufforderung , das zum Starten des **react-starter-kit-aem-headless-forms** Projekt, drücken **Strg+C**, und geben Sie **Y** und drücken Sie die Eingabetaste, um den npm-Prozess zu beenden. Es ist wichtig, den npm-Server zu stoppen, damit er nicht mit dem nächsten Satz von Übungen in Konflikt gerät.

1. Schließen Sie die Fenster Visual Studio Code und Eingabeaufforderung .


## Lektion 5

### Ziel

Wiedergabe des Formulars als Headless-Formular über die Google Material-Benutzeroberfläche

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwickler, wie Sie das zuvor erstellte adaptive Formular mithilfe der Google Material-Benutzeroberfläche als Headless-Formular wiedergeben.

### Übung

Richten Sie das lokale Repository mithilfe des Starterprojekts der Materialbenutzeroberfläche ein:

1. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.

   ![](/help/forms/assets/screenshot2028115829.png)


1. Verwenden Sie in der Eingabeaufforderung den folgenden Befehl, um zu **c:\git** Ordner:

   ```Shell
   cd c:\git
   ```

1. Führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus, um einen Ordner mit dem Namen mui zu erstellen und mithilfe der folgenden Befehle zum Ordner mui zu navigieren:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Verwenden Sie den folgenden Befehl, um das React-Starter-Projekt des adaptiven Formulars zu klonen:

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. Verwenden Sie den folgenden Befehl in der angegebenen Reihenfolge, um zum **react-starter-kit-aem-headless-forms** und öffnen Sie den Code in Visual Studio Code:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

So rendern Sie das in Ihrer Cloud Service-Veröffentlichungsumgebung gehostete Formular:

1. Benennen Sie die **env_template** Datei in **.env** -Datei. Klicken Sie zum Umbenennen mit der rechten Maustaste auf die **env_template** Datei und wählen Sie **Umbenennen**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. Legen Sie die folgenden Werte für die Variablen in der .env-Datei fest. Speichern Sie nach dem Aktualisieren der Variablen die Datei. Verwenden Sie die **STRG + S** Wechseln Sie die Kombination, um die Datei zu speichern.

   * **AEM_URL**: Geben Sie die URL der Veröffentlichungsumgebung des Cloud-Service an. Beispiel: [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: Geben Sie den Pfad des adaptiven Formulars an, das in der vorherigen Lektion erstellt wurde. Beispiel: /content/forms/af/registration/

      ![](/help/forms/assets/screenshot2028126929.png)

1. Öffnen Sie das Befehlsfenster, um sicherzustellen, dass Sie sich im **react-starter-kit-aem-headless-forms** und führen Sie den folgenden Befehl aus:

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. Führen Sie im Fenster Eingabeaufforderung den folgenden Befehl aus:

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   Der Befehl startet einen lokalen Entwicklungsserver und rendert die von AEM abgerufene Formulardefinition per Frontend-Bibliothek der Google-Benutzeroberfläche.

   >[!NOTE]
   >
   >Wenn nach der Ausführung des `npm start` Befehl für mehr als 3-4 Minuten, ändern Sie `localhost` in der Browser-URL auf 127.0.0.1 und Treffer **Eingabe**.

   ![](/help/forms/assets/screenshot2028127229.png)

1. So bewerten Sie die Ausführung derselben Geschäftslogik in dieser Formularausgabe:

   Auswählen **Aktivieren Sie das Kontrollkästchen, um 5 % Rabatt zu erhalten.**. Die nachfolgende Option **Möchten Sie sich für das We.Finance Corporate Credit Card Formular bewerben?** wird deaktiviert.

   ![](/help/forms/assets/screenshot2028127329.png)

## Lektion 6

### Ziel

Erstellen Sie ein alternatives Erscheinungsbild des Headless-Formulars mithilfe der Komponentenvarianten der Materialbenutzeroberfläche

### Lektionskontext

In dieser Lektion erfahren Sie als Frontend-Entwickler, wie Sie mithilfe der Materialbenutzeroberfläche eine alternative Darstellung verschiedener Komponenten für das adaptive Formular erstellen, das zuvor vom Business-Anwender erstellt wurde.

### Übung

Aktualisieren Sie die Variation der Komponenten im Headless-Projekt. So ändern Sie die Variante der Texteingabekomponente der materiellen Benutzeroberfläche in `OutlinedInput`:

1. Navigieren Sie in Visual Code zur Texteingabekomponente, indem Sie die `index.tsx` Datei unter `src/components/textinput/index.tsx`.

1. Hinzufügen `//` am Anfang der Codezeile 103. Die Zeile wird in einen Kommentar umgewandelt.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Fügen Sie in Zeile 104 Folgendes hinzu, um eine andere Variante der Komponente zu verwenden und die Datei zu speichern. Verwenden Sie die **STRG + S** Wechseln Sie die Kombination, um die Datei zu speichern.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   Es ist wichtig, die richtige Groß-/Kleinschreibung für die Variante &quot;OutlineInput&quot;zu verwenden, da die Kompilierung andernfalls fehlschlagen würde. Die Kompilierung der lokalen Entwicklungsumgebung beginnt automatisch in der Eingabeaufforderung. Warten Sie, bis die folgende Meldung angezeigt wird

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Aktualisieren Sie den Browser, wenn er nicht automatisch aktualisiert wird, um zu sehen, wie die Texteingabe-Komponente eine andere Variante verwendet.

   ![](/help/forms/assets/screenshot2028127729.png)


   Diese Änderung erfolgt für Endbenutzer ohne Änderung der Formulardefinition auf dem AEM Forms-Server und ist spezifisch für den betreffenden Headless-Kanal. Beispiel: Webkanal in diesem Labor.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Schließen Sie Visual Studio Code und Eingabeaufforderung Windows.

## Häufig gestellte Fragen (FAQs)

+++ Ist der Assistent für adaptive Formulare öffentlich verfügbar?

Ja, es ist mit AEM Forms als Cloud Service verfügbar.

+++


+++ Sind Kernkomponenten öffentlich verfügbar?

Ja, die Kernkomponenten des adaptiven Forms sind mit AEM Forms als Cloud Service verfügbar.

+++

+++ Sind Headless-Formulare öffentlich verfügbar?

Ja, Headless-Formulare sind mit AEM Forms als Cloud Service verfügbar.

+++

+++ Benötigen Headless-Formulare eine separate Lizenz?

Nein, Headless-Formulare verwenden dieselbe Lizenzwertmetrik, die Anzahl der Formularübermittlungen.

+++

+++ Sind Kernkomponenten und Headless-Formulare in AEM 6.5 Forms verfügbar?

Ja, sowohl Kernkomponenten für adaptive Formulare als auch Headless-Formulare sind mit AEM Forms 6.5 Service Pack 16 und höher verfügbar.

+++


## Nächste Schritte

Nachdem Sie nun gelernt haben, wie Sie adaptive Formulare erstellen und über Headless-Formulare an mehrere Kanäle senden, sollten Sie versuchen, Ihre neuen Fähigkeiten in die Tat umzusetzen. Viel Spaß und machen Sie weiter, indem Sie außergewöhnliche Erlebnisse für die Datenerfassung erstellen und Ihren Endbenutzern, wo sie sind, im Maßstab bereitstellen.

## Ressourcen

* [Einführung in die Kernkomponenten des adaptiven Formulars](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [Erstellen eines adaptiven Formulars mit Kernkomponenten](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [Aktualisierungsstile für die auf Kernkomponenten basierende AF](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Headless-adaptive Formulare](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Verwenden des Headless-React-Starter-Kits](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)


