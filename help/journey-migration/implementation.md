---
title: Implementierungsphase
description: Sicherstellen, dass Ihr Code und die Inhalte für die Migration in die Cloud bereit sind
exl-id: d124f9a5-a754-4ed0-a839-f2968c7c8faa
feature: Migration
role: Admin
source-git-commit: 913b1beceb974243f0aa7486ddd195998d5e9439
workflow-type: tm+mt
source-wordcount: '2288'
ht-degree: 100%

---

# Implementierungsphase {#implementation-phase}

In der Implementierungsphase der Tour lernen Sie die Tools kennen, mit denen Sie Ihren Code und Ihre Inhalte so gestalten können, dass sie in AEM as a Cloud Service verschoben werden können.

## Die bisherige Entwicklung {#story-so-far}

In den vorherigen Teilen der Tour haben Sie sich [mit den Änderungen in AEM as a Cloud Service](/help/journey-migration/getting-started.md) vertraut gemacht und in der [Bereitschaftsphase](/help/journey-migration/readiness.md) ermittelt, ob Ihre Bereitstellung bereit ist, in die Cloud verschoben zu werden.

In diesem Artikel wird die Verwendung der von Adobe bereitgestellten Tools erläutert, um sicherzustellen, dass Ihr Code und Ihre Inhalte bereit sind, in die Cloud verschoben zu werden.

## Ziel {#objective}

Dieses Dokument zielt auf Folgendes ab:

* Ihnen eine Einführung in Cloud Manager, die fortwährende Integration von AEM und das für die Bereitstellung von Code für AEM as a Cloud Service benutzte Bereitstellungs-Framework zu geben.
* Sie auf den neuesten Stand des Content Transfer Tools zu bringen
* Ihnen eine Beschreibung der Code-Refaktorierungs-Tools an die Hand zu geben, die Sie verwenden müssen, um Ihren Code für AEM as a Cloud Service zu modernisieren  

## Verwenden von Cloud Manager {#using-cloud-manager}

Bevor Sie anfangen, müssen Sie sich auch mit Cloud Manager vertraut machen, da dies der einzige Mechanismus für die Bereitstellung von Code für AEM as a Cloud Service ist.

Cloud Manager ermöglicht Unternehmen die Selbstverwaltung von AEM in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen.

Sie können sich mit der Verwendung von Cloud Manager vertraut machen, indem Sie die unten stehenden Ressourcen konsultieren:

* [Onboarding-Tour](/help/journey-onboarding/overview.md) erklärt die Selbsthilfe-Ressourcen für das Onboarding von Experience Manager as a Cloud Service.

* [Integration von Git mit Adobe Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md), um mehr über die Verwendung eines Single Git-Repositorys zur Bereitstellung von Code zu erfahren.

