---
title: Erstellen und Veröffentlichen von adaptiven Forms mit Edge Delivery Services
description: Schrittweise Anweisungen zum Erstellen, Verfassen und Veröffentlichen von adaptivem Forms mit Kernkomponenten- oder Edge Delivery Services-Vorlagen in AEM, mit Schwerpunkt auf technischer Genauigkeit und Klarheit.
keywords: Adaptive Formulare, Edge-Bereitstellungsdienste, Kernkomponenten, universeller Editor, Formularerstellung, AEM Forms, Vorlagenauswahl, Formularveröffentlichung
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '1774'
ht-degree: 5%

---


# Erstellen und Veröffentlichen von adaptiven Forms mit Edge Delivery Services

Dieses Dokument enthält Anweisungen zum Erstellen, Konfigurieren und Veröffentlichen von Adaptive Forms in AEM mithilfe von Edge Delivery Services. Es behandelt Kernkomponenten- und Edge Delivery Services-Vorlagen.

Am Ende dieses Handbuchs erfahren Sie, wie Sie:

- Wählen Sie den entsprechenden Vorlagentyp für Ihren Anwendungsfall aus
- Erstellen von Formularen mit Kernkomponenten oder Edge Delivery Services-Vorlagen
- Erstellen von Formularen mit dem richtigen Editor
- Konfigurieren und Veröffentlichen von Formularen in Edge Delivery Services
- Zugreifen auf veröffentlichte Formulare und Überprüfen der Bereitstellung

## Vorlagenauswahl

Bevor Sie beginnen, bestimmen Sie, welcher Vorlagentyp Ihren Anforderungen entspricht:

| Kriterien | Kernkomponentenvorlage | Edge Delivery Services-Vorlage |
|-------------------------|-----------------------------------------|-------------------------------------|
| Am besten geeignet für | Unternehmens-Workflows, komplexe Integrationen | Öffentliche Formulare mit hoher Leistung |
| Editor | Editor für adaptive Formulare | Universeller Editor |
| Publishing | AEM-Veröffentlichung + Edge Delivery Services | Nur Edge Delivery Services |
| Komplexität | Erweiterte Formularfunktionen | Optimierte, schnelle Formulare |
| Integration | Vollständiges AEM-Ökosystem | Git-basierte Entwicklung |
| Lernkurve | Vertrautheit der AEM-Anwender | Moderner, vereinfachter Ansatz |

**Entscheidungshilfe:**

![Vorlagenauswahl-Entscheidung](/help/edge/docs/forms/universal-editor/assets/template-selection-decision.svg)

- Verwenden Sie **Kernkomponenten** für komplexe Workflows, eine tief greifende AEM-Integration oder die Nutzung vorhandener AEM-Assets.
- Verwenden Sie **Edge Delivery Services** für Leistung, Einfachheit und moderne Entwicklungsverfahren.


*Entscheidungs-Flussdiagramm für die Auswahl des entsprechenden Vorlagentyps*

## Voraussetzungen

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie fortfahren:

### Technische Anforderungen

- **AEM Forms as a Cloud Service**: Eine aktive Autoreninstanz mit einer Forms-Lizenz.
- **GitHub-**: Persönliches oder organisatorisches Konto für die Repository-Verwaltung.
- **Repository-Setup**: Wählen Sie eine der folgenden Optionen:
   - **Neues Projekt**: [Erstellen eines neuen AEM-Projekts mit dem Adaptive Forms-Block](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block). Das Repository ist für Edge Delivery Services vorkonfiguriert.
   - **Vorhandenes Projekt**: [Hinzufügen eines adaptiven Forms-Blocks zu einem vorhandenen Repository](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) und Aktualisieren der Konfiguration.

### Umgebungskonfiguration

- **AEM-GitHub-**: [Herstellen einer Verbindung](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) zwischen Ihrer AEM-Instanz und dem GitHub-Repository.
- **Edge Delivery Services**: Stellen Sie sicher, dass das Repository für die automatische Bereitstellung konfiguriert ist.
- **Berechtigungen**: Vergewissern Sie sich, dass Sie über die erforderlichen Zugriffsrechte für die Erstellung und Veröffentlichung von Formularen verfügen.

