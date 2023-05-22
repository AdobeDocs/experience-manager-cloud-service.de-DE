---
title: Richtlinien und Best Practices für die Verwendung des Content Transfer Tools   (Frühere Version)
description: Richtlinien und Best Practices für die Verwendung des Content Transfer Tools
hide: true
hidefromtoc: true
exl-id: 03449606-0fb4-4a9f-9abb-6b17c27a6046
source-git-commit: eadcf71aa96298383b05e61251dfeb5f345df6b9
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 100%

---

# Richtlinien und Best Practices für die Verwendung des Content Transfer Tools   (Frühere Version) {#guidelines}

## Richtlinien und Best Practices {#best-practices}

Im folgenden Abschnitt erfahren Sie mehr über die Richtlinien und Best Practices für die Verwendung des Content Transfer Tools:

* Führen Sie eine [Revisionsbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=de) und [Datenspeicher-Konsistenzprüfungen](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16550.html?lang=de) auf dem **Quell**-Repository aus, um mögliche Probleme zu identifizieren und die Größe des Repositorys zu reduzieren.

* Wenn die AEM Cloud Author Content Delivery Network (CDN)-Konfiguration so konfiguriert ist, dass sie eine Zulassungsliste von IPs enthält, stellen Sie sicher, dass die IPs der Quellumgebung auch der Zulassungsliste hinzugefügt werden. Dadurch wird sichergestellt, dass die Quellumgebung und AEM Cloud-Umgebung miteinander kommunizieren können.

* Führen Sie die Aufnahme mit dem aktivierten Modus *Wischen* durch, bei dem das vorhandene Repository (Author oder Publish) in der Zielumgebung des AEM Cloud Service gelöscht und dann mit den Daten des Migrationssatzes aktualisiert wird. Dieser Modus ist viel schneller als der Nicht-Löschmodus, bei dem der Migrationssatz zusätzlich zum aktuellen Inhalt angewendet wird.

* Nach Abschluss der Aktivität zum Inhaltstransfer ist in der Cloud Service-Umgebung die korrekte Projektstruktur erforderlich, um sicherzustellen, dass der Inhalt in der Cloud Service-Umgebung erfolgreich gerendert wird.

* Stellen Sie sicher, dass im Unterverzeichnis `crx-quickstart` der AEM-Quellinstanz genügend Speicherplatz vorhanden ist, bevor Sie das Content Transfer Tool ausführen. Dies ist notwendig, da das Content Transfer Tool eine lokale Kopie des Repositorys erstellt, die später in den Migrationssatz hochgeladen wird.
Die allgemeine Formel zur Berechnung des erforderlichen freien Speicherplatzes lautet wie folgt:
   `data store size + node store size * 1.5`

   * *Datenspeichergröße*: Das Content Transfer Tool verwendet 64 GB, auch wenn der eigentliche Datenspeicher größer ist.
   * *Knotenspeichergröße*: Größe des Segmentspeicherverzeichnisses oder der MongoDB-Datenbank.
Bei einer Segmentspeichergröße von 20 GB wären daher 94 GB freier Speicherplatz erforderlich.

* Während der gesamten Übertragung von Inhalten muss ein Migrationssatz beibehalten werden, um die Auffüllung von Inhalten zu unterstützen. Da maximal zehn Migrationssätze gleichzeitig während der Inhaltsübertragungsaktivität erstellt und gepflegt werden können, wird empfohlen, das Content-Repository entsprechend zu unterteilen. Dadurch wird sichergestellt, dass Ihnen die Migrationssätze nicht ausgehen.

## Wichtige Überlegungen vor der Verwendung des Content Transfer Tools {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transfer Tools:

* Die Systemanforderungen für das Content Transfer Tool sind AEM 6.3 + und Java™ 8. Wenn Sie eine niedrigere AEM-Version verwenden, müssen Sie Ihr Content-Repository auf AEM 6.5 aktualisieren, um das Content Transfer Tool verwenden zu können.

