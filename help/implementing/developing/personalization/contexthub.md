---
title: ContextHub
description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 92%

---

# ContextHub {#contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Seine Hauptfunktion ist die Möglichkeit, [Kontextdaten anzuzeigen, während die Simulation verschiedener Rollen und das Wechseln zwischen ihnen ermöglicht wird](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub ermöglicht Ihnen Folgendes:

* [Präsentieren, Anzeigen, Wechseln von Rollen und Simulieren von Anwendererlebnissen](#presentation) beim Erstellen von Seiten mithilfe von Kontextdaten
* [Beibehalten von Kontextdaten](#persistence) auf Ihrer Website als Datenschichtdarstellung
* [Verwalten von Segmenten](#segmentation) für den ausgewählten Kontext

Die Client-seitige JavaScript-API ermöglicht Ihnen den Zugriff auf die Daten zur Personalisierung von Inhalten.

## Präsentation {#presentation}

Die [ContextHub-Symbolleiste](/help/sites-cloud/authoring/personalization/contexthub.md) ermöglicht es Marketern und Autoren, gespeicherte Daten anzuzeigen und zu bearbeiten, um das Anwendererlebnis beim Erstellen von Seiten zu simulieren. Die Symbolleiste besteht aus Gruppen von Benutzeroberflächenmodulen, die Zugriff auf [ContextHub-Stores](#persistence) bieten, die ContextHub-Daten auf dem Client persistieren.

Jedes ContextHub-UI-Modul ist eine Instanz eines vordefinierten Modultyps:

* ContextHub stellt verschiedene [Beispiel-Modultypen](sample-modules.md) bereit.
* Verwenden Sie AEM-Konsolen, um [UI-Module hinzuzufügen](configuring-contexthub.md#adding-a-ui-module) und sie [in UI-Modi zu gruppieren](configuring-contexthub.md#adding-a-ui-mode).
* Entwicklerinnen und Entwickler können [benutzerdefinierte Modultypen erstellen](extending-contexthub.md#creating-contexthub-ui-module-types).

Entwicklerinnen und Entwickler müssen [die ContextHub-Komponente zur Seite hinzufügen](configuring-contexthub.md).

## Persistenz {#persistence}

ContextHub speichert persistente Kontextdaten auf dem Client. Mit der ContextHub-JavaScript-API können Sie auf Stores zugreifen, um Daten bei Bedarf zu erstellen, zu aktualisieren und zu löschen. Daher stellt ContextHub eine Datenschicht auf Ihren Seiten dar.

Jeder ContextHub-Store ist eine Instanz eines vordefinierten Store-Typs:

* ContextHub stellt verschiedene [Beispielspeicherarten bereit](sample-stores.md).
* Verwenden Sie AEM-Konsolen, um [Stores zu erstellen](configuring-contexthub.md#creating-a-contexthub-store).
* Entwickler können [anwenderdefinierte Speichertypen erstellen](extending-contexthub.md#creating-custom-store-candidates).
* Entwicklerinnen und Entwickler können über JavaScript auf [Store-Daten](adding-contexthub.md#interacting-with-contexthub-stores) zugreifen.

## Segmentierung {#segmentation}

ContextHub enthält eine Segmentierungs-Engine, die Segmente verwaltet und bestimmt, welche Segmente für den aktuellen Kontext aufgelöst werden. Mehrere Segmente sind definiert. Sie können die JavaScript-API verwenden, um [aufgelöste Segmente zu bestimmen](adding-contexthub.md#determining-resolved-contexthub-segments).
