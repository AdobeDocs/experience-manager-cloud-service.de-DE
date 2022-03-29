---
title: Site-Designs
description: Erfahren Sie, wie Sie AEM-Site-Designs verwenden, um den Stil und das Design Ihrer Site anzupassen.
feature: Administering
role: Admin
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 100%

---

# Site-Designs {#site-themes}

Erfahren Sie, wie Sie AEM-Site-Designs verwenden, um den Stil und das Design Ihrer Site anzupassen.

## Überblick {#overview}

Ein AEM-Site-Design ist ein Paket, das die CSS-, JavaScript- und statischen Ressourcen enthält, die das Aussehen Ihrer AEM-Site definieren und die Struktur eines AEM-Site-Designs einhalten.

Sites, die mit AEM-Site-Vorlagen erstellt wurden, ermöglichen den einfachen Download, die Anpassung und die Neuimplementierung von Designs.

>[!NOTE]
>
>AEM-Site-Designs sollten nicht mit [AEM-Site-Vorlagen verwechselt werden.](site-templates.md) AEM-Site-Designs enthalten nur die Stil-Informationen für eine AEM-Site. AEM-Site-Vorlagen definieren die Site-Struktur und den anfänglichen Inhalt sowie ein AEM-Site-Design, um die [schnelle Erstellung von Sites](create-site.md) zu ermöglichen.

## Verwenden von Site-Designs {#using-themes}

Site-Designs werden auf zwei verschiedene Arten verwendet:

* Sie werden als Teil einer Site-Vorlage verwendet, um beim [Erstellen einer Site](create-site.md) den Stil zu bestimmen.
* Sie werden heruntergeladen, nachdem eine Site basierend auf einer Site-Vorlage erstellt wurde, sodass ein Frontend-Entwickler den Stil weiter anpassen kann.

>[!TIP]
>
>Eine vollständige Beschreibung des Prozesses zum Erstellen einer Site aus einer Vorlage und zum Anpassen ihres Designs finden Sie im Abschnitt [Tour zum Quick Site Creation](/help/journey-sites/quick-site/overview.md).

## Struktur von Site-Designs {#structure}

Site-Designs sind einfach Pakete mit einer logischen Struktur, die den Zweck des Paketinhalts klar widerspiegelt. Ein Site-Design weist die folgende Struktur auf, die für ein Frontend-Projekt typisch ist.

* `src/main.ts`: Der Haupteinstiegspunkt Ihres JS- und CSS-Designs
* `src/site`: JS- und CSS-Dateien, die für die gesamte Site gelten
* `src/components`: JS- und CSS-Dateien, die für AEM-Komponenten spezifisch sind
* `src/resources`: Statische Dateien wie Symbole, Logos und Schriftarten

## Standard-Site-Design {#standard-site-theme}

Adobe bietet ein Referenz-Design basierend auf Best Practices, das Sie als Grundlage für das Erstellen eines eigenen Designs verwenden können. [Das Standard-Site-Design ist auf GitHub verfügbar.](https://github.com/adobe/aem-site-template-standard-theme-e2e)

## Entwickeln von Site-Designs {#developing-themes}

Adobe bietet einen AEM-Site-Design-Assistenten als Satz von Skripten zum Erstellen neuer Site-Designs.

[Der AEM-Site-Design-Assistent ist zusammen mit der Nutzungsdokumentation auf GitHub verfügbar.](https://github.com/adobe/aem-site-theme-builder) Um das Design anpassen zu können, ist Erfahrung in der Frontend-Entwicklung erforderlich.
