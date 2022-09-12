---
title: Replikation
description: Replikation von Verteilung und Problembehandlung.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: 30428716603a53f3a549a18541de593bbfe879df
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 87%

---

# Replikation {#replication}

Adobe Experience Manager as a Cloud Service verwendet die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html)-Funktion, um den zu replizierenden Inhalt in einen Pipeline-Service zu verschieben, der unter Adobe I/O außerhalb der AEM-Laufzeit ausgeführt wird.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Distribution](/help/overview/architecture.md#content-distribution).

## Methoden zum Veröffentlichen von Inhalten {#methods-of-publishing-content}

### Schnelles Rückgängigmachen einer Veröffentlichung/Veröffentlichen – Geplantes Rückgängigmachen einer Veröffentlichung/Veröffentlichen {#publish-unpublish}

Ermöglicht das sofortige Veröffentlichen ausgewählter Seiten, ohne die zusätzlichen Optionen wie bei der Verwendung der Funktion „Veröffentlichung verwalten“.

Weitere Informationen finden Sie unter [Veröffentlichung verwalten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Einschalt- und Ausschaltzeiten – Trigger-Konfiguration {#on-and-off-times-trigger-configuration}

Die zusätzlichen Möglichkeiten für **Einschaltzeit** und **Ausschaltzeit** sind auf der [Registerkarte „Standard“ der Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic) verfügbar.

Um die entsprechende automatische Replikation zu realisieren, müssen Sie die **automatische Replikation** in der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) **Ein-Aus-Trigger-Konfiguration** aktivieren:

![OSGi-Ein-Aus-Trigger-Konfiguration](/help/operations/assets/replication-on-off-trigger.png)

### Veröffentlichung verwalten {#manage-publication}

Veröffentlichung verwalten bietet mehr Optionen als „Quick Publish“. Mit dieser Funktion können Sie auch untergeordnete Seiten einschließen, Verweise anpassen, alle nötigen Workflows starten und bei Bedarf zu einem späteren Zeitpunkt veröffentlichen.

Wenn Sie die untergeordneten Elemente eines Ordners für die Option „Später veröffentlichen“ einbeziehen, wird der Workflow „Inhaltsstruktur veröffentlichen“ aufgerufen, der in diesem Artikel beschrieben wird.

Ausführlichere Informationen zur Funktion „Veröffentlichung verwalten“ finden Sie in der [Dokumentation zu Veröffentlichungsgrundlagen](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Workflow zum Veröffentlichen der Inhaltsstruktur {#publish-content-tree-workflow}

Sie können eine Baumstruktur replizieren, indem Sie **Tools > Workflow > Modelle** auswählen und das vorkonfigurierte Workflow-Modell **Inhaltsstruktur veröffentlichen** kopieren, wie unten dargestellt:

![](/help/operations/assets/publishcontenttreeworkflow.png)

Ändern Sie das Originalmodell nicht und rufen Sie es nicht auf. Kopieren Sie stattdessen unbedingt zuerst das Modell und ändern oder rufen Sie dann diese Kopie auf.

Wie alle Workflows kann es auch über eine API aufgerufen werden. Weitere Informationen finden Sie unter [Programmgesteuerte Interaktion mit Workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=de#extending-aem).

Alternativ können Sie dies auch erreichen, indem Sie ein Workflow-Modell erstellen, das den Prozessschritt `Publish Content Tree` verwendet:

1. Gehen Sie auf der Homepage von AEM as a Cloud Service zu **Tools > Workflow > Modelle**
1. Klicken Sie auf der Seite „Workflow-Modelle“ in der oberen rechten Ecke des Bildschirms auf **Erstellen**.
1. Fügen Sie Ihrem Modell einen Titel und einen Namen hinzu. Weitere Informationen finden Sie unter [Erstellen von Workflow-Modellen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de).
1. Wählen Sie das neu erstellte Modell aus der Liste aus und klicken Sie auf **Bearbeiten**.
1. Ziehen Sie im folgenden Fenster den Prozessschritt per Drag-and-Drop in den aktuellen Modellfluss:

   ![Prozessschritt](/help/operations/assets/processstep.png)

1. Klicken Sie auf den Prozessschritt im Fluss und wählen Sie **Konfigurieren** aus, indem Sie auf das Schraubenschlüsselsymbol klicken.
1. Klicken Sie auf die Registerkarte **Prozess** und wählen Sie `Publish Content Tree` aus der Dropdown-Liste aus.

   ![Aktivieren der Braumstruktur](/help/operations/assets/newstep.png)

1. Legen Sie alle zusätzlichen Parameter im Feld **Argumente** fest. Es können mehrere kommagetrennte Argumente kombiniert werden. Beispiel:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >Eine Liste der Parameter finden Sie unten im Abschnitt **Parameter**.

1. Klicken Sie auf **Fertig**, um das Workflow-Modell zu speichern.

**Parameter**

* `includeChildren` (boolescher Wert, Standard: `false`). „false“ bedeutet, dass nur der Pfad veröffentlicht wird. „true“ bedeutet, dass auch untergeordnete Elemente veröffentlicht werden.
* `replicateAsParticipant` (boolescher Wert, Standard: `false`). Wenn als `true` konfiguriert, verwendet die Replikation die `userid` des Prinzipals, der den Teilnehmerschritt ausgeführt hat.
* `enableVersion` (boolescher Wert, Standard: `true`). Dieser Parameter bestimmt, ob bei der Replikation eine neue Version erstellt wird.
* `agentId` (Zeichenfolgenwert, Standard bedeutet, dass nur Agenten für die Veröffentlichung verwendet werden). Es wird empfohlen, die agentId explizit anzugeben. Legen Sie sie beispielsweise auf den Wert „publish“ fest. Wird der Agent auf `preview` gesetzt, erfolgt die Veröffentlichung im Vorschaudienst.
* `filters` (Zeichenfolgenwert, Standard bedeutet, dass alle Pfade aktiviert sind). Verfügbare Werte sind:
   * `onlyActivated` - Nur Pfade, die als aktiviert markiert sind, werden aktiviert.
   * `onlyModified` – Nur Pfade werden aktiviert, die bereits aktiviert sind und deren Änderungsdatum nach dem Aktivierungsdatum liegt.
   * Das obige kann als ODER mit einem senkrechten Strich („|“) angegeben werden. Beispiel: `onlyActivated|onlyModified`.

**Protokollierung**

Wenn der Workflow-Schritt für die Aktivierung der Baumstruktur gestartet wird, werden die Konfigurationsparameter auf der INFO-Protokollebene protokolliert. Wenn Pfade aktiviert werden, wird auch eine INFO-Anweisung protokolliert.

Eine endgültige INFO-Anweisung wird dann protokolliert, nachdem der Workflow-Schritt alle Pfade repliziert hat.

Zusätzlich können Sie die Protokollebene der Logger unter `com.day.cq.wcm.workflow.process.impl` auf DEBUG/TRACE erhöhen, um weitere Protokollinformationen zu erhalten.

Bei Fehlern wird der Workflow-Schritt mit einem `WorkflowException` beendet, der die zugrunde liegende Ausnahme umschließt.

Nachfolgend finden Sie Beispiele für Protokolle, die während eines Beispiel-Workflows zum Veröffentlichen von Inhaltsstrukturen erzeugt werden:

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Fortsetzung der Unterstützung**

Der Workflow verarbeitet Inhalte in Blöcken, von denen jeder eine Teilmenge des zu veröffentlichenden vollständigen Inhalts darstellt. Wenn der Workflow aus irgendeinem Grund vom System angehalten wird, wird der noch nicht verarbeitete Block neu gestartet und verarbeitet. In einer Protokollanweisung wird angegeben, dass die Bearbeitung des Inhalts aus einem bestimmten Pfad wieder aufgenommen wurde.

### Replikations-API {#replication-api}

Sie können Inhalte mithilfe der Replikations-API veröffentlichen, die in AEM as a Cloud Service Funktionen enthalten ist.

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

Beim Replizieren von Ressourcen wie im Beispiel oben werden nur die standardmäßig aktiven Agenten verwendet. In AEM as a Cloud Service ist dies nur der Publish-Agent, der die Autoren- mit der Veröffentlichungsebene verbindet.

Um die Vorschaufunktion zu unterstützen, wurde ein neuer Preview-Agent hinzugefügt, der standardmäßig nicht aktiv ist. Dieser Agent wird verwendet, um die Autoren- mit der Vorschauebene zu verbinden. Wenn Sie nur über den Vorschauagenten replizieren möchten, müssen Sie diesen Vorschauagenten explizit über einen `AgentFilter` auswählen.

Im folgenden Beispiel erfahren Sie, wie Sie dazu vorgehen:

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

Wenn Sie keinen solchen Filter bereitstellen und nur den Publish-Agenten verwenden, wird der Preview-Agent nicht verwendet und die Replikationsaktion wirkt sich nicht auf die Vorschauebene aus.

Der Gesamt-`ReplicationStatus` einer Ressource wird nur geändert, wenn die Replikationsaktion mindestens einen Agenten enthält, der standardmäßig aktiv ist. Im obigen Beispiel ist dies nicht der Fall, da die Replikation nur den Preview-Agenten verwendet. Daher müssen Sie die neue `getStatusForAgent()`-Methode verwenden, mit der Sie den Status für einen bestimmten Agenten abfragen können. Diese Methode funktioniert auch für den Publish-Agenten. Gibt einen Wert zurück, der nicht null ist, wenn eine Replikationsaktion mit dem bereitgestellten Agenten durchgeführt wurde.

### Methoden zur Invalidierung von Inhalten {#invalidating-content}

Sie können Inhalte direkt ungültig machen, indem Sie entweder die Sling Content Invalidation (SCD) vom Autor (bevorzugte Methode) verwenden oder die Replikations-API verwenden, um den Replikationsagenten für das Leeren des Publish-Dispatchers aufzurufen. Siehe Abschnitt [Zwischenspeicherung](/help/implementing/dispatcher/caching.md) für weitere Details.

**Kapazitätsbeschränkungen der Replikations-API**

Es wird empfohlen, weniger als 100 Pfade gleichzeitig zu replizieren, wobei 500 die feste Grenze darstellen. Oberhalb der harten Grenze wird ein `ReplicationException` wird geworfen.
Wenn Ihre Anwendungslogik keine atomare Replikation erfordert, kann diese Grenze durch Festlegen der `ReplicationOptions.setUseAtomicCalls` auf &quot;false&quot;, was eine beliebige Anzahl von Pfaden akzeptiert, aber intern Behälter erstellt, die unterhalb dieser Grenze bleiben.

Die Größe des pro Replikationsaufruf gesendeten Inhalts darf nicht größer sein als `10 MB`. Dies umfasst die Knoten und Eigenschaften, jedoch keine Binärdateien (Workflow-Pakete und Inhaltspakete werden als Binärdateien betrachtet).


## Fehlerbehebung {#troubleshooting}

Um Fehler bei der Replikation zu beheben, navigieren Sie zu den Replikationswarteschlangen in der Web-Benutzeroberfläche des AEM-Autoren-Service:

1. Navigieren Sie im AEM-Startmenü zu **Tools > Bereitstellung > Distribution**.
2. Wählen Sie die Karte **Veröffentlichen** aus.
   ![Status](assets/publish-status.png "Status")
3. Überprüfen des Warteschlangenstatus, der grün sein sollte.
4. Sie können die Verbindung zum Replikations-Service testen.
5. Wählen Sie die Registerkarte **Protokolle** aus, auf der der Verlauf der Inhaltsveröffentlichungen angezeigt wird.

![Protokolle](assets/publish-logs.png "Protokolle")

Wenn der Inhalt nicht veröffentlicht werden konnte, wird die gesamte Veröffentlichung vom AEM-Veröffentlichungs-Service zurückgesetzt.
In diesem Fall zeigt die bearbeitbare Haupt-Warteschlange einen roten Status an und sollte überprüft werden, um festzustellen, welche Elemente den Abbruch der Veröffentlichung verursacht haben. Wenn Sie auf diese Warteschlange klicken, werden die ausstehenden Elemente angezeigt, die einzeln oder insgesamt gelöscht werden können.
