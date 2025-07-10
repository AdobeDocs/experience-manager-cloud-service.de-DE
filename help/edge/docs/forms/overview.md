---
title: Überblick über Edge Delivery Services für AEM Forms
description: Edge Delivery Services für AEM Forms wurde für Spitzenleistung entwickelt und ermöglicht es Ihnen, sich die Zukunft der optimierten Datenerfassung und Benutzerinteraktion vorzustellen.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 67fe933807f8a1bca681a6bcee7164f7c117bcac
workflow-type: tm+mt
source-wordcount: '1874'
ht-degree: 7%

---


# Erste Schritte mit Forms in AEM Edge Delivery Services

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unseren [Vorabveröffentlichungskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features) zugegriffen werden kann. </span>

Dieses Handbuch hilft Ihnen, Formulare mit Adobe Experience Manager (AEM) Edge Delivery Services (EDS) zu verstehen und zu implementieren. Unabhängig davon, ob Sie ein einfaches Kontaktformular oder ein komplexes Datenerfassungs-Tool erstellen, führt Sie diese Seite durch Ihre Optionen.

## Grundlegendes zu Forms in Edge Delivery Services

Edge Delivery Services ist Adobes moderne Lösung für die Bereitstellung von Web-Inhalten, einschließlich Formularen, mit außergewöhnlicher Leistung und Agilität. Durch die Verwendung von Edge Delivery Services für Ihre Formulare können Sie:

* **Schnellere Erlebnisse bereitstellen:** Forms wird unglaublich schnell geladen, da sie von einem globalen Netzwerk von Edge-Servern (CDNs) in der Nähe Ihrer Benutzer bereitgestellt werden. Dies verbessert die Benutzerzufriedenheit und kann die Formularabschlussraten erhöhen.
* **Einfaches Aktualisieren von Forms:** Der Edge Delivery Services-Ansatz ermöglicht häufig schnellere Entwicklungszyklen und Inhaltsaktualisierungen, sodass Sie Ihre Formulare schnell anpassen können.
* **Modernes, responsives Forms erstellen** Erstellen Sie Formulare, die großartig aussehen und nahtlos auf jedem Gerät funktionieren.
* **Profitieren Sie von Skalierbarkeit und Zuverlässigkeit:** Ihre Formulare sind so robust und skalierbar wie die zugrunde liegende Edge-Infrastruktur.

In diesem Handbuch wird Folgendes erläutert:

* Erläutern Sie die verschiedenen Möglichkeiten zum Erstellen (Verfassen) von Formularen für Ihre Edge Delivery Sites.
* Erfahren Sie, wie Sie konfigurieren können, was passiert, nachdem ein Benutzer ein Formular sendet (Übermittlungsaktionen).
* Helfen Sie bei der Auswahl der besten Methoden für Ihre spezifischen Bedürfnisse und Team-Fähigkeiten.
* Bereitstellen von Architekturdiagrammen und Best Practices.

## Wichtige Begriffe, die Sie kennen sollten

* **Edge Delivery Services (EDS):** Adobes Performance-First-Architektur für die Bereitstellung von AEM-Inhalten über CDNs. Auch bekannt als Project Franklin.
* **AEM Forms:** Adobes Lösung zum Erstellen, Verwalten und Verarbeiten von Formularen.
* **Universeller Editor (UE):** Ein visueller WYSIWYG-Editor für AEM-Inhalte, einschließlich Formularen.
* **Dokumentenbasiertes Authoring:** Erstellen von Formularen mit Microsoft Word oder Google Docs/Sheets.
* **Dokumenterstellung (Document Authoring, DA):** Ein von Adobe gehosteter Dienst für das Erstellen von Inhalten (einschließlich Seiten, auf denen Formulare gehostet werden können) für Edge Delivery Services.
* **Forms Submission Service (FSS):** Ein Adobe-Service, der das Senden von Formulardaten an Tabellen oder E-Mails vereinfacht.
* **AEM-Veröffentlichungsinstanz:** Die Live-AEM-Umgebung, die komplexe Formularübermittlungen verarbeiten kann.
* **CORS (Cross-Origin Resource Sharing):** Eine Browser-Sicherheitsfunktion, die beim Einbetten von Formularen aus verschiedenen Domains konfiguriert werden muss.
* **CDN (Content Delivery Network):** Ein Netzwerk von Servern, das Benutzern je nach geografischem Standort schnell Web-Inhalte bereitstellt.


**Konzeptdiagramm für Edge Delivery Services Form Interaction**

<!--  
```mermaid
graph LR
    User[User on Device] >|Interacts| EdgeForm[Edge-Delivered Form Page]
    EdgeForm >|Loads Instantly| CDN[CDN Edge Server]
    CDN >|Serves Content| User
    EdgeForm >|Submits Data| Backend[Backend Processing - e.g. Forms Submission Service / AEM Publish]
    style User fill:#f9f,stroke:#333,stroke-width:2px
    style EdgeForm fill:#ccf,stroke:#333,stroke-width:2px
    style CDN fill:#9cf,stroke:#333,stroke-width:2px
    style Backend fill:#fca,stroke:#333,stroke-width:2px
``` -->

