---
title: Multi-Site-Manager und Übersetzung
description: Erfahren Sie, wie Sie Ihre Inhalte in Ihrem gesamten Projekt wiederverwenden und mehrsprachige Websites in AEM verwalten können.
feature: Verwalten
role: Administrator
exl-id: a3d48884-081e-44f8-8055-ee3657757bfd
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 36%

---

# Multi Site Manager and Translation {#msm-and-translation}

Adobe Experience Managers integrierte Multi-Site-Manager- und Übersetzungs-Tools vereinfachen die Lokalisierung Ihrer Inhalte.

* Multi-Site-Manager (MSM) und die zugehörigen Live Copy-Funktionen ermöglichen Ihnen die Verwendung desselben Site-Inhalts an mehreren Orten und ermöglichen gleichzeitig Variationen:
   * [Wiederverwenden von Inhalten: Multi-Site-Manager und Live Copy](msm/overview.md)
* Mit der Übersetzung können Sie die Übersetzung von Seiteninhalten automatisieren, um mehrsprachige Websites zu erstellen und zu verwalten:
   * [Übersetzen von Inhalten für mehrsprachige Sites](translation/overview.md)

Diese beiden Funktionen können kombiniert werden, um Websites zu unterstützen, die sowohl [multinational als auch mehrsprachig](#multinational-and-multilingual-sites) sind.

## Internationale, mehrsprachige Sites {#multinational-and-multilingual-sites}

Sie können durch den kombinierten Einsatz von Multi Site Manager und Übersetzungs-Workflow auf effiziente Weise Inhalte für internationale, mehrsprachige Sites erstellen.

Normalerweise würden Sie eine Übergeordnete Site in einer Sprache und für ein bestimmtes Land erstellen und diese Inhalte dann als Grundlage für die anderen Sites verwenden, wobei Sie bei Bedarf Übersetzungen verwenden.

1. [Übersetzen](translation/overview.md) Sie die Master-Website in verschiedene Sprachen.
1. Verwenden Sie [Multi Site Manager](msm/overview.md) für Folgendes:
   1. Verwenden Sie Inhalte der Übergeordneten Site und deren Übersetzungen erneut, um Websites für andere Länder und Kulturen zu erstellen.
   1. Trennen Sie bei Bedarf die Elemente der Live Copies, um Lokalisierungsdetails hinzuzufügen.

>[!TIP]
>
>Beschränken Sie die Verwendung von Multi Site Manager auf Inhalte in einer Sprache.
>
>Verwenden Sie z. B. das Übergeordnete Englisch , um die englische Seitenversion für die USA, Kanada, Großbritannien usw. zu erstellen. Seiten und verwenden Sie das französische Übergeordnete , um die französische Seitenversion für Frankreich, die Schweiz, Kanada usw. zu erstellen.

Das folgende Diagramm veranschaulicht, wie die Hauptkonzepte sich überschneiden (es sind jedoch nicht alle beteiligten Ebenen/Elemente dargestellt):

![Lokalisierungsübersicht](assets/localization-overview.png)

Bei diesem und vergleichbaren Szenarien verwaltet MSM nicht die verschiedenen Sprachversionen als solche.

* [](msm/overview.md) MSMmanagt die Bereitstellung übersetzter Inhalte von einem Blueprint (d. h. einem globalen Übergeordnete) zu den Live Copies (d. h. den lokalen Sites) innerhalb der Grenzen einer Sprache.
* Die AEM-Integrationsfunktionen zur [Übersetzung](translation/overview.md) verwalten kombiniert mit Übersetzungsmanagementdiensten von Drittanbietern die Sprachen und die Übersetzung der Inhalte in diese verschiedenen Sprachen.

Bei noch komplexeren Nutzungsszenarien kann MSM auch über Sprach-Master hinweg eingesetzt werden.

>[!TIP]
>
>Bei allen Nutzungsszenarien wird empfohlen, die folgenden Best Practices zu lesen:
>
>* [Best Practices für MSM](msm/best-practices.md)
* [Best Practices für die Übersetzung](translation/best-practices.md)

