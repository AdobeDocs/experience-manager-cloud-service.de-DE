---
title: Erstellen und Verwenden von Designs
description: Sie können Designs verwenden, um ein adaptives Formular mithilfe von Kernkomponenten zu stilisieren und eine visuelle Identität bereitzustellen. Ein Design kann für beliebig viele adaptive Formulare gemeinsam genutzt werden.
source-git-commit: 1357b36dc3d14d2ceceb6761cb005b592472890a
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 20%

---


# Designs in Adaptive Forms (Kernkomponenten) {#themes-for-af-using-core-components}

Sie können Designs erstellen und anwenden, um ein adaptives Formular mit Kernkomponenten zu stilisieren. Zu einem Design gehören Stildetails für die Komponenten und Bereiche. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider. Das Design wird unabhängig, ohne Verweis auf ein adaptives Formular, verwaltet.

Wenn Sie [Erstellen eines adaptiven Formulars](/help/forms/creating-adaptive-form.md) Unter Verwendung von Kernkomponenten werden die vordefinierten Designs unter dem **Stil** Registerkarte. Standardmäßig wird nur der **Arbeitsfläche** -Design verfügbar ist.

>[!NOTE]
>
>Ein Thema für adaptives Formular sollte nicht mit [Vorlagen für adaptive Formulare.](/help/forms/template-editor.md) Designs für adaptive Formulare enthalten nur die Stilinformationen für ein adaptives Formular. Vorlagen für adaptive Formulare definieren die Formularstruktur und den anfänglichen Inhalt und enthalten ein Design, um die Erstellung neuer [Adaptives Formular.](/help/forms/creating-adaptive-form.md)

## Verwenden des Canvas-Designs in Adaptive Forms mit Kernkomponenten {#using-theme-in-adaptive-form}

Schritte zum Anwenden eines Designs auf ein adaptives Formular:

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an.

1. Tippen **Adobe Experience Manager** > **Forms** > **Forms und Dokumente**.

1. Klicken **Erstellen** > **Adaptives Forms**. Der Assistent zum Erstellen des adaptiven Formulars wird geöffnet.

1. Wählen Sie die Kernkomponentenvorlage im **Quelle** Registerkarte.

   >[!NOTE]
   >
   > Wenn Sie ein adaptives Formular mit Kernkomponenten erstellen, wird auf der Registerkarte &quot;Stil&quot;das Thema &quot;Arbeitsfläche&quot;angezeigt. Dies ist das einzige vorkonfigurierte Design, das derzeit verfügbar ist. Sie können das Design jedoch nach Ihren Vorstellungen ändern und für die zukünftige Verwendung speichern, indem Sie eine Frontend-Pipeline einrichten.

1. Wählen Sie das Thema Arbeitsfläche im **Stil** Registerkarte.
1. Klicken Sie auf **Erstellen**.

Themen für adaptive Formulare werden als Teil einer Vorlage für adaptive Formulare verwendet, um beim Erstellen eines adaptiven Formulars Stile zu definieren.

## Design anpassen {#customizing-theme}

So passen Sie ein Design an:

* [Einrichten einer Pipeline in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline)
* Konfigurieren Sie einen Benutzer mit dem [Mitwirkende](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html).
* Sie sollten eine [Grundkenntnisse von Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git) und Cloud Service-Git-Repositorys.

