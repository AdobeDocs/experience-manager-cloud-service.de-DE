---
title: Erste Schritte mit AEM Forms Edge Delivery Services - Tutorial für Entwickler
description: Dieses Tutorial hilft Ihnen, ein neues Adobe Experience Manager Forms-Projekt (AEM) einzurichten. In zehn bis zwanzig Minuten haben Sie Ihre eigenen Formulare erstellt.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 2aa70e78764616f41fe64e324c017873cfba1d5b
workflow-type: tm+mt
source-wordcount: '1770'
ht-degree: 1%

---


# Erste Schritte – Entwicklertutorial

Im heutigen digitalen Zeitalter ist die Erstellung benutzerfreundlicher Formulare für jedes Unternehmen von entscheidender Bedeutung. Mit AEM Forms Edge Delivery Services (EDS) können Sie Formulare mit vertrauten Tools wie Google Docs und Microsoft Office erstellen.

Diese Formulare senden Daten direkt an eine Microsoft Excel- oder Google Tabellen-Datei, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um gesendete Daten einfach zu verarbeiten oder einen bestehenden Geschäftsarbeitsablauf zu initiieren.

AEM Forms bietet einen Block, der als Adaptiver Forms-Block bezeichnet wird und mit dem Sie mühelos Formulare erstellen können, um erfasste Daten zu erfassen und zu speichern. Sie können ein neues AEM-Projekt erstellen, das bereits mit dem adaptiven Forms-Block ausgestattet ist, oder den Adaptive Forms-Block zu einem vorhandenen AEM hinzufügen.

Dieses Tutorial zu AEM Forms führt Sie durch das Erstellen, Anzeigen einer Vorschau und Veröffentlichen Ihres eigenen benutzerdefinierten Formulars mit einem neuen Adobe Experience Manager (AEM) Forms-Projekt. Außerdem lernen Sie, adaptive Forms-Bausteine zu einem bestehenden AEM hinzuzufügen.

