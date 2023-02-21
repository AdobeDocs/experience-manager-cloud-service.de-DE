---
title: Aktualisieren Ihrer Inhaltsfragmente für das Paging und die Sortierung
description: Erfahren Sie, wie Sie Ihre Inhaltsfragmente für Paging und Sortierung in Adobe Experience Manager as a Cloud Service für die Bereitstellung Headless Content aktualisieren.
source-git-commit: d12e2c3c23b5c0eebe35038c6c461c7f05dedc55
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 6%

---


# Aktualisieren Ihrer Inhaltsfragmente für Paging und Sortierung in GraphQL-Filterung {#updating-content-fragments-for-paging-and-sorting-graphql-filtering}

Um die Leistung Ihrer GraphQL-Filter zu optimieren, müssen Sie eine Prozedur ausführen, um Ihre Inhaltsfragmente zu aktualisieren.

>[!NOTE]
>
>Nach dem Aktualisieren Ihrer Inhaltsfragmente können Sie den Empfehlungen für [Optimieren von GraphQL-Abfragen](/help/headless/graphql-api/graphql-optimization.md).


## Voraussetzungen {#prerequisites}

Stellen Sie sicher, dass Sie mindestens AEM Version 2023.1.0 von as a Cloud Service haben.

## Aktualisieren von Inhaltsfragmenten {#updating-content-fragments}

Gehen Sie wie folgt vor, um das Verfahren auszuführen:

1. Aktivieren Sie die Aktualisierung, indem Sie die folgenden Variablen für Ihre Instanz mithilfe der Cloud Manager-Benutzeroberfläche festlegen:

   ![Cloud Manager-Umgebungskonfiguration](assets/cfm-graphql-update-01.png "Cloud Manager-Umgebungskonfiguration")

   Die verfügbaren Variablen sind:

   <table style="table-layout:auto">
    <tbody>
     <tr>
      <th> </th>
      <th>Name</th>
      <th>Wert</th>
      <th>Standardwert</th>
      <th>Service</th>
      <th>Angewandt</th>
      <th>Typ</th>
      <th>Anmerkungen</th>
     </tr>
     <tr>
      <td>1</td>
      <td>`AEM_RELEASE_CHANNEL` </td>
      <td>`prerelease` </td>
      <td> </td>
      <td>Alle </td>
      <td> </td>
      <td>Variable </td>
      <td>Erforderlich, um die Funktion zu aktivieren. </td>
     </tr>
     <tr>
      <td>2</td>
      <td>`CF_MIGRATION_ENABLED` </td>
      <td>`1` </td>
      <td>0 </td>
      <td>Alle </td>
      <td> </td>
      <td>Variable </td>
      <td>Aktiviert(!=0) oder deaktiviert (0) das Auslösen des Inhaltsfragmentmigrationsauftrags. </td>
     </tr>
     <tr>
      <td>3</td>
      <td>`CF_MIGRATION_ENFORCE` </td>
      <td>`1` </td>
      <td>`0` </td>
      <td>Alle </td>
      <td> </td>
      <td>Variable </td>
      <td>Durchsetzen (!=0) Neumigration von Inhaltsfragmenten.<br>Wenn Sie dieses Flag auf 0 setzen, wird eine inkrementelle Migration von CFs durchgeführt. Wenn der Auftrag also aus irgendeinem Grund beendet wird, beginnt die nächste Ausführung des Auftrags mit der Migration von dem Punkt, an dem er beendet wurde. Beachten Sie, dass die erste Migration erzwungen werden sollte (Wert = 1). </td>
     </tr>
     <tr>
      <td>4</td>
      <td>`CF_MIGRATION_BATCH` </td>
      <td>`50` </td>
      <td>`50` </td>
      <td>Alle </td>
      <td> </td>
      <td>Variable </td>
      <td>Größe des Batches zum Speichern der Anzahl von Inhaltsfragmenten nach der Migration.<br>Dies ist relevant für die Anzahl der CFs, die in einem Batch im Repository gespeichert werden, und kann zur Optimierung der Anzahl der Schreibvorgänge in das Repository verwendet werden. </td>
     </tr>
     <tr>
      <td>5</td>
      <td>`CF_MIGRATION_LIMIT` </td>
      <td>`1.000` </td>
      <td>`1.000` </td>
      <td>Alle </td>
      <td> </td>
      <td>Variable </td>
      <td>Maximale Anzahl an Inhaltsfragmenten, die gleichzeitig verarbeitet werden sollen.<br>Siehe auch Notizen für "CF_MIGRATION_INTERVAL". </td>
     </tr>
     <tr>
      <td>6</td>
      <td>`CF_MIGRATION_INTERVAL` </td>
      <td>"60" </td>
      <td>`600` </td>
      <td>Alle </td>
      <td> </td>
      <td>Variable </td>
      <td>Intervall (Sekunden) zur Verarbeitung verbleibender Inhaltsfragmente bis zum nächsten Limit<br>Dieses Intervall gilt auch als Wartezeit vor dem Start des Auftrags sowie als Verzögerung zwischen der Verarbeitung jeder nachfolgenden CF_MIGRATION_LIMIT-Anzahl von CFs.<br>(*)</td>
     </tr>
    </tbody>
   </table>

   >[!NOTE]
   >
   >(*)
   >
   >Der Wert von `CF_MIGRATION_INTERVAL` kann auch dazu beitragen, die Gesamtausführungszeit des Migrationsauftrags zu schätzen.
   >
   >Beispiel:
   >
   >* Gesamtzahl der Inhaltsfragmente = 20.000
   >* CF_MIGRATION_LIMIT = 1000
   >* CF_MIGRATION_INTERNAL = 60 (Sec)
   >* Ungefährer Zeitaufwand für den Abschluss der Migration = 60 + (20.000/1000 * 60) = 1260 Sec = 21 Minuten
      >  Die zusätzliche &quot;60&quot;Sekunden, die zu Beginn hinzugefügt werden, ist auf die anfängliche Verzögerung beim Starten des Auftrags zurückzuführen.

   >
   >Sie sollten auch wissen, dass dies nur der *Minimum* Zeit erforderlich, um den Auftrag abzuschließen, nicht jedoch die E/A-Zeit. Die tatsächlich benötigte Zeit könnte deutlich über dieser Schätzung liegen.

