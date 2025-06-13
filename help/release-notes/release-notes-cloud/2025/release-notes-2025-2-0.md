---
title: Versionshinweise für Version 2025.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2025.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
exl-id: b893663d-35f1-43ae-a029-4c249b117f2d
source-git-commit: 403ffbede5438131d0b0e770215b990e2d16c018
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 96%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2025.2.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2025.2.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2023 oder 2024 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.2.0) ist der 4. März 2025. Die nächste Version (2025.3.0) ist für den 27. März 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video zur Versionsübersicht Februar 2025 an, das eine Zusammenfassung der Funktionen bietet, die der Version 2025.2.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3458080?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in AEM Sites {#new-features-sites}

**Automatisches Tagging für Inhaltsfragmente**

Beim Erstellen von Inhaltsfragmenten ist es jetzt möglich, automatisch Tags zu erben, die dem Inhaltsmodell zugewiesen wurden. Dies ermöglicht eine wirksame automatische Klassifizierung von Inhalten, die in Inhaltsfragmenten gespeichert sind.

**UUID-Unterstützung für Inhaltsfragmente**

Die UUID-Unterstützung für Inhaltsfragmente ist jetzt allgemein verfügbar. Die neue Funktion ändert nicht das pfadbasierte Verhalten von Vorgängen innerhalb von AEM, z. B. Verschieben, Umbenennen, Rollout, bei denen Pfade automatisch angepasst werden. Sie kann jedoch die externe Verwendung von Inhaltsfragmenten vereinfachen und stabiler gestalten, insbesondere wenn GraphQL-Abfragen verwendet werden, die direkt auf einzelne Fragmente mit ByPath-Abfragen abzielen. Solche Abfragen können fehlschlagen, wenn sich ein Fragmentpfad ändert. Bei Verwendung des neuen Abfragetyps „ById“ bleibt die Abfrage jetzt stabil, da sich die UUID eines Fragments nicht ändert, auch wenn Pfade dies tun.

**Dynamic Media mit OpenAPI-Unterstützung im Inhaltsfragment-Editor und in GraphQL**

Assets, die in anderen AEM as a Cloud Service-Programmen als Inhaltsfragmenten gespeichert sind, und die mit der neuen „Dynamic Media mit OpenAPI“-Funktion aktiviert sind, können jetzt in Inhaltsfragmenten verwendet werden. Mit der Bildauswahl im neuen Inhaltsfragment-Editor können jetzt „Remote“-Repositorys als Quelle für Bild-Assets ausgewählt werden, auf die im Fragment verwiesen werden soll. Und bei der Bereitstellung solcher Inhaltsfragmente mit AEM GraphQL enthält die JSON-Antwort jetzt die erforderlichen Eigenschaften für Remote-Assets (assetId, repositoryId), damit Client-Anwendungen entsprechende „Dynamic Media mit OpenAPI“-URLs erstellen können, um das Bild abzurufen.

**Inhaltsfragmenteditor – Rollout**

Die Aktivierung des neuen [Inhaltsfragment-Editors](/help/sites-cloud/administering/content-fragments/authoring.md) in AEM as a Cloud Service erfolgt weiterhin mithilfe von [Unified Shell](/help/overview/aem-cloud-service-on-unified-shell.md) (unter Verwendung der Spectrum-Benutzeroberfläche). Nachdem er im November 2024 bereits zur Standardeinstellung für alle Cloud Service-Entwicklungsumgebungen wurde, wird er ab dem 1. April 2025 auch für alle Staging-Umgebungen und ab dem 1. Mai 2025 für alle Produktionsumgebungen als Standard festgelegt. In allen Fällen haben Benutzende weiterhin die Möglichkeit, zum herkömmlichen Inhaltsfragmenteditor in der Touch-optimierten Benutzeroberfläche von AEM zurückzukehren.

**Übersetzungs-HTTP-API**

Die AEM-Übersetzungs-HTTP-REST-API, die sich seit einiger Zeit im Early-Adopter-Modus befindet, ist jetzt allgemein verfügbar. Die Dokumentation finden Sie [hier.](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/translation/) Die -API ermöglicht die Automatisierung erforderlicher Schritte im Übersetzungs-Management-Prozess für Inhalte in AEM.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in AEM Assets {#new-features-assets}

**Neue Verpackungsstruktur in Dynamic Media**

Eine überarbeitete Verpackungsstruktur in Dynamic Media ist jetzt verfügbar, die besser auf Markterwartungen ausgerichtet ist und Tracking unterstützt. Die neue Verpackungsstruktur umfasst:

* Dynamic Media Prime, einschließlich Dynamic Media mit OpenAPIs und Videos, um die Bereitstellung zu verbessern.

* Mit Dynamic Media Ultimate werden Bereitstellungs- und Umwandlungsfunktionen hinzugefügt, um höhere Nutzungsanforderungen zu erfüllen.

Sie müssen über Assets as a Cloud Service Prime oder Ultimate verfügen, um von der neuen Verpackungsstruktur zu profitieren.

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion soll die Barrierefreiheit und das Anwendererlebnis verbessern, indem akkurate Untertitel bereitgestellt werden. Untertitel werden aus dem Originalaudio, zusätzlichen Audiospuren oder Untertiteln generiert, die auf der Registerkarte „Beschriftungen und Audiospuren“ auf der Seite mit den Videoeigenschaften bereitgestellt werden. Es werden mehr als 60 Sprachen unterstützt. Die Untertitel können dabei vor der Veröffentlichung des Videos überprüft und in einer Vorschau angezeigt werden.

**Anpassen der Suchfilter**

Benutzerdefinierte Suchfilter verbessern die Genauigkeit und Effizienz beim Auffinden relevanter Informationen. Sie ermöglichen spezifischere Suchvorgänge, bei denen Daten nach bestimmten Attributen wie Marke, Produkt, Kategorie oder anderen wichtigen Identifikatoren gefiltert werden. Dies führt zu einer besseren Organisation sowie einem reduziertem Zeitaufwand, weil keine irrelevanten Ergebnisse durchgesehen werden müssen, und ermöglicht eine schnellere Entscheidungsfindung. Darüber hinaus wird Skalierbarkeit unterstützt, da in großen Datensätzen leichter navigiert und eine einfachere Analyse durchgeführt werden kann.

![Anpassen von Suchfiltern](/help/assets/assets/custom-search-filters.png)

### Early-Access-Funktionen in Content Hub {#early-access-content-hub}

Mit Content Hub können Sie nun neben den bereits vorhandenen statischen Ausgabedarstellungen auch dynamische Ausgabedarstellungen sowie Ausgabedarstellungen für den intelligenten Zuschnitt anzeigen und herunterladen. Als Content Hub-Admin können Sie auch über die Benutzeroberfläche „Konfiguration“ die Verfügbarkeit dieser Ausgabedarstellungen für Benutzende konfigurieren.

![Dynamische Ausgabedarstellungen](/help/assets/assets/download-single-asset-renditions-dynamic.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### HTML-E-Mail-Vorlagen in adaptiven Formularen

Adaptive Formulare ermöglichen die Verwendung von [HTML-E-Mail-Vorlagen](/help/forms/html-email-templates-in-adaptive-forms.md). Mit HTML-E-Mail-Vorlagen können Sie beim Übermitteln eines Formulars umfangreiche, personalisierte und visuell ansprechende E-Mails senden. Diese E-Mails können mit Formulardaten angepasst und mit verschiedenen E-Mail-Tags, wie Bildern und Links, erweitert werden. Bei adaptiven Formularen können Sie entweder eine Datei mit einer HTML-Vorlage hochladen oder diese Vorlagen mit einem Texteditor erstellen.

![HTML-E-Mail-Vorlagen](/help/forms/assets/html-email.png)

#### Erweiterte Cloud-Speicher-Unterstützung: Direkter PDF-Upload in Azure Blob Storage

Mit den APIs zur Dokumenterstellung in AEM Forms können Sie nun [generierte PDF-Dokumente direkt in Azure Blob Storage hochladen](/help/forms/early-access-ea-features.md#doc-generation-api). Diese Erweiterung optimiert Speicherung und Abruf und verbessert so die Effizienz und Integration mit Cloud-Workflows.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Java 21-Unterstützung {#java21}

Wie in den Versionshinweisen von Januar erwähnt, können Sie nun mit Java 21 Code erstellen. Diese Version umfasst neue Funktionen (z. B. Musterabgleich für Switch-Anweisungen, versiegelte Klassen) und Leistungsverbesserungen. Java 17-Builds werden jetzt ebenfalls unterstützt. Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support). 

Die leistungsfähigere Java 21 **Runtime** wird automatisch bereitgestellt, wenn ein Java 17- oder Java 21-Build erkannt wird. Wir empfehlen jedoch auch, sich für Umgebungen, die mit Java 11 erstellt wurden, für die Java 21 Runtime anzumelden. Senden Sie hierzu einfach eine E-Mail an [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Erfahren Sie mehr zu den [Java 21 Runtime-Anforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Im Februar wurde Java 21 **Runtime** in Entwicklungs-/RDE-Umgebungen bereitgestellt (mit Ausnahme der bereits mit Java 17 oder 21 erstellten Umgebungen, die bereits über die Java 21 Runtime verfügen). Java 21 wird im April auf Staging-/Produktionsumgebungen angewendet.

### Edge-Computing – Einladung zum Feedback! {#edge-computing-feedback}

Edge-Computing bringt die Datenverarbeitung näher an den Browser heran, was Vorteile bietet, darunter eine reduzierte Latenz. Adobe würde gerne von Ihnen hören, ob Sie diese Technologie als nützlich für AEM Publish Delivery- und Edge Delivery Services-Projekte erachten. Teilen Sie uns bitte außerdem mit, wofür Sie sie voraussichtlich verwenden würden. Diese Information hilft uns bei der Gestaltung der Produkt-Roadmap. 

Verschiedene mögliche Anwendungsfälle:
* Authentifizierung mit einer IdP, um Zugriff auf Inhalte zu erhalten
* Rendern dynamischer (personalisierter, lokalisierter) Inhalte basierend auf Geolocation, Gerätetyp, Benutzerattributen usw.
* Erweiterte Bildbearbeitung
* Middleware zwischen dem CDN und einem Ursprung
* Eine Ebene zwischen dem Browser und eines Dritteranbieter-APIs, möglicherweise zur Neuformatierung der API-Antwort
* Aggregieren von Daten aus verschiedenen Quellen, um dem Client-Browser das Rendern zu erleichtern

Schreiben Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit Fragen und Kommentaren!

### OpenAPI-basierte APIs – Early-Adopter-Programm {#open-apis-earlyadopter}

Entwickelnde können AEM as a Cloud Service-Funktionen in ihre eigenen Anwendungen und Tools integrieren. Neue AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation, weil sie konsistent, gut dokumentiert und benutzerfreundlich sein sollen. Anmeldeinformationen für Endpunkte, für die eine Authentifizierung erforderlich ist, werden durch Erstellen von Adobe Developer Console-Projekten generiert.

Erfahren Sie mehr über [OpenAPI-basierte AEM-APIs](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [End-to-End-Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) aus, in dem Konfiguration und Verwendung veranschaulicht werden.

Konkret sind die unten aufgeführten API-Endpunkte im Rahmen eines Early-Adopter-Programms verfügbar. Wenn Sie daran interessiert sind, senden Sie eine E-Mail an [aem-apis@adobe.com](mailto:aem-apis@adobe.com), in der Sie beschreiben, wie Sie die API-Endpunkte verwenden möchten.

* [Sites-Inhaltsfragmente-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de)
* [Assets-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* Sites- und Assets-Ordner-APIs
* [Forms-Kommunikationen-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Neue AEM Developer Console (öffentliche Beta-Version) {#aem-developer-console-beta}

Probieren Sie die neu gestaltete [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, die ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem in der aktuellen AEM Developer Console auf die Schaltfläche *Neue Konsole verfügbar* geklickt wird. Adobe freut sich über Feedback, das Sie per E-Mail an [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com) senden können.

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2025-releases/2502-release/whats-new-2025-02-0).

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
