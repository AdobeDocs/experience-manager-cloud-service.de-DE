---
title: Erste Schritte mit Edge Delivery Services für AEM Forms mit dem universellen Editor
description: Erfahren Sie, wie Sie leistungsstarke Formulare mit Edge Delivery Services mit WYSIWYG Authoring im universellen Editor erstellen und veröffentlichen.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 2%

---


# Erste Schritte mit Edge Delivery Services für AEM Forms mit dem universellen Editor

| Authoring-Methode | -Anleitung |
|---------------------------------|-----------------------------------------------------------------------|
| **Universeller Editor (WYSIWYG)** | Dieser Artikel |
| **Dokumentenbasiertes Authoring** | [Dokumentbasiertes Tutorial](/help/edge/docs/forms/tutorial.md) |

Edge Delivery Services für AEM Forms kombiniert leistungsstarke Web-Bereitstellung mit WYSIWYG-Authoring im universellen Editor. In diesem Handbuch wird das Erstellen, Anpassen und Veröffentlichen von schnell ladenden Formularen behandelt.

## Was Sie erreichen werden

Am Ende dieses Tutorials werden Sie:

- Einrichten eines GitHub-Repositorys mit dem adaptiven Forms-Block
- Erstellen einer in Edge Delivery Services integrierten AEM-Site
- Erstellen und Veröffentlichen von Formularen mit dem universellen Editor
- Konfigurieren einer lokalen Entwicklungsumgebung

## Pfad auswählen

Wählen Sie den Ansatz aus, der Ihrem Szenario entspricht:

![Wählen Sie Ihr Pfadentscheidungsleitfaden](/help/edge/docs/forms/universal-editor/assets/choose-your-path.svg)
*Abbildung: Visuelle Anleitung zur Auswahl des richtigen Implementierungspfads*

