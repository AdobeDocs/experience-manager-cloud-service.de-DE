---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 8c33426c38b087c83b945572374089ad9cb44daf
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 40%

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

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.1.0) ist der Freitag, 25. Januar 2024. Die nächste Version mit neuen Funktionen (2024.2.0) ist für den Freitag, 29. Februar 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht Januar 2024 an, das eine Zusammenfassung der Funktionen bietet, die der Version 2024.1.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3427041?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Extension Manager in AEM Sites {#sites-extension-manager}

**Neue Funktionen [Extension Manager in AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/)** , um Ihre AEM einzurichten, indem Sie Benutzeroberflächen-Erweiterungen konfigurieren.

![Extension Manager in AEM Sites](/help/assets/sites/extension-manager/homepage.png)

Der Extension Manager in AEM Sites ermöglicht es Entwicklern und Anwendern, auf Benutzeroberflächen-Erweiterungen zuzugreifen, sie zu verwalten und anzupassen, die zur Verbesserung der Funktionen von AEM Sites entwickelt wurden.
Mit dem Extension Manager können Sie:

* Aktivieren oder Deaktivieren von Erweiterungen pro Instanz;
* Konfigurieren von Erweiterungsparametern;
* Vorschau von Erweiterungen anzeigen und einen freigebbaren Vorschau-Link erstellen;
* Funktionen zur Erweiterbarkeit der Benutzeroberfläche über interaktive Demos;
* Greifen Sie über Erstanbietererweiterungen auf Adobe zu.

Wir suchen aktiv nach Feedback und neuen Anwendungsfällen für Benutzeroberflächen-Erweiterungen. Wenn Sie eine Verbindung herstellen möchten, senden Sie bitte eine E-Mail an `uix@adobe.com`.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Vorabversionsfunktionen für die Admin-Ansicht {#admin-view-prerelease}

**Vorschau der Ausgabedarstellungen für alle unterstützten Videotypen anzeigen**

Experience Manager Assets generiert jetzt standardmäßig Vorschaudarstellungen aller unterstützten Videotypen, ohne dass eine Verarbeitungsprofilkonfiguration erforderlich ist.

### Asset-Ansicht {#assets-view-features}

**Smart-Tags-Blockierungsliste**

Mit Assets Essentials können Sie jetzt eine Blockierungsliste mit Wörtern festlegen, die beim Hochladen in das Repository nicht als Smart-Tags zu Assets hinzugefügt werden sollen. Diese Funktion hilft Ihnen, die Markenkonformität zu wahren und reduziert den Aufwand für die Moderation von Smart-Tags.

![Smart-Tags-Blockierungsliste](/help/assets/assets/block-tags.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Frühkindliche Betreuung {#forms-early-adopter}

* **[Senden eines adaptiven Formulars an das Adobe Workfront Fusion-Szenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service bietet vordefinierte Optionen, um ein adaptives Formular einfach mit Adobe Workfront zu verbinden. Dadurch wird der Prozess zum Senden eines adaptiven Formulars an ein Adobe Workfront-Szenario vereinfacht, sodass Sie bei der Übermittlung eines adaptiven Formulars ein Workfront Fusion-Szenario Trigger haben.

* **[Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/supporting-new-language-localization-core-components.md)**: Adaptive Forms, die auf Kernkomponenten basiert, kann jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. Die RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese unterschiedlichen Zielgruppen zu bedienen und auf RTL-Märkten auszuwählen. In bestimmten Regionen ist es auch ein gesetzliches Mandat, Formulare in der Landessprache zu verfassen. Durch die Unterbringung der lokalen Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

  ![Unterstützung von Sprachen mit Rechts-Links](/help/forms/assets/right-to-left-language-support.png)

* **[Protect Ihrer Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch die Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sorgt auch für ein beruhigendes Gefühl. Signature-APIs ermöglichten Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies vorgesehen ist, die Dokumente ändern können.

  Sie können schreiben an `aem-forms-early-adopter-program@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Unterstützung für Dynatrace {#dynatrace}

Dynatraktikkunden können ihre AEM überwachen. [Lesen von](/help/implementing/cloud-manager/dynatrace.md) , um eine Verbindung mit Ihrer Dynatraktionsumgebung zur Überwachung der Anwendungsleistung anzufordern. Beachten Sie, dass das New Relic-APM, das für alle Kunden verfügbar ist, die Datenerfassung stoppt, wenn Dynatrace aktiviert ist.

### RDE-Unterstützung für Frontend-Code mithilfe von Site-Designs und Site-Vorlagen: Frühkindliches Adopter-Programm {#rde-frontend-early-adopter}

[Rapid Development Environments (RDEs)](/help/implementing/developing/introduction/rapid-development-environments.md) unterstützt jetzt Front-End-Code basierend auf [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md) und [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md), für frühe Anwender. Bei RDEs erfolgt dies über eine Befehlszeilenanweisung und nicht über eine [Front-End-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Bitte wenden Sie sich an **aemcs-rde-support@adobe.com** , um es auszuprobieren und Feedback zu geben.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
