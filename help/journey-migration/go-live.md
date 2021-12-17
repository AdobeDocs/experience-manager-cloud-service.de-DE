---
title: Live-Schaltung
description: Erfahren Sie, wie Sie die Migration durchführen, sobald der Code und der Inhalt Cloud-fähig sind.
source-git-commit: fe0261fa9708b2250b6f5e4931100a9fc006e55d
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 4%

---


# Live-Schaltung {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Vorbereiten der Live-Schaltung"
>abstract="Um eine reibungslose und erfolgreiche Live-Schaltung von AEM as a Cloud Service sicherzustellen, sollten Sie u. a. Freeze-Perioden von Code und Inhalt, Testdurchläufe, Auffüllungen des Inhalts, Leistungstests und Sicherheitstests planen."

In diesem Teil der Journey erfahren Sie, wie Sie die Migration planen und durchführen können, sobald sowohl der Code als auch der Inhalt bereit sind, auf AEM as a Cloud Service übertragen zu werden. Darüber hinaus erfahren Sie, welche Best Practices und bekannten Einschränkungen bei der Durchführung der Migration gelten.

## Die bisherige Entwicklung {#story-so-far}

In den vorherigen Phasen der Journey:

* Sie haben gelernt, wie Sie mit dem Übergang zu AEM as a Cloud Service im [Erste Schritte](/help/journey-migration/getting-started.md) Seite.
* Durch Lesen der [Bereitschaftsphase](/help/journey-migration/readiness.md)
* Machen Sie sich mit den Tools und Prozessen vertraut, mit denen Sie Code und Content Cloud mit der [Implementierungsphase](/help/journey-migration/implementation.md).

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie die Migration zu AEM as a Cloud Service durchführen können, sobald Sie mit den vorherigen Schritten des Journey vertraut sind. Sie erfahren, wie Sie die ursprüngliche Produktionsmigration durchführen und welche Best Practices bei der Migration auf AEM as a Cloud Service anwenden.

## Erstmalige Produktionsmigration {#initial-migration}

