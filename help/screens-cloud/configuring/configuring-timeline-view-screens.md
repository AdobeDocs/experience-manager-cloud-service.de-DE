---
title: Konfigurieren der Timeline-Ansicht für AEM Screens
description: Auf dieser Seite wird beschrieben, wie Sie eine Timeline-Ansicht in Screens as a Cloud Service konfigurieren.
source-git-commit: 30317d006142b3fbfc1b62fab5b4e28cb1b7dbb7
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 9%

---

# Konfigurieren der Timeline-Ansicht für AEM Screens {#configuring-timelineview-screens}

## Einführung {#introduction}

In diesem Abschnitt wird beschrieben, wie Sie eine Timeline-Ansicht für AEM Screens erstellen.

AEM bietet eine Suite von Funktionen, mit denen mehrere Personen in Gruppen in einem Unternehmen bei der Erstellung, Verwaltung und Verwendung von Kanälen zusammenarbeiten können.
In der Timeline, die sich in der linken Leiste befindet, werden die Kanäle, der Speicherort oder der Lebenszyklus eines beliebigen Bildschirmordners in der zeitlichen Reihenfolge beschrieben, in der angegeben wird, was mit ihm über seine Lebensdauer passiert ist. Dies kann nach Typ gefiltert werden.
Die Timeline-Leiste bietet zusätzlich zu den Lebenszyklusprotokollen die folgenden Funktionen.

![Profil auf Ordner anwenden](/help/screens-cloud/assets/configure/Screens-timeline1.jpg)

![Profil auf Ordner anwenden](/help/screens-cloud/assets/configure/screens-timeline2.jpg)

Führen Sie die folgenden Schritte aus, um eine Timeline-Ansicht für AEM Screens zu erstellen:

1. Kommentar hinzufügen
1. eine Version speichern
1. einen Workflow starten

Im folgenden Abschnitt werden diese Schritte detailliert beschrieben.

### Kommentar hinzufügen {#addcomment}

Die über die Timeline verfügbare Kommentierung ermöglicht es Benutzern, einen zentralisierten und historischen Datensatz für Diskussionen zu erstellen, die über den Kanal, den Speicherort oder einen beliebigen Ordner auf dem Bildschirm stattfinden.
Kommentare bieten AEM Benutzern eine gute konsolidierte Möglichkeit, eine Methode zu besprechen, die beibehalten werden kann, sodass andere wichtige Entscheidungen verstehen können.

1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten
1. Kanal auswählen
1. Öffnen Sie die Spalte Timeline .
1. Fügen Sie den gewünschten Kommentar hinzu und drücken Sie die Eingabetaste

![Kommentar hinzufügen](/help/screens-cloud/assets/configure/screen-timeline3.jpg)

Die Informationen in der Timeline werden aktualisiert, um anzugeben, dass der Kommentar hinzugefügt wurde.

![Kommentar hinzufügen](/help/screens-cloud/assets/configure/screens-timeline4.jpg)

### Eine Version speichern {#saveversion}

Durch die Versionierung wird ein &quot;Schnappschuss&quot;eines Kanals zu einem bestimmten Zeitpunkt erstellt. Bei der Versionierung können Sie die folgenden Aktionen durchführen:
* Erstellen Sie eine Version eines Kanals.
* Wiederherstellen eines Kanals auf eine frühere Version, z. B.:
   * , um eine Änderung rückgängig zu machen, die Sie an der Seite vorgenommen haben.
* Vergleichen Sie die aktuelle Version eines Kanals mit einer früheren Version:
   * , um Unterschiede im Kanalinhalt hervorzuheben.


#### Neue Version erstellen {#createnewversion}

1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten
1. Kanal auswählen
1. Öffnen Sie die Spalte Timeline .
1. Klicken Sie auf die Schaltfläche (drei Punkte) neben dem Kommentarfeld am unteren Rand.

   ![Kommentar hinzufügen](/help/screens-cloud/assets/configure/screens-timeline5.jpg)

1. Als Version speichern
1. Geben Sie bei Bedarf einen Titel und einen Kommentar ein

   ![Kommentar hinzufügen](/help/screens-cloud/assets/configure/screens-timeline6.jpg)

1. Bestätigen Sie die neue Version mit Erstellen. Die Informationen in der Timeline werden aktualisiert, um die neue Version anzugeben.