### Validierung einrichten


1. Überprüfen Sie, ob das GitHub-Repository den adaptiven Forms-Block enthält.
2. Testen Sie die Verbindung zwischen AEM und Ihrem GitHub-Repository.
3. Stellen Sie sicher, dass Sie Inhalte in Edge Delivery Services veröffentlichen können.



## Workflow zur Formularerstellung und -veröffentlichung

Der Prozess umfasst drei Hauptphasen:

- **Phase 1:** [Vorlagenauswahl und Formularerstellung](#step-1-template-selection-and-form-creation)
- **Phase 2:** [Formularerstellung und -entwurf](#step-2-form-authoring-and-design)
- **Phase 3:** [Konfiguration und Veröffentlichung](#step-3-configuration-and-publishing)

Jede Phase umfasst Validierungsschritte zur Bestätigung der korrekten Einrichtung.

![Dreistufiger Workflow](/help/edge/docs/forms/universal-editor/assets/three-phase-workflow.svg)
*Überblick über die drei Hauptphasen bei der Erstellung und Veröffentlichung von Formularen*

### Schritt 1: Vorlagenauswahl und Formularerstellung

Wählen Sie den Workflow basierend auf Ihrer Vorlagenauswahl aus:

>[!BEGINTABS]

>[!TAB Edge Delivery Services-Vorlage]

**Anwendungsfall:** Hochleistungsformulare und moderne Entwicklungs-Workflows.

**Funktionen:** Bearbeiten im universellen Editor und Edge Delivery Services-Veröffentlichung.

#### Verfahren

1. **Zugriff auf die Formularerstellung**
   - Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
   - Gehen Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.
   - Klicken Sie auf **Erstellen** > **Adaptive Formulare**.

1. **Vorlage auswählen**
   - Wählen Sie auf der Registerkarte **0}Source** eine **Edge Delivery Services-basierte Vorlage.**
   - Die **Erstellen** wird aktiviert.

     ![Erstellen von EDS-Formularen](/help/edge/assets/create-eds-forms.png)

1. **Optionen konfigurieren (optional)**
   - **Registerkarte „Data Source**: Wählen Sie bei Bedarf die Datenintegration aus.
   - **Registerkarte „Übermittlung**: Wählen Sie eine Übermittlungsaktion aus (kann später konfiguriert werden).
   - **Registerkarte Versand**: Zeitplan für die Veröffentlichung/das Rückgängigmachen der Veröffentlichung festlegen.

1. **Abschließen der Formulareinrichtung**
   - Klicken Sie **Erstellen**, um den Assistenten für die Formularerstellung zu öffnen.
   - Geben Sie Folgendes ein:
      - **Name**: Interne Kennung (keine Leerzeichen, Bindestriche verwenden).
      - **Titel**: Anzeigename für das Formular.
      - **GitHub-**: Repository-URL (z. B. `https://github.com/your-org/your-repo`).

   ![Assistent für die Formularerstellung](/help/edge/assets/create-form-wizard.png)

1. **Validierung**
   - Nachdem Sie auf **Erstellen** geklickt haben, überprüfen Sie:
      - Das Formular wird im universellen Editor geöffnet.
      - Die GitHub-URL ist korrekt verknüpft.
      - Die Komponentenpalette ist verfügbar.
      - Die Arbeitsfläche des Formulars ist sichtbar.

   ![Benutzeroberfläche des universellen Editors](/help/edge/assets/author-form.png)

**Ergebnis:** Das Formular ist für das Authoring im universellen Editor bereit.

>[!TAB Kernkomponentenvorlage]

**Anwendungsfall:** Unternehmens-Workflows und komplexe Integrationen.

**Funktionen:** Authoring mit dem Editor für adaptive Forms, Dual Publishing (AEM + Edge Delivery Services), erweiterte Formularfunktionen.

#### Verfahren

1. **Zugriff auf die Formularerstellung**
   - Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
   - Gehen Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.
   - Klicken Sie auf **Erstellen** > **Adaptive Formulare**.

1. **Vorlage und Design auswählen**
   - Wählen Sie auf der **** Source **eine (Kernkomponentenbasierte Vorlage**.
   - Wählen Sie ein **Design** für die Formatierung aus.
   - Die **Erstellen** wird aktiviert.

   ![Kernkomponenten-Vorlagenauswahl](/help/forms/assets/core-component-based-template.png)

1. **Optionen konfigurieren (optional)**
   - **Registerkarte „Data Source**: Wählen Sie bei Bedarf die Datenintegration aus.
   - **Registerkarte „Übermittlung**: Wählen Sie eine Übermittlungsaktion aus (kann später konfiguriert werden).
   - **Registerkarte Versand**: Zeitplan für die Veröffentlichung/das Rückgängigmachen der Veröffentlichung festlegen.

1. **Abschließen der Formulareinrichtung**
   - Klicken Sie **Erstellen**, um den Assistenten für die Formularerstellung zu öffnen.
   - Geben Sie Folgendes ein:
      - **Name**: Interne Kennung (keine Leerzeichen, Bindestriche verwenden).
      - **Titel**: Anzeigename für das Formular.
      - **Path**: Speicherort im AEM-Repository.

     ![Assistent für die Formularerstellung](/help/forms/assets/create-cc-form.png)

1. **Validierung**
   - Nachdem Sie auf **Erstellen** geklickt haben, überprüfen Sie:
      - Das Formular wird im Editor für adaptive Forms geöffnet.
      - Die Komponenten-Symbolleiste ist verfügbar.
      - Auf das Bedienfeld Eigenschaften kann zugegriffen werden.
      - Design-Stile werden angewendet.

     ![Editor für adaptive Formulare](/help/forms/assets/af-editor-form.png)

**Ergebnis:** Das Formular ist für das Authoring im Editor für adaptive Forms bereit.

>[!ENDTABS]

### Schritt 2: Erstellen und Entwerfen von Formularen

Das Authoring-Erlebnis variiert je nach Vorlage:

- **Edge Delivery Services-Vorlage**: Universeller Editor
- **Kernkomponentenvorlage**: Adaptiver Forms-Editor

![Editor-Vergleich](/help/edge/docs/forms/universal-editor/assets/editor-comparison.svg)
*Vergleich der Funktionen des universellen Editors mit denen des adaptiven Forms-Editors*

>[!BEGINTABS]

>[!TAB Universeller Editor (Edge Delivery Services)]

**Schnittstelle** Moderne, optimierte Bearbeitung für optimale Leistung.

#### Hinzufügen von Formularkomponenten

1. **Zugriff auf die Komponentenbibliothek**
   - Öffnen Sie den Inhaltsbrowser im universellen Editor.
   - Navigieren Sie in **Inhaltsstruktur zur Komponente** Adaptives Formular“.

   ![Navigation in der Inhaltsstruktur](/help/edge/assets/content-tree.png)

1. **Formularfelder hinzufügen**
   - Klicken Sie auf **Hinzufügen**, um die Komponentenbibliothek zu öffnen.
   - Wählen Sie Komponenten in der Liste **Adaptive Formularkomponenten** aus.
   - Ziehen Sie Komponenten per Drag-and-Drop auf die Arbeitsfläche des Formulars.

   ![Komponenten hinzufügen](/help/edge/assets/add-component.png)

1. **Formular entwerfen**
   - Konfigurieren Sie die Feldeigenschaften im Bedienfeld Eigenschaften .
   - Legen Sie Validierungsregeln und -verhalten fest.
*s Passen Sie Stil und Layout nach Bedarf an.

   ![Ausgefülltes Registrierungsformular](/help/edge/assets/contact-us.png)

#### Validierung

- Alle erforderlichen Felder sind vorhanden.
- Feldeigenschaften sind korrekt konfiguriert.
- Layout ist responsiv und barrierefrei.
- Validierungsregeln funktionieren erwartungsgemäß.

#### Nächste Schritte

- [Konfigurieren von Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md) für die Datenverarbeitung.
- [Handbuch zum universellen Editor](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) für erweiterte Funktionen.

>[!TAB Editor für adaptive Forms (Kernkomponenten)]

**Benutzeroberfläche:** Bearbeitung mit vollem Funktionsumfang und erweiterten Formularfunktionen.

#### Hinzufügen von Formularkomponenten

1. **Zugriff auf die Komponentenbibliothek**
   - Klicken Sie im Abschnitt **Komponenten hierher ziehen** auf **Komponente einfügen**.

   ![Bereich zum Einfügen von Komponenten](/help/forms/assets/drag-components-af-editor.png)

2. **Formularfelder hinzufügen**
   - Durchsuchen Sie die **Adaptive Formularkomponenten** Liste.
   - Ziehen Sie die gewünschten Komponenten in das Formular.
   - Verwenden Sie erweiterte Komponenten wie Bedienfelder, Assistenten und Datenintegrationen.

   ![Komponentenbibliothek hinzufügen](/help/forms/assets/add-component-af.png)

3. **Formular entwerfen**
   - Konfigurieren Sie die Feldeigenschaften im Bedienfeld Eigenschaften .
   - Festlegen komplexer Validierungsregeln und Geschäftslogik.
   - Anwenden von Designs und erweiterten Stilen.

   ![Registrierungs-Formular ausgefüllt](/help/forms/assets/af-editor-form.png)

#### Validierung

- Alle erforderlichen Felder sind vorhanden.
- Komplexe Validierungsregeln werden konfiguriert.
- Design-Stile werden angewendet.
- Die Datenintegration funktioniert wie vorgesehen (falls zutreffend).

#### Nächste Schritte

- [Konfigurieren von Übermittlungsaktionen](/help/forms/configure-submit-actions-core-components.md) für erweiterte Workflows.
- [Handbuch zu Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md) für Unternehmensfunktionen.

>[!ENDTABS]

### Schritt 3: Konfiguration und Veröffentlichung

Konfigurieren Sie Edge Delivery Services und veröffentlichen Sie Ihr Formular. Der Prozess unterscheidet sich je nach Vorlagentyp.

#### Edge Delivery Services-Konfiguration

>[!BEGINTABS]
>[!TAB Edge Delivery Services-Vorlage (automatisch)]

**Konfiguration:** (kein manuelles Setup erforderlich).

- Die GitHub-Repository-Verbindung und die Edge Delivery Services-Konfiguration werden während der Formularerstellung erstellt.
- Veröffentlichungsendpunkte werden automatisch konfiguriert.

**Überprüfung:**

- Bestätigen Sie, dass die Konfiguration in den Formulareinstellungen angezeigt wird.
- Stellen Sie sicher, dass die GitHub-URL korrekt verknüpft ist.

![Automatische EDS-Konfiguration](/help/edge/assets/aem-instance-eds-configuration.png)

>[!TAB Kernkomponentenvorlage (manuell)]

**Konfiguration:** manuelles Setup erforderlich.

#### Manuelle Konfigurationsschritte

1. **Zugriffs-Konfigurations-Tools**
   - Navigieren Sie zu **Tools** > **Cloud Services** > **Edge Delivery Services-Konfiguration**.

   ![EDS-Konfigurationszugriff](/help/edge/assets/select-eds-conf.png)

1. **Konfiguration erstellen**
   - Wählen Sie den Ordner aus, der dem Namen Ihres Formulars entspricht (z. B. `forms/enrollment-form`).
   - Klicken Sie **Erstellen** > **Konfiguration**.

   ![Erstellen der EDS-Konfiguration](/help/forms/assets/create-eds-conf.png)

1. **Eigenschaften konfigurieren**
   - Klicken Sie auf **Edge Delivery Services-**.
   - Wählen Sie **Eigenschaften** aus, um das Konfigurationsdialogfeld zu öffnen.

   ![Konfigurationseigenschaften](/help/forms/assets/eds-conf.png)

1. **Parameter festlegen**
   - **Erforderlich:**
      - **Organisation**: GitHub-Organisationsname.
      - **Site-**: GitHub-Repository-Name.
      - **Verzweigung**: Name der Verzweigung (leer lassen für Haupt).
   - **optional:**
      - **Edge-Host**: Standard (wird sowohl auf .page als auch auf .live veröffentlicht).
      - **Site Authentication Token**: Für eine sichere Authentifizierung (falls erforderlich).

1. **Konfiguration speichern**
   - Klicken Sie auf **Speichern und schließen**.

#### Validierung

- Konfiguration wurde erfolgreich erstellt.
- GitHub-Organisation und -Repository sind korrekt angegeben.
- Die Verzweigungseinstellungen stimmen mit der Repository-Struktur überein.
- Das Formular wird im Konfigurationsordner angezeigt.

>[!ENDTABS]

#### Formular veröffentlichen

>[!BEGINTABS]
>[!TAB Veröffentlichung im universellen Editor]

**Für Edge Delivery Services-Vorlagen**

1. Klicken Sie im universellen Editor auf **Veröffentlichen**-Schaltfläche (oben rechts).
2. Bestätigen Sie, dass die Veröffentlichung erfolgreich war, im Dialogfeld.
3. Beachten Sie die generierten URLs für Staging- und Live-Versionen.

   ![Veröffentlichung im universellen Editor](/help/edge/assets/publish-form.png)

- [Veröffentlichungshandbuch](/help/edge/docs/forms/universal-editor/publish-forms.md)

>[!TAB Veröffentlichung des adaptiven Forms-Editors]

1. Wählen Sie in der Experience Manager Forms-Konsole das zu veröffentlichende Formular aus.
2. Klicken **[!UICONTROL in]** Symbolleiste auf „Veröffentlichen“. Überprüfen Sie die zu veröffentlichenden Referenz-Assets.

![Veröffentlichen eines Formulars im Editor für adaptive Formulare](/help/forms/assets/publish-af-editor.png)

>[!NOTE]
>
> Weitere Informationen [ Sie unter „Veröffentlichung in Experience Manager Forms ](/help/forms/manage-publication.md)&quot;.

>[!ENDTABS]

## Formular-URLs

Veröffentlichte Formulare sind über Edge Delivery Services-URLs zugänglich.

### URL-Struktur

- **Gestaffelt (Vorschau/Test):**

  ```
  https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
  ```

- **Live (Produktion):**

  ```
  https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
  ```

#### URL-Parameter

- `<branch>`: Name der GitHub-Verzweigung (z. B. `main`, `develop`)
- `<repo>`: GitHub-Repository-Name (z. B. `my-forms-project`)
- `<owner>`: GitHub-Organisation oder -Benutzername (z. B. `company-name`)
- `<form_name>`: Formularkennzeichnung, wie in AEM definiert (z. B. `contact-us`)

#### Beispiel

Beispiel für Formular-`contact-us` im Repository `forms-project` unter `acme-corp`:

- **Gestaffelt:** `https://main--forms-project--acme-corp.aem.page/content/forms/af/contact-us`
- **Live:** `https://main--forms-project--acme-corp.aem.live/content/forms/af/contact-us`

#### Umgebungsunterschiede

- **Gestaffelt (.page):** Neueste Änderungen zum Testen.
- **Live (.live):** Veröffentlichte Inhalte für die Produktion.

![URL-Struktur](/help/edge/docs/forms/universal-editor/assets/url-structure.svg)
*Aufschlüsselung der URL-Struktur von Edge Delivery Services-Formularen*

#### Visuelle Beispiele

**Edge Delivery Services-Vorlage:**

- Bereitgestellt: ![Registrierungsformular für bereitgestellte Version](/help/forms/assets/registration-form-staged-version.png)
- Live: ![Live-Version des Registrierungsformulars](/help/forms/assets/registration-form-live-version.png)

**Kernkomponentenvorlage:**

- Gestaffelt: ![Registrierungsformular für gestaffelte Version](/help/forms/assets/enrollment-form-staged-version.png)
- Live: ![Live-Version des Registrierungsformulars](/help/forms/assets/enrollment-form-live-version.png)

## Fehlerbehebung

Im Folgenden finden Sie häufige Probleme und Lösungen für AEM Forms mit Edge Delivery Services.

+++Formular wird nicht geladen

**Problem:** Formular-URL gibt 404 oder eine leere Seite zurück.

**Auflösung:**

- Entfernen Sie `.html` Erweiterung aus URLs.
- Überprüfen Sie, ob das Formular veröffentlicht wurde.
- Überprüfen Sie das GitHub-Repository für den adaptiven Forms-Block.
- Stellen Sie sicher, dass der Formularname mit der URL übereinstimmt (Groß-/Kleinschreibung beachten).

+++

+++Konfigurationsprobleme

**Problem:** Edge Delivery Services-Konfiguration funktioniert nicht.

**Auflösung:**

- Stellen Sie sicher, dass die GitHub-URL `https://github.com/owner/repository` Format vorliegt.
- Verwenden Sie den richtigen Verzweigungsnamen in der Konfiguration.
- Überprüfen Sie den Repository-Zugriff (öffentlich oder authentifiziert).
- Überprüfen Sie die `fstab.yaml` auf korrekte GitHub-Details.

+++

+++Veröffentlichungsprobleme

**Problem:** Änderungen werden nicht auf der Live-Site angezeigt.

**Auflösung:**

- Warten Sie 2-3 Minuten auf die Aktualisierung des CDN-Cache.
- Bestätigen Sie, dass der Veröffentlichungs-Workflow abgeschlossen ist.
- Testen Sie zuerst in der Staging-Umgebung (.page).
- Stellen Sie sicher, dass das GitHub-Repository aktualisiert wird.

+++

+++Probleme mit dem universellen Editor

**Problem:** Formular kann nicht bearbeitet werden oder Komponenten werden nicht geladen.

**Auflösung:**

- Verwenden Sie einen unterstützten Browser (Chrome, Firefox, Safari).
- Leeren Sie den Browser-Cache und löschen Sie Cookies.
- Überprüfen Sie die Netzwerkverbindung.
- Autorenberechtigungen bestätigen.

+++

+++Fehler bei der Formularübermittlung

**Problem:** Formularübermittlungen funktionieren nicht.

**Auflösung:**

- Konfigurieren Sie die Übermittlungsaktion in den Formulareigenschaften.
- Übermittlungsendpunkte manuell testen.
- Überprüfen Sie die CORS-Einstellungen beim Einbetten von Formularen.
- Überprüfen Sie, ob die erforderlichen Felder konfiguriert sind.

+++

+++Leistungsprobleme

**Problem** Langsames Laden von Formularen oder schlechte Leistung.

**Auflösung:**

- Optimieren von Bildern.
- Entfernen Sie unnötige Komponenten.
- Edge Delivery Services CDN nutzen.
- Benutzerdefinierte JavaScript/CSS minimieren.

+++

+++Hilfe anfordern

Wenn die Probleme bestehen bleiben:

1. Überprüfen Sie den Status des Adobe Experience Cloud-Service.
2. Lesen Sie die [Dokumentation zu Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=de).
3. Besuchen Sie [Adobe Experience League-Community](https://experienceleaguecommunities.adobe.com/).
4. Adobe-Kundenunterstützung kontaktieren.

+++

## Nächste Schritte

Beachten Sie nach Abschluss der Formularerstellung und -veröffentlichung Folgendes:

### Sofortige Aktionen

- Testen Sie Ihr Formular mit diesem Handbuch.
- Überprüfen Sie Ihr GitHub-Repository und Ihre AEM-Verbindung.
- Beispielformulare überprüfen.

### Fortgeschrittene Themen

- [Konfigurieren von Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md): Richten Sie die Datenverarbeitung und Integrationen ein.
- [Formulardatenmodelle](/help/forms/create-form-data-models.md): Verbinden von Formularen mit Backend-Datenquellen.

### Leistungsoptimierung

- [Best Practices für Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=de): Maximieren Sie die Leistung.
- [Formularanalyse](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/analytics.html): Verfolgen Sie die Formularleistung und das Benutzerverhalten.

