---
title: Handbuch zur Migration zu Experience Manager as a Cloud Service für Partner
description: Handbuch zur Migration zu Experience Manager as a Cloud Service für Partner
exl-id: 9d5a72b8-06af-4b82-ab20-e65aea7903b3
feature: Migration
role: Admin
source-git-commit: 2e257634313d3097db770211fe635b348ffb36cf
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 98%

---

# Migrationshandbuch für Adobe Experience Manager as a Cloud Service für Partner {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="Migration zu AEM as a Cloud Service"
>abstract="Beschreibt den empfohlenen schrittweisen Ansatz für den Übergang von Kunden von verschiedenen Experience Manager-Implementierungen zu Experience Manager as a Cloud Service und unterstützt bestehende Kunden bei der Bereitstellung zusammenhängender, kontinuierlicher Erlebnisse."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=de" text="Was ist neu und anders?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/introduction.html?lang=de" text="Einführung in AEM as a Cloud Service."

Adobe Experience Manager (AEM) as a Cloud Service bietet eine aktualisierte Architektur für Experience Manager. Diese Grundlage beruht auf einer Container-basierten Infrastruktur, einer API-gesteuerten Entwicklung und einem geleiteten DevOps-Prozess. Dadurch sind Marketing-Fachleute und Entwickelnde bei Customer Experience Management-Innovationen weiterhin immer einen Schritt voraus.

Cloud Service vereint umfassende vorkonfigurierte Funktionen und die Erweiterbarkeit von Adobe Experience Manager mit der Flexibilität der modernen Cloud-nativen Architektur, die es Marken ermöglicht, die sich ständig weiterentwickelnden Kundenanforderungen zu erfüllen.

Auf dieser Seite wird der stufenweise Ansatz beschrieben, der für die Umstellung von Kundinnen und Kunden von vorherigen Experience Manager-Bereitstellungen zu Experience Manager as a Cloud Service empfohlen wird. Die neue, speziell entwickelte Plattform hilft Ihnen, vernetzte, kontinuierliche Erlebnisse bereitzustellen.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

Eine allgemeine Darstellung der Migrationstour finden Sie im folgenden Diagramm.

![Allgemeine Darstellung der Migrations-Tour](/help/journey-migration/assets/migration-process.png)

## Erste Schritte mit Adobe Experience Manager as a Cloud Service {#getting-started}

