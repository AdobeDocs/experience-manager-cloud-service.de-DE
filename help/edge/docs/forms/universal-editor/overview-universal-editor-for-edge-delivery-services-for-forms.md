---
title: Universeller Editor für Edge Delivery Services für Forms (EDS Forms Block)
description: Verwenden Sie den universellen Editor für Edge Delivery Services für Forms (EDS Forms Block), um adaptive Forms zu erstellen.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: ef6f00203241c12fce08cf81495b36f47e64613e
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 14%

---

# Universeller Editor für Edge Delivery Services für Forms (EDS Forms Block)


Der universelle Editor soll Inhaltserstellern und Formularautoren dabei helfen, Formulare einfach zu erstellen, zu verwalten und zu bearbeiten. Es bietet ein einfaches, visuelles und effizientes Bearbeitungserlebnis, das sich auf Edge Delivery Services (EDS) konzentriert.

Mit dem universellen Editor können Benutzer Formularelemente (wie Textfelder, Kontrollkästchen und Optionsfelder) verwenden, um Formulare in einer What You See Is What You Get (WYSIWYG)-Oberfläche zu erstellen. Der WYSIWYG-Ansatz macht die Erstellung von Formularen intuitiv und barrierefrei, auch für diejenigen ohne technisches Know-how.

Der universelle Editor ist speziell auf Edge Delivery Services (EDS) ausgerichtet. Die Hauptstärke des universellen Editors liegt in seinem robusten Funktionssatz, der erweiterte Formularerstellungsfunktionen, dynamische Regelbearbeitung und die nahtlose Integration mit verschiedenen Datenquellen umfasst. Benutzer können schnell responsive Formulare mithilfe von vordefinierten Komponenten, anpassbaren Vorlagen und einer umfangreichen Bibliothek von Formularelementen entwerfen.

![Universeller Editor](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=50%, align-center}

Die Funktionen des universellen Editors sind sorgfältig darauf ausgelegt, ein schlankes Client-seitiges Rendering, Browser-übergreifende Kompatibilität und die strikte Einhaltung von Barrierefreiheitsstandards zu gewährleisten.

## Wichtigste Funktionen des universellen Editors für EDS Forms


<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/generate-forms.svg" alt="WYSIWYG-Benutzeroberfläche"> 
    <h3>WYSIWYG-Benutzeroberfläche</h3>
    <p>Der universelle Editor bietet eine WYSIWYG-Benutzeroberfläche für den Formularentwurf mit einer vordefinierten Komponentenbibliothek, responsivem Design, vorlagenbasierter Erstellung und Änderungen an Echtzeit-Feldern.
 </p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/rule-editor.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Regeleditor">
    <h3>Regeleditor</h3>
    <p>Mit dem Regeleditor können Benutzer mithilfe ereignisgesteuerter Regeln, sofortiger Validierung und Fehlerbehandlung über Lightweight JavaScript und JSON dynamische Formularinteraktionen erstellen.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/responsive.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Responsiver Modus">
    <h3>Responsiver Modus </h3>
    <p>Entwerfen von Formularen, die sich nahtlos auf allen Geräten (Desktop-PCs, Tablets und Mobilgeräte) anpassen. Verwenden Sie den responsiven Modus, um Formulare für verschiedene Bildschirmgrößen in der Vorschau anzuzeigen und zu testen.</p>
  </div>
</div>
<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/personalization.svg" alt="WYSIWYG-Schnittstelle alt=" WYSIWYG Interface"> 
    <h3>Personalisierung</h3>
    <p>Personalization verwendet Benutzerdaten, um benutzerspezifische Formularerlebnisse bereitzustellen und Inhalte, Layouts oder Optionen basierend auf den Benutzereinstellungen dynamisch anzupassen.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/experimentation-ab-testing.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Regeleditor">
    <h3>A/B-Tests</h3>
    <p>A/B-Tests (Experimente) ermöglichen es Unternehmen, mit verschiedenen Formularentwürfen, Layouts und Funktionen zu experimentieren, um die Varianten mit der besten Leistung zu ermitteln.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/adobe-workfront.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Integration mit Adobe Workfront">
    <h3> Aufgabenverwaltung </h3>
    <p>Durch die Integration mit Adobe Workfront können Teams Aufgaben für die Erstellung und Wartung von Formularen verwalten und so optimierte Workflows sicherstellen.</p>
  </div>
</div>

<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/prefill-services.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Vorbefüllungs-Services">
    <h3>Vorbefüllungs-Services</h3>
    <p>Vorbefüllungs-Services füllen Formularfelder automatisch mit relevanten Benutzerdaten aus verschiedenen Quellen, wodurch die manuelle Eingabe reduziert und das Benutzererlebnis verbessert wird.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/data-binding.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Datenbindung">
    <h3>Datenbindung</h3>
    <p>Die Datenbindung ermöglicht direkte Verbindungen zwischen Formularfeldern und Backend-Datenquellen und unterstützt Echtzeit-Updates und erweiterte Datenzuordnung für die strukturierte, konforme Datenspeicherung.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/publish-unpublish.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Internationalisierung/Lokalisierung">
    <h3>Veröffentlichen/Rückgängigmachen der Veröffentlichung</h3>
    <p>Kontrollieren Sie ganz einfach die Sichtbarkeit Ihrer Formulare - veröffentlichen oder heben Sie die Veröffentlichung mit nur wenigen Klicks auf, um Verfügbarkeit und Inhaltsaktualisierungen dynamisch zu verwalten.</p>
  </div>
</div>

<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/analyticsandtracking.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Analytics und Tracking">
    <h3>Analytics und Tracking</h3>
    <p>Gewinnen Sie mit der integrierten Analyse und Verfolgung Einblicke in das Benutzerverhalten, Formularinteraktionen und Übermittlungsraten, um eine datengesteuerte Formularoptimierung zu ermöglichen.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/submit-actions.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Aktionen übermitteln">
    <h3>Aktionen übermitteln</h3>
    <p>Übermittlungsaktionen unterstützen Backend-Integration, Logik für die bedingte Übermittlung, sichere Endpunkte und Präprozessoren und optimieren so die Übermittlungs-Workflows.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/custom-components.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Aufgabenverwaltung">
    <h3>Benutzerdefinierte Komponenten</h3>
    <p>Benutzerdefinierte Komponenten ermöglichen es Entwicklerinnen und Entwicklern, die Formularfunktionen durch die Erstellung eindeutiger Elemente zu erweitern, die auf bestimmte Anwendungsfälle im Unternehmen zugeschnitten sind.</p>
  </div>
</div>

<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/editor-customization.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Editor-Anpassung">
    <h3>Editor-Anpassung</h3>
    <p>Entwickler können die Funktionalität des universellen Editors durch Benutzeroberflächenerweiterungen erweitern, was maßgeschneiderte Lösungen ermöglicht, die spezifischen organisatorischen Anforderungen entsprechen.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/embedding-forms.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Einbetten von Forms">
    <h3>Einbetten von Forms</h3>
    <p>Betten Sie Formulare mithilfe der integrierten Einbettungskomponente des universellen Editors direkt in Edge Delivery Services Sites-Seiten ein, um ein nahtloses Benutzererlebnis zu gewährleisten.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/thank-you.svg" alt="WYSIWYG-Benutzeroberfläche" alt="Benutzerdefinierte Komponenten">
    <h3>Dankeskonfiguration</h3>
    <p>Einfaches Anpassen der Bestätigungsmeldung oder -seite, die Benutzern nach erfolgreicher Formularübermittlung angezeigt wird.
    </p>
  </div>
</div>
</div>


<!-- ![Universal Editor](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg)  **WYSIWYG interface for Form creation**: Universal Editor provides a WYSIWYG interface for form design. It provides pre-built component library, responsive design support, and template-based form creation. You can instantly add or remove form fields and modify field properties (like label, data binding, validation). You can also plugin custom form components to Universal Editor.


* **Rule editor**: The rule editor stands out as a powerful mechanism for creating sophisticated form interactions. It supports event-driven rules, instant validation, and error handling through lightweight JavaScript and JSON-based definitions. This allows developers to implement complex form logic, such as conditional field visibility, automatic calculations, and dynamic form behaviour without extensive coding.

* **Submit actions**: Submit Actions enable form submission workflows. These actions provide comprehensive backend integration options, supporting protocols like REST API. The system allows you configure data pre-processors for automatic data transformation, conditional submission logic based on form field values, and secure endpoint connections. Organizations can define complex submission rules that validate data, and manage form responses with granular control.

* **Pre-fill services:** Pre-fill Services enhance user experience by intelligently populating form fields with relevant data. These services connect to various data sources, including user profiles, browser local storage, and external databases. The mechanism supports dynamic data population, enabling automatic completion of form fields based on contextual information. Users benefit from reduced manual data entry, while administrators gain flexibility in configuring pre-fill rules across different form types and scenarios. The pre-fill functionality adapts to different authentication methods, including session-based approaches and token-based systems, ensuring both convenience and security.

