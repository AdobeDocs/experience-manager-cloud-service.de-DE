---
title: Wartungsaufgaben in AEM as a Cloud Service
description: Erfahren Sie mehr über Wartungsaufgaben in AEM as a Cloud Service und deren Konfiguration.
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
feature: Operations
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 99%

---


# Wartungsaufgaben in AEM as a Cloud Service {#maintenance-tasks-in-aem-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="Wartungsaufgaben"
>abstract="Wartungsaufgaben sind Prozesse, die nach einem Zeitplan ausgeführt werden, um das Repository zu optimieren. Bei AEM as a Cloud Service ist der Kundenaufwand der Konfiguration von Betriebseigenschaften für Wartungsaufgaben minimal. Kunden können ihre Ressourcen auf Angelegenheiten in der Anwendungsebene konzentrieren und die Infrastrukturvorgänge Adobe überlassen."

Wartungsaufgaben sind Prozesse, die nach einem Zeitplan ausgeführt werden, um das Repository zu optimieren. Bei AEM as a Cloud Service ist der Kundenaufwand der Konfiguration von Betriebseigenschaften für Wartungsaufgaben minimal. Kunden können ihre Ressourcen auf Angelegenheiten in der Anwendungsebene konzentrieren und die Infrastrukturvorgänge Adobe überlassen.

## Konfigurieren von Wartungsaufgaben {#maintenance-tasks-configuring}

In früheren Versionen von AEM konnten Sie Wartungsaufgaben mithilfe der Wartungskarte konfigurieren (Tools > Vorgänge > Wartung). Bei AEM as a Cloud Service ist die Wartungskarte nicht mehr vorhanden. Daher sollten Konfigurationen an die Quell-Code-Verwaltung übertragen und mithilfe von Cloud Manager bereitgestellt werden. Adobe verwaltet Wartungsaufgaben, deren Einstellungen von Kundinnen und Kunden nicht konfiguriert werden können (z. B. Datenspeicherbereinigung).  Andere Wartungsaufgaben können kundenseitig konfiguriert werden, wie in der folgenden Tabelle beschrieben.

>[!CAUTION]
>
>Adobe behält sich das Recht vor, Konfigurationseinstellungen für Wartungsaufgaben der Kundschaft außer Kraft zu setzen, um Probleme wie Leistungsbeeinträchtigungen zu verhindern.

