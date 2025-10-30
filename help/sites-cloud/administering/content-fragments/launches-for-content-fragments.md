---
title: Launches für Inhaltsfragmente
description: Erfahren Sie, wie Sie Launches für Inhaltsfragmente in Adobe Experience Manager as a Cloud Service verwenden. Mit Launches können Sie Inhalte für eine zukünftige Veröffentlichung effizient entwickeln und gleichzeitig Ihre aktuellen Inhaltsfragmente beibehalten.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
exl-id: c0b9e571-3be5-42ab-8d56-d93e8ef4c2f7
source-git-commit: 39ff527f0082a18f0853964172eabf438caa1098
workflow-type: tm+mt
source-wordcount: '1582'
ht-degree: 100%

---

# Launches für Inhaltsfragmente {#launches-for-content-fragments}

In Adobe Experience Manager (AEM) as a Cloud Service helfen Ihnen Launches, Inhalte für eine künftige Version effizient zu entwickeln.

Ein *Launch* wird erstellt, damit Sie Änderungen zur Vorbereitung auf spätere Veröffentlichungen vornehmen und gleichzeitig die aktuellen Inhalte pflegen können. Für Inhaltsfragmente bedeutet dies, dass Sie tatsächlich zwei Versionen gleichzeitig bearbeiten: Inhalte, die derzeit veröffentlicht sind, und eine Version dieser Inhalte, die zu einem späteren Zeitpunkt veröffentlicht werden soll. Wenn es so weit ist, können Sie die den Inhalt der ursprünglichen Inhaltsfragmente ersetzen und die neuen Versionen veröffentlichen.

>[!NOTE]
>
>Launches sind auch für Seiten verfügbar. Die grundlegenden Konzepte sind dieselben, aber es gibt Unterschiede bei ihrer Verwaltung in AEM.
>
>Ausführliche Informationen finden Sie unter [Launches für Seiten](/help/sites-cloud/authoring/launches/overview.md).

Erstellen Sie einen *Launch* und bearbeiten und aktualisieren Sie dann Ihre Inhaltsfragmente in Ihrem *Launch*. Wenn in dieser Phase Änderungen an den *Quellfragmenten* vorgenommen werden, können Sie diese mit dem Vorgang *Rebase ausführen* in den *Launch* kopieren. Wenn er bereit ist, wird der Launch-Inhalt über *Bewerben* zurück an die Quelle dupliziert. Anschließend können Sie die Quellfragmente entweder manuell oder automatisch aktivieren (abhängig von den Feldern, die beim Erstellen und Bearbeiten des Launches festgelegt wurden). Sie können auch angeben, ob referenzierte Fragmente in diesen Prozess einbezogen werden sollen.

Die Fragmente für saisonale Produkte in Ihrem Online-Shop werden beispielsweise einmal pro Quartal aktualisiert, damit die präsentierten Produkte der aktuellen Saison entsprechen. Zur Vorbereitung auf die nächste Quartalaktualisierung können Sie einen Launch der relevanten Fragmente erstellen. Während des Quartals werden die folgenden Änderungen in der Launch-Kopie gesammelt:

* Bearbeitungen, die direkt an den Launch-Fragmenten in Vorbereitung auf das nächste Quartal vorgenommen werden.
* Änderungen an den Quellinhaltsfragmenten, die Sie mit *Rebase ausführen* auf Ihre Launch-Seiten übertragen.
* Sie können auch durch Inhalte in der Launch-Verzweigung navigieren und Fragmente je nach Bedarf hinzufügen oder entfernen.

Wenn ein neues Quartal beginnt, leiten Sie die Launch-Seiten weiter, damit Sie die Quellseiten veröffentlichen können, die den aktualisierten Inhalt enthalten. Sie können entweder alle Fragmente weiterleiten oder nur die Seiten, an denen Sie Änderungen vorgenommen haben.

![Überblick über Launches – Ausführen von Rebases und Weiterleiten](/help/sites-cloud/administering/content-fragments/assets/cf-launches-overview.png)

In diesem Abschnitt wird beschrieben, wie Sie Launches über die [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/managing.md) erstellen, bearbeiten, bewerben und Rebases ausführen sowie bei Bedarf löschen.

