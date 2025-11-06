---
title: Erweitern des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Optionen zum Erweitern der Funktionen des universellen Editors, um die Anforderungen Ihrer Inhaltsautorinnen und Inhaltsautoren zu unterstützen.
feature: Developing
role: Admin, Developer
exl-id: 2f487fa5-57a7-477a-ad68-590e6cc12f4e
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 100%

---

# Erweitern des universellen Editors {#extending}

Erfahren Sie mehr über die verschiedenen Optionen zum Erweitern der Funktionen des universellen Editors, um die Anforderungen Ihrer Inhaltsautorinnen und Inhaltsautoren zu unterstützen.

>[!TIP]
>
>Der universelle Editor bietet außerdem mehrere [Anpassungsoptionen](/help/implementing/universal-editor/customizing.md), mit denen Sie Ihre Projektanforderungen besser erfüllen können.

## Erweiterungen {#extensions}

Als Adobe Experience Cloud-Service kann die Benutzeroberfläche des universellen Editors mit App Builder und Experience Manager erweitert werden. Adobe bietet viele vorkonfigurierte Erweiterungen, die Sie über den [Extension Manager](https://experience.adobe.com/aem/extension-manager) für Ihr Projekt verwenden können.

* **[Erweiterung für AEM Multi-Site-Management (MSM)](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance)**: Unterbrechen oder reaktivieren Sie die Vererbung auf Komponentenebene
* **[AEM-Erweiterung für Seiteneigenschaften](/help/sites-cloud/authoring/universal-editor/authoring.md#page-properties)**: Greifen Sie im universellen Editor auf das Fenster „Seiteneigenschaften“ einer Seite zu
* **[AEM Site Admin-Erweiterung](/help/sites-cloud/authoring/universal-editor/authoring.md#sites-console)**: Öffnen Sie im universellen Editor die Sites-Konsole zum Speicherort der Seite
* **[AEM-Erweiterung für Seitensperren](/help/sites-cloud/authoring/universal-editor/authoring.md#locking-pages)**: Ermöglicht das Anzeigen und Ändern des Seitensperrstatus im universellen Editor
* **[AEM-Erweiterung für Workflows](/help/sites-cloud/authoring/universal-editor/authoring.md#workflows)**: Starten Sie im universellen Editor Workflows auf der Seite und in Seiteninhalten
* **[AEM-Erweiterung für Entwickler-Anmeldung im universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md#developer-login)**: Wenn Sie lokal entwickeln, können Sie sich einfach bei Ihrem lokalen AEM-SDK authentifizieren 
* **[Varianten generieren](/help/generative-ai/generate-variations-integrated-editor.md)**: Verwenden Sie generative künstliche Intelligenz (KI), um Varianten für Ihre Inhalte direkt im Panel „Eigenschaften“ zu erstellen.
* **[AEM-Produktauswahl für den universellen Editor](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/ue-product-picker/)**: Integrieren Sie Adobe Commerce-Daten, indem Sie Produktdaten im Editor auswählen oder entfernen.
* **[Inhaltsentwürfe im universellen Editor](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/universal-editor-content-drafts/)**: Erstellen, bearbeiten und verwalten Sie mehrere Inhaltsentwürfe.
* **[Konfigurierbare Asset-Auswahl](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/)**: Aktivieren Sie die Asset-Auswahl aus weiteren Repositorys, die von der bearbeiteten Seite nicht verwendet werden.
* **Formularregel-Editor**: Fügen Sie AEM Forms-Feldern dynamisches Verhalten visuell ohne Kodierung hinzu.
* **[Inhaltsfragmente nach Adobe Target exportieren](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/exporting-content-fragment-to-adobe-target/)**: Exportieren Sie Inhaltsfragmente, die in Adobe Experience Manager as a Cloud Service erstellt wurden, nach Adobe Target, um sie als Angebote in Target-Aktivitäten zu verwenden und Erlebnisse im benötigten Umfang zu testen und zu personalisieren.
* **[Inhaltsfragment-Workflows](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/content-fragments-workflows/)**: Starten Sie einen AEM-Workflow für ausgewählte Inhaltsfragmente.

Weitere Informationen zum Aktivieren dieser Erweiterungen [finden Sie in der Dokumentation zu Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

## Erweitern der Benutzeroberfläche {#extending-ui}

Die Benutzeroberflächenerweiterungen des universellen Editors sind JavaScript-Anwendungen, die mit Adobe App Builder erstellt wurden. Sie können dem Kopfzeilenmenü und dem Panel „Eigenschaften“ Ihre eigenen Schaltflächen und Aktionen hinzufügen und eigene Ereignisse für den universellen Editor erstellen.

Wenn Sie die Möglichkeiten zum Erstellen eigener Erweiterungen erkunden möchten, lesen Sie die folgenden Ressourcen:

1. [Erweiterbarkeit der Benutzeroberfläche](https://developer.adobe.com/uix/docs/) – Dies ist die Entwicklerdokumentation für die Benutzeroberflächenerweiterung.
1. [Anleitung für die Erweiterung der Benutzeroberfläche](https://developer.adobe.com/uix/docs/guides/) – Schritt-für-Schritt-Anleitung zur Entwicklung Ihrer eigenen Erweiterung
1. [Erweiterungspunkte für die UI des universellen Editors](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) – Dokumentation zu den Erweiterungspunkten speziell für den universellen Editor

>[!TIP]
>
>Wenn Sie es vorziehen, anhand von Beispielen zu lernen, sehen Sie sich das [Tutorial zur Erweiterbarkeit der AEM-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview) an. Obwohl der Fokus des Tutorials auf der Erweiterung der Inhaltsfragmentkonsole liegt, ist das Konzept zur Implementierung einer Benutzeroberflächenerweiterung im universellen Editor identisch.

Mit dem [Extension Manager in AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/) können Sie Ihre Erweiterungen auf Instanzbasis aktivieren oder deaktivieren, auf Erweiterungen von Adobe zugreifen, einschließlich der Erweiterungen für den universellen Editor, und vieles mehr.

## Erweiterungspunkte {#extension-points}

Neben der UI-Erweiterbarkeit bietet der universelle Editor viele weitere flexible Erweiterungspunkte, um die nahtlose Integration benutzerdefinierter Geschäftsanforderungen zu ermöglichen.

* **[Blöcke](https://www.aem.live/developer/block-collection)**: Im einfachen JSON-Format können Projekte die für die Inhaltserstellung verfügbaren Blöcke und Funktionen anpassen.
* **[Benutzerdefinierte Benutzeroberfläche](#extending-ui)**: Erweiterungen können die erforderliche Benutzeroberfläche in Seiten-Panels oder modalen Dialogfeldern anzeigen.
* **[Ereignisse](/help/implementing/universal-editor/events.md)**: Erweiterungen empfangen Ereignisse zu den von Autorinnen oder Autoren auf der Seite verwendeten Aktionen und Auswahlen und reagieren entsprechend.
