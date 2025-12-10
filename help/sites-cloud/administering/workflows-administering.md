---
title: Verwalten der Workflow-Instanzen
description: Erfahren Sie, wie Sie Workflow-Instanzen mithilfe der Workflow-Konsole verwalten
feature: Administering
role: Admin
exl-id: d2adb5e8-3f0e-4a3b-b7d0-dbbc5450e45f
solution: Experience Manager Sites
source-git-commit: 372d8969b1939e9a24d7910a1678a17c0dc9f9fd
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 92%

---

# Verwalten der Workflow-Instanzen {#administering-workflow-instances}

Die Workflow-Konsole stellt mehrere Tools für die Verwaltung von Workflow-Instanzen bereit, um sicherzustellen, dass sie wie erwartet ausgeführt werden.

Für die Verwaltung Ihrer Workflows steht eine Reihe von Konsolen bereit. Verwenden Sie die [globale Navigation](/help/sites-cloud/authoring/basic-handling.md#global-navigation), um das Bedienfeld **Tools** zu öffnen, und wählen Sie dann **Workflow** aus:

* **Modelle**: Workflow-Definitionen verwalten
* **Instanzen**: Laufende Workflow-Instanzen anzeigen und verwalten
* **Starter**: Launches von Workflows verwalten
* **Archiv**: Protokoll der erfolgreich abgeschlossenen Workflows anzeigen
* **Fehler**: Protokoll der mit Fehlern abgeschlossenen Workflows anzeigen
* **Automatisch zuweisen**: Automatische Zuweisung von Workflows zu Vorlagen konfigurieren

## Überwachen des Status von Workflow-Instanzen {#monitoring-the-status-of-workflow-instances}

1. Wählen Sie über die Navigation **Tools** und dann **Workflow** aus.
1. Wählen Sie **Instanzen** aus, um die Liste der aktuell ausgeführten Workflow-Instanzen anzuzeigen.
1. In der oberen Leiste in der rechten Ecke zeigen die Workflow-Instanzen **Laufende Workflows**, **Status** und **Details** an.
1. **Laufende Workflows** zeigt die Anzahl der aktuell ausgeführten Workflows und ihren Status an. In den angegebenen Bildern ist beispielsweise die Anzahl der **laufenden Workflows** sowie der **Status** der AEM-Instanz zu sehen:

   * **Status: Gesund**
     ![status-healthy](/help/sites-cloud/administering/assets/status-healthy.png)

   * **Status: Ungesund**
     ![status-unhealthy](/help/sites-cloud/administering/assets/status-unhealthy.png)

1. Klicken Sie für **Statusdetails** von Workflow-Instanzen auf **Details**, um die **Anzahl der laufenden Workflows**, **abgeschlossenen Workflow-Instanzen**, **abgebrochenen Workflow-Instanzen**, **fehlgeschlagenen Workflow-Instanzen** usw. anzuzeigen. Beispielsweise sind unten die jeweiligen Bilder aufgeführt, die **Statusdetails** wie folgt anzeigen:

   * **Statusdetails: Gesund**
     ![status-details-healthy](/help/sites-cloud/administering/assets/status-details-healthy.png)

   * **Statusdetails: Ungesund**
     ![status-details-unhealthy](/help/sites-cloud/administering/assets/status-details-unhealthy.png)

   >[!NOTE]
   >
   > Um eine gesunde Workflow-Instanz zu erhalten, befolgen Sie die Best Practices unter [Regelmäßige Bereinigung der Workflow-Instanzen](#regular-purging-of-workflow-instances) oder [Best Practices für Workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-best-practices.html?lang=de).

## Durchsuchen von Workflow-Instanzen {#search-workflow-instances}

1. Wählen Sie über die Navigation **Tools** und dann **Workflow** aus.
1. Wählen Sie **Instanzen** aus, um die Liste der aktuell ausgeführten Workflow-Instanzen anzuzeigen. Wählen Sie in der oberen Leiste links die Option **Filter**. Alternativ können Sie den Tastaturbefehl Alt+1 verwenden. Daraufhin wird das folgende Dialogfeld angezeigt:

   ![wf-99-1](/help/sites-cloud/administering/assets/wf-99-1.png)

1. Wählen Sie im Dialogfeld „Filter“ die gewünschten Suchkriterien für den Workflow aus. Sie können anhand der folgenden Eingaben suchen:

   * Payload-Pfad: einen bestimmten Pfad auswählen
   * Workflow-Modell: ein Workflow-Modell auswählen
   * Bevollmächtigter: einen Workflow-Bevollmächtigten auswählen
   * Typ: Aufgabe, Workflow-Element oder Workflow-Fehler
   * Aufgabenstatus: „Aktiv“, „Abgeschlossen“ oder „Beendet“
   * Meine Position: Eigentümer UND Bevollmächtigter, nur Eigentümer, nur Bevollmächtigter
   * Startdatum: Startdatum vor oder nach einem bestimmten Datum
   * Enddatum: Enddatum vor oder nach einem bestimmten Datum
   * Fälligkeitsdatum: Fälligkeitsdatum vor oder nach einem bestimmten Datum
   * Aktualisierungsdatum: Aktualisierungsdatum vor oder nach einem bestimmten Datum

## Aussetzen, Fortsetzen und Beenden einer Workflow-Instanz {#suspending-resuming-and-terminating-a-workflow-instance}

1. Wählen Sie über die Navigation **Tools** und dann **Workflow** aus.
1. Wählen Sie **Instanzen** aus, um die Liste der aktuell ausgeführten Workflow-Instanzen anzuzeigen.

   ![wf-96-1](/help/sites-cloud/administering/assets/wf-96-1.png)

1. Wählen Sie ein spezifisches Element aus und verwenden Sie dann je nachdem **Beenden**, **Aussetzen** oder **Fortsetzen**. Eine Bestätigung und/oder weitere Details sind erforderlich:

   ![wf-97-1](/help/sites-cloud/administering/assets/wf-97-1.png)

   >[!NOTE]
   >
   >
   >Um einen Workflow zu beenden oder abzubrechen, muss er in einem Zustand sein, in dem auf Benutzerinteraktionen gewartet wird, z. B. in einem Teilnehmerschritt. Der Versuch, einen Workflow abzubrechen, der gerade Aufträge ausführt (aktive Threads, die gerade ausgeführt werden), führt möglicherweise nicht zu den erwarteten Ergebnissen.


## Anzeigen archivierter Workflows {#viewing-archived-workflows}

1. Wählen Sie über die Navigation **Tools** und dann **Workflow** aus.

1. Wählen Sie **Archiv** aus, um die Liste der erfolgreich abgeschlossenen Workflow-Instanzen anzuzeigen.

   ![archived-instances](/help/sites-cloud/administering/assets/archived-instances.png)

   >[!NOTE]
   >
   >
   >Der Abbruchstatus wird als erfolgreiches Beenden betrachtet, da er infolge der Benutzeraktion auftritt, wie zum Beispiel:
   >
   >* nach der Verwendung der Aktion **Beenden** oder
   >* wenn eine von einem Workflow betroffene Seite (erzwungenermaßen) gelöscht wird, dann wird der Workflow beendet.

1. Wählen Sie ein spezifisches Element und dann **Offener Verlauf** aus, um mehr Details anzuzeigen:

   ![wf-99](/help/sites-cloud/administering/assets/wf-99.png)

## Beheben von Workflow-Instanzfehlern {#fixing-workflow-instance-failures}

Schlägt ein Workflow fehl, ermöglicht Ihnen AEM mit der **Fehler-Konsole** die Untersuchung und das Ergreifen entsprechender Maßnahmen, sobald die ursprüngliche Ursache behoben wurde:

* **Fehlerdetails**
Öffnet ein Fenster, das die **Fehlermeldung**, den **Schritt und den &#x200B;** Fehlerstapel** anzeigt.

* **Offener Verlauf** Die Details des Workflow-Verlaufs werden angezeigt.

* **Schritt erneut ausführen** Hierdurch wird die Komponenteninstanz „Skriptschritt“ erneut ausgeführt. Verwenden Sie den Befehl „Schritt erneut ausführen“, nachdem Sie die Ursache des ursprünglichen Fehlers behoben haben. Wiederholen Sie zum Beispiel den Schritt nach der Behebung eines Fehlers in dem Skript, das vom Prozessschritt ausgeführt wird.
* **Beenden** Beenden Sie den Workflow, wenn der Fehler eine nicht mit dem Workflow zu vereinbarende Situation verursacht hat. So kann der Workflow beispielsweise von Umgebungsbedingungen abhängen, wie zum Beispiel von Informationen im Repository, die nicht mehr für die Workflow-Instanz gelten.
* **Beenden und erneut versuchen** Dies hat ähnliche Auswirkungen wie **Beenden**, außer dass eine neue Workflow-Instanz mit der ursprünglichen Payload und Beschreibung sowie dem ursprünglichen Titel gestartet wird.

Setzen Sie den Workflow anschließend zur Untersuchung von Fehlern fort oder beenden Sie ihn. Gehen Sie hierzu wie folgt vor:

1. Wählen Sie über die Navigation **Tools** und dann **Workflow** aus.

1. Wählen Sie **Fehler** aus, um die Liste der Workflow-Instanzen anzuzeigen, die nicht erfolgreich abgeschlossen wurden.
1. Wählen Sie ein spezifisches Element und dann die entsprechende Aktion aus:

![workflow-failure](/help/sites-cloud/administering/assets/workflow-failure.png)

## Regelmäßiges Bereinigen von Workflow-Instanzen {#regular-purging-of-workflow-instances}

Die Minimierung der Anzahl von Workflow-Instanzen steigert die Leistung der Workflow-Engine, sodass Sie regelmäßig abgeschlossene oder laufende Workflow-Instanzen aus dem Repository löschen können.

Konfigurieren Sie die **Adobe Granite Workflow-Bereinigungskonfiguration**, um Workflow-Instanzen je nach ihrem Alter und Status zu löschen. Darüber hinaus können Sie Workflow-Instanzen aller Modelle oder eines bestimmten Modells löschen.

Sie können auch mehrere Konfigurationen des Service erstellen, um Workflow-Instanzen zu löschen, die andere Kriterien erfüllen. Erstellen Sie zum Beispiel eine Konfiguration, mit der die Instanzen eines bestimmten Workflow-Modells gelöscht werden, wenn sie bedeutend länger als erwartet ausgeführt werden. Erstellen Sie eine weitere Konfiguration, die alle abgeschlossenen Workflows nach einigen Tagen löscht, um die Größe des Repositorys zu minimieren.

Zum Konfigurieren des Service können Sie die OSGi-Konfigurationsdateien konfigurieren. Siehe [OSGi-Konfigurationsdateien](/help/implementing/deploying/configuring-osgi.md). In der folgenden Tabelle werden die Eigenschaften beschrieben, die für beide Methoden erforderlich sind.

>[!NOTE]
>Für das Hinzufügen der Konfiguration zum Repository lautet die Service-PID:
>`com.adobe.granite.workflow.purge.Scheduler`
>Da der Service ein Factory-Service ist, erfordert der Name des `sling:OsgiConfig`-Knotens einen ein Kennungssuffix, wie zum Beispiel:
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

| Eigenschaftsname (Web-Konsole) | OSGi-Eigenschaftsname | Beschreibung |
|--- |--- |--- |
| Vorgangsname  | `scheduledpurge.name` | Dies ist ein beschreibender Name für die geplante Bereinigung. |
| Workflow-Status | `scheduledpurge.workflowStatus` | Dies ist der Status der zu bereinigenden Workflow-Instanz. Die folgenden Werte sind gültig:<br><br>- ABGESCHLOSSEN: Abgeschlossene Workflow-Instanzen werden gelöscht.<br>- WIRD AUSGEFÜHRT: Laufende Workflow-Instanzen werden gelöscht. |
| Zu bereinigende Modelle | `scheduledpurge.modelIds` | Die ID der zu löschenden Workflow-Modelle.<br>Die ID ist der Pfad zum Modellknoten, zum Beispiel:<br> `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model` <br><br> Geben Sie keinen Wert an, um Instanzen aller Workflow-Modelle zu bereinigen.<br>Um mehrere Modelle anzugeben, klicken Sie in der Web-Konsole auf die Schaltfläche `+` . |
| Workflow-Alter | `scheduledpurge.daysold` | Dies gibt das Alter der zu bereinigenden Workflow-Instanz in Tagen an. |
| Workflow-Payload-Paket | `scheduledpurge.purgePackagePayload` | Gibt an, ob das Payload-Paket gelöscht werden soll (`true` oder `false`). |


## Einstellen der maximalen Größe des Posteingangs {#setting-the-maximum-size-of-the-inbox}

Sie können die maximale Größe des Posteingangs durch die Konfiguration des **Adobe Granite Workflow-Service** bestimmen. Siehe [Hinzufügen einer OSGi-Konfiguration zum Repository](/help/implementing/deploying/configuring-osgi.md). In der folgenden Tabelle wird die Eigenschaft beschrieben, die Sie konfigurieren können.

>[!NOTE]
>Für das Hinzufügen der Konfiguration zum Repository lautet die Service-PID:
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Eigenschaftsname (Web-Konsole) | OSGi-Eigenschaftsname |
|---|---|
| Max. Größe für Posteingangsabfrage | granite.workflow.inboxQuerySize |

## Verwenden von Workflow-Variablen für kundeneigene Datenspeicher {#using-workflow-variables-customer-datastore}

Von Workflows verarbeitete Daten werden im von Adobe bereitgestellten Speicher (JCR) gespeichert. Diese Daten können von sensibler Natur sein. Sie können alle benutzerdefinierten Metadaten/Daten in Ihrem eigenen verwalteten Speicher speichern, anstatt die von Adobe bereitgestellte Datenspeicherung zu verwenden. In diesen Abschnitten wird beschrieben, wie Sie diese Variablen für die externe Speicherung einrichten.

### Festlegen des Modells für die Verwendung der externen Datenspeicherung von Metadaten {#set-model-for-external-storage}

Auf der Ebene des Workflow-Modells wird ein Flag bereitgestellt, das angibt, dass das Modell (und seine Laufzeitinstanzen) über eine externe Datenspeicherung von Metadaten verfügt. Workflow-Variablen werden nicht für die Workflow-Instanzen der Modelle, die für den externen Speicher markiert sind, in JCR beibehalten.

Die Eigenschaft *userMetadataPersistenceEnabled* wird im *jcr:content-Knoten* Workflow-Modells gespeichert. Dieses Flag wird in Workflow-Metadaten als *cq:userMetaDataCustomPersistenceEnabled* beibehalten.

Die folgende Illustration zeigt, wie Sie die Hervorhebung in einem Workflow festlegen.

![workflow-externalize-config](/help/sites-cloud/administering/assets/workflow-externalize-config.png)

### APIs für Metadaten in der externen Datenspeicherung {#apis-for-metadata-external-storage}

Um die Variablen extern zu speichern, müssen Sie die APIs implementieren, die der Workflow bereitstellt.

UserMetaDataPersistenceContext

Die folgenden Beispiele zeigen die Verwendung der API.

```
@ProviderType
public interface UserMetaDataPersistenceContext {
 
    /**
     * Gets the workflow for persistence
     * @return workflow
     */
    Workflow getWorkflow();
 
    /**
     * Gets the workflow id for persistence
     * @return workflowId
     */
    String getWorkflowId();
 
    /**
     * Gets the user metadata persistence id
     * @return userDataId
     */
    String getUserDataId();
}
```

UserMetaDataPersistenceProvider

```
/**
 * This provider can be implemented to store the user defined workflow-data metadata in a custom storage location
 */
@ConsumerType
public interface UserMetaDataPersistenceProvider {
 
   /**
    * Retrieves the metadata using a unique identifier
    * @param userMetaDataPersistenceContext
    * @param metaDataMap of user defined workflow data metaData
    * @throws WorkflowException
    */
   void get(UserMetaDataPersistenceContext userMetaDataPersistenceContext, MetaDataMap metaDataMap) throws WorkflowException;
 
   /**
    * Stores the given metadata to the custom storage location
    * @param userMetaDataPersistenceContext
    * @param metaDataMap metadata map
    * @return the unique identifier that can be used to retrieve metadata. If null is returned, then workflowId is used.
    * @throws WorkflowException
    */
   String put(UserMetaDataPersistenceContext userMetaDataPersistenceContext, MetaDataMap metaDataMap) throws WorkflowException;
 
} 
```
