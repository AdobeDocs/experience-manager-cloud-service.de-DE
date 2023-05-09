---
title: Vorschau von Seiten mit ContextHub-Daten
description: In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können Sie mithilfe der Leiste Store-Daten bearbeiten und Inhalte in der Vorschau ansehen.
exl-id: 9c0536c5-900e-4814-9e31-f9fee5adc17c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 57%

---

# Vorschau von Seiten mit ContextHub-Daten  {#previewing-pages-using-contexthub-data}

In der ContextHub-Symbolleiste werden Daten aus ContextHub-Stores angezeigt und Sie können Store-Daten ändern. Die ContextHub-Symbolleiste ist für die Vorschau von Inhalten nützlich, die durch Daten in einem ContextHub-Store bestimmt werden.

Die Symbolleiste besteht aus einer Reihe von Benutzeroberflächenmodi, die ein oder mehrere Benutzeroberflächenmodule enthalten.

* Benutzeroberflächenmodi sind Symbole, die links in der Symbolleiste angezeigt werden. Wenn Sie auf ein Symbol klicken oder tippen, zeigt die Symbolleiste die darin enthaltenen UI-Module an.
* Benutzeroberflächenmodule zeigen Daten aus einem oder mehreren ContextHub-Stores an. Einige Benutzeroberflächenmodule ermöglichen es Ihnen auch, gespeicherte Daten zu bearbeiten.

Es werden verschiedene Benutzeroberflächenmodi und -module von ContextHub installiert. Möglicherweise hat Ihr Admin [ContextHub so konfiguriert](/help/implementing/developing/personalization/configuring-contexthub.md), dass andere Module als die hier gezeigten dargestellt werden.

## Einblenden der ContextHub-Symbolleiste {#revealing-the-contexthub-toolbar}

Die ContextHub-Symbolleiste ist im Vorschaumodus verfügbar. Die Symbolleiste wird nur für Autoreninstanzen angezeigt, wenn diese Funktion zuvor vom Administrator aktiviert wurde.

![Die ContextHub-Symbolleiste](/help/sites-cloud/authoring/assets/contexthub-toolbar.png)

1. Klicken oder tippen Sie bei zur Bearbeitung geöffneter Seite auf die Vorschauoption.

   ![Die Vorschauschaltfläche](/help/sites-cloud/authoring/assets/contexthub-preview-button.png)

1. Klicken oder tippen Sie auf das ContextHub-Symbol, um die Symbolleiste einzublenden.

   ![Die ContextHub-Schaltfläche](/help/sites-cloud/authoring/assets/contexthub-button.png)

## Benutzeroberflächenmodul-Funktionen {#ui-module-features}

Jedes UI-Modul bietet unterschiedliche Funktionen, die folgenden Arten von Funktionen sind jedoch üblich. Da UI-Module erweiterbar sind, kann Ihr Entwickler nach Bedarf andere Funktionen implementieren.

### Inhalt der Symbolleiste {#toolbar-content}

Mit den Benutzeroberflächenmodulen können in der Symbolleiste Daten aus einem oder mehr ContextHub-Stores eingeblendet werden. Benutzeroberflächenmodule lassen sich anhand ihres Symbols oder Titels identifizieren.

![ContextHub-Rollen](/help/sites-cloud/authoring/assets/contexthub-persona-button.png)

### Popup-Inhalt {#popup-content}

Einige Benutzeroberflächenmodule zeigen ein überlagertes Popup an, wenn darauf geklickt oder getippt wird. In der Regel enthält das Popup zusätzlich zu den in der Symbolleiste verfügbaren Informationen weitere Daten.

![ContextHub-Profilinformationen](/help/sites-cloud/authoring/assets/contexthub-profile.png)

### Popup-Formulare {#popup-forms}

In einigen Popup-Overlays der Benutzeroberflächenmodule befinden sich Formularelemente, mit deren Hilfe Sie Daten im ContextHub Store bearbeiten können. Wenn der Seiteninhalt durch die Speicherdaten bestimmt wird, können Sie das Formular verwenden und Änderungen am Seiteninhalt beobachten.

### Vollbildmodus {#fullscreen-mode}

Die Popup-Überlagerung kann ein Symbol enthalten, auf das Sie klicken oder tippen können, um den Popup-Inhalt so zu erweitern, dass er das gesamte Browser-Fenster oder den Bildschirm einnimmt.

![Schaltfläche „Vollbild“](/help/sites-cloud/authoring/assets/contexthub-fullscreen.png)
