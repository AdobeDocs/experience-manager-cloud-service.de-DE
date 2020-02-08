---
title: Suchen
description: Rasches Auffinden Ihrer Inhalte dank umfassender Suchfunktionen
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Suche{#search-feature}

Die Autorenumgebung von AEM bietet abhängig vom Ressourcentyp verschiedene Möglichkeiten zur Inhaltssuche.

## Grundlagen zur Suche {#search-basics}

Die Suchfunktion ist über die obere Symbolleiste verfügbar:

![Suchschaltfläche](/help/sites-cloud/authoring/assets/search-button.png)

Die Suchleiste bietet Ihnen folgende Möglichkeiten:

* Suchen Sie nach einem bestimmten Keyword, Pfad oder Tag
* Filtern nach ressourcenspezifischen Kriterien, wie Änderungsdatumsangaben, Seitenstatus, Dateigröße usw.
* Definieren und Verwenden einer [gespeicherten Suche](#saved-searches), die auf den oben genannten Kriterien basiert

>[!NOTE]
>
>Search can also be invoked by using the hotkey `/` (forward slash) whenever the search rail is visible.

## Suchen und Filtern {#search-and-filter}

So durchsuchen und filtern Sie Ressourcen: 

1. Öffnen Sie die Option **Suchen** (mit der Lupe in der Symbolleiste) und geben Sie den Suchbegriff ein. Es werden Empfehlungen angezeigt, die Sie dann auswählen können:

   ![Suchbegriff](/help/sites-cloud/authoring/assets/search-term.png)

   Standardmäßig sind die Suchergebnisse auf den aktuellen Speicherort beschränkt (d. h. Konsole und Ressourcentyp): 

   ![Suchposition](/help/sites-cloud/authoring/assets/search-term-location.png)

1. Falls erforderlich, können Sie den Positionsfilter entfernen (wählen Sie dazu **X** neben dem Filter aus, den Sie entfernen möchten), um alle Konsolen/Ressourcentypen zu durchsuchen.
1. Die Ergebnisse werden angezeigt, und zwar gruppiert nach Konsole und Ressourcentyp.

   Sie können entweder eine spezifische Ressource (für eine spätere Aktion) oder eine Drilldown-Suche auswählen, indem Sie den erforderlichen Ressourcentyp auswählen, z. B. **Alle Sites anzeigen**: 

   ![Suchergebnisse](/help/sites-cloud/authoring/assets/search-results.png)

1. Wenn Sie weitere Details anzeigen möchten, wählen Sie das Symbol für die Seitenleiste (oben links) aus, um den Seitenbereich **Filter und Optionen** zu öffnen.

   ![Schaltfläche &quot;Leiste&quot;](/help/sites-cloud/authoring/assets/rail-button.png)

   Je nach Ressourcentyp zeigt Search eine vordefinierte Auswahl von Such-/Filterkriterien an.

   Im Seitenbereich können Sie folgende Elemente auswählen:

   * Gespeicherte Suchvorgänge
   * Verzeichnisse, die durchsucht werden sollen
   * Tags
   * Suchkriterien, z. B. Modifizierte Datumswerte, Veröffentlichungsstatus, LiveCopy-Status
   >[!NOTE]
   >
   >Die Suchkriterien können variieren:
   >
   >* abhängig vom ausgewählten Ressourcentyp – beispielsweise sind die Kriterien „Assets“ und „Communities“ nach Themen spezialisiert.
   >* je nach Instanz, da die Suchformulare (entsprechend der Stelle in AEM) angepasst werden können.

<!--
  >* Your instance as the [Search Forms](/help/sites-administering/search-forms.md) can be customized (appropriate to the location within AEM).
  -->

![Suchseitenbedienfeld](/help/sites-cloud/authoring/assets/search-side-panel.png)

1. Sie können auch weitere Suchbegriffe hinzufügen.

1. Schließen Sie die Funktion **Suchen** über das **X** (rechts oben).

>[!NOTE]
>
>Die Suchkriterien werden bei Auswahl eines Elements in den Suchergebnissen beibehalten.
>
>Bei Auswahl eines Elements auf der Seite mit den Suchergebnissen bleiben die Suchkriterien erhalten, wenn Sie über die Zurück-Schaltfläche des Browsers zur Suchseite zurückkehren.

## Saved Searches {#saved-searches}

Sie können nicht nur nach zahlreichen Facetten suchen, sondern auch eine bestimmte Suchkonfiguration speichern, um diese später abzurufen und zu verwenden:

1. Definieren Sie die Suchkriterien und wählen Sie **Speichern**.

   ![Speichern einer Suche](/help/sites-cloud/authoring/assets/search-side-panel.png)

1. Weisen Sie einen Namen zu und wählen Sie **Speichern** zur Bestätigung:

   ![Speichern einer Suche mit einem Namen](/help/sites-cloud/authoring/assets/search-save-name.png)

1. Die gespeicherte Suche ist außerdem in der Auswahl verfügbar, wenn Sie das nächste Mal auf den Suchbereich zugreifen:

   ![Gespeicherte Suchvorgänge](/help/sites-cloud/authoring/assets/saved-searches.png)

1. Nach dem Speichern können Sie:

   * **x** (für den Namen der gespeicherten Suche) verwenden, um eine neue Abfrage zu starten. Die gespeicherte Suche selbst wird nicht gelöscht.
   * die Option **Gespeicherte Suche bearbeiten** verwenden, die Suchbedingungen ändern und dann erneut auf **Speichern** klicken.

Sie können gespeicherte Suchen ändern, indem Sie die gespeicherte Suche auswählen und am unteren Rand des Suchbereichs auf **Gespeicherte Suche bearbeiten** klicken.

![Speichern einer Suche ändern](/help/sites-cloud/authoring/assets/saved-searches-modify.png)
