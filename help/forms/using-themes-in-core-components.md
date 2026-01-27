---
title: Erstellen und Verwenden von Designs in adaptiven Forms
description: Mithilfe von Designs und unter Verwendung von Kernkomponenten können Sie ein adaptives Formular formatieren und ihm eine visuelle Identität verleihen. Ein Design kann für beliebig viele adaptive Formulare gemeinsam genutzt werden.
keywords: Formular-Builder-Designs, Kernkomponenten für adaptive Formulare, Formular-Design-Builder, Formatierung adaptiver Formulare, Anpassen von Designs, Erstellen von Formulardesigns
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: 5b55a280c5b445d366c7bf189b54b51e961f6ec2
workflow-type: tm+mt
source-wordcount: '2881'
ht-degree: 95%

---

# Verwenden von Designs zum Formatieren von auf Kernkomponenten basierenden adaptiven Formularen{#themes-for-af-using-core-components}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-or-customize-themes-for-adaptive-forms-core-components.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können Designs erstellen und anwenden, um ein adaptives Formular zu formatieren. Zu einem Design gehören Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider. Ein Design wird ohne Verweis auf ein adaptives Formular unabhängig verwaltet und kann über mehrere adaptive Formulare hinweg wiederverwendet werden.

In diesem Artikel wird erläutert, wie Sie mit Designs benutzerdefinierte Erscheinungsbilder für auf Kernkomponenten basierende adaptive Formulare erstellen können.

## Verfügbare Designs zum Formatieren für Kernkomponenten

Forms as Cloud Service bietet die folgenden aufgelisteten Designs für auf Kernkomponenten basierende adaptive Formulare:

