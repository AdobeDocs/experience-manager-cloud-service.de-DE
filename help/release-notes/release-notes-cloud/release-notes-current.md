---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: cb4764709a86ae2acb33a10dc9a53126804ee7ec
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 67%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.10.0) ist der Freitag, 30. Oktober 2025. Die nächste Version (2025.11.0) ist für den Freitag, 20. November 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#new-sites}

* [Launches für Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md): Inhaltsautoren können jetzt zukünftige Varianten strukturierter Inhalte mithilfe von Launches für Inhaltsfragmente erstellen und planen. Die neue Inhaltsfragmentkonsole ermöglicht das Erstellen, Bearbeiten, Verwalten und Planen von Inhaltsfragment-Launches als Verzweigungen für zukünftige Inhalte, die mit der Quellverzweigung synchronisiert werden können. Eine neue Vergleichsansicht bietet einen klaren Überblick über alle Inhaltsänderungen, bevor ein Launch zur zukünftigen Veröffentlichung übergeben wird.

* Der [Inhaltsmodell-Editor für AEM](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)Inhaltsfragmente wurde modernisiert, um ihn an andere auf React-Spektrum basierende Benutzeroberflächen in AEM anzupassen. Die Implementierung der Benutzeroberfläche und das Erweiterbarkeitsmodell sind jetzt mit dem Inhaltsfragmenteditor und dem universellen Editor konsistent. Der neue Modelleditor ist jetzt Standard, wenn über die neue Admin-Benutzeroberfläche des Inhaltsmodells geöffnet wird. Beim Öffnen eines Inhaltsmodells in der Touch-optimierten Benutzeroberfläche wird der Editor für die Touch-optimierte Benutzeroberfläche geöffnet und Sie können den neuen Editor ausprobieren.

<!--

### New Features in Content Hub {#new-features-content-hub}

**Mark Collections as Favourites**

You can now mark collections as Favorites in Content Hub, making it easier to organize and retrieve them. Once added, your favourite collections are conveniently available from the **Favourites** tab on the Content Hub home page.

**Pin collections for quick access**

Content Hub Administrators can now pin collections in Content Hub for quick access. Pinned collections are displayed in a dedicated **Pinned** section on the Collections home page, making it easier to keep important collections within reach.

