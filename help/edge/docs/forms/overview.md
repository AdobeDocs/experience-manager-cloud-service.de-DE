---
title: Übersicht über den AEM Forms Edge-Bereitstellungsdienst
description: AEM Forms Edge Delivery Service wurde für optimale Leistung entwickelt und ermöglicht es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 6fc55366119662ed803008f4cec8731e43120942
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# AEM Forms Edge Delivery Service {#aem-forms-edge-delivery-service-overview}

AEM Forms Edge Delivery Service ist ein von Adobe angebotener zusammenstellbarer Service, mit dem Sie leistungsstarke Webformulare erstellen und bereitstellen können. Dieser zusammenstellbare Dienst lässt sich nahtlos in Adobe Experience Manager (AEM) integrieren, damit Sie mit einem intuitiven und effizienten Workflow leistungsstarke, blitzschnelle Webformulare entwerfen, erstellen und bereitstellen können.

Der AEM Forms Edge Delivery Service hilft Ihnen bei Folgendem:

* **Gestaltete visuell verblüffende Formulare**: Entdecken Sie die bunten, Cookie-Cutter-Designs und fesseln Sie Benutzer mit dynamischen, modernen Formularen, die Ihre Markenidentität widerspiegeln. Nutzen Sie vorgefertigte Komponenten oder erstellen Sie eigene benutzerdefinierte Komponenten, um Ihre Vision schnell und einfach umzusetzen.

* **Erstellen von Formularen mit perfektem Leuchtturm-Ergebnis**: Erstellen Sie Formulare, die schnell geladen und gerendert werden, selbst bei langsamen Internetverbindungen. Schnellere Ladezeiten und optimiertes Benutzererlebnis tragen zu höheren Formularabschlussraten und verbesserten Konversionsraten bei.

* **Vereinfachen Sie Authoring und Übermittlung**: Erstellen Sie Formulare mit vertrauten Tools wie Microsoft Excel oder Google Tabellen anstelle der herkömmlichen Authoring-Umgebungen. Senden Sie Formulare direkt an Ihre Microsoft Excel- oder Google Tabellen und verwenden Sie ihr Ökosystem, um die übermittelten Daten einfach zu verarbeiten.

## Erste Schritte mit dem AEM Forms Edge Delivery Service

<div>

