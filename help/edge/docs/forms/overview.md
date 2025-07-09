---
title: Überblick über Edge Delivery Services für AEM Forms
description: Erfahren Sie, wie Sie mit Edge Delivery Services leistungsstarke Formulare mit AEM Forms erstellen und bereitstellen können, um eine schnelle Entwicklung und optimierte Datenerfassung zu ermöglichen.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 1ddf97f56e5a9b7c95959da47a748f5a6d128e43
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 8%

---


# Edge Delivery Services für AEM Forms


Edge Delivery Services für AEM Forms ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autorinnen und Autoren (neue) Formulare schnell aktualisieren, veröffentlichen und live schalten können.  Diese Dienste bieten außergewöhnliche und sehr wirkungsvolle Formularerlebnisse, die Interaktionen und Konversionen fördern. Diese Formularerlebnisse sind einfach zu erstellen und zu entwickeln.

* **Schnellere Erlebnisse:** Forms werden über ein globales Content Delivery Network (CDN) bereitgestellt, sodass sie für die Benutzer schnell geladen werden.
* **Schnelle Entwicklung:** Ein optimierter Entwicklungsprozess ermöglicht schnellere Aktualisierungen. Änderungen können veröffentlicht werden, ohne auf lange Pipeline-Builds zu warten.
* **Flexibles Authoring** Sie können aus verschiedenen Tools wählen, um Formulare zu erstellen, einschließlich dokumentbasierter Bearbeitung (Microsoft Word, Google Docs/Sheets) oder eines visuellen WYSIWYG-Editors (universeller Editor).

## Funktionsweise

Mit Edge Delivery Services können sich die Struktur und der Inhalt Ihres Formulars in Quellen wie AEM as a Cloud Service, Microsoft SharePoint oder Google Drive befinden. Diese Inhalte werden in einem globalen CDN veröffentlicht. Wenn ein Benutzer Ihre Site besucht, wird das Formular direkt vom nächsten CDN-Edge-Server bereitgestellt, um eine optimale Leistung zu erzielen.

![Vereinfachtes Architekturdiagramm, das die Inhaltsquellen, ein CDN und den Benutzer anzeigt.](/help/forms/assets/eds-simplified-architecture.png)
**Vereinfachte Edge Delivery Services-Architektur mit Forms**

Die von Benutzerinnen und Benutzern übermittelten Daten können zur weiteren Verarbeitung an verschiedene Ziele gesendet werden, von einer einfachen Tabelle bis hin zu einem leistungsstarken AEM-Backend.

## Auswählen einer Authoring-Methode

Es gibt mehrere Möglichkeiten, Formulare für Ihre Edge Delivery Services-Sites zu erstellen. Die beste Methode hängt von den Fähigkeiten Ihres Teams, der Komplexität des Formulars und Ihren Projektanforderungen ab.

![Entscheidungsbaum, der bei der Auswahl einer Methode zur Formularerstellung hilft.](/help/forms/assets/eds-authoring-selection.png)
**Entscheidungsbaum für die Formularerstellung**

### Dokumentenbasiertes Authoring

Auf diese Weise können Sie [Formulare mit Microsoft Word oder Google Docs/Sheets erstellen](/help/edge/docs/forms/create-forms.md). Formularfelder, Beschriftungen und Typen definieren Sie in einem Dokument mithilfe eines bestimmten Tabellenformats. Edge Delivery Services konvertiert dieses Dokument in ein interaktives HTML-Formular.

**Funktionen:**

* Autor in vertrauten Tools: Word-, Google Docs- oder Google-Arbeitsblättern.
* Definieren Sie Felder wie Texteingaben, E-Mail, Dropdown-Listen, Kontrollkästchen und Optionsfelder.
* Legen Sie grundlegende Validierungsregeln fest, z. B. erforderliche Felder.
* Integrieren Sie Google reCAPTCHA für den Spam-Schutz.
* Unterstützung für Datei-Uploads.
* Senden von Daten direkt an eine Tabelle oder E-Mail-Adresse.
* Erweitern Sie mit benutzerdefiniertem Code über GitHub für erweiterte Komponenten und Stile.

**Am besten geeignet für:**

* Teams, die hauptsächlich Dokumenten-Editoren für die Inhaltserstellung verwenden.
* Schnelles Erstellen einfacher bis mäßig komplexer Formulare.
* Einfache Datenerfassung in einer Tabelle oder E-Mail.

Übermittlungen von dokumentbasierten Formularen werden normalerweise vom [AEM Forms Submission Service](/help/forms/forms-submission-service.md) verarbeitet, der Daten an eine konfigurierte Tabelle oder E-Mail-Adresse weiterleitet.

### Authoring mit dem universellen Editor

Der [universelle Editor bietet eine moderne WYSIWYG-](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) zum Erstellen von Formularen per Drag-and-Drop.

**Funktionen:**

* Visuelle Formularerstellung per Drag-and-Drop mit einer Bibliothek vordefinierter Komponenten.
* Echtzeit-Validierung und komplexe Geschäftslogik konfigurieren (z. B. Felder basierend auf Benutzerauswahlen ein-/ausblenden).
* Live-Vorschau für verschiedene Geräte.
* Umfassende Integration mit AEM as a Cloud Service-Funktionen wie Inhaltsfragmenten, AEM-Workflows und Benutzerberechtigungen.
* KI-gestützte Formularerstellung und -bearbeitung über Experience Builder.

**Am besten geeignet für:**

