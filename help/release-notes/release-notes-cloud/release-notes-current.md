---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: f5510d83ed2ff52496fd7e83ba29010684731938
workflow-type: tm+mt
source-wordcount: '1957'
ht-degree: 47%

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

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.9.0) ist der Freitag, 25. September 2025. Die nächste Version mit neuen Funktionen (2025.10.0) ist für den Freitag, 30. Oktober 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in der Vorabversion von Experience Manager Sites {#prerelease-sites}

Der Inhaltsmodell-Editor für AEM-Inhaltsfragmente wurde modernisiert, um ihn an andere auf React Spectrum basierende Benutzeroberflächen in AEM anzupassen. Die Implementierung der Benutzeroberfläche und das Erweiterbarkeitsmodell sind jetzt mit dem Inhaltsfragment-Editor und dem universellen Editor konsistent. Der neue Modell-Editor ist jetzt standardmäßig, wenn er über die neue Admin-Benutzeroberfläche des Inhaltsmodells geöffnet wird. Beim Öffnen eines Inhaltsmodells in der Touch-optimierten Benutzeroberfläche wird der Editor für die Touch-optimierte Benutzeroberfläche geöffnet. Außerdem werden Angebote zum Testen des neuen Editors angezeigt.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#new-features-assets-view}

**Verbesserte Textformatierung mit Teilzeichenfolgen in Dynamic Media-Vorlagen**

Sie können jetzt Formatierungen auf Teilzeichenfolgen in Textebenen von Dynamic Media-Vorlagen anwenden. Ein ausgewähltes Wort oder eine ausgewählte Phrase wird als separate Ebene behandelt, sodass Sie die Schriftart, Schriftgröße, Farbe und mehr anpassen können. Die Ebene der Unterzeichenfolge wird parametrisiert, sodass Sie sie mithilfe der Versand-URL der Vorlage in Echtzeit aktualisieren können

### Neue Funktionen in Dynamic Media mit OpenAPI-Funktionen {#new-features-dynamic-media-with-openapi}

**SEO-freundliches DM mit OpenAPI-URLs**

Erstellen Sie Vanity-URLs für die Asset-Bereitstellung in DM mit OpenAPI und ersetzen Sie lange systemgenerierte UUIDs durch kurze, lesbare Kennungen. Dadurch werden Links SEO-freundlich und besser auf Ihre Marke oder Kampagnen abgestimmt. Vanity-URLs werden zur Laufzeit automatisch zur ursprünglichen Asset-UUID aufgelöst, ohne vorhandene Workflows zu unterbrechen.

>[!NOTE]
>
>Diese Funktion ist nur in begrenztem Umfang verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

<!--

### New Features in Content Hub {#new-features-content-hub}

**Mark Collections as Favourites**

You can now mark collections as Favorites in Content Hub, making it easier to organize and retrieve them. Once added, your favourite collections are conveniently available from the **Favourites** tab on the Content Hub home page.

**Pin collections for quick access**

Content Hub Administrators can now pin collections in Content Hub for quick access. Pinned collections are displayed in a dedicated **Pinned** section on the Collections home page, making it easier to keep important collections within reach.

>[!NOTE]
>
>These features are available as Limited Availability features. You can [create and submit an Adobe Customer Support case](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) to enable it for your deployment.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in Experience Manager Forms {#new-features-forms}

**Workflow-Schritt „Formulardatenmodell aufrufen“ für SharePoint-Listenanlagen**

Der Workflow-Schritt „Formulardatenmodell aufrufen“ unterstützt jetzt die Verarbeitung von Workflow-seitigen Metadaten für Base64-kodierte Anlagen-Arrays in SharePoint-Listenbasierten Formulardatenmodellen. Mit dieser Verbesserung kann der Workflow-Schritt Metadaten wie Dateinamen, MIME-Typ und benutzerdefinierte Eigenschaften für jeden Anhang übergeben, speichern und abrufen. Diese Funktion ermöglicht ein umfassenderes Daten-Management und ermöglicht eine nahtlose nachgelagerte Integration. Weitere Informationen finden Sie unter [Verbesserte Unterstützung im Workflow-Schritt „Formulardatenmodell aufrufen“ für SharePoint-Listenanhänge](/help/forms/aem-forms-workflow-step-reference.md#invoke-form-data-model-fdm-service-step).

### Vorab veröffentlichte Funktionen in AEM Forms

**Verbesserungen am Regeleditor**

Der Regeleditor unterstützt jetzt die erweiterte Navigation und ermöglicht die Verwendung von Funktionen und mathematischen Ausdrücken in Eingabeparametern.

**Verbesserte Navigation mit Unterstützung der Ereignis-Payload**

Die `Navigate To` Aktion in den Handlern zum Aufrufen von Services unterstützt jetzt `EVENT_PAYLOAD` und ermöglicht es Formularautoren, Folgeaktionen basierend auf Ereignisantworten zu konfigurieren. Diese Verbesserung bietet mehr Flexibilität beim Entwerfen von Workflows nach der Übermittlung, wodurch reibungslosere Übergänge und personalisiertere Benutzererlebnisse gewährleistet werden. Weitere Informationen finden Sie unter [Erweiterte Navigation mit Unterstützung der Ereignis-Payload](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service).

**Unterstützung von Funktionen und mathematischen Ausdrücken in Eingabeparametern**

Eingabeparameter unterstützen jetzt sowohl Funktionsaufrufe als auch mathematische Ausdrücke, sodass Formularautoren dynamisch berechnete Werte direkt übergeben können. Diese Verbesserung optimiert die Regelkonfigurationen, macht zusätzliche Felder überflüssig und Formulare anpassbarer an komplexe Logik und berechnungsgesteuerte Szenarien. Weitere Informationen finden Sie unter [Unterstützung von Funktionen und mathematischen Ausdrücken in Eingabeparametern](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters).

### Neue Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

**PDF-Vorschau im Editor für interaktive Kommunikation**

Benutzer können PDFs mit interaktiver Kommunikation ohne Daten, mit lokalen JSON-Datendateien oder mit Daten aus einem Datenmodell in der Vorschau anzeigen, was flexible datengesteuerte Tests ermöglicht. Weitere Informationen finden Sie unter [PDF-Vorschau im Editor für interaktive Kommunikation](/help/forms/interactive-communication/pdf-preview-in-interactive-communication-editor-with-different-data-options.md).

**Unterstützung benutzerdefinierter Schriftarten in der interaktiven Kommunikation**

Mit der Funktion für benutzerdefinierte Schriftarten können Benutzende benutzerdefinierte oder vom Unternehmen genehmigte Schriftarten in die interaktive Kommunikation einbetten, um so ein konsistentes und markenübergreifendes PDF-Rendering auf allen Geräten und Plattformen sicherzustellen. Weitere Informationen finden Sie unter [Unterstützung benutzerdefinierter Schriftarten in interaktiver Kommunikation](/help/forms/interactive-communication/add-custom-fonts-to-interactive-communication-editor.md).

**Importieren und Exportieren von interaktiver Kommunikation**

Diese Funktion ermöglicht die Migration und Wiederverwendung interaktiver Kommunikation über verschiedene Umgebungen hinweg. Sie können jetzt eine interaktive Kommunikation zusammen mit den zugehörigen Fragmenten und Datenmodellen aus einer Umgebung exportieren und in eine andere importieren. Weitere Informationen finden Sie unter [Interaktive Kommunikation importieren und exportieren](/help/forms/interactive-communication/import-and-export-interactive-communications.md).

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

### Neue Funktionen in der Versionsverwaltung {#new-features-release-management}

**Pausieren der automatischen Wartungsaktualisierungen**

Live-Schaltungstage, Live-Ereignisse, Spitzenumsätze - diese Momente sind unvermeidlich. [Unsere neuen Self-Service-Funktionen](/help/implementing/deploying/quiet-hours-update-free-periods.md) stoppen automatische Wartungs-Updates, wenn es darauf ankommt, damit Ihre Teams fokussiert bleiben.

* Ruhige Stunden: Blockieren Sie die automatische Wartung während der festgelegten Zeiten jeden Tag. Ideal für Arbeitszeiten, nächtliche Abläufe oder morgendliche Umschläge.
* Update-freier Zeitraum: Blockieren Sie die automatische Wartung für eine ganze Woche. Verwenden Sie ihn für Launches, Promos oder jährliche Einfrierungen.

>[!NOTE]
>
>Verfügbar als Funktion zur eingeschränkten Verfügbarkeit am 25. September.
>>Senden Sie eine E-Mail an [0}aemcs-update-free@adobe.com&quot;, um sie in Ihren Programmen aktivieren zu lassen.](mailto:aemcs-update-free@adobe.com)

### Neue Version von AEM Developer Tools for Eclipse {#aem-develeper-tools-for-eclipse}

Version 1.4.0 der AEM Developer Tools for Eclipse wurde veröffentlicht. Diese Version unterstützt nun Eclipse IDE 2022-12 oder höher und wurde mit der aktuellen Version validiert (2025-09). Die Tools funktionieren jetzt mit modernen Versionen des AEM-Projektarchetyps und enthalten Verbesserungen von Sling IDE-Tools 1.3.0.

Installieren Sie vom [Eclipse Marketplace](https://marketplace.eclipse.org/content/aem-developer-tools-eclipse) und lesen Sie die Seite [AEM Developer Tools](https://eclipse.adobe.com) für weitere Details.

### Bevorstehende Einstellung von Java-APIs {#java-api-deprecation}

Mehrere veraltete APIs wurden am 31. August zum Entfernen markiert und sollten daher nicht mehr referenziert werden. Sie erhalten Benachrichtigungen des Aktionszentrums, wenn eine veraltete API-Nutzung in Ihrem Code erkannt wird, und nach dem 13. November werden während Cloud Manager-Builds Hinweise angezeigt, die die Bedeutung der Entfernung der Nutzung unterstreichen. Ausführliche Informationen finden Sie im [Artikel zur Einstellung](/help/release-notes/deprecated-removed-features.md#aem-apis). Als Referenz sind diese APIs unten aufgeführt:

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

Die *Java 11-* ist veraltet, und die meisten Umgebungen wurden bereits auf die leistungsfähigere Java 21 **Laufzeitumgebung**.

Wenn Ihre Umgebung aufgrund nicht unterstützter Abhängigkeiten nicht aktualisiert werden konnte (siehe [Java 21-Laufzeitanforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), sollten Sie eine E-Mail von Adobe mit den nächsten Schritten erhalten haben. Wie dort beschrieben, hat Adobe am 18. **2025 Ihre** Dev **- und** RDE **-Umgebungen aktualisiert** damit Sie Ihre Site und Ihre Prozesse validieren und Probleme beheben können. Die Upgrades für **Staging** und **Produktion** werden am 14. **2025**.

>[!NOTE]
>
>Die Laufzeitversion ist von der Build-Version Ihres Codes getrennt. Obwohl das Erstellen mit Java 21 empfohlen wird, werden Java 11-Builds derzeit noch akzeptiert. Ein separater Hinweis zur Abschaffung von Java 11 für Builds wird in Zukunft freigegeben.

### Durchsetzung der Konfigurationsrichtlinie für AEM-Java-Protokolle {#logconfig-policy}

Wie in den Versionshinweisen vom April erwähnt, müssen AEM-Java-Protokolle einem Standardformat entsprechen, um eine zuverlässige Überwachung in allen Kundenumgebungen sicherzustellen. Benutzerdefinierte Protokollkonfigurationen – wie etwa Änderungen an der Protokollformatierung, Ausgabedateien oder Standardprotokollebenen – werden nicht mehr unterstützt. Protokolle müssen an die Standarddateien weitergeleitet werden, und die standardmäßigen Protokollebenen für AEM-Produkt-Code müssen beibehalten werden. Ausführliche Informationen finden Sie im [Artikel zur Protokollierung](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Ab dem **. Oktober** werden alle nicht unterstützten benutzerdefinierten Protokollierungsüberschreibungen ignoriert. Nach unserer Analyse ist der Großteil der Kundschaft nicht betroffen, und Adobe hat sich mit Kundinnen und Kunden in Verbindung gesetzt, deren aktuelle Konfiguration möglicherweise betroffen ist.

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

Mit der Edge-Authentifizierung können Sie den Zugriff auf Edge Delivery Services-Seiten auf diejenigen beschränken, die sich bei Ihrem Identitätsanbieter (IdP) authentifiziert haben. Dies wird durch die Bereitstellung einer OpenID Connect (OIDC)-YAML-Konfigurationsdatei erreicht.

Bei Interesse senden Sie bitte eine E-Mail an [](mailto:aemcs-edgecompute-feedback@adobe.com)aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls und allen Fragen, die Sie haben könnten.

<!--
### CDN Configuration for Edge Delivery Services (Beta Program) {#cdn-eds-beta}

The Adobe-Managed CDN offers flexible configuration options, as described in the [Config Pipeline article](/help/operations/config-pipeline.md#configurations). 

Now in beta, youcan deploy a config pipeline for features including CDN origin selectors, response and request transformations, CDN log forwarding and more. Please reach out to [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) with the details of your use case.

-->

### Canary-Produktionsbereitstellungen, um Code zu testen, bevor Live-Traffic akzeptiert wird (Beta-Programm) {#canary-beta}

Validieren Sie einen Produktions-Build mit reinem Test-Traffic, bevor Sie ihn für Endbenutzer verfügbar machen. Senden Sie an die Produktion, leiten Sie nur den Canary-Traffic weiter (mithilfe einer speziellen Kopfzeile) und überwachen Sie das Verhalten. Leiten Sie dann entweder den Live-Traffic weiter oder setzen Sie ihn zurück, ohne dass sich dies auf die Kunden auswirkt.

Stellen Sie Ihre Code-Versionen für die Produktion bereit, beschränken Sie sie jedoch auf internen Test-Traffic, bevor Sie entscheiden, ob Sie Live-Traffic akzeptieren oder zurücksetzen.

E-Mail [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com), um Zugriff anzufordern und Feedback zu geben.

### Snapshots für schnelle Entwicklungsumgebungen (Alpha-Programm) {#rde-snapshot-program}

In Alpha unterstützen schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs) jetzt eine Funktion, um einen Snapshot des aktuellen Code- und Inhaltsstatus zu erstellen, der zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

Wenn Sie Feedback zu dieser Funktion geben möchten, senden Sie uns eine E-Mail an [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com).

### AEM-Protokollweiterleitung an weitere Ziele (Beta-Programm) {#log-forwarding-beta}

Die Protokolle können zwar von Cloud Manager heruntergeladen werden, aber viele Unternehmen ziehen es vor, diese Protokolle an ein bevorzugtes Protokollierungsziel weiterzuleiten. AEM unterstützt bereits die AEM- und CDN-Protokollweiterleitung an Azure Blob Storage, Datadog, HTTPS, Elasticsearch (und OpenSearch) und Splunk. Diese Funktion wird eigenständig konfiguriert und mithilfe der Konfigurations-Pipeline bereitgestellt.

Jetzt in der Beta-Phase können Sie AEM-Protokolle an Amazon S3, Sumo Logic, Dynatrace und Ihr eigenes New Relic-Konto (nicht das von Adobe bereitgestellte Konto) weiterleiten. Beachten Sie, dass zwar AEM-Protokolle (einschließlich Apache/Dispatcher) für diese Protokollierungsziele unterstützt werden, jedoch keine CDN-Protokolle. Schreiben Sie eine E-Mail an [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com), um Zugriff zu erhalten.

Weitere Informationen finden Sie in der [Dokumentation zur Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md).

### Erweiterte Anwendungsleistungsüberwachung (APM) (Alpha-Programm) {#apm-alpha}

Zur Beobachtung unterstützt AEM Cloud Service derzeit von Adobe bereitgestellte [New Relic One](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) und kundenverwaltete [Dynatrace](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace). Wenn wir Unterstützung für zusätzliche APM-Optionen prüfen, senden Sie uns bitte eine E-Mail an [](mailto:aemcs-apm-beta@adobe.com)aemcs-apm-beta@adobe.com) mit Ihrem bevorzugten Anbieter oder Ihrer bevorzugten Technologie sowie mit Anwendungsfällen.


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
