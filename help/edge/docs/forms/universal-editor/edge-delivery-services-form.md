---
Title: How Edge Delivery Services Forms work?
Description: This article provides information on how Edge Delivery Services Forms work. It also provides information on various form authoring platforms, including the Universal Editor and document-based authoring.
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Working of Edge Delivery Services Forms, How Edge Delivery Services Forms work?
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
exl-id: db58ce85-139a-4cc1-8e18-73da76357299
source-git-commit: bb01a76ae2bfd78ae648e91545f34f20fabebd10
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 100%

---


# Edge Delivery Services Forms

Adobe Edge Delivery Services Forms verändert die Art und Weise, wie Formulare erstellt, ausgeführt und verarbeitet werden. Durch die Nutzung von Edge Delivery Services können Unternehmen schnelle, sichere und hochverfügbare digitale Formulare erstellen, die das Benutzererlebnis und die betriebliche Effizienz mit einer schnellen Entwicklungsumgebung verbessern. Mit Edge Delivery Services Forms können Sie Konvertierungen steigern, Kosten senken und die Bereitstellung von Inhalten beschleunigen.

## Vorteile von Edge Delivery Services Forms

* **Schnellere Formularerstellung**: Erstellen Sie leistungsstarke Formulare mit einer perfekten Lighthouse-Bewertung und überwachen Sie deren tatsächliche Leistung kontinuierlich mithilfe von Real User Monitoring (RUM).

* **Optimierter Authoring-Prozess**: Verwalten Sie Inhalte aus mehreren Quellen ganz einfach, um mehr Flexibilität zu erreichen. Standardmäßig können Sie Formulare mit WYSIWYG und dokumentenbasiertem Authoring erstellen und so eine nahtlose Integration verschiedener Inhaltsformate ermöglichen.

* **Benutzerfreundlichkeit für nicht technische Benutzende**: Mit Edge Delivery Services können auch Personen ohne umfangreiche Programmierkenntnisse Formulare ganz einfach verwalten und veröffentlichen.

* **Verbessertes Benutzererlebnis**: Sie stellen schnelle Ladezeiten und reibungslose Interaktionen sicher, was den Benutzenden minimale Wartezeiten und ein intuitives Ausfüllen des Formulars ermöglicht.

* **Ausführung ohne Server**: Edge Delivery Services ermöglicht die Ausführung von Formularlogik ohne Server. Hierzu gehört Folgendes:

   * **Client-seitige Validierung**: Die Formularfeldvalidierung erfolgt auf dem Client, wodurch Roundtrip-Verzögerungen reduziert werden.

   * **Vorausfüllen und Personalisierung**: Das Vorausfüllen von Formulardaten erfolgt auf dem Client, um ein nahtloses Benutzererlebnis zu gewährleisten.

   * **Übermittlungsverarbeitung**: Formularübermittlungen werden ohne zentralen Server validiert und sicher weitergeleitet.

## Wie funktioniert Edge Delivery Services Forms?

Benutzende können Edge Delivery Services Forms mit dokumentenbasierten Authoring-Tools wie Google Drive, SharePoint oder dem universellen Editor (WYSIWYG-Authoring) erstellen und dabei die grundlegenden Stile, Verhaltensweisen und Komponenten nutzen, die im GitHub-Repository verfügbar sind. Nach der Erstellung können Edge Delivery Services Forms mithilfe des Formularübermittlungsdiensts Daten an beliebige Plattformen senden.

![Funktionsweise von Edge Delivery Services Forms](/help/edge/docs/forms/assets/eds-forms-working.png)

### Schlüsselkomponenten von Edge Delivery Services Forms

Die Hauptkomponenten von Edge Delivery Services Forms sind:

* **GitHub-Repository**: Das GitHub-Repository dient als Textbaustein für die Erstellung von Edge Delivery Services Forms. Die Formulare nutzen grundlegende Stile und Funktionen aus dem Repository und ermöglichen es Benutzenden, Anpassungen und benutzerdefinierte Komponenten zu Edge Delivery Services Forms hinzuzufügen.