* [Aufrufen und Anzeigen von Launches in der Inhaltsfragmentkonsole](#launches-in-the-content-fragment-console)
* [Erstellen eines Launch](#create-a-launch)
* [Bearbeiten von Launch-Inhalten](#edit-launch-content)
* [Verwalten von Inhalten in einem Launch](#manage-content-within-a-launch)
* [Vergleichen von Launch mit Quelle](#compare-launch-to-source)
* [Ausführen eines Rebase eines Launch von einer Quelle](#rebase-a-launch-from-source)
* [Weiterleiten eines Launch an die Quelle](#promote-a-launch-to-source)
* [Löschen eines Launch](#delete-a-launch)

## Launches in der Inhaltsfragmentkonsole {#launches-in-the-content-fragment-console}

Auf der Registerkarte **Launches** in der Inhaltsfragmentkonsole können Sie Launches erstellen, alle vorhandenen Launches auflisten, die wichtigsten Eigenschaften anzeigen und Aktionen für sie durchführen.

Wenn kein Launch ausgewählt ist, können Sie [einen neuen Launch erstellen](#create-a-launch).

![Registerkarte „Launches“ in der Konsole](/help/sites-cloud/administering/content-fragments/assets/cf-launches-tab.png)

Wählen Sie einen Launch aus, um Folgendes anzuzeigen:

* die Symbolleiste mit den verfügbaren Aktionen
* das rechte Panel mit den Eigenschaften und weiteren Aktionen

![Symbolleiste mit Launch-Aktionen in der Konsole](/help/sites-cloud/administering/content-fragments/assets/cf-launches-actions.png)

Die Symbolleiste ermöglicht Ihnen Folgendes:

* **[Öffnen eines Launch](#edit-launch-content)**
* **[Bearbeiten von Quellen](#manage-content-within-a-launch)**
* **[Vergleichen von Launch mit Quelle](#compare-launch-to-source)**
* **[Weiterleiten](#promote-a-launch-to-source)**
* **[Ausführen eines Rebase](#promote-a-launch-to-source)**
* **[Löschen eines Launch](#delete-a-launch)**

Im rechten Panel haben Sie folgende Möglichkeiten:

* Bearbeiten des Launch-**Titels**
* Bearbeiten der Launch-**Beschreibung**
* Aktualisieren der Konfigurationsdetails, die beim [Erstellen des Launch](#create-a-launch) festgelegt wurden:

   * **Verweise einbeziehen**: Erstellen Sie den Launch entweder mit referenzierten Inhaltsfragmenten oder ohne. Standardmäßig werden referenzierte Fragmente eingeschlossen.

      * Referenzierte Fragmente sind auch betroffen, wenn Sie [Fragmente zu einem späteren Zeitpunkt hinzufügen oder entfernen](#manage-content-within-a-launch).

     >[!NOTE]
     >
     >Siehe [Details zu einbezogenen Verweisen](#details-concerning-included-references)

   * **Bereit für die Veröffentlichung**: Durch Aktivieren dieses Umschalters werden die Fragmente automatisch veröffentlicht, wenn der Launch zur Quelle weitergeleitet wird.

* Definieren Sie außerdem:

   * Ein **Datum und eine Uhrzeit für die Weiterleitung**: Wenn der [Launch automatisch weitergeleitet werden soll](#promote-automatically)

## Erstellen eines Launch {#create-a-launch}

So erstellen Sie einen Launch:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die Registerkarte **Launches**.

1. Wählen Sie **Launch erstellen** aus. 

1. Navigieren Sie zum entsprechenden Ordner und wählen Sie das Fragment aus, das im Launch aufgenommen werden soll:

   ![Auswählen von Inhaltsfragmenten für neuen Launch](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-select-cfs.png)

1. Wählen Sie **Weiter** aus.

1. Geben Sie Details an, um den Launch zu konfigurieren:

   * **Titel**
   * **Beschreibung**
   * **Verweise einbeziehen**: Erstellen Sie den Launch entweder mit referenzierten Inhaltsfragmenten oder ohne. Standardmäßig werden referenzierte Fragmente eingeschlossen.

     >[!NOTE]
     >
     >Siehe [Details zu einbezogenen Verweisen](#details-concerning-included-references)

   * **Bereit für die Veröffentlichung**: Durch Aktivieren dieses Umschalters werden die Fragmente automatisch veröffentlicht, wenn der Launch zur Quelle weitergeleitet wird.

   ![Details für neuen Launch](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-launch-details.png)

1. **Speichern** Sie die Konfiguration.

1. Sie kehren zur Registerkarte **Launches** der Inhaltsfragmentkonsole zurück, auf der Folgendes geschieht:

   * Ihr neuer Launch wird nun aufgelistet
   * In einer Meldung wird bestätigt, dass die Launch-Erstellung begonnen hat:

      * **Auftrag zur Erstellung von neuem Launch gestartet. Überwachen Sie den Fortschritt in AEM und laden Sie die Seite nach Abschluss neu.**

1. Wählen Sie im Meldungsfeld **Anzeigen** aus, um weitere Details zu [Hintergrundvorgängen](/help/operations/asynchronous-jobs.md) in der AEM-Konsole anzuzeigen.

   ![Neuer Launch in der Konsole](/help/sites-cloud/administering/content-fragments/assets/cf-launches-new-launch-in-console.png)

## Bearbeiten von Launch-Inhalten {#edit-launch-content}

So bearbeiten Sie die Inhaltsfragmente in Ihrem Launch:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die Registerkarte **Launches**.

1. Wählen Sie den Launch aus, um die Aktionen der Symbolleiste anzuzeigen.

1. Wählen Sie **Launch öffnen** aus. 

   Ihr Launch wird zusammen mit den darin enthaltenen Fragmenten angezeigt.

   ![Bearbeiten von Launch-Inhalten](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-launch-content.png)

1. Wählen Sie **Bearbeiten** für das zu aktualisierende Fragment aus. Es wird wie gewohnt im [Fragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md) geöffnet.

## Verwalten von Inhalten in einem Launch {#manage-content-within-a-launch}

So verwalten Sie die Inhaltsfragmente in Ihrem Launch und bearbeiten ihre Inhalte:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die Registerkarte **Launches**.

1. Wählen Sie den Launch aus.

1. Wählen Sie **Quellen bearbeiten** aus.

   Die Quellfragmente Ihres Launches werden angezeigt.

   ![Bearbeiten von Quellen](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-sources.png)

1. Sie haben folgende Möglichkeiten:

   1. **Fügen Sie Quellen hinzu**, um Ihrem Launch weitere Fragmente hinzuzufügen.

      * Wenn für den Launch **Verweise einbeziehen** festgelegt ist, werden auch alle referenzierten Inhaltsfragmente in den Launch importiert (falls sie noch nicht vorhanden sind).

   1. Wählen Sie **Bearbeiten** für das zu aktualisierende Quellfragment aus. Es wird wie gewohnt im [Fragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md) geöffnet.

   1. Wählen Sie ein Fragment und dann in der Symbolleiste die Aktion **Quellen löschen** aus, um dieses Fragment aus dem Launch zu entfernen.

      * Wenn für den Launch **Verweise einbeziehen** festgelegt ist, werden auch alle referenzierten Inhaltsfragmente aus dem Launch entfernt, außer sie werden auch von anderen Inhaltsfragmente im Launch referenziert.

   >[!NOTE]
   >
   >Siehe [Details zu einbezogenen Verweisen](#details-concerning-included-references)

## Vergleichen von Launch mit Quelle {#compare-launch-to-source}

Es wird empfohlen, vor jeder Aktion der Typs „Rebase ausführen“ oder „Bewerben“ immer die Quelle und den Launch zu vergleichen, um die Änderungen und ihre Auswirkungen auf Ihren Inhalt zu bestätigen (beide Aktionen überschreiben den Zielinhalt):

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die Registerkarte **Launches**.

1. Wählen Sie den Launch aus.

1. Wählen Sie **Launch mit Quelle vergleichen** aus.

   * Die Quell- und Launch-Fragmente werden nebeneinander angezeigt, um die Unterschiede hervorzuheben.
      * Quellfragmente werden auf der linken Seite und Launch-Fragmente auf der rechten Seite angezeigt.
      * Aktualisierungen werden hervorgehoben:
         * Quelle: Blau
         * Launch: Rosa
         * Konflikte: Gelb
   * Die Aktionen [Bewerben](#promote-a-launch-to-source) und [Rebase ausführen](#rebase-a-launch-from-source) sind oben rechts verfügbar.
   * **Aktualisierungen gefunden**: Links oben wird eine Zusammenfassung aller Aktualisierungen angezeigt. Die Anzahl der Quellaktualisierungen in blau, die Anzahl der Launch-Aktualisierungen in rosa und die Aktualisierungen von beiden (Konflikte) in gelb.
      * Mit den Augensymbolen können Sie die tatsächlichen Inhaltsaktualisierungen anzeigen oder ausblenden, um einen klareren Überblick zu erhalten.
   * Mit den Schiebereglern bezüglich **Einschlüssen** können Sie die Inhaltsfragmente definieren, die in den nachfolgenden Vorgängen des Typs „Bewerben“ oder „Rebase ausführen“ eingeschlossen werden sollen:
      * **Alle einschließen** oben rechts
      * **Einschließen** über jedem Fragment im Launch

     >[!NOTE]
     >
     >Die Schieberegler gelten nur für Aktionen des Typs „Bewerben“ und „Rebase ausführen“, die vom Vergleichsbildschirm aus ausgeführt werden.

   * Inhaltsfragmente werden auf Feldebene angezeigt (Inhaltsfragmentelement-/Datentypebene), wobei die Änderungen durch Hervorhebungen angezeigt werden.
   * Wählen Sie **Anzeigen**, um die Unterschiede neu zu berechnen.

   ![Vergleichen von Quelle und Launch](/help/sites-cloud/administering/content-fragments/assets/cf-launches-compare.png)

## Ausführen eines Rebase eines Launch (von einer Quelle) {#rebase-a-launch-from-source}

Wenn Aktualisierungen an den Quellfragmenten vorgenommen wurden und Sie diese Änderungen in Ihren Launch kopieren möchten:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die Registerkarte **Launches**.

1. Wählen Sie Ihren Launch und Ihre Fragmente aus.

1. Wählen Sie **Rebase ausführen** aus.

>[!NOTE]
>
>Sie könne einen **Rebase** eines Launch auch von **[Launch mit Quelle vergleichen](#compare-launch-to-source)** aus ausführen.

## Weiterleiten eines Launch (an die Quelle) {#promote-a-launch-to-source}

Wenn Ihr Launch zur Veröffentlichung bereit ist, sollte er in die Quelle kopiert werden. Sie können dies entweder in der Konsole tun oder die Einstellungen so konfigurieren, dass dies automatisch zu einem bestimmten Datum und zu einer bestimmten Uhrzeit geschieht.

### Manuelles Weiterleiten {#promote-manually}

Wenn Ihr Launch zur Veröffentlichung bereit ist, kann er mit folgender expliziter Aktion in die Quelle kopiert werden. 

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die Registerkarte **Launches**.

1. Wählen Sie Ihren Launch und Ihre Fragmente aus.

1. Wählen Sie **Bewerben** aus.

>[!NOTE]
>
>Sie könne einen **Rebase** eines Launch auch von **Launch mit Quelle vergleichen** aus ausführen.

### Automatisches Weiterleiten {#promote-automatically}

Damit ein Launch automatisch zu einem bestimmten Datum und zu einer bestimmten Uhrzeit weitergeleitet wird, müssen Sie Folgendes tun:

1. Definieren Sie das **Datum und die Uhrzeit für die Weiterleitung** im rechten Panel der Registerkarte [Launches](#launches-in-the-content-fragment-console).

1. Wenn der Inhalt bei der Weiterleitung veröffentlicht werden kann, legen Sie beim [Erstellen des Launch](#create-a-launch) oder im rechten Panel der Registerkarte [Launches](#launches-in-the-content-fragment-console) **Bereit für die Veröffentlichung** fest.

## Löschen eines Launch {#delete-a-launch}

Nachdem Sie Ihren Launch weitergeleitet oder entschieden haben, dass Sie ihn nicht mehr benötigen, können Sie ihn löschen:

1. Navigieren Sie zur Inhaltsfragmentkonsole.

1. Öffnen Sie die Registerkarte **Launches**.

1. Wählen Sie den Launch aus.

1. Wählen Sie **Launch löschen** aus.

   Bevor der Launch gelöscht wird, werden Sie zur Bestätigung der Aktion aufgefordert.

## Details zu einbezogenen Verweisen {#details-concerning-included-references}

Die folgenden Inhaltsfragmentverweise werden für Launches berücksichtigt, abhängig vom [Datentyp](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types):

* Der Datentyp **Fragmentreferenz**, der sowohl für Verweise auf einzelne Fragmente als auch für Fragmentverweise mit mehreren Feldern gilt.
* Fragmente, auf die innerhalb des Datentyps **Mehrzeilentext** bei Verwendung von **Rich Text** verwiesen wird.

Alle Punkte gelten auch für Fragmente, auf die in Varianten verwiesen wird

Folgendes wird nicht berücksichtigt:

* Fragmente, auf die innerhalb von Inhaltsreferenz-Datentypen verwiesen wird sowohl **Inhaltsreferenz** (pfadbasiert) als auch **Inhaltsreferenz (UUID)**.
* Fragmente, auf die innerhalb des Datentyps **Fragmentverweis (UUID)** verwiesen wird.
