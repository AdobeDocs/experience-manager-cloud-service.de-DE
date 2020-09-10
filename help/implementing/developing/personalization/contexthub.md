---
title: ContextHub
description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
translation-type: tm+mt
source-git-commit: 75d6b51c0148a21ca401d98a5eaf644fc6b0e8cc
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 67%

---


# ContextHub {#contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Das wichtigste Merkmal ist die Möglichkeit, Kontextdaten zu [Ansichten, während verschiedene Personen simuliert und umgeschaltet werden.](/help/sites-cloud/authoring/personalization/contexthub.md)

Der ContextHub ermöglicht Ihnen Folgendes:

* [Präsentieren, Ansicht, Wechseln von Personen und Simulieren von Benutzererlebnissen](#presentation) beim Erstellen von Seiten mithilfe von Kontextdaten.
* [Bewahren Sie Kontextdaten](#persistence) auf Ihrer Website als Datenschichtdarstellung auf.
* [Verwalten Sie Segmente](#segmentation) für den ausgewählten Kontext.

Die clientseitige JavaScript-API ermöglicht Ihnen den Zugriff auf die Daten zur Personalisierung von Inhalten.

## Präsentation {#presentation}

Die [ContextHub-Symbolleiste](/help/sites-cloud/authoring/personalization/contexthub.md) ermöglicht es Vermarktern und Autoren, gespeicherte Daten zu sehen und zu manipulieren, um die Benutzererfahrung beim Erstellen von Seiten zu simulieren. Die Symbolleiste besteht aus Gruppen von UI-Modulen, die Zugriff auf [ContextHub-Stores bieten,](#persistence) die ContextHub-Daten auf dem Client beibehalten.

Jedes ContextHub-UI-Modul ist eine Instanz eines vordefinierten Modultyps:

* ContextHub stellt mehrere [Beispielmodularten](sample-modules.md) bereit.
* Verwenden Sie AEM-Konsolen, um [UI-Module hinzuzufügen](configuring-contexthub.md#adding-a-ui-module) und sie in [UI-Modi zu gruppieren](configuring-contexthub.md#adding-a-ui-mode).
* Entwickler können [benutzerdefinierte Modularten erstellen](extending-contexthub.md#creating-contexthub-ui-module-types).

Entwickler müssen die [ContextHub-Komponente in die Seite einfügen](configuring-contexthub.md).

## Persistenz {#persistence}

ContextHub speichert persistente Kontextdaten auf dem Client. Die ContextHub JavaScript-API ermöglicht Ihnen den Zugriff auf Stores, um Daten nach Bedarf zu erstellen, zu aktualisieren und zu löschen. Daher stellt ContextHub eine Datenschicht auf Ihren Seiten dar.

Jeder ContextHub-Speicher ist eine Instanz eines vordefinierten Speichertyps:

* [ContextHub stellt verschiedene Beispielspeicherarten bereit](sample-stores.md).
* Verwenden Sie AEM-Konsolen zum [Erstellen von Speichern](configuring-contexthub.md#creating-a-contexthub-store).
* Entwickler können [benutzerdefinierte Speichertypen erstellen](extending-contexthub.md#creating-custom-store-candidates).
* Entwickler können auf die [gespeicherten Daten](configuring-contexthub.md#interacting-with-contexthub-stores) über JavaScript zugreifen.

## Segmentierung {#segmentation}

ContextHub enthält eine Segmentations-Engine, die Segmente verwaltet und bestimmt, welche Segmente für den aktuellen Kontext aufgelöst werden. Mehrere Segmente sind definiert. Sie können die Javascript-API verwenden, um [aufgelöste Segmente zu ermitteln](configuring-contexthub.md#determining-resolved-contexthub-segments).
