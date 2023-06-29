---
title: ContextHub
description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 54%

---

# ContextHub {#contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Seine Hauptfunktion ist die Möglichkeit, [Kontextdaten anzuzeigen, während die Simulation verschiedener Rollen und der Wechsel zwischen ihnen ermöglicht wird](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub ermöglicht Ihnen Folgendes:

* [Präsentieren, Anzeigen, Wechseln von Rollen und Simulieren von Anwendererlebnissen](#presentation) beim Erstellen von Seiten mithilfe von Kontextdaten
* [Beibehalten von Kontextdaten](#persistence) auf Ihrer Website als Datenschichtdarstellung
* [Verwalten von Segmenten](#segmentation) für den ausgewählten Kontext

Die clientseitige JavaScript-API ermöglicht den Zugriff auf die Daten zur Personalisierung von Inhalten.

## Präsentation {#presentation}

Die [ContextHub-Symbolleiste](/help/sites-cloud/authoring/personalization/contexthub.md) ermöglicht es Marketern und Autoren, gespeicherte Daten anzuzeigen und zu bearbeiten, um das Anwendererlebnis beim Erstellen von Seiten zu simulieren. Die Symbolleiste besteht aus Gruppen von UI-Modulen, die den Zugriff auf [ContextHub-Speicher](#persistence) ermöglichen, in denen ContextHub-Daten auf dem Client beibehalten werden.

Jedes ContextHub-UI-Modul ist eine Instanz eines vordefinierten Modultyps:

* ContextHub bietet mehrere [Beispielmodultypen](sample-modules.md).
* Verwenden AEM Konsolen für [Benutzeroberflächenmodule hinzufügen](configuring-contexthub.md#adding-a-ui-module)und [gruppieren sie in UI-Modi](configuring-contexthub.md#adding-a-ui-mode).
* Entwickler können [Erstellen benutzerdefinierter Modultypen](extending-contexthub.md#creating-contexthub-ui-module-types).

Entwickler müssen [Fügen Sie die ContextHub-Komponente zur Seite hinzu.](configuring-contexthub.md).

## Persistenz {#persistence}

ContextHub speichert persistente Kontextdaten auf dem Client. Mit der ContextHub-JavaScript-API können Sie auf Stores zugreifen, um bei Bedarf Daten zu erstellen, zu aktualisieren und zu löschen. Daher stellt ContextHub eine Datenschicht auf Ihren Seiten dar.

Jeder ContextHub-Store ist eine Instanz eines vordefinierten Storetyps:

* ContextHub stellt verschiedene [Beispielspeicherarten bereit](sample-stores.md).
* Verwenden AEM Konsolen für [Stores erstellen](configuring-contexthub.md#creating-a-contexthub-store).
* Entwickler können [anwenderdefinierte Speichertypen erstellen](extending-contexthub.md#creating-custom-store-candidates).
* Entwickler können [Zugriffsspeicherdaten](adding-contexthub.md#interacting-with-contexthub-stores) über JavaScript.

## Segmentierung {#segmentation}

ContextHub enthält eine Segmentierungsmaschine, die Segmente verwaltet und bestimmt, welche Segmente für den aktuellen Kontext aufgelöst werden. Mehrere Segmente sind definiert. Sie können die JavaScript-API verwenden, um [aufgelöste Segmente bestimmen](adding-contexthub.md#determining-resolved-contexthub-segments).
