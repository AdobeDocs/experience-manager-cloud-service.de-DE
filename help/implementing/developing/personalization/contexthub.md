---
title: ContextHub
description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

# ContextHub {#contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Seine Hauptfunktion ist die Möglichkeit, [Kontextdaten anzuzeigen, während die Simulation verschiedener Rollen und der Wechsel zwischen ihnen ermöglicht wird](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub ermöglicht Ihnen Folgendes:

* [Präsentieren, Anzeigen, Wechseln von Rollen und Simulieren von Anwendererlebnissen](#presentation) beim Erstellen von Seiten mithilfe von Kontextdaten
* [Beibehalten von Kontextdaten](#persistence) auf Ihrer Website als Datenschichtdarstellung
* [Verwalten von Segmenten](#segmentation) für den ausgewählten Kontext

Die Client-seitige JavaScript-API ermöglicht Ihnen den Zugriff auf die Daten zur Personalisierung von Inhalten.

## Präsentation {#presentation}

Die [ContextHub-Symbolleiste](/help/sites-cloud/authoring/personalization/contexthub.md) ermöglicht es Marketern und Autoren, gespeicherte Daten anzuzeigen und zu bearbeiten, um das Anwendererlebnis beim Erstellen von Seiten zu simulieren. Die Symbolleiste besteht aus Gruppen von UI-Modulen, die den Zugriff auf [ContextHub-Speicher](#persistence) ermöglichen, in denen ContextHub-Daten auf dem Client beibehalten werden.

Jedes ContextHub-UI-Modul ist eine Instanz eines vordefinierten Modultyps:

* ContextHub stellt mehrere [Beispielmodularten](sample-modules.md) bereit.
* Verwenden Sie AEM-Konsolen, um [UI-Module hinzuzufügen](configuring-contexthub.md#adding-a-ui-module) und sie in [UI-Modi zu gruppieren](configuring-contexthub.md#adding-a-ui-mode).
* Entwickler können [benutzerdefinierte Modularten erstellen](extending-contexthub.md#creating-contexthub-ui-module-types).

Entwickler müssen die [ContextHub-Komponente in die Seite einfügen](configuring-contexthub.md).

## Persistenz {#persistence}

ContextHub speichert persistente Kontextdaten auf dem Client. Mit der ContextHub-JavaScript-API können Sie auf Speicher zugreifen, um Daten bei Bedarf zu erstellen, zu aktualisieren und zu löschen. Daher stellt ContextHub eine Datenschicht auf Ihren Seiten dar.

Jeder ContextHub-Speicher ist eine Instanz eines vordefinierten Speichertyps:

* ContextHub stellt verschiedene [Beispielspeicherarten bereit](sample-stores.md).
* Verwenden Sie AEM-Konsolen zum [Erstellen von Speichern](configuring-contexthub.md#creating-a-contexthub-store).
* Entwickler können [anwenderdefinierte Speichertypen erstellen](extending-contexthub.md#creating-custom-store-candidates).
* Entwickler können auf die [gespeicherten Daten](adding-contexthub.md#interacting-with-contexthub-stores) über JavaScript zugreifen.

## Segmentierung  {#segmentation}

ContextHub enthält eine Segmentations-Engine, die Segmente verwaltet und bestimmt, welche Segmente für den aktuellen Kontext aufgelöst werden. Mehrere Segmente sind definiert. Sie können die Javascript-API verwenden, um [aufgelöste Segmente zu ermitteln](adding-contexthub.md#determining-resolved-contexthub-segments).
