---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 8a64e2ca1dc3987558c36346422ee43d202d9ecc
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 91%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.1.0) ist der 25. Januar 2024. Die nächste Version mit neuen Funktionen (2024.3.0) ist für den 4. April 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video zur Versionsübersicht von Januar 2024 an, das eine Zusammenfassung der Funktionen gibt, die in Version 2024.1.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3427041?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Extension Manager in AEM Sites {#sites-extension-manager}

**Entdecken Sie den neuen [Extension Manager in AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/)**, um Ihre AEM-Einrichtung zu personalisieren, indem Sie Benutzeroberflächenerweiterungen konfigurieren.

![Extension Manager in AEM Sites](/help/assets/sites/extension-manager/homepage.png)

Der Extension Manager in AEM Sites ermöglicht Entwickelnden und Anwendenden den Zugriff, die Verwaltung und die Anpassung von [Benutzeroberflächen-Erweiterungen](https://developer.adobe.com/uix/docs/), die mit [Adobe App Builder](https://developer.adobe.com/app-builder/) erstellt wurden, um die Funktionalität von AEM Sites zu verbessern.
Mit dem Extension Manager können Sie:

* Erweiterungen pro Instanz aktivieren oder deaktivieren;
* Erweiterungsparameter konfigurieren;
* eine Vorschau von Erweiterungen anzeigen und einen freigebbaren Vorschau-Link erstellen;
* Funktionen zur Erweiterbarkeit der Benutzeroberfläche über interaktive Demos entdecken;
* über Erstanbietererweiterungen auf Adobe zugreifen.

Wir suchen aktiv nach Feedback und neuen Anwendungsfällen für Benutzeroberflächenerweiterungen. Wenn Sie in Kontakt treten möchten, senden Sie bitte eine E-Mail an `uix@adobe.com`.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Vorabversionsfunktionen für die Admin-Ansicht {#admin-view-prerelease}

**Vorschau der Ausgabedarstellungen für alle unterstützten Videotypen**

Experience Manager Assets generiert jetzt standardmäßig Vorschaudarstellungen aller unterstützten Videotypen, ohne dass eine Verarbeitungsprofilkonfiguration erforderlich ist.

### Assets-Ansicht {#assets-view-features}

**Smart-Tags-Blockierungsliste**

Mit Assets Essentials können Sie jetzt eine Blockierungsliste mit Wörtern festlegen, die beim Hochladen in das Repository nicht als Smart-Tags zu Assets hinzugefügt werden sollen. Diese Funktion hilft Ihnen, die Markenkonformität zu wahren und reduziert den Aufwand für die Moderation von Smart-Tags.

![Smart-Tags-Blockierungsliste](/help/assets/assets/block-tags.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Early-Adopter-Programm {#forms-early-adopter}

* **[Senden eines adaptiven Formulars an das Adobe Workfront Fusion-Szenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service bietet vordefinierte Optionen, um ein adaptives Formular einfach mit Adobe Workfront zu verbinden. Dadurch wird der Prozess zum Senden eines adaptiven Formulars an ein Adobe Workfront-Szenario vereinfacht, indem Sie bei der Übermittlung eines adaptiven Formulars ein Workfront Fusion-Szenario auslösen können.

* **[Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/supporting-new-language-localization-core-components.md)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese unterschiedlichen Zielgruppen zu bedienen und in RTL-Märkte einzutreten. In bestimmten Regionen ist es außerdem gesetzlich vorgeschrieben, Formulare in der jeweiligen Regionalsprache bereitzustellen. Durch die Anpassung an lokale Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

  ![Unterstützung von Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/assets/right-to-left-language-support.png)

* **[Schützen Sie Ihre Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies auch vorgesehen ist, die Dokumente ändern können.

  Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-early-adopter-program@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

* **[Sie können den Datendienst Real User Monitoring (RUM) nutzen](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**, um die Client-seitige Sammlung für AEM as a Cloud Service zu aktivieren.
Der Datendienst Real User Monitoring (RUM) bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kundinnen und Kunden, die entweder ein von Adobe verwaltetes CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Für diejenigen, die ein nicht von Adobe verwaltetes CDN verwenden, kann jetzt außerdem die automatisierte Traffic-Berichterstellung aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

  Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-rum-adopter@adobe.com`. Geben Sie in der E-Mail den Domain-Namen für jede Umgebung an, für die Sie RUM aktivieren möchten. Das Produkt-Team von Adobe aktiviert dann den Datendienst Real User Monitoring (RUM) für Sie.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Unterstützung für Dynatrace {#dynatrace}

Dynatrace-Kundinnen und -Kunden können ihre AEM-Nutzung überwachen. [Lesen Sie](/help/implementing/cloud-manager/dynatrace.md), wie Sie die Konnektivität mit Ihrer Dynatrace-Umgebung für die Überwachung der Anwendungsleistung anfordern können. Beachten Sie, dass die New Relic-APM, die für alle Kundinnen und Kunden verfügbar ist, die Datenerfassung stoppt, wenn Dynatrace aktiviert ist.

### RDE-Unterstützung für Frontend-Code mithilfe von Site-Designs und Site-Vorlagen: Early-Adopter-Programm {#rde-frontend-early-adopter}

[Schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs)](/help/implementing/developing/introduction/rapid-development-environments.md) unterstützen jetzt Frontend-Code basierend auf [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md) und [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md) für Early Adopters. Bei RDEs erfolgt dies über eine Befehlszeilenanweisung und nicht über eine [Frontend-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Bitte wenden Sie sich an **aemcs-rde-support@adobe.com**, um dies auszuprobieren und Feedback zu hinterlassen.

### CDN-Konfiguration Frühkindlicher Anwender {#cdn-config-early-adopter}

Zusätzlich zu den kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), das die optional lizenzierbaren Web Application Firewall (WAF)-Regeln enthält, gibt es eine Möglichkeit, die Configuration Pipeline zum Deklarieren und Bereitstellen zu verwenden [andere Typen von CDN-Konfigurationen](/help/implementing/dispatcher/cdn-configuring-traffic.md). Treten Sie dem frühen Adopter-Programm per E-Mail bei. **aemcs-cdn-config-adopter@adobe.com** Zugriff auf:
* 301/302 Client-seitige Umleitungen
* Proxying-Anfragen am Edge zu beliebigen Ursprüngen
* URL-Transformationen
* Anforderungs- oder Antwortheader festlegen oder ändern
* benutzerdefinierte Fehlerseiten, wenn das CDN nicht AEM erreichen kann

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

