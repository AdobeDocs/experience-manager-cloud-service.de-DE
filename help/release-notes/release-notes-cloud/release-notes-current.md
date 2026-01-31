---
title: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager] as a Cloud Service
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: c5c63e4ecfa099f953c1cf01861c0342ba4bae18
workflow-type: tm+mt
source-wordcount: '2145'
ht-degree: 37%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2023 oder 2024 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2026.1.0) ist der Freitag, 29. Januar 2026. Die nächste Versionsveröffentlichung (2026.2.0) ist für den Freitag, 26. Februar 2026 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## AEM Beta-Programme {#aem-beta-programs}

Beta-Programme für Adobe Experience Manager (AEM) bieten Kunden eine Möglichkeit, auf Vorabversionsfunktionen und -code zuzugreifen, Feedback zu geben und die Zukunft von AEM zu gestalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

**Vorteile der Teilnahme**
Wenn Sie frühzeitig auf von Adobe entwickelte Funktionen zugreifen können, können Kunden und Partner Feedback geben und die Produktentwicklung mitgestalten. Außerdem erhalten sie Unterstützung bei der Vorbereitung auf die Einführung neuer Funktionen vor der allgemeinen Verfügbarkeit.

**Aktuelle Beta-Programme**
In den folgenden Abschnitten sind aktive Beta-Programme aufgeführt.

### Agenten in AEM (Beta-Programm) {#agents-in-aem-beta-program}

Frühzeitiger Zugriff auf leistungsstarke, neue AEM-Funktionen für Produktion, Governance, Optimierung, Erkennung und Entwicklung. Ihr Feedback prägt direkt die Roadmap und die endgültigen Funktionen von Adobe. Weitere [ finden Sie unter „Übersicht über Agenten ](/help/ai-in-aem/agents/overview.md) AEM&quot;.

Dieses Programm dauert in der Regel 4-6 Wochen, kann aber so angepasst werden, dass es Ihre Fähigkeit zur aktiven Teilnahme berücksichtigt.

Um an diesem Programm teilzunehmen, senden Sie eine E-Mail an [](mailto:aemagentsteam@adobe.com)aemagentsteam@adobe.com. Geben Sie dabei so weit wie möglich die folgenden Details an:

* Namen und Adobe ID der Team-Mitglieder, die Agenten aktiv verwenden werden.
* Listen Sie bestimmte Agenten auf, die Sie oder Ihr Team verwenden werden. Oder sagen Sie einfach „Alle Agenten“.

Kunden, die für die Teilnahme ausgewählt wurden, werden direkt von Adobe benachrichtigt. Die Teilnahme unterliegt bestimmten Eignungskriterien, einschließlich Kundenlizenzierung und begrenzter Programmkapazität. Obwohl zunächst nicht alle Anfragen berücksichtigt werden können, werden in zukünftigen Beta-Schüben möglicherweise weitere Kunden in Betracht gezogen.

### AEM Foundation (Beta-Programme) {#aem-foundation-beta-programs}

