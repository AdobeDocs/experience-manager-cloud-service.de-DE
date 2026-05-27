---
title: Workflows für die Strukturreplikation in AEM as a Cloud Service
description: Erfahren Sie, wie Sie tiefe Inhaltshierarchien mithilfe des Workflow-Schritts zur Baumstrukturaktivierung und der zugehörigen Workflows in AEM as a Cloud Service replizieren.
feature: Operations
role: Admin
source-git-commit: d6555eebfa13a400f084ef4edefb92b4471adcac
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 82%

---

# Workflows für die Strukturreplikation in AEM as a Cloud Service {#tree-replication-workflows}

Wenn Sie einen großen Zweig der Inhaltsstruktur veröffentlichen müssen, kann die standardmäßige seitenweise Veröffentlichung langsam und ressourcenintensiv sein. AEM as a Cloud Service bietet Workflow-basierte Ansätze, mit denen tiefe Inhaltshierarchien in verwaltbaren Blöcken repliziert, die bei ausgelasteten Replikationswarteschlangen angehalten und bei Unterbrechung fortgesetzt werden können.

Verwenden Sie den **Workflow-Schritt für die Aktivierung der Baumstruktur** für die Massenreplikation der Baumstruktur. Dies ist der empfohlene Ansatz für große Payloads. Der **Workflow „Inhaltsstruktur veröffentlichen** bleibt zur Referenz dokumentiert, wird jedoch zugunsten des Schritts „Baumstrukturaktivierung“ eingestellt.

Weitere Replikationsthemen finden Sie unter [Replikation](/help/operations/replication.md).

## Workflow-Schritt für die Strukturaktivierung {#tree-activation}

Der Workflow-Schritt für die Aktivierung der Baumstruktur soll eine tiefe Hierarchie von Inhaltsknoten dynamisch replizieren. Er wird automatisch angehalten, wenn die Warteschlange zu groß wird, damit andere Replikationen parallel mit minimaler Latenz fortgesetzt werden können.

So erstellen Sie ein Workflow-Modell, das den Prozessschritt `TreeActivation` verwendet:

1. Gehen Sie auf der Homepage von AEM as a Cloud Service zu **Tools > Workflow > Modelle**.
1. Klicken Sie auf der Seite „Workflow-Modelle“ in der oberen rechten Ecke des Bildschirms auf **Erstellen**.
1. Fügen Sie Ihrem Modell einen Titel und einen Namen hinzu. Weitere Informationen finden Sie unter [Erstellen von Workflow-Modellen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de).
1. Wählen Sie das neu erstellte Modell aus der Liste aus und klicken Sie auf **Bearbeiten**
1. Löschen Sie im folgenden Fenster den standardmäßig angezeigten Schritt
1. Ziehen Sie den Prozessschritt per Drag-and-Drop in den aktuellen Modellfluss:

   ![Prozessschritt](/help/operations/assets/processstep.png)

1. Klicken Sie auf den Prozessschritt im Fluss und wählen Sie **Konfigurieren** aus, indem Sie auf das Schraubenschlüsselsymbol klicken.
1. Wählen Sie die Registerkarte **Prozess** und wählen Sie `Publish Content Tree` aus der Dropdown-Liste aus; aktivieren Sie dann das Kontrollkästchen **Handler-Modus**

   ![Aktivieren der Braumstruktur](/help/operations/assets/new-treeactivationstep.png)

1. Legen Sie alle zusätzlichen Parameter im Feld **Argumente** fest. Mehrere kommagetrennte Argumente können zusammengefügt werden. Beispiel:

   `enableVersion=false,agentId=publish,chunkSize=50,maxTreeSize=500000,dryRun=false,filters=onlyModified,maxQueueSize=10`

   >[!NOTE]
   >
   >Eine Liste der Parameter finden Sie unten im Abschnitt **Parameter**.

1. Klicken Sie auf **Fertig**, um das Workflow-Modell zu speichern.

