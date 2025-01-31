---
title: Erste Schritte mit Edge Delivery Services für AEM Forms im universellen Editor - Entwickler-Tutorial
description: In diesem Tutorial lernen Sie alles über ein neues Adobe Experience Manager (AEM) Forms-Projekt. In zehn bis zwanzig Minuten haben Sie Ihre eigenen Edge Delivery Services Forms im universellen Editor erstellt.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: c27b8e413c060de601a72a669d86c4add2a4167d
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 22%

---


# Erste Schritte mit Edge Delivery Services für AEM Forms mit dem universellen Editor (WYSIWYG)

Im heutigen digitalen Zeitalter sind benutzerfreundliche Formulare für alle Organisationen unverzichtbar. Edge Delivery Services-Forms werden mit dem universellen Editor erstellt, der WYSIWYG-Funktionen (What-you-see-is-what-you-get) bietet. Es bietet eine moderne, intuitive Benutzeroberfläche für effizientes Formular-Authoring.

AEM Forms bietet einen -Block, den so genannten adaptiven Forms-Block, mit dem Sie Forms-Edge Delivery Services zur Datenerfassung und -speicherung einfach erstellen können. Sie können [ein neues AEM-Projekt erstellen, das mit dem adaptiven Forms-Block vorkonfiguriert ist](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) oder [den adaptiven Forms-Block zu einem vorhandenen AEM-Projekt hinzufügen](#add-adaptive-forms-block-to-your-existing-aem-project).

Dieses Tutorial führt Sie durch die Erstellung, Vorschau und Veröffentlichung Ihres eigenen Formulars mit einem neuen oder vorhandenen Adobe Experience Manager Site-Projekt mithilfe der WYSIWYG-Bearbeitung im universellen Editor.


## Voraussetzungen

* Sie verfügen über ein GitHub-Konto und sind mit den Git-Grundlagen vertraut.
* Sie verfügen über ein Google- oder Microsoft SharePoint-Konto.
* Sie sind mit den Grundlagen von HTML, CSS und JavaScript vertraut.
* Sie haben Node/npm für die lokale Entwicklung installiert.

## Erstellen eines neuen, mit adaptivem Formularblock vorkonfigurierten AEM-Projekt

Die AEM Forms-Bausteinvorlage ermöglicht einen schnellen Einstieg in ein AEM-Projekt, das mit dem adaptiven Formularblock vorkonfiguriert ist. Dies ist der schnellste und einfachste Weg, AEM-Best Practices zu befolgen und direkt zum Erstellen Ihrer Formulare zu gelangen.

### Erste Schritte mit der AEM Forms-Baustein-Repository-Vorlage

1. Erstellen Sie ein GitHub-Repository für Ihr AEM-Projekt. So erstellen Sie ein Repository:
   1. Navigieren Sie zu [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![AEM Forms-Bausteinvorlage](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. Klicken Sie auf **Option „Diese Vorlage verwenden** und wählen Sie die Option **Neues Repository erstellen** aus.

      ![Erstellen eines neuen Repositorys mithilfe der AEM Forms-Bausteinvorlage](/help/edge/docs/forms/assets/use-eds-form-template.png)

      Der **„Neues Repository erstellen** wird geöffnet.

   1. Wählen **auf dem Bildschirm** Neues Repository erstellen“ den **Eigentümer** aus und geben Sie **Repository-Namen** an. Adobe empfiehlt, das Repository auf &quot;**&quot;**. Wählen Sie daher die Option **Public** (öffentlich) aus und klicken Sie auf **Create Repository** (Repository erstellen).

      ![Festlegen des Repositorys als öffentlich](/help/edge/docs/forms/assets/name-eds-repo.png)

1. Installieren Sie die AEM Code Sync GitHub App in Ihrem Repository. So installieren Sie sie:
   1. Navigieren Sie zu [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Wählen Sie auf dem Bildschirm **AEM-Code-** installieren) die Option **Nur Repositorys auswählen** und wählen Sie Ihr neu erstelltes Repository aus. Klicken Sie auf **Speichern**.

   ![Festlegen des Repositorys als öffentlich](/help/edge/docs/forms/assets/aem-code-sync-up.png)

1. Verknüpfen Sie jetzt das mit AEM Forms Boilerplate erstellte GitHub-Repository mit Ihrer Authoring-Umgebung für AEM-Projekte. So richten Sie die Verbindung ein:

   1. Wechseln Sie zum GitHub-Repository, das Sie zuvor mit dem AEM Forms-Textbaustein erstellt haben.
   1. Öffnen Sie die Datei **fstab.yaml** zur Bearbeitung.

      ![Öffnen Sie die Datei fstab.yaml](/help/edge/docs/forms/assets/open-fstab.png)

   1. Bearbeiten Sie die **fstab.yaml**, um den Einhängepunkt Ihres Projekts zu aktualisieren. Ersetzen Sie die URL durch die URL Ihrer AEM as a Cloud Service-Autoreninstanz.
      `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`

      ![Datei „fstab.yaml“ ](/help/edge/docs/forms/assets/edit-fstab-file.png)

   1. Bestätigen Sie die aktualisierte **fstab.yaml**-Datei, sobald Sie die Referenz aktualisiert haben und alles gut aussieht.

      ![Übergeben Sie die Änderungen](/help/edge/docs/forms/assets/commit-fstab-changes.png)

      Wenn Build-Probleme auftreten, lesen Sie [Beheben von Build-Problemen in GitHub](#troubleshooting-github-build-issues).

### Erstellen eines neuen AEM-Projekts

Nachdem Sie nun über ein GitHub-Projekt verfügen, können Sie mit dem Erstellen und Veröffentlichen eines neuen AEM-Projekts in der AEM as a Cloud Service-Autoreninstanz fortfahren.
1. Erstellen eines neuen AEM-Projekts:

   1. Melden Sie sich bei der AEM as a Cloud Service-Autoreninstanz an und wählen Sie **Sites** aus.

      ![Websites auswählen](/help/edge/assets/select-sites.png)

   1. Klicken Sie **Erstellen** > **Site aus Vorlage**.

      ![create-sites](/help/edge/docs/forms/assets/create-sites.png)

   1. Wählen Sie die Edge Delivery Services-Site-Vorlage aus und klicken Sie auf **Weiter**.

      ![select-site-template](/help/edge/docs/forms/assets/select-site-template.png)

      >[!NOTE]
      >
      > * Wenn die Edge Delivery Services-Site-Vorlage in Ihrer Autoreninstanz nicht verfügbar ist, klicken Sie auf die Schaltfläche Importieren , um die Vorlage hochzuladen.
      > * Sie können die Edge Delivery Services-Site-Vorlagen von [GitHub](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases) herunterladen.

   1. Geben Sie die folgenden Details ein, um ein neues AEM-Projekt zu erstellen:
      * **Site-Titel**: Fügen Sie einen beschreibenden Titel für die Site hinzu.
      * **Site-Titel** - Verwenden Sie die `site-name`, die Sie im vorherigen Schritt definiert haben.
      * **GitHub-URL**: Verwenden Sie die URL des GitHub-Projekts, das Sie im vorherigen Schritt erstellt haben.

      ![AEM-Site erstellen](/help/edge/docs/forms/assets/create-aem-site.png)

   1. Das **Site erstellen** wird angezeigt, klicken Sie auf **OK**.

      ![Klicken Sie auf OK](/help/edge/docs/forms/assets/click-ok-aem-site.png)

      In nur wenigen Minuten wird Ihr neues AEM-Projekt erstellt.

   1. Navigieren Sie zu Ihrem neu erstellten AEM-Projekt in der Sites-Konsole und klicken Sie auf **Bearbeiten**.
In diesem Fall wird die `index.html` Seite zur Illustration verwendet.

      ![AEM-Site bearbeiten](/help/edge/docs/forms/assets/edit-site.png)

      Das AEM-Projekt wird im universellen Editor auf einer neuen Registerkarte geöffnet und ermöglicht das Erstellen in WYSIWYG. Sie können jetzt Ihr AEM-Projekt bearbeiten.

      ![Site wird im universellen Editor geöffnet](/help/edge/docs/forms/assets/site-in-universal-editor.png)

1. Publish hat Ihr AEM-Projekt erstellt

   Nachdem Sie die Bearbeitung des AEM-Projekts abgeschlossen haben, veröffentlichen Sie es. Zur Veröffentlichung:

   1. Wählen Sie in der Sites-Konsole alle AEM-Projektseiten aus und klicken Sie auf **Quick Publish**.

      ![AEM Sites-Projekt veröffentlichen](/help/edge/docs/forms/assets/publish-sites.png)

   1. Das **Quick Publish** Bestätigungsdialogfeld wird angezeigt. Klicken Sie auf **Publish**, um den Veröffentlichungsprozess zu starten.

      ![Publish-Schnellbestätigungsdialogfeld](/help/edge/docs/forms/assets/quick-publish.png)

      Alternativ können Sie Ihre AEM-Projektseiten direkt über die Benutzeroberfläche des universellen Editors veröffentlichen.

      ![Publish-Schnellbestätigungsdialogfeld](/help/edge/docs/forms/assets/qui.png)

   Herzlichen Glückwunsch! Sie haben eine neue Website auf `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repositorys.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.
   * `<site-name>` bezieht sich auf den Namen der erstellten Site.

   Wenn der Zweigname beispielsweise `main`, das Repository `edsforms`, der Eigentümer `wkndforms` und der `site-name` `eds-forms` ist, würde die Website unter `https://main--edsforms--wkndforms.aem.page/content/eds-forms/` ausgeführt

   >[!NOTE]
   >
   > * Um die `index.html` des AEM-Projekts anzuzeigen, verwenden Sie die URL `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
   > * Um andere Seiten als die `index page` des AEM-Projekts anzuzeigen, verwenden Sie die URL `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<site-page-name>`

Jetzt können Sie mit dem [Erstellen und Hinzufügen von Formularen zu Ihrem AEM-Projekt](#add-edge-delivery-services-forms-to-aem-project) beginnen.

## Hinzufügen eines adaptiven Forms-Blocks zu einem vorhandenen AEM-Projekt

Wenn Sie über ein vorhandenes AEM-Projekt verfügen, können Sie den adaptiven Formularblock in Ihr aktuelles Projekt integrieren, um mit der Formularerstellung zu beginnen.

>[!NOTE]
>
>
> Dieser Schritt gilt für Projekte, die mit dem [AEM-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-xwalk) erstellt wurden. Wenn Sie Ihr AEM Projekt mit dem [AEM Forms-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-forms) erstellt haben, können Sie diesen Schritt überspringen.

So integrieren Sie ihn:

1. Klonen Sie das GitHub-Repository des adaptiven Forms-Blocks [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms) auf Ihrem Computer.
1. Suchen Sie im heruntergeladenen Ordner den Ordner `blocks/form` und kopieren Sie ihn.
1. Klonen Sie das GitHub-Repository Ihres AEM-Projekts auf Ihrem Computer.
1. Navigieren Sie jetzt zum `blocks` Ordner in Ihrem lokalen AEM-Projekt-Repository und fügen Sie den kopierten Formularordner dort ein.
1. Übergeben Sie diese Änderungen und übertragen Sie sie in das AEM-Projekt-Repository auf GitHub.

Das war&#39;s! Der adaptive Forms-Block ist jetzt Teil Ihres AEM-Projekts. Sie können [Formulare erstellen und zu Ihrem AEM-Projekt hinzufügen](#add-edge-delivery-services-forms-to-aem-site-project).

## Erstellen von AEM Forms mit WYSIWYG

Sie können Ihr AEM-Projekt im universellen Editor für das WYSIWYG-Authoring öffnen, wo Sie das Projekt bearbeiten und den Abschnitt für adaptive Formulare hinzufügen können, um Edge Delivery Services-Formulare in AEM-Projektseiten einzuschließen.

1. Fügen Sie den Abschnitt Adaptives Formular zu Ihrer AEM-Projektseite hinzu. Hinzufügen:
   1. Navigieren Sie zu Ihrem AEM-Projekt in der Sites-Konsole und klicken Sie auf **Bearbeiten**. Die Seite &quot;AEM-Projekt“ wird im universellen Editor zur Bearbeitung geöffnet.
In diesem Fall wird die `index.html` Seite zur Illustration verwendet.
   1. Öffnen Sie die Inhaltsstruktur und navigieren Sie zu der Position, an der Sie den Abschnitt für das adaptive Formular hinzufügen möchten.
   1. Klicken Sie auf **[!UICONTROL Hinzufügen]** und wählen Sie die Komponente **[!UICONTROL Adaptives Formular]** aus der Komponentenliste aus.

   ![Inhaltsstruktur](/help/edge/docs/forms/assets/add-adaptive-form-block.png)

   Der Abschnitt für adaptive Formulare wird an der angegebenen Position hinzugefügt. Sie können jetzt damit beginnen, Formularkomponenten zur AEM-Projektseite hinzuzufügen.

1. Fügen Sie Formularkomponenten zum hinzugefügten Abschnitt für adaptive Formulare hinzu. So fügen Sie Formularkomponenten hinzu:
   1. Navigieren Sie in der Inhaltsstruktur zum hinzugefügten Abschnitt für adaptive Formulare .

      ![Adaptiver Formularblock hinzugefügt](/help/edge/docs/forms/assets/adative-form-block.png)


   1. Klicken Sie auf **[!UICONTROL Hinzufügen]** und fügen Sie die gewünschten Komponenten aus der Liste **Adaptive Formularkomponenten** hinzu.

      ![Komponente hinzufügen](/help/edge/docs/forms/assets/add-component.png)

      Sie können die erforderlichen adaptiven Forms-Komponenten auch per Drag-and-Drop verschieben, da der universelle Editor eine intuitive Drag-and-Drop-Funktion bietet.

   1. Wählen Sie die hinzugefügte Komponente des adaptiven Formulars aus, um ihre Eigenschaften mithilfe von **[!UICONTROL Eigenschaften]** zu aktualisieren.

      ![Eigenschaften öffnen](/help/edge/docs/forms/assets/component-properties.png)

      Im folgenden Screenshot wird das Formular angezeigt, das mit WYSIWYG Authoring im AEM-Projekt verfasst wurde:

      ![Formular hinzugefügt](/help/edge/docs/forms/assets/added-form-aem-sites.png)

   >[!NOTE]
   >
   > Es ist wichtig, die AEM-Projektseite erneut zu veröffentlichen, nachdem Sie Änderungen vorgenommen haben. Andernfalls sind die Aktualisierungen nicht im Browser sichtbar.

1. Veröffentlichen Sie die AEM-Projektseite erneut.

   1. Klicken Sie auf **Publish**, um die AEM-Projektseite nach dem Hinzufügen des Formulars erneut zu veröffentlichen.

      ![Formular veröffentlichen](/help/edge/docs/forms/assets/publish-form.png)

   1. Das Bestätigungsdialogfeld **Publish** wird auf dem Bildschirm angezeigt. Klicken Sie auf **Publish**, um mit der Veröffentlichung zu beginnen.

      ![Formular 1 veröffentlichen](/help/edge/docs/forms/assets/publish-form1.png)

      Nachdem Sie auf die Schaltfläche **Publish** geklickt haben, wird die `Publish started successfully` angezeigt.

      ![Formular veröffentlichen2](/help/edge/docs/forms/assets/publish-form2.png)

   Sie können jetzt die Seite AEM-Projekt mit dem hinzugefügten Formular Edge Delivery Services unter der folgenden URL aufrufen:
   `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   Wenn der Zweigname beispielsweise `main` lautet, das Repository `edsforms` ist, der Eigentümer `wkndforms` und der Site-Name `eds-forms` ist, würde die URL wie folgt lauten:
   `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   ![Indexseite](/help/edge/docs/forms/assets/publish-index-page.png)

Sie können die Edge Delivery Services-Forms gestalten, indem Sie die `.css`- und `.js` im adaptiven Forms-Block bearbeiten und [eine lokale AEM-Entwicklungsumgebung einrichten](#set-up-local-aem-development-environment) um die Änderungen sofort in Ihrem Browser anzuzeigen.

## Einrichten einer lokalen AEM-Entwicklungsumgebung

Sie können eine lokale AEM-Entwicklungsumgebung einrichten, um benutzerdefinierte Stile und Komponenten lokal zu entwickeln. So arbeiten Sie mit einer lokalen AEM-Entwicklungsumgebung:

1. **Installieren der AEM-CLI**: Die AEM-CLI vereinfacht Entwicklungsaufgaben. Installieren Sie sie global mit npm:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. **GitHub-Projekt klonen**: Klonen Sie Ihr AEM-Projekt-Repository aus GitHub mit dem folgenden Befehl, wobei Sie Folgendes ersetzen <owner> durch die Repository-Besitzerin bzw. den Repository-Besitzer und <repo> mit dem Repository-Namen:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. **Lokale Umgebung starten**: Navigieren Sie zu Ihrem Projektverzeichnis und starten Sie Ihre lokale AEM-Instanz mit einem einzigen Befehl:

   ```
   cd <repo>
   aem up
   ```

Sie können lokale Änderungen im Ordner Adaptive Forms Block-`blocks/form` für die Formatierung und Codierung Ihrer Formulare vornehmen! Bearbeiten Sie die `.css` oder `.js` Dateien in diesem Verzeichnis, und Sie können sehen, dass die Änderungen sofort in Ihrem Browser widergespiegelt werden.

Nachdem Sie Ihre Änderungen abgeschlossen haben, verwenden Sie Git-Befehle, um sie zu übernehmen und zu pushen. Dadurch werden Ihre Vorschau- und Produktionsumgebungen aktualisiert, auf die über die folgenden URLs zugegriffen werden kann (Ersetzen Sie Platzhalter durch Ihre Projektdetails):

Vorschau: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
Produktion: `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`


## Beheben von Build-Problemen in GitHub

Stellen Sie einen reibungslosen Build-Prozess in GitHub sicher, indem Sie potenzielle Probleme beheben:

* **Beheben von Linting-Fehlern:**
Sollten Sie auf Linting-Fehler stoßen, können Sie diese umgehen. Öffnen Sie die Datei [EDS Project]/package.json und ändern Sie das Skript „lint“ von `"lint": "npm run lint:js && npm run lint:css"` zu `"lint": "echo 'skipping linting for now'"`. Speichern Sie die Datei und übertragen Sie die Änderungen auf Ihr GitHub-Projekt.

<!-- * **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file. -->
