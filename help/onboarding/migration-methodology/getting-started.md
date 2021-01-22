---
title: Migration zum Experience Manager als Cloud Service
description: Migration zum Experience Manager als Cloud Service
translation-type: tm+mt
source-git-commit: dc2d529c6bbdb4e0fd963021e40bc333b321c95c
workflow-type: tm+mt
source-wordcount: '2117'
ht-degree: 12%

---


# Migration nach Adobe Experience Manager als Cloud Service {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="Migration zu AEM als Cloud-Dienst"
>abstract="Erläutert den empfohlenen stufenweisen Ansatz für Transition-Kunden von verschiedenen Experience Manager-Bereitstellungen bis zum Experience Manager als Cloud Service und hilft Bestandskunden bei der Bereitstellung vernetzter, kontinuierlicher Erlebnisse"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en" text="Was ist neu und anders?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en" text="Einführung in AEM as a Cloud Service."

Adobe Experience Manager (AEM) als Cloud Service-Angebot bietet eine umgestaltete Grundlage für den Experience Manager, die auf einer Container-basierten Infrastruktur, API-basierter Entwicklung und einem geleiteten DevOps-Prozess aufbaut und es Marketingexperten und Entwicklern ermöglicht, stets die neuesten Entwicklungen im Bereich des Customer Experience Management zu verfolgen.

Cloud Service vereint umfassende Out-of-the-Box-Funktionen und Erweiterbarkeit von Adobe Experience Manager mit der Agilität der modernen Cloud-nativen Architektur, die es Marken ermöglicht, die ständig wachsende Verbrauchernachfrage zu befriedigen.

Dieser Einpager erläutert den empfohlenen Stufenansatz für Transitionen-Kunden von verschiedenen Experience Manager bis hin zum Experience Manager als Cloud Service und hilft Bestandskunden dabei, zusammenhängende, kontinuierliche Erlebnisse auf dieser modernen, bedarfsorientierten Plattform für Experience Management bereitzustellen.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

<br>

## Erste Schritte mit Adobe Experience Manager als Cloud Service {#getting-started}

