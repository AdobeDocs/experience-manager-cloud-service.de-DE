---
title: Multi-Site-Manager und -Übersetzung
description: Erfahren Sie, wie Sie Ihre Inhalte projektübergreifend wiederverwenden und mehrsprachige Websites in AEM verwalten können.
translation-type: tm+mt
source-git-commit: 4fc4dbe2386d571fa39fd6d10e432bb2fc060da1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 36%

---


# Multi-Site-Manager und Übersetzung {#msm-and-translation}

Adobe Experience Managers integrierte Multi-Site-Manager- und Übersetzungstools vereinfachen die Lokalisierung Ihrer Inhalte.

* Multi-Site-Manager (MSM) und seine Live-Copy-Funktionen ermöglichen Ihnen die Verwendung desselben Site-Inhalts an mehreren Orten, wobei Variationen möglich sind:
   * [Wiederverwenden von Inhalten: Multi-Site-Manager und Live Copy](msm/overview.md)
* Mit der Übersetzung können Sie die Übersetzung von Seiteninhalten automatisieren, um mehrsprachige Websites zu erstellen und zu verwalten:
   * [Übersetzen von Inhalten für mehrsprachige Sites](translation/overview.md)

Diese beiden Funktionen können kombiniert werden, um Websites zu berücksichtigen, die sowohl [multinational als auch mehrsprachig](#multinational-and-multilingual-sites) sind.

## Internationale, mehrsprachige Sites {#multinational-and-multilingual-sites}

Sie können durch den kombinierten Einsatz von Multi Site Manager und Übersetzungs-Workflow auf effiziente Weise Inhalte für internationale, mehrsprachige Sites erstellen.

Normalerweise würden Sie eine Site in einer Sprache und für ein bestimmtes Land Übergeordnet erstellen und diese dann als Grundlage für die anderen Sites verwenden, wobei Sie gegebenenfalls eine Übersetzung verwenden würden.

1. [Übersetzen](translation/overview.md) Sie die Master-Website in verschiedene Sprachen.
1. Verwenden Sie [Multi Site Manager](msm/overview.md) für Folgendes:
   1. Wiederverwendung von Inhalten der Übergeordnet-Site und deren Übersetzungen, um Sites für andere Länder und Kulturen zu erstellen.
   1. Trennen Sie bei Bedarf die Elemente der Live Copies, um Details zur lokale Anpassung hinzuzufügen.

>[!TIP]
>
>Begrenzen Sie die Verwendung von Multi-Site-Manager auf Inhalte in einer Sprache.
>
>Verwenden Sie z.B. den englischen Übergeordnete, um die englische Seitenversion für die USA, Kanada, Großbritannien usw. zu erstellen. Seiten und verwenden Sie das französische Übergeordnet, um die französische Seitenversion für Frankreich, die Schweiz, Kanada usw. zu erstellen.

Das folgende Diagramm veranschaulicht, wie die Hauptkonzepte sich überschneiden (es sind jedoch nicht alle beteiligten Ebenen/Elemente dargestellt):

![Übersicht über die lokale Anpassung](assets/localization-overview.png)

Bei diesem und vergleichbaren Szenarien verwaltet MSM nicht die verschiedenen Sprachversionen als solche.

* [](msm/overview.md) MSMmanagt die Bereitstellung übersetzter Inhalte von einem Entwurf (d.h. einem globalen Übergeordnete) zu den Live Copies (d.h. den lokalen Sites) innerhalb einer Sprache.
* Die AEM-Integrationsfunktionen zur [Übersetzung](translation/overview.md) verwalten kombiniert mit Übersetzungsmanagementdiensten von Drittanbietern die Sprachen und die Übersetzung der Inhalte in diese verschiedenen Sprachen.

Bei noch komplexeren Nutzungsszenarien kann MSM auch über Sprach-Master hinweg eingesetzt werden.

>[!TIP]
>
>Bei allen Nutzungsszenarien wird empfohlen, die folgenden Best Practices zu lesen:
>
>* [Best Practices für MSM](msm/best-practices.md)
>* [Best Practices für die Übersetzung](translation/best-practices.md)

