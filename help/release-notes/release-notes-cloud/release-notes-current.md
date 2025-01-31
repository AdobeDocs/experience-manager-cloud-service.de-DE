---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 190e68ebcd3c2a7ba7b995690c802a04728e6962
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 42%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.1.0) ist der Freitag, 30. Januar 2025. Die nächste Version (2025.2.0) ist für den Freitag, 27. Februar 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the January 2025 Release Overview video for a summary of the features added in the 2025.1.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**Kommentare zum Inhaltsfragment-Editor jetzt allgemein verfügbar**

Sie können bei der Erstellung von AEM-Inhaltsfragmenten einfach mit Kollegen zusammenarbeiten, indem Sie den neuen und modernisierten Kommentardienst im AEM-Inhaltsfragment-Editor verwenden.
[Weitere Informationen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/authoring?#commenting-on-your-fragment).

**Inhaltsfragment-Editor und Admin-Benutzeroberflächen, aktualisierte AEM as a Cloud Service-Versionsunterstützung**

Die mindestens unterstützte AEM as a Cloud Service-Version für neue Administrator- und Editor-Benutzeroberflächen für Inhaltsfragmente ist jetzt 2023.8.13099. Frühere Versionen von vor der allgemeinen Verfügbarkeit der neuen Benutzeroberflächen werden nicht mehr unterstützt

### Early-Adopter-Programm {#sites-early-adopter}

**Verbesserte Inhaltsfragmente**

Verbesserte [Inhaltsfragmentverweise mit eindeutigen ID-basierten Verweisen](/help/headless/graphql-api/uuid-reference-upgrade.md), um sicherzustellen, dass GraphQL-Abfragen für einzelne Inhaltsfragmente stabil bleiben können, selbst wenn das Fragment an einen anderen Speicherort verschoben wurde. Dies ist jetzt mit „ByID“-Abfragen möglich. Während sich Pfade ändern können, was möglicherweise zu laufenden „ByPath“-Abfragen führen kann, sind UUIDs stabil. Die neuen IDs können auch als Eigenschaften in jeder Abfrage oder einer anderen anwendbaren API-Anfrage zurückgegeben werden. Aktuelle Einschränkung (2025.1): Seitenverweise werden noch nicht mit eindeutigen IDs unterstützt. Wenn Seiten in Inhaltsfragmenten referenziert werden, sollte diese Funktion nicht verwendet werden. Diese Einschränkung soll mit der nächsten AEM as a Cloud Service-Version entfernt werden.

**AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten**

Die [AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten](/help/headless/aem-rest-openapi-content-fragment-delivery.md) ist jetzt für AEM as a Cloud Service verfügbar.

### Veraltete Funktionen {#sites-deprecated}

#### SPA-Editor {#spa-editor}

[Der SPA-](/help/implementing/developing/hybrid/introduction.md) wird für neue Projekte ab Version 2025.1.0 nicht mehr unterstützt. Der SPA-Editor wird für bestehende Projekte weiterhin unterstützt, sollte jedoch nicht für neue Projekte verwendet werden.

Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind jetzt:

* [Der universelle Editor](/help/edge/wysiwyg-authoring/authoring.md) für die visuelle Bearbeitung.
* [Der Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) für die formularbasierte Bearbeitung

#### PWA-Funktionen {#pwa-features}

[Die Funktionen der Progressive Web App (PWA](/help/sites-cloud/authoring/sites-console/enable-pwa.md) für AEM Sites werden für neue Projekte ab Version 2025.1.0 nicht mehr unterstützt. Diese Funktion wird für bestehende Projekte weiterhin unterstützt, sollte jedoch nicht für neue Projekte verwendet werden

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in AEM Assets {#new-features-assets}

**Dynamic Media-Vorlagen**

Personalisieren Sie Bild- und Textbanner direkt mit einem benutzerfreundlichen WYSIWYG Dynamic Media-Vorlageneditor, indem Sie die URL in eine Erstanbieter- oder Drittanbieteranwendung einbetten, um mit Echtzeit-Bannerinhalten ansprechende Erlebnisse zu schaffen.

![Dynamische Ausgabedarstellungen](/help/assets/assets/dm-templates-smart-text-resize.png)

**Dynamic Media-Versandberichte**

Gewinnen Sie Einblicke in den Versand für Assets, die über Dynamic Media bereitgestellt werden, einschließlich der Anzahl der Sendungen auf Asset-Ebene, Referrer-Details, Asset-Pfade in AEM Assets und eindeutiger Asset-IDs. Generieren von Berichten für alle Assets im AEM Assets-Repository oder für bestimmte Ordnerhierarchien. Mit diesen Einblicken können Sie den ROI der bereitgestellten Assets messen, die Kanalleistung bewerten und fundierte Entscheidungen für das Asset-Management treffen.

![Dynamische Ausgabedarstellungen](/help/assets/assets/referrer.png)

**Dynamic Media Multi-Audio und Untertitel**

[Unterstützung für mehrere Untertitel und Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) - Sie können jetzt auf einfache Weise mehrere Untertitel und mehrere Audiospuren zu einem Primärvideo hinzufügen. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

**Unterstützung von dynamischem adaptivem Streaming über HTTP**

Neue Protokollunterstützung (DASH – Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF) eingeführt:

* Adaptives Streaming (DASH/HLS) sorgt für ein besseres Anwendererlebnis bei der Videoanzeige.

* DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weithin verwendet

**Asset-Beziehungen**

Die Assets-Ansicht unterstützt jetzt das Anzeigen und Bearbeiten von Asset-Beziehungen in einem vereinfachten Bedienfeld mit Asset-Details. Fügen Sie mühelos Beziehungen wie Source und Derivative zu Inhalten hinzu, damit Benutzer relevante Hero-Inhalte effektiver finden können.

**Assets erneut verarbeiten**

Die Assets-Ansicht unterstützt jetzt die Neuverarbeitung von Assets, die in einem Ordner verfügbar sind. Sie können entweder die Option **Vollständiger Prozess** verwenden oder erweiterte Optionen wie standardmäßige Vorschau-Ausgabedarstellungen, Metadaten, Nachbearbeitungs-Workflow und Verarbeitungsprofil verwenden.

### Early Access-Funktionen in AEM Assets {#early-access-features-assets}

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion soll die Barrierefreiheit und das Benutzererlebnis verbessern, indem akkurate Untertitel in Echtzeit bereitgestellt werden. Untertitel werden aus dem Originalaudio, zusätzlichen Audiospuren oder zusätzlichen Untertiteln generiert, die in der Registerkarte „Untertitel und Audio“ auf der Seite mit den Videoeigenschaften bereitgestellt werden. Da mehr als 60 Sprachen unterstützt werden, können Untertitel vor der Veröffentlichung des Videos überprüft und in der Vorschau angezeigt werden.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in AEM Forms {#forms-new-features}

* **Veröffentlichung verwalten**: Sie können den Workflow „Veröffentlichung verwalten“ verwenden, um Formulare in Umgebungen zu veröffentlichen oder die Veröffentlichung rückgängig zu machen, normalerweise von der Autoreninstanz bis zur Veröffentlichungs- und Vorschauinstanz. Er ermöglicht es Benutzenden, Inhalte zu veröffentlichen, ihre Veröffentlichung rückgängig zu machen oder ihre Veröffentlichung effizient zu planen.

* **[Automatisches Speichern eines Entwurfs für auf Kernkomponenten basierende adaptive Formulare](/help/forms/save-core-component-based-form-as-draft.md)**: Benutzende können jetzt von einer automatischen Speicherfunktion profitieren, mit der ein teilweise ausgefülltes Formular automatisch als Entwurf gespeichert wird. Sie können später zurückkehren, um das Ausfüllen des Formulars auf demselben oder einem anderen Gerät abzuschließen. Diese Funktion verbessert die Konversionsraten für Unternehmen, indem Formularabbrüche reduziert werden, da Benutzende nicht mit dem Ausfüllen von Formularen von Anfang an beginnen müssen.

* **[Verbesserungen des Regeleditors](/help/forms/invoke-service-enhancements-rule-editor.md)**: Für adaptive Forms, die auf Kernkomponenten basieren, können Sie die Ausgabe von „Service aufrufen“ verwenden, um Dropdown-Optionen auszufüllen und wiederholbare oder einzelne Bedienfelder festzulegen. Darüber hinaus kann diese Ausgabe zur Validierung anderer Felder verwendet werden.

* **[Verbessern des Anwendererlebnisses mit Navigations-Schaltflächen in Bedienfeld-Layouts](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)**: Sie können Ihren Bedienfeld-Layouts jetzt Navigations-Schaltflächen hinzufügen, z. B. horizontale Registerkarten, vertikale Registerkarten, Akkordeons oder Assistent. Diese Schaltflächen verbessern das Anwendererlebnis, indem sie die Übergänge zwischen Bedienfeldern vereinfachen und sich auf das ausgewählte Bedienfeld konzentrieren.


### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### [HTML von E-Mail-Vorlagen in adaptiven Forms](/help/forms/html-email-templates-in-adaptive-forms.md)

Adaptive Forms ermöglicht die Verwendung von HTML-E-Mail-Vorlagen. HTML-E-Mail-Vorlagen ermöglichen es Ihnen, beim Senden eines Formulars ansprechende, personalisierte und visuell ansprechende E-Mails zu senden. Diese E-Mails können mit Formulardaten angepasst und mit verschiedenen E-Mail-Tags, wie Bildern und Links, erweitert werden. Bei Adaptive Forms können Sie entweder eine Datei hochladen, die eine HTML-Vorlage enthält, oder einen Texteditor verwenden, um diese Vorlagen zu erstellen.

![HTML-E-Mail-Vorlagen](/help/forms/assets/html-email.png)

#### Erweiterte Cloud-Speicher-Unterstützung: Direkter PDF-Upload in Azure Blob Storage

AEM Forms Document Generation-APIs unterstützen jetzt das direkte Hochladen generierter PDF-Dokumente in Azure Blob Storage. Diese Verbesserung optimiert die Speicherung und den Abruf und verbessert die Effizienz und Integration mit Cloud-Workflows.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Java 21-Unterstützung {#java21}

Sie können jetzt mit Java 21 Code erstellen, der neue Funktionen (z. B. Mustervergleich für Switch-Anweisungen, versiegelte Klassen) und Leistungsverbesserungen enthält. Java 17-Builds werden ebenfalls neu unterstützt. Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie im Artikel [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) .

Die leistungsfähigere Java 21 **Laufzeitumgebung** wird automatisch bereitgestellt, wenn ein Java 17- oder Java 21-Build erkannt wird. Wir empfehlen jedoch auch, sich für Umgebungen, die mit Java 11 erstellt wurden, bei der Java 21-Laufzeitumgebung anzumelden, indem Sie eine E-Mail an [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) senden. Erfahren Sie mehr über [Java 21-Laufzeitanforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Java 21 **runtime** wird schrittweise in **allen**-Umgebungen bereitgestellt (abgesehen von den bereits mit Java 17 oder 21 erstellten Umgebungen, die bereits Java 21-Laufzeitumgebungen haben), beginnend mit Sandboxes und dev/rde im Februar und dann mit Staging/Produktion im April.

### Sandbox-Programme unterstützen Konfigurations-Pipelines {#sandbox-config-pipelines}

Sandbox-Programme unterstützen jetzt Konfigurations-Pipelines, die in Cloud Manager so konfiguriert werden können, dass sie YAML-Dateien bereitstellen, die in Git persistiert werden.

[Erfahren Sie mehr](/help/operations/config-pipeline.md) über Konfigurations-Pipelines, die die Konfiguration des CDN, die Protokollweiterleitung und Wartungsaufgaben für die Versionsbereinigung/Auditprotokollbereinigung ermöglichen.

### OpenAPI-basierte APIs – Early-Adopter-Programm {#open-apis-earlyadopter}

Entwickelnde können AEM as a Cloud Service-Funktionen in ihre eigenen Anwendungen und Tools integrieren. Neue AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation mit dem Ziel, konsistent, gut dokumentiert und benutzerfreundlich zu sein. Anmeldeinformationen für Endpunkte, für die eine Authentifizierung erforderlich ist, werden durch Erstellen von Adobe Developer Console-Projekten generiert.

Erfahren Sie mehr über [OpenAPI-basierte AEM-APIs](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [End-to-End-Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) aus, in dem Konfiguration und Verwendung veranschaulicht werden.

Konkret sind die unten aufgeführten API-Endpunkte im Rahmen eines Early-Adopter-Programms verfügbar. Wenn Sie daran interessiert sind, senden Sie eine E-Mail an [aem-apis@adobe.com](mailto:aem-apis@adobe.com), in der Sie beschreiben, wie Sie die API-Endpunkte verwenden möchten.

* [Sites-Inhaltsfragmente-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de)
* [Assets-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [Sites- und Assets-Ordner-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [Forms-Kommunikationen-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge-Computing – Einladung zum Feedback! {#edge-computing-feedback}

Edge-Computing bringt die Datenverarbeitung näher an den Browser heran, was Vorteile bietet, darunter eine reduzierte Latenz. Adobe würde es begrüßen zu hören, wenn Sie diese Technologie für AEM Publish Delivery and Edge Delivery Services-Projekte nützlich finden. Teilen Sie uns außerdem mit, was Sie sich vorstellen, um es als Input für die Produkt-Roadmap zu verwenden. Schreiben Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit Fragen und Kommentaren!

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
