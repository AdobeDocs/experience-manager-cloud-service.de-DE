---
title: Site-Designs
description: Erfahren Sie, wie Sie mit AEM-Site-Designs den Stil und das Design Ihrer Site für herkömmliche AEM-Authoring-Projekte mit Veröffentlichungsbereitstellung anpassen können.
feature: Administering
role: Admin
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
solution: Experience Manager Sites
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 98%

---


# Site-Designs {#site-themes}

{{traditional-aem}}

Erfahren Sie, wie Sie mit AEM-Site-Designs den Stil und das Design Ihrer Site für herkömmliche AEM-Authoring-Projekte mit Veröffentlichungsbereitstellung anpassen können.

## Überblick {#overview}

Ein AEM-Site-Design ist ein Paket, das die CSS-, JavaScript- und statischen Ressourcen enthält, die das Aussehen Ihrer AEM-Site definieren und die Struktur eines AEM-Site-Designs einhalten.

Sites, die mit AEM-Site-Vorlagen erstellt wurden, ermöglichen das einfache Herunterladen, Anpassen und erneute Bereitstellen der Designs für herkömmliche AEM-Authoring-Projekte mit [Veröffentlichungsbereitstellung](/help/sites-cloud/authoring/author-publish.md).

>[!NOTE]
>
>AEM-Site-Designs sollten nicht mit [AEM-Site-Vorlagen verwechselt werden](site-templates.md). AEM-Site-Designs enthalten nur die Stil-Informationen für eine AEM-Site. AEM-Site-Vorlagen definieren die Site-Struktur und den anfänglichen Inhalt und beinhalten ein AEM-Site-Design, um die [schnelle Erstellung von Sites](create-site.md) zu ermöglichen.

## Verwenden von Site-Designs {#using-themes}

Site-Designs werden auf zwei verschiedene Arten verwendet:

* Sie werden als Teil einer Site-Vorlage verwendet, um beim [Erstellen einer Site](create-site.md) den Stil zu bestimmen.
* Sie werden heruntergeladen, nachdem eine Site basierend auf einer Site-Vorlage erstellt wurde, sodass ein Frontend-Entwickler den Stil weiter anpassen kann.

>[!TIP]
>
>Eine vollständige Beschreibung des Prozesses zum Erstellen einer Site aus einer Vorlage und zum Anpassen ihres Designs finden Sie im Abschnitt [Tour zum Quick Site Creation](/help/journey-sites/quick-site/overview.md).

## Struktur von Site-Designs {#structure}

Site-Designs sind einfach Pakete mit einer logischen Struktur, die den Zweck des Paketinhalts klar widerspiegelt. Für ein typisches Frontend-Projekt empfiehlt Adobe die folgende Struktur für ein Site-Design:

* `src/theme.ts`: Der Haupteinstiegspunkt Ihres JS- und CSS-Designs
* `src/site`: JS- und CSS-Dateien, die für die gesamte Site gelten
* `src/components`: JS- und CSS-Dateien, die für AEM-Komponenten spezifisch sind
* `src/resources`: Statische Dateien wie Symbole, Logos und Schriftarten

Abhängig von den spezifischen Projektanforderungen kann Ihre Designstruktur variieren, solange der Haupteinstiegspunkt `src/theme.ts` beibehalten wird.

## Standard-Site-Design {#standard-site-theme}

Adobe bietet ein Referenz-Design basierend auf Best Practices, das Sie als Grundlage für das Erstellen eines eigenen Designs verwenden können. [Das Standard-Site-Design ist auf GitHub verfügbar.](https://github.com/adobe/aem-site-template-standard/tree/main/theme)

## Entwickeln von Site-Designs {#developing-themes}

Adobe bietet einen AEM-Site-Design-Assistenten als Satz von Skripten zum Erstellen neuer Site-Designs.

[Der AEM-Site-Design-Assistent ist zusammen mit der Nutzungsdokumentation auf GitHub verfügbar.](https://github.com/adobe/aem-site-theme-builder) Um das Design anpassen zu können, ist Erfahrung in der Frontend-Entwicklung erforderlich.