* Java™ muss in der AEM-Umgebung konfiguriert sein, damit der Befehl `java` von der Person ausgeführt werden kann, die AEM startet.

* Deinstallieren Sie vor der Installation der Version 1.3.0 ältere Versionen des Content Transfer Tools, da es eine wesentliche Änderung der Architektur im Tool gab. Mit 1.3.0 sollten Sie außerdem neue Migrationssätze erstellen und die Extraktion und Aufnahme der neuen Migrationssätze erneut ausführen.

* Das Content Transfer Tool kann mit den folgenden Arten von Datenspeicher genutzt werden: Dateispeicher, S3-Datenspeicher, freigegebener S3-Datenspeicher und Azure Blob-Datenspeicher.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, müssen Sie dafür sorgen, dass Ihre Umgebung aktuell ist bzw. auf die neueste Version aktualisiert wird. Wenn Sie eine *Produktionsumgebung* nutzen, wird diese automatisch aktualisiert.

* Um das Content Transfer Tool verwenden zu können, müssen Sie in Ihrer Quellinstanz ein Benutzer mit Administratorrechten sein und zur lokalen AEM-Gruppe **Administratoren** in der Cloud Service-Instanz gehören, an die Sie Inhalte übertragen. Unberechtigte Benutzende können das Zugriffstoken zur Verwendung des Content Transfer Tools nicht abrufen.

* Wenn die Einstellung **Vorhandene Inhalte in der Cloud-Instanz vor der Aufnahme löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein Repository erstellt, in das die Inhalte aufgenommen werden. Dieser Workflow bedeutet, dass alle Einstellungen einschließlich der Berechtigungen auf der Zielinstanz von Cloud Service zurückgesetzt werden. Dieses Verhalten trifft auch für Admin-Benutzerinnen und -Benutzer zu, die der Gruppe **Administratoren** hinzugefügt werden. Die Person muss in die Gruppe **Administratoren** aufgenommen werden, um das Zugriffstoken für das Content Transfer Tool abrufen zu können.

* Das Content Transfer Tool unterstützt nicht das Zusammenführen von Inhalten aus mehreren Quellen in der Ziel-Cloud-Service-Instanz, wenn die Inhalte aus den beiden Quellen in dieselben Pfade auf dem Ziel verschoben werden. Wenn Sie Inhalte aus mehreren Quellen in eine einzige Cloud-Service-Zielinstanz verschieben möchten, müssen Sie sicherstellen, dass sich die Inhaltspfade der Quellen nicht überschneiden.

* Das Zugriffstoken kann gelegentlich ablaufen, entweder nach einem bestimmten Zeitraum oder nach einem Upgrade der Cloud Service-Umgebung. Wenn das Zugriffstoken abgelaufen ist, können Sie keine Verbindung zur Cloud Service-Instanz herstellen. In diesem Fall müssen Sie das neue Zugriffstoken abrufen. Das Statussymbol eines bestehenden Migrationssatzes ändert sich in eine rote Wolke und zeigt eine Meldung an, wenn Sie den Mauszeiger darüber bewegen.

* Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Alle Inhalte, die im Migrationssatz angegeben sind, werden in die gewählte Zielinstanz aufgenommen. Benutzende können einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen. Wenn Sie Inhalte in eine Produktionsinstanz verschieben, installieren Sie CTT auf der Quell-Autoreninstanz, um Inhalte in die Ziel-Autoreninstanz zu verschieben. Installieren Sie auf ähnliche Weise CTT auf der Quell-Veröffentlichungsinstanz, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben. Weitere Einzelheiten finden Sie unter [Ausführen des Content Transfer Tools auf einer Veröffentlichungsinstanz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de#running-tool).

* Die vom Content Transfer Tool übertragenen Benutzenden und Gruppen sind nur diejenigen, die vom Inhalt zur Erfüllung der Berechtigungen benötigt werden. Der *Extraktions*-Vorgang kopiert das gesamte `/home` in den Migrationssatz und der *Aufnahme*-Vorgang kopiert alle Benutzer und Gruppen, auf die in den ACLs der migrierten Inhalte verwiesen wird. Informationen zum automatischen Zuordnen der vorhandenen Benutzer und Gruppen zu ihren IMS-IDs finden Sie unter [Verwenden des User Mapping Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=de).

* Während der Extraktionsphase wird das Content Transfer Tool in einer aktiven AEM-Quellinstanz ausgeführt.

* Erstellen Sie ein Support-Ticket nach Abschluss der *Extraktionsphase* des Prozesses zur Inhaltsübertragung und vor dem Start der *Aufnahmephase*, um Inhalte in Ihre *Staging*- oder *Produktionsinstanzen* von AEM as a Cloud Service aufzunehmen. Benachrichtigen Sie Adobe über die beabsichtigte *Aufnahme*, damit Adobe sicherstellen kann, dass es während des *Aufnahmeprozesses* zu keiner Unterbrechung kommt. Öffnen Sie das Support-Ticket eine Woche vor dem geplanten *Aufnahmedatum*. Nachdem Sie das Support-Ticket eingereicht haben, gibt Ihnen das Support-Team eine Anleitung für die nächsten Schritte. Erstellen Sie ein Support-Ticket mit den folgenden Details:

   * Genaues Datum und geschätzte Uhrzeit (mit Ihrer Zeitzone), zu der Sie die *Aufnahmephase* starten möchten.
   * Umgebungstyp (Phase oder Produktion), in den Sie Daten aufnehmen möchten.
   * Programm-ID.

* In der *Aufnahmephase* für die Autoreninstanz wird die gesamte Autorenbereitstellung herunterskaliert. Dieser Prozess bedeutet, dass AEM Author während der gesamten Aufnahme nicht verfügbar ist. Stellen Sie auch sicher, dass keine Cloud Manager-Pipelines ausgeführt werden, während Sie die *Aufnahmephase* ausführen.

* Bei Verwendung von `Amazon S3` oder `Azure` als Datenspeicher im Quell-AEM-System sollte der Datenspeicher so konfiguriert werden, dass die gespeicherten Blobs nicht gelöscht werden können (gesammelter Abfall). Dadurch wird die Integrität der Indexdaten sichergestellt. Wird diese Konfiguration nicht auf diese Weise vorgenommen, kann es zu fehlgeschlagenen Extraktionen kommen, da die Integrität dieser Indexdaten nicht gewährleistet ist.

* Wenn Sie benutzerdefinierte Indizes verwenden, müssen Sie sicherstellen, dass Sie die benutzerdefinierten Indizes mit dem Knoten `tika` konfigurieren, bevor Sie das Content Transfer Tool ausführen. Weitere Informationen finden Sie unter [Vorbereiten der neuen Indexdefinition](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=de#preparing-the-new-index-definition).

* Wenn Sie eine Auffüllung vornehmen wollen, stellen Sie sicher, dass die Inhaltsstruktur der vorhandenen Inhalte zwischen der ersten Extraktion und der Auffüllungsextraktion nicht verändert wird. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Achten Sie darauf, dies während des Migrationsprozesses entsprechend einzuschränken.

* Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen und Auffüllungen mit `wipe=false` durchzuführen, müssen Sie aufgrund einer aktuellen Einschränkung im Content Transfer Tool die Versionsbereinigung deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu lassen und in einen Migrationssatz aufzufüllen, dann müssen Sie die Aufnahme als `wipe=true` durchführen.

## Wie geht es weiter {#whats-next}

Nun, da Sie die Richtlinien, Best Practices und wichtigen Überlegungen zur Verwendung des Content Transfer Tool kennen, können Sie das Tool jetzt installieren und verwenden, beginnend mit der Erstellung eines Migrationssatzes. Weitere Informationen finden Sie unter [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de).
