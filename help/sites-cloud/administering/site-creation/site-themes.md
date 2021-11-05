---
title: Site-Themen
description: Erfahren Sie, wie AEM Site-Designs verwendet werden können, um den Stil und das Design Ihrer Site anzupassen.
feature: Administering
role: Admin
source-git-commit: 9e7ad4a640f1783be5aed75e01e860b647662f52
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 1%

---


# Site-Themen {#site-themes}

Erfahren Sie, wie AEM Site-Designs verwendet werden können, um den Stil und das Design Ihrer Site anzupassen.

>[!CAUTION]
>
>Das Tool für die schnelle Site-Erstellung ist derzeit eine technische Vorschau. Sie wird zu Test- und Evaluierungszwecken bereitgestellt und ist nicht zur Verwendung in der Produktion bestimmt, es sei denn, sie wurde mit der Adobe Support vereinbart.

## Übersicht {#overview}

Ein AEM Site-Design ist ein Paket, das die CSS-, JavaScript- und statischen Ressourcen enthält, die die Formatierung Ihrer AEM Site definieren und die Struktur eines AEM Site-Designs einhalten.

Sites, die mit AEM Site-Vorlagen erstellt wurden, ermöglichen den einfachen Download, die Anpassung und die Neuimplementierung der Designs.

>[!NOTE]
>
>AEM Website-Designs sollten nicht mit [AEM Site-Vorlagen.](site-templates.md) AEM Site-Designs enthalten nur die Styling-Informationen für eine AEM Site. AEM Site-Vorlagen definieren die Site-Struktur und den anfänglichen Inhalt sowie ein AEM Site-Design, um [schnelle Site-Erstellung.](create-site.md)

## Verwenden von Site-Designs {#using-themes}

Site-Designs werden auf zwei verschiedene Arten verwendet:

* Sie werden als Teil einer Site-Vorlage verwendet, um die Formatierung zu definieren, wenn [Erstellen einer Site.](create-site.md)
* Sie werden heruntergeladen, nachdem eine Site basierend auf einer Site-Vorlage erstellt wurde, sodass ein Frontend-Entwickler die Formatierung weiter anpassen kann.

>[!TIP]
>
>Eine vollständige Beschreibung des Prozesses zum Erstellen einer Site aus einer Vorlage und zum Anpassen ihres Designs finden Sie im Abschnitt [Journey zur schnellen Site-Erstellung.](/help/journey-sites/quick-site/overview.md)

## Struktur von Site-Designs {#structure}

Site-Designs sind einfach Pakete mit einer logischen Struktur, die den Zweck des Paketinhalts klar widerspiegelt. Ein Site-Design weist die folgende Struktur auf, die für ein Frontend-Projekt typisch ist.

* `src/main.ts`: Der Haupteinstiegspunkt Ihres JS- und CSS-Designs
* `src/site`: JS- und CSS-Dateien, die für die gesamte Site gelten
* `src/components`: JS- und CSS-Dateien, die für AEM Komponenten spezifisch sind
* `src/resources`: Statische Dateien wie Symbole, Logos und Schriftarten

## Standard-Site-Design {#standard-site-theme}

Adobe bietet ein Best Practices-Referenzthema, das Sie als Grundlage für die Erstellung eines eigenen Designs verwenden können. [Das Standard-Site-Design ist auf GitHub verfügbar.](https://github.com/adobe/aem-site-template-standard-theme-e2e)

## Entwickeln von Site-Designs {#developing-themes}

Adobe bietet und AEM Site-Design-Builder als Satz von Skripten zum Erstellen neuer Site-Designs.

[Der AEM Site Theme Builder ist zusammen mit der Nutzungsdokumentation auf GitHub verfügbar.](https://github.com/adobe/aem-site-theme-builder) Für die Anpassung des Designs ist ein Frontend-Entwicklungs-Erlebnis erforderlich.
