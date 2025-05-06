---
title: Erstellen von Workflows in AEM?
description: Erfahren Sie mehr über die verschiedenen Formularerstellungsplattformen, die in Adobe Experience Manager (AEM) verfügbar sind, und wie Sie die richtige Plattform für Ihre Anforderungen auswählen.
feature: Edge Delivery Services, Adaptive Forms, Core Components
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: f6c6b4c17482eb519fb0d4287704d775d0a5da00
workflow-type: ht
source-wordcount: '1176'
ht-degree: 100%

---


# Wie erstelle ich Formulare in Adobe Experience Manager (AEM)?

Adobe Experience Manager (AEM) bietet eine flexible Plattform zum Erstellen ansprechender, responsiver, dynamischer und anpassungsfähiger Formulare. Es bietet eine intuitive Benutzeroberfläche und eine Vielzahl vordefinierter Komponenten zum Erstellen und Verwalten von adaptiven Formularen. Formulare können je nach Ihren Anforderungen mit oder ohne Formularmodell oder Schema erstellt werden.

## Wichtige Aspekte bei der Auswahl einer Authoring-Plattform

AEM bietet mehrere Möglichkeiten zum Erstellen interaktiver und ansprechender Formulare. Beachten Sie bei der Auswahl einer Authoring-Umgebung für Formulare die folgenden Faktoren:

| ?? **Überlegung** | ?? **Welche Fragen sollten gestellt werden** |
|----------------------|--------------------|
| **Benutzerkompetenz** | Wer erstellt die Formulare – Entwickelnde, Geschäftsbenutzende oder Inhaltsverfassende? |
| **Formularkomplexität** | Benötigt das Formular erweiterte Regeln, dynamische Abschnitte oder Integrationen? |
| **Anforderungen bezüglich Wiederverwendbarkeit** | Werden Teile des Formulars in verschiedenen Formularen oder Projekten wiederverwendet? |
| **Design-Flexibilität** | Benötigen Sie vollständige Kontrolle über Layout, Designs und Stil? |
| **Integrationsanforderungen** | Muss das Formular mit Datenmodellen, Workflows oder externen Systemen verbunden werden? |
| **Benutzerfreundlichkeit**  | Ist die Plattform intuitiv für das technische Kompetenzniveau Ihres Teams? |
| **Leistung und Skalierbarkeit** | Wird das Formular im großen Maßstab oder in Umgebungen mit hohem Traffic verwendet? |
| **Omni-Channel-Bereitstellung** | Wird das Formular auf Websites, in mobilen Apps, an Terminals oder auf mehreren Kanälen verwendet? |
| **Veröffentlichungsflexibilität** | Wo werden die Formulare in AEM, Edge Delivery oder benutzerdefinierten Programmen veröffentlicht? |

## Übersicht über die Methoden zum Erstellen von Formularen in AEM

AEM unterstützt mehrere Authoring-Methoden, die jeweils für unterschiedliche Benutzeranforderungen, technische Fähigkeiten und Veröffentlichungsziele geeignet sind.

* [Foundation-Komponenten](/help/forms/create-adaptive-form-tutorial.md): Verwenden Sie Foundation-Komponenten, um herkömmliche, interaktive Formulare zu erstellen. Am besten geeignet für Formulare, die in ältere Systeme integriert oder auf bewährte Workflows angewiesen sind. Formulare, die mit Foundation-Komponenten erstellt wurden, können nur in AEM veröffentlicht werden und sind nicht mit Edge Delivery Services kompatibel.

* [Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md): Verwenden Sie Kernkomponenten, um moderne, responsive und skalierbare Formulare zu erstellen. Sie unterstützen Wiederverwendbarkeit, Barrierefreiheit und bessere Leistung. Formulare, die mit Kernkomponenten erstellt wurden, können sowohl in AEM als auch in Edge Delivery Services veröffentlicht werden und bieten somit plattformübergreifende Flexibilität.

