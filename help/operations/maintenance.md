---
title: Wartungsaufgaben in AEM as a Cloud Service
description: Wartungsaufgaben in AEM as a Cloud Service
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
source-git-commit: cd48b78383974027d8980397632c395a5958edbf
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 75%

---

# Wartungsaufgaben in AEM as a Cloud Service

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="Wartungsaufgaben"
>abstract="Wartungsaufgaben sind Prozesse, die planmäßig ausgeführt werden, um das Repository zu optimieren. Bei AEM as a Cloud Service ist der Kundenaufwand der Konfiguration von Betriebseigenschaften für Wartungsaufgaben minimal. Kunden können ihre Ressourcen auf Angelegenheiten in der Anwendungsebene konzentrieren und die Infrastrukturvorgänge Adobe überlassen."

Wartungsaufgaben sind Prozesse, die planmäßig ausgeführt werden, um das Repository zu optimieren. Bei AEM as a Cloud Service ist der Kundenaufwand der Konfiguration von Betriebseigenschaften für Wartungsaufgaben minimal. Kunden können ihre Ressourcen auf Angelegenheiten in der Anwendungsebene konzentrieren und die Infrastrukturvorgänge Adobe überlassen.

## Konfigurieren von Wartungsaufgaben

In früheren Versionen von AEM konnten Sie Wartungsaufgaben mithilfe der Wartungskarte konfigurieren (Tools > Vorgänge > Wartung). Bei AEM as a Cloud Service ist die Wartungskarte nicht mehr vorhanden. Daher sollten Konfigurationen an die Quell-Code-Verwaltung übertragen und mithilfe von Cloud Manager bereitgestellt werden. Adobe verwaltet Wartungsaufgaben, deren Einstellungen von Kunden nicht konfiguriert werden können (z. B. Datenspeicherbereinigung, Auditprotokollbereinigung, Versionsbereinigung). Andere Wartungsaufgaben können von Kunden konfiguriert werden, wie in der folgenden Tabelle beschrieben.

>[!CAUTION]
>
>Adobe behält sich das Recht vor, Konfigurationseinstellungen für Wartungsaufgaben eines Kunden außer Kraft zu setzen, um Probleme wie Leistungsbeeinträchtigungen zu verhindern.

Die folgende Tabelle zeigt die Wartungsaufgaben, die zum Zeitpunkt der Veröffentlichung von AEM as a Cloud Service verfügbar sind.

