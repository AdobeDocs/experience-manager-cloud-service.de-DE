---
title: Launches für Inhaltsfragmente
description: Erfahren Sie, wie Sie Launches für Inhaltsfragmente in Adobe Experience Manager as a Cloud Service verwenden. Launches ermöglichen es Ihnen, Inhalte für eine zukünftige Version effizient zu entwickeln und dabei Ihre aktuellen Inhaltsfragmente beizubehalten.
feature: Content Fragments
role: User, Developer, Architect
hide: true
hidefromtoc: true
index: false
solution: Experience Manager Sites
source-git-commit: f2adbc7fd92e846c6e09e52644f45c720c04dc4e
workflow-type: tm+mt
source-wordcount: '1582'
ht-degree: 1%

---


# Launches für Inhaltsfragmente {#launches-for-content-fragments}

In Adobe Experience Manager (AEM) as a Cloud Service ermöglichen Launches die effiziente Entwicklung von Inhalten für eine zukünftige Version.

Ein *Launch* wird erstellt, um Ihnen Änderungen zur Vorbereitung auf eine zukünftige Veröffentlichung zu ermöglichen und gleichzeitig Ihre aktuellen Inhalte zu pflegen. Bei Inhaltsfragmenten bedeutet dies, dass Sie effektiv zwei Versionen gleichzeitig bearbeiten: aktuell veröffentlichte Inhalte und eine Version dieser Inhalte, die zu einem späteren Zeitpunkt veröffentlicht werden sollen. Sobald diese Zeit gekommen ist, können Sie den Inhalt der ursprünglichen Inhaltsfragmente ersetzen und die neuen Versionen veröffentlichen.

>[!NOTE]
>
>Launches sind auch für Seiten verfügbar. Die grundlegenden Konzepte sind dieselben, aber es gibt Unterschiede bei ihrer Verwaltung in AEM.
>
>Ausführliche Informationen finden Sie [Launches für Seiten](/help/sites-cloud/authoring/launches/overview.md).

Erstellen Sie einen *Launch* und bearbeiten und aktualisieren Sie dann Ihre Inhaltsfragmente in Ihrem *Launch*. Wenn in dieser Phase Änderungen an den *Source*-Fragmenten vorgenommen werden, können Sie diese mit dem Vorgang *Rebase* in *Launch* kopieren. Wenn er bereit ist *dupliziert* Hochstufen“ den Launch-Inhalt zurück an die Quelle. Anschließend können Sie die Quellfragmente entweder manuell oder automatisch aktivieren (abhängig von den Feldern, die beim Erstellen und Bearbeiten des Launches festgelegt wurden). Sie können auch angeben, ob referenzierte Fragmente in diesen Prozess einbezogen werden sollen.

Beispielsweise werden die saisonalen Produktfragmente Ihres Online-Shops vierteljährlich aktualisiert, sodass die vorgestellten Produkte mit der aktuellen Saison übereinstimmen. Zur Vorbereitung auf die nächste vierteljährliche Aktualisierung können Sie einen Launch der entsprechenden Fragmente erstellen. Während des Quartals werden die folgenden Änderungen in der Launch-Kopie gesammelt:

* Bearbeitungen, die direkt an den Launch-Fragmenten in Vorbereitung auf das nächste Quartal durchgeführt werden.
* Änderungen an den Quellinhaltsfragmenten, die Sie mit „Rebase“ auf *Launch-Seiten*.
* Sie können auch in Inhalten in der Launch-Verzweigung navigieren und Fragmente nach Bedarf hinzufügen oder entfernen.

Wenn das nächste Quartal kommt, stufen Sie die Launch-Seiten hoch, damit Sie die Quellseiten veröffentlichen können (den aktualisierten Inhalt enthalten). Sie können entweder alle Fragmente oder nur die Fragmente weiterleiten, die Sie geändert haben.

![Launches - Übersicht - Neubasieren und Hochstufen](/help/sites-cloud/administering/content-fragments/assets/cf-launches-overview.png)

In diesem Abschnitt wird beschrieben, wie Sie Launches über die (Inhaltsfragmentkonsole) erstellen, bearbeiten, verwalten, neu basieren[ weiterleiten und bei Bedarf löschen ](/help/sites-cloud/administering/content-fragments/managing.md):