![Form Interaction](/help/forms/assets/eds-form-interaction.png)
Dieses Diagramm zeigt einen Benutzer, der mit einem Formular interagiert, das schnell über ein CDN bereitgestellt wird. Die von ihnen übermittelten Daten werden dann von einem Backend-System verarbeitet.

## Wie funktioniert Forms in Edge?

Mit EDS können Ihre Website-Inhalte (einschließlich der Struktur Ihrer Formulare) aus verschiedenen Quellen wie AEM as a Cloud Service, SharePoint, Google Drive oder dem Document Authoring (DA)-Service stammen. Diese Inhalte werden dann in einem globalen CDN veröffentlicht. Wenn ein Benutzer Ihre Site besucht, werden die Inhalte direkt vom nächsten CDN-Edge-Server bereitgestellt, was eine maximale Geschwindigkeit gewährleistet.

<!--*   **Where AEM Forms Fit In**
    Forms in an EDS architecture are designed to be:
    *   **Fast Loading:** Form structures are often simple HTML rendered client-side.
    *   **Decoupled:** The visual part of the form (frontend) is separate from where the data goes after submission (backend).
    *   **Flexible to Create:** You have different tools to build your forms.
    *   **Configurable for Submission:** You can send data to simple services or powerful AEM backends.-->

**Vereinfachte Edge Delivery Services-Architektur mit Forms**

<!--
```mermaid
    graph TD
        UserStart[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User on Device] >|Interacts| EdgeForm[Edge-Delivered Form Page]
        EdgeForm >|Loads Instantly| CDN[CDN Edge Server]
        CDN >|Serves Content| UserEnd[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User on Device]
        EdgeForm >|Submits Data| Backend[Backend Processing - Form Submission Service / AEM Publish]

        style UserStart fill:#f9f,stroke:#333,stroke-width:2px
        style UserEnd fill:#f9f,stroke:#333,stroke-width:2px
        style EdgeForm fill:#ccf,stroke:#333,stroke-width:2px
        style CDN fill:#9cf,stroke:#333,stroke-width:2px
        style Backend fill:#fca,stroke:#333,stroke-width:2px
``` -->

![Architektur](/help/forms/assets/eds-simplified-architecture.png)
Dieses Diagramm zeigt die Journey: Formulare werden in einem Autorensystem definiert, in Edge veröffentlicht, für Benutzer bereitgestellt und gesendete Daten werden von einem Backend verarbeitet.

## Auswählen der Authoring-Methode für ein Formular

Sie haben drei Möglichkeiten, Formulare für Ihre Edge Delivery Services-Sites zu erstellen. Ihre Auswahl hängt von den Fähigkeiten Ihres Teams, der Komplexität des Formulars und Ihren Projektanforderungen ab.

### Welcher Authoring-Ansatz ist der richtige für Sie?

Verwenden Sie diesen Entscheidungsbaum für folgende Auswahlmöglichkeiten:

**Entscheidungsbaum für die Formularerstellung**
<!--    
```mermaid
    graph TD
        A{Start: I need to create a form for an Edge Delivery Services site} > B{What are my team's primary content creation tools & skills?}
        B -- "We mainly use Word / Google Docs / Sheets" > C{How complex is the form and where does the data need to go?}
        B -- "We use AEM and prefer visual tools (Marketers or Designers)" > D[Use Universal Editor - WYSIWYG]
        B -- "Our site content is managed in Document Authoring (DA)" > E[Use Document Authoring - Embed Forms]
        C -- "Simple to moderate form, data to a spreadsheet or email" > F[Use Document-Based Authoring]
        C -- "More complex logic or needs AEM backend integration" > D
        E > G[Create form using Document-Based Authoring or Universal Editor, then embed in your DA page]

        style A fill:#f9f,stroke:#333,stroke-width:2px
        style F fill:#ccf,stroke:#333,stroke-width:2px
        style D fill:#ccf,stroke:#333,stroke-width:2px
        style G fill:#ccf,stroke:#333,stroke-width:2px
``` -->

![Auswählen der richtigen Plattform](/help/forms/assets/eds-authoring-selection.png)

Dieser Entscheidungsbaum hilft Ihnen bei der Auswahl einer Authoring-Methode basierend auf Ihren Team- und Formularanforderungen.

### Erstellen von Forms mit Dokumenten (Word/Google Docs)

