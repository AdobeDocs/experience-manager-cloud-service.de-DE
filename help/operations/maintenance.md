---
title: Wartungsaufgaben in AEM as a Cloud Service
description: Wartungsaufgaben in AEM as a Cloud Service
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
translation-type: tm+mt
source-git-commit: c7e954e3ed49d6189d050b2c33c04a9266853758
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 85%

---

# Wartungsaufgaben in AEM as a Cloud Service

Wartungsaufgaben sind Prozesse, die planmäßig ausgeführt werden, um das Repository zu optimieren. Bei AEM as a Cloud Service ist der Kundenaufwand der Konfiguration von Betriebseigenschaften für Wartungsaufgaben minimal. Kunden können ihre Ressourcen auf Angelegenheiten in der Anwendungsebene konzentrieren und die Infrastrukturvorgänge Adobe überlassen.

Weitere Informationen zu Wartungsaufgaben finden Sie auf den folgenden Seiten:

* [AEM-Wartungsleitfaden](https://helpx.adobe.com/de/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [Vorgangs-Dashboard für Wartungsaufgaben](https://helpx.adobe.com/de/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## Konfigurieren von Wartungsaufgaben

In früheren Versionen von AEM konnten Sie Wartungsaufgaben mithilfe der Wartungskarte konfigurieren (Tools > Vorgänge > Wartung). Bei AEM as a Cloud Service ist die Wartungskarte nicht mehr vorhanden. Daher sollten Konfigurationen an die Quell-Code-Verwaltung übertragen und mithilfe von Cloud Manager bereitgestellt werden. Adobe verwaltet Wartungsaufgaben, die keine Kundenentscheidungen erfordern (z. B. Speicherbereinigung), während sich andere Wartungsaufgaben vom Kunden konfigurieren lassen (siehe folgende Tabelle).

>[!CAUTION]
>
>Adobe behält sich das Recht vor, Konfigurationseinstellungen für Wartungsaufgaben eines Kunden außer Kraft zu setzen, um Probleme wie Leistungsbeeinträchtigungen zu verhindern.

Die folgende Tabelle zeigt die Wartungsaufgaben, die zum Zeitpunkt der Veröffentlichung von AEM as a Cloud Service verfügbar sind.

| Wartungsaufgabe | Wer ist für die Konfiguration verantwortlich | Konfigurationsweise (optional) |
|---|---|---|
| Speicherbereinigung | Adobe | N/A – volle Verantwortung von Adobe |
| Versionsbereinigung | Adobe | Volle Verantwortung von Adobe, aber in Zukunft werden Kunden in der Lage sein, bestimmte Parameter selbst zu konfigurieren. |
| Bereinigung von Prüfprotokollen | Adobe | Volle Verantwortung von Adobe, aber in Zukunft werden Kunden in der Lage sein, bestimmte Parameter selbst zu konfigurieren. |
| Lucene-Binärdateien-Bereinigung | Adobe | Nicht verwendet und daher von Adobe deaktiviert. |
| Ad-hoc-Aufgabenbereinigung | Kunde | Muss in github vorgenommen werden. <br> Überschreiben Sie den Konfigurationsknoten des vordefinierten Wartungsfensters unter `/libs` durch Erstellen von Eigenschaften im Ordner `/apps/settings/granite/operations/maintenance/granite_weekly` oder `granite_daily`. Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster. <br> Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn `granite_TaskPurgeTask`). <br> Informationen zum Konfigurieren der OSGi-Eigenschaften finden Sie in der [AEM 6.5-Dokumentation zu Wartungsaufgaben](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html). |
| Workflow-Bereinigung | Kunde | Muss in github vorgenommen werden. <br> Überschreiben Sie den Konfigurationsknoten des vordefinierten Wartungsfensters unter `/libs` durch Erstellen von Eigenschaften im Ordner `/apps/settings/granite/operations/maintenance/granite_weekly` oder `granite_daily`. Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster. <br> Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn `granite_WorkflowPurgeTask`). <br> Informationen zum Konfigurieren der OSGi-Eigenschaften finden Sie in der [AEM 6.5-Dokumentation zu Wartungsaufgaben](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html). |
| Projektbereinigung | Kunde | Muss in github vorgenommen werden. <br> Überschreiben Sie den Konfigurationsknoten des vordefinierten Wartungsfensters unter `/libs` durch Erstellen von Eigenschaften im Ordner `/apps/settings/granite/operations/maintenance/granite_weekly` oder `granite_daily`. Weitere Konfigurationsdetails finden Sie in der Tabelle zum Wartungsfenster. <br> Aktivieren Sie die Wartungsaufgabe, indem Sie unter dem obigen Knoten einen weiteren Knoten mit den entsprechenden Eigenschaften hinzufügen (nennen Sie ihn `granite_ProjectPurgeTask`). <br> Informationen zum Konfigurieren von OSGi-Eigenschaften finden Sie in der [AEM 6.5-Dokumentation zu Wartungsaufgaben](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html). |

