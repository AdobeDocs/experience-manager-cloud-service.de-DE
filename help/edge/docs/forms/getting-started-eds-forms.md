---
title: Erste Schritte mit Formularen in AEM Edge Delivery Services
description: Erfahren Sie, wie Sie in Adobe Experience Manager Edge Delivery Services leistungsstarke Formulare erstellen und bereitstellen, wobei der Schwerpunkt auf dem Authoring-Ansatz mit dem universellen Editor liegt.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: ht
source-wordcount: '580'
ht-degree: 100%

---


# Erste Schritte mit Formularen in AEM Edge Delivery Services

<!--
<span class="preview"> This is a pre-release feature available through our <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features">pre-release channel</a>. </span>
-->

Adobe Experience Manager (AEM) Edge Delivery Services (EDS) ermöglicht die Bereitstellung von schnellen, hochgradig skalierbaren Web-Erlebnissen direkt am Edge. In diesem Handbuch wird erläutert, **wie Sie Formulare für diese Erlebnisse erstellen und veröffentlichen** – mit einer klaren Empfehlungshierarchie:

1. **Universeller Editor (UE) – Beste Wahl für die meisten Teams**
2. **Dokumentenbasiertes Authoring (Docs/Sheets) – ideal für schnelle, einfache Formulare**
3. **Dokumenterstellung (Document Authoring, DA) – Zum Einbetten von Formularen in vom DA erstellte Seiten**

Am Ende können Sie die richtige Authoring-Methode auswählen, Übermittlungsoptionen verstehen und die nächsten Schritte in Richtung produktionsbereiter Formulare ausführen.



## Auswählen einer Authoring-Methode

| Team und Anforderungen | Empfohlene Methode | Vorteile |
|--------------------|--------------------|-----|
| Marketing- und Design-Fachleute benötigen visuelle Kontrolle, Bedingungslogik oder AEM-Integrationen | **Universeller Editor** | Drag-and-Drop, erweiterte Regeln, Übermittlungen an FSS oder AEM Publish |
| Autorinnen und Autoren von Inhalten, die bereits in Word/Google Docs/Sheets arbeiten; einfache Datenerfassung in Tabellen/E-Mails | **Dokumentenbasiertes Authoring** | Vertraute Tools, schnellster Weg zu einfachen Formularen |
| Website-Seiten, die per **Dokumenterstellung (Document Authoring, DA)** erstellt wurden | **Einbetten** eines UE- oder DOC-basierten Formulars in die DA-Seite | DA erstellt keine Formulare selbst |


## Authoring-Methoden im Detail

### Universeller Editor

Der universelle Editor ist ein visuelles Drag-and-Drop-Authoring-Tool für Marketing- und Design-Fachleute, das Geschwindigkeit und Leistung auf Unternehmensniveau vereint:

- WYSIWYG-Bearbeitung in Echtzeit und Gerätevorschau.
- Erweiterte Regeln und Validierungs-UI – kein Code erforderlich.
- Direkte Integration mit AEM-Assets, Workflows und Formulardatenmodell (FDM).
- Nahtlose Übergabe an Entwicklung-Teams für benutzerdefinierte Komponenten in Vanilla JS/CSS.
- Flexible Übermittlungsziele: Beginnen Sie einfach mit dem **Forms Submission Service (FSS)** oder wechseln Sie bei steigenden Bedarf zu **Übermittlungsaktionen der AEM-Veröffentlichungsumgebung**.

> **Empfehlung**: Beginnen Sie jedes neue Formularprojekt mit dem universellen Editor, es sei denn, Ihr Team arbeitet zu 100 % dokumentenbasiert und das Formular ist sehr einfach.


### Dokumentenbasiertes Authoring (Docs/Sheets)

Dokumentenbasiertes Authoring eignet sich am besten für die Erstellung einfacher, weniger komplexer Formulare mit bekannten Tools wie Microsoft Word, Google Docs oder Google Sheets. Diese Methode ist ideal für Inhalts-Teams, die eine schnelle und unkomplizierte Möglichkeit zum Erstellen von Formularen benötigen.

- Definieren Sie Formularfelder in einer Tabelle (Docs) oder als Zeilen (Sheets).
- Unterstützt die grundlegende Feldüberprüfung und Google reCAPTCHA für den Spam-Schutz.
- Formularübermittlungen werden ausschließlich über den Forms Submission Service abgewickelt.
- Sofortige Veröffentlichung: Alle im Quelldokument vorgenommenen Änderungen werden sofort auf der Site übernommen, ohne dass eine Bereitstellungs-Pipeline erforderlich ist.


### Einbetten von Formularen in der Dokumentenerstellung

Die Dokumenterstellung (Document Authoring, DA) ist für die Erstellung strukturierter Seiteninhalte. Die Erstellung nativer Formulare wird nicht unterstützt. Gehen Sie wie folgt vor, um einer mit DA erstellten Seite ein Formular hinzuzufügen:

1. Erstellen Sie das Formular mit dem **universellen Editor** (empfohlen) oder dem dokumentenbasierten Authoring.
2. Veröffentlichen Sie das Formular, um eine eindeutige URL zu generieren (z. B. `/forms/contact-us`).
3. Fügen Sie auf Ihrer DA-Seite einen Block **Formular einbetten** ein und geben Sie die URL des veröffentlichten Formulars an.

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

1. **Erste Schritte mit dem universellen Editor:** Informationen zum Erstellen von Formularen finden Sie unter [Erste Schritte mit dem universellen Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md).
2. **Konfigurieren der Formularübermittlung**: Wählen Sie Ihre bevorzugte Übermittlungsmethode aus und richten Sie sie ein. Konfigurationsanweisungen finden Sie unter [Forms Submission Service](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) oder „Übermittlungsaktionen der AEM-Veröffentlichungsumgebung“.
3. **Anwendung von Best Practices:** Prüfen Sie die [Best Practices für den Formularentwurf](/help/edge/docs/forms/universal-editor/best-practices-eds-forms.md), um Barrierefreiheit und Leistung sicherzustellen.
4. **Verwenden des dokumentenbasierten Authorings:** Informationen zum Erstellen von Formularen mit Microsoft Excel oder Google Sheets finden Sie im [Tutorial zum dokumentenbasierten Authoring](/help/edge/docs/forms/tutorial.md).
5. **Einbetten von Formularen in die Dokumenterstellung:** Wenn Sie Seiten in der Dokumenterstellung erstellen, finden Sie im [DA-Tutorial](https://www.aem.live/developer/da-tutorial) Anweisungen zum Einbetten veröffentlichter Formulare.

> **Nun können Sie Ihr erstes leistungsstarkes Formular mit AEM Edge Delivery Services erstellen.**