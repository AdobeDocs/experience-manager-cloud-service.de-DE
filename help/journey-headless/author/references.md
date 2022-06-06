---
title: Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten
description: Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten für Inhalte, andere Fragmente und andere Assets (Medien). Einführung in die Notwendigkeit und die Mechanik verschachtelter Fragmente für Headless-CMS-Seitenbearbeitung.
exl-id: a65e8a5a-954b-4307-8027-ca8bac5f4261
source-git-commit: e81b852dc90e3cc5abc8b9f218f48d0fc1cc66eb
workflow-type: ht
source-wordcount: '729'
ht-degree: 100%

---

# Erfahren Sie mehr über die Verwendung von Verweisen in Inhaltsfragmenten {#author-headless-references}

## Die bisherige Entwicklung {#story-so-far}

Zu Beginn der [AEM Headless-Inhaltsautoren-Tour](overview.md) wurden in der [Einführung](introduction.md) die grundlegenden Konzepte und die Terminologie für das Authoring für Headless behandelt.

Sie haben die Grundlagen der Headless-CMS-Seitenbearbeitung kennengelernt, mit einer Einführung in die Seitenbearbeitung mit AEM as a Cloud Service und insbesondere die Bearbeitung von Inhaltsfragmenten.

Dieser Artikel baut auf diesen auf. Sie erfahren, wie Sie Verweise verwenden können, um eigene Inhalte für Ihr AEM Headless-Projekt zu erstellen.

## Ziel {#objective}

* **Zielgruppe**: Fortgeschrittene
* **Ziel**: Einführung der Verwendung von Verweisen für die Headless-CMS-Seitenbearbeitung. Welche Arten von Verweisen sind verfügbar und zu welchen Zwecken dienen sie?

   * Inhaltsreferenzen
   * Asset-/Medienverweise
   * Fragmentreferenzen
   * Ad-hoc-Verweise aus einem Textblock

## Was sind Verweise {#what-are-references}

Verweise sind lediglich ein Mechanismus zum Verbinden Ihrer Ressourcen, sei es mit anderen Inhalten, Assets (wie in Bildern) oder anderen Fragmenten. Obwohl sie sehr ähnlich sind, gibt es einige Unterschiede.

Einige Verweise verfügen über dedizierte Datentypen (z. B. Inhaltsverweise und Fragmentverweise), während andere einfach als Verweis in einem Textblock hinzugefügt werden (Asset-Verweise und Ad-hoc-Verweise).

![Inhaltsfragmente – Verweise](/help/journey-headless/author/assets/headless-journey-author-references-01.png)

## Inhaltsreferenzen {#content-references}

Inhaltsverweise tun genau das – sie ermöglichen es Ihnen, auf beliebige andere Inhalte zu verweisen. Dadurch wird ein Browser geöffnet, in dem Sie das Inhaltselement auswählen können.

## Asset-/Medienverweise {#assets-media-references}

Mithilfe der Option **Asset einfügen** können Sie innerhalb eines Textblocks auf Assets (z. B. Bilder oder Medien) verweisen. Dadurch wird ein Browser geöffnet, in dem Sie das Asset auswählen können.

![Inhaltsfragmente – Asset einfügen](/help/journey-headless/author/assets/headless-journey-author-references-02.png)

## Fragmentreferenzen {#fragment-references}

Fragmentverweise tun genau das – sie ermöglichen es Ihnen, auf ein anderes Fragment zu verweisen. Warum dies von Bedeutung ist, bedarf einer näheren Erläuterung.

Bei Ihnen sind möglicherweise die folgenden Inhaltsfragmentmodelle definiert:

* Stadt
* Unternehmen
* Person
* Auszeichnungen

Es scheint ziemlich einfach, aber natürlich hat eine Firma sowohl einen CEO als auch Mitarbeiter...und dies sind alles Leute, die jeweils als Person definiert sind.

Und eine Person kann eine Auszeichnung bekommen (oder vielleicht zwei).

* Meine Firma – Firma
   * CEO – Person
   * Mitarbeiter – Person
      * Persönliche Auszeichnungen – Auszeichnung

