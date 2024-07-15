---
title: SecurBank-Beispielanwendung für den universellen Editor
description: Erfahren Sie mehr über den universellen Editor mit praxisnaher Erfahrung, indem Sie die SecurBank-App verwenden, die die Leistung, Flexibilität und Benutzerfreundlichkeit des universellen Editors demonstriert, um die Inhaltserstellung zu beschleunigen.
exl-id: 97e1395f-b51e-4cee-b1d0-2466a08f96af
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 1%

---

# SecurBank-Beispielanwendung für den universellen Editor {#securbank}

Erfahren Sie mehr über den universellen Editor mit praxisnaher Erfahrung, indem Sie die SecurBank-App verwenden, die die Leistung, Flexibilität und Benutzerfreundlichkeit des universellen Editors demonstriert, um die Inhaltserstellung zu beschleunigen.

## Voraussetzungen {#prerequisites}

* Sie müssen dem **AEM Administrator** [Produktprofil](/help/journey-onboarding/assign-profiles-aem.md) zugewiesen sein, um die SecurBank-App zu installieren.
* Für die lokale Entwicklung muss [Node.js](https://nodejs.org) Version 20 oder höher installiert sein.

## Installation von SecurBank {#installation}

Die Installation der SecurBank-App ist unkompliziert, aber da sie viele Bereiche von AEM as a Cloud Service berührt, sind eine Reihe von Schritten erforderlich. Im Folgenden finden Sie eine Übersicht der wichtigsten Schritte.

1. [Erstellen Sie ein Sandbox-Programm in Cloud Manager.](#create-sandbox-program)
1. [Klonen Sie das Git-Repository des Programms und aktualisieren Sie mit dem SecurBank AEM Projektinhalt.](#clone-and-update)
1. [Führen Sie die Pipeline aus, um das AEM Projekt SecurBank bereitzustellen.](#run-pipeline)
1. [Rufen Sie Cloud Manager-Anmeldeinformationen für die Entwicklung lokaler Web-Apps ab.](#retrieve-credentials)
1. [Laden Sie die SecurBank-Webanwendung herunter und konfigurieren Sie sie.](#download-web-app)
1. [Führen Sie die SecurBank-Webanwendung aus.](#run-web-app)

In den folgenden Abschnitten werden die einzelnen erforderlichen Aufgaben beschrieben.

### Erstellen Sie ein Sandbox-Programm in Cloud Manager. {#create-sandbox-program}

Sie benötigen ein neues Cloud Manager-Programm, in dem Sie SecurBank installieren können.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus

1. Erstellen Sie ein neues Sandbox-Programm für die SecurBank-App.

   * Verwenden Sie die Standardoptionen bei Auswahl von **Lösungen und Add-ons**.
   * Weitere Informationen zum Erstellen eines Sandbox-Programms finden Sie im Dokument [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) .

### Klonen Sie das Git-Repository des Programms und aktualisieren Sie mit dem SecurBank AEM Projektinhalt. {#clone-and-update}

1. Nachdem das Programm erstellt wurde, öffnen Sie es und tippen oder klicken Sie auf der Registerkarte **Repositorys** auf die Schaltfläche **Zugriff auf Repo Info** , um das Dialogfeld **Repository Info** zu öffnen und die Anmeldeinformationen anzuzeigen, die für den Zugriff auf das Git-Repository für die Sandbox-Umgebung erforderlich sind.

   * Weitere Informationen zum Zugriff auf Ihre Repository-Informationen finden Sie im Dokument &quot;[Zugreifen auf Repositorys&quot;](/help/implementing/cloud-manager/managing-code/accessing-repos.md)&quot;.

1. Klonen Sie mithilfe der Anmeldeinformationen im Dialogfeld **Repository Info** das Repository auf Ihrem lokalen Computer.

1. Suchen Sie den Ordner des lokalen Klons, öffnen Sie ihn und löschen Sie alle Inhalte mit Ausnahme der ausgeblendeten/Punktdateien.

1. Rufen Sie den neuesten AEM-Projektcode von SecurBank unter [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank) von GitHub ab, indem Sie auf **Code** und dann im Dropdown-Menü auf **ZIP herunterladen** klicken.

1. Dekomprimieren Sie den Inhalt der ZIP-Datei in Ihrem lokalen Dateisystem und verschieben Sie sie in den jetzt leeren Ordner des lokalen Klons des Sandbox-Programms.

1. Wechseln Sie mit dem Terminal zum Ordner des geklonten Projekts, übertragen Sie den gesamten Inhalt und pushen Sie ihn auf Git.

   1. `git add --all`
   1. `git commit -m "Adding SecurBank app code"`
   1. `git push`

### Führen Sie die Pipeline aus, um das AEM Projekt SecurBank bereitzustellen. {#run-pipeline}

Wenn das AEM-Projekt für SecurBank an das Sandbox-Repository übermittelt wird, kann es mit einer Pipeline bereitgestellt werden.

1. Kehren Sie zur Registerkarte **Übersicht** Ihres Sandbox-Programms in Cloud Manager zurück und führen Sie die produktionsfremde Vollstapelproduktions-Pipeline aus.

   * Deaktivieren Sie alle Optionen für die Pipeline-Ausführung.
   * Weitere Informationen zum Ausführen von Pipelines finden Sie im Dokument [Verwalten von Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) .

### Rufen Sie Cloud Manager-Anmeldeinformationen für die Entwicklung lokaler Web-Apps ab. {#retrieve-credentials}

Bevor Sie die SecurBank-App ausführen können, benötigen Sie Cloud Manager-Anmeldeinformationen, um die App mit Cloud Manager zu verbinden.

1. Kehren Sie während der Ausführung der Pipeline zur Registerkarte **Übersicht** in Cloud Manager zurück, tippen oder klicken Sie auf die Suchschaltfläche neben dem Umgebungsnamen und wählen Sie **Developer Console** aus.

1. Wählen Sie in der Developer Console die Registerkarte **Integrationen**, dann die Registerkarte **Lokales Token** und tippen oder klicken Sie auf **Lokales Entwicklungstoken abrufen**.

1. Eine JSON-Datei wird mit dem Zugriffstoken erstellt. Kopieren Sie nur das Token selbst (die verbleibende JSON ist nicht erforderlich) an einen sicheren Speicherort, um es in einem zukünftigen Schritt zu verwenden, bevor Sie die Developer Console schließen und zu Cloud Manager zurückkehren.

1. Klicken Sie in Cloud Manager auf der Registerkarte **Überblick** mit der rechten Maustaste auf die URL der Umgebung, um sie zu kopieren und für einen zukünftigen Schritt an einem sicheren Ort zu speichern.

### Laden Sie die SecurBank-Webanwendung herunter und konfigurieren Sie sie. {#download-web-app}

Jetzt können Sie die SecurBank-Webanwendung herunterladen und konfigurieren.

1. Rufen Sie den neuesten SecurBank-App-Code von GitHub unter [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events) ab, indem Sie auf **Code** klicken und dann im Dropdown-Menü auf **ZIP herunterladen** klicken.

1. Dekomprimieren Sie den Inhalt der ZIP-Datei auf Ihrem lokalen Dateisystem.

1. Starten Sie Ihren bevorzugten Code-Editor und öffnen Sie die ausgeblendete Umgebungsdatei im SecurBank-App-Projekt unter `summit-2024-l425-ue-z-final-with-events/react-app/.env`.

1. Nehmen Sie die folgenden Änderungen an der Datei `.env` vor und speichern Sie die Änderungen.

   * Fügen Sie für `REACT_APP_HOST_URI` den Wert der zuvor kopierten URL Ihrer Umgebung ein.
   * Fügen Sie für `REACT_APP_DEV_TOKEN` den Wert des zuvor kopierten lokalen Entwicklungstokens ein.

### Führen Sie die SecurBank-Webanwendung aus. {#run-web-app}

Wenn alles sowohl in Cloud Manager als auch lokal eingerichtet ist, können Sie die SecurBank-Webanwendung ausführen.

1. Navigieren Sie in der Befehlszeile Ihres lokalen Computers zum Ordner &quot;`react-app`&quot;des von Ihnen heruntergeladenen und dekomprimierten SecurBank-App-Projekts.

1. Installieren Sie in Ihrem Ordner `react-app` die SecurBank-App mit dem Befehl `node -i` .

1. Starten Sie nach der Installation die SecurBank-App mit dem Befehl `npm start` .

1. Wenn die Installation und der Start erfolgreich waren, sehen Sie Folgendes:

* Die folgende Ausgabe im Terminal.

  ```text
  Compiled successfully!
  
  You can now view securbank in the browser.
  
    Local:            https://localhost:3000
    On Your Network:  https://192.168.1.15:3000
  
  Note that the development build is not optimized.
  To create a production build, use npm run build.
  
  webpack compiled successfully
  ```

   * Und ein Browserfenster öffnet sich zur URL `https://localhost:3000`.

      * Beachten Sie, dass dies zu Entwicklungszwecken dient und daher kein gültiges Zertifikat bereitgestellt wird. Daher müssen Sie möglicherweise Ihren Browser informieren, damit er auf die Seite zugreifen kann.

Herzlichen Glückwunsch! Die SecurBank-App sollte jetzt in Ihrem Browser erfolgreich ausgeführt werden.

Wenn der Inhalt noch nicht angezeigt wird, stellen Sie sicher, dass die von Ihnen ausgeführte Pipeline **In der Entwicklung bereitstellen** erfolgreich abgeschlossen wurde.

![SecurBank-App im Browser](assets/securbank.png)