1. Überwachen Sie den Fortschritt und den Abschluss der Aktualisierung.

   Überwachen Sie dazu die Protokolle auf der Autoren- und der Golden-Publish-Seite aus:

   * `com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob`

      * Autorenprotokolle; Beispiel:

         ```shell
         23.01.2023 13:13:45.926 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<dd9ffdc1-0c28-4d04-9a96-5d4d223e457e> is the leader, will schedule the upgrade schedule job.
         ...
         23.01.2023 13:13:45.941 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
         
         23.01.2023 13:20:40.960 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 6m, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
         ```
   * Golden-publish-Protokolle; Beispiel:

      ```shell
      23.01.2023 12:35:05.150 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<ad1b399e-77be-408e-bc3f-57097498fddb> is the leader, will schedule the upgrade schedule job.
      
      23.01.2023 12:35:05.161 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
      ...
      23.01.2023 12:40:45.180 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 5m, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
      ```


1. Deaktivieren Sie das Aktualisierungsverfahren.

   >[!IMPORTANT]
   >
   >Dieser Schritt ist erforderlich, um das Upgrade abzuschließen.

   Nachdem das Aktualisierungsverfahren ausgeführt wurde, setzen Sie die Cloud-Umgebungsvariable zurück `CF_MIGRATION_ENABLED` auf &quot;0&quot;, um das Recycling aller Pods Trigger.

   <table>
    <tbody>
     <tr>
      <th> </th>
      <th>Name</th>
      <th>Wert</th>
      <th>Standardwert</th>
      <th>Service</th>
      <th>Angewandt</th>
      <th>Typ</th>
      <th>Anmerkungen</th>
     </tr>
     <tr>
      <td></td>
      <td>`CF_MIGRATION_ENABLED` </td>
      <td>`0` </td>
      <td>`0` </td>
      <td>Alle </td>
      <td> </td>
      <td>Variable </td>
      <td>Deaktiviert(0) (oder Aktiviert(!=0)) Auslösen des Inhaltsfragment-Migrationsauftrags. </td>
     </tr>
    </tbody>
   </table>

   >[!NOTE]
   >
   >Dies ist besonders für die Veröffentlichungsstufe wichtig, da die Inhaltsaktualisierung nur auf Golden Publish erfolgt und beim Recycling von Pods alle normalen Veröffentlichungs-Pods auf Golden Publish basieren.

1. Überprüfen Sie den Abschluss des Aktualisierungsvorgangs.

   Sie können den erfolgreichen Abschluss der Aktualisierung mithilfe des Repository-Browsers in der Cloud Manager-Entwicklerkonsole überprüfen, um die Inhaltsfragmentdaten zu überprüfen.

   * Vor der ersten vollständigen Migration wird die `cfGlobalVersion` -Eigenschaft nicht vorhanden ist.
Daher ist das Vorhandensein dieser Eigenschaft auf dem JCR-Knoten `/content/dam` mit dem Wert `1`bestätigt den Abschluss der Migration.

   * Sie können auch die folgenden Eigenschaften für die einzelnen Inhaltsfragmente überprüfen:

      * `_strucVersion` sollte den Wert von `1`
      * `indexedData` Struktur muss vorhanden sein

      >[!NOTE]
      >
      >Durch dieses Verfahren werden Inhaltsfragmente in Autoren- und Veröffentlichungsinstanzen aktualisiert.
      >
      >Daher wird empfohlen, die Verifizierung über den Repository-Browser durchzuführen für *mindestens* ein Autor *und* eine Veröffentlichungsinstanz.


## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen:

* Die Leistungsoptimierung von GraphQL-Filtern ist erst nach einer vollständigen Aktualisierung aller Inhaltsfragmente möglich (erkennbar an der Tatsache, dass die `cfGlobalVersion` -Eigenschaft für den JCR-Knoten `/content/dam`)

* Wenn Inhaltsfragmente aus einem Inhaltspaket importiert werden (mithilfe von `crx/de`), nachdem das Aktualisierungsverfahren ausgeführt wurde, werden diese Inhaltsfragmente erst dann in den GraphQL-Abfrageergebnissen berücksichtigt, wenn das Aktualisierungsverfahren erneut ausgeführt wird.