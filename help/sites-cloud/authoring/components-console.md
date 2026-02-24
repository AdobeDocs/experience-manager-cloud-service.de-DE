---
title: Komponentenkonsole
description: Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: f4949331-5302-46d3-a004-b813bb95ec2f
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 98%

---

# Komponentenkonsole {#components-console}

Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind, und wichtige Informationen für jede Komponente anzuzeigen.

Über **Tools** > **Allgemein** > **Komponenten** kann auf sie zugegriffen werden. Da es keine Baumstruktur für Komponenten gibt, ist nur die Listenansicht verfügbar.

![Die Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>In der Komponentenkonsole werden alle im System vorhandenen Komponenten angezeigt. Im [Komponenten-Browser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) werden Komponenten angezeigt, die Autoren zur Verfügung stehen, und alle Komponentengruppen verborgen, die mit einem Punkt beginnen (`.`).

## Suchen {#search-field}

Mit dem Symbol **Nur Inhalt** (oben links) können Sie den **Suchbereich** öffnen, um die Komponenten zu durchsuchen und/oder zu filtern:

![Suchen in der Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console-search.png)

### Komponentendetails {#component-details}

Um Details zu einer bestimmten Komponente anzuzeigen, wählen Sie die gewünschte Ressource aus. Drei Registerkarten bieten Folgendes:

* **Eigenschaften**

  ![Eigenschaften der Komponentenkonsole](/help/sites-cloud/authoring/assets/components-console-properties.png)

  In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

   * Ansehen der allgemeinen Eigenschaften der Komponente
      * Sehen Sie sich an, wie das Symbol oder die Abkürzung für die Komponente definiert wurde. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Durch Klicken auf die Symbolquelle gelangen Sie zu dieser Komponente.
   * Zeigen Sie den **Ressourcentyp** und **Ressourcen-Supertyp** (sofern definiert) für die Komponente an.
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
