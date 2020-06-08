---
title: Vorschau von Seiten mit ContextHub-Daten
description: In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können Sie mithilfe der Leiste Store-Daten bearbeiten und Inhalte in der Vorschau ansehen.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 100%

---


# Vorschau von Seiten mit ContextHub-Daten {#previewing-pages-using-contexthub-data}

In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können mithilfe der Leiste Store-Daten bearbeitet werden. Die ContextHub-Symbolleiste eignet sich besonders für die Vorschau von Inhalten, die durch Daten im ContextHub Store gesteuert werden.<!--The [ContextHub](/help/sites-developing/contexthub.md) toolbar displays data from ContextHub stores and enables you to change store data. The ContextHub toolbar is useful for previewing content that is determined by data in a ContextHub store.-->

Diese Symbolleiste besteht aus einer Reihe Benutzeroberflächenmodi, die eines oder mehrere Oberflächenmodule enthalten.

* Benutzeroberflächenmodi werden durch die Symbole links in der Symbolleiste dargestellt. Klicken oder tippen Sie auf ein solches Symbol, zeigt die Symbolleiste die im Modus enthaltenen Benutzeroberflächenmodule an.
* In den Oberflächenmodulen werden Daten aus einem oder mehreren ContextHub Stores dargestellt. Einige Oberflächenmodule ermöglichen die Bearbeitung von Store-Daten.

Es werden verschiedene Benutzeroberflächenmodi und -module von ContextHub installiert. Möglicherweise hat Ihr Administrator ContextHub so konfiguriert, dass andere Module als die hier gezeigten dargestellt werden.<!--ContextHub installs several UI modes and UI modules. Your administrator may have [configured ContextHub](/help/sites-administering/contexthub-config.md) to display different ones.-->

## Einblenden der ContextHub-Symbolleiste {#revealing-the-contexthub-toolbar}

Die ContextHub-Symbolleiste ist im Vorschaumodus verfügbar. Die Symbolleiste wird nur für Autoreninstanzen angezeigt, wenn diese Funktion zuvor vom Administrator aktiviert wurde.

![Die ContextHub-Symbolleiste](/help/sites-cloud/authoring/assets/contexthub-toolbar.png)

1. Klicken oder tippen Sie bei zur Bearbeitung geöffneter Seite auf die Vorschauoption.

   ![Die Vorschauschaltfläche](/help/sites-cloud/authoring/assets/contexthub-preview-button.png)

1. Klicken oder tippen Sie auf das ContextHub-Symbol, um die Symbolleiste einzublenden.

   ![Die ContextHub-Schaltfläche](/help/sites-cloud/authoring/assets/contexthub-button.png)

## Benutzeroberflächenmodul-Funktionen {#ui-module-features}

Jedes Benutzeroberflächenmodul verfügt über eigene Funktionen, es stehen jedoch auch folgende gemeinsam genutzte Funktionen zur Verfügung. Da sich die Benutzeroberflächenmodule erweitern lassen, können Entwickler je nach Wunsch weitere Funktionen einbauen.

### Inhalt der Symbolleiste   {#toolbar-content}

Mit den Benutzeroberflächenmodulen können in der Symbolleiste Daten aus einem oder mehr ContextHub-Stores eingeblendet werden. Benutzeroberflächenmodule lassen sich anhand ihres Symbols oder Titels identifizieren.

![ContextHub-Rollen](/help/sites-cloud/authoring/assets/contexthub-persona-button.png)

### Popup-Inhalt {#popup-content}

Einige Benutzeroberflächenmodule zeigen ein überlagertes Popup an, wenn darauf geklickt oder getippt wird. In der Regel enthält das Popup zusätzlich zu den in der Symbolleiste verfügbaren Informationen weitere Daten.

![ContextHub-Profilinformationen](/help/sites-cloud/authoring/assets/contexthub-profile.png)

### Popup-Formulare {#popup-forms}

In einigen Popup-Overlays der Benutzeroberflächenmodule befinden sich Formularelemente, mit deren Hilfe Sie Daten im ContextHub Store bearbeiten können. Steuern diese Store-Daten Seiteninhalte, können Sie mit dem Formular Änderungen vornehmen, die sich dann in den Seiteninhalten widerspiegeln.

### Vollbildmodus   {#fullscreen-mode}

Die Popup-Überlagerung kann ein Symbol enthalten, auf das Sie klicken oder tippen können, um den Popup-Inhalt so zu erweitern, dass er das gesamte Browser-Fenster oder den Bildschirm einnimmt.

![Schaltfläche „Vollbild“](/help/sites-cloud/authoring/assets/contexthub-fullscreen.png)