In der folgenden Tabelle sind die verfügbaren Wartungsaufgaben aufgeführt.

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>Wartungsaufgabe</th>
    <th>Wer ist für die Konfiguration verantwortlich</th>
    <th>Konfigurationsweise (optional)</th>
  </tr>  
  <tr>
    <td>Speicherbereinigung</td>
    <td>Adobe</td>
    <td>N/A – volle Verantwortung von Adobe</td>
  </td> 
  </tr>
  <tr>
    <td>Versionsbereinigung</td>
    <td>Kundin/Kunde</td>
    <td>Die Versionsbereinigung ist derzeit standardmäßig deaktiviert, die Richtlinie kann jedoch wie unter <a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks">Wartungsaufgaben für Versionsbereinigung und Audit-Protokollbereinigung</a> beschrieben konfiguriert werden.<br/><br/>Die Bereinigung wird in Kürze standardmäßig aktiviert, wobei diese Werte überschrieben werden können.<br>
   </td>
  </td>
  </tr>
  <tr>
    <td>Bereinigung der Auditprotokolle</td>
    <td>Kundin/Kunde</td>
    <td>Die Auditprotokollbereinigung ist derzeit standardmäßig deaktiviert, die Richtlinie kann jedoch wie unter <a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks">Wartungsaufgaben für Versionsbereinigung und Auditprotokollbereinigung</a> beschrieben konfiguriert werden.<br/><br/>Die Bereinigung wird in Kürze standardmäßig aktiviert, wobei diese Werte überschrieben werden können.<br>
   </td>
   </td>
  </tr>
  <tr>
    <td>Lucene-Binärdateien-Bereinigung</td>
    <td>Adobe</td>
    <td>Nicht verwendet und daher von Adobe deaktiviert.</td>
  </td>
  </tr>
  <tr>
    <td>Ad-hoc-Aufgabenbereinigung</td>
    <td>Kundin/Kunde</td>
    <td>
    <p>Das muss in Git geschehen. Überschreiben Sie den vorkonfigurierten Konfigurationsknoten des Wartungsfensters unter <code>/libs</code> durch Erstellen von Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> oder <code>granite_monthly</code>.</p>
    <p>Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster. Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten hinzufügen. Benennen Sie ihn <code>granite_TaskPurgeTask</code>, wobei Sie das Attribut <code>sling:resourceType</code> auf <code>granite/operations/components/maintenance/task</code> und das Attribut <code>granite.maintenance.name</code> auf <code>TaskPurge</code> setzen. Konfigurieren Sie die OSGi-Eigenschaften. Eine Liste der Eigenschaften finden Sie unter <code>com.adobe.granite.taskmanagement.impl.purge.TaskPurgeMaintenanceTask</code>.</p>
  </td>
  </tr>
    <tr>
    <td>Workflow-Bereinigung</td>
    <td>Kundin/Kunde</td>
    <td>
    <p>Das muss in Git geschehen. Überschreiben Sie den Standardkonfigurationsknoten des Wartungsfensters unter <code>/libs</code>, indem Sie Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> oder <code>granite_monthly</code> erstellen. Weitere Konfigurationsdetails finden Sie unten in der Tabelle zum Wartungsfenster.</p>
    <p>Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn <code>granite_WorkflowPurgeTask</code>). Informationen zum Konfigurieren der OSGi-Eigenschaften finden Sie in der <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html?lang=de#regular-purging-of-workflow-instances">AEM 6.5-Dokumentation zu Wartungsaufgaben</a>.</p>
  </td>
  </tr>
  <tr>
    <td>Projektbereinigung</td>
    <td>Kundin/Kunde</td>
    <td>
    <p>Das muss in Git geschehen. Überschreiben Sie den Standardkonfigurationsknoten des Wartungsfensters unter <code>/libs</code>, indem Sie Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> oder <code>granite_monthly</code> erstellen. Weitere Konfigurationsdetails finden Sie unten in der Tabelle zum Wartungsfenster.</p>
    <p>Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn <code>granite_ProjectPurgeTask</code>). Siehe die Liste der <a href="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi">OSGi-Eigenschaften</a> zur <b>Bereinigungskonfiguration von Adobe-Projekten</b>.</p>
  </td>
  </tr>
  </tbody>
</table>

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>Konfiguration von Wartungsfenstern</th>
    <th>Wer ist für die Konfiguration verantwortlich</th>
    <th>Konfigurationstyp</th>
    <th>Parameter</th>
  </tr>
  <tr>
    <td>Täglich</td>
    <td>Kundin/Kunde</td>
    <td>JCR-Knotendefinition</td>
  <td>
  <p><strong>windowSchedule=daily</strong> (dieser Wert sollte nicht geändert werden)</p>
  <p><strong>windowStartTime = HH:MM</strong> unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.</p>
  <p><strong>windowEndTime = HH:MM</strong> unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.</p>
  <p>Eine Wartungsaufgabe kann während dieses Zeitraums nicht mehr als einmal ausgeführt werden.</p>
  </td> 
  </tr>
  <tr>
    <td>Wöchentlich</td>
    <td>Kundin/Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td>
    <p><strong>windowSchedule=weekly</strong> (dieser Wert sollte nicht geändert werden)</p>
    <p><strong>windowStartTime = HH:MM</strong> unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.</p>
    <p><strong>windowEndTime = HH:MM</strong> unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.</p>
    <p>Eine Wartungsaufgabe kann während dieses Zeitraums nicht mehr als einmal ausgeführt werden.</p>
    <p><strong>windowScheduleWeekdays= Array von zwei Werten von 1–7 (z. B. [5,5])</strong> Der erste Wert des Arrays ist der Starttag, an dem der Auftrag geplant wird, der zweite Wert der Endtag, an dem der Auftrag gestoppt wird. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben.</p>
    </td>
  </tr>
  <tr>
    <td>Monatlich</td>
    <td>Kundin/Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td>
    <p><strong>windowSchedule=monthly</strong> (dieser Wert sollte nicht geändert werden)</p>
    <p><strong>windowStartTime = HH:MM</strong> unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.</p>
    <p><strong>windowEndTime = HH:MM</strong> unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.</p>
    <p>Eine Wartungsaufgabe kann während dieses Zeitraums nicht mehr als einmal ausgeführt werden.</p>
    <p><strong>windowScheduleWeekdays=Array von zwei Werten von 1–7 (z. B. [5,5])</strong>. Der erste Wert des Arrays ist der Starttag, an dem der Auftrag geplant wird, der zweite Wert der Endtag, an dem der Auftrag gestoppt wird. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0, um in der ersten Woche des Monats zu planen, oder 1, um in der letzten Woche des Monats zu planen. Wird kein Wert angegeben, werden die Aufträge an dem Tag geplant, der durch windowScheduleWeekdays (jeden Monat) festgelegt ist.</p>
    </td>
    </tr>
    </tbody>
