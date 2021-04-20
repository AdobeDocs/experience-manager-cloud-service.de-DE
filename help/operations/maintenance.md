---
title: Wartungsaufgaben in AEM as a Cloud Service
description: Wartungsaufgaben in AEM as a Cloud Service
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
translation-type: tm+mt
source-git-commit: 7700ad89b1c2a3009c4b64c1af899a0130708a32
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 94%

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

Kunden können die Ausführung der einzelnen Aufgaben für Workflow-Bereinigung, Ad-hoc-Aufgabenbereinigung und Projektbereinigung während des täglichen, wöchentlichen oder monatlichen Wartungsfensters planen. Diese Konfigurationen sollten direkt in der Quell-Code-Verwaltung bearbeitet werden. In der folgenden Tabelle werden die verfügbaren Konfigurationsparameter der einzelnen Fenster beschrieben.

<table>
  <tr>
    <th>Konfiguration von Wartungsfenstern</th>
    <th>Wer ist für die Konfiguration verantwortlich</th>
    <th>Konfigurationstyp</th>
    <th>Standort</th>
    <th>Beispiel</th>
    <th>Parameter</th>
  </tr>
  <tr>
    <td>Täglich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td>Siehe unten stehende Position 1</td>
    <td>Siehe Code-Beispiel 1 unten</td>
  <td>
  <strong>windowSchedule</strong> = daily (dieser Wert sollte nicht geändert werden)
  <strong>windowStartTime</strong> = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.
  <strong>windowEndTime</strong> = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.
  </td> 
  </tr>
  <tr>
    <td>Wöchentlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td>Siehe unten Position 2</td>
    <td>Siehe Code-Beispiel 2 unten</td>
    <td>
    <strong>windowSchedule</strong> = weekly (dieser Wert sollte nicht geändert werden)
    <strong>windowStartTime</strong> = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.
    <strong>windowEndTime</strong> = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.
    <strong>windowScheduleWeekdays = Array mit 2 Werten von 1–7. Beispiel: [5,5].</strong> Der erste Wert des Arrays ist der Anfangstag, an dem der Auftrag geplant wird, und der zweite Wert der Endtag, an dem der Auftrag beendet wird. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben.
    </td> 
  </tr>
  <tr>
    <td>Monatlich</td>
    <td>Kunde</td>
    <td>JCR-Knotendefinition</td>
    <td>Siehe unten Position 3</td>
    <td>Siehe Code-Beispiel 3 unten</td>
    <td>
    <strong>windowSchedule</strong> = daily (dieser Wert sollte nicht geändert werden)
    <strong>windowStartTime</strong> = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll.
    <strong>windowEndTime</strong> = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem monatlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind.
    <strong>windowScheduleWeekdays = Array mit 2 Werten von 1–7. Beispiel: [5,5].</strong> Der erste Wert des Arrays ist der Anfangstag, an dem der Auftrag geplant wird, und der zweite Wert der Endtag, an dem der Auftrag beendet wird. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben.
    <strong>windowFirstLastStartDay - 0/1</strong> 0, um in der ersten Woche des Monats zu planen, oder 1, um in der letzten Woche des Monats zu planen. Wenn kein Wert angegeben ist, werden Aufträge praktisch jeden Tag terminiert (wie von „windowScheduleWeekdays“ jeden Monat gesteuert).
    </td> 
    </tr>
</table>

Standorte:

1. /apps/settings/granite/operations/maintenance/granite_daily
2. /apps/settings/granite/operations/maintenance/granite_weekly
3. /apps/settings/granite/operations/maintenance/granite_month

Codebeispiele:

Code-Beispiel 1

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

Code-Beispiel 2

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

Code-Beispiel 3

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

| Konfiguration von Wartungsfenstern | Wer ist für die Konfiguration verantwortlich | Konfigurationstyp | Standort | Beispiel | Parameter |
|---|---|---|---|---|---|
| Täglich | Kunde | JCR-Knotendefinition | Siehe unten stehende Position 1 | Siehe Code-Beispiel 1 unten | **** windowSchedule = daily (dieser Wert sollte nicht geändert werden). <br> **** windowStartTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beginnen soll. <br> **** windowEndTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem täglichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind. |
| Wöchentlich | Kunde | JCR-Knotendefinition | Siehe unten Position 2 | Siehe Code-Beispiel 2 unten | **** windowSchedule = weekly (dieser Wert sollte nicht geändert werden). <br> **** windowStartTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die mit dem wöchentlichen Wartungsfenster verknüpften Maintenance-Aufgaben mit der Ausführung beginnen sollen. <br> **** windowEndTime = HH:MM unter Verwendung der 24-Stunden-Zeit. Definiert, wann die Ausführung der mit dem wöchentlichen Wartungsfenster verknüpften Wartungsaufgaben beendet werden soll, wenn diese noch nicht abgeschlossen sind. <br> **windowScheduleWeekdays= Array mit 2 Werten von 1-7**  (z. B.  [5,5]). Der erste Wert des Arrays ist der Anfangstag, an dem der Auftrag geplant wird, und der zweite Wert der Endtag, an dem der Auftrag beendet wird. Die genaue Uhrzeit von Anfang und Ende wird durch „windowStartTime“ bzw. „windowEndTime“ angegeben. |

