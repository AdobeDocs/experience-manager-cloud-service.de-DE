---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: bbf66195593032eb2ccf073ec78685c9d9726235
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 65%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.3.0) ist der Freitag, 27. März 2025. Die nächste Version mit neuen Funktionen (2025.4.0) ist für den Freitag, 24. April 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in Dynamic Media {#new-features-dynamic-media}

**Unterstützung von langen Formularen für Videos, die mit Dynamic Media mit Open API bereitgestellt werden**

Dynamic Media mit OpenAPI unterstützt jetzt Videos in langer Form. Die Videos in langer Form unterstützen bis zu 50 GB und 2 Stunden.

### Dynamic Media Classic {#dmc}

<!-- CARRY OVER TO APRIL 2025 RELEASE NOTES -->

Die Registerkarte Bandbreite im Reporting-Dashboard von Dynamic Media Classic wird seit April 2025 nicht mehr unterstützt.

Siehe [Bandbreite und Speicher, Berichtstypen](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/setup/administration-setup#types-of-reports).


## Neue Funktionen in der Assets-Ansicht {#new-features-assets-view}


**Unterstützung für Root-Tags**

AEM Assets unterstützt jetzt die Zuordnung einer Tag-Eigenschaft in einem Metadatenformular zu benutzerdefinierten Metadaten. Darüber hinaus können Sie als Administrator die Verfügbarkeit von Tags für Benutzer einschränken, indem Sie den Zugriff auf ein bestimmtes Root-Tag und die Tags beschränken, die unter dem Root-Tag vorhanden sind.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### HTML-E-Mail-Vorlagen in adaptiven Formularen

Adaptive Formulare ermöglichen die Verwendung von [HTML-E-Mail-Vorlagen](/help/forms/html-email-templates-in-adaptive-forms.md). Mit HTML-E-Mail-Vorlagen können Sie beim Übermitteln eines Formulars umfangreiche, personalisierte und visuell ansprechende E-Mails senden. Diese E-Mails können mit Formulardaten angepasst und mit verschiedenen E-Mail-Tags, wie Bildern und Links, erweitert werden. Bei adaptiven Formularen können Sie entweder eine Datei mit einer HTML-Vorlage hochladen oder diese Vorlagen mit einem Texteditor erstellen.

![HTML-E-Mail-Vorlagen](/help/forms/assets/html-email.png)

#### Erweiterte Cloud-Speicher-Unterstützung: Direkter PDF-Upload in Azure Blob Storage

Mit AEM Forms Document Generation-APIs können Sie jetzt [generierte PDF-Dokumente direkt ](/help/forms/early-access-ea-features.md#doc-generation-api) Azure Blob Storage hochladen. Diese Erweiterung optimiert Speicherung und Abruf und verbessert so die Effizienz und Integration mit Cloud-Workflows.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Java 21-Unterstützung {#java21}

Ab der Version Januar können Sie Code mit Java 21 und Java 17 erstellen. Sie erhalten Zugriff auf neue Funktionen wie Mustervergleich, versiegelte Klassen und verschiedene Leistungsverbesserungen. Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie im Artikel [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) .

Die leistungsfähigere Java 21-Version **runtime** wird automatisch bereitgestellt, wenn ein Java 17- oder Java 21-Build erkannt wird. Adobe empfiehlt jedoch auch, den Opt-in für die Java 21-Laufzeitumgebung für Umgebungen, die mit Java 11 erstellt wurden, per E-Mail an [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) durchzuführen. Erfahren Sie mehr zu den [Java 21 Runtime-Anforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Die Java 21 **Laufzeitumgebung** wurde im Februar in Ihren Entwicklungs-/RDE-Umgebungen bereitgestellt. Sie wird am 28. **und 29.** auf Ihre Staging-/Produktionsumgebungen angewendet. Beachten Sie, **Erstellen von Code** mit Java 21 (oder Java 17) unabhängig von der Java 21-Laufzeit ist - Sie müssen explizit Schritte zum Erstellen von Code mit Java 21 (oder Java 17) ausführen.

### AEM-Protokollweiterleitung an weitere Ziele - Beta-Programm {#log-forwarding-earlyadopter}

Jetzt in der Beta-Phase können Sie AEM-Protokolle an New Relic (mithilfe von HTTPS), Amazon S3 und Sumo Logic weiterleiten. Beachten Sie, dass AEM-Protokolle (einschließlich Apache/Dispatcher) unterstützt werden, jedoch keine CDN-Protokolle. Zugriff per E-Mail ](mailto:aemcs-logforwarding-beta@adobe.com)0}aemcs-logforwarding-beta@adobe.com&quot;.[

Während Protokolle von Cloud Manager heruntergeladen werden können, ist es für viele Unternehmen von Vorteil, diese Protokolle an ein bevorzugtes Protokollierungsziel zu streamen. AEM unterstützt bereits die (GA) AEM- und CDN-Protokollweiterleitung an Azure Blob Storage, Datadog, HTTPS, Elasticsearch (und OpenSearch) und Splunk. Diese Funktion wird im Selbstbedienungsmodus konfiguriert und mithilfe der Konfigurations-Pipeline bereitgestellt.

Weitere Informationen finden Sie in [ Dokumentation zur ](/help/implementing/developing/introduction/log-forwarding.md).

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

Erfahren Sie mehr über [OpenAPI-basierte AEM-APIs](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [End-to-End-Tutorial](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) aus, in dem Konfiguration und Verwendung veranschaulicht werden.

Konkret sind die unten aufgeführten API-Endpunkte im Rahmen eines Early-Adopter-Programms verfügbar. Wenn Sie daran interessiert sind, senden Sie eine E-Mail an [aem-apis@adobe.com](mailto:aem-apis@adobe.com), in der Sie beschreiben, wie Sie die API-Endpunkte verwenden möchten.

* [Sites-Inhaltsfragmente-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de)
* [Assets-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [Sites- und Assets-Ordner-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [Forms-Kommunikationen-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Neue AEM Developer Console (öffentliche Beta-Version) {#aem-developer-console-beta}

Probieren Sie die neu gestaltete [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, die ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem in der aktuellen AEM Developer Console auf die Schaltfläche *Neue Konsole verfügbar* geklickt wird. Adobe freut sich über Feedback, das Sie per E-Mail an [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com) senden können.

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2025-releases/2502-release/whats-new-2025-02-0).

<!-- THE FOLLOWING URL WAS USED ABOVE BUT IT WAS 404. IT WAS REPLACED WITH THE URL ABOVE 
(https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0). -->

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
