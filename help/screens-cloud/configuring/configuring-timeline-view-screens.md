---
title: Konfigurieren der Timeline-Ansicht für AEM Screens
description: Auf dieser Seite wird beschrieben, wie Sie eine Timeline-Ansicht in Screens as a Cloud Service konfigurieren.
exl-id: 53afe1f5-8f0b-4cca-a819-d3e9375cbe37
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 98%

---

# Konfigurieren der Timeline-Ansicht für AEM Screens {#configuring-timelineview-screens}

## Einführung {#introduction}

In diesem Abschnitt wird beschrieben, wie Sie eine Timeline-Ansicht für AEM Screens erstellen.

AEM bietet eine Suite von Funktionen, mit denen mehrere Personen in Gruppen in einem Unternehmen bei der Erstellung, Verwaltung und Verwendung von Kanälen zusammenarbeiten können.
In der Timeline, die sich in der linken Leiste befindet, werden die Kanäle, der Speicherort oder der Lebenszyklus eines beliebigen Screen-Ordners in der zeitlichen Reihenfolge beschrieben, in der angegeben wird, was mit ihm über seine Lebensdauer passiert ist. Diese kann nach Typ gefiltert werden.
Die Timeline-Leiste bietet zusätzlich zu den Lebenszyklusprotokollen die folgenden Funktionen.

![Profil auf Ordner anwenden](/help/screens-cloud/assets/configure/Screens-timeline1.jpg)

![Profil auf Ordner anwenden](/help/screens-cloud/assets/configure/screens-timeline2.jpg)

Führen Sie die folgenden Schritte aus, um eine Timeline-Ansicht für AEM Screens zu erstellen:

1. Kommentar hinzufügen
1. eine Version speichern
1. einen Workflow starten

Die folgenden Abschnitte beschreiben diese Schritte detaillierter.

### Kommentar hinzufügen {#addcomment}

Die über die Timeline verfügbare Kommentierung ermöglicht es Benutzenden, einen zentralisierten und historischen Eintrag für Diskussionen zu erstellen, die über den Kanal, den Speicherort oder einen beliebigen Ordner auf dem Bildschirm stattfinden.
Kommentare bieten AEM-Benutzenden eine gute konsolidierte Möglichkeit, sich mit einer Methode zu besprechen, die beibehalten werden kann, sodass andere Personen wichtige Entscheidungen verstehen können.

1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten.
1. Wählen Sie den Kanal aus. 
1. Öffnen Sie die Spalte **Zeitleiste**.
1. Fügen Sie Ihren Kommentar hinzu und drücken Sie die **Eingabetaste**.

![Hinzufügen eines Kommentars](/help/screens-cloud/assets/configure/screen-timeline3.jpg)

Die Informationen in der Timeline werden aktualisiert, um anzugeben, dass der Kommentar hinzugefügt wurde.

![Hinzufügen eines Kommentars](/help/screens-cloud/assets/configure/screens-timeline4.jpg)

### Speichern einer Version {#saveversion}

Durch die Versionierung wird eine „Momentaufnahme“ eines Kanals zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung können Sie die folgenden Aktionen durchführen:

* Erstellen einer Version eines Kanals.
* Wiederherstellen einer früheren Version eines Kanals, z. B.:
   * zum Rückgängigmachen einer Änderung an der Seite.
* Vergleichen der aktuellen Version eines Kanals mit einer früheren Version:
   * zum Hervorheben der Unterschiede im Kanalinhalt.


#### Erstellen einer neuen Version {#createnewversion}

1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten.
1. Wählen Sie den Kanal aus. 
1. Öffnen Sie die Spalte **Timeline**.
1. Klicken Sie auf die Schaltfläche (drei Punkte) neben dem Kommentarfeld am unteren Rand der Seite.

   ![Hinzufügen eines Kommentars](/help/screens-cloud/assets/configure/screens-timeline5.jpg)

1. Wählen Sie **Als Version speichern**.
1. Geben Sie eine **Beschriftung** und einen **Kommentar** für die Version ein.

   ![Hinzufügen eines Kommentars](/help/screens-cloud/assets/configure/screens-timeline6.jpg)

1. Bestätigen Sie die neue Version, indem Sie **Erstellen** auswählen. Die Informationen in der Timeline werden entsprechend der neuen Version aktualisiert.

#### Zurücksetzen auf eine Version {#revertversion}

Wiederherstellen einer früheren Version für die ausgewählte Seite:

