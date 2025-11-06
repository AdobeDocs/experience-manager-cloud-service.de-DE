---
title: Erste Schritte mit Edge Delivery Services für AEM Forms mithilfe des universellen Editors
description: Erfahren Sie, wie Sie unter Einsatz von Edge Delivery Services mit WYSIWYG-Authoring im universellen Editor leistungsstarke Formulare erstellen und veröffentlichen können.
feature: Edge Delivery Services
role: Admin, Developer
level: Intermediate
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2608'
ht-degree: 100%

---


# Erste Schritte mit Edge Delivery Services für AEM Forms mithilfe des universellen Editors

| Authoring-Methode | Handbuch |
|---------------------------------|-----------------------------------------------------------------------|
| **Universeller Editor (WYSIWYG)** | Dieser Artikel |
| **Dokumentenbasiertes Authoring** | [Dokumentenbasiertes Tutorial](/help/edge/docs/forms/tutorial.md) |

Edge Delivery Services für AEM Forms kombiniert eine effektive Web-Bereitstellung mit WYSIWYG-Authoring im universellen Editor. In diesem Handbuch wird das Erstellen, Anpassen und Veröffentlichen von schnell ladenden Formularen behandelt.

## Was Sie erreichen werden:

Am Ende dieses Tutorials werden Sie folgende Aufgaben erledigen können:

- Ein GitHub-Repository mit dem adaptiven Formularblock einrichten
- Eine in Edge Delivery Services integrierte AEM-Site erstellen
- Formulare mit dem universellen Editor erstellen und veröffentlichen
- Eine lokale Entwicklungsumgebung konfigurieren

## Wählen Sie Ihren Pfad aus

Wählen Sie den Ansatz aus, der Ihrem Szenario entspricht:

![Wählen Sie Ihren Pfad –Entscheidungshandbuch](/help/edge/docs/forms/universal-editor/assets/choose-your-path.svg)
*Abbildung: Visuelle Anleitung zur Auswahl des richtigen Implementierungspfads*

