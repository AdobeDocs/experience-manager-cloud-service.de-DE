---
title: Replikation
description: Distribution  und Fehlerbehebung bei der Replikation.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
translation-type: tm+mt
source-git-commit: eb92c66f2b9e8e6ec859114da2de049747ec251e
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 39%

---

# Replikation {#replication}

Adobe Experience Manager as a Cloud Service verwendet die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html)-Funktion, um den zu replizierenden Inhalt in einen Pipeline-Service zu verschieben, der unter Adobe I/O außerhalb der AEM-Laufzeit ausgeführt wird.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Distribution](/help/core-concepts/architecture.md#content-distribution).

## Methoden zum Veröffentlichen von Inhalten {#methods-of-publishing-content}

### Schnelles Rückgängigmachen einer Veröffentlichung/Veröffentlichen – Geplantes Rückgängigmachen einer Veröffentlichung/Veröffentlichen {#publish-unpublish}

Diese Standard-AEM-Funktionen für Autoren ändern sich mit AEM Cloud Service nicht.

### Einschalt- und Ausschaltzeiten – Trigger-Konfiguration {#on-and-off-times-trigger-configuration}

Die zusätzlichen Möglichkeiten für **Einschaltzeit** und **Ausschaltzeit** sind auf der [Registerkarte „Standard“ der Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic) verfügbar.

Um die entsprechende automatische Replikation zu realisieren, müssen Sie die **automatische Replikation** in der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) **Ein-Aus-Trigger-Konfiguration** aktivieren:

![OSGi-Ein-Aus-Trigger-Konfiguration](/help/operations/assets/replication-on-off-trigger.png)

### Aktivieren eines Baumes {#tree-activation}

Aktivieren eines Baumes:

1. Navigieren Sie im AEM-Startmenü zu **Tools > Bereitstellung > Distribution**.
2. Wählen Sie die Karte **forwardPublisher** aus.
3. Wählen Sie in der Benutzeroberfläche der forwardPublisher-Web-Konsole **Verteilen** aus.

   ![Verteilen](assets/distribute.png "Verteilen")
4. Wählen Sie den Pfad im Pfad-Browser aus, wählen Sie aus, einen Knoten oder Baum hinzuzufügen oder zu löschen, und wählen Sie **Senden** aus.

### Content Tree-Arbeitsablauf veröffentlichen {#publish-content-tree-workflow}

Sie können eine Strukturreplikation durch Auswahl von **Tools - Workflow - Models** und Kopieren des Out-of-the-Box-Workflow-Modells **Content-Struktur veröffentlichen** wie unten dargestellt Trigger ausführen:

![](/help/operations/assets/publishcontenttreeworkflow.png)

Ändern Sie das Originalmodell nicht oder rufen Sie es nicht auf. Stellen Sie stattdessen sicher, dass Sie das Modell zuerst kopieren und dann ändern oder aufrufen.

