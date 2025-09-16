---
title: Erstellen und Veröffentlichen von adaptiven Formularen mit Edge Delivery Services
description: Schrittweise Anleitungen zum Erstellen, Verfassen und Veröffentlichen adaptiver Formulare mit Edge Delivery Services-Vorlagen in AEM, wobei der Schwerpunkt auf technischer Genauigkeit und Klarheit liegt.
keywords: adaptive Formulare, Edge Delivery Services, universeller Editor, Formularerstellung, AEM Forms, Formularveröffentlichung
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 07160248d5b5817d155a118475878ce04a687a32
workflow-type: ht
source-wordcount: '1005'
ht-degree: 100%

---


# Erstellen und Veröffentlichen von adaptiven Formularen mit Edge Delivery Services

Dieses Dokument enthält schrittweise Anweisungen zum Erstellen, Konfigurieren und Veröffentlichen von adaptiven Formularen mithilfe von Edge Delivery Services-Vorlagen in AEM. Es umfasst den gesamten Workflow von der Erstellung von Formularen bis zur Bereitstellung in der Produktion.

Am Ende dieses Handbuchs haben Sie Folgendes gelernt:

- Erstellen von Formularen mit Edge Delivery Services-Vorlagen
- Erstellen von Formularen mit dem universellen Editor
- Konfigurieren und Veröffentlichen von Formularen in Edge Delivery Services
- Zugreifen auf veröffentlichte Formulare und Überprüfen der Bereitstellung



## Voraussetzungen

Stellen Sie sicher, dass folgende Voraussetzungen erfüllt sind, bevor Sie fortfahren:


- **AEM Forms as a Cloud Service**: Eine aktive Autoreninstanz mit einer Forms-Lizenz.
- **GitHub-Konto**: Persönliches oder geschäftliches Konto für die Repository-Verwaltung.
- **Repository-Setup**: Wählen Sie eine der folgenden Optionen:
   - **Neues Projekt**: [Erstellen Sie ein neues AEM-Projekt mit dem adaptiven Formularblock](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block). Das Repository ist für Edge Delivery Services vorkonfiguriert.
   - **Vorhandenes Projekt**: [Fügen Sie einen adaptiven Formularblock zu einem vorhandenen Repository hinzu](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) und aktualisieren Sie die Konfiguration.

- **AEM-GitHub-Verbindung**: [Stellen Sie eine Verbindung](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) zwischen Ihrer AEM-Instanz und dem GitHub-Repository her.
- **Edge Delivery Services**: Stellen Sie sicher, dass das Repository für die automatische Bereitstellung konfiguriert ist.
- **Berechtigungen**: Vergewissern Sie sich, dass Sie über die erforderlichen Zugriffsrechte für die Erstellung und Veröffentlichung von Formularen verfügen.

- Überprüfen Sie, ob das GitHub-Repository den adaptiven Formularblock enthält.



## Workflow zur Erstellung und Veröffentlichung von Formularen

Der Prozess umfasst drei Hauptphasen:

