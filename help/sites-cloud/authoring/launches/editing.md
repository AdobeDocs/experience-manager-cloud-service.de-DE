---
title: Bearbeiten von Launches
description: Nachdem Sie einen Launch für Ihre Seite (oder eine Reihe von Seiten) erstellt haben, können Sie den Inhalt in der „Launch Copy“ der Seiten bearbeiten.
exl-id: d3cd3383-e0a0-4019-9f97-8baa3be99e6e
source-git-commit: abe5f8a4b19473c3dddfb79674fb5f5ab7e52fbf
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 91%

---

# Bearbeiten von Launches {#editing-launches}

## Bearbeiten von Launch-Seiten {#editing-launch-pages}

Wenn ein Launch für eine Seite (oder mehrere Seiten) erstellt wurde, können Sie den Inhalt in der Launch Copy der Seiten bearbeiten.

1. Rufen Sie [Launches aus Verweisen (Konsole „Sites“)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) auf, um die verfügbaren Aktionen anzuzeigen.
1. Klicken Sie auf **Zur Seite gehen**, um die Seite zur Bearbeitung zu öffnen.

Beim Bearbeiten der Seite wird in der oberen Symbolleiste zusammen mit der Variablen **Urlaub** und **Navigieren** options:

![Launch über den Seiten-Editor verlassen und navigieren](/help/sites-cloud/authoring/assets/launches-edit-01.png)

>[!NOTE]
>
>Es ist nicht zulässig, eine Seite innerhalb eines Launchs zu verschieben. Der Versuch, diese Aktion auszuführen, löst eine Warnmeldung aus:
>
>* Warnung: Bei dieser Seite handelt es sich um die Quellseite eines Launches. Das Verschieben der Seite ist nicht zulässig.

### Bearbeiten von Launch-Seiten auf der Basis einer Live Copy {#editing-launch-pages-subject-to-a-live-copy}

Wenn Ihr Launch auf einer [Live Copy](/help/sites-cloud/administering/msm/overview.md) basiert, sehen Sie Folgendes:

* Schlosssymbole (kleine Vorhängeschlösser), wenn Sie eine Komponente bearbeiten (Inhalt und/oder Eigenschaften)
* die Registerkarte **Live Copy** in den **Seiteneigenschaften**

Eine Live Copy wird verwendet, um Inhalte *von* der Quellverzweigung *mit* Ihrer Launch-Verzweigung zu synchronisieren (um Ihren Launch mit den Änderungen an der Quelle zu aktualisieren).

Sie können Änderungen auf dieselbe Weise vornehmen wie für eine standardmäßige Live Copy. Zum Beispiel:

* Durch Klicken auf ein geschlossenes Schloss wird die Synchronisierung unterbrochen und Sie haben die Möglichkeit, neue Aktualisierungen am Inhalt Ihres Launches vorzunehmen. Nach dem Entsperren (offenes Vorhängeschloss) werden Ihre Änderungen nicht durch Änderungen überschrieben, die an derselben Stelle innerhalb des Quellzweigs vorgenommen werden.
* Sie können die Vererbung für eine bestimmte Seite **aussetzen** (und **fortsetzen**).

Siehe [Ändern des Live-Copy-Inhalts](/help/sites-cloud/administering/msm/creating-live-copies.md).

## Vergleichen einer Launch-Seite mit ihrer Quellseite {#comparing-a-launch-page-to-its-source-page}

Um die vorgenommenen Änderungen zu verfolgen, können Sie den Launch in **Referenzen** anzeigen und die Launch- mit der Quellseite vergleichen:

1. Navigieren Sie in der **Sites-Konsole** [zu den Quellseiten Ihres Launches und wählen Sie sie eine aus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie das Bedienfeld **[Verweise](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** und wählen Sie **Launches** aus.
1. Wählen Sie den gewünschten Launch aus und dann **Mit Quelle vergleichen**

   ![Vergleichen von Launch und Quelle](/help/sites-cloud/authoring/assets/launches-compare.png)

1. Die beiden Seiten (Launch und Quelle) werden nebeneinander geöffnet.

   Vollständige Informationen zur Verwendung der Vergleichsfunktion finden Sie unter [Seitenvergleich](/help/sites-cloud/authoring/features/page-diff.md).

## Ändern der verwendeten Quellseiten {#changing-the-source-pages-used}

Sie können jederzeit Seiten zum Bereich der Quellseiten für einen Launch hinzufügen oder daraus entfernen:

1. Sie können auf den Launch wie folgt zugreifen und ihn auswählen:
   * über die [Konsole „Launches“](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Wählen Sie **Bearbeiten** aus.
   * [Verweise (Sites-Konsole)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console), um die verfügbaren Aktionen anzuzeigen:
      * Wählen Sie **Launch bearbeiten** aus.
      * Die Quellseiten werden angezeigt.
1. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie dann mit **Speichern**.

>[!NOTE]
>
>Um Seiten zu einem Launch hinzuzufügen, müssen sie sich unter einem gemeinsamen Sprachstamm befinden. d. h. innerhalb einer einzelnen Site.

## Bearbeiten einer Launch-Konfiguration {#editing-a-launch-configuration}

Sie können die Eigenschaften für einen Launch jederzeit bearbeiten:

1. Sie können auf den Launch wie folgt zugreifen und ihn auswählen:
   * über die [Konsole „Launches“](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Wählen Sie **Eigenschaften** aus.
   * [Verweise (Sites-Konsole)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console), um die verfügbaren Aktionen anzuzeigen:
      * Wählen Sie **Eigenschaften bearbeiten** aus.
      * Die Details werden angezeigt.
1. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie dann mit **Speichern**.
   * Unter [Launches – Reihenfolge der Ereignisse](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) finden Sie Informationen zum Zweck und zur Interaktion der Felder **Launch-Datum** und **Bereit für Produktion**.

## Ermitteln des Launch-Status einer Seite {#discovering-the-launch-status-of-a-page}

Der Status wird angezeigt, wenn Sie einen bestimmten Launch auf der Registerkarte „Verweise“ auswählen (siehe [Launches in Verweisen (Sites-Konsole))](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console).

![Ermitteln des Launch-Status](/help/sites-cloud/authoring/assets/launches-status.png)