</table>

**Standorte**:

* Täglich – /apps/settings/granite/operations/maintenance/granite_daily
* Wöchentlich – /apps/settings/granite/operations/maintenance/granite_weekly
* Monatlich – /apps/settings/granite/operations/maintenance/granite_month

**Code-Beispiele**

Code-Beispiel 1 (täglich)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
  xmlns:jcr="http://www.jcp.org/jcr/1.0" 
  jcr:primaryType="sling:Folder"
  sling:configCollectionInherit="true"
  sling:configPropertyInherit="true"
  windowSchedule="daily"
  windowStartTime="03:00"
  windowEndTime="05:00"
 />
```

Code-Beispiel 2 (wöchentlich)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
   xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="sling:Folder"
   sling:configCollectionInherit="true"
   sling:configPropertyInherit="true"
   windowEndTime="15:30"
   windowSchedule="weekly"
   windowScheduleWeekdays="[5,5]"
   windowStartTime="14:30"/>
```

Code-Beispiel 3 (monatlich)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
   xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="sling:Folder"
   sling:configCollectionInherit="true"
   sling:configPropertyInherit="true"
   windowEndTime="15:30"
   windowSchedule="monthly"
   windowFirstLastStartDay=0
   windowScheduleWeekdays="[5,5]"
   windowStartTime="14:30"/>
