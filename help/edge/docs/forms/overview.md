---
title: Überblick über Edge Delivery Services für AEM Forms
description: Edge Delivery Services für AEM Forms
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: ht
source-wordcount: '1033'
ht-degree: 100%

---

# Edge Delivery Services für AEM Forms


Edge Delivery Services für AEM Forms ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autorinnen und Autoren (neue) Formulare schnell aktualisieren, veröffentlichen und live schalten können.  Diese Dienste bieten außergewöhnliche und sehr wirkungsvolle Formularerlebnisse, die Interaktionen und Konversionen fördern. Diese Formularerlebnisse sind einfach zu erstellen und zu entwickeln.

Diese Dienste ermöglichen Ihnen Folgendes:

* **Erstellen von Registrierungserlebnissen mit den Tools Ihrer Wahl**: Erhöhen Sie die Effizienz beim Authoring durch Entkopplung der Inhaltsquellen. Sie können standardmäßig dokumentenbasiertes Authoring (Microsoft SharePoint und Google Drive) und WYSIWYG-Authoring (universeller Editor oder Editor für adaptive Formulare) verwenden. Sie können mit mehreren Inhaltsquellen auf derselben Formular-Site arbeiten und Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen, den universellen Editor oder den Editor für adaptive Formulare verwenden.

* **Bereitstellen außergewöhnlicher digitaler Registrierungserlebnisse:** Stellen Sie digitale Registrierungserlebnisse bereit, die schnell und kontinuierlich geladen und gerendert werden, und überwachen Sie die Leistung von Formularen durch eine betriebliche Telemetrie. Schnellere Ladezeiten und ein optimiertes Anwendererlebnis tragen zu höheren Formularabschluss- und Konversionsraten bei.

* **Verwenden eines benutzerfreundlichen Toolsets:** Edge Delivery Services für AEM Forms
verwendet einfaches HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse zu erstellen und so die steile Lernkurve eines bestimmten Frameworks zu vermeiden. Entwickelnde mit grundlegenden Kenntnissen in der Webentwicklung können Formularkomponenten und Erlebnisse anpassen und problemlos erstellen. Es ist nicht erforderlich, auf die Ausführung einer Pipeline zu warten. Checken Sie einfach Ihren Code in GitHub ein und Ihre Änderungen sind live.

## Überblick über Edge Delivery Services für AEM Forms {#edge-overview}

Edge Delivery Services für AEM Forms ermöglicht eine hohe Flexibilität bei der Erstellung von Formularen auf Ihrer Website. Sie können Inhalte und Formulare mit [WYSIWYG-Authoring](/help/forms/creating-adaptive-form-core-components.md) ebenso wie mit [dokumentenbasiertem Authoring](/help/edge/docs/forms/create-forms.md) erstellen. Edge Delivery Services für AEM Forms
stellt einen Formularblock (auch als [adaptiver Formularblock](/help/edge/docs/forms/create-forms.md) bezeichnet) bereit, um Ihrer Edge Delivery Services-Site ein Formular hinzuzufügen.

Sie können beispielsweise Formulare direkt in Microsoft Excel oder Google Tabellen erstellen, und diese Tabellen werden in Formulare für Ihre Website umgewandelt. Alle neuen Formulare oder Formularinhalte, wie z. B. ein neues Formularfeld, stehen sofort auf Ihrer Website zur Verfügung, ohne dass ein Neuerstellungsprozess erforderlich ist.

Das folgende Diagramm zeigt, wie Sie Inhalte in Microsoft Excel oder Google Tabellen (dokumentbasiertes Authoring) bearbeiten und mit Edge Delivery Services veröffentlichen können. Es zeigt auch die AEM-Veröffentlichungsmethode mit WYSIWYG-Authoring (universeller Editor oder Editor für adaptive Formulare).

![Veröffentlichen in Edge Delivery Services und AEM](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)

Edge Delivery Services für AEM Forms nutzt GitHub, damit Kundinnen und Kunden Code direkt über ihr GitHub-Repository verwalten und bereitstellen können. Sie können beispielsweise Formulare entweder in [Google Tabellen](/help/edge/docs/forms/create-forms.md) oder [Microsoft Excel](/help/edge/docs/forms/create-forms.md) schreiben und die Komponenten Ihrer Formulare können mithilfe von CSS und JavaScript in einem GitHub-Repository entwickelt werden.

Wenn Ihre Formulare bereit sind, können Sie [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content) verwenden, eine Chrome-Browser-Erweiterung, um Inhaltsaktualisierungen in der Vorschau anzuzeigen und zu veröffentlichen.

