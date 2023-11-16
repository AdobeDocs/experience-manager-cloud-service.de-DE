---
title: Komponentenkonsole
description: Mit der Komponentenkonsole können Sie alle für Ihre Instanz definierten Komponenten durchsuchen
exl-id: f4949331-5302-46d3-a004-b813bb95ec2f
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 69%

---

# Komponentenkonsole {#components-console}

Mit der Komponentenkonsole können Sie alle für Ihre Instanz definierten Komponenten durchsuchen und wichtige Informationen zu den einzelnen Komponenten anzeigen.

Auf sie kann über **Tools** > **Allgemein** > **Komponenten** zugegriffen werden. Da es keine Baumstruktur für Komponenten gibt, ist nur die Listenansicht verfügbar.

![Die Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>In der Komponentenkonsole werden alle im System vorhandenen Komponenten angezeigt. Im [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) werden Komponenten angezeigt, die Autoren zur Verfügung stehen, und alle Komponentengruppen verborgen, die mit einem Punkt beginnen (`.`).

## Suchen {#search-field}

Mit dem Symbol **Nur Inhalt** (oben links) können Sie den **Suchbereich** öffnen, um die Komponenten zu durchsuchen und/oder zu filtern:

![Suchen in der Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console-search.png)

### Komponentendetails {#component-details}

Um Details zu einer bestimmten Komponente anzuzeigen, tippen/klicken Sie auf die gewünschte Ressource. Drei Registerkarten bieten:

* **Eigenschaften**

  ![Eigenschaften der Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console-properties.png)

  In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

   * Ansehen der allgemeinen Eigenschaften der Komponente
      * Sehen Sie sich an, wie das Symbol oder die Abkürzung für die Komponente definiert wurde. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Wenn Sie auf die Quelle des Symbols klicken, gelangen Sie zu dieser Komponente.
   * Anzeigen der **Ressourcentyp** und **Resource Super Type** (sofern definiert) für die Komponente.
      * Wenn Sie auf den Ressourcen-Supertyp klicken, gelangen Sie zu dieser Komponente.

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
