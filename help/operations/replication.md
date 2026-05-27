---
title: Replikation
description: Erfahren Sie mehr über die Verteilung und Fehlerbehebung bei der Replikation in AEM as a Cloud Service.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
feature: Operations
role: Admin
source-git-commit: d6555eebfa13a400f084ef4edefb92b4471adcac
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 43%

---

# Replikation {#replication}

Adobe Experience Manager as a Cloud Service verwendet die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html)-Funktion, um den zu replizierenden Inhalt in einen Pipeline-Dienst zu verschieben, der unter Adobe Developer außerhalb der AEM-Laufzeit ausgeführt wird.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Verteilung](/help/overview/architecture.md#content-distribution).

## Methoden zum Veröffentlichen von Inhalten {#methods-of-publishing-content}

>[!NOTE]
>
>Wenn Sie an Massenveröffentlichungen von Inhalten interessiert sind, erstellen Sie einen Workflow mit dem [Workflow-Schritt für die Strukturaktivierung](/help/operations/tree-replication-workflows.md#tree-activation), der eine effiziente Verarbeitung umfangreicher Payloads ermöglicht.
>Es wird nicht empfohlen, für die Massenveröffentlichung Ihren eigenen, benutzerdefinierten Code zu erstellen.
>Wenn Sie aus irgendeinem Grund Anpassungen vornehmen müssen, können Sie mit diesem Schritt einen Workflow über vorhandene Workflow-APIs auslösen.
>Es empfiehlt sich immer, nur Inhalte zu veröffentlichen, die auch veröffentlicht werden müssen. Achten Sie außerdem darauf, nicht zu versuchen, eine große Anzahl von Inhalten zu veröffentlichen, wenn dies nicht notwendig ist. Es gibt jedoch keine Beschränkungen hinsichtlich der Menge der Inhalte, die Sie über Workflows mit dem Workflow-Schritt für die Strukturaktivierung senden können.

### Schnelles Rückgängigmachen einer Veröffentlichung/Veröffentlichen – Geplantes Rückgängigmachen einer Veröffentlichung/Veröffentlichen {#publish-unpublish}

Diese Funktion ermöglicht das sofortige Veröffentlichen ausgewählter Seiten, ohne die zusätzlichen Optionen, die über den Ansatz „Veröffentlichung verwalten“ möglich sind.

Weitere Informationen finden Sie unter [Veröffentlichung verwalten](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication).

### Einschalt- und Ausschaltzeiten – Trigger-Konfiguration {#on-and-off-times-trigger-configuration}

Die zusätzlichen Möglichkeiten für **Einschaltzeit** und **Ausschaltzeit** sind auf der [Registerkarte „Standard“ der Seiteneigenschaften](/help/sites-cloud/authoring/sites-console/page-properties.md#basic) verfügbar.

Um die automatische Replikation für diese Funktion zu realisieren, aktivieren Sie die **Automatische Replikation** in der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) **Ein-Aus-Trigger-Konfiguration**:

![OSGi-Ein-Aus-Trigger-Konfiguration](/help/operations/assets/replication-on-off-trigger.png)

### Veröffentlichung verwalten {#manage-publication}

„Veröffentlichung verwalten“ bietet mehr Optionen als „Schnell veröffentlichen“. Mit diesen können Sie auch untergeordnete Seiten einschließen, Verweise anpassen, alle nötigen Workflows starten und die Veröffentlichung bei Bedarf zu einem späteren Zeitpunkt starten.

Wenn Sie die untergeordneten Elemente eines Ordners für die Option „Später veröffentlichen“ einbeziehen, wird der Workflow „Inhaltsstruktur veröffentlichen“ aufgerufen, der unter [Workflows für die Strukturreplikation](/help/operations/tree-replication-workflows.md#publish-content-tree-workflow) beschrieben wird.

Ausführlichere Informationen zur Funktion „Veröffentlichung verwalten“ finden Sie in der [Dokumentation zu Veröffentlichungsgrundlagen](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication).

Um tiefe Inhaltshierarchien stapelweise zu replizieren, verwenden Sie einen Workflow-basierten Ansatz. Siehe [Workflows für die Strukturreplikation](/help/operations/tree-replication-workflows.md) für den empfohlenen Workflow-Schritt für die Aktivierung der Baumstruktur, die Konfigurationsparameter und die Anleitung zur Überwachung. Der veraltete Workflow „Inhaltsstruktur veröffentlichen“ ist dort ebenfalls als Referenz dokumentiert.

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
// if you need to get the status for more than 1 resource at once, this approach is more performant
Map<String,ReplicationStatus> allStatus = replicationStatusProvider.getBatchReplicationStatus(enResource,deResource);
```

**Replikationsagenten**

AEM as a Cloud Service bietet zwei vordefinierte Replikationsagenten, die Inhalte über Sling Content Distribution von der Autoren- zur Zielebene weiterleiten:

* **publish** - Repliziert aktivierte Inhalte auf der Live-Veröffentlichungsebene. Dieser Agent ist standardmäßig aktiviert und wird bei der Veröffentlichung über die Benutzeroberfläche, Workflows oder die Replikations-API verwendet, sofern nicht anders angegeben.
* **preview** - Repliziert Inhalte auf der Vorschauebene, damit Autoren Änderungen überprüfen können, bevor sie live gehen. Dieser Agent ist standardmäßig nicht aktiviert.

Sie können beide Agenten unter **Tools** > **Bereitstellung** > **Verteilung** anzeigen und überwachen:

![Verteilungsagenten mit Veröffentlichungs- und Vorschau](/help/operations/assets/replication-agents.png "Verteilungsagenten")

Wenn Sie eine Agentenkarte auswählen, werden ihr Status, ihre Protokolle und [Warteschlangendetails](#replication-queues) geöffnet.

**Replikation mit bestimmten Agenten**

Wenn Sie wie oben gezeigt mit der API replizieren, werden nur Agenten verwendet, die standardmäßig aktiviert sind - in AEM as a Cloud Service also nur **publish**. Um ausschließlich auf der Vorschauebene zu replizieren, übergeben Sie eine `AgentFilter`, die den Vorschauagenten auswählt:

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

Wenn Sie ohne eine `AgentFilter` replizieren, wird nur **publish** verwendet und die Vorschauebene ist nicht betroffen.

Die `ReplicationStatus` einer Ressource wird nur aktualisiert, wenn die Replikation mindestens einen Agenten enthält, der standardmäßig aktiviert ist. Im obigen Beispiel wurde nur **preview** verwendet, sodass `ReplicationStatus.isActivated` weiterhin `false` bleibt. Verwenden Sie `getStatusForAgent()`, um den Status für einen bestimmten Agenten zu überprüfen, z. B. `getStatusForAgent("preview")` nach einer reinen Vorschaureplikation oder `getStatusForAgent("publish")` für die Live-Veröffentlichungsebene.

### Methoden zum Invalidieren von Inhalten {#invalidating-content}

Sie können Inhalte direkt ungültig machen, indem Sie entweder die Sling Content Invalidation (SCD) von Author verwenden (bevorzugte Methode) oder die Replikations-API verwenden, um den Replikationsagenten für das Leeren des Publish-Dispatchers aufzurufen. Weitere Information finden Sie auf der Seite [Caching](/help/implementing/dispatcher/caching.md).

**Kapazitätsbeschränkungen der Replikations-API**

Replizieren Sie weniger als 100 Pfade gleichzeitig, wobei 500 die Grenze ist. Oberhalb der Grenze wird eine `ReplicationException` ausgelöst.
Wenn Ihre Anwendungslogik keine atomare Replikation erfordert, kann diese Grenze außer Kraft gesetzt werden, indem Sie die `ReplicationOptions.setUseAtomicCalls` auf „false“ setzen. Dadurch wird eine beliebige Anzahl von Pfaden akzeptiert, aber es werden intern Buckets erstellt, um unter diesem Grenzwert zu bleiben.

Die Größe des pro Replikationsaufruf gesendeten Inhalts darf nicht größer sein als `10 MB`. Diese Regel umfasst die Knoten und Eigenschaften, jedoch keine Binärdateien (Workflow-Pakete und Inhaltspakete werden als Binärdateien erachtet).


## Replikations-Warteschlangen {#replication-queues}

Jeder Replikationsagent zeigt zwei Replikationswarteschlangen an. AEM as a Cloud Service zeigt nicht mehr für jeden Veröffentlichungs-Pod eine separate Warteschlange an. Die Veröffentlichungsebene wird automatisch skaliert, sodass Warteschlangen pro Pod die Komplexität erhöhten, ohne dass praktische Vorteile entstanden wären. Der Warteschlangenstatus wird wie folgt konsolidiert:

* **persistiert** - Die Änderung wird dauerhaft auf der Veröffentlichungsebene gespeichert. Nachdem ein Element diese Warteschlange gelöscht hat, wird der Inhalt beibehalten. Veröffentlichungsinstanzen erreichen im Laufe der Zeit einen konsistenten Status.
* **Vollständig veröffentlicht** - Die Änderung ist auf allen Veröffentlichungs-Pods verfügbar und der Dispatcher-Cache wird für die betroffenen Pfade gelöscht. Nachdem ein Element diese Warteschlange gelöscht hat, erhalten Besucher den aktualisierten Inhalt.

### Überwachen von Replikationswarteschlangen {#monitor-replication-queues}

1. Navigieren Sie in der [globalen Navigation](/help/sites-cloud/authoring/basic-handling.md#global-navigation) von AEM zu **Tools** > **Bereitstellung**.

   ![Navigieren Sie in der Tools-/](/help/operations/assets/replication-agent-navigation.png "-Navigation zur Verteilung")

1. Wählen Sie **Verteilung** aus und öffnen Sie dann die **publish** oder **preview** Agentenkarte.

1. Überprüfen Sie auf **Registerkarte** Status“, ob jede Warteschlange einen einwandfreien Status aufweist. Überprüfen Sie **Artikel ausstehend** für Arbeit, die darauf wartet, verarbeitet zu werden, und **Letztes Element verarbeitet** für die letzte Aktivität.

   ![Replikationswarteschlangen mit persistenten und vollständig veröffentlichten ](/help/operations/assets/replication-queues.png "Replikationswarteschlangen")

1. Wählen Sie **Verbindung testen** aus, um zu überprüfen, ob der Agent den Verteilungs-Service erreichen kann.
1. Wählen Sie die **Protokolle** aus, um den Verlauf der Inhaltsveröffentlichungen anzuzeigen.

   ![Replikationsprotokolle](/help/operations/assets/publish-logs.png "Protokolle")

## Fehlerbehebung {#troubleshooting}

Wenn Inhalte nicht veröffentlicht werden können, wird die Veröffentlichung vom AEM-Veröffentlichungs-Service rückgängig gemacht. Verwenden Sie [Replikationswarteschlangen überwachen](#monitor-replication-queues), um die Registerkarte **Status** des Agenten zu öffnen und die betroffene Warteschlange zu identifizieren.

Wenn eine Warteschlange den Status Rot aufweist, überprüfen Sie die ausstehenden Elemente, um herauszufinden, was den Fehler verursacht hat. Wählen Sie die Warteschlange aus, um ausstehende Elemente anzuzeigen, und löschen Sie dann bei Bedarf einzelne Elemente oder die gesamte Warteschlange.
