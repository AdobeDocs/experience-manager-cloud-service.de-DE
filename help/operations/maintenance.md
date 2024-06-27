---
title: Wartungsaufgaben in AEM as a Cloud Service
description: Erfahren Sie mehr über Wartungsaufgaben in AEM as a Cloud Service und deren Konfiguration.
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
feature: Operations
role: Admin
source-git-commit: 4113bb47dee5f3a2c7743f9a79c60654e58cb6bd
workflow-type: tm+mt
source-wordcount: '2106'
ht-degree: 43%

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

Die folgende Tabelle zeigt die verfügbaren Wartungsaufgaben.

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
    <td>Kunde</td>
    <td>Die Versionsbereinigung ist derzeit standardmäßig deaktiviert, die Richtlinie kann jedoch wie im Abschnitt <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks">Wartungsaufgaben für Versionsbereinigung und Auditprotokollbereinigung</a> Abschnitt.<br/><br/>Die Bereinigung wird in Kürze standardmäßig aktiviert, wobei diese Werte überschrieben werden können.<br><br> <!--Alexandru: leave the two line breaks in place, otherwise spacing won't render properly-->
   </td>
  </td>
  </tr>
  <tr>
    <td>Bereinigung von Prüfprotokollen</td>
    <td>Kunde</td>
    <td>Die Bereinigung des Auditprotokolls ist derzeit standardmäßig deaktiviert, die Richtlinie kann jedoch wie im Abschnitt <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks">Wartungsaufgaben für Versionsbereinigung und Auditprotokollbereinigung</a> Abschnitt.<br/><br/>Die Bereinigung wird in Kürze standardmäßig aktiviert, wobei diese Werte überschrieben werden können.<br><br> <!--Alexandru: leave the two line breaks in place, otherwise spacing won't render properly-->
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
    <td>Kunde</td>
    <td>
    <p>Das muss in Git geschehen. Überschreiben Sie den vorkonfigurierten Konfigurationsknoten des Wartungsfensters unter <code>/libs</code> durch Erstellen von Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> oder <code>granite_monthly</code>.</p>
    <p>Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster. Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten hinzufügen. Benennen Sie ihn <code>granite_TaskPurgeTask</code>, wobei Sie das Attribut <code>sling:resourceType</code> auf <code>granite/operations/components/maintenance/task</code> und das Attribut <code>granite.maintenance.name</code> auf <code>TaskPurge</code> setzen. Konfigurieren Sie die OSGi-Eigenschaften. Eine Liste der Eigenschaften finden Sie unter <code>com.adobe.granite.taskmanagement.impl.purge.TaskPurgeMaintenanceTask</code>.</p>
  </td>
  </tr>
    <tr>
    <td>Workflow-Bereinigung</td>
    <td>Kunde</td>
    <td>
    <p>Das muss in Git geschehen. Überschreiben Sie den Standardkonfigurationsknoten des Wartungsfensters unter <code>/libs</code>, indem Sie Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> oder <code>granite_monthly</code> erstellen. Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster.</p>
    <p>Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn <code>granite_WorkflowPurgeTask</code>). Informationen zum Konfigurieren der OSGi-Eigenschaften finden Sie in der <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html?lang=de#regular-purging-of-workflow-instances">AEM 6.5-Dokumentation zu Wartungsaufgaben</a>.</p>
  </td>
  </tr>
  <tr>
    <td>Projektbereinigung</td>
    <td>Kunde</td>
    <td>
    <p>Das muss in Git geschehen. Überschreiben Sie den Standardkonfigurationsknoten des Wartungsfensters unter <code>/libs</code>, indem Sie Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> oder <code>granite_monthly</code> erstellen. Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster.</p>
    <p>Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn <code>granite_ProjectPurgeTask</code>). Siehe die Liste der OSGi-Eigenschaften unter „Bereinigungskonfiguration von Adobe-Projekten“.</p>
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
    <td>Kunde</td>
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
    <td>Kunde</td>
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
    <td>Kunde</td>
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