- **Phase 1:** [Formulareinrichtung](#step-1-form-creation)
- **Phase 2:** [Formularerstellung und -gestaltung](#step-2-form-authoring-and-design)
- **Phase 3:** [Konfiguration und Veröffentlichung](#step-3-configuration-and-publishing)

Jede Phase umfasst Validierungsschritte zur Bestätigung der korrekten Einrichtung.


### Schritt 1: Formulareinrichtung

1. **Aufrufen der Formulareinrichtung**
   - Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
   - Gehen Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.
   - Klicken Sie auf **Erstellen** > **Adaptive Formulare**.

1. **Auswählen der Vorlage**
   - Wählen Sie auf der Registerkarte **Quelle** eine **Edge Delivery Services-basierte Vorlage** aus.
   - Die Schaltfläche **Erstellen** wird aktiviert.

     ![Erstellen von EDS-Formularen](/help/edge/assets/create-eds-forms.png)

1. **Konfigurieren von Optionen (optional)**
   - **Registerkarte „Datenquelle“**: Wählen Sie bei Bedarf Datenintegration aus.
   - **Registerkarte „Übermittlung“**: Wählen Sie eine Übermittlungsaktion aus (kann später konfiguriert werden).
   - **Registerkarte „Bereitstellung“**: Legen Sie einen Zeitplan für die Veröffentlichung/das Aufheben der Veröffentlichung fest.

1. **Abschließen der Formulareinrichtung**
   - Klicken Sie auf **Erstellen**, um den Assistenten für die Formularerstellung zu öffnen.
   - Geben Sie Folgendes ein:
      - **Name**: Interne Kennung (keine Leerzeichen, stattdessen Bindestriche verwenden).
      - **Titel**: Der Anzeigename für Ihr Formular.
      - **GitHub-URL**: Repository-URL (z. B. `https://github.com/your-org/your-repo`).

   ![Assistent für die Formularerstellung](/help/edge/assets/create-form-wizard.png)

1. **Validierung**
   - Nachdem Sie auf **Erstellen** geklickt haben, überprüfen Sie folgende Aspekte:
      - Das Formular lässt sich im universellen Editor öffnen. 
      - Die GitHub-URL ist korrekt verknüpft.
      - Die Komponentenpalette ist verfügbar.
      - Die Arbeitsfläche des Formulars ist sichtbar.

   ![Benutzeroberfläche des universellen Editors](/help/edge/assets/author-form.png)

**Ergebnis:** Das Formular ist für das Authoring im universellen Editor bereit.

### Schritt 2: Erstellen und Gestalten von Formularen


1. **Aufrufen der Komponentenbibliothek**
   - Öffnen Sie den Inhalts-Browser im universellen Editor.
   - Navigieren Sie in der Inhaltsstruktur zur Komponente **Adaptives Formular**.

   ![Navigation in der Inhaltsstruktur](/help/edge/assets/content-tree.png)

1. **Hinzufügen von Formularfeldern**
   - Klicken Sie auf das Symbol **Hinzufügen**, um die Komponentenbibliothek zu öffnen. 
   - Wählen Sie Komponenten aus der Liste **Adaptive Formularkomponenten**.
   - Ziehen Sie Komponenten per Drag-and-Drop auf die Arbeitsfläche des Formulars.

   ![Hinzufügen von Komponenten](/help/edge/assets/add-component.png)

1. **Gestalten des Formulars**
   - Konfigurieren Sie die Feldeigenschaften im Bedienfeld „Eigenschaften“.
   - Legen Sie Validierungsregeln und -verhalten fest.
   - Passen Sie Stil und Layout nach Bedarf an.

   ![Ausgefülltes Registrierungsformular](/help/edge/assets/contact-us.png)

#### Validierung

- Alle erforderlichen Felder sind vorhanden.
- Feldeigenschaften sind korrekt konfiguriert.
- Layout ist responsiv und zugänglich.
- Validierungsregeln funktionieren erwartungsgemäß.

#### Nächste Schritte

- [Konfigurieren von Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md) für die Datenverarbeitung.
- [Handbuch zum universellen Editor](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) für erweiterte Funktionen.

### Schritt 3: Konfiguration und Veröffentlichung

Konfigurieren Sie Edge Delivery Services und veröffentlichen Sie Ihr Formular. 

**Konfiguration:** automatisch (kein manuelles Setup erforderlich).

- Die Verbindung zum GitHub-Repository sowie die Edge Delivery Services-Konfiguration werden während der Formularerstellung eingerichtet.
- Veröffentlichungsendpunkte werden automatisch konfiguriert.

**Verifizierung:**

- Vergewissern Sie sich, dass die Konfiguration in den Formulareinstellungen angezeigt wird.
- Stellen Sie sicher, dass die GitHub-URL korrekt verlinkt ist.

![Automatische EDS-Konfiguration](/help/edge/assets/aem-instance-eds-configuration.png)

#### Veröffentlichen des Formulars

1. Klicken Sie im universellen Editor auf die Schaltfläche **Veröffentlichen** (oben rechts).
2. Vergewissern Sie sich im Dialogfeld, dass die Veröffentlichung erfolgreich war.
3. Beachten Sie die generierten URLs für Staging- und Live-Versionen.

   ![Veröffentlichen im universellen Editor](/help/edge/assets/publish-form.png)

- [Handbuch für die Veröffentlichung](/help/edge/docs/forms/universal-editor/publish-forms.md)

## Formular-URLs

Veröffentlichte Formulare sind über Edge Delivery Services-URLs aufrufbar.

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
- `<repo>`: Name des GitHub-Repositorys (z. B. `my-forms-project`)
- `<owner>`: GitHub-Organisation oder -Benutzername (z. B. `company-name`)
- `<form_name>`: Formularkennung, wie in AEM definiert (z. B. `contact-us`)

#### Beispiel

Beispiel für Formular `contact-us` in Repository `forms-project` unter Organisation `acme-corp`:

- **Gestaffelt:** `https://main--forms-project--acme-corp.aem.page/content/forms/af/contact-us`
- **Live:** `https://main--forms-project--acme-corp.aem.live/content/forms/af/contact-us`

#### Umgebungsunterschiede

- **Gestaffelt (.page):** Neueste Änderungen zum Testen.
- **Live (.live):** Veröffentlichte Inhalte für die Produktion.

![URL-Struktur](/help/edge/docs/forms/universal-editor/assets/url-structure.svg)
*Aufschlüsselung der URL-Struktur von Edge Delivery Services-Formularen*

#### Visuelle Beispiele

**Edge Delivery Services-Vorlage:**

- Gestaffelt: ![Gestaffelte Version des Registrierungsformulars](/help/forms/assets/registration-form-staged-version.png)
- Live: ![Live-Version des Registrierungsformulars](/help/forms/assets/registration-form-live-version.png)

## Fehlerbehebung

Im Folgenden finden Sie häufige Probleme und Lösungen für AEM Forms mit Edge Delivery Services.

+++Formular wird nicht geladen

**Problem:** Formular-URL gibt 404 oder eine leere Seite zurück.

**Auflösung:**

- Entfernen Sie die Erweiterung `.html` aus URLs.
- Überprüfen Sie, ob das Formular veröffentlicht wurde.
- Prüfen Sie das GitHub-Repository auf den adaptiven Formularblock.
- Stellen Sie sicher, dass der Formularname mit der URL übereinstimmt (Groß-/Kleinschreibung beachten).

+++

+++Konfigurationsprobleme

**Problem:** Edge Delivery Services-Konfiguration funktioniert nicht.

**Auflösung:**

- Stellen Sie sicher, dass die GitHub-URL im Format `https://github.com/owner/repository` vorliegt.
- Verwenden Sie den richtigen Verzweigungsnamen in der Konfiguration.
- Überprüfen Sie den Repository-Zugriff (öffentlich oder authentifiziert).
- Prüfen Sie `fstab.yaml` auf korrekte GitHub-Details.

+++

+++Probleme bei der Veröffentlichung

**Problem** Änderungen werden nicht auf der Live-Site angezeigt.

**Auflösung:**

- Warten Sie 2-3 Minuten, bis der CDN-Cache aktualisiert wurde.
- Vergewissern Sie sich, dass der Veröffentlichungs-Workflow abgeschlossen wurde.
- Testen Sie zuerst in der gestaffelten Umgebung (.page).
- Stellen Sie sicher, dass das GitHub-Repository aktualisiert wurde.

+++

+++Probleme mit dem universellen Editor

**Problem:** Formular kann nicht bearbeitet werden oder Komponenten werden nicht geladen.

**Auflösung:**

- Verwenden Sie einen unterstützten Browser (Chrome, Firefox, Safari).
- Leeren Sie den Browsercache und löschen Sie Cookies.
- Überprüfen Sie die Netzwerkverbindung.
- Überprüfen Sie Autorenberechtigungen.

+++

+++Fehler bei der Formularübermittlung

**Problem:** Formularübermittlungen funktionieren nicht.

**Auflösung:**

- Konfigurieren Sie die Übermittlungsaktion in den Formulareigenschaften.
- Testen Sie Übermittlungsendpunkte manuell.
- Überprüfen Sie die CORS-Einstellungen, wenn Sie Formulare einbetten.
- Überprüfen Sie, ob die erforderlichen Felder konfiguriert sind.

+++

+++Leistungsprobleme

**Problem:** Langsames Laden von Formularen oder mangelhafte Leistung.

**Auflösung:**

- Optimieren Sie Bilder.
- Entfernen Sie unnötige Komponenten.
- Nutzen Sie das Edge Delivery Services-CDN.
- Minimieren Sie benutzerdefiniertes JavaScript/CSS.

+++

+++Hilfe

Wenn die Probleme bestehen bleiben:

1. Überprüfen Sie den Dienststatus von Adobe Experience Cloud.
2. Lesen Sie die [Dokumentation zu Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=de).
3. Besuchen Sie die [Adobe Experience League-Community](https://experienceleaguecommunities.adobe.com/?profile.language=de).
4. Wenden Sie sich an die Adobe-Kundenunterstützung.

+++

## Nächste Schritte

Beachten Sie nach Abschluss der Formularerstellung und -veröffentlichung folgende Aspekte:

- [Konfigurieren von Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md): Einrichten von Datenverarbeitung und Integrationen.
- [Formulardatenmodelle](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md): Verbinden von Formularen mit Backend-Datenquellen.
- [Best Practices für Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=de): Maximieren der Leistung.
- [Formularanalyse](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/analytics.html?lang=de): Verfolgen der Formularleistung und des Benutzerverhaltens.

