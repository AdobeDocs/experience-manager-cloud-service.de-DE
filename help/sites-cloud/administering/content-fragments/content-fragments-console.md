---
title: Inhaltsfragmentkonsole
description: Erfahren Sie, wie Sie Inhaltsfragmente über die Inhaltsfragmentkonsole verwalten.
landing-page-description: Erfahren Sie, wie Sie Inhaltsfragmente über die Konsole "Inhaltsfragmente"verwalten, die sich auf die Verwendung von Inhaltsfragmenten mit hohem Volumen für Headless-Anwendungsfälle konzentriert, aber auch beim Erstellen von Seiten verwendet wird.
feature: Content Fragments
role: User
exl-id: 0e6e3b61-a0ca-44b8-914d-336e29761579
source-git-commit: 944665bc7cac1f00811187a508a18800c3d73f2a
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 63%

---

# Inhaltsfragmentkonsole  {#content-fragments-console}

Erfahren Sie, wie die Inhaltsfragmentkonsole den Zugriff auf Ihre Inhaltsfragmente optimiert und Sie dabei unterstützt, diese zu erstellen, zu durchsuchen und zu verwalten, indem Sie Verwaltungsaufgaben durchführen, wie Inhalte veröffentlichen, ihre Veröffentlichung aufheben und Kopien anfertigen.

Die Inhaltsfragmentkonsole dient der Verwaltung, Suche und Erstellung von Inhaltsfragmenten. Sie wurde für die Verwendung in einem Headless-Kontext optimiert, wird aber auch beim Erstellen von Inhaltsfragmenten für die Seitenbearbeitung verwendet.

>[!NOTE]
>
>In dieser Konsole werden nur Inhaltsfragmente angezeigt. Andere Asset-Typen wie Bilder und Videos werden nicht angezeigt.

>[!NOTE]
>
>Der Zugriff auf Ihre Inhaltsfragmente ist derzeit über folgende Kanäle möglich:
>
>* diese **Inhaltsfragmentkonsole**
>* die **Assets**-Konsole – siehe [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)


>[!NOTE]
>
>Auswahl von [Tastaturbefehle sind in dieser Konsole verfügbar](/help/sites-cloud/administering/content-fragments/content-fragments-console-keyboard-shortcuts.md).

Die Inhaltsfragmentkonsole kann direkt von der obersten Ebene der globalen Navigation aus aufgerufen werden:

![Globale Navigation – Inhaltsfragmentkonsole](assets/cfc-global-navigation.png)

## Grundlegende Struktur und Handhabung der Konsole {#basic-structure-handling-content-fragments-console}

Wenn Sie **Inhaltsfragmente** auswählen, wird die Konsole in einer neuen Registerkarte geöffnet.

![Inhaltsfragmentkonsole – Übersicht](assets/cfc-console-overview.png)

Hier können Sie sehen, dass es drei Hauptbereiche gibt:

* Die obere Symbolleiste
   * Bietet die standardmäßigen AEM-Funktionen
   * Zeigt auch Ihre IMS-Organisation an
* Das linke Bedienfeld
   * Hier können Sie die Ordnerstruktur ein- oder ausblenden
   * Sie können einen bestimmten Zweig des Baums auswählen
