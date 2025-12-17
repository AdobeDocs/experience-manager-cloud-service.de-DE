---
title: Versionshinweise für Version 2025.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2025.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
exl-id: b1d25db0-d4a8-4663-b7fe-2d7381e12567
source-git-commit: 76ccdf13f56d7020ef266bc54bebbcc6eff1067d
workflow-type: tm+mt
source-wordcount: '2273'
ht-degree: 96%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2025.7.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2025.7.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2023 oder 2024 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.7.0) ist der 7. August 2025. Die nächste Version (2025.8.0) ist für den 28. August 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440929?captions=ger&quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#enhancements-sites}

* Sie können jetzt Inhaltsfragmente mit referenzierten Fragmenten (untergeordneten Elementen) in einem einzigen Vorgang kopieren. Dies ermöglicht die Wiederverwendung vorhandener Inhaltsfragmentstrukturen für die Erstellung neuer Inhalte.
* In der Admin-Benutzeroberfläche von Inhaltsfragmenten können Sie jetzt den Workflow-Status für Inhaltsfragmente mit detaillierten Informationen zu vergangenen und derzeit laufenden Workflows für ein ausgewähltes Fragment anzeigen.
* Beim Umbenennen oder Verschieben einer Live Copy-Quellseite wird jetzt die erneute Veröffentlichung einer entsprechend umbenannten oder verschobenen Live Copy-Seite ausgelöst.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Hinzufügen von Formen zu Dynamic Media-Vorlagen**