| **Pfad A: neues Projekt** | **Pfad B: vorhandenes Projekt** |
|----------------------------------------|-------------------------------------------|
| Mit einer vorkonfigurierten Vorlage beginnen | Formulare zu Ihrem vorhandenen AEM-Projekt hinzufügen |
| **Am besten geeignet für:** neue Implementierungen | **Am besten geeignet für:** bestehende AEM-Sites |
| **Was Sie erhalten:** vorkonfigurierter Formularblock | **Was Sie erhalten:** Formulare, die zu einer vorhandenen Site hinzugefügt werden |
| **Schritte:** Vorlage → Setup → Formulare | **Schritte:** Integration → Konfiguration → Formulare |
| [Mit Pfad A beginnen](#path-a-create-new-project-with-forms) | [Mit Pfad B beginnen](#path-b-add-forms-to-existing-project) |

## Voraussetzungen

Um sicherzustellen, dass Edge Delivery Services für AEM Forms mit dem universellen Editor reibungslos funktioniert, prüfen und bestätigen Sie die folgenden Voraussetzungen, bevor Sie fortfahren:

### Zugriffsanforderungen

- **GitHub-Konto**: Sie müssen über ein GitHub-Konto mit Berechtigungen zum Erstellen neuer Repositorys verfügen. Dies ist für die Verwaltung des Quell-Codes Ihres Projekts und die Zusammenarbeit mit Ihrem Team von entscheidender Bedeutung.
- **Authoring-Zugriff auf AEM as a Cloud Service**: Stellen Sie sicher, dass Sie Authoring-Zugriff auf Ihre AEM as a Cloud Service-Umgebung haben. Dieser Zugriff ist erforderlich, damit Sie Formulare erstellen, bearbeiten und veröffentlichen können.

### Technische Anforderungen

- **Vertrautheit mit Git**: Sie sollten mit der Durchführung grundlegender Git-Vorgänge wie dem Klonen von Repositorys, dem Übergeben von Änderungen und dem Pushen von Aktualisierungen vertraut sein. Diese Fähigkeiten sind für die Quellenverwaltung und die Zusammenarbeit bei Projekten von grundlegender Bedeutung.
- **Grundlegendes zu Web-Technologien**: Es werden grundlegende Kenntnisse in HTML, CSS und JavaScript empfohlen. Diese Technologien bilden das Fundament für die Anpassung und Fehlerbehebung bei Formularen.
- **Node.js (Version 16 oder höher)**: Für die lokale Entwicklung und die Ausführung von Build-Tools ist Node.js erforderlich. Stellen Sie sicher, dass auf Ihrem System Version 16 oder höher installiert ist.
- **Paket-Manager (npm oder yarn)**: Sie benötigen entweder npm (Node Package Manager) oder yarn, um Projektabhängigkeiten und Skripte zu verwalten.

### Empfohlener Hintergrund

- **AEM Sites-Konzepte**: Ein grundlegendes Verständnis von AEM Sites, einschließlich Site-Struktur und Inhaltserstellung, hilft Ihnen bei der effektiven Navigation und Integration von Formularen.
- **Prinzipien der Formulargestaltung**: Wenn Sie mit Best Practices für die Formulargestaltung vertraut sind (wie z. B. Benutzerfreundlichkeit, Zugänglichkeit und Datenvalidierung), können Sie effektive und benutzerfreundliche Formulare erstellen.
- **Erfahrung mit WYSIWYG-Editoren**: Frühere Erfahrungen mit der Verwendung von What You See Is What You Get (WYSIWYG)-Editoren helfen Ihnen, die visuellen Authoring-Funktionen des universellen Editors effizienter zu nutzen.

>[!TIP]
>
> Neu bei AEM? Beginnen Sie mit dem [Handbuch mit ersten Schritten zu AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=de).

## Pfad A: Erstellen eines neuen Projekts mit Formularen

**Empfohlen für:** neue Projekte, Pilotprojekte oder Proof-of-Concept-Initiativen

Nutzen Sie den AEM Forms-Baustein, um Ihre Projekteinrichtung zu beschleunigen. Dieser Baustein bietet eine einsatzbereite Vorlage, die den adaptiven Formularblock nahtlos integriert, sodass Sie Formulare auf Ihrer AEM-Site schnell erstellen und bereitstellen können.

### Überblick

Um Ihr neues Projekt mit integrierten Formularen erfolgreich zu starten, gehen Sie folgendermaßen vor:

1. Erstellen Sie mit der AEM Forms-Bausteinvorlage ein GitHub-Repository.
2. Richten Sie AEM Code Sync ein, um die Inhaltssynchronisierung zwischen AEM und Ihrem Repository zu automatisieren.
3. Konfigurieren Sie die Verbindung zwischen Ihrem GitHub-Projekt und Ihrer AEM-Umgebung.
4. Erstellen und veröffentlichen Sie eine neue AEM-Site.
5. Verwalten und fügen Sie Formulare mit dem universellen Editor hinzu.

Die folgenden Abschnitte führen Sie im Detail durch die einzelnen Schritte, um für eine reibungslose und effiziente Projekteinrichtung zu sorgen.

+++Schritt 1: Erstellen eines GitHub-Repositorys aus einer Vorlage

1. **Zugriff auf die AEM Forms-Bausteinvorlage**
   - Navigieren Sie zu [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

   ![AEM Forms-Bausteinvorlage](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   *Abbildung: AEM Forms-Baustein-Repository mit vorkonfiguriertem adaptiven Formularblock*

2. **Erstellen Ihres Repositorys**
   - Klicken Sie auf **Diese Vorlage verwenden** > **Neues Repository erstellen**.

   ![Erstellen eines Repositorys aus einer Vorlage](/help/edge/docs/forms/assets/use-eds-form-template.png)
   *Abbildung: Verwenden der Vorlage zum Erstellen eines neuen Repositorys*

3. **Konfigurieren der Repository-Einstellungen**
   - **Inhaber**: Wählen Sie Ihr GitHub-Konto oder Ihre Organisation aus.
   - **Repository-Name**: Wählen Sie einen beschreibenden Namen aus (z. B. `my-forms-project`).
   - **Sichtbarkeit**: Wählen Sie **Öffentlich** (für Edge Delivery Services empfohlen).
   - Klicken Sie auf **Repository erstellen**.

   ![Repository-Konfiguration](/help/edge/docs/forms/assets/name-eds-repo.png)
   *Abbildung: Konfigurieren des neuen Repositorys mit öffentlicher Sichtbarkeit*

**Validierung** Vergewissern Sie sich, dass Sie ein neues GitHub-Repository haben, das auf der Bausteinvorlage von AEM Forms basiert.

+++

+++Schritt 2: Installieren von AEM Code Sync

AEM Code Sync sorgt für eine automatische Synchronisierung von Inhaltsänderungen zwischen Ihrer AEM-Authoring-Umgebung und Ihrem GitHub-Repository.

1. **Installieren der GitHub-App**
   - Navigieren Sie zu [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).

2. **Konfigurieren von Zugriffsberechtigungen**
   - Wählen Sie **Nur bestimmte Repositorys**.
   - Wählen Sie Ihr neu erstelltes Repository aus.
   - Klicken Sie auf **Speichern**.

   ![Installation von AEM Code Sync](/help/edge/docs/forms/assets/aem-code-sync-up.png)
   *Abbildung: Installieren von AEM Code Sync mit Repository-spezifischen Berechtigungen*

**Checkpoint:** AEM Code Sync ist jetzt installiert und hat Zugriff auf Ihr Repository.

+++

+++Schritt 3: Konfigurieren der AEM-Integration

Die `fstab.yaml`-Datei verbindet Ihr GitHub-Repository für die Inhaltssynchronisierung mit der AEM-Authoring-Umgebung.

1. **Navigieren Sie zu Ihrem Repository.**
   - Wechseln Sie zu Ihrem neu erstellten GitHub-Repository.
   - Sie sollten die Bausteindateien von AEM Forms sehen.

2. **Erstellen der Datei „fstab.yaml“**
   - Klicken Sie im Stammverzeichnis auf **Datei hinzufügen** > **Neue Datei erstellen**.
   - Suchen Sie die Datei `fstab.yaml`.

   ![Erstellen der „fstab.yaml“](/help/edge/docs/forms/assets/open-fstab.png)
   *Abbildung: Erstellen der Konfigurationsdatei „fstab.yaml“*

3. **Fügen Sie Ihre AEM-Verbindungsdetails hinzu.**

   Kopieren Sie die folgende Konfiguration und fügen Sie sie ein. Ersetzen Sie dabei die Platzhalter:

   ```yaml
   mountpoints:
     /: 
     url: https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main
     type: "markup" 
     suffix: ".html" 
   ```

   **Ersetzen Sie:**
   - `<aem-author>`: Ihre AEM as a Cloud Service-Autoren-URL (z. B. `author-p12345-e67890.adobeaemcloud.com`)
   - `<owner>`: Ihren GitHub-Benutzernamen oder Ihre Organisation
   - `<repository>`: Ihren Repository-Name

   **Beispiel:**

   ```yaml
   mountpoints:
     /: https://author-p12345-e67890.adobeaemcloud.com/bin/franklin.delivery/mycompany/my-forms-project/main
   ```

   ![Bearbeiten der Datei „fstab.yaml“](/help/edge/docs/forms/assets/edit-fstab-file.png)
   *Abbildung: Konfigurieren des Bereitstellungspunkts für die AEM-Integration*

4. **Übermitteln Sie die Konfiguration.**
   - Fügen Sie eine Commit-Nachricht hinzu: „Konfiguration für AEM-Integration hinzufügen“.
   - Klicken Sie auf **Neue Datei übermitteln**.

   ![Übermitteln von fstab-Änderungen](/help/edge/docs/forms/assets/commit-fstab-changes.png)
   *Abbildung: Übermitteln der fstab.yaml-Konfiguration*

**Validierung:** Prüfen Sie die Verbindung zwischen Ihrem GitHub-Repository und AEM.

>[!NOTE]
>
> Haben Sie Build-Probleme? Siehe [Beheben von Build-Problemen in GitHub](#troubleshooting-github-build-issues).

+++

+++Schritt 4: Erstellen einer mit Ihrem GitHub-Repository verbundenen AEM-Site.

1. **Zugriff auf die AEM Sites-Konsole**
   - Melden Sie sich bei Ihrer Authoring-Instanz in AEM as a Cloud Service an.
   - Navigieren Sie zu **Sites**.

   ![AEM Sites-Konsole](/help/edge/assets/select-sites.png)
   *Abbildung: Aufrufen der AEM Sites-Konsole*

2. **Starten der Site-Erstellung**
   - Klicken Sie auf **Erstellen** > **Site aus Vorlage**.

   ![Option „Site erstellen“](/help/edge/docs/forms/assets/create-sites.png)
   *Abbildung: Erstellen einer neuen Site aus einer Vorlage*

3. **Auswählen der Edge Delivery Services-Vorlage**
   - Wählen Sie die Vorlage **Edge Delivery Services-Site** aus.
   - Klicken Sie auf **Weiter**.

   ![Auswahl der Site-Vorlage](/help/edge/docs/forms/assets/select-site-template.png)
   *Abbildung: Auswählen der Site-Vorlage für Edge Delivery Services*

   >[!NOTE]
   >
   >**Vorlage nicht verfügbar?** Wenn die Edge Delivery Services-Vorlage nicht angezeigt wird:
   >
   >1. Klicken Sie auf **Importieren**, um die Vorlage hochzuladen.
   >2. Herunterladen von Vorlagen aus [GitHub-Versionen](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)

4. **Konfigurieren Sie Ihre Site**

   Geben Sie folgende Informationen ein:

   | Feld | Wert | Beispiel |
   |-----------------|-----------------------------|-----------------------------------------|
   | **Site-Titel** | Beschreibender Name für Site | „Mein Formularprojekt“ |
   | **Site-Name** | URL-freundlicher Name | „my-forms-project“ |
   | **GitHub-URL** | Ihre Repository-URL | `https://github.com/mycompany/my-forms-project` |

   ![Site-Konfiguration](/help/edge/docs/forms/assets/create-aem-site.png)
   *Abbildung: Konfigurieren Ihrer neuen AEM-Site mit GitHub-Integration*

5. **Vollständige Site-Erstellung**
   - Prüfen Sie Ihre Einstellungen.
   - Klicken Sie auf **Erstellen**.

   ![Bestätigen der Site-Erstellung](/help/edge/docs/forms/assets/click-ok-aem-site.png)
   *Abbildung: Bestätigen der Site-Erstellung*

   **Sie waren erfolgreich!** Ihre AEM-Site ist jetzt eingerichtet und mit GitHub verbunden.

6. **Öffnen im universellen Editor**
   - Suchen Sie in der Sites-Konsole Ihre neue Site.
   - Wählen Sie die Seite `index`
   - Klicken Sie auf **Bearbeiten**.

   ![Bearbeiten der Site im universellen Editor](/help/edge/docs/forms/assets/edit-site.png)
   *Abbildung: Öffnen Ihrer Site zum Bearbeiten*

   Der universelle Editor wird auf einer neuen Registerkarte geöffnet und bietet WYSIWYG-Authoring-Funktionen.

   ![Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/assets/site-in-universal-editor.png)
   *Abbildung: Ihre Site wurde im universellen Editor zur WYSIWYG-Bearbeitung geöffnet*

**Validierung:** Vergewissern Sie sich, dass Ihre AEM-Site zum Erstellen von Formularen bereit ist.

+++

+++Schritt 5: Veröffentlichen Ihrer Site

Durch das Veröffentlichen wird Ihre Site in Edge Delivery Services für globalen Zugriff verfügbar.

1. **Quick Publish über die Sites-Konsole**
   - Kehren Sie zur AEM Sites-Konsole zurück.
   - Wählen Sie die Seiten Ihrer Site aus (oder wählen mit Strg+A alles aus).
   - Klicken Sie auf **Quick Publish**.

   ![Veröffentlichen von AEM-Site](/help/edge/docs/forms/assets/publish-sites.png)
   *Abbildung: Auswählen von Seiten für Quick Publish*

2. **Bestätigen der Veröffentlichung**
   - Klicken Sie im Bestätigungsdialogfeld auf **Veröffentlichen**.

   ![Quick Publish-Dialogfeld](/help/edge/docs/forms/assets/quick-publish.png)
   *Abbildung: Bestätigen der Veröffentlichungsaktion*

   **Alternative** Sie können mit der Schaltfläche „Veröffentlichen“ auch direkt im universellen Editor veröffentlichen.

   ![Veröffentlichen im universellen Editor](/help/edge/docs/forms/assets/qui.png)
   *Abbildung: Direktes Veröffentlichen im universellen Editor*

3. **Zugreifen auf Ihre Live-Site**

   Ihre Website ist jetzt live unter:

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **Erläuterung der URL-Struktur:**
   - `<branch>`: GitHub-Verzweigung (normalerweise `main`)
   - `<repo>`: Ihr Repository-Name
   - `<owner>`: Ihr GitHub-Benutzername oder Ihre Organisation
   - `<site-name>`: Der Name Ihrer AEM-Site

   **Beispiel:**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

**Validierung:** Vergewissern Sie sich, dass Ihre Site in Edge Delivery Services live ist.

>[!TIP]
>
> **URL-Muster:**
>
> - **Startseite:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
> - **Andere Seiten:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<page-name>`

**Weiter:** [Erstellen Ihres ersten Formulars](#create-your-first-form)

+++

## Pfad B: Hinzufügen von Formularen zu vorhandenem Projekt

**Am besten geeignet für:** Vorhandene AEM-Sites mit Edge Delivery Services

Wenn Sie bereits über ein AEM-Projekt mit Edge Delivery Services verfügen, können Sie durch Integration des adaptiven Formularblocks Formularfunktionen hinzufügen.

### Voraussetzungen für Pfad B

Um mit der Integration von Formularen in Ihr bestehendes AEM-Projekt fortzufahren, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Sie haben ein bestehendes AEM-Projekt, das mit dem [AEM-Baustein XWalk](https://github.com/adobe-rnd/aem-boilerplate-xwalk) erstellt wurde.
- Sie haben eine [lokale Entwicklungsumgebung eingerichtet](#set-up-local-development-environment).
- Sie verfügen über Git-Zugriff auf Ihr Projekt-Repository, mit dem Sie Änderungen nach Bedarf klonen, ändern und per Push übertragen können.

>[!NOTE]
>
> Wenn Ihr Projekt ursprünglich mit dem [AEM Forms-Baustein](https://github.com/adobe-rnd/aem-boilerplate-forms) eingerichtet wurde, ist die Formularfunktionalität bereits enthalten. In diesem Fall können Sie mit dem Abschnitt [Erstellen Ihres ersten Formulars](#create-your-first-form) fortfahren.

Das folgende Handbuch bietet einen strukturierten Ansatz zum Hinzufügen von Formularfunktionen zu Ihrem vorhandenen Projekt. Jeder Schritt soll eine für nahtlose Integration und optimale Funktionalität in der universellen Editor-Umgebung sorgen.

### Überblick

Sie werden die folgenden übergeordneten Schritte ausführen:

1. Kopieren Sie die adaptiven Formularblock-Dateien in Ihr Projekt.
2. Aktualisieren Sie die Konfiguration Ihres Projekts, um Formularkomponenten zu erkennen und zu unterstützen.
3. Passen Sie ESLint-Regeln an, um die neuen Dateien und Kodierungsmuster aufzunehmen.
4. Erstellen Sie Ihr Projekt und übertragen Sie die Änderungen in Ihr Repository.

+++Schritt 1: Kopieren von Formularblockdateien

1. **Navigieren Sie zu Ihrem lokalen Projekt.**

   ```bash
   cd /path/to/your/aem-project
   ```

2. **Laden Sie erforderliche Dateien aus dem AEM Forms-Baustein herunter.**

   Kopieren Sie diese Dateien aus dem [AEM Forms-Baustein-Repository](https://github.com/adobe-rnd/aem-boilerplate-forms):

   | Quelle | Ziel | Zweck |
   |------------------------------------------------------------------------|----------------------------|----------------------------|
   | [`blocks/form/`](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) | `blocks/form/` | Zentrale Formularfunktionalität |
   | [`scripts/form-editor-support.js`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) | `scripts/form-editor-support.js` | Integration des universellen Editors |
   | [`scripts/form-editor-support.css`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) | `scripts/form-editor-support.css` | Editor-Formatierung |

3. **Editor-Unterstützung aktualisieren**
   - Ersetzen Sie Ihre `/scripts/editor-support.js`-Datei durch die Datei [editor-support.js aus dem AEM Forms-Baustein](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js).

**Validierung:** Vergewissern Sie sich, dass sich Formularblockdateien in Ihrem Projekt befinden.

+++

+++Schritt 2: Aktualisieren der Komponentenkonfiguration

1. **Aktualisieren von Abschnittsmodell**

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

   **Ergebnis:** Aktiviert Formularkomponenten in der Komponentenauswahl des universellen Editors.

**Validierung:** Vergewissern Sie sich, dass im universellen Editor Formularkomponenten angezeigt werden.

+++

+++Schritt 3: Konfigurieren von ESLint (optional)

**Wozu dient dieser Schritt:** Verhindert Linting-Fehler aus formularspezifischen Dateien und konfiguriert korrekte Validierungsregeln.

1. **Aktualisieren von .eslintignore**

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

   Fügen Sie diese Regeln zum `rules`-Objekt in `/.eslintrc.js` hinzu:

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

**Validierung:** Vergewissern Sie sich, dass ESLint mit Formularkomponenten funktioniert.

+++

+++Schritt 4: Erstellen und Bereitstellen

1. **Installieren von Abhängigkeiten und Aufbauen**

   ```bash
   # Install any new dependencies
   npm install
   
   # Build component definitions
   npm run build:json
   ```

   **Ergebnis:**
   - Aktualisiert `component-definition.json` mit Formularkomponenten
   - Erzeugt `component-models.json` mit Formularmodellen
   - Erstellt `component-filters.json` mit Filterregeln

2. **Überprüfen der generierten Dateien**

   Vergewissern Sie sich, dass diese Dateien im Projektstamm formularbezogene Objekte enthalten:
   - `component-definition.json`
   - `component-models.json`
   - `component-filters.json`

3. **Übermitteln und Übertragen von Änderungen**

   ```bash
   git add .
   git commit -m "Add Adaptive Forms Block integration"
   git push origin main
   ```

**Validierung:** Vergewissern Sie sich, dass Ihr Projekt Formularfunktionen enthält.

+++

**Weiter:** [Erstellen Ihres ersten Formulars](#create-your-first-form)

## Erstellen Ihres ersten Formulars

**Wer diesem Abschnitt folgen sollte:**\
Dieser Abschnitt ist für Benutzende relevant, die entweder Pfad A (neues Projekt) oder Pfad B (vorhandenes Projekt) folgen.

Jetzt, da Ihr Projekt für die Formularerstellung vorbereitet ist, können Sie mit der intuitiven WYSIWYG-Authoring-Umgebung des universellen Editors Ihr erstes Formular erstellen. Die folgenden Schritte stellen einen strukturierten Ansatz für das Entwerfen, Konfigurieren und Veröffentlichen eines Formulars innerhalb Ihrer AEM-Site dar.

### Überblick

Der Prozess der Erstellung eines Formulars im universellen Editor besteht aus mehreren wichtigen Schritten:

1. **Einfügen des adaptiven Formularblocks**\
   Fügen Sie zunächst den adaptiven Formularblock zur ausgewählten Seite hinzu.

2. **Hinzufügen von Formularkomponenten**\
   Füllen Sie Ihr Formular, indem Sie Komponenten wie Textfelder, Schaltflächen und andere Eingabeelemente einfügen.

3. **Konfigurieren von Komponenteneigenschaften**\
   Passen Sie die Einstellungen und Eigenschaften der einzelnen Komponenten an die Anforderungen Ihres Formulars an.

4. **Anzeigen einer Vorschau und Testen Ihres Formulars**\
   Verwenden Sie die Vorschaufunktion, um das Erscheinungsbild und Verhalten Ihres Formulars vor der Veröffentlichung zu überprüfen.

5. **Veröffentlichen der aktualisierten Seite**\
   Wenn Sie zufrieden sind, veröffentlichen Sie Ihre Seite, um das Formular für Endbenutzende verfügbar zu machen.

Die folgenden Abschnitte werden Sie detailliert durch die einzelnen Schritte führen, um eine reibungslose und effektive Formularerstellung sicherzustellen.

+++Schritt 1: Hinzufügen eines adaptiven Formularblocks

1. **Öffnen Ihrer Seite im universellen Editor**
   - Navigieren Sie zur **Sites**-Konsole in AEM.
   - Wählen Sie die Seite aus, auf der Sie ein Formular hinzufügen möchten (z. B. `index`).
   - Klicken Sie auf **Bearbeiten**.

   Ihre Seite wird im universellen Editor zur WYSIWYG-Bearbeitung geöffnet.

2. **Hinzufügen der adaptiven Formularkomponente**
   - Öffnen Sie das Bedienfeld **Inhaltsstruktur** (linke Seitenleiste).
   - Navigieren Sie zu einem Abschnitt, in dem Sie Ihr Formular hinzufügen möchten.
   - Klicken Sie auf das Symbol **Hinzufügen** (+). 
   - Wählen Sie **Adaptives Formular** in der Komponentenliste aus.

   ![Hinzufügen von adaptivem Formularblock](/help/edge/docs/forms/assets/add-adaptive-form-block.png)
   *Abbildung: Hinzufügen eines adaptiven Formularblocks zu Ihrer Seite*

**Validierung** Vergewissern Sie sich, dass Sie einen leeren Formular-Container haben.

+++

+++Schritt 2: Hinzufügen von Formularkomponenten

1. **Navigieren zu Ihrem Formularblock**
   - Suchen Sie in der Inhaltsstruktur den Abschnitt mit dem neu hinzugefügten adaptiven Formular.

   ![Adaptiver Formularblock hinzugefügt](/help/edge/docs/forms/assets/adative-form-block.png)
   *Abbildung: Adaptiver Formularblock in der Inhaltsstruktur*

2. **Hinzufügen von Formularkomponenten**

   Es gibt zwei Möglichkeiten, um Komponenten hinzuzufügen:

   **Methode A: Zum Hinzufügen klicken**
   - Klicken Sie in Ihrem Formularabschnitt auf das Symbol **Hinzufügen** (+).
   - Wählen Sie Komponenten aus der Liste **Adaptive Formularkomponenten**.

   **Methode B: Drag-and-Drop**
   - Ziehen Sie Komponenten direkt aus dem Komponentenfeld in das Formular.

   ![Hinzufügen von Formularkomponenten](/help/edge/docs/forms/assets/add-component.png)
   *Abbildung: Hinzufügen von Komponenten zu Ihrem Formular*

   **Empfohlene Anfangskomponenten:**
   - Texteingabe (für Name, E-Mail)
   - Textbereich (für Nachrichten)
   - Schaltfläche „Senden“

3. **Konfigurieren von Komponenteneigenschaften**
   - Wählen Sie eine beliebige Formularkomponente aus.
   - Verwenden Sie das Bedienfeld **Eigenschaften** (rechte Seitenleiste) zum Konfigurieren von:
      - Beschriftungen und Platzhaltern
      - Validierungsregeln
      - Erforderlichen Feldeinstellungen

   ![Bedienfeld „Komponenteneigenschaften“](/help/edge/docs/forms/assets/component-properties.png)
   *Abbildung: Konfigurieren von Komponenteneigenschaften*

4. **Anzeigen einer Vorschau Ihres Formulars**

   Ihr Formular wird in etwa so aussehen:

   ![Ausgefüllte Formularvorschau](/help/edge/docs/forms/assets/added-form-aem-sites.png)
   *Abbildung: Beispielformular, das mit dem universellen Editor erstellt wurde*

**Validierung:** Vergewissern Sie sich, dass das Formular zur Veröffentlichung bereit ist.

>[!IMPORTANT]
>
> Denken Sie daran, die Seite zu veröffentlichen, nachdem Sie Änderungen vorgenommen haben, damit Aktualisierungen im Browser angezeigt werden.

+++

+++Schritt 3: Veröffentlichen Ihres Formulars

1. **Veröffentlichen im universellen Editor**
   - Klicken Sie im universellen Editor auf die Schaltfläche **Veröffentlichen**.

   ![Veröffentlichen von Formular](/help/edge/docs/forms/assets/publish-form.png)
   *Abbildung: Veröffentlichen Ihres Formulars im universellen Editor*

2. **Bestätigen der Veröffentlichung**
   - Klicken Sie im Bestätigungsdialogfeld auf **Veröffentlichen**.

   ![Veröffentlichungsbestätigung](/help/edge/docs/forms/assets/publish-form1.png)
   *Abbildung: Bestätigen der Veröffentlichungsaktion*

   Sie sehen eine Erfolgsmeldung, in der die Veröffentlichung bestätigt wird.

   ![Erfolgreiche Veröffentlichung](/help/edge/docs/forms/assets/publish-form2.png)
   *Abbildung: Bestätigung der erfolgreichen Veröffentlichung*

3. **Anzeigen Ihres Live-Formulars**

   Ihr Formular ist jetzt live unter:

   ```
   https://<branch>--<repo>--<owner>.aem.live/content/<site-name>/
   ```

   **Beispiel-URL:**

   ```
   https://main--my-forms-project--mycompany.aem.live/content/my-forms-project/
   ```

   ![Live-Formularseite](/help/edge/docs/forms/assets/publish-index-page.png)
   *Abbildung: Ihre veröffentlichte Formularseite in Edge Delivery Services*

**Herzlichen Glückwunsch!** Ihr Formular ist jetzt live und bereit, ausgefüllt und übermittelt zu werden.

+++

### Nächste Schritte

Nachdem Sie nun über ein funktionsfähiges Formular verfügen, können Sie folgende Aufgaben erledigen:

- **Anpassen der Formatierung** durch Bearbeiten von CSS- und JavaScript-Dateien
- **Hinzufügen erweiterter Formularfunktionen**, z. B. Validierungsregeln und bedingte Logik
- **Einrichten einer lokalen Entwicklungsumgebung** für eine schnellere Iteration
- **Erstellen eigenständiger Formulare** für spezifische Anwendungsfälle

>[!TIP]
>
> **Weitere Informationen:** [Erstellen eigenständiger Formulare im universellen Editor](/help/edge/docs/forms/universal-editor/create-forms.md)

## Einrichten einer lokalen Entwicklungsumgebung

**Am besten geeignet für:** Entwicklerinnen und Entwickler, die den Formularstil und das Verhalten anpassen möchten

In einer lokalen Entwicklungsumgebung können Sie Änderungen vornehmen und sofort anzeigen, ohne den Veröffentlichungszyklus durchlaufen zu müssen.

+++Einrichten der AEM-CLI und lokalen Entwicklungsumgebung

1. **Installieren der AEM-CLI**

   Die AEM-CLI vereinfacht lokale Entwicklungsaufgaben:

   ```bash
       npm install -g @adobe/aem-cli
   ```

2. **Klonen Ihres Repositorys**

   ```bash
   git clone https://github.com/<owner>/<repo>
   cd <repo>
   ```

   Ersetzen Sie `<owner>` und `<repo>` durch Ihre tatsächlichen GitHub-Details.

3. **Starten des lokalen Entwicklungs-Servers**

   ```bash
   aem up
   ```

   Dadurch wird ein lokaler Server mit Hot-Reload-Funktionen gestartet.

4. **Vornehmen von Anpassungen**

   - Bearbeiten Sie Dateien im Verzeichnis `blocks/form/` für Formularstile und -verhalten.
   - Ändern Sie `form.css` für Stile.
   - Aktualisieren Sie `form.js` für das Verhalten.

   **Sofortiges Anzeigen von Änderungen** in Ihrem Browser unter `http://localhost:3000`

5. **Bereitstellen Ihrer Änderungen**

   ```bash
   git add .
   git commit -m "Custom form styling"
   git push origin main
   ```

   Ihre Änderungen sind verfügbar unter:
   - **Vorschau:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
   - **Produktion:** `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`

+++


## Fehlerbehebung

### Häufige Probleme und Lösungen

+++Build-Probleme in GitHub

**Problem:** Build-Fehler oder Verknüpfungsfehler

**Lösung 1: Beheben von Linting-Fehlern**

Wenn Sie auf Linting-Fehler stoßen:

1. Öffnen Sie `package.json` in Ihrem Projektstamm.
2. Suchen Sie das `lint`-Skript:

   ```json
   "scripts": {
     "lint": "npm run lint:js && npm run lint:css"
   }
   ```

3. Deaktivieren Sie Linting vorübergehend:

   ```json
   "scripts": {
     "lint": "echo 'skipping linting for now'"
   }
   ```

4. Bestätigen und übermitteln Sie die Änderungen.

**Lösung 2: Fehler im Modulpfad**

Wenn „Der Pfad zum Modul &quot;/scripts/lib-franklin.js&quot; kann nicht aufgelöst werden“ angezeigt wird:

1. Navigieren Sie zu `blocks/form/form.js`
2. Aktualisieren Sie die import-Anweisung:

   ```javascript
   // Change this:
   import { ... } from '/scripts/lib-franklin.js';
   
   // To this:
   import { ... } from '/scripts/aem.js';
   ```

+++

+++Probleme mit der Formularfunktionalität

**Problem:** Formularübermittlungen funktionieren nicht

**Lösungen:**

- Stellen Sie sicher, dass Sie über eine Schaltflächenkomponente zum Senden verfügen.
- Überprüfen Sie die Konfiguration der Formularaktions-URL.
- Überprüfen Sie die Formularvalidierungsregeln.
- Testen Sie zuerst im Vorschaumodus.

**Problem:** Formatierungsprobleme

**Lösungen:**

- Überprüfen Sie CSS-Dateipfade in `blocks/form/`.
- Löschen Sie den Browsercache.
- Überprüfen Sie die CSS-Syntax.
- Testen Sie in der lokalen Entwicklungsumgebung.

+++

+++Probleme mit dem universellen Editor

**Problem:** Formularkomponenten werden im universellen Editor nicht angezeigt

**Lösungen:**

- Überprüfen Sie, ob AEM Code Sync installiert ist und ausgeführt wird.
- Vergewissern Sie sich, dass `fstab.yaml` über die richtige AEM-Autoren-URL verfügt.
- Stellen Sie sicher, dass für Ihre AEM-Instanz der frühzeitige Zugriff aktiviert ist.
- Vergewissern Sie sich, dass `component-definition.json` Formularkomponenten enthält.

**Problem:** Änderungen nach der Veröffentlichung nicht sichtbar

**Lösungen:**

- Warten Sie auf die CDN-Cache-Aktualisierung.
- Prüfen Sie den Browsercache (versuchen Sie es im Inkognito-/privaten Modus).
- Überprüfen Sie, ob das richtige URL-Format verwendet wird.

+++



