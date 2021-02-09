---
title: Migration zu Experience Manager as a Cloud Service
description: Migration zu Experience Manager as a Cloud Service
translation-type: tm+mt
source-git-commit: dc2d529c6bbdb4e0fd963021e40bc333b321c95c
workflow-type: tm+mt
source-wordcount: '2117'
ht-degree: 100%

---


# Migration zu Adobe Experience Manager as a Cloud Service {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="Migration zu AEM as a Cloud Service"
>abstract="Beschreibt den empfohlenen schrittweisen Ansatz für den Übergang von Kunden von verschiedenen Experience Manager-Implementierungen zu Experience Manager as a Cloud Service und unterstützt bestehende Kunden bei der Bereitstellung zusammenhängender, kontinuierlicher Erlebnisse."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=de" text="Was ist neu und anders?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=de" text="Einführung in AEM as a Cloud Service."

Adobe Experience Manager (AEM) as a Cloud Service bietet eine neu strukturierte Grundlage für Experience Manager, die auf einer Container-basierten Infrastruktur, einer API-gesteuerten Entwicklung und einem geführten DevOps-Prozess aufbaut, sodass Marketing-Experten und Entwickler bei Innovationen im Customer Experience Management immer einen Schritt voraus sind.

Cloud Service vereint umfassende vorkonfigurierte Funktionen und Erweiterbarkeit von Adobe Experience Manager mit der Flexibilität der modernen Cloud-nativen Architektur, die es Marken ermöglicht, die sich ständig weiterentwickelnden Kundenanforderungen zu erfüllen.

Dieser Überblick beschreibt den empfohlenen schrittweisen Ansatz für den Übergang von Kunden von verschiedenen Experience Manager-Implementierungen zu Experience Manager as a Cloud Service und unterstützt bestehende Kunden bei der Bereitstellung zusammenhängender, kontinuierlicher Erlebnisse auf dieser modernen, speziell entwickelten Plattform für die Erlebnisverwaltung.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

<br>

## Erste Schritte mit Adobe Experience Manager as a Cloud Service {#getting-started}