* [Edge Delivery Services-Formulare](/help/edge/docs/forms/overview.md): Adobe Edge Delivery Services-Formulare verändern die Art und Weise, wie Formulare erstellt, ausgeführt und verarbeitet werden. Durch die Nutzung von Edge Delivery Services können Unternehmen schnelle, sichere und hochverfügbare digitale Formulare erstellen, die das Benutzererlebnis und die betriebliche Effizienz mit einer schnellen Entwicklungsumgebung verbessern. Sie haben zwei Möglichkeiten, Edge Delivery Services-Fomulare zu erstellen:
   * [WYSIWYG-Authoring](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): Verwenden Sie den universellen Editor für die visuelle Drag-and-Drop-Formularerstellung, der sich ideal für Inhaltsverfassende mit eingeschränkten technischen Kenntnissen eignet. Formulare, die mit dem universellen Editor erstellt wurden, werden mit Edge Delivery Services bereitgestellt, um ein schnelles, leichtes Rendern zu ermöglichen.
   * [Dokumentbasiertes Authoring](/help/edge/docs/forms/tutorial.md): Verwenden Sie Tools wie Microsoft Excel oder Google Sheets, um Formularstruktur und -inhalt zu definieren. Diese Methode ist nützlich für Geschäftsbenutzende, die tabellengesteuerte Eingaben bevorzugen. Diese Formulare werden normalerweise über Edge Delivery Services veröffentlicht und eignen sich für einfache Anwendungsfälle mit hohem Volumen.
