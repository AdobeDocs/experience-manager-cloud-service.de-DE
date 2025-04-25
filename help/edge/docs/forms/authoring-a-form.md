---
title: Wie erstelle ich Formulare in AEM?
description: Erfahren Sie mehr über die verschiedenen Formularerstellungsplattformen, die in Adobe Experience Manager (AEM) verfügbar sind, und wie Sie die richtige Plattform für Ihre Anforderungen auswählen.
feature: Edge Delivery Services, Adaptive Forms, Core Components
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: f6c6b4c17482eb519fb0d4287704d775d0a5da00
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 12%

---


# Wie erstelle ich Forms in Adobe Experience Manager (AEM)?

Adobe Experience Manager (AEM) bietet eine flexible Plattform zum Erstellen ansprechender, responsiver, dynamischer und anpassungsfähiger Formulare. Es bietet eine intuitive Benutzeroberfläche und eine Vielzahl vordefinierter Komponenten zum Erstellen und Verwalten von adaptivem Forms. Forms kann je nach Ihren Anforderungen mit oder ohne Formularmodell oder Schema erstellt werden.

## Wichtige Aspekte bei der Auswahl einer Authoring-Plattform

AEM bietet mehrere Möglichkeiten zum Erstellen interaktiver und ansprechender Formulare. Beachten Sie bei der Auswahl einer Authoring-Umgebung für Formulare die folgenden Faktoren:

| ?? **Berücksichtigung** | ?? **Was fragen** |
|----------------------|--------------------|
| **Benutzerwissen** | Wer verfasst die Formulare - Entwickler, Geschäftsbenutzer oder Inhaltsautoren? |
| **Formularkomplexität** | Benötigt das Formular erweiterte Regeln, dynamische Abschnitte oder Integrationen? |
| **Wiederverwendbarkeit erforderlich** | Werden Teile des Formulars in verschiedenen Formularen oder Projekten wiederverwendet? |
| **Designflexibilität** | Benötigen Sie vollständige Kontrolle über Layout, Designs und Stil? |
| **Integrationsanforderungen** | Muss das Formular mit Datenmodellen, Workflows oder externen Systemen verbunden werden? |
| **Benutzerfreundlichkeit** | Ist die Plattform intuitiv für die technischen Fähigkeiten Ihres Teams? |
| **Leistung und Skalierbarkeit** | Wird das Formular skaliert oder in Umgebungen mit hohem Traffic verwendet? |
| **Omni-Channel-** | Wird das Formular auf Websites, in mobilen Apps, an Kiosken oder auf mehreren Kanälen verwendet? |
| **Veröffentlichungsflexibilität** | Wo werden die Formulare in AEM, Edge Delivery oder benutzerdefinierten Programmen veröffentlicht? |

## Übersicht über die Methoden zum Erstellen von Formularen in AEM

AEM unterstützt mehrere Authoring-Methoden, die jeweils für unterschiedliche Benutzeranforderungen, technische Fähigkeiten und Veröffentlichungsziele geeignet sind.

* [Foundation-Komponenten](/help/forms/create-adaptive-form-tutorial.md): Verwenden Sie Foundation-Komponenten, um herkömmliche, interaktive Formulare zu erstellen. Am besten geeignet für Formulare, die in ältere Systeme integriert sind oder auf bewährte Workflows angewiesen sind. Forms, das mit Foundation-Komponenten erstellt wurde, kann nur in AEM veröffentlicht werden und ist nicht mit Edge Delivery Services kompatibel.

* [Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md): Verwenden Sie Kernkomponenten, um moderne, responsive und skalierbare Formulare zu erstellen. Sie unterstützen Wiederverwendbarkeit, Barrierefreiheit und bessere Leistung. Forms, das mit Kernkomponenten erstellt wurde, kann sowohl in AEM als auch in Edge Delivery Services veröffentlicht werden und bietet somit plattformübergreifende Flexibilität.

* [Edge Delivery Services Forms](/help/edge/docs/forms/overview.md): Edge Delivery Services Forms verändert die Art und Weise, wie Formulare erstellt, ausgeführt und verarbeitet werden. Durch die Nutzung von Edge Delivery Services können Unternehmen schnelle, sichere und hochverfügbare digitale Formulare erstellen, die das Benutzererlebnis und die betriebliche Effizienz mit einer schnellen Entwicklungsumgebung verbessern. Sie haben zwei Möglichkeiten, Edge Delivery Services Forms zu erstellen:
   * [WYSIWYG-Authoring](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): Verwenden Sie den universellen Editor für die visuelle, Drag-and-Drop-Formularerstellung, der sich ideal für Inhaltsautoren mit eingeschränkten technischen Kenntnissen eignet. Forms, die mit dem universellen Editor erstellt wurden, werden mit Edge Delivery Services bereitgestellt, um ein schnelles, leichtes Rendern zu ermöglichen.
   * [Dokumentenbasiertes Authoring](/help/edge/docs/forms/tutorial.md): Verwenden Sie Tools wie Microsoft Excel oder Google Sheets, um Formularstruktur und -inhalt zu definieren. Diese Methode ist nützlich für Business-Anwender, die tabellengesteuerte Eingaben bevorzugen. Diese Formulare werden normalerweise über Edge Delivery Services veröffentlicht und eignen sich für einfache Anwendungsfälle mit hohem Volumen.
