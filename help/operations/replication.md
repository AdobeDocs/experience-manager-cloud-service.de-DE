---
title: Replikation
description: Verteilung und Fehlerbehebung der Replikation.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: 3cafd809cba2d844ee4507c41eb1b5302ad5b6ba
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 28%

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

### Arbeitsablauf der Inhaltsstruktur veröffentlichen {#publish-content-tree-workflow}

Sie können eine Baumstruktur replizieren, indem Sie **Tools - Workflow - Modelle** auswählen und das vordefinierte Workflow-Modell **Inhaltsstruktur veröffentlichen** kopieren, wie unten dargestellt:

![](/help/operations/assets/publishcontenttreeworkflow.png)

Ändern Sie das Originalmodell nicht oder rufen Sie es auf. Stellen Sie stattdessen sicher, dass Sie das Modell zuerst kopieren und dann ändern oder aufrufen.

Wie alle Workflows kann sie auch über API aufgerufen werden. Weitere Informationen finden Sie unter [Programmgesteuerte Interaktion mit Workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=en#extending-aem).

Alternativ können Sie dies auch erreichen, indem Sie ein Workflow-Modell erstellen, das den Prozessschritt `Publish Content Tree` verwendet:

1. Gehen Sie auf der AEM as a Cloud Service-Homepage zu **Tools - Workflow - Modelle**
1. Klicken Sie auf der Seite &quot;Workflow-Modelle&quot;in der oberen rechten Ecke des Bildschirms auf **Erstellen** .
1. Fügen Sie Ihrem Modell einen Titel und einen Namen hinzu. Weitere Informationen finden Sie unter [Erstellen von Workflow-Modellen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)
1. Wählen Sie das neu erstellte Modell aus der Liste aus und drücken Sie **Bearbeiten**
1. Ziehen Sie im folgenden Fenster den Prozessschritt in den aktuellen Modellfluss:

   ![Prozessschritt](/help/operations/assets/processstep.png)

1. Klicken Sie auf den Prozessschritt im Fluss und wählen Sie **Konfigurieren** aus, indem Sie auf das Schraubenschlüsselsymbol drücken
1. Klicken Sie auf die Registerkarte **Prozess** und wählen Sie `Publish Content Tree` aus der Dropdown-Liste aus.

   ![Treeactivation](/help/operations/assets/newstep.png)

1. Legen Sie alle zusätzlichen Parameter im Feld **Argumente** fest. Es können mehrere kommagetrennte Argumente kombiniert werden. Beispiel:

   `enableVersion=true,agentId=publish`


   >[!NOTE]
   >
   >Eine Liste der Parameter finden Sie unten im Abschnitt **Parameter** .

1. Drücken Sie **Fertig**, um das Workflow-Modell zu speichern.

**Parameter**

* `replicateAsParticipant` (boolescher Wert, Standard:  `false`). Wenn als `true` konfiguriert, verwendet die Replikation die `userid` des Prinzipals, der den Teilnehmerschritt ausgeführt hat.
* `enableVersion` (boolescher Wert, Standard:  `true`). Dieser Parameter bestimmt, ob bei der Replikation eine neue Version erstellt wird.
* `agentId` (Zeichenfolgenwert, Standard bedeutet, dass nur Agenten für die Veröffentlichung verwendet werden). Es wird empfohlen, explizit über die agentId zu sein. Legen Sie ihn beispielsweise auf den Wert fest: veröffentlichen. Wird der Agent auf `preview` gesetzt, wird er im Vorschaudienst veröffentlicht
* `filters` (Zeichenfolgenwert, Standard bedeutet, dass alle Pfade aktiviert sind). Verfügbare Werte sind:
   * `onlyActivated` - Nur Pfade, die nicht als aktiviert markiert sind, werden aktiviert.
   * `onlyModified` - Nur Pfade aktivieren, die bereits aktiviert sind und deren Änderungsdatum nach dem Aktivierungsdatum liegt.
   * Das obige kann ODER mit einem senkrechten Strich (&quot;|&quot;) angegeben werden. Beispiel: `onlyActivated|onlyModified`.

**Protokollierung**

Wenn der Workflow-Schritt für die Strukturaktivierung gestartet wird, werden die Konfigurationsparameter auf der INFO-Protokollebene protokolliert. Wenn Pfade aktiviert werden, wird auch eine INFO-Anweisung protokolliert.

Eine endgültige INFO-Anweisung wird dann protokolliert, nachdem der Workflow-Schritt alle Pfade repliziert hat.

Zusätzlich können Sie die Loglevel der Logger unter `com.day.cq.wcm.workflow.process.impl` auf DEBUG/TRACE erhöhen, um weitere Protokollinformationen zu erhalten.

Bei Fehlern wird der Workflow-Schritt mit einem `WorkflowException` beendet, der die zugrunde liegende Ausnahme umbricht.

Nachfolgend finden Sie Beispiele für Protokolle, die während eines Workflows mit einer Inhaltsstruktur für die Beispielveröffentlichung generiert werden:

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Unterstützung für die Fortsetzung der Migration**

Der Workflow verarbeitet Inhalte in Teilen, von denen jeder eine Teilmenge des zu veröffentlichenden vollständigen Inhalts darstellt. Wenn der Workflow aus irgendeinem Grund vom System angehalten wird, wird der noch nicht verarbeitete Block neu gestartet und verarbeitet. In einer Protokollanweisung wird angegeben, dass der Inhalt aus einem bestimmten Pfad wieder aufgenommen wurde.

### Replikations-API {#replication-api}

Sie können Inhalte mithilfe der Replcation API veröffentlichen, die in AEM als Cloud Service enthalten ist.

Weitere Informationen finden Sie in der [API-Dokumentation](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html).

**Grundlegende Verwendung der API**

```
@Reference
Replicator replicator;
@Reference
ReplicationStatusProvider replicationStatusProvider;

....
Session session = ...
// Activate a single page to all agents, which are active by default
replicator.replicate(session,ReplicationActionType.ACTIVATE,"/content/we-retail/en");
// Activate multiple pages (but try to limit it to approx 100 at max)
replicator.replicate(session,ReplicationActionType.ACTIVATE, new String[]{"/content/we-retail/en","/content/we-retail/de"});

// ways to get the replication status
Resource enResource = resourceResolver.getResource("/content/we-retail/en");
Resource deResource = resourceResolver.getResource("/content/we-retail/de");
ReplicationStatus enStatus = enResource.adaptTo(ReplicationStatus.class);
// if you need to get the status for more more than 1 resource at once, this approach is more performant
Map<String,ReplicationStatus> allStatus = replicationStatusProvider.getBatchReplicationStatus(enResource,deResource);
```

**Replikation mit bestimmten Agenten**

Beim Replizieren von Ressourcen wie im Beispiel oben werden nur die standardmäßig aktiven Agenten verwendet. In AEM als Cloud Service ist dies nur der Agent &quot;publish&quot;, der den Autor mit der Veröffentlichungsstufe verbindet.

Um die Vorschaufunktion zu unterstützen, wurde ein neuer Agent namens &quot;Vorschau&quot;hinzugefügt, der standardmäßig nicht aktiv ist. Dieser Agent wird verwendet, um den Autor mit der Vorschauebene zu verbinden. Wenn Sie nur über den Vorschauagenten replizieren möchten, müssen Sie diesen Vorschauagenten explizit über einen `AgentFilter` auswählen.

Im folgenden Beispiel erfahren Sie, wie Sie dies durchführen:

```
private static final String PREVIEW_AGENT = "preview";

ReplicationStatus beforeStatus = enResource.adaptTo(ReplicationStatus.class); // beforeStatus.isActivated == false

ReplicationOptions options = new ReplicationOptions();
options.setFilter(new AgentFilter() {
  @Override
  public boolean isIncluded (Agent agent) {
    return agent.getId().equals(PREVIEW_AGENT);
  }
});
// will replicate only to preview
replicator.replicate(session,ReplicationActionType.ACTIVATE,"/content/we-retail/en", options);

ReplicationStatus afterStatus = enResource.adaptTo(ReplicationStatus.class); // afterStatus.isActivated == false
ReplicationStatus previewStatus = afterStatus.getStatusForAgent(PREVIEW_AGENT); // previewStatus.isActivated == true
```

Wenn Sie einen solchen Filter nicht bereitstellen und nur den Agenten &quot;publish&quot;verwenden, wird der Agent &quot;preview&quot;nicht verwendet und die Replikationsaktion wirkt sich nicht auf die Vorschauebene aus.

Die Gesamtsumme `ReplicationStatus` einer Ressource wird nur geändert, wenn die Replikationsaktion mindestens einen Agenten enthält, der standardmäßig aktiv ist. Im obigen Beispiel ist dies nicht der Fall, da die Replikation nur den Agenten &quot;preview&quot;verwendet. Daher müssen Sie die neue `getStatusForAgent()`-Methode verwenden, mit der Sie den Status für einen bestimmten Agenten abfragen können. Diese Methode funktioniert auch für den Agenten &quot;publish&quot;. Gibt einen Wert zurück, der nicht null ist, wenn eine Replikationsaktion mit dem bereitgestellten Agenten durchgeführt wurde.

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
