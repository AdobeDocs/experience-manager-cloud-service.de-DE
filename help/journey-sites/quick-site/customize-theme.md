---
title: Anpassen des Site-Designs
description: Erfahren Sie, wie das Site-Design erstellt wird, wie Sie es anpassen und wie Sie es mit Live-AEM testen können.
exl-id: b561bee0-3a64-4dd3-acb8-996f0ca5bfab
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 1%

---

# Anpassen des Site-Designs {#customize-the-site-theme}

Erfahren Sie, wie das Site-Design erstellt wird, wie Sie es anpassen und wie Sie es mit Live-AEM testen können.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Schnellsite-Journey [Git-Repository-Zugriffsinformationen abrufen,](retrieve-access.md) Sie haben gelernt, wie die Frontend-Entwickler-Benutzer Cloud Manager auf Git-Repository-Informationen zugreifen können, und sollten jetzt:

* Erfahren Sie auf hoher Ebene, was Cloud Manager ist.
* Sie haben Ihre Anmeldeinformationen abgerufen, um auf das AEM Git zuzugreifen, damit Sie Ihre Anpassungen übernehmen können.

Dieser Teil des Journey führt den nächsten Schritt durch und nimmt den Abschnitt zum Site-Design auf und zeigt Ihnen, wie Sie es anpassen und dann diese Anpassungen mit den von Ihnen abgerufenen Zugriffsberechtigungen vornehmen können.

## Ziel {#objective}

In diesem Dokument wird erläutert, wie das AEM Site-Design erstellt wird, wie es angepasst wird und wie es mit Live-AEM getestet wird. Nach dem Lesen sollten Sie:

* Machen Sie sich mit der grundlegenden Struktur des Site-Designs und dessen Bearbeitung vertraut.
* Erfahren Sie, wie Sie Ihre Designanpassungen mit echten AEM über einen lokalen Proxy testen können.
* Erfahren Sie, wie Sie Ihre Änderungen in das AEM Git-Repository übertragen.

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Journey gilt für den Frontend-Entwickler.

## Grundlegendes zur Themenstruktur {#understand-theme}

Extrahieren Sie das vom AEM-Administrator bereitgestellte Design an die Stelle, an der Sie das Design bearbeiten möchten, und öffnen Sie es in Ihrem bevorzugten Editor.

![Design bearbeiten](assets/edit-theme.png)

Sie sehen, dass das Design ein typisches Frontend-Projekt ist. Die wichtigsten Teile der Struktur sind:

* `src/main.ts`: Der Haupteinstiegspunkt Ihres JS- und CSS-Designs
* `src/site`: JS- und CSS-Dateien, die für die gesamte Site gelten
* `src/components`: JS- und CSS-Dateien, die für AEM Komponenten spezifisch sind
* `src/resources`: Statische Dateien wie Symbole, Logos und Schriftarten