* [Headless-Authoring](https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service): Verwenden Sie APIs, um Formulare für ein beliebiges Frontend als JSON zu rendern, z. B. React, Angular, Mobile Apps oder Kiosks, ohne von AEM abhängig zu sein. Derzeit unterstützen nur Kernkomponenten die Headless-Bereitstellung. Headless-Formulare eignen sich ideal für Omni-Channel-Anwendungsfälle und werden unabhängig vom Seiten-Rendering von AEM genutzt, was sie flexibel für benutzerdefinierte Frontend-Bereitstellungen macht.

### Vergleichende Analyse der Authoring-Methoden für AEM-Formulare

&#x200B;Die folgende Tabelle bietet einen knappen Vergleich verschiedener Authoring-Methoden für AEM-Formulare, wobei die Ansätze, Funktionen, Veröffentlichungsoptionen und idealen Anwendungsfälle hervorgehoben werden, um Sie bei der Auswahl der für Ihre Anforderungen am besten geeigneten Methode zu unterstützen.

| **Berücksichtigung** | **Foundation-Komponenten** | **Kernkomponenten** | **Universeller Editor (WYSIWYG)** | **Dokumentenbasiertes Authoring** | **Headless-Authoring** |
|--------------------------|---------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **Ideal für** | Pflegen älterer Formulare und Workflows in AEM | Skalierbare, moderne Formulare mit komplexen Workflows und Integrationen | Erstellen von Formularen für Edge Delivery Service-Sites mit komplexen Anforderungen | Schnelles Prototyping oder einfache Formulare ohne erweiterte Übermittlungsdienste | Omni-Channel-Erlebnisse über Plattformen hinweg (Web, Mobile, Kiosks usw.) |
| **Benutzerwissen** | Entwickler, Inhaltsautoren | Entwickler, fortgeschrittene Autoren | Business-Anwender, Inhaltsautoren | Geschäftsbenutzer | Entwickler |
| **Formularkomplexität** | Grundlegende Formulare | Komplexe Formulare mit dynamischen Abschnitten | Komplexe Formulare mit benutzerdefinierten Aktionen | Einfache Formulare | Hochkomplexe, API-gesteuerte Formulare |
| **Designflexibilität** | Limited | Hoch (CSS-/JS-Anpassung) | Moderat (basierend auf Vorlagen) | Limited | Hoch (Frontend-Framework-Kontrolle) |
| **Integrationsfunktion** | Grundlegende AEM-Workflows | Erweitert (Datenmodelle, Workflows) | Integriert mit externen Systemen | Einfach (Google Sheets, Excel) | Vollständige Kontrolle über APIs |
| **Veröffentlichungsmethode** | Nur AEM | AEM und Edge Delivery Services | Edge Delivery Services | Edge Delivery Services | Beliebiges Frontend über APIs |
| **Leistung und SEO** | Standard | Im Vergleich zu Foundation-Komponenten verbessert | Hohe Google Lighthouse-Werte für schnelleres Rendering und bessere SEO | Hohe Google Lighthouse-Werte für schnelleres Rendering und bessere SEO | Hängt von der Implementierung ab |
| **Omni-Channel-** | Limited | Mittel | Mittel | Limited | Hoch |

<!--
| **Form authoring methods** | **Key Approach** | **Features** | **Publishing Method** | **Use Cases** |
|-----------------------------|------------------|--------------|-----------------------|---------------|
| **Foundation Components** | Classic AEM authoring interface designed for standard web pages. | Includes basic components like text, images, tables, and charts. Limited reuse capabilities and primarily web-based. | Published on AEM only. | Best for maintaining legacy forms and workflows within AEM. |
| **Core Components** | Provides a modern, flexible approach with high customization capabilities. | Component-based authoring within AEM, offering high customization with CSS and JS. Built around accessibility guidelines and integrated with AEM Sites. | Published on AEM and Edge Delivery Services. | Suitable for scalable, modern forms with complex workflows and integrations. |
| **Universal Editor (WYSIWYG)** | Offers a WYSIWYG interface for intuitive form creation. | Forms are designed using an intuitive drag-and-drop interface. These forms inherit look and feel from the configured Edge Delivery Services GitHub repository for the corresponding form. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for creating forms for Edge Delivery Service sites and pages, especially scenarios involving complex forms, workflows, custom actions, or integrations with external systems. |
| **Document-based Authoring** | Uses familiar tools like Google Docs and Microsoft Office for form creation. | Forms are designed using spreadsheets, with data directly submitted to Google Sheets or Microsoft Excel. These forms are faster to create and deploy. No prior knowledge of AEM is required to develop custom components and styles for these forms. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for quick prototyping or basic forms where advanced submission services are not needed. Well-suited for surveys, registration, or feedback forms requiring data storage in spreadsheets. |
| **Headless Authoring** | Enables API-driven content creation for omnichannel delivery. | Full control via frontend frameworks, allowing content delivery across various platforms through APIs. | Can be integrated with any frontend via APIs. | Ideal for omnichannel experiences across platforms, suitable for web, mobile, kiosks, and more. |-->

