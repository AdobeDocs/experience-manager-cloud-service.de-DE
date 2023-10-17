---
title: Wie können Designs in Adaptive Forms erstellt und verwendet werden?
description: Sie können Designs verwenden, um ein adaptives Formular mithilfe von Kernkomponenten zu gestalten und eine visuelle Identität bereitzustellen. Ein Design kann für beliebig viele adaptive Formulare gemeinsam genutzt werden.
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: 7a65aa82792500616f971df52b8ddb6d893ab89d
workflow-type: tm+mt
source-wordcount: '2698'
ht-degree: 18%

---

# Designs in Adaptive Forms {#themes-for-af-using-core-components}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-or-customize-themes-for-adaptive-forms-core-components.html) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können Designs erstellen und anwenden, um ein adaptives Formular zu formatieren. Zu einem Design gehören Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider. Ein Design wird unabhängig voneinander ohne Verweis auf ein adaptives Formular verwaltet und kann über mehrere adaptive Forms hinweg wiederverwendet werden.

## Verfügbare Designs

Forms as Cloud Service bietet die folgenden aufgelisteten Designs für Kernkomponenten-basiertes adaptives Forms:

* [Design „Canvas“](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-Design](https://github.com/adobe/aem-forms-theme-easel)

## Grundlegendes zur Struktur der Themen

Ein Design ist ein Paket, das die CSS-Datei, JavaScript-Dateien und Ressourcen (wie Symbole) umfasst, die den Stil Ihres adaptiven Forms definieren. Ein Design für adaptives Formular folgt einer bestimmten Organisation, die aus den folgenden Komponenten besteht:

* `src/theme.scss`: Dieser Ordner enthält die CSS-Datei, die einen breiten Einfluss auf das gesamte Design hat. Es dient als zentralisierter Ort zur Definition und Verwaltung des Stils und Verhaltens Ihres Designs. Durch Bearbeitung dieser Datei können Sie Änderungen vornehmen, die im gesamten Design allgemein angewendet werden und das Erscheinungsbild und die Funktionalität Ihrer adaptiven Forms- und AEM Sites-Seiten beeinflussen.

* `src/site`: Dieser Ordner enthält CSS-Dateien, die auf die Seite einer gesamten AEM Site angewendet werden. Diese Dateien bestehen aus Code und Stilen, die sich auf die Funktionalität und das Layout der Seite Ihrer AEM auswirken. Alle hier vorgenommenen Änderungen werden auf allen Seiten Ihrer Site übernommen. [Wann sollte es verwendet werden?]

* `src/components`: Die CSS-Dateien in diesem Ordner sind für einzelne AEM Kernkomponenten entwickelt. Jeder dedizierte Ordner für eine Komponente enthält `.scss` -Datei, die diese bestimmte Komponente in einem adaptiven Formular formatiert. Beispielsweise enthält die Datei /src/components/accordion/_accordion.scss Stilinformationen für die Adaptive Forms Accordion-Komponente.

  ![Designstruktur für adaptives Formular](/help/forms/assets/theme_structure.png)

* `src/resources`: Dieser Ordner enthält statische Dateien wie Symbole, Logos und Schriftarten. Diese Ressourcen werden verwendet, um die visuellen Elemente und das Gesamtdesign Ihres Designs zu verbessern.

## Erstellen von Designs

Forms bietet die folgenden aufgelisteten Designs für die auf Kernkomponenten basierende adaptive Forms.

* [Design „Canvas“](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-Design](https://github.com/adobe/aem-forms-theme-easel)

Sie können [Anpassen dieser Designs, um ein neues Design zu erstellen](#customize-a-theme-core-components).

![Workflow für die Designanpassung](/help/forms/assets/workflow-of-customization-of-theme.png)

## Anpassen eines Designs {#customize-a-theme-core-components}

Das Anpassen eines Designs bezieht sich auf den Prozess der Änderung und Personalisierung des Erscheinungsbilds eines Designs. Wenn Sie ein Design anpassen, ändern Sie dessen Design-Elemente, Layout, Farben, Typografie und manchmal den zugrunde liegenden Code. Damit können Sie ein einzigartiges und maßgeschneidertes Erscheinungsbild für Ihre Website oder Anwendung erstellen und dabei die grundlegende Struktur und Funktionalität des Designs beibehalten.

### Voraussetzungen {#prerequisites-to-customize}

* Machen Sie sich mit [Einrichten einer Pipeline in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline) und über grundlegende Kenntnisse zum Einrichten einer Pipeline verfügen, können Sie Ihre Designanpassungen effizient verwalten und bereitstellen.
* Erfahren Sie, wie [Konfigurieren eines Benutzers mit der Rolle &quot;Mitarbeiter&quot;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html?lang=de). Wenn Sie verstehen, wie Sie einen Benutzer mit der Rolle &quot;contributor&quot;konfigurieren, können Sie die erforderlichen Berechtigungen für die Designanpassung erteilen.
* Installieren Sie die neueste Version von [Apache Maven.](https://maven.apache.org/download.cgi) Apache Maven ist ein Werkzeug zur Automatisierung von Builds, das häufig für Java™-Projekte verwendet wird. Durch die Installation der neuesten Version stellen Sie sicher, dass Sie über die erforderlichen Abhängigkeiten für die Designanpassung verfügen.
* Installieren Sie einen Nur-Text-Editor. Beispielsweise Microsoft® Visual Studio-Code. Die Verwendung eines Texteditors wie Microsoft® Visual Studio Code bietet eine benutzerfreundliche Umgebung zum Bearbeiten und Ändern von Designdateien.

### Einrichten Ihrer Arbeitsumgebung

* [Aktivieren der adaptiven Forms-Kernkomponenten](/help/forms/enable-adaptive-forms-core-components.md)  für Ihre lokale Entwicklungs- und Cloud Service-Umgebung.
* Konfigurieren [Front-End-Implementierungs-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html) für Ihre Cloud Service-Umgebung. Alternativ können Sie die Pipeline später konfigurieren, sodass Sie das Thema vor der Einrichtung der Bereitstellungs-Pipeline flexibel priorisieren und verfeinern können.

<!-- 
To deploy your themes to a Forms as a Cloud Service environment, first test theme on a local development environment to address any issues. Once the theme is tested, configure the front-end deployment pipeline, which is responsible for deploying the themes.

These themes are deployed to a Forms as a Cloud Service environment via the front-end pipeline. You can configure the pipeline later also, after testing the theme on a local development environment. 

-->

Nachdem Sie die Voraussetzungen kennengelernt und die Entwicklungsumgebung konfiguriert haben, sind Sie gut darauf vorbereitet, Ihr Thema an Ihre spezifischen Anforderungen anzupassen.

### Anpassen eines Designs {#steps-to-customize-a-theme-core-components}

Das Anpassen eines Designs ist ein mehrstufiger Prozess. Um das Design anzupassen, führen Sie die Schritte in der angegebenen Reihenfolge aus:

1. [Klonen eines Designs](#download-a-theme-core-components)
1. [Namen eines Designs festlegen](#set-name-of-theme)
1. [Anpassen eines Designs](#customize-the-theme)
1. [Testen eines Designs](#test-the-theme)
1. [Bereitstellen eines Designs](#deploy-the-theme)

Die im Dokument bereitgestellten Beispiele basieren auf dem **Arbeitsfläche** -Design, aber es ist wichtig zu beachten, dass Sie jedes Thema klonen und es mit denselben Anweisungen anpassen können. Diese Anweisungen gelten für jedes Thema, sodass Sie Designs entsprechend Ihren spezifischen Anforderungen ändern können.

#### 1. Ein Design klonen {#download-a-theme-core-components}

Um ein Design für die auf Kernkomponenten basierende adaptive Forms zu klonen, wählen Sie eines der folgenden Designs:

* [Design „Canvas“](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-Design](https://github.com/adobe/aem-forms-theme-easel)

Um ein Design zu klonen, führen Sie die folgenden Anweisungen aus:

1. Öffnen Sie die Eingabeaufforderung oder das Terminal-Fenster in Ihrer lokalen Entwicklungsumgebung.

1. Führen Sie die `git clone` -Befehl zum Klonen eines Designs.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Ersetzen Sie die [Pfad des Git-Repositorys des Designs] mit der tatsächlichen URL des entsprechenden Git-Repositorys des Designs

   Um beispielsweise das Canvas-Design zu klonen, führen Sie den folgenden Befehl aus:

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

   Nachdem Sie den Befehl erfolgreich ausgeführt haben, steht auf Ihrem Computer eine lokale Kopie des Designs im  `aem-forms-theme-canvas` Ordner.


#### 2. Namen eines Designs festlegen {#set-name-of-theme}

1. Öffnen Sie den Ordner &quot;Design&quot;in einem Texteditor. Um beispielsweise die `aem-forms-theme-canvas` Ordner im Visual Studio-Code-Editor.

1. Navigieren Sie zum Ordner `aem-forms-theme-canvas`.

1. Führen Sie den folgenden Befehl aus:

   ```
         code .
   ```

   ![Öffnen Sie den Designordner in einem Texteditor.](/help/forms/assets/aem-forms-theme-folder-in-vs-code.png)

   Der Ordner wird im Visual Studio-Code geöffnet.

1. Öffnen Sie die Datei `package.json`, um sie zu bearbeiten.

1. Legen Sie die Werte für die `name` und `description` -Attribute.

   Das Attribut name wird verwendet, um das Design eindeutig zu identifizieren, z. B. &quot;aem-forms-wknd-theme&quot;, das im **Stil** Tab von **Assistent zum Erstellen von Formularen**. Das Attribut description enthält zusätzliche Details zum Thema, einschließlich seines Zwecks und der Szenarien, für die es entwickelt wurde. Sie können auch die Version, Beschreibung und Lizenz für das Design angeben.

1. Speichern und schließen Sie die Datei.

![Bild beim Namen des Arbeitsflächendesigns ändern](/help/forms/assets/changename_canvastheme.png)


#### 3. Anpassen eines Designs {#customize-the-theme}

Sie können einzelne Komponenten anpassen oder Änderungen auf Designebene mithilfe globaler Variablen eines Designs vornehmen. Änderungen an globalen Variablen wirken sich auf alle einzelnen Komponenten aus. Sie können beispielsweise globale Variablen verwenden, um die Rahmenfarbe aller Komponenten eines adaptiven Formulars und eine helle Füllfarbe zu ändern, um CTA (Aktionsaufruf) mithilfe der Schaltflächenkomponente festzulegen:

* [Festlegen von Stilen auf Designebene](#theme-customization-global-level)

* [Festlegen von Stilen auf Komponentenebene](#component-based-customization)

##### Festlegen von Stilen auf Designebene{#theme-customization-global-level}

Die `variable.scss` -Datei enthält die globalen Variablen des Designs. Durch Aktualisierung dieser Variablen können Sie stilistisch relevante Änderungen auf der Designebene vornehmen. Gehen Sie wie folgt vor, um Stile auf Designebene anzuwenden:

1. Öffnen Sie die Datei `<your-theme-sources>/src/site/_variables.scss`, um sie zu bearbeiten.
1. Ändern Sie den Wert einer beliebigen Eigenschaft. Die standardmäßige Fehlerfarbe lautet beispielsweise `red`. So ändern Sie die Fehlerfarbe von `red` nach `blue`ändern Sie den Farb-Hex-Code des `$errorvariable`. Beispiel: `$error: #196ee5`.
1. Speichern und schließen Sie die Datei.

   ![Bearbeiten eines Designs](/help/forms/assets/edit_theme.png)

Auf ähnliche Weise können Sie die `variable.scss` -Datei, um Schriftfamilie und -typ, Design- und Schriftfarben, Schriftgröße, Designabstand, Fehlersymbol, Designrahmenstile und mehr Variablen festzulegen, die sich auf mehrere adaptive Formularkomponenten auswirken.

##### Festlegen von Stilen auf Komponentenebene {#component-based-customization}

Sie können auch Schriftart, Farbe, Größe und andere CSS-Eigenschaften einer bestimmten Kernkomponente des adaptiven Formulars ändern. Beispiel: Schaltfläche, Kontrollkästchen, Container, Fußzeile usw. Sie können die Schaltfläche oder das Kontrollkästchen formatieren, indem Sie die CSS-Datei der jeweiligen Komponente bearbeiten und sie an den Stil Ihres Unternehmens anpassen. So passen Sie einen Stil einer Komponente an:

1. Öffnen Sie die Datei `<your-theme-sources>/src/components/<component>/<component.scss>` zur Bearbeitung. Um beispielsweise die Schriftfarbe der Schaltflächenkomponente zu ändern, öffnen Sie die `<your-theme-sources>/src/components/button/button.scss`, Datei .
1. Ändern Sie den Wert von beliebig gemäß Ihren Anforderungen. So ändern Sie beispielsweise die Farbe der Schaltflächenkomponente beim Maushover auf `green`, ändern Sie den Wert der `color: $white` -Eigenschaft in der `cmp-adaptiveform-button__widget:hover` -Klasse in Hex-Code `#12B453` oder anderen Schatten von `green`. Der endgültige Code sieht wie folgt aus:

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

Um die Änderungen in der lokalen Umgebung in der Vorschau anzuzeigen und zu testen und das Design entsprechend den Anforderungen für verschiedene AEM anzupassen, führen Sie die folgenden Schritte aus:

* 4,1 [Lokale Umgebung für Tests konfigurieren](#rename-env-file-theme-folder)
* 4,2 [Testen des Designs mithilfe der lokalen Umgebung](#start-a-local-proxy-server)

##### 4.1. Konfigurieren der lokalen Umgebung für Tests {#rename-env-file-theme-folder}

1. Öffnen Sie den Ordner &quot;Design&quot;in einem Texteditor. Öffnen Sie beispielsweise die `aem-forms-theme-canvas` Ordner im Visual Studio-Code-Editor.
1. Benennen Sie die `env_template` Datei in `.env` -Datei im Ordner &quot;Design&quot;und fügen Sie die folgenden Parameter hinzu:

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   Beispielsweise lautet die URL des Formulars `http://localhost:4502/editor.html/content/forms/af/contactusform.html`. Die Werte von:

   * AEM_URL = `http://localhost:4502/`
   * AEM_ADAPTIVE_FORM = `contactusform`

1. Speichern Sie die Datei.

   ![Canvas-Design-Struktur](/help/forms/assets/env-file-canvas-theme.png)

##### 4.2 Thema mithilfe einer lokalen Umgebung testen {#start-a-local-proxy-server}

1. Navigieren Sie zum Stammverzeichnis des Designordners. In diesem Fall lautet der Name des Designordners `aem-forms-theme-canvas`.
1. Öffnen Sie die Eingabeaufforderung oder das Terminal.
1. Ausführen `npm install` , um die Abhängigkeiten zu installieren.
1. Ausführen `npm run live` , um eine Vorschau des Formulars mit dem aktualisierten Design in Ihrem lokalen Browser anzuzeigen.

   >[!NOTE]
   >
   > Wenn während der Ausführung des `npm run live` Befehl, führen Sie die folgenden Befehle aus, bevor `npm run live` command:
   >
   > * `npm install parcel --save-dev`
   > * `npm i @parcel/transformer-sass`

Dies ist eine heiße Implementierung. Wann immer Sie also Änderungen vornehmen und die `_variables.scss` und `button.scss` -Dateien, wählt der Server automatisch die Änderungen aus und zeigt eine Vorschau der neuesten Ausgabe an. Die Zeile `[Browsersync] File event [change]` bedeutet, dass der Server die neuesten Änderungen erkannt hat und die Änderungen in der lokalen Umgebung bereitstellt.

![Proxy-Browser-Synchronisierung](/help/forms/assets/browser_sync.png)

Nach den Beispielen, die sowohl auf Design- als auch auf Komponentenebene für Designanpassungen bereitgestellt werden, werden die Fehlermeldungen eines adaptiven Formulars in `blue` Farbe, während sich die Beschriftungsfarbe für die Schaltflächenkomponente in `green` beim Bewegen der Maus.

**Vorschau des Designstufenstils**

![Beispiel: Fehlerfarbe auf blau eingestellt](/help/forms/assets/theme-level-changes.png)

**Vorschau des Stils auf Komponentenebene**

![Beispiel: Hover-Farbe auf Grün eingestellt](/help/forms/assets/button-customization.png)

###### Testen des Designs für Formulare, die in einer Cloud Service-Umgebung gehostet werden

Sie können das Design auch für das adaptive Formular testen, das auf Ihrer as a Cloud Service AEM Forms-Instanz gehostet wird. Führen Sie die folgenden Schritte aus, um die lokale Umgebung für das Testen der Designs mit dem auf der Cloud-Instanz gehosteten adaptiven Forms zu konfigurieren und festzulegen:

1. Öffnen Sie den Ordner &quot;Design&quot;in einem Texteditor. Öffnen Sie beispielsweise die `aem-forms-theme-canvas` Ordner im Visual Studio-Code-Editor.
1. Benennen Sie die `env_template` Datei in `.env` und fügen Sie die folgenden Parameter hinzu:

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   Beispielsweise lautet die URL des Formulars in der Cloud-Umgebung . `https://author-XXXX.adobeaemcloud.com/editor.html/content/forms/af/contactusform.html`. Die Werte von:

   * AEM_URL = `https://author-XXXX-cmstg.adobeaemcloud.com/`
   * AEM_ADAPTIVE_FORM = `contactusform`
1. Speichern Sie die Datei.
1. Erstellen Sie einen lokalen Benutzer.

   >[!NOTE]
   >
   > So erstellen Sie einen lokalen Benutzer:
   >
   > * Navigieren Sie zu **[!UICONTROL AEM]** > **[!UICONTROL Instrumente]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]** .
   > * Stellen Sie sicher, dass der Benutzer Mitglied der `forms-users` hinzugefügt.

1. Navigieren Sie zum Stammverzeichnis des Designordners. In diesem Fall lautet der Name des Designordners `aem-forms-theme-canvas`.
1. Ausführen `npm run live` und Sie werden zu einem lokalen Browser weitergeleitet.
1. Klicks `SIGN IN LOCALLY (ADMIN TASKS ONLY)` und melden Sie sich mit den Anmeldeinformationen des lokalen Benutzers an.

Sie können eine Vorschau des adaptiven Formulars mit den neuesten Änderungen anzeigen. Sobald Sie mit den Änderungen in einem Designordner zufrieden sind, stellen Sie das Design mithilfe der Frontend-Pipeline in Ihrer AEM Cloud Service-Umgebung bereit.

#### 5. Bereitstellen eines Designs {#deploy-the-theme}

So stellen Sie das Design mithilfe der Frontend-Pipeline in Ihrer Cloud Service-Umgebung bereit:

* 5,1 [Repository für Design erstellen](#create-a-new-theme-repo)
* 5,2 [Übertragen Sie die Änderungen an das Repository.](#committing-the-changes)
* 5,3 [Ausführen der Frontend-Pipeline](#run-a-frontend-pipeline)

##### 5.1 Repository für Design erstellen{#create-a-new-theme-repo}

Sie benötigen ein Repository, um das Design bereitzustellen. Melden Sie sich bei Ihrer [AEM Cloud Manager-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git) und fügen Sie ein neues Repository für Ihr Design hinzu.

1. Erstellen Sie ein neues Repository für Design, indem Sie auf **[!UICONTROL Repositorys]** > **[!UICONTROL Repository hinzufügen]**.

   ![Erstellen eines neuen Design-Repo](/help/forms/assets/createrepo_canvastheme.png)


1. Geben Sie die **Repository-Name** im **Repository hinzufügen** Dialogfeld. Der angegebene Name lautet beispielsweise `custom-canvas-theme-repo`.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Hinzufügen eines Repository für das Canvas-Design-Repo](/help/forms/assets/addcanvasthemerepo.png)

1. Klicks **[!UICONTROL Repository-URL kopieren]** zum Kopieren der URL des Repositorys.

   ![URL des Canvas-Designs](/help/forms/assets/copyurl_canvastheme.png)

   >[!NOTE]
   > 
   > * Sie können ein einzelnes Repository für mehrere Designs verwenden.
   > * Um verschiedene Designs bereitzustellen, müssen Sie separate Front-End-Pipelines erstellen.
   >* Sie können beispielsweise dasselbe Repository wie `custom-canvas-theme-repo`, für Canvas-Design, WKND-Design und EASEL-Design. Um die Designs bereitzustellen, müssen Sie jedoch separate Front-End-Pipelines erstellen. Zukünftige Anpassungen für ein bestimmtes Design werden mithilfe der entsprechenden Frontend-Pipeline bereitgestellt.

##### 5.2. Übertragen Sie die Änderungen in das Repository {#committing-the-changes}

Nun können Sie die Änderungen an das Design-Repository Ihres AEM Forms-Cloud Service übertragen. .

1. Navigieren Sie zum Stammverzeichnis des Designordners.  In diesem Fall lautet der Name des Designordners `aem-forms-theme-canvas`.
1. Öffnen Sie die Eingabeaufforderung oder das Terminal.
1. Führen Sie den folgenden Befehl in der angegebenen Reihenfolge aus:

   ```
   git remote add [alias-name-for-repository] [URL of repository]
   git add .
   git commit
   git push [name-for-createdrepository]
   ```

   Beispiel:

   ```
   git remote add canvascloudthemerepo https://git.cloudmanager.adobe.com/stage-aemformsdev/customcanvastheme/
   git add .
   git commit
   git push canvascloudthemerepo 
   ```

   ![Vorgenommene Änderungen](/help/forms/assets/cmd_git_push.png)



##### 5.3 Ausführen der Frontend-Pipeline {#run-a-frontend-pipeline}

Das Design wird mithilfe der [Front-End-Pipeline.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html). Um Design bereitzustellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrem AEM Cloud Manager-Repository an.
1. Klicks **[!UICONTROL Hinzufügen]** -Schaltfläche in der **[!UICONTROL Pipelines]** Abschnitt.
1. Auswählen **[!UICONTROL Hinzufügen einer produktionsfremden Pipeline]** oder **[!UICONTROL Produktions-Pipeline hinzufügen]** basierend auf der Cloud Service-Umgebung. Hier finden Sie beispielsweise die **[!UICONTROL Produktions-Pipeline hinzufügen]** ausgewählt ist.
1. Im **[!UICONTROL Produktions-Pipeline hinzufügen]** Dialog als Teil der **[!UICONTROL Konfiguration]** -Schritte, geben Sie den Namen für Ihre Pipeline an. Beispielsweise lautet der Name der Pipeline `customcanvastheme`.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie die **[!UICONTROL Zielgerichtete Implementierung]** > die **[!UICONTROL Frontend-Code]** -Optionen in der **[!UICONTROL Quellcode]** Schritte.
1. Wählen Sie die **[!UICONTROL Repository]** und **[!UICONTROL Git-Verzweigung]** -Werte, die Ihre neuesten Änderungen aufweisen. Hier lautet beispielsweise der ausgewählte Repository-Name . `custom-canvas-theme-repo` und die Git-Verzweigung `main`.
1. Wählen Sie die **[!UICONTROL Code-Speicherort]** as `/`, wenn sich Ihre Änderungen im Stammordner befinden.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Front-End-Pipeline erstellen](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   Nachdem die Pipelineeinrichtung abgeschlossen ist, wird die Aktionsaufruf-Karte aktualisiert.

1. Klicken Sie mit der rechten Maustaste auf die erstellte Pipeline.
1. Klicken Sie auf **[!UICONTROL Ausführen]** .

   ![run-a-piplein](/help/forms/assets/canvas-theme-run-pipeline.png)

Sobald der Build abgeschlossen ist, wird das Design in der Autoreninstanz zur Verwendung verfügbar. Sie wird unter dem **[!UICONTROL Stil]** Registerkarte im Assistenten zur Erstellung adaptiver Formulare beim Erstellen eines neuen adaptiven Formulars.

![Benutzerdefiniertes Design auf der Registerkarte &quot;Stil&quot;](/help/forms/assets/custom-theme-style-tab.png)

## Anwenden eines Designs auf ein adaptives Formular {#using-theme-in-adaptive-form}

Schritte zum Anwenden eines Designs auf ein adaptives Formular:

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an.

1. Tippen Sie auf **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**. 

1. Klicken Sie auf **Erstellen** > **Adaptive Formulare**. Der Assistent zum Erstellen des adaptiven Formulars wird geöffnet.

1. Wählen Sie die Kernkomponentenvorlage auf der Registerkarte **Quelle**.
1. Wählen Sie das Design im **Stil** Registerkarte.
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

## Häufig gestellte Fragen  {#faq}

**F:** Welche Anpassung hat bei der Anpassung in einem Designordner sowohl auf globaler Ebene als auch auf Komponentenebene Priorität?

**Ans:** Wenn Anpassungen sowohl auf globaler als auch auf Komponentenebene vorgenommen werden, hat die Anpassung auf Komponentenebene Priorität.

## Siehe nächste Punkte

* [Festlegen des Layouts von Formularen für verschiedene Bildschirmgrößen und Gerätetypen](/help/sites-cloud/authoring/features/responsive-layout.md)
* [Generieren des Datensatzdokuments für adaptive Forms (Kernkomponenten)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Erstellen einer adaptiven Forms mit wiederholbaren Abschnitten](/help/forms/create-forms-repeatable-sections.md)
* [Vorlagen für Musterdesigns und Formulardatenmodelle](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)


## Verwandter Artikel {#related-article}

* [Aktivieren der Kernkomponenten für adaptive Formulare in AEM Forms as a Cloud Service und lokaler Entwicklungsumgebung](/help/forms/enable-adaptive-forms-core-components.md)
* [Erstellen eines eigenständigen, auf Kernkomponenten basierenden adaptiven Formulars](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=de)