**Parameter**

| Name | default | Beschreibung |
| -------------- | ------- | --------------------------------------------------------------- |
| path |         | Der Stammpfad zum Starten |
| agentId | publish | Agent, der die Replikation erhält (`publish` oder `preview`) |
| chunkSize | 50 | Die Anzahl der Pfade, die in einer einzelnen Replikation gebündelt werden sollen |
| maxTreeSize | 500000 | Die maximale Anzahl von Knoten, damit eine Baumstruktur als klein gilt |
| maxQueueSize | 10 | Die maximale Anzahl von Elementen in der Replikationswarteschlange |
| enableVersion | false | Aktivierung der Versionierung |
| dryRun | false | Bei Festlegung auf „true“ wird die Replikation nicht tatsächlich aufgerufen. |
| userId |         | Nur für den Auftrag. Beim Workflow wird die Person verwendet, die den Workflow aufruft |
| filters |         | Liste mit den Namen der Knotenfilter. Siehe unterstützte Filter unten |

**Unterstützte Filter**

| Name | Beschreibung |
| ------------- | ------------------------------------------- |
| onlyModified | Knoten: sowohl neue als auch bereits vorhandene, die seit der letzten Veröffentlichung geändert wurden. |
| onlyActivated | Knoten: die vor der letzten Veröffentlichung veröffentlicht wurden. |


**Fortsetzung der Unterstützung**

Der Workflow verarbeitet Inhalte in Blöcken, von denen jeder eine Teilmenge des vollständigen zu veröffentlichenden Inhalts darstellt.  Wenn der Workflow vom System angehalten wird, wird er dort fortgesetzt, wo er abgebrochen wurde.

**Überwachen des Workflow-Fortschritts**

1. Gehen Sie auf der Startseite von AEM as a Cloud Service zu **Tools > Allgemein > Aufträge**.
1. Sehen Sie sich die Zeile an, die Ihrem Workflow entspricht. Die Spalte *Fortschritt* gibt an, wie die Replikation voranschreitet. Beispielsweise kann dort „41/564“ und nach der Aktualisierung „52/564“ angezeigt werden.

   ![Treeactivation-Fortschritt](/help/operations/assets/treeactivation-progress.png)


1. Wenn Sie die Zeile auswählen und öffnen, erhalten Sie weitere Details zum Status der Workflow-Ausführung.

   ![Details zum Treeactivation-Status](/help/operations/assets/treeactivation-progress-details.png)



## Workflow zum Veröffentlichen der Inhaltsstruktur {#publish-content-tree-workflow}

>[!NOTE]
>
>Diese Funktion wurde zugunsten des leistungsfähigeren Schritts zur Strukturaktivierung aufgegeben, der in einen benutzerdefinierten Workflow eingeschlossen werden kann.

+++ Klicken Sie hier, um mehr über diese nicht mehr unterstützte Funktion zu erfahren.

Sie können eine Baumstruktur replizieren, indem Sie **Tools > Workflow > Modelle** auswählen und das vorkonfigurierte Workflow-Modell **Inhaltsstruktur veröffentlichen** kopieren, wie unten dargestellt:

![Die Workflow-Karte für die Veröffentlichung der Inhaltsstruktur](/help/operations/assets/publishcontenttreeworkflow.png)

Rufen Sie das Originalmodell nicht auf. Kopieren Sie stattdessen unbedingt zuerst das Modell und rufen Sie dann diese Kopie auf.

