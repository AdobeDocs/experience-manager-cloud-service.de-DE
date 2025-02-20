---
title: Universeller Editor für Edge Delivery Services for Forms (EDS Forms Block)
description: Verwenden Sie den universellen Editor für Edge Delivery Services for Forms (EDS Forms Block), um adaptive Formulare zu erstellen.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: d711e0d1-a2fc-4aa6-af87-6e77a7bc5d2e
source-git-commit: 7a868ddc3d13eaf3b5352e130b2026db64a02723
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 78%

---

# Universeller Editor für Edge Delivery Services for Forms (EDS Forms Block)

Der universelle Editor revolutioniert die Formularerstellung für Adobe Edge Delivery Services (EDS), indem er eine einfache, visuelle und intuitive What You See Is What You Get(WYSIWYG)-Benutzeroberfläche bereitstellt. Er wurde für Personen, die Inhalte und Formulare erstellen, entwickelt und vereinfacht die herkömmlichen komplexen Formularerstellungsprozesse, sodass er auch von Benutzenden ohne technischen Hintergrund verwendet werden kann.

Mit dem universellen Editor können Sie schnell responsive, interaktive Formulare mithilfe vorkonfigurierter Komponenten wie Textfelder, Kontrollkästchen und Optionsfelder entwerfen. Die robusten Funktionen unterstützen dynamische Regeln, eine nahtlose Datenintegration und eine erweiterte Personalisierung, sodass jedes Formular auf Ihre Bedürfnisse zugeschnitten ist.

Unabhängig davon, ob Sie nun einfaches Client-seitiges Rendern ermöglichen, Browser-übergreifende Kompatibilität sicherstellen oder strenge Barrierefreiheitsstandards befolgen, bietet der universelle Editor eine optimierte Lösung für die Erstellung und Verwaltung von Formularen.

![Universeller Editor](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center} -->

## Hauptfunktionen des universellen Editors für EDS-Formulare



Im Folgenden finden Sie das Layout mit Karten mit gleicher Breite (unter Verwendung von Spalten mit fester Breite):

| ![WYSIWYG-Schnittstelle](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg) | ![Regeleditor](/help/edge/docs/forms/universal-editor/assets/rule-editor.svg) | ![Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/assets/submit-actions.svg) |
|:-------------:|:-------------:|:-------------:|
| [**WYSIWYG-Schnittstelle**](/help/edge/docs/forms/universal-editor/universal-editor-user-interface.md) | [**Regeleditor**](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) | [**Übermittlungsaktionen**](/help/edge/docs/forms/universal-editor/submit-action.md) |
| Der universelle Editor bietet eine WYSIWYG-Benutzeroberfläche für Formularentwürfe – mit einer vorkonfigurierten Komponentenbibliothek, responsivem Design, vorlagenbasierter Erstellung und Echtzeitänderungen von Feldern. | Mit dem Regeleditor können Benutzende mithilfe ereignisgesteuerter Regeln, sofortiger Validierung und einer auf einfachem JavaScript und JSON basierenden Fehlerbehandlung dynamische Formularinteraktionen erstellen. | Übermittlungsaktionen unterstützen Backend-Integration, Logik für bedingte Übermittlungen, sichere Endpunkte sowie Präprozessoren und optimieren so Übermittlungs-Workflows. |

| ![Veröffentlichen/Rückgängigmachen der Veröffentlichung](/help/edge/docs/forms/universal-editor/assets/publish-unpublish.svg) | ![Responsiver Modus](/help/edge/docs/forms/universal-editor/assets/responsive.svg) | ![Benutzerdefinierte Komponenten](/help/edge/docs/forms/universal-editor/assets/custom-components.svg) |
|:-------------:|:-------------:|:-------------:|

| [**Veröffentlichen/Rückgängigmachen der Veröffentlichung**](/help/edge/docs/forms/universal-editor/publish-forms.md) | [**Responsiver Modus**](/help/edge/docs/forms/universal-editor/responsive-layout.md) | [**Benutzerdefinierte Komponenten**](/help/edge/docs/forms/universal-editor/create-custom-component.md) |
| Steuern Sie ganz einfach die Sichtbarkeit Ihrer Formulare - veröffentlichen Sie sie oder heben Sie ihre Veröffentlichung mit nur wenigen Klicks direkt im Editor auf. | Entwerfen von Formularen, die sich nahtlos auf allen Geräten (Desktop-PCs, Tablets und Mobilgeräte) anpassen. Verwenden Sie den responsiven Modus, um Formulare für verschiedene Bildschirmgrößen in der Vorschau anzuzeigen und zu testen. | Benutzerdefinierte Komponenten ermöglichen es Entwicklerinnen und Entwicklern, die Formularfunktionen durch die Erstellung eindeutiger Elemente zu erweitern, die auf bestimmte Anwendungsfälle im Unternehmen zugeschnitten sind. |

