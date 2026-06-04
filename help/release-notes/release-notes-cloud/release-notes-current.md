---
title: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager] as a Cloud Service
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 3443e9d000cf9ddc4f4f2ac18bcdf614688f5242
workflow-type: tm+mt
source-wordcount: '2287'
ht-degree: 28%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen wie 2024 oder 2025 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2026.5.0) war der 28. Mai 2026. Die nächste Version (2026.6.0) ist für den 25. Juni 2026 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the May 2026 Release Overview video for a summary of the features added in the 2026.5.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3491490/?quality=12)

-->

## AEM Beta-Programme {#aem-beta-programs}

Beta-Programme für Adobe Experience Manager (AEM) bieten Kunden eine Möglichkeit, auf Vorabversionsfunktionen und -code zuzugreifen, Feedback zu geben und die Zukunft von AEM zu gestalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

**Vorteile der Teilnahme**

Wenn Sie frühzeitig auf von Adobe entwickelte Funktionen zugreifen können, können Kunden und Partner Feedback geben und die Produktentwicklung mitgestalten. Außerdem erhalten sie Unterstützung bei der Vorbereitung auf die Einführung neuer Funktionen vor der allgemeinen Verfügbarkeit.

**Aktuelle Beta-Programme**

In den folgenden Abschnitten sind aktive Beta- und Early-Access-Programme aufgeführt.

