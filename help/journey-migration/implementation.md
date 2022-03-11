---
title: Implementierungsphase
description: Sicherstellen, dass Code und Inhalt für die Migration in die Cloud bereit sind
exl-id: d124f9a5-a754-4ed0-a839-f2968c7c8faa
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '2422'
ht-degree: 10%

---

# Implementierungsphase {#implementation-phase}

In der Implementierungsphase des Journey werden Sie die Tools untersuchen, mit denen Sie Ihren Code und Ihre Inhalte so gestalten können, dass sie auf AEM as a Cloud Service verschoben werden können.

## Die bisherige Entwicklung {#story-so-far}

In den vorherigen Teilen der Journey haben Sie [Lernen Sie die Änderungen in AEM as a Cloud Service kennen](/help/journey-migration/getting-started.md)und bestimmen, ob Ihre Bereitstellung bereit ist, mit der [Bereitschaftsphase](/help/journey-migration/readiness.md).

In diesem Artikel wird die Verwendung der von Adobe bereitgestellten Tools erläutert, um sicherzustellen, dass Ihr Code und Ihre Inhalte bereit für die Verschiebung in die Cloud sind.

## Ziel {#objective}

Dieses Dokument zielt auf Folgendes ab:

* Einführung in Cloud Manager, AEM kontinuierliche Integration und Bereitstellungsframework für die Bereitstellung von Code für AEM as a Cloud Service
* Machen Sie sich mit dem Content Transfer Tool auf den neuesten Stand
* Beschreiben Sie die Code-Refaktorierungs-Tools, die Sie verwenden müssen, um Ihren Code für AEM as a Cloud Service zu modernisieren

## Verwenden von Cloud Manager {#using-cloud-manager}

Bevor Sie beginnen, müssen Sie sich mit Cloud Manager vertraut machen, da dies der einzige Mechanismus für die Bereitstellung von Code auf AEM as a Cloud Service ist.

Cloud Manager ermöglicht Unternehmen die Selbstverwaltung von AEM in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen.

Sie können sich mit der Verwendung von Cloud Manager vertraut machen, indem Sie die unten stehenden Ressourcen konsultieren:

* [Einstieg in Experience Manager as a Cloud Service](/help/onboarding/home.md), um sich mit den Selbsthilferessourcen beim Einstieg in Experience Manager as a Cloud Service vertraut zu machen.

* [Integration von Git mit Adobe Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md), um mehr über die Verwendung eines Single Git-Repositorys zur Bereitstellung von Code zu erfahren.

