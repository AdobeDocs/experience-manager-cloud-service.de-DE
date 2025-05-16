---
title: Versionshinweise für Version 2023.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: b36add58-a2ba-4299-94be-e0026e9c553c
feature: Release Information
role: Admin
source-git-commit: 603602dc70f9d7cdf78b91b39e3b7ff5090a6bc0
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 77%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.12.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.12.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.12.0) ist der Freitag, 14. Dezember 2023. Die nächste Version (2024.1.0) ist für den Donnerstag, 25. Januar 2023 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the December 2023 Release Overview video for a summary of the features added in the 2023.12.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Early-Adopter-Programm {#sites-early-adopter}

**Sie können den [Real Use Monitoring (RUM) Data Service) nutzen](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** um die Client-seitige Erfassung für AEM as a Cloud Service zu aktivieren.

Der Real Use Monitoring-Datendienst (RUM) bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kundinnen und Kunden, die entweder ein von Adobe verwaltetes CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Für diejenigen, die ein nicht von Adobe verwaltetes CDN verwenden, kann jetzt außerdem die automatisierte Traffic-Berichterstellung aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

Wenn Sie diese neue Funktion testen und Ihr Feedback geben möchten, senden Sie eine E-Mail an `aemcs-rum-adopter@adobe.com` sowie Ihren Domain-Namen für die Produktions-, Staging- und Entwicklungsumgebung über Ihre mit Ihrer Adobe ID verknüpfte E-Mail-Adresse. Das Produkt-Team von Adobe wird dann den Real Use Monitoring (RUM)-Datendienst für Sie aktivieren.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

**GenAI-Bilder mit Adobe Firefly erstellen**

Erstellen Sie neue Bilder auf Basis von Suchabfragen mit Integration einer Adobe Firefly Text-zu-Bild-Funktion (Adobe Firefly-Lizenz erforderlich).

![Assets Firefly-Integration](/help/assets/assets/assets-firefly-integration.png)

**Nach ähnlichen Bildern suchen**

Sie können jetzt Inhalte einfach finden, indem Sie ein Bild auswählen und ähnliche Bilder im Experience Manager Assets-Repository anzeigen.

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)


**Video Preview**: AEM Assets now generates preview renditions of all supported video formats by default, without the need to configure a processing profile.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Experience Manager Forms] {#forms-features}

* **[Verbinden eines adaptiven Formulars mit einer Microsoft® SharePoint-Liste](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms bietet eine vorkonfigurierte Integration zum Senden von Formulardaten direkt an eine SharePoint-Liste, sodass Sie die Listenfunktionen von SharePoint verwenden können. Sie können die Microsoft SharePoint-Liste als Datenquelle für ein Formulardatenmodell konfigurieren und die Übermittlungsaktion **Senden mit Formulardatenmodell** verwenden, um ein adaptives Formular mit der SharePoint-Liste zu verbinden.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Early-Adopter-Programm {#forms-early-adopter}

* **[Senden eines adaptiven Formulars an das Adobe Workfront Fusion-Szenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service bietet vordefinierte Optionen, um ein adaptives Formular einfach mit Adobe Workfront zu verbinden. Dadurch wird der Prozess zum Senden eines adaptiven Formulars an ein Adobe Workfront-Szenario vereinfacht, indem Sie bei der Übermittlung eines adaptiven Formulars ein Workfront Fusion-Szenario auslösen können.

* **[Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/supporting-new-language-localization-core-components.md)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese unterschiedlichen Zielgruppen zu bedienen und in RTL-Märkte einzutreten. In bestimmten Regionen ist es außerdem gesetzlich vorgeschrieben, Formulare in der jeweiligen Regionalsprache bereitzustellen. Durch die Anpassung an lokale Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

  ![Unterstützung von Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/assets/right-to-left-language-support.png)

* **[Schützen Sie Ihre Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies auch vorgesehen ist, die Dokumente ändern können.

  Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Early-Adopter-Programm für die Domain-Zuordnung {#cdn-config-early-adopter}

Zusätzlich zu den kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), die die optional lizenzierbaren WAF-Regeln (Web Application Firewall) enthalten, gibt es die Möglichkeit, die Konfigurations-Pipeline zu verwenden, um andere Arten von CDN-Konfigurationen zu deklarieren und bereitzustellen. Wir würden uns über Ihre Anwendungsfälle freuen, einschließlich:
* 301/302 Client-seitige Umleitungen
* Weiterleitungs-Anfragen am Edge zu beliebigen Ursprüngen
* URL-Transformationen
* Festlegen oder Ändern von Anfragen- oder Antwortkopfzeilen
* benutzerdefinierte Fehlerseiten, wenn das CDN AEM nicht erreichen kann
* Authentifizierung mit Benutzername/Kennwort
* alle anderen nützlichen CDN-Konfigurationen

Senden Sie von Ihrer offiziellen E-Mail-ID mit **Feedback eine E-Mail an** aemcs-cdn-config-adopter@adobe.com.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
