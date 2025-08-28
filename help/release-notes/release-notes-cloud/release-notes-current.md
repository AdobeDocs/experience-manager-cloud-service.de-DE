---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 96022123209fff18548b77a4cbd63ccec697119b
workflow-type: tm+mt
source-wordcount: '1902'
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

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.8.0) ist der Freitag, 28. August 2025. Die nächste Version mit neuen Funktionen (2025.9.0) ist für den Freitag, 25. September 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440929?quality=12&captions=ger)

-->

## Experience Hub {#experience-hub}

Die [Experience Hub](/help/experience-hub.md) ist Ihr zentraler Ausgangspunkt für den Zugriff auf alle AEM-Funktionen. Er wird anhand Ihrer Benutzerrolle und der Ihnen zur Verfügung stehenden Lizenzen personalisiert, sodass jeder Benutzer seine Ergebnisse effizient erzielen kann.

## KI-Assistent in AEM {#AI-assistant}

Der [AI Assistant](/help/implementing/cloud-manager/ai-assistant-in-aem.md) für AEM bietet eine Gesprächsoberfläche, mit der Sie sofortige Antworten auf Ihre produktbezogenen Fragen zu AEM erhalten (*für alle Benutzenden verfügbar* und die Erstellung von Support-Tickets automatisieren können (*für Support-Admins verfügbar*). Es ist direkt in AEM eingebettet und kann über die AEM Experience Hub-, Cloud Manager- und Authoring-Benutzeroberfläche aufgerufen werden.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#enhancements-sites}

* In der Admin-Benutzeroberfläche von Inhaltsfragmenten können Sie jetzt den Workflow-Status für Inhaltsfragmente mit detaillierten Informationen zu vergangenen und derzeit laufenden Workflows für ein ausgewähltes Fragment anzeigen.
* Die Leistung beim Öffnen von Inhaltsfragmenten im neuen Inhaltsfragment-Editor wurde in gängigen Szenarien um 25 % erhöht, indem Fragmente über UUID statt über den Pfad geöffnet wurden.
* Beim Kopieren von Inhaltsfragmenten mit referenzierten Fragmenten werden Kopien der referenzierten Fragmente jetzt am selben Speicherort wie die übergeordnete Fragmentkopie gespeichert.
* Sie können jetzt einen benutzerdefinierten Arbeitsbereich in den Ordnereinstellungen konfigurieren, um die Inhaltsfragmente in den konfigurierten Arbeitsbereich in Adobe Target zu exportieren.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in Content Hub {#new-features-content-hub}

**Massensuche über Filtereigenschaften**

Mit Content Hub können Sie jetzt schneller die benötigten Assets finden. Mit der neuen Funktion für die Massensuche können Sie mehrere Werte für eine beliebige Filtereigenschaft eingeben - getrennt durch ein Trennzeichen (z. B. mehrere SKU-IDs) - und sofort alle übereinstimmenden Assets mit einer einzigen Suche abrufen.

### Neue Funktionen in Dynamic Media mit OpenAPI-Funktionen {#new-features-dynamic-media-with-openapi}

**SEO-freundliches DM mit OpenAPI-URLs**

Erstellen Sie Vanity-URLs für die Asset-Bereitstellung in DM mit OpenAPI und ersetzen Sie lange systemgenerierte UUIDs durch kurze, lesbare Kennungen. Dadurch werden Links SEO-freundlich und besser auf Ihre Marke oder Kampagnen abgestimmt. Vanity-URLs werden zur Laufzeit automatisch zur ursprünglichen Asset-UUID aufgelöst, ohne vorhandene Workflows zu unterbrechen.

>[!NOTE]
>
>Diese Funktion wird am 10. September als Funktion für eingeschränkte Verfügbarkeit verfügbar sein. Sie können [einen Adobe-Kunden-Support-Fall erstellen und senden](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um ihn für Ihre Bereitstellung zu aktivieren.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

* **Datums- und Uhrzeiteingabekomponente**: Eine Datums- und Uhrzeitkomponente ist jetzt verfügbar, sodass Benutzende sowohl Datum als auch Uhrzeit über eine Kalender- und Uhrenschnittstelle auswählen oder Werte in einem unterstützten Format manuell eingeben können.
* [Verbesserte Fehlerbehandlung für Datei-Uploads](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab): Die Dateianlagenkomponente validiert jetzt den hochgeladenen Dateityp automatisch anhand der Zulassungsliste. Wenn ein(e) Benutzende(r) eine Datei in einem nicht unterstützten Format hochlädt, wird im Formular während der Übermittlung ein Fehler angezeigt. Die Komponente überprüft auch den Dateiinhalt, um seinen Typ zu überprüfen, wodurch die allgemeine Sicherheit des Formulars verbessert wird.
* **Angegebene Fehlerantwort für benutzerdefinierte Übermittlungsaktion**: Wenn bei einer benutzerdefinierten Übermittlungsaktion ein nicht behandelter Fehler auftritt, wird der Fehler-Code 502 zurückgegeben. Auf diese Weise können Sie erkennen, dass das Problem mit der benutzerdefinierten Übermittlungsaktion zusammenhängt, was das Debugging erleichtert.
* [Ausgeblendete Felder vom Datensatzdokument ausschließen](/help/forms/generate-document-of-record-core-components.md#document-of-record-settings): Es wurde eine neue Eigenschaft hinzugefügt, die den Ausschluss ausgeblendeter Felder vom Datensatzdokument ermöglicht. Standardmäßig ist diese Option nicht aktiviert und gilt für alle Formularfelder.

### Vorabversionsfunktionen in AEM Forms

* [Generieren und Synchronisieren von AFP-](/help/forms/document-generation-afp-api.md): Sie können jetzt die AEM Forms-Kommunikations-API verwenden, um eine XDP-Datei in das AFP-Format zu konvertieren. AFP ist ein leistungsstarkes Format, das im Großdruck in Unternehmen weit verbreitet ist.
* **Verbesserungen im Regeleditor**
   * **Verbesserungen bei Validierungs- und Zurücksetzungsfunktionen**: Die Methoden zum Validieren und Zurücksetzen unterstützen jetzt die Ausführung auf Bedienfeld-, Feld- und Formularebene. Zuvor wurden sie nur auf Formularebene unterstützt.
   * **Moderner JavaScript-**: Unterstützung für ECMAScript 2019 und neuere Funktionen wurde für benutzerdefinierte Funktionen hinzugefügt, sodass Sie effizienteren, modularen und wiederverwendbaren Code schreiben können
   * **Download-Datensatzdokument-Option im Regeleditor**: Eine Funktion zum Herunterladen des Datensatzdokuments (DoR) wurde im Regeleditor als vordefinierte Option hinzugefügt.
     ![Datensatzdokument](/help/forms/assets/document-of-record-rn.gif)
   * **Dynamische Variablen im Regeleditor**: Sie können jetzt dynamische (temporäre) Variablen im Regeleditor verwenden, um die Flexibilität beim Definieren von Bedingungen und Aktionen zu erhöhen. Ausgeblendete Felder sind nicht mehr zum Speichern temporärer Werte erforderlich.
   * **Benutzerdefinierte ereignisbasierte Regeln im Regeleditor**: Sie können jetzt benutzerdefinierte Trigger und Ereignisregeln definieren, die auf diesen Ereignissen basieren.
   * **Kontextabhängige wiederholbare Bereichsregeln**: In wiederholbaren Bereichen werden Regeln jetzt kontextbasiert ausgeführt und nicht mehr nur auf die letzte Bereichsinstanz angewendet.
   * **Regeln werden durch Parameter ausgelöst**: Der Regeleditor unterstützt jetzt die Ausführung von Regeln anhand von Abfrageparametern, UTM-Parametern oder Browser-Parametern.
   * **Formularspezifische benutzerdefinierte Funktionen**: Edge Delivery Services Forms unterstützt jetzt formularspezifische benutzerdefinierte Funktionsskripte und bietet so mehr Flexibilität bei der Verwaltung wiederverwendbarer Logiken.
   * **Statische Importe für benutzerdefinierte Funktionen**: Der Regeleditor im universellen Editor unterstützt jetzt statische Importe, sodass Entwicklerinnen und Entwickler Funktionen in mehreren Formularen organisieren, freigeben und wiederverwenden können.

### Early-Adopter-Funktionen in AEM Forms

* **Komponente „Freihandsignatur**: Sie können jetzt die Komponente „Freihandsignatur“ verwenden, um Benutzern beim Hinzufügen ihrer Signaturen zu einem Formular zu helfen, z. B. in einem Vereinbarungsformular. Die Komponente ermöglicht es Benutzenden, ihre Signatur direkt im Formular mit der Maus, dem Stift oder dem Touchscreen zu zeichnen.
* **Direkte API-Integration im Regeleditor**: Adaptive Forms unterstützen jetzt die direkte API-Integration im visuellen Regeleditor, ohne dass ein Formulardatenmodell erforderlich ist. Autoren können APIs mithilfe eines URL- oder cURL-Imports konfigurieren, Eingabe-/Ausgabeparameter zuordnen und Aufrufe mit Authentifizierung sichern.

<!--
**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

## [!DNL Experience Manager] as a [!DNL Cloud Service] als Fundament {#foundation}

### JavaScript-Kompilierungsaktualisierung {#javascript-compilation}

Die standardmäßige Kompilierung der Client-seitigen Bibliothek (clientlibs) für JavaScript zielt jetzt auf ECMASCRIPT_2018 anstelle von ECMASCRIPT5 ab. Diese Aktualisierung war in der Vergangenheit zwar überschreibbar, ermöglicht aber standardmäßig Leistungsverbesserungen, eine moderne JavaScript-Syntax und Funktionen.

### Bevorstehende Einstellung von Java-APIs {#java-api-deprecation}

Verschiedene veraltete APIs zielen auf die Entfernung am 31. August ab und sollten daher nicht mehr referenziert werden. Anfang September werden Benachrichtigungen des Aktionszentrums gesendet, wenn die API-Nutzung erkannt wird, und nach dem 25. September werden während Cloud Manager-Builds Benachrichtigungen angezeigt, um die Bedeutung der Entfernung der Nutzung zu unterstreichen. Ausführliche Informationen finden [ im Artikel ](/help/release-notes/deprecated-removed-features.md#aem-apis)veraltet“, aber zur Vereinfachung sind diese APIs unten aufgeführt:

<details>
  <summary>Erweitern Sie , um die veralteten Java-APIs anzuzeigen</summary>

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
</details>

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

### Abschaffung der Java 11-Laufzeit {#java11-runtime-deprecation}

Die *Java 11-Laufzeitumgebung* ist jetzt veraltet, und die meisten Umgebungen wurden bereits auf die leistungsfähigere **Java 21-Laufzeitumgebung** aktualisiert.

Wenn Ihre Umgebung aufgrund nicht unterstützter Abhängigkeiten nicht aktualisiert werden konnte (siehe [Java 21-Laufzeitanforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), sollten Sie eine E-Mail von Adobe mit konkreten nächsten Schritten erhalten haben. Stellen Sie sicher, dass alle erforderlichen Aktualisierungen bis zum 1 **Oktober 2025 abgeschlossen**, damit Ihre Umgebung unterbrechungsfrei aktualisiert werden kann.

Hinweis: Die Laufzeitversion ist von der Build-Version Ihres Codes getrennt. Es wird zwar empfohlen, Builds mit Java 21 durchzuführen, aber Java 11-Builds werden derzeit noch unterstützt. Ein separater Hinweis zur Abschaffung von Java 11 für Builds wird in Zukunft freigegeben.

### Durchsetzung der Konfigurationsrichtlinie für AEM-Java-Protokolle {#logconfig-policy}

Wie in den Versionshinweisen vom April erwähnt, müssen AEM-Java-Protokolle einem Standardformat entsprechen, um eine zuverlässige Überwachung in allen Kundenumgebungen sicherzustellen. Benutzerdefinierte Protokollkonfigurationen – wie etwa Änderungen an der Protokollformatierung, Ausgabedateien oder Standardprotokollebenen – werden nicht mehr unterstützt. Protokolle müssen an die Standarddateien weitergeleitet werden, und die standardmäßigen Protokollebenen für AEM-Produkt-Code müssen beibehalten werden. Ausführliche Informationen finden Sie im [Artikel zur Protokollierung](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Ab **25.** werden alle nicht unterstützten benutzerdefinierten Protokollierungsüberschreibungen ignoriert. Nach unserer Analyse ist der Großteil der Kundschaft nicht betroffen, und Adobe hat sich mit Kundinnen und Kunden in Verbindung gesetzt, deren aktuelle Konfiguration möglicherweise betroffen ist.

Bitte überprüfen und aktualisieren Sie alle nachgelagerten Prozesse, die auf einem benutzerdefinierten Protokollierungsverhalten basieren. Zum Beispiel:

* Wenn Ihr Protokollweiterleitungssystem ein benutzerdefiniertes Protokollformat erwartet, müssen Sie möglicherweise Ihre Aufnahmeregeln anpassen.
* Wenn Sie zuvor die Ausführlichkeit des Protokolls durch Ändern der Protokollebenen reduziert haben, beachten Sie, dass eine Rückkehr zu den Standardebenen das Protokollvolumen erhöhen kann.

### Edge Computing (Beta-Programm) {#edge-computing}

Mit der Edge-Datenverarbeitung können Sie JavaScript auf CDN-Ebene ausführen, wodurch die Datenverarbeitung näher an die Endbenutzenden heranrückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge.

Häufige Anwendungsszenarien umfassen:

* Authentifizieren von Benutzenden bei einem Identitätsanbieter, bevor Zugriff auf Inhalte gewährt wird
* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Formatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer API-Antworten) vor ihrer Bereitstellung im Browser
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden
* Bereitstellen eines MCP-Servers für LLMs wie ChatGPT und Claude für den Zugriff auf benutzerdefinierte Tools

Wir haben nur eine begrenzte Anzahl von Möglichkeiten für die AEM-Veröffentlichungsbereitstellung oder Edge Delivery Services-Projekte für Live-Produktions-Sites. Wenn Sie an einer Teilnahme interessiert sind oder mehr erfahren möchten, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls.

### CDN-Konfiguration für Edge Delivery Services (Beta-Programm) {#cdn-eds-beta}

Das von Adobe verwaltete CDN bietet flexible Konfigurationsoptionen, wie im Artikel zu [Konfigurations-Pipelines](/help/operations/config-pipeline.md#configurations) beschrieben.

Jetzt in der Beta-Phase können Sie eine Konfigurations-Pipeline für Funktionen bereitstellen, einschließlich CDN-Ursprünge-Selektoren, Antwort- und Anfrageumwandlungen, CDN-Protokollweiterleitung und mehr. Wenden Sie sich mit den Details Ihres Anwendungsfalls an [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com).

### Snapshots für schnelle Entwicklungsumgebungen (Alpha-Programm) {#rde-snapshot-program}

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