* **[Erstellen Sie ein neues AEM-Projekt, das bereits mit Adaptive Forms Block ausgestattet ist.](#create-a-new-eds-project-pre-equipped-with-adaptive-forms-block)**
* **[Adaptiven Forms-Block zu einem bestehenden AEM hinzufügen](#add-adaptive-forms-block-to-an-existing-eds-project)**



## Voraussetzungen

* Sie verfügen über ein GitHub-Konto und verstehen die Git-Grundlagen.
* Sie haben ein Google- oder Microsoft SharePoint-Konto.
* Sie verstehen die Grundlagen von HTML, CSS und JavaScript.
* Sie haben Node/npm für die lokale Entwicklung installiert.

**Kopf hoch!** In diesem Tutorial werden macOS, Chrome und Visual Studio Code verwendet. Während die Schritte für andere Setups angepasst werden können, unterscheiden sich die Screenshots und spezifischen Elemente der Benutzeroberfläche möglicherweise je nach Betriebssystem, Browser und Code-Editor.


## Erstellen Sie ein neues AEM-Projekt, das bereits mit Adaptive Forms Block ausgestattet ist.

Die AEM Forms-Vorlage für Bausteinvorlagen ermöglicht einen schnellen Einstieg in ein AEM Projekt, das mit dem Adaptiven Forms-Block vorkonfiguriert ist. Dies ist die schnellste und einfachste Methode, AEM Best Practices zu befolgen und direkt beim Erstellen Ihrer Formulare zu beginnen.

### Erste Schritte mit der AEM Forms-Vorlage für Vorlagen für Vorlagen für Vorlagen

1. Erstellen Sie ein GitHub-Repository für Ihr AEM Projekt. Erstellen des Repositorys:
   1. Navigieren Sie zu [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![AEM Forms-Vorlage](/help/edge/assets/aem-forms-boilerplate.png)
   1. Klicken Sie auf **Verwenden Sie diese Vorlage** und wählen Sie die **Neues Repository erstellen** -Option. Der Bildschirm zum Erstellen eines neuen Repositorys wird geöffnet.

      ![Erstellen eines neuen Repositorys mithilfe von AEM Forms-Vorlage](/help/edge/assets/create-new-repository-using-aem-forms-boilerplate.png)

   1. Wählen Sie im Bildschirm &quot;Neues Repository erstellen&quot;die Option **owner** und geben Sie **Repository-Name** . Adobe empfiehlt, dass das Repository auf **Öffentlich**. Wählen Sie also die **öffentlich** und klicken Sie auf **Repository erstellen**.

   ![Repository auf &quot;Öffentlich&quot;festlegen](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. Installieren Sie die GitHub-App zur AEM Codesynchronisierung auf Ihrem Repository. So installieren Sie:
   1. Navigieren Sie zu [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Wählen Sie im Bildschirm AEM Codesynchronisierung installieren die Option **Nur Repositorys auswählen** und wählen Sie das neu erstellte Repository aus. Klicken Sie auf „Speichern“.

   ![Repository auf &quot;Öffentlich&quot;festlegen](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

   >[!NOTE]
   >
   >
   > Wenn Sie Github Enterprise mit IP-Filterung verwenden, können Sie die folgende IP zur Zulassungsliste hinzufügen: 3.227.118.73

   Herzlichen Glückwunsch! Sie haben eine neue Website, die auf `https://<branch>--<repo>--<owner>.hlx.page/`.

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repository.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.

   Wenn der Zweigname beispielsweise `main`, ist das Repository `wefinance`, und der Eigentümer ist `wkndforms`, würde die Website unter [https://main—wefinance—wkndforms.hlx.page/](https://main--wefinance--wkndforms.hlx.page/).



### Verknüpfen Ihrer eigenen Inhaltsquelle

Ihr neu erstelltes Github-Repository verweist auf [Beispielinhalt, der im Ordner &quot;Google Drive&quot;gespeichert ist](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_). Dieser schreibgeschützte Inhalt bietet einen guten Ausgangspunkt für Ihre Formulare. Sie können es in Ihr eigenes Google-Laufwerk kopieren und an Ihre Anforderungen anpassen.

![Beispielinhalt auf dem Google-Laufwerk](/help/edge/assets/folder-with-sample-content.png)

So kopieren Sie den Beispielinhalt in Ihren eigenen Inhaltsordner und verweisen Ihr Github-Repository auf Ihren eigenen Inhaltsordner:

1. Erstellen Sie einen neuen Ordner speziell für Ihre AEM in Google Drive oder Microsoft SharePoint. In diesem Dokument wird ein Ordner verwendet, der in Microsoft SharePoint erstellt wurde.

1. Geben Sie den Ordner für den Adobe Experience Manager-Benutzer frei (helix@adobe.com).

   ![Verwenden Sie die Option Zugriff verwalten , um Ordner für AEM Benutzer - SharePoint freizugeben.](/help/edge/assets/share-folder-with-aem-user.png)

   ![Verwenden Sie die Option Zugriff verwalten , um Ordner für AEM Benutzer freizugeben - Google Drive](/help/edge/assets/share-google-drive-folder.png)


   Stellen Sie sicher, dass Sie dem Adobe Experience Manager-Benutzer Bearbeitungsrechte für den Ordner zugewiesen haben.

   ![Ordner für AEM Benutzer freigeben, Bearbeitungsrechte bereitstellen SharePoint](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png)

   ![Ordner für AEM Benutzer freigeben, Bearbeitungsrechte bereitstellen - Google Drive](/help/edge/assets/add-aem-user-google-folder.png)

1. Kopieren Sie die [Beispielinhalt, der im Ordner &quot;Google Drive&quot;gespeichert ist](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_) in Ihren Ordner. So kopieren Sie:

   1. Laden Sie die Dateien zusammen herunter oder laden Sie einzelne Dateien herunter.

      ![Beispielinhalt herunterladen](/help/edge/assets/download-sample-content.png)

      Die `index`, `nav`, und `footer` -Dateien definieren das grundlegende Layout Ihrer Seiten und ändern sich im gesamten Projekt nur selten. Sie haben auch eine bestimmte Struktur, die sich von den meisten anderen Inhaltsdateien unterscheidet. Indem Sie sich diese Dateien ansehen, werden Sie ein Gefühl dafür bekommen, wie Inhalte in AEM Projekten organisiert werden.


   1. Laden Sie diese Dateien in den Ordner Microsoft SharePoint oder Google Drive hoch.

      ![Beispielinhalt auf dem Google-Laufwerk](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      Stellen Sie sicher, dass Sie die  `enquiry` Blätter aus dem Beispielinhalt in Ihren Ordner auf Google Drive oder Microsoft SharePoint. Sie enthält die Struktur für ein Beispielformular.

1. Nachdem Sie Ihren Inhaltsordner eingerichtet haben, ist es an der Zeit, ihn mit Ihrem Projekt auf GitHub zu verknüpfen, das Sie zuvor mit AEM Forms-Vorlage erstellt haben. So verbinden Sie sich:

   1. Wechseln Sie zum GitHub-Repository, das Sie zuvor mit AEM Forms Boilerplate erstellt haben.
   1. Öffnen Sie `fstab.yaml` zur Bearbeitung.
   1. Ersetzen Sie die vorhandene Referenz durch den Pfad zum Ordner, den Sie für den AEM Benutzer freigegeben haben (helix@adobe.com).

      ![Beispielinhalt auf dem Google-Laufwerk](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Wenn Sie Microsoft SharePoint verwenden, verwendet der Ordnerpfad das folgende Format:

      ```HTML
      https://<tenant>.sharepoint.com/sites/  <sp-site>/Shared%20Documents/<folder-name>
      ```

      Beispiel:

      ```HTML
      https://adobe.sharepoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Weitere Informationen zum Verwalten von Dateien mit in Microsoft SharePoint finden Sie unter [Verwendung von Adobe Sharepoint](https://www.aem.live/docs/setup-customer-sharepoint).



   1. Aktualisieren bestätigen `fsatb.yaml` -Datei, sobald Sie die Referenz aktualisiert haben und alles gut aussieht. Wenn Build-Probleme auftreten, lesen Sie [Beheben von GitHub-Build-Problemen](#troubleshooting-github-build-issues).



      ![Aktualisierte Datei &quot;fsatab.yaml&quot;bestätigen](/help/edge/assets/commit-updated-fstab-yaml.png)

      Dadurch wird Ihr Inhaltsordner mit Ihrer Website verbunden. Nach der Aktualisierung des Verweises treten möglicherweise anfänglich Fehler vom Typ &quot;404 nicht gefunden&quot;auf. Dies liegt daran, dass Ihre Inhalte noch nicht in der Vorschau angezeigt wurden. Im nächsten Abschnitt wird erläutert, wie Sie mit der Bearbeitung und Vorschau Ihres Inhalts beginnen können.

      ![Aktualisierte Datei &quot;fsatab.yaml&quot;bestätigen](/help/edge/assets/aem-forms-project-folder-error.png)

### Vorschau erstellen und Inhalt veröffentlichen

Nach Abschluss des letzten Schritts ist Ihre neue Inhaltsquelle nicht leer, sie wird jedoch erst auf Ihrer Website sichtbar sein, wenn sie in die Vorschau- oder Live-Phasen weitergeleitet wird. Derzeit kann dies zu 404-Fehlern führen.

So zeigen Sie eine Vorschau von nicht veröffentlichten Inhalten an:

1. Installieren Sie die Chrome-Erweiterung namens [AEM Sidekick](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo).

   ![Installieren von AEM Sidekick](/help/edge/assets/install-aem-sidekick.png)

   Nachdem Sie die Erweiterung in Chrome installiert haben, vergessen Sie nicht, sie zu veröffentlichen. Dies erleichtert die Suche.

   ![Pin AEM Sidekick](/help/edge/assets/pin-aem-sidekick.png)

1. Um die Sidekick Chrome-Erweiterung einzurichten, wechseln Sie zum Ordner &quot;Google Drive&quot;oder &quot;Microsoft SharePoint&quot;und klicken Sie mit der rechten Maustaste auf das Erweiterungssymbol in der Browser-Symbolleiste und wählen Sie `Add this project`.

   ![AEM Sidekick - Hinzufügen eines Projekts](/help/edge/assets/aem-sidekick-add-a-project.png)

   Sobald die Erweiterung installiert und Ihr Projekt hinzugefügt wurde, können Sie Ihre Inhalte auf Ihrem Google-Laufwerk in der Vorschau anzeigen und veröffentlichen.

1. Wählen Sie alle Dokumente im Ordner Microsoft SharePoint oder Google Drive aus. Sie können mehrere Dokumente auswählen, indem Sie beim Klicken die Strg-Taste (Windows/Linux) oder die Befehlstaste (Mac) gedrückt halten.

   ![Alle Dateien auswählen](/help/edge/assets/select-all-files.png)

1. Klicken Sie auf das AEM Sidekick-Symbol, das in Ihre Chrome-Erweiterungsleiste eingefügt ist. Auf dem Bildschirm wird eine Symbolleiste angezeigt. Sie können die Vorschau oder Veröffentlichung des Inhalts auswählen.

   Wenn Sie `index`, `nav`, `footer` und `enquiry` -Dateien sind, sind dies separate Dokumente mit eigenen Vorschau- und Veröffentlichungszyklen. Stellen Sie daher sicher, dass Sie alle Dokumente in der Vorschau anzeigen (und veröffentlichen).

   Nach der Vorschau der Dateien werden die Dokumente in neuen Browserregisterkarten angezeigt. Um eine Vorschau des Beispielformulars anzuzeigen, gehen Sie zur folgenden URL:


   ```HTML
   https://<branch>--<repository>--<owner>.hlx.live
   ```

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repository.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.


   `https://<branch>--<repo>--<owner>.hlx.page/enquiry` URL.

   Wenn das Repository Ihres Projekts beispielsweise &quot;wefinance&quot;heißt, befindet es sich unter dem Kontoinhaber &quot;wkndforms&quot;und Sie verwenden die &quot;main&quot;-Verzweigung, lautet die URL:



   [https://main—wefinance—wkndforms.hlx.page](https://main--wefinance--wkndforms.hlx.page).

### Formular aktualisieren

1. Wechseln Sie zum Ordner Microsoft SharePoint oder Google Drive .

1. Öffnen Sie `enquiry.xlsx` zur Bearbeitung.

   ![Anfrageformular](/help/edge/assets/enquiry-form-microsoft-sharepoint.png)

1. Ändern Sie den Titel der Senden-Schaltfläche in `Let's Chat`.

   ![Anfrageformular](/help/edge/assets/enquiry-form-microsoft-sharepoint.png)

1. Verwenden Sie AEM Sidekick, um eine Vorschau anzuzeigen und die `enquiry.xlsx` -Datei.

   ![Anfrageformular](/help/edge/assets/enquiry-form-preview-publish.png)

1. Um eine Vorschau des Anfrageformulars anzuzeigen, gehen Sie zur folgenden URL:


   ```HTML
   https://<branch>--<repository>--<owner>.hlx.page/enquiry
   ```

   Der Titel der Senden-Schaltfläche wird aktualisiert. Füllen Sie nun das Formular aus und klicken Sie auf die Senden-Schaltfläche. Es tritt ein Fehler ähnlich dem folgenden auf, da das Arbeitsblatt nicht [auf noch akzeptierte Daten eingestellt ist](/help/edge/docs/forms/submit-forms.md).


### Entwickeln von Stil und Funktionalität


So können Sie in kurzer Zeit mit einer lokalen AEM-Entwicklungsumgebung arbeiten:

1. Installieren der AEM-CLI: Die AEM-CLI vereinfacht die Entwicklungsaufgaben. Installieren wir es global mit npm:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. Klonen Sie Ihr GitHub-Projekt: Klonen Sie Ihr Projekt-Repository von GitHub mithilfe des folgenden Befehls und ersetzen Sie es durch den folgenden Befehl: <owner> mit dem Repository-Eigentümer und <repo> mit dem Repository-Namen:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. Starten Sie Ihre lokale Umgebung: Navigieren Sie zu Ihrem Projektverzeichnis und starten Sie Ihre lokale AEM-Instanz mit einem einzigen Befehl:

   ```
   cd <repo>
   aem up
   ```

Adaptiver Forms-Block `blocks/form` Ordner ist Ihr Spielplatz für Stile und Code für Ihre Formulare! Alle bearbeiten `.css` oder `.js` -Dateien in diesem Verzeichnis speichern, werden die Änderungen sofort in Ihrem Browser angezeigt.

Bereit zur Präsentation Ihrer Erstellung? Verwenden Sie Git, um Ihre Änderungen zu übernehmen und zu übertragen. Dadurch werden Ihre Vorschau- und Produktionsumgebungen aktualisiert, auf die über diese URLs zugegriffen werden kann (Platzhalter durch Ihre Projektdetails ersetzen):

Vorschau: `https://<branch>--<repo>--<owner>.hlx.page/`
Produktion: `https://<branch>--<repo>--<owner>.hlx.live/`
Herzlichen Glückwunsch! Sie haben Ihre lokale Entwicklungsumgebung erfolgreich eingerichtet und Ihre Änderungen bereitgestellt.



## Adaptiven Forms-Block zu Ihrem bestehenden AEM hinzufügen


>[!VIDEO](https://video.tv.adobe.com/v/3427789)

Wenn Sie über ein vorhandenes AEM-Projekt verfügen, können Sie den Block Adaptive Forms in Ihr aktuelles Projekt integrieren, um mit der Formularerstellung zu beginnen. So integrieren Sie:

1. Klonen Sie das Adaptive Forms Block-Repository: https://github.com/adobe-rnd/aem-boilerplate-forms auf Ihrem Computer.

1. Suchen Sie im heruntergeladenen Ordner nach dem `blocks/form` Ordner. Kopieren Sie diesen Ordner. Navigieren Sie nun zur lokalen AEM Ihres Projekts. `blocks` und fügen Sie den kopierten Formularordner hier ein.

1. Übernehmen Sie diese Änderungen und übertragen Sie sie in Ihr AEM Projekt auf GitHub.


Das war´s! Der Adaptive Forms-Block ist jetzt Teil Ihres AEM-Projekts. Sie können mit der Erstellung und dem Hinzufügen von Formularen zu Ihren AEM beginnen.


## Beheben von GitHub-Build-Problemen

Stellen Sie einen reibungslosen GitHub-Build-Prozess sicher, indem Sie potenzielle Probleme beheben:

* **Fehler: Modulpfad auflösen:**
Wenn der Fehler &quot;Pfad zum Modul kann nicht aufgelöst werden &quot;&#39;../../scripts/lib-franklin.js&#39;&quot; auftritt, navigieren Sie zum [EDS-Projekt]/blocks/forms/form.js. Aktualisieren Sie die Importanweisung, indem Sie die Datei &quot;lib-franken.js&quot;durch die Datei &quot;aem.js&quot;ersetzen.

* **Linking-Fehler beheben:**
Sollten Sie auf Linkingfehler stoßen, können Sie diese umgehen. Öffnen Sie die [EDS-Projekt]/package.json und ändern Sie das Skript &quot;lint&quot;von &quot;lint&quot;: &quot;npm run lint:js &amp;&amp; npm run lint:css&quot; in &quot;lint&quot;: &quot;echo &#39;skipping linting for now&#39;&quot;. Speichern Sie die Datei und übertragen Sie die Änderungen auf Ihr GitHub-Projekt.


## Siehe auch

* [Erstellen eines Formulars mit Google Tabellen oder Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Formulare direkt an Ihre Microsoft Excel- oder Google Tabellen senden](/help/edge/docs/forms/submit-forms.md)
* [Ändern des Erscheinungsbilds Ihrer Formulare](/help/edge/docs/forms/style-theme-forms.md)






