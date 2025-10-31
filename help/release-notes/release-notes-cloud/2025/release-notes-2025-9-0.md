---
title: Versionshinweise für Version 2025.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2025.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: ed51ff8df6d1e387960e8580c6dfb543a09ef8fa
workflow-type: tm+mt
source-wordcount: '2083'
ht-degree: 89%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2025.9.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2025.9.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2023 oder 2024 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.9.0) ist der 25. September 2025. Die nächste Version mit neuen Funktionen (2025.10.0) ist für den 30. Oktober 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in der Vorabversion von Experience Manager Sites {#prerelease-sites}

Der Inhaltsmodelleditor für AEM-Inhaltsfragmente wurde modernisiert, um ihn an andere auf React Spectrum basierende Benutzeroberflächen in AEM anzupassen. Die Implementierung der Benutzeroberfläche und das Erweiterbarkeitsmodell sind jetzt mit dem Inhaltsfragmenteditor und dem universellen Editor konsistent. Der neue Modelleditor ist jetzt Standard, wenn über die neue Admin-Benutzeroberfläche des Inhaltsmodells geöffnet wird. Beim Öffnen eines Inhaltsmodells in der Touch-optimierten Benutzeroberfläche wird der Editor für die Touch-optimierte Benutzeroberfläche geöffnet und Sie können den neuen Editor ausprobieren.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#new-features-assets-view}

**Verbesserte Textformatierung mit Unterzeichenfolgen in Dynamic Media-Vorlagen**

Sie können jetzt Formatierungen auf Unterzeichenfolgen in Textebenen von Dynamic Media-Vorlagen anwenden. Ein ausgewähltes Wort oder ein ausgewählter Satzteil wird als separate Ebene behandelt, sodass Sie die Schrift, den Schriftgrad, die Farbe und mehr anpassen können. Die Ebene der Unterzeichenfolge wird parametrisiert, sodass Sie sie mithilfe der Versand-URL der Vorlage in Echtzeit aktualisieren können.

### Neue Funktionen in Dynamic Media mit OpenAPI-Funktionen {#new-features-dynamic-media-with-openapi}

**Bereitstellungs-URLs für markenspezifische und lesbare Assets**

Verbessern der Lesbarkeit von Dynamic Media mit OpenAPI-URLs durch Verwendung von Vanity-URLs in Dynamic Media mit OpenAPI. Vanity-URLs ermöglichen es, lange, systemgenerierte, schwer zu speichernde UUIDs in Asset-Bereitstellungs-URLs durch kurze, markengesteuerte IDs zu ersetzen. Dies macht Vanity-URLs kürzer, leichter zu lesen und freizugeben und ermöglicht eine bessere Abstimmung mit Ihrer Marke oder Ihren Kampagnen. Vanity-URLs werden zur Laufzeit automatisch zur ursprünglichen Asset-UUID aufgelöst, ohne vorhandene Workflows zu unterbrechen.

>[!NOTE]
>
>Diese Funktion ist nur eingeschränkt verfügbar. Siehe diesen [Artikel](/help/assets/vanity-urls.md) um zu beginnen.

### Neue Funktionen in Content Hub {#new-features-content-hub}

**Sammlungen als Favoriten markieren**

Sie können Sammlungen in Content Hub jetzt als Favoriten markieren, was das Organisieren und Abrufen erleichtert. Nach dem Hinzufügen sind Ihre Lieblingssammlungen bequem über die Registerkarte Favoriten auf der Content Hub-Startseite verfügbar.


**Sammlungen für schnellen Zugriff anheften**

Content Hub-Administratoren können jetzt Sammlungen in Content Hub anheften, um schnell darauf zugreifen zu können. Angeheftete Sammlungen werden in einem speziellen angehefteten Abschnitt auf der Startseite von Sammlungen angezeigt, was es einfacher macht, wichtige Sammlungen in Reichweite zu halten.

>[!IMPORTANT]
>
>Diese Funktionen sind als Funktionen mit begrenzter Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

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

**Workflow-Schritt „Aufrufen von Formulardatenmodell“ für SharePoint-Listenanhänge**

Der Workflow-Schritt „Aufrufen von Formulardatenmodell“ unterstützt jetzt die Verarbeitung von Workflow-seitigen Metadaten für Base64-kodierte Anhang-Arrays in auf SharePoint-Listen basierten Formulardatenmodellen. Mit dieser Verbesserung kann der Workflow-Schritt Metadaten wie Dateinamen, MIME-Typ und benutzerdefinierte Eigenschaften für jeden Anhang übergeben, speichern und abrufen. Diese Funktion ermöglicht ein umfassenderes Daten-Management und ermöglicht eine nahtlose nachgelagerte Integration. Weitere Informationen finden Sie unter [Verbesserte Unterstützung für Workflow-Schritt „Aufrufen von Formulardatenmodell“ für SharePoint-Listenanhänge](/help/forms/aem-forms-workflow-step-reference.md#invoke-form-data-model-fdm-service-step).

<!-- ### Pre-Release features in AEM Forms -->

### Neue Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

* **PDF-Vorschau im Editor für interaktive Kommunikation**

  Benutzende können PDFs mit interaktiver Kommunikation ohne Daten, mit lokalen JSON-Datendateien oder mit Daten aus einem Datenmodell in der Vorschau anzeigen, was flexible datengesteuerte Tests ermöglicht. Weitere Informationen finden Sie unter [PDF-Vorschau im Editor für interaktive Kommunikation](/help/forms/interactive-communication/pdf-preview-in-interactive-communication-editor-with-different-data-options.md).

* **Unterstützung benutzerdefinierter Schriften in der interaktiven Kommunikation**

  Mit der Funktion für benutzerdefinierte Schriften können Benutzende benutzerdefinierte oder vom Unternehmen genehmigte Schriftarten in die interaktive Kommunikation einbetten, um so eine konsistente und markenübergreifende PDF-Ausgabe auf allen Geräten und Plattformen sicherzustellen. Weitere Informationen finden Sie unter [Unterstützung benutzerdefinierter Schriften in interaktiver Kommunikation](/help/forms/interactive-communication/add-custom-fonts-to-interactive-communication-editor.md).

* **Importieren und Exportieren von interaktiver Kommunikation**

  Diese Funktion ermöglicht die Migration und Wiederverwendung interaktiver Kommunikation über verschiedene Umgebungen hinweg. Sie können jetzt interaktive Kommunikation zusammen mit den zugehörigen Fragmenten und Datenmodellen aus einer Umgebung exportieren und in eine andere importieren. Weitere Informationen finden Sie unter [Importieren und Exportieren von interaktiver Kommunikation](/help/forms/interactive-communication/import-and-export-interactive-communications.md).

* **Verbesserungen beim Regeleditor**

  Der Regeleditor unterstützt jetzt eine verbesserte Navigation und ermöglicht die Verwendung von Funktionen und mathematischen Ausdrücken in Eingabeparametern.

   * **Verbesserte Navigation mit Unterstützung der Ereignis-Payload**: Die `Navigate To`-Aktion in den Handlern für das Aufrufen von Services unterstützt jetzt `EVENT_PAYLOAD` und ermöglicht es Formularautoren, Folgeaktionen basierend auf Ereignisantworten zu konfigurieren. Diese Verbesserung bietet mehr Flexibilität beim Entwerfen von Workflows nach der Übermittlung, wodurch reibungslosere Übergänge und personalisiertere Benutzererlebnisse gewährleistet werden. Weitere Informationen finden Sie unter [Verbesserte Navigation mit Unterstützung der Ereignis-Payload](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service).

   * **Unterstützung von Funktionen und mathematischen Ausdrücken in Eingabeparametern**: Eingabeparameter unterstützen jetzt sowohl Funktionsaufrufe als auch mathematische Ausdrücke, sodass Formularautoren dynamisch berechnete Werte direkt übergeben können. Diese Verbesserung optimiert die Regelkonfigurationen, beseitigt die Notwendigkeit zusätzlicher Felder und macht Formulare anpassbarer an komplexe Logik und berechnungsgesteuerte Szenarien. Weitere Informationen finden Sie unter [Unterstützung von Funktionen und mathematischen Ausdrücken in Eingabeparametern](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters).

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
>>Senden Sie eine E-Mail an [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com), um sie in Ihren Programmen zu aktivieren.

### Neue Version von AEM Developer Tools für Eclipse {#aem-develeper-tools-for-eclipse}

Version 1.4.0 von AEM Developer Tools für Eclipse wurde veröffentlicht. Diese Version unterstützt nun Eclipse IDE 2022–12 oder höher und wurde mit der aktuellen Version getestet (2025-09). Die Tools funktionieren jetzt mit modernen Versionen des AEM-Projektarchetyps und enthalten Verbesserungen von Sling IDE Tooling 1.3.0.

Installieren Sie vom [Eclipse Marketplace](https://marketplace.eclipse.org/content/aem-developer-tools-eclipse) aus. Weitere Details finden Sie auf der [Seite zu den AEM Developer Tools](https://eclipse.adobe.com).

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

Die *Java 11-Laufzeit* ist jetzt veralte und die meisten Umgebungen wurden bereits auf die leistungsfähigere **Java 21-Laufzeit** aktualisiert.

Wenn Ihre Umgebung aufgrund nicht unterstützter Abhängigkeiten nicht aktualisiert werden konnte (siehe [Anforderungen für Java 21-Laufzeit](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), sollten Sie eine E-Mail von Adobe mit konkreten nächsten Schritten erhalten haben. Wie dort beschrieben, hat Adobe am **18. September 2025** die **Entwicklungs**- und **RDE**-Umgebungen aktualisiert, damit Sie Ihre Site und Ihre Prozesse validieren und Probleme beheben können. Die Upgrades für **Staging**- und **Produktions**-Umgebungen werden am **14. Oktober 2025** durchgeführt.

>[!NOTE]
>
>Die Laufzeitversion ist unabhängig von der Build-Version Ihres Codes. Es wird zwar empfohlen, Builds mit Java 21 durchzuführen, aber Java 11-Builds werden derzeit noch unterstützt. Ein separater Hinweis zur Abschaffung von Java 11 für Builds wird in Zukunft freigegeben.

### Durchsetzung der Konfigurationsrichtlinie für AEM-Java-Protokolle {#logconfig-policy}

Wie in den Versionshinweisen vom April erwähnt, müssen AEM-Java-Protokolle einem Standardformat entsprechen, um eine zuverlässige Überwachung in allen Kundenumgebungen sicherzustellen. Benutzerdefinierte Protokollkonfigurationen – wie etwa Änderungen an der Protokollformatierung, Ausgabedateien oder Standardprotokollebenen – werden nicht mehr unterstützt. Protokolle müssen an die Standarddateien weitergeleitet werden, und die standardmäßigen Protokollebenen für AEM-Produkt-Code müssen beibehalten werden. Ausführliche Informationen finden Sie im [Artikel zur Protokollierung](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Ab **30. Oktober** werden alle nicht unterstützten benutzerdefinierten Protokollierungsüberschreibungen ignoriert. Nach unserer Analyse ist der Großteil der Kundschaft nicht betroffen, und Adobe hat sich mit Kundinnen und Kunden in Verbindung gesetzt, deren aktuelle Konfiguration möglicherweise betroffen ist.

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

### Snapshots für schnelle Entwicklungsumgebungen (Alpha-Programm) {#rde-snapshot-program}

In Alpha unterstützen schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs) jetzt eine Funktion, um einen Snapshot des aktuellen Code- und Inhaltsstatus zu erstellen, der zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

Wenn Sie Feedback zu dieser Funktion geben möchten, senden Sie uns eine E-Mail an [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com).

### AEM-Protokollweiterleitung an weitere Ziele (Beta-Programm) {#log-forwarding-beta}

Die Protokolle können zwar von Cloud Manager heruntergeladen werden, aber viele Unternehmen ziehen es vor, diese Protokolle an ein bevorzugtes Protokollierungsziel weiterzuleiten. AEM unterstützt bereits die AEM- und CDN-Protokollweiterleitung an Azure Blob Storage, Datadog, HTTPS, Elasticsearch (und OpenSearch) und Splunk. Diese Funktion wird eigenständig konfiguriert und mithilfe der Konfigurations-Pipeline bereitgestellt.

Jetzt in der Beta-Phase können Sie AEM-Protokolle an Amazon S3, Sumo Logic, Dynatrace und Ihr eigenes New Relic-Konto (nicht das von Adobe bereitgestellte Konto) weiterleiten. Beachten Sie, dass zwar AEM-Protokolle (einschließlich Apache/Dispatcher) für diese Protokollierungsziele unterstützt werden, jedoch keine CDN-Protokolle. Schreiben Sie eine E-Mail an [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com), um Zugriff zu erhalten.

Weitere Informationen finden Sie in der [Dokumentation zur Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md).

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