Durch das Bereinigen von Versionen und des Auditprotokolls wird die Größe des Repositorys verringert und in einigen Szenarien kann die Leistung verbessert werden.

>[!NOTE]
>
>Adobe empfiehlt Kunden, keine Versionsbereinigung zu konfigurieren.

### Standardwerte {#defaults}

Derzeit ist die Bereinigung nicht standardmäßig aktiviert, aber dies wird sich in Zukunft ändern. Umgebungen, die erstellt wurden, bevor die standardmäßige Bereinigung aktiviert wurde, haben einen konservativeren Schwellenwert, sodass das Bereinigen nicht unerwartet erfolgt. Weitere Informationen zur standardmäßigen Bereinigungsrichtlinie finden Sie in den Abschnitten Versionsbereinigung und Auditprotokollbereinigung unten.
<!-- Version purging and audit log purging are on by default, with different default values for environments with ids higher than **TBD** versus those with ids lower than that value. -->

<!-- ### Overriding the default values with a new configuration {#override} -->

Die standardmäßigen Bereinigungswerte können überschrieben werden, indem eine Konfigurationsdatei deklariert und wie unten beschrieben bereitgestellt wird.

<!-- The reason for this behavior is to clarify the ambiguity over whether the default purge values would take effect once you remove the declaration. -->

### Anwenden einer Konfiguration {#configure-purge}

Deklarieren Sie eine Konfigurationsdatei und stellen Sie sie wie in den folgenden Schritten beschrieben bereit.

>[!NOTE]
>Nachdem Sie den Knoten zur Versionsbereinigung in der Konfigurationsdatei bereitgestellt haben, müssen Sie ihn deklarieren und nicht entfernen. Die Konfigurations-Pipeline schlägt fehl, wenn Sie dies versuchen.
> 
>Ebenso müssen Sie den Bereinigungsknoten für das Audit-Protokoll nach der Bereitstellung in der Konfigurationsdatei deklarieren und nicht entfernen.

**1** - erstellen Sie die folgende Ordner- und Dateistruktur im Ordner der obersten Ebene Ihres Projekts in Git:

```
config/
     mt.yaml
```

**2** - Deklarieren Sie Eigenschaften in der Konfigurationsdatei, die Folgendes enthalten:

* eine &quot;kind&quot;-Eigenschaft mit dem Wert &quot;MaintenanceTasks&quot;.
* eine Eigenschaft &quot;version&quot;(derzeit ist es Version 1).
* ein optionales &quot;metadata&quot;-Objekt mit der Eigenschaft `envTypes` mit einer kommagetrennten Liste des Umgebungstyps (dev, stage, prod), für den diese Konfiguration gültig ist. Wenn kein Metadatenobjekt deklariert wird, ist die Konfiguration für alle Umgebungstypen gültig.
* ein Datenobjekt mit `versionPurge` und `auditLogPurge` Objekte.

Siehe Definitionen und Syntax der `versionPurge` und `auditLogPurge` Objekte darunter.

Sie sollten die Konfiguration ähnlich wie im folgenden Beispiel strukturieren:

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

>[!NOTE]
>Sie können `yq` , um die YAML-Formatierung Ihrer Konfigurationsdatei lokal zu überprüfen (z. B. `yq mt.yaml`).

**3** - Konfigurieren Sie die Konfigurations-Pipelines für Nicht-Produktion- und Produktionsumgebungen.

Rapid Development Environments (RDEs) unterstützen keine Bereinigung. Erstellen Sie für andere Umgebungstypen in Produktionsprogrammen (ohne Sandbox-Programme) eine zielgerichtete Bereitstellungskonfigurationspipeline in Cloud Manager.

Siehe [Konfigurieren von Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) für weitere Details.

### Versionsbereinigung {#version-purge}

>[!NOTE]
>
>Adobe empfiehlt Kunden, keine Versionsbereinigung zu konfigurieren.

#### Standardwerte für Versionsbereinigung {#version-purge-defaults}

<!-- For version purging, environments with an id higher than **TBD** have the following default values: -->