* [Konfiguration von Adobe Experience as a Cloud Service](/help/security/ims-support.md#aem-configuration), um mehr über die Verwaltung von Produkten und den Benutzerzugriff in Admin Console zu erfahren.

## Verwenden Sie die von Adobe bereitgestellten Tools, um Ihre Inhalte und Ihren Code bereit für die Cloud zu machen {#use-tools-to-make-code-and-content-cloud-ready}

Die genauen Schritte Ihrer Umstellung auf Cloud Service hängen von den von Ihnen erworbenen Systemen und den von Ihnen befolgten Lebenszykluspraktiken für die Software-Entwicklung ab.

Die folgende Abbildung zeigt die wichtigsten Schritte in der Phase, in der Sie Ihren Code und Ihre Inhalte für die Verwendung mit AEM as a Cloud Service konvertieren:

![Konversionsschritte](/help/journey-migration/assets/exec-image1.png)

In den folgenden Kapiteln werden wir Ihnen die Tools vorstellen, mit denen Sie dies erreichen können.

## Inhaltsmigration {#content-migration}

Sie können das Adobe Content Transfer Tool verwenden, um Inhalte von Ihrer aktuellen AEM-Instanz in Ihre Cloud Service-Instanz zu übertragen.

Mit diesem Tool können Sie die gewünschte Teilmenge Ihrer Inhalte angeben, die Sie von Ihrer AEM-Quellinstanz auf Ihre AEM Cloud Service-Instanz übertragen möchten.

Die Migration von Inhalten ist ein mehrstufiger Prozess, der die Planung, Verfolgung und Zusammenarbeit zwischen verschiedenen Teams erfordert.

Eine ausführliche Beschreibung der Funktionsweise des Tools und seiner von Adobe empfohlenen Verwendung finden Sie in der [Dokumentation zum Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md).

## Code-Refaktorierung {#code-refactor}

### Einrichten für die Entwicklungsabteilung {#set-up-for-development}

Wir sollten jetzt mit der Refaktorierung der vorhandenen Funktionen beginnen, damit sie mit Cloud Services kompatibel sind.

Sehen Sie sich zunächst die Dokumentation zu den grundlegenden Tools an und beginnen Sie mit der Refaktorierung Ihres Codes:


* Bei der Planung empfiehlt es sich, eine Liste von Bereichen zu erstellen, die überarbeitet werden müssen, damit sie mit AEM as a Cloud Service kompatibel sind. Weitere Informationen zur Refaktorierung und Optimierung von Code für Cloud Service finden Sie in den [Entwicklungsrichtlinien](/help/implementing/developing/introduction/development-guidelines.md).
* Lesen Sie mehr darüber, wie Sie [Konfigurationen in AEM as a Cloud Service verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/configurations.html?lang=de#what-is-a-configuration).
* Erfahren Sie, wie Sie eine lokale Entwicklungsumgebung einrichten, indem Sie das [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=de) herunterladen
* Machen Sie sich abschließend mit der [AEM as a Cloud Service Java-API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) vertraut.

Darüber hinaus haben Sie folgende Möglichkeiten:

* In diesem Video erfahren Sie, wie Sie das Dispatcher-SDK lokal installieren:

  >[!VIDEO](https://video.tv.adobe.com/v/30601)

* In diesem Video erfahren Sie, wie Sie das Dispatcher-SDK konfigurieren:

  >[!VIDEO](https://video.tv.adobe.com/v/30602)

### Ein neuer Denkansatz {#a-change-in-mindset}

Das Entwickeln und Ausführen von Code in AEM as a Cloud Service erfordert einen neuen Denkansatz. Beachten Sie, dass der Code robust sein muss, insbesondere da eine Instanz jederzeit gestoppt werden kann. Code, der in Cloud Service ausgeführt wird, muss wissen, dass er immer in einem Cluster ausgeführt wird. Das bedeutet, dass immer mehr als eine Instanz ausgeführt wird.

Bestimmte Änderungen sind erforderlich, damit AEM Maven-Projekte Cloud-kompatibel sind. AEM as a Cloud Service erfordert für die Bereitstellung in AEM die Trennung von *Inhalten* und *Code* in separate Pakete:

* `/apps` und `/libs` werden als unveränderliche Bereiche von AEM betrachtet, da sie nach dem Start von AEM (d. h. zur Laufzeit) nicht mehr geändert werden können. Dies umfasst die Erstellung, Aktualisierung oder Löschung von Vorgängen. Jeder Versuch, einen unveränderlichen Bereich zur Laufzeit zu ändern, schlägt fehl.

* Alle weiteren Komponenten im Repository (z. B. `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp`) sind veränderliche Bereiche, d. h. sie können zur Laufzeit geändert werden.

Weitere Informationen erhalten Sie in der Dokumentation [Empfohlene Paketstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md#recommended-package-structure).


### Cloud-Migrations-Tools {#cloud-migration-tools}

Adobe bietet mehrere Tools, die Ihnen helfen, einige Ihrer Code-Refaktorierungsaufgaben zu beschleunigen. Wenn Sie diese Tools und die Probleme, die sie lösen, verstehen, können Sie die Komplexität und die für die Migration benötigte Zeit reduzieren.

* [Asset Workflow Migration](/help/journey-migration/moving-to-aem-assets/asset-workflow-migration-tool.md), ein Tool zur automatischen Migration von Asset-Verarbeitungs-Workflows
* [Dispatcher Converter](/help/journey-migration/refactoring-tools/dispatcher-transformation-utility-tools.md), ein Tool, das Ihre bestehenden Dispatcher-Konfigurationen in ein Format konvertiert, das für AEM as a Cloud Service-Formate geeignet ist.
* [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/repo-modernizer.html?lang=de), ein Tool, das ein AEM Multimode-Projekt als Eingabe verwendet und es in ein AEM as a Cloud Service-Projekt konvertiert
* [Index Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/index-converter.html?lang=de), ein Tool, das Indizes in ein Formular konvertiert, das mit AEM as a Cloud Service kompatibel ist
* [Modernization Tools](/help/journey-migration/refactoring-tools/aem-modernization-tools.md), eine Sammlung von Dienstprogrammen, mit denen ältere AEM-Funktionen in die modernen und unterstützten Funktionen von AEM as a Cloud Service umgewandelt werden können.

Sobald Sie die lokale Entwicklungsumgebung eingerichtet haben, sollten Sie sich mit dem AEM as a Cloud Service SDK vertraut machen, indem Sie die [Dokumentation](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) konsultieren.

### Planen eines Code-Freeze {#schedule-a-code-freeze}

Um Ihre laufende Code-Entwicklung in Ihrem aktiven AEM zusammen mit der Code-Refaktorierung als Teil Ihrer Umstellung zu verwalten, empfiehlt Adobe, eine Code-Freeze-Periode einzuplanen, bis Sie die Neustrukturierung Ihres Maven-Projekts für die Kompatibilität mit AEM as a Cloud Service abgeschlossen haben.

Sobald die Neustrukturierung des Projekts abgeschlossen ist, können Sie die Entwicklung neuen Codes basierend auf dieser neuen Struktur fortsetzen. Dadurch werden Cloud Manager-Pipeline-Fehler bei der Code-Bereitstellung und beim Testen reduziert.

>[!NOTE]
>Die Aufgaben zur Übertragung von Inhalten und zur Code-Refaktorierung müssen nicht sequenziell ausgeführt werden. Diese Aufgaben können unabhängig voneinander ausgeführt werden. Die richtige Projektstruktur ist jedoch erforderlich, um sicherzustellen, dass der Inhalt in Ihrer Cloud Service-Umgebung erfolgreich gerendert wird.

## Best Practices für die Bereitstellung und das Testen von Code {#best-practices}

Die Cloud Manager-Pipeline unterstützt die Ausführung von Tests, die für die Staging-Umgebung ausgeführt werden.

Befolgen Sie die Best Practices in den folgenden Dokumenten bezüglich der Code-Qualitätstests:

* [Code-Qualitätstests](/help/implementing/cloud-manager/code-quality-testing.md), ein Dokument, das den Prozess der Erstellung von Test-Skripts beschreibt und das Konzept der empfohlenen Abdeckung von mindestens 50 % erläutert.
* [Verstehen der Qualitätsregeln für benutzerspezifischen Code](/help/implementing/cloud-manager/custom-code-quality-rules.md), welches darauf abzielt, die benutzerspezifischen Regeln für die Code-Qualität zu beschreiben, die von Cloud Manager ausgeführt werden und auf den Best Practices von AEM Engineering basieren.

## Vorbereiten der Live-Schaltung {#preparing-for-go-live}

Die Vorbereitung des Quellsystems auf die Migration umfasst Aufgaben auf der System- und AEM-Administratorebene. Sie können zunächst überprüfen, ob das Inhalts-Repository in einem gut gepflegten Zustand ist, indem Sie die [Revisionsbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=de) und den Aufgabenstatus der [Datenspeicherbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/data-store-garbage-collection.html?lang=de) überprüfen. Wenn Sie AEM Version 6.3 ausführen (da das Content Transfer Tool ab Version 6.3 kompatibel ist), wird empfohlen, eine Offline-Komprimierung mit einer anschließenden Datenspeicherbereinigung durchzuführen.

[Konsistenzprüfung der Daten](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/consistency-check.html?lang=de) wird für alle AEM-Versionen empfohlen, um sicherzustellen, dass das Inhalts-Repository einen guten Zustand aufweist, um Migrationsaktivitäten zu initiieren.

Zugriff auf Systemadministratorebene wird für die Installation und Konfiguration von [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) benötigt

Es wird außerdem empfohlen, nicht verwendete Assets, Seiten, AEM-Projekte, Benutzer und Gruppen zu überprüfen, um Zeit bei der Migration zu sparen. Siehe Abschnitt [Content-Repository-Status](#repository-health).

### Content-Repository-Status {#repository-health}

Sobald der Zugriff auf einen [Produktionsklon](#proof-of-migration) etabliert wurde, fahren Sie mit der Prüfung des Respository-Status fort. Wie im vorherigen Abschnitt erwähnt, besteht das Ziel darin, das Repository auf der Quelle zu bereinigen und zu komprimieren, bevor die Migration gestartet wird. Durch diesen Schritt sparen Sie möglicherweise viel Zeit, die Sie ansonsten nach dem Beginn der Migration für die Fehlerbehebung aufbringen müssten.

| Aktionselement | Wichtige Vorteile |
|---------|----------|
| Benutzer, Gruppen und Berechtigungen | Sie müssen die Anzahl der Benutzer, Gruppen und die Komplexität von Mitgliedschaften verstehen. Suchen Sie nach Möglichkeiten, nicht verwendete Benutzer und Gruppen in der Quelle vor der Migration zu bereinigen. |
| Unvollständige Asset-Verarbeitung | Versuchen Sie, die Verarbeitung von Assets im Quellsystem abzuschließen, bevor Sie mit der Migration beginnen, um potenzielle Bedenken bei AEM as a Cloud Service nach der Migration zu vermeiden. |
| Inhaltsstatus | Es wird empfohlen, vor dem Start der Migration nach ungültigen Inhalten zu suchen und diese zu bereinigen. Suchen Sie beispielsweise nach Assets oder Seiten, die keine Originalausgabeformate aufweisen oder die in der Workflow-Verarbeitung hängen bleiben. Siehe auch [Asset-Status](#asset-health). |

## Erfassen von Daten {#gathering-data}

>[!NOTE]
> Im Abschnitt [Strategie für die Migration von Inhalten und zeitlicher Ablauf](#content-strategy-and-timeline) wird genauer beschrieben, wie Sie die gesammelten Daten extrapolieren und einen Migrationsplan erstellen.

Die Datenerfassung kann Ihnen bei der Planung der Migrationsaktivitäten und der damit verbundenen Aufgaben helfen. Die Extraktions- und Aufnahmezeiten sind besonders nützlich, da die Datenpunkte einer bestimmten Größe des Migrationssatzes zugeordnet werden können. So können diese Datenpunkte extrapoliert werden, um einen Plan zu erstellen:

* Gesamtdauer der [Extraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)
* Gesamtdauer für die [Aufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
* Gesamtdauer der [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)
* Gesamtdauer der [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)


<!-- Alexandru: hiding this for now

One more important datapoint is the amount of time it takes to complete the [user mapping](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md), if this is coupled with the content migration. You can take this data point into consideration for more realistic estimates, because it is added to the overall extraction timeline and it may not be required to run it during top-ups.

-->

Diese Datenpunkte können Ihnen auch helfen, [KPIs festzulegen](/help/journey-migration/readiness.md#establish-kpis), und Sie bei anderen Migrationsaufgaben unterstützen.

### Migrationsplan {#migration-plan}

Basierend auf den erfassten Datenpunkten (siehe oben) können Sie einen Migrationsplan erstellen, der in einen übergeordneten Projektplan integriert werden kann. Dieser Schritt ermöglicht es allen wichtigen Interessengruppen, die Migrationsaktivitäten zu visualisieren und zu planen.

Die folgende Tabelle zeigt einen typischen Migrationsplan:

| Migrationsiteration | Startdatum | Geschätztes Enddatum | Abhängigkeiten | Geschätzte Dauer (in Tagen) | Zusätzliche Details/Aktionselemente |
|---|---|---|---|---|---|
| PRDCLONE-AUTHOR-INITIAL-USRMAP-CSSTAGE-AUTHOR |   |   |   |   |   |
| PRDCLONE-PUBLISH-TOPUP-CSSTAGE-AUTHOR |   |   |   |   |   |

Wie Sie der obigen Tabelle entnehmen können, ist es hilfreich, ein bestimmtes Benennungsformat zu verwenden, um die Migrationsiterationen zu identifizieren, z. B.: **PRDCLONE** für die AEM-Quellumgebung, **AUTHOR/PUBLISH** für die AEM as a Cloud Service-Umgebung, **CSSTAGE-AUTHOR** für die AEM as a Cloud Service-Instanz usw.

Einige wichtige Details, die Ihren Migrationsplan beeinflussen:

**Gesamtzahl der erforderlichen Extraktionen**

* Die Extraktionen von Autoren- und Veröffentlichungsinstanz in bestimmten Umgebungen werden als zwei parallele Extraktionen betrachtet, da sie voneinander unabhängig sind.
* Anzahl der Auffüllextraktionen basierend auf dem Repository-Wachstum in bestimmten Zeiträumen.

**Gesamtzahl der erforderlichen Aufnahmen**

* Es ist wichtig, dieses Element im Plan zu erfassen, da ein extrahierter Satz in mehrere Cloud Service-Umgebungen aufgenommen werden kann.
* Anzahl der Auffüll-Aufnahmen.
* Die Migration von Inhalten von der Quell-Autorenistanz zur Cloud Service-Autoreninstanz und von der Quell-Veröffentlichungsinstanz zur Cloud Service-Veröffentlichungsinstanz ist die Best Practice, um zu verhindern, dass die gesamten Autoreninhalte in die Cloud Service-Veröffentlichungsinstanz importiert werden.

### Migrationsverfolgung {#migration-tracker}

Sie können die Migrationsverfolgung verwenden, um die Zeiten sowohl für die anfänglichen als auch für die Auffüllvorgänge zu notieren. Diese Datenpunkte helfen Ihnen bei der Formulierung realistischer Anforderungen für den Inhalts-Freeze vor der endgültigen Auffüllung.

Die Verfolgung hilft Ihnen auch bei Folgendem:

* Identifizieren Sie alle Abweichungen vom Planer, die Anpassungen im Plan oder in den Zeitplänen für die Live-Schaltung erfordern.
* Geben Sie einen realistischen Status an, der in allen notwendigen Kommunikationen verwendet werden kann.
* Planen der anfänglichen oder künftigen Auffüllmigrationen

Die folgende Tabelle zeigt eine funktionale Migrationsverfolgung:

| Quelle (Umgebung/Instanz/URL) | Ziel (Umgebung/Instanz/URL) | Name des Migrationssatzes, Typ (anfänglich oder Auffüllung) | Größe des Migrationssatzes (MB) | Benutzerzuordnung (Ja / Nein) | Extraktionsdauer (Anfang, Ende, benötigte Zeit) | Aufnahmedauer (Start, Ende, benötigte Zeit) | Probleme/Lösungen/Details |
|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |

## Strategie für die Migration von Inhalten und zeitlicher Ablauf {#content-strategyand-timeline}

Im folgenden Abschnitt werden die wichtigen Schritte und zugehörigen Aufgaben beschrieben, die zur Formulierung einer Inhaltsmigrationsstrategie und eines Zeitplans verwendet werden können.

![Schritte zum Formulieren einer Migrationsstrategie](/help/journey-migration/assets/content-migration2.png)

### Ausrüstung {#fitment}

* Führen Sie Revisionsbereinigung, Datenspeicherbereinigung und Datenkonsistenzprüfungen durch. Siehe auch [Vorbereitung auf die Live-Schaltung](#preparing-for-go-live)
* [Zusammenstellen von Statistiken](#gathering-data) über das AEM-Quell-Repository:
   * Segmentspeichergröße
   * Indexspeichergröße
   * Anzahl der Seiten
   * Anzahl der Assets 
   * Anzahl der Anwender und Gruppen
* Überprüfen Sie, ob die folgenden Funktionen für die AEM-Quelle aktiviert sind (auch in AEM as a Cloud Service erforderlich):
   * Smart-Tagging
   * Ähnlichkeitssuche
   * Suchen nach Text, der in Word- und PDF-Dokumenten enthalten ist
* Abrufen des Best Practice Analyzer-[Berichts](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)
* Import in [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md)
   * Schauen Sie sich die Empfehlung zur Selbstanalyse an, um sicher zu sein, dass AEM as a Cloud Service die Speicheranforderungen erfüllen kann.
* Erstellen Sie ein Adobe-Support-Ticket, falls Sie weitere Informationen brauchen, bevor Sie den Migrationsplan fortsetzen.

### Migrationsnachweis {#proof-of-migration}

* Fordern Sie einen Produktionsklon an, der:
   * Sich in derselben Netzwerkzone befindet
   * Produktionsinhalte wie Anwender und Gruppen bereitstellt
   * Klonen von Autor und Veröffentlichung - je einen Knoten im Fall eines Clusters oder einer Veröffentlichungsfarm
* Wählen Sie eine Teilmenge des zu migrierenden Inhalts aus, sodass:
   * Es sich um eine Mischung aller verfügbaren Inhaltstypen handelt
   * Alle Benutzenden und Gruppen enthalten sind.
* Entweder 25 % des Inhalts oder bis zu 1 TB Inhalt enthalten sind, je nachdem, welcher Wert kleiner ist.
* Führen Sie mindestens eine vollständige [Auffüllmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) vom Produktionsklon in die produktionsfremde Umgebung von AEM as a Cloud Service aus
* Lösen Sie alle potenziellen Probleme wie:
   * Speicherplatz in der AEM-Quelle
   * Verbindung zwischen der AEM-Quelle und AEM as a Cloud Service
   * Alle [Einschränkungen bei der Aufnahme](go-live.md#known-limitations).
* Notieren Sie die benötigte Zeit für [Extraktion und Aufnahme](#gathering-data):
   * Ermitteln, wie viel Inhalt pro Woche hinzugefügt wird
   * Extrahieren Sie die vom Migrationsnachweis aus gemessenen Zeiten, um einen [Migrationsplan](#migration-plan) zu erstellen.

## Wie geht es weiter {#what-is-next}

Nachdem Sie vollständig verstanden haben, wie Sie beurteilen können, ob Ihre AEM-Installation für die Verlagerung in die Cloud bereit ist, und wie Sie die dafür erforderlichen Tools verwenden können, ist es an der Zeit, zur [Phase der Inbetriebnahme](/help/journey-migration/go-live.md) überzugehen.
