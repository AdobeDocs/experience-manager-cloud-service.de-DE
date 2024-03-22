---
title: Methoden zum Erstellen von Inhalten in AEM
description: Erfahren Sie mehr über die verschiedenen Möglichkeiten, Inhalte in AEM zu erstellen, und wie sich diese unterscheiden.
feature: Authoring
exl-id: ef482843-451b-474e-a8d0-d0bfcc17221b
source-git-commit: d91254b52c257a3758da200a2c74b736ca457884
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 84%

---

# Methoden zum Erstellen von Inhalten in AEM {#authoring-methods}

Erfahren Sie mehr über die verschiedenen Möglichkeiten, Inhalte in AEM zu erstellen, wie sich diese unterscheiden und wann sich welche Methode empfiehlt.

## Authoring-Flexibilität mit AEM {#authoring-flexibility}

AEM as a Cloud Service bietet verschiedene Editoren, um verschiedene Inhaltstypen zu bearbeiten und verschiedene Authoring-Anwendungsfälle zu unterstützen.

* [AEM-Seiteneditor](#page-editor): Hierbei handelt es sich um den klassischen Editor für die Inhaltserstellung in AEM. Dieser hat sich bereits bei Tausenden von Websites bewährt.
* [AEM-Inhaltsfragment-Editor](#cf-editor): Dies ist der Editor der Wahl für die Erstellung von Headless-Inhalten.
* [Universeller Editor](#universal-editor): Diese moderne Benutzeroberfläche ermöglicht es, AEM-Inhalte inhaltsunabhängig zu erstellen. Er ist die erste Wahl bei AEM-Projekten, die Edge Delivery Services nutzen.
* [Dokumentenbasiertes Authoring](#document-based) - Wenn Sie Edge Delivery Services verwenden, können Sie Ihren Inhalt als herkömmliche Dokumente wie Microsoft Word- oder Google-Dokumente erstellen, die vollständig außerhalb AEM Konsolen liegen.

Aufgrund der Integrierbarkeit und Skalierbarkeit von AEM können diese Methoden je nach den Anforderungen Ihres Projekts ausschließlich oder in Kombination miteinander verwendet werden.

Wenden Sie sich an die Systemadministration oder das Projekt.-Management, wenn Sie nicht sicher sind, welche Authoring-Optionen Ihnen zur Verfügung stehen oder wenn Sie neue Möglichkeiten für die Inhaltserstellung kennenlernen möchten.

## AEM-Seiteneditor {#page-editor}

Hierbei handelt es sich um den klassischen Editor für die Inhaltserstellung in AEM. Dieser hat sich bereits bei Tausenden von Websites bewährt.

![Der AEM-Seiteneditor](assets/authoring-methods-page-editor.png)

Der AEM-Seiteneditor steht für eine integrierte Umgebung zum Authoring von Inhalten über eine WYSIWYG(What-you-see-is-what-you-get)-Oberfläche. Sie können vordefinierte Komponenten per Drag &amp; Drop verschieben, um eine Seite zu erstellen und Inhalte im Kontext zu bearbeiten.

Weitere Informationen zum AEM-Seiteneditor finden Sie unter [Der AEM-Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md).

## AEM-Inhaltsfragment-Editor {#cf-editor}

Der AEM-Inhaltsfragment-Editor ist der Editor der Wahl für die Erstellung von Headless-Inhalten.

![Der AEM-Inhaltsfragment-Editor](assets/authoring-methods-cf-editor.png)

Der AEM-Inhaltsfragment-Editor bietet eine übersichtliche Benutzeroberfläche zum Erstellen und Verwalten strukturierter Inhalte, was für die Headless-Bereitstellung ideal ist.

Weitere Informationen zum AEM-Inhaltsfragment-Editor finden Sie unter [Verwalten von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md) und [Erstellen von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md).

>[!NOTE]
>
>Der *neue* Editor, der in diesem Abschnitt beschrieben wird, ist bei der lokalen Entwicklungsarbeit für AEM as a Cloud Service nicht verfügbar.
>
>Der [*ursprüngliche* Inhaltsfragmente-Editor](/help/assets/content-fragments/content-fragments-variations.md) steht ebenfalls zur Verfügung.

## Universeller Editor {#universal-editor}

Beim universellen Editor handelt es sich um eine moderne Benutzeroberfläche, mit der Sie AEM-Inhalte inhaltsunabhängig erstellen können. Er ist die erste Wahl bei AEM-Projekten, die Edge Delivery Services nutzen.

![Der universelle Editor](assets/authoring-methods-ue.png)

Der universelle Editor wird über die Sites-Konsole in AEM aufgerufen, bietet jedoch die Fähigkeit und inhaltsunabhängige Flexibilität, nicht nur AEM-Inhalte, sondern auch ordnungsgemäß instrumentierte externe Inhalte zu bearbeiten.

Weitere Informationen zum universellen Editor finden Sie unter [Authoring mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md).

## Dokumentenbasiertes Authoring  {#document-based}

Wenn Sie Edge Delivery Services verwenden, können Sie Inhalte als herkömmliche Dokumente z. B. mit Microsoft Word oder Google Docs erstellen, und zwar komplett außerhalb der [AEM **Sites**-Konsole](/help/sites-cloud/authoring/sites-console/introduction.md).

![Bearbeiten dokumentbasierter Inhalte](assets/authoring-methods-document.jpg)

Mit Document-basiertem Authoring können Autoren die Tools verwenden, die sie bereits kennen, und dennoch von der Geschwindigkeit und Leistung AEM Edge Delivery Services profitieren, ihre Inhalte zu veröffentlichen. Die dokumentbasierte Bearbeitung erfordert keine Verwendung der AEM-Konsole.

Weitere Informationen zur dokumentbasierten Bearbeitung finden Sie im Dokument . [Inhaltserstellung für Edge Delivery Services.](/help/edge/authoring.md)
