---
title: 'Richtlinien und Best Practices für die Verwendung des Content Transfer Tools  '
description: Lernen Sie die Richtlinien und Best Practices für die Verwendung des Content Transfer Tools kennen.
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
feature: Migration
role: Admin
source-git-commit: 943685ed9c33ba42c4dd1cb941b2eca1cce8bfe8
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 100%

---


# Richtlinien und Best Practices für die Verwendung des Content Transfer Tools {#guidelines}

## Richtlinien und Best Practices {#best-practices}

<!-- Alexandru: hiding for now

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Guidelines and Best Practices"
>abstract="Review guidelines and best practices to use the Content Transfer tool including revision cleanup tasks, Disk space considerations and more."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de" text="Important Considerations for using Content Transfer Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/group-migration.md#important-considerations" text="Important Considerations when Migrating Groups" 

-->

Das Content Transfer Tool integriert den Inhaltstransferprozess in Cloud Acceleration Manager. Es ist erforderlich, diese Version (2.0 oder höher, wobei jetzt Version 3.0 empfohlen wird) zu verwenden, um alle gebotenen Vorteile nutzen zu können:

* Self-Service-Methode zur einmaligen Extraktion eines Migrationssatzes und zur gleichzeitigen Aufnahme in mehrere Umgebungen
* Verbessertes Benutzererlebnis durch bessere Ladezustände, Limits und Fehlerbehandlung
* Aufnahmeprotokolle bleiben erhalten und stehen immer zur Fehlerbehebung zur Verfügung.

Um mit der Verwendung der neuesten Version zu beginnen, müssen ältere Versionen des Content Transfer Tools deinstalliert werden. Mit Version 2.0 und höher erstellen Sie Migrationssätze und führen Extraktion und Aufnahme mit diesen Sätzen erneut durch.
Versionen vor 2.0.0 werden nicht unterstützt. Es wird empfohlen, die neueste Version zu verwenden.

Die folgenden Richtlinien und Best Practices gelten für die neue Version des Content Transfer Tools:

* Führen Sie eine [Revisionsbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=de) und [Datenspeicher-Konsistenzprüfungen](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16550.html?lang=de) auf dem **Quell-Repository** aus, um mögliche Probleme zu identifizieren und die Größe des Repositorys zu reduzieren.

* Adobe empfiehlt, in der Aufnahmephase die Aufnahme mit aktiviertem *Löschmodus* durchzuführen, in dem das vorhandene Repository (Author oder Publish) in der Adobe Experience Manager (AEM) Cloud Service-Zielumgebung gelöscht wird. Aktualisieren Sie dann mit den Migrationssatzdaten. Dieser Modus ist schneller als der Nicht-Löschmodus, bei dem der Migrationssatz zusätzlich zum aktuellen Inhalt angewendet wird.

* Nach Abschluss der Aktivität zum Inhaltstransfer ist in der Cloud Service-Umgebung die korrekte Projektstruktur erforderlich, um sicherzustellen, dass der Inhalt in der Cloud Service-Umgebung erfolgreich gerendert wird.

* Stellen Sie sicher, dass im Unterverzeichnis `crx-quickstart` der AEM-Quellinstanz genügend Speicherplatz vorhanden ist, bevor Sie das Content Transfer Tool ausführen. Dies ist notwendig, da das Content Transfer Tool eine lokale Kopie des Repositorys erstellt, die später in den Migrationssatz hochgeladen wird.
Die allgemeine Formel zur Berechnung des erforderlichen freien Speicherplatzes lautet wie folgt:
  `data store size + node store size * 1.5`

* *Datenspeichergröße*: Das Content Transfer Tool verwendet 64 GB, auch wenn der eigentliche Datenspeicher größer ist.
* *Knotenspeichergröße*: Größe des Segmentspeicherverzeichnisses oder der MongoDB-Datenbank.
Bei einer Segmentspeichergröße von 20 GB wären daher 94 GB freier Speicherplatz erforderlich.

* Während der gesamten Übertragung von Inhalten muss ein Migrationssatz beibehalten werden, um die Auffüllung von Inhalten zu unterstützen. Es können maximal 10 Migrationssätze pro Projekt in Cloud Acceleration Manager erstellt und gleichzeitig verwaltet werden, während die Aktivität zum Übertragen von Inhalten ausgeführt wird. Wenn mehr als 10 Migrationssätze benötigt werden, erstellen Sie in Cloud Acceleration Manager ein zweites Projekt. Dies erfordert jedoch zusätzliches Projekt-Management und Out-of-Product-Governance, um zu verhindern, dass Inhalte auf dem Ziel von mehreren Benutzenden überschrieben werden.

* Ändern Sie nicht das Installationsverzeichnis des CTT-Tools. Standardmäßig findet die Installation im Pfad „crx-quickstart/cloud-migration“ statt. Dieser spezifische Speicherort wird intern von anderen Bibliotheken verwendet. Eine Änderung dieses Pfads kann zu Extraktionsproblemen führen.

## Wichtige Überlegungen vor der Verwendung des Content Transfer Tools {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transfer Tools:

* Die Systemanforderungen für das Content Transfer Tool sind AEM 6.3 + und Java™ 8. Wenn Sie eine niedrigere AEM-Version verwenden, aktualisieren Sie Ihr Content-Repository auf AEM 6.5, um das Content Transfer Tool verwenden zu können.

* Java™ muss in der AEM-Umgebung konfiguriert sein, damit der Befehl `java` von der Person ausgeführt werden kann, die AEM startet.

