---
title: Versionshinweise für Version 2025.1.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2025.1.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 085629bf-fb24-4511-af6c-bbbeedcb6b98
source-git-commit: fecbebde808c545a84889da5610a79c088f2f459
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 92%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2025.1.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2025.1.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2023 oder 2024 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.1.0) ist der 30. Januar 2025. Die nächste Version (2025.2.0) ist für den 4. März 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video zur Versionsübersicht von Januar 2025 an, das eine Zusammenfassung der Funktionen gibt, die in Version 2025.1.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3456072?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**Inhaltsfragment-Editor – Kommentarfunktion nun allgemein verfügbar**

Die neue und modernisierte Kommentarfunktion im Inhaltsfragment-Editor von AEM ermöglicht beim Erstellen von AEM-Inhaltsfragmenten eine einfache Zusammenarbeit mit Kolleginnen und Kollegen.
[Weitere Informationen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/authoring?#commenting-on-your-fragment).

**Inhaltsfragmenteditor und Admin-Benutzeroberflächen: AEM as a Cloud Service-Versionsunterstützung aktualisiert**

Die unterstützte AEM as a Cloud Service-Mindestversion für neue Admin- und Editor-Benutzeroberflächen für Inhaltsfragmente lautet nun 2023.8.13099. Frühere Versionen aus der Zeit vor der allgemeinen Verfügbarkeit der neuen Benutzeroberflächen werden nicht mehr unterstützt.

### Early-Adopter-Programm {#sites-early-adopter}

**Verbesserte Inhaltsfragmente**

Die [Referenzierung von Inhaltsfragmenten mit eindeutigen ID-basierten Referenzen](/help/headless/graphql-api/uuid-reference-upgrade.md) wurde verbessert, um sicherzustellen, dass GraphQL-Abfragen für einzelne Inhaltsfragmente stabil bleiben können, selbst wenn das Fragment an einen anderen Speicherort verschoben wurde. Dies ist jetzt mit „ByID“-Abfragen möglich. Während sich Pfade ändern können, was zu Fehlern in „ByPath“-Abfragen führen kann, sind UUIDs stabil. Die neuen IDs können auch als Eigenschaften in einer Abfrage oder einer anderen anwendbaren API-Anfrage zurückgegeben werden. Aktuelle Einschränkung (2025.1): Seitenverweise werden noch nicht mit eindeutigen IDs unterstützt. Wenn Seiten in Inhaltsfragmenten referenziert werden, sollte diese Funktion nicht verwendet werden. Diese Einschränkung soll mit der nächsten AEM as a Cloud Service-Version aufgehoben werden.

**AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten**

Die [AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten](/help/headless/aem-content-fragment-delivery-with-openapi.md) ist nun für AEM as a Cloud Service verfügbar.

### Veraltete Funktionen {#sites-deprecated}

#### SPA-Editor {#spa-editor}

Der [SPA-Editor](/help/implementing/developing/hybrid/introduction.md) wird ab Version 2025.1.0 für neue Projekte nicht mehr unterstützt. Für bestehende Projekte wird er weiterhin unterstützt, sollte allerdings nicht mehr für neue Projekte verwendet werden.

Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind nun:

* der [universelle Editor](/help/edge/wysiwyg-authoring/authoring.md) zur visuellen Bearbeitung
* der [Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) zur formularbasierten Bearbeitung

#### PWA-Funktionen {#pwa-features}

[Die Funktionen der Progressive Web App (PWA](/help/sites-cloud/authoring/sites-console/enable-pwa.md) für AEM Sites werden jetzt für neue Projekte ab Version 2025.1.0 nicht mehr unterstützt. Diese Funktion wird für bestehende Projekte weiterhin unterstützt, sollte jedoch nicht für neue Projekte verwendet werden

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in AEM Assets {#new-features-assets}

**Dynamic Media-Bereitstellungsberichte**

Verschaffen Sie sich Erkenntnisse zu den mit Dynamic Media bereitgestellten Assets, darunter zur Anzahl der Bereitstellungen auf Asset-Ebene sowie zu Referrer-Details, Asset-Pfaden in AEM Assets und eindeutigen Asset-IDs. Generieren Sie Berichte für alle Assets im AEM Assets-Repository oder für bestimmte Ordnerhierarchien. Mit diesen Erkenntnissen können Sie den ROI der bereitgestellten Assets messen, die Kanalleistung bewerten und fundierte Entscheidungen für das Asset-Management treffen.

![Dynamische Ausgabedarstellungen](/help/assets/assets/referrer.png)

**Mehrere Audiospuren und mehrfache Untertitel in Dynamic Media**

[Unterstützung für mehrfache Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) – Sie können nun ganz einfach mehrfache Untertitel und mehrere Audiospuren zu einem primären Video hinzufügen.  Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

**Unterstützung für Dynamic Adaptive Streaming über HTTP**

Neue Protokollunterstützung (DASH – Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF) eingeführt:

* Adaptives Streaming (DASH/HLS) sorgt für ein besseres Zuschauererlebnis bei der Videoanzeige.

* DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weithin verwendet


**Erneutes Verarbeiten von Assets**

Die Assets-Ansicht unterstützt nun die erneute Verarbeitung von Assets, die in einem Ordner verfügbar sind. Sie können entweder die Option **Vollständiger Prozess** auswählen oder erweiterte Optionen wie „Standarddarstellungen für die Vorschau“, „Metadaten“, „Nachbearbeitungs-Workflow“ und „Verarbeitungsprofil“ verwenden.

### Early-Access-Funktionen in AEM Assets {#early-access-features-assets}

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion hat das Ziel, die Barrierefreiheit und das Benutzererlebnis zu verbessern, indem akkurate Untertitel in Echtzeit bereitgestellt werden. Untertitel werden aus dem Originalaudio, zusätzlichen Audiospuren oder Untertiteln generiert, die auf der Registerkarte „Beschriftungen und Audiospuren“ auf der Seite mit den Videoeigenschaften bereitgestellt werden. Es werden mehr als 60 Sprachen unterstützt. Die Untertitel können dabei vor der Veröffentlichung des Videos überprüft und in einer Vorschau angezeigt werden.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in AEM Forms {#forms-new-features}

* **Veröffentlichung verwalten**: Sie können den Workflow [Veröffentlichung verwalten](/help/forms/manage-publication.md#publish-forms-using-the-manage-publication-option) verwenden, um Formulare in Umgebungen zu veröffentlichen oder die Veröffentlichung rückgängig zu machen, normalerweise von der Autoreninstanz bis zur Veröffentlichungs- und Vorschauinstanz. Er ermöglicht es Benutzenden, Inhalte zu veröffentlichen, ihre Veröffentlichung rückgängig zu machen oder ihre Veröffentlichung effizient zu planen.

* **[Automatisches Speichern eines Entwurfs für auf Kernkomponenten basierende adaptive Formulare](/help/forms/save-core-component-based-form-as-draft.md)**: Benutzende können jetzt von einer automatischen Speicherfunktion profitieren, mit der ein teilweise ausgefülltes Formular automatisch als Entwurf gespeichert wird. Sie können später zurückkehren, um das Ausfüllen des Formulars auf demselben oder einem anderen Gerät abzuschließen. Diese Funktion verbessert die Konversionsraten für Unternehmen, indem Formularabbrüche reduziert werden, da Benutzende nicht mit dem Ausfüllen von Formularen von Anfang an beginnen müssen.

* **[Verbesserungen des Regeleditors](/help/forms/invoke-service-enhancements-rule-editor.md)**: Für adaptive Forms, die auf Kernkomponenten basieren, können Sie die Ausgabe von „Service aufrufen“ verwenden, um Dropdown-Optionen auszufüllen und wiederholbare oder einzelne Bedienfelder festzulegen. Darüber hinaus kann diese Ausgabe zur Validierung anderer Felder verwendet werden.

* **[Verbessern des Anwendererlebnisses mit Navigations-Schaltflächen in Bedienfeld-Layouts](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)**: Sie können Ihren Bedienfeld-Layouts jetzt Navigations-Schaltflächen hinzufügen, z. B. horizontale Registerkarten, vertikale Registerkarten, Akkordeons oder Assistent. Diese Schaltflächen verbessern das Anwendererlebnis, indem sie die Übergänge zwischen Bedienfeldern vereinfachen und sich auf das ausgewählte Bedienfeld konzentrieren.


### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### [HTML-E-Mail-Vorlagen in adaptivem Forms](/help/forms/html-email-templates-in-adaptive-forms.md)

Adaptive Forms ermöglicht die Verwendung von HTML-E-Mail-Vorlagen. Mit HTML-E-Mail-Vorlagen können Sie beim Übermitteln eines Formulars umfangreiche, personalisierte und visuell ansprechende E-Mails senden. Diese E-Mails können mit Formulardaten angepasst und mit verschiedenen E-Mail-Tags, wie Bildern und Links, erweitert werden. Bei adaptiven Formularen können Sie entweder eine Datei mit einer HTML-Vorlage hochladen oder diese Vorlagen mit einem Texteditor erstellen.

![HTML-E-Mail-Vorlagen](/help/forms/assets/html-email.png)

#### Erweiterte Cloud-Speicher-Unterstützung: Direkter PDF-Upload in Azure Blob Storage

AEM Forms Document Generation-APIs unterstützen jetzt das direkte Hochladen generierter PDF-Dokumente in Azure Blob Storage. Diese Erweiterung optimiert Speicherung und Abruf und verbessert so die Effizienz und Integration mit Cloud-Workflows.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Java 21-Unterstützung {#java21}

Sie können nun mit Java 21 Code erstellen. Diese Version umfasst neue Funktionen (z. B. Musterabgleich für Switch-Anweisungen, versiegelte Klassen) und Leistungsverbesserungen. Java 17-Builds werden jetzt ebenfalls unterstützt. Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support). 

Die leistungsfähigere Java 21 **Runtime** wird automatisch bereitgestellt, wenn ein Java 17- oder Java 21-Build erkannt wird. Wir empfehlen jedoch auch, sich für Umgebungen, die mit Java 11 erstellt wurden, für die Java 21 Runtime anzumelden. Senden Sie hierzu einfach eine E-Mail an [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Erfahren Sie mehr zu den [Java 21 Runtime-Anforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Die Java 21 **Runtime** wird schrittweise in **allen** Umgebungen bereitgestellt (mit Ausnahme der bereits mit Java 17 oder 21 erstellten Umgebungen, die bereits über die Java 21 Runtime verfügen). Den Anfang machen Sandboxes und (schnelle) Entwicklungsumgebungen im Februar, im April folgen dann die Staging-/Produktionsumgebungen.

### Unterstützung für Konfigurations-Pipelines durch Sandbox-Programme {#sandbox-config-pipelines}

Sandbox-Programme unterstützen nun Konfigurations-Pipelines, die in Cloud Manager so konfiguriert werden können, dass sie in Git persistierte YAML-Dateien bereitstellen.

[Erfahren Sie mehr](/help/operations/config-pipeline.md) über Konfigurations-Pipelines, die die Konfiguration von CDN, Protokollweiterleitung und Wartungsaufgaben für die Versionsbereinigung/Audit-Protokollbereinigung ermöglichen.

### OpenAPI-basierte APIs – Early-Adopter-Programm {#open-apis-earlyadopter}

Entwickelnde können AEM as a Cloud Service-Funktionen in ihre eigenen Anwendungen und Tools integrieren. Neue AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation, weil sie konsistent, gut dokumentiert und benutzerfreundlich sein sollen. Anmeldeinformationen für Endpunkte, für die eine Authentifizierung erforderlich ist, werden durch Erstellen von Adobe Developer Console-Projekten generiert.

Erfahren Sie mehr über [OpenAPI-basierte AEM-APIs](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [End-to-End-Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) aus, in dem Konfiguration und Verwendung veranschaulicht werden.

Konkret sind die unten aufgeführten API-Endpunkte im Rahmen eines Early-Adopter-Programms verfügbar. Wenn Sie daran interessiert sind, senden Sie eine E-Mail an [aem-apis@adobe.com](mailto:aem-apis@adobe.com), in der Sie beschreiben, wie Sie die API-Endpunkte verwenden möchten.

* [Sites-Inhaltsfragmente-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de)
* [Assets-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* Sites- und Assets-Ordner-APIs
* [Forms-Kommunikationen-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge-Computing – Einladung zum Feedback! {#edge-computing-feedback}

Edge-Computing bringt die Datenverarbeitung näher an den Browser heran, was Vorteile bietet, darunter eine reduzierte Latenz. Adobe würde gerne von Ihnen hören, ob Sie diese Technologie als nützlich für AEM Publish Delivery- und Edge Delivery Services-Projekte erachten. Teilen Sie uns bitte außerdem mit, wofür Sie sie voraussichtlich verwenden würden. Diese Information hilft uns bei der Gestaltung der Produkt-Roadmap. Schreiben Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit Fragen und Kommentaren!

### Neue AEM Developer Console (öffentliche Beta-Version) {#aem-developer-console-beta}

Probieren Sie die neu gestaltete [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, die ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem in der aktuellen AEM Developer Console auf die Schaltfläche *Neue Konsole verfügbar* geklickt wird. Adobe freut sich über Feedback, das Sie per E-Mail an [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com) senden können.

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2412-release/fixed-issues-2024-12-0).

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