<style>
    .card-container {
        width: calc(33% - 10px);
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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Erstellen eines Formulars mit Formularen mit Formularen" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formular erstellen</b>
        </a>
        <p>Erstellen Sie Formulare, die schnell und automatisch auf Mobilgeräten geladen und wiedergegeben werden.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Hinzufügen von Überprüfungen zu Formularfeldern" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Feldvalidierungen anwenden</b>
        </a>
        <p>Reduzieren Sie Fehler und Frustration, indem Sie die Formulareingaben auf korrekte Formatierung überprüfen.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/form-fragments.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Formularfragmente in einem EDS-Formular verwenden" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formularfragmente erstellen</b>
        </a>
        <p>Verwenden Sie vorkonfigurierte Fragmente über mehrere Formulare hinweg erneut.</p>
    </div>
    <!-- Repeat the same structure for other cards -->

<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: -5px;">
  <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
          <img src="/help/edge/assets/smock_abc_18_n.svg" alt="EDS-Formular übersetzen" style="border-radius: 5px;"> </b>
          <br><b style="margin-top: 5px;">Formular übersetzen</b>
      </a>
      <p>Erweitern Sie die Reichweite Ihrer Formulare, während Sie die Kosten im Auge behalten.</p>
  </div>
  <div class="card-container">
      <a href="/help/edge/docs/forms/style-theme-forms.md">
          <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Stile oder Designs auf ein Formular anwenden" style="border-radius: 5px;"> </b>
          <br><b style="margin-top: 5px;">Anpassen eines Designs</b>
      </a>
      <p>Erstellen Sie ein konsistentes Markenbild, indem Sie dasselbe Design auf alle Formulare anwenden.</p>
  </div>
  <div class="card-container">
    <a href="/help/edge/docs/forms/repeatable-forms.md">  
      <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Wiederholbare Abschnitte zu einem EDS-Formular hinzufügen" alt="Formularfragmente in einem EDS-Formular verwenden" style="border-radius: 5px;"> </b>
          <br><b style="margin-top: 5px;">Wiederholbare Abschnitte hinzufügen</b>
      </a>
      <p>Erstellen und fügen Sie mühelos wiederholbare Abschnitte zu einem Formular hinzu.</p>
  </div>
</div>
<!-- Repeat the same structure for other cards -->

<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: -5px;">
  <div class="card-container">
    <a href="/help/edge/docs/forms/custom-components-forms.md"> 
      <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Erstellen benutzerdefinierter Formularkomponenten mit standardmäßigem JavaScript und CSS"  style="border-radius: 5px;"> </b>
          <br><b style="margin-top: 5px;">Erstellen benutzerdefinierter Komponenten</b>
      </a>
      <p>legen Sie standardmäßige JavaScript- und CSS-Elemente fest, um Komponenten und Designs zu erstellen.</p>
  </div>
  <div class="card-container">
    <a href="/help/edge/docs/forms/recaptacha-forms.md">  
      <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Verwenden von reCAPTCHA in einem EDS-Formular" style="border-radius: 5px;"> </b>
          <br><b style="margin-top: 5px;">reCAPTCHA verwenden</b>
      </a>
      <p>Verwenden Sie die OOTB reCAPTCHA-Integration für einen robusten Spam- und Bot-Schutz.</p>
  </div>
  <div class="card-container">
    <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
      <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Formular senden" alt="Formularfragmente in einem EDS-Formular verwenden" style="border-radius: 5px;"> </b>
          <br><b style="margin-top: 5px;">Formular an Tabelle senden</b>
      </a>
      <p>Senden Sie Formulare direkt an Ihre Microsoft Excel- oder Google Tabellen.</p>
  </div>
</div>
</div>

</br>

<!-- 
<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 5px;">
    <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
       <a href="/help/edge/docs/forms/create-forms.md"> <img src="/help/edge/assets/smock_devices_18_n.svg"alt="Create a form using eds forms" style="width: 75px, Height: 50px; border-radius: 5px;"> 
        <b style="margin-top: 10px;"> Create a form</b> </a>
        <p> Create forms that that load and render quickly and automatically reflows on mobile devices.</p> <a href="/help/edge/docs/forms/create-forms.md"> </a>
    </div>
    <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
        <a href="/help/edge/docs/forms/validate-forms.md"> <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Add validations to form fields" style="width: 75px, Height: 50px; border-radius: 5px;"> 
        <b style="margin-top: 10px;">Apply field validations</b> </a>
        <p>Reduce errors and frustration by checking form inputs for proper formatting.</p>
    </div>
    <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
        <a href="/help/edge/docs/forms/form-fragments.md">  <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Use Form Fragments in an EDS Form" style="width: 75px, Height: 50px; border-radius: 5px;"> 
        <b style="margin-top: 10px;">Create form fragments</b> </a>
        <p>Reuse preconfigured fragments across multiple forms.</p>
    </div>
    <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
        <a href="/help/edge/docs/forms/translate-forms.md">  <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an EDS Form" style="width: 75px, Height: 50px; border-radius: 5px;"> 
        <b style="margin-top: 10px;">Translate a form </b> </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
        <a href="/help/edge/docs/forms/style-theme-forms.md">  <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an eds form" style="width: 75px, Height: 50px; border-radius: 5px;"> 
        <b style="margin-top: 10px;">Customize a theme</b> </a>
        <p>Create a consistent brand image by applying same theme across forms. </p>
    </div>
    <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an EDS Form" style="width: 75px, Height: 50px; border-radius: 5px;"> 
        <b style="margin-top: 10px;">Add repeatable sections</b> </a>
        <p>Effortlessly create and add repeatable sections to a form.</p>
    </div>
   <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
         <a href="/help/edge/docs/forms/custom-components-forms.md"> <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Create custom forms components using standard JavaScript and CSS" style="width: 75px, Height: 50px; border-radius: 5px;">  
        <b style="margin-top: 10px;">Create custom components</b> </a>
        <p>Use standard JavaScript and CSS to create components and themes.</p>
    </div>
    <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
         <a href="/help/edge/docs/forms/recaptacha-forms.md">  <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an EDS Form" style="width: 75px, Height: 50px; border-radius: 5px;"> 
        <b style="margin-top: 10px;">Use reCAPTCHA</b> </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>
        <div style="width: 30%; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; padding: 10px; box-sizing: border-box;">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" style="width: 75px, Height: 50px; border-radius: 5px;"> 
        <b style="margin-top: 10px;">Submit form to spreadsheet</b> </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
    
</div>

-->