| Was ist anders? | Architekturüberblick |
|--------------------------|--------------------------|
| <ul><li>[Moderne Architektur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[Automatische Updates](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/aem-version-updates.html?lang=en#aem-version-updates)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)</li><li>[Asset-Mikrodienste](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=de)</li><li>[Direct-Access-Binärdateien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=en#asset-upload-with-direct-binary-access)</li><li>[Trennung von Code und Inhalt](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Replikation als Dienst](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/replication.html?lang=en)</li><li>[Admin-Konsole, Gruppen-/Benutzermitgliedschaft und ACLs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li></ul> | <ul><li>[Einführung in AEM Architektur](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=en#underlying-technology)</li><li>[Umgebung-Stapel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[Autorenebene](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[AEM Publish-Ebene](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=en#content-delivery) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)  (CI/CD)</li><li>[Identitätsverwaltung ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#onboarding-users-in-admin-console) über  [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li><li>[Asset Compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service – Laufzeitarchitektur](/help/core-concepts/assets/concepts-03.png "AEM as a Cloud Service – Laufzeitarchitektur")

<br>

## Developer Journey in Adobe Experience Manager als Cloud Service {#developer-journey}

### Entwickeln

Die Grundlagen der Codeentwicklung sind in Adobe Experience Manager als Cloud Service vergleichbar mit den Adobe Experience Manager On Premise- und Managed Services-Lösungen.

Entwickler schreiben Code und testen ihn lokal, der dann als Cloud Service-Umgebung an das Remote-Adobe Experience Manager gesendet wird.

Informationen zum Anpassen des Experience Managers als Cloud Service finden Sie in den Selbsthilfe-Ressourcen zur Implementierung für Experience Manager als Cloud Service.

| Lokale Entwicklungseinrichtung | Was Sie vor Ihrem Beginn wissen sollten |
|-----------|------------|
| <ol><li>Weitere Informationen finden Sie in der Dokumentation zu [Adobe Experience Manager SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing).</li><li>Sehen Sie sich [Dispatcher SDK](https://video.tv.adobe.com/v/30601?captions=ger) installieren an, um zu erfahren, wie Sie Dispatcher SDK installieren.</li><li>Sehen Sie sich [Dispatcher-SDK konfigurieren](https://video.tv.adobe.com/v/30602?captions=ger) an, um zu erfahren, wie Sie Dispatcher-SDK konfigurieren</li><li>Weitere Informationen finden Sie in der Dokumentation zu [Lokale Entwicklungseinstellungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>Konfigurieren des Zugriffs auf Experience Manager [Durchlaufen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en#accessing)</li></ol> | <ol><li>[Entwicklungsgrundlagen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Entwicklungsrichtlinien](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)</li><li>[Die Projektstruktur des Experience Managers](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)</li><li>[Konzept der Digital Foundation](https://solutionpartners.adobe.com/content/dam/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Stilsystem](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/style-system.html?lang=en#authoring)</li><li>[Überlagerungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/overlays.html?lang=en#developing)</li><li>[Experience Manager als Cloud Service-API-Referenz](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/)</li></ol> |

>[!TIP]
> Siehe Lernprogramm zum Entwickeln und Bereitstellen von WKND auf dem lokalen Experience Manager-SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en)[

### Bereitstellung

Entwickler schreiben Code und testen ihn lokal, bevor sie ihn an Remote-AEM as a Cloud Service-Umgebungen pushen.

Dafür wird Cloud Manager benötigt, das ein optionales Tool zur Inhaltsbereitstellung für Managed Services war. Dies ist nun das einzige Verfahren zur Implementierung von Code in AEM as a Cloud Service-Umgebungen.

Informationen zum Konfigurieren und Bereitstellen auf AEM als Cloud Service-Umgebung finden Sie in den Selbsthilfe-Ressourcen.

1. [CM-Leitungen konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager)
   * Produktions-Pipeline
   * Produktionsfremde Pipelines und Pipelines für Tests der Codequalität
2. [Code bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#using-cloud-manager)
3. [Testergebnisse verstehen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=en#using-cloud-manager)
4. **Zugriff auf Protokolle**
   * [über CM-Benutzeroberfläche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)
   * [über Adobe i/o cli](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
5. [Betrieb und Instandhaltung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/home.html?lang=en)
   * [OSGI-Konfiguration konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#deploying)
   * [Sichern und Wiederherstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en)

>[!TIP]
> Siehe Übung zum Bereitstellen von WKND für Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/develop-wknd-tutorial.html?lang=en)[

### Hilfe und Ressourcen

1. [Tipps und Tricks zum Debuggen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en#debugging-aem-as-a-cloud-service)
2. [Entwicklerkonsole](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging) (Nur für lokale SDK- und Experience Manager Cloud Dev-Umgebung verfügbar)
4. [Protokolle und Protokollierung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [CM-Protokolle](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging) (Build-Unit-Test, Code-Scan, Build-Image, Bereitstellung)
   * [Experience Manager Cloud Service Logs](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Lokale SDK-Protokolle (unter host:port/crx-quickstart/logs)

>[!NOTE]
> Weitere Hilfe erhalten Sie unter Umständen:
>1. [Wenden Sie sich an das Experience Manager-Supportteam](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. [Experience Manager Communities und Foren](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)


<br>

## Wechsel nach Adobe Experience Manager als Cloud Service {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Auf Adobe Experience Manager als Cloud Service umziehen"
>abstract="Dieser Einpager erläutert den empfohlenen Stufenansatz für Transitionen-Kunden von verschiedenen Experience Manager bis hin zum Experience Manager als Cloud Service und hilft Bestandskunden dabei, zusammenhängende, kontinuierliche Erlebnisse auf dieser modernen, bedarfsorientierten Plattform für Experience Management bereitzustellen."

**Experience Manager als Cloud Service bietet eine skalierbare, sichere und agile Technologiebasis für Experience Manager-Sites und -Assets, die es Marketingexperten und IT-Mitarbeitern ermöglicht, sich auf die Bereitstellung effektiver Erlebnisse im Maßstab zu konzentrieren.**

Mit dem Experience Manager als Cloud Service können sich Ihre Teams auf Innovationen konzentrieren, anstatt Produktverbesserungen vorzunehmen. Neue Produktfunktionen werden umfassend getestet und ohne Unterbrechungen an Ihre Teams geliefert, sodass sie immer Zugriff auf die neueste Anwendung haben.

Die Umstellung auf Cloud Service umfasst drei Phasen: Planung, Ausführung und die Phase nach der Live-Schaltung.
Für eine erfolgreiche und reibungslose Umstellung sollten Sie eine ordnungsgemäße Planung sicherstellen und die in diesem Handbuch beschriebenen Best Practices einhalten.

Die nachstehende Abbildung zeigt eine bildliche Darstellung der empfohlenen Umstellung auf Cloud Service.

![image](/help/move-to-cloud-service/assets/home-img1.png)

<br>

### Planung

Bevor Sie mit dem Journey der Transition zum Cloud Service beginnen, sollten Sie sich mit dem Experience Manager als Cloud Service vertraut machen und die wesentlichen Änderungen überprüfen, die daran vorgenommen wurden, und auch die Funktionen überprüfen, die ersetzt oder nicht mehr unterstützt wurden.

<table>
<tr>
<td>Projektsuche und -bewertung</td>
<td><ul><li>Beachten Sie die wichtigen Unterschiede zwischen Adobe Experience Manager als Cloud Service und Experience Manager 6.x unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=en">Wichtige Änderungen am Experience Manager als Cloud Service</a>.</li><li>Weitere Informationen zu Funktionen, die als nicht mehr unterstützt markiert wurden, finden Sie unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=en#deprecated-features">Veraltete Funktionen</a>.</li><li>[Nur für Cloud Service-Migrationen] Beurteilung der Bereitschaft des Cloud Service: Führen Sie den <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration">Best Practices Analyzer(BPA)</a> auf der Quell-Umgebung aus. </li><li>Durchführen einer Bewertung zu wichtigen Änderungen und veralteten Funktionen in Experience Manager CS</li></ul></td>
</tr>
<tr>
<td>Überprüfen</td>
<td><ul><li>Führen Sie anhand der Entdeckungen Aufwandsschätzungen und Ressourcenbeschaffungsübungen durch.</li></ul></td>
</tr>
<tr>
<td>Maßnahme</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">Einrichtung von Projekt-KPIs</a>, Erfolgskriterien und Projektzeitschienen</li></ul></td>
</tr>
</table>

>[!NOTE]
>Der Bericht &quot;Best Practices-Analyzer&quot;beschleunigt die Abschätzung der Zeit und Kosten, die für die Transition als Cloud Service erforderlich sind, indem Informationen bereitgestellt werden, die andernfalls manuell erfasst und ausgewertet werden müssten.


<br>

### Ausführung

Vor dem Beginn der Ausführungsphase eines Projekts sollten Sie an Bord des Cloud Service sein. Sie müssen sich auch mit Cloud Manager vertraut machen. Dies ist der Mechanismus zum Bereitstellen von Projektcode auf einer Experience Manager Cloud Service-Instanz.

Cloud Manager ermöglicht Unternehmen die Selbstverwaltung von Experience Managern in der Cloud. Es enthält ein Framework zur kontinuierlichen Integration und zum kontinuierlichen Versand ([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/overview/ci-cd-pipeline.html?lang=en#overview)), mit dem IT-Teams und Implementierungspartner den Versand von Anpassungen oder Updates beschleunigen können, ohne dass dadurch die Leistung oder Sicherheit beeinträchtigt wird.

#### Inhaltsmigration

1. [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration) : zum Verschieben vorhandener Inhalte von einer Quellinstanz (On-Premise oder AMS) in die Zielgruppe AEM Cloud Service-Instanz verwendet.
2. [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#package-manager) : zum Importieren und Exportieren veränderlicher Inhalte des Repositorys verwendet werden.


#### Refaktorieren/Optimieren

| Erste Schritte | Code überprüfen und umrechnen | Dispatcher-Überprüfung |
|---|---|---|
| <ul><li>[Lokale Dev-Einrichtung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[Lokaler Dispatcher einrichten](https://video.tv.adobe.com/v/30602/?captions=ger)</li><li>[Kompilieren Sie Ihren Code mit SDK API jar](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[AEM Dev-Richtlinien überprüfen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)<ul><li>Hintergrundaufgaben und Aufträge mit langer Laufzeit</li><li>Sling-Planungen</li><li>Nutzung von Eingabestreams und mehr</li></ul></li></ul> | <ul><li>Führen Sie [Best Practices Analyzer(BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) auf der Quell-Umgebung aus.[**Nur Migration**]<ul><li>Überlegungen zur Projektstruktur (basierend auf [Cloud-Archetyp](https://github.com/adobe/aem-project-archetype))<ul><li>Trennung von Code und Inhalt (veränderlich oder unveränderlich)</li><li>[Benutzerdefinierte Indexdefinitionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#indexing)</li><li>[Benutzerdefinierte rundes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#runmodes)</li></ul></li></ul></li><li>Überprüfen und Ausführen erforderlicher Änderungen</li><li>[Auf lokalem SDK ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en) bereitstellen</li><li>Durchführung von Rauchtests über AEM SDK</li></ul> | <ul><li>Überprüfen Sie [Dispatcher-Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#local-validation-of-dispatcher-configuration) zur Umgestaltung</li><li>Verwenden Sie gegebenenfalls das Tool [Dispatcher Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=en#introduction-dispatcher). [**Nur Migration**]</li><li>Tests können mit [Dispatcher SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#prerequisites) durchgeführt werden</li></ul> |

>[!TIP]
> Assets Customers: Überprüfen und Neufaktorieren von Assets Workflows mithilfe der Werkzeuge [Asset Cloud-Migration](https://github.com/adobe/aem-cloud-migration)


#### Bereitstellung/GoLive

1. [In Cloud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=en#managing-code) Management bereitstellen
2. Führen Sie den Kundencode über die [Cloud Manager-Qualitätspipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) aus.
3. [In Umgebung für Entwicklung bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**Migration**] onlyContent transfer using packages or  [Content Transfer Tool](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md)(CTT)
5. Empfohlene Testzyklen durchführen (Rauch, QS und mehr)
6. In die Cloud Manager-Produktionspipeline hochladen
7. Rauchprüfung
8. Aufschalten

<br>

### Post-Go-Live

In der Phase nach der Live-Schaltung sollten Sie die Bereinigung temporärer Dateien sicherstellen, Best Practices für die kontinuierliche Entwicklung überprüfen und Protokolle verwalten.

>[!TIP]
> Es stehen Werkzeuge zur Fehlerbehebung AEM Cloud Service-Umgebung zur Verfügung
>1. [Entwicklerkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#aem-as-a-cloud-service-development-tools)
>2. [CRX/DE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging)
>3. [Verwalten von Protokollen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)


<br>

### Tools und Ressourcen

| Bewertung | Umgestaltung | Experience Manager-Modernisierung | Inhaltsmigration |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[Best Practices-Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)</li></li> | <ul><li>[Unified Experience Plugin](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#refactoring-tools)</li></ul> | <ul><li>[Statischen Vorlagen in bearbeitbare Vorlagen](https://opensource.adobe.com/aem-modernize-tools/pages/tools/page-structure.html)</li><li>[Designkonfigurationen in Richtlinien](https://opensource.adobe.com/aem-modernize-tools/pages/tools/policy-importer.html) <li>[Foundation-Komponenten in Kernkomponenten](https://opensource.adobe.com/aem-modernize-tools/pages/tools/component.html)</li><li>[Klassische Benutzeroberfläche in Touch-optimierte Benutzeroberfläche](https://opensource.adobe.com/aem-modernize-tools/pages/tools/dialog.html)</li></ul> | <ul><li>[Content Transfer-Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#cloud-migration)</li><li>[Package Manager verwendet](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement)</li></ul> |

>[!NOTE]
> Weitere Hilfe erhalten Sie unter Umständen:
>1. [Wenden Sie sich an das Experience Manager-Supportteam](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. [Experience Manager Communities und Foren](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

