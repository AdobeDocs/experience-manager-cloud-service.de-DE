---
title: Maintenance-Aufgaben in AEM als Cloud Service
description: 'Maintenance-Aufgaben in AEM als Cloud Service '
translation-type: tm+mt
source-git-commit: c3af507716ef60541ecca8dafb797651e8ece9d3
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 2%

---


# Maintenance-Aufgaben in AEM als Cloud Service

Aufgaben zur Wartung sind Prozesse, die planmäßig ausgeführt werden, um das Repository zu optimieren. Bei AEM als Cloud Service ist die Konfiguration der Betriebseigenschaften von Wartungs-Aufgaben minimal. Die Kunden können ihre Ressourcen auf Anwendungsfälle konzentrieren und die Infrastrukturvorgänge der Adobe überlassen.

Weitere Informationen zu Aufgaben der Wartung finden Sie auf den folgenden Seiten:

* [AEM](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [Operations Dashboard Maintenance Aufgaben](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## Aufgaben zur Wartung konfigurieren

In früheren Versionen von AEM können Sie die Maintenance-Aufgaben mithilfe der Maintenance-Karte konfigurieren (Tools > Vorgänge > Wartung). Bei AEM als Cloud Service ist die Maintenance-Karte nicht mehr verfügbar. Daher sollten die Konfigurationen der Quellcodeverwaltung unterliegen und mithilfe von Cloud Manager bereitgestellt werden. Adobe verwaltet Aufgaben, die keine Kundenentscheidung erfordern (z. B. Datastore Garbage Collection), während andere Aufgaben der Wartung vom Kunden konfiguriert werden können (siehe folgende Tabelle).

>[!CAUTION]
>
>Adobe behält sich das Recht vor, die Konfigurationseinstellungen der Aufgabe für die Instandhaltung außer Kraft zu setzen, um Probleme wie Leistungsbeeinträchtigung zu vermeiden.

Die folgende Tabelle zeigt die Aufgaben zur Wartung, die zum Zeitpunkt der Veröffentlichung von AEM als Cloud Service verfügbar sind.

| Aufgabe der Wartung | Wem gehört die Konfiguration | Konfigurieren (optional) |
|---|---|---|
| Datastore-Müllsammlung | Adobe | N/A - Eigentum der Adobe |
| Versionsbereinigung | Adobe | Voll im Besitz der Adobe, aber in Zukunft werden die Kunden in der Lage sein, bestimmte Parameter zu konfigurieren. |
| Bereinigung des Prüfprotokolls | Adobe | Voll im Besitz der Adobe, aber in Zukunft werden die Kunden in der Lage sein, bestimmte Parameter zu konfigurieren. |
| Lucene-Binärdateien-Bereinigung | Adobe | Nicht verwendet und daher durch Adobe deaktiviert. |
| Ad-hoc-Aufgaben-Bereinigung | Kunde | Muss in github gemacht werden. <br> Überschreiben Sie den Konfigurationsknoten im vordefinierten Wartungsfenster `/libs` durch Erstellen von Eigenschaften im Ordner `/apps/settings/granite/operations/maintenance/granite_weekly` oder `granite_daily`. Weitere Konfigurationsdetails finden Sie in der Tabelle des Wartungsfensters. <br> Aktivieren Sie die Maintenance-Aufgabe, indem Sie unter dem Knoten oben einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn `granite_TaskPurgeTask`). <br> Die OSGI-Eigenschaften konfigurieren finden Sie in der Dokumentation zur [AEM 6.5 Maintenance Aufgabe](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Workflow-Bereinigung | Kunde | Muss in github gemacht werden. <br> Überschreiben Sie den Konfigurationsknoten im vordefinierten Wartungsfenster, `/libs` indem Sie Eigenschaften im Ordner`/apps/settings/granite/operations/maintenance/granite_weekly` oder `granite_daily`erstellen. Weitere Konfigurationsdetails finden Sie in der Tabelle des Wartungsfensters. <br> Aktivieren Sie die Maintenance-Aufgabe, indem Sie unter dem Knoten oben einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn `granite_WorkflowPurgeTask`). <br> OSGI-Eigenschaften konfigurieren siehe Dokumentation zur [AEM 6.5 Maintenance Aufgabe](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Projekt-Bereinigung | Kunde | Muss in github gemacht werden. <br> Überschreiben Sie den Konfigurationsknoten im vordefinierten Wartungsfenster `/libs` durch Erstellen von Eigenschaften im Ordner `/apps/settings/granite/operations/maintenance/granite_weekly` oder `granite_daily`. Weitere Konfigurationsdetails finden Sie in der Tabelle des Wartungsfensters. <br> Aktivieren Sie die Maintenance-Aufgabe, indem Sie einen Knoten unter dem oben stehenden Knoten (Name) mit den entsprechenden Eigenschaften hinzufügen `granite_ProjectPurgeTask`. <br> OSGI-Eigenschaften konfigurieren siehe Dokumentation zur [AEM 6.5 Maintenance Aufgabe](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

Die Kunden können die Ausführung der einzelnen Aufgaben für Workflow-Bereinigung, Ad-hoc-Aufgaben-Bereinigung und Projektbereinigung während des täglichen, wöchentlichen oder monatlichen Wartungsfensters planen. Diese Konfigurationen sollten direkt in der Quellcodeverwaltung bearbeitet werden. Die folgende Tabelle beschreibt die für jedes Fenster verfügbaren Konfigurationsparameter.

<table>
  <tr>
    <th>Konfiguration des Wartungsfensters</th>
    <th>Wem gehört die Konfiguration</th>
    <th>Konfigurationstyp</th>
    <th>Ort</th>
    <th>Beispiel</th>
    <th>Parameter</th>
  </tr>
  <tr>
    <td>Täglich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td><code>/apps/settings/granite/operations/maintenance/granite_daily </code></td>
    <td>Siehe Codebeispiel 1 unten</td>
   <td>
    <ul>
    <li><strong>windowSchedule</strong> = daily (dieser Wert sollte nicht geändert werden)</li>
    <li><strong>windowStartTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem täglichen Wartungsfenster verknüpften Aufgaben mit der Ausführung beginnen sollen.</li>
    <li><strong>windowEndTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem täglichen Wartungsfenster verknüpften Maintenance-Aufgaben die Ausführung beenden sollen, wenn sie noch nicht abgeschlossen sind.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Wöchentlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td><code>/apps/settings/granite/operations/maintenance/granite_weekly</code></td>
    <td>Siehe Codebeispiel 2 unten</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = weekly (dieser Wert sollte nicht geändert werden)</li>
    <li><strong>windowStartTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem wöchentlichen Wartungsfenster verknüpften Maintenance-Aufgaben mit der Ausführung beginnen sollen.</li>
    <li><strong>windowEndTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem wöchentlichen Wartungsfenster verknüpften Maintenance-Aufgaben die Ausführung beenden sollen, wenn sie noch nicht abgeschlossen sind.</li>
    <li><strong>windowScheduleWeekdays = Array mit 2 Werten von 1-7. z. B. [5,5].</strong> Der erste Wert des Arrays ist der Tag des Beginns, an dem der Auftrag geplant wird, und der zweite Wert ist der Endtag, an dem der Auftrag beendet wird. Die genaue Uhrzeit des Beginns und des Endes wird durch windowStartTime bzw. windowEndTime bestimmt.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Monatlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td><code>/apps/settings/granite/operations/maintenance/granite_monthly</code></td>
    <td>Siehe Codebeispiel 3 unten</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = daily (dieser Wert sollte nicht geändert werden)</li>
    <li><strong>windowStartTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem monatlichen Wartungsfenster verknüpften Aufgaben mit der Ausführung beginnen sollen.</li>
    <li><strong>windowEndTime</strong> = HH:MM unter Verwendung als 24-Stunden-Uhr. Definiert, wann die mit dem monatlichen Wartungsfenster verknüpften Aufgaben nicht mehr ausgeführt werden sollten, wenn sie noch nicht abgeschlossen sind.</li>
    <li><strong>windowScheduleWeekdays = Array mit 2 Werten von 1-7. z. B. [5,5].</strong> Der erste Wert des Arrays ist der Tag des Beginns, an dem der Auftrag geplant wird, und der zweite Wert ist der Endtag, an dem der Auftrag beendet wird. Die genaue Uhrzeit des Beginns und des Endes wird durch windowStartTime bzw. windowEndTime bestimmt.</li>
    <li><strong>windowFirstLastStartDay - 0/1</strong> 0, um die erste Woche des Monats zu planen, oder 1, um die letzte Woche des Monats zu planen. Wenn kein Wert vorhanden ist, werden Aufträge praktisch jeden Tag gemäß den Regeln von windowScheduleWeekdays jeden Monat terminiert.</li>
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