### Agenten in AEM (frühzeitiger Zugriff){#agents-in-aem}

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

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in Content Hub {#new-features-content-hub}

**KI-Suche**

AEM Assets Content Hub enthält jetzt KI-Suchen, eine erweiterte Suchfunktion, die die Bedeutung und den Zweck von Benutzerabfragen versteht, anstatt sich nur auf exakte Keyword-Übereinstimmungen zu verlassen. KI-Suche liefert genauere und kontextbezogene Ergebnisse, indem sie Beziehungen zwischen Wörtern, Konzepten und der Benutzerabsicht erkennt. Es unterstützt mehrsprachige Abfragen, verarbeitet Rechtschreibfehler und Tippfehler, versteht Synonyme und zeigt relevante Assets, auch wenn Benutzende keine exakten Metadatenbegriffe verwenden.

Bei einer Suche nach `Woman drinking coffee` können beispielsweise auch Assets zurückgegeben werden, die mit verwandten Begriffen wie `Lady`, `Girl`, `Latte` oder `Cappuccino` getaggt wurden.

Admins können KI-Suchen in Content Hub über das Konfigurationsmenü aktivieren oder deaktivieren, indem sie entweder KI-Suchen oder die herkömmliche Keyword-Suche auswählen.


**Benutzerdefinierte Sortieroptionen**

Mit Content Hub können Admins jetzt benutzerdefinierte Metadatenfelder als Sortieroptionen auf der Content Hub-Startseite aktivieren. Zusätzlich zu den standardmäßigen Sortieroptionen, Größe, Geändert, Name und Relevanz können Admins geschäftsspezifische Metadatenfelder wie Kanal, Region, SKU oder Kampagne konfigurieren, um Benutzenden zu helfen, Suchergebnisse effektiver zu organisieren.

**Asset-Suche und Download-Ereignisunterstützung für Bereitstellungs-APIs**

AEM Assets-Bereitstellungs-APIs unterstützen jetzt die Asset-Suche und Asset-Download-Ereignisse, sodass Unternehmen verfolgen und darauf reagieren können, wie Assets in allen verbundenen Anwendungen und Erlebnissen erkannt und genutzt werden. Diese Ereignisse verbessern die Sichtbarkeit von Asset-Nutzungsmustern, unterstützen Analyse- und Reporting-Workflows und vereinfachen die Integration mit externen Systemen und Automatisierungsprozessen.

Mit ereignisgesteuerten Einblicken können Teams die Interaktion mit Inhalten besser verstehen und vernetztere Workflows für digitale Assets erstellen. Weitere Informationen finden Sie in der [API-Dokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/asset_downloaded).

**Asset-Bereitstellungs-URL**

Content Hub ermöglicht es Benutzenden jetzt, die Bereitstellungs-URL eines Assets direkt aus den Asset-Eigenschaften zu kopieren. Diese Verbesserung erleichtert die Freigabe und Einbettung genehmigter Assets auf Websites, Anwendungen und externen Systemen. Durch schnellen Zugriff auf bereitstellungsfertige Links können Teams die Workflows für die Inhaltsverteilung optimieren und die Wiederverwendung von Assets in digitalen Erlebnissen beschleunigen.

>[!IMPORTANT]
>
>Diese Funktionen sind als Funktionen mit begrenzter Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.


### Neue Funktionen in Dynamic Media mit OpenAPI-Funktionen {#new-features-dynamic-media-openapi}

**Intelligentes Zuschneiden von Videos**

Dynamic Media mit OpenAPI-Funktionen unterstützen jetzt smartes Zuschneiden von Videos für Video-Assets in AEM Assets. Smartes Zuschneiden von Videos verwendet eine KI-gestützte Analyse, um das primäre Subjekt automatisch über verschiedene Seitenverhältnisse und Geräte hinweg im Fokus zu halten und so optimierte Anzeigeerlebnisse im Web und auf Mobilgeräten bereitzustellen. Nach der Aktivierung und Konfiguration durch Admins können Unternehmen smarte zugeschnittene Videoausgaben für genehmigte Assets generieren und während der Wiedergabe dynamisch das am besten geeignete Frame bereitstellen.

**Unterstützung für mehrere Untertitel und Audiospuren für Videos**

Dynamic Media mit OpenAPI-Funktionen unterstützen jetzt mehrere Untertitel und mehrere Audiospuren für Video-Assets. Die Lösung ermöglicht es Unternehmen, lokalisierte und barrierefreie Videoerlebnisse für globale Zielgruppen bereitzustellen, indem mehrere sprachspezifische Untertitel und Audiospuren mit einem einzigen primären Video verknüpft werden. Autoren können diese Inhalte effizient über eine einheitliche Benutzeroberfläche verwalten, wodurch die Bereitstellung mehrsprachiger Inhalte vereinfacht und regionale Barrierefreiheitsanforderungen unterstützt werden.

>[!IMPORTANT]
>
>Diese Funktionen sind als Funktionen mit begrenzter Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in AEM Forms

* **Versionierungsunterstützung in Forms Manager**
Forms Manager [unterstützt jetzt die Versionierung für adaptive Forms (Kernkomponenten und Foundation-Komponenten](/help/forms/manage-form-versions-forms-manager.md), Formularfragmente, Designs, XDP-Vorlagen und binäre Assets. Erstellen Sie Versionen, zeigen Sie den vollständigen Versionsverlauf an und stellen Sie frühere Status Ihrer Formular-Assets direkt über die Konsole Forms und Dokumente wieder her.

* **Überschreiben der reCAPTCHA-Cloud-Konfiguration mit OSGi** 
ReCAPTCHA Enterprise-Projekt-IDs, Site-Schlüssel und Geheimnisse, die Sie mit Ihren Quelldateien aufbewahren, können in jeder Cloud Service-Umgebung in unterschiedliche Werte aufgelöst werden, nachdem Sie [die kontextabhängige Außerkraftsetzung der Konfiguration hinzufügen und über Cloud Manager bereitstellen](/help/forms/captcha-adaptive-forms.md#override-recaptcha-osgi).

* **Zertifikatbasierte Authentifizierung** 
Adaptive Forms, die an eine Microsoft SharePoint-Liste senden, unterstützen jetzt [zertifikatbasierte Authentifizierung](/help/forms/connect-forms-to-sharepoint-list.md#certificate-based-authentication) neben der OAuth-URL-Authentifizierung. Für die zertifikatbasierte Anmeldung müssen Sie einen Zertifikatalias und Mandantendetails in AEM und Microsoft Azure registrieren.

* **Verbesserungen beim Regeleditor**

   * Der Regeleditor für adaptive Forms unterstützt jetzt die vereinfachte Grammatik für [Ereignisregeln für Dispatch und Bei Trigger für vordefinierte (OOTB) Trigger und für benutzerdefinierte Ereignisse](/help/forms/rule-editor-enhancements-use-cases.md#simplified-grammar-for-ootb-and-custom-events) sodass Autorinnen und Autoren nicht nur auf Grammatik für benutzerdefinierte Trigger beschränkt sind.
   * Wenn Regeln für adaptive Forms, die auf Kernkomponenten basieren, jetzt die [Dateianlagenkomponente zusammen mit anderen Bedingungen unter Verwendung der Und- oder Oder-Logik](/help/forms/rule-editor-enhancements-use-cases.md#combined-when-conditions-with-the-file-attachment-component) enthalten, führt die Regel ihre Aktionen nur aus, wenn der Anlagenstatus und die anderen Prüfungen alle wie beabsichtigt auswerten.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation - Neue Funktionen {#foundation-new}

#### KI-gestützte Code-Migration zu AEM as a Cloud Service {#aem-ide-cs-migration}

Beschleunigen Sie die Migration von AEM 6.5 (oder früher) zu AEM as a Cloud Service (Java-Stack), indem Sie IDE-KI-Tools verwenden, um die Empfehlungen des Best Practices Analyzer-Berichts zu befolgen.

Erfahren Sie mehr über [IDE-KI-Tools für die Cloud](/help/journey-migration/cloud-migration-skill/overview-cloud-migration-skill.md)Migration und auch über andere [Lokale Entwicklung mit KI-Tools](/help/ai-in-aem/local-development-with-ai-tools.md) (Agentenkenntnisse und lokale MCP-Server).

>[!VIDEO](https://video.tv.adobe.com/v/3491438/?quality=12)

#### Änderungen der Anzeige des Status der Replikationswarteschlange {#replication-queue-status-display}

In der Authoring-Benutzeroberfläche zeigen Replikationsagenten jetzt zwei konsolidierte Warteschlangen an - **persistiert** und **vollständig veröffentlicht** - anstelle separater Warteschlangen pro Publishing-Pod. Dies reduziert die Komplexität und spiegelt die automatische Skalierung der Publishing-Ebene wider.

Weitere Informationen zu [Replikationswarteschlangen](/help/operations/replication.md#replication-queues).

![Replikationswarteschlangen mit persistenten und vollständig veröffentlichten ](/help/operations/assets/replication-queues.png "Replikationswarteschlangen")

### Wichtige Hinweise zu [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation-notices}

#### Rich-Fehler bei der IMS-Authentifizierung {#ims-auth-rich-errors}

Zur Fehlerbehebung bei IMS-Integrationen unterstützt `imsauth` jetzt *Rich-Fehler*.

Anstatt nur einen HTTP-Status-Code zurückzugeben, bieten diese Fehler zusätzlichen Kontext, um Probleme zu diagnostizieren und zu beheben, die die Authentifizierung und den Zugriff blockieren können.

#### Einstellung von Java-APIs {#java-api-deprecation}

Es ist wichtig, die Verwendung veralteter APIs zu entfernen.

Seit **14.** schlagen Cloud Manager-Pipelines, die Code enthalten, der mit APIs zum Entfernen von 2/26/2026 **, während des** fehl. Bereitstellungen werden blockiert, bis die veraltete API-Nutzung entfernt wird. *Dies kann verhindern, dass zeitkritische Updates veröffentlicht werden, und sich auf Ihre Geschäftsabläufe auswirken.*

Ab **11. Juni 2026** Umgebungen, die diese veralteten APIs verwenden, **keine wichtigen Adobe-Versions-Updates** und unterliegen nicht den Standardverpflichtungen von Adobe in Bezug auf Leistung und Verfügbarkeit. Infolgedessen erhalten Sie keine neuen Funktionen oder Fehlerbehebungen, die Anwendungsstabilität und -verfügbarkeit kann sich negativ auswirken und das Sicherheitsrisiko kann weiter zunehmen.

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

#### Verwalten von Ruhezeiten und Aktualisieren von Freizeiten mit dem AEM AI Assistant (eingeschränkte Verfügbarkeit) {#quiet-hours-ai}

Ruhestunden können jetzt direkt über den AEM AI-Assistenten angezeigt, erstellt und bearbeitet sowie Freizeiten aktualisiert werden.
Der Hauptvorteil liegt in der Verringerung von Zeitplanfehlern. Wenn Sie eine Anfrage stellen, führt Sie der Assistent durch das Mögliche und kennzeichnet die geltenden Beschränkungen, z. B. die Obergrenze für drei Zeiträume, die obligatorische Lücke von einer Woche zwischen Zeiträumen und die geplanten Zeitfenster für Wartungsausschlüsse, für die Sie keinen Zeitplan festlegen können. Anstatt also nach einer fehlgeschlagenen Konfiguration eine Einschränkung zu ermitteln, werden Geschäftsinhaber und Bereitstellungs-Manager im selben Gespräch auf einen gültigen Zeitplan geleitet. Dadurch werden wichtige Geschäftsfenster vor automatischen Wartungs-Updates geschützt und gleichzeitig das Hin- und Herschieben und Fehlkonfigurieren reduziert.

#### Snapshots für RDEs (*Public Beta*-Programm) {#rde-snapshot-program}

In der öffentlichen Beta-Version (Anfang Juni) unterstützen schnelle Entwicklungsumgebungen (RDEs) jetzt eine Funktion [um einen Schnappschuss zu erstellen](/help/implementing/developing/introduction/rapid-development-environments.md#snapshots) des aktuellen Status von Code und Inhalten, die zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

Anfang Juni wird die Aktualisierung auf die neuesten AIO-Plug-ins diese Funktion aktivieren.

*Durch die Verwendung der RDE-Snapshots-Beta erkennen Sie an, dass sie sich noch in der Entwicklung befindet und dass Sie sich nicht auf die ordnungsgemäße Funktionsweise der Technologie oder die Verfügbarkeit von Daten verlassen sollten. Obwohl wir diese Funktion ausführlich getestet haben, besteht eine geringe Möglichkeit, dass Ihre RDE instabil wird. In diesem Fall wird sie durch Zurücksetzen wieder in den Betriebszustand versetzt.*


#### AEM Edge-Funktionen (Beta-Programm) {#edge-functions}

[AEM Edge-](/help/implementing/developing/introduction/edge-functions.md): Ermöglicht die Ausführung von JavaScript auf CDN-Ebene, wodurch die Datenverarbeitung näher am Endbenutzer rückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge.

Häufige Anwendungsszenarien umfassen:

* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Umformatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer API-Antworten), bevor sie an den Browser gesendet werden
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden

Beta-Version für AEM-Veröffentlichungs-Bereitstellung oder Edge Delivery Services-Projekte für Live-Produktions-Sites. Wenn Sie an einer Teilnahme interessiert sind oder mehr erfahren möchten, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls.

#### Fehlerbehebung bei der Web-Stufen-Konfigurations-Pipeline (Beta-Programm) {#devagent-webtier}

Die Funktionen [Fehlerbehebung bei Pipelines](/help/ai-in-aem/agents/brand-experience/development/development.md) des Entwicklungsagenten helfen Entwicklerinnen und Entwicklern bei der effizienten Diagnose und Lösung von Problemen in AEM as a Cloud Service-Bereitstellungen. Zusätzlich zur Unterstützung von Full-Stack-Pipelines (Bereitstellung und Code-Qualität) unterstützt der Entwicklungsagent jetzt die Fehlerbehebung für die **Web Tier Config-Pipeline** als Teil eines Beta-Programms.

aem-devagent@adobe.com Um Zugriff auf die Beta-Version anzufordern, senden Sie eine E-Mail an [](mailto:aem-devagent@adobe.com). Bereits vorhandener Zugriff auf Agenten in AEM ist erforderlich.

#### Fehlerbehebung bei der Replikations-KI (Beta-Programm) {#replication-ai-troubleshooting-alpha}

Mithilfe des KI-Assistenten in der AEM-Autoreninstanz und anderen Benutzeroberflächen können Sie replikationsbezogene Probleme wie blockierte Warteschlangen beheben. Um am Beta-Programm teilzunehmen, senden Sie eine E-Mail an [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com), in der Ihr Interesse beschrieben wird.

#### Edge-Authentifizierung für Edge Delivery Services (Beta-Programm) {#edge-authentication}

Mit der Edge-Authentifizierung können Sie den Zugriff auf Edge Delivery Services-Seiten auf diejenigen beschränken, die sich bei Ihrem Identitätsanbieter (IdP) authentifiziert haben. Dies wird durch die Bereitstellung einer YAML-Konfigurationsdatei von OpenID Connect (OIDC) erreicht.

Bei Interesse senden Sie bitte eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls und allen Fragen, die Sie haben.

#### Canary-Produktionsbereitstellungen zum Testen von Code vor Annahme von Live-Traffic (Beta-Programm) {#canary-beta}

Validieren Sie einen Produktions-Build mit reinem Test-Traffic, bevor Sie ihn für Endbenutzende verfügbar machen. Senden Sie an die Produktion, leiten Sie nur den Canary-Traffic weiter (mithilfe einem speziellen Header) und überwachen Sie das Verhalten. Leiten Sie den Live-Traffic dann entweder weiter oder setzen Sie ihn zurück, ohne dass sich dies auf die Kundinnen und Kunden auswirkt.

Senden Sie eine E-Mail an [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com), um Zugriff anzufordern und Feedback mitzuteilen.

#### Erkennung und automatische Behebung von AEM-Code-Problemen über den IDE AI-Agenten (Alpha-Programm) {#ide-ai-aemcode-issues}

Java-Stack-Teams, die [KI-unterstützte Entwicklung](/help/ai-in-aem/local-development-with-ai-tools.md) in Tools wie Cursor, Claude Code, Visual Studio und IntelliJ verwenden, können jetzt weiter gehen: Eine neue IDE-Agent-Fähigkeit erkennt und behebt Probleme direkt in Ihrer AEM-Codebasis, reduziert Prüfungszyklen und behebt Probleme in der Entwicklungsphase.

Diese Funktion befindet sich in der Alpha-Phase. Sich dem Programm anschließen und Feedback mit dem Team geben unter [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com).

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
