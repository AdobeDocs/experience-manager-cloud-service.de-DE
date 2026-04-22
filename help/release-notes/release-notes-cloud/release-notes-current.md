---
title: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager] as a Cloud Service
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: a10a4bf02d5e006e6c151b48606c4e9412193a14
workflow-type: tm+mt
source-wordcount: '2180'
ht-degree: 29%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2026.3.0) ist der Freitag, 26. März 2026. Die nächste Version mit neuen Funktionen (2026.4.0) ist für den Freitag, 30. April 2026 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Werfen Sie einen Blick auf das Video „Versionsübersicht März 2026“ für eine Zusammenfassung der neuen Funktionen in der Version 2026.3.0:

>[!VIDEO](https://video.tv.adobe.com/v/3483060/?quality=12)

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

Wenn Sie die leistungsstarken neuen AEM-Agentenfunktionen für Produktion, Governance, Optimierung, Erkennung und Entwicklung erkunden möchten, [erfahren Sie hier, wie Sie darauf zugreifen können.](/help/ai-in-aem/agents/overview.md)

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

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Ein-/Auschecken von Inhaltsfragmenten {#cf-checkout-in}

Um die Parität mit der Touch-optimierten Benutzeroberfläche von AEM zu verbessern, können Inhaltsfragmente jetzt auch über die neue Admin-Benutzeroberfläche für Inhaltsfragmente ein- und ausgecheckt werden. Die Auscheckfunktion bleibt unverändert, sodass ein ausgechecktes Inhaltsfragment effektiv gesperrt wird und somit verhindert wird, dass es von anderen Benutzern im Inhaltsfragment-Editor bearbeitet wird. Benutzende, die ein Inhaltsfragment besitzen, und Admins können das Fragment aus- und wieder einchecken. Das Auschecken eines Fragments hat keine Auswirkungen auf referenzierte untergeordnete Fragmente oder Assets.

### Bedienfeld „Inhaltsfragmentstarts“ {#cf-launches-jobs}

Asynchrone Aufträge für Inhaltsfragment-Starts können jetzt im Bedienfeld Eigenschaften der Admin-Benutzeroberfläche für Inhaltsfragment-Starts angezeigt werden, um ihren Status zu beobachten - wenn ein Auftrag noch ausgeführt wird, bereits abgeschlossen wurde oder abgebrochen wurde, zusammen mit relevanten Details zum Auftrag.

### Aktualisierung auf RTE des Inhaltsfragment-Editors {#cf-rte-update}

Der Rich-Text-Editor (RTE) des Inhaltsfragment-Editors wurde von TinyMCE zu TipTap migriert. Diese Änderung bringt eine Reihe von Vorteilen mit sich.

* Der universelle Editor und der Inhaltsfragment-Editor verwenden jetzt denselben RTE-Technologie-Stack.
   * Dies bedeutet, dass beide Editoren jetzt dieselbe HTML erstellen.
   * Erweiterungen können jetzt wiederverwendet werden.
   * Die gleichen Funktionen und Methoden sind jetzt mit beiden Editoren verfügbar (in Headless-Anwendungsfällen).
   * Das letztendliche Ziel besteht darin, dass eine Konfiguration zu einem einheitlichen Erlebnis in beiden Editoren führt.
* Der Inhaltseditor bietet jetzt ein neues Erscheinungsbild im Spectrum 2-Stil.
* Im Inhaltsfragment-Editor stehen neue Funktionen zur Verfügung, einschließlich Suchen und Ersetzen und Beraten für Inhalte.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Inhaltsberater in AEM Sites**

Der Content Advisor ist jetzt in AEM Sites verfügbar und führt direkt die intelligente Asset-Erkennung über AEM Assets ein. Benutzer können mühelos die relevantesten Assets direkt in ihrem Workflow finden, durchsuchen und wiederverwenden, sodass sie keine Kontexte wechseln müssen.

Der Content Advisor bietet intelligente Funktionen für Assets, wie beispielsweise auf Kampagnenübersichten basierende Vorschläge, kontextuelle Vorschläge, Zugriff auf Dynamic Media-Ausgabedarstellungen und detaillierte Asset-Metadaten.

Bald verfügbar - Unterstützung von Content Advisor für Adobe Workfront- und AJO B2C-Anwendungen, einschließlich der Möglichkeit, Inhaltsfragmente zu entdecken

### Neue Funktionen in Dynamic Media {#dynamic-media-new-features}

#### Aktualisierungen des Dynamic Media-Vorlageneditors {#dynamic-media-template-editor-updates}

**Verbesserungen beim Ebenenmanagement**

* Ebenen per Drag-and-Drop neu anordnen: Ebenen können jetzt direkt im Ebenenbedienfeld durch Ziehen neu angeordnet werden. Dies bietet eine schnellere und intuitivere Möglichkeit, die Stapelreihenfolge der Ebenen über die vorhandenen Aktionen „Vorwärts bewegen“ oder „Rückwärts senden“ hinaus zu organisieren.
* Kopieren, Einfügen und Duplizieren: Vollständige Unterstützung für das Kopieren, Einfügen und Duplizieren von Ebenen mit Tastaturbefehlen (Strg+C, V, D) oder dem Kontextmenü mit Unterstützung für mehrschichtige Auswahlen.
* Schaltfläche „Eigenschaften der Ebene trennen“: Die dedizierte Schaltfläche „Ebeneneigenschaften“ wurde hinzugefügt, um die Navigation zu den Ebeneneinstellungen zu erleichtern. Für den schnellen Zugriff können Sie auf Ebenen mit Doppelklick auf Unterstützung doppelklicken.

**Textformatierungsfunktionen**

* Zeilenabstand steuern : Der neue Zeilenabstand-Schieberegler ermöglicht die präzise Steuerung der Zeilenhöhe in Textebenen mit vollständiger Unterstützung einschließlich Rückgängig/Wiederholen und Vorlagenspeichern/Laden.
* Formatierung für Großbuchstaben: Textebenen unterstützen jetzt die Formatierungsoption „Alle Großbuchstaben“ in der Symbolleiste „Schriftstil“ neben „Fett“, „Kursiv“ und „Unterstrichen“.
* Optionen für die vertikale Ausrichtung : Es wurden Steuerelemente für die vertikale Ausrichtung für Textebenen hinzugefügt, die eine präzisere Textpositionierung innerhalb von Textfeldern ermöglichen.

**Steuerelemente für Größe und Dimension**

* Seitenverhältnis entsperren : Benutzende können jetzt das Seitenverhältnis beim Anpassen der Größeneigenschaften entsperren, was unabhängige Breiten- und Höhenanpassungen für eine flexiblere Ebenengröße ermöglicht.
* Konfiguration von Einpassungslinien: Es wurde Unterstützung für `copyfitlines`- und `copyfitmaxlines` in Eigenschaften von Einpassungslinien für Text hinzugefügt, um das Einpassungsverhalten besser steuern zu können.

**Optisches Polieren**

* Aktualisierte Symbole für Timer- und Shape-Ebenen mit verfeinerten Spectrum 2 (S2) Design-System-Symbolen.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Early-Access-Funktionen in AEM Forms {#forms-early-access-features}

**Kennzeichnungen für das Dropdown-Menü mit Mehrfachauswahl in der Übermittlungs-PDF anzeigen**
Mehrfachauswahl-Dropdown-Komponenten in adaptiver Forms rendern jetzt ihre ausgewählten Anzeigebeschriftungen in der [generierten Übermittlungs-PDF](/help/forms/generate-document-of-record-core-components.md), um sicherzustellen, dass das Dokument genau das widerspiegelt, was Benutzende im Formular sehen.

**Verbesserte Barrierefreiheit für Kontrollkästchen-, Optionsfeld- und Bedienfeldkomponenten**
Adaptive Forms-Kernkomponenten führen WCAG 2.2-konformes semantisches Markup für [Kontrollkästchen-Gruppen (v2)](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group), [Optionsfeldgruppen (v2)](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button) und die [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) ein. Diese Komponenten nutzen `<fieldset>` und `<legend>` HTML-Elemente, um aussagekräftige Beziehungen zwischen Gruppenbeschriftungen und ihren Optionen herzustellen und so eine genaue Interpretation durch Bildschirmlesehilfen und andere Hilfstechnologien zu ermöglichen.

**Versionierungsunterstützung in Forms Manager**
Forms Manager [unterstützt jetzt die Versionierung für adaptive Forms (Kernkomponenten und Foundation-Komponenten](/help/forms/manage-form-versions-forms-manager.md), Formularfragmente, Designs, XDP-Vorlagen und binäre Assets. Erstellen Sie Versionen, zeigen Sie den vollständigen Versionsverlauf an und stellen Sie frühere Status Ihrer Formular-Assets direkt über die Konsole Forms und Dokumente wieder her.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation - Neue Funktionen {#foundation-new}

#### Vereinfachte Indexverwaltung {#simplified-index-management}

[Vereinfachte Indexverwaltung](https://oak-indexing.github.io/oakTools/simplified.html) bietet eine einfachere Möglichkeit, benutzerdefinierte Indizes zu definieren und vordefinierte Indizes (OOTB) mit einer JSON-Datei anzupassen, ohne vollständige Definitionen zu kopieren oder Versionen manuell zu verwalten. Anpassungen werden mit dem neuesten vorkonfigurierten Index zusammengeführt, und bei Bedarf wird eine neue Indexversion erstellt.

#### Cloud Manager MCP-Server {#cm-mcp-server}

>[!VIDEO](https://video.tv.adobe.com/v/3480340/?quality=12)

Moderne IDEs verwenden das Model Context Protocol (MCP), um umfangreichen Sprachmodellen (LLMs) das Aufrufen von Tools zu ermöglichen, die von MCP-Servern bereitgestellt werden. Anstatt direkt in allgemeine API-Spezifikationen zu integrieren, können Entwickler ihre Absicht einfach in natürlicher Sprache beschreiben.

Der Cloud Manager MCP-Server ermöglicht die direkte Interaktion mit Cloud Manager-APIs über die IDE mithilfe von Eingabeaufforderungen. Zu den unterstützten Szenarien gehören die Ausführung von Pipelines, die Überprüfung des Umgebungsstatus und mehr.

Weitere Informationen zu [AEM MCP-Servern](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md).

### Wichtige Hinweise zu [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-notices}

#### Einstellung von Java-APIs {#java-api-deprecation}

Die veralteten APIs zum Entfernen von 2/26/2026 sollten nicht mehr im Code verwendet werden. Um Bereitstellungsblöcke zu verhindern, entfernen Sie die API-Nutzung vor dem **30. März 2026**. Wichtige Daten:

* **Ab 26. Januar 2026**: Benachrichtigungs-E-Mails zum Aktionscenter werden als Erinnerung gesendet, um die Verwendung dieser APIs zu entfernen.
* **26. Februar 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet, **während** Schritts **Code-Qualität** angehalten. Bereitstellungs-Manager, Projekt-Manager oder Geschäftsinhaber können das Problem außer Kraft setzen, damit die Pipeline fortgesetzt werden kann. *Dies kann Ihre Fähigkeit, Code-Änderungen zu validieren und freizugeben, verlangsamen.*
* **30. März 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet **schlagen** während des **Code-** fehl. Bereitstellungen werden blockiert, bis die veraltete API-Nutzung entfernt wird. *Dies kann verhindern, dass zeitkritische Updates veröffentlicht werden, und sich auf Ihre Geschäftsabläufe auswirken.*
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

### Early-Adopter-Funktionen in [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-early-adopter}

#### IDE-KI-Tools für die Entwicklung von AEM Java und Dispatcher (öffentliches Beta-Programm) {#ai-dev-beta}

Java-Stack-Teams verwenden zunehmend KI-unterstützte Entwicklung in Tools wie Cursor, Claude Code, Visual Studio und IntelliJ, um die Funktionsbereitstellung zu beschleunigen und die Code-Qualität zu verbessern.

Beteiligen Sie sich an der öffentlichen Beta-Version (keine Anmeldung erforderlich), um IDE-Tools auszuprobieren, die von Codierungs-Agenten verwendet werden können, um AEM-Code und Dispatcher-Konfigurationen zu generieren und zu debuggen.

Weitere Informationen finden Sie in der [Dokumentation zur lokalen Entwicklung mit KI](/help/ai-in-aem/local-development-with-ai-tools.md)Tools und in der E-Mail [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com) mit Fragen oder Feedback.

#### AEM Edge-Funktionen (Beta-Programm) {#edge-functions}

[AEM Edge-](/help/implementing/developing/introduction/edge-functions.md): Ermöglicht die Ausführung von JavaScript auf CDN-Ebene, wodurch die Datenverarbeitung näher am Endbenutzer rückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge.

Häufige Anwendungsszenarien umfassen:

* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Umformatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer API-Antworten), bevor sie an den Browser gesendet werden
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden
* Bereitstellen eines MCP-Servers für LLMs wie ChatGPT und Claude für den Zugriff auf benutzerdefinierte Tools

Wir haben nur eine begrenzte Anzahl von Möglichkeiten für die AEM-Veröffentlichungsbereitstellung oder Edge Delivery Services-Projekte für Live-Produktions-Sites. Wenn Sie an einer Teilnahme interessiert sind oder mehr erfahren möchten, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls.

#### Fehlerbehebung bei der Web-Stufen-Konfigurations-Pipeline mit dem Entwicklungsagenten (Beta-Programm) {#devagent-webtier}

Die Funktionen [Fehlerbehebung bei Pipelines](/help/ai-in-aem/agents/brand-experience/development/development.md) des Entwicklungsagenten helfen Entwicklerinnen und Entwicklern bei der effizienten Diagnose und Lösung von Problemen in AEM as a Cloud Service-Bereitstellungen. Zusätzlich zur Unterstützung von Full-Stack-Pipelines (Bereitstellung und Code-Qualität) unterstützt der Entwicklungsagent jetzt die Fehlerbehebung für die **Web Tier Config-Pipeline** als Teil eines Beta-Programms.

aem-devagent@adobe.com Um Zugriff auf die Beta-Version anzufordern, senden Sie eine E-Mail an [](mailto:aem-devagent@adobe.com). Bereits vorhandener Zugriff auf Agenten in AEM ist erforderlich.

#### IDE AI-Tools für die Migration von AEM 6.5 zu AEM Cloud Service (Alpha-Programm) {#cm-ide-migration}

Beschleunigen Sie die Migration von AEM 6.5 zu AEM as a Cloud Service (Java-Stack), indem Sie IDE-KI-Tools verwenden, um die Empfehlungen des [Best Practices Analyzer-Berichts“ ](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

Für weitere Informationen senden Sie eine E[Mail an ](mailto:aemcs-ai-ide-tools-feedback@adobe.com)aemcs-ai-ide-tools-feedback@adobe.com.

#### Edge-Authentifizierung für Edge Delivery Services (Beta-Programm) {#edge-authentication}

Mit der Edge-Authentifizierung können Sie den Zugriff auf Edge Delivery Services-Seiten auf diejenigen beschränken, die sich bei Ihrem Identitätsanbieter (IdP) authentifiziert haben. Dies wird durch die Bereitstellung einer YAML-Konfigurationsdatei von OpenID Connect (OIDC) erreicht.

Bei Interesse senden Sie bitte eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls und allen Fragen, die Sie haben.

#### Canary-Produktionsbereitstellungen zum Testen von Code vor Annahme von Live-Traffic (Beta-Programm) {#canary-beta}

Validieren Sie einen Produktions-Build mit reinem Test-Traffic, bevor Sie ihn für Endbenutzende verfügbar machen. Senden Sie an die Produktion, leiten Sie nur den Canary-Traffic weiter (mithilfe einem speziellen Header) und überwachen Sie das Verhalten. Leiten Sie den Live-Traffic dann entweder weiter oder setzen Sie ihn zurück, ohne dass sich dies auf die Kundinnen und Kunden auswirkt.

Stellen Sie Ihre Code-Versionen für die Produktion bereit, beschränken Sie sie jedoch auf internen Test-Traffic, bevor Sie entscheiden, ob Sie Live-Traffic annehmen oder zurücksetzen.

Senden Sie eine E-Mail an [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com), um Zugriff anzufordern und Feedback mitzuteilen.

#### Snapshots für RDEs (Beta-Programm) {#rde-snapshot-program}

In der Beta-Phase unterstützen schnelle Entwicklungsumgebungen (RDEs) jetzt eine Funktion, um einen Schnappschuss des aktuellen Status von Code und Inhalten zu erstellen, der zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

Senden Sie eine E-Mail an [](mailto:aemcs-rde-support@adobe.com)aemcs-rde-support@adobe.com), wenn Sie an der Verwendung dieser Funktion und der Bereitstellung von Feedback dazu interessiert sind.

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
