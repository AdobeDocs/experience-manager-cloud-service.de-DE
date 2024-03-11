---
title: Übersicht über AEM Forms Edge Delivery Services
description: AEM Forms-Edge Delivery Services wurden für optimale Leistung entwickelt und ermöglichen es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 67d9eaaf18725403f6a152b04e022cdca6902de0
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 2%

---

# AEM Forms Edge Delivery Services

AEM Forms Edge Delivery Services ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autoren schnell aktualisieren und veröffentlichen können und neue Formulare schnell gestartet werden.

AEM Forms Edge Delivery Services bietet außergewöhnliche Formularerlebnisse, die Interaktionen und Konvertierungen fördern und damit wirkungsvolle Erlebnisse ermöglichen, die einfach zu erstellen und zu entwickeln sind.

Diese Dienste ermöglichen Ihnen Folgendes:

* **Erstellen Sie mit Tools Ihrer Wahl ein Registrierungserlebnis:** Erhöhen Sie die Autoreneffizienz durch Entkopplung von Inhaltsquellen. Standardmäßig können Sie sowohl dokumentbasiertes Authoring (Microsoft SharePoint oder Google Drive) als auch AEM Authoring (Adaptiver Forms Editor) verwenden. Daher können Sie mit mehreren Inhaltsquellen im selben Formular arbeiten und Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen oder Adaptive Forms Editor verwenden.

* **außergewöhnliche digitale Einschreibeerlebnisse bieten:** Bereitstellung digitaler Registrierungserlebnisse, die schnell geladen und gerendert werden. Schnellere Ladezeiten und optimiertes Benutzererlebnis tragen zu höheren Formularvervollständigungs- und Konversionsraten bei.

* **Verwenden Sie die benutzerfreundlichen Tools für Entwickler:** AEM Forms verwendet einfaches HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse zu erstellen und so die steile Lernkurve eines bestimmten Frameworks zu vermeiden. Entwickler mit grundlegenden Kenntnisse in der Webentwicklung können Formularkomponenten und Erlebnisse anpassen und einfach erstellen. Es ist nicht erforderlich, auf die Ausführung einer Pipeline zu warten. Checken Sie einfach Ihren Code in Github ein und Ihre Änderungen sind live.

## Übersicht über AEM Forms Edge Delivery Services {#edge-overview}

Das folgende Diagramm zeigt, wie Sie Formulare in Microsoft Excel oder Google Tabellen (dokumentbasierte Bearbeitung) bearbeiten und in Edge Delivery Services veröffentlichen können. Außerdem wird die AEM Veröffentlichungsmethode mit dem adaptiven Forms-Editor angezeigt.

