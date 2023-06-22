---
title: Multi Site Manager und Übersetzung
description: Erfahren Sie, wie Sie Ihre Inhalte projektübergreifend wiederverwenden und mehrsprachige Websites in AEM verwalten können.
feature: Administering
role: Admin
exl-id: a3d48884-081e-44f8-8055-ee3657757bfd
source-git-commit: 1fc57dacbf811070664d5f5aaa591dd705516fa8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 49%

---

# Multi Site Manager und Übersetzung {#msm-and-translation}

Multi Site Manager und Übersetzungs-Tools von Adobe Experience Manager vereinfachen die Lokalisierung Ihrer Inhalte.

* Multi Site Manager (MSM) und seine Live Copy-Funktionen ermöglichen Ihnen die Verwendung desselben Site-Inhalts sowie deren Variationen an mehreren Orten:
   * [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](msm/overview.md)
* Die Übersetzungsfunktion ermöglicht Ihnen die Automatisierung der Übersetzung von Seiteninhalten, um mehrsprachige Websites zu erstellen und zu pflegen:
   * [Übersetzen von Inhalten für mehrsprachige Sites](translation/overview.md)

Diese beiden Funktionen können kombiniert und für [internationale, mehrsprachige](#multinational-and-multilingual-sites) Websites eingesetzt werden.

>[!TIP]
>
>Wenn Sie mit der Übersetzung von Inhalten noch nicht vertraut sind, lesen Sie [Sites Translation Journey](/help/journey-sites/translation/overview.md). Es handelt sich um einen geführten Weg durch die Übersetzung Ihrer AEM Sites-Inhalte mit AEM leistungsstarken Übersetzungstools. Ideal, wenn Sie keine AEM- oder Übersetzungserfahrung haben.

## Internationale, mehrsprachige Websites {#multinational-and-multilingual-sites}

Sie können durch den kombinierten Einsatz von Multi Site Manager und Übersetzungs-Workflow auf effiziente Weise Inhalte für internationale, mehrsprachige Websites erstellen.

In der Regel erstellen Sie eine primäre Site in einer Sprache und für ein bestimmtes Land und verwenden diese Inhalte dann als Grundlage für die anderen Sites, wobei Sie bei Bedarf eine Übersetzung verwenden.

1. [Übersetzen](translation/overview.md) die primäre Site in verschiedene Sprachen unterteilt.
1. Verwenden Sie [Multi Site Manager](msm/overview.md) für Folgendes:
   1. Wiederverwenden von Inhalten der primären Site und deren Übersetzungen, um Websites für andere Länder und Kulturen zu erstellen.
   1. Trennen Sie bei Bedarf Elemente von den Live Copies, um Lokalisierungsdetails hinzuzufügen.

>[!TIP]
>
>Beschränken Sie die Verwendung von Multi Site Manager auf Inhalte in einer Sprache.
>
>Verwenden Sie beispielsweise das primäre Englisch , um die englische Version der Seiten für die USA, Kanada und Großbritannien zu erstellen. Verwenden Sie dann die primäre französische Version, um die französische Seitenversion für Frankreich, die Schweiz, Kanada usw. zu erstellen.

Das folgende Diagramm veranschaulicht, wie sich die Hauptkonzepte überschneiden (es sind jedoch nicht alle beteiligten Ebenen/Elemente dargestellt):

![Übersicht über die lokale Anpassung](assets/localization-overview.png)

In diesem Szenario und vergleichbaren Versionen verwaltet MSM nicht die verschiedenen Sprachversionen als solche.

* [MSM](msm/overview.md) verwaltet die Bereitstellung übersetzter Inhalte von einem Blueprint (d. h. einem primären globalen Design) zu den Live Copies (d. h. den lokalen Sites) innerhalb der Grenzen einer Sprache.
* Die [Übersetzung](translation/overview.md) Integrationsfunktionen von AEM mit Übersetzungsmanagementdiensten von Drittanbietern verwalten die Sprachen und übersetzen Inhalte in diese verschiedenen Sprachen.

Für erweiterte Anwendungsfälle kann MSM auch in allen Primärsprachen verwendet werden.

>[!TIP]
>
>Bei allen Nutzungsszenarien wird empfohlen, die folgenden Best Practices zu lesen:
>
>* [Best Practices für MSM](msm/best-practices.md)
>* [Best Practices für die Übersetzung](translation/best-practices.md)
