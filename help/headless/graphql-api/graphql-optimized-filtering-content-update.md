---
title: Aktualisieren von Inhaltsfragmenten für optimierte GraphQL-Filterung
description: Erfahren Sie, wie Sie Ihre Inhaltsfragmente für optimierte GraphQL-Filterung in Adobe Experience Manager as a Cloud Service für die Bereitstellung von Headless-Inhalten aktualisieren.
exl-id: 211f079e-d129-4905-a56a-4fddc11551cc
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 8d14936ad21dc5879c72383defc3db22ce9a24ef
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 100%

---

# Aktualisieren von Inhaltsfragmenten für optimierte GraphQL-Filterung {#updating-content-fragments-for-optimized-graphql-filtering}

Um die Leistung Ihrer GraphQL-Filter zu optimieren, führen Sie eine Prozedur aus, um Ihre Inhaltsfragmente zu aktualisieren.

>[!NOTE]
>
>Nach dem Aktualisieren Ihrer Inhaltsfragmente können Sie den Empfehlungen zum [Optimieren von GraphQL-Abfragen](/help/headless/graphql-api/graphql-optimization.md) folgen.


## Voraussetzungen {#prerequisites}

Es gibt Voraussetzungen für diese Aufgabe:

1. Stellen Sie sicher, dass Sie mindestens Version 2023.1.0 von AEM as a Cloud Service haben.

1. Stellen Sie sicher, dass die Person, die die Aufgabe ausführt, über die erforderlichen Berechtigungen verfügt:

   * Es ist mindestens die Rolle `Deployment Manager` in Cloud Manager erforderlich.

## Aktualisieren von Inhaltsfragmenten {#updating-content-fragments}

1. Aktivieren Sie die Aktualisierung, indem Sie die folgenden Variablen für Ihre Instanz mithilfe der Cloud Manager-Benutzeroberfläche festlegen:

   ![Cloud Manager-Umgebungskonfiguration](assets/cfm-graphql-update-01.png "Cloud Manager-Umgebungskonfiguration")

   Die folgenden Variablen sind verfügbar:

   | | Name | Wert | Standardwert | Service | Applied | Typ | Anmerkungen |
   |---|---|---|---|---|---|---|---|
   | 1 | `CF_MIGRATION_ENABLED` | `1` | `0` | Alle | | Variable | Aktiviert(!=0) oder deaktiviert (0) das Auslösen des Inhaltsfragment-Migrationsauftrags. |
   | 2 | `CF_MIGRATION_ENFORCE` | `1` | `0` | Alle | | Variable | Setzt die (!=0)-Neumigration von Inhaltsfragmenten durch. Wenn Sie diese Markierung auf 0 setzen, wird eine inkrementelle Migration von Inhaltsfragmenten durchgeführt. Das heißt, wenn der Auftrag aus irgendeinem Grund abgebrochen wird, beginnt die nächste Ausführung des Auftrags mit der Migration an der Stelle, an der er abgebrochen wurde. Die erste Migration sollte durchgesetzt werden (Wert = 1). |
   | 3 | `CF_MIGRATION_BATCH` | `50` | `50` | Alle | | Variable | Größe des Batches zum Speichern der Anzahl von Inhaltsfragmenten nach der Migration. Dies ist für die Anzahl der Inhaltsfragmente relevant, die in einem Batch im Repository gespeichert werden, und kann zur Optimierung der Anzahl der Schreibvorgänge in das Repository verwendet werden. |
   | 4 | `CF_MIGRATION_LIMIT` | `1000` | `1000` | Alle | | Variable | Maximale Anzahl an Inhaltsfragmenten, die gleichzeitig verarbeitet werden sollen. Siehe auch Anmerkungen zu `CF_MIGRATION_INTERVAL`. |
   | 5 | `CF_MIGRATION_INTERVAL` | `60` | `600` | Alle | | Variable | Intervall (Sekunden) zur Verarbeitung der verbleibenden Inhaltsfragmente bis zum nächsten Limit. Dieses Intervall wird sowohl als Wartezeit vor dem Start des Auftrags als auch als Verzögerung zwischen der Verarbeitung jeder nachfolgenden CF_MIGRATION_LIMIT-Anzahl von Inhaltsfragmenten betrachtet. (*) |

   >[!NOTE]
   >
   >(*)
   >
   >Der Wert von `CF_MIGRATION_INTERVAL` kann auch dazu beitragen, die Gesamtausführungszeit des Migrationsauftrags abzuschätzen.
   >
   >Beispiel:
   >
   >* Gesamtzahl der Inhaltsfragmente = 20.000
   >* CF_MIGRATION_LIMIT = 1000
   >* CF_MIGRATION_INTERNAL = 60 (Sek.)
   >* Ungefährer Zeitaufwand um die Migration abzuschließen = 60 + (20.000/1000 x 60) = 1260 Sek. = 21 Minuten
   >  Die zusätzlichen „60“ Sekunden, die zu Beginn hinzugefügt werden, sind auf die anfängliche Verzögerung beim Starten des Auftrags zurückzuführen.
   >
   >Dies ist nur die *minimale* Zeit, die für die Ausführung des Auftrags benötigt wird, sie umfasst nicht die I/O-Zeit. Die tatsächlich benötigte Zeit könnte über dieser Schätzung liegen.

