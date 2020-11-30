---
title: Verwalten der Workflow-Instanzen
description: Erfahren Sie, wie Workflow-Instanzen verwaltet werden
translation-type: tm+mt
source-git-commit: c19079b1be36c4e87962491f263ddf97ab98f831
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 100%

---


# Verwalten der Workflow-Instanzen {#administering-workflow-instances}

Die Workflow-Konsole stellt mehrere Tools für die Verwaltung von Workflow-Instanzen bereit, um sicherzustellen, dass sie wie erwartet ausgeführt werden.

Für die Verwaltung Ihrer Workflows steht eine Reihe von Konsolen bereit. Verwenden Sie die [globale Navigation](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation), um das Bedienfeld **Tools** zu öffnen, und wählen Sie dann **Workflow** aus:

* **Modelle**: Workflow-Definitionen verwalten
* **Instanzen**: Laufende Workflow-Instanzen anzeigen und verwalten
* **Starter**: Launches von Workflows verwalten
* **Archiv**: Protokoll der erfolgreich abgeschlossenen Workflows anzeigen
* **Fehler**: Protokoll der mit Fehlern abgeschlossenen Workflows anzeigen
* **Automatisch zuweisen**: Automatische Zuweisung von Workflows zu Vorlagen konfigurieren

## Überwachen des Status von Workflow-Instanzen {#monitoring-the-status-of-workflow-instances}

1. Wählen Sie über die Navigation **Tools** und dann **Workflow** aus.
1. Wählen Sie **Instanzen** aus, um die Liste der aktuell ausgeführten Workflow-Instanzen anzuzeigen.

   ![wf-97](/help/sites-cloud/administering/assets/wf-97.png)


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

## Anzeigen archivierter Workflows {#viewing-archived-workflows}

1. Wählen Sie über die Navigation **Tools** und dann **Workflow** aus.

1. Wählen Sie **Archiv** aus, um die Liste der erfolgreich abgeschlossenen Workflow-Instanzen anzuzeigen.

   ![wf-98](/help/sites-cloud/administering/assets/wf-98.png)

   >[!NOTE]
   >Der Abbruchstatus wird als erfolgreiches Beenden betrachtet, da er infolge der Benutzeraktion auftritt, wie zum Beispiel:
   >
   >* nach der Verwendung der Aktion **Beenden** oder
   >* wenn eine von einem Workflow betroffene Seite (erzwungenermaßen) gelöscht wird, wird der Workflow beendet


1. Wählen Sie ein spezifisches Element und dann **Offener Verlauf** aus, um mehr Details anzuzeigen:

   ![wf-99](/help/sites-cloud/administering/assets/wf-99.png)

## Beheben von Workflow-Instanzfehlern {#fixing-workflow-instance-failures}

Schlägt ein Workflow fehl, ermöglicht Ihnen AEM mit der **Fehler-Konsole** die Untersuchung und das Ergreifen entsprechender Maßnahmen, sobald die ursprüngliche Ursache behoben wurde:

* **Fehlerdetails**
Öffnet ein Fenster zum Anzeigen von 
**Fehlermeldung**, **Schritt** und **Fehlerstapel**.

* **Offener Verlauf** Die Details des Workflow-Verlaufs werden angezeigt.

* **Schritt erneut ausführen** Hierdurch wird die Komponenteninstanz „Skriptschritt“ erneut ausgeführt. Verwenden Sie den Befehl „Schritt erneut ausführen“, nachdem Sie die Ursache des ursprünglichen Fehlers behoben haben. Wiederholen Sie zum Beispiel den Schritt nach der Behebung eines Bugs in dem Skript, das vom Prozessschritt ausgeführt wird.
* **Beenden** Beenden Sie den Workflow, wenn der Fehler eine nicht mit dem Workflow zu vereinbarende Situation verursacht hat. So kann der Workflow beispielsweise von Umgebungsbedingungen abhängen, wie zum Beispiel von Informationen im Repository, die nicht mehr für die Workflow-Instanz gelten.
* **Beenden und erneut versuchen** Dies hat ähnliche Auswirkungen wie **Beenden**, außer dass eine neue Workflow-Instanz mit der ursprünglichen Payload und Beschreibung sowie dem ursprünglichen Titel gestartet wird.

Setzen Sie den Workflow anschließend zur Untersuchung von Fehlern fort oder beenden Sie ihn. Gehen Sie hierzu wie folgt vor:

1. Wählen Sie über die Navigation **Tools** und dann **Workflow** aus.

