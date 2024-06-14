---
title: Anwendungsfälle und Lernpfade für universelle Editoren
description: Erfahren Sie mehr über die wichtigsten Anwendungsfälle des universellen Editors und wie Sie am besten über seine Verwendung und die Implementierung in Ihren eigenen Projekten erfahren.
exl-id: 398ad0e2-c299-4c49-9784-05c84c67bec2
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 3%

---

# Anwendungsfälle und Lernpfade für universelle Editoren {#use-cases-learning-paths}

Erfahren Sie mehr über die wichtigsten Anwendungsfälle des universellen Editors und wie Sie am besten mehr über dessen Verwendung und dessen Implementierung in Ihren eigenen Projekten erfahren.

## Überblick {#overview}

Der universelle Editor ist ein vielseitiger visueller Editor, der Teil von Adobe Experience Manager Sites ist. Sie ermöglicht es Autoren, die WYSIWYG-Bearbeitung (What-you-see-is-what-you-get) eines Headless- oder Headful-Erlebnisses durchzuführen.

In diesem Dokument werden diese beiden Anwendungsfälle ausführlich erläutert und Sie erfahren, wie Sie mehr darüber erfahren können, damit Sie den universellen Editor in Ihr eigenes Projekt implementieren können.

>[!TIP]
>
>Falls noch nicht geschehen, lesen Sie bitte das Dokument [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md) für eine vollständige Übersicht und einen vollständigen Wert des universellen Editors.

## Anwendungsfälle {#use-cases}

Der universelle Editor stellt Ihren Inhaltsautoren einen bequemen, intuitiven visuellen Editor zur Verfügung, unabhängig davon, welche Art von Inhalt sie erstellen. Die beiden Hauptanwendungsfälle sind:

* [WYSIWYG Authoring](#wysiwyg-authoring) - Verwenden Sie die AEM Sites-Konsole, um Ihre Inhalte und Autorenseiten in AEM mit dem universellen Editor zu verwalten.
* [Headless Authoring](#headless-authoring) - Verfassen Sie Inhalte in Ihrer eigenen, benutzerdefinierten Headless-Anwendung mit dem Universal Editor.

### WYSIWYG Authoring {#wysiwyg-authoring}

Wenn Sie bereits mit AEM vertraut sind, können Sie die Sites-Konsole verwenden, um Ihre Seiten zu erstellen und zu verwalten und sie dann mit dem universellen Editor zu bearbeiten.

Auf diese Weise können Sie von den in der Sites-Konsole verfügbaren Tools wie Seitenverwaltung (Kopieren, Einfügen, Verschieben) und Workflows profitieren, aber auch vom modernen universellen Editor.

Wenn dies Ihr Anwendungsfall ist, sehen Sie sich die folgenden Dokumente an, um einen vollständigen Überblick darüber zu erhalten, wie Sie mit dem universellen Editor in AEM arbeiten können.

1. [Erste Schritte für Entwickler beim WYSIWYG-Authoring mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) - Erste Schritte mit Ihrem ersten Universal Editor-Projekt in AEM
1. [Erstellen von für die Verwendung mit dem universellen Editor instrumentierten Bausteinen](/help/edge/wysiwyg-authoring/create-block.md) - Erfahren Sie, wie Sie Bausteine instrumentieren können, um Ihre Inhalte im universellen Editor bearbeitbar zu machen.
1. [Inhaltsmodellierung für WYSIWYG-Authoring mit Edge Delivery Services-Projekten](/help/edge/wysiwyg-authoring/content-modeling.md) - Erfahren Sie mehr über die Struktur von Bausteinen, um Ihre Inhalte für die Verwendung mit dem universellen Editor effektiv zu modellieren.

Nachdem Sie diese Dokumente gelesen haben, können Sie auf diese Seite zurückkehren, um mehr über den Anwendungsfall für Headless Authoring und die allgemeine Funktionsweise des universellen Editors zu erfahren.

### Headless Authoring {#headless-authoring}

Wenn Sie bereits über eine Headless-App verfügen, können Sie den Universal Editor verwenden, um Inhalte für die App zu erstellen und deren Inhalt als Inhaltsfragmente in AEM beizubehalten. Die einzige Voraussetzung ist, dass die App so konfiguriert ist, dass sie die Verwendung des universellen Editors ermöglicht.

Wenn dies Ihr Anwendungsfall ist, sehen Sie sich das folgende Dokument an, um ein Beispiel für eine Headless-App zu finden, die für die Verwendung des universellen Editors instrumentiert ist.

* [SecurBank-Beispielanwendung für den universellen Editor](/help/implementing/universal-editor/securbank.md)

Nachdem Sie dieses Dokument gelesen haben, können Sie auf diese Seite zurückkehren, um mehr über den WYSIWYG-Anwendungsfall für die Bearbeitung und die allgemeine Funktionsweise des universellen Editors zu erfahren.

## So funktioniert der universelle Editor {#how-ue-works}

Der universelle Editor bietet die Möglichkeit, beliebige Inhalte direkt zu erstellen und dem Inhaltsautor unabhängig vom Inhalt eine völlig intuitive und einheitliche Benutzeroberfläche zur Verfügung zu stellen.

Der universelle Editor funktioniert wie folgt.

1. Ein Entwickler instrumentiert die App oder Seite für die Verwendung des universellen Editors. Diese Anleitung teilt dem Editor mit, welcher Inhalt bearbeitet werden kann und wie er beibehalten werden soll.
   * Für WYSIWYG-Authoring werden Seiten, die mit der Vorlage &quot;Textbaustein&quot;erstellt wurden, automatisch instrumentiert.
   * Für Headless-Authoring kann Ihre App einfach instrumentiert werden.
1. Der Inhaltsautor lädt den universellen Editor, der Ihre Seite zur Bearbeitung lädt. Da es instrumentiert wird, weiß es, welcher Inhalt bearbeitbar ist und wie er dargestellt und beibehalten werden soll.
1. Der Inhaltsautor bearbeitet den Seiteninhalt in einer intuitiven WYSIWYG-Benutzeroberfläche und bearbeitet ihn an Ort und Stelle.
1. Der universelle Editor behält die Änderungen automatisch wieder in AEM bei.

Weitere Informationen zur Architektur des universellen Editors finden Sie im Dokument [Architektur des universellen Editors.](/help/implementing/universal-editor/architecture.md)

## Universelle Editor-Konzepte {#concepts}

Damit eine Seite oder App vom universellen Editor bearbeitet werden kann, muss sie ordnungsgemäß instrumentiert werden. Nach der Instrumentierung kann es weiter an Ihre Projektanforderungen angepasst werden.

* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md) - Damit eine App oder Seite vom universellen Editor bearbeitet werden kann, muss sie ordnungsgemäß instrumentiert werden. Dazu gehören auch die korrekten Metadaten, damit der Editor den Inhalt der App bearbeiten kann.
* [Modelldefinitionen, Felder und Komponententypen](/help/implementing/universal-editor/field-types.md) - Sobald die Metadaten vorhanden sind, um die Bearbeitung einer Komponente zu ermöglichen, definieren Sie in der Eigenschaftenleiste des Editors, welche Felder und Komponententypen sie bearbeiten können. Erstellen Sie dazu ein Modell und verknüpfen Sie es über die Komponente mit diesem.
* [Anpassen des Authoring-Erlebnisses für den universellen Editor](/help/implementing/universal-editor/customizing.md) - Sobald die App oder Seite vollständig instrumentiert wurde, kann das Universeller Editor-Erlebnis weiter angepasst werden, indem die verfügbaren Komponenten gefiltert oder die Funktionalität des Editors erweitert wird.
* [Universelle Editor-Ereignisse](/help/implementing/universal-editor/events.md) - Sie können Ihre App weiter anpassen, indem Sie auf Standardereignisse reagieren, die das Universal an Änderungen am Inhalt und an der Benutzeroberfläche sendet.