<!--| Maintenance Task | Who owns the configuration | How to configure (optional)  |
|---|---|---|
| Datastore garbage collection | Adobe | N/A - fully Adobe owned |
| Version Purge | Adobe | Fully owned by Adobe, but in the future, customers will be able to configure certain parameters. |
| Audit Log Purge  | Adobe | Fully owned by Adobe, but in the future, customers will be able to configure certain parameters. |
| Lucene Binaries Cleanup | Adobe | Unused and therefore disabled by Adobe. |
| Ad-hoc Task Purge | Customer | Must be done in git. <br> Override the out-of-the-box Maintenance window configuration node under `/libs` by creating properties under the the folder `/apps/settings/granite/operations/maintenance/granite_weekly` or `granite_daily`. See the Maintenance Window table below for additional configuration details. <br> Enable the maintenance task by adding another node under the node above (name it `granite_TaskPurgeTask`) with the appropriate properties. <br> Configure the OSGI properties see the [AEM 6.5 Maintenance Task documentation](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)|
| Workflow Purge | Customer |  Must be done in git. <br> Override the out-of-the-box Maintenance window configuration node under `/libs` by creating properties under the the folder`/apps/settings/granite/operations/maintenance/granite_weekly` or `granite_daily`. See the Maintenance Window table below for additional configuration details. <br> Enable the maintenance task by adding another node under the node above (name it `granite_WorkflowPurgeTask`) with the appropriate properties. <br> Configure the OSGI properties see [AEM 6.5 Maintenance Task documentation](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Project Purge | Customer |  Must be done in git. <br> Override the out-of-the-box Maintenance window configuration node under `/libs` by creating properties under the the folder `/apps/settings/granite/operations/maintenance/granite_weekly` or `granite_daily`. See the Maintenance Window table below for additional configuration details. <br> Enable the maintenance task by adding a node under the node above (name it `granite_ProjectPurgeTask`) with the appropriate properties. <br> Configure OSGI properties see [AEM 6.5 Maintenance Task documentation](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

Customers can schedule each of the Workflow Purge, Ad-hoc Task Purge and Project Purge Maintenance tasks to be executed during the daily, weekly, or monthly maintenance windows. These configurations should be edited directly in source control. The table below describes the configuration parameters available for each of the window. Also, see the locations and code samples provided after the table.-->

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
    <td>Adobe</td>
    <td>Damit die Autorenstufe weiterhin leistungsfähig bleibt, müssen ältere Versionen jedes Inhalts unter dem <code>/content</code> -Knoten des Repositorys werden gemäß folgendem Verhalten gelöscht:<br><ol>
  <li>Versionen, die älter als 30 Tage sind, werden entfernt</li>
  <li>Die letzten 5 Versionen der letzten 30 Tage werden beibehalten.</li>
  <li>Unabhängig von den obigen Regeln wird die neueste Version beibehalten.</li>
</ol><br>HINWEIS: das oben beschriebene Verhalten wird ab dem 14. März 2022 für neue Umgebungen erzwungen und für bestehende Umgebungen (die vor dem 14. März 2022 erstellt wurden) am 21. April 2022 erzwungen.</td>
  </td>
  </tr>
  <tr>
    <td>Bereinigung von Prüfprotokollen</td>
    <td>Adobe</td>
    <td>Damit die Autorenstufe weiterhin leistungsfähig bleibt, sollten ältere Prüfprotokolle unter der <code>/content</code> -Knoten des Repositorys werden gemäß folgendem Verhalten gelöscht:<br><ol>
  <li>Für die Replikationsprüfung werden Prüfprotokolle entfernt, die älter als 3 Tage sind</li>
  <li>Bei der DAM (Assets)-Prüfung werden Prüfprotokolle entfernt, die älter als 30 Tage sind</li>
  <li>Für die Seitenprüfung werden Protokolle entfernt, die älter als 3 Tage sind.<br></li>
</ol><br>HINWEIS: das oben beschriebene Verhalten wird ab dem 14. März 2022 für neue Umgebungen erzwungen und für bestehende Umgebungen (die vor dem 14. März 2022 erstellt wurden) am 21. April 2022 erzwungen.</td>
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
    <p>Muss in Git erfolgen. Überschreiben Sie den Konfigurationsknoten des vordefinierten Wartungsfensters unter <code>/libs</code> durch Erstellen von Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> oder <code>granite_daily</code>.</p>
    <p>Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster.  Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn <code>granite_TaskPurgeTask</code>). Informationen zum Konfigurieren der OSGi-Eigenschaften finden Sie unter <a href="https://helpx.adobe.com/de/experience-manager/kb/AEM6-Maintenance-Guide.html">AEM 6.5 Dokumentation zu Wartungsaufgaben</a>.</p>
  </td>
  </tr>
    <tr>
    <td>Workflow-Bereinigung</td>
    <td>Kunde</td>
    <td>
    <p>Muss in Git erfolgen. Überschreiben Sie den Konfigurationsknoten des vordefinierten Wartungsfensters unter <code>/libs</code> durch Erstellen von Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> oder <code>granite_daily</code>. Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster.</p>
    <p> Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn <code>granite_WorkflowPurgeTask</code>). Informationen zum Konfigurieren der OSGi-Eigenschaften finden Sie unter <a href="https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html">AEM 6.5 Dokumentation zu Wartungsaufgaben</a>.</p>
  </td>
  </tr>
  <tr>
    <td>Projektbereinigung</td>
    <td>Kunde</td>
    <td>
    <p>Muss in Git erfolgen. Überschreiben Sie den Konfigurationsknoten des vordefinierten Wartungsfensters unter <code>/libs</code> durch Erstellen von Eigenschaften im Ordner <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> oder <code>granite_daily</code>. Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster.</p>
    <p> Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn <code>granite_ProjectPurgeTask</code>). Informationen zum Konfigurieren der OSGi-Eigenschaften finden Sie unter <a href="https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html">AEM 6.5 Dokumentation zu Wartungsaufgaben</a>.</p>
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
    <p><strong>windowScheduleWeekdays= Array von 2 Werten von 1–7 (z. B. [5,5])</strong> Der erste Wert des Arrays ist der Starttag, an dem der Auftrag geplant wird, und der zweite Wert ist der Endtag, an dem der Auftrag gestoppt wird. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben.</p>
    </td>
  </tr>
  <tr>
    <td>Monatlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td>
    <p><strong>windowSchedule=daily</strong> (dieser Wert sollte nicht geändert werden)</p>
    <p><strong>windowStartTime = HH:MM</strong> unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.</p>
    <p><strong>windowEndTime = HH:MM</strong> unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.</p>
    <p><strong>windowScheduleWeekdays= Array von 2 Werten von 1–7 (z. B. [5,5])</strong> Der erste Wert des Arrays ist der Starttag, an dem der Auftrag geplant wird, und der zweite Wert ist der Endtag, an dem der Auftrag gestoppt wird. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0, um in der ersten Woche des Monats zu planen, oder 1, um in der letzten Woche des Monats zu planen. Wenn kein Wert angegeben ist, werden Aufträge praktisch jeden Tag terminiert (wie von „windowScheduleWeekdays“ jeden Monat gesteuert).</p>
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
