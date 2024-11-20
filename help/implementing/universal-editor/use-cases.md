---
title: Anwendungsfälle und Lernpfade für den universellen Editor
description: Erfahren Sie mehr über die wichtigsten Anwendungsfälle des universellen Editors und darüber, wie Sie am besten weitere Informationen über seine Verwendung und die Implementierung in Ihre eigenen Projekte einholen.
exl-id: 398ad0e2-c299-4c49-9784-05c84c67bec2
feature: Developing
role: Admin, Architect, Developer
source-git-commit: a7b48559e5bf60c86fecd73a8bcef6c9aaa03b80
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 82%

---

# Anwendungsfälle und Lernpfade für den universellen Editor {#use-cases-learning-paths}

Erfahren Sie mehr über die wichtigsten Anwendungsfälle des universellen Editors und darüber, wie Sie am besten weitere Informationen über seine Verwendung und die Implementierung in Ihre eigenen Projekte einholen.

## Überblick {#overview}

Der universelle Editor ist ein vielseitiger visueller Editor, der Teil von Adobe Experience Manager Sites ist. Er ermöglicht Autorinnen und Autoren die WYSIWYG-Bearbeitung („What you see is what you get“) von beliebigen Headless- und Headful-Erlebnissen.

In diesem Dokument werden diese beiden Anwendungsfälle ausführlich erläutert und es wird gezeigt, wie Sie mehr darüber erfahren können, damit Sie den universellen Editor in Ihr eigenes Projekt implementieren können.

>[!TIP]
>
>Falls Sie dies noch nicht getan haben, lesen Sie das Dokument [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md), um einen vollständigen Überblick für den universellen Editor zu erhalten und dessen Nutzen zu erkennen.

## Anwendungsfälle {#use-cases}

Der universelle Editor bietet Ihren Inhaltsautorinnen und Inhaltsautoren einen praktischen, intuitiven visuellen Editor, unabhängig davon, welche Art von Inhalt sie erstellen. Die zwei wichtigsten Anwendungsfälle sind:

* [WYSIWYG-Authoring](#wysiwyg-authoring): Verwenden Sie die AEM Sites-Konsole, um Ihre Inhalte zu verwalten und Seiten in AEM mit dem universellen Editor zu erstellen
* [Headless-Authoring](#headless-authoring): Erstellen Sie Inhalte in Ihrer benutzerdefinierten Headless-Anwendung mit dem universellen Editor.

### WYSIWYG-Authoring {#wysiwyg-authoring}

Wenn Sie bereits mit AEM vertraut sind, können Sie die Sites-Konsole verwenden, um Ihre Seiten zu erstellen und zu verwalten und sie dann mit dem universellen Editor zu bearbeiten.

Auf diese Weise können Sie die in der Sites-Konsole verfügbaren Tools wie Seitenverwaltung (Kopieren, Einfügen, Verschieben) und Workflows nutzen, aber auch vom modernen universellen Editor profitieren.

Falls dies Ihr Anwendungsfall ist, sehen Sie sich als nächsten Schritt die folgenden Dokumente an, um einen vollständigen Überblick über den Einstieg in den universellen Editor in AEM zu erhalten.

1. [Erste-Schritte-Handbuch für Entwickelnde zum WYSIWYG-Authoring mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md): Erfahren Sie mehr über die ersten Schritte bei Ihrem ersten universellen Editor-Projekt in AEM
1. [Erstellen von für den universellen Editor instrumentierten Bausteinen](/help/edge/wysiwyg-authoring/create-block.md): Erfahren Sie, wie Sie Bausteine instrumentieren können, um Ihre Inhalte im universellen Editor bearbeitbar zu machen
1. [Inhaltsmodellierung für WYSIWYG-Authoring-Projekte mit Edge Delivery Services](/help/edge/wysiwyg-authoring/content-modeling.md): Erfahren Sie, wie Bausteine strukturiert sind, um Ihre Inhalte für den universellen Editor effektiv zu modellieren.

Nachdem Sie diese Dokumente gelesen haben, können Sie auf diese Seite zurückkehren, um mehr über den Anwendungsfall „Headless-Authoring“ und die allgemeine Funktionsweise des universellen Editors zu erfahren.

### Headless-Authoring {#headless-authoring}

Wenn Sie bereits über eine Headless-Anwendung verfügen, können Sie den universellen Editor verwenden, um Inhalte für die Anwendung zu erstellen und deren Inhalte als Inhaltsfragmente in AEM beizubehalten. Die einzige Voraussetzung: Die Anwendung muss so konfiguriert sein, dass sie die Verwendung des universellen Editors ermöglicht.

Wenn dies Ihr Anwendungsfall ist, sehen Sie sich als nächsten Schritt das folgende Dokument an. Darin enthalten ist ein Beispiel für eine Headless-Anwendung, die für den universellen Editor instrumentiert ist.

* [SecurBank-Beispielanwendung für den universellen Editor](/help/implementing/universal-editor/securbank.md)

Nachdem Sie dieses Dokument gelesen haben, können Sie auf diese Seite zurückkehren, um mehr über den Anwendungsfall „WYSIWYG-Authoring“ und die allgemeine Funktionsweise des universellen Editors zu erfahren.

## Funktionsweise des universellen Editors {#how-ue-works}

Der universelle Editor ermöglicht es, beliebige Inhalte direkt zu erstellen, und stellt Inhaltsautorinnen und -autoren unabhängig vom Inhalt eine völlig intuitive und einheitliche Benutzeroberfläche zur Verfügung.

Der universelle Editor funktioniert wie folgt.

1. Eine Entwicklungsperson instrumentiert die Anwendung oder Seite für den universellen Editor. Im Rahmen dieser Instrumentierung wird der Editor angewiesen, welcher Inhalt bearbeitet werden kann und wie er beibehalten werden soll.
   * Wenn Sie der Dokumentation [Erste Schritte für Entwickler bei der WYSIWYG-Bearbeitung mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) folgen, werden Ihre Seiten automatisch instrumentiert.
   * Für das Headless-Authoring kann Ihre Anwendung einfach instrumentiert werden.
1. Die Inhaltsautorin bzw. der Inhaltsautor lädt den universellen Editor, der wiederum Ihre Seite zwecks Bearbeitung lädt. Aufgrund seiner Instrumentierung weiß er, welcher Inhalt bearbeitbar ist und wie dieser dargestellt und beibehalten werden soll.
1. Die Inhaltsautorin bzw. der Inhaltsautor bearbeitet den Seiteninhalt in einer intuitiven WYSIWYG-Benutzeroberfläche; die Bearbeitung erfolgt dabei direkt.
1. Der Universal Editor behält die Änderungen automatisch wieder in der Datenquelle bei.

Weitere Informationen zur Architektur des universellen Editors finden Sie im Dokument [Architektur des universellen Editors](/help/implementing/universal-editor/architecture.md).

## Konzepte des universellen Editors {#concepts}

Damit eine Seite oder App vom universellen Editor bearbeitet werden kann, muss sie ordnungsgemäß instrumentiert werden.

* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md): Damit eine Anwendung mit dem universellen Editor bearbeitet werden kann, muss sie ordnungsgemäß instrumentiert sein. Dazu gehören auch die korrekten Metadaten, damit der Editor den Inhalt der Anwendung bearbeiten kann.
* [Modelldefinitionen, Felder und Komponententypen](/help/implementing/universal-editor/field-types.md) - Sobald die Metadaten vorhanden sind, um die Bearbeitung einer Komponente zu ermöglichen, definieren Sie im Eigenschaftenbereich des Editors, welche Felder und Komponententypen sie bearbeiten können.
* [Universelle Editor-Ereignisse](/help/implementing/universal-editor/events.md): Sie können Ihre App weiter anpassen, indem Sie die Bearbeitungserfahrung in Ihrer App verbessern, indem Sie Ereignisse nutzen, die der universelle Editor für Inhalte oder Benutzeroberflächen ausgibt.

Der universelle Editor kann auch an Ihre Projektanforderungen angepasst werden.

* [Anpassen des Authoring-Erlebnisses für den universellen Editor](/help/implementing/universal-editor/customizing.md) - Das Erlebnis für den universellen Editor kann durch Filtern verschiedener Aspekte des Editors oder durch Erweitern der Funktionalität des Editors angepasst werden.
