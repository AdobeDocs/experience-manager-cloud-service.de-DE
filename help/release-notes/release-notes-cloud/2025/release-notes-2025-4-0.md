---
title: Versionshinweise für Version 2025.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2025.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 48e09824-5c67-49d8-8896-358d679649fc
source-git-commit: 0664e5dc4a7619a52cd28c171a44ba02c592ea3d
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 97%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2025.4.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2025.4.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2023 oder 2024 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.4.0) ist der 24. April 2025. Die nächste Version (2025.5.0) ist für den 5. Juni 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Übersichtsvideo zur Version April 2025 an, das eine Zusammenfassung der Funktionen bietet, die in Version 2025.4.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3463991?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#enhancements-sites}

**Neue Admin-Benutzeroberfläche des Inhaltsfragmentmodells**

Zur weiteren Vervollständigung der Liste der neuen Client-seitigen Benutzeroberflächen beim Arbeiten mit AEM-Inhaltsfragmenten ist jetzt eine neue Admin-Benutzeroberfläche für Inhaltsfragmentmodelle verfügbar. Die neue Benutzeroberfläche bietet eine klare und moderne Listenansicht, die die Suche nach Modellen mit Filtern ermöglicht und die Modell-Tags und die vorhandenen Inhaltsfragmente anzeigt, die auf einem bestimmten Modell basieren. Die Dokumentation finden Sie [hier](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md). 

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media (Scene7) {#dynamic-media-scene7}

**Dynamic Media (Scene7) wird in erweiterten Sicherheitsumgebungen nicht unterstützt**

Dynamic Media (Scene7) auf AEM as a Cloud Service ist nicht HIPAA-fähig und kann nicht in AEM-Umgebungen verwendet werden, in denen die erweiterte Sicherheit aktiviert ist.

Ab der AEM as a Cloud Service-Version April 2025 verhindert eine technische Einschränkung, dass Dynamic Media (Scene7) in Umgebungen mit verbesserter Sicherheit konfiguriert wird. Infolgedessen ist die Karte **Dynamic Media-Konfiguration** unter **Tools** > **Cloud Services** in diesen Umgebungen nicht mehr sichtbar.

Kunden, die AEM 6.5 verwenden, sollten außerdem beachten, dass der Stack von Dynamic Media (Scene7) nicht HIPAA-fähig ist.

### Dynamic Media Classic {#dynamic-media-classic}

**Reporting**

Die Registerkarte „Bandbreite“ im Reporting-Dashboard von Dynamic Media Classic wird seit April 2025 nicht mehr unterstützt.

Siehe [Bandbreite und Speicher, Berichtstypen](https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/setup/administration-setup#types-of-reports).

## Neue Funktionen in der Assets-Ansicht {#new-features-assets-view}

**Asset-Beziehungen**

Die Assets-Ansicht unterstützt nun das Anzeigen und Bearbeiten von Asset-Beziehungen in einem vereinfachten Bedienfeld mit Asset-Details. Fügen Sie mühelos Beziehungen wie „Quelle“ und „Bearbeitung“ zu Inhalten hinzu, damit Benutzende relevante Hero-Inhalte effektiver finden können.

Beispiel für eine ![Assets-Beziehung](/help/assets/assets/asset-relations-example.png)

**Vergleichen von Versionen eines Assets**

Sie können jetzt mithilfe der Assets-Ansicht schnell eine beliebige Version eines Assets auswählen und mit der neuesten Version vergleichen.

![Vergleichen von Asset-Versionen](/help/assets/assets/version-compare2.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Funktionen der Vorabversion

* [Universeller Editor für adaptive Formulare und Formularfragmente](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): Der universelle Editor unterstützt jetzt die Erstellung sowohl von adaptiven Formularen als auch von wiederverwendbaren Formularfragmenten. Autorinnen und Autoren können in einer vereinfachten WYSIWYG-Authoring-Umgebung Formulare visuell erstellen, Übermittlungsaktionen konfigurieren und eine reCAPTCHA-Validierung hinzufügen. Diese Funktion beschleunigt die Erstellung von Formularen, erhöht die Konsistenz und verbessert den Schutz vor Spam und automatisiertem Missbrauch.

* [SharePoint-Dokumentbibliothek – Anhänge mit Originaldateinamen speichern](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library): Sie haben jetzt die Möglichkeit, Formularanhänge unter Verwendung ihrer Originaldateinamen zu speichern, wenn Sie sie in einer SharePoint-Dokumentbibliothek speichern. Diese Verbesserung vereinfacht die Identifizierung und Verwaltung hochgeladener Dateien.

* **Regeleditor**:
   * [Binäre Bedingung mit Klickereignis in der Wenn-Klausel](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor): Der Regeleditor ermöglicht jetzt die Kombination eines Schaltflächen-Klickereignisses (_Wird angeklickt_) mit anderen Bedingungen innerhalb der Wenn-Klausel. Dies ermöglicht eine präzisere Kontrolle der Regelausführung basierend auf der Benutzerinteraktion und anderen Faktoren. Hinweis: Bei Verwendung mehrerer Bedingungen muss das Klickereignis die erste aufgeführte Bedingung sein.
   * [Validierungsbedingungen für Felder und Bereiche](/help/forms/rule-editor-core-components-usecases.md): Der Regeleditor enthält jetzt die Bedingungen _IsValid_ und _IsNotValid_. Damit können Sie den Validierungsstatus bestimmter Felder oder ganzer Bedienfelder (einschließlich Layouts wie horizontale Registerkarten, vertikale Registerkarten, Akkordeons und Assistenten) überprüfen und die Formularnavigation und das Benutzererlebnis auf der Grundlage der Validierungsergebnisse verbessern.
* [Verbesserte Verwaltung des SharePoint-Listenumfangs](/help/forms/connect-forms-to-sharepoint-list.md): SharePoint-Sites unterstützen jetzt alle verwalteten Pfade, z. B. /sites und /teams. Diese Verbesserung ermöglicht eine breitere Integration über verschiedene Site-Strukturen von SharePoint hinweg und bietet mehr Flexibilität bei der Verbindung mit organisatorischen Inhalten.
* [Unterstützung für das Speichern des Datensatzdokuments in der SharePoint-Liste](/help/forms/generate-document-of-record-core-components.md#bind-adaptive-form-components-with-template-fields): Formulare, die mit einem auf SharePoint-Listen basierenden Formulardatenmodell (FDM) erstellt wurden, können jetzt den Nachweis (DoR) in SharePoint-Listen speichern, indem die Feldeigenschaft „Bindungsverweis für Nachweis“ konfiguriert wird. Diese Verbesserung ermöglicht die nahtlose Integration unterstützter Formulardaten und Dokumente mit dem SharePoint-Speicher.
* [Unterstützung der automatischen Zuordnung für adaptive Formularfragmente](/help/forms/adaptive-form-fragments-core-components.md#auto-mapping-support-for-fragments-in-an-adaptive-form): Adaptive Forms unterstützen jetzt das automatische Einfügen übereinstimmender Fragmente, wenn Schemaobjekte an einer definierten Fragmentstruktur ausgerichtet werden. Dies optimiert die Formularerstellung und fördert die Wiederverwendung.

### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Integration von Adobe Experience Platform (AEP) mit Forms

* [Integration von AEM Forms mit Adobe Experience Platform](/help/forms/aem-forms-aep-connector.md): Der AEM Forms to Adobe Experience Platform-Connector ermöglicht eine nahtlose Integration zwischen adaptiven Formularen und Adobe Experience Platform. Mit dieser Funktion können Formulardaten XDM-Schemata zugeordnet und in Echtzeit direkt an AEP gesendet werden. Sie optimiert die Datenerfassung für Anwendungsfälle in den Bereichen Personalisierung und Aktivierung in allen Adobe Experience Cloud-Lösungen.

## CIF-Add-on {#cloud-services-cif}

### Verbesserungen {#enhancements-cif}

* Hinzufügen einer Auswahl von Produktvarianten für CIF-Produktverweis-Datentyp.
* **Experimentell**: [JSON+LD in CIF-Kernkomponenten in PDPs](/help/commerce-cloud/cif-storefront/customizing/json-ld.md)
* **Experimentell**: [CIF-Möglichkeit, den Cache zu löschen](/help/commerce-cloud/cif-storefront/configuring/clear-cache.md)

### Fehlerbehebungen {#bug-fixes-cif}

* Beheben eines Suchproblems im Produktfeld
* Produkt-URL-Format funktioniert für #variant_sku nicht wie erwartet.
* Der Produktlistenkomponente können nicht mehr als 20 SKUs hinzugefügt werden.

## [!DNL Experience Manager] as a [!DNL Cloud Service] als Fundament {#foundation}

### OpenAPI-basierte APIs {#open-apis}

Entwickelnde können AEM as a Cloud Service-Funktionen in ihre eigenen Anwendungen und Tools integrieren. Neue AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation, weil sie konsistent, gut dokumentiert und benutzerfreundlich sein sollen. Anmeldeinformationen für Endpunkte, für die eine Authentifizierung erforderlich ist, werden durch Erstellen von Adobe Developer Console-Projekten generiert und unterstützen OAuth-Server-zu-Server, Web-Anwendung und Single Page Application (SPA).

[Sehen Sie die vollständige Liste](https://developer.adobe.com/experience-cloud/experience-manager-apis/?lang=de#openapi-based-apis) der OpenAPI-basierten APIs, [erfahren Sie mehr](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [umfassendes Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) aus, das Konfiguration und Verwendung veranschaulicht.

In diesem Video erfahren Sie, wie Sie ein authentifiziertes API für die spätere Verwendung konfigurieren:

>[!VIDEO](https://video.tv.adobe.com/v/3457510?quality=12&learn=on)

### Verbesserungen bei der CDN-Konfiguration {#cdn-enhancements}

Das von Adobe verwaltete CDN bietet flexible Konfigurationsoptionen, wie im Artikel [Konfigurations-Pipelines konfigurieren](/help/operations/config-pipeline.md#configurations) beschrieben. Im Folgenden finden Sie einige aktuelle Funktionen:

#### Einschließen zusätzlicher Eigenschaften in CDN-Protokolle {#props-in-cdnlogs}

Dies ist nützlich für Szenarien wie das Debugging und die Datenanalyse. Sie können über die Standardeigenschaften hinaus weitere Informationen in Ihre CDN-Protokolle aufnehmen, indem Sie die Aktion `logProperty` in [Anfrage- und Antworttransformationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) festlegen.

#### Die Eigenschaften Region, Kontinent und Organisation als übereinstimmende Bedingungen {#matching-conditions}

CDN-Regeln können jetzt basierend auf Region, Kontinent und Organisation abgeglichen werden, einschließlich für Anwendungsfälle wie Sperren von Traffic und Umleitungen. `clientRegion` und `clientContinent` ergänzen das bereits unterstützte `clientCountry`, sodass sie auf der Grundlage der geografischen Lage abgeglichen werden, während `clientAsName` und `clientAsNumber` mit Autonomous Systems abgeglichen werden, um große ISPs, Unternehmen oder Cloud-Anbieter zu identifizieren. Erfahren Sie mehr über diese [neu verfügbar gemachte Anfrageeigenschaften](/help/security/traffic-filter-rules-including-waf.md#condition-structure).

#### Festlegen eines Cookie-Werts {#cookie-attributes}

Sie können Cookie-Attribute in [Antworttransformationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) festlegen.

### Java 21-Unterstützung {#java21}

Ab der Januar-Version können Sie Code mit Java 21 und Java 17 erstellen. Sie erhalten Zugriff auf neue Funktionen wie Mustervergleich, versiegelte Klassen und verschiedene Leistungsverbesserungen. Die Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support). 

Die leistungsfähigere Java 21 **Runtime** wird automatisch bereitgestellt, wenn ein Java 17- oder Java 21-Build erkannt wird. Adobe empfiehlt jedoch auch, sich für Umgebungen, die mit Java 11 erstellt wurden, für die Java 21 Runtime anzumelden. Senden Sie hierzu einfach eine E-Mail an [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Erfahren Sie mehr zu den [Java 21 Runtime-Anforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Die Java 21 **Runtime** wurde im Februar für Ihre Entwicklungs-/RDE-Umgebungen bereitgestellt und wird am **28. und 29. April** auf Ihre Staging-/Produktionsumgebungen angewendet. Beachten Sie, dass das **Erstellen von Code** mit Java 21 (oder Java 17) unabhängig von der Java 21-Laufzeit erfolgt. Sie müssen explizit Schritte zum Erstellen von Code mit Java 21 (oder Java 17) ausführen.

### Durchsetzung der Protokollierungskonfigurationsrichtlinie von AEM {#logconfig-policy}

Um eine effektive Überwachung von Kundenumgebungen zu gewährleisten, müssen die AEM-Java-Protokolle ein konsistentes Format aufweisen und sollten nicht durch benutzerdefinierte Konfigurationen überschrieben werden. Die Protokollausgabe muss an die Standarddateien weitergeleitet bleiben. Für AEM-Produkt-Code müssen die standardmäßigen Protokollebenen beibehalten werden. Es ist jedoch akzeptabel, die Protokollebenen für den von der Kundin oder dem Kunden entwickelten Code anzupassen.

Zu diesem Zweck sollten keine Änderungen an den folgenden OSGi-Eigenschaften vorgenommen werden:
* **Apache Sling Log Configuration** (PID: `org.apache.sling.commons.log.LogManager`) – *alle Eigenschaften*
* **Apache Sling Logging Logger Configuration** (werksseitige PID: `org.apache.sling.commons.log.LogManager.factory.config`):
   * `org.apache.sling.commons.log.file`
   * `org.apache.sling.commons.log.pattern`

Mitte Mai wird AEM eine Richtlinie durchsetzen, durch die alle benutzerdefinierten Änderungen an diesen Eigenschaften ignoriert werden. Bitte überprüfen und passen Sie Ihre nachgelagerten Prozesse entsprechend an. Wenn Sie beispielsweise die Protokollweiterleitungsfunktion verwenden:
* Wenn Ihr Protokollierungsziel ein benutzerdefiniertes (nicht standardmäßiges) Protokollformat erwartet, müssen Sie möglicherweise Ihre Aufnahmeregeln aktualisieren.
* Wenn Änderungen an den Protokollebenen die Protokollierbarkeit reduzieren, beachten Sie, dass die standardmäßigen Protokollebenen zu einer erheblichen Steigerung des Protokollierungsvolumens führen können.

### AEM-Protokollweiterleitung an weitere Ziele – Beta-Programm {#log-forwarding-earlyadopter}

In der Beta-Version können Sie AEM-Protokolle an New Relic (mithilfe von HTTPS), Amazon S3 und Sumo Logic weiterleiten. Beachten Sie, dass zwar AEM-Protokolle (einschließlich Apache/Dispatcher) unterstützt werden, jedoch keine CDN-Protokolle. Schreiben Sie eine E-Mail an [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com), um Zugriff zu erhalten.

Die Protokolle können zwar von Cloud Manager heruntergeladen werden, aber viele Unternehmen ziehen es vor, diese Protokolle an ein bevorzugtes Protokollierungsziel weiterzuleiten. AEM unterstützt bereits die (allgemein verfügbare) AEM- und CDN-Protokollweiterleitung an Azure Blob Storage, Datadog, HTTPS, Elasticsearch (und OpenSearch) und Splunk. Diese Funktion wird eigenständig konfiguriert und mithilfe der Konfigurations-Pipeline bereitgestellt.

Weitere Informationen finden Sie in der [Dokumentation zur Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md).

### Edge-Computing – Einladung zum Feedback! {#edge-computing-feedback}

Edge-Computing bringt die Datenverarbeitung näher an den Browser heran, was Vorteile bietet, darunter eine reduzierte Latenz. Adobe würde gerne von Ihnen hören, ob Sie diese Technologie als nützlich für AEM Publish Delivery- und Edge Delivery Services-Projekte erachten. Teilen Sie uns bitte außerdem mit, wofür Sie sie voraussichtlich verwenden würden. Diese Information hilft uns bei der Gestaltung der Produkt-Roadmap. 

Verschiedene mögliche Anwendungsfälle:

* Authentifizierung mit einer IdP, um Zugriff auf Inhalte zu erhalten
* Personalisierung durch das Rendern dynamischer Inhalte basierend auf Geolocation, Gerätetyp, Benutzerattributen usw.
* Erweiterte Bildbearbeitung
* Middleware zwischen dem CDN und einem Ursprung
* Eine Ebene zwischen dem Browser und eines Dritteranbieter-APIs, möglicherweise zur Neuformatierung der API-Antwort
* Aggregieren von Daten aus verschiedenen Quellen, um dem Client-Browser das Rendern zu erleichtern

Schreiben Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit Fragen und Kommentaren!

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
