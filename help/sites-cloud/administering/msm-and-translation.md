---
title: Multi Site Manager und Übersetzung
description: Erfahren Sie, wie Sie Ihre Inhalte projektübergreifend wiederverwenden und mehrsprachige Websites in AEM verwalten können.
feature: Verwalten
role: Administrator
exl-id: a3d48884-081e-44f8-8055-ee3657757bfd
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 100%

---

# Multi Site Manager und Übersetzung {#msm-and-translation}

Multi Site Manager und Übersetzungs-Tools von Adobe Experience Manager vereinfachen die Lokalisierung Ihrer Inhalte.

* Multi Site Manager (MSM) und seine Live Copy-Funktionen ermöglichen Ihnen die Verwendung desselben Site-Inhalts sowie deren Variationen an mehreren Orten:
   * [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](msm/overview.md)
* Die Übersetzungsfunktion ermöglicht Ihnen die Automatisierung der Übersetzung von Seiteninhalten, um mehrsprachige Websites zu erstellen und zu pflegen:
   * [Übersetzen von Inhalten für mehrsprachige Sites](translation/overview.md)

Diese beiden Funktionen können kombiniert und für [internationale, mehrsprachige](#multinational-and-multilingual-sites) Websites eingesetzt werden.

## Internationale, mehrsprachige Sites {#multinational-and-multilingual-sites}

Sie können durch den kombinierten Einsatz von Multi Site Manager und Übersetzungs-Workflow auf effiziente Weise Inhalte für internationale, mehrsprachige Sites erstellen.

Erstellen Sie eine primäre Website in einer Sprache für ein bestimmtes Land und verwenden Sie diese Inhalte als Grundlage für die anderen Sites, wobei Sie bei Bedarf Übersetzungen einsetzen.

1. [Übersetzen](translation/overview.md) Sie die primäre Website in verschiedene Sprachen.
1. Verwenden Sie [Multi Site Manager](msm/overview.md) für Folgendes:
   1. Verwenden Sie die Inhalte der primären Website sowie ihre Übersetzungen, um Sites für andere Länder und Kulturen zu erstellen.
   1. Trennen Sie bei Bedarf Elemente von den Live Copies, um Lokalisierungsdetails hinzuzufügen.

>[!TIP]
>
>Beschränken Sie die Verwendung von Multi Site Manager auf Inhalte in einer Sprache.
>
>Verwenden Sie z. B. den englischen primären Inhalt, um die englische Seitenversion für die USA, Kanada, Großbritannien usw. zu erstellen, und den französischen primären Inhalt, um die französische Seitenversion für Frankreich, die Schweiz, Kanada usw. zu erstellen.

Das folgende Diagramm veranschaulicht, wie sich die Hauptkonzepte überschneiden (es sind jedoch nicht alle beteiligten Ebenen/Elemente dargestellt):

![Übersicht über die lokale Anpassung](assets/localization-overview.png)

Bei diesem und vergleichbaren Szenarien verwaltet MSM nicht die verschiedenen Sprachversionen als solche.

* [MSM](msm/overview.md) verwaltet die Bereitstellung der übersetzten Inhalte von einer Blueprint (d. h. einem globalen Stamm) für die Live Copies (d. h. die lokalen Sites) innerhalb einer Sprache.
* Die AEM-Integrationsfunktionen zur [Übersetzung](translation/overview.md) verwalten kombiniert mit Übersetzungs-Management-Services von Drittanbietern die Sprachen und die Übersetzung der Inhalte in diese verschiedenen Sprachen.

Bei noch komplexeren Nutzungsszenarien kann MSM auch über Sprachstämme hinweg eingesetzt werden.

>[!TIP]
>
>Bei allen Nutzungsszenarien wird empfohlen, die folgenden Best Practices zu lesen:
>
>* [Best Practices für MSM](msm/best-practices.md)
* [Best Practices für die Übersetzung](translation/best-practices.md)