Kunden können die Ausführung der einzelnen Aufgaben für Workflow-Bereinigung, Ad-hoc-Aufgabenbereinigung und Projektbereinigung während des täglichen, wöchentlichen oder monatlichen Wartungsfensters planen. Diese Konfigurationen sollten direkt in der Quell-Code-Verwaltung bearbeitet werden. In der folgenden Tabelle werden die verfügbaren Konfigurationsparameter der einzelnen Fenster beschrieben. Sehen Sie sich auch die Speicherorte und Codebeispiele an, die nach der Tabelle bereitgestellt werden.

<table>
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
  <p><strong></strong>windowSchedule = daily (dieser Wert sollte nicht geändert werden)</p>
  <p><strong></strong>windowStartTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.</p>
  <p><strong></strong>windowEndTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.</p>
  </td> 
  </tr>
  <tr>
    <td>Wöchentlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td>
    <p><strong></strong>windowSchedule = weekly (dieser Wert sollte nicht geändert werden)</p>
    <p><strong></strong>windowStartTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.</p>
    <p><strong></strong>windowEndTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.</p>
    <p><strong>windowScheduleWeekdays= Array mit 2 Werten von 1-7 (z. B. [5,5])</strong>  Der erste Wert des Arrays ist der Tag des Beginns, an dem der Auftrag geplant wird, und der zweite Wert ist der Endtag, an dem der Auftrag beendet werden soll. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben.</p>
    </td>
  </tr>
  <tr>
    <td>Monatlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td>
    <p><strong></strong>windowSchedule = daily (dieser Wert sollte nicht geändert werden)</p>
    <p><strong></strong>windowStartTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.</p>
    <p><strong></strong>windowEndTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.</p>
    <p><strong>windowScheduleWeekdays = Array von 2 Werten von 1-7 (z. B. [5,5])</strong>  Der erste Wert des Arrays ist der Tag des Beginns, an dem der Auftrag geplant wird, und der zweite Wert ist der Endtag, an dem der Auftrag beendet werden soll. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0, um einen Zeitplan für die erste Woche des Monats bzw. 1 für die letzte Woche des Monats zu erstellen. Wenn kein Wert angegeben ist, werden Aufträge praktisch jeden Tag terminiert (wie von „windowScheduleWeekdays“ jeden Monat gesteuert).</p>
    </td> 
    </tr>
    </tbody>
</table>

**Standorte**:

* Täglich - /apps/settings/granite/operations/maintenance/granite_daily
* Wöchentlich - /apps/settings/granite/operations/maintenance/granite_weekly
* Monatlich - /apps/settings/granite/operations/maintenance/granite_month

**Codebeispiele**:

Codebeispiel 1 (täglich)

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

Codebeispiel 2 (wöchentlich)

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

Codebeispiel 3 (monatlich)

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
