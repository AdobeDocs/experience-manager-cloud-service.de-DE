---
title: Erweitern des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Optionen zur Erweiterung der Funktionen des universellen Editors, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 0cab4a807be4aa402667feddb6a948f0d2db371f
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 6%

---


# Erweitern des universellen Editors {#extending}

Erfahren Sie mehr über die verschiedenen Optionen zur Erweiterung der Funktionen des universellen Editors, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.

>[!TIP]
>
>Der universelle Editor bietet außerdem mehrere [Anpassungsoptionen](/help/implementing/universal-editor/customizing.md) mit denen Sie Ihre Projektanforderungen besser erfüllen können.

## Erweiterungen {#extensions}

Als Adobe Experience Cloud-Service kann die Benutzeroberfläche des universellen Editors mithilfe von App Builder und Experience Manager erweitert werden. Adobe bietet viele vorgefertigte Erweiterungen, die Sie für Ihr Projekt verwenden können.

* **[AEM-Produktauswahl für universellen Editor](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/ue-product-picker/)**: Integrieren Sie Adobe Commerce-Daten, indem Sie Produktdaten aus dem Editor auswählen oder daraus entfernen.
* **[Inhaltsentwürfe im universellen Editor](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/universal-editor-content-drafts/)**: Erstellen, Bearbeiten und Verwalten mehrerer Inhaltsentwürfe.
* **[Konfigurierbare Asset-Auswahl](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/)**: Aktivieren Sie die Asset-Auswahl aus anderen Repositorys als dem, der von der bearbeiteten Seite verwendet wird.
* **Forms-Regeleditor**: Dynamisches Verhalten visuell, ohne Kodierung, zu AEM Forms-Feldern hinzufügen.
* **[Exportieren von Inhaltsfragmenten nach Adobe Target](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/exporting-content-fragment-to-adobe-target/)**: Exportieren Sie Inhaltsfragmente, die in Adobe Experience Manager as a Cloud Service erstellt wurden, nach Adobe Target, um sie als Angebote in Target-Aktivitäten zu verwenden und skaliert zu testen und zu personalisieren.
* **[Inhaltsfragment-Workflows](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/content-fragments-workflows/)**: Starten eines AEM-Workflows für ausgewählte Inhaltsfragmente.

## Erweitern der Benutzeroberfläche {#extending-ui}

Die Benutzeroberflächenerweiterungen des universellen Editors sind JavaScript-Programme, die mit Adobe App Builder erstellt wurden. Mit denselben Tools können Sie auch eigene Schaltflächen und Aktionen zum Kopfzeilenmenü und zum Bedienfeld Eigenschaften hinzufügen sowie eigene Ereignisse für den universellen Editor erstellen.

Wenn Sie die Möglichkeiten zum Erstellen Ihrer eigenen Erweiterungen erkunden möchten, lesen Sie die folgenden Ressourcen:

1. [Erweiterbarkeit der Benutzeroberfläche](https://developer.adobe.com/uix/docs/) – Dies ist die Entwicklerdokumentation für die Benutzeroberflächenerweiterung.
1. [Anleitung für die Erweiterung der Benutzeroberfläche](https://developer.adobe.com/uix/docs/guides/) – Schritt-für-Schritt-Anleitung zur Entwicklung Ihrer eigenen Erweiterung
1. [Die Erweiterungspunkte der universellen Editor-Benutzeroberfläche](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Dokumentation zu universellen Editor-spezifischen Erweiterungspunkten

>[!TIP]
>
>Wenn Sie es vorziehen, anhand von Beispielen zu lernen, lesen Sie bitte das [Tutorial zur Erweiterbarkeit der AEM-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview). Obwohl sie sich auf die Erweiterung der Inhaltsfragmentkonsole konzentriert, sind die Konzepte zur Implementierung einer Benutzeroberflächenerweiterung im universellen Editor dieselben.

[Mit Extension Manager in AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/) können Sie Ihre Erweiterungen für jede Instanz aktivieren oder deaktivieren, auf die First-Party-Erweiterungen von Adobe zugreifen, einschließlich der Erweiterungen für den universellen Editor, und vieles mehr.

## Erweiterungspunkte {#extension-points}

Zusätzlich zur UI-Erweiterbarkeit bietet der universelle Editor viele weitere flexible Erweiterungspunkte, um die nahtlose Integration benutzerdefinierter Geschäftsanforderungen zu ermöglichen.

* **[Blöcke](/help/edge/developer/block-collection.md)**: Im einfachen JSON-Format können Projekte die für die Inhaltserstellung verfügbaren Blöcke und Funktionen anpassen.
* **[Benutzerdefinierte Benutzeroberfläche](#extending-ui)**: Erweiterungen können die erforderliche Benutzeroberfläche in Seitenbereichen oder modalen Dialogfeldern anzeigen.
* **[Ereignisse](/help/implementing/universal-editor/events.md)**: Erweiterungen erhalten Ereignisse zu den Aktionen und Auswahlen des Autors auf der Seite, damit sie entsprechend reagieren.
