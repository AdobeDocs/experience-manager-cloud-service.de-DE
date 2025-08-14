---
title: Erstellen und Veröffentlichen von adaptiven Forms mit Edge Delivery Services
description: Schrittweise Anweisungen zum Erstellen, Verfassen und Veröffentlichen von adaptivem Forms mithilfe von Edge Delivery Services-Vorlagen in AEM, mit Schwerpunkt auf technischer Genauigkeit und Klarheit.
keywords: Adaptive Formulare, Edge-Bereitstellungsdienste, universeller Editor, Formularerstellung, AEM Forms, Formularveröffentlichung
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 07160248d5b5817d155a118475878ce04a687a32
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 4%

---


# Erstellen und Veröffentlichen von adaptiven Forms mit Edge Delivery Services

Dieses Dokument enthält schrittweise Anweisungen zum Erstellen, Konfigurieren und Veröffentlichen von adaptivem Forms mithilfe von Edge Delivery Services-Vorlagen in AEM. Sie umfasst den gesamten Workflow von der Formularerstellung bis zur Produktionsbereitstellung.

Am Ende dieses Handbuchs erfahren Sie, wie Sie:

- Erstellen von Formularen mit Edge Delivery Services-Vorlagen
- Erstellen von Formularen mit dem universellen Editor
- Konfigurieren und Veröffentlichen von Formularen in Edge Delivery Services
- Zugreifen auf veröffentlichte Formulare und Überprüfen der Bereitstellung



## Voraussetzungen

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie fortfahren:


- **AEM Forms as a Cloud Service**: Eine aktive Autoreninstanz mit einer Forms-Lizenz.
- **GitHub-**: Persönliches oder organisatorisches Konto für die Repository-Verwaltung.
- **Repository-Setup**: Wählen Sie eine der folgenden Optionen:
   - **Neues Projekt**: [Erstellen eines neuen AEM-Projekts mit dem Adaptive Forms-Block](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block). Das Repository ist für Edge Delivery Services vorkonfiguriert.
   - **Vorhandenes Projekt**: [Hinzufügen eines adaptiven Forms-Blocks zu einem vorhandenen Repository](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) und Aktualisieren der Konfiguration.

- **AEM-GitHub-**: [Herstellen einer Verbindung](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) zwischen Ihrer AEM-Instanz und dem GitHub-Repository.
- **Edge Delivery Services**: Stellen Sie sicher, dass das Repository für die automatische Bereitstellung konfiguriert ist.
- **Berechtigungen**: Vergewissern Sie sich, dass Sie über die erforderlichen Zugriffsrechte für die Erstellung und Veröffentlichung von Formularen verfügen.

- Überprüfen Sie, ob das GitHub-Repository den adaptiven Forms-Block enthält.



## Workflow zur Formularerstellung und -veröffentlichung

Der Prozess umfasst drei Hauptphasen:

- **Phase 1:** [Formularerstellung](#step-1-form-creation)
- **Phase 2:** [Formularerstellung und -entwurf](#step-2-form-authoring-and-design)
- **Phase 3:** [Konfiguration und Veröffentlichung](#step-3-configuration-and-publishing)

Jede Phase umfasst Validierungsschritte zur Bestätigung der korrekten Einrichtung.


### Schritt 1: Formularerstellung

1. **Zugriff auf die Formularerstellung**
   - Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
   - Gehen Sie zu **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**.
   - Klicken Sie auf **Erstellen** > **Adaptive Formulare**.

1. **Vorlage auswählen**
   - Wählen Sie auf der Registerkarte **0&rbrace;Source** eine **Edge Delivery Services-basierte Vorlage.**
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

### Schritt 2: Erstellen und Entwerfen von Formularen


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
   - Passen Sie Stil und Layout nach Bedarf an.

   ![Ausgefülltes Registrierungsformular](/help/edge/assets/contact-us.png)

#### Validierung

- Alle erforderlichen Felder sind vorhanden.
- Feldeigenschaften sind korrekt konfiguriert.
- Layout ist responsiv und barrierefrei.
- Validierungsregeln funktionieren erwartungsgemäß.

#### Nächste Schritte

- [Konfigurieren von Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md) für die Datenverarbeitung.
- [Handbuch zum universellen Editor](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) für erweiterte Funktionen.

### Schritt 3: Konfiguration und Veröffentlichung

Konfigurieren Sie Edge Delivery Services und veröffentlichen Sie Ihr Formular.

**Konfiguration:** (kein manuelles Setup erforderlich).

- Die GitHub-Repository-Verbindung und die Edge Delivery Services-Konfiguration werden während der Formularerstellung erstellt.
- Veröffentlichungsendpunkte werden automatisch konfiguriert.

**Überprüfung:**

- Bestätigen Sie, dass die Konfiguration in den Formulareinstellungen angezeigt wird.
- Stellen Sie sicher, dass die GitHub-URL korrekt verknüpft ist.

![Automatische EDS-Konfiguration](/help/edge/assets/aem-instance-eds-configuration.png)

#### Formular veröffentlichen

1. Klicken Sie im universellen Editor auf **Veröffentlichen**-Schaltfläche (oben rechts).
2. Bestätigen Sie, dass die Veröffentlichung erfolgreich war, im Dialogfeld.
3. Beachten Sie die generierten URLs für Staging- und Live-Versionen.

   ![Veröffentlichung im universellen Editor](/help/edge/assets/publish-form.png)

- [Veröffentlichungshandbuch](/help/edge/docs/forms/universal-editor/publish-forms.md)

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

+++Hilfe

Wenn die Probleme bestehen bleiben:

1. Überprüfen Sie den Status des Adobe Experience Cloud-Service.
2. Lesen Sie die [Dokumentation zu Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=de).
3. Besuchen Sie [Adobe Experience League-Community](https://experienceleaguecommunities.adobe.com/?profile.language=de).
4. Adobe-Kundenunterstützung kontaktieren.

+++

## Nächste Schritte

Beachten Sie nach Abschluss der Formularerstellung und -veröffentlichung Folgendes:

- [Konfigurieren von Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md): Richten Sie die Datenverarbeitung und Integrationen ein.
- [Formulardatenmodelle](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md): Verbinden von Formularen mit Backend-Datenquellen.
- [Best Practices für Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=de): Maximieren Sie die Leistung.
- [Formularanalyse](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/analytics.html): Verfolgen Sie die Formularleistung und das Benutzerverhalten.

