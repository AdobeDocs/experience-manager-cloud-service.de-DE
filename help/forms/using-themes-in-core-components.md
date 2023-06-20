---
title: Erstellen und Verwenden von Designs
description: Mithilfe von Designs können Sie ein adaptives Formular formatieren und ihm eine visuelle Identität verleihen. Ein Design kann für beliebig viele adaptive Formulare gemeinsam genutzt werden.
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: bceec9ea6858b1c4c042ecd96f13ae5cac1bbee5
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 98%

---

# Designs in adaptiven Formularen (Kernkomponenten) {#themes-for-af-using-core-components}

Sie können mithilfe von Kernkomponenten Designs erstellen und anwenden, um ein adaptives Formular zu formatieren. Ein Design enthält Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider. Das Design wird unabhängig, ohne Verweis auf ein adaptives Formular, verwaltet.

Wenn Sie [ein adaptives Formular](/help/forms/creating-adaptive-form.md) unter Verwendung von Kernkomponenten erstellen, erscheinen die vorkonfigurierten Designs unter der Registerkarte **Stil**. Standardmäßig ist nur das **Canvas**-Design verfügbar.

>[!NOTE]
>
>Ein Design für adaptive Formulare sollte nicht mit [Vorlagen für adaptive Formulare verwechselt werden.](/help/forms/template-editor.md) Designs für adaptive Formulare enthalten nur die Stilinformationen für ein adaptives Formular. Vorlagen für adaptive Formulare definieren die Formularstruktur und den anfänglichen Inhalt und enthalten ein Design, das die Erstellung neuer [Adaptives Formular.](/help/forms/creating-adaptive-form.md)

## Verwenden des Canvas-Designs in adaptiven Formularen mit Kernkomponenten {#using-theme-in-adaptive-form}

Schritte zum Anwenden eines Designs auf ein adaptives Formular:

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an.

1. Tippen Sie auf **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**. 

1. Klicken Sie auf **Erstellen** > **Adaptive Formulare**. Der Assistent zum Erstellen des adaptiven Formulars wird geöffnet.

1. Wählen Sie die Kernkomponentenvorlage auf der Registerkarte **Quelle**.

   >[!NOTE]
   >
   > Wenn Sie ein adaptives Formular mit Kernkomponenten erstellen, wird auf der Registerkarte „Stil“ das Canvas-Design angezeigt. Dies ist das einzige vorkonfigurierte Design, das derzeit verfügbar ist. Sie können das Design jedoch nach Ihren Vorstellungen ändern und für die zukünftige Verwendung speichern, indem Sie eine Frontend-Pipeline einrichten.

1. Wählen Sie das Canvas-Design auf der Registerkarte **Stil**.
1. Klicken Sie auf **Erstellen**.

Designs für adaptive Formulare werden als Teil einer Vorlage für adaptive Formulare verwendet, um beim Erstellen eines adaptiven Formulars Stile zu definieren.

## Anpassen des Designs {#customizing-theme}

Anpassen eines Designs:

* [Einrichten einer Pipeline in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline)
* Konfigurieren Sie eine Benutzerin bzw. einen Benutzer mit der Rolle [Mitwirkende](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html?lang=de).
* Sie sollten über [Grundkenntnisse in Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git) und Cloud Service-Git-Repositorys verfügen.

Anpassen eines Canvas-Designs:

1. [Klonen des Canvas-Designs](#1-download-canvas-theme-download-canvas-theme)
1. [Grundlegendes zur Struktur des Designs](#2-understand-structure-of-the-canvas-theme-structure-of-canvas-theme)
1. [Name in package.json und package_lock.json ändern](#changename-packagelock-packagelockjson)
1. [Erstellen Sie die ](#3-create-the-env-file-in-a-theme-folder-creating-env-file-theme-folder)
1. [Starten Sie den lokalen Proxy-Server](#4-start-a-local-proxy-server-starting-a-local-proxy-server)
1. [Anpassen des Designs](#customize-the-theme-customizing-theme)
1. [Übergeben Sie die Änderungen](#6-committing-the-changes-committing-the-changes)
1. [Bereitstellen der Pipeline](#7-deploying-the-customized-theme-deploy-customized-theme)

### 1. Klonen Sie das Canvas-Design {#download-canvas-theme}

Öffnen Sie die Eingabeaufforderung und führen Sie den folgenden Befehl aus, um das Canvas-Design zu klonen:

```
git clone https://github.com/adobe/aem-forms-theme-canvas
```

>[!NOTE]
>
> Auf der Registerkarte „Stil“ des Assistenten zur Formularerstellung wird der gleiche Design-Name angezeigt wie in der Datei package.json.

### 2. Grundlegendes zur Struktur des Designs {#structure-of-canvas-theme}

Ein Design für adaptive Formulare ist ein Paket, das die CSS-, JavaScript- und statischen Ressourcen enthält, die das Aussehen Ihrer Formulare definieren und die Struktur eines Designs für adaptive Formulare einhalten. Ein Design für adaptive Formulare weist die folgende Struktur auf, die für ein Frontend-Projekt typisch ist:

* `src/components`: JavaScript- &amp; CSS-Dateien, die spezifisch für AEM-Kernkomponenten sind
* `src/resources`: Statische Dateien wie Symbole, Logos und Schriftarten
* `src/site`: JavaScript- &amp; CSS-Dateien, die für die gesamte AEM Sites-Seite gelten
* `src/theme.ts`: Der Haupteinstiegspunkt für Ihr JavaScript- und CSS-Design
* `src\theme.scss`: JavaScript- und CSS-Dateien, die für das gesamte Design gelten

Der Ordner `src/components` enthält JavaScript- und CSS-Dateien, die für alle AEM-Kernkomponenten wie Schaltfläche, Kontrollkästchen, Container, Fußzeile usw. spezifisch sind. Sie können die Schaltfläche oder das Kontrollkästchen gestalten, indem Sie die CSS-Datei bearbeiten, die für die AEM-Komponente spezifisch ist.

![Bearbeiten des Designs](/help/forms/assets/theme_structure.png)

Um das Design anzupassen, können Sie den lokalen Proxy-Server starten und die Design-Anpassungen in Echtzeit basierend auf tatsächlichen AEM-Inhalt anzeigen.

### 3. Ändern Sie den Namen des Canvas-Designs in package.json und package_lock.json {#changename-packagelock-packagelockjson}

Aktualisieren Sie den Namen und die Version des Canvas-Designs in den Dateien `package.json` und `package_lock.json`.

>[!NOTE]
>
> Namen sollten keinen `@aemforms`-Tag haben. Es sollte ein einfacher Text als vom Benutzer bereitgestellter Name sein.

![Canvas-Design-Bild](/help/forms/assets/changename_canvastheme.png)

### 4. Erstellen Sie die .env-Datei in einem Design-Ordner {#creating-env-file-theme-folder}

Erstellen Sie eine `.env`-Datei im Design-Ordner und fügen Sie die folgenden Parameter hinzu:

* **AEM URL**
AEM_URL=https://[author-instance]

* **AEM Site-Name**
AEM_ADAPTIVE_FORM=Form_name

* **AEM Proxy-Port**
AEM_PROXY_PORT=7000


![Canvas-Design-Struktur](/help/forms/assets/env-file-canvas-theme.png)

### 5. Starten Sie einen lokalen Proxy-Server {#starting-a-local-proxy-server}

1. Navigieren Sie in der Befehlszeile zum Stammverzeichnis des Designs auf Ihrem lokalen Computer.
1. Führen Sie `npm install` aus. npm ruft die Abhängigkeiten ab und installiert das Projekt.
1. Führen Sie `npm run live` aus. Der Proxy-Server wird gestartet.

   ![npm run live](/help/forms/assets/theme_proxy.png)


1. Tippen oder klicken Sie auf **LOKAL ANMELDEN (NUR AUFGABEN VON ADMINS** und melden Sie sich mit den von AEM-Admins für Sie bereitgestellten Anmeldeinformationen des Proxy-Benutzers an.

   ![Lokale Anmeldung](/help/forms/assets/local_signin.png)

   >[!NOTE]
   >
   > * Erstellen Sie einen lokalen Benutzer, um sich lokal anzumelden. Geben Sie die Mitwirkende-Rolle für den Design-Designer an.
   > * Wenn Sie die AEM-URL als `http://localhost:[port]/` in der `.env`-Datei des Canvas-Designs angeben, werden Sie direkt zum Browser weitergeleitet.

1. Ändern Sie nach der Anmeldung die URL im Browser dahingehend, dass sie auf den Pfad zu den Beispielinhalten verweist, den der AEM-Administrator für Sie bereitgestellt hat.

   * Wenn der angegebene Pfad z. B. `/content/formname.html?wcmmode=disabled` war, ändern Sie die URL zu `http://localhost:[port]/content/forms/af/formname.html?wcmmode=disabled`

   ![Proxys für Beispielinhalte](/help/forms/assets/sample_af.png)

Navigieren Sie zu einem adaptiven Formular, um das auf ein adaptives Formular angewendete Canvas-Design anzuzeigen.

### 6. Passen Sie das Design an {#customize-theme}

1. Öffnen Sie die Datei `<your-theme-sources>/src/site/_variables.scss` in Ihrem Editor.

   >[!NOTE]
   >
   > Sie können alle Komponenten des adaptiven Formulars in einer Site direkt gestalten, indem Sie die `site/_variables.scss`-Datei bearbeiten.

1. Bearbeiten Sie die Variable für die `font colour` auf `red`.

   ![Bearbeiten eines Designs](/help/forms/assets/edit_theme.png)

   **Gestalten Sie die verschiedenen AEM-Komponenten.**

   Sie können die verschiedenen Komponenten eines adaptiven Formulars formatieren, indem Sie dessen CSS-Datei im Editor ändern. Es gibt verschiedene CSS-Ordner für jede Kernkomponente des adaptiven Formulars im Canvas-Design-Ordner.

   ![Kernkomponente](/help/forms/assets/theme-component.png)

   Um Stile für eine bestimmte Komponente im Design-Editor anzugeben, können Sie die CSS in einem Design-Ordner bearbeiten. Wenn Sie beispielsweise die Rahmenfarbe eines Textfeldfelds ändern möchten, öffnen Sie die CSS-Datei im Editor und ändern Sie die Rahmenfarbe dort.

   ![Bearbeiten der CSS-Textbox](/help/forms/assets/edit_color_textbox.png)

1. Wenn Sie die Datei speichern, erkennt der Proxy-Server die Änderung über die Zeile `[Browsersync] File event [change]`.

   ![Proxy-Browser-Synchronisierung](/help/forms/assets/browser_sync.png)

1. Wenn Sie zum Browser des lokalen Proxy-Servers zurückkehren, ist die Änderung sofort sichtbar.

   ![Ändern des AF-Designs](/help/forms/assets/edit_theme_af.png)

Der Design-Designer zeigt eine Vorschau der Änderungen im lokalen Proxy-Server an und passt das Design entsprechend den Anforderungen für verschiedene AEM-Komponenten an.

Bevor Sie die Änderungen in das AEM Git-Repository übernehmen, müssen Sie auf Ihre [Git-Repository-Informationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git) zugreifen.

### 7. Bestätigen Sie die Änderungen {#committing-the-changes}

Nachdem Sie Änderungen am Design vorgenommen und es mit einem lokalen Proxy-Server getestet haben, übertragen Sie die Änderungen in das Git-Repository Ihres AEM Forms Cloud Services. Dadurch wird das angepasste Design in Ihrer Forms Cloud Service-Umgebung für Autoren von adaptiven Formularen zur Verfügung gestellt.

Bevor Sie Änderungen an das Git-Repository Ihres AEM Forms Cloud Services übertragen, benötigen Sie einen Klon des Repositorys auf Ihrem lokalen Computer. Klonen des Repositorys:

1. Erstellen Sie ein neues Design-Repository, indem Sie auf die **[!UICONTROL Repositorys]**-Option klicken.

   ![Erstellen eines neuen Design-Repo](/help/forms/assets/createrepo_canvastheme.png)

1. Klicken Sie auf **[!UICONTROL Repository hinzufügen]** und geben Sie den **Repository-Namen** im Dialogfeld **Repository hinzufügen** an. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Hinzufügen eines Repository für das Canvas-Design-Repo](/help/forms/assets/addcanvasthemerepo.png)

1. Klicken Sie auf **[!UICONTROL Repository-URL kopieren]**, um die URL des erstellten Repositorys zu kopieren.

   ![URL des Canvas-Designs](/help/forms/assets/copyurl_canvastheme.png)

1. Öffnen Sie die Eingabeaufforderung und klonen Sie das oben erstellte Cloud-Repository.

   ```
   git clone https://git.cloudmanager.adobe.com/aemforms/Canvasthemerepo/
   ```

1. Verschieben Sie die Dateien des Design-Repositorys, das Sie bearbeiten, in das Cloud-Repository mit einem ähnlichen Befehl wie
   `cp -r [source-theme-folder]/* [destination-cloud-repo]`
Verwenden Sie beispielsweise diesen Befehl `cp -r [C:/cloned-git-canvas/*] [C:/cloned-repo]`
1. Bestätigen Sie mit den folgenden Befehlen die Design-Dateien im Verzeichnis des Cloud-Repository, die Sie hierhin verschoben haben.

   ```text
   git add .
   git commit -a -m "Adding theme files"
   git push
   ```

1. Die Anpassungen werden auf das Git-Repository übertragen.

   ![Vorgenommene Änderungen](/help/forms/assets/cmd_git_push.png)

Ihre Anpassungen sind jetzt sicher im Git-Repository gespeichert.


### 8. Ausführen der Frontend-Pipeline {#deploy-pipeline}

1. Erstellen Sie die Frontend-Pipeline, um das angepasste Design bereitzustellen. Erfahren Sie, [wie Sie eine Frontend-Pipeline zur Bereitstellung eines benutzerdefinierten Designs einrichten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline).
1. Führen Sie die erstellte Frontend-Pipeline aus, um den benutzerdefinierten Design-Ordner unter der Registerkarte **[!UICONTROL Stil]** des Assistenten zur Erstellung eines adaptiven Formulars bereitzustellen.

>[!NOTE]
>
>Wenn Sie in Zukunft Änderungen im Ordner des Arbeitsflächen-Designs vornehmen, müssen Sie die obige Pipeline erneut ausführen. Daher müssen Sie sich an den Namen der Pipeline erinnern.

## Beispiel für die Anpassung des Designs {#example-to-customize-a-theme}

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an.
1. Öffnen Sie ein adaptives Formular, das mithilfe von Kernkomponenten erstellt wurde.
1. Starten Sie den lokalen Proxy-Server über die Eingabeaufforderung und klicken Sie auf **LOKAL ANMELDEN (NUR ADMINISTRATORAUFGABEN)**.
1. Nach der Anmeldung werden Sie zum Browser weitergeleitet, wo Sie das angewendete Design sehen.
1. Laden Sie das [Arbeitsflächen-Design](https://github.com/adobe/aem-forms-theme-canvas) herunter und extrahieren Sie den heruntergeladenen ZIP-Ordner.
1. Öffnen Sie den extrahierten ZIP-Ordner in Ihrem bevorzugten Editor.
1. Erstellen Sie eine `.env`-Datei im Design-Ordner und fügen Sie Parameter hinzu: **AEM URL**, **AEM_ADAPTIVE_FORM** und **AEM_PROXY_PORT**.
1. Öffnen Sie die CSS-Datei des Textfelds im Ordner des Arbeitsflächen-Designs und ändern Sie die Farbe des Rahmens in `red` und speichern Sie die Änderungen.
1. Öffnen Sie den Browser erneut und Sie sehen, dass die Änderungen sofort in einem adaptiven Formular übernommen werden.
1. Verschieben Sie den Ordner des Arbeitsflächen-Designs in Ihr geklontes Repository.
1. Übernehmen Sie die Änderungen und führen Sie die Frontend-Pipeline aus.

Sobald die Pipeline ausgeführt wird, ist das Design auf der Registerkarte „Stil“ verfügbar.

## Best Practices {#best-practices}

* **Vermeiden von Assets aus einem anderen Design**

  Bei der Bearbeitung von Designs können Sie Assets (etwa Bilder) aus anderen Designs durchsuchen und hinzufügen. Angenommen, Sie bearbeiten den Hintergrund einer Seite. Wenn Sie beispielsweise **[!UICONTROL Seite]** ![Bearbeiten-Schaltfläche](assets/edit-button.png) > **[!UICONTROL Hintergrund]** > **[!UICONTROL Hinzufügen]** > **[!UICONTROL Bild]** auswählen, wird ein Dialogfeld angezeigt, in dem Sie Bilder aus anderen Designs suchen und hinzufügen können.

  Es können Probleme im aktuellen Design auftreten, wenn ein Asset aus einem anderen Design hinzugefügt und dieses andere Design später verschoben oder gelöscht wird. Wir empfehlen daher, keine Assets aus anderen Designs zu suchen und hinzuzufügen.

* **Ändern der Layout-Breite des Container-Bereichs**

  Es wird nicht empfohlen, die Layout-Breite des Container-Bereichs zu ändern. Wenn Sie die Breite eines Container-Bereichs angeben, wird er statisch und passt sich nicht mehr an unterschiedliche Displays an.

* **Verwendung des Formular- oder Design-Editors für die Arbeit mit Kopf- und Fußzeile**

  Verwenden Sie den Design-Editor, wenn Sie Kopf- und Fußzeilen mit Formatierungsoptionen wie Schriftschnitt, Hintergrund und Transparenz formatieren möchten.
Wenn Sie Informationen wie ein Logo, einen Firmennamen in der Kopfzeile und Copyright-Informationen in der Fußzeile angeben möchten, verwenden Sie dazu die im Formular-Editor verfügbaren Optionen.