* [Aufrufen und Anzeigen von Launches in der Inhaltsfragmentkonsole](#launches-in-the-content-fragment-console)
* [Erstellen eines Launches](#create-a-launch)
* [Launch-Inhalt bearbeiten](#edit-launch-content)
* [Verwalten von Inhalten in einem Launch](#manage-content-within-a-launch)
* [Launch mit Quelle vergleichen](#compare-launch-to-source)
* [Starten von Source aus neu basieren](#rebase-a-launch-from-source)
* [Bewerben eines Launches für Source](#promote-a-launch-to-source)
* [Löschen von Launches](#delete-a-launch)

## Launches in der Inhaltsfragmentkonsole {#launches-in-the-content-fragment-console}

Auf **Registerkarte** Launches“ der Inhaltsfragmentkonsole können Sie Launches erstellen, alle vorhandenen Launches auflisten, die wichtigsten Eigenschaften anzeigen und Aktionen für sie durchführen.

Wenn kein Launch ausgewählt ist, können Sie [einen neuen Launch erstellen](#create-a-launch).

![Registerkarte „Launches“ in der Konsole](/help/sites-cloud/administering/content-fragments/assets/cf-launches-tab.png)

Launch auswählen, der angezeigt werden soll:

* Symbolleiste mit den verfügbaren Aktionen
* im rechten Bereich mit Eigenschaften und weiteren Aktionen

![Startaktionen-Symbolleiste in der Konsole](/help/sites-cloud/administering/content-fragments/assets/cf-launches-actions.png)

Die Symbolleiste bietet folgende Möglichkeiten:

* **[Launch öffnen](#edit-launch-content)**
* **[Quellen bearbeiten](#manage-content-within-a-launch)**
* **[Launch mit Source vergleichen](#compare-launch-to-source)**
* **[Bewerben](#promote-a-launch-to-source)**
* **[Neu basieren](#promote-a-launch-to-source)**
* **[Launch löschen](#delete-a-launch)**

Im rechten Bedienfeld haben Sie folgende Möglichkeiten:

* Launch bearbeiten **Titel**
* Bearbeiten des Launches **Beschreibung**
* Aktualisieren Sie die Konfigurationsdetails, die beim Erstellen [ Launches festgelegt wurden](#create-a-launch):

   * **Verweise einschließen**: Erstellen Sie den Launch entweder mit oder ohne, einschließlich referenzierter Inhaltsfragmente. Standardmäßig sind referenzierte Fragmente enthalten.

      * Referenzierte Fragmente sind auch betroffen, wenn [ zu einem späteren Zeitpunkt Fragmente aus dem Launch hinzufügen ](#manage-content-within-a-launch) entfernen.

     >[!NOTE]
     >
     >Siehe [Details zu enthaltenen Verweisen](#details-concerning-included-references)

   * **Veröffentlichungsbereit** Durch Aktivieren dieses Umschalters werden die Fragmente automatisch veröffentlicht, wenn der Launch zur Quelle weitergeleitet wird.

* Und definieren Sie auch:

   * A **Promote Date** and Time: , wenn der [Launch automatisch beworben werden soll](#promote-automatically)

## Erstellen eines Launches {#create-a-launch}

So erstellen Sie einen Launch:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die **Launches**.

1. Wählen Sie **Launch erstellen** aus.

1. Navigieren Sie zum entsprechenden Ordner und wählen Sie die Fragmente aus, die in den Launch aufgenommen werden sollen:

   ![Inhaltsfragmente für neuen Launch auswählen](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-select-cfs.png)

1. Wählen Sie **Weiter** aus.

1. Geben Sie Details an, um den Launch zu konfigurieren:

   * **Titel**
   * **Beschreibung**
   * **Verweise einschließen**: Erstellen Sie den Launch entweder mit oder ohne, einschließlich referenzierter Inhaltsfragmente. Standardmäßig sind referenzierte Fragmente enthalten.

     >[!NOTE]
     >
     >Siehe [Details zu enthaltenen Verweisen](#details-concerning-included-references)

   * **Veröffentlichungsbereit**: Wenn Sie diesen Umschalter aktivieren, werden die Fragmente automatisch veröffentlicht, wenn der Launch zur Quelle hochgestuft wird.

   ![Details für neuen Launch](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-launch-details.png)

1. **Speichern** Sie die Konfiguration.

1. Sie kehren zur Registerkarte **Launches** der Inhaltsfragmentkonsole zurück, auf der Folgendes geschieht:

   * Ihr neuer Launch wird jetzt aufgelistet
   * In einer Meldung wird bestätigt, dass die Launch-Erstellung begonnen hat:

      * **Der Vorgang wurde gestartet, um einen neuen Launch zu erstellen, den Fortschritt in AEM zu überwachen und die Seite nach Abschluss neu zu laden.**

1. Wählen **Anzeigen** aus dem Meldungsfeld aus, um weitere Details in der AEM-Konsole für ([) ](/help/operations/asynchronous-jobs.md).

   ![Neuer Launch in der Konsole](/help/sites-cloud/administering/content-fragments/assets/cf-launches-new-launch-in-console.png)

## Launch-Inhalt bearbeiten {#edit-launch-content}

So bearbeiten Sie die Inhaltsfragmente in Ihrem Launch:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die **Launches**.

1. Wählen Sie den Launch aus, um die Symbolleistenaktionen anzuzeigen.

1. Wählen Sie **Launch öffnen** aus.

   Ihr Launch wird zusammen mit den darin enthaltenen Fragmenten angezeigt.

   ![Bearbeiten von Launch-Inhalten](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-launch-content.png)

1. Wählen Sie **Bearbeiten** für das Fragment aus, das Sie aktualisieren möchten. Er wird wie gewohnt im [Fragment](/help/sites-cloud/administering/content-fragments/authoring.md)Editor) geöffnet.

## Verwalten von Inhalten in einem Launch {#manage-content-within-a-launch}

So verwalten Sie die Inhaltsfragmente in Ihrem Launch und bearbeiten auch ihre Inhalte:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die **Launches**.

1. Wählen Sie Ihren Launch aus.

1. Wählen Sie **Quellen bearbeiten** aus.

   Die Quellfragmente Ihres Launches werden angezeigt.

   ![Source bearbeiten](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-sources.png)

1. Sie haben folgende Möglichkeiten:

   1. **Quellen hinzufügen**, um Ihrem Launch weitere Fragmente hinzuzufügen.

      * Wenn **Verweise einschließen** für den Launch wahr ist, werden alle referenzierten Inhaltsfragmente auch in den Launch eingebracht (falls noch nicht vorhanden).

   1. Wählen **für** Quellfragment, das Sie aktualisieren möchten, „Bearbeiten“ aus. Er wird wie gewohnt im [Fragment](/help/sites-cloud/administering/content-fragments/authoring.md)Editor) geöffnet.

   1. Wählen Sie ein Fragment und dann in **Symbolleiste die Aktion** Quellen löschen“ aus, um dieses Fragment aus dem Launch zu entfernen.

      * Wenn **Verweise einschließen** für den Launch wahr ist, werden alle referenzierten Inhaltsfragmente auch aus dem Launch entfernt, es sei denn, sie werden auch von anderen Inhaltsfragmenten referenziert, die sich noch im Launch befinden.

   >[!NOTE]
   >
   >Siehe [Details zu enthaltenen Verweisen](#details-concerning-included-references)

## Launch mit Quelle vergleichen {#compare-launch-to-source}

Es wird empfohlen, vor jeder Rebase- oder Promote-Aktion immer die Quelle und den Launch zu vergleichen, um die Änderungen und ihre Auswirkungen auf Ihren Inhalt zu bestätigen (beide Aktionen überschreiben den Zielinhalt):

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die **Launches**.

1. Wählen Sie Ihren Launch aus.

1. Wählen Sie **Launch mit Source vergleichen** aus.

   * Die Quell- und Launch-Fragmente werden nebeneinander angezeigt, um die Unterschiede hervorzuheben.
      * Source-Fragmente werden auf der linken Seite und Launch-Fragmente auf der rechten Seite angezeigt.
      * Aktualisierungen sind hervorgehoben:
         * Source: Blau
         * Start: rosa
         * Konflikte: gelb
   * Die [Promote](#promote-a-launch-to-source) und [Rebase](#rebase-a-launch-from-source)-Aktionen sind oben rechts verfügbar.
   * **Updates gefunden**: Links oben wird eine Zusammenfassung aller Updates angezeigt. Die Anzahl der Quellaktualisierungen in Blau, die Anzahl der Launch-Aktualisierungen in Rosa und die Aktualisierungen für beide (Konflikte) in Gelb.
      * Mit den Augensymbolen können Sie die tatsächlichen Inhaltsaktualisierungen anzeigen oder ausblenden, um einen klareren Überblick zu erhalten.
   * Mit **Einschließen**-Schiebereglern können Sie die Inhaltsfragmente definieren, die in den nachfolgenden Heraufstufen- oder Neubasisvorgang aufgenommen werden sollen:
      * **Alle einschließen** oben rechts
      * **Einschließen** über jedem Fragment im Launch

     >[!NOTE]
     >
     >Die Schieberegler gelten nur für Hochstufen- und Neubasieren-Aktionen, die vom Vergleichsbildschirm aus ausgeführt werden.

   * Inhaltsfragmente werden auf Feldebene angezeigt (Inhaltsfragmentelementebene/Datentypebene), wobei die Änderungen durch Hervorhebungen hervorgehoben werden.
   * Wählen **Ansicht**, um die Unterschiede neu zu berechnen.

   ![Source und Launch vergleichen](/help/sites-cloud/administering/content-fragments/assets/cf-launches-compare.png)

## Neubasieren von Launches (aus Source) {#rebase-a-launch-from-source}

Wenn Aktualisierungen an den Quellfragmenten vorgenommen wurden und Sie diese Änderungen in Ihren Launch kopieren möchten:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die **Launches**.

1. Wählen Sie Ihren Launch und Ihre Fragmente aus.

1. Wählen Sie **Rebase** aus.

>[!NOTE]
>
>Sie können einen Launch auch **neu basieren** von **[Launch mit Source vergleichen](#compare-launch-to-source)**.

## Hochstufen eines Launches (nach Source) {#promote-a-launch-to-source}

Wenn Ihr Launch zur Veröffentlichung bereit ist, sollte er in die Quelle kopiert werden. Sie können dies entweder in der Konsole tun oder die Einstellungen so konfigurieren, dass dies automatisch zu einem bestimmten Datum und zu einer bestimmten Uhrzeit geschieht.

### Manuell hochstufen {#promote-manually}

Wenn Ihr Launch zur Veröffentlichung bereit ist, kann er mit der expliziten Aktion in die Quelle kopiert werden:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die **Launches**.

1. Wählen Sie Ihren Launch und Ihre Fragmente aus.

1. Wählen Sie **Bewerben** aus.

>[!NOTE]
>
>Sie können einen Launch auch **Hochstufen** von **Launch mit Source vergleichen**.

### Automatisch hochstufen {#promote-automatically}

Damit ein Launch automatisch zu einem bestimmten Datum und zu einer bestimmten Uhrzeit hochgestuft wird, müssen Sie Folgendes tun:

1. Definieren Sie **Promote-Datum** und -Uhrzeit im rechten Bereich der Registerkarte [Launches](#launches-in-the-content-fragment-console).

1. Wenn der Inhalt veröffentlicht werden kann, wenn er hochgestuft wird, setzen **beim [Erstellen des Launches](#create-a-launch) oder im rechten Bereich der Registerkarte [Launches“ auf &quot;** fertig](#launches-in-the-content-fragment-console).

## Löschen von Launches {#delete-a-launch}

Nachdem Sie Ihren Launch hochgestuft oder entschieden haben, dass Sie ihn nicht mehr benötigen, können Sie ihn löschen:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die **Launches**.

1. Wählen Sie Ihren Launch aus.

1. Wählen Sie **Launch löschen** aus.

   Sie werden aufgefordert, die Aktion zu bestätigen, bevor der Launch gelöscht wird.

## Details zu enthaltenen Verweisen {#details-concerning-included-references}

Für Launches werden die folgenden Inhaltsfragmentverweise berücksichtigt, abhängig vom [Datentyp](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types):

* Der **Fragmentverweis** Datentyp, der sowohl für Verweise auf einzelne Fragmente als auch für Fragmentverweise mit mehreren Feldern gilt.
* Fragmente, auf die innerhalb des Datentyps **Mehrzeiliger Text** bei Verwendung von **Rich-Text** verwiesen wird.

Alle Punkte gelten auch für Fragmente, auf die in Varianten verwiesen wird

Folgendes wird nicht berücksichtigt:

* Fragmente, auf die innerhalb von Inhaltsreferenz-Datentypen verwiesen wird **sowohl** Inhaltsreferenz) (pfadbasiert) als auch **Inhaltsreferenz (UUID)**.
* Fragmente, auf die innerhalb des **Fragmentverweis (UUID)** Datentyps verwiesen wird.