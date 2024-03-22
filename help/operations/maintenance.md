---
title: Wartungsaufgaben in AEM as a Cloud Service
description: Erfahren Sie mehr über Wartungsaufgaben in AEM as a Cloud Service und deren Konfiguration.
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
source-git-commit: 4ac5ec2a2b8da90820734e4fc06c084c810c0724
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 91%

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

Die folgende Tabelle zeigt die Wartungsaufgaben, die zum Zeitpunkt der Veröffentlichung von AEM as a Cloud Service verfügbar sind.

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
    <td>Für bestehende Umgebungen (die vor dem 15. April 2024 erstellt wurden) ist die Bereinigung deaktiviert und wird in Zukunft aktiviert, wobei der Standardwert 7 Jahre beträgt. Kunden können ihn mit niedrigeren benutzerdefinierten Werten konfigurieren (z. B. 30 Tage).<br><br> <!--Alexandru: leave the two line breaks in place, otherwise spacing won't render properly-->Für neue Umgebungen (die ab dem Dienstag, 15. April 2024 erstellt wurden) ist die Bereinigung standardmäßig mit den unten stehenden Werten aktiviert, wobei Kundinnen und Kunden benutzerdefinierte Werte konfigurieren können.
     <ol>
       <li>Versionen, die älter als 30 Tage sind, werden entfernt</li>
       <li>Die letzten 5 Versionen der letzten 30 Tage werden beibehalten</li>
       <li>Unabhängig von den obigen Regeln wird die neueste Version beibehalten.</li>
       <br>Es wird empfohlen, dass Kunden, die durch gesetzliche Vorschriften verpflichtet sind, die Seiten einer Website genau so wiederzugeben, wie sie an einem bestimmten Datum erschienen sind, hierfür spezialisierte externe Dienste integrieren.
     </ol></td>
  </td>
  </tr>
  <tr>
    <td>Bereinigung von Prüfprotokollen</td>
    <td>Adobe</td>
    <td>Für bestehende Umgebungen (die vor dem 15. April 2024 erstellt wurden) ist die Bereinigung deaktiviert und wird in Zukunft aktiviert, wobei der Standardwert 7 Jahre beträgt. Kunden können ihn mit niedrigeren benutzerdefinierten Werten konfigurieren (z. B. 30 Tage).<br><br> <!-- See above for the two line breaks -->Für neue Umgebungen (die ab April 2024 erstellt wurden) ist die Bereinigung standardmäßig unter der Variablen <code>/content</code> Knoten des Repositorys gemäß folgendem Verhalten:
     <ol>
       <li>Für die Replikationsprüfung werden Prüfprotokolle entfernt, die älter als 3 Tage sind</li>
       <li>Bei der DAM (Assets)-Prüfung werden Prüfprotokolle entfernt, die älter als 30 Tage sind</li>
       <li>Für die Seitenprüfung werden Protokolle entfernt, die älter als 3 Tage sind.</li>
       <br>Es wird empfohlen, dass Kunden, die durch gesetzliche Vorschriften verpflichtet sind, nicht bearbeitbare Prüfprotokolle zu erstellen, hierfür spezialisierte externe Dienste integrieren.
     </ol></td>
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