Diese Methode eignet sich hervorragend zum schnellen [ (Erstellen von Formularen, wenn Ihr Team mit Microsoft Word oder Google Docs/Sheets vertraut ist](/help/edge/docs/forms/create-forms.md).

**Funktionsweise: Vom Dokument zum Web-Formular**

Sie definieren die Felder, Beschriftungen und Typen Ihres Formulars direkt in einem Word-Dokument oder einer Google-Tabelle mithilfe eines speziellen Tabellenformats oder eines „Formularblocks“. Wenn Sie dieses Dokument veröffentlichen, konvertiert Edge Delivery Services es automatisch in ein Web-fähiges HTML-Formular, mit dem Benutzende auf Ihrer Site interagieren können.

**Funktionen und Leistungsmerkmale**

* Autor in bekannten Tools: Word, Google Docs, Google Sheets.
* Definieren Sie Felder: Texteingaben, E-Mail, Dropdown-Listen, Kontrollkästchen, Optionsfelder, Textbereiche.
* Fügen Sie Beschriftungen, Platzhalter und Hilfemeldungen hinzu.
* Legen Sie grundlegende Validierungsregeln fest: erforderliche Felder, E-Mail-Format.
* Integrieren Sie reCAPTCHA für den Spam-Schutz.
* Datei-Uploads zulassen.
* Sofortige Veröffentlichung: Änderungen im Dokument werden auf der Live-Site schnell übernommen.
* Mit benutzerdefiniertem Code erweitern: Fortgeschrittene Benutzer können über GitHub benutzerdefinierte Formularkomponenten und Stile hinzufügen.

**Überlegungen**

* Ihr Team verwendet regelmäßig Word oder Google Docs/Sheets für Inhalte.
* Sie müssen einfache bis mäßig komplexe Formulare schnell erstellen.
* Sie möchten Formulardaten direkt an eine Tabelle oder E-Mail-Adresse mit minimalem Setup senden.

**Funktionsweise von Übermittlungen (hauptsächlich Forms Submission Service)**

Auf diese Weise erstellte Forms [senden ihre Daten normalerweise an den AEM Forms Submission Service](/help/forms/forms-submission-service.md). Sie konfigurieren dies (häufig im Quelldokument selbst), um Daten an ein Google-Blatt, eine Excel-Datei auf OneDrive/SharePoint oder als E-Mail zu senden.

**Dokumentenbasiertes Authoring-**
<!--    
```mermaid
    graph LR
        subgraph Authoring["You define your form in a Google Sheet or Word Document"]
        Sheet[Spreadsheet or Document with field definitions:\nField Name - Type - Label\nemail - email - Email Address\nmessage - textarea - Your Message]
    end

        Sheet >|Edge Delivery Services automatically converts it| JSON[Internal Form Definition as JSON]
    JSON >|A 'Form Block' on your page renders it as| HTMLForm[Live HTML Form on Your Website]

        style Sheet fill:#e6ffe6,stroke:#333
        style JSON fill:#e6e6ff,stroke:#333
        style HTMLForm fill:#ffe6e6,stroke:#333
```-->

![Dokumentbasiert](/help/forms/assets/eds-doc-based.png)
Dieses Diagramm zeigt, wie ein in einem Dokument definiertes Formular zu einem Live-Web-Formular wird.

### Visuelles Forms mit universellem Editor

Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) bietet eine moderne Drag-and-Drop-Oberfläche zum Erstellen von Formularen direkt in Ihrem Webbrowser.

**Funktionsweise: Erstellen von Formularen per Drag-and-Drop**

Sie verwenden eine visuelle Benutzeroberfläche, um Formularkomponenten (z. B. Eingabefelder, Schaltflächen, Dropdown-Listen) auf Ihre Seite zu ziehen. Sie können dann die Eigenschaften jeder Komponente (Beschriftungen, Validierung usw.) über ein Eigenschaftenbedienfeld konfigurieren. Der universelle Editor zeigt Ihnen eine Echtzeitvorschau Ihres Formulars an.

**Funktionen und Leistungsmerkmale**

* Visuelle Formularerstellung mit einer Bibliothek vordefinierter Komponenten.
* Echtzeit-Validierung und Geschäftslogik konfigurieren (z. B. Felder basierend auf einer Auswahl ein-/ausblenden).
* Anzeigen von Live-Vorschauen für verschiedene Geräte (Desktop, Mobilgerät).
* Integration mit AEM-Funktionen wie Inhaltsfragmenten, AEM-Workflows und Benutzerberechtigungen.
* Verwenden Sie den „Experience Builder“, um KI-Unterstützung für das Erstellen oder Bearbeiten von Formularen mithilfe von Eingabeaufforderungen zu erhalten.

**Überlegungen**

* Sie müssen komplexe Formulare mit bedingter Logik, mehrstufigen Bedienfeldern oder Personalisierung erstellen.
* Ihr Team (z. B. Marketing-Experten, Business-Anwender) bevorzugt visuelle Tools.
* Sie benötigen eine starke Integration mit AEM as a Cloud Service für Governance, Workflows oder die Verwendung von AEM-Assets in Ihren Formularen.

**Funktionsweise von Übermittlungen (Forms Submission Service oder AEM Publish)**

Forms mit dem universellen Editor kann:

* Verwenden Sie den einfachen [Forms Submission Service](/help/forms/forms-submission-service.md) (zum Senden von Daten an Tabellen oder E-Mails).
* Senden Sie Daten an Ihre AEM-Veröffentlichungsinstanz, um eine erweiterte Verarbeitung zu ermöglichen (z. B. das Starten eines AEM-Workflows, die Verwendung des Formulardatenmodells oder die Integration in andere Unternehmenssysteme).

**Konzept des universellen Editors**

