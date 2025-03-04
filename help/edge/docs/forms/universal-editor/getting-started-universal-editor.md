---
title: Erste Schritte mit Edge Delivery Services für AEM Forms im universellen Editor – Entwickler-Tutorial
description: In diesem Tutorial lernen Sie alles über ein neues Adobe Experience Manager (AEM) Forms-Projekt. In zehn bis zwanzig Minuten haben Sie Ihre eigenen Edge Delivery Services-Formulare im universellen Editor erstellt.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: 964fd32a7dbcb97190d40cb42100d0d66e69a0c4
workflow-type: tm+mt
source-wordcount: '1846'
ht-degree: 96%

---


# Erste Schritte mit Edge Delivery Services für AEM Forms mithilfe des universellen Editors (WYSIWYG)

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> mit dem Namen Ihrer GitHub-Organisation und dem Repository-Namen. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Organisationsname adobe und der Repository-Name abc.</span>


Im heutigen digitalen Zeitalter sind benutzerfreundliche Formulare für jede Organisation schlicht unverzichtbar. Edge Delivery Services-Formulare werden mit dem universellen Editor erstellt, der WYSIWYG(What You See Is What You Get)-Funktionen bietet. Dieser verfügt über eine moderne, intuitive Benutzeroberfläche zur effizienten Formularerstellung.

