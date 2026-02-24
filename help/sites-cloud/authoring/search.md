---
title: Suchen
description: Rasches Auffinden von Inhalten dank umfassender Suchfunktionen
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 8a799e9a-1461-4e79-ae90-1978af6cf0ed
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 99%

---

# Suchen {#search-feature}

Die Autorenumgebung von AEM bietet abhängig vom Ressourcentyp verschiedene Möglichkeiten zur Inhaltssuche.

## Grundlagen zur Suche {#search-basics}

Die Suchfunktion ist über die obere Symbolleiste verfügbar:

![Suchsymbol](/help/sites-cloud/authoring/assets/search-icon.png)

Die Suchleiste bietet Ihnen folgende Möglichkeiten:

* Suchen Sie nach einem bestimmten Keyword, Pfad oder Tag
* Filtern Sie nach ressourcenspezifischen Kriterien, wie Änderungsdatumsangaben, Seitenstatus und Dateigröße.
* Definieren und Verwenden einer [gespeicherten Suche](#saved-searches), die auf den oben genannten Kriterien basiert

>[!NOTE]
>
>Sie können die Suche auch aufrufen, indem Sie den Hotkey `/` (Schrägstrich) verwenden, wenn die Suchleiste sichtbar ist.

## Suchen und Filtern {#search-and-filter}

So durchsuchen und filtern Sie Ressourcen:

1. Öffnen Sie die Option **Suchen** (mit der Lupe in der Symbolleiste) und geben Sie den Suchbegriff ein. Es werden Empfehlungen angezeigt, die Sie dann auswählen können:

   ![Suchbegriff](/help/sites-cloud/authoring/assets/search-term.png)

   Standardmäßig sind die Suchergebnisse auf Ihre aktuelle Position begrenzt (d. h. Konsole und zugehöriger Ressourcentyp):

   ![Suchposition](/help/sites-cloud/authoring/assets/search-term-location.png)

1. Bei Bedarf können Sie den Positionsfilter entfernen (wählen Sie für den zu entfernenden Filter das **X** aus), um alle Konsolen-/Ressourcentypen zu durchsuchen.
1. Die Ergebnisse werden gemäß der Konsole und dem zugehörigen Ressourcentyp gruppiert angezeigt.

   Sie können entweder eine spezifische Ressource (für eine spätere Aktion) oder eine Drilldown-Suche auswählen, indem Sie den erforderlichen Ressourcentyp auswählen, z. B. **Alle Sites anzeigen**:

   ![Suchergebnisse](/help/sites-cloud/authoring/assets/search-results.png)

1. Wenn Sie weitere Details anzeigen möchten, wählen Sie das Symbol für die Seitenleiste (oben links) aus, um den Seitenbereich **Filter und Optionen** zu öffnen.

   ![Seitenleisten-Schaltfläche](/help/sites-cloud/authoring/assets/rail-button.png)

   Je nach Ressourcentyp zeigt die Suche eine vordefinierte Auswahl von Such-/Filterkriterien an.

   Im seitlichen Bedienfeld können Sie Folgendes auswählen:

   * Gespeicherte Suchvorgänge
   * Verzeichnis durchsuchen
   * Tags
   * Suchkriterien, z. B. Änderungsdatum, Veröffentlichungsstatus, Status der Live Copy.

   >[!NOTE]
   >
   >Die Suchkriterien können variieren:
   >
   >* in Abhängigkeit von dem von Ihnen ausgewählten Ressourcentyp, wobei z. B. die Kriterien „Assets“ und „Communitys“ verständlicherweise spezialisiert sind.
   >* Je nach Instanz, da die Suchformulare (entsprechend der Stelle in AEM) angepasst werden können.

<!--
  >* Your instance as the [Search Forms](/help/sites-administering/search-forms.md) can be customized (appropriate to the location within AEM).
  -->

![Suchen im seitlichen Bedienfeld](/help/sites-cloud/authoring/assets/search-side-panel.png)

1. Sie können auch zusätzliche Suchbegriffe hinzufügen.

1. Schließen Sie die **Suche** mit dem **X** (oben rechts).

>[!NOTE]
>
>Suchkriterien werden beibehalten, wenn ein Element in den Suchergebnissen ausgewählt wird.
>
>Bei Auswahl eines Elements auf der Seite mit den Suchergebnissen bleiben die Suchkriterien erhalten, wenn Sie über die Zurück-Schaltfläche des Browsers zur Suchseite zurückkehren.

## Gespeicherte Suchvorgänge {#saved-searches}

Sie können nicht nur nach zahlreichen Facetten suchen, sondern auch eine bestimmte Suchkonfiguration speichern, um diese später abzurufen und zu verwenden:

1. Definieren Sie die Suchkriterien und wählen Sie **Speichern**.

   ![Speichern einer Suche](/help/sites-cloud/authoring/assets/search-side-panel.png)

1. Weisen Sie einen Namen zu und wählen Sie zur Bestätigung **Speichern** aus:

   ![Speichern einer Suche mit einem Namen](/help/sites-cloud/authoring/assets/search-save-name.png)

1. Die gespeicherte Suche ist außerdem in der Auswahl verfügbar, wenn Sie das nächste Mal auf den Suchbereich zugreifen:

   ![Gespeicherte Suchvorgänge](/help/sites-cloud/authoring/assets/saved-searches.png)

1. Nach dem Speichern können Sie:

   * **x** (für den Namen der gespeicherten Suche) verwenden, um eine neue Abfrage zu starten. Die gespeicherte Suche selbst wird nicht gelöscht.
   * die Option **Gespeicherte Suche bearbeiten** verwenden, die Suchbedingungen ändern und dann erneut auf **Speichern** klicken.

Gespeicherte Suchen können geändert werden, indem Sie die gespeicherte Suche auswählen und unten im Suchfeld auf **Gespeicherte Suche bearbeiten** klicken.

![Ändern einer gespeicherten Suche](/help/sites-cloud/authoring/assets/saved-searches-modify.png)
