---
title: Verwenden der Erweiterung für externe AJO-Verweise für Inhaltsfragmente
description: Erfahren Sie mehr über die Erweiterung "AJO External References“ von Inhaltsfragmenten
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
source-git-commit: f755a5c621b68b3110642e6cfe150798555b6707
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---


# Die Erweiterung Inhaltsfragment AJO External References . {#content-fragment-external-references-extension}

Um Erlebnisse aus AEM für ein anderes Adobe-Produkt in der Vorschau anzuzeigen, können Sie die Benutzeroberflächenerweiterung aktivieren:

* **Externe AJO-Referenzen**

Die AJO External References-Erweiterung funktioniert durch Abrufen von Verweisen auf Inhaltsfragmente aus allen Organisationen und Sandboxes, die mit vordefinierten Tags verknüpft sind. Die Erweiterung zeigt dann Details an.

Bei einer Integration mit Adobe Journey Optimizer (AJO) hängen die Details beispielsweise davon ab, ob es sich bei der Referenz um eine Kampagne, eine Journey oder eine Vorlage handelt.

>[!NOTE]
>
>Weitere Informationen zum Aktivieren der Erweiterung finden Sie unter [Extension Manager in AEM Experience Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

So verwenden Sie beispielsweise die -Erweiterung mit AJO:

>[!NOTE]
>
>Siehe auch [AJO-Integration](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/integrations/aem-fragments).

1. Öffnen Sie die [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console).

1. Navigieren Sie zu Ihrem Inhaltsfragment - dem Fragment, das über verschiedene AJO-Kanäle hinweg erstellt und verwendet wurde.

1. Öffnen Sie Ihr Inhaltsfragment im [Editor](/help/sites-cloud/administering/content-fragments/managing.md#editing-the-content-of-your-fragment).

1. Die Erweiterung &quot;AJO External References“ ist als Registerkarte im rechten Bedienfeld verfügbar. Wählen Sie die Registerkarte aus, um die Erweiterung zu öffnen:

   Erweiterung für ![AJO External References](/help/sites-cloud/administering/content-fragments/assets/cf-ajo-fragment-external-references-extension.png)

   Sobald ein Verweistyp ausgewählt ist, zeigt die Erweiterung die entsprechenden externen Verweise als Tabelle mit den Spalten an:

   * **Name**: der Name der Referenz, in der das Inhaltsfragment verwendet wird
   * **Vorschau** Wählen Sie diesen Link, um die Vorschau zu starten.
   * **Status**: der Status der Referenz

1. Sie können den **Verweistyp** aus der Dropdown-Liste auswählen, um zwischen drei Verweistypen zu wechseln:

   * **Kampagne**
      * Zeigt eine Liste aller Kampagnen mit Links zum aktuellen Inhaltsfragment an.
      * Sie können dann eine ausgewählte Kampagne in der Vorschau anzeigen.
      * Standard
   * **Journey**
      * Zeigt die neueste Journey an.
      * Sie können dann eine ausgewählte Journey auswählen und in der Vorschau anzeigen.
   * **Vorlage**
      * Zeigt Vorlagen für das Inhaltsfragment an.
      * Anschließend können Sie eine ausgewählte Vorlage auswählen und in der Vorschau anzeigen.