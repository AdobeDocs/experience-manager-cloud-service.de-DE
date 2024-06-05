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

* Sie müssen dem **AEM Administrator** [Produktprofil](/help/journey-onboarding/assign-profiles-aem.md) um die SecurBank-App zu installieren.
* Sie müssen [Node.js](https://nodejs.org) für die lokale Entwicklung installierte Version 20 oder höher.

## Installation von SecurBank {#installation}

Die Installation der SecurBank-App ist unkompliziert, aber da sie viele Bereiche AEM as a Cloud Service betrifft, sind eine Reihe von Schritten erforderlich. Im Folgenden finden Sie eine Übersicht der wichtigsten Schritte.

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

   * Standardoptionen bei Auswahl von **Lösungen und Add-ons**.
   * Weitere Informationen zum Erstellen eines Sandbox-Programms finden Sie im Dokument [Erstellen von Sandbox-Programmen.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)

### Klonen Sie das Git-Repository des Programms und aktualisieren Sie mit dem SecurBank AEM Projektinhalt. {#clone-and-update}

1. Öffnen Sie das Programm nach seiner Erstellung und öffnen Sie es auf der **Repositorys** Registerkarte, tippen oder klicken Sie auf die **Zugriff auf Repo Info** Schaltfläche zum Öffnen **Repository-Informationen** und die Anmeldeinformationen anzeigen, die für den Zugriff auf das Git-Repository für die Sandbox-Umgebung erforderlich sind.

   * Weitere Informationen zum Zugriff auf Ihre Repository-Informationen finden Sie im Dokument . [Zugreifen auf Repositorys.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

1. Verwenden der Anmeldeinformationen in der **Repository-Informationen** das Repository auf Ihrem lokalen Computer klonen.

1. Suchen Sie den Ordner des lokalen Klons, öffnen Sie ihn und löschen Sie alle Inhalte mit Ausnahme der ausgeblendeten/Punktdateien.

1. Rufen Sie den neuesten SecurBank AEM Projektcode von GitHub unter ab. [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank) durch Klicken auf **Code** und dann **ZIP herunterladen** in der Dropdown-Liste.

1. Dekomprimieren Sie den Inhalt der ZIP-Datei in Ihrem lokalen Dateisystem und verschieben Sie sie in den jetzt leeren Ordner des lokalen Klons des Sandbox-Programms.

1. Wechseln Sie mit dem Terminal zum Ordner des geklonten Projekts, übertragen Sie den gesamten Inhalt und pushen Sie ihn auf Git.

   1. `git add --all`
   1. `git commit -m "Adding SecurBank app code"`
   1. `git push`

### Führen Sie die Pipeline aus, um das AEM Projekt SecurBank bereitzustellen. {#run-pipeline}

Wenn das AEM-Projekt für SecurBank an das Sandbox-Repository übermittelt wird, kann es mit einer Pipeline bereitgestellt werden.

1. Kehren Sie zu **Übersicht** Registerkarte Ihres Sandbox-Programms in Cloud Manager erstellen und die produktionsfremde Pipeline für den vollständigen Stapel ausführen.

   * Deaktivieren Sie alle Optionen für die Pipeline-Ausführung.
   * Weitere Informationen zum Ausführen von Pipelines finden Sie im Dokument . [Verwalten von Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines)

### Rufen Sie Cloud Manager-Anmeldeinformationen für die Entwicklung lokaler Web-Apps ab. {#retrieve-credentials}

Bevor Sie die SecurBank-App ausführen können, benötigen Sie Cloud Manager-Anmeldeinformationen, um die App mit Cloud Manager zu verbinden.

1. Kehren Sie während der Ausführung der Pipeline zum **Übersicht** Registerkarte in Cloud Manager, tippen oder klicken Sie auf die Suchschaltfläche neben dem Umgebungsnamen und wählen Sie **Entwicklerkonsole**.

1. Wählen Sie in der Entwicklerkonsole die **Integrationen** und dann **Lokaler Token** Registerkarte und tippen oder klicken **Abrufen des lokalen Entwicklungstokens**.

1. Eine JSON-Datei wird mit dem Zugriffstoken erstellt. Kopieren Sie nur das Token selbst (die verbleibende JSON ist nicht erforderlich) an einen sicheren Speicherort, um es in einem zukünftigen Schritt zu verwenden, bevor Sie die Developer Console schließen und zu Cloud Manager zurückkehren.

1. Zurück in Cloud Manager, auf der **Übersicht** klicken Sie mit der rechten Maustaste auf die URL der Umgebung, um sie zu kopieren und an einem sicheren Ort zu speichern, um sie in einem zukünftigen Schritt zu verwenden.

### Laden Sie die SecurBank-Webanwendung herunter und konfigurieren Sie sie. {#download-web-app}

Jetzt können Sie die SecurBank-Webanwendung herunterladen und konfigurieren.

1. Abrufen des neuesten SecurBank-App-Codes von GitHub unter [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events) durch Klicken auf **Code** und dann **ZIP herunterladen** in der Dropdown-Liste.

1. Dekomprimieren Sie den Inhalt der ZIP-Datei auf Ihrem lokalen Dateisystem.

1. Starten Sie den gewünschten Code-Editor und öffnen Sie die ausgeblendete Umgebungsdatei im SecurBank-App-Projekt unter `summit-2024-l425-ue-z-final-with-events/react-app/.env`.

1. Nehmen Sie die folgenden Änderungen an der `.env` und speichern Sie die Änderungen.

   * Für `REACT_APP_HOST_URI` Fügen Sie den Wert der zuvor kopierten URL Ihrer Umgebung ein.
   * Für `REACT_APP_DEV_TOKEN` Fügen Sie den Wert des zuvor kopierten lokalen Entwicklungstokens ein.

### Führen Sie die SecurBank-Webanwendung aus. {#run-web-app}

Wenn alles sowohl in Cloud Manager als auch lokal eingerichtet ist, können Sie die SecurBank-Webanwendung ausführen.

1. Navigieren Sie in der Befehlszeile Ihres lokalen Computers zum `react-app` Ordner des von Ihnen heruntergeladenen und dekomprimierten SecurBank-App-Projekts.

1. In der `react-app` Ordner installieren Sie die SecurBank-App mit der `node -i` Befehl.

1. Starten Sie nach der Installation die SecurBank-App mit der `npm start` Befehl.

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

   * Und ein Browserfenster, das zur URL geöffnet ist `https://localhost:3000`.

      * Beachten Sie, dass dies zu Entwicklungszwecken dient und daher kein gültiges Zertifikat bereitgestellt wird. Daher müssen Sie möglicherweise Ihren Browser informieren, damit er auf die Seite zugreifen kann.

Herzlichen Glückwunsch! Die SecurBank-App sollte jetzt in Ihrem Browser erfolgreich ausgeführt werden.

Wenn der Inhalt noch nicht angezeigt wird, stellen Sie sicher, dass die Variable **Bereitstellen in der Entwicklung** Pipeline, die Sie erfolgreich ausgeführt haben.

![SecurBank-App im Browser](assets/securbank.png)
