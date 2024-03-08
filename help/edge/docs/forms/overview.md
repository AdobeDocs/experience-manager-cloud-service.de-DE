---
title: Übersicht über AEM Forms Edge Delivery Services
description: AEM Forms-Edge Delivery Services wurden für optimale Leistung entwickelt und ermöglichen es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 53a66eac5ca49183221a1d61b825401d4645859e
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# AEM Forms Edge Delivery Services

Optimieren Sie Formulare und steigern Sie die Abschlussraten mit Adobe AEM Forms-Edge Delivery Services. Diese leistungsstarken, zusammenstellbaren Dienste ermöglichen es Ihnen, Formulare auf Unternehmensebene mit außergewöhnlicher Leistung und visueller Attraktivität zu erstellen. AEM priorisiert sowohl das Anwendererlebnis als auch Ihre Geschäftsziele, gewährleistet blitzschnelle Ladezeiten und höhere Konvertierungen von Formularen.

Der Service bietet folgende Möglichkeiten:

* **Erstellen außergewöhnlicher Registrierungserlebnisse**: Erstellen Sie Registrierungserlebnisse, die schnell geladen und gerendert werden, selbst bei langsamen Internetverbindungen. Schnellere Ladezeiten und optimiertes Benutzererlebnis tragen zu höheren Formularabschlussraten und verbesserten Konversionsraten bei.

* **Registrierungserlebnisse mit Tools Ihrer Wahl erstellen**: Erhöhen Sie die Authoring-Effizienz durch Entkopplung der Inhaltsquellen. Standardmäßig können Sie beide **Dokumentenbasiertes Authoring** (Microsoft SharePoint oder Google Drive) und **AEM Authoring** (AEM). Daher können Sie mit mehreren Inhaltsquellen im selben Formular arbeiten und Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen oder Adaptive Forms Editor verwenden.

* **Verwenden Sie die benutzerfreundlichen Tools für Entwickler:** AEM Forms verwendet einfaches HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse ohne normalen Verwaltungsaufwand zu erstellen. Jeder Entwickler mit Grundkenntnissen von HTML, CSS und JS sollte in der Lage sein, eigene Komponenten zu erstellen, ohne dass er eine bestimmte Sprache oder ein bestimmtes Framework erlernen muss. Keine Pipeline oder Wartezeit erforderlich, checken Sie Ihren Code in Github ein und Ihre Änderungen sind live. Darüber hinaus ist keine Pipeline oder Wartezeit erforderlich, Sie können Ihren Code in Github einchecken und Ihre Änderungen sind live.


## Erstellen eines digitalen Registrierungserlebnisses

AEM Forms bietet beide **Dokumentenbasiertes Authoring** (Microsoft SharePoint oder Google Drive) und **AEM Authoring** (AEM). Sie können die [Adaptiver Forms-Block](/help/edge/docs/forms/create-forms.md) , um Ihrer Edge Delivery Services-Site ein Formular hinzuzufügen.


>[!BEGINTABS]

>[!TAB Dokumentenbasiertes Authoring]

Dokumentenbasiertes Authoring ist eine vielseitige Option, mit der einfache Formulare mit grundlegenden Funktionen erstellt werden können. Dadurch können Sie verschiedene Eingabetypen wie Textfelder, Dropdown-Menüs und Optionsfelder integrieren und so Benutzerdaten effektiv erfassen. Es bietet eine grundlegende Version von Regeln zum Hinzufügen von dynamischem Verhalten zu Formularen. Die wichtigsten Funktionen des dokumentbasierten Authoring sind:

* **[HTML5-basierte Formularfeldkomponenten](/help/edge/docs/forms/form-components.md)**: Mit AEM Forms Edge Delivery Services können Sie benutzerfreundliche und interaktive Formulare mithilfe von Formularkomponenten erstellen, die auf HTML5 basieren. [Eingabetypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, und <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a>  -Elemente. Diese Komponenten decken unterschiedliche Arten der Datenerfassung ab und können einfach an Ihre spezifischen Anforderungen angepasst werden.

* **Zugänglichkeit**: Auf die Felder im Formularblock kann zugegriffen werden. Jede Bezeichnung ist mit dem entsprechenden Eingabeelement verknüpft und IDs werden automatisch für die Verknüpfung generiert. Mit Feldern verknüpfte Beschreibungen werden über das Attribut aria-describedby verknüpft. Die Tastaturnavigation mit den standardmäßigen Tabulator-/Umschalt- und Tabulatortasten wird unterstützt.

* **[Formatierung](/help/edge/docs/forms/style-theme-forms.md)**: Jedes Formularfeld verfügt über eine feste HTML-Struktur, die einfach mit benutzerdefinierten CSS- oder JavaScript-Dateien dekoriert werden kann. Selektoren für Zielgruppenfelder in CSS und JS werden basierend auf Typ und Name bereitgestellt. Sie können einfach neue Selektoren aufgrund der standardisierten Struktur erstellen und Ihr Formular gestalten.

* **Grundlegende Regeln**: Einfaches Erstellen einer Logik, die die Sichtbarkeit, Validierung und das Verhalten von Feldern basierend auf Benutzereingaben oder vordefinierten Bedingungen anpasst. Regeln bieten eine flexible und intuitive Möglichkeit, intelligente Formulare hinzuzufügen, um sicherzustellen, dass sie sich nahtlos an Benutzereingaben anpassen.

* **Überprüfungen**: Vor der Übermittlung wird das Formular validiert und ungültige Felder werden entsprechend mit Fehlermeldungen markiert, die dem Benutzer angezeigt werden. Der adaptive Forms-Block unterstützt die gesamte von modernen Browsern unterstützte HTML-Formularüberprüfung und bietet zusätzliche Validierungsfunktionen wie Überprüfungsskript, Dateigröße, Dateityp, Gesamtdateigröße und mehr.

* **Datei-Uploads**: Sie können Ihren Formularen Dateianlagenfunktionen hinzufügen. Unabhängig davon, ob Sie Dokumente, Bilder oder andere Dateien von Ihren Benutzern erfassen müssen, bietet Ihnen die Funktion zum Hochladen von Dateien mühelos einen schnellen Einstieg. Mit den verfügbaren benutzerdefinierten Bearbeitungsoptionen können Sie den Datei-Upload-Prozess an Ihre spezifischen Anforderungen anpassen.

* **reCAPTCHA**: Profitieren Sie von der nahtlosen Integration von Google reCAPTCHA in Ihre Formulare mit unserer vordefinierten OOTB-Unterstützung. Schützen Sie Ihre Formulare vor betrügerischen Aktivitäten, Spam und Missbrauch und bewahren Sie gleichzeitig ein reibungsloses und ununterbrochenes Benutzererlebnis. Der Adaptive Forms-Block unterstützt reCaptcha V3 und reCaptcha Enterprise.

* **E-Mail-Benachrichtigung bei Formularübermittlung senden**: Beseitigen Sie den Aufwand manueller Nachbearbeitungen und sorgen Sie für eine zeitnahe Kommunikation mit unserer integrierten E-Mail-Automatisierung für Formularübermittlungen. Mit dieser integrierten Lösung können Sie relevante Parteien mühelos benachrichtigen, einschließlich der Übermittlung von Formulardaten, wenn ein Benutzer ein Formular auf Ihrer Website ausfüllt. Es sind keine komplexen Konfigurationen oder zusätzlichen Tools erforderlich - sie können nativ verwendet werden.

>[!TAB AEM Authoring]

AEM Authoring bietet zusätzliche Funktionen, die über das dokumentbasierte Authoring hinausgehen und Ihnen die Möglichkeit bieten, komplexere und interaktive Formulare zu erstellen. Zusätzlich zu den Funktionen des dokumentbasierten Authoring bietet AEM Authoring die folgenden zusätzlichen Funktionen:

* Erweiterte Regeln: Definieren Sie logikbasierte Aktionen in Ihren Formularen. Sie können Regeln verwenden, um Formularbereiche bedingt ein- oder auszublenden, Felder auf der Grundlage der Benutzereingabe vorauszufüllen und verschiedene Überprüfungen durchzuführen, um die Datenintegrität sicherzustellen.

* Serverseitige Erweiterbarkeit: Erweitern Sie die Funktionen Ihrer Formulare, indem Sie sie in die serverseitige Logik integrieren. Auf diese Weise können Sie komplexe Berechnungen durchführen, mit externen Systemen interagieren und bestimmte Aufgaben basierend auf Benutzeraktionen im Formular automatisieren.
* Optimieren von Workflows und Datenverwaltung: Nutzen Sie die AEM, um:
   * Benutzerfreundliche Formulare mit AEM Editoren erstellen.
   * Generieren Sie ein &quot;Datensatzdokument&quot;, um die gesendeten Daten sicher und fälschungssicher zu archivieren.
   * Erleichtern Sie das e-Signieren mit Adobe Sign für ein reibungsloses und sicheres Signieren.
   * Automatisieren Sie Geschäftsprozesse durch AEM Workflows und lösen Sie Aktionen basierend auf Formularübermittlungen aus.
   * Einfache Integration in verschiedene Datenquellen, sodass ein nahtloser Datenfluss und -austausch möglich sind.

>[!ENDTABS]








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
