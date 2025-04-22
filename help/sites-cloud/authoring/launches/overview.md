---
title: Launches
description: Launches helfen Ihnen, Inhalte für eine künftige Version effizient zu entwickeln. So sind Sie in der Lage, Änderungen für eine spätere Veröffentlichung vorzunehmen – unter Beibehaltung der aktuellen Seiten.
exl-id: 3e410120-d08f-4d05-932f-07bc4440af2b
solution: Experience Manager Sites
feature: Authoring, Launches
role: User
source-git-commit: 9ddda040eda85b29c86a4940cb656f26073b0f12
workflow-type: ht
source-wordcount: '957'
ht-degree: 100%

---

# Launches {#launches}

Launches helfen Ihnen, Inhalte für eine künftige Version effizient zu entwickeln.

Ein *Launch* wird erstellt, damit Sie Änderungen zur Vorbereitung auf spätere Veröffentlichungen vornehmen und gleichzeitig die aktuellen Seiten pflegen können. Das bedeutet, dass Sie tatsächlich zwei Versionen gleichzeitig bearbeiten: Seiten, die derzeit veröffentlicht sind, und eine Version dieser Seiten, die zu einem späteren Zeitpunkt veröffentlicht werden soll. Wenn es so weit ist, können Sie die Originalseiten ersetzen und die neue Version veröffentlichen.

Erstellen Sie einen *Launch* und leiten Sie Ihre *Launch*-Seiten nach deren Bearbeitung und Aktualisierung wieder an die *Quelle* *zurück*. Sie können dann diese *Quellseiten* (oberste Ebene) aktivieren. Durch die Weiterleitung wird der Launch-Inhalt wieder auf die Quellseiten kopiert und kann entweder manuell oder automatisch ausgeführt werden (abhängig von den Feldern, die beim Erstellen und Bearbeiten des Launches festgelegt wurden).

Beispiel: Die saisonalen Produktseiten in Ihrem Online-Shop werden einmal pro Quartal aktualisiert, damit die präsentierten Produkte der aktuellen Saison entsprechen. Zur Vorbereitung auf die nächste Quartals-Aktualisierung können Sie einen Launch der relevanten Web-Seiten erstellen. Während des Quartals werden die folgenden Änderungen in der Launch-Kopie gesammelt:

* Änderungen an den Quellseiten, die die Folge normaler Wartungsarbeiten sind. Diese Änderungen werden automatisch in den Launch-Seiten dupliziert.
* Änderungen, die in Vorbereitung auf das nächste Quartal direkt auf den Launch-Seiten vorgenommen werden.

Sie können auch Folgendes durchführen:

* Navigieren durch Inhalte in der Launch-Verzweigung; Hinzufügen oder Entfernen von Seiten nach Bedarf
* Anzeigen in der Vorschau, wie veröffentlichte Inhalte zu einem bestimmten Zeitpunkt in der Zukunft aussehen werden

Wenn ein neues Quartal beginnt, leiten Sie die Launch-Seiten weiter, damit Sie die Quellseiten veröffentlichen können, die den aktualisierten Inhalt enthalten. Sie können entweder alle Seiten weiterleiten oder nur die Seiten, die Sie geändert haben.

Launches können auch:

* Für mehrere Stammverzweigungen erstellt werden. Sie können zwar den Launch für die gesamte Site erstellen (und die Änderungen dort vornehmen), dies kann jedoch sehr umständlich sein, da die gesamte Site kopiert werden muss. Wenn Hunderte oder sogar Tausende von Seiten beteiligt sind, wirken sich die Kopieraktion und später die für die Promotions-Aufgaben erforderlichen Vergleiche auf die Systemanforderungen und die Leistung aus.
* Verschachtelt werden (ein Launch innerhalb eines Launches), um Ihnen die Möglichkeit zu geben, einen Launch aus einem bestehenden Launch zu erstellen, sodass Autorinnen und Autoren sich die bereits vorgenommenen Änderungen zunutze machen können, anstatt dieselben Änderungen mehrfach für jeden Launch vornehmen zu müssen.

