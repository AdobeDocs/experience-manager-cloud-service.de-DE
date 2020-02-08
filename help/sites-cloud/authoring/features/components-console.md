---
title: Komponentenkonsole
description: Mit der Komponenten-Konsole können Sie alle für Ihre Instanz definierten Komponenten durchsuchen
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Komponentenkonsole {#components-console}

Mit der Komponenten-Konsole können Sie alle für Ihre Instanz definierten Komponenten durchsuchen und wichtige Informationen zu jeder Komponente anzeigen.

It can be accessed from **Tools ->** **General ->** **Components**. Da es keine Baumstruktur für Komponenten gibt, ist nur die Listenansicht verfügbar.

![Die Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>Die Komponentenkonsole zeigt alle Komponenten im System an. Im [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) werden Komponenten angezeigt, die Autoren zur Verfügung stehen, und alle Komponentengruppen verborgen, die mit einem Punkt beginnen ( `.`).

## Suche{#search-field}

Mit dem Symbol **Nur Inhalt** (oben links) können Sie den **Suchbereich** öffnen, um die Komponenten zu durchsuchen und/oder zu filtern: 

![Suchen in der Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console-search.png)

### Komponentendetails {#component-details}

Um weitere Einzelheiten zu einer bestimmten Komponente anzuzeigen, tippen/klicken Sie auf die gewünschte Ressource. Die drei Registerkarten bieten:

* **Eigenschaften**

   ![Komponentenkonsole - Eigenschaften](/help/sites-cloud/authoring/assets/components-console-properties.png)

   In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

   * Ansehen der allgemeinen Eigenschaften der Komponente
      * View how the icon or abbreviation has been defined for the component. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Durch Klicken auf die Symbolquelle gelangen Sie zu dieser Komponente.
   * Ansehen des **Ressourcentyps** und des **Ressourcen-Supertyps** (sofern definiert) für die Komponente
      * Durch Klicken auf den Ressourcen-Supertyp gelangen Sie zu dieser Komponente.
   >[!NOTE]
   >
   >Because `/apps` is not editable at runtime, the Components Console is read-only.

* **Richtlinien**

   ![Komponentenkonsole - Richtlinien](/help/sites-cloud/authoring/assets/components-console-policies.png)

* **Live-Nutzung**

   ![Live-Nutzung von Komponenten](/help/sites-cloud/authoring/assets/components-console-live-usage.png)

   >[!CAUTION]
   >
   >Aufgrund der Art der Informationen, die für diese Ansicht erfasst werden, kann es eine Weile dauern, bis sie zusammengestellt/angezeigt wird. 

* **Dokumentation**

   Etwaige vom Entwickler für eine Komponente bereitgestellte Dokumentation wird auf der Registerkarte **Dokumentation** angezeigt. Ist keine Dokumentation verfügbar, wird die Registerkarte **Dokumentation** nicht angezeigt. <!-- If the developer has provided [documentation for the component](/help/sites-developing/developing-components.md#documenting-your-component), it will appear on the **Documentation** tab. If there is no documentation available, the **Documentation** tab will not be shown.-->

   ![Komponentendokumentation](/help/sites-cloud/authoring/assets/components-console-documentation.png)
