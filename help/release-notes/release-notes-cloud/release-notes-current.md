---
title: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager] as a Cloud Service
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 49d29c468a2047e3026948030c3663db0beada53
workflow-type: tm+mt
source-wordcount: '1944'
ht-degree: 35%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2026.2.0) ist der Mittwoch, 3. März 2026. Die nächste Version (2026.3.0) ist für den Freitag, 26. März 2026 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video zur Versionsübersicht Februar 2026 an, das eine Zusammenfassung der Funktionen bietet, die der Version 2026.2.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3480408/?captions=ger&quality=12)


## AEM Beta-Programme {#aem-beta-programs}

Beta-Programme für Adobe Experience Manager (AEM) bieten Kunden eine Möglichkeit, auf Vorabversionsfunktionen und -code zuzugreifen, Feedback zu geben und die Zukunft von AEM zu gestalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

**Vorteile der Teilnahme**
Wenn Sie frühzeitig auf von Adobe entwickelte Funktionen zugreifen können, können Kunden und Partner Feedback geben und die Produktentwicklung mitgestalten. Außerdem erhalten sie Unterstützung bei der Vorbereitung auf die Einführung neuer Funktionen vor der allgemeinen Verfügbarkeit.

**Aktuelle Beta-Programme**
In den folgenden Abschnitten sind aktive Beta-Programme aufgeführt.

### Agenten in AEM {#agents-in-aem}

Wenn Sie die leistungsstarken, neuen AEM agentischen Funktionen in den Bereichen Produktion, Governance, Optimierung, Ermittlung und Entwicklung erkunden möchten, [informieren Sie sich hier darüber, wie Sie darauf zugreifen können.](/help/ai-in-aem/agents/overview.md)

<!--
### Agents in AEM (Explorer program) {#agents-in-aem-beta-program}

Gain early access to powerful, new AEM agentic capabilities across production, governance, optimization, discovery, and development. Your feedback directly shapes Adobe's roadmap and final features. See [Overview of Agents in AEM](/help/ai-in-aem/agents/overview.md) to learn more.

This program typically lasts 4-6 weeks, but can be tailored to be flexible around your ability to actively participate. 

To opt in to participate in this program, email [aemagentsteam@adobe.com](mailto:aemagentsteam@adobe.com) and include the following details to the extent possible:

* Names and Adobe ID's of team members who will actively use agents.
* List Specific agents that you or your team will want to use. Or simply say "All Agents."

Customers selected for participation will be notified directly by Adobe. Participation is subject to eligibility considerations, including customer licensing and limited program capacity. While not all requests can be accommodated initially, additional customers may be considered in future beta waves.
-->

### AEM Foundation (Beta-Programme) {#aem-foundation-beta-programs}