In diesem Abschnitt wird beschrieben, wie Sie Launch-Seiten innerhalb der Sites-Konsole oder der [Konsole „Launches“](#the-launches-console) erstellen, bearbeiten und weiterleiten (und bei Bedarf [löschen](/help/sites-cloud/authoring/launches/creating.md#deleting-a-launch)):

* [Erstellen von Launches](/help/sites-cloud/authoring/launches/creating.md)
* [Bearbeiten von Launches](/help/sites-cloud/authoring/launches/editing.md)
* [Verwalten von Seiten in Launches](/help/sites-cloud/authoring/launches/managing-pages.md)
* [Verwenden von Timewarp zur Vorschau von Inhalten basierend auf Launches](/help/sites-cloud/authoring/launches/preview.md)
* [Weiterleiten von Launches](/help/sites-cloud/authoring/launches/promoting.md)

## Der Ablauf eines Launches {#launches-the-order-of-events}

Mit Launches können Sie effizient den Inhalt für eine zukünftige Veröffentlichung einer oder mehrerer aktivierter Web-Seiten entwickeln.

Launches ermöglichen Folgendes:

* Erstellen Sie eine Kopie Ihrer Quellseiten:
   * Die Kopie ist Ihr Launch.
   * Die Quellseiten der höchsten Stufe werden als **Produktion** bezeichnet.
      * Die Quellseiten können aus mehreren (verschiedenen) Verzweigungen stammen.

  ![Reihenfolge der Launches](/help/sites-cloud/authoring/assets/launches-order.png)

* Bearbeiten Sie die Launch-Konfiguration:
   * Sie können Seiten bzw. Verzweigungen zum Launch hinzufügen oder entfernen.
   * Sie können Launch-Eigenschaften bearbeiten, z. B. **Titel**, **Launch-Datum** und die Markierung **Produktionsbereit**.
* Sie können Inhalte entweder manuell oder automatisch weiterleiten und veröffentlichen:
   * Manuell:
      * Leiten Sie Ihren Launch-Inhalt, wenn er zur Veröffentlichung bereit ist, wieder an das **Ziel** (Quellseiten) zurück.
      * Veröffentlichen Sie den Inhalt von den Quellseiten (nachdem die Seiten weitergeleitet wurden).
      * Leiten Sie entweder alle Seiten oder nur die überarbeiteten Seiten weiter.
   * Automatisch (dies beinhaltet Folgendes):
      * Das Feld **Launch-Datum** (**Live**-**Datum)**: Dieses Feld kann beim Erstellen oder Bearbeiten eines Launches festgelegt werden.
      * Die Markierung **Produktionsbereit**: Dies kann nur beim Bearbeiten eines Launches festgelegt werden.
      * Wenn das Flag **Produktionsbereit** gesetzt wurde, wird der Launch automatisch am angegebenen **Launch-Datum** (**Datum der** Live-Schaltung **)** an die Produktionsseiten weitergeleitet. Nach der Promotion werden die Produktionsseiten automatisch veröffentlicht.\
        Wenn kein Datum ausgewählt wurde, hat die Markierung keine Auswirkungen.
* Paralleles Aktualisieren der Quell- und Launch-Seiten:
   * Änderungen an den Quellseiten werden automatisch in der Launch-Kopie implementiert (wenn sie mit Vererbung eingerichtet wurden, d. h. in Form einer Live Copy).
   * Änderungen an der Launch-Kopie können ohne Störung dieser automatischen Aktualisierungen oder der Quellseiten vorgenommen werden.

  ![Parallele Aktionen](/help/sites-cloud/authoring/assets/launches-parallel.png)

* [Erstellen eines verschachtelten Launches](/help/sites-cloud/authoring/launches/creating.md#creating-a-nested-launch) – ein Launch innerhalb eines Launches:
   * Die Quelle ist ein schon vorhandener Launch.
   * Sie können [einen verschachtelten Launch zu einem beliebigen Ziel weiterleiten](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch). Dies kann ein übergeordneter Launch oder die Quellseiten der obersten Ebene (Produktion) sein.

  ![Ein verschachtelter Launch](/help/sites-cloud/authoring/assets/launches-nested.png)

  >[!CAUTION]
  >
  >Durch Löschen eines Launches werden der Launch selbst sowie alle nachfolgenden verschachtelten Launches entfernt.

>[!NOTE]
>
>Für das Erstellen und Bearbeiten von Launches sind Zugriffsrechte auf `/content/launches` erforderlich (wie bei der Standardgruppe `content-authors`).
>
>Bitte wenden Sie sich an Ihre Systemadmins, falls Probleme auftreten.

## Launches in „Verweise“ (Sites-Konsole) {#launches-in-references-sites-console}

1. Navigieren Sie in der **Sites**-Konsole zur Quelle der Launches.
1. Öffnen Sie die Leiste **Referenzen** und wählen Sie die Quellseite aus.
1. Wählen Sie **Launches** aus. Die vorhandenen Launches werden aufgelistet, mit Zugriff auf die **Launches-Konsole**:

   ![Verweise auf Launches in der Sites-Konsole](/help/sites-cloud/authoring/assets/launches-references.png)

1. Wählen Sie den entsprechenden Launch aus. Die Liste der möglichen Aktionen wird daraufhin angezeigt:

   ![Aktionen für Launches in der Sites-Konsole](/help/sites-cloud/authoring/assets/launches-references-actions.png)

## Die Konsole „Launches“  {#the-launches-console}

Die Konsole „Launches“ bietet eine Zusammenfassung Ihrer Launches und ermöglicht es Ihnen, auf diese zu reagieren.

![Launches-Konsole – Verwalten von Inhalten](/help/sites-cloud/authoring/assets/launches-navigate-launches-console.png)

Auf die Konsole kann wie folgt zugegriffen werden:

* Über die Konsole **Tools**: **Tools**, **Allgemein**, **Launches**.

* **Launches-Konsole** unten im Abschnitt **Launches** der Leiste **Verweise**, wenn Sie durch Quellinhalte in der Sites-Konsole navigieren.

  ![Launches-Konsole in Verweisen auf Launches in der Sites-Konsole](/help/sites-cloud/authoring/assets/launches-references.png)

* Die Schaltfläche **Launch** oben rechts beim Navigieren in Launch-Inhalten in der Sites-Konsole:

  ![Launches-Option in der Sites-Konsole](/help/sites-cloud/authoring/assets/launches-console-navigate-launch-content.png)
