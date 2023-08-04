---
title: Anpassen der Ansichten von Seiteneigenschaften
description: Erfahren Sie, wie Seiteneigenschaften von Autoren angezeigt und bearbeitet werden.
source-git-commit: f159f0ef86c2b82da4e7308a0892b4947b6e43fb
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 43%

---


# Anpassen der Ansichten von Seiteneigenschaften{#customizing-views-of-page-properties}

Jede Seite verfügt über einen Satz von [properties](/help/sites-cloud/authoring/fundamentals/page-properties.md) die von Benutzern angezeigt und bearbeitet werden können. Einige sind beim Erstellen der Seite erforderlich (Ansicht erstellen), andere können später angezeigt und bearbeitet (Ansicht bearbeiten) werden. Diese Seiteneigenschaften werden über das Dialogfeld (`cq:dialog`) der entsprechenden Seitenkomponente definiert und bereitgestellt.

Der Standardstatus für jede Seiteneigenschaft ist wie folgt:

* In der Erstellungsansicht ausgeblendet (z. B. **Seite erstellen** wizard)

* In der Bearbeitungsansicht verfügbar (z. B. **Eigenschaften anzeigen**)

Felder müssen bei Bedarf spezifisch konfiguriert werden. Dies geschieht mithilfe der entsprechenden Knoteneigenschaften:

* Seiteneigenschaft, die in der Erstellungsansicht verfügbar sein soll (z. B. **Seite erstellen** Assistent):

   * Name: `cq:showOnCreate`
   * Typ: `Boolean`

* Seiteneigenschaft, die in der Bearbeitungsansicht verfügbar sein soll, z. B. **Ansicht**/**Bearbeiten**  **Eigenschaften** Option:

   * Name: `cq:hideOnEdit`
   * Typ: `Boolean`

>[!TIP]
>
>Eine Anleitung zum Anpassen der Seiteneigenschaften finden Sie im [Tutorial zum Erweitern der Seiteneigenschaften](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html?lang=de).

## Konfigurieren der Seiteneigenschaften {#configuring-your-page-properties}

Sie können auch die verfügbaren Felder konfigurieren, indem Sie das Dialogfeld Ihrer Seitenkomponente konfigurieren und die entsprechenden Knoteneigenschaften anwenden.

Beispiel: Der [**Seitenerstellungsassistent**](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) zeigt standardmäßig die Felder an, die unter **Weitere Titel und Beschreibungen** gruppiert sind. Um diese auszublenden, nehmen Sie folgende Konfiguration vor:

1. Erstellen Sie Ihre Seitenkomponente unter `/apps`.
1. Erstellen Sie eine Überschreibung (mit *dialog diff*, das von [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) bereitgestellt wird) für den Abschnitt `basic` der Seitenkomponente. Beispiel:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

1. Legen Sie die Eigenschaft `path` auf `basic` fest, um auf die Überschreibung der Registerkarte „Standard“ zu verweisen (siehe auch den nächsten Schritt). Beispiel:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Erstellen Sie eine Überschreibung des Abschnitts `basic` - `moretitles` am entsprechenden Pfad; Beispiel:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Wenden Sie die entsprechende Knoteneigenschaft an:

   * **Name**: `cq:showOnCreate`
   * **Typ**: `Boolean`
   * **Wert**: `false`

   Die **Weitere Titel und Beschreibungen** wird nicht mehr im Abschnitt **Seite erstellen** Assistent.

>[!NOTE]
>
>Informationen zum Konfigurieren von Seiteneigenschaften für die Verwendung mit Live Copies finden Sie im Dokument . [Erweitern des Multi-Site-Managers](/help/implementing/developing/extending/msm.md#configuring-msm-locks-on-page-properties) für weitere Details.

## Beispielkonfiguration von Seiteneigenschaften {#sample-configuration-of-page-properties}

In diesem Beispiel wird die Dialogfeldvergleichstechnik des [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) einschließlich der Verwendung [`sling:orderBefore`](/help/implementing/developing/introduction/sling-resource-merger.md#properties). Es zeigt auch die Verwendung von `cq:showOnCreate` und `cq:hideOnEdit`.

Den Code dieser Seite finden Sie unter [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