![Architektur von Edge Delivery](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

AEM Forms Edge Delivery services ist ein zusammenstellbarer Satz von Diensten, der Ihnen eine hohe Flexibilität bei der Erstellung von Formularen auf Ihrer Website ermöglicht. Sie können beide AEM Content Management mit [AEM Authoring](/help/forms/creating-adaptive-form-core-components.md) sowie [Dokumentenbasiertes Authoring](/help/edge/docs/forms/create-forms.md).

Sie können beispielsweise Formulare direkt in Microsoft Excel oder Google Tabellen erstellen und diese Tabellen werden in Formulare für Ihre Website umgewandelt. Neuer Formularinhalt, z. B. ein neues Formularfeld, steht sofort auf Ihrer Website zur Verfügung, ohne dass ein Neuerstellungsprozess erforderlich ist.

Edge Delivery Services nutzt GitHub, damit Kundinnen und Kunden Code direkt über ihr GitHub-Repository verwalten und bereitstellen können. Sie können beispielsweise Formulare in [Google Tabellen oder Microsoft Excel](/help/edge/docs/forms/create-forms.md) und die Komponenten Ihrer Formulare können mithilfe von CSS und JavaScript in GitHub entwickelt werden. Wenn Sie bereit sind, können Sie die [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content) Browsererweiterung, um Inhaltsaktualisierungen in der Vorschau anzuzeigen und zu veröffentlichen.

![Installieren von AEM Sidekick](/help/edge/assets/install-aem-sidekick.png)

AEM Forms Edge Delivery Services stellt einen Formularblock bereit, der als [Adaptiver Forms-Block](/help/edge/docs/forms/create-forms.md) , um Ihrer Edge Delivery Services-Site ein Formular hinzuzufügen.

Die Wahl zwischen [Dokumentenbasiertes Authoring](#document-based-authoring-features) und [AEM Authoring](#aem-authoring-features) hängt von Ihren spezifischen Anforderungen ab.

Für einfache Formulare, die einfach grundlegende Informationen wie Namen und E-Mails erfassen (denken Sie an Formulare, Formulare zur Lead-Generierung oder Formular für Serviceanfragen) und in denen Sie nur die Daten benötigen, um zu einer Tabelle zu gelangen, wird die [Dokumentenbasiertes Authoring](/help/edge/docs/forms/create-forms.md) ist perfekt geeignet. Sie können diese Formulare wie ein Dokument in Google-Dokumenten erstellen.

Wenn Ihre Formulare komplexer werden, z. B. mehrere Bedienfelder, komplexe Regeln und Geschäftslogik, Datenmanipulationen, Integration in externe Systeme oder optimierte Workflows mithilfe AEM Funktionen, dann [AEM Authoring](/help/forms/creating-adaptive-form-core-components.md) ist eine bessere Option.


### Wichtige Funktionen der Dokumentenbearbeitung und AEM Authoring

Die dokumentbasierte Inhaltserstellung bietet eine Reihe grundlegender Funktionen und AEM Authoring bietet zusätzliche Funktionen, die über die dokumentbasierte Inhaltserstellung hinausgehen. So können Sie komplexere und interaktive Formulare erstellen. Die wichtigsten Funktionen von Document-basiertem Authoring und AEM Authoring sind:

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

#### Dokumentbasierte Authoring-Funktionen

Mit der dokumentbasierten Bearbeitung können Sie Formulare mit vertrauten Tools wie Microsoft Excel oder Google Tabellen erstellen. Diese Formulare bieten die folgenden Funktionen:

* Barrierefreie Komponenten für ein benutzerfreundliches Erlebnis.
* Standardisierte HTML-Struktur für konsistentes Rendering.
* Regeln und Überprüfungen zur Gewährleistung der Datengenauigkeit.
* Optionen für Dateianlagen zum Erfassen zusätzlicher Informationen.
* Google reCAPTCHA-Integration für den Spam-Schutz.
* Möglichkeit, benutzerdefinierte Formularkomponenten für bestimmte Anforderungen zu erstellen.
* Senden Sie Formulardaten direkt an Microsoft Excel- oder Google Tabellen oder E-Mail-Adressen.

#### AEM Authoring-Funktionen

AEM Authoring (mit dem adaptiven Forms-Editor) bietet eine WYSIWYG-Oberfläche zum Erstellen von Formularen und bietet alle Funktionen der dokumentbasierten Bearbeitung sowie eine Vielzahl zusätzlicher Funktionen:

* Erweiterter Regeleditor zum Erstellen einer komplexen Logik.
* Serverseitige Erweiterbarkeit für benutzerdefinierte Funktionen.
* WYSIWYG-Bearbeitungserfahrung für einfache Formularerstellung und -visualisierung.
* Datensatzdokumentfunktionalität zum Erstellen fälschungssicherer Archive gesendeter Daten.
* Integration mit Adobe Sign für elektronische Signaturen.
* Integration mit Adobe Workfront Fusion, um bei der Formularübermittlung Adobe Workfront Fusion-Szenarien auszulösen.
* Integration mit verschiedenen Datenquellen zum Vorausfüllen von Formularen und zum Senden von Daten.
* Formulardatenmodell zum Definieren der Datenstruktur und der Interaktionen mit verschiedenen Datenquellen.
* Möglichkeit zur Konfiguration mehrerer Sendeaktionen für die Verarbeitung von Formularübermittlungen, einschließlich der Übermittlung von Daten an Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics und vielen weiteren Datenquellen.

Im Wesentlichen baut AEM Authoring auf der Grundlage der dokumentbasierten Bearbeitung auf und bietet ein erweitertes Toolkit für die Erstellung und Verwaltung komplexer Formulare.

### Authoring-Workflow

![Dokumentenbasiertes Authoring](/help/edge/assets/document-based-authoring-workflow.png)

![AEM Authoring](/help/edge/assets/aem-authoring-workflow.png)


## Erstellen von Formularen

* [Erste Schritte mit AEM Forms Edge Delivery Services](/help/edge/docs/forms/tutorial.md)
* [Erstellen eines Formulars mit Google Tabellen oder Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Richten Sie Ihre Google Tabellen- oder Microsoft Excel-Dateien ein, um Daten zu akzeptieren &#x200B;](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen Sie Ihr Formular und beginnen Sie mit der Datenerfassung](/help/edge/docs/forms/publish-forms.md)
* [Anpassen des Erscheinungsbilds von Formularen &#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [Wiederholbare Abschnitte zu einem Formular-&#x200B; hinzufügen](/help/edge/docs/forms/repeatable-forms.md)
* [Anzeigen einer benutzerdefinierten Dankesmeldung nach der &#x200B;](/help/edge/docs/forms/thank-you-page-form.md)
* [Komponenten von Bausteinen für adaptive Formulare und ihre Eigenschaften](/help/edge/docs/forms/form-components.md)



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