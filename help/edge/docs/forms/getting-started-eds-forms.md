---
title: Erste Schritte mit Forms in AEM Edge Delivery Services
description: Erfahren Sie, wie Sie in Adobe Experience Manager Edge Delivery Services leistungsstarke Formulare erstellen und bereitstellen, wobei der Schwerpunkt auf dem Authoring-Ansatz mit dem universellen Editor liegt.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%

---


# Erste Schritte mit Forms in AEM Edge Delivery Services

<span class="preview"> Dies ist eine Vorabversion-Funktion, die über unseren <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features">Vorabversionskanal</a> verfügbar ist</span>

Adobe Experience Manager (AEM) Edge Delivery Services (EDS) ermöglicht die Bereitstellung von schnellen, hochgradig skalierbaren Web-Erlebnissen direkt am Edge. In diesem Handbuch wird erläutert **wie Sie Formulare für diese Erlebnisse erstellen und** - mit einer klaren Empfehlungshierarchie:

1. **Universeller Editor (UE) - Beste Wahl für die meisten Teams**
2. **Dokumentenbasiertes Authoring (Dokumente/Blätter) - Ideal für schnelle, einfache Formulare**
3. **Dokumenterstellung (Document Authoring, DA) - Zum Einbetten von Formularen in von der DA erstellte Seiten**

Am Ende können Sie die richtige Authoring-Methode auswählen, Übermittlungsoptionen verstehen und die nächsten Schritte in Richtung produktionsbereiter Formulare ausführen.



## Auswählen einer Authoring-Methode

| Team und Anforderung | Empfohlene Methode | Warum |
|--------------------|--------------------|-----|
| Marketing-Experten und -Designer benötigen visuelle Kontrolle, Bedingungslogik oder AEM-Integrationen | **Universeller Editor** | Drag-and-Drop, erweiterte Regeln, Übermittlungen an FSS oder AEM Publish |
| Inhaltsautoren, die bereits in Word/Google Docs/Sheets arbeiten; einfache Datenerfassung in Tabellen/E-Mails | **Dokumentenbasiertes Authoring** | Bekannte Tools, schnellster Pfad für grundlegende Formulare |
| Integrierte Website-Seiten **Dokumenterstellung (Document Authoring, DA)** | **Einbetten** eines UE- oder DOC-basierten Formulars in die DA-Seite | DA erstellt keine Formulare selbst |


## Authoring-Methoden im Detail

### Universeller Editor

Der universelle Editor ist ein visuelles Drag-and-Drop-Authoring-Tool für Marketing-Experten und Designer, das Geschwindigkeit mit Leistung auf Unternehmensniveau kombiniert:

* Echtzeit-WYSIWYG-Bearbeitung und Gerätevorschau.
* Erweiterte Regeln und Validierungs-UI - kein Code erforderlich.
* Direkte Integration mit AEM-Assets, Workflows und Formulardatenmodell (FDM).
* Nahtlose Übergabe an Entwickler für benutzerdefinierte Komponenten in Vanilla JS/CSS.
* Flexible Übermittlungsziele: Beginnen Sie einfach mit dem **Forms Submission Service (FSS)** oder wechseln Sie bei **steigenden Bedarf zu** AEM-Veröffentlichungs-Übermittlungsaktionen.

> **Empfehlung** Beginnen Sie jedes neue Formularprojekt mit dem universellen Editor, es sei denn, Ihr Team ist zu 100 % dokumentzentriert und das Formular ist sehr einfach.


### Dokumentenbasiertes Authoring (Dokumente/Blätter)

Das dokumentbasierte Authoring eignet sich am besten für die Erstellung einfacher, weniger komplexer Formulare mit bekannten Tools wie Microsoft Word, Google Docs oder Google Sheets. Diese Methode eignet sich ideal für Inhalts-Teams, die eine schnelle und unkomplizierte Möglichkeit zum Erstellen von Formularen benötigen.

* Definieren Sie Formularfelder in einer Tabelle (Dokumente) oder als Zeilen (Blätter).
* Unterstützt die grundlegende Feldüberprüfung und Google reCAPTCHA für den Spam-Schutz.
* Formularübermittlungen werden ausschließlich über den Forms Submission Service abgewickelt.
* Sofortige Veröffentlichung : Alle im Quelldokument vorgenommenen Änderungen werden sofort auf der Site übernommen, ohne dass eine Bereitstellungs-Pipeline erforderlich ist.


### Einbetten von Forms in die Dokumenterstellung (DA)

Die Dokumenterstellung (Document Authoring, DA) ist für die Erstellung strukturierter Seiteninhalte konzipiert und unterstützt nicht die Erstellung nativer Formulare. Gehen Sie wie folgt vor, um ein Formular zu einer von DAM erstellten Seite hinzuzufügen:

1. Erstellen Sie das Formular mit dem **universellen Editor** (empfohlen) oder dem dokumentbasierten Authoring.
2. Veröffentlichen Sie das Formular, um eine eindeutige URL zu generieren (z. B. `/forms/contact-us`).
3. Fügen Sie auf Ihrer DAM-Seite einen **Einbettungsformular**-Block ein und geben Sie die URL des veröffentlichten Formulars an.

<!-- 
## Feature Comparison

| Capability | Universal Editor | Document-Based | Document Authoring |
|------------|-----------------|----------------|--------------------|
| Visual drag-and-drop | ✅ | – | – |
| Advanced rules editor | ✅ | Limited | – |
| Attachments | ✅ | EA | – |
| reCAPTCHA Enterprise | ✅ | ✅ | Depends on embed |
| Submit to spreadsheet/email | ✅ (FSS) | ✅ (FSS) | Via embed |
| Submit to AEM workflows/FDM | ✅ | – | Via UE embed |
| Custom components (JS/CSS) | ✅ | ✅ | Via embed |
| Localization via Sites | ✅ | Manual | Via embed |

-->

## Nächste Schritte

1. **Erste Schritte mit dem universellen Editor:** Informationen zum Erstellen von Formularen finden Sie [ „Erste Schritte ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) universellen Editor“.
2. **Formularübermittlung konfigurieren** Wählen Sie Ihre bevorzugte Übermittlungsmethode aus und richten Sie sie ein. Konfigurationsanweisungen finden Sie unter [Forms-Übermittlungsdienst](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) oder AEM-Veröffentlichungs-Übermittlungsaktionen .
3. **Anwendung von Best Practices:** Überprüfen Sie [Best Practices für den Formularentwurf](/help/edge/docs/forms/universal-editor/best-practices-eds-forms.md) um Barrierefreiheit und Leistung sicherzustellen.
4. **Verwenden der dokumentbasierten Inhaltserstellung:** Um Formulare mit Microsoft Excel oder Google Sheets zu erstellen, folgen Sie der [Tutorial zur dokumentbasierten Inhaltserstellung](/help/edge/docs/forms/tutorial.md).
5. **Einbetten von Forms in die Dokumenterstellung:** Wenn Sie Seiten in der Dokumenterstellung erstellen, finden Sie im [DA-Tutorial](https://www.aem.live/developer/da-tutorial) Anweisungen zum Einbetten veröffentlichter Formulare.

> **Sie können jetzt Ihr erstes Hochleistungsformular mit AEM Edge Delivery Services erstellen.**