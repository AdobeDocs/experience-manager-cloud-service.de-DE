---
title: Übersicht über den AEM Forms Edge-Bereitstellungsdienst
description: AEM Forms Edge Delivery Service wurde für optimale Leistung entwickelt und ermöglicht es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e8fbe3efae7368c940cc2ed99cc9a352bbafbc22
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 2%

---


# AEM Forms Edge Delivery Service

Mit dem Adobe Edge Delivery Service können Sie Formulare optimieren und höhere Abschlussraten erzielen. Mit diesem leistungsstarken, zusammenstellbaren Dienst können Sie Formulare auf Unternehmensebene mit außergewöhnlicher Leistung und visueller Attraktivität erstellen. AEM priorisiert sowohl das Anwendererlebnis als auch Ihre Geschäftsziele, gewährleistet blitzschnelle Ladezeiten und erhöhte Formularabschlüsse.

Der Service bietet folgende Möglichkeiten:

* **Captivate von Benutzern mit atemberaubenden Formularen**: Erstellen Sie komplexe und ansprechende Formulare mit einer Bibliothek vordefinierter Komponenten. Integrieren Sie einfach reCAPTCHA, senden Sie Formulare direkt per E-Mail und ermöglichen Sie nahtlose Dateiuploads, um Speicherlösungen wie Sharepoint, Azure Storage und Amazon S3 zu sichern. Erstellen Sie sogar eigene benutzerdefinierte Formularkomponenten, um Ihre einzigartige Vision zum Leben zu erwecken.

* **Erstellen von digitalen Registrierungserlebnissen mit Tools Ihrer Wahl**: Erhöhen Sie die Authoring-Effizienz durch Entkopplung der Inhaltsquellen. Sie können standardmäßig sowohl dokumentbasiertes Authoring (Microsoft 365 und Google Workspace) als auch AEM Authoring (AEM Editoren) verwenden. Daher können Sie mit mehreren Inhaltsquellen auf derselben Website arbeiten und Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen oder Adaptive Forms Editor verwenden.

* **Formulare mit perfektem Lighthouse-Wert erstellen**: Erstellen Sie Formulare, die schnell geladen und gerendert werden, selbst bei langsamen Internetverbindungen. Schnellere Ladezeiten und optimiertes Benutzererlebnis tragen zu höheren Formularabschlussraten und verbesserten Konversionsraten bei.

  <div>
    <style>
    .image-container {
    width: 80%;
    text-align: center; 
    }
    .image-container img {
        width: 70%; /* Set image width to 70% of the container */
        border: .5px solid; /* Maintain the border style */
        padding: 15px; /* Maintain the padding */
    }
</style>
    <div class="image-container">
    <img src="/help/edge/assets/eds-forms-key-features.png" alt="Wichtige Funktionen von EDS Forms">
    </div>


</div>
&lt;!— &gt; **Captivate-Benutzer mit atemberaubenden Formularen*: Erstellen Sie komplexe und ansprechende Formulare mit Leichtigkeit mithilfe einer Bibliothek vordefinierter Komponenten. Integrieren Sie einfach reCAPTCHA, senden Sie Formulare direkt per E-Mail und ermöglichen Sie nahtlose Dateiuploads, um Speicherlösungen wie Sharepoint, Azure Storage und Amazon S3 zu sichern. Erstellen Sie sogar eigene benutzerdefinierte Formularkomponenten, um Ihre einzigartige Vision zum Leben zu erwecken.

    ![Registrierungsformulare](/help/edge/assets/enrollment-form.png)

* **Erstellen von Formularen mit perfektem Leuchtturm-Ergebnis**: Erstellen Sie Formulare, die schnell geladen und gerendert werden, selbst bei langsamen Internetverbindungen. Schnellere Ladezeiten und optimiertes Benutzererlebnis tragen zu höheren Formularabschlussraten und verbesserten Konversionsraten bei.

  ![perfekte Leuchtturmbewertung für Ihre Formulare](/help/edge/assets/lighthouse-forms.png)

* **Erstellen von digitalen Registrierungserlebnissen mit Tools Ihrer Wahl**: Erhöhen Sie die Authoring-Effizienz durch Entkopplung der Inhaltsquellen. standardmäßig sowohl AEM-Authoring als auch dokumentbasiertes Authoring verwenden. Daher können Sie mit mehreren Inhaltsquellen auf derselben Website arbeiten und Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen oder AEM Editoren verwenden.

  ![Bearbeitungswerkzeuge für Edge-Formulare](/help/edge/assets/edge-delivery-forms-authoring-tools.png)

