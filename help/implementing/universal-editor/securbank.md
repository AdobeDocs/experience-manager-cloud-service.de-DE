---
title: SecurBank-Beispielanwendung für den universellen Editor
description: Erfahren Sie mehr über den universellen Editor anhand eines praktischen Beispiels mit der SecurBank-Anwendung, die die Leistung, Flexibilität und Benutzerfreundlichkeit des universellen Editors für eine schnellere Inhaltserstellung zeigt.
exl-id: 97e1395f-b51e-4cee-b1d0-2466a08f96af
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '902'
ht-degree: 100%

---

# SecurBank-Beispielanwendung für den universellen Editor {#securbank}

Erfahren Sie mehr über den universellen Editor anhand eines praktischen Beispiels mit der SecurBank-Anwendung, die die Leistung, Flexibilität und Benutzerfreundlichkeit des universellen Editors für eine schnellere Inhaltserstellung zeigt.

## Voraussetzungen {#prerequisites}

* Sie müssen dem **AEM-Admin**-[Produktprofil](/help/journey-onboarding/assign-profiles-aem.md) zugewiesen sein, um die SecurBank-Anwendung installieren zu können.
* Für die lokale Entwicklung muss [Node.js](https://nodejs.org) der Version 20 oder höher installiert sein.

## Installieren von SecurBank {#installation}

Die Installation der SecurBank-Anwendung ist an sich unkompliziert. Aber da sie viele Bereiche von AEM as a Cloud Service berührt, ist eine Reihe von Schritten erforderlich. Nachstehend finden Sie eine Übersicht der wesentlichen Schritte:

1. [Erstellen eines Sandbox-Programms in Cloud Manager](#create-sandbox-program)
1. [Klonen des Git-Repositorys des Programms und Aktualisieren des Repositorys mit SecurBank-AEM-Projektinhalten](#clone-and-update)
1. [Ausführen der Pipeline zur Bereitstellung des SecurBank-AEM-Projekts](#run-pipeline)
1. [Abrufen von Cloud Manager-Anmeldedaten für die lokale Entwicklung von Web-Anwendungen](#retrieve-credentials)
1. [Herunterladen und Konfigurieren der SecurBank-Web-Anwendung](#download-web-app)
1. [Ausführen der SecurBank-Web-Anwendung](#run-web-app)

In den folgenden Abschnitten werden die einzelnen erforderlichen Aufgaben beschrieben.

### Erstellen eines Sandbox-Programms in Cloud Manager. {#create-sandbox-program}

Sie benötigen ein neues Cloud Manager-Programm, in dem Sie SecurBank installieren können.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/ ) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus

1. Erstellen Sie ein neues Sandbox-Programm für die SecurBank-Anwendung.

   * Verwenden Sie die Standardoptionen bei Auswahl von **Lösungen und Add-ons**.
   * Weitere Informationen zum Erstellen eines Sandbox-Programms finden Sie im Dokument [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).

### Klonen des Git-Repositorys des Programms und Aktualisieren des Repositorys mit SecurBank-AEM-Projektinhalten. {#clone-and-update}

1. Nachdem das Programm erstellt wurde, öffnen Sie es und tippen oder klicken Sie auf der Registerkarte **Repositorys** auf die Schaltfläche **Auf Repository-Informationen zugreifen**. Daraufhin wird das Dialogfeld **Repository-Informationen** mit den Anmeldedaten angezeigt, die für den Zugriff auf das Git-Repository für die Sandbox-Umgebung erforderlich sind.

   * Weitere Informationen zum Zugriff auf Ihre Repository-Informationen finden Sie im Dokument [Zugreifen auf Repositorys](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Klonen Sie mithilfe der Anmeldedaten im Dialogfeld **Repository-Informationen** das Repository auf Ihrem lokalen Computer.

1. Suchen Sie den Ordner des lokalen Klons, öffnen Sie ihn und löschen Sie alle Inhalte bis auf die ausgeblendeten (DOT-)Dateien.

1. Rufen Sie den neuesten AEM-Projekt-Code von SecurBank unter [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank) von GitHub ab, indem Sie auf **Code** und dann im Dropdown-Menü auf **Download ZIP** (ZIP herunterladen) klicken.

1. Dekomprimieren Sie den Inhalt der ZIP-Datei auf Ihrem lokalen Dateisystem und verschieben Sie ihn in den jetzt leeren Ordner des lokalen Klons des Sandbox-Programms.

1. Wechseln Sie mit dem Terminal zum Ordner des geklonten Projekts, committen Sie den gesamten Inhalt und pushen Sie ihn auf Git.

   1. `git add --all`
   1. `git commit -m "Adding SecurBank app code"`
   1. `git push`

### Ausführen der Pipeline zur Bereitstellung des SecurBank-AEM-Projekts. {#run-pipeline}

Wenn das AEM-Projekt für SecurBank an das Sandbox-Repository übertragen wurde, kann es mit einer Pipeline bereitgestellt werden.

1. Kehren Sie zur Registerkarte **Übersicht** Ihres Sandbox-Programms in Cloud Manager zurück und führen Sie die produktionsfremde Fullstack-Pipeline aus.

   * Deaktivieren Sie alle Optionen für die Pipeline-Ausführung.
   * Weitere Informationen zum Ausführen von Pipelines finden Sie im Dokument [Verwalten von Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines).

### Abrufen von Cloud Manager-Anmeldedaten für die lokale Web-Anwendungsentwicklung. {#retrieve-credentials}

Bevor Sie die SecurBank-Anwendung ausführen können, benötigen Sie Cloud Manager-Anmeldedaten, um die Anwendung mit Cloud Manager zu verbinden.

1. Kehren Sie während der Ausführung der Pipeline zur Registerkarte **Übersicht** in Cloud Manager zurück, tippen oder klicken Sie neben dem Umgebungsnamen auf die Schaltfläche mit den Auslassungspunkten und wählen Sie **Entwicklerkonsole** aus.

1. Wählen Sie in der Developer Console die Registerkarte **Integrationen** und dann die Registerkarte **Lokales Token** aus. Tippen oder klicken Sie anschließend auf **Lokales Entwicklungs-Token abrufen**.

1. Es wird eine JSON-Datei mit dem Zugriffs-Token erstellt. Kopieren Sie nur das Token selbst (die verbleibende JSON-Datei ist nicht erforderlich) an einen sicheren Speicherort, um es in einem zukünftigen Schritt zu verwenden, bevor Sie die Developer Console schließen und zu Cloud Manager zurückkehren.

1. Klicken Sie in Cloud Manager auf der Registerkarte **Übersicht** mit der rechten Maustaste auf die URL der Umgebung, um sie zu kopieren und für einen zukünftigen Schritt an einem sicheren Ort zu speichern.

### Herunterladen und Konfigurieren der SecurBank-Web-Anwendung. {#download-web-app}

Nun können Sie die SecurBank-Web-Anwendung herunterladen und konfigurieren.

1. Rufen Sie den neuesten SecurBank-Anwendungs-Code von GitHub unter [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events) ab, indem Sie auf **Code** und dann im Dropdown-Menü auf **Download ZIP** (ZIP herunterladen) klicken.

1. Dekomprimieren Sie den Inhalt der ZIP-Datei auf Ihr lokales Dateisystem.

1. Starten Sie Ihren bevorzugten Code-Editor und öffnen Sie die ausgeblendete Umgebungsdatei im SecurBank-Anwendungsprojekt unter `summit-2024-l425-ue-z-final-with-events/react-app/.env`.

1. Nehmen Sie die folgenden Änderungen an der `.env`-Datei vor und speichern Sie die Änderungen.

   * Fügen Sie für `REACT_APP_HOST_URI` den Wert der zuvor kopierten URL Ihrer Umgebung ein.
   * Fügen Sie für `REACT_APP_DEV_TOKEN` den Wert des zuvor kopierten lokalen Entwicklungs-Tokens ein.

### Ausführen der SecurBank-Web-Anwendung {#run-web-app}

Wenn alles sowohl in Cloud Manager als auch lokal eingerichtet ist, können Sie die SecurBank-Web-Anwendung ausführen.

1. Navigieren Sie in der Befehlszeile Ihres lokalen Computers zum Ordner `react-app` des von Ihnen heruntergeladenen und dekomprimierten SecurBank-Anwendungsprojekts.

1. Installieren Sie in Ihrem Ordner `react-app` die SecurBank-Anwendung mit dem Befehl `node -i`.

1. Starten Sie nach der Installation die SecurBank-Anwendung mit dem Befehl `npm start`.

1. Wenn die Installation und der Start erfolgreich waren, sehen Sie Folgendes:

* Diese Ausgabe im Terminal:

  ```text
  Compiled successfully!
  
  You can now view securbank in the browser.
  
    Local:            https://localhost:3000
    On Your Network:  https://192.168.1.15:3000
  
  Note that the development build is not optimized.
  To create a production build, use npm run build.
  
  webpack compiled successfully
  ```

   * Und ein mit der URL `https://localhost:3000` geöffnetes Browser-Fenster.

      * Beachten Sie, dass dies zu Entwicklungszwecken dient und daher kein gültiges Zertifikat bereitgestellt wird. Möglicherweise müssen Sie also Ihren Browser anweisen, einen Zugriff auf die Seite zuzulassen.

Herzlichen Glückwunsch! Die SecurBank-Anwendung sollte nun in Ihrem Browser erfolgreich ausgeführt werden.

Wenn der Inhalt noch nicht angezeigt wird, stellen Sie sicher, dass die von Ihnen ausgeführte Pipeline **Bereitstellung für Entwickler** erfolgreich abgeschlossen wurde.

![SecurBank-Anwendung im Browser](assets/securbank.png)