Bevor Sie die Produktionsmigration durchführen können, befolgen Sie die im Abschnitt [Inhaltsmigrationsstrategie und -zeitleiste](/help/journey-migration/implementation.md##strategy-timeline) Abschnitt [Implementierungsphase](/help/journey-migration/implementation.md).

* Starten Sie die Migration von der Produktion basierend auf den Erfahrungen, die Sie während der AEM as a Cloud Service Staging-Migration für Klone gesammelt haben:
   * Autor/Autor
   * Publish-Publish

* Validieren Sie die Inhalte, die sowohl in der AEM as a Cloud Service Autoren- als auch in der Veröffentlichungsstufe erfasst werden.
* Weisen Sie das Inhaltserstellungsteam an, zu vermeiden, dass Inhalte sowohl an der Quelle als auch am Ziel verschoben werden, bis die Aufnahme abgeschlossen ist.
* Neue Inhalte können hinzugefügt, bearbeitet oder gelöscht werden. Verschieben Sie sie jedoch nicht. Dies gilt sowohl für die Quelle als auch für das Ziel.
* Notieren Sie die [Zeitaufwand](/help/journey-migration/implementation.md#gathering-data) für die vollständige Extraktion und Aufnahme, um eine Schätzung für künftige zusätzliche Migrationszeitpläne zu erhalten.
* Erstellen Sie eine [Migrationsplaner](/help/journey-migration/implementation.md#migration-plan) für Autoren- und Veröffentlichungsinstanz.

## Inkrementelle Top-Ups {#top-up}

Nach der ersten Migration aus der Produktion müssen Sie inkrementelle Auffüllungen durchführen, um sicherzustellen, dass Ihr Inhalt in der Cloud-Instanz auf den neuesten Stand gebracht wird. Daher wird empfohlen, die folgenden Best Practices zu befolgen:

* Erfassen Sie Daten zur Inhaltsmenge. Beispiel: pro Woche, zwei Wochen oder Monat.
* Planen Sie die Auffüllungen so, dass Sie mehr als 48 Stunden Inhaltsextraktion und -aufnahme vermeiden. Dies wird empfohlen, damit die Inhaltsauffüllungen in einen Wochenendzeitrahmen passen.
* Planen Sie die Anzahl der erforderlichen Auffüllungen und verwenden Sie diese Schätzungen für die Planung um das Aufschaltdatum.

## Identifizieren von Code- und Zeitleisten zum Einfrieren von Inhalten für die Migration {#code-content-freeze}

Wie bereits erwähnt, müssen Sie einen Einfrierzeitraum für Code und Inhalt planen. Verwenden Sie die folgenden Fragen, um die Gefrierzeit zu planen:

* Wie lange muss ich die Inhaltserstellung einfrieren?
* Wie lange sollte ich mein Versand-Team bitten, keine neuen Funktionen mehr hinzuzufügen?

Um die erste Frage zu beantworten, sollten Sie die Zeit in Betracht ziehen, die für die Durchführung von Testläufen in Nicht-Produktionsumgebungen benötigt wurde. Um die zweite Frage zu beantworten, benötigen Sie eine enge Zusammenarbeit zwischen dem Team, das neue Funktionen hinzufügt, und dem Team, das den Code refaktoriert. Das Ziel sollte darin bestehen sicherzustellen, dass der gesamte Code, der zur vorhandenen Bereitstellung hinzugefügt wird, auch der Cloud Services-Verzweigung hinzugefügt, getestet und bereitgestellt wird. Im Allgemeinen bedeutet dies, dass der Code-Freeze-Wert niedriger ist.

Darüber hinaus müssen Sie planen, dass der Inhalt beim Planen der endgültigen Inhaltsauffüllung einfriert.

## Best Practices {#best-practices}

Bei der Planung oder Durchführung der Migration sollten Sie die folgenden Richtlinien beachten:

* Migrieren von der Autoreninstanz zur Autoreninstanz und zur Veröffentlichungsinstanz
* Anfordern eines Produktionsklons, der verwendet werden kann für:
   * Repository-Statistiken erfassen
   * Nachweis der Migration
   * Vorbereitung des Migrationsplans
   * Identifizieren von Anforderungen zum Einfrieren von Inhalten
   * Ermitteln Sie bei der Migration von der Produktion eventuelle Upsizing-Anforderungen.

**Best Practices für Content Transfer Tool**

Stellen Sie sicher, dass Sie bei der Live-Schaltung die Inhaltsmigration in der Produktion anstatt in einem Klon ausführen. Ein guter Ansatz ist die Verwendung von [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) für die Erstmigration und führen Sie dann die Auffüllextraktionen häufig (auch täglich) aus, um kleinere Blöcke zu extrahieren und eine langfristige Belastung der AEM zu vermeiden.

Bei der Produktionsmigration sollten Sie vermeiden, das Content Transfer Tool aus einem Klon auszuführen, da:

* Wenn für einen Kunden bei Auffüllmigration Inhaltsversionen migriert werden müssen, werden die Versionen nicht durch die Ausführung des Content Transfer Tool aus einem Klon migriert. Selbst wenn der Klon häufig von einem Live-Autor neu erstellt wird, werden bei jeder Erstellung eines Klons die Checkpoints zurückgesetzt, die vom Content Transfer Tool zur Berechnung der Deltas verwendet werden.
* Da ein Klon nicht als Ganzes aktualisiert werden kann, muss das ACL Query-Paket verwendet werden, um den hinzugefügten oder bearbeiteten Inhalt zu verpacken und zu installieren, um ihn zu klonen. Das Problem bei diesem Ansatz besteht darin, dass gelöschte Inhalte in der Quellinstanz nie zum Klon gelangen, es sei denn, sie werden manuell aus Quelle und Klon gelöscht. Dadurch wird die Möglichkeit eröffnet, dass der gelöschte Produktionsinhalt nicht im Klon gelöscht und AEM as a Cloud Service wird.

**Die Auslastung Ihrer AEM beim Ausführen der Inhaltsmigration optimieren**

Beachten Sie, dass die Belastung der AEM während der Extraktionsphase größer sein wird. Beachten Sie Folgendes:

* Das Content Transfer Tool ist ein externer Java-Prozess, der einen JVM-Heap von 4 GB verwendet
* Die Nicht-AzCopy-Version lädt Binärdateien herunter, speichert sie auf einem temporären Speicherplatz auf der AEM-Autoreninstanz, belegt Datenträger-E/A und lädt sie dann in den Azure-Container hoch, der Netzwerkbandbreite verbraucht
* [AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) überträgt Blobs direkt vom Blob Store zum Azure-Container, wodurch Datenträger-E/A und Netzwerkbandbreite gespart werden. Die AzCopy-Version verwendet weiterhin die Festplatte und Netzwerkbandbreite, um die Daten aus dem Segmentspeicher in den Azure-Container zu extrahieren und hochzuladen
* Der Content Transfer Tool-Prozess ist während der Aufnahmephase weniger umfangreich auf den Systemressourcen, da nur die Erfassungslogs gestreamt werden und die Quellinstanz im Hinblick auf die Datenträger-E/A oder die Netzwerkbandbreite nicht sehr belastet ist.

## Bekannte Einschränkungen {#known-limitations}

Beachten Sie, dass die gesamte Aufnahme fehlschlägt, wenn eine der folgenden Einschränkungen im extrahierten Migrationssatz gefunden wird:

* Ein JCR-Knoten mit einem Namen, der länger als 150 Zeichen ist
* JCR-Knoten, der größer als 16 MB ist
* Jeder Benutzer/jede Gruppe mit `rep:AuthorizableID` aufgenommen wird, die bereits auf AEM as a Cloud Service vorhanden ist
* Wenn ein extrahiertes und erfasstes Asset vor der nächsten Iteration der Migration in einen anderen Pfad entweder auf der Quelle oder am Ziel verschoben wird.

## Asset-Konsistenz {#asset-health}

Im Vergleich zum Abschnitt über der Aufnahme **nicht** aufgrund der folgenden Asset-Bedenken fehlschlagen. Es wird jedoch dringend empfohlen, in diesen Szenarien die entsprechenden Schritte zu unternehmen:

* Jedes Asset, bei dem die ursprüngliche Ausgabedarstellung fehlt
* Jeder Ordner, der fehlt `jcr:content` Knoten

Beide der oben genannten Punkte werden im [Best Practice Analyzer](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) Bericht.

## Go-Live-Checkliste {#Go-Live-Checklist}

Überprüfen Sie die nachstehende Liste der Aktivitäten, um sicherzustellen, dass Sie eine reibungslose und erfolgreiche Migration durchführen können:

* Planen Sie einen Einfrierzeitraum für Code und Inhalt. Siehe auch [Zeitpläne für Code und das Einfrieren von Inhalten für die Migration](#code-content-freeze).
* Letzte Inhaltsauffüllung durchführen
* Abschließen der Testiterationen
* Ausführen von Leistungs- und Sicherheitstests
* Umstellen und die Migration auf der Produktionsinstanz durchführen

Sie können immer auf die Liste verweisen, falls Sie Ihre Aufgaben bei der Migration neu alibrieren müssen.

## Wie geht es weiter {#what-is-next}

Sobald Sie wissen, wie die Migration auf AEM as a Cloud Service durchgeführt wird, können Sie die [Nach der Live-Schaltung](/help/journey-migration/post-go-live.md) -Seite, damit Ihre Instanz reibungslos ausgeführt wird.