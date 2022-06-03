---
title: Richtlinien und Best Practices für die Verwendung des Content Transfer Tools (Veraltet)
description: Richtlinien und Best Practices für die Verwendung des Content Transfer Tools
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '1512'
ht-degree: 94%

---

# Richtlinien und Best Practices für die Verwendung des Content Transfer Tools (Veraltet) {#guidelines}

## Richtlinien und Best Practices {#best-practices}

Im folgenden Abschnitt erfahren Sie mehr über die Richtlinien und Best Practices für die Verwendung des Content Transfer Tools:

* Es wird empfohlen, ein [Revision Cleanup](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=de) und [Datenspeicher-Konsistenzprüfungen](https://helpx.adobe.com/de/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) im **Quell**-Repository durchzuführen, um potenzielle Probleme zu identifizieren und die Größe des Repositorys zu reduzieren.

* Wenn das Content Delivery Network (CDN) von AEM Cloud Author so konfiguriert ist, dass eine Whitelist von IPs vorliegt, sollte sichergestellt werden, dass die IPs der Quellumgebung auch der Zulassungsliste hinzugefügt werden, damit die Quellumgebung und die AEM Cloud-Umgebung miteinander kommunizieren können.

* In der Aufnahmephase wird empfohlen, die Aufnahme mit aktiviertem *Wischmodus* auszuführen, wobei das vorhandene Repository (Autor oder Veröffentlichung) in der Zielumgebung von AEM Cloud Service vollständig gelöscht und dann mit den Migrationssatzdaten aktualisiert wird. Dieser Modus ist viel schneller als der Nicht-Löschmodus, bei dem der Migrationssatz zusätzlich zum aktuellen Inhalt angewendet wird.

* Nach Abschluss der Aktivität zum Inhaltstransfer ist in der Cloud Service-Umgebung die korrekte Projektstruktur erforderlich, um sicherzustellen, dass der Inhalt in der Cloud Service-Umgebung erfolgreich gerendert wird.

* Stellen Sie sicher, dass im Unterverzeichnis `crx-quickstart` der AEM-Quellinstanz genügend Speicherplatz vorhanden ist, bevor Sie das Content Transfer Tool ausführen. Dies ist notwendig, da das Content Transfer Tool eine lokale Kopie des Repositorys erstellt, die später in den Migrationssatz hochgeladen wird.
Die allgemeine Formel zur Berechnung des erforderlichen freien Festplattenspeicherplatzes lautet wie folgt:
   `data store size + node store size * 1.5`

   * *Datenspeichergröße*: Das Content Transfer Tool verwendet 64 GB, auch wenn der eigentliche Datenspeicher größer ist.
   * *Knotenspeichergröße*: Größe des Segmentspeicherverzeichnisses oder der MongoDB-Datenbank.
Bei einer Segmentspeichergröße von 20 GB wären daher 94 GB freier Speicherplatz erforderlich.

* Ein Migrationssatz muss während der gesamten Aktivität zum Content-Transfer verwaltet werden, um das Auffüllen von Content zu unterstützen. Da während der Aktivität zum Content-Transfer maximal zehn Migrationssätze gleichzeitig erstellt und verwaltet werden können, wird empfohlen, das Content Repository entsprechend zu unterteilen, um sicherzustellen, dass Ihnen ausreichend Migrationssätze zur Verfügung stehen.

## Wichtige Überlegungen vor der Verwendung des Content Transfer Tools {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transfer Tools:

* Die Mindest-Systemanforderungen für das Content Transfer Tool sind AEM 6.3 + und JAVA 8. Wenn Sie eine niedrigere AEM-Version verwenden, müssen Sie Ihr Content-Repository auf AEM 6.5 aktualisieren, um das Content Transfer Tool verwenden zu können.

* Java muss in der AEM-Umgebung konfiguriert werden, damit der `java`-Befehl vom Benutzer, der AEM startet, ausgeführt werden kann.

* Es wird empfohlen, ältere Versionen des Content Transfer Tools bei der Installation der Version 1.3.0 zu deinstallieren, da es eine wesentliche Änderung der Architektur im Tool gab. Mit 1.3.0 sollten Sie außerdem neue Migrationssets erstellen und die Extraktion und Aufnahme der neuen Migrationssätze erneut ausführen.

* Das Content Transfer Tool kann mit den folgenden Arten von Datenspeicher genutzt werden: Dateispeicher, S3-Datenspeicher, freigegebener S3-Datenspeicher und Azure Blob-Datenspeicher.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, müssen Sie dafür sorgen, dass Ihre Umgebung aktuell ist bzw. auf die neueste Version aktualisiert wird. Wenn Sie eine *Produktionsumgebung* nutzen, wird diese automatisch aktualisiert.

* Um das Content Transfer Tool verwenden zu können, müssen Sie in Ihrer Quellinstanz ein Benutzer mit Administratorrechten sein und zur lokalen AEM-Gruppe **Administratoren** in der Cloud Service-Instanz gehören, an die Sie Inhalte übertragen. Unberechtigte Benutzer können das Zugriffs-Token zur Verwendung des Content Transfer Tools nicht abrufen.

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in dem Inhalte erfasst werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **Administratoren** hinzugefügt werden. Der Benutzer muss der **Administratoren** um das Zugriffstoken für das Content Transfer Tool abzurufen.

* Das Content Transfer-Tool unterstützt nicht das Zusammenführen von Cloud Services aus mehreren Quellen in der Zielinstanz, wenn der Inhalt aus den beiden Quellen in die gleichen Pfade auf dem Ziel verschoben wird. Um Cloud Service aus mehreren Quellen in eine Zielquellen-Instanz zu verschieben, müssen Sie sicherstellen, dass sich die Inhaltspfade aus den Quellen nicht überschneiden.

* Das Zugriffs-Token kann gelegentlich ablaufen, entweder nach einem bestimmten Zeitraum oder nach einem Upgrade der Cloud Service-Umgebung. Wenn das Zugriffs-Token abgelaufen ist, können Sie keine Verbindung zur Cloud Service-Instanz herstellen und müssen das neue Zugriffs-Token abrufen. Als Statussymbol für einen vorhandenen Migrationssatz wird eine rote Wolke angezeigt. Wenn Sie mit dem Mauszeiger darauf zeigen, wird eine Meldung eingeblendet.

* Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Der im Migrationssatz angegebene Inhalt wird in die ausgewählte Zielinstanz aufgenommen. Der Benutzer kann einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen. Es wird empfohlen, beim Verschieben von Inhalten in eine Produktionsinstanz CTT in der Quellautoreninstanz zu installieren, um Inhalte in die Zielautoreninstanz zu verschieben, und CTT in ähnlicher Weise in der Quell-Veröffentlichungsinstanz zu installieren, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben. Weitere Informationen finden Sie unter [Ausführen des Content Transfer Tools in einer Veröffentlichungsinstanz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#running-ctt-on-publish).

* Die vom Content Transfer Tool übertragenen Benutzer und Gruppen sind nur diejenigen, die vom Content zur Erfüllung der Berechtigungen benötigt werden. Der *Extraktions*-Vorgang kopiert das gesamte `/home` in den Migrationssatz und der *Aufnahme*-Vorgang kopiert alle Benutzer und Gruppen, auf die in den ACLs der migrierten Inhalte verwiesen wird. Informationen zum automatischen Zuordnen der vorhandenen Benutzer und Gruppen zu ihren IMS-IDs finden Sie unter [Verwenden des User Mapping Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#cloud-migration).

* Während der Extraktionsphase wird das Content Transfer Tool in einer aktiven AEM-Quellinstanz ausgeführt.

* Nachdem die *Extraktionsphase* des Inhaltstransfers abgeschlossen und die *Aufnahmephase* zur Aufnahme von Inhalt in Ihre *Staging*- oder *Produktionsinstanzen* von AEM as a Cloud Service begonnen wird, müssen Sie ein Support-Ticket erstellen, um Adobe über Ihre Absicht zu informieren, eine *Aufnahme* auszuführen, damit Adobe sicherstellen kann, dass der *Aufnahmevorgang* nicht unterbrochen wird. Erstellen Sie das Support-Ticket 1 Woche vor dem geplanten *Aufnahmedatum*. Sobald Sie das Support-Ticket eingereicht haben, wird Sie das Support-Team über die nächsten Schritte informieren. Erstellen Sie ein Support-Ticket mit den folgenden Details:

   * Genaues Datum und geschätzte Uhrzeit (mit Ihrer Zeitzone), zu der Sie die *Aufnahmephase* starten möchten.
   * Umgebungstyp (Phase oder Produktion), in den Sie Daten aufnehmen möchten.
   * Programm-ID.

* In der *Aufnahmephase* für die Autoreninstanz wird die gesamte Autorenimplementierung herunterskaliert. In anderen Worten, die Autoreninstanz von AEM ist während des gesamten Aufnahmevorgangs nicht verfügbar. Stellen Sie auch sicher, dass keine Cloud Manager-Pipelines ausgeführt werden, während Sie die *Aufnahmephase* ausführen.

* Bei Verwendung von `Amazon S3` oder `Azure` als Datenspeicher im Quell-AEM-System sollte der Datenspeicher so konfiguriert werden, dass die gespeicherten Blobs nicht gelöscht werden können (gesammelter Abfall). Dadurch wird die Integrität der Indexdaten sichergestellt. Wird diese Konfiguration nicht auf diese Weise vorgenommen, kann es zu fehlgeschlagenen Extraktionen kommen, da die Integrität dieser Indexdaten nicht gewährleistet ist.

* Wenn Sie benutzerdefinierte Indizes verwenden, müssen Sie sicherstellen, dass Sie die benutzerdefinierten Indizes mit dem Knoten `tika` konfigurieren, bevor Sie das Content Transfer Tool ausführen. Weitere Informationen finden Sie unter [Vorbereiten der neuen Indexdefinition](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=de#preparing-the-new-index-definition).

* Wenn Sie Auffüllungen vornehmen möchten, ist es wichtig, dass die Inhaltsstruktur des vorhandenen Inhalts von dem Zeitpunkt an nicht geändert wird, zu dem die ursprüngliche Extraktion erfolgt, bis zum Zeitpunkt der Ausführung der Auffüllextraktion. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Stellen Sie sicher, dass Sie dies während des Migrationsprozesses einschränken.

* Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen und Auffüllungen mit `wipe=false` durchzuführen, müssen Sie aufgrund einer aktuellen Einschränkung im Content Transfer Tool die Versionsbereinigung deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu lassen und in einen Migrationssatz aufzufüllen, dann müssen Sie die Aufnahme als `wipe=true` durchführen.

## Wie geht es weiter {#whats-next}

Nun, da Sie die Richtlinien, Best Practices und wichtigen Überlegungen zur Verwendung des Content Transfer Tool kennen, können Sie das Tool jetzt installieren und verwenden, beginnend mit der Erstellung eines Migrationssatzes. Weitere Informationen finden Sie unter [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de).
