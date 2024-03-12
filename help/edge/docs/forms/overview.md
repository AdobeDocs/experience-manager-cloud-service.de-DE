---
title: Übersicht über AEM Forms Edge Delivery Services
description: AEM Forms-Edge Delivery Services wurden für optimale Leistung entwickelt und ermöglichen es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 6d4b194d17cc27a6a8596825401dc723bebe7b27
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 0%

---

# AEM Forms Edge Delivery Services

AEM Forms Edge Delivery Services ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autoren neue Formulare schnell aktualisieren, veröffentlichen und starten können. Diese Dienste bieten außergewöhnliche und wirkungsvolle Formularerlebnisse, die Interaktionen und Konversionen fördern. Diese Formularerfahrungen sind einfach zu erstellen und zu entwickeln.

Diese Dienste ermöglichen Ihnen Folgendes:

* **Erstellen Sie mit Tools Ihrer Wahl ein Registrierungserlebnis:** Erhöhen Sie die Autoreneffizienz durch Entkopplung von Inhaltsquellen. Standardmäßig können Sie sowohl die dokumentbasierte Bearbeitung (Microsoft SharePoint oder Google Drive) als auch die AEM Authoring (Adaptiver Forms Editor) verwenden. Sie können mit mehreren Inhaltsquellen auf derselben Formularsite arbeiten und Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen oder Adaptive Forms Editor verwenden.

* **außergewöhnliche digitale Einschreibeerlebnisse bieten:** Bereitstellung digitaler Registrierungserlebnisse, die schnell geladen und gerendert werden. Schnellere Ladezeiten und optimiertes Benutzererlebnis tragen zu höheren Formularvervollständigungs- und Konversionsraten bei.

* **Verwenden Sie die benutzerfreundlichen Tools für Entwickler:** AEM Forms-Edge Delivery Services verwenden einfaches HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse zu erstellen und so die steile Lernkurve eines bestimmten Frameworks zu vermeiden. Entwickler mit grundlegenden Kenntnisse in der Webentwicklung können Formularkomponenten und Erlebnisse anpassen und einfach erstellen. Es ist nicht erforderlich, auf die Ausführung einer Pipeline zu warten. Checken Sie einfach Ihren Code in GitHub ein und Ihre Änderungen sind live.

## Übersicht über AEM Forms Edge Delivery Services {#edge-overview}

AEM Forms Edge Delivery services ermöglichen eine hohe Flexibilität bei der Erstellung von Formularen auf Ihrer Website. Sie können Inhalte und Formulare erstellen mit [AEM Authoring](/help/forms/creating-adaptive-form-core-components.md) sowie [Dokumentenbasiertes Authoring](/help/edge/docs/forms/create-forms.md). AEM Forms Edge Delivery Services stellt einen Formularblock bereit, der als [Adaptiver Forms-Block](/help/edge/docs/forms/create-forms.md) , um Ihrer Edge Delivery Services-Site ein Formular hinzuzufügen.

Sie können beispielsweise Formulare direkt in Microsoft Excel oder Google Tabellen erstellen und diese Tabellen werden in Formulare für Ihre Website umgewandelt. Alle neuen Formulare oder Formularinhalte, wie z. B. ein neues Formularfeld, stehen sofort auf Ihrer Website zur Verfügung, ohne dass ein Neuerstellungsprozess erforderlich ist.

Das folgende Diagramm zeigt, wie Sie Formulare in Microsoft Excel oder Google Tabellen (Dokumentenbasiertes Authoring) bearbeiten und in Edge Delivery Services veröffentlichen können. Außerdem wird die AEM Veröffentlichungsmethode mit dem adaptiven Forms-Editor (AEM Authoring) angezeigt.