<!--
* **Measure customer impact and deliver effective forms**: Use our RUM dashboards to visualize form performance and identify areas for improvement. Experiment with different versions and continuously optimize your forms for maximum effectiveness, ensuring you capture the data you need and drive better business outcomes.

* **Use Integrated services:** Use integrated services to streamline and empowers your users with a one-stop shop for managing their digital enrollment journeys. Use e-signatures, automated workflows, document of record (DoR), and seamless data integration, simplify the entire digital enrollment process, accelerate approvals, and optimizes your business workflows. 

    
>[!NOTE]
    >
    >
    > WYSIWYG authoring capability, integrated services, and customer impact measuring features are available under early adopter program. You can write to aem-forms-early-adopter-program@adobe.com from your official email id to join the early adopter program and request access to the capability.

    -->

## Schlüsselfunktionen

* **HTML5-basierte Formularfeldkomponenten**: Mit dem AEM Forms Edge Delivery Service können Sie benutzerfreundliche und interaktive Formulare mithilfe von Formularfeldern erstellen, die auf einer gültigen HTML5 basieren. [Eingabetypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, und <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a>  Komponenten. Diese Komponenten decken unterschiedliche Arten der Datenerfassung ab und können einfach an Ihre spezifischen Anforderungen angepasst werden.

* **Zugänglichkeit**: Auf die Felder im Formularblock kann zugegriffen werden. Jede Bezeichnung ist mit dem entsprechenden Eingabeelement verknüpft und IDs werden automatisch für die Verknüpfung generiert. Mit Feldern verknüpfte Beschreibungen werden über das Attribut aria-describedby verknüpft. Die Tastaturnavigation mit den standardmäßigen Tabulator-/Umschalt- und Tabulatortasten wird unterstützt.

* **Formularregeln**: Erstellen Sie eine Logik, die die Sichtbarkeit, Validierung und das Verhalten von Feldern basierend auf Benutzereingaben oder vordefinierten Bedingungen anpasst. Regeln bieten eine flexible und intuitive Möglichkeit, intelligente Formulare hinzuzufügen, um sicherzustellen, dass sie sich nahtlos an Benutzereingaben anpassen.

* **Datei-Uploads**: Verbessern Sie Ihre Formulare mit nahtlosen Dateianlagenfunktionen. Unabhängig davon, ob Sie Dokumente, Bilder oder andere Dateien von Ihren Benutzern erfassen müssen, ermöglicht Ihnen der Block für adaptive Formulare die mühelose Integration der Funktionen zum Hochladen von Dateien. Mit den verfügbaren benutzerdefinierten Bearbeitungsoptionen können Sie den Datei-Upload-Prozess an Ihre spezifischen Anforderungen anpassen.

* **Formularüberprüfung**: Vor der Übermittlung wird das Formular validiert und ungültige Felder werden entsprechend mit Fehlermeldungen markiert, die dem Benutzer angezeigt werden. Für die Anzeige dieser Fehler stehen verschiedene Muster zur Verfügung.

* **Formatieren von Forms**: Jedes Formularfeld verfügt über eine feste HTML-Struktur, die mithilfe benutzerdefinierter CSS- oder JavaScript-Dateien weiter dekoriert werden kann. Selektoren für Zielgruppenfelder in CSS/JS werden basierend auf Typ und Name bereitgestellt.


## Erstellen von Formularen

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
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Formular senden" alt="Formularfragmente in einem EDS-Formular verwenden" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formular an Tabelle senden</b>
        </a>
        <p>Senden Sie Formulare direkt an Ihre Microsoft Excel- oder Google Tabellen.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Stile oder Designs auf ein Formular anwenden" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Anpassen eines Designs</b>
        </a>
        <p>Erstellen Sie ein konsistentes Markenbild, indem Sie dasselbe Design auf alle Formulare anwenden.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Hinzufügen von Überprüfungen zu Formularfeldern" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Feldvalidierungen anwenden</b>
        </a>
        <p>Reduzieren Sie Fehler und Frustration, indem Sie die Formulareingaben auf korrekte Formatierung überprüfen.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Verwenden Sie Regeln, um einem Formular dynamisches Verhalten hinzuzufügen" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Verwenden Sie Regeln, um einem Formular dynamisches Verhalten hinzuzufügen</b>
        </a>
        <p>Verwenden Sie vorkonfigurierte Fragmente über mehrere Formulare hinweg erneut.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="EDS-Formular übersetzen" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formular übersetzen</b>
        </a>
        <p>Erweitern Sie die Reichweite Ihrer Formulare, während Sie die Kosten im Auge behalten.</p>
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


</div>


</br>