1. Überwachen Sie den Fortschritt und den Abschluss der Aktualisierung.

   Überwachen Sie dazu die Protokolle auf Autor und Golden-Publish von:

   * `com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob`

      * Autor-Protokolle; Beispiel:

        ```shell
        23.01.2023 13:13:45.926 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<dd9ffdc1-0c28-4d04-9a96-5d4d223e457e> is the leader, will schedule the upgrade schedule job.
        ...
        23.01.2023 13:13:45.941 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
        
        23.01.2023 13:20:40.960 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 6m, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
        ```

      * Golden-Publish-Protokolle; Beispiel:

        ```shell
        23.01.2023 12:35:05.150 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<ad1b399e-77be-408e-bc3f-57097498fddb> is the leader, will schedule the upgrade schedule job.
        
        23.01.2023 12:35:05.161 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
        ...
        23.01.2023 12:40:45.180 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 5m, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
        ```

   Kunden oder Kundinnen, die mithilfe von Splunk den Zugriff auf die Umgebungsprotokolle aktiviert haben, können die folgende Beispielabfrage verwenden, um den Aktualisierungsprozess zu überwachen. Weitere Informationen zur Aktivierung der Splunk-Protokollierung finden Sie unter [Debuggen von Produktions- und Staging-Umgebung](/help/implementing/developing/introduction/logging.md#debugging-production-and-stage).

   ```splunk
   index=<indexName> sourcetype=aemerror aem_envId=<environmentId> msg="*com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished*" 
   (aem_tier=golden-publish OR aem_tier=author) | table _time aem_tier pod_name msg | sort -_time desc
   ```

   Dabei gilt:

   * `environmentId`: eine Kennung der Kundenumgebung, z. B. `e1234`
   * `indexName`: ein Kundenindexname, der `aemerror`-Ereignisse sammelt

   Beispielausgabe:

   <table style="table-layout:auto">
     <thead>
       <tr>
       <th>_Zeit</th>
       <th>aem_tier</th>
       <th>pod_name</th>
       <th>msg</th>
       </tr>
     </thead> 
     <tbody>
       <tr>
         <td>2023-04-21 06:00:35.723</td>
         <td>author</td>
         <td>cm-p1234-e1234-aem-author-76d6dc4b79-8lsb5</td>
         <td>[sling-threadpool-bb5da4dd-6b05-4230-93ea-1d5cd242e24f-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 391m, slingJobId: 2023/4/20/23/16/db7963df-e267-489b-b69a-5930b0dadb37_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=36756, failedCount=0, skippedCount=0}</td>
       </tr>
       <tr>
         <td>2023-04-21 06:05:48.207</td>
         <td>golden-publish</td>
         <td>cm-p1234-e1234-aem-golden-publish-644487c9c5-lvkv2</td>
         <td>[sling-threadpool-284b9a9a-8454-461e-9bdb-44866c6ddfb1-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 211m, slingJobId: 2023/4/20/23/15/66c1690a-cdb7-4e66-bc52-90f33394ddfc_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=19557, failedCount=0, skippedCount=0}</td>
       </tr>
     </tbody>
   <table>

1. Deaktivieren Sie das Aktualisierungsverfahren.

   >[!IMPORTANT]
   >
   >Dieser Schritt ist erforderlich, um das Upgrade abzuschließen.

   Nachdem das Aktualisierungsverfahren ausgeführt wurde, setzen Sie die Cloud-Umgebungsvariable `CF_MIGRATION_ENABLED` auf „0“ zurück, um das Recycling aller Pods auszulösen.

   | | Name | Wert | Standardwert | Service | Applied | Typ | Anmerkungen |
   |---|---|---|---|---|---|---|---|
   | | `CF_MIGRATION_ENABLED` | `0` | `0` | Alle | | Variable | Deaktiviert(0) (oder Aktiviert(!=0)) das Auslösen des Migrationsauftrags für Inhaltsfragment. |

   >[!NOTE]
   >
   >Dies ist für die Veröffentlichungsstufe von Bedeutung, da die Inhaltsaktualisierung nur auf Golden-Publish erfolgt und beim Recycling von Pods alle normalen Veröffentlichungs-Pods auf Golden-Publish basieren.

1. Überprüfen Sie den Abschluss des Aktualisierungsvorgangs.

   Sie können den erfolgreichen Abschluss der Aktualisierung mithilfe des Repository-Browsers in der Cloud Manager Developer Console überprüfen, um die Inhaltsfragmentdaten zu überprüfen.

   * Vor der ersten vollständigen Migration ist die Eigenschaft `cfGlobalVersion` nicht vorhanden.
Das Vorhandensein dieser Eigenschaft auf dem JCR-Knoten `/content/dam` mit einem Wert von `1` bestätigt daher den Abschluss der Migration.

   * Sie können auch die folgenden Eigenschaften für die einzelnen Inhaltsfragmente überprüfen:

      * `_strucVersion` sollte den Wert von `1` haben
      * `indexedData`-Struktur muss vorhanden sein

     >[!NOTE]
     >
     >Durch dieses Verfahren werden Inhaltsfragmente in Autoren- und Veröffentlichungsinstanzen aktualisiert.
     >
     >Daher empfiehlt Adobe, dass Sie die Verifizierung über den Repository-Browser für *mindestens* eine Autoren- *und* eine Veröffentlichungsinstanz durchführen.

## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen:

* Die Leistungsoptimierung von GraphQL-Filtern ist erst nach einer vollständigen Aktualisierung aller Ihrer Inhaltsfragmente möglich (erkennbar am Vorhandensein der Eigenschaft `cfGlobalVersion` für den JCR-Knoten `/content/dam`).

* Wenn Inhaltsfragmente aus einem Inhaltspaket (mit `crx/de`) importiert werden, nachdem das Aktualisierungsverfahren ausgeführt wurde, werden diese Inhaltsfragmente erst nach erneuter Ausführung des Aktualisierungsverfahrens in den GraphQL-Abfrageergebnissen berücksichtigt.