Derzeit ist die Bereinigung nicht standardmäßig aktiviert, aber dies wird sich in Zukunft ändern.

Umgebungen, die erstellt wurden, nachdem die standardmäßige Bereinigung aktiviert wurde, haben die folgenden Standardwerte:

* Versionen, die älter als 30 Tage sind, werden entfernt.
* Die letzten fünf Versionen der letzten 30 Tage werden beibehalten.
* Unabhängig von den obigen Regeln wird die neueste Version (zusätzlich zur aktuellen Datei) beibehalten.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

Umgebungen, die erstellt wurden, bevor die standardmäßige Bereinigung aktiviert wurde, haben die folgenden Standardwerte. Es wird jedoch empfohlen, diese Werte zu senken, um die Leistung zu optimieren.

* Versionen, die älter als 7 Jahre sind, werden entfernt.
* Alle Versionen der letzten 7 Jahre werden aufbewahrt.
* Nach 7 Jahren werden andere Versionen als die neueste Version (zusätzlich zur aktuellen Datei) entfernt.

#### Eigenschaften für Versionsbereinigung {#version-purge-properties}

Die zulässigen Eigenschaften sind unten aufgeführt.

Die Spalten, die *default* die Standardwerte für die Zukunft angeben, wenn Standardwerte angewendet werden; *TBD* gibt eine Umgebungs-ID an, die noch nicht ermittelt wurde.

| Eigenschaften | zukünftiger Standard für envs>TBD | zukünftige Standardeinstellung für envs&lt;=TBD | erforderlich | Typ | Werte |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| Pfade | [&quot;/content&quot;] | [&quot;/content&quot;] | Ja | Zeichenfolgen-Array | Gibt an, unter welchen Pfaden Versionen beim Erstellen neuer Versionen gelöscht werden sollen.  Kunden müssen diese Eigenschaft deklarieren, doch der einzig zulässige Wert ist &quot;/content&quot;. |
| maximumAgeDays | 30 | 2557 (7 Jahre + 2 Schalttage) | Ja | Ganzzahl | Jede Version, die älter als der konfigurierte Wert ist, wird entfernt. Wenn der Wert 0 beträgt, wird die Bereinigung nicht basierend auf dem Alter der Version durchgeführt. |
| maximumVersions | 5 | 0 (keine Begrenzung) | Ja | Ganzzahl | Jede Version, die älter als die n. neueste Version ist, wird entfernt. Wenn der Wert 0 beträgt, wird die Bereinigung nicht basierend auf der Anzahl der Versionen durchgeführt. |
| minimumVersions | 1 | 1 | Ja | Ganzzahl | Die Mindestanzahl der Versionen, die unabhängig vom Alter beibehalten werden. Beachten Sie, dass immer mindestens 1 Version beibehalten wird. Der Wert muss 1 oder höher sein. |
| keepLabeledVersion | Falsch | Falsch | Ja | Boolesch | Bestimmt, ob explizit gekennzeichnete Versionen von der Bereinigung ausgeschlossen werden. Für eine bessere Repository-Optimierung wird empfohlen, diesen Wert auf false festzulegen. |


**Eigenschafteninteraktionen**

Die folgenden Beispiele veranschaulichen die Interaktion von Eigenschaften bei Kombination.

Beispiel:

```
maximumAgeDays = 30
maximumVersions = 10
minimumVersions = 2
```

Wenn am 23. Tag 11 Versionen vorliegen, wird die älteste Version beim nächsten Ausführen der Bereinigungs-Wartungsaufgabe bereinigt, da die Variable `maximumVersions` -Eigenschaft auf 10 festgelegt ist.

Wenn an Tag 31 fünf Versionen vorhanden sind, werden nur 3 seit der `minimumVersions` -Eigenschaft auf 2 festgelegt ist.

Beispiel:

```
maximumAgeDays = 30
maximumVersions = 0
minimumVersions = 1
```

Seit der Variablen `maximumVersions` -Eigenschaft auf 0 gesetzt.