* **Formularbearbeitung**: Edge Delivery Services Forms unterstützt zwei Arten der Bearbeitung: WYSIWYG- und dokumentenbasiertes Authoring. Das dokumentenbasierte Authoring ermöglicht es Benutzenden, Formulare mit vertrauten Tools wie Google Docs und Microsoft Office zu erstellen. Mit dem WYSIWYG-Authoring können Benutzende Formulare visuell mit dem universellen Editor entwerfen, wodurch es auch für Benutzende ohne technischen Hintergrund einfach ist, Formulare zu erstellen und zu verwalten. Der universelle Editor bietet ein intuitives Erlebnis bei der Formularerstellung und ermöglicht Zugriff auf zahlreiche Formularfunktionen.

* **Formularübermittlungsdienst**: Mit dem Formularübermittlungsdienst können Sie Daten aus Formularübermittlungen auf beliebigen Plattformen speichern, z. B. OneDrive, SharePoint oder Google Sheets. Dadurch wird der Zugriff auf und die Verwaltung von Formulardaten in Ihrem bevorzugten System erleichtert.

## Erstellen eines Formulars

Adobe Experience Manager bietet und unterstützt mehrere Editoren zur Formularerstellung. Sie können Folgendes verwenden:
* [Universeller Editor (zum WYSIWYG-Authoring)](#universal-editor-for-wysiwyg-authoring)
* [Microsoft Excel oder Google Tabellen (auch als dokumentbasiertes Authoring bezeichnet)](#microsoft-excel-or-google-sheets-known-as-document-based-authoring)

### Universeller Editor (zum WYSIWYG-Authoring)

Der universelle Editor ist ein vielseitiger visueller Editor mit WYSIWYG(What You See Is What You Get)-Funktion bietet, der eine intuitive Formularerstellung ermöglicht. Es wird empfohlen, beim Erstellen neuer Formulare den universellen Editor zu verwenden, da dieser ein modernes, benutzerfreundliches Design und eine praktische Drag-and-Drop-Oberfläche bietet.

Um Formulare mit dem universellen Editor zu erstellen, werden die in der AEM-Umgebung verfügbaren Edge Delivery Services-Vorlagen verwendet. Diese Formulare übernehmen ihr Look-and-Feel von den Konfigurationen im Edge Delivery Services-GitHub-Repository. [Eine Verbindung zwischen Ihrer AEM-Umgebung und dem Edge Delivery Services-GitHub-Repository](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) wird hergestellt, um die Veröffentlichung dieser Formulare in Edge Delivery Services zu ermöglichen.

Ausführliche Anweisungen zum Authoring mit dem universellen Editor finden Sie unter [Inhaltserstellung mit dem universellen Editor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring).

### Microsoft Excel oder Google Tabellen (auch als dokumentbasiertes Authoring bezeichnet)

Sie können Formulare durch dokumentbasiertes Authoring mit Microsoft Excel- oder Google Tabellen-Dateien erstellen, sodass Sie die robusten Ökosysteme und APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint nutzen können. Dieser Ansatz ist besonders nützlich, wenn es darum geht, einfache Formulare ohne erweiterte Übermittlungsdienste zu erstellen.

Um ein Formular mit Microsoft Excel oder Google Tabellen zu erstellen, [richten Sie ein AEM-Projekt mit der AEM Forms-Bausteinvorlage ein](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) und klonen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer. AEM Forms Edge Delivery bietet eine Funktion für adaptive Formularblöcke, die die Erstellung von Formularen zum Erfassen und Speichern von Daten vereinfacht. Informationen zum Erstellen und Veröffentlichen von Formularen mit einem adaptiven Formularblock in Edge Delivery Services finden Sie unter [Erstellen eines Formulars](/help/edge/docs/forms/create-forms.md).

<!--
## Adaptive Forms editors (for Core Components or foundation components based authoring)

You can author forms that are engaging, responsive and dynamic. The Adaptive Form editor provides a user-friendly wizard that allows you to quickly create Adaptive Forms. The form wizard features easy tab navigation, enabling you to select pre-configured templates for foundation or core components, themes, data models, and submission options to create a form efficiently. 

[Authoring forms with Core Components](/help/forms/creating-adaptive-form-core-components.md) allows you to leverage standardized data capture components that can be customized, reducing development time and lowering maintenance costs for digital enrollment experiences. These forms can be published using the Adaptive Forms Block on Edge Delivery Services or through the AEM Publish instance. 

[Authoring forms with Foundation Components](/help/forms/create-an-adaptive-form.md) uses classic data capture components. These forms can only be published using the AEM Publish instance. 

You can also publish forms created using Adaptive Forms Editors on Edge Delivery Services by establishing [connection between your AEM environment and the Edge Delivery Services GitHub repository](/help/edge/docs/forms/publishing-forms.md).


| **Adaptive Forms editors** | Provides a wizard-driven approach to quickly start forms authoring using templates, styling, and predefined fields. | Use these editors to create Core Components based forms or Foundation Components based forms. | These forms can be published on Edge Delivery Services or via AEM Publish instances.  | Use these editors to create Core Components based forms or Foundation Components based forms. Ideal for scenarios involving complex forms, complex workflows, custom actions, or integrations with external systems. |  



## Types of Publishing for Edge Delivery Services Forms

You can publish Edge Delivery Services Forms on one of the following:

* **Edge Delivery Services Form Submission**: Edge Delivery Services Form Submissions ensure that form interactions, including submission and data processing, are handled efficiently and securely. This enables a faster and more reliable user experience, particularly during high traffic periods. By processing form submissions at the edge, Edge Delivery Services minimizes the reliance on a centralized server.

* **AEM Publish instance**: The AEM Forms server offers a publish instance that manages the forms and related assets available to end users.
-->

### Auswählen zwischen verschiedenen Typen zur Formularerstellung

In der folgenden Tabelle sind die Funktionen und Anwendungsfälle für jeden Authoring-Editor aufgeführt, sodass Sie die richtige Wahl basierend auf Ihren Bedürfnissen und den Anforderungen an die Formularübermittlung treffen können.

| **Editor zur Formularerstellung** | **Zentraler Ansatz** | **Funktionen** | **Veröffentlichungsmethode** | **Anwendungsfälle** |
|--------|-----------|-------|-------|------------------------------------------------|
| **Dokumentenbasiertes Authoring** | Nutzt vertraute Tools wie Google Docs und Microsoft Office zur Formularerstellung. | Formulare werden mithilfe von Tabellen erstellt, wobei die Daten direkt an Google Tabellen- oder Microsoft Excel-Blätter übermittelt werden. </br> </br> Diese Formulare lassen sich schneller erstellen und bereitstellen. Sie benötigen keine AEM-Vorkenntnisse, um benutzerdefinierte Komponenten und Stile für diese Formulare zu entwickeln. | Diese Formulare werden in Edge Delivery Services veröffentlicht und haben einen sehr hohen Google Lighthouse Score. </br> </br> Dieser hohe Score führt zu schnellerem Rendern und besserer SEO. | Diese Formulare eignen sich ideal für schnelle Prototypen oder einfache Formulare, bei denen keine erweiterten Übermittlungsdienste benötigt werden. </br> </br> Sie sind für Umfragen, Registrierungen oder Feedback-Formulare geeignet, für die eine Datenspeicherung in Tabellen erforderlich ist. Diese Formulare werden in Edge Delivery Services veröffentlicht |
| **Universeller Editor**  </br> </br> Wenn Sie ein neues Formular erstellen, verwenden Sie den universellen Editor. | Bietet eine WYSIWYG-Oberfläche zur intuitiven Formularerstellung. | Formulare werden über eine intuitive Drag-and-Drop-Oberfläche entwickelt. </br> </br> Diese Formulare übernehmen das Look-and-Feel des konfigurierten Edge Delivery Services-GitHub-Repositorys für das entsprechende Formular. | Diese Formulare werden in Edge Delivery Services veröffentlicht und haben einen sehr hohen Google Lighthouse Score. </br> </br> Dieser hohe Score führt zu schnellerem Rendern und besserer SEO. | Diese Formulare sind ideal zum Erstellen von Formularen für Edge Delivery Service-Sites und -Seiten geeignet. Diese Formularszenarien umfassen komplexe Formulare, komplexe Workflows, benutzerdefinierte Aktionen oder Integrationen mit externen Systemen |

>[!NOTE]
>
>
> Sollten Funktionen im universellen Editor fehlen, die zuvor im Editor für adaptive Formulare verfügbar gewesen sind, können Sie diese per E-Mail an mailto:aem-forms-ea@adobe.com unter Angabe Ihrer offiziellen E-Mail-Adresse anfordern.

## Siehe auch

{{see-more-forms-eds}}