>[!NOTE]
>
>These features are available as Limited Availability features. You can [create and submit an Adobe Customer Support case](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) to enable it for your deployment.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in Experience Manager Forms {#new-features-forms}

**Universeller Editor für adaptive Formulare und Formularfragmente**

Der universelle Editor bietet jetzt ein einheitliches Authoring-Erlebnis zum Erstellen adaptiver Forms und wiederverwendbarer Formularfragmente. Autorinnen und Autoren können Formulare visuell entwerfen, Übermittlungsaktionen konfigurieren und die reCAPTCHA-Validierung in eine intuitive WYSIWYG-Umgebung integrieren.

<!-- ### Pre-Release features in AEM Forms 

**Rule Editor Enhancements**

The Rule Editor now supports enhanced navigation and allows use of function and mathematical expressions in input parameters.

**Enhanced Navigation with Event Payload Support**
 
The `Navigate To` action in the Invoke Service handlers now supports `EVENT_PAYLOAD`, enabling form authors to configure follow-up actions based on event responses. This enhancement offers greater flexibility in designing post-submission workflows, ensuring smoother transitions and more personalized user experiences. For more information, see [Enhanced Navigation with Event Payload Support](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service).

**Function and Mathematical Expression Support in Input Parameters**
 
Input parameters now support both function calls and mathematical expressions, enabling form authors to pass dynamically computed values directly. This enhancement streamlines rule configurations, eliminates the need for extra fields, and makes forms more adaptable to complex logic and calculation-driven scenarios. For more information, see [Function and Mathematical Expression Support in Input Parameters](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters). -->

### Neue Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Verbesserungen der interaktiven Kommunikation

##### Vorlagensperrung

Sperren Sie Inhalte und Layout-Elemente in Vorlagen, um die Markenintegrität zu wahren und unbefugte Änderungen zu verhindern. Dadurch wird die Konsistenz des Designs in der gesamten Kommunikation sichergestellt.

##### Unterstützung von Inhaltsüberläufen

Einführung der Option „Seitenumbrüche innerhalb von Inhalten zulassen“ für Fluss-Layouts. Diese Verbesserung ermöglicht eine reibungslose mehrseitige Bearbeitung und eine bessere Textverwaltung für komplexe Dokumente.

##### XDP-Dateibearbeitung

Der Editor für interaktive Kommunikation unterstützt jetzt die XDP-Bearbeitung, einschließlich der Fragmentintegration. Sie können jetzt XDP-Dateien in einem Browser bearbeiten, anstatt in Forms Designer, das nur auf dem Microsoft Windows-Desktop ausgeführt wird.

##### Dynamische Seitennummerierung

Auf Musterseiten wird automatisch „Seite ##&quot; angezeigt, um eine klare, konsistente Paginierung über mehrseitige Dokumente hinweg zu gewährleisten.

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

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen für die Versionsverwaltung {#new-features-release-management}

**Pausieren der automatischen Wartungs-Updates**

Tage, an denen die Live-Schaltung geschieht, Live-Ereignisse stattfinden oder Spitzenumsätze erzielt werden – in diesen Momenten muss alles funktionieren. [Unsere neuen Self-Service-Funktionen](/help/implementing/deploying/quiet-hours-update-free-periods.md) stoppen automatische Wartungs-Updates, wenn dies notwendig ist, damit Ihre Teams fokussiert bleiben.

* Ruhezeiten: Blockieren Sie die automatische Wartung während jeden Tag während festgelegter Zeiten. Ideal für Arbeitszeiten, nächtliche Ausführungen oder morgendliche Umstellungen.
* Update-freier Zeitraum: Blockieren Sie die automatische Wartung für eine ganze Woche. Verwenden Sie dies für Launches, Promos oder jährliche Pausen.

>[!NOTE]
>
>Verfügbar als Funktion mit eingeschränkter Verfügbarkeit am 25. September.
>Senden Sie eine E-Mail an [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com), um sie in Ihren Programmen zu aktivieren.

### AEM-Protokollweiterleitung an weitere Ziele {#log-forwarding}

Es ist jetzt möglich, AEM-Protokolle an Amazon S3, Sumo Logic, Dynatrace und Ihr eigenes New Relic-Konto (nicht das von Adobe bereitgestellte Konto) weiterzuleiten. Beachten Sie, dass AEM-Protokolle (einschließlich Apache/Dispatcher) für diese Protokollierungsziele unterstützt werden, jedoch keine CDN-Protokolle.

Siehe den vollständigen Satz von [unterstützten Protokollweiterleitungszielen](/help/implementing/developing/introduction/log-forwarding.md).

### Pipeline für Edge Delivery Services konfigurieren {#config-pipeline-eds}

Konfigurations-Pipelines werden jetzt für Sites unterstützt, die mit Edge Delivery Services erstellt wurden, wodurch diese Funktion über die bloße Bereitstellung von AEM Author und AEM Publish hinausgeht. Sie können Konfigurations-Pipelines verwenden, um Einstellungen wie die CDN-Konfiguration zu verwalten, einschließlich Traffic-Filterregeln und Ursprungsauswahlelementen. Siehe [Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

Konfigurations-Pipelines für Edge Delivery unterstützen über Cloud Manager-Pipeline-Variablen auch Geheimnisse.

Siehe [Hinzufügen einer Edge Delivery-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).

### Bevorstehende Einstellung von Java-APIs {#java-api-deprecation}

Verschiedene veraltete APIs wurden für die Einstellung am 31. August vorgemerkt und sollten daher nicht mehr referenziert werden. Sie erhalten Benachrichtigungen des Aktionszentrums, wenn die Nutzung einer veralteten API in Ihrem Code erkannt wird, und nach dem 13. November werden während Cloud Manager-Builds Benachrichtigungen angezeigt, die zum Beenden der Nutzung auffordern. Ausführliche Informationen finden Sie im [Artikel zur Einstellung](/help/release-notes/deprecated-removed-features.md#aem-apis). Als Referenz sind diese APIs unten aufgeführt:

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

### Abschaffung der Java 11-Laufzeit {#java11-runtime-deprecation}

Adobe hat **Staging** und **Produktion** Umgebungen am 14. Oktober **2025 auf die leistungsfähigere Java 21 Runtime** aktualisiert. Ab Ende Januar funktionieren weder die AEM Cloud Service SDK noch Cloud-Umgebungen mit Java 11 Runtime.

>[!NOTE]
>
> Um die neuesten Leistungsoptimierungen und Sprachverbesserungen zu nutzen, wird empfohlen, mit Java 17 oder Java 21 (bevorzugt) zu erstellen. Das Erstellen mit Java 8 und Java 11 wird derzeit weiterhin unterstützt, wird aber in einer kommenden Version eingestellt. Vor der Einstellung wird eine separate Mitteilung veröffentlicht. Siehe den *Build-Zeitanforderungen* Abschnitt [dieses Artikels](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).
>

### Durchsetzung der Konfigurationsrichtlinie für AEM-Java-Protokolle {#logconfig-policy}

Wie in den Versionshinweisen vom April erwähnt, müssen AEM-Java-Protokolle einem Standardformat entsprechen, um eine zuverlässige Überwachung in allen Kundenumgebungen sicherzustellen. Benutzerdefinierte Protokollkonfigurationen – wie etwa Änderungen an der Protokollformatierung, Ausgabedateien oder Standardprotokollebenen – werden nicht mehr unterstützt. Protokolle müssen an die Standarddateien weitergeleitet werden, und die standardmäßigen Protokollebenen für AEM-Produkt-Code müssen beibehalten werden. Ausführliche Informationen finden Sie im [Artikel zur Protokollierung](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Ab dem **. November** werden alle nicht unterstützten benutzerdefinierten Protokollierungsüberschreibungen ignoriert. Nach unserer Analyse ist der Großteil der Kundschaft nicht betroffen, und Adobe hat sich mit Kundinnen und Kunden in Verbindung gesetzt, deren aktuelle Konfiguration möglicherweise betroffen ist.

Bitte überprüfen und aktualisieren Sie alle nachgelagerten Prozesse, die auf einem benutzerdefinierten Protokollierungsverhalten basieren. Zum Beispiel:

* Wenn Ihr Protokollweiterleitungssystem ein benutzerdefiniertes Protokollformat erwartet, müssen Sie möglicherweise Ihre Aufnahmeregeln anpassen.
* Wenn Sie zuvor die Ausführlichkeit des Protokolls durch Ändern der Protokollebenen reduziert haben, beachten Sie, dass eine Rückkehr zu den Standardebenen das Protokollvolumen erhöhen kann.

### Edge-Datenverarbeitung (Beta-Programm) {#edge-computing}

Mit der Edge-Datenverarbeitung können Sie JavaScript auf CDN-Ebene ausführen, wodurch die Datenverarbeitung näher an die Endbenutzenden heranrückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge.

Häufige Anwendungsszenarien umfassen:

* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Umformatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer API-Antworten), bevor sie an den Browser gesendet werden
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden
* Bereitstellen eines MCP-Servers für LLMs wie ChatGPT und Claude für den Zugriff auf benutzerdefinierte Tools

Wir haben nur eine begrenzte Anzahl von Möglichkeiten für die AEM-Veröffentlichungsbereitstellung oder Edge Delivery Services-Projekte für Live-Produktions-Sites. Wenn Sie an einer Teilnahme interessiert sind oder mehr erfahren möchten, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls.

### Edge-Authentifizierung für Edge Delivery Services (Beta-Programm) {#edge-authentication}

Mit der Edge-Authentifizierung können Sie den Zugriff auf Edge Delivery Services-Seiten auf diejenigen beschränken, die sich bei Ihrem Identitätsanbieter (IdP) authentifiziert haben. Dies wird durch die Bereitstellung einer YAML-Konfigurationsdatei von OpenID Connect (OIDC) erreicht.

Bei Interesse senden Sie bitte eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls und allen Fragen, die Sie haben.

<!--
### CDN Configuration for Edge Delivery Services (Beta Program) {#cdn-eds-beta}

The Adobe-Managed CDN offers flexible configuration options, as described in the [Config Pipeline article](/help/operations/config-pipeline.md#configurations). 

Now in beta, youcan deploy a config pipeline for features including CDN origin selectors, response and request transformations, CDN log forwarding and more. Please reach out to [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) with the details of your use case.

-->

### Canary-Produktionsbereitstellungen zum Testen von Code vor Annahme von Live-Traffic (Beta-Programm) {#canary-beta}

Validieren Sie einen Produktions-Build mit reinem Test-Traffic, bevor Sie ihn für Endbenutzende verfügbar machen. Senden Sie an die Produktion, leiten Sie nur den Canary-Traffic weiter (mithilfe einem speziellen Header) und überwachen Sie das Verhalten. Leiten Sie den Live-Traffic dann entweder weiter oder setzen Sie ihn zurück, ohne dass sich dies auf die Kundinnen und Kunden auswirkt.

Stellen Sie Ihre Code-Versionen für die Produktion bereit, beschränken Sie sie jedoch auf internen Test-Traffic, bevor Sie entscheiden, ob Sie Live-Traffic annehmen oder zurücksetzen.

Senden Sie eine E-Mail an [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com), um Zugriff anzufordern und Feedback mitzuteilen.


### KI-Antworten - Intelligentere, kontextbezogene Antworten für AEM Sites (Beta-Programm) {#ai-answers-beta}

Mit KI-Antworten erhalten Ihre Besucher eine neue Möglichkeit, mit Ihren Inhalten zu interagieren. Basierend auf der RAG-Technologie (Retrieval-Augmented Generation) nutzt diese Lösung Ihre von AEM verwalteten Daten, um direkt in Ihren digitalen Erlebnissen präzise, markenkonsistente Antworten bereitzustellen.

Im Rahmen dieser Beta-Version können Sie KI-Antworten in Ihrer AEM Cloud Service-Umgebung sicher untersuchen. Mit diesem Ansatz können Sie die Leistung, Genauigkeit und das Gesamterlebnis überprüfen, bevor Sie ihn für Ihre Live-Zielgruppe verfügbar machen. Nach der Validierung können Sie Ihr KI-Antworterlebnis zur vollständigen Produktion weiterleiten.

Um den Beta-Zugriff anzufordern oder Ihr Feedback zu geben, kontaktieren Sie [feedback-ai-answers@adobe.com](mailto:feedback-ai-answers@adobe.com).


### Snapshots für schnelle Entwicklungsumgebungen (Alpha-Programm) {#rde-snapshot-program}

In Alpha unterstützen schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs) jetzt eine Funktion, um einen Snapshot des aktuellen Code- und Inhaltsstatus zu erstellen, der zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

Wenn Sie Feedback zu dieser Funktion geben möchten, senden Sie uns eine E-Mail an [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com).

### Erweiterte Leistungsüberwachung von Anwendungen (APM) (Alpha-Programm) {#apm-alpha}

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