Wie alle Workflows kann sie auch über die API aufgerufen werden. Weitere Informationen finden Sie unter [Programmatische Interaktion mit Workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=en#extending-aem).

Alternativ können Sie dies auch durch Erstellen eines Workflow-Modells erreichen, das den Prozessschritt `Publish Content Tree` verwendet:

1. Gehen Sie auf der AEM als Cloud Service-Homepage zu **Tools - Workflow - Modelle**
1. Klicken Sie auf der Seite &quot;Workflow-Modelle&quot;in der oberen rechten Ecke des Bildschirms auf **Create**
1. hinzufügen Sie Ihrem Modell einen Titel und einen Namen. Weitere Informationen finden Sie unter [Erstellen von Workflow-Modellen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)
1. Wählen Sie das neu erstellte Modell aus der Liste und drücken Sie die Taste **Bearbeiten**
1. Ziehen Sie im folgenden Fenster den Prozessschritt in den aktuellen Modellfluss:

   ![Prozessschritt](/help/operations/assets/processstep.png)

1. Klicken Sie auf den Prozessschritt im Fluss und wählen Sie **Konfigurieren**, indem Sie auf das Schraubenschlüsselsymbol klicken
1. Klicken Sie auf die Registerkarte **Process** und wählen Sie `Publish Content Tree` aus der Dropdown-Liste

   ![Treaktivierung](/help/operations/assets/newstep.png)

1. Legen Sie weitere Parameter im Feld **Argumente** fest. Es können mehrere kommagetrennte Argumente miteinander verbunden werden. Beispiel:

   `enableVersion=true,agentId=publish`


   >[!NOTE]
   >
   >Die Liste der Parameter finden Sie im Abschnitt **Parameter**.

1. Drücken Sie **Fertig**, um das Workflow-Modell zu speichern.

**Parameter**

* `replicateAsParticipant` (boolescher Wert, Standard:  `false`). Bei der Konfiguration als `true` verwendet die Replizierung das `userid` des Prinzips, das den Schritt des Teilnehmers ausgeführt hat.
* `enableVersion` (boolescher Wert, Standard:  `true`). Dieser Parameter bestimmt, ob bei der Replikation eine neue Version erstellt wird.
* `agentId` (Zeichenfolgenwert, Standard bedeutet, dass alle aktivierten Agenten verwendet werden).
* `filters` (Zeichenfolgenwert, Standard bedeutet, dass alle Pfade aktiviert sind). Verfügbare Werte sind:
   * `onlyActivated` - Es werden nur Pfade aktiviert, die nicht als aktiviert markiert sind.
   * `onlyModified` - Aktivieren Sie nur Pfade, die bereits aktiviert sind und deren Änderungsdatum nach dem Datum der Aktivierung liegt.
   * Die obige kann mit einem senkrechten Strich (|) versehen werden. Beispiel: `onlyActivated|onlyModified`.

**Protokollierung**

Wenn der Arbeitsablaufschritt der drei Aktivierungen Beginn, protokolliert er seine Konfigurationsparameter auf der INFO-Protokollierungsebene. Wenn Pfade aktiviert werden, wird auch eine INFO-Anweisung protokolliert.

Eine endgültige INFO-Anweisung wird dann protokolliert, nachdem der Workflow-Schritt alle Pfade repliziert hat.

Zusätzlich können Sie die Loglevel der Logger unter `com.day.cq.wcm.workflow.process.impl` auf DEBUG/TRACE erhöhen, um weitere Protokollinformationen zu erhalten.

Bei Fehlern endet der Workflow-Schritt mit einem `WorkflowException`, wodurch die zugrunde liegende Ausnahme umgebrochen wird.

Nachstehend finden Sie Beispiele für Protokolle, die während eines Arbeitsablaufs mit einer Struktur zum Veröffentlichen von Inhalten generiert wurden:

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Unterstützung für die Fortsetzung der Migration**

Der Workflow verarbeitet Inhalte in Textbausteinen, von denen jede eine Untergruppe des zu veröffentlichenden vollständigen Inhalts darstellt. Wenn der Workflow aus irgendeinem Grund vom System beendet wird, wird der noch nicht verarbeitete Stapel neu gestartet und verarbeitet. In einer Protokollanweisung wird angegeben, dass der Inhalt aus einem bestimmten Pfad wiederaufgenommen wurde.

## Fehlerbehebung {#troubleshooting}

Um Fehler bei der Replikation zu beheben, navigieren Sie zu den Replikationswarteschlangen in der Web-Benutzeroberfläche des AEM-Autoren-Service:

1. Navigieren Sie im AEM-Startmenü zu **Tools > Bereitstellung > Distribution**.
2. Wählen Sie die Karte **forwardPublisher** aus.
   ![Status](assets/status.png "Status")
3. Überprüfen des Warteschlangenstatus, der grün sein sollte.
4. Sie können die Verbindung zum Replikations-Service testen.
5. Wählen Sie die Registerkarte **Protokolle** aus, auf der der Verlauf der Inhaltsveröffentlichungen angezeigt wird.

![Protokolle](assets/logs.png "Protokolle")

Wenn der Inhalt nicht veröffentlicht werden konnte, wird die gesamte Veröffentlichung vom AEM-Veröffentlichungs-Service zurückgesetzt.
In diesem Fall sollten die Warteschlangen überprüft werden, um festzustellen, welche Elemente den Abbruch der Veröffentlichung verursacht haben. Wenn Sie auf eine Warteschlange mit rotem Status klicken, wird die Warteschlange mit ausstehenden Elementen angezeigt, von der aus einzelne oder alle Elemente bei Bedarf gelöscht werden können.