| Was ist anders? | Architekturüberblick |
|--------------------------|--------------------------|
| <ul><li>[Moderne Architektur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html?lang=de)</li><li>[Automatische Aktualisierungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html?lang=de)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=de)</li><li>[Asset-Microservices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html?lang=de)</li><li>[Binärdateien mit direktem Zugriff](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html?lang=de)</li><li>[Trennung von Code und Inhalt](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de)</li><li>[Replikation als Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/replication.html?lang=de)</li><li>[Admin Console, Gruppen-/Benutzermitgliedschaft und ACLs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=de)</li></ul> | <ul><li>[Einführung in die AEM-Architektur](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=de#underlying-technology)</li><li>[Umgebungsstapel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html?lang=de)</li><li>[Autorenebene](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=de#underlying-technology)</li><li>[Veröffentlichungsebene](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=de#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=de)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=de) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=de) (CI/CD)</li><li>[Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=de) über [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=de)</li><li>[Asset Compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/home.html?lang=de)</li></ul> |

![AEM as a Cloud Service – Laufzeitarchitektur](/help/overview/assets/concepts-03.png "AEM as a Cloud Service – Laufzeitarchitektur")

<br>

## Entwickler in Adobe Experience Manager as a Cloud Service {#developer-journey}

### Entwickeln

Die Grundlagen der Code-Entwicklung in Adobe Experience Manager as a Cloud Service ähneln denen von Adobe Experience Manager On-Premise- und Managed Services-Lösungen.

Entwickelnde schreiben Code und testen ihn lokal, bevor sie ihn per Push an Adobe Experience Manager as a Cloud Service-Remote-Umgebungen übertragen.

In den Selbsthilferessourcen zur Bereitstellung von Experience Manager as a Cloud Service erfahren Sie, wie Sie Ihre Bereitstellung von Experience Manager as a Cloud Service anpassen können.

| Lokale Entwicklungseinrichtung | Vorbereitung |
|-----------|------------|
| <ol><li>Weitere Informationen finden Sie in der Dokumentation zum [Adobe Experience Manager-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=de).</li><li>Sehen Sie sich [Installieren des Dispatcher-SDK](https://video.tv.adobe.com/v/30601) an, um zu verstehen, wie das Dispatcher-SDK installiert wird.</li><li>Sehen Sie sich [Konfigurieren des Dispatcher-SDK](https://video.tv.adobe.com/v/32985?captions=ger) an, um zu verstehen, wie Dispatcher-SDK konfiguriert wird.</li><li>Weitere Informationen finden Sie in der Dokumentation zu den [lokalen Entwicklungseinstellungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=de#local-development-environment-set-up).</li><li>Konfigurieren des Zugriffs auf Experience Manager – [Beispiel](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=de#accessing)</li></ol> | <ol><li>[Entwicklungsgrundlagen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=de)</li><li>[Entwicklungsrichtlinien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=de)</li><li>[Grundlegendes zur Experience Manager-Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de)</li><li>[Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)</li><li>[Digital Foundation Blueprint](https://solutionpartners.adobe.com/content/dam/solution/en/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Stilsystem](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/style-system.html?lang=de)</li><li>[Überlagerungen](/help/implementing/developing/introduction/overlays.md)</li><li>[API-Referenz für Experience Manager as a Cloud Service](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/)</li></ol> |

>[!TIP]
> Weitere Informationen zum [Entwickeln und Bereitstellen von WKND im lokalen Experience Manager-SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de) finden Sie im Tutorial.

### Bereitstellen

Entwickelnde schreiben Code und testen ihn lokal, bevor sie ihn per Push an AEM as a Cloud Service-Remote-Umgebungen übertragen.

Cloud Manager, zuvor lediglich ein optionales Tool zur Inhaltsbereitstellung für Managed Services, ist nun erforderlich. und die einzige Möglichkeit zur Code-Bereitstellung in AEM as a Cloud Service-Umgebungen.

Informationen zur Konfiguration und Bereitstellung in AEM as a Cloud Service-Umgebungen finden Sie in den Selbsthilferessourcen.

1. [Konfigurieren von CM-Pipelines](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/introduction-ci-cd-pipelines.html?lang=de)

   * Produktions-Pipeline
   * Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität

1. [Bereitstellen von Code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de)
1. [Grundlegendes zu Testergebnissen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=de)
1. **Abrufen von Protokollen**

   * [über die CM-Benutzeroberfläche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html?lang=de)
   * [über Adobe I/O-CLI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=de#debugging)

1. [Vorgänge und Wartung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/home.html?lang=de)

   * [Konfigurieren von OSGI-Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html?lang=de)
   * [Sichern und Wiederherstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html?lang=de)

>[!TIP]
> Weitere Informationen zum Bereitstellen von WKND für [Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de) finden Sie im Tutorial.

### Hilfe und Ressourcen

1. [Tipps und Tricks zum Debuggen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=de#debugging-aem-as-a-cloud-service)
1. [Entwicklerkonsole](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de#debugging)
1. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html?lang=de) (Nur für lokale SDK- und Experience Manager Cloud-Entwicklungsumgebungen verfügbar)
1. [Protokolle und Protokollierung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=de#debugging)

   * [CM-Protokolle](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=de#debugging) (Build-Unit-Test, Code-Scan, Build-Image, Bereitstellung)
   * [Experience Manager Cloud Service-Protokolle](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=de#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Lokale SDK-Protokolle (unter host:port/crx-quickstart/logs)

>[!NOTE]
>
> Weitere Hilfe finden Sie unter:
>
>1. [Kontaktieren Sie das Experience Manager-Supportteam](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).
>1. [Experience Manager-Communities und -Foren](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community?profile.language=de&lang=de)

<br>

## Wechsel zu Adobe Experience Manager as a Cloud Service {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Wechsel zu Adobe Experience Manager as a Cloud Service"
>abstract="Dieser Überblick beschreibt den empfohlenen schrittweisen Ansatz für den Übergang von Kunden von verschiedenen Experience Manager-Implementierungen zu Experience Manager as a Cloud Service und unterstützt bestehende Kunden bei der Bereitstellung zusammenhängender, kontinuierlicher Erlebnisse auf dieser modernen, speziell entwickelten Plattform für die Erlebnisverwaltung."

**Experience Manager as a Cloud Service bietet eine technologische Grundlage für Experience Manager Sites und Assets, sodass sich Marketing-Experten und IT darauf konzentrieren können, skaliert wirkungsvolle Erlebnisse bereitzustellen.**

Mit Experience Manager as a Cloud Service können sich Ihre Teams auf Innovationen konzentrieren, anstatt Produktaktualisierungen planen zu müssen. Neue Produktfunktionen werden umfassend getestet und ohne Unterbrechungen an Ihre Teams bereitgestellt, sodass sie immer Zugriff auf die neueste Anwendung haben.

Die Umstellung auf Cloud Service umfasst drei Phasen: Planung, Ausführung und die Phase nach der Live-Schaltung.
Für einen erfolgreichen und reibungslosen Übergang sollten Sie eine ordnungsgemäße Planung sicherstellen und die in diesem Handbuch beschriebenen Best Practices einhalten.

Die nachstehende Abbildung zeigt eine übersichtliche Darstellung des empfohlenen Übergangs zu Cloud Service.

![Allgemeine Darstellung der empfohlenen Umstellung zu Cloud Service](/help/journey-migration/assets/home-img1.png)

<br>

### Planung

Vor die Umstellung zu Cloud Service sollten Sie Folgendes beachten:

* Machen Sie sich mit Experience Manager as a Cloud Service vertraut.
* Informieren Sie sich über die wesentlichen Änderungen.
* Informieren Sie sich über die Funktionen, die ersetzt oder eingestellt wurden.

<table>
<tr>
<td>Projektsuche und -bewertung</td>
<td><ul><li>Informationen zu wichtigen Unterschieden zwischen Adobe Experience Manager as a Cloud Service und Experience Manager 6.x finden Sie unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=de">Wesentliche Änderungen an Experience Manager as a Cloud Service</a>.</li><li>Weitere Informationen zu Funktionen, die als veraltet markiert wurden, finden Sie unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html?lang=de">Veraltete Funktionen</a>.</li><li>[Nur für Cloud Service-Migrationen] Bewerten der Cloud Service-Bereitschaft: Führen Sie den <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de">Best Practices Analyzer (BPA)</a> in der Quell-Umgebung aus. </li><li>Führen Sie eine Bewertung in Bezug auf wesentliche Änderungen und veraltete Funktionen in Experience Manager CS durch.</li></ul></td>
</tr>
<tr>
<td>Überprüfung</td>
<td><ul><li>Führen Sie anhand der Ergebnisse eine Aufwandsschätzung und Ressourcenplanung durch.</li></ul></td>
</tr>
<tr>
<td>Messen</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html?lang=de">Legen Sie Projekt-KPIs</a>, Erfolgskriterien und Projektzeitleisten fest.</li></ul></td>
</tr>
</table>

>[!NOTE]
>Mithilfe des Best Practices Analyzer-Berichts kann der Zeit- und Kostenaufwand für die Umstellung auf AEM as a Cloud Service schneller abgeschätzt werden, indem Informationen bereitgestellt werden, die andernfalls manuell erfasst und ausgewertet werden müssten.


<br>

### Ausführung

Bevor Sie mit der Ausführungsphase eines Projekts beginnen, sollten Sie Cloud Service integriert haben. Machen Sie sich auch mit Cloud Manager vertraut. Dies ist der Mechanismus zum Bereitstellen von Projekt-Code auf einer Experience Manager Cloud Service-Instanz.

Cloud Manager ermöglicht Unternehmen die Selbstverwaltung von Experience Manager in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung ([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/overview/ci-cd-pipelines.html?lang=de)), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen.

#### Inhaltsmigration

1. [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=de#migration): Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können.
1. [Paket-Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de#package-manager) : Wird zum Importieren und Exportieren von veränderlichen Inhalten des Repositorys verwendet.


#### Umgestalten/Optimieren

| Erste Schritte | Code überprüfen und umgestalten | Dispatcher-Überprüfung |
|---|---|---|
| <ul><li>[Lokale Entwicklungseinstellungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=de#local-development-environment-set-up)</li><li>[Lokale Dispatcher-Einrichtung](https://video.tv.adobe.com/v/32985?captions=ger)</li><li>[Code mit SDK-API-Jar kompilieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=de).</li><li>[AEM-Entwicklungsrichtlinien überprüfen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=de)<ul><li>Hintergrundaufgaben und Aufträge mit langer Laufzeit</li><li>Sling-Planungen</li><li>Nutzung von Eingabe-Streams und mehr</li></ul></li></ul> | <ul><li>Führen Sie den [Best Practices Analyzer (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de) in der Quell-Umgebung aus.[**Nur Migration**]<ul><li>Überlegungen zur Projektstruktur (basierend auf dem [Cloud-Archetyp](https://github.com/adobe/aem-project-archetype))<ul><li>Trennung von Code und Inhalt (veränderlich oder unveränderlich)</li><li>[Benutzerdefinierte Indexdefinitionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=de)</li><li>[Benutzerdefinierte Ausführungsmodi](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=de)</li></ul></li></ul></li><li>Überprüfen und Ausführen erforderlicher Änderungen</li><li>Im lokalen SDK [bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de)</li><li>Feuerproben über AEM-SDK durchführen</li></ul> | <ul><li>[Dispatcher-Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=de) für Umgestaltung überprüfen</li><li>Nutzen Sie gegebenenfalls das Tool [Dispatcher Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=de). [**Nur Migration**]</li><li>Tests können mit dem [Dispatcher-SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=de#prerequisites) durchgeführt werden.</li></ul> |

>[!TIP]
> Assets-Kunden : Überprüfung und Umgestaltung von Asset-Workflows mit den Tools zur [Asset-Cloud-Migration](https://github.com/adobe/aem-cloud-migration).


#### Bereitstellung/Live-Schaltung

1. [Im Cloud Manager-git bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/git-integration.html?lang=de)
2. Kunden-Code über die [Cloud Manager-Qualitäts-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-quality-testing.html?lang=de) ausführen
3. [In der Entwicklungsumgebung bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=de#debugging)
4. **Nur Migration** Inhaltstransfer mit Paketen oder dem [Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md)(CTT)
5. Empfohlene Testzyklen durchführen (Feuerprobe, QS und mehr)
6. In die Cloud Manager-Produktions-Pipeline weiterleiten
7. Validierung durch Feuerproben
8. Live-Schaltung

<br>

### Nach der Live-Schaltung

In der Phase nach der Live-Schaltung sollten Sie die Bereinigung temporärer Dateien sicherstellen, Best Practices für die kontinuierliche Entwicklung überprüfen und Protokolle verwalten.

>[!TIP]
>
> Es stehen Tools zur Fehlerbehebung in Umgebungen von AEM as a Cloud Service zur Verfügung.
>
>1. [Entwicklerkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=de)
>1. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html?lang=de)
>1. [Verwalten von Protokollen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html?lang=de)

<br>

### Tools und Ressourcen

| Bewertung | Umgestaltung | Experience Manager-Modernisierung | Inhaltsmigration |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de)</li></li> | <ul><li>[Unified Experience-Plug-in](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html?lang=de)</li></ul> | <ul><li>[Statischen Vorlagen in bearbeitbare Vorlagen](https://opensource.adobe.com/aem-modernize-tools/pages/structure.html)</li><li>[Design-Konfigurationen in Richtlinien](https://opensource.adobe.com/aem-modernize-tools/pages/policy.html) <li>[Foundation-Komponenten in Kernkomponenten](https://opensource.adobe.com/aem-modernize-tools/pages/component.html)</li><li>[Klassische Benutzeroberfläche in Touch-optimierte Benutzeroberfläche](https://opensource.adobe.com/aem-modernize-tools/pages/all-in-one.html)</li></ul> | <ul><li>[Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de)</li><li>[Paket-Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de#contentmanagement)</li></ul> |

>[!NOTE]
>
> Weitere Hilfe finden Sie unter:
>
>1. [Kontaktieren Sie das Experience Manager-Supportteam](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).
>1. [Experience Manager-Communities und -Foren](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community?profile.language=de&lang=de)