### Vergleich der Funktionen der Authoring-Methoden für AEM-Formulare

Die folgende Tabelle bietet einen detaillierten Vergleich der wichtigsten Funktionen der verschiedenen Authoring-Methoden für AEM-Formulare. So können Sie den für Ihre Anforderungen am besten geeigneten Ansatz auswählen&#x200B;

| **Funktion** | **Foundation-Komponenten** | **Kernkomponenten** | **Universeller Editor (WYSIWYG)** | **Dokumentenbasiertes Authoring** | **Headless-Authoring** |
|-----------------------------------------|---------------------------|---------------------|-------------------------------|-----------------------------|------------------------|
| **Einheitliche Komposition mit Sites** | ❌ | ✅ | ✅ | ❌ | ❌ |
| **Unterstützung für eingebettete Formulare** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Regeln (dynamisches Verhalten)** | Erweiterter Regeleditor mit benutzerdefinierten Funktionen | Erweiterter Regeleditor mit benutzerdefinierten Funktionen | Erweiterter Regeleditor mit benutzerdefinierten Funktionen | Eingeschränkt: Ein-/Ausblenden, Wert berechnen, benutzerdefinierte Funktionen | Eingeschränkt: Erfordert benutzerdefinierte Implementierung |
| **Anlagenunterstützung** | ✅ | ✅ | ✅ |  (EARLY ACCESS) | ❌ |
| **CAPTCHA-Unterstützung** | reCAPTCHA v2/Enterprise, hCAPTCHA (EA), Drehkreuz (EA) | reCAPTCHA v2/Enterprise, hCAPTCHA (EA) | reCAPTCHA Enterprise | reCAPTCHA Enterprise | Benutzerdefinierte Integration erforderlich |
| **Funktionen zur Übermittlung** | REST-Endpunkt, E-Mail, Formulardatenmodell (FDM), AEM-Workflow aufrufen, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | REST-Endpunkt, E-Mail, Formulardatenmodell (FDM), AEM-Workflow aufrufen, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | REST-Endpunkt, E-Mail, Formulardatenmodell (FDM), AEM-Workflow aufrufen, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion (EA) | Nur Tabellenkalkulation | Benutzerdefinierte API-Endpunkte |
| **Datenschema** | FDM, benutzerdefiniert | FDM, benutzerdefiniert | FDM, benutzerdefiniert | Benutzerdefiniert | Benutzerdefiniert |
| **Vorbefüllen** | ✅ | ✅ | ?? (über den Assistenten) | ✅ | Benutzerdefinierte Implementierung |
| **Fragmente** | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Visual Rule Editor** | ✅ | ✅ | ✅ | ❌ | ❌ |
| **Lokalisierung** | ✅ | ✅ | ?? (über Sites) |  (Excel - Manuell, Google Sheets-Funktion) | Benutzerdefinierte Implementierung |
| **Datenschema (Datenstruktur)** | ✅ | ✅ | ?? (über die UI-Erweiterung) | ❌ | Benutzerdefinierte Implementierung |
| **Vorlagenunterstützung** | ✅ | ✅ | Nur anfänglicher Inhalt, keine Richtlinie | ❌ | Benutzerdefinierte Implementierung |
| **Portal** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **DoR-Authoring** | ✅ | ✅ | ?? (via Derlina) | ❌ | ❌ |
| **DoR-Generierung** | ✅ | ✅ | ?? (FORMS-2475 Neu) | ❌ | ❌ |
| **Theme** | ✅ | ✅ |  (auf Projektebene) |  (auf Projektebene) | Benutzerdefinierte Implementierung |
| **Benutzerdefinierte Komponente** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **OOTB- und benutzerdefinierte Funktionen** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Fragmentreferenz** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Sign-Integration** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **RTL-Unterstützung** | ❌ | ✅ | ?? | ?? | Benutzerdefinierte Implementierung |
| **Experimente** | ❌ | ❌ | ✅ | ✅ | Benutzerdefinierte Implementierung |
| **Aufgabenverwaltung über Workfront** | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Personalization-Erweiterung** | ❌ | ❌ | ?? | ❌ | Benutzerdefinierte Implementierung |
| **Editoranpassung** | ❌ | ❌ | ✅ (über die UI-Erweiterung) | ❌ | Benutzerdefinierte Implementierung |
| **Übermittlungsaktion** | ✅ | ✅ | ✅ | Nur Tabellenkalkulation | Benutzerdefinierte Implementierung |


## Verwandte Artikel

* [Dokumentbasiertes Authoring mit Microsoft Excel oder Google Tabellen](/help/edge/docs/forms/create-forms.md)
* [Universeller Editor zum WYSIWYG-Authoring](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [Erstellen eines adaptiven Formulars (Foundation-Komponenten)](/help/forms/creating-adaptive-form.md)
* [Erstellen eines adaptiven Formulars (Kernkomponenten)](/help/forms/create-an-adaptive-form.md)
