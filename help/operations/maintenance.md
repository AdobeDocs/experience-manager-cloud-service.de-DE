---
title: Wartungsaufgaben in AEM als Cloud-Dienst
description: 'Wartungsaufgaben in AEM als Cloud-Dienst '
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e

---


# Wartungsaufgaben in AEM als Cloud-Dienst

Wartungsaufgaben sind Prozesse, die nach einem Zeitplan ausgeführt werden, um das Repository zu optimieren. Mit AEM als Cloud-Dienst müssen Kunden die operativen Eigenschaften von Wartungsaufgaben nur minimal konfigurieren. Kunden können ihre Ressourcen auf Probleme auf Anwendungsebene konzentrieren, wobei die Infrastrukturvorgänge Adobe überlassen bleiben.

Weitere Informationen zu Wartungsaufgaben finden Sie auf den folgenden Seiten:

* [AEM Maintenance Guide](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [Aufgaben zur Dashboard-Wartung](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## Konfigurieren von Wartungsaufgaben

In früheren Versionen von AEM können Sie Wartungsaufgaben mithilfe der Maintenance-Karte konfigurieren (Tools > Vorgänge > Wartung). Für AEM als Cloud-Dienst ist die Maintenance-Karte nicht mehr verfügbar. Daher sollten Konfigurationen der Quellcodeverwaltung zugewiesen und mithilfe des Cloud-Managers bereitgestellt werden. Adobe verwaltet Wartungsaufgaben, die keine Kundenentscheidung erfordern (z. B. Datastore Garbage Collection), während andere Wartungsaufgaben vom Kunden konfiguriert werden können (siehe folgende Tabelle).

>[!CAUTION]
>
>Adobe behält sich das Recht vor, die Konfigurationseinstellungen für Wartungsaufgaben eines Kunden außer Kraft zu setzen, um Probleme wie Leistungsbeeinträchtigung zu vermeiden.

Die folgende Tabelle zeigt die Wartungsaufgaben, die zum Zeitpunkt der Veröffentlichung von AEM als Cloud-Dienst verfügbar sind.

| Wartungsaufgabe | Wem gehört die Konfiguration | Konfigurieren (optional) |
|---|---|---|
| Datastore-Müllsammlung | Adobe | Nicht zutreffend - vollständig im Besitz von Adobe |
| Versionsbereinigung | Adobe | Adobe ist vollständig im Besitz, aber in Zukunft können Kunden bestimmte Parameter konfigurieren. |
| Bereinigung des Prüfprotokolls | Adobe | Adobe ist vollständig im Besitz, aber in Zukunft können Kunden bestimmte Parameter konfigurieren. |
| Lucene-Binärdateien-Bereinigung | Adobe | Nicht verwendet und daher von Adobe deaktiviert. |
| Ad-hoc-Aufgabenbereinigung | Kunde | Muss in github gemacht werden. <br> Überschreiben Sie den Konfigurationsknoten des Wartungsfensters unter und `/libs` mit `/apps` oder `/conf/global/settings/granite/operations/maintenance/granite_weekly``granite_daily` . Weitere Konfigurationsdetails finden Sie in der Tabelle des Wartungsfensters. <br> Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem Knoten oben einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn `granite_TaskPurgeTask`). <br> Informationen zum Konfigurieren der OSGI-Eigenschaften finden Sie in der Dokumentation zu [AEM 6.5 Maintenance Task](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Workflow-Bereinigung | Kunde | Muss in github gemacht werden. <br> Überschreiben Sie den Konfigurationsknoten des Wartungsfensters unter und `/libs` mit `/apps` oder `/conf/global/settings/granite/operations/maintenance/granite_weekly``granite_daily` . Weitere Konfigurationsdetails finden Sie in der Tabelle des Wartungsfensters. <br> Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem Knoten oben einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn `granite_WorkflowPurgeTask`). <br> Konfigurieren der OSGI-Eigenschaften siehe Dokumentation zu [AEM 6.5 Maintenance Task](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Projekt-Bereinigung | Kunde | Muss in github gemacht werden. <br> Überschreiben Sie den Konfigurationsknoten des Wartungsfensters unter und `/libs` mit `/apps` oder `/conf/global/settings/granite/operations/maintenance/granite_weekly``granite_daily` . Weitere Konfigurationsdetails finden Sie in der Tabelle des Wartungsfensters. <br> Aktivieren Sie die Wartungsaufgabe, indem Sie einen Knoten unter dem oben stehenden Knoten (Name) mit den entsprechenden Eigenschaften hinzufügen `granite_ProjectPurgeTask`. <br> OSGI-Eigenschaften konfigurieren siehe Dokumentation zu [AEM 6.5 Maintenance Task](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

Kunden können die Ausführung der Aufgaben &quot;Workflow-Bereinigung&quot;, &quot;Ad-hoc-Aufgabenbereinigung&quot;und &quot;Projektbereinigung&quot;während des täglichen, wöchentlichen oder monatlichen Wartungsfensters planen. Diese Konfigurationen sollten direkt in der Quellcodeverwaltung bearbeitet werden. Die folgende Tabelle beschreibt die für jedes Fenster verfügbaren Konfigurationsparameter.

<table>
  <tr>
    <th>Konfiguration des Wartungsfensters</th>
    <th>Wem gehört die Konfiguration</th>
    <th>Konfigurationstyp</th>
    <th>Standort</th>
    <th>Beispiel</th>
    <th>Parameter</th>
  </tr>
  <tr>
    <td>Täglich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_daily </code> (die den Knoten in <code>/apps</code> und <code>/libs</code>außer Kraft setzt)</td>
    <td>Siehe Codebeispiel 1 unten</td>
   <td>
    <ul>
    <li><strong>windowSchedule</strong> = daily (dieser Wert sollte nicht geändert werden)</li>
    <li><strong>windowStartTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem Fenster "Tägliche Wartung"verknüpften Wartungsaufgaben mit der Ausführung beginnen sollen.</li>
    <li><strong>windowEndTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden sollen, wenn sie noch nicht abgeschlossen sind.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Wöchentlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_weekly</code> (die den Knoten in <code>/apps</code> und <code>/libs</code>außer Kraft setzt)</td>
    <td>Siehe Codebeispiel 2 unten</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = weekly (dieser Wert sollte nicht geändert werden)</li>
    <li><strong>windowStartTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben ausgeführt werden sollen.</li>
    <li><strong>windowEndTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden sollen, wenn sie noch nicht abgeschlossen sind.</li>
    <li><strong>windowScheduleWeekdays = Array mit 2 Werten von 1-7. z. B. [5,5].</strong> Der erste Wert des Arrays ist der Starttag, an dem der Auftrag geplant wird, und der zweite Wert ist der Endtag, an dem der Auftrag beendet werden soll. Die genaue Uhrzeit des Start- und Enddatums wird durch windowStartTime bzw. windowEndTime bestimmt.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Monatlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_monthly</code> (die den Knoten in <code>/apps</code> und <code>/libs</code>außer Kraft setzt)</td>
    <td>Siehe Codebeispiel 3 unten</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = daily (dieser Wert sollte nicht geändert werden)</li>
    <li><strong>windowStartTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben ausgeführt werden sollen.</li>
    <li><strong>windowEndTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden sollten, wenn sie noch nicht abgeschlossen sind.</li>
    <li><strong>windowScheduleWeekdays = Array mit 2 Werten von 1-7. z. B. [5,5].</strong> Der erste Wert des Arrays ist der Starttag, an dem der Auftrag geplant wird, und der zweite Wert ist der Endtag, an dem der Auftrag beendet werden soll. Die genaue Uhrzeit des Start- und Enddatums wird durch windowStartTime bzw. windowEndTime bestimmt.</li>
    <li><strong>windowFirstLastStartDay - 0/1</strong> 0, um die erste Woche des Monats zu planen, oder 1, um die letzte Woche des Monats zu planen. Wenn kein Wert vorhanden ist, werden Aufträge praktisch jeden Tag gemäß den Regeln von windowScheduleWeekdays jeden Monat geplant.</li>
    </ul> </td> 
  </tr>
</table>

Codebeispiel 1

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

Codebeispiel 2

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

Codebeispiel 3

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