* [Design „Canvas“](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [Design „EASEL“](https://github.com/adobe/aem-forms-theme-easel)

## Grundlegendes zur Struktur der Designs

Ein Design ist ein Paket, das Formatierungs-Komponenten wie die CSS-Datei, JavaScript-Dateien und Ressourcen (wie etwa Symbole) umfasst, die den Stil Ihrer adaptiven Formulare definieren. Ein Design für ein adaptives Formular folgt einer bestimmten Organisation, die aus den folgenden Komponenten besteht:

* `src/theme.scss`: Dieser Ordner enthält die CSS-Datei, die einen großen Einfluss auf das gesamte Design hat. Sie dient als zentralisierter Speicherort zur Definition und Verwaltung des Stils und Verhaltens Ihres Designs. Durch Bearbeitung dieser Datei können Sie Änderungen vornehmen, die im gesamten Design allgemein angewendet werden und das Erscheinungsbild und die Funktionalität Ihrer adaptiven Formular- und AEM Sites-Seiten beeinflussen.

* `src/site`: Dieser Ordner enthält CSS-Dateien, die auf die gesamte Seite einer AEM-Site angewendet werden. Diese Dateien bestehen aus Code und Stilen, die die Gesamtfunktionalität und das Layout der Seite Ihrer AEM-Site beeinflussen. Alle hier vorgenommenen Änderungen werden auf sämtlichen Seiten Ihrer Site übernommen. [Wann ist es einzusetzen?]

* `src/components`: Die CSS-Dateien in diesem Ordner wurden für einzelne AEM-Kernkomponenten entwickelt. Jeder spezielle Ordner für eine Komponente enthält eine `.scss`-Datei, die die jeweilige Komponente in einem adaptiven Formular formatiert. Die Datei /src/components/accordion/_accordion.scss enthält zum Beispiel Stilinformationen für die Akkordeon-Komponente für adaptive Formulare.

  ![Design-Struktur auf Basis eines adaptiven Formulars](/help/forms/assets/theme_structure.png)

* `src/resources`: Dieser Ordner enthält statische Dateien wie Symbole, Logos und Schriftarten. Diese Ressourcen werden verwendet, um die visuellen Elemente und das gesamte Erscheinungsbild Ihres Designs zu verbessern.

## Erstellen von Designs

Forms as a Cloud Service bietet die folgenden Designs zum Formatieren adaptiver Formulare für auf Kernkomponenten basierende adaptive Formulare:

* [Design „Canvas“](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [Design „EASEL“](https://github.com/adobe/aem-forms-theme-easel)

Sie können [jedes dieser Designs anpassen, um ein neues Design zu erstellen](#customize-a-theme-core-components).

![Workflow für die Design-Anpassung](/help/forms/assets/workflow-of-customization-of-theme.png)

## Anpassen eines Designs {#customize-a-theme-core-components}

Das Anpassen eines Designs bezieht sich auf den Prozess des Änderns, Formatierens und Personalisierens des Erscheinungsbilds eines Designs. Wenn Sie ein Design anpassen, ändern Sie dessen Design-Elemente, Layout, Farben, Typografie und manchmal den zugrunde liegenden Code. Auf diese Weise können Sie ein einzigartiges und maßgeschneidertes Erscheinungsbild für Ihre Website oder Anwendung erstellen und dabei die grundlegende Struktur und Funktionalität des Designs beibehalten.

### Voraussetzungen {#prerequisites-to-customize}

* Wenn Sie sich mit dem [Einrichten einer Pipeline in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline) vertraut machen und über grundlegende Kenntnisse zum Einrichten einer Pipeline verfügen, können Sie Ihre Design-Anpassungen effizient verwalten und bereitstellen.
* Erfahren Sie, wie [Benutzende mit der Rolle „Mitwirkende“ konfiguriert werden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html?lang=de). Wenn Sie wissen, wie Sie Benutzende mit der Rolle „Mitwirkende“ konfigurieren, können Sie die erforderlichen Berechtigungen für die Design-Anpassung erteilen.
* Installieren Sie die neueste Version von [Apache Maven](https://maven.apache.org/download.cgi). Apache Maven ist ein Tool zur Automatisierung von Builds, das häufig für Java™-Projekte verwendet wird. Durch die Installation der neuesten Version stellen Sie sicher, dass Sie über die erforderlichen Abhängigkeiten für die Design-Anpassung verfügen.
* Installieren Sie einen Nur-Text-Editor. Beispielsweise Microsoft® Visual Studio Code. Die Verwendung eines Texteditors wie Microsoft® Visual Studio Code bietet eine benutzerfreundliche Umgebung zum Bearbeiten und Ändern von Design-Dateien.

### Einrichten Ihrer Arbeitsumgebung

* Konfigurieren Sie eine [Frontend-Bereitstellungs-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html?lang=de) für Ihre Cloud Service-Umgebung. Alternativ können Sie die Pipeline auch später konfigurieren, sodass Sie das Design vor der Einrichtung der Bereitstellungs-Pipeline flexibel priorisieren und verfeinern können.

<!-- 
To deploy your themes to a Forms as a Cloud Service environment, first test theme on a local development environment to address any issues. Once the theme is tested, configure the front-end deployment pipeline, which is responsible for deploying the themes.

These themes are deployed to a Forms as a Cloud Service environment via the front-end pipeline. You can configure the pipeline later also, after testing the theme on a local development environment. 

-->

Nachdem Sie die Voraussetzungen kennengelernt und die Entwicklungsumgebung konfiguriert haben, sind Sie nun gut darauf vorbereitet, Ihr Design an Ihre spezifischen Anforderungen anzupassen bzw. es entsprechend zu formatieren.

### Anpassen eines Designs {#steps-to-customize-a-theme-core-components}

Das Anpassen eines Designs ist ein mehrstufiger Prozess. Um das Design anzupassen, führen Sie die Schritte in der angegebenen Reihenfolge aus:

1. [Klonen eines Designs](#download-a-theme-core-components)
1. [Festlegen des Namens eines Designs](#set-name-of-theme)
1. [Anpassen eines Designs](#customize-the-theme)
1. [Testen eines Designs](#test-the-theme)
1. [Bereitstellen eines Designs](#deploy-the-theme)

Die im Dokument bereitgestellten Beispiele basieren auf dem Design **Canvas**. Sie müssen aber beachten, dass Sie jedes Design klonen und es mit denselben Anweisungen anpassen können. Diese Anweisungen gelten für jedes Design, sodass Sie Designs entsprechend Ihren spezifischen Anforderungen ändern können.

Beginnen wir mit einem Prozess, um mithilfe von Designs ein Branding-Erlebnis für Ihre auf Kernkomponenten basierenden adaptiven Formulare zu erstellen.

#### &#x200B;1. Klonen eines Designs {#download-a-theme-core-components}

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

   Nach Ausführung des Befehls verfügen Sie über eine lokale Kopie des Designs auf Ihrem Computer im Ordner `aem-forms-theme-canvas`.


#### &#x200B;2. Festlegen des Namens eines Designs {#set-name-of-theme}

1. Öffnen Sie das Design-Projekt in Ihrer IDE. Um beispielsweise den Ordner `aem-forms-theme-canvas` im Visual Studio Code-Editor zu öffnen.

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
   > * Das Attribut „name“ wird verwendet, um das Design eindeutig zu identifizieren, und der angegebene Name wird auf der Registerkarte **Stil** des **Assistenten für die Formularerstellung** angezeigt.
   > * Sie können abhängig von Ihrer Wahl einen Namen für Ihr Design festlegen, beispielsweise `mytheme` oder `customtheme`. In diesem Fall haben wir jedoch `aem-forms-wknd-theme` als Namen angegeben.

1. Öffnen Sie die Datei `package-lock.json`, um sie zu bearbeiten.
1. Legen Sie die Werte für die Attribute `name` und `version` fest. Stellen Sie sicher, dass die Werte für die Attribute `name` und `version` in der Datei `Package-lock`.json mit denen in der Datei `Package.json` übereinstimmen.

   ![Abbildung der Namensänderung des Canvas-Designs](/help/forms/assets/changename_canvastheme-package-lock.png)

1. (Optional) Öffnen Sie die `ReadMe`-Datei zum Bearbeiten und aktualisieren Sie den Namen des Designs.

   ![Abbildung der Namensänderung des Canvas-Designs](/help/forms/assets/changename_canvastheme-readme-file.png)

1. Speichern und schließen Sie die Dateien.

**Überlegungen beim Festlegen des Design-Namens**

* Sie müssen `@aemforms` aus dem Design-Namen in den Dateien `Package.json` und `Package-lock.json` entfernen. Wird `@aemforms` nicht aus dem benutzerdefinierten Design-Namen entfernt, führt dies während der Design-Bereitstellung zu einem Front-End-Pipeline-Fehler.
* Es wird empfohlen, das Design `version` in den Dateien `Package.json` und `Package-lock.json` zu aktualisieren, damit für Ihr Design die im Laufe der Zeit durchgeführten Änderungen und Verbesserungen genau widergespiegelt werden.
* Hinsichtlich wichtiger Informationen zur Verwendung, Installationsanweisungen und anderer relevanter Details wird empfohlen, den Namen des Designs in der `ReadMe`-Datei zu aktualisieren.

#### &#x200B;3. Anpassen eines Designs {#customize-the-theme}

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

Sie können auch Schriftart, Farbe, Größe und andere CSS-Eigenschaften einer bestimmten Kernkomponente eines adaptiven Formulars ändern. Beispiele: Schaltfläche, Kontrollkästchen, Container, Fußzeile usw. Sie können eine Schaltfläche oder ein Kontrollkästchen formatieren, indem Sie die CSS-Datei der jeweiligen Komponente bearbeiten und sie an den Stil Ihrer Organisation anpassen. So passen Sie einen Stil einer Komponente an:

1. Öffnen Sie die Datei `<your-theme-sources>/src/components/<component>/<component.scss>` zur Bearbeitung. Um zum Beispiel die Schriftfarbe der Schaltflächen-Komponente zu ändern, öffnen Sie die Datei `<your-theme-sources>/src/components/button/button.scss`.
1. Ändern Sie die Werte entsprechend Ihren Anforderungen. Ändern Sie beispielsweise die Farbe der Schaltflächenkomponente beim Bewegen des Mauszeigers in `green`, ändern Sie den Wert der Eigenschaft `color: $white` in der Klasse `cmp-adaptiveform-button__widget:hover` in den Hex-Code `#12B453` oder eine andere Schattierung von `green`. Der endgültige Code sieht wie folgt aus:

   ```
   .cmp-adaptiveform-button__widget:hover {
   background: $dark-gray;
   color: #12B453;
   }
   ```

1. Speichern und schließen Sie die Datei.

   ![Bearbeiten der CSS-Textbox](/help/forms/assets/edit_color_textbox.png)

   >[!NOTE]
   >
   > Wenn ein Stil sowohl auf Design- als auch auf Komponentenebene definiert ist, hat der auf Komponentenebene definierte Stil Priorität.

#### &#x200B;4. Testen eines benutzerdefinierten Designs {#test-the-theme}

Um die Änderungen in der lokalen Umgebung in der Vorschau anzuzeigen und zu testen und das Design entsprechend den Anforderungen für verschiedene AEM-Komponenten anzupassen, führen Sie die folgenden Schritte aus:

* 4.1 [Konfigurieren der lokalen Umgebung für Tests](#rename-env-file-theme-folder)
* 4.2 [Testen des Designs anhand einer lokalen Umgebung](#start-a-local-proxy-server)

##### 4.1. Konfigurieren der lokalen Umgebung für Tests {#rename-env-file-theme-folder}

1. Öffnen Sie das Design-Projekt in Ihrer IDE. Öffnen Sie beispielsweise den Ordner `aem-forms-theme-canvas` im Visual Studio Code-Editor.
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

##### 4.2 Testen des Designs anhand einer lokalen Umgebung {#start-a-local-proxy-server}

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

Entsprechend den Beispielen, die sowohl auf Design- als auch auf Kernkomponentenebene für Design-Anpassungen bereitgestellt wurden, werden die Fehlermeldungen eines adaptiven Formulars in die Farbe `blue` geändert, während die Beschriftungsfarbe für die Schaltflächen-Komponente sich in `green` ändert, wenn Sie den Mauszeiger darüber bewegen.

**Vorschau des Stils auf Design-Ebene**

![Beispiel: Fehlerfarbe auf Blau gesetzt](/help/forms/assets/theme-level-changes.png)

**Vorschau des Stils auf Komponentenebene**

![Beispiel: Hover-Farbe auf Grün gesetzt](/help/forms/assets/button-customization.png)

Das Anpassen eines Designs hilft beim Entwerfen des benutzerdefinierten Erscheinungsbilds für das auf Kernkomponenten basierende adaptive Formular gemäß den Anforderungen Ihrer Organisation.

###### Testen des Designs für Formulare, die in einer Cloud Service-Umgebung gehostet werden

Sie können das Design auch für das adaptive Formular testen, das auf Ihrer AEM Forms as a Cloud Service-Instanz gehostet wird. Führen Sie die folgenden Schritte aus, um die lokale Umgebung für das Testen der Designs mit dem auf der Cloud-Instanz gehosteten adaptiven Formular zu konfigurieren und festzulegen:

1. Öffnen Sie das Design-Projekt in Ihrer IDE. Öffnen Sie beispielsweise den Ordner `aem-forms-theme-canvas` im Visual Studio Code-Editor.
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

#### &#x200B;5. Bereitstellen eines Designs {#deploy-the-theme}

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
   >* Sie können ein einziges Repository für mehrere Designs verwenden.
   >* Um verschiedene Designs bereitzustellen, müssen Sie separate Frontend-Pipelines erstellen.
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

   Beispiel:

   ```
   git remote add canvascloudthemerepo https://git.cloudmanager.adobe.com/stage-aemformsdev/customcanvastheme/
   git add .
   git commit
   git push canvascloudthemerepo 
   ```

   ![Vorgenommene Änderungen](/help/forms/assets/cmd_git_push.png)



##### 5.3. Ausführen der Frontend-Pipeline {#run-a-frontend-pipeline}

Das Design wird mithilfe der [Frontend-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html?lang=de) bereitgestellt. Um das Design bereitzustellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrem AEM Cloud Manager-Repository an.
1. Klicken Sie im Abschnitt **[!UICONTROL Pipelines]** auf die Schaltfläche **[!UICONTROL Hinzufügen]**.
1. Wählen Sie je nach Cloud Service-Umgebung **[!UICONTROL Produktionsfremde Pipeline hinzufügen]** oder **[!UICONTROL Produktions-Pipeline hinzufügen]** aus. Hier ist beispielsweise **[!UICONTROL Produktions-Pipeline hinzufügen]** ausgewählt.
1. Geben Sie im Dialogfeld **[!UICONTROL Produktions-Pipeline hinzufügen]** als Teil der **[!UICONTROL Konfigurationsschritte]** den Namen für Ihre Pipeline an. Beispielsweise lautet der Name der Pipeline `customcanvastheme`.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie die Optionen **[!UICONTROL Zielgerichtete Bereitstellung]** > **[!UICONTROL Frontend-Code]** in den Schritten 
unter **[!UICONTROL Quell-Code]** aus.
1. Wählen Sie die Werte für das **[!UICONTROL Repository]** und die **[!UICONTROL Git-Verzweigung]** aus, die Ihre neuesten Änderungen aufweisen. Hier lautet beispielsweise der ausgewählte Repository-Name `custom-canvas-theme-repo` und die Git-Verzweigung `main`.
1. Wählen Sie als **[!UICONTROL Code-Speicherort]** „`/`“ aus, wenn sich Ihre Änderungen im Stammordner befinden.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Frontend-Pipeline erstellen](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   Wenn die Einrichtung der Pipeline abgeschlossen ist, wird die Karte mit dem Aktionsaufruf aktualisiert.

   >[!NOTE]
   >
   > Um sicherzustellen, dass Ihre Frontend-Pipeline in Cloud Manager nicht fehlschlägt, setzen [&#x200B; die Node.js-Version auf 20](#set-the-nodejs-vesrion-to-20).

1. Klicken Sie mit der rechten Maustaste auf die erstellte Pipeline.
1. Klicken Sie auf **[!UICONTROL Ausführen]** .

   ![run-a-pipeline](/help/forms/assets/canvas-theme-run-pipeline.png)

Sobald die Erstellung abgeschlossen ist, steht das Design in der Autoreninstanz zur Verwendung zur Verfügung. Es wird unter der Registerkarte **[!UICONTROL Stil]** im Assistenten zur Erstellung adaptiver Formulare beim Erstellen eines adaptiven Formulars angezeigt.

![Benutzerdefiniertes Design auf der Registerkarte „Stil“](/help/forms/assets/custom-theme-style-tab.png)

Das angepasste Design hilft beim Erstellen eines Markenerlebnisses für auf Kernkomponenten basierende adaptive Formulare.

## Anwenden eines Designs auf ein adaptives Formular {#using-theme-in-adaptive-form}

Schritte zum Anwenden eines Designs auf ein adaptives Formular:

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an.

1. Wählen Sie **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.

1. Klicken Sie auf **Erstellen** > **Adaptive Formulare**. Der Assistent zum Erstellen des adaptiven Formulars wird geöffnet.

1. Wählen Sie die Kernkomponentenvorlage auf der Registerkarte **Quelle**.
1. Wählen Sie das Design auf der Registerkarte **Stil** aus.
1. Klicken Sie auf **Erstellen**.

Designs für adaptive Formulare werden als Teil einer Vorlage für adaptive Formulare verwendet, um beim Erstellen eines adaptiven Formulars Stile zu definieren.

## Legen Sie die Node.js-Version auf 20 fest.

So legen Sie die Node.js-Version mithilfe der Pipeline-Konfiguration auf 20 fest:

1. Gehen Sie zum **Pipelines** und suchen Sie Ihre Frontend-Pipeline.
2. Klicken Sie rechts in der Pipeline auf das Dreipunkt-Menü **⋯** und wählen Sie aus der Dropdown-Liste **Variablen anzeigen/bearbeiten**.
3. Füllen Sie **Dialogfeld** Variablenkonfiguration“ die Felder wie folgt aus:
   * **NAME** - NODE_VERSION
   * **WERT** - 20
   * **SCHRITT ANGEWENDET** - Build
   * **TYPE** - Variable
4. Klicken Sie auf **Speichern**, um die Konfiguration anzuwenden.

![Pipeline-Konfiguration](/help/forms/assets/pipeline-config.png)

## Best Practices {#best-practices}

* **Vermeiden von Assets aus einem anderen Design**

  Bei der Bearbeitung von Designs können Sie Assets (etwa Bilder) aus anderen Designs durchsuchen und hinzufügen. Angenommen, Sie bearbeiten den Hintergrund einer Seite. Wenn Sie beispielsweise **[!UICONTROL Seite]** ![Bearbeiten-Schaltfläche](assets/edit-button.png) > **[!UICONTROL Hintergrund]** > **[!UICONTROL Hinzufügen]** > **[!UICONTROL Bild]** auswählen, wird ein Dialogfeld angezeigt, in dem Sie Bilder aus anderen Designs suchen und hinzufügen können.

  Es können Probleme im aktuellen Design auftreten, wenn ein Asset aus einem anderen Design hinzugefügt und dieses andere Design später verschoben oder gelöscht wird. Wir empfehlen daher, keine Assets aus anderen Designs zu suchen und hinzuzufügen.

* **Ändern der Layout-Breite des Container-Bereichs**

  Es wird nicht empfohlen, die Layout-Breite des Container-Bereichs zu ändern. Wenn Sie die Breite eines Container-Bereichs angeben, wird er statisch und passt sich nicht mehr an unterschiedliche Displays an.

## Häufig gestellte Fragen {#faq}

**Frage:** Welche Anpassung hat Vorrang, wenn Anpassungen in einem Design-Ordner sowohl auf der globalen Ebene als auch auf der Komponentenebene vorgenommen werden?

**Antwort:** Wenn Anpassungen sowohl auf globaler als auch auf Komponentenebene vorgenommen werden, hat die Anpassung auf Komponentenebene Priorität.



## Siehe auch {#see-also}

{{see-also}}

* [Festlegen des Layouts von Formularen für verschiedene Bildschirmgrößen und Gerätetypen](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Generieren eines Datensatzdokuments für adaptive Formulare (Kernkomponenten)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Erstellen eines adaptiven Formulars mit wiederholbaren Abschnitten](/help/forms/create-forms-repeatable-sections.md)
* [Beispielthemenvorlagen und Formulardatenmodelle](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=de)
