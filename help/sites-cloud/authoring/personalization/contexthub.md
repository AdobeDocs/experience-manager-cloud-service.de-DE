---
title: Vorschau von Seiten mit ContextHub-Daten
description: In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können Sie mithilfe der Leiste Store-Daten bearbeiten und Inhalte in der Vorschau ansehen.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 9c0536c5-900e-4814-9e31-f9fee5adc17c
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 98%

---

# Vorschau von Seiten mit ContextHub-Daten  {#previewing-pages-using-contexthub-data}

In der ContextHub-Symbolleiste werden Daten aus ContextHub Stores angezeigt. Außerdem können mithilfe dieser Leiste Store-Daten bearbeitet werden. Die ContextHub-Symbolleiste ist für die Vorschau von Inhalten nützlich, die durch Daten in einem ContextHub-Store bestimmt werden.

Die Symbolleiste besteht aus einer Reihe von UI-Modi, die ein oder mehrere UI-Module enthalten.

* UI-Modi sind Symbole, die links in der Symbolleiste angezeigt werden. Wenn Sie ein Symbol auswählen, zeigt die Symbolleiste die UI-Module an, die sie enthält.
* UI-Module zeigen Daten aus einem oder mehreren ContextHub-Stores an. Einige UI-Module ermöglichen es Ihnen auch, Store-Daten zu bearbeiten.

Es werden verschiedene Benutzeroberflächenmodi und -module von ContextHub installiert. Möglicherweise hat Ihr Admin [ContextHub so konfiguriert](/help/implementing/developing/personalization/configuring-contexthub.md), dass andere Module als die hier gezeigten dargestellt werden.

## Einblenden der ContextHub-Symbolleiste {#revealing-the-contexthub-toolbar}

Die ContextHub-Symbolleiste ist im Vorschaumodus verfügbar. Die Symbolleiste wird nur für Autoreninstanzen angezeigt, wenn diese Funktion zuvor vom Administrator aktiviert wurde.

![Die ContextHub-Symbolleiste](/help/sites-cloud/authoring/assets/contexthub-toolbar.png)

1. Wählen Sie bei zur Bearbeitung geöffneter Seite die Vorschauoption in der Symbolleiste aus.

   ![Die Vorschauschaltfläche](/help/sites-cloud/authoring/assets/contexthub-preview-button.png)

1. Um die Symbolleiste anzuzeigen, wählen Sie das Symbol „ContextHub“ aus.

   ![Die ContextHub-Schaltfläche](/help/sites-cloud/authoring/assets/contexthub-button.png)

## Benutzeroberflächenmodul-Funktionen {#ui-module-features}

Jedes UI-Modul bietet unterschiedliche Funktionen, die folgenden Arten von Funktionen sind jedoch allgemein üblich. Da sich die UI-Module erweitern lassen, können Entwicklerinnen und Entwickler je nach Wunsch weitere Funktionen implementieren.

### Inhalt der Symbolleiste {#toolbar-content}

Mit den Benutzeroberflächenmodulen können in der Symbolleiste Daten aus einem oder mehr ContextHub-Stores eingeblendet werden. Benutzeroberflächenmodule lassen sich anhand ihres Symbols oder Titels identifizieren.

![ContextHub-Rollen](/help/sites-cloud/authoring/assets/contexthub-persona-button.png)

### Popup-Inhalt {#popup-content}

Einige UI-Module zeigen ein überlagertes Popup an, wenn darauf geklickt oder getippt wird. In der Regel enthält das Popup zusätzlich zu den in der Symbolleiste verfügbaren Informationen weitere Daten.

![ContextHub-Profilinformationen](/help/sites-cloud/authoring/assets/contexthub-profile.png)

### Popup-Formulare {#popup-forms}

In einigen Popup-Überlagerungen eines Moduls befinden sich Formularelemente, mit deren Hilfe Sie Daten im ContextHub Store bearbeiten können. Wenn Seiteninhalt durch die Store-Daten bestimmt wird, können Sie das Formular verwenden und Änderungen am Seiteninhalt beobachten.

### Vollbildmodus {#fullscreen-mode}

Popup-Überlagerungen können ein Symbol enthalten, das Sie auswählen können, um den Popup-Inhalt so zu erweitern, dass er das gesamte Browser-Fenster oder den Bildschirm einnimmt.

![Schaltfläche „Vollbild“](/help/sites-cloud/authoring/assets/contexthub-fullscreen.png)