* Das Content Transfer Tool kann mit den folgenden Arten von Datenspeicher genutzt werden: Dateispeicher, S3-Datenspeicher, freigegebener S3-Datenspeicher und Azure Blob-Datenspeicher.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, müssen Sie dafür sorgen, dass Ihre Umgebung aktuell ist bzw. auf die neueste Version aktualisiert wird. Wenn Sie eine *Produktionsumgebung* nutzen, wird diese automatisch aktualisiert.

* Um eine Aufnahme zu starten, müssen Sie der lokalen **AEM-Admin-Gruppe** in der Cloud Service-Instanz angehören, an die Sie Inhalte übertragen. Unberechtigte Personen können die Aufnahme nicht starten, ohne das Migrations-Token manuell angeben zu müssen.

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in dem Inhalte erfasst werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Admins, die der Gruppe **Admins** hinzugefügt werden. Benutzende müssen erneut zur **Admin-Gruppe** hinzugefügt werden, um das Zugriffs-Token für das Content Transfer Tool abrufen zu können.

* Der Extraktionsschlüssel ist 14 Tage nach seiner Erstellung/Erneuerung gültig. Er kann jederzeit erneuert werden. Wenn der Extraktionsschlüssel abgelaufen ist, können Sie keine Extraktion durchführen.

* Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Alle Inhalte, die im Migrationssatz angegeben sind, werden in die gewählte Zielinstanz aufgenommen. Benutzende können einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen. Adobe empfiehlt, beim Verschieben von Inhalten auf eine Produktionsinstanz CTT auf der Quell-Autoreninstanz zu installieren, um Inhalte auf die Ziel-Autoreninstanz zu verschieben. Installieren Sie auf ähnliche Weise CTT auf der Quell-Veröffentlichungsinstanz, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben. Weitere Einzelheiten finden Sie unter [Ausführen des Content Transfer Tools auf einer Veröffentlichungsinstanz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de#running-tool).

* Die vom Content Transfer Tool übertragenen Gruppen sind nur diejenigen, die vom Inhalt zur Erfüllung der Berechtigungen benötigt werden. Im _Extraktionsprozess_ wird der gesamte Ordner `/home/groups` in den Migrationssatz kopiert. Weitere Informationen finden Sie unter [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md). Im _Aufnahmeprozess_ werden alle Gruppen, auf die in den migrierten Inhalts-ACLs verwiesen wird, kopiert. Siehe [Migrieren von geschlossenen Benutzergruppen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) für zusätzliche Überlegungen zu Gruppen, die in einer Richtlinie für geschlossene Benutzergruppen (CUG) verwendet werden.

* Während der Extraktionsphase wird das Content Transfer Tool in einer aktiven AEM-Quellinstanz ausgeführt.

* In der *Aufnahmephase* für die Autoreninstanz wird die gesamte Autorenbereitstellung herunterskaliert. Dies bedeutet, dass AEM Author während des gesamten Aufnahmeprozesses nicht verfügbar ist. Stellen Sie zudem sicher, dass während der laufenden *Aufnahmephase* keine Cloud Manager-Pipelines ausgeführt werden.

* Bei Verwendung von `Amazon S3` oder `Azure` als Datenspeicher im Quell-AEM-System sollte der Datenspeicher so konfiguriert werden, dass die gespeicherten Blobs nicht gelöscht werden können (gesammelter Abfall). Dadurch wird die Integrität der Indexdaten sichergestellt. Wird diese Konfiguration nicht auf diese Weise vorgenommen, kann es zu fehlgeschlagenen Extraktionen kommen, da die Integrität dieser Indexdaten nicht gewährleistet ist.

* Wenn Sie benutzerdefinierte Indizes verwenden, müssen Sie sicherstellen, dass Sie die benutzerdefinierten Indizes mit dem Knoten `tika` konfigurieren, bevor Sie das Content Transfer Tool ausführen. Weitere Informationen finden Sie unter [Vorbereiten der neuen Indexdefinition](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=de#preparing-the-new-index-definition).

* Wenn Sie eine Auffüllung vornehmen möchten, darf sich die Inhaltsstruktur der vorhandenen Inhalte zwischen der ersten Extraktion und der Auffüllungsextraktion nicht ändern. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Achten Sie darauf, dies während des Migrationsprozesses entsprechend einzuschränken.

* Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen und Auffüllungen mit `wipe=false` durchzuführen, müssen Sie aufgrund einer aktuellen Einschränkung im Content Transfer Tool die Versionsbereinigung deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu lassen und in einen Migrationssatz aufzufüllen, dann müssen Sie die Aufnahme als `wipe=true` durchführen.

* Das Content Transfer Tool (CTT) unterstützt keine Aufnahmen mit Zusammenführungen. Um Inhalte aus mehreren Systemen in einer einzigen Cloud Service-Instanz zusammenzuführen, können nur aus einem Quellsystem Versionen migriert werden. Dieser Prozess erfordert die Verwendung von Migrationen mit dem Parameter „wipe=false“, was aufgrund der inkrementellen Natur des Vorgangs zu längeren Aufnahmezeiten führen kann. Wenn möglich, konsolidieren Sie Inhalte auf einem einzigen Quellsystem, bevor Sie mit der Migration beginnen, um die Notwendigkeit der Zusammenführung von Inhalten zu vermeiden.

* Ein Migrationssatz läuft nach längerer Inaktivität ab. Danach sind die zugehörigen Daten nicht mehr verfügbar. Weitere Informationen finden Sie unter [Ablauf von Migrationssätzen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de#migration-set-expiry).

## So geht es weiter {#whats-next}

Nun, da Sie die Richtlinien, Best Practices und wichtigen Überlegungen zur Verwendung des Content Transfer Tool kennen, können Sie das Tool jetzt installieren und verwenden, beginnend mit der Erstellung eines Migrationssatzes. Siehe [Erste Schritte mit dem Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).