1. Wählen Sie **Fehler** aus, um die Liste der Workflow-Instanzen anzuzeigen, die nicht erfolgreich abgeschlossen wurden.
1. Wählen Sie ein spezifisches Element und dann die entsprechende Aktion aus:

   ![wf-47](/help/sites-cloud/administering/assets/wf-47.png)

## Regelmäßiges Bereinigen von Workflow-Instanzen {#regular-purging-of-workflow-instances}

Die Minimierung der Anzahl von Workflow-Instanzen steigert die Leistung der Workflow-Engine, sodass Sie regelmäßig abgeschlossene oder laufende Workflow-Instanzen aus dem Repository löschen können.

Konfigurieren Sie die **Adobe Granite Workflow-Bereinigungskonfiguration**, um Workflow-Instanzen je nach ihrem Alter und Status zu löschen. Darüber hinaus können Sie Workflow-Instanzen aller Modelle oder eines bestimmten Modells löschen.

Sie können auch mehrere Konfigurationen des Service erstellen, um Workflow-Instanzen zu löschen, die andere Kriterien erfüllen. Erstellen Sie zum Beispiel eine Konfiguration, mit der die Instanzen eines bestimmten Workflow-Modells gelöscht werden, wenn sie bedeutend länger als erwartet ausgeführt werden. Erstellen Sie eine weitere Konfiguration, die alle abgeschlossenen Workflows nach einer bestimmten Anzahl von Tagen löscht, um die Größe des Repositorys zu minimieren.

Zum Konfigurieren des Service können Sie die OSGi-Konfigurationsdateien konfigurieren. Siehe [OSGi-Konfigurationsdateien](/help/implementing/deploying/configuring-osgi.md). In der folgenden Tabelle werden die Eigenschaften beschrieben, die für beide Methoden erforderlich sind.

>[!NOTE]
>Für das Hinzufügen der Konfiguration zum Repository lautet die Service-PID:
>`com.adobe.granite.workflow.purge.Scheduler`
>Da der Service ein Factory-Service ist, erfordert der Name des `sling:OsgiConfig`-Knotens einen ein Kennungssuffix, wie zum Beispiel:
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

<table>
 <tbody>
  <tr>
   <th>Eigenschaftsname (Web-Konsole)</th>
   <th>OSGi-Eigenschaftsname</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Auftragsname</td>
   <td>scheduledpurge.name</td>
   <td>Dies ist ein beschreibender Name für die geplante Bereinigung.</td>
  </tr>
  <tr>
   <td>Workflow-Status</td>
   <td>scheduledpurge.workflowStatus</td>
   <td><p>Dies ist der Status der zu bereinigenden Workflow-Instanz. Die folgenden Werte sind gültig:</p>
    <ul>
     <li>ABGESCHLOSSEN: Abgeschlossene Workflow-Instanzen werden gelöscht.</li>
     <li>WIRD AUSGEFÜHRT: Aktuell ausgeführte Workflow-Instanzen werden gelöscht.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Zu bereinigende Modelle</td>
   <td>scheduledpurge.modelIds</td>
   <td><p>Dies ist die ID der zu bereinigenden Workflow-Modelle. Die ID ist der Pfad zum Modellknoten, wie zum Beispiel:<br /> /conf/global/settings/workflow/models/dam/update_asset/jcr:content/model<br /> Geben Sie keinen Wert zur Bereinigung der Instanzen aller Workflow-Modelle ein.</p> <p>Klicken Sie zum Angeben mehrerer Modelle auf die „+“-Schaltfläche innerhalb der Web-Konsole. </p> </td>
  </tr>
  <tr>
   <td>Workflow-Alter</td>
   <td>scheduledpurge.daysold</td>
   <td>Dies gibt das Alter der zu bereinigenden Workflow-Instanz in Tagen an.</td>
  </tr>
 </tbody>
</table>

## Einstellen der maximalen Größe des Posteingangs  {#setting-the-maximum-size-of-the-inbox}

Sie können die maximale Größe des Posteingangs durch die Konfiguration des **Adobe Granite Workflow-Service** bestimmen. Siehe [Hinzufügen einer OSGi-Konfiguration zum Repository](/help/implementing/deploying/configuring-osgi.md). In der folgenden Tabelle wird die Eigenschaft beschrieben, die Sie konfigurieren können.

>[!NOTE]
>Für das Hinzufügen der Konfiguration zum Repository lautet die Service-PID:
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Eigenschaftsname (Web-Konsole) | OSGi-Eigenschaftsname |
|---|---|
| Max. Größe für Posteingangsabfrage | granite.workflow.inboxQuerySize |