![Installieren von AEM Sidekick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

Die Wahl zwischen [dokumentenbasiertem Authoring](#document-based-authoring-features) und [WYSIWYG-Authoring](#wysiwyg-authoring-features) hängt von Ihren spezifischen Anforderungen ab:

* Für einfache Formulare, die nur grundlegende Informationen mit einigen Feldern erfassen (denken Sie an Formulare, Formulare zur Lead-Generierung oder Formulare für Service-Anfragen) und in denen Sie eine schnelle Datenkonnektivität mithilfe einer Tabelle benötigen, ist das [dokumentbasierte Authoring](#document-based-authoring-features) gut geeignet. Sie können diese Formulare wie ein Dokument in Google Tabellen oder Microsoft Excel erstellen.

* Bei komplexen Formularen wie Formularen, die mehrere Bereiche, komplexe Regeln und Business-Logik, Datenmanipulationen, Integrationen in externe Systeme oder optimierte Workflows mithilfe von AEM-Funktionen erfordern, ist [WYSIWYG-Authoring](#wysiwyg-authoring-features) die bessere Option.


### Wichtige Funktionen des dokumentenbasierten Authorings und des WYSIWYG-Authorings

Das dokumentenbasierte Authoring bietet eine Reihe grundlegender Funktionen, während das WYSIWYG-Authoring zusätzliche Funktionen bietet, die über das dokumentenbasierte Authoring hinausgehen. So können Sie komplexere und interaktive Formulare erstellen. Die wichtigsten Funktionen des dokumentenbasierten Authorings und des WYSIWYG-Authorings sind:

#### Funktionen des dokumentbasierten Authorings

Mit dem dokumentbasierten Authoring können Sie Formulare mit vertrauten Tools wie Microsoft Excel oder Google Tabellen erstellen. Diese Formulare bieten die folgenden Funktionen:

* Barrierefreie Komponenten für ein benutzerfreundliches Erlebnis.
* Standardisierte HTML-Struktur für konsistentes Rendern.
* Regeln und Überprüfungen zur Gewährleistung der Datengenauigkeit.
* Optionen für Dateianhänge zum Erfassen zusätzlicher Informationen.
* Google reCAPTCHA-Integration für den Spam-Schutz.
* Möglichkeit zur Erstellung benutzerdefinierter Formularkomponenten für bestimmte Anforderungen.
* Übermitteln Sie Formulardaten direkt an Microsoft Excel oder Google Tabellen oder E-Mail-Adressen.
* Überwachen der Formularleistung durch betriebliche Telemetrie

#### Funktionen des WYSIWYG-Authorings

Das WYSIWYG-Authoring bietet WYSIWYG-Schnittstellen (den universellen Editor und den Editor für adaptive Formulare) zum Erstellen von Formularen. Es bietet alle Funktionen des dokumentenbasierten Authorings sowie eine Vielzahl zusätzlicher Funktionen:

* Erweiterter Regeleditor zum Erstellen einer komplexen Logik.
* Server-seitige Erweiterbarkeit für benutzerdefinierte Funktionen.
* WYSIWYG-Bearbeitungserlebnis für einfache Formularerstellung und -visualisierung.
* Dokument der Datensatzfunktionalität zum Erstellen fälschungssicherer Archive übermittelter Daten.
* Integration in Adobe Sign für elektronische Signaturen.
* Integration in Adobe Workfront Fusion, um bei der Formularübermittlung Adobe Workfront Fusion-Szenarien auszulösen.
* Integration in verschiedene Datenquellen zum Vorausfüllen von Formularen und zum Übermitteln von Daten.
* Formulardatenmodell (FDM) zum Definieren der Datenstruktur und der Interaktionen mit verschiedenen Datenquellen.
* Möglichkeit zur Wahl zwischen mehreren Sendeaktionen für die Verarbeitung von Formularübermittlungen, darunter die Übermittlung von Daten an Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics und viele weiteren Datenquellen.

Alle oben genannten Funktionen sind auch über den Editor für adaptive Formulare verfügbar.

Im Wesentlichen baut das WYSIWYG-Authoring (universeller Editor und [Editor für adaptive Formulare](/help/forms/creating-adaptive-form-core-components.md)) auf der Grundlage des [dokumentenbasierten Authorings](/help/edge/docs/forms/create-forms.md) auf, mit einem erweiterten Toolkit für die Erstellung und Verwaltung komplexer Formulare.

>[!NOTE]
>
>
> Die WYSIWYG-Authoring-Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Wenn Sie Interesse haben, senden Sie eine kurze E-Mail von Ihrer Arbeitsadresse an aem-forms-ea@adobe.com, um Zugriff auf die Funktion anzufordern.

### Edge Delivery Services für AEM Forms

: Erstellen, Veröffentlichen und Übermitteln von Formularen

Die folgenden Diagramme zeigen den Prozess des Erstellens, Veröffentlichens und Übermittelns von Formularen mit dokumentenbasiertem Authoring und mit WYSIWYG-Authoring.

![Dokumentbasiertes Authoring](/help/edge/assets/document-based-authoring-workflow.png)

![WYSIWYG-Authoring](/help/edge/assets/wysiwyg-authoring-workflow.png)

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