Wie alle Workflows kann es auch über eine API aufgerufen werden. Weitere Informationen finden Sie unter [Programmgesteuerte Interaktion mit Workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=de#extending-aem).

Alternativ können Sie auch ein Workflow-Modell erstellen, das den Prozessschritt `Publish Content Tree` verwendet.

1. Gehen Sie auf der Homepage von AEM as a Cloud Service zu **Tools > Workflow > Modelle**.
1. Klicken Sie auf der Seite „Workflow-Modelle“ in der oberen rechten Ecke des Bildschirms auf **Erstellen**.
1. Fügen Sie Ihrem Modell einen Titel und einen Namen hinzu. Weitere Informationen finden Sie unter [Erstellen von Workflow-Modellen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de).
1. Wählen Sie das neu erstellte Modell aus der Liste aus und klicken Sie auf **Bearbeiten**
1. Ziehen Sie im folgenden Fenster den Prozessschritt per Drag-and-Drop in den aktuellen Modellfluss:

   ![Prozessschritt](/help/operations/assets/processstep.png)

1. Klicken Sie auf den Prozessschritt im Fluss und wählen Sie **Konfigurieren** aus, indem Sie auf das Schraubenschlüsselsymbol klicken.
1. Wählen Sie die Registerkarte **Prozess** und wählen Sie `Publish Content Tree` aus der Dropdown-Liste aus; aktivieren Sie dann das Kontrollkästchen **Handler-Modus**

   ![Aktivieren der Braumstruktur](/help/operations/assets/newstep.png)

1. Legen Sie alle zusätzlichen Parameter im Feld **Argumente** fest. Mehrere kommagetrennte Argumente können zusammengefügt werden. Beispiel:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >Eine Liste der Parameter finden Sie unten im Abschnitt **Parameter**.

1. Klicken Sie auf **Fertig**, um das Workflow-Modell zu speichern.

**Parameter**

* `includeChildren` (boolescher Wert, Standard: `false`). Der Wert `false` bedeutet, dass nur der Pfad veröffentlicht wird, während `true` bedeutet, dass auch untergeordnete Elemente veröffentlicht werden.
* `replicateAsParticipant` (boolescher Wert, Standard: `false`). Wenn als `true` konfiguriert, verwendet die Replikation die `userid` des Prinzipals, der den Teilnehmerschritt ausgeführt hat.
* `enableVersion` (boolescher Wert, Standard: `false`). Dieser Parameter bestimmt, ob bei der Replikation eine neue Version erstellt wird.
* `agentId` (Zeichenfolgenwert, Standard bedeutet, dass nur Agenten für die Veröffentlichung verwendet werden). Geben Sie den Zielagenten explizit an, z. B. `publish` für die Live-Veröffentlichungsebene oder `preview` für die Vorschauebene.
* `filters` (Zeichenfolgenwert, Standard bedeutet, dass alle Pfade aktiviert sind). Verfügbare Werte sind:
   * `onlyActivated`: nur Seiten aktivieren, die bereits vorher aktiviert waren. Dies stellt eine Art von Reaktivierung dar.
   * `onlyModified` – Nur Pfade werden aktiviert, die bereits aktiviert sind und deren Änderungsdatum nach dem Aktivierungsdatum liegt.
   * Das obige kann als ODER mit einem senkrechten Strich („|“) angegeben werden. Beispiel: `onlyActivated|onlyModified`.

**Protokollierung**

Wenn der Workflow-Schritt für die Aktivierung der Baumstruktur gestartet wird, werden die Konfigurationsparameter auf der INFO-Protokollebene protokolliert. Wenn Pfade aktiviert werden, wird auch eine INFO-Anweisung protokolliert.

Eine endgültige INFO-Anweisung wird dann protokolliert, nachdem der Workflow-Schritt alle Pfade repliziert hat.

Zusätzlich können Sie die Protokollebene der Logger unter `com.day.cq.wcm.workflow.process.impl` auf DEBUG/TRACE erhöhen, um weitere Protokollinformationen zu erhalten.

Bei Fehlern wird der Workflow-Schritt mit einer `WorkflowException` beendet, welche die zugrunde liegende Ausnahme umschließt.

Nachfolgend finden Sie Beispiele für Protokolle, die während eines Beispiel-Workflows zum Veröffentlichen von Inhaltsstrukturen erzeugt werden:

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

+++