* [Headless-Authoring](https://experienceleague.adobe.com/de/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service): Verwenden Sie APIs, um Formulare für ein beliebiges Frontend als JSON zu rendern, z. B. React, Angular, mobile Apps oder Terminals, ohne von AEM abhängig zu sein. Derzeit unterstützen nur Kernkomponenten die Headless-Bereitstellung. Headless-Formulare eignen sich ideal für Omni-Channel-Anwendungsfälle und werden unabhängig vom Seiten-Rendering von AEM genutzt, was sie flexibel für benutzerdefinierte Frontend-Bereitstellungen macht.

### Vergleichende Analyse der Authoring-Methoden für AEM-Formulare

Die folgende Tabelle bietet einen kompakten Vergleich verschiedener Authoring-Methoden für AEM-Formulare, wobei die Ansätze, Funktionen, Veröffentlichungsoptionen und idealen Anwendungsfälle hervorgehoben werden, um Sie bei der Auswahl der für Ihre Anforderungen am besten geeigneten Methode zu unterstützen.

| **Überlegung** | **Foundation-Komponenten** | **Kernkomponenten** | **Universeller Editor (WYSIWYG)** | **Dokumentenbasiertes Authoring** | **Headless-Authoring** |
|--------------------------|---------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **Ideal für** | Pflegen älterer Formulare und Workflows in AEM | Skalierbare, moderne Formulare mit komplexen Workflows und Integrationen | Erstellen von Formularen für Edge Delivery Service-Sites mit komplexen Anforderungen | Schnelles Prototyping oder einfache Formulare ohne erweiterte Übermittlungsdienste | Plattformübergreifende Omni-Channel-Erlebnisse (Web, Mobile, Terminals usw.) |
| **Benutzerkompetenz** | Entwickelnde, Inhaltsverfassende | Entwickelnde, fortgeschrittene Verfassende | Geschäftsbenutzende, Inhaltsverfassende | Geschäftsbenutzende | Entwickelnde |
| **Formularkomplexität** | Grundlegende Formulare | Komplexe Formulare mit dynamischen Abschnitten | Komplexe Formulare mit benutzerdefinierten Aktionen | Einfache Formulare | Hochkomplexe, API-gesteuerte Formulare |
| **Design-Flexibilität** | Limitiert | Hoch (CSS-/JS-Anpassung) | Moderat (basierend auf Vorlagen) | Limitiert | Hoch (Frontend-Framework-Kontrolle) |
| **Integrationsfähigkeit** | Grundlegende AEM-Workflows | Erweitert (Datenmodelle, Workflows) | Integriert mit externen Systemen | Einfach (Google Sheets, Excel) | Vollständige Kontrolle über APIs |
| **Veröffentlichungsmethode** | Nur AEM | AEM und Edge Delivery Services | Edge Delivery Services | Edge Delivery Services | Beliebiges Frontend über APIs |
| **Leistung und SEO** | Standard | Verbesserung gegenüber Foundation-Komponenten | Hohe Google Lighthouse-Bewertungen für schnelleres Rendering und bessere SEO | Hohe Google Lighthouse-Bewertungen für schnelleres Rendering und bessere SEO | Abhängig von der Implementierung |
| **Omni-Channel-Bereitstellung** | Limitiert | Mittel | Mittel | Limitiert | Hoch |

<!--
| **Form authoring methods** | **Key Approach** | **Features** | **Publishing Method** | **Use Cases** |
|-----------------------------|------------------|--------------|-----------------------|---------------|
| **Foundation Components** | Classic AEM authoring interface designed for standard web pages. | Includes basic components like text, images, tables, and charts. Limited reuse capabilities and primarily web-based. | Published on AEM only. | Best for maintaining legacy forms and workflows within AEM. |
| **Core Components** | Provides a modern, flexible approach with high customization capabilities. | Component-based authoring within AEM, offering high customization with CSS and JS. Built around accessibility guidelines and integrated with AEM Sites. | Published on AEM and Edge Delivery Services. | Suitable for scalable, modern forms with complex workflows and integrations. |
| **Universal Editor (WYSIWYG)** | Offers a WYSIWYG interface for intuitive form creation. | Forms are designed using an intuitive drag-and-drop interface. These forms inherit look and feel from the configured Edge Delivery Services GitHub repository for the corresponding form. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for creating forms for Edge Delivery Service sites and pages, especially scenarios involving complex forms, workflows, custom actions, or integrations with external systems. |
| **Document-based Authoring** | Uses familiar tools like Google Docs and Microsoft Office for form creation. | Forms are designed using spreadsheets, with data directly submitted to Google Sheets or Microsoft Excel. These forms are faster to create and deploy. No prior knowledge of AEM is required to develop custom components and styles for these forms. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for quick prototyping or basic forms where advanced submission services are not needed. Well-suited for surveys, registration, or feedback forms requiring data storage in spreadsheets. |
| **Headless Authoring** | Enables API-driven content creation for omnichannel delivery. | Full control via frontend frameworks, allowing content delivery across various platforms through APIs. | Can be integrated with any frontend via APIs. | Ideal for omnichannel experiences across platforms, suitable for web, mobile, kiosks, and more. |-->

### Funktionsvergleich der Authoring-Methoden für AEM-Formulare

Die folgende Tabelle bietet einen detaillierten Vergleich der wichtigsten Funktionen der verschiedenen Authoring-Methoden für AEM-Formulare. So können Sie den für Ihre Anforderungen am besten geeigneten Ansatz auswählen.

| **Funktion** | **Foundation-Komponenten** | **Kernkomponenten** | **Universeller Editor (WYSIWYG)** | **Dokumentenbasiertes Authoring** | **Headless-Authoring** |
|-----------------------------------------|---------------------------|---------------------|-------------------------------|-----------------------------|------------------------|
| **Einheitliche Komposition mit Sites** | ❌ | ✅ | ✅ | ❌ | ❌ |
| **Unterstützung für eingebettete Formulare** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Regeln (dynamisches Verhalten)** | Erweiterter Regeleditor mit benutzerdefinierten Funktionen | Erweiterter Regeleditor mit benutzerdefinierten Funktionen | Erweiterter Regeleditor mit benutzerdefinierten Funktionen | Limitiert: Ein-/Ausblenden, Wert berechnen, benutzerdefinierte Funktionen | Limitiert: Erfordert benutzerdefinierte Implementierung |
| **Unterstützung für Anhänge** | ✅ | ✅ | ✅ | ℹ️ (Frühzeitiger Zugriff) | ❌ |
| **CAPTCHA-Unterstützung** | reCAPTCHA v2/Enterprise, hCaptcha (EA), Turnstile (EA) | reCAPTCHA v2/Enterprise, hCaptcha (EA) | reCAPTCHA Enterprise | reCAPTCHA Enterprise | Benutzerdefinierte Integration erforderlich |
| **Übermittlungsfunktionen** | REST-Endpunkt, E-Mail, Formulardatenmodell (FDM), AEM-Workflow aufrufen, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | REST-Endpunkt, E-Mail, Formulardatenmodell (FDM), AEM-Workflow aufrufen, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | REST-Endpunkt, E-Mail, Formulardatenmodell (FDM), AEM-Workflow aufrufen, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | Nur Kalkulationstabelle | Benutzerdefinierte API-Endpunkte |
| **Datenschema** | FDM, benutzerdefiniert | FDM, benutzerdefiniert | FDM, benutzerdefiniert | Benutzerdefiniert | Benutzerdefiniert |
| **Vorausfüllen** | ✅ | ✅ | ?? (über Assistenten) | ✅ | Benutzerdefinierte Implementierung |
| **Fragmente** | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Visueller Regeleditor** | ✅ | ✅ | ✅ | ❌ | ❌ |
| **Lokalisierung** | ✅ | ✅ | ?? (über Sites) | ℹ️ (Excel – manuell, Google Sheets-Funktion) | Benutzerdefinierte Implementierung |
| **Datenschema (Datenstruktur)** | ✅ | ✅ | ?? (über UI-Erweiterung) | ❌ | Benutzerdefinierte Implementierung |
| **Vorlagenunterstützung** | ✅ | ✅ | Nur anfänglicher Inhalt, keine Richtlinie | ❌ | Benutzerdefinierte Implementierung |
| **Portal** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **DoR-Authoring** | ✅ | ✅ | ?? (über Derlina) | ❌ | ❌ |
| **DoR-Generierung** | ✅ | ✅ | ?? (FORMS-2475 Neu) | ❌ | ❌ |
| **Desing** | ✅ | ✅ | ℹ️ (auf Projektebene) | ℹ️ (auf Projektebene) | Benutzerdefinierte Implementierung |
| **Benutzerdefinierte Komponente** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **OOTB und benutzerdefinierte Funktionen** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Fragmentreferenz** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Sign-Integration** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **RTL-Unterstützung** | ❌ | ✅ | ?? | ?? | Benutzerdefinierte Implementierung |
| **Experimente** | ❌ | ❌ | ✅ | ✅ | Benutzerdefinierte Implementierung |
| **Aufgabenverwaltung über Workfront** | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Personalisierungserweiterung** | ❌ | ❌ | ?? | ❌ | Benutzerdefinierte Implementierung |
| **Editoranpassung** | ❌ | ❌ | ✅ (über UI-Erweiterung) | ❌ | Benutzerdefinierte Implementierung |
| **Übermitteln-Aktion** | ✅ | ✅ | ✅ | Nur Kalkulationstabelle | Benutzerdefinierte Implementierung |


## Verwandte Artikel

* [Dokumentbasiertes Authoring mit Microsoft Excel oder Google Tabellen](/help/edge/docs/forms/create-forms.md)
* [Universeller Editor zum WYSIWYG-Authoring](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [Erstellen eines adaptiven Formulars (Foundation-Komponenten)](/help/forms/creating-adaptive-form.md)
* [Erstellen eines adaptiven Formulars (Kernkomponenten)](/help/forms/create-an-adaptive-form.md)