So passen Sie ein Canvas-Design an:
1. [Klonen des Arbeitsflächendesigns](#1-download-canvas-theme-download-canvas-theme)
1. [Grundlegendes zur Struktur des Designs](#2-understand-structure-of-the-canvas-theme-structure-of-canvas-theme)
1. [Name in package.json und package_lock.json ändern](#changename-packagelock-packagelockjson)
1. [Erstellen Sie die ](#3-create-the-env-file-in-a-theme-folder-creating-env-file-theme-folder)
1. [Starten Sie den lokalen Proxyserver.](#4-start-a-local-proxy-server-starting-a-local-proxy-server)
1. [Design anpassen](#customize-the-theme-customizing-theme)
1. [Übergeben Sie die Änderungen](#6-committing-the-changes-committing-the-changes)
1. [Pipeline bereitstellen](#7-deploying-the-customized-theme-deploy-customized-theme)

### 1. Klonen Sie das Leinwanddesign {#download-canvas-theme}

Öffnen Sie die Eingabeaufforderung und führen Sie den folgenden Befehl aus, um das Arbeitsflächendesign zu klonen:

```
git clone https://github.com/adobe/aem-forms-theme-canvas
```

>[!NOTE]
>
> Auf der Registerkarte &quot;Stil&quot;des Assistenten zur Formularerstellung wird der gleiche Designname angezeigt wie in der Datei package.json .

### 2. Grundlegendes zur Struktur des Themas {#structure-of-canvas-theme}

Ein Design für adaptives Formular ist ein Paket, das die CSS-, JavaScript- und statischen Ressourcen enthält, die die Formatierung Ihres Formulars definieren und die Struktur eines Designs für adaptive Formulare einhalten. Ein Design für ein adaptives Formular weist die folgende Struktur auf, die für ein Frontend-Projekt typisch ist:

* `src/components`: Spezifische JavaScript- und CSS-Dateien für AEM Kernkomponenten
* `src/resources`: Statische Dateien wie Symbole, Logos und Schriftarten
* `src/site`: JavaScript- und CSS-Dateien, die für die gesamte AEM Sites-Seite gelten
* `src/theme.ts`: Der Haupteinstiegspunkt Ihres JavaScript- und CSS-Designs
* `src\theme.scss`: JavaScript- und CSS-Dateien, die für das gesamte Design gelten

Die `src/components` enthält JavaScript- und CSS-Dateien, die für alle AEM Kernkomponenten wie Schaltfläche, Kontrollkästchen, Container, Fußzeile usw. spezifisch sind. Sie können die Schaltfläche oder das Kontrollkästchen formatieren, indem Sie die CSS-Datei bearbeiten, die für die AEM Komponente spezifisch ist.

![Design bearbeiten](/help/forms/assets/theme_structure.png)

Um das Design anzupassen, können Sie den lokalen Proxy-Server starten, um die Designanpassungen in Echtzeit basierend auf tatsächlichen AEM Inhalt anzuzeigen.

### 3. Ändern Sie den Namen in package.json und package_lock.json des Canvas-Designs {#changename-packagelock-packagelockjson}

Aktualisieren Sie den Namen und die Version des Canvas-Designs im `package.json` und `package_lock.json` Dateien.

>[!NOTE]
>
> Namen dürfen nicht `@aemforms` -Tag. Es sollte sich um einfachen Text als vom Benutzer bereitgestellten Namen handeln.

![Leinwanddesign-Thema](/help/forms/assets/changename_canvastheme.png)

### 4. Erstellen Sie die .env-Datei in einem Designordner {#creating-env-file-theme-folder}

Erstellen Sie eine `.env` -Datei im Ordner &quot;Design&quot;und fügen Sie die folgenden Parameter hinzu:

* **AEM URL**
AEM_URL=https://[author-instance]

* **AEM Site-Name**
AEM_ADAPTIVE_FORM=Form_name

* **AEM Proxyanschluss**
AEM_PROXY_PORT=7000


![Struktur von Arbeitsflächendesigns](/help/forms/assets/env-file-canvas-theme.png)

### 5. Lokalen Proxyserver starten {#starting-a-local-proxy-server}

1. Navigieren Sie in der Befehlszeile zum Stammverzeichnis des Designs auf Ihrem lokalen Computer.
1. Führen Sie `npm install` aus. npm ruft die Abhängigkeiten ab und installiert das Projekt.
1. Führen Sie `npm run live` aus. Der Proxy-Server wird gestartet.

   ![npm run live](/help/forms/assets/theme_proxy.png)


1. Tippen oder klicken Sie auf **LOKAL ANMELDEN (NUR ADMINISTRATORAUFGABEN)** und melden Sie sich mit den vom AEM Administrator angegebenen Proxy-Benutzeranmeldeinformationen an.

   ![Lokale Anmeldung](/help/forms/assets/local_signin.png)

   >[!NOTE]
   >
   > * Erstellen Sie einen lokalen Benutzer, um sich lokal anzumelden. Geben Sie die Mitwirkende-Rolle für den Design-Designer an.
   > * Wenn Sie die AEM-URL als `http://localhost:[port]/` im `.env` Datei des Canvas-Designs, werden Sie direkt zum Browser umgeleitet.


1. Ändern Sie nach der Anmeldung die URL im Browser dahingehend, dass sie auf den Pfad zu den Beispielinhalten verweist, den der AEM-Administrator für Sie bereitgestellt hat.

   * Wenn der angegebene Pfad z. B. `/content/formname.html?wcmmode=disabled` warändern Sie die URL in `http://localhost:[port]/content/forms/af/formname.html?wcmmode=disabled`

   ![Proxys für Beispielinhalte](/help/forms/assets/sample_af.png)

Navigieren Sie zu einem adaptiven Formular, um das auf ein adaptives Formular angewendete Arbeitsflächendesign anzuzeigen.

### 6. Anpassen des Designs {#customize-theme}

1. Öffnen Sie die Datei in Ihrem Editor `<your-theme-sources>/src/site/_variables.scss`.

   >[!NOTE]
   >
   > Sie können alle Komponenten des adaptiven Formulars in einer Site direkt gestalten, indem Sie die `site/_variables.scss` -Datei.

1. Bearbeiten Sie die Variable für die `font colour` nach `red`.

   ![Design bearbeiten](/help/forms/assets/edit_theme.png)

   **Gestalten Sie die verschiedenen AEM.**

   Sie können die verschiedenen Komponenten eines adaptiven Formulars formatieren, indem Sie dessen CSS-Datei im Editor ändern. Es gibt verschiedene CSS-Ordner für jede Kernkomponente des adaptiven Formulars im Ordner &quot;Arbeitsflächendesign&quot;.

   ![Kernkomponente](/help/forms/assets/theme-component.png)

   Um Stile für eine bestimmte Komponente im Design-Editor anzugeben, können Sie die CSS in einem Designordner bearbeiten. Wenn Sie beispielsweise die Rahmenfarbe eines Textfeldfelds ändern möchten, öffnen Sie die CSS-Datei im Editor und ändern Sie die Rahmenfarbe.

   ![Textbox-CSS bearbeiten](/help/forms/assets/edit_color_textbox.png)

1. Wenn Sie die Datei speichern, erkennt der Proxy-Server die Änderung über die Zeile `[Browsersync] File event [change]`.

   ![Proxy-Browser-Synchronisierung](/help/forms/assets/browser_sync.png)

1. Wenn Sie zum Browser des lokalen Proxyservers zurückkehren, ist die Änderung sofort sichtbar.

   ![AF-Design ändern](/help/forms/assets/edit_theme_af.png)

Der Design-Designer zeigt eine Vorschau der Änderungen im lokalen Proxy-Server an und passt das Design entsprechend den Anforderungen für verschiedene AEM an.

Bevor Sie die Änderungen in das AEM Git-Repository übernehmen, müssen Sie auf Ihre [Git-Repository-Informationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git).

### 7. Zusagen der Änderungen {#committing-the-changes}

Nachdem Sie Änderungen am Design vorgenommen und es mit einem lokalen Proxy-Server getestet haben, übertragen Sie die Änderungen in das Git-Repository Ihres AEM Forms-Cloud Service. Dadurch wird das angepasste Design in Ihrer Forms-Cloud Service-Umgebung für adaptive Forms-Autoren zur Verfügung gestellt.

Bevor Sie Änderungen an das Git-Repository Ihres AEM Forms-Cloud Service übertragen, benötigen Sie einen Klon des Repositorys auf Ihrem lokalen Computer. So klonen Sie das Repository:

1. Erstellen Sie ein neues Design-Repository, indem Sie auf die **[!UICONTROL Repositorys]** -Option.

   ![Erstellen eines neuen Design-Repo](/help/forms/assets/createrepo_canvastheme.png)

1. Klicken **[!UICONTROL Repository hinzufügen]** und geben Sie die **Repository-Name** im **Repository hinzufügen** Dialogfeld. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Repository für Leinwanddesign hinzufügen](/help/forms/assets/addcanvasthemerepo.png)

1. Klicken **[!UICONTROL Repository-URL kopieren]** , um die URL des erstellten Repositorys zu kopieren.

   ![URL des Arbeitsflächendesigns](/help/forms/assets/copyurl_canvastheme.png)

1. Öffnen Sie die Eingabeaufforderung und klonen Sie das oben erstellte Cloud-Repository.

   ```
   git clone https://git.cloudmanager.adobe.com/aemforms/Canvasthemerepo/
   ```

1. Verschieben Sie die Dateien des Design-Repositorys, die Sie bearbeiten, mit einem Befehl, der dem
   `cp -r [source-theme-folder]/* [destination-cloud-repo]`
Verwenden Sie beispielsweise diesen Befehl 
`cp -r [C:/cloned-git-canvas/*] [C:/cloned-repo]`
1. Übertragen Sie die Designdateien, in die Sie mit den folgenden Befehlen verschoben haben, im Verzeichnis des Cloud-Repositorys.

   ```text
   git add .
   git commit -a -m "Adding theme files"
   git push
   ```

1. Die Anpassungen werden an das Git-Repository gesendet.

   ![Vorgenommene Änderungen](/help/forms/assets/cmd_git_push.png)

Ihre Anpassungen werden jetzt sicher im Git-Repository gespeichert.


### 8. Ausführen der Frontend-Pipeline {#deploy-pipeline}

1. Erstellen Sie die Front-End-Pipeline, um das angepasste Design bereitzustellen. Lernen [Einrichten einer Frontend-Pipeline zum Bereitstellen eines benutzerdefinierten Designs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline).
1. Führen Sie die erstellte Frontend-Pipeline aus, um den benutzerdefinierten Designordner unter dem **[!UICONTROL Stil]** Registerkarte eines Assistenten zur Erstellung adaptiver Formulare.

>[!NOTE]
>
>Wenn Sie in Zukunft Änderungen im Designordner der Arbeitsfläche vornehmen, müssen Sie die oben beschriebene Pipeline erneut ausführen. Daher muss der Name der Pipeline gespeichert werden.

## Beispiel zum Anpassen des Designs {#example-to-customize-a-theme}

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an.
1. Öffnen Sie ein adaptives Formular, das mit Kernkomponenten erstellt wurde.
1. Starten Sie den lokalen Proxyserver über die Eingabeaufforderung und klicken Sie auf **LOKAL ANMELDEN (NUR ADMINISTRATORAUFGABEN)**.
1. Nach der Anmeldung werden Sie zum Browser weitergeleitet und sehen sich das angewendete Design an.
1. Laden Sie die [Arbeitsflächendesign](https://github.com/adobe/aem-forms-theme-canvas) und extrahieren Sie den heruntergeladenen ZIP-Ordner.
1. Öffnen Sie den extrahierten ZIP-Ordner in Ihrem bevorzugten Editor.
1. Erstellen Sie eine `.env` -Datei im Ordner &quot;Design&quot;und fügen Sie Parameter hinzu: **AEM URL**, **AEM_ADAPTIVE_FORM** und **AEM_PROXY_PORT**.
1. Öffnen Sie die CSS-Datei des Textfelds im Ordner &quot;Canvas-Design&quot;und ändern Sie die Rahmenfarbe, um `red` Farbe zu markieren und die Änderungen zu speichern.
1. Öffnen Sie den Browser erneut und Sie sehen, dass die Änderungen sofort in einem adaptiven Formular übernommen werden.
1. Verschieben Sie den Designordner der Arbeitsfläche in Ihr geklontes Repository.
1. Übernehmen Sie die Änderungen und führen Sie die Frontend-Pipeline aus.

Sobald die Pipeline ausgeführt wird, ist das Design auf der Registerkarte Stil verfügbar.

## Best Practices {#best-practices}

* **Vermeiden von Assets aus einem anderen Design**

   Bei der Bearbeitung von Designs können Sie Assets (etwa Bilder) aus anderen Designs durchsuchen und hinzufügen. Angenommen, Sie bearbeiten den Hintergrund einer Seite. Wenn Sie beispielsweise **[!UICONTROL Seite]** ![Bearbeiten-Schaltfläche](assets/edit-button.png) > **[!UICONTROL Hintergrund]** > **[!UICONTROL Hinzufügen]** > **[!UICONTROL Bild]** auswählen, wird ein Dialogfeld angezeigt, in dem Sie Bilder aus anderen Designs suchen und hinzufügen können.

   Es können Probleme im aktuellen Design auftreten, wenn ein Asset aus einem anderen Design hinzugefügt und dieses andere Design später verschoben oder gelöscht wird. Wir empfehlen daher, keine Assets aus anderen Designs zu suchen und hinzuzufügen.

* **Ändern der Layout-Breite des Container-Bereichs**

   Es wird nicht empfohlen, die Layout-Breite des Container-Bereichs zu ändern. Wenn Sie die Breite eines Container-Bereichs angeben, wird er statisch und passt sich nicht mehr an unterschiedliche Displays an.

* **Verwenden des Formular-Editors oder Design-Editors für die Arbeit mit Kopf- und Fußzeilen**

   Verwenden Sie den Design-Editor, wenn Sie Kopf- und Fußzeilen mit Formatierungsoptionen wie Schriftschnitt, Hintergrund und Transparenz formatieren möchten.
Wenn Sie Informationen wie ein Logo, einen Firmennamen in der Kopfzeile und Copyright-Informationen in der Fußzeile angeben möchten, verwenden Sie dazu die im Formular-Editor verfügbaren Optionen.