AEM Forms umfasst einen Block, der als adaptiver Formularblock bezeichnet wird und mit dem Sie mühelos Edge Delivery Services-Formulare erstellen können, um Daten zu erfassen und zu speichern. Sie können [ein neues AEM-Projekt vorkonfiguriert mit einem adaptiven Formularblock erstellen](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) oder [den adaptiven Formularblock einem bestehenden AEM-Projekt hinzufügen](#add-adaptive-forms-block-to-your-existing-aem-project).

![GitHub-Repository-Workflow](/help/edge/assets/repo-workflow.png)

Dieses Tutorial führt Sie durch die Erstellung, Vorschau und Veröffentlichung Ihres eigenen Formulars mit einem neuen oder vorhandenen Adobe Experience Manager Sites-Projekt mithilfe der WYSIWYG-Bearbeitungsfunktion des universellen Editors.


## Voraussetzungen

* Sie verfügen über ein GitHub-Konto und sind mit den Git-Grundlagen vertraut.
* Sie sind mit den Grundlagen von HTML, CSS und JavaScript vertraut.
* Sie haben Node/npm für die lokale Entwicklung installiert.

## Erstellen eines neuen, mit adaptivem Formularblock vorkonfigurierten AEM-Projekt

Die AEM Forms-Bausteinvorlage ermöglicht einen schnellen Einstieg in ein AEM-Projekt, das mit dem adaptiven Formularblock vorkonfiguriert ist. Dies ist die schnellste und einfachste Methode, AEM Best Practices zu befolgen und direkt mit der Formularerstellung zu beginnen.

### Erste Schritte mit der AEM Forms-Baustein-Repository-Vorlage

1. Erstellen Sie ein GitHub-Repository für Ihr AEM-Projekt. So erstellen Sie ein Repository:
   1. Navigieren Sie zu [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![AEM Forms-Bausteinvorlage](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. Klicken Sie auf **Use this template** (Diese Vorlage verwenden) und wählen Sie die Option **Create a new repository** (Neues Repository erstellen) aus. 

      ![Erstellen eines neuen Repositorys mithilfe der AEM Forms-Bausteinvorlage](/help/edge/docs/forms/assets/use-eds-form-template.png)

      Der Bildschirm **Create a new repository** (Neues Repository erstellen) wird geöffnet.

   1. Wählen Sie im Bildschirm **Create a new repository** (Neues Repository erstellen) die **verantwortliche Person** aus und geben Sie den **Repository-Namen** an. Adobe empfiehlt, das Repository als **öffentlich** festzulegen. Wählen Sie daher die Option **Public** (öffentlich) aus und klicken Sie auf **Create Repository** (Repository erstellen).

      ![Festlegen des Repositorys als öffentlich](/help/edge/docs/forms/assets/name-eds-repo.png)

1. Installieren Sie die AEM Code Sync GitHub App in Ihrem Repository. So installieren Sie sie:
   1. Navigieren Sie zu [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Wählen Sie im Bildschirm **Install AEM Code Sync** (AEM Code Sync installieren) die Option **Only select Repositories** (Nur ausgewählte Repositorys) und dann das neu erstellte Repository aus. Klicken Sie auf **Speichern**.

   ![Festlegen des Repositorys als öffentlich](/help/edge/docs/forms/assets/aem-code-sync-up.png)

1. Verknüpfen Sie jetzt das mit der AEM Forms-Bausteinvorlage erstellte GitHub-Repository mit der Authoring-Umgebung Ihres AEM-Projekts. So richten Sie die Verbindung ein:

   1. Wechseln Sie zum GitHub-Repository, das Sie zuvor mit dem AEM Forms-Textbaustein erstellt haben.
   1. Öffnen Sie die Datei **fstab.yaml**, um sie zu bearbeiten.

      ![Öffnen der Datei „fstab.yaml“](/help/edge/docs/forms/assets/open-fstab.png)

   1. Bearbeiten Sie die Datei **fstab.yaml**, um den Bereitstellungspunkt Ihres Projekts zu aktualisieren. Ersetzen Sie die URL durch die URL Ihrer AEM as a Cloud Service-Autoreninstanz.
      `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`

      ![Bearbeiten der Datei „fstab.yaml“ ](/help/edge/docs/forms/assets/edit-fstab-file.png)

   1. Übergeben Sie die aktualisierte Datei **fstab.yaml**, sobald Sie die Referenz aktualisiert haben und alles gut aussieht.

      ![Änderungen übergeben](/help/edge/docs/forms/assets/commit-fstab-changes.png)

      Falls Build-Probleme auftreten, lesen Sie [Beheben von Build-Problemen in GitHub](#troubleshooting-github-build-issues).

### Erstellen eines neuen AEM-Projekts

Nachdem Sie nun über ein GitHub-Projekt verfügen, können Sie mit dem Erstellen und Veröffentlichen eines neuen AEM-Projekts in der AEM as a Cloud Service-Autoreninstanz fortfahren.
1. So erstellen Sie ein neues AEM-Projekt:

   1. Melden Sie sich bei der AEM as a Cloud Service-Autoreninstanz an und wählen Sie **Sites** aus.

      ![Sites auswählen](/help/edge/assets/select-sites.png)

   1. Klicken Sie auf **Erstellen** > **Site aus Vorlage**.

      ![Sites erstellen](/help/edge/docs/forms/assets/create-sites.png)

   1. Wählen Sie die Edge Delivery Services-Site-Vorlage aus und klicken Sie auf **Weiter**.

      ![Site-Vorlage auswählen](/help/edge/docs/forms/assets/select-site-template.png)

      >[!NOTE]
      >
      > * Wenn die Edge Delivery Services-Site-Vorlage in Ihrer Autoreninstanz nicht verfügbar ist, klicken Sie auf die Schaltfläche „Importieren“, um die Vorlage hochzuladen.
      > * Sie können die Edge Delivery Services-Site-Vorlagen von [GitHub](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases) herunterladen.

   1. Geben Sie die folgenden Details ein, um ein neues AEM-Projekt zu erstellen:
      * **Site-Titel**: Fügen Sie einen beschreibenden Titel für die Site hinzu.
      * **Site-Name**: Verwenden Sie den `site-name`, den Sie im vorherigen Schritt definiert haben.
      * **GitHub-URL**: Verwenden Sie die URL des GitHub-Projekts, das Sie im vorherigen Schritt erstellt haben.

      ![AEM-Site erstellen](/help/edge/docs/forms/assets/create-aem-site.png)

   1. Das Dialogfeld **Site erstellen** wird angezeigt. Klicken Sie auf **OK**.

      ![Auf OK klicken](/help/edge/docs/forms/assets/click-ok-aem-site.png)

      Ihr neues AEM-Projekt wird in nur wenigen Minuten erstellt.

   1. Navigieren Sie zu Ihrem neu erstellten AEM-Projekt in der Sites-Konsole und klicken Sie auf **Bearbeiten**.
In diesem Fall wird die Seite `index.html` zur Veranschaulichung verwendet.

      ![AEM-Site bearbeiten](/help/edge/docs/forms/assets/edit-site.png)

      Das AEM-Projekt wird im universellen Editor auf einer neuen Registerkarte geöffnet, wo ein WYSIWYG-Authoring möglich ist. Sie können Ihr AEM-Projekt nun bearbeiten.

      ![Site wird im universellen Editor geöffnet](/help/edge/docs/forms/assets/site-in-universal-editor.png)

1. Veröffentlichen Ihres erstellten AEM-Projekts

   Nachdem Sie die Bearbeitung des AEM-Projekts abgeschlossen haben, veröffentlichen Sie es. So gehen Sie zum Veröffentlichen vor:

   1. Wählen Sie in der Sites-Konsole alle AEM-Projektseiten aus und klicken Sie auf **Quick Publish**.

      ![AEM Sites-Projekt veröffentlichen](/help/edge/docs/forms/assets/publish-sites.png)

   1. Das Bestätigungsdialogfeld **Quick Publish** wird angezeigt. Klicken Sie auf **Veröffentlichen**, um den Veröffentlichungsprozess zu starten.

      ![Quick Publish-Bestätigungsdialogfeld](/help/edge/docs/forms/assets/quick-publish.png)

      Alternativ können Sie Ihre AEM-Projektseiten direkt über die Benutzeroberfläche des universellen Editors veröffentlichen.

      ![Quick Publish-Bestätigungsdialogfeld](/help/edge/docs/forms/assets/qui.png)

   Herzlichen Glückwunsch! Sie haben eine neue Website auf `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repositorys.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.
   * `<site-name>` bezieht sich auf den Namen der erstellten Site.

   Wenn beispielsweise der Name der Verzweigung `main`, das Repository `edsforms`, die verantwortliche Person `wkndforms` und der `site-name` `eds-forms` lauten, läuft die Website unter `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   >[!NOTE]
   >
   > * Um die Seite `index.html` des AEM-Projekts anzuzeigen, verwenden Sie die URL `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
   > * Um andere Seiten als die `index page` des AEM-Projekts anzuzeigen, verwenden Sie die URL `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<site-page-name>`

Sie können nun mit der [Erstellung und dem Hinzufügen von Formularen zu Ihrem AEM-Projekt](#add-edge-delivery-services-forms-to-aem-project) beginnen.

## Hinzufügen eines adaptiven Formularblocks zu Ihrem bestehenden AEM-Projekt

Wenn Sie über ein vorhandenes AEM-Projekt verfügen, können Sie den adaptiven Formularblock in Ihr aktuelles Projekt integrieren, um mit der Formularerstellung zu beginnen.

>[!NOTE]
>
>
> Dieser Schritt gilt für Projekte, die mit dem [AEM-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-xwalk) erstellt wurden. Wenn Sie Ihr AEM Projekt mit dem [AEM Forms-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-forms) erstellt haben, können Sie diesen Schritt überspringen.

So integrieren Sie ihn:
1. **Hinzufügen von erforderlichen Dateien und Ordnern**
   1. Kopieren Sie die folgenden Ordner und Dateien aus dem [AEM Forms-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-forms) und fügen Sie sie in Ihr AEM-Projekt ein:

      * Ordner [form block](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form)
      * Ordner [form-common](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-common)
      * Ordner [form-components](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-components)
      * Datei [form-editor-support.js](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js)
      * Datei [form-editor-support.css](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css)

1. **Aktualisieren von Komponentendefinitionen und Modelldateien**
   1. Navigieren Sie zur Datei `../models/_component-definition.json` in Ihrem AEM-Projekt und aktualisieren Sie sie mit den Änderungen in der Datei [_component-definition.json im AEM Forms-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-definition.json#L39-L48).

   1. Navigieren Sie zur Datei `../models/_component-models.json` in Ihrem AEM-Projekt und aktualisieren Sie sie mit den Änderungen in der Datei [_component-models.json im AEM Forms-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-models.json#L24-L26)

1. **Hinzufügen des Formulareditors im Skripteditor**
   1. Navigieren Sie zur Datei `../scripts/editor-support.js` in Ihrem AEM-Projekt und aktualisieren Sie sie mit den Änderungen in der Datei [editor-support.js im AEM Forms-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js#L105-L106)
1. **Aktualisieren der ESLint-Konfigurationsdatei**
   1. Navigieren Sie zur Datei `../.eslintignore` in Ihrem AEM-Projekt und fügen Sie die folgende Code-Zeile hinzu, um Fehler im Zusammenhang mit der Formularblock-Regel-Engine zu vermeiden:

      ```
          blocks/form/rules/formula/*
          blocks/form/rules/model/*
      ```

1. Bestätigen Sie diese Änderungen und übertragen Sie sie in Ihr AEM-Projekt-Repository auf GitHub.

Das war&#39;s! Der adaptive Formularblock ist jetzt Teil Ihres AEM-Projekts. Sie können [mit dem Erstellen und Hinzufügen von Formularen zu Ihren AEM-Seiten beginnen](#add-edge-delivery-services-forms-to-aem-site-project).

## Erstellen von AEM-Formularen mit WYSIWYG

Sie können Ihr AEM-Projekt zwecks WYSIWYG-Authoring im universellen Editor öffnen. Darin können Sie das Projekt bearbeiten und den Abschnitt „Adaptives Formular“ hinzufügen, um Edge Delivery Services-Formulare in AEM-Projektseiten einzuschließen.

1. Fügen Sie den Abschnitt „Adaptives Formular“ zu Ihrer AEM-Projektseite hinzu. Gehen Sie dazu wie folgt vor:
   1. Navigieren Sie in der Sites-Konsole zu Ihrem AEM-Projekt, wählen Sie die zu bearbeitende Site-Seite aus und klicken Sie auf **Bearbeiten**. Die AEM-Projektseite wird im universellen Editor zur Bearbeitung geöffnet.
In diesem Fall wird die Seite `index.html` zur Veranschaulichung verwendet.
   1. Öffnen Sie die Inhaltsstruktur und navigieren Sie zu dem Abschnitt, in dem Sie den Abschnitt „Adaptives Formular“ hinzufügen möchten.
   1. Klicken Sie auf **[!UICONTROL Hinzufügen]** und wählen Sie die Komponente **[!UICONTROL Adaptives Formular]** aus der Komponentenliste aus.

   ![Inhaltsstruktur](/help/edge/docs/forms/assets/add-adaptive-form-block.png)

   Der Abschnitt „Adaptives Formular“ wird hinzugefügt. Sie können nun damit beginnen, Formularkomponenten zur AEM-Projektseite hinzuzufügen.

1. Fügen Sie Formularkomponenten zum hinzugefügten Abschnitt „Adaptives Formular“ hinzu. So fügen Sie Formularkomponenten hinzu:
   1. Navigieren Sie in der Inhaltsstruktur zum hinzugefügten Abschnitt „Adaptives Formular“.

      ![Hinzugefügter adaptiver Formularblock](/help/edge/docs/forms/assets/adative-form-block.png)


   1. Klicken Sie auf das Symbol **[!UICONTROL Hinzufügen]** und fügen Sie die gewünschten Komponenten aus der Liste der **adaptiven Formularkomponenten** hinzu.

      ![Hinzufügen der Komponente](/help/edge/docs/forms/assets/add-component.png)

      Sie können die erforderlichen adaptiven Formularkomponenten auch einfach ziehen und ablegen. Der universelle Editor verfügt nämlich über eine intuitive Drag-and-Drop-Funktion.

   1. Wählen Sie die hinzugefügte adaptive Formularkomponente aus und aktualisieren Sie ihre Eigenschaften mithilfe von **[!UICONTROL Eigenschaften]**.

      ![Öffnen von Eigenschaften](/help/edge/docs/forms/assets/component-properties.png)

   1. Zeigen Sie das Formular in einer Vorschau an.
 Im folgenden Screenshot wird das Formular angezeigt, das mittels WYSIWYG-Authoring im AEM-Projekt erstellt wurde:

      ![Hinzugefügtes Formular](/help/edge/docs/forms/assets/added-form-aem-sites.png)

      Sobald Sie mit der Vorschau zufrieden sind, können Sie die Seite veröffentlichen.

      >[!NOTE]
      >
      > Es ist wichtig, die AEM-Projektseite erneut zu veröffentlichen, nachdem Sie Änderungen vorgenommen haben. Andernfalls sind die Aktualisierungen nicht im Browser sichtbar.

1. Veröffentlichen Sie die AEM-Projektseite erneut.

   1. Klicken Sie auf **Veröffentlichen**, um die AEM-Projektseite nach dem Hinzufügen des Formulars erneut zu veröffentlichen.

      ![Veröffentlichen des Formulars](/help/edge/docs/forms/assets/publish-form.png)

   1. Das Bestätigungsdialogfeld **Veröffentlichen** wird auf dem Bildschirm angezeigt. Klicken Sie auf **Veröffentlichen**, um mit der Veröffentlichung zu beginnen.

      ![Veröffentlichen von Formular1](/help/edge/docs/forms/assets/publish-form1.png)

      Nachdem Sie auf die Schaltfläche **Veröffentlichen** geklickt haben, wird die Meldung `Publish started successfully` angezeigt.

      ![Veröffentlichen von Formular2](/help/edge/docs/forms/assets/publish-form2.png)

   Sie können nun die AEM-Projektseite mit dem hinzugefügten Edge Delivery Services-Formular unter der folgenden URL aufrufen:
   `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   Wenn beispielsweise der Name der Verzweigung `main`, das Repository `edsforms`, die verantwortliche Person `wkndforms` und der Site-Name `eds-forms` lauten, sieht die URL wie folgt aus:
   `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   ![Indexseite](/help/edge/docs/forms/assets/publish-index-page.png)

Sie können die Edge Delivery Services-Formulare gestalten, indem Sie die `.css`- und `.js`-Dateien im adaptiven Formularblock bearbeiten und [eine lokale AEM-Entwicklungsumgebung einrichten](#set-up-local-aem-development-environment), um die Änderungen sofort in Ihrem Browser anzuzeigen.

>[!NOTE]
>
> Sie können auch [ein eigenständiges Formular im universellen Editor erstellen und es in Edge Delivery Services veröffentlichen](/help/edge/docs/forms/universal-editor/create-forms.md).

## Einrichten einer lokalen AEM-Entwicklungsumgebung

Sie können eine lokale AEM-Entwicklungsumgebung einrichten, um benutzerdefinierte Stile und Komponenten lokal zu entwickeln. Gehen Sie wie folgt vor, um in kürzester Zeit eine lokale AEM-Entwicklungsumgebung verwenden zu können:

1. **AEM-CLI installieren**: Die AEM-CLI vereinfacht Entwicklungsaufgaben. Wir werden sie global mit npm installieren:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. **GitHub-Projekt klonen**: Klonen Sie Ihr AEM-Projekt-Repository von GitHub mithilfe des folgenden Befehls und ersetzen Sie die Platzhalter <owner> durch die Repository-Besitzerin bzw. den Repository-Besitzer und <repo> mit dem Repository-Namen:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. **Lokale Umgebung starten**: Navigieren Sie zu Ihrem Projektverzeichnis und starten Sie Ihre lokale AEM-Instanz mit einem einzigen Befehl:

   ```
   cd <repo>
   aem up
   ```

Sie können lokale Änderungen im Ordner `blocks/form` für adaptive Formularblöcke zur Formatierung und Codierung Ihrer Formulare vornehmen. Bearbeiten Sie die `.css`- oder `.js`-Dateien in diesem Verzeichnis. Die Änderungen werden sofort in Ihrem Browser angezeigt.

Nachdem Sie Ihre Änderungen abgeschlossen haben, verwenden Sie Git-Befehle, um sie zu bestätigen und zu übertragen. Dadurch werden Ihre Vorschau- und Produktionsumgebungen aktualisiert, auf die über die folgenden URLs zugegriffen werden kann (Platzhalter durch Ihre Projektdetails ersetzen):

Vorschau: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`

Produktion: `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`


## Beheben von Build-Problemen in GitHub

Stellen Sie einen reibungslosen Build-Prozess in GitHub sicher, indem Sie potenzielle Probleme beheben:

* **Beheben von Linting-Fehlern:**
Sollten Sie auf Linting-Fehler stoßen, können Sie diese umgehen. Öffnen Sie die Datei [EDS Project]/package.json und ändern Sie das Skript „lint“ von `"lint": "npm run lint:js && npm run lint:css"` zu `"lint": "echo 'skipping linting for now'"`. Speichern Sie die Datei und übertragen Sie die Änderungen auf Ihr GitHub-Projekt.

* **Auflösen des Modulpfadfehlers:**
Wenn der Fehler „Pfad zum Modul ‚../../scripts/lib-franklin.js‘ kann nicht aufgelöst werden“ auftritt, navigieren Sie zu [EDS-Projekt]/blocks/forms/form.js. Aktualisieren Sie die Importanweisung, indem Sie die Datei „lib-franklin.js“ durch die Datei „aem.js“ ersetzen.

## Siehe auch

{{universal-editor-see-also}}
