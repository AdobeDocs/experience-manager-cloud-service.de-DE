---
title: Anpassen der Ansichten von Seiteneigenschaften
description: Erfahren Sie, wie Seiteneigenschaften von Autorinnen und Autoren angezeigt und bearbeitet werden können.
exl-id: 363b3c2d-f965-485f-bdae-2ea5b4cecb83
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# Anpassen der Ansichten von Seiteneigenschaften{#customizing-views-of-page-properties}

Jede Seite verfügt über einen Satz von [Eigenschaften](/help/sites-cloud/authoring/sites-console/page-properties.md), die von Benutzenden angezeigt und bearbeitet werden können. Einige sind beim Erstellen der Seite erforderlich (Ansicht erstellen), andere können später angezeigt und bearbeitet werden (Ansicht bearbeiten). Diese Seiteneigenschaften werden über das Dialogfeld (`cq:dialog`) der entsprechenden Seitenkomponente definiert und bereitgestellt.

Der Standardstatus für jede Seiteneigenschaft ist wie folgt:

* In der Erstellungsansicht ausgeblendet (z. B. im **Seitenerstellungsassistenten**)

* In der Bearbeitungsansicht verfügbar (z. B. unter **Eigenschaften anzeigen**)

Felder müssen einzeln konfiguriert werden, wenn eine Änderung erforderlich ist. Dies erfolgt mithilfe der entsprechenden Knoteneigenschaften:

* Seiteneigenschaft, die in der Erstellungsansicht verfügbar sein soll (z. B. im **Seitenerstellungsassistenten**):

   * Name: `cq:showOnCreate`
   * Typ: `Boolean`

* Seiteneigenschaft, die in der Bearbeitungsansicht verfügbar sein soll (z. B. die Option **Anzeigen**/**Bearbeiten**) **Eigenschaften**:

   * Name: `cq:hideOnEdit`
   * Typ: `Boolean`

>[!TIP]
>
>Eine Anleitung zum Anpassen der Seiteneigenschaften finden Sie im [Tutorial zum Erweitern der Seiteneigenschaften](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html?lang=de).

## Konfigurieren von Seiteneigenschaften {#configuring-your-page-properties}

Sie können diese Felder auch konfigurieren, indem Sie das Dialogfeld Ihrer Seitenkomponente konfigurieren und die entsprechenden Knoteneigenschaften anwenden.

Beispiel: Der [**Seitenerstellungsassistent**](/help/sites-cloud/authoring/sites-console/creating-pages.md#creating-a-new-page) zeigt standardmäßig die Felder an, die unter **Weitere Titel und Beschreibungen** gruppiert sind. Um diese auszublenden, nehmen Sie folgende Konfiguration vor:

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

   Der Abschnitt **Weitere Titel und Beschreibungen** wird nicht mehr im **Seitenerstellungsassistenten** angezeigt.

>[!NOTE]
>
>Wenn Sie Seiteneigenschaften für die Verwendung mit Live Copies konfigurieren, finden Sie weitere Details unter [Erweitern des Multi Site Managers](/help/implementing/developing/extending/msm.md#configuring-msm-locks-on-page-properties).

## Beispielkonfiguration von Seiteneigenschaften {#sample-configuration-of-page-properties}

Dieses Beispiel zeigt die „dialog diff“-Technik von [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md), einschließlich der Verwendung von [`sling:orderBefore`](/help/implementing/developing/introduction/sling-resource-merger.md#properties). Es zeigt auch die Verwendung von `cq:showOnCreate` und `cq:hideOnEdit`.

Den Code dieser Seite finden Sie auf [GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog).
