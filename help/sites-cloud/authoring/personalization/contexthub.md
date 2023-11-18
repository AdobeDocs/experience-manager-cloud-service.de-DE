---
title: Vorschau von Seiten mit ContextHub-Daten
description: In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können Sie mithilfe der Leiste Store-Daten bearbeiten und Inhalte in der Vorschau ansehen.
exl-id: 9c0536c5-900e-4814-9e31-f9fee5adc17c
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 72%

---

# Vorschau von Seiten mit ContextHub-Daten  {#previewing-pages-using-contexthub-data}

In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können mithilfe dieser Leiste Store-Daten bearbeitet werden. Die ContextHub-Symbolleiste ist für die Vorschau von Inhalten nützlich, die durch Daten in einem ContextHub-Store bestimmt werden.

Die Symbolleiste besteht aus einer Reihe von UI-Modi, die ein oder mehrere UI-Module enthalten.

* UI-Modi sind Symbole, die links in der Symbolleiste angezeigt werden. Wenn Sie ein Symbol auswählen, zeigt die Symbolleiste die darin enthaltenen Benutzeroberflächenmodule an.
* UI-Module zeigen Daten aus einem oder mehreren ContextHub-Stores an. Einige UI-Module ermöglichen es Ihnen auch, Store-Daten zu bearbeiten.

Es werden verschiedene Benutzeroberflächenmodi und -module von ContextHub installiert. Möglicherweise hat Ihr Admin [ContextHub so konfiguriert](/help/implementing/developing/personalization/configuring-contexthub.md), dass andere Module als die hier gezeigten dargestellt werden.

## Einblenden der ContextHub-Symbolleiste {#revealing-the-contexthub-toolbar}

Die ContextHub-Symbolleiste ist im Vorschaumodus verfügbar. Die Symbolleiste wird nur für Autoreninstanzen angezeigt, wenn diese Funktion zuvor vom Administrator aktiviert wurde.

![Die ContextHub-Symbolleiste](/help/sites-cloud/authoring/assets/contexthub-toolbar.png)

1. Wenn die Seite zur Bearbeitung geöffnet ist, wählen Sie in der Symbolleiste Vorschau aus.

   ![Die Vorschauschaltfläche](/help/sites-cloud/authoring/assets/contexthub-preview-button.png)

1. Um die Symbolleiste einzublenden, wählen Sie das ContextHub-Symbol aus.

   ![Die ContextHub-Schaltfläche](/help/sites-cloud/authoring/assets/contexthub-button.png)

## Benutzeroberflächenmodul-Funktionen {#ui-module-features}

Jedes UI-Modul bietet unterschiedliche Funktionen, die folgenden Arten von Funktionen sind jedoch allgemein üblich. Da sich die UI-Module erweitern lassen, können Entwicklerinnen und Entwickler je nach Wunsch weitere Funktionen implementieren.

### Inhalt der Symbolleiste {#toolbar-content}

Mit den Benutzeroberflächenmodulen können in der Symbolleiste Daten aus einem oder mehr ContextHub-Stores eingeblendet werden. Benutzeroberflächenmodule lassen sich anhand ihres Symbols oder Titels identifizieren.

![ContextHub-Rollen](/help/sites-cloud/authoring/assets/contexthub-persona-button.png)

### Popup-Inhalt {#popup-content}

Einige Benutzeroberflächenmodule zeigen eine Popup-Überlagerung an, wenn darauf geklickt oder getippt wird. In der Regel enthält das Popup zusätzliche Informationen, als in der Symbolleiste angezeigt werden.

![ContextHub-Profilinformationen](/help/sites-cloud/authoring/assets/contexthub-profile.png)

### Popup-Formulare {#popup-forms}

Die Popup-Überlagerung eines Moduls kann Formularelemente enthalten, mit denen Sie die Daten im ContextHub-Store ändern können. Wenn Seiteninhalt durch die Store-Daten bestimmt wird, können Sie das Formular verwenden und Änderungen am Seiteninhalt beobachten.

### Vollbildmodus {#fullscreen-mode}

Popup-Überlagerungen können ein Symbol enthalten, mit dem Sie den Popup-Inhalt erweitern und so das gesamte Browserfenster oder den gesamten Bildschirm abdecken.

![Schaltfläche „Vollbild“](/help/sites-cloud/authoring/assets/contexthub-fullscreen.png)
