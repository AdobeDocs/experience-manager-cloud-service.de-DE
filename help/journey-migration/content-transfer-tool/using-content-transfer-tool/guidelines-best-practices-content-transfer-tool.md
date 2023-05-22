---
title: Richtlinien und Best Practices für die Verwendung des Content Transfer Tools
description: Richtlinien und Best Practices für die Verwendung des Content Transfer Tools
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
source-git-commit: 5475f9995513d09e61bd8f52242b3e74b8d4694c
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 100%

---

# Richtlinien und Best Practices für die Verwendung des Content Transfer Tools {#guidelines}

## Richtlinien und Best Practices {#best-practices}

<!-- Alexandru: hiding for now

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Guidelines and Best Practices"
>abstract="Review guidelines and best practices to use the Content Transfer tool including revision cleanup tasks, Disk space considerations and more."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html" text="Important Considerations for using Content Transfer Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/user-mapping-and-migration.md#important-considerations" text="Important Considerations when Mapping and Migrating Users" 

-->

Es ist eine neue Version des Content Transfer Tool verfügbar, die den Inhaltstransferprozess mit Cloud Acceleration Manager integriert. Es wird dringend empfohlen, zu dieser neuen Version zu wechseln, um alle Vorteile nutzen zu können, die sie bietet:

* Self-Service-Methode zur einmaligen Extraktion eines Migrationssatzes und zur gleichzeitigen Aufnahme in mehrere Umgebungen
* Verbessertes Benutzererlebnis durch bessere Ladezustände, Limits und Fehlerbehandlung
* Aufnahmeprotokolle bleiben erhalten und stehen immer zur Fehlerbehebung zur Verfügung.

Um mit der Verwendung der neuen Version zu beginnen, müssen Sie ältere Versionen des Inhaltsübertragungs-Tools deinstallieren. Dies ist erforderlich, da die neue Version mit einer größeren Veränderung der Architektur einhergeht. Mit Version 2.x müssen Sie neue Migrationssätze erstellen und die Extraktion und Aufnahme für die neuen Migrationssätze erneut ausführen.
Versionen vor 2.0.0 werden nicht mehr unterstützt. Es wird empfohlen, die neueste Version zu verwenden.

Die folgenden Richtlinien und Best Practices gelten für die neue Version des Content Transfer Tool:

* Es wird empfohlen, eine [Revisionsbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=de) und [Datenspeicher-Konsistenzprüfungen](https://helpx.adobe.com/de/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) im **Quell**-Repository durchzuführen, um potenzielle Probleme zu identifizieren und die Größe des Repositorys zu reduzieren.

* In der Aufnahmephase wird empfohlen, die Aufnahme mit aktiviertem *Wischmodus* auszuführen, wobei das vorhandene Repository (Autor oder Veröffentlichung) in der Zielumgebung von AEM Cloud Service vollständig gelöscht und dann mit den Migrationssatzdaten aktualisiert wird. Dieser Modus ist viel schneller als der Nicht-Löschmodus, bei dem der Migrationssatz zusätzlich zum aktuellen Inhalt angewendet wird.

* Nach Abschluss der Aktivität zum Inhaltstransfer ist in der Cloud Service-Umgebung die korrekte Projektstruktur erforderlich, um sicherzustellen, dass der Inhalt in der Cloud Service-Umgebung erfolgreich gerendert wird.

* Stellen Sie sicher, dass im Unterverzeichnis `crx-quickstart` der AEM-Quellinstanz genügend Speicherplatz vorhanden ist, bevor Sie das Content Transfer Tool ausführen. Dies ist notwendig, da das Content Transfer Tool eine lokale Kopie des Repositorys erstellt, die später in den Migrationssatz hochgeladen wird.
Die allgemeine Formel zur Berechnung des erforderlichen freien Speicherplatzes lautet wie folgt:
   `data store size + node store size * 1.5`

   * *Datenspeichergröße*: Das Content Transfer Tool verwendet 64 GB, auch wenn der eigentliche Datenspeicher größer ist.
   * *Knotenspeichergröße*: Größe des Segmentspeicherverzeichnisses oder der MongoDB-Datenbank.
Bei einer Segmentspeichergröße von 20 GB wären daher 94 GB freier Speicherplatz erforderlich.

* Ein Migrationssatz muss während der gesamten Aktivität zum Content-Transfer verwaltet werden, um das Auffüllen von Content zu unterstützen. Es können maximal fünf Migrationssätze pro Projekt im Cloud Acceleration Manager erstellt und verwaltet werden, während die Aktivität zum Übertragen von Inhalten ausgeführt wird. Wenn mehr als fünf Migrationssätze benötigt werden, müssen Sie ein zweites Projekt im Cloud Acceleration Manager erstellen. Dies erfordert jedoch zusätzliches Projektmanagement und Out-of-Product-Governance, um zu verhindern, dass Inhalte auf dem Ziel von mehreren Benutzern überschrieben werden.

## Wichtige Überlegungen vor der Verwendung des Content Transfer Tools {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transfer Tools:

* Die Mindest-Systemanforderungen für das Content Transfer Tool sind AEM 6.3 + und JAVA 8. Wenn Sie eine niedrigere AEM-Version verwenden, müssen Sie Ihr Content-Repository auf AEM 6.5 aktualisieren, um das Content Transfer Tool verwenden zu können.

* Java muss in der AEM-Umgebung konfiguriert werden, damit der `java`-Befehl vom Benutzer, der AEM startet, ausgeführt werden kann.

* Das Content Transfer Tool kann mit den folgenden Arten von Datenspeicher genutzt werden: Dateispeicher, S3-Datenspeicher, freigegebener S3-Datenspeicher und Azure Blob-Datenspeicher.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, müssen Sie dafür sorgen, dass Ihre Umgebung aktuell ist bzw. auf die neueste Version aktualisiert wird. Wenn Sie eine *Produktionsumgebung* nutzen, wird diese automatisch aktualisiert.

* Um eine Aufnahme zu starten, müssen Sie der lokalen AEM-**Administratoren**-Gruppe in der Cloud Service-Instanz angehören, an die Sie Inhalte übertragen. Unberechtigte Benutzer können die Aufnahme nicht starten, ohne das Migrations-Token manuell angeben zu müssen.

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in dem Inhalte erfasst werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **Administratoren** hinzugefügt werden. Der Benutzer muss erneut zur Gruppe der **Administratoren** hinzugefügt werden, um das Zugriffstoken für das Content Transfer Tool abrufen zu können.

* Aufnahmen unterstützen nicht das Zusammenführen von Inhalten aus mehreren Quellen in der Zielinstanz von Cloud Service, wenn die Inhalte aus den beiden Quellen in dieselben Pfade auf dem Ziel verschoben werden. Wenn Sie Inhalte aus mehreren Quellen in eine einzige Zielinstanz von Cloud Service verschieben möchten, müssen Sie sicherstellen, dass sich die Inhaltspfade der Quellen nicht überschneiden.

* Der Extraktionsschlüssel ist 14 Tage nach seiner Erstellung/Erneuerung gültig. Er kann jederzeit erneuert werden. Wenn der Extraktionsschlüssel abgelaufen ist, können Sie keine Extraktion vornehmen.

* Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Der im Migrationssatz angegebene Inhalt wird in die ausgewählte Zielinstanz aufgenommen. Der Benutzer kann einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen. Es wird empfohlen, beim Verschieben von Inhalten in eine Produktionsinstanz CTT in der Quellautoreninstanz zu installieren, um Inhalte in die Zielautoreninstanz zu verschieben, und CTT in ähnlicher Weise in der Quell-Veröffentlichungsinstanz zu installieren, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben. Weitere Einzelheiten finden Sie unter [Ausführen des Content Transfer Tools auf einer Veröffentlichungsinstanz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de#running-tool).

* Die vom Content Transfer Tool übertragenen Benutzenden und Gruppen sind nur diejenigen, die vom Inhalt zur Erfüllung der Berechtigungen benötigt werden. Im _Extraktionsprozess_ wird alles unter `/home` in den Migrationssatz kopiert und eine Benutzerzuordnung erstellt, indem ein aus der E-Mail-Adresse jedes Benutzers bzw. jeder Benutzerin generiertes Feld hinzugefügt wird. Weitere Informationen finden Sie unter [Benutzerzuordnung und Prinzipalmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md). Im _Aufnahmeprozess_ werden alle Benutzenden und Gruppen, auf die in den migrierten Inhalts-ACLs verwiesen wird, kopiert.

* Während der Extraktionsphase wird das Content Transfer Tool in einer aktiven AEM-Quellinstanz ausgeführt.

* Nachdem die *Extraktionsphase* des Inhaltstransfers abgeschlossen und die *Aufnahmephase* zur Aufnahme von Inhalt in Ihre *Staging*- oder *Produktionsinstanzen* von AEM as a Cloud Service begonnen wird, müssen Sie ein Support-Ticket erstellen, um Adobe über Ihre Absicht zu informieren, eine *Aufnahme* auszuführen, damit Adobe sicherstellen kann, dass der *Aufnahmevorgang* nicht unterbrochen wird. Erstellen Sie das Support-Ticket 1 Woche vor dem geplanten *Aufnahmedatum*. Sobald Sie das Support-Ticket eingereicht haben, wird Sie das Support-Team über die nächsten Schritte informieren. Erstellen Sie ein Support-Ticket mit den folgenden Details:

   * Genaues Datum und geschätzte Uhrzeit (mit Ihrer Zeitzone), zu der Sie die *Aufnahmephase* starten möchten.
   * Umgebungstyp (Phase oder Produktion), in den Sie Daten aufnehmen möchten.
   * Programm-ID.

* In der *Aufnahmephase* für die Autoreninstanz wird die gesamte Autorenbereitstellung herunterskaliert. In anderen Worten, die Autoreninstanz von AEM ist während des gesamten Aufnahmevorgangs nicht verfügbar. Stellen Sie auch sicher, dass keine Cloud Manager-Pipelines ausgeführt werden, während Sie die *Aufnahmephase* ausführen.

* Bei Verwendung von `Amazon S3` oder `Azure` als Datenspeicher im Quell-AEM-System sollte der Datenspeicher so konfiguriert werden, dass die gespeicherten Blobs nicht gelöscht werden können (gesammelter Abfall). Dadurch wird die Integrität der Indexdaten sichergestellt. Wird diese Konfiguration nicht auf diese Weise vorgenommen, kann es zu fehlgeschlagenen Extraktionen kommen, da die Integrität dieser Indexdaten nicht gewährleistet ist.

* Wenn Sie benutzerdefinierte Indizes verwenden, müssen Sie sicherstellen, dass Sie die benutzerdefinierten Indizes mit dem Knoten `tika` konfigurieren, bevor Sie das Content Transfer Tool ausführen. Weitere Informationen finden Sie unter [Vorbereiten der neuen Indexdefinition](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=de#preparing-the-new-index-definition).

* Wenn Sie Auffüllungen vornehmen möchten, ist es wichtig, dass die Inhaltsstruktur des vorhandenen Inhalts von dem Zeitpunkt an nicht geändert wird, zu dem die ursprüngliche Extraktion erfolgt, bis zum Zeitpunkt der Ausführung der Auffüllextraktion. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Stellen Sie sicher, dass Sie dies während des Migrationsprozesses einschränken.

* Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen und Auffüllungen mit `wipe=false` durchzuführen, müssen Sie aufgrund einer aktuellen Einschränkung im Content Transfer Tool die Versionsbereinigung deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu lassen und in einen Migrationssatz aufzufüllen, dann müssen Sie die Aufnahme als `wipe=true` durchführen.

* Ein Migrationssatz läuft nach längerer Inaktivität ab. Danach sind die zugehörigen Daten nicht mehr verfügbar. Bitte lesen Sie [Ablauf von Migrationssätzen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de#migration-set-expiry), um mehr darüber zu erfahren.

## Wie geht es weiter {#whats-next}

Nun, da Sie die Richtlinien, Best Practices und wichtigen Überlegungen zur Verwendung des Content Transfer Tool kennen, können Sie das Tool jetzt installieren und verwenden, beginnend mit der Erstellung eines Migrationssatzes. Weitere Informationen finden Sie unter [Erste Schritte mit dem Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).