* **Data binding capabilities**: Data binding in the Universal Editor enables direct, dynamic connections between form fields and backend data sources. This feature allows real-time synchronization of form data, supporting complex data mapping scenarios. The system supports transforming form inputs into structured database records with minimal configuration. Advanced mapping supports nested data structures, allowing complex form designs to interact seamlessly with intricate data models.

* **Internationalization/localization capabilities**: Internationalization support ensures global accessibility, with multi-language rendering, right-to-left language compatibility, and locale-specific formatting.

* **Analytics and tracking mechanisms**: The built-in analytics and tracking mechanisms provide comprehensive insights into form interactions, submission rates, and user behavior, enabling continuous optimization of form design and performance. 

* **Experimentation (A/B Testing)**: The Universal Editor supports experimentation by allowing organizations to run A/B tests on form designs to identify the best-performing layouts or features.

* **Task Management via Adobe Workfront**: Integration with Adobe Workfront allows teams to manage tasks related to form creation and maintenance, ensuring streamlined collaboration and efficient workflows.

* **Editor Customization via UI Extension**: Developers can extend the functionality of the Universal Editor through UI extensions, enabling tailored solutions that fit specific organizational needs. -->

## Vordefinierte Formularkomponenten

Der universelle Editor bietet standardmäßig die folgenden Formularkomponenten:

<table>
  <thead>
    <tr>
      <th></th> 
      <th>Formularkomponenten</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="22"><img src="/help/edge/docs/forms/universal-editor/assets/adaptive-forms-components.png" alt="Formularkomponenten" style="width: 100%;"></td> 
      <td><b>Akkordeon</b></td>
      <td>Reduzierbare Bedienfeldstruktur zum Organisieren von Inhalten.</td>
    </tr>
    <tr>
      <td><b>Schaltfläche</b></td>
      <td>Fügt interaktive Elemente für Aktionen wie Navigation oder benutzerdefinierte Logik hinzu.</td>
    </tr>
    <tr>
      <td><b>Captcha</b></td>
      <td>Verhindert Spam, indem Benutzer mithilfe von Google reCAPTCHA oder HCaptcha eine menschliche Verifizierungsaufgabe ausführen müssen.</td>
    </tr>
    <tr>
      <td><b>Kontrollkästchen</b></td>
      <td>Ermöglicht Benutzern das Konfigurieren eines Kontrollkästchens.</td>
    </tr>
    <tr>
      <td><b>Kontrollkästchengruppe</b></td>
      <td>Ermöglicht Benutzern die Auswahl mehrerer Optionen aus einer Gruppe.</td>
    </tr>
    <tr>
      <td><b>Datumsauswahl</b></td>
      <td>Ermöglicht Benutzern die Auswahl eines Datums über eine Kalenderschnittstelle.</td>
    </tr>
    <tr>
      <td><b>Dropdown-Listen</b></td>
      <td>Bietet Einzel- oder Mehrfachauswahl-Optionen aus einer vordefinierten Liste.</td>
    </tr>
    <tr>
      <td><b>E-Mail</b></td>
      <td>Erfasst E-Mail-Adressen mit einfacher Formatvalidierung.</td>
    </tr>
    <tr>
      <td><b>Dateianhang</b></td>
      <td>Ermöglicht das Hochladen von Dokumenten, Bildern oder anderen Dateitypen.</td>
    </tr>
    <tr>
      <td><b>Formularfragmente</b></td>
      <td>Wiederverwendbare Formularkomponenten für Abschnitte wie Adressfelder oder Kontaktdetails.</td>
    </tr>
    <tr>
      <td><b>Bild</b></td>
      <td>Unterstützt das Hochladen und Anzeigen von Bildern in Formularen.</td>
    </tr>
    <tr>
      <td><b>Modal</b></td>
      <td>Zeigt ein Popup-Dialogfeld an, das häufig für Warnhinweise, zusätzliche Informationen oder eine Bestätigung verwendet wird.</td>
    </tr>
    <tr>
      <td><b>Numerisches Feld</b></td>
      <td>Erfasst numerische Eingaben und ermöglicht die Validierung von Zahlen oder Bereichen.</td>
    </tr>
    <tr>
      <td><b>Bedienfeld</b></td>
      <td>Organisiert Formularabschnitte mit erweiterbaren/ausblendbaren Bereichen.</td>
    </tr>
    <tr>
      <td><b>Optionsschalter</b></td>
      <td>Aktiviert die Auswahl aus einer Optionsgruppe.</td>
    </tr>
    <tr>
      <td><b>Bewertung</b></td>
      <td>Ermöglicht Benutzern die Angabe einer Sternebewertung.</td>
    </tr>
    <tr>
      <td><b>Schaltfläche „Zurücksetzen“</b></td>
      <td>Setzt die Formularfelder auf ihren Standardstatus zurück.</td>
    </tr>
    <tr>
      <td><b>Schaltfläche „Senden“</b></td>
      <td>Trigger übermitteln Formulare und initiieren definierte Workflows.</td>
    </tr>
    <tr>
      <td><b>Telefonnummernfeld</b></td>
      <td>Erfasst Telefonnummern mit Formatierung basierend auf dem Land.</td>
    </tr>
    <tr>
      <td><b>Text</b></td>
      <td>Bietet einen speziellen Abschnitt für die Anzeige rechtlicher Begriffe und die Erfassung von Benutzerzustimmung durch Kontrollkästchen.</td>
    </tr>
    <tr>
      <td><b>Textfeld</b></td>
      <td>DC erfasst einzeilige Eingaben, wie Namen oder E-Mail-Adressen.</td>
    </tr>
    <tr>
      <td><b>Assistent</b></td>
      <td>Leitet Benutzende Schritt für Schritt durch einen mehrteiligen Formularprozess.</td>
    </tr>
  </tbody>
