---
title: Verwenden der Erweiterung für externe AJO-Verweise in Inhaltsfragmenten
description: Erfahren Sie mehr über die Erweiterung für externe AJO-Verweise in Inhaltsfragmenten
feature: Content Fragments
role: User, Developer
solution: Experience Manager Sites
exl-id: 79c90e6b-91da-4f5a-ac96-a98ef7f8d4cd
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 100%

---

# Die Erweiterung für externe AJO-Verweise in Inhaltsfragmenten {#content-fragment-external-references-extension}

Um Erlebnisse aus AEM für ein anderes Adobe-Produkt in der Vorschau anzuzeigen, können Sie die UI-Erweiterung aktivieren:

* **Externe AJO-Verweise**

Die Erweiterung für externe AJO-Verweise funktioniert durch Abrufen von Verweisen auf Inhaltsfragmente aus allen Organisationen und Sandboxes, die mit vordefinierten Tags verknüpft sind. Die Erweiterung zeigt dann Details an.

Bei einer Integration mit Adobe Journey Optimizer (AJO) hängen die Details beispielsweise davon ab, ob es sich bei der Referenz um eine Kampagne, eine Journey oder eine Vorlage handelt.

>[!NOTE]
>
>Weitere Informationen zum Aktivieren der Erweiterung finden Sie unter [Extension Manager in AEM Experience Manager](https://developer.adobe.com/uix/docs/extension-manager/).

So verwenden Sie beispielsweise die Erweiterung mit AJO:

>[!NOTE]
>
>Siehe auch [AJO-Integration](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/integrations/aem-fragments).

1. Öffnen Sie die [Inhaltsfragmente-Konsole](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console).

1. Navigieren Sie zu Ihrem Inhaltsfragment – dem Fragment, das über verschiedene AJO-Kanäle hinweg erstellt und verwendet wurde.

1. Öffnen Sie das Inhaltsfragment im [Editor](/help/sites-cloud/administering/content-fragments/managing.md#editing-the-content-of-your-fragment).

1. Die Erweiterung für externe AJO-Verweise ist als Registerkarte im rechten Panel verfügbar. Wählen Sie die Registerkarte aus, um die Erweiterung zu öffnen:

   ![Erweiterung für externe AJO-Verweise](/help/sites-cloud/administering/content-fragments/assets/cf-ajo-fragment-external-references-extension.png)

   Sobald ein Verweistyp ausgewählt ist, zeigt die Erweiterung die entsprechenden externen Verweise als Tabelle mit folgenden Spalten an:

   * **Name**: Der Name des Verweises, in dem das Inhaltsfragment verwendet wird
   * **Vorschau**: Wählen Sie diesen Link aus, um die Vorschau zu starten
   * **Status**: Der Status des Verweises

1. Sie können den **Verweistyp** aus der Dropdown-Liste auswählen und zwischen drei Verweistypen wechseln:

   * **Kampagne**
      * Zeigt eine Liste aller Kampagnen mit Links zum aktuellen Inhaltsfragment an.
      * Sie können dann eine ausgewählte Kampagne in der Vorschau anzeigen.
      * Standard
   * **Journey**
      * Zeigt die neueste Journey an.
      * Sie können dann eine ausgewählte Journey auswählen und in der Vorschau anzeigen.
   * **Vorlage**
      * Zeigt Vorlagen für das Inhaltsfragment an.
      * Anschließend können Sie eine ausgewählte Vorlage wählen und in der Vorschau anzeigen.
