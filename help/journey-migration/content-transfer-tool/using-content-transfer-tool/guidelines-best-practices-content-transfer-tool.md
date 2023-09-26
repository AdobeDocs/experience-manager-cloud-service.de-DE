---
title: Richtlinien und Best Practices für die Verwendung des Content Transfer Tool
description: Erfahren Sie mehr über die Richtlinien und Best Practices für die Verwendung des Content Transfer Tool.
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
source-git-commit: d67c5c9baafb9b7478f1d1c2ad924f5a8250a1ee
workflow-type: tm+mt
source-wordcount: '1554'
ht-degree: 60%

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
* Verbesserte Benutzererfahrung durch verbesserte Ladezustände, Limits und Fehlerbehandlung
* Aufnahmeprotokolle bleiben erhalten und stehen immer zur Fehlerbehebung zur Verfügung.

Um mit der Verwendung der neuen Version zu beginnen, deinstallieren Sie ältere Versionen des Content Transfer Tool. Dies ist erforderlich, da die neue Version mit einer größeren Veränderung der Architektur einhergeht. Mit Version 2.x erstellen Sie Migrationssätze und führen die Extraktion und Aufnahme auf den Sets erneut aus.
Versionen vor 2.0.0 werden nicht unterstützt. Es wird empfohlen, die neueste Version zu verwenden.

Die folgenden Richtlinien und Best Practices gelten für die neue Version des Content Transfer Tool:

* Ausführen [Revisionsbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=de) und [Konsistenzprüfungen von Datenspeichern](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16550.html?lang=de) auf **source** Repository, sodass Sie potenzielle Probleme erkennen und die Größe des Repositorys reduzieren können.

* In der Aufnahmephase empfiehlt Adobe, die Aufnahme mit der *wischen* Modus aktiviert, bei dem das vorhandene Repository (Autor oder Veröffentlichung) in der Adobe Experience Manager-Zielumgebung (AEM) gelöscht wird. Aktualisieren Sie dann mit den Migrationssatzdaten. Dieser Modus ist schneller als der Nicht-Wischmodus, bei dem der Migrationssatz zusätzlich zum aktuellen Inhalt angewendet wird.

* Nach Abschluss der Aktivität zum Inhaltstransfer ist in der Cloud Service-Umgebung die korrekte Projektstruktur erforderlich, um sicherzustellen, dass der Inhalt in der Cloud Service-Umgebung erfolgreich gerendert wird.

* Stellen Sie sicher, dass im Unterverzeichnis `crx-quickstart` der AEM-Quellinstanz genügend Speicherplatz vorhanden ist, bevor Sie das Content Transfer Tool ausführen. Dies ist notwendig, da das Content Transfer Tool eine lokale Kopie des Repositorys erstellt, die später in den Migrationssatz hochgeladen wird.
Die allgemeine Formel zur Berechnung des erforderlichen freien Speicherplatzes lautet wie folgt:
  `data store size + node store size * 1.5`

   * *Datenspeichergröße*: Das Content Transfer Tool verwendet 64 GB, auch wenn der eigentliche Datenspeicher größer ist.
   * *Knotenspeichergröße*: Größe des Segmentspeicherverzeichnisses oder der MongoDB-Datenbank.
Bei einer Segmentspeichergröße von 20 GB wären daher 94 GB freier Speicherplatz erforderlich.

* Während der gesamten Übertragung von Inhalten muss ein Migrationssatz beibehalten werden, um die Auffüllung von Inhalten zu unterstützen. Es können maximal 20 Migrationssätze pro Projekt in Cloud Acceleration Manager erstellt und gepflegt werden, während die Aktivität zum Inhaltstransfer stattfindet. Wenn mehr als 20 Migrationssätze benötigt werden, erstellen Sie ein zweites Projekt in Cloud Acceleration Manager. Dies erfordert jedoch zusätzliches Projektmanagement und Out-of-Product-Governance, um zu verhindern, dass Inhalte auf dem Ziel von mehreren Benutzern überschrieben werden.