* Das Haupt-/rechte Bedienfeld – von hier aus können Sie:
   * Eine Liste aller Inhaltsfragmente im ausgewählten Zweig des Baums anzeigen:
      * Der Speicherort wird durch die Breadcrumbs angegeben. Diese können auch verwendet werden, um den Speicherort zu ändern.
      * Es werden die Inhaltsfragmente aus dem ausgewählten Ordner und dazu alle untergeordneten Ordner angezeigt.:
         * [Verschiedene Informationsfelder](#selectuse-available-columns) über ein Inhaltsfragment Links bereitstellt; Je nach Feld können diese:
            * Öffnen Sie das entsprechende Fragment im Editor
            * Anzeigen von Informationen zu Verweisen
            * Informationen zu Sprachversionen des Fragments anzeigen
         * Sie können [Wählen Sie mindestens ein Inhaltsfragment aus, um die verfügbaren Aktionen anzuzeigen.](#actions-selected-content-fragment)
      * Sie können eine Spaltenüberschrift auswählen, um die Tabelle nach dieser Spalte zu sortieren. Klicken Sie erneut, um zwischen aufsteigender und absteigender Sortierung umzuschalten.
   * Ein neues Inhaltsfragment **[erstellen](#creating-new-content-fragment)**
   * Die Inhaltsfragmente entsprechend einer Auswahl von Eigenschaften [filtern](#filtering-fragments) und den Filter für die zukünftige Verwendung speichern
   * Die Inhaltsfragmente [durchsuchen](#searching-fragments)
   * [Die Tabellenansicht so anpassen, dass ausgewählte Spalten mit Informationen angezeigt werden](#selectuse-available-columns)
   * Verwenden Sie **In Assets öffnen**, um den aktuellen Speicherort direkt in der Konsole **Assets** zu öffnen

      >[!NOTE]
      >
      >Die Konsole **Assets** wird verwendet, um auf Assets wie Bilder, Videos usw. zuzugreifen.  Auf die Konsole kann wie folgt zugegriffen werden:
      >
      >* mithilfe des Links **In Assets öffnen** (in der Konsole „Inhaltsfragmente“)
      >* direkt über das globale Navigationsfenster


## Aktionen für ein (ausgewähltes) Inhaltsfragment {#actions-selected-content-fragment}

Wenn Sie ein bestimmtes Fragment auswählen, wird eine Symbolleiste geöffnet, die die verfügbaren Aktionen für dieses Fragment anzeigt. Sie können auch mehrere Fragmente auswählen. Die Auswahl der Aktionen wird dann entsprechend angepasst.

![Konsole „Inhaltsfragmente“ – Symbolleiste für ein ausgewähltes Fragment](assets/cfc-fragment-toolbar.png)

* **Öffnen**
* **Veröffentlichen** (und **Veröffentlichung rückgängig machen**)
* **Kopieren**
* **Verschieben**
* **Umbenennen**
* **Löschen**

>[!NOTE]
>
>Aktionen wie Veröffentlichen, Veröffentlichung aufheben, Löschen, Verschieben, Umbenennen, Kopieren lösen einen asynchronen Vorgang aus. Der Fortschritt dieses Vorgangs kann über die AEM-Benutzeroberfläche für asynchrone Vorgänge überwacht werden.

## Informationen zu Ihren Inhaltsfragmenten {#information-content-fragments}

Der Rechts-/Hauptbereich (Tabellenansicht) der Konsole enthält eine Reihe von Informationen zu Ihren Inhaltsfragmenten. Einige Elemente bieten auch direkte Links zu weiteren Aktionen und/oder Informationen:

* **Name**
   * Stellt einen Link zum Öffnen des Fragments im Editor bereit.
* **Modell**
   * Stellt einen Link zum Öffnen des Fragments im Editor bereit.
* **Ordner**
   * Stellt einen Link zum Öffnen des Ordners in der Konsole bereit.
Wenn Sie den Mauszeiger über einen Ordnernamen bewegen, wird der JCR-Pfad angezeigt.
* **Status**
   * Nur Informationen
* **Geändert**
   * Nur Informationen
* **Geändert von**
   * Nur Informationen
* **Veröffentlicht bei**
   * Nur Informationen
* **Herausgeber**
   * Nur Informationen
* **Referenziert von**

   * Stellt einen Link bereit, der ein Dialogfeld öffnet, in dem alle übergeordneten Verweise dieses Fragments aufgelistet werden. einschließlich der Referenzierung von Inhaltsfragmenten, Experience Fragments und Seiten. Um eine bestimmte Referenz zu öffnen, klicken Sie auf die **Titel** im Dialogfeld.

      ![Konsole &quot;Inhaltsfragmente&quot;- Dialogfeld &quot;Verweise&quot;](assets/cfc-console-references-dialog.png)

* **Sprache**

   * Gibt das Gebietsschema des Inhaltsfragments zusammen mit der Gesamtzahl der mit dem Inhaltsfragment verknüpften Gebietsschemas/Sprachkopien an.

      ![Konsole &quot;Inhaltsfragmente&quot;- Sprachindikator](assets/cfc-console-language-indicator.png)

      * Klicken/tippen Sie auf die Anzahl , um ein Dialogfeld zu öffnen, in dem alle Sprachkopien angezeigt werden. Um eine bestimmte Sprachkopie zu öffnen, klicken Sie auf die Schaltfläche **Titel** im Dialogfeld.

         ![Konsole &quot;Inhaltsfragmente&quot;- Dialogfeld &quot;Sprache&quot;](assets/cfc-console-languages-dialog.png)

## Verfügbare Spalten auswählen {#select-available-columns}

Wie bei anderen Konsolen können Sie die sichtbaren und für die Aktion verfügbaren Spalten konfigurieren:

![Konsole &quot;Inhaltsfragmente&quot;- Spaltenkonfiguration](assets/cfc-console-column-icon.png)

Daraufhin wird eine Liste von Spalten angezeigt, die Sie ausblenden oder anzeigen können:

![Konsole &quot;Inhaltsfragmente&quot;- Spaltenkonfiguration](assets/cfc-console-column-selection.png)

## Erstellen eines neuen Inhaltsfragments {#creating-new-content-fragment}

Durch Klicken auf **Erstellen** wird das kompakte Dialogfeld **Neues Inhaltsfragment** geöffnet:

![Konsole „Inhaltsfragmente“ – Erstellen eines neuen Fragments](assets/cfc-console-create.png)

## Filtern von Fragmenten {#filtering-fragments}

Der Filterbereich bietet folgende Optionen:

* eine Auswahl an Eigenschaften, die ausgewählt und kombiniert werden können
* die Möglichkeit, Ihre Konfiguration zu **speichern**
* die Option zum Abrufen eines gespeicherten Suchfilters für die Wiederverwendung

![Konsole „Inhaltsfragmente“ – Filtern](assets/cfc-console-filter.png)

## Suchen von Fragmenten {#searching-fragments}

Das Suchfeld unterstützt die Volltextsuche. Geben Sie Ihre Suchbegriffe in das Suchfeld ein:

![Konsole „Inhaltsfragmente“ – Suchen](assets/cfc-console-search-01.png)

Die ausgewählten Ergebnisse werden bereitgestellt:

![Konsole „Inhaltsfragmente“ – Suchergebnisse](assets/cfc-console-search-02.png)

Das Suchfeld bietet außerdem schnellen Zugriff auf die **letzten Inhaltsfragmente** und die **gespeicherten Suchvorgänge**:

![Konsole „Inhaltsfragmente“ – Zuletzt und gespeichert](assets/cfc-console-search-03.png)