Und das ist nur für den Einstieg. Je nach Komplexität kann eine Auszeichnung firmenspezifisch sein oder eine Firma könnte ihre Hauptverwaltung in einer bestimmten Stadt haben.

Die Repräsentation dieser Beziehungen kann mit Fragmentverweisen erreicht werden, da diese sowohl von Ihnen (dem Autor) als auch von den Headless-Programmen verstanden werden.

Als Autor sind Sie nicht für die Definition dieser Beziehungen verantwortlich (das wird vom Inhaltsarchitekten beim Erstellen des Inhaltsfragmentmodells vorgenommen), Sie müssen jedoch wissen, wie Sie die Verweise erkennen und bearbeiten können.

<!--
![Content Modeling with Content Fragments](/help/journey-headless/developer/assets/headless-modeling-01.png "Content Modeling with Content Fragments")
-->

### Bearbeiten verschachtelter Fragmente {#author-nested-fragment}

Die Bearbeitung von Fragmentverweisen ist relativ einfach (obwohl das Feld normalerweise nicht als **Fragmentverweis** bezeichnet wird). Sie können den Verweis entweder direkt eingeben oder (wahrscheinlicher) auf das Ordnersymbol klicken, um einen Browser zu öffnen, in dem Sie navigieren und das gewünschte Fragment auswählen können.

![Inhaltsfragmente – Verweise](/help/journey-headless/author/assets/headless-journey-author-references-03.png)

Die Definition des Inhaltsfragmentmodells steuert:

* ob Sie wählen können, mehrere Verweise hinzuzufügen
* die Modelltypen der Inhaltsfragmente, die Sie auswählen können. Das Inhaltsfragmentmodell definiert die Fragmentmodelle, die für den Verweis zulässig sind, sodass AEM nur Fragmente basierend auf diesen Modellen anzeigt.

### Navigieren in verschachtelten Fragmenten {#navigate-nested-fragment}

Wenn Sie die Registerkarte **Baumstruktur** des Inhaltsfragment-Editors verwenden, können Sie durch die Fragmente navigieren, auf die Ihr Fragment verweist, und dann durch alle Verweise, die sie möglicherweise enthalten. Wenn Sie eine Referenz auswählen, wird dieses Fragment zur Bearbeitung geöffnet.

>[!NOTE]
>
>Mithilfe der Breadcrumbs im Hauptbedienfeld können Sie zurück zu Ihrem Ausgangspunkt gelangen.

![Strukturbaum der Inhaltsfragmente](/help/assets/content-fragments/assets/cfm-structuretree-02.png)

## Ad-hoc-Verweise {#adhoc-references}

Ad-hoc-Verweise können als einfacher Link innerhalb eines Textblocks hinzugefügt werden:

![Inhaltsfragmente – Ad-hoc-Verweise](/help/journey-headless/author/assets/headless-journey-author-references-04.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie sich mit Verweisen und Strukturen in Inhaltsfragmenten vertraut gemacht haben, fahren Sie mit dem nächsten Schritt fort: [Erfahren Sie mehr über Metadaten und Tagging](metadata-tagging.md). In diesem Abschnitt wird erläutert, wie Sie Metadaten und Tags für Ihre Inhaltsfragmente definieren können.

## Zusätzliche Ressourcen {#additional-resources}

* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)

      * [Anwenden der Konfiguration auf Ihren Assets-Ordner](/help/assets/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

      * [Erstellen eines Inhaltsfragments](/help/assets/content-fragments/content-fragments-managing.md#creating-a-content-fragment)
   * [Varianten – Authoring von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-variations.md)

   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)

      * [Inhaltsfragmentmodelle – Datentypen](/help/assets/content-fragments/content-fragments-models.md#data-types)

      * [Inhaltsfragmentmodelle – Eigenschaften](/help/assets/content-fragments/content-fragments-models.md#properties)


* Anleitungen für den Einstieg
   * [Erstellen eines Asset-Ordners – Headless-Einrichtung](/help/headless/setup/create-assets-folder.md)

* AEM Headless-Inhaltsarchitekten-Tour

* AEM Headless-Übersetzungs-Tour