* Ändern Sie nicht das Installationsverzeichnis des CTT-Tools. Standardmäßig findet die Installation im Pfad crx-quickstart/cloud-migration statt. Dieser spezifische Speicherort wird intern von anderen Bibliotheken verwendet. Eine Änderung dieses Pfads kann zu Extraktionsproblemen führen.

## Wichtige Überlegungen vor der Verwendung des Content Transfer Tools {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transfer Tools:

* Die Systemanforderungen für das Content Transfer Tool sind AEM 6.3 + und Java™ 8. Wenn Sie eine niedrigere AEM verwenden, aktualisieren Sie Ihr Content Repository auf AEM 6.5, um das Content Transfer Tool zu verwenden.

* Java™ muss in der AEM-Umgebung konfiguriert sein, damit der Befehl `java` von der Person ausgeführt werden kann, die AEM startet.

* Das Content Transfer Tool kann mit den folgenden Arten von Datenspeicher genutzt werden: Dateispeicher, S3-Datenspeicher, freigegebener S3-Datenspeicher und Azure Blob-Datenspeicher.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, müssen Sie dafür sorgen, dass Ihre Umgebung aktuell ist bzw. auf die neueste Version aktualisiert wird. Wenn Sie eine *Produktionsumgebung* nutzen, wird diese automatisch aktualisiert.

* Um eine Aufnahme zu starten, müssen Sie der lokalen AEM angehören **Administratoren** -Gruppe in der Cloud Service-Instanz, an die Sie Inhalte übertragen. Unberechtigte Benutzer können die Aufnahme nicht starten, ohne das Migrationstoken manuell angeben zu müssen.

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in dem Inhalte erfasst werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für einen Administrator, der der **Administratoren** hinzugefügt. Der Benutzer muss in die **Administratoren** -Gruppe, um das Zugriffstoken für das Content Transfer Tool abzurufen.

* Aufnahmen unterstützen nicht das Zusammenführen von Inhalten aus mehreren Quellen in der Zielinstanz von Cloud Service, wenn die Inhalte aus den beiden Quellen in dieselben Pfade auf dem Ziel verschoben werden. Um Cloud Service aus mehreren Quellen in eine Zielquellen-Instanz zu verschieben, stellen Sie sicher, dass sich die Inhaltspfade aus den Quellen nicht überschneiden.

* Der Extraktionsschlüssel ist 14 Tage nach seiner Erstellung oder Erneuerung gültig. Er kann jederzeit erneuert werden. Wenn der Extraktionsschlüssel abgelaufen ist, können Sie keine Extraktion durchführen.

* Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Alle Inhalte, die im Migrationssatz angegeben sind, werden in die gewählte Zielinstanz aufgenommen. Benutzende können einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen. Adobe empfiehlt, beim Verschieben von Inhalten auf eine Produktionsinstanz die CTT auf der Quellautorinstanz zu installieren, um Inhalte in die Zielautorinstanz zu verschieben. Installieren Sie auf ähnliche Weise CTT auf der Quell-Veröffentlichungsinstanz, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben. Weitere Einzelheiten finden Sie unter [Ausführen des Content Transfer Tools auf einer Veröffentlichungsinstanz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de#running-tool).

* Die vom Content Transfer Tool übertragenen Benutzenden und Gruppen sind nur diejenigen, die vom Inhalt zur Erfüllung der Berechtigungen benötigt werden. Im _Extraktionsprozess_ wird alles unter `/home` in den Migrationssatz kopiert und eine Benutzerzuordnung erstellt, indem ein aus der E-Mail-Adresse jedes Benutzers bzw. jeder Benutzerin generiertes Feld hinzugefügt wird. Weitere Informationen finden Sie unter [Benutzerzuordnung und Prinzipalmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md). Im _Aufnahmeprozess_ werden alle Benutzenden und Gruppen, auf die in den migrierten Inhalts-ACLs verwiesen wird, kopiert. Siehe [Migrieren geschlossener Benutzergruppen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) für zusätzliche Überlegungen zu Gruppen, die in einer CUG-Richtlinie (Closed User Group, geschlossene Benutzergruppe) verwendet werden.

* Während der Extraktionsphase wird das Content Transfer Tool in einer aktiven AEM-Quellinstanz ausgeführt.

* Erstellen Sie ein Support-Ticket nach Abschluss der *Extraktionsphase* des Prozesses zur Inhaltsübertragung und vor dem Start der *Aufnahmephase*, um Inhalte in Ihre *Staging*- oder *Produktionsinstanzen* von AEM as a Cloud Service aufzunehmen. Adobe über Ihre Absicht informieren, *Aufnahme* damit Adobe sicherstellen kann, dass während der *Aufnahme* -Prozess. Öffnen Sie das Support-Ticket eine Woche vor dem geplanten *Aufnahmedatum*. Nachdem Sie das Support-Ticket gesendet haben, bietet das Supportteam Anleitungen zu den nächsten Schritten an. Sie können ein Support-Ticket mit den folgenden Details senden:

   * Genaues Datum und geschätzte Uhrzeit (mit Ihrer Zeitzone), zu der Sie die *Aufnahmephase* starten möchten.
   * Umgebungstyp (Phase oder Produktion), in den Sie Daten aufnehmen möchten.
   * Programm-ID.

* In der *Aufnahmephase* für die Autoreninstanz wird die gesamte Autorenbereitstellung herunterskaliert. Das bedeutet, dass die AEM während des gesamten Aufnahmevorgangs nicht verfügbar ist. Stellen Sie außerdem sicher, dass keine Cloud Manager-Pipelines ausgeführt werden, während Sie die *Aufnahme* Phase.

* Bei Verwendung von `Amazon S3` oder `Azure` als Datenspeicher im Quell-AEM-System sollte der Datenspeicher so konfiguriert werden, dass die gespeicherten Blobs nicht gelöscht werden können (gesammelter Abfall). Dadurch wird die Integrität der Indexdaten sichergestellt. Wird diese Konfiguration nicht auf diese Weise vorgenommen, kann es zu fehlgeschlagenen Extraktionen kommen, da die Integrität dieser Indexdaten nicht gewährleistet ist.

* Wenn Sie benutzerdefinierte Indizes verwenden, müssen Sie sicherstellen, dass Sie die benutzerdefinierten Indizes mit dem Knoten `tika` konfigurieren, bevor Sie das Content Transfer Tool ausführen. Siehe [Vorbereiten der neuen Indexdefinition](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#preparing-the-new-index-definition) für weitere Details.

* Wenn Sie Auffüllungen durchführen möchten, darf sich die Inhaltsstruktur des vorhandenen Inhalts nicht von dem Zeitpunkt an ändern, zu dem die erste Extraktion erfolgt, bis zum Zeitpunkt der Auffüllextraktion. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Achten Sie darauf, dies während des Migrationsprozesses entsprechend einzuschränken.

* Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen und Auffüllungen mit `wipe=false` durchzuführen, müssen Sie aufgrund einer aktuellen Einschränkung im Content Transfer Tool die Versionsbereinigung deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu lassen und in einen Migrationssatz aufzufüllen, dann müssen Sie die Aufnahme als `wipe=true` durchführen.

* Ein Migrationssatz läuft nach einer längeren Inaktivitätsdauer ab, nach der seine Daten nicht mehr verfügbar sind. Überprüfen [Ablauf des Migrationssatzes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de#migration-set-expiry) für weitere Details.

## Wie geht es weiter {#whats-next}

Nun, da Sie die Richtlinien, Best Practices und wichtigen Überlegungen zur Verwendung des Content Transfer Tool kennen, können Sie das Tool jetzt installieren und verwenden, beginnend mit der Erstellung eines Migrationssatzes. Siehe [Erste Schritte mit dem Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).