| ![Stile](/help/edge/docs/forms/universal-editor/assets/personalization.svg) | ![Vorbefüllungs-Services](/help/edge/docs/forms/universal-editor/assets/prefill-services.svg) | ![A/B-Tests](/help/edge/docs/forms/universal-editor/assets/experimentation-ab-testing.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Stile**](/help/edge/docs/forms/universal-editor/style-theme-forms.md) | **Vorbefüllungs-Services** (in Kürze verfügbar) | [**A/B-Tests**](https://github.com/adobe/aem-experimentation/blob/main/documentation/experiments.md) |
| Die Formatierung mit CSS ermöglicht es Entwicklerinnen und Entwicklern, das Erscheinungsbild von Formularelementen anzupassen und ein visuell ansprechendes Design zu erstellen, das mit der Ästhetik der Website übereinstimmt. | Services zum Vorausfüllen füllen Formularfelder automatisch mit relevanten Benutzerdaten aus verschiedenen Quellen auf, was weniger manuelle Eingaben erfordert und das Anwendererlebnis verbessert. | A/B-Tests ermöglichen es Unternehmen, mit verschiedenen Formularentwürfen, Layouts und Funktionen zu experimentieren, um die leistungsstärksten Varianten zu ermitteln. |

| ![Analytics und Tracking](/help/edge/docs/forms/universal-editor/assets/analyticsandtracking.svg) | ![Aufgabenverwaltung](/help/edge/docs/forms/universal-editor/assets/adobe-workfront.svg) | ![Datenbindung](/help/edge/docs/forms/universal-editor/assets/data-binding.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Analytics und Tracking**](https://www.aem.live/developer/martech-integration) | **Aufgabenverwaltung** | **Datenbindung** |
| Verschaffen Sie sich mit der integrierten Analyse- und Tracking-Funktion Erkenntnisse zum Benutzerverhalten sowie zu Formularinteraktionen und Übermittlungsraten, um eine datengesteuerte Formularoptimierung zu ermöglichen. | Durch die Integration mit Adobe Workfront können Teams Aufgaben für die Erstellung und Pflege von Formularen verwalten und so optimierte Workflows sicherstellen. | Die Datenbindung ermöglicht direkte Verbindungen zwischen Formularfeldern und Backend-Datenquellen und unterstützt Echtzeit-Updates und erweiterte Datenzuordnung. |

| ![CAPTCHA](/help/edge/docs/forms/universal-editor/assets/captcha.svg) | ![Einbetten von Forms](/help/edge/docs/forms/universal-editor/assets/embedding-forms.svg) | ![Dankeskonfiguration](/help/edge/docs/forms/universal-editor/assets/thank-you.svg) |
|:-------------:|:-------------:|:-------------:|

| **Editor-Anpassung** | **Einbetten von Forms** | [**Dankeskonfiguration**](/help/edge/docs/forms/universal-editor/submit-action.md#show-a-custom-thank-you-message-on-adaptive-form-submission-submit-action-message-ue) |
| Entwickler können die Funktionalität des Editors durch Benutzeroberflächenerweiterungen erweitern und so maßgeschneiderte Lösungen für spezifische organisatorische Anforderungen ermöglichen. | Betten Sie Formulare mithilfe der integrierten Einbettungskomponente des universellen Editors direkt in Edge Delivery Services Sites-Seiten ein. | Einfaches Anpassen der Bestätigungsmeldung oder -seite, die Benutzern nach erfolgreicher Formularübermittlung angezeigt wird. |


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

## Vorkonfigurierte Formularkomponenten

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
      <td>Verhindert Spam, indem den Benutzenden mithilfe von Google reCaptcha oder HCaptcha eine Aufgabe ausführen müssen, um zu bestätigen, dass es sich um Menschen handelt.</td>
    </tr>
    <tr>
      <td><b>Kontrollkästchen</b></td>
      <td>Ermöglicht den Benutzenden das Konfigurieren eines Kontrollkästchens.</td>
    </tr>
    <tr>
      <td><b>Kontrollkästchengruppe</b></td>
      <td>Ermöglicht den Benutzenden die Auswahl mehrerer Optionen aus einer Gruppe.</td>
    </tr>
    <tr>
      <td><b>Datumsauswahl</b></td>
      <td>Ermöglicht den Benutzenden die Auswahl eines Datums über eine Kalenderoberfläche.</td>
    </tr>
    <tr>
      <td><b>Dropdown-Liste</b></td>
      <td>Bietet Optionen zur Einzel- oder Mehrfachauswahl aus einer vordefinierten Liste.</td>
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
      <td>Zeigt ein Popup-Dialogfeld an, was häufig für Warnhinweise, zusätzliche Informationen oder eine Bestätigung verwendet wird.</td>
    </tr>
    <tr>
      <td><b>Numerisches Feld</b></td>
      <td>Erfasst numerische Eingaben und ermöglicht die Validierung von Zahlen oder Bereichen.</td>
    </tr>
    <tr>
      <td><b>Bedienfeld</b></td>
      <td>Organisiert Formularabschnitte mit erweiterbaren/ausblendbaren Bedienfeldern.</td>
    </tr>
    <tr>
      <td><b>Optionsschalter</b></td>
      <td>Aktiviert die Einzelauswahl aus einer Optionsgruppe.</td>
    </tr>
    <tr>
      <td><b>Bewertung</b></td>
      <td>Ermöglicht den Benutzenden die Angabe einer Sternebewertung.</td>
    </tr>
    <tr>
      <td><b>Schaltfläche „Zurücksetzen“</b></td>
      <td>Setzt die Formularfelder auf ihren Standardstatus zurück.</td>
    </tr>
    <tr>
      <td><b>Schaltfläche „Senden“</b></td>
      <td>Löst das Absenden von Formularen aus und initiiert definierte Workflows.</td>
    </tr>
    <tr>
      <td><b>Telefonnummernfeld</b></td>
      <td>Erfasst Telefonnummern mit Formatierung basierend auf dem Land.</td>
    </tr>
    <tr>
      <td><b>Text</b></td>
      <td>Bietet einen speziellen Abschnitt für die Anzeige rechtlicher Bedingungen und die Erfassung der Benutzerzustimmung durch Kontrollkästchen.</td>
    </tr>
    <tr>
      <td><b>Textfeld</b></td>
      <td>Erfasst einzeilige Eingaben, wie Namen oder E-Mail-Adressen.</td>
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

Um den universellen Editor und seine erweiterten Funktionen wie den Regeleditor zu aktivieren, senden Sie eine E-Mail mit Ihrer offiziellen E-Mail-ID an aem-forms-ea@adobe.com. Das Team von Adobe unterstützt Sie dabei, Ihre Formularerstellung zu transformieren.

## Häufig gestellte Fragen (FAQ)

**F. Wer kann den universellen Editor verwenden?**
Der universelle Editor wurde für eine breite Zielgruppe entwickelt, darunter:

* Inhaltserstellende, die visuell ansprechende Formulare erstellen möchten
* Entwickelnde, die erweiterte Anpassungs- und Integrationsfunktionen benötigen
* Organisationen, die sich skalierbare, sichere und konforme Formularlösungen wünschen

**F: Kann ich mit dem universellen Editor erstellte Formulare in meine bestehenden Systeme integrieren?**
Selbstverständlich. Der universelle Editor unterstützt eine nahtlose Datenbindung mit Backend-Systemen und ermöglicht so Echtzeitaktualisierungen und erweiterte Datenzuordnungen. Außerdem lässt er sich mit Tools wie Adobe Workfront zwecks Aufgaben-Management integrieren und unterstützt sichere Endpunkte für Workflows zwecks Datenübermittlung.

**F: Können die Formularkomponenten angepasst werden?**
Ja, mit dem universellen Editor können Entwickelnde benutzerdefinierte Komponenten erstellen, die auf spezifische organisatorische Anforderungen zugeschnitten sind. Darüber hinaus können Sie die Funktionalität des Editors durch Benutzeroberflächenerweiterungen und benutzerdefinierte Workflows ausweiten.

**F: Wie sieht es mit dem universellen Editor und dem Thema Barrierefreiheit aus?**
Der universelle Editor wurde unter strikter Einhaltung von Barrierefreiheitsstandards, darunter WCAG (Web Content Accessibility Guidelines), entwickelt. Dadurch wird sichergestellt, dass die Formulare für Personen mit Behinderungen nutzbar sind, was ein inklusives Erlebnis ermöglicht.

**F: Welche Art von Analysen bieten mir Formulare?**
Der universelle Editor enthält integrierte Analyse- und Tracking-Tools zur Überwachung von Benutzerinteraktionen, Formularübermittlungsraten und Konversionsmetriken. Dank dieser Erkenntnisse können Sie Ihre Formulare leistungsstärker gestalten.


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