1. Navigieren Sie zum Kanal, um einen Kommentar hinzuzufügen.
1. Wählen Sie den Kanal aus. 
1. Öffnen Sie die Spalte **Timeline**.
1. Wählen Sie aus der Dropdown-Liste zum Filtern entweder **Alle anzeigen** oder **Versionen**. Die Kanalversionen für den ausgewählten Kanal werden aufgelistet.
1. Wählen Sie die Version aus, die Sie wiederherstellen möchten. Die möglichen Optionen werden angezeigt:

   ![Hinzufügen eines Kommentars](/help/screens-cloud/assets/configure/screens-timeline7.jpg)

1. Wählen Sie **Auf diese Version zurücksetzen**. Die ausgewählte Version wird wiederhergestellt und die Informationen in der Timeline werden aktualisiert.

#### Anzeigen der Vorschau einer Version {#previewversion}

Sie können eine Vorschau einer bestimmten Version anzeigen:

1. Navigieren Sie zum Kanal, um einen Kommentar hinzuzufügen.
1. Wählen Sie den Kanal aus. 
1. Öffnen Sie die Spalte **Timeline**.
1. Wählen Sie aus der Dropdown-Liste zum Filtern entweder **Alle anzeigen** oder **Versionen**. Die Kanalversionen für den ausgewählten Kanal werden aufgelistet.
1. Wählen Sie die Version, die Sie in der Vorschau anzeigen möchten.  Die möglichen Optionen werden angezeigt:

   ![Anzeigen der Versionsvorschau](/help/screens-cloud/assets/configure/screens-timeline8.jpg)

1. Wählen Sie **Vorschau**. Der Kanal wird auf einer neuen Registerkarte angezeigt.

#### Vergleichen einer Version mit der aktuellen Version {#compareversion}

Sie können eine bestimmte Version mit der aktuellen Version vergleichen:

1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten.
1. Wählen Sie den Kanal aus. 
1. Öffnen Sie die Spalte **Timeline**.
1. Wählen Sie aus der Dropdown-Liste zum Filtern entweder **Alle anzeigen** oder **Versionen**. Die Kanalversionen für den ausgewählten Kanal werden aufgelistet.
1. Wählen Sie die Version aus, die Sie vergleichen möchten.  Die möglichen Optionen werden angezeigt:

   ![Vergleichen der Version](/help/screens-cloud/assets/configure/screens-timeline9.jpg)

1. Wählen Sie **Mit aktueller Version vergleichen** aus. Das Popup wird geöffnet und zeigt die Unterschiede an.

### Starten eines Workflows {#workflowstart}

Beim Authoring können Sie Workflows aufrufen, um auf Ihren Kanälen Maßnahmen zu ergreifen. Es ist auch möglich, mehrere Workflows anzuwenden.
Wenn Sie den Workflow anwenden, geben Sie die folgenden Informationen an:

* Der anzuwendende Workflow.
* Optional ein Titel, der zur Identifizierung der Workflow-Instanz im Posteingang einer Benutzerin oder eines Benutzers dient.
* Die Workflow-Payload.

#### Starten des Workflows

1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten.
1. Wählen Sie den Kanal aus. 
1. Öffnen Sie die Spalte **Timeline**.
1. Klicken Sie auf die Schaltfläche (drei Punkte) neben dem Kommentarfeld unten.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline10.jpg)

1. Wählen Sie **Workflow starten** aus.
1. Der Assistent „Workflow erstellen“ wird geöffnet und gibt die Workflow-Details an.
1. Wählen Sie **Workflow-Modell** aus der Dropdown-Liste und geben Sie den Workflow-Titel ein.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline11.jpg)

1. Fahren Sie fort, indem Sie auf **Weiter** klicken.
1. Im Schritt „Umfang“ haben Sie folgende Möglichkeiten:
   * **Inhalte hinzufügen**, um dem Workflow zusätzliche Ressourcen hinzuzufügen.
   * **Untergeordnete Elemente einbeziehen**, um anzugeben, dass untergeordnete Elemente der betreffenden Ressource im Workflow enthalten sind.
   * **Auswahl entfernen**, um die betreffende Ressource aus dem Workflow zu entfernen.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline12.jpg)

1. Wählen Sie **Erstellen**, um den Assistenten zu schließen und die Workflow-Instanz zu erstellen. 
1. Je nach ausgewähltem Workflow-Modell müssen Sie eventuell einige zusätzliche Aktionen durchführen, um den Workflow abzuschließen.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline13.jpg)