Siehe [AEM Foundation-Betaprogramme](#foundation-early-adopter).

### Cloud Manager (Beta-Programme) {#cloud-manager-beta-programs}

Siehe [Cloud Manager-Beta-Programme](/help/implementing/cloud-manager/release-notes/current.md).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Content Advisor für den Zugriff auf AEM Assets in Adobe Express**

[Content Advisor ist jetzt in Adobe Expreß &#x200B;](/help/assets/native-integration-adobe-express.md) verfügbar und führt die intelligente Asset Discovery für AEM Assets direkt in der Express-Oberfläche ein. Content Advisor bietet kontextbezogene Empfehlungen auf der Grundlage von Leinwand-Content und Kampagnenbeschreibungen, unterstützt KI-gestützte Suche, ermöglicht native Unterstützung für kanalbereite, &quot;on the fly&quot;-Ausgabedarstellungen auf Basis von Dynamic Media und bietet viele weitere Funktionen. Mit Content Advisor könnt ihr genehmigte Assets auf völlig neue Weise erkennen und verwenden. So könnt ihr Inhalte schneller finden und eure Workflows optimieren.

### Neue Funktionen in Dynamic Media mit OpenAPI {#dynamic-media-openAPI-new-features}

**Attributbasierte Zugriffssteuerung (ABAC) für Dynamic Media mit OpenAPI**

Die attributbasierte Zugriffssteuerung (ABAC) ermöglicht es Admins, den Zugriff auf Dynamic Media mit OpenAPI-Assets mithilfe von metadatengesteuerten Regeln zu steuern. Admins können Regeln für Benutzergruppen basierend auf Asset-Metadaten definieren, um zu bestimmen, welche Assets für bestimmte Gruppen sichtbar sind. Wenn die Metadaten eines Assets den definierten Bedingungen entsprechen, wird automatisch Zugriff gewährt. Diese Funktion hilft Unternehmen bei der Durchsetzung besserer Governance und stellt sicher, dass Benutzer Dynamic Media nur mit OpenAPI-Assets anzeigen und damit arbeiten können, die für ihre Rolle oder Berechtigungen relevant sind.

>[!NOTE]
>
>Die attributbasierte Zugriffssteuerung (ABAC) für Dynamic Media mit OpenAPI ist eine Funktion mit begrenzter Verfügbarkeit. Sie können es aktivieren, indem Sie ein „Support[Ticket“ &#x200B;](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Early-Access-Funktionen in AEM Forms {#forms-early-access-features}

**Anzeigen von Beschriftungen für das Dropdown-Menü &quot;Mehrfachauswahl&quot; auf der Übermittlungs-PDF**
Dropdownkomponenten mit Mehrfachauswahl in Adaptive Forms rendern jetzt ihre ausgewählten Anzeigebeschriftungen auf der [generierten Übermittlungs-PDF](/help/forms/generate-document-of-record-core-components.md), um sicherzustellen, dass das Dokument genau das widerspiegelt, was Benutzer auf dem Formular sehen.

**Verbesserte Zugänglichkeit für Kontrollkästchen-, Optionsfeld- und Bedienfeldkomponenten**
Adaptive Forms-Kernkomponenten führen WCAG 2.2-kompatibles semantisches Markup für [Kontrollkästchengruppen(v2)](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group), [Optionsfeldgruppen(v2)](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button) und die [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) ein. Diese Komponenten verwenden `<fieldset>`- und `<legend>`-HTML-Elemente, um sinnvolle Beziehungen zwischen Gruppenbezeichnungen und ihren Optionen herzustellen. Dies ermöglicht eine präzise Interpretation durch Bildschirmlesehilfen und andere Hilfstechnologien.

**Versionsunterstützung in Forms Manager**
Forms Manager unterstützt jetzt [&#x200B; die Versionierung für Adaptive Forms (Core Components und Foundation Components)](/help/forms/manage-form-versions-forms-manager.md), Formularfragmente, Designs, XDP-Vorlagen und binäre Assets. Erstellen Sie Versionen, zeigen Sie den vollständigen Versionsverlauf an und stellen Sie frühere Status Ihrer Formularelemente direkt in der Forms &amp; Dokumente -Konsole wieder her.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation - Neue Funktionen {#foundation-new}

#### Pausieren der automatischen Wartungsaktualisierungen {#pause-updates}

Tage, an denen die Live-Schaltung geschieht, Live-Ereignisse stattfinden oder Spitzenumsätze erzielt werden – in diesen Momenten muss alles funktionieren. [Unsere neuen Self-Service-Funktionen](/help/implementing/deploying/quiet-hours-update-free-periods.md) stoppen automatische Wartungs-Updates, wenn dies notwendig ist, damit Ihre Teams fokussiert bleiben.

* Ruhezeiten: Blockieren Sie die automatische Wartung während jeden Tag während festgelegter Zeiten. Ideal für Arbeitszeiten, nächtliche Ausführungen oder morgendliche Umstellungen.
* Update-freier Zeitraum: Blockieren Sie die automatische Wartung für eine ganze Woche. Verwenden Sie dies für Launches, Promos oder jährliche Pausen.

#### Fehlerbehebung bei Code-Qualitäts-Pipelines mit dem Entwicklungsagenten {#devagent-codequality}

Die Pipeline-Fehlerbehebungsfunktionen des Entwicklungs-Agenten helfen Entwicklerinnen und Entwicklern, Probleme in AEM as a Cloud Service-Bereitstellungen effizienter zu diagnostizieren und zu beheben.

Die Fehlerbehebung bei Pipelines, die sich zuvor auf **Build- und Unit** Tests“ konzentrierte, unterstützt jetzt auch den **Code-Scan**-Schritt in Pipelines zur Full-Stack-Bereitstellung und Code-Qualität.

Der Code-Überprüfungsschritt bewertet den Code anhand von Qualitätsregeln, erkennt Sicherheitslücken und generiert detaillierte Qualitätsberichte. Wenn dieser Schritt fehlschlägt, können Sie den KI-Assistenten verwenden, um den Entwicklungsagenten zu einer Ursachenanalyse zusammen mit empfohlenen Anleitungen zur Behebung aufzufordern.

Erfahren Sie mehr über den [Entwicklungsagenten](/help/ai-in-aem/agents/brand-experience/development/development.md) und die Fehlerbehebung bei Pipelines.

### Wichtige Hinweise zu [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-notices}

#### Einstellung von Java-APIs {#java-api-deprecation}

Die veralteten APIs zum Entfernen von 2/26/2026 sollten nicht mehr im Code verwendet werden. Um Bereitstellungsblöcke zu verhindern, entfernen Sie die API-Nutzung vor dem 30. März 2026. Wichtige Daten:

* **Ab 26. Januar 2026**: Benachrichtigungs-E-Mails zum Aktionscenter werden als Erinnerung gesendet, um die Verwendung dieser APIs zu entfernen.
* **26. Februar 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet, werden während des Schritts **Codequalität** **angehalten**. Ein Bereitstellungsmanager, Projektmanager oder Geschäftsinhaber kann das Problem überschreiben, damit die Pipeline fortgesetzt werden kann. *Dies kann die Validierung und Veröffentlichung von Codeänderungen verlangsamen.*
* **30. März 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet, schlagen **fehl** während des Schritts **Codequalität**. Bereitstellungen werden blockiert, bis die veraltete API-Verwendung entfernt wird. *Dies kann verhindern, dass zeitkritische Updates veröffentlicht werden, und sich auf Ihre Geschäftsabläufe auswirken.*
* **4. Mai 2026**: Umgebungen, die weiterhin veraltete APIs verwenden **erhalten keine wichtigen Adobe-Versions-** und unterliegen nicht den Standardverpflichtungen von Adobe in Bezug auf Leistung und Verfügbarkeit. Infolgedessen erhalten Sie keine neuen Funktionen oder Fehlerbehebungen, die Anwendungsstabilität und -verfügbarkeit kann sich negativ auswirken und das Sicherheitsrisiko kann weiter zunehmen.

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
* `org.apache.jackrabbit.oak.plugins.memory`

+++

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

### Early-Adopter-Funktionen in [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-early-adopter}

#### AEM Edge-Funktionen (Beta-Programm) {#edge-functions}

Mit AEM Edge Functions können Sie JavaScript auf der CDN-Ebene ausführen, um die Datenverarbeitung näher an den Endbenutzer heranzuführen. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge.

Häufige Anwendungsszenarien umfassen:

* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Umformatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer API-Antworten), bevor sie an den Browser gesendet werden
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden
* Bereitstellen eines MCP-Servers für LLMs wie ChatGPT und Claude für den Zugriff auf benutzerdefinierte Tools

Wir haben nur eine begrenzte Anzahl von Möglichkeiten für die AEM-Veröffentlichungsbereitstellung oder Edge Delivery Services-Projekte für Live-Produktions-Sites. Wenn Sie an einer Teilnahme interessiert sind oder mehr erfahren möchten, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls.

#### Cloud Manager MCP-Server (Beta-Programm) {#cm-mcp-server}

>[!VIDEO](https://video.tv.adobe.com/v/3480351/?captions=ger&quality=12)

Moderne IDEs verwenden das Model Context Protocol (MCP), um umfangreichen Sprachmodellen (LLMs) das Aufrufen von Tools zu ermöglichen, die von MCP-Servern bereitgestellt werden. Anstatt direkt in allgemeine API-Spezifikationen zu integrieren, können Entwickler ihre Absicht einfach in natürlicher Sprache beschreiben.

Der jetzt in der Beta-Version verfügbare Cloud Manager MCP-Server ermöglicht die direkte Interaktion mit Cloud Manager-APIs über eine IDE mithilfe von Eingabeaufforderungen. Unterstützte Szenarien sind das Ausführen von Pipelines, das Überprüfen des Umgebungsstatus und vieles mehr.

Weitere Informationen zu [AEM MCP-Servern](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md). Um den Zugriff auf die Betaversion des Cloud Manager MCP-Servers anzufordern, senden Sie eine E-Mail an [aemcs-mcp-feedback@adobe.com](mailto:aemcs-mcp-feedback@adobe.com) und fügen Sie eine Beschreibung Ihres Anwendungsfalls hinzu.

#### Fehlerbehebung bei der Web-Stufen-Konfigurations-Pipeline mit dem Entwicklungsagenten (Beta-Programm) {#devagent-webtier}

Die Funktionen [Fehlerbehebung bei Pipelines](/help/ai-in-aem/agents/brand-experience/development/development.md) des Entwicklungsagenten helfen Entwicklerinnen und Entwicklern bei der effizienten Diagnose und Lösung von Problemen in AEM as a Cloud Service-Bereitstellungen. Zusätzlich zur Unterstützung von Full-Stack-Pipelines (Bereitstellung und Code-Qualität) unterstützt der Entwicklungsagent jetzt die Fehlerbehebung für die **Web Tier Config-Pipeline** als Teil eines Beta-Programms.

aem-devagent@adobe.com Um Zugriff auf die Beta-Version anzufordern, senden Sie eine E-Mail an [&#128279;](mailto:aem-devagent@adobe.com). Bereits vorhandener Zugriff auf Agenten in AEM ist erforderlich.

#### IDE-KI-Tools für die Entwicklung von AEM Java und Dispatcher (Beta-Programm) {#ai-dev-beta}

Java-Stack-Teams verwenden zunehmend KI-unterstützte Entwicklung in Tools wie Cursor, Claude Code, Visual Studio und IntelliJ, um die Funktionsbereitstellung zu beschleunigen und die Code-Qualität zu verbessern. Beta-Version hinzufügen für:

* Austausch von Erfahrungen aus der Praxis, um zukünftige von Adobe unterstützte KI-Funktionen zu gestalten
* Testen Sie IDE-Tools, die von KI-Agenten verwendet werden können, um AEM-Code und Dispatcher-Konfiguration zu generieren und zu debuggen

Für weitere Informationen senden Sie eine E[Mail an &#x200B;](mailto:aemcs-java-adopter@adobe.com)aemcs-java-adopter@adobe.com.

#### IDE AI-Tools für die Migration von AEM 6.5 zu AEM Cloud Service (Alpha-Programm) {#cm-ide-migration}

Beschleunigen Sie die Migration von AEM 6.5 zu AEM as a Cloud Service (Java-Stack), indem Sie IDE-KI-Tools verwenden, um die Empfehlungen des [Best Practices Analyzer-Berichts“ &#x200B;](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

Für weitere Informationen senden Sie eine E[Mail an &#x200B;](mailto:aem-devagent@adobe.com)aem-devagent@adobe.com.

#### Edge-Authentifizierung für Edge Delivery Services (Beta-Programm) {#edge-authentication}

Mit der Edge-Authentifizierung können Sie den Zugriff auf Edge Delivery Services-Seiten auf diejenigen beschränken, die sich bei Ihrem Identitätsanbieter (IdP) authentifiziert haben. Dies wird durch die Bereitstellung einer YAML-Konfigurationsdatei von OpenID Connect (OIDC) erreicht.

Bei Interesse senden Sie bitte eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls und allen Fragen, die Sie haben.

#### Canary-Produktionsbereitstellungen zum Testen von Code vor Annahme von Live-Traffic (Beta-Programm) {#canary-beta}

Validieren Sie einen Produktions-Build mit reinem Test-Traffic, bevor Sie ihn für Endbenutzende verfügbar machen. Senden Sie an die Produktion, leiten Sie nur den Canary-Traffic weiter (mithilfe einem speziellen Header) und überwachen Sie das Verhalten. Leiten Sie den Live-Traffic dann entweder weiter oder setzen Sie ihn zurück, ohne dass sich dies auf die Kundinnen und Kunden auswirkt.

Stellen Sie Ihre Code-Versionen für die Produktion bereit, beschränken Sie sie jedoch auf internen Test-Traffic, bevor Sie entscheiden, ob Sie Live-Traffic annehmen oder zurücksetzen.

Senden Sie eine E-Mail an [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com), um Zugriff anzufordern und Feedback mitzuteilen.

#### Snapshots für RDEs (Beta-Programm) {#rde-snapshot-program}

In der Beta-Phase unterstützen schnelle Entwicklungsumgebungen (RDEs) jetzt eine Funktion, um einen Schnappschuss des aktuellen Status von Code und Inhalten zu erstellen, der zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

Senden Sie eine E-Mail an [&#128279;](mailto:aemcs-rde-support@adobe.com)aemcs-rde-support@adobe.com), wenn Sie an der Verwendung dieser Funktion und der Bereitstellung von Feedback dazu interessiert sind.

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
