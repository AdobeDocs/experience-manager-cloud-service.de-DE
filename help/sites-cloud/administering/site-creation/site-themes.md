---
title: Site-Designs
description: Erfahren Sie, wie Sie AEM-Site-Designs verwenden, um den Stil und das Design Ihrer Site anzupassen.
feature: Administering
role: Admin
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '364'
ht-degree: 100%

---

# Site-Designs {#site-themes}

Erfahren Sie, wie Sie AEM-Site-Designs verwenden, um den Stil und das Design Ihrer Site anzupassen.

## Überblick {#overview}

Ein AEM-Site-Design ist ein Paket, das die CSS-, JavaScript- und statischen Ressourcen enthält, die das Aussehen Ihrer AEM-Site definieren und die Struktur eines AEM-Site-Designs einhalten.

Sites, die mit AEM-Site-Vorlagen erstellt wurden, ermöglichen den einfachen Download, die Anpassung und die Neu-Bereitstellung von Designs.

>[!NOTE]
>
>AEM-Site-Designs sollten nicht mit [AEM-Site-Vorlagen verwechselt werden](site-templates.md). AEM-Site-Designs enthalten nur die Stil-Informationen für eine AEM-Site. AEM-Site-Vorlagen definieren die Site-Struktur und den anfänglichen Inhalt und beinhalten ein AEM-Site-Design, um die [schnelle Erstellung von Sites](create-site.md) zu ermöglichen.

## Verwenden von Site-Designs {#using-themes}

Site-Designs werden auf zwei verschiedene Arten verwendet:

* Sie werden als Teil einer Site-Vorlage verwendet, um beim [Erstellen einer Site](create-site.md) den Stil zu bestimmen.
* Sie werden heruntergeladen, nachdem eine Site basierend auf einer Site-Vorlage erstellt wurde, sodass Frontend-Entwickelnde den Stil weiter anpassen können.

>[!TIP]
>
>Eine vollständige Beschreibung des Prozesses zum Erstellen einer Site aus einer Vorlage und zum Anpassen ihres Designs finden Sie in der [Tour zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md).

## Struktur von Site-Designs {#structure}

Site-Designs sind einfach Pakete mit einer logischen Struktur, die den Zweck des Paketinhalts klar widerspiegelt. Für ein typisches Frontend-Projekt empfiehlt Adobe die folgende Struktur für ein Site-Design:

* `src/theme.ts`: Der Haupteinstiegspunkt Ihres JS- und CSS-Designs
* `src/site`: JS- und CSS-Dateien, die für die gesamte Site gelten
* `src/components`: JS- und CSS-Dateien, die für AEM-Komponenten spezifisch sind
* `src/resources`: Statische Dateien wie Symbole, Logos und Schriftarten

Abhängig von den spezifischen Projektanforderungen kann Ihre Designstruktur variieren, solange der Haupteinstiegspunkt `src/theme.ts` beibehalten wird.

## Standard-Site-Design {#standard-site-theme}

Adobe bietet ein Referenz-Design basierend auf Best Practices, das Sie als Grundlage für das Erstellen eines eigenen Designs verwenden können. [Das Standard-Site-Design ist auf GitHub verfügbar](https://github.com/adobe/aem-site-template-standard/tree/main/theme).

## Entwickeln von Site-Designs {#developing-themes}

Adobe bietet einen AEM-Site-Design-Assistenten als Satz von Skripten zum Erstellen neuer Site-Designs.

[Der AEM-Site-Design-Assistent ist zusammen mit der Nutzungsdokumentation auf GitHub verfügbar](https://github.com/adobe/aem-site-theme-builder). Um das Design anpassen zu können, ist Erfahrung in der Frontend-Entwicklung erforderlich.