| Was ist anders? | Architekturüberblick |
|--------------------------|--------------------------|
| <ul><li>[Moderne Architektur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=de)</li><li>[Automatische Aktualisierungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/aem-version-updates.html?lang=de#aem-version-updates)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=de)</li><li>[Asset-Microservices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=de)</li><li>[Binärdateien mit direktem Zugriff](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=de#asset-upload-with-direct-binary-access)</li><li>[Trennung von Code und Inhalt](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=de#developing)</li><li>[Replikation als Dienst](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/replication.html?lang=de)</li><li>[Admin Console, Gruppen-/Benutzermitgliedschaft und ACLs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=de)</li></ul> | <ul><li>[Einführung in die AEM-Architektur](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=de#underlying-technology)</li><li>[Umgebungsstapel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[Autorenebene](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=de#underlying-technology)</li><li>[Veröffentlichungsebene](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=de#content-delivery)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=de#content-delivery) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) (CI/CD)</li><li>[Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=de#onboarding-users-in-admin-console) über [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li><li>[Asset Compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/home.html?lang=de)</li></ul> |

![AEM as a Cloud Service – Laufzeitarchitektur](/help/core-concepts/assets/concepts-03.png "AEM as a Cloud Service – Laufzeitarchitektur")

<br>

## Entwickler in Adobe Experience Manager as a Cloud Service {#developer-journey}

### Entwickeln

Die Grundlagen der Code-Entwicklung in Adobe Experience Manager as a Cloud Service ähneln denen von Adobe Experience Manager On-Premise- und Managed Services-Lösungen.

Entwickler schreiben Code und testen ihn lokal, bevor sie ihn an Remote-Adobe Experience Manager as a Cloud Service-Umgebungen pushen.

In den Selbsthilferessourcen zur Implementierung von Experience Manager as a Cloud Service erfahren Sie, wie Sie Ihre Implementierung von Experience Manager as a Cloud Service anpassen können.

| Lokale Entwicklungseinrichtung | Vorbereitung |
|-----------|------------|
| <ol><li>Weitere Informationen finden Sie in der Dokumentation zum [Adobe Experience Manager-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=de#developing).</li><li>Sehen Sie sich [Installieren des Dispatcher-SDK](https://video.tv.adobe.com/v/30601) an, um zu verstehen, wie das Dispatcher-SDK installiert wird.</li><li>Sehen Sie sich [Konfigurieren des Dispatcher-SDK](https://video.tv.adobe.com/v/30602) an, um zu verstehen, wie Dispatcher-SDK konfiguriert wird.</li><li>Weitere Informationen finden Sie in der Dokumentation zu den [lokalen Entwicklungseinstellungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=de#local-development-environment-set-up).</li><li>Konfigurieren des Zugriffs auf Experience Manager – [Beispiel](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=de#accessing)</li></ol> | <ol><li>[Entwicklungsgrundlagen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Entwicklungsrichtlinien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#developing)</li><li>[Grundlegendes zur Experience Manager-Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)</li><li>[Digital Foundation Blueprint](https://solutionpartners.adobe.com/content/dam/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Stilsystem](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/style-system.html?lang=de#authoring)</li><li>[Überlagerungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/overlays.html?lang=de#developing)</li><li>[API-Referenz für Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/)</li></ol> |

>[!TIP]
> Weitere Informationen zum [Entwickeln und Bereitstellen von WKND im lokalen Experience Manager-SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de) finden Sie im Tutorial.

### Bereitstellen

Entwickler schreiben Code und testen ihn lokal, bevor sie ihn an Remote-AEM as a Cloud Service-Umgebungen pushen.

Dafür wird Cloud Manager benötigt, das ein optionales Tool zur Inhaltsbereitstellung für Managed Services war. Dies ist nun das einzige Verfahren zur Implementierung von Code in AEM as a Cloud Service-Umgebungen.

Informationen zur Konfiguration und Bereitstellung in AEM as a Cloud Service-Umgebungen finden Sie in den Selbsthilferessourcen.

1. [Konfigurieren von CM-Pipelines](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=de#using-cloud-manager)
   * Produktions-Pipeline
   * Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität
2. [Bereitstellen von Code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#using-cloud-manager)
3. [Grundlegendes zu Testergebnissen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=de#using-cloud-manager)
4. **Abrufen von Protokollen**
   * [über die CM-Benutzeroberfläche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=de#using-cloud-manager)
   * [über Adobe I/O-CLI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=de#debugging)
5. [Vorgänge und Wartung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/home.html?lang=de)
   * [Konfigurieren von OSGI-Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#deploying)
   * [Sichern und Wiederherstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=de)

>[!TIP]
> Weitere Informationen zum Bereitstellen von WKND für [Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/develop-wknd-tutorial.html?lang=de) finden Sie im Tutorial.

### Hilfe und Ressourcen

1. [Tipps und Tricks zum Debuggen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=de#debugging-aem-as-a-cloud-service)
2. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=de#debugging)  (Nur für lokale SDK- und Experience Manager Cloud-Entwicklungsumgebungen verfügbar)
4. [Protokolle und Protokollierung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [CM-Protokolle](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=de#debugging) (Build-Unit-Test, Code-Scan, Build-Image, Bereitstellung)
   * [Experience Manager Cloud Service-Protokolle](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Lokale SDK-Protokolle (unter host:port/crx-quickstart/logs)

>[!NOTE]
> Weitere Hilfe erhalten Sie hier:
>1. [Kontaktieren Sie das Experience Manager-Supportteam](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=de).
>2. [Experience Manager-Communities und -Foren](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)


<br>

## Wechsel zu Adobe Experience Manager as a Cloud Service {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Wechsel zu Adobe Experience Manager as a Cloud Service"
>abstract="Dieser Überblick beschreibt den empfohlenen schrittweisen Ansatz für den Übergang von Kunden von verschiedenen Experience Manager-Implementierungen zu Experience Manager as a Cloud Service und unterstützt bestehende Kunden bei der Bereitstellung zusammenhängender, kontinuierlicher Erlebnisse auf dieser modernen, speziell entwickelten Plattform für die Erlebnisverwaltung."

**Experience Manager as a Cloud Service bietet eine technologische Grundlage für Experience Manager Sites und Assets, sodass sich Marketing-Experten und IT darauf konzentrieren können, skaliert wirkungsvolle Erlebnisse bereitzustellen.**

Mit Experience Manager as a Cloud Service können sich Ihre Teams auf Innovationen konzentrieren, anstatt Produktaktualisierungen planen zu müssen. Neue Produktfunktionen werden umfassend getestet und ohne Unterbrechungen an Ihre Teams geliefert, sodass sie immer Zugriff auf das neueste Programm haben.

Die Umstellung auf Cloud Service umfasst drei Phasen: Planung, Ausführung und die Phase nach der Live-Schaltung.
Für eine erfolgreiche und reibungslose Umstellung sollten Sie eine ordnungsgemäße Planung sicherstellen und die in diesem Handbuch beschriebenen Best Practices einhalten.

Die nachstehende Abbildung zeigt eine bildliche Darstellung der empfohlenen Umstellung auf Cloud Service.

![image](/help/move-to-cloud-service/assets/home-img1.png)

<br>

### Planung

Bevor Sie mit der Umstellung auf Cloud Service beginnen, sollten Sie sich mit Experience Manager as a Cloud Service vertraut machen und die wichtigen Änderungen und Funktionen einsehen, die ersetzt oder eingestellt wurden.

<table>
<tr>
<td>Projektsuche und -bewertung</td>
<td><ul><li>Informationen zu wichtigen Unterschieden zwischen Experience Manager as a Cloud Service und Experience Manager 6.x finden Sie unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=de">Wesentliche Änderungen an Adobe Experience Manager as a Cloud Service</a>.</li><li>Weitere Informationen zu Funktionen, die als veraltet markiert wurden, finden Sie unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=de#deprecated-features">Veraltete Funktionen</a>.</li><li>[Nur für Cloud Service-Migrationen] Bewerten der Cloud Service-Bereitschaft: Führen Sie den <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration">Best Practices Analyzer (BPA)</a> in der Quell-Umgebung aus. </li><li>Führen Sie eine Bewertung in Bezug auf wesentliche Änderungen und veraltete Funktionen in Experience Manager CS durch.</li></ul></td>
</tr>
<tr>
<td>Überprüfung</td>
<td><ul><li>Führen Sie anhand der Ergebnisse eine Aufwandsschätzung und Ressourcenplanung durch.</li></ul></td>
</tr>
<tr>
<td>Messen</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">Legen Sie Projekt-KPIs</a>, Erfolgskriterien und Projektzeitleisten fest.</li></ul></td>
</tr>
</table>

>[!NOTE]
>Mithilfe des Best Practices Analyzer-Berichts kann der Zeit- und Kostenaufwand für die Umstellung auf AEM as a Cloud Service schneller abgeschätzt werden, indem Informationen bereitgestellt werden, die andernfalls manuell erfasst und ausgewertet werden müssten.


<br>

### Ausführung

Bevor Sie mit der Ausführungsphase eines Projekts beginnen, sollten Sie Cloud Service integriert haben. Machen Sie sich auch mit Cloud Manager vertraut. Dies ist der Mechanismus zum Bereitstellen von Projekt-Code auf einer Experience Manager Cloud Service-Instanz.

Cloud Manager ermöglicht Unternehmen die Selbstverwaltung von Experience Manager in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung ([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/overview/ci-cd-pipeline.html?lang=de#overview)), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen.

#### Inhaltsmigration

1. [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=de#migration): Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können.
2. [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de#package-manager) : Wird zum Importieren und Exportieren von veränderlichen Inhalten des Repositorys verwendet.


#### Umgestalten/Optimieren

| Erste Schritte | Code überprüfen und umgestalten | Dispatcher-Überprüfung |
|---|---|---|
| <ul><li>[Lokale Entwicklungseinstellungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[Lokale Dispatcher-Einrichtung](https://video.tv.adobe.com/v/30602/)</li><li>[Code mit SDK-API-Jar kompilieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing).</li><li>[AEM-Entwicklungsrichtlinien überprüfen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)<ul><li>Hintergrundaufgaben und Aufträge mit langer Laufzeit</li><li>Sling-Planungen</li><li>Nutzung von Eingabe-Streams und mehr</li></ul></li></ul> | <ul><li>Führen Sie den [Best Practices Analyzer (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de#cloud-migration) in der Quell-Umgebung aus.[**Nur Migration**]<ul><li>Überlegungen zur Projektstruktur (basierend auf dem [Cloud-Archetyp](https://github.com/adobe/aem-project-archetype))<ul><li>Trennung von Code und Inhalt (veränderlich oder unveränderlich)</li><li>[Benutzerdefinierte Indexdefinitionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=de#indexing)</li><li>[Benutzerdefinierte Ausführungsmodi](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de#runmodes)</li></ul></li></ul></li><li>Überprüfen und Ausführen erforderlicher Änderungen</li><li>Im lokalen SDK [bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en)</li><li>Feuerproben über AEM-SDK durchführen</li></ul> | <ul><li>[Dispatcher-Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=de#local-validation-of-dispatcher-configuration) für Umgestaltung überprüfen</li><li>Nutzen Sie gegebenenfalls den [Dispatcher Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=de#introduction-dispatcher). [**Nur Migration**]</li><li>Tests können mit dem [Dispatcher-SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=de#prerequisites) durchgeführt werden.</li></ul> |

>[!TIP]
> Assets-Kunden : Überprüfung und Umgestaltung von Asset-Workflows mit den Tools zur [Asset-Cloud-Migration](https://github.com/adobe/aem-cloud-migration).


#### Bereitstellung/Live-Schaltung

1. [Im Cloud Manager-git bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=de#managing-code)
2. Kunden-Code über die [Cloud Manager-Qualitäts-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#how-to-use) ausführen
3. [In der Entwicklungsumgebung bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**Nur Migration**] Inhaltstransfer mit Paketen oder dem [Content Transfer Tool](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md)(CTT)
5. Empfohlene Testzyklen durchführen (Feuerprobe, QS und mehr)
6. In die Cloud Manager-Produktions-Pipeline weiterleiten
7. Validierung durch Feuerproben
8. Live-Schaltung

<br>

### Nach der Live-Schaltung

In der Phase nach der Live-Schaltung sollten Sie die Bereinigung temporärer Dateien sicherstellen, Best Practices für die kontinuierliche Entwicklung überprüfen und Protokolle verwalten.

>[!TIP]
> Es stehen Tools zur Fehlerbehebung in AEM as a Cloud Service-Umgebungen zur Verfügung.
>1. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#aem-as-a-cloud-service-development-tools)
>2. [CRX/DE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging)
>3. [Verwalten von Protokollen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)


<br>

### Tools und Ressourcen

| Bewertung | Umgestaltung | Experience Manager-Modernisierung | Inhaltsmigration |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)</li></li> | <ul><li>[Unified Experience-Plug-in](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=de#refactoring-tools)</li></ul> | <ul><li>[Statischen Vorlagen in bearbeitbare Vorlagen](https://opensource.adobe.com/aem-modernize-tools/pages/tools/page-structure.html)</li><li>[Design-Konfigurationen in Richtlinien](https://opensource.adobe.com/aem-modernize-tools/pages/tools/policy-importer.html) <li>[Foundation-Komponenten in Kernkomponenten](https://opensource.adobe.com/aem-modernize-tools/pages/tools/component.html)</li><li>[Klassische Benutzeroberfläche in Touch-optimierte Benutzeroberfläche](https://opensource.adobe.com/aem-modernize-tools/pages/tools/dialog.html)</li></ul> | <ul><li>[Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#cloud-migration)</li><li>[Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de#contentmanagement)</li></ul> |

>[!NOTE]
> Weitere Hilfe erhalten Sie hier:
>1. [Kontaktieren Sie das Experience Manager-Supportteam](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en).
>2. [Experience Manager-Communities und -Foren](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

