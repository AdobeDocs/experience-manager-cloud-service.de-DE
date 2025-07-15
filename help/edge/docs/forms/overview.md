---
title: Überblick über Edge Delivery Services für AEM Forms
description: Erstellen und liefern Sie leistungsstarke Formulare in Adobe Experience Manager Edge Delivery Services mit einem Schwerpunkt auf dem Authoring-Ansatz mit dem universellen Editor.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 48%

---


# Edge Delivery Services für AEM Forms


Edge Delivery Services für AEM Forms ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autorinnen und Autoren (neue) Formulare schnell aktualisieren, veröffentlichen und live schalten können.  Diese Dienste bieten außergewöhnliche und sehr wirkungsvolle Formularerlebnisse, die Interaktionen und Konversionen fördern. Diese Formularerlebnisse sind einfach zu erstellen und zu entwickeln.

Diese Dienste ermöglichen Ihnen Folgendes:

* **Erstellen von Registrierungserlebnissen mit den Tools Ihrer Wahl**: Erhöhen Sie die Effizienz beim Authoring durch Entkopplung der Inhaltsquellen. Sie können standardmäßig dokumentenbasiertes Authoring (Microsoft SharePoint und Google Drive) und WYSIWYG-Authoring (universeller Editor oder Editor für adaptive Formulare) verwenden. Sie können mit mehreren Inhaltsquellen auf derselben Formular-Site arbeiten und Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen, den universellen Editor oder den Editor für adaptive Formulare verwenden.

* **Bereitstellen außergewöhnlicher digitaler Registrierungserlebnisse:** Stellen Sie digitale Registrierungserlebnisse bereit, die schnell und kontinuierlich geladen und gerendert werden, und überwachen Sie die Leistung von Formularen durch eine betriebliche Telemetrie. Schnellere Ladezeiten und ein optimiertes Anwendererlebnis tragen zu höheren Formularabschluss- und Konversionsraten bei.

* **Verwenden eines benutzerfreundlichen Toolsets:** Edge Delivery Services für AEM Forms
verwendet einfaches HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse zu erstellen und so die steile Lernkurve eines bestimmten Frameworks zu vermeiden. Entwickelnde mit grundlegenden Kenntnissen in der Webentwicklung können Formularkomponenten und Erlebnisse anpassen und problemlos erstellen. Es ist nicht erforderlich, auf die Ausführung einer Pipeline zu warten. Checken Sie einfach Ihren Code in GitHub ein und Ihre Änderungen sind live.

## Auswählen einer Authoring-Methode


Adobe Experience Manager (AEM) Edge Delivery Services (EDS) ermöglicht die Bereitstellung von schnellen, hochgradig skalierbaren Web-Erlebnissen direkt am Edge. In diesem Handbuch wird erläutert **wie Sie Formulare für diese Erlebnisse erstellen und** - mit einer klaren Empfehlungshierarchie:

1. **Universeller Editor (UE) - Beste Wahl für die meisten Teams**
2. **Dokumentenbasiertes Authoring (Dokumente/Blätter) - Ideal für schnelle, einfache Formulare**
3. **Dokumenterstellung (Document Authoring, DA) - Zum Einbetten von Formularen in von der DA erstellte Seiten**

Am Ende können Sie die richtige Authoring-Methode auswählen, Übermittlungsoptionen verstehen und die nächsten Schritte in Richtung produktionsbereiter Formulare ausführen.





| Team und Anforderung | Empfohlene Methode | Warum |
|--------------------|--------------------|-----|
| Marketing-Experten und -Designer benötigen visuelle Kontrolle, Bedingungslogik oder AEM-Integrationen | **Universeller Editor** | Drag-and-Drop, erweiterte Regeln, Übermittlungen an FSS oder AEM Publish |
| Inhaltsautoren, die bereits in Word/Google Docs/Sheets arbeiten; einfache Datenerfassung in Tabellen/E-Mails | **Dokumentenbasiertes Authoring** | Bekannte Tools, schnellster Pfad für grundlegende Formulare |
| Integrierte Website-Seiten **Dokumenterstellung (Document Authoring, DA)** | **Einbetten** eines UE- oder DOC-basierten Formulars in die DA-Seite | DA erstellt keine Formulare selbst |


## Authoring-Methoden im Detail

### Universeller Editor

<span class="preview"> Dies ist eine Vorabversion-Funktion, die über unseren <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features">Vorabversionskanal</a> verfügbar ist</span>

Der universelle Editor ist ein visuelles Drag-and-Drop-Authoring-Tool für Marketing-Experten und Designer, das Geschwindigkeit mit Leistung auf Unternehmensniveau kombiniert:

* Echtzeit-WYSIWYG-Bearbeitung und Gerätevorschau.
* Direkte Integration mit AEM-Assets, Workflows und Formulardatenmodell (FDM).
* Nahtlose Übergabe an Entwickler für benutzerdefinierte Komponenten in Vanilla JS/CSS.
* Erweiterter Regeleditor zum Erstellen einer komplexen Logik.
* Server-seitige Erweiterbarkeit für benutzerdefinierte Funktionen.
* WYSIWYG-Bearbeitungserlebnis für einfache Formularerstellung und -visualisierung.
* Dokument der Datensatzfunktionalität zum Erstellen fälschungssicherer Archive übermittelter Daten.
* Integration in Adobe Sign für elektronische Signaturen.
* Integration in Adobe Workfront Fusion, um bei der Formularübermittlung Adobe Workfront Fusion-Szenarien auszulösen.
* Integration in verschiedene Datenquellen zum Vorausfüllen von Formularen und zum Übermitteln von Daten.
* Formulardatenmodell (FDM) zum Definieren der Datenstruktur und der Interaktionen mit verschiedenen Datenquellen.
* Möglichkeit zur Wahl zwischen mehreren Sendeaktionen für die Verarbeitung von Formularübermittlungen, darunter die Übermittlung von Daten an Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics und viele weiteren Datenquellen.
* Übermitteln mit Übermittlungsaktionen des Forms Submission Service (FSS) oder der AEM-Veröffentlichung

> **Empfehlung** Beginnen Sie jedes neue Formularprojekt mit dem universellen Editor, es sei denn, Ihr Team ist zu 100 % dokumentzentriert und das Formular ist sehr einfach.


### Dokumentenbasiertes Authoring (mit Microsoft Docs oder Google Sheets)

Das dokumentbasierte Authoring eignet sich am besten für die Erstellung einfacher, weniger komplexer Formulare mit bekannten Tools wie Microsoft Word, Google Docs oder Google Sheets. Diese Methode eignet sich ideal für Inhalts-Teams, die eine schnelle und unkomplizierte Möglichkeit zum Erstellen von Formularen benötigen.

* Barrierefreie Komponenten für ein benutzerfreundliches Erlebnis.
* Standardisierte HTML-Struktur für konsistentes Rendern.
* Regeln und Überprüfungen zur Gewährleistung der Datengenauigkeit.
* Optionen für Dateianhänge zum Erfassen zusätzlicher Informationen.
* Google reCAPTCHA-Integration für den Spam-Schutz.
* Möglichkeit zur Erstellung benutzerdefinierter Formularkomponenten für bestimmte Anforderungen.
* Übermitteln Sie Formulardaten direkt an Microsoft Excel oder Google Tabellen oder E-Mail-Adressen.
* Überwachen der Formularleistung durch betriebliche Telemetrie


### Einbetten von Forms in die Dokumenterstellung (DA)

Die Dokumenterstellung (Document Authoring, DA) ist für die Erstellung strukturierter Seiteninhalte konzipiert und unterstützt nicht die Erstellung nativer Formulare. Um ein Formular zu einer von der geräteübergreifenden Analyse erstellten Seite hinzuzufügen, können Sie das Formular mit dem **universellen Editor** (empfohlen) oder der dokumentbasierten Bearbeitung erstellen und das Formular in die Seite für die Dokumenterstellung einbetten.

## Veröffentlichen von Edge Delivery Services Forms {#edge-overview}

Das folgende Diagramm zeigt, wie Sie Inhalte in Microsoft Excel oder Google Tabellen (dokumentbasiertes Authoring) bearbeiten und mit Edge Delivery Services veröffentlichen können. Außerdem wird die AEM-Veröffentlichungsmethode mit dem WYSIWYG-Authoring-Tool (universeller Editor) angezeigt.

![Veröffentlichen in Edge Delivery Services und AEM](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)


<!-- 
## Feature Comparison

| Capability | Universal Editor | Document-Based | Document Authoring |
|------------|-----------------|----------------|--------------------|
| Visual drag-and-drop | ✅ | – | – |
| Advanced rules editor | ✅ | Limited | – |
| Attachments | ✅ | EA | – |
| reCAPTCHA Enterprise | ✅ | ✅ | Depends on embed |
| Submit to spreadsheet/email | ✅ (FSS) | ✅ (FSS) | Via embed |
| Submit to AEM workflows/FDM | ✅ | – | Via UE embed |
| Custom components (JS/CSS) | ✅ | ✅ | Via embed |
| Localization via Sites | ✅ | Manual | Via embed |

-->

## Nächste Schritte

1. **Erste Schritte mit dem universellen Editor:** Informationen zum Erstellen von Formularen finden Sie [ „Erste Schritte ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) universellen Editor“.
1. **Verwenden der dokumentbasierten Inhaltserstellung:** Um Formulare mit Microsoft Excel oder Google Sheets zu erstellen, folgen Sie der [Tutorial zur dokumentbasierten Inhaltserstellung](/help/edge/docs/forms/tutorial.md).
1. **Einbetten von Forms in die Dokumenterstellung:** Wenn Sie beim Erstellen von Dokumenten Seiten erstellen, erstellen Sie das Formular mit dem **universellen Editor** (empfohlen) oder der dokumentbasierten Bearbeitung und betten Sie das Formular in eine [DA-Seite ein](https://www.aem.live/developer/da-tutorial).

Jetzt können Sie Ihr erstes Hochleistungsformular mit AEM Edge Delivery Services erstellen.


<!-- 

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