---
title: Wie können Designs in adaptive Formularen erstellt und verwendet werden?
description: Mithilfe von Designs können Sie ein adaptives Formular formatieren und ihm eine visuelle Identität verleihen. Ein Design kann für beliebig viele adaptive Formulare gemeinsam genutzt werden.
feature: Adaptive Forms, Core Components
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: 159407dfaa5d17caddca2953a5732f0e91eb474c
workflow-type: tm+mt
source-wordcount: '2754'
ht-degree: 93%

---

# Designs in adaptiven Formularen {#themes-for-af-using-core-components}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-or-customize-themes-for-adaptive-forms-core-components.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können Designs erstellen und anwenden, um ein adaptives Formular zu formatieren. Zu einem Design gehören Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider. Ein Design wird ohne Verweis auf ein adaptives Formular unabhängig verwaltet und kann über mehrere adaptive Formulare hinweg wiederverwendet werden.

## Verfügbare Designs

Forms as Cloud Service bietet die folgenden aufgelisteten Designs für auf Kernkomponenten basierende adaptive Formulare:

* [Design „Canvas“](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [Design „EASEL“](https://github.com/adobe/aem-forms-theme-easel)

## Grundlegendes zur Struktur der Designs

Ein Design ist ein Paket, das die CSS-Datei, JavaScript-Dateien und Ressourcen (wie etwa Symbole) umfasst, die den Stil Ihrer adaptiven Formulare definieren. Ein Design für ein adaptives Formular folgt einer bestimmten Organisation, die aus den folgenden Komponenten besteht:

* `src/theme.scss`: Dieser Ordner enthält die CSS-Datei, die einen großen Einfluss auf das gesamte Design hat. Sie dient als zentralisierter Speicherort zur Definition und Verwaltung des Stils und Verhaltens Ihres Designs. Durch Bearbeitung dieser Datei können Sie Änderungen vornehmen, die im gesamten Design allgemein angewendet werden und das Erscheinungsbild und die Funktionalität Ihrer adaptiven Formular- und AEM Sites-Seiten beeinflussen.

* `src/site`: Dieser Ordner enthält CSS-Dateien, die auf die gesamte Seite einer AEM-Site angewendet werden. Diese Dateien bestehen aus Code und Stilen, die die Gesamtfunktionalität und das Layout der Seite Ihrer AEM-Site beeinflussen. Alle hier vorgenommenen Änderungen werden auf sämtlichen Seiten Ihrer Site übernommen. [Wann ist es einzusetzen?]

* `src/components`: Die CSS-Dateien in diesem Ordner wurden für einzelne AEM-Kernkomponenten entwickelt. Jeder spezielle Ordner für eine Komponente enthält eine `.scss`-Datei, die die jeweilige Komponente in einem adaptiven Formular formatiert. Die Datei /src/components/accordion/_accordion.scss enthält zum Beispiel Stilinformationen für die Akkordeon-Komponente für adaptive Formulare.

  ![Design-Struktur auf Basis eines adaptiven Formulars](/help/forms/assets/theme_structure.png)

* `src/resources`: Dieser Ordner enthält statische Dateien wie Symbole, Logos und Schriftarten. Diese Ressourcen werden verwendet, um die visuellen Elemente und das gesamte Erscheinungsbild Ihres Designs zu verbessern.

## Erstellen von Designs

Forms as a Cloud Service bietet die folgenden aufgelisteten Designs für auf Kernkomponenten basierende adaptive Formulare.

* [Design „Canvas“](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [Design „EASEL“](https://github.com/adobe/aem-forms-theme-easel)

Sie können [jedes dieser Designs anpassen, um ein neues Design zu erstellen](#customize-a-theme-core-components).

![Workflow für die Design-Anpassung](/help/forms/assets/workflow-of-customization-of-theme.png)

## Anpassen eines Designs {#customize-a-theme-core-components}

Das Anpassen eines Designs bezieht sich auf den Prozess der Änderung und Personalisierung des Erscheinungsbilds eines Designs. Wenn Sie ein Design anpassen, ändern Sie dessen Design-Elemente, Layout, Farben, Typografie und manchmal den zugrunde liegenden Code. Auf diese Weise können Sie ein einzigartiges und maßgeschneidertes Erscheinungsbild für Ihre Website oder Anwendung erstellen und dabei die grundlegende Struktur und Funktionalität des Designs beibehalten.

### Voraussetzungen {#prerequisites-to-customize}

* Wenn Sie sich mit dem [Einrichten einer Pipeline in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline) vertraut machen und über grundlegende Kenntnisse zum Einrichten einer Pipeline verfügen, können Sie Ihre Design-Anpassungen effizient verwalten und bereitstellen.
* Erfahren Sie, wie [Benutzende mit der Rolle „Mitwirkende“ konfiguriert werden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html?lang=de). Wenn Sie wissen, wie Sie Benutzende mit der Rolle „Mitwirkende“ konfigurieren, können Sie die erforderlichen Berechtigungen für die Design-Anpassung erteilen.
* Installieren Sie die neueste Version von [Apache Maven.](https://maven.apache.org/download.cgi) Apache Maven ist ein Tool zur Automatisierung von Builds, das häufig für Java™-Projekte verwendet wird. Durch die Installation der neuesten Version stellen Sie sicher, dass Sie über die erforderlichen Abhängigkeiten für die Design-Anpassung verfügen.
* Installieren Sie einen Nur-Text-Editor. Beispielsweise Microsoft® Visual Studio Code. Die Verwendung eines Texteditors wie Microsoft® Visual Studio Code bietet eine benutzerfreundliche Umgebung zum Bearbeiten und Ändern von Design-Dateien.

### Einrichten Ihrer Arbeitsumgebung

* [Aktivieren Sie Kernkomponenten für adaptive Formulare](/help/forms/enable-adaptive-forms-core-components.md) für Ihre lokale Bereitstellung und die Cloud Service-Umgebung.
* Konfigurieren Sie die [Frontend-Bereitstellungs-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html?lang=de) für Ihre Cloud Service-Umgebung. Alternativ können Sie die Pipeline später konfigurieren, sodass Sie das Design vor der Einrichtung der Bereitstellungs-Pipeline flexibel priorisieren und verfeinern können.

<!-- 
To deploy your themes to a Forms as a Cloud Service environment, first test theme on a local development environment to address any issues. Once the theme is tested, configure the front-end deployment pipeline, which is responsible for deploying the themes.

These themes are deployed to a Forms as a Cloud Service environment via the front-end pipeline. You can configure the pipeline later also, after testing the theme on a local development environment. 

-->

Nachdem Sie die Voraussetzungen kennengelernt und die Entwicklungsumgebung konfiguriert haben, sind Sie nun gut darauf vorbereitet, Ihr Design an Ihre spezifischen Anforderungen anzupassen.

### Anpassen eines Designs {#steps-to-customize-a-theme-core-components}

Das Anpassen eines Designs ist ein mehrstufiger Prozess. Um das Design anzupassen, führen Sie die Schritte in der angegebenen Reihenfolge aus:

1. [Klonen eines Designs](#download-a-theme-core-components)
1. [Festlegen des Namens eines Designs](#set-name-of-theme)
1. [Anpassen eines Designs](#customize-the-theme)
1. [Testen eines Designs](#test-the-theme)
1. [Bereitstellen eines Designs](#deploy-the-theme)

Die im Dokument bereitgestellten Beispiele basieren auf dem Design **Canvas**. Sie müssen aber beachten, dass Sie jedes Design klonen und es mit denselben Anweisungen anpassen können. Diese Anweisungen gelten für jedes Design, sodass Sie Designs entsprechend Ihren spezifischen Anforderungen ändern können.

#### 1. Klonen eines Designs {#download-a-theme-core-components}

Um ein Design für die auf Kernkomponenten basierenden adaptiven Formulare zu klonen, wählen Sie eines der folgenden Designs aus:

* [Design „Canvas“](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [Design „EASEL“](https://github.com/adobe/aem-forms-theme-easel)

Gehen Sie wie folgt vor, um ein Design zu klonen:

1. Öffnen Sie die Eingabeaufforderung oder das Terminal-Fenster in Ihrer lokalen Entwicklungsumgebung.

1. Führen Sie den Befehl `git clone` aus, um ein Design zu klonen.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Ersetzen Sie den [Pfad des Git-Repositorys des Designs] durch die tatsächliche URL des entsprechenden Git-Repositorys des Designs.

   Um beispielsweise das Canvas-Design zu klonen, führen Sie den folgenden Befehl aus:

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

   Nach erfolgreicher Ausführung des Befehls verfügen Sie über eine lokale Kopie des Designs auf Ihrem Computer im Ordner `aem-forms-theme-canvas`.


#### 2. Festlegen des Namens eines Designs {#set-name-of-theme}

1. Öffnen Sie den Design-Ordner in einem einfachen Texteditor. Um beispielsweise den Ordner `aem-forms-theme-canvas` im Visual Studio Code-Editor zu öffnen.

1. Navigieren Sie zum Ordner `aem-forms-theme-canvas`.

1. Führen Sie den folgenden Befehl aus:

   ```
      code .
   ```

   ![Öffnen Sie den Design-Ordner in einem Texteditor.](/help/forms/assets/aem-forms-theme-folder-in-vs-code.png)

   Der Ordner wird in Visual Studio Code geöffnet.

1. Öffnen Sie die Datei `package.json`, um sie zu bearbeiten.

1. Legen Sie die Werte für die Attribute `name` und `version` fest.

   ![Abbildung der Namensänderung des Canvas-Designs](/help/forms/assets/changename_canvastheme.png)

   >[!NOTE]
   >
   > * Das Attribut name dient zur eindeutigen Identifizierung des Designs und der angegebene Name wird im **Stil** des **Assistent zum Erstellen von Formularen**.
   > * Sie können je nach Wahl einen Namen für Ihr Design auswählen, beispielsweise `mytheme` oder `customtheme`. In diesem Fall haben wir jedoch den Namen als `aem-forms-wknd-theme`.

1. Öffnen Sie die Datei `package-lock.json`, um sie zu bearbeiten.
1. Legen Sie die Werte für die `name` und `version` -Attribute. Stellen Sie sicher, dass die Werte für `name` und `version` -Attributen in `Package-lock`.json-Datei mit den Dateien in `Package.json` -Datei.

   ![Abbildung der Namensänderung des Canvas-Designs](/help/forms/assets/changename_canvastheme-package-lock.png)

1. (Optional) Öffnen Sie die `ReadMe` -Datei zum Bearbeiten und aktualisieren Sie den Namen des Designs.

   ![Abbildung der Namensänderung des Canvas-Designs](/help/forms/assets/changename_canvastheme-readme-file.png)

1. Speichern und schließen Sie die Dateien.

**Überlegungen beim Festlegen des Designnamens**

* Sie müssen die `@aemforms` aus dem Designnamen in `Package.json` Datei und `Package-lock.json` -Datei. Falls Sie die `@aemforms` von Ihrem benutzerdefinierten Designnamen aus, führt dies zum Fehler der Frontend-Pipeline während der Designbereitstellung.
* Es wird empfohlen, das Design zu aktualisieren `version` in `Package.json` Datei und `Package-lock.json` -Datei, um Änderungen und Verbesserungen im Zeitverlauf für Ihr Design genau widerzuspiegeln.
* Für wichtige Informationen zur Verwendung, zu Installationsanweisungen und anderen relevanten Details wird empfohlen, den Namen des Designs im Abschnitt `ReadMe` -Datei.

#### 3. Anpassen eines Designs {#customize-the-theme}

Sie können einzelne Komponenten anpassen oder Änderungen auf Design-Ebene mithilfe globaler Variablen eines Designs vornehmen. Änderungen an globalen Variablen wirken sich auf alle einzelnen Komponenten aus. Sie können beispielsweise globale Variablen verwenden, um die Rahmenfarbe aller Komponenten eines adaptiven Formulars zu ändern und eine helle Füllfarbe für einen Aktionsaufruf (CTA) mithilfe der Schaltflächenkomponente festzulegen:

* [Festlegen von Stilen auf Design-Ebene](#theme-customization-global-level)

* [Festlegen von Stilen auf Komponentenebene](#component-based-customization)

##### Festlegen von Stilen auf Design-Ebene{#theme-customization-global-level}

Die Datei `variable.scss` enthält die globalen Variablen des Designs. Durch Aktualisieren dieser Variablen können Sie stilbezogene Änderungen auf Design-Ebene vornehmen. Gehen Sie wie folgt vor, um Stile der Design-Ebene anzuwenden:

1. Öffnen Sie die Datei `<your-theme-sources>/src/site/_variables.scss`, um sie zu bearbeiten.
1. Ändern Sie den Wert einer beliebigen Eigenschaft. Die standardmäßige Fehlerfarbe ist beispielsweise `red`. Um die Fehlerfarbe von `red` in `blue` zu ändern, ändern Sie den Farb-Hex-Code von `$errorvariable`. Zum Beispiel: `$error: #196ee5`.
1. Speichern und schließen Sie die Datei.

   ![Bearbeiten eines Designs](/help/forms/assets/edit_theme.png)

Auf ähnliche Weise können Sie die Datei `variable.scss` verwenden, um Schriftfamilie und -typ, Design- und Schriftfarben, Schriftgröße, Design-Abstand, Fehlersymbol, Design-Rahmenstile und weitere Variablen festzulegen, die sich auf mehrere adaptive Formularkomponenten auswirken.

##### Festlegen von Stilen auf Komponentenebene {#component-based-customization}

Sie können auch Schriftart, Farbe, Größe und andere CSS-Eigenschaften einer bestimmten Kernkomponente des adaptiven Formulars ändern. Beispiele: Schaltfläche, Kontrollkästchen, Container, Fußzeile usw. Sie können die Schaltfläche oder das Kontrollkästchen formatieren, indem Sie die CSS-Datei der jeweiligen Komponente bearbeiten und sie an den Stil Ihrer Organisation anpassen. So passen Sie einen Stil einer Komponente an:

1. Öffnen Sie die Datei `<your-theme-sources>/src/components/<component>/<component.scss>` zur Bearbeitung. Um zum Beispiel die Schriftfarbe der Schaltflächenkomponente zu ändern, öffnen Sie die Datei `<your-theme-sources>/src/components/button/button.scss`.
1. Ändern Sie die Werte entsprechend Ihren Anforderungen. Ändern Sie beispielsweise die Farbe der Schaltflächenkomponente beim Bewegen des Mauszeigers in `green`, ändern Sie den Wert der Eigenschaft `color: $white` in der Klasse `cmp-adaptiveform-button__widget:hover` in den Hex-Code `#12B453` oder eine andere Schattierung von `green`. Der endgültige Code sieht wie folgt aus:

   ```
   .cmp-adaptiveform-button__widget:hover {
   background: $dark-gray;
   color: #12B453;
   }
   ```

1. Speichern und schließen Sie die Datei.

   ![Bearbeiten der CSS-Textbox](/help/forms/assets/edit_color_textbox.png)

   >
   >
   > Wenn ein Stil sowohl auf Design- als auch auf Komponentenebene definiert ist, hat der auf Komponentenebene definierte Stil Priorität.

#### 4. Testen eines benutzerdefinierten Designs {#test-the-theme}

Um die Änderungen in der lokalen Umgebung in der Vorschau anzuzeigen und zu testen und das Design entsprechend den Anforderungen für verschiedene AEM-Komponenten anzupassen, führen Sie die folgenden Schritte aus:

* 4.1 [Konfigurieren der lokalen Umgebung für Tests](#rename-env-file-theme-folder)
* 4.2 [Testen des Designs mithilfe der lokalen Umgebung](#start-a-local-proxy-server)

##### 4.1. Konfigurieren der lokalen Umgebung für Tests {#rename-env-file-theme-folder}

1. Öffnen Sie den Design-Ordner in einem einfachen Texteditor. Öffnen Sie beispielsweise den Ordner `aem-forms-theme-canvas` im Visual Studio Code-Editor.
1. Benennen Sie im Design-Ordner die `env_template`-Datei in eine `.env`-Datei um und fügen Sie die folgenden Parameter hinzu:

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   Die URL des Formulars lautet beispielsweise `http://localhost:4502/editor.html/content/forms/af/contactusform.html`. Die Werte sind also:

   * AEM_URL = `http://localhost:4502/`
   * AEM_ADAPTIVE_FORM = `contactusform`

1. Speichern Sie die Datei.

   ![Canvas-Design-Struktur](/help/forms/assets/env-file-canvas-theme.png)

##### 4.2 Testen des Designs mithilfe der lokalen Umgebung {#start-a-local-proxy-server}

1. Navigieren Sie zum Stammverzeichnis des Design-Ordners. In diesem Fall lautet der Name des Design-Odners `aem-forms-theme-canvas`.
1. Öffnen Sie die Eingabeaufforderung oder das Terminal.
1. Führen Sie `npm install` aus, um die Abhängigkeiten zu installieren.
1. Führen Sie `npm run live` aus, um eine Vorschau des Formulars mit dem aktualisierten Design in Ihrem lokalen Browser anzuzeigen.

   >[!NOTE]
   >
   > Wenn während der Ausführung des Befehls `npm run live` ein Fehler auftritt, führen Sie die folgenden Befehle vor dem Befehl `npm run live` aus:
   >
   > * `npm install parcel --save-dev`
   > * `npm i @parcel/transformer-sass`

Hierbei handelt es sich um ein „Hot Deployment“. Wann immer Sie also Änderungen vornehmen und die Dateien `_variables.scss` und `button.scss` speichern, sucht der Server automatisch nach Änderungen und zeigt eine Vorschau der neuesten Ausgabe an. Die Zeile `[Browsersync] File event [change]` bedeutet, dass der Server die neuesten Änderungen erkannt hat und die Änderungen in der lokalen Umgebung bereitstellt.

![Proxy-Browser-Synchronisierung](/help/forms/assets/browser_sync.png)

Entsprechend den Beispielen, die sowohl auf Design- als auch auf Komponentenebene für Design-Anpassungen bereitgestellt werden, werden die Fehlermeldungen eines adaptiven Formulars in die Farbe `blue` geändert, während die Beschriftungsfarbe für die Schaltflächenkomponente sich in `green` ändert, wenn Sie den Mauszeiger darüber bewegen.

**Vorschau des Stils auf Design-Ebene**

![Beispiel: Fehlerfarbe auf Blau gesetzt](/help/forms/assets/theme-level-changes.png)

**Vorschau des Stils auf Komponentenebene**

![Beispiel: Hover-Farbe auf Grün gesetzt](/help/forms/assets/button-customization.png)

###### Testen des Designs für Formulare, die in einer Cloud Service-Umgebung gehostet werden

Sie können das Design auch für das adaptive Formular testen, das auf Ihrer AEM Forms as a Cloud Service-Instanz gehostet wird. Führen Sie die folgenden Schritte aus, um die lokale Umgebung für das Testen der Designs mit dem auf der Cloud-Instanz gehosteten adaptiven Formular zu konfigurieren und festzulegen:

1. Öffnen Sie den Design-Ordner in einem einfachen Texteditor. Öffnen Sie beispielsweise den Ordner `aem-forms-theme-canvas` im Visual Studio Code-Editor.
1. Benennen Sie die `env_template`-Datei in eine `.env`-Datei um und fügen Sie die folgenden Parameter hinzu:

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   Beispielsweise lautet die URL des Formulars in der Cloud-Umgebung `https://author-XXXX.adobeaemcloud.com/editor.html/content/forms/af/contactusform.html`. Die Werte sind also:

   * AEM_URL = `https://author-XXXX-cmstg.adobeaemcloud.com/`
   * AEM_ADAPTIVE_FORM = `contactusform`
1. Speichern Sie die Datei.
1. Erstellen Sie eine lokale Benutzerin oder einen lokalen Benutzer.

   >[!NOTE]
   >
   > So erstellen Sie eine lokale Benutzerin oder einen lokalen Benutzer:
   >
   > * Navigieren Sie zu **[!UICONTROL AEM-Startseite]** > **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
   > * Stellen Sie sicher, dass die Benutzerin bzw. der Benutzer Mitglied der Gruppe `forms-users` ist.

1. Navigieren Sie zum Stammverzeichnis des Design-Ordners. In diesem Fall lautet der Name des Design-Ordners `aem-forms-theme-canvas`.
1. Führen Sie `npm run live` aus und Sie werden zu einem lokalen Browser weitergeleitet.
1. Klicken Sie auf `SIGN IN LOCALLY (ADMIN TASKS ONLY)` und melden Sie sich mit den Anmeldeinformationen der lokalen Benutzerin bzw. des lokalen Benutzers an.

Sie können eine Vorschau des adaptiven Formulars mit den neuesten Änderungen anzeigen. Sobald Sie mit den Änderungen in einem Design-Ordner zufrieden sind, stellen Sie das Design mithilfe der Frontend-Pipeline in Ihrer AEM Cloud Service-Umgebung bereit.

#### 5. Bereitstellen eines Designs {#deploy-the-theme}

So stellen Sie das Design mithilfe der Frontend-Pipeline in Ihrer Cloud Service-Umgebung bereit:

* 5.1 [Erstellen eines Repositorys für das Design](#create-a-new-theme-repo)
* 5.2 [Übertragen der Änderungen in das Repository](#committing-the-changes)
* 5.3. [Ausführen der Frontend-Pipeline](#run-a-frontend-pipeline)

##### 5.1 Erstellen eines Repositorys für das Design{#create-a-new-theme-repo}

Sie benötigen ein Repository, um das Design bereitzustellen. Melden Sie sich bei Ihrem [AEM Cloud Manager-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git) an und fügen Sie ein neues Repository für Ihr Design hinzu.

1. Erstellen Sie ein neues Repository für das Design, indem Sie auf **[!UICONTROL Repositorys]** > **[!UICONTROL Repository hinzufügen]** klicken.

   ![Erstellen eines neuen Design-Repositorys](/help/forms/assets/createrepo_canvastheme.png)


1. Geben Sie den **Repository-Namen** im Dialogfeld **Repository hinzufügen** an. Der angegebene Name lautet beispielsweise `custom-canvas-theme-repo`.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Hinzufügen eines Repository für das Canvas-Design-Repo](/help/forms/assets/addcanvasthemerepo.png)

1. Klicken Sie auf **[!UICONTROL Repository-URL kopieren]**, um die URL des Repositorys zu kopieren.

   ![URL des Canvas-Designs](/help/forms/assets/copyurl_canvastheme.png)

   >[!NOTE]
   > 
   > * Sie können ein einziges Repository für mehrere Designs verwenden.
   > * Um verschiedene Designs bereitzustellen, müssen Sie separate Frontend-Pipelines erstellen.
   >* Sie können beispielsweise dasselbe Repository, z. B. `custom-canvas-theme-repo`, für das Canvas-Design, das WKND-Design und das EASEL-Design verwenden. Um die Designs bereitzustellen, müssen Sie jedoch separate Frontend-Pipelines erstellen. Zukünftige Anpassungen für ein bestimmtes Design werden mithilfe der entsprechenden Frontend-Pipeline bereitgestellt.

##### 5.2. Übertragen von Änderungen in das Repository {#committing-the-changes}

Nun können Sie die Änderungen in das Design-Repository Ihres AEM Forms-Cloud-Service übertragen.

1. Navigieren Sie zum Stammverzeichnis des Design-Ordners. In diesem Fall lautet der Name des Design-Ordners `aem-forms-theme-canvas`.
1. Öffnen Sie die Eingabeaufforderung oder das Terminal.
1. Führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus:

   ```
   git remote add [alias-name-for-repository] [URL of repository]
   git add .
   git commit
   git push [name-for-createdrepository]
   ```

   Zum Beispiel:

   ```
   git remote add canvascloudthemerepo https://git.cloudmanager.adobe.com/stage-aemformsdev/customcanvastheme/
   git add .
   git commit
   git push canvascloudthemerepo 
   ```

   ![Vorgenommene Änderungen](/help/forms/assets/cmd_git_push.png)



##### 5.3. Ausführen der Frontend-Pipeline {#run-a-frontend-pipeline}

Das Design wird mithilfe der [Frontend-Pipeline bereitgestellt.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html?lang=de). Um das Design bereitzustellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrem AEM Cloud Manager-Repository an.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** im Abschnitt **[!UICONTROL Pipelines]**.
1. Wählen Sie je nach Cloud-Service-Umgebung **[!UICONTROL Produktionsfremde Pipeline hinzufügen]** oder **[!UICONTROL Produktions-Pipeline hinzufügen]** aus. Hier ist beispielsweise **[!UICONTROL Produktions-Pipeline hinzufügen]** ausgewählt.
1. Geben Sie im Dialogfeld **[!UICONTROL Produktions-Pipeline hinzufügen]** als Teil der **[!UICONTROL Konfigurationsschritte]** den Namen für Ihre Pipeline an. Beispielsweise lautet der Name der Pipeline `customcanvastheme`.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie die Optionen **[!UICONTROL Zielgerichtete Bereitstellung]** > **[!UICONTROL Frontend-Code]** in den Schritten 
unter **[!UICONTROL Quell-Code]** aus.
1. Wählen Sie die Werte für das **[!UICONTROL Repository]** und die **[!UICONTROL Git-Verzweigung]** aus, die Ihre neuesten Änderungen aufweisen. Hier lautet beispielsweise der ausgewählte Repository-Name `custom-canvas-theme-repo` und die Git-Verzweigung `main`.
1. Wählen Sie als **[!UICONTROL Code-Speicherort]** „`/`“ aus, wenn sich Ihre Änderungen im Stammordner befinden.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Frontend-Pipeline erstellen](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   Wenn die Einrichtung der Pipeline abgeschlossen ist, wird die Karte mit dem Aktionsaufruf aktualisiert.

1. Klicken Sie mit der rechten Maustaste auf die erstellte Pipeline.
1. Klicken Sie auf **[!UICONTROL Ausführen]** .

   ![run-a-pipeline](/help/forms/assets/canvas-theme-run-pipeline.png)

Sobald die Erstellung abgeschlossen ist, steht das Design in der Autoreninstanz zur Verwendung zur Verfügung. Es wird unter der Registerkarte **[!UICONTROL Stil]** im Assistenten zur Erstellung adaptiver Formulare beim Erstellen eines adaptiven Formulars angezeigt.

![Benutzerdefiniertes Design auf der Registerkarte „Stil“](/help/forms/assets/custom-theme-style-tab.png)

## Anwenden eines Designs auf ein adaptives Formular {#using-theme-in-adaptive-form}

Schritte zum Anwenden eines Designs auf ein adaptives Formular:

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an.

1. Wählen Sie **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.

1. Klicken Sie auf **Erstellen** > **Adaptive Formulare**. Der Assistent zum Erstellen des adaptiven Formulars wird geöffnet.

1. Wählen Sie die Kernkomponentenvorlage auf der Registerkarte **Quelle**.
1. Wählen Sie das Design auf der Registerkarte **Stil** aus.
1. Klicken Sie auf **Erstellen**.

Designs für adaptive Formulare werden als Teil einer Vorlage für adaptive Formulare verwendet, um beim Erstellen eines adaptiven Formulars Stile zu definieren.

## Best Practices {#best-practices}

* **Vermeiden von Assets aus einem anderen Design**

  Bei der Bearbeitung von Designs können Sie Assets (etwa Bilder) aus anderen Designs durchsuchen und hinzufügen. Angenommen, Sie bearbeiten den Hintergrund einer Seite. Wenn Sie beispielsweise **[!UICONTROL Seite]** ![Bearbeiten-Schaltfläche](assets/edit-button.png) > **[!UICONTROL Hintergrund]** > **[!UICONTROL Hinzufügen]** > **[!UICONTROL Bild]** auswählen, wird ein Dialogfeld angezeigt, in dem Sie Bilder aus anderen Designs suchen und hinzufügen können.

  Es können Probleme im aktuellen Design auftreten, wenn ein Asset aus einem anderen Design hinzugefügt und dieses andere Design später verschoben oder gelöscht wird. Wir empfehlen daher, keine Assets aus anderen Designs zu suchen und hinzuzufügen.

* **Ändern der Layout-Breite des Container-Bereichs**

  Es wird nicht empfohlen, die Layout-Breite des Container-Bereichs zu ändern. Wenn Sie die Breite eines Container-Bereichs angeben, wird er statisch und passt sich nicht mehr an unterschiedliche Displays an.

* **Verwendung des Formular- oder Design-Editors für die Arbeit mit Kopf- und Fußzeile**

  Verwenden Sie den Design-Editor, wenn Sie Kopf- und Fußzeilen mit Formatierungsoptionen wie Schriftschnitt, Hintergrund und Transparenz formatieren möchten.
Wenn Sie Informationen wie ein Logo, einen Firmennamen in der Kopfzeile und Copyright-Informationen in der Fußzeile angeben möchten, verwenden Sie dazu die im Formular-Editor verfügbaren Optionen.

## Häufig gestellte Fragen {#faq}

**Frage:** Welche Anpassung hat Vorrang, wenn Anpassungen in einem Design-Ordner sowohl auf der globalen Ebene als auch auf der Komponentenebene vorgenommen werden?

**Antwort:** Wenn Anpassungen sowohl auf globaler als auch auf Komponentenebene vorgenommen werden, hat die Anpassung auf Komponentenebene Priorität.

<!--

## See next

* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Generate Document of Record for Adaptive Forms (Core Components](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Create an Adaptive Forms with Repeatable sections](/help/forms/create-forms-repeatable-sections.md)
* [Sample themes templates and form data models](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)


>[!MORELIKETHIS]
>
>* [Enable Adaptive Forms Core Components on AEM Forms as a Cloud Service and local development environment](/help/forms/enable-adaptive-forms-core-components.md)

-->


## Siehe auch {#see-also}

{{see-also}}
* [Festlegen des Layouts von Formularen für verschiedene Bildschirmgrößen und Gerätetypen](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Generieren eines Datensatzdokuments für adaptive Formulare (Kernkomponenten)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Erstellen eines adaptiven Formulars mit wiederholbaren Abschnitten](/help/forms/create-forms-repeatable-sections.md)
* [Beispielthemenvorlagen und Formulardatenmodelle](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=de)
* [Aktivieren der Kernkomponenten für adaptive Formulare in AEM Forms as a Cloud Service und lokaler Entwicklungsumgebung](/help/forms/enable-adaptive-forms-core-components.md)