* Erstellen komplexer Formulare mit bedingter Logik, mehrstufigen Bedienfeldern oder Personalisierung.
* Teams (z. B. Marketing-Experten, Business-Anwender), die visuelle Tools bevorzugen.
* Projekte, die eine starke Integration mit dem AEM-Backend für die Datenverarbeitung und Workflows erfordern.

Forms, das mit dem universellen Editor erstellt wurde, kann den [Forms Submission Service](/help/forms/forms-submission-service.md) verwenden oder so konfiguriert sein, dass [Übermittlungsaktionen, die vorkonfiguriert für die erweiterte Datenverarbeitung bereitgestellt werden](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) verwendet werden, z. B. das Senden von Daten an einen AEM-Workflow, einen REST-Endpunkt oder an eine Datenbank.

### Einbetten von Forms in Dokumenterstellungsseiten

[Document Authoring (DA)](https://www.aem.live/developer/da-tutorial) ist ein von Adobe gehosteter Service zur Verwaltung von Website-Inhalten für Edge Delivery Services. Auch wenn die geräteübergreifende Analyse selbst kein Tool zum Erstellen von Formularen ist, können Sie damit Web-Seiten erstellen und dann Formulare einbetten, die mit anderen Methoden erstellt wurden.

**Funktionsweise:**

1. **Formular erstellen:** Erstellen Sie Ihr Formular entweder mit dokumentbasierter Bearbeitung oder mit dem universellen Editor.
2. **Formular veröffentlichen:** Stellen Sie sicher, dass das Formular über eine eigene URL veröffentlicht wurde und zugänglich ist.
3. **In DA einbetten:** Fügen Sie auf der Seite für die Dokumenterstellung einen Block hinzu, der auf die einzubettende Formular-URL verweist.

Dieser Ansatz ist für Teams gedacht, die die Dokumenterstellung als primäres Content-Management-System für Edge Delivery Services Sites verwenden.

## Vergleich der Authoring-Methode

| Kriterien | Dokumentenbasiertes Authoring | Universeller Editor (WYSIWYG) | Forms in der Dokumenterstellung (Document Authoring, DA) |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **Primäres Authoring-Tool** | Word/Google Docs/Sheets | Browser (universeller AEM-Editor) | Nicht zutreffend (Forms sind *eingebettet*) |
| **Team-Qualifikationsstufe** | Vertrautheit mit Dokumenteditoren | Komfortabel mit visuellen Web-Tools | Verwendet DAM für Seiteninhalte |
| **Typische** | Einfach bis mäßig | Mittelmäßig bis komplex, Enterprise-Klasse | Hängt vom eingebetteten Formular ab |
| **Übermittlungsoptionen** | Forms Submission Service (an Blatt/E-Mail) | Forms Submission Service, AEM Publish (Workflow, Formulardatenmodell, Integrationen von Drittanbietern) | Folgt dem Setup des eingebetteten Formulars |
| **AEM Backend-Integration** | Minimal | Hoch (mit AEM Publish-Übermittlung) | Indirekt über das eingebettete universelle Editor-Formular |
| **Am besten geeignet für…** | Schnelle Erstellung einfacher Formulare durch Content-Teams, schnelle Datenerfassung. | Marketer und Business-Anwender, die visuelle Kontrolle, komplexe Formulare oder eine tief greifende AEM-Integration benötigen. | Sites, bei denen primärer Inhalt in DAM verwaltet wird. |

<!-- 
## Detailed Feature Comparison

| **Capability**                        | **Universal Editor (WYSIWYG)** | **Document-based Authoring** | **Document Authoring (DA)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Unified Composition with Sites**    | ✅                            |                              | ✅ (with embedded forms)     |
| **Embedding Form Support**            | ✅                            | ✅                          | ✅ (embed from Universal Editor or Docs)   |
| **Rules (Dynamic Behavior)**          | Advanced rules editor with custom functions | Limited: Show/hide, compute value, custom functions | Depends on embedded form     |
| **Attachment Support**                | ✅                            | ℹ️ (Early Access)           | Depends on embedded form     |
| **CAPTCHA Support**                   | reCAPTCHA Enterprise          | reCAPTCHA Enterprise       | Depends on embedded form     |
| **Submission Features**               | REST, Email, FDM, Workflow, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion (EA) | Only Spreadsheet            | Follows embedded form's setup |
| **Data Schema**                       | FDM, Custom                   | Custom                      | Based on embedded form       |
| **Pre-fill**                          | 💡 (via Wizard)               | ✅                          | Depends on embedded form     |
| **Fragments**                         | ✅                            | ✅                          | Depends on embedded form     |
| **Visual Rule Editor**                | ✅                            |                              |                              |
| **Localization**                      | 💡 (via Sites)                | ℹ️ (Excel/Sheets manual)    | Depends on embedded form     |
| **Template Support**                  | Only Initial Content          |                              |                              |
| **Theme**                             | ℹ️ (at project level)         | ℹ️ (at project level)        | ℹ️ (based on hosting site)    |
| **Custom Component**                  | ✅                            | ✅                          | ✅ (if embedded component supports it) |
| **Experimentation**                   | ✅                            | ✅                          | Depends on embed context     |
| **Submit Action**                     | ✅                            | Only Spreadsheet            | Based on embedded form       |
-->



## Nächste Schritte

* [Erstellen eines Formulars mit dokumentbasierter Bearbeitung](/help/edge/docs/forms/tutorial.md)
* [Erfahren Sie mehr über den universellen Editor für Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Konfigurieren von Formularübermittlungsaktionen](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
* [Informationen zur Dokumenterstellung (Document Authoring, DA)](https://www.aem.live/developer/da-tutorial)
