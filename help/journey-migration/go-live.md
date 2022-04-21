---
title: Live-Schaltung
description: Erfahren Sie, wie Sie die Migration durchführen, sobald der Code und der Inhalt Cloud-fähig sind.
exl-id: 10ec0b04-6836-4e26-9d4c-306cf743224e
source-git-commit: 9a10348251fe7559ae5d3c4a203109f1f6623bce
workflow-type: tm+mt
source-wordcount: '1644'
ht-degree: 77%

---

# Live-Schaltung {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Vorbereiten der Live-Schaltung"
>abstract="Um eine reibungslose und erfolgreiche Live-Schaltung von AEM as a Cloud Service sicherzustellen, sollten Sie u. a. Freeze-Perioden von Code und Inhalt, Testdurchläufe, Auffüllungen des Inhalts, Leistungstests und Sicherheitstests planen."

In diesem Teil der Journey erfahren Sie, wie Sie die Migration planen und durchführen können, sobald sowohl der Code als auch der Inhalt bereit sind, auf AEM as a Cloud Service übertragen zu werden. Darüber hinaus erfahren Sie, welche Best Practices und bekannten Einschränkungen bei der Durchführung der Migration gelten.

## Die bisherige Entwicklung {#story-so-far}

In den vorherigen Phasen der Tour:

* Sie haben auf der Seite [Erste Schritte](/help/journey-migration/getting-started.md) erfahren, wie Sie mit dem Übergang zu AEM as a Cloud Service beginnen können.
* Sie haben ermittelt, ob Ihre Implementierung bereit ist, in die Cloud verschoben zu werden, indem Sie die Seite [Bereitschaftsphase](/help/journey-migration/readiness.md) gelesen haben.
* Sie haben sich mit den Tools und dem Prozess vertraut gemacht, mit denen Sie Ihren Code und Inhalt für die Cloud bereit machen können, indem Sie die Seite [Implementierungsphase](/help/journey-migration/implementation.md) gelesen haben.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie die Migration zu AEM as a Cloud Service durchführen können, sobald Sie mit den vorherigen Schritten der Tour vertraut sind. Sie erfahren, wie Sie die ursprüngliche Produktionsmigration durchführen und welche Best Practices Sie bei der Migration auf AEM as a Cloud Service anwenden sollten.

## Erstmalige Produktionsmigration {#initial-migration}

