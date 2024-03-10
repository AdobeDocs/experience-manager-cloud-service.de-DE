---
title: Übersicht über AEM Forms Edge Delivery Services
description: AEM Forms-Edge Delivery Services wurden für optimale Leistung entwickelt und ermöglichen es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 2aa70e78764616f41fe64e324c017873cfba1d5b
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 17%

---

# AEM Forms Edge Delivery Services

Optimieren Sie Formulare und steigern Sie die Abschlussraten mit Adobe AEM Forms-Edge Delivery Services. Diese leistungsstarken, zusammenstellbaren Dienste ermöglichen es Ihnen, Formulare auf Unternehmensebene mit außergewöhnlicher Leistung und visueller Attraktivität zu erstellen. AEM priorisiert sowohl das Anwendererlebnis als auch Ihre Geschäftsziele, gewährleistet blitzschnelle Ladezeiten und höhere Konvertierungen von Formularen.

Der Service bietet folgende Möglichkeiten:

* **Erstellen außergewöhnlicher Registrierungserlebnisse**: Erstellen Sie Registrierungserlebnisse, die schnell geladen und gerendert werden, selbst bei langsamen Internetverbindungen. Schnellere Ladezeiten und optimiertes Benutzererlebnis tragen zu höheren Formularabschlussraten und verbesserten Konversionsraten bei.

* **Registrierungserlebnisse mit Tools Ihrer Wahl erstellen**: Erhöhen Sie die Authoring-Effizienz durch Entkopplung der Inhaltsquellen. Standardmäßig können Sie beide **Dokumentenbasiertes Authoring** (Microsoft SharePoint oder Google Drive) und **AEM Authoring** (Adaptiver Forms-Editor). Daher können Sie mit mehreren Inhaltsquellen im selben Formular arbeiten und Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen oder Adaptive Forms Editor verwenden.

* **Verwenden Sie die benutzerfreundlichen Tools für Entwickler:** AEM Forms verwendet einfaches HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse ohne normalen Verwaltungsaufwand zu erstellen. Jeder Entwickler mit Grundkenntnissen von HTML, CSS und JS sollte in der Lage sein, eigene Komponenten zu erstellen, ohne dass er eine bestimmte Sprache oder ein bestimmtes Framework erlernen muss. Keine Pipeline oder Wartezeit erforderlich, checken Sie Ihren Code in Github ein und Ihre Änderungen sind live. Darüber hinaus ist keine Pipeline oder Wartezeit erforderlich, Sie können Ihren Code in Github einchecken und Ihre Änderungen sind live.


## Übersicht über AEM Forms Edge Delivery Services {#edge-overview}

Das folgende Diagramm zeigt, wie Sie Inhalte in Microsoft Excel oder Google Tabellen (dokumentbasierte Bearbeitung) bearbeiten und in Edge Delivery Services veröffentlichen können. Außerdem wird die AEM Veröffentlichungsmethode mit dem adaptiven Forms-Editor angezeigt.

![Architektur von Edge Delivery](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

Edge Delivery Services ist ein zusammenstellbarer Satz von Diensten, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Wie bereits erwähnt, können Sie beide [AEM Content Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/getting-started/concepts.html?lang=de) mit [AEM Authoring](/help/implementing/universal-editor/introduction.md) sowie [Dokumentenbasiertes Authoring](https://www.aem.live/docs/authoring)

Sie können beispielsweise Inhalte direkt aus Microsoft Excel oder Google Tabellen verwenden. Das bedeutet, dass Inhalte aus diesen Quellen zu Formularen auf Ihrer Website werden können. Der neue Inhalt wird sofort und ohne Neuerstellungsprozess hinzugefügt.

Edge Delivery Services nutzt GitHub, damit Kundinnen und Kunden Code direkt über ihr GitHub-Repository verwalten und bereitstellen können. Sie können beispielsweise Formulare entweder in Google Tabellen oder Microsoft Excel schreiben und die Komponenten Ihrer Formulare können mithilfe von CSS und JavaScript in GitHub entwickelt werden. Wenn Sie bereit sind, können Sie die Sidekick-Browser-Erweiterung verwenden, um Inhaltsaktualisierungen in der Vorschau anzuzeigen und zu veröffentlichen.

AEM Forms Edge Delivery Services stellt einen Formularblock bereit, der als [Adaptiver Forms-Block](/help/edge/docs/forms/create-forms.md) , um Ihrer Edge Delivery Services-Site ein Formular hinzuzufügen.

### Wichtige Funktionen von AEM Forms Edge Delivery Services

Dokumentenbasiertes Authoring bietet grundlegende Funktionen und AEM Authoring bietet zusätzliche Funktionen, die über das dokumentbasierte Authoring hinausgehen. So können Sie komplexere und interaktive Formulare erstellen. In der folgenden Tabelle sind die wichtigsten Funktionen für beide aufgeführt:

<!-- 

>[!BEGINTABS]

>[!TAB Document-based authoring]

Document-based authoring is a versatile option suitable for creating simple forms with essential functionalities. It allows you to integrate various input types like text fields, dropdown menus, and radio buttons, enabling you to collect user data effectively. It offers a basic version of rules to add dynamic behaviour to forms. Key features of Document-based authoring are: 

* **[HTML5-based Form Field components](/help/edge/docs/forms/form-components.md)**: AEM Forms Edge Delivery Services allow you to create user-friendly and interactive forms using form components based on HTML5 [input types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, and <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a>  elements. These components cater to different types of data collection and can be easily customized to fit your specific needs.  

* **Accessibility**: The fields in the form block are accessible. Each label is linked with its respective input element, and IDs are auto-generated for linking. Descriptions associated with fields are linked via the aria-describedby attribute. Keyboard navigation using the standard Tab/Shift + Tab keys is supported.

* **[Styling](/help/edge/docs/forms/style-theme-forms.md)**: Each form field has a fixed HTML structure that can be easily decorated using custom CSS or JavaScript files. Selectors for targeting fields in CSS and JS are provided based on type and name. You can easily create new selectors due to the standradized structure and style your form. 

* **Basic Rules**: Easily create logic that adjusts field visibility, validation, and behavior based on user input or predefined conditions. Rules offer a flexible and intuitive way to add intelligence to your forms, ensuring they adapt seamlessly based on user inputs.

* **Validations**: Before submission, the form is validated, and invalid fields are appropriately marked with error messages displayed to the user. Adaptive Forms Block support all the HTML form validation, supported by modern browsers, and provide additional validation mechanism like validation script, file size, file type, overall file size, and more. 

* **File Uploads**: You can add file attachment capabilities to your forms. Whether you need to gather documents, images, or other files from your users, file upload functionality serves you effortlessly. With custom handling options available, you can tailor the file upload process to suit your specific requirements.

* **reCAPTCHA**: Benefit from seamless integration of Google reCAPTCHA into your forms with our out-of-the-box (OOTB) support. Safeguard your forms against fraudulent activities, spam, and abuse, while maintaining a smooth and uninterrupted user experience. Adaptive Forms Block supports reCaptcha V3 and reCaptcha Enterprise. 

* **Send email notification on form submission**: Eliminate the hassle of manual follow-ups and ensure timely communication with our built-in email automation for form submissions. This integrated solution lets you effortlessly notify relevant parties, including sending form data, whenever someone fills out a form on your website. No need for complex configurations or additional tools – it's ready to use out of the box.

>[!TAB AEM Authoring]

AEM Authoring unlocks additional capabilities beyond the document-based authoring, empowering you to build more complex and interactive forms. In additon to the features of Document-based authoring, AEM authoring offers the following additional features:  

* Advanced Rules: Define logic-based actions within your forms. You can use rules to conditionally show or hide form sections, pre-populate fields based on user input, and perform various validations to ensure data integrity.

* Server-side extensibility: Extend the functionalities of your forms by integrating them with server-side logic. This allows you to perform complex calculations, interact with external systems, and automate specific tasks based on user actions within the form.
* Streamline workflows and data management: Leverage the power of AEM to:
    * Design user-friendly forms using AEM editors.
    * Generate a "Document of Record" for secure and tamper-proof archiving of submitted data.
    * Facilitate e-signing with Adobe Sign for a smooth and secure signing experience.
    * Automate business processes through AEM workflows, triggering actions based on form submissions.
    * Effortlessly integrate with various data sources, enabling seamless data flow and exchange.

>[!ENDTABS]



## Start creating forms

-->

|                                           | Dokumentenbasiertes Authoring | AEM Authoring (adaptiver Forms-Editor) |
| ----------------------------------------- | ------------------------ | ------------------------------------ |
| **Formularfunktionen** |                          |                                      |
| Barrierefreie Komponenten | ✓ | ✓ |
| Standardisierte HTML-Struktur | ✓ | ✓ |
| Regeln und Überprüfungen | ✓ | ✓ |
| Dateianlagen (Datei-Upload) | ✓ | ✓ |
| Google reCAPTCHA | ✓ | ✓ |
| Benutzerdefinierte Komponenten | ✓ | ✓ |
| An E-Mail übermitteln | ✓ | ✓ |
| **Erweiterte Funktionen** |                          |                                      |
| Erweiterte Regeln mit visuellem Regeleditor |                          | ✓ |
| Serverseitige Erweiterbarkeit |                          | ✓ |
| Mehrere Sendeaktionen |                          | ✓ |
| **Formularentwurf und -verwaltung** |                          |                                      |
| Adaptiver Forms-Editor für WYSIWYG-Bearbeitung |                          | ✓ |
| **Integrationen** |                          |                                      |
| Datensatzdokument |                          | ✓ |
| Integration mit Adobe Sign |                          | ✓ |
| Integration mit Adobe Analytics |                          | ✓ |
| Integration mit Marketo |                          | ✓ |
| Integration mit mehreren Datenquellen |                          | ✓ |
| Mehrere Sendeaktionen |                          | ✓ |


## Erstellen von Formularen

* [Erste Schritte - Tutorial für Entwickler](/help/edge/docs/forms/tutorial.md)
* [Erstellen eines Formulars mit Google Tabellen oder Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Formulare direkt an Ihre Microsoft Excel- oder Google Tabellen senden](/help/edge/docs/forms/submit-forms.md)
* [Ändern des Erscheinungsbilds Ihrer Formulare](/help/edge/docs/forms/style-theme-forms.md)


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