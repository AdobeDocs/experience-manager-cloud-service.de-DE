---
title: Unterstützte Client-Plattformen
description: Erfahren Sie, welche Browser für das Erstellen von Inhalten mit Adobe Experience Manager as a Cloud Service und den Zugriff auf mit AEM veröffentlichte Sites unterstützt werden.
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 22d4e6b5f87221b2739cf1dd9d59b4652a014316
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 26%

---


# Unterstützte Client-Plattformen {#supported-platforms}

Erfahren Sie, welche Browser für das Erstellen von Inhalten mit Adobe Experience Manager as a Cloud Service und den Zugriff auf mit AEM veröffentlichte Sites unterstützt werden.

>[!TIP]
>
>In diesem Dokument werden die von AEM as a Cloud Service unterstützten Client-Plattformen beschrieben. Einzelheiten zur Build-Umgebung für die Entwicklung Ihres AEM-Projekts finden Sie im Dokument [Build-Umgebung.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)

## Unterstützungsebenen {#support-levels}

Adobe definiert die folgenden Unterstützungsebenen für die Clientplattformen von AEM.

| Unterstützungsebene | Beschreibung |
|---|---|
| A: Unterstützt | Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird über den Qualitätssicherungsvorgang von Adobe abgedeckt. |
| R: Eingeschränkte Unterstützung  | Der Support erfordert eine formelle Anfrage an Adobe, die -Konfiguration in einem Projekt zu verwenden. Nach der Bestätigung durch Adobe bietet Adobe im Rahmen des eingeschränkten Support-Programms volle Unterstützung. Weitere Informationen erhalten Sie bei der Kundenunterstützung von Adobe. |
| Z: Nicht unterstützt | Die Konfiguration wird nicht unterstützt. Adobe macht keine Angaben dazu, ob die Konfiguration funktioniert, und unterstützt sie nicht. |

## Unterstützte Browser für die Inhaltserstellung {#authoring}

Die Benutzeroberfläche von AEM ist für größere Bildschirme optimiert, die sich in Notebooks, Desktop-Computern und Tablet-Geräten (wie Apple iPad oder Microsoft Surface) befinden. Der Telefon-Formfaktor wird für keinen Anwendungsfall beim Authoring unterstützt.

Die Benutzeroberfläche von Adobe Experience Manager funktioniert je nach Authoring[Methode mit den folgenden Clientplattformen](/help/edge/authoring-methods.md)

* [universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md)
* [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md)
* [Dokumentenbasiertes Authoring](/help/edge/docs/authoring.md) mithilfe der [Sidekick](/help/edge/docs/sidekick.md)

Alle Browser werden mit dem Standardsatz von Plug-ins und Add-ons getestet.

| Browser | Unterstützungsebene des universellen Editors | Unterstützungsebene des Seiteneditors | Sidekick-Unterstützungsebene |
|---|---|---|---|
| Google Chrome (Evergreen) | A: Unterstützt | A: Unterstützt | A: Unterstützt |
| Microsoft Edge (Evergreen) | A: Unterstützt | A: Unterstützt | Z: Nicht unterstützt |
| Mozilla Firefox (Evergreen) | A: Unterstützt | A: Unterstützt | Z: Nicht unterstützt |
| Mozilla Firefox neueste ESR [1] | A: Unterstützt | A: Unterstützt | Z: Nicht unterstützt |
| Safari auf macOS (Evergreen) | A: Unterstützt | A: Unterstützt | Z: Nicht unterstützt |
| Safari auf iOS (Evergreen) [2] | Z: Nicht unterstützt | A: Unterstützt | Z: Nicht unterstützt |

1. Version mit erweiterter Unterstützung von Firefox ([ Sie mehr auf mozilla.org](https://www.mozilla.org/de-DE/firefox/enterprise/))
1. Unterstützung nur für Apple iPad

>[!NOTE]
>
>**Unterstützung für Browser mit schnellen Versionszyklen:**
>
>Die Versionen von Firefox, Chrome und Edge werden regelmäßig aktualisiert. Adobe ist bestrebt, die oben aufgeführte Unterstützungsebene für bevorstehende Versionen dieser Browser beizubehalten.

## Unterstützte Browser für Websites {#websites}

Die Browser-Unterstützung für von AEM gerenderte Websites hängt von der Implementierung von AEM-Seitenvorlagen, -Blöcken, -Design und -Komponentenausgabe ab. Daher haben die Entwickler, die Ihr Projekt implementieren, letztendlich die Kontrolle über die Kompatibilität Ihrer Site.

Die AEM [Projektvorlage](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md#create-github-project) [Kernkomponenten](/help/implementing/developing/components/overview.md#aem-core-components) und [WKND-](/help/implementing/developing/introduction/develop-wknd-tutorial.md) sind mit allen modernen Browsern kompatibel.