```

## Wartungsaufgaben für Versionsbereinigung und Auditprotokollbereinigung {#purge-tasks}

Durch das Bereinigen der Versionen und des Auditprotokolls wird die Größe des Repositorys verringert und in einigen Szenarien kann die Leistung verbessert werden.

>[!NOTE]
>
>AEM Guides-Kundinnen und -Kunden sollten keine Versionsbereinigung konfigurieren.

### Standardwerte {#defaults}

Derzeit ist die Bereinigung nicht standardmäßig aktiviert, aber dies wird sich in Zukunft ändern. Umgebungen, die vor Aktivierung der standardmäßigen Bereinigung erstellt wurden, haben einen konservativeren Schwellenwert, sodass das Bereinigen nicht unerwartet erfolgt. Weitere Informationen zu den Richtlinien für standardmäßige Bereinigungen finden Sie unten in den Abschnitten „Versionsbereinigung“ und „Auditprotokollbereinigung“.
<!-- Version purging and audit log purging are on by default, with different default values for environments with ids higher than **TBD** versus those with ids lower than that value. -->

<!-- ### Overriding the default values with a new configuration {#override} -->

Die standardmäßigen Bereinigungswerte können überschrieben werden, indem eine Konfigurationsdatei deklariert und wie unten beschrieben bereitgestellt wird.

<!-- The reason for this behavior is to clarify the ambiguity over whether the default purge values would take effect once you remove the declaration. -->

### Anwenden einer Konfiguration {#configure-purge}

Deklarieren Sie eine Konfigurationsdatei und stellen Sie sie wie in den folgenden Schritten beschrieben bereit.

>[!NOTE]
>Nachdem Sie den Knoten zur Versionsbereinigung in der Konfigurationsdatei bereitgestellt haben, müssen Sie ihn deklarieren und dürfen ihn nicht entfernen. Wenn Sie dies versuchen, schlägt die Konfigurations-Pipeline fehl.
> 
>Ebenso müssen Sie den Knoten für die Auditprotokollbereinigung nach der Bereitstellung in der Konfigurationsdatei deklarieren und dürfen ihn nicht entfernen.

**1** Erstellen Sie eine Datei mit dem Namen `mt.yaml` oder ähnlich.

**2** Platzieren Sie die Datei unter einem Ordner der obersten Ebene mit dem Namen `config` oder ähnlich, wie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) beschrieben.

**3** Deklarieren Sie Eigenschaften in der Konfigurationsdatei, die Folgendes enthalten:

* einige Eigenschaften oberhalb des Datenknotens – eine Beschreibung finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Eigenschaftswert `kind` sollte *MaintenanceTasks* sein und die Version auf *1* festgelegt werden.

* ein Datenobjekt mit den Objekten `versionPurge` und `auditLogPurge`.

Siehe die Definitionen und Syntax der Objekte `versionPurge` und `auditLogPurge` unten.

Strukturieren Sie die Konfiguration ähnlich wie im folgenden Beispiel:

```
kind: "MaintenanceTasks"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  versionPurge:
    maximumVersions: 15
    maximumAgeDays: 20
    paths: ["/content"]
    minimumVersions: 1
    retainLabelledVersions: false
  auditLogPurge:
    rules:
      - replication:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["Activate", "Deactivate", "Delete", "Test", "Reverse", "Internal Poll"]
      - pages:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["PageCreated", "PageModified", "PageMoved", "PageDeleted", "VersionCreated", "PageRestored", "PageValid", "PageInvalid"]
      - dam:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["ASSET_EXPIRING", "METADATA_UPDATED", "ASSET_EXPIRED", "ASSET_REMOVED", "RESTORED", "ASSET_MOVED", "ASSET_VIEWED", "PROJECT_VIEWED", "PUBLISHED_EXTERNAL", "COLLECTION_VIEWED", "VERSIONED", "ADDED_COMMENT", "RENDITION_UPDATED", "ACCEPTED", "DOWNLOADED", "SUBASSET_UPDATED", "SUBASSET_REMOVED", "ASSET_CREATED", "ASSET_SHARED", "RENDITION_REMOVED", "ASSET_PUBLISHED", "ORIGINAL_UPDATED", "RENDITION_DOWNLOADED", "REJECTED"]
