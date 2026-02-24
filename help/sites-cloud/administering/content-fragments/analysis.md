---
title: Analysieren von Inhaltsfragmenten
description: Machen Sie sich mit der Struktur Ihrer Inhaltsfragmente vertraut. Hier finden Sie Informationen, die sowohl für die Headless-Bereitstellung als auch für die Erstellung von Seiten relevant sind.
feature: Content Fragments
role: User, Developer
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: d9268c1a-bfe6-4df7-bad9-6007dd79e0aa
solution: Experience Manager Sites
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 97%

---

# Analysieren der Struktur von Inhaltsfragmenten {#analyzing-content-fragments-structure}

Inhaltsfragmente sind für die [Headless-Bereitstellung mit GraphQL](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md) konzipiert. Dies bedeutet, dass sie eine mehrschichtige Struktur haben können.

Experience Manager (AEM) bietet verschiedene Methoden zum Anzeigen und Analysieren der Fragmentstruktur.

## Verweise {#references}

Die mehrschichtige Struktur wird mithilfe von Verweisen aufgebaut:

* [Datentypen für Verweise werden im Inhaltsfragmentmodell definiert](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#using-references-to-form-nested-content)
* Beim Authoring (Bearbeiten) haben Sie folgende Möglichkeiten:
   * [Verwalten dieser Verweise](/help/sites-cloud/administering/content-fragments/authoring.md##manage-references)
   * [Suchen von übergeordneten Verweisen Ihres Fragments](/help/sites-cloud/administering/content-fragments/managing.md#parent-references-fragment)

## Strukturbaum {#structure-tree}

Öffnen Sie die Registerkarte **Baumstruktur** über die Editor-Symbolleiste, um die hierarchische Struktur des Inhaltsfragments und dessen Verweise anzuzeigen. Verwenden Sie das Link-Symbol, um Verweise zu öffnen.

Zum Beispiel:

![Inhaltsfragmenteditor – Baumstruktur](assets/cf-authoring-structure-tree.png)