Sie können jetzt in Experience Manager Assets [Formebenen zu Dynamic Media-Vorlagen hinzufügen](/help/assets/dynamic-media/dynamic-media-templates.md#add-shapes-to-the-canvas). Ähnlich wie Bild- und Textebenen unterstützen Formebenen Parameter für Echtzeit-Updates über die Vorlagen-URL. Sie können auch Links mit Aktionsaufrufen (CTA-Links) zu Formen in Ihre Vorlagen aufnehmen.

![Hinzufügen von Formen zu Dynamic Media-Vorlagen](/help/assets/assets/enable-uniform-radius-shape.png)

**Verbesserungen von KI-generierten Metadaten**

Mit AEM können Sie auf der Seite „Asset-Suche“ jetzt [die Anzeige von Asset-Titeln in der Karten- oder Listenansicht konfigurieren](/help/assets/smart-tags.md#configure-ai-generated-titles). Sie können wahlweise den von Ihnen definierten Asset-Titel oder den von der KI generierten Titel anzeigen oder den KI-generierten Titel nur verwenden, wenn es noch keinen Titel für das Asset gibt.

![Konfigurieren von KI-generierten Titeln](/help/assets/assets/configure-title-ai-generated.png)

Sie können jetzt auch KI-generierte Metadaten auf Ordnerebene deaktivieren.

### Neue Funktionen in Content Hub {#new-features-content-hub}

**Verbesserte Branding-Flexibilität in Content Hub**

Aufbauend auf vorhandenen Personalisierungsfunktionen ermöglicht Content Hub Admins jetzt die weitere Anpassung ihrer Bereitstellung, indem sie benutzerdefinierte Logobilder hinzufügen. Die Unterstützung des TIFF-Dateiformats wurde sowohl für Banner- als auch für Logogbilder hinzugefügt, was die Design-Flexibilität erhöht.

**Intelligentere Freigabe mit benannten Links**

Sie können jetzt beim Generieren eines freigegebenen Links einen Titel hinzufügen – sowohl in der Asset-Detailansicht als auch nach der Auswahl eines oder mehrerer Assets. Auf diese Weise können die Personen, die den Link bekommen, den Zweck jedes Links leicht identifizieren, insbesondere, wenn sie mehrere freigegebene Assets erhalten.

![Privater und öffentlicher Link](/help/assets/assets/shared-link-for-assets.png)

**Verbesserte Filternavigation**

Content Hub enthält jetzt in Filtern die Option **Alle anzeigen**, mit der Benutzende alle verfügbaren Facetten zusammen mit der Asset-Anzahl im Zusammenhang mit der aktuellen Einschränkung auf bis zu zehn Facetten anzeigen können. Verbesserte Such- und Sortierfunktionen in jedem Filter erleichtern die effizientere Erkennung und Verwaltung von Assets.

### AEM-Desktop-Anwendung Version 3.0.0 {#desktop-app-release-3.0.0}

Profitieren Sie von dem automatisierten Hochladen neuer Dateien und Ordner, erweiterten Dateivorgängen, einer intelligenteren Asset-Erkennung und einer nahtlosen Integration in AEM, wodurch das Content Management schneller, klarer und intuitiver wird.

Eine vollständige Liste der Funktionen finden Sie unter [Versionshinweise zur Desktop-App](https://experienceleague.adobe.com/de/docs/experience-manager-desktop-app/using/release-notes).

### Neue Funktionen in Dynamic Media mit OpenAPI-Funktionen {#new-features-dynamic-media-with-openapi}

**Vorschau von Assets vor der Veröffentlichung**

[!DNL Dynamic Media with OpenAPI capabilities] können jetzt Assets direkt in [!DNL AEM Sites] Autorenseiten in der Vorschau anzeigen, bevor sie sie öffentlich verfügbar machen. Geben Sie Vorschauseiten für Projektbeteiligte frei, um Feedback zur visuellen Qualität und kontextuellen Anpassung zu erhalten. Während des Überprüfungszyklus können Sie mehrere Asset-Versionen erstellen und verwalten, bevor Sie sie zur Veröffentlichung fertigstellen.

**Verbesserte intelligente Bildbearbeitung für OpenAPI-Bildanfragen**

Alle OpenAPI-Bildanfragen nutzen jetzt uneingeschränkt die intelligente Bildbearbeitung mit automatischer Promotion und Fallback-Logik. Diese Verbesserung optimiert Bilder basierend auf Geräte- und Netzwerkbedingungen, sorgt für schnellere Seitenladevorgänge und verringert die Bandbreitennutzung – ohne Abstriche bei der visuellen Qualität.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in AEM Forms {#forms-new-features}

**Universeller Editor für adaptive Formulare und Formularfragmente**

Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) unterstützt jetzt die Erstellung von adaptiven Formularen und von wiederverwendbaren Formularfragmenten. Autorinnen und Autoren können in einer vereinfachten WYSIWYG-Authoring-Umgebung Formulare visuell erstellen, Übermittlungsaktionen konfigurieren und eine reCAPTCHA-Validierung hinzufügen. Diese Funktion beschleunigt die Erstellung von Formularen, erhöht die Konsistenz und verbessert den Schutz vor Spam und automatisiertem Missbrauch.

![Universeller Editor](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center}


**Formularübermittlungsdienst für Edge Delivery Services-Formulare**

Der [Formularübermittlungsdienst](/help/forms/forms-submission-service.md). ermöglicht die nahtlose Speicherung von Daten aus übermittelten adaptiven Formularen direkt auf gängigen Kalkulationstabellen-Plattformen wie Google Sheets, Microsoft OneDrive oder SharePoint. Diese Integration optimiert das Daten-Management durch die Möglichkeit der direkten Übermittlung von Formulardaten an die von Ihnen gewählte Tabelle, wodurch die manuelle Datenübertragung entfällt und Fehler reduziert werden.

Die wichtigsten Vorteile sind:

* **Direkte Integration:** Sie können Ihre Formulare so konfigurieren, dass die Daten direkt an eine festgelegte Kalkulationstabelle übermittelt werden.
* **Benutzerdefinierte Datenzuordnung:** Sie können Formularfelder den entsprechenden Spalten in der Tabellenkalkulation zuordnen, um die Datenspeicherung zu organisieren.
* **Zugriffskontrolle:** Mit vorhandenen Tabellenberechtigungen können Sie verwalten, wer auf übermittelte Daten zugreifen oder sie bearbeiten kann.

**Generieren und Synchronisieren von AFP-Ausgabedarstellungen aus adaptiven Formularen**

Das [AFP Output Sync-API](/help/forms/document-generation-afp-api.md) ermöglicht es Administratorinnen und Administratoren sowie Benutzerinnen und Benutzern, aus adaptiven Formularen AFP-Ausgaben (Advanced Function Presentation) zu generieren und die Ausgaben mit externen Systemen oder Speicherorten zu synchronisieren. AFP ist ein leistungsstarkes, für das Drucken optimiertes Dokumentformat, das häufig in großen Unternehmensumgebungen zum Einsatz kommt.

<!-- ### New pre-release features in AEM Forms {#forms-new-pre-release-features}

**Enhancements in Rule Editor**

* The `validate` method in the function list now supports validation at the panel, field, and form levels.
* Client-side custom function parsing now supports ES10+ JavaScript features and static imports.
* The button to download Document of Record (DoR) is now available as an out-of-the-box (OOTB) option in the rule editor.
* Rules now support the use of dynamic variables.
* Custom event-based rules are now supported.
* Repeatable panel rules are now executed based on context, rather than only on the last panel instance.
* Rules can now be triggered based on query parameters, UTM parameters, and browser parameters.
* Form-specific custom function scripts are now supported for Adaptive Forms in Edge Delivery Services.

 -->

### Neue Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).


<!-- **Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

**Regel-Editor für den Editor für interaktive Kommunikation**

In einer intuitiven Point-and-Click-Oberfläche können Sie dynamische, datengesteuerte Aktionen direkt in Ihren Dokumenten erstellen. Sie können bedingte Logik einfach definieren, Workflows automatisieren und Inhalte personalisieren, ohne programmieren zu müssen.

**AEM Forms-Strukturvorlagen-CLI für benutzerdefinierte Komponenten**

>[!VIDEO](https://video.tv.adobe.com/v/3470514/aem-forms scaffolding-aem-custom component generator-aem-forms cli-aem-forms custom component-aem-forms development tool)

Beschleunigen Sie die AEM Forms Edge Delivery Services-Entwicklung mit diesem CLI-Tool. Sie können den Code und die Anbindungen, die für den Beginn der Entwicklung von benutzerdefinierten Komponenten erforderlich sind, ohne Boilerplates und großen Aufwand sofort erzeugen.

**API-Integrationstool für dynamische Formulardaten**

Mit dem API-Integrations-Tool können Formularautoren dynamische, intelligente Formulare erstellen, mit denen basierend auf den Aktionen der Benutzenden Daten automatisch von externen REST-APIs abgerufen und ausgefüllt werden. Durch diese No-Code-Integrationsfunktion werden statische Formulare zu responsiven Datenerfassungsschnittstellen.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Knotenansicht für die Berechtigungsverwaltung {#node-view}

AEM führt die Berechtigungsverwaltung für die Knotenansicht ein. Die Hauptfunktionalität bleibt mit der klassischen Benutzeroberfläche identisch, ist jedoch benutzerfreundlicher und effizienter. Weitere Informationen finden Sie im [spezifischen Artikel](/help/security/touch-ui-principal-view.md).

### Aktualisierter Prozess zur Abschaffung {#updated-deprecation-process}

Adobe überprüft regelmäßig Funktionen, Bibliotheken, APIs und Konfigurationen, um sicherzustellen, dass sie den Leistungs-, Sicherheits- und Wertstandards entsprechen. Wenn Funktionen diese Standards nicht mehr erfüllen, werden sie als veraltet gekennzeichnet, und ihre Verwendung muss bis zu einem bestimmten Entfernungsdatum eingestellt werden. Bis zu diesem Datum erinnert Adobe die Kundinnen und Kunden mit E-Mail-Benachrichtigungen und Aktionen, die in Cloud Manager durchgeführt werden müssen, bevor sie mit neuen Builds fortfahren oder welche bereitstellen. Wenn die erforderlichen Maßnahmen nicht ergriffen werden, kann es passieren, dass ein Upgrade auf neue Versionen von AEM nicht möglich ist, was sich auf Sicherheit, Leistung, Zuverlässigkeit und Verfügbarkeit auswirken kann.

Weitere Informationen finden Sie im Artikel zur [Abschaffung](/help/release-notes/deprecated-removed-features.md).

#### Veraltete Java-APIs und OSGi-Konfigurationen, deren Entfernungsdatum sich nähert {#deprecated-near-removals}

Erweitern Sie die unten stehende Liste, um die veralteten APIs und OSGi-Konfigurationen anzuzeigen, die nicht mehr verwendet werden dürfen. Ausführliche Informationen, einschließlich der Timelines für die Entfernung, finden Sie im Artikel zur Abschaffung.

<details>
  <summary>Erweitern Sie die Liste, um die veralteten Versionen anzuzeigen</summary>

Jav-APIs:

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

OSGi-Eigenschaften:

* `org.apache.sling.commons.log.LogManager` (alle Eigenschaften)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)

</details>

### Abschaffung der Java 11-Laufzeit {#java11-runtime-deprecation}

Die *Java 11 Runtime* ist jetzt veraltet, und die meisten Umgebungen wurden bereits auf die leistungsfähigere **Java 21 Runtime** aktualisiert.

Wenn Ihre Umgebung aufgrund nicht unterstützter Abhängigkeiten nicht aktualisiert werden konnte (siehe [Java 21-Laufzeitanforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), sollten Sie eine E-Mail von Adobe mit konkreten nächsten Schritten erhalten haben. Bitte stellen Sie sicher, dass alle erforderlichen Aktualisierungen bis zum **28. August 2025** abgeschlossen sind, damit Ihre Umgebung unterbrechungsfrei aktualisiert werden kann.

Hinweis: Die Laufzeitversion ist von der Build-Version Ihres Codes getrennt. Es wird zwar empfohlen, Builds mit Java 21 durchzuführen, aber Java 11-Builds werden derzeit noch unterstützt. Ein separater Hinweis zur Abschaffung von Java 11 für Builds wird in Zukunft freigegeben.

### Durchsetzung der Konfigurationsrichtlinie für AEM-Java-Protokolle {#logconfig-policy}

Wie in den Versionshinweisen vom April erwähnt, müssen AEM-Java-Protokolle einem Standardformat entsprechen, um eine zuverlässige Überwachung in allen Kundenumgebungen sicherzustellen. Benutzerdefinierte Protokollkonfigurationen – wie etwa Änderungen an der Protokollformatierung, Ausgabedateien oder Standardprotokollebenen – werden nicht mehr unterstützt. Protokolle müssen an die Standarddateien weitergeleitet werden, und die standardmäßigen Protokollebenen für AEM-Produkt-Code müssen beibehalten werden. Ausführliche Informationen finden Sie im [Artikel zur Protokollierung](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Ab **Ende August** werden alle nicht unterstützten benutzerdefinierten Protokollierungsüberschreibungen ignoriert. Nach unserer Analyse ist der Großteil der Kundschaft nicht betroffen, und Adobe hat sich mit Kundinnen und Kunden in Verbindung gesetzt, deren aktuelle Konfiguration möglicherweise betroffen ist.

Bitte überprüfen und aktualisieren Sie alle nachgelagerten Prozesse, die auf einem benutzerdefinierten Protokollierungsverhalten basieren. Zum Beispiel:

* Wenn Ihr Protokollweiterleitungssystem ein benutzerdefiniertes Protokollformat erwartet, müssen Sie möglicherweise Ihre Aufnahmeregeln anpassen.
* Wenn Sie zuvor die Ausführlichkeit des Protokolls durch Ändern der Protokollebenen reduziert haben, beachten Sie, dass eine Rückkehr zu den Standardebenen das Protokollvolumen erhöhen kann.

### Standardmäßige Bereinigung älterer Versionen und Auditprotokolle {#mt-defaults}

Derzeit sind die zugehörigen *Bereinigungs-Wartungsaufgaben* in Inhaltsversionen und Auditprotokollen standardmäßig deaktiviert. Daher werden keine Daten entfernt, außer dies ist explizit konfiguriert.

Um die Repository-Leistung zu optimieren, wird die Bereinigung jedoch standardmäßig zu einem späteren angekündigten Datum aktiviert.

Weitere Details finden Sie im [Artikel zu Wartungsaufgaben](/help/operations/maintenance.md#defaults).

#### Inhaltsversionen {#mt-content}

* **Neue Umgebungen** (erstellt nach einem bevorstehenden Datum, das später mitgeteilt wird):
   * Versionen, die älter als 30 Tage sind, werden regelmäßig gelöscht.
   * Die letzten fünf Versionen der letzten 30 Tage werden zusammen mit der neuesten Version und der aktuellen Version unabhängig von deren Alter beibehalten.

* **Vorhandene Umgebungen** (vor diesem bevorstehenden Datum erstellt):
   * Versionen, die älter als 7 Jahre sind, werden regelmäßig gelöscht.
   * Alle Versionen der letzten 7 Jahre werden beibehalten.
   * Dieser hohe Standardschwellenwert verhindert ein unbeabsichtigtes Entfernen aktueller Daten. Es wird jedoch empfohlen, niedrigere Werte zu konfigurieren, um die Repository-Leistung zu optimieren.

* Sie können diese Standardwerte über die YAML-Konfiguration ändern, die über die Konfigurations-Pipeline bereitgestellt wird.

#### Auditprotokoll {#mt-auditlogs}

* **Neue Umgebungen** (erstellt nach einem bevorstehenden Datum, das separat kommuniziert wird):
   * Replikations-, DAM- und Seiten-Audit-Protokolle, die älter als sieben Tage sind, werden regelmäßig gelöscht.
   * Alle Ereignisse werden standardmäßig protokolliert.

* **Vorhandene Umgebungen** (vor diesem bevorstehenden Datum erstellt):
   * Replikations-, DAM- und Seiten-Auditprotokolle, die älter als sieben Jahre sind, werden regelmäßig gelöscht.
   * Alle Ereignisse werden standardmäßig protokolliert.
   * Dieser hohe Standardschwellenwert verhindert ein unbeabsichtigtes Entfernen aktueller Daten. Es wird jedoch empfohlen, niedrigere Werte zu konfigurieren, um die Repository-Leistung zu optimieren.

* Sie können diese Standardwerte über die YAML-Konfiguration ändern, die über die Konfigurations-Pipeline bereitgestellt wird.

### Edge-Datenverarbeitung (Alpha-Programm) {#edge-computing}

Mit der Edge-Datenverarbeitung können Sie JavaScript auf CDN-Ebene ausführen, wodurch die Datenverarbeitung näher an die Endbenutzenden heranrückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge.

Häufige Anwendungsszenarien umfassen:

* Authentifizieren von Benutzenden bei einem Identitätsanbieter, bevor Zugriff auf Inhalte gewährt wird
* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Umformatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer API-Antworten), bevor sie an den Browser gesendet werden
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden
* Bereitstellen eines MCP-Servers für LLMs wie ChatGPT und Claude für den Zugriff auf benutzerdefinierte Tools

Wir haben nur eine begrenzte Anzahl von Möglichkeiten für die AEM-Veröffentlichungsbereitstellung oder Edge Delivery Services-Projekte für Live-Produktions-Sites. Wenn Sie an einer Teilnahme interessiert sind oder mehr erfahren möchten, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls.

### CDN-Konfiguration für Edge Delivery Services (Beta-Programm) {#cdn-eds-beta}

Das von Adobe verwaltete CDN bietet flexible Konfigurationsoptionen, wie im Artikel zu [Konfigurations-Pipelines](/help/operations/config-pipeline.md#configurations) beschrieben.

Stellen Sie jetzt in der Beta-Phase eine Konfigurations-Pipeline für Funktionen bereit, darunter CDN-Ursprungs-Selektoren, Antwort- und Anfragetransformationen und CDN-Protokollweiterleitung. Wenden Sie sich mit den Details Ihres Anwendungsfalls an [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com).

### Snapshots für schnelle Entwicklungsumgebungen (Alpha-Programm) {#rde-snapshot-beta}

In Alpha unterstützen schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs) jetzt eine Funktion, um einen Snapshot des aktuellen Code- und Inhaltsstatus zu erstellen, der zu einem späteren Zeitpunkt wiederhergestellt werden kann. Dies kann nützlich sein, wenn Code synchronisiert wird, der möglicherweise zurückgesetzt werden muss, oder wenn zwischen der Entwicklung verschiedener Funktionen gewechselt wird. Es ist auch möglich, nur den veränderlichen Inhalt als bekannten Ausgangspunkt für Tests wiederherzustellen.

Wenn Sie Feedback zu dieser Funktion geben möchten, senden Sie uns eine E-Mail an [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com).

### AEM-Protokollweiterleitung an weitere Ziele (Beta-Programm) {#log-forwarding-beta}

Die Protokolle können zwar von Cloud Manager heruntergeladen werden, aber viele Unternehmen ziehen es vor, diese Protokolle an ein bevorzugtes Protokollierungsziel weiterzuleiten. AEM unterstützt bereits die AEM- und CDN-Protokollweiterleitung an Azure Blob Storage, Datadog, HTTPS, Elasticsearch (und OpenSearch) und Splunk. Diese Funktion wird eigenständig konfiguriert und mithilfe der Konfigurations-Pipeline bereitgestellt.

Jetzt in der Beta-Phase können Sie AEM-Protokolle an Amazon S3, Sumo Logic, Dynatrace und Ihr eigenes New Relic-Konto (nicht das von Adobe bereitgestellte Konto) weiterleiten. Beachten Sie, dass zwar AEM-Protokolle (einschließlich Apache/Dispatcher) für diese Protokollierungsziele unterstützt werden, jedoch keine CDN-Protokolle. Schreiben Sie eine E-Mail an [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com), um Zugriff zu erhalten.

Weitere Informationen finden Sie in der [Dokumentation zur Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md).

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