Bevor Sie die Produktionsmigration durchführen können, befolgen Sie bitte die Schritte zur Anpassung und zum Nachweis der Migration, die im Abschnitt [Inhaltsmigrationsstrategie und Zeitplan](/help/journey-migration/implementation.md##strategy-timeline) der [Implementierungsphase](/help/journey-migration/implementation.md) beschrieben sind.

* Starten Sie die Migration von der Produktion basierend auf den Erfahrungen, die Sie während der Staging-Migration für Klone in AEM as a Cloud Service gesammelt haben:
   * Author-Author
   * Publish-Publish

* Validieren Sie die Inhalte, die sowohl in der Autoren- als auch in der Veröffentlichungsstufe von AEM as a Cloud Service erfasst werden.
* Weisen Sie das Inhaltserstellungs-Team an zu vermeiden, dass Inhalte sowohl an der Quelle als auch am Ziel verschoben werden, bis die Aufnahme abgeschlossen ist.
* Neue Inhalte können hinzugefügt, bearbeitet oder gelöscht werden. Verschieben Sie sie jedoch nicht. Dies gilt sowohl für die Quelle als auch für das Ziel.
* Notieren Sie den [Zeitaufwand](/help/journey-migration/implementation.md#gathering-data) für die vollständige Extraktion und Aufnahme, um eine Schätzung für künftige zusätzliche Migrationszeitpläne zu erhalten.
* Erstellen Sie jeweils einen [Migrationsplaner](/help/journey-migration/implementation.md#migration-plan) für die Autoren- und die Veröffentlichungsinstanz.

## Inkrementelles Auffüllen {#top-up}

Nach der ersten Migration aus der Produktion müssen Sie inkrementelle Auffüllungen durchführen, um sicherzustellen, dass Ihr Inhalt in der Cloud-Instanz auf den neuesten Stand gebracht wird. Daher wird empfohlen, die folgenden Best Practices zu befolgen:

* Sammeln Sie Daten zur Inhaltsmenge. Zum Beispiel: je eine Woche, zwei Wochen oder einen Monat.
* Planen Sie die Auffüllungen so, dass Sie eine mehr als 48 Stunden dauernde Inhaltsextraktion und -aufnahme vermeiden. Dies wird empfohlen, damit die Inhaltsauffüllungen in einen Wochenendzeitrahmen passen.
* Planen Sie die Anzahl der erforderlichen Auffüllungen und verwenden Sie diese Schätzungen für die Planung um den Tag der Live-Schaltung herum.

## Identifizieren von Zeitplänen für das Einfrieren von Code und Inhalten für die Migration {#code-content-freeze}

Wie bereits erwähnt, müssen Sie einen Einfrierzeitraum für Code und Inhalte planen. Verwenden Sie die folgenden Fragen, um den Einfrierzeitraum zu planen:

* Wie lange muss ich die Inhaltserstellung einfrieren?
* Für welchen Zeitraum sollte ich mein Versand-Team bitten, keine neuen Funktionen mehr hinzuzufügen?

Um die erste Frage zu beantworten, sollten Sie die Zeit in Betracht ziehen, die für die Durchführung von Testläufen in Nicht-Produktionsumgebungen benötigt wurde. Um die zweite Frage zu beantworten, benötigen Sie eine enge Zusammenarbeit zwischen dem Team, das neue Funktionen hinzufügt, und dem Team, das den Code überarbeitet. Das Ziel sollte darin bestehen sicherzustellen, dass der gesamte Code, der zur vorhandenen Implementierung hinzugefügt wird, auch zur Cloud Services-Verzweigung hinzugefügt, getestet und bereitgestellt wird. Im Allgemeinen bedeutet dies, dass die Dauer des Einfrierens von Code geringer sein wird.

Darüber hinaus müssen Sie ein Einfrieren von Inhalten einplanen, wenn die endgültige Auffüllung der Inhalte geplant ist.

## Best Practices {#best-practices}

Bei der Planung oder Durchführung der Migration sollten Sie die folgenden Richtlinien beachten:

* Migrieren von einer Autoreninstanz zur anderen und von einer Veröffentlichungsinstanz zur anderen
* Anfordern eines Produktionsklons, der für Folgendes verwendet werden kann:
   * Erfassen von Repository-Statistiken
   * Nachweis der Migration
   * Vorbereitung des Migrationsplans
   * Identifizieren von Anforderungen zum Einfrieren von Inhalten
   * Ermitteln Sie bei der Migration von der Produktion eventuelle Upsizing-Anforderungen der Produktion.

**Best Practices für das Content Transfer Tool**

Stellen Sie sicher, dass Sie bei der Live-Schaltung die Inhaltsmigration in der Produktion anstatt in einem Klon ausführen. Ein guter Ansatz ist die Verwendung von [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) für die Erstmigration. Führen Sie dann die Auffüllextraktionen häufig (z. B. täglich) aus, um kleinere Blöcke zu extrahieren und eine langfristige Belastung der AEM-Quelle zu vermeiden.

Bei der Produktionsmigration sollten Sie aus folgenden Gründen vermeiden, das Content Transfer Tool aus einem Klon auszuführen:

* Wenn für einen Kunden bei Auffüllmigration Inhaltsversionen migriert werden müssen, werden die Versionen bei Ausführung des Content Transfer Tool aus einem Klon nicht migriert. Selbst wenn der Klon häufig von einem Live-Autor neu erstellt wird, werden bei jeder Erstellung eines Klons die Checkpoints zurückgesetzt, die vom Content Transfer Tool zur Berechnung der Deltas verwendet werden.
* Da ein Klon nicht als Ganzes aktualisiert werden kann, muss das ACL Query-Paket verwendet werden, um den bei der Produktion hinzugefügten oder bearbeiteten Inhalt zu verpacken und zu installieren, damit er geklont werden kann. Das Problem bei diesem Ansatz besteht darin, dass das Löschen von Inhalten in der Quellinstanz nie zum Klon gelangt, es sei denn, sie werden manuell aus Quelle und Klon gelöscht. Dadurch besteht die Möglichkeit, dass der gelöschte Produktionsinhalt nicht im Klon gelöscht und AEM as a Cloud Service wird.

**Optimieren Sie die Belastung Ihrer AEM-Quelle bei der Migration von Inhalten**

Beachten Sie, dass die Belastung der AEM-Quelle während der Extraktionsphase größer sein wird. Beachten Sie Folgendes:

* Das Content Transfer Tool ist ein externer Java-Prozess, der einen JVM-Heap von 4 GB verwendet
* Die Nicht-AzCopy-Version lädt Binärdateien herunter, speichert sie auf einem temporären Speicherplatz auf der AEM-Autoreninstanz, was Datenträger-E/A belegt, und lädt sie dann in den Azure-Container hoch, was Netzwerkbandbreite verbraucht
* [AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) überträgt dagegen Blobs direkt vom Blob Store zum Azure-Container, wodurch Datenträger-E/A und Netzwerkbandbreite gespart werden. Die AzCopy-Version verwendet weiterhin die Festplatte und Netzwerkbandbreite, um die Daten aus dem Segmentspeicher in den Azure-Container zu extrahieren und hochzuladen
* Der Content Transfer Tool-Prozess belastet die Systemressourcen während der Aufnahmephase weniger, da nur Aufnahmeprotokolle gestreamt werden und die Quellinstanz in Bezug auf Festplatten-E/A oder Netzwerkbandbreite nicht stark belastet wird.

## Bekannte Einschränkungen {#known-limitations}

Bitte beachten Sie, dass das gesamte Ingestion fehlschlägt, wenn eine der folgenden Verletzungen von Einschränkungen als Teil des extrahierten Migrationssets gefunden wird:

* Ein JCR-Knoten mit einem Namen, der länger als 150 Zeichen ist
* Ein JCR-Knoten, der größer als 16 MB ist
* Jede(r) Benutzer/Gruppe, der/die mit `rep:AuthorizableID` aufgenommen wird und bereits in AEM as a Cloud Service vorhanden ist
* Ein extrahiertes und erfasstes Asset wird vor der nächsten Iteration der Migration in einen anderen Pfad entweder auf der Quelle oder am Ziel verschoben.

## Asset-Konsistenz {#asset-health}

Im Gegensatz zum obigen Abschnitt schlägt die Aufnahme **nicht** aufgrund der folgenden Bedenken bei Assets fehl. Es wird jedoch dringend empfohlen, in diesen Szenarien die entsprechenden Schritte zu unternehmen:

* Jedes Asset, bei dem die ursprüngliche Ausgabedarstellung fehlt
* Jeder Ordner, dessen `jcr:content`-Knoten fehlt

Die beiden oben genannten Punkte werden im [Best Practice Analyzer](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)-Bericht identifiziert und gemeldet.

## Go-Live-Checkliste {#Go-Live-Checklist}

Sehen Sie sich diese Aktivitätenliste an, um sicherzustellen, dass Sie eine reibungslose und erfolgreiche Migration durchführen.

* Führen Sie eine End-to-End-Produktions-Pipeline mit Funktions- und UI-Tests aus, um eine **immer aktuell** AEM Produkterlebnis. Sehen Sie sich die folgenden Ressourcen an.
   * [AEM-Versionsaktualisierungen](/help/implementing/deploying/aem-version-updates.md)
   * [Benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [Testen der Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md)
* Migrieren Sie Inhalte in die Produktion und stellen Sie sicher, dass beim Staging eine relevante Untergruppe zum Testen verfügbar ist.
   * Beachten Sie, dass die Best Practices von DevOps für AEM implizieren, dass der Code von der Entwicklungsumgebung in die Produktionsumgebung verschoben wird, während [Der Inhalt wird aus Produktionsumgebungen nach unten verschoben.](/help/overview/enterprise-devops.md#code-movement)
* Planen der Periode zum Einfrieren von Code und Inhalten.
   * Siehe auch Abschnitt . [Zeitpläne für Code und das Einfrieren von Inhalten für die Migration](#code-content-freeze)
* Ausführen der endgültigen Inhaltsauffüllung.
* Überprüfen Sie die Dispatcher-Konfigurationen.
   * Verwenden Sie einen lokalen Dispatcher-Validator, der die Konfiguration, Validierung und Simulation des Dispatchers lokal erleichtert
      * [Richten Sie die lokalen Dispatcher-Tools ein.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=de#prerequisites)
   * Überprüfen Sie die Konfiguration des virtuellen Hosts sorgfältig.
      * Die einfachste (und standardmäßige) Lösung besteht darin, `ServerAlias *` in Ihrer virtuellen Host-Datei im `/dispatcher/src/conf.d/available_vhostsfolder`.
         * Dadurch können die von Produktfunktionstests, Dispatcher-Cache-Invalidierung und Klonen verwendeten Host-Aliase funktionieren.
      * Wenn `ServerAlias *` ist nicht akzeptabel, mindestens `ServerAlias` -Einträge müssen zusätzlich zu Ihren benutzerdefinierten Domänen zulässig sein:
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* Konfigurieren Sie CDN, SSL und DNS.
   * Wenn Sie Ihr eigenes CDN verwenden, geben Sie ein Support-Ticket ein, um das entsprechende Routing zu konfigurieren.
      * Siehe Abschnitt . [Kunden-CDN verweist auf AEM verwaltetes CDN](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) in der CDN-Dokumentation .
      * Sie müssen SSL und DNS gemäß der Dokumentation Ihres CDN-Anbieters konfigurieren.
   * Wenn Sie kein zusätzliches CDN verwenden, verwalten Sie SSL und DNS gemäß der folgenden Dokumentation:
      * Verwalten von SSL-Zertifikaten
         * [Einführung in die Verwaltung von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * Verwalten von benutzerdefinierten Domänennamen (DNS)
         * [Einführung in benutzerdefinierte Domänennamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [Verwalten des benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * Denken Sie daran, den TTL-Satz für Ihren DNS-Eintrag zu validieren.
      * Die TTL ist die Zeit, die ein DNS-Eintrag in einem Cache verbleibt, bevor der Server um eine Aktualisierung gebeten wird.
      * Wenn Sie eine sehr hohe TTL haben, dauert die Aktualisierung Ihres DNS-Eintrags länger.
* Führen Sie Leistungs- und Sicherheitstests durch, die Ihren Geschäftsanforderungen und -zielen entsprechen.
* Fahren Sie mit dem Mauszeiger darüber und stellen Sie sicher, dass die Live-Schaltung ohne neue Bereitstellung oder Inhaltsaktualisierung durchgeführt wird.

Sie können immer auf die Liste verweisen, falls Sie Ihre Aufgaben bei der Migration neu kalibrieren müssen.

## Wie geht es weiter {#what-is-next}

Sobald Sie wissen, wie die Migration auf AEM as a Cloud Service durchgeführt wird, können Sie die Seite [Nach der Live-Schaltung](/help/journey-migration/post-go-live.md) aufrufen, damit Ihre Instanz reibungslos ausgeführt wird.
