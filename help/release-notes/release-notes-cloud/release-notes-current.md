---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: a5121436b2e48302fcf14478764aede1495e089c
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 27%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.12.0) war der Freitag, 14. Dezember 2023. Die nächste Version (2024.1.0) ist für den Donnerstag, 25. Januar 2023 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the December 2023 Release Overview video for a summary of the features added in the 2023.12.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Frühkindliche Betreuung {#sites-early-adopter}

**Sie können die [Datendienst für die Echtzeit-Benutzerüberwachung (RUM)](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** , um die clientseitige Erfassung für AEM as a Cloud Service zu aktivieren.

Der Real User Monitoring (RUM) Data Service bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktion sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist zwar für Kunden von Vorteil, die entweder Adobe-verwaltetes CDN oder nicht-Adobe-verwaltetes CDN verwenden. Darüber hinaus kann für Kunden, die ein nicht von Adobe verwaltetes CDN verwenden, die automatisierte Traffic-Berichterstellung jetzt für sie aktiviert werden, sodass die Freigabe von Traffic-Berichten für Adobe entfällt.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte eine E-Mail an `aemcs-rum-adopter@adobe.com`zusammen mit Ihrem Domänennamen für die Produktions-, Staging- und Entwicklungsumgebung von Ihrer E-Mail-Adresse aus, die mit Ihrer Adobe ID verknüpft ist. Das Produktteam von Adobe aktiviert dann den Datendienst für die Echtzeit-Benutzerüberwachung (RUM) für Sie.


<!--

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### New Features in Admin View {#admin-view-features}



* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)


**Video Preview**: AEM Assets now generates preview renditions of all supported video formats by default, without the need to configure a processing profile.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Experience Manager Forms] {#forms-features}

* **[Verbinden eines adaptiven Formulars mit einer Microsoft® SharePoint-Liste](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms bietet eine vorkonfigurierte Integration zum Senden von Formulardaten direkt an eine SharePoint-Liste, sodass Sie die Listenfunktionen von SharePoint verwenden können. Sie können die Microsoft SharePoint-Liste als Datenquelle für ein Formulardatenmodell konfigurieren und die **Senden mit Formulardatenmodell** Übermittlungsaktion zum Verbinden eines adaptiven Formulars mit einer SharePoint-Liste.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Frühkindliche Betreuung {#forms-early-adopter}

* **[Senden eines adaptiven Formulars an das Adobe Workfront Fusion-Szenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service bietet vordefinierte Optionen, um ein adaptives Formular einfach mit Adobe Workfront zu verbinden. Dadurch wird der Prozess zum Senden eines adaptiven Formulars an ein Adobe Workfront-Szenario vereinfacht, sodass Sie bei der Übermittlung eines adaptiven Formulars ein Workfront Fusion-Szenario Trigger haben.

* **[Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/supporting-new-language-localization-core-components.md)**: Adaptive Forms, die auf Kernkomponenten basiert, kann jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. Die RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese unterschiedlichen Zielgruppen zu bedienen und auf RTL-Märkten auszuwählen. In bestimmten Regionen ist es auch ein gesetzliches Mandat, Formulare in der Landessprache zu verfassen. Durch die Unterbringung der lokalen Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

  ![Unterstützung von Sprachen mit Rechts-Links](/help/forms/assets/right-to-left-language-support.png)

* **[Protect Ihrer Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzer Zugriff erhalten. Diese befestigte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Augen, sondern bietet auch Seelenfrieden. Signature-APIs ermöglichten Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Dienst verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur beabsichtigte Empfänger Dokumente ändern können.

  Sie können schreiben an `aem-forms-early-adopter-program@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### CDN-Konfiguration Frühkindlicher Anwender {#cdn-config-early-adopter}

Zusätzlich zu den kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), das die optional lizenzierbaren Web Application Firewall (WAF)-Regeln enthält, gibt es eine Möglichkeit, die Configuration Pipeline zu verwenden, um andere Typen der CDN-Konfiguration zu deklarieren und bereitzustellen. Wir würden uns über Ihre Anwendungsfälle freuen, einschließlich:
* 301/302 Client-seitige Umleitungen
* Proxying-Anfragen am Edge zu beliebigen Ursprüngen
* URL-Transformationen
* Anforderungs- oder Antwortheader festlegen oder ändern
* benutzerdefinierte Fehlerseiten, wenn das CDN nicht AEM erreichen kann
* Authentifizierung durch Benutzername/Kennwort
* alle anderen nützlichen CDN-Konfigurationen

E-Mail an senden **aemcs-cdn-config-adopter@adobe.com** von Ihrer offiziellen E-Mail-ID mit Ihrem Feedback.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
