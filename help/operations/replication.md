---
title: Replikation
description: Verteilung und Fehlerbehebung bei der Replikation.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 48%

---

# Replikation {#replication}

Adobe Experience Manager as a Cloud Service verwendet die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) Möglichkeit, den zu replizierenden Inhalt in einen Pipeline-Dienst zu verschieben, der auf Adobe Developer außerhalb der AEM ausgeführt wird.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Distribution](/help/overview/architecture.md#content-distribution).

## Methoden zum Veröffentlichen von Inhalten {#methods-of-publishing-content}

>[!NOTE]
>
>Wenn Sie an Massenveröffentlichungen von Inhalten interessiert sind, verwenden Sie die [Arbeitsablauf der Inhaltsstruktur veröffentlichen](#publish-content-tree-workflow).
>Dieser Workflow-Schritt wurde speziell für den Cloud Service entwickelt und kann große Payloads effizient verarbeiten.
>Es wird nicht empfohlen, eigenen benutzerdefinierten Code für die Massenveröffentlichung zu erstellen.
>Wenn Sie aus welchen Gründen auch immer anpassen müssen, können Sie diesen Workflow-/Workflow-Schritt mithilfe vorhandener Workflow-APIs Trigger haben.
>Es empfiehlt sich immer, nur Inhalte zu veröffentlichen, die veröffentlicht werden müssen. Achten Sie außerdem darauf, nicht zu versuchen, eine große Anzahl von Inhalten zu veröffentlichen, wenn dies nicht notwendig ist. Es gibt jedoch keine Beschränkungen dafür, wie viel Inhalt Sie über den Workflow zur Inhaltsstruktur veröffentlichen senden können.

### Schnelles Rückgängigmachen einer Veröffentlichung/Veröffentlichen – Geplantes Rückgängigmachen einer Veröffentlichung/Veröffentlichen {#publish-unpublish}

Mit dieser Funktion können Sie die ausgewählten Seiten sofort veröffentlichen, ohne die zusätzlichen Optionen zu nutzen, die über den Ansatz Veröffentlichung verwalten möglich sind.

Weitere Informationen finden Sie unter [Veröffentlichung verwalten](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Einschalt- und Ausschaltzeiten – Trigger-Konfiguration {#on-and-off-times-trigger-configuration}

Die zusätzlichen Möglichkeiten für **Einschaltzeit** und **Ausschaltzeit** sind auf der [Registerkarte „Standard“ der Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic) verfügbar.

Um die automatische Replikation für diese Funktion zu realisieren, aktivieren Sie **Automatische Replikation** im [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) **Ein-Aus-Trigger-Konfiguration**:

![OSGi-Ein-Aus-Trigger-Konfiguration](/help/operations/assets/replication-on-off-trigger.png)

### Veröffentlichung verwalten {#manage-publication}

Veröffentlichung verwalten bietet mehr Optionen als &quot;Quick Publish&quot;. Dies ermöglicht die Einbeziehung untergeordneter Seiten, die Anpassung der Verweise, den Start entsprechender Workflows und das Angebot der Option zur späteren Veröffentlichung.

Wenn Sie die untergeordneten Elemente eines Ordners für die Option &quot;Später veröffentlichen&quot;einbeziehen, wird der Workflow Inhaltsstruktur veröffentlichen aufgerufen, der in diesem Artikel beschrieben wird.

Ausführlichere Informationen zur Funktion „Veröffentlichung verwalten“ finden Sie in der [Dokumentation zu Veröffentlichungsgrundlagen](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Workflow zum Veröffentlichen der Inhaltsstruktur {#publish-content-tree-workflow}

Sie können eine Baumstruktur replizieren, indem Sie **Tools > Workflow > Modelle** auswählen und das vorkonfigurierte Workflow-Modell **Inhaltsstruktur veröffentlichen** kopieren, wie unten dargestellt:

![Die Workflow-Karte &quot;Inhaltsstruktur veröffentlichen&quot;](/help/operations/assets/publishcontenttreeworkflow.png)

Ändern Sie das Originalmodell nicht und rufen Sie es nicht auf. Kopieren Sie stattdessen unbedingt zuerst das Modell und ändern oder rufen Sie dann diese Kopie auf.

Wie alle Workflows kann es auch über eine API aufgerufen werden. Weitere Informationen finden Sie unter [Programmgesteuerte Interaktion mit Workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=de#extending-aem).

Alternativ können Sie ein Workflow-Modell erstellen, das die `Publish Content Tree` Prozessschritt:

1. Gehen Sie auf der Homepage von AEM as a Cloud Service zu **Tools > Workflow > Modelle**.
1. Drücken Sie auf der Seite &quot;Workflow-Modelle&quot;die **Erstellen** in der oberen rechten Ecke des Bildschirms.
1. Fügen Sie Ihrem Modell einen Titel und einen Namen hinzu. Weitere Informationen finden Sie unter [Erstellen von Workflow-Modellen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de)..
1. Wählen Sie das neu erstellte Modell aus der Liste aus und klicken Sie auf **Bearbeiten**.
1. Ziehen Sie im folgenden Fenster den Prozessschritt per Drag-and-Drop in den aktuellen Modellfluss:

   ![Prozessschritt](/help/operations/assets/processstep.png)

1. Wählen Sie den Prozessschritt im Fluss aus und wählen Sie **Konfigurieren** durch Drücken des Schraubenschlüsselsymbols.
1. Wählen Sie die **Prozess** Registerkarte und wählen Sie `Publish Content Tree` aus der Dropdown-Liste aus, und überprüfen Sie dann die **Handler-Modus** Kontrollkästchen

   ![Aktivieren der Braumstruktur](/help/operations/assets/newstep.png)

1. Legen Sie alle zusätzlichen Parameter im Feld **Argumente** fest. Mehrere kommagetrennte Argumente können zusammengefasst werden. Beispiel:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >Eine Liste der Parameter finden Sie unten im Abschnitt **Parameter**.

1. Klicken Sie auf **Fertig**, um das Workflow-Modell zu speichern.

**Parameter**

* `includeChildren` (boolescher Wert, Standard: `false`). Der Wert `false` bedeutet, dass nur der Pfad veröffentlicht wird; `true` bedeutet, dass auch Kinder veröffentlicht werden.
* `replicateAsParticipant` (boolescher Wert, Standard: `false`). Wenn als `true` konfiguriert, verwendet die Replikation die `userid` des Prinzipals, der den Teilnehmerschritt ausgeführt hat.
* `enableVersion` (boolescher Wert, Standard: `true`). Dieser Parameter bestimmt, ob bei der Replikation eine neue Version erstellt wird.
* `agentId` (Zeichenfolgenwert, Standard bedeutet, dass nur Agenten für die Veröffentlichung verwendet werden). Es wird empfohlen, die agentId explizit anzugeben. Legen Sie sie beispielsweise auf den Wert „publish“ fest. Festlegen des Agenten auf `preview` wird in den Vorschaudienst veröffentlicht.
* `filters` (Zeichenfolgenwert, Standard bedeutet, dass alle Pfade aktiviert sind). Verfügbare Werte sind:
   * `onlyActivated`: nur Seiten aktivieren, die bereits vorher aktiviert waren. Dies stellt eine Art von Reaktivierung dar.
   * `onlyModified` – Nur Pfade werden aktiviert, die bereits aktiviert sind und deren Änderungsdatum nach dem Aktivierungsdatum liegt.
   * Das obige kann als ODER mit einem senkrechten Strich („|“) angegeben werden. Beispiel: `onlyActivated|onlyModified`.

**Protokollierung**

Wenn der Workflow-Schritt für die Strukturaktivierung gestartet wird, werden die Konfigurationsparameter auf der INFO-Protokollebene protokolliert. Wenn Pfade aktiviert werden, wird auch eine INFO-Anweisung protokolliert.

Eine endgültige INFO-Anweisung wird protokolliert, nachdem der Workflow-Schritt alle Pfade repliziert hat.

Außerdem können Sie die Protokollierungsstufe unten erhöhen `com.day.cq.wcm.workflow.process.impl` zu DEBUG/TRACE , um weitere Protokollinformationen zu erhalten.

Wenn Fehler auftreten, wird der Workflow-Schritt mit einem `WorkflowException`, wodurch die zugrunde liegende Ausnahme umschlossen wird.

Im Folgenden finden Sie Beispiele für Protokolle, die während eines beispielhaften Workflows für die Struktur von Veröffentlichungsinhalten generiert werden:

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Fortsetzung der Unterstützung**

Der Workflow verarbeitet Inhalte in Blöcken, von denen jeder eine Teilmenge des zu veröffentlichenden vollständigen Inhalts darstellt. Wenn der Workflow vom System angehalten wird, wird der noch nicht verarbeitete Teil neu gestartet und verarbeitet. Eine Protokollanweisung gibt an, dass der Inhalt aus einem bestimmten Pfad wieder aufgenommen wurde.

### Replikations-API {#replication-api}

Sie können Inhalte mithilfe der Replikations-API veröffentlichen, die in AEM as a Cloud Service enthalten ist.

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

Beim Replizieren von Ressourcen werden wie im Beispiel oben nur die standardmäßig aktiven Agenten verwendet. as a Cloud Service bedeutet AEM nur den Agenten &quot;publish&quot;, der den Autor mit der Veröffentlichungsstufe verbindet.

Um die Vorschaufunktion zu unterstützen, wurde ein neuer Preview-Agent hinzugefügt, der standardmäßig nicht aktiv ist. Dieser Agent wird verwendet, um die Autoren- mit der Vorschauebene zu verbinden. Wenn Sie nur über den Vorschauagenten replizieren möchten, müssen Sie diesen Vorschauagenten explizit über einen `AgentFilter`.

Siehe folgendes Beispiel:

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

Der Gesamt-`ReplicationStatus` einer Ressource wird nur geändert, wenn die Replikationsaktion mindestens einen Agenten enthält, der standardmäßig aktiv ist. Im obigen Beispiel war dieser Fluss nicht der Fall. Die Replikation verwendete nur den Agenten &quot;Vorschau&quot;. Daher müssen Sie die neue `getStatusForAgent()` -Methode, die die Abfrage des Status für einen bestimmten Agenten ermöglicht. Diese Methode funktioniert auch für den Publish-Agenten. Gibt einen Wert zurück, der nicht null ist, wenn eine Replikationsaktion mit dem bereitgestellten Agenten durchgeführt wurde.

### Methoden zum Invalidieren von Inhalten {#invalidating-content}

Sie können Inhalte direkt ungültig machen, indem Sie entweder die Sling Content Invalidation (SCD) vom Autor (bevorzugte Methode) verwenden oder die Replikations-API verwenden, um den Replikationsagenten für das Leeren des Dispatchers aufzurufen. Siehe [Zwischenspeicherung](/help/implementing/dispatcher/caching.md) für weitere Details.

**Kapazitätsbeschränkungen der Replikations-API**

Replizieren Sie weniger als 100 Pfade gleichzeitig, wobei 500 die Grenze ist. Oberhalb der Grenze wird ein `ReplicationException` geworfen wird.
Wenn Ihre Anwendungslogik keine atomare Replikation erfordert, kann diese Grenze durch Festlegen der `ReplicationOptions.setUseAtomicCalls` auf &quot;false&quot;, was eine beliebige Anzahl von Pfaden akzeptiert, aber intern Behälter erstellt, die unterhalb dieses Limits bleiben.

Die Größe des pro Replikationsaufruf gesendeten Inhalts darf nicht größer sein als `10 MB`. Diese Regel enthält die Knoten und Eigenschaften, jedoch keine Binärdateien (Workflow-Pakete und Inhaltspakete werden als Binärdateien betrachtet).


## Fehlerbehebung {#troubleshooting}

Um Fehler bei der Replikation zu beheben, navigieren Sie zu den Replikationswarteschlangen in der Web-Benutzeroberfläche des AEM-Autoren-Service:

1. Navigieren Sie im AEM Startmenü zu **Tools > Bereitstellung > Verteilung**
2. Wählen Sie die Karte **Veröffentlichen** aus.
   ![Status](assets/publish-status.png "Status")
3. Überprüfen des Warteschlangenstatus, der grün sein sollte.
4. Sie können die Verbindung zum Replikations-Service testen.
5. Wählen Sie die Registerkarte **Protokolle** aus, auf der der Verlauf der Inhaltsveröffentlichungen angezeigt wird.

![Protokolle](assets/publish-logs.png "Protokolle")

Wenn der Inhalt nicht veröffentlicht werden konnte, wird die gesamte Veröffentlichung vom AEM-Veröffentlichungs-Service zurückgesetzt.
In diesem Fall zeigt die bearbeitbare Hauptwarteschlange einen roten Status an und sollte überprüft werden, um festzustellen, welche Elemente den Abbruch der Veröffentlichung verursacht haben. Durch Klicken auf diese Warteschlange werden die ausstehenden Elemente angezeigt, von denen aus ein einzelnes Element oder alle Elemente bei Bedarf gelöscht werden können.