#### Auf eine Version zurücksetzen {#revertversion}

So stellen Sie die ausgewählte Seite auf eine frühere Version zurück:
1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten
1. Kanal auswählen
1. Öffnen Sie die Spalte Timeline .
1. Wählen Sie entweder Alle anzeigen oder Versionen aus dem Dropdown-Menü Filter . Die Kanalversionen für den ausgewählten Kanal werden aufgelistet
1. Wählen Sie die Version aus, die Sie wiederherstellen möchten. Die möglichen Optionen werden angezeigt:

   ![Kommentar hinzufügen](/help/screens-cloud/assets/configure/screens-timeline7.jpg)

1. Wählen Sie Auf diese Version zurück. Die ausgewählte Version wird wiederhergestellt und die Informationen in der Timeline aktualisiert.

#### Vorschau einer Version anzeigen {#previewversion}

Sie können eine Vorschau einer bestimmten Version anzeigen:
1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten
1. Kanal auswählen
1. Öffnen Sie die Spalte Timeline .
1. Wählen Sie entweder Alle anzeigen oder Versionen aus dem Dropdown-Menü Filter . Die Kanalversionen für den ausgewählten Kanal werden aufgelistet
1. Wählen Sie die Version aus, die Sie in der Vorschau anzeigen möchten. Die möglichen Optionen werden angezeigt:

   ![Vorschau der Version](/help/screens-cloud/assets/configure/screens-timeline8.jpg)

1. Wählen Sie Vorschau aus. Der Kanal wird in einer neuen Registerkarte angezeigt.

#### Version mit aktueller Version vergleichen {#compareversion}

Sie können eine bestimmte Version mit der aktuellen Version vergleichen:
1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten
1. Kanal auswählen
1. Öffnen Sie die Spalte Timeline .
1. Wählen Sie entweder Alle anzeigen oder Versionen aus dem Dropdown-Menü Filter . Die Kanalversionen für den ausgewählten Kanal werden aufgelistet
1. Wählen Sie die Version aus, die Sie vergleichen möchten. Die möglichen Optionen werden angezeigt:

   ![Version vergleichen](/help/screens-cloud/assets/configure/screens-timeline9.jpg)

1. Wählen Sie Mit aktueller Version vergleichen aus. Das Popup wird geöffnet, um die Unterschiede anzuzeigen

### Workflow starten {#workflowstart}

Beim Authoring können Sie Workflows aufrufen, um Aktionen auf Ihren Kanälen durchzuführen. Es ist auch möglich, mehr als einen Workflow anzuwenden.
Wenn Sie den Workflow anwenden, geben Sie die folgenden Informationen an:
* Der anzuwendende Workflow
* Optional: Ein Titel, der dabei hilft, die Workflow-Instanz im Posteingang eines Benutzers zu identifizieren
* Die Workflow-Payload

#### Workflow starten

1. Navigieren Sie zu dem Kanal, für den Sie einen Kommentar hinzufügen möchten
1. Kanal auswählen
1. Öffnen Sie die Spalte Timeline .
1. Klicken Sie auf die Schaltfläche (drei Punkte) neben dem Kommentarfeld unten.

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline10.jpg)

1. Workflow starten
1. Der Assistent Workflow erstellen wird geöffnet, um die Workflow-Details anzugeben.
1. Wählen Sie Workflow-Modell aus der Dropdown-Liste aus und geben Sie den Workflow-Titel ein

   ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline11.jpg)

1. Fahren Sie fort, indem Sie auf Weiter klicken.
1. Im Schritt zum Umfang können Sie
* Inhalt hinzufügen , um zusätzliche Ressourcen zum Workflow hinzuzufügen
* Untergeordnete Elemente einschließen , um anzugeben, dass untergeordnete Elemente dieser Ressource im Workflow enthalten sind
* Auswahl entfernen , um diese Ressource aus dem Workflow zu entfernen

  ![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline12.jpg)

1. Verwenden Sie Erstellen , um den Assistenten zu schließen und die Workflow-Instanz zu erstellen
1. Je nach ausgewähltem Workflow-Modell müssen Sie eventuell einige zusätzliche Aktionen ausführen, um den Workflow abzuschließen.

![Workflow starten](/help/screens-cloud/assets/configure/screens-timeline13.jpg)