![Architektur von Edge Delivery](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

AEM Forms Edge Delivery Services verwendet GitHub, damit Kunden Code direkt über ihr GitHub-Repository verwalten und bereitstellen können. Sie können beispielsweise Formulare in [Google Tabellen](/help/edge/docs/forms/create-forms.md) oder [Microsoft Excel](/help/edge/docs/forms/create-forms.md) und die Komponenten Ihrer Formulare können mithilfe von CSS und JavaScript in einem GitHub-Repository entwickelt werden.

Wenn Ihre Formulare fertig sind, können Sie die [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), eine Chrome-Browsererweiterung, um Inhaltsaktualisierungen in der Vorschau anzuzeigen und zu veröffentlichen.

![Installieren von AEM Sidekick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

Die Wahl zwischen [Dokumentenbasiertes Authoring](#document-based-authoring-features) und [AEM Authoring](#aem-authoring-features) hängt von Ihren spezifischen Anforderungen ab:

* Für einfache Formulare, die einfach grundlegende Informationen mit einigen Feldern erfassen (denken Sie an Formulare, Formulare zur Lead-Generierung oder Formulare für Serviceanfragen) und in denen Sie eine schnelle Datenkonnektivität mithilfe einer Tabelle benötigen, muss die [Dokumentenbasiertes Authoring](#document-based-authoring-features) ist gut geeignet. Sie können diese Formulare wie ein Dokument in Google Tabellen oder Microsoft Excel erstellen.

* Bei komplexen Formularen wie Formularen, die mehrere Bedienfelder erfordern, komplexen Regeln und Geschäftslogik, Datenmanipulationen, Integration in externe Systeme oder optimierte Workflows mithilfe AEM Funktionen, [AEM Authoring](#aem-authoring-features) ist eine bessere Option.


### Wichtige Funktionen der Dokumentenbearbeitung und AEM Authoring

Die dokumentbasierte Inhaltserstellung bietet eine Reihe grundlegender Funktionen und AEM Authoring bietet zusätzliche Funktionen, die über die dokumentbasierte Inhaltserstellung hinausgehen. So können Sie komplexere und interaktive Formulare erstellen. Die wichtigsten Funktionen von Document-basiertem Authoring und AEM Authoring sind:

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

AEM Authoring bietet eine WYSIWYG-Schnittstelle (Adaptiver Forms-Editor) zum Erstellen von Formularen und bietet alle Funktionen der dokumentbasierten Bearbeitung sowie eine Vielzahl zusätzlicher Funktionen:

* Erweiterter Regeleditor zum Erstellen einer komplexen Logik.
* Serverseitige Erweiterbarkeit für benutzerdefinierte Funktionen.
* WYSIWYG-Bearbeitungserfahrung für einfache Formularerstellung und -visualisierung.
* Datensatzdokumentfunktionalität zum Erstellen fälschungssicherer Archive gesendeter Daten.
* Integration mit Adobe Sign für elektronische Signaturen.
* Integration mit Adobe Workfront Fusion, um bei der Formularübermittlung Adobe Workfront Fusion-Szenarien auszulösen.
* Integration mit verschiedenen Datenquellen zum Vorausfüllen von Formularen und zum Senden von Daten.
* Formulardatenmodell zum Definieren der Datenstruktur und der Interaktionen mit verschiedenen Datenquellen.
* Möglichkeit zur Auswahl aus mehreren Sendeaktionen für die Verarbeitung von Formularübermittlungen, einschließlich der Übermittlung von Daten an Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics und vielen weiteren Datenquellen.

Im Wesentlichen [AEM Authoring](/help/forms/creating-adaptive-form-core-components.md) baut auf der Grundlage von [Dokumentenbasiertes Authoring](/help/edge/docs/forms/create-forms.md), mit einem erweiterten Toolkit für die Erstellung und Verwaltung komplexer Formulare.

>[!NOTE]
>
>
> Die AEM Authoring-Funktion ist im Rahmen des Programms für die frühe Adoptimierung verfügbar. Wenn Sie Interesse haben, senden Sie eine kurze E-Mail von Ihrer Arbeitsadresse an aem-forms-ea@adobe.com , um Zugriff auf die Funktion anzufordern.

### AEM Forms Edge Delivery Services: Authoring, Publishing und Übermittlung von Forms

Die folgenden Diagramme illustrieren den Prozess des Erstellens, Veröffentlichen und Übermittlens von Formularen mithilfe der Dokumentenbearbeitung und AEM Authoring.

![Dokumentenbasiertes Authoring ](/help/edge/assets/document-based-authoring-workflow.png)

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