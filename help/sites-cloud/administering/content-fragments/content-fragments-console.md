---
title: Inhaltsfragmentkonsole
description: Erfahren Sie, wie Sie Inhaltsfragmente über die Konsole "Inhaltsfragmente"verwalten.
landing-page-description: Erfahren Sie, wie Sie Inhaltsfragmente über die Konsole "Inhaltsfragmente"verwalten, die sich auf die Verwendung von Inhaltsfragmenten mit hohem Volumen für Headless-Anwendungsfälle konzentriert, aber auch beim Erstellen von Seiten verwendet wird.
exl-id: 0e6e3b61-a0ca-44b8-914d-336e29761579
source-git-commit: 99e3c07f8376859692db41c633bfaa602ed65358
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Inhaltsfragmentkonsole  {#content-fragments-console}

Erfahren Sie, wie die Konsole &quot;Inhaltsfragmente&quot;den Zugriff auf Ihre Inhaltsfragmente optimiert und Sie dabei unterstützt, diese zu erstellen, zu durchsuchen und zu verwalten, indem Sie Verwaltungsaktionen wie die Veröffentlichung, das Rückgängigmachen der Veröffentlichung und das Kopieren durchführen.

Die Konsole &quot;Inhaltsfragmente&quot;dient der Verwaltung, Suche und Erstellung von Inhaltsfragmenten. Es wurde für die Verwendung in einem Headless-Kontext optimiert, wird aber auch beim Erstellen von Inhaltsfragmenten für die Seitenbearbeitung verwendet.

>[!NOTE]
>
>In dieser Konsole werden nur Inhaltsfragmente angezeigt. Andere Asset-Typen wie Bilder und Videos werden nicht angezeigt.

>[!NOTE]
>
>Der Zugriff auf Ihre Inhaltsfragmente ist derzeit über folgende Kanäle möglich:
>
>* this **Inhaltsfragmente** console
>* die **Assets** console - see [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)


>[!NOTE]
>
>Auswahl von [Tastaturbefehle sind in dieser Konsole verfügbar](/help/sites-cloud/administering/content-fragments/content-fragments-console-keyboard-shortcuts.md).

Die Konsole &quot;Inhaltsfragmente&quot;kann direkt von der obersten Ebene der globalen Navigation aus aufgerufen werden:

![Globale Navigation - Konsole &quot;Inhaltsfragmente&quot;](assets/cfc-global-navigation.png)

Auswählen **Inhaltsfragmente** öffnet die Konsole in einer neuen Registerkarte.

![Konsole &quot;Inhaltsfragmente&quot;- Übersicht](assets/cfc-console-overview.png)

Hier können Sie sehen, dass es drei Hauptbereiche gibt:

* die obere Symbolleiste
   * Standard-AEM
   * Zeigt auch Ihre IMS-Organisation an
* Das linke Bedienfeld
   * Hier können Sie die Ordnerstruktur ein- oder ausblenden
   * Sie können einen bestimmten Zweig des Baums auswählen
* Das Haupt-/rechte Bedienfeld - von hier aus können Sie:
   * Liste aller Inhaltsfragmente im ausgewählten Zweig des Baums anzeigen
      * Der Standort wird durch die Breadcrumbs angegeben. diese können auch verwendet werden, um den Standort zu ändern
      * Inhaltsfragmente aus dem ausgewählten Ordner und alle untergeordneten Ordner werden angezeigt
         * Verschiedene Informationsfelder über ein Inhaltsfragment bieten Links. Diese können das entsprechende Fragment im Editor öffnen
      * Sie können eine Spaltenüberschrift auswählen, um die Tabelle nach dieser Spalte zu sortieren. Wählen Sie erneut aus, um zwischen aufsteigender und absteigender
   * **[Erstellen](#creating-new-content-fragment)** ein neues Inhaltsfragment
   * [Filter](#filtering-fragments) die Inhaltsfragmente entsprechend einer Auswahl von Eigenschaften und speichern Sie den Filter für die zukünftige Verwendung
   * [Suche](#searching-fragments) die Inhaltsfragmente
   * Anpassen der Tabellenansicht zum Anzeigen ausgewählter Informationsspalten
   * Verwendung **In Assets öffnen** , um die aktuelle Position direkt im **Assets** Konsole.

      >[!NOTE]
      >
      >Die **Assets** -Konsole wird verwendet, um auf Assets wie Bilder, Videos usw. zuzugreifen.  Auf diese Konsole kann zugegriffen werden:
      >
      >* mithilfe der **In Assets öffnen** Link (in der Konsole &quot;Inhaltsfragmente&quot;)
      >* direkt über das globale Navigationsfenster


Wenn Sie ein bestimmtes Fragment auswählen, wird eine Symbolleiste geöffnet, die sich auf die für dieses Fragment verfügbaren Aktionen konzentriert. Sie können auch mehrere Fragmente auswählen. Die Auswahl der Aktionen wird entsprechend angepasst.

![Konsole &quot;Inhaltsfragmente&quot;- Symbolleiste für ein ausgewähltes Fragment](assets/cfc-fragment-toolbar.png)

## Erstellen eines neuen Inhaltsfragments {#creating-new-content-fragment}

Auswählen **Erstellen** öffnet den Kompakt **Neues Inhaltsfragment** dialog:

![Konsole &quot;Inhaltsfragmente&quot;- Erstellen eines neuen Fragments](assets/cfc-console-create.png)

## Filtern von Fragmenten {#filtering-fragments}

Der Bereich Filter bietet folgende Optionen:

* Auswahl an Eigenschaften, die ausgewählt und kombiniert werden können
* die Möglichkeit, **Speichern** Ihre Konfiguration
* die Option zum Abrufen eines gespeicherten Suchfilters für die Wiederverwendung

![Konsole &quot;Inhaltsfragmente&quot;- Filtern](assets/cfc-console-filter.png)

## Suchen von Fragmenten {#searching-fragments}

Das Suchfeld unterstützt die Volltextsuche. Geben Sie Ihre Suchbegriffe in das Suchfeld ein:

![Konsole &quot;Inhaltsfragmente&quot;- Suchen](assets/cfc-console-search-01.png)

Stellt die ausgewählten Ergebnisse bereit:

![Konsole &quot;Inhaltsfragmente&quot;- Suchergebnisse](assets/cfc-console-search-02.png)

Das Suchfeld bietet außerdem schnellen Zugriff auf **Letzte Inhaltsfragmente** und **Gespeicherte Suchen**:

![Konsole &quot;Inhaltsfragmente&quot;- Zuletzt und gespeichert](assets/cfc-console-search-03.png)
