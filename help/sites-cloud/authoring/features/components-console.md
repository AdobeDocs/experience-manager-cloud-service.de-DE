---
title: Komponentenkonsole
description: Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind.
exl-id: f4949331-5302-46d3-a004-b813bb95ec2f
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 100%

---

# Komponentenkonsole {#components-console}

Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind, und wichtige Informationen für jede Komponente anzuzeigen.

Auf sie kann über **Tools** > **Allgemein** > **Komponenten** zugegriffen werden. Da es keine Baumstruktur für Komponenten gibt, ist nur die Listenansicht verfügbar.

![Die Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>In der Komponentenkonsole werden alle im System vorhandenen Komponenten angezeigt. Im [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) werden Komponenten angezeigt, die Autoren zur Verfügung stehen, und alle Komponentengruppen verborgen, die mit einem Punkt beginnen (`.`).

## Suche {#search-field}

Mit dem Symbol **Nur Inhalt** (oben links) können Sie den **Suchbereich** öffnen, um die Komponenten zu durchsuchen und/oder zu filtern: 

![Suchen in der Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console-search.png)

### Komponentendetails {#component-details}

Um weitere Einzelheiten zu einer bestimmten Komponente anzuzeigen, tippen/klicken Sie auf die gewünschte Ressource. Die drei Registerkarten bieten:

* **Eigenschaften**

   ![Eigenschaften der Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console-properties.png)

   In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

   * Ansehen der allgemeinen Eigenschaften der Komponente
      * Sehen Sie sich an, wie das Symbol oder die Abkürzung für die Komponente definiert wurde. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Durch Klicken auf die Symbolquelle gelangen Sie zu dieser Komponente.
   * Ansehen des **Ressourcentyps** und des **Ressourcen-Supertyps** (sofern definiert) für die Komponente
      * Durch Klicken auf den Ressourcen-Supertyp gelangen Sie zu dieser Komponente.

   >[!NOTE]
   >
   >Da `/apps` zur Laufzeit nicht bearbeitet werden kann, ist die Komponentenkonsole schreibgeschützt.

* **Richtlinien**

   ![Richtlinien der Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console-policies.png)

* **Live-Nutzung**

   ![Live-Nutzung von Komponenten](/help/sites-cloud/authoring/assets/components-console-live-usage.png)

   >[!CAUTION]
   >
   >Aufgrund der Art der Informationen, die für diese Ansicht erfasst werden, kann es eine Weile dauern, bis sie zusammengestellt/angezeigt wird. 

* **Dokumentation**

   Etwaige vom Entwickler für eine Komponente bereitgestellte Dokumentationen werden auf der Registerkarte **Dokumentation** angezeigt. Ist keine Dokumentation verfügbar, wird die Registerkarte **Dokumentation** nicht angezeigt. <!-- If the developer has provided [documentation for the component](/help/sites-developing/developing-components.md#documenting-your-component), it will appear on the **Documentation** tab. If there is no documentation available, the **Documentation** tab will not be shown.-->

   ![Dokumentation zu Komponenten](/help/sites-cloud/authoring/assets/components-console-documentation.png)