Eine Version, die älter als 30 Tage ist, wird beibehalten.

### Bereinigung von Prüfprotokollen {#audit-purge}

#### Standardwerte für die Auditprotokollbereinigung {#audit-purge-defaults}

<!-- For audit log purging, environments with an id higher than **TBD** have the following default values: -->

Derzeit ist die Bereinigung nicht standardmäßig aktiviert, aber dies wird sich in Zukunft ändern.

Umgebungen, die erstellt wurden, nachdem die standardmäßige Bereinigung aktiviert wurde, haben die folgenden Standardwerte:

* Replikations-, DAM- und Seitenprüfungsprotokolle, die älter als 7 Tage sind, werden entfernt.
* Alle möglichen Ereignisse werden protokolliert.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

Umgebungen, die erstellt wurden, bevor die standardmäßige Bereinigung aktiviert wurde, haben die folgenden Standardwerte. Es wird jedoch empfohlen, diese Werte zu senken, um die Leistung zu optimieren.

* Replikations-, DAM- und Seitenprüfprotokolle, die älter als 7 Jahre sind, werden entfernt.
* Alle möglichen Ereignisse werden protokolliert.

>[!NOTE]
>Es wird empfohlen, dass Kunden, die über regulatorische Anforderungen verfügen, um nicht bearbeitbare Prüfprotokolle zu erstellen, in spezialisierte externe Dienste integrieren.

#### Eigenschaften zur Bereinigung des Auditprotokolls {#audit-purge-properties}

Die zulässigen Eigenschaften sind unten aufgeführt.

Die Spalten, die *default* die Standardwerte für die Zukunft angeben, wenn Standardwerte angewendet werden; *TBD* gibt eine Umgebungs-ID an, die noch nicht ermittelt wurde.


| Eigenschaften | zukünftiger Standard für envs>TBD | zukünftige Standardeinstellung für envs&lt;=TBD | erforderlich | Typ | Werte |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| Regeln | - | - | Ja | Objekt | Einer oder mehrere der folgenden Knoten: Replikation, Seiten, dam. Jeder dieser Knoten definiert Regeln mit den folgenden Eigenschaften. Alle Eigenschaften müssen deklariert werden. |
| maximumAgeDays | 7 Tage | für alle 2557 (7 Jahre + 2 Schalttage) | Ja | integer | Bei Replikation, Seiten oder DAM: die Anzahl der Tage, in denen die Prüfprotokolle aufbewahrt werden. Auditprotokolle, die älter als der konfigurierte Wert sind, werden gelöscht. |
| contentPath | &quot;/content&quot; | &quot;/content&quot; | Ja | Zeichenfolge | Der Pfad, unter dem die Prüfprotokolle für den zugehörigen Typ gelöscht werden. Muss auf &quot;/content&quot;gesetzt sein. |
| Typen | alle Werte | alle Werte | Ja | Array der Auflistung | Für **Replikation**, lauten die aufgezählten Werte: Aktivieren, Deaktivieren, Löschen, Test, Umkehren, Interne Umfrage. Für **pages**, lauten die aufgezählten Werte: PageCreated, PageModified, PageMoved, PageDeleted, VersionCreated, PageRestoned, PageRolled Out, PageValid, PageInvalid. Für **dam**, lauten die aufgezählten Werte: ASSET_EXPIRING, METADATA_UPDATED, ASSET_EXPIRED, ASSET_REMOVED, RESTORED, ASSET_MOVED, ASSET_VIEWED, PROJECT_VIEWED, PUBLISHED_EXTERNAL, COLLECTION_VIEWED, VERSIONED, ADDED_COMMENT, RENDITION AKTUALISIERT, AKZEPTIERT, HERUNTERGELADEN, SUBASSET_UPDATED, SUBASSET_REMOVED, ASSET_CREATED, ASSET_SHARED, RENDITION_REMOVED, ASSET_PUBLISHED, ORIGINAL_UPDATED, RENDITION_DOWNLOADED, REJECTED. |