| **Pfad A: Neues Projekt** | **Pfad B: vorhandenes Projekt** |
|----------------------------------------|-------------------------------------------|
| Mit einer vorkonfigurierten Vorlage beginnen | Hinzufügen von Formularen zu Ihrem aktuellen AEM-Projekt |
| **Best for:** Neue Implementierungen | **Am besten geeignet für:** bestehende AEM Sites |
| **Was Sie erhalten** Vorkonfigurierter Forms-Block | **Was Sie erhalten:** Forms zu vorhandener Site hinzugefügt |
| **Schritte:** → Einrichtung → Forms | **Schritte:** Integration → Konfiguration → Forms |
| [Mit Pfad A beginnen](#path-a-create-new-project-with-forms) | [Mit Pfad B beginnen](#path-b-add-forms-to-existing-project) |

## Voraussetzungen

Bevor Sie beginnen, stellen Sie Folgendes sicher:

### Erforderlicher Zugriff

- **GitHub-Konto** mit Berechtigung zum Erstellen von Repositorys
- Authoring-Zugriff **** AEM as a Cloud Service

### Technische Anforderungen

- **Git-Grundlagen**: Klonen, Übertragen, Push-Vorgänge
- **Web-Technologien**: HTML, CSS, JavaScript-Grundlagen
- **Node.js** (ab Version 16 empfohlen) für die lokale Entwicklung
- **npm** oder **arn** Package Manager

### Empfohlene Kenntnisse

- Grundlegendes zu AEM Sites-Konzepten
- Vertrautheit mit den Prinzipien des Formularentwurfs
- Erfahrung mit WYSIWYG-Editoren

>[!TIP]
>
> Neu bei AEM? Beginnen Sie mit den ersten Schritten mit dem [Handbuch zu AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=de).

## Pfad A: Neues Projekt mit Forms erstellen

**Best for:** Neue Implementierungen oder Proof-of-Concepts

Das Textbaustein-Tool von AEM Forms bietet eine vorkonfigurierte Vorlage mit integriertem adaptivem Forms-Block.

### Übersicht über die Schritte

1. Einrichten eines GitHub-Repositorys über die Vorlage
2. Installieren von AEM Code Sync
3. Konfigurieren der AEM-Projektverbindung
4. Erstellen und Veröffentlichen einer AEM-Site
5. Hinzufügen von Formularen mit dem universellen Editor

Gehen wir die einzelnen Schritte durch:

+++Schritt 1: Erstellen eines GitHub-Repositorys aus einer Vorlage

1. **Zugriff auf die AEM Forms-Textvorlage**
   - Wechseln Sie zu [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)

   ![Textbausteinvorlage für AEM Forms](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   *Abbildung: AEM Forms-Textbaustein-Repository mit vorkonfiguriertem adaptiven Forms-Block*

2. **Repository erstellen**
   - Klicken Sie **Diese Vorlage verwenden** > **Neues Repository erstellen**

   ![Repository aus Vorlage erstellen](/help/edge/docs/forms/assets/use-eds-form-template.png)
   *Abbildung: Verwenden der Vorlage zum Erstellen eines neuen Repositorys*

3. **Repository-Einstellungen konfigurieren**
   - **Inhaber**: Wählen Sie Ihr GitHub-Konto oder Ihre Organisation aus
   - **Repository-Name**: Wählen Sie einen beschreibenden Namen aus (z. B. `my-forms-project`)
   - **Sichtbarkeit**: Wählen Sie **Öffentlich** (für Edge Delivery Services empfohlen)
   - Klicken Sie auf **Repository erstellen**

   ![Repository-Konfiguration](/help/edge/docs/forms/assets/name-eds-repo.png)
   *Abbildung: Konfigurieren des neuen Repositorys mit öffentlicher Sichtbarkeit*

**Validierung** Bestätigen Sie, dass Sie ein neues GitHub-Repository haben, das auf der Textvorlage von AEM Forms basiert.

+++

+++Schritt 2: Installieren von AEM Code Sync

AEM Code Sync synchronisiert automatisch Inhaltsänderungen zwischen Ihrer AEM-Autorenumgebung und Ihrem GitHub-Repository.

1. **Installieren der GitHub-App**
   - Wechseln Sie zu [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)

2. **Konfigurieren von Zugriffsberechtigungen**
   - Wählen Sie **Nur Repositorys auswählen**
   - Wählen Sie Ihr neu erstelltes Repository
   - Klicken Sie auf **Speichern**.

   ![Installation der AEM-Codesynchronisierung](/help/edge/docs/forms/assets/aem-code-sync-up.png)
   *Abbildung: Installieren von AEM Code Sync mit Repository-spezifischen Berechtigungen*

**Checkpoint:** AEM Code Sync ist jetzt installiert und hat Zugriff auf Ihr Repository.

+++

+++Schritt 3: Konfigurieren der AEM-Integration

Die `fstab.yaml`-Datei verbindet Ihr GitHub-Repository mit der AEM-Autorenumgebung für die Inhaltssynchronisierung.

1. **Navigieren Sie zu Ihrem Repository**
   - Wechseln Sie zu Ihrem neu erstellten GitHub-Repository
   - Sie sollten die Textbausteindateien für AEM Forms sehen

2. **Erstellen Sie die Datei „fstab.yaml“**
   - Klicken Sie **Datei hinzufügen** > **Neue Datei erstellen** im Stammverzeichnis
   - Benennen Sie die Datei `fstab.yaml`

   ![Erstellen der Datei „fstab.yaml“](/help/edge/docs/forms/assets/open-fstab.png)
   *Abbildung: Erstellen der Konfigurationsdatei „fstab.yaml“*

3. **Fügen Sie Ihre AEM-Verbindungsdetails hinzu**

   Kopieren Sie die folgende Konfiguration und fügen Sie sie ein. Ersetzen Sie dabei die Platzhalter:

   ```yaml
   mountpoints:
     /: https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main
   ```

   **Ersetzen:**
   - `<aem-author>`: Ihre AEM as a Cloud Service-Autoren-URL (z. B. `author-p12345-e67890.adobeaemcloud.com`)
   - `<owner>`: Ihr GitHub-Benutzername oder Ihre Organisation
   - `<repository>`: Ihr Repository-Name

   **Beispiel:**

   ```yaml
   mountpoints:
     /: https://author-p12345-e67890.adobeaemcloud.com/bin/franklin.delivery/mycompany/my-forms-project/main
   ```

   ![Bearbeiten der Datei „fstab.yaml“](/help/edge/docs/forms/assets/edit-fstab-file.png)
   *Abbildung: Konfigurieren des Bereitstellungspunkts für die AEM-Integration*

4. **Bestätigen Sie die Konfiguration**
   - Fügen Sie eine Commit-Nachricht hinzu: &quot;AEM-Integrationskonfiguration hinzufügen“
   - Klicken Sie **Neue Datei übertragen**

   ![Übernehmen von fstab-Änderungen](/help/edge/docs/forms/assets/commit-fstab-changes.png)
   *Abbildung: Übergeben der fstab.yaml-Konfiguration*

**Validierung:** Bestätigen Sie Ihre GitHub-Repository-Verbindung mit AEM.

>[!NOTE]
>
>Haben Sie Build-Probleme? Siehe [Fehlerbehebung für GitHub-Build-Probleme](#troubleshooting-github-build-issues).

+++

+++Schritt 4: Erstellen Sie eine AEM-Site, die mit Ihrem GitHub-Repository verbunden ist.

1. **Zugriff auf die AEM Sites-Konsole**
   - Melden Sie sich bei Ihrer AEM as a Cloud Service-Autoreninstanz an
   - Navigieren Sie zu **Sites**

   ![AEM Sites-Konsole](/help/edge/assets/select-sites.png)
   *Abbildung: Zugriff auf die AEM Sites-Konsole*

2. **Site-Erstellung starten**
   - Klicken Sie **Erstellen** > **Site aus Vorlage**

   ![Option „Site erstellen“](/help/edge/docs/forms/assets/create-sites.png)
   *Abbildung: Erstellen einer neuen Site aus einer Vorlage*

3. **Wählen Sie die Edge Delivery Services-Vorlage**
   - Wählen Sie die Vorlage **Edge Delivery Services-Site** aus
   - Klicken Sie auf **Weiter**.

   ![Site-Vorlagenauswahl](/help/edge/docs/forms/assets/select-site-template.png)
   *Abbildung: Auswählen der Edge Delivery Services-Site-Vorlage*

   >[!NOTE]
   >
   >**Vorlage nicht verfügbar?** Wenn die Edge Delivery Services-Vorlage nicht angezeigt wird:
   >
   >1. Klicken Sie auf **Importieren**, um die Vorlage hochzuladen
   >2. Herunterladen von Vorlagen aus [GitHub-Versionen](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)

4. **Konfigurieren der Site**

   Geben Sie folgende Informationen ein:

   | Feld | Wert | Beispiel |
   |-----------------|-----------------------------|-----------------------------------------|
   | **Site-Titel** | Beschreibender Name der Website | „Mein Forms-Projekt“ |
   | **Site-Name** | URL-freundlicher Name | „my-forms-project“ |
   | **GitHub-URL** | Ihre Repository-URL | `https://github.com/mycompany/my-forms-project` |

   ![Site-Konfiguration](/help/edge/docs/forms/assets/create-aem-site.png)
   *Abbildung: Konfigurieren Ihrer neuen AEM-Site mit GitHub-Integration*

5. **Vollständige Site-Erstellung**
   - Überprüfen der Einstellungen
   - Klicken Sie auf **Erstellen**.

   ![Bestätigen der Site-Erstellung](/help/edge/docs/forms/assets/click-ok-aem-site.png)
   *Abbildung: Bestätigen der Site-Erstellung*

   **Erfolg!** Ihre AEM-Site ist jetzt erstellt und mit GitHub verbunden.

6. **Im universellen Editor öffnen**
   - Suchen Sie in der Sites-Konsole Ihre neue Site
   - Wählen Sie die Seite `index`
   - Klicken Sie auf **Bearbeiten**

   ![Website im universellen Editor bearbeiten](/help/edge/docs/forms/assets/edit-site.png)
   *Abbildung: Öffnen der Site zur Bearbeitung*

   Der universelle Editor wird auf einer neuen Registerkarte geöffnet und bietet WYSIWYG-Authoring-Funktionen.

   ![Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/assets/site-in-universal-editor.png)
   *Abbildung: Ihre Site wurde im universellen Editor zur Bearbeitung in WYSIWYG geöffnet*

**Validierung:** Sie, dass Ihre AEM-Site zum Erstellen von Formularen bereit ist.

+++

+++Schritt 5: Veröffentlichen der Site

Durch die Veröffentlichung wird Ihre Site in Edge Delivery Services für globalen Zugriff verfügbar.

1. **Quick Publish über die Sites-Konsole**
   - Kehren Sie zur AEM Sites-Konsole zurück
   - Seiten der Site auswählen (oder alles mit Strg+A auswählen)
   - Klicken Sie **Quick Publish**

   ![Veröffentlichen der AEM-Site](/help/edge/docs/forms/assets/publish-sites.png)
   *Abbildung: Auswählen von Seiten für die Schnellveröffentlichung*

2. **Veröffentlichung bestätigen**
   - Klicken Sie im Bestätigungsdialogfeld auf **Veröffentlichen**

   ![Dialogfeld „Quick Publish“](/help/edge/docs/forms/assets/quick-publish.png)
   *Abbildung: Bestätigen der Veröffentlichungsaktion*

   **Alternative** Sie können mit der Schaltfläche Veröffentlichen auch direkt im universellen Editor veröffentlichen.

   ![Veröffentlichen im universellen Editor](/help/edge/docs/forms/assets/qui.png)
   *Abbildung: Direktes Veröffentlichen im universellen Editor*

3. **Zugriff auf Ihre Live-Site**

   Ihre Website ist jetzt live unter:

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **Erläuterung der URL-Struktur:**
   - `<branch>`: GitHub-Verzweigung (normalerweise `main`)
   - `<repo>`: Ihr Repository-Name
   - `<owner>`: Ihr GitHub-Benutzername oder Ihre Organisation
   - `<site-name>`: Ihr AEM-Site-Name

   **Beispiel:**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

**Validierung:** Bestätigen Sie, dass Ihre Site auf Edge Delivery Services live ist.

>[!TIP]
>
> **URL-Muster:**
>
> - **Startseite:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
> - **Andere Seiten:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<page-name>`

**Weiter:** [Erstellen Sie Ihr erstes Formular](#create-your-first-form)

+++

## Pfad B: Forms zu vorhandenem Projekt hinzufügen

**Am besten geeignet für:** vorhandener AEM Sites mit Edge Delivery Services

Wenn Sie bereits über ein AEM-Projekt mit Edge Delivery Services verfügen, können Sie durch Integration des adaptiven Forms-Blocks Formularfunktionen hinzufügen.

### Voraussetzungen für Pfad B

- Vorhandenes AEM-Projekt, erstellt mit [AEM Boilerplate XWalk](https://github.com/adobe-rnd/aem-boilerplate-xwalk)
- Einrichten einer lokalen Entwicklungsumgebung
- Git-Zugriff auf Ihr Projekt-Repository

**Mit AEM Forms Textbaustein?** Wenn Ihr Projekt mit dem [AEM Forms-Textbaustein](https://github.com/adobe-rnd/aem-boilerplate-forms) erstellt wurde, sind Formulare bereits integriert. Wechseln Sie zu [Erstes Formular erstellen](#create-your-first-form).

Gehen wir die einzelnen Schritte durch:

### Übersicht über die Schritte

1. Kopieren von adaptiven Forms-Blockdateien
2. Projektkonfiguration aktualisieren
3. Konfigurieren von ESLint-Regeln
4. Änderungen erstellen und bestätigen

+++Schritt 1: Forms-Blockdateien kopieren

1. **Navigieren Sie zu Ihrem lokalen Projekt**

   ```bash
   cd /path/to/your/aem-project
   ```

2. **Herunterladen erforderlicher Dateien vom AEM Forms-Textbaustein**

   Kopieren Sie diese Dateien aus dem Textbausteinrepository von [AEM Forms](https://github.com/adobe-rnd/aem-boilerplate-forms):

   | Quelle | Ziel | Zweck |
   |------------------------------------------------------------------------|----------------------------|----------------------------|
   | [`blocks/form/`](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) | `blocks/form/` | Kernfunktionen von Formularen |
   | [`scripts/form-editor-support.js`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) | `scripts/form-editor-support.js` | Integration des universellen Editors |
   | [`scripts/form-editor-support.css`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) | `scripts/form-editor-support.css` | Editor-Stile |

3. **Editor-Unterstützung aktualisieren**
   - Ersetzen Sie Ihre `/scripts/editor-support.js`-Datei durch die Datei [editor-support.js aus AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js)

**Validierung:** Sie, dass sich Formularblockdateien in Ihrem Projekt befinden.

+++

+++Schritt 2: Aktualisieren der Komponentenkonfiguration

1. **Abschnittsmodell aktualisieren**

   Öffnen Sie `/models/_section.json` und fügen Sie den Filtern Formularkomponenten hinzu:

   ```json
   {
        "filters": [
        {
      "id": "section",
      "components": [
           "text",
           "image",
           "button",
        "form",
        "embed-adaptive-form"
      ]
       }
     ]
   }
   ```

   **Vorgehensweise:** Aktiviert Formularkomponenten in der Komponentenauswahl des universellen Editors.

**Validierung:** Formularkomponenten werden im universellen Editor angezeigt.

+++

+++Schritt 3: Konfigurieren von ESLint (optional)

**Warum dieser Schritt:** Verhindert Verknüpfungsfehler aus formularspezifischen Dateien und konfiguriert korrekte Validierungsregeln.

1. **Aktualisieren .eslintignore**

   Fügen Sie diese Zeilen zu `/.eslintignore` hinzu:

   ```bash
   # Form block rule engine files
    blocks/form/rules/formula/*
    blocks/form/rules/model/*
    blocks/form/rules/functions.js
    scripts/editor-support.js
    scripts/editor-support-rte.js
   ```

2. **Aktualisieren von .eslintrc.js**

   Fügen Sie diese Regeln zum `rules` in `/.eslintrc.js` hinzu:

   ```javascript
   {
     "rules": {
       // Existing rules...
   
       // Form component cell limits
    'xwalk/max-cells': ['error', {
         '*': 4, // default limit
      form: 15,
      wizard: 12,
      'form-button': 7,
      'checkbox-group': 20,
      checkbox: 19,
      'date-input': 21,
      'drop-down': 19,
      email: 22,
      'file-input': 20,
      'form-fragment': 15,
      'form-image': 7,
      'multiline-input': 23,
      'number-input': 22,
      panel: 17,
      'radio-group': 20,
      'form-reset-button': 7,
      'form-submit-button': 7,
      'telephone-input': 20,
      'text-input': 23,
      accordion: 14,
      modal: 11,
      rating: 18,
      password: 20,
         tnc: 12
       }],
   
       // Disable this rule for forms
       'xwalk/no-orphan-collapsible-fields': 'off'
     }
   }
   ```

**Validierung:**, dass ESLint mit Formularkomponenten funktioniert.

+++

+++Schritt 4: Erstellen und bereitstellen

1. **Installieren von Abhängigkeiten und Build**

   ```bash
   # Install any new dependencies
   npm install
   
   # Build component definitions
   npm run build:json
   ```

   **Funktion:**
   - Aktualisiert `component-definition.json` mit Formularkomponenten
   - Erzeugt `component-models.json` mit Formularmodellen
   - Erstellt `component-filters.json` mit Filterregeln

2. **Überprüfen der generierten Dateien**

   Vergewissern Sie sich, dass diese Dateien im Projektstamm formularbezogene Objekte enthalten:
   - `component-definition.json`
   - `component-models.json`
   - `component-filters.json`

3. **Änderungen übertragen und übertragen**

   ```bash
   git add .
   git commit -m "Add Adaptive Forms Block integration"
   git push origin main
   ```

**Validierung:** Sie, dass Ihr Projekt Formularfunktionen enthält.

+++

**Weiter:** [Erstellen Sie Ihr erstes Formular](#create-your-first-form)

## Erstellen des ersten Formulars

**Gilt für:** Benutzer von Pfad A und Pfad B

Nachdem Ihr Projekt mit Formularfunktionen eingerichtet wurde, erstellen wir Ihr erstes Formular mit der WYSIWYG-Oberfläche des universellen Editors.

### Überblick über den Prozess der Formularerstellung

1. **Adaptiven Formularblock hinzufügen** auf Ihrer Seite
2. **Hinzufügen von Formularkomponenten** (Texteingaben, Schaltflächen usw.)
3. **Konfigurieren von Komponenteneigenschaften**
4. **Vorschau und Test** des Formulars
5. **Veröffentlichen** der aktualisierten Seite

Gehen wir die einzelnen Schritte durch:

+++Schritt 1: Adaptiven Formularblock hinzufügen

1. **Öffnen Sie Ihre Seite im universellen Editor**
   - Navigieren Sie zur **Sites**-Konsole in AEM
   - Wählen Sie die Seite aus, auf der Sie ein Formular hinzufügen möchten (z. B. `index`)
   - Klicken Sie auf **Bearbeiten**

   Ihre Seite wird im universellen Editor zur Bearbeitung in WYSIWYG geöffnet.

2. **Fügen Sie die Komponente Adaptives Formular hinzu**
   - Öffnen Sie das **Inhaltsstruktur**-Bedienfeld (linke Seitenleiste)
   - Navigieren Sie zu einem Abschnitt, in dem Sie Ihr Formular hinzufügen möchten
   - Klicken Sie auf **Symbol** Hinzufügen“ (+)
   - Wählen Sie **Adaptives Formular** in der Komponentenliste aus

   ![Hinzufügen eines adaptiven Formularblocks](/help/edge/docs/forms/assets/add-adaptive-form-block.png)
   *Abbildung: Hinzufügen eines adaptiven Formularblocks zu Ihrer Seite*

**Validierung** Bestätigen Sie, dass Sie einen leeren Formular-Container haben.

+++

+++Schritt 2: Hinzufügen von Formularkomponenten

1. **Navigieren Sie zu Ihrem Formularblock**
   - Suchen Sie in der Inhaltsstruktur den Abschnitt für das neu hinzugefügte adaptive Formular .

   ![Adaptiver Formularblock hinzugefügt](/help/edge/docs/forms/assets/adative-form-block.png)
   *Abbildung: Adaptiver Formularblock in der Inhaltsstruktur*

2. **Hinzufügen von Formularkomponenten**

   Sie können Komponenten auf zwei Arten hinzufügen:

   **Methode A: Zum Hinzufügen klicken**
   - Klicken Sie auf **Symbol** Hinzufügen“ (+) in Ihrem Formularabschnitt
   - Wählen Sie Komponenten in der Liste **Adaptive Formularkomponenten** aus

   **Methode B: Drag-and-Drop**
   - Ziehen Sie Komponenten direkt aus dem Komponentenfeld in das Formular

   ![Hinzufügen von Formularkomponenten](/help/edge/docs/forms/assets/add-component.png)
   *Abbildung: Hinzufügen von Komponenten zu einem Formular*

   **Empfohlene Starterkomponenten:**
   - Texteingabe (für Name, E-Mail)
   - Textbereich (für Nachrichten)
   - Schaltfläche „Senden“

3. **Konfigurieren von Komponenteneigenschaften**
   - Eine beliebige Formularkomponente auswählen
   - Verwenden Sie das Bedienfeld **Eigenschaften** (rechte Seitenleiste) zum Konfigurieren von:
      - Beschriftungen und Platzhalter
      - Validierungsregeln
      - Erforderliche Feldeinstellungen

   ![Bedienfeld Komponenteneigenschaften](/help/edge/docs/forms/assets/component-properties.png)
   *Abbildung: Konfigurieren von Komponenteneigenschaften*

4. **Vorschau des Formulars**

   Ihr Formular sieht in etwa so aus:

   ![Ausgefüllte Formularvorschau](/help/edge/docs/forms/assets/added-form-aem-sites.png)
   *Abbildung: Beispielformular, das mit dem universellen Editor erstellt wurde*

**Validierung:** Sie, dass das Formular zur Veröffentlichung bereit ist.

>[!IMPORTANT]
>
> Denken Sie daran, die Seite zu veröffentlichen, nachdem Sie Änderungen vorgenommen haben, damit Aktualisierungen im Browser angezeigt werden.

+++

+++Schritt 3: Formular veröffentlichen

1. **Veröffentlichen im universellen Editor**
   - Klicken Sie im universellen Editor auf **Veröffentlichen**-Schaltfläche

   ![Formular wird ](/help/edge/docs/forms/assets/publish-form.png)
   *Abbildung: Veröffentlichen Ihres Formulars im universellen Editor*

2. **Veröffentlichung bestätigen**
   - Klicken Sie im Bestätigungsdialogfeld auf **Veröffentlichen**

   ![Veröffentlichungsbestätigung](/help/edge/docs/forms/assets/publish-form1.png)
   *Abbildung: Bestätigen der Veröffentlichungsaktion*

   Sie sehen eine Erfolgsmeldung, die die Veröffentlichung bestätigt.

   ![Erfolgreiche Veröffentlichung](/help/edge/docs/forms/assets/publish-form2.png)
   *Abbildung: Bestätigung der erfolgreichen Veröffentlichung*

3. **Live-Formular anzeigen**

   Ihr Formular ist jetzt live unter:

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **Beispiel-URL:**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

   ![Live Form Page](/help/edge/docs/forms/assets/publish-index-page.png)
   *Abbildung: Die veröffentlichte Formularseite in Edge Delivery Services*

**Herzlichen Glückwunsch!** Ihr Formular ist jetzt live und bereit, Übermittlungen zu erfassen.

+++

### Nächste Schritte

Nachdem Sie nun über ein Arbeitsformular verfügen, können Sie:

- **Anpassen des** durch Bearbeiten von CSS- und JavaScript-Dateien
- **Hinzufügen erweiterter Formularfunktionen** wie Validierungsregeln und bedingter Logik
- **Einrichten der lokalen Entwicklung** für eine schnellere Iteration
- **Erstellen eigenständiger Formulare** für bestimmte Anwendungsfälle

>[!TIP]
>
> **Weitere Informationen:** [Erstellen eigenständiger Formulare im universellen Editor](/help/edge/docs/forms/universal-editor/create-forms.md)

## Einrichten einer lokalen Entwicklungsumgebung

**Am besten geeignet für:** Entwickler, die den Formularstil und das Verhalten anpassen möchten

In einer lokalen Entwicklungsumgebung können Sie Änderungen vornehmen und sofort anzeigen, ohne den Veröffentlichungszyklus zu durchlaufen.

+++Einrichten von AEM CLI und lokaler Entwicklung

1. **Installieren von AEM CLI**

   Die AEM-CLI vereinfacht lokale Entwicklungsaufgaben:

   ```bash
   npm install -g @adobe/aem-cli
   ```

2. **Klonen Sie Ihr Repository**

   ```bash
   git clone https://github.com/<owner>/<repo>
   cd <repo>
   ```

   Ersetzen Sie `<owner>` und `<repo>` durch Ihre tatsächlichen GitHub-Details.

3. **Starten Sie den lokalen Entwicklungs-Server**

   ```bash
   aem up
   ```

   Dadurch wird ein lokaler Server mit Hot-Relload-Funktionen gestartet.

4. **Anpassungen vornehmen**

   - Bearbeiten von Dateien im `blocks/form/` Verzeichnis für Formularstile und -verhalten
   - `form.css` für Stile ändern
   - `form.js` für das Verhalten aktualisieren

   **Änderungen sofort anzeigen** in Ihrem Browser unter `http://localhost:3000`

5. **Bereitstellen Ihrer Änderungen**

   ```bash
   git add .
   git commit -m "Custom form styling"
   git push origin main
   ```

   Ihre Änderungen sind verfügbar unter:
   - **Vorschau:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
   - **Produktion:** `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`

+++


## Fehlerbehebung

### Häufige Probleme und Lösungen

+++GitHub-Build-Probleme

**Problem** Build-Fehler oder Verknüpfungsfehler

**Lösung 1: Linting-Fehler beheben**

Wenn Sie auf Verknüpfungsfehler stoßen:

1. Öffnen Sie `package.json` in Ihrem Projektstamm
2. Suchen des `lint`:

   ```json
   "scripts": {
     "lint": "npm run lint:js && npm run lint:css"
   }
   ```

3. Linting vorübergehend deaktivieren:

   ```json
   "scripts": {
     "lint": "echo 'skipping linting for now'"
   }
   ```

4. Bestätigen und Übertragen der Änderungen

**Lösung 2: Fehler im Modulpfad**

Wenn „Der Pfad zum Modul &quot;/scripts/lib-franklin.js&quot; kann nicht aufgelöst werden“ angezeigt wird:

1. Navigieren Sie zu `blocks/form/form.js`
2. Aktualisieren Sie die Importanweisung:

   ```javascript
   // Change this:
   import { ... } from '/scripts/lib-franklin.js';
   
   // To this:
   import { ... } from '/scripts/aem.js';
   ```

+++

+++Probleme mit dem universellen Editor

**Problem:** Formularkomponenten werden nicht im universellen Editor angezeigt

**Lösungen:**

- Überprüfen Sie, ob AEM Code Sync installiert ist und ausgeführt wird
- Vergewissern Sie sich, dass `fstab.yaml` über die richtige AEM-Autoren-URL verfügt
- Stellen Sie sicher, dass für Ihre AEM-Instanz der frühzeitige Zugriff aktiviert ist
- Bestätigen, `component-definition.json` Formularkomponenten enthält

**Problem:** Änderungen nach der Veröffentlichung nicht sichtbar

**Lösungen:**

- Auf CDN-Cache-Aktualisierung warten
- Browser-Cache überprüfen (im Inkognito-/Privat-Modus versuchen)
- Überprüfen, ob das richtige URL-Format verwendet wird

+++

+++Probleme mit der Formularfunktionalität

**Problem:** Formularübermittlungen funktionieren nicht

**Lösungen:**

- Stellen Sie sicher, dass Sie über eine Senden-Schaltflächenkomponente verfügen
- Konfiguration der Formularaktions-URL überprüfen
- Überprüfen von Formularvalidierungsregeln
- Zuerst im Vorschaumodus testen

**Problem:** Stilprobleme

**Lösungen:**

- Überprüfen von CSS-Dateipfaden in `blocks/form/`
- Browser-Cache löschen
- Überprüfen der CSS-Syntax
- Testen in der lokalen Entwicklungsumgebung

+++