Siehe [AEM Foundation-Betaprogramme](#foundation-early-adopter).

### Cloud Manager (Beta-Programme) {#cloud-manager-beta-programs}

Siehe [Cloud Manager-Beta-Programme](/help/implementing/cloud-manager/release-notes/current.md).

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Content MCP-Server {#content-MCP}

AEM Cloud Service enthält jetzt **Content-MCP-Server**, die eine standardisierte Möglichkeit für KI-gestützte Erlebnisse bieten, über MCP-kompatible Tools mit AEM-Inhalten zu arbeiten.

Entwickler und Power-User, die in Chat-Apps und Agentenplattformen arbeiten, können AEM mit benutzerdefinierten Kopiloten und Automatisierungen verbinden, sodass die Inhaltsarbeit Teil von End-to-End-Unternehmens-Workflows wird.

AEM bietet zwei Server:

1. **Schreibgeschützter Content MCP Server** - zum sicheren Abrufen von Inhalten
1. **Lese-/Schreib-Content-MCP-Server** - für Inhaltsänderungen

Diese MCP-Server umfassen Tools zum Arbeiten mit **Pages**, **Content Fragments** und **Assets** und können von den folgenden MCP-Clients verwendet werden: **ChatGPT**, **Claude**, **Cursor** und **Microsoft Copilot Studio**.

Weitere Informationen finden Sie unter [Verwenden von MCP mit AEM Cloud Service](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md). Bei Fragen oder Feedback senden Sie eine E-Mail an [aemcs-mcp-feedback@adobe.com](mailto:aemcs-mcp-feedback@adobe.com).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**KI-Suche**

KI-Suche führt ein intelligentes, kontextbezogenes Sucherlebnis ein, das über den herkömmlichen Keyword-Abgleich hinausgeht, indem es die Bedeutung und den Zweck hinter Benutzerabfragen versteht. Basierend auf KI und maschinellem Lernen liefert sie genauere Ergebnisse, selbst wenn Abfragen unterschiedlich formuliert sind, falsche Schreibweisen enthalten, Synonyme verwenden oder in verschiedenen Sprachen übermittelt werden, sodass Benutzende relevante Inhalte schneller und mit weniger Aufwand finden können.

Weitere Informationen finden Sie unter KI-Suchen in der Ansicht [Assets](/help/assets/search-assets-view.md#ai-search) und [Admin](/help/assets/search-assets.md#ai-search).

**Desktop-Programm Version 3.0.1**

[Desktop-Programm 3.0.1 (20. Dezember 2025)](https://experienceleague.adobe.com/de/docs/experience-manager-desktop-app/using/release-notes) verbessert die Zuverlässigkeit, Leistung und Stabilität aller wichtigen Workflows. Diese Version stellt eine konsistente Ordnerbenennung sicher, indem sie Synchronisierungsprobleme mit AEM Author behebt, die unterbrechungsfreie Verwendung der App während aktiver Übertragungen ermöglicht, die Reaktionsfähigkeit der Benutzeroberfläche durch asynchrone Verarbeitung verbessert, große Dateiübertragungen mit Paginierung optimiert und Stabilitätsprobleme behebt, einschließlich Neustarts des Autoren-Servers und Abstürze während großer Ordner-Uploads und -Downloads.

**Adobe Asset Link CEP-Version 2026.01.0**

[Adobe Asset Link CEP 2026.01.0](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) führt eine neue Option Fehlende Links neu verknüpfen in InDesign ein, die automatisch andere fehlende Assets aus demselben AEM-Ordner neu verknüpft. Die Funktion ordnet Assets basierend auf dem Dateinamen zu, wodurch der manuelle Aufwand beim Wiederherstellen defekter Links erheblich reduziert wird.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

* [Verbesserungen am Fußnoten-Platzhalter in adaptivem Forms (Foundation-Komponenten)](/help/forms/footnotes-richtextsupport.md):
   * Das Rendering von Fußnoten wurde weiter verfeinert, um die mehrzeilige Formatierung durch Zeilenumbrüche zu unterstützen und so eine klarere und ausdrucksstärkere Darstellung des Fußnoteninhalts zu ermöglichen.
   * Fußnoten bleiben nun unabhängig von der Sichtbarkeit der zugehörigen Bedienfelder dauerhaft im Fußnoten-Platzhalter sichtbar, wodurch ein einheitlicher Zugriff auf kritische Informationen gewährleistet ist.


### Neue Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

* [Werte aus einem JSON-Array abrufen](/help/forms/invoke-service-enhancements-rule-editor.md#retrieve-property-values-from-a-json-array): Erweiterte Datenintegrationsfunktionen ermöglichen jetzt den Aufruf von APIs über benutzerdefinierte Funktionen, um Werte effizient aus JSON-Arrays zu extrahieren und direkt an adaptive Formularfelder zu binden. Diese Verbesserung optimiert die Datennutzung, minimiert die manuelle Zuordnung und unterstützt dynamischere, datengesteuerte Formularerlebnisse.

* **Aufrufen der zugehörigen Benutzeroberfläche auf einer Veröffentlichungsinstanz**: Erweiterte Unterstützung ist jetzt verfügbar, um die zugehörige Benutzeroberfläche direkt auf Veröffentlichungsinstanzen aufzurufen. Diese Funktion definiert die erforderliche Konfiguration, Payload-Struktur und den Aufruffluss, vereinfacht die Integration und beschleunigt die Bereitstellung in allen Umgebungen.

<!--
**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. 
-->

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Wichtige Hinweise zu [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-notices}

#### Einstellung von Java-APIs {#java-api-deprecation}

Die veralteten APIs zum Entfernen von 2/26/2026 sollten nicht mehr im Code verwendet werden. Um Bereitstellungsblöcke zu verhindern, entfernen Sie die API-Nutzung vor dem 26. März 2026. Wichtige Daten:

* **Ab 26. Januar 2026**: Benachrichtigungs-E-Mails zum Aktionscenter werden **wöchentlich pro Umgebung** gesendet, um Sie daran zu erinnern, die Verwendung dieser APIs zu entfernen.
* **26. Februar 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet, **während** Schritts **Code-Qualität** angehalten. Bereitstellungs-Manager, Projekt-Manager oder Geschäftsinhaber können das Problem außer Kraft setzen, damit die Pipeline fortgesetzt werden kann.
* **26. März 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet **schlagen** während des **Code-Qualitäts-**-Schritts fehl **blockieren Bereitstellungen** neuen Codes, bis die Verwendung entfernt wird.
* **30. April 2026**: Umgebungen, die diese APIs weiterhin verwenden, **möglicherweise keine wichtigen Adobe-Versions-Updates mehr**.

Ausführliche Informationen finden Sie im [Artikel zur Einstellung](/help/release-notes/deprecated-removed-features.md#aem-apis). Als Referenz sind diese APIs unten aufgeführt:

+++ Zum Anzeigen der veralteten Java-APIs erweitern

* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.bson`
* `org.apache.jackrabbit.oak.plugins.blob`
* `org.apache.jackrabbit.oak.plugins.memory`

+++

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

#### Abschaffung der Java 11-Laufzeit {#java11-runtime-deprecation}

Adobe hat **Staging** und **Produktion** Umgebungen am 14. Oktober **2025 auf die leistungsfähigere Java 21 Runtime** aktualisiert. Ab **9.** (schrittweiser Rollout bis zum 11. Februar) funktionieren weder die AEM Cloud Service-SDK noch Cloud-Umgebungen mit der Java 11-Laufzeitumgebung.

>[!NOTE]
>
> Um die neuesten Leistungsoptimierungen und Sprachverbesserungen zu nutzen, wird empfohlen, mit Java 17 oder Java 21 (bevorzugt) zu erstellen. Das Erstellen mit Java 8 und Java 11 wird derzeit weiterhin unterstützt, wird aber in einer kommenden Version eingestellt. Vor der Einstellung wird eine separate Mitteilung veröffentlicht. Siehe den *Build-Zeitanforderungen* Abschnitt [dieses Artikels](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).
>

#### Durchsetzung der Konfigurationsrichtlinie für AEM-Java-Protokolle {#logconfig-policy}

AEM Java-Protokolle müssen einem Standardformat entsprechen, um eine zuverlässige Überwachung in allen Kundenumgebungen sicherzustellen. Benutzerdefinierte Protokollkonfigurationen – wie etwa Änderungen an der Protokollformatierung, Ausgabedateien oder Standardprotokollebenen – werden nicht mehr unterstützt. Protokolle müssen an die Standarddateien weitergeleitet werden, und die standardmäßigen Protokollebenen für AEM-Produkt-Code müssen beibehalten werden. Ausführliche Informationen finden Sie im [Artikel zur Protokollierung](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Alle nicht unterstützten benutzerdefinierten Protokollierungsüberschreibungen *werden jetzt ignoriert*. Die meisten Kunden waren davon nicht betroffen und Adobe hat sich mit Kunden in Verbindung gesetzt, deren aktuelle Konfiguration möglicherweise betroffen ist.

Bitte überprüfen und aktualisieren Sie alle nachgelagerten Prozesse, die auf einem benutzerdefinierten Protokollierungsverhalten basieren. Zum Beispiel:

* Wenn Ihr Protokollweiterleitungssystem ein benutzerdefiniertes Protokollformat erwartet, müssen Sie möglicherweise Ihre Aufnahmeregeln anpassen.
* Wenn Sie zuvor die Ausführlichkeit des Protokolls durch Ändern der Protokollebenen reduziert haben, beachten Sie, dass eine Rückkehr zu den Standardebenen das Protokollvolumen erhöhen kann.

### Early-Adopter-Funktionen in [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-early-adopter}

#### Pausieren der automatischen Wartungsaktualisierungen {#pause-updates}

Tage, an denen die Live-Schaltung geschieht, Live-Ereignisse stattfinden oder Spitzenumsätze erzielt werden – in diesen Momenten muss alles funktionieren. [Unsere neuen Self-Service-Funktionen](/help/implementing/deploying/quiet-hours-update-free-periods.md) stoppen automatische Wartungs-Updates, wenn dies notwendig ist, damit Ihre Teams fokussiert bleiben.

* Ruhezeiten: Blockieren Sie die automatische Wartung während jeden Tag während festgelegter Zeiten. Ideal für Arbeitszeiten, nächtliche Ausführungen oder morgendliche Umstellungen.
* Update-freier Zeitraum: Blockieren Sie die automatische Wartung für eine ganze Woche. Verwenden Sie dies für Launches, Promos oder jährliche Pausen.

>[!NOTE]
>
>Verfügbar als Funktion mit eingeschränkter Verfügbarkeit am 25. September.
>Senden Sie eine E-Mail an [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com), um sie in Ihren Programmen zu aktivieren.
>

#### AEM Edge-Funktionen (Beta-Programm) {#edge-functions}

Mit AEM Edge-Funktionen (in früheren Versionshinweisen als *Edge Computing* bezeichnet) können Sie JavaScript auf CDN-Ebene ausführen, wodurch die Datenverarbeitung näher am Endbenutzer liegt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge.

Häufige Anwendungsszenarien umfassen:

* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Umformatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer API-Antworten), bevor sie an den Browser gesendet werden
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden
* Bereitstellen eines MCP-Servers für LLMs wie ChatGPT und Claude für den Zugriff auf benutzerdefinierte Tools

Wir haben nur eine begrenzte Anzahl von Möglichkeiten für die AEM-Veröffentlichungsbereitstellung oder Edge Delivery Services-Projekte für Live-Produktions-Sites. Wenn Sie an einer Teilnahme interessiert sind oder mehr erfahren möchten, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls.

#### Edge-Authentifizierung für Edge Delivery Services (Beta-Programm) {#edge-authentication}

Mit der Edge-Authentifizierung können Sie den Zugriff auf Edge Delivery Services-Seiten auf diejenigen beschränken, die sich bei Ihrem Identitätsanbieter (IdP) authentifiziert haben. Dies wird durch die Bereitstellung einer YAML-Konfigurationsdatei von OpenID Connect (OIDC) erreicht.

Bei Interesse senden Sie bitte eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls und allen Fragen, die Sie haben.

#### Canary-Produktionsbereitstellungen zum Testen von Code vor Annahme von Live-Traffic (Beta-Programm) {#canary-beta}

Validieren Sie einen Produktions-Build mit reinem Test-Traffic, bevor Sie ihn für Endbenutzende verfügbar machen. Senden Sie an die Produktion, leiten Sie nur den Canary-Traffic weiter (mithilfe einem speziellen Header) und überwachen Sie das Verhalten. Leiten Sie den Live-Traffic dann entweder weiter oder setzen Sie ihn zurück, ohne dass sich dies auf die Kundinnen und Kunden auswirkt.

Stellen Sie Ihre Code-Versionen für die Produktion bereit, beschränken Sie sie jedoch auf internen Test-Traffic, bevor Sie entscheiden, ob Sie Live-Traffic annehmen oder zurücksetzen.

Senden Sie eine E-Mail an [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com), um Zugriff anzufordern und Feedback mitzuteilen.

#### KI-Antworten - Intelligentere, kontextbezogene Antworten für AEM Sites (Beta-Programm) {#ai-answers-beta}

Mit KI-Antworten erhalten Ihre Besucher eine neue Möglichkeit, mit Ihren Inhalten zu interagieren. Basierend auf der RAG-Technologie (Retrieval-Augmented Generation) nutzt diese Lösung Ihre von AEM verwalteten Daten, um direkt in Ihren digitalen Erlebnissen präzise, markenkonsistente Antworten bereitzustellen.

Wir bereiten uns darauf vor, das Beta-Programm für KI-Antworten zu starten, und laden Kunden jetzt ein, ihr Interesse zu registrieren. Da die Kapazität der Beta-Version sehr begrenzt sein wird, werden frühe Anmeldungen vorrangig berücksichtigt. Durch die Teilnahme an der Beta-Version können Sie KI-Antworten in Ihrer AEM Cloud Service-Umgebung untersuchen, die Leistung und Genauigkeit überprüfen und die zukünftige Erfahrung gestalten, bevor sie allgemein verfügbar wird.

Um eine Teilnahme anzufordern oder Updates zu erhalten, wenden Sie sich bitte an [feedback-ai-answers@adobe.com](mailto:feedback-ai-answers@adobe.com).

#### Snapshots für RDEs (Beta-Programm) {#rde-snapshot-program}

In der Beta-Phase unterstützen schnelle Entwicklungsumgebungen (RDEs) jetzt eine Funktion, um einen Schnappschuss des aktuellen Status von Code und Inhalten zu erstellen, der zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

Senden Sie eine E-Mail an [](mailto:aemcs-rde-support@adobe.com)aemcs-rde-support@adobe.com), wenn Sie an der Verwendung dieser Funktion und der Bereitstellung von Feedback dazu interessiert sind.

#### KI-Tools für IDEs für AEM Java und Dispatcher-Entwicklung (Beta-Programm) {#ai-dev-beta}

Java-Stack-Teams verwenden zunehmend KI-unterstützte Entwicklung in Tools wie Cursor, Claude Code, Visual Studio und IntelliJ, um die Funktionsbereitstellung zu beschleunigen und die Code-Qualität zu verbessern. Beta-Version hinzufügen für:

* Austausch von Erfahrungen aus der Praxis, um zukünftige von Adobe unterstützte KI-Funktionen zu gestalten
* Testen Sie IDE-Tools, die von KI-Agenten verwendet werden können, um AEM-Code und Dispatcher-Konfiguration zu generieren und zu debuggen

Für weitere Informationen senden Sie eine E[Mail an ](mailto:aemcs-java-adopter@adobe.com)aemcs-java-adopter@adobe.com.

#### Erweiterte Leistungsüberwachung von Anwendungen (APM) (Alpha-Programm) {#apm-alpha}

Zur Beobachtung unterstützt AEM Cloud Service derzeit von Adobe bereitgestelltes [New Relic One](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) und kundenverwaltetes [Dynatrace](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace). Da wir gerade Unterstützung für weitere APM-Optionen prüfen, bitten wir Sie, uns eine E-Mail an [aemcs-apm-beta@adobe.com](mailto:aemcs-apm-beta@adobe.com) zu senden und uns Ihren bevorzugten Anbieter bzw. Ihre bevorzugte Technologie sowie Ihre Anwendungsfälle mitzuteilen.

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Universeller Editor {#universal-editor}

Eine vollständige Liste der Versionen des universellen Editors finden Sie [hier](/help/release-notes/universal-editor/current.md).

## Generieren von Varianten {#generate-variations}

Eine vollständige Liste der Versionen für das Generieren von Varianten finden Sie [hier](/help/generative-ai/release-notes-generate-variations.md).

## Versionshinweise zu Experience Cloud {#experience-cloud}

Informationen zu Versionen anderer Experience Cloud-Anwendungen finden Sie [hier](https://experienceleague.adobe.com/de/docs/release-notes/experience-cloud/current).
