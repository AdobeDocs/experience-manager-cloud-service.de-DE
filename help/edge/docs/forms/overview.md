---
title: Übersicht über den AEM Forms Edge-Bereitstellungsdienst
description: AEM Forms Edge Delivery Service wurde für optimale Leistung entwickelt und ermöglicht es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 4a3ebcf7985253ebca24e90ab57ae7eaf3e924e9
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 1%

---


# AEM Forms Edge Delivery Service {#aem-forms-edge-delivery-service-overview}

AEM Forms Edge Delivery Service ist ein von Adobe angebotener zusammenstellbarer Service, mit dem Sie leistungsstarke Webformulare erstellen und bereitstellen können. Der Service bietet folgende Möglichkeiten:

* **Gestaltete visuell verblüffende Formulare**: Entdecken Sie die bunten, Cookie-Cutter-Designs und fesseln Sie Benutzer mit dynamischen, modernen Formularen, die Ihre Markenidentität widerspiegeln. Nutzen Sie vorgefertigte Komponenten oder erstellen Sie eigene benutzerdefinierte Komponenten, um Ihre Vision schnell und einfach umzusetzen.

* **Erstellen von Formularen mit perfektem Leuchtturm-Ergebnis**: Erstellen Sie Formulare, die schnell geladen und gerendert werden, selbst bei langsamen Internetverbindungen. Schnellere Ladezeiten und optimiertes Benutzererlebnis tragen zu höheren Formularabschlussraten und verbesserten Konversionsraten bei.

* **Vereinfachen Sie Authoring und Übermittlung**: Nutzen Sie Authoring-Tools, mit denen Sie sich auskennen, wie z. B. Microsoft Excel oder Google Tabellen (Dokumentenbasiertes Authoring), JSON-Dateien (Headless Authoring) oder Adaptive Forms Editor (WYSIWYG Authoring), um Formulare zu entwerfen und zu erstellen. Der Dienst ist von der Inhaltsquelle entkoppelt und bietet die Flexibilität bei der Inhaltserstellung, indem Sie Ihre bevorzugten Authoring-Tools verwenden können.

  ![Bearbeitungswerkzeuge für Edge-Formulare](/help/edge/assets/edge-delivery-forms-authoring-tools.png)

  >[!NOTE]
  >
  >
  > Die WYSIWYG-Authoring-Funktion ist im Rahmen des Programms für frühe Anwender verfügbar. Sie können von Ihrer offiziellen E-Mail-ID aus an aem-forms-early-adopter-program@adobe.com schreiben, um dem frühen Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

## Erste Schritte mit den Grundlagen

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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Erstellen eines Formulars mit Formularen mit Formularen" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Erstellen eines Formulars mit Google Tabellen oder Microsoft Excel</b>
        </a>
        <p>Erstellen Sie Formulare, die schnell und automatisch auf Mobilgeräten geladen und wiedergegeben werden.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Hinzufügen von Überprüfungen zu Formularfeldern" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Feldvalidierungen anwenden</b>
        </a>
        <p>Reduzieren Sie Fehler und Frustration, indem Sie die Formulareingaben auf korrekte Formatierung überprüfen.</p>
    </div>    <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Stile oder Designs auf ein Formular anwenden" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Anpassen eines Designs</b>
        </a>
        <p>Erstellen Sie ein konsistentes Markenbild, indem Sie dasselbe Design auf alle Formulare anwenden.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="EDS-Formular übersetzen" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formular übersetzen</b>
        </a>
        <p>Erweitern Sie die Reichweite Ihrer Formulare, während Sie die Kosten im Auge behalten.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/form-fragments.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Formularfragmente in einem EDS-Formular verwenden" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formularfragmente erstellen</b>
        </a>
        <p>Verwenden Sie vorkonfigurierte Fragmente über mehrere Formulare hinweg erneut.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Wiederholbare Abschnitte zu einem EDS-Formular hinzufügen" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Wiederholbare Abschnitte hinzufügen</b>
        </a>
        <p>Erstellen und fügen Sie mühelos wiederholbare Abschnitte zu einem Formular hinzu.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Erstellen benutzerdefinierter Formularkomponenten mit standardmäßigem JavaScript und CSS"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Erstellen benutzerdefinierter Komponenten</b>
        </a>
        <p>Verwenden Sie standardmäßiges JavaScript und CSS, um Komponenten und Designs zu erstellen.</p>
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


</br>