```

Beachten Sie Folgendes, damit die Konfiguration gültig ist:

* Alle Eigenschaften müssen definiert sein. Es gibt keine geerbten Standardwerte.
* Die in den Eigenschaftstabellen unten aufgeführten Typen (Ganzzahlen, Zeichenfolgen, Boolesche Werte usw.) müssen beachtet werden.

**4**: Erstellen Sie eine Konfigurations-Pipeline in Cloud Manager, wie im Artikel [Konfiguration der Pipeline“ ](/help/operations/config-pipeline.md#managing-in-cloud-manager).

### Versionsbereinigung {#version-purge}

>[!NOTE]
>
>AEM Guides-Kundinnen und -Kunden sollten keine Versionsbereinigung konfigurieren.

#### Standardwerte für die Versionsbereinigung {#version-purge-defaults}

<!-- For version purging, environments with an id higher than **TBD** have the following default values: -->

Derzeit ist die Bereinigung nicht standardmäßig aktiviert, aber dies wird sich in Zukunft ändern.

Umgebungen, die nach Aktivierung der standardmäßigen Bereinigung erstellt wurden, haben die folgenden Standardwerte:

* Versionen, die älter als 30 Tage sind, werden entfernt.
* Die letzten fünf Versionen der letzten 30 Tage werden beibehalten.
* Unabhängig von den obigen Regeln wird die neueste Version (zusätzlich zur aktuellen Datei) beibehalten.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

Umgebungen, die vor Aktivierung der standardmäßigen Bereinigung erstellt wurden, haben die unten aufgeführten Standardwerte. Es wird jedoch empfohlen, diese Werte zu verringern, um die Leistung zu optimieren.

* Versionen, die älter als sieben Jahre sind, werden entfernt.
* Alle Versionen der letzten sieben Jahre werden beibehalten.
* Nach sieben Jahren werden andere Versionen als die neueste Version (zusätzlich zur aktuellen Datei) entfernt.

#### Eigenschaften der Versionsbereinigung {#version-purge-properties}

Die zulässigen Eigenschaften sind im Folgenden aufgeführt.

Die Spalten, die *default* angeben, geben die Standardwerte für die Zukunft an, wenn Standardwerte angewendet werden. *TBD* gibt eine Umgebungs-ID an, die noch nicht ermittelt wurde.

| Eigenschaften | Zukünftiger Standard für Umgebungen>TBD | Zukünftiger Standard für Umgebungen&lt;=TBD | Erforderlich | Typ | Werte |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| Pfade | [&quot;/content&quot;] | [&quot;/content&quot;] | Ja | Zeichenfolgen-Array | Gibt an, unter welchen Pfaden Versionen bereinigt werden sollen, wenn neue Versionen erstellt werden. Diese Eigenschaft muss kundenseitig deklariert werden. Es ist jedoch nur der Wert &quot;/content&quot; zulässig. |
| maximumAgeDays | 30 | 2557 (7 Jahre + 2 Schalttage) | Ja | Ganzzahl | Jede Version, die älter als der konfigurierte Wert ist, wird entfernt. Lautet der Wert „0“, wird die Bereinigung nicht auf Basis des Alters der Version durchgeführt. |
| maximumVersions | 5 | 0 (kein Limit) | Ja | Ganzzahl | Jede Version, die älter als die n-te neueste Version ist, wird entfernt. Lautet der Wert „0“, wird die Bereinigung nicht auf Basis der Anzahl der Versionen durchgeführt. |
| minimumVersions | 1 | 1 | Ja | Ganzzahl | Die Mindestanzahl der Versionen, die unabhängig vom Alter beibehalten werden. Es wird immer mindestens eine Version beibehalten. Der Wert muss „1“ oder höher sein. |
| keepLabeledVersion | false | false | Ja | Boolesch | Bestimmt, ob explizit gekennzeichnete Versionen von der Bereinigung ausgeschlossen werden. Für eine bessere Repository-Optimierung wird empfohlen, diesen Wert auf „false“ festzulegen. |


**Interaktion von Eigenschaften**

Die folgenden Beispiele veranschaulichen, wie kombinierte Eigenschaften miteinander interagieren.

Zum Beispiel:

```
maximumAgeDays = 30
maximumVersions = 10
minimumVersions = 2
```

Wenn an Tag 23 elf Versionen vorliegen, wird die älteste Version beim nächsten Ausführen der Bereinigungswartungsaufgabe bereinigt, da die Eigenschaft `maximumVersions` auf den Wert „10“ eingestellt ist.

Wenn an Tag 31 fünf Versionen vorhanden sind, werden nur drei Versionen bereinigt, da die Eigenschaft `minimumVersions` auf den Wert „2“ eingestellt ist.

Zum Beispiel:

```
maximumAgeDays = 30
maximumVersions = 0
minimumVersions = 1
```

Versionen, die noch keine 30 Tage alt sind, werden nicht bereinigt, da die Eigenschaft `maximumVersions` auf den Wert „0“ eingestellt ist.

Eine Version, die älter als 30 Tage ist, wird beibehalten.

### Bereinigung der Auditprotokolle {#audit-purge}

#### Standardwerte für die Auditprotokollbereinigung {#audit-purge-defaults}

<!-- For audit log purging, environments with an id higher than **TBD** have the following default values: -->

Derzeit ist die Bereinigung nicht standardmäßig aktiviert, aber dies wird sich in Zukunft ändern.

Umgebungen, die nach Aktivierung der standardmäßigen Bereinigung erstellt wurden, haben die folgenden Standardwerte:

* Replikations-, DAM-und Seiten-Auditprotokolle, die älter als sieben Tage sind, werden entfernt.
* Alle möglichen Ereignisse werden protokolliert.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

Umgebungen, die vor Aktivierung der standardmäßigen Bereinigung erstellt wurden, haben die unten aufgeführten Standardwerte. Es wird jedoch empfohlen, diese Werte zu verringern, um die Leistung zu optimieren.

* Replikations-, DAM-und Seiten-Auditprotokolle, die älter als sieben Jahre sind, werden entfernt.
* Alle möglichen Ereignisse werden protokolliert.

>[!NOTE]
>Es wird empfohlen, dass Kundinnen und Kunden, die durch gesetzliche Vorschriften verpflichtet sind, nicht bearbeitbare Auditprotokolle zu erstellen, hierfür spezialisierte externe Dienste integrieren.

#### Eigenschaften der Auditprotokollbereinigung {#audit-purge-properties}

Die zulässigen Eigenschaften sind im Folgenden aufgeführt.

Die Spalten, die *default* angeben, geben die Standardwerte für die Zukunft an, wenn Standardwerte angewendet werden. *TBD* gibt eine Umgebungs-ID an, die noch nicht ermittelt wurde.


| Eigenschaften | Zukünftiger Standard für Umgebungen>TBD | Zukünftiger Standard für Umgebungen&lt;=TBD | Erforderlich | Typ | Werte |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| Regeln | - | - | Ja | Objekt | Einer oder mehrere der folgenden Knoten: Replikation, Seiten, DAM. Jeder dieser Knoten definiert Regeln mit den unten aufgeführten Eigenschaften. Alle Eigenschaften müssen deklariert werden. |
| maximumAgeDays | 7 Tage | für alle 2557 (7 Jahre + 2 Schalttage) | Ja | Ganzzahl | Bei Replikation, Seiten oder DAM: die Anzahl der Tage, für die die Auditprotokolle aufbewahrt werden. Auditprotokolle, die älter als der konfigurierte Wert sind, werden gelöscht. |
| contentPath | &quot;/content&quot; | &quot;/content&quot; | Ja | Zeichenfolge | Der Pfad, unter dem die Auditprotokolle für den zugehörigen Typ gelöscht werden. Muss auf &quot;/content&quot; gesetzt sein. |
| Typen | Alle Werte | Alle Werte | Ja | Array der Auflistung | Für **replication** lauten die aufgezählten Werte: Activate, Deactivate, Delete, Test, Reverse, Internal Poll. Für **pages** lauten die aufgezählten Werte: PageCreated, PageModified, PageMoved, PageDeleted, VersionCreated, PageRestoned, PageRolled Out, PageValid, PageInvalid. Für **dam** lauten die aufgezählten Werte: ASSET_EXPIRING, METADATA_UPDATED, ASSET_EXPIRED, ASSET_REMOVED, RESTORED, ASSET_MOVED, ASSET_VIEWED, PROJECT_VIEWED, PUBLISHED_EXTERNAL, COLLECTION_VIEWED, VERSIONED, ADDED_COMMENT, RENDITION_UPDATED, ACCEPTED, DOWNLOADED, SUBASSET_UPDATED, SUBASSET_REMOVED, ASSET_CREATED, ASSET_SHARED, RENDITION_REMOVED, ASSET_PUBLISHED, ORIGINAL_UPDATED, RENDITION_DOWNLOADED, REJECTED. |