<!--    
```mermaid
    graph TD
    subgraph UE_Interface["Universal Editor Interface in your Browser"]
        Toolbar[Editor Toolbar and Asset Finder]
        Canvas[Your Page with the Form Being Built]
        ComponentPalette[Available Form Components:\nInput / Dropdown / Button\nDrag and drop]
        PropertiesPanel[Configure Selected Component:\nLabel / Validation / Rules]
    end
    ComponentPalette >|Drag & Drop onto| Canvas
    Canvas >|Select a component to edit its| PropertiesPanel
    UE_Interface >|Creates| RenderedForm[Live Form on Your Website]

    style UE_Interface fill:#f0f8ff,stroke:#333
    style RenderedForm fill:#ffe6e6,stroke:#333
```-->

![Universeller Editor](/help/forms/assets/eds-ue-based.png)

Dieses Diagramm zeigt die wichtigsten Teile des universellen Editors, der für die Formularerstellung verwendet wird.

### Verwenden von Forms mit der Dokumenterstellung (Document Authoring, DA)

[Dokumenterstellung (Document Authoring, DA)](https://www.aem.live/developer/da-tutorial) ist ein von Adobe gehosteter Service für die Erstellung und Verwaltung Ihrer wichtigsten Website-Inhalte (Seiten, Artikel), die über Edge Delivery Services bereitgestellt werden. Dies ist eine Alternative zur Verwendung von SharePoint oder Google Drive für Ihre Edge Delivery Services-Quellinhalte.

**Grundlegendes zur Dokumenterstellung (Document Authoring, DA) für Edge Delivery Services-Inhalte**

Die Dokumenterstellung bietet eine Authoring-Umgebung auf Unternehmensniveau, die das Design-System (Spectrum) von Adobe und das Dokumentenmodell (Blöcke, Abschnitte) von AEM verwendet. Es wurde für strukturiertes Content-Management für EDS entwickelt.

**Handhabung von Forms durch DAM (Einbetten, nicht direktes Authoring)**

DA selbst ist **Tool zum Erstellen von Formularen von Grund auf**. Stattdessen verwenden Sie DA, um Ihre Web-Seiten zu erstellen, und dann *Sie* (die mit der dokumentbasierten Inhaltserstellung oder dem universellen Editor erstellt wurden) in diese von DA erstellten Seiten ein.

**Schritte zum Einbetten von Forms in DAM-Seiten**

1. **Formular erstellen** Formular erstellen Sie es wie folgt:
   * Dokumentenbasiertes Authoring (Word/Google Docs)
   * Universeller Editor

1. **Formular veröffentlichen:** Stellen Sie sicher, dass das Formular über eine eigene Edge Delivery-URL veröffentlicht wurde und zugänglich ist (z. B. `https://your-eds-project.hlx.page/forms/contact-us`).
1. **Erstellen Sie Ihre Seite in DA:** Erstellen oder bearbeiten Sie die Seite in der Dokumenterstellung, in der das Formular angezeigt werden soll.
1. **Formular einbetten** Verwenden Sie einen bestimmten „Block“ oder eine bestimmte Komponente innerhalb Ihrer DAM-Seite, um auf das Formular zu verweisen und es über seine URL einzubetten. Die DAM-Seite ruft dann dieses extern erstellte Formular ab und zeigt es an.

**Dokumenterstellung mit eingebettetem Formular**
<!--
```mermaid
    graph TD
    subgraph FormCreation["1. Create Form using other methods"]
        UE_Form[Universal Editor Form] >|Published to| FormLocation[Form lives at its own Edge Delivery Services URL:\nfor example: /forms/my-contact-form]
        DocBased_Form[Document-Based Form] >|Published to| FormLocation
    end

    subgraph DA_Content["2. Author Page in Document Authoring"]
        DAPage[Your Web Page Authored in DA\nExample: /main-site/landing-page]
        EmbedBlock[On DA Page, add 'Embed Form' Block\nPoints to /forms/my-contact-form]
    end

    DAPage > EmbedBlock
    User[User visits your DA Page] > DAPage
    EmbedBlock >|DA Page fetches and displays| FormLocation[The Form appears on your DA Page]

    style FormCreation fill:#e6ffe6,stroke:#333
    style DA_Content fill:#ffe6cc,stroke:#333
    style FormLocation fill:#ccf,stroke:#333
```-->

![Dokumenterstellung](/help/forms/assets/eds-da-based.png)

Dieses Diagramm zeigt, dass Sie ein Formular zuerst mit UE oder Docs erstellen und dann in eine Seite einbetten, die Sie beim Erstellen von Dokumenten erstellt haben.


### Vergleich von Authoring-Optionen

| Kriterien | Dokumentenbasiertes Authoring | Universeller Editor (WYSIWYG) | Forms in der Dokumenterstellung (Document Authoring, DA) |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **Primäres Authoring-Tool** | Word/Google Docs/Sheets | Browser (universeller AEM-Editor) | Nicht zutreffend (Forms sind *eingebettet*) |
| **Team-Qualifikationsstufe** | Vertrautheit mit Dokumenteditoren | Komfortabel mit visuellen Web-Tools | Verwendet DAM für Seiteninhalte |
| **Typische** | Einfach bis mäßig | Mittelmäßig bis komplex, Enterprise-Klasse | Hängt vom eingebetteten Formular ab |
| **Einreichungsoption 1 (einfach)** | Forms Submission Service (an Blatt/E-Mail) | Forms Submission Service (an Blatt/E-Mail) | Folgt dem Setup des eingebetteten Formulars |
| **Übermittlungsoption 2 (erweitert)** | Nicht zutreffend | AEM-Veröffentlichung (Workflow, FDM usw.) | Folgt dem Setup des eingebetteten Formulars |
| **AEM Backend-Integration** | Minimal | Hoch (mit AEM Publish-Übermittlung) | Indirekt über das eingebettete universelle Editor-Formular |
| **Am besten geeignet für…** | Schnelle Erstellung einfacher Formulare durch Content-Teams, schnelle Datenerfassung. | Marketer, Business-Anwender, die visuelle Kontrolle, komplexe Formulare oder eine tief greifende AEM-Integration benötigen. | Websites, auf denen Primärinhalte in DAM verwaltet werden und die Formulare aus anderen Quellen benötigen. |

**Verbesserter Entscheidungsbaum**
<!--
```mermaid
    graph TD
    A{Start Here: I need a form on my Edge Delivery Services Site} > B{What's my team's main authoring tool & skill for form content?};
    B -- "Word/Google Docs" > C{How complex is the form & data destination?};
    C -- "Simple form, data to Sheet/Email" > Sol1[CHOOSE: Document-Based Authoring + Forms Submission Service];
    C -- "Needs more logic OR AEM backend\nlike Workflow or FDM" > Sol2[CONSIDER: Can Universal Editor meet this need better?];

    B -- "AEM User / Visual Editor needed\nMarketer or Designer" > D{Where does the form data need to go?};
    D -- "Simple - to Sheet/Email" > Sol3[CHOOSE: Universal Editor + Forms Submission Service];
    D -- "Advanced - AEM Workflow, FDM,\n3rd Party via AEM" > Sol4[CHOOSE: Universal Editor + AEM Publish Submissions\nRequires additional setup];

    B -- "Our main site content is in Document Authoring (DA)" > Sol5[STRATEGY: Author form using Sol1, Sol2, Sol3 or Sol4 first\nTHEN embed that form into your DA page];

    A > F{Will this form be embedded or fetched from another site or domain?};
    F -- "Yes" > G[IMPORTANT: Configure CORS on the site hosting the form.\nEnsure any form JavaScript blocks are available where the form is displayed];

    style Sol1 fill:#90ee90,stroke:#333
    style Sol2 fill:#fffacd,stroke:#333
    style Sol3 fill:#90ee90,stroke:#333
    style Sol4 fill:#90ee90,stroke:#333
    style Sol5 fill:#add8e6,stroke:#333
    style G fill:#ffb6c1,stroke:#333
```-->

![Entscheidungsbaum](/help/forms/assets/eds-enhanced-decision.png)

## Funktionsvergleich der Authoring-Methoden

Die folgende Tabelle bietet einen detaillierten Vergleich der wichtigsten Funktionen der verschiedenen Authoring-Methoden für AEM-Formulare. So können Sie den für Ihre Anforderungen am besten geeigneten Ansatz auswählen.

| **Funktion** | **Universeller Editor (WYSIWYG)** | **Dokumentenbasiertes Authoring** | **Dokumenterstellung (Document Authoring, DA)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Einheitliche Komposition mit Sites** | ✅ |                              | ✅ (mit integrierten Formularen) |
| **Unterstützung für eingebettete Formulare** | ✅ | ✅ | ✅ (Einbetten im universellen Editor oder in Dokumenten) |
| **Regeln (dynamisches Verhalten)** | Erweiterter Regeleditor mit benutzerdefinierten Funktionen | Limitiert: Ein-/Ausblenden, Wert berechnen, benutzerdefinierte Funktionen | Hängt von eingebettetem Formular ab |
| **Unterstützung für Anhänge** | ✅ | ℹ️ (Frühzeitiger Zugriff) | Hängt von eingebettetem Formular ab |
| **CAPTCHA-Unterstützung** | reCAPTCHA Enterprise | reCAPTCHA Enterprise | Hängt von eingebettetem Formular ab |
| **Übermittlungsfunktionen** | REST, E-Mail, FDM, Workflow, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion (EA) | Nur Kalkulationstabelle | Folgt dem Setup des eingebetteten Formulars |
| **Datenschema** | FDM, benutzerdefiniert | Benutzerdefiniert | Basierend auf eingebettetem Formular |
| **Vorausfüllen** | 💡 (über Assistenten) | ✅ | Hängt von eingebettetem Formular ab |
| **Fragmente** | ✅ | ✅ | Hängt von eingebettetem Formular ab |
| **Visueller Regeleditor** | ✅ |                              |                              |
| **Lokalisierung** | 💡 (über Sites) |  (Excel/Sheets-Handbuch) | Hängt von eingebettetem Formular ab |
| **Datenschema (Datenstruktur)** | 💡 (über die UI-Erweiterung) |                              |                              |
| **Vorlagenunterstützung** | Nur anfänglicher Inhalt |                              |                              |
| **Portal** |                               |                              |                              |
| **Desing** | ℹ️ (auf Projektebene) | ℹ️ (auf Projektebene) |  (basierend auf der Hosting-Site) |
| **Benutzerdefinierte Komponente** | ✅ | ✅ | ✅ (wenn die eingebettete Komponente dies unterstützt) |
| **OOTB und benutzerdefinierte Funktionen** | ✅ | ✅ | ✅ (in eingebetteter Form) |
| **Fragmentreferenz** |                               |                              |                              |
| **Sign-Integration** |                               |                              |                              |
| **Experimente** | ✅ | ✅ | Hängt vom Einbettungskontext ab |
| **Aufgabenverwaltung über Workfront** | ✅ |                              |                              |
| **Personalisierungserweiterung** | 💡 |                              |                              |
| **Editoranpassung** | ✅ (über die UI-Erweiterung) |                              |                              |
| **Übermitteln-Aktion** | ✅ | Nur Kalkulationstabelle | Basierend auf eingebettetem Formular |

<!--

## Best Practices for Creating Forms

Building great forms goes beyond just the technology. Here's how to ensure your forms are user-friendly and achieve their goals:

* **Designing User-Friendly and Accessible Forms**

  *   **Use Clear, Visible Labels:** Every form field needs a `<label>`. Don't rely only on placeholder text (text inside the input field), as it disappears when users type and is bad for accessibility.
        *   *Good:* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
        *   *Bad:* `<input type="email" placeholder="Email Address">`
  *   **Keep it Simple:** Use standard HTML input types (`<input type="date">`, `<input type="tel">`) where possible. They often have better mobile support and accessibility than complex custom widgets.
  *   **Logical Order and Grouping:** Arrange fields in a way that makes sense to the user. Group related fields together using `<fieldset>` and `<legend>`.
  *   **Provide Clear Instructions:** For any fields that might be confusing, offer concise help text or tooltips.
  *   **Keyboard Navigation:** Ensure users can navigate through your entire form using only the keyboard (Tab, Shift+Tab, Enter, Spacebar).
  *   **Error Handling:** Make errors obvious and easy to correct. Display error messages next to the relevant field and explain what needs to be fixed.

* **Ensuring Your Forms Load Quickly and Are Visible**

  *   **Place Forms Prominently:** If a form is important, make sure users can see it easily without too much scrolling ("above the fold" if possible). Adobe's research shows many forms get low interaction because they are hidden.
  *   **Optimize Assets:** Keep any custom JavaScript or CSS for your forms as small as possible to ensure fast load times. Edge Delivery Services helps with the base page load, but heavy form scripts can still slow things down.

* **Handling User Data Responsibly**
  *   **Ask Only What You Need:** The less Personal Identifiable Information (PII) you ask for, the better. Every field is a potential reason for a user to abandon the form.
  *   **Be Transparent:** Clearly explain *why* you need certain information and *how it will be used*. Link to your privacy policy. This builds trust.

* **Improving User Experience: Captcha Alternatives**

  * **Rethink Visible Captchas:** Those "type the wavy text" or "click all the traffic lights" tests can be very frustrating for users, especially those with disabilities, and often lead to high drop-off rates.

*   **Consider Alternatives:**
    *   **Honeypot Fields:** Add a hidden field that only bots would fill out. If it has data, the submission is likely spam.
    *   **Time-Based Checks:** Measure how quickly a form is submitted. Submissions that are too fast are often bots.
    *   **Invisible reCAPTCHA (v3):** This Google service analyzes user behavior in the background and only presents a challenge if the user seems suspicious. This is often a much better user experience.

**Form Design Do's and Don'ts**

```mermaid
    graph LR
subgraph GoodFormUX [Do ✅ - For Better Forms]
    direction LR
    ClearLabels[Use Visible <label> Tags for All Fields]
    SimpleInputs[Prefer Standard HTML Input Types]
    KeyboardNav[Ensure Full Keyboard Navigation]
    ClearErrors[Show Clear, Actionable Error Messages]
    MinimalPII[Ask Only for Necessary Information]
    TransparentUse[Explain How Data is Used - Privacy Info]
    InvisibleCaptcha[Use Invisible or Behavioral CAPTCHA]
    ProminentPlacement[Make Form Easy to Find on Page]
end

subgraph BadFormUX [Don't ❌ - Avoid These]
    direction LR
    PlaceholderOnly[Only Use Placeholder Text for Labels]
    ComplexWidgets[Use Overly Complex Custom Widgets]
    PoorErrors[Vague or Missing Error Messages]
    ExcessivePII[Request Excessive Personal Data]
    VisibleHardCaptcha[Use Hard-to-Solve Visible CAPTCHAs]
    HiddenForm[Hide the Form Deep in the Page]
end

style GoodFormUX fill:#e6ffe6,stroke:#333
style BadFormUX fill:#ffe6e6,stroke:#333
```

## Quick Decision Guide: Choosing the Right Form Strategy

Let's bring it all together to help you decide on the best approach for your forms.

*   **Matching Form Features to Your Project Goals**
    *   **For speed and simplicity with basic data capture (to spreadsheets/email):** Document-Based Authoring with the Forms Submission Service is often your fastest route.
    *   **For visually rich forms with potential for AEM backend integration:** Universal Editor is your tool. You can start with the Forms Submission Service for simple needs and scale to full AEM Publish submissions for complex workflows.
    *   **If your site content is managed in Document Authoring (DA):** You'll create forms using one of the above methods and then embed them into your DA pages. The submission logic will be tied to how the original embedded form was configured.-->

Wenn Sie auf dem aufbauen möchten, was Sie gelernt haben, können Sie folgendermaßen fortfahren:

[Wählen Sie Ihre Übermittlungsstrategie](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) entscheiden Sie, ob Ihr Projekt die Einfachheit des Forms Submission Service (ideal für die Tabellenkalkulations-/E-Mail-Ausgabe) oder die Flexibilität und Backend-Integration erfordert, die von AEM Publish Submit Actions angeboten wird.

Informationen zum Entwerfen [ effektiven, barrierefreien und benutzerfreundlichen Formularen finden Sie im Artikel ](/help/edge/docs/forms/universal-editor/best-pratices-eds-forms.md)Best Practices für die Erstellung von Forms&quot;.

## Nächste Schritte

Dieses Handbuch bietet einen Überblick über die Verwendung von Formularen mit AEM Edge Delivery Services. Detailliertere schrittweise Anleitungen zu bestimmten Konfigurationen finden Sie in der offiziellen Adobe Experience Manager-Dokumentation:

* [Dokumentenbasiertes Authoring mit Edge Delivery Services Forms](/help/edge/docs/forms/tutorial.md)
* [Universeller Editor mit Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Dokumenterstellung (Document Authoring, DA) und Einbetten von Inhalten](https://www.aem.live/developer/da-tutorial)
* [AEM Forms Submission Service](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)


<!-- 
# Edge Delivery Services for AEM Forms
 

Edge Delivery Services for AEM Forms is a composable set of services that enables a rapid development environment where authors can update, publish, and launch new forms rapidly. These services deliver exceptional and high impact forms experiences that drive engagement and conversions. These forms experiences are easy to author and develop.

These services enable you to:

* **Create enrolment experiences with tools of your choice:** Increase authoring efficiency by decoupling content sources. Out of the box you can use Document-based Authoring (Microsoft SharePoint or Google Drive), WYSIWYG Authoring (Universal Editor or Adaptive Forms Editor). You can work with multiple content sources on the same forms site and use your preferred authoring tools, such as Microsoft Excel, Google Sheets, Universal Editor, or Adaptive Forms Editor.

* **Deliver exceptional Digital Enrolment experiences:** Deliver Digital Enrolment experiences that load and render quickly and continuously monitor your forms performance through Operational Telemetry. Faster loading times and optimized user experience contribute to higher form completion and conversion rates. 

* **Use developer friendly toolset:** Edge Delivery Services for AEM Forms
 uses plain HTML, modern CSS, and vanilla JavaScript to create exceptional experiences, avoiding the steep learning curve of a specific framework. A developer with basic web development skills can customize and easily build form components and experiences. There is no need to wait for a pipeline to run, just check-in your code into GitHub and your changes are live.

## Edge Delivery Services for AEM Forms Overview {#edge-overview}

Edge Delivery Services for AEM Forms allows for a high degree of flexibility in how you author forms on your website. You can author content and forms with [WYSIWYG Authoring](/help/forms/creating-adaptive-form-core-components.md) as well as [Document-based Authoring](/help/edge/docs/forms/create-forms.md). Edge Delivery Services for AEM Forms
 provide a forms block, known as [Adaptive Forms Block](/help/edge/docs/forms/create-forms.md) to add a form to your Edge Delivery Services site.

For example, you author forms directly in Microsoft Excel or Google Sheets and these spreadsheets are transformed into forms for your website. Any new form or form content, such as a new form field, is instantly available on your website without requiring a rebuild process.

The following diagram illustrates how you can edit forms in Microsoft Excel or Google Sheets (Document-based Authoring) and publish to Edge Delivery Services. It also shows the AEM publishing method using the WYSIWYG Authoring (Universal Editor or Adaptive Forms Editor).

![Publish to Edge Delivery Services and AEM](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)

Edge Delivery Services for AEM Forms uses GitHub so customers can manage and deploy code directly from their GitHub repository. For example, you can write forms in either [Google Sheets](/help/edge/docs/forms/create-forms.md) or [Microsoft Excel](/help/edge/docs/forms/create-forms.md) and the components of your forms can be developed by using CSS and JavaScript in a GitHub repository.

When your forms are ready, you can use the [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), a chrome browser extension, to preview and publish content updates.

![Install AEM SideKick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

The choice between the [Document-based Authoring ](#document-based-authoring-features) and [WYSIWYG Authoring](#wysiwyg-authoring-features) depends on your specific requirements:

* For simple forms that just collect basic information with a few fields (think contact us forms, lead generation forms, or service request forms), and where you need quick data connectivity using a spreadsheet, the [Document-based Authoring](#document-based-authoring-features) is a good fit. You can build these forms like you would build a document in Google Sheets or Microsoft Excel. 

* For complex forms, like forms requiring multiple panels, complex rules and business logic, data manipulation, integration with external systems, or streamlined workflows using AEM features, then [WYSIWYG Authoring](#wysiwyg-authoring-features) is a better option. 


### Key Features of Document-based Authoring and WYSIWYG Authoring

Document-based Authoring offers a basic set of features and WYSIWYG Authoring unlocks additional capabilities beyond the Document-based Authoring, empowering you to build more complex and interactive forms. The key features of both Document-based Authoring and WYSIWYG Authoring are:

#### Document-based Authoring features

Document-based Authoring  allows you to create forms using familiar tools like Microsoft Excel or Google Sheets. These forms offer the following functionalities:

* Accessible components for a user-friendly experience.
* Standardized HTML structure for consistent rendering.
* Rules and validations to ensure data accuracy.
* File attachment options for collecting additional information.
* Google reCAPTCHA integration for spam protection.
* Ability to create custom form components for specific needs.
* Submit form data directly to Microsoft Excel or Google Sheets or email addresses.
* Monitor your forms performance through Operational Telemetry

#### WYSIWYG Authoring features

WYSIWYG Authoring provides WYSIWYG interfaces (Universal Editor and Adaptive Forms Editor) for building forms and offers all the capabilities of Document-based Authoring, plus a wide range of additional features:

* Advanced rules editor for creating complex logic.
* Server-side extensibility for custom functionalities.
* WYSIWYG editing experience for easy form creation and visualization.
* Document of record functionality to create tamper-proof archives of submitted data.
* Integration with Adobe Sign for electronic signatures.
* Integration with Adobe Workfront Fusion to triggering Adobe Workfront Fusion scenarios upon form submission.
* Integration with various data sources for pre-populating forms and submitting data.
* Form Data Model (FDM) for defining data structure and interactions with various data sources.
* Ability to choose from multiple submit actions for handling form submissions, including submitting data to Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, many more data sources.

The all above features are also available via Adaptive Forms Editor. 

In essence, WYSIWYG Authoring (Universal Editor and [Adaptive Forms Editor](/help/forms/creating-adaptive-form-core-components.md)) builds upon the foundation of [Document-based Authoring](/help/edge/docs/forms/create-forms.md), providing a more advanced toolkit for creating and managing complex forms. 

>[!NOTE]
>
>
> The WYSIWYG Authoring capability is available under the early-adopter program. If you are interested, send a quick email from your work address to aem-forms-ea@adobe.com to request access to the capability.

### Edge Delivery Services for AEM Forms

: Authoring, Publishing, and Submission of Forms  

The following diagrams illustrate the process of creating, publishing, and submitting forms using Document-based Authoring and WYSIWYG Authoring.

![Document-based Authoring](/help/edge/assets/document-based-authoring-workflow.png)

![WYSIWYG Authoring](/help/edge/assets/wysiwyg-authoring-workflow.png)

## Start creating forms

* [Get started with Edge Delivery Services for AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Create a form using Google Sheets or Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Set up your Google Sheets or Microsoft Excel files to start accepting data​](/help/edge/docs/forms/submit-forms.md)
* [Publish your form and start collecting data](/help/edge/docs/forms/publish-forms.md)
* [Customize the look of your forms​](/help/edge/docs/forms/style-theme-forms.md)
* [Add repeatable sections to a form​](/help/edge/docs/forms/repeatable-forms.md)
* [Show a custom thank you message after form submission​](/help/edge/docs/forms/thank-you-page-form.md)
* [Adaptive Form Block components and their properties](/help/edge/docs/forms/form-components.md)
* [Real Use Monitoring](https://www.aem.live/developer/rum#authentication)

<!-- 

## Start creating forms

<div>

  <style>
    .card-container {
        width: calc(33.33% - 10px);;
        margin: 5px;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 5px;
        box-sizing: border-box;
        transition: background-color 0.3s ease; /* Adding transition effect */
    }
    .card-container:hover {
        background-color: #f0f0f0; /* Changing background color on hover */
    }
</style>

<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: -5px;">
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md">
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using Edge Delivery Services forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an Edge Delivery Services form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Customize a theme</b>
        </a>
        <p>Create a consistent brand image by applying the same theme across forms.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Add validations to form fields" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Apply field validations</b>
        </a>
        <p>Reduce errors and frustration by checking form inputs for proper formatting.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Use rules to add dynamic behaviour to a form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use rules to add dynamic behaviour to a form</b>
        </a>
        <p>Reuse preconfigured fragments across multiple forms.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Add repeatable sections</b>
        </a>
        <p>Effortlessly create and add repeatable sections to a form.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Create custom forms components using standard JavaScript and CSS"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create custom components</b>
        </a>
        <p>Use standard JavaScript and CSS to create components and themes.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->