>[!TIP]
>
>Weitere Informationen zum standardmäßigen AEM-Site-Design finden Sie unter dem GitHub-Link im [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

Sobald Sie sich mit der Struktur des Designprojekts vertraut gemacht haben, starten Sie den lokalen Proxy, damit Sie alle Designanpassungen in Echtzeit sehen können, basierend auf dem tatsächlichen AEM Inhalt.

## Starten des lokalen Proxys {#starting-proxy}

1. Navigieren Sie in der Befehlszeile zum Stammverzeichnis des Designs auf Ihrem lokalen Computer.
1. Ausführen `npm install` und npm ruft Abhängigkeiten ab und installiert das Projekt.

   ![npm install](assets/npm-install.png)

1. Ausführen `npm run live` und der Proxyserver gestartet wird.

   ![npm run live](assets/npm-run-live.png)

1. Wenn der Proxy-Server gestartet wird, wird automatisch ein Browser geöffnet für `http://localhost:7001/`. Tippen oder klicken Sie auf **LOKAL ANMELDEN (NUR ADMINISTRATORAUFGABEN)** und melden Sie sich mit den vom AEM Administrator angegebenen Anmeldeinformationen des Proxybenutzers an.

   ![Lokale Anmeldung](assets/sign-in-locally.png)

1. Ändern Sie nach der Anmeldung die URL im Browser so, dass sie auf den Pfad zum Beispielinhalt verweist, den der AEM-Administrator Ihnen bereitgestellt hat.

   * Wenn der angegebene Pfad beispielsweise `/content/<your-site>/en/home.html?wcmmode=disabled`
   * Sie ändern die URL in `http://localhost:7001/content/<your-site>/en/home.html?wcmmode=disabled`

   ![Proxys für Beispielinhalt](assets/proxied-sample-content.png)

Sie können auf der Site navigieren, um den Inhalt zu untersuchen. Die Site wird live von der Live-AEM-Instanz abgerufen, damit Sie Ihre Designanpassungen an echten Inhalt vornehmen können.

## Design anpassen {#customize-theme}

Jetzt können Sie mit der Anpassung des Designs beginnen. Im Folgenden finden Sie ein einfaches Beispiel, um zu veranschaulichen, wie Sie Ihre Änderungen live über den Proxy anzeigen können.

1. Öffnen Sie die Datei in Ihrem Editor `<your-theme-sources>/src/site/_variables.scss`

   ![Design bearbeiten](assets/edit-theme.png)

1. Variable bearbeiten `$color-background` und legen Sie einen anderen Wert als Weiß fest. In diesem Beispiel `orange` verwendet.

   ![Design bearbeitet](assets/edited-theme.png)

1. Wenn Sie die Datei speichern, sehen Sie, dass der Proxy-Server die Änderung über die Zeile erkennt `[Browsersync] File event [change]`.

   ![Proxy-Browsersynchronisierung](assets/proxy-browsersync.png)

1. Wenn Sie zum Browser des Proxyservers zurückkehren, ist die Änderung sofort sichtbar.

   ![Orange-Design](assets/orange-theme.png)

Sie können das Design weiterhin an die Anforderungen anpassen, die Ihnen der AEM-Administrator gestellt hat.

## Zusagen der Änderungen {#committing-changes}

Sobald Ihre Anpassungen abgeschlossen sind, können Sie sie in das AEM Git-Repository übertragen. Zuerst müssen Sie das Repository auf Ihrem lokalen Computer klonen.

1. Navigieren Sie in der Befehlszeile zu der Stelle, an der Sie das Repo klonen möchten.
1. Führen Sie den Befehl aus, den Sie [wurde zuvor aus Cloud Manager abgerufen.](retrieve-access.md) Sie sollte der `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`. Verwenden Sie den Git-Benutzernamen und das Kennwort, die [Sie haben im vorherigen Teil dieser Journey abgerufen.](retrieve-access.md)

   ![Repo klonen](assets/clone-repo.png)

1. Verschieben Sie das Designprojekt, das Sie bearbeitet haben, mit einem Befehl, der dem `mv <site-theme-sources> <cloned-repo>`
1. Übertragen Sie im Verzeichnis des geklonten Repo die Designdateien, in die Sie gerade mit den folgenden Befehlen verschoben haben.

   ```text
   git add .
   git commit -m "Adding theme sources"
   git push
   ```

1. Die Anpassungen werden an das AEM Git-Repository gesendet.

   ![Vorgenommene Änderungen](assets/changes-committed.png)

Ihre Anpassungen werden jetzt sicher im AEM Git-Repository gespeichert.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der Journey zur AEM Schnellseitenerstellung abgeschlossen haben, sollten Sie Folgendes tun:

* Machen Sie sich mit der grundlegenden Struktur des Site-Designs und dessen Bearbeitung vertraut.
* Erfahren Sie, wie Sie Ihre Designanpassungen mit echten AEM über einen lokalen Proxy testen können.
* Erfahren Sie, wie Sie Ihre Änderungen in das AEM Git-Repository übertragen.

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit der Journey zur AEM SchnellSite-Erstellung fort, indem Sie das Dokument erneut überprüfen. [Bereitstellen Ihres benutzerdefinierten Designs,](deploy-theme.md) wo Sie erfahren, wie Sie das Design mithilfe der Frontend-Pipeline bereitstellen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zur Schnellseitenerstellung zu wechseln, indem Sie das Dokument lesen [Bereitstellen Ihres benutzerdefinierten Designs,](deploy-theme.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf dem Journey weiterarbeiten müssen.

* [AEM Site-Design](https://github.com/adobe/aem-site-template-standard-theme-e2e) - Dies ist das GitHub-Repository des AEM Site-Designs.
* [npm](https://www.npmjs.com) - AEM Designs, die zum schnellen Erstellen von Sites verwendet werden, basieren auf npm.
* [Webpack](https://webpack.js.org) - AEM Themen, die zum schnellen Erstellen von Sites verwendet werden, basieren auf Webpack.
