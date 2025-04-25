---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 11d019e10dc9246e5560f7fe27472d047cdc7caa
workflow-type: tm+mt
source-wordcount: '1551'
ht-degree: 48%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.4.0) ist der Freitag, 24. April 2025. Die nächste Version (2025.5.0) ist für den Freitag, 29. Mai 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in Experience Manager Sites {#enhancements-sites}

**Neue Admin-Benutzeroberfläche des Inhaltsfragmentmodells**

Um die Liste der neuen Client-seitigen Benutzeroberflächen beim Arbeiten mit AEM-Inhaltsfragmenten weiter zu vervollständigen, ist jetzt eine neue Admin-Benutzeroberfläche für Inhaltsfragmentmodelle verfügbar. Die neue Benutzeroberfläche bietet eine klare und moderne Listenansicht, die die Suche nach Modellen mit Filtern ermöglicht und die Modell-Tags und die vorhandenen Inhaltsfragmente, die auf einem bestimmten Modell basieren, anzeigt. Die Dokumentation finden Sie [hier](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media (Scene7) {#dynamic-media-scene7}

**Dynamic Media (Scene7) wird in erweiterten Sicherheitsumgebungen nicht unterstützt**

Dynamic Media (Scene7) auf AEM as a Cloud Service ist nicht HIPAA-fähig und kann nicht in AEM-Umgebungen verwendet werden, in denen die erweiterte Sicherheit aktiviert ist.

Ab der AEM as a Cloud Service-Version vom April 2025 verhindert eine technische Einschränkung, dass Dynamic Media (Scene7) in Umgebungen mit verbesserter Sicherheit konfiguriert wird. Infolgedessen ist die Karte **Dynamic Media-Konfiguration** unter **Tools** > **Cloud Services** in diesen Umgebungen nicht mehr sichtbar.

Kunden, die AEM 6.5 verwenden, sollten außerdem beachten, dass der Dynamic Media (Scene7)-Stack nicht HIPAA-fähig ist.

### Dynamic Media Classic {#dynamic-media-classic}

**Reporting**

Die Registerkarte „Bandbreite“ im Reporting-Dashboard von Dynamic Media Classic wird seit April 2025 nicht mehr unterstützt.

Siehe [Bandbreite und Speicher, Berichtstypen](https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/setup/administration-setup#types-of-reports).


## Neue Funktionen in der Assets-Ansicht {#new-features-assets-view}

**Asset-Beziehungen**

Die Assets-Ansicht unterstützt nun das Anzeigen und Bearbeiten von Asset-Beziehungen in einem vereinfachten Bedienfeld mit Asset-Details. Fügen Sie mühelos Beziehungen wie Source und Derivative zu Inhalten hinzu, damit Benutzer relevante Hero-Inhalte effektiver finden können.

Beispiel für eine ![Assets-Beziehung](/help/assets/assets/asset-relations-example.png)

**Vergleichen von Versionen eines Assets**

Sie können jetzt mithilfe der Assets-Ansicht schnell eine beliebige Version eines Assets auswählen und mit der neuesten Version vergleichen.

![Vergleichen von Asset-Versionen](/help/assets/assets/version-compare2.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Funktionen der Vorabversion

* [Universeller Editor - Formularfragmente](/help/edge/docs/forms/universal-editor/creating-form-fragments.md): Mit dem universellen Editor können Sie jetzt Formularfragmente für adaptive Forms erstellen und wiederverwenden. Bei diesen Fragmenten handelt es sich um wiederverwendbare Formularabschnitte (z. B. Kontaktdaten, Einverständnisfelder), die einmal erstellt und auf mehrere Formulare angewendet werden können. Diese Funktion optimiert die Formularerstellung, stellt Konsistenz sicher und verbessert die Effizienz bei der Bearbeitung.

* [SharePoint-Dokumentbibliothek - Anhänge mit Originaldateinamen speichern](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library): Sie haben jetzt die Möglichkeit, Formularanhänge unter Verwendung ihrer Originaldateinamen zu speichern, wenn Sie sie in einer SharePoint-Dokumentbibliothek speichern. Diese Verbesserung vereinfacht die Identifizierung und Verwaltung hochgeladener Dateien.

* **Regeleditor**:
   * [Binäre Bedingung mit Klickereignis in der Wenn-Klausel](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor): Der Regeleditor ermöglicht jetzt die Kombination eines Schaltflächen-Klickereignisses (_Wird angeklickt_) mit anderen Bedingungen innerhalb der Wenn-Klausel. Dies ermöglicht eine präzisere Kontrolle der Regelausführung basierend auf der Benutzerinteraktion und anderen Faktoren. Hinweis: Bei Verwendung mehrerer Bedingungen muss das Klickereignis die erste aufgeführte Bedingung sein.
   * [Validierungsbedingungen für Felder und Bereiche](/help/forms/rule-editor-core-components-usecases.md): Der Regeleditor enthält jetzt _IsValid_ und _IsNotValid_ Bedingungen. Damit können Sie den Validierungsstatus bestimmter Felder oder ganzer Bedienfelder (einschließlich Layouts wie horizontale Registerkarten, vertikale Registerkarten, Akkordeons und Assistenten) überprüfen und die Formularnavigation und das Benutzererlebnis auf der Grundlage der Validierungsergebnisse verbessern.
* **Verbesserte Bereichsverwaltung für SharePoint-Listen**: SharePoint-Sites unterstützen jetzt alle verwalteten Pfade, z. B. /sites und /teams. Diese Verbesserung ermöglicht eine breitere Integration über verschiedene Site-Strukturen von SharePoint hinweg und bietet mehr Flexibilität bei der Verbindung mit organisatorischen Inhalten.
* **Unterstützung für das Speichern des Datensatzdokuments in der SharePoint-Liste**: Forms, das mit einem auf SharePoint-Listen basierenden Formulardatenmodell (FDM) erstellt wurde, kann jetzt das Datensatzdokument (DoR) in SharePoint-Listen speichern, indem die Feldeigenschaft „Bindungsverweis für Datensatzdokument“ konfiguriert wird. Diese Verbesserung ermöglicht die nahtlose Integration unterstützter Formulardaten und Dokumente in den SharePoint-Speicher.

### Early Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Integration von Adobe Experience Platform (AEP) mit Forms

Integrationsfunktionen zwischen Forms und AEP sind jetzt für Early Adopters verfügbar.

## CIF-Add-on {#cloud-services-cif}

### Verbesserungen {#enhancements-cif}

* Hinzufügen der Auswahl von Produktvarianten für den CIF-Produktreferenz-Datentyp
* [Experimentell]: JSON+LD in CIF-Kernkomponenten in PDPs
* [Experimentell]: CIF-Fähigkeit zum Löschen des Caches

### Fehlerbehebungen {#bug-fixes-cif}

* Beheben eines Suchproblems im Produktfeld
* Format der Produkt-URL funktioniert für #variant_sku nicht erwartungsgemäß
* Es können nicht mehr als 20 SKUs zur Produktlisten-Komponente hinzugefügt werden

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### OpenAPI-basierte APIs {#open-apis}

Entwickelnde können AEM as a Cloud Service-Funktionen in ihre eigenen Anwendungen und Tools integrieren. Neue AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation, weil sie konsistent, gut dokumentiert und benutzerfreundlich sein sollen. Anmeldeinformationen für Endpunkte, für die eine Authentifizierung erforderlich ist, werden durch Erstellen von Adobe Developer Console-Projekten generiert und unterstützen OAuth-Server-zu-Server, Web-App und Einzelseiten-App (SPA).

[Sehen Sie die vollständige Liste](https://developer.adobe.com/experience-cloud/experience-manager-apis/#openapi-based-apis) der OpenAPI-basierten APIs, [Erfahren Sie mehr](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [-Tutorial aus, ](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) Konfiguration und Verwendung veranschaulicht.

In diesem Video erfahren Sie, wie Sie eine authentifizierte API für die spätere Verwendung konfigurieren:

>[!VIDEO](https://video.tv.adobe.com/v/3457510?quality=12&learn=on)

### Verbesserungen bei der CDN-Konfiguration {#cdn-enhancements}

Das von Adobe verwaltete CDN bietet flexible Konfigurationsoptionen, wie im Artikel [Pipeline konfigurieren](/help/operations/config-pipeline.md#configurations) beschrieben. Im Folgenden finden Sie einige aktuelle Funktionen:

#### Einschließen zusätzlicher Eigenschaften in CDN-Protokolle {#props-in-cdnlogs}

Dies ist nützlich für Szenarien wie das Debugging und die Datenanalyse. Sie können über die Standardeigenschaften hinaus weitere Informationen in Ihre CDN-Protokolle aufnehmen, indem Sie die `logProperty` -Aktion in [Anfrage- und Antworttransformationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) festlegen.

#### Eigenschaften von Region, Kontinent und Organisation als übereinstimmende Bedingungen {#matching-conditions}

CDN-Regeln können jetzt basierend auf Region, Kontinent und Organisation für Anwendungsfälle abgeglichen werden, einschließlich Sperren von Traffic und Umleitungen. `clientRegion` und `clientContinent` ergänzen die bereits unterstützten `clientCountry`, sodass sie auf der Grundlage der geografischen Lage übereinstimmen, während `clientAsName` und `clientAsNumber` mit Autonomous Systems übereinstimmen, um große ISPs, Unternehmen oder Cloud-Anbieter zu identifizieren. Weitere Informationen zu diesen [neu verfügbar gemachten Anfrageeigenschaften](/help/security/traffic-filter-rules-including-waf.md#condition-structure).

#### Cookie-Wert festlegen {#cookie-attributes}

Sie können Cookie-Attribute in [Antworttransformationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) festlegen.

### Java 21-Unterstützung {#java21}

Ab der Januar-Version können Sie Code mit Java 21 und Java 17 erstellen. Sie erhalten Zugriff auf neue Funktionen wie Mustervergleich, versiegelte Klassen und verschiedene Leistungsverbesserungen. Die Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support). 

Die leistungsfähigere Java 21 **Runtime** wird automatisch bereitgestellt, wenn ein Java 17- oder Java 21-Build erkannt wird. Adobe empfiehlt jedoch auch, sich für Umgebungen, die mit Java 11 erstellt wurden, für die Java 21 Runtime anzumelden. Senden Sie hierzu einfach eine E-Mail an [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Erfahren Sie mehr zu den [Java 21 Runtime-Anforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Die Java 21 **Runtime** wurde im Februar für Ihre Entwicklungs-/RDE-Umgebungen bereitgestellt und wird am **28. und 29. April** auf Ihre Staging-/Produktionsumgebungen angewendet. Beachten Sie, dass das **Erstellen von Code** mit Java 21 (oder Java 17) unabhängig von der Java 21-Laufzeit erfolgt. Sie müssen explizit Schritte zum Erstellen von Code mit Java 21 (oder Java 17) ausführen.

### AEM-Protokollweiterleitung an weitere Ziele - Beta-Programm {#log-forwarding-earlyadopter}

In der Beta-Version können Sie AEM-Protokolle an New Relic (mithilfe von HTTPS), Amazon S3 und Sumo Logic weiterleiten. Beachten Sie, dass zwar AEM-Protokolle (einschließlich Apache/Dispatcher) unterstützt werden, jedoch keine CDN-Protokolle. Schreiben Sie eine E-Mail an [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com), um Zugriff zu erhalten.

Die Protokolle können zwar von Cloud Manager heruntergeladen werden, aber viele Unternehmen ziehen es vor, diese Protokolle an ein bevorzugtes Protokollierungsziel weiterzuleiten. AEM unterstützt bereits die (allgemein verfügbare) AEM- und CDN-Protokollweiterleitung an Azure Blob Storage, Datadog, HTTPS, Elasticsearch (und OpenSearch) und Splunk. Diese Funktion wird eigenständig konfiguriert und mithilfe der Konfigurations-Pipeline bereitgestellt.

Weitere Informationen finden Sie in der [Dokumentation zur Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md).

### Edge-Computing – Einladung zum Feedback! {#edge-computing-feedback}

Edge-Computing bringt die Datenverarbeitung näher an den Browser heran, was Vorteile bietet, darunter eine reduzierte Latenz. Adobe würde gerne von Ihnen hören, ob Sie diese Technologie als nützlich für AEM Publish Delivery- und Edge Delivery Services-Projekte erachten. Teilen Sie uns bitte außerdem mit, wofür Sie sie voraussichtlich verwenden würden. Diese Information hilft uns bei der Gestaltung der Produkt-Roadmap. 

Verschiedene mögliche Anwendungsfälle:

* Authentifizierung mit einer IdP, um Zugriff auf Inhalte zu erhalten
* Personalization durch Rendern dynamischer Inhalte basierend auf Geolokalisierung, Gerätetyp, Benutzerattributen usw.
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