* [Konfiguration von Adobe Experience as a Cloud Service](/help/security/ims-support.md#aem-configuration), um mehr über die Verwaltung von Produkten und den Benutzerzugriff in Admin Console zu erfahren.

## Verwenden Sie die in der Adobe bereitgestellten Tools, um Ihre Inhalte und die Code-Cloud bereit zu machen. {#use-tools-to-make-code-and-content-cloud-ready}

Die genauen Schritte für die Umstellung auf den Cloud Service hängen von den von Ihnen erworbenen Systemen und den von Ihnen befolgten Lebenszykluspraktiken für die Softwareentwicklung ab.

Die folgende Abbildung zeigt die wichtigsten Schritte in der Phase, in der Sie Code und Inhalt für die Verwendung mit AEM as a Cloud Service konvertieren müssen:

![image](/help/journey-migration/assets/exec-image1.png)

In den folgenden Kapiteln werden wir die Tools detailliert beschreiben, die Sie dazu benötigen.

## Inhaltsmigration {#content-migration}

Um Inhalte von Ihrer aktuellen AEM-Instanz in Ihre Cloud Service-Instanz zu migrieren, können Sie das Content Transfer Tool von Adobe verwenden.

Mit diesem Tool können Sie die gewünschte Teilmenge Ihres Inhalts angeben, die Sie von Ihrer AEM-Quellinstanz auf Ihre AEM Cloud Service-Instanz übertragen möchten.

Die Inhaltsmigration ist ein mehrstufiger Prozess, der die Planung, Verfolgung und Zusammenarbeit zwischen verschiedenen Teams erfordert.

Eine ausführliche Beschreibung der Funktionsweise des Tools und seiner empfohlenen Verwendung finden Sie im Abschnitt [Dokumentation zum Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md).

## Code-Umgestaltung {#code-refactor}

### Für Entwicklung einrichten {#set-up-for-development}

Es ist an der Zeit, mit der Refaktorierung der vorhandenen Funktionen zu beginnen, um mit Cloud Services kompatibel zu sein.

Dazu müssen Sie sich die Dokumentation ansehen, in der die grundlegenden Tools beschrieben werden, die Sie zum Refaktorieren Ihres Codes benötigen:


* Bei der Planung ist es empfehlenswert, eine Liste von Gebieten zu erstellen, die umgestaltet werden müssen, um mit AEM as a Cloud Service vereinbar zu sein. Sie können [Entwicklungsrichtlinien](/help/implementing/developing/introduction/development-guidelines.md) für weitere Informationen zur Umgestaltung und Optimierung des Codes für den Cloud Service.
* Lesen Sie mehr darüber, wie [Konfigurationen verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/configurations.html?lang=en#what-is-a-configuration) in AEM as a Cloud Service.
* Erfahren Sie, wie Sie eine lokale Entwicklungsumgebung einrichten, indem Sie die [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en)
* Machen Sie sich schließlich mit dem [as a Cloud Service Java-API AEM](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

Darüber hinaus haben Sie folgende Möglichkeiten:

* In diesem Video erfahren Sie, wie Sie das Dispatcher-SDK lokal installieren:

   >[!VIDEO](https://video.tv.adobe.com/v/30601)

* In diesem Video erfahren Sie, wie Sie das Dispatcher-SDK konfigurieren:

   >[!VIDEO](https://video.tv.adobe.com/v/30602)

### Änderung der Mindesthöhe {#a-change-in-mindset}

Die Entwicklung und Ausführung von Code in AEM as a Cloud Service erfordert eine Änderung der Denkweise. Beachten Sie, dass der Code robust sein muss, insbesondere da eine Instanz jederzeit gestoppt werden kann. Code, der in Cloud Service ausgeführt wird, muss wissen, dass er immer in einem Cluster ausgeführt wird. Das bedeutet, dass immer mehr als eine Instanz ausgeführt wird.

Bestimmte Änderungen sind erforderlich, damit AEM Maven-Projekte Cloud-kompatibel sind. AEM as a Cloud Service erfordert eine Trennung von *content* und *code* in verschiedene Pakete zur Implementierung in AEM:

* `/apps` und `/libs` werden als unveränderliche Bereiche von AEM betrachtet, da sie nach AEM Start (d. h. zur Laufzeit) nicht mehr geändert werden können. Dies umfasst das Erstellen, Aktualisieren oder Löschen von Vorgängen. Jeder Versuch, einen unveränderlichen Bereich zur Laufzeit zu ändern, schlägt fehl.

* Alles andere im Repository (z. B. `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp`) sind alle veränderlichen Bereiche, d. h. sie können zur Laufzeit geändert werden.

Weitere Informationen erhalten Sie im Abschnitt [Empfohlene Paketstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md#recommended-package-structure) Dokumentation.


### Cloud-Migrations-Tools {#cloud-migration-tools}

Adobe bietet mehrere Tools, die Ihnen helfen, einige Ihrer Code-Refaktorierungsaufgaben zu beschleunigen. Das Verständnis dieser Werkzeuge und der Probleme, die sie lösen, wird die Komplexität und die Zeit der Migration verringern.

* [Asset-Workflow-Migration](/help/journey-migration/moving-to-aem-assets/asset-workflow-migration-tool.md), ein Tool zur automatischen Migration von Asset-Verarbeitungs-Workflows
* [Dispatcher Converter](/help/journey-migration/refactoring-tools/dispatcher-transformation-utility-tools.md), ein Tool, das Ihre bestehenden Dispatcher-Konfigurationen in ein Format konvertiert, das für AEM as a Cloud Service Formate geeignet ist.
* [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/repo-modernizer.html?lang=en), ein Tool, das ein AEM Multimode-Projekt als Eingabe verwendet und es in ein as a Cloud Service AEM konvertiert
* [Index Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/index-converter.html?lang=en), ein Tool, das Indizes in ein Formular konvertiert, das mit AEM as a Cloud Service kompatibel ist
* [Modernisierungs-Tools](/help/journey-migration/refactoring-tools/aem-modernization-tools.md), eine Suite von Dienstprogrammen, mit denen ältere AEM-Funktionen in die modernen und unterstützten Funktionen von AEM as a Cloud Service konvertiert werden können.

Sobald Sie die lokale Entwicklungsumgebung eingerichtet haben, sollten Sie sich mit dem AEM as a Cloud Service SDK vertraut machen, indem Sie die [Dokumentation](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

### Planen eines Code-Freeze {#schedule-a-code-freeze}

Um Ihre laufende Code-Entwicklung auf Ihrem aktiven AEM zusammen mit den Code-Refaktorierungsaufgaben im Rahmen Ihrer Journey-Umstellung zu verwalten, empfehlen wir Ihnen, einen Code-Freeze-Zeitraum zu planen, bis Sie die Umstrukturierung Ihres Maven-Projekts abgeschlossen haben, damit es mit AEM as a Cloud Service kompatibel ist.

Sobald die Projektumstrukturierung abgeschlossen ist, können Sie die neue Codeentwicklung anhand dieser neuen Struktur fortsetzen. Dadurch werden Cloud Manager-Pipeline-Fehler während der Codebereitstellung und -tests reduziert.

>[!NOTE]
>Die Aufgaben Inhaltstransfer und Code-Refaktorierung müssen nicht sequenziell ausgeführt werden. Diese Aufgaben können unabhängig voneinander ausgeführt werden. Die richtige Projektstruktur ist jedoch erforderlich, um sicherzustellen, dass der Inhalt in Ihrer Cloud Service-Umgebung erfolgreich gerendert wird.

## Best Practices für die Implementierung und das Testen von Code {#best-practices}

Die Cloud Manager-Pipeline unterstützt die Ausführung von Tests, die für die Staging-Umgebung ausgeführt werden.

Befolgen Sie die Best Practices in den folgenden Dokumenten zum Testen der Code-Qualität:

* [Tests der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md), ein Dokument, das den Prozess des Schreibens von Testskripten beschreibt und das Konzept der empfohlenen Abdeckung von mindestens 50 % erläutert.
* [Grundlegendes zu benutzerspezifischen Regeln für Code-Qualität](/help/implementing/cloud-manager/custom-code-quality-rules.md) , um die benutzerspezifischen Regeln für die Code-Qualität zu beschreiben, die von Cloud Manager ausgeführt werden und auf Best Practices von AEM Engineering basieren.

## Vorbereitung auf die Live-Schaltung {#preparing-for-go-live}

Die Vorbereitung des Quellsystems auf die Migration umfasst Aufgaben auf der System- und AEM Administratorebene. Sie können zunächst überprüfen, ob das Inhalts-Repository in einem gut gepflegten Zustand ist, indem Sie die [Revisionsbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=de) und [Speicherbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/data-store-garbage-collection.html) Aufgabenstatus. Wenn Sie AEM Version 6.3 ausführen (da das Content Transfer Tool ab Version 6.3 kompatibel ist), wird empfohlen, eine Offline-Komprimierung durchzuführen, gefolgt von der Datenspeicherbereinigung.

[Konsistenzprüfung der Daten](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/consistency-check.html) wird für alle AEM-Versionen empfohlen, um sicherzustellen, dass das Inhalts-Repository einen guten Status aufweist, um Migrationsaktivitäten zu starten.

Zugriff auf Systemadministratorebene ist für die Installation und Konfiguration erforderlich [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md)

Es wird außerdem empfohlen, nicht verwendete Assets, Seiten, AEM Projekte, Benutzer und Gruppen zu überprüfen, um Zeit bei der Migration zu sparen. Siehe [Content Repository-Konsistenz](#repository-health) Abschnitt.

### Content Repository-Konsistenz {#repository-health}

Einmaliger Zugriff auf eine [Produktionsklon](#proof-of-migration) festgelegt wurde, um den Zustand des Repositorys zu überprüfen. Wie im vorherigen Abschnitt erwähnt, besteht das Ziel darin, das Repository auf der Quelle zu bereinigen und zu komprimieren, bevor die Migration gestartet wird. Durch diesen Schritt sparen Sie möglicherweise viel Zeit, da Sie sonst nach dem Beginn der Migration mit der Fehlerbehebung arbeiten.

| Aktionselement | Wichtige Takeaways |
|---------|----------|
| Benutzer, Gruppen und Berechtigungen | Sie müssen die Anzahl der Benutzer, Gruppen und die Komplexität von Mitgliedschaften verstehen. Suchen Sie nach Möglichkeiten, nicht verwendete Benutzer, Gruppen in der Quelle vor der Migration zu bereinigen. |
| Unvollständige Asset-Verarbeitung | Versuchen Sie, die Verarbeitung von Assets im Quellsystem abzuschließen, bevor Sie mit der Migration beginnen, um potenzielle Bedenken bei AEM as a Cloud Service Nachmigration zu vermeiden. |
| Inhaltskonsistenz | Es wird empfohlen, vor dem Starten der Migration nach ungültigen Inhalten zu suchen und diese zu bereinigen. Suchen Sie beispielsweise nach Assets oder Seiten, die keine Original-Ausgabeformate aufweisen oder die bei der Workflow-Verarbeitung hängen bleiben. Siehe auch [Asset-Konsistenz](#asset-health). |

## Datenerfassung {#gathering-data}

>[!NOTE]
> Die [Inhaltsmigrationsstrategie und -zeitleiste](#content-strategy-and-timeline) im Abschnitt wird beschrieben, wie Sie die gesammelten Daten extrapolieren und einen Migrationsplan erstellen.

Die Datenerfassung kann Ihnen bei der Planung der Migrationsaktivitäten und der damit verbundenen Aufgaben helfen. Die Extraktions- und Erfassungszeiten sind besonders nützlich, da die Datenpunkte einer bestimmten Größe des Migrationssatzes zugeordnet werden können. Daher können diese Datenpunkte extrapoliert werden, um einen Plan zu erstellen:

* Gesamtdauer [Extraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)
* Gesamtdauer [Aufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
* Gesamtdauer der Aufstockung [Extraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)
* Gesamtdauer der Aufstockung [Aufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)

Ein weiterer wichtiger Datenpunkt ist die Zeit, die zum Abschließen der [Benutzerzuordnung](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md), wenn dies mit der Inhaltsmigration verknüpft ist. Sie können diesen Datenpunkt für realistischere Schätzungen berücksichtigen, da er zur gesamten Extraktionszeitleiste hinzugefügt wird und möglicherweise nicht während der Auffüllungen ausgeführt werden muss.

Diese Datenpunkte können Ihnen auch helfen [Festlegen von KPIs](/help/journey-migration/readiness.md#establish-kpis) und anderen Migrationsaufgaben.

### Migrationsplan {#migration-plan}

Basierend auf den erfassten Datenpunkten (siehe oben) können Sie einen Migrationsplan erstellen, der in einen Makroprojektplan integriert werden kann. Dieser Schritt wird es allen wichtigen Interessengruppen ermöglichen, die Migrationsaktivitäten zu visualisieren und zu planen.

Die folgende Tabelle zeigt einen typischen Migrationsplan:

| Migrationserweiterung | Startdatum | Geschätztes Enddatum | Abhängigkeiten | Geschätzte Dauer (in Tagen) | Zusätzliche Details/Aktionselemente |
|---|---|---|---|---|---|
| PRDCLONE-AUTHOR-INITIAL-USRMAP-CSSTAGE-AUTHOR |  |  |  |  |  |
| PRDCLONE-PUBLISH-TOPUP-CSSTAGE-AUTHOR |  |  |  |  |  |

Wie Sie in der obigen Tabelle sehen können, ist es hilfreich, ein bestimmtes Benennungsformat zu verwenden, um die Migrationsdurchläufe zu identifizieren, z. B.: **PRDCLON** für die AEM-Quellumgebung , **AUTOR/VERÖFFENTLICHUNG** für die AEM as a Cloud Service Umgebung, **CSSTAGE-AUTHOR** für die AEM as a Cloud Service Instanz usw.

Einige wichtige Details, die sich auf Ihren Migrationsplan auswirken:

**Gesamtzahl der erforderlichen Auszüge**

* Die Extraktion von Autoren- und Veröffentlichungsinstanzen in bestimmten Umgebungen wird als zwei parallele Extraktionen betrachtet, da sie voneinander unabhängig sind.
* Anzahl der Auffüllextraktionen basierend auf dem Repository-Wachstum in bestimmten Zeiträumen.

**Gesamtzahl der erforderlichen Gestaltungen**

* Es ist wichtig, dieses Element im Plan zu erfassen, da ein extrahiertes Set in mehrere Cloud Service-Umgebungen aufgenommen werden kann.
* Anzahl der Auffüllaufnahme.
* Die Migration von Inhalten von der Quell-Autoreninstanz zur Cloud Service-Autoreninstanz und von der Quell-Veröffentlichung zur Cloud Service-Veröffentlichung ist die Best Practice, um zu verhindern, dass der gesamte Autoreninhalt in die Cloud Service-Veröffentlichung aufgenommen wird.

### Migrationsverfolgung {#migration-tracker}

Sie können den Migrationstocker verwenden, um die Zeiten sowohl für die ersten als auch für die Auffüllvorgänge zu notieren. Diese Datenpunkte helfen Ihnen bei der Formulierung realistischer Anforderungen an das Einfrieren von Inhalten vor der endgültigen Auffüllung.

Der Tracker hilft Ihnen auch bei Folgendem:

* Identifizieren Sie alle Abweichungen vom Planer, die Anpassungen im Plan oder in den Live-Zeitplänen erfordern.
* Geben Sie einen realistischen Status an, der in allen notwendigen Kommunikationen verwendet werden kann.
* Planen der ersten oder künftigen Aufstockung der Migration

Die folgende Tabelle zeigt einen funktionalen Migrationstracker:

| Quelle (Umgebung/Instanz/URL) | Ziel (Umgebung/Instanz/URL) | Name des Migrationssatzes, Typ (Anfänglich oder Aufwärts) | Größe des Migrationssatzes (MB) | Benutzerzuordnung (Ja/Nein) | Extraktionsdauer (Start, Ende, Dauer) | Aufnahmedauer (Start, Ende, Dauer) | Probleme/Lösungen/Details |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |

## Inhaltsmigrationsstrategie und -zeitleiste {#content-strategyand-timeline}

Im folgenden Abschnitt werden die wichtigen Schritte und zugehörigen Aufgaben beschrieben, die zur Formulierung einer Inhaltsmigrationsstrategie und eines Zeitplans verwendet werden können.

![image](/help/journey-migration/assets/content-migration2.png)

### Ausrüstung {#fitment}

* Führen Sie Revisionsbereinigung, Datenspeicherbereinigung und Datenkonsistenzprüfungen durch. Siehe auch [Vorbereitung auf die Live-Schaltung](#preparing-for-go-live)
* [Zusammenstellen von Statistiken](#gathering-data) über das AEM Quell-Repository:
   * Segmentspeichergröße
   * Indexspeichergröße
   * Anzahl Seiten
   * Anzahl der Assets
   * Anzahl der Benutzer und Gruppen
* Überprüfen Sie, ob die folgenden Funktionen für die AEM aktiviert sind (auch in AEM as a Cloud Service erforderlich):
   * Smart-Tagging
   * Ähnlichkeitssuche
   * Suchen nach Text, der in Word- und PDF-Dokumenten enthalten ist
* Sammeln von Best Practice Analyzer [Bericht](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)
* Import in [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md)
   * Überprüfen Sie die Selbstanalyse-Empfehlung, um sicherzustellen, dass AEM as a Cloud Service die Speicheranforderungen handhaben kann.
* Erstellen Sie ein Ticket zur Adobe-Unterstützung , um weitere Informationen zu erhalten, bevor Sie den Migrationsplan fortsetzen.

### Migrationsnachweis {#proof-of-migration}

* Anfordern eines Produktionsklons, der:
   * Befindet sich in derselben Netzwerkzone
   * Stellt Produktionsinhalte wie Benutzer und Gruppen bereit
   * Klonen von Autoren- und Veröffentlichungsinstanz - je einen Knoten im Fall eines Clusters oder einer Veröffentlichungsfarm
* Wählen Sie eine Teilmenge des zu migrierenden Inhalts aus, sodass:
   * Es handelt sich um eine Mischung aller verfügbaren Inhaltstypen
   * Enthält alle Benutzer und Gruppen, falls vorhanden [Benutzerzuordnung](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md) ist erforderlich
* Umfasst entweder 25 % des Inhalts oder bis zu 1 TB Inhalt, je nachdem, welcher Wert kleiner ist.
* Führen Sie mindestens einen vollständigen aus und [top-up](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) Migration vom Produktionsklon in die AEM as a Cloud Service Nicht-Produktionsumgebung
* Lösen Sie alle potenziellen Probleme wie:
   * Speicherplatz auf der AEM
   * Verbindung zwischen AEM und AEM as a Cloud Service
   * Alle [Einschränkungen bei der Erfassung](go-live.md#known-limitations).
* Notieren Sie die benötigte Zeit für [Extraktion und Aufnahme](#gathering-data):
   * Ermitteln, wie viel Inhalt pro Woche hinzugefügt wird
   * Extrahieren Sie die vom Migrationsnachweis aus gemessenen Zeiten, um eine [Migrationsplan](#migration-plan).

## Wie geht es weiter {#what-is-next}

Sobald Sie vollständig verstanden haben, wie Sie beurteilen können, ob Ihre AEM-Installation bereit ist, in die Cloud verschoben zu werden, da wir lernen, die erforderlichen Tools zu verwenden, um sie bereit zu machen, ist es an der Zeit, zum [Go-Live-Phase](/help/journey-migration/go-live.md).
