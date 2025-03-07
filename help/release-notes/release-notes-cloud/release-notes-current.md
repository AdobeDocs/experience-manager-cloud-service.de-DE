---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 896a2927c0f5733ab23ca9f6c9e975f8388daff9
workflow-type: tm+mt
source-wordcount: '1419'
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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.2.0) ist der Mittwoch, 4. März 2025. Die nächste Version (2025.3.0) ist für den Freitag, 27. März 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in AEM Sites {#new-features-sites}

**Automatisches Tagging von Inhaltsfragmenten**

Beim Erstellen von Inhaltsfragmenten ist es jetzt möglich, automatisch Tags zu erben, die dem Inhaltsmodell zugewiesen wurden. Dies ermöglicht eine leistungsstarke automatische Klassifizierung von Inhalten, die in Inhaltsfragmenten gespeichert sind.

**Unterstützung der Inhaltsfragment-UUID**

Die Unterstützung der Inhaltsfragment-UUID ist jetzt allgemein verfügbar. Die neue Funktion ändert nicht das pfadbasierte Verhalten von Vorgängen innerhalb von AEM, z. B. Verschieben, Umbenennen, Rollout, bei denen Pfade automatisch angepasst werden. Sie kann jedoch die externe Verwendung von Inhaltsfragmenten vereinfachen und stabiler gestalten, insbesondere wenn GraphQL-Abfragen verwendet werden, die direkt einzelne Fragmente mit ByPath-Abfragen ansprechen. Solche Abfragen können fehlschlagen, wenn sich ein Fragmentpfad ändert. Bei Verwendung des neuen Abfragetyps ById bleibt die Abfrage jetzt stabil, da sich die UUID eines Fragments in Fällen, in denen Pfade dies tun, nicht ändert.

**Dynamic Media mit OpenAPI-Unterstützung im Inhaltsfragment-Editor und in GraphQL**

Assets, die in anderen AEM as a Cloud Service-Programmen als Inhaltsfragmenten gespeichert sind und die mit der neuen Dynamic Media-Funktion mit OpenAPI-Funktion aktiviert sind, können jetzt in Inhaltsfragmenten verwendet werden. Mit der Bildauswahl im neuen Inhaltsfragment-Editor können jetzt „Remote“-Repositorys als Quelle für Bild-Assets ausgewählt werden, auf die im Fragment verwiesen werden soll. Und bei der Bereitstellung solcher Inhaltsfragmente mit AEM GraphQL enthält die JSON-Antwort jetzt die erforderlichen Eigenschaften für Remote-Assets (assetId, repositoryId), damit Client-Anwendungen entsprechende Dynamic Media-Dateien mit OpenAPI-URLs erstellen können, um das Bild abzurufen.

**Übersetzungs-HTTP-API**

Die AEM Translation HTTP REST-API, die sich seit einiger Zeit im Early-Adopter-Modus befindet, ist jetzt allgemein verfügbar. Die Dokumentation finden Sie [hier](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/translation/). Die -API ermöglicht die Automatisierung erforderlicher Schritte im Übersetzungs-Management-Prozess für Inhalte in AEM.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in AEM Assets {#new-features-assets}

**Neue Paketstruktur in Dynamic Media**

Eine überarbeitete Dynamic Media-Verpackungsstruktur ist jetzt verfügbar, um sie besser an die Markterwartungen anzupassen und das Tracking zu unterstützen. Die neue Verpackungsstruktur umfasst:

* Dynamic Media Prime, einschließlich Dynamic Media mit OpenAPIs und Videos, um die Bereitstellung zu verbessern.

* Mit Dynamic Media Ultimate werden Bereitstellungs- und Umwandlungsfunktionen hinzugefügt, um höhere Nutzungsanforderungen zu erfüllen.

Sie müssen über Assets as a Cloud Service Prime oder Ultimate verfügen, um von der neuen Verpackungsstruktur zu profitieren.

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion verbessert die Barrierefreiheit und das Benutzererlebnis, indem genaue Beschriftungen bereitgestellt werden. Untertitel werden aus dem Originalaudio generiert, zusätzliche Audiospuren oder zusätzliche Untertitel werden auf der Registerkarte „Untertitel und Audio“ auf der Seite mit den Videoeigenschaften bereitgestellt. Es werden mehr als 60 Sprachen unterstützt. Die Untertitel können dabei vor der Veröffentlichung des Videos überprüft und in einer Vorschau angezeigt werden.

**Anpassen von Suchfiltern**

Benutzerdefinierte Suchfilter verbessern die Genauigkeit und Effizienz beim Auffinden relevanter Informationen. Sie ermöglicht eine besser auf die Bedürfnisse zugeschnittene Suche, bei der Daten nach bestimmten Attributen wie Marke, Produkt, Kategorie oder anderen Schlüsselkennungen gefiltert werden. Dies verbessert die Organisation, verringert die Zeit, die mit dem Durchsuchen irrelevanter Ergebnisse verbracht wird, und ermöglicht eine schnellere Entscheidungsfindung. Es unterstützt auch die Skalierbarkeit, da große Datensätze leichter navigiert und analysiert werden können.

![Anpassen von Suchfiltern](/help/assets/assets/custom-search-filters.png)


### Early Access-Funktionen in Content Hub {#early-access-content-hub}

Mit Content Hub können Sie jetzt neben den bereits vorhandenen statischen Ausgabedarstellungen auch dynamische und intelligente Zuschnittausgabedarstellungen anzeigen und herunterladen. Als Content Hub-Administrator können Sie auch über die Benutzeroberfläche „Konfiguration“ die Verfügbarkeit dieser Ausgabedarstellungen für Benutzerinnen und Benutzer konfigurieren.

![Dynamische Ausgabedarstellungen](/help/assets/assets/download-single-asset-renditions-dynamic.png)



## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### HTML-E-Mail-Vorlagen in Adaptive Forms

Adaptive Forms ermöglicht die Verwendung von [HTML-E-Mail-Vorlagen](/help/forms/html-email-templates-in-adaptive-forms.md). Mit HTML-E-Mail-Vorlagen können Sie beim Übermitteln eines Formulars umfangreiche, personalisierte und visuell ansprechende E-Mails senden. Diese E-Mails können mit Formulardaten angepasst und mit verschiedenen E-Mail-Tags, wie Bildern und Links, erweitert werden. Bei adaptiven Formularen können Sie entweder eine Datei mit einer HTML-Vorlage hochladen oder diese Vorlagen mit einem Texteditor erstellen.

![HTML-E-Mail-Vorlagen](/help/forms/assets/html-email.png)

#### Erweiterte Cloud-Speicher-Unterstützung: Direkter PDF-Upload in Azure Blob Storage

Mit den APIs zur Dokumenterstellung in AEM Forms können Sie jetzt [generierte PDF-Dokumente direkt ](/help/forms/early-access-ea-features.md#doc-generation-api) Azure Blob Storage hochladen. Diese Erweiterung optimiert Speicherung und Abruf und verbessert so die Effizienz und Integration mit Cloud-Workflows.


## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Java 21-Unterstützung {#java21}

Wie in den Versionshinweisen vom Januar erwähnt, können Sie jetzt Code mit Java 21 erstellen, der neue Funktionen (z. B. Mustervergleich für Switch-Anweisungen, versiegelte Klassen) und Leistungsverbesserungen enthält. Java 17-Builds werden ebenfalls neu unterstützt. Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support). 

Die leistungsfähigere Java 21 **Runtime** wird automatisch bereitgestellt, wenn ein Java 17- oder Java 21-Build erkannt wird. Wir empfehlen jedoch auch, sich für Umgebungen, die mit Java 11 erstellt wurden, für die Java 21 Runtime anzumelden. Senden Sie hierzu einfach eine E-Mail an [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Erfahren Sie mehr zu den [Java 21 Runtime-Anforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Im Februar wurde Java 21 **runtime** in Entwicklungs-/RDE-Umgebungen bereitgestellt (abgesehen von den bereits mit Java 17 oder 21 erstellten Umgebungen, die bereits Java 21-Runtime aufweisen). Java 21 wird im April auf Staging-/Produktionsumgebungen angewendet.

### Edge-Computing – Einladung zum Feedback! {#edge-computing-feedback}

Edge-Computing bringt die Datenverarbeitung näher an den Browser heran, was Vorteile bietet, darunter eine reduzierte Latenz. Adobe möchte wissen, ob diese Technologie für die AEM-Veröffentlichungsbereitstellung und Edge Delivery Services-Projekte nützlich ist. Teilen Sie uns außerdem mit, was Sie sich vorstellen, um es als Input für die Produkt-Roadmap zu verwenden.

Einige mögliche Anwendungsfälle:
* Authentifizierung mit einer ID, um Zugriff auf Inhalte zu erhalten
* Rendern dynamischer (personalisierter, lokalisierter) Inhalte basierend auf Geolokalisierung, Gerätetyp, Benutzerattributen usw.
* Erweiterte Bildbearbeitung
* Middleware zwischen dem CDN und einem Ursprung
* Eine Ebene zwischen dem Browser und einer API eines Drittanbieters, möglicherweise zur Neuformatierung der API-Antwort
* Aggregieren von Daten aus verschiedenen Quellen, um dem Client-Browser das Rendern zu erleichtern

Schreiben Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit Fragen und Kommentaren!

### OpenAPI-basierte APIs – Early-Adopter-Programm {#open-apis-earlyadopter}

Entwickelnde können AEM as a Cloud Service-Funktionen in ihre eigenen Anwendungen und Tools integrieren. Neue AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation, weil sie konsistent, gut dokumentiert und benutzerfreundlich sein sollen. Anmeldeinformationen für Endpunkte, für die eine Authentifizierung erforderlich ist, werden durch Erstellen von Adobe Developer Console-Projekten generiert.

Erfahren Sie mehr über [OpenAPI-basierte AEM-APIs](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [End-to-End-Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) aus, in dem Konfiguration und Verwendung veranschaulicht werden.

Konkret sind die unten aufgeführten API-Endpunkte im Rahmen eines Early-Adopter-Programms verfügbar. Wenn Sie daran interessiert sind, senden Sie eine E-Mail an [aem-apis@adobe.com](mailto:aem-apis@adobe.com), in der Sie beschreiben, wie Sie die API-Endpunkte verwenden möchten.

* [Sites-Inhaltsfragmente-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de)
* [Assets-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [Sites- und Assets-Ordner-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [Forms-Kommunikationen-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Neue AEM Developer Console (öffentliche Beta-Version) {#aem-developer-console-beta}

Probieren Sie die neu gestaltete [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, die ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem in der aktuellen AEM Developer Console auf die Schaltfläche *Neue Konsole verfügbar* geklickt wird. Adobe freut sich über Feedback, das Sie per E-Mail an [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com) senden können.

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0).

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