</table>

<!-- * Footer: Adds a footer section for consistent design or additional information.
* Form Container: Wraps all form elements and manages overall form properties.
* Header: Adds a header section for form titles, branding, or instructions.-->
<!-- * 
* Prefillable Fields: Automatically populates form fields with data from predefined sources such as user profiles or APIs. 

* Switches/Toggle Buttons: Provides binary on/off choices for user input.


* Title: Adds a text-based heading or label to improve form clarity and organization.


In-addtion to pre-built form components, the Universal editor also provides support for:

* **Embedding Forms in Another Webpage**: The Universal Editor supports embedding forms directly into Edge Deliver Services Sites pages. This can be done using the embed component provided out of the box.

* **Validation Messages**: Validation messages provide real-time feedback to users when they enter incorrect or incomplete data. Features include:
    * Dynamic Error Display: Instantly alerts users to errors, such as invalid email addresses or missing required fields.
    * Customizable Messages: Allows form authors to define user-friendly error texts.
    * Rule-Based Validation: Supports advanced validation logic, such as checking dependencies between fields or implementing conditional rules.

* **Hidden Fields**: Hidden fields store data invisibly within the form, often for backend processing or prefilled values. Use cases include:
    * Passing contextual information (e.g., user ID or session data) to the backend without displaying it to users.
    * Capturing metadata like timestamps or tracking IDs.
    * Hidden fields are not visible to end-users but can be prefilled, updated dynamically, or used in workflows.

* **Custom Components**: Custom components allow developers to extend the functionality of forms by creating specialized or third-party integrations. Features include:
    * Flexibility: Developers can design unique form elements tailored to specific use cases.
    * Third-Party Integration: Embed widgets or tools like payment gateways, analytics trackers, or AI-driven input fields.
    * Seamless Compatibility: Custom components can integrate with the Universal Editor's drag-and-drop interface and existing features like data binding or validation.

* **Thank you Configuration**: Customize the acknowledgment message or page shown after form submission.
-->


## Onboarding

Um den universellen Editor und den Regeleditor für Ihre Umgebung zu aktivieren oder zusätzliche Funktionen wie Forms-Portal, Datensatzdokument, Adobe Sign-Integration oder Sprachunterstützung von rechts nach links anzufordern, senden Sie einfach eine E-Mail an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) von Ihrer offiziellen Adresse mit Ihrer Anfrage.



## Beginnen mit dem Erstellen von Formularen

* [Erste Schritte mit Edge Delivery Services für AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Erstellen eines Formulars mit Google Tabellen oder Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Einrichten von Google Tabellen- oder Microsoft Excel-Dateien, um Daten zu akzeptieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen des Formulars und Starten der Datenerfassung](/help/edge/docs/forms/publish-forms.md)
* [Anpassen des Erscheinungsbilds von Formularen](/help/edge/docs/forms/style-theme-forms.md)
* [Hinzufügen wiederholbarer Abschnitte zu einem Formular](/help/edge/docs/forms/repeatable-forms.md)
* [Anzeigen einer benutzerdefinierten Dankesnachricht nach der Formularübermittlung](/help/edge/docs/forms/thank-you-page-form.md)
* [Komponenten von adaptiven Formularblöcken und ihre Eigenschaften](/help/edge/docs/forms/form-components.md)
* [Real Use Monitoring](https://www.aem.live/developer/rum#authentication)

<!-- 

## Start creating forms

<div>

  <style>
    .card-container {
        width: calc(30% - 10px);;
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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using eds forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an eds form" style="border-radius: 5px;"> </b>
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
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an EDS Form" style="border-radius: 5px;"> </b>
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
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->
