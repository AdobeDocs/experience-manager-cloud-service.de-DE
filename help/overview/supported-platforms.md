---
title: Unterstützte Client-Plattformen
description: Erfahren Sie, welche Browser für die Erstellung von Inhalten mit Adobe Experience Manager as a Cloud Service und den Zugriff auf mit AEM veröffentlichte Sites unterstützt werden.
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 7ddd0a75-621a-4499-91d1-7b3408a68269
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 99%

---

# Unterstützte Client-Plattformen {#supported-platforms}

Erfahren Sie, welche Browser für die Erstellung von Inhalten mit Adobe Experience Manager as a Cloud Service und den Zugriff auf mit AEM veröffentlichte Sites unterstützt werden.

>[!TIP]
>
>In diesem Dokument werden die von AEM as a Cloud Service unterstützten Client-Plattformen beschrieben. Weitere Informationen zur Build-Umgebung für die Entwicklung Ihres AEM-Projekts finden Sie im Dokument [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md).

## Unterstützungsebenen {#support-levels}

Adobe definiert die folgenden Unterstützungsebenen für Client-Plattformen von AEM.

| Unterstützungsebene | Beschreibung |
|---|---|
| A: Unterstützt | Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird über den Qualitätssicherungsvorgang von Adobe abgedeckt. |
| R: Eingeschränkte Unterstützung  | Zur Unterstützung ist eine formelle Anfrage an Adobe erforderlich, um die Konfiguration in einem Projekt verwenden zu können. Nach der Bestätigung durch Adobe bietet Adobe im Rahmen des eingeschränkten Support-Programms volle Unterstützung. Weitere Informationen erhalten Sie bei der Kundenunterstützung von Adobe. |
| Z: Nicht unterstützt | Die Konfiguration wird nicht unterstützt. Adobe macht keine Angaben dazu, ob die Konfiguration funktioniert, und unterstützt sie nicht. |

## Unterstützte Browser für die Erstellung von Inhalten {#authoring}

Die AEM-Benutzeroberfläche ist für größere Bildschirme von Notebooks, Desktop-Computern und Tablets (z. B. Apple iPad oder Microsoft Surface) optimiert. Der Telefon-Formfaktor wird für keinen Authoring-Anwendungsfall unterstützt.

Die Adobe Experience Manager-Benutzeroberfläche funktioniert abhängig von der [Authoring-Methode](/help/edge/overview.md#authoring-method) mit den folgenden Client-Plattformen. 

* [Universeller Editor](/help/sites-cloud/authoring/universal-editor/authoring.md)
* [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md)
* [Dokumentbasiertes Authoring](https://www.aem.live/docs/aem-authoring) mithilfe des [Sidekicks](https://www.aem.live/docs/sidekick)

Alle Browser werden mit dem Standardsatz von Plug-ins und Add-ons getestet.

| Browser | Unterstützungsebene des universellen Editors | Unterstützungsebene des Seiteneditors | Unterstützungsebene des Sidekicks |
|---|---|---|---|
| Google Chrome (Evergreen) | A: Unterstützt | A: Unterstützt | A: Unterstützt |
| Microsoft Edge (Evergreen) | A: Unterstützt | A: Unterstützt | Z: Nicht unterstützt |
| Mozilla Firefox (Evergreen) | A: Unterstützt | A: Unterstützt | Z: Nicht unterstützt |
| Aktuelle ESR von Mozilla Firefox [1] | A: Unterstützt | A: Unterstützt | Z: Nicht unterstützt |
| Safari auf macOS (Evergreen) | A: Unterstützt | A: Unterstützt | Z: Nicht unterstützt |
| Safari auf iPadOS (Evergreen) | Z: Nicht unterstützt | A: Unterstützt | Z: Nicht unterstützt |

1. Version mit erweiterter Unterstützung von Firefox ([weitere Informationen dazu finden Sie auf mozilla.org](https://www.mozilla.org/de-DE/firefox/enterprise/))

>[!NOTE]
>
>**Unterstützung für Browser mit schnellen Versionszyklen:**
>
>Die Versionen von Firefox, Chrome und Edge werden regelmäßig aktualisiert. Adobe ist bestrebt, die Unterstützungsebene wie oben aufgeführt für die künftigen Versionen dieser Browser aufrechtzuerhalten.

## Unterstützte Browser für Websites {#websites}

Die Browser-Unterstützung für mit AEM gerenderte Websites hängt von der Implementierung der AEM-Seitenvorlagen, den Blöcken, dem Design und der Komponentenausgabe ab. Daher haben die Entwicklerinnen und Entwickler, die Ihr Projekt implementieren, letztendlich die Kontrolle über die Kompatibilität Ihrer Site.

Die AEM-[Bausteinvorlage,](https://www.aem.live/developer/ue-tutorial#create-github-project) [Kernkomponenten](/help/implementing/developing/components/overview.md#aem-core-components) und [beispielhafte WKND-Site](/help/implementing/developing/introduction/develop-wknd-tutorial.md) sind alle mit modernen Browsern kompatibel.